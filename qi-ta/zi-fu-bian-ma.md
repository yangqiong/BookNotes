Unicode 只是一个字符集，它只规定了符号的二级制编码，**却没有规定这个二进制代码如何存储**。比如以UTF-8活着UTF-16等方式存储。

UTF8编码规则

* 对于单字节字符，字节的第一位设为0，后面7位为这个字符的unicode码。对于英文字母，UTF-8和ASCII编码是相同的。
* 对于n（n&gt;1）节字符，第一个字节的前n位为1，第n+1位设为0。后面每个字节的前两位一律设为10。剩余的没有提及的二进制位，全部为这个符号的unicode码。

---

* [字符编码笔记：ASCII，Unicode和UTF-8](http://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html)





