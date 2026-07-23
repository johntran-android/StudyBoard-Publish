# Course 1 - Neural Networks & Deep Learning

📊 **Progress:** `73` Notes | `373` Screenshots

---
<a id="node-gijr46v"></a>

## Course 1 - Neural Networks & Deep Learning

<br>

<a id="node-ge1p0ny"></a>

## C1w1_introduction To N.n

<br>

<a id="node-r8gy7hv"></a>

### What's A Neural Network

<br>

<a id="node-nfr3s4q"></a>

#### The term "Deep Learning" refers to training Neural Networks, sometimes very
large Neural Networks.

A Neural Network is a function that can be used to predict outcomes based on
inputs, often implemented using neurons.

Neurons are individual units in a Neural Network that receive input and generate
output based on a set of weights and biases.

A simple example of a Neural Network is using linear regression to predict
housing prices based on house size.

In the example, the input (house size) goes through a single neuron that applies
a linear function and a ReLU function to generate the predicted price.

A larger Neural Network can be built by stacking multiple neurons together to
handle more complex inputs and outputs.

The process of training a Neural Network involves giving it input/output pairs and
adjusting the weights and biases of the neurons to minimize prediction error.

A more complex Neural Network can be used to predict housing prices based on
multiple features such as number of bedrooms, zip code, and walkability.

<br>

<a id="node-11zr2j1"></a>

<p align="center"><kbd><img src="assets/sjzxqppm2cd.png" width="80%"></kbd></p>

<br>

<a id="node-5q7fmzj"></a>

<p align="center"><kbd><img src="assets/hq7z4mqxo5a.png" width="80%"></kbd></p>

<br>

<a id="node-7j834v1"></a>

<p align="center"><kbd><img src="assets/01mchppwz18j.png" width="80%"></kbd></p>

<br>

<a id="node-5jr7rek"></a>

### Supervised Learning With N.n

<br>

<a id="node-b2nzlwh"></a>

#### 1 The majority of economic value created by neural networks has been through
supervised learning.

2 Various applications of neural networks include online advertising, computer
vision, speech recognition, machine translation, and autonomous driving.

3 Different types of neural networks are useful for different applications, such as
convolutional neural networks (CNNs) for image applications and recurrent
neural networks (RNNs) for sequence data.

4 Standard CNN and RNN architectures are used for image and
one-dimensional sequence data, respectively.

5 Machine learning can be applied to structured data and unstructured data.

6 Structured data refers to databases of data, while unstructured data includes
audio, images, and text.

<br>

<a id="node-tsbinbu"></a>

<p align="center"><kbd><img src="assets/c46bwg1t0qc.png" width="80%"></kbd></p>

<br>

<a id="node-tijoa04"></a>

<p align="center"><kbd><img src="assets/ymrf7rmaxm.png" width="80%"></kbd></p>

<br>

<a id="node-yz09iyq"></a>

<p align="center"><kbd><img src="assets/o83y83z57v.png" width="80%"></kbd></p>

<br>

<a id="node-jso4psm"></a>

### Why Is Deep Learning Taking Off?

<br>

<a id="node-ktx07sc"></a>

#### Sure, here is a more detailed answer with indexed points:  1 The video discusses the reasons behind the
rise of deep learning, despite the fact that the basic technical ideas behind deep learning have been
around for decades.

2 The main driver behind the rise of deep learning is the amount of data that is now available for various
tasks, such as spam classification, ad click prediction, and self-driving cars.

3 Traditional learning algorithms like support vector machines or logistic regression show a plateau in
performance after a certain point, as the amount of data increases.

4 However, with deep learning, the performance can continue to improve as more data is added, and the
neural network size increases.

5 This is because deep learning algorithms can take advantage of the huge amounts of data that are now
available, and larger neural networks can be trained to process that data.

6 In fact, today, the most reliable way to improve the performance of a neural network is to either train a
larger network or to add more data.

7 The amount of labeled data is plotted on the x-axis in the video, where labeled data refers to the training
examples with both input X and label Y.

8 In the regime of smaller training sets, the relative ordering of the algorithms is not well defined, and
performance depends more on the skill of the engineer at hand-engineering features.

9 However, in the regime of very large training sets, very large M, neural networks are seen to dominate
the other approaches.

10 The rise of deep learning has been made possible by the scale of data and the scale of computation,
such as the ability to train large neural networks on CPUs or GPUs.

11 Additionally, there have been significant algorithmic innovations in deep learning that have made neural
networks faster, such as the switch from sigmoid to ReLU activation functions.

12 Overall, deep learning has taken off due to the combination of scale, both in terms of data and
computation, and significant algorithmic innovations.

<br>

<a id="node-z2hbxmh"></a>

<p align="center"><kbd><img src="assets/b56abvkindr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:..
>
>
>
> Những algorithm 'cũ' như SVM khi có nhiều data nó sẽ tốt hơn nhưng
>  vẫn bị giới hạn, đại khái là sẽ không biết làm gì với quá nhiều data.
>
>
>
> Còn n.n phức tạp thì càng nhiều data nó càng tốt.
>
>
>
> Muốn n.n perform tốt thì phải 1-Nhiều data, 2-Phức tạp
>
>
>
> Do 'Big data' có được từ
> digitalization, sự phát triển của
> Camera, Mobile phone,...
>
>
>
> Nếu 'Small training set' thì performance sẽ tuỳ thuộc vào
> skill của con người như 'feature engineering' nên một model
> bằng SVM làm tốt có thể vượt trội n.n. Tuy nhiên nếu ở phân khúc
> 'Big data' thì Big n.n sẽ vượt trội những algorithm khác.

<br>

<a id="node-49b8tyg"></a>

<p align="center"><kbd><img src="assets/tkgtiy17uqd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:..
>
>
>
> Máy tính nhanh hơn giúp tăng tốc Quá trình Idea - Thử - Điều chỉnh
>
>
>
> Những algorithm mới cũng giúp quá trình 'Training' nhanh hơn
> ví dụ thay Sigmoid bằng Relu.

<br>

<a id="node-8g758al"></a>

<p align="center"><kbd><img src="assets/xeulnkil5d.png" width="80%"></kbd></p>

> [!NOTE]
> Data, sự phát triển của phần cứng sẽ giúp
> Deep learning còn phát triển nữa trong những năm tới.

<br>

<a id="node-ylddhq4"></a>

<p align="center"><kbd><img src="assets/qw6kc8uxp69.png" width="80%"></kbd></p>

<br>

<a id="node-uo7unsu"></a>

### About This Course

<br>

<a id="node-dwje6y8"></a>

#### The speaker gives an overview of the first course in a deep learning specialization,
which comprises five courses. The first course covers the most important
foundations of deep learning, including building and working with a deep neural
network. The course is four weeks long, with each week covering new material and
including 10 multiple-choice questions to check understanding. In week two, learners
will learn about the basics of neural network programming and practice implementing
the algorithms through a programming exercise. In week three, learners will code up
a single hidden layer neural network, and in week four, they will build a deep neural
network with many layers. The speaker encourages learners to take the
multiple-choice questions seriously and to use them to check their understanding of
the material.

<br>

<a id="node-kk66eqp"></a>

<p align="center"><kbd><img src="assets/4zs1spp8lxa.png" width="80%"></kbd></p>

<br>

<a id="node-gn2bbvq"></a>

<p align="center"><kbd><img src="assets/ecj3lak7cm5.png" width="80%"></kbd></p>

<br>

<a id="node-sexx9rc"></a>

### Quiz

<br>

<a id="node-ms05ldq"></a>

<p align="center"><kbd><img src="assets/g24j4zr4n3m.png" width="80%"></kbd></p>

<br>

<a id="node-vvkdk1q"></a>

<p align="center"><kbd><img src="assets/m02fpfqdixr.png" width="80%"></kbd></p>

<br>

<a id="node-3qz85oh"></a>

<p align="center"><kbd><img src="assets/8mt0t69t8dj.png" width="80%"></kbd></p>

<br>

<a id="node-shtijys"></a>

<p align="center"><kbd><img src="assets/wqdt5x2te5h.png" width="80%"></kbd></p>

<br>

<a id="node-weyl45s"></a>

<p align="center"><kbd><img src="assets/alscaidy8f.png" width="80%"></kbd></p>

<br>

<a id="node-qy7n322"></a>

<p align="center"><kbd><img src="assets/5yckdugm6qm.png" width="80%"></kbd></p>

<br>

<a id="node-o2bchf3"></a>

<p align="center"><kbd><img src="assets/335dj6cyujp.png" width="80%"></kbd></p>

<br>

<a id="node-ce4o4ry"></a>

<p align="center"><kbd><img src="assets/nbc6wkckbq.png" width="80%"></kbd></p>

<br>

<a id="node-lf397pe"></a>

<p align="center"><kbd><img src="assets/4m5zovehnmv.png" width="80%"></kbd></p>

<br>

<a id="node-fplkt05"></a>

<p align="center"><kbd><img src="assets/3rfgf3pjik5.png" width="80%"></kbd></p>

<br>

<a id="node-9nsru1y"></a>

<p align="center"><kbd><img src="assets/ok6ftatcpr8.png" width="80%"></kbd></p>

<br>

<a id="node-18kpdf9"></a>

<p align="center"><kbd><img src="assets/y5jqv0fars9.png" width="80%"></kbd></p>

<br>

<a id="node-13j5c0a"></a>

## C1w2_n.n Basic

<br>

<a id="node-3pvsypb"></a>

### Logistic Regression As A Neural Network

<br>

<a id="node-tb70oe2"></a>

#### Binary Classification

<br>

<a id="node-rti9o47"></a>

##### 1 The basics of neural network programming include techniques that are
important to process the entire training set.

2 The computation of a neural network is organized in forward propagation and
backward propagation.

3 Logistic regression is an algorithm for binary classification that is going to be
used to convey the ideas.

4 To turn pixel intensity values into a feature vector, they are unrolled to get a
long feature vector that lists all the red, green and blue pixel intensity values of
the image.

5 Binary classification aims to learn a classifier that can input an image
represented by a feature vector x and predict whether the corresponding label y
is 1 or 0.

6 Notations used in the course include lowercase m to denote the number of
training samples, M_train, to emphasize that this is the number of training
examples, and m_subscript_test to denote the number of test examples.

7 A matrix X is defined by taking the training set inputs x1, x2, and so on, and
stacking them in columns.

<br>

<a id="node-1ws7b4v"></a>

<p align="center"><kbd><img src="assets/hndv272fmem.png" width="80%"></kbd></p>

<br>

<a id="node-ywcayvy"></a>

<p align="center"><kbd><img src="assets/lzawl0f3s4a.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:..
>
>
>
> Thường thì define X dạng mxn, nhưng đối với n.n thì define nm 
> sẽ dễ làm hơn. Y cũng vậy.

<br>

<a id="node-56j5ya9"></a>

#### Logistic Regression

<br>

<a id="node-76k0yjt"></a>

##### 1 Logistic regression is a learning algorithm used for binary classification problems
where the output labels Y are either zero or one.

2 Given an input feature vector X, the goal of logistic regression is to output a
prediction Y hat, which is the probability that Y is equal to one given X.

3 The parameters of logistic regression are W, which is an X-dimensional vector,
and b, which is a real number.

4 The initial idea of using Y hat as a linear function of the input X, Y hat = w
transpose X + b, is not effective for binary classification because it does not
guarantee that Y hat will be between zero and one.

5 Instead, logistic regression uses the sigmoid function to ensure that Y hat is
between zero and one.

6 The sigmoid function maps any real number Z to a value between zero and one,
with values close to one for large positive Z, and values close to zero for large
negative Z.

7 The formula for the sigmoid function is sigmoid of Z = 1 / (1 + e^(-Z)).

8 The parameters W and B of logistic regression are learned by defining a cost
function, which will be explained in the next video.

9 There is an alternative notation for logistic regression that uses an extra feature
called X0, but in this course, W and B are kept separate.

<br>

<a id="node-pfq9cgy"></a>

<p align="center"><kbd><img src="assets/vihwdjoa5e.png" width="80%"></kbd></p>

<br>

<a id="node-i5qqid6"></a>

<p align="center"><kbd><img src="assets/n3sch20mpsk.png" width="80%"></kbd></p>

<br>

<a id="node-t69xy3l"></a>

#### Logistic Regression Cost Function

<br>

<a id="node-4wuf9yh"></a>

##### 1 Logistic regression model to train parameters W and B for given training
examples.

2 Definition of the cost function to measure how well the algorithm is
performing on the training set.

3 Convention of superscript parentheses I to index different training
examples.

4 Use of a different loss function in logistic regression, which is negative y
log y hat plus 1 minus y log 1 minus y hat.

5 Justification of the loss function, where it tries to make y hat large if y is
equal to one and small if y is equal to zero.

<br>

<a id="node-fuoz6mi"></a>

<p align="center"><kbd><img src="assets/7t2ntdhymhs.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:..
>
>
>
> Ở đây ổng dùng kí tự sigma - σ để biểu thị hàm Sigmoid.
> Mấy khoá khác ổng dùng chữ g.
>
>
>
> Define Loss function cho Logistic Regression (y^-y)^2/2 cũng được
> nhưng nó lại khiến G.D không work, do lúc này hàm J sẽ non-convex
> Do đó người ta define Loss function kiểu khác:
> ylog(y^) + (1 - y)log(1-y^)
>
>
>
> Và Cost function là trung bình cộng (mean value) tất cả Loss 
> của toàn bộ dataset m

<br>

<a id="node-js0b9o0"></a>

<p align="center"><kbd><img src="assets/gdvc9db3ku4.png" width="80%"></kbd></p>

<br>

<a id="node-5nfpj0n"></a>

#### Gradient Descent

<br>

<a id="node-5exj9hr"></a>

##### 1 Recap of logistic regression and its loss and cost functions.

2 Discussion of the convexity of the cost function and why it's
important for logistic regression.

3 Explanation of gradient descent as an optimization algorithm to find
the best parameters for the cost function.

4 Description of how gradient descent updates the values of the
parameters to approach the minimum of the cost function.

5 Explanation of the role of the learning rate in controlling the size of
steps in the gradient descent algorithm.

<br>

<a id="node-g1h1qtg"></a>

<p align="center"><kbd><img src="assets/4cc9bsaknqw.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:..
>
>
>
> "And /**for logistic regression**/, almost any initialization  method works.
> Usually you Initialize the values of 0, Random initialization also works, but
> people don't usually do that for  logistic regression./**But because this
> function is convex, no matter where you initialize, you should get to the
> same point or roughly the same point."**/
>
>
>
> Vì hàm J convex nên dù có Initialize (W, b) thế nào - Random hay cho
> bằng 0 thì nó sẽ đều converge về global optima

<br>

<a id="node-zmfvloh"></a>

<p align="center"><kbd><img src="assets/gfu5lygtc8q.png" width="80%"></kbd></p>

<br>

<a id="node-ci1q51y"></a>

<p align="center"><kbd><img src="assets/o9ci6xn551e.png" width="80%"></kbd></p>

> [!NOTE]
> Một ghi chú nhỏ không quan trọng lắm:
> Trong calculus người ta dùng kí tự **'∂'**- gọi là
> kí tự '/**Partial derivative**/' khi hàm J depend on 2 params
> trở lên còn nếu chỉ 1 param thì dùng chữ **'d'**
>
>
>
> Ổng cho là làm vậy chỉ tổ phức tạp nên ở đây dùng chữ 'd' hết.
>
>
>
> Trong code sẽ là **dw, db (hay dj_dw, dj_db)**

<br>

<a id="node-j213ou5"></a>

<p align="center"><kbd><img src="assets/qhm5yhwgx5s.png" width="80%"></kbd></p>

<br>

<a id="node-ljct7v9"></a>

#### Derivatives

<br>

<a id="node-k987rmv"></a>

##### 1 The video aims to help people gain an intuitive understanding of calculus and
derivatives.

2 Even if someone does not have a deep understanding of calculus, they can still
apply deep learning.

3 Forward and backward functions will encapsulate everything one needs to know
about calculus for deep learning.

4 Calculus is important for deep learning, but intuitive understanding is enough to
build and apply algorithms.

5 The video will explore the details of derivatives, but for experts in calculus, this
video may be skipped.

6 The video explains the concept of derivatives by plotting a straight line and
exploring how the slope changes.

7 The slope of a line represents the derivative, which is the rate of change of the
function.

8 The slope or derivative is defined as the height divided by the width of a small
triangle.

9 When the slope is equal to three, it means that if you nudge a variable a to the right,
f(a) goes up three times as much as you nudged the value of a.

<br>

<a id="node-smt38t1"></a>

<p align="center"><kbd><img src="assets/2ge5ute8h6k.png" width="80%"></kbd></p>

> [!NOTE]
> Official definition thì 'small value' không phải là 0.01, hay 0.0001
> mà là một khoảng vô cùng nhỏ. Nhưng đại khái definition của
> Derivative là chỉ vậy:   
>
>
>
> **"Khi kéo a tăng lên một khoảng hàm f(a)
> /cũng tăng lên một khoảng gấp mấy lần/ thì đó chính là
> derivative của hàm f tại a"**  
>
>
>
> Và cũng là slop - Độ dốc của hàm f(a) tại a.
>
>
>
> Và đối với hàm linear thì thấy rõ là độ dốc ở đâu cũng bằng nhau.

<br>

<a id="node-j92nldm"></a>

<p align="center"><kbd><img src="assets/5m1eryhvjmn.png" width="80%"></kbd></p>

<br>

<a id="node-bnc34t2"></a>

#### More Derivative Examples

<br>

<a id="node-cv6bjx1"></a>

##### 1 The video demonstrates a slightly more complex example where the slope of the
function varies at different points in the function.

2 The function used as an example is f(a) = a².

3 The video shows that the slope of the function at a given point can be determined by
nudging a slightly to the right and observing the change in f(a).

4 The video explains that the ratio of the height of the triangle over the width of the
triangle is different at different points on the curve, which is why the derivative is
different at different points.

5 The video shows that if you pull up a calculus textbook, you'll find that the slope of
the function a² is equal to 2a.

6 The video demonstrates that the derivative of f(a) = a² is equal to 4 when a = 2 and
10 when a = 5.

7 The video explains that the derivative is defined using infinitesimally small nudges to
a, which is why the amount that f(a) goes up isn't exactly given by the formula but is
only approximately given by the derivative.

<br>

<a id="node-xcagev5"></a>

<p align="center"><kbd><img src="assets/83prpzf0tp4.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu trong sách Calculus ta thấy công thức tính 
> d_f(a)/d_a = **2a** với f = a^2 thì có nghĩa là : 
>
>
>
> Nếu kéo a lên một khoảng tiny ví dụ 0,001 thì 
> hàm f = a^2 sẽ tăng lên 1 khoảng /**gấp 2a lần**/ = 2a*0.001

<br>

<a id="node-4a3pj5v"></a>

<p align="center"><kbd><img src="assets/guf47muiv2d.png" width="80%"></kbd></p>

<br>

<a id="node-utgwfeh"></a>

<p align="center"><kbd><img src="assets/c098bl1msg.png" width="80%"></kbd></p>

> [!NOTE]
> Wrap up: 
> /**Derivative của một function (tại điểm nào đó) đơn giản chỉ là 
> độ dốc của function đó (tại điểm nào đó)**
> /
> 1. The derivative of the function just means **the slope** of a function 
> and the slope of a function can be different at different points on the 
> function
>
>
>
> 2. Muốn xem công thức của tính derivative cho các hàm khác nhau
> thì có thể mở sách Calculus ra xem.

<br>

<a id="node-44a9dvi"></a>

#### Computation Graph

<br>

<a id="node-21u696a"></a>

##### 1 Introduction: Explanation of forward pass and backward pass in neural networks
using computation graph.

2 Example problem: Computing a function J of three variables a, b, and c, which is J =
3(a + bc).

3 Steps to compute J:

4 a. Compute u = bc.  5 b. Compute V = a * u.  6 c. Compute J = 3V.

7 Computation graph: Visual representation of the three steps with a, b, and c as
inputs, and u, V, and J as the intermediate and final outputs, respectively.

8 Example calculation: Values of a, b, and c are given as 5, 3, and 2, respectively. The
values of u, V, and J are computed as 6, 30, and 33, respectively, using the
computation graph.

9 Importance of computation graph: Useful for optimizing a special output variable,
such as J, in neural networks.

10 Left-to-right computation: The computation graph enables a left-to-right pass for
computing the value of J.

11 Right-to-left computation: In order to compute derivatives, a right-to-left pass is
needed, which is explained in the next video.

<br>

<a id="node-3szwcxk"></a>

<p align="center"><kbd><img src="assets/yl1siztfd6.png" width="80%"></kbd></p>

> [!NOTE]
> Nền tảng đằng sau tên gọi khái niệm của 'Forward propagation' đại khái là
> để tính value (ví dụ của cost function J) thì tính từ trái qua phải. Còn tính
> derivative thì ngược lại (Back propagation)

<br>

<a id="node-ojytr02"></a>

#### Derivatives With A Computation Graph

<br>

<a id="node-1quortk"></a>

##### 1 Introduction: The video discusses how to use a computation graph to figure out derivative
calculations for a function J by taking a cleaned-up version of the computation graph used in the
previous video.

2 Derivative of J with respect to v: The video demonstrates how to compute the derivative of J
with respect to v, which is equal to 3, by increasing the value of v by 0.001, using the analogy of
the previous video where f(a) = 3a and df/da = 3.

3 Derivative of J with respect to a: The video illustrates how to calculate dJ/da, which is also
equal to 3, by changing the value of a by 0.001 and breaking it down to the chain rule, where
dv/da = 1 and dJ/dv = 3, which when multiplied give dJ/da = 3.

4 Backward calculation: The video shows how computing dJ/dv can help in calculating dJ/da and
how it's a backward calculation to find the derivatives of the variables that come before J.

5 Notational Convention: The video introduces a new notational convention, which is to call the
final output variable, J in this case, as "dvar" while computing the derivative of the final output
variable with respect to intermediate variables.

<br>

<a id="node-8zrw24y"></a>

<p align="center"><kbd><img src="assets/7hrwuekd5m4.png" width="80%"></kbd></p>

> [!NOTE]
> 1.Đại khái là để tính derivative thì tính theo chiều ngược lại, ví dụ
> để tính dJ_da thì phải tính dJ_dv, dv_da và:
>
>
>
> dJ_da = dJ_dv . dv_da
>
>
>
> và nó gọi là 'Chain rule' trong calculus 
>
>
>
> 2.Đại khái là trong code sẽ viết gọn dFinalOutput/dVar thành dVar
> Ví dụ:
>  'dJ_da' thành 'da', 'dJ_dv' thành 'dv' thôi.

<br>

<a id="node-p6e58tf"></a>

<p align="center"><kbd><img src="assets/2r8blqkmkcy.png" width="80%"></kbd></p>

> [!NOTE]
> So that was the computation graph and how does a forward or
> left to right calculation to compute the **cost function** such as J
> that you might want to optimize. And a backwards or a right to
> left calculation to compute **derivatives**
>
> So the key takeaway from this video, from this example, is that 
> when computing derivatives and computing all of these 
> derivatives, the most efficient way to do so is /**through a right 
> to left computation**/ following the direction of the red arrows

<br>

<a id="node-31aokep"></a>

<p align="center"><kbd><img src="assets/1x5vm7lv12q.png" width="80%"></kbd></p>

<br>

<a id="node-5ar00g0"></a>

#### Logistic Regression Gradient Descent

<br>

<a id="node-338yxuy"></a>

##### Main ideas:  1 Introduction to computing derivatives for implementing
gradient descent for logistic regression.

2 Explanation of the key equations necessary to implement gradient
descent for logistic regression using computation graphs.

3 Forward propagation steps of computing loss on a single training
example.

4 Backward propagation steps to compute the derivatives of the loss
with respect to each variable.

5 Explanation of the derivative of the loss with respect to A and how it is
computed.

6 Deriving the derivative of the loss with respect to Z using the chain
rule.

7 Computation of how much W and B need to be changed.

8 Explanation of how to update W1, W2, and B to perform one step of
gradient descent with respect to a single example.

<br>

<a id="node-00kwpp3"></a>

<p align="center"><kbd><img src="assets/b3502q6hh17.png" width="80%"></kbd></p>

<br>

<a id="node-ag9w8up"></a>

<p align="center"><kbd><img src="assets/0brpe2u4qsw6.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái đây chính là đi ngược lại (Back Prop) để  ..
>
>
>
> ..tính ra '/**derivative of cost function J with respect to w, b** / 
> Hay viết gọn là dj_dw (or dw) và dj_db (or db)  
> Phục vụ cho việc /**dùng Gradient Descent update w, b sao 
> cho minimize J**/.
>
> Có thể xem lại sách Calculus để tự tính lại derivative (đạo hàm)
> của: 
> - hàm Loss function L = -( ylog(a) + (1-y)log(1-a) ) -> dL_da
> - hàm sigmoid a = sigmoid(z) -> da_dz
> - hàm z = w(transpose).x + b -> dz_dw, dz_db

<br>

<a id="node-gh91sap"></a>

<p align="center"><kbd><img src="assets/trs2ts79iqg.png" width="80%"></kbd></p>

> [!NOTE]
> D/**ùng Gradient Descent update w,
> b sao cho minimize J**/.

<br>

<a id="node-35fe1hi"></a>

<p align="center"><kbd><img src="assets/vrs83nz5k1.png" width="80%"></kbd></p>

<br>

<a id="node-6kkhnlj"></a>

#### Gradient Descent On M Examples

<br>

<a id="node-dnwlv2n"></a>

##### 1 Reminder of the definition of the cost function J.

2 Explanation of how to compute derivatives for the cost function J with
respect to each parameter w and b for m training examples.

3 Derivatives with respect to each parameter are computed as the
average of derivatives with respect to each parameter for the individual
loss terms.

4 An algorithm is presented that computes the derivatives of the cost
function J with respect to each parameter w and b.

5 Details of the algorithm are presented, including initialization, for loop
over training set, calculations for the accumulator values, division by m to
compute the averages, and updating of parameter values.

6 Two weaknesses with the algorithm are noted: two for loops are
needed to implement logistic regression and it assumes that the number
of features is known.

<br>

<a id="node-wsam2yy"></a>

<p align="center"><kbd><img src="assets/uma7fq0foj.png" width="80%"></kbd></p>

> [!NOTE]
> Derivative of J w.r.t w, b trên toàn bộ m dataset X, y - dJ_dw, dJ_db
> Tính bằng cách lấy trung bình của tất cả
> Derivative of J w.r.t w, b trên từng dataset x(i), y(i) - dJ_dw(i), dJ_db(i)

<br>

<a id="node-24m6ghw"></a>

<p align="center"><kbd><img src="assets/0gsoy8gu7ve9.png" width="80%"></kbd></p>

> [!NOTE]
> Không khó hiểu gì nhưng nhắc cho để ý:
> 1. J, dw, db là 'accumulator' 
> -> Update bằng operator += trong loop nên không có superscrip (i) 
> còn dz là đv từng dataset nên có superscrip (i) - dz(i)
>
>
>
> 2. Toàn bộ ở đây chỉ là **1 iteration - để update dw, db một lần.**
>
> Dễ dàng thấy có 2 nhược điểm:
>
>
>
> Phải dùng 2 for loop, 1 cái loop over m training set, 1 cái
> loop tất cả  các feature để tính dw: Ở đây chỉ có dw1, dưa
> nhưng thực tế có n feature với n có khi cả ngàn.
>
>
>
> Solution : **Vectorization**

<br>

<a id="node-7o4ytlf"></a>

<p align="center"><kbd><img src="assets/0diissw3ut6i.png" width="80%"></kbd></p>

<br>

<a id="node-bky0auq"></a>

#### DERIVATION OF dL/dz

<br>

<a id="node-wckmq67"></a>

##### ...

<br>

<a id="node-ajfmgsq"></a>

<p align="center"><kbd><img src="assets/i1ibmldd6x.png" width="80%"></kbd></p>

<br>

<a id="node-2xlvr1i"></a>

<p align="center"><kbd><img src="assets/rm6qdpwr9hi.png" width="80%"></kbd></p>

<br>

<a id="node-z31qxxp"></a>

<p align="center"><kbd><img src="assets/ttg5sdlou4n.png" width="80%"></kbd></p>

<br>

<a id="node-srmkadn"></a>

<p align="center"><kbd><img src="assets/g3hozdmque5.png" width="80%"></kbd></p>

<br>

<a id="node-fidnpit"></a>

<p align="center"><kbd><img src="assets/oi9r7f9u2cj.png" width="80%"></kbd></p>

<br>

<a id="node-3n2kcy8"></a>

### Python And Vectorization

<br>

<a id="node-6l159xe"></a>

#### Vectorization

<br>

<a id="node-qrz773o"></a>

##### 1 The course teaches strategies for structuring a machine learning
project to improve efficiency and quickly get systems working.

2 The example given is of improving a cat classification system with
90% accuracy.

3 There are many ideas to try to improve a deep learning system, but
choosing the wrong approach can waste time.

4 The course teaches strategies for analyzing a machine learning
problem to identify the most promising ideas to pursue.

5 The instructor will share lessons learned from building and
shipping deep learning products.

6 The strategies taught in the course are unique and not commonly
taught in university deep learning courses.

7 Machine learning strategy has changed with the emergence of
deep learning algorithms.

8 The course aims to make learners more effective at getting deep
learning systems to work.

<br>

<a id="node-k4a0tcy"></a>

<p align="center"><kbd><img src="assets/i488tnawqim.png" width="80%"></kbd></p>

<br>

<a id="node-6jrwewt"></a>

<p align="center"><kbd><img src="assets/l4wu0ldqj1.png" width="80%"></kbd></p>

> [!NOTE]
> 2499719.1349626444
> Vectorization: 8.999824523925781ms
> 2499719.1349626444
> Non-Vectorization: 7566.00022315979ms
> Vectorization is /**840**/.6830825474198 times faster than non-vectorization
> If some trainning task take **1 hour** to finish with vectorization, 
> it will need **35 days** to finish

<br>

<a id="node-rs7892l"></a>

<p align="center"><kbd><img src="assets/kw3k8zdqvw.png" width="80%"></kbd></p>

> [!NOTE]
> And it turns out that both GPU and CPU have parallelization instructions. 
> They're sometimes called SIMD instructions. 
> This stands for a single instruction multiple data.
>
>
>
> But what this basically means is that, if you use built-in functions 
> such as this np. function or other functions that don't require 
> you explicitly implementing a for loop. 
> It enables Python numPy to take much better advantage of 
> parallelism to do your computations much faster.
>
>
>
> And this is true both computations on CPUs and computations on GPUs. 
> It's just that GPUs are remarkably good at these SIMD calculations but 
> CPU is actually also not too bad at that. 
> Maybe just not as good as GPUs.
>
> Rule of thumb is to avoid for - loop as much as possible

<br>

<a id="node-p01cgzx"></a>

<p align="center"><kbd><img src="assets/xkqlmuh812.png" width="80%"></kbd></p>

<br>

<a id="node-byz5y1i"></a>

#### Vectorization More Example

<br>

<a id="node-y03evq1"></a>

##### 1 Rule of thumb: avoid explicit for-loops whenever possible to speed up
code.

2 Example 1: Vector multiplication using matrix A and vector v -
non-vectorized implementation using two for-loops, vectorized
implementation using np dot (A,v).

3 Example 2: Exponential operation on every element of vector v -
non-vectorized implementation using a for-loop, vectorized
implementation using np.exp(v).

4 NumPy built-in functions for element-wise operations.

5 Applying vectorization to logistic regression gradient descent
implementation to eliminate one of the two for-loops.

6 Eliminating the need for a for-loop over training examples in logistic
regression with further vectorization.

7 Vectorization can significantly speed up code.

<br>

<a id="node-qlfdx72"></a>

<p align="center"><kbd><img src="assets/ohvdbmrlrn.png" width="80%"></kbd></p>

<br>

<a id="node-v2cbxoe"></a>

<p align="center"><kbd><img src="assets/efnb4an5qla.png" width="80%"></kbd></p>

<br>

<a id="node-98qwfnt"></a>

<p align="center"><kbd><img src="assets/o6kpvhk34z.png" width="80%"></kbd></p>

<br>

<a id="node-scf14si"></a>

#### Vectorizing Logstic Regression

<br>

<a id="node-sg6f0kd"></a>

##### Main ideas:  1 The video explains how to vectorize the implementation of
logistic regression and process the entire training set without using explicit for
loops.

2 The four propagation steps of logistic regression are explained with an
example of making a prediction on M training examples.

3 The matrix X is defined as the training inputs, stacked together in different
columns, and a matrix Z is defined to compute all the values of Z1, Z2,...,ZM in
one step.

4 The values A1, A2,...,AM are computed using a vectorized sigmoid function
that takes the matrix Z as input.

5 Stacking lowercase A results in a new variable, capital A.

6 The video concludes that instead of looping over M training examples to
compute Z and A, you can use the one-line code to compute all Z and A at the
same time.

<br>

<a id="node-oda6v6b"></a>

<p align="center"><kbd><img src="assets/m7xjglsiqem.png" width="80%"></kbd></p>

<br>

<a id="node-n82lime"></a>

<p align="center"><kbd><img src="assets/ier7pi78wsk.png" width="80%"></kbd></p>

> [!NOTE]
> X = n x m (ở khoá trước đây nó define dạng m x n)
>
>
>
> W = n x 1 -> W(T) = 1 x n 
>
>
>
> Z = W(T) . X = 1 x n . n x m = 1 x m
>
>
>
> W(T) . X + b thì b sẽ dc broadcast thành [b b ...b] = 1x m
>
>
>
> =>  W(T) . X + b = 1 x m + 1 x m = 1 x m
>
>
>
> Hàm sigmoid nhận vector được =>
> a(Z) = 1x m

<br>

<a id="node-jt08xw2"></a>

<p align="center"><kbd><img src="assets/rosjsu25hnq.png" width="80%"></kbd></p>

<br>

<a id="node-ugfcjfc"></a>

#### Vectorizng Logistic Regression' S Gradient Computation

<br>

<a id="node-yeopw43"></a>

##### Main ideas:  1 The previous video demonstrated how vectorization could be used to compute the
predictions for an entire training set simultaneously.

2 This video shows how to use vectorization for gradient computation for all M training samples.

3 The new variable dZ is defined as dz1, dz2, ..., dzm, which is a 1 by m matrix or an m
dimensional row vector.

4 dz can be computed as A - Y where A and Y are defined as a1 through am and y1 through ym,
respectively.

5 Vectorization can be used to implement the derivative calculations efficiently.

6 The vectorized implementation of db is one over m times np.sum of dz, while the vectorized
implementation of dw is one over m times the matrix X times dz transpose.

7 The previous implementation of logistic regression was highly inefficient and required loops
over dw1, dw2, etc.

8 The new implementation uses vectorization to replace the loops, making it more efficient.

9 The updated code involves computing capital Z as w transpose X + B, then calculating a as
sigmoid of capital Z, dz as A - Y, dw as 1/m x dz transpose, and db as 1/m times np.sum of dz.

10 The vectorized implementation allows for the computation of updates to the parameters
without a for loop over the training set.

<br>

<a id="node-smooii4"></a>

<p align="center"><kbd><img src="assets/xw08byn9qd.png" width="80%"></kbd></p>

> [!NOTE]
> QUAN TRỌNG

<br>

<a id="node-fhwyir7"></a>

<p align="center"><kbd><img src="assets/4fqwuhcbkxd.png" width="80%"></kbd></p>

> [!NOTE]
> Now, I know I said that we should get rid of explicit for loops whenever
> you can but if you want to implement multiple iterations as a gradient
>  descent then /**you still need a for loop over the number of
>  iterations**/. So, if you want to have a thousand iterations of gradient
> descent, you might still need a for loop over the iteration
> number. /**There is an outermost for loop like that then I don't think there
> is any way to get rid of that for loop**/
>
>
>
>
> Còn cái for loop iteration để update w, b thì không thể có cách nào
> bỏ được vì cơ chế của Gradient Descent phải vậy

<br>

<a id="node-ajwlibu"></a>

<p align="center"><kbd><img src="assets/01e2w2wfkojs.png" width="80%"></kbd></p>

<br>

<a id="node-v2etg1w"></a>

#### Broadcasting In Python

<br>

<a id="node-nb9yg4w"></a>

##### 1 Broadcasting is a technique to make Python code run faster.

2 Broadcasting allows performing operations between arrays with different shapes.

3 In the video, broadcasting is explained using an example of calculating the
percentage of calories from carbs, proteins, and fats in 100 grams of four different
foods.

4 Broadcasting can be used to sum down columns of a matrix and divide each
column by their corresponding sum without using an explicit for-loop.

5 The video demonstrates how to sum vertically using axis 0, which sums down the
columns, and how to reshape a matrix.

6 The reshape command is a constant time operation and can be used to ensure
that matrices have the correct size.

7 The video explains how broadcasting works, and provides examples of adding a 4
by 1 vector to a number and multiplying a 4 by 3 matrix by a 1 by 3 matrix.

<br>

<a id="node-2iy5xlf"></a>

<p align="center"><kbd><img src="assets/nky91mjap9.png" width="80%"></kbd></p>

<br>

<a id="node-zwh748p"></a>

<p align="center"><kbd><img src="assets/r0tpihm11pg.png" width="80%"></kbd></p>

> [!NOTE]
> A.sum(axis = 0) => Sum vertically

<br>

<a id="node-zb5ynm1"></a>

<p align="center"><kbd><img src="assets/wxxt93c416k.png" width="80%"></kbd></p>

<br>

<a id="node-ovktwqt"></a>

<p align="center"><kbd><img src="assets/01uo61bd7rob.png" width="80%"></kbd></p>

> [!NOTE]
> 'Cal' vốn dĩ đã là 1x4 rồi nhưng ổng
> nói thêm lệnh reshape cho  chắc ăn
> không sao cả.

<br>

<a id="node-jsp3426"></a>

<p align="center"><kbd><img src="assets/ob1wh8mf6b.png" width="80%"></kbd></p>

<br>

<a id="node-oo1c2di"></a>

<p align="center"><kbd><img src="assets/umtl8eejs1.png" width="80%"></kbd></p>

> [!NOTE]
> Trong Octave/Matlab bsxfun làm việc tương tự

<br>

<a id="node-x17jo3z"></a>

#### A Note On Python/ Numpy Vectors

<br>

<a id="node-9prb9ao"></a>

##### 1 Python numpy's broadcasting operations and flexibility are both strengths
and weaknesses of the programming language.

2 Broadcasting and flexibility can cause subtle and strange bugs in the
code if not used correctly.

3 The rank 1 array in Python numpy is a funny data structure that behaves
inconsistently as either a row vector or a column vector, making it
nonintuitive.

4 It is recommended to use (n, 1) or (1, n) arrays to ensure consistent
behavior.

5 Assertion statements can be used to check the dimensions of arrays and
ensure consistent behavior.

6 Reshaping rank 1 arrays can also ensure consistent behavior.

<br>

<a id="node-g3xbl01"></a>

<p align="center"><kbd><img src="assets/yzsvdvkgl9.png" width="80%"></kbd></p>

> [!NOTE]
> Rank 1 array - 1-Dimensional array behave rất kì cục (ex.
> a.T cũng y nguyên), ko phải row vector cũng ko phải
> column vector.

<br>

<a id="node-9q83n9b"></a>

<p align="center"><kbd><img src="assets/9080qugsazt.png" width="80%"></kbd></p>

> [!NOTE]
> Nên luôn luôn defin Rank 2 array

<br>

<a id="node-eea82qv"></a>

<p align="center"><kbd><img src="assets/kiiclxy65q8.png" width="80%"></kbd></p>

> [!NOTE]
> 1. Đừng dùng Rank 1 array, dùng Rank 2
>
>
>
> 2.Đừng ngại reshape để chắc chắn mình đang có shape 
> mong muốn
>
>
>
> 3.Dùng Assert để báo lỗi khi shape ko đúng

<br>

<a id="node-ti5pvwf"></a>

<p align="center"><kbd><img src="assets/je9ndnvcrh.png" width="80%"></kbd></p>

<br>

<a id="node-vpvqzdq"></a>

#### Quick Tour Notebook

<br>

<a id="node-l36zsmr"></a>

##### ...

<br>

<a id="node-ib9e3v4"></a>

<p align="center"><kbd><img src="assets/c079pqwpbzq.png" width="80%"></kbd></p>

> [!NOTE]
> Có issue gì thì Restart Kernel

<br>

<a id="node-mk2f4hl"></a>

#### Logistic Regression Cost Function

<br>

<a id="node-dtu8ncd"></a>

##### 1 In this optional video, the speaker justifies the use of the cost function for logistic
regression that was introduced in an earlier video.

2 In logistic regression, the prediction y hat is the sigmoid of w transpose x + b, where
sigmoid is a familiar function. The goal is to interpret y hat as the probability that y=1
given x.

3 The chance that y=1 given x is y hat, and the chance that y=0 given x is 1- y hat.

4 These two equations can be summarized into a single equation: (y hat ^ y )(1- y hat)^(1-y) for
y=0 or 1. This equation is a correct definition for p(y|x).

5 Because the log function is a strictly monotonically increasing function, maximizing
log p(y|x) gives a similar result as optimizing p(y|x).

6 The loss function for a single example is -[y log y hat + (1-y) log (1- y hat)].

7 The cost function for the entire training set is the negative sum of the loss function
over all m examples. This is derived using the principle of maximum likelihood
estimation, which means choosing the parameters that maximize the probability of the
observations in the training set.

<br>

<a id="node-7oxhthy"></a>

<p align="center"><kbd><img src="assets/j97k4pwjmzj.png" width="80%"></kbd></p>

> [!NOTE]
> Notation: IID = I**dentically Independently Distributed**
>
>
>
> IID là viết tắt của "Independent and Identically Distributed". Nó có 
> nghĩa là một tập hợp các biến ngẫu nhiên độc lập với nhau và có 
> phân bố (tức các xác suất xuất hiện của các giá trị của biến) giống 
> nhau. Điều này có nghĩa là mỗi biến ngẫu nhiên trong tập hợp này 
> không bị ảnh hưởng bởi biến khác và tất cả chúng có cùng một 
> phân bố xác suất.
>
> "Now, finally, because the log function is a strictly monotonically 
> increasing function, your maximizing log p(y|x) should give you 
> a similar result as optimizing p(y|x)."
>
>
>
> ChatGPT: The statement is referring to the use of logarithmic functions in 
> machine learning and how they can affect optimization. A log function
>  is a mathematical function that takes a positive real number as input 
> and returns its logarithm to the base of a specified number. In this 
> context, \_/**"strictly monotonically increasing"\_ means that as the input to
>  the log function increases, its output also increases and does so in a 
> consistent, one-to-one relationship.**/
>
>
>
> Therefore, maximizing the logarithm of the conditional probability 
> p(y|x) (the probability of observing a target variable y given a feature 
> x) should give similar results as optimizing p(y|x) directly. /**This is 
> because the log function preserves the ordering of the original values
>  and allows for optimization in log-space, which can often be 
> computationally easier and faster.**/

<br>

<a id="node-64k2oy8"></a>

<p align="center"><kbd><img src="assets/zb3e8im402.png" width="80%"></kbd></p>

> [!NOTE]
> **Maximum likelihood estimation** is like when you are trying to guess
>  what the best answer is to a question.
> Imagine you have a big jar of candy, and you have to guess how many
>  candies are inside.
> You might start by making a guess, like 50. Then, your friend would tell 
> you if your guess is too high or too low.
> You would keep adjusting your guess until you get as close as 
> possible to the correct answer.
> In the same way, maximum likelihood estimation is a way for a 
> computer to make its best guess about something, by using all the 
> information it has, and constantly adjusting its guess until it gets as 
> close as possible to the correct answer.

<br>

<a id="node-07f5qli"></a>

### Quiz: Neural Network Basic

<br>

<a id="node-crx1p5u"></a>

<p align="center"><kbd><img src="assets/erq1bqh13bo.png" width="80%"></kbd></p>

<br>

<a id="node-nh0xkwr"></a>

<p align="center"><kbd><img src="assets/c7dhlqek3d8.png" width="80%"></kbd></p>

<br>

<a id="node-o5gkvgx"></a>

<p align="center"><kbd><img src="assets/w9d2loviz7o.png" width="80%"></kbd></p>

<br>

<a id="node-xi96q8k"></a>

<p align="center"><kbd><img src="assets/1e5kivqhmqkh.png" width="80%"></kbd></p>

<br>

<a id="node-b4437m3"></a>

<p align="center"><kbd><img src="assets/rpit0y1ic5o.png" width="80%"></kbd></p>

<br>

<a id="node-ycacgxt"></a>

<p align="center"><kbd><img src="assets/qmi5mmj2qe8.png" width="80%"></kbd></p>

<br>

<a id="node-wm4awr7"></a>

<p align="center"><kbd><img src="assets/vz3hr610n49.png" width="80%"></kbd></p>

<br>

<a id="node-om0h5de"></a>

<p align="center"><kbd><img src="assets/1m8qej545t9.png" width="80%"></kbd></p>

<br>

<a id="node-km359at"></a>

<p align="center"><kbd><img src="assets/jq0iuoh04yo.png" width="80%"></kbd></p>

<br>

<a id="node-ovpn6og"></a>

<p align="center"><kbd><img src="assets/a2zmof17iyb.png" width="80%"></kbd></p>

<br>

<a id="node-vtv52n3"></a>

### Programming Assignment

<br>

<a id="node-o72fvjg"></a>

#### Some Notes

<br>

<a id="node-cu36oxu"></a>

<p align="center"><kbd><img src="assets/8bre48tl89.png" width="80%"></kbd></p>

<br>

<a id="node-cplml7j"></a>

<p align="center"><kbd><img src="assets/zachsnskos.png" width="80%"></kbd></p>

<br>

<a id="node-rxyck6z"></a>

<p align="center"><kbd><img src="assets/u6ixs9urd6g.png" width="80%"></kbd></p>

<br>

<a id="node-x5g24jt"></a>

<p align="center"><kbd><img src="assets/coxjv40q63s.png" width="80%"></kbd></p>

<br>

<a id="node-shrzkur"></a>

<p align="center"><kbd><img src="assets/ohwd5vz2vqe.png" width="80%"></kbd></p>

<br>

<a id="node-9wkonlb"></a>

<p align="center"><kbd><img src="assets/ufubq3r2bme.png" width="80%"></kbd></p>

<br>

<a id="node-pin2bsp"></a>

#### Python Basic With Numpy

<br>

<a id="node-4vgpf5v"></a>

<p align="center"><kbd><img src="assets/53vdxv3mxcj.png" width="80%"></kbd></p>

<br>

<a id="node-2kvw88a"></a>

<p align="center"><kbd><img src="assets/9f6zlu08d9.png" width="80%"></kbd></p>

<br>

<a id="node-lx9cgmx"></a>

<p align="center"><kbd><img src="assets/30j80vh1jh9.png" width="80%"></kbd></p>

<br>

<a id="node-9h0ze3v"></a>

<p align="center"><kbd><img src="assets/ov9d4y33c7e.png" width="80%"></kbd></p>

<br>

<a id="node-sgu58p4"></a>

<p align="center"><kbd><img src="assets/v1bfum76a2c.png" width="80%"></kbd></p>

<br>

<a id="node-za50ura"></a>

<p align="center"><kbd><img src="assets/vzbtbrg4cx.png" width="80%"></kbd></p>

<br>

<a id="node-49igb3z"></a>

<p align="center"><kbd><img src="assets/6yr9jbz47dr.png" width="80%"></kbd></p>

<br>

<a id="node-lfwllc4"></a>

<p align="center"><kbd><img src="assets/fev6w8mzpwl.png" width="80%"></kbd></p>

<br>

<a id="node-rv1ppvv"></a>

<p align="center"><kbd><img src="assets/w8j2c0v1a4.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hvsjiia6hge.png" width="80%"></kbd></p>

<br>

<a id="node-b6zrjau"></a>

<p align="center"><kbd><img src="assets/k9l7bxeqre.png" width="80%"></kbd></p>

<br>

<a id="node-8ds722p"></a>

<p align="center"><kbd><img src="assets/06sdvwy75nb5.png" width="80%"></kbd></p>

<br>

<a id="node-4urtqru"></a>

<p align="center"><kbd><img src="assets/6pgen4qs4ej.png" width="80%"></kbd></p>

<br>

<a id="node-0197fte"></a>

<p align="center"><kbd><img src="assets/6p0si6fvgon.png" width="80%"></kbd></p>

<br>

<a id="node-hy4j2li"></a>

<p align="center"><kbd><img src="assets/mntgmamthp.png" width="80%"></kbd></p>

> [!NOTE]
> "This is a 3 by 3 by 2 array, typically images will be (num_px_x, num_px_y,3)
> where 3 represents the RGB values"
>
>
>
> Đây là một ma trận 3 x 3 x 2, thông thường hình ảnh sẽ có dạng (num_px_x,
> num_px_y, 3) trong đó 3 biểu diễn cho các giá trị RGB.  RGB là một mô hình
> màu sắc mà sử dụng 3 giá trị rời rạc để biểu  diễn một màu sắc cụ thể.
> num_px_x và num_px_y là chiều rộng  và chiều cao của hình ảnh.

<br>

<a id="node-h6yp7eq"></a>

<p align="center"><kbd><img src="assets/pqa1h2lx5x7.png" width="80%"></kbd></p>

> [!NOTE]
> Cái này là 2 colors channels image

<br>

<a id="node-1n2fzpu"></a>

<p align="center"><kbd><img src="assets/7ju4d5bgvns.png" width="80%"></kbd></p>

<br>

<a id="node-b7satb1"></a>

<p align="center"><kbd><img src="assets/do7cbv6c1el.png" width="80%"></kbd></p>

<br>

<a id="node-irfh6r7"></a>

<p align="center"><kbd><img src="assets/7wz2sfkzkj4.png" width="80%"></kbd></p>

<br>

<a id="node-egvo20a"></a>

<p align="center"><kbd><img src="assets/ediwvs07pt8.png" width="80%"></kbd></p>

<br>

<a id="node-cdk95jp"></a>

<p align="center"><kbd><img src="assets/lptj7mwwusc.png" width="80%"></kbd></p>

<br>

<a id="node-9uigwkw"></a>

<p align="center"><kbd><img src="assets/hf49yb242y8.png" width="80%"></kbd></p>

<br>

<a id="node-8p4z381"></a>

<p align="center"><kbd><img src="assets/r1gm1adsprs.png" width="80%"></kbd></p>

<br>

<a id="node-gatztbl"></a>

<p align="center"><kbd><img src="assets/zd6zi1ctfi.png" width="80%"></kbd></p>

<br>

<a id="node-h0b5bar"></a>

<p align="center"><kbd><img src="assets/ec5yi8afr4.png" width="80%"></kbd></p>

<br>

<a id="node-wfczsrh"></a>

<p align="center"><kbd><img src="assets/iblmdsp2ju.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/1shwgn619cl.png" width="80%"></kbd></p>

<br>

<a id="node-3cm5ls5"></a>

<p align="center"><kbd><img src="assets/fdu3t49ndka.png" width="80%"></kbd></p>

<br>

<a id="node-7masl4m"></a>

<p align="center"><kbd><img src="assets/yki9agieqn8.png" width="80%"></kbd></p>

<br>

<a id="node-m228id9"></a>

<p align="center"><kbd><img src="assets/urror7y4g9q.png" width="80%"></kbd></p>

<br>

<a id="node-7ukxkmp"></a>

<p align="center"><kbd><img src="assets/8qe09pdxgwr.png" width="80%"></kbd></p>

<br>

<a id="node-mu47ms9"></a>

<p align="center"><kbd><img src="assets/e0stws9c3d.png" width="80%"></kbd></p>

<br>

<a id="node-37z27xt"></a>

<p align="center"><kbd><img src="assets/lo7hhk02evp.png" width="80%"></kbd></p>

<br>

<a id="node-6ew9ih7"></a>

<p align="center"><kbd><img src="assets/no54rk8xys.png" width="80%"></kbd></p>

<br>

<a id="node-kuw1q9x"></a>

<p align="center"><kbd><img src="assets/4f6isnizn59.png" width="80%"></kbd></p>

> [!NOTE]
> * or np.multiply() = . * in Matlab

<br>

<a id="node-frpdqgj"></a>

<p align="center"><kbd><img src="assets/pm2b26ls8vk.png" width="80%"></kbd></p>

<br>

<a id="node-kmjh1w9"></a>

<p align="center"><kbd><img src="assets/cbu4oxku6ud.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu để keepdims = True thì bị lỗi tại Loss expect a float.

<br>

<a id="node-pwc2i3o"></a>

<p align="center"><kbd><img src="assets/erk7s9d60fo.png" width="80%"></kbd></p>

<br>

<a id="node-z1togx3"></a>

<p align="center"><kbd><img src="assets/19psud13wj.png" width="80%"></kbd></p>

<br>

<a id="node-ndndega"></a>

<p align="center"><kbd><img src="assets/wspr5czww2m.png" width="80%"></kbd></p>

<br>

<a id="node-tbndoks"></a>

<p align="center"><kbd><img src="assets/h9ygwaedla9.png" width="80%"></kbd></p>

> [!NOTE]
> So sánh function .dot() khi input là vector (1D array) và matrix (2D array)

<br>

<a id="node-ufua1j4"></a>

##### Grade

<br>

<a id="node-1l7ukpp"></a>

<p align="center"><kbd><img src="assets/elravmf4u3.png" width="80%"></kbd></p>

<br>

<a id="node-0aootz1"></a>

#### Logistic Regression With A Neural Network Mindset

> [!NOTE]
> Build a logistic regression classifier to recognize cats.  This
> assignment will step you through how to do this with a
> Neural Network mindset, and will also hone your intuitions
> about deep learning.

<br>

<a id="node-9v6x0ur"></a>

<p align="center"><kbd><img src="assets/d3akb5wlzrf.png" width="80%"></kbd></p>

<br>

<a id="node-7akz9d8"></a>

<p align="center"><kbd><img src="assets/c0tvw524nm.png" width="80%"></kbd></p>

<br>

<a id="node-1ansu7k"></a>

<p align="center"><kbd><img src="assets/kk0q5o8bd9.png" width="80%"></kbd></p>

<br>

<a id="node-rtmbzuf"></a>

<p align="center"><kbd><img src="assets/3aspn08l1r9.png" width="80%"></kbd></p>

<br>

<a id="node-ncpigm1"></a>

- **mpl.imshow()**

<br>

<a id="node-dvfcbym"></a>

<p align="center"><kbd><img src="assets/n0knxx5b5o.png" width="80%"></kbd></p>

<br>

<a id="node-m7kulgw"></a>

<p align="center"><kbd><img src="assets/pmxgdeczfeb.png" width="80%"></kbd></p>

<br>

<a id="node-rctsuuo"></a>

<p align="center"><kbd><img src="assets/102u2wuydux.png" width="80%"></kbd></p>

<br>

<a id="node-03opkkr"></a>

<p align="center"><kbd><img src="assets/0zhobo2bczh.png" width="80%"></kbd></p>

<br>

<a id="node-pmpxamt"></a>

<p align="center"><kbd><img src="assets/rvod0j26v4.png" width="80%"></kbd></p>

> [!NOTE]
> Hàm reshape cứ nhớ là nếu cho cái dimension = -1 thì đại khái
> là bảo Python tự tính.

<br>

<a id="node-uotzh6g"></a>

<p align="center"><kbd><img src="assets/t68ef579ni.png" width="80%"></kbd></p>

<br>

<a id="node-q756cyr"></a>

<p align="center"><kbd><img src="assets/dzc9aezvl9r.png" width="80%"></kbd></p>

> [!NOTE]
> Trong ví dụ dưới u.shape là 2x3x2 nên khi 
> reshape(u.shape[0], -1) hay reshape(u.shape[2], -1) thì cũng 
> như nhau vì đều là reshape(2, -1). 
> Có nghĩa là ta bảo nó làm sao có 2 row, còn lại số column 
> bao nhiêu thì tự tính.
>
>
>
> Vả nếu nó tính ko ra được (đại khái là nó không chia element 
> đều ra được thì nó sẽ báo lỗi)
> Ví dụ có 12 unit (2x3x2) mà reshape(5,-1) thì nó sẽ lỗi vì 12 cái 
> mà muốn sắp thành 5 hàng thì ko chẵn.
> Nhưng reshape(6,-1) thì ok => 6x2

<br>

<a id="node-asul9et"></a>

<p align="center"><kbd><img src="assets/6pu4nx8qhak.png" width="80%"></kbd></p>

<br>

<a id="node-8mgzzk6"></a>

<p align="center"><kbd><img src="assets/z0xqvm8t18.png" width="80%"></kbd></p>

<br>

<a id="node-3faamti"></a>

<p align="center"><kbd><img src="assets/8l45lo52h1.png" width="80%"></kbd></p>

<br>

<a id="node-wwjlxa4"></a>

<p align="center"><kbd><img src="assets/z5qluu4nu3.png" width="80%"></kbd></p>

<br>

<a id="node-xq7fyrr"></a>

<p align="center"><kbd><img src="assets/om2b5v0nn2m.png" width="80%"></kbd></p>

<br>

<a id="node-t5cauzr"></a>

<p align="center"><kbd><img src="assets/8zc907ifdzb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qziqx6q2x3l.png" width="80%"></kbd></p>

> [!NOTE]
> Vì hàm np.exp() accept vector or matrix -> dùng nó
> trong hàm sigmoid cũng sẽ accept vector . matrix

<br>

<a id="node-hkdr0dn"></a>

<p align="center"><kbd><img src="assets/5eeoyhxx1h.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu define b = 0 -> b sẽ là int

<br>

<a id="node-nqltpgu"></a>

<p align="center"><kbd><img src="assets/8qm9d5qama8.png" width="80%"></kbd></p>

<br>

<a id="node-c7pekm2"></a>

<p align="center"><kbd><img src="assets/180kkhrdypw.png" width="80%"></kbd></p>

<br>

<a id="node-tywnw4c"></a>

<p align="center"><kbd><img src="assets/3lso7ev6yny.png" width="80%"></kbd></p>

> [!NOTE]
> Chỉ có hơi rắc rối chưa quen dùng hàm **np.dot
>
>
>
> Và khác với Khoá ML cũ, X define dạng n x m 
> (chứ không phải m x n) nên lấy m = X.shape[1]**

<br>

<a id="node-8hiksmz"></a>

<p align="center"><kbd><img src="assets/ndfbd1zckjl.png" width="80%"></kbd></p>

<br>

<a id="node-99kigh8"></a>

<p align="center"><kbd><img src="assets/h4u83feactt.png" width="80%"></kbd></p>

<br>

<a id="node-xosd57q"></a>

<p align="center"><kbd><img src="assets/w98hmv87cui.png" width="80%"></kbd></p>

<br>

<a id="node-ky3uy1n"></a>

<p align="center"><kbd><img src="assets/cput3yjtmz7.png" width="80%"></kbd></p>

<br>

<a id="node-v644tom"></a>

- **hàm np.dot()**

<br>

<a id="node-iqt4qlp"></a>

<p align="center"><kbd><img src="assets/nx2v2pi3a1q.png" width="80%"></kbd></p>

> [!NOTE]
> np.dot()
>
>
>
> 2 Matrix thì tuân thủ quy tắc size matrix

<br>

<a id="node-pnixfxz"></a>

<p align="center"><kbd><img src="assets/tdbcagppfx.png" width="80%"></kbd></p>

> [!NOTE]
> (2x3) không thể .dot với (2x3)

<br>

<a id="node-y4afx78"></a>

<p align="center"><kbd><img src="assets/3jcoe45emr2.png" width="80%"></kbd></p>

> [!NOTE]
> np.dot()
>
>
>
> 2 1D array thì + lại.

<br>

<a id="node-rdus0x7"></a>

<p align="center"><kbd><img src="assets/zpc219hvgla.png" width="80%"></kbd></p>

> [!NOTE]
> np.dot()
>
>
>
> 1D array với Matrix cột thì được, coi matrix cột như 1D array

<br>

<a id="node-cq8qyea"></a>

<p align="center"><kbd><img src="assets/1cheamv9z77.png" width="80%"></kbd></p>

<br>

<a id="node-ofpfdka"></a>

<p align="center"><kbd><img src="assets/w9gyzg44yd.png" width="80%"></kbd></p>

<br>

<a id="node-gr4xer9"></a>

<p align="center"><kbd><img src="assets/mjdtzxtb00h.png" width="80%"></kbd></p>

<br>

<a id="node-fi82j3x"></a>

<p align="center"><kbd><img src="assets/6u5vfsco36.png" width="80%"></kbd></p>

> [!NOTE]
> **CHÚ Ý BƯỚC NÀY** w = w.reshape(X.shape[0], 1) **LÀ ĐỂ CHẮC CHẮN
> W CÓ SHAPE MONG MUỐN
>
>
>
> Trong lecture ổng có nhấn mạnh đừng ngại reshape để đảm bảo shape
> đúng**

<br>

<a id="node-5exijgv"></a>

<p align="center"><kbd><img src="assets/wiqjmyophtd.png" width="80%"></kbd></p>

<br>

<a id="node-x7cxxy1"></a>

<p align="center"><kbd><img src="assets/olbhdxatvh.png" width="80%"></kbd></p>

<br>

<a id="node-s2r9t5h"></a>

<p align="center"><kbd><img src="assets/6f3mmi4n9bl.png" width="80%"></kbd></p>

<br>

<a id="node-3ompd2q"></a>

<p align="center"><kbd><img src="assets/avltad3have.png" width="80%"></kbd></p>

<br>

<a id="node-1fbtpe2"></a>

<p align="center"><kbd><img src="assets/kp46dzwutch.png" width="80%"></kbd></p>

<br>

<a id="node-gf00we8"></a>

<p align="center"><kbd><img src="assets/zwwzn6yk7d.png" width="80%"></kbd></p>

> [!NOTE]
> **optimize(...X_train, Y_train,...) mới đúng, chứ với X, Y là sai**

<br>

<a id="node-0x2vtd1"></a>

<p align="center"><kbd><img src="assets/k45kgg4sx1e.png" width="80%"></kbd></p>

> [!NOTE]
> **Comment**: Training accuracy is close to 100%. 
> This is a **good** sanity check: your model is working and has high 
> enough capacity to fit the training data. 
> Test accuracy is **70%. It is actually not bad for this simple model,** 
> given the small dataset we used and that logistic regression is a 
> linear classifier. But no worries, you'll build an even better classifier 
> next week!
> Also, you see that the model is **clearly overfitting** the training data. 
> Later in this specialization you will learn how to reduce overfitting, 
> for example by using **regularization**.

<br>

<a id="node-j1xafpn"></a>

<p align="center"><kbd><img src="assets/ymlpvtybxv.png" width="80%"></kbd></p>

<br>

<a id="node-6ne5eua"></a>

<p align="center"><kbd><img src="assets/syqrgzvx6o.png" width="80%"></kbd></p>

<br>

<a id="node-nqn1qcp"></a>

<p align="center"><kbd><img src="assets/3jracx7a60y.png" width="80%"></kbd></p>

> [!NOTE]
> **Thử với các learning rate khác nhau**

<br>

<a id="node-xl5l54i"></a>

<p align="center"><kbd><img src="assets/v04lo3zqbe.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/f55krbq9u0h.png" width="80%"></kbd></p>

<br>

<a id="node-ochl790"></a>

<p align="center"><kbd><img src="assets/gbg23rz6ntp.png" width="80%"></kbd></p>

<br>

<a id="node-6rm027w"></a>

<p align="center"><kbd><img src="assets/6n0r67qlnin.png" width="80%"></kbd></p>

<br>

<a id="node-bmlagme"></a>

## C1w3_shalow Neural Networks

<br>

<a id="node-f4y4xfd"></a>

### Neural Networks Overview

<br>

<a id="node-2j8qfge"></a>

#### 1 Overview of the week's topic: The speaker provides an introduction to the topic of
implementing a neural network.

2 Recap of logistic regression: The speaker briefly recaps the logistic regression model, which
involves computing a z-value based on input features x and parameters w and b, then using a
sigmoid function to calculate the output value a or y-hat, which is used to compute the loss
function L.

3 Neural network structure: The speaker introduces the structure of a neural network, which
involves stacking together many sigmoid units. Each node in the network involves two
calculations: a z-like calculation and an a-like calculation. The network is composed of layers,
with superscript square brackets used to refer to quantities associated with each layer.

4 Calculation of z and a: The speaker explains that the network starts by computing z1 based on
input features x, then computes a1 as the sigmoid of z1. The process is repeated to compute z2
and a2, which is the final output of the neural network and is also referred to as y-hat.

5 Backward calculation: The speaker notes that the network requires a backward calculation in
order to compute derivatives and make updates to the parameters w and b. This calculation
involves computing da2, dz2, dw2, and db2 in a right-to-left manner.

6 Key takeaway: The speaker emphasizes that a neural network is essentially an extension of
logistic regression, where the z and a calculations are repeated multiple times. The notation and
details can be complex, but they will be further explained in upcoming videos.

<br>

<a id="node-gqdvcii"></a>

<p align="center"><kbd><img src="assets/rsy1rjh493.png" width="80%"></kbd></p>

<br>

<a id="node-x46botd"></a>

### Neural Network Representation

<br>

<a id="node-bnjp1mk"></a>

#### 1 Explanation of a two-layer neural network with multiple hidden units

2 The neural network computes the output in the same way as logistic
regression but repeatedly

3 Each node in the hidden layer of the neural network performs two
steps of computation

4 The first step is the computation of z = w transpose x + b

5 The second step is the computation of a = sigmoid(z)

6 The notation used in the computation of a and z

7 Explanation of the first and second hidden units in the neural
network

8 The process of vectorizing the computation for efficiency

9 The matrix of weight vectors and input features multiplied to get z

10 Adding the bias vector to z

11 The outcome of the computation corresponds to the values of z for
each hidden unit.

12 The vector is called the vector of activations.

<br>

<a id="node-nyzr92n"></a>

<p align="center"><kbd><img src="assets/wbyp3dtexma.png" width="80%"></kbd></p>

<br>

<a id="node-orwg57n"></a>

### Computing A Neural Network's Output

<br>

<a id="node-fxpurel"></a>

#### 1 The video provides justification for the vectorized implementation for
propagation through a neural network by considering the forward propagation
calculation for a few examples.

2 The matrix X is formed by stacking together all of the training examples, and
when this matrix is multiplied by W, the resulting matrix contains the
corresponding outputs stacked up in columns.

3 The video recapitulates the steps for implementing forward propagation for
one training example at a time and then shows how to vectorize it across all
training examples at the same time.

4 The video also highlights the symmetry in the equations for the different
layers of the neural network and how deeper neural networks repeat the same
computation even more times.

5 Finally, the video notes that sigmoid functions are not always the best choice
for neural networks and hints at the topic of the next video, which will explore
using different activation functions.

<br>

<a id="node-uyba17r"></a>

<p align="center"><kbd><img src="assets/moxkxbrdk4m.png" width="80%"></kbd></p>

<br>

<a id="node-8x10oix"></a>

<p align="center"><kbd><img src="assets/1rrzmxyuajz.png" width="80%"></kbd></p>

<br>

<a id="node-udlw3rf"></a>

<p align="center"><kbd><img src="assets/5kmoavwb37i.png" width="80%"></kbd></p>

<br>

<a id="node-yxwgozk"></a>

### Vectorizing Across Multiple

<br>

<a id="node-w1z6m0s"></a>

#### 1 To compute the prediction on a neural network for multiple training
examples, you need to vectorize the computation process.

2 To do this, you need to repeat the process for each training example,
using the activation function notation a\\_2\\_.

3 To get rid of the repetition, you can stack the training examples in
columns to create a matrix X.

4 You can then compute the value of the different variables, Z[1], A[1],
Z[2], and A[2], using the matrix X, and the weights W and biases b.

5 By stacking the vectors in columns for Z[1], A[1], Z[2], and A[2], you
can create the matrices Z[1], A[1], Z[2], and A[2], respectively.

6 Vectorizing the computation process allows you to compute the
predictions of all your training examples at the same time.

<br>

<a id="node-04e9a59"></a>

<p align="center"><kbd><img src="assets/pdg2j6gq2en.png" width="80%"></kbd></p>

<br>

<a id="node-3njvn5i"></a>

<p align="center"><kbd><img src="assets/n3sj1238h1k.png" width="80%"></kbd></p>

<br>

<a id="node-mpg67s5"></a>

### Explanation For Vectorized Implementation

<br>

<a id="node-s08d36u"></a>

#### Main ideas:  1 The previous video discussed the vectorized implementation of neural
network propagation through training examples horizontally stacked in the matrix x.

2 The justification for the correctness of the equations was explained by going
through part of the forward propagation calculation for a few examples.

3 The training set X is formed by vertically stacking the vectors x1, x2, etc. and
multiplying it by w gives the corresponding z values, which are also vertically stacked
in matrix capital Z1.

4 Python broadcasting allows adding the bias term b to the values while maintaining
the correct values.

5 Similar reasoning can be used to show that all four steps of the forward
propagation calculation work.

6 Recap of the four steps of forward propagation and how they can be vectorized
across multiple training examples using stacked matrices.

7 The symmetry between the equations for z1 and a1 and z2 and a2 shows that the
different layers of a neural network are doing the same computation.

8 Next, the video will discuss why the sigmoid function is not the best choice for
neural networks.

<br>

<a id="node-s7lbg0h"></a>

<p align="center"><kbd><img src="assets/go3xu53isys.png" width="80%"></kbd></p>

<br>

<a id="node-mdvhfgd"></a>

<p align="center"><kbd><img src="assets/4ltzyxzlpco.png" width="80%"></kbd></p>

> [!NOTE]
> **ĐẠI KHÁI LÀ CHỈ CÓ VẬY THÔI, MORE DEEPLY N.N CŨNG CHỈ 
> LÀ LẶP LẠI NHIỀU LẦN NHỮNG PHÉP TÍNH KIỂU NÀY.**
>
>
>
> So this kind of shows that the different layers of a neural network
> are roughly doing the same thing or just doing the same
> computation  over and over. And here we have two-layer neural
> network where we  go to a much deeper neural network in next
> week's videos. You see  that /**even deeper neural networks are
> basically taking these two steps and just doing them even more
> times** /than you're seeing here

<br>

<a id="node-gox8wis"></a>

### Activation Functions

<br>

<a id="node-608rbgf"></a>

#### Main ideas:  1 Choice of activation function is an important decision when
building a neural network.

2 The sigmoid function is commonly used but there are other options that can
work better.

3 The hyperbolic tangent (tan h) function is often a better choice for hidden
layers.

4 The mean of activations using tan h is closer to zero, making learning easier.

5 The sigmoid function is useful for binary classification output layers.

6 The rectified linear unit (ReLU) and Leaky ReLU are popular choices for
hidden layers.

7 The ReLU and Leaky ReLU have advantages over sigmoid and tan h
functions.

8 Choosing an activation function depends on the specific task and the
individual preferences of the user.

<br>

<a id="node-fbyfsx0"></a>

<p align="center"><kbd><img src="assets/ephj7vo39pt.png" width="80%"></kbd></p>

> [!NOTE]
> - Hàm **tanh** tốt hơn sigmoid vì nó đại khái là 'center' hơn, kiểu 
> như quay quay 0 thay vì 0.5 như sigmoid giúp g.d chạy nhanh 
> hơn kiểu kiểu như tại sao ',mean normalization' giúp g.d chạy 
> nhanh hơn vậy.
>
>
>
> - Do đó hàm **sigmoid** ít dùng nữa trừ việc dùng cho output là a 
> binary classification vì tự nhiên sigmoid sẽ phù hợp hơn khi 
> xuất ra giá trị P trong khoảng (0,1)
>
>
>
> - Hidden layer: **Relu, Leaky Relu** or Tanh trong đó:
> **Cứ default Relu, còn thích cứ thử Leaky Relu** 
>
>
>
> - Tại sao Relu tốt hơn thì:
> Đại khái là hàm Relu hay Leaky Relu có **'derivative' ít bị bằng
> 0** hơn (Nhìn vào đồ thị hàm sigmoid và Tanh có 2 đầu đi 
> ngang - hoặc gần ngang 
> -> Đạo hàm bằng 0) 
> -> Làm chậm quá trình gradient descent

<br>

<a id="node-eqkhkg1"></a>

<p align="center"><kbd><img src="assets/upjmnry9gte.png" width="80%"></kbd></p>

<br>

<a id="node-tuj3lvk"></a>

<p align="center"><kbd><img src="assets/5gsukyk5c1.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là khi làm thực tế có nhiều lúc ko biết chọn bao
> nhiêu layer, bao nhiêu unit, dùng activation function, initializa
> như thế nào ...thì nếu thấy không  chắc biết dùng cái nào
> thay vì cái nào thì **cứ thử hết và dùng CV set để so sánh kết
> quả**. Khi đó mình sẽ có 1 cảm giác / cảm nhận về 'evolution'
> của algorithm thay vì cứ nhắm mắt nghe theo lời khuyên nên
> dùng hàm Relu hay gì gì vì có thể nó không đúng với trường
> hợp cụ thể của mình

<br>

<a id="node-jgcfl44"></a>

### Why Do You Need Non-linear Activation Functions

<br>

<a id="node-0k865rd"></a>

#### 1 A neural network needs a non-linear activation function to compute interesting functions.

2 The linear activation function, which just outputs whatever was input, is not useful because
the neural network outputs a linear function of the input.

3 Even in deep neural networks with many layers, if linear activation functions are used, the
network is just computing a linear activation function and is therefore not computing more
interesting functions.

4 One place where a linear activation function might be used is in the output layer for
regression problems, where the output y-hat is a real number going anywhere from minus
infinity to plus infinity.

5 However, in this case, the hidden units should not use activation functions or should use
non-linear activation functions like ReLU or tanh.

6 Using a linear activation function in the hidden layer is extremely rare except for some
special circumstances relating to compression.

7 The non-linear activation function is a critical part of neural networks because it allows for
the computation of more interesting functions.

8 In the next video, the slope or the derivatives of individual activation functions will be
discussed to set up for the discussion on gradient descent.

<br>

<a id="node-320r7or"></a>

<p align="center"><kbd><img src="assets/i8kl15lwec.png" width="80%"></kbd></p>

> [!NOTE]
> 1. Linear apply to linear = linear, nên dùng cho hidden layer thì cũng 
> coi như không có hidden layer = không 'learn' thêm được
> Interesting feature nào.
>
>
>
> Trừ những trường hợp rất đặc biệt (rất hiếm) chứ ko dùng linear
> Function ở hidden layer
>
>
>
>  2. Trừ trường hợp output layer là regression (ví dụ predict
> House price) thì dùng linear function thôi.

<br>

<a id="node-5vzjox7"></a>

### Derivatives Of Activation Functions

<br>

<a id="node-z08v09d"></a>

#### Main ideas:  1 Backpropagation in neural networks requires
computing the slope or derivative of the activation functions.

2 Sigmoid activation function has a derivative formula of g(z) * (1 -
g(z)).

3 The Tanh activation function has a derivative formula of 1 - a^2.

4 ReLU activation function has a derivative of 0 for z < 0 and 1 for z >
0.

5 Leaky ReLU activation function has a small positive slope for z < 0
and a slope of 1 for z > 0.

<br>

<a id="node-ohje1ye"></a>

<p align="center"><kbd><img src="assets/xkq7rddwq38.png" width="80%"></kbd></p>

<br>

<a id="node-cz5j3jx"></a>

<p align="center"><kbd><img src="assets/o1fzsa8i4a.png" width="80%"></kbd></p>

> [!NOTE]
> But you can think of it as that, **the chance of z being exactly 0.
> 000000 Is so small** that it almost doesn't matter where you  set
> the derivative to be equal to when z is equal to 0
>
> Finally, here's how you compute the derivatives for the ReLU and
> Leaky ReLU activation functions. For the value g of z is equal to
> max of (0,z), so the derivative is equal to, turns out to be 0 , if z is
> less than 0 and 1 if z is greater than 0. **It's actually undefined,
> technically undefined if z is equal to exactly 0.**

<br>

<a id="node-3npbfg1"></a>

<p align="center"><kbd><img src="assets/p3g4gb5mjs.png" width="80%"></kbd></p>

> [!NOTE]
> Giải thích tại sao derivative của relu lại undefine tại  z = 0

<br>

<a id="node-i71mtds"></a>

<p align="center"><kbd><img src="assets/c6qr104zgom.png" width="80%"></kbd></p>

<br>

<a id="node-ugnkpbj"></a>

### Gradient Descent For Neural Networks

<br>

<a id="node-rubn3wi"></a>

#### 1 Introduction to implementing gradient descent for neural network with
one hidden layer.

2 Explanation of the parameters and dimensions for a neural network
with a single hidden layer.

3 Cost function for binary classification and how to train the parameters
using gradient descent.

4 Initialization of parameters and the importance of random initialization.

5 Derivatives of the cost function with respect to the parameters W1,
B1, W2, and B2.

6 Forward propagation for computation of neural network outputs.

7 Back propagation for computing derivatives and updating the
parameters using gradient descent.

8 Explanation of Python NumPy commands used to compute the
derivatives.

<br>

<a id="node-dz2qwsu"></a>

<p align="center"><kbd><img src="assets/p5jyea8mue.png" width="80%"></kbd></p>

<br>

<a id="node-fuzjzyw"></a>

<p align="center"><kbd><img src="assets/3rwk5738mxj.png" width="80%"></kbd></p>

<br>

<a id="node-auop411"></a>

### Backpropagation Intuition

<br>

<a id="node-ivta3do"></a>

#### 1 The video explains the intuition for deriving the equations for backpropagation
using a computation graph.

2 The forward pass in logistic regression involves computing z, A, and A loss,
while the backward pass involves computing da, dz, dw, and db.

3 The loss function for logistic regression is L(a, y) = -y log A - (1 - y) log(1 - A).

4 Da for logistic regression is equal to -y/A + (1 - y)/(1 - A).

5 Dz for logistic regression is equal to A - y, which is computed using the chain
rule of calculus.

6 Dw for logistic regression is equal to dz times x, while db is equal to dz.

7 In a two-layer neural network, backpropagation computes da2, dz2, dw2, and
db2, and then computes da1, dz1, dw1, and db1.

8 Da1 and dz1 are often collapsed into one step in practice.

9 Dz1 is computed as w2 transpose times dz2 times an element-wise product of
g1 prime of z1.

10 The computation for dz2 is the same as for logistic regression, dz2 = a2 - y.

11 Dw2 is equal to dz2 times a1 transpose, and db2 is equal to dz2.

12 There is an extra transpose in dw2 compared to dw for logistic regression
because a1 is a row vector while w2 is a column vector.

<br>

<a id="node-zpdmaj6"></a>

<p align="center"><kbd><img src="assets/gnh5gtrqqej.png" width="80%"></kbd></p>

<br>

<a id="node-jhog66u"></a>

<p align="center"><kbd><img src="assets/iivhwvxjbjp.png" width="80%"></kbd></p>

> [!NOTE]
> One tip when implementing backprop, if you just make sure that the
> dimensions of your matrices match up, if you think through, what are the
> dimensions of your various matrices including w^1, w^2, z^1, z^2, a^1, a^2,
> and so on, and **just make sure that the dimensions of these matrix
> operations may match up**, sometimes that will **already eliminate quite a lot
> of bugs** in backprop

<br>

<a id="node-e471v2g"></a>

<p align="center"><kbd><img src="assets/43gwsc1nid.png" width="80%"></kbd></p>

<br>

<a id="node-j4nmrx2"></a>

<p align="center"><kbd><img src="assets/jrvjyg8d8qn.png" width="80%"></kbd></p>

> [!NOTE]
> Chỗ này nói trông giống của Logistic regression chỉ
> khác thêm cái  'transpose' là do W quan hệ với w theo
> kiểu W là matrix mà các  hàng là w.T .
>
> This step is quite similar for logistic regression, where we
> had that  dw was equal to dz times x, except that now, a^1
> plays the role of  x, and there's an extra transpose there.
> Because the relationship  between the capital matrix
> W and our individual parameters w  was, there's a
> transpose there, because w is equal to a row vector.In the
> case of logistic regression with the single output, dw^2 is
> like  that, whereas w here was a column vector. That's why
> there's an extra  transpose for a^1, whereas we didn't for x
> here for logistic regression.

<br>

<a id="node-zehlb1j"></a>

<p align="center"><kbd><img src="assets/2zg65ktrypc.png" width="80%"></kbd></p>

<br>

<a id="node-qwiel4a"></a>

### Random Initialization

<br>

<a id="node-ib46rdj"></a>

#### 1 When changing the neural network, it is important to initialize the weights
randomly.

2 For logistic regression, initializing the weights to zero was okay, but it won't
work for neural networks.

3 Initializing w to all zeros and then applying gradient descent creates
symmetry between the hidden units.

4 Symmetry means that both hidden units are computing the same function
and will remain symmetric after every iteration.

5 The solution is to initialize the parameters randomly.

6 You can use np.random.randn to generate a Gaussian random variable for
w1, multiply it by a very small number, such as 0.01, and initialize b to zero.

7 The same applies to w2 and b2.

8 Initializing weights to very large values causes the activation function to be
saturated, which slows down learning.

9 Multiplying by a small number, such as 0.01, is reasonable to avoid the
saturation of the activation function.

10 Same goes for w2.

<br>

<a id="node-atturvh"></a>

<p align="center"><kbd><img src="assets/4fstun5ukuc.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu initialize params  = 0 hết thì gradient descent thì cả network
> các hidden layer vô nghĩa

<br>

<a id="node-djbt7z5"></a>

<p align="center"><kbd><img src="assets/7gqq3h6ssy9.png" width="80%"></kbd></p>

> [!NOTE]
> Giải pháp là small random number.
>
>
>
> Tại sao không phải large random number, vì khi đó đại khái là
> Ta sẽ bắt đầu ở đoạn cuối hay đầu của đồ thị hàm sigmoid, tanh
> nơi mà đường đồ thị nằm ngang - > Derivative = 0 => 
> dẫn đến là Gradient descent rất chậm.

<br>

<a id="node-boo5q7x"></a>

<p align="center"><kbd><img src="assets/z6de2530lo.png" width="80%"></kbd></p>

<br>

<a id="node-exkw9bw"></a>

### Quiz: Shallow Neural Network

<br>

<a id="node-8dsd1cu"></a>

<p align="center"><kbd><img src="assets/izens289a6e.png" width="80%"></kbd></p>

<br>

<a id="node-4ojeoy6"></a>

<p align="center"><kbd><img src="assets/vmjzoygya5o.png" width="80%"></kbd></p>

<br>

<a id="node-d4acqu4"></a>

<p align="center"><kbd><img src="assets/cxji6rehg3a.png" width="80%"></kbd></p>

<br>

<a id="node-afld8n7"></a>

<p align="center"><kbd><img src="assets/qjoo5f2kh9.png" width="80%"></kbd></p>

<br>

<a id="node-vds21tt"></a>

<p align="center"><kbd><img src="assets/bjvny98w0lc.png" width="80%"></kbd></p>

<br>

<a id="node-7c3wcsk"></a>

<p align="center"><kbd><img src="assets/f4dxokl8pdf.png" width="80%"></kbd></p>

<br>

<a id="node-flcfspw"></a>

<p align="center"><kbd><img src="assets/6i3433x4viu.png" width="80%"></kbd></p>

<br>

<a id="node-uc6cp3z"></a>

<p align="center"><kbd><img src="assets/p5t2e2s0d0c.png" width="80%"></kbd></p>

<br>

<a id="node-isbfjo7"></a>

<p align="center"><kbd><img src="assets/7jh375q54oc.png" width="80%"></kbd></p>

<br>

<a id="node-gt7zcy8"></a>

<p align="center"><kbd><img src="assets/5ucjm6xlw2c.png" width="80%"></kbd></p>

<br>

<a id="node-8amwjal"></a>

<p align="center"><kbd><img src="assets/unhpimvdbc.png" width="80%"></kbd></p>

<br>

<a id="node-u4svs4q"></a>

<p align="center"><kbd><img src="assets/u063b4fhquh.png" width="80%"></kbd></p>

<br>

<a id="node-m42nj4l"></a>

### Programming Assignment: Planar Data
classification With One Hidden Layer

<br>

<a id="node-bcqelas"></a>

#### 1. + 2.

<br>

<a id="node-4y0d5ny"></a>

<p align="center"><kbd><img src="assets/9i765uudo6.png" width="80%"></kbd></p>

<br>

<a id="node-weuw2pk"></a>

<p align="center"><kbd><img src="assets/opot13baa6e.png" width="80%"></kbd></p>

<br>

<a id="node-1rofryu"></a>

<p align="center"><kbd><img src="assets/zp3td8o3vqo.png" width="80%"></kbd></p>

<br>

<a id="node-dvcyfu4"></a>

#### 3 - Simple Logistic Regression

<br>

<a id="node-ti1gk0y"></a>

<p align="center"><kbd><img src="assets/fk3y30ifso4.png" width="80%"></kbd></p>

<br>

<a id="node-r30xuxr"></a>

<p align="center"><kbd><img src="assets/q8cuqpt7s2.png" width="80%"></kbd></p>

<br>

<a id="node-q3zz11j"></a>

#### 4.2 - Initialize the model's parameters

<br>

<a id="node-cu7snpc"></a>

#### 4 - Neural Network model¶

<br>

<a id="node-nsv6gmh"></a>

<p align="center"><kbd><img src="assets/v0qswwisd6q.png" width="80%"></kbd></p>

<br>

<a id="node-dkq6hh9"></a>

<p align="center"><kbd><img src="assets/t5cvm4e9k1.png" width="80%"></kbd></p>

<br>

<a id="node-fnof5ok"></a>

#### 4.1 - Defining the neural network structure

<br>

<a id="node-kj150j6"></a>

<p align="center"><kbd><img src="assets/hh9jyqv8b7.png" width="80%"></kbd></p>

<br>

<a id="node-706i843"></a>

<p align="center"><kbd><img src="assets/lrn0dw29aii.png" width="80%"></kbd></p>

<br>

<a id="node-deq4qxk"></a>

#### 4.2 - Initialize the model's parameters

<br>

<a id="node-5pl3d5e"></a>

<p align="center"><kbd><img src="assets/ne278zns3bd.png" width="80%"></kbd></p>

<br>

<a id="node-zjoxwtw"></a>

<p align="center"><kbd><img src="assets/cl5jlbrdbzf.png" width="80%"></kbd></p>

<br>

<a id="node-gq0hah4"></a>

<p align="center"><kbd><img src="assets/06jjzcc8mb74.png" width="80%"></kbd></p>

<br>

<a id="node-r135dfw"></a>

#### 4.3 - The loop

<br>

<a id="node-qclnw17"></a>

<p align="center"><kbd><img src="assets/vgpo3j9yusa.png" width="80%"></kbd></p>

<br>

<a id="node-4uav0k8"></a>

<p align="center"><kbd><img src="assets/0qlcssi7546e.png" width="80%"></kbd></p>

<br>

<a id="node-q7w3v1a"></a>

<p align="center"><kbd><img src="assets/a0csk6k1zcb.png" width="80%"></kbd></p>

<br>

<a id="node-06usjb7"></a>

#### 4.4 - Compute the Cost

<br>

<a id="node-iqivkb8"></a>

<p align="center"><kbd><img src="assets/81qhndc7ap7.png" width="80%"></kbd></p>

<br>

<a id="node-vizvjma"></a>

<p align="center"><kbd><img src="assets/vodgs1rxw7.png" width="80%"></kbd></p>

<br>

<a id="node-e5vvle4"></a>

<p align="center"><kbd><img src="assets/m2vcp1zy39i.png" width="80%"></kbd></p>

<br>

<a id="node-tgpg2r5"></a>

#### 4.5 - Implement Backpropagation

<br>

<a id="node-rr9wi1i"></a>

<p align="center"><kbd><img src="assets/b0et5dy3eww.png" width="80%"></kbd></p>

<br>

<a id="node-iae14r2"></a>

<p align="center"><kbd><img src="assets/k0leeyc8reo.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/p1nqp9hqgjn.png" width="80%"></kbd></p>

<br>

<a id="node-vxyqvuk"></a>

<p align="center"><kbd><img src="assets/odwxyrt8lf.png" width="80%"></kbd></p>

<br>

<a id="node-lmus9rg"></a>

#### 4.6 - Update Parameters

<br>

<a id="node-wvj721o"></a>

<p align="center"><kbd><img src="assets/waslr4ajexf.png" width="80%"></kbd></p>

<br>

<a id="node-9hjwiom"></a>

<p align="center"><kbd><img src="assets/u9kzpgo6byi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ax0wlwplgpo.png" width="80%"></kbd></p>

<br>

<a id="node-m3qzoxw"></a>

<p align="center"><kbd><img src="assets/swbllskomq.png" width="80%"></kbd></p>

<br>

<a id="node-k10t5wc"></a>

#### 4.7 - Integration

<br>

<a id="node-gkzr43g"></a>

<p align="center"><kbd><img src="assets/579siipmbyb.png" width="80%"></kbd></p>

<br>

<a id="node-rihjaxc"></a>

<p align="center"><kbd><img src="assets/v6jekl0rdid.png" width="80%"></kbd></p>

<br>

<a id="node-ewx84fl"></a>

<p align="center"><kbd><img src="assets/ao9t6ylqn2j.png" width="80%"></kbd></p>

<br>

<a id="node-hw8b570"></a>

#### 5 - Test the Model

<br>

<a id="node-n4unzvm"></a>

##### 5.1 - Predict

<br>

<a id="node-lpkflew"></a>

<p align="center"><kbd><img src="assets/zcttj9a6k7q.png" width="80%"></kbd></p>

<br>

<a id="node-xefhhx6"></a>

<p align="center"><kbd><img src="assets/ccya6xe0p5.png" width="80%"></kbd></p>

<br>

<a id="node-o3aqvjq"></a>

##### 5.2 - Test the Model on the Planar Dataset

<br>

<a id="node-3jwpcno"></a>

<p align="center"><kbd><img src="assets/3956dzdml9d.png" width="80%"></kbd></p>

<br>

<a id="node-1br1w7h"></a>

<p align="center"><kbd><img src="assets/erv5rszct3.png" width="80%"></kbd></p>

<br>

<a id="node-uutimcf"></a>

<p align="center"><kbd><img src="assets/53gf71cmoum.png" width="80%"></kbd></p>

<br>

<a id="node-3bc161m"></a>

#### 6 - Tuning hidden layer size

<br>

<a id="node-pnjwkgr"></a>

<p align="center"><kbd><img src="assets/v3qpylbph2c.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ku30skwt7so.png" width="80%"></kbd></p>

<br>

<a id="node-ds3xc88"></a>

#### 7- Performance on other datasets

<br>

<a id="node-lrp8ac1"></a>

<p align="center"><kbd><img src="assets/4x8dyebucos.png" width="80%"></kbd></p>

<br>

<a id="node-luxk4vf"></a>

#### Thực Hành F.p & B.p

<br>

<a id="node-l41hjbw"></a>

##### L.g

<br>

<a id="node-rafea5t"></a>

<p align="center"><kbd><img src="assets/cwumpqbsof4.png" width="80%"></kbd></p>

<br>

<a id="node-b5k45hj"></a>

<p align="center"><kbd><img src="assets/hzq4e20ctq.png" width="80%"></kbd></p>

<br>

<a id="node-pwwqqp8"></a>

##### S.n.n

<br>

<a id="node-27ff1co"></a>

<p align="center"><kbd><img src="assets/nk9kwyd6pp.png" width="80%"></kbd></p>

<br>

<a id="node-oncz50t"></a>

<p align="center"><kbd><img src="assets/gsl6kigfkhe.png" width="80%"></kbd></p>

<br>

<a id="node-bnoyls2"></a>

##### N.n

<br>

<a id="node-xnmuxv6"></a>

- **Foward Prop**

<br>

<a id="node-yrlvj3b"></a>

<p align="center"><kbd><img src="assets/mvr9kjqwtx.png" width="80%"></kbd></p>

<br>

<a id="node-qh3qs1y"></a>

<p align="center"><kbd><img src="assets/lnp2wpzrjx.png" width="80%"></kbd></p>

<br>

<a id="node-lvre5xh"></a>

<p align="center"><kbd><img src="assets/9jdhvg4oont.png" width="80%"></kbd></p>

<br>

<a id="node-ve1ouyk"></a>

<p align="center"><kbd><img src="assets/ww6qscnc9y.png" width="80%"></kbd></p>

<br>

<a id="node-nmqim59"></a>

<p align="center"><kbd><img src="assets/pui93dp1i0l.png" width="80%"></kbd></p>

<br>

<a id="node-3cnj4ta"></a>

- **Backward Prop**

<br>

<a id="node-17bwxq5"></a>

<p align="center"><kbd><img src="assets/quadojxm8z.png" width="80%"></kbd></p>

<br>

<a id="node-5iz795d"></a>

<p align="center"><kbd><img src="assets/nene8o59uao.png" width="80%"></kbd></p>

<br>

<a id="node-7gxk9wz"></a>

<p align="center"><kbd><img src="assets/flvzmfur1yt.png" width="80%"></kbd></p>

<br>

<a id="node-1sh3lu5"></a>

<p align="center"><kbd><img src="assets/7d4bs3ffy2m.png" width="80%"></kbd></p>

<br>

<a id="node-02mkus5"></a>

<p align="center"><kbd><img src="assets/gz8fh817jeu.png" width="80%"></kbd></p>

<br>

<a id="node-5gpdcz8"></a>

### Ian Goodfellow

<br>

<a id="node-abl6wge"></a>

<p align="center"><kbd><img src="assets/oyr6003cv7e.png" width="80%"></kbd></p>

> [!NOTE]
> I think one thing that I got from your courses at Stanford is that linear
> algebra and probability are very important, that people get excited about
> the machine learning algorithms, but if you want to be a really excellent
> practitioner, you've got to master the basic math that underlies the whole
> approach in the first place.
>
> I think a lot of people that want to get into AI start thinking that they absolutely need
> to get a Ph.D. or some other kind of credential like that. I don't think that's actually a
> requirement anymore. One way that you could get a lot of attention is to write good
> code and put it on GitHub. If you have an interesting project that solves a problem
> that someone working at the top level wanted to solve, once they find your GitHub
> repository, they'll come find you and ask you to come work there. A lot of the people
> that I've hired or recruited at OpenAI last year or at Google this year, I first became
> interested in working with them because of something that I saw that they released
> in an open-source forum on the Internet
>
> So read your book, practice the materials and post on GitHub and
> maybe on Archive. I think if you learned by reading the book, it's
> really important to also work on a project at the same time, to either
> choose some way of applying machine learning to an area that you
> are already interested in
>
> ML Security
>
> Like if you're a field biologist and you want to get into deep learning,
> maybe you could use it to identify birds, or if you don't have an idea for
> how you'd like to use machine learning in your own life, you could pick
> something like making a Street View house numbers classifier, where all
> the data sets are set up to make it very straightforward for you. And that
> way, you get to exercise all of the basic skills while you read the book or
> while you watch Coursera videos that explain the concepts to you

<br>

<a id="node-1jjh0q4"></a>

## C1w4_deep Neural Network

<br>

<a id="node-7e7of70"></a>

### Deep L-layer Neural Network

<br>

<a id="node-c1rzin3"></a>

#### 1 By the fourth week of the course, students have learned about forward propagation and
back propagation in the context of a neural network, as well as logistic regression,
vectorization, and the importance of random weight initialization.

2 With this foundational knowledge, the focus of the fourth week is on putting these ideas
together to implement a deep neural network.

3 A deep neural network is a neural network with multiple hidden layers, as opposed to a
shallow model like logistic regression, which is a one-layer neural network.  4 The number
of hidden layers in a neural network is a matter of degree and can vary depending on the
problem at hand. While there is no easy way to predict the ideal depth for a network, it is
common to try different values and evaluate their performance on a development set or
across validation data.

5 Notation is used to describe the architecture and activations of deep neural networks.
Specifically, L denotes the number of layers, and N superscript [l] denotes the number of
nodes in layer l. a[l] denotes the activations in layer l, and W[l] and b[l] are used to
compute the value of z[l] in layer l.

6 x represents the input features, as well as the activations of layer zero, while a[L]
represents the predicted output or y-hat of the neural network.

7 The course website provides a notation sheet or guide that students can refer to if they
forget what a particular symbol or term means.

8 In the next video, the course will go into more detail about what forward propagation
looks like in a deep neural network.

<br>

<a id="node-bvrkelo"></a>

<p align="center"><kbd><img src="assets/dq6xbxdwenn.png" width="80%"></kbd></p>

<br>

<a id="node-9dxckzg"></a>

### Forward Propagation In Deep Network

<br>

<a id="node-tgu5hd8"></a>

#### 1 The video discusses the process of forward propagation in a deep L-layer neural
network using a single training example, followed by the vectorized version, where
forward propagation is carried out on the entire training set.

2 The activations for layer one are computed using the formula z1 = w1*x + b1 and a1
= g(z1), where w1 and b1 are the parameters affecting the activations in layer one and
g is the activation function for layer one.

3 The activations for subsequent layers are computed in a similar way, using the
activation values from the previous layer, until the activations for the final layer, layer L,
are computed, giving the estimated output y hat.

4 The forward propagation equation for a single training example is generalized as zl =
wl*a(l-1) + bl, where a0 = x and a(l-1) is the activation value from the previous layer.

5 The vectorized version of forward propagation involves stacking the vectors z and a
for all training examples and carrying out the same computations using matrix
multiplication.

6 The video recommends using a for loop to compute activations for all layers in a deep
neural network, as it is difficult to implement it without one.

7 Understanding matrix dimensions is crucial when implementing a deep neural
network to minimize bugs and ensure correct implementation.

<br>

<a id="node-otz5p95"></a>

<p align="center"><kbd><img src="assets/pnlh4dq72ff.png" width="80%"></kbd></p>

> [!NOTE]
> Vẫn phải for loop cho các l = 1-L. Không có cách nào khác.

<br>

<a id="node-8mpnz7p"></a>

### Getting Your Matrix Dimension Rights

<br>

<a id="node-atbx1c6"></a>

#### 1 One debugging tool to check the correctness of deep neural network implementation
is to work through the dimensions of the matrices involved.

2 The dimensions of the weight matrix, W, is determined by the number of hidden units
in the current and previous layer. The dimensions of the bias vector, B, is equal to the
number of hidden units in the current layer.

3 The activation vector, Z, for each layer is a vector of dimension equal to the number of
hidden units in that layer.

4 For input features, x, and activation vector, Z, to have the same dimension, the weight
matrix, W, must have dimensions equal to the number of hidden units in the current
layer by the number of features or hidden units in the previous layer.

5 In vectorized implementation, the dimensions of Z and X will change, but the
dimensions of W and B will remain the same.

6 The dimensions of dw and db, the gradients of the weight and bias, respectively,
should be the same as the dimensions of W and B.

<br>

<a id="node-25fr35n"></a>

<p align="center"><kbd><img src="assets/osyjxno72xf.png" width="80%"></kbd></p>

<br>

<a id="node-6jkwc2k"></a>

<p align="center"><kbd><img src="assets/jhbyi2d4ob.png" width="80%"></kbd></p>

<br>

<a id="node-n531hut"></a>

### Why Deep Representations?

<br>

<a id="node-jv1973l"></a>

#### 1 Deep neural networks are effective for many problems and require a lot of
hidden layers.

2 The first layer of a neural network is typically a feature detector or edge
detector for images.

3 The neural network looks for simple things like edges and then composes
them in later layers to learn more complex functions.

4 This simple-to-complex hierarchical representation applies to other types of
data like speech recognition.

5 Deep neural networks can detect surprisingly complex things, like faces or
phrases, despite computing seemingly simple functions.

6 The circuit theory suggests that deep neural networks can compute more
functions than shallow networks.

7 Deep learning draws loose inspiration from the way the human brain detects
simple things and builds them up into more complex objects.

<br>

<a id="node-62jlc5v"></a>

<p align="center"><kbd><img src="assets/kefnmi0mx5a.png" width="80%"></kbd></p>

<br>

<a id="node-k0c6u3s"></a>

<p align="center"><kbd><img src="assets/9gmsszcs4hc.png" width="80%"></kbd></p>

> [!NOTE]
> Có nghĩa là với 1 simple L-layer network thì shallower network
> phải có số hidden unit gấp nhiều lần theo cấp luỹ thừa thì mới
> sánh bằng

<br>

<a id="node-twcs4qe"></a>

### Building Blocks Of Deep Neural Networks

<br>

<a id="node-mtul986"></a>

#### 1 Deep neural networks can be built by putting together the building blocks of
forward propagation and backpropagation.

2 Each layer has parameters (weights and biases) that are used in the forward
propagation step to compute activations of that layer and in the backward
propagation step to compute derivatives with respect to the parameters and
activations of the previous layer.

3 Forward propagation involves feeding input features through the network
and computing activations for each layer using its parameters and activations
from the previous layer. These activations are cached for later use in the
backward propagation step.

4 Backward propagation involves computing derivatives with respect to the
parameters and activations of each layer, starting from the output layer and
going backwards to the input layer. These derivatives are used to update the
parameters of the network in order to minimize a cost function.

5 Each iteration of training through a neural network involves one forward
propagation step followed by one backward propagation step.

<br>

<a id="node-lnjkt9a"></a>

<p align="center"><kbd><img src="assets/qqg9uwarxwf.png" width="80%"></kbd></p>

<br>

<a id="node-lq03d0u"></a>

<p align="center"><kbd><img src="assets/xi4lgq8kdr.png" width="80%"></kbd></p>

<br>

<a id="node-ljwg244"></a>

### Forward And Backward Propagation

<br>

<a id="node-awsmpuh"></a>

#### 1 Recap of the basic building blocks of implementing a deep neural network:
forward propagation and backward propagation.

2 Forward propagation involves inputting a^l-1 and outputting a^l and the cache,
z^l. The activation function is applied to z^l, and if a vectorized implementation is
used, b is Python broadcasting and a^l is g applied element-wise to z.

3 The forward function is initialized with a^0, which is the input features for one
training example or the input features for the entire training set.

4 Backward propagation involves inputting da^l and outputting da^l-1, dw^l, and
db^l.

5 The equations for computing these derivatives are dz^l = da^l * g^l prime(z^l),
dw^l = dz^l * a^l-1, db^l = dz^l, and da^l-1 = w^l transpose * dz^l.

6 A vectorized implementation of the backward function involves dz^l = da^l * g^l
prime(z^l), dw^l = 1/m * dz^l * a^l-1 transpose, db^l = 1/m * np.sum(dz^l, axis=1,
keepdims=True), and da^l-1 = w^l transpose * dz^l.

7 The output y-hat is used to compute the loss, which allows for backward
iteration to compute the derivatives.

8 The backward recursion is initialized with da^l, which is equal to y/a + (1-y)/(1-a)
for binary classification.

9 To implement forward propagation and backward propagation for a three-layer
neural network, the input data x is initialized for the forward recursion and da^2
and da^1 are passed backwards for the backward recursion.

<br>

<a id="node-6koeuqs"></a>

<p align="center"><kbd><img src="assets/qn75axmup.png" width="80%"></kbd></p>

<br>

<a id="node-gt1r79n"></a>

<p align="center"><kbd><img src="assets/tihvzsp8hz.png" width="80%"></kbd></p>

<br>

<a id="node-r1k2hge"></a>

<p align="center"><kbd><img src="assets/jvp2eoo0au.png" width="80%"></kbd></p>

<br>

<a id="node-cv28fh9"></a>

<p align="center"><kbd><img src="assets/pk2xhkogd1.png" width="80%"></kbd></p>

> [!NOTE]
> Although I have to say, even today when I implement
> a learning algorithm, sometimes even I'm surprised
> when my learning algorithm implementation works
> and it's because a lot of the complexity of machine
> learning comes from the data rather than from the
> lines of codes. Sometimes you feel like you
> implement a few lines of code, not quite sure what it
> did, but it almost magically works, and it's because a
> lot of magic is actually not in the piece of code you
> write which is often not too long

<br>

<a id="node-kgzbd60"></a>

### Parameters Vs Hyperparams

<br>

<a id="node-icshi21"></a>

#### 1 Developing deep Neural Nets requires organizing not only parameters, but
also hyper parameters.

2 Hyper parameters include the learning rate alpha, number of iterations,
number of hidden layers, number of hidden units, activation function,
momentum term, mini-batch size, and regularization parameters.

3 Hyper parameters control the ultimate parameters W and B.

4 Deep learning is an intricate process that involves trying out different hyper
parameter settings.

5 Applying deep learning is an empirical process that involves trying out many
different values and seeing what works.

6 There are systematic ways to try out a range of values for hyper parameters.

7 The best value for hyper parameters might change over time, even if working
on the same problem.

<br>

<a id="node-ftyis5q"></a>

<p align="center"><kbd><img src="assets/7cq0fdy6pq6.png" width="80%"></kbd></p>

<br>

<a id="node-wyrp1mw"></a>

<p align="center"><kbd><img src="assets/hn9swjmlt1c.png" width="80%"></kbd></p>

> [!NOTE]
> Empirical process: Đại khái là phải thử nhiều giá trị khác nhau của Hyper params
>
> Different problem different choices for hyper params: 
> Đại khái là khi apply qua 1 vấn đề mới thì nên lặp lại quá trình thử 
> sai để chọn hyper params vì mỗi vấn đề mỗi khác.
>
> Vài tháng check lại: 
> Và dù đã chọn được hyper params tốt rồi thì vài tháng nên check lại
> một lần vì sự thay đổi của CPU, GPU khiến mọi thứ thay đổi theo

<br>

<a id="node-9ehemz1"></a>

### Deep Learning & Brain

<br>

<a id="node-t0hifaj"></a>

#### The article discusses the loose analogy between deep learning and the
human brain. While the structure of a neural network may resemble a
biological neuron, the complexity of a single neuron is far greater than
what is currently understood. There is still much unknown about how the
brain learns and whether it uses similar algorithms to backpropagation
and gradient descent. The author notes that the analogy between deep
learning and the brain may have been useful in the past, but as the field
has progressed, it is breaking down. Finally, the author provides a
summary of the video, which covers how to implement forward and
backpropagation in deep neural networks.

<br>

<a id="node-mpcxv3k"></a>

<p align="center"><kbd><img src="assets/bhpg4fcy4z.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó giông giống neuron thôi chứ hiện giờ ngay cả
> neuroscientist cũng chưa hiểu Neuron nó hoạt động, học như thế
> nào

<br>

<a id="node-8iaevdz"></a>

### Quiz: Key Concepts On Deep Neural Network

<br>

<a id="node-2nv4enx"></a>

<p align="center"><kbd><img src="assets/46eb3bde3ap.png" width="80%"></kbd></p>

<br>

<a id="node-vz4jhhm"></a>

<p align="center"><kbd><img src="assets/0jp4y6lxddhu.png" width="80%"></kbd></p>

<br>

<a id="node-p4j9dab"></a>

<p align="center"><kbd><img src="assets/ebgdo6akzyv.png" width="80%"></kbd></p>

<br>

<a id="node-1yctxyw"></a>

<p align="center"><kbd><img src="assets/yr4fr5qkrpd.png" width="80%"></kbd></p>

> [!NOTE]
> Đánh nhầm

<br>

<a id="node-b3rmhrn"></a>

<p align="center"><kbd><img src="assets/36i18luvxpp.png" width="80%"></kbd></p>

<br>

<a id="node-qbf2hpr"></a>

<p align="center"><kbd><img src="assets/7fi4jwj36mx.png" width="80%"></kbd></p>

<br>

<a id="node-701o94f"></a>

<p align="center"><kbd><img src="assets/9ik09e82lwb.png" width="80%"></kbd></p>

<br>

<a id="node-twgsh5i"></a>

<p align="center"><kbd><img src="assets/qucosfd7atg.png" width="80%"></kbd></p>

<br>

<a id="node-wxauydq"></a>

<p align="center"><kbd><img src="assets/z28scl05dd.png" width="80%"></kbd></p>

<br>

<a id="node-yihkt03"></a>

<p align="center"><kbd><img src="assets/rg97b1acgv8.png" width="80%"></kbd></p>

<br>

<a id="node-vg65kk6"></a>

<p align="center"><kbd><img src="assets/6m69f2bcwsq.png" width="80%"></kbd></p>

<br>

<a id="node-ahu6xpz"></a>

### Programming Assignments: Build Your Deep Neural Network: Step By Step

<br>

<a id="node-rvt5gen"></a>

#### 1 - Packages

<br>

<a id="node-sw1jcb6"></a>

<p align="center"><kbd><img src="assets/ze7dbgqac5.png" width="80%"></kbd></p>

<br>

<a id="node-4jcrzp9"></a>

<p align="center"><kbd><img src="assets/kk5ct32ujp.png" width="80%"></kbd></p>

<br>

<a id="node-x5os2hh"></a>

#### 2 - Outline

<br>

<a id="node-zjyt4ts"></a>

<p align="center"><kbd><img src="assets/peb7a1f34d.png" width="80%"></kbd></p>

<br>

<a id="node-65vxykl"></a>

<p align="center"><kbd><img src="assets/9q2q5sudc4f.png" width="80%"></kbd></p>

<br>

<a id="node-n8i2t2e"></a>

<p align="center"><kbd><img src="assets/cow7km750gs.png" width="80%"></kbd></p>

<br>

<a id="node-pe1snhb"></a>

#### 3 - Initialization

<br>

<a id="node-vle2jpz"></a>

##### 3.1 - 2-layer Neural Network

<br>

<a id="node-4jqbzo7"></a>

<p align="center"><kbd><img src="assets/b2zihqzcgq.png" width="80%"></kbd></p>

<br>

<a id="node-ahae4y1"></a>

<p align="center"><kbd><img src="assets/e7t73foeyg5.png" width="80%"></kbd></p>

<br>

<a id="node-ccvje6v"></a>

<p align="center"><kbd><img src="assets/hkpigdxp3mv.png" width="80%"></kbd></p>

<br>

<a id="node-9q5xva5"></a>

##### 3.2 - L-layer Neural Network

<br>

<a id="node-ghevfju"></a>

<p align="center"><kbd><img src="assets/p28vcf3kx6.png" width="80%"></kbd></p>

<br>

<a id="node-aupwiew"></a>

<p align="center"><kbd><img src="assets/njyzpl7jlhi.png" width="80%"></kbd></p>

<br>

<a id="node-7d07it7"></a>

<p align="center"><kbd><img src="assets/58kjvss8jsg.png" width="80%"></kbd></p>

<br>

<a id="node-yfehm1i"></a>

<p align="center"><kbd><img src="assets/9ncxtqyvwu6.png" width="80%"></kbd></p>

<br>

<a id="node-whyvn2q"></a>

#### 4 - Forward Propagation Module

<br>

<a id="node-3w1h1m8"></a>

##### 4.1 - Linear Forward

<br>

<a id="node-mwh6c2z"></a>

<p align="center"><kbd><img src="assets/jfoftv5u2ss.png" width="80%"></kbd></p>

<br>

<a id="node-8r1htr3"></a>

<p align="center"><kbd><img src="assets/9c7juf7xxnd.png" width="80%"></kbd></p>

<br>

<a id="node-8gbsm2o"></a>

<p align="center"><kbd><img src="assets/cqsa280lc6q.png" width="80%"></kbd></p>

<br>

<a id="node-cp2wyqc"></a>

##### 4.2 - Linear-Activation Forward

<br>

<a id="node-gj1r8gv"></a>

<p align="center"><kbd><img src="assets/imxi7kcyn97.png" width="80%"></kbd></p>

<br>

<a id="node-wz2f2in"></a>

<p align="center"><kbd><img src="assets/pekdhigu8pr.png" width="80%"></kbd></p>

<br>

<a id="node-lfjw09o"></a>

<p align="center"><kbd><img src="assets/ia7pjaj3ltk.png" width="80%"></kbd></p>

<br>

<a id="node-6g8j6rr"></a>

<p align="center"><kbd><img src="assets/ogunz582yib.png" width="80%"></kbd></p>

<br>

<a id="node-kc4rg31"></a>

##### 4.3 - L-Layer Model

<br>

<a id="node-wpktm0b"></a>

<p align="center"><kbd><img src="assets/06qrjq9jf02.png" width="80%"></kbd></p>

<br>

<a id="node-y5uh1n3"></a>

<p align="center"><kbd><img src="assets/tki6l9swbz.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3oq0ezucleu.png" width="80%"></kbd></p>

> [!NOTE]
> for l in range(1, L) -> l = 1,2...L-1

<br>

<a id="node-cdltw23"></a>

<p align="center"><kbd><img src="assets/zkus5manz2d.png" width="80%"></kbd></p>

<br>

<a id="node-m1k86r8"></a>

#### 5 - Cost Function

<br>

<a id="node-vpdi4yh"></a>

<p align="center"><kbd><img src="assets/lez8ntnilrh.png" width="80%"></kbd></p>

<br>

<a id="node-6tsfk8a"></a>

<p align="center"><kbd><img src="assets/i83hiisc4vp.png" width="80%"></kbd></p>

<br>

<a id="node-0mnzvsj"></a>

<p align="center"><kbd><img src="assets/d69ixzt3lu7.png" width="80%"></kbd></p>

<br>

<a id="node-8wcnajf"></a>

#### 6 - Backward Propagation Module

<br>

<a id="node-zeld9x4"></a>

<p align="center"><kbd><img src="assets/9flhvbwyii.png" width="80%"></kbd></p>

<br>

<a id="node-uxp1g7b"></a>

<p align="center"><kbd><img src="assets/g95cdnir2zj.png" width="80%"></kbd></p>

> [!NOTE]
> keepdims = True sẽ ngăn không để Python nó biến kết quả đang matrix 2D
> thành array vector 1D

<br>

<a id="node-pab6yi4"></a>

##### 6.1 - Linear Backward

<br>

<a id="node-2kbb9w1"></a>

<p align="center"><kbd><img src="assets/y3kze58ikd.png" width="80%"></kbd></p>

<br>

<a id="node-u3wldu3"></a>

<p align="center"><kbd><img src="assets/5bfz9myw2mg.png" width="80%"></kbd></p>

<br>

<a id="node-oxlhhka"></a>

<p align="center"><kbd><img src="assets/gq4n6du2jzj.png" width="80%"></kbd></p>

<br>

<a id="node-yfigok2"></a>

##### 6.2 - Linear-Activation Backward

<br>

<a id="node-jvaq04u"></a>

<p align="center"><kbd><img src="assets/jv51bz42r0i.png" width="80%"></kbd></p>

<br>

<a id="node-cm8b6yn"></a>

<p align="center"><kbd><img src="assets/dqawfrlr00f.png" width="80%"></kbd></p>

<br>

<a id="node-ym5omnl"></a>

##### 6.3 - L-Model Backward

<br>

<a id="node-imo4s3r"></a>

<p align="center"><kbd><img src="assets/ptfbqlapj0e.png" width="80%"></kbd></p>

<br>

<a id="node-3qfjr1n"></a>

<p align="center"><kbd><img src="assets/1gyr9lfg2m7.png" width="80%"></kbd></p>

<br>

<a id="node-uze0qdt"></a>

<p align="center"><kbd><img src="assets/mw7c5ctqs5.png" width="80%"></kbd></p>

<br>

<a id="node-hd9n7lx"></a>

<p align="center"><kbd><img src="assets/68o73klbkyc.png" width="80%"></kbd></p>

<br>

<a id="node-xojwl6w"></a>

##### 6.4 - Update Parameters

<br>

<a id="node-dk980rs"></a>

<p align="center"><kbd><img src="assets/lgmkkrfafz.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zwrr0facl6.png" width="80%"></kbd></p>

<br>

<a id="node-m2qywni"></a>

<p align="center"><kbd><img src="assets/rphmxfkye29.png" width="80%"></kbd></p>

<br>

<a id="node-vb3j91v"></a>

<p align="center"><kbd><img src="assets/sxk2e47gi6s.png" width="80%"></kbd></p>

<br>

<a id="node-96zmezq"></a>

#### Tóm Lược Quy
trình Cho Dễ Hiểu

<br>

<a id="node-om0jrlq"></a>

<p align="center"><kbd><img src="assets/ptkp5y8h12.png" width="80%"></kbd></p>

<br>

<a id="node-fgvvdcj"></a>

<p align="center"><kbd><img src="assets/n6qz0i20zc.png" width="80%"></kbd></p>

<br>

<a id="node-csqcb8n"></a>

<p align="center"><kbd><img src="assets/62svx4b9y9k.png" width="80%"></kbd></p>

<br>

<a id="node-p9t747r"></a>

### Programming Assignment: Deep Neural Network - Application

> [!NOTE]
> Build and train a deep L-layer neural network, and apply it to 
> the very important problem of classifying cat images from 
> non-cat images.  :)

<br>

<a id="node-n1v7ebn"></a>

#### 1 - Packages

<br>

<a id="node-448r2jy"></a>

<p align="center"><kbd><img src="assets/arcwna4ikol.png" width="80%"></kbd></p>

<br>

<a id="node-iisuref"></a>

#### 2 - Load and Process the Dataset

<br>

<a id="node-hz3qegb"></a>

<p align="center"><kbd><img src="assets/8nirtukq5ta.png" width="80%"></kbd></p>

<br>

<a id="node-latysue"></a>

<p align="center"><kbd><img src="assets/hqpbjpvpf9n.png" width="80%"></kbd></p>

<br>

<a id="node-eg8dxfc"></a>

<p align="center"><kbd><img src="assets/otxe8tg51o.png" width="80%"></kbd></p>

<br>

<a id="node-bixddsq"></a>

#### 3 - Model Architecture

<br>

<a id="node-cie6a9g"></a>

##### 3.1 - 2-layer Neural Network

<br>

<a id="node-ew9ni9e"></a>

<p align="center"><kbd><img src="assets/z4gp1w7mkg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/77avbuyr4rd.png" width="80%"></kbd></p>

<br>

<a id="node-83e0bmj"></a>

##### 3.2 - L-layer Deep Neural Network

<br>

<a id="node-o9vgjoc"></a>

<p align="center"><kbd><img src="assets/1a1t88e7edb.png" width="80%"></kbd></p>

<br>

<a id="node-5qypk9b"></a>

##### 3.3 - General Methodology

<br>

<a id="node-cat4gyo"></a>

<p align="center"><kbd><img src="assets/k79o2z96qu.png" width="80%"></kbd></p>

<br>

<a id="node-d74ho8r"></a>

#### 4 - Two-layer Neural Network

<br>

<a id="node-8hsa37l"></a>

##### Exercise 1 - two_layer_model

<br>

<a id="node-018l0ia"></a>

<p align="center"><kbd><img src="assets/g8jf3pltuxf.png" width="80%"></kbd></p>

<br>

<a id="node-7k1oaz6"></a>

<p align="center"><kbd><img src="assets/7r2xke3vq6e.png" width="80%"></kbd></p>

<br>

<a id="node-6tsoxcw"></a>

<p align="center"><kbd><img src="assets/q0x31jzevnr.png" width="80%"></kbd></p>

<br>

<a id="node-8t975w5"></a>

<p align="center"><kbd><img src="assets/1tzszhwx321.png" width="80%"></kbd></p>

<br>

<a id="node-voeb7vb"></a>

<p align="center"><kbd><img src="assets/9bl9c5ue03p.png" width="80%"></kbd></p>

<br>

<a id="node-rk7md8p"></a>

##### 4.1 - Train the model

<br>

<a id="node-1si3vfh"></a>

<p align="center"><kbd><img src="assets/4b7xr1bgyln.png" width="80%"></kbd></p>

<br>

<a id="node-5dklz3g"></a>

<p align="center"><kbd><img src="assets/llonodiyn7b.png" width="80%"></kbd></p>

<br>

<a id="node-5qy2soo"></a>

<p align="center"><kbd><img src="assets/ai0z3f6rmj.png" width="80%"></kbd></p>

> [!NOTE]
> Note: You may notice that running the model on fewer iterations (say
> 1500) gives better accuracy on the test set. This is called **"early
> stopping"** and you'll hear more about it in the next course. Early stopping
> is a way to prevent overfitting.

<br>

<a id="node-4pyjkqo"></a>

#### 5 - L-layer Neural Network

<br>

<a id="node-gddfvg6"></a>

##### Exercise 2 - L_layer_model

<br>

<a id="node-itvjc4c"></a>

<p align="center"><kbd><img src="assets/pluompjf4cg.png" width="80%"></kbd></p>

<br>

<a id="node-x61cqjd"></a>

<p align="center"><kbd><img src="assets/fv5ld4ym8lm.png" width="80%"></kbd></p>

<br>

<a id="node-xyiw5ez"></a>

<p align="center"><kbd><img src="assets/samvpnqzcqi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/2w3zzpkgtwx.png" width="80%"></kbd></p>

<br>

<a id="node-48qouc4"></a>

##### 5.1 - Train the model

<br>

<a id="node-fn4ld5a"></a>

<p align="center"><kbd><img src="assets/6h97z5m3rln.png" width="80%"></kbd></p>

<br>

<a id="node-6o5gx5g"></a>

<p align="center"><kbd><img src="assets/m262kswfvc.png" width="80%"></kbd></p>

> [!NOTE]
> In the next course on "Improving deep neural networks," you'll be 
> able to obtain even higher accuracy by systematically 
> **searching for better hyperparameters: learning_rate, 
> layers_dims, or num_iterations, for example.**

<br>

<a id="node-v5mnq0h"></a>

#### 6 - Results Analysis

<br>

<a id="node-83jpyxb"></a>

<p align="center"><kbd><img src="assets/sjz3qcikitk.png" width="80%"></kbd></p>

<br>

<a id="node-sh264sp"></a>

#### 7 - Test with your own image (optional/ungraded exercise)

<br>

<a id="node-ulx70xz"></a>

<p align="center"><kbd><img src="assets/1drak2pissz.png" width="80%"></kbd></p>

<br>

<a id="node-xwmf46m"></a>

<p align="center"><kbd><img src="assets/2wsdmajavt.png" width="80%"></kbd></p>

<br>

<a id="node-n371i4h"></a>

### References

> [!NOTE]
> **Week 2:
>  • GitHub**: \_Implementing a Neural Network from Scratch in Python – An Introduction\_ (Denny Britz, 2015)
>  • \_Why normalize images by subtracting dataset's image mean, instead of the current image mean in deep learning?\_ (Stack Exchange)
> **Week 3:**
>  • \_CS231n: Convolutional Neural Networks for Visual Recognition\_ (Stanford University)
> **Week 4:**
> \_Autoreload of modules in IPython\_ (Stack Overflow)

<br>

