# this is a note while i'm learning the AVC, may be little helpful


## 
防止竞争位的作用：

解码反过来处理

NAL的起始码到底是什么：0x 00 00 01， 0x 00 00 00 01也是，**因为是介质存储为了字节对齐的目的而已。**
所以起始码按照0x 00 00 01 来处理
起始码都按3个字节来处理

## 图像的IDR, I, P, B 是在哪里判断出来
首先不能说是picture的类型是I，P，还是B
因为图像是分成slice的，而slice才有I，P，B这样的说法
句法元素在slice header的第二个 slice_type 指明

nal 是可以判断出来 IDR 的，在 nal_uint_type 中说明


## 重建图像
预测值pred
残差值residual
二者的和就是图像的值


## 类的设置
本来一开始是想设置一个pixmap对象，直接从源数据中取出指针，然后对这个数据进行操作，
但是现在发现，看也不好看，用也不好用，说不定效率还低
emmmm，我关心那么多内存的问题干什么呢？
反正运算是不可能用8位的吧，运算必然是要用比这高的