# Feasibility of Learning
Learning 是做得到?做不到? 若做不到，有沒有辦法加上一些條件讓他做得到?
## Learning is impossible
1. 對於同樣的dataset，可能會有非常多種的解釋

![04_handout_page-0004](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/0c539018-13e2-4415-9f31-56a2c01b5ff0)

2. 情境:輸入是一個3維度的向量(每個維度只能是0 or 1)，試著找出 $g$ 。但 $g$ 跟 $f$ 真的一樣嗎? 不一定。
   - 或許在 $D$ 中， $g \approx f$ ，然而在 $D$ 之外的data中，很有可能 $g \not\approx f$
     
![04_handout_page-0005](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/8f399d4b-13cd-49ae-a5cd-8109804875cc)
![04_handout_page-0006](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/f623c0de-b36e-452f-b8f0-f3c523845dd0)

3. 在機器學習的研究中，他們把這一系列的研究稱為 **No Free Lunch**。 No Free Lunch 指的是我們將資料餵進機器中，讓機器去學習，通常我們沒有辦法在沒有看過的資料下，知道 $g$ 跟 $f$ 到底像不像。
   我們會需要加入一些setting。

## Probability to the Rescue
1. learning想要做的事情便是對於未知的 $f$ 去做一些推論，因此有沒有什麼工具讓我們將未知的東西做一些推論?
   - 情境: 假設一個瓶子中有橘色和綠色的彈珠，我們可以用推論的方式去推算橘色彈珠的機率。-> 抽樣
   - in sample的 $v$ 會告訴我們out of sample $\mu$ 的資訊嗎?
  
![04_handout_page-0010](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/4186e3a8-c16e-49a7-926c-a2624282fe8c)
![04_handout_page-0011](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/d8f09209-93ec-4f09-97d6-eea808d06a0c)

2. **Hoeffding's Inequality**
   - $\mu$ 是罐子中的比例， $v$ 是我們抽樣出的比例。我們抽出的數量為 $N$
   - 當 $N$ 很大， $v$ 和 $\mu$ 會很接近，在誤差 $\epsilon$ 以內。
     **$$P[|\nu - \mu| \gt \varepsilon] \leq 2\exp(-2\varepsilon^2 N)$$**
   - 此不等式表示: 當 $N$ 很大的時候， $v$ 和 $\mu$ 會很接近
   - $v=\mu$ 這個statement是PAC (probably approximately correct)
   - larger sample size $N$ or looser gap $\epsilon$ 會有越高機率 $v \approx \mu$。也就是說，如果抽樣的樣本夠大的話，我們大概可以推論說這個 $\mu$ 的值跟我們抽樣出來的 $v$ 的值是類似的。
   - 有關Hoeffding's Inequality 可參考: https://medium.com/機器學習基石系列/機器學習基石系列-1-hoffedings-inequality-c40c7a8f123d
   
![04_handout_page-0012](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/21b27ee1-df98-4b54-bcfd-c986e3188314)
![04_handout_page-0013](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/2a9189fb-0a07-4e7b-9906-a0321f9707ba)

3. 題目

![04_handout_page-0015](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/7fc8ea43-d3ec-44f6-8d43-8ab7ca7d3b90)

## Connection to Leanring
1. 將剛剛彈珠的例子衍伸到learning的領域中
   - 左邊的彈珠例子可以一一對應到右邊learning的範疇中
   - 如果 $N$ 夠大且資料 $x_n$ 是i.i.d (independent and identically distributed)的從 $X$ 取出來，我們大概可以說 $h$ 跟 $f$ 不一樣的機率到底是多少?

![04_handout_page-0016](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/308db72d-c636-4c5b-be54-7a74333036a9)

2. Added Components 
   - $E_{out}(h) = \mathbb{E}_{x \sim P} \left[ h(x) \neq f(x) \right]$
     + $E_{out}$  相當於 $\mu$ (unknown)
   - $E_{in}(h) = \frac{1}{N} \sum_{n=1}^{N} \left[ h(x_n) \neq y_n \right]$
     + $E_{in}$ 相當於 $v$

![04_handout_page-0017](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/c975fa9e-403c-4e94-beb1-8df95b381437)

![04_handout_page-0017](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/1344c839-db32-4008-b7e0-01d925823db6)

3. 將Hoeffding's equality套用進來
   - $E_{out}$ : out-of-sample error
   - $E_{in}$ : in-sample error
   - $\Pr[|E_{in}(h) - E_{out}(h)| \geq \varepsilon] \leq 2\exp(-2\varepsilon^2 N)$      
   - Hoeffding's equality 告訴我們，當 $E_{in}$ 和 $E_{out}$ 很接近，且$E_{in}$都很小，那麼 $E_{out}$ 就很小。 $E_{out}$ 很小就代表如果資料繼續從 $P$ 產生出來的話， $h$ 和 $f$ 會很接近。

![04_handout_page-0018](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/78dbe326-89c4-40af-ad77-31e8ddef2347)

4. 我們現在有的保證: 如果資料夠大，那麼 $E_{in}$ 和 $E_{out}$ 就很接近。代表已經學到東西了嗎? $g \approx f$ 嗎?
   - 剛剛一切的推導都建立在只有一個 $h$ 上面，所以如果上述都要成真，代表你的演算法一定要選擇該 $h$ 。然而，如果有一個機器學習的演算法，不論其面對什麼樣的題目都選定一樣的 $h$ ，通常這個 $h$ 不會太好。(他的 $E_{in}$ 可能是很大的)。你會很有信心地得到 $g \not\approx f \text{ PAC}$ (可以很確定 $g$ 和 $f$ 一點也不接近)
   - 然而，真正的learning應該是有選擇的。因此現在做到的事情並非learning，而是 **Verification**。
   - Verification: 利用verifying examples去驗證這一個hypothesis好or不好
   - 現在只能驗證hypothesis的好與壞，還沒有辦法進行選擇
![04_handout_page-0019](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/b1234265-0fa9-4d66-9fe4-2baca713f254)
![04_handout_page-0020](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/ce521a9f-d8f3-48d5-b650-03de8c983ee6)

5. 題目

![04_handout_page-0022](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/950738e9-0b46-4ea8-8bea-eb0dba27631e)

## Connection to Real Learning
1. Problem: 當我們只有一個hypothesis，可以做verification。but if 當我們有很多hypothesis的時候，該怎麼辦?
2. 以擲硬幣當作例子: 如果150人中有人連續5次投到正面，代表這一個銅板真的比其他銅板要好嗎(「好」代表更容易出現正面)? 不是的，因為150人中，至少有一個人擲中5次正面的機率高於99%。也就是說，當今天我選擇了丟了五次正面的，並且說這個銅板比較幸運(好)，其實並非是對的。
   - Hoeffding告訴我們，取樣出來的資料跟大部分的資料是一樣的，只有少數是bad example(bad example表示 $E_{in}$ 和 $E_{out}$ 相差很遠)
   - 有選擇的時候，會惡化這些bad example: 只有一顆銅板時，最不好的五個正面的機率是1/32，當你有150個選擇時，選擇到全部都是正面的機率超過99%。

![04_handout_page-0024](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/deef0513-8395-49a7-8166-49a7e362195b)

3. 什麼是bad?
   - 什麼是bad sample? ex:  在擲銅板的情境中， $E_{out}$ 實際上是1/2，但是我們丟到五次正面( $E_{in} = 0$ )，兩者相差很多
   - 什麼是bad data? $E_{in}$ 和 $E_{out}$ 相差很遠。當兩者相差的比 $\epsilon$ 還遠，我們就說他是bad data。
   - 要記住的是，Hoeffding保證了抽出來的情形中有很大的機會會是good data，少數才有可能是bad data。
![04_handout_page-0025](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/9659e767-2406-4c66-bffb-34d6e75cccca)


4. 若有很多的hypothesis，那不好的機率會變成什麼樣子?
   - 不好的資料代表演算法沒有辦法自由自在地做選擇，他可能會「踩到雷」。也就代表存在hypothesis是 $E_{in}$ 和 $E_{out}$ 相差很遠
   - 好的資料代表演算法自由地做選擇得到的都是對的。
   - 如下圖，若採用 $D_1$ ，則可能會在 $h_1$ 、 $h_3$ 、 $h_M$ 踩到雷 -> 標為BAD

![04_handout_page-0026](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/fa7b534f-20fe-4fbb-916f-79554739ff31)

5. 總共的BAD加起來有多少?

![04_handout_page-0027](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/58f7c3c3-9186-4da2-a6fd-9484aa496157)

6. 結論:如果資料量夠多，我們可以說每一個 $h$ 都是安全的，也就是代表不管怎麼選擇都可以選到  $E_{in}$ 和 $E_{out}$ 是接近的( $E_{in}(g) =E_{out}(g)$ 這個statement是PAC)
7. 更新後，將演算法設計成，找一個 $E_{in}$ 最小的，就可以得到 $E_{out}$ 很小 -> learning is possible (在有限數量的hypothesis的情況下)

![04_handout_page-0028](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/36c7dca6-8c47-4f54-9341-3324afa5f120)

8. 進一步的問題，如果是不是有限多種呢?像是perceptron就有無限多條線。(之後才會說明)
9. 問題

![04_handout_page-0030](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/21e330a0-4578-442b-8752-d9a9e383ab42)

