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

毫无疑问，纯文本、格式丑陋的 RFC 文件难以阅读，不过这一点总算将被改变；RFC Editor 正在设计更美观、可定制的新 [RFC 格式][rfc_format]。同时，如果你想要的是可用性更高的 RFC 文件，可以选择使用第三方存储库来查阅；例如，[greenbytes][greenbytes] 维护了一个与 WebDAV（[基于 Web 的分布式编写和版本控制][wiki_webdav]）相关的 RFC 文件列表，[HTTP 工作组（HTTP Working Group）][http_group] 则维护与 HTTP 相关的列表。

## 这份 RFC 属于哪一类？

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

## 用语要求

几乎所有 RFC 在其顶部附近都有样板，看起来像这样：

```text
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
"OPTIONAL" in this document are to be interpreted as described in
BCP 14 [RFC2119] [RFC8174] when, and only when, they appear in all
capitals, as shown here.

本文档中的关键字 "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", 与
"OPTIONAL"，当且仅当它们的所有字母都是大写形式时，它们取的即是 BCP 14 [RFC2119]
[RFC8174] 中表述的含义。
```

[rfc_2119]: https://tools.ietf.org/html/rfc2119

这些 [RFC2119][rfc_2119] 关键字有助于定义互通性，但有时也会使开发者感到困惑。规范中有以下类似表述是常见的情况：

```text
The Foo message MUST NOT contain a Bar header.
消息 Foo 中不能包含头部 Bar。
```

该要求限制的对象是协议工件（artefact，可理解为协议的某种实现的实例，或者“协议伪实例”，相当于编程中的“伪代码”），即“Foo 消息”。如果你要发送一个该协议的实例对象，那么很显然它不应该包含 Bar 头部；如果它包含了，则它不是符合规范的消息。

但是，接收者收到后有如何行为则规定得没有那么清晰；如果你看到带有 Bar 头部的 Foo 消息，你会怎么办？

有些开发者会拒绝包含 Bar 头部的 Foo 消息，即便规范没有说明应该这样做。其他开发者可能仍将处理该消息，但是会先解析丢弃 Bar 头部，或者忽略它——即使规范中明确指出需要处理所有头部。

所有这些处理方式的差异都可能（无意间）导致互通性问题。正确的做法是遵循消息头部的常规处理，除​​非有相反的特定要求。

因为一般来说，规范会再编写时明确指出相应行为的；换句话说，未被明确禁止的行为都是被允许的。因此，过多地阅读规范可能会在无意中带来一些坏处，因为你可能引入一些其他人必须处理的新行为。

在理想情况下，规范是根据处理消息的人的行为来定义的，如下所示：

```text
Senders of the Foo message MUST NOT include a Bar header. Recipients
of a Foo message that includes a Bar header MUST ignore the Bar header,
but MUST NOT remove it.

Foo 消息的发送者不得在其中包含 Bar 头部。包含 Bar 头部的 Foo 消息的接收者必须忽略
Bar 头部，但不得移除它。
```

[http_conformance]: https://httpwg.org/specs/rfc7230.html#conformance

如果没有相关规定，最好在规范中（例如，HTTP 协议的 [一致性与错误处理][http_conformance] 部分）的其他地方寻求有关错误处理的一般建议。

另外需要记住的是要求的*目标*对象是什么；大多数规范都有一套高度完善的术语，用于区分协议中的不同角色。

[http_proxy]: https://httpwg.org/specs/rfc7230.html#intermediaries

例如，HTTP 具有 [代理][http_proxy] 的定义，它是一种中介，既实现了客户端又实现了服务器（但它不是 User-Agent 或真正的服务器）；他们需要注意针对所有这些角色的要求。

同样地，HTTP 会根据特定情况在某些要求中区分“generating（生成）”消息和仅“forwarding（转发）”消息。关注这种特定的术语可以免去大量的猜测。

### 关键字 “SHOULD”

是的，关键字 “SHOULD”值得单独说一下。尽管在去除这个关键字上面做了很多努力，这个含义模糊的词仍困扰着许多RFC 文件。RFC2119 将其描述为：

```text
SHOULD  This word, or the adjective "RECOMMENDED", mean that there
        may exist valid reasons in particular circumstances to ignore a
        particular item, but the full implications must be understood and
        carefully weighed before choosing a different course.

应该     这个词或是形容词“推荐”，它们的意思是在特定情况下可能存在正当理由而忽略特定条款，
        前提是必须理解其全部含义并在选择其他方案之前经过请仔细权衡。
```

实际上，作者经常使用“SHOULD（应该）”和“SHOULD NOT（不应该）”来表示“我们希望你这样做，但是我们知道我们并不总是要求你做到。”

[http_method_overview]: https://httpwg.org/specs/rfc7231.html#method.overview

例如，在 [HTTP 方法概述][http_method_overview] 中，我们可以看到：

```text
When a request method is received that is unrecognized or not
implemented by an origin server, the origin server SHOULD respond
with the 501 (Not Implemented) status code. When a request method
is received that is known by an origin server but not allowed for
the target resource, the origin server SHOULD respond with the 405
(Method Not Allowed) status code.

当收到无法识别或未经服务器实现的请求方法时，服务器**应该**响应状态代码 501（未
实现）。当收到一个请求方法为服务器所知但目标资源不被允许访问时，服务器**应该**
响应状态码 405（不允许的方法）。
```

这些“应该”不是必须遵守的，因为服务器也许有合理的理由决定采取其他措施；如果请求来自被认为是攻击者的客户端，则它可能会断开连接，或者说请求的资源要求使用 HTTP 身份验证，则在进入 405 之前，它可能会使用 401（未经身份验证）响应该请求。

“应该”也*不*意味着服务器就可以随意忽略规范要求，因为这让它给人一种不尊重规范的感觉。

[multipart]: https://httpwg.org/specs/rfc7231.html#multipart.types

有时我们会 [看到][multipart] “应该”遵循以下形式：

```text
A sender that generates a message containing a payload body SHOULD
generate a Content-Type header field in that message unless the
intended media type of the enclosed representation is unknown to
the sender.

在发送方生成了包含 payload（有效载荷）体的消息时，“应该”同时在该消息中头部中生
成 Content-Type 字段，除非有效载荷的媒体类型对发送方来说是未知的。
```

注意“除非”这个词——它指定了“应该”允许的“特殊情况”。可以说，可以将其指定为“必须”，因为除非子句仍然适用，但是这种规范风格较为普遍。

## 阅读规范实例

另一个非常常见的陷阱是浏览规范示例，并实现它们。

不幸的是，示例通常是作者最少关注的部分，因为需要随着协议的每次更改都要对其进行更新。

结果就是，它们通常是规范中最不可靠的部分。是的，作者绝对应该在发布之前仔细检查示例，但是疏忽总是会存在。

另外，即使是一个完美的示例，也可能并不意在说明你正在寻找的协议的各个方面；简洁起见，通常会将它们截断，或者在解码步骤之后才显示。

最好还是阅读实际的文本即使这会花费更多时间；因为示例不是规范。

## 使用 ABNF（Augmented Backus–Naur Form，增强型巴科斯-瑙尔范式）

[abnf]: https://tools.ietf.org/html/rfc5234

[增强型巴科斯-瑙尔范式][abnf] 常被用于定义协议工件实例。例如：

```text
FooHeader = 1#foo
foo       = 1*9DIGIT [ ";" "bar" ]
```

一旦你习惯了这种表示法，ABNF 会提供一个易于理解的“草图”，概述一个协议实例的结构与格式。

然而，ABNF 是“有抱负和理想化的”——它识别一条消息的理想形式，那么你生成的那些消息就需要与之完全匹配。它没有指定如何处理匹配失败的消息。实际上，许多规范都*无法*说明 ABNF 与消息处理要求之间的关系。

如果你尝试严格执行 ABNF，大多数协议都会严重失败，但有时 ABNF 的确很重要。在上面的示例中，不允许在分号周围使用空格，但是可以打赌还是会有某些人会将空格放在分号周围，并且某些协议的实现会接受它。

因此，请确保你阅读了 ABNF 周边的说明以了解其他要求或需要的上下文，假如你发现到没有直白的规范要求，你可能需要调整解析严格程度以使其比 ABNF 所暗示的更容易接受输入。

一些规范开始承认 ABNF 的理想性，并指定了包含错误处理的显式解析算法。当这些被指定时，应严格遵循这些规定，以确保互通性。

## 安全注意事项

[rfc_3552]:https://tools.ietf.org/html/rfc3552

自 [RFC3552][rfc_3552] 以来，RFC 样板就开始包含“安全注意事项”部分。

因此，很少有缺乏关于安全性的实质性部分而发布 RFC 的情况；评审过程不允许草案说“此协议没有安全注意事项”。

所以需要阅读并确保你了解“安全注意事项”部分，无论你是要实施还是部署协议；如果不这样做，那么你接下来很可能会被安全性问题困扰。

遵循其引用（如果有）也是一个好主意。如果没有，请尝试查找那些用于理解所讨论的问题的术语。

## 了解更多

[working_group]: https://datatracker.ietf.org/wg/
[ieft_area]: https://ietf.org/topics/areas/

如果 RFC 无法回答你的问题，或者你不确定其文本的意图，那么最好的办法是找到最相关的 [工作组][working_group]，并在其邮件列表中提出问题。如果没有活跃的工作组讨论相关主题，请尝试相应 [区域][ieft_area] 的邮件列表。

提交勘误表通常不是你应该采取的第一步——建议先和他人交流确认。

现在许多工作组都在使用 GitHub 来管理其规范；如果你对现行规范存在疑问，请提出问题。如果它已经成为 RFC 文件，通常最好是使用邮件列表来反馈，除非你找到其他截然相反的指示。

我相信还有更多关于如何阅读 RFC 的文章，有些人会质疑我写的这篇文章，但这就是我对它们的看法。我希望它能发挥作用。

## 译者

- [Octobug](https://github.com/Octobug)
- [Shady](https://github.com/shady-robot)
