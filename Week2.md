# Learning to Answer Yes/No
## Perceptron Hypothesis Set
![02_handout_page-0003](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/f24c1273-9b01-401a-8663-5907b5c1a563)
![02_handout_page-0004](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/046d9960-d832-411b-a536-7aa4acb7aae0)
1. 怎麼判定該不該發信用卡給某位客戶?
   - 將每一個使用者用一個向量表示，每一個維度代表某一種feature，將維度綜合計算出score
   - 如果score超過某一個標準，就發給他。
   - 總結: 讓電腦算出score後，減掉所設定的標準。若結果是正，則代表好(+1)。若結果為負，則代表不好(-1) --> y: {+1,-1}
   - h(x): perceptron 感知器
2. h(x)
![02_handout_page-0005](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/f8983013-8f80-4831-9d35-a588cb670ee9)
  - 將門檻值也當成一個w -> w0*x0
![02_handout_page-0006](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/2110ff33-4e25-4866-8a87-46fc3fb208ff)
  - perceptron 即為平面上一條一條的線，所以有時又會稱為【linear classifiers】
## Perceptron Learning Algorithm
1. How to select g from H?
   - Unknown: f
   - 我們只知道D是由f產生的，所以首要目標是希望g和f在看過的資料D上要長的很接近或一模一樣 `g(x_n) = f(x_n) = y_n`
   - 難: 有無限多條線可以選擇
   - 思路: 隨機取一條線，慢慢去移動、修正
2. Perceptron Learning Algorithm
   - 一輪一輪(t)的去做修正
   - 在某一輪中，該條線在某一個點w_t犯了錯 -> 修正
   - 怎麼修正?
     + if實際符號為正，但它跟我說是負的，代表w跟x的角度太大。修正方式就是把w+x，將之轉回來。
     + if實際符號為負，但他跟我說是正的，代表w跟x的角度太小。修正方式是w-x，將之轉開。
   - 一直修正直到不再犯錯
   - 【知錯能改演算法】
![02_handout_page-0010](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/c2628a7e-b0fd-46d2-90d8-6276dc3aed5f)
3. Cyclic PLA: 一個點一個點輪流去看，一個點沒有犯錯，則繼續看下一個點。如果這個點犯了錯，進行修正。如果全部的點都看完又繞回來發現都沒有犯錯，就表示完成了
![02_handout_page-0011](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/22c58596-8aaf-4fec-99c1-f91ae6546719)
4. 衍伸問題: PLA演算法一定會停嗎?若真的停下來了，g和f相同嗎
5. Question
更新規則： $\mathbf{w}_{t+1} \leftarrow \mathbf{w}_t + y_n$
將之左右乘上 $x_n y_n$ 即可推出 (請看下圖)
![02_handout_page-0036](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/97d125a4-5da3-473a-b141-12ac53d62bd3)
![02_handout-25](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/f9b73fe9-8a6a-4174-916f-6ae9306b9fab)
