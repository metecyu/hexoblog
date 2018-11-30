---
title: 网站地址是否要加www
date: 2018-11-27 16:44:01
tags: 域名
id: 2018112701

---

二十年以来，一直有一个关于是否应该在网站名称前面加www的争论。到底应不应该加呢？
<!-- more -->

### 一些历史背景
尽管人们经常交替使用 "域名" 和 "主机名" 这两个词，但其实两者不太一样，我将简单的介绍一下，以便让大家理解。
作为 it 管理员, 你的网络就是你的域。给域名起一个名字是有意义的，而且dns包含了这个域。 所以你首先要注册一个域名，譬如  "example.com" . 有了域名，就可以在域名下设置相应的主机。每台网络连接的计算机都被认为是主机。为万维网文档提供服务的主机自然也会在你的域下获得主机名 "www"。因此得到了完整的域名（专业术语叫全限定域名）"www.example.com"  。 你也会对网络中其它主机做相同的操作, 无论你是否有web服务器，这就是主机在网络中的组织方式。

要转到"example.com" 域中的Web服务器，就要访问名为"www.example.com" 的主机. 随便说下，很早以前没有虚拟主机这样的东西。所有Web服务器都提供单个Web站点（至少每台主机都有自己的IP地址）。 所以大家都不会太关注主机名，只要它指向正确的IP地址就好了。

"裸域名"，即你的域名前没有"www" - 如"example.com" 在DNS术语中称为"源（the origin）"。随着万维网在1990年代中期的普及，一些管理员开始将源指向与www主机相同的IP地址。 这将允许网站访问者在其Web浏览器中仅键入"example.com" ，而不是完整的主机名"www.example.com" 。

### seo（搜索引擎优化）来了
由于源"example.com" 和主机名"www.example.com" 可以指向不同的IP地址，并且自1997年1月以来，在同一IP的主机上可以部署多个网站， 
做seo专家推荐我们最好选择一个规范的主机名，将源地址跳转至www的主机上（使用HTTP 301响应代码）。



### 人类对URL的理解
2000年前后，我在一家营销机构工作，当时一直比较担心如果我们遗漏了"www"，人们会不会不知道它是万维网地址。譬如刚刚开始省略"http://"的时候。 由于这些问题，我个人更喜欢使用完整的主机名，如"www.example.com" 。

今天，我认为这根本不是一个问题。只要网站使用常用的顶级域名，人们就能理解这是不是一个web地址，无论加不加www。因为多个主机域名可以指向同一台主机。如果你的规范主机名是"www.example.com" 并且你在印刷广告中仅使用"example.com" 并不重要，因为它看起来更好。 但是，如果你使用新的顶级域名，例如.beer，那最好包含www，这样更容易理解。

### 不带www的网址更漂亮，更容易
我不得不不承认："example.com" 比"www.example.com" 更短，所以读、写都更便捷。 所以人们开始放弃"www"部分，只是输入原地址，这样也更容易理解。

### 为什么加不加www还是一个问题？
为什么我们还在讨论这个问题，人们不能只使用他们喜欢的东西吗，and the rest of us leave them to it?
是的，当然可以。
但你看，如果你是一个网站管理员，你要考虑清楚再做决定。因为与互联网上的大多数事情一样，当我们开始使用它们时，并非所有事情都被考虑过，比如cookies。

### cookie 被传递到子域

从主域名设置的 cookie 也将被发送到所有子域。也就是说, 如果 "example..com"   上的网站设置了 cookie, 浏览器在访问 "www.example.com"   时也会发送此 cookie。听起来是件好事, 因为反正是同一个网站, 对吧？但cookie 也会被送到 "cdn.example.com"  、"email.example.com"  、"intranet.example.com"  、thirdpartyservice.example.com 等。而且当第三方服务使用你的域名是，也会获取主域名的cookie。

而在"www.example.com"   中设置的 cookie 将不会发生上述问题，"同级" 主机上不会获得www的cookie数据。因为你的浏览器认为它们不是 "子服务", 而是完全不同的服务, 不应访问你的 cookie。



### 不必要的 cookie 会影响性能

http 和 cookie 的工作方式是这样的, cookie会从浏览器发送至web服务器（每个请求都会发送）。这意味着, 如果你的网站对原点设置了 cookie ("example..com"  ), 则此cookie属性还会向发送给"email.example.com"   或 "intranet.example.com"  的请求一起提交 。这会减慢通信速度, 用户体验更差。

本段落可能翻译的不好，附上原文:
> The way HTTP and cookies work, is that they are sent from the browser for each and every request to the web server. This means that if your website sets a cookie for the origin ("example.com" ) this cookie will also have to be sent to every request that you make to e.g. "email.example.com"  or "intranet.example.com" . This slows down the communication and leaves your with a worse user experience.


### Cookie可以由第三方阅读。 

如果你的网站位于主域名（"example.com" ）并已登录到CMS，CMS将向浏览器发出cookie，以便登录会话。然后，当你访问"someinternalservice.example.com" 时，该服务的管理员可以读取该cookie，并复制它，可以使用它作为你登录到公司CMS。同理，访问"email.example.com" 时，电子邮件服务供应商也能拿到CMS的cookie。访问"cdn.example.com" 时CDN供应商也如此，其它类似的子域名也一样。

如果你担心"example.com" 上设置cookie有隐患，还是建议你在网址前面加一个"www"。cookie是神奇的特性。HTTPS和2FA都没有用。其他安全措施，如IP限制（ IP restrictions）可能有所帮助。


### 如果你愿意，可以共享子域中的Cookie
现在，如果你在子域上有个服务，例如 "sso.example.com" ，根据RFC 6265（cookie标准）你可以对主域名设置cookie并与"example.com" 或 "www.example.com"  共享。 因此避免将"裸域"作为主机名，实际上为你提供了更大的灵活性（灵活度是指每个子域名操作自己的cookie，不会相互影响）。


### DNS主域不能是CNAME 
谈到灵活性，我们不得不再回到DNS。 
DNS中有一个限制，即来源必须是A类型记录，这意味着它必须指向固定的IP地址。 
当你的站点变大并将其移动到托管服务，或者想要将其指向Web应用程序、防火墙或DDoS缓冲区时，你可能希望使用CNAME类型的记录，将主机名指向供应商的另一个灵活主机名 根据你的流量和需求进行管理。

现在，如果你的网站托管在源地址（ "example.com" ），则无法执行此操作。 但是"www"的主机名可以作为CNAME记录。因此，如果想要更大的扩展性、灵活性，无论是现在还是将来，你都应该使用www主机名。

### 结论：请使用www
无论你是否使用www，这都很重要。我同意原始域名看起来更漂亮，但这只是浏览器本身地址栏中的实际问题。 你可以使用"www.example.com" 作为规范主机名，但在其他任何地方，你都可以使用裸域。 无论如何，它会将用户重定向到正确的位置。
一些重要的事情表明你应该使用完整的主机名和www：譬如：性能，安全性，灵活性。
应该结束用不用www的争论了，去用www吧。

[原文:To www or not to www](https://bjornjohansen.no/www-or-not?utm_source=wanqu.co&utm_campaign=Wanqu+Daily&utm_medium=website)
