# C1w1_logistic Regression

📊 **Progress:** `64` Notes | `113` Screenshots

---
<a id="node-ky4woqh"></a>

## C1w1_logistic Regression

> [!NOTE]
> Learn to extract features from text into numerical vectors, then build a binary 
> classifier for tweets using a logistic regression!
>
>
>
> Learning Objectives
>
>
>
>  • Sentiment analysis
>  • Logistic regression
>  • Data pre-processing
>  • Calculating word frequencies
>  • Feature extraction
>  • Vocabulary creation
>  • Supervised learning

<br>

<a id="node-fhb2l42"></a>

## Welcome To NLP Spec

<br>

<a id="node-mj5e60l"></a>

> [!NOTE]
> 1 Introduction of Younes and Lukasz as instructors of the
> specialization.
>
> 2 Overview of the development of NLP from rule-based systems to
> deep learning-based systems.
>
> 3 The rise of end-to-end systems and attention models in NLP.
>
> 4 Overview of the four courses in the specialization, starting with
> classification and vector spaces in the first course.
>
> 5 The second course focuses on probabilistic models in NLP.
>
> 6 The third course teaches sequence models.
>
> 7 The fourth course focuses on attention models and their applications
> in chatbots, question answering, and text summarization.
>
> 8 The potential impact of these models in industry, including call
> centers and data analysis.
>
> 9 Excitement about learning and building NLP systems.

<br>

<a id="node-fcwapmu"></a>

## Welcome To Course 1

<br>

<a id="node-hcbp4vv"></a>

> [!NOTE]
> 1 Introduction to NLP course
>
> 2 Topics covered: classification and vector spaces
>
> 3 Applications of NLP to sentiment analysis and word translation
>
> 4 Example problem of building a system to classify positive and negative
> product reviews
>
> 5 Week 1: \\*Representing text as a vector\\* and using\\* logistic regression\\* to
> classify sentiment
>
> 6 Week 2: Using the \\*Naive Bayes classifier\\* for sentiment classification
>
> 7 Week 3: Learning about \\*vector space models\\* and their applications in
> \\*information retrieval, indexing, relevancy ranking, and information
> filtering\\*
>
> 8 Week 4: Building a simple \\*machine translation\\* system and using
> \\*locality sensitive hashing\\* to improve \\*nearest neighbor search\\*
>
> 9 Importance of NLP concepts in search engine algorithms

<br>

<a id="node-e31gge1"></a>

## Acknowledgement - Ken Church

<br>

<a id="node-mw8fnid"></a>

<p align="center"><kbd><img src="assets/otpg8cxkw78.png" width="80%"></kbd></p>

<br>

<a id="node-qrvr0xa"></a>

## Week Introduction

<br>

<a id="node-cd9744i"></a>

> [!NOTE]
> Welcome to the first week of Course 1.
>
> This week is all about \\*logistic regression\\*, which is a very
> important tool used in many applications in NLP.
>
> Logistic regression algorithms are \\*particularly useful\\* because
> they are \\*easy to train\\* and provide you with a \\*good baseline
> result\\*.
>
> This week you'll use logistic regression for \\*sentiment analysis of
> tweets\\*.
>
> You will first \\*process your data\\*, then you \\*train your model\\* and
> finally, you will \\*test the accuracy \\*of your model.

<br>

<a id="node-2reg4s9"></a>

## Supervised Ml & Sentiment Analysis

<br>

<a id="node-3dxx882"></a>

> [!NOTE]
> 1 The \\*goal\\* of supervised machine learning is to \\*minimize error rates or cost\\*
> by \\*mapping input features X to output labels Y hat.\\*
>
> 2 \\*Logistic regression\\* is a \\*classification\\* algorithm used to assign
> observations to two distinct classes.
>
> 3 In the context of \\*sentiment analysis\\*, logistic regression can be used to
> predict whether a tweet has a positive or negative sentiment.
>
> 4 The steps for building a logistic regression classifier for sentiment analysis
> include: p\\*rocessing raw tweets to extract useful features\\*, \\*training\\* the
> \\*classifier\\* to\\* minimize the cost,\\* and \\*making predictions\\* based on the trained
> model.
>
> 5 The next video will cover how to extract features from tweets for sentiment
> analysis.

<br>

<a id="node-a1nvlkz"></a>

<p align="center"><kbd><img src="assets/b4q3fgaeh45.png" width="80%"></kbd></p>

<br>

<a id="node-3ekxtd4"></a>

<p align="center"><kbd><img src="assets/2ef1etukp2e.png" width="80%"></kbd></p>

<br>

<a id="node-323x15o"></a>

<p align="center"><kbd><img src="assets/ydptkiagjda.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là: Preprocess để **extract feature** from text rồi
> bỏ vào Lo.Re model để **train** và **classify**

<br>

<a id="node-6d236qy"></a>

## Vocabulary & Feature Extraction

<br>

<a id="node-vr30phe"></a>

> [!NOTE]
> 1 Introduction: Learning to \\*represent text as a vector\\*
>
> 2 Building a vocabulary: Creating a \\*list of unique words\\*
>
> 3 Extracting features: Assigning values to features in a tweet
> based on the vocabulary
>
> 4 \\*Sparse\\* \\*representation\\*: Representation with a small relative
> number of non-zero values
>
> 5 Problems with large vocabularies: Model training takes
> \\*excessive time\\*
>
> 6 Conclusion: Recap of representing text as a vector and
> introduction to identifying problems with large vocabularies in
> the next video.

<br>

<a id="node-f0ums49"></a>

<p align="center"><kbd><img src="assets/ckn93xy2jdi.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tạo bộ dictionary/ list các unique words

<br>

<a id="node-f1yujk5"></a>

<p align="center"><kbd><img src="assets/u66v2ckg1gi.png" width="80%"></kbd></p>

> [!NOTE]
> Một cách để 'extract feature' - tức là tạo feature vector gọi là **sparse**
> **representation** (từ nào có trong dic thì gán 1, không có thì gán 0
>
>
>
> Cách xây dựng vector kiểu này khiến số 0 nhiều nên gọi là "sparse"
> tạm dịch là "trống trải" / "thưa thớt"

<br>

<a id="node-062007w"></a>

<p align="center"><kbd><img src="assets/mjoe5svo3cc.png" width="80%"></kbd></p>

> [!NOTE]
> Vấn đề đ.v làm kiểu này là số params phải learn là rất lớn - độ
> dài của feature vector = V và V thường rất lớn do bộ vocab
> size lớn

<br>

<a id="node-xyqkl09"></a>

<p align="center"><kbd><img src="assets/eqmn31p5en.png" width="80%"></kbd></p>

<br>

<a id="node-5f35nzi"></a>

<p align="center"><kbd><img src="assets/t8zmvlesylj.png" width="80%"></kbd></p>

> [!NOTE]
> 13 từ - the0-theta13 = 14

<br>

<a id="node-le2ln7x"></a>

## Negative & Positive Frequencies

<br>

<a id="node-xqx6q1t"></a>

<p align="center"><kbd><img src="assets/cqrvjm4g4mv.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái cách feature extraction này, đối với từng từ trong
> vocabulary list, ta đếm số lần nó xuất hiện trong positive và
> negative câu

<br>

<a id="node-atdqq9t"></a>

<p align="center"><kbd><img src="assets/2rpo4836doe.png" width="80%"></kbd></p>

> [!NOTE]
> Các câu trong corpus dc gắn label
> positive / negative

<br>

<a id="node-jrna3vb"></a>

<p align="center"><kbd><img src="assets/vp5qpmnq4fr.png" width="80%"></kbd></p>

> [!NOTE]
> Thì happy xuất hiện 2 lần trong các
> câu positive -> posFreq = 2

<br>

<a id="node-jq32uaq"></a>

<p align="center"><kbd><img src="assets/9o312zjymhl.png" width="80%"></kbd></p>

> [!NOTE]
> "sad" xuất hiện 2 lần trong
> negative câu -> negFreq = 2

<br>

<a id="node-vr0a5rq"></a>

<p align="center"><kbd><img src="assets/vy3up8qcuur.png" width="80%"></kbd></p>

<br>

<a id="node-mi2snkz"></a>

## Feature Extraction With Frequencies

<br>

<a id="node-0yhglpl"></a>

<p align="center"><kbd><img src="assets/9b5kkqmya1b.png" width="80%"></kbd></p>

<br>

<a id="node-5238h9a"></a>

<p align="center"><kbd><img src="assets/tigkn797vmm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là encode feature theo 3 dimension thay
> vì V dimension như cách làm trước

<br>

<a id="node-dy7km75"></a>

<p align="center"><kbd><img src="assets/dt56cduobr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tổng các PosFreq của
> các từ trong câu này là 8

<br>

<a id="node-og6ly07"></a>

<p align="center"><kbd><img src="assets/n9heeua835.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tổng các NegFreq của
> các từ trong câu này là 11

<br>

<a id="node-6hlfhy7"></a>

<p align="center"><kbd><img src="assets/rgp143iwwy.png" width="80%"></kbd></p>

> [!NOTE]
> Nên feature representation (encode) của câu này là [1,8,11]

<br>

<a id="node-7mm1pip"></a>

## Preprocessing

<br>

<a id="node-uldeupf"></a>

<p align="center"><kbd><img src="assets/o7umrwtz2x.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái preprocess đầu tiên là bỏ đi 'stop word' vốn
> không thay đổi lắm thông tin

<br>

<a id="node-4y3azjg"></a>

<p align="center"><kbd><img src="assets/iq2g7eh19k.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó là punctuation tuy nhiên
>
>
>
> Đôi khi phải cân nhắc giữ lại punctuation nếu
> nó thể hiện thông tin cần thiết cho nlp task cụ thể đang làm

**🔗 See also:** [linked note](./c1w2_naive_bayes.md#node-bhe9qvd)

<br>

<a id="node-zyuursj"></a>

<p align="center"><kbd><img src="assets/m7arby1wbqg.png" width="80%"></kbd></p>

> [!NOTE]
> Bỏ luôn handles và URLS, còn lại câu này mang ý nghĩa positive, thì
> một ML model tốt sẽ detect dc là positive

<br>

<a id="node-j6ldzhc"></a>

<p align="center"><kbd><img src="assets/ajosyw50a57.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng là 'Stemming' - bỏ đi mấy cái hậu tố (suffix) chỉ giữ
> lại cái từ gốc và giúp giảm bớt vocab list
>
>
>
> Và lowercase hết

<br>

<a id="node-8w6y0f3"></a>

<p align="center"><kbd><img src="assets/5tcx1sxnoit.png" width="80%"></kbd></p>

> [!NOTE]
> Kết quả sau khi
> preprocessed

<br>

<a id="node-l59qeki"></a>

## Preprocessing Reading

<br>

<a id="node-gi2j89e"></a>

> [!NOTE]
> When preprocessing, you have to perform the following:
>
> 1 Eliminate handles and URLs
>
> 2 Tokenize the string into words.
>
> 3 Remove stop words like "and, is, a, on, etc."
>
> 4 Stemming- or convert every word to its stem. Like dancer, dancing, danced,
> becomes 'danc'. You can use porter stemmer to take care of this.
>
> 5 Convert all your words to lower case.
>
> For example the following tweet "@YMourri and @AndrewYNg are tuning a GREAT AI
> model at https://deeplearning.ai!!!" after preprocessing becomes
>
> [\\/tun\\/,\\/great\\/,\\/ai\\/,\\/model\\/]. Hence you can see how we eliminated handles,
> tokenized it into words, removed stop words, performed stemming, and converted
> everything to lower case.

<br>

<a id="node-1h66j70"></a>

## Lab: Nl Preprocessing

<br>

<a id="node-cfwlg7q"></a>

> [!NOTE]
> In this lab, we will be exploring how to preprocess tweets for
> sentiment analysis. We will \\*provide a function for
> preprocessing tweets\\* during this week's assignment, but it is
> \\*still good to know what is going on\\* under the hood.
>
> By the end of this lecture, you will see \\*how to use the NLTK
> package to perform a preprocessing\\* pipeline for Twitter
> datasets.

<br>

<a id="node-dk3x23r"></a>

> [!NOTE]
> Setup
>
> Đại khái là sẽ dùng thư viện Python NLTK dùng để
> natural language preprocessing, có các modules để
> collect, handling và processing Twitter data

<br>

<a id="node-3x8fiyg"></a>

<p align="center"><kbd><img src="assets/rmy015kzqa.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là sẽ dùng thư viện Python NLTK dùng để natural
> language preprocessing, có các modules để collect,
> handling và processing Twitter data

<br>

<a id="node-lqkgg5s"></a>

#### About the Twitter dataset

<br>

<a id="node-1dfvdtp"></a>

<p align="center"><kbd><img src="assets/f53uhehsg16.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là 5000 positive 5000 negative, chia đều vậy là để
> tạo một dataset cân bằng chứ nhớ là nó không phản ánh
> distribution trong thực tế (dĩ nhiên)
>
>
>
> Đại khái là có 2 list, mỗi entry là string

<br>

<a id="node-oqqunun"></a>

<p align="center"><kbd><img src="assets/eyxm8it7h88.png" width="80%"></kbd></p>

<br>

<a id="node-77ece9n"></a>

#### Looking at raw texts

<br>

<a id="node-opugcpz"></a>

<p align="center"><kbd><img src="assets/g7xp76rs4zt.png" width="80%"></kbd></p>

> [!NOTE]
> Xem để có cái hiểu data chiếm 80% thành công của một data science
> project. Đại khái nhận thấy tweet hay chứa url và emoticon ví dụ :)

<br>

<a id="node-ln8b03x"></a>

> [!NOTE]
> Preprocess raw text for
> Sentiment analysis

<br>

<a id="node-qsp6ebb"></a>

<p align="center"><kbd><img src="assets/72ixdmq6f4x.png" width="80%"></kbd></p>

> [!NOTE]
> Chọn một câu mà ta thấy complex. Download một số tool
> preprocessing từ NLTK để làm

<br>

<a id="node-8c4nsij"></a>

> [!NOTE]
> Remove hyperlinks,
> Twitter marks and styles

<br>

<a id="node-tzjeboi"></a>

<p align="center"><kbd><img src="assets/uyszvi6ju.png" width="80%"></kbd></p>

<br>

<a id="node-u0yyqo8"></a>

##### Tokenize the string

<br>

<a id="node-hcjxlyz"></a>

<p align="center"><kbd><img src="assets/fl0snfz84do.png" width="80%"></kbd></p>

<br>

<a id="node-fsbeovz"></a>

> [!NOTE]
> Remove stop words
> and punctuations

<br>

<a id="node-f3ey0e9"></a>

<p align="center"><kbd><img src="assets/q4fmjfmujnb.png" width="80%"></kbd></p>

> [!NOTE]
> Xem những stop word và punctuation có gì

<br>

<a id="node-b9f2co1"></a>

<p align="center"><kbd><img src="assets/qva39aetk0h.png" width="80%"></kbd></p>

> [!NOTE]
> Một số trường hợp stop word cần phải được customize
> lại vì mang thông tin quan trọng, còn ở đây ổng bỏ hết,
> emoticon cũng vậy

<br>

<a id="node-38j2gf7"></a>

##### Stemming

<br>

<a id="node-1ba55cd"></a>

<p align="center"><kbd><img src="assets/hpr7zpkmtkv.png" width="80%"></kbd></p>

> [!NOTE]
> Stemming như trong bài giảng đã hiểu là convert về cái từ gốc mà nếu add
> mấy cái suffix râu ria sẽ ra nhiều từ khác nhau như ed, ing thì stemming sẽ
> **giúp giảm vocab size rất nhiều**, mà vẫn **giữ phần lớn ý nghĩa của từ vựng**
>
>
>
> Có nhiều module để **stemming** nhưng ở đây ổng chọn **Porter**

<br>

<a id="node-ccu38lp"></a>

<p align="center"><kbd><img src="assets/fvg2lffy2b.png" width="80%"></kbd></p>

<br>

<a id="node-i6h7ch5"></a>

##### process_tweet()

<br>

<a id="node-421sbkd"></a>

<p align="center"><kbd><img src="assets/ur3krj2uwh.png" width="80%"></kbd></p>

> [!NOTE]
> Đai khái là mấy step trên sẽ làm sẵn trong funciton **process_tweet**()
> **khi làm assignment chỉ việc gọi function** này thôi nhưng **quan trọng là
> đã hiểu nó làm cái gì**

<br>

<a id="node-zajx2lx"></a>

## Putting It All Together

<br>

<a id="node-oeahp5w"></a>

<p align="center"><kbd><img src="assets/p8kk594gxcj.png" width="80%"></kbd></p>

> [!NOTE]
> Mỗi 1 câu sẽ được represented/encoded
> bởi một 3 dimensions vector

<br>

<a id="node-3qwa1ab"></a>

<p align="center"><kbd><img src="assets/a651ufcuzo.png" width="80%"></kbd></p>

<br>

<a id="node-1vgmlc0"></a>

<p align="center"><kbd><img src="assets/fepquclh77e.png" width="80%"></kbd></p>

> [!NOTE]
> Và làm vậy với 1 một bộ m
> câu, ta được 1 matrix

<br>

<a id="node-prdfjw1"></a>

<p align="center"><kbd><img src="assets/k916f7ht2fj.png" width="80%"></kbd></p>

> [!NOTE]
> - Bước build_freqs:
>
>
>
> Với tất cả các tweets và label tương ứng (positive hay negative), nó tạo
> 1 bộ vocab và tương ưng mỗi vocab là chỉ số positive và negative
> frequency ví dụ ' happy' pos = 200, neg = 50 tức là nó xuất hiện 200 lần
> trong các câu có label positive và 50 lần trong các câu gắn label
> negative
>
>
>
> Ini matrix X  = shape (m,3) tức là có m row, 3 columns
>
>
>
> - Bước process_tweet như đã xem ở lab trước nó sẽ xử lý các bước
> như loại bỏ stop word, punctuation, stemming,,
>
>
>
> - Bước extract_features sẽ là cái mình sẽ làm trong programming
> assignment : Dựa vào frequency dictionary, mình sẽ tạo representative
> vector cho mỗi tweet đã được preprocessed.
>
>
>
> Thì đại khái là tính tổng positive count và negative của các từ trong câu

<br>

<a id="node-bks9p5j"></a>

## Visualization Word Frequencies

<br>

<a id="node-10wp2l6"></a>

> [!NOTE]
> Building and Visualizing word frequencies
>
> In this lab, we will focus on the \\*build_freqs\\*() helper
> function and visualizing a dataset fed into it. In our goal of
> tweet sentiment analysis, this function will \\*build a
> dictionary where we can lookup how many times a word
> appears in the lists of positive or negative\\* tweets. This
> will be very helpful when extracting the features of the
> dataset in the week's programming assignment. Let's see
> how this function is implemented under the hood in this
> notebook.

<br>

<a id="node-erd9596"></a>

#### Setup

<br>

<a id="node-u9fnnvr"></a>

<p align="center"><kbd><img src="assets/veagklkazf.png" width="80%"></kbd></p>

<br>

<a id="node-l1pek6x"></a>

#### Load the NLTK sample dataset

<br>

<a id="node-sbowjb4"></a>

<p align="center"><kbd><img src="assets/gpwmuluwglm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ổng load bộ twitter dataset from NLTK, rồi lấy ra các
> positive tweets và negative tweets rồi concat lại thì 5000 câu đầu
> là positive, 5000 câu sau là negative. Xong tạo 2 array 5000 số 1
> và 5000 số 0 rồi concat lại để thành cái vector label

<br>

<a id="node-7hqlskj"></a>

#### Dictionaries

<br>

<a id="node-izjdwdp"></a>

<p align="center"><kbd><img src="assets/575jlbwl2sa.png" width="80%"></kbd></p>

<br>

<a id="node-v0cxmvx"></a>

<p align="center"><kbd><img src="assets/esc3r1mw59p.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là một số tính chất của Python dictionary có thể
> get() để có default value nếu ko có key trong dic còn
> dùng [] thì ko có nó báo lỗi.

<br>

<a id="node-2skc6rg"></a>

#### Word frequency dictionary

<br>

<a id="node-br987le"></a>

<p align="center"><kbd><img src="assets/vhx6bbp3ve.png" width="80%"></kbd></p>

> [!NOTE]
> Cũng dễ hiểu chỉ lưu ý chỗ này là có cái vụ 2 element key, tức là ví dụ
> (word, y) là key freqs[('happy',1)] = 10 tức là từ 'happy', cột positive thì
> bằng 10.

<br>

<a id="node-7nb4nai"></a>

<p align="center"><kbd><img src="assets/ytmmah5ayle.png" width="80%"></kbd></p>

<br>

<a id="node-raj87ze"></a>

<p align="center"><kbd><img src="assets/3dgg2pme8wy.png" width="80%"></kbd></p>

<br>

<a id="node-yoslirc"></a>

#### Table of word counts

<br>

<a id="node-c0ogvrc"></a>

<p align="center"><kbd><img src="assets/fqirq78iyc.png" width="80%"></kbd></p>

<br>

<a id="node-95l5pht"></a>

<p align="center"><kbd><img src="assets/4ua6ysnk74v.png" width="80%"></kbd></p>

<br>

<a id="node-bgweyc9"></a>

<p align="center"><kbd><img src="assets/jvpiqv8bnkh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:
>
>
>
> Plot một số từ theo 2 thông số log của positive count và log
> của negative count
>
>
>
> Cho ta cái nhìn trực quan (visualizing) về 'mức độ' positive
> và  negative của chúng  ('/scatter plot to inspect this table
> visually')
>
>
>
> /Và dùng hàm log '/take into account the wide discrepancies
> between the raw counts' /hiểu đại khái là để cho giảm bớt
> sự quá chênh lệch giữa các giá trị pos và neg sẽ khiến plot
> bị stretch

<br>

<a id="node-qjakgdc"></a>

## Logistic Regression Overview

<br>

<a id="node-gdn1nih"></a>

<p align="center"><kbd><img src="assets/nskkdh779v.png" width="80%"></kbd></p>

<br>

<a id="node-lc9mgcs"></a>

<p align="center"><kbd><img src="assets/jgkvcy2ulmb.png" width="80%"></kbd></p>

<br>

<a id="node-grvj6cz"></a>

<p align="center"><kbd><img src="assets/jwqo0b049c.png" width="80%"></kbd></p>

> [!NOTE]
> Có vector representation x, nhân với theta transpose rồi
> bỏ vào sigmoid tính ra probability x là positive bằng bao
> nhiêu đem so với threshold = 0.5

<br>

<a id="node-5kqwozq"></a>

## Lo.re Training

<br>

<a id="node-kf898lx"></a>

<p align="center"><kbd><img src="assets/0rtzmxvwzbs.png" width="80%"></kbd></p>

<br>

<a id="node-972cg0n"></a>

<p align="center"><kbd><img src="assets/onahyymq3w.png" width="80%"></kbd></p>

> [!NOTE]
> Gradient descent

<br>

<a id="node-ifllfc4"></a>

## Lab: Visualizing Tweets And Lo.re Models

<br>

<a id="node-lzk88yw"></a>

> [!NOTE]
> \\*Objectives:\\* Visualize and interpret the logistic
> regression model
>
> \\*Steps: \\*  • Plot tweets in a scatter plot using their
> positive and negative sums.
>
> • Plot the output of the logistic regression model in the
> same plot as a solid line

<br>

<a id="node-pdpej5l"></a>

#### Import the required libraries

<br>

<a id="node-3f0e6tv"></a>

<p align="center"><kbd><img src="assets/qtwwp4yq5gg.png" width="80%"></kbd></p>

<br>

<a id="node-49vgjtz"></a>

#### Load the NLTK sample dataset

<br>

<a id="node-syjuv93"></a>

<p align="center"><kbd><img src="assets/it2bwg7y0t.png" width="80%"></kbd></p>

<br>

<a id="node-c2arpq3"></a>

#### Load the extracted features

<br>

<a id="node-qbhc327"></a>

<p align="center"><kbd><img src="assets/abk1zp7f3km.png" width="80%"></kbd></p>

> [!NOTE]
> Ý là do cuối tuần sẽ làm function extract feature này nên để khỏi ' lộ đáp án' ổng
> load sẵn các prep vector từ CSV file

<br>

<a id="node-txw8eyy"></a>

<p align="center"><kbd><img src="assets/sk77dbo256.png" width="80%"></kbd></p>

<br>

<a id="node-pxda44n"></a>

#### Load a pretrained Logistic Regression model

<br>

<a id="node-9iv99gi"></a>

> [!NOTE]
> In the same way, as part of this week's assignment, a
> Logistic regression model must be trained. The next cell
> contains the resulting model from such training. Notice that a
> list of 3 numeric values represents the whole model, that we
> have called theta  𝜃
>
> theta = [6.03518871e-08, 5.38184972e-04, -5.58300168e-04]

<br>

<a id="node-oxjjc0f"></a>

> [!NOTE]
> Plot the samples in
> a scatter plot

<br>

<a id="node-res3pot"></a>

<p align="center"><kbd><img src="assets/qttsmb8gid.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là plot các data instance ra dù là 3D đáng lẽ phải vẽ trong
> không gian 3 chiều thì ổng nói khi đó 3 giá trị của theta (đã trained) sẽ
> cho ra 1 plane phân tách các instance thành 2 class, nhưng ở đây do
> cái feature đầu là bias đều bằng 1 nên vẽ mỗi instance bằng 2 feature
> sau lên Cartesian (2D)

<br>

<a id="node-8h5lofw"></a>

<p align="center"><kbd><img src="assets/kjtirigxsn.png" width="80%"></kbd></p>

<br>

<a id="node-0y4vkyr"></a>

> [!NOTE]
> Plot the model
> alongside the data

<br>

<a id="node-o3mvzlk"></a>

<p align="center"><kbd><img src="assets/ty561swi5ys.png" width="80%"></kbd></p>

> [!NOTE]
> Nói chung là nhừ theta vẽ ra cái đường phân chia (Decision Boundary?) rồi 2 cái
> arrow vuông góc với nó. Chưa hiểu cụ thể lắm nhưng chắc cũng ko quan trọng.

<br>

<a id="node-865spno"></a>

<p align="center"><kbd><img src="assets/1c94u8wc6gd.png" width="80%"></kbd></p>

<br>

<a id="node-ak1ldrp"></a>

<p align="center"><kbd><img src="assets/cd0e3rabtli.png" width="80%"></kbd></p>

<br>

<a id="node-gmmh8gi"></a>

## Log.re: Testing

<br>

<a id="node-05q9nhu"></a>

> [!NOTE]
> 1 Using data to predict new data points
>
> 2 Analyzing model generalization
>
> 3 Computing accuracy of a model
>
> 4 Process of computing sigmoid function for X_val with parameters
> Theta
>
> 5 Evaluating whether each value of h of Theta is greater than or
> equal to a threshold value
>
> 6 Building a predictions vector with zeros and ones
>
> 7 Computing accuracy by comparing predictions with true values
>
> 8 Dividing number of correct predictions by the total number of
> observations to estimate model's performance on unseen data
>
> 9 Summary of concepts learned in the first week of specialization
>
> 10 Implementation of concepts in programming exercise

<br>

<a id="node-hn99arc"></a>

<p align="center"><kbd><img src="assets/wrjtasz23qo.png" width="80%"></kbd></p>

<br>

<a id="node-4o509u8"></a>

<p align="center"><kbd><img src="assets/8hitk17mfgm.png" width="80%"></kbd></p>

<br>

<a id="node-9vr5duz"></a>

<p align="center"><kbd><img src="assets/rib4zkr0vm.png" width="80%"></kbd></p>

<br>

<a id="node-n59yoef"></a>

<p align="center"><kbd><img src="assets/peyul5nany8.png" width="80%"></kbd></p>

<br>

<a id="node-c8e9w9y"></a>

<p align="center"><kbd><img src="assets/gu4thg3p5nn.png" width="80%"></kbd></p>

<br>

<a id="node-xlcyh6a"></a>

## Lo.re Cost Function

<br>

<a id="node-xsu811s"></a>

> [!NOTE]
> 1 Introduction to logistic regression cost function and its
> intuition
>
> 2 Components of the logistic regression cost function
> equation
>
> 3 Explanation of the two terms in the cost function equation
> and their relevance to label values of 0 and 1
>
> 4 Visualization of the cost function for label values of 0 and 1
>
> 5 Understanding the impact of prediction accuracy on overall
> cost
>
> 6 Mention of Naive Bayes as a different classification
> algorithm for predicting sentiment in tweets

<br>

<a id="node-5h7q7c7"></a>

<p align="center"><kbd><img src="assets/jqxbk7em94.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/q1sbhkzseq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/mk1we4rb5xe.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4s9vc0mrxk4.png" width="80%"></kbd></p>

> [!NOTE]
> Trung bình cộng của loss cho từng data sample
>
>
>
> Và vì loss này tính bởi hàm log nên luôn âm nên thêm dấu trừ ở phía trước để
> chuyển cost function thành dương

<br>

<a id="node-z6btlf5"></a>

<p align="center"><kbd><img src="assets/xnh7lf7bgtc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6g6ihhs6thm.png" width="80%"></kbd></p>

> [!NOTE]
> Ôn lại thôi chứ biết rồi, 2 vế kiểu như sẽ phụ trách cho 2
> trường hợp y = 1 hay = 0. 
> Nếu y = 1 (thì vế 2 = 0, bỏ): 
> Nếu y^ cũng càng gần 1 thì log của (y^) sẽ càng gần bằng 0
> -> Loss gần 0. 
> Nếu y^ càng gần 0, log (0) sẽ về vô cùng -> Loss về vô cùng

<br>

<a id="node-97riuif"></a>

<p align="center"><kbd><img src="assets/aotwg66lp1l.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/t8leh1fxeqe.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự khi y = 0

<br>

<a id="node-yqneb27"></a>

## Optional Logistic Regression: Cost Function

<br>

<a id="node-72mbzkw"></a>

> [!NOTE]
> 1. Đại khái xây dựng function P(y(i)) cho 1 instance như này sẽ đảm bảo
> nếu tối đa được P sẽ cho ra predict chính xác
>
> 2. Xây dựng objective như này (tối đa tích của các P(i)) - PI sẽ  đảm bảo
> muốn PI lớn thì tất cả (P(y(i)) phải lớn = phải 'ráng' mà predict đúng cho mọi
> instance mới được.
>
> 3. Và để cho PI lớn nhất thì cũng tương đương làm log(PI) của nó lớn  nhất
>
> 4. Và dựa vào phép tính lôgarit, có thể chuyển nó thành dạng tổng log
>
> 5. Và Làm nó nó lớn nhất cũng chính là làm cho (Trừ của nó) nhỏ nhất ->
> Hoá ra hàm J
>
> Hiểu được cái này rồi, rất hay

<br>

<a id="node-8v7ir1p"></a>

<p align="center"><kbd><img src="assets/2k8cgplv13.png" width="80%"></kbd></p>

<br>

<a id="node-1mae11e"></a>

<p align="center"><kbd><img src="assets/zqy5v7y4mgf.png" width="80%"></kbd></p>

<br>

<a id="node-3698pv3"></a>

<p align="center"><kbd><img src="assets/p1e1oydq13h.png" width="80%"></kbd></p>

<br>

<a id="node-xf50ymp"></a>

<p align="center"><kbd><img src="assets/s3tp8uqhobn.png" width="80%"></kbd></p>

<br>

<a id="node-hutbl41"></a>

## Week Conclusion

<br>

<a id="node-2pn5b6t"></a>

## Lo.re: Gradient

<br>

<a id="node-audrsau"></a>

<p align="center"><kbd><img src="assets/vo4duhz73gd.png" width="80%"></kbd></p>

<br>

<a id="node-586zclf"></a>

<p align="center"><kbd><img src="assets/0ovpfgkfdkel.png" width="80%"></kbd></p>

<br>

<a id="node-hf6lou9"></a>

<p align="center"><kbd><img src="assets/juaf45cs1bi.png" width="80%"></kbd></p>

<br>

<a id="node-13tpi61"></a>

<p align="center"><kbd><img src="assets/qmo8bu9914h.png" width="80%"></kbd></p>

<br>

<a id="node-55s2ke2"></a>

<p align="center"><kbd><img src="assets/xlpdyodvdon.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zc5nhua6uo8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/d1exywf9kf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/krwhkqaz8a.png" width="80%"></kbd></p>

> [!NOTE]
> Tự triển khai

<br>

<a id="node-vn0vgwk"></a>

## Quiz: Log.re

<br>

<a id="node-pixrd6m"></a>

## Programming Assignment: Log.re

<br>

<a id="node-pfhsgy2"></a>

> [!NOTE]
> Welcome to week one of this specialization. You will learn about
> logistic regression. Concretely, you will be implementing logistic
> regression for sentiment analysis on tweets. Given a tweet, you
> will decide if it has a positive sentiment or a negative one.
> Specifically you will:
>
> • Learn how to \\/extract features\\/ for logistic regression given
> some text
>
> • Implement \\/\\*logistic regression from scratch\\*\\/
>
> • Apply logistic regression on a \\/\\*natural language processing
> task\\*\\/
>
> • \\/\\*Test\\*\\/ using your logistic regression
>
> • Perform \\/\\*error analysis\\*\\/

<br>

<a id="node-rljbwtx"></a>

#### Import Functions and Data

<br>

<a id="node-e8wkrgp"></a>

<p align="center"><kbd><img src="assets/c1io60rkezl.png" width="80%"></kbd></p>

<br>

<a id="node-a7u2guc"></a>

<p align="center"><kbd><img src="assets/cewl5zhdqbb.png" width="80%"></kbd></p>

<br>

<a id="node-kvgh1sb"></a>

<p align="center"><kbd><img src="assets/2090ha3e7h.png" width="80%"></kbd></p>

<br>

<a id="node-7hxssa6"></a>

<p align="center"><kbd><img src="assets/cww99wx88zg.png" width="80%"></kbd></p>

<br>

<a id="node-fgepawx"></a>

<p align="center"><kbd><img src="assets/wm6j82n72cc.png" width="80%"></kbd></p>

<br>

<a id="node-9b6r08z"></a>

#### 1 - Logistic Regression

<br>

<a id="node-wi9kmig"></a>

##### 1.1 - Sigmoid

<br>

<a id="node-th7mu49"></a>

<p align="center"><kbd><img src="assets/ja6q5cx7yo.png" width="80%"></kbd></p>

<br>

<a id="node-zfl5kqj"></a>

##### Exercise 1 - sigmoid (UNQ_C1)

<br>

<a id="node-2ar75wi"></a>

<p align="center"><kbd><img src="assets/wq5x85dd6p.png" width="80%"></kbd></p>

<br>

<a id="node-vzif657"></a>

<p align="center"><kbd><img src="assets/vysjvhnef8.png" width="80%"></kbd></p>

<br>

<a id="node-taxu0yf"></a>

##### 1.2 - Cost function and Gradient

<br>

<a id="node-t8214q0"></a>

<p align="center"><kbd><img src="assets/bd26nojxad.png" width="80%"></kbd></p>

<br>

<a id="node-x6si8rm"></a>

<p align="center"><kbd><img src="assets/cy708skd01e.png" width="80%"></kbd></p>

<br>

<a id="node-l7y6087"></a>

##### Exercise 2 - gradientDescent (UNQ_C2)

<br>

<a id="node-ks70wqw"></a>

<p align="center"><kbd><img src="assets/12mynx9a0yba.png" width="80%"></kbd></p>

<br>

<a id="node-csibo9n"></a>

<p align="center"><kbd><img src="assets/nfowqlrgnc.png" width="80%"></kbd></p>

<br>

<a id="node-2eyr07s"></a>

<p align="center"><kbd><img src="assets/p23t9jf86sn.png" width="80%"></kbd></p>

<br>

<a id="node-64e8e71"></a>

#### 2 - Extracting the Features

<br>

<a id="node-j9aofiq"></a>

##### Exercise 3 - extract_features (UNQ_C3)

<br>

<a id="node-b51a5qf"></a>

<p align="center"><kbd><img src="assets/uao5xiwdh2j.png" width="80%"></kbd></p>

<br>

<a id="node-swur7fi"></a>

<p align="center"><kbd><img src="assets/3d81cgnidzp.png" width="80%"></kbd></p>

> [!NOTE]
> Phải dùng get để còn handle case nếu
> word ko có trong dictionary

<br>

<a id="node-8ltzync"></a>

<p align="center"><kbd><img src="assets/xlgn9mgq6gp.png" width="80%"></kbd></p>

<br>

<a id="node-npdbtej"></a>

#### 3 - Training Your Model

<br>

<a id="node-r6x548l"></a>

<p align="center"><kbd><img src="assets/a2xpf41tsco.png" width="80%"></kbd></p>

<br>

<a id="node-ihzzx85"></a>

#### 4 - Test your Logistic Regression

<br>

<a id="node-r20d1j0"></a>

##### Exercise 4 - predict_tweet (UNQ_C4)

<br>

<a id="node-6461kig"></a>

<p align="center"><kbd><img src="assets/qyuix4863ti.png" width="80%"></kbd></p>

<br>

<a id="node-0nf42rh"></a>

<p align="center"><kbd><img src="assets/432ygtt5vrf.png" width="80%"></kbd></p>

<br>

<a id="node-2kxaeiy"></a>

##### 4.1 - Check the Performance using the Test Set

<br>

<a id="node-q6qhar8"></a>

<p align="center"><kbd><img src="assets/eqneetcnbg7.png" width="80%"></kbd></p>

<br>

<a id="node-ctc14h7"></a>

##### Exercise 5 - test_logistic_regression (UNQ_C5)

<br>

<a id="node-id3jjfg"></a>

<p align="center"><kbd><img src="assets/h17kqw2cf36.png" width="80%"></kbd></p>

<br>

<a id="node-60641h2"></a>

#### 5 - Error Analysis

<br>

<a id="node-oevpe8q"></a>

<p align="center"><kbd><img src="assets/ithwnuab85h.png" width="80%"></kbd></p>

<br>

<a id="node-37u1aei"></a>

<p align="center"><kbd><img src="assets/rwzdynbpdk.png" width="80%"></kbd></p>

<br>

<a id="node-f6ss0st"></a>

#### 6 - Predict with your own Tweet

<br>

<a id="node-h94aem7"></a>

<p align="center"><kbd><img src="assets/exqv6ad6mbo.png" width="80%"></kbd></p>

<br>

<a id="node-b2ta214"></a>

## Andrew Ng & Chris Manning

<br>

