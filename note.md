# Windows nvidia-smi
	C:\Program Files\NVIDIA Corporation\NVSMI

# Xshell
	^H ctrl+backspace



# Excel
	each 10: f(x)=OFFSET(A$10,(ROW(A1)-1)*10,)

# ffmpeg
```bash
-allowed_extensions ALL允许任意扩展名
```

# 查看版本
### opencv
```bash
pkg-config opencv --modversion
```

# ERROR
### cannot open display
	当使用su 到另外一个用户运行某个程序，而这个程序又要有图形显示的时候，就有可能有下面提示：
	No protocol specified
	(gedit:14333): Gtk-WARNING **: cannot open display: :0.0
	这是因为Xserver默认情况下不允许别的用户的图形程序的图形显示在当前屏幕上. 如果需要别的用户的图形显示在当前屏幕上, 则应以当前登陆的用户, 也就是切换身份前的用户执行如下命令。
	xhost +通过执行这条命令，就授予了其它用户访问当前屏幕的权限，于是就可以以另外的用户运行需要运行的程序了。

### 编译共享库使用静态库报错
	relocation R_X86_64_32 against `.rodata' can not be used when making a shared object
	recompile 静态库 with -fPIC

# ELSE
### 熵
	信息熵：H(x) = ∫-p(x) log p(x)
	交叉熵：H(p,q) = ∫-p(x) log q(x)
	KL散度(相对熵)：KL(p||q) = H(p,q)-H(p) = ∫ p(x) log (p(x)/q(x))
	JS散度：JS(p||q)=1/2*(KL(p||(p+q)/2)) + KL(q||(p+q)/2))
