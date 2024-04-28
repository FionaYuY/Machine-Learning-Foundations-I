# Types of Learning
## Learning with Different Output Space
1. binary classification 二元分類: $y = \lbrace -1, +1 \rbrace$ 
   - 是否發放信用卡
   - 是否為垃圾郵件
   - 病人是否生病
   - 答對或答錯
2. Multiclass Classification 多元分類: $y = \lbrace 1, 2, 3, \ldots , K \rbrace$
   - binary classification 是特例(當K=2)
   - 手寫字分類、圖片分類、信件分類等等
   - 很常被運用在視覺或聽覺的辨識
3. Regression迴歸分析: $y \in \mathbb{R} \quad \text{or} \quad y \in [\text{lower}, \text{upper}] \subseteq \mathbb{R}$
   - 如果 $y$ 是有範圍的，則特稱為bounded regression
   - 股票預測、氣溫預測
4. Strucuted Learning結構化的學習:較進階的問題，輸出空間有某一種結構在裡面。例如在自然語言辨識，寫出一段話時，能不能判斷每一個字的詞性
   - multiclass classification: word -> word class
   - 當輸入為一個sentence，輸出是一連串有【結構】的word class。ex: $y = \lbrace PVN, PVP, NVN, PV, \ldots\rbrace \text{, not including } VVVV$
   - 假設輸出為VVVVV(連續五個動詞)，就可以得知這個句子的文法錯誤
   - 其他應用:折一下蛋白質會影響到蛋白質什麼
  
![03_handout_page-0007](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/113daf60-0dad-4f7b-a2c1-8a5bedea2bf8)

5. 問題

![03_handout_page-0010](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/18a05b39-3247-4f62-b93f-693363c4e528)

##  Learning with Different Data Label
1. 情境:收集一堆銅板，收集其重量、大小等等，丟進機器學習演算法，使其學習分出四個類別的銅板 -> 監督式學習 supervised learning
   - 給銅板，也給答案
2. 如果不告訴機器銅板的分類和意義是什麼，機器將之歸類、分群 -> 分群 clustering, 非監督式學習 unsupervised learning
   - 分群的應用: 將網路上的文章自動分類到不同主題、把顧客分群做不同的促銷活動 

![03_handout_page-0013](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/45d0a10f-7ff9-413f-8fa2-b70148bffd01)

3. Other Unsupervised Learning Problems
   - 相較於監督式學習(有固定標記label)，非監督式學習的目標比較分散，也比較難衡量演算法的好壞。此外，非監督式學習有很多的演算法。

![03_handout_page-0014](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/a6fc3185-a230-4d3c-8a85-18f0c5330405)

4. Semi-supervised Learning Problems 半監督式學習
   - 針對少數的點給予label，大部分的點不給
   - 優點:若要將所有data都進行標記，會很花時間和錢。

![03_handout_page-0015](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/c2404816-d83f-4137-ab2d-ee0b668de9db)

5. Reinforcement Learning
   - 應用
     + 線上廣告系統:廣告系統藉由顧客資料呈現廣告，顧客有點進廣告、沒點進廣告的行為，會讓廣告系統學習如何更好的呈現廣告
   - 通常學習動作會序列的發生，一筆一筆學

![03_handout_page-0016](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/d593b815-3b39-4b78-b01f-3bf86befee8d)
![03_handout_page-0017](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/a01fedb3-f8f5-4f57-bc5e-eefcb54c00a5)

6. 總結

![03_handout_page-0018](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/b8117de4-ea4c-4b0a-8163-e8f0d6437b24)

7. 問題

![03_handout_page-0020](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/7c2b2d06-2867-450d-983c-29bcf0cdac3a)

## Learning with Different Protocol
1. batch learning批次學習: 整批整批的將資料餵給演算法
   - 像填壓式教育
   
![03_handout_page-0021](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/303ab668-e0d6-4c2d-a8f6-a16da16b7c84)
![03_handout_page-0022](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/86da26d0-7be3-4d1e-b253-942174202556)

2. online learning 線上學習: 按順序一筆一筆來學習

![03_handout_page-0023](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/a4f0a6cb-87d0-4f5d-abd2-7bc078443b22)

3. 不管是batch learning或是online learning，機器都是被動的。餵什麼資料進去，他就做什麼。另一種學習方法是: active learning主動學習 
4. Active learning 主動學習: 讓機器有問問題的能力
   - 通常用在如果要取得label會很貴的場合

![03_handout_page-0024](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/87b5a383-05a9-4dae-bba9-28125ca71cd7)

5. 總結

![03_handout_page-0025](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/3a7d1e35-ef1c-466d-907a-94b27cd9d7f9)

6. 問題

![03_handout_page-0027](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/9d741965-5f6a-4ec8-906a-5096ee3bf32c)


7. 補充: 可參考此篇文章 https://medium.com/@kaojia/%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%9203-%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%A8%AE%E9%A1%9E-%E7%9B%A3%E7%9D%A3%E5%BC%8F%E5%AD%B8%E7%BF%92-%E9%9D%9E%E7%9B%A3%E7%9D%A3%E5%BC%8F%E5%AD%B8%E7%BF%92-%E6%89%B9%E6%AC%A1%E5%AD%B8%E7%BF%92-batch-learning-83d60fc861f9

## Learning with Different Input Space
1. Concrete features
   - 具體。從輸入X的角度而言，比較具體的資料，而且跟我們想要做的事情可能有一些關係。實際上他們代表一些已經經過處理的資訊，我們相信這些資訊可以跟我們想要輸出的是有一謝關係的。
   - 例如:在銅板分類的情境中，大小、重量；信用卡分發的情境中，顧客的資料；癌症診斷的情境中，病患的資料。通常這些資料中，都帶有著人類對於這些領域的了解(domain knowledge)。也就是說，我們將人類的專業作為預處理，思考後才去給機器做。這些對機器學習來說，是比較簡單的問題。

![03_handout_page-0028](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/6b7a4d01-b3e3-4fff-901d-812254d11293)
![03_handout_page-0029](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/34079718-1cbf-4af4-9997-ec397d45a716)

2. Raw features
   - 情境:若要做手寫數字辨識，對稱性、密度等等便是concrete features。將16*16像素的圖片，轉乘256維度的向量。點跟點之間的關係，就會是raw features。
   - 越抽象，就代表對機器越困難
   - raw features通常會由機器或人將之轉換成較具體的特徵 -> feature engineering

![03_handout_page-0030](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/9ce17c7f-a4ed-4360-82c9-046104617ddc)
![03_handout_page-0031](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/cc6e2745-1630-4df7-8919-87f1e04472be)

3. Abstract features
   - 若輸入是非常抽象的，例如ID編號(ex:使用者id)
   - 需要從編號中抽取出真正的特徵(ex:使用者的資訊、喜好)
   - 比raw features更抽象，難度也更高

![03_handout_page-0032](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/7979dae0-cc32-43d6-ba2b-d37c600a5905)

4. 總結

![03_handout_page-0033](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/8bb305ab-4221-43ee-ac7b-67a7b5fdea75)

5. 題目

![03_handout_page-0035](https://github.com/FionaYuY/Machine-Learning-Foundations-I/assets/151610467/a60063f6-8d45-49e7-86f2-6eb9e1737b36)
