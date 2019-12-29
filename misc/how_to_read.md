# 如何阅读 RFC 文件

[mnot]: https://www.mnot.net/
[how_to_read]: https://www.mnot.net/blog/2018/07/31/read_rfc

*本文译自 [How to Read an RFC][how_to_read], [mnot’s blog (Mark Nottingham)][mnot]*

无论好坏，“请求意见稿”（RFCs）为我们指明了许多与互联网有关的协议。这些文档被陷入其中寻找隐含意义的开发者视为圣经，然后又由于它们不易被理解而被回避，被认为无关紧要。这常常会引起挫败感，更甚者引发互通性问题与安全性问题。

[mark_nottingham]: https://datatracker.ietf.org/person/Mark%20Nottingham

然而，通过了解它们的构造和发布流程，可以更轻松地理解你正在查阅的内容。这是我自身的经验，是在我对 HTTP 和一些 [其他信息][mark_nottingham] 的了解过程中体会到的。

## 从哪儿开始？

[rfc_editor]: https://www.rfc-editor.org/
[ietf_tools]: https://tools.ietf.org/

[RFC Editor][rfc_editor] 是查找 RFC 文档的权威网站。不过正如我们将在下面看到的那样，这里缺少一些关键信息，因此大多数人都选择使用 [tools.ietf.org][ietf_tools]。

由于 RFC 文件数量太多（目前将近 9,000 个！），仅仅是找到正确的 RFC 也是很困难的。显然你可以使用普通的 Web 搜索引擎查找它们，RFC Editor 在其站点上也有出色的搜索功能。

[every_rfc]: https://everyrfc.org/

另一个选项是 [EveryRFC][every_rfc]，在这里可以按 RFC 文档的标题、关键字搜索，也可以直接选定某些标签进行探索。

[rfc_format]: https://www.rfc-editor.org/rse/format-faq/
[greenbytes]: https://greenbytes.de/tech/webdav/
[wiki_webdav]: https://zh.wikipedia.org/wiki/%E5%9F%BA%E4%BA%8EWeb%E7%9A%84%E5%88%86%E5%B8%83%E5%BC%8F%E7%BC%96%E5%86%99%E5%92%8C%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6
[http_group]: https://httpwg.org/specs/

毫无疑问，纯文本、格式丑陋的 RFC 文件难以阅读，不过这一点总算将被改变；RFC Editor 正在设计更美观、可定制的新 [RFC 格式][rfc_format]。同时，如果你想要的是可用性更高的 RFC 文件，可以选择使用第三方存储库来查阅；例如，[greenbytes][greenbytes] 维护了一个与 WebDAV（[基于 Web 的分布式编写和版本控制][wiki_webdav]）相关的 RFC 文件列表，[HTTP Working Group][http_group] 则维护与 HTTP 相关的列表。

## 这份 RFC 是什么样的？

所有的 RFC 文件顶部都有如下横幅：

```Text
Internet Engineering Task Force (IETF)                  R. Fielding, Ed.
Request for Comments: 7230                                         Adobe
Obsoletes: 2145, 2616                                    J. Reschke, Ed.
Updates: 2817, 2818                                           greenbytes
Category: Standards Track                                      June 2014
ISSN: 2070-1721
```

[indepent_stream]: https://www.rfc-editor.org/about/independent/

最左上角的 “Internet Engineering Task Force (IETF)（互联网工程任务组）” 表明这是 IETF 的产物；尽管并不广为人知，还是有其他方法可以发布无需获得 IETF 认可的 RFC 文件；例如，[独立提交流程][indepent_stream]。

事实上存在着很多“流（stream）”可以用来发布文档。**只有 IETF 流表明协议规范已经经过整个 IEFT 组织审核并做出共识声明**。

较早的文档（大约在 RFC5705 之前）中最左上角写的是“Network Working Group（网络工作组）”，因此你需要多花一点时间才能确定它们是否代表 IETF 共识；请参阅“Status of this Memo（此备忘录的状态）”部分，也可以查阅 [RFC Editor 网站][rfc_editor]。

[datatracker]: https://datatracker.ietf.org/submit/

在此下方是“请求意见稿”编号。**如果显示的是“Internet-Draft（互联网草案）”，则它不是 RFC**；这只是一个建议，*任何人*都 [可以写一个][datatracker]。仅凭某些文档是互联网草案并不意味着它会被 IETF 所采用。

*类别*可以是“Standards Track（标准记录）”、“Informational（报告性的）”、“Experimental（实验性的）”和“Best Current Practice（最佳现行实践）”其中之一。它们之间的区别有时是模糊的，但如果是 IETF 产出的（请参见上文），则表明已经经过合理的评审。但是请注意，即使经过 IETF 共识发布，报告性的和实验性的文件也*不是*标准。

最后，文档的**作者**列在标题的右侧。与学术界不同，这不是谁为文档做出了贡献的完整列表；通常，完整贡献列表是在“致谢”部分的末尾完成的。在 RFC 文档中，这实际上指的是“编写文档的人”。通常，你会看到追加在名字后面的“Ed.”。这表明他们是编辑者，通常是因为文本原先已存在（例如修订 RFC 时）。

## 它是最新的吗？

[diff_7158_7159]: https://tools.ietf.org/rfcdiff?url1=rfc7158&url2=rfc7159

RFC 是系列文档的存档；它们甚至连一个字符都不能改变（请参阅 [RFC7158 和 RFC7159 之间的差异对比][diff_7158_7159] 以查看极端效果示例；它们搞错了年份 ;）。

因此，重要的是要知道你看到的是正确的文档。头部横幅包含了一些元数据，它们发挥以下作用：

- **Obsoletes**（过时列表）列出了被本文档完全替代的 RFC 文件；也就是说，你应该使用此文档，而不要使用 Obsoletes 指出的文档。需要注意的是，新版本的协议不一定会淘汰旧版本的协议；例如 HTTP/2 不会替代 HTTP/1.1，因为它仍然是旧协议的合法（也是必要的）规范。但是，RFC7230 的确淘汰了 RFC2616，因为它是该协议（HTTP/1.1）新的标准。
- **Updates**（更新列表）列出了被本文档实质性改变了的 RFC，换句话说，如果你正在阅读更新列表的文档，则也应该阅读本文档。

[rfc_2616]: https://tools.ietf.org/html/rfc2616

不幸的是，纯 ASCII 文本的 RFC 文件（例如 RFC Editor 上面的 RFC）无法告知你哪些文档更新或淘汰了你当前正在阅读的文档。这就是大多数人选择使用 tools.ietf.org 的 RFC 存储库的原因，它将这些信息放在 [如下的文件头部横幅中][rfc_2616]：

```text
[Docs] [txt|pdf] [draft-ietf-http...] [Tracker] [Diff1] [Diff2] [Errata]

Obsoleted by: 7230, 7231, 7232, 7233, 7234, 7235          DRAFT STANDARD
Updated by: 2817, 5785, 6266, 6585                          Errata Exist
```

工具页面上的每个数字都是一个链接，因此你可以轻松找到最新的文档。

即使是最新的 RFC 也经常出现问题。在工具横幅中，你还会在右侧看到“Errata Exist（存在勘误）”的警告，以及位于其上方的勘误链接。

**勘误**是在没必要发布新 RFC 文件时对相应文档的更正和澄清。有时，它们可能会对 RFC 的实施方式产生重大影响（例如规范中的错误导致重大误解），因此值得一读。

[errata_7230]: https://www.rfc-editor.org/errata_search.php?rfc=7230

例如这是 [RFC7230 的勘误表][errata_7230]。阅读勘误表时，请牢记其状态；许多人因为误读规范导致提交的勘误被否决了。

## 理解上下文

对于开发者来说，查看 RFC 并实施他们所看到的内容，却执行了与作者意图相反的操作，这种情况比你想像的要普遍得多。

这是因为在读者选择性阅读（就像读任何“圣经”一样）时，要以一种不被误读的方式编写规范是很困难的。

结果就是，不仅需要阅读直接相关的文本，（至少）阅读其引用的任何内容也是有必要的，无论是否在同一份规范中。假如你是在紧要关头，即使无法阅读整个文档，阅读所有可能相关的部分也会大有帮助。

[http_crlf]: https://httpwg.org/specs/rfc7230.html#http.message
[http_lf]:https://httpwg.org/specs/rfc7230.html#message.robustness

例如，HTTP 消息头部被 [定义][http_crlf] 为由 CRLF 分隔，但是如果你跳过这部分文档到 [这里][http_lf]，显而易见你还是会看到“a recipient MAY recognize a single LF as a line terminator and ignore any preceding CR.（接收端**也许**会将 LF 符作为行分隔符，并忽略前面的 CR 符。）”的提示。

[iana]:https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%8F%B7%E7%A0%81%E5%88%86%E9%85%8D%E5%B1%80
[http_registry]: https://www.iana.org/assignments/http-methods/http-methods.xhtml

另一点需要谨记的是，许多协议都设置了 IANA（[Internet Assigned Numbers Authority，互联网号码分配局][iana]）登记列表管理它们的规范扩展；这些才是事实标准的来源，而不是规范文档。例如，HTTP 方法的权威列表包含在这个 [登记表][http_registry]中，而不是在 HTTP 规范文档中。

## Interpreting Requirements

Almost all RFCs have boilerplate that looks something like this near the top:

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
"OPTIONAL" in this document are to be interpreted as described in
BCP 14 [RFC2119] [RFC8174] when, and only when, they appear in all
capitals, as shown here.
These RFC2119 keywords help define interoperability, but they also sometimes confuse developers. It’s very common to see a specification say something like:

The Foo message MUST NOT contain a Bar header.
This requirement is placed upon a protocol artefact, the” Foo message”. If you’re sending one, it’s pretty clear it needs to not contain a Bar header; if you include one, it won’t be a conformant message.

However, the behaviour of the recipient is much less clear; if you see a Foo message with a Bar header, what do you do?

Some developers will reject a message that contains it, even though the specification says nothing about doing so. Others will still process the message, but strip the Bar header, or ignore it – even when the spec explicitly says that all headers need to be processed.

All of these things can – unintentionally – cause interoperability issues. The correct thing to do is to follow normal processing for the header unless there’s a specific requirement to the contrary.

That’s because in general, specifications are written so that behaviours are overtly specified; in other words, everything that is not explicitly disallowed is allowed. Therefore, reading too much into specifications can unintentionally cause harm, since you’ll be introducing new behaviours that others will have to work around.

In an ideal world, the specification would be defined in terms of the behaviours of those who handle the message, like this:

Senders of the Foo message MUST NOT include a Bar header. Recipients
of a Foo message that includes a Bar header MUST ignore the Bar header,
but MUST NOT remove it.
Absent that, it’s best to look for more general advice about error handling elsewhere in the specification (e.g., HTTP’s Conformance and Error Handling section).

Also, keep in mind the target of requirements; most specifications have a highly developed set of terms that they use to distinguish between different roles in the protocol.

For example, HTTP has proxies, which are a kind of intermediary, which implement both a client and a server (but not a User-Agent or an origin server); they need to pay attention to requirements targeted at all of those roles.

Likewise, HTTP distinguishes between “generating” a message and merely “forwarding” it in some requirements, depending on the specific situation. Paying attention to this kind of specific terminology can save you a lot of guesswork.

### SHOULD

Yep, SHOULD deserves its own section. This wishy-washy term plagues many RFCs, despite efforts to eradicate it. RFC2119 describes it as:

SHOULD  This word, or the adjective "RECOMMENDED", mean that there
        may exist valid reasons in particular circumstances to ignore a
        particular item, but the full implications must be understood and
        carefully weighed before choosing a different course.
In practice, authors often use SHOULD and SHOULD NOT to mean “We’d like you to do this, but we know we can’t always require it.”

For example, in the overview of HTTP methods, we see:

When a request method is received that is unrecognized or not
implemented by an origin server, the origin server SHOULD respond
with the 501 (Not Implemented) status code. When a request method
is received that is known by an origin server but not allowed for
the target resource, the origin server SHOULD respond with the 405
(Method Not Allowed) status code.
These SHOULDs are not MUSTs because the server might reasonably decide to take another action; if the request is from a client that is believed to be an attacker, it might drop the connection, or if HTTP authentication is required for the resource, it might enforce that with a 401 (Not Authenticated) before getting to the 405.

SHOULD doesn’t mean that the server is free to ignore a requirement because it doesn’t feel like honouring it.

Sometimes, we see a SHOULD that follows this form:

A sender that generates a message containing a payload body SHOULD
generate a Content-Type header field in that message unless the
intended media type of the enclosed representation is unknown to
the sender.
Notice the “unless” – it’s specifying the “particular circumstances” that the SHOULD allows. Arguably this could be specified as a MUST, since the unless clause would still apply, but this style of specification is somewhat common.

## Reading Examples

Another very common pitfall is to skim the specification for examples, and implement what they do.

Unfortunately, examples typically get the least amount of attention from authors, since they need to be updated with each change to the protocol.

As a result, they’re very often the least reliable parts of the spec. Yes, the authors should absolutely double-check the examples before publication, but errors do slip through.

Also, even a perfect example might not be intended to illustrate the aspect of the protocol you’re looking for; they’re often truncated for brevity, or shown after an decoding step takes place.

Even though it takes more time, it’s better to read the actual text; examples are not the specification.

## On ABNF

Augmented BNF is often used to define protocol artefacts. For example:

FooHeader = 1#foo
foo       = 1*9DIGIT [ ";" "bar" ]
Once you get used to it, ABNF offers an easy-to-understand sketch of what protocol elements should look like.

However, ABNF is “aspirational” - it identifies an ideal form for a message, and those messages that you generate really need to match it. It doesn’t specify what to do with received messages that fail to match it. In fact, many specifications fail to say what the relationship of ABNF is to processing requirements at all.

Most protocols will fail badly if you try to enforce their ABNF strictly, but sometimes it matters. In the example above, whitespace isn’t allowed around the semicolon, but you can bet that some people will put it there, and some implementations will accept it.

So, make sure you read the text around the ABNF for additional requirements or context, and realise that absent a direct requirement, you may have to adjust parsing to be more accepting of input than the ABNF implies.

Some specifications are starting to acknowledge the aspirational nature of ABNF and specifying explicit parsing algorithms that incorporate error handling. When specified, these should be followed exactly, to ensure interoperability.

## Security Considerations

Ever since RFC3552, the RFC boilerplate has included a “Security Considerations” section.

As a result, it’s rare for an RFC to be published without a substantial section on security; the review process does not allow a draft to just say “There are no security considerations for this protocol”.

So, it pays to read and make sure you understand the Security Considerations section, whether you’re implementing or deploying the protocol; if you don’t, it’s very likely that something will bite you down the road.

Following its references (if any) is also a good idea. If there aren’t any, try looking up some of the terms used to get an appreciation of the issues being discussed.

## Finding Out More

If an RFC doesn’t answer your question, or you’re not sure about the intent of its text, the best thing to do is to find the most relevant Working Group and ask a question on their mailing list. If there isn’t an active working group covering the topic in question, try the mailing list for the appropriate area.

Filing an errata is usually not the first step you should take – talk to someone first.

Many Working Groups are now using Github for managing their specifications; if you have a question about an active specification, go ahead and file an issue. If it’s already an RFC, it’s usually best to use the mailing list unless you find directions to the contrary.

I’m sure there’s more to write about how to read RFCs, and some will dispute what I’ve written here, but this is how I think about them. I hope it was useful.

## 译者

- [Octobug](https://github.com/Octobug)
- [Shady](https://github.com/shady-robot)
