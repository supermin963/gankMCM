
 [TOC]

## 线性规划
### 线性规划的定义:
>线性规划问题是在一组线性约束条件的限制下，求一线性目标函数最大或最小的问题。

 难点在于如何将实际问题转化为一个线性规划问题，**决策变量的选取**，至关重要。

***线性规划的MATLAB标准形式需要记住。
![image.png](https://upload-images.jianshu.io/upload_images/8518563-49dcc5cf6b63148f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

注意：目标函数必须是小于的形式，如果原始是大约那么将前面加一个负号。
以及MATLAB的输入形式：

`[x,fval]=linprog(c,A,b,Aeq,beq,LB,UB,X0,OPTIONS)`

这里fval 返回目标函数的值，LB 和UB 分别是变量x 的下界和上界， x0是x的初始值，OPTIONS 是控制参数。

**例题** :

![例题](https://upload-images.jianshu.io/upload_images/8518563-43b18aa983b39bbb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```matlab
%注意输入系数矩阵的时候直接按照原来的表示方法进行输入。
%但是！！
%调用linprog的时候需要根据标准形式进行变换。负号要有昂~
%以及最后的值如果是求max，要乘以c'。而不是-c
%另，删掉这条吧。太长了。
c=[2;3;-5];
a=[-2,5,-1;1,3,1]; b=[-10;12];
aeq=[1,1,1];
beq=7;
x=linprog(-c,a,b,aeq,beq,zeros(3,1))
value=c'*x
```

