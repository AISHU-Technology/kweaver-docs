# HTTP响应状态码

## 1XX

​        这一类型的状态码，代表请求已被接受，需要继续处理。这类响应是临时响应，只包含状态行和某些可选的响应头信息，并以空行结束。由于HTTP/1.0协议中没有定义任何1xx状态码，所以除非在某些试验条件下，服务器禁止向此类客户端发送1xx响应。这些状态码代表的响应都是信息性的，标示客户应该采取的其他行动。

| 状态码 | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| 100    | HTTP **`100 Continue`** 信息型状态响应码表示目前为止一切正常，客户端应该继续请求，如果已完成请求则忽略。 |
| 101    | HTTP **`101 Switching Protocol`**（协议切换）状态码表示服务器应客户端升级协议的请求（[`Upgrade` (en-US)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Upgrade)请求头）正在切换协议。 |
| 103    | **`103 Early Hints`** 信息状态响应码，一般和 [`Link`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Link) header（首部）一起使用，来允许用户在服务器还在准备响应数据的时候预加载一些资源。 |

## 2XX

​      这一类型的状态码，代表请求已成功被服务器接收、理解、并接受。

| 状态码 | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| 200    | 状态码 **`200 OK`** 表明请求已经成功。默认情况下状态码为 200 的响应可以被缓存。 |
| 201    | 在 HTTP 协议中，**`201 Created`** 是一个代表成功的应答状态码，表示请求已经被成功处理，并且创建了新的资源。新的资源在应答返回之前已经被创建。同时新增的资源会在应答消息体中返回，其地址或者是原始请求的路径，或者是 [`Location`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Location) 首部的值。 |
| 202    | 在 HTTP 协议中，**`102 Processing`** 状态码向客户端表示已收到完整请求，并且服务器正在处理该请求。（已废弃） |
| 203    | 在 HTTP 协议中，响应状态码 **`203 Non-Authoritative Information`** 表示请求已经成功被响应，但是获得的负载与源头服务器的状态码为 [`200`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status/200) (`OK`) 的响应相比，经过了拥有转换功能的 [proxy](https://developer.mozilla.org/zh-CN/docs/Glossary/Proxy_server)（代理服务器）的修改。 |
| 204    | HTTP **`204 No Content`** 成功状态响应码，表示该请求已经成功了，但是客户端客户不需要离开当前页面。默认情况下 204 响应是可缓存的。一个 [`ETag`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/ETag) 标头包含在此类响应中。 |
| 205    | 在 HTTP 协议中，响应状态码 **`205 Reset Content`** 用来通知客户端重置文档视图，比如清空表单内容、重置 canvas 状态或者刷新用户界面。 |
| 206    | HTTP **`206 Partial Content`** 成功状态响应代码表示请求已成功，服务器已经成功处理了部分GET请求。类似于FlashGet或者迅雷这类的HTTP 下载工具都是使用此类响应实现断点续传或者将一个大文档分解为多个下载段同时下载。 |

## 3XX

​        这类状态码代表需要客户端采取进一步的操作才能完成请求。通常，这些状态码用来重定向，后续的请求地址（重定向目标）在本次响应的Location域中指明。

​        当且仅当后续的请求所使用的方法是GET或者HEAD时，用户浏览器才可以在没有用户介入的情况下自动提交所需要的后续请求。客户端应当自动监测无限循环重定向（例如：A→B→C→……→A或A→A），因为这会导致服务器和客户端大量不必要的资源消耗。按照HTTP/1.0版规范的建议，浏览器不应自动访问超过5次的重定向。

| 状态码 | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| 300    | **`300 Multiple Choices`** 是一个用来表示重定向的响应状态码，表示该请求拥有多种可能的响应。用户代理或者用户自身应该从中选择一个。由于没有如何进行选择的标准方法，这个状态码极少使用。 |
| 301    | HTTP **`301 Moved Permanently`** 说明请求的资源已经被移动到了由 [`Location`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Location) 头部指定的 url 上，是固定的不会再改变。搜索引擎会根据该响应修正。 |
| 302    | HTTP **`302 Found`** 重定向状态码表明请求的资源被暂时的移动到了由该 HTTP 响应的响应头 [`Location`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Location) 指定的 URL 上。浏览器会重定向到这个 URL，但是搜索引擎不会对该资源的链接进行更新 |
| 303    | HTTP **303 See Other** 重定向状态码，通常作为 [`PUT`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/PUT) 或 [`POST`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/POST) 操作的返回结果，它表示重定向链接指向的不是新上传的资源，而是另外一个页面，比如消息确认页面或上传进度页面。而请求重定向页面的方法要总是使用 [`GET`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET)。 |
| 304    | HTTP **`304 Not Modified`** 说明无需再次传输请求的内容，也就是说可以使用缓存的内容。这通常是在一些安全的方法（[safe](https://developer.mozilla.org/zh-CN/docs/Glossary/Safe)），例如[`GET`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET) 或[`HEAD`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/HEAD) 或在请求中附带了头部信息： [`If-None-Match`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/If-None-Match) 或[`If-Modified-Since`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/If-Modified-Since)。如果是 [`200`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status/200) `OK` ，响应会带有头部 [`Cache-Control`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Cache-Control), [`Content-Location`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Location), [`Date`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Date), [`ETag`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/ETag), [`Expires`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Expires)，和 [`Vary`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Vary)。 |
| 307    | [HTTP](https://developer.mozilla.org/zh-CN/docs/Glossary/HTTP) **`307 Temporary Redirect`**，临时重定向响应状态码，表示请求的资源暂时地被移动到了响应的 [`Location`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Location) 首部所指向的 URL 上。 |
| 308    | 在 HTTP 协议中， **308 Permanent Redirect**（永久重定向）是表示重定向的响应状态码，说明请求的资源已经被永久的移动到了由 [`Location`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Location) 首部指定的 URL 上。浏览器会进行重定向，同时搜索引擎也会更新其链接（用 SEO 的行话来说，意思是“链接汁”（link juice）被传递到了新的 URL）。在重定向过程中，请求方法和消息主体不会发生改变，然而在返回 [`301`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status/301) 状态码的情况下，请求方法有时候会被客户端错误地修改为 [`GET`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET) 方法。 |

## 4XX

​         这类的状态码代表了客户端看起来可能发生了错误，妨碍了服务器的处理。除非响应的是一个HEAD请求，否则服务器就应该返回一个解释当前错误状况的实体，以及这是临时的还是永久性的状况。这些状态码适用于任何请求方法。浏览器应当向用户显示任何包含在此类错误响应中的实体内容。

​        如果错误发生时客户端正在传送数据，那么使用TCP的服务器实现应当仔细确保在关闭客户端与服务器之间的连接之前，客户端已经收到了包含错误信息的数据包。如果客户端在收到错误信息后继续向服务器发送数据，服务器的TCP栈将向客户端发送一个重置数据包，以清除该客户端所有还未识别的输入缓冲，以免这些数据被服务器上的应用程序读取并干扰后者。

| 状态码 | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| 400    | 超文本传输协议（HTTP）**400 `Bad Request`** 响应状态码表示服务器因某些被认为是客户端错误的原因（例如，请求语法错误、无效请求消息格式或者欺骗性请求路由），而无法或不会处理该请求。 |
| 401    | 状态码 **`401 Unauthorized`** 代表客户端错误，指的是由于缺乏目标资源要求的身份验证凭证，发送的请求未得到满足。 |
| 402    | **`402 Payment Required`** 是一个被保留使用的非标准客户端错误状态响应码。 |
| 403    | 状态码 **`403 Forbidden`** 代表客户端错误，指的是服务器端有能力处理该请求，但是拒绝授权访问。 |
| 404    | HTTP 响应状态码 **`404 Not Found`** 指的是服务器无法找到所请求的资源。返回该响应的链接通常称为坏链（broken link）或死链（dead link），它们会导向链接出错处理（[link rot](https://zh.wikipedia.org/wiki/失效連結)）页面。 |
| 405    | 状态码 **`405 Method Not Allowed`** 表明服务器禁止了使用当前 HTTP 方法的请求。 |
| 406    | HTTP 协议中的 **`406 Not Acceptable`** 状态码表示客户端错误，指代服务器端无法提供与 [`Accept-Charset`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Accept-Charset) 以及 [`Accept-Language`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Accept-Language) 消息头指定的值相匹配的响应。 |
| 407    | 状态码 **`407 Proxy Authentication Required`** 代表客户端错误，指的是由于缺乏位于浏览器与可以访问所请求资源的服务器之间的代理服务器（[proxy server](https://developer.mozilla.org/zh-CN/docs/Glossary/Proxy_server) ）要求的身份验证凭证，发送的请求尚未得到满足。 |
| 408    | 响应状态码 **`408 Request Timeout`** 表示服务器想要将没有在使用的连接关闭。一些服务器会在空闲连接上发送此信息，即便是在客户端没有发送任何请求的情况下。 |
| 409    | 响应状态码 **`409 Conflict`** 表示请求与服务器端目标资源的当前状态相冲突。 |
| 410    | HTTP **`410 Gone`** 说明请求的目标资源在原服务器上不存在了，并且是永久性的丢失。如果不清楚是否为永久或临时的丢失，应该使用[`404`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status/404) |
| 411    | 响应状态码 **`411 Length Required`** 属于客户端错误，表示由于缺少确定的[`Content-Length`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Length) 首部字段，服务器拒绝客户端的请求。 |
| 412    | 在 HTTP 协议中，响应状态码 **412 Precondition Failed**（先决条件失败）表示客户端错误，意味着对于目标资源的访问请求被拒绝。这通常发生于采用除 [`GET`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET) 和 [`HEAD`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/HEAD) 之外的方法进行条件请求时，由首部字段 [`If-Unmodified-Since`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/If-Unmodified-Since) 或 [`If-None-Match`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/If-None-Match) 规定的先决条件不成立的情况下。这时候，请求的操作——通常是上传或修改文件——无法执行，从而返回该错误状态码。 |
| 413    | HTTP 响应状态码 **`413 Content Too Large`** 表示请求主体的大小超过了服务器愿意或有能力处理的限度，服务器可能会关闭连接或返回 [`Retry-After`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Retry-After) 标头字段。 |
| 414    | 响应码 **`414 URI Too Long`** 表示客户端所请求的 URI 超过了服务器允许的范围。 |
| 415    | **`415 Unsupported Media Type`** 是一种 HTTP 协议的错误状态代码，表示服务器由于不支持其有效载荷的格式，从而拒绝接受客户端的请求。 |
| 416    | HTTP **`416 Range Not Satisfiable`** 错误状态码意味着服务器无法处理所请求的数据区间。最常见的情况是所请求的数据区间不在文件范围之内，也就是说，[`Range`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Range) 首部的值，虽然从语法上来说是没问题的，但是从语义上来说却没有意义。 |
| 417    | HTTP 协议中的 **`417 Expectation Failed`** 状态码表示客户端错误，意味着服务器无法满足 [`Expect`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Expect) 请求消息头中的期望条件。 |
| 421    | HTTP **`421 Misdirected Request`** 客户端错误响应状态码表明，请求被定向到一个无法生成响应的服务器。如果连接被重复使用或选择了其他服务，就有可能出现这种情况。 |
| 422    | HTTP 422 状态码表示服务器理解请求实体的内容类型，并且请求实体的语法是正确的，但是服务器无法处理所包含的指令。 |
| 423    | HTTP **`423 Locked`** 错误响应状态码表示暂定目标资源被*锁定*，即无法访问。其内容应包含一些 WebDAV XML 格式的信息。 |
| 424    | HTTP **`424 Failed Dependency`** 客户端错误响应代码表明，由于请求的操作依赖于另一个操作，且该操作失败，因此无法在资源上执行该方法。 |
| 429    | 在 HTTP 协议中，响应状态码 **`429 Too Many Requests`** 表示在一定的时间内用户发送了太多的请求，即超出了“频次限制”。 |
| 431    | 响应码 **`431 Request Header Fields Too Large`** 表示由于请求中的首部字段的值过大，服务器拒绝接受客户端的请求。客户端可以在缩减首部字段的体积后再次发送请求。 |
| 451    | **`451 Unavailable For Legal Reasons`**（因法律原因不可用）是一种 HTTP 协议的错误状态代码，表示服务器由于法律原因，无法提供客户端请求的资源，例如可能会导致法律诉讼的页面。 |

## 5XX

​       表示服务器无法完成明显有效的请求。这类状态码代表了服务器在处理请求的过程中有错误或者异常状态发生，也有可能是服务器意识到以当前的软硬件资源无法完成对请求的处理。除非这是一个HEAD请求，否则服务器应当包含一个解释当前错误状态以及这个状况是临时的还是永久的解释信息实体。浏览器应当向用户展示任何在当前响应中被包含的实体。这些状态码适用于任何响应方法。

| 状态码 | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| 500    | 在 HTTP 协议中，**`500 Internal Server Error`** 是表示服务器端错误的响应状态码，意味着所请求的服务器遇到意外的情况并阻止其执行请求。 |
| 501    | HTTP **`501 Not Implemented`** 服务器错误响应码表示请求的方法不被服务器支持，因此无法被处理。服务器必须支持的方法（即不会返回这个状态码的方法）只有 [`GET`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET) 和 [`HEAD`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/HEAD)。 |
| 502    | **`502 Bad Gateway`** 是一种 HTTP 协议的服务端错误状态代码，它表示作为网关或代理的服务器，从上游服务器中接收到的响应是无效的。 |
| 503    | **`503 Service Unavailable`** 是一种 HTTP 协议的服务器端错误状态代码，它表示服务器尚未处于可以接受请求的状态。 |
| 504    | **`504 Gateway Timeout`** 是一种 HTTP 协议的服务器端错误状态代码，表示扮演网关或者代理的服务器无法在规定的时间内获得想要的响应。 |
| 505    | **`505 HTTP Version Not Supported`** 是一种 HTTP 协议的服务器端错误状态代码，表示服务器不支持请求所使用的 HTTP 版本。 |
| 506    | HTTP 协议的 **`506 Variant Also Negotiates`** 响应状态码 可以在 TCN（透明内容协商，见 RF2295）上下文给出。TCN 协议允许客户端取回给定资源的最佳变量/变元，这里服务器支持多个变量/变元。 |
| 511    | **`511 Network Authentication Required`** 是一种 HTTP 协议的错误状态代码，表示客户端需要通过验证才能使用该网络。该状态码不是由源头服务器生成的，而是由控制网络访问的拦截代理服务器生成的。 |



## 参考地址

https://developer.mozilla.org/zh-CN/docs/Web/HTTP

