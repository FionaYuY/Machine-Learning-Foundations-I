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

2. Hoeffding's Inequality
   - $\mu$ 是罐子中的比例， $v$ 是我們抽樣出的比例。我們抽出的數量為 $N$
   - 當 $N$ 很大， $v$ 和 $\mu$ 會很接近，在誤差 $\epsilon$ 以內。
    $$\Pr[|\nu - \mu| \geq \varepsilon] \leq 2\exp(-2\varepsilon^2 N)$$
   - 此不等式表示: 當 $N$ 很大的時候， $v$ 和 $\mu$ 會很接近
   - $v=\mu$ 這個statement是PAC (probably approximately correct)
   - larger sample size $N$ or looser gap $\epsilon$ 會有越高機率 $v \approx \mu$。也就是說，如果抽樣的樣本夠大的話，我們大概可以推論說這個 $\mu$ 的值跟我們抽樣出來的 $v$ 的值是類似的。
   
![04_handout_page-0012](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/21b27ee1-df98-4b54-bcfd-c986e3188314)
![04_handout_page-0013](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/2a9189fb-0a07-4e7b-9906-a0321f9707ba)

3. 題目

![04_handout_page-0015](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/7fc8ea43-d3ec-44f6-8d43-8ab7ca7d3b90)

## Connection to Leanring
1. 
