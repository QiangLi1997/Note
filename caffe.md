### deploy file
	dim: 1 #num，对待识别样本进行数据增广的数量，可自行定义。一般会进行5次crop，之后分别flip。如果该值为10则表示一个样本会变成10个，之后输入到网络进行识别。如果不进行数据增广，可以设置成1 
	dim: 3  #通道数，表示RGB三个通道 
	dim: 128
	dim: 128   #图像的长和宽 
### HDF5
	hdf5_data_param {
	     source: "mydata/train_list.txt"    //坑
	     batch_size: 200
	   }
	conda install graphviz
	conda install pydot
	python /data/liqiang/caffe/python/draw_net.py train.prototxt train.png --rankdir=BT
	caffe  train --solver hsr_solver.prototxt -gpu 0 2>&1 | tee train.log
	caffe  train --solver hsr_solver.prototxt --snapshot=lenet_iter_1000.solverstate
	caffe接收图像格式: W*H*C*N
	caffe  pronounced as cafe ---Yangqing Jia kaifei
### 输出静默
	layer {
	  name: "silence"
	  type: "Silence"
	  bottom: "parlabel"
	}
### 拼接层(默认1，1:沿通道拼接；0:沿batch拼接)
	layer {
	  name: "concat"
	  bottom: "in1"
	  bottom: "in2"
	  top: "out"
	  type: "Concat"
	  concat_param {
	  axis: 1
	  }
	}
### 官方建议反卷积参数
	layer {
	  name: "upsample", type: "Deconvolution"
	  bottom: "{{bottom_name}}" top: "{{top_name}}"
	  convolution_param {
	    kernel_size: {{2 * factor - factor % 2}} stride: {{factor}}
	    num_output: {{C}} group: {{C}}
	    pad: {{ceil((factor - 1) / 2.)}}
	    weight_filler: { type: "bilinear" } bias_term: false
	  }
	  param { lr_mult: 0 decay_mult: 0 }
	}
### log2excel
``` bash
cat train.log | grep "Test net" >testloss.log
cat train.log | grep "Train net" >trainloss.log
```
