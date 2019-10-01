---
description: Linux是一種自由和開放原始碼的類UNIX 作業系統。
---

# Linux

### Linux kernel \(Linux 核心版本\) vs Linux distribution \(Linux 發佈商版本\)

將Linux Kernel\(含tools\)與可運行的軟體整合起來，加上工具程式， 這個工具程式可以讓使用者以光碟/DVD或者透過網路直接安裝/管理Linux系統。 這個『Kernel + Softwares + Tools + 可完整安裝程序』的咚咚，我們稱之為Linux distribution。

![](../../.gitbook/assets/image%20%2852%29.png)

> 因此，如果以CentOS這個distribution來說， 應該說：『我用的Linux是CentOS這個 distribution，版本為7.x 版，請問....』才對喔！

### 各大Linux Distributions的主要異同

 每個Linux distributions使用的kernel都是[http://www.kernel.org](http://www.kernel.org/)所釋出的，而他們所選擇的軟體，幾乎都是目前很知名的軟體，重複性相當的高， 例如網頁伺服器的Apache，電子郵件伺服器的Postfix/sendmail，檔案伺服器的Samba等等。還有Linux Standard Base \(LSB\)等標準來規範開發者，以及目錄架構的File system Hierarchy Standard \(FHS\)標準規範。唯一差別的，可能就是該開發者自家所開發出來的管理工具，以及套件管理的模式吧。所以，基本上，每個Linux distributions除了架構的嚴謹度與選擇的套件內容外， 其實差異並不太大。

|  | RPM 軟體管理 | DPKG 軟體管理 | 其他未分類 |
| :--- | :--- | :--- | :--- |
| 商業公司 | RHEL \(Red Hat 公司\) SuSE \(Micro Focus\) | Ubuntu \(Canonical Ltd.\) |  |
| 社群單位 | Fedora CentOS OpenSuSE | Debian B2D | Gentoo |



## UNIX

{% hint style="warning" %}
Linux不源於任何版本的UNIX的源代碼，並不是UNIX，而是一個**類UNIX**的產品。
{% endhint %}

UNIX，一種多用戶、多行程的電腦作業系統，源自於從20世紀70年代開始在美國AT&T公司的貝爾實驗室開發的 AT&T Unix 。

Unix在學術機構和大型企業中得到了廣泛的應用，當時的UNIX擁有者AT&T公司以低廉甚至免費的許可將Unix原始碼授權給學術機構做研究或教學之用，許多機構在此原始碼基礎上加以擴充和改進，形成了所謂的「Unix變種」，這些變種反過來也促進了Unix的發展，其中最著名的變種之一是由加州大學柏克萊分校開發的柏克萊軟件套件\(BSD\)產品。

後來AT&T意識到了Unix的商業價值，不再將Unix原始碼授權給學術機構，並對之前的Unix及其變種聲明了版權權利。BSD在Unix的歷史發展中具有相當大的影響力，被很多商業廠家採用，成為很多商用Unix的基礎。其不斷增大的影響力終於引起了AT&T的關注，於是開始了一場持久的版權官司，這場官司一直打到AT&T將自己的Unix系統實驗室賣掉，新接手的Novell採取了一種比較開明的做法，允許柏克萊分校自由發佈自己的Unix變種，但是前提是必須將來自於AT&T的程式碼完全刪除，於是誕生了4.4 BSD Lite版，由於這個版本不存在法律問題，4.4 BSD Lite成為了現代柏克萊軟件套件的基礎版本。

Unix因為其安全可靠，高效強大的特點在伺服器領域得到了廣泛的應用。直到GNU/Linux流行開始前，Unix也是科學計算、大型電腦、超級電腦等所用作業系統的主流。現在其仍然被應用於一些對穩定性要求極高的數據中心之上。

### 類Unix系統

1984年，Richard Stallman發起了GNU專案，目標是建立一個完全自由且向下相容UNIX的作業系統。這個專案不斷發展壯大，包含了越來越多的內容。現在，GNU專案的產品，如Emacs、GCC等已經成為各種其它自由發佈的類UNIX系統中的核心角色。

1990年，Linus Torvalds決定編寫一個自己的Minix內核，初名為Linus' Minix，意為Linus的Minix內核，後來改名為Linux。此內核於1991年正式發佈，並逐漸引起人們的注意。當時GNU作業系統仍未完成，GNU系統軟件集與Linux內核結合後，GNU軟件構成了這個POSIX相容作業系統GNU/Linux的基礎。今天GNU/**Linux已經成為發展最為活躍的自由／開放原始碼的類Unix作業系統**。

### Linux VS Unix

Linux和Unix的最大的區別是，前者是開發源代碼的自由軟體，而後者是對源代碼實行知識產權保護的傳統商業軟體。這應該是他們最大的不同，這種不同體現在用戶對前者有很高的自主權，而對後者卻只能去被動的適應；這種不同還表現在前者的開發是處在一個完全開放的環境之中，而後者的開發完全是處在一個黑箱之中，只有相關的開發人員才能夠接觸的產品的原型。



## Reference

{% embed url="http://linux.vbird.org/linux\_basic/0110whatislinux.php" %}

{% embed url="https://zh.wikipedia.org/zh-hk/UNIX" %}

{% embed url="https://coctec.com/docs/linux/show-post-52472.html" %}

{% embed url="https://ithelp.ithome.com.tw/articles/10210448" %}

{% embed url="https://www.zhihu.com/question/24217234" %}

