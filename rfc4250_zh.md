# 1. 简介
这个文档没有定义任何新的协议。文档仅为SSH协议创建IANA数据库的初始状态，同时包含了未来将要分配的指令。除了一种被普遍认为过时了的HISTROIC算法外，文档没有定义任何新的协议或者编号范围。新的协议和编号范围仅在[SSH-ARCH]、[SSH-TRANS]、[SSH-USERAUTH]、[SSH-CONNECT]文件中有过定义。

# 2. 贡献者
这一系列的文档的主要原始创作者有：Tatu Ylonen, Tero Kivinen, Timo J. Rinne, Sami Lehtinen（SSH通信安全公司的所有成员），还有Markku-Juhani O. Saarinen（来自于Jyvaskyla大学)。Darren Moffat是最初的作者，做出了大量的贡献。
有许多人为这个文档做出了数以年记的付出，这些人包括Mats Andersson、Ben Harris、Bill Sommerfeld、Brent McClure、Niels Moller、Damien Miller、Derek Fawcus、Frank Cusack、Heikki Nousiainen、Jakob Schlyter、Jeff Van Dyke、Jeffrey Altman、Jeffrey Hutzelman、Jon Bright、Joseph Galbraith、Ken Hornstein、Markus Friedl、Martin Forssen、Nicolas Williams、Niels Provos、Perry Metzger、Peter Gutmann、Simon Josefsson、Simon Tatham、Wei Dai、Denis Bider、der Mouse和Tadayoshi Kohno，对这些人致以感谢。将这些人名列出来，并非是他们为这篇文档签名背书，而是他们对它做出了贡献。

# 3. 文档中涉及到的公约
## 3.1. RFC 2119中的关键词
所有的SSH协议系列的文档都将使用以下的关键词来描述所需要的条件："MUST"（必须）、"MUST NOT"（必须不）、"REQUIRED"（必需的）、"SHALL"（应该）、"SHALL NOT"（不应该）、"SHOULD"（可能）、"SHOULD NOT"（不可能）、"RECOMMENDED"（推荐）、"MAY"（也许）和"OPTIONAL"（可选）。这些关键词在[RFC2119]中有解释。
## 3.2. RFC 2434中的关键词
文档中出现的这些关键词将用来描述命名空间的分配："PRIVATE USE"(专有的)、"HIERARCHICAL ALLOCATION"(按级分配)、"FIRST COME FIRST SERVED"(先到先获取服务)、"EXPERT REVIEW"(专家审查)、"SPECIFICATION REQUIRED"（规格需求）, "IESG APPROVAL"（IESG许可）、"IETF CONSENSUS"（IETF公约）和"STANDARDS ACTION"（标准行动），这些关键词可以在RFC2434中找到解释。为了更确切的了解这些关键词的意义，文档中会对这些名次再次作出解释。
- PRIVATE USE - 仅作为私有或者局部使用，由本地站点定义其类型和目的。私有值不是为了防止多个站点采用不同（或者不兼容）的方式使用相同的值。IANA不需要去审查私有值的分配，一般来说，这些私有分配的值也不用在协同工作上。
- HIERARCHICAL ALLOCATION - 被委派的管理者在对命名空间获得控制的情况下，可以分配值。IANA根据其他策略之一，控制更高级别的命名空间。
- FIRST COME FIRST SERVED - 任何人都可以获得一个被分配的值，只需要他们提供一个接触点(联络点)并提供一个简单的描述来说明这个值将被用在什么地方。对于数字，IANA会分配一个确定的值；对于名称，通常是一个特定的名称。
- EXPERT REVIEW - 需要被指定的专家所认可。
- SPECIFICATION REQUIRED - 值和意义都必须在RFC文档中被定义，也可以引用自其他永久性的可以随时方便查阅的永久性文档。这些值的定义需要有足够的细节，以确保在各个不相关实现上可以协同工作，实现互通。
- IESG APPROVAL - 新的分配请求必须由IESG进行许可，但不是一定要符合RFC文档记录（虽然IESG有权逐案要求提供文档或其他证明材料）。
- IETF CONSENSUS - 新的值由IETF一致性过程进行分配，特别是当新的分配是由IESG许可的RFC文档生成时。通常，IESG会针对一个将要产生的分配，寻求适当的人（如果存在一个相关的工作组，则可能会向工作组获取信息）提供信息。
- STANDARDS ACTION - 这些值仅分配给IESG所许可的标准方针RFC文档。
## 3.3. 协议的字段和值
文档中定义了协议的字段以及这些字段可以被填充的值。消息定义中会对协议的字段进行规定，比如，SSH_MSG_CHANNEL_DATA消息被定义成如下格式：
```
byte    SSH_MSG_CHANNEL_DATA
uint32  recipient channel
string  data
```
文档使用单引号标记字段，使用双引号标记字段中的值。比如，字段'data'的可选值为"foo"和"bar"。
# 4. IANA 注意事项
这个文档全部是SSH协议的IANA注意事项，这些注意事项在[SSH-ARCH]、[SSH-TRANS]、[SSH-CONNECT]这些文档中都有描述。这一章节包含命名空间取名的规则、注册表的初始状态和将要分配的值的说明。
## 4.1. 消息编号
消息编号使用一个字节对数据包的负载做出声明。
### 4.1.1. 协议
协议数据包中的消息编号从1到255这255个数字中取值。这些编号按照以下方式进行分配：
- 传输层协议</br>
1 - 19 通用的传输层消息（例如断开连接、忽略、调试等等消息）</br>
20 - 29 算法协商消息</br>
30 - 49 特定的密钥交换方法（当使用不同的认证方法时，这些编号可以复用表示不同的含义）

- 用户认证协议</br>
50 - 59 通用的用户认证消息</br>
60 - 79 特定的用户认证方法（当使用不同的认证方法时，这些编号可以服用表示不同的含义）

- 连接协议</br>
80 - 89 通用的连接协议</br>
90 - 127 和通道有关的消息

- 为客户端协议保留的编号：128 - 191

- 本地扩展编号

### 4.1.2. 初始分配值
消息ID值的初始分配的值如下表所示：

| Message ID | 值 | 相关文档
|:--|:--|:--|
|SSH_MSG_DISCONNECT|1|[SSH-TRANS]|
| SSH_MSG_IGNORE | 2 | [SSH-TRANS] |
| SSH_MSG_UNIMPLEMENTED | 3 | [SSH-TRANS] |
| SSH_MSG_DEBUG | 4 | [SSH-TRANS] |
| SSH_MSG_SERVICE_REQUEST | 5 | [SSH-TRANS] |
| SSH_MSG_SERVICE_ACCEPT | 6 | [SSH-TRANS] |
| SSH_MSG_KEXINIT | 20 | [SSH-TRANS] |
| SSH_MSG_NEWKEYS | 21 | [SSH-TRANS] |
| SSH_MSG_USERAUTH_REQUEST | 50 | [SSH-USERAUTH] |
| SSH_MSG_USERAUTH_FAILURE | 51 | [SSH-USERAUTH] |
| SSH_MSG_USERAUTH_SUCCESS | 52 | [SSH-USERAUTH] |
| SSH_MSG_USERAUTH_BANNER | 53 | [SSH-USERAUTH] |
| SSH_MSG_GLOBAL_REQUEST | 80 | [SSH-CONNECT] |
| SSH_MSG_REQUEST_SUCCESS | 81 | [SSH-CONNECT] |
| SSH_MSG_REQUEST_FAILURE | 82 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_OPEN | 90 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_OPEN_CONFIRMATION | 91 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_OPEN_FAILURE | 92 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_WINDOW_ADJUST | 93 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_DATA | 94 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_EXTENDED_DATA | 95 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_EOF | 96 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_CLOSE | 97 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_REQUEST | 98 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_SUCCESS | 99 | [SSH-CONNECT] |
| SSH_MSG_CHANNEL_FAILURE | 100 | [SSH-CONNECT] |
### 4.1.3. 其他将要分配的值
在1到29、50到59和80到127之间的新的消息号的分配，必须通过STANDARDS ACTION方法进行分配，STANDARDS ACTION在[RFC2434]中有描述。</br>
30到49之间的消息号用于密钥交换方法，它们具体的含义将在密钥交换方法中进行定义。</br>
60到79之间的消息号用于进行用户的校验授权，它们的含义将在用户授权方法中进行定义。</br>
128到191之间的消息号必须通过IETF CONSENSUS方法进行分配，IETF CONSENSUS方法在文档[RFC2434]中有描述。</br>
191到255之间的消息号则由IANA进行管理。这个范围内的消息号将会用于PRIVATE USE命名空间。

## 4.2 断开连接的原因的描述及相关代码
断开消息"reason code"是一个无符号32位整形值(uint32)，其相关联的描述消息"description"是一个可读的字符串，用于描述连接断开的原因。

### 4.2.1. 协议
当数据包中包含SSH_MSG_DISCONNECT消息时，则必须同时包含一个介于0x00000001到0xFFFFFFFF之间的'reason code'。这一部分的详细内容在[SSH-TRANS]中有描述。

### 4.2.2. 初始赋值
下表中包含了SSH_MSG_DISCONNECT的描述和原因代码的初始值。
|名称| 值|
|:--|:--|
| SSH_DISCONNECT_HOST_NOT_ALLOWED_TO_CONNECT | 1 |
| SSH_DISCONNECT_PROTOCOL_ERROR | 2 |
| SSH_DISCONNECT_KEY_EXCHANGE_FAILED | 3 |
| SSH_DISCONNECT_RESERVED | 4 |
| SSH_DISCONNECT_MAC_ERROR | 5 |
| SSH_DISCONNECT_COMPRESSION_ERROR | 6 |
| SSH_DISCONNECT_SERVICE_NOT_AVAILABLE | 7 |
| SSH_DISCONNECT_PROTOCOL_VERSION_NOT_SUPPORTED | 8 |
| SSH_DISCONNECT_HOST_KEY_NOT_VERIFIABLE | 9 |
| SSH_DISCONNECT_CONNECTION_LOST | 10 |
| SSH_DISCONNECT_BY_APPLICATION | 11 |
| SSH_DISCONNECT_TOO_MANY_CONNECTIONS | 12 |
| SSH_DISCONNECT_AUTH_CANCELLED_BY_USER | 13 |
| SSH_DISCONNECT_NO_MORE_AUTH_METHODS_AVAILABLE | 14 |
| SSH_DISCONNECT_ILLEGAL_USER_NAME | 15 |

### 4.2.3. 其他将要分配的值
断开消息的原因代码必须按照顺序进行分配。新的断开消息的原因代码和他们相关的描述文本，都必须通过IETF CONSENSUS方法进行分配（在[RFC2434]中有描述），他们的取值范围为：0x00000010到0xFDFFFFFF。IANA不会为断开消息的原因代码分配0xFE000000到0xFFFFFFFF之间的值，这个范围内的值用作断开消息的原因代码时，仅限于私有域。

## 4.3. 通道连接失败原因代码和描述
连接失败原因代码时一个无符号32位整型数(uint32)。连接失败原因的描述文本是一个可读的信息，用来描述通道连接失败的原因。这一部分在文档[SSH-CONNECT]中有描述。

### 4.3.1. 协议
当数据包中包含SSH_MSG_CHANNEL_OPEN_FAILURE消息时，必须包含一个原因代码，原因代码的取值范围为：0x00000001到0xFFFFFFFF。

### 4.3.2. 初始赋值
以下表格中包含了原因代码和描述的初始赋值。表格中给出的原因代码的值是一个可读的十进制数字，实际使用时，应该使用32位无符号数值。
|名称|原因代码|
|:--|:--|
| SSH_OPEN_ADMINISTRATIVELY_PROHIBITED | 1 |
| SSH_OPEN_CONNECT_FAILED | 2 |
| SSH_OPEN_UNKNOWN_CHANNEL_TYPE | 3 |
| SSH_OPEN_RESOURCE_SHORTAGE | 4 |

### 4.3.3. 其他将要分配的值
通道连接失败的原因代码必须按照顺序进行分配。当请求一个新的通道连接失败的原因代码和描述字符串时，必须依照IETF CONSENSUS方法进行分配（在文档[RFC2434]中有描述），他们的取值范围为0x00000005到0xFDFFFFFF。IANA不会为通道连接失败的原因代码分配0xFE000000到0xFFFFFFFF之间的值，这个范围内的值仅用于私有域(PRIVATE USE)，私有域在文档[RFC2434]中有描述。

### 4.3.4 