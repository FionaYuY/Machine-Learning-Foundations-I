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

## Effective Number of Hypotheses
1. 進一步討論，如果要用線以外的hypothesis set(ex:hyperplane)， 要怎麼知道有多少種hypotheses?
   - 假設有N個點，這N個點看過去到底產生了幾種可能性(圈圈叉叉的組合)。這些組合稱為dichotomy(二分)。
   - 一個hypothesis可以做出多少種不一樣的dichotomy?
   - 把所有dichotomy放在一個集合裡面( $\mathcal{H}(x_1, x_2, \ldots, x_N)$ )
   - $\left| \mathcal{H}(x_1, x_2, \ldots, x_N) \right|$ : 為hypothesis set $H$ 在 $(x_1, x_2, \ldots, x_N)$ 所能產生的所有dichotomy的數量
   - 比較dichotomy set和hypothesis set有什麼不同?
     + hypothesis set可能是平面上所有的直線，他可以每個hypothesis對輸入空間X裡面所有的點取值
     + dichotomy set 只針對N個特定的點來作取值
![05_handout_page-0019](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/ac94c3ec-2768-4e34-8923-690b98c3c8c4)

2. 接下來，開始進一步思考能不能將Hoeffding中的 $M$ 用dichotomy set的大小取代掉。
   - 一個小麻煩: dichotomy set取決於我們所選好的 $x_1, x_2, \ldots, x_N$ ，這一點會對於未來的分析有點麻煩，因此我們要先移除掉對於x的依賴。
   - 解決方法: 算最多有幾種。選一把 $x_1, x_2, \ldots, x_N$ ，計算他的dichotomy set大小。再選另一把 $x_1, x_2, \ldots, x_N$ ，計算dichotomy set的大小...選擇最大的dichotomy set的大小( $m_H$ )
   - $m_H$ 會用來取代 $M$ ，他是一個比 $M$ 小的數字。
   - $m_H$ : **growth function** 成長函數，這個函數的輸出一定是有限的(最多就 $2^N$ )

![05_handout_page-0020](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/5d192eff-bad2-4aa3-a19f-1fff404fe9b7)

3. Growth Function for Positive Rays
   - input: $\mathcal{X} = \mathbb{R}$ (one dimension)，所有輸入都在數線上
   - 任一個門檻值決定不一樣的hypothesis(大於門檻值+1。小於門檻值-1) -> 稱為positive ray(hypothesis往正向射)
   - 這個可以是做1D的perceptron
   - 如果用這個hypothesis set可以切出多少種不一樣的dichotomy set?最多N+1種(N個點可以切成N+1個區塊，將門檻取在任何一個區塊內，就會產生一種不同的dichotomy)
   - 當N夠大時， $(N + 1) \ll 2^N$
     
![05_handout_page-0020](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/6e995944-83e0-47ec-a47c-c31382aa31ee)

4. Growth Function for Positivee Intervals
   - input: $\mathcal{X} = \mathbb{R}$ (one dimension)，所有輸入都在數線上
   - 如果用這個hypothesis set可以切出多少種不一樣的dichotomy set?最多 $\binom{N + 1}{2} + 1$ 種(N個點可以切成N+1個區塊，將門檻的端點取在其中個區塊內，就會產生一種不同的dichotomy)(+1是指如果兩個端點取再同一個區域中，所有N個點都會回傳叉叉)
   - 當N夠大時， $\left( \frac{1}{2}N^2 + \frac{1}{2}N + 1 \right) \ll 2^N$

![05_handout_page-0022](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/eaede341-5c0b-451a-bfb6-0022af8e6538)

5. Growth Function for Convex Sets
   - input: $\mathcal{X} = \mathbb{R}^2$ (two dimensional)，輸入空間為平面
   - 每一個hypothesis對應到一個convex set(在裡面的是正的，以外的是負的)

![05_handout_page-0023](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/ce8d2422-3f35-41ba-9ffd-7c91db9bcfba)
![05_handout_page-0024](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/9fa3c267-7c8e-466c-9bfc-995a299fec63)

   - 將所有這樣的hypothesis集合成一個hypothesis set的話，grwoth function 會變成怎樣?
   - 一個極端的可能:將所有的輸入排在一個圈上。不管要做出什麼樣的dichotomy，就做出一個多邊形，並將所有正的點連起來，再將多邊形稍微往外擴一點點。如此一來，不管要做出什麼樣的dichotomy都可以很輕易地用凸多邊形做出來。也就是說，這樣的hypothesis set每一種dichotomy都可以做出來。代表 $m_{\mathcal{H}}(N) = 2^N$ 。這N個點叫做**shattered**，意指這N個點被這個hypothesis打破了，也就是說這所有的情形通通都可以做出來。

6. 問題

![05_handout_page-0025](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/38b0dc55-7a93-41a1-a296-b2919cbca163)

## Break Point
1. The four Growth Functions

![05_handout_page-0026](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/6b936b5a-3b8c-4a88-8a35-6089ad9e7c7f)

2. 如果將 $m_H(N)$ 替代掉 $M$
   - 不等式右邊的式子由growth function和exponential組成
   - 果growth function是N的多項式，後面exponential減少的比較快，所以N夠大時，後面這個壞事發生的機率會越來越小，upper bound會越來越小，越可以看做壞事發生的機率可能很接近0
   - 然而，若growth function是N的指數成長(ex:convex sets)，就無法保證 $E_in$ $E_out$ 非常接近

3. 想要找出在成長函數中，第一個看起來有一些希望的點在哪裡?(此點稱為**Break point**)
   - 在perceptron中，三個點我們可以做出8種所有的dichotomy，四個點就沒有辦法做出所有的dichotomy了，因此將「4」這樣的點叫做一個break point。
   - 在break point上發現當 $m_{\mathcal{H}}(k) < 2^k$ ，有第一個break point後，後面的也都是break point了
   - 在perceptron中發現第一個不能shatter的點就是4。

![05_handout_page-0027](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/9aa7d28a-0c45-4f42-86e9-0753fbee297f)

4. The four break points

![05_handout_page-0028](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/079c3d83-b13c-4efd-805e-915e97963a00)
   
   - 猜想:會不會break point跟成長函數成長的速度有關係?
   - 或許可以證明，當break point在k的時候，成長函數成長的速度大概跟 $N^{k-1}$ 有關

5. 問題

![05_handout_page-0029](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/ef34ec8f-cf98-4169-a75d-bcd52daaf146)












