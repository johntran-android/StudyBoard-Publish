# C1w2_n.n Basic

📊 **Progress:** `64` Notes | `163` Screenshots

---
<a id="node-4bqxnuv"></a>

## C1w2_n.n Basic

<br>

<a id="node-xvtzji5"></a>

## Logistic Regression As A Neural Network

<br>

<a id="node-fahjewu"></a>

### Binary Classification

<br>

<a id="node-03jgemd"></a>

> [!NOTE]
> 1 The basics of neural network programming include techniques that are
> important to process the entire training set.
>
> 2 The computation of a neural network is organized in forward propagation and
> backward propagation.
>
> 3 Logistic regression is an algorithm for binary classification that is going to be
> used to convey the ideas.
>
> 4 To turn pixel intensity values into a feature vector, they are unrolled to get a
> long feature vector that lists all the red, green and blue pixel intensity values of
> the image.
>
> 5 Binary classification aims to learn a classifier that can input an image
> represented by a feature vector x and predict whether the corresponding label y
> is 1 or 0.
>
> 6 Notations used in the course include lowercase m to denote the number of
> training samples, M_train, to emphasize that this is the number of training
> examples, and m_subscript_test to denote the number of test examples.
>
> 7 A matrix X is defined by taking the training set inputs x1, x2, and so on, and
> stacking them in columns.

<br>

<a id="node-tjnjat5"></a>

<p align="center"><kbd><img src="assets/oh7wdqzbgj.png" width="80%"></kbd></p>

<br>

<a id="node-1cgnt7n"></a>

<p align="center"><kbd><img src="assets/9mzefeya3kd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:..
>
>
>
> Thường thì define X dạng mxn, nhưng đối với n.n thì define nm 
> sẽ dễ làm hơn. Y cũng vậy.

<br>

<a id="node-lfgorxw"></a>

### Logistic Regression

<br>

<a id="node-g5qgic1"></a>

> [!NOTE]
> 1 Logistic regression is a learning algorithm used for binary classification problems
> where the output labels Y are either zero or one.
>
> 2 Given an input feature vector X, the goal of logistic regression is to output a
> prediction Y hat, which is the probability that Y is equal to one given X.
>
> 3 The parameters of logistic regression are W, which is an X-dimensional vector,
> and b, which is a real number.
>
> 4 The initial idea of using Y hat as a linear function of the input X, Y hat = w
> transpose X + b, is not effective for binary classification because it does not
> guarantee that Y hat will be between zero and one.
>
> 5 Instead, logistic regression uses the sigmoid function to ensure that Y hat is
> between zero and one.
>
> 6 The sigmoid function maps any real number Z to a value between zero and one,
> with values close to one for large positive Z, and values close to zero for large
> negative Z.
>
> 7 The formula for the sigmoid function is sigmoid of Z = 1 / (1 + e^(-Z)).
>
> 8 The parameters W and B of logistic regression are learned by defining a cost
> function, which will be explained in the next video.
>
> 9 There is an alternative notation for logistic regression that uses an extra feature
> called X0, but in this course, W and B are kept separate.

<br>

<a id="node-6vnfqzm"></a>

<p align="center"><kbd><img src="assets/sdh8hlkfoz.png" width="80%"></kbd></p>

<br>

<a id="node-wixvpwa"></a>

<p align="center"><kbd><img src="assets/q48hc3yikx.png" width="80%"></kbd></p>

<br>

<a id="node-gkb5gdr"></a>

### Logistic Regression Cost Function

<br>

<a id="node-5gzb8jx"></a>

> [!NOTE]
> 1 Logistic regression model to train parameters W and B for given training
> examples.
>
> 2 Definition of the cost function to measure how well the algorithm is
> performing on the training set.
>
> 3 Convention of superscript parentheses I to index different training
> examples.
>
> 4 Use of a different loss function in logistic regression, which is negative y
> log y hat plus 1 minus y log 1 minus y hat.
>
> 5 Justification of the loss function, where it tries to make y hat large if y is
> equal to one and small if y is equal to zero.

<br>

<a id="node-vz5yenp"></a>

<p align="center"><kbd><img src="assets/ebqf00kgccn.png" width="80%"></kbd></p>

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

<a id="node-gq1huno"></a>

<p align="center"><kbd><img src="assets/4q6zz3mtzjd.png" width="80%"></kbd></p>

<br>

<a id="node-5haak74"></a>

### Gradient Descent

<br>

<a id="node-tz3q6m7"></a>

> [!NOTE]
> 1 Recap of logistic regression and its loss and cost functions.
>
> 2 Discussion of the convexity of the cost function and why it's
> important for logistic regression.
>
> 3 Explanation of gradient descent as an optimization algorithm to find
> the best parameters for the cost function.
>
> 4 Description of how gradient descent updates the values of the
> parameters to approach the minimum of the cost function.
>
> 5 Explanation of the role of the learning rate in controlling the size of
> steps in the gradient descent algorithm.

<br>

<a id="node-nwaj1v6"></a>

<p align="center"><kbd><img src="assets/gtz3b7r2w8.png" width="80%"></kbd></p>

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

<a id="node-vpvq6a7"></a>

<p align="center"><kbd><img src="assets/jmmejjva7es.png" width="80%"></kbd></p>

<br>

<a id="node-0kvh5g9"></a>

<p align="center"><kbd><img src="assets/qhk8n7g42l.png" width="80%"></kbd></p>

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

<a id="node-v2fe22f"></a>

<p align="center"><kbd><img src="assets/2ms14iago5c.png" width="80%"></kbd></p>

<br>

<a id="node-1kwg74m"></a>

### Derivatives

<br>

<a id="node-66vvr82"></a>

> [!NOTE]
> 1 The video aims to help people gain an intuitive understanding of calculus and
> derivatives.
>
> 2 Even if someone does not have a deep understanding of calculus, they can still
> apply deep learning.
>
> 3 Forward and backward functions will encapsulate everything one needs to know
> about calculus for deep learning.
>
> 4 Calculus is important for deep learning, but intuitive understanding is enough to
> build and apply algorithms.
>
> 5 The video will explore the details of derivatives, but for experts in calculus, this
> video may be skipped.
>
> 6 The video explains the concept of derivatives by plotting a straight line and
> exploring how the slope changes.
>
> 7 The slope of a line represents the derivative, which is the rate of change of the
> function.
>
> 8 The slope or derivative is defined as the height divided by the width of a small
> triangle.
>
> 9 When the slope is equal to three, it means that if you nudge a variable a to the right,
> f(a) goes up three times as much as you nudged the value of a.

<br>

<a id="node-9ct3v36"></a>

<p align="center"><kbd><img src="assets/a6tyzc422vg.png" width="80%"></kbd></p>

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

<a id="node-s5tjamb"></a>

<p align="center"><kbd><img src="assets/fo2pdfuzbta.png" width="80%"></kbd></p>

<br>

<a id="node-993qdyi"></a>

### More Derivative Examples

<br>

<a id="node-4ay4gv4"></a>

> [!NOTE]
> 1 The video demonstrates a slightly more complex example where the slope of the
> function varies at different points in the function.
>
> 2 The function used as an example is f(a) = a².
>
> 3 The video shows that the slope of the function at a given point can be determined by
> nudging a slightly to the right and observing the change in f(a).
>
> 4 The video explains that the ratio of the height of the triangle over the width of the
> triangle is different at different points on the curve, which is why the derivative is
> different at different points.
>
> 5 The video shows that if you pull up a calculus textbook, you'll find that the slope of
> the function a² is equal to 2a.
>
> 6 The video demonstrates that the derivative of f(a) = a² is equal to 4 when a = 2 and
> 10 when a = 5.
>
> 7 The video explains that the derivative is defined using infinitesimally small nudges to
> a, which is why the amount that f(a) goes up isn't exactly given by the formula but is
> only approximately given by the derivative.

<br>

<a id="node-7ajhews"></a>

<p align="center"><kbd><img src="assets/mj1e75qr5vs.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu trong sách Calculus ta thấy công thức tính 
> d_f(a)/d_a = **2a** với f = a^2 thì có nghĩa là : 
>
>
>
> Nếu kéo a lên một khoảng tiny ví dụ 0,001 thì 
> hàm f = a^2 sẽ tăng lên 1 khoảng /**gấp 2a lần**/ = 2a*0.001

<br>

<a id="node-p51dc8a"></a>

<p align="center"><kbd><img src="assets/4q6tnd7ugf2.png" width="80%"></kbd></p>

<br>

<a id="node-r3n3ocw"></a>

<p align="center"><kbd><img src="assets/t3nttujaihp.png" width="80%"></kbd></p>

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

<a id="node-g66a0j5"></a>

### Computation Graph

<br>

<a id="node-em3gs7s"></a>

> [!NOTE]
> 1 Introduction: Explanation of forward pass and backward pass in neural networks
> using computation graph.
>
> 2 Example problem: Computing a function J of three variables a, b, and c, which is J =
> 3(a + bc).
>
> 3 Steps to compute J:
>
> 4 a. Compute u = bc.  5 b. Compute V = a * u.  6 c. Compute J = 3V.
>
> 7 Computation graph: Visual representation of the three steps with a, b, and c as
> inputs, and u, V, and J as the intermediate and final outputs, respectively.
>
> 8 Example calculation: Values of a, b, and c are given as 5, 3, and 2, respectively. The
> values of u, V, and J are computed as 6, 30, and 33, respectively, using the
> computation graph.
>
> 9 Importance of computation graph: Useful for optimizing a special output variable,
> such as J, in neural networks.
>
> 10 Left-to-right computation: The computation graph enables a left-to-right pass for
> computing the value of J.
>
> 11 Right-to-left computation: In order to compute derivatives, a right-to-left pass is
> needed, which is explained in the next video.

<br>

<a id="node-5une8vw"></a>

<p align="center"><kbd><img src="assets/rafz1xd0u4r.png" width="80%"></kbd></p>

> [!NOTE]
> Nền tảng đằng sau tên gọi khái niệm của 'Forward propagation' đại khái là
> để tính value (ví dụ của cost function J) thì tính từ trái qua phải. Còn tính
> derivative thì ngược lại (Back propagation)

<br>

<a id="node-4h0jkue"></a>

### Derivatives With A Computation Graph

<br>

<a id="node-ahsufcy"></a>

> [!NOTE]
> 1 Introduction: The video discusses how to use a computation graph to figure out derivative
> calculations for a function J by taking a cleaned-up version of the computation graph used in the
> previous video.
>
> 2 Derivative of J with respect to v: The video demonstrates how to compute the derivative of J
> with respect to v, which is equal to 3, by increasing the value of v by 0.001, using the analogy of
> the previous video where f(a) = 3a and df/da = 3.
>
> 3 Derivative of J with respect to a: The video illustrates how to calculate dJ/da, which is also
> equal to 3, by changing the value of a by 0.001 and breaking it down to the chain rule, where
> dv/da = 1 and dJ/dv = 3, which when multiplied give dJ/da = 3.
>
> 4 Backward calculation: The video shows how computing dJ/dv can help in calculating dJ/da and
> how it's a backward calculation to find the derivatives of the variables that come before J.
>
> 5 Notational Convention: The video introduces a new notational convention, which is to call the
> final output variable, J in this case, as "dvar" while computing the derivative of the final output
> variable with respect to intermediate variables.

<br>

<a id="node-idmgeh5"></a>

<p align="center"><kbd><img src="assets/yi37cqe01o.png" width="80%"></kbd></p>

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

<a id="node-bl1rldd"></a>

<p align="center"><kbd><img src="assets/3p91mzkz2og.png" width="80%"></kbd></p>

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

<a id="node-9104ke6"></a>

<p align="center"><kbd><img src="assets/cmbgi0pgvk.png" width="80%"></kbd></p>

<br>

<a id="node-0t5u5h0"></a>

### Logistic Regression Gradient Descent

<br>

<a id="node-9pp20sn"></a>

> [!NOTE]
> Main ideas:  1 Introduction to computing derivatives for implementing
> gradient descent for logistic regression.
>
> 2 Explanation of the key equations necessary to implement gradient
> descent for logistic regression using computation graphs.
>
> 3 Forward propagation steps of computing loss on a single training
> example.
>
> 4 Backward propagation steps to compute the derivatives of the loss
> with respect to each variable.
>
> 5 Explanation of the derivative of the loss with respect to A and how it is
> computed.
>
> 6 Deriving the derivative of the loss with respect to Z using the chain
> rule.
>
> 7 Computation of how much W and B need to be changed.
>
> 8 Explanation of how to update W1, W2, and B to perform one step of
> gradient descent with respect to a single example.

<br>

<a id="node-mip1hfi"></a>

<p align="center"><kbd><img src="assets/3ratsttk6py.png" width="80%"></kbd></p>

<br>

<a id="node-sswlvmf"></a>

<p align="center"><kbd><img src="assets/tqapf092cv.png" width="80%"></kbd></p>

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

<a id="node-8tog1mg"></a>

<p align="center"><kbd><img src="assets/ob1atwplawn.png" width="80%"></kbd></p>

> [!NOTE]
> D/**ùng Gradient Descent update w,
> b sao cho minimize J**/.

<br>

<a id="node-fjnrqlz"></a>

<p align="center"><kbd><img src="assets/bwyw3dspsc7.png" width="80%"></kbd></p>

<br>

<a id="node-w2w5eu1"></a>

### Gradient Descent On M Examples

<br>

<a id="node-me7c8is"></a>

> [!NOTE]
> 1 Reminder of the definition of the cost function J.
>
> 2 Explanation of how to compute derivatives for the cost function J with
> respect to each parameter w and b for m training examples.
>
> 3 Derivatives with respect to each parameter are computed as the
> average of derivatives with respect to each parameter for the individual
> loss terms.
>
> 4 An algorithm is presented that computes the derivatives of the cost
> function J with respect to each parameter w and b.
>
> 5 Details of the algorithm are presented, including initialization, for loop
> over training set, calculations for the accumulator values, division by m to
> compute the averages, and updating of parameter values.
>
> 6 Two weaknesses with the algorithm are noted: two for loops are
> needed to implement logistic regression and it assumes that the number
> of features is known.

<br>

<a id="node-gs7gq26"></a>

<p align="center"><kbd><img src="assets/3pyuk4nzxke.png" width="80%"></kbd></p>

> [!NOTE]
> Derivative of J w.r.t w, b trên toàn bộ m dataset X, y - dJ_dw, dJ_db
> Tính bằng cách lấy trung bình của tất cả
> Derivative of J w.r.t w, b trên từng dataset x(i), y(i) - dJ_dw(i), dJ_db(i)

<br>

<a id="node-yfct65k"></a>

<p align="center"><kbd><img src="assets/zbi0f6qsg7.png" width="80%"></kbd></p>

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

<a id="node-oua83ih"></a>

<p align="center"><kbd><img src="assets/4p8ffjlp9pd.png" width="80%"></kbd></p>

<br>

<a id="node-e56xb35"></a>

### DERIVATION OF dL/dz

<br>

<a id="node-6stxslb"></a>

#### ...

<br>

<a id="node-w6f9ryw"></a>

<p align="center"><kbd><img src="assets/f98m8moctgq.png" width="80%"></kbd></p>

<br>

<a id="node-uhu8r2c"></a>

<p align="center"><kbd><img src="assets/e3ve1962xtf.png" width="80%"></kbd></p>

<br>

<a id="node-bqpodz3"></a>

<p align="center"><kbd><img src="assets/pjsz6cayth.png" width="80%"></kbd></p>

<br>

<a id="node-i3e3jcc"></a>

<p align="center"><kbd><img src="assets/xk8dj9dtbio.png" width="80%"></kbd></p>

<br>

<a id="node-s58umsc"></a>

<p align="center"><kbd><img src="assets/xrsrz9ehz8d.png" width="80%"></kbd></p>

<br>

<a id="node-vpcy4n2"></a>

## Python And Vectorization

<br>

<a id="node-dkl7hja"></a>

### Vectorization

<br>

<a id="node-e2g49oo"></a>

> [!NOTE]
> 1 The course teaches strategies for structuring a machine learning
> project to improve efficiency and quickly get systems working.
>
> 2 The example given is of improving a cat classification system with
> 90% accuracy.
>
> 3 There are many ideas to try to improve a deep learning system, but
> choosing the wrong approach can waste time.
>
> 4 The course teaches strategies for analyzing a machine learning
> problem to identify the most promising ideas to pursue.
>
> 5 The instructor will share lessons learned from building and
> shipping deep learning products.
>
> 6 The strategies taught in the course are unique and not commonly
> taught in university deep learning courses.
>
> 7 Machine learning strategy has changed with the emergence of
> deep learning algorithms.
>
> 8 The course aims to make learners more effective at getting deep
> learning systems to work.

<br>

<a id="node-gwvioen"></a>

<p align="center"><kbd><img src="assets/5iu62dd6h19.png" width="80%"></kbd></p>

<br>

<a id="node-8t3pt74"></a>

<p align="center"><kbd><img src="assets/fcgzuum2p8e.png" width="80%"></kbd></p>

> [!NOTE]
> 2499719.1349626444
> Vectorization: 8.999824523925781ms
> 2499719.1349626444
> Non-Vectorization: 7566.00022315979ms
> Vectorization is /**840**/.6830825474198 times faster than non-vectorization
> If some trainning task take **1 hour** to finish with vectorization, 
> it will need **35 days** to finish

<br>

<a id="node-x8v9j3f"></a>

<p align="center"><kbd><img src="assets/g8opu7yigr.png" width="80%"></kbd></p>

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

<a id="node-3bywtyy"></a>

<p align="center"><kbd><img src="assets/wy05ra8impg.png" width="80%"></kbd></p>

<br>

<a id="node-bm9mtku"></a>

### Vectorization More Example

<br>

<a id="node-0irxjte"></a>

> [!NOTE]
> 1 Rule of thumb: avoid explicit for-loops whenever possible to speed up
> code.
>
> 2 Example 1: Vector multiplication using matrix A and vector v -
> non-vectorized implementation using two for-loops, vectorized
> implementation using np dot (A,v).
>
> 3 Example 2: Exponential operation on every element of vector v -
> non-vectorized implementation using a for-loop, vectorized
> implementation using np.exp(v).
>
> 4 NumPy built-in functions for element-wise operations.
>
> 5 Applying vectorization to logistic regression gradient descent
> implementation to eliminate one of the two for-loops.
>
> 6 Eliminating the need for a for-loop over training examples in logistic
> regression with further vectorization.
>
> 7 Vectorization can significantly speed up code.

<br>

<a id="node-jthoxtn"></a>

<p align="center"><kbd><img src="assets/yow9oav4n5p.png" width="80%"></kbd></p>

<br>

<a id="node-2ve1t59"></a>

<p align="center"><kbd><img src="assets/k4wwf2fkj1p.png" width="80%"></kbd></p>

<br>

<a id="node-j0o8ycl"></a>

<p align="center"><kbd><img src="assets/la826mcb7i.png" width="80%"></kbd></p>

<br>

<a id="node-1h941ur"></a>

### Vectorizing Logstic Regression

<br>

<a id="node-acqlaeh"></a>

> [!NOTE]
> Main ideas:  1 The video explains how to vectorize the implementation of
> logistic regression and process the entire training set without using explicit for
> loops.
>
> 2 The four propagation steps of logistic regression are explained with an
> example of making a prediction on M training examples.
>
> 3 The matrix X is defined as the training inputs, stacked together in different
> columns, and a matrix Z is defined to compute all the values of Z1, Z2,...,ZM in
> one step.
>
> 4 The values A1, A2,...,AM are computed using a vectorized sigmoid function
> that takes the matrix Z as input.
>
> 5 Stacking lowercase A results in a new variable, capital A.
>
> 6 The video concludes that instead of looping over M training examples to
> compute Z and A, you can use the one-line code to compute all Z and A at the
> same time.

<br>

<a id="node-u6tnjhb"></a>

<p align="center"><kbd><img src="assets/3zgnuuogqkj.png" width="80%"></kbd></p>

<br>

<a id="node-abn6tv3"></a>

<p align="center"><kbd><img src="assets/nmjx1di01xf.png" width="80%"></kbd></p>

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

<a id="node-y569u7t"></a>

<p align="center"><kbd><img src="assets/kd0lj3hn2ba.png" width="80%"></kbd></p>

<br>

<a id="node-lmcr4x9"></a>

### Vectorizng Logistic Regression' S Gradient Computation

<br>

<a id="node-9lmqfpb"></a>

> [!NOTE]
> Main ideas:  1 The previous video demonstrated how vectorization could be used to compute the
> predictions for an entire training set simultaneously.
>
> 2 This video shows how to use vectorization for gradient computation for all M training samples.
>
> 3 The new variable dZ is defined as dz1, dz2, ..., dzm, which is a 1 by m matrix or an m
> dimensional row vector.
>
> 4 dz can be computed as A - Y where A and Y are defined as a1 through am and y1 through ym,
> respectively.
>
> 5 Vectorization can be used to implement the derivative calculations efficiently.
>
> 6 The vectorized implementation of db is one over m times np.sum of dz, while the vectorized
> implementation of dw is one over m times the matrix X times dz transpose.
>
> 7 The previous implementation of logistic regression was highly inefficient and required loops
> over dw1, dw2, etc.
>
> 8 The new implementation uses vectorization to replace the loops, making it more efficient.
>
> 9 The updated code involves computing capital Z as w transpose X + B, then calculating a as
> sigmoid of capital Z, dz as A - Y, dw as 1/m x dz transpose, and db as 1/m times np.sum of dz.
>
> 10 The vectorized implementation allows for the computation of updates to the parameters
> without a for loop over the training set.

<br>

<a id="node-mmg6j8b"></a>

<p align="center"><kbd><img src="assets/vejacjvprb.png" width="80%"></kbd></p>

> [!NOTE]
> QUAN TRỌNG

<br>

<a id="node-9ztaz5o"></a>

<p align="center"><kbd><img src="assets/5lqjvcxyqqx.png" width="80%"></kbd></p>

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

<a id="node-0ovzdar"></a>

<p align="center"><kbd><img src="assets/ntkuscxd95.png" width="80%"></kbd></p>

<br>

<a id="node-m91jnph"></a>

### Broadcasting In Python

<br>

<a id="node-luu3zc7"></a>

> [!NOTE]
> 1 Broadcasting is a technique to make Python code run faster.
>
> 2 Broadcasting allows performing operations between arrays with different shapes.
>
> 3 In the video, broadcasting is explained using an example of calculating the
> percentage of calories from carbs, proteins, and fats in 100 grams of four different
> foods.
>
> 4 Broadcasting can be used to sum down columns of a matrix and divide each
> column by their corresponding sum without using an explicit for-loop.
>
> 5 The video demonstrates how to sum vertically using axis 0, which sums down the
> columns, and how to reshape a matrix.
>
> 6 The reshape command is a constant time operation and can be used to ensure
> that matrices have the correct size.
>
> 7 The video explains how broadcasting works, and provides examples of adding a 4
> by 1 vector to a number and multiplying a 4 by 3 matrix by a 1 by 3 matrix.

<br>

<a id="node-g310029"></a>

<p align="center"><kbd><img src="assets/9k4a5yccp77.png" width="80%"></kbd></p>

<br>

<a id="node-1is98tl"></a>

<p align="center"><kbd><img src="assets/djcz7nfjvv6.png" width="80%"></kbd></p>

> [!NOTE]
> A.sum(axis = 0) => Sum vertically

<br>

<a id="node-hq62rc0"></a>

<p align="center"><kbd><img src="assets/vkkrd0krkf7.png" width="80%"></kbd></p>

<br>

<a id="node-n5mzd7q"></a>

<p align="center"><kbd><img src="assets/873slxaf3dh.png" width="80%"></kbd></p>

> [!NOTE]
> 'Cal' vốn dĩ đã là 1x4 rồi nhưng ổng
> nói thêm lệnh reshape cho  chắc ăn
> không sao cả.

<br>

<a id="node-7xuq02z"></a>

<p align="center"><kbd><img src="assets/73cqktmx26c.png" width="80%"></kbd></p>

<br>

<a id="node-i8ffzlb"></a>

<p align="center"><kbd><img src="assets/9x94dkh3rld.png" width="80%"></kbd></p>

> [!NOTE]
> Trong Octave/Matlab bsxfun làm việc tương tự

<br>

<a id="node-3n8sonf"></a>

### A Note On Python/ Numpy Vectors

<br>

<a id="node-qn8lzrh"></a>

> [!NOTE]
> 1 Python numpy's broadcasting operations and flexibility are both strengths
> and weaknesses of the programming language.
>
> 2 Broadcasting and flexibility can cause subtle and strange bugs in the
> code if not used correctly.
>
> 3 The rank 1 array in Python numpy is a funny data structure that behaves
> inconsistently as either a row vector or a column vector, making it
> nonintuitive.
>
> 4 It is recommended to use (n, 1) or (1, n) arrays to ensure consistent
> behavior.
>
> 5 Assertion statements can be used to check the dimensions of arrays and
> ensure consistent behavior.
>
> 6 Reshaping rank 1 arrays can also ensure consistent behavior.

<br>

<a id="node-fq5c5qy"></a>

<p align="center"><kbd><img src="assets/5t9wpl0t9d5.png" width="80%"></kbd></p>

> [!NOTE]
> Rank 1 array - 1-Dimensional array behave rất kì cục (ex.
> a.T cũng y nguyên), ko phải row vector cũng ko phải
> column vector.

<br>

<a id="node-gtdmo9g"></a>

<p align="center"><kbd><img src="assets/gmfvvucz1z6.png" width="80%"></kbd></p>

> [!NOTE]
> Nên luôn luôn defin Rank 2 array

<br>

<a id="node-sxn6akg"></a>

<p align="center"><kbd><img src="assets/dj0fnx25y3p.png" width="80%"></kbd></p>

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

<a id="node-7n41oeo"></a>

<p align="center"><kbd><img src="assets/5gu4zjl0y6t.png" width="80%"></kbd></p>

<br>

<a id="node-05dcced"></a>

### Quick Tour Notebook

<br>

<a id="node-3vnywel"></a>

#### ...

<br>

<a id="node-knzmuzd"></a>

<p align="center"><kbd><img src="assets/ijob1nlh2fn.png" width="80%"></kbd></p>

> [!NOTE]
> Có issue gì thì Restart Kernel

<br>

<a id="node-qdobp9h"></a>

### Logistic Regression Cost Function

<br>

<a id="node-wmep0to"></a>

> [!NOTE]
> 1 In this optional video, the speaker justifies the use of the cost function for logistic
> regression that was introduced in an earlier video.
>
> 2 In logistic regression, the prediction y hat is the sigmoid of w transpose x + b, where
> sigmoid is a familiar function. The goal is to interpret y hat as the probability that y=1
> given x.
>
> 3 The chance that y=1 given x is y hat, and the chance that y=0 given x is 1- y hat.
>
> 4 These two equations can be summarized into a single equation: (y hat ^ y )(1- y hat)^(1-y) for
> y=0 or 1. This equation is a correct definition for p(y|x).
>
> 5 Because the log function is a strictly monotonically increasing function, maximizing
> log p(y|x) gives a similar result as optimizing p(y|x).
>
> 6 The loss function for a single example is -[y log y hat + (1-y) log (1- y hat)].
>
> 7 The cost function for the entire training set is the negative sum of the loss function
> over all m examples. This is derived using the principle of maximum likelihood
> estimation, which means choosing the parameters that maximize the probability of the
> observations in the training set.

<br>

<a id="node-bepmsdk"></a>

<p align="center"><kbd><img src="assets/65lz9ei9z5u.png" width="80%"></kbd></p>

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

<a id="node-bjge5nr"></a>

<p align="center"><kbd><img src="assets/4usd63kgav8.png" width="80%"></kbd></p>

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

<a id="node-t76bq0c"></a>

## Quiz: Neural Network Basic

<br>

<a id="node-htia1ew"></a>

<p align="center"><kbd><img src="assets/z0oosz203rd.png" width="80%"></kbd></p>

<br>

<a id="node-qliseqb"></a>

<p align="center"><kbd><img src="assets/naun1ksgfh.png" width="80%"></kbd></p>

<br>

<a id="node-3rlkly9"></a>

<p align="center"><kbd><img src="assets/zhc1xx1h95r.png" width="80%"></kbd></p>

<br>

<a id="node-h0z7oxk"></a>

<p align="center"><kbd><img src="assets/ocidqw4dh8.png" width="80%"></kbd></p>

<br>

<a id="node-dc3fbxb"></a>

<p align="center"><kbd><img src="assets/di1073ppaom.png" width="80%"></kbd></p>

<br>

<a id="node-i4l4wxc"></a>

<p align="center"><kbd><img src="assets/4kbg8tf8s3p.png" width="80%"></kbd></p>

<br>

<a id="node-bjnow6r"></a>

<p align="center"><kbd><img src="assets/1eqzcble6lk.png" width="80%"></kbd></p>

<br>

<a id="node-mlqwzu7"></a>

<p align="center"><kbd><img src="assets/bh4dfsruwwc.png" width="80%"></kbd></p>

<br>

<a id="node-zdelisy"></a>

<p align="center"><kbd><img src="assets/6k06v89916u.png" width="80%"></kbd></p>

<br>

<a id="node-ownd3wk"></a>

<p align="center"><kbd><img src="assets/ornb8sm6wi.png" width="80%"></kbd></p>

<br>

<a id="node-gyrd2db"></a>

## Programming Assignment

<br>

<a id="node-j9qa843"></a>

### Some Notes

<br>

<a id="node-k88a27k"></a>

<p align="center"><kbd><img src="assets/nagz8r8u8d.png" width="80%"></kbd></p>

<br>

<a id="node-4k5li6k"></a>

<p align="center"><kbd><img src="assets/4zeqd4qgjm7.png" width="80%"></kbd></p>

<br>

<a id="node-mf72viw"></a>

<p align="center"><kbd><img src="assets/isv9rvyukyb.png" width="80%"></kbd></p>

<br>

<a id="node-yyi8oe9"></a>

<p align="center"><kbd><img src="assets/svqpma1tplh.png" width="80%"></kbd></p>

<br>

<a id="node-8b9razz"></a>

<p align="center"><kbd><img src="assets/k2b9c1vba7f.png" width="80%"></kbd></p>

<br>

<a id="node-7dbuger"></a>

<p align="center"><kbd><img src="assets/jcwp6tn6xy.png" width="80%"></kbd></p>

<br>

<a id="node-stwlvk1"></a>

### Python Basic With Numpy

<br>

<a id="node-103orij"></a>

<p align="center"><kbd><img src="assets/kamo1t5uaa.png" width="80%"></kbd></p>

<br>

<a id="node-goip0ec"></a>

<p align="center"><kbd><img src="assets/wtyeaz3uenn.png" width="80%"></kbd></p>

<br>

<a id="node-gbagx0a"></a>

<p align="center"><kbd><img src="assets/i5mkv9r4wdl.png" width="80%"></kbd></p>

<br>

<a id="node-tk75mat"></a>

<p align="center"><kbd><img src="assets/iqc9fgvwcq.png" width="80%"></kbd></p>

<br>

<a id="node-lganjd0"></a>

<p align="center"><kbd><img src="assets/akuftpbog76.png" width="80%"></kbd></p>

<br>

<a id="node-iw820c4"></a>

<p align="center"><kbd><img src="assets/rjzxkwrfzvb.png" width="80%"></kbd></p>

<br>

<a id="node-ovkfphk"></a>

<p align="center"><kbd><img src="assets/4d32wdnitnv.png" width="80%"></kbd></p>

<br>

<a id="node-mghl5da"></a>

<p align="center"><kbd><img src="assets/ysbjr0en95.png" width="80%"></kbd></p>

<br>

<a id="node-0xgv0x2"></a>

<p align="center"><kbd><img src="assets/c3vz2nk23k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/c0evmvbdbw.png" width="80%"></kbd></p>

<br>

<a id="node-6fkl6yp"></a>

<p align="center"><kbd><img src="assets/vk4g49iddq.png" width="80%"></kbd></p>

<br>

<a id="node-mqx7lyh"></a>

<p align="center"><kbd><img src="assets/t425t4r66u.png" width="80%"></kbd></p>

<br>

<a id="node-xzpyksp"></a>

<p align="center"><kbd><img src="assets/kpuz6rfzsnp.png" width="80%"></kbd></p>

<br>

<a id="node-5qrvhfl"></a>

<p align="center"><kbd><img src="assets/dl7kdort5a.png" width="80%"></kbd></p>

<br>

<a id="node-ba7fy0s"></a>

<p align="center"><kbd><img src="assets/v3dpe05mri.png" width="80%"></kbd></p>

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

<a id="node-cmnbiom"></a>

<p align="center"><kbd><img src="assets/wdg604ie3s.png" width="80%"></kbd></p>

> [!NOTE]
> Cái này là 2 colors channels image

<br>

<a id="node-vraqm3u"></a>

<p align="center"><kbd><img src="assets/n0esigdem5.png" width="80%"></kbd></p>

<br>

<a id="node-9fq4hkk"></a>

<p align="center"><kbd><img src="assets/fenryca2o8q.png" width="80%"></kbd></p>

<br>

<a id="node-qpqf9z8"></a>

<p align="center"><kbd><img src="assets/5hp4fn2ee2w.png" width="80%"></kbd></p>

<br>

<a id="node-xc063gc"></a>

<p align="center"><kbd><img src="assets/u5twhgzg02.png" width="80%"></kbd></p>

<br>

<a id="node-v04v052"></a>

<p align="center"><kbd><img src="assets/czle4m7g25d.png" width="80%"></kbd></p>

<br>

<a id="node-u6eopkb"></a>

<p align="center"><kbd><img src="assets/k9tv3wzkre.png" width="80%"></kbd></p>

<br>

<a id="node-fuf6xvs"></a>

<p align="center"><kbd><img src="assets/hq09md0b46b.png" width="80%"></kbd></p>

<br>

<a id="node-7zqfd6f"></a>

<p align="center"><kbd><img src="assets/a2ru2a4ifoo.png" width="80%"></kbd></p>

<br>

<a id="node-gn9zbht"></a>

<p align="center"><kbd><img src="assets/tfyk8jtu1aq.png" width="80%"></kbd></p>

<br>

<a id="node-de1nnw8"></a>

<p align="center"><kbd><img src="assets/fsuflcanzmb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/22qti8pys84.png" width="80%"></kbd></p>

<br>

<a id="node-h2tdvma"></a>

<p align="center"><kbd><img src="assets/7an61hay9p.png" width="80%"></kbd></p>

<br>

<a id="node-xpyqavh"></a>

<p align="center"><kbd><img src="assets/vgdqacw1khs.png" width="80%"></kbd></p>

<br>

<a id="node-jjxo5au"></a>

<p align="center"><kbd><img src="assets/2jew3x1amjh.png" width="80%"></kbd></p>

<br>

<a id="node-5uxj3cs"></a>

<p align="center"><kbd><img src="assets/q3faxq9tkzm.png" width="80%"></kbd></p>

<br>

<a id="node-jc0s0fl"></a>

<p align="center"><kbd><img src="assets/tt26agvetn9.png" width="80%"></kbd></p>

<br>

<a id="node-5g88r9w"></a>

<p align="center"><kbd><img src="assets/iv0gw3irsjs.png" width="80%"></kbd></p>

<br>

<a id="node-em116ba"></a>

<p align="center"><kbd><img src="assets/c6aqpg044f.png" width="80%"></kbd></p>

<br>

<a id="node-kiwlzel"></a>

<p align="center"><kbd><img src="assets/583o096m7rm.png" width="80%"></kbd></p>

> [!NOTE]
> * or np.multiply() = . * in Matlab

<br>

<a id="node-cw5559n"></a>

<p align="center"><kbd><img src="assets/rnm1lw5gwak.png" width="80%"></kbd></p>

<br>

<a id="node-8jdc11g"></a>

<p align="center"><kbd><img src="assets/ywwn8078zo.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu để keepdims = True thì bị lỗi tại Loss expect a float.

<br>

<a id="node-cyb2u09"></a>

<p align="center"><kbd><img src="assets/kpl1xyb957.png" width="80%"></kbd></p>

<br>

<a id="node-ojuodfn"></a>

<p align="center"><kbd><img src="assets/wjl8q79ara.png" width="80%"></kbd></p>

<br>

<a id="node-cs4fj3w"></a>

<p align="center"><kbd><img src="assets/34iqxux4us3.png" width="80%"></kbd></p>

<br>

<a id="node-s8602k6"></a>

<p align="center"><kbd><img src="assets/r2dhwrr6n1.png" width="80%"></kbd></p>

> [!NOTE]
> So sánh function .dot() khi input là vector (1D array) và matrix (2D array)

<br>

<a id="node-yhneg0j"></a>

#### Grade

<br>

<a id="node-lxo0474"></a>

<p align="center"><kbd><img src="assets/3nnlzmbg29n.png" width="80%"></kbd></p>

<br>

<a id="node-65ylsoy"></a>

### Logistic Regression With A Neural Network Mindset

> [!NOTE]
> Build a logistic regression classifier to recognize cats.  This
> assignment will step you through how to do this with a
> Neural Network mindset, and will also hone your intuitions
> about deep learning.

<br>

<a id="node-ppr1hoc"></a>

<p align="center"><kbd><img src="assets/id9mownrigs.png" width="80%"></kbd></p>

<br>

<a id="node-ak6iqaf"></a>

<p align="center"><kbd><img src="assets/wgpp3om1vx.png" width="80%"></kbd></p>

<br>

<a id="node-1vsokow"></a>

<p align="center"><kbd><img src="assets/u23714k4h5b.png" width="80%"></kbd></p>

<br>

<a id="node-t1xeqiz"></a>

<p align="center"><kbd><img src="assets/2pfut37x5au.png" width="80%"></kbd></p>

<br>

<a id="node-4u090lz"></a>

- **mpl.imshow()**

<br>

<a id="node-74csgn9"></a>

<p align="center"><kbd><img src="assets/jwdxylglbyd.png" width="80%"></kbd></p>

<br>

<a id="node-w609e1l"></a>

<p align="center"><kbd><img src="assets/v2c2up8xgcr.png" width="80%"></kbd></p>

<br>

<a id="node-iv9o1qf"></a>

<p align="center"><kbd><img src="assets/yvhzfuey0z.png" width="80%"></kbd></p>

<br>

<a id="node-4hqx7nq"></a>

<p align="center"><kbd><img src="assets/b85zhjotpps.png" width="80%"></kbd></p>

<br>

<a id="node-e1eer8d"></a>

<p align="center"><kbd><img src="assets/3ywarut9zrg.png" width="80%"></kbd></p>

> [!NOTE]
> Hàm reshape cứ nhớ là nếu cho cái dimension = -1 thì đại khái
> là bảo Python tự tính.

<br>

<a id="node-cxui0g5"></a>

<p align="center"><kbd><img src="assets/8xf4f2m95nr.png" width="80%"></kbd></p>

<br>

<a id="node-y1e88mm"></a>

<p align="center"><kbd><img src="assets/t0a0vnjjnr.png" width="80%"></kbd></p>

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

<a id="node-zzbaha9"></a>

<p align="center"><kbd><img src="assets/ujv2hivz4mf.png" width="80%"></kbd></p>

<br>

<a id="node-twge3f3"></a>

<p align="center"><kbd><img src="assets/g6l9egs3u3g.png" width="80%"></kbd></p>

<br>

<a id="node-q814rlh"></a>

<p align="center"><kbd><img src="assets/m7a7urw887.png" width="80%"></kbd></p>

<br>

<a id="node-tgeu8x9"></a>

<p align="center"><kbd><img src="assets/kvitadqxiuf.png" width="80%"></kbd></p>

<br>

<a id="node-c9gdyqf"></a>

<p align="center"><kbd><img src="assets/1g91mruqxey.png" width="80%"></kbd></p>

<br>

<a id="node-pfd44fs"></a>

<p align="center"><kbd><img src="assets/r1mao0yy12j.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/dbr3g01sk1b.png" width="80%"></kbd></p>

> [!NOTE]
> Vì hàm np.exp() accept vector or matrix -> dùng nó
> trong hàm sigmoid cũng sẽ accept vector . matrix

<br>

<a id="node-6t3x256"></a>

<p align="center"><kbd><img src="assets/mavkkupex5.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu define b = 0 -> b sẽ là int

<br>

<a id="node-25slebm"></a>

<p align="center"><kbd><img src="assets/xngdtj7x66o.png" width="80%"></kbd></p>

<br>

<a id="node-zn31ne5"></a>

<p align="center"><kbd><img src="assets/2wclvoxeiz9.png" width="80%"></kbd></p>

<br>

<a id="node-i55tar4"></a>

<p align="center"><kbd><img src="assets/rs9t01h0vni.png" width="80%"></kbd></p>

> [!NOTE]
> Chỉ có hơi rắc rối chưa quen dùng hàm **np.dot
>
>
>
> Và khác với Khoá ML cũ, X define dạng n x m 
> (chứ không phải m x n) nên lấy m = X.shape[1]**

<br>

<a id="node-nrcce69"></a>

<p align="center"><kbd><img src="assets/fmcm044vc2o.png" width="80%"></kbd></p>

<br>

<a id="node-v395y3h"></a>

<p align="center"><kbd><img src="assets/zf5obv7i7is.png" width="80%"></kbd></p>

<br>

<a id="node-m4voo7u"></a>

<p align="center"><kbd><img src="assets/d71otee47f.png" width="80%"></kbd></p>

<br>

<a id="node-8xm825h"></a>

<p align="center"><kbd><img src="assets/yswjahfqko8.png" width="80%"></kbd></p>

<br>

<a id="node-vl979n1"></a>

- **hàm np.dot()**

<br>

<a id="node-eivvmy8"></a>

<p align="center"><kbd><img src="assets/gfu4niws3x.png" width="80%"></kbd></p>

> [!NOTE]
> np.dot()
>
>
>
> 2 Matrix thì tuân thủ quy tắc size matrix

<br>

<a id="node-86fribf"></a>

<p align="center"><kbd><img src="assets/dnmbhl8gwz6.png" width="80%"></kbd></p>

> [!NOTE]
> (2x3) không thể .dot với (2x3)

<br>

<a id="node-ff8ddi7"></a>

<p align="center"><kbd><img src="assets/u0lmhjl8uc.png" width="80%"></kbd></p>

> [!NOTE]
> np.dot()
>
>
>
> 2 1D array thì + lại.

<br>

<a id="node-txovxk9"></a>

<p align="center"><kbd><img src="assets/fwomg5vrxei.png" width="80%"></kbd></p>

> [!NOTE]
> np.dot()
>
>
>
> 1D array với Matrix cột thì được, coi matrix cột như 1D array

<br>

<a id="node-a47wmza"></a>

<p align="center"><kbd><img src="assets/kl9na9rxwn.png" width="80%"></kbd></p>

<br>

<a id="node-mf9w8sn"></a>

<p align="center"><kbd><img src="assets/ombrf56pa4f.png" width="80%"></kbd></p>

<br>

<a id="node-2xn001u"></a>

<p align="center"><kbd><img src="assets/15fdev0oark.png" width="80%"></kbd></p>

<br>

<a id="node-3z112u7"></a>

<p align="center"><kbd><img src="assets/kk6171zg95.png" width="80%"></kbd></p>

> [!NOTE]
> **CHÚ Ý BƯỚC NÀY** w = w.reshape(X.shape[0], 1) **LÀ ĐỂ CHẮC CHẮN
> W CÓ SHAPE MONG MUỐN
>
>
>
> Trong lecture ổng có nhấn mạnh đừng ngại reshape để đảm bảo shape
> đúng**

<br>

<a id="node-3jo3trm"></a>

<p align="center"><kbd><img src="assets/dbfd8l3h6sw.png" width="80%"></kbd></p>

<br>

<a id="node-63lu5re"></a>

<p align="center"><kbd><img src="assets/t5hea1r6qz.png" width="80%"></kbd></p>

<br>

<a id="node-4dxkngr"></a>

<p align="center"><kbd><img src="assets/b9hn2ugbp9s.png" width="80%"></kbd></p>

<br>

<a id="node-ow53g0v"></a>

<p align="center"><kbd><img src="assets/ld8s8ei52i.png" width="80%"></kbd></p>

<br>

<a id="node-kzxkw01"></a>

<p align="center"><kbd><img src="assets/telydkzl5xn.png" width="80%"></kbd></p>

<br>

<a id="node-3oojmb9"></a>

<p align="center"><kbd><img src="assets/ng50tnz8sqi.png" width="80%"></kbd></p>

> [!NOTE]
> **optimize(...X_train, Y_train,...) mới đúng, chứ với X, Y là sai**

<br>

<a id="node-4xy7sph"></a>

<p align="center"><kbd><img src="assets/roh8mgevpr.png" width="80%"></kbd></p>

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

<a id="node-wqzdosg"></a>

<p align="center"><kbd><img src="assets/kkhyoot9ryo.png" width="80%"></kbd></p>

<br>

<a id="node-5z6yg0n"></a>

<p align="center"><kbd><img src="assets/zth4wrpe9a.png" width="80%"></kbd></p>

<br>

<a id="node-vfllb81"></a>

<p align="center"><kbd><img src="assets/tyxr5f5118h.png" width="80%"></kbd></p>

> [!NOTE]
> **Thử với các learning rate khác nhau**

<br>

<a id="node-98kh957"></a>

<p align="center"><kbd><img src="assets/2ymn6wsm3kp.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/eu8nf8o8k3d.png" width="80%"></kbd></p>

<br>

<a id="node-rluldtb"></a>

<p align="center"><kbd><img src="assets/lgs3w9mwrp.png" width="80%"></kbd></p>

<br>

<a id="node-edxzbhp"></a>

<p align="center"><kbd><img src="assets/idcp27ubclc.png" width="80%"></kbd></p>

<br>

