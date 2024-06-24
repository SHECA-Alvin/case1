# **事件报告**

## **事件报告**

### **概括**

国际上有一部分CA对于IP SSL证书的控制权验证，是验443/80/22/25这4个端口，有另外一部分，只验443/80，做法各有不一样，BR上说的也比较模糊，我们实际也是4个端口在做验证，环度贴牌了我们之后，做了一些差异化优势宣传其中包括就是，我们的证书可以除了80/443以外更灵活的去验证，就此引来了CBA论坛上的一个公开讨论。

讨论组地址如下：https://groups.google.com/a/mozilla.org/g/dev-security-policy/c/QTs1PQfZOBE



### **时间线**

所有时间戳均为北京时间 

 ● **2023-06-22 11:00**  万维信在例行检查中发现 cab讨论组中有一篇关于SHECA证书的讨论，讨论环度对外的一篇文章宣传可通过除80和443端口的其他端口对IP地址做验证，并且对方对我们的CPS描述有一些疑问。

● **2023-06-22 16:20**  立刻排查，发现按照BR描述使用22和25端口是合理的 不过确实存在一定歧义，且我们了解到globalsign和sectigo也是支持22和25端口的，当时对这个端口的定义就是参考gloabasign的

BR的原文如下



```
Confirming the Applicant’s control over the requested IP Address by confirming the presence of a Request Token or Random Value contained in the content of a file or webpage in the form of a meta tag under the “/.well‐known/pki‐validation” directory, or another path registered with IANA for the purpose of validating control of IP Addresses, on the IP Address that is accessible by the CA via HTTP/HTTPS over an Authorized Port. The Request Token or Random Value MUST NOT appear in the request.
If a Random Value is used, the CA SHALL provide a Random Value unique to the certificate request and SHALL not use the Random Value after the longer of
i. 30 days or
ii. if the Applicant submitted the certificate request, the time frame permitted for reuse of validated information relevant to the certificate (such as in Section 4.2.1 of this document).
```

```
通过确认在IP地址的内容中存在在文件或网页的形式的“/.well-known/pki-validation”目录下的meta标签中的请求令牌或随机值，或者在用于验证IP地址控制的目的的另一个由IANA注册的路径，来确认申请人对请求的IP地址的控制权。该IP地址可通过HTTP/HTTPS在CA上通过授权端口访问。请求令牌或随机值不得出现在请求中。
如果使用随机值，CA应提供一个对证书请求唯一的随机值，并且不得在以下时间之后使用随机值：
i. 30天，
ii. 如果申请人提交了证书请求，则在与证书相关的验证信息可重用的时间范围内（如本文档的第4.2.1节）。
```

**根据BR中的定义 授权端口指的是** **80(http)、443(https)、25(smtp)、22(ssh)**

**http和https的默认端口是80和443，所以按照BR的描述我们使用25和22是符合规定的。**

● **2023-06-23 01:00**  我和和何总商量过，我们不正面回答这个端口的问题，一方面不想由此话题引来更多的关注和讨论，另一方面这个是BR的定义模糊SHECA没办法去正面给出答复。

回复的表达意愿是：

​            1、     我们严格符合BR要求在做

​            2、     环度只是代理商他们发表了和实际不符的营销文章我们已经要求他们处理整改删除。

​            3、     我们不公开讨论我们怎么做，具体可以以我们披露的cps为准，然后引导了对方去看我们的cps，并解答了对方对我们CPS的疑问。

并发布了回复

回复原文如下：

```
感谢Aaron Gable的关注。SHECA在看到您的评论后立刻检查了我们的CPS内容。SHECA最新的CPS地址为：https://assets-cdn.sheca.com/documents/sheca-certification-practice-statement-en-v3.6.3.pdf。

1.SHECA未在CPS声明使用BR中的3.2.2.5.4对IP进行验证，因为该方法已于2019年7月31日被禁止。

2.SHECA的CPS中第3.2.6章节描述了SHECA的IP验证方式，其中第二条的（1）和（2）对应BR中的3.2.2.5.1章节，（3）对应BR中的3.2.2.5.3章节。

环度是SHECA的经销商（代理商），环度不具备任何签发、审核SSL证书的权限和职责，SHECA的SSL证书签发流程严格遵守BR的规定，所有关于SSL证书审核和验证规则对外披露均应在SHECA的CPS中进行，不存在任何其他披露渠道。本次环度未经SHECA同意擅自发布不符合实际的营销文章，我们已紧急联系环度处理。

希望能解答您的疑惑！
```

● **2023-06-24 09:00** 我们发现CPS的中英文版本不一致且描述不清晰，我回复的时候参考的中文，发现后立刻要求合规部门立刻排查BR并整改，并在重新回复对方。



**目前状态：继续跟进，但是仅回复CPS相关的问题 端口问题不做正面回复，等待CAB人员给出正面答复。**



### **整改项**

| 目前环度所有关于定制产品营销的文章已全部下线，需要发出的都已发给我们在审核 |
| ------------------------------------------------------------ |
| 后续所有合作商对外的产品宣传稿件必须由SHECA核查              |
| 要求合规部门必须保证CPS的准确性                              |

### 

### **思考**

在业务扩展的过程中，一定要做好对自身不限于产品层面的风险把控，包括销售测、市场测。
