# Course 2 - Improving Deep Neural Networks:
hyperparams Tuning, Regularization & Optimization

📊 **Progress:** `103` Notes | `302` Screenshots

---
<a id="node-6jutbu9"></a>

## Course 2 - Improving Deep Neural Networks:
hyperparams Tuning, Regularization & Optimization

<br>

<a id="node-6nlzefh"></a>

## C2w1_practical Aspects Of Deep Learning

<br>

<a id="node-w3thbyc"></a>

### Setting Up Your Machine Learning Application

<br>

<a id="node-og9haaf"></a>

#### Train Dev Test Sets

<br>

<a id="node-3u2um6t"></a>

##### 1 The course is about practical aspects of deep learning and making neural network
work well by \\*optimizing hyperparameters\\*, \\*data setup\\*, and optimization \\*algorithms\\*.

2 Deep learning has been successful in various areas including \\*natural language
processing\\*, \\*computer vision\\*, \\*speech recognition\\*, structured data, computer security,
and logistics.

3 Intuitions from one application area \\*do not always transfer to another\\*, and it is difficult
to guess the best choice of \\*hyperparameters\\* on the first attempt.

4 Applied deep learning is an\\* iterative process\\* where \\*setting up data sets efficiently\\* can
help make progress quicker.

5 The workflow of training deep learning algorithms involves \\*training on a training set,\\*
using a \\*dev set\\* or hold-out cross-validation set to \\*choose the best model\\*, and \\*evaluating\\*
the final model on a \\*test set\\* for an \\*unbiased estimate\\* of its performance.

6 In the previous era of machine learning, a \\*70/30\\* train-test split was widely considered
best practice, but in the modern \\*big data\\* era, different rules of thumb are required.

<br>

<a id="node-ldtkvzt"></a>

<p align="center"><kbd><img src="assets/34tb9xoxvyh.png" width="80%"></kbd></p>

> [!NOTE]
> And what I've seen is that intuitions from one domain or from one
> application area often **do not transfer** to other application areas. And the
> best choices may **depend on the amount of data** you have, the
> **number of input features** you have through your **computer
> configuration** and whether you're training on **GPUs** **or CPUs**. And if
> so, exactly what **configuration** of GPUs and CPUs...and many other things.
>
> Even **very experienced** deep learning people find it almost **impossible** to
> correctly guess the **best choice of hyperparameters** the very first time. And
> so today, applied deep learning is a very **iterative process** where you
> just have to **go around this cycle many times** to hopefully **find a good
> choice of network** for your application

<br>

<a id="node-p9np8rr"></a>

<p align="center"><kbd><img src="assets/5a2rat2ecuv.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là hồi xưa data ít thì chia 7/3/3 còn nay thì thường chỉ 98/1/1 là đủ

<br>

<a id="node-9es8zgv"></a>

<p align="center"><kbd><img src="assets/rnrw1p03plk.png" width="80%"></kbd></p>

> [!NOTE]
> Đv vấn đề mismatched train/test đại khái là training set và test set
> có feature khác nhau. Ví dụ ảnh để train thì dùng ảnh chất lượng
> cao còn ảnh để test thì lại do user upload lên có chất lượng kém.
> Lời khuyên / nguyên tắc tối thượng là
>
>
>
> '**Make sure the dev & test come from the same distribution"**
>
>
>
> Cụ thể trong trường hợp này thì phải dùng web images để  train
> còn user upload image để cross validation + test
>
> Cái nữa là không nhất thiết phải có test sét vì
> thật ra nó chỉ đóng vai trò 'công bố' tỉ lệ đúng
> của model 1 cách khách quan. Nếu không có
> nhu cầu này thì ko cần test set.

<br>

<a id="node-86gpmqi"></a>

#### Bias / Variance

<br>

<a id="node-lggdt2m"></a>

##### 1 Good machine learning practitioners have a \\*sophisticated understanding\\* of \\*bias\\* and
\\*variance\\*.

2 Bias and Variance is e\\*asily learned\\* but \\*difficult to master.\\*

3 In Deep Learning area, there is\\* less discussion\\* of the \\*Bias/Variance trade-off.\\*

4 Bias and variance are visualized through a 2D example in which a straight line represents
underfitting, an overly complex curve represents overfitting, and a medium complexity curve
represents a reasonable fit.

5 High dimensional problems require metrics such as the \\*train set error\\* and the \\*development
set error\\* to \\*understand bias and variance\\*.

6 \\*High variance\\* is determined when an algorithm performs \\*well on the training set\\* but \\*poorly
on the development set\\*.

7 \\*High bias\\* is determined when an algorithm is \\*not performing well on the training set\\* and
\\*does not fit the data well\\*.

8 \\*High bias\\* and \\*high variance\\* occur when an algorithm is \\*not performing well on the training\\*
set and \\*does not generalize well to the development set.\\*

9 Low bias and low variance occur when an algorithm is \\*performing well on the training set\\*
and \\*generalizes well to the development set\\*.

10 Analyzing bias and variance is predicated on the \\*assumption\\* that the \\*optimal error is
nearly 0%\\*.

<br>

<a id="node-en4uatx"></a>

<p align="center"><kbd><img src="assets/4a9bwdbyg6g.png" width="80%"></kbd></p>

> [!NOTE]
> Vấn đề là đv 2D thì còn plot được, còn nhiều D hơn
> thì phải có cách khác để nhận biết vấn đề overfitting

<br>

<a id="node-4jwwyq1"></a>

<p align="center"><kbd><img src="assets/f0g6yg52xej.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là những nhận định trên phải giả định **Bayes error** là 0%.
> Chứ nếu lớn hơn, ví dụ như 14%, thì 15% của training error không
> phải là high bias.
>
>
>
> Và thực tế nhiều vấn đề Bayes error ko phải là 0%

<br>

<a id="node-lp2b91f"></a>

<p align="center"><kbd><img src="assets/zqpfn09rrjc.png" width="80%"></kbd></p>

> [!NOTE]
> Optimal (Bayes) error là gì?

<br>

<a id="node-f9eze73"></a>

<p align="center"><kbd><img src="assets/23jxg6oumhy.png" width="80%"></kbd></p>

<br>

<a id="node-yoysb7b"></a>

#### Basic Recipe For Machine Learning

<br>

<a id="node-4ag62nr"></a>

##### 1 The \\*basic\\* \\*recipe\\* for training a neural network involves \\*diagnosing\\*
whether the algorithm has \\*high bias or high variance\\*.

2 If there is a \\*high bias\\*, solutions could be \\*adding more hidden layers,\\*
\\*more hidden units,\\* or training it for a\\* longer time.\\* One could also try
different neural network \\*architectures\\* to see if there' s a better-suited
one for the problem at hand.

3 If there is a \\*high variance\\*, adding \\*more data\\* is the best solution, if
possible. If not, \\*regularization\\* or trying a \\*different\\* neural network
architecture could help.

4 Selecting the \\*appropriate solution\\* for the problem is \\*essential\\*. If one
has a \\*high bias\\* problem, getting \\*more data \\*is \\*not\\* always the most
efficient solution.

5 \\*Deep learning\\* has made it easier to reduce bias and variance without
necessarily increasing the other.

<br>

<a id="node-kx83c0l"></a>

- **Sure, here's a more detailed answer with indexed style:

In the previous video, the concept of bias and variance in machine learning
algorithms was introduced. These concepts can help diagnose issues with
an algorithm's performance and guide improvements.

When training a neural network, a basic recipe can be used. After an \\*initial
model is trained\\*, the following steps can be taken:

Determine if the algorithm has \\*high bias\\* by evaluating its performance on the
training set. If high bias is detected, try \\*increasing the complexity\\* of the
network, training for a \\*longer period of time\\*, using \\*more advanced
optimization\\* algorithms, or experimenting with \\*different\\* neural network
\\*architectures\\*. Continue trying these approaches until bias is reduced to
acceptable levels, as indicated by \\*good performance on the training set.\\*

Once bias is under control, evaluate the algorithm for \\*high variance\\* by
looking at its performance on the \\*development set.\\* If high variance is
detected, try \\*getting more data,\\* using \\*regularization\\* techniques, or
experimenting with \\*different neural network architectures\\*. Continue trying
these approaches\\* until both bias and variance are at acceptable levels\\*. The
set of approaches to try will depend on whether the algorithm has a bias or
variance problem. It is \\*important to be clear\\* about \\*which type of problem\\* is
present to select the m\\*ost useful approaches\\* to try.

In the past, there was a \\*bias-variance tradeoff\\* where \\*reducing one type of
error could increase the other\\*. However, in the era of deep learning and big
data, it is possible to reduce bias or variance without hurting the other type of
error as much. Increasing the size of the network and getting more data are
both effective approaches for reducing error without introducing the tradeoff.

The basic recipe for machine learning presented in the video provides a
\\*systematic approach\\* to improving algorithm performance. By \\*understanding\\*
the b\\*ias-variance tradeoff\\* and \\*selecting appropriate approaches\\* to try, it is
possible to drive down b\\*oth types of error\\* and achieve good performance.**

> [!NOTE]
> Quy trình

<br>

<a id="node-s7t63bo"></a>

<p align="center"><kbd><img src="assets/1mqlr71humw.png" width="80%"></kbd></p>

> [!NOTE]
> High bias -> 
> - Dùng bigger (more complex) network
> - Train longer
> - Different NN architecture (sẽ nói sau)
>
>
>
> High variace: 
> - Train in more data
> - Regularization
> - Different NN architecture
>
> Đv vấn đề **trade off giữa bias vs variance** thì đại khái là ổng nói
> **ngày xưa thô**i còn với modern n.n thì nếu có **nhiều data** (fix
> issue high variance) + dùng **big network** (fix issue high bias) thì
> không hề có chuyện phải trade of giữa bias và variance. Có
> chăng là '**computational time**'. Và đây chính là **ưu điểm quan trọng**
> rất lớn của N.N giúp nó phát triển mạnh

<br>

<a id="node-35uienl"></a>

### Connect With Your Mentors And Fellow Learners On Discourse!

<br>

<a id="node-4nsq573"></a>

### Regularizing Your Neural Network

<br>

<a id="node-3lqubm4"></a>

#### Clarification About Upcoming Regularization Video

<br>

<a id="node-kcnp7su"></a>

##### ...

<br>

<a id="node-3z65sj1"></a>

<p align="center"><kbd><img src="assets/u7w8d1f4bm.png" width="80%"></kbd></p>

<br>

<a id="node-z66uox7"></a>

#### Regularization

<br>

<a id="node-exij5d6"></a>

##### 1 \\*Regularization\\* is a technique used to \\*prevent overfitting\\* or \\*reduce variance\\* in neural
networks.

2 One common way to perform regularization is by \\*adding a regularization term\\* to the \\*cost
function\\* of the network.

3 The most common type of regularization is \\*L2 regularization\\*, which \\*adds a term to the
cost function\\* that is proportional to the \\*squared norm of the weight parameters\\* of the
network.

4 \\*L1 regularization\\* is an alternative to \\*L2 regularization\\* that adds a term proportional to the
\\*absolute value of the weight parameters\\* instead of their squared value. This can \\*make the
weight vector sparse\\*, but it is \\*not as commonly used as L2\\* regularization.

5 The\\* regularization parameter\\*, \\*lambda\\*, is used to control the strength of the regularization
and is \\*typically set using a development set\\* or cross-validation.

6 Regularization is used \\*not only in logistic regression\\* but also in \\*neural networks\\*, where
the regularization term is added to the cost function for all the parameters in the network.

7 L2 regularization in neural networks adds a term proportional to the \\*squared norm\\* \\*of all
the weight parameters\\* in the network.

8 Lambda is a hyperparameter that needs to be tuned for regularization to work effectively.

<br>

<a id="node-3uuovzd"></a>

<p align="center"><kbd><img src="assets/iqebhql4ynd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ôn lại để regularize **Logistic Regression**, add thêm 1
> R**eg term** bằng **(lambda/2m)* tổng bình phương các weight**
> nếu là L2, nếu là L1 thì **(lambda/2m)*tổng giá trị tuyệt đối của
> weight.**
>
>
>
> Mà đối với L2, tổng bình phương các weight chính là **bình
> phương của norm** (gọi là L2 norm, **Frobenius norm**) của
> vector W (=[w1,w2..wn])
>
>
>
> Make weight vector W **sparse** đại khái là **w_j bị set = 0** khiến
> **vector hay matrix W có nhiều chỗ 0 gọi là sparse**, **còn L2 thì
> nó chỉ ém w về gần bằng 0 thôi**
>
>
>
> Weight decay chính là cách gọi khác của L2 regularization

<br>

<a id="node-y7u8yh2"></a>

<p align="center"><kbd><img src="assets/prjr6a5gmaq.png" width="80%"></kbd></p>

> [!NOTE]
> **"Frobenius norm"** The Frobenius norm is a matrix norm that defines
> the magnitude of  a matrix. It is defined as the **square root of the sum
> of the squares  of all the elements of a matrix**. In other words, it
> calculates the **L2  norm of a matrix**. It is commonly used in linear
> algebra and in the  training of machine learning models, particularly in
> deep learning. In the context of deep learning, the **Frobenius norm** of
> the weight  matrix of a layer is often used as a **regularization term** to
> **encourage** the model to have **small weights**, which helps to prevent
> **overfitting** and improve the **generalization** performance of the model.
> The Frobenius norm is also used to measure the **similarity between
> two matrices**, by calculating the distance between the two matrices.
>
>
>
> **"Weight decay"** Weight decay is a regularization technique used in
> training machine learning models, especially neural networks, to
> p**revent overfittin**g  and improve the generalization performance of the
> model. It works  by **adding a penalty term to the loss function** that is
> proportional to  the magnitude of the model weights. **This penalization
> discourages  the model from having too high weights**, which reduces
> the  magnitude of weights and therefore the complexity of the model,
> leading to a better generalization to unseen data. **The term weight
> decay is often used interchangeably** with **L2 regularization.**
>
> Tương tự trong NN cũng add **regularization term** vào **cost function**
> bằng **tổng bình phương tất cả các weight của toàn network** nhân với
> lambda/2m. Khi triển khai ra chút xíu thì được kiểu như khi update w thì
> nhân w với 1 hệ số bằng (**1 - alpha.lambda/m)** nhỏ hơn 1 nên **khiến
> w nhỏ lại** một chút (trước khi update với derivative (- alpha*dJ/dw) lại
> gọi là **weight decay**

<br>

<a id="node-85jt7ht"></a>

- **1 What is overfitting and how can it be addressed?  2 If your neural network is overfitting your data, that means
it's fitting the training data too well and not generalizing to new, unseen data. One of the main ways to address
overfitting is through regularization, which helps to reduce variance in the network.

3 What is regularization and how does it work?  4 Regularization is a technique used to prevent overfitting by
adding a penalty term to the cost function. In logistic regression, for example, this penalty term is lambda/2m
times the squared L2 norm of the weight vector w. The lambda term is the regularization parameter that needs
to be tuned using a development set or cross-validation.

5 What is L2 regularization?  6 L2 regularization is the most common type of regularization used in practice. It
works by adding a penalty term to the cost function that is proportional to the squared L2 norm of the weight
vector w. The effect of L2 regularization is to shrink the weight vector towards zero, which reduces variance in
the network.

7 Why is L2 regularization applied only to the weight vector and not to the bias term?  8 The weight vector w
usually has many more parameters than the bias term b, especially in high-dimensional problems where
overfitting is more likely to occur. Therefore, adding regularization to w has a greater effect on reducing
variance than adding regularization to b.

9 What is L1 regularization?  10 L1 regularization is another type of regularization that works by adding a
penalty term to the cost function that is proportional to the L1 norm of the weight vector w. Unlike L2
regularization, L1 regularization tends to produce sparse weight vectors with many zero entries, which can help
with model compression.

11 Why is L2 regularization more commonly used than L1 regularization?  12 L2 regularization is used much
more often than L1 regularization in practice because it has been shown to produce better generalization
performance in many cases. However, L1 regularization may be useful in certain situations where model
sparsity is important.

13 How is regularization applied to a neural network?  14 In a neural network, regularization can be applied by
adding a penalty term to the cost function that is proportional to the squared L2 norm of all the weight matrices
in the network. The regularization parameter lambda needs to be tuned using a development set or
cross-validation.

15 What is the formula for the squared L2 norm of a matrix?  16 The squared L2 norm of a matrix is defined as
the sum of the squares of all its elements. For a weight matrix w with dimensions n[l] x n[l-1], where l is the
layer number, the formula for the squared L2 norm is lambda/2m * sum(i=1 to n[l-1], j=1 to n[l]) w[i,j]^2.

17 How is the lambda parameter represented in Python?  18 Lambda is a reserved keyword in Python, so in
the programming exercises, l-a-m-b-d is used instead to represent the lambda regularization parameter.**

<br>

<a id="node-zlpwmml"></a>

#### Why Regularization Reduces Overfitting?

<br>

<a id="node-3q1nxef"></a>

##### 1 \\*Regularization\\* helps with \\*overfitting\\* and r\\*educing variance\\* problems.

2 The addition of an \\*extra term\\* \\*penalizes weight matrices\\* from being \\*too large\\*.

3 By cranking up \\*lambda\\*, which is the \\*regularization parameter\\*, the weights will be
\\*closer to zero\\* and it will \\*simplify the network\\*, making it \\*less prone to overfitting\\*.

4 If the \\*regularization parameter\\* is large, the \\*weights are small\\*, and the activation
function is \\*tanh\\*, then each layer will be \\*roughly linear\\* and the \\*whole network will
compute a linear function\\*.

5 The network will be computing something \\*not too far from a big linear function,\\*
which is a simple function, rather than a complex highly non-linear function, making
it \\*less able to overfit\\*.

6 Implementational tip: when implementing regularization, the cost function J is
modified by adding an extra term that penalizes the weights being too large.

<br>

<a id="node-mm67qka"></a>

<p align="center"><kbd><img src="assets/hlm2ktyu67l.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tương tự như tác dụng của Reg đ/v các algorithm
> khác thì đv N.N cũng vậy nó sẽ **'ÉM' (penalize)** cho các các
> **params w không thể lớn được thậm chí gần = 0**, từ đó nó
> khiến cho model trở nên **simple** hơn (trong lecture  ổng nói vẽ
> vậy là có ý như w ở các hidden layer thành gần 0 hết dẫn đến
> model nó **'dần trở nên như 1 linear regression model'**. Nhưng
> thực tế không phải w nó bằng 0 mà là nó trở nên nhỏ đi nên giảm
> độ ảnh hưởng đến model.
>
> Penalize có nghĩa là phạt hoặc trừng phạt. Trong
> khoa học máy  tính, từ này thường được sử dụng
> để miêu tả việc thêm một điều  kiện giới hạn hoặc
> hạn chế cho một mô hình trong quá trình huấn
> luyện, để tránh overfitting và cải thiện hiệu suất tổng
> quát của mô hình.

<br>

<a id="node-lhnpmzm"></a>

<p align="center"><kbd><img src="assets/c7465ldgc3.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu sét **lambda lớn** để Regularization tác dụng
> mạnh **ém weight nhỏ xuống** thì vì z = wa + b, **z cũng sẽ
> nhỏ lại**
>
>
>
> vì thế a = g(z) mà g thường là tanh, sigmoid, hay relu thì **đều
> có tính chất 'LINEAR' trong đoạn z nhỏ**. Hiểu đại khái là sẽ
> **khiến toàn bộ hệ thống trở nên linear hơn** -> **tăng độ bias,
> giảm tính variance.**
>
> Và khi dùng Regularization thì nhớ add RegTerm
> khi tính J nếu không sẽ không thấy J giảm khi
> Iteration Gradient Descent
>
> Ví dụ ổng lấy hàm tanh cho thấy nếu z trong
> khoảng nhỏ quanh 0, thì g(z) sẽ gần như tuyến
> tính. Đối với sigmoid cũng tương tự.

<br>

<a id="node-nz081cf"></a>

- **1 Why does regularization help with overfitting?   2 Regularization helps with overfitting by
adding an extra term to the cost function that penalizes large weight values. This penalty
term encourages the model to use simpler, more generalizable patterns instead of complex,
overfitting ones.

3 Why does it help with reducing variance problems?  4 Reducing variance in a model
means making it less sensitive to small changes in the training data. Regularization achieves
this by shrinking the weights towards zero, making the model more robust and less prone to
overfitting.

5 Intuition behind regularization: simplified neural networks  6 Regularization can be thought
of as reducing the complexity of the neural network by shrinking the weights towards zero.
This can result in a simpler network that is less prone to overfitting. In the extreme case
where the regularization parameter is very large, the weights are effectively zeroed out,
resulting in a much simpler network.

7 Intuition behind regularization: impact on activation functions  8 Regularization can also
affect the activation functions used in the network. For example, with the tanh activation
function, small weights will result in small values for the input to the activation function. This
can cause the activation function to behave more like a linear function, resulting in a simpler,
more interpretable model.

9 Implementational tip: debugging gradient descent with regularization  10 When
implementing gradient descent with regularization, it's important to plot the training and
validation error as a function of the regularization parameter. This can help determine the
optimal value of the regularization parameter that balances bias and variance in the model.**

<br>

<a id="node-uyd7hgg"></a>

#### Dropout Regularization

<br>

<a id="node-gzp1sa6"></a>

##### 1 \\*Dropout\\* is a \\*powerful regularization technique\\* to \\*prevent over-fitting\\* in neural
networks.

2 Dropout involves \\*randomly setting some nodes to zero\\* during training, which
results in a much \\*smaller network\\*.

3 By training on smaller networks for each example, the network can be
\\*regularized\\*.

4 There are \\*different ways\\* to implement dropout, with the most common being
the \\*inverted dropout technique\\*.

5 \\*Inverted dropout \\*involves generating a \\*random matrix\\* with a \\*probability of
eliminating hidden units\\*, \\*element-wise multiplying the activation matrix by the
dropout matrix\\*, and \\*scaling up the output.\\*

6 Inverted dropout helps to \\*avoid reducing the expected value of the output \\*while
regularizing the network, regardless of the keep probability value used.

<br>

<a id="node-kbq9sng"></a>

<p align="center"><kbd><img src="assets/3n4b7buoys2.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái cách làm này là với **mỗi lần train** từ 1 bộ
> dataset ta sẽ **randomly bỏ bớt một số hidden unit**

<br>

<a id="node-gdz2bw7"></a>

<p align="center"><kbd><img src="assets/d0vyw32rd2.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái nó sẽ tạo matrix d3 cùng shape với a3, nhưng mỗi item là 1 - true.
> 0 - false trong đó **khả năng 1 - true là 80%  khả năng 0 - false là 20%.
> Gọi là keep-prob = 0,8**
>
>
>
> a3 = **np.multiply(a3, d3)** sẽ bỏ bớt unit (set = 0)
>
>
>
> Cuối cùng là lấy a3 = **a3 / 0.8** đại khái là để **cho nó lớn lên lại** để nó
> **'not change the expected value'**

<br>

<a id="node-qjrez0m"></a>

<p align="center"><kbd><img src="assets/j4q4w38g61a.png" width="80%"></kbd></p>

> [!NOTE]
> Lúc prediction thì đừng có drop out

<br>

<a id="node-0wv9gy0"></a>

- **Sure, I'd be happy to provide more detail with indexed main ideas.  1 Dropout regularization:  2 In
addition to L2 regularization, dropout is another powerful technique for regularization in neural
networks. Dropout is a regularization technique that randomly sets activations to zero during the
training process to prevent overfitting.

3 Applying dropout to a neural network:  4 When applying dropout, we go through each of the
layers of the network and set a probability of eliminating a node in the neural network. For each
node in each layer, we toss a coin with a 50/50 chance of keeping or eliminating the node. If a
node is eliminated, we remove all the outgoing connections from that node, resulting in a much
smaller network. We then train this much smaller network using backpropagation.

5 Training with different neural networks:  6 For each training example, we train it using one of
these neural networks that we obtain after eliminating nodes with dropout. We repeat this
process for each training example, resulting in different neural networks for each example.

7 Implementing dropout using inverted dropout:  8 There are a few ways to implement dropout,
but the most common technique is called inverted dropout. Inverted dropout involves creating a
random matrix with the same shape as the layer's activations, where each element of the matrix
has a certain probability of being set to zero.

9 Keep probability:  10 This probability, also known as keep.prob, determines the probability of
keeping each node in the layer. For example, if keep.prob is set to 0.8, there is a 20% chance of
eliminating any given node.

11 Scaling up activations:  12 We then take the activations from the layer and multiply them
element-wise with the random matrix created using the keep.prob value. This has the effect of
zeroing out a certain percentage of the activations. We then scale up the resulting activations by
dividing them by the keep.prob value, which ensures that the expected value of the activations is
maintained.

13 Benefits of dropout:  14 Using dropout can help to prevent overfitting by reducing the
interdependence of the neurons in the network, forcing them to learn more robust features.
Dropout has been shown to be a highly effective regularization technique and is widely used in
deep learning.**

<br>

<a id="node-qmf5z43"></a>

#### Clarification About Upcoming Understanding Dropout Video

<br>

<a id="node-3amqhqd"></a>

##### ...

<br>

<a id="node-1ml0wew"></a>

<p align="center"><kbd><img src="assets/54z1ysvx92x.png" width="80%"></kbd></p>

<br>

<a id="node-k93i2ze"></a>

#### Understanding Dropout

<br>

<a id="node-b6fj6sl"></a>

##### 1 Dropout is a \\*regularization\\* technique that randomly knocks out units in a neural
network, giving the effect of working with a \\*smaller network\\*, which can \\*prevent
overfitting\\*.

2 Dropout \\*shrinks the squared norm of the weights\\* by \\*spreading out the weights\\*,
which is similar to \\*L2 regularization\\*.

3 The L2 penalty on different ways can be different depending on the size of the
activation being multiplied into that way, making dropout an adaptive form of L2
regularization.

4 To implement \\*dropout\\*, a \\*keep-prop\\* is chosen, which is the \\*chance of keeping a
unit in each layer\\*, and it is feasible to \\*vary keep-prop by layer\\* to reduce overfitting.

5 It is possible to \\*apply dropout to the input layer\\*, but it is \\*less common in practice\\*.

6 Dropout is frequently used in c\\*omputer visio\\*n due to the\\* large input sizes\\* and lack
of data, but should \\*only be used if overfitting occurs.\\*

7 The \\*downside\\* of using dropout is that it introduces \\*additional hyperparameters\\* to
search for using cross-validation, and it is important to consider \\*which layers are
most prone to overfitting.\\*

<br>

<a id="node-63srvxu"></a>

<p align="center"><kbd><img src="assets/0wywuob35gh.png" width="80%"></kbd></p>

> [!NOTE]
> Apply d**ifferent Keep-Prob cho layer khác nhau,** layer nào **nhiều
> unit** -> **độ overfitting cao** thì cho **K.P nhỏ** (Để dropout nhiều)
> và ngược lại.
>
>
>
> Hay dùng trong Computer Vision (do dễ bị overfitting)
>
>
>
> Downside: Đại khái là J ko còn được define tốt nữa dẫn đến **ko đo
> lường sự giảm của J** được (trong quá trình G.D vẽ ra **learning
> curve.**  Nên đại khái ổng nói là ổng sẽ **turn off D.O để make sure J
> giảm dần rồi sau đó mới mở lên.**
>
>
>
> "So you lose this **debugging tool** to have a plot a draft like this. So
> what I usually do is **turn off drop out** or if you will **set keep-propped
> = 1** and run my code and make sure that it is monitored quickly
> decreasing J. And then **turn on drop out**"
>
> Đại khái là vì các feature (ý là input vào một layer, chính là output của layer
> trước) có thể biến mất tuỳ hứng nên các hidden unit nó sẽ học cách' không
> phụ thuộc vào 1 feature nào mà sẽ **'spreading out the weights'**

<br>

<a id="node-iiz6wy1"></a>

- **1 What is dropout?  2 Dropout is a regularization technique used in neural networks to
prevent overfitting. It randomly drops out or "knocks out" units in the network on each
iteration, effectively creating a smaller network.

3 How does dropout work as a regularizer?  4 Dropout works as a regularizer by preventing
units from relying too heavily on any one feature, forcing them to spread out their weights and
not overfit to specific patterns in the data. This leads to a shrinking effect on the squared
norm of the weights, similar to the effect of L2 regularization. In fact, dropout can be shown to
be an adaptive form of L2 regularization, where the penalty on different weights varies
depending on the size of the activation being multiplied into that weight.

5 What is the intuition behind dropout from the perspective of a single unit?  6 The intuition
behind dropout from the perspective of a single unit is that, for a unit to do its job, it needs to
generate a meaningful output based on its inputs. However, with dropout, inputs can get
randomly eliminated, meaning that any one feature could go away at random. This makes the
unit reluctant to put too much weight on any one input, and instead, it spreads out its weights
and gives a little bit of weight to each of the inputs. This, in turn, has a regularizing effect on
the network.

7 How can the keep prop be varied by layer when implementing dropout?  8 The keep prop,
which is the chance of keeping a unit in each layer, can be varied by layer when
implementing dropout. For example, in a network with three input features and seven hidden
units, the first weight matrix (W1) would be 7x3, the second (W2) would be 7x7, and the third
(W3) would be 3x7, and so on. The keep prop can be set to a lower value for layers where
you worry more about overfitting and a higher value for layers where you worry less about
overfitting. In practice, a keep prop of 1.0 is common for the input layer, where you want to
keep all the features.

9 What are some implementation tips for using dropout?  10 Some implementation tips for
using dropout include:  • Using dropout only if you're worried about overfitting  • Varying the
keep prop by layer to apply a more powerful form of dropout to layers with more parameters  •
Applying dropout to the input layer only if needed, with a keep prop close to 1.0  • Being
mindful of the hyperparameters involved in using dropout and using cross-validation to find
the best values  • Being aware that dropout is commonly used in computer vision
applications, but it can also be used in other areas where overfitting is a concern.**

<br>

<a id="node-chwb7sg"></a>

#### Other Regularization Methods

<br>

<a id="node-phgyxas"></a>

##### 1 Introduction to regularization techniques in neural networks

2 \\*Data augmentation\\* as a regularization technique, including
flipping and cropping images to create new examples

3 \\*Early stopping\\* as a technique to prevent overfitting by stopping
the training process early

4 How early stopping works by selecting a mid-size parameter value
for the neural network

5 Downside of using early stopping and \\*separating optimization and
regularization\\* tasks in machine learning.

<br>

<a id="node-jdadqpp"></a>

<p align="center"><kbd><img src="assets/cvimmrv9pm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tạo thêm data thì sẽ giảm Overfitting

<br>

<a id="node-m8vr6yp"></a>

<p align="center"><kbd><img src="assets/wyysdfwl2rc.png" width="80%"></kbd></p>

> [!NOTE]
> **Early stoping:**
> Pros**: Chỉ chạy G.D rồi quyết định stop để lấy ra W.b
> Cons: V**i phạm phương pháp MỖI LẦN 1 VIỆC - 
> **Orthogonalization**: Tức là Tập trung giảm J hoặc tập trung 
> giảm Overfitting -> Nó phải hy sinh việc tìm ra W, b sao cho J min 
> để đánh đổi việc không bị overfitting
>
>
>
> **L2_Reg** 
> Pros Cứ Train cho đã đời mà ko sợ (Overfiting)
> Cons: là phải chọn **lambda** -> More computational expensive

<br>

<a id="node-l46k7lt"></a>

- **Sure, here's a more detailed answer, still using indexed style:  1 Regularization techniques: In addition
to L2 regularization and dropout, there are other techniques for reducing overfitting in neural networks.
One such technique is data augmentation, which involves adding synthetic training examples to the
dataset by applying random transformations to existing examples, such as flipping an image
horizontally or taking random crops. This can help to make the training set less redundant and provide
more variety for the model to learn from. Another technique is early stopping, which involves
monitoring the validation error as the model is trained and stopping the training process when the
error stops improving or starts to increase. This can help to prevent the model from overfitting to the
training data by finding the best point at which to stop training.

2 Data augmentation: Data augmentation is a technique for creating additional training examples by
applying random transformations to existing examples in the dataset. For example, flipping an image
horizontally or taking random crops can help to provide more variety for the model to learn from. This
technique can be especially useful when it's difficult or expensive to obtain more data. However, it's
important to use transformations that are relevant to the problem at hand, such as flipping a cat image
horizontally but not vertically.

3 Early stopping: Early stopping is a technique for preventing overfitting by monitoring the validation
error as the model is trained and stopping the training process when the error stops improving or
starts to increase. This helps to find the best point at which to stop training and prevent the model
from overfitting to the training data. However, it's important to be aware of the potential downsides of
early stopping, such as the need to choose an appropriate stopping point and the potential for
increased computational cost.

4 Choosing regularization techniques: When choosing regularization techniques for a neural network,
it's important to consider the trade-off between reducing bias and reducing variance. L2 regularization
can help to reduce variance by penalizing large weights, while dropout can help to reduce variance by
randomly dropping out units during training. Data augmentation can also help to reduce variance by
providing more variety for the model to learn from. On the other hand, early stopping can help to
reduce variance by finding the best point at which to stop training, but may also increase bias if the
model is not allowed to train for long enough.

5 Separating optimization and regularization: One approach to machine learning is to separate the
tasks of optimization and regularization. In this approach, the focus is on finding the best values of the
weights and biases that minimize the cost function, without considering methods for reducing
overfitting. After optimizing the cost function, regularization techniques such as L2 regularization,
dropout, or data augmentation can be applied to reduce overfitting. This can simplify the process of
choosing among the space of possible algorithms and hyperparameters, making machine learning
easier to understand and implement.**

<br>

<a id="node-lgfuf6o"></a>

### Setting Up Your Optimization Problem

<br>

<a id="node-1jnhobo"></a>

#### Normalizing Inputs

<br>

<a id="node-2gvb0ez"></a>

##### 1 \\*Normalizing inputs\\* can \\*speed up\\* neural network training.

2 The normalization process involves \\*subtracting the mean\\* and \\*normalizing
the variances\\* of the input features.

3 It is important to \\*use the same normalization parameters\\* for both \\*training\\*
and \\*test\\* sets.

4 Normalizing input features helps to ensure that the\\* cost function\\* is more
\\*symmetric\\* and \\*easier to optimize\\*.

5 Features should be on \\*similar scales\\* to avoid \\*elongated cost functions\\* and
\\*slow gradient descent\\*.

6 Normalizing features is especially important when the \\*input features\\* come
from \\*dramatically different scales.\\*

7 Normalization generally \\*does not harm performance\\*, and is often \\*beneficial
in speeding up\\* training.

8 There are other techniques to speed up neural network training that will be
discussed in the next section.

<br>

<a id="node-mjtskwp"></a>

<p align="center"><kbd><img src="assets/d10hx7qvx0e.png" width="80%"></kbd></p>

<br>

<a id="node-0qg9ur8"></a>

<p align="center"><kbd><img src="assets/hslwdsolush.png" width="80%"></kbd></p>

<br>

<a id="node-td3w1a0"></a>

- **ure, here's a more detailed answer:

1 Normalizing Inputs: When training a neural network, one technique to speed up the training is
to normalize your inputs. This involves two steps:

2 a. Subtract out or zero out the mean: This step involves calculating the mean of the input
features using the formula mu = 1/m * sum(x_i) and subtracting it from each training example, so
x_i becomes x_i - mu.

3 b. Normalize the variances: In this step, the variance of each feature is calculated using the
formula sigma^2 = 1/m * sum(x_i^2) and then each example is divided by this vector sigma. This
ensures that each feature has equal variance and results in a more symmetric cost function.

4 Importance of Normalizing Inputs: Normalizing inputs is important because if the features are
on very different scales, it's more likely that the cost function will be elongated and the
parameters will take on very different values. This results in a more difficult optimization problem,
and the gradient descent algorithm may take a lot of steps before it finds the minimum.
Normalizing the inputs ensures that the cost function is more symmetric, and gradient descent
can go straight to the minimum without oscillating around.

5 When to Normalize Inputs: Normalizing inputs is particularly important when the features come
from very different scales, such as one feature ranging from 1-1000 and another from 0-1.
However, performing this type of normalization typically doesn't harm the training algorithm, and
it's often done regardless of the feature scales. If the features come in on similar scales, such as
all ranging from -1 to 1, then this step is less important, but it can still be helpful in speeding up
training.

6 Consistency in Normalization: When normalizing the training data, it's important to use the
same mu and sigma to normalize the test set. This ensures that the data goes through the same
transformation, and the test set is scaled in the same way as the training set.

7 Other Techniques to Speed up Training: There are other techniques to speed up training of
neural networks, such as:  8 a. Using an appropriate learning rate  9 b. Using early stopping to
prevent overfitting  10 c. Regularization to prevent overfitting  11 d. Using dropout to prevent
overfitting  12 e. Using batch normalization to stabilize training  13 f. Using a better optimization
algorithm such as Adam, RMSProp, or Adagrad.**

<br>

<a id="node-869wj20"></a>

#### Vanishing / Exploding Gradients

<br>

<a id="node-9aj4ajo"></a>

##### 1 The problem of data \\*vanishing\\* and \\*exploding\\* gradients in deep neural
networks

2 The effect of \\*weight initialization\\* on the vanishing and exploding
gradients

3 Mathematical explanation of the effect of weight initialization on the
output Y and activations A

4 The intuition behind the \\*exponential increase\\* or \\*decrease\\* of activations
with a very deep network

5 The similar exponential increase or decrease of gradients as \\*a function
of the number of layers\\*

6 The difficulty of training when gradients are exponentially smaller or
larger than L

7 The partial solution to the problem of vanishing and exploding gradients:
\\*careful choice of weight initialization\\*

<br>

<a id="node-k4ghtm8"></a>

<p align="center"><kbd><img src="assets/1o6e4ycp4rg.png" width="80%"></kbd></p>

> [!NOTE]
> **Vanishing and Exploding Gradients:**
> Chữ **gradient** ý muốn nói 'Sự thay đổi của the output of the model
> do sự thay đổi của tham số' (the change in the output of a model 
> with respect to a change in its weights)
>
>
>
> **Vanishing** **gradient** ý nói khi gradient quá nhỏ khiến cho model
> update rất chậm, khiến quá trình training rất chậm thậm chí dừng
> luôn.
>
>
>
> **Exploding** **gradient** thì ngược lại, khiến model update quá nhanh, 
> khiến kết quả không stable.
>
>
>
> Một số giải pháp là dùng hàm activation khác như **Relu, Tanh** và **initialization**
>
> I - Identity matrix **[1 0; 0 1]**
>
>
>
> Đại khái ổng giả sử 1 NN như vầy, coi như không dùng activation function
> - g(z) = z và bỏ qua b giả thì triển khai ra  được y^ là = W[L] (W[L-1]**(L-1))X  (giả sử thêm W của
> hidden unit bằng nhau)
>
>
>
> Ý muốn nói có nghĩa là y^ sẽ là một function theo số mũ L Từ đó nếu W của hidden unit nhỏ hơn
> Identity matrix 1 chút ví dụ như 0.5 0; 0 0,5 thì y^ sẻ nhỏ đi theo cấp luỹ thừa của L tức là sẽ rất rất
> nhỏ
>
>
>
> Ngược lại nếu W của hidden unit lớn hơn một chút, thì y^ sẽ lớn theo cấp luỹ thừa
>
>
>
> Thì ý ổng là tương tự như như ở đây lấy việc **tính activation qua các layer** ra để minh hoạ thì với
> g**radient nó cũng vậy**, từ đó tạo ra hiện tượng **exploding gradient** và **vanishing gradient**

<br>

<a id="node-spevj24"></a>

<p align="center"><kbd><img src="assets/1rjypn4p9ic.png" width="80%"></kbd></p>

<br>

<a id="node-iveb4nz"></a>

- **1 The problem of vanishing and exploding gradients: When training a very deep neural network,
the derivatives or slopes of the network can sometimes get very small or very large, making
training difficult. This is known as the problem of vanishing and exploding gradients.

2 Weight initialization and its impact on the problem: Careful choices of random weight
initialization can significantly reduce the problem of vanishing and exploding gradients.

3 The structure of a neural network: A neural network has layers and hidden units, and each
layer has weight matrices W1, W2, W3, etc. The output Y is the result of a multiplication of all
the weight matrices and the input X.

4 Linear activation function and biases: In the video, the activation function used is a linear
function and the bias is ignored to simplify the calculation.

5 The impact of weight matrices on activations: If each weight matrix is slightly larger than 1
times the identity matrix, the activations will increase exponentially as a function of the number
of layers L. On the other hand, if each weight matrix is slightly smaller than the identity matrix,
the activations will decrease exponentially.

6 The impact of weight matrices on gradients: The same argument can be used to show that the
derivatives or gradients of the network will also increase or decrease exponentially as a function
of the number of layers.

7 The difficulty of training deep networks: If the activations or gradients increase or decrease
exponentially as a function of the number of layers, it can make training difficult, especially if the
gradients become exponentially smaller than L.

8 Partial solution to the problem: Careful choice of weight initialization can help to alleviate the
problem of vanishing and exploding gradients, but it doesn't completely solve the problem.

9 Importance of weight initialization: Weight initialization is an important aspect of training neural
networks and can have a significant impact on the success of the training.

10 Conclusion: Vanishing and exploding gradients can be a significant problem when training
deep neural networks, but careful weight initialization can help to mitigate the problem.**

<br>

<a id="node-k2sgwdx"></a>

#### Weight Initialization For Deep Networks

<br>

<a id="node-8fekh3v"></a>

##### 1 Problem of vanishing and exploding gradients in very deep neural networks

2 Partial solution is a better or more \\*careful choice of random initialization\\* for
the neural network

3 Example of initializing weights for a single neuron

4 Generalizing to deep networks

5 Setting \\*variance of weights\\* to \\*prevent z from blowing up\\* or becoming \\*too
small\\*

6 Setting weight matrix W for a certain layer to \\*np.random.randn\\* times \\*square
root of 1 over the number of features\\* that are fed into each neuron in layer l

7 Using a variance of \\*2/n\\* for \\*ReLu\\* activation function, and \\*1/n\\* for TanH
activation function

8 Different initialization formulas: \\*Xavier\\* initialization and \\*Yoshua Bengio's\\*
formula

9 The \\*variance\\* parameter can be tuned with \\*hyperparameters\\*

10 Importance of choosing a\\* reasonable scaling for weight initialization\\* to avoid
exploding or vanishing gradients

11 The trick can help neural networks trained much more quickly

<br>

<a id="node-apjt3ys"></a>

<p align="center"><kbd><img src="assets/nplplwtodq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ini weight randomly nhưng nhân thêm (element-wise) với:
>
>
>
> random(...)*sqrt(**2/số feature = unit của layer trước**)  (**2/fan_in**)
>
>
>
> thì cái này có tên là **He (hoặc Klaiming) - initialization**, work tốt 
> với reLU, LeakyReLU, ELU, GELU, Swish, Mish.. 
> Do ông **Kaiming He** phát minh (Ageron p.360)
>
>
>
> Nếu activation là None, tanh, softmax thì dùng Glorot /Xavier initilization:
> thay term trong sqrt bằng **1/fan_average**
>
>
>
> với fan là chỉ số feature vào hoặc ra một layer:
> nên fan_average là 0.5(số unit layer trước + số unit layer này)
>
>
>
> Chỗ này ông Andrew bị nhầm, Xavier phải là 1/fan_avg = 2/(n[l-1]+n[l])
> mới đúng ổng chỉ cái trên là sai.
>
>
>
> Cái trên **1/fan_in** là **LeCun** initialization work tốt đv **SELU** (Ageron)
>
> Nói chung là các công thức ini He/Kaiming - Glorot / Xavier - LeCun khác nhau
> chút đỉnh ở cái term trong dấu sqrt và mỗi cái sẽ work tốt tuỳ activation function.

<br>

<a id="node-q3ar2wd"></a>

- **Sure, here is a more detailed summary of the video:

1 The video discusses the problem of vanishing and exploding gradients in deep neural networks,
where the gradients of the loss function with respect to the weights become either too small or too
large, leading to slow or unstable learning.

2 One partial solution to this problem is to use \\*better weight initialization techniques\\*, which can help
\\*control the scale\\* of the \\*activations\\* \\*and\\* \\*gradients\\* throughout the network.

3 To understand weight initialization, the video starts with the example of a single neuron, where the
input features are multiplied by weights and summed up to produce an activation value, which is then
passed through an activation function to produce an output.

4 To prevent the activation values from becoming too large or too small, it is desirable to \\*set the
variance of the weights to an appropriate value\\*. In particular, if the number of input features is large,
the weights should be \\/\\*scaled down by a factor proportional to the square root of the number of input
features\\*\\/, in order to keep the activation value from growing too large.

5 For a \\*deep neural network\\* with multiple layers, the same principle applies, but with the number of
input features replaced by the \\*number of units in the previous layer\\*. Specifically, the variance of the
weights for each layer should be \\/\\*scaled down by a factor proportional to the square root of the
number of units in the previous layer.\\*\\/

6 The video notes that this initialization technique works particularly well with \\*ReLU\\* activation
functions, and that a scaling factor of 2/n (rather than 1/n) should be used for ReLU in order to
achieve better performance.

7 \\*Other activation functions\\* may require different initialization techniques. For example, the \\*Tanh\\*
activation function may require a \\*scaling factor of 1/sqrt(n) instead of 2/sqrt(n)\\*, which is known as the
\\*Xavier initialization\\*.

8 In practice, the \\*variance of the weights \\*can be \\*adjusted by a hyperparameter\\*, which can be \\*tuned\\*
to achieve better performance on a \\*particular task.\\*

9 Overall, \\*weight initialization\\* is an important technique for improving the \\*stability\\* and \\*efficiency\\* of
deep learning, and should be carefully considered when designing and training deep neural networks.**

<br>

<a id="node-5u25w8k"></a>

#### Numerical Approximation Of Gradients

<br>

<a id="node-uew5ihg"></a>

##### 1 Backpropagation implementation requires testing to ensure
correctness

2 Numerically approximating computations of gradients helps
build up to gradient checking

3 Two-sided difference gives a better approximation of the
gradient than a one-sided difference

4 Formal definition of a derivative is f of theta plus epsilon minus f
of theta minus epsilon over 2 epsilon

5 Error of approximation is on the order of epsilon squared for the
formal definition and on the order of epsilon for the two-sided
difference

6 Two-sided difference is preferred for gradient checking, even
though it runs twice as slow as one-sided difference

<br>

<a id="node-e7oezph"></a>

<p align="center"><kbd><img src="assets/p4kzayr6ner.png" width="80%"></kbd></p>

> [!NOTE]
> Khúc cuối ổng nói đại khái là vầy, có 2 cách tính gần đúng 
> giá trị (**dJ/dθ**) để thực hiện việc Gradient Checking - So sánh giá
> trị gần đúng của dJ/dθ (or dJ/dw, dJ/db) với kết quả của 
> Gradient descent để đảm bảo G.D đang chạy đúng )
>
>
>
> Thì dùng '**2 side difference approximation**' sẽ chính xác hơn 
> là **1-side difference approximation**
>
> Đại khái là check xem (trong quá trình backprop) gradient
> mình tính có đúng không (đây là đ.v việc tự backprop chứ
> làm bằng Keras thì khỏi bàn)
> Cách làm là so sánh dJ/dtheta với 'gần đúng của dJ/dtheta) tính bằng
> [ J(theta+epsilon)-J(theta-epsilon) ] / 2*epsilon
>
>
>
> Ổng lấy ví dụ hàm J(theta) = theta***3 -> dJ/dtheta = 3*theta**2
> thì giả dụ với theta = 1 thì tính bằng gần đúng sẽ ra
> 3.0001 gần bằng với 3*1**2 = 3.
>
>
>
> Đại khái là ổng minh hoạ việc tính ra term gần đúng của dj/dtheta
> sẽ gần bằng dj/dtheta lúc Backprop.
>
>
>
> Còn về cách tính thì nhìn hình là hiểu:
> dJ/dtheta (derivative / đạo hàm của hàm J w.r.t theta) chính là hệ số
> góc của tiếp tuyến với hàm J tại theta (=tang của góc bởi tiếp tuyến
> và phương ngang) -> thì góc này có thể tính gần đúng bằng
> góc dưới của tam giác màu xanh lá.

<br>

<a id="node-xs083vf"></a>

<p align="center"><kbd><img src="assets/h8fhwjz43ii.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là 1 cái thì error giảm (về không) với 1 tốc
> độ tỉ lệ thuận với bình phương của epsilon nên
> nhanh hơn cái kia chỉ tỉ lệ thuận với epsilon nên
> cái đầu chính xác hơn

<br>

<a id="node-vru25d1"></a>

- **1 When implementing \\*backpropagation\\*, it's important to \\*check that your implementation is
correct.\\*

2 One way to do this is through\\* gradient checking\\*, which involves \\*approximating the gradient of
a function numerically\\*.

3 To approximate the gradient, you can \\*nudge\\* the\\* input variable\\* (e.g. \\*theta\\*) by a \\*small amount\\*
(e.g. \\*epsilon\\*) to get two new values of the function (\\*f(theta+epsilon) and f(theta-epsilon)\\*).

4 You can then compute the height of a larger triangle using these two values, which provides a
more accurate estimate of the gradient.

5 This method involves taking a\\* two-sided difference\\*, rather than a \\*one-sided difference\\*, which
leads to \\*greater accuracy\\* in the approximation.

6 The approximation \\*error for the two-sided difference\\* is on the order of \\*epsilon squared\\*, which
is much smaller than the \\*error for the one-sided difference\\* (which is on the order of \\*epsilon\\*).

7 When doing gradient checking, it's important to use the more accurate two-sided difference
method, even though it may be slower.

8 The formal definition of the derivative involves taking the limit of the difference quotient as
epsilon approaches zero.

9 The approximation error for a non-zero value of epsilon is on the order of epsilon squared.

10 The two-sided difference method involves computing f(theta+epsilon) and f(theta-epsilon),
which provides a \\*better approximation of the gradient\\* and \\*reduces the approximation error.\\***

<br>

<a id="node-rdtaoex"></a>

#### Gradient Checking

<br>

<a id="node-hsbj4yp"></a>

##### 1 Gradient checking is a technique to debug and verify the correctness of back
propagation implementations in neural networks.

2 To implement gradient checking, the first step is to \\*reshape all the network
parameters into a giant vector theta.
\\*
3 The cost function J is then expressed as a \\*function of theta.\\*

4 Next, all the \\*derivatives\\* of the cost function with respect to the network
\\*parameters\\* are also \\*reshaped into a giant vector d theta\\*.

5 To perform gradient checking, a \\*loop\\* is implemented for \\*each component of
theta\\*, where a two-sided difference is taken for each component of theta.

6 The \\*difference is then divided by 2 epsilon\\* to \\*approximate\\* the partial
derivative of J with respect to that component of theta.

7 The approximation for each component is then computed for every value of i.

8 The d\\*ifference between the approximation and the actual derivative\\* is then
computed u\\*sing the Euclidean distance formula\\*.

9 If the \\*difference is very smal\\*l (i.e., less than\\* 10^-7\\*), the derivative
approximation is l\\*ikely correct.\\*

10 If the difference is larger, it is possible that there is a bug in the
implementation, and the individual components of d theta should be checked to
locate the source of the problem.

<br>

<a id="node-agqf4ra"></a>

<p align="center"><kbd><img src="assets/0hrxjs1yl8lc.png" width="80%"></kbd></p>

<br>

<a id="node-43lz4rw"></a>

<p align="center"><kbd><img src="assets/qhrq2hla7n.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dùng '2-side difference approximation' để tính ra vector
> **d(θ_approx)** rồi so sánh xem nó có **gần bằng** với **d(θ)** 
> hay không
>
>
>
> Check bằng công thức trong hình.
>
> "So when implementing a neural network, what often happens is 
> I'll implement foreprop, implement backprop. And then I might find 
> that this grad check has a relatively **big value**. And then I will 
> suspect that there **must be a bug**, go in **debug, debug, debug**. 
> And after debugging for a while, If I find that it **passes grad 
> check with a small value**, then you can be much **more 
> confident** that it's then correct."
>
> Loop trong vector **Θ** chứa toàn bộ params **θ_i**, để tính  **dθ_i
> approx** - giá trị approximation của dJ w.r.t từng θ_i,  mỗi cái tính bằng
> công thức đã biết:
>
>
>
> **dθ_i = [J(θ_i + epsilon) - J(θ_i - epsilon)] / 2*epsilon**
>
>
>
> Bỏ vào để ra vector **dΘ_approx**
>
>
>
> So sánh: Không phải là so từng cái mà là so cả vector **dΘ_approx** với
> **dΘ** (cái này là từ backprop) bằng cách dùng **Euclidean norm** (còn
> gọi là L2 norm) của **hiệu 2 vector này**. 
>
>
>
> Tức là tính norm của **dΘ_approx - dΘ**
>
> Công thức tính L2 norm là bằng square root của tổng bình phương các
> element trong vector.
>
>
>
> Với cách tính này kiểu như **sqrt của tổng bình phương các sai  lệch**
> giữa **dθ_i approx** và **dθ_i** vậy
>
>
>
> So sánh sai lệch này nếu nhỏ hơn 10^-7 thì ok tự tin là tính derivative
> đúng

<br>

<a id="node-1x1va2r"></a>

<p align="center"><kbd><img src="assets/u04rlrdwhi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/pxzrsxjsypg.png" width="80%"></kbd></p>

<br>

<a id="node-yfmz6fh"></a>

- **Sure, I'd be happy to provide a more detailed answer for you!

1 Gradient checking is a technique used to debug and verify the implementation and
\\*backpropagation\\* process in a neural network. It can \\*save a lot of time\\* and help identify
bugs in implementations.

2 To implement gradient checking, the first step is to \\*take all the network parameters\\*, such
as W1, B1, etc., and \\*reshape them into a giant parameter vector called theta\\*. This
involves \\*reshaping all the W's into vectors\\* and \\*concatenating\\* them with the other
parameters.

3 Next, the \\*cost function J is transformed into a function of theta\\*. The derivatives, such as
dW[1], db[1], etc., are then \\*reshaped into a giant vector called d theta\\*.

4 To implement gradient checking, \\*a loop\\* is used to compute \\*d theta approx I\\* for each
component of theta. This involves taking a two-sided difference of J of theta by nudging
theta I up and down by a small amount (epsilon) and computing the difference between
these values.

5 The two resulting vectors, \\*d theta approx\\* and \\*d theta\\*, are then compared to check if they
are approximately equal. This is done by computing the \\*Euclidean distance between the
vectors\\* and \\*normalizing it by the lengths of the vectors\\*.

6 A good value for \\*epsilon\\* is around \\*10^-7\\*, and if the formula gives a value of 10^-7 or
smaller, the derivative approximation is likely correct. \\*If it is around 10^-5, it's worth
double-checking the components of the vector\\*. If it is l\\*arger than 10^-3\\*, there may be a
\\*bug somewhere\\*, and it's important to investigate individual components of d theta to try
and track down the source of the problem. Overall, gradient checking is an important
technique for debugging and verifying neural network implementations, and can help save
time and prevent bugs in the backpropagation process.**

<br>

<a id="node-93gkrjn"></a>

#### Gradient Checking Implementation Notes

<br>

<a id="node-h37aon2"></a>

##### 1 Gradient checking is a \\*useful tool for debugging\\* neural networks.

2 Grad check \\*should not be used during training\\*, only for \\*debugging\\*.

3 If an algorithm \\*fails grad check\\*, look at \\*individual components to identify the
bug.\\*

4 Remember to \\*include regularization when using grad check.\\*

5 \\*Dropout\\* is difficult to use with \\*grad check because of its randomness\\*.

6 \\*Turn off dropout\\* when using \\*grad chec\\*k to double check correctness.

7 It is possible that implementation of backpropagation is \\*correct\\* \\*only when
weights and biases are close to 0\\*.

8 It is recommended to \\*run grad check\\* at \\*random initialization\\* and \\*after some
training\\*.

9 Week 1 materials covered setting up train, dev, and test sets, analyzing bias
and variance, regularization, and gradient checking.

10 The programming exercise in week 1 will allow for the application of these
concepts.

<br>

<a id="node-rk963ir"></a>

<p align="center"><kbd><img src="assets/opyzxkcy4x.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là so sánh thấy sai khác lớn là biết có bug rồi
> thì bấy giờ ta sẽ **xem xét đơn lẻ dw, db so với dθ [i]** 
> Giả sử thấy dw thì gần bằng còn db thì khác chứng tỏ sai
> đâu đó chỗ db. Nói chung là nó sẽ giúp **khoanh vùng bug**
>
>
>
> Nhớ add **Regularization** term khi tính J (tính J để tính 
> numerical_gradient)
>
>
>
> **Tắt Dropout** khi làm Gradient Checking vì nó khiến 
> tính toán J sai. Làm G.C xong thì bật lên lại
>
> "It is not impossible, rarely happens, but it's not impossible
> that  your implementation of gradient descent is **correct
> when w and b  are close to 0, so at random initialization**.
> But that as you run  gradient descent and w and b become
> bigger, maybe your  implementation of backprop is correct
> only when w and b is  close to 0, but it **gets more inaccurate
> when w and b become large**. So one thing you could do, I
> don't do this very often, but one thing  you could do is **run
> grad check at random initialization** and then  train the
> network for a while so that w and b have some time  to
> wander away from 0, from your small random initial values. "
>
>
>
> Đại khái là có thể (dù hiếm) xảy ra là back-prop chạy đúng
> khi W, b nhỏ ~0 còn khi nó lớn hơn 0 thì lại sai. Do đó ý ổng
> nói là ồng hay run grad check khi ini xong  rồi train một thời
> gian cho w, b nó thay đổi khỏi 0 thì grad-check lại

<br>

<a id="node-ny0qyph"></a>

<p align="center"><kbd><img src="assets/vg9htu80149.png" width="80%"></kbd></p>

<br>

<a id="node-moznzu9"></a>

<p align="center"><kbd><img src="assets/sh1kv6cwlgo.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là run G.C khi ini (ban
> đầu) và khi đã train 1 lúc

<br>

<a id="node-45vexja"></a>

- **1 In this video, the speaker shares some \\*practical tips\\* and \\*notes\\* on implementing
gradient checking for a neural network.

2 One of the tips is to only use gradient checking for \\*debugging\\* and \\*not during
training\\*. This is because computing d theta approx i for all values of i is a slow
computation. Instead, backprop should be used to compute d theta for implementing
gradient descent.

3 If an algorithm \\*fails grad check\\*, the speaker advises to look at the \\*individual
components to identify the bug\\*. By \\*examining the different values of i\\*, the location of
the bug can be determined. For example, if the values of theta or d theta are very far
off, all corresponding to dbl for some layer, the bug might be in how the derivative with
respect to parameters b is being computed.

4 Another tip is to \\*remember the regularization term when doing grad check\\*. If
regularization is being used in the cost function, it's \\*important to include \\*that term in
the calculation of d theta.

5 \\*Dropout\\* cannot be easily checked with grad check because in every iteration,
dropout \\*randomly eliminates different subsets of hidden unit\\*s. This makes it difficult to
compute the cost function J that dropout is doing gradient descent on. Therefore, grad
check should be \\*implemented without dropout\\*, and dropout should be turned on
afterwards.

6 It's possible that the implementation of backprop may be \\*correct\\* \\*only\\* when w and b
are\\* close to 0\\* and become more \\*inaccurate as w and b become larger.\\* To address
this, the speaker \\*suggests running grad check at random initialization\\* and then
training the network for a while before r\\*unning grad check again\\*.

7 Overall, the video covers a range of topics, including setting up train, dev, and test
sets, analyzing bias and variance, applying different forms of regularization, and
gradient checking. These concepts are further elaborated in the week's programming
exercise.**

<br>

<a id="node-m6dt3eg"></a>

### Quiz

<br>

<a id="node-at81en9"></a>

<p align="center"><kbd><img src="assets/ypddu3vr0p.png" width="80%"></kbd></p>

<br>

<a id="node-t6hinur"></a>

<p align="center"><kbd><img src="assets/0u2917tsru5.png" width="80%"></kbd></p>

<br>

<a id="node-fydzcd7"></a>

<p align="center"><kbd><img src="assets/bb5hcg4tsv6.png" width="80%"></kbd></p>

<br>

<a id="node-tu75oqp"></a>

<p align="center"><kbd><img src="assets/4umoeomltkv.png" width="80%"></kbd></p>

<br>

<a id="node-1hxxwny"></a>

<p align="center"><kbd><img src="assets/n7ay2a5m5h7.png" width="80%"></kbd></p>

<br>

<a id="node-puzmdc6"></a>

<p align="center"><kbd><img src="assets/ah717foa4oc.png" width="80%"></kbd></p>

<br>

<a id="node-tqshixf"></a>

<p align="center"><kbd><img src="assets/r1smq1nn7dq.png" width="80%"></kbd></p>

<br>

<a id="node-kevgply"></a>

<p align="center"><kbd><img src="assets/dhxc7u4e2sd.png" width="80%"></kbd></p>

<br>

<a id="node-9lurrn7"></a>

<p align="center"><kbd><img src="assets/9fyevtmh9ia.png" width="80%"></kbd></p>

<br>

<a id="node-2lb3lx3"></a>

<p align="center"><kbd><img src="assets/nus1cmfz1hm.png" width="80%"></kbd></p>

<br>

<a id="node-qjm80rf"></a>

<p align="center"><kbd><img src="assets/ctgerhm0ne8.png" width="80%"></kbd></p>

<br>

<a id="node-qin5t5t"></a>

<p align="center"><kbd><img src="assets/xk2ulxhgo1.png" width="80%"></kbd></p>

<br>

<a id="node-tkzgm3r"></a>

### Programming Assignments

<br>

<a id="node-qjcea4l"></a>

#### How to Download your Notebook

<br>

<a id="node-ig17ew9"></a>

<p align="center"><kbd><img src="assets/cuh9kl0gs5b.png" width="80%"></kbd></p>

<br>

<a id="node-mpeujvs"></a>

<p align="center"><kbd><img src="assets/37fucik837u.png" width="80%"></kbd></p>

<br>

<a id="node-zl5q43h"></a>

#### Programming Assignments 1: Initialization

<br>

<a id="node-u0v6ysg"></a>

<p align="center"><kbd><img src="assets/okkosvan8yk.png" width="80%"></kbd></p>

<br>

<a id="node-tudjiii"></a>

<p align="center"><kbd><img src="assets/hblo0m7ciuh.png" width="80%"></kbd></p>

<br>

<a id="node-ux5g8s6"></a>

<p align="center"><kbd><img src="assets/s1n7on632kb.png" width="80%"></kbd></p>

<br>

<a id="node-03kxygm"></a>

##### 4 - Zero Initialization

<br>

<a id="node-js50f6t"></a>

<p align="center"><kbd><img src="assets/04wml96s9meq.png" width="80%"></kbd></p>

<br>

<a id="node-ucacges"></a>

<p align="center"><kbd><img src="assets/wo78p0m6ssa.png" width="80%"></kbd></p>

<br>

<a id="node-9j4b73j"></a>

<p align="center"><kbd><img src="assets/95uovft0awr.png" width="80%"></kbd></p>

<br>

<a id="node-8vwyqn2"></a>

<p align="center"><kbd><img src="assets/gjqzy2purpe.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gc372sa5bb.png" width="80%"></kbd></p>

<br>

<a id="node-8jyj0nf"></a>

##### 5 - Random Initialization

<br>

<a id="node-xk4j2pv"></a>

<p align="center"><kbd><img src="assets/xhjocpuh66i.png" width="80%"></kbd></p>

<br>

<a id="node-yg9kpgo"></a>

<p align="center"><kbd><img src="assets/nq1u8stq0yn.png" width="80%"></kbd></p>

<br>

<a id="node-eci4ter"></a>

<p align="center"><kbd><img src="assets/fgt1d1smu4.png" width="80%"></kbd></p>

<br>

<a id="node-kbt78uf"></a>

<p align="center"><kbd><img src="assets/yaek1gumtki.png" width="80%"></kbd></p>

<br>

<a id="node-rnib15a"></a>

<p align="center"><kbd><img src="assets/zkepox75bp.png" width="80%"></kbd></p>

<br>

<a id="node-zfbk8o3"></a>

##### 6 - He Initialization

<br>

<a id="node-vemyocm"></a>

<p align="center"><kbd><img src="assets/2wpd6ypdu5g.png" width="80%"></kbd></p>

<br>

<a id="node-a9bg54r"></a>

<p align="center"><kbd><img src="assets/nbf6ha0ome.png" width="80%"></kbd></p>

<br>

<a id="node-gl9wcm8"></a>

<p align="center"><kbd><img src="assets/dxrw2ja8xz6.png" width="80%"></kbd></p>

<br>

<a id="node-ocemhwi"></a>

<p align="center"><kbd><img src="assets/v2hopucvloj.png" width="80%"></kbd></p>

<br>

<a id="node-qazoi84"></a>

##### 7 - Conclusions

<br>

<a id="node-fsho2jg"></a>

<p align="center"><kbd><img src="assets/qf3jdfu2stl.png" width="80%"></kbd></p>

<br>

<a id="node-0oyy412"></a>

<p align="center"><kbd><img src="assets/5n5dmjvw8sb.png" width="80%"></kbd></p>

<br>

<a id="node-1xff0km"></a>

#### Programming Assignments 2: Regularization

<br>

<a id="node-3ptm640"></a>

##### 1 - Packages

<br>

<a id="node-pipgbb3"></a>

<p align="center"><kbd><img src="assets/n2mi6377rn.png" width="80%"></kbd></p>

<br>

<a id="node-epkqoum"></a>

<p align="center"><kbd><img src="assets/4qissn6cujg.png" width="80%"></kbd></p>

<br>

<a id="node-be22ibh"></a>

##### 2 - Problem Statement

<br>

<a id="node-xsme54l"></a>

<p align="center"><kbd><img src="assets/f15avvna5st.png" width="80%"></kbd></p>

<br>

<a id="node-x9j5kd3"></a>

##### 3 - Loading the Dataset

<br>

<a id="node-132i90f"></a>

<p align="center"><kbd><img src="assets/bs2vsq11zza.png" width="80%"></kbd></p>

<br>

<a id="node-lxegtgf"></a>

##### 4 - Non-Regularized Model

<br>

<a id="node-9yel19j"></a>

<p align="center"><kbd><img src="assets/arh3wqt2ez9.png" width="80%"></kbd></p>

<br>

<a id="node-1dhihzb"></a>

<p align="center"><kbd><img src="assets/l93r5nyw1p.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/cjx60grby7.png" width="80%"></kbd></p>

<br>

<a id="node-5ubt2y1"></a>

<p align="center"><kbd><img src="assets/mpb47xjtgsm.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ba7bmdtbbks.png" width="80%"></kbd></p>

<br>

<a id="node-vobqdeb"></a>

##### 5 - L2 Regularization

<br>

<a id="node-f82743p"></a>

<p align="center"><kbd><img src="assets/x9cw8mzxce.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/oa014vpik2.png" width="80%"></kbd></p>

<br>

<a id="node-nk32ost"></a>

<p align="center"><kbd><img src="assets/a50dos0xwhl.png" width="80%"></kbd></p>

<br>

<a id="node-6iraon3"></a>

<p align="center"><kbd><img src="assets/kbtfteo9yr.png" width="80%"></kbd></p>

<br>

<a id="node-fjp87nh"></a>

<p align="center"><kbd><img src="assets/1j946kf8ujt.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xusad4etcup.png" width="80%"></kbd></p>

<br>

<a id="node-gswzsp4"></a>

<p align="center"><kbd><img src="assets/l9dxg4spdqj.png" width="80%"></kbd></p>

<br>

<a id="node-g0ozof4"></a>

<p align="center"><kbd><img src="assets/qu6goudhvf9.png" width="80%"></kbd></p>

<br>

<a id="node-3f5a6n5"></a>

<p align="center"><kbd><img src="assets/79c77if83xv.png" width="80%"></kbd></p>

<br>

<a id="node-6cx4ewa"></a>

##### 6 - Dropout

<br>

<a id="node-zejgxu2"></a>

<p align="center"><kbd><img src="assets/ec9qnblnwsm.png" width="80%"></kbd></p>

<br>

<a id="node-s2l9keh"></a>

<p align="center"><kbd><img src="assets/gowpf584bal.png" width="80%"></kbd></p>

<br>

<a id="node-9qg56xh"></a>

<p align="center"><kbd><img src="assets/i2lk1xcu4f.png" width="80%"></kbd></p>

<br>

<a id="node-8hce218"></a>

<p align="center"><kbd><img src="assets/c4erfaeg72w.png" width="80%"></kbd></p>

<br>

<a id="node-ndahhhp"></a>

<p align="center"><kbd><img src="assets/zym39rghivh.png" width="80%"></kbd></p>

<br>

<a id="node-1snmqmd"></a>

- **6.1 - Forward Propagation with Dropout**

<br>

<a id="node-4uab3xu"></a>

<p align="center"><kbd><img src="assets/0k66ugf4tats.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/drtho91pzeo.png" width="80%"></kbd></p>

<br>

<a id="node-8gwmzke"></a>

<p align="center"><kbd><img src="assets/rn21j0yszy.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/c9h4vu0wvb.png" width="80%"></kbd></p>

<br>

<a id="node-uo2zncp"></a>

- **6.2 - Backward Propagation with Dropout**

<br>

<a id="node-4pw6ezr"></a>

<p align="center"><kbd><img src="assets/g8t757n0b8.png" width="80%"></kbd></p>

<br>

<a id="node-e88demy"></a>

<p align="center"><kbd><img src="assets/ov1j4xc527f.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/lxcrviivln.png" width="80%"></kbd></p>

<br>

<a id="node-uc6mqje"></a>

<p align="center"><kbd><img src="assets/nt9qie2dkeh.png" width="80%"></kbd></p>

<br>

<a id="node-0i4cesf"></a>

<p align="center"><kbd><img src="assets/mmh28uz7lda.png" width="80%"></kbd></p>

<br>

<a id="node-yrk107j"></a>

<p align="center"><kbd><img src="assets/v7b631koqsq.png" width="80%"></kbd></p>

<br>

<a id="node-j6f98fb"></a>

##### 7 - Conclusions

<br>

<a id="node-s10fppk"></a>

<p align="center"><kbd><img src="assets/uof0tfp6cri.png" width="80%"></kbd></p>

<br>

<a id="node-8bp2g4b"></a>

<p align="center"><kbd><img src="assets/rfqimnt3hge.png" width="80%"></kbd></p>

<br>

<a id="node-ijr3dg6"></a>

#### Programming Assignments: Gradient Checking

<br>

<a id="node-f39s33m"></a>

##### Gradient Checking

<br>

<a id="node-engc607"></a>

<p align="center"><kbd><img src="assets/hufvsbfxy4g.png" width="80%"></kbd></p>

<br>

<a id="node-tmbe6hd"></a>

<p align="center"><kbd><img src="assets/42nfrw0m86i.png" width="80%"></kbd></p>

<br>

<a id="node-a23c1yh"></a>

<p align="center"><kbd><img src="assets/1gjsv2ffy99.png" width="80%"></kbd></p>

<br>

<a id="node-03f1c84"></a>

##### 4 - 1-Dimensional Gradient Checking

<br>

<a id="node-u8tsqzx"></a>

<p align="center"><kbd><img src="assets/2tvm82p7jr1.png" width="80%"></kbd></p>

<br>

<a id="node-k04ytmc"></a>

<p align="center"><kbd><img src="assets/t61jill42up.png" width="80%"></kbd></p>

<br>

<a id="node-txrq3x0"></a>

<p align="center"><kbd><img src="assets/9ogjix12fzv.png" width="80%"></kbd></p>

<br>

<a id="node-54w2t8m"></a>

<p align="center"><kbd><img src="assets/aaqetkr5oz.png" width="80%"></kbd></p>

<br>

<a id="node-sulols1"></a>

<p align="center"><kbd><img src="assets/hl1plie7kug.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hdhjmknuhn.png" width="80%"></kbd></p>

<br>

<a id="node-x0sytws"></a>

##### 5 - N-Dimensional Gradient Checking

<br>

<a id="node-v48tzuy"></a>

<p align="center"><kbd><img src="assets/n5p2z1w7j0m.png" width="80%"></kbd></p>

<br>

<a id="node-as1qsb9"></a>

<p align="center"><kbd><img src="assets/wvc2dm7191h.png" width="80%"></kbd></p>

<br>

<a id="node-xxsrmt7"></a>

<p align="center"><kbd><img src="assets/1ur6btnoy8u.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây ổng cố tình làm sai chỗ dW2 ( *2 -> Sai, ko có *2
> làm gì) và db1 (4 ./ .. -> Sai, 1/ mới đúng).
> Mục đích để tí nữa Gradient Check thấy sai và xem lại

<br>

<a id="node-yl11jqq"></a>

<p align="center"><kbd><img src="assets/jaosls56fo.png" width="80%"></kbd></p>

<br>

<a id="node-mblsims"></a>

<p align="center"><kbd><img src="assets/ld5u0z0ajj.png" width="80%"></kbd></p>

<br>

<a id="node-va9e1ht"></a>

<p align="center"><kbd><img src="assets/py58z6symuk.png" width="80%"></kbd></p>

<br>

<a id="node-ougahrw"></a>

<p align="center"><kbd><img src="assets/0dujqi0dveyp.png" width="80%"></kbd></p>

<br>

<a id="node-k8xyrjk"></a>

<p align="center"><kbd><img src="assets/20qhliyryr4.png" width="80%"></kbd></p>

<br>

<a id="node-rfghbd8"></a>

<p align="center"><kbd><img src="assets/sokfs0j5i9t.png" width="80%"></kbd></p>

<br>

<a id="node-6rmpke3"></a>

<p align="center"><kbd><img src="assets/t4cxghhgd5q.png" width="80%"></kbd></p>

<br>

<a id="node-y311i2x"></a>

## C2w2_optimization Algorithms

<br>

<a id="node-e8o8q72"></a>

### Mini-batch Gradient Descent

<br>

<a id="node-1m9a5hn"></a>

#### 1 Introduction to \\*optimization algorithms\\* for \\*faster neural network training\\*.

2 \\*Vectorization\\* allows for \\*processing large training sets\\* without an explicit For
loop.

3 Gradient descent algorithm requires \\*processing the entire training set\\* before
taking one step.

4 Mini-batch gradient descent algorithm involves dividing training sets into
\\*mini-batches\\* and \\*processing them iteratively\\* for faster training.

5 Mini-batches consist of a \\*subset of the training set\\* and are processed in a
For loop using one step of gradient descent.

6 The dimensions of XT and YT for mini-batches are MX by 1,000 and 1 by 1,
000, respectively.

7 The mini-batch gradient descent algorithm is \\*more efficient\\* than the batch
gradient descent algorithm for large training sets.

<br>

<a id="node-38vi1ji"></a>

<p align="center"><kbd><img src="assets/zennszmwnts.png" width="80%"></kbd></p>

<br>

<a id="node-zmlg36z"></a>

<p align="center"><kbd><img src="assets/y0c8i7nc5m.png" width="80%"></kbd></p>

<br>

<a id="node-vsr4vdh"></a>

<p align="center"><kbd><img src="assets/9issyyrkyw.png" width="80%"></kbd></p>

> [!NOTE]
> **Epoc chính là số Iteration** thôi 
> Trong mỗi epoch/Iteration:
>
>
>
> Đ/v **mini batch**: nó sẽ chạy lần lượt tất
> cả các mini-batch ví dụ có 10 mini-batch thì nó update w,b **10 lần.**
>
>
>
> Còn đ/v **batch**: thì mỗi epoch nó chạy hết toàn bộ m data rồi update
> w,b **1 lần**
>
>
>
> Còn đ/v **Stochastic** thì để mỗi epoc / iteration nó chạy từng dataset
> và mỗi lần chạy nó update w,b 1 lần -> mỗi epoch/iteration nó update
> W,b **1000 lần. -> Câu dưới ChatGPT nó trả lời sai ở chỗ Stochastic**

<br>

<a id="node-jyibkv0"></a>

<p align="center"><kbd><img src="assets/oofyvgkeqc.png" width="80%"></kbd></p>

<br>

<a id="node-czy1csy"></a>

<p align="center"><kbd><img src="assets/kcufvis74x.png" width="80%"></kbd></p>

<br>

<a id="node-74pheyj"></a>

- **Sure, I'd be happy to provide more detail on the main ideas presented in the text.

1 \\*Optimization algorithms\\* for \\*faster\\* training: The text introduces the concept of \\*optimization
algorithms\\*, which can \\*enable faster training\\* of neural networks. As machine learning is an iterative
and empirical process, it often involves training a large number of models to find one that performs
well. However, training on large datasets can be slow, so having efficient optimization algorithms
can speed up the process and improve efficiency for teams.

2 \\*Mini-batch gradient\\* \\*descent\\*: The text goes on to explain mini-batch gradient descent, which is an
optimization algorithm that enables \\*faster training\\* of neural networks. Instead of processing the
entire training set at once, mini-batch gradient descent \\*splits the data into smaller subsets\\* called
\\*mini-batches\\*. These mini-batches typically contain around \\*1,000\\* \\*examples\\* each.

3 Notation for mini-batches: The text introduces new notation to represent mini-batches. X
superscript curly braces 1 through 5,000 represents the input data for each mini-batch, while Y
superscript curly braces 1 through 5,000 represents the corresponding output data.

4 Implementation of mini-batch gradient descent: To run mini-batch gradient descent, the text
explains that you would run a \\*For loop\\* for T equals 1 to 5,000, representing the 5,000
mini-batches. Inside the loop, \\*one step of gradient descent is implemented using the mini-batch\\* XT,
YT. This \\*allows progress to be made even before the entire training set has been processed\\*,
resulting in \\*faster training times.\\*

5 \\*Vectorization\\* for processing large datasets: The text also mentions that vectorization can be used
to process all m examples in a training set relatively quickly. \\*However, when m is very large\\* (e.g., 5
million or 50 million),\\* even vectorization can be slow\\*. Mini-batch gradient descent allows progress
to be made with smaller subsets of the data, enabling faster training times overall.

6 \\*Comparison\\* to batch gradient descent: The text notes that mini-batch gradient descent is
different from batch gradient descent, which \\*processes the entire training set at once\\*. While batch
gradient descent is sometimes referred to as "\\*batch\\*" because it processes the entire set at once,
mini-batch gradient descent is so-named because it processes smaller subsets (i.e., mini-batches)
of the data.

Overall, the text provides an overview of mini-batch gradient descent as an \\*optimization algorithm\\*
for faster training of neural networks. It introduces new notation for mini-batches and explains how
the algorithm is implemented. It also highlights the importance of optimization algorithms in
improving efficiency for machine learning teams.**

<br>

<a id="node-kmz8ezv"></a>

### Understanding Mini-batch Gradient Descent

<br>

<a id="node-dof2j4m"></a>

#### 1 The \\*cost function should decrease on every iteration\\* of batch
gradient descent.

2 Mini-batch gradient descent \\*may not decrease the cost function
on every iteration\\* due to training on different mini-batches.

3 \\*The size of the mini-batch\\* used in gradient descent is a
\\*parameter that needs to be chosen\\*.

4 A \\*mini-batch size\\* of \\*m\\* results in \\*batch\\* gradient descent, while a
mini-batch size of \\*1\\* results in \\*stochastic\\* gradient descent.

5 \\*Batch\\* gradient descent takes \\*too much time per iteration\\* for a
large training set, while \\*stochastic\\* gradient descent can be
\\*extremely noisy\\*.

6 The mini-batch size used in practice is usually somewhere in
between \\*1 and m\\*, as these values are respectively too small and
too large.

<br>

<a id="node-q13nskv"></a>

<p align="center"><kbd><img src="assets/mfl22kfu8sh.png" width="80%"></kbd></p>

<br>

<a id="node-3691zgf"></a>

<p align="center"><kbd><img src="assets/hk9l9x21ey6.png" width="80%"></kbd></p>

> [!NOTE]
> Mini batch size = m thì chính là /**Batch:** /Với data lớn thì nó 
> rất lâu vì mỗi lần 'chạy' g.d là nó phải tính toàn bộ data 
>
>
>
> Mini batch size = 1 thì ta có /**Stochastic**/
> Ưu điểm của nó là **cho ra 'progress' ngay chỉ với 1 training sample.**
> Và cái vấn đề 'zig zac / noisy' của nó có thể cải thiện bằng
> cách chọn learning rate nhỏ hơn.
> Tuy nhiên Stochastic có nhược điểm là coi như vứt bỏ sức 
> mạnh của **vectorization**
>
> Chỉ với **mini batch** thì có được cả 2 ưu điểm:
> - **Progress mà không phải đợi tính hết cả bộ data**
> - Vẫn tận dụng được sức mạnh của **vectorization**

<br>

<a id="node-ebkk7gj"></a>

<p align="center"><kbd><img src="assets/g1tz9dmvs0o.png" width="80%"></kbd></p>

> [!NOTE]
> - Nếu training size nhỏ thì không cần mini-batch làm gì ví dụ 
> <**2000**. Còn lớn hơn thì nên dùng mini batch.
>
>
>
> - **Thử nhiều giá trị** **mini-batch size 2^6, 2^7**... Typical use là 
> 64-512. 
>
>
>
> - Đảm bảo mini batch data **fit CPU/GPU memory** -> Cái này 
> phải thì  tuỳ vào application và data gì nhưng đại khái phải 
> check, nếu không nó sẽ fail

<br>

<a id="node-54gvfp3"></a>

- **1 Mini-batch gradient descent \\*allows for progress\\* to be made even w\\*hen the entire
training set has not been processed yet\\*. The cost function J(t) may \\*not decrease on
every iteration\\* due to processing different mini-batches X(t), Y(t), resulting in a \\*noisier
trend downwards.\\*

2 The \\*size\\* of the mini-batch is a \\*parameter that needs to be chosen\\*. The two extremes
are:

• \\*Batch\\* gradient descent, where the mini-batch size is equal to the training set size \\*m\\*.
In this case, the entire training set is processed on every iteration.

• \\*Stochastic\\* gradient descent, where the mini-batch size is equal to \\*1\\*. In this case, \\*each
example is its own mini-batch\\*, and the gradient descent step is taken with just a single
training example at a time.

3 \\*Batch\\* gradient descent can take relatively \\*large steps\\* with \\*low noise\\*, but takes \\*too
long per iteration\\* when processing a\\* large training set\\*. \\*Stochastic\\* gradient descent can
be \\*extremely noisy\\* and \\*won't ever converg\\*e, but is \\*faster\\* per iteration when processing
a \\*small\\* training set.

4 In practice, the \\*mini-batch size\\* used will be s\\*omewhere between 1 and m\\*. If the
mini-batch size is \\*too small\\*, then the \\*noise\\* from processing individual examples will be
too high. If the mini-batch size is \\*too large\\*, then the time per iteration will be \\*too long\\*. A
good mini-batch size allows for a \\*balance\\* between the two.**

<br>

<a id="node-l059o76"></a>

### Exponentially Weighted Averages

<br>

<a id="node-fq5hv35"></a>

#### 1 The speaker wants to show some \\*optimization algorithms\\* that are
\\*faster than gradient descent.\\*

2 To understand these algorithms, it is necessary to understand
\\*exponentially weighted averages\\*, also known as \\*exponentially
weighted moving averages.\\*

3 The speaker provides an example of \\*how to compute\\* exponentially
weighted averages using the d\\*aily temperature data from London\\*.

4 The formula for computing exponentially weighted averages is
given, and its general formula is presented.

5 The speaker explains how to \\*vary the parameter beta\\* to obtain
\\*different effect\\*s, such as a \\*smoother\\* or \\*noisier\\* curve, or \\*faster\\* or
\\*slower adaptation\\* to temperature changes.

6 Varying \\*beta\\* is a \\*hyperparameter\\* that can be tuned to optimize
learning algorithms.

<br>

<a id="node-w61ah7b"></a>

<p align="center"><kbd><img src="assets/r41ibuv7aq9.png" width="80%"></kbd></p>

<br>

<a id="node-wpl2jd6"></a>

<p align="center"><kbd><img src="assets/zf4wam9y35c.png" width="80%"></kbd></p>

> [!NOTE]
> Beta lớn -> **Lấy nhiều ảnh hưởng của quá khứ**, 
> **giảm ảnh hưởng của hiện tại** 
> -> **Trễ nhận ra sự thay đổi hơn** 
> -> **Đường cong smooth hơn** do nó thay đổi 
> chậm hơn
>
>
>
> Ngược lại nó **nhạy hơn,** đường cong nó **wiggly hơn**.

<br>

<a id="node-qdyitb6"></a>

<p align="center"><kbd><img src="assets/7ftf6ic2jkw.png" width="80%"></kbd></p>

> [!NOTE]
> Ngược lại beta nhỏ -> nó nhạy hơn, đường cong nó wigly hơn.

<br>

<a id="node-7qznhlb"></a>

- **1 Introduction: The speaker wants to introduce a few optimization algorithms that are f\\*aster\\*
than g\\*radient descent.\\*

2 \\*Exponentially Weighted Averages\\*: To understand these algorithms, it is important to
understand exponentially weighted averages, also known as \\*exponentially weighted moving
averages\\* in statistics.

3 \\*Temperature\\* Data Example: The speaker provides an example of \\*daily temperature data
\\*from London over the course of a year.

4 \\*Computation\\* of Moving Average: In order to compute the trends or moving average of the
temperature, the speaker proposes a formula using an \\*exponentially weighted average\\*. The
formula initializes \\*V0\\* to zero and then averages it with a \\*weight of 0.9 times\\* the\\* previous value\\*
plus\\* 0.1 times\\* the temperature \\*of that day\\*. The more general formula is V on a given day is 0.9
times V from the previous day plus 0.1 times the temperature of that day.

5 Plotting the Moving Average: The computed moving average is plotted in red and shows a
\\*smoother\\* curve than the original data.

6 Varying the \\*Beta\\* Parameter: The speaker then discusses how\\* varying the beta paramete\\*r in
the formula can \\*lead to different effects\\*. A \\*high beta\\* value results in a \\*smoother curve\\* but
more \\*latency in adapting to temperature changes\\*, while a l\\*ow beta\\* value results in a \\*noisier
curve\\* but \\*quicker adaptation\\* to temperature changes.

7 Importance of \\*Choosing the Right Beta\\* \\*Value\\*: The speaker notes that the choice of beta
value is a \\*hyperparameter\\* that can affect the performance of a learning algorithm and that
there is usually some value in between that works best.**

<br>

<a id="node-vtd349c"></a>

### Understand Exponentially Weighted Averages

<br>

<a id="node-0hsbkav"></a>

#### 1 \\*Exponentially weighted averages \\*is a \\*key\\* \\*component\\* of several optimization
algorithms used to train neural networks.

2 The video delves deeper into intuitions for understanding the algorithm.

3 The \\*key equation\\* for implementing exponentially weighted averages is
presented.

4 \\*Different values of beta\\* result in different \\*exponentially decaying functions\\*.

5 The algorithm computes averages of daily temperatures.

6 The equation for computing V100 is derived.

7 \\*V100\\* is a \\*weighted average of theta values\\*, where the \\*weight decays
exponentially over time\\*.

8 The daily temperature is multiplied by an \\*exponentially decaying function\\* and
then \\*summed up to compute V100\\*.

9 All \\*coefficients\\* add up to one, or very close to one, up to a detail called \\*bias
correction.\\*

10 It takes about \\*10 days\\* for the height of the \\*exponentially decaying function\\* to
\\*decay\\* to around \\*1/3\\* or one over \\*e\\* of the peak.

11 When \\*beta equals 0.9,\\* the algorithm is as if computing an \\*exponentially
weighted average\\* that focuses on the \\*last 10 days' temperature.\\*

<br>

<a id="node-ktri3pa"></a>

<p align="center"><kbd><img src="assets/3olnqcll5nr.png" width="80%"></kbd></p>

<br>

<a id="node-gjk6942"></a>

<p align="center"><kbd><img src="assets/z1ny5wt67c.png" width="80%"></kbd></p>

<br>

<a id="node-4zy4juz"></a>

<p align="center"><kbd><img src="assets/jqxdrkzq7z.png" width="80%"></kbd></p>

<br>

<a id="node-6m5kwpf"></a>

<p align="center"><kbd><img src="assets/frnn0bjhbi.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ..V100 sau khi triển khai thành ra:
>
> = 0.1*θ_100 + 0.1*0.9^1*θ_99 + 0.1*0.9^2*θ_98 +...
>
>
>
> thì đại khái là 2 cái này element-wised nhân nhau rồi sum up
>
>
>
> [θ_1,...θ_99, θ_100]
>
>
>
> và
>
>
>
> [... 0,1*0.9^2, 0,1*0.9, 0.1] = là hàm gọi là **exponentially decaying function**
>
>
>
> 2. Cái nữa mà ổng sẽ nói thêm sau là các coefficient 
> 0.1 + 0,1*0.9^1 + 0.1*0.9^2 ...~= 1 mà gọi là **correctness bias** gì đó
>
> Thì điều này đại khái đồng nghĩa là nếu **beta = 0,9** tương đương **eps = 0.1** thì
> kiểu như vt sẽ là average của 10 ngày trước đó cái này chưa hiểu lắm

<br>

<a id="node-lcgm617"></a>

<p align="center"><kbd><img src="assets/b1brmymbep7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **exponentially decaying function** có quy luật là
>
>
>
> (1-eps)**(1/eps) = 1/e ~= 0.3
>
>
>
> là sau 1/eps ngày thì value **giảm còn** ~= 1/3 ban đầu
> Ví dụ eps = 0.1 thì mất 10 ngày
> Ví dụ eps = 0.02 thì mất 50 ngày

<br>

<a id="node-gew2g4m"></a>

<p align="center"><kbd><img src="assets/pwzxrtt8fdj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là implement như thế nào thì
> trong code không có v1,v2,...mà là
> repeatedly assigning

<br>

<a id="node-ejfisxi"></a>

- **1 In the last video, we learned about \\*exponentially weighted averages\\* (EWAs), which are a
\\*key component\\* of several optimization algorithms used to train neural networks.

2 In this video, the focus is on understanding the intuition behind EWAs and how they
compute averages of daily temperature.

3 The\\* key equation\\* for implementing EWAs is presented, which includes a parameter called
\\*beta\\* that determines the \\*weight given to past values\\*.

4 \\*Different\\* \\*values\\* of \\*beta\\* result in \\*different weights for past values\\*, and the resulting graph
shows an exponentially decaying function.

5 To understand how this function is computing averages of daily temperature, the equation
is \\*rearranged\\* with decreasing values of T.

6 This \\*rearranged\\* \\*equation\\* is then used to \\*calculate V100\\*, which is the average of theta
values from day 100 to day 1.

7 The \\*coefficients\\* of the \\*theta\\* \\*values\\* in the equation can be expanded out and simplified,
showing that V100 is a weighted sum of theta values.

8 This sum of theta values is weighted by an \\*exponentially decaying function\\*, which results
in a graph that \\*decays exponentially from theta 100 to theta 1.\\*

9 The value of \\*beta\\* determines \\*how quickly the weight given to past values decays\\*, with
\\*larger values resulting in slower decay.
\\*
10 The number of days that the \\*EWA\\* averages over can be calculated based on the value of
\\*beta\\*, with beta equal to 0.9 resulting in an average over the last 10 days.

11 More generally, if beta is \\*1-epsilon\\*, where \\*epsilon is small,\\* then the \\*EWA\\* averages over
\\*approximately 1/epsilon days.\\*

12 This video provides a \\*detailed understanding\\* of the intuition behind EWAs and how they
work to compute averages of daily temperature.**

<br>

<a id="node-ktwu6xv"></a>

### Bias Correction In Exponentially Weighted Averages

<br>

<a id="node-tkjkmkz"></a>

#### 1 \\*Exponentially weighted moving averages\\* can be used to \\*smooth out
noisy data\\* and \\*capture trends\\* over time.

2 When implementing \\*exponential moving averages,\\* \\*bias correction\\* can
\\*improve accuracy\\*, especially during the\\* initial phas\\*e of the estimate.

3 Without bias correction, the e\\*stimate may start off much lower than
expected\\*, leading to a \\*biased assessment.\\*

4 To correct this bias, instead of using \\*V_t\\* as the estimate, we use \\*V_t
divided by 1-Beta^t\\*, where t is the current day.

5 As \\*t becomes large\\*, \\*Beta to the t approaches 0\\*, so \\*bias correction
becomes less important\\*.

6 Implementing bias correction can help obtain a \\*better estimate of the
data\\* during the \\*initial phase of learning\\*.

7 While most implementations of exponentially weighted moving averages
\\*do not include bias correction\\*, it can be \\*useful in certain situations\\*.

8 With these concepts, we can build \\*better optimization algorithm\\*s using
\\*exponential moving averages.\\*

<br>

<a id="node-495i3ub"></a>

<p align="center"><kbd><img src="assets/niy63o9yph.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với cách tính 'Exponentially weighted average'
> thì những lúc đầu t nhỏ, bởi vì initialize v_0 = 0 nên đại khái là
> giá trị tính ra sai lệch rất lớn so với giá trị thực tế.
>
>
>
> Cách khắc phục là 'Bias correction', sau khi tính vt thì chia cho 
> (1-beta^t)
>
>
>
> Thì giai đoạn đầu với t nhỏ, -> việc điều chỉnh v_t = v_t/(1-beta^t)
> sẽ giúp **fix sự sai lệch trên.** 
>
>
>
> Ví dụ trong hình ổng nói nếu không có B.C, thì v_1 chỉ bằng 0.02 theta_1,
> v_2 chỉ bằng 0,0196 theta_1 + 0,02 theta_2 đại khái là nhỏ hơn rất nhiều theta_2 
> -> Dẫn đến sai lệch ở khúc đầu
>
>
>
> Còn khi chia cho 1 - beta**t thì :
>
>
>
> v_1 = v_1/(1-0.98**1) = 0.02theta_1/0.02 = bằng ra lại theta_2 -> Hết lệch
>
>
>
> v_2 = v_2/(0.0396) = ..nói chung là việc chia cho term này giúp 'khôi
> phục' - có thể không nguyên vẹn nhưng khắc phục tình trạng cách biệt lớn ban đầu.
>
>
>
> Giai đoạn sau, t lớn, beta^t tiến về 0 -> 1-beta^1 tiến về 1 
> -> **hiệu ứng của Bias correction mất dần.**

<br>

<a id="node-261xzq4"></a>

### Gradient Descent With Momentum

<br>

<a id="node-4lazf0q"></a>

#### 1 The Momentum algorithm or \\*Gradient Descent with Momentum\\* is an
\\*optimization algorithm\\* that works \\*faster\\* than \\*standard Gradient Descent.\\*

2 The basic idea is to compute an \\*exponentially weighted average\\* of the
\\*gradients\\* and use that to update weights instead of using the gradients
themselves.

3 Gradient Descent often \\*oscillates\\* and takes many steps to reach the
minimum, \\*preventing\\* the use of \\*larger learning rates.\\*

4 \\*Momentum\\* \\*smooths out\\* the steps of Gradient Descent by taking a \\*more
straightforward path\\* and \\*damping out the oscillations to the minimum.\\*

5 Momentum can be \\*viewed as\\* providing \\*acceleration\\* to a \\*ball rolling down a
bowl-shaped function\\* and \\*momentum terms\\* \\*represent velocity\\*.

6 The algorithm involves\\* computing the derivatives\\*, computing \\*vdW\\* and \\*vdb\\*,
and updating the \\*weights\\* using vdW and vdb.

7 Momentum works for some people as an \\*analogy\\* of a ball rolling down a
bowl but may not work for everyone.

<br>

<a id="node-kqkaxo9"></a>

<p align="center"><kbd><img src="assets/v3d3zbk3c.png" width="80%"></kbd></p>

> [!NOTE]
> Vấn đề của G.D là nó sẽ bị **zic zac** ở 1 phương không mong muốn
> (một feature nào đó, hiểu đại khái thôi). Nên ta phải khắc phục bằng
> cách **khống chế learning rate alpha**. Nhưng điều này lài làm chậm
> quá trình G.D. Đại khái là chúng ta bị một mâu thuẫn là **muốn 
> G.D đi mạnh ở cái hướng mà nó sẽ tới minimum** (muốn vậy phải để
> Alpha lớn) nhưng lại phải **khống chế cái phương tán loạn kia** để nó
> không bị 'Diverge') (muốn vậy phải để alpha nhỏ.) Do đó 
> G.D không thể nhanh được.
>
>
>
>
> Đại khái thay vì update W, b bởi dW, db
> thì nay ta update bởi **vdW**, **vdb**
> trong đó vdW, vcb tính bằng phương pháp **'Exponentially weighted 
> average'** 
>
>
>
> Đại khái hệ quả là làm cho 'đường đi' của Gradient Descent nó
> **bớt zic zac/ tán loạn** về phương ngang (đang lấy ví dụ như trong 
> hình) mà **bước dài hơn về phương dọc** (là phương sẽ đến minimum)
>
> Advantages of gradient descent with momentum over traditional 
> gradient descent include:
>  1 Faster Convergence: Momentum helps **accelerate 
> gradient descent in the right direction**, thus speeding up 
> convergence. It helps to **overcome the problems of oscillations
>  or getting stuck in local minima**, which are commonly faced in 
> traditional gradient descent.
>  2 Stabilization: Gradient descent with momentum tends to 
> **dampen oscillations and moves more smoothly towards the 
> minimum**. This can lead to faster convergence and better results.
>
>
>
>  3 Handling of sparse gradients: **Sparse gradients** occur 
> when the gradient vector has **mostly zero entrie**s. Momentum helps 
> to overcome this problem by **accumulating the gradient information**
> over multiple iterations, providing a **more robust update**.
>
>
>
> Overall, gradient descent with momentum provides a better 
> optimization experience compared to traditional gradient descent. 
> However, **it is important to note that the choice of optimization 
> algorithm depends on the specific problem, and it is always a good 
> idea to experiment with different optimization algorithms** to 
> determine which one works best for a given problem.
>
> Cũng chưa hiểu tại sao lại tương đương việc vận tốc với gia
> tốc momentum gì đó trong bài toán ball roll down the hill

<br>

<a id="node-dkoo2oi"></a>

<p align="center"><kbd><img src="assets/7ygepfxdndo.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là có 2 phiên bản, cái nào cũng được.
> 1 cái là vdw = beta*vdw + (1-beta)*dw 
> 1 cái bỏ cái 1-beta đi mà tính vdw = beta*vdw + dw luôn
>
>
>
> Riêng mr Andrew prefer cái đầu hơn. 
>
>
>
> Beta thường chọn là 0.9 còn alpha phải tune riêng
>
>
>
> Và trong thực tế người ta cũng không bias correction vì sau chừng
> 10 iteration là hiện tượng (sai lệch ban đầu này) cũng không còn
>
> Finally, I just want to mention that if you read the literature on gradient descent with
> momentum often you see it with this term omitted, with this 1 minus Beta term
> omitted. So you end up with vdW equals Beta vdw plus dW. And the net effect of
> using this version in purple is that vdW ends up being scaled by a factor of 1 minus
> Beta, or really 1 over 1 minus Beta.
>
>
>
> And so when you're performing these gradient descent updates, alpha just
> needs to change by a corresponding value of 1 over 1 minus Beta. In practice,
> both of these will work just fine, it just affects what's the best value of the learning
> rate alpha.
>
>
>
> But I find that this particular formulation is a little less intuitive. Because one impact
> of this is that if you end up tuning the hyperparameter Beta, then this affects the
> scaling of vdW and vdb as well. And so you end up needing to retune the learning
> rate, alpha, as well, maybe.
>
>
>
> Chưa hiểu khúc này lắm nhưng chắc cũng không quan trọng mấy mà đại khái là
> nó chỉ ảnh hưởng chút đến best value của alpha

<br>

<a id="node-8w0vms1"></a>

- **1 The video discusses the \\*algorithm\\* called \\*momentum\\*, or \\*gradient descent with
momentum\\*, which almost always works \\*faster\\* than the \\*standard gradient descent
algorithm.\\*

2 The basic idea of the momentum algorithm is to compute an \\*exponentially weighted
average of the gradients\\* and \\*use that gradient to update the weights instead of using the
usual gradient.\\*

3 The standard gradient descent algorithm often takes many steps and \\*oscillates\\*
towards the minimum because it cannot use a l\\*arge learning rate\\* due to the \\*oscillations\\*.

4 The momentum algorithm \\*smooths out the steps\\* of gradient descent by \\*computing a
moving average of the derivatives for w\\*. It \\*averages out the oscillations\\* in the \\*vertical
direction\\*, \\*where\\* \\*slowing things down is desired\\*, and \\*takes steps that are much smaller in
the vertical direction\\* but are \\*more directed to moving quickly in the horizontal direction.\\*

5 The momentum algorithm works by computing \\*vdW\\* to be \\*Beta vdw plus 1 minus Beta
dW\\*, where Beta is a \\*hyperparameter\\* between 0 and 1, and similarly computing \\*vdb\\*.

6 The weights are updated using \\*W gets updated as W minus the learning rate times
vdW\\*, and similarly, b gets updated as b minus alpha times vdb.

7 An analogy to understand the momentum algorithm is to think of the \\*derivatives\\*
providing \\*acceleration\\* to a ball that is \\*rolling down a hill\\*, while the \\*momentum terms
represent velocity.
\\*
8 The \\*momentum\\* algorithm \\*prevents the ball from speeding up without limit by applying
a row of friction\\*, which is similar to how the momentum algorithm applies the Beta
hyperparameter.

9 Finally, the video presents the algorithm and its implementation details.**

<br>

<a id="node-mrun80b"></a>

### Rmsprop

<br>

<a id="node-ny8bddv"></a>

#### 1 RMSprop is another algorithm that can\\* speed up gradient descent,\\* and it aims to
\\*slow down learning in the vertical direction\\* and \\*speed up learning in the horizontal
direction\\*.

2 On each iteration, RMSprop computes the\\* derivative of the parameters on the
current mini-batch\\*, then keeps an \\*exponentially weighted average\\* of the \\*squares of
these derivatives.\\*

3 \\*RMSprop\\* updates the parameters by dividing the \\*derivative\\* of each \\*parameter\\* by
the \\*square root\\* of the\\* exponentially weighted average\\* of the \\*squares of the
derivatives of that parameter.\\*

4 The effect of this is that the \\*updates in the vertical direction\\* \\*are divided by a much
larger number\\*, which helps \\*damp out oscillations\\*, whereas the \\*updates in the
horizontal direction are divided by a smaller number.\\*

5 In practice, \\*RMSprop\\* is used in a \\*high-dimensional space of parameters\\*, and it can
\\*damp out oscillations\\* in a \\*subset of parameters.\\*

6 RMSprop stands for \\*Root Mean Squared Prop\\* because it \\*squares\\* the derivatives and
then takes the\\* square root at the end.\\*

7 To avoid division by zero, RMSprop adds a s\\*mall epsilon to the denominator.\\*

8 In the next video, RMSprop will be combined with momentum.

<br>

<a id="node-63b68fd"></a>

<p align="center"><kbd><img src="assets/807pmoomve.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với **param nào mà khiến G.D đi sai hướng - oscillate**,
> ví dụ ở đây cho dễ hình dung là b, thì **average weight của nó
> sẽ lớn** -> việc **chia db cho sqrt(sdb)** sẽ làm **b nhỏ lại** -> **Giảm bớt 
> ảnh hường của b, giảm bớt oscillation**
>
>
>
> Ngược lại với weight/param nào khiến G.D đi đúng hướng, 
> ở đây ví dụ là w, thì nó ít oscillation -> sdw nhỏ -> dw chia 
> cho sqrt(sdw) không ảnh hưởng mấy đến w -> giữ hướng 
> đi đúng đó.
>
> Bài sau sẽ kết hợp momentum và
> RMSProp nên đánh beta2 để phân biệt.
>
>
>
> Thêm epsilon để không bị chia cho 0

<br>

<a id="node-n33u7iz"></a>

- **1 What is RMSprop and how does it work?

- RMSprop is \\*another algorithm\\*, in addition to momentum, that can \\*speed up gradient descen\\*t.
It stands for \\*root\\* \\*mean\\* \\*square\\* \\*prop\\* and it is designed to\\* slow down the learning in the
vertical direction\\* and \\*speed up learning in the horizontal direction\\*. To accomplish this, on each
iteration, RMSprop \\*computes the derivative of the current mini-batch\\* as usual, then it keeps an
\\*exponentially weighted average\\* \\*of the squares of the derivatives\\*, which is denoted as \\*SdW\\*
and \\*Sdb\\*. These terms are updated as follows: SdW = beta * SdW + (1 - beta) * dW^2 and Sdb =
beta * Sdb + (1 - beta) * db^2, where beta is a hyperparameter and the squaring operation is an
element-wise operation. Next, RMSprop updates the parameters as follows: \\*W = W - learning_rate *
dW / sqrt(SdW)\\* and b = b - learning_rate * db / sqrt(Sdb), where learning_rate is the hyperparameter
that controls how big of a step is taken during each iteration.

2 How does RMSprop help with oscillations in the vertical direction?

- RMSprop helps with oscillations in the vertical direction by slowing down the learning rate in that
direction. This is achieved by keeping a larger value of Sdb, which is the exponentially weighted
average of the squares of the derivatives in the vertical direction. The derivatives in the vertical
direction tend to be much larger than those in the horizontal direction, due to the steep slope of the
function in the vertical direction. As a result, Sdb will be relatively large, and when db is divided by
sqrt(Sdb) in the update equation for b, the resulting update will be much smaller than in the horizontal
direction, effectively damping out the oscillations in the vertical direction.

3 How does RMSprop help with faster learning in the horizontal direction?

- RMSprop helps with faster learning in the horizontal direction by speeding up the learning rate in that
direction. This is achieved by keeping a smaller value of SdW, which is the exponentially weighted
average of the squares of the derivatives in the horizontal direction. The derivatives in the horizontal
direction tend to be much smaller than those in the vertical direction, due to the gentle slope of the
function in the horizontal direction. As a result, SdW will be relatively small, and when dW is divided by
sqrt(SdW) in the update equation for W, the resulting update will be much larger than in the vertical
direction, effectively allowing for faster learning in the horizontal direction.

4 How is RMSprop applied in practice?

- In practice, RMSprop is applied by computing the derivatives of the current mini-batch as usual, then
keeping an exponentially weighted average of the squares of the derivatives in each dimension of the
parameter vector. The resulting terms SdW and Sdb are used to update the parameters in each
dimension, with a learning rate that is scaled by the inverse square root of SdW or Sdb, respectively.
To prevent division by zero, a small constant is added to SdW and Sdb before taking the square root.
Additionally, a hyperparameter beta is used to control the weighting of the current and previous values
in the exponential moving averages of SdW and Sdb, respectively. In practice, beta is typically set to a
value between 0.9 and 0.99.**

<br>

<a id="node-wugf5hw"></a>

### Clarification About Upcoming Adam Optimization Video

<br>

<a id="node-jhg450p"></a>

#### ...

<br>

<a id="node-6ui9he6"></a>

<p align="center"><kbd><img src="assets/ghn5k2m9lj.png" width="80%"></kbd></p>

<br>

<a id="node-pl18mbs"></a>

### Adam Optimization Algorithm

<br>

<a id="node-v5f9dc3"></a>

#### 1 Introduction:  2 During the history of deep learning, many optimization algorithms were
proposed by researchers, but few generalize well across a wide range of neural networks.
The deep learning community developed \\*skepticism\\* about new optimization algorithms,
preferring to \\*use gradient descent with momentum\\* as a \\*reliable approach\\*.

3 \\*RMSprop\\* and \\*Adam Optimization Algorithm:\\*  4 RMSprop and the Adam optimization
algorithm are two algorithms that have been shown to \\*work well across a wide range of
deep learning architectures\\*. The Adam optimization algorithm is a \\*combination\\* of
\\*momentum\\* and \\*RMSprop\\*. It uses hyperparameters \\*Beta_1\\* and \\*Beta_2\\* to calculate the
\\*moving\\* \\*weighted\\* \\*average\\* \\*of the derivatives and their squares\\*.

5 Implementation of Adam:  6 To implement Adam, we first initialize \\*V_dw\\*, \\*V_db\\*, \\*S_dw\\*,
and \\*S_db\\* to zero. We then compute the derivatives, dw, and db, using mini-batch gradient
descent, and calculate the momentum and RMSprop updates using \\*Beta_1\\* and \\*Beta_2\\*.
\\*Bias correction\\* is implemented \\*to correct\\* V_dw, V_db, S_dw, and S_db. Finally, the
weights are updated using the learning rate hyperparameter \\*Alpha\\* and the \\*RMSprop-like\\*
update.

7 Hyper-parameters and Tuning:  8 The Adam optimization algorithm has several
\\*hyper-parameters\\* that need to be tuned, including \\*Alpha\\*, \\*Beta_1\\*, \\*Beta_2\\*, and \\*Epsilon\\*.
Alpha is the learning rate and needs to be tuned, while default values of Beta_1, Beta_2,
and Epsilon are often used. Beta_1 computes the mean of the derivatives, and Beta_2 is
used to compute the exponentially weighted average of the squares. The term Adam
stands for \\*Adaptive\\* \\*Moment\\* \\*Estimation\\*.

9 Conclusion and Further Discussion:  10 The Adam optimization algorithm is an \\*effective
learning algorithm\\* that allows for quicker training of neural networks. However, tuning the
hyperparameters is necessary for optimal performance.

<br>

<a id="node-0hsx4gm"></a>

<p align="center"><kbd><img src="assets/oklc86m5ki9.png" width="80%"></kbd></p>

> [!NOTE]
> Adam algorithm kết hợp giữa momentum g.d và RMSprop

<br>

<a id="node-dwb99qg"></a>

<p align="center"><kbd><img src="assets/art667sdowa.png" width="80%"></kbd></p>

> [!NOTE]
> Các hyperparam beta1, beta2, epsilon thường dùng và chỉ cần
> tune Alpha. và Adam không liên quan gì ông này Adam Coat

<br>

<a id="node-vf4ymbs"></a>

### Clarification About Learning Rate Decay Video

<br>

<a id="node-8zszak9"></a>

#### ...

<br>

<a id="node-uve5ntw"></a>

<p align="center"><kbd><img src="assets/rqdqa9usd6.png" width="80%"></kbd></p>

<br>

<a id="node-hzjc67v"></a>

### Learning Rate Decay

<br>

<a id="node-3uu4fjl"></a>

#### 1 \\*Learning rate\\* \\*decay\\* is a technique that can help \\*speed up\\* the learning algorithm by
\\*gradually reducing\\* the \\*learning rate over time\\*.

2 By using a \\*smaller\\* learning rate, the algorithm can \\*oscillate\\* in a \\*tighter region\\* \\*around
the minimum\\* instead of \\*wandering far away\\* as training goes on and on.

3 One way to implement \\*learning rate decay\\* is to set the \\*learning rate Alpha\\* to be equal
to \\*1 over 1 plus a paramete\\*r (decay rate times epoch num) times some\\* initial learning
rate Alpha 0.\\*

4 Other than this formula for learning rate decay, there are other ways people use to
decay the learning rate \\*manually\\*, using \\*exponential decay\\*, learning rate that decreases
and discretizes, etc.

5 \\*Manual decay\\* is sometimes used when \\*training only a small number of models\\* and
the \\*learning rate is controlled by hand\\*, \\*hour-by-hour\\*, \\*day-by-day\\*.

6 Next week, when we talk about \\*hyperparameter tuning\\*, there will be more \\*systematic
ways\\* to organize all the \\*hyperparameters\\* and \\*efficiently search amongst them.\\*

7 \\*Learning rate decay\\* is usually \\*lower\\* down on the \\*list of things to try\\*, compared to
\\*setting a fixed value of Alph\\*a and \\*getting it to be well-tuned\\*, which has a huge impact on
training.

8 Lastly, the concept of \\*local optima\\* and \\*saddle points\\* in \\*neural network\\*s are briefly
mentioned as a topic for future discussion.

<br>

<a id="node-up6xoe3"></a>

<p align="center"><kbd><img src="assets/8lt626thgbr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với mini-bactch gradient descent với **Fixed alpha** thì 
> **J sẽ không converge chính xác về Minimum** mà sẽ **loanh quanh** khu
> vực đó. Vấn đề này có thể **tạm chấp nhận** vì dù sao mini-batch 
> giúp G.D nhanh hơn và kết quả cũng không qúa tệ.
>
>
>
> Tuy nhiên có thể improve vấn đề này bằng cách cho alpha **giảm 
> dần - Decay**

<br>

<a id="node-1pwyodq"></a>

<p align="center"><kbd><img src="assets/67irgnosvkd.png" width="80%"></kbd></p>

<br>

<a id="node-53gqofo"></a>

<p align="center"><kbd><img src="assets/zf4i3qkmqk.png" width="80%"></kbd></p>

> [!NOTE]
> **Manually decay:** Đại khái là tự adjust alpha thủ công
> chỉ dc khi training vài model hàng giờ, hàng ngày liền
> thì cách này đại khái là theo dõi model và tự điều chỉnh
> alphaIf you're **training just one model at a time**, and if your
> model takes **many hours** or even many **days to train**,
> what some people would do is **just watch your model**
> as it's training over a large number of days, and then
> now you say, **oh, it looks like the learning rate slowed
> down, I'm going to decrease Alpha a little bit**.Of course,
> this works, this **manually controlling Alpha**, really **tuning
> Alpha by hand, hour-by-hour, day-by-day**. This works
> only if you're training **only a small number of model**s, but
> **sometimes people do that as well**
>
> Một số cách thức decay alpha hay dùng

<br>

<a id="node-z5isj8d"></a>

### The Problem Of Local Optima

<br>

<a id="node-bk9q6xi"></a>

#### 1 In the early days of deep learning, people were concerned about
optimization algorithms getting stuck in \\*bad local optima\\*.

2 As our understanding of deep learning has advanced, \\*our understanding
of local optima is changing\\*.

3 Most points of zero gradient in a cost function are actually \\*saddle points
rather than local optima\\*, especially in \\*high-dimensional spaces\\*.

4 \\*Plateaus\\* can\\* slow down learning\\* and are a \\*problem for optimization
algorithms\\*.

5 \\*Sophisticated\\* \\*optimization\\* algorithms, such as \\*momentum\\*, \\*RmsProp\\*,
and \\*Adam\\*, can help \\*overcome the problem of plateaus\\*.

6 Our understanding of high-dimensional optimization problems is still
evolving.

<br>

<a id="node-jnhn7tm"></a>

<p align="center"><kbd><img src="assets/r5trndv3lc.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là trong thực tế khó gặp l**ocal optima - Stuck /
> không có đường xuống nữa** ( - vấn đề mà ML lúc trước hay
> nói đến) mà là thường là dạng **Saddle - nơi luôn có đường
> để xuống.**

<br>

<a id="node-mokt6vo"></a>

<p align="center"><kbd><img src="assets/7xei7ca3qgj.png" width="80%"></kbd></p>

> [!NOTE]
> Nên vấn đề là **không phải ta sẽ bị stuck ko xuống được
> nữa** mà là khi gặp mấy cái saddle này ta sẽ **xuống rất rất chậm**
>
>
>
> *Ta ở đây ý nói J trong quá trình training, xuống ở đây ý nói 
> việc giảm J trong quá trình G.D
>
>
>
> Và vấn đề trên đ**ã được giải quyết** bằng nhưng **Algorithm** cải tiến
> như **momentum**, **Adam**

<br>

<a id="node-iaze63j"></a>

### Quiz

<br>

<a id="node-zzglfo2"></a>

<p align="center"><kbd><img src="assets/d70y5k39jd.png" width="80%"></kbd></p>

<br>

<a id="node-x1c424h"></a>

<p align="center"><kbd><img src="assets/t7l64v4adaa.png" width="80%"></kbd></p>

<br>

<a id="node-rrl3ua9"></a>

<p align="center"><kbd><img src="assets/czdx0nz8mb6.png" width="80%"></kbd></p>

<br>

<a id="node-qvcs9n5"></a>

<p align="center"><kbd><img src="assets/bkitx1a884o.png" width="80%"></kbd></p>

<br>

<a id="node-dnst995"></a>

<p align="center"><kbd><img src="assets/vmd4oonx89.png" width="80%"></kbd></p>

<br>

<a id="node-bnkw8f5"></a>

<p align="center"><kbd><img src="assets/ll1x0o14erq.png" width="80%"></kbd></p>

<br>

<a id="node-tzliadb"></a>

<p align="center"><kbd><img src="assets/zcncxi2q5x8.png" width="80%"></kbd></p>

<br>

<a id="node-lvur4ae"></a>

<p align="center"><kbd><img src="assets/xqhba1yu55s.png" width="80%"></kbd></p>

<br>

<a id="node-y076dgd"></a>

<p align="center"><kbd><img src="assets/f57a0syeica.png" width="80%"></kbd></p>

<br>

<a id="node-rdwtliv"></a>

<p align="center"><kbd><img src="assets/orlnqiay1rr.png" width="80%"></kbd></p>

<br>

<a id="node-75wglpg"></a>

<p align="center"><kbd><img src="assets/gyy9mnwlrsa.png" width="80%"></kbd></p>

<br>

<a id="node-qyv36d3"></a>

<p align="center"><kbd><img src="assets/go1lyqlhse9.png" width="80%"></kbd></p>

<br>

<a id="node-y369maw"></a>

### Programming Assignment

<br>

<a id="node-dwnqm9x"></a>

#### Optimization Methods

<br>

<a id="node-k5ry8yn"></a>

<p align="center"><kbd><img src="assets/ge5rk0fmlmh.png" width="80%"></kbd></p>

<br>

<a id="node-7xihc16"></a>

#### 1- Packages

<br>

<a id="node-qaayfq6"></a>

<p align="center"><kbd><img src="assets/a4al7qns76.png" width="80%"></kbd></p>

<br>

<a id="node-guulhm1"></a>

#### 2 - Gradient Descent

<br>

<a id="node-r4hx3f6"></a>

##### Exercise 1 - update_parameters_with_gd

> [!NOTE]
> Update params như thông thường

<br>

<a id="node-klashzv"></a>

<p align="center"><kbd><img src="assets/lbric41oyvd.png" width="80%"></kbd></p>

<br>

<a id="node-6noilf6"></a>

<p align="center"><kbd><img src="assets/vqs3iscl0l.png" width="80%"></kbd></p>

<br>

<a id="node-95iv4pb"></a>

<p align="center"><kbd><img src="assets/qu25d68342o.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/urlmwd99s5j.png" width="80%"></kbd></p>

<br>

<a id="node-bzhms4y"></a>

<p align="center"><kbd><img src="assets/lp4xcgwmyjn.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/lovj910qhg.png" width="80%"></kbd></p>

<br>

<a id="node-anzvfg9"></a>

#### 3 - Mini-Batch Gradient Descent

<br>

<a id="node-a67nbwi"></a>

##### 2 steps: Shuffle & Partition

<br>

<a id="node-n1rftjw"></a>

<p align="center"><kbd><img src="assets/lk3u92yor6g.png" width="80%"></kbd></p>

<br>

<a id="node-qyzlqvv"></a>

<p align="center"><kbd><img src="assets/3cpcodmlqrc.png" width="80%"></kbd></p>

<br>

<a id="node-xtwyi4u"></a>

##### Exercise 2 - random_mini_batches

> [!NOTE]
> Chia bộ data thành các mini batch,
> Số mini_batch = K  + 1 bộ lẻ 
> (nếu có thì size = m - K*mini_batch_size)
> K = np.roundoff(m/mini_batch_size).

<br>

<a id="node-bahg7cf"></a>

<p align="center"><kbd><img src="assets/4a7tj7n0tr6.png" width="80%"></kbd></p>

<br>

<a id="node-ntojx54"></a>

<p align="center"><kbd><img src="assets/bmpxkyg968u.png" width="80%"></kbd></p>

<br>

<a id="node-lskc7mv"></a>

<p align="center"><kbd><img src="assets/krqd6fkwj8.png" width="80%"></kbd></p>

<br>

<a id="node-4bs0i51"></a>

<p align="center"><kbd><img src="assets/rskfadgjk0f.png" width="80%"></kbd></p>

<br>

<a id="node-b1nolrx"></a>

<p align="center"><kbd><img src="assets/bthspbz7sem.png" width="80%"></kbd></p>

<br>

<a id="node-6ivxhrj"></a>

<p align="center"><kbd><img src="assets/dojgsp4kf1.png" width="80%"></kbd></p>

<br>

<a id="node-kfej60e"></a>

##### Note

> [!NOTE]
> *NOTE

<br>

<a id="node-m5t86pf"></a>

<p align="center"><kbd><img src="assets/3lg0qiiirqk.png" width="80%"></kbd></p>

> [!NOTE]
> *NOTE

<br>

<a id="node-12rd6cf"></a>

#### 4 - Momentum

<br>

<a id="node-efp8pno"></a>

##### Exercise 3 - initialize_velocity

> [!NOTE]
> Chỉ ini vdW1, vdb1, ...vdWL, vdbL bởi 
> np.zeros(shape)
> Với shape tương ứng của W1, b1,..WL, bL
> Bỏ vào trong dictionary v luôn
> Ex. v[dw1=...], v[db1=...]

<br>

<a id="node-3cx9qrn"></a>

<p align="center"><kbd><img src="assets/6u66yknt678.png" width="80%"></kbd></p>

<br>

<a id="node-fsatvh3"></a>

<p align="center"><kbd><img src="assets/u218qrdmnva.png" width="80%"></kbd></p>

<br>

<a id="node-al4fmlg"></a>

<p align="center"><kbd><img src="assets/z0xbymgb5rj.png" width="80%"></kbd></p>

<br>

<a id="node-15wswib"></a>

##### Exercise 4 - update_parameters_with_momentum

> [!NOTE]
> Update params with MOMENTUM
> Thay vì update W,b với dW, db thông thường thì
> Nay update W với vdW, vdb
> Với vdW, vdb Tính theo công thức **Exponentially 
> Weight Average** 
>
>
>
> vdW = beta*vdW + (1-beta)*dW 
> vdb = beta*vdb + (1-beta)*db

<br>

<a id="node-3ez8fjp"></a>

<p align="center"><kbd><img src="assets/pw4beouy2k.png" width="80%"></kbd></p>

<br>

<a id="node-qijqz5r"></a>

<p align="center"><kbd><img src="assets/q2gv73ahowj.png" width="80%"></kbd></p>

<br>

<a id="node-bkrz783"></a>

##### Note

> [!NOTE]
> *NOTE

<br>

<a id="node-0rof3m1"></a>

<p align="center"><kbd><img src="assets/pn12gnxtth.png" width="80%"></kbd></p>

> [!NOTE]
> *NOTE

<br>

<a id="node-rojldpp"></a>

#### 5 - Adam

<br>

<a id="node-1a1fwr2"></a>

##### Exercise 5 - initialize_adam

> [!NOTE]
> Chỉ ini vdW1, vdb1, ...vdWL, vdbL 
> sdW1, sdb1, ...sdWL, sdbL
> bởi np.zeros(shape)
> Với shape tương ứng của W1, b1,..WL, bL
> Bỏ vào trong dictionary v luôn
> Ex. v[dw1=...], v[db1=...]

<br>

<a id="node-oygf4k6"></a>

<p align="center"><kbd><img src="assets/k1lllwqctx.png" width="80%"></kbd></p>

<br>

<a id="node-qn0r5l2"></a>

<p align="center"><kbd><img src="assets/msrowmzg0a.png" width="80%"></kbd></p>

<br>

<a id="node-xn7lby8"></a>

<p align="center"><kbd><img src="assets/h9j472f6qsk.png" width="80%"></kbd></p>

<br>

<a id="node-t09mmpn"></a>

##### Exercise 6 - update_parameters_with_adam

> [!NOTE]
> Update params with ADAM

<br>

<a id="node-05tukth"></a>

<p align="center"><kbd><img src="assets/48x427zeh5l.png" width="80%"></kbd></p>

<br>

<a id="node-6mj02j1"></a>

<p align="center"><kbd><img src="assets/il8zuvgf91.png" width="80%"></kbd></p>

<br>

<a id="node-e1pgqhs"></a>

<p align="center"><kbd><img src="assets/zzc9vjiokpm.png" width="80%"></kbd></p>

<br>

<a id="node-8b8m45x"></a>

#### 6 - Model with different Optimization algorithms

> [!NOTE]
> Lần lượt thử train model với 3 loaị để coi cái 
> nào tốt hơn: G.D, Momentum, Adam

<br>

<a id="node-o3pjevm"></a>

##### 'Moons' dataset

<br>

<a id="node-wb1knq4"></a>

<p align="center"><kbd><img src="assets/9f0hu0jvlgo.png" width="80%"></kbd></p>

<br>

<a id="node-i4fkprc"></a>

<p align="center"><kbd><img src="assets/dmdd31tzv9u.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/l5uady9v3il.png" width="80%"></kbd></p>

<br>

<a id="node-kdsw7pm"></a>

##### 6.1 - Mini-Batch Gradient Descent

<br>

<a id="node-8oa3uzq"></a>

<p align="center"><kbd><img src="assets/80t4oi3qjiv.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jwl7faltian.png" width="80%"></kbd></p>

<br>

<a id="node-pfewoss"></a>

##### 6.2 - Mini-Batch Gradient Descent with Momentum

<br>

<a id="node-eo4e0qa"></a>

<p align="center"><kbd><img src="assets/9s1nfrd9zzb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/tfnfvt07fe.png" width="80%"></kbd></p>

<br>

<a id="node-oooh7sj"></a>

##### 6.3 - Mini-Batch with Adam

<br>

<a id="node-j75o8k8"></a>

<p align="center"><kbd><img src="assets/w13w3xs2y19.png" width="80%"></kbd></p>

<br>

<a id="node-v7uakxj"></a>

<p align="center"><kbd><img src="assets/b35u499awqg.png" width="80%"></kbd></p>

<br>

<a id="node-kg2mkuz"></a>

##### 6.4 - Summary

> [!NOTE]
> *NOTE

<br>

<a id="node-cqlmwhh"></a>

<p align="center"><kbd><img src="assets/z3trq2sfoak.png" width="80%"></kbd></p>

> [!NOTE]
> *NOTE

<br>

<a id="node-1sosngm"></a>

#### 7 - Learning Rate Decay and Scheduling

<br>

<a id="node-0q0xnf2"></a>

##### Thêm 'Learning decay' element

<br>

<a id="node-g6vicpu"></a>

<p align="center"><kbd><img src="assets/21baqlo8y2.png" width="80%"></kbd></p>

<br>

<a id="node-hegnmrs"></a>

<p align="center"><kbd><img src="assets/j41176nvb7i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/t4ypxcrsv4.png" width="80%"></kbd></p>

<br>

<a id="node-9e3dom2"></a>

##### 7.1 - Decay on every iteration

<br>

<a id="node-buq04kh"></a>

- **Exercise 7 - update_lr**

<br>

<a id="node-crlii4u"></a>

<p align="center"><kbd><img src="assets/mmug6q9qdrd.png" width="80%"></kbd></p>

<br>

<a id="node-we56j6j"></a>

<p align="center"><kbd><img src="assets/lwdhkbhr1b.png" width="80%"></kbd></p>

<br>

<a id="node-3b4cmg6"></a>

<p align="center"><kbd><img src="assets/bbh31jex2rk.png" width="80%"></kbd></p>

> [!NOTE]
> *NOTE

<br>

<a id="node-d2diavs"></a>

##### 7.2 - Fixed Interval Scheduling

<br>

<a id="node-sozyelb"></a>

- **Exercise 8 - schedule_lr_decay**

<br>

<a id="node-nx25upi"></a>

<p align="center"><kbd><img src="assets/3c8ypiilssk.png" width="80%"></kbd></p>

<br>

<a id="node-2vke3fx"></a>

<p align="center"><kbd><img src="assets/quelmtw5yui.png" width="80%"></kbd></p>

<br>

<a id="node-0mor2tb"></a>

##### 7.3 - Using Learning Rate Decay for each Optimization Method

<br>

<a id="node-8irpttw"></a>

- **7.3.1 - Gradient Descent with Learning Rate Decay**

<br>

<a id="node-3v7fnhb"></a>

<p align="center"><kbd><img src="assets/vw69ea5zju8.png" width="80%"></kbd></p>

<br>

<a id="node-inabj84"></a>

<p align="center"><kbd><img src="assets/1m4b5crws2k.png" width="80%"></kbd></p>

<br>

<a id="node-i9b9bvg"></a>

- **7.3.2 - Gradient Descent with Momentum and Learning Rate Decay**

<br>

<a id="node-j0viiyz"></a>

<p align="center"><kbd><img src="assets/wui5sy4b5lm.png" width="80%"></kbd></p>

<br>

<a id="node-f3hluim"></a>

<p align="center"><kbd><img src="assets/45pang75phg.png" width="80%"></kbd></p>

<br>

<a id="node-0lnrzt5"></a>

- **7.3.3 - Adam with Learning Rate Decay**

<br>

<a id="node-on2gimg"></a>

<p align="center"><kbd><img src="assets/6jgikkq4m76.png" width="80%"></kbd></p>

<br>

<a id="node-r6ceb9h"></a>

<p align="center"><kbd><img src="assets/o2eia1u3r5b.png" width="80%"></kbd></p>

<br>

<a id="node-qnvgg7d"></a>

##### 7.4 - Achieving similar performance with different methods

> [!NOTE]
> *NOTE

<br>

<a id="node-b48bill"></a>

<p align="center"><kbd><img src="assets/5s6pf8lwque.png" width="80%"></kbd></p>

> [!NOTE]
> *NOTE

<br>

<a id="node-6lhf61r"></a>

## C2w3_hyperparamter Tuning, Batch
normalization & Programming Frameworks

<br>

<a id="node-b7zet6e"></a>

### Hyperparams Tuning

> [!NOTE]
> 1ST REVIEWED

<br>

<a id="node-z1fkwds"></a>

#### Tuning Process

<br>

<a id="node-8gm03q6"></a>

##### 1 There are a lot of hyperparameters that need to be set when training deep
neural networks, such as \\*learning rate\\*, \\*momentum term\\*,\\* number of layers,\\*
number of hidden units, mini-batch size, and learning rate decay.

2 Some of these hyperparameters are \\*more important than others\\*. \\*Learning
rate\\* is the\\* most important,\\* followed by \\*momentum term\\*, \\*mini-batch size\\*,
and number of \\*hidden units.\\*

3 It's difficult to know in advance which hyperparameters will be the most
important, so it's important to\\* try out a wide range of values\\*.

4 \\*Sampling at random\\* is a \\*better approach\\* than systematically exploring
values in a \\*grid\\* because it allows for a \\*more rich exploration\\* of the
hyperparameter space.

5\\* Coarse to fine sampling\\* is a \\*common practice\\* that involves \\*zooming\\* \\*in\\* on
\\*promising areas\\* of the \\*hyperparameter space\\* and exploring more densely
within that area.

<br>

<a id="node-nlhjb19"></a>

<p align="center"><kbd><img src="assets/2qzsbq46ae4.png" width="80%"></kbd></p>

<br>

<a id="node-4u6qkc1"></a>

<p align="center"><kbd><img src="assets/xzr2c8axxx.png" width="80%"></kbd></p>

> [!NOTE]
> Khó biết được hyperparam nào là quan trọng (khiến Model tốt)
>
>
>
> Nên thay vì làm theo kiểu Grid như hồi đầu của ML, bây giờ
> nên chọn **Random** .

<br>

<a id="node-jf0mvsl"></a>

<p align="center"><kbd><img src="assets/4bj5nq3yoyf.png" width="80%"></kbd></p>

> [!NOTE]
> Khi thấy 'vị trí' nào cho kết qua tốt -> Zoom vào khu
> vực đó **(Coarse to fine)**

<br>

<a id="node-o133qv4"></a>

- **1 Hyperparameters in neural networks: Neural networks involve setting a lot of different
hyperparameters, ranging from the learning rate alpha to the momentum term beta, the
hyperparameters for the Adam Optimization Algorithm (beta one, beta two, and epsilon), the
number of layers, the number of hidden units for the different layers, and the mini-batch size.

2 Importance of hyperparameters: Some of these hyperparameters are more important than
others. The most important hyperparameter to tune is usually the learning rate alpha. Other
hyperparameters that should be considered next include the momentum term (0.9 is a good
default), the \\*mini-batch size\\* (to ensure the optimization algorithm is running efficiently), and the
hidden units.

3 \\*Tuning\\* \\*hyperparameters\\*: How do you go about finding a good setting for these
hyperparameters? It's important to \\*systematically organize your hyperparameter\\* tuning process
to make it more efficient for you to converge on a good setting of the hyperparameters.

4 \\*Sampling\\* hyperparameters: In earlier generations of machine learning algorithms, if you had
two hyperparameters, it was common practice to sample the points in a grid and systematically
explore these values. However, in deep learning, it's better to choose the\\* points at random\\* to try
\\*out on a randomly chosen set of points\\*. This is because it's difficult to know in advance which
hyperparameters are going to be the most important for your problem.

5 Importance of sampling at random: Some hyperparameters are \\*much more important than
other\\*s. If you sample in a grid, you might find that you' ve only tried out a few values of the most
important hyperparameter, while having tried out many different values of a less important
hyperparameter. Sampling at random helps to explore a \\*more diverse set of possible values for
the most important hyperparameters\\*, whatever they turn out to be.

6 \\*Coarse to fine sampling\\* scheme: Another common practice when sampling hyperparameters is
to use a \\*coarse to fine sampling scheme\\*. This involves \\*starting with a larger set of
hyperparameters\\* and then \\*zooming in to a smaller region\\* of the hyperparameters to sample
m\\*ore densely within this space.\\* This can help to\\* focus more resources on searching within the
most promising regions\\* of hyperparameters.**

<br>

<a id="node-n5ysdo2"></a>

#### Using An Appropriate Scale To Pick Hyperparameters

<br>

<a id="node-3jjsjb1"></a>

##### 1\\* Random sampling\\* over hyperparameters allows \\*efficient search\\* over their
space.

2 It is \\*important\\* to pick the \\*appropriate scale\\* on which to explore the
hyperparameters.

3 \\*Sampling uniformly at random \\*over the range of hyperparameters might be
\\*reasonable for certain hyperparameters,\\* such as the \\*number of hidden units\\*
and \\*layers\\* in a neural network.

4 It is\\* not reasonable\\* to sample uniformly at random over the range of all
hyperparameters.

5 Searching for hyperparameters on a\\* log scale\\* is \\*more reasonable\\*, especially
for hyperparameters such as the \\*learning rate.\\*

6 To sample on a log scale, you need to take the \\*low\\* and \\*high values\\*, take
\\*logs\\* to figure out what \\*a\\* and\\* b\\* are, sample \\*r\\* \\*uniformly between a and b\\*, and
set the \\*hyperparameter to be 10 to the power of r.\\*

7 Sampling for the hyperparameter \\*beta\\* used for computing exponentially
weighted averages is \\*tricky\\* and \\*should not be\\* \\*sampled on a linear scale.
\\*
8 To explore the r\\*ange of values for beta\\*, it is important to \\*consider the range
of values for the corresponding exponentially weighted average\\*s.

<br>

<a id="node-771htso"></a>

<p align="center"><kbd><img src="assets/u5shgl9856.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ như ta đang chọn random số hidden unit cho layer mà
> Ta nhắm chừng trong khoảng 50 - 100, thế là lẽ dĩ nhiên ta
> lấy random vài giá trị trong khoảng này.
>
>
>
> Hoặc số layer nhắm chừng trong khoảng 2,3,4, ta cứ thử từng 
> cái 2,3,4..
> Thì đại khái là cái hyperparam kiểu này ta làm vâỵ được, nhưng đối 
> với cái khác thì không....

<br>

<a id="node-kfforzp"></a>

<p align="center"><kbd><img src="assets/cu89204bx87.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ như alpha nhắm trong khoảng từ 0.001 tới 1
> Nếu ta cũng làm như cách làm ở thằng hidden unit
> thì đại khái là ta sẽ 90% là chọn alpha từ 0.1-1. chỉ còn 10%
> từ 0.001-0.1
> 90 hay 10 là đại ý nói do cái **scale nó ko bằng nhau** nên 
> không làm vậy được.
>
>
>
> Thay vào đó phải làm theo kiểu lấy **log**.
>
>
>
> Ví dụ muốn lấy từ 0.0001 - 1. Thừ xem **0.0001** là log(a) **a bao nhiêu**.
> **1** là log(b) -> **b bao nhiêu.**
> -> Dẫn tới bài toán chọn **r random trong đoạn [a,b]** -> **alpha = 10^r**

<br>

<a id="node-brctsog"></a>

<p align="center"><kbd><img src="assets/bz0v4azi508.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự như vậy với beta.
>
>
>
> Nhớ lại (1-epsilon)^(1/epsilon)
>
>
>
> 0.9000 -> 0.9005: Tăng 0.0005
> Beta = 0.9 -> epsilon = 0.1 -> 1/epsilon = 10 thì hiểu đại khái là nó lấy 
> Trung bình của 10 ngày trước đó.
> Beta = 0.9005 -> Epsilon = 0.095 -> 1/epsilon cũng cỡ 10 (10,05)
>
>
>
> 0.9990 -> 0.9995: Cũng tăng 0.0005
> Beta = 0.9990 -> epsilon = 0.001 -> 1/epsilon = 1000
> Beta = 0.9995 -> epsilon = 0.0005 -> 1/epsilon = 2000
>
>
>
> Có nghĩa là trong đoạn cùng là 0.0005 mà mức ảnh hưởng của nó
> hoàn toàn khác nhau

<br>

<a id="node-mfm3smk"></a>

<p align="center"><kbd><img src="assets/cuvbe954vjm.png" width="80%"></kbd></p>

<br>

<a id="node-gwe799i"></a>

- **1 Sampling hyperparameters at random can be an efficient way to search over their
space, but it's important to pick the appropriate scale to explore them.

2 Uniformly sampling hyperparameters may not be appropriate for all ranges of values.
For example, when searching for the learning rate alpha, using a linear scale from 0.0001
to 1 would result in sampling mostly from the range of 0.1 to
1. Instead, it's better to use a logarithmic scale where values are spaced equally on the
log scale.

3 To sample on a logarithmic scale in Python, you can use the following code:  • Let r = -4
* np.random.rand()  • A randomly chosen value of alpha would then be alpha = 10 to the
power of r  • This results in alpha being sampled between 10 to the -4 and 10 to the 0

4 In a more general case, if you want to sample between 10 to the a and 10 to the b on a
log scale, you can use the following steps:  • Take the log base 10 of the low value to find
a  • Take the log base 10 of the high value to find b  • Sample r uniformly at random
between a and b  • Set the hyperparameter to be 10 to the r

5 Another tricky case is sampling the hyperparameter beta used for computing
exponentially weighted averages. In this case, it's important to understand the effect of
changing the value of beta on the average. Using a linear scale to sample beta between
0.9 and 0.999 may not be effective since the values are spaced closely together near 0.
999. Instead, a good way to sample beta is to use the formula beta = 1 - 10 to the power
of -x, where x is sampled uniformly at random between 1 and 4.

6 Overall, it's important to understand the range of values that each hyperparameter can
take and to choose an appropriate scale for sampling in order to efficiently explore their
space.**

<br>

<a id="node-ezrhn31"></a>

#### Hyperparams Tuning In Practice: Pandas Vs. Caviar

<br>

<a id="node-71t37ac"></a>

##### 1 Intuitions about hyperparameter settings from one application
area may or may not transfer to a different one, but
\\*cross-fertilization among different domains\\* is \\*increasingly
common\\*.

2 \\*Hyperparameter settings\\* can get \\*stale\\* due to \\*changes\\* in \\*data\\*
or \\*computational resources,\\* so it's recommended to \\*retest\\* or
\\*reevaluate hyperparameters\\* at least once \\*every several months.\\*

3 Two \\*major ways\\* of searching for hyperparameters are the
\\*panda approac\\*h, where \\*one model\\* is \\*gradually tweaked\\*, and the
\\*caviar approach\\*, where \\*many mode\\*ls are trained \\*in parallel \\*and
the b\\*est one is chosen.\\*

4 The choice between the two approaches \\*depends on the
amount of computational resources\\* available.

<br>

<a id="node-1e0rfmx"></a>

<p align="center"><kbd><img src="assets/b5thtxlp28f.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nên **retest hyperparams vài tháng một lần** vì
> những **sự thay đổ**i có thể khiến cái mình đã tune ngon 
> hết ngon
> Ví dụ: Data thay đổi, server khác, 
>
>
>
> Còn chuyển từ domain này qua domain khác thì đại ý là 
> Deep learning nó có ưu điểm là kế thừa được những cái từ
> domain khác, nhưng hyperparam thì không, phải tune lại.

<br>

<a id="node-updgz7v"></a>

<p align="center"><kbd><img src="assets/0gv40brrsp2g.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là máy mạnh thì **chạy nhiều model cùng lúc** rồi **xem
> cái nào ngon nhất**.-> Như cá hồi đẻ trứng
>
>
>
> Còn không thì c**hăm như chăm con**, từng ngày từng ngày 
> theo dõi và điều chỉnh. Ví dụ ngày thứ 2 thử giảm alpha xuống 
> Qua thứ 3 thấy ok, thử cái khác qua thứ 4 thấy nó không ổn,
> liền quay lại setting của ngày thứ 3, thử setting khác -> Chăm 
> như chăm con

<br>

<a id="node-5azg99p"></a>

- **1 Importance of \\*cross-fertilization\\* in deep learning:  2 Deep learning is applied in various application
areas, and\\* intuitions about hyperparameter settings\\* from one area \\*may or may not transfer\\* to a
different one. However, there is a lot of \\*cross-fertilization among different application domains\\*, with
researchers reading increasingly from other domains to look for inspiration for cross-fertilization. For
example, ideas developed in \\*computer vision\\*, such as \\*ConVnets\\* or \\*ResNets\\*, have been successfully
applied to \\*speech\\*, and vice versa.

3 The risk of \\*stale hyperparameter settings:\\*  4 Intuitions about the \\*best hyperparameter settings can get
stale over time,\\* even when working on the same problem. For instance, a good setting that was once
found may \\*no longer work\\* due to c\\*hanges in data or hardware\\*. Therefore, it is recommended to \\*retest\\*
or \\*reevaluate\\* \\*hyperparameters\\* \\*periodically\\*, maybe at least\\* once every several months\\*, to ensure that
the current hyperparameter values are\\* still suitable.\\*

5 Two major \\*schools of thought \\*in \\*hyperparameter search\\*:  6 There are two major ways in which people
go about searching for hyperparameters: \\*babysitting\\* one model and \\*training\\* many models in \\*parallel\\*.

7 \\*Babysitting\\* one model:  8 If c\\*omputational resources are limited\\*, then one approach is to \\*babysit\\* one
model by \\*gradually nudging up\\* and \\*down the parameters\\*. For example, one might initialize the
parameters randomly and start training, then gradually watch the learning curve, maybe the cost
function or dataset error, gradually decrease over the first day. At the end of the day, one might try
increasing the learning rate a little bit and see how it performs, and then adjust the parameters again
the following day, and so on. The approach is called the p\\*anda approach\\*, as it is similar to how pandas
have few children and \\*put a lot of effort into ensuring their survival\\*.

9 Training\\* many models in parallel:\\*  10 If there are \\*enough computational resources\\*, then one can train
\\*many models\\* in \\*parallel\\* with \\*different hyperparameters\\*. Each model generates its \\*own learning curve\\*,
and the \\*best hyperparameter setting\\* is selected based on\\* which model performs the best\\*. This
approach is called the \\*caviar strategy\\*, as it is similar to how fish reproduce by laying many eggs and not
paying too much attention to any one of them.

11 Choosing between the two approaches:  12 The choice between the two approaches is mainly a
function of how \\*much computational resources are available\\*. If there are enough resources, then the
caviar strategy can be used to try a lot of different hyperparameter settings and select the best one
\\*quickly\\*. However, if \\*resources are limited\\*, then the panda approach can be used to gradually adjust the
hyperparameters of one model over time.**

<br>

<a id="node-gaymba5"></a>

### Batch Normalization

> [!NOTE]
> 1ST REVIEWED

<br>

<a id="node-0ekepse"></a>

#### Clarification About Upcoming
normalization Activations In A Network

<br>

<a id="node-x9kl1o7"></a>

##### ...

<br>

<a id="node-0jj4800"></a>

<p align="center"><kbd><img src="assets/l98xticnt5.png" width="80%"></kbd></p>

<br>

<a id="node-ifvxs4e"></a>

#### Normalization Activations In A Network

<br>

<a id="node-47f2rjb"></a>

##### 1 Batch normalization is a deep learning algorithm that was created by
Sergey Ioffe and Christian Szegedy.

2 Batch normalization can make the hyperparameter search problem much
easier, make neural networks more robust, and enable easy training of very
deep networks.

3 Normalizing input feature values can speed up learning in models such as
logistic regression.

4 Batch normalization can be used to normalize the mean and variance of
activations in hidden layers.

5 Batch normalization normalizes the values of z before the activation
function is applied, and this is done much more often in practice.

6 To implement batch norm, you compute the mean and variance of
intermediate values, normalize the values using mean and variance, and
use learnable parameters gamma and beta to set the mean and variance of
the normalized values to desired values.

7 Gamma and beta parameters can be updated using gradient descent or
other algorithms, just like the weights of a neural network.

<br>

<a id="node-bbxklx4"></a>

<p align="center"><kbd><img src="assets/vpy2jto8o0i.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cũng như normalization đ.v X giúp ích cho việc training
> thì normalize các hidden unit output cũng vậy.

<br>

<a id="node-s9t9zx3"></a>

<p align="center"><kbd><img src="assets/m2wbstly7vt.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4z4ifc0vm42.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây nó cũng normalize Theo kiểu tương tự 
> feature scaling (-mu) + mean normalization (/sigma)
>
>
>
> Nhưng có cái là 'không muốn cho mean = 0 để tận dụng khả
> năng của hàm sigmoid gì gì đó nên thay vì dùng
> z_norm, dùng z~ (Đọc là z tilde) = Gamma*z_norm + beta và Train
> Gamma và Beta như W, b.
>
>
>
> Chưa hiểu thì từ từ sẽ hiểu
>
> Đại khái là nếu data chỉ loanh quanh quanh
> mốc z = 0 thì sigmoid(z) chỉ loanh quanh mốc 0.
> 5 và đoạn này nó khá tuyến tính nên nó sẽ
> không tận dụng được khả năng phi tuyến tính
> của hàm sigmoid

<br>

<a id="node-jeiu3jy"></a>

#### Fitting Batch Norm Into A Neural Network

<br>

<a id="node-uj8cooe"></a>

##### 1 Introduction to deep neural networks as a series of computations with
multiple layers, each layer computing two things: Z and A.

2 Traditional process of computing Z and A without Batch Normalization.

3 Batch Normalization explained as a new layer that normalizes the Z
values using Beta and Gamma parameters, computed for each layer.

4 The intuition behind using normalized values instead of un-normalized
ones in computing the activations.

5 The new parameters added to the network for each layer where Batch
Normalization is applied.

6 Optimization methods such as gradient descent, RMSprop, and Adam
used for updating Beta and Gamma parameters.

7 Implementation of Batch Normalization in deep learning frameworks.

8 Mini-batch processing used in applying Batch Normalization during
training.

<br>

<a id="node-1o4hxcb"></a>

<p align="center"><kbd><img src="assets/y7mo1jf5s57.png" width="80%"></kbd></p>

> [!NOTE]
> Thêm bước tính từ z -> z ~ (z tilde) nữa
>
>
>
> Và training thêm d_beta và d_gamma nữa
> (update beta, gamma như W, b bằng G.D vậy
>
>
>
> Nếu dùng Framework như TensorFlow thì không
> cần làm chỉ cần khai báo nó tự làm. Nói chung là
> chỉ cần hiểu nó làm gì là được.

<br>

<a id="node-jef7ys2"></a>

<p align="center"><kbd><img src="assets/2fk76e31fa.png" width="80%"></kbd></p>

> [!NOTE]
> 1. Thường là làm việc với Mini-batch, thì nó sẽ như vầy, như vầy..
> Các step normalize (Batch norm) sẽ chỉ đ.v từng mini. batch 
>
>
>
> 2. Với Batch-norm thì param b trở nên vô nghĩa, nên có thể bỏ.
>
>
>
> 3.Beta[l] Gamma[l] sẽ cùng size / shape (n[l], 1) với b[l]

<br>

<a id="node-9zwysay"></a>

<p align="center"><kbd><img src="assets/83tti4gvwqs.png" width="80%"></kbd></p>

> [!NOTE]
> Put them together

<br>

<a id="node-fr659p9"></a>

#### Why Does Batch Norm Work

<br>

<a id="node-lkml28m"></a>

##### 1 Batch normalization speeds up learning by normalizing all input features to take
on a similar range of values.

2 Batch normalization makes weights deeper in a network more robust to changes
to weights in earlier layers by addressing the problem of covariate shift.

3 Covariate shift occurs when the distribution of X changes, and it becomes
necessary to retrain a learning algorithm even if the ground truth function mapping
from X to Y remains unchanged.

4 From the perspective of a certain layer in a deep network, it gets some values
from the earlier layers and has to map them to Y-hat, but these values change as
the parameters in earlier layers change, causing the problem of covariate shift.

5 Batch normalization reduces the amount that the distribution of hidden unit
values shifts around, ensuring that their mean and variance remain the same,
making the network more robust to the problem of covariate shift.

<br>

<a id="node-dmflnsa"></a>

<p align="center"><kbd><img src="assets/hubft9xsa1w.png" width="80%"></kbd></p>

> [!NOTE]
> **Covariate shift.** 
> And the idea is that, if you've learned some X to Y mapping, 
> if the distribution of X changes, then you might need to retrain 
> your learning algorithm.

<br>

<a id="node-252sf7i"></a>

<p align="center"><kbd><img src="assets/39ac4gdc51r.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/skrnton6uz.png" width="80%"></kbd></p>

> [!NOTE]
> "So from the perspective of the third hidden layer, these hidden unit
> values are changing all the time, and so it's suffering from  the problem
> of covariate shift" 
> Đại khái là params được update liên tục dẫn đến cái **"DISTRIBUTION
> CỦA INPUT CỦA HIDDEN LAYER"** thay đổi liên tục nên gây khó khăn
> cho quá trình training. -> Batch Norm giúp fix vấn đề này

<br>

<a id="node-rph5l80"></a>

<p align="center"><kbd><img src="assets/7e0zslm2opl.png" width="80%"></kbd></p>

<br>

<a id="node-hqi3m3t"></a>

<p align="center"><kbd><img src="assets/9mqrrt2jq0a.png" width="80%"></kbd></p>

> [!NOTE]
> **Covariate shift:** This is the phenomenon where the
> **distribution of the inputs to a layer changes during training**,
> which makes it difficult for the network to learn. By normalizing the
> inputs to each layer, batch normalization reduces the internal
> covariate shift, which can make it easier for the network to learn.

<br>

<a id="node-yjnqrdo"></a>

#### Batch Norm At Test Time

<br>

<a id="node-yx305wy"></a>

##### 1 Batch normalization processes data in mini batches during
training.

2 During training, mean and variance are computed on the
entire mini batch.

3 During test time, processing a single example at a time, you
need to estimate mean and variance from training data.

4 Exponentially weighted averages are used to estimate mean
and variance from training data.

5 At test time, use the estimated mean and variance to scale
the test example.

6 Deep learning frameworks usually have default ways to
estimate mean and variance.

7 Using batch normalization can help train deeper networks
and improve learning algorithm efficiency.

<br>

<a id="node-lmw15sb"></a>

<p align="center"><kbd><img src="assets/ut5nl1rloes.png" width="80%"></kbd></p>

> [!NOTE]
> But that test time, you might need to process a single example at
> a time. So, the way to do that is to estimate mu and sigma
> squared from your training set and there are many ways to do
> that. You could **in theory run your whole training set through
> your final  network to get mu and sigma squared**. But in
> practice, what people  usually do is implement and exponentially
> weighted average where  you **just keep track of the mu and
> sigma squared values you're  seeing during training** and use
> and exponentially the weighted  average, also sometimes called
> the running average, to just get a  rough estimate of mu and
> sigma squared and then you use those  values of mu and sigma
> squared that test time to do the scale and  you need the head
> and unit values Z

<br>

<a id="node-v8rkj0s"></a>

### Multiclass Classification

<br>

<a id="node-u9hu9xe"></a>

#### Clarification About Upcoming Softmax

<br>

<a id="node-lbeha3b"></a>

##### ...

<br>

<a id="node-cofydg7"></a>

<p align="center"><kbd><img src="assets/80m11anjsk7.png" width="80%"></kbd></p>

<br>

<a id="node-t12fro9"></a>

#### Softmax Regression

<br>

<a id="node-b72tznm"></a>

##### 1 \\*Binary\\* \\*classification\\* involves two possible labels, \\*0\\* or \\*1\\*.

2 \\*Softmax\\* \\*regression\\* is a \\*generalization\\* of \\*logistic regression\\* used
for recognizing \\*multiple classes\\*.

3 Softmax regression uses a \\*Softmax\\* \\*layer\\* to generate the
\\*probabilities\\* for \\*each of the classes\\*.

4 The number of \\*units\\* in the \\*Softmax\\* layer is \\*equal to the number
of classes\\*.

5 The \\*Softmax\\* \\*activation\\* \\*function\\* computes a temporary variable, t,
which is e to the power of the output of the final layer.

6 The output of the Softmax activation function, aL, is the vector t
normalized to sum to 1.

7 The i-th element of the output vector aL represents the p\\*robability
of the input belonging to the i-th class\\*.

8 The \\*probabilities\\* generated by the Softmax layer should \\*sum to 1.\\*

<br>

<a id="node-b6smri9"></a>

<p align="center"><kbd><img src="assets/5iag3qv5hry.png" width="80%"></kbd></p>

<br>

<a id="node-036ssvg"></a>

<p align="center"><kbd><img src="assets/57lfwzr8xb.png" width="80%"></kbd></p>

<br>

<a id="node-r07hclc"></a>

<p align="center"><kbd><img src="assets/sg1wmenjf8.png" width="80%"></kbd></p>

<br>

<a id="node-1ldlylu"></a>

- **1 Softmax regression is a generalization of logistic regression for multiple classes. Instead of just
recognizing two classes, Softmax regression allows you to recognize \\*one of C possible classes,\\*
where C is the number of classes you're trying to categorize your inputs into.

2 To use Softmax regression, you need to build a new neural network where the upper layer has
C units. The goal is for each unit to output the probability of its corresponding class, given the
input x.

3 The output labels y hat in Softmax regression are a C by 1 dimensional vector, where each
element represents the \\*probability of its corresponding class.\\*

4 Because \\*probabilities should sum to one\\*, the \\*elements in y hat should also sum to one.\\*

5 The standard model for Softmax regression uses a \\*Softmax layer\\* in the output layer to generate
these probabilities. The Softmax activation function is used to compute the output of the final
layer.

6 The \\*Softmax\\* activation function takes the\\* linear part\\* of the layer (\\*zL\\*) and computes a temporary
variable (t), which is e to the zL (element-wise). Then, the output aL is computed by normalizing t
to sum to one. This ensures that the elements in aL \\*represent probabilities that sum to one.\\*

7 In the Softmax layer, the output aL is a C by 1 dimensional vector, where each element
represents the probability of its corresponding class. The i-th element of aL is computed as ti
divided by the sum of all the ti's, where ti is the i-th element of the vector t.

8 An example is given to illustrate how the Softmax activation function works. In the example, zL
is a four-dimensional vector: 5, 2, -1, 3. Using the Softmax activation function, we compute t,
which is e to the 5, e to the 2, e to the -1, e to the 3. We then normalize t to sum to one, which
gives us the output aL, where each element represents the probability of its corresponding class.**

<br>

<a id="node-jedrl33"></a>

#### Training A Softmax Classifier

<br>

<a id="node-ytfcji0"></a>

##### 1 Softmax activation function was introduced in the previous video and
in this video, we will deepen our understanding of softmax classification
and learn about the training model that uses a softmax layer.

2 Softmax classification generalizes the logistic activation function to C
classes and if C=2, then softmax with C=2 essentially reduces to logistic
regression.

3 The loss function used in softmax classification is the negative sum of
j=1 through C of yj log yhat j, where yj is the true label and yhat j is the
predicted probability of the class j.

4 The loss function tries to make the corresponding probability of the
true class as high as possible, which is a form of \\*maximum likelihood
estimation.\\*

5 To reduce the loss on the training set, the neural network adjusts the
predicted probability of the true class.

<br>

<a id="node-o1snkdv"></a>

<p align="center"><kbd><img src="assets/boxjjym666g.png" width="80%"></kbd></p>

<br>

<a id="node-ka9x1i3"></a>

<p align="center"><kbd><img src="assets/bdmw2yeudw.png" width="80%"></kbd></p>

> [!NOTE]
> Hiểu đại khái Machine nó sẽ muốn làm gì:
> Muốn min L thì phải min Sum y_iLog(y^_i), mà y_1, y_3, y_4 = 0 
> -> Phải min y_2log(y^_2) mà y_2 = 1 
> -> Phải min log(y^_2)
> -> Phải max y^_2
>
>
>
> Softmax thật ra là mở rộng khái quát hoá của Logistic Regression

<br>

<a id="node-uudnrrx"></a>

<p align="center"><kbd><img src="assets/q7ha4d6u4kr.png" width="80%"></kbd></p>

> [!NOTE]
> Programming assignment này sẽ bắt đầu dùng Framework 
> (TensorFlow) nên chỉ cần ForProp, BackProp nó sẽ làm giùm
> mình nhưng đại khái cũng giống cách tính BackProp bữa trước
> làm thôi, chỉ có cái là h y nó có C hàng chứ 1 ko phải 1 hàng

<br>

<a id="node-oh68s47"></a>

### Introduction To Programming Frameworks

<br>

<a id="node-bdqhbq4"></a>

#### Deep Learning Frameworks

<br>

<a id="node-apo8g2h"></a>

##### 1 Deep learning algorithms can be implemented from scratch using Python and
NumPY, but more complex models may require the use of deep learning software
frameworks.

2 Implementing everything yourself from scratch becomes increasingly impractical as
models get larger and more complex.

3 There are now many good deep learning software frameworks available to help
implement complex models, such as convolutional neural networks and recurring
neural networks.

4 Choosing a framework depends on several factors, including ease of programming,
running speeds, and whether or not the framework is truly open.  5 Some popular
deep learning frameworks include TensorFlow, PyTorch, Keras, and Caffe.

6 Each of these frameworks has a dedicated user and developer community, and
each is a credible choice for some subset of applications.

7 The criteria recommended for choosing a framework include ease of programming,
running speeds, and whether or not the framework is truly open.

8 Truly open frameworks are those that are not only open source but also have good
governance and are not under the control of a single company.

9 Multiple frameworks could be a good choice depending on the user's preferences
and the application they are working on.

10 Using a deep learning software framework can make development of machine
learning applications more efficient by providing a higher level of abstraction than just
a numerical linear algebra library.

<br>

<a id="node-ztxleca"></a>

<p align="center"><kbd><img src="assets/n3lgyjkubhn.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là khi làm các bài toán lớn thì sử dụng các lib sẽ giúp 
> ta tiện hơn

<br>

<a id="node-6kcy2c6"></a>

<p align="center"><kbd><img src="assets/4zwrtufs3ze.png" width="80%"></kbd></p>

> [!NOTE]
> Các Framework này improve liên tục và đây là 1 số tiêu chí để chọn F.W

<br>

<a id="node-iomp9re"></a>

#### Tensorflow

<br>

<a id="node-in587y0"></a>

<p align="center"><kbd><img src="assets/c00x16y1vit.png" width="80%"></kbd></p>

<br>

<a id="node-nzi7yaw"></a>

<p align="center"><kbd><img src="assets/odjr0v85rk.png" width="80%"></kbd></p>

<br>

<a id="node-4eyxe3i"></a>

<p align="center"><kbd><img src="assets/zruppetbir.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là T.S nó sẽ tự tính BackProp

<br>

<a id="node-8zdb51k"></a>

#### Learn About Gradient Tape And More

<br>

<a id="node-0wncnxy"></a>

<p align="center"><kbd><img src="assets/xjvew49zsa.png" width="80%"></kbd></p>

<br>

<a id="node-bom33rb"></a>

### Quiz

<br>

<a id="node-i74z08t"></a>

<p align="center"><kbd><img src="assets/m7cgutquet.png" width="80%"></kbd></p>

<br>

<a id="node-l7t0rxh"></a>

<p align="center"><kbd><img src="assets/0813bohi31t.png" width="80%"></kbd></p>

> [!NOTE]
> Không 'equally' vì rõ ràng Alpha quan trọng hơn Epsilon nhiều

<br>

<a id="node-y3qagqs"></a>

<p align="center"><kbd><img src="assets/nyndpv60wxh.png" width="80%"></kbd></p>

> [!NOTE]
> Này quá rõ, nếu máy mạnh thì chạy nhiều cái cùng lúc

<br>

<a id="node-ukasizo"></a>

<p align="center"><kbd><img src="assets/jpqy3pqsbo.png" width="80%"></kbd></p>

<br>

<a id="node-6p6vt8j"></a>

<p align="center"><kbd><img src="assets/xiumoxs2s9q.png" width="80%"></kbd></p>

<br>

<a id="node-9x5pzs2"></a>

<p align="center"><kbd><img src="assets/srurewq0nu.png" width="80%"></kbd></p>

<br>

<a id="node-cyrc79p"></a>

<p align="center"><kbd><img src="assets/3cxercr5itn.png" width="80%"></kbd></p>

<br>

<a id="node-pq7muaf"></a>

<p align="center"><kbd><img src="assets/paluwv119aa.png" width="80%"></kbd></p>

> [!NOTE]
> Beta gammar được train như Web bằng G.D ...nên câu
> đầu sai, câu 2 đúng.
>
>
>
> Beta[l], gammae[l] cũng như, b[l] là. vector mỗi unit 1 cái
> nên không phải là 1 R cho cả layer -> Câu 3 sai
>
>
>
> Câu 4 sai vì ko phải là Optimal value, mà đó là value khiến
> cho  Gamma và Beta vô nghĩa (Khiến Z~ bằng Z)
>
>
>
> Câu 5 đúng

<br>

<a id="node-q0tw59l"></a>

<p align="center"><kbd><img src="assets/ffswo3zil9b.png" width="80%"></kbd></p>

> [!NOTE]
> Sai vì vẫn có tính Batch Norm

<br>

<a id="node-l02t7yc"></a>

<p align="center"><kbd><img src="assets/bjok07xdab.png" width="80%"></kbd></p>

<br>

<a id="node-mu354zt"></a>

### Programming Assignment

<br>

<a id="node-4b4j39f"></a>

#### Introduction to TensorFlow

<br>

<a id="node-podorp1"></a>

##### .

<br>

<a id="node-1eqkg0m"></a>

<p align="center"><kbd><img src="assets/vcmvoj53o7h.png" width="80%"></kbd></p>

<br>

<a id="node-gi2ty19"></a>

<p align="center"><kbd><img src="assets/50kt4l2qoca.png" width="80%"></kbd></p>

<br>

<a id="node-bg6sqf6"></a>

##### Checking TensorFlow Version

<br>

<a id="node-oe3wtuy"></a>

#### 2 - Basic Optimization with GradientTape

<br>

<a id="node-zuzgibf"></a>

#### Basic Optimization with GradientTape

<br>

<a id="node-xgxylmq"></a>

<p align="center"><kbd><img src="assets/7tqbmag1069.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/e7u29urcdht.png" width="80%"></kbd></p>

<br>

<a id="node-vkjpirq"></a>

<p align="center"><kbd><img src="assets/g3u73cg7w7p.png" width="80%"></kbd></p>

<br>

<a id="node-gcnbf8p"></a>

<p align="center"><kbd><img src="assets/rvzr0r58sn9.png" width="80%"></kbd></p>

<br>

<a id="node-k2crpfc"></a>

#### 2.1 - Linear Function

> [!NOTE]
> Làm quen với TF Khai báo
> Constant với tf.constant() .
> tf.matmul(), tf.add() Tính
> thử Y = WX + b bằng T.F

<br>

<a id="node-7rml2z4"></a>

<p align="center"><kbd><img src="assets/3td0cu6mhxe.png" width="80%"></kbd></p>

<br>

<a id="node-4dk484k"></a>

##### Exercise 1 - linear_function

<br>

<a id="node-6swfk2s"></a>

<p align="center"><kbd><img src="assets/76t3ctzdevi.png" width="80%"></kbd></p>

<br>

<a id="node-lvg6qe6"></a>

<p align="center"><kbd><img src="assets/ckcdhx5vps4.png" width="80%"></kbd></p>

<br>

<a id="node-t8mf5q9"></a>

#### 2.2 - Computing the Sigmoid

> [!NOTE]
> Làm quen với TF
> tf.keras.activation.sigmoid()
> tf.cast(.., tf.float32)

<br>

<a id="node-lmq1pju"></a>

<p align="center"><kbd><img src="assets/92e25xvdm7l.png" width="80%"></kbd></p>

<br>

<a id="node-a6l3o4e"></a>

##### Exercise 2 - sigmoid

<br>

<a id="node-1kdktzo"></a>

<p align="center"><kbd><img src="assets/nb8cyiwy49.png" width="80%"></kbd></p>

<br>

<a id="node-liqz3hx"></a>

<p align="center"><kbd><img src="assets/yu4ht92z7w.png" width="80%"></kbd></p>

<br>

<a id="node-6g2ljcr"></a>

#### 2.3 - Using One Hot Encodings

> [!NOTE]
> One hot encoding with TF
> Dùng tf.one_hot(labels, depth)
> và tf.reshape(.., [-1, ]) để

<br>

<a id="node-xzj0cm2"></a>

<p align="center"><kbd><img src="assets/shpu9kcn7il.png" width="80%"></kbd></p>

<br>

<a id="node-2jle8bg"></a>

##### Exercise 3 - one_hot_matrix

<br>

<a id="node-jowutw4"></a>

<p align="center"><kbd><img src="assets/iy07fuhf2i.png" width="80%"></kbd></p>

<br>

<a id="node-r1ptinw"></a>

<p align="center"><kbd><img src="assets/g0ceesfvpft.png" width="80%"></kbd></p>

<br>

<a id="node-8720fun"></a>

<p align="center"><kbd><img src="assets/n7i680fw4ca.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/fyx5gx7ythv.png" width="80%"></kbd></p>

> [!NOTE]
> Argument -1 có nghĩa là để nó tự chuyển thành 1D vector size bằng
> mấy cái kia nhân lại (dồn lại hết thành 1 row)

<br>

<a id="node-ilyty3t"></a>

#### 2.4 - Initialize the Parameters

> [!NOTE]
> Initialize bằng GlorotNormal.

<br>

<a id="node-j5hkmz3"></a>

<p align="center"><kbd><img src="assets/ktkuyxiexhr.png" width="80%"></kbd></p>

<br>

<a id="node-p6447f6"></a>

##### Exercise 4 - initialize_parameters

<br>

<a id="node-9dtsf2n"></a>

<p align="center"><kbd><img src="assets/lrfe9k5s7gq.png" width="80%"></kbd></p>

<br>

<a id="node-zsfvm0m"></a>

<p align="center"><kbd><img src="assets/y4718nyq8p.png" width="80%"></kbd></p>

<br>

<a id="node-rlb1elh"></a>

#### 3 - Building Your First Neural Network in TensorFlow

<br>

<a id="node-z2otbqz"></a>

#### 3.2 Compute the Total Loss

> [!NOTE]
> Viết hàm tính loss function dùng TF's 
> categorical_crossentropy(logits, labels)
>
>
>
> Cứ tưởng kẹt ở Excersie này, người ta đã gợi ý là phải đảm
> bảo argument's shape đúng mà. Có điều không có nói vụ 
> **from_logits** khiến mò mãi mới đúng
>
>
>
> 1. Chú ý thứ tự argument, **(labels, logits)**
>
>
>
> 2. Vì yêu cầu shape = (no. examples - m, no. features - n) nên
> phải **transpose**. Với TF, dùng **tf.transpose()**
>
>
>
> 3.Phải thêm **from_logits = True** mới đúng
>
> **from_logits = True** có nghĩa là Y^ (output của last layer
> trong n.n) vẫn ở dạng 'raw output', không phải dạng '
> Probability'.
>
>
>
> Layer cuối cùng nó để Linear (tức là tính tính Z3 = Z[L] =
> W[L]. A[L-1] + b[L] và không tính A[L] hay nói cách khác g[L] =
> L (không áp dụng hàm rêu hay sigmoid gì cả)  Để rồi mới bỏ
> Z[L] đó vào Softmax để tính ra Probability
>
>
>
> Thì đây cũng vậy, cái mà mình bỏ vào cùng với y là Z, là **raw
> output** chứ không phải là **Probability** nên phải ghi rõ
> **from_logit = True**
>
>
>
> Nếu không ghi, hoặc để = false, hàm categorical_crossentropy
> sẽ apply **Softmax** (tính ra Probability) rồi mới tính Loss

<br>

<a id="node-whs5utq"></a>

<p align="center"><kbd><img src="assets/9xr2dfvpsdc.png" width="80%"></kbd></p>

<br>

<a id="node-rq1j0sg"></a>

##### Exercise 6 - compute_total_loss

<br>

<a id="node-n95tu2d"></a>

<p align="center"><kbd><img src="assets/2dtl3kx5jwa.png" width="80%"></kbd></p>

<br>

<a id="node-wuqqqk2"></a>

<p align="center"><kbd><img src="assets/1vh9je49fhh.png" width="80%"></kbd></p>

<br>

<a id="node-ek203hu"></a>

<p align="center"><kbd><img src="assets/ebsdhnnv30c.png" width="80%"></kbd></p>

> [!NOTE]
> **from_logits = True** có nghĩa là Y^ (output của last layer
> trong n.n) vẫn ở dạng 'raw output', không phải dạng '
> Probability'.
>
>
>
> Nhớ lại, layer cuối cùng nó để Linear (tức là tính tính Z[L] =
> W[L]. A[L-1] + b[L] và không tính A[L] hay nói cách khác g[L] =
> L (không áp dụng hàm rêu hay sigmoid gì cả)  Để rồi mới bỏ
> Z[L] đó vào Softmax để tính ra Probability
>
>
>
> Thì đây cũng vậy, cái mà mình bỏ vào cùng với y là Z, là **raw
> output** chứ không phải là **Probability** nên phải ghi rõ
> **from_logit = True**
>
>
>
> Nếu không ghi, hoặc để = false, hàm categorical_crossentropy
> sẽ apply **Softmax** (tính ra Probability) rồi mới tính Loss

<br>

<a id="node-x7ihfal"></a>

<p align="center"><kbd><img src="assets/283rrxino4h.png" width="80%"></kbd></p>

<br>

<a id="node-2lgc9wu"></a>

#### 3.1 - Implement Forward Propagation

> [!NOTE]
> Forward Prop với tf
> Thay vì dùng np.dot(), relu() thì dùng 
> tf.matmul(), tf.add() và 
> tf.keras.activations.relu()

<br>

<a id="node-lm2g0ml"></a>

<p align="center"><kbd><img src="assets/vp9bwj42ntc.png" width="80%"></kbd></p>

<br>

<a id="node-914sgw6"></a>

##### Exercise 5 - forward_propagation

<br>

<a id="node-7ku8zxj"></a>

<p align="center"><kbd><img src="assets/1h9hnmbwvaa.png" width="80%"></kbd></p>

<br>

<a id="node-0psqprb"></a>

<p align="center"><kbd><img src="assets/9dt1q1rpjn.png" width="80%"></kbd></p>

<br>

<a id="node-ws2ujf4"></a>

#### 3.3 - Train the Model

> [!NOTE]
> Build modal để train dùng TF

<br>

<a id="node-t7omi73"></a>

<p align="center"><kbd><img src="assets/959ir6uio2.png" width="80%"></kbd></p>

<br>

<a id="node-vtg1qgh"></a>

<p align="center"><kbd><img src="assets/he0qgkl0lp6.png" width="80%"></kbd></p>

<br>

<a id="node-ozq0yk9"></a>

<p align="center"><kbd><img src="assets/oqzmsepo9tl.png" width="80%"></kbd></p>

<br>

<a id="node-t642oy0"></a>

<p align="center"><kbd><img src="assets/91ppe9j30vf.png" width="80%"></kbd></p>

<br>

<a id="node-84msg61"></a>

<p align="center"><kbd><img src="assets/dxo0kpvcmw9.png" width="80%"></kbd></p>

<br>

<a id="node-z96v00p"></a>

<p align="center"><kbd><img src="assets/z0lpm8mg99k.png" width="80%"></kbd></p>

<br>

<a id="node-8yd0wx6"></a>

- **optimizer = tf.keras.optimizers. Adam(learning_rate)**

> [!NOTE]
> Dùng optimizer Adam

<br>

<a id="node-c42c4v3"></a>

- **dataset = tf.data.Dataset. zip((X_train, Y_train))**

> [!NOTE]
> Đại khái là nó giúp tạo 1 Dataset modal
> để dùng cho  training bằng TF

<br>

<a id="node-mxjmzrt"></a>

<p align="center"><kbd><img src="assets/v7rdng147fk.png" width="80%"></kbd></p>

<br>

<a id="node-xkqf01z"></a>

- **grads = tape. gradient(minibatch_total_loss, trainable_variables)**

> [!NOTE]
> Notice the tape.gradient function: this allows you to
> retrieve the operations recorded for **automatic
> differentiation** inside the GradientTape block.
>
>
>
> Đây chính là bước T.F giúp mình tính Gradient dW1, db1, dW2, db2..

<br>

<a id="node-naim5pg"></a>

<p align="center"><kbd><img src="assets/3gtxwxmaml1.png" width="80%"></kbd></p>

<br>

<a id="node-ggbrxsa"></a>

- **optimizer. apply_gradients(zip(grads, trainable_variables))**

> [!NOTE]
> Then, calling the optimizer method
> **apply_gradients**, will apply the optimizer's
> update rules to each trainable parameter.
>
>
>
> Đây chính là bước mà T.F nó update W1, b1,
> W2, b2... với dW1, db1, dW2, db2...
>
>
>
> Và với optimizer là Adam thì nó sẽ update theo 
> kiểu Adam: Momentum + RMSProp

<br>

<a id="node-hre72p8"></a>

<p align="center"><kbd><img src="assets/61myjz49xh8.png" width="80%"></kbd></p>

<br>

<a id="node-de5ojbb"></a>

- **minibatches = dataset. batch(minibatch_size).prefetch(8)**

> [!NOTE]
> Đại khái là bước này giúp chuẩn bị mini-batch 
> - **Chia data thành từng Mini-batch**, và **load trước 
> 8 cái (prefetch(8))** để khi chạy cái này thì luôn có 
> sẵn 8 cái giúp nhanh hơn

<br>

<a id="node-na9ssos"></a>

<p align="center"><kbd><img src="assets/3428z3wquda.png" width="80%"></kbd></p>

<br>

<a id="node-1o04wdb"></a>

- **#We need to reset object to start measuring from 0 the accuracy each epoch
train_accuracy.reset_states()

# We accumulate the accuracy of all the batches
train_accuracy.update_state(minibatch_Y, tf.transpose(Z3))**

> [!NOTE]
> CategoricalAccuracy của TF này giúp tính độ ' accuracy'
> của Z3 và Y. Mỗi iteration/epoch reset lại để train xong thì
> update

<br>

<a id="node-0m8ajcb"></a>

<p align="center"><kbd><img src="assets/o6msu1mxdc.png" width="80%"></kbd></p>

<br>

<a id="node-1x41383"></a>

- **costs.append(epoch_total_loss)
            train_acc.append(train_accuracy.result())
            test_acc.append(test_accuracy.result())**

> [!NOTE]
> Sau mỗi lần train-update params (mỗi
> iteration). cứ 100 lần thì ghi lại cót,
> accuracy để tí nữa plot ra

<br>

<a id="node-qxg1r9h"></a>

#### 4 - Bibliography

<br>

<a id="node-uv56f0w"></a>

### References

<br>

<a id="node-ov0vyfp"></a>

<p align="center"><kbd><img src="assets/iwj8soh9g1j.png" width="80%"></kbd></p>

<br>

