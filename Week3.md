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

