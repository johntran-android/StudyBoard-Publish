# C1w3_shalow Neural Networks

📊 **Progress:** `23` Notes | `91` Screenshots

---
<a id="node-zk88i0h"></a>

## C1w3_shalow Neural Networks

<br>

<a id="node-pjup4r3"></a>

## Neural Networks Overview

<br>

<a id="node-zn53agg"></a>

> [!NOTE]
> 1 Overview of the week's topic: The speaker provides an introduction to the topic of
> implementing a neural network.
>
> 2 Recap of logistic regression: The speaker briefly recaps the logistic regression model, which
> involves computing a z-value based on input features x and parameters w and b, then using a
> sigmoid function to calculate the output value a or y-hat, which is used to compute the loss
> function L.
>
> 3 Neural network structure: The speaker introduces the structure of a neural network, which
> involves stacking together many sigmoid units. Each node in the network involves two
> calculations: a z-like calculation and an a-like calculation. The network is composed of layers,
> with superscript square brackets used to refer to quantities associated with each layer.
>
> 4 Calculation of z and a: The speaker explains that the network starts by computing z1 based on
> input features x, then computes a1 as the sigmoid of z1. The process is repeated to compute z2
> and a2, which is the final output of the neural network and is also referred to as y-hat.
>
> 5 Backward calculation: The speaker notes that the network requires a backward calculation in
> order to compute derivatives and make updates to the parameters w and b. This calculation
> involves computing da2, dz2, dw2, and db2 in a right-to-left manner.
>
> 6 Key takeaway: The speaker emphasizes that a neural network is essentially an extension of
> logistic regression, where the z and a calculations are repeated multiple times. The notation and
> details can be complex, but they will be further explained in upcoming videos.

<br>

<a id="node-kdsiy06"></a>

<p align="center"><kbd><img src="assets/bgsqcb465hq.png" width="80%"></kbd></p>

<br>

<a id="node-0yarc9t"></a>

## Neural Network Representation

<br>

<a id="node-sc72ymy"></a>

> [!NOTE]
> 1 Explanation of a two-layer neural network with multiple hidden units
>
> 2 The neural network computes the output in the same way as logistic
> regression but repeatedly
>
> 3 Each node in the hidden layer of the neural network performs two
> steps of computation
>
> 4 The first step is the computation of z = w transpose x + b
>
> 5 The second step is the computation of a = sigmoid(z)
>
> 6 The notation used in the computation of a and z
>
> 7 Explanation of the first and second hidden units in the neural
> network
>
> 8 The process of vectorizing the computation for efficiency
>
> 9 The matrix of weight vectors and input features multiplied to get z
>
> 10 Adding the bias vector to z
>
> 11 The outcome of the computation corresponds to the values of z for
> each hidden unit.
>
> 12 The vector is called the vector of activations.

<br>

<a id="node-qkr7dil"></a>

<p align="center"><kbd><img src="assets/vnvkt5di9v.png" width="80%"></kbd></p>

<br>

<a id="node-xjxc8j5"></a>

## Computing A Neural Network's Output

<br>

<a id="node-jw7uwmb"></a>

> [!NOTE]
> 1 The video provides justification for the vectorized implementation for
> propagation through a neural network by considering the forward propagation
> calculation for a few examples.
>
> 2 The matrix X is formed by stacking together all of the training examples, and
> when this matrix is multiplied by W, the resulting matrix contains the
> corresponding outputs stacked up in columns.
>
> 3 The video recapitulates the steps for implementing forward propagation for
> one training example at a time and then shows how to vectorize it across all
> training examples at the same time.
>
> 4 The video also highlights the symmetry in the equations for the different
> layers of the neural network and how deeper neural networks repeat the same
> computation even more times.
>
> 5 Finally, the video notes that sigmoid functions are not always the best choice
> for neural networks and hints at the topic of the next video, which will explore
> using different activation functions.

<br>

<a id="node-ql407k9"></a>

<p align="center"><kbd><img src="assets/3p00leew0gy.png" width="80%"></kbd></p>

<br>

<a id="node-db927rn"></a>

<p align="center"><kbd><img src="assets/cr5vw8ch65f.png" width="80%"></kbd></p>

<br>

<a id="node-j37fkzj"></a>

<p align="center"><kbd><img src="assets/snjtg335w1l.png" width="80%"></kbd></p>

<br>

<a id="node-tkbn8bk"></a>

## Vectorizing Across Multiple

<br>

<a id="node-w595ald"></a>

> [!NOTE]
> 1 To compute the prediction on a neural network for multiple training
> examples, you need to vectorize the computation process.
>
> 2 To do this, you need to repeat the process for each training example,
> using the activation function notation a\\_2\\_.
>
> 3 To get rid of the repetition, you can stack the training examples in
> columns to create a matrix X.
>
> 4 You can then compute the value of the different variables, Z[1], A[1],
> Z[2], and A[2], using the matrix X, and the weights W and biases b.
>
> 5 By stacking the vectors in columns for Z[1], A[1], Z[2], and A[2], you
> can create the matrices Z[1], A[1], Z[2], and A[2], respectively.
>
> 6 Vectorizing the computation process allows you to compute the
> predictions of all your training examples at the same time.

<br>

<a id="node-mc5y5qj"></a>

<p align="center"><kbd><img src="assets/nm078fva7qp.png" width="80%"></kbd></p>

<br>

<a id="node-gmidugi"></a>

<p align="center"><kbd><img src="assets/n8g2cc3amuh.png" width="80%"></kbd></p>

<br>

<a id="node-9uh1e9u"></a>

## Explanation For Vectorized Implementation

<br>

<a id="node-xffhl7a"></a>

> [!NOTE]
> Main ideas:  1 The previous video discussed the vectorized implementation of neural
> network propagation through training examples horizontally stacked in the matrix x.
>
> 2 The justification for the correctness of the equations was explained by going
> through part of the forward propagation calculation for a few examples.
>
> 3 The training set X is formed by vertically stacking the vectors x1, x2, etc. and
> multiplying it by w gives the corresponding z values, which are also vertically stacked
> in matrix capital Z1.
>
> 4 Python broadcasting allows adding the bias term b to the values while maintaining
> the correct values.
>
> 5 Similar reasoning can be used to show that all four steps of the forward
> propagation calculation work.
>
> 6 Recap of the four steps of forward propagation and how they can be vectorized
> across multiple training examples using stacked matrices.
>
> 7 The symmetry between the equations for z1 and a1 and z2 and a2 shows that the
> different layers of a neural network are doing the same computation.
>
> 8 Next, the video will discuss why the sigmoid function is not the best choice for
> neural networks.

<br>

<a id="node-f7wi3q1"></a>

<p align="center"><kbd><img src="assets/c9lcx4e7iv.png" width="80%"></kbd></p>

<br>

<a id="node-znmwh4d"></a>

<p align="center"><kbd><img src="assets/13o9ptvwlm2r.png" width="80%"></kbd></p>

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

<a id="node-i4ues2t"></a>

## Activation Functions

<br>

<a id="node-rpkfjfj"></a>

> [!NOTE]
> Main ideas:  1 Choice of activation function is an important decision when
> building a neural network.
>
> 2 The sigmoid function is commonly used but there are other options that can
> work better.
>
> 3 The hyperbolic tangent (tan h) function is often a better choice for hidden
> layers.
>
> 4 The mean of activations using tan h is closer to zero, making learning easier.
>
> 5 The sigmoid function is useful for binary classification output layers.
>
> 6 The rectified linear unit (ReLU) and Leaky ReLU are popular choices for
> hidden layers.
>
> 7 The ReLU and Leaky ReLU have advantages over sigmoid and tan h
> functions.
>
> 8 Choosing an activation function depends on the specific task and the
> individual preferences of the user.

<br>

<a id="node-qs4sfh8"></a>

<p align="center"><kbd><img src="assets/onr8wvk97a.png" width="80%"></kbd></p>

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

<a id="node-nhsl7u9"></a>

<p align="center"><kbd><img src="assets/1dglik7bkl.png" width="80%"></kbd></p>

<br>

<a id="node-tyv3xak"></a>

<p align="center"><kbd><img src="assets/o1z24augf8h.png" width="80%"></kbd></p>

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

<a id="node-kw8ue1l"></a>

## Why Do You Need Non-linear Activation Functions

<br>

<a id="node-bop7ml1"></a>

> [!NOTE]
> 1 A neural network needs a non-linear activation function to compute interesting functions.
>
> 2 The linear activation function, which just outputs whatever was input, is not useful because
> the neural network outputs a linear function of the input.
>
> 3 Even in deep neural networks with many layers, if linear activation functions are used, the
> network is just computing a linear activation function and is therefore not computing more
> interesting functions.
>
> 4 One place where a linear activation function might be used is in the output layer for
> regression problems, where the output y-hat is a real number going anywhere from minus
> infinity to plus infinity.
>
> 5 However, in this case, the hidden units should not use activation functions or should use
> non-linear activation functions like ReLU or tanh.
>
> 6 Using a linear activation function in the hidden layer is extremely rare except for some
> special circumstances relating to compression.
>
> 7 The non-linear activation function is a critical part of neural networks because it allows for
> the computation of more interesting functions.
>
> 8 In the next video, the slope or the derivatives of individual activation functions will be
> discussed to set up for the discussion on gradient descent.

<br>

<a id="node-uxg0o4b"></a>

<p align="center"><kbd><img src="assets/xgj0r5ysz48.png" width="80%"></kbd></p>

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

<a id="node-xdjc5be"></a>

## Derivatives Of Activation Functions

<br>

<a id="node-iuu6urz"></a>

> [!NOTE]
> Main ideas:  1 Backpropagation in neural networks requires
> computing the slope or derivative of the activation functions.
>
> 2 Sigmoid activation function has a derivative formula of g(z) * (1 -
> g(z)).
>
> 3 The Tanh activation function has a derivative formula of 1 - a^2.
>
> 4 ReLU activation function has a derivative of 0 for z < 0 and 1 for z >
> 0.
>
> 5 Leaky ReLU activation function has a small positive slope for z < 0
> and a slope of 1 for z > 0.

<br>

<a id="node-h5km91a"></a>

<p align="center"><kbd><img src="assets/u4a08hsb21.png" width="80%"></kbd></p>

<br>

<a id="node-4n2dvq9"></a>

<p align="center"><kbd><img src="assets/4zbu17ep3h2.png" width="80%"></kbd></p>

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

<a id="node-r9pg3i5"></a>

<p align="center"><kbd><img src="assets/c4a5iuk3ndi.png" width="80%"></kbd></p>

> [!NOTE]
> Giải thích tại sao derivative của relu lại undefine tại  z = 0

<br>

<a id="node-9k2izbq"></a>

<p align="center"><kbd><img src="assets/7314g5q2aux.png" width="80%"></kbd></p>

<br>

<a id="node-zvh9c7m"></a>

## Gradient Descent For Neural Networks

<br>

<a id="node-g3ffa41"></a>

> [!NOTE]
> 1 Introduction to implementing gradient descent for neural network with
> one hidden layer.
>
> 2 Explanation of the parameters and dimensions for a neural network
> with a single hidden layer.
>
> 3 Cost function for binary classification and how to train the parameters
> using gradient descent.
>
> 4 Initialization of parameters and the importance of random initialization.
>
> 5 Derivatives of the cost function with respect to the parameters W1,
> B1, W2, and B2.
>
> 6 Forward propagation for computation of neural network outputs.
>
> 7 Back propagation for computing derivatives and updating the
> parameters using gradient descent.
>
> 8 Explanation of Python NumPy commands used to compute the
> derivatives.

<br>

<a id="node-prqv2k1"></a>

<p align="center"><kbd><img src="assets/ps4ihm2ql9e.png" width="80%"></kbd></p>

<br>

<a id="node-ram260v"></a>

<p align="center"><kbd><img src="assets/r40ojw3gg9.png" width="80%"></kbd></p>

<br>

<a id="node-q0qmcsi"></a>

## Backpropagation Intuition

<br>

<a id="node-8i5si8k"></a>

> [!NOTE]
> 1 The video explains the intuition for deriving the equations for backpropagation
> using a computation graph.
>
> 2 The forward pass in logistic regression involves computing z, A, and A loss,
> while the backward pass involves computing da, dz, dw, and db.
>
> 3 The loss function for logistic regression is L(a, y) = -y log A - (1 - y) log(1 - A).
>
> 4 Da for logistic regression is equal to -y/A + (1 - y)/(1 - A).
>
> 5 Dz for logistic regression is equal to A - y, which is computed using the chain
> rule of calculus.
>
> 6 Dw for logistic regression is equal to dz times x, while db is equal to dz.
>
> 7 In a two-layer neural network, backpropagation computes da2, dz2, dw2, and
> db2, and then computes da1, dz1, dw1, and db1.
>
> 8 Da1 and dz1 are often collapsed into one step in practice.
>
> 9 Dz1 is computed as w2 transpose times dz2 times an element-wise product of
> g1 prime of z1.
>
> 10 The computation for dz2 is the same as for logistic regression, dz2 = a2 - y.
>
> 11 Dw2 is equal to dz2 times a1 transpose, and db2 is equal to dz2.
>
> 12 There is an extra transpose in dw2 compared to dw for logistic regression
> because a1 is a row vector while w2 is a column vector.

<br>

<a id="node-22rrcvt"></a>

<p align="center"><kbd><img src="assets/ae9bm04jjdi.png" width="80%"></kbd></p>

<br>

<a id="node-smygbvb"></a>

<p align="center"><kbd><img src="assets/887578rt6n7.png" width="80%"></kbd></p>

> [!NOTE]
> One tip when implementing backprop, if you just make sure that the
> dimensions of your matrices match up, if you think through, what are the
> dimensions of your various matrices including w^1, w^2, z^1, z^2, a^1, a^2,
> and so on, and **just make sure that the dimensions of these matrix
> operations may match up**, sometimes that will **already eliminate quite a lot
> of bugs** in backprop

<br>

<a id="node-fcwkd9j"></a>

<p align="center"><kbd><img src="assets/fcrspbqe88p.png" width="80%"></kbd></p>

<br>

<a id="node-dmh73cn"></a>

<p align="center"><kbd><img src="assets/up38rtiw18i.png" width="80%"></kbd></p>

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

<a id="node-uaursjb"></a>

<p align="center"><kbd><img src="assets/9hx84om1zaa.png" width="80%"></kbd></p>

<br>

<a id="node-86wz5qn"></a>

## Random Initialization

<br>

<a id="node-k0ynyx3"></a>

> [!NOTE]
> 1 When changing the neural network, it is important to initialize the weights
> randomly.
>
> 2 For logistic regression, initializing the weights to zero was okay, but it won't
> work for neural networks.
>
> 3 Initializing w to all zeros and then applying gradient descent creates
> symmetry between the hidden units.
>
> 4 Symmetry means that both hidden units are computing the same function
> and will remain symmetric after every iteration.
>
> 5 The solution is to initialize the parameters randomly.
>
> 6 You can use np.random.randn to generate a Gaussian random variable for
> w1, multiply it by a very small number, such as 0.01, and initialize b to zero.
>
> 7 The same applies to w2 and b2.
>
> 8 Initializing weights to very large values causes the activation function to be
> saturated, which slows down learning.
>
> 9 Multiplying by a small number, such as 0.01, is reasonable to avoid the
> saturation of the activation function.
>
> 10 Same goes for w2.

<br>

<a id="node-p4nizrb"></a>

<p align="center"><kbd><img src="assets/mz6eiipsgcq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu initialize params  = 0 hết thì gradient descent thì cả network
> các hidden layer vô nghĩa

<br>

<a id="node-hc7ophr"></a>

<p align="center"><kbd><img src="assets/yds9lp9d1td.png" width="80%"></kbd></p>

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

<a id="node-kt8reeu"></a>

<p align="center"><kbd><img src="assets/pxyxt6n8l8l.png" width="80%"></kbd></p>

<br>

<a id="node-hn4d1kk"></a>

## Quiz: Shallow Neural Network

<br>

<a id="node-ur3ctnc"></a>

<p align="center"><kbd><img src="assets/2dgblwu6rzy.png" width="80%"></kbd></p>

<br>

<a id="node-gj2tkuv"></a>

<p align="center"><kbd><img src="assets/61fvh3wr4t5.png" width="80%"></kbd></p>

<br>

<a id="node-xpfw798"></a>

<p align="center"><kbd><img src="assets/loutf35yq5.png" width="80%"></kbd></p>

<br>

<a id="node-o6wnfs4"></a>

<p align="center"><kbd><img src="assets/aglym4qey7g.png" width="80%"></kbd></p>

<br>

<a id="node-34zlx0i"></a>

<p align="center"><kbd><img src="assets/nlzy9po4ldq.png" width="80%"></kbd></p>

<br>

<a id="node-l6masgd"></a>

<p align="center"><kbd><img src="assets/18yfhixphq4.png" width="80%"></kbd></p>

<br>

<a id="node-ezku5ld"></a>

<p align="center"><kbd><img src="assets/di0o6r0lumw.png" width="80%"></kbd></p>

<br>

<a id="node-jc5i73q"></a>

<p align="center"><kbd><img src="assets/g0yzpg13k7.png" width="80%"></kbd></p>

<br>

<a id="node-22jk296"></a>

<p align="center"><kbd><img src="assets/7p7csigd8aq.png" width="80%"></kbd></p>

<br>

<a id="node-lmskide"></a>

<p align="center"><kbd><img src="assets/kt7qfp2112.png" width="80%"></kbd></p>

<br>

<a id="node-1gzj8fu"></a>

<p align="center"><kbd><img src="assets/x615c5k1bch.png" width="80%"></kbd></p>

<br>

<a id="node-td61z6p"></a>

<p align="center"><kbd><img src="assets/bg8p48xxj25.png" width="80%"></kbd></p>

<br>

<a id="node-8pzx0r5"></a>

> [!NOTE]
> PROGRAMMING ASSIGNMENT: PLANAR DATA
> CLASSIFICATION WITH ONE HIDDEN LAYER

<br>

<a id="node-j8mlmjp"></a>

### 1. + 2.

<br>

<a id="node-3duc6fu"></a>

<p align="center"><kbd><img src="assets/o18w7t727rp.png" width="80%"></kbd></p>

<br>

<a id="node-j8ab5yl"></a>

<p align="center"><kbd><img src="assets/i0nxa0v3ub.png" width="80%"></kbd></p>

<br>

<a id="node-3uylqdi"></a>

<p align="center"><kbd><img src="assets/x7nshfubs5.png" width="80%"></kbd></p>

<br>

<a id="node-hh3z9zz"></a>

### 3 - Simple Logistic Regression

<br>

<a id="node-fcr2rlf"></a>

<p align="center"><kbd><img src="assets/36tv2snuvvo.png" width="80%"></kbd></p>

<br>

<a id="node-hnyqqku"></a>

<p align="center"><kbd><img src="assets/orizxfo461h.png" width="80%"></kbd></p>

<br>

<a id="node-3lhfwcn"></a>

### 4.2 - Initialize the model's parameters

<br>

<a id="node-pcm228x"></a>

### 4 - Neural Network model¶

<br>

<a id="node-zq125k8"></a>

<p align="center"><kbd><img src="assets/oqn1beilhf.png" width="80%"></kbd></p>

<br>

<a id="node-vzxad96"></a>

<p align="center"><kbd><img src="assets/4vhtih5m5w5.png" width="80%"></kbd></p>

<br>

<a id="node-jd237l9"></a>

### 4.1 - Defining the neural network structure

<br>

<a id="node-x7zptgc"></a>

<p align="center"><kbd><img src="assets/zjeoxc5jpb.png" width="80%"></kbd></p>

<br>

<a id="node-vhdb7he"></a>

<p align="center"><kbd><img src="assets/yg0lvpi0d6.png" width="80%"></kbd></p>

<br>

<a id="node-xuia6sf"></a>

### 4.2 - Initialize the model's parameters

<br>

<a id="node-exehs0n"></a>

<p align="center"><kbd><img src="assets/r7kg5mmf9xs.png" width="80%"></kbd></p>

<br>

<a id="node-0zo70ky"></a>

<p align="center"><kbd><img src="assets/9ozqandl7l.png" width="80%"></kbd></p>

<br>

<a id="node-ubv87o4"></a>

<p align="center"><kbd><img src="assets/nn9nclfw9s8.png" width="80%"></kbd></p>

<br>

<a id="node-73zsabi"></a>

### 4.3 - The loop

<br>

<a id="node-cgukzby"></a>

<p align="center"><kbd><img src="assets/b8ngd6f07dc.png" width="80%"></kbd></p>

<br>

<a id="node-mczowii"></a>

<p align="center"><kbd><img src="assets/ujj1b4fcgz.png" width="80%"></kbd></p>

<br>

<a id="node-ut422iq"></a>

<p align="center"><kbd><img src="assets/4sszppa6x29.png" width="80%"></kbd></p>

<br>

<a id="node-e8ej7ch"></a>

### 4.4 - Compute the Cost

<br>

<a id="node-r0sbx26"></a>

<p align="center"><kbd><img src="assets/u3bxiigcvis.png" width="80%"></kbd></p>

<br>

<a id="node-t5txefm"></a>

<p align="center"><kbd><img src="assets/8rwd0slqorq.png" width="80%"></kbd></p>

<br>

<a id="node-7m7oiqn"></a>

<p align="center"><kbd><img src="assets/db0snf45tm.png" width="80%"></kbd></p>

<br>

<a id="node-2h7m84t"></a>

### 4.5 - Implement Backpropagation

<br>

<a id="node-e79nsq4"></a>

<p align="center"><kbd><img src="assets/hpphl0fmmbm.png" width="80%"></kbd></p>

<br>

<a id="node-frq4e7x"></a>

<p align="center"><kbd><img src="assets/pw9fo75qr6k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/khqlno5yfs.png" width="80%"></kbd></p>

<br>

<a id="node-urujazh"></a>

<p align="center"><kbd><img src="assets/nffh8ymh97.png" width="80%"></kbd></p>

<br>

<a id="node-0xprbgk"></a>

### 4.6 - Update Parameters

<br>

<a id="node-g4pb3ur"></a>

<p align="center"><kbd><img src="assets/pln30lolldd.png" width="80%"></kbd></p>

<br>

<a id="node-c9m7hb8"></a>

<p align="center"><kbd><img src="assets/3x0x8yahjb5.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/631g2ullhp.png" width="80%"></kbd></p>

<br>

<a id="node-9k718nf"></a>

<p align="center"><kbd><img src="assets/hzfkvoxu9va.png" width="80%"></kbd></p>

<br>

<a id="node-yaee336"></a>

### 4.7 - Integration

<br>

<a id="node-0xbydzo"></a>

<p align="center"><kbd><img src="assets/7b403z9btth.png" width="80%"></kbd></p>

<br>

<a id="node-6nrydix"></a>

<p align="center"><kbd><img src="assets/m0henfqtl4b.png" width="80%"></kbd></p>

<br>

<a id="node-oytp0nv"></a>

<p align="center"><kbd><img src="assets/lkgonyoe5s.png" width="80%"></kbd></p>

<br>

<a id="node-x1jlg3f"></a>

### 5 - Test the Model

<br>

<a id="node-dtcws90"></a>

#### 5.1 - Predict

<br>

<a id="node-6jpmbcu"></a>

<p align="center"><kbd><img src="assets/8l9zbuupi2f.png" width="80%"></kbd></p>

<br>

<a id="node-mwkc5eo"></a>

<p align="center"><kbd><img src="assets/rz66xa5jw2.png" width="80%"></kbd></p>

<br>

<a id="node-axdbk5h"></a>

#### 5.2 - Test the Model on the Planar Dataset

<br>

<a id="node-z1idofs"></a>

<p align="center"><kbd><img src="assets/ddxeufdgyhi.png" width="80%"></kbd></p>

<br>

<a id="node-hgepg5f"></a>

<p align="center"><kbd><img src="assets/evnkyvrk7od.png" width="80%"></kbd></p>

<br>

<a id="node-zdp8wh4"></a>

<p align="center"><kbd><img src="assets/tkjor3eqete.png" width="80%"></kbd></p>

<br>

<a id="node-ws8qoyz"></a>

### 6 - Tuning hidden layer size

<br>

<a id="node-jbyyu5x"></a>

<p align="center"><kbd><img src="assets/9gko7dldvq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/pvacasxrg5n.png" width="80%"></kbd></p>

<br>

<a id="node-4osvewa"></a>

### 7- Performance on other datasets

<br>

<a id="node-97ee4rb"></a>

<p align="center"><kbd><img src="assets/ko5uzhobql9.png" width="80%"></kbd></p>

<br>

<a id="node-9zzkxy7"></a>

### Thực Hành F.p & B.p

<br>

<a id="node-fyy4ks5"></a>

#### L.g

<br>

<a id="node-m6u7rpm"></a>

<p align="center"><kbd><img src="assets/udvvcfbxji.png" width="80%"></kbd></p>

<br>

<a id="node-dhfhj2d"></a>

<p align="center"><kbd><img src="assets/5q8akeoqzzl.png" width="80%"></kbd></p>

<br>

<a id="node-38onlxu"></a>

#### S.n.n

<br>

<a id="node-10ck9l9"></a>

<p align="center"><kbd><img src="assets/86397ny8scr.png" width="80%"></kbd></p>

<br>

<a id="node-ow0x20v"></a>

<p align="center"><kbd><img src="assets/vw6fk7hwnbn.png" width="80%"></kbd></p>

<br>

<a id="node-da0s9sd"></a>

#### N.n

<br>

<a id="node-ure777b"></a>

##### Foward Prop

<br>

<a id="node-te2u2nn"></a>

<p align="center"><kbd><img src="assets/hahby5rduy9.png" width="80%"></kbd></p>

<br>

<a id="node-dvpkchf"></a>

<p align="center"><kbd><img src="assets/a5idcq7g2p7.png" width="80%"></kbd></p>

<br>

<a id="node-th1do4h"></a>

<p align="center"><kbd><img src="assets/y5oki7bytm.png" width="80%"></kbd></p>

<br>

<a id="node-0zhnml9"></a>

<p align="center"><kbd><img src="assets/4zxcezon6p7.png" width="80%"></kbd></p>

<br>

<a id="node-jlkyd5g"></a>

<p align="center"><kbd><img src="assets/l7fjghdcylk.png" width="80%"></kbd></p>

<br>

<a id="node-rmmdgtb"></a>

##### Backward Prop

<br>

<a id="node-7856xam"></a>

<p align="center"><kbd><img src="assets/716a1hbuvht.png" width="80%"></kbd></p>

<br>

<a id="node-fcnpyuy"></a>

<p align="center"><kbd><img src="assets/sedx1dgv2c.png" width="80%"></kbd></p>

<br>

<a id="node-0x2x2ou"></a>

<p align="center"><kbd><img src="assets/1bjfpzp81np.png" width="80%"></kbd></p>

<br>

<a id="node-vl9pkwp"></a>

<p align="center"><kbd><img src="assets/camzhvk3ke4.png" width="80%"></kbd></p>

<br>

<a id="node-ibi7fb2"></a>

<p align="center"><kbd><img src="assets/l7hsqqpatj9.png" width="80%"></kbd></p>

<br>

<a id="node-lujdsuf"></a>

## Ian Goodfellow

<br>

<a id="node-3amorml"></a>

<p align="center"><kbd><img src="assets/q0vremed5x8.png" width="80%"></kbd></p>

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

