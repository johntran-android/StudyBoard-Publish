# Course 4 - Convolutional Neural Network

📊 **Progress:** `168` Notes | `478` Screenshots

---
<a id="node-5qel0v6"></a>

## Course 4 - Convolutional Neural Network

<br>

<a id="node-5qjhktj"></a>

## C4w1_foundations Of Convolutional Neural Network

<br>

<a id="node-p7qq66d"></a>

### Computer Vision

<br>

<a id="node-xnw5tjw"></a>

#### 1 \\*Computer vision\\* is rapidly advancing thanks to deep learning,
enabling new applications that were impossible a few years ago.

2 The computer vision research community's creativity and
inventiveness in coming up with new neural network architectures
and algorithms can inspire cross-fertilization into other areas.

3 Computer vision problems include \\*image classification\\*, \\*object
detection\\*, and \\*neural style transfer\\*, among others.

4 One of the challenges of computer vision problems is that the
\\*inputs can get really big\\*, requiring better implementation of the
\\*convolution operatio\\*n, which is one of the fundamental building
blocks of convolutional neural networks.

<br>

<a id="node-qhujfd3"></a>

<p align="center"><kbd><img src="assets/j785376y1a.png" width="80%"></kbd></p>

<br>

<a id="node-hhd63j3"></a>

<p align="center"><kbd><img src="assets/zcjzk8noy19.png" width="80%"></kbd></p>

> [!NOTE]
> ..

<br>

<a id="node-x7p6fvx"></a>

<p align="center"><kbd><img src="assets/xs0ulzhqhr.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu X là image size 1000x1000x3 -> X sẽ là 3 Millions features -> W[1]
> sẽ là 1000x3M = 3 tỉ cái weights: Quá lớn nên phải dùng 1 cái mới :
> Convolutional N.N

<br>

<a id="node-m86ynh9"></a>

### Edge Detection Example

<br>

<a id="node-wxwwgig"></a>

#### • The \\*convolution operation\\* is a fundamental building block of
\\*convolutional neural networks\\*.

• \\*Edge detection\\* is one of the many applications of the convolution
operation.

• \\*Early\\* layers of a neural network \\*detect\\* \\*edges\\* while \\*later layers\\*
detect \\*complete objects\\*.

• Convolution involves a \\*filter\\* or \\*kernel\\* being passed over an input
image to produce an output image.

• The output of the convolution operation is determined by taking
\\*element-wise products\\* and \\*summing\\* up the resulting values.

• The \\*output\\* of the convolution operation is \\*smaller\\* in size than the
\\*input\\* image.

<br>

<a id="node-h9k164q"></a>

<p align="center"><kbd><img src="assets/ak7njbufjc.png" width="80%"></kbd></p>

> [!NOTE]
> Để detect object - Thì đầu tiên là làm sao xác định (detect) được cái edge -
> đường viền, ranh giới của các object trước

<br>

<a id="node-olyrscn"></a>

<p align="center"><kbd><img src="assets/2g9bqi5akpj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ckdhjrsxlw.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/7bpsqr3eh12.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/2sdo6uy955k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/shs9inrwuj.png" width="80%"></kbd></p>

> [!NOTE]
> Filter or Kernel
>
>
>
> Ví dụ hình 6x6x1 (gray scale nên x1)
>
>
>
> * Trong toán học * là phép toán 'Convolution', trong Python thì
> lại là multiply, element-wised multiply

<br>

<a id="node-7lgv6q5"></a>

<p align="center"><kbd><img src="assets/6lhpn8yr4f3.png" width="80%"></kbd></p>

> [!NOTE]
> Turn out to be a '**EDGE** detector' sẽ thấy sau.
>
>
>
> Python: conv-forward
> TensorFlow: tf.nn.con2d
> Keras: Conv2D

<br>

<a id="node-dihuzq8"></a>

<p align="center"><kbd><img src="assets/z6xuclqfo2o.png" width="80%"></kbd></p>

> [!NOTE]
> In case the dimensions here seem a little bit wrong that the
> detected edge seems really thick, that's only because we are
> working with very small images in this example. And if you are
> using, say a 1000 by 1000 image rather than a 6 by 6 image then
> you find that this does a pretty good job, really detecting the vertical
> edges in your image
>
>
>
> Đại khái là bằng cách 'convol' với cái filter, sẽ cho ra kết quả
> 'detect' được cái '**edge**'. Ta thấy cái hình bên phải chính là cái 
> edge - đường viền đó.

<br>

<a id="node-exy33qa"></a>

### More Edge Detection

<br>

<a id="node-dibegty"></a>

#### 1 The video discusses \\*edge detection\\*, which is the process of
i\\*dentifying boundaries\\* in an image.

2 The video explains the \\*difference between positive and negative
edges\\* and how this is detected using edge detection filters.

3\\* Different edge detection filters\\* are discussed, including the three
by three filter for detecting vertical and horizontal edges, the \\*Sobel
filter\\*, and the \\*Scharr\\* filter.

4 The video highlights the possibility of using \\*machine learning\\* to
\\*learn the parameters of an edge detection filter\\*.

5 The \\*limitations of edge detection\\* in \\*small images\\* and the
\\*potential for deep learning to improve edge detection in complex
images\\* are also discussed.

<br>

<a id="node-upceqk8"></a>

<p align="center"><kbd><img src="assets/r0x6hly7zko.png" width="80%"></kbd></p>

> [!NOTE]
> 1 ví dụ cho thấy nếu ta 'flip' cái hình input thì cái edge sẽ màu dark thay vì
> light, và nếu ta không quan tâm màu thì ta có thể lấy giá trị tuyệt đối ||30|| =
> -||30|| = 30

<br>

<a id="node-i1z40f0"></a>

<p align="center"><kbd><img src="assets/bbd3jt0s8xr.png" width="80%"></kbd></p>

> [!NOTE]
> So in summary, different filters allow you to
> find vertical and horizontal edges.

<br>

<a id="node-izg7vmv"></a>

<p align="center"><kbd><img src="assets/lca1bkfhzq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cái matrix filter để dùng cho viêc edge detection này
> như cái ở trên [1 1 1 0 0 0 ..] có thể có những kiểu khác với các
> tên khác nhau có người thích dùng cái. [1 2 1..] gọi là **Sobel** filter, a
> little bit better có nguời thấy [3 10 3..] tốt hơn gọi là **Scharr** filter.
>
>
>
> Nhưng cái chính là **với N.N, máy tính nó sẽ học để cho ra cái filter
> sao cho giúp detect cái edge tốt nhất**, **có thể ra cái Sobel, hoặc
> thậm chí ra cái tốt hơn cả mấy cái đó.**
>
> Và không chỉ detect edge dọc,
> ngang mà cả đường chéo, 45 độ
> 70 độ v.v

<br>

<a id="node-eurpq6y"></a>

### Padding

<br>

<a id="node-b3nxusl"></a>

#### 1 \\*Padding\\* is a \\*modification\\* to the \\*basic convolutional operation\\* that can
help build \\*deep neural networks\\*.

2 A convolutional operation\\* reduces the size of the image.\\*

3 \\*Shrinking\\* the image too much may lead to \\*loss of information. \\*  

4 \\*Padding\\* is a solution to this problem as it \\*preserves\\* the size of the
image.

5 By padding the image, the output dimension increases by \\*2p\\* in each
direction.  

6 \\*Valid convolution \\*is a type of convolution that \\*doesn't use
padding.\\*

7 \\*Same convolution\\* is a type of convolution where the \\*output size\\* is the
\\*same\\* as the\\* input size\\*.

8 The amount of \\*padding\\* \\*required\\* to achieve the \\*same\\* convolution is
\\*(f-1)/2\\*, where \\*f is the size of the filter\\*.

<br>

<a id="node-6mhekgf"></a>

<p align="center"><kbd><img src="assets/lwtnoi4zd6b.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là để khắc phục 2 vấn đề là **'bị nhỏ dần' - shrinking output**
> và **'bỏ qua / ít dùng cái ở biên' sẽ khiến model bị bias đối với
> các info ở cạnh của input**  thì người ta dùng '**padding**'
>
>
>
> Có thể dùng padding p = 1, hoặc 2 ...

<br>

<a id="node-8cpd1yg"></a>

<p align="center"><kbd><img src="assets/q983bo0qjj.png" width="80%"></kbd></p>

> [!NOTE]
> **Valid padding** là không dùng padding 
>
>
>
> **Same padding** là sao cho output dimension bằng với input **p = (f-1)/2**
>
>
>
> Conventionally **f thường là số lẻ 3x3, 5x5, 7x7 để padding không bị
> asymmetric**
>
> Nếu có bối rối ko nhớ đc thì chỉ cần nhớ
> nếu không có padding thì thì từ n giảm xuống còn n - f + 1 
>
>
>
> Vậy muốn giữ nguyên thì + thêm f -1 nữa nên p = (f-1) /  2, 
> tại 2 bên quá dể nhớ

<br>

<a id="node-w2zt0fw"></a>

### Strided Convolutions

<br>

<a id="node-vmwq7ag"></a>

#### 1 \\*Strided\\* convolutions are a basic building block of Convolutional Neural
Networks.

2 A \\*strided\\* convolution involves taking an element-wise product of an
image and a filter, but \\*instead of stepping the filter by one\\*, it is stepped
by a \\*stride s.\\*

3 The output dimensions of the strided convolution are governed by the
formula: (N + 2P - F)/S + 1, where N is the input size, P is the padding, F
is the filter size, and S is the stride.

4 If the output dimensions are \\*not an integer\\*, they are \\*rounded down.\\*

5 The \\*convention\\* for convolutions is that the \\*filter\\* must \\*lie entirely\\* within
the image or the image plus padding region.

6 The difference between \\*convolution\\* and \\*cross-correlation\\* is that
convolution involves a flip of the filter on both axes before taking the
element-wise product and summing, while cross-correlation does not
involve this flip. However, the \\*deep learning literature\\* often r\\*efers to both
operations as convolutions.\\*

<br>

<a id="node-491rgul"></a>

<p align="center"><kbd><img src="assets/0p7f1qjvlbtn.png" width="80%"></kbd></p>

<br>

<a id="node-dflcvff"></a>

<p align="center"><kbd><img src="assets/sn1l96f4s27.png" width="80%"></kbd></p>

<br>

<a id="node-hoe0qth"></a>

<p align="center"><kbd><img src="assets/bzbse8cfira.png" width="80%"></kbd></p>

<br>

<a id="node-6a80qy3"></a>

<p align="center"><kbd><img src="assets/nl75by0g0q.png" width="80%"></kbd></p>

<br>

<a id="node-8z435un"></a>

<p align="center"><kbd><img src="assets/o72z3udqb6.png" width="80%"></kbd></p>

<br>

<a id="node-7oi9uwm"></a>

<p align="center"><kbd><img src="assets/6y4tg1lufwh.png" width="80%"></kbd></p>

<br>

<a id="node-8hyilvb"></a>

<p align="center"><kbd><img src="assets/lr0u5224j4.png" width="80%"></kbd></p>

> [!NOTE]
> Kí hiệu [z] (đúng hơn là chỉ có ngoặc ở dưới: Round down
> -> Nếu (n+2p-f)/s **không nguyên thì round down** - làm tròn xuống.
>
>
>
> Theo convention thì **filter phải nằm trọn trong image + padding** thì mới tính

<br>

<a id="node-lt3layv"></a>

<p align="center"><kbd><img src="assets/4hc5ux3t2ny.png" width="80%"></kbd></p>

> [!NOTE]
> Chọn s cho kết quả nguyên thì tốt không thì
> làm tròn cũng được

<br>

<a id="node-70463xk"></a>

<p align="center"><kbd><img src="assets/qlww62iq0nm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là đúng ra phải gọi là '**Cross-correlation**' chứ không phải
> convolution vì **trong toán học** phép convolution yêu cầu phải **flip** cái matrix
> filter horizontally và vertically trước.
>
>
>
> Điều này sẽ giúp phép toán convolution có tính chất (A*B)*C = A*(B*C)
> gọi là **associativity** nhưng trong Deep learning thì cái này không giúp ích
> gì mấy nên người ta cứ gọi là Convolution mà không cần phải flip để cho
> đơn giản

<br>

<a id="node-3ehjspg"></a>

### Convolutions Over Volume

<br>

<a id="node-nyiwwie"></a>

#### • \\*3D convolution\\* can be used to \\*detect features\\* in
3D volumes.

• \\*Filters\\* are placed in the volume and multiplied with
corresponding values from the color channels to
produce an output volume.

• \\*Different parameters\\* can be used to create \\*different
feature detectors\\*.

• \\*Multiple filters\\* can be used at the same time to
detect \\*multiple types of features\\* (more complex features)

<br>

<a id="node-b381q82"></a>

<p align="center"><kbd><img src="assets/h9dt4kalvpw.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cũng convol từng **'lớp' của filter
> với từng 'lớp'** của cái image Xong rồi
> **sum** **kết quả của cả 3 lớp lại**

<br>

<a id="node-9juavzm"></a>

<p align="center"><kbd><img src="assets/1te3eiltca6.png" width="80%"></kbd></p>

<br>

<a id="node-2cnh3bk"></a>

<p align="center"><kbd><img src="assets/zts9l34waai.png" width="80%"></kbd></p>

<br>

<a id="node-85t9cws"></a>

<p align="center"><kbd><img src="assets/ols26u9oulc.png" width="80%"></kbd></p>

> [!NOTE]
> Feature detector: Đại khái là các thay đổi giá trị của **params khác** (của
> filter) sẽ giúp **detect feature khác nhau** ví dụ sẽ quyết định được là "
> Chỉ detect edge with color RED", or "detect edge chung"
>
>
>
> Đại khái cũng chỉ nói lại việc thay đổi cái param - giá trị của cái  Filter sẽ
> giúp detect các pattern/feature khác nhau có điều filter bây h là 3D chứ
> ko chỉ 2D nên nó có thể detect nhiều pattern phức tạp hơn ví dụ như
> cũng đường viền nhưng mà đường viền màu này màu  kia nữa chứ
> không chỉ đường viền chung chung

<br>

<a id="node-uz7pnz1"></a>

<p align="center"><kbd><img src="assets/qgzva92ses7.png" width="80%"></kbd></p>

> [!NOTE]
> **Multiple features detector**: Đại khái là kết hợp nhiều filter sẽ **detect
> dc nhiều features cùng lúc** -> More complex features detector
>
>
>
> Mỗi filter ra 1 output xong **stack mấy cái output lại**

<br>

<a id="node-6gilq0w"></a>

### One Layer Of A Convolutional Network

<br>

<a id="node-w6kyo7m"></a>

#### 1 The video demonstrates how to build one layer of a convolutional neural
network using an example of \\*convolving a 3D volum\\*e with\\* two filters\\* to
produce different \\*4 by 4 outputs.\\*

2 The resulting outputs are passed through a \\*bias\\* and \\*non-linearity\\* to
produce a\\* 4 by 4 output\\* \\*for each filter,\\* which are then \\*stacked up\\* to form a
\\*4 by 4 by 2 output volume.\\*

3 The convolution operation is \\*similar to a linear operation\\* in a
non-convolutional neural network, where the \\*filters\\* play a \\*role similar to w1\\*
and the \\*output\\* of the convolution operation plays a role similar to \\*w1 times
a0.
\\*
4 One layer of a convolutional neural network can have \\*multiple filters,\\*
which can result in a \\*higher-dimensional output volume.\\*

5 To calculate the number of parameters in a layer with ten 3 by 3 by 3
filters, one needs to multiply the number of parameters per filter (28) by the
number of filters (10), resulting in 280 parameters.

<br>

<a id="node-g8uvhvj"></a>

<p align="center"><kbd><img src="assets/m2yau0ajt3g.png" width="80%"></kbd></p>

> [!NOTE]
> Giống như a[1] = w.a[0] + b thì
> filter đóng vai trò như w

<br>

<a id="node-vpgs9uo"></a>

<p align="center"><kbd><img src="assets/vo8qobaih1p.png" width="80%"></kbd></p>

> [!NOTE]
> 10 filter, mỗi cái 3x3x3 = 27
> params, thêm 1 cái bias là 28.
> Vậy tổng là 280 params

<br>

<a id="node-h1k5sgl"></a>

<p align="center"><kbd><img src="assets/t47cy1o020k.png" width="80%"></kbd></p>

> [!NOTE]
> Khái quát hoá nên có thể bối rối chỉ cần nhớ
>
>
>
> Muốn convol được thì **số lớp (bề dày, số channel) của filter phải bằng bề 
> dày của input** để convol xong nó gộp lại thành 1 channel
>
>
>
> Vậy input a[l-1] là nH [l-1] x nW [l-1] x **nC [l-1]** 
> thì filter cũng f [l] x f [l] x **nC [l-1]
>
>
>
> NHƯNG LAYER [l] CÓ NHIỀU FILTER = nC [l]
> nên mỗi kết quả từ mỗi filter stack lại thành ra nC [l] channel**
>
>
>
> nên output là a[l] sẽ (có shape) là nH [l] x nW [l] x nC [l]
>
>
>
> Và theo quan hệ của conv operation thì 
>
>
>
> nH [l] = [ n[H] [l-1] - f + 2*p [l] ] / s [l] + 1 (] là round-down)
> nW cũng vậy
>
>
>
> Tổng số weight layer [l] là: 
> (1 cái filter có f [l] x f [l] x nC [l-1] params) x nC [l] cái filter=f [l] x f [l] x nC [l-1]x nC [l] params

<br>

<a id="node-d1v92bx"></a>

### Simple Convolutional Network Example

<br>

<a id="node-r5ucoih"></a>

#### 1 Introduction to a deep convolutional neural network for
\\*image classification.\\*

2 Example of a \\*ConvNet\\* using small images.

3 Explanation of the \\*dimensions\\* and \\*number of filters\\* for
each convolutional layer.

4 \\*Flattening\\* the output of the \\*last convolutional layer\\* into a
vector for the final prediction.

5 The importance of \\*selecting\\* \\*hyperparameters\\* in designing
a convolutional neural network.

6 Upcoming guidelines and suggestions for \\*selecting
hyperparameters.\\*

<br>

<a id="node-neqpa0f"></a>

<p align="center"><kbd><img src="assets/wqfx8fad4fh.png" width="80%"></kbd></p>

<br>

<a id="node-gckzqio"></a>

<p align="center"><kbd><img src="assets/7zasvv8m80m.png" width="80%"></kbd></p>

> [!NOTE]
> Some note:
>
>
>
> Kết quả cuối (volume cuối) 7x7x40 sẽ được **flatten** thành 1 vector
> và bỏ vào **sigmoid** hay **softmax** để tính 
>
>
>
> Nhận thấy: **nC tăng dần** qua các layer 3-10-20-40, **nW, nH** **thì giảm dần**

<br>

<a id="node-w9s4zjy"></a>

<p align="center"><kbd><img src="assets/5hg0pt6194h.png" width="80%"></kbd></p>

> [!NOTE]
> Convolution thôi cũng được nhưng nó
> thường có thêm **pooling layer** và **FC** layer

<br>

<a id="node-8sqv07o"></a>

### Pooling Layers

<br>

<a id="node-gj5tkec"></a>

#### 1 ConvNets use \\*pooling layers\\* to \\*reduce representation size\\*, \\*increase speed\\*
and \\*make features more robust.\\*

2 \\*Max pooling\\* is a common type of pooling layer.

3 In max pooling, the input is divided into regions and the \\*output is the maximum
value of each region.\\*

4 The \\*hyperparameters\\* of max pooling are\\* filter size\\* and \\*stride\\*, which determine
the s\\*ize of the regions\\*.

5 Max pooling helps \\*preserve features detected anywhere in the filter\\*, while
\\*suppressing others that aren't detected\\*.

6 The intuition behind \\*why max pooling works well\\* is \\*not fully understood.\\*

7 Max pooling has \\*hyperparameters\\* but no parameters to learn, so it's a \\*fixed
computation.\\*

8 The formulas for figuring out the \\*output size\\* of convolutional layers also work
for max pooling.

9 Max pooling can be applied to \\*3D\\* \\*inputs and the output will have the same
dimension.\\*

<br>

<a id="node-86ukcnm"></a>

<p align="center"><kbd><img src="assets/a169vdc86ec.png" width="80%"></kbd></p>

> [!NOTE]
> /"Max pooling helps preserve features detected anywhere in
> the filter, while suppressing others that aren't detected." / Đại
> khái là max pooling giúp kiểu như giữ lại những gì (feature) nó
> phát hiện

<br>

<a id="node-rztuf5u"></a>

<p align="center"><kbd><img src="assets/povpankbgt.png" width="80%"></kbd></p>

> [!NOTE]
> Quan hệ tính size của input vào output cũng theo công thức 
> = round-down[ (n - f + 2p) / s ] + 1
>
>
>
> Và nếu là 3 channel thì output cũng có 3 channel
> (mỗi channel của filter sẽ 'tính'  với 1 channel của input)
> có điều khác với convol thường thì **pooling nó không gộp các
> channel kết quả lại** nên kết quả vẫn **giữ số channel** của input 
> (và của filter)

<br>

<a id="node-qj4fjyh"></a>

<p align="center"><kbd><img src="assets/7ni27vneifq.png" width="80%"></kbd></p>

<br>

<a id="node-owtbvz9"></a>

<p align="center"><kbd><img src="assets/ucte6abjgx.png" width="80%"></kbd></p>

<br>

<a id="node-3ccwn3v"></a>

### CNN Example

<br>

<a id="node-gy0qmmn"></a>

<p align="center"><kbd><img src="assets/xl4d1gdmati.png" width="80%"></kbd></p>

> [!NOTE]
> - Ở đây, và từ đây ổng sẽ ko viết cụ thể số filter
> của từng layer nữa mà tự hiểu rằng số channel
> của output chính là số filter
>
>
>
> Ví dụ từ 32x32x3 -> 28x28x**6** **tự hiểu có 6 filter,** size filter bao nhiêu
>  thì tính theo công thức. Nhẩm được thì nhẩm 
> 28 = (32 - f + 2*0)/1 + 1 -> f = ...
>
>
>
> - Layer 1 gồm 1 Conv và 1 Pool
> - Layer 2 cũng 1 Conv và 1 Pool
> - Rồi flatten rồi qua mấy cái Dense (Fully Connected) layer
> nữa cuối cùng là Softmax
>
>
>
> CONV-POOL-CONV-POOL-FC-FC-FC-SOFTMAX
>
>
>
> Cái mô hình này chính là **LeNet-5**

<br>

<a id="node-rm9p9kj"></a>

<p align="center"><kbd><img src="assets/q0cxknx0x2h.png" width="80%"></kbd></p>

<br>

<a id="node-0mvzgso"></a>

### Why Convolutions?

<br>

<a id="node-t603rlg"></a>

#### 1 Convolutional layers have \\*two main advantages\\* over fully
connected layers: \\*parameter sharing\\* and \\*sparsity of
connections.\\*

2 Convolutional layers have a lot\\* fewer parameters\\*, which
allows for \\*smaller training sets and less overfitting\\*.

3 Convolutional neural networks \\*capture translation invariance\\*,
which helps them \\*recognize objects regardless of their location\\*
in an image.

4 \\*Training\\* a convolutional neural network involves using a
\\*labeled training\\* set to \\*adjust the weights of the filters\\* to
produce accurate outputs.

<br>

<a id="node-qwqzl38"></a>

<p align="center"><kbd><img src="assets/a60t9unqjas.png" width="80%"></kbd></p>

<br>

<a id="node-oxcn9fa"></a>

<p align="center"><kbd><img src="assets/6d2p5zz61cn.png" width="80%"></kbd></p>

> [!NOTE]
> Thấy rõ đại khái là nếu là n.n thường thì số params sẽ rất lớn khi layer 1 có
> 3072 unit layer 2 có 4704 unit sẽ ra là **14 triệu params** trong khi ConvNet
> chỉ cần **156**

<br>

<a id="node-vsvbop2"></a>

<p align="center"><kbd><img src="assets/nbarspl0a38.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/djzn30l8dtp.png" width="80%"></kbd></p>

> [!NOTE]
> **Params sharing**: Đại khái là **1 vài weight (trong filter)** có
> thể giúp **detect feature ở nhiều vị trí khác nhau** trong hình
> chứ **không nhất thiết phải là mỗi chỗ một cái** -> **Giảm bớt
> số weight** cần thiết
>
>
>
> **Sparsity of connections**: Đại khái là:..
>
>
>
> Fully-connected NN thì **mỗi unit của layer trước** sẽ **connect
> tới mọi unit của layer sau,** cũng như là **mỗi unit của layer sau
> sẽ connect với mọi unit của layer trước** 
>
>
>
> Conv NN thì **mỗi output chỉ connect với một vài input
> thôi -** nhớ lại lúc tính thì mỗi số của là kết quả của phép tính
> convolution của 1 vài ô trong các channel thôi chứ không phải
> tất cả

<br>

<a id="node-1uqcez0"></a>

<p align="center"><kbd><img src="assets/cy9tykstn4w.png" width="80%"></kbd></p>

> [!NOTE]
> '**Translation invariance**' là tính chất của một mô hình hoặc một hệ thống
> có khả năng xử lý các đối tượng, hình ảnh, văn bản,... mà **không bị ảnh
> hưởng bởi vị trí tương đối giữa chúng** trong không gian hay thời gian.
>
>
>
> Nói cách khác, tính chất này cho phép mô hình hoặc hệ thống đó **nhận ra
> các đối tượng giống nhau dù chúng xuất hiện ở những vị trí khác nhau**
> trên màn hình hoặc thời gian.
>
>
>
> -> Đại khái là 1 hệ thống mà có tính chất 'translation invariance' như để
> detect hình con mèo trong một bức ảnh thì dù con mèo  xuất hiện ở đâu
> trong bức ảnh nó cũng detect được

<br>

<a id="node-7sranfl"></a>

- **7 Training a convolutional neural network

- Building a \\*labeled training\\* set for a specific task, such as identifying
images of cats and dogs.

- \\*Preprocessing\\* the \\*data\\* to \\*standardize\\* the \\*image size\\* and pixel values.

- \\*Defining the architecture\\* of the convolutional neural network, including the
\\*number\\* and\\* type of layer\\*s, \\*activation\\* functions, and \\*optimization\\* algorithm.

- \\*Initializing the weights \\*of the network and using \\*backpropagation\\* to \\*adjust
the weights\\* to \\*minimize the loss\\* between the \\*predicted\\* and actual labels.

- \\*Evaluating the performance\\* of the network on a \\*validation set\\* and
\\*adjusting the hyperparameters\\* as necessary.

- Finally, \\*testing the trained network\\* on a test set to \\*evaluate its
generalization performance.\\***

<br>

<a id="node-hxqvs7k"></a>

<p align="center"><kbd><img src="assets/gdta0soq9xm.png" width="80%"></kbd></p>

<br>

<a id="node-zbmkpas"></a>

### Quiz

<br>

<a id="node-4a9f9fs"></a>

<p align="center"><kbd><img src="assets/sa9hgnkv9h.png" width="80%"></kbd></p>

<br>

<a id="node-q9e6d45"></a>

<p align="center"><kbd><img src="assets/pp6c1d2sjzs.png" width="80%"></kbd></p>

<br>

<a id="node-87eq4im"></a>

<p align="center"><kbd><img src="assets/g890v0i72a7.png" width="80%"></kbd></p>

> [!NOTE]
> 3x3 = 9 (weights) + 1 (bias) = 10 x 128 (no. filters) = 1280

<br>

<a id="node-n5qrayz"></a>

<p align="center"><kbd><img src="assets/15vr6vpd1q3.png" width="80%"></kbd></p>

<br>

<a id="node-97xxdra"></a>

<p align="center"><kbd><img src="assets/1vsebeglrcc.png" width="80%"></kbd></p>

<br>

<a id="node-lmfeuly"></a>

<p align="center"><kbd><img src="assets/5ykb1fbro28.png" width="80%"></kbd></p>

> [!NOTE]
> Nhẩm rất nhanh (do s = 1 nên đỡ rối vụ chia s) là n sau
> khi cònv là 63 - 7+1 = 63 - 6 vậy padding phải bù lại để
> giữ nguyên 63 -> 2p = 6 => p = 3

<br>

<a id="node-p5s22sd"></a>

<p align="center"><kbd><img src="assets/a7vaiknsds6.png" width="80%"></kbd></p>

> [!NOTE]
> Nhẩm: channel vẫn là 12. 128 - 4 (f) / 4(s) =
> 31. Xong + 1 là 32 -> 32x32x12

<br>

<a id="node-2rcpexj"></a>

<p align="center"><kbd><img src="assets/93iynsrse6p.png" width="80%"></kbd></p>

<br>

<a id="node-z80ahtn"></a>

<p align="center"><kbd><img src="assets/c4vb35zqf54.png" width="80%"></kbd></p>

> [!NOTE]
> Cái ý đầu sai, vì hiển nhiên ta ko thể 'omit' - bỏ qua
> cái conv layer trong quá trình backprop
>
>
>
> Cái ý 3 transfer learning không chỉ có Conv mới có

<br>

<a id="node-yr75j9q"></a>

<p align="center"><kbd><img src="assets/t74im4fmn9.png" width="80%"></kbd></p>

<br>

<a id="node-x4n158v"></a>

### Programming Assignments: Convolutional Model

<br>

<a id="node-2fvhxhj"></a>

#### Be able to:  
• Explain the convolution operation

• Apply two different types of pooling operation

• Identify the components used in a convolutional
neural network (padding, stride, filter, ...) and their
purpose

• Build a convolutional neural network

> [!NOTE]
> Nói chung là làm những 'công việc' của
> convolution from scratch bằng numpy

<br>

<a id="node-02zn763"></a>

##### 1 - Packages:
Matplotlib, numpy

<br>

<a id="node-j3ejzkf"></a>

<p align="center"><kbd><img src="assets/xuy8i1ygji.png" width="80%"></kbd></p>

<br>

<a id="node-p41c142"></a>

##### 2 - Outline of the Assignment:
Đại khái là mô tả sơ những function sẽ làm cho 
Convolution n.n from scratch (bằng numpy)

Ổng nói dù những Framework như TS, PT bây giờ
giúp việc define ConvNet dể dàng nhưng việc hiểu nó
vẫn là quan trọng vì nó là một trong những khái niệm
khó của Deep Learning

 • \\*Convolution functions\\*, including:
 ▪ Zero Padding
 ▪ Convolve window
 ▪ Convolution forward
 ▪ Convolution backward (optional)
 • \\*Pooling functions\\*, including:
 ▪ Pooling forward
 ▪ Create mask
 ▪ Distribute value
 ▪ Pooling backward (optional)
Notebook sau sẽ dùng TensorFlow để làm những cái tương tự

<br>

<a id="node-3a6o1fr"></a>

<p align="center"><kbd><img src="assets/m7aopx7s72j.png" width="80%"></kbd></p>

> [!NOTE]
> Ổng nói dù những Framework như TS, PT bây giờ
> giúp việc define ConvNet dể dàng nhưng việc hiểu nó
> vẫn là quan trọng vì nó là một trong những khái niệm
> khó của Deep Learning

<br>

<a id="node-9is0hin"></a>

##### 3 - Convolutional
Neural Networks

<br>

<a id="node-qw6szch"></a>

- **3.0 - Convolutional
Neural Networks**

<br>

<a id="node-sfxz9m8"></a>

<p align="center"><kbd><img src="assets/qbysz6fcgf.png" width="80%"></kbd></p>

<br>

<a id="node-u5agaw8"></a>

- **3.1 - Zero-Padding:

Nhắc lại vai trò của padding trong việc giữ cho size
không bị giảm và  giúp thông tin tại edge của image
không bị ngó lơ / xem nhẹ**

<br>

<a id="node-qsnvpmp"></a>

<p align="center"><kbd><img src="assets/aicep2kq02c.png" width="80%"></kbd></p>

<br>

<a id="node-f3pkegl"></a>

- **Function zero_pad(X, pad) -> X_pad:

Code function zero_pad (X, pad) -> X_pad
dùng np.pad()
Mỗi data sample là 1 image -> dài x rộng x 3 (màu RGB) 
-> X = có m bộ - Do đó X có shape = m x n_h x n_w x n_c: n_c = 3
Trong python X.shape = (m, n_h, n_w, n_c)**

<br>

<a id="node-qsvxc5l"></a>

<p align="center"><kbd><img src="assets/n99ie93g2eq.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng function np.pad() của python bỏ
> vào X và chỉ định các dimension nào
> cần pad, pad bao nhiêu

<br>

<a id="node-lxzo7aj"></a>

<p align="center"><kbd><img src="assets/7h629vjqjhv.png" width="80%"></kbd></p>

<br>

<a id="node-7xvlt3b"></a>

<p align="center"><kbd><img src="assets/9c7ns5l5p35.png" width="80%"></kbd></p>

<br>

<a id="node-cxn3n1d"></a>

- **3.2 - Single Step of Convolution

Đại khái là bỏ filter lên 1 vị trí của input và tính để cho
ra 1 số. Thì phép tính này sẽ là phép tính element-wise
multiplication giữa 2 matrix (đúng hơn là 2 volume)
cùng size rồi sum lại.

Quá trình convol thì sẽ (slide window) đi và tính hết các
chỗ khác thì đây là 1 bước trong đó.

Nên hiểu là có n_C_prev channel luôn, nên đây là
phép tính trên 2 volume có size là f, f, n_C_prev

f là bề dài, rộng, n_C_prev là số channel (bề sâu / dầy)
của filter**

<br>

<a id="node-1sjdjrh"></a>

<p align="center"><kbd><img src="assets/5ob4asibbjj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bỏ filter lên 1 vị trí của input và tính để cho ra 1 số.
> Thì phép tính này sẽ là phép tính element-wise multiplication
> giữa 2 matrix (đúng hơn là 2 volume) cùng size rồi sum lại.
>
>
>
> Quá trình convol thì sẽ (slide window) đi và tính hết các chỗ khác
> thì đây là 1 bước trong đó.
>
>
>
> Nên hiểu là có n_C_prev channel luôn, nên đây là phép tính
> trên 2 volume có size là f, f, n_C_prev
>
>
>
> f là bề dài, rộng, n_C_prev là số channel (bề sâu / dầy) của filter

<br>

<a id="node-p65l9gt"></a>

<p align="center"><kbd><img src="assets/jq4nfna015n.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/58rrbkpbr0u.png" width="80%"></kbd></p>

<br>

<a id="node-pi9w8l0"></a>

- **Exercise 2 - conv_single_step(a_slice_prev,
W, b)

Đại khái là thực hiện 1 bước tính của phép
convol.

Dùng np.multiply để element-wised multiply

Chỉ có chú ý chỗ khi sum() nó trả về float luôn,
nhưng cộng với b (matrix (1,1,1) đang là
matrix thì nó thành matrix lại => Cast b thành
float trước bằng .item()**

<br>

<a id="node-kfe8qe4"></a>

<p align="center"><kbd><img src="assets/u4qn17ckan.png" width="80%"></kbd></p>

<br>

<a id="node-wbho4ug"></a>

<p align="center"><kbd><img src="assets/brjgrkyawe9.png" width="80%"></kbd></p>

<br>

<a id="node-dh7mw8z"></a>

- **3.3 - Convolutional Neural Networks - Forward Pass

Đại khái làm làm quá trình convol một input volume với
nhiều filter để Ra một output volume**

<br>

<a id="node-c76hnck"></a>

<p align="center"><kbd><img src="assets/gcte2ggnrya.png" width="80%"></kbd></p>

<br>

<a id="node-8gcy9wf"></a>

- **Exercise 3 - conv_forward: (...)

Nói chung là đây là function sẽ thực hiện việc convol một input
volume, với n_c filter để cho ra output volume

Quá trình làm ở lần đầu chưa hiểu lắm nhưng ở lần review thứ 1
thì thấy rõ ràng. Cũng nhờ hình vẽ minh hoạ phân tích kĩ ở lần học.
Những chỗ khó là những chỗ sai lần đầu làm :

- Loop trong số lần convol: Chính là nH và nW mà lúc đầu thấy bối
rối vì  chưa để ý rằng với công thức nH = ..nH_prev thì ta đã biết
được size của output thì từ đó chính là số bước convol cần tính.

- Lấy 1 'window' để convol, với các thông số vertical_start / end -
horizontal_start / end thì cũng không có gì khó hiểu khi nhìn lại
v_start chính là bằng h trong range nH * stride. Và end thì dễ rồi bằng
start + filter size f thôi.**

> [!NOTE]
> Sai hai chỗ:

<br>

<a id="node-b30n64p"></a>

<p align="center"><kbd><img src="assets/kwxeai0x9lo.png" width="80%"></kbd></p>

<br>

<a id="node-aci3s07"></a>

<p align="center"><kbd><img src="assets/cg543sbu5e.png" width="80%"></kbd></p>

<br>

<a id="node-jm4uuxx"></a>

<p align="center"><kbd><img src="assets/6kkigohwh15.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0wtsxs0ail0h.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/z1sg30ekcd.png" width="80%"></kbd></p>

<br>

<a id="node-tmj2cx4"></a>

<p align="center"><kbd><img src="assets/ijhribi7w6r.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/lp8bcmk1id.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6xnrldf4l6b.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/n6bneggdm2h.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4o7nbrodf7g.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/5bz6iwormhd.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/229s79hl2dx.png" width="80%"></kbd></p>

<br>

<a id="node-6ru0mxn"></a>

##### 4 - Pooling Layer

<br>

<a id="node-ycoufaf"></a>

- **4.1 - Forward Pooling

Làm conv_forward rồi thì cái này dễ hiểu thoi, chỉ
thay bằng bước convol bằng phép tính max,
mean**

> [!NOTE]
> Sai 1 chỗ

<br>

<a id="node-jn8hbtv"></a>

<p align="center"><kbd><img src="assets/pt33ii72edd.png" width="80%"></kbd></p>

<br>

<a id="node-7k56cf5"></a>

<p align="center"><kbd><img src="assets/6lztm6wh2a.png" width="80%"></kbd></p>

<br>

<a id="node-b4nerqr"></a>

<p align="center"><kbd><img src="assets/09gbqi8wou9k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/x1ilzwbprf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/u1c15j7qxv.png" width="80%"></kbd></p>

<br>

<a id="node-vb3p8x5"></a>

<p align="center"><kbd><img src="assets/opgopg0ry1.png" width="80%"></kbd></p>

<br>

<a id="node-5ni57z3"></a>

##### What you should
remember:

<br>

<a id="node-t60soz0"></a>

<p align="center"><kbd><img src="assets/ri72qtoaec.png" width="80%"></kbd></p>

<br>

<a id="node-ib89teu"></a>

##### 5 - Backpropagation in
Convolutional Neural Networks

> [!NOTE]
> Quay lại sau

<br>

<a id="node-hbpvm8e"></a>

- **5.1 - Convolutional Layer Backward Pass**

<br>

<a id="node-ypg3dwn"></a>

- **5.2 Pooling Layer - Backward Pass**

<br>

<a id="node-1s56e3i"></a>

### Programming Assignments: Convolutional Model Application

<br>

<a id="node-1ejajaf"></a>

#### Welcome to the second (required) programming exercise
of Course 4 of the Deep Learning Specialization.

In this notebook you will build ConvNets to create a
\\*mood classifier\\* and \\*identify sign language digits\\*,
while gaining familiarity with the \\*TF Keras Sequential\\*
and \\*Functional APIs\\* along the way.

<br>

<a id="node-vrmk2af"></a>

##### 1 - Packages

<br>

<a id="node-smob7sn"></a>

<p align="center"><kbd><img src="assets/tcd6m13837c.png" width="80%"></kbd></p>

<br>

<a id="node-zduxt0c"></a>

##### 1.1 - Load the Data and Split the
Data into Train/Test Sets

<br>

<a id="node-es4mqi7"></a>

<p align="center"><kbd><img src="assets/oj3jz2ld5lo.png" width="80%"></kbd></p>

<br>

<a id="node-eg53f0s"></a>

<p align="center"><kbd><img src="assets/0fky6r8fk2jl.png" width="80%"></kbd></p>

<br>

<a id="node-ovkl39t"></a>

##### 2 - Layers in TF Keras

<br>

<a id="node-uk881t3"></a>

<p align="center"><kbd><img src="assets/glncw4q1iz.png" width="80%"></kbd></p>

<br>

<a id="node-607d425"></a>

##### 3 - The Sequential API: Đại khái
là thay vì tự làm như bài trước,
nay ta dùng Framework TS
Keras's Sequential

<br>

<a id="node-ek9w1tm"></a>

<p align="center"><kbd><img src="assets/2f0xeb1lm6u.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây ổng có nói Sequential chỉ phù hợp cho
> simple và straightforward task còn muốn
> flexible hơn thì dùng Functional

<br>

<a id="node-0t9q0me"></a>

##### 3.1 - Create the Sequential Model: Đại
khái nó như một list các layer và khi work
thì nó sẽ lần lượt 'chạy' từng layer

<br>

<a id="node-2g31465"></a>

<p align="center"><kbd><img src="assets/rqr3m4j0n4k.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là Sequential phù hợp cho những
> structure đơn giản  chạy 1 lèo, và 1 input 1
> output còn nếu muốn flexible hơn kiểu như
> skip connection, ...hoặc ra nhiều output thì
> dùng Functional
>
>
>
> Cái nữa là nó cần biết shape của input trước
> để kiểu như chuẩn bị nếu không nó phải đợi
> đến khi bỏ input vào

<br>

<a id="node-rp6o7m2"></a>

##### Exercise 1 - happyModel: Lần lượt define các
layer như gợi ý bỏ để define nên Sequential model

<br>

<a id="node-ds6ejhc"></a>

<p align="center"><kbd><img src="assets/miu6rxl8v1.png" width="80%"></kbd></p>

> [!NOTE]
> Ở lần review 1 đã hiểu thêm 1 số thứ:
>
>
>
> Dense nó có kernel_ini..là **glorot_uniform** là 1 kiểu ini
> randomly do ông **Glorot** phát minh nhằm mục đích giảm hiện
> tượng **Vanishing Gradient**. Công thức cụ thể thì xem trong
> sách nhưng đại khái là random. Có lẽ không cần define vì Keras
> dùng cái này làm default, có những cái khác là **he_uniform**,..
>
>
>
> BatchNorm nó có hyper param - axis thường dùng axis cuối nên
> ở đây hiểu được tại sao để 3 vì input có 4D - m, nH, nW, nC
> index 0,1,2,3

<br>

<a id="node-mkgorws"></a>

<p align="center"><kbd><img src="assets/e6n7u8rfi6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/w34nakjr989.png" width="80%"></kbd></p>

<br>

<a id="node-o5wx9za"></a>

<p align="center"><kbd><img src="assets/fh13g1w2bi8.png" width="80%"></kbd></p>

<br>

<a id="node-x8c35te"></a>

<p align="center"><kbd><img src="assets/ljc55pmolmk.png" width="80%"></kbd></p>

> [!NOTE]
> Define model xong có thể compile với **Adam**
> optimizer, loss function là **binary_crossentropy** vì
> đây là bài toán binary classification (output từ
> sigmoid ra probability trong [0,1]**)** và metrics là **accuracy**

<br>

<a id="node-q7k8m1a"></a>

##### 3.2 - Train and

Dùng fit(X_train, Y_train) argument epochs,
batch_size

Evaluate the Model chỉ cần gọi evaluate(bỏ vào
test set) quá tiện

<br>

<a id="node-306s3o3"></a>

<p align="center"><kbd><img src="assets/58mr1m1usm.png" width="80%"></kbd></p>

<br>

<a id="node-9j2h29n"></a>

##### 4 - The Functional API: Nói sơ về Functional
API cho thấy nó flexible, mạnh mẽ hơn
Sequential API ví dụ có thể define 'Skip Connection'
 hứa hẹn sắp tới sẽ tìm hiểu
nhiều hơn

<br>

<a id="node-ujfwxn5"></a>

<p align="center"><kbd><img src="assets/4fcknv3vyz5.png" width="80%"></kbd></p>

<br>

<a id="node-ka7ns54"></a>

##### 4.1 - Load the SIGNS Dataset: Dataset
cho vấn đề nhận diện kí tự hình ảnh cho
người câm điếc đã dùng ở Course 2

<br>

<a id="node-z3d6vwk"></a>

<p align="center"><kbd><img src="assets/5zibbvaf9up.png" width="80%"></kbd></p>

<br>

<a id="node-fam0y4q"></a>

##### 4.2 - Split the Data into Train/Test Sets Thực
hiện việc \\*normalization\\* và dùng custom
function \\*convert_to_one_hot\\*() để transform
Y_train, Y_test

<br>

<a id="node-dzpb59a"></a>

<p align="center"><kbd><img src="assets/08xj06hgvwqj.png" width="80%"></kbd></p>

<br>

<a id="node-lr9ms0a"></a>

##### 4.3 - Forward Propagation

Đại khái là từng bước từng bước define các layer trong '
computational graphs'

Bắt đầu bởi ts.keras.Input() rồi lần lượt Conv2D - ReLU
-MaxPool2D - Conv2D - ReLU - MaxPool2D - Flatten - FC -
Output:

Cách thức là: Bỏ output của thằng trước thành input của thằng
sau -  Đây chính là lý do của cái tên Functional, các layer work
như function với việc nhận input và cho ra oupput

Ngoài ra thì một số điểm đáng chú ý
Define a input node as a callable object.
Flatten batch_size, h, w, c -> batch_size, h*w*c
Define output using the last of the
function's composition - Dense

<br>

<a id="node-4f7jm8j"></a>

<p align="center"><kbd><img src="assets/imtfnd205x.png" width="80%"></kbd></p>

> [!NOTE]
> Define output using the last of the
> function's composition - Dense

<br>

<a id="node-962w835"></a>

<p align="center"><kbd><img src="assets/tihdr8bq0t.png" width="80%"></kbd></p>

<br>

<a id="node-n2k3n8x"></a>

##### Exercise 2 - convolutional_model: Chỉ chú ý là Conv2D's argument 
filters chỉ số lượng filters, kernel mới là filters's size

Z1 = tf.keras.layers.Conv2D(filters=8, kernel_size=(4,4), strides=(1, 1), padding='same' )(input_img)

A1 = tf.keras.layers.ReLU()(Z1)

P1 = tf.keras.layers.MaxPool2D(pool_size=(8, 8), strides=(8, 8), padding='same')(A1)

Z2 = tf.keras.layers.Conv2D(filters=16, kernel_size=(2,2) , strides=(1, 1), padding='same')(P1)

A2 = tf.keras.layers.ReLU()(Z2)

P2 = tf.keras.layers.MaxPool2D(pool_size=(4, 4), strides=(4, 4), padding='same')(A2)

F = tf.keras.layers.Flatten()(P2)

outputs = tf.keras.layers.Dense(units= 6 , activation='softmax')(F)

model = tf.keras.Model(inputs=input_img, outputs=outputs)


Xong cũng compile, Sequential và
Functional chỉ là phương pháp để tạo kiến trúc model khác
nhau chứ vẫn đều là tạo TF Keras model object

<br>

<a id="node-2sz74a9"></a>

<p align="center"><kbd><img src="assets/r5ji6ohbf9.png" width="80%"></kbd></p>

<br>

<a id="node-fi9aiwd"></a>

<p align="center"><kbd><img src="assets/iij6pvb7eg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/t9hc2lach8c.png" width="80%"></kbd></p>

<br>

<a id="node-vi1nnl5"></a>

<p align="center"><kbd><img src="assets/r7y94b7kqal.png" width="80%"></kbd></p>

> [!NOTE]
> Xong cùng compile, Sequential và
> Functional chỉ là phương pháp để tạo kiến trúc model khác
> nhau chứ vẫn đều là tạo TF Keras model object

<br>

<a id="node-xemll8u"></a>

##### 4.4 - Train the Model: 
Tạo train / test dataset modal cho Conv_model với tf.Dataset.\\*from_tensor_slices\\*()
Gọi fucntion \\*fit()\\* trên conv_model created
ở trên, bỏ vào train_dataset và test_set, no. epochs

<br>

<a id="node-zqhgpfx"></a>

<p align="center"><kbd><img src="assets/bsdgvyv8nyf.png" width="80%"></kbd></p>

<br>

<a id="node-otsycnb"></a>

<p align="center"><kbd><img src="assets/ttmjpk217g.png" width="80%"></kbd></p>

<br>

<a id="node-qwjpsq9"></a>

##### 5 - History Object: Dùng kết quả (history) của training
process để visualize

Có thể thấy bỏ history của Keras model.
history bỏ vào DataFrame của Pandas xong là
vẽ ra training history dễ dàng. TF và Keras quả thật rất tiện

<br>

<a id="node-bieyc6s"></a>

<p align="center"><kbd><img src="assets/xvbf0pxcwb.png" width="80%"></kbd></p>

<br>

<a id="node-v591pui"></a>

<p align="center"><kbd><img src="assets/i5458wpzmt.png" width="80%"></kbd></p>

> [!NOTE]
> Có thể thấy bỏ history của Keras model.
> history bỏ vào DataFrame của Pandas xong là
> vẽ ra training history dễ dàng. TF và Keras quả thật rất tiện

<br>

<a id="node-6jkjn0y"></a>

<p align="center"><kbd><img src="assets/m1itfduvcrl.png" width="80%"></kbd></p>

<br>

<a id="node-2y6b5ki"></a>

##### 6 - Bibliography: Nên đọc thêm

<br>

<a id="node-etnbbns"></a>

<p align="center"><kbd><img src="assets/bu9qhvjw745.png" width="80%"></kbd></p>

<br>

<a id="node-mbjlw00"></a>

## C4w2_deep Convolutional Models: Case Studies

<br>

<a id="node-l5uvgg6"></a>

### Why look at case studies?

<br>

<a id="node-c89edf6"></a>

#### 1 Case studies of effective convolutional neural networks

2 Importance of looking at \\*case studies\\* to gain intuition and
confidence in building effective convnets

3 \\*Transferability of neural network architecture\\* across different
computer vision tasks

4 \\*Potential satisfaction in reading research papers\\* from the field
of computer vision

5 Outline of the next few videos: classic networks such as
\\*LeNet\\*-5, \\*AlexNet\\*, and \\*VGG\\*; \\*ResNet\\*, a deep 152-layer neural
network with interesting tricks; and the \\*Inception\\* neural network

6 Benefits of learning from these examples, even for those not
working in computer vision, as ideas are \\*cross-fertilizing\\* into
other disciplines.

<br>

<a id="node-4v2kefr"></a>

<p align="center"><kbd><img src="assets/i3zlutxos3k.png" width="80%"></kbd></p>

<br>

<a id="node-f0lt6g7"></a>

### Classic Networks

<br>

<a id="node-07kf8hd"></a>

#### Xem qua 1 số classic ConvNet
Nhận xét chung là nó thường có cấu trúc là 
\\*Conv - Pool - Conv - Pool ...Conv - Pool- FC - FC.. -FC - Sofmax 
Qua các layer thì nH, nW giảm, nC tăng\\*

<br>

<a id="node-smmbk8i"></a>

<p align="center"><kbd><img src="assets/6n51o9b8i3x.png" width="80%"></kbd></p>

> [!NOTE]
> Một số nhận xét:
> Qua các layer:
> nH, nW giảm, nC tăng
> Conv - Pool  - Conv - Pool
> **60k** params

<br>

<a id="node-er0pvft"></a>

<p align="center"><kbd><img src="assets/e7hmpfxxiad.png" width="80%"></kbd></p>

> [!NOTE]
> Một số nhận xét:
> Giống như LeNet như bigger
> **~60 mils** params

<br>

<a id="node-hspvpx0"></a>

<p align="center"><kbd><img src="assets/7ufe4dae5nv.png" width="80%"></kbd></p>

> [!NOTE]
> Một số nhận xét:
> Giống như Alexnet nhưng bigger
> **~138 mils** params

<br>

<a id="node-shrnltq"></a>

### Resnet

<br>

<a id="node-3vhsnl0"></a>

#### Training \\*very deep\\* neural networks is difficult due to \\*vanishing\\* and \\*exploding\\*
gradient problems.

\\*Skip connections\\* are a solution to these problems as they \\*allow activations from
one layer to be fed to another layer much deeper\\* in the network, allowing the
building of \\*ResNets\\*.

\\*ResNets\\* are built from \\*residual blocks\\* which consist of a main path of layers and
a shortcut that allows information to flow directly to deeper layers.

Adding these residual blocks to a plain network turns it into a ResNet and allows
for the training of \\*much deeper neural networks without significant loss\\* in
performance.

ResNets \\*help with the vanishing and exploding gradient problems\\*, allowing the
training of \\*much deeper neural networks \\*without \\*compromising performance\\*.

<br>

<a id="node-98o8g11"></a>

<p align="center"><kbd><img src="assets/hoishiibmcg.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Residual block nó có thêm cái 
> '**Shortcut /Skip Connection**' chuyển a[l] vào step tính a[l+2]
>
>
>
> a[l+2] = g(z[l+2] + a[l])
>
>
>
> Khi vì lí do nào đó, params khiến **z[l+1] = 0** có thể do hiện tượng
> gradient exploding / vanishing thì a[l+2] sẽ bằng g(a[l]) = max(0, a[l]) (reLU) = a[l]
> từ đó đại khái là **không bị mất thông tin**

<br>

<a id="node-x2vhfwi"></a>

<p align="center"><kbd><img src="assets/0rd4jfnqlcqg.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là RestNet giúp khắc phục vấn đề **nhiều layer thì
> performance giảm** do Gradient Vanishing / Exploding từ đó
> **cho phép train very deep network**

<br>

<a id="node-zyorofh"></a>

### Why Resnets Work

<br>

<a id="node-jrjvljn"></a>

#### 1 \\*Residual Networks (ResNets)\\* work well in terms of training because they
can be made \\*deeper without decreasing performance\\* on the training set.

2 Making neural networks \\*deeper\\* can \\*hurt the ability to train them well\\* on
the training set, which is a prerequisite to doing well on the holdout, test
sets or during deployment.

3 ResNets include \\*residual blocks \\*with \\*shortcut connections\\*, making it
easy for these extra layers to \\*learn the identity function\\*.

4 \\*The identity function is easy to learn\\*, so the addition of extra layers in the
neural network \\*doesn't hurt\\* its ability to perform \\*as well as a simpler
network without these extra layers\\*.

5 \\*Same convolutions\\* are often used in ResNets to \\*ensure\\* that the
dimension of the \\*input \\*and\\* output \\*of the layers\\* are equal\\*, making it easier
to \\*carry out\\* the \\*shortcut connection\\* and the addition of two equal
dimension vectors.

<br>

<a id="node-loqbnac"></a>

<p align="center"><kbd><img src="assets/kwi0s7nimlf.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu regularization (ví dụ vậy) bóp W, b (l+1) bằng 0 thì a[l+2] sẽ
> bằng g(a[l]) và = a[l] vì g là reLU 
>
>
>
> Có nghĩa là ..nếu gradient vanishing xảy ra, thì ..không bị làm sao cả,
>  a[l+2] chỉ đơn giản là a[l+2] quay lại bằng a[l] thay vì =0
> (ý ổng nói network rất dễ learn được identity function đại khái là 
> vậy)   
>
>
>
> Bằng 0 có nghĩa là không học được gì nữa (hiểu đại khái vậy, vì nếu
> a[l+2] = 0 thì mấy cái layer sau = 0 hết)
>
>
>
> Đo đó, với 'Skip connection' thì đầu tiên là **add thêm extra layer, hay
>  tạo very deep network sẽ không gây hại** đến model.
>
>
>
> Và từ ko gây haị thì chỉ có thể nâng lên thành improve hệ
> thống, ý nói nếu tệ nhất mà chỉ ko gây hại thì chắc chắn phải có thể
> improve rồi.
>
>
>
> Ngược lại, nếu không có Skip connection, thì việc add thêm layer rất dễ
> dẫn đến việc hệ thống bị stuck khi W bị = 0
>
> Đại khái là để a[l+2] bằng size với a[l], ta nhân thêm a[l] với 1 matrix **Ws**. Ws
> có thể **trainable** hoặc **fixed value**  Hoặc với ConvNet thì dùng **Same
> padding** để giữ size của input và output

<br>

<a id="node-jixb0kb"></a>

<p align="center"><kbd><img src="assets/ygyba934c.png" width="80%"></kbd></p>

> [!NOTE]
> Một ví dụ 
> Conv conv conv pool, conv conv .. conv pool
> ..
>
>
>
> Sau pool (size nó giảm) thì dùng Ws để khôi phục:
> Chưa rõ lắm nhưng đại khái là vậy

<br>

<a id="node-t3iawka"></a>

- **Sure, here's a more detailed answer with indexed main ideas:  

1 \\*ResNets\\* are deep neural networks that
work well because they can be made \\*deeper\\* without \\*significantly hurting performance\\* on the \\*training\\* \\*set\\*,
which is a \\*prerequisite\\* for good performance on the test set.

2 The reason \\*ResNets\\* can be made deeper without hurting performance is because of the use of \\*residual
blocks\\*, which include a \\*skip connection\\* that allows the network to \\*learn the identity function\\* more easily.

3 Let's look at an example to see how the skip connection works in a ResNet block. Suppose we have an
input X feeding into a neural network that outputs activation \\*a[l]\\*. We want to make the network deeper by
adding two extra layers to output \\*a[l+2]\\*. We add a \\*residual block\\* with a \\*skip connection\\* to achieve this. If we
assume all activations are greater than or equal to zero, then a[l+2] can be expressed as \\*g(w[l+2] * a[l+1] +
b[l+2] + a[l])\\*, where g is the activation function and w[l+2] and b[l+2] are the weights and biases for the
added layers.

4 If we use \\*L2 regularization to shrink the weights\\*, w[l+2], and assume b[l+2] = 0 for simplicity, then we can
see that if w[l+2] = 0, the \\*entire term w[l+2] * a[l+1] + b[l+2] disappears\\*, leaving just \\*a[l]\\* \\*as the input to the
activation function\\*. If g is the ReLU function, which outputs only non-negative numbers, then \\*g(a[l]) = a[l].\\*
This means that the \\*identity function\\* is \\*easy for the residual block to learn\\*, and it can easily make \\*a[l+2]
equal to a[l].\\*

5 Adding two extra layers with a residual block \\*does not significantly hurt performance\\* because the \\*residual
block can easily learn the identity function\\*. However, the goal is not just to avoid hurting performance but to
improve it. \\*If the added layers can learn something useful\\*, then the \\*network can do even better than simply
learning the identity function.\\*

6 In \\*very deep plain networks\\* without residual connections, it becomes \\*difficult to learn even the identity
function\\*, which is why \\*adding more layers can actually hurt performance\\*. \\*ResNets\\* \\*work because they make
it easy for the extra layers to learn the identity function\\*, and from there they \\*have a chance of learning
something useful.\\*

7 Another detail worth noting is that the \\*dimensions of z[l+2] and a[l] must be the same\\* for the skip
connection to work. This is why s\\*ame convolutions are often used in ResNets to preserve the dimensions of
the inputs and outputs of each layer\\*, making it \\*easier to carry out the skip connection\\* and the addition of the
two vectors. \\*If the dimensions are different, an extra matrix must be added to make the dimensions match.\\***

<br>

<a id="node-5z01j3y"></a>

### Networks In Networks And
1x1 Convolutions

<br>

<a id="node-igbq62h"></a>

#### 1 Using a \\*one-by-one convolution\\* can help in designing content
architectures.

2 A one-by-one convolution can \\*multiply an image by a single number\\*
or \\*perform a more complex operation\\*.

3 A one-by-one convolution takes each position in an input volume and
applies a \\*fully connected neural network\\* to it.

4 A one-by-one convolution is sometimes called a "\\*network in network\\*"
and has been influential in other neural network architectures.

5 One way to use a one-by-one convolution is to \\*shrink the number of
channels\\* in an input volume.

6 A one-by-one convolution \\*adds nonlinearity\\* and \\*allows for learning a
more complex function in a network\\*.

<br>

<a id="node-2g124q7"></a>

<p align="center"><kbd><img src="assets/d4mkvs6i9s8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4i66d0rqvmv.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái nó giống như apply 1 fully connected cho mỗi position của volumn (nhìn hình sẽ hiểu).

<br>

<a id="node-2umtjao"></a>

<p align="center"><kbd><img src="assets/atfvwh45nqm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là 1x1 Conv có thể có công dụng giúp giảm n_c, giống  cách
> như Pool giúp giảm n_h, n_w
>
>
>
> Ví dụ xài 32 cái filer 1x1x192 sẽ giúp tạo output 28x28x32
>
>
>
> Còn không (nếu không muốn giảm n_c - giữ nguyên 1x1x192) thì nó
> cũng giúp tăng hiệu quả học tập lên

<br>

<a id="node-crzhjnu"></a>

### Inception Network Motivation

<br>

<a id="node-ca19f0m"></a>

<p align="center"><kbd><img src="assets/r0ethmf18ql.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là khỏi phải suy nghĩ giữa chọn filter size là 1x1, hay 3x3, hay
> 5x5 rồi dùng **conv** hay **pool**, thì cứ dùng hết:
>
>
>
> 64 cái filter 1x1 ra cục xanh lá 28x28x64
> 128 cái filter 3x3 same padding -> 28x28x128
> 32 cái filter 5x5 same padding -> 28x28x32
> 32 cái max pooling -> 28x28x32
>
>
>
> Xong stack lại và để cho máy tính nó **/tự quyết định sẽ dùng cái nào/**
>
> *Cái 1x1 ghi là 28x28x64 thì đương nhiên phải hiểu là
> **xài 64 cái filter có size 28x28x192.** Tương tự 128 cái
> filter 3x3x192 32 cái filter 5x5x192

<br>

<a id="node-ufhvn38"></a>

<p align="center"><kbd><img src="assets/b4xnpqah1l.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/07mdxcc5weea.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/89m5swy99vr.png" width="80%"></kbd></p>

> [!NOTE]
> Tại sao lại nhân 5x5x192 đã hiểu: Mỗi lần convol là nó tính 5x5 phép
> nhân rồi cộng lại - là cho 1 lớp, có nc lớp -> 5x5xnc phép nhân

<br>

<a id="node-wtyxu8m"></a>

<p align="center"><kbd><img src="assets/g7nhbjt5vr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bằng cách dùng 1x1 Convolution, số phép tính cần thiết giảm đi 1/10
>
>
>
> 28x28x192 - 32 cái filter 5x5 same padding -> **28x28x32: 120m params**
>
>
>
> thì nếu dùng 2 bước với 1x1 filter
>
>
>
> 28x28x192 - dùng 16 cái 1x1 -> 28x28x16 - dùng 32 cái 5x5 same padding -> **28x28x32: thì chỉ có 12m params**

<br>

<a id="node-6fz6mk7"></a>

### Inception Network

<br>

<a id="node-whl840f"></a>

#### 1 The inception module takes the activation from a previous layer as input
and \\*outputs multiple feature maps of different sizes.\\*

2 The inception network is made up of a \\*series of inception blocks\\*, which
consist of \\*multiple inception modules\\* concatenated together.

3 The inception network \\*repeats these inception blocks\\* in different positions
in the network.

4 The inception network also includes \\*additional side branches\\*, which \\*use
hidden layers to make predictions\\* alongside the main output layer.

5 The side branches help to \\*ensure that the features computed are useful
for making predictions\\*.

<br>

<a id="node-y90curp"></a>

<p align="center"><kbd><img src="assets/wgcttmgpwr.png" width="80%"></kbd></p>

> [!NOTE]
> Ứng dụng ý tưởng ở lecture trước, Inception module sử dụng đủ loại filter, chú ý là như đã nói, dùng 2 bước
> với 16 cái 1x1(x192) và 3x3(x16) gọi là bottle-neck layer thay vì 3x3(x192) same padding để giảm số params

<br>

<a id="node-fjba246"></a>

<p align="center"><kbd><img src="assets/00qo9sgnlr8wm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái (Inception network) là nhiều Inception module
>
>
>
> Additional side branched: Dùng softmax tại các hidden layer, đại khái là
> cũng generate well predicting và giảm overfitting
>
>
>
> Term "Inception" đúng là đến từ phim Inception
>
>
>
> Cái trong hình dưới là GoogleNet

<br>

<a id="node-kms15u9"></a>

### Mobilenet

<br>

<a id="node-qy290q9"></a>

#### 1 Introduction to \\*MobileNets\\*, a \\*convolutional neural network architecture\\* used for
computer vision that can run on devices with \\*low computational power\\*.

2 Need for \\*MobileNets\\* as other neural networks are \\*computationally expensive.\\*

3 Explanation of the \\*normal convolution process\\* used in other neural networks.

4 \\*Computational cost\\* of normal convolution determined.

5 Introduction of \\*depthwise separable convolution\\* used in \\*MobileNets\\*.

6 Explanation of how the \\*depthwise convolution\\* works.

7 Calculation of the computational cost of depthwise convolution.

<br>

<a id="node-2anvp6i"></a>

<p align="center"><kbd><img src="assets/1alblxrfr0fi.png" width="80%"></kbd></p>

<br>

<a id="node-26t2hb8"></a>

<p align="center"><kbd><img src="assets/uhn314beegn.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tính lại xem Convolution thông
> thường cần bao nhiêu phép tính
>
> Trong Normal Conv: Mỗi lần cái filter convol để tính ra 1 số cho 1
> dimension của output, nó tính cho từng dimension của input sau
> đó nó **cộng lại cho nên kết quả là chỉ còn 1 channel, nhưng có
> nc cái filter thì thành ra cục output có nc channel**
>
>
>
> 6x6x3 -  1 filter 3x3x3 -> 4x4x**1** 
> x **5 cái** filter thành ra **4x4x5**

<br>

<a id="node-ny8cktg"></a>

<p align="center"><kbd><img src="assets/xu09jogztnk.png" width="80%"></kbd></p>

> [!NOTE]
> Còn depthwise thì
> nó khác 1 chút

<br>

<a id="node-5pe3s0o"></a>

<p align="center"><kbd><img src="assets/eb4qs8bwp45.png" width="80%"></kbd></p>

> [!NOTE]
> **DepthWise** đại khái là ở mỗi lần filter convol nó sẽ tính riêng từng
> dimension, và không cộng lại để 'ép' lại thành 1 channel.

<br>

<a id="node-nlyu4kd"></a>

<p align="center"><kbd><img src="assets/kysuz530ir.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/o31xhi26zxf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/1hpyxvym34x.png" width="80%"></kbd></p>

<br>

<a id="node-qpnmala"></a>

<p align="center"><kbd><img src="assets/5qp787a35k8.png" width="80%"></kbd></p>

> [!NOTE]
> Kết quả là sau khi convol với 1 filter nó
> vẫn giữ số channel của input (chứ không
> ép lại thành 1 channel)
>
>
>
> 6x6x**3** - 1 **(chỉ một)** filter 3x3x3 -> 4x4x**3**

<br>

<a id="node-kqbwfpb"></a>

<p align="center"><kbd><img src="assets/27hgqvdrx5l.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó cái cục này được convol qua 5 cái
> 1x1x3 filter để thành ra **4x4x5** giống như
> output của normal convolution '

<br>

<a id="node-rj1xr5g"></a>

<p align="center"><kbd><img src="assets/su6odyq4rfk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/fppk2979ckp.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/a3z2y8ep21c.png" width="80%"></kbd></p>

<br>

<a id="node-p7gaxqr"></a>

<p align="center"><kbd><img src="assets/riub5m4s9d.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cho thấy cùng là từ input 6x6x3 -> output 4x4x5 nhưng
> dùng **Depth-wise Separable Convolution** giúp giảm **~10x**
> computational expensive so với **normal convolution**

<br>

<a id="node-boaz1a5"></a>

<p align="center"><kbd><img src="assets/sneqzsozv9k.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ổng nói đúng ra là phải vẽ icon thành nhiều lớp hơn 3x3xnc
> nếu nc = 8 chẳng hạn phải vẽ thành 8 lớp nhưng quy ước cứ giữ icon
> như vậy cho gọn và mình tự hiểu là được

<br>

<a id="node-xofi4od"></a>

### Mobilenet Architecture

<br>

<a id="node-eyj3yyu"></a>

#### Main ideas:  1 \\*MobileNet\\* is a neural network that uses a \\*depthwise\\*
\\*separable\\* \\*convolutional operation\\* to \\*reduce computational cost.
\\*
2 The \\*MobileNet v1\\* architecture uses a block comprising a \\*depthwise
convolutional operation\\* and a \\*stack\\* of \\*13 layers\\* to make a
\\*classification\\* prediction.

3 \\*MobileNet v2\\* is an \\*improvement\\* over the basic MobileNet
architecture that \\*includes a residual connection\\* and an\\* expansion
layer \\*before the \\*depthwise\\* convolution and the \\*pointwise\\* convolution.

4 MobileNet v2 repeats the block \\*17 times\\* and uses \\*pooling\\*,
\\*fully-connected\\*, and \\*softmax layers\\* to make a classification prediction.

5 The MobileNet v2 \\*bottleneck block\\* \\*increases the size\\* of the
representation within the block and \\*projects it back down to a smaller
set of values\\*, \\*reducing the amount of memory\\* \\*needed\\* to store
activations from layer to layer.

<br>

<a id="node-9n1gnup"></a>

<p align="center"><kbd><img src="assets/niviqg1wt3i.png" width="80%"></kbd></p>

<br>

<a id="node-fp3m6aj"></a>

<p align="center"><kbd><img src="assets/qfwtrjhtzse.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó expand ra để tính toán được nhiều feature hữu
> ích hơn, sau đó co lại để đáp ứng điều kiện dung lượng bộ nhớ
> hạn hẹp -> Tốt hơn MobileNet v1 mà vẫn đáp ứng bộ nhớ nhỏ
>
>
>
> Expand: nxnx3 - 18 cái filter 1x1x3 -> nxnx18
>
>
>
> Depth-wise: nxnx18 - 1 cái filter n_hxn_w x18 **depth-wise** -> nxn18
>
> (Khúc này có lẽ phải hiểu là dùng same padding để giữ size n
> và n_h, n_w ổng cũng không nói tới nhưng cũng không quan trọng)
>
>
>
> Projection: nxnx18 - 3 cái 1x1x18 -> nxn3
>
> Đại khái như vậy là đủ hiểu
> MobileNet v2 rồi, muốn xem
> kĩ hơn để biết chi tiết thì đọc
> Paper của Sandler
>
> Từ nxnx3 -> nxnx18 thì ta dùng 18 cái filter 1x1x3
>
>
>
> Còn từ nxnx18 về lại nxnx3 thì dùng 3 cái filter 1x1x18

<br>

<a id="node-di66yjh"></a>

### Efficientnet

<br>

<a id="node-6jgajkc"></a>

#### 1 The benefits of using \\*computationally efficient neural networks\\* like
MobileNet V1 and V2.

2 The \\*challenge\\* of adapting neural networks to \\*different devices\\* with
varying \\*computational resources\\*.

3 The concept of \\*EfficientNet\\* and how it can be used to \\*scale up\\* \\*or
down\\* neural networks based on a \\*device's computational budget\\*.

4 The three factors that can be adjusted to scale up or down neural
networks:\\* image resolution\\*, network \\*depth\\*, and layer \\*width\\*.

5 The importance of \\*finding the right trade-off between image
resolution, network depth, and layer width\\* to optimize neural network
performance for a specific device.

6 The usefulness of \\*open source implementations of EfficientNet\\* for
adapting neural network architectures to specific devices.

<br>

<a id="node-dyalouh"></a>

<p align="center"><kbd><img src="assets/360tq3qd75q.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng higher resolution image

<br>

<a id="node-9srpxws"></a>

<p align="center"><kbd><img src="assets/84zwe3j8h6f.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng deeper network

<br>

<a id="node-0xpn0y5"></a>

<p align="center"><kbd><img src="assets/1s5s8qliyjj.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng wider network

<br>

<a id="node-bhigw0u"></a>

<p align="center"><kbd><img src="assets/vteg6yiotd9.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi là: Với cụ thể 1 giới hạn về khả năng tính toán, làm
> sao để chọn được / quyết định được r, d, w? Hay nói cách
> khác là  scale cái nào lên và giữ nguyên cái nào hoặc scale
> cùng lúc cả 3 cái lên với tỉ lệ bao nhiêu? -> **Loot at
> OpenSource implementation of EfficientNet**

<br>

<a id="node-j7bmkae"></a>

<p align="center"><kbd><img src="assets/cyc58cnfse.png" width="80%"></kbd></p>

> [!NOTE]
> Build N.N for mobile devices, embedded devices

<br>

<a id="node-h334u7z"></a>

### Using Open-source
implementation

<br>

<a id="node-r207zbp"></a>

#### 1 \\*Practical advice\\* on using neural network and \\*ConvNet\\* \\*architectures\\*

2 Importance of \\*open-source implementations\\* for \\*replicating\\* neural
networks

3 \\*Difficulty\\* of replicating neural networks without \\*open-source
implementations\\*

4 Benefits of using \\*open-source implementations\\*, such as \\*faster
implementation and transfer learning\\*

5 Using \\*GitHub\\* to find open-source implementations

<br>

<a id="node-0tsp76c"></a>

<p align="center"><kbd><img src="assets/mniwppxn3z7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nên search (GitHub) và xài cái người ta làm

<br>

<a id="node-0fkj156"></a>

### Transfer Learning

<br>

<a id="node-txx2n52"></a>

#### 1 \\*Pre-training\\* and\\* transfer learning\\* can help build computer vision
applications faster.

2 Many \\*pre-trained models are available for download\\*, which have
already been \\*trained on large public datasets\\*.

3 Using transfer learning, \\*pre-trained weights can be used as a starting
point\\* for a new task.

4 \\*Frozen\\* \\*layers\\* in pre-trained models can be used to \\*extract features\\* that
can be used for a new classification problem.

5 \\*Pre-computing features from frozen layers\\* can help speed up training
with a small dataset.

6 \\*Fewer layers can be frozen\\* if there is a \\*larger labeled dataset\\* available.

7 If there is a \\*lot of data\\* available, \\*the whole pre-trained network can be
used for training.\\*

8 There are different ways to initialize the last few layers of the network
for the new classification problem.

9 The number of layers frozen and trained on top can be adjusted based
on the available dataset size.

<br>

<a id="node-ooimhrp"></a>

<p align="center"><kbd><img src="assets/ehjj15qcqo7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:  Nếu có ít data, cứ giữ nguyên hidden layers, và train cái layer cuối
> thôi. **Precompute** đại khái là (từ feature x của mình **tính output của layer cuối
> trước với cái n.n của người ta - như 1 function**) để khi chạy G.D để training layer
> cuối của mình thì khỏi phải làm bước tính toán này (forward propagation)
>
>
>
> Nếu có nhiều data hơn thì freeze mấy layer đầu thôi, train mấy layer cuối thậm chi
> train lại hết, coi các weight đã train của họ như initialization

<br>

<a id="node-racjohg"></a>

<p align="center"><kbd><img src="assets/e8l5ai079up.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ổng nói Transfer learning hầu như là cái phải
> làm, trừ khi mình có rất rất nhiều data thì mới làm từ
> đầu

<br>

<a id="node-h3xjqe5"></a>

### Data Augmentation

<br>

<a id="node-yb6syio"></a>

#### 1 \\*Computer vision\\* task often \\*requires more data\\* to improve performance.

2 \\*Data augmentation\\* is a \\*commonly used technique\\* to improve the
performance of computer vision systems.

3 \\*Mirroring\\* and \\*random cropping\\* are frequently used data augmentation
techniques.

4 \\*Color shifting\\* is another commonly used data augmentation technique.

5 The motivation behind color shifting is to make the learning algorithm
more robust to changes in image color.

6 \\*PCA Color Augmentation\\* is a specific implementation of color shifting.

7 \\*Loading images from a hard disk using a CPU\\* thread is a common
implementation of data augmentation in practice.

<br>

<a id="node-j4xu1hw"></a>

<p align="center"><kbd><img src="assets/y3quo1qnpj.png" width="80%"></kbd></p>

<br>

<a id="node-c64mr8w"></a>

<p align="center"><kbd><img src="assets/0pygs83eypi.png" width="80%"></kbd></p>

<br>

<a id="node-sktivex"></a>

<p align="center"><kbd><img src="assets/z3lqerhss7.png" width="80%"></kbd></p>

<br>

<a id="node-49mszkt"></a>

### State Of Computer Vision

<br>

<a id="node-9a0ygqo"></a>

#### 1 Deep learning has been successfully applied to various problems, including
computer vision.

2 \\*Computer vision is a complex problem\\*, and \\*deep learning requires a large
amount of data to achieve good performance.\\*

3 There is often a \\*trade-off\\* between the \\*amount of data available\\* and \\*the need
for hand-engineering\\* in machine learning.

4 The computer vision literature has historically\\* relied more on
hand-engineering \\*due to \\*limited data availability\\*, but with the \\*increase in data\\*
sets, the \\*use of hand-engineering has decreased\\*.

5 \\*Object detection\\*, a subset of computer vision, has \\*smaller data sets\\* and
therefore requires more \\*complex algorithms\\* and \\*specialized components.
\\*
6 \\*Transfer learning\\* is a technique that can help in cases where there is \\*limited
data.
\\*
7 Researchers in computer vision are enthusiastic about \\*achieving high
performance on standardized benchmark\\* data sets and competitions.

<br>

<a id="node-1h76qn9"></a>

<p align="center"><kbd><img src="assets/nrp9xsu840j.png" width="80%"></kbd></p>

<br>

<a id="node-szmc8qt"></a>

<p align="center"><kbd><img src="assets/0ffklezchrf.png" width="80%"></kbd></p>

<br>

<a id="node-nbvpen7"></a>

<p align="center"><kbd><img src="assets/jz7z86am9k.png" width="80%"></kbd></p>

<br>

<a id="node-hed4dro"></a>

### Quiz

<br>

<a id="node-6xklk8k"></a>

<p align="center"><kbd><img src="assets/w9d822zkeej.png" width="80%"></kbd></p>

<br>

<a id="node-sfnqs9p"></a>

<p align="center"><kbd><img src="assets/616lj1cfjv9.png" width="80%"></kbd></p>

<br>

<a id="node-8u6ejpj"></a>

<p align="center"><kbd><img src="assets/hjqqj89fq6u.png" width="80%"></kbd></p>

<br>

<a id="node-lmu09fy"></a>

<p align="center"><kbd><img src="assets/61jwpldtdsk.png" width="80%"></kbd></p>

> [!NOTE]
> a[l+2] = g(z[l+2] + a[l]) (a[l] bỏ trong activation
> function luôn)
>
>
>
> vì g hay dùng ReLU nên nếu z[l+2] = 0 thì a[l+2] =
> max(0, a[l]) = a[l]

<br>

<a id="node-n7hi7kx"></a>

<p align="center"><kbd><img src="assets/jgz9954ufbb.png" width="80%"></kbd></p>

<br>

<a id="node-xtz3p26"></a>

<p align="center"><kbd><img src="assets/zghgg8khf5.png" width="80%"></kbd></p>

<br>

<a id="node-ia2lxwp"></a>

<p align="center"><kbd><img src="assets/4caotffcj59.png" width="80%"></kbd></p>

<br>

<a id="node-td2tb9j"></a>

<p align="center"><kbd><img src="assets/x7bv6cbfu1f.png" width="80%"></kbd></p>

<br>

<a id="node-c831l14"></a>

<p align="center"><kbd><img src="assets/iy0m8nok1rh.png" width="80%"></kbd></p>

<br>

<a id="node-7rv7y7c"></a>

<p align="center"><kbd><img src="assets/utkp07jhc1h.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gid9bng70x6.png" width="80%"></kbd></p>

<br>

<a id="node-dlkpjef"></a>

### Programming Assignment: Residual Networks

<br>

<a id="node-ykod0yx"></a>

#### • Implement the basic building blocks of ResNets in a deep
neural network using Keras

• Put together these building blocks to implement and train a
state-of-the-art neural network for image classification

• Implement a skip connection in your network

For this assignment, you'll use Keras.

<br>

<a id="node-0nx1r5w"></a>

##### Residual Networks

<br>

<a id="node-s3lgcgn"></a>

<p align="center"><kbd><img src="assets/amfqsot6b4j.png" width="80%"></kbd></p>

<br>

<a id="node-qhcge1q"></a>

##### 1 - Packages

<br>

<a id="node-49t1wu3"></a>

<p align="center"><kbd><img src="assets/kyromnfc1zr.png" width="80%"></kbd></p>

<br>

<a id="node-lfryprp"></a>

##### 2 - The Problem of Very
Deep Neural Networks:

Đại khái là vấn đề Gradient Vanishing - params về 0 rất nhanh 
khiến model stop learning Hoặc / Exploding - params trở nên rất lớn

<br>

<a id="node-x3x208f"></a>

<p align="center"><kbd><img src="assets/mv9zlau8e6k.png" width="80%"></kbd></p>

<br>

<a id="node-4q7srax"></a>

##### 3 - Building a Residual Network:

Nhắc lại rằng RestNet không những giúp giải quyết vấn đề
Vanishing Gradient mà còn giúp tăng performance của
network

Có hai loại block trong ResNet là \\*Identity\\* block và
\\*Convolutional\\* block

<br>

<a id="node-zrgm7m3"></a>

<p align="center"><kbd><img src="assets/1llbztourzq.png" width="80%"></kbd></p>

<br>

<a id="node-48y68vj"></a>

##### 3.1 - The Identity Block:

Đại khái là các step để tạo nên ResNet's
identity block

Nói đến việc sẽ thêm 1 bước BatchNorm để
tăng tốc training, chỉ cần  một dòng code với
Keras.

Và trong bài này mình sẽ skip 2 layer chứ
không phải 1 như trong lecture

> [!NOTE]
> Có cái vụ
> BatchNormalization
> chưa hiểu lắm

<br>

<a id="node-edhhesh"></a>

<p align="center"><kbd><img src="assets/nlqbdg620k.png" width="80%"></kbd></p>

<br>

<a id="node-w97hz2k"></a>

<p align="center"><kbd><img src="assets/wev55ryq41.png" width="80%"></kbd></p>

<br>

<a id="node-fjm4ygr"></a>

##### Exercise 1 - identity_block: Đại khái là làm theo gợi ý lần lượt khai báo các
layer

Conv2D, BatchNorm, Activation (Relu),

Conv2D, BatchNorm, Activation (Relu)

Conv2D, BatchNorm, Add, Activation (Relu)

Với input thằng sau là ouput thằng trước từ đó X được update qua các layer.

Để ý thấy ở đây nó dùng keras.layer.Activation('relu') thay vì keras.layer.
RELU()  như ở P.A tuần trước

Và thao tác '\\*Skip Connection\\*' được thực hiện bằng cách save X_shortcut
và add  với X ở layer \\*Add\\*

<br>

<a id="node-hlswixg"></a>

<p align="center"><kbd><img src="assets/zwchi24hdvd.png" width="80%"></kbd></p>

<br>

<a id="node-9smlikg"></a>

<p align="center"><kbd><img src="assets/7kf9zlj7zud.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/d2db53wc5f4.png" width="80%"></kbd></p>

<br>

<a id="node-x9ing6n"></a>

<p align="center"><kbd><img src="assets/f4q1wh7flif.png" width="80%"></kbd></p>

<br>

<a id="node-fjra9g3"></a>

##### 3.2 - The Convolutional Block:

Đại khái là cái này chỉ khác cái identity block ở chỗ nó có
thêm bước dùng Conv2D để resize X_shortcut nhằm để
X và X_shortcut cùng size cho bước Add, bước này đóng
vai trò như \\/\\*Ws\\*\\/ trong lecture nói tới.

Nói tới đại khái là không áp dụng Activation function vì
mục đích chỉ là resize thôi

Để ý thấy cho X và X_shortcut cùng size thì ở Conv2D
cho layer thứ 3 và cho shortcut phải cùng số lượng filter

> [!NOTE]
> Có cái vụ Glorot uniform
> seed là không hiểu

<br>

<a id="node-hp0okby"></a>

<p align="center"><kbd><img src="assets/y6w6jigoord.png" width="80%"></kbd></p>

<br>

<a id="node-sykqfgg"></a>

<p align="center"><kbd><img src="assets/94q9mnnajx8.png" width="80%"></kbd></p>

<br>

<a id="node-cbt3ipb"></a>

##### Exercise 2 - convolutional_block

Đại khái là làm theo gợi ý lần lượt khai báo các layer

Conv2D, BatchNorm, Activation (Relu),

Conv2D, BatchNorm, Activation (Relu)

Conv2D, BatchNorm, Add, Activation (Relu)

Với input thằng sau là ouput thằng trước từ đó X được
update qua các layer.

Chỉ có thêm cái Conv và Batch cho Shortcut với filter là
F3

<br>

<a id="node-qu5nili"></a>

<p align="center"><kbd><img src="assets/ajskdu4vun.png" width="80%"></kbd></p>

<br>

<a id="node-fjy8gen"></a>

<p align="center"><kbd><img src="assets/by1ei46kbjb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0y448ajy52zg.png" width="80%"></kbd></p>

<br>

<a id="node-dtgytp9"></a>

<p align="center"><kbd><img src="assets/fqj20ydo1o.png" width="80%"></kbd></p>

<br>

<a id="node-8xav71h"></a>

##### 4 - Building Your First ResNet Model (50 layers)

Đại khái là dùng các function ở trên để tạo một
network  \\*so deep \\*có 50 layers (?!) có kiến trúc
như hình

<br>

<a id="node-33nkpg1"></a>

<p align="center"><kbd><img src="assets/1o2sru17ii.png" width="80%"></kbd></p>

<br>

<a id="node-ywkskhv"></a>

##### Exercise 3 - ResNet50

Đại khái là cũng lần lượt define từng layer
theo kiến trúc của network define trong sơ
đồ.

Và cuối cùng tạo model: model =
Model(inputs = X_input, outputs = X)

<br>

<a id="node-e7x7mzf"></a>

<p align="center"><kbd><img src="assets/gk1wcfxxelc.png" width="80%"></kbd></p>

<br>

<a id="node-e3zxnju"></a>

<p align="center"><kbd><img src="assets/ivx1bol465h.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/wfu2ll9mule.png" width="80%"></kbd></p>

<br>

<a id="node-767bjei"></a>

<p align="center"><kbd><img src="assets/52jfkso1vn7.png" width="80%"></kbd></p>

<br>

<a id="node-a5a7saz"></a>

##### Compile và Load Data 

Dùng \\*Adam\\* optimizers, 
\\*categorical_crossentropy\\* loss function, 
Metrics dùng \\*accuracy

\\*Data là bộ\\* hand-sign data\\* bữa trước

<br>

<a id="node-vk2pcpz"></a>

<p align="center"><kbd><img src="assets/f72qprvf26.png" width="80%"></kbd></p>

<br>

<a id="node-w38x28y"></a>

<p align="center"><kbd><img src="assets/x1eutu3j3nf.png" width="80%"></kbd></p>

<br>

<a id="node-llaontp"></a>

##### ..và train model dùng 10 epochs, batch size
= 32

<br>

<a id="node-o7jn3o4"></a>

<p align="center"><kbd><img src="assets/gye4xaredar.png" width="80%"></kbd></p>

<br>

<a id="node-pstkmiz"></a>

<p align="center"><kbd><img src="assets/dgdgjidkomv.png" width="80%"></kbd></p>

<br>

<a id="node-qm5ku35"></a>

<p align="center"><kbd><img src="assets/28vvzzgt3tb.png" width="80%"></kbd></p>

<br>

<a id="node-sihqslo"></a>

##### Submit và load pretrain model: Đại khái là ổng kêu thích thì train lại
với nhiều  epoch hơn và load về cái model đã được train bằng GPU
để chạy thử xem accuracy bao nhiêu.

\\*What you should remember\\*:

• Very deep "plain" networks don't work in practice because vanishing
gradients make them hard to train.

• Skip connections help address the Vanishing Gradient problem.
They also make it easy for a ResNet block to learn an identity
function.

• There are two main types of blocks: The \\*identity block\\* and
the \\*convolutional block\\*.

• Very deep Residual Networks are built by stacking these blocks
together.

> [!NOTE]
> State of the art: HIện đại nhất. Ý là
> dùng cái này là hiện đại nhất rồi

<br>

<a id="node-o4835tc"></a>

<p align="center"><kbd><img src="assets/s5tvwi0r84n.png" width="80%"></kbd></p>

<br>

<a id="node-0nikjru"></a>

<p align="center"><kbd><img src="assets/b0ftgpxfwi.png" width="80%"></kbd></p>

<br>

<a id="node-43ajjml"></a>

##### 5 - Test on Your Own Image (Optional/Ungraded)

Dùng hình tự chụp để test thử thấy hình như không đúng.
Ổng có hỏi là h thử nghĩ xem tại sao ?

Có thể liên quan đến 'distribution' Hình dùng để train là trên
mạng, còn đây là hình tự  chụp dẫn đến training set và
production set bị khác distribution

Giải pháp là gì? Xem lại Course 3

> [!NOTE]
> Giải pháp là gì -> Xem lại course 3

<br>

<a id="node-z38sewd"></a>

<p align="center"><kbd><img src="assets/c38dg4ra3wt.png" width="80%"></kbd></p>

<br>

<a id="node-kultc2f"></a>

<p align="center"><kbd><img src="assets/pnch0fx45rl.png" width="80%"></kbd></p>

<br>

<a id="node-4twk889"></a>

##### 6 - Bibliography

This notebook presents the ResNet algorithm from He
et al. (2015).  The implementation here also took
significant inspiration and follows the structure given in
the GitHub repository of Francois Chollet:

• Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian
Sun - \\_Deep Residual Learning for Image Recognition
(2015) \\_

• Francois Chollet's GitHub repository: \\_https://github.
com/fchollet/deep-learning-models/blob/master/resnet50.
py\\_

<br>

<a id="node-tk8tm7u"></a>

### Programming Assignment: Transfer Learning With Mobilenet

<br>

<a id="node-2zintcl"></a>

#### Welcome to this week's assignment, where you'll be using transfer
learning on a pre-trained CNN to build an Alpaca/Not Alpaca
classifier! A pre-trained model is a network that's already been trained
on a large dataset and saved, which allows you to use it to customize
your own model cheaply and efficiently. The one you'll be using,
MobileNetV2, was designed to provide fast and computationally
efficient performance. It's been pre-trained on ImageNet, a dataset
containing over 14 million images and 1000 classes. By the end of
this assignment, you will be able to:

• \\/Create a dataset\\/ from a directory

• \\/Preprocess and augment data using the Sequential API\\/

• Adapt a \\/pretrained model to new data\\/ and train a classifier using
the Functional API and \\/MobileNet\\/

• Fine-tune a classifier's final layers to improve accuracy

<p align="center"><kbd><img src="assets/t0e8yr75ivd.png" width="80%"></kbd></p>

<br>

<a id="node-e8lbbbg"></a>

##### 1 - Packages

<br>

<a id="node-k4tczkc"></a>

<p align="center"><kbd><img src="assets/6k0nidzpvnp.png" width="80%"></kbd></p>

<br>

<a id="node-y2lloo5"></a>

##### 1.1 Create the Dataset and Split it into Training and
Validation Sets

Đại khái là dùng \\/\\*image_dataset_from_directory\\*()
của Keras để \\*load image từ  thư mục\\* \\/chỉ định,
return một \\*TensorFlow Dataset\\*, quy định sẵn batch
size, size để nó Resize image, tỉ lệ phân chia và tên
các gói để phân chia.

<br>

<a id="node-nuav5qu"></a>

<p align="center"><kbd><img src="assets/t8nijfei8t.png" width="80%"></kbd></p>

> [!NOTE]
> This code block is for loading image data from a directory and splitting it into training and
> validation datasets. It uses the **image_dataset_from_directory**() function **from the
> TensorFlow library**, which **creates a TensorFlow dataset** from image files located in a
> directory.
>
>
>
> The following are the explanations of the parameters used:
>
>
>
> • **BATCH_SIZE**: It defines the number of images to be processed in a single batch. Here,
> the batch size is set to 32, meaning that 32 images will be processed at a time.
>
>
>
> • **IMG_SIZE**: It is a tuple containing the height and width of the image. **The images will be**
> **resized to this size** before being used in the model. Here, the image size is set to (160,
> 160).
>
>
>
> • **directory**: It specifies the directory containing the image files.
>
>
>
> • **shuffle**: It determines whether the dataset should be shuffled before each epoch. Here, it is
> set to True, which means the dataset will be shuffled.
>
>
>
> • **validation_split**: It is the fraction of the data to be used for validation. Here, 20% of the data
> is used for validation and 80% for training.
>
>
>
> • **subset**: It specifies whether the dataset to be created is for training or validation. Here, the
> training subset is used for creating the training dataset, and the validation subset is used for
> creating the validation dataset.
>
>
>
> • **seed**: It is used to seed the random number generator. Here, it is set to 42 for
> reproducibility.
>
>
>
> The image_dataset_from_directory() function returns a TensorFlow dataset that can be
> used for training a machine learning model. In this code block, two datasets are created:
> train_dataset and validation_dataset, each containing images for training and validation
> respectively.

<br>

<a id="node-fl88cnb"></a>

<p align="center"><kbd><img src="assets/6w6amgku4lr.png" width="80%"></kbd></p>

> [!NOTE]
> Có một số hình bị sai

<br>

<a id="node-v04skp0"></a>

##### 2 - Preprocess and Augment Training Data:

Đại khái là nói về \\/\\*prefetch()\\*\\/ data đã từng dùng ở
assignment  trước để kiểu như chuẩn bị để khi chạy
G.D luôn có sẵn data. Lợi hại hơn nữa là nó có thể tối
ưu số lượng data chuẩn bị sẵn giùm mình luôn bằng
cách để \\/buffer_size = AUTOTUNE.

Lợi hại hơn nữa là nó có thể làm cái vụ Data Augmentation nữa\\/

<br>

<a id="node-d68gush"></a>

<p align="center"><kbd><img src="assets/2kd3z1tgmmh.png" width="80%"></kbd></p>

<br>

<a id="node-yltnmg0"></a>

##### Exercise 1 - data_augmenter:

Đại khái đơn giản là khởi tạo 1 Sequential và bỏ vào 2 layer:
RandomFlip và RandomRotation

data_augmentation = tf.keras.Sequential()
data_augmentation.add(RandomFlip('horizontal'))
data_augmentation.add(RandomRotation(0.2))

Sau đó xài thử trên một image xem chơi

<br>

<a id="node-cl5c7nl"></a>

<p align="center"><kbd><img src="assets/5ucjh23h2cr.png" width="80%"></kbd></p>

<br>

<a id="node-4sc2kvk"></a>

<p align="center"><kbd><img src="assets/2dtj8jcvt1s.png" width="80%"></kbd></p>

<br>

<a id="node-vvd14jf"></a>

##### \\*What you should remember:\\*

• When calling \\/image_data_set_from_directory\\/(), specify
the train/val subsets and match the seeds to prevent
overlap

• Use \\/prefetch\\/() to prevent memory bottlenecks when
reading from disk

• Give your model more to learn from with simple data
\\/augmentations\\/ like rotation and flipping.

• When using a pretrained model, it's best to \\/reuse the
weights\\/ it was trained on.

<br>

<a id="node-51jbgzc"></a>

<p align="center"><kbd><img src="assets/59scqbd3nh8.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng lại preprocess_input???

<br>

<a id="node-86nphy9"></a>

##### 3 - Using MobileNetV2 for Transfer Learning

<br>

<a id="node-14b5dzk"></a>

<p align="center"><kbd><img src="assets/4dgfy2ouisg.png" width="80%"></kbd></p>

<br>

<a id="node-v4bds0y"></a>

##### 3.1 - Inside a MobileNetV2 Convolutional Building Block

<br>

<a id="node-wyz3o6w"></a>

- **Đại khái là nói lại về
MobileNet v2 building block**

<br>

<a id="node-h6xt0bm"></a>

<p align="center"><kbd><img src="assets/kzi7gaim7ga.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/rrptqe9t66.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói lại về MobileNet v2 building block

<br>

<a id="node-i0yqy04"></a>

<p align="center"><kbd><img src="assets/7kcg0zfm29l.png" width="80%"></kbd></p>

<br>

<a id="node-kx9xht1"></a>

<p align="center"><kbd><img src="assets/1navdh2ffq7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó expand ra để tính toán được nhiều feature hữu
> ích hơn, sau đó co lại để đáp ứng điều kiện dung lượng bộ nhớ
> hạn hẹp -> Tốt hơn MobileNet v1 mà vẫn đáp ứng bộ nhớ nhỏ
>
> Đại khái như vậy là đủ hiểu
> MobileNet v2 rồi, muốn xem
> kĩ hơn để biết chi tiết thì đọc
> Paper của Sandler
>
> Từ nxnx3 -> nxnx18 thì ta dùng 18 cái filter 1x1x3
>
>
>
> Còn từ nxnx18 về lại nxnx3 thì dùng 3 cái filter 1x1x18

<br>

<a id="node-qy7juup"></a>

- **Đại khái là nó dùng lại cái MobileNet v2, \\/include_top\\/ =
True tức là giữ nguyên layer cuối (Softmax), và
weights đã được pretrained

Summary xem thì nhận thấy :

Đại khái là cấu trúc 1 Bottleneck layer thường sẽ như
vầy

-> Expand Conv - Expand BN - Expand Relu
Depthwise - Depthwise BN - Depthwise Relu Project
Conv - Project BN - Add (Skip connection) ->**

<br>

<a id="node-4aq3zy8"></a>

<p align="center"><kbd><img src="assets/5lyjnc9259n.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó dùng lại cái MobileNet v2,
> include_top = True tức là giữ nguyên layer cuối
> (Softmax), và weights đã được pretrained
>
> Chưa hiểu IMAGE_SHAPE = IMG_SIZE + (3,) là sao

<br>

<a id="node-qwvqwx6"></a>

<p align="center"><kbd><img src="assets/0gn55e4xqww7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cấu trúc 1 Bottleneck layer thường sẽ như vầy
>
>
>
> -> Expand Conv - Expand BN - Expand Relu
> Depthwise - Depthwise BN - Depthwise Relu
> Project Conv - Project BN - Add (Skip connection) ->

<br>

<a id="node-y7euwr5"></a>

##### What you should remember:

MobileNetV2's unique features are:

Depthwise separable convolutions that provide lightweight
feature filtering and creation Input and output bottlenecks
that preserve important information on either end of the
block

Depthwise separable convolutions deal with both spatial
and depth (number of channels) dimensions

<br>

<a id="node-2hy1aga"></a>

##### Đại khái là Xem thử performance của cái pretrain
network rao sao trên 1 batch data

Kết quả không tốt do pretrain data không có
alpaca, nên việc tiếp theo là bỏ layer cuối (top
layer) mà train lại layer cuối

<br>

<a id="node-iyz3k43"></a>

<p align="center"><kbd><img src="assets/8dgn47x5mq5.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là lấy 1 batch data (32 cái) ra và nói về cái format của kết
> quả, trả về 2 con số probability cao nhất ứng với khả năng của 1
> hình thuộc về 2 loại

<br>

<a id="node-elc6vaf"></a>

<p align="center"><kbd><img src="assets/cvsg0hg3w9b.png" width="80%"></kbd></p>

<br>

<a id="node-0qvs525"></a>

<p align="center"><kbd><img src="assets/055t5cqd1frm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là kết quả không tốt do pretrain data không có alpaca, nên
> việc tiếp theo là bỏ layer cuối (top layer) mà train lại layer cuối

<br>

<a id="node-sm90i3i"></a>

##### 3.2 - Layer Freezing with the Functional API

Đại khái ta sẽ bỏ layer cuối và đóng băng (freez)
cái pretrain network  đơn giản bằng cách set
params \\/include_top = false và , model.trainable =
false

Sau đó add 1 layer và train nó.\\/

<br>

<a id="node-1qp28rp"></a>

<p align="center"><kbd><img src="assets/tts1lyvbtd.png" width="80%"></kbd></p>

<br>

<a id="node-leaox76"></a>

##### Exercise 2 - alpaca_model:

Theo gợi ý lần lượt define model mới, dùng
lại Pretrain model  Add thêm layer cuối với
GlobalAveragePooling2D, Dropout, và
Dense với 1 unit

Chỉ chưa hiểu tại sao layer cuối dùng Linear
mà ko phải sigmoid

<br>

<a id="node-jvl7an8"></a>

<p align="center"><kbd><img src="assets/v3n65a0ar8o.png" width="80%"></kbd></p>

> [!NOTE]
> Tại sao lại Linear ở cuối mà ko phải Sigmoid

<br>

<a id="node-8rxpkhe"></a>

<p align="center"><kbd><img src="assets/eocle6pbo3b.png" width="80%"></kbd></p>

<br>

<a id="node-6nn326j"></a>

##### Compile & train model: Adam
optimizer, BinaryCrossentropy loss
function, accuracy

<br>

<a id="node-pxhp98a"></a>

<p align="center"><kbd><img src="assets/ajglxr5ckd.png" width="80%"></kbd></p>

<br>

<a id="node-6lrwjd9"></a>

<p align="center"><kbd><img src="assets/bd8avi581l4.png" width="80%"></kbd></p>

<br>

<a id="node-8jnggv3"></a>

<p align="center"><kbd><img src="assets/4klgdz5ngy2.png" width="80%"></kbd></p>

<br>

<a id="node-6ngmec7"></a>

##### 3.3 - Fine-tuning the Model:

Đại khái là gỡ băng 1 số layer cuối (bao nhiêu thì tuỳ
nên phải thử) để nó train các 'high feature' với data
của con alpaca, giữ nguyên các  'low feature'

<br>

<a id="node-qqyyzvw"></a>

<p align="center"><kbd><img src="assets/n1n83wxe87q.png" width="80%"></kbd></p>

<br>

<a id="node-q0knda2"></a>

##### Exercise 3:

Đại khái là lấy base_model ra (model2.
layers[4]) sửa lại một chút như unfreez từ
layer số 120 trở đi

<br>

<a id="node-2akp836"></a>

<p align="center"><kbd><img src="assets/d4s0v5rqyto.png" width="80%"></kbd></p>

> [!NOTE]
> tại sao model2.layers[4] ???

<br>

<a id="node-krj8wjc"></a>

<p align="center"><kbd><img src="assets/f5jxiy79b7.png" width="80%"></kbd></p>

> [!NOTE]
> Tốt hơn hẳn, validation_acc: 95%

<br>

<a id="node-vi5b393"></a>

<p align="center"><kbd><img src="assets/1wr8elwa5oh.png" width="80%"></kbd></p>

<br>

<a id="node-hti9kml"></a>

<p align="center"><kbd><img src="assets/zi68td1i8dp.png" width="80%"></kbd></p>

<br>

<a id="node-8rkv983"></a>

##### \\*What you should remember\\*:

• To adapt the classifier to new data: Delete the top layer, add a new
classification layer, and train only on that layer

• When freezing layers, avoid keeping track of statistics (like in the batch
normalization layer)

• Fine-tune the final layers of your model to capture high-level details near
the end of the network and potentially improve accuracy

\\*Congratulations! \\*You've completed this assignment on transfer learning
and fine-tuning. Here's a quick recap of all you just accomplished:

• Created a dataset from a directory

• Augmented data with the Sequential API

• Adapted a pretrained model to new data with the Functional API and
MobileNetV2

• Fine-tuned the classifier's final layers and boosted the model's accuracy

<br>

<a id="node-wzze8cn"></a>

## C4w3_object Detection

<br>

<a id="node-042h8wl"></a>

### Object Localization

<br>

<a id="node-gx18po4"></a>

#### Đại khái là bài toán bây giờ là không những chỉ phân loại -vd. có phải
xe hơi hay không (\\*classification)\\* mà còn vẽ cái box xung quanh cái
xe (\\*classification with localization)\\*. Và mở rộng hơn là detect nhiều
object khác loại trên cùng 1 image (\\*Object detection\\*)

Đại khái là muốn localize thì ta \\*sửa cái output layer\\*, v.d đang là 
Softmax ra 4 unit tương ứng 4 loại khả dĩ của cái hình, để
\\*thêm vào 4 chỉ số nữa là bx, by, bw, bh\\* = Vị trí của cái object.

Bằng cách \\*có thêm 4 thông số này trong training set,\\* đại khái
là ta có thể khiến cho network có thể học được cách xác định
được 4 chỉ số này trong các mẫu mới -> Localize được cái xe.

Đại khái là label (y) ngoài 4 unit (để chỉ ra 4 loại xe, người,
moto, nền, hoặc 4 thông số probability tương ứng) thì bây
giờ sẽ có thêm  Pc - 1 là object, 0 là nền (bx, by, bh, bw) -
vị trí cái object nếu có hoặc bỏ trống (?) nếu không, và C1
C1 C3 - class label hoặc Probability class

Cuối cùng là define Loss function có thể dùng \\*square của
từng cặp tương ưng giữa y^ và y \\*hoặc kĩ hơn thì dùng
từng hàm khác nhau  đ/v các chỉ số khác nhau như

- Binary Cross Entropy đ.v pC,
- Squared Error đ.v bx, by, bh, bw
- Log (Categorical Cross Entropy) đ.v C1, C2, C3

<br>

<a id="node-yu7c94s"></a>

<p align="center"><kbd><img src="assets/xcrzlu39rbc.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bài toán bây giờ là không những chỉ phân loại -vd. có phải
> xe hơi hay không (**classification)** mà còn vẽ cái box xung quanh cái
> xe (**classification with localization)**. Và mở rộng hơn là detect nhiều
> object khác loại trên cùng 1 image (**Object detection**)

<br>

<a id="node-w6aabs4"></a>

<p align="center"><kbd><img src="assets/b1b15ytfp6s.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là muốn localize thì ta **sửa cái output layer**, v.d đang là 
> Softmax ra 4 unit tương ứng 4 loại khả dĩ của cái hình, để
> **thêm vào 4 chỉ số nữa là bx, by, bw, bh** = Vị trí của cái object.
>
>
>
> Bằng cách **có thêm 4 thông số này trong training set,** đại khái
> là ta có thể khiến cho network có thể học được cách xác định
> được 4 chỉ số này trong các mẫu mới -> Localize được cái xe.

<br>

<a id="node-o0rp69r"></a>

<p align="center"><kbd><img src="assets/43zfvk2055h.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng là define Loss function có thể dùng **square của
> từng cặp tương ưng giữa y^ và y** hoặc kĩ hơn thì dùng
> từng hàm khác nhau đ/v các chỉ số khác nhau như
>
>
>
> - Binary Cross Entropy đ.v pC,
> - Squared Error đ.v bx, by, bh, bw
> - Log (Categorical Cross Entropy) đ.v C1, C2, C3
>
> Đại khái là label (y) ngoài 4 unit (để chỉ ra 4 loại xe, người,
> moto, nền, hoặc 4 thông số probability tương ứng) thì bây
> giờ sẽ có thêm  Pc - 1 là object, 0 là nền (bx, by, bh, bw) -
> vị trí cái object nếu có hoặc bỏ trống (?) nếu không, và C1
> C1 C3 - class label hoặc Probability class

<br>

<a id="node-5xm0m1b"></a>

### Landmark Detection

<br>

<a id="node-bm0bj0l"></a>

#### Đại khái là ta có thể dạy cho máy tính cách xác định các key point
trên khuôn mặt bằng cách tạo unit của output layer cho 'toạ độ' của
các  điểm đó l1x, l1y, l2x, l2y....

Dĩ nhiên label (Y train) cũng phải có những landmark này và công
việc xác định các điểm này tốn nhiều công sức (\\*laborious\\*)

Ứng dụng của cái này lấy ví dụ như chuyển khuôn mặt cười thành
khóc, những hiệu ứng của Snapchat như đội nón đều dựa trên
việc xác định được các landmark của khuôn mặt. \\*Recognize emotion\\*

Một ví dụ khác là xác định bộ khung - tư thế người.

<br>

<a id="node-y4wyqk0"></a>

<p align="center"><kbd><img src="assets/6u828gvgy2r.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ta có thể dạy cho máy tính cách xác định các key point
> trên khuôn mặt bằng cách tạo unit của output layer cho 'toạ độ' của
> các điểm đó **l1x, l1y, l2x, l2y....**
>
>
>
> Dĩ nhiên label (Y train) cũng phải có những landmark này và công
> việc xác định các điểm này tốn nhiều công sức (laborious)
>
>
>
> Ứng dụng của cái này lấy ví dụ như chuyển khuôn mặt cười thành
> khóc, những hiệu ứng của Snapchat như đội nón đều dựa trên
> việc xác định được các landmark của khuôn mặt. **Recognize emotion**
>
>
>
> Một ví dụ khác là xác định bộ khung - tư thế người.

<br>

<a id="node-xv8krg4"></a>

### Object Detection

<br>

<a id="node-0jcbytt"></a>

#### Đại khái là chạy (sliding) check từng ô đó xem có phải là xe hay không
(bằng cách bỏ vào bài toán classification).

Nhưng nhược điểm là với Deep Learning thì cách làm kiểu Sliding
Window này rất\\* tốn computational resource\\*.

Cách này đã có từ lâu khi Machine Learning còn thô sơ và người ta dùng
với very simple algorithm như Linear regression và nó cũng tạm được.

Nhưng h n.n với ConvNet rất tốn kém nên cách này không dùng được

<br>

<a id="node-9pt8l5i"></a>

<p align="center"><kbd><img src="assets/ipy9ody34.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là đầu tiên người ta train 1
> convNet để classify xe trước với các
> training set là hình xe crop sát với cái xe

<br>

<a id="node-ut28b4z"></a>

<p align="center"><kbd><img src="assets/9h81gq5rroj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là /**chạy (sliding) check từng ô**/ đó xem có phải là xe hay không
> (bằng cách **bỏ vào bài toán car classification**).
>
>
>
> Nhưng nhược điểm là với Deep Learning thì cách làm kiểu Sliding
> Window này rất  **tốn computational resource.**
>
>
>
> Cách này đã có từ lâu khi Machine Learning **còn thô sơ** và người ta dùng
> với very simple algorithm như Linear regression và nó cũng tạm được.
>
>
>
> Nhưng h n.n với ConvNet rất tốn kém nên cách này không dùng được

<br>

<a id="node-v16o8g6"></a>

### Convolutional Implementation
of Sliding Windows

<br>

<a id="node-te5puht"></a>

#### Đại khái là có thể thay cái 400 unit FC layer bằng Conv layer
1x1x400 bằng cách dùng 400 filter 5x5x16. Về mặt toán học tính
toán thì như nhau.

Tương tự với layer softmax

Vi diệu

Đại khái là thay vì dùng \\*sliding window \\*để cắt ra từng ô rồi bỏ
vào convNet để forward ra 1 kết quả xem có phải cái xe hay
không, làm vậy phải slide và forward 4 lần

Thay vì vậy, \\*cứ bỏ cái hình bự vào luôn\\* dùng cái \\*convNet\\*
nó sẽ tính ra kết quả cuối cùng chính là \\*chứa đựng kết quả của
4 lần riêng lẻ.\\*

<br>

<a id="node-4qez6v3"></a>

<p align="center"><kbd><img src="assets/l1jy3bk3bw.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là có thể thay cái 400 unit FC layer bằng
> Conv layer 1x1x400 bằng cách dùng 400 filter
> 5x5x16. Về mặt toán học tính toán thì như nhau.
>
>
>
> Tương tự với layer softmax

<br>

<a id="node-s7kb1k1"></a>

<p align="center"><kbd><img src="assets/rvcf7zminj.png" width="80%"></kbd></p>

> [!NOTE]
> Vi diệu
>
>
>
> Đại khái là thay vì dùng **sliding window** để cắt ra từng ô rồi bỏ vào
> convNet để forward ra 1 kết quả xem có phải cái xe hay không, làm vậy
> phải slide và forward 4 lần
>
>
>
> Thay vì vậy, **cứ bỏ cái hình bự vào luôn** dùng cái **convNet** nó sẽ tính ra
> kết quả cuối cùng chính là **chứa đựng kết quả của 4 lần riêng lẻ.**

<br>

<a id="node-7xhxv93"></a>

<p align="center"><kbd><img src="assets/s14obbwd49p.png" width="80%"></kbd></p>

<br>

<a id="node-agx5ry1"></a>

### Bounding Box Predictions

<br>

<a id="node-sxcr0wc"></a>

#### 1 Sliding windows have a \\*problem with accurate bounding box\\*
predictions \\*even with a convolutional implementation.\\*

2 The \\*YOLO\\* (You Only Look Once) algorithm offers a way to \\*output
more accurate bounding boxes\\* by \\*applying image classification and
localization algorithms\\* to a grid system.

3 The grid system divides the input image into cells, and for each
cell, a target label vector Y is defined, with the first output
representing whether there is an image in that grid cell.

4 \\*The target label vector Y includes PC, BX, BY, BH, BW\\* to specify
the bounding box and C1, C2, C3 to specify the object class.

5 The total volume of the target output is 3 by 3 by 8 because the
image is divided into a 3 by 3 grid system, and for each grid cell,
there is an eight-dimensional target vector Y.

6 To train the neural network, the input is the image, and the output
is the target label vector Y.

<br>

<a id="node-wuyg3fj"></a>

<p align="center"><kbd><img src="assets/veklxw325xl.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là làm sao để detect chính xác **bounding box -** một
> problem của Sliding window dù cho có áp dụng **Convolutional
> implementation vẫn chưa khắc phục được**. Kiểu như có thể B.B đúng phải hình chữ nhật nhưng window chỉ
> có hình vuông nên ko thể chính xác được

<br>

<a id="node-ef7tlca"></a>

<p align="center"><kbd><img src="assets/ed1zyr3z6rw.png" width="80%"></kbd></p>

> [!NOTE]
> "And the basic idea is you're going to take the image classification
> and localization algorithm that you saw in the first video of this
> week and apply that to each of the nine grid cells of this image."
>
>
>
> Đại khái là **áp dụng bài toán classification & localization cho mỗi
> ô trong 9 ô lưới**
>
>
>
> (3x3 để minh hoạ, thực tế có thể dùng **more fine grid - lưới dày
> hơn)**
>
>
>
> ???: YOLO nó assign cái object cho cái ô (grid cell)và ô giữa
> dù có dính một phần của cả hai object vẫn coi như không có
> object nào
>
>
>
> **Đại khái là ta define output là 1 volume 3x3x8 và dùng Back Prop
> để training (với y là cũng 3x3x8), xong ta predict với image mới ra
> một volume 3x3x8 để từ đó với mỗi ô ta xem nó có phải là object
> hay không bằng /pC/, nếu có thì là object gì bằng /C1, C2, C3/
> và 'toạ độ' bao nhiêu /bx, by, bw, bh**
>
>
>
> /Cách assign object to grid cell là ta tính được bx, by rồi thì tất
> nhiên ta xác định được nó nằm trong ô nào, nên dù cái object nó
> có trải dài qua nhiều ô thì cũng chỉ có 1 ô được assign
>
> Một vài nhận xét với phương pháp **YOLO**
>
>
>
> Không phải tính từng ô mà chỉ tính 1 phát một với ConvNet
>
>
>
> B.B không bị gom gọm trong kích thước Sliding Window
>
>
>
> Chạy nhanh

<br>

<a id="node-9h7ee68"></a>

<p align="center"><kbd><img src="assets/j762exo8owt.png" width="80%"></kbd></p>

<br>

<a id="node-66c1mc5"></a>

### Intersection Over Union

<br>

<a id="node-4k2j74s"></a>

#### Đại khái là tính ra chỉ số \\*Itersection / Unit (giao hợp)\\* và quyết
định môt threshold để xem nó có correct hay không

1 Introduction to Intersection Over Union (IoU) function for
evaluating object detection algorithms.

2 IoU computes the overlap between the ground-truth bounding
box and the predicted bounding box.

3 Conventionally, an IoU of 0.5 or greater is considered correct,
but more stringent criteria can also be used.

4 IoU can be used to measure the overlap between any two
bounding boxes and is a way to measure similarity.

5 IoU is used in non-max suppression, which is a tool to improve
the performance of object detection algorithms.

6 IoU is not to be confused with the promissory note concept in
IoU.

<br>

<a id="node-2dr2hkg"></a>

<p align="center"><kbd><img src="assets/tf4ulq1uonj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tính ra chỉ số Itersection / Unit (giao hợp)
> và quyết định môt threshold để xem nó có correct hay 
> không
>
>
>
> Thường ta lấy 0.5 nhưng có thể tăng lên nếu muốn strict hơn

<br>

<a id="node-tvl8nlj"></a>

### Non-max Suppression

<br>

<a id="node-0tbjkq4"></a>

#### Main ideas:  1 Object detection algorithms may find multiple
detections of the same object.

2 Non-max suppression is a method to ensure that object
detection algorithms only detect each object once.

3 Non-max suppression works by \\*selecting the most confident
detection\\* and then \\*suppressing overlapping detections.\\*

4 The first step of non-max suppression is to \\*discard all boxes
with a probability less than or equal to some threshold.\\*

5 The next step is to repeatedly \\*pick the box with the highest
probability\\* and \\*output it as a prediction\\* and \\*suppress all box
that overlap it\\* until there are no more boxes left.

<br>

<a id="node-17zsm92"></a>

<p align="center"><kbd><img src="assets/zxeq34n4he.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là trong quá trình có thể nhiều cell cùng detect rằng nó
> chứa center của cái xe từ đó thành ra nó detect cái xe nhiều lần

<br>

<a id="node-hh5frs7"></a>

<p align="center"><kbd><img src="assets/b27zy6j022k.png" width="80%"></kbd></p>

> [!NOTE]
> Cái Non-max Suppresion sẽ làm là với mỗi object, nó xác định cái B.B
> có Pc lớn nhất và xác định các b.b khác mà overlap nhiều với cái đầu
>
>
>
> Cái tên thể hiện hết: Suppression - Bỏ đi, Non-max là không  phải cái lớn
> nhất (về Probability).

<br>

<a id="node-zttcw8l"></a>

<p align="center"><kbd><img src="assets/eh6zadyfbh8.png" width="80%"></kbd></p>

<br>

<a id="node-w7s0if5"></a>

<p align="center"><kbd><img src="assets/mr9hb7neg3.png" width="80%"></kbd></p>

<br>

<a id="node-2ne3lb6"></a>

<p align="center"><kbd><img src="assets/t71xf57x2z.png" width="80%"></kbd></p>

<br>

<a id="node-gdewcue"></a>

<p align="center"><kbd><img src="assets/pfji8bx17wp.png" width="80%"></kbd></p>

<br>

<a id="node-mh4jkvx"></a>

### Anchor Boxes

<br>

<a id="node-y8t2efu"></a>

#### 1 Object detection with grid cells has a \\*limitation of detecting only
one object per cell\\*.

2 Anchor boxes are \\*pre-defined shapes used to associate multiple
predictions with different anchor boxes.\\*

3 Anchor boxes \\*allow for detecting objects with different shapes
and sizes in a single grid cell\\*.

4 The \\*target label\\* with anchor boxes consists of a \\*3 by 3 grid and
anchor box pair, with each pair containing 8 dimensions for object
detection.\\*

5 Anchor boxes are assigned to the same grid cell as before, but
with the highest Intersection over Union (IoU) with the object's
shape. -> ???

6 The output Y is 3 by 3 by 16 with two anchor boxes or 3 by 3 by
24 with three anchor boxes.

7 Anchor boxes allow for better object detection and localization
within a single grid cell.

<br>

<a id="node-574c607"></a>

<p align="center"><kbd><img src="assets/rzk7tfbl3ga.png" width="80%"></kbd></p>

<br>

<a id="node-1y6bnz3"></a>

<p align="center"><kbd><img src="assets/77s3y68b3p.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thay đổi 1 chút, trước đây trong label y sẽ define 8 giá trị Pc,
> bx, by, bh, bw, C1, C2, C3 đồng nghĩa với việc: **object thì nó sẽ gán vào
> một cell** bởi các thông số đó. Hiểu đại khái là giả sử có 2 object thì
> trong các ô, chỉ có 2 ô sẽ có các giá trị bx, by, bh, bw thôi.
>
>
>
> Còn bây giờ, 2 object sẽ được 'đánh dấu' / gán vào thêm 2 cái  anchor
> box nữa

<br>

<a id="node-orisrhk"></a>

<p align="center"><kbd><img src="assets/zyo0y46wl09.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu lắm, hiểu là anchor box nó define
> như vậy nhưng cụ thể làm gì thì chưa rõ

<br>

<a id="node-2ef3e60"></a>

### Yolo Algorithm

<br>

<a id="node-da2ck6e"></a>

#### 1 The YOLO object detection algorithm combines various components of
object detection.

2 To construct the training set, the appropriate \\*target vector y is formed
for each of the nine grid cells.\\*

3 The final output volume is 3 by 3 by 16, but in practice, it may be more
like 19 by 19 by 16 or 19 by 19 by 24 if more anchor boxes are used.

4 The neural network makes predictions by outputting a 3 by 3 by 2 by 8
volume, where for each of the nine grid cells, a vector is obtained.

5 Non-max suppression is run to get rid of low probability predictions, and
independently run non-max suppression for each of the three classes of
objects to detect pedestrians, cars, and motorcycles.

<br>

<a id="node-7bg8v1r"></a>

<p align="center"><kbd><img src="assets/4tdjizv2jip.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là training label sẽ có dạng như vậy với 2 object là
> (3x3) x (số anchor) x (5 + số class) Thực tế có thể là 19x19

<br>

<a id="node-msgnvt0"></a>

<p align="center"><kbd><img src="assets/q4tqhh33ype.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi sau khi train, và predict new image thì: Chỉ số đầu pc
> của mỗi cell sẽ cho biết có object hay không, Nếu có thì
> các thông số sẽ là vị trí và class của nó

<br>

<a id="node-c5djewp"></a>

<p align="center"><kbd><img src="assets/ov9fkuxa06b.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/kw8nys4obj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jxjt5bjisv7.png" width="80%"></kbd></p>

<br>

<a id="node-nudpzcy"></a>

<p align="center"><kbd><img src="assets/kxqy6gke2cj.png" width="80%"></kbd></p>

> [!NOTE]
> Xong tiếp theo là làm quy trình non-max
> đv mỗi class để xoá đi các bounding box

<br>

<a id="node-vntfvtg"></a>

### Region Proposals

<br>

<a id="node-nmo337u"></a>

#### 1 Introduction to region proposals in object detection

2 Comparison between sliding windows and region
proposals

3 R-CNN algorithm and its implementation of region
proposals

4 Improvements to the R-CNN algorithm, including Fast
R-CNN and Faster R-CNN

5 The influence of region proposals in computer vision

6 The potential for a single-step approach in object
detection, similar to the You Only Look Once (YOLO)
algorithm.

<br>

<a id="node-ouvtprc"></a>

<p align="center"><kbd><img src="assets/gt3kzejoq8.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái idea là thay vì chạy (Sliding window + classification) hoặc Sliding
> window with ConvNet, trong đó ta đều check những cell mà rõ ràng là
> không có khả năng có object, thì ta sẽ dùng một cái gọi là **Segmentation
> algorithm** để xác định các **vùng có khả năng có object nhất sau đó chỉ
> run trên những vùng này**

<br>

<a id="node-6jwsbde"></a>

<p align="center"><kbd><img src="assets/bcfr318aj1.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái cái R-CNN nó chậm do bước
> Region Proposal  nên có vài cách khác
> dùng Conv để tăng tốc việc này.

<br>

<a id="node-o0hu99p"></a>

### Semantic Segmentation With U-net

<br>

<a id="node-vgjapqc"></a>

#### 1. Semantic segmentation là gì?

Semantic segmentation là một kỹ thuật thị giác máy tính liên quan đến gán nhãn cho mỗi
pixel trong hình ảnh với một nhãn lớp tương ứng. Mục tiêu của semantic segmentation là
tạo ra một đường viền chi tiết của một đối tượng, để chúng ta biết chính xác những pixel
thuộc về đối tượng và những pixel nào không thuộc về đối tượng đó.

2. Ứng dụng của semantic segmentation:

Semantic segmentation có nhiều ứng dụng thương mại, bao gồm xe tự lái, hình ảnh y học
và lập kế hoạch phẫu thuật. Ví dụ, trong xe tự lái, semantic segmentation có thể được sử
dụng để xác định các bề mặt lái được, giúp cho xe dễ dàng di chuyển.

3.Làm thế nào semantic segmentation hoạt động?

Trong semantic segmentation, mục tiêu là gán nhãn lớp cho mỗi pixel trong hình ảnh. Để
làm được điều này, chúng ta cần sửa đổi kiến trúc của một mạng neural tích chập (CNN).
Các lớp cuối cùng của CNN được loại bỏ và mạng được sửa đổi để tăng dần kích thước
đầu ra, sao cho nó phù hợp với kích thước của hình ảnh đầu vào.

4.Làm thế nào để phân đoạn hình ảnh bằng semantic segmentation?

Để phân đoạn một hình ảnh bằng semantic segmentation, CNN tạo ra một ma trận nhãn
lớp cho mỗi pixel trong hình ảnh. Số hàng và cột trong ma trận tương ứng với chiều cao và
chiều rộng của hình ảnh đầu vào, trong khi số kênh tương ứng với số nhãn lớp. Ví dụ, nếu
chúng ta muốn phân đoạn một hình ảnh thành các ô tô và tòa nhà, chúng ta sẽ có hai kênh:
một cho ô tô và một cho tòa nhà.

5.Transpose convolution:

Để tăng kích thước ma trận đầu ra trong semantic segmentation, chúng ta sử dụng một
phép toán gọi là transpose convolution. Transpose convolution được sử dụng để "hoàn
ngược" quá trình giảm mẫu xuất hiện ở các lớp trước của CNN. Đầu ra của một transpose
convolution có cùng hình dạng với đầu vào, nhưng v

<br>

<a id="node-7m5kwus"></a>

<p align="center"><kbd><img src="assets/pct4goex7a9.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ta đã trải qua 2 bước, 1 là **object recognition** - bài toán
> classification để xác định xem nó là hình con mèo hay không
> 2 là **object detection** - nâng cấp hơn, không những xác định con mèo
> mà còn vẽ cái bounding box quanh con mèo.
>
>
>
> Bây giờ bài toán thứ 3 nâng cấp hơn nữa là không những vẽ b.b
> mà vẽ sát cái viền của con mèo - **segmentation**

<br>

<a id="node-o8yy95p"></a>

<p align="center"><kbd><img src="assets/s4zjy2s4a3c.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là một số ứng dụng của cái
> này, sẽ giúp ích rất nhiều

<br>

<a id="node-cl91gkw"></a>

<p align="center"><kbd><img src="assets/9uzpdqffwsc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sy0v2en3hbe.png" width="80%"></kbd></p>

> [!NOTE]
> N.n phải output 1 matrix như này: mỗi pixel
> trong image đều được label

<br>

<a id="node-0hogk7h"></a>

<p align="center"><kbd><img src="assets/nq29zx5zyg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sal5w0j5b9j.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là để làm segmentation phải thay mấy cái layer cuối theo kiểu
> tăng cái size lên như này để về lại size ban đầu của input image. Cái này
> cần tới **Transpose Operation**

<br>

<a id="node-0401bzo"></a>

### Transpose Convolutions

<br>

<a id="node-e7ri72k"></a>

#### Trong bài giảng này, người giảng giải thích về khái niệm transpose
convolution, là một phần quan trọng trong kiến trúc đơn vị. Để làm
cho đầu vào kích thước 2x2 được phóng to lên kích thước 4x4, ta
có thể sử dụng transpose convolution. Khác với convolution thông
thường, transpose convolution sử dụng một bộ lọc (filter) để phóng
to dữ liệu đầu ra thay vì áp dụng bộ lọc lên đầu vào. Bài giảng cung
cấp một ví dụ chi tiết về cách sử dụng transpose convolution với
đầu vào 2x2, bộ lọc 3x3, padding 1 và stride 2 để phóng to đầu vào
thành đầu ra 4x4. Một vài bước tính toán được trình bày để minh
họa quá trình phóng to. Cuối cùng, transpose convolution được cho
là một cách hiệu quả để phóng to dữ liệu đầu vào nhỏ hơn lên kích
thước lớn hơn trong bối cảnh của thuật toán học sâu.

<br>

<a id="node-7yyw206"></a>

<p align="center"><kbd><img src="assets/kn9r5rgnulo.png" width="80%"></kbd></p>

<br>

<a id="node-95pypkg"></a>

<p align="center"><kbd><img src="assets/figak30c63d.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hstjrrpdpaf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/b25ygojfxsw.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zb9y1kv8ew.png" width="80%"></kbd></p>

<br>

<a id="node-n0zslcz"></a>

<p align="center"><kbd><img src="assets/a914vmdjak5.png" width="80%"></kbd></p>

<br>

<a id="node-6ed70i9"></a>

### U-net Architecture Intuition

<br>

<a id="node-oatvxda"></a>

#### - Đại khái là sử dụng \\*convolution thông thường phần
đầu\\* của mạng nơ-ron.

- Sử dụng \\*transpose convolution trong phần thứ hai
của mạng nơ-ron để khôi phục lại kích thước ảnh gốc.\\*

- Giới thiệu \\*skip connections\\* từ các lớp trước đến
các lớp sau để cải thiện hiệu suất bằng cách \\*cung cấp
thông tin bối cảnh cấp cao và thông tin kết cấu cấp
thấp\\* để cho phép mạng nơ-ron bắt được thông tin
không gian chi tiết, tinh vi.

<br>

<a id="node-wb61u18"></a>

<p align="center"><kbd><img src="assets/gjqix57grl5.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dùng Transpose Conv ở những layer cuối và **Skip
> Connection** cho phép cung cấp **những low-level feature nhưng
> chi tiết** để cộng với những **high-level feature nhưng chung
> chung** để tạo nên kết quả cuối cùng

<br>

<a id="node-5pdwzyp"></a>

### U-net Architecture

<br>

<a id="node-9oqag6f"></a>

#### 1. Qua 1 vài lớp Conv layer (Conv Relu) giữ nguyên kích thước  (với
same padding) nhưng tăng dimensions (tăng số filter lên)

2,3,4. Dùng (Max) Pooling, giảm kích thước xuống rồi lại qua vài lớp
Conv-reLu để tăng dimension

5. Dùng Transpose Conv để (chưa tăng kích thước) mà giảm
dimensions xuống rồi ghép với cái Skip Connection từ bước 4.

6,7,8. Dùng Transpose Conv để tăng kích thước + giảm dimensions
xuống rồi ghép với cái Skip Connection từ bước 3,2,1

9. Dùng Conv ReLU cho những layer cuối lúc này kích thước đã  phục hồi ban
đầu, layer cuối dùng Conv (1x1) để xuất ra kết quả cuối cùng.

<br>

<a id="node-rv7kyd1"></a>

<p align="center"><kbd><img src="assets/i6m03jz4d6p.png" width="80%"></kbd></p>

> [!NOTE]
> Đây là một trong những cái kết trúc
> neural network nền tảng quan trọng
> nhất của Computer Vision

<br>

<a id="node-03mlvip"></a>

<p align="center"><kbd><img src="assets/77ulqjpdj7n.png" width="80%"></kbd></p>

<br>

<a id="node-kxkgwbs"></a>

<p align="center"><kbd><img src="assets/zjmg1w4ezg.png" width="80%"></kbd></p>

> [!NOTE]
> 1. Qua 1 vài lớp /**Conv layer (Conv Relu)**/ **giữ nguyên kích thước**  (với
> same padding) nhưng **tăng dimensions** (tăng số filter lên)
>
>
>
> 2,3,4. Dùng /**(Max) Pooling**/, giảm kích thước xuống rồi lại qua vài lớp
> Conv-reLu để tăng dimension
>
>
>
> 5. Dùng /**Transpose Conv/** để (chưa tăng kích thước) mà **giảm
> dimensions xuống** rồi ghép với cái Skip Connection từ bước 4.
>
>
>
> 6,7,8. Dùng /**Transpose Conv/** để **tăng kích thước** + **giảm dimensions
> xuống** rồi ghép với cái Skip Connection từ bước 3,2,1
>
>
>
> 9. Dùng Conv ReLU cho những layer cuối lúc này kích thước đã  phục hồi ban
> đầu, layer cuối dùng Conv (1x1) để xuất ra kết quả cuối cùng.

<br>

<a id="node-fzphp0c"></a>

### Quiz

<br>

<a id="node-tjv14x9"></a>

<p align="center"><kbd><img src="assets/13btp2pmoele.png" width="80%"></kbd></p>

<br>

<a id="node-o7ddlzn"></a>

<p align="center"><kbd><img src="assets/ljzpmubk27n.png" width="80%"></kbd></p>

<br>

<a id="node-wcqneyw"></a>

<p align="center"><kbd><img src="assets/lhu5gvgt3bo.png" width="80%"></kbd></p>

<br>

<a id="node-qcumihc"></a>

<p align="center"><kbd><img src="assets/4uwr1mkdgby.png" width="80%"></kbd></p>

<br>

<a id="node-fhkwqho"></a>

<p align="center"><kbd><img src="assets/rg46r7iv10h.png" width="80%"></kbd></p>

<br>

<a id="node-e733edc"></a>

<p align="center"><kbd><img src="assets/k8injs5p4eb.png" width="80%"></kbd></p>

<br>

<a id="node-hy1lu77"></a>

<p align="center"><kbd><img src="assets/9ryhxyctium.png" width="80%"></kbd></p>

<br>

<a id="node-gcwz4sq"></a>

<p align="center"><kbd><img src="assets/xwkymr70gl.png" width="80%"></kbd></p>

<br>

<a id="node-ftiko15"></a>

<p align="center"><kbd><img src="assets/wxp4be2poij.png" width="80%"></kbd></p>

<br>

<a id="node-hy8ettj"></a>

<p align="center"><kbd><img src="assets/uc9vorxsqag.png" width="80%"></kbd></p>

<br>

<a id="node-4bmwy2z"></a>

### Programming Assignment

<br>

<a id="node-klfpive"></a>

#### By the end of this assignment, you'll be able to:

Detect objects in a car detection dataset
Implement non-max suppression to increase accuracy
Implement intersection over union
Handle bounding boxes, a type of image annotation popular in deep learning

<p align="center"><kbd><img src="assets/das6jz5ig09.png" width="80%"></kbd></p>

<br>

<a id="node-7059o2l"></a>

##### \\*..\\*

<br>

<a id="node-d18wq76"></a>

- **Packages**

<br>

<a id="node-nvjxmay"></a>

<p align="center"><kbd><img src="assets/ju7f6lon0il.png" width="80%"></kbd></p>

<br>

<a id="node-ck62ams"></a>

- **1 - Problem Statement**

<br>

<a id="node-ppuvi8w"></a>

<p align="center"><kbd><img src="assets/2v6nrz85ue.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/a7dhtjbxgpi.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là đi vòng vòng chụp hình, về vẽ **Bounding
> Box**  quanh cái xe để tạo training set
>
>
>
> Đại khái ở đây chỉ có 1 object (xe), nếu có 80 class thì có
> thể dùng c1, c2,....c80 hoặc dùng 80 one-hot encoded
> vector

<br>

<a id="node-3oy4vv7"></a>

- **2 - Yolo**

<br>

<a id="node-mqg74z0"></a>

- **YOLO: Đại khái là nó (algorithm) chỉ cần look qua cái
image 1 lầnm lúc forward  propagation để predict**

<br>

<a id="node-shvnbfo"></a>

- **2.1 - Model Details**

<br>

<a id="node-7vuk1ib"></a>

<p align="center"><kbd><img src="assets/zs97er0795l.png" width="80%"></kbd></p>

<br>

<a id="node-8v6jx0n"></a>

<p align="center"><kbd><img src="assets/2b9krx9dpek.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/v2og5f3ogne.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu trong lecture chỉ có 2 anchor box, và 3 class nên 
> y = [Pc, bx, by, bh, bw, c1, c2, c3, ..
> ..Pc, bx, by, bh, bw, c1, c2, c3]
>
>
>
> Thì ở đây là có 5 anchorbox và 80 cái class !!!
>
>
>
> [Pc, bx, by, bh, bw, c1, c2, c3, ..c80 //Anchor box 1
> ..Pc, bx, by, bh, bw, c1, c2, c3..c80  //Anchor box 2
> ..Pc, bx, by, bh, bw, c1, c2, c3..c80  //Anchor box 3
> ..Pc, bx, by, bh, bw, c1, c2, c3..c80  //Anchor box 4
> ..Pc, bx, by, bh, bw, c1, c2, c3..c80  //Anchor box 5
> ]

<br>

<a id="node-dhid6jk"></a>

<p align="center"><kbd><img src="assets/cn61gr8ew6d.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái mỗi 1 cell sẽ có 5 box (như khi mình define anchor box),
> tính 5 con số pc của mỗi cell để biết khả năng (probability) cell đó có
> object hay không. 
> Rồi nhân với [c1, ...c80] để ra khả năng có object class nào
>
>
>
> **Đang nói cho 1 cell nha:**
>
>
>
> Box 1:
>
>
>
> pc*[c1,...c80] để ra [pc*c1, pc*c2,....pc*c80]
>
>
>
> Trong 80 con số này, **số lớn nhất** (v.d pcc3) sẽ thể hiện khả năng 
> cao (nhất) box 1 này chứa object class số 3 (ở đây class #3 là xe hơi)
> -> Assign blah blah có nghĩa đại khái là mình sẽ tuyên bố
> box 1 sẽ chứa xe hơi (class #3) và class score là 44%
>
>
>
> **Tính tương tự cho 4 box còn lại (của 1 cell)
>
>
>
>
> Vậy làm cùng lúc cho 19x19 (tổng số cell) x5 (5 box mỗi cell) thì sao**

<br>

<a id="node-bwmv5p6"></a>

<p align="center"><kbd><img src="assets/czoxg54lti8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/55l7e43ko6k.png" width="80%"></kbd></p>

<br>

<a id="node-gjsollw"></a>

- **2.2 - Filtering with a Threshold on Class Scores

Đại khái là thay vì để chung các thông số của 1 box trong 1 vector

[Pc, bx, by, bh, bw, c1, c2...c80]

thì ta chia ra thành 3 vector:

- Box confidence: Pc

- Boxes: bx, by, bh, bw

- Boxes class probability: c1, c2, ...c80

19x19x (số box) x (1 object probability + 4 thông số vị trí object

+ 80 thông số class prob)

tách thành

- Box confidence: 19x19x (số box) x (1 object probability)

- Boxes: bx, by, bh, bw: 19x19x (số box) x (4 thông số vị trí object)

- Boxes class probability: c1, c2, ...c80: 19x19x (số box) x (80 thông
số class prob)**

<br>

<a id="node-xr6zwha"></a>

<p align="center"><kbd><img src="assets/tv1w8jpggd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thay vì để chung các thông số của 1 box trong 1 vector
>
>
>
> [Pc, bx, by, bh, bw, c1, c2...c80]
>
>
>
> thì ta chia ra thành 3 vector:
>
>
>
> - Box confidence: Pc
>
>
>
> - Boxes: bx, by, bh, bw
>
>
>
> - Boxes class probability: c1, c2, ...c80
>
>
>
> 19x19x (số box) x (1 object probability + 4 thông số vị trí object + 80 thông số
> class prob)
>
>
>
> tách thành
>
>
>
> - Box confidence: 19x19x (số box) x (1 object probability)
>
>
>
> - Boxes: bx, by, bh, bw: 19x19x (số box) x (4 thông số vị trí object)
>
>
>
> - Boxes class probability: c1, c2, ...c80: 19x19x (số box) x (80 thông số class
> prob)

<br>

<a id="node-texje5n"></a>

<p align="center"><kbd><img src="assets/24jzu8fuv89.png" width="80%"></kbd></p>

<br>

<a id="node-12ykjdf"></a>

- **Exercise 1 - yolo_filter_boxes**

<br>

<a id="node-lmm6fhv"></a>

<p align="center"><kbd><img src="assets/n4b8iigj2.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tính Pc trong của một box bằng cách nhân Pc
> object với  vector class probability [c1, c2, c3...c80]
>
>
>
> - Để ra 'probability of an object with class c_i'  
> [Pc*c1, Pc*c2, ... , Pc*c80]
>
>
>
> - Lấy ra giá trị lớn nhất cùng với index của nó trong 80 cái 
> Dùng **argmax** và **reduce_max
>
>
>
> -** Cuối cùng là dùng boolean_max để loại bỏ những cái dưới
> Threshold
>
>
>
> Do mình đang làm đv dimension cuối nên axis=-1 để nó lấy cái cuối

<br>

<a id="node-io1hupp"></a>

<p align="center"><kbd><img src="assets/j0e517j7aj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/rd5rch9vwan.png" width="80%"></kbd></p>

<br>

<a id="node-f2tzr6a"></a>

<p align="center"><kbd><img src="assets/vhvzjwdwlse.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vt2rwqi5dms.png" width="80%"></kbd></p>

<br>

<a id="node-ftj4o97"></a>

<p align="center"><kbd><img src="assets/mxoybxu5rd.png" width="80%"></kbd></p>

<br>

<a id="node-m0o6sak"></a>

<p align="center"><kbd><img src="assets/b4lfqro1j6.png" width="80%"></kbd></p>

<br>

<a id="node-1ikp85g"></a>

- **2.3 - Non-max Suppression**

<br>

<a id="node-r8c4lg4"></a>

<p align="center"><kbd><img src="assets/9ul9b8tndge.png" width="80%"></kbd></p>

<br>

<a id="node-y47vzcw"></a>

- **Exercise 2 - iou**

<br>

<a id="node-9pgzk1z"></a>

<p align="center"><kbd><img src="assets/mzl1xwn9nri.png" width="80%"></kbd></p>

<br>

<a id="node-hse1e71"></a>

<p align="center"><kbd><img src="assets/o2z6jah5al.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu hai box không overlap nhau, thì intersection phải bằng
> 0  -> inter_width  = max(0, inter_area's width) inter_height  =
> max(0, inter_area's height)

<br>

<a id="node-lqpzern"></a>

<p align="center"><kbd><img src="assets/3vmquynfodq.png" width="80%"></kbd></p>

<br>

<a id="node-txey19u"></a>

- **2.4 - YOLO Non-max Suppression**

<br>

<a id="node-bzcgt79"></a>

<p align="center"><kbd><img src="assets/6dv2spz3ndo.png" width="80%"></kbd></p>

<br>

<a id="node-xaiopwq"></a>

- **Exercise 3 - yolo_non_max_suppression**

<br>

<a id="node-3b0zgv3"></a>

<p align="center"><kbd><img src="assets/55yufn6d8hb.png" width="80%"></kbd></p>

<br>

<a id="node-cv5lkx9"></a>

<p align="center"><kbd><img src="assets/e1exokq4ifq.png" width="80%"></kbd></p>

<br>

<a id="node-msfunw2"></a>

<p align="center"><kbd><img src="assets/zu8bxurxs8p.png" width="80%"></kbd></p>

<br>

<a id="node-53zildw"></a>

- **2.5 - Wrapping Up the Filtering**

<br>

<a id="node-pp678rg"></a>

<p align="center"><kbd><img src="assets/4cfmkxfl8zu.png" width="80%"></kbd></p>

<br>

<a id="node-uw1f9g8"></a>

- **Exercise 4 - yolo_eval**

<br>

<a id="node-o5hoe7l"></a>

<p align="center"><kbd><img src="assets/mg976l8hrib.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/rdxop6lqh3n.png" width="80%"></kbd></p>

<br>

<a id="node-mjgb2ai"></a>

<p align="center"><kbd><img src="assets/b82sc2yre8l.png" width="80%"></kbd></p>

<br>

<a id="node-j60093k"></a>

- **3 - Test YOLO Pre-trained Model on Images: Đại khái là
dùng Pretrained YOLO model để detect**

<br>

<a id="node-2zfjxjk"></a>

- **3.1 - Defining Classes, Anchors and Image Shape**

<br>

<a id="node-zq25xxv"></a>

<p align="center"><kbd><img src="assets/ee5e71s7o8a.png" width="80%"></kbd></p>

<br>

<a id="node-dwoaep9"></a>

- **3.2 - Loading a Pre-trained Model**

<br>

<a id="node-r3ucbos"></a>

<p align="center"><kbd><img src="assets/waqeq73qrc.png" width="80%"></kbd></p>

<br>

<a id="node-5ku04jz"></a>

- **3.3 - Convert Output of the Model to Usable Bounding Box Tensors**

<br>

<a id="node-xeassd6"></a>

<p align="center"><kbd><img src="assets/r0m7crsi1ob.png" width="80%"></kbd></p>

<br>

<a id="node-pjv8twv"></a>

- **3.4 - Filtering Boxes**

<br>

<a id="node-js4t6fx"></a>

<p align="center"><kbd><img src="assets/440ldlnhug3.png" width="80%"></kbd></p>

<br>

<a id="node-reudco3"></a>

- **3.5 - Run the YOLO on an Image**

<br>

<a id="node-2bqitl1"></a>

<p align="center"><kbd><img src="assets/brvsz3y1f8a.png" width="80%"></kbd></p>

<br>

<a id="node-j3mz5hb"></a>

<p align="center"><kbd><img src="assets/3szwtdxoo6w.png" width="80%"></kbd></p>

<br>

<a id="node-lyqt2lu"></a>

<p align="center"><kbd><img src="assets/7r0eosve5sv.png" width="80%"></kbd></p>

<br>

<a id="node-0ng3a43"></a>

<p align="center"><kbd><img src="assets/2gokrdv8fzg.png" width="80%"></kbd></p>

<br>

<a id="node-bbiztl3"></a>

<p align="center"><kbd><img src="assets/qv6ib6v5ooo.png" width="80%"></kbd></p>

<br>

<a id="node-drefdsj"></a>

- **4 - Summary for YOLO**

<br>

<a id="node-o056be4"></a>

<p align="center"><kbd><img src="assets/rsq3w93okt9.png" width="80%"></kbd></p>

<br>

<a id="node-zm2xtxw"></a>

- **5 - References**

<br>

<a id="node-gjqtg85"></a>

<p align="center"><kbd><img src="assets/l2drzllijd.png" width="80%"></kbd></p>

<br>

<a id="node-muhumkn"></a>

### PROGRAMMING ASSIGNMENT: \\*Image Segmentation with U-Net\\*

<br>

<a id="node-z4nfxwe"></a>

#### Welcome to the final assignment of Week 3 in Course 4 of the Deep Learning
Specialization! You'll be building your own U-Net, a type of CNN designed for
quick, precise image segmentation, and using it to predict a label for every
single pixel in an image - in this case, an image from a self-driving car dataset.

<p align="center"><kbd><img src="assets/scj7emula7d.png" width="80%"></kbd></p>

<br>

<a id="node-5cy5s8u"></a>

##### Image Segmentation with U-Net

<br>

<a id="node-mo6jpig"></a>

<p align="center"><kbd><img src="assets/0p659hk5shph.png" width="80%"></kbd></p>

<br>

<a id="node-rxfd909"></a>

##### 1 - Packages

<br>

<a id="node-qy31l7b"></a>

<p align="center"><kbd><img src="assets/rxvmm1162z.png" width="80%"></kbd></p>

<br>

<a id="node-104nvvx"></a>

##### 2 - Load and Split the Data

<br>

<a id="node-9z87g6u"></a>

<p align="center"><kbd><img src="assets/slcfg4wffp.png" width="80%"></kbd></p>

<br>

<a id="node-v27i9tt"></a>

<p align="center"><kbd><img src="assets/jmujgv4feg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/liat1pgsu19.png" width="80%"></kbd></p>

<br>

<a id="node-dkct11r"></a>

##### 2.1 - Split Your Dataset into
Unmasked and Masked Images

<br>

<a id="node-8wabegh"></a>

<p align="center"><kbd><img src="assets/e5zgoz2o14h.png" width="80%"></kbd></p>

<br>

<a id="node-zb86t0c"></a>

##### 2.2 - Preprocess Your Data

<br>

<a id="node-lgtby0x"></a>

<p align="center"><kbd><img src="assets/zrqhl6dvvch.png" width="80%"></kbd></p>

<br>

<a id="node-5ywfg3l"></a>

##### 3 - U-Net

<br>

<a id="node-2ifeu7s"></a>

<p align="center"><kbd><img src="assets/rhchdupriih.png" width="80%"></kbd></p>

<br>

<a id="node-i6hzic8"></a>

##### 3.1 - Model Details

<br>

<a id="node-yyxjjfz"></a>

<p align="center"><kbd><img src="assets/vwmxza6yx8q.png" width="80%"></kbd></p>

<br>

<a id="node-dy7itgu"></a>

<p align="center"><kbd><img src="assets/toscruu8d6.png" width="80%"></kbd></p>

<br>

<a id="node-0kqdpql"></a>

<p align="center"><kbd><img src="assets/t5wnl5g1wc7.png" width="80%"></kbd></p>

<br>

<a id="node-0185hos"></a>

##### 3.2 - Encoder (Downsampling Block)

<br>

<a id="node-xsoq7t2"></a>

<p align="center"><kbd><img src="assets/0vflzttsys2h.png" width="80%"></kbd></p>

<br>

<a id="node-g33x26x"></a>

##### Exercise 1 - conv_block

<br>

<a id="node-rhfeisy"></a>

<p align="center"><kbd><img src="assets/6i65i4ur7z.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/g5yyoejgijc.png" width="80%"></kbd></p>

<br>

<a id="node-zbc51qw"></a>

<p align="center"><kbd><img src="assets/jytamevkv3.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/oruq6fonxum.png" width="80%"></kbd></p>

<br>

<a id="node-y6q79a7"></a>

<p align="center"><kbd><img src="assets/z8zmnp3smgq.png" width="80%"></kbd></p>

<br>

<a id="node-h31fs5h"></a>

##### 3.3 - Decoder (Upsampling Block)

<br>

<a id="node-3yj96gn"></a>

<p align="center"><kbd><img src="assets/ryxt6xm8q2e.png" width="80%"></kbd></p>

<br>

<a id="node-bw9xx5z"></a>

##### Exercise 2 - upsampling_block

<br>

<a id="node-u40u4rx"></a>

<p align="center"><kbd><img src="assets/ltwblzsq1p.png" width="80%"></kbd></p>

<br>

<a id="node-x9huwmz"></a>

<p align="center"><kbd><img src="assets/42pnwdjjvgu.png" width="80%"></kbd></p>

<br>

<a id="node-9e1oy47"></a>

<p align="center"><kbd><img src="assets/3bw789iha44.png" width="80%"></kbd></p>

<br>

<a id="node-dgy9872"></a>

##### 3.4 - Build the Model

<br>

<a id="node-1e6e1jj"></a>

<p align="center"><kbd><img src="assets/yxn10hmz2l.png" width="80%"></kbd></p>

<br>

<a id="node-hkglsmu"></a>

##### Exercise 3 - unet_model

<br>

<a id="node-xlic1bg"></a>

<p align="center"><kbd><img src="assets/jv2k0qkog.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/r3tofsboyxi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/meabrh14s5.png" width="80%"></kbd></p>

<br>

<a id="node-0q04bii"></a>

<p align="center"><kbd><img src="assets/533nu0a7ye.png" width="80%"></kbd></p>

<br>

<a id="node-rv7xy27"></a>

##### 3.5 - Set Model Dimensions

<br>

<a id="node-9jno0ae"></a>

<p align="center"><kbd><img src="assets/e1pry7a8c85.png" width="80%"></kbd></p>

<br>

<a id="node-1a058t5"></a>

<p align="center"><kbd><img src="assets/wk0meh0lbyn.png" width="80%"></kbd></p>

<br>

<a id="node-e29lvun"></a>

<p align="center"><kbd><img src="assets/btgt9zngbm.png" width="80%"></kbd></p>

<br>

<a id="node-cww1cug"></a>

##### 3.6 - Loss Function: SparseCategoricalCrossentropy

<br>

<a id="node-9go7y5c"></a>

<p align="center"><kbd><img src="assets/fxzkgdh3kln.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là mỗi pixel là 1 vector 11 dimensions (do có 11 classes)
> và gía trị mỗi item trong vector là class probabilities của pixel đó.

<br>

<a id="node-u0iyj0t"></a>

<p align="center"><kbd><img src="assets/81q2rzqm3h.png" width="80%"></kbd></p>

> [!NOTE]
> Output 128x128x11

<br>

<a id="node-zmlqa9v"></a>

##### 3.7 - Dataset Handling: Display input
image và true-mask (đại khái là cái y) hình
có segmentation dùng để train và y^ muốn
đạt được

<br>

<a id="node-oadkz3p"></a>

<p align="center"><kbd><img src="assets/8jce2g9gwy6.png" width="80%"></kbd></p>

<br>

<a id="node-31u880a"></a>

<p align="center"><kbd><img src="assets/0s785myojna.png" width="80%"></kbd></p>

<br>

<a id="node-0xf03mn"></a>

##### 4 - Train the Model

<br>

<a id="node-ndw5wbn"></a>

<p align="center"><kbd><img src="assets/e5y146vqe6r.png" width="80%"></kbd></p>

<br>

<a id="node-eb7wqow"></a>

##### 4.1 - Create Predicted Masks

<br>

<a id="node-3rd7v27"></a>

<p align="center"><kbd><img src="assets/fa93xrz17p6.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bước này nó sẽ xác định cái class
> của từng pixel thuộc về đây, dùng argument max

<br>

<a id="node-u5auhoq"></a>

##### 4.2 - Plot Model Accuracy

<br>

<a id="node-itv84oe"></a>

<p align="center"><kbd><img src="assets/0qz9g509y2hb.png" width="80%"></kbd></p>

<br>

<a id="node-k2jidpq"></a>

##### 4.3 - Show Predictions

<br>

<a id="node-xaoaxio"></a>

<p align="center"><kbd><img src="assets/lf59vwhznio.png" width="80%"></kbd></p>

<br>

<a id="node-gfiyvbp"></a>

<p align="center"><kbd><img src="assets/v6qwyomor3p.png" width="80%"></kbd></p>

<br>

<a id="node-k9zlyz6"></a>

<p align="center"><kbd><img src="assets/0bj3xmp0qcif.png" width="80%"></kbd></p>

<br>

<a id="node-0i4a9mq"></a>

##### Conclusion You've come to the end of this assignment. Awesome work
creating a state-of-the art model for semantic image segmentation! This is a
very important task for self-driving cars to get right. Elon Musk will surely be
knocking down your door at any moment. ;)

What you should remember:

- Semantic image segmentation predicts a label for every single pixel in an
image
- U-Net uses an equal number of convolutional blocks and transposed
convolutions for downsampling and upsampling
- Skip connections are used to prevent border pixel information loss and
overfitting in U-Net

<br>

<a id="node-tvqdril"></a>

## C4w4_face Recognition & Neural Style Transfer

<br>

<a id="node-pxm79p8"></a>

### Face Recognition

<br>

<a id="node-s558meu"></a>

#### What's Face
recognition?

<br>

<a id="node-6rv4k6a"></a>

#### One Shot Learning

<br>

<a id="node-vxtpjus"></a>

##### 1 Face recognition requires solving the one-shot learning problem

2 Deep learning algorithms historically struggle with one-shot learning

3 One approach to address one-shot learning is to input an image, feed it to a
ConvNet, and output a label using a softmax unit with multiple outputs

4 Learning a similarity function, denoted d, is a more effective approach to
one-shot learning for face recognition

5 The function d takes two images and outputs the degree of difference between
them

6 During recognition time, if the degree of difference is less than a threshold, the
two images are predicted to be the same person

7 Learning function d allows for adding new people to the database without
needing to retrain the neural network

8 Training a neural network to learn function d is discussed in the next video.

<br>

<a id="node-6k05t75"></a>

<p align="center"><kbd><img src="assets/xms758x9o6.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là vấn đề One-shot learning, vì
> không có nhiều data để train

<br>

<a id="node-balx2c3"></a>

<p align="center"><kbd><img src="assets/zth4297z55j.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là learn được function d() tính được độ 'difference'
> giữa các images. Cùng 1 người thì ra số nhỏ

<br>

<a id="node-6sn7zb8"></a>

#### Siamese Network

<br>

<a id="node-6tyhzp8"></a>

##### 1 The function d compares two faces and determines their similarity or
difference using a Siamese network.

2 A feature vector of 128 numbers is computed by a fully connected layer to
encode an input image, which represents a good representation of the image.

3 A Siamese neural network architecture runs two identical convolutional
neural networks on two different inputs and then compares them.

4 \\*The Siamese neural network is trained by learning parameters that result
in a function d, which tells when two pictures are of the same person.\\*

5 The objective function to make a neural network learn to determine
similarity or difference between two faces is defined using the triplet loss
function.

<br>

<a id="node-04oysq2"></a>

<p align="center"><kbd><img src="assets/8skfshhe3sv.png" width="80%"></kbd></p>

<br>

<a id="node-ed44twq"></a>

<p align="center"><kbd><img src="assets/e0v93hlow8m.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **learn params của 1 NN sao cho** đưa hai image (x1), x(2)
> vào cho ra đầu ra f(x1), f(x2) sao cho: nếu cùng 1 người thì norm của
> hai vector nhỏ khác nhau thì norm lớn - Đó gọi là Siamese Network

<br>

<a id="node-2zft4ws"></a>

#### Triplet Loss

<br>

<a id="node-xiweo9a"></a>

##### 1 Gradient descent can be used to learn the parameters of a neural network
to give a good encoding for pictures of faces.

2 The triplet loss function is used to compare pairs of images and ensure
that similar images have similar encodings.

3 The triplet loss function involves looking at three images at a time: an
anchor image, a positive image (of the same person as the anchor), and a
negative image (of a different person).

4 The goal of the triplet loss function is to have the encoding of the anchor
image and the positive image be closer together than the encoding of the
anchor image and the negative image, with a margin parameter to prevent
trivial solutions.

5 The triplet loss function is formalized as the max of the difference between
the squared norm of the anchor-positive encoding and the squared norm of
the anchor-negative encoding minus a margin parameter and zero.

<br>

<a id="node-f4dhe6m"></a>

<p align="center"><kbd><img src="assets/q7ei7qf1aib.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ở đây ta định nghĩa một loss function để dùng trong
> công việc train siamese network. Bằng cách tạo ra một mệnh đề
> trong đó bắt buộc so sánh các cặp hình ảnh sao cho: **encoding
> của anchor image phải giống với encoding của positive image
> và khác với encoding của negative image.**
>
>
>
> Trong đó dùng một distance function tính bằng squared norm
> của cặp encoding của anchor - positive / anchor - negative.
>
>
>
> Và một tham số alpha để tránh máy tính nó cho kết quả zero.

<br>

<a id="node-oj4nsgm"></a>

<p align="center"><kbd><img src="assets/rfyf523y2ul.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dựa vào yêu cầu ta define một hàm loss như vầy,
> rồi cost function. Cách define vầy sẽ khiến muốn minimize loss
> thì hiệu số giữa encoding của A và encoding của P phải nhỏ
> hơn nhiều hiệu số giữa encoding của A và encoding của N
>
>
>
> Yêu cầu là training set phải có nhiều picture của 1 người để từ
> đó có các cặp A-P, A-N

<br>

<a id="node-oh6ta5x"></a>

<p align="center"><kbd><img src="assets/6eaci7w2svo.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là phải choose triplets A,P,N sao cho làm
> cho việc training khó bởi vì nếu chọn ngẫu nhiên
> thì rất dễ để có cặp A-P khác xa A-N

<br>

<a id="node-i8kfb15"></a>

<p align="center"><kbd><img src="assets/s21d8svgrq.png" width="80%"></kbd></p>

> [!NOTE]
> Tóm lại đại khái là vầy:
>
>
>
> Chuẩn bị bộ data theo kiểu cặp 3 cái A-P-N Trong đó có
> A-P là của cùng 1 người,
>
>
>
> DÙng hàm Triplet Loss để Gradient Descent để train ra
> params sao cho decoding của hai người khác nhau sẽ
> lớn hơn nhiều decoding của 2 ảnh của cùng 1 người

<br>

<a id="node-p6mj8ry"></a>

<p align="center"><kbd><img src="assets/oddma9rbhik.png" width="80%"></kbd></p>

> [!NOTE]
> Tóm lại đại khái là vầy:
>
>
>
> Đại khái là một số company có những bộ data rất lớn và khó mà
> tiếp cận được, nhưng một số publish model đã train đó mình có
> thể xài lại được (transfer learning)

<br>

<a id="node-x2c54jy"></a>

#### Clarification About
upcoming Face Verification...

<br>

<a id="node-8hitafg"></a>

#### Face Verification And
binary Classification

<br>

<a id="node-7n9f8j3"></a>

##### 1 Introduction to Face Recognition: There are different ways to learn parameters for face
recognition systems, including the Triplet Loss and a straight binary classification approach.

2 Straight Binary Classification for Face Recognition: Face recognition can be posed as a
binary classification problem by using a Siamese Network to compute embeddings and
inputting them into a logistic regression unit to predict whether the two images are of the
same person or not.

3 Computing the Logistic Regression Unit: The logistic regression unit \\*takes the differences
between the encodings as features\\* and \\*trains appropriate weights on these features to
predict whether the two images are of the same person or not.\\*

4 Variations on Computing the Formula: There are different variations on computing the
formula for the logistic regression unit, including the \\*chi-square similarity formula\\*.

5 Training the Siamese Network: The Siamese Network is trained using pairs of similar and
dissimilar images to learn to predict whether the two images are of the same person or not.

6 Pre-Computing Encodings: Pre-computing encodings can save significant computation time
and works for both the binary classification approach and the Triplet Loss approach.

7 Creating a Training Set: To train a face verification or recognition system, a training set of
pairs of images with target labels of one for same persons and zero for different persons is
created.

8 Conclusion: With the knowledge of these techniques, one can train a face verification or
recognition system that can perform one-shot learning.

<br>

<a id="node-h9hhwbw"></a>

<p align="center"><kbd><img src="assets/67qoeevex5.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là vầy: Thay vì dùng phương pháp Triplet loss, ta có
> thể dùng cách 'Binary Classification'.
>
>
>
> Đại loại ra ta lấy output của Siamese network bỏ vào logistic
> regression. L. G sẽ **đại khái là train input data mà feature là
> sự giống và khác nhau của encoding của 2 bức ảnh kết quả
> bởi Siamese network để rồi train được params sao cho cùng
> người thì ra y^ = 1, khác người thì y^ = 0.**
>
>
>
> Có một vài 'biến thể' trong cách define logistic regression như
> dùng  **Absolute** value hay **Squared** value. 
>
>
>
> Ký hiệu của term f(x(i)) - f(x(j)) gọi là χ - CHI

<br>

<a id="node-y6ezt8x"></a>

<p align="center"><kbd><img src="assets/ltx6nnlq8sp.png" width="80%"></kbd></p>

> [!NOTE]
> Các bộ training data sample là các cặp hình, cùng 1 người
> thì y = 1, khác người thì y = 0.

<br>

<a id="node-7p8wq6f"></a>

### Neural Style Transfer

<br>

<a id="node-uhdxlyd"></a>

#### What's Neural Style Transfer?

<br>

<a id="node-v3yvzjh"></a>

##### Đại khái là một ứng dụng hay ho của ConvNet là cái
này, apply style của 1 image cho 1 image khác.

Cần xem thử các feature learned bởi ConvNet tại các
layers khác nhau trông như thế nào

<br>

<a id="node-npi6pf2"></a>

<p align="center"><kbd><img src="assets/jlp1m2lusvr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là một ứng dụng hay ho của ConvNet là cái này, apply
> style của 1 image cho 1 image khác.
>
>
>
> Cần xem thử các feature learned bởi ConvNet tại các layers khác
> nhau trông như thế nào

<br>

<a id="node-8xdyp1m"></a>

#### What Are Deep Convnets Learning

<br>

<a id="node-0tkd07d"></a>

##### 1 The video aims to explain what the deeper layers of a ConvNet are
really doing and provide visualizations that will help viewers understand
the neural network's functioning better.

2 To visualize what hidden units in different layers are computing, one
can find out the\\* images that maximize that unit's activation\\* by scanning
through the training sets.

3 Hidden units in layer 1 usually detect relatively \\*simple features such as
edges or shades of color.\\*

4 Hidden units in d\\*eeper layers\\* of the neural network see a \\*larger region
of the image\\* and \\*detect more complex shapes and patterns\\*.

5 The features that second and third layers detect are \\*getting more
complicated\\*.

6 The video cites a paper titled "\\*Visualizing and Understanding
Convolutional Networks" by Matthew Zeiler and Rob Fergus\\* that offers
more sophisticated ways of visualizing when the ConvNet is running.

<br>

<a id="node-cg8bbup"></a>

<p align="center"><kbd><img src="assets/lz9v427kcm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là trong layer 1
>
>
>
> Với mỗi hidden layer, tìm 9 cái hình mà có unit activation lớn nhất.
>
> Lần lượt vậy với các hidden layer khác.
>
>
>
> In ra để xem nó như thế nào thì thấy càng sâu thì nó học thêm các feature /
> pattern càng  phức tạp s

<br>

<a id="node-4eupb79"></a>

<p align="center"><kbd><img src="assets/pbmm38gf8co.png" width="80%"></kbd></p>

<br>

<a id="node-cdzjypg"></a>

<p align="center"><kbd><img src="assets/y15ls6tcoaf.png" width="80%"></kbd></p>

<br>

<a id="node-sf36284"></a>

<p align="center"><kbd><img src="assets/abs3jwe5q.png" width="80%"></kbd></p>

<br>

<a id="node-ot6q5kj"></a>

<p align="center"><kbd><img src="assets/ptjqjpy8xnf.png" width="80%"></kbd></p>

<br>

<a id="node-vvz7tvk"></a>

<p align="center"><kbd><img src="assets/dvql41jzhgw.png" width="80%"></kbd></p>

<br>

<a id="node-5lpd2lq"></a>

#### Cost Function

<br>

<a id="node-a41rmc4"></a>

##### Đại khái ý tưởng là define một hàm cost function sao cho bao gồm
cost function:

đ/v Content -> Làm sao cho kết quả giống với hình gốc và

đ/v Style -> Làm sao cho kết quả giống với hình style

Và nếu minimize hàm cost function này thì kết quả sẽ vừa giống
hình gốc và vừa giống hình style

<br>

<a id="node-g627h2d"></a>

<p align="center"><kbd><img src="assets/3pv0o6fihov.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái ý tưởng là define một hàm cost function sao cho bao gồm cost
> function:
>
>
>
> đ/v Content -> Làm sao cho kết quả giống với hình gốc
>
>
>
> đ/v Style -> Làm sao cho kết quả giống với hình style
>
>
>
> Và nếu minimize hàm cost function này thì kết quả sẽ vừa giống hình
> gốc và vừa giống hình style

<br>

<a id="node-v2b15ps"></a>

<p align="center"><kbd><img src="assets/525yeoktwqi.png" width="80%"></kbd></p>

<br>

<a id="node-m1unbgi"></a>

#### Content Cost Function

<br>

<a id="node-8q681d7"></a>

##### 1 The neural style transfer algorithm has a cost function with a content
cost component and a style cost component.

2 The content cost function measures the similarity of the hidden layer
activations between a content image and a generated image.

3 A layer is chosen somewhere in between shallow and deep layers to
compute the content cost.

4 A pre-trained ConvNet, such as a VGG network, can be used to
measure the similarity between the activations of the content image and
the generated image.

5 The content cost function is defined as the element-wise sum of
squares of differences between the activations in layer l, between the
images in C and G.

6 The content cost function incentivizes the algorithm to find an image G
that has hidden layer activations similar to those of the content image.

7 The style cost function will be discussed next.

<br>

<a id="node-hxxnsvc"></a>

<p align="center"><kbd><img src="assets/fpz6dt3rsoe.png" width="80%"></kbd></p>

> [!NOTE]
> /Use hidden layer l to compute content cost: / Đại khái là nếu L nhỏ, kiểu
> như bắt buộc cái hình mới phải giống y chang cái hình gốc, còn nếu L lớn
> thì chỉ cần giống giống một cách chung chung thôi.
>
>
>
> Vì L nhỏ thì nó ở cấp shallow feature, nên giống ở cấp này tức là phải
> giống ở những nét những feature sơ cấp -> Nên phải giống y mới được
> còn L lớn thì nó ở deep feature nên giống ở cấp này tức là giống ở mức
> pattern - Không cần y chang.
>
> *a[l](C) & a[l](G):
> Unrolled into vectors
>
> Use pre-trained ConvNet: Đại khái là
> nên dùng pre-trained ConvNet để dùng
> cho step này

<br>

<a id="node-8hcdyyy"></a>

#### Clarification ....

<br>

<a id="node-p5jzeyw"></a>

<p align="center"><kbd><img src="assets/vrc59wmhxqq.png" width="80%"></kbd></p>

<br>

<a id="node-o2yn95d"></a>

#### Style Cost Function

<br>

<a id="node-syfehkw"></a>

<p align="center"><kbd><img src="assets/qu1ermpu3zl.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên phải định nghĩa 'style' là sự
> correlation giữa các channels

<br>

<a id="node-7on3un4"></a>

<p align="center"><kbd><img src="assets/h7zce7m8nwq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dùng độ correlated giữa các layer để đánh giá xem
> style của generated image có giống style của style input image
> không
>
>
>
> Và độ correlated giữa các channel đại khái là ví dụ như là "nếu
> sọc dọc xuất hiện thì nó sẽ có xu hướng màu cam",..đại khái
> kiểu kiểu vậy sẽ "làm nên" / "tạo nên" style của image.

<br>

<a id="node-macybe8"></a>

<p align="center"><kbd><img src="assets/7gmoc5ftbi7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/dys8qpqejpl.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/9h0wk8sqrpo.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là define matrix 'Style' thể hiện style của 1 layer l còn gọi
> là Gram matrix.
>
>
>
> Và Từ đó define nên cost function đại khái à chêch lệch giữa style
> tại layer l của 2 bức hình - gốc và hình generated
>
>
>
> Có thể (/2nhnwnc) - normalization gì đó nhưng không quan trọng
> ổng nói vậy chưa hiểu lắm .

<br>

<a id="node-a2tihz6"></a>

<p align="center"><kbd><img src="assets/p3lax2gxnsh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái mở rộng ra define cost function thể hiện chênh lệch giữa
> style của các layer l = 1 - L của hai bức hình style gốc và
> generated image;
>
>
>
> /**Thì nếu train dc bức hình generate sao cho minimize hàm J
> này thì bức hình đó sẽ có style gần giống với bức hình gốc nhất.
>
>
>
> /Và kết hợp với Jcontent nữa thì minimize J sẽ ra bức hình có
> content giống content của bức hình content còn style thì giống
> style của bức Styled image.**

<br>

<a id="node-43agwky"></a>

#### 1d & 3d Generalizations

<br>

<a id="node-1sfpqgy"></a>

<p align="center"><kbd><img src="assets/ie1mb6bx13e.png" width="80%"></kbd></p>

> [!NOTE]
> Chắc không có gì khó hiểu chỉ có ghi chú cho nhớ lại:
>
>
>
> Filter dimension không ghi thì cũng phải hiểu là có cùng số
> dimension với input 14x14x3 thì filter cũng 5x5x3 (3 dimension)
>
>
>
> và có 16 cái filter thì out sẽ là 10x10x16

<br>

<a id="node-wn19gaz"></a>

<p align="center"><kbd><img src="assets/uo65w96ooyd.png" width="80%"></kbd></p>

<br>

<a id="node-4ckhcap"></a>

<p align="center"><kbd><img src="assets/xn3v6u9wxyh.png" width="80%"></kbd></p>

<br>

<a id="node-kk3m4ix"></a>

#### Quiz

<br>

<a id="node-socbw8t"></a>

<p align="center"><kbd><img src="assets/a9uhu588og.png" width="80%"></kbd></p>

<br>

<a id="node-q5ux760"></a>

<p align="center"><kbd><img src="assets/ufeyti8ku1j.png" width="80%"></kbd></p>

> [!NOTE]
> Correct. One-shot learning
> **refers to the amount of data we
> have** to solve a task.

<br>

<a id="node-fxmr4t9"></a>

<p align="center"><kbd><img src="assets/qvg1ehzhn1a.png" width="80%"></kbd></p>

> [!NOTE]
> Correct. Although it is **necessary to have several
> pictures of the same person**, it is **not absolutely
> necessary that all the pictures only come from
> current members of the team**.

<br>

<a id="node-015fzx9"></a>

<p align="center"><kbd><img src="assets/ufmzfz60fy.png" width="80%"></kbd></p>

<br>

<a id="node-czph4d2"></a>

<p align="center"><kbd><img src="assets/gtvfg4b6l46.png" width="80%"></kbd></p>

<br>

<a id="node-27264p9"></a>

<p align="center"><kbd><img src="assets/n6q7u5ssaa9.png" width="80%"></kbd></p>

<br>

<a id="node-9xsfiyh"></a>

<p align="center"><kbd><img src="assets/6d53kptnrh3.png" width="80%"></kbd></p>

<br>

<a id="node-sr0jmw4"></a>

<p align="center"><kbd><img src="assets/r1bjvvoj8ae.png" width="80%"></kbd></p>

<br>

<a id="node-7zfor8w"></a>

<p align="center"><kbd><img src="assets/hc5qx58vuoq.png" width="80%"></kbd></p>

<br>

<a id="node-sovjg4n"></a>

<p align="center"><kbd><img src="assets/ygdoe30xbft.png" width="80%"></kbd></p>

<br>

<a id="node-c5gqkzt"></a>

#### Programming Assignment: Face Recognition

<br>

<a id="node-hf8hjud"></a>

##### Welcome to the first (required) programming exercise of the final week
of Course 4 in the Deep Learning Specialization. In this notebook you
will build a face recognition system...one much better than the one
shown in the cartoon below! :)

By the end of this assignment, you'll be able to:
 • Differentiate between face recognition and face verification
 • Implement one-shot learning to solve a face recognition problem
 • Apply the triplet loss function to learn a network's parameters in the context of face recognition
 • Explain how to pose face recognition as a binary classification problem
 • Map face images into 128-dimensional encodings using a pretrained model
 • Perform face verification and face recognition with these encodings

<p align="center"><kbd><img src="assets/bg838uscyz.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ..

<br>

<a id="node-jb9gmk4"></a>

- **Face Recognition**

<br>

<a id="node-jaag6gw"></a>

<p align="center"><kbd><img src="assets/8m6iux14smi.png" width="80%"></kbd></p>

<br>

<a id="node-atxo2jr"></a>

- **1 - Packages**

<br>

<a id="node-3cic74n"></a>

<p align="center"><kbd><img src="assets/8se527o67mu.png" width="80%"></kbd></p>

<br>

<a id="node-c2b87is"></a>

- **2 - Naive Face Verification:

Đại khái là có thể so sánh độ giống của 2 bức hình (để
xác định cùng 1 người theo kiểu pixel to pixel, nhưng rõ
ràng sẽ rất kém vì so sánh kiểu đó không ổn, pixel nó thay
đổi rất nhiều do độ sáng, góc chụp...) nên thay vì vậy phải
tạo ra một hàm để encode và so sánh 2 cái encoding này**

<br>

<a id="node-y6q1tpy"></a>

<p align="center"><kbd><img src="assets/d20ig7gich.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là có thể so sánh độ giống của 2 bức hình (để
> xác định cùng 1 người theo kiểu pixel to pixel, nhưng rõ
> ràng sẽ rất kém vì so sánh kiểu đó không ổn, pixel nó thay đổi rất
> nhiều do độ sáng, góc chụp...) nên thay vì vậy
> phải tạo ra một hàm để encode và so sánh 2 cái encoding này

<br>

<a id="node-st0cwgm"></a>

- **3 - Encoding Face Images into a
128-Dimensional Vector**

<br>

<a id="node-zvqk0b1"></a>

- **3.1 - Using a ConvNet to Compute Encodings

Đại khái là cái cần làm là Train một cái NN để encode input 
images sao cho:
- Cùng một người thì distance (giữa 2 encoding) thấp
- Hai người khác nhau thì distance cao.

Mà để train cái NN này thì cần nhiều data và tốn nhiều thời gian
cho nên theo lẽ thường của Deep Learning là ta sẽ tìm một cái
model đã pretrain để xài (train lại hoặc dùng như khởi đầu)

Và ổng đã tìm sẵn cho mình xài: \\*keras-facenet-h5/model. json\\*
và cái Network Implementation dùng để train ra cái model ở trên
là làm theo Inception model của ông Szegedy et al, xem trong
file\\* inception_blocks_v2.py

\\*Đại khái là xem thử model (pretrained) output, input sao
mình sẽ dùng nó để 'tính' / encode ra encoding, để rồi từ đó
tính ra distance của 2 encoding.

Nếu distance của encoding của 2 image cùng 1 người mà nhỏ
và 2 người khác nhau mà lớn thì model đó good

Đại khái là triplet loss sẽ giúp train model (phải train tiếp
dựa trên pretrain model) sao cho thoả mãn tính chất trên**

<br>

<a id="node-tfft9zn"></a>

<p align="center"><kbd><img src="assets/lymnffktvam.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cái cần làm là Train một cái NN để encode input 
> images sao cho:
> - Cùng một người thì distance (giữa 2 encoding) thấp
> - Hai người khác nhau thì distance cao.
>
>
>
> Mà để train cái NN này thì cần nhiều data và tốn nhiều thời gian
> cho nên theo lẽ thường của Deep Learning là ta sẽ tìm một cái
> model đã pretrain để xài (train lại hoặc dùng như khởi đầu)
>
>
>
> Và ổng đã tìm sẵn cho mình xài: **keras-facenet-h5/model. json**
> và cái Network Implementation dùng để train ra cái model ở trên
> là làm theo Inception model của ông Szegedy et al, xem trong
> file **inception_blocks_v2.py**

<br>

<a id="node-0e42x1o"></a>

<p align="center"><kbd><img src="assets/z7p3d2un02q.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là xem thử model (pretrained) output, input sao
> mình sẽ dùng nó để 'tính' / encode ra encoding, để rồi từ đó
> tính ra distance của 2 encoding.
>
>
>
> Nếu distance của encoding của 2 image cùng 1 người mà nhỏ
> và 2 người khác nhau mà lớn thì model đó good

<br>

<a id="node-w592iyq"></a>

<p align="center"><kbd><img src="assets/42es1sb3t6c.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là triplet loss sẽ giúp train model  sao cho thoả mãn tính chất trên

<br>

<a id="node-g3t39uv"></a>

- **3.2 - The Triplet Loss

Đại khái là làm chơi cho biết chứ do dùng
Pretrained model nên thực tế không cần làm**

<br>

<a id="node-ptcczj6"></a>

<p align="center"><kbd><img src="assets/vapvx8r1pld.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/tzoq09u0i2q.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là làm chơi cho biết chứ do dùng
> Pretrained model nên thực tế không cần làm

<br>

<a id="node-2g13xo7"></a>

- **Exercise 1 - triplet_loss**

<br>

<a id="node-hqav1gg"></a>

<p align="center"><kbd><img src="assets/fbrdmmt1zcj.png" width="80%"></kbd></p>

<br>

<a id="node-4dzj57l"></a>

<p align="center"><kbd><img src="assets/4dizcro79zk.png" width="80%"></kbd></p>

<br>

<a id="node-shvqxpw"></a>

<p align="center"><kbd><img src="assets/77zqv8ldbqo.png" width="80%"></kbd></p>

<br>

<a id="node-kw9a5vk"></a>

<p align="center"><kbd><img src="assets/m8eoctq06t.png" width="80%"></kbd></p>

<br>

<a id="node-wzxon4a"></a>

- **4 - Loading the Pre-trained Model

Đại khái là load cái model (pretrained)
ra xài thôi**

<br>

<a id="node-nj01vgd"></a>

<p align="center"><kbd><img src="assets/tdmdkddv53k.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là load cái model (pretrained) ra xài thôi

<br>

<a id="node-pulm3v7"></a>

- **5 - Applying the Model**

<br>

<a id="node-4it1930"></a>

<p align="center"><kbd><img src="assets/jq3b9z7rtvb.png" width="80%"></kbd></p>

<br>

<a id="node-1siifax"></a>

- **5.1 - Face Verification**

<br>

<a id="node-jzfuq9x"></a>

<p align="center"><kbd><img src="assets/qmeecfhgic.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dùng cái retrained model để tạo các 'encoding'
> của các nhân viên từ ảnh của họ. 
> Tên - encoding

<br>

<a id="node-vk0thrx"></a>

<p align="center"><kbd><img src="assets/a90ko1nka.png" width="80%"></kbd></p>

<br>

<a id="node-syn1ah5"></a>

- **Exercise 2 - verify

Đại khái là

Lấy cái hình (chụp từ camera) (từ image path) bỏ vào tính
Encoding.

Có cái tên (identity) -> Lấy cái encoding từ database ra

Tính distance giữa 2 cái encoding này bằng function distance of a
& b = \\*np.linalg.norm(a-b)\\*

So với threshold để decide**

<br>

<a id="node-mspl4ex"></a>

<p align="center"><kbd><img src="assets/bb15ohblpsl.png" width="80%"></kbd></p>

<br>

<a id="node-vkmbz18"></a>

<p align="center"><kbd><img src="assets/xpa9efp9i.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là
>
>
>
> Lấy cái hình (chụp từ camera) (từ image path) bỏ vào tính
> Encoding.
>
>
>
> Có cái tên (identity) -> Lấy cái encoding từ database ra
>
>
>
> Tính distance giữa 2 cái encoding này bằng function distance of a
> & b = **np.linalg.norm(a-b)**
>
>
>
> So với threshold để decide

<br>

<a id="node-myt29dz"></a>

<p align="center"><kbd><img src="assets/3jnh0o7u1jd.png" width="80%"></kbd></p>

<br>

<a id="node-z4suknm"></a>

<p align="center"><kbd><img src="assets/a22cyz20zla.png" width="80%"></kbd></p>

<br>

<a id="node-v7jqflx"></a>

- **5.2 - Face Recognition

Đại khái là thay vì dùng cái identity (tên) để lấy ra encoding
Trong database rồi so nó với encoding của bức hình chụp từ
camera thì giờ ta sẽ cứ check hết distance của cam image's encoding
với các encoding trong database. Cái nào nhỏ hơn threshold thì
Suy ra là người đó, không có thì suy ra là người lạ.**

<br>

<a id="node-8y289qg"></a>

<p align="center"><kbd><img src="assets/uk4vf355qg.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thay vì dùng cái identity (tên) để lấy ra encoding
> Trong database rồi so nó với encoding của bức hình chụp từ
> camera thì giờ ta sẽ cứ check hết distance của cam image's encoding
> với các encoding trong database. Cái nào nhỏ hơn threshold thì
> Suy ra là người đó, không có thì suy ra là người lạ.

<br>

<a id="node-tu64kki"></a>

- **Exercise 3 - who_is_it**

<br>

<a id="node-3hj8efk"></a>

<p align="center"><kbd><img src="assets/2gjkbkz1bct.png" width="80%"></kbd></p>

<br>

<a id="node-dw79te4"></a>

<p align="center"><kbd><img src="assets/i3okv2jud5i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/5te8menvtx2.png" width="80%"></kbd></p>

<br>

<a id="node-rzjjlzh"></a>

<p align="center"><kbd><img src="assets/350z8dryjhl.png" width="80%"></kbd></p>

<br>

<a id="node-jvfwam6"></a>

- **\\*Congratulations\\*! You've completed this assignment, and your face recognition system is
working well! It not only lets in authorized persons, but now people don't need to carry an ID
card around anymore!

You've now seen how a state-of-the-art face recognition system works, and can describe the
difference between face recognition and face verification. Here's a quick recap of what you'
ve accomplished:

• Posed face recognition as a binary classification problem

• Implemented one-shot learning for a face recognition problem

• Applied the triplet loss function to learn a network's parameters in the context of face
recognition

• Mapped face images into 128-dimensional encodings using a pretrained model

• Performed face verification and face recognition with these encodings Great work!

\\*What you should remember\\*:

• Face verification solves an easier 1:1 matching problem; face recognition addresses a
harder 1:K matching problem.

• Triplet loss is an effective loss function for training a neural network to learn an encoding of
a face image.

• The same encoding can be used for verification and recognition. Measuring distances
between two images' encodings allows you to determine whether they are pictures of the
same person.**

<br>

<a id="node-4gzveuc"></a>

- **Ways to improve your facial recognition model:

Although you won't implement these here, here are some ways to
further improve the algorithm:

Put more images of each person (under different lighting conditions,
taken on different days, etc.) into the database. Then, given a new
image, compare the new face to multiple pictures of the person. This
would increase accuracy.

Crop the images to contain just the face, and less of the "border"
region around the face. This preprocessing removes some of the
irrelevant pixels around the face, and also makes the algorithm more
robust.**

<br>

<a id="node-0l9hycs"></a>

- **6 - References \\* \\*

1 Florian Schroff, Dmitry Kalenichenko, James Philbin (2015). \\_FaceNet: A Unified Embedding
for Face Recognition and Clustering

\\_  2 Yaniv Taigman, Ming Yang, Marc'Aurelio Ranzato, Lior Wolf (2014). \\_DeepFace: Closing the
gap to human-level performance in face verification\\_

3 This implementation also took a lot of inspiration from the official FaceNet github
repository: \\_https://github.com/davidsandberg/facenet\\_

4 Further inspiration was found here: \\_https://machinelearningmastery.
com/how-to-develop-a-face-recognition-system-using-facenet-in-keras-and-an-svm-classifier/\\_

5 And here: \\_https://github.com/nyoki-mtl/keras-facenet/blob/master/notebook/tf_to_keras.
ipynb\\_**

<br>

<a id="node-gpb1has"></a>

#### Programming Assignment: Art Generation with Neural Style Transfer

<br>

<a id="node-3g7wwh8"></a>

##### Welcome to the final (required) programming exercise, of the final  week of Course 4 in the
Deep Learning Specialization! In this notebook,  you'll use transfer learning to generate new
artistic images.

\\*Upon completion of this assignment, you will be able to:\\*

• Implement the neural style transfer algorithm

• Generate novel artistic images using your algorithm

• Define the style cost function for Neural Style Transfer

• Define the content cost function for Neural Style Transfer Most of the algorithms you've
studied optimize a cost function to get a set of parameter values. With Neural Style Transfer,
you'll get to optimize a cost function to get pixel values. Exciting!

<p align="center"><kbd><img src="assets/r30ucg5ovgd.png" width="80%"></kbd></p>

<br>

<a id="node-7pre3og"></a>

- **1 - Packages**

<br>

<a id="node-fssotd7"></a>

<p align="center"><kbd><img src="assets/oghlknh5np.png" width="80%"></kbd></p>

<br>

<a id="node-n9mpk7e"></a>

- **2 - Problem Statement**

<br>

<a id="node-62op9om"></a>

<p align="center"><kbd><img src="assets/qjbj7dja7ys.png" width="80%"></kbd></p>

<br>

<a id="node-3t4jly9"></a>

- **3 - Transfer Learning**

<br>

<a id="node-tufzs63"></a>

<p align="center"><kbd><img src="assets/uypov8o4oxk.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dùng một cái NN đã train với một kho data image khủng

<br>

<a id="node-khzdh6e"></a>

- **4 - Neural Style Transfer (NST)

- First, you will build the content cost function  𝐽𝑐𝑜𝑛𝑡𝑒𝑛𝑡(𝐶,𝐺)
- Second, you will build the style cost function  𝐽𝑠𝑡𝑦𝑙𝑒(𝑆,𝐺)
- Finally, you'll put it all together to get 𝐽(𝐺) = 𝛼𝐽𝑐𝑜𝑛𝑡𝑒𝑛𝑡(𝐶,𝐺) + 𝛽𝐽𝑠𝑡𝑦𝑙𝑒(𝑆,𝐺)**

<br>

<a id="node-21jdqw0"></a>

- **4.1 - Computing the
Content Cost**

<br>

<a id="node-q3g7rno"></a>

- **4.1.1 - Make Generated Image G Match the Content of Image C

Đại khái là bước 1 là:

Làm sao để Generated image giống với Content.

Chọn l giữa giữa để 'nó' capture cả low level và high level 
features.

Ta dùng content image và generated image bỏ vào cái VGG network
để forward prop để lấy ra a(C) và a(G) - Ouput của
hidden layer thứ L**

<br>

<a id="node-g21k3h8"></a>

<p align="center"><kbd><img src="assets/d9uxr6t8kve.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bước 1 là:
>
>
>
> Làm sao để Generated image giống với Content.
>
>
>
> Chọn l giữa giữa để 'nó' capture cả low level và high level 
> features.
>
>
>
> Ta dùng content image và generated image bỏ vào cái VGG network
> để forward prop để lấy ra a(C) và a(G) - Ouput của
> hidden layer thứ L

<br>

<a id="node-invivdq"></a>

<p align="center"><kbd><img src="assets/4yl3w3fw8vc.png" width="80%"></kbd></p>

<br>

<a id="node-btq6yic"></a>

- **4.1.2 - Content Cost Function 𝐽𝑐𝑜𝑛𝑡𝑒𝑛𝑡(𝐶,𝐺)**

<br>

<a id="node-3uyvx43"></a>

<p align="center"><kbd><img src="assets/vaispcw0vus.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là sau khi forward prop
> để có a(C) và a(G) ta bỏ vào define một 
> Cost function J_content sao cho minimize 'khoảng cách'
> giữa hai volume: ||(a(C) - a(G))|| ^2 
>
>
>
> Trong bài có nói có thể có hoặc không việc 'normalization'

<br>

<a id="node-2plhfdk"></a>

- **Exercise 1 - compute_content_cost

a_C = content_output[-1]
a_G = generated_output[-1]
    
_, n_H, n_W, n_C = a_G.get_shape().as_list()
    
a_C_unrolled = tf.reshape(a_C, shape=[_, n_H*n_W, n_C])
a_G_unrolled = tf.reshape(a_G, shape=[_, -1, n_C])
    
J_content = tf.reduce_sum(
        tf.square(
            tf.subtract(a_C_unrolled, a_G_unrolled)
        )
    , axis=None) 
J_content = J_content / (4*n_H*n_W*n_C)

\\*What you should remember:\\*

• The content cost takes a hidden layer activation of
the neural network, and measures how different  a(𝐶)
and 𝑎𝐺) are.

• When you minimize the content cost later, this will
help make sure 𝐺 has similar content as 𝐶.**

<br>

<a id="node-2pqu6w0"></a>

<p align="center"><kbd><img src="assets/05t25qqwd29b.png" width="80%"></kbd></p>

<br>

<a id="node-aecdy2w"></a>

<p align="center"><kbd><img src="assets/3eghvfsy5nw.png" width="80%"></kbd></p>

<br>

<a id="node-tcua8mj"></a>

<p align="center"><kbd><img src="assets/rztk0qswl2g.png" width="80%"></kbd></p>

<br>

<a id="node-cuq2tbs"></a>

- **4.2 - Computing
the Style Cost**

<br>

<a id="node-wyh0scj"></a>

- **4.2 - Computing the Style Cost**

<br>

<a id="node-vb7ujgz"></a>

<p align="center"><kbd><img src="assets/fmwol3f8156.png" width="80%"></kbd></p>

<br>

<a id="node-ig39bt7"></a>

- **4.2.1 - Style Matrix**

<br>

<a id="node-ecikkgm"></a>

<p align="center"><kbd><img src="assets/vzxsg07ndcs.png" width="80%"></kbd></p>

<br>

<a id="node-x967d20"></a>

<p align="center"><kbd><img src="assets/ofm67wvy49.png" width="80%"></kbd></p>

<br>

<a id="node-u5jz8i8"></a>

<p align="center"><kbd><img src="assets/ekbgjvu9bg7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/goqbqx49bf9.png" width="80%"></kbd></p>

<br>

<a id="node-ylikssr"></a>

- **Exercise 2 - gram_matrix**

<br>

<a id="node-dhp2jjp"></a>

<p align="center"><kbd><img src="assets/tw4y99imvg.png" width="80%"></kbd></p>

<br>

<a id="node-g10a2l5"></a>

- **4.2.2 - Style Cost**

<br>

<a id="node-8uqi6kd"></a>

<p align="center"><kbd><img src="assets/eg2r0usl455.png" width="80%"></kbd></p>

<br>

<a id="node-3bxfdkv"></a>

- **Exercise 3 - compute_layer_style_cost**

<br>

<a id="node-7p1077a"></a>

<p align="center"><kbd><img src="assets/n2hyy2f1nn.png" width="80%"></kbd></p>

<br>

<a id="node-qqdh0ph"></a>

<p align="center"><kbd><img src="assets/bmcf5ytkdid.png" width="80%"></kbd></p>

<br>

<a id="node-plkpgnv"></a>

- **4.2.3 Style Weights

Đại khái là tính J_style với nhiều layer thay vì chỉ một layer nào
đó ở giữa giữa network architecture sẽ cho kết quả tốt hơn.

Hiểu đại khái là nếu mình "tính" J_style ảnh hưởng bởi nhiều
layer thậm chí tất cả layer thì Generated image sẽ càng giống
style với Styled image.

Cho mỗi layer một tham số để control ảnh hưởng nhiều hay ít.**

<br>

<a id="node-gfrnlo3"></a>

<p align="center"><kbd><img src="assets/4r838vs4b1.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tính J_style với nhiều layer thay vì chỉ một layer nào
> đó ở giữa giữa network architecture sẽ cho kết quả tốt hơn.
>
>
>
> Hiểu đại khái là nếu mình "tính" J_style ảnh hưởng bởi nhiều
> layer thậm chí tất cả layer thì Generated image sẽ càng giống
> style với Styled image.
>
>
>
> Cho mỗi layer một tham số để control ảnh hưởng nhiều hay ít.

<br>

<a id="node-w5xwh5j"></a>

<p align="center"><kbd><img src="assets/szvteqaep6g.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây đại khái là chọn mấy layer này (block1_conv1, block2_conv1..)
> mỗi cái đóng góp 20%.

<br>

<a id="node-hii6t7v"></a>

- **Exercise 4 - compute_style_cost**

<br>

<a id="node-0hdi2bp"></a>

<p align="center"><kbd><img src="assets/i7ptw1gwu9h.png" width="80%"></kbd></p>

<br>

<a id="node-loal7bz"></a>

<p align="center"><kbd><img src="assets/kisddpm56d.png" width="80%"></kbd></p>

> [!NOTE]
> Đã hiểu vì sao bỏ thằng cuối, xem minh hoạ

<br>

<a id="node-2y2dtq8"></a>

- **How do you choose the coefficients for each layer? The deeper
layers capture higher-level concepts, and the features in the deeper
layers are less localized in the image relative to each other. So if
you want the generated image to softly follow the style image, try
choosing larger weights for deeper layers and smaller weights for
the first layers. In contrast, if you want the generated image to
strongly follow the style image, try choosing smaller weights for
deeper layers and larger weights for the first layers.

What you should remember:

The style of an image can be represented using the Gram matrix of
a hidden layer's activations.

You get even better results by combining this representation from
multiple different layers.

This is in contrast to the content representation, where usually using
just a single hidden layer is sufficient.

Minimizing the style cost will cause the image  𝐺   to follow the style
of the image  𝑆**

<br>

<a id="node-d0m55ld"></a>

- **4.3 - Defining the Total Cost to Optimize**

<br>

<a id="node-z082udx"></a>

- **Exercise 5 - total_cost

\\*What you should remember:\\*

• The total cost is a linear combination of the content cost
𝐽𝑐𝑜𝑛𝑡𝑒𝑛𝑡(𝐶,𝐺)  and the style cost 𝐽𝑠𝑡𝑦𝑙𝑒(𝑆,𝐺).

• 𝛼 and 𝛽 are hyperparameters that control the relative
weighting between content and style.**

<br>

<a id="node-ylutuz6"></a>

<p align="center"><kbd><img src="assets/rw3c2w8pj2i.png" width="80%"></kbd></p>

<br>

<a id="node-6hmsgl3"></a>

- **5 - Solving the Optimization Problem**

<br>

<a id="node-2d2trgi"></a>

- **5 - Solving the
Optimization Problem**

<br>

<a id="node-4mp1cur"></a>

<p align="center"><kbd><img src="assets/6nkzsjnysk3.png" width="80%"></kbd></p>

<br>

<a id="node-2cdbcva"></a>

- **5.1 Load the Content Image**

<br>

<a id="node-gsro4ag"></a>

<p align="center"><kbd><img src="assets/icx16fpisir.png" width="80%"></kbd></p>

<br>

<a id="node-1vcas85"></a>

- **5.2 Load the Style Image**

<br>

<a id="node-5gn5u2q"></a>

<p align="center"><kbd><img src="assets/xckwb895lpj.png" width="80%"></kbd></p>

<br>

<a id="node-u8ssmeq"></a>

- **5.3 Randomly Initialize the Image to be Generated**

<br>

<a id="node-o2ek6tf"></a>

<p align="center"><kbd><img src="assets/xqr85ef7z6.png" width="80%"></kbd></p>

<br>

<a id="node-9f5kz94"></a>

- **5.4 - Load Pre-trained VGG19 Model**

<br>

<a id="node-e6v82la"></a>

<p align="center"><kbd><img src="assets/7errnckv2ls.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/7g8e0u1xlwf.png" width="80%"></kbd></p>

> [!NOTE]
> This is a Python function that takes a pre-trained VGG model (vgg) and a
> list of layer names (layer_names) as inputs and returns a new Keras model
> that outputs the intermediate activations of the specified layers.
>
>
>
> The function first creates a list of output tensors by using a list
> comprehension to iterate over layer_names and extract the output tensor
> for each layer from the vgg model. Specifically, for each layer in
> layer_names, it gets the output tensor of that layer from the vgg model
> using vgg.get_layer(layer[0]).output. The output tensor is then added to the
> outputs list.
>
>
>
> After collecting the output tensors for all the specified layers, the function
> creates a new Keras model that takes the vgg model's input tensor as input
> and outputs a list of the intermediate activation tensors corresponding to
> the specified layers. The Model function in Keras is used to create this new
> model, and the outputs list and vgg.input tensor are passed as arguments
> to it.
>
>
>
> Finally, the function returns the **newly created Keras model** that outputs the
> intermediate activations of the specified layers.

<br>

<a id="node-a4i9jso"></a>

- **5.5 - Compute Total Cost**

<br>

<a id="node-9unh0de"></a>

- **5.5.1 - Compute Content Cost**

<br>

<a id="node-r0gy83p"></a>

<p align="center"><kbd><img src="assets/25koxxivxj8.png" width="80%"></kbd></p>

<br>

<a id="node-g7wcqri"></a>

- **5.5.2 - Compute Style Cost**

<br>

<a id="node-5eb4azl"></a>

<p align="center"><kbd><img src="assets/p4xmmyj3g5.png" width="80%"></kbd></p>

<br>

<a id="node-rtw2m9u"></a>

<p align="center"><kbd><img src="assets/tcpf4419lm.png" width="80%"></kbd></p>

<br>

<a id="node-rj9z9u1"></a>

- **Exercise 6 - train_step**

<br>

<a id="node-e05uhxk"></a>

<p align="center"><kbd><img src="assets/npcltkzk0x.png" width="80%"></kbd></p>

<br>

<a id="node-47wcwao"></a>

- **5.6 - Train the Model**

<br>

<a id="node-ha8r6ar"></a>

<p align="center"><kbd><img src="assets/dzweon7dawg.png" width="80%"></kbd></p>

<br>

<a id="node-1kdv6wo"></a>

<p align="center"><kbd><img src="assets/70oq7xwrwv.png" width="80%"></kbd></p>

<br>

<a id="node-6z6w8q8"></a>

<p align="center"><kbd><img src="assets/cdw4cdzezcv.png" width="80%"></kbd></p>

<br>

<a id="node-6zq9o2y"></a>

<p align="center"><kbd><img src="assets/jtoq4wxgj0p.png" width="80%"></kbd></p>

<br>

<a id="node-j33i9qt"></a>

- **\\*Conclusion:

\\*Great job on completing this assignment! You are now able to use Neural Style
Transfer to generate artistic images. This is also your first time building a model
in which the optimization algorithm updates the pixel values rather than the
neural network's parameters. Deep learning has many different types of models
and this is only one of them!

\\*What you should remember:

\\* • Neural Style Transfer is an algorithm that given a content image C and a
style image S can generate an artistic image

• It uses representations (hidden layer activations) based on a pretrained
ConvNet.

• The content cost function is computed using one hidden layer's activations.

• The style cost function for one layer is computed using the Gram matrix of that
layer's activations. The overall style cost function is obtained using several
hidden layers.

• Optimizing the total cost function results in synthesizing new images.**

<br>

<a id="node-f1ulsf7"></a>

- **6 - Test With Your Own Image (Optional/Ungraded)**

> [!NOTE]
> SẼ QUAY LẠI
> LÀM SAU

<br>

<a id="node-9mz2dxk"></a>

- **Here are some ideas on how to tune your
hyperparameters:

To select different layers to represent the style,
redefine STYLE_LAYERS

To alter the number of iterations you want to run the
algorithm, try changing epochs given in Section 5.6.

To alter the relative weight of content versus style, try
altering alpha and beta values

Happy coding!**

<br>

<a id="node-k59gh8t"></a>

- **7 - References

The Neural Style Transfer algorithm was due to Gatys et al. (2015). Harish
Narayanan and Github user "log0" also have highly readable write-ups this lab
was inspired by. The pre-trained network used in this implementation is a VGG
network, which is due to Simonyan and Zisserman (2015). Pre-trained weights
were from the work of the MathConvNet team.

• Leon A. Gatys, Alexander S. Ecker, Matthias Bethge, (2015). \\_A Neural
Algorithm of Artistic Style \\_

• Harish Narayanan, \\_Convolutional neural networks for artistic style transfer. \\_

• Log0, \\_TensorFlow Implementation of "A Neural Algorithm of Artistic Style". \\_

• Karen Simonyan and Andrew Zisserman (2015). \\_Very deep convolutional
networks for large-scale image recognition \\_

• \\_MatConvNet.\\_**

<br>

