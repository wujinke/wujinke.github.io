---
title: TensorFlow显示卷积层结果
date: 2019-06-19 16:16:54
tags: [深度学习, TensorFlow, 卷积层可视化]
---

最近在学习深度子空间聚类的代码，想看一下在深度学习过程中的每一层的卷积层的可视化结果是如何的，因此在网上各种搜索尝试，最终实现如下

<!--more-->

```python
input_image = Img[11:12]  #选择一幅图片
W_conv1 = CAE.sess.run(CAE.encoder_layer[2], feed_dict={CAE.x:input_image}) #得到input_image的第三层的卷积层
#W_conv1 = CAE.sess.run(tf.reshape(W_conv1, [3, 1, 8, 8]))
W_conv1 = CAE.sess.run(tf.transpose(W_conv1, [3, 0, 2, 1]))
# 为了显示方便对得到的卷积层进行rashape 卷积层的本身维度为 [1,8,8,3] [,row,col,channle]
fig1,ax1 = plt.subplots(nrows=1, ncols=6, figsize = (6,1))
for i in range(5):
    ax1[i].imshow(W_conv1[i][0],cmap='gray')
#input_image = CAE.sess.run(tf.reshape(input_image, [1, 1, 32, 32]))
input_image = CAE.sess.run(tf.transpose(input_image, [3, 0, 2, 1]))
ax1[5].imshow(input_image[0][0],cmap='gray')#为了显示灰度图片，加上cmap=‘gray’
plt.title('W_conv1 3×8×8')
plt.show()
```

最终显示结果如下，可以看到在第三层的卷积层的时候，显示的是一种深层的语义特征

![1560932811760](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1560932811760.png)

之后希望能够在使用FPN（特征金字塔）来对这些卷积层的特征进行处理！