# C5w2_natural Language Processing & Word Embeddings

📊 **Progress:** `59` Notes | `103` Screenshots

---
<a id="node-86gxnev"></a>

## C5w2_natural Language Processing & Word Embeddings

<br>

<a id="node-c4vdx6g"></a>

## Introduction To Word Embeddings

<br>

<a id="node-vpbt7j9"></a>

### Word Representation

<br>

<a id="node-v8wtdnt"></a>

> [!NOTE]
> 1 Last week's topics: RNNs, GRUs, and LSTMs.
>
> 2 NLP is being revolutionized by deep learning.
>
> 3 Word embeddings are a way of representing words.
>
> 4 The weakness of one-hot representation is that it treats each word as a
> separate entity and doesn't allow for generalization across words.
>
> 5 Featurized representations could allow for better generalization and
> recognition of relationships between words.
>
> 6 Features can include gender, royalty, age, whether it is food, size, cost,
> etc.
>
> 7 A 300-dimensional vector can represent a word in a featurized
> representation.
>
> 8 Apple and orange would have similar representations in a featurized
> representation.

<br>

<a id="node-ijne1gf"></a>

<p align="center"><kbd><img src="assets/7pl7kcxnaye.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cách define one-hot vector **(one-hot representation)** cho
> các từ không giúp nắm bắt được thực tế có những từ liên quan gần
> nhau như  'Apple' và "Orange', 'King' và ' Queen'
>
>
>
> Kiểu như dot(a,b) nào cũng = 0
>
>
>
> Nên ngay cả khi thuật toán học được câu trả lời là 'I want a glass of
> orange juice' thì khi làm câu tương tự với 'apple' nó cũng phải  học lại từ
> đầu.

<br>

<a id="node-aix3gfe"></a>

<p align="center"><kbd><img src="assets/pnzagd0a00p.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu ta có thể tạo feature vector kiểu như này cho các  từ
> thì ta có thể nắm bắt được từ nào là gần nhau, từ nào là food, từ nào
> là đàn ông, đàn bà ....Tức là khai thác được nhiều hơn  đặc tính của
> từng từ. Gọi là (**featurized representation**)
>
>
>
> Thực tế thì word vector được define phức tạp hơn như đại khái là vậy,

<br>

<a id="node-d78wxvx"></a>

<p align="center"><kbd><img src="assets/kb2adp3gfg.png" width="80%"></kbd></p>

> [!NOTE]
> Khái niệm 'Embedded' - Đại khái là việc xây dựng các vector cho 
> các word như slide trước đã nói, từ đó hình dung trong không
> cian 300 chiều (giả sử vector có 300 features), các từ sẽ group
> lại thành nhóm do tương quan giống nhau giữa chúng.
>
>
>
> Và t-SNE là phương pháp để plot cái đó thành 2D để xem được

<br>

<a id="node-z2pxfux"></a>

### Using Word Embeddings

<br>

<a id="node-wdfi78p"></a>

> [!NOTE]
> Tiếp đại khái ý nói là cái word embedding này có thể được \\*'làm' bởi
> large dataset\\* với hàng tỷ từ trên internet (tự làm hay download
> pretrained word embedding) chỉ cần \\*dùng lại\\* nó trong vấn đề của
> mình (như name entity recognition vốn \\*có ít data  hơn\\* nhiều) -
> Chính là \\*'transfer learning'
>
> \\*Cuối cùng đại khái là khái niệm embedding nó rất gần với  khái niệm
> encoding trong face encoding.\\*
>
> \\*Đúng hơn là ta \\*train ra 1 cái network để làm công tác encoding\\*: là cho
> 1 cái hình vào thì encoding ra được 1 vector sao cho cùng 1 người thì 2
> vector gần nhau, khác người thì xa nhau. Và làm được vậy mới bất kì
> khuôn mặt mới nào.
>
> Còn word embedding là ta sẽ tạo cho \\*mỗi từ một fixed value vector
> mang đặc tính của từ đó\\*, và chỉ cần làm với 1 giới hạn từ vì từ lạ cứ
> cho là Unknown thôi Nói chung là hai khái niệm này rất gần nhau chỉ
> khác nhau do cách làm.

<br>

<a id="node-h837w0w"></a>

<p align="center"><kbd><img src="assets/v3pjqf9bsg.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là quay lại nói về 'name entity recognition' task, mà ta  đã xác
> định Sally Johnson là tên người, thì với việc bây giờ ta  có 'featurized
> representation' thì sẽ rất dễ cho thuật toán biết được Robert Lin cũng
> là tên người do apple farmer rất gần với orange  farmer.
>
>
>
> Tiếp đại khái ý nói là cái word embedding này có thể được **'làm' bởi
> large dataset** với hàng tỷ từ trên internet (tự làm hay download
> pretrained word embedding) chỉ cần **dùng lại** nó trong vấn đề của
> mình (như name entity recognition vốn **có ít data  hơn** nhiều) -
> Chính là **'transfer learning'**

<br>

<a id="node-d5h21l0"></a>

<p align="center"><kbd><img src="assets/mw0x8itvfc.png" width="80%"></kbd></p>

> [!NOTE]
> Tóm lại đại khái rất đơn giản là 
> 1. Learn hoặc download pretrained cái word embedding 
> bằng large dataset trên internet
>
>
>
> 2. Dùng cái word embedding đó trong bài toán cụ thể cuả mình 
> mà có ít data hơn nhiều
>
> Thay vì dùng 10000 dimension one-hot vector
> thì giờ chỉ cần dùng 300 'dense' vector
>
>
>
> 3. Có thể tiếp tục fine-tune cái word embedding đó với data mới
> (chỉ khi dataset của mình cũng không nhỏ thì làm)
>
> Tiếp đại khái nói là Transfer Learning chỉ useful khi data A lớn
> hơn nhiều data B, nên đ/v một số task của NLP như "
> **named entity recognition**, "**text summarization",** "
> **co-reference resolution**" thì nó ok, còn đ/v "**translation
> modeling**" nơi mà ta có 1 large dataset cho nó thì không

<br>

<a id="node-p841zjb"></a>

<p align="center"><kbd><img src="assets/abk3o1wzcb9.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng đại khái là khái niệm embedding nó rất gần với  khái niệm
> encoding trong face encoding.
>
>
>
> Face encoding là nó được train bởi neural network (Siamese network
> architecture) để tạo ra **128 dimensional representation of different faces**
> rồi so sánh để xác định có phải cùng 1 người ko.
>
>
>
> Đúng hơn là ta **train ra 1 cái network để làm công tác encoding**: là cho
> 1 cái hình vào thì encoding ra được 1 vector sao cho cùng 1 người thì 2
> vector gần nhau, khác người thì xa nhau. Và làm được vậy mới bất kì
> khuôn mặt mới nào.
>
>
>
> Còn word embedding là ta sẽ tạo cho **mỗi từ một fixed value vector
> mang đặc tính của từ đó**, và chỉ cần làm với 1 giới hạn từ vì từ lạ cứ
> cho là Unknown thôi Nói chung là hai khái niệm này rất gần nhau chỉ
> khác nhau do cách làm.

<br>

<a id="node-4mud5i9"></a>

### Properties Of Word Embeddings

<br>

<a id="node-ax14bcl"></a>

> [!NOTE]
> 1 Word embeddings can help in building NLP applications.
>
> 2 Word embeddings can also help with analogy reasoning.
>
> 3 A four-dimensional vector can be used to represent words in this example.
>
> 4 The gender is the main difference between man and woman and also
> between king and queen, as represented by these vectors.
>
> 5 An algorithm can compute the difference between vectors to find a word
> that completes an analogy.
>
> 6 The algorithm can find a word w that maximizes the similarity e w
> compared to e king minus e man plus e woman.
>
> 7 Research papers report 30-75% accuracy on analogy using tasks like
> these.

<br>

<a id="node-sl4srby"></a>

<p align="center"><kbd><img src="assets/o26e0xz8x5.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nhờ Word Embedding, ta có thể giải bài toán
> 'Man to woman like King to ...' bằng cách tìm từ nào mà
> khiến eMan - eWoman gằn bằng eKing - e??? vì như thế 
> ta sẽ tìm đc queen vì chính xác 2 cặp này là về Gender

<br>

<a id="node-keufw7w"></a>

<p align="center"><kbd><img src="assets/br8pk6mm215.png" width="80%"></kbd></p>

> [!NOTE]
> Ổng nói research paper cho biết
> phương pháp này cho độ chính
> xác khá ok từ 30-75%

<br>

<a id="node-j7iuury"></a>

<p align="center"><kbd><img src="assets/sxkcekz1our.png" width="80%"></kbd></p>

> [!NOTE]
> Tên là hàm cosine vì nó chính là cosine giữa 2 vector 
>
>
>
> Có thể dùng ||u-v||**2 vốn là hàm tính sự khác nhau giữa 2
> vector, nên phải lấy '-' để chỉ sự giống nhau. Nhưng người
> ta thường dùng hàm cosine hơn.
>
>
>
> Nói chung là nếu train dc Word Embedding với large word cortex
> thì sẽ rất dễ dàng tìm được các cặp từ kiểu vậy

<br>

<a id="node-7jvuxgc"></a>

### Embedding Matrix

<br>

<a id="node-kxx55t0"></a>

> [!NOTE]
> • Formalizing the problem of learning a good word embedding
>
> • Learning an embedding matrix when implementing a word embedding
> algorithm
>
> • The embedding matrix is a 300-dimensional by 10,000-dimensional
> matrix for a 10,000-word vocabulary
>
> • The columns of the matrix represent embeddings for the words in the
> vocabulary
>
> • A one-hot vector is used to represent each word in the vocabulary
>
> • The product of the embedding matrix and a one-hot vector selects the
> corresponding embedding for the word
>
> • The notation "E 6257" represents the embedding vector for the word "
> Orange"

<br>

<a id="node-w2fvug8"></a>

<p align="center"><kbd><img src="assets/8h82mt2272k.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tính (lấy ra) vector e6257 (embedding của từ)
> bằng cách mấy matrix E (Embedding matrix) nhân với
> one-hot vector o6256
>
>
>
> Sao không lấy ra bằng E[6257] ta -> Computational Expensive

<br>

<a id="node-cuxrs1p"></a>

## Learning Word Embeddings: Word2vec & Glove

<br>

<a id="node-dtysr7q"></a>

### Learning Word Embeddings

<br>

<a id="node-kfm3wfd"></a>

> [!NOTE]
> 1 In this video, you'll learn some concrete algorithms for learning word embeddings,
> which are used in natural language processing.
>
> 2 Historically, researchers used relatively complex algorithms to learn word
> embeddings. However, over time, they discovered that simpler algorithms could also
> provide good results, especially for large datasets.
>
> 3 Some of the most popular algorithms today are so simple that they might seem
> almost magical. Therefore, the video will start by introducing slightly more complex
> algorithms, which can help develop intuition about why they work.
>
> 4 \\*One way to learn a set of embeddings\\* is by \\*building a neural language
> model\\*, which \\*predicts the next word in a sequence given the previous words\\*.
>
> 5 To build a neural network for this task, you can start by taking a list of words and
> constructing a one-hot vector for each word.
>
> 6 Next, you can multiply each one-hot vector by a matrix of parameters E to obtain
> an embedding vector for each word. This step means that each embedding vector is
> obtained by taking the dot product of the corresponding one-hot vector and the
> matrix E.
>
> 7 Once you have the embedding vectors for all the words, you can fill them into a
> neural network layer. This layer feeds into a softmax, which classifies among the 10,
> 000 possible outputs in the vocabulary for the final word we're trying to predict.
>
> 8 The neural network layer and softmax each have their own parameters, which are
> optimized during training using gradient descent.
>
> 9 To handle long sentences, you can use a fixed historical window, such as the
> previous four words, as input to the neural network.
>
> 10 The parameters of the model include the matrix E and the weights of the neural
> network layer and softmax. The same matrix E is used for all the words.
>
> 11 By repeatedly predicting the next word given a historical window, the algorithm
> learns to produce good word embeddings. Specifically, the algorithm learns to
> produce similar embeddings for words that appear in similar contexts, which allows
> it to better fit the training set.
>
> 12 Overall, this algorithm provides a decent way to learn word embeddings, even
> though it might seem simplistic compared to other algorithms.

<br>

<a id="node-r4f84po"></a>

<p align="center"><kbd><img src="assets/lh8qtt1kxj.png" width="80%"></kbd></p>

> [!NOTE]
> Build a language model (đại khái là ví dụ cho câu I want a glass
> of orange ... _ -> Predict 'juice') **cũng là một cách để làm 'Word
> embedding'**
>
>
>
> Mỗi từ, như đã biết, sẽ được biến thành một one-hot vector (ví
> dụ "I" -> o4343, "want" -> o9665)
>
>
>
> Dùng Embedding Matrix E để nhân với o4343 -> e4343
> (embedding vector) embedding vector size = 300
>
>
>
> Bỏ vào N.N với đầu ra là softmax 10.000 unit **để thuật toán cố
> gắng học / huấn luyện các params sao cho output map  với
> target là từ ' juice'.**
>
>
>
> Output đại khái là vector of probability khả năng từ còn thiếu là
> từng từ trong word list nên có size 10000
>
>
>
> Params sẽ là matrix E và W[1], b[1], W[2], b[2]
>
>
>
> Có thể chỉ 'lấy 4 từ trước đó' để train thôi (input sẽ chỉ có 
> [e1 e3852..e6257] gọi là dùng **'Fixed history" -** Đây là cách để 
> handle với long-short sentences

<br>

<a id="node-jbtih5o"></a>

<p align="center"><kbd><img src="assets/ctv1cljsuk.png" width="80%"></kbd></p>

> [!NOTE]
> Ý là nếu mục đích chính là 'Word embedding' thì có thể quy định train
> từ kiểu 4 trước 4 sau, hoặc chỉ từ trước hoặc 1 từ gần đó gọi là '**Skip
> Gram**'.

<br>

<a id="node-ghftf9v"></a>

### Word2vec

<br>

<a id="node-t56olrs"></a>

> [!NOTE]
> Skip Gram model: Skip là vì nó bỏ qua một số từ để tìm cách map hai từ
> xa nhau nào đó.
>
> Như mô hình trước, từ 'context' sẽ được one-hot encoded (o_c) rồi thông
> qua matrix E để biến thành embedding vector e_c tương tự bài trước
> define một network đầu ra là softmax để tính ra y^ = probability vector
>
> Với y cũng one-hot vector. tính loss function bằng hàm cross entropy
>
> Và dùng Gradient Descent để train params của model gồm Matrix E và
> Theta (params của softmax)

<br>

<a id="node-gkh7twz"></a>

<p align="center"><kbd><img src="assets/kacr375ki5c.png" width="80%"></kbd></p>

<br>

<a id="node-swzyber"></a>

<p align="center"><kbd><img src="assets/qdsea6hlz2o.png" width="80%"></kbd></p>

> [!NOTE]
> Skip Gram model: Skip là vì nó bỏ qua một số từ để tìm cách map hai từ
> xa nhau nào đó.
>
>
>
> Như mô hình trước, từ 'context' sẽ được one-hot encoded (o_c) rồi thông
> qua matrix E để biến thành embedding vector e_c tương tự bài trước
> define một network đầu ra là softmax để tính ra y^ = probability vector
>
>
>
> Với y cũng one-hot vector. tính loss function bằng hàm cross entropy
>
>
>
> Và dùng Gradient Descent để train params của model gồm Matrix E và
> Theta (params của softmax)

<br>

<a id="node-zmmglxr"></a>

<p align="center"><kbd><img src="assets/joih4uh81uf.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Softmax nó có cái step phải tính tổng hết toàn bộ data
> training nên khi scale lên sẽ rất chậm.
>
>
>
> Còn cái nữa là nếu lấy context c một cách random thì  những từ như
> the, of, a...sẽ xuất hiện nhiều do đó người ta có một số cách để giải
> quyết chuyện này.

<br>

<a id="node-w25i3kd"></a>

### Negative Sampling

<br>

<a id="node-6pel2uv"></a>

> [!NOTE]
> Đại khái là biến nó thành 10.000 bài toán 
> binary classification với logistic regression
> bằng cách 'tạo' target y đại khái nói là cặp
> Orange-juice thì đúng (=1), các cặp khác (orange-king,...)
> thì sai (=0) - \\*số từ sai quy định bởi 'k'\\*
>
> Dựa vào cách define y như vậy, ta train 10.000 bài toán binary
> thì đại khái sẽ nhanh hơn là train bài toán softmax.

<br>

<a id="node-go34wy0"></a>

<p align="center"><kbd><img src="assets/gdxduizrphl.png" width="80%"></kbd></p>

<br>

<a id="node-ciarvm1"></a>

<p align="center"><kbd><img src="assets/u9yglr8maiq.png" width="80%"></kbd></p>

> [!NOTE]
> Skip-Gram with Softmax
>
>
>
> Đại khái là y (target) sẽ là one-hot vector có size = 10.000 số 1 ở
> index của cái từ đúng (ví dụ ở đây là từ  cần tìm ...orange __ ->
> orange juice) trong vocab list. y^ đương nhiên cũng là vector có
> size 10000 nhưng các giá trị của nó lần lượt là 'probability của các
> từ trong vocab là từ đúng.
>
>
>
> Như vậy trong quá trình training bằng G. D, tại mỗi iteration, như
> đã biết ta lần lượt forward prop đê tính y^, rồi từ y^,y -> tính loss
> bằng hàm cross entropy, rồi với loss -> back prop để tính gradient
> và update params để xong một lần iteration. Và chạy ví dụ 1000
> lần Iterations (no.epochs = 1000)
>
>
>
> Vấn để là ở chỗ tính y^, vì dùng softmax nên trong công thức nó
> phải có bước tính tổng hết 10.000 unit của softmax layer nên rất
> '**computational expensive**'
>
> Sample Negative
>
>
>
> Đại khái là biến nó thành 10.000 bài toán 
> binary classification với logistic regression
> bằng cách 'tạo' target y đại khái nói là cặp
> Orange-juice thì đúng (=1), các cặp khác (orange-king,...)
> thì sai (=0) - **số từ sai quy định bởi 'k'**
>
>
>
> Dựa vào cách define y như vậy, ta train 10.000 bài toán binary
> thì đại khái sẽ nhanh hơn là train bài toán softmax.
>
>
>
> Chưa hiểu cụ thể nó train như thế nào nhưng tạm thời biết vậy.

<br>

<a id="node-o38p8ry"></a>

<p align="center"><kbd><img src="assets/uymls55b4vm.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng là đại khái cách để chọn mấy từ sai (ngẫu nhiên kia) -
> thì đại khái là nếu chọn ngẫu nhiên thật thì lại một lần nữa ta sẽ
> gặp nhiều  từ 'the' 'a' ...nên ông gì đó đề ra cách chọn có công
> thức như vầy đại khái là sao cho hợp lý.
>
> /"Somewhere in-between Extreme of taking uniform
> distribution vs Extreme of taking whatever was the observed
> distribution" -> Chưa hiểu lắm. / Câu trên đề cập đến khái
> niệm chọn phân phối xác suất để mô tả một tập dữ liệu hoặc
> sự kiện.
>
>
>
> Ở hai đầu cực, bạn có thể giả định một phân phối đồng đều,
> trong đó tất cả các kết quả có cùng xác suất xảy ra. Ví dụ, nếu
> bạn tung một xúc xắc sáu mặt công bằng, mỗi số có xác suất
> 1/6 được tung ra.
>
>
>
> Ở cực khác, bạn có thể sử dụng phân phối quan sát được của
> dữ liệu, đại diện cho tần suất mà mỗi kết quả xảy ra. Ví dụ, nếu
> bạn có một bộ điểm kiểm tra, bạn có thể sử dụng phân phối
> quan sát của các điểm số để tính xác suất để đạt được một
> điểm số nhất định.
>
>
>
> Tuy nhiên, trong nhiều trường hợp, cả phân phối đồng đều và
> phân phối quan sát đều không phù hợp. Thay vào đó, bạn cần
> tìm một phân phối nằm ở giữa hai đầu cực này mà phù hợp
> nhất với dữ liệu. Phân phối này nên bao gồm các đặc điểm
> chính của dữ liệu, chẳng hạn như trung bình, phương sai và
> hình dạng. Quá trình này thường được thực hiện thông qua
> các phương pháp thống kê và suy luận.

<br>

<a id="node-ry8wbhl"></a>

<p align="center"><kbd><img src="assets/pfzege93bkn.png" width="80%"></kbd></p>

> [!NOTE]
> Transfer learning: Đại khái ổng nói cũng như các vấn
> để deep learning khác ta có thể download các
> **pre-trained word-vectors** để dùng.

<br>

<a id="node-8lbn1dx"></a>

### Clarifications About ...

<br>

<a id="node-p0f9vl6"></a>

<p align="center"><kbd><img src="assets/eg4bdt4zj7m.png" width="80%"></kbd></p>

<br>

<a id="node-mdu9tob"></a>

<p align="center"><kbd><img src="assets/6uxve6trh8q.png" width="80%"></kbd></p>

<br>

<a id="node-f300scm"></a>

### Glove Word Vectors

<br>

<a id="node-wgaptsd"></a>

> [!NOTE]
> 1 Introduction to the GloVe algorithm for computing word
> embeddings
>
> 2 Explanation of the X_ij count and its relation to word
> occurrences in the corpus
>
> 3 Optimization objective of the GloVe algorithm
>
> 4 Weighting factor to account for frequent and infrequent
> words
>
> 5 Symmetry of the roles of theta and e in the GloVe
> algorithm
>
> 6 Training procedure for the GloVe algorithm

<br>

<a id="node-tilsalw"></a>

<p align="center"><kbd><img src="assets/57qchtm9567.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là define Xij mang ý nghĩa 'how often từ i và từ j xuất hiện cùng
> nhau' - tính bằng cách đếm số lần từ i xuất hiện khi có j xuất hiện
>
>
>
> Xij sẽ = Xji nếu ta quy định theo kiệu 'có xuất hiện gần nhau' còn nếu quy
> định theo kiểu từ này xuất hiện ngay sau từ kia  thì có thể Xij khác Xji.

<br>

<a id="node-g5zb6n8"></a>

<p align="center"><kbd><img src="assets/2slo4qrr01i.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là xây dựng optimization objective như vậy - minimize
> Tuy đơn giản những thật sự sẽ giúp làm được Word Embedding
> rất tốt
>
>
>
> Hàm f là để kiểm soát không xảy ra 0log0 - nếu Xij = 0 thì bỏ qua, đại
> khái vậy Đồng thời để tăng giảm 'tần xuất / trọng số / mức độ' của các
> từ the/a/an sao cho nó không quá cao và những từ hiếm như 'durian'
> sao cho nó không quá thấp.
>
> Chữ màu xanh chưa hiểu lắm nhưng đại khái
> ổng nói một điều funny là Theta_i và e_j có vai
> trò symmetric -  (như nhau??) nên Ew (final) có
> thể tính bằng trung bình của e_w và theta_w

<br>

<a id="node-89zzl35"></a>

<p align="center"><kbd><img src="assets/22wnw78jww9.png" width="80%"></kbd></p>

> [!NOTE]
> Cũng chưa hiểu lắm

<br>

<a id="node-7q8ggjx"></a>

## Applications Using Word Embeddings

<br>

<a id="node-yil7mrd"></a>

### Sentiment Classification

<br>

<a id="node-0uvo3ap"></a>

<p align="center"><kbd><img src="assets/7zp8csnli1t.png" width="80%"></kbd></p>

<br>

<a id="node-l923fve"></a>

<p align="center"><kbd><img src="assets/3p3pyqqba7c.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là một cách đơn giản có thể tạo model như vầy, mỗi từ trong
> comment biến thành one-hot vector, rồi embedding vector nhờ
> Embedding Matrix (download pre-trained E matrix), tính average thành 1
> vector lại rồi bỏ vào một layer softmax với 5 unit (thể hiện rating từ 1 - 5)
> -> y^ và train network simple này
>
>
>
> Nhưng solution đơn giản này thì bị cái là nó sẽ không xử lý tốt  data kiểu
> như " Completely lacking in **good** taste, **good** service, and **good**
> ambience" vì câu này sẽ có vẻ good hơn là bad

<br>

<a id="node-u3u7f2m"></a>

<p align="center"><kbd><img src="assets/x9n9vz6z3y.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là đây là một cách hiệu quả hơn phương án trước, ở đây ta train
> model bằng RNN theo structure many-to-one như trong hình.
>
>
>
> Với cách làm này ổng nói nó sẽ work rất tốt, và ngay cả khi ví dụ
> như thay 'lacking' bằng 'absent' - một từ không có trong training
> set nhưng miễn là nó xuất hiện khi training cái Embedding Matrix E
> mà cái này chắc chắn phải có rồi vì E được train với cả tỷ từ lận - thì
> model vẫn sẽ work tốt với các từ mới này

<br>

<a id="node-523mf3w"></a>

### Debiasing Word Embeddings

<br>

<a id="node-msy88bt"></a>

> [!NOTE]
> 1 Machine learning and AI algorithms are increasingly trusted to make
> important decisions, and it is important to eliminate bias in their
> decisions.
>
> 2 Word embeddings, which can learn analogies, may reflect gender,
> ethnicity, age, sexual orientation, and other biases of the text used to
> train the model.
>
> 3 Bias relating to socioeconomic status is also a concern, as machine
> learning algorithms are used in important decisions ranging from
> college admissions to the criminal justice system.
>
> 4 To reduce or eliminate bias in word embeddings, one can \\*identify
> the direction corresponding to a particular bias\\* and \\*perform
> neutralization to get rid of bias in words that are not definitional\\*.
>
> 5 \\*The bias direction can be found using a singular value
> decomposition algorithm\\*, and the neutralization step can make
> words gender-neutral.

<br>

<a id="node-auby3b5"></a>

<p align="center"><kbd><img src="assets/7gyju1y8mjk.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là làm sao để ML không tạo ra những kết quả có định kiến /
> thiên kiến (bias)

<br>

<a id="node-1dz55ht"></a>

<p align="center"><kbd><img src="assets/5yhxinmjl3b.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là làm 3 bước:
>
>
>
> 1. Xác định bias direction: Đại khái là bằng cách tính average hiệu
> của một số vector như e_he - e_she, e_male - e_female .. ta sẽ
> xác định được đâu là '**Bias direction**'. 
>
>
>
> 2. Tiếp những từ **'non-definitional'** thì **project** để loại bỏ bias - khái
> niệm '**project**' tương tư như của **Principal Component Analysis.**
>
>
>
> 3. Đại khái là **manually** chọn ra các cặp từ cần phải được '**equalize**'
> - để đảm bảo loại bỏ hoàn toàn bias.
>
>
>
> Nói chung đại khái là vậy nhưng cụ thể thế nào thì phải qua
> Programming Assigment mới rõ dc
>
> Đại khái là
>
>
>
> Bước 1: Cái từ nào nên 'trung tính' thì 'quán chiếu' nó về trục trung
> tính - để chi, để nó trung tính với các từ phân giới tính. đó là bước
> 1.
>
>
>
> Bước 2: Đại khái là 'biến' các từ (chính xác hơn là vector của từ)
> phân giới tính thành hoàn toàn đối xứng với trục trung tính.
>
>
>
> Với 2 bước này, từ cần trung tính hoàn toàn nằm trên trục trung tính
> (kết quả của bước 1) sẽ cách đều các từ phân tính từ đó đảm bảo
> các từ như computer, babysitter không hề nghiêng về phía nữ hay
> nam
>
>
>
> Các bước làm này đều là những phép toán biến đổi vector, trong đó
> bước một dùng PCA để quán chiếu biến các vector từ trung tính mà
> giảm thiểu thay đổi giá trị nó (đại khái vậy)

<br>

<a id="node-5f4rxk0"></a>

## Quiz

<br>

<a id="node-m9xmbyq"></a>

<p align="center"><kbd><img src="assets/t4y6765ye.png" width="80%"></kbd></p>

<br>

<a id="node-z252eq1"></a>

<p align="center"><kbd><img src="assets/zt0pjjuoq3n.png" width="80%"></kbd></p>

<br>

<a id="node-oyyr9r9"></a>

<p align="center"><kbd><img src="assets/9hbha1z65k.png" width="80%"></kbd></p>

<br>

<a id="node-84s5dqm"></a>

<p align="center"><kbd><img src="assets/gzc2ny5vbtl.png" width="80%"></kbd></p>

<br>

<a id="node-epu6zg2"></a>

<p align="center"><kbd><img src="assets/3vhkoxr86uh.png" width="80%"></kbd></p>

<br>

<a id="node-93pttc4"></a>

<p align="center"><kbd><img src="assets/c6zbjo4oc1r.png" width="80%"></kbd></p>

<br>

<a id="node-c1i64ja"></a>

<p align="center"><kbd><img src="assets/h4388u5ciu.png" width="80%"></kbd></p>

<br>

<a id="node-xaau692"></a>

<p align="center"><kbd><img src="assets/87ymuazcwnr.png" width="80%"></kbd></p>

<br>

<a id="node-5k33139"></a>

<p align="center"><kbd><img src="assets/36soqoisior.png" width="80%"></kbd></p>

<br>

<a id="node-6oo515r"></a>

<p align="center"><kbd><img src="assets/n1looitftme.png" width="80%"></kbd></p>

<br>

<a id="node-lxvcz67"></a>

<p align="center"><kbd><img src="assets/j57dm6x735s.png" width="80%"></kbd></p>

<br>

<a id="node-m2f149x"></a>

## Programming Assignments 1

<br>

<a id="node-06pnwcm"></a>

<p align="center"><kbd><img src="assets/c0frrgbfcou.png" width="80%"></kbd></p>

> [!NOTE]
> Welcome to your first assignment of Week 2, Course 5 of the Deep Learning Specialization!
>
> Because word embeddings are very computationally expensive to train, most ML practitioners
> will load a pre-trained set of embeddings. In this notebook you'll try your hand at \\_\\*loading\\*\\_,
> \\_\\*measuring similarity between\\*\\_, and \\_\\*modifying pre-trained embeddings\\*\\_.
>
> \\*After this assignment you'll be able to\\*:
>  • Explain how word embeddings capture relationships between words
>  • Load pre-trained word vectors
>  • Measure similarity between word vectors using cosine similarity
>  • Use word embeddings to solve word analogy problems such as Man is to Woman as King is to \\*__\\*.
>
>
> At the end of this notebook you'll have a chance to try an optional exercise, where you'll modify
> word embeddings to \\_\\*reduce their gender bias\\*\\_. Reducing bias is an important
> consideration in ML and NLP, so you're encouraged to take this chall

<br>

<a id="node-wjj9ojv"></a>

#### Packages

<br>

<a id="node-carmb37"></a>

#### 1 - Load the Word Vectors

<br>

<a id="node-m2ltui9"></a>

<p align="center"><kbd><img src="assets/jlufaryuht.png" width="80%"></kbd></p>

<br>

<a id="node-s4yk7wp"></a>

> [!NOTE]
> 2 - Embedding Vectors
> Versus One-Hot Vectors

<br>

<a id="node-x99fk0r"></a>

<p align="center"><kbd><img src="assets/hdglv6bxdnv.png" width="80%"></kbd></p>

<br>

<a id="node-dmttc24"></a>

#### 3 - Cosine Similarity

<br>

<a id="node-rymb702"></a>

<p align="center"><kbd><img src="assets/zftvsaq71tr.png" width="80%"></kbd></p>

<br>

<a id="node-td2i7zm"></a>

> [!NOTE]
> Exercise 1 - cosine_similarity
>
> Theo công thức, dễ chỉ có chú yý arg dùng 1D
> vector khá nguy hiểm

<br>

<a id="node-xbj6wfh"></a>

<p align="center"><kbd><img src="assets/946xqo0uram.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/49br1dyw8qu.png" width="80%"></kbd></p>

<br>

<a id="node-pxm7s7m"></a>

<p align="center"><kbd><img src="assets/h5for0o1p7.png" width="80%"></kbd></p>

<br>

<a id="node-9yb93ov"></a>

<p align="center"><kbd><img src="assets/6kuvj9e04vj.png" width="80%"></kbd></p>

<br>

<a id="node-3zvh9xe"></a>

#### 4 - Word Analogy Task

<br>

<a id="node-2hd4r2v"></a>

> [!NOTE]
> Exercise 2 -
> complete_analogy

<br>

<a id="node-cuiufz5"></a>

<p align="center"><kbd><img src="assets/frw1bqclzgs.png" width="80%"></kbd></p>

<br>

<a id="node-wvpz9e1"></a>

> [!NOTE]
> \\*Congratulations! \\*You've come to the end of the graded portion of the
> assignment. By now, you've:
>
> • Loaded some pre-trained word vectors
>
> • Measured the similarity between word vectors using cosine similarity
>
> • Used word embeddings to solve word analogy problems such as Man is to
> Woman as King is to __.
>
> Cosine similarity is a relatively simple and intuitive, yet powerful, method you
> can use to capture nuanced relationships between words. These exercises
> should be helpful to you in explaining how it works, and applying it to your
> own projects!
>
> \\*What you should remember\\*:  • Cosine similarity is a good way to
> compare the similarity between pairs of word vectors.
>
> ▪ Note that L2 (Euclidean) distance also works.
>
> • For NLP applications, using a pre-trained set of word vectors is often a
> great way to get started.

<br>

<a id="node-bpzmiov"></a>

> [!NOTE]
> 5 - Debiasing Word Vectors
> (OPTIONAL/UNGRADED)
>
> Đại khái là
>
>
>
> Bước 1: Cái từ nào nên 'trung tính' thì 'quán chiếu' nó về trục trung
> tính - để chi, để nó trung tính với các từ phân giới tính. đó là bước
> 1.
>
>
>
> Bước 2: Đại khái là 'biến' các từ (chính xác hơn là vector của từ)
> phân giới tính thành hoàn toàn đối xứng với trục trung tính.
>
>
>
> Với 2 bước này, từ cần trung tính hoàn toàn nằm trên trục trung tính
> (kết quả của bước 1) sẽ cách đều các từ phân tính từ đó đảm bảo
> các từ như computer, babysitter không hề nghiêng về phía nữ hay
> nam
>
>
>
> Các bước làm này đều là những phép toán biến đổi vector, trong đó
> bước một dùng PCA để quán chiếu biến các vector từ trung tính mà
> giảm thiểu thay đổi giá trị nó (đại khái vậy)

<br>

<a id="node-fywl6lh"></a>

> [!NOTE]
> 5.1 - Neutralize Bias for
> Non-Gender Specific Words
>
> Đại khái là thực hiện việc biến một vector từ cần trung tính để
> nó 'trung tính' với vector bias - vector định kiến tức là làm sao
> để cho nó vuông góc với bias vector -> cosin similarity = 0 -> Ko
> liên quan đến nhau

<br>

<a id="node-o4vkptl"></a>

<p align="center"><kbd><img src="assets/apcbb0wi4ew.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thực hiện việc biến một vector từ cần trung tính để
> nó 'trung tính' với vector bias - vector định kiến tức là làm sao
> để cho nó vuông góc với bias vector -> cosin similarity = 0 -> Ko
> liên quan đến nhau

<br>

<a id="node-b0ez9l6"></a>

> [!NOTE]
> Exercise 3 - neutralize
>
> Làm theo công thức thôi

<br>

<a id="node-uev7fef"></a>

<p align="center"><kbd><img src="assets/tpvt6hk24k8.png" width="80%"></kbd></p>

<br>

<a id="node-py53au0"></a>

<p align="center"><kbd><img src="assets/ycy08ltcibs.png" width="80%"></kbd></p>

<br>

<a id="node-5x0h93j"></a>

<p align="center"><kbd><img src="assets/uwlu3oe14uf.png" width="80%"></kbd></p>

<br>

<a id="node-nzrxn7n"></a>

> [!NOTE]
> 5.2 - Equalization Algorithm for
> Gender-Specific Words

<br>

<a id="node-xeszbi4"></a>

<p align="center"><kbd><img src="assets/npxcfgywwf.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là biến đổi các vector từ phân tính thành ra cách đều
> trục trung tính giúp loại bỏ hoàn toàn bias

<br>

<a id="node-y1ow4eh"></a>

<p align="center"><kbd><img src="assets/qxb8wjqjgwc.png" width="80%"></kbd></p>

<br>

<a id="node-89bocea"></a>

##### Exercise 4 - equalize

<br>

<a id="node-tarhao5"></a>

<p align="center"><kbd><img src="assets/0smf3jb9439j.png" width="80%"></kbd></p>

<br>

<a id="node-9oxy2q3"></a>

<p align="center"><kbd><img src="assets/2tghy1jw3cm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là giờ nó gần
> như bằng nhau rồi

<br>

<a id="node-uwfeloa"></a>

<p align="center"><kbd><img src="assets/y7uhn5f1oue.png" width="80%"></kbd></p>

<br>

<a id="node-jf51xnp"></a>

> [!NOTE]
> \\*Congratulations!
>
> \\*You have come to the end of both graded and
> ungraded portions of this notebook, and have seen
> several of the ways that word vectors can be applied
> and modified. Great work pushing your knowledge in
> the areas of neutralizing and equalizing word vectors!
> See you next time.

<br>

<a id="node-cqsjpkk"></a>

#### 6 - References

<br>

<a id="node-ldqlkrx"></a>

## Programming Assignments 2

<br>

<a id="node-j2ainjf"></a>

> [!NOTE]
> \\*What you'll build:
>
> \\* 1 In this exercise, you'll start with a baseline model (Emojifier-V1)
> using word embeddings.
>
> 2 Then you will build a more sophisticated model (Emojifier-V2) that
> further incorporates an LSTM. By the end of this notebook, you'll be
> able to:
>
> • Create an embedding layer in Keras with pre-trained word vectors
>
> • Explain the advantages and disadvantages of the GloVe algorithm
>
> • Describe how negative sampling learns word vectors more efficiently
> than other methods
>
> • Build a sentiment classifier using word embeddings
>
> • Build and train a more sophisticated classifier using an LSTM

<br>

<a id="node-41ph7u7"></a>

#### Packages

<br>

<a id="node-v4q8yj9"></a>

<p align="center"><kbd><img src="assets/6ka7s19ev8x.png" width="80%"></kbd></p>

<br>

<a id="node-9w40qw1"></a>

#### 1 - Baseline Model: Emojifier-V1

<br>

<a id="node-p5g2l9d"></a>

##### 1.1 - Dataset EMOJISET

<br>

<a id="node-bpc81va"></a>

<p align="center"><kbd><img src="assets/viu9m0of12o.png" width="80%"></kbd></p>

<br>

<a id="node-za0mbe2"></a>

<p align="center"><kbd><img src="assets/klfyylwu11f.png" width="80%"></kbd></p>

<br>

<a id="node-t1x02sp"></a>

<p align="center"><kbd><img src="assets/pjsze6xf1af.png" width="80%"></kbd></p>

<br>

<a id="node-7ptu9xc"></a>

##### 1.2 - Overview of the Emojifier-V1

<br>

<a id="node-bhjqo1g"></a>

<p align="center"><kbd><img src="assets/22zni7igay.png" width="80%"></kbd></p>

<br>

<a id="node-ej680ba"></a>

<p align="center"><kbd><img src="assets/gvghm9n843u.png" width="80%"></kbd></p>

<br>

<a id="node-y0y168f"></a>

##### 1.3 - Implementing Emojifier-V1

<br>

<a id="node-xi703sf"></a>

<p align="center"><kbd><img src="assets/whr6qbdbb2.png" width="80%"></kbd></p>

<br>

<a id="node-p092ezl"></a>

> [!NOTE]
> Exercise 1 - sentence_to_avg
>
> Đại khái là tách 1 câu thành list các từ, biến mỗi từ thành
> embedding vector nhờ Embedding Matrix (ở đây chỉ là 1
> dictionary, word -> vector), rồi tính 1 vector average của
> các e vector đó. Sẽ là vector "đại diện" cho sentence

<br>

<a id="node-naby75h"></a>

<p align="center"><kbd><img src="assets/0zuew1q8ue1p.png" width="80%"></kbd></p>

<br>

<a id="node-h7h19ca"></a>

<p align="center"><kbd><img src="assets/fo6jjnu5pcj.png" width="80%"></kbd></p>

<br>

<a id="node-vzvvszd"></a>

<p align="center"><kbd><img src="assets/mh1e0jg2rva.png" width="80%"></kbd></p>

<br>

<a id="node-7s64pur"></a>

##### 1.4 - Implement the Model

<br>

<a id="node-0ryuphs"></a>

<p align="center"><kbd><img src="assets/3j07y1wvjcj.png" width="80%"></kbd></p>

<br>

<a id="node-v1w4o3n"></a>

> [!NOTE]
> Exercise 2 - model
>
> Đại khái là:
> Forward prop tính cost function
> Loop trong iteration, 
> Loop trong m
> Với mỗi data sample (là 1 sentence), biến thành embedding vector (của 
> Sentence đó) bằng function đã làm.
> Dùng công thức tính z(i), a(i) hay y^(i), loss(i), cộng dồn loss vào cost
> Dùng công thức (cũng đơn giản nên tự biết, ở đây ổng ko nói mà làm sẵn)
> để backward prop tính gradient dW, db
> Update W, b

<br>

<a id="node-qfth3ue"></a>

<p align="center"><kbd><img src="assets/5aguuyo5ide.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3ka9f0jc03f.png" width="80%"></kbd></p>

<br>

<a id="node-yg6l1a2"></a>

<p align="center"><kbd><img src="assets/r77hy02o2x.png" width="80%"></kbd></p>

<br>

<a id="node-bda164j"></a>

<p align="center"><kbd><img src="assets/gdwpektd5ia.png" width="80%"></kbd></p>

<br>

<a id="node-8f4bqu5"></a>

<p align="center"><kbd><img src="assets/78srhaik93u.png" width="80%"></kbd></p>

<br>

<a id="node-da03zkf"></a>

<p align="center"><kbd><img src="assets/3sri0relvpv.png" width="80%"></kbd></p>

<br>

<a id="node-1x78lkg"></a>

##### Training

<br>

<a id="node-agbxj08"></a>

<p align="center"><kbd><img src="assets/ejjdebyzpk.png" width="80%"></kbd></p>

<br>

<a id="node-ivlqh04"></a>

##### 1.5 - Examining Test Set Performance

<br>

<a id="node-zk0xpjz"></a>

<p align="center"><kbd><img src="assets/h01ce94wem.png" width="80%"></kbd></p>

<br>

<a id="node-38yexsv"></a>

<p align="center"><kbd><img src="assets/o1ss080kje.png" width="80%"></kbd></p>

<br>

<a id="node-b0n2ucd"></a>

<p align="center"><kbd><img src="assets/4qh7gygeq9g.png" width="80%"></kbd></p>

<br>

<a id="node-4a90vht"></a>

> [!NOTE]
> What you should remember:
>
> Even with a mere 127 training examples, you can get a reasonably good
> model for Emojifying.
>
> This is due to the generalization power word vectors gives you.
>
> Emojify-V1 will perform poorly on sentences such as *"This movie is not
> good and not enjoyable"*
>
> It doesn't understand combinations of words.
>
> It just averages all the words' embedding vectors together, without
> considering the ordering of words.

<br>

<a id="node-zt5bvpi"></a>

#### 2 - Emojifier-V2: Using LSTMs in Keras

<br>

<a id="node-vyakr0t"></a>

##### 2.1 - Model Overview

<br>

<a id="node-fmastsr"></a>

<p align="center"><kbd><img src="assets/wkmigpjy79j.png" width="80%"></kbd></p>

<br>

<a id="node-5hilfo4"></a>

<p align="center"><kbd><img src="assets/fuxvt32ipav.png" width="80%"></kbd></p>

<br>

<a id="node-7enoonx"></a>

##### 2.2 Keras and Mini-batching

<br>

<a id="node-whdlhhz"></a>

<p align="center"><kbd><img src="assets/j6o8ophhpb.png" width="80%"></kbd></p>

<br>

<a id="node-6p3usyr"></a>

##### 2.3 - The Embedding Layer

<br>

<a id="node-wdoj8yy"></a>

<p align="center"><kbd><img src="assets/upnsreyh6m.png" width="80%"></kbd></p>

<br>

<a id="node-40uqnz1"></a>

> [!NOTE]
> Nói rất rõ, đại khái là ta có thể train Embedding layer hoặc dùng
> pre-trained weight.
>
> Mục đích cuối cùng của Embedding layer là biến một từ thành
> một embedding vector sao cho nó đại diện được tốt nhất của từ
> đó ở các khía cạnh, giúp quá trình học / huấn luyện đạt được
> hiệu quả (ví dụ giúp train ra một model có thể translate một câu
> tiếng Pháp sang câu tiếng Anh chuẩn nhất)
>
> Do đó nếu chỉ định Embedding layer là trainable (có dùng
> pre-trained weights hay không cũng dc) thì khi train (phải hiểu là
> train cả 1 Network thì nó sẽ tìm cách cải thiện cái việc
> Embedding này sao cho đạt được mục đích ở trên - bằng cách
> tìm ra weight tốt nhất

<br>

<a id="node-e6eoy8l"></a>

<p align="center"><kbd><img src="assets/1dpmdk3v8hv.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/lapsx438lq.png" width="80%"></kbd></p>

<br>

<a id="node-x307hxn"></a>

> [!NOTE]
> Exercise 3 - sentences_to_indices
> Ini X_index = zeros (m, max_len)
> Loop trong m, lấy từng câu (data sample) ra
> Split câu ra
> Loop trong các từ, biến mỗi từ thành index nhờ word_to_index (dictionary)
> Gán vào X_index tại vị trí i,j
>
> Như vậy các vector (chính là các hàng của X_index) đếu bằng size nhau (max_length)
> mà cái nào ngắn sẽ được fill bằng 0.

<br>

<a id="node-5rif23t"></a>

<p align="center"><kbd><img src="assets/yw8ch8t4djd.png" width="80%"></kbd></p>

<br>

<a id="node-dlcljqy"></a>

<p align="center"><kbd><img src="assets/bwbavhjvx8.png" width="80%"></kbd></p>

<br>

<a id="node-thcsh3c"></a>

<p align="center"><kbd><img src="assets/g25xokxl3j.png" width="80%"></kbd></p>

<br>

<a id="node-p299y53"></a>

<p align="center"><kbd><img src="assets/6at4f5tl2fi.png" width="80%"></kbd></p>

<br>

<a id="node-7hcsfrp"></a>

##### Exercise 4 - pretrained_embedding_layer

<br>

<a id="node-wuwkpv2"></a>

<p align="center"><kbd><img src="assets/z9box62267.png" width="80%"></kbd></p>

**🔗 See also:** [linked note](#node-b4gjyv5)

<br>

<a id="node-9w7kqkt"></a>

> [!NOTE]
> Ở đây nói rất rõ là ta sẽ tự define Embedding layer BẰNG cách
> \\*'set the embedding weights to be equal to the embedding
> matrix'\\*
>
> Bằng cách nào đó, tải trên mạng blah blah ta có một \\*dictionary\\*
> Trong đó \\*mỗi từ sẽ với tương ứng một embedded vector\\* mà
> vector này đại diện cho nó, có tính chất như thế nào thì xem  lại
> theo link (mà đại khái là embedded vector dc tạo ra nhằm mục
> đích chứa trong mình những thông tin hữu ích về các khía cạnh
> của từ đó như giới tính, ngành nghề ....)
>
> Như vậy, Embedding layer sẽ đại khái là \\*nhận một từ thì biến thành
> một embedded vector\\*, nhận \\*một list\\* các từ (1 câu/1 sequence /
> vector) thì biến thành một \\*matrix\\*. Nói chúng là bỏ vào 1 volume
> (hay còn gọi là Tensor) có \\*mấy dimension\\* thì nó \\*tạo ra thêm một
> dimension\\* nữa, vì cứ 1 từ (sẽ biểu thị bởi 1 con số - index) thì nó
> tạo một vector

**🔗 See also:** [linked note](./c5w4_transformer_network.md#node-nvxlrgw)

<br>

<a id="node-9wym0fc"></a>

<p align="center"><kbd><img src="assets/m4r8mxgexka.png" width="80%"></kbd></p>

> [!NOTE]
> Dù có thắc mắc là **tại sao input_dim** lại bằng **vocab_size**
> nhưng có thể hiểu là Embedding nó có nhiệm vụ là:.. 
>
>
>
> Embedding một **index input** thành một **embedding vector**, 
> nên nó như một dictionary

**🔗 See also:** [linked note](./c5w4_transformer_network.md#node-7vptaod)

<br>

<a id="node-a0p5sl5"></a>

<p align="center"><kbd><img src="assets/oxjbgw2fbwo.png" width="80%"></kbd></p>

<br>

<a id="node-eqmtepv"></a>

##### 2.4 - Building the Emojifier-V2

<br>

<a id="node-vq5g77s"></a>

<p align="center"><kbd><img src="assets/pwal21l9wk.png" width="80%"></kbd></p>

<br>

<a id="node-d669ujq"></a>

##### Exercise 5 - Emojify_V2

<br>

<a id="node-19p38ir"></a>

<p align="center"><kbd><img src="assets/xgvb4jpzd3n.png" width="80%"></kbd></p>

<br>

<a id="node-uj3m0nw"></a>

<p align="center"><kbd><img src="assets/ieakmgzgmu.png" width="80%"></kbd></p>

<br>

<a id="node-kvy1oq9"></a>

<p align="center"><kbd><img src="assets/tksitoz7bpl.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/99jmr5e7i5g.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu Embedding layer lắm (input, output shape) -> Cứ hiểu tạm là nó
> được define để bỏ vào index thì cho ra embedding vector, nên đầu vào là input
> volume shape bao nhiêu ko biết cứ qua nó là thành ra tăng thêm 1 chiều nữa
> (vì idx number
> - 1D thành vector - 2D) -> Hiểu vậy là đúng rồi đó, đọc cái giải thích ChatGPT

<br>

<a id="node-vsvgbaf"></a>

<p align="center"><kbd><img src="assets/tu7ljc23v3.png" width="80%"></kbd></p>

> [!NOTE]
> In Keras, an embedding layer is a type of layer that maps \\*input values\\* (such
> as words or categorical variables) to \\*fixed-size vectors of real numbers\\*, also
> known as embeddings. These embeddings can be used as a more compact
> and dense representation of the original input, making it easier to work with
> and analyze.
>
> The embedding layer takes as input a matrix of integers, where each row
> represents a sequence of input values. Each value in the matrix represents a
> categorical variable, such as a word or an item in a list of categories. The layer
> then looks up the corresponding \\*embedding vector\\* for each \\*input value\\* in a
> \\*lookup table\\*, which is \\*learned during training\\*.
>
> The size of the embedding vectors is a hyperparameter that needs to be
> specified when defining the layer. The dimensionality of the embedding space
> should be chosen such that it is large enough to capture the relevant
> information in the input data, but not so large as to introduce overfitting.
>
> The output of the embedding layer is a matrix of the same shape as the input
> matrix, but with \\*each integer value replaced by its corresponding embedding
> vector\\*. This matrix can then be passed on to further layers for processing.
>
> Overall, the embedding layer in Keras is a powerful tool for transforming
> categorical inputs into dense, continuous representations that can be more
> easily processed by neural networks. It is commonly used in natural language
> processing (NLP) applications, where it is used to represent words or
> sequences of words as embeddings.

<br>

<a id="node-b4gjyv5"></a>

> [!NOTE]
> Đại khái là mỗi input value sẽ được replace bởi 1 embedded
> vector (mà item value của vector đó là real number)
>
> Bằng cách nó look up value từ 1 lookup table được \\*learned
> during trainning.\\*
>
> Kểu như mình có thể:  Pre-train rồi gán trainable = false
> để không train lại cái embedding layer này
>
> Pre-train rồi gán trainable = true để tiếp tục train embedding
> layer này
>
> Hoặc Train từ đầu (không có pre-train gì cả)
>
> Thì trong assigment này chính là xài cái \\*pre-train và không
> train lại\\*

**🔗 See also:** [linked note](#node-wuwkpv2)

<br>

<a id="node-gjc4mm2"></a>

<p align="center"><kbd><img src="assets/1a6phf9csc1.png" width="80%"></kbd></p>

> [!NOTE]
> Params cua Embedding layer không trainable

<br>

<a id="node-7anfm5w"></a>

##### 2.5 - Train the Model

<br>

<a id="node-pg5uzi8"></a>

<p align="center"><kbd><img src="assets/hzc3st4vddv.png" width="80%"></kbd></p>

<br>

<a id="node-gchl5cw"></a>

<p align="center"><kbd><img src="assets/k6k2oax9qkj.png" width="80%"></kbd></p>

<br>

<a id="node-rs8qmus"></a>

<p align="center"><kbd><img src="assets/5jcheyfi5d3.png" width="80%"></kbd></p>

<br>

<a id="node-4fn5rak"></a>

> [!NOTE]
> \\*Congratulations! \\*You've completed this notebook, and
> harnessed the power of LSTMs to make your words more
> emotive! ❤️❤️❤️
>
> By now, you've:
>
> • Created an embedding matrix
>
> • Observed how negative sampling learns word vectors more
> efficiently than other methods
>
> • Experienced the advantages and disadvantages of the GloVe
> algorithm
>
> • And built a sentiment classifier using word embeddings!
>
> Cool! (or Emojified: 😎😎😎 )

<br>

<a id="node-c8j7zy2"></a>

<p align="center"><kbd><img src="assets/zzqdk223tt.png" width="80%"></kbd></p>

<br>

<a id="node-0gquaqz"></a>

#### 3 - Acknowledgments

<br>

