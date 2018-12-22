# 資訊學科能力競賽筆試 筆記
## 有號數字 表示法 (Signed Number Representations)
### 符號大小 (Sign and Magnitude)
> 用一個位元 (bit) 來表示 正(+)、負(-)
> 符號大小 (Sign and Magnitude) 表示法的 +0、-0 不一樣
### 1 的補數 (Ones’ Complement)
> 又稱 反碼
> 
> 藉由 反轉/反向 ( inverse ) 每一個位元，原本是 『 1 』 就變 『 0 』，『 0 』就變 『 1 』
> 
> 例如 (4位元 1 的補數):
『 3 』，表示為: 0011;
『 -3 』，就是 『 3 』的反向，表示為: 1100。
> 
> **0 依然有兩種表示法 +0、-0**。
> 
> 減法 可以透過加一個『負數』來完成。
> 例如:
> 3 – 2 運算，可以透過 3 + (-2) 來完成。
> 『 3 』 表示為: 0011，
> 『 + 』為 1 的補數加法 (常表示為: {+1s}、+’)，
> 『 -2 』表示為: 1101。
> ![](https://s3.notfalse.net/wp-content/uploads/2017/02/25142907/ones-complement-sum.png)
> 如果有『爆掉』的位數，要再將它加回，稱為 — — **端回進位 (end around carry)，也就是將任何溢出的最高有效位元，加回最低有效位元**。
這是 1 的補數的重要性質!
### 2 的補數 (Two’s Complement)
> 或稱 補碼
>  2 的補數之『負數』，其實就是 1 的補數 + 1
>  
> 如果有『爆掉』的位數，不需 做 端回進位 (end around carry)。
> 
> 減法 一樣可透過 加 一個『負數』來完成。
> 例如:
> 3 – 2 運算，可以透過 3 + (-2) 來完成。
> 
> 『 3 』 表示為: 0011，
> 『 + 』為 2 的補數加法 (常表示為: {+2s})，
> 『 -2 』表示為: 1110。
> ![](https://s3.notfalse.net/wp-content/uploads/2017/02/25211142/twos-complement-sum.png)
### 偏移表示法 (Biased Notation)
> 又稱 移碼 excess-N，
> 即是透過將原數的 2 的補數，再加上一個 偏移值 而得。
> 
> 例如:
> 二進位浮點數算術標準 (IEEE 754) 中，
單精度浮點數的偏移值為 127。
> 
> 『 -1 』的 2’s 補數: 1111 1111(2)，
> 而 偏移值 127 之偏移表示法: -1 + 127 = 126 = 0111 1110(2)。
> 
> 『 1 』的 2’s 補數: 0000 0001(2)，
> 而 偏移值 127 之偏移表示法: 1 + 127 = 128 = 1000 0000(2)。

參考 : https://notfalse.net/20/signed-number-representations

## 資訊技術（Information Technology，IT）
* 也稱資訊和通訊技術（Information and Communications Technology，ICT）
* 是主要用於管理和處理資訊所採用的各種技術總稱
* 依照存儲和處理資訊的不同，可以將資訊技術的發展分為幾個不同的階段：前機械時期（3000 BC – 1450 AD）、機械時期（1450–1840）、機電時期（1840–1940）及電子時期（1940–現時）
* 商業領域中，美國資訊技術協會（ITAA）定義資訊技術為「對於以電腦為基礎之資訊系統的研究、設計、開發、應用、實現、維護或應用。」

參考 : https://zh.wikipedia.org/wiki/%E4%BF%A1%E6%81%AF%E6%8A%80%E6%9C%AF

## 無條件流程轉移(GOTO)
```cpp
 start:
 goto start;
```
* Goto敘述用以無條件跳至指定的行標籤或行號。
* 標記名稱用來代表一個位址；行號必須是數字，行標籤可以是數字和文字的混合，但是目的行標籤必須再加上「：」符號。
* 程式中應避免使用Goto敘述，因為它容易造成程式閱讀上的困難，且破壞程式結構的完整性。

參考 : http://www.chwa.com.tw/tresource/vs/book2/ch3/3-2.htm

## 傳參考參數傳遞（Pass by reference）
### 參考（Reference）型態
```cpp
int var = 10;  // 定義變數
int *ptr = &var; // 定義指標，指向var的位址
int &ref = var;  // 定義參考，代表var變數
```
注意參考型態一定要初始化，例如下面的定義是不能通過編譯的：
```cpp
int &ref; // error
```
為何參考型態一定要初始化？因為參考初始化後就不能改變它所代表的物件，任何指定給參考的值，就相當於指定給原來的物件，例如：
```cpp
#include <iostream>
using namespace std;

int main() {
    int var = 10;
    int &ref = var;
 
    cout << "var: " << var 
         << endl;
    cout << "ref: " << ref
         << endl;
 
    ref = 20;

    cout << "var: " << var 
         << endl;
    cout << "ref: " << ref
         << endl;

    return 0;
}
```
執行結果 : 
> var: 10
> ref: 10
> var: 20
> ref: 20

**事實上很少會直接如上的方式來使用參考，而是用於函式傳遞時一種「傳參考」（Pass by reference）方式，目的在於可於函式中直接操作目標變數或物件，或者是避免複製一個大型物件**


參考 : https://openhome.cc/Gossip/CppGossip/Reference.html
https://openhome.cc/Gossip/CppGossip/PassBy.html

##  分而治之（分治法）
分治法是建基於多項分支遞迴的一種很重要的演算法範式。字面上的解釋是「分而治之」，就是把一個複雜的問題分成兩個或更多的相同或相似的子問題，直到最後子問題可以簡單的直接求解，原問題的解即子問題的解的合併。

**實際上就是類似於數學歸納法，找到解決本問題的求解方程公式，然後根據方程公式設計遞迴程式。**

參考 : https://itw01.com/AHDEYMV.html
https://zh.wikipedia.org/wiki/%E5%88%86%E6%B2%BB%E6%B3%95

## 銷售時點情報系統（Point of Sale）
是零售業界為記錄銷售資訊所使用的一種資訊系統。
端點資訊服務，Point of Service的簡稱，Point of Sale的新叫法

參考 : https://zh.wikipedia.org/wiki/POS

## 時脈週期（Clock Cycle）
* 時脈 (clock) 是電腦內部一個類似時鐘的裝置，它每計數一次，稱為一個時脈週期 (clock cycle)，電腦就可以完成少量工作。
* 時脈速度 (clock rate) 指的是時脈計數的速度，單位為MHz (百萬赫茲) 或GHz (十億赫茲)，也就是每秒鐘幾百萬次或每秒鐘幾十億次，而時脈每計數一次所經過的時間稱為時脈週期時間(clock cycle time)。
* 電腦的效能取決於時脈速度、CPI和指令數目等因素。
* CPU時脈週期 (CPU clock cycle) 是CPU執行一個程式所花費的時脈週期

* CPU時間 = CPU時脈週期 * 時脈週期時間
### tip :
* **y 個時脈週期 / x GHz   =   y / x (ns 奈秒)**

參考 : https://docs.google.com/viewer?url=http%3A%2F%2Fwww.cinfo.kyu.edu.tw%2FCPU.ppt

## ARM架構
過去稱作進階精簡指令集機器

由於節能的特點，ARM處理器非常適用於行動通訊領域，符合其主要設計目標為低成本、高效能、低耗電的特性。

參考 : https://zh.wikipedia.org/zh-tw/ARM%E6%9E%B6%E6%A7%8B

## 著作權利歸屬
著作權法第11條規定
1. 受雇人於職務上完成之著作，以該受雇人為著作人。但契約約定以雇用人為著作人者，從其約定。
2. **依前項規定，以受雇人為著作人者，其著作財產權歸雇用人享有。但契約約定其著作財產權歸受雇人享有者，從其約定。**
3. 前二項所稱受雇人，包括公務員。

參考 : https://www.tipo.gov.tw/ct.asp?xItem=219595&ctNode=7561&mp=1

## 布林運算式符號
^  and
v  or
┏— not

## 無線網路
* 為何會選擇2.4GHz 和5GHz，這是因為國際上有個 ISM 頻段共識，將部分無線電頻率免費開放給工業（Industrial）、科學（Scientific）、醫學（Medical）類別使用，無須額外特許證照或是費用。
* 就無線電波的物理性質比較2.4GHz 和5GHz，**2.4GHz能夠傳輸的距離較遠**，或者反過來敘述，同樣距離下2.4GHz的訊號品質比較好。
* 只是越方便、越好的頻率也就越多人用，用來加熱食物的微波爐、製造品質低落的USB 3.1 Gen 1產品也會**干擾2.4GHz**。
* 雖然我們一般都稱5GHz 使用頻率，實務上大約從5.1GHz～5.9GHz 這之間的頻率均可以使用。802.11a、802.11n、早期802.11ac 無線網路產品，所使用的5GHz 頻率大約是5.735GHz～5.835GHz之間。

### 2.4GHz
> 2.4GHz頻段可分為14個WLAN信道，除了第14號信道與第13信道間隔了12MHz外，其餘每個信道之間的間隔均為5MHz，而IEEE802.11標準規定，每一個信號都需要占用20MHz（實際上是22MHz）的頻寬，相當於5個WLAN信道。

### 5GHz
> **5GHz頻段的範圍比起2.4GHz無疑要寬廣得多**，覆蓋範圍實際上是4.9GHz到5.8GHz，信道的劃分也更多樣化，不過有一個標準是不變的，那就是信道對應的中心頻率提升5MHz，信道的編號就加1，這點與2.4GHz頻段信道劃分的標準基本一致的。支持5GHz頻段的無線路由器多數使用的是第36號信道至第165號信道，兩者對應的中心頻率分別為5.170GHz至5.825GHz。
> 

原文網址：https://kknews.cc/zh-tw/tech/y8kne9a.html


參考 : https://www.techbang.com/posts/54296-the-ultimate-wi-fi-signal-enhancement-concept-knowledge-wi-fi-wireless-local-area-networks-11-essential-concepts-to-clarify
https://kknews.cc/zh-tw/tech/y8kne9a.html

## 真值表
### 卡洛圖
> 若是 ABvCDvAD 這種
> 1. 把 **1 圈起來**(盡量2 4 8個一組)
> 2. 找出每組相同的 ABCD，如果是 0 要加 bar
> 3. 每組相同的寫在一起，不同組的中間以 v(加) 隔開

> 若是 (BvCvD)(AvC)(AvD) 這種
> 1. 把 **0 圈起來**(盡量2 4 8個一組)
> 2. 找出每組相同的 ABCD，如果是 0 要加 bar
> 3. 每組相同的寫在一起，不同組的中間以 v(加) 隔開
> 4. **整體再加一個 bar，
> 原本同組的變加，加的地方變乘，
> 有 bar 變沒 bar，沒 bar 變有 bar**

參考 : 訊科同學

## 阻斷服務攻擊（denial-of-service attack，DoS attack、DoS）
* 亦稱洪水攻擊
* 一種網路攻擊手法，其目的在於使目標電腦的網路或系統資源耗盡，使服務暫時中斷或停止，導致其正常用戶無法存取。
* DoS也常被用於抗議，自由軟體基金會創辦人理察·斯托曼曾表示，DoS是「網路街頭抗議」的一種形式。
* 阻斷服務的攻擊也可能會導致目標電腦同一網路中的其他電腦被攻擊，網際網路和區域網路之間的**頻寬會被攻擊導致大量消耗，不但影響目標電腦，同時也影響區域網路中的其他電腦**。如果攻擊的規模較大，整個地區的網路連接都可能會受到影響。
* 可以具體分成兩種形式：頻寬消耗型以及資源消耗型。它們都是透過大量合法或偽造的請求占用大量網路以及器材資源，以達到癱瘓網路以及系統的目的。
### 分散式阻斷服務攻擊（distributed denial-of-service attack，DDoS attack、DDoS）
> 當駭客使用網路上兩個或以上被攻陷的電腦作為「殭屍」向特定的目標發動「阻斷服務」式攻擊時，稱為**分散式阻斷服務攻擊（distributed denial-of-service attack，DDoS attack、DDoS）**。
> DDoS發起者一般針對重要服務和知名網站進行攻擊，如銀行、信用卡支付閘道器、甚至根域名伺服器等。

參考 : https://zh.wikipedia.org/wiki/%E9%98%BB%E6%96%B7%E6%9C%8D%E5%8B%99%E6%94%BB%E6%93%8A

## SQL資料隱碼攻擊（SQL injection）
是發生於應用程式與資料庫層的安全漏洞。簡而言之，是在輸入的字串之中夾帶SQL指令，在設計不良的程式當中忽略了字元檢查，那麼這些夾帶進去的惡意指令就會被資料庫伺服器誤認為是正常的SQL指令而執行，因此遭到破壞或是入侵。
### SQL
> 最為廣泛運用的資料庫語言。
> 
> 是一種特定目的程式語言，用於管理**關聯式資料庫管理系統（RDBMS）**，或在**關係流資料管理系統（RDSMS）** 中進行流處理。

參考 : https://zh.wikipedia.org/wiki/SQL%E8%B3%87%E6%96%99%E9%9A%B1%E7%A2%BC%E6%94%BB%E6%93%8A
https://zh.wikipedia.org/wiki/SQL

## 跨網站指令碼（Cross-site scripting，XSS）
通常指的是通過**利用網頁開發時留下的漏洞，通過巧妙的方法注入惡意指令程式碼到網頁，使用戶載入並執行攻擊者惡意製造的網頁程式**。這些惡意網頁程式通常是JavaScript，但實際上也可以包括Java，VBScript，ActiveX，Flash或者甚至是普通的HTML。攻擊成功後，攻擊者可能得到更高的權限（如執行一些操作）、私密網頁內容、對談和cookie等各種內容。

攻擊者**使被攻擊者在瀏覽器中執行指令碼**後，如果需要收集來自被攻擊者的資料（如cookie或其他敏感資訊），可以自行架設一個網站，讓被攻擊者通過JavaScript等方式把收集好的資料作為參數提交，隨後以資料庫等形式記錄在攻擊者自己的伺服器上。

參考 : https://zh.wikipedia.org/wiki/%E8%B7%A8%E7%B6%B2%E7%AB%99%E6%8C%87%E4%BB%A4%E7%A2%BC

## 網路釣魚（Phishing）
* 又名網釣法或網路網釣
* 是一種企圖從電子通訊中，透過偽裝成信譽卓著的法人媒體以獲得如用戶名、密碼和信用卡明細等個人敏感資訊的犯罪詐騙過程。
* 這些通訊都聲稱（自己）來自於風行的社群網站（YouTube、Facebook、MySpace）、拍賣網站（eBay）、網路銀行、電子支付網站（PayPal）、或網路管理者（雅虎、網際網路服務提供者、公司機關），以此來誘騙受害人的輕信。
* 常常導引用戶到URL與介面外觀與真正網站幾無二致的假冒網站輸入個人資料。

參考 : https://zh.wikipedia.org/wiki/%E9%92%93%E9%B1%BC%E5%BC%8F%E6%94%BB%E5%87%BB

## 時間複雜度
* O(n²)表示當n很大的時候，複雜度約等於Cn²，C是某個常數，簡單說就是當n足夠大的時候，隨著n的線性增長複雜度將沿平方增長。
* O(n)表示，n很大的時候複雜度約等於Cn，C是某個常數。簡言之：隨著n的線性增長，複雜度沿線性級別增長。
* O(1)表示，n很大的時候，複雜度基本就不增長了。簡言之：隨著n的線性增長，複雜度不受n的影響，沿常數級別增長（此處的常數是1）。

|    | Bubble sort | Quick Sort | Merge Sort | Heap Sort | Insertion Sort | Selection Sort |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| best case | N | NlogN | NlogN | NlogN | N | N² |
| worst case | N² | N² | NlogN | NlogN | N² | N² |
### 氣泡排序法（Bubble sort）
> 最佳狀態：待排序的序列**本身是有序序列**，排序次數根據優化後的程式碼，可以得出是N-1次，**時間複雜度為O(N)**

> 最壞的情況：待排序的**序列是逆序的**，此時需要排序1 2 3 ……(N – 1) = N(N – 1 )/2次，**時間複雜度為O(N²)**

參考 : https://codertw.com/%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC/29857/#outline__6
http://alrightchiu.github.io/SecondRound/comparison-sort-merge-sorthe-bing-pai-xu-fa.html

## IP 位址：網路和主機
IP 位址是個 32 位元的數字，該位址會獨一無二地識別 TCP/IP 網路上的主機 (電腦或其他裝置，例如印表機或路由器)。

IP 位址一般會使用半形句點來分隔 4 個十進位小數點格式的數字來表示，例如 192.168.123.132。若要了解如何使用子網路遮罩區分主機、網路及子網路，請以二進位表示法檢查 IP 位址。

例如，十進位小數點 IP 位址 192.168.123.132 就是 (使用二進位表示法的) 32 位元數字 110000000101000111101110000100。將它分成 4 部分，每一部分為 8 個二進位數字。這些 8 個位元的區段稱為八位元資料組。於是上列 IP 位址範例就會變成 11000000.10101000.01111011.10000100。

為使 TCP/IP 廣域網路 (WAN) 能有效做為網路集合，在網路之間傳送資料封包的路由器，並不知道資訊封包目的地之主機的確切位置。路由器只會知道主機所屬的網路，並且會利用儲存在其路由表中的資訊，來決定如何將封包傳送到目的地主機的網路。當封包傳送到目的地網路之後，該封包就會傳送到適當的主機。

為了使上述程序可以運作，IP 位址有兩個部分。IP 位址的第一個部分是做為網路位址，最後一個部分是做為主機位址。如果您選擇範例 192.168.123.132 並將它分成這兩個部分，則會有下列結果：


192.168.123.    網路
.132 主機
 
或者

192.168.123.0 - 網路位址。
0.0.0.132     - 主機位址。

參考 : https://support.microsoft.com/zh-tw/help/164015/understanding-tcp-ip-addressing-and-subnetting-basics

## 子網路遮罩
TCP/IP 運作所需要的第二個項目，是子網路遮罩。 TCP/IP 通訊協定會使用子網路遮罩，來決定主機是位於本機子網路上或在遠端網路上。
> 
> 在本範例中，子網路遮罩是 255.255.255.0。255 在二進位表示法中等於 11111111。因此，子網路遮罩為：

>    11111111.11111111.11111111.0000000
>  
> 以使用 255.255.255.0 子網路遮罩的本範例而言，網路 ID 是 192.168.123.0，主機位址是 0.0.0.132。 當某封包抵達 192.168.123.0 子網路時 (從本機子網路或遠端網路)，且該封包的目的地位址為 192.168.123.132，您的電腦會從網路接收該封包並加以處理。
> 
> 幾乎所有十進位子網路遮罩都會轉換成左邊全部都是 1 及右邊全部都是 0 的二進位數字。 其他一些常見的子網路遮罩為：
>  
> 1111111.11111111.1111111.11000000 (255.255.255.192) 
> 1111111.11111111.1111111.11100000 (255.255.255.224)

參考 : https://support.microsoft.com/zh-tw/help/164015/understanding-tcp-ip-addressing-and-subnetting-basics

## 網路類別
網際網路位址是由 InterNIC (http://www.internic.net ) 負責配置，該組織負責管理網際網路。 這些 IP 位址分成若干類別。 最常見的是類別 A、B 及 C。類別 D 和 E 雖然存在，但一般使用者通常不使用它們。 每個位址類別都有不同的預設子網路遮罩。

* 類別 A 網路會使用預設子網路遮罩 255.0.0.0，並以 **0-127** 做為第一個八位元資料組。 位址 10.52.36.11 是類別 A 的位址。 它的第一個八位元資料組是 10，介於 1 與 126 (含) 之間。
* 類別 B 網路使用預設子網路遮罩 255.255.0.0，並以 **128-191** 做為第一個八位元資料組。 位址 172.16.52.63 是類別 B 的位址。 它的第一個八位元資料組是 172，介於 128 與 191 (含) 之間。
* 類別 C 的網路會使用預設子網路遮罩 255.255.255.0，並以 **192-223** 做為第一個八位元資料組。 位址 192.168.123.132 是類別 C 的位址。 它的第一個八位元資料組是 192，介於 192 與 223 (含) 之間。

參考 : https://support.microsoft.com/zh-tw/help/164015/understanding-tcp-ip-addressing-and-subnetting-basics

## 子網路
無法使用的兩個位址是 192.168.123.0 和 192.168.123.255，因為**主機部分全部是 1 及全部是 0 的二進位位址是無效的**。 0 位址無效，因為該位址是用來指定未指定主機的網路。 255 位址 (使用二進位表示法，即全部是 1 的主機位址) 則是用來對網路上的所有主機廣播訊息。

## 網際網路協定（Internet Protocol Suite，IPS）
* 一個網路通訊模型，以及一整個網路傳輸協定家族，為網際網路的基礎通訊架構。
* 它常被通稱為TCP/IP協定套組（TCP/IP Protocol Suite，或TCP/IP Protocols），**簡稱TCP/IP**。因為該協定家族的**兩個核心協定：TCP（傳輸控制協定）和IP（網際網路協定），為該家族中最早通過的標準**。
* 由於在網路通訊協定普遍採用分層的結構，當多個層次的協定共同工作時，類似電腦科學中的堆疊，因此又被稱為**TCP/IP協定疊（TCP/IP Protocol Stack）** 。
* TCP/IP提供點對點的連結機制，將資料應該如何封裝、定址、傳輸、路由以及在目的地如何接收，都加以標準化。它將軟體通訊過程抽象化為四個抽象層，常被視為是**簡化的七層OSI模型**。

    ### 應用層
    包括所有和應用程式協同工作，利用基礎網路交換應用程式專用的資料的協定。
    ### 傳輸層
    解決諸如端到端可靠性（「資料是否已經到達目的地？」）和保證資料按照正確的順序到達這樣的問題。
    ### 網路互連層
    解決在一個單一網路上傳輸封包的問題。
    所有的路由協定，如BGP、OSPF、和RIP實際上也是網路層的一部分，儘管它們似乎應該屬於更高的協定疊。
    ### 網路埠層
    網路埠層實際上並不是網際網路協定組中的一部分，但是它是封包從一個裝置的網路層傳輸到另外一個裝置的網路層的方法。
    
    |網際網路協定疊中的層|例|
    | -------- | -------- |
    | **應用層 application layer** | HTTP、FTP、DNS |
    | **傳輸層 transport layer** |TCP、UDP、RTP、SCTP |
    |**網路互連層 internet layer** | 對於TCP/IP來說這是網際網路協定（IP）|
    |**網路埠層 link layer** | 乙太網路、Wi-Fi、MPLS |

參考 : https://zh.wikipedia.org/wiki/TCP/IP%E5%8D%8F%E8%AE%AE%E6%97%8F#%E7%BD%91%E7%BB%9C%E6%8E%A5%E5%8F%A3%E5%B1%82

## OSI模型
**開放式系統互連通訊參考模型**（Open System Interconnection Reference Model，OSI），簡稱為OSI模型（OSI model），一種概念模型，由國際標準化組織提出，一個**試圖使各種電腦在世界範圍內互連為網路的標準框架**。

1984年，國際標準組織（ISO）發布了著名的**ISO/IEC 7498**標準，它定義了網路互聯的7層框架，也就是開放式系統互聯參考模型。

* #### 應用層（Application Layer）
    提供為應用軟體而設的埠，以設定與另一應用軟體之間的通訊。
    例如: HTTP，HTTPS，FTP，TELNET，SSH，SMTP，POP3等。
* #### 表達層（Presentation Layer）
    把資料轉換為能與接收者的系統格式相容並適合傳輸的格式。
* #### 會議層（Session Layer）
    負責在資料傳輸中設定和維護電腦網路中兩台電腦之間的通訊連接。
* #### 傳輸層（Transport Layer）
    把傳輸表頭（TH）加至資料以形成資料包。傳輸表頭包含了所使用的協定等傳送資訊。
    例如:傳輸控制協定（TCP）等。
* #### 網路層（Network Layer）
    決定資料的路徑選擇和轉寄，將網路表頭（NH）加至資料包，以形成封包。網路表頭包含了網路資料。
    例如:網際網路協定（IP）等。
* #### 資料連結層（Data Link Layer）
    負責網路尋址、錯誤偵測和改錯。
* #### 實體層（Physical Layer）
    在局部區域網路上傳送資料框（data frame），它負責管理電腦通訊裝置和網路媒體之間的互通。包括了針腳、電壓、線纜規範、集線器、中繼器、網卡、主機介面卡等。

參考 : https://zh.wikipedia.org/wiki/OSI%E6%A8%A1%E5%9E%8B

## 堆疊 Stack

![](https://blog.kdchang.cc/2016/06/24/javascript-data-structure-algorithm-stack/stack.png)

* 堆疊器只有一個出口，資料的存入或取出都需經由此出入口。
* 每次存或取資料的位置，都是從當時堆疊器內所有資料的最上層開始。
* 堆疊觀念：表示資料存取的順序為先進後出(First In Last Out，FILO)如圖中的物品A；或稱為後進先出(Last In First Out，LIFO)，如圖中的物品E。

堆疊觀念在計算機中使用很廣，例如主副程式間訊息傳送，CPU中斷處理、遞迴程式的呼叫及返還。

參考 : http://www.chwa.com.tw/TResource/HS/book2/ch7/7-3.htm
https://blog.kdchang.cc/2016/06/24/javascript-data-structure-algorithm-stack/

## 佇列 Queue
![](https://c.share.photo.xuite.net/jane17512001/1c88ab5/9057290/1042580395_m.jpg)
* 佇列有一個入口及一個出口。
* 新的資料由末端加入，而由前端(Front)移出資料，資料存取的順序為先進先出(First In First Out ,FIFO)，如圖中的A先由右端加入，再由左端取出。
* 佇列觀念常用在計算機作業系統方面的應用，如列表、讀卡、緩衝區程式等等，大都採用先到先做的佇列觀念。

參考 : http://www.chwa.com.tw/TResource/HS/book2/ch7/7-3.htm
https://blog.xuite.net/jane17512001/PenguinDesign/237379254-Queue%28%E4%BD%87%E5%88%97%29%E3%80%81ConcurrentLinkedQueue

## 堆積 Heap
![](https://upload.wikimedia.org/wikipedia/commons/d/d2/Heap-as-array.svg)

## 雜湊表 Hash Table
Hash Table希望能夠將存放資料的「Table」的大小(size)降到「真正會存放進Table的資料的數量」，也就是「有用到的Key的數量」：

若有用到的Key之數量為n，Table的大小為m，那麼目標就是m=Θ(n)。
要達到這個目標，必須引入Hash Function，將Key對應到符合Table大小m的範圍內，index=h(Key)，即可成為Hash Table的index，如圖。
![](https://raw.githubusercontent.com/alrightchiu/SecondRound/master/content/Algorithms%20and%20Data%20Structures/HashTable%20series/Intro/f4.png)

### 很可能發生Collision
可惜事與願違，因為|U|≫m，再加上Hash Function設計不易，所以很可能發生Collision。

Collision就是兩筆資料存進同一個Table之slot的情形，這將會使得查詢資料失敗(例如：使用item1的Key，卻回傳item2的資料)。

若以Division Method實作Hash Function，定義h(Key)=Keymodm，Table大小為m=6，目前要處理的資料之Key有67,26,50,33,16,71，那麼各個Key將被對應到的index如下，同時參考圖：

h(67)=67mod6=1
h(26)=26mod6=2
h(50)=50mod6=2
h(33)=33mod6=3
h(16)=16mod6=4
h(71)=71mod6=5
「item26」與「item50」經過Hash Function後，同時想要將資料存進Table[2]，這就是Collision。
![](https://raw.githubusercontent.com/alrightchiu/SecondRound/master/content/Algorithms%20and%20Data%20Structures/HashTable%20series/Intro/f5.png)

參考 : http://alrightchiu.github.io/SecondRound/hash-tableintrojian-jie.html#dict

## 4G
根據ITU對4G的基本定義，4G網路在**高速移動下應可達到每秒100Mb的資料傳輸量，低速每秒可達1Gb**，但目前尚未有商業營運的行動網路達到該標準。

參考 : https://www.ithome.com.tw/node/65114

## IPv6
**網際協定第6版（Internet Protocol version 6，IPv6）** 是網際協定（IP）的最新版本，用作網際網路的網路層協定，用它來取代IPv4主要是為了解決IPv4位址枯竭問題，不過它也在其他很多方面對IPv4有所改進。

### 與IPv4比較
在Internet上，資料以分組的形式傳輸。**IPv6定義了一種新的分組格式**，目的是為了最小化路由器處理的訊息標頭。由於IPv4訊息和IPv6訊息標頭有很大不同，因此這兩種協定無法互操作。但是在大多數情況下，IPv6僅僅是對IPv4的一種保守擴展。除了嵌入了網際網路位址的那些應用協定（如FTP和NTPv3，新位址格式可能會與當前協定的語法衝突）以外，大多數傳輸層和應用層協定幾乎不怎麼需要修改就可以在IPv6上運行。

參考 : https://zh.wikipedia.org/wiki/

## NFC
**近距離無線通訊（Near-field communication，NFC）**，又簡稱近距離通訊或近場通訊，是一套通訊協定，讓兩個電子裝置（其中一個通常是行動裝置，例如智慧型手機）在相距幾公分之內進行通訊。

NFC被用於非接觸支付系統，如同過去的信用卡與電子票券智慧型卡一般，將允許行動支付取代或支援這類系統。NFC應用於社群網路，分享聯絡方式、相片、影片或檔案。具備 NFC 功能的裝置可以充當電子身分證和鑰匙卡。NFC 提供了設定簡便的低速連接，也可用於引導能力更強的無線連接。

參考 : https://zh.wikipedia.org/wiki/%E8%BF%91%E5%A0%B4%E9%80%9A%E8%A8%8A

## 病毒（virus）
電腦病毒（computer virus），或稱電腦病毒。是一種在人為或非人為的情況下產生的、在用戶不知情或未批准下，**能自我複製或運行的電腦程式**；電腦病毒往往會影響受感染電腦的正常運作，或是被控制而不自知，也有電腦正常運作僅盜竊資料等用戶非自發啟動的行為。

為了能夠複製其自身，病毒必須能夠執行程式碼並能夠對內存執行寫操作。基於這個原因，**許多病毒都是將自己附著在合法的執行檔上。如果使用者企圖執行該執行檔，那麼病毒就有機會運行**。

參考 : https://zh.wikipedia.org/wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%97%85%E6%AF%92

## 特洛伊木馬（Trojan Horse）
特洛伊木馬（Trojan Horse），在電腦領域中指的是**一種後門程式**，是駭客用來盜取其他用戶的個人資訊，甚至是遠端控制對方的電腦而加殼製作，然後通過各種手段傳播或者騙取目標使用者執行該程式，以達到盜取密碼等各種資料資料等目的。與病毒相似，**木馬程式有很強的隱秘性，隨作業系統啟動而啟動**。

參考 :  https://zh.wikipedia.org/wiki/%E7%89%B9%E6%B4%9B%E4%BC%8A%E6%9C%A8%E9%A9%AC_(%E7%94%B5%E8%84%91)

## 蠕蟲（worm）
電腦蠕蟲（computer worm）與電腦病毒相似，是一種能夠**自我複製**的電腦程式。

**與電腦病毒不同的是，電腦蠕蟲不需要附在別的程式內，可能不用使用者介入操作也能自我複製或執行**。電腦蠕蟲未必會直接破壞被感染的系統，卻幾乎都對網路有害。電腦蠕蟲可能會執行垃圾程式碼以發動分散式阻斷服務攻擊，令電腦的執行效率極大程度降低，從而影響電腦的正常使用；可能會損毀或修改目標電腦的檔案；亦可能只是浪費頻寬。

參考 : https://zh.wikipedia.org/wiki/%E9%9B%BB%E8%85%A6%E8%A0%95%E8%9F%B2

## 虛擬記憶體（virtual memory）
虛擬記憶體是電腦系統記憶體管理的一種技術。**它使得應用程式認為它擁有連續可用的記憶體（一個連續完整的位址空間），而實際上，它通常是被分隔成多個實體記憶體碎片**，還有部分暫時儲存在外部磁碟記憶體上，在需要時進行資料交換。與沒有使用虛擬記憶體技術的系統相比，使用這種技術的系統使得大型程式的編寫變得更容易，對真正的實體記憶體（例如RAM）的使用也更有效率。

參考 : https://zh.wikipedia.org/wiki/%E8%99%9A%E6%8B%9F%E5%86%85%E5%AD%98

## 動態主機設定協定（Dynamic Host Configuration Protocol，DHCP）
動態主機設定協定（英語：Dynamic Host Configuration Protocol，DHCP）是一個區域網路的網路協定，使用UDP協定工作，主要有兩個用途：

* 用於內部網路或網路服務供應商自動分配IP位址給用戶
* 用於內部網路管理員作為對所有電腦作中央管理的手段

參考 : https://zh.wikipedia.org/wiki/%E5%8A%A8%E6%80%81%E4%B8%BB%E6%9C%BA%E8%AE%BE%E7%BD%AE%E5%8D%8F%E8%AE%AE

## 用戶資料報協定（User Datagram Protocol，UDP）
**用戶資料報協定（User Datagram Protocol，UDP）**，又稱**使用者資料包協定**，是一個簡單的面向資料報的傳輸層協定，正式規範為RFC 768。

在TCP/IP模型中，UDP為網路層以上和應用層以下提供了一個簡單的埠。UDP只提供資料的不可靠傳遞，它一旦把應用程式發給網路層的資料傳送出去，就不保留資料備份（所以UDP有時候也被認為是不可靠的資料報協定）。**UDP在IP資料報的頭部僅僅加入了復用和資料校驗（欄位）**。

參考 : https://zh.wikipedia.org/wiki/%E5%8A%A8%E6%80%81%E4%B8%BB%E6%9C%BA%E8%AE%BE%E7%BD%AE%E5%8D%8F%E8%AE%AE
