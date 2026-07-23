# C1w2 - Naive Bayes

📊 **Progress:** `83` Notes | `112` Screenshots

---
<a id="node-biy5eee"></a>

## C1w2 - Naive Bayes

> [!NOTE]
> Learn the theory behind Bayes' rule for conditional probabilities, then apply it 
> toward building a Naive Bayes tweet classifier of your own!
>
>
>
> Learning Objectives
>
>
>
>  • Error analysis
>  • Naive Bayes inference
>  • Log likelihood
>  • Laplacian smoothing
>  • conditional probabilities
>  • Bayes rule
>  • Sentiment analysis
>  • Vocabulary creation
>  • Supervised learning

<br>

<a id="node-ij3f6y9"></a>

## Probability & Bayes's Rule

<br>

<a id="node-wlnn1c4"></a>

<p align="center"><kbd><img src="assets/ao3r1abl455.png" width="80%"></kbd></p>

<br>

<a id="node-1o5bqfy"></a>

<p align="center"><kbd><img src="assets/2qxwlprtig7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là trong corpus các tweets được label positive hay negative.
> Và trong số đó từ happy xuất hiện trong các tweet của cả 2 class

<br>

<a id="node-g60dhbr"></a>

<p align="center"><kbd><img src="assets/kpq0vp1nss9.png" width="80%"></kbd></p>

> [!NOTE]
> Cho A là sự kiện: "1 tweet là positive", thì Probability của A sẽ là tổng số
> sự kiện mà có A xuất hiện (13) chia tổng số sự kiện (20)
>
>
>
> Và Probability mà A ko xuất hiện sẽ là 1 - P(A) với điều kiện là
> tất cả event (tweet) đều được label là Pos hay Neg nhưng không
> được cả hai

<br>

<a id="node-6tfm0z8"></a>

<p align="center"><kbd><img src="assets/k5dwebs77k.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự, cho sự kiện B là '1 tweet có chứa từ 'happy' thì Probability
> của B là số lần B xuất hiện (tổng các tweet chứa từ này) = 4, chia cho
> tổng số sự kiện (tổng số tweet = 20)

<br>

<a id="node-fco6pbk"></a>

<p align="center"><kbd><img src="assets/zvmvx9vww7h.png" width="80%"></kbd></p>

> [!NOTE]
> Và Probability của cả A và B cùng
> xảy ra (intersection) sẽ kí hiệu như vầy

<br>

<a id="node-rpqf5ir"></a>

## Bayes's Rule

<br>

<a id="node-2q80tb5"></a>

<p align="center"><kbd><img src="assets/09svasgxz2om.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về khái niệm tính xác xuất (probability / likelihood) xảy ra
> A. nếu đã xảy ra B (P(A, given B)) thì ta tính **tỉ số các event có A (tweet
> là positive) = 3 \_trong các event có B\_ (tweet có chữ 'happy') = 4 = 75%**
>
>
>
> ta nói **"xác suất 1 tweet có chữ happy là một positive tweet là 75%"**

<br>

<a id="node-vivqnsj"></a>

<p align="center"><kbd><img src="assets/bf9pmq7j0mk.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự, P(B, given A) là: \_**trong các event A**\_ (số Positive tweet)  =
> 13 thì **có bao nhiêu tweet mang chữ 'happy' event B** = 3.
>
>
>
> Ta nói xác suất một tweet positive có chữ happy chỉ là 23,1%

<br>

<a id="node-ctkfmbs"></a>

<p align="center"><kbd><img src="assets/x7zg89uxwa8.png" width="80%"></kbd></p>

> [!NOTE]
> 2 cách 'nói':
> - Khả năng xảy ra B nếu A đã xảy ra
>
>
>
> - Trong các sự kiện A, có bao nhiêu cơ hội cũng xảy ra B

<br>

<a id="node-c7cj1cl"></a>

<p align="center"><kbd><img src="assets/qxqqauiwdgl.png" width="80%"></kbd></p>

> [!NOTE]
> Công thức khái quát
> hoá như sau: 
>
>
>
> Trong các **sự kiện/khả năng** xảy ra 'happy' = **P(happy)** thì: 
>
>
>
> có bao nhiêu **sự kiện/khả năng** vừa có happy vừa có 
> positive = **P(happy giao với positive)**

<br>

<a id="node-6m5qjpm"></a>

<p align="center"><kbd><img src="assets/6zecl75ibho.png" width="80%"></kbd></p>

<br>

<a id="node-1yhtmee"></a>

<p align="center"><kbd><img src="assets/0f3htvajtn9.png" width="80%"></kbd></p>

<br>

<a id="node-hiwgse0"></a>

<p align="center"><kbd><img src="assets/4exkfud6gso.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jmlpc8xm3al.png" width="80%"></kbd></p>

<br>

<a id="node-jgmn06o"></a>

<p align="center"><kbd><img src="assets/0k3oqcq97lck.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là chỉ cần nhớ Bayes rule được
> hình thành từ khái niệm Conditional
> probabilities và công thức

<br>

<a id="node-73t3c3n"></a>

<p align="center"><kbd><img src="assets/8cpgf6r3dp.png" width="80%"></kbd></p>

<br>

<a id="node-0rqgcqj"></a>

## Naive Bayes Introduction

<br>

<a id="node-roe6xao"></a>

> [!NOTE]
> 1 Introduction to Naive Bayes as a method for text classification
>
> 2 The Naive Bayes method is a simple and fast baseline for many text classification
> tasks
>
> 3 The Naive Bayes method makes the assumption that all features used for classification
> are independent
>
> 4 The first step in Naive Bayes is to extract the vocabulary and the word counts from the
> positive and negative corpora
>
> 5 The conditional probabilities of each word given the class are computed by dividing the
> frequency of each word in a class by its corresponding sum of words in the class
>
> 6 A table of conditional probabilities is created, which has the property that the sum of
> probabilities for each class is 1
>
> 7 Some words have a significant difference between probabilities, carrying more weight
> in determining tweet sentiments
>
> 8 The probability function is smoothed to avoid a situation where a word appears in only
> one corpus
>
> 9 The Naive Bayes inference condition rule for binary classification is introduced
>
> 10 The product of probabilities for each word in the tweet is calculated, and a conclusion
> is drawn regarding the sentiment of the tweet
>
> 11 Issues with the implementation are discussed, and the simplification of calculations is
> promised for the next video.

<br>

<a id="node-6kf86e5"></a>

<p align="center"><kbd><img src="assets/875os03nvyg.png" width="80%"></kbd></p>

> [!NOTE]
> Có tên Naive là vì nó ngây thơ giả định rằng các features independent nhau
> nhưng thự tế không phải vậy nhưng vẫn khá tốt trong việc tạo 1 model đơn
> giản cho việc sentiment recognition
>
>
>
> Đại khái là có 2 corpus pos và neg sentence, ta extract tất cả các từ ra
> thành 1 vocab list, rồi đếm số lần mỗi từ xuất hiện trong pos corpus và neg
> corpus rồi tổng lại pos bao nhiêu neg bao nhiêu

<br>

<a id="node-t8bmqoe"></a>

<p align="center"><kbd><img src="assets/h8hnc2slqm7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/etrln4nud48.png" width="80%"></kbd></p>

> [!NOTE]
> Tính P(word,Pos) và P(word, Neg) của
> từng từ để tạo 1 table mới

<br>

<a id="node-o68c1bb"></a>

<p align="center"><kbd><img src="assets/3wxxqbf536w.png" width="80%"></kbd></p>

> [!NOTE]
> Dễ hiểu được tính chất tổng các
> cột đều bằng 1

<br>

<a id="node-n5wptlp"></a>

<p align="center"><kbd><img src="assets/rmq6x7241e8.png" width="80%"></kbd></p>

> [!NOTE]
> Những từ như I, am có P_pos và neg bằng nhau và ko giúp ích gì trong
> sentiment recognition nhưng happy hay sad có 2 chỉ số này chênh lệch ->
> Nó là những power word sẽ có sức nặng để quyết định kết quả của
> sentiment analysis của câu
>
> Còn những từ như because ko xuất hiện trong 1 cột (neg) thì ta sẽ smooth
> cái probability function để giúp P pos hay neg không bằng 0 (để công thức
> Naive Bayes không bị lỗi do chia 0)

<br>

<a id="node-zo2g94m"></a>

<p align="center"><kbd><img src="assets/8hfvusj2h7l.png" width="80%"></kbd></p>

> [!NOTE]
> Phương pháp: Tính product của các tỉ số P_pos và P_neg của các từ trong
> câu, ví dụ câu này ra 1.4 -> Khả năng câu này là positive sentiment

<br>

<a id="node-z4n5h9k"></a>

<p align="center"><kbd><img src="assets/237nmbnl0qf.png" width="80%"></kbd></p>

<br>

<a id="node-iz9n050"></a>

## Laplacian Smoothing

<br>

<a id="node-ue7nn00"></a>

> [!NOTE]
> 1 Counting word **occurrence** for probability calculation
>  2 **Problem with probability of zero** for **unseen word** pairs
>  3 Introduction to **smoothing**
>  4 **Laplacian smoothing** technique to **avoid zero probabilities**
>  5 Formula for Laplacian smoothing
>  6 Calculation of probability using Laplacian smoothing
>  7 Importance of Laplacian smoothing
>  8 Introduction to log likelihood in next video.

<br>

<a id="node-k02d8jw"></a>

<p align="center"><kbd><img src="assets/6dtuqyjh5z4.png" width="80%"></kbd></p>

> [!NOTE]
> "So now all the probabilities in each column will sum to one. This process is
> called Laplacian in smoothing."
>
>
>
> Mình hiểu là cộng 1 trên tử để cho P không bằng 0 dù cho từ ko xuất hiện
> trong cột neg/pos (freq (w|pos) hay freg(w|neg = 0) thì cộng thêm V (số
> unique word) ở dưới để tổng các P theo công thức mới (Laplacian
> smoothing) vẫn = 1
>
>
>
> Nếu có bối rối:
>
>
>
> freq(w1|Pos) +freq(w2|Pos)... = 3 + 3 + 2 +. ..= N_pos = 13
>
>
>
> V là số unique words = 8

<br>

<a id="node-4qnhk1s"></a>

<p align="center"><kbd><img src="assets/nk8m2hbkp9.png" width="80%"></kbd></p>

<br>

<a id="node-ccvx6c3"></a>

<p align="center"><kbd><img src="assets/uz6pjrp9ocf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/wjc6hw0ihrn.png" width="80%"></kbd></p>

> [!NOTE]
> Tính lại Probability table với
> Laplacian smoothing

<br>

<a id="node-q680puo"></a>

<p align="center"><kbd><img src="assets/tjrclrh82rd.png" width="80%"></kbd></p>

<br>

<a id="node-1wcj675"></a>

<p align="center"><kbd><img src="assets/5mnrn4qpeqj.png" width="80%"></kbd></p>

> [!NOTE]
> Với Laplacian Smoothing, P ('because', neg
> class) không còn bằng 0 nữa

<br>

<a id="node-ziylhod"></a>

<p align="center"><kbd><img src="assets/r72bkvmlb1s.png" width="80%"></kbd></p>

> [!NOTE]
> Mục đích là để P ko bằng 0 như trường hợp từ because ở trên có
> P(' Because'. Neg class) = 0 để khi tính công thức Naive Bayes
> không bị lỗi chia 0

<br>

<a id="node-mz92tyb"></a>

<p align="center"><kbd><img src="assets/2s6at8f6gg6.png" width="80%"></kbd></p>

<br>

<a id="node-n2k92r6"></a>

## Log Likelihood P1

<br>

<a id="node-youe127"></a>

> [!NOTE]
> 1 The video introduces the concept of **log likelihood**s, which
> are l**ogarithms of the probabilities** used in sentiment
> classification.
>
> 2 Words are classified as **neutral**, **positive**, or **negative** using
> **conditional probabilities**, and their **ratios** are used for
> classification.
>
> 3 The **ratios** for each word are essential for **Naive Bayes'
> binary classification**, and a mathematical **trick** using
> **logarithms** can be used to **prevent numerical underflow.**
>
> 4 **Lambda** is introduced as the **log of the ratio of the
> probability that a word is positive** **over the probability that it
> is negative**, and it can be used to calculate the log score for
> sentiment classification.
>
> 5 The video emphasizes the **importance** of the **prior ratio** in
> **unbalanced data-sets** and how it affects the Naive Bayes'
> formula for binary classification.

<br>

<a id="node-f3iwne7"></a>

<p align="center"><kbd><img src="assets/immq5k2np9b.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tính thêm cột **ratios** và dùng nó để tính 'tính positive,
> negative hay neutral' của từ. Càng **cao thì càng positive**, càng **gần 0 thì
> càng negative**

<br>

<a id="node-84rfm3c"></a>

<p align="center"><kbd><img src="assets/jpjsqra0tsn.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **Full Naive Bayes** sẽ có thêm 'prior' ratios (P(pos)/P(neg))
> sẽ tính tới sự không cân bằng của dataset, cho tới giờ do Pos
> sentences = Neg sentences nên tỉ số này bằng 1.
>
>
>
> Nói chung là Naive Bayes là 1 algorithm **đơn giản và nhanh** để tạo
> baseline (kiểu như 1 chuẩn/một model prototype để đánh giá)

<br>

<a id="node-43mhtyp"></a>

<p align="center"><kbd><img src="assets/5qnqbjo3d2a.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là do các P đều nhỏ hơn 1 nên làm việc
> với nó dễ bị n**umberical underflow** issue - kiểu như số nó quá
> nhỏ dẫn đến lỗi máy tính.
>
>
>
> Người ta dùng **log** để tính toán giúp giải quyết issue này

<br>

<a id="node-rhgzua4"></a>

<p align="center"><kbd><img src="assets/pwpstlf74r.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ với cách dùng log, thay vì ta tính **TÍCH (Product) của các
> tỉ số** P(w|pos) / P(w|Neg) để ra số rồi xem > 1 thì suy ra Pos <
> 1 thì suy ra Neg thì ..
>
>
>
> với log ta tính **TỔNG (Sum) các log của tỉ số**
> P_pos / P_neg - gọi là lambda thì kết quả cũng như vậy

<br>

<a id="node-v1fqczo"></a>

<p align="center"><kbd><img src="assets/i0w40g1fj3.png" width="80%"></kbd></p>

<br>

<a id="node-lapuo3a"></a>

<p align="center"><kbd><img src="assets/ovidpgyom8q.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/prjmojcjki.png" width="80%"></kbd></p>

<br>

<a id="node-t02svu1"></a>

## Log Likelihood P2

<br>

<a id="node-55vyewa"></a>

> [!NOTE]
> 1 Inference: Learn how to calculate the **log likelihood of a tweet**
> based on the **lambda dictionary**
>
> 2 Log likelihood: **Sum up the lambdas from each word** in the
> tweet to calculate the l**og likelihood**
>
> 3 Sentiment analysis: Determine whether a **tweet is positive or
> negative** based on the **log likelihood value**
>
> 4 Power words: **Words with positive or negative sentiment** have
> more influence on the **log likelihood score**
>
> 5 Decision threshold: The **threshold** for the log likelihood score
> is **0** instead of 1
>
> 6 Training: Introduction to **training a naive bayes model** for
> sentiment analysis.

<br>

<a id="node-i5n1i62"></a>

<p align="center"><kbd><img src="assets/d19bg7qnd1c.png" width="80%"></kbd></p>

> [!NOTE]
> Log likelihood  của 1 tweets là
> tổng các lambda của các từ trong tweet

<br>

<a id="node-uhopj4c"></a>

<p align="center"><kbd><img src="assets/c09cp80g3zt.png" width="80%"></kbd></p>

> [!NOTE]
> Với Log (likelihood) range sẽ là (-infi infi) và decision
> threshold là 0 không phải (0-infi) với threshold 1 nữa

<br>

<a id="node-5s7a71n"></a>

<p align="center"><kbd><img src="assets/9vmxatm298.png" width="80%"></kbd></p>

> [!NOTE]
> Log likelihood của tweet dương thì
> positive, âm thì negative

<br>

<a id="node-8x3uggw"></a>

<p align="center"><kbd><img src="assets/4mqrpz8ixxj.png" width="80%"></kbd></p>

<br>

<a id="node-ad8661h"></a>

## Training Naive Bayes

<br>

<a id="node-hat8zm2"></a>

> [!NOTE]
> 1 Naive Bayes classifier is trained differently from logistic regression or
> deep learning.
>
> 2 The first step in any supervised machine learning project is to **gather** and
> **preprocess** data.
>
> 3 Preprocessing involves **lowercase** texts, **removing** **punctuation**, **URLs**,
> handles, **stop words**, **stemming**, and **tokenizing**.
>
> 4 The next step is to **compute the vocabulary** for each word in each class
> to produce a table of **frequencies** and **conditional probabilities**.
>
> 5 The **Lambda** score for each word is estimated using the **log of the ratio**
> of conditional probabilities.
>
> 6 The **log prior** is estimated by counting the number of positive and
> negative tweets and computing the log of the ratio.
>
> 7 **Training a Naive Bayes** model can be divided into **six logical steps.**
>
> 8 The final step is to **classify sentences** using the **probability table** built in
> the previous steps.

<br>

<a id="node-4h3yi0b"></a>

<p align="center"><kbd><img src="assets/qh5lhtabeuj.png" width="80%"></kbd></p>

> [!NOTE]
> Bước 0 là chuẩn bị data và bước 1 Preprocess data
>
>
>
> Trong thực tế bước preprocess có thể chiếm nhiều thời gian
> hơn là trong assignment này

<br>

<a id="node-lyoi13n"></a>

<p align="center"><kbd><img src="assets/w5wf16epcm.png" width="80%"></kbd></p>

> [!NOTE]
> Bước 2 là đếm số lần 1 từ xuất hiện trong pos corpus và neg corpus

<br>

<a id="node-ia0jjmh"></a>

<p align="center"><kbd><img src="assets/bcd61gkrmgl.png" width="80%"></kbd></p>

> [!NOTE]
> Step 3 và 4 là tính **Conditional Probability** P(w,Pos) và
> P(w, Neg) của mỗi từ và lambda (log của ratios Ppos/Pneg)

<br>

<a id="node-j1cixic"></a>

<p align="center"><kbd><img src="assets/xu3xzpy8zi9.png" width="80%"></kbd></p>

> [!NOTE]
> Kế là tính log prior vốn trong assignment này do
> balanced nên = 0 nhưng trong unbalanced dataset
> thì chỉ số này có thể quan trọng

<br>

<a id="node-k3tj66c"></a>

<p align="center"><kbd><img src="assets/nb7bon3nvxb.png" width="80%"></kbd></p>

<br>

<a id="node-gykbyfk"></a>

## Lab: Visualizing Likelihoods And Confidence

<br>

<a id="node-mw4uiri"></a>

> [!NOTE]
> In this lab, we will cover an **essential part of data analysis** that has not
> been included in the lecture videos. As we stated in the previous module,
> **data visualization** gives **insight** into the **expected performance** of
> any model.
>
> In the following exercise, you are going to make a **visual inspection** of
> the tweets dataset using the **Naïve Bayes features**. We will see how we
> can understand the **log-likelihood ratio** explained in the videos as a pair
> of numerical features that can be fed in a machine learning algorithm.
>
> At the end of this lab, we will introduce the concept of **confidence ellipse**
> as a tool for representing the **Naïve Bayes** model visually.

<br>

<a id="node-0lak0ti"></a>

#### Import

<br>

<a id="node-68kv1mc"></a>

<p align="center"><kbd><img src="assets/ha4q5ipdyb7.png" width="80%"></kbd></p>

<br>

<a id="node-jy6ec3u"></a>

#### Calculate the likelihoods for each tweet

<br>

<a id="node-4vbis7x"></a>

<p align="center"><kbd><img src="assets/bjx487eyrzw.png" width="80%"></kbd></p>

> [!NOTE]
> Log likelihood của một từ w là log của
> ratios P(w, pos) và P(w, neg)
>
>
>
> Thì ở đây định nghĩa thêm Log likelihood của 1 câu tweet là 
> log của ratios giữa P(tweet, pos) và P(tweet, neg)
>
>
>
> P(tweet, pos) là tích các P(word, pos) trong câu
> tương tự P(tweet, neg) cũng là tích các P(w, neg) trong câu
>
>
>
> Nên ta có Log (P(tweet, pos)/P(tweet, neg)) 
>
>
>
> = log(P(tweet, pos)) - log(P(tweet, neg)) 
> (do Log(a/b) = log(a)-log(b)
>
>
>
> = log[P(w1, pos)*P(w2, pos) ...P(wn, pos)] - log[P(w1, neg)*P(w2, neg) ...P(wn, neg)]
>
>
>
> = [ log(P(w1, pos) + log(P(w2, pos) + ...log(P(wn, pos) ]
> - [ log(P(w1, neg) + log(P(w2, neg) + ...log(P(wn, neg) ]

<br>

<a id="node-cwzuzh3"></a>

<p align="center"><kbd><img src="assets/iij5ie5rmaq.png" width="80%"></kbd></p>

<br>

<a id="node-nl9jssg"></a>

<p align="center"><kbd><img src="assets/olraatjzi4.png" width="80%"></kbd></p>

<br>

<a id="node-408uaxd"></a>

> [!NOTE]
> Using Confidence Ellipses to
> interpret Naïve Bayes

<br>

<a id="node-hpcxpid"></a>

<p align="center"><kbd><img src="assets/k7uhrhfnij.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu lắm như đại khái là vẽ cái phân bố (distribution) của
> data theo Confidence Ellipses sẽ giúp có cái nhìn tốt hơn là chỉ
> vẽ khơi khơi (Cartesian plane). Tốt hơn ở đây chắc là thể hiện
> thêm các cấp phân bố standard deviation mấy cái đường
> ellipse chấm chấm

<br>

<a id="node-5dal0cd"></a>

<p align="center"><kbd><img src="assets/dfxnfetpcs.png" width="80%"></kbd></p>

<br>

<a id="node-ue4ie6a"></a>

<p align="center"><kbd><img src="assets/mudug7flm0a.png" width="80%"></kbd></p>

<br>

<a id="node-eh18cfa"></a>

<p align="center"><kbd><img src="assets/7t4grrsjjur.png" width="80%"></kbd></p>

<br>

<a id="node-5od2d2g"></a>

<p align="center"><kbd><img src="assets/kauu99r050b.png" width="80%"></kbd></p>

<br>

<a id="node-e1gaf5w"></a>

<p align="center"><kbd><img src="assets/lgq60bpxxbh.png" width="80%"></kbd></p>

<br>

<a id="node-xrtkphs"></a>

## Testing Naive Bayes

<br>

<a id="node-hize6yx"></a>

> [!NOTE]
> 1 The main task is to apply the Naive Bayes classifier on **real test examples.**
>
> 2 The **conditional probabilities** are used to predict the sentiment of new unseen tweets.
>
> 3 The **model performance** is evaluated using a **test set** of annotated tweets.
>
> 4 **Pre-processing of text** is necessary before applying the model to predict sentiments.
>
> 5 The model can only give a score for words **it's seen before.**
>
> 6 The **score obtained** from the model can be used to predict whether a tweet has
> positive or negative sentiment.
>
> 7 **Validation set** is used to measure the performance of the trained model.
>
> 8 The **accuracy function** is implemented to **measure the performance of the model**.
>
> 9 The score of each entry in the validation set is computed and evaluated to get a vector of
> zeros and ones indicating whether the predicted sentiment is negative or positive,
> respectively.
>
> 10 The **accuracy of the model** is computed by **comparing the predicted labels** with
> the **true labels** provided in the validation set.
>
> 11 The words that don't appear in the Lambda table are treated as **neutral words.**
>
> 12 The Naive Bayes method is applied to classify tweets in the coding exercise at the end
> of the week.

<br>

<a id="node-umtebju"></a>

<p align="center"><kbd><img src="assets/yymw27hcct.png" width="80%"></kbd></p>

<br>

<a id="node-pp60b9x"></a>

<p align="center"><kbd><img src="assets/qyt49tnre7l.png" width="80%"></kbd></p>

<br>

<a id="node-diuscun"></a>

<p align="center"><kbd><img src="assets/uzrccdo4aq.png" width="80%"></kbd></p>

> [!NOTE]
> Nhớ rằng cái model này không có params gì hết, cơ bản chỉ là đếm, nên predict
> 1 tweet mới ta sẽ preprocess nó thành vector các từ, rồi tính tổng các lambda
> của các từ đó, từ nào ko có trong table thì thôi, rồi cộng với log prior ra kết quả
> so với 0 để kết luận

<br>

<a id="node-24iqov2"></a>

<p align="center"><kbd><img src="assets/hchao3avy0b.png" width="80%"></kbd></p>

> [!NOTE]
> Evaluate đv CV set.

<br>

<a id="node-16gz3n1"></a>

<p align="center"><kbd><img src="assets/kuhzoj4rxq9.png" width="80%"></kbd></p>

<br>

<a id="node-s6mg9sj"></a>

<p align="center"><kbd><img src="assets/fh4185673u.png" width="80%"></kbd></p>

<br>

<a id="node-7p40zoz"></a>

## Application Of Naive Bayes

<br>

<a id="node-ac9hjwc"></a>

> [!NOTE]
> 1 Naive Bayes method can be used for v**arious classification tasks**, such as **sentiment
> analysis**, **author identification, spam filtering, information retrieval, and word
> disambiguation.** 
> 2 The **Naive Bayes formula** calculates the **ratio between** the **conditional probabilities of the
> priors** and **likelihoods to estimate the probability for each class**.
>
> 3 Naive Bayes can be used for **author identification** by training a model to recognize
> whether a new document was written by one author or another, based on their **unique
> writing style.**
>
> 4 **Spam filtering** can be performed using Naive Bayes by **analyzing the sender, subject,
> and content** of an email to determine whether it is spam or not.
>
> 5 **Information retrieval** can be done using Naive Bayes by calculating the **likelihood** of
> **documents given a query** and storing them based on their likelihoods.
>
> 6 Naive Bayes can be used for **word disambiguation** by **calculating the score of the
> documents given that a word refers to each possible meaning**, and choosing the one with
> the highest score.
>
> 7 Naive Bayes is a **popular method** due to its **simplicity** in training, use, and interpretation.
>
> 8 The assumptions underlying the Naive Bayes method will be discussed in the upcoming
> videos.

<br>

<a id="node-ymvylup"></a>

<p align="center"><kbd><img src="assets/2uwgs3pzp3e.png" width="80%"></kbd></p>

<br>

<a id="node-p3a0k77"></a>

<p align="center"><kbd><img src="assets/ngsl3vmc8s.png" width="80%"></kbd></p>

<br>

<a id="node-pyn3lbk"></a>

<p align="center"><kbd><img src="assets/s8mxjs0ijq.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu lắm

<br>

<a id="node-bxpanri"></a>

<p align="center"><kbd><img src="assets/hej2dtieqs.png" width="80%"></kbd></p>

<br>

<a id="node-lxpaivl"></a>

<p align="center"><kbd><img src="assets/ulmr2n8jhw.png" width="80%"></kbd></p>

<br>

<a id="node-ju2etrl"></a>

<p align="center"><kbd><img src="assets/kipc13rx7wk.png" width="80%"></kbd></p>

> [!NOTE]
> Note: Bayes Rule thường dùng
> như 1 simple baseline

<br>

<a id="node-ws90klz"></a>

## Naive Bayes Assumptions

<br>

<a id="node-5w6pbeg"></a>

> [!NOTE]
> 1 The main **assumption** underlying the naïve bayes method is **independence**
> of **words in a sentence.**
>
> 2 Naïve bayes is a **simple** model that **doesn't require setting custom
> parameter**s.
>
> 3 Naïve bayes assumes **independence** between the predictors or **features**
> associated with each class, which may **not always be the case.**
>
> 4 Naïve bayes could l**ead to under or overestimation** of the **conditional
> probabilities of individual words.**  5 Naïve bayes **relies on the distribution of the
> training data sets**, which could result in an **overly optimistic or pessimistic
> model**.
>
> 6 The assumption of **independence in naïve bayes is difficult to guarantee**, but
> the model **works well in certain situations.**
>
> 7 The relative frequency of positive and negative tweets in training data sets needs
> to be balanced for accurate results.
>
> 8 If naïve bayes fails to perform well, there are solutions to improve its
> performance, which will be covered in the next video.

<br>

<a id="node-4f5acfc"></a>

<p align="center"><kbd><img src="assets/ofiruj6azrr.png" width="80%"></kbd></p>

<br>

<a id="node-vhens3j"></a>

<p align="center"><kbd><img src="assets/vcvi0ywp0f.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Naive Bayes assume các từ độc lập với nhau và rõ ràng là
> không đúng (ví dụ 'hot' và 'sunny' có quan hệ rõ ràng với 'desert', do đó
> nó không nắm bắt được các liên hệ giữa các Từ. Các course sau sẽ nói
> đến các model làm tốt hơn việc này (RNN, Transformer).

<br>

<a id="node-x9vxl2g"></a>

<p align="center"><kbd><img src="assets/2voz6zmognb.png" width="80%"></kbd></p>

> [!NOTE]
> Dẫn đến trong vấn đề dưới nó sẽ tính ra P
> của các chữ đều bằng nhau.

<br>

<a id="node-tdcu96f"></a>

<p align="center"><kbd><img src="assets/mju4vlicm2.png" width="80%"></kbd></p>

> [!NOTE]
> Cái thứ hai đại khái là nó **phụ thuộc vào data distribution của dataset
> mà vốn các bộ data này thường được cleaned và artificially balanced**
> như tweet dataset trong khi đó thường trong thực tế sẽ nhiều positive
> tweet hơn do cái negative bị banned hoặc user muted (???) negative
> tweet. Đại khái là do đó Naive Bayes ko thể phản ánh đúng thực tế như
> thế nào và dẫn đến model bị **overconfidence** hay **overpessimistic**

<br>

<a id="node-w1b8gi9"></a>

<p align="center"><kbd><img src="assets/2gn2wcx33jt.png" width="80%"></kbd></p>

> [!NOTE]
> Dù vậy nó vẫn tốt trong
> một số trường hợp

<br>

<a id="node-f64am7f"></a>

## Error Analysis

<br>

<a id="node-evi6q7s"></a>

> [!NOTE]
> 1 **NLP errors** are **inevitable** no matter what method you use
>
> 2 Errors in NLP can be caused by **loss of semantic meaning**, **word**
> **order**, and **language quirks** that are **difficult for machines** to understand
>
> 3 It's important to **analyze processed text** to ensure accurate results,
> including **checking for punctuation and word removal**
>
> 4 **Naïve base classification** relies on word **frequency** **counts** and can
> lead to **errors due to its independence assumption**
>
> 5 **Word vectors** can be used to improve NLP results
>
> 6 Naïve base classification may fail in cases of **adversarial attacks,**
> which are **language phenomena like sarcasm, irony, and euphemism**
> that machines have **difficulty understanding.**

<br>

<a id="node-6pqo1z3"></a>

<p align="center"><kbd><img src="assets/r35osbx0mcl.png" width="80%"></kbd></p>

<br>

<a id="node-bhe9qvd"></a>

<p align="center"><kbd><img src="assets/o1ljews4ow.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nhớ lại 1 điểm lưu ý trong Processing bữa trước khi
> removing **Punctuation** phải cẩn thận vì đôi khi nó chứa thông tin quan
> trọng, ví dụ bỏ cái mặt buồn ở dưới thôi là thay đổi hết ý nghĩa câu

<br>

<a id="node-nfr67cn"></a>

<p align="center"><kbd><img src="assets/8xnfi14donl.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự với Stop Words

<br>

<a id="node-p4l2cwz"></a>

<p align="center"><kbd><img src="assets/wiue3efzk8h.png" width="80%"></kbd></p>

> [!NOTE]
> Word order nữa, nói chung là những model sau như RNN, Attention và
> Transformer sẽ handle dc những ca này

<br>

<a id="node-d463s5o"></a>

<p align="center"><kbd><img src="assets/i3tz87rapq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là sao đó mà câu positive sau khi
> preprocess thì nghe rất negative

<br>

<a id="node-6g3p87x"></a>

> [!NOTE]
> An adversarial attack in the context of naïve Bayes refers to a situation
> where the model misclassifies a text input due to the use of language
> phenomena such as **sarcasm, irony, or euphemism.** These language phenomena can be **easily understood by humans**
> but can be **challenging for machines** to interpret. In the given
> example, the text "This is a ridiculously powerful movie. The plot was
> gripping and I cried right through until the ending" contains **positive**
> language, but the **pre-processing step used by naïve Bayes** to
> extract features and analyze sentiment may **incorrectly classify it as
> negative** due to the presence of words like "**ridiculous**" or "cried."
>
> This can **result in inaccurate sentiment analysis** and affect the
> overall performance of the model. To avoid such adversarial attacks, it
> is important to use **more sophisticated models** that can better
> understand the nuances of language and context. (GPT)
>
> Đại khái cái sao đó chính là hiện tượng gọi là Adversarial
> attack, model quá đơn giản như Naive Bayes ko nắm bắt
> được sự 'lắt léo' trong ngôn ngữ khiến nó ko hiểu được ý
> nghĩa positive của câu trên

<br>

<a id="node-t1zb29e"></a>

## Week Conclusion

<br>

<a id="node-gtydt69"></a>

## Quiz

<br>

<a id="node-zsu8dwk"></a>

<p align="center"><kbd><img src="assets/1hzho0bbqlb.png" width="80%"></kbd></p>

<br>

<a id="node-6kdx3bx"></a>

<p align="center"><kbd><img src="assets/j8szpbdmmm8.png" width="80%"></kbd></p>

<br>

<a id="node-jlng1cv"></a>

<p align="center"><kbd><img src="assets/gb8yc4feb7i.png" width="80%"></kbd></p>

<br>

<a id="node-j8nr2jr"></a>

<p align="center"><kbd><img src="assets/g8dap1ojdju.png" width="80%"></kbd></p>

<br>

<a id="node-77gpcuc"></a>

<p align="center"><kbd><img src="assets/xa33q3rez2q.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0bhxkob7je1.png" width="80%"></kbd></p>

> [!NOTE]
> Không hiểu sao sai

<br>

<a id="node-m4aj7dz"></a>

<p align="center"><kbd><img src="assets/rwp1fy7k1bf.png" width="80%"></kbd></p>

<br>

<a id="node-yjt1e25"></a>

<p align="center"><kbd><img src="assets/g9otow6nmu.png" width="80%"></kbd></p>

<br>

<a id="node-51lqp0l"></a>

<p align="center"><kbd><img src="assets/l3dib4lhbo.png" width="80%"></kbd></p>

<br>

<a id="node-kwab4yd"></a>

<p align="center"><kbd><img src="assets/xhxqayrc0zd.png" width="80%"></kbd></p>

<br>

<a id="node-qsg6083"></a>

<p align="center"><kbd><img src="assets/hyhzm4me7ih.png" width="80%"></kbd></p>

<br>

<a id="node-ol183sa"></a>

## PROGRAMMING ASSIGNMENT: Naive Bayes

<br>

<a id="node-lfx7uyd"></a>

> [!NOTE]
> Welcome to week two of this specialization. You will learn about **Naive
> Bayes**. Concretely, you will be using Naive Bayes for **sentiment analysis** on
> **tweets**. Given a tweet, you will decide if it has a positive sentiment or a
> negative one. Specifically you will:
>
> • **Train a naive bayes model** on a **sentiment analysis task**
>
> • **Test using your model**
>
> • **Compute ratios of positive words to negative words**
>
> • Do some **error analysis**
>
> • Predict on your own tweet
>
> You may already be familiar with Naive Bayes and its justification in terms of
> **conditional probabilities** and **independence**.
>
> • In this week's lectures and assignments we used the **ratio of probabilities
> between positive and negative sentiment.**
>
> • This approach gives us simpler formulas for these 2-way classification
> tasks.

<br>

<a id="node-2mgc1l4"></a>

#### Importing Functions and Data

<br>

<a id="node-07ntd95"></a>

> [!NOTE]
> from utils import process_tweet, lookup
> import pdb
> from **nltk.corpus** import **stopwords**, **twitter_samples**
> import numpy as np
> import pandas as pd
> import nltk
> import string
> from nltk.tokenize import **TweetTokenizer**
> from os import getcwd
> import w2_unittest
>
> **nltk.download('twitter_samples')
> nltk.download('stopwords')**

<br>

<a id="node-2gr2gup"></a>

<p align="center"><kbd><img src="assets/qd055zwefn.png" width="80%"></kbd></p>

> [!NOTE]
> If you are running this notebook in your local computer, don't
> forget to download the tweeter samples and stopwords from nltk.
>
>
>
> nltk.download('stopwords') nltk.download('twitter_samples')

<br>

<a id="node-7orhv0h"></a>

> [!NOTE]
> filePath = f"{getcwd()}/../tmp2/"
> nltk.data.path.append(filePath)
>
> \\/# **get the sets of positive and negative tweets**\\/
> all_positive_tweets = twitter_samples.strings('**positive_tweets.json**')
> all_negative_tweets = twitter_samples.strings('**negative_tweets.json**')
>
> \\/# **split the data into two pieces**, one for training and one for testing (validation set)
> \\/test_pos = all_positive_tweets[**4000**:]
> train_pos = all_positive_tweets[:**4000**]
> test_neg = all_negative_tweets[4000:]
> train_neg = all_negative_tweets[:4000]
>
> train_x = train_pos + train_neg
> test_x = test_pos + test_neg
>
> **# avoid assumptions about the length of all_positive_tweets**
> train_y = np.append(np.ones(len(train_pos)), np.zeros(len(train_neg)))
> test_y = np.append(np.ones(len(test_pos)), np.zeros(len(test_neg)))

<br>

<a id="node-cd8vq6u"></a>

#### 1 - Process the Data

<br>

<a id="node-nk4iitd"></a>

> [!NOTE]
> For any machine learning project, once you've gathered the data, **the first step is to process it** to make useful inputs to your model.
>
> **Remove noise**: You will first want to remove noise from your data -- that is, **remove words
> that don't tell you much** about the content. These include all **common words like 'I, you, are,
> is**, etc...' that would not give us enough information on the sentiment.
>
> We'll also remove **stock market tickers**, **retweet** **symbols**, **hyperlinks**, and **hashtags**
> because they can not tell you a lot of information on the sentiment. You also want to remove all
> the **punctuation** from a tweet. The reason for doing this is because we want to **treat words
> with or without the punctuation** as the same word, instead of treating "happy" , "happy?", "
> happy!", "happy," and "happy." as different words.
>
> Finally you want to use **stemming** to only keep track of one variation of each word. In other
> words, we'll treat "motivation", "motivated", and " motivate" similarly by grouping them within the
> same stem of **"motiv-"**. We have given you the function \\/**process_tweet**\\/ that does this for
> you.

<br>

<a id="node-w4hts5k"></a>

> [!NOTE]
> custom_tweet = "RT @Twitter @chapagain Hello There! Have a great
> day. :) #good #morning http://chapagain.com.np"
>
> # print cleaned tweet print(process_tweet(custom_tweet))
> -> ['hello', 'great', 'day', ':)', 'good', 'morn']

<br>

<a id="node-bytoog9"></a>

> [!NOTE]
> 1.1 - Implementing your
> Helper Functions

<br>

<a id="node-y37ysk9"></a>

> [!NOTE]
> To help you train your naive bayes model, you will need to **compute a dictionary** where the **keys are a tuple
> (word, label)** and the values are the corresponding **frequency**. Note that the labels we'll use here are 1 **for
> positive and 0 for negative**.
>
> You will also implement a **lookup helper function** that takes in the **freqs** **dictionary**, a **word**, and a
> **label** (1 or 0) and **returns the number of times that word and label tuple appears in the collection of tweets.**
>
> For example: given a list of tweets ["I am rather excited", "you are rather happy"] and the label 1, the function will
> return a dictionary that contains the following key-value pairs:
>
> { ("rather", 1): 2, ("happi", 1) : 1, ("excit", 1) : 1 }
>
> - Notice how for each word in the given string, the same label 1 is assigned to each word.
>
> - Notice how the words "I" and "am" are not saved, since it was removed by **process_tweet** because it is a
> **stopword**.
>
> - Notice how the word " rather" appears twice in the list of tweets, and so its count value is 2.

<br>

<a id="node-c165nve"></a>

##### Exercise 1 - count_tweets

<br>

<a id="node-d1kqhvl"></a>

> [!NOTE]
> Create a function **count_tweets** that **takes a list of tweets** as input, **cleans** all of them, and **returns a
> dictionary**.
>
> - The **key** in the dictionary is a **tuple containing the stemmed word and its class label,** e.g. ("happi",1).
>
> - The **value** the **number of times this word appears in the given collection of tweet**s (an integer).
>
> **Hints**
>
> • Please use the `**process_tweet**` function that was imported above, and then store the words in their respective
> dictionaries and sets.
>
> • You may find it useful to use the `**zip**` function to match each element in `tweets` with each element in `ys`.
>
> • Remember to **check** if the key in the dictionary **exists** before adding that key to the dictionary, or
> incrementing its value.
>
> • Assume that the `result` dictionary that is input will contain clean key-value pairs (you can assume that the values
> will be integers that can be incremented). It is **good practice to check the datatype** before **incrementing** the
> value, but it's not required here.

<br>

<a id="node-pf5vsfi"></a>

<p align="center"><kbd><img src="assets/u46ybcw91r.png" width="80%"></kbd></p>

<br>

<a id="node-uohpubq"></a>

<p align="center"><kbd><img src="assets/pcljujf9eqd.png" width="80%"></kbd></p>

<br>

<a id="node-mk5boib"></a>

> [!NOTE]
> 2 - Train your Model
> using Naive Bayes

<br>

<a id="node-5juxwao"></a>

##### Some explaination

<br>

<a id="node-3uwmohi"></a>

<p align="center"><kbd><img src="assets/h42xc4uple7.png" width="80%"></kbd></p>

<br>

<a id="node-8lspezv"></a>

<p align="center"><kbd><img src="assets/4so34ozbgum.png" width="80%"></kbd></p>

> [!NOTE]
> Phòng khi bối rối ngu đột xuất để rồi không hiểu tại sao logprior lại bằng
> log(Dpos/Dneg) thì P(Dpos) = Dpos/D, P(Dneg) = Dneg/D Nên chia hai thằng
> đó cho nhau ra Dpos/Dneg

<br>

<a id="node-bxd5yl0"></a>

<p align="center"><kbd><img src="assets/51liw785zkt.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/k0p3h71zxb.png" width="80%"></kbd></p>

<br>

<a id="node-hozvdnb"></a>

> [!NOTE]
> \\/**Create freqs dictionary** \\/
>
> • Given your **count_tweets** function, you can compute a dictionary
> called **freqs** that contains all the frequencies.
>
> • In this freqs dictionary, the **key** is the tuple **(word, label)**
>
> • The value is the **number of times it has appeared**.
>
> We will use this dictionary in several parts of this assignment.

<br>

<a id="node-ikn915t"></a>

> [!NOTE]
> # Build the freqs dictionary for later uses
> freqs = count_tweets({}, train_x, train_y)

<br>

<a id="node-qm9cdu5"></a>

> [!NOTE]
> Exercise 2 -
> train_naive_bayes

<br>

<a id="node-i8fd78v"></a>

<p align="center"><kbd><img src="assets/qqgnkasy5ws.png" width="80%"></kbd></p>

<br>

<a id="node-em2ta23"></a>

<p align="center"><kbd><img src="assets/e5jeqe8hvx7.png" width="80%"></kbd></p>

<br>

<a id="node-ctj4ca1"></a>

<p align="center"><kbd><img src="assets/nih24ssnao.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/yozkwa4f4yk.png" width="80%"></kbd></p>

> [!NOTE]
> len(y==1) là ra y xì len của y, nhớ nha vì y==1 ra 1 vector
> dài bằng y chưa các kết quả so sánh các vị trí của y với 1.
> giống thì bằng 1, khác thì = 0. Nên phải sum mới đúng
>
> Cách làm như này rất gọn mà Python nó mạnh những cái như vậy
> vocab = set([key[0] for key in freqs])

<br>

<a id="node-fhs3541"></a>

<p align="center"><kbd><img src="assets/hjnfgq1cx4l.png" width="80%"></kbd></p>

<br>

<a id="node-n7u4ahr"></a>

#### 3 - Test your Naive Bayes

<br>

<a id="node-t467qqn"></a>

##### Exercise 3 - naive_bayes_predict

<br>

<a id="node-116zxfj"></a>

<p align="center"><kbd><img src="assets/ox8z010jdkr.png" width="80%"></kbd></p>

<br>

<a id="node-7r7q9g1"></a>

> [!NOTE]
> Note 
>
> Note we calculate the **prior** from the **training data**,
> and that the training data is evenly split between positive
> and negative labels (4000 positive and 4000 negative
> tweets). This means that the ratio of positive to negative 1,
> and the logprior is **0.**
>
> The value of 0.0 means that when we add the logprior to
> the log likelihood, we're just adding zero to the log
> likelihood. However, please remember to include the
> logprior, because whenever the data is not perfectly
> balanced, the logprior will be a non-zero value.

<br>

<a id="node-vosjb0p"></a>

<p align="center"><kbd><img src="assets/ef3rhafg17s.png" width="80%"></kbd></p>

<br>

<a id="node-9hq0ap7"></a>

<p align="center"><kbd><img src="assets/r9xbt5e7c5.png" width="80%"></kbd></p>

<br>

<a id="node-yy4u8lo"></a>

##### Exercise 4 - test_naive_bayes

<br>

<a id="node-tblta79"></a>

> [!NOTE]
> Implement test_naive_bayes. **Instructions**:
>
> • Implement **test_naive_bayes** to check the accuracy of your
> predictions.
>
> • The function takes in your **test_x**, **test_y**, **log_prior**, and
> **loglikelihood**
>
> • It returns the accuracy of your model.
>
> • First, use **naive_bayes_predict** function to make predictions
> for each tweet in test_x.

<br>

<a id="node-s5uak5c"></a>

<p align="center"><kbd><img src="assets/ii40sgas2h8.png" width="80%"></kbd></p>

> [!NOTE]
> Nhờ câu hint mà làm thôi
>
>
>
> # error is the average of the **absolute** values of the  **differences**
> between y_hats and test_y
>
>
>
> differences -> Trừ nhau chứ gì**,** average -> sum./len**.**  Nhớabsolute nữa, không nó ra âm
>
>
>
> error = np.abs(np.sum(y_hats - test_y)/len(test_y))
>
> abs(y^-y) chứ ko phải sum hết rồi mới abs

<br>

<a id="node-3h8mjek"></a>

<p align="center"><kbd><img src="assets/ma4vptzhx4l.png" width="80%"></kbd></p>

<br>

<a id="node-b90tow7"></a>

> [!NOTE]
> # UNQ_C7 (UNIQUE CELL IDENTIFIER, DO NOT EDIT)
> # Run this cell to test your function
> for tweet in ['I am happy', 'I am bad', 'this movie should have been great.', 'great', 'great great', 'great great great', 'great great great great']:
>     # print( '%s -> %f' % (tweet, naive_bayes_predict(tweet, logprior, loglikelihood)))
>     p = naive_bayes_predict(tweet, logprior, loglikelihood)
> #     print(f'{tweet} -> {p:.2f} ({p_category})')
>     print(f'{tweet} -> {p:.2f}')
>
> ->
> I am happy -> 2.14
> I am bad -> -1.31
> this movie should have been great. -> 2.12
> great -> 2.13
> great great -> 4.26
> great great great -> 6.39
> great great great great -> 8.52

<br>

<a id="node-lohv7b2"></a>

<p align="center"><kbd><img src="assets/pugejznhbb8.png" width="80%"></kbd></p>

<br>

<a id="node-hdk8hcd"></a>

> [!NOTE]
> 4 - Filter words by Ratio of
> Positive to Negative Counts

<br>

<a id="node-565arho"></a>

> [!NOTE]
> • Some words have **more positive counts** than others, and can be
> considered "more positive". Likewise, some words can be considered
> more negative than others.
>
> • One way for us to define the level of positiveness or negativeness,
> without calculating the log likelihood, is to compare the positive to
> negative frequency of the word.
>
> ▪ Note that we can also use the log likelihood calculations to compare
> relative positivity or negativity of words.
>
> • We can calculate the ratio of positive to negative frequencies of a
> word.
>
> • Once we're able to calculate these ratios, we can also **filter a subset of
> words** that have a **minimum ratio of positivity / negativity** or higher.
>
> • Similarly, we can also filter a subset of words that have a maximum
> ratio of positivity / negativity or lower (words that are at least as
> negative, or even more negative than a given threshold).

<br>

<a id="node-uaupvma"></a>

##### Exercise 5 - get_ratio

<br>

<a id="node-joh89sa"></a>

<p align="center"><kbd><img src="assets/0xfm5mavzrjd.png" width="80%"></kbd></p>

<br>

<a id="node-xsvg3mk"></a>

<p align="center"><kbd><img src="assets/uftfslie9bn.png" width="80%"></kbd></p>

<br>

<a id="node-o6lrgpz"></a>

> [!NOTE]
> Exercise 6 -
> get_words_by_threshold

<br>

<a id="node-1pc1f8m"></a>

<p align="center"><kbd><img src="assets/qnuq6d2q9mp.png" width="80%"></kbd></p>

<br>

<a id="node-30b2l60"></a>

<p align="center"><kbd><img src="assets/uihyd89gm9p.png" width="80%"></kbd></p>

<br>

<a id="node-4b767be"></a>

<p align="center"><kbd><img src="assets/ln950jqm938.png" width="80%"></kbd></p>

> [!NOTE]
> Notice the difference between the positive and negative ratios.
> Emojis like **:(** and words like '**me**' **tend to have a negative**
> connotation. Other words like glad, community, arrives, tend to
> be found in the positive tweets.

<br>

<a id="node-ffi2t66"></a>

#### 5 - Error Analysis¶

<br>

<a id="node-lbf9ywf"></a>

> [!NOTE]
> # Some error analysis done for you
> print('Truth Predicted Tweet')
> for x, y in zip(test_x, test_y):
>     y_hat = naive_bayes_predict(x, logprior, loglikelihood)
>     if y != (np.sign(y_hat) > 0):
>         print('%d\\t%0.2f\\t%s' % (y, np.sign(y_hat) > 0, ' '.join(
>             process_tweet(x)).encode('ascii', 'ignore')))
>
> In this part you will see some tweets that your model
> missclassified. Why do you think the missclassifications
> happened? Were there any assumptions made by your
> naive bayes model?

<br>

<a id="node-9fzlu81"></a>

> [!NOTE]
> Truth Predicted Tweet
> 1 0.00 b'truli later move know queen bee upward bound movingonup'
> 1 0.00 b'new report talk burn calori cold work harder warm feel better weather :p'
> 1 0.00 b'harri niall 94 harri born ik stupid wanna chang :D'
> 1 0.00 b'park get sunlight'
> 1 0.00 b'uff itna miss karhi thi ap :p'
> 0 1.00 b'hello info possibl interest jonatha close join beti :( great'
> 0 1.00 b'u prob fun david'
> 0 1.00 b'pat jay'
> 0 1.00 b'sr financi analyst expedia inc bellevu wa financ expediajob job job hire'

<br>

<a id="node-mi69xel"></a>

#### 6 - Predict with your own Tweet

<br>

<a id="node-rv99iu6"></a>

> [!NOTE]
> # Test with your own tweet - feel free to modify `my_tweet`
> my_tweet = 'I am happy because I am learning :)'
>
> p = naive_bayes_predict(my_tweet, logprior, loglikelihood)
> print(p)
>
> -> 9.571143871339594
>
> Congratulations on completing this
> assignment. See you next week!

<br>

