# The Learning Problem
## Course Introduction
1. 機器學習是一門由理論和實務所結合的學問
2. 本課程以機器學習的「基礎」來做切入
3. 四個主題
   - When Can Machines Learn?
   - Why Can Machines Learn?
   - How Can Machines Learn?
   - How Can Machines Learn Better?
  
## What is Machine Learning
1. What is 'learning'?
   - 學習是從【觀察】出發，經過【學習內化】，最終變成有用的【技巧】。
   - Observations -> learning -> skill
2. Machine Learning
   - Data -> Machine Learning -> Skill
3. What is 'skill'?
   - 技巧想要做的便是增進某一種東西的表現
   - 因此，機器學習的過程即為 Data -> ML -> improved performance measure
4. ML is an alternative route to build complicated systems
   - 有些情況下我們很難用城市定義機器需要做的事(ex:辨別一棵樹)，機器學習便是讓機器自己去分析資料、自己學會
5. 什麼時候可以使用機器學習
   - When human cannot program the system manually
   - When human cannot define the solution easily
   - When needing rapid decisions that humans cannot do?
     + High-frequency trading (超短線股票買賣)
   - When needing to be user-oriented in a massive scale
6. 機器學習是教電腦釣魚，而不是給他魚吃
7. 使用機器學習的三個關鍵
   - exists some 'underlying pattern' to be learned
   - but no programmable (easy) definition
   - somehow there is data about the pattern

## Applications of Machine Learning
1. 機器學習的應用
   - food: 從推特中學習到【去某家餐廳用餐之食物中毒的可能性】
   - clothing: 推薦顧客如何搭配衣服
   - housing: 預測房子的能源消耗狀況
   - transportation: 無人車自動辨識交通號誌
   - education: 線上答題系統預測出學生對於未見過的題型的答對機率
     + 答對: 學生能力 > 題目難度
     + 【逆向工程】: 利用資料回推學生的程度、題目難度
   - entertainment: 推薦系統 (機器學習使用者的喜好)
2. 機器怎麼學習使用者的喜好
   - 電影的特徵:電影類型、演員...
   - 將使用者的喜好、電影特徵分別轉換成向量，兩者內積。如果很高，則表示使用者可能會給該電影很高的評價，反之亦然。
   - 機器會從rating反推使用者的特徵(喜好)，進而預測其對其他電影的評價

## Components of Machine Learning
1. 情境:銀行該不該發信用卡給某一位客戶
   - 顧客資料: age, gender, annual salary, year in residence, year in job, current debt...
   - pattern to be learned: approve credit card good for bank?B
2. Basic Notations
![01_handout_page-0022](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/70ec3568-f7ce-4e9f-95df-22323303810c)
  - input x: 申請人的相關資料
  - output y: 發卡後的結果(good/bad)
  - **Target funcion** f: X -> Y 電腦要學習的【未知】pattern
  - Training examples(以前的資料): `D = {(x_1,y_1),(x_2,y_2),...,(x_n,y_n)}`
  - **hypothesis** g: X -> Y 電腦學習到的函數。希望g和f越像越好。
![01_handout_page-0024](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/56ed369c-9636-4bc4-928f-8e9337cb632f)
  - **learning algorithm** A 機器學習演算法要做的事情便是從他看到的資料中，從hypothesis set(H)裡選一個最好的出來
  - **hypothesis set** H 各種可能的hypothesis (h)
  - 機器學習模型指的是learning algotithm和她使用的hypothesis set
3. 機器學習
  - 從data中算出一個hypothesis(g)，期望g很接近f

## Machine Learning and Other Fields
1. 機器學習: 希望用資料去找出一個hypothesis g，期望g和目標f很接近
2. 資料探勘: 希望能夠用資料找出一些有用的事情、性質(ex:關聯性)
   - 傳統的資料探勘中，希望在很多的資料當中，還能夠很有效率的計算
3. 人工智慧: 希望電腦做出某種東西，呈現出一些聰明的表現(ex:自動駕駛、下棋)
   - 機器學習是實現人工智慧的一種方式
4. 統計: 利用資料做推論
   - 統計是實現機器學習的一種方法
   














