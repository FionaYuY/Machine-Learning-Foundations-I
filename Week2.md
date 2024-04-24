# Learning to Answer Yes/No
## Perceptron Hypothesis Set
![02_handout_page-0003](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/f24c1273-9b01-401a-8663-5907b5c1a563)
![02_handout_page-0004](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/046d9960-d832-411b-a536-7aa4acb7aae0)
1. 怎麼判定該不該發信用卡給某位客戶?
   - 將每一個使用者用一個向量表示，每一個維度代表某一種feature，將維度綜合計算出score
   - 如果score超過某一個標準，就發給他。
   - 總結: 讓電腦算出score後，減掉所設定的門檻。若結果是正，則代表好(+1)。若結果為負，則代表不好(-1) --> $\mathcal{Y}: \{ +1 (\text{good}), -1 (\text{bad}) \}$
   - $h(x)$ : perceptron 感知器
2. $h(x)$

![02_handout_page-0005](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/f8983013-8f80-4831-9d35-a588cb670ee9)
  - 將門檻值也當成一個 $w \to w_0 \times x_0$ ， $w_0$ 為門檻值(要學習的)、 $x_0$ 為1。
![02_handout_page-0006](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/2110ff33-4e25-4866-8a87-46fc3fb208ff)
  - perceptron 即為平面上一條一條的線，所以有時又會稱為【linear classifiers】
## Perceptron Learning Algorithm
1. How to select $g$ from $H$ ?
   - Unknown: $f$
   - 我們只知道 $D$ 是由 $f$ 產生的，所以首要目標是希望 $g$ 和 $f$ 在看過的資料 $D$ 上要長的很接近或一模一樣 $g(\mathbf{x}_n) = f(\mathbf{x}_n) = y_n$
   - 思路: 隨機取一條線，慢慢去移動、修正
2. Perceptron Learning Algorithm
   - 一輪一輪( $t$ )的去做修正
   - 在某一輪中，該條線在某一個點 $(x_{n(t)}, y_{n(t)})$ 犯了錯 -> 修正 $w_t$
   - 怎麼修正?
     + if實際符號為正，但它跟我說是負的，代表 $w$ 跟 $x$ 的角度太大。修正方式就是把 $w+x$，將之轉回來。(實際符號為正，代表 $w$ 和 $x$ 內積應該是正的，兩者角度應該是銳角。然而，現在是負的，則表示角度太大，因此需要把角度調小)
     + if實際符號為負，但他跟我說是正的，代表 $w$ 跟 $x$ 的角度太小。修正方式是 $w-x$ ，將之轉開。(實際符號是負，代表 $w$ 和 $x$ 內積應該是負的，兩者角度應該是鈍角。然而，現在是正的，則表示角度太小，因此需要把角度調大)
   - 一直修正直到不再犯錯
   - 【知錯能改演算法】

![02_handout_page-0010](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/c2628a7e-b0fd-46d2-90d8-6276dc3aed5f)

3. Cyclic PLA: 一個點一個點輪流去看，一個點沒有犯錯，則繼續看下一個點。如果這個點犯了錯，進行修正。如果全部的點都看完又繞回來發現都沒有犯錯，就表示完成了

![02_handout_page-0011](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/22c58596-8aaf-4fec-99c1-f91ae6546719)

4. 衍伸問題: PLA演算法一定會停嗎?若真的停下來了， $g$ 和 $f$ 相同嗎
5. Question
更新規則： $\mathbf{w}_{t+1} \leftarrow \mathbf{w}_t + y_n$
將之左右乘上 $x_n y_n$ 即可推出 (請看下圖)

![02_handout_page-0036](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/97d125a4-5da3-473a-b141-12ac53d62bd3)
![02_handout-25](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/f9b73fe9-8a6a-4174-916f-6ae9306b9fab)

## Guarantee of PLA
1. PLA 什麼時候停止?要達到停止，必需條件是要有一條直線可以切開資料-> Linear Separability
2. 假設有一條線是linear separable，PLA一定會停止嗎?
   - 目標函數 $w_f$ :目標的那條線，該線會滿足 $y_n = \text{sign}(w_f^T x_n)$ ，也就是說正的都會在正的這一邊，父的都會在負的那一邊
   - $w_f$ 是完美的，所以每個 $x_n$ 都會正確的遠離線 $\min_{n} y_n w_f^T x_n > 0$
   - 當進行PLA時，選到的某一個錯誤的點也會滿足這樣的性質(因為 $w_f$ 是完美的): $y_{n(t)} w_f^T x_{n(t)} \geq \min_{n} y_n w_f^T x_n > 0$
   - 以上述兩點基礎，我們進一步看到 $w_f$ 跟我們PLA在找的 $w_t$ 到底接不接近 -> 衡量兩個向量的方式中，其中一種就是內積，內積越大越接近
   - 因此更新後可得， $w_f^T w_{t+1} = w_f^T ( w_t + y_{n(t)} x_{n(t)} )$
   - 展開後，並帶入上面的基礎可得， $w_f^T w_{t+1} \geq w_f^T w_t + \min_{n} y_n w_f^T x_n$
   - 最後可得 $w_f^T w_{t+1} > w_f^T w_t + 0$
   - 也就是說 $w_f$ 和 $w_t$ 的內積會越來越大->越來越接近(前提是長度是一樣的情況下，下一段討論)

![02_handout_page-0027](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/64bdcd89-147d-40cc-a47b-c29315b806ca)

3. PLA有錯才改 $\Leftrightarrow \text{sign}(w_t^T x_{n(t)}) \neq y_{n(t)} \Leftrightarrow y_{n(t)} w_t^T x_{n(t)} \leq 0$
   - $\|w_{t+1}\|^2 = \|w_t + y_{n(t)} x_{n(t)}\|^2$
   - 展開後， $\|w_{t+1}\|^2 = \|w_t\|^2 + 2y_{n(t)} w_t^T x_{n(t)} + \|y_{n(t)} x_{n(t)}\|^2 $
   - 錯誤更新時， $\|w_{t+1}\|^2 \leq \|w_t\|^2 + 0 + \|y_{n(t)} x_{n(t)}\|^2$
   - 因此，如果只有犯錯才更新的話， $w_t$ 不會成長太快，因為它會加上一個負的項上去。他只會靠 $\|y_{n(t)} x_{n(t)}\|^2$ 成長
   - 跟最遠的點比較，可得 $\|w_{t+1}\|^2 \leq \|w_t\|^2 + \max_{n} \|y_n x_n\|^2$ ( $y_n$ 平方之後會是1，可省略)
   - 總結:每一次更新， $w_t$ 的長度最大就只會成長 $\max_{n} \|x_n\|^2$
4. 結合2.( $w_f$ 和 $w_t$ 內積越來越大)和3.( $w_t$ 長度慢慢的長)，可以知道 $w_f$ 和 $w_t$ 越來越接近
5. 結合起來，從 $w_0$ 開始，經過T次更新， $\frac{w_f^T w_T}{\|w_f\| \|w_T\|} \geq \sqrt{T} \cdot \text{constant}$
   - 兩個正規化的向量的內積，角度會越來越靠近
   - 每更新一次就靠近一點，靠近的速度跟更新的次數成一個根號的比例
   - 會不會無限制靠近?不可能 -> 因為兩個向量最大內積為1，因此可以證明這個演算法會停下來

![02_handout_page-0028](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/4b8b722e-a418-4905-b585-32c6bb9bd836)

6. PLA要更新幾次才會停下來?
   - $\rho$ 就是目標那條線的法向量。如果是線性可分，則 $\rho$ 一定大於0 

![02_handout_page-0030](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/dee3b24c-7f86-4613-90e3-8e25810a9635)

## Non-Separble Data
1. 上一個section證明了PLA會停，如果資料線性可分，PLA每次挑一個錯誤來修正，總結來說有兩點
   - 線性可分代表， $w_f$ 和 $w_t$ 越來越接近
   - 用錯誤來修正代表， $w_t$ 的長度會緩慢的成長
2. PLA
   - 優點: 很簡單、可用於任何dimension
   - 缺點:
     + 需要假設資料是線性可分的，因此拿到資料時，其實不能確定PLA能不能停
     + 多久會停下來? $\frac{R^2}{\rho^2}$ ，但 $\rho$ 是用 $w_f$ 算出來的，但 $w_f$ 未知。
     + 因此，實務上，不知道PLA會不會停，也不知道多久會停
3. 有時候資料中會有雜訊，也就代表拿到的資料不見得是【線性可分】。
   
![02_handout_page-0032](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/2d593d42-fd31-49ec-a355-ab33c4209d1e)

4. 有沒有辦法在資料不是線性可分，或是有雜訊的狀況下，還是找到一條好的線
   - 大部分的情況下，假訊相對是小的，通常y跟f要有一定對應程度， $y_n = f(x_n)$
   - 如果要在資料 $D$ 找一個跟 $f$ 很相像的 $g$ ，也應該要滿足 $y_n = g(x_n)$
   - 也就是說，我們要找一條犯的錯誤最小的線g， $w_g \leftarrow \argmin_w \sum_{n=1}^{N} |y_n \neq \text{sign}(w^T x_n)|$  --> 是一個NP-hard的問題
   - 我們沒辦法找到那條最完美的線，所以嘗試找尋一條【還不錯】的線，其中一個方法【pocket algorithm】

![02_handout_page-0033](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/950511ca-e76f-4288-be6d-b3ca81f847bd)

5. pocket algotithm
   - 可以看做PLA的變形
   - 【keeping best weights in pocket】
   - 會用較隨機的更新方式，因為想要找到的線能有多一點不一樣的地方，看能不能找到一條比較好的線
   - 跟PLA不同之處為，每次找到一條新的線，比較新的線與口袋的線哪一條比較好(犯的錯較少)，如果新的線較好，就將口袋裡的線丟掉，放新的線在口袋裡。跑得夠多了，看夠多的線了，就讓他停下來。

![02_handout_page-0034](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/a7c7d452-ad5b-43dd-a940-6a1669beff7f)

6. 問題

![02_handout_page-0036](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/0dfa423e-bd4d-4fdf-9a2c-00221493e468)

















