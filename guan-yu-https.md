### 一篇关于https很不错的文章

* #### 张大胖与Bill沟通需要约定一个只有两个人知道的密钥

###### ![](/assets/6401.webp)

* #### 如何传递密钥？通过一种RSA算法的非对称加密算法，一个私钥一个公钥。
* #### **用私钥加密的数据，只有对应的公钥才能解密，用公钥加密的数据， 只有对应的私钥才能解密**
* #### 张大胖用Bill公钥去加密，Bill私钥去解密

#### ![](/assets/6402.webp)

#### ![](/assets/6403.webp)

* #### 如何确认Bill的公钥？“数字证书”：把原始信息和数据签名合并
* #### 张大胖收到Bill的证书时，用同样的Hash算法把信息生成消息摘要，然后用CA的公钥把数字签名解密生成消息摘要，对比是否一致。

![](/assets/6404.webp)

![](/assets/6405.webp)

* #### 总结。张大胖替换成浏览器， Bill 替换成某个网站。
* #### **简化的（例如下图没有包含Pre-Master Secret）**https流程图

![](/assets/640.webp)

原文链接：[一个故事讲完https](https://mp.weixin.qq.com/s/StqqafHePlBkWAPQZg3NrA)
