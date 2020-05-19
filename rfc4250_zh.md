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
# 4. IANA 