---
layout: post
title:  "Variable和placeholder的区别"
date:   2018-08-10 18:26:23
categories: 深度学习
tags: 深度学习 Tensorflow
excerpt: Variable是一个变量，是可以持久和更新的数据，主要用于存储训练变量比如权重矩阵W和偏置b一般定义为Variable.
mathjax: true
---
* content
{:toc}

### Variable和placeholder的区别

Variable是一个变量，是可以持久和更新的数据，主要用于存储训练变量比如权重矩阵W和偏置b一般定义为Variable;

placehoder不用初始化，在session.run(xx, feed_dict)时指定，主要用于输入样本和对应的标签



tf.truncated_normal(shape, mean, stddev) :shape表示生成张量的维度，mean是均值，stddev是标准差。这个函数产生正太分布，均值和标准差自己设定。



方法定义

tf.nn.conv2d (input, filter, strides, padding, use_cudnn_on_gpu=None, data_format=None, name=None)

参数：

- input : 输入的要做卷积的图片，要求为一个张量，shape为 [ batch, in_height, in_weight, in_channel ]，其中batch为图片的数量，in_height 为图片高度，in_weight 为图片宽度，in_channel 为图片的通道数，灰度图该值为1，彩色图为3。（也可以用其它值，但是具体含义不是很理解）
- filter： 卷积核，要求也是一个张量，shape为 [ filter_height, filter_weight, in_channel, out_channels ]，其中 filter_height 为卷积核高度，filter_weight 为卷积核宽度，in_channel 是图像通道数 ，和 input 的 in_channel 要保持一致，out_channel 是卷积核数量。
- strides： 卷积时在图像每一维的步长，这是一个一维的向量，[ 1, strides, strides, 1]，第一位和最后一位固定必须是1
- padding： string类型，值为“SAME” 和 “VALID”，表示的是卷积的形式，是否考虑边界。”SAME”是考虑边界，不足的时候用0去填充周围，”VALID”则不考虑
- use_cudnn_on_gpu： bool类型，是否使用cudnn加速，默认为true



tf.nn.max_pool(value, ksize, strides, padding, name=None)

参数是四个，和卷积很类似：

第一个参数value：需要池化的输入，一般池化层接在卷积层后面，所以输入通常是feature map，依然是[batch, height, width, channels]这样的shape

第二个参数ksize：池化窗口的大小，取一个四维向量，一般是[1, height, width, 1]，因为我们不想在batch和channels上做池化，所以这两个维度设为了1

第三个参数strides：和卷积类似，窗口在每一个维度上滑动的步长，一般也是[1, stride,stride, 1]

第四个参数padding：和卷积类似，可以取'VALID' 或者'SAME'

返回一个Tensor，类型不变，shape仍然是[batch, height, width, channels]这种形式



两种初始化所有变量的方法：

1: tf.global_variables_initializer().run(）

