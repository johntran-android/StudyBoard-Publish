# C3w2_recurrent Neural Networks For Language Modeling

📊 **Progress:** `85` Notes | `138` Screenshots

---
<a id="node-h8gtvl3"></a>

## C3w2_recurrent Neural Networks For Language Modeling

> [!NOTE]
> Learn about the limitations of traditional language models and see how RNNs and GRUs 
> use sequential data for text prediction. Then build your own next-word generator using a 
> simple RNN on Shakespeare text data!
>
>
>
> Learning Objectives
>
>
>
>  • N-grams
>  • Gated recurrent units
>  • Recurrent neural networks

<br>

<a id="node-nx978r9"></a>

## Traditional Languages Models

<br>

<a id="node-szgnmpk"></a>

> [!NOTE]
> 1 N-gram language models have **limitations** in terms of **space** and **memory requirements.**
>
> 2 To compute the **probability of a sequence of word**s, **N-gram models require computing conditional
> probabilities for bigrams** or higher-order N-grams.
>
> 3 The p**robability of a sentence** in an N-gram model is obtained by **multiplying the probabilities of each
> word using its previous (N-1) words**.
>
> 4 N-gram models **struggle to capture dependencies between words that are far apart**, as they would
> **require accounting for conditional probabilities in very long word sequences.**
>
> 5 **Estimating** these probabilities **becomes challenging** with **large corpora**, and **storing all possible
> combinations of probabilities** would **require significant space and memory**.
>
> 6 **Recurrent Neural Networks (RNNs)** and **Gated Recurrent Units (GRUs)** are **more efficient models**
> for **natural language processing (NLP)** tasks like **machine translation.**
>
> 7 **RNNs and GRUs** are **more suitable for scenarios with limited space**, such as **mobile applications**,
> as they do **not require storing the entire probability distribution** like N-gram models.
>
> 8 **RNNs** are introduced as an alternative to traditional N-gram language models in this video, offering
> more efficient approaches for NLP tasks.

<br>

<a id="node-nty2w6z"></a>

<p align="center"><kbd><img src="assets/qtlyat54mao.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với N-Gram model ra được câu này là có P(sen) cao nhất.

<br>

<a id="node-6jfcj7x"></a>

<p align="center"><kbd><img src="assets/mxvw52x07y.png" width="80%"></kbd></p>

> [!NOTE]
> Xác suất của từ tiếp theo sẽ phụ thuộc vào n-1 từ trước đó (N-gram). Hạn
> chế của phương pháp này là nó khó nắm bắt được dependencies của
> những từ ở xa và nếu có làm được cũng cần rất nhiều space và RAM

<br>

<a id="node-ib4yslf"></a>

## RNN

<br>

<a id="node-bquk8dy"></a>

> [!NOTE]
> 1 **Recurrent Neural Networks (RNNs)** have **advantages** over **traditional N-gram language
> models** in **capturing dependencies** that **N-grams cannot capture**.
>
> 2 **RNNs** can **propagate information** **from the beginning to the end of a sequence**, allowing for
> **better predictions**.
>
> 3 Traditional language models, like **trigrams**, may **select the most probable word based on the
> previous context**, but it **may not make sense in the context of the sentence.**
>
> 4 RNNs are **not limited to considering only the previous n words** and **can use information from the
> entire sequence.**
>
> 5 To capture dependencies for sentence completion using an N-gram model, one would need to
> account for impractical and lengthy sequences of words.
>
> 6 RNNs propagate information through a sequence by computing values at each step, **using
> information from previous computations** and the **current word**.
>
> 7 The computations in an RNN are **repeated for each word in the sequence**, with the **same
> weights** multiplied to propagate information.
>
> 8 RNNs are called **recurrent** because they \\_**repeatedly feed the computed values to
> themselves**\\_ **until** a **prediction is made**.
>
> 9 The main advantage of RNNs is **their ability to propagate information within sequences**, **sharing
> most of the parameters in the computations**.
>
> 10 **Different types of RNN architectures** will be explored in the next video, along with guidelines on
> when to use each type.

<br>

<a id="node-dwfkvlj"></a>

<p align="center"><kbd><img src="assets/ga7xj77jroi.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu dùng **N-gram ví dụ 3-gram** trong bài toán này nó
> sẽ chọn từ have vì "did not have" có **xác suất cao trong corpus**
> nhưng **rõ ràng là sai bét.**

<br>

<a id="node-3djiid3"></a>

<p align="center"><kbd><img src="assets/s4igzll9bio.png" width="80%"></kbd></p>

> [!NOTE]
> Ý nói **để làm đúng được** nó phải **dựa trên context là cả
> câu chứ không thể chỉ dựa vào vài từ trước đó**.

<br>

<a id="node-m5ogchk"></a>

<p align="center"><kbd><img src="assets/n8xdws9pq4.png" width="80%"></kbd></p>

> [!NOTE]
> **Mỗi lần tính toán (cho một từ, một time step)** nó sẽ lấy thông
> tin từ trước đó và hiện tại do đó kết quả của từ cần tìm sẽ được
> dựa trên thông tin từ tất cả các từ trong câu giúp tạo ra kết quả
> chính xác hơn N-gram

<br>

<a id="node-snrz7ch"></a>

<p align="center"><kbd><img src="assets/v2w6bsebl6g.png" width="80%"></kbd></p>

> [!NOTE]
> Chữ recurrent là vì các **time-step** đều được **share cùng một
> Wh**, kiểu như tính toán lặp đi lặp lại với input từ time-step trước và
> current word cho đến khi hoàn thành (tìm được từ, hay hoàn thành
> câu)

<br>

<a id="node-u3imtdt"></a>

<p align="center"><kbd><img src="assets/qc3lsyvxrvn.png" width="80%"></kbd></p>

<br>

<a id="node-5q6bv83"></a>

<p align="center"><kbd><img src="assets/ppnmy4sw7b.png" width="80%"></kbd></p>

<br>

<a id="node-cu27jw8"></a>

## Applications Of RNN

<br>

<a id="node-zbsklxx"></a>

> [!NOTE]
> 1 **Different tasks in A**I can be **categorized** based on their **input and output nature.**
>
> 2 **One-to-One task**s involve taking a **set of input features** and **returning a single output**.
>
> 3 Fo**r tasks like predicting a team's position on a leaderboard** using **input scores**, a recurrent neural
> network (RNN) isn't significantly different from a conventional neural network.
>
> 4 **One-to-Many** tasks involve **taking a single input (e.g., an image)** and **generating multiple outputs (e.g.,
> a caption describing the image).**
>
> 5 **Sentiment analysis** is an example of a **Many-to-One task**, where a **sequence of words is inputted**, and
> the **RNN outputs the sentiment (positive or negative).**
>
> 6 **Many-to-Many tasks** involve **multiple inputs and multiple outputs**, such as **machine translation**, where a
> **sequence of words in one language is translated to another language**.
>
> 7 The **encoder-decoder architecture** is commonly **used in machine translation**, with the **encoder capturing
> the overall meaning of the input sentenc**e and the **decoder generating the translated sequence.**
>
> 8 **RNNs** are **powerful architectures** that can be **used to solve various problems in natural language
> processing (NLP)**, including **machine translation and caption generation.**
>
> 9 **RNNs** are **versatile tools** that can be **shaped according to the specific task requirements.**
>
> 10 Choosing the appropriate RNN architecture depends on the task at hand.
>
> 11 The next video will cover a simple recurrent neural network, which can be applied to the different
> architectures discussed.

<br>

<a id="node-wp75oze"></a>

<p align="center"><kbd><img src="assets/qt0qkhr27eg.png" width="80%"></kbd></p>

<br>

<a id="node-5bdx32f"></a>

<p align="center"><kbd><img src="assets/4o6f00awubr.png" width="80%"></kbd></p>

<br>

<a id="node-zuzgace"></a>

<p align="center"><kbd><img src="assets/yzys3f2a33.png" width="80%"></kbd></p>

<br>

<a id="node-zudxzda"></a>

<p align="center"><kbd><img src="assets/uef3igd2owi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/y73yjtyvzrr.png" width="80%"></kbd></p>

<br>

<a id="node-37iq1b0"></a>

<p align="center"><kbd><img src="assets/9idtzsjev1t.png" width="80%"></kbd></p>

<br>

<a id="node-c7r4c9t"></a>

<p align="center"><kbd><img src="assets/yepry4u9u2s.png" width="80%"></kbd></p>

<br>

<a id="node-vxoxujl"></a>

## Math In RNN

<br>

<a id="node-umn7stu"></a>

> [!NOTE]
> 1 **Recurrent Neural Networks** (RNNs) are **powerful models** for **processing sequential data** and **making sequential
> predictions**.
>
> 2 The computation in a **plain or vanilla RNN** involves taking an **input x**, a **hidden state h**, and producing a
> p**rediction y^** at each **time step <t>** 
> 3 The hidden state at each time step is computed using an **activation function g**, which takes the **product of a
> weight matrix Wh** and the previous **hidden state h<t-1>, concatenated with the input
> variable x<t>** and **a bias term bh**
>
> 4 The **prediction y^** is obtained by using an **activation function g** with the **product** of the **hidden state h<t>** and
> another set of parameters **Wy** plus a **bias term by.**
>
> 5 These equations represent the **mathematical operations** performed in a simple RNN.
>
> 7 The hidden states in RNNs enable the **propagation of information through time**, allowing the network to
> **capture dependencies across different positions** **within a sequence.**
>
> 8 Diagrams similar to the one presented in the video are often used in RNN literature to illustrate the
> **computation flow** and **information propagation** within a recurrent unit.
>
> 9 **Hidden states** serve as the **variables that facilitate information propagation in RNNs.**
>
> 10 The video provides an introduction to the forward propagation equations and the concept of hidden states in
> RNNs, with the promise of explaining the cost function in the next video.

<br>

<a id="node-64mvmmk"></a>

<p align="center"><kbd><img src="assets/xrb1okv5eil.png" width="80%"></kbd></p>

<br>

<a id="node-hl9k42v"></a>

<p align="center"><kbd><img src="assets/v3yxcl5du57.png" width="80%"></kbd></p>

> [!NOTE]
> [h<t-1>, x<t>] tức là h<t-1> sẽ được concatenate với x<t> hoặc cũng
> có thể được triển khai ở dạng riêng biệt Whh và Whx mà trong
> DLSpec mr Andrew ghi là Waa và Wax.
>
>
>
> Wh chính là Whh (hay Waa) stack theo phương horizontally với Whx
> (hay Wax).
>
>
>
> Activation function là tanh hay reLU (DLSpec).
>
>
>
> h<t0) hay a<0> theo DLSpec được initialize là Zeros vector

<br>

<a id="node-o0g241f"></a>

<p align="center"><kbd><img src="assets/k013psin0qo.png" width="80%"></kbd></p>

<br>

<a id="node-fmwha6q"></a>

<p align="center"><kbd><img src="assets/gaa1dqm5olv.png" width="80%"></kbd></p>

> [!NOTE]
> Sơ đồ thể hiện các bước tính
> toán của một RNN unit

<br>

<a id="node-5f83d44"></a>

<p align="center"><kbd><img src="assets/7suyntzxphr.png" width="80%"></kbd></p>

<br>

<a id="node-366xf2v"></a>

<p align="center"><kbd><img src="assets/1agaaz6ojrd.png" width="80%"></kbd></p>

> [!NOTE]
> Hidden state h<t> sẽ có vai trò trong việc mang / lưu thông
> tin through time giúp model nắm bắt được các quan hệ của
> các unit / time-step ở xa nhau

<br>

<a id="node-xi2xfdi"></a>

<p align="center"><kbd><img src="assets/sqapg3dopc.png" width="80%"></kbd></p>

> [!NOTE]
> Theo DLSpec ta đã biết h<t-1> sẽ stack theo vertically với
> x<t> nên kết quả là 4+10 x 1 = 14x1. Nên để nhân matrix
> được thì Wh phải là 4x14 hoặc 14x14.

<br>

<a id="node-c8ehdaz"></a>

## Lab: Hidden State Activation

<br>

<a id="node-u98ehc8"></a>

<p align="center"><kbd><img src="assets/7ji2yq420sc.png" width="80%"></kbd></p>

<br>

<a id="node-2p8iitr"></a>

<p align="center"><kbd><img src="assets/r2nyq053cw.png" width="80%"></kbd></p>

> [!NOTE]
> Wh là horizontally stack của Whh và Whx.
> Còn [ h<t-1>, x<t>] là vertically stack của
> h<t-1> và x<t>

<br>

<a id="node-tq9thgt"></a>

<p align="center"><kbd><img src="assets/accdkjizey.png" width="80%"></kbd></p>

<br>

<a id="node-pnlh8tu"></a>

<p align="center"><kbd><img src="assets/ivgjp9cbct.png" width="80%"></kbd></p>

> [!NOTE]
> Để horizontally stack ta dùng concatenate ((matrix 1, matrix 2), axis=)
> axis = 1 tức là "concate theo cột" tức là horizontally ||| + || -> |||||
>
>
>
> Cách khác là hstack (horizontally stack)

<br>

<a id="node-ou52jqt"></a>

<p align="center"><kbd><img src="assets/a53df5jjgw.png" width="80%"></kbd></p>

<br>

<a id="node-m7a0lwc"></a>

<p align="center"><kbd><img src="assets/pphj0s7psn.png" width="80%"></kbd></p>

> [!NOTE]
> [ h<t-1>, x<t>] là vertically stack của h<t-1> và x<t>

<br>

<a id="node-ngebs6o"></a>

<p align="center"><kbd><img src="assets/vo0rglr3gt.png" width="80%"></kbd></p>

> [!NOTE]
> Để vertical stack ta dùng
> concatenate (axis = 0) hoặc vstack()

<br>

<a id="node-fhl4rjs"></a>

<p align="center"><kbd><img src="assets/w0z4u7lqe7.png" width="80%"></kbd></p>

<br>

<a id="node-927jip0"></a>

<p align="center"><kbd><img src="assets/9ykcyd9z7qp.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là so sánh thử xem có đúng là hai công thức nhân (nhân
> matrix) Wh là horizontlly stack của Whh và Whx với vertically stack của
> h<t-1> và x<t> có chính là tổng của Whh.h<t-1> và Whx.x<t> hay
> không.

<br>

<a id="node-6zhmo6t"></a>

<p align="center"><kbd><img src="assets/lle7792lwf.png" width="80%"></kbd></p>

<br>

<a id="node-4rvvht5"></a>

<p align="center"><kbd><img src="assets/atn9h1kfea6.png" width="80%"></kbd></p>

> [!NOTE]
> Kết qủa đúng là
> giống nhau

<br>

<a id="node-4hz4si7"></a>

> [!NOTE]
> Summary That's it! We've verified that the **two formulas
> produce the same results**, and seen how to combine
> matrices vertically and horizontally to make that happen.
> We now have all the intuition needed to understand the
> math notation of RNNs.

<br>

<a id="node-9mqai9e"></a>

## Cost Function For RNN

<br>

<a id="node-09nxc5d"></a>

<p align="center"><kbd><img src="assets/hvccb4ris74.png" width="80%"></kbd></p>

> [!NOTE]
> Cross entropy loss là loss function cho bài toán **multi-class classification**
>
>
>
> Ví dụ **y = [1, 0, 0]** - thể hiện **ground-truth label** là con **mèo** trong bộ 3
> class [mèo gà, chó] và **y^ = [y^_1 y^_2 y^_3]**.
>
>
>
> Thì loss (cho training example này) sẽ là **- (1*y^_1 + 0*y^_2 + 0*y^3)** = **- y^1**.
>
>
>
> Vậy **muốn giảm loss** thì model phải làm sao cho (**- y^_1)** càng nhỏ càng tốt,
> đồng nghĩa **y^_1** **phải** **càng lớn càng tốt.**
>
>
>
> Dẫn tới là nó sẽ adjust weight sao cho nó ra **y^ ví dụ = [0.99, 0.005, 0. 005]** để
> predict image là con mèo.
>
>
>
> Trong bài toán này, **nếu nó là mèo thì không thể là gà hay chó**, nên label y là
> **[1 0 0] hoặc [0 1 0]** chứ không thể **[1 1 0]** được.
>
>
>
> Và **tổng ba giá trị y^_1, y^_2, y^_3 phải = 1** nên layer cuối sẽ chọn **Softmax**
> activation function và cross function sẽ là **Categorical Cross Entropy**
>
>
>
> ===Tuy nhiên nếu là bài toán khác, **multi-label classification** === label cho 1
> example y(i) viết gọn là y sẽ là [1 1 1] thì y^ sẽ có thể là [0.99 0.98 0.98] thì
> activation function sẽ là: **Sigmoid** và loss function tương ứng sẽ là **Binary Cross
> Entropy**

<br>

<a id="node-c2pk5p8"></a>

> [!NOTE]
> So sánh, ôn lại hai bài toán
> Multi-class và Multi-label

<br>

<a id="node-i6lw3zx"></a>

<p align="center"><kbd><img src="assets/hqcsj3ymxa.png" width="80%"></kbd></p>

<br>

<a id="node-bm7tk8o"></a>

<p align="center"><kbd><img src="assets/9bebf7ty654.png" width="80%"></kbd></p>

<br>

<a id="node-29j60wr"></a>

<p align="center"><kbd><img src="assets/ee246xujzj5.png" width="80%"></kbd></p>

<br>

<a id="node-wk4rnqg"></a>

<p align="center"><kbd><img src="assets/ckrav4dncfa.png" width="80%"></kbd></p>

<br>

<a id="node-1kyeamn"></a>

<p align="center"><kbd><img src="assets/mtfcd8nh4go.png" width="80%"></kbd></p>

<br>

<a id="node-juagdzz"></a>

<p align="center"><kbd><img src="assets/af1nyrevkzm.png" width="80%"></kbd></p>

<br>

<a id="node-a19bji8"></a>

<p align="center"><kbd><img src="assets/6ge0bealqhk.png" width="80%"></kbd></p>

> [!NOTE]
> Đối với RNN ta tính trung bình
> loss của các time-step

<br>

<a id="node-6e1o9om"></a>

## Implementation Note

<br>

<a id="node-lu32g4i"></a>

<p align="center"><kbd><img src="assets/nhwsp5r0clh.png" width="80%"></kbd></p>

<br>

<a id="node-duatjfi"></a>

<p align="center"><kbd><img src="assets/ysizixrcack.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó như một function bình thường làm cái việc là **loop
> trong tất cả các time-step của sequence** (**elements**, **chính là x**
> tensor) để **tính toán các bước của một RNN unit / time-step** dùng
> function **fn** với input là **x** và **previous hidden state là cur_value** để
> được **y<t> = y và h<t> = cur_value** (hay a<t> trong DLSpec).
>
>
>
> **Append** y vào ys là một list chứa các y<t>.
>
>
>
> Ổng nói sở dĩ phải có cái scan function như này là kiểu như tạo
> một **abstraction function để TF nó tối ưu bằng cách run trên GPU**

<br>

<a id="node-oe5em78"></a>

<p align="center"><kbd><img src="assets/eeb6w8ujube.png" width="80%"></kbd></p>

<br>

<a id="node-4f9rwse"></a>

<p align="center"><kbd><img src="assets/iomloo009k.png" width="80%"></kbd></p>

<br>

<a id="node-fz0lrsi"></a>

<p align="center"><kbd><img src="assets/hpoz3dp38f7.png" width="80%"></kbd></p>

<br>

<a id="node-tb7l8h8"></a>

> [!NOTE]
> LAB: VANILLA RNN, GRU AND THE SCAN
> FUNCTION

<br>

<a id="node-lv44hew"></a>

<p align="center"><kbd><img src="assets/dnvw53cg75i.png" width="80%"></kbd></p>

<br>

<a id="node-t9gk8d2"></a>

> [!NOTE]
> Part 1: Forward method for
> vanilla RNNs and GRUs

<br>

<a id="node-wdv8rz7"></a>

<p align="center"><kbd><img src="assets/edqj0d70ua6.png" width="80%"></kbd></p>

> [!NOTE]
> Embedding size (emb) 128 là **size của embedding vector x<t>**
> (Tất nhiên **nếu xử lý một batch** thì x<t> sẽ là (**batch_size, emb**).
> Hidden state size **h_dim** hoặc **(batch_size, h_dim**) là size của
> **h<t> (hay a<t>** theo DLSpec)

<br>

<a id="node-qausuon"></a>

<p align="center"><kbd><img src="assets/c824v3oh0wc.png" width="80%"></kbd></p>

> [!NOTE]
> Nhận xét, họ không define axis cho np.
> concatenate như trong DLSpec

<br>

<a id="node-vnjw9as"></a>

<p align="center"><kbd><img src="assets/3ikv2aivc7y.png" width="80%"></kbd></p>

> [!NOTE]
> **Reset gate** thì kiểu như cho **phép model quyết định** thông tin của **c<t>**
>  **có cần phải lấy từ previous hidden state h<t-1> hay không**.
> Ta thấy nếu value (của element trong Reset gate tensor) **gần 1**
> tức là **model nhận thấy h<t-1> quan trọng** cần (cùng với x<t>)
> để tính toán c<t>.
> Còn ngược lại, nó sẽ adjust weight để **Reset gate value ~=0** và
> **c<t> sẽ chỉ ảnh hưởng bởi x<t>**
>
>
>
> Có thể thấy **Update gate** trong GRU với sigmoid function sẽ
> khiến **h<t>** **một là giữ bằng hidden state trước h<t-1>** hoặc **bỏ đi
> thay mới bằng c<t>**. Tất nhiên sigmoid cho ra trong khoảng 0,1
> nhưng như Mr Andrew có nói thực tế nó sẽ ~=0 hoặc ~=1 để
> control việc dùng c<t> hay h<t-1>

<br>

<a id="node-d3zn02e"></a>

<p align="center"><kbd><img src="assets/ivih7fl0s2.png" width="80%"></kbd></p>

> [!NOTE]
> Update gate của RNN

<br>

<a id="node-6rdz9ij"></a>

<p align="center"><kbd><img src="assets/xwxoo73wuer.png" width="80%"></kbd></p>

> [!NOTE]
> Reset gate

<br>

<a id="node-alpv9j0"></a>

<p align="center"><kbd><img src="assets/p7sfrygr0dm.png" width="80%"></kbd></p>

<br>

<a id="node-nht4nmr"></a>

> [!NOTE]
> Part 2: Implementation of
> the scan function

<br>

<a id="node-t5cojm8"></a>

<p align="center"><kbd><img src="assets/mrof1ozwum.png" width="80%"></kbd></p>

<br>

<a id="node-pi3qz36"></a>

> [!NOTE]
> Part 3: Comparison between
> vanilla RNNs and GRUs

<br>

<a id="node-174pls8"></a>

<p align="center"><kbd><img src="assets/dklbclvac4o.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cho thấy **GRU chậm hơn RNN tuy
> nhiên nó cho phép giữ thông tin liên quan cần
> thiết cho long sequence**s.

<br>

<a id="node-cwq1hfg"></a>

> [!NOTE]
> LAB: WORKING WITH JAX NUMPY AND
> CALCULATING PERPLEXITY

<br>

<a id="node-qxe4j38"></a>

### Jax numpy

<br>

<a id="node-gw23tks"></a>

<p align="center"><kbd><img src="assets/m965vb3d4w8.png" width="80%"></kbd></p>

<br>

<a id="node-g4r8v9d"></a>

<p align="center"><kbd><img src="assets/jmlwvyuyji.png" width="80%"></kbd></p>

<br>

<a id="node-1qtq39q"></a>

### Calculating Perplexity

<br>

<a id="node-xe0tytl"></a>

<p align="center"><kbd><img src="assets/fg895e40h4.png" width="80%"></kbd></p>

> [!NOTE]
> Ôn lại perplexity là metric giúp đánh giá một language model xem khả
> năng nó tạo ra một sample (ví dụ như một câu) có giống thật hay
> không. Ta đã học qua, đại khái là nó tính chỉ số này dựa trên xác suất
> của cái câu mà nó tạo có cao hay không. Công thức của nó như vầy.
> Và để tránh "**underflow problems**" - khi số quá nhỏ, thì người ta
> **thường tính log của Perplexity** thay vì Perplexity.
>
>
>
> Theo sự hiểu, language model sau khi đ**ược huấn luyện từ một
> corpus** sẽ học được ... kiểu như **"xác suất của các từ trong corpus"**
> . Do đó **để test 'năng lực' của model**, người ta sẽ **đưa cho model
> xem một sequence các từ và bảo nó dự đoán từ tiếp theo, rồi so sánh
> nó với kết quả thực.**

<br>

<a id="node-l92w2uq"></a>

<p align="center"><kbd><img src="assets/k9q7g76jkhk.png" width="80%"></kbd></p>

> [!NOTE]
> Các biến đổi dưới dựa vào các công thức sau:
>
>
>
> 1. căn bậc N của a là a^(1/N)
>
>
>
> 2. 1/a là a^-1
>
>
>
> 3. (a^(-1))^(1/N) = a^(-1/N) vì (a^b)^c) = a^(b*c).
>
>
>
> 4. Log(a^b) = (1/b)*Log(a)
>
>
>
> 5. Log(a*b*c) = Log(a) + Log(b) + Log(c)

<br>

<a id="node-an1wgjm"></a>

<p align="center"><kbd><img src="assets/b8j6oz3o0uj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bài toán của mình sắp tới sẽ là **dùng RNN hay GRU để build một
> language model**, trong đó model sẽ **predict một sequence** (hoặc chính xác
> hơn là **một** **batch các sequence**).
>
>
>
> Tất nhiên **ground truth label cũng là môt sequence hay batch các sequence**.
> Ở đây là một kiểu như **cho ví dụ một "bộ" predictions và label**. **Batch size là
> 32**, chiều dài **sequence là 64**. Tuy nhiên để ý predictions có shape là (32 x
> 64 x **256)**
>
>
>
> Cái dimension cuối là bởi vì, model không **"một phát" cho ra luôn "từ thứ nhất
> là 5 (**ứng với từ thứ 5 trong vocab là "I" ví dụ vậy), **từ thứ hai là 7**, **từ thứ
> ba là 11**... để rồi một prediction **y^(i)** của nó có dạng **[5 7 11 ...** ]
>
>
>
> Mà thay vào đó, **tại mỗi vị trí,** nó sẽ cho ra **một array/vector các giá trị xác
> suất** của **các từ trong vocab**, t**ổng các giá trị p này sẽ bằng 1** và để kết
> luận ta sẽ **lấy từ tương ứng với vị trí có p lớn nhất.**
>
>
>
> Và ở đây ví dụ vocab có **256 từ. Đó là lí do predictions có shape như vậy**
>
>
>
> Nói thêm chút xíu không ảnh hưởng đó là, ở ví dụ này, **predictions chứa log
> probabilities** chứ **không phải thuần tuý probabilities**.  Do đó các giá trị của
> y^(i)<1> prediction của example i, tại time-step (từ) thứ 1 sẽ là **một array có tổng
> không bằng 1 (vì là log của prob) chứ không phải prob**

<br>

<a id="node-wt3ipyz"></a>

<p align="center"><kbd><img src="assets/b1qb2li70zh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vxxevk22xl.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy thì, nói về **y**, có dạng một **tensor shape:** **m example x số từ
> trong sequence** ví dụ **y(1) có thể là [5 120 4 ...]** thể hiện **câu đúng
> của training example x(1) là [Anh muốn ăn cơm]** trong đó **'Anh' là từ
> thứ 5 trong vocab**, **'muốn' là từ thứ 120**...
>
>
>
> Muốn đưa vào model **để tính loss thì cũng phải biến ' Anh', 'muốn',...
> thành one-hot vector** có **độ dài bằng vocab size = 256,** như ta đã biết
> số 1 trong vector sẽ nằm tại index của từ 'Anh' trong vocab.
>
>
>
> Do đó ở đây giới thiệu function **tl.one_hot** để **thực hiện việc one-hot
> encoding này**. Người ta dùng **predictions.shape[-1]** để **lấy giá trị của
> last dimension** của predictions chính là **256**. Có thể cho tiện, **thay vì
> phải hard code là 256, hay một variable vocab size nào đó**

<br>

<a id="node-nt1jf9d"></a>

<p align="center"><kbd><img src="assets/e44jrszjq2p.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sy9w4umoi.png" width="80%"></kbd></p>

> [!NOTE]
> Khúc này là nói về việc **tính log perplexity** theo công thức đây **rất giống
> cách tính loss function**. Hình vẽ lý giải tại sao axis = -1 và log_p sẽ là
> tensor batch_size (32) x Ty (64)

<br>

<a id="node-4c56jyy"></a>

<p align="center"><kbd><img src="assets/r3rhg81n2j.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **target** như ta nói ở trên **batch (32) x sequence_len
> (64)** khi chưa sử lý one-hot sẽ **có giá trị là index của từ đúng trong
> vocab**. Và **chỗ nào = 0 tức là padding** bởi **zeros padding**.
>
>
>
> Ví dụ câu **"I love you"** sẽ thành **[159 23 241 0 0 0 ...0]** với **3 vị
> trí đầu tiên** là **index của từ I, love, you trong vocab**, còn lại **fill 0
> vào cho đủ sequence_len**.
>
>
>
> Hiểu vậy rồi thì dễ hiểu tại sao nó tính cái **non_pad** như bên dưới.
> Mục đích của **non_pad có shape là (32x64)** sẽ là cái **filter để nhân
> nó với matrix log sẽ bỏ đi những log của padding**

<br>

<a id="node-wyja3o6"></a>

<p align="center"><kbd><img src="assets/2hwrsoc3fb7.png" width="80%"></kbd></p>

<br>

<a id="node-v8vnm5u"></a>

<p align="center"><kbd><img src="assets/cuz1yehcdvu.png" width="80%"></kbd></p>

> [!NOTE]
> Nhân với log_p để bỏ đi các effect của padding

<br>

<a id="node-5m2n9tt"></a>

<p align="center"><kbd><img src="assets/6dxqfteaivn.png" width="80%"></kbd></p>

> [!NOTE]
> Chỗ này lạ nè, tính perplexity nhìn giống như tính loss
> vậy. Chưa hiểu lắm. Nhưng cứ theo đó mà tính

<br>

<a id="node-1s5719f"></a>

<p align="center"><kbd><img src="assets/eg39ajgrqt.png" width="80%"></kbd></p>

<br>

<a id="node-dj4j0wy"></a>

<p align="center"><kbd><img src="assets/x9eoi91lr7.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu những mang máng hiểu (tại sao tính perplexity lại như vậy) .
> Giả sử tại một từ có G.T là [0 1 0 0] model predict ra là [a b c d] thì để P
> cao thì b phải cao, không việc nhân với y sẽ khiến trong loss function chỉ
> quan tâm đến b, và muốn giảm loss thì b phải cao lên = tăng khả năng
> đoán đúng. Và ở khía cạnh đánh giá bằng Perplexity, model có muốn có
> Perplexity cao thì cũng phải cho ra con số b cao. Ý nói logic giống nhau,
> khi dùng ylogy^ để xây dựng loss function cũng như là perplexity score.

<br>

<a id="node-pkoi1yv"></a>

<p align="center"><kbd><img src="assets/n03bhwkhmr.png" width="80%"></kbd></p>

<br>

<a id="node-hevs03g"></a>

## Gru - Gated Recurrent Units

<br>

<a id="node-fd4ntd9"></a>

<p align="center"><kbd><img src="assets/cv0qfssbzqv.png" width="80%"></kbd></p>

<br>

<a id="node-8ero3ux"></a>

<p align="center"><kbd><img src="assets/tstg3gj64k.png" width="80%"></kbd></p>

> [!NOTE]
> 1 Vanilla RNNs are powerful but suffer from the **vanishing information problem** for
> **long sequences.**
>
>
>
> 2 Gated Recurrent Units (GRUs) are **more complex models** that can **handle long
> sequences effectively.**
>
>
>
> 3 GRUs **allow relevant information to be preserved** in the **hidden state** over **long
> sequences.**
>
>
>
> 4 GRUs can be used for tasks such as predicting missing words in a sentence
> based on context.
>
>
>
> 5 GRUs use **relevance** and **update gates** to **control the flow of information in the
> hidden state**.
>
>
>
> 6 GRUs are an extension of vanilla RNNs with additional computations.
>
>
>
> 7 GRUs take inputs of the current variable (X) and the previous hidden state (h)
> at each time step.
>
>
>
> 8 **Relevance gates (Gamma subscript r)** and **update gates (Gamma subscript u)**
> are computed using **sigmoid activation functions**.
>
>
>
> 9 **Relevance gates** determine **which information from previous hidden states is
> relevant**.
>
>
>
> 10 A **candidate hidden state (h prime)** is computed based on the **previous hidden
> state and the relevance gates.**
>
>
>
> 11 A n**ew hidden state** is calculated using the **previous hidden stat**e, **candidate
> hidden state, and update gates.**
>
>
>
> 12 **Update gate**s determine h**ow much information from the  previous hidden state
> will be overwritten.**
>
>
>
> 13 A prediction (y hat) is computed using the current hidden state.
>
>
>
> 14 GRUs overcome the vanishing information problem and allow for better
> long-term dependency modeling compared to vanilla RNNs.
>
> Có nói trong DLSpec, nói lại cho nhớ rõ không thừa. Điểm quan trọng
> thứ nhất chính là **Relevant gate** (trong DLSpec mình note là
> **Reset gate**, cũng không sai) cho phép model **đánh giá sự "
> relevant" của các thông tin trước đó h<t0> với thông tin đưa vào hiện
> tại x<t1>** để quyết định sẽ **có hay không nhiều hay ít phần thông tin
> trước đó để kết hợp với thông tin hiện tại để tính ra h'<t1>** tạm gọi là
> **candidate cho hidden state** ở time-step hiện tại.
>
>
>
> Và **Update gate** sẽ q**uyết định phần thông tin nào là lấy từ
> candidate này hay từ previous hidden state.** Tức ở đây nó sẽ **dùng
> cả relevant gate và update gate** để **cân nhắc kết hợp thông tin cũ
> và mới dựa theo sự liên quan**.

<br>

<a id="node-dww1r7k"></a>

<p align="center"><kbd><img src="assets/4uku391fvux.png" width="80%"></kbd></p>

> [!NOTE]
> Remember that a **vanilla RNN** such as this one computes an activation function
> with the previous hidden states and currents variable X's parameters to get the
> current hidden state. With the current hidden state, another activation function
> is computed to get the current prediction y hat. **This architecture is updating the
> hidden state at every time step, for long sequences, the information tends to
> vanish**. This is one cause of the so-called vanishing gradients problem.

<br>

<a id="node-g3yrtbp"></a>

<p align="center"><kbd><img src="assets/3vhz8ec2prm.png" width="80%"></kbd></p>

<br>

<a id="node-zfli79s"></a>

<p align="center"><kbd><img src="assets/k3d4lmjwb8o.png" width="80%"></kbd></p>

<br>

<a id="node-864ei3l"></a>

## Lab: Creating A Gru Model Using Trax

<br>

<a id="node-46cealt"></a>

<p align="center"><kbd><img src="assets/ng4j2dsy4kf.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái ngắn gọn là minh hoạ **một simple Vanilla neural network
> define với Trax dùng Serial layers combinator**. Trong Trax thì
> **activation function cũng là một layer riêng biệt**. Và cuối cùng nói
> **Trax rất dễ hiểu**, lệnh **print model** sẽ **cho ra ngay cấu trúc
> của model define thế nào thì thấy thế đó** không lòng vòng giấu
> diếm

<br>

<a id="node-qspkxda"></a>

<p align="center"><kbd><img src="assets/2b1a89uyl84.png" width="80%"></kbd></p>

<br>

<a id="node-fzjpgga"></a>

<p align="center"><kbd><img src="assets/drdkseyts0u.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jx8ygh2e2f.png" width="80%"></kbd></p>

> [!NOTE]
> Giải thích ShiftRight: Tương tự bài toán tạo ra tên khủng long ở DLSpec.
> Nhưng ở đây ta không tự làm quá trình loop (forward) nên không làm như
> trong bài toán đó trong đó define **y<t> = x<t+1>** mà ta sẽ dùng **ShiftRight
> layer n_shifts = 1**. Nói **ngắn gọn lại** cho mục đích của việc này là **để
> model predict một time-step y^<t>** dựa vào **những từ / kí tự trước đó**. Do
> đó ban đầu (time-step 1, chưa có gì), thì đương nhiên phải input vào model
> (x<1>) để predict phải là "chưa có gì", tức x<t> phải = 0. Và ta làm vậy bằng
> cách insert một số 0 vào vị trí đầu của tensor x. Chứ nếu không ShiftRight
> hoá ra model predict lại nhận / dựa vào chữ đầu tiên để predict ra chữ đầu
> tiên à? (Như trong tên khủng long, nhận chữ d rồi predict chữ d thì rõ ràng là
> không đúng)

<br>

<a id="node-m8b8dpr"></a>

<p align="center"><kbd><img src="assets/p43hem9lh5.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/15o111tcdtd.png" width="80%"></kbd></p>

> [!NOTE]
> Define một GRU network, lí do **Dense layer có n_units = vocab_size**
> là vì cái này là họ kiểu như nói trước (hướng dẫn) về bài toán dự đoán kí
> tự / generate chuỗi kí tự trong P.A. tương tự như trong bài toán generate
> tên khủng long của DLSpec, trong đó ta tạo một RNN học các pattern
> trong tên khủng long bằng một bộ data tên khủng long. để khi training
> xong, sampling từ model để có tên khủng long mới để mà đặt cho một
> loại khủng long mới phát hiện.
>
>
>
> Và **activation z<t> của mỗi time-step tính từ hidden state là một vector
> có size bằng vocab size** (cho dù là bài toán ở cấp kí tự, cũng gọi là
> vocab size), **gọi là logit.**
>
>
>
> Và **cái softmax tính với z<t> sẽ cho ra output y<t>**, đương nhiên là
> một **vector dài vocab size, chứa các chỉ số probability score của các kí
> tự**, để rồi cái nào có **p cao nhất sẽ là cái được chọn.** Thì ở đây, **họ còn
> cho z<t> qua một Fully Connected layer trước khi qua softmax** nên có
> thể hiển **độ dài của output từ F.C layer cũng phải bằng vocab size,** do đó
> **số hidden unit của F.C (hay Dense) layer cũng bằng vocab size là
> vậy**.

<br>

<a id="node-lb89dvd"></a>

<p align="center"><kbd><img src="assets/kyrkz1xj1f.png" width="80%"></kbd></p>

> [!NOTE]
> một helper function giúp print
> các layer của model (access
> bằng model.sublayers)

<br>

<a id="node-b5r8snu"></a>

## Deep And Bi-directional Rnns

<br>

<a id="node-7jljwss"></a>

> [!NOTE]
> 1 **Deep recurrent neural networks (RNNs)** are useful for **capturing dependencies that shallow
> RNNs cannot capture.**
>
> 2 Equations used in implementing deep RNNs and their relation to the cost function are explained.
>
> 3 Bidirectional neural networks and their importance are introduced.
>
> 4 **Bidirectional RNNs** **propagate information both from the beginning to the end of a sequence** and
> f**rom the end to the beginning**, allowing predictions to be made for missing information.
>
> 5 Bidirectional RNNs are r**epresented as acyclic graphs** where information **flows independently in
> both directions.**
>
> 6 Computation of **hidden states** and **predictions** in a bidirectional RNN involves **propagating
> information from both direction**s.
>
> 7 **Deep RNNs** consist of **multiple hidden layers,** similar to **regular deep neural networks**.
>
> 8 Information **flows through time in deep RNNs**, followed by **propagation through the layers** to
> obtain predictions.
>
> 9 Bidirectional RNNs and deep RNNs are **variations** of the **vanilla RNN model**, offering **more
> complex capabilities.**
>
> 10 The passage concludes by summarizing the topics covered: RNNs, gated recurrent units,
> bidirectional RNNs, and deep RNNs. It mentions that in the assignments, learners will have the
> opportunity to work with RNNs and understand their implementation.

<br>

<a id="node-kf9mno0"></a>

<p align="center"><kbd><img src="assets/zcbuarnium.png" width="80%"></kbd></p>

<br>

<a id="node-y0nhogr"></a>

<p align="center"><kbd><img src="assets/kmzrif1t95c.png" width="80%"></kbd></p>

> [!NOTE]
> An RNN that's **propagates information** from the **beginning to the end**
> of sequences, would be able to make a prediction tool. It would **take
> the words before the blank as inputs** and **do its best to predict the
> missing word**. However, because **Louise** **doesn't appear until the
> beginning of the next sentenc**e, it would have to guess between **her,
> him and them**
>
> Như đã biết từ DLSpec, bài toán như thế này sẽ không
> giải quyết được bằng uni-directional RNN vì thông tin
> quan trọng cần thiết lại nằm ở sau.

<br>

<a id="node-v7pz5dm"></a>

<p align="center"><kbd><img src="assets/nact05gijw.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/kk6g3squh8.png" width="80%"></kbd></p>

> [!NOTE]
> Thì nếu 'làm' ở chiều ngược lại bắt đầu với
> zeros và tính với các time-step từ T đến t1.
> Hoàn toàn tương tự.

<br>

<a id="node-t00b5pg"></a>

<p align="center"><kbd><img src="assets/528zh3gewta.png" width="80%"></kbd></p>

> [!NOTE]
> Và bi-directional RNNs sẽ combine
> cả hai chiều đi và về lại.

<br>

<a id="node-svdnego"></a>

<p align="center"><kbd><img src="assets/mntxctd7jug.png" width="80%"></kbd></p>

> [!NOTE]
> và prediction y^<t> sẽ được tính
> từ combination cả hidden state
> <t> ở cả hai chiều.

<br>

<a id="node-h0th2d1"></a>

<p align="center"><kbd><img src="assets/j4cbif2wajq.png" width="80%"></kbd></p>

> [!NOTE]
> Deep RNNs sẽ stack các RNNs lại với nhau, thay vì dùng
> Wy tính y^ từ hidden state h<t>, nó sẽ có Wa để tính a<t>
> từ h<t> và dùng a<t> bỏ vào thay cho x của RNNs layer tiếp
> theo.

<br>

<a id="node-3ri30kj"></a>

<p align="center"><kbd><img src="assets/engjpuq04.png" width="80%"></kbd></p>

<br>

<a id="node-vxp5azv"></a>

<p align="center"><kbd><img src="assets/1jgo8wcr4jpi.png" width="80%"></kbd></p>

<br>

<a id="node-0db9f4h"></a>

<p align="center"><kbd><img src="assets/ty22b0kb9wp.png" width="80%"></kbd></p>

<br>

<a id="node-wmdtj12"></a>

## Week Conclusion

<br>

<a id="node-wpl3dt4"></a>

## Quiz

<br>

<a id="node-glp0mlm"></a>

<p align="center"><kbd><img src="assets/21kop4kdqsm.png" width="80%"></kbd></p>

<br>

<a id="node-5pxnl0r"></a>

<p align="center"><kbd><img src="assets/c42376zegwm.png" width="80%"></kbd></p>

<br>

<a id="node-gjcrke8"></a>

<p align="center"><kbd><img src="assets/voovz4hwmf.png" width="80%"></kbd></p>

<br>

<a id="node-hltltn4"></a>

<p align="center"><kbd><img src="assets/h23tn0qv5tw.png" width="80%"></kbd></p>

<br>

<a id="node-erhc0zm"></a>

<p align="center"><kbd><img src="assets/gy72l0n2y5s.png" width="80%"></kbd></p>

> [!NOTE]
> Ý là mỗi từ cần dự đoán tại một time-step chỉ có 1 đáp án đúng chứ
> không phải nhiều đáp án đúng. Nếu nhiều đáp án đúng, hay y<t> là
> multi-hot vector, thì phải tính loss trung bình của nhiều class tại time-step
> đó. Còn phải chia T là vì để tính trung bình loss trên tất cả các time-step
> mới có thể coi là loss của model trên training example x(i). Mỗi time-step
> predict ra một từ, nó cho ra y^(i)<t> là một probability scores vector, để
> so vối y(i)<t> được loss trên time-step <t>. Và loss tính trung trên toàn
> time-step là loss trên training example đó

<br>

<a id="node-5tbhsd1"></a>

<p align="center"><kbd><img src="assets/okq21npskkp.png" width="80%"></kbd></p>

<br>

<a id="node-lt76u32"></a>

<p align="center"><kbd><img src="assets/udav02zs4s.png" width="80%"></kbd></p>

<br>

<a id="node-9vhfk8x"></a>

<p align="center"><kbd><img src="assets/jxfq4por7zl.png" width="80%"></kbd></p>

<br>

<a id="node-89n3lnw"></a>

<p align="center"><kbd><img src="assets/26po2ac9e9v.png" width="80%"></kbd></p>

<br>

<a id="node-s4r4nd3"></a>

<p align="center"><kbd><img src="assets/balf0spz1tj.png" width="80%"></kbd></p>

<br>

<a id="node-wdevy6h"></a>

## P.a Deep N-grams

<br>

<a id="node-z2mavkd"></a>

> [!NOTE]
> Welcome to the second assignment of course 3. In this assignment you will explore 
> **Recurrent Neural Networks RNN**.
>
>  • You will be using the fundamentals of google's \\_**trax**\\_ package to implement any 
> kind of deeplearning model.
>
> By completing this assignment, you will learn how to implement models from scratch:
>  • How to **convert a line of text** into a **tensor**
>  • **Create an iterator** to **feed data to the model**
>  • Define a **GRU** **model** using **trax**
>  • **Train the model** using **trax**
>  • **Compute the accuracy** of your model using the **perplexity**
>  • **Predict** using your own model

<br>

<a id="node-x2f14dd"></a>

#### Overview

<br>

<a id="node-prvlgxv"></a>

> [!NOTE]
> Your task will be to **predict the next set of characters** using the **previous characters.**
>  • Although this task **sounds simple**, it is **pretty useful.**
>  • You will start by **converting a line of text** into a **tensor**
>  • Then you will **create a generator** to **feed data into the model**
>  • You will **train a neural network** in order to **predict the new set of characters** of 
> defined length.
>  • You will **use embeddings** for each character and **feed them as inputs** to your 
> model.
>  ▪ Many **natural language task**s rely on **using embeddings for predictions.**
>  • Your model will **convert each character to its embedding**, run the embeddings 
> through a **Gated Recurrent Unit GRU**, and **run it through a linear layer** to predict the next 
> set of characters.
>
> Đại khái là bài toán **predict một chuỗi kí tự** dựa trên **những kí tự
> trước đó,** qua đó học được **cách "chuẩn bị" chuỗi kí tự thành một
> tensor**, tạo một **generator để feed data vào model,** **xây dựng
> và train một GRU neural network** dùng **trax** cũng như là làm việc
> với **embedding**.

<br>

<a id="node-0sdkwit"></a>

<p align="center"><kbd><img src="assets/gzond0ns79m.png" width="80%"></kbd></p>

<br>

<a id="node-cloj7k0"></a>

> [!NOTE]
> The figure above gives you a summary of what you are about to implement.
>  • You will **get the embeddings**;
>  • **Stack the embeddings on top of each other**;
>  • Run them through **two layers** with a **relu activation** in the middle;
>  • Finally, you will **compute the softmax**.
>
> To predict the next character:
>
>  • **Use the softmax output** and **identify the word** with the **highest probability.**  • The word with the highest probability is the prediction for the next word.

<br>

<a id="node-fzl8u93"></a>

<p align="center"><kbd><img src="assets/7a04i3wtnxc.png" width="80%"></kbd></p>

<br>

<a id="node-u95ds0u"></a>

#### 1 - Importing the Data

<br>

<a id="node-sj0vgbz"></a>

#### 1.1 - Loading in the Data

<br>

<a id="node-rep0bkz"></a>

> [!NOTE]
> Now **import the dataset** and do some **processing**.
>  • The dataset has **one sentence per line.**
>  • You will be **doing character generation**, so you have to process each sentence 
> by **converting each character (and not word) to a number.**
>  • You will use the **ord** function to c**onvert a unique character** to a **unique integer 
> ID.**
>  • **Store** **each line** in a **list**.
>  • Create a **data generator** that takes in the **batch_size** and the **max_length**.
>  ▪ The **max_length** corresponds to the **maximum length of the sentence**.

<br>

<a id="node-cm604c2"></a>

<p align="center"><kbd><img src="assets/pctq1k9q1e.png" width="80%"></kbd></p>

> [!NOTE]
> **Define path** và **filename** để **open file, load data** bỏ
> đi khoảng trống đầu cuối câu và **add vào lines -
> dạng một list các sentence.**

<br>

<a id="node-xbiuo0d"></a>

<p align="center"><kbd><img src="assets/yy3fs9dwm0q.png" width="80%"></kbd></p>

> [!NOTE]
> **lowercase hết**, và chia ra thành **hai bộ**: **training**
> set và **validation** set. Validation set lấy **1000 item
> (sentence | text) cuối cùng** (**[-1000:]**) còn lại là training set.

<br>

<a id="node-ugcpl64"></a>

#### 1.2 - Convert a Line to Tensor

<br>

<a id="node-ljreyiw"></a>

<p align="center"><kbd><img src="assets/cz2reaurrjk.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ta sẽ **convert từng character thành
> number** dùng function **ord**() của Python
> giúp làm việc này. Nó sẽ **biến kí tự** thành
> **unicode integer tương ứng.**

<br>

<a id="node-uj3e203"></a>

#### Exercise 1 - line_to_tensor (UNQ_C1)

<br>

<a id="node-a4eknlu"></a>

> [!NOTE]
> **Instructions:** **Write a function** that **takes in a single line** and **transforms each character** 
> into **its unicode integer.** This returns **a list of integers**, which we'll refer to as a **tensor**.
>  • Use a **special integer** to represent the **end of the sentence** (the end of the line).
>  • This will be the **EOS_int** (end of sentence integer) parameter of the function.
>  • Include the **EOS_int** as the **last integer** of the
>  • For this exercise, you will **use the number 1** to **represent the end of a 
> sentence.**
>
> Đại khái là **viết một function** nhận một **single line of text** và "
> chuyển" **character của nó** thành **unicode** integer và **thêm một
> con số đặc biệt** đóng vai trò đại diện cho **End of Sentence**,
> mà ở đây sẽ dùng số **1**.

<br>

<a id="node-1gp886j"></a>

<p align="center"><kbd><img src="assets/ygr9tzscnp9.png" width="80%"></kbd></p>

<br>

<a id="node-st3oatt"></a>

#### 1.3 - Batch Generator

<br>

<a id="node-scmxodj"></a>

> [!NOTE]
> Most of the time in **Natural Language Processing**, and **AI** in general we use **batches** when 
> training our data sets. Here, you will **build a data generator** that **takes in a text** and 
> r**eturns a batch of text lines** (lines are **sentences**).
>
>  • The **generator** converts **text lines** (sentences) into n**umpy arrays of integers** 
> **padded by zeros** so that **all arrays have the same length**, which is the **length of the 
> longest sentence** in the entire data set.
>
> Once you create the generator, you can **iterate on it** like this:
> **next(data_generator)**
>
> This generator r**eturns the data** in a **format** that you could **directly use in your model** when 
> computing the **feed-forward of your algorithm**. This iterator returns a **batch of lines** and 
> **per token mask**. The batch is a tuple of three parts: **inputs**, **targets**, **mask**. The **inputs** and 
> **targets** are **identical**. The **second column** will be u**sed to evaluate your predictions**. **Mask 
> is 1 for non-padding tokens.**
>
> Đại khái là thường trong ML và NLP model sẽ "xử lý" từng batch nhiều training
> sample thay vì chỉ một mỗi lần. Mình sẽ viết một function đóng vai trò là một
> generator nhận một đoạn text và xử lý sao cho trả về nhiều list (arrays) các tensor,
> mỗi tensor như nói ở trên là một list các integer đại diện cho character mà bên trên ta
> đã làm. Function này sẽ dùng một keyword đặc biệt là yield thay vì return mà ta đã
> biết để có thể giống như trả kết quả về từng batch theo yêu cầu - cho phép có thể "
> iterate" trong function.
>
>
>
> Trong function, ta sẽ phải làm sao đó để các tensor có cùng chiều dài lấy bằng chiều
> dài của tensor dài nhất (câu dài nhất) trong dataset chính là input text (tức là function
> generator này sẽ nhận nguyên một bộ training dataset mà ta đã chuẩn bị ở trên ~
> sương sương hơn 100k lines). Các câu sẽ được padding (fill) với số 0 để đạt đủ
> chiều dài. Và tương ứng ta cũng sẽ trả về một cái mask - kiểu như một cái matrix
> bằng shape với batch of tensor mà ta trả ra nhưng chỗ nào là padding sẽ là 0, còn
> không phải padding sẽ là 1.

<br>

<a id="node-sc4fqhb"></a>

> [!NOTE]
> **Instructions:** Implement the data generator below. Here are some things you will need.
>  • **While True loop**: this will **yield one batch** at a time.
>  • **if index >= num_lines**, **set index to 0**.
>  • The generator should return **shuffled** batches of data. To achieve this **without 
> modifying the actual lines** a **list containing the indexes of data_lines** is created. This list 
> can be **shuffled** and **used to get random batches** everytime the index is reset.
>  • **if len(line) < max_length** **append line to cur_batch**.
>  ▪ Note that a line that has **length equal** to **max_length** should **not be appended** 
> to the batch.
>  ▪ This is because **when converting the characters into a tensor of integers**, an 
> **additional end of sentence token id will be added**.
>  ▪ So if max_length is 5, and a line has 4 characters, the tensor representing 
> those 4 characters plus the end of sentence character will be of length 5, which is the 
> max length.
>  • if **len(cur_batch) == batch_size**, go over every line, convert it to an int and 
> store it.
>  **Remember that when calling np you are really calling trax.fastmath.numpy which is 
> trax’s version of numpy that is compatible with JAX. As a result of this, where you 
> used to encounter the type numpy.ndarray now you will find the type 
> jax.interpreters.xla.DeviceArray.**

<br>

<a id="node-564z0a6"></a>

#### Exercise 2 - data_generator (UNQ_C2)

<br>

<a id="node-g10tra5"></a>

<p align="center"><kbd><img src="assets/86c764tgytn.png" width="80%"></kbd></p>

<br>

<a id="node-x9anhj5"></a>

<p align="center"><kbd><img src="assets/n0tnvuxzm3.png" width="80%"></kbd></p>

<br>

<a id="node-2r3blah"></a>

<p align="center"><kbd><img src="assets/pqx3ey0y6ir.png" width="80%"></kbd></p>

<br>

<a id="node-akgmvdx"></a>

<p align="center"><kbd><img src="assets/ecc8gysc7n9.png" width="80%"></kbd></p>

<br>

<a id="node-z40nrtx"></a>

> [!NOTE]
> Now that you have your generator, you can just call them and
> they will return tensors which correspond to your lines in
> Shakespeare. The **first column and the second column are
> identical**. Now you can go ahead and start building your
> neural network

<br>

<a id="node-62qjrpd"></a>

#### 1.4 - Repeating Batch Generator

<br>

<a id="node-sun0sir"></a>

> [!NOTE]
> The way the iterator is currently defined, it will **keep providing batches forever.**
>
> Although it is not needed, we want to show you the **itertools.cycle function** which is really 
> **useful when the generator eventually stops**
>
> Notice that **it is expected to use this function within the training function** further below
>
> Usually we want to **cycle over the dataset multiple times during training** (i.e. train for 
> **multiple \\/epochs**\\/).
>
> For small datasets we can use \\_**itertools.cycle**\\_ to achieve this easily.
>
> Chưa hiểu lắm đại khái là giới thiệu một cách tiện lợi để
> chạy qua / lướt qua dataset nhiều lần kiểu như nhiều
> epoches

<br>

<a id="node-twgye72"></a>

<p align="center"><kbd><img src="assets/5vd7u02dqh9.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái hiểu là giúp khi cycle
> qua dataset nhiều lần

<br>

<a id="node-3puagum"></a>

> [!NOTE]
> The purpose of using itertools.cycle in this context is to create an iterator that can
> provide  an infinite sequence of batches of data. The iterator keeps cycling through
> the provided data repeatedly, allowing for easy repetition of the dataset during
> training.
>
> In the given code, the infinite_data_generator is created using itertools.cycle. It
> takes the output of the data_generator function, which likely generates batches of
> data for training a machine learning model. By using itertools.cycle, the data
> generator is transformed into an infinite iterator.
>
> This is particularly useful when training a model for multiple epochs or repeatedly
> cycling over the dataset. During each iteration, the next function is called on the
> infinite_data_generator to retrieve the next batch of data. Since itertools.cycle
> ensures that the iterator keeps cycling indefinitely, it allows for seamless access to
> the dataset without explicitly handling the end of the data.
>
> The use of itertools.cycle **simplifies** the **process of iterating over the dataset** **multiple
> times**, especially when dealing with small datasets. It **eliminates t**he need to
> **manually reset or handle the end of the dataset**, making it **convenient** for **training
> functions** that **require repeated access to the data.**

<br>

<a id="node-tjyu99v"></a>

#### 2 - Defining the GRU Model

<br>

<a id="node-3shaos8"></a>

> [!NOTE]
> Now that you have the input and output tensors, you will go ahead
> and **initialize your  model**. You will be implementing the **GRULM**,
> **gated recurrent unit** model. To implement  this model, you will be
> using **google's trax package**. Instead of making you implement
> the GRU from scratch, we will give you the **necessary method**s
> from a build in package.  You can use the following packages
> when constructing the model:
>
> Rồi bây giờ đến build
> GRU model với trax

<br>

<a id="node-5w61x95"></a>

<p align="center"><kbd><img src="assets/yuj56iwq42.png" width="80%"></kbd></p>

> [!NOTE]
> Thì đại khái là ta sẽ dùng những cái này, đầu tiên là Serial layer giúp combine các layer serially
> (tuần tự) chỉ việc bỏ các layer vào, cách nhau bởi dấu phẩy. Còn ShiftRight thì man mán hiểu là
> giúp shift "chuyển dịch" input sentence qua bên phải 1 vị trí (default n_shifts = 1) bằng cách chèn
> số 0 vào trước, nhằm mục đích gì chưa hiểu lắm

<br>

<a id="node-5y0dbbz"></a>

<p align="center"><kbd><img src="assets/agw7fhlyrdd.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/n7zrnjrwug.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự bài toán tạo ra tên khủng long ở DLSpec. Nhưng ở đây ta
> không tự làm quá trình loop (forward) nên không làm như trong bài toán
> đó trong đó define **y<t> = x<t+1>** mà ta sẽ dùng **ShiftRight layer
> n_shifts = 1**. Nói **ngắn gọn lại** cho mục đích của việc này là **để
> model predict một time-step y^<t>** dựa vào **những từ / kí tự trước
> đó**. Do đó ban đầu (time-step 1, chưa có gì), thì đương nhiên phải input
> vào model (x<1>) để predict phải là "chưa có gì", tức x<t> phải = 0. Và ta
> làm vậy bằng cách insert một số 0 vào vị trí đầu của tensor x. Chứ nếu
> không ShiftRight hoá ra model predict lại nhận / dựa vào chữ đầu tiên để
> predict ra chữ đầu tiên à? (Như trong tên khủng long, nhận chữ d rồi
> predict chữ d thì rõ ràng là không đúng)

<br>

<a id="node-45but53"></a>

<p align="center"><kbd><img src="assets/c1m8u9i2hyt.png" width="80%"></kbd></p>

<br>

<a id="node-en2warw"></a>

#### Exercise 3 - GRULM (UNQ_C3)

<br>

<a id="node-y77jf6d"></a>

<p align="center"><kbd><img src="assets/gy6y4sifj1a.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3bowe16mz1.png" width="80%"></kbd></p>

> [!NOTE]
> Define một GRU network, lí do **Dense layer có n_units = vocab_size**
> là vì cái này là họ kiểu như nói trước (hướng dẫn) về bài toán dự đoán kí
> tự / generate chuỗi kí tự trong P.A. tương tự như trong bài toán generate
> tên khủng long của DLSpec, trong đó ta tạo một RNN học các pattern
> trong tên khủng long bằng một bộ data tên khủng long. để khi training
> xong, sampling từ model để có tên khủng long mới để mà đặt cho một
> loại khủng long mới phát hiện.
>
>
>
> Và **activation z<t> của mỗi time-step tính từ hidden state là một vector
> có size bằng vocab size** (cho dù là bài toán ở cấp kí tự, cũng gọi là
> vocab size), **gọi là logit.**
>
>
>
> Và **cái softmax tính với z<t> sẽ cho ra output y<t>**, đương nhiên là
> một **vector dài vocab size, chứa các chỉ số probability score của các kí
> tự**, để rồi cái nào có **p cao nhất sẽ là cái được chọn.** Thì ở đây, **họ
> còn cho z<t> qua một Fully Connected layer trước khi qua softmax** nên
> có thể hiển **độ dài của output từ F.C layer cũng phải bằng vocab size,**
> do đó **số hidden unit của F.C (hay Dense) layer cũng bằng vocab size
> là vậy**.

<br>

<a id="node-apdgxcj"></a>

<p align="center"><kbd><img src="assets/2j6ia8cjwg5.png" width="80%"></kbd></p>

<br>

<a id="node-20l6inf"></a>

#### 3 - Training

<br>

<a id="node-w2qu3yp"></a>

> [!NOTE]
> Now you are **going to train your model**. As usual, you have to **define the cost function**, the
> **optimizer**, and **decide whether you will be training it** on a **gpu** or **cpu**. You also have to **feed in a
> built model**. Before, going into the training, we re-introduce
> the **TrainTask** and **EvalTask** **abstractions** from the **last week's assignment.**
>
> To train a model on a task, Trax defines an **abstraction** t**rax.supervised.training**.**TrainTask** which
> **packages the train data, loss and optimizer (among other things) together into an object.**
>
> Similarly to evaluate a model, Trax defines an abstraction **trax.supervised.training.EvalTask** which
> **packages the eval data and metrics** (among other things) into another object.
>
> The final piece tying things together is the **trax.supervised.training.Loop abstraction** that is a very
> **simple and flexible** way to **put** **everything together** and train the model, all the while **evaluating it
> and saving checkpoint**s. Using **training.Loop** will **save you a lot of code** compared to always
> **writing the training loop by hand**, like you did in **courses 1 and 2.** More importantly, you are **less
> likely to have a bug** in that code that would **ruin your training**
>
> Đại khái là nhắc lại những **cái abstraction TrainTask, EvalTask** giúp **đóng gói
> training/evaluation data, optimizer và loss** lại thành một **object**, và **Loop giúp
> handle phần training loop, save checkpoint..**. t**hay vì phải tự viết giúp giảm
> nguy cơ bug.**

<br>

<a id="node-x7l2bka"></a>

> [!NOTE]
> An **epoch** is traditionally defined as **one pass through the dataset.**
>
> Since the **dataset was divided in batches** you need **several steps (gradient
> evaluations)** in order to complete an epoch. So, one epoch corresponds to the
> **number of examples in a batch** times the **number of steps**. In short, in **each
> epoch** you **go over all the dataset.**
>
> The **max_length** variable defines the **maximum length of lines** to be used in
> training our data, **lines longer than that** length **are discarded.**
>
> Below is a function and results that indicate **how many lines conform to our
> criteria of maximum length** of a sentence **in the entire dataset** and **how many
> steps are required in order to cover the entire dataset** which in turn corresponds
> to an **epoch**..
>
> Đại khái là nói lại về **định nghĩa của một epoch** là sao, nó là **một lần loop qua
> hết toàn bộ training** data. Vì **bộ data chia thành nhiều batch**, trong đó **model
> sẽ xử lý từng batch và gradient descent update**, nên **một epoch là bằng số step
> (tức là số batch) nhân với số training data trong batch**. Ở đây đại khái là **viết
> function tính thử xem sẽ có bao nhiêu batch / hay bao nhiêu step trong toàn bộ
> dataset**, vì ta không dùng toàn bộ dataset mà **bỏ đi những câu dài hơn
> max_len** (phần tạo generator có làm) khi tính function này phải trừ đi những câu
> dài hơn max_lenght

<br>

<a id="node-z4wucxu"></a>

<p align="center"><kbd><img src="assets/ozp7aqb9ef.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ batch_size = 4.

<br>

<a id="node-jsyn4or"></a>

<p align="center"><kbd><img src="assets/i8s703qv15.png" width="80%"></kbd></p>

<br>

<a id="node-kz53uph"></a>

#### 3.1 - Training the Model

<br>

<a id="node-tx4rvq6"></a>

<p align="center"><kbd><img src="assets/rk6zyypqm.png" width="80%"></kbd></p>

<br>

<a id="node-y8sbjbp"></a>

#### Exercise 4 - train_model (UNQ_C4)

<br>

<a id="node-ym12thi"></a>

<p align="center"><kbd><img src="assets/980lqb55n1t.png" width="80%"></kbd></p>

<br>

<a id="node-7463y3p"></a>

<p align="center"><kbd><img src="assets/24w1ss82zz1.png" width="80%"></kbd></p>

<br>

<a id="node-sm3w9pc"></a>

<p align="center"><kbd><img src="assets/so7eerggr8.png" width="80%"></kbd></p>

<br>

<a id="node-2t7rsby"></a>

#### 4 - Evaluation

<br>

<a id="node-xugb90t"></a>

<p align="center"><kbd><img src="assets/br71k4vfp5f.png" width="80%"></kbd></p>

<br>

<a id="node-1oo4nhi"></a>

#### 4.1 - Evaluating using the Deep Nets

<br>

<a id="node-zw7yqq9"></a>

#### Exercise 5 - test_model (UNQ_C5)

<br>

<a id="node-40aszuj"></a>

<p align="center"><kbd><img src="assets/i9bu6199i9d.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu thấy khó hiểu, xem lại Lab
> trước, đã giải thích rất rõ

<br>

<a id="node-t7xgh5j"></a>

<p align="center"><kbd><img src="assets/pm901hde0oc.png" width="80%"></kbd></p>

<br>

<a id="node-zignqte"></a>

#### 5 - Generating the Language with your Own Model

<br>

<a id="node-0ssuw3z"></a>

<p align="center"><kbd><img src="assets/d5vg8clo96m.png" width="80%"></kbd></p>

<br>

<a id="node-4d4jfb3"></a>

<p align="center"><kbd><img src="assets/je4z5r13fh.png" width="80%"></kbd></p>

> [!NOTE]
> In the generated text above, you can see that the model
> generates text that **makes sense capturing dependencies
> between words and without any input.** A **simple n-gram
> model would have not been able to capture all of that in
> one sentence.**

<br>

<a id="node-5c30gby"></a>

<p align="center"><kbd><img src="assets/5s6nxrsrgo3.png" width="80%"></kbd></p>

<br>

<a id="node-albpr3l"></a>

<p align="center"><kbd><img src="assets/q478u69r88e.png" width="80%"></kbd></p>

<br>

<a id="node-s04dq4u"></a>

<p align="center"><kbd><img src="assets/8afviqljor7.png" width="80%"></kbd></p>

<br>

<a id="node-bdjk89w"></a>

<p align="center"><kbd><img src="assets/elvmvc7kh0a.png" width="80%"></kbd></p>

<br>

<a id="node-wek2cbt"></a>

<p align="center"><kbd><img src="assets/0emg7ttwb05n.png" width="80%"></kbd></p>

<br>

<a id="node-l8ospin"></a>

<p align="center"><kbd><img src="assets/jfenayyx81o.png" width="80%"></kbd></p>

<br>

<a id="node-hxoimn3"></a>

> [!NOTE]
> in the predict() function above, why don't we use the max probability to
> get the next character?
>
> ChatGPT
>
> In the predict() function, the max probability is not used directly to select
> the next character because the goal is to introduce randomness and
> diversity in the generated text. By using Gumbel sampling instead of
> directly choosing the maximum probability, the generated text becomes
> less deterministic and more varied.
>
> If the maximum probability were always chosen, the generated text
> would be more predictable and repetitive. The Gumbel sampling process
> adds randomness by considering the probabilities along with the Gumbel
> noise, controlled by the temperature parameter. This randomness allows
> the model to explore different possibilities and generate more diverse
> text.
>
> In essence, Gumbel sampling with the temperature parameter provides
> a way to balance between exploration and exploitation. Higher
> temperatures result in more exploration and randomness, while lower
> temperatures make the sampling process more focused on exploiting the
> highest probabilities.
>
> By using Gumbel sampling instead of relying solely on the maximum
> probability, the generated text becomes more interesting and less
> predictable, capturing a broader range of possibilities and allowing for
> more creative outputs.

<br>

<a id="node-77wkkhc"></a>

> [!NOTE]
> is is  the similar 'random sampling with distribution" technique?
>
> ChatGPT
>
> Yes, Gumbel sampling with temperature can be considered a form of
> random sampling with a specific distribution. In this case, the
> Gumbel distribution is used as the underlying distribution for
> sampling. Random sampling with distribution involves drawing
> samples from a given probability distribution. In the case of Gumbel
> sampling, the goal is to sample from a categorical distribution. The
> Gumbel distribution is utilized to introduce randomness and
> exploration in the sampling process. The Gumbel distribution is often
> used to model extreme values and is defined by its shape and
> location parameters. By transforming uniform random numbers
> through the Gumbel distribution, Gumbel sampling allows us to
> select a category or item from a categorical distribution in a
> probabilistic manner. The temperature parameter in Gumbel
> sampling controls the level of randomness in the sampling process.
> Higher temperatures lead to more diverse and random samples,
> while lower temperatures make the sampling process more focused
> and deterministic. Therefore, Gumbel sampling with temperature can
> be seen as a form of random sampling with the Gumbel distribution,
> where the temperature parameter determines the level of exploration
> and randomness in the generated samples.

<br>

<a id="node-qgpcxwr"></a>

#### Summary

<br>

<a id="node-tz05whi"></a>

> [!NOTE]
> **On statistical methods** 
> Using a **statistical method** like the one you implemented in **course 2** will **not give you 
> results that are as good.** Your model will **not be able to encode information seen 
> previously in the data set** and as a result, the **perplexity will increase**. Remember from 
> course 2 that the **higher the perplexity, the worse your model** is. Furthermore, **statistical 
> ngram models** take up t**oo much space and memory**. As a result, it will be **inefficient** and 
> too **slow**. Conversely, with **deepnets, you can get a better perplexity**. Note, l**earning about 
> n-gram language models is still important** and allows you to better understand deepnets.
>
> Đại khái là những **statistical method như N-gram ở course 2** **không đạt kết quả
> tốt** được như này. Vì nó **không nắm bắt và "nhớ" được thông tin mà nó gặp ở
> trước đó**, dẫn tới **perplexity cao**, đồng nghĩa **model tệ**. Ngoài ra nó còn **đòi hỏi
> nhiều memory** nên **không hiệu quả** và chạy **chậm**. Còn với **Deep Net**, những
> **vấn đề này được cải thiện đáng kể**. Tuy vậy ổng nói **việc hiểu về các statistical
> model** đóng vai trò **quan trọng** trong việc **giúp ta hiểu hơn về Deepnet**

<br>

