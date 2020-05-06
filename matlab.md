# 无图形界面运行
```bash
matlab -nodesktop -nosplash -r matlabfile (no .m)
matlab -nodisplay -nodesktop -nojvm -nosplash -r matlabfile (no .m)
```
# PCA
```matlab
[coeff,~,~,~,~,mu]=pca(x)	%X:n*p coeff:p*p(p<=n) result=(X-mu)*coeff
```


# subplot

```matlab
figure;
subplot(2,2,1), imshow(I), title('original image');
subplot(2,2,2), imshow(J), title('noised image');
subplot(2,2,3), imshow(K), title('denoised image 1');
subplot(2,2,4), imshow(K), title('denoised image 2');
```
# 单变量函数绘制
```matlab
x = 1:1:100;
y = exp(-0.1*x);
plot(x,y)
xlabel('x');
ylabel('y');
grid on
```
# 双变量函数绘制
```matlab
t=0:1:10;
[x,y] =meshgrid(t);
z=(x-y)./(y+1);
surfc(x,y,z);
shading interp
xlabel('x')
ylabel('y');
zlabel('z');
title('f');
```
# fitcsvm
matlab自带的SVM分类器
```matlab
x=[1,2;2,3;3,3;2,1;3,2];
y=[1;1;1;-1;-1];
svmmodel=fitcsvm(x,y,'BoxConstraint',1e10);
```
BoxConstraint为软间隔分类错误惩罚系数，默认为1，调大可接近硬间隔

# else
```matlab
im2double(a): double(a)/255.0 if a -> uint8
a=[b,c,d] 字符串用单引号 双引号为单引号转义(字符串连接)
imresize(im,scale,'nearest'/'bilinear'/'bicubic')
```
