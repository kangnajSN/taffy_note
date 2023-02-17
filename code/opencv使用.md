### 两个图片拼接
> 将两张图片上下拼接
```java

Mat m2 = Imgcodecs.imread(path+i+".png", Imgcodecs.IMREAD_UNCHANGED); //大图片
Mat m1 = Imgcodecs.imread("", Imgcodecs.IMREAD_UNCHANGED); //小图片

//宽度取两个矩阵中的较大者的宽度
double w = Math.max(m2.size().width, m1.size().width);
//高度为两图的宽度之和
double h = m1.size().height + m2.size().height + 30;
//创建一个大矩阵对象
Mat des = Mat.zeros((int)h, (int)w, m1.type());

//在最终的大图上标记一块区域，用于存放复制图1（左图）的数据，大小为从第0列到m1.cols()列
Mat rectForM1 = des.rowRange(new Range(0, m1.rows()));

//标记出位于rectForM1的垂直方向上中间位置的区域，高度为图1的高度，此时该区域的大小已经和图1的大小相同。（用于存放复制图1（左图）的数据）
int colOffset1 = (int)(rectForM1.size().width-m1.cols())/2;
rectForM1 = rectForM1.colRange(colOffset1, colOffset1 + m1.cols());


//在最终的大图上标记一块区域，用于存放复制图2（右图）的数据
Mat rectForM2 = des.rowRange(new Range(m1.rows()+30, des.rows()));

//标记出位于rectForM2的垂直方向上中间位置的区域，高度为图2的高度，此时该区域的大小已经和图2的大小相同。（用于存放复制图2（右图）的数据）

int colOffset2 = (int)(rectForM2.size().width-m2.cols())/2;
rectForM2 = rectForM2.colRange(colOffset2, colOffset2 + m2.cols());


//将图1拷贝到des的指定区域 rectForM1
m1.copyTo(rectForM1);
//将图2拷贝到des的指定区域 rectForM2
m2.copyTo(rectForM2);

Imgcodecs.imwrite(path+i+".png", des);

```
