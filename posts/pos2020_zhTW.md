[category]: <> (中文)
[date]: <> (2020/11/06)
[title]: <> (為什麼權益證明棒棒的（2020 年十一月）)
[pandoc]: <> (--mathjax)

_感谢Chih-Cheng Liang和Hsiao-wei Wang翻译这个文章_

權益證明（Proof of Stake, PoS）比工作量證明（Proof of Work, PoW）在區塊鏈安全上更具優勢的關鍵因素有三個。

## 權益證明在同樣成本下可提供更高的安全性

理解這點最簡單的方式就是把權益證明和工作量證明擺在一起看，假設每天有 $1 的區塊獎勵，攻擊此網路所需的成本是多少。

### 基於 GPU 的工作量證明

你可以便宜租到 GPU，所以攻擊網路的成本就只是租到足夠的 GPU 算力去壓過現有的礦工。在區塊獎勵每花的 $1，現有的礦工應該花費將近 $1 的成本（如果他們花費更多，礦工就會因為無利可圖而退出；如果花費比這個數字少，新礦工就會加入來獲取利潤）。因此，攻擊網路只需要暫時花費比 $1/天 多一點點，而且可能只需要持續幾個小時。

**總攻擊成本： ~$0.26 （假設攻擊 6 小時），且因為攻擊者可以收到區塊獎勵，所以這個數字還有可能壓到零**

### 基於 ASIC 的工作量證明

ASICs 其實是資本成本：當買進 ASIC 時你預期大概可以用兩年，因為它會慢慢耗損或是因為更新更好的硬體出來而過時。如果一個鏈被 51% 攻擊了，社群大概會用更換 PoW 演算法應對，而這時你的 ASIC 就會失去價值。平均而言，用挖礦大概是大約 1/3 的經常性成本與 2/3 的資本成本（詳見 [這裡](https://eth.wiki/concepts/proof-of-stake-faqs#what-about-capital-lockup-costs)）。因此，每天每花費 $1 在區塊獎勵上，礦工每天會花 ~$0.33 在電力與維護上，並花費 ~$0.67 在他們的 ASIC 上。假設 ASIC 可以用 ~2 年，礦工會需要為那單位的 ASIC 硬體花費 $486.67 。

> 譯註：$486.67 = 365 天 x 2 年 x $0.67 資本成本

**總攻擊成本：$486.67 （ASICs） + $0.08（電力與維護）= $486.75**

> 譯注：這邊電力與維護成本也是假設攻擊 6 小時

話雖如此，值得注意的是 ASICs （相較 GPU）帶來較高的安全性是以中心化的高代價換來的，因此[加入 ASIC 挖礦的門檻也非常高](https://blog.ethereum.org/2014/06/19/mining/)。

### 權益證明 Proof of stake

權益證明的成本幾乎是百分百的資本成本（抵押的幣）；唯一的營運成本是運行節點的成本。這樣人們會願意為每天每 $1 的區塊獎勵鎖住多少的資金呢？不像 ASIC，抵押的幣不會折舊，而且當你不想抵押了你還可以在一段短時間內取回你的幣。因此，參與者應該會願意為同樣程度的獎勵付出比 ASIC 的情況更高的資本成本。

讓我們假設 ~15% 的報酬率足夠吸引人們抵押（這是 eth2 的期望報酬率）。因此每天 $1 的區塊獎勵會吸引相當於 6.667 年報酬的抵押，或換算為金額為 $2,433 。節點消耗的硬體與電力成本很小，每一千元的電腦可以抵押上百上千元，而且每月 ~$100 的電力與網路費也算足夠。但保守的說，我們假設這些經常性成本是抵押總成本的 ~10%。所以我們只有每天 $0.90 的區塊獎勵對應到資本成本，因此我們還要把上面的數字減少 ~10%。

> 譯註：  6.667 年 = $1 /（15% 年報酬）； $2,433 = $1 每天 x 365 x 6.667

**總攻擊成本： $0.90/天 * 6.667 年 = $2,189**

長期來說，這個攻擊成本會預期再更高，因為抵押會變得更有效率，而且人們也會更能接受較低的報酬率。我個人預期這個數字最終會攀升到 $10,000 的程度。

注意取得這麼高程度安全性的唯一「代價」是無法任意移動你的資金的不方便。甚至有可能因為人們認知到這些鎖住的幣會造成幣的價值攀升，所以在社群流通的貨幣總數、或是能做有生產性投資的資金，都能維持不變。反觀 PoW，維持共識的「代價」是[瘋狂地確實損耗大量電力](https://www.theverge.com/2019/7/4/20682109/bitcoin-energy-consumption-annual-calculation-cambridge-index-cbeci-country-comparison)。

### 更高安全性或更低成本？

注意我們有兩種方式可以運用這個增加 5-20 倍的每單位成本安全性。一種方式是區塊獎勵維持現狀，並受益於增加的安全性。另一種方式是維持現有程度的安全性，並大量減少區塊獎勵（也就是減少共識機制成本的「浪費」）。

兩種方式都行。我個人喜歡後者，因為我們下文會看到，比起工作量證明，在權益證明中一個成功的攻擊能夠造成的傷害更少，而且更容易從攻擊中復原。

## 權益證明更容易從攻擊中復原

在工作量證明的系統，如果你的鏈遭受 51% 攻擊，你會怎麼做？目前為止，實務上唯一的應對一直是「慢慢等，直到攻擊者覺得無聊了」。但這忽略了一種更危險的攻擊叫做「重生點埋伏攻擊 (spawn camping attack)」，攻擊者可以對鏈攻擊再攻擊，明確的目標就是要讓鏈無法再使用。

> 譯注：重生點埋伏是一種遊戲術語，在對方玩家陣亡重生的地方埋伏，造成對方玩家一重生就再陣亡，毫無回擊能力。

基於 GPU 的系統完全沒有防禦的辦法，而且持續攻擊的攻擊者可以輕易讓一個鏈永遠毫無用處（或更實際一點，轉移到權益證明或權威證明（proof of authority））。實際上，在攻擊開始後的前幾天，攻擊者的成本就會變得非常低，而誠實礦工會離開，因為他們沒辦法再攻擊持續之下取得區塊獎勵。

在基於 ASIC 的系統，社群有辦法應對第一波攻擊，但接下來的攻擊就會變得很容易。社群可以在第一波攻擊之後，硬分叉來更換工作量證明的演算法，也就是把所有 ASIC 「變磚」（包含攻擊者與誠實礦工的 ASIC）。但如果攻擊者願意承受自己 ASIC 變磚的成本，接下來的情況就和 GPU 的情況一樣（因為還沒有足夠的時間去為新演算法打造與生產 ASIC），所以在這之後攻擊者可以很便宜地持續重生點埋伏攻擊。

> 譯註：變磚為電子產品俚語，代表損壞後無法使用，像磚頭一樣

權益證明的情況，情況則變得非常開朗。針對一些種類的 51% 攻擊（特別指想要推翻已經敲定的區塊），權益證明[共識有內建](https://arxiv.org/abs/1710.09437)的「砍押金（slashing）」機制，大比例的攻擊者抵押會被自動銷毀（而且不會銷毀到其他人的抵押）。針對其他種類的，更難偵測的攻擊（特別指 51% 合謀截斷其他人訊息），社群可以協調一個「少數使用者發起軟分叉 minority user-activated soft fork (UASF)」，可以大量銷毀攻擊者的資金（在以太坊中，可以透過「離線懲罰 inactivity leak 」做到）。不需要真的明確做到「硬分叉刪除貨幣」。除了 UASF 需要人為協調要選擇哪個少數區塊，其餘的事情都是自動化的，只要遵照協定規則去執行即可。

> 譯註：少數區塊 minority block 是小於 51% 抵押總數的驗證者決定出來的區塊。

因此，對鏈的第一次攻擊就會耗損攻擊者幾百萬美元，而且社群可以幾天內馬上站穩腳步。第二次攻擊仍然會花費攻擊者數百萬美元，因為他們需要買新的幣去取代舊的已經燒毀的幣。再攻擊第三次，就會再燒更多的數百萬美元。局面極為不對稱，而且優勢並不會在攻擊者那邊。

## 權益證明比 ASIC 更去中心化

基於 GPU 的工作量證明還算合理地去中心化，因為取得 GPU 不會太難。但前面提過，基於 GPU 的挖礦難以滿足「在攻擊之下的安全性」這個準則。另一方面，基於 ASIC 的挖礦，則需要數百萬美元的資本才能做（而且如果你的 ASIC 是買來的，多數時候，製造商會佔更多便宜）

這個資本門檻會是回答「權益證明代表富者更富」這個常見論點的答案：ASIC 挖礦也是富者更富，而且這個局面下，富者更佔優勢。權益證明的最低抵押門檻在相比之下算是很低，而且許多一般人有機會接觸。

> 譯註：就文章完成當下 32 ETH @ 440 USD ，最低抵押門檻大概是 40 萬台幣。

進一步說，權益證明更能抵抗審查。GPU 挖礦和 ASIC 挖礦很容易偵測，他們需要大量電力消耗、昂貴硬體採購、及大型廠房。另一方面，權益證明可以跑在一台不起眼的筆電上，甚至也可以透過 VPN 做。

## 工作量證明可能的優勢

我認為 PoW 有兩大主要的真正優勢，但這些優勢其實有相當的限制。

### 權益證明更像個「封閉系統」，長期而言財富更加集中

在權益證明，如果你有一些幣，你可以抵押那些幣，並且獲得更多同種類的幣。在工作量證明，你總是可以獲得更多幣，但你需要一些外部資源來達成。因此，人們會說長期而言權益證明的幣的分配會更集中。

我的回應是，在 PoS 中，報酬一般而言會很低（所以驗證者的獲利也會低）。在 eth2 ，我們預期驗證者的年報酬會相當於總 ETH 供給量的 ~0.5-2%。而且更多驗證者抵押，利率會更低。因此，可能要花個一世紀，整個資產集中程度才會翻倍，而且在這樣的時間跨度之下，其他促進分配的壓力（人們想花他們手上的錢，分配金錢到慈善或他們自己的子孫等等）比較可能會佔上風。

### 權益證明需要「弱主觀性（weak subjectivity）」而工作量證明不需要

關於「弱主觀性」的觀念可以看這個 [原始介紹](https://blog.ethereum.org/2014/11/25/proof-stake-learned-love-weak-subjectivity/)。本質上，就是節點在第一次上線，或是在離線很長一段時間之後（數個月）再次上線，這個節點必須要透過第三方的資源，才能決定正確的鏈頭在哪。這個第三方可以是他們的朋友、可以是交易所或區塊鏈瀏覽器網站、或是客戶端開發者本身、又或是其他角色。PoW 則沒有這樣的要求。

然而，這可能是一個很弱的要求。事實上，使用者本身就已經必須對客戶端開發者、或「社群」有這種程度的信任。最起碼，使用者必須信任某個人（通常是客戶端開發者）來告訴他們協定是什麼，這個協定曾經經歷過什麼樣的更新。這在任何軟體應用都無法避免。因此，這個 PoS 所需要增加的額外信任，其實已經算很少了。

但就算這些風險最終變得重要，對我而言相較於 PoS 系統帶來巨大的好處：更好的效率與更能從攻擊復原的能力，那些風險仍算微小。

參考來源：我之前寫權益證明的文章

- 英：[Proof of Stake FAQ](https://eth.wiki/concepts/proof-of-stake-faqs)
- 英 [A Proof of Stake Design Philosophy](https://medium.com/@VitalikButerin/a-proof-of-stake-design-philosophy-506585978d51) 中 [一种权益证明设计哲学](https://ethfans.org/posts/a-proof-of-stake-design-philosophy)