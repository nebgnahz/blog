Equifax Incidents 2017
---

我觉得我的数据应该是泄露的，当然我并没有查。做了一些背景调研，好像暂时来讲，没有
什么特别值得做的补救措施。特别喜欢这篇
[文章](http://www.kalzumeus.com/2017/09/09/identity-theft-credit-reports/)，讲了
干货，基本就说泄露信息在没有造成实质性的伤害之前，不用特别担心。不过一旦受到伤害，
文章里列举了很多措施来 act professionally，包括邮件怎么写， 用 USPS 寄出，做备份，
不要虚张声势。


## 新闻

- [Equifax 可能是史上最严重的个人信息泄露](https://arstechnica.com/information-technology/2017/09/why-the-equifax-breach-is-very-possibly-the-worst-leak-of-personal-info-ever/)
- [Equifax 执行人出售股权](https://www.bloomberg.com/news/articles/2017-09-07/three-equifax-executives-sold-stock-before-revealing-cyber-hack)
- [Equifax 将面临巨额诉讼](https://www.bloomberg.com/news/articles/2017-09-08/equifax-sued-over-massive-hack-in-multibillion-dollar-lawsuit)
- [Apache Struts 陈述](https://blogs.apache.org/foundation/entry/apache-struts-statement-on-equifax)
- [Equifax 总会说你已经被影响了](https://techcrunch.com/2017/09/08/psa-no-matter-what-you-write-equifax-may-tell-you-youve-been-impacted-by-the-hack/)

## 相关数据

- 受影响人数：1 亿 4300 万（44% 的人口）
- 潜在泄露内容：姓名，社会安全号，生日，地址，驾照，银行信息，保险信息，和其他商业信息

## 可以采取的措施

### 冻结账户

1. 问题 1：身份证明，你怎么证明你是“你”在冻结账户的时候？
2. 问题 2：PIN 安全度低，冻结时虽然可以提供 PIN，但也可以 "Forgot my PIN"，然后基于你的个人信息已经泄露，别人可以轻松解冻。
5. 问题 5：PIN 安全度低，Equifax 冻结的码是[时间](https://twitter.com/webster/status/906346071210778625)，就是说你今天 2 点冻结，你的 PIN 是 0908171400.
3. 问题 3：麻烦，之后申请账户时特别麻烦：有用户之前冻结了账户，然后无法申请信用卡；要解锁时需要 **邮寄** PIN 到某个地方。
4. 问题 4：花钱，给三个机构同时冻结。解冻时候还得付钱（至少加州如此）。

不过 [FTC 是这么建议的](https://www.consumer.ftc.gov/articles/0497-credit-freeze-faqs).

### 使用 trustedidpremier 检测

[www.equifaxsecurity2017.com](www.equifaxsecurity2017.com) 使用 WordPress。 TLS
安全证书有问题。域名没有注册在 Equifax 名下。Whois 是一个不可信的信箱。他要 SSN
其中的 6 位，剩下的 3 位其实很容易才出来（区域码）。网站很像钓鱼网站（Cisco Open
DNS 检测可疑）。

另外 TrustedID Premier 的
[Terms of Use](https://trustedidpremier.com/static/terms) 之前有些问题，New York
Attorney General 有些反馈，现在网站已经更新了。不过我是看不太懂这些法律术语。

### 改 SSN？

特别慢，并且得证明已经有真实的危害，而不是潜在危害。

### Do Nothing

"Admitting I'm fucked, refusing to feed the vultures, and for all else I have
the number of a good attorney." by @jstarfish
