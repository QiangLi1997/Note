# 配置
## Anaconda
#### 换源
##### 目录
```
清华源：
https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
...
科大源：
https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
...
```
##### 命令
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/ (添加源到首位)
conda config --remove-key channels(换回默认源)
conda config --set show_channel_urls yes(设置搜索时显示通道地址)
```
##### ~/.condarc
```
auto_activate_base: false
ssl_verify: true
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
show_channel_urls: true
```
#### 环境
```bash
conda info -e
conda create -n py36 python=3.6
conda create -n rcan --clone edsr
conda clean -p      #删除没有用的包
conda remove -n py36 --all
conda install -n py36 package_name(=version)
conda list
conda upgrade --all
```
#### search package
```bash
https://anaconda.org/
conda install -c chembl easydict
```
## pip
#### 国内源	
```bash
pip install scrapy -i https://pypi.tuna.tsinghua.edu.cn/simple #https://pypi.mirrors.ustc.edu.cn/simple

pip install torch==1.5.0+cu101 torchvision==0.6.0+cu101 -f https://download.pytorch.org/whl/torch_stable.html

```
# 库
## TensorFlow
#### 检测GPU:
```python
from tensorflow.python.client import device_lib
	print(device_lib.list_local_devices())
```
#### 合适版本组合
```bash
to set
```
## PyTroch
#### install
```bash
stable python version: 3.7
conda install pytorch torchvision cuda80 (-c soumith)
(conda install pytorch torchvision (-c soumith))
pip install git+https://github.com/pytorch/tnt.git@master (PyTorchNet)
```
#### torch.masked_select(input,mask,out=None)
```python
torch.masked_select(x,x>0) #返回所有符合mask的值的一维向量
```
## OS
#### listdir
```python
for filename in os.listdir(dirname):
	print(filename)	#包含目录名和文件名
```
#### rename
```python
os.rename(filepath,newfilepath)
```
#### 判断文件存在
```python
import shutil
if not os.path.exists(filepath):
	shutil.copyfile(srcpath,filepath)
	shutil.move(srcpath,filepath)
else:
	os.rename(filepath,newfilepath)
```
## Argparse [[doc]](https://docs.python.org/2/library/argparse.html)
#### code
```python
import argparse
parser = argparse.ArgumentParser(description="Demo of argparse")
parser.add_argument('-n','--name', default=' Li ', help="your name")
parser.add_argument('-a','--age', default='22', type=int, help="your age")
args = parser.parse_args()
```
#### help info
```
>python xxx.py --help
usage: xxx.py [-h] [-n NAME] [-a AGE]

Demo of argparse

optional arguments:
  -h, --help            show this help message and exit
  -n NAME, --name NAME  your name
  -a AGE, --age AGE     your age
```
#### usage
```
>>> print(args)
Namespace(age=22, name=' Li ')
>>> a=args.name
>>> b=args.age
>>> a
' Li '
>>> b
22
```
#### 布尔变量
##### 默认假变量
```python
parser.add_argument('--is_real_time', default=False, type=bool, help='xxx')
```
useage:
```bash
python xxx.py --is_real_time true
(不一定是true，只要是字符串即判为true)
同样的，Python函数传布尔值参数时，直接传False也是无效的
```
##### 非默认假变量
```python
group = parser.add_mutually_exclusive_group(required=False)
group.add_argument('--gpu', dest='use_gpu', action='store_true')
group.add_argument('--no-gpu', dest='use_gpu', action='store_false')
parser.set_defaults(use_gpu=True)
```
## dlib合适版本	
```bash
dlib==19.7.0 face_recognition
```
## tqdm
#### windows cmd环境新行问题解决
```python
for i in tqdm(range(10),ascii=True)
```
## pickle
#### pkl文件读取
```python
#import cPickle as pickle
import pickle

fr = open('xxx.pkl','rb')
data = pickle.load(fr)
print(data)
fr.close()
```
## lmdb
```python
import lmdb
#创建
env = lmdb.open("./mylmdb", map_size=1099511627776)
txn = env.begin(write=True)
#添加
txn.put(key = '1'.encode(), value = 'a'.encode())
txn.put(key = '2'.encode(), value = 'b'.encode())
txn.put(key = '3'.encode(), value = 'c'.encode())
#删除
txn.delete(key = '1'.encode())
# 修改
txn.put(key = '3'.encode(), value = 'd'.encode())
print(txn.get('3'.encode()))
#遍历
for key, value in txn.cursor():
    print (key, value)
#提交更改
txn.commit()
env.close()
```
# 函数
#### assert
```python
assert ...(condition)
false:AssertionError
```
#### range
```
range(k) 0,1,...,k-1
```
#### print
```python
print(a,b,c,sep="*",end="*")
```

# 语法
#### for变量赋值
```python
>>> for c in range(3):
...     c+=1
...     print (c)
... 
1
2
3
```
#### 将模块当做脚本去启动有什么用？
```bash
python xxx.py
python -m xxx.py
这是两种加载py文件的方式:
1叫做直接运行
2相当于import,叫做当做模块来启动
```
#### import对比form import
```python
from random import *
for i in range(5):
  print(randint(1, 10)) # 这里就不需要random.前缀了
```

#### 字典
```python
dic={'a':'b'}
'a' in dic #True
'b' in dic #False
```
# 其他
#### numpy发音
```
网上比较通行读法是num pie, ‘num’ from number, ‘pie’ from python。 但是Numpy这个词中的num应该是来源于Numeric，如果按照这个逻辑的话，应该读作new pie才对。
```
