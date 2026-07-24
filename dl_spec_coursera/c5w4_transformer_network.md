# C5w4_transformer Network

📊 **Progress:** `193` Notes | `202` Screenshots

---
<a id="node-xh0n1jx"></a>

## C5w4_transformer Network

<br>

<a id="node-ogkrnna"></a>

## Transformers Network

<br>

<a id="node-yavzysp"></a>

### Transformer Network Intuition

<br>

<a id="node-qx9sqt6"></a>

> [!NOTE]
> Main idea:
>
> The transformer architecture is a complex neural network architecture that
> has **revolutionized the field of NLP**. It allows for **parallel processing of
> sequences**, unlike traditional sequential models such as RNNs, GRUs, and
> LSTMs.
>
> The major innovation of the transformer architecture is **combining** the use of
> **attention-based representations** and a **CNN-style of processing**.
>
> **Self-attention** and **multi-headed attention** are the two key ideas that go into
> **computing rich representations** for **all the words in a sentence in parallel.**
> These representations can be used for machine translation or other NLP
> tasks to create effectiveness.
>
> The transformer architecture was introduced in a seminal paper and has
> been widely used in the field.
>
> The next few videos will dive into the transformer architecture piece by piece
> so that viewers can understand how it works and apply it with ease.

<br>

<a id="node-9n7oizs"></a>

<p align="center"><kbd><img src="assets/5yc17ajdmyu.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ổng nói  RNN thì bị vanishing gradient khiến mất thông tin
> khi phải truyền đường dài và GRU và LSTM giúp khắc phục chuyện đó
> trong việc nắm bắt "long range dependencies and sequences"
>
>
>
> Bất lợi là structure ngày càng phức tạp, và mỗi unit như 1 bottleneck
> khiến thông tin bị chậm đi khi phải di chuyển qua nhiều 'node' (ví dụ
> trong sequence model) nên Transformer nó sẽ giúp thông tin đi song
> song cùng lúc với nhau

<br>

<a id="node-7csoluk"></a>

<p align="center"><kbd><img src="assets/5lfzyd8s2gf.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là
>
>
>
> Transformer network kết hợp tính chất 'parallel' của CNN, và Attention
> based representation
>
>
>
> 2 key ideas là **Self-attention**: Đại khái ví dụ ta có một chuỗi 5 từ thì
> ta sẽ tính ra representation của 5 từ đó.
>
>
>
> **Multi-head attention** thì dùng for loop để tìm những version khác
> nhau của những representation này.
>
>
>
> Và turn out là những **representation này rất giàu thông tin**, có thể dùng
> cho Machine Translation hay những NLP task khác

<br>

<a id="node-xd1qa6f"></a>

### Self-attention

<br>

<a id="node-ye63ywk"></a>

> [!NOTE]
> 1 Self-attention mechanism of transformers is **the most
> important core idea** behind what makes transformer networks
> work.
>
> 2 To \\/**use attention with a style more like CNNs**\\/, you need to
> **calculate self-attention**, where you create **attention-based
> representations for each of the words in your input sentence**.
>
> 3 For every word, you have three values called the **query**, **key**,
> and **value**, which are the key inputs to **computing the attention
> value for each word**.
>
> 4 The query, key, and value vectors are supposed to **pull up
> the most information** that's needed to help compute the most
> useful representation.
>
> 5 The goal of the operation is to **create attention-based
> representations** for each word that \\_**look at the surrounding
> words to figure out what's actually going on in how we're
> talking about the word in the sentence.**\\_

<br>

<a id="node-fedev9r"></a>

<p align="center"><kbd><img src="assets/fdbph18k0mn.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/95nx0v9o8cb.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ta cũng **embedding 1 từ thành 1 embedded vector**
>
>
>
> Nhưng thay vì chỉ đơn giản là look up embbeded vector từ
> Embedded matrix thì bây giờ..
>
>
>
> **Dựa vào hoàn cảnh**, sẽ chọn / **tính các embedded vector khác nhau
> kiểu như tuỳ tình huống phù hợp với từ này trong câu**.
>
>
>
> Kiểu như Africa là 1 châu lục? Africa là 1 di tích lịch sử? Africa là một địa
> điểm du lịch?
>
>
>
> Đó là **representation** vector A gọi là '**attention-based vector
> representation of a word**' = **vector đại diện của 1 từ được tính toán
> dựa trên hoàn cảnh xung quanh của từ đó**.
>
>
>
> Và khi tính toán thì thực ra nó cũn không khác mấy các cơ chế attention
> trong RNN bữa trước chỉ khác cái là nó làm /. tính **CÙNG LÚC** cho 5 từ
> trong câu chứ không phải 1.
>
> Nhìn trong công thức thấy sự tương đồng khi dùng softmax

<br>

<a id="node-1iakoqf"></a>

<p align="center"><kbd><img src="assets/3pwqtvjm3h8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vimdujd3xuh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/diwqso78bzb.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi: Ở Africa có gì xảy ra?
>
>
>
> Thì q<3>.k<1> sẽ đánh giá là nếu trả lời là 'Jane' thì tốt như thế nào.
> tương tự,
> Thì q<3>.k<2> sẽ đánh giá là nếu trả lời là 'visit' thì tốt như thế nào.
> Và tương tự vậy cho các từ khác.
>
>
>
> Tất cả nhằm mục đích:
> Gom tất cả thông tin cần thiết để tìm ra đại diện tốt nhất / hữu ích nhất
> = representation A<3> cho từ thứ 3 - l'Afrique.
>
>
>
> Rồi giả sử đại khái kết quả thấy q<3>.k<2> cho ra số lớn thì đại khái
> cho biết trạng thái phù hợp nhất để  Africa là một điạ điểm để visit.
>
>
>
> Rất khó giải thích nhưng hiểu hiểu đại khái là tìm ra cách để **embbed 
> tốt nhất đại diện cho 1 từ.**
>
> "The key advantage of this representation is the word of l'Afrique
> **isn't some fixed word embedding**. Instead, it lets the
> **self-attention mechanism realize that l'Afrique is the destination
> of a visite**, of a visit, and thus **compute a richer, more useful
> representation** for this word"
>
>
>
> Hiểu đại khái là A<3> không chỉ là một **fixed** word embedding -
> mà là một embedding **mang trong mình nhiều thông tin hữu ích
> hơn về hoàn cảnh của nó,** cụ thể trong tình huống này nó là một
> destination để mà visit
>
> Công thức tổng quát là vầy
>
>
>
> Denominator có dấu sqrt chỉ là để **scale cái dot-product attention**
>
>
>
> "The term in the denominator is just to scale the dot-product, so it
> **doesn't explode**. You don' t really need to worry about it. But another
> name for this type of attention is the **scaled dot-product attention**."
>
> q<3> = W(Q).x<3>
> k<3> = W(K).x<3>
> v<3> = W(V).x<3>

<br>

<a id="node-2sl6yie"></a>

<p align="center"><kbd><img src="assets/ini2121fwj.png" width="80%"></kbd></p>

> [!NOTE]
> To recap, associated with each of the five words you end up with a
> **query**, a **key**, and a **value**.
>
>
>
> The **query** lets you ask a question about that word, such as what's
> happening in Africa.
>
>
>
> The **key** looks at all of the other words, and **by the similarity to the
> query**, helps you figure out which **words gives the most relevant answer
> to that question**. In this case, visite is what's happening in Africa,
> someone's visiting Africa.
>
>
>
> Then finally, the **value** allows the representation to plug in **how 'visite'
> should be represented within A^3**, within the representation of Africa.
>
>
>
> This allows you to come up with **a representation for the word Africa
> that says this is Africa and someone is visiting Africa**. This is a **much
> more nuanced, much richer representation** for the word than if you just
> had to pull up the same fixed word embedding for every single word
> **without being able to adapt it based on what words are to the left and
> to the right of that word**. We've all got to **take into account and in the
> context**. Now, you have learned about the self-attention mechanism
>
> Đại khái là thông qua query, key và value mà ta tính
> toán được 1 vector representation của 1 từ mang
> trong mình thông tin hữu ích về hoàn cảnh của từ đó
> chứ không chỉ là 1 embedding vector luôn giống nhau

<br>

<a id="node-extfgpj"></a>

<p align="center"><kbd><img src="assets/vykd3g8d6j8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/w4gbn3voxe8.png" width="80%"></kbd></p>

<br>

<a id="node-yiois88"></a>

> [!NOTE]
> Có mấy cái mà mr Andrew hoàn toàn không nói tới hoặc mình không tự
> hiểu được đó là  Ba cái matrix Q, K, V được tạo ra như thế nào
>
> Thì đây, đaị khái là một cái Attention (không phải Self-attention nha) sẽ
> cần 3 cái **INPUT PARAMS có tên là Query, Key và Value** và ba cái này sẽ dùng để tính ra Q, K, V.
>
> Và (cái này thì ông Andrew có hint) là để làm Self-attention thì ba cái
> Query, Key và  Value sẽ **giống nhau**
>
> Đại khái là ta sẽ bỏ cái embedding-encoding block vào và cho nó **ĐỒNG
> THỜI LÀ Query, Key, và Value
>
> Rồi nó tính Q, K, V như thế nào?**
>
> Đại khái là thông qua **linear layer** của Attention với các weights matrix **W_Q**, **W_K**,
> **W_V** - Đều có size là (**emb_dim**, **emb_dim**). Qua các linear layer này Query, Key,
> Value input params (mà ta sẽ gán vào cho tụi nó bằng cái embedded sequence bao gồm
> word embedding và positional embedding) sẽ **" tạo ra"** ba matrix **Q**, **K**, **V**
> - đều có shape là **sequence_len** x **emb_dim**.
>
> Rồi từ Q,K,V nó sẽ tính ra **attention score** và nói ngắn gọn cộng với những cái mà Andrew
> cũng đã nói và giải thích rõ trong article 4 của loạt bài đó là: Trong quá trình training, tất cả
> các **word embedding vectors** và **weights** của Attention linear layers **W_Q**, **W_K**,**W_V** sẽ được
> **train** sao cho cách sắp xếp/kiến trúc của attention giúp minimize loss qua đó tìm ra được
> các weight và embedding sao cho word embedded vector phản ánh tốt nhất thông tin của 1
> từ.Khúc cuối này khá khó diễn đạt, nhưng đại khái là cách kiến trúc của Attention sẽ giúp khi
> training nó sẽ cải thiện dần dần embedding vector đồng nghĩa giảm dần cost.

<br>

<a id="node-wnlnswh"></a>

### Multi-head Attention

<br>

<a id="node-c7c6y85"></a>

> [!NOTE]
> 1 Multi-head attention mechanism is a modification of self-attention
> mechanism that involves **computing multiple self-attentions** for a given
> sequence.
>
> 2 The input vectors Q, K, and V are multiplied by matrices WQ, WK, and
> WV to obtain query, key, and value vectors for each input term.
>
> 3 The same set of query, key, and value vectors are used to compute
> multiple self-attentions.
>
> 4 Each self-attention calculation for a sequence is called a **head**, and the
> number of heads is denoted by **'h'**.
>
> 5 **Each head represents a different feature**, and the final output is the
> **concatenation of all the heads**.
>
> 6 The different heads' values can **be computed in parallel** because no
> head's value depends on the value of any other head.
>
> 7 In practice, the computation of different heads' values is not done in a big
> for-loop.

<br>

<a id="node-f699prf"></a>

<p align="center"><kbd><img src="assets/6q0zebhsrv9.png" width="80%"></kbd></p>

> [!NOTE]
> 1 "head" kiểu như 1 bộ các vector
> representation, multi-head có nghĩa là tính
> ra nhiều bộ chứ không chỉ có 1.
>
>
>
> Trong đó, để tính ra một bộ thì ta làm gì?
>
>
>
> Đ.v mỗi từ tính, ví dụ từ thứ nhất ta ra q<1>, k<1>, v<1> 
> Tính inner dot W1_Q.q<1>, W1_K.k<1>, W1_V.v<1>
>
>
>
> Làm vậy với các từ khác
>
>
>
> Cuối cùng là dùng các kết quả đó để tính ra "representation" của các
> từ, tạo thành một bộ các representation đầu tiên, đó là một 'head'
>
>
>
> Với 'head' đầu tiên này, biểu thị bởi số 1 trong W1_Q, W1_K, W1_V
> các matrix này kiểu được encoded để đặt câu hỏi: Điều gì đã xảy ra ở l'Afrique.
>
>
>
> Và trong quá trình tính toán (học. huấn luyện) nó cho thấy "visit" 
> đóng vai trò quan trọng để trả lời câu hỏi này, biểu thị bằng giá trị
> của W1_Q.q<2>, W1_K.k<2>, W1_V.v<2> "lớn nhất" (lớn nhất 
> như thế nào thì để hiểu hơn sau)

<br>

<a id="node-uyxqja0"></a>

<p align="center"><kbd><img src="assets/zjpzmq7u39n.png" width="80%"></kbd></p>

> [!NOTE]
> Xong head 1, tính head 2 thì  **W2_Q,K,V**...đại khái biểu thị câu hỏi khác,
> **khi nào** ở l'Afrique (**When**?) và cũng tính tương tự  để tính ra 1 bộ
> representation vector của các từ gọi là head #2
>
>
>
> Thì head 2 mang trong mình những thông tin hữu ích để trả lời câu hỏi "When"
> đ/v các từ - Chú ý là đ/v các từ nha, vì mỗi representation vector cho mỗi từ.
>
>
>
> Làm tương tự như vậy với **h** lần ví dụ 3 lần (h = 3) hay 8 lần (h=8). Ta có 8
> heads.
>
>
>
> Bây giờ **stack các head (concatenate)** lại và nhân cho một cái W_0 để tạo
> thành một ...**multi-head**
>
>
>
> Thì cái multi-head này chứa rất nhiều thông tin hữu ích của các  từ trong câu
> này.
>
>
>
> Và dù ổng nói cứ hình dung là ta lần lượt tính các head này nhưng  Thực tế thì
> ta **tính nó cùng lúc (parallel)** vì các head này độc lập với nhau

<br>

<a id="node-89jiytp"></a>

### Transformer Network

<br>

<a id="node-dazdkvt"></a>

> [!NOTE]
> 1 The transformer architecture **combines self-attention** and **multi-headed
> attention** mechanisms to perform sequence to sequence translation
> tasks.
>
> 2 The encoder block takes the **word embeddings** as input and uses
> **multi-headed attention to compute Q, K, and V matrices** which are then
> passed through a **feed-forward neural network**.
>
> 3 The **decoder** block generates the English translation **by using
> multi-headed attention to compute Q, K, and V matrices from the
> previous output** and the **French sentence embeddings**, and passing
> them through a **feed-forward neural network** to **generate the next word in
> the sequence**.
>
> 4 The transformer architecture uses **positional encoding** to account for
> the position of each word in the input sequence.
>
> 5 The transformer architecture is **repeated N times**, typically **six**, to
> **improve the accuracy** of the translation task.
>
> 6 The transformer architecture has additional features such as **residual
> connections**, **layer normalization**, and **masked multi-headed attention** to
> improve its performance.

<br>

<a id="node-6u7scrk"></a>

<p align="center"><kbd><img src="assets/pnmdrvmchep.png" width="80%"></kbd></p>

> [!NOTE]
> *Tất cả đều chỉ là hiểu đại khái như sau:
>
>
>
> Có vẻ như (trong bài trước mình chưa hiểu rõ lắm) đó là
> kết quả của bước multi-head attention tính ra representation
> của các từ gì đó chính là Q, K, V??? Cái này khi làm assignment
> sẽ quay lại xác nhận sau
>
>
>
> Trong thực tế người ta hay có thêm SOS (start of
> sentence)  token nữa sẽ hữu ích
>
>
>
> N times: Tính ra rồi lấy kết qủa quay ngược lại tính lại
>
>
>
> Mask: Che đi 1 phần, rồi xem thử n.n nó predict còn
> lại ra sao
>
>
>
> Add & Norm: Giống như batch norm giúp tăng tốc
>
>
>
> Positional encoding: công thức sin, cos là để mỗi
> vector p<> của mỗi từ đều khác nhau, và việc tính PE
> là để giúp lưu giữ thông tin vị trí của từng từ trong câu
> giúp ích cho sự translation

<br>

<a id="node-9a51ejb"></a>

<p align="center"><kbd><img src="assets/g6djrdht9lm.png" width="80%"></kbd></p>

> [!NOTE]
> Giải thích đại khái cái block thứ 2 Decoder:
>
>
>
> Ban đầu câu translation chưa có gì chỉ có SOS
>
>
>
> bỏ vào Multi-Head attention tính ra Q,
>
>
>
> Xong mới lấy K, V từ Encoder để vào M.H.A và
> FFNN và quay lại N lần để tính ra chữ thứ 2 là
> gì, hy vọng là nó ra 'Jane'.
>
>
>
> Có nghĩa là nó pull thông tin từ Encoder kết
> hợp những từ đã predict (Ban đầu chỉ có SOS -
> Bất đầu câu, sau đó là <SOS> Jane, <SOS>
> Jane visit..) để predict ra từ tiếp theo.

<br>

<a id="node-av4d591"></a>

<p align="center"><kbd><img src="assets/sezdcd8lhkb.png" width="80%"></kbd></p>

> [!NOTE]
> Giả sử **word embedding vector** của các từ là có 4 dimension,
> đồng nghĩa x<1>, x<2>,...đều là vector 4 dimensions
>
>
>
> Ta sẽ tạo tương ứng các **positional embedding vector** cũng có
> dimension = 4 p<1>, p<2>...
>
>
>
> Thì trong công thức tính PE, **pos** là 'numerical position' của từ, đối
> với "Jane" thì pos = 1
>
>
>
> '**i**' là vị trí trong encoding vector = 0,1,2,3
>
>
>
> Thì **sin, cos** đại khái là để tạo 1 **unique** (positional encoding)
> vector cho mỗi từ
>
>
>
> Ổng vẽ mấy cái plot của các i khác nhau là để giải thích 
> rằng sin, cos sẽ giúp p<1> (màu xanh) khác p<3> (màu tím)
>
>
>
> Và p<1> sẽ add directly vào x<1>
>
> Ngoài ra còn nói về **'Residual network**' giống như ở ResNet
>
>
>
> Nhớ lại Residual ở C4 mục đích đại khái là để giữ thông tin lỡ may
> bị gradient vanishing
>
>
>
> "And their purpose in this case is to **pass along positional
> information** **through the entire architecture**."
>
> Đại khái là với RNN thì do mình feed info vào từng từ một nên cơ bản nó có
> thông tin vị trí của các từ trong câu, còn với cái này (Transformer network) tất
> cả các từ xử lý cùng lúc nên không biết thứ tự của từ trong câu, positional
> encoding là để cung cấp thông tin này

<br>

<a id="node-n1q2vs7"></a>

<p align="center"><kbd><img src="assets/i44t127e3j.png" width="80%"></kbd></p>

> [!NOTE]
> "When training you have access to the entire correct
> English translation, the correct output and they're
> correct input.
>
>
>
> And because you have the full correct output you don't
> actually have to generate the words one at a time
> during training.
>
>
>
> Instead, what masking does is it blocks out the last part
> of the sentence to mimic what the network will need to
> do at test time or during prediction.
>
>
>
> In other words, all that mask multi- head attention does
> is repeatedly pretends that the network had perfectly
> translated.
>
>
>
> Say the first few words and hides the remaining words
> to see if given a perfect first part of the translation,
> whether the neural network can predict the next word in
> the sequence accurately."

<br>

<a id="node-in8hyim"></a>

### Loạt Bài Về Transfomrer Của Ketan Doshi

<br>

<a id="node-ncx1mr1"></a>

#### Part 1 - Overview

<br>

<a id="node-3md6k3a"></a>

##### What's a Tramfromer

<br>

<a id="node-9csr5no"></a>

<p align="center"><kbd><img src="assets/4ootzucet43.png" width="80%"></kbd></p>

<br>

<a id="node-5xbz4z6"></a>

<p align="center"><kbd><img src="assets/vtek62fayk.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là kiến trúc như hình:
> Tất cả các Encoder đều giống nhau hết, Decoder cũng
> vậy

<br>

<a id="node-5cnxmyi"></a>

<p align="center"><kbd><img src="assets/q1gsi3tjfxl.png" width="80%"></kbd></p>

> [!NOTE]
> The Encoder contains the all-important Self-attention layer that
> computes the relationship between different words in the sequence, as
> well as a Feed-forward layer.
>
>
>
> The Decoder contains the Self-attention layer and the Feed-forward
> layer, as well as a second Encoder-Decoder attention layer.
>
>
>
> Each Encoder and Decoder has its own set of weights.

<br>

<a id="node-ioq8kty"></a>

<p align="center"><kbd><img src="assets/9d56x5x3bu5.png" width="80%"></kbd></p>

> [!NOTE]
> Nhìn kĩ vào trong 1 Encoder, có Self-Attention
> layer, Feed-forward layer với Residual-skip
> connection và LayerNorms

<br>

<a id="node-bd5l5vc"></a>

##### What Attention do?

<br>

<a id="node-0d56qk5"></a>

<p align="center"><kbd><img src="assets/2fh4h92a203.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó giúp nắm bắt được từ nào thì quan hệ
> gần gũi / xa cách với từ nào
>
>
>
> "While processing a word, Attention enables the
> model to **focus** on other words in the input that
> are **closely related** to that word."
>
>
>
> Ví dụ trong câu này thì ball gần gũi với holding và
> blue hơn là boy. Kiểu như khi cần trả lời câu hỏi  "
> Làm gì với ball?" ->  Holding "Ball như thế nào?" ->
> Blue

<br>

<a id="node-8iia7rd"></a>

> [!NOTE]
> eg. Consider two sentences:
>
> The **cat** drank the milk because **it** was hungry.
> The cat drank the **milk** because **it** was sweet.
>
> Ví dụ trong 2 câu này thì từ 'it' "chỉ" tới 2 cái khác nhau

<br>

<a id="node-uve2i1e"></a>

<p align="center"><kbd><img src="assets/f3d1zlqjy6o.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là quan hệ của 'it' với các từ 'cat','milk' trong 2 câu sẽ hoàn toàn khác nhau.
> Câu đầu nó gắn mạnh với từ 'cat' hơn câu sau nó gắn mạnh với 'milk' hơn.

<br>

<a id="node-aj7gi4j"></a>

<p align="center"><kbd><img src="assets/hlf6mbygard.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Transformer sẽ include nhiều
> attention scores cho mỗi từ

<br>

<a id="node-6qa88js"></a>

##### Training the Transformer

<br>

<a id="node-zpxfwvo"></a>

<p align="center"><kbd><img src="assets/lqttf60czaf.png" width="80%"></kbd></p>

<br>

<a id="node-f0lz9w8"></a>

> [!NOTE]
> 1.The input sequence is **converted** into **Embeddings** (with **Position Encoding**)
> and **fed to the Encoder.**
>
> 2.The stack of Encoders processes this and produces an **encoded
> representation of the input sequence**.
>
> 3.The **target sequence** is **prepended** with a **start-of-sentence token**, converted
> into **Embeddings** (with Position Encoding), and fed to the Decoder.
>
> 4.The stack of Decoders processes this **along with the Encoder stack’s
> encoded representation** to produce an **encoded representation of the target
> sequence**.
>
> 5.The Output layer **converts** it into **word probabilities** and the **final output
> sequence**.
>
> 6.The Transformer’s **Loss function** **compares** this output sequence with the
> target sequence from the training data. This loss is used to generate gradients
> to train the Transformer during **back-propagation**.

<br>

<a id="node-fues3d6"></a>

##### Inference

<br>

<a id="node-s7cunjr"></a>

<p align="center"><kbd><img src="assets/bllegd7ehkv.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Inference khác Training là (tất nhiên) không có
> một target nào để 'bỏ vào' Decoder' mà thay vào đó là các '
> kết quả' từ previous step giống như Seq2Seq
>
>
>
> Nhưng thay vì chỉ bỏ 1 từ 'previous' step output gần nhất thì
> bỏ tất cả sequence dc tạo ra .

<br>

<a id="node-xj0l5i7"></a>

> [!NOTE]
> 1.The input sequence is **converted** into **Embeddings** (with **Position Encoding**) and **fed
> to the Encoder.**
>
> 2.The stack of Encoders **processes** this and produces **an encoded representation** of
> the input sequence.
>
> 3.Instead of the target sequence, we use an **empty sequence** with only a
> **start-of-sentence token**. This is converted into **Embeddings** (with **Position Encoding**)
> and **fed to the Decoder.**
>
> 4.The stack of Decoders **processes** this along **with the Encoder stack’s encoded
> representation** to produce an **encoded representation of the target sequence.**
>
> 5.The Output layer **converts** it into **word probabilities** and produces an **output
> sequence**.
>
> 6.We **take the last word of the output sequence** as the **predicted word**. That word is
> now filled into the second position of our Decoder input sequence, which now contains
> a start-of-sentence token and the first word.
>
> 7.Go back to step #3. As before, feed the new Decoder sequence into the model. Then
> **take the second word of the output and append it to the Decoder sequence**. Repeat
> this **until it predicts an end-of-sentence token**. Note that since the Encoder sequence
> does not change for each iteration, we do not have to repeat steps #1 and #2 each
> time (\\/Thanks to Michal Kučírka for pointing this out\\/).

<br>

<a id="node-jebcxlh"></a>

##### Teacher Forcing

<br>

<a id="node-rai3rd1"></a>

> [!NOTE]
> Đại khái là, cái việc ta bỏ và để model nó học từ Target sentence
> vào Decoder giống như là ta đưa đáp án cho nó để giả sử nó có
> predict một từ sai, thì từ tiếp theo sẽ vẫn được dựa trên giả định là
> những từ trước đều đúng (nhờ target sentence) giúp không bị sai
> càng sai, kiểu vậy.
>
> Và để ý cái target không chỉ đóng vai trò như thông thường nơi mà
> chỉ dùng target (hay label) trong việc tính loss function
>
> Ngoài ra còn giúp cho việc ouptut tất cả các từ cùng lúc nữa giúp
> tăng tốc quá trình rất nhiều

<br>

<a id="node-t2fzpcj"></a>

##### What are Transformers used for?

<br>

<a id="node-ymd9evr"></a>

> [!NOTE]
> Rất nhiều trong những NLP task như language model
> và text classification. Machine Translation, Text
> Summarization, Question-Answering, Named Entity
> Recognition..

<br>

<a id="node-uheza8c"></a>

- **Transformer Classification architecture**

<br>

<a id="node-ko3fj65"></a>

<p align="center"><kbd><img src="assets/ntg6lbqce5.png" width="80%"></kbd></p>

<br>

<a id="node-wjvccu8"></a>

- **Transformer Language Model architecture**

<br>

<a id="node-4eztx33"></a>

<p align="center"><kbd><img src="assets/qc2649xv6he.png" width="80%"></kbd></p>

<br>

<a id="node-7ur9xzq"></a>

> [!NOTE]
> How are they
> better than RNNs?

<br>

<a id="node-nzrmt8k"></a>

<p align="center"><kbd><img src="assets/0qdh3weg19c.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là như mr Andrew đã có nói đến, cái Transformer sẽ kết
> hợp ưu điểm của CNN trong việc sử lý cùng lúc giúp tăng tốc
> quá trình training và inference và cái Attention-based learning
> giúp nắm bắt thông tin ngữ cảnh (đại loại vậy). Khắc phục hạn
> chế của RNN (ko xử lý cùng lúc dc, CNN không xử lý thông tin
> chuỗi được)

<br>

<a id="node-k0amia3"></a>

#### Part 2 - How It Work

<br>

<a id="node-z2iaewl"></a>

##### Architecture Overview

<br>

<a id="node-bqivmtg"></a>

<p align="center"><kbd><img src="assets/11aqkb4jddi8.png" width="80%"></kbd></p>

<br>

<a id="node-yrb6ew3"></a>

> [!NOTE]
> Data inputs for both the Encoder and Decoder, which
> contains:   
> Embedding layer   
> Position Encoding layer
>
> The Encoder stack contains a number of Encoders. Each
> Encoder contains:   
> Multi-Head Attention layer   
> Feed-forward layer
>
> The Decoder stack contains a number of Decoders. Each
> Decoder contains:   
> Two Multi-Head Attention layers
> Feed-forward layer
>
> Output (top right) — generates the final output, and contains:
> Linear layer   Softmax layer.

<br>

<a id="node-q8v1fd4"></a>

##### Embedding and Position Encoding

<br>

<a id="node-kcxrwau"></a>

- **Embedding**

<br>

<a id="node-ftzcspo"></a>

<p align="center"><kbd><img src="assets/42i42eo674l.png" width="80%"></kbd></p>

> [!NOTE]
> Input sequence thì bỏ vào Input Embedding, target
> sequence thì bỏ vào Output Embedding (có tên vậy vì
> khi inference, thì ko có target sequence mà thay bằng
> chính output sequence)

<br>

<a id="node-jnuiqoz"></a>

<p align="center"><kbd><img src="assets/sv24dkykxq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái như đã biết, mỗi từ sẽ được. map với một
> numeric id dùng một vocabulary, rồi embedding layer sẽ
> map mỗi từ với một embedding vector

<br>

<a id="node-w5bgrwb"></a>

- **Position Encoding**

<br>

<a id="node-ao985j1"></a>

> [!NOTE]
> Ở đây giải thích tại sao phải có position encoding,
> đại khái là vì với cách làm không còn 'handle' từng từ
> một bỏ vào model mà sẽ 'làm' cùng lúc, dẫn đến
> không còn có thông tin về vị trí của từ trong câu nữa
> nên phải dùng cách này để bổ sung

<br>

<a id="node-xbto4rs"></a>

<p align="center"><kbd><img src="assets/k2grd7ggaul.png" width="80%"></kbd></p>

> [!NOTE]
> Các vị trí của pe vector sẽ tính theo công thức như
> sau: Số chẵn 0,2,4... thì sin, số lẻ thì cos. /
> - **pos**/ is the position of the word in the sequence /
>
>
>
> - **d_model**/ is the length of the encoding vector (same
> as the embedding vector) and /
>
>
>
> - **i**/ is the index value into this vector.

<br>

<a id="node-ztpxr2i"></a>

<p align="center"><kbd><img src="assets/j5mppknrvsm.png" width="80%"></kbd></p>

> [!NOTE]
> PE vector sẽ có cùng độ dài với word
> embedding vector là **d-model** = **encoding_size**
> **embedding_dim** = d = ...

<br>

<a id="node-hp5pglg"></a>

<p align="center"><kbd><img src="assets/2di7o6jq11r.png" width="80%"></kbd></p>

<br>

<a id="node-u68yxs0"></a>

##### Matrix Dimensions

<br>

<a id="node-o2vapzl"></a>

<p align="center"><kbd><img src="assets/p8q1qq7g4yr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái như đã nói ở trước, PE vector sẽ có độ
> dài bằng với Word Embedding vector:
> embedding_dim, và do đó mỗi một sequence được
> input vào model sẽ 'trở thành / embedded & encoded thành': 
>
>
>
> matrix word embedding và position encoding matrix có shape:
> **sequence_len** x **embedding_dim**
>
>
>
> Mở rộng hơn do nó sẽ 'handle' không phải một mà là một **batch_size**
> cái sequence nên input sẽ là: 
> Block word embedding và block position encoding đều có shape là
> **batch_size**, **sequence_len**, **embedding_dim**
>
>
>
> Block hay còn gọi là volume, tensor

<br>

<a id="node-n3oj6on"></a>

> [!NOTE]
> The (**samples, sequence length, embedding size**) shape
> produced by the Embedding and Position Encoding layers is
> preserved all through the Transformer, as the data flows
> through the Encoder and Decoder Stacks until it is reshaped
> by the final Output layers.
>
> Và cái shape như vậy sẽ được giữ xuyên
> suốt cho đến khi Output layer

<br>

<a id="node-zytsemu"></a>

<p align="center"><kbd><img src="assets/9kr4qp09m4g.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là để cho đơn giản, ta bỏ đi cái dimension
> batch_size (hay số sample) mà chỉ dùng hình vẽ như của
> 1 single sample nhưng phải hiểu là thực tế nó sẽ 'xử' một
> batch_size sample cùng lúc

<br>

<a id="node-w0apoh7"></a>

##### Encoder

<br>

<a id="node-i9ssb4l"></a>

<p align="center"><kbd><img src="assets/8no1bties77.png" width="80%"></kbd></p>

<br>

<a id="node-y6ujxat"></a>

> [!NOTE]
> The Encoder and Decoder Stacks consists of several
> (**usually six**) Encoders and Decoders respectively,
> connected sequentially.
>
> The first Encoder in the stack receives its input from the
> Embedding and Position Encoding. The other Encoders in
> the stack receive their input from the previous Encoder.
>
> Both the Self-attention and Feed-forward sub-layers, have
> a residual skip-connection around them, followed by a
> Layer-Normalization.
>
> The output of the last Encoder is fed into each Decoder in
> the Decoder Stack as explained below.

<br>

<a id="node-newnhcb"></a>

<p align="center"><kbd><img src="assets/zs5hbf2838g.png" width="80%"></kbd></p>

<br>

<a id="node-vkgz3gf"></a>

##### Decoder

<br>

<a id="node-2n5ouf7"></a>

<p align="center"><kbd><img src="assets/aruamdxxshu.png" width="80%"></kbd></p>

<br>

<a id="node-464dmuu"></a>

> [!NOTE]
> The Decoder’s structure is very similar to the Encoder’s but with a
> couple of differences.
>
> Like the Encoder, the first Decoder in the stack receives its input from
> the Output Embedding and Position Encoding. The other Decoders in
> the stack receive their input from the previous Decoder.
>
> The Decoder passes its input into a Multi-head Self-attention layer.
> This operates in a slightly different way than the one in the Encoder. It
> is only allowed to attend to earlier positions in the sequence. This is
> done by masking future positions, which we’ll talk about shortly.
>
> Unlike the Encoder, the Decoder has a second Multi-head attention
> layer, known as the Encoder-Decoder attention layer. The
> Encoder-Decoder attention layer works like Self-attention, except that
> it combines two sources of inputs — the Self-attention layer below it
> as well as the output of the Encoder stack.
>
> The Self-attention output is passed into a Feed-forward layer, which
> then sends its output upwards to the next Decoder.
>
> Each of these sub-layers, Self-attention, Encoder-Decoder attention,
> and Feed-forward, have a residual skip-connection around them,
> followed by a Layer-Normalization.

<br>

<a id="node-ahkser2"></a>

##### Attention

<br>

<a id="node-81h49wt"></a>

> [!NOTE]
> In the Transformer, Attention is used in three places:
>
> - Self-attention in the Encoder — the input sequence pays
> attention to itself
>
> - Self-attention in the Decoder — the target sequence pays
> attention to itself
>
> - Encoder-Decoder-attention in the Decoder — the target
> sequence pays attention to the input sequence
>
> ***The Attention layer takes its input in the form of three
> parameters, known as the Query, Key, and Value.**
>
> I**n the Encoder’s Self-attention, the Encoder’s input is
> passed to all three parameters, Query, Key, and Value.**
>
> Có nghĩa đại khái là 1 Attention layer nó quy định
> sẽ nhận input ở dạng 3 params là Query, Key,
> Value hiểu đại khái như **3 cái cổng để nhận
> thông tin vậy**. Và đối vối Self-Attention của
> Encoder, ta sẽ đưa cái Encoder's input (là cái
> sequence embedding/encoding block từ layer
> Embedding và Position Encoding) **vào cả ba cửa
> này** của Attention layer
>
>
>
> *Gọi Attention layer là layer con (sublayer) của
> Encoding layer

<br>

<a id="node-efyqffr"></a>

<p align="center"><kbd><img src="assets/jk5ofdr32cb.png" width="80%"></kbd></p>

<br>

<a id="node-fxw2ff4"></a>

<p align="center"><kbd><img src="assets/tnafwj0r4qs.png" width="80%"></kbd></p>

> [!NOTE]
> Ở Decoder cũng tương tự như vậy đối
> với cái Attention đầu tiên của nó, còn cái
> thứ 2 thì khác một chút:
>
>
>
> Cổng Value và Key sẽ nhận cái block out từ cái Encoder cuối cùng
> (có 6 cái encoder)
>
>
>
> Cổng Query thì nhận cái block out từ cái Self-Attention đầu tiên (sau 
> khi qua thêm cái layer norm)

<br>

<a id="node-9cb5xdp"></a>

##### Multi-head Attention

<br>

<a id="node-h68d4lv"></a>

<p align="center"><kbd><img src="assets/jt6lotrer8.png" width="80%"></kbd></p>

<br>

<a id="node-ib8jz2r"></a>

> [!NOTE]
> The Transformer calls each Attention processor an
> Attention Head and **repeats it several times in
> parallel**. This is known as Multi-head attention. It
> gives its Attention **greater power of discrimination**, by
> **combining several similar Attention calculations**.
>
> The Query, Key, and Value are each passed through
> separate **Linear layers**, each with their **own weights**,
> producing three results called **Q**, **K**, and **V**
> respectively. These are then combined together using
> the **Attention formula** as shown below, to produce the
> **Attention Score**.

<br>

<a id="node-q3t65p8"></a>

<p align="center"><kbd><img src="assets/2xhklyfv2hg.png" width="80%"></kbd></p>

> [!NOTE]
> Đây là cái đoạn mà mr Andrew lướt qua đây
>
>
>
> Có nghĩa là sau khi thông tin từ sequence Embedding/Encoding được cống
> nạp vào Attention qua ba cổng Query, Key, Value thì nó sẽ được xử lý qua ba
> sublayer của Attention (cũng như Attention  là sublayer của Encoding) để tạo
> ra Q,K,V.
>
>
>
> **Và điều quan trọng cần hiểu rằng các Linear layer này có các weight
> (param) là W_Q, W_K, W_V - sẽ được train cùng với / cũng như các
> sequence Embedding cũng được train trong quá trình training**
>
>
>
> Còn train như thế nào / mục đích gì thì nó sẽ liên quan đến 
> vai trò của Q,K,V. Đại khái là Q,K,V sẽ giúp mục đích cuối cùng là 
> "CỦNG CỐ / BỒI ĐẮP" thêm cho cái sequence embedding block
> sao cho nó mang thêm thông tin ngữ cảnh (bên cạnh thông tin nội 
> dung và vị trí)
>
>
>
> Hãy để ý, cái output của Encoder **vẫn là một embedding block có shape
> y hệt như lúc vào** (**batch_size**, **sequence_len**, **embedding_dim**)

<br>

<a id="node-yfefm9t"></a>

> [!NOTE]
> The important thing to realize here is that the Q, K, and V values **carry
> an encoded representation of each word in the sequence**. The
> Attention calculations then combine each word with every other word
> in the sequence, so that the Attention Score encodes a score for each
> word in the sequence.
>
> Cụ thể Q,K,V làm gì để trong quá trình training nó
> bồi đắp thông  tin ngữ cảnh cho embedding vector
> thì sẽ giải thích sau
>
>
>
> Nhưng để ý là nó có shape y như input embedding
> block, chẳng qua nó mang trong mình những cái gì
> đó giúp trong quá trình huấn luyện nó sẽ giúp đánh
> giá ngữ cảnh của các từ để tìm ra quan hệ giữa
> các từ trong câu. Hiểu đại khái vậy

<br>

<a id="node-9qylo2p"></a>

##### Attention Masks

<br>

<a id="node-23olgd5"></a>

<p align="center"><kbd><img src="assets/xftmhicvj4.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái Mask sẽ giúp trong lúc tính
> nó sẽ bỏ qua cái padding

<br>

<a id="node-m8w84ls"></a>

<p align="center"><kbd><img src="assets/t4g5t3qh7.png" width="80%"></kbd></p>

<br>

<a id="node-ns6f739"></a>

> [!NOTE]
> In the Decoder Self-attention: masking serves to **prevent the
> decoder from ‘peeking’ ahead at the rest of the target sentence
> when predicting the next word.** The Decoder processes words in the source sequence and
> uses them to predict the words in the destination sequence.
> During training, this is done via Teacher Forcing, where the
> complete target sequence is fed as Decoder inputs. Therefore,
> while predicting a word at a certain position, the Decoder has
> available to it the target words preceding that word as well as
> the target words following that word. This allows the Decoder to
> ‘cheat’ by using target words from future ‘time steps’. For
> instance, when predicting ‘\\/Word 3’\\/, the Decoder should refer
> only to the first 3 input words from the target but not the fourth
> word ‘\\/Ketan’\\/.

<br>

<a id="node-q55unkq"></a>

<p align="center"><kbd><img src="assets/rc4wcbyywka.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cái Mask này thì khác nó sẽ che đi cái phần
> mà chưa cần tới ví dụ đang predict từ số 3 thì không
> nên cho nó biết từ số 4,5 là gì tránh việc nó cheating
> bằng việc học thông tin từ cả những future timesteps

<br>

<a id="node-jriktvm"></a>

<p align="center"><kbd><img src="assets/t45s914qhl.png" width="80%"></kbd></p>

<br>

<a id="node-exbxl8q"></a>

> [!NOTE]
> When calculating the Attention Score (refer to the picture
> earlier showing the calculations) masking is applied to
> the numerator just before the Softmax. The masked out
> elements (white squares) are set to **negative infinity**,
> so that **Softmax turns those values to zero**.
>
> Cái này có thể bổ trợ cho việc hiểu thêm về
> khúc này của Programming assignment vốn
> chưa hiểu lắm

<br>

<a id="node-srr2do8"></a>

##### Generate Output

<br>

<a id="node-61lbp6r"></a>

<p align="center"><kbd><img src="assets/mlne4nnin8n.png" width="80%"></kbd></p>

<br>

<a id="node-bmmrwoy"></a>

> [!NOTE]
> The last Decoder in the stack passes its output to the Output
> component which converts it into the final output sentence.
>
> The Linear layer projects the Decoder vector into **Word Scores**,
> with a score value for each unique word in the target vocabulary,
> at each position in the sentence. For instance, if our final output
> sentence has 7 words and the target Spanish vocabulary has
> 10000 unique words, we generate **10000 score values** for each of
> those 7 words. The score values indicate the likelihood of
> occurrence for each word in the vocabulary in that position of the
> sentence.
>
> The **Softmax** layer then **turns those scores into probabilities** (which
> add up to 1.0). In each position, we find the index for the word with
> the **highest probability**, and then map that index to the
> corresponding word in the vocabulary. Those words then form the
> output sequence of the Transformer.
>
> Giải thích quá dể hiểu rồi, đại khái là nó sẽ output ra
> (tương ứng với mỗi từ) 1 vector có 10000 số, rồi
> softmax biến thành 10000 probability number (tổng lại
> bằng 1) từ đó ông nào có probability cao nhất sẽ là từ
> được chọn để dịch cho vị trí đó

<br>

<a id="node-uhaqmqe"></a>

> [!NOTE]
> Training and
> Loss Function

<br>

<a id="node-fvvsl9q"></a>

> [!NOTE]
> During training, we use a loss function such as **cross-entropy loss** to
> **compare** the \\_**generated output probability distribution**\\_ to the **target
> sequence**. The probability distribution gives the probability of each word
> occurring in that position.
>
> Let’s assume our target vocabulary contains just four words. Our goal is to
> produce a probability distribution that matches our expected target sequence
> “De nada END”. This means that the probability distribution for the first
> word-position should have a probability of 1 for “De” with probabilities for all
> other words in the vocabulary being 0. Similarly, “nada” and “END” should
> have a probability of 1 for the second and third word-positions respectively.
>
> As usual, the loss is used to compute gradients to train the Transformer via
> **backpropagation**.

<br>

<a id="node-2wfwd4l"></a>

<p align="center"><kbd><img src="assets/xlzaw9oabfd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là vầy, giả sử từ điển chỉ có 4 từ, thì probability vector của từ thứ
> 1 (vốn dĩ đúng phải là 'De') sẽ là như bên dưới với chỉ số probability dành
> cho 'De' cao, dù cho 'Bueno', 'Nada' cũng có nhưng thấp hơn), trong khi
> kết quả đúng phải là như bên trên với 100% dành cho 'De'.
>
>
>
> Dựa vào đó, model sẽ dùng hàm cross-entropy để tính ra loss function
> value từ đó dùng Back-Propagation để tính gradietns

<br>

<a id="node-ysuvru0"></a>

#### Part 3 - Multi-head Attentions

<br>

<a id="node-dvcgoty"></a>

> [!NOTE]
> How Attention is used in
> the Transformer

<br>

<a id="node-hhusdyp"></a>

<p align="center"><kbd><img src="assets/otvef46d0al.png" width="80%"></kbd></p>

<br>

<a id="node-4twoi1z"></a>

> [!NOTE]
> Encoder Self-Attention
>
> The input sequence is fed to the Input Embedding and
> Position Encoding, which produces an encoded
> representation for each word in the input sequence that
> captures the meaning and position of each word. This is
> fed to all three parameters, Query, Key, and Value in the
> Self-Attention in the first Encoder which then also
> produces an encoded representation for each word in
> the input sequence, that now incorporates the attention
> scores for each word as well. As this passes through all
> the Encoders in the stack, each Self-Attention module
> also adds its own attention scores into each word’s
> representation.

<br>

<a id="node-7vwicp8"></a>

<p align="center"><kbd><img src="assets/e6s875mzg9.png" width="80%"></kbd></p>

<br>

<a id="node-jjz83n2"></a>

> [!NOTE]
> Decoder Self-Attention
>
> Coming to the Decoder stack, the target sequence is fed to the
> Output Embedding and Position Encoding, which produces an
> encoded representation for each word in the target sequence
> that captures the meaning and position of each word. This is fed
> to all three parameters, Query, Key, and Value in the
> Self-Attention in the first Decoder which then also produces an
> encoded representation for each word in the target sequence,
> which now incorporates the attention scores for each word as
> well. After passing through the Layer Norm, this is fed to the
> Query parameter in the Encoder-Decoder Attention in the first
> Decoder

<br>

<a id="node-cv03q33"></a>

> [!NOTE]
> Encoder-Decoder Attention
>
> Along with that, the output of the final Encoder in the stack is passed
> to the Value and Key parameters in the Encoder-Decoder Attention.
> The Encoder-Decoder Attention is therefore getting a representation
> of both the target sequence (from the Decoder Self-Attention) and a
> representation of the input sequence (from the Encoder stack). It,
> therefore, produces a representation with the attention scores for
> each target sequence word that captures the influence of the
> attention scores from the input sequence as well. As this passes
> through all the Decoders in the stack, each Self-Attention and each
> Encoder-Decoder Attention also add their own attention scores into
> each word’s representation.

<br>

<a id="node-psmwo2f"></a>

##### Multiple Attention Heads

<br>

<a id="node-s13fymk"></a>

<p align="center"><kbd><img src="assets/e0226t7r4wo.png" width="80%"></kbd></p>

<br>

<a id="node-adlv4uv"></a>

> [!NOTE]
> n the Transformer, the Attention module repeats its
> computations multiple times in parallel. Each of these is called
> an Attention Head. The Attention module **splits its Query, Key,
> and Value parameters N-ways** and **passes each split
> independently through a separate Head**. All of these similar
> Attention calculations are then **combined together** to produce a
> **final Attention score**. This is called Multi-head attention and
> gives the Transformer greater power to encode multiple
> relationships and nuances for each word.
>
> Đại khái là nó sẽ split ba cái Query, Key, Value
> làm 8 phần (giả sử h hay N = 8 heads)
>
>
>
> Rồi mỗi phần nó sẽ xử lý bằng một head, tính
> toán đã đời, nhiều lần, cuối cùng nó gom lại làm
> kết quả cuối cùng - **final Attention score**

<br>

<a id="node-7hivej8"></a>

> [!NOTE]
> Attention
> Hyperparameters

<br>

<a id="node-rl481xn"></a>

> [!NOTE]
> - **Embedding Size** — width of the embedding vector (we use
> a width of 6 in our example). This dimension is carried
> forward throughout the Transformer model and hence is
> sometimes referred to by other names like ‘model size’ etc.
>
> - **Query Size** (equal to Key and Value size)— the size of the
> weights used by three Linear layers to produce the Query,
> Key, and Value matrices respectively (we use a Query size of
> 3 in our example)
>
> - **Number of Attention heads** (we use 2 heads in our example)
> In addition, we also have the Batch size, giving us one
> dimension for the number of samples.

<br>

<a id="node-pfc48n6"></a>

##### Input Layers

<br>

<a id="node-gok080v"></a>

<p align="center"><kbd><img src="assets/p8nynmrqi9m.png" width="80%"></kbd></p>

<br>

<a id="node-ezk9392"></a>

> [!NOTE]
> The Input Embedding and Position Encoding layers
> produce a matrix of shape (Number of Samples,
> Sequence Length, Embedding Size) which is fed to
> the Query, Key, and Value of the first Encoder in the
> stack.
>
> To make it simple to visualize, we will drop the Batch
> dimension in our pictures and focus on the
> remaining dimensions.

<br>

<a id="node-8oy7g74"></a>

<p align="center"><kbd><img src="assets/g84f65lc4if.png" width="80%"></kbd></p>

<br>

<a id="node-cwylhpy"></a>

##### Linear Layers

<br>

<a id="node-3u37jys"></a>

<p align="center"><kbd><img src="assets/49o72eebbzs.png" width="80%"></kbd></p>

<br>

<a id="node-yjpaki5"></a>

> [!NOTE]
> There are three separate Linear layers for the Query, Key,
> and Value. Each Linear layer has its own weights. The
> input is passed through these Linear layers to produce
> the Q, K, and V matrices.

<br>

<a id="node-9zgudmb"></a>

> [!NOTE]
> Splitting data across
> Attention heads

<br>

<a id="node-ddyes0o"></a>

> [!NOTE]
> However, the important thing to understand is that this is a
> **logical split only**.
>
> The Query, Key, and Value are **not physically split into
> separate matrices**, one for each Attention head. A single data
> matrix is used for the Query, Key, and Value, respectively, with
> **logically separate sections** of the matrix for each Attention
> head.
>
> Similarly, there are **not separate Linear layers**, one for each
> Attention head. All the Attention heads share the same Linear
> layer but simply operate on their ‘own’ **logical section** of the
> data matrix.
>
> Đại khái là chỉ split về logic thôi chứ vẫn chỉ có 1
> bộ Query, Key, Value tương ứng với 3 Linear thôi.
> Nó sẽ kiểu như partition (phân vùng) ra để handle
> cho mỗi Head 1 vùng

<br>

<a id="node-o9tda8z"></a>

<p align="center"><kbd><img src="assets/nclg996m4rk.png" width="80%"></kbd></p>

> [!NOTE]
> This logical split is done by partitioning the input data as well as the
> Linear layer weights uniformly across the Attention heads. We can
> achieve this by choosing the Query Size as below:
>
>
>
> Query Size = Embedding Size / Number of heads

<br>

<a id="node-re2m20k"></a>

<p align="center"><kbd><img src="assets/ll8puhbi3g.png" width="80%"></kbd></p>

> [!NOTE]
> In our example, that is why the Query Size = 6/2 = 3. Even though
> the layer weight (and input data) is a single matrix we can think of
> it as ‘**stacking together**’ the separate layer weights for each head.

<br>

<a id="node-2lfk4pd"></a>

> [!NOTE]
> The computations for all Heads can be therefore be
> achieved via a **single matrix operation** rather than requiring
> N separate operations. This makes the computations more
> **efficient** and keeps the model **simple** because fewer Linear
> layers are required, while still achieving the **power of the
> independent** Attention heads.

<br>

<a id="node-nbddnm7"></a>

> [!NOTE]
> Reshaping the Q, K,
> and V matrices

<br>

<a id="node-d26d0ei"></a>

> [!NOTE]
> The Q, K, and V matrices output by the Linear layers are
> reshaped to include an explicit Head dimension. Now each ‘slice’
> corresponds to a matrix per head.
>
> This matrix is reshaped again by swapping the Head and
> Sequence dimensions. Although the Batch dimension is not
> drawn, the dimensions of Q are now (Batch, Head, Sequence,
> Query size).

<br>

<a id="node-bto45j1"></a>

<p align="center"><kbd><img src="assets/d1yzdoyfjn.png" width="80%"></kbd></p>

<br>

<a id="node-o35q1x1"></a>

<p align="center"><kbd><img src="assets/3do6dykpugg.png" width="80%"></kbd></p>

> [!NOTE]
> In the picture below, we can see the complete process of splitting our
> example Q matrix, after coming out of the Linear layer.
>
>
>
> The final stage is for visualization only — although the Q matrix is a
> single matrix, we can think of it as a logically separate Q matrix per
> head.

<br>

<a id="node-3oq3r7w"></a>

> [!NOTE]
> Compute the Attention
> Score for each head

<br>

<a id="node-51vn7f3"></a>

<p align="center"><kbd><img src="assets/u8zbo434l7.png" width="80%"></kbd></p>

> [!NOTE]
> We now have the 3 matrices, Q, K, and V, split across the heads.
> These are used to compute the Attention Score.
>
>
>
> We will show the computations for a single head using just the last two
> dimensions (Sequence and Query size) and skip the first two
> dimensions (Batch and Head). Essentially, we can imagine that the
> computations we’re looking at are getting ‘repeated’ for each head and
> for each sample in the batch (although, obviously, they are happening
> as a single matrix operation, and not as a loop).
>
>
>
> The first step is to do a matrix multiplication between Q and K.

<br>

<a id="node-rm447up"></a>

<p align="center"><kbd><img src="assets/f0smspuala.png" width="80%"></kbd></p>

> [!NOTE]
> A Mask value is now added to the result. In the Encoder Self-attention, the
> mask is used to mask out the Padding values so that they don’t participate
> in the Attention Score.
>
>
>
> Different masks are applied in the Decoder Self-attention and in the
> Decoder Encoder-Attention which we’ll come to a little later in the flow.

<br>

<a id="node-crnci0w"></a>

<p align="center"><kbd><img src="assets/gggwrwqi8fl.png" width="80%"></kbd></p>

> [!NOTE]
> The result is now scaled by dividing by the square root of the
> Query size, and then a Softmax is applied to it.

<br>

<a id="node-4epnp73"></a>

<p align="center"><kbd><img src="assets/nfs2cbyjgl9.png" width="80%"></kbd></p>

> [!NOTE]
> Another matrix multiplication is performed between the output of the Softmax and the V matrix.

<br>

<a id="node-w9rq71m"></a>

<p align="center"><kbd><img src="assets/gqglh7y7j0h.png" width="80%"></kbd></p>

> [!NOTE]
> The complete Attention Score calculation in the Encoder
> Self-attention is as below:

<br>

<a id="node-fafso2n"></a>

> [!NOTE]
> Merge each Head’s
> Attention Scores together

<br>

<a id="node-mxy23ja"></a>

> [!NOTE]
> We now have separate Attention Scores for each head, which need to
> be combined together into a single score. This Merge operation is
> essentially the reverse of the Split operation.
>
> It is done by simply reshaping the result matrix to eliminate the Head
> dimension. The steps are:
>
> Reshape the Attention Score matrix by swapping the Head and
> Sequence dimensions. In other words, the matrix shape goes from
> (Batch, Head, Sequence, Query size) to (Batch, Sequence, Head,
> Query size). Collapse the Head dimension by reshaping to (Batch,
> Sequence, Head * Query size). This effectively concatenates the
> Attention Score vectors for each head into a single merged Attention
> Score. Since Embedding size =Head
> * Query size, the merged Score is (Batch, Sequence, Embedding
> size). In the picture below, we can see the complete process of
> merging for the example Score matrix.

<br>

<a id="node-2uye9zr"></a>

<p align="center"><kbd><img src="assets/kudwq2heqlc.png" width="80%"></kbd></p>

<br>

<a id="node-vctsmk8"></a>

##### End-to-end Multi-head Attention

<br>

<a id="node-m930cl2"></a>

<p align="center"><kbd><img src="assets/73o2utvcjgw.png" width="80%"></kbd></p>

> [!NOTE]
> Putting it all together, this is the end-to-end
> flow of the Multi-head Attention.

<br>

<a id="node-23q0qfi"></a>

> [!NOTE]
> Multi-head split captures
> richer interpretations

<br>

<a id="node-vvajz49"></a>

> [!NOTE]
> An Embedding vector captures the meaning of a word. In the case of
> Multi-head Attention, as we have seen, the Embedding vectors for the
> input (and target) sequence gets logically split across multiple heads.
> What is the significance of this?
>
> This means that separate sections of the Embedding can learn different
> aspects of the meanings of each word, as it relates to other words in the
> sequence. This allows the Transformer to capture richer interpretations
> of the sequence.
>
> This may not be a realistic example, but it might help to build intuition.
> For instance, one section might capture the ‘gender-ness’ (male, female,
> neuter) of a noun while another might capture the ‘cardinality’ (singular
> vs plural) of a noun. This might be important during translation because,
> in many languages, the verb that needs to be used depends on these
> factors.

<br>

<a id="node-2ey0zyi"></a>

<p align="center"><kbd><img src="assets/9vrcii3naw.png" width="80%"></kbd></p>

<br>

<a id="node-eltfxi9"></a>

> [!NOTE]
> Decoder Self-Attention
> and Masking

<br>

<a id="node-uvxz2fv"></a>

> [!NOTE]
> The Decoder Self-Attention works just like the Encoder
> Self-Attention, except that it operates on each word of the target
> sequence.

<br>

<a id="node-laac13z"></a>

<p align="center"><kbd><img src="assets/yw5k20wdug.png" width="80%"></kbd></p>

<br>

<a id="node-biw21q3"></a>

> [!NOTE]
> Decoder Encoder-Decoder
> Attention and Masking

<br>

<a id="node-ya86209"></a>

> [!NOTE]
> The Encoder-Decoder Attention takes its input from two sources.
> Therefore, unlike the Encoder Self-Attention, which computes the
> interaction between each input word with other input words, and Decoder
> Self-Attention which computes the interaction between each target word
> with other target words, the Encoder-Decoder Attention computes the
> interaction between each target word with each input word.
>
> Therefore each cell in the resulting Attention Score corresponds to the
> interaction between one Q (ie. target sequence word) with all other K (ie.
> input sequence) words and all V (ie. input sequence) words.
>
> Similarly, the Masking masks out the later words in the target output, as
> was explained in detail in the \\_second article\\_ of the series.

<br>

<a id="node-ndkce7s"></a>

<p align="center"><kbd><img src="assets/0o16igfng54.png" width="80%"></kbd></p>

<br>

<a id="node-ydwcg7u"></a>

#### Why They Work So Well

<br>

<a id="node-l12cdfn"></a>

> [!NOTE]
> How does the input sequence
> reach the Attention module

<br>

<a id="node-rw6npin"></a>

<p align="center"><kbd><img src="assets/6jhg3v3hur.png" width="80%"></kbd></p>

<br>

<a id="node-xsg6imi"></a>

> [!NOTE]
> As an example, let’s say that we’re working on an
> English-to-Spanish translation problem, where one sample
> source sequence is “The ball is blue”. The target sequence
> is “La bola es azul”.
>
> The source sequence is first passed through the
> Embedding and Position Encoding layer, which generates
> embedding vectors for each word in the sequence. The
> embedding is passed to the Encoder where it first reaches
> the Attention module.
>
> Within Attention, the embedded sequence is passed
> through three Linear layers which produce three separate
> matrices — known as the Q, K, and K. These
> are the three matrices that are used to compute the
> Attention Score.
>
> The important thing to keep in mind is that each ‘row’ of
> these matrices corresponds to one word in the source
> sequence.

<br>

<a id="node-z89dlwg"></a>

<p align="center"><kbd><img src="assets/522qot0se1.png" width="80%"></kbd></p>

<br>

<a id="node-522ywb9"></a>

> [!NOTE]
> Each input row is a word
> from the sequence

<br>

<a id="node-evy3rm0"></a>

> [!NOTE]
> The way we will understand what is going on with Attention, is by starting
> with the individual words in the source sequence, and then following
> their path as they make their way through the Transformer. In particular,
> we want to focus on what goes on inside the Attention Module.
>
> That will help us clearly see how each word in the source and target
> sequences interacts with other words in the source and target
> sequences.
>
> So as we go through this explanation, concentrate on what operations
> are being performed on each word, and how each vector maps to the
> original input word. We do not need to worry about many of the other
> details such as matrix shapes, specifics of the arithmetic calculations,
> multiple attention heads, and so on if they are not directly relevant to
> where each word is going.
>
> So to simplify the explanation and the visualization, let’s ignore the
> embedding dimension and track just the rows for each word.

<br>

<a id="node-3uga067"></a>

<p align="center"><kbd><img src="assets/mh0k5i3z1nc.png" width="80%"></kbd></p>

> [!NOTE]
> Để đơn giản, tạm thời quên đi mỗi một
> Q1, Q2, K1, K2,..là 1 embedding
> vector, cứ coi như 1 cục đi

<br>

<a id="node-ys92kkc"></a>

> [!NOTE]
> Each word goes through a series of
> learnable transformations

<br>

<a id="node-z93u9c2"></a>

> [!NOTE]
> Each such row has been generated from its corresponding
> source word by a series of transformations — embedding,
> position encoding, and linear layer.
>
> **All of those transformations are trainable operations. This
> means that the weights used in those operations are not
> pre-decided but are learned by the model in such a way that they
> produce the desired output predictions.** The key question is, how does the Transformer figure out what
> set of weights will give it the best results? Keep this point in the
> back of your mind as we will come back to it a little later.

<br>

<a id="node-f2lel21"></a>

<p align="center"><kbd><img src="assets/cjxu0g3xm1.png" width="80%"></kbd></p>

<br>

<a id="node-kzf8g56"></a>

> [!NOTE]
> Attention Score — Dot Product
> between Query and Key words

<br>

<a id="node-f9gc63z"></a>

<p align="center"><kbd><img src="assets/hsk54exexy.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hyc0guei0rr.png" width="80%"></kbd></p>

<br>

<a id="node-psuxxvb"></a>

<p align="center"><kbd><img src="assets/2tri7xbot2d.png" width="80%"></kbd></p>

> [!NOTE]
> As we can see from the formula, the first step within Attention is to do a matrix multiply
> (ie. dot product) between the Query (Q) matrix and a transpose of the Key (K) matrix.
> Watch what happens to each word.
>
>
>
> We produce an intermediate matrix (let’s call it a ‘factor’ matrix) where each cell is a
> matrix multiplication between two words.

<br>

<a id="node-9j8wg7t"></a>

<p align="center"><kbd><img src="assets/1tqb81d8q1m.png" width="80%"></kbd></p>

> [!NOTE]
> For instance, each column in the fourth row corresponds to a dot product
> between the fourth Query word with every Key word.

<br>

<a id="node-ji4z2xl"></a>

> [!NOTE]
> Attention Score — Dot Product between
> Query-Key and Value word

<br>

<a id="node-qdzqkmu"></a>

<p align="center"><kbd><img src="assets/lzluj9t0bj.png" width="80%"></kbd></p>

> [!NOTE]
> The next step is a matrix multiply between this intermediate ‘factor’ matrix and the
> Value (V) matrix, to produce the attention score that is output by the attention
> module. Here we can see that the fourth row corresponds to the fourth Query word
> matrix multiplied with all other Key and Value words.

<br>

<a id="node-wcopo6a"></a>

<p align="center"><kbd><img src="assets/x8ulzanc89.png" width="80%"></kbd></p>

> [!NOTE]
> This produces the Attention Score vector (Z) that is output by the Attention Module.
>
>
>
> The way to think about the output score is that, for each word, it is the encoded value of
> every word from the “Value” matrix, weighted by the “factor” matrix. The factor matrix is the
> dot product of the Query value for that specific word with the Key value of all words.

<br>

<a id="node-iom426l"></a>

> [!NOTE]
> What is the role of the Query,
> Key, and Value words?

<br>

<a id="node-lq9flf5"></a>

<p align="center"><kbd><img src="assets/bmkq2njf1uk.png" width="80%"></kbd></p>

> [!NOTE]
> The Query word can be interpreted as the word for which we are
> calculating Attention. The Key and Value word is the word to which we are
> paying attention ie. how relevant is that word to the Query word.

<br>

<a id="node-qofuw3c"></a>

> [!NOTE]
> For example, for the sentence, “The ball is blue”, the row for
> the word “blue” will contain the attention scores for “blue”
> with every other word. Here, “blue” is the Query word, and
> the other words are the “Key/Value”.
>
> There are other operations being performed such as a
> division and a softmax, but we can ignore them in this
> article. They just change the numeric values in the matrices
> but don’t affect the position of each word row in the matrix.
> Nor do they involve any inter-word interactions.

<br>

<a id="node-u7ywmd1"></a>

> [!NOTE]
> Dot Product tells us the
> similarity between words

<br>

<a id="node-sfrmwph"></a>

> [!NOTE]
> So we have seen that the Attention Score is capturing some
> interaction between a particular word, and every other word in the
> sentence, by doing a dot product, and then adding them up. But
> how does the matrix multiply help the Transformer determine the
> relevance between two words?
>
> To understand this, remember that the Query, Key, and Value
> rows are actually vectors with an Embedding dimension. Let’s
> zoom in on how the matrix multiplication between those vectors is
> calculated.

<br>

<a id="node-hevg4f6"></a>

<p align="center"><kbd><img src="assets/40jloq3402e.png" width="80%"></kbd></p>

<br>

<a id="node-j7jgm6l"></a>

> [!NOTE]
> When we do a dot product between two vectors, we multiply
> pairs of numbers and then sum them up.
>
> If the two paired numbers (eg. ‘a’ and ‘d’ above) are both
> positive or both negative, then the product will be positive.
> The product will increase the final summation.
>
> If one number is positive and the other negative, then the
> product will be negative. The product will reduce the final
> summation.
>
> If the product is positive, the larger the two numbers, the
> more they contribute to the final summation.
>
> This means that if the signs of the corresponding numbers in
> the two vectors are aligned, the final sum will be larger.

<br>

<a id="node-ykqt4ia"></a>

> [!NOTE]
> How does the Transformer learn the
> relevance between words?

<br>

<a id="node-s9pekjb"></a>

> [!NOTE]
> This notion of the Dot Product applies to the attention score as well. If the vectors for two words are more
> aligned, the attention score will be higher.
>
> So what is the behavior we want for the Transformer?
>
> We want the attention score to be high for two words that are relevant to each other in the sentence. And we
> want the score to be low for two words that are unrelated to one another.
>
> For example, for the sentence, “The black cat drank the milk”, the word “milk” is very relevant to “drank”,
> perhaps slightly less relevant to “cat”, and irrelevant to “black”. We want “milk” and “drank” to produce a high
> attention score, for “milk” and “cat” to produce a slightly lower score, and for “milk” and “black”, to produce a
> negligible score.
>
> This is the output we want the model to learn to produce.
>
> For this to happen, the word vectors for “milk” and “drank” must be aligned. The vectors for “milk” and “cat”
> will diverge somewhat. And they will be quite different for “milk” and “black”.
>
> Let’s go back to the point we had kept at the back of our minds — how does the Transformer figure out what
> set of weights will give it the best results?
>
> The word vectors are generated based on the word embeddings and the weights of the Linear layers.
> Therefore the Transformer can learn those embeddings, Linear weights, and so on to produce the word
> vectors as required above.
>
> In other words, it will learn those embeddings and weights in such a way that if two words in a sentence are
> relevant to each other, then their word vectors will be aligned. And hence produce a higher attention score.
> For words that are not relevant to each other, the word vectors will not be aligned and will produce a lower
> attention score.
>
> Therefore the embeddings for “milk” and “drank” will be very aligned and produce a high attention score.
> They will diverge somewhat for “milk” and “cat” to produce a slightly lower score and will be quite different for
> “milk” and “black”, to produce a low score.
>
> This then is the principle behind the Attention module.

<br>

<a id="node-3b0i2st"></a>

> [!NOTE]
> Summarizing — What makes
> the Transformer tick?

<br>

<a id="node-8lqty1q"></a>

> [!NOTE]
> The dot product between the Query and Key computes the relevance
> between each pair of words. This relevance is then used as a “factor” to
> compute a weighted sum of all the Value words. That weighted sum is output
> as the Attention Score.
>
> The Transformer learns embeddings etc, in such a way that words that are
> relevant to one another are more aligned.
>
> This is one reason for introducing the three Linear layers and making three
> versions of the input sequence, for the Query, Key, and Value. That gives the
> Attention module some more parameters that it is able to learn to tune the
> creation of the word vectors.

<br>

<a id="node-2uvjv5u"></a>

> [!NOTE]
> Encoder Self-Attention in
> the Transformer

<br>

<a id="node-s87qldl"></a>

<p align="center"><kbd><img src="assets/wm5wdjqq6u.png" width="80%"></kbd></p>

<br>

<a id="node-9rzz16b"></a>

> [!NOTE]
> Attention is used in the Transformer in three places:
>
> - Self-attention in the Encoder — the source sequence pays attention to itself
>
> - Self-attention in the Decoder — the target sequence pays attention to itself
>
> - Encoder-Decoder-attention in the Decoder — the target sequence pays
> attention to the source sequence
>
> In the Encoder Self Attention, we compute the relevance of each word in the
> source sentence to each other word in the source sentence. This happens in
> all the Encoders in the stack.

<br>

<a id="node-pial442"></a>

##### Decoder Self-Attention in the Transformer

<br>

<a id="node-ymgizln"></a>

<p align="center"><kbd><img src="assets/n9p1nqkb9ak.png" width="80%"></kbd></p>

> [!NOTE]
> Most of what we’ve just seen in the Encoder Self Attention applies to Attention in
> the Decoder as well, with a few small but significant differences.

<br>

<a id="node-cbxmoc5"></a>

<p align="center"><kbd><img src="assets/yxrkws0e52i.png" width="80%"></kbd></p>

> [!NOTE]
> In the Decoder Self Attention, we compute the
> relevance of each word in the target sentence to each
> other word in the target sentence.

<br>

<a id="node-egt8ot6"></a>

> [!NOTE]
> Encoder-Decoder Attention
> in the Transformer

<br>

<a id="node-hgh8u62"></a>

<p align="center"><kbd><img src="assets/zj7uxscb39.png" width="80%"></kbd></p>

> [!NOTE]
> In the Encoder-Decoder Attention, the Query is obtained from the target sentence
> and the Key/Value from the source sentence. Thus it computes the relevance of
> each word in the target sentence to each word in the source sentence.

<br>

<a id="node-3l3cibe"></a>

### Quiz

<br>

<a id="node-thsfju9"></a>

<p align="center"><kbd><img src="assets/j8o2s8x3k4g.png" width="80%"></kbd></p>

<br>

<a id="node-o4eul8i"></a>

<p align="center"><kbd><img src="assets/hajtl3r5cln.png" width="80%"></kbd></p>

<br>

<a id="node-daiae89"></a>

<p align="center"><kbd><img src="assets/y4j80v4ujc.png" width="80%"></kbd></p>

<br>

<a id="node-o3ayfyi"></a>

<p align="center"><kbd><img src="assets/30at7vw3vvc.png" width="80%"></kbd></p>

<br>

<a id="node-105qyr0"></a>

<p align="center"><kbd><img src="assets/bd67v8lmjbp.png" width="80%"></kbd></p>

<br>

<a id="node-0vujdd4"></a>

<p align="center"><kbd><img src="assets/bvv8d32tk69.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Q đặt ra câu hỏi, K xác định câu trả
> lời nào (từ nào) có ý nghĩa nhất / thích hợp
> nhất / V là đại diện của từ đó

<br>

<a id="node-jkvcmfz"></a>

<p align="center"><kbd><img src="assets/jnzeyy8ufo.png" width="80%"></kbd></p>

<br>

<a id="node-g2oyarr"></a>

<p align="center"><kbd><img src="assets/iawma1d18a.png" width="80%"></kbd></p>

<br>

<a id="node-fokeon5"></a>

<p align="center"><kbd><img src="assets/hy4itbx1ezc.png" width="80%"></kbd></p>

<br>

<a id="node-2u60jy9"></a>

<p align="center"><kbd><img src="assets/fxgu85nq4b.png" width="80%"></kbd></p>

<br>

<a id="node-j3n0nnq"></a>

<p align="center"><kbd><img src="assets/oh2f4ncfja7.png" width="80%"></kbd></p>

> [!NOTE]
> "Unique", not "common" Đại khái là positional encoding phải
> unique ở mỗi từ, không phải chung cho mỗi từ

<br>

<a id="node-iaw6f3g"></a>

### Programming Assignment

<br>

<a id="node-khqair7"></a>

> [!NOTE]
> Welcome to Week 4's assignment, the last assignment of Course 5
> of the Deep Learning Specialization! And congratulations on making
> it to the last assignment of the entire Deep Learning Specialization -
> you're almost done!
>
> Earlier in the course, you've implemented sequential neural
> networks such as RNNs, GRUs, and LSTMs. In this notebook you'll
> explore the Transformer architecture, a neural network that takes
> advantage of parallel processing and allows you to substantially
> speed up the training process.
>
> **After this assignment you'll be able to**:
>
> • Create \\/**positional encodings**\\/ to capture **sequential
> relationships** in data
>
> • Calculate \\/**scaled dot-product self-attention**\\/ with word
> embeddings
>
> • Implement \\/**masked multi-head attention**\\/
>
> • Build and train a\\/ Transformer model\\/

<br>

<a id="node-oyvfimp"></a>

##### Packgages

<br>

<a id="node-bqrxa9v"></a>

<p align="center"><kbd><img src="assets/l9wa1o586a.png" width="80%"></kbd></p>

<br>

<a id="node-ocntwk3"></a>

##### 1 - Positional Encoding

<br>

<a id="node-ufrz3i2"></a>

<p align="center"><kbd><img src="assets/d8s362jqurg.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với RNN thì do mình feed info vào từng từ một nên cơ bản
> nó có thông tin vị trí của các từ trong câu, còn với cái này
> (Transformer network) tất cả các từ xử lý cùng lúc nên không biết thứ
> tự của từ trong câu, positional encoding là để cung cấp thông tin này
>
> Đại khái là bằng cách dùng sin() và cos() thông tin vị trí trong positional
> encoding khiến giá trị bị khống chế trong -1 1 = nhỏ nên word
> embedding không bị distort. Đại khái vậy còn sẽ hiểu rõ hơn ở
> Ungraded Lab

<br>

<a id="node-zavhqyy"></a>

<p align="center"><kbd><img src="assets/0wv6p9wiv1oh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4v8kpj82775.png" width="80%"></kbd></p>

> [!NOTE]
> 'd' = **embedding_dimension**

<br>

<a id="node-88b3t63"></a>

##### 1.1 - Sine and Cosine Angles

<br>

<a id="node-dhvpl4c"></a>

- **Exercise 1 - get_angles**

<br>

<a id="node-yhd9cs9"></a>

<p align="center"><kbd><img src="assets/tltnt738xn.png" width="80%"></kbd></p>

<br>

<a id="node-venfi77"></a>

<p align="center"><kbd><img src="assets/mpd40gs9hpb.png" width="80%"></kbd></p>

> [!NOTE]
> d_model = encoding size = đại
> khái là độ dài của encoding /
> embedding vector = **embedding_dimension**

<br>

<a id="node-vo3tw0n"></a>

> [!NOTE]
> 1.2 - Sine and Cosine
> Positional Encodings

<br>

<a id="node-0hqi7y2"></a>

- **Exercise 2 - positional_encoding**

<br>

<a id="node-bo86c08"></a>

<p align="center"><kbd><img src="assets/y1bze9gypjh.png" width="80%"></kbd></p>

> [!NOTE]
> Tạm thời làm bằng for loop (vẫn đúng) cho qua dc phần này
> cho rồi nhưng nên quay lại làm theo kiểu được suggest để
> hiểu

<br>

<a id="node-q4lkgo9"></a>

<p align="center"><kbd><img src="assets/kv2xygwf518.png" width="80%"></kbd></p>

<br>

<a id="node-jey3hgy"></a>

<p align="center"><kbd><img src="assets/j8ksmf5nw4l.png" width="80%"></kbd></p>

<br>

<a id="node-mfg9425"></a>

<p align="center"><kbd><img src="assets/v9t44f4pqh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/fyue9z3l2nl.png" width="80%"></kbd></p>

<br>

<a id="node-0k39o0v"></a>

> [!NOTE]
> 2 - Masking
>
> There are two types of masks that are useful when building
> your Transformer network: the \\/padding mask\\/ and
> the \\/look-ahead mask\\/. Both help the softmax computation
> give the appropriate weights to the words in your input
> sentence.

<br>

<a id="node-7al5i1t"></a>

- **2.1 - Padding Mask**

<br>

<a id="node-oreclqo"></a>

<p align="center"><kbd><img src="assets/7qgqor07tot.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là khi bỏ input sequence vào (vào Transformer model) thì cần các
> sequence có cùng độ dài. Kiểu như các câu phải có cùng độ dài
>
>
>
> Để làm vậy thì câu dài quá Max-len sẽ bị truncated, câu ngắn hơn thì thêm
> zeros vào (padding)
>
>
>
> Mà làm vậy thì các zeros number sẽ ảnh hưởng đến kết quả tính toán của
> hàm softmax, nên cần dùng cái gọi là  Masking.
>
>
>
> Đại khái là nó sẽ hướng dẫn là số nào thì "tính", số nào thì "bỏ qua"
>
>
>
> Ổng làm giùm mình, chỉ cần đảm bảo hiểu làm được

<br>

<a id="node-4wojiid"></a>

<p align="center"><kbd><img src="assets/8y9qx1hql3n.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/h1xg7rqwh16.png" width="80%"></kbd></p>

<br>

<a id="node-345jb3a"></a>

<p align="center"><kbd><img src="assets/ep5qsws321.png" width="80%"></kbd></p>

<br>

<a id="node-o0vvpl1"></a>

<p align="center"><kbd><img src="assets/t0m1es4boka.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó dùng tf.math.equal với arg = 0 và
> decoder_token_ids) để tạo matrix và chỗ nào
> khác 0 thì True, = 0 thì False
>
>
>
> Sau đó nó biến True thành 1 , False thành 0 bằng tf.cast
>
>
>
> Rồi Add cái matrix đó vào để từ 2D (năm) thành 1 cái volume
> 3D (m,1,m) dùng function tf.newaxis
>
>
>
> Kiểu như dài nhiêu rộng nhiêu, giờ có thêm sâu bao nhiêu nữa

<br>

<a id="node-fgtf7jw"></a>

<p align="center"><kbd><img src="assets/md0o289awx8.png" width="80%"></kbd></p>

<br>

<a id="node-4438032"></a>

<p align="center"><kbd><img src="assets/vwe2nv1mu6.png" width="80%"></kbd></p>

> [!NOTE]
> Giải thích cái khái niệm add
> thêm 1 dimension là sao

<br>

<a id="node-7z919e9"></a>

- **2.2 - Look-ahead Mask**

<br>

<a id="node-xd9aawu"></a>

<p align="center"><kbd><img src="assets/yhienkr6z8c.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu lắm cách làm

<br>

<a id="node-lg3t56f"></a>

<p align="center"><kbd><img src="assets/bmofopy9ifp.png" width="80%"></kbd></p>

<br>

<a id="node-q8y99l4"></a>

##### 3 - Self-Attention

<br>

<a id="node-zot21by"></a>

- **Exercise 3 - scaled_dot_product_attention**

<br>

<a id="node-85a03oc"></a>

<p align="center"><kbd><img src="assets/ihcjgvcd2le.png" width="80%"></kbd></p>

<br>

<a id="node-887ossd"></a>

<p align="center"><kbd><img src="assets/5vqm8q7v78.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/j1gnk09by08.png" width="80%"></kbd></p>

> [!NOTE]
> 1. Tính Q@K.T: Dùng hàm tf.matmul và tf.transpose thôi, đơn giản
>
>
>
> (..., seq_len_q, depth) @ (..., seq_len_k, depth).T  = (..., seq_len_q,
> seq_len_k)
>
>
>
> 2. tính sqrt(dk): Cái này dk chỉ nói là dimension của matrix k, trong bài
> giảng cũng không nói rõ làm stuck chỗ này cho tới khi hỏi ChatGPT. Thì
> ra đại khái là tính như lấy shape rồi lấy cái size của dimension cuối rồi
> cát thành float. Nói tóm lại, trong hướng dẫn nó nói dimension của k tức
> là size của dimension cuối vậy tức là depth? - Đúng là depth
> Nhưng phải làm theo kiểu của ChatGPT vì đảm bao luôn đúng
> bởi access dimension cuối bằng [-1]
>
>
>
> 3. Tính cái M - mask cũng không được hướng dẫn rõ ràng
> chỉ nói: "Multiply (1. - mask) by -1e9 before applying the softmax."
> hoá ra phải tính mask = (1 - mask)* -1e9 
> Chưa hiểu tại sao.
>
>
>
> 4. Tính cái cục [QK.t/sqrt(dk)] - M rồi bỏ vào softmax: Không đến nổi
> không hiểu
>
>
>
> 5. Nhân với V: Matlmul thôi.
>
>
>
> Tóm lại stuck ở cái chỗ chưa biết dk là cái gì và mask
>
> Tìm hiểu lại Mask: Tại sao
> mask = (1 - mask) * -1e9
>
> Các matrix q,k,v có shape như vậy là sao chưa hiểu luôn
>
>
>
> ***depth** sẽ chính là **embedding_dim**

<br>

<a id="node-x8md0yv"></a>

<p align="center"><kbd><img src="assets/yi2jcl2ryz.png" width="80%"></kbd></p>

<br>

<a id="node-rte2zk6"></a>

<p align="center"><kbd><img src="assets/k47ittal31.png" width="80%"></kbd></p>

<br>

<a id="node-dhsqzqe"></a>

##### 4 - Encoder

<br>

<a id="node-pwq6cur"></a>

- **4.1 Encoder Layer**

<br>

<a id="node-wmdqecw"></a>

<p align="center"><kbd><img src="assets/30e81e9gf8j.png" width="80%"></kbd></p>

<br>

<a id="node-htbpmcj"></a>

<p align="center"><kbd><img src="assets/vpg1hwdsgtg.png" width="80%"></kbd></p>

> [!NOTE]
> Tại sao: 
> (batch_size, seq_len, **dff***(là gì))
> (batch_size, seq_len,**d_model**
>
>
>
> -> **dff** chính là 'fully connected dimension' - size của Fully Connected layer
>
>
>
> và **d_model** chính là embedding_dimension**: Size của embedded vector.**

<br>

<a id="node-qam8ms1"></a>

> [!NOTE]
> Đại khái hiểu một điểm quan trọng là
>
> Sau khi qua MHA, kết quả nó không ra liền cái embedding vector
> (hiểu đại khái là mấy cái vector A<1>,A<2>..trong hình vẽ của bài
> giảng) ..
>
> ..Nói đúng hơn là "chưa vội" lấy kết quả của M.H.A làm word
> embedding vector..
>
> ..mà những vector output sẽ bỏ vào 2 Dense layer nữa mới để nó
> học tiếp rồi mới lấy cái output từ đó làm embedding vector.

<br>

<a id="node-veghbl0"></a>

- **Exercise 4 - EncoderLayer**

<br>

<a id="node-pwh2xz6"></a>

<p align="center"><kbd><img src="assets/sqx889h7i2.png" width="80%"></kbd></p>

<br>

<a id="node-cnj8lh8"></a>

<p align="center"><kbd><img src="assets/633n3qptpw2.png" width="80%"></kbd></p>

> [!NOTE]
> Trong cái ini này thì **embedding_dim** chính là chiều dài của word
> embedded vector A<1>,A<2>.. Đọc trong doc cũng thấy args (không phải
> call argument) thì constructor của Multi-head Attention bỏ vào:
> **num_heads** = Số attention head, trong bài giảng có nói là **"h"**
> **key_dim** = **Size của each attention head for query and key**
>
>
>
> Tạm hiểu **"size of each attention head"** đại khái là **chiều dài của
> word embedding vector**

<br>

<a id="node-7gbg078"></a>

<p align="center"><kbd><img src="assets/944s4n4yp7.png" width="80%"></kbd></p>

<br>

<a id="node-n1e9tgq"></a>

<p align="center"><kbd><img src="assets/fr77krvn82l.png" width="80%"></kbd></p>

<br>

<a id="node-g04r761"></a>

<p align="center"><kbd><img src="assets/dde8gutj2hg.png" width="80%"></kbd></p>

<br>

<a id="node-c1d6wl7"></a>

<p align="center"><kbd><img src="assets/d4ehph92sfj.png" width="80%"></kbd></p>

<br>

<a id="node-lfhyzqc"></a>

<p align="center"><kbd><img src="assets/yb1xq863x.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/mkhynlqmi1.png" width="80%"></kbd></p>

> [!NOTE]
> Dù chưa hiểu như đại khái hiểu như vầyđể làm cái đoạn
> **self.mha_output = self.mha(x,x,x,mask) :** 
>
>
>
> Xem document của MultiHeadAttention thấy '**call argument**' của nó là 
> query, value, key, attention_mask,,,
>
>
>
> Trong đó query, value và key là **Tensor** với các shape:
>
>
>
> - Query: B = batch size, T , dim 
> (trong assignment hint có nói thêm T là **target sequence shape**)
>
>
>
> - Value: B, S, dim
> (trong assignment hint có nói thêm S là **ouput shape**)
>
>
>
> - Key: B, S, dim
>
>
>
> Mà x nó đã ghi sẵn là tensor of shape: 
> B - batch size, input_seq_len, fully_connected_dim
>
>
>
> **Đã nói rõ trong hint là sẽ bỏ Q, K, V vào (cùng với mask) vào 
> cái multihead attention layer mà nếu là đang compute self-attention
> thì Q, K, V bằng nhau. Vậy thì là bỏ x,x,x chứ gì nữa.**
>
> Rồi x tại sao cái dimension thứ 3 của
> x là **fully_connected_dim**?
>
>
>
> Khả năng là do để output từ mha khớp với layer tiếp sau đó
> là Fully-Connected layer
>
> Còn khúc dưới thì không đến nỗi khó quá ko làm được dù chưa thật rõ
> nhưng cứ làm theo hint

<br>

<a id="node-d5mk2z5"></a>

<p align="center"><kbd><img src="assets/m1doj76tl8b.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/na8qbgbjid.png" width="80%"></kbd></p>

> [!NOTE]
> Chỗ này mr Andrew
> hình như đã ghi sai shape

<br>

<a id="node-fncnnyw"></a>

- **4.2 - Full Encoder**

<br>

<a id="node-cgcuqn6"></a>

<p align="center"><kbd><img src="assets/hsb25uibmb.png" width="80%"></kbd></p>

<br>

<a id="node-wlknpjk"></a>

- **Exercise 5 - Encoder**

<br>

<a id="node-d3bwrcl"></a>

<p align="center"><kbd><img src="assets/o20nds7781.png" width="80%"></kbd></p>

<br>

<a id="node-vtvm8zw"></a>

<p align="center"><kbd><img src="assets/ab14nkhqfs8.png" width="80%"></kbd></p>

<br>

<a id="node-nvxlrgw"></a>

> [!NOTE]
> Giải thích dòng: **self.embedding = Embedding(input_vocab_size, self.embedding_dim)** 
>
> mà lúc call nó biến x từ:
>
> x  -- Tensor of shape (batch_size, input_seq_len)
>
> để thành ra:
>
> x = self.embedding(x)  # (batch_size, input_seq_len, **embedding_dim**)
>
> --> Đại khái là bước này define một Embedding layer, bài trước ta đã
> làm (Embedding), nhưng ở đó mình dùng một pre-trained word
> embedding matrix để define ra Embedding layer và set cho nó trainable
> = False.
>
> Còn bây giờ, đại khái là ta chỉ define nó trong 'hệ thống' và khi 'train' nó
> sẽ train luôn cái Embedding layer's weights = Đồng nghĩa nó sẽ tìm
> weights sao cho Embedding layer sẽ có thể tạo ra các word embedding
> vector đại diện tốt cho từ (nắm bắt được các tính chất của từ đó)
>
> - Có thể confuse một chút là cái Self-Attention cũng tìm cách tạo các
> vector A<> đại diện cho từ sao cho nó nắm bắt ngữ cảnh của từ trong
> câu thì kệ nó cứ hiểu đại khái là cái (step) nào cũng có tác dụng của nó
> -> Không có gì confuse sâu khi đọc 4 articles của **Ketan Doshi,** ta hiểu rằng
> Self Attention layer sẽ 'add' thêm vào các embedding vector này các thông
> tin 'ngữ cảnh', tức **dimension của vector embedded vẫn vậy**, chỉ là được kiểu
> như là bồi đắp thêm/củng cố thêm thôi.

<br>

<a id="node-7vptaod"></a>

<p align="center"><kbd><img src="assets/21h27cc5b2p.png" width="80%"></kbd></p>

> [!NOTE]
> Embedding layer trong document arg  \\/**input_dim**\\/: "Integer. Size of the
> vocabulary",  **output_dim**: Integer. Dimension of the dense embedding
>
> và
>
> Input shape 2D tensor with shape: (batch_size, **input_length**).
>
> Output shape 3D tensor with shape: (batch_size, **input_length**,
> **output_dim**).
>
> Hiểu đại khái là đưa **input dim** là max của số lượng các từ cần embedded
> vậy không "liên quan" đến **input_length !???**
>
> Nên khi define ở bài trước thì Embedding(vocab_size, embedding_dim) bài
> này thì Embedding (input_vacab_size, embedding_dim) Còn khi 'chạy' ta đưa
> vào một câu dài 10 thì input_length =10
> - Input là tensor (batch_size, 10) thì nó cho ra
> - output là batch_size, 10, 50)
>
> Hiểu đại khái là đưa input dim là max của số
> lượng các từ cần embedded vậy không "liên
> quan" đến input_length Không biết hiểu vậy có
> đúng không!??? Quay lại sau

<br>

<a id="node-qxg98q0"></a>

<p align="center"><kbd><img src="assets/sswzfu5qda.png" width="80%"></kbd></p>

<br>

<a id="node-mmajyyk"></a>

> [!NOTE]
> Giải thích dòng self.pos_encoding = positional_encoding(max..., **embedding_dim**)
>
> Thì đại khái là sau loạt bài của **Ketan**, ta hiểu (rõ hơn) rằng một data instance 
> (một sequence - hay một câu đi cho rõ) hoặc nhiều (một số lượng batch_size)
> các sequence sẽ được trải qua quá trình xử lý như sau:
>
> a. Đuợc embedded (trong Keras như bài asigment này thì chính là bước Embedding
> layer ở trên) -> Tức là quá trình mỗi một từ trong sequence (câu) sẽ được biến
> thành một embedding vector có độ dài là **embedding_dim.** Cái này đã nói ở trên 
>
> b. Cùng lúc đó, một cách ngắn gọn giải thích lại câu chuyện là tại vì không như RNN
> mà ở đó ta đưa vào từng từ để learn nên có sẵn thông tin **vị trí**, bây giờ với Transformer
> cách làm kết hợp lợi điểm của CNN là xử lý **CÙNG LÚC** và tuyệt chiêu **attention-based 
> t**hì lại **không còn thông tin vị trí** nên phải dùng **kĩ thuật Positional Encoding** để bổ
> sung thông tin này, tạm giải thích gọn vậy thôi.
>
> Vậy thì thông tin của positional encoding này sẽ có cùng shape với embedding vector
> tức là cũng batch_size, sequence_length, embedding_size.
> Mà điều có thể gây confuse là mr Andrew hình như không nói rõ trong bài giảng và trong
> các function như positional_encoding thì dùng chữ **d / d_model** (trong test_function)
> rằng cái positional encoding vector và word embedding vector đều có dimension là
> **embedding_dim.** 
> *Sẵn tiện trong loạt bài của Ketan cũng cho biết **embedding_dim** là constant dùng 
> xuyên suốt nên còn được gọi là **d_model** giống như dimension của model vậy.
> Cái này cũng giải thích bối rối **d-model** ở define **FullyConnected** (theo link mà xem)
>
> Để kết lại phải nói thêm là cái **positional_encoding** block sẽ được **CỘNG** với **word
> embedding** block vì cùng size mà (batch, seq_len, emb_dim) trước khi bỏ vào Encoder
> Câu này giải thích luôn cho dòng **x += self.pos_encoding** của call()
> Còn cụ thể tại sao gọi (:,:sequence_len,:) thì chưa hiểu lắm

<br>

<a id="node-pzc3rq8"></a>

> [!NOTE]
> Giải thích dòng:
> self.enc_layers = [EncoderLayer(embedding_dim=self.embedding_dim,
>                                         num_heads=num_heads,
>                                         fully_connected_dim=fully_connected_dim,
>                                         dropout_rate=dropout_rate,
>                                         layernorm_eps=layernorm_eps) 
>                            **for _ in range(self.num_layers)]**
>
> Đại khái là nó tạo 1 list có **num_layers cái** EncoderLayer object 
> Các argument như thế này là define theo required của function **__ini__()** 
> trong **EncoderLayer** class
>
> Sau khi đọc loạt bài của Ketan, ta hiểu rằng người ta cho thông tin 'chạy qua'
> một vài Encode, mà trong loạt bài của Ketan là 6 cái. Đừng lầm lẫn với 
> Multi-head gì ở đây vốn là mỗi một Encoder chứa 1 cái Multi-head Attention
> Và như vậy cứ **out của thằng (Encoder) trước là input của thằng sau** thôi.
> Nên trong function call() mr Andrew làm vậy trong for-loop num_layers  
>
> Cái input của Encoder sẽ là cái volume các embedding vector có shape như sau
> (**batch_size**, **seq_len**, **emb_dim**)
>
> Kiểu như: 
> - Có B - **batch_size** sample (sample là 1 câu đó), 
> - Mỗi sample /câu có **sequence_len** từ
> - Mỗi từ là một embedding vector có size là **embedding_dim**

<br>

<a id="node-kpwnwu9"></a>

<p align="center"><kbd><img src="assets/bi2utygw506.png" width="80%"></kbd></p>

<br>

<a id="node-jg23or9"></a>

##### 5 - Decoder

<br>

<a id="node-wxt44q5"></a>

- **5.1 - Decoder Layer**

<br>

<a id="node-aze5mco"></a>

<p align="center"><kbd><img src="assets/m8op144a8vl.png" width="80%"></kbd></p>

<br>

<a id="node-efi9gtx"></a>

<p align="center"><kbd><img src="assets/ztdctip3jlg.png" width="80%"></kbd></p>

<br>

<a id="node-acoxqr1"></a>

- **Exercise 6 - DecoderLayer**

<br>

<a id="node-ggz4lg0"></a>

<p align="center"><kbd><img src="assets/4wewlthpv1w.png" width="80%"></kbd></p>

<br>

<a id="node-bfccx8i"></a>

<p align="center"><kbd><img src="assets/dy5qdrkzt6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/5ybk6ts2gz.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/pqvgeq6h23g.png" width="80%"></kbd></p>

<br>

<a id="node-ziv2et3"></a>

> [!NOTE]
> Chỗ này mr Andrew hình như đã nhầm khi mà ghi rằng:  **x** là tensor và
> **enc_output** là shape: (batch_size, target_seq_len, **full_connected_dim là
> đâu đúng? phải là embedding_dim chứ)** Mà ở Encoder ổng cũng ghi là output là batch_size, sequence_len, **embedding_dim**  Và output sau mha1 cũng là batch_size, sequence_len, **d_model** =  **embedding_dim
> Nói chung có thể chỗ nào là fully_connected_dim đều phải sửa là embedding_dim** Vì Theo loạt bài của Ketan thì sequence embedding sẽ giữ nguyên shape là
> **batch_size**, **sequence_len**, **embedding_dim** xuyên suốt

<br>

<a id="node-fbllwym"></a>

<p align="center"><kbd><img src="assets/wl8orpavui.png" width="80%"></kbd></p>

> [!NOTE]
> Chỗ này mr Andrew
> hình như đã ghi sai shape

<br>

<a id="node-8siawo2"></a>

<p align="center"><kbd><img src="assets/pglm3rlwbpq.png" width="80%"></kbd></p>

<br>

<a id="node-oteu8g9"></a>

- **5.2 - Full Decoder**

<br>

<a id="node-s7q2jty"></a>

<p align="center"><kbd><img src="assets/7mfcrwk78f9.png" width="80%"></kbd></p>

<br>

<a id="node-hn41t73"></a>

- **Exercise 7 - Decoder**

<br>

<a id="node-iacp1f6"></a>

<p align="center"><kbd><img src="assets/nb4wvfjf85g.png" width="80%"></kbd></p>

<br>

<a id="node-9t49dkf"></a>

<p align="center"><kbd><img src="assets/a1wttq2wghq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/b6w6v5f7a0c.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/uxpmdsh67n.png" width="80%"></kbd></p>

<br>

<a id="node-sp4bq8f"></a>

<p align="center"><kbd><img src="assets/f4rrz7mbt7v.png" width="80%"></kbd></p>

> [!NOTE]
> Chỗ này mr Andrew
> hình như đã ghi sai shape

<br>

<a id="node-2y0xo44"></a>

##### 6 - Transformer

<br>

<a id="node-7yzmbgf"></a>

- **Exercise 8 - Transformer**

<br>

<a id="node-kzjyv3q"></a>

<p align="center"><kbd><img src="assets/zaa7z6b937j.png" width="80%"></kbd></p>

<br>

<a id="node-y1nvhik"></a>

<p align="center"><kbd><img src="assets/ktvw03gdbvg.png" width="80%"></kbd></p>

<br>

<a id="node-4xxybkj"></a>

<p align="center"><kbd><img src="assets/4pgrnczcxvd.png" width="80%"></kbd></p>

<br>

<a id="node-ow19d25"></a>

<p align="center"><kbd><img src="assets/oe5zjog1qvl.png" width="80%"></kbd></p>

<br>

<a id="node-loz7zon"></a>

<p align="center"><kbd><img src="assets/1dte4sqr01x.png" width="80%"></kbd></p>

> [!NOTE]
> Chỗ này mr Andrew
> hình như đã ghi sai shape

<br>

<a id="node-xc47td6"></a>

> [!NOTE]
> **Conclusion** You've come to the end of the graded portion of the assignment. By now, you've:
>  • Created positional encodings to capture sequential relationships in data
>  • Calculated scaled dot-product self-attention with word embeddings
>  • Implemented masked multi-head attention
>  • Built and trained a Transformer model
>
> **What you should remember**:
>  • The combination of self-attention and convolutional network layers allows of parallelization of training and \\/faster training\\/.
>  • Self-attention is calculated using the generated query Q, key K, and value V matrices.
>  • Adding positional encoding to word embeddings is an effective way to include sequence information in self-attention calculations.
>  • Multi-head attention can help detect multiple features in your sentence.
>  • Masking stops the model from 'looking ahead' during training, or weighting zeroes too mu

<br>

<a id="node-dttw0kr"></a>

##### 7 - References

<br>

<a id="node-c973iie"></a>

<p align="center"><kbd><img src="assets/6jd0wh7wnzn.png" width="80%"></kbd></p>

<br>

<a id="node-u7tmzm1"></a>

## Transformer Applications - Ungraded Labs

<br>

<a id="node-j7ps31i"></a>

### Tranformer Pre-processing

<br>

<a id="node-9avur7q"></a>

> [!NOTE]
> Welcome to Week 4's first ungraded lab. In this notebook you
> will delve into the pre-processing methods you apply to raw text
> to before passing it to the encoder and decoder blocks of the
> transformer architecture.

<br>

<a id="node-tkl47to"></a>

##### Packages

<br>

<a id="node-uo7eshu"></a>

> [!NOTE]
> import tensorflow as tf
> import numpy as np
> import matplotlib.pyplot as plt
> import os
>
> from tensorflow.keras.layers import **Embedding**
> from tensorflow.keras.preprocessing.text import **Tokenizer**
> from tensorflow.keras.preprocessing.sequence import **pad_sequences**

<br>

<a id="node-or32rns"></a>

##### 1 - Positional Encoding

<br>

<a id="node-4fn8y73"></a>

<p align="center"><kbd><img src="assets/7kuanqq20px.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cái sequence embedding output tổng hợp bởi word embedding
> và position encoding chỉ là những con số, khó lòng hình dung được ý
> nghĩa của nó nhưng bằng cách plot nó trên Cartesian plane thì có thể giúp
> nhận thấy rằng từ mà gần nhau trong câu thì sẽ gần nhau trên plot

<br>

<a id="node-7qcszrk"></a>

##### 1.1 - Positional encoding visualizations

<br>

<a id="node-2dci5el"></a>

<p align="center"><kbd><img src="assets/tgd5fdkr75.png" width="80%"></kbd></p>

<br>

<a id="node-f26amd8"></a>

<p align="center"><kbd><img src="assets/adntw939rra.png" width="80%"></kbd></p>

<br>

<a id="node-b6mj04q"></a>

<p align="center"><kbd><img src="assets/erxb256hj2v.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là có 2 tính chất quan trọng đó là:
>
>
>
> 1. Tất cả các position encoding vector đều có norm bằng nhau dẫn
> đến một kết luận là dot product của 2 vector nay **sẽ không bị ảnh
> hưởng bởi the scale của vector** và do đó đây sẽ là một đặc điểm
> quan trọng trong việc tính toán sự liên quan của các  từ với nhau
>
>
>
> 2. **Sự khác biệt** của 2 vector bất kì miễn là pos c**ùng cách nhau k thì
> đều giống nhau** dù pos có thay đổi ra sao.

<br>

<a id="node-cno212f"></a>

> [!NOTE]
> 1.2 - Comparing positional encodings
>
> Nói chung là dùng visualization để
> check positional encodinga

<br>

<a id="node-7thjywk"></a>

- **1.2.1 Correlation**

<br>

<a id="node-jilo2jt"></a>

<p align="center"><kbd><img src="assets/2d3rowctcf4.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, việc các pe vector khác biệt nhau chưa nói lên điều gì, plot
> matrix các chỉ số correlation của mỗi vector với từng vector ở vị trí khác
> sẽ thấy nếu encoding tốt thì nó phải có dạng đối xứng qua đường chéo
> với đường chéo cao nhất (bản thân mỗi thằng giống chính nó nhất) càng
> xa đường chéo càng giảm

<br>

<a id="node-vp2py2b"></a>

- **1.2.2 Euclidean distance**

<br>

<a id="node-1r8jqwl"></a>

<p align="center"><kbd><img src="assets/trc1srhi2t.png" width="80%"></kbd></p>

> [!NOTE]
> Ngược lại thay vì dùng 'độ giống' (correlation) thì dùng ' độ khác' -
> Euclidean distance thì cũng sẽ thấy dạng đối xứng, càng xa đường chéo
> càng tăng - càng xa nhau càng khác nhau nhiều

<br>

<a id="node-2awnaa9"></a>

##### 2 - Semantic embedding

<br>

<a id="node-l6a8gz3"></a>

> [!NOTE]
> You have gained insight into the **relationship
> positional encoding vectors have with other vectors**
> at different positions by creating correlation and
> distance matrices. Similarly, you can gain a stronger
> intuition as to **how positional encodings affect word
> embeddings** by visualizing the sum of these vectors.

<br>

<a id="node-1pfj7yx"></a>

##### 2.1 - Load pretrained embedding

<br>

<a id="node-avob69w"></a>

<p align="center"><kbd><img src="assets/refau97f5lo.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là load pre-trained embedding vector from Glove project,
> mỗi vector có 100 features tức embedding_dim = 100

<br>

<a id="node-mlo2vri"></a>

<p align="center"><kbd><img src="assets/abqpwsmaff5.png" width="80%"></kbd></p>

> [!NOTE]
> Ổng tạo 2 câu với các cặp từ 'gần nhau' - gần nhau vì ngữ nghĩa, tính
> chất gần nhau thể hiện bởi embedding vector và 1 câu thì để cặp từ
> gần nhau thì sát nhau, 1 câu để lộn xộn

<br>

<a id="node-31psj99"></a>

<p align="center"><kbd><img src="assets/bcb41khp5sb.png" width="80%"></kbd></p>

> [!NOTE]
> Khúc này ổng nói đại khái là tạm thời có thể lướt qua vì sẽ giải thích kĩ hơn
> sau, nhưng đại khái là cách 1 text có nhiều câu với độ dài ngắn khác nhau
> được tokenize và padding như thế nào trước khi bỏ vào Embedding layer để
> tạo embedding vectors
>
>
>
> Cụ thể là cứ **mỗi câu sẽ trở thành một array**, **độ dài fixed** bởi một  const
> MAX_SEQUENCE_LEN, nên câu **ngắn quá thì dc padding** bởi 0, **dài quá
> thì bị truncated**.
>
>
>
> Rồi trong array thì **mỗi số là index của từ** trong một **dictionary**, vậy thôi

<br>

<a id="node-1qfg7kj"></a>

<p align="center"><kbd><img src="assets/bwkqqsz8kr.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại khái là ổng dùng cái pre-trained embedding vectors từ Glove
> project để tạo một cái Embedding layer nhưng để đơn giản thỉ bỏ hết chỉ giữ
> nhưng vector của các từ có trong câu và không phải từ nào trong câu cũng
> chắc chắn có trong cái pre-trained nên sẽ fill bằng 0
>
>
>
> Khúc cuối, sau khi embedding, thì xem shape thấy 2,100 (2 câu, mỗi câu 100
> token), đã trở thành 2,100,100 (2 câu, mỗi câu 100 vector, mỗi vector 100 số)

<br>

<a id="node-9cyxclf"></a>

##### 2.2 - Visualization on a Cartesian plane

<br>

<a id="node-zoci806"></a>

<p align="center"><kbd><img src="assets/tem6umny9np.png" width="80%"></kbd></p>

> [!NOTE]
> Này đại khái là plot các embedding vector lên Cartesian plane (sau khi
> đã PCA từ 100D còn 2D) thì thể hiện rõ các từ gần nhau sẽ ..gần
> nhau.

<br>

<a id="node-rxdkcth"></a>

<p align="center"><kbd><img src="assets/tqjq3shhn8c.png" width="80%"></kbd></p>

<br>

<a id="node-0im2uys"></a>

<p align="center"><kbd><img src="assets/w66cf677i5.png" width="80%"></kbd></p>

<br>

<a id="node-fe2xxu3"></a>

> [!NOTE]
> 3 - Semantic and positional embedding
>
> Đại khái là với sự kết hợp với Positional Encoding (với trọng số
> nào đó) thì yếu tố 'vị trí trong câu' của các từ bắt đầu tạo ảnh
> hưởng (đến embedding vector - nói ở đây chỉ tổng của cả word
> embedding hay còn gọi là semantic embedding và positional
> encoding). Cụ thể là từ gần nhau trong câu bắt đầu xích lại gần
> nhau trên Cartesian plane hơn, như red, wolf - đứng sát nhau
> trong câu, dù semantic nó xa nhau
>
> Nếu thay đổi trọng số, thì ảnh hưởng của pe vào embedding
> tổng cũng giảm dần

<br>

<a id="node-626fz99"></a>

<p align="center"><kbd><img src="assets/fg44z9b7mzk.png" width="80%"></kbd></p>

<br>

<a id="node-unayw2l"></a>

<p align="center"><kbd><img src="assets/ozbmy9i1hld.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với sự kết hợp với Positional Encoding (với trọng số nào
> đó) thì yếu tố 'vị trí trong câu' của các từ bắt đầu tạo ảnh hưởng (đến
> embedding vector - nói ở đây chỉ tổng của cả word embedding hay
> còn gọi là semantic embedding và positional encoding). Cụ thể là từ
> gần nhau trong câu bắt đầu xích lại gần nhau trên Cartesian plane
> hơn, như red, wolf - đứng sát nhau trong câu, dù semantic nó xa nhau

<br>

<a id="node-42rja3t"></a>

<p align="center"><kbd><img src="assets/o6gcif9s3ok.png" width="80%"></kbd></p>

<br>

<a id="node-zx2y65a"></a>

<p align="center"><kbd><img src="assets/nzj58xbakr9.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu thay đổi trọng số, thì ảnh hưởng của pe vào embedding tổng cũng giảm
> dần

<br>

<a id="node-4wii9kd"></a>

> [!NOTE]
> **What you should remember**:
>
> • Positional encodings can be expressed as linear
> functions of each other, which allow the model to
> learn according to the relative positions of words.
>
> • Positional encodings can affect the word
> embeddings, but if the relative weight of the
> positional encoding is small, the sum will retain the
> semantic meaning of the words.

<br>

<a id="node-y5l3vbm"></a>

> [!NOTE]
> TRANSFORMER NETWORK APPLICATION:
> NAMED-ENTITY RECONITION

<br>

<a id="node-27hndm2"></a>

> [!NOTE]
> 1. Use tokenizers and pre-trained models from the
> HuggingFace Library.
>
> 2. Fine-tune a pre-trained transformer model for
> Named-Entity Recognition

<br>

<a id="node-d9ljozp"></a>

##### Packages

<br>

<a id="node-dz7nnzw"></a>

<p align="center"><kbd><img src="assets/26gjgt3ram6.png" width="80%"></kbd></p>

<br>

<a id="node-w79y5yj"></a>

> [!NOTE]
> 1 - Named-Entity Recogniton
> to Process Resumes

<br>

<a id="node-z3vgtpt"></a>

> [!NOTE]
> When faced with a large amount of unstructured text data, named-entity
> recognition (NER) can help you detect and classify important information
> in your dataset. For instance, in the running example "Jane vists Africa in
> September", NER would help you detect "Jane", "Africa", and "September"
> as named-entities and classify them as person, location, and time.
>
> - You will use a variation of the Transformer model you built in the last
> assignment to **process a large dataset of resumes**.
>
> - You will find and **classify relevant information** such as the companies the
> applicant worked at, skills, type of degree, etc.
>
> Đại khái là (ứng dụng NER) xử lý một tập resumes data lớn
> để lấy những thông tin quan trọng từ các candidates

<br>

<a id="node-1pky7o4"></a>

##### 1.1 - Data Cleaning

<br>

<a id="node-6hhozsk"></a>

> [!NOTE]
> Cái này ổng làm một loạt xem qua các function
>
> Khúc đầu đại khái là chuẩn bị một số function để giúp lấy dữ liệu
> **get_entities**()... Mấy cái này nhờ CHatGPT sẽ có thể hiểu sau
>
> - **convert_dataturks_to_spacy**: Hiểu đại khái là convert gì đó
>
> - **trim_entity_spans**: Removes leading and trailing white spaces
> from entity spans -> Hiểu đại khái là trim
>
> Chưa hiểu cụ thể

<br>

<a id="node-0ut6x80"></a>

##### 1.2 - Padding and Generating Tags

<br>

<a id="node-judgoyh"></a>

<p align="center"><kbd><img src="assets/ayowin48u36.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu nó làm gì nhưng đại khái là lấy ra xem có những tag gì
>
> Chưa hiểu cụ thể

<br>

<a id="node-7ja9g9a"></a>

<p align="center"><kbd><img src="assets/3ao2e3a8v3v.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu cụ thể

<br>

<a id="node-0qvemdf"></a>

##### 1.3 - Tokenize and Align Labels with 🤗 Library

<br>

<a id="node-cdwt0wz"></a>

<p align="center"><kbd><img src="assets/k8cwg2tyyif.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu cụ thể
>
> Đại khái là kiểu như phải tokenize cái input trước khi bỏ vào Transformer model,
> và thường dùng 1 cái Transformer tokenizer (kiểu như thư viện) nên phải đảm
> bảo cái thằng tokenizer với Transformer model phải 'hợp' nhau. (Type phải match
> nhau)

<br>

<a id="node-zob6gjp"></a>

##### Exercise 1 - tokenize_and_align_labels

<br>

<a id="node-icz92bh"></a>

<p align="center"><kbd><img src="assets/2j22vvrj4mo.png" width="80%"></kbd></p>

> [!NOTE]
> Ok thì đại khái là cái kiểu của thằng Distill..tokenizer này là nó làm cái kiểu bẻ 1
> từ ra thành nhiều subword để tokenize, nên để không bị kiểu như 'lệch'
> (misalignment) với các tags ban đầu thì gán như vầy: Bẻ ra thì cái đầu gán
> bằng (index) cái cũ, còn mấy cái sau thì gán =-100. Cái special token cũng gán
> -100 luôn.

<br>

<a id="node-rhvc7n6"></a>

<p align="center"><kbd><img src="assets/kz8f0nvn7xs.png" width="80%"></kbd></p>

> [!NOTE]
> Sau khi tokenize xong giờ mới tạo train/test set đây

<br>

<a id="node-qaagl5p"></a>

##### 1.4 - Optimization

<br>

<a id="node-iilkgck"></a>

<p align="center"><kbd><img src="assets/ftxs96fy9vs.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dùng cái Transformer model tên là
> **TFDistilBertForTokenClassification**
>
>
>
> Và nó cũng là **pre-trained model** luôn (thể hiện bởi **from_pretrained**) -
> đại khái giống như họ (**HuggingFace library)** có sẵn những pre-trained
> model để sẵn vậy) ta sẽ load về và **fine-tune** thêm nên mới gọi phần này là
> optimization

<br>

<a id="node-yu3v95f"></a>

<p align="center"><kbd><img src="assets/dj8rd0mczys.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thử 1 text mới, tokenize nó, rồi bỏ vào model predict thử ở đây cái
> **model(inputs).logits hình như chỉ số probability** rồi lấy **argmax để lấy ra
> prediction**
>
> Cần confirm lại: logits

<br>

<a id="node-ae82iyu"></a>

<p align="center"><kbd><img src="assets/gzz5udzia58.png" width="80%"></kbd></p>

> [!NOTE]
> Xem model(input)

<br>

<a id="node-vfcqqm9"></a>

<p align="center"><kbd><img src="assets/25kwsjvnqrn.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này cài thêm cái **Sequeval** chưa hiểu để tác dụng gì
> Nhưng có thể để đọc **value** của **sequence** chăng

<br>

<a id="node-9v6cvfi"></a>

<p align="center"><kbd><img src="assets/mi3itzozey.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này đại khái là predict lại toàn bộ train set

<br>

<a id="node-fe3ih78"></a>

<p align="center"><kbd><img src="assets/6six7jr3sob.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/k0mfri76sfl.png" width="80%"></kbd></p>

> [!NOTE]
> Vẽ thử ra xem và chi tiết thì thấy **TRUE LABEL** 1035 cái name, location 116, ,,,,

<br>

<a id="node-mn7acdf"></a>

<p align="center"><kbd><img src="assets/yqp95zqno0c.png" width="80%"></kbd></p>

> [!NOTE]
> So với Prediction

<br>

<a id="node-0hmb0kr"></a>

<p align="center"><kbd><img src="assets/1edlg12k67o.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng là xem các thông số để
> evaluate: precision, recall, f1-score

<br>

<a id="node-otqjd90"></a>

> [!NOTE]
> Congratulations!
>
> Here's what you should remember:
>
> - Named-entity recognition (NER) detects and classifies
> named-entities, and can help process resumes, customer reviews,
> browsing histories, etc.
> - You must preprocess text data with the corresponding tokenizer to
> the pretrained model before feeding your input into your Transformer
> model.

<br>

<a id="node-zv9iw6o"></a>

> [!NOTE]
> TRANSFORMER NETWORK
> APPLICATION: QUESTION ANSWERING

<br>

<a id="node-hj2mnkp"></a>

> [!NOTE]
> Welcome to Week 4's third, and the last lab of the course!
> Congratulations on making it this far. In this notebook you'll
> explore another application of the transformer architecture that
> you built.
>
> After this assignment you'll be able to:
>
> - Perform extractive Question Answering
>
> - Fine-tune a pre-trained transformer model to a custom dataset
>
> - Implement a QA model in TensorFlow and PyTorch

<br>

<a id="node-fqyj2f4"></a>

##### 1 - Extractive Question Answering

<br>

<a id="node-yo6j9om"></a>

> [!NOTE]
> Question answering (QA) is a task of natural language processing
> that aims to automatically answer questions. The goal
> of \\/extractive\\/ QA is to identify the portion of the text that contains
> the answer to a question. For example, when tasked with answering
> the question 'When will Jane go to Africa?' given the text data 'Jane
> visits Africa in September', the question answering model will
> highlight ' September'.
>
> • You will use a variation of the Transformer model you built in the
> last assignment to answer questions about stories.
>
> • You will implement extractive QA model in TensorFlow and in
> PyTorch.  **Recommendation:**
>
> • If you are interested, check out the \\_Course 4: Natural Language
> Processing with Attention Models\\_ of our \\_Natural Language
> Processing Specialization\\_ where you can learn how to build
> Transformers and perform QA using the \\_Trax\\_ library.
>
> extractive QA có mục đích là dùng train AI
> model sao cho đại khái là cho một story rồi hỏi
> lại những chi tiết của story đó

<br>

<a id="node-5reesty"></a>

- **1.1 - Data Cleaning**

<br>

<a id="node-omqqe61"></a>

<p align="center"><kbd><img src="assets/hthsejvbuy.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là mỗi câu hỏi entry nó có 3 text hai câu đầu là context, câu
> cuối là câu hỏi.Và cái supporting ids là ids của câu giúp trả lời câu hỏi

<br>

<a id="node-c9w3mrn"></a>

<p align="center"><kbd><img src="assets/duv2xwj5y7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó loop qua hết và bỏ type_set vào set, check thử chỉ
> có 1 loại là [0,0,1] có nghĩa là mọi dataset đều có format như vậy

<br>

<a id="node-zou02bx"></a>

<p align="center"><kbd><img src="assets/ebb8ho8szp7.png" width="80%"></kbd></p>

<br>

<a id="node-6x73qbd"></a>

<p align="center"><kbd><img src="assets/5fynpoj9md8.png" width="80%"></kbd></p>

<br>

<a id="node-vxot1jn"></a>

<p align="center"><kbd><img src="assets/mazewmjwylm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thêm start / end index của cái answer trong câu
>
>
>
> Vd story.answer là 'garden' thì tìm trong story.sentences vị trí của Start
> và end của garden là 28 - 34

<br>

<a id="node-jqsltv3"></a>

- **1.2 - Tokenize and Align Labels with 🤗 Library**

<br>

<a id="node-zot322i"></a>

> [!NOTE]
> **1.2 - Tokenize and Align with** 🤗 **Library** 
>
> Now you have all the data you need to train a Transformer model to perform Question
> Answering! You are ready for a task you may have already encountered in the
> Named-Entity Recognition lab - tokenizing and aligning your input. To feed text data to a
> Transformer model, you will need to tokenize your input using a \\_🤗 Transformer
> tokenizer\\_. It is crucial that the tokenizer you use must match the Transformer model
> type you are using! In this exercise, you will use the 🤗 \\_DistilBERT fast tokenizer\\_,
> which standardizes the length of your sequence to 512 and pads with zeros.
>
> Transformer models are often trained by tokenizers that split words into subwords. For
> instance, the word 'Africa' might get split into multiple subtokens. This can create some
> misalignment between the list of tags for the dataset and the list of labels generated by
> the tokenizer, since the tokenizer can split one word into several, or add special tokens.
> Before processing, it is important that you align the start and end indices with the tokens
> associated with the target answer word with a tokenize_and_align() function. In this case,
> since you are interested in the start and end indices of the answer, you will want to align
> the index of the sentence to match the index of the token for a word.
>
> Lại nữa dùng tokenizer DistillBERT để tokenize trước khi bỏ vào
> Transformer model, nhắc lại tầm quan trọng của việc hai thằng đó
> phải 'HỢP' nhau
>
>
>
> Thằng DistillBERT này làm việc theo kiểu tokenize ra độ dài 512 và
> pad với 0
>
>
>
> Y như Ungraded Lab trước, ta cũng cần phải align lại vì tokenizer
> sẽ split 1 từ ra thành nhiều subword dẫn đến bị lệch..

<br>

<a id="node-8e9g16t"></a>

<p align="center"><kbd><img src="assets/xtc53ihenws.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là viết function để làm cái việc 'align'

<br>

<a id="node-ojnb4ju"></a>

> [!NOTE]
> This is a Python function called tokenize_align that takes in an
> example argument. The purpose of the function is to tokenize and
> align text data for use in a question-answering model.
>
> The function uses a tokenizer, which is not defined in the code
> snippet, but is likely an object that performs text tokenization. The
> tokenizer is used to encode the example's sentences and question,
> with truncation and padding enabled to ensure that all inputs have
> the same length. The max_length parameter sets the maximum
> allowed length of the resulting tokenized sequences.
>
> The char_to_token method of the encoding object is used to align the
> answer span to the corresponding positions in the tokenized input.
> The start_positions variable stores the token index of the first
> character in the answer span, and end_positions stores the token
> index of the last character in the answer span.
>
> If the answer span's starting or ending character is outside the range
> of the tokenized input, then char_to_token returns None. In this case,
> the corresponding start_positions or end_positions variable is set to
> the maximum token index.
>
> Finally, the function returns a dictionary with the tokenized input IDs,
> attention mask, start position, and end position. These values can be
> used as input to a question-answering model.

<br>

<a id="node-1a883vm"></a>

> [!NOTE]
> qa_dataset['train'][200]
>
> ->
>
> {'question': 'What is north of the bathroom?',
>  'sentences': 'The garden is north of the bathroom. The hallway is south of the bathroom.',
>  'answer': 'garden',
>  'str_idx': 4,
>  'end_idx': 10,
>  'input_ids': [101,
>   1996,
>   3871,
>   2003,
>   2167,
>   1997,
>   1996,
>   5723,
>   1012,
>   1996,
>   6797,
>   2003,
>   2148,
>   1997,
>   1996,
>   5723,
>   1012,
>   102,
>   2054,
>   2003,
>   2167,
>   1997,
>   1996,
>   5723,
>   1029,
>   102],
>  'attention_mask': [1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1,
>   1],
>  'start_positions': 2,
>  'end_positions': 2}

<br>

<a id="node-yvvxtrf"></a>

##### 2 - Training

<br>

<a id="node-brm5aq7"></a>

- **2.1 TensorFlow implementation**

<br>

<a id="node-nj4jwbs"></a>

<p align="center"><kbd><img src="assets/fkvnvik65qf.png" width="80%"></kbd></p>

> [!NOTE]
> Hiểu tới đâu hay tới đó, ở đây là ổng..
>
>
>
> Load train & test set từ qa_dataset
>
>
>
> Load pre-trained model

<br>

<a id="node-51gejc4"></a>

<p align="center"><kbd><img src="assets/wkfmp8l9227.png" width="80%"></kbd></p>

> [!NOTE]
> Hiểu tới đâu hay tới đó
>
>
>
> Đại khái là nếu implement bằng TensorFlow thì phải set data format sang
> Tensor có thể khiến tạo ra các Tensor dài ngắn khác nhau gọi là ragged tensor
> nên mình phải dùng function **to_tensor**(), function này giúp kiểu như 'sửa
> lại' đễ tạo thành các tensor đều có size [None, tokenizer. model_max_length],
> vậy thôi

<br>

<a id="node-jy5ll6u"></a>

<p align="center"><kbd><img src="assets/7awapadvjno.png" width="80%"></kbd></p>

> [!NOTE]
> Tại sao lại dùng SparseCategoricalCrossentropy

<br>

<a id="node-xps5f1z"></a>

<p align="center"><kbd><img src="assets/jk51323rpjr.png" width="80%"></kbd></p>

<br>

<a id="node-1vq9dou"></a>

<p align="center"><kbd><img src="assets/78v6w72sy7s.png" width="80%"></kbd></p>

<br>

<a id="node-3zj3xoo"></a>

- **2.2 PyTorch implementation**

<br>

<a id="node-y922ja3"></a>

##### What you should remember:

<br>

<a id="node-xvvrdpy"></a>

> [!NOTE]
> • Transformer models are often trained by tokenizers that split
> words into subwords.
>
> ▪ Before processing, it is important that you align the start and
> end indices with the tokens associated with the target answer
> word.
>
> • PyTorch is a relatively light and easy to implement framework
> that can make rapid prototyping easier, while TensorFlow has
> advantages in scaling and is more widely used in production
>
> ▪ tf.GradientTape allows you to build custom training loops in
> TensorFlow
>
> ▪ The Trainer API in PyTorch gives you a basic training loop
> that is compatible with 🤗 models and datasets

<br>

<a id="node-5va1zy5"></a>

### Transformer Using Trax Librabry

<br>

