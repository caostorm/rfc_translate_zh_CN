# 1. 简介
这个文档没有定义任何新的协议。文档仅为SSH协议创建IANA数据库的初始状态，同时包含了未来将要分配的指令。除了一种被普遍认为过时了的HISTROIC算法外，文档没有定义任何新的协议或者编号范围。新的协议和编号范围仅在[SSH-ARCH]、[SSH-TRANS]、[SSH-USERAUTH]、[SSH-CONNECT]文件中有过定义。

# 2. 贡献者
这一系列的文档的主要原始创作者有：Tatu Ylonen, Tero Kivinen, Timo J. Rinne, Sami Lehtinen（SSH通信安全公司的所有成员），还有Markku-Juhani O. Saarinen（来自于Jyvaskyla大学)。Darren Moffat是最初的作者，做出了大量的贡献。
有许多人为这个文档做出了数以年记的付出，这些人包括Mats Andersson、Ben Harris、Bill Sommerfeld、Brent McClure、Niels Moller、Damien Miller、Derek Fawcus、Frank Cusack、Heikki Nousiainen、Jakob Schlyter、Jeff Van Dyke、Jeffrey Altman、Jeffrey Hutzelman、Jon Bright、Joseph Galbraith、Ken Hornstein、Markus Friedl、Martin Forssen、Nicolas Williams、Niels Provos、Perry Metzger、Peter Gutmann、Simon Josefsson、Simon Tatham、Wei Dai、Denis Bider、der Mouse和Tadayoshi Kohno，对这些人致以感谢。将这些人名列出来，并非是他们为这篇文档签署，而是他们对它做出了贡献。

# 3. 文档中涉及到的公约
## 3.1. RFC 2119中的关键词
所有的SSH协议系列的文档都将使用以下的关键词来描述所需要的条件："MUST"（必须）、"MUST NOT"（必须不）、"REQUIRED"（必需的）、"SHALL"（应该）、"SHALL NOT"（不应该）、"SHOULD"（可能）、"SHOULD NOT"（不可能）、"RECOMMENDED"（推荐）、"MAY"（也许）和"OPTIONAL"（可选）。这些关键词在[RFC2119]中有解释。
## 3.2. RFC 2434中的关键词