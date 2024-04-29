# Training versus Testing
## Recap and Preview
1. Learning is PAC-possible if enough statistical data and finite $|H|$
2. If $|\mathcal{H}| = M$  finite, N large enough, for whatever $g$ picked by  $\mathcal{A}$ , $E_{out}(g) \approx E_{in}(g)$

   If $\mathcal{A}$ finds one $g$ with $E_{in}(g) \approx 0$ , PAC guarantee for $E_{out}(g) \approx 0 \Rightarrow$ learning possible

![05_handout_page-0003](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/95807b8d-526e-411a-9d8f-2846d0599a03)

3. Two central questions
   - Can we make sure that $E_{out}(g)$ is close enough to $E_{in}(g)$ ?
   - Can we make  $E_{in}(g) small enough?

![05_handout_page-0004](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/a4f42214-0259-41e3-b432-36440789d5c2)
4. $M$ 跟上述兩個問題有什麼關係? 兩種可能性: 
   - $M$ 屬於相對小的數字:
     + GOOD: $M$ 很小，則表示壞事情發生的機率很小(壞事情: $E_{out}$ 和 $E_{in}$ 很不接近)，也就是說大部分的情況下 $E_{out}$ 和 $E_{in}$ 很接近
     + NOT GOOD: $M$ 很小時，演算法的選擇很有限，不一定能夠找到一個 $E_{in}$ 很小的hypothesis $g$ 。
   - $M$ 屬於相對大的數字
     + NOT GOOD: 壞事情發生的機率增加了，沒有辦法保證 $E_{out}$ 和 $E_{in}$ 很接近
     + GOOD: 有很多選擇
   - 選擇重要的 $M$ 對於之後learning的成效有關(太小太大都不好)
   - 當 $M$ 無限大怎麼辦?
![05_handout_page-0005](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/92d90c85-fb5e-4b50-8fa6-4c57e56512d8)

5. 當 $M$ 無限大怎麼辦?
   - 先將  $M$ 先換成 $m_H$ ( $m_H$ 是一個有限的數量)
   - 之後會再詳細說明
![05_handout_page-0006](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/5e8fdc6a-5f2c-4bcf-bf9d-c1cf67f437fb)

6. 問題

![05_handout_page-0007](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/285f0716-b819-4fb1-90e7-3a8ac89ea361)

## Effective Number of Lines
1. 當 $M$ 無限大時，前面提到的 union bound 會有問題。無限多項相加起來，可能會跑到無限大，或是遠比1大的數字 -> bound就沒有意義了

![05_handout_page-0008](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/873259c5-1a64-4a6c-8a14-3afcf5b6bd68)

2. 為什麼可以用union bound? 前提是壞事情不會重疊。然而，假如今天有兩個很接近的hypothesis(ex:perceptron中兩條很接近的線)， 則 (1) $E_{out}(h_1) \approx E_{out}(h_2)$ (2) for most  $D$ , $E_{in}(h_1) = E_{in}(h_2)$ 。
   也就是說，壞事情通常是有重疊的。 -> union bound is over-estimating -> 造成沒有辦法處理 $M$ 無限大的情況
3. Problem: 怎麼找出壞事情重疊的部分? 能不能把無限多個hypothesis分成有限多類，每一類是長得差不多的hypothees。在近一步找出重疊的部分
4. 怎麼把hypothesis歸為不同類?

![05_handout_page-0010](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/949bc98d-82d9-4fdc-b3b8-55efbb9bff31)
![05_handout_page-0011](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/50ab777f-1dc7-44e3-af0c-a9929f513909)
![05_handout_page-0012](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/255a8b80-26b0-4684-a2f9-6fe5de8ae415)
![05_handout_page-0013](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/c15b895d-3083-49bd-a249-3a0bd6e5c9b3)
![05_handout_page-0014](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/d560bcc0-2ccb-46b7-8e31-a1d96a41a985)
![05_handout_page-0015](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/1fef8054-db32-4241-8502-6ea134ff2880)
![05_handout_page-0016](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/728885be-5d13-45c2-99b3-32d6e40bb745)

5. 從上述例子，可以得知，如果我們從輸入的點看出去的話，得到的線的種類是有限的。(effective number of lines 有效的線的數量)
   - must be $\leq 2^N$ WHY?因為每個點只有2種可能性(o/x)
   - 也就表示就算有無限多條線，effective number of lines還是有限的
   - 用此有限的數字(effective)將 $M$ 取代掉，可以得到 $\Pr[|E_{in}(g) - E_{out}(g)| > \epsilon] \leq 2 \cdot \text{effective}(N) \cdot \exp(-2\epsilon^2 N)$
   - If (1) effective(N) can replace $M$ and (2) effective(N) $\ll 2^N$ learning possible with infinite lines

![05_handout_page-0017](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/e7c38ed5-a41f-4cc0-ae7b-cfca73bc38e3)

6. 問題

![05_handout_page-0018](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/e5dbbe57-050a-46bb-8852-80b7f15eb9da)
