# C1w4_deep Neural Network

📊 **Progress:** `21` Notes | `95` Screenshots

---
<a id="node-2bu7cf4"></a>

## C1w4_deep Neural Network

<br>

<a id="node-1azrys7"></a>

## Deep L-layer Neural Network

<br>

<a id="node-zsdgtgd"></a>

> [!NOTE]
> 1 By the fourth week of the course, students have learned about forward propagation and
> back propagation in the context of a neural network, as well as logistic regression,
> vectorization, and the importance of random weight initialization.
>
> 2 With this foundational knowledge, the focus of the fourth week is on putting these ideas
> together to implement a deep neural network.
>
> 3 A deep neural network is a neural network with multiple hidden layers, as opposed to a
> shallow model like logistic regression, which is a one-layer neural network.  4 The number
> of hidden layers in a neural network is a matter of degree and can vary depending on the
> problem at hand. While there is no easy way to predict the ideal depth for a network, it is
> common to try different values and evaluate their performance on a development set or
> across validation data.
>
> 5 Notation is used to describe the architecture and activations of deep neural networks.
> Specifically, L denotes the number of layers, and N superscript [l] denotes the number of
> nodes in layer l. a[l] denotes the activations in layer l, and W[l] and b[l] are used to
> compute the value of z[l] in layer l.
>
> 6 x represents the input features, as well as the activations of layer zero, while a[L]
> represents the predicted output or y-hat of the neural network.
>
> 7 The course website provides a notation sheet or guide that students can refer to if they
> forget what a particular symbol or term means.
>
> 8 In the next video, the course will go into more detail about what forward propagation
> looks like in a deep neural network.

<br>

<a id="node-l5k93hl"></a>

<p align="center"><kbd><img src="assets/c076o3nnu3.png" width="80%"></kbd></p>

<br>

<a id="node-fdhaakd"></a>

## Forward Propagation In Deep Network

<br>

<a id="node-c1fd4xy"></a>

> [!NOTE]
> 1 The video discusses the process of forward propagation in a deep L-layer neural
> network using a single training example, followed by the vectorized version, where
> forward propagation is carried out on the entire training set.
>
> 2 The activations for layer one are computed using the formula z1 = w1*x + b1 and a1
> = g(z1), where w1 and b1 are the parameters affecting the activations in layer one and
> g is the activation function for layer one.
>
> 3 The activations for subsequent layers are computed in a similar way, using the
> activation values from the previous layer, until the activations for the final layer, layer L,
> are computed, giving the estimated output y hat.
>
> 4 The forward propagation equation for a single training example is generalized as zl =
> wl*a(l-1) + bl, where a0 = x and a(l-1) is the activation value from the previous layer.
>
> 5 The vectorized version of forward propagation involves stacking the vectors z and a
> for all training examples and carrying out the same computations using matrix
> multiplication.
>
> 6 The video recommends using a for loop to compute activations for all layers in a deep
> neural network, as it is difficult to implement it without one.
>
> 7 Understanding matrix dimensions is crucial when implementing a deep neural
> network to minimize bugs and ensure correct implementation.

<br>

<a id="node-kd3v37c"></a>

<p align="center"><kbd><img src="assets/ilenufp0ni.png" width="80%"></kbd></p>

> [!NOTE]
> Vẫn phải for loop cho các l = 1-L. Không có cách nào khác.

<br>

<a id="node-13jgq2z"></a>

## Getting Your Matrix Dimension Rights

<br>

<a id="node-unxpm9q"></a>

> [!NOTE]
> 1 One debugging tool to check the correctness of deep neural network implementation
> is to work through the dimensions of the matrices involved.
>
> 2 The dimensions of the weight matrix, W, is determined by the number of hidden units
> in the current and previous layer. The dimensions of the bias vector, B, is equal to the
> number of hidden units in the current layer.
>
> 3 The activation vector, Z, for each layer is a vector of dimension equal to the number of
> hidden units in that layer.
>
> 4 For input features, x, and activation vector, Z, to have the same dimension, the weight
> matrix, W, must have dimensions equal to the number of hidden units in the current
> layer by the number of features or hidden units in the previous layer.
>
> 5 In vectorized implementation, the dimensions of Z and X will change, but the
> dimensions of W and B will remain the same.
>
> 6 The dimensions of dw and db, the gradients of the weight and bias, respectively,
> should be the same as the dimensions of W and B.

<br>

<a id="node-x6lvv5k"></a>

<p align="center"><kbd><img src="assets/ssqgue7a08.png" width="80%"></kbd></p>

<br>

<a id="node-wqip6pq"></a>

<p align="center"><kbd><img src="assets/tdjg519tfzm.png" width="80%"></kbd></p>

<br>

<a id="node-deuy7nr"></a>

## Why Deep Representations?

<br>

<a id="node-0lkd0a9"></a>

> [!NOTE]
> 1 Deep neural networks are effective for many problems and require a lot of
> hidden layers.
>
> 2 The first layer of a neural network is typically a feature detector or edge
> detector for images.
>
> 3 The neural network looks for simple things like edges and then composes
> them in later layers to learn more complex functions.
>
> 4 This simple-to-complex hierarchical representation applies to other types of
> data like speech recognition.
>
> 5 Deep neural networks can detect surprisingly complex things, like faces or
> phrases, despite computing seemingly simple functions.
>
> 6 The circuit theory suggests that deep neural networks can compute more
> functions than shallow networks.
>
> 7 Deep learning draws loose inspiration from the way the human brain detects
> simple things and builds them up into more complex objects.

<br>

<a id="node-nzbf8o0"></a>

<p align="center"><kbd><img src="assets/twrxmzh3oy7.png" width="80%"></kbd></p>

<br>

<a id="node-2lbh2g9"></a>

<p align="center"><kbd><img src="assets/7dd2rxy96tu.png" width="80%"></kbd></p>

> [!NOTE]
> Có nghĩa là với 1 simple L-layer network thì shallower network
> phải có số hidden unit gấp nhiều lần theo cấp luỹ thừa thì mới
> sánh bằng

<br>

<a id="node-v2nzvw3"></a>

## Building Blocks Of Deep Neural Networks

<br>

<a id="node-q479jdz"></a>

> [!NOTE]
> 1 Deep neural networks can be built by putting together the building blocks of
> forward propagation and backpropagation.
>
> 2 Each layer has parameters (weights and biases) that are used in the forward
> propagation step to compute activations of that layer and in the backward
> propagation step to compute derivatives with respect to the parameters and
> activations of the previous layer.
>
> 3 Forward propagation involves feeding input features through the network
> and computing activations for each layer using its parameters and activations
> from the previous layer. These activations are cached for later use in the
> backward propagation step.
>
> 4 Backward propagation involves computing derivatives with respect to the
> parameters and activations of each layer, starting from the output layer and
> going backwards to the input layer. These derivatives are used to update the
> parameters of the network in order to minimize a cost function.
>
> 5 Each iteration of training through a neural network involves one forward
> propagation step followed by one backward propagation step.

<br>

<a id="node-cmaameo"></a>

<p align="center"><kbd><img src="assets/tv5ke10qzz.png" width="80%"></kbd></p>

<br>

<a id="node-j5iqkpd"></a>

<p align="center"><kbd><img src="assets/tcc6xk13nah.png" width="80%"></kbd></p>

<br>

<a id="node-j5w1z7h"></a>

## Forward And Backward Propagation

<br>

<a id="node-e9bhiag"></a>

> [!NOTE]
> 1 Recap of the basic building blocks of implementing a deep neural network:
> forward propagation and backward propagation.
>
> 2 Forward propagation involves inputting a^l-1 and outputting a^l and the cache,
> z^l. The activation function is applied to z^l, and if a vectorized implementation is
> used, b is Python broadcasting and a^l is g applied element-wise to z.
>
> 3 The forward function is initialized with a^0, which is the input features for one
> training example or the input features for the entire training set.
>
> 4 Backward propagation involves inputting da^l and outputting da^l-1, dw^l, and
> db^l.
>
> 5 The equations for computing these derivatives are dz^l = da^l * g^l prime(z^l),
> dw^l = dz^l * a^l-1, db^l = dz^l, and da^l-1 = w^l transpose * dz^l.
>
> 6 A vectorized implementation of the backward function involves dz^l = da^l * g^l
> prime(z^l), dw^l = 1/m * dz^l * a^l-1 transpose, db^l = 1/m * np.sum(dz^l, axis=1,
> keepdims=True), and da^l-1 = w^l transpose * dz^l.
>
> 7 The output y-hat is used to compute the loss, which allows for backward
> iteration to compute the derivatives.
>
> 8 The backward recursion is initialized with da^l, which is equal to y/a + (1-y)/(1-a)
> for binary classification.
>
> 9 To implement forward propagation and backward propagation for a three-layer
> neural network, the input data x is initialized for the forward recursion and da^2
> and da^1 are passed backwards for the backward recursion.

<br>

<a id="node-3c9l1n5"></a>

<p align="center"><kbd><img src="assets/kt1ampxtqna.png" width="80%"></kbd></p>

<br>

<a id="node-kkt0wpe"></a>

<p align="center"><kbd><img src="assets/zj2dyhz9vgi.png" width="80%"></kbd></p>

<br>

<a id="node-7x0pp8g"></a>

<p align="center"><kbd><img src="assets/frfr3wlom1h.png" width="80%"></kbd></p>

<br>

<a id="node-e6vzrqn"></a>

<p align="center"><kbd><img src="assets/fvzq78bh1x9.png" width="80%"></kbd></p>

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

<a id="node-ljqq4b2"></a>

## Parameters Vs Hyperparams

<br>

<a id="node-na2yts6"></a>

> [!NOTE]
> 1 Developing deep Neural Nets requires organizing not only parameters, but
> also hyper parameters.
>
> 2 Hyper parameters include the learning rate alpha, number of iterations,
> number of hidden layers, number of hidden units, activation function,
> momentum term, mini-batch size, and regularization parameters.
>
> 3 Hyper parameters control the ultimate parameters W and B.
>
> 4 Deep learning is an intricate process that involves trying out different hyper
> parameter settings.
>
> 5 Applying deep learning is an empirical process that involves trying out many
> different values and seeing what works.
>
> 6 There are systematic ways to try out a range of values for hyper parameters.
>
> 7 The best value for hyper parameters might change over time, even if working
> on the same problem.

<br>

<a id="node-1vv0rsw"></a>

<p align="center"><kbd><img src="assets/bseit3s81wj.png" width="80%"></kbd></p>

<br>

<a id="node-d9bge0y"></a>

<p align="center"><kbd><img src="assets/3s1oypv67kn.png" width="80%"></kbd></p>

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

<a id="node-o3ghp3r"></a>

## Deep Learning & Brain

<br>

<a id="node-e9w9v0z"></a>

> [!NOTE]
> The article discusses the loose analogy between deep learning and the
> human brain. While the structure of a neural network may resemble a
> biological neuron, the complexity of a single neuron is far greater than
> what is currently understood. There is still much unknown about how the
> brain learns and whether it uses similar algorithms to backpropagation
> and gradient descent. The author notes that the analogy between deep
> learning and the brain may have been useful in the past, but as the field
> has progressed, it is breaking down. Finally, the author provides a
> summary of the video, which covers how to implement forward and
> backpropagation in deep neural networks.

<br>

<a id="node-0vcomxn"></a>

<p align="center"><kbd><img src="assets/bcwex0ej1nu.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó giông giống neuron thôi chứ hiện giờ ngay cả
> neuroscientist cũng chưa hiểu Neuron nó hoạt động, học như thế
> nào

<br>

<a id="node-1p30j92"></a>

## Quiz: Key Concepts On Deep Neural Network

<br>

<a id="node-2ru8083"></a>

<p align="center"><kbd><img src="assets/southitjpb9.png" width="80%"></kbd></p>

<br>

<a id="node-9hz0kqh"></a>

<p align="center"><kbd><img src="assets/n63111pnkg.png" width="80%"></kbd></p>

<br>

<a id="node-eqxuo54"></a>

<p align="center"><kbd><img src="assets/rm0osboj4q9.png" width="80%"></kbd></p>

<br>

<a id="node-ooxefcq"></a>

<p align="center"><kbd><img src="assets/vzld2otuuno.png" width="80%"></kbd></p>

> [!NOTE]
> Đánh nhầm

<br>

<a id="node-ocos4hq"></a>

<p align="center"><kbd><img src="assets/7bp8k89rqs4.png" width="80%"></kbd></p>

<br>

<a id="node-s7dp7s6"></a>

<p align="center"><kbd><img src="assets/d3y7ka8h7jl.png" width="80%"></kbd></p>

<br>

<a id="node-gd6j8eo"></a>

<p align="center"><kbd><img src="assets/xl0crxi3mbh.png" width="80%"></kbd></p>

<br>

<a id="node-okjcwcs"></a>

<p align="center"><kbd><img src="assets/qt19ea3x2l.png" width="80%"></kbd></p>

<br>

<a id="node-b5c0hiz"></a>

<p align="center"><kbd><img src="assets/d17y4w0b3ph.png" width="80%"></kbd></p>

<br>

<a id="node-dstnswo"></a>

<p align="center"><kbd><img src="assets/qv1nic6vgtk.png" width="80%"></kbd></p>

<br>

<a id="node-b7wxwda"></a>

<p align="center"><kbd><img src="assets/18jpx12gh6f.png" width="80%"></kbd></p>

<br>

<a id="node-wcjecsw"></a>

## Programming Assignments: Build Your Deep Neural Network: Step By Step

<br>

<a id="node-voz1p3w"></a>

### 1 - Packages

<br>

<a id="node-emacxba"></a>

<p align="center"><kbd><img src="assets/8k25apckprq.png" width="80%"></kbd></p>

<br>

<a id="node-2gprfxq"></a>

<p align="center"><kbd><img src="assets/yui0h8qaou.png" width="80%"></kbd></p>

<br>

<a id="node-ty2tz4z"></a>

### 2 - Outline

<br>

<a id="node-m3gmoog"></a>

<p align="center"><kbd><img src="assets/zml8mwzavhq.png" width="80%"></kbd></p>

<br>

<a id="node-fergjfz"></a>

<p align="center"><kbd><img src="assets/w9sjbevrrin.png" width="80%"></kbd></p>

<br>

<a id="node-zrivkjq"></a>

<p align="center"><kbd><img src="assets/b3hqk5zgij7.png" width="80%"></kbd></p>

<br>

<a id="node-f7c8ljv"></a>

### 3 - Initialization

<br>

<a id="node-q2pmpar"></a>

#### 3.1 - 2-layer Neural Network

<br>

<a id="node-3rjze9t"></a>

<p align="center"><kbd><img src="assets/usqk5l6zam.png" width="80%"></kbd></p>

<br>

<a id="node-kqt9wag"></a>

<p align="center"><kbd><img src="assets/c0qoh4h2ewj.png" width="80%"></kbd></p>

<br>

<a id="node-8nl70li"></a>

<p align="center"><kbd><img src="assets/javqdjo2hrn.png" width="80%"></kbd></p>

<br>

<a id="node-u1t1rrv"></a>

#### 3.2 - L-layer Neural Network

<br>

<a id="node-rpftaix"></a>

<p align="center"><kbd><img src="assets/fz32w2m2snc.png" width="80%"></kbd></p>

<br>

<a id="node-9jutauf"></a>

<p align="center"><kbd><img src="assets/2e88x0u0p5o.png" width="80%"></kbd></p>

<br>

<a id="node-jze1cgb"></a>

<p align="center"><kbd><img src="assets/u39svr360pq.png" width="80%"></kbd></p>

<br>

<a id="node-membnvp"></a>

<p align="center"><kbd><img src="assets/yzi06pkkajf.png" width="80%"></kbd></p>

<br>

<a id="node-ubduuyg"></a>

### 4 - Forward Propagation Module

<br>

<a id="node-9h6mnx8"></a>

#### 4.1 - Linear Forward

<br>

<a id="node-4rabgux"></a>

<p align="center"><kbd><img src="assets/hc1ve618ou.png" width="80%"></kbd></p>

<br>

<a id="node-4gvhga8"></a>

<p align="center"><kbd><img src="assets/kblt6oqo.png" width="80%"></kbd></p>

<br>

<a id="node-ittezxp"></a>

<p align="center"><kbd><img src="assets/sv15pil1dz.png" width="80%"></kbd></p>

<br>

<a id="node-ugwh356"></a>

#### 4.2 - Linear-Activation Forward

<br>

<a id="node-igor7he"></a>

<p align="center"><kbd><img src="assets/hiwz2uv841t.png" width="80%"></kbd></p>

<br>

<a id="node-z12pmt8"></a>

<p align="center"><kbd><img src="assets/i3eksoptvp.png" width="80%"></kbd></p>

<br>

<a id="node-di9fmki"></a>

<p align="center"><kbd><img src="assets/00leqarz9i808.png" width="80%"></kbd></p>

<br>

<a id="node-8c4cab2"></a>

<p align="center"><kbd><img src="assets/q4gl8lpp7gc.png" width="80%"></kbd></p>

<br>

<a id="node-mzqz97u"></a>

#### 4.3 - L-Layer Model

<br>

<a id="node-3t0zhnq"></a>

<p align="center"><kbd><img src="assets/q1ssfm1j8b9.png" width="80%"></kbd></p>

<br>

<a id="node-vo5ouyd"></a>

<p align="center"><kbd><img src="assets/nefn25i5xs.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/mttzeglmscb.png" width="80%"></kbd></p>

> [!NOTE]
> for l in range(1, L) -> l = 1,2...L-1

<br>

<a id="node-qq8k410"></a>

<p align="center"><kbd><img src="assets/akvmbdu6jiw.png" width="80%"></kbd></p>

<br>

<a id="node-1zo1tb6"></a>

### 5 - Cost Function

<br>

<a id="node-a2jmy7g"></a>

<p align="center"><kbd><img src="assets/pb72mdudiv.png" width="80%"></kbd></p>

<br>

<a id="node-w3o97cx"></a>

<p align="center"><kbd><img src="assets/f5735bwnco6.png" width="80%"></kbd></p>

<br>

<a id="node-to6rj4k"></a>

<p align="center"><kbd><img src="assets/34p4qfhn279.png" width="80%"></kbd></p>

<br>

<a id="node-v2lmp7p"></a>

### 6 - Backward Propagation Module

<br>

<a id="node-xa0hn2s"></a>

<p align="center"><kbd><img src="assets/3xuoxivbsh6.png" width="80%"></kbd></p>

<br>

<a id="node-3ywvl73"></a>

<p align="center"><kbd><img src="assets/prntwpk2wdg.png" width="80%"></kbd></p>

> [!NOTE]
> keepdims = True sẽ ngăn không để Python nó biến kết quả đang matrix 2D
> thành array vector 1D

<br>

<a id="node-1xk1phk"></a>

#### 6.1 - Linear Backward

<br>

<a id="node-ieatu22"></a>

<p align="center"><kbd><img src="assets/svoyi12nyzh.png" width="80%"></kbd></p>

<br>

<a id="node-ackvxp9"></a>

<p align="center"><kbd><img src="assets/tl5fjb70xr.png" width="80%"></kbd></p>

<br>

<a id="node-fm3sik7"></a>

<p align="center"><kbd><img src="assets/477bp2ya38y.png" width="80%"></kbd></p>

<br>

<a id="node-j0zbka3"></a>

#### 6.2 - Linear-Activation Backward

<br>

<a id="node-q6q4uxj"></a>

<p align="center"><kbd><img src="assets/lbbcra0n8zm.png" width="80%"></kbd></p>

<br>

<a id="node-8q9ir1n"></a>

<p align="center"><kbd><img src="assets/fw6fcenfi7a.png" width="80%"></kbd></p>

<br>

<a id="node-rk66p17"></a>

#### 6.3 - L-Model Backward

<br>

<a id="node-xb08m7x"></a>

<p align="center"><kbd><img src="assets/rhf77jgrgxq.png" width="80%"></kbd></p>

<br>

<a id="node-ymdbbuu"></a>

<p align="center"><kbd><img src="assets/t1a8n25npxc.png" width="80%"></kbd></p>

<br>

<a id="node-0g0g8nw"></a>

<p align="center"><kbd><img src="assets/t2qm1rw3cue.png" width="80%"></kbd></p>

<br>

<a id="node-oczbe93"></a>

<p align="center"><kbd><img src="assets/6yjt0g8wsam.png" width="80%"></kbd></p>

<br>

<a id="node-c6qfrgf"></a>

#### 6.4 - Update Parameters

<br>

<a id="node-85gyxmq"></a>

<p align="center"><kbd><img src="assets/rg1hj5eee4p.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qtk3u3u05yd.png" width="80%"></kbd></p>

<br>

<a id="node-5ctk2di"></a>

<p align="center"><kbd><img src="assets/g3wcm7qc2o.png" width="80%"></kbd></p>

<br>

<a id="node-keh3ogt"></a>

<p align="center"><kbd><img src="assets/lx77chocpme.png" width="80%"></kbd></p>

<br>

<a id="node-h1f4ovd"></a>

> [!NOTE]
> TÓM LƯỢC QUY
> TRÌNH CHO DỄ HIỂU

<br>

<a id="node-iv5pc9i"></a>

<p align="center"><kbd><img src="assets/vmk6fw4wvf.png" width="80%"></kbd></p>

<br>

<a id="node-qpdfb9p"></a>

<p align="center"><kbd><img src="assets/3d74mld4c6r.png" width="80%"></kbd></p>

<br>

<a id="node-85gtocl"></a>

<p align="center"><kbd><img src="assets/grunlm0y6hq.png" width="80%"></kbd></p>

<br>

<a id="node-pv3muoz"></a>

## Programming Assignment: Deep Neural Network - Application

> [!NOTE]
> Build and train a deep L-layer neural network, and apply it to 
> the very important problem of classifying cat images from 
> non-cat images.  :)

<br>

<a id="node-0qcbs95"></a>

### 1 - Packages

<br>

<a id="node-3tqqyw0"></a>

<p align="center"><kbd><img src="assets/hkzwyqr8mst.png" width="80%"></kbd></p>

<br>

<a id="node-fvfuwlh"></a>

### 2 - Load and Process the Dataset

<br>

<a id="node-77vhrv8"></a>

<p align="center"><kbd><img src="assets/00f481jewdmze.png" width="80%"></kbd></p>

<br>

<a id="node-jzt0grp"></a>

<p align="center"><kbd><img src="assets/r5g6da951uq.png" width="80%"></kbd></p>

<br>

<a id="node-yjit9ae"></a>

<p align="center"><kbd><img src="assets/m6iheova8b.png" width="80%"></kbd></p>

<br>

<a id="node-ogng7d2"></a>

### 3 - Model Architecture

<br>

<a id="node-cyb1pbq"></a>

#### 3.1 - 2-layer Neural Network

<br>

<a id="node-9u4d43q"></a>

<p align="center"><kbd><img src="assets/a4swjr0bkyh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/87dhviclrim.png" width="80%"></kbd></p>

<br>

<a id="node-zhwthd7"></a>

#### 3.2 - L-layer Deep Neural Network

<br>

<a id="node-dtfqb5q"></a>

<p align="center"><kbd><img src="assets/k7wwc62l3d.png" width="80%"></kbd></p>

<br>

<a id="node-1b2xn7a"></a>

#### 3.3 - General Methodology

<br>

<a id="node-n95ww1k"></a>

<p align="center"><kbd><img src="assets/tj95w40j99s.png" width="80%"></kbd></p>

<br>

<a id="node-8adxwlu"></a>

### 4 - Two-layer Neural Network

<br>

<a id="node-r4wr1pa"></a>

#### Exercise 1 - two_layer_model

<br>

<a id="node-b3j5hd2"></a>

<p align="center"><kbd><img src="assets/dillcatvjit.png" width="80%"></kbd></p>

<br>

<a id="node-pa1rt2h"></a>

<p align="center"><kbd><img src="assets/4ahd83j2kp7.png" width="80%"></kbd></p>

<br>

<a id="node-ro9c42g"></a>

<p align="center"><kbd><img src="assets/f7jngzlwnde.png" width="80%"></kbd></p>

<br>

<a id="node-r47u9rt"></a>

<p align="center"><kbd><img src="assets/2p8i8tflwq4.png" width="80%"></kbd></p>

<br>

<a id="node-8bhxefq"></a>

<p align="center"><kbd><img src="assets/q17noaavntf.png" width="80%"></kbd></p>

<br>

<a id="node-0b8yg4a"></a>

#### 4.1 - Train the model

<br>

<a id="node-ogllk7p"></a>

<p align="center"><kbd><img src="assets/otz8q8a1nz.png" width="80%"></kbd></p>

<br>

<a id="node-mob02k5"></a>

<p align="center"><kbd><img src="assets/98b25oh0cow.png" width="80%"></kbd></p>

<br>

<a id="node-rckssw2"></a>

<p align="center"><kbd><img src="assets/m29v7xwq3k.png" width="80%"></kbd></p>

> [!NOTE]
> Note: You may notice that running the model on fewer iterations (say
> 1500) gives better accuracy on the test set. This is called **"early
> stopping"** and you'll hear more about it in the next course. Early stopping
> is a way to prevent overfitting.

<br>

<a id="node-ed2o09q"></a>

### 5 - L-layer Neural Network

<br>

<a id="node-q3ttt9n"></a>

#### Exercise 2 - L_layer_model

<br>

<a id="node-e82u1z2"></a>

<p align="center"><kbd><img src="assets/ibixkglbpe.png" width="80%"></kbd></p>

<br>

<a id="node-g2dhg7z"></a>

<p align="center"><kbd><img src="assets/7tou8cln9j.png" width="80%"></kbd></p>

<br>

<a id="node-8ivxugu"></a>

<p align="center"><kbd><img src="assets/r4nyj9kom5i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gfhsbhoscor.png" width="80%"></kbd></p>

<br>

<a id="node-o528027"></a>

#### 5.1 - Train the model

<br>

<a id="node-qij9rzs"></a>

<p align="center"><kbd><img src="assets/tfovu25tjfi.png" width="80%"></kbd></p>

<br>

<a id="node-puq9m7k"></a>

<p align="center"><kbd><img src="assets/p9rr0m7smb.png" width="80%"></kbd></p>

> [!NOTE]
> In the next course on "Improving deep neural networks," you'll be 
> able to obtain even higher accuracy by systematically 
> **searching for better hyperparameters: learning_rate, 
> layers_dims, or num_iterations, for example.**

<br>

<a id="node-0h5vsqc"></a>

### 6 - Results Analysis

<br>

<a id="node-kuaeyyc"></a>

<p align="center"><kbd><img src="assets/y2br4fzxfo.png" width="80%"></kbd></p>

<br>

<a id="node-6e4pxib"></a>

### 7 - Test with your own image (optional/ungraded exercise)

<br>

<a id="node-uspqs4d"></a>

<p align="center"><kbd><img src="assets/tnm4a2jd3y.png" width="80%"></kbd></p>

<br>

<a id="node-exvhusl"></a>

<p align="center"><kbd><img src="assets/11wqns7s9p4.png" width="80%"></kbd></p>

<br>

<a id="node-f4al29v"></a>

## References

> [!NOTE]
> **Week 2:
>  • GitHub**: \_Implementing a Neural Network from Scratch in Python – An Introduction\_ (Denny Britz, 2015)
>  • \_Why normalize images by subtracting dataset's image mean, instead of the current image mean in deep learning?\_ (Stack Exchange)
> **Week 3:**
>  • \_CS231n: Convolutional Neural Networks for Visual Recognition\_ (Stanford University)
> **Week 4:**
> \_Autoreload of modules in IPython\_ (Stack Overflow)

<br>

