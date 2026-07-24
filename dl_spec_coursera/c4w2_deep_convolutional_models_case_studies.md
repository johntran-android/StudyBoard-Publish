# C4w2_deep Convolutional Models: Case Studies

📊 **Progress:** `88` Notes | `118` Screenshots

---
<a id="node-xpm7ep6"></a>

## C4w2_deep Convolutional Models: Case Studies

<br>

<a id="node-7gtsb3p"></a>

## Why look at case studies?

<br>

<a id="node-e21nlb3"></a>

> [!NOTE]
> 1 Case studies of effective convolutional neural networks
>
> 2 Importance of looking at **case studies** to gain intuition and
> confidence in building effective convnets
>
> 3 **Transferability of neural network architecture** across different
> computer vision tasks
>
> 4 **Potential satisfaction in reading research papers** from the field
> of computer vision
>
> 5 Outline of the next few videos: classic networks such as
> **LeNet**-5, **AlexNet**, and **VGG**; **ResNet**, a deep 152-layer neural
> network with interesting tricks; and the **Inception** neural network
>
> 6 Benefits of learning from these examples, even for those not
> working in computer vision, as ideas are **cross-fertilizing** into
> other disciplines.

<br>

<a id="node-xnxwxb5"></a>

<p align="center"><kbd><img src="assets/eod3b086v0l.png" width="80%"></kbd></p>

<br>

<a id="node-7vnwcli"></a>

## Classic Networks

<br>

<a id="node-dtxzeoy"></a>

> [!NOTE]
> Xem qua 1 số classic ConvNet
> Nhận xét chung là nó thường có cấu trúc là 
> **Conv - Pool - Conv - Pool ...Conv - Pool- FC - FC.. -FC - Sofmax 
> Qua các layer thì nH, nW giảm, nC tăng**

<br>

<a id="node-mx2fvgt"></a>

<p align="center"><kbd><img src="assets/jad7mtn5k4.png" width="80%"></kbd></p>

> [!NOTE]
> Một số nhận xét:
> Qua các layer:
> nH, nW giảm, nC tăng
> Conv - Pool  - Conv - Pool
> **60k** params

<br>

<a id="node-hxs6wqk"></a>

<p align="center"><kbd><img src="assets/iw48mhx2l2m.png" width="80%"></kbd></p>

> [!NOTE]
> Một số nhận xét:
> Giống như LeNet như bigger
> **~60 mils** params

<br>

<a id="node-lxbx0fy"></a>

<p align="center"><kbd><img src="assets/mhfqfo6ss6t.png" width="80%"></kbd></p>

> [!NOTE]
> Một số nhận xét:
> Giống như Alexnet nhưng bigger
> **~138 mils** params

<br>

<a id="node-uyrz06j"></a>

## Resnet

<br>

<a id="node-vkn2ted"></a>

> [!NOTE]
> Training **very deep** neural networks is difficult due to **vanishing** and **exploding**
> gradient problems.
>
> **Skip connections** are a solution to these problems as they **allow activations from
> one layer to be fed to another layer much deeper** in the network, allowing the
> building of **ResNets**.
>
> **ResNets** are built from **residual blocks** which consist of a main path of layers and
> a shortcut that allows information to flow directly to deeper layers.
>
> Adding these residual blocks to a plain network turns it into a ResNet and allows
> for the training of **much deeper neural networks without significant loss** in
> performance.
>
> ResNets **help with the vanishing and exploding gradient problems**, allowing the
> training of **much deeper neural networks** without **compromising performance**.

<br>

<a id="node-hmugdqs"></a>

<p align="center"><kbd><img src="assets/s5f9r3rrjrh.png" width="80%"></kbd></p>

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

<a id="node-tug7xi5"></a>

<p align="center"><kbd><img src="assets/qb2j5xubes9.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là RestNet giúp khắc phục vấn đề **nhiều layer thì
> performance giảm** do Gradient Vanishing / Exploding từ đó
> **cho phép train very deep network**

<br>

<a id="node-f0y01c6"></a>

## Why Resnets Work

<br>

<a id="node-g99go3z"></a>

> [!NOTE]
> 1 **Residual Networks (ResNets)** work well in terms of training because they
> can be made **deeper without decreasing performance** on the training set.
>
> 2 Making neural networks **deeper** can **hurt the ability to train them well** on
> the training set, which is a prerequisite to doing well on the holdout, test
> sets or during deployment.
>
> 3 ResNets include **residual blocks** with **shortcut connections**, making it
> easy for these extra layers to **learn the identity function**.
>
> 4 **The identity function is easy to learn**, so the addition of extra layers in the
> neural network **doesn't hurt** its ability to perform **as well as a simpler
> network without these extra layers**.
>
> 5 **Same convolutions** are often used in ResNets to **ensure** that the
> dimension of the **input** and **output** of the layers **are equal**, making it easier
> to **carry out** the **shortcut connection** and the addition of two equal
> dimension vectors.

<br>

<a id="node-p0rlkvg"></a>

<p align="center"><kbd><img src="assets/ck619lf1l8l.png" width="80%"></kbd></p>

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

<a id="node-o245n23"></a>

<p align="center"><kbd><img src="assets/c55mo7b7oai.png" width="80%"></kbd></p>

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

<a id="node-howt58s"></a>

> [!NOTE]
> Sure, here's a more detailed answer with indexed main ideas:  
>
> 1 **ResNets** are deep neural networks that
> work well because they can be made **deeper** without **significantly hurting performance** on the **training** **set**,
> which is a **prerequisite** for good performance on the test set.
>
> 2 The reason **ResNets** can be made deeper without hurting performance is because of the use of **residual
> blocks**, which include a **skip connection** that allows the network to **learn the identity function** more easily.
>
> 3 Let's look at an example to see how the skip connection works in a ResNet block. Suppose we have an
> input X feeding into a neural network that outputs activation **a[l]**. We want to make the network deeper by
> adding two extra layers to output **a[l+2]**. We add a **residual block** with a **skip connection** to achieve this. If we
> assume all activations are greater than or equal to zero, then a[l+2] can be expressed as **g(w[l+2] * a[l+1] +
> b[l+2] + a[l])**, where g is the activation function and w[l+2] and b[l+2] are the weights and biases for the
> added layers.
>
> 4 If we use **L2 regularization to shrink the weights**, w[l+2], and assume b[l+2] = 0 for simplicity, then we can
> see that if w[l+2] = 0, the **entire term w[l+2] * a[l+1] + b[l+2] disappears**, leaving just **a[l]** **as the input to the
> activation function**. If g is the ReLU function, which outputs only non-negative numbers, then **g(a[l]) = a[l].**
> This means that the **identity function** is **easy for the residual block to learn**, and it can easily make **a[l+2]
> equal to a[l].**
>
> 5 Adding two extra layers with a residual block **does not significantly hurt performance** because the **residual
> block can easily learn the identity function**. However, the goal is not just to avoid hurting performance but to
> improve it. **If the added layers can learn something useful**, then the **network can do even better than simply
> learning the identity function.**
>
> 6 In **very deep plain networks** without residual connections, it becomes **difficult to learn even the identity
> function**, which is why **adding more layers can actually hurt performance**. **ResNets** **work because they make
> it easy for the extra layers to learn the identity function**, and from there they **have a chance of learning
> something useful.**
>
> 7 Another detail worth noting is that the **dimensions of z[l+2] and a[l] must be the same** for the skip
> connection to work. This is why s**ame convolutions are often used in ResNets to preserve the dimensions of
> the inputs and outputs of each layer**, making it **easier to carry out the skip connection** and the addition of the
> two vectors. **If the dimensions are different, an extra matrix must be added to make the dimensions match.**

<br>

<a id="node-wjav0e2"></a>

> [!NOTE]
> NETWORKS IN NETWORKS AND
> 1X1 CONVOLUTIONS

<br>

<a id="node-oldov10"></a>

> [!NOTE]
> 1 Using a **one-by-one convolution** can help in designing content
> architectures.
>
> 2 A one-by-one convolution can **multiply an image by a single number**
> or **perform a more complex operation**.
>
> 3 A one-by-one convolution takes each position in an input volume and
> applies a **fully connected neural network** to it.
>
> 4 A one-by-one convolution is sometimes called a "**network in network**"
> and has been influential in other neural network architectures.
>
> 5 One way to use a one-by-one convolution is to **shrink the number of
> channels** in an input volume.
>
> 6 A one-by-one convolution **adds nonlinearity** and **allows for learning a
> more complex function in a network**.

<br>

<a id="node-7hz74z7"></a>

<p align="center"><kbd><img src="assets/rbgpowinaba.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/w2xjnogg9ir.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái nó giống như apply 1 fully connected cho mỗi position của volumn (nhìn hình sẽ hiểu).

<br>

<a id="node-wuzejbj"></a>

<p align="center"><kbd><img src="assets/sfes3zumgr.png" width="80%"></kbd></p>

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

<a id="node-vz6fsop"></a>

## Inception Network Motivation

<br>

<a id="node-b5f07a1"></a>

<p align="center"><kbd><img src="assets/dmjfvec5igr.png" width="80%"></kbd></p>

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

<a id="node-unqn0hi"></a>

<p align="center"><kbd><img src="assets/93nffoksg8r.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/veffr1ltidi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/n9v7yqxvx9.png" width="80%"></kbd></p>

> [!NOTE]
> Tại sao lại nhân 5x5x192 đã hiểu: Mỗi lần convol là nó tính 5x5 phép
> nhân rồi cộng lại - là cho 1 lớp, có nc lớp -> 5x5xnc phép nhân

<br>

<a id="node-s31yjyc"></a>

<p align="center"><kbd><img src="assets/yvvdw8ik4zh.png" width="80%"></kbd></p>

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

<a id="node-77yfwko"></a>

## Inception Network

<br>

<a id="node-yk6a3tp"></a>

> [!NOTE]
> 1 The inception module takes the activation from a previous layer as input
> and **outputs multiple feature maps of different sizes.**
>
> 2 The inception network is made up of a **series of inception blocks**, which
> consist of **multiple inception modules** concatenated together.
>
> 3 The inception network **repeats these inception blocks** in different positions
> in the network.
>
> 4 The inception network also includes **additional side branches**, which **use
> hidden layers to make predictions** alongside the main output layer.
>
> 5 The side branches help to **ensure that the features computed are useful
> for making predictions**.

<br>

<a id="node-1gjan3d"></a>

<p align="center"><kbd><img src="assets/qb6frntg2y.png" width="80%"></kbd></p>

> [!NOTE]
> Ứng dụng ý tưởng ở lecture trước, Inception module sử dụng đủ loại filter, chú ý là như đã nói, dùng 2 bước
> với 16 cái 1x1(x192) và 3x3(x16) gọi là bottle-neck layer thay vì 3x3(x192) same padding để giảm số params

<br>

<a id="node-ezu95sh"></a>

<p align="center"><kbd><img src="assets/5dow7jwtf8v.png" width="80%"></kbd></p>

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

<a id="node-5lsz8xz"></a>

## Mobilenet

<br>

<a id="node-x2h72h5"></a>

> [!NOTE]
> 1 Introduction to **MobileNets**, a **convolutional neural network architecture** used for
> computer vision that can run on devices with **low computational power**.
>
> 2 Need for **MobileNets** as other neural networks are **computationally expensive.**
>
> 3 Explanation of the **normal convolution process** used in other neural networks.
>
> 4 **Computational cost** of normal convolution determined.
>
> 5 Introduction of **depthwise separable convolution** used in **MobileNets**.
>
> 6 Explanation of how the **depthwise convolution** works.
>
> 7 Calculation of the computational cost of depthwise convolution.

<br>

<a id="node-gqub1ep"></a>

<p align="center"><kbd><img src="assets/43f85a8f1n9.png" width="80%"></kbd></p>

<br>

<a id="node-4anwgd2"></a>

<p align="center"><kbd><img src="assets/wgyahjblqk.png" width="80%"></kbd></p>

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

<a id="node-e7fxiz4"></a>

<p align="center"><kbd><img src="assets/3qpmyxbgcv.png" width="80%"></kbd></p>

> [!NOTE]
> Còn depthwise thì
> nó khác 1 chút

<br>

<a id="node-60tq5md"></a>

<p align="center"><kbd><img src="assets/iz4s72xblvl.png" width="80%"></kbd></p>

> [!NOTE]
> **DepthWise** đại khái là ở mỗi lần filter convol nó sẽ tính riêng từng
> dimension, và không cộng lại để 'ép' lại thành 1 channel.

<br>

<a id="node-gim72j9"></a>

<p align="center"><kbd><img src="assets/ueafmnvunrh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/li04ozd6wu.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/tbc2s2zhd3.png" width="80%"></kbd></p>

<br>

<a id="node-c7v2gi5"></a>

<p align="center"><kbd><img src="assets/g8iuhzz1gko.png" width="80%"></kbd></p>

> [!NOTE]
> Kết quả là sau khi convol với 1 filter nó
> vẫn giữ số channel của input (chứ không
> ép lại thành 1 channel)
>
>
>
> 6x6x**3** - 1 **(chỉ một)** filter 3x3x3 -> 4x4x**3**

<br>

<a id="node-cradcae"></a>

<p align="center"><kbd><img src="assets/rlsrn7x4mae.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó cái cục này được convol qua 5 cái
> 1x1x3 filter để thành ra **4x4x5** giống như
> output của normal convolution '

<br>

<a id="node-k7hm3z5"></a>

<p align="center"><kbd><img src="assets/8q5e8hqgjva.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/icmxypp3zbo.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/pqvjjm0njx.png" width="80%"></kbd></p>

<br>

<a id="node-5nixah9"></a>

<p align="center"><kbd><img src="assets/j4jmz7ovln.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cho thấy cùng là từ input 6x6x3 -> output 4x4x5 nhưng
> dùng **Depth-wise Separable Convolution** giúp giảm **~10x**
> computational expensive so với **normal convolution**

<br>

<a id="node-6t2512o"></a>

<p align="center"><kbd><img src="assets/fk5o3p49uwu.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ổng nói đúng ra là phải vẽ icon thành nhiều lớp hơn 3x3xnc
> nếu nc = 8 chẳng hạn phải vẽ thành 8 lớp nhưng quy ước cứ giữ icon
> như vậy cho gọn và mình tự hiểu là được

<br>

<a id="node-2i1bsla"></a>

## Mobilenet Architecture

<br>

<a id="node-rm8jcsi"></a>

> [!NOTE]
> Main ideas:  1 **MobileNet** is a neural network that uses a **depthwise**
> **separable** **convolutional operation** to **reduce computational cost.** 
> 2 The **MobileNet v1** architecture uses a block comprising a **depthwise
> convolutional operation** and a **stack** of **13 layers** to make a
> **classification** prediction.
>
> 3 **MobileNet v2** is an **improvement** over the basic MobileNet
> architecture that **includes a residual connection** and an **expansion
> layer** before the **depthwise** convolution and the **pointwise** convolution.
>
> 4 MobileNet v2 repeats the block **17 times** and uses **pooling**,
> **fully-connected**, and **softmax layers** to make a classification prediction.
>
> 5 The MobileNet v2 **bottleneck block** **increases the size** of the
> representation within the block and **projects it back down to a smaller
> set of values**, **reducing the amount of memory** **needed** to store
> activations from layer to layer.

<br>

<a id="node-rq0hxgd"></a>

<p align="center"><kbd><img src="assets/toz3450wjaa.png" width="80%"></kbd></p>

<br>

<a id="node-9vdjfkv"></a>

<p align="center"><kbd><img src="assets/2p3ddbjv54v.png" width="80%"></kbd></p>

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

<a id="node-1438qc5"></a>

## Efficientnet

<br>

<a id="node-z3glpur"></a>

> [!NOTE]
> 1 The benefits of using **computationally efficient neural networks** like
> MobileNet V1 and V2.
>
> 2 The **challenge** of adapting neural networks to **different devices** with
> varying **computational resources**.
>
> 3 The concept of **EfficientNet** and how it can be used to **scale up** **or
> down** neural networks based on a **device's computational budget**.
>
> 4 The three factors that can be adjusted to scale up or down neural
> networks: **image resolution**, network **depth**, and layer **width**.
>
> 5 The importance of **finding the right trade-off between image
> resolution, network depth, and layer width** to optimize neural network
> performance for a specific device.
>
> 6 The usefulness of **open source implementations of EfficientNet** for
> adapting neural network architectures to specific devices.

<br>

<a id="node-l6kmtrv"></a>

<p align="center"><kbd><img src="assets/12qj50z0kim.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng higher resolution image

<br>

<a id="node-9lumc7k"></a>

<p align="center"><kbd><img src="assets/mtl9bz82tqh.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng deeper network

<br>

<a id="node-fuov5a5"></a>

<p align="center"><kbd><img src="assets/qfqu5u1d06.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng wider network

<br>

<a id="node-61q81v5"></a>

<p align="center"><kbd><img src="assets/2m1wzgntph7.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi là: Với cụ thể 1 giới hạn về khả năng tính toán, làm
> sao để chọn được / quyết định được r, d, w? Hay nói cách
> khác là  scale cái nào lên và giữ nguyên cái nào hoặc scale
> cùng lúc cả 3 cái lên với tỉ lệ bao nhiêu? -> **Loot at
> OpenSource implementation of EfficientNet**

<br>

<a id="node-hz6pjfq"></a>

<p align="center"><kbd><img src="assets/1v9qghyngqu.png" width="80%"></kbd></p>

> [!NOTE]
> Build N.N for mobile devices, embedded devices

<br>

<a id="node-das7s08"></a>

> [!NOTE]
> USING OPEN-SOURCE
> IMPLEMENTATION

<br>

<a id="node-gd1x1r5"></a>

> [!NOTE]
> 1 **Practical advice** on using neural network and **ConvNet** **architectures**
>
> 2 Importance of **open-source implementations** for **replicating** neural
> networks
>
> 3 **Difficulty** of replicating neural networks without **open-source
> implementations**
>
> 4 Benefits of using **open-source implementations**, such as **faster
> implementation and transfer learning**
>
> 5 Using **GitHub** to find open-source implementations

<br>

<a id="node-he4iic4"></a>

<p align="center"><kbd><img src="assets/8pybinn07hc.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nên search (GitHub) và xài cái người ta làm

<br>

<a id="node-xdzm3ko"></a>

## Transfer Learning

<br>

<a id="node-43drl2e"></a>

> [!NOTE]
> 1 **Pre-training** and **transfer learning** can help build computer vision
> applications faster.
>
> 2 Many **pre-trained models are available for download**, which have
> already been **trained on large public datasets**.
>
> 3 Using transfer learning, **pre-trained weights can be used as a starting
> point** for a new task.
>
> 4 **Frozen** **layers** in pre-trained models can be used to **extract features** that
> can be used for a new classification problem.
>
> 5 **Pre-computing features from frozen layers** can help speed up training
> with a small dataset.
>
> 6 **Fewer layers can be frozen** if there is a **larger labeled dataset** available.
>
> 7 If there is a **lot of data** available, **the whole pre-trained network can be
> used for training.**
>
> 8 There are different ways to initialize the last few layers of the network
> for the new classification problem.
>
> 9 The number of layers frozen and trained on top can be adjusted based
> on the available dataset size.

<br>

<a id="node-c2p9z6v"></a>

<p align="center"><kbd><img src="assets/qqdbzbz69tm.png" width="80%"></kbd></p>

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

<a id="node-z5i4vsj"></a>

<p align="center"><kbd><img src="assets/4s10xtkgbpl.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ổng nói Transfer learning hầu như là cái phải
> làm, trừ khi mình có rất rất nhiều data thì mới làm từ
> đầu

<br>

<a id="node-ww3h4qo"></a>

## Data Augmentation

<br>

<a id="node-prcds3q"></a>

> [!NOTE]
> 1 **Computer vision** task often **requires more data** to improve performance.
>
> 2 **Data augmentation** is a **commonly used technique** to improve the
> performance of computer vision systems.
>
> 3 **Mirroring** and **random cropping** are frequently used data augmentation
> techniques.
>
> 4 **Color shifting** is another commonly used data augmentation technique.
>
> 5 The motivation behind color shifting is to make the learning algorithm
> more robust to changes in image color.
>
> 6 **PCA Color Augmentation** is a specific implementation of color shifting.
>
> 7 **Loading images from a hard disk using a CPU** thread is a common
> implementation of data augmentation in practice.

<br>

<a id="node-bjnx27k"></a>

<p align="center"><kbd><img src="assets/zaqzmlssm6.png" width="80%"></kbd></p>

<br>

<a id="node-y9hds7m"></a>

<p align="center"><kbd><img src="assets/lxxezeo7jxm.png" width="80%"></kbd></p>

<br>

<a id="node-9pc1hst"></a>

<p align="center"><kbd><img src="assets/svcbwloh13g.png" width="80%"></kbd></p>

<br>

<a id="node-z5sgl3x"></a>

## State Of Computer Vision

<br>

<a id="node-e8ou3am"></a>

> [!NOTE]
> 1 Deep learning has been successfully applied to various problems, including
> computer vision.
>
> 2 **Computer vision is a complex problem**, and **deep learning requires a large
> amount of data to achieve good performance.**
>
> 3 There is often a **trade-off** between the **amount of data available** and **the need
> for hand-engineering** in machine learning.
>
> 4 The computer vision literature has historically **relied more on
> hand-engineering** due to **limited data availability**, but with the **increase in data**
> sets, the **use of hand-engineering has decreased**.
>
> 5 **Object detection**, a subset of computer vision, has **smaller data sets** and
> therefore requires more **complex algorithms** and **specialized components.** 
> 6 **Transfer learning** is a technique that can help in cases where there is **limited
> data.** 
> 7 Researchers in computer vision are enthusiastic about **achieving high
> performance on standardized benchmark** data sets and competitions.

<br>

<a id="node-nelkdci"></a>

<p align="center"><kbd><img src="assets/a9bqzg0bqyn.png" width="80%"></kbd></p>

<br>

<a id="node-n8h272g"></a>

<p align="center"><kbd><img src="assets/kcb5ebbka8.png" width="80%"></kbd></p>

<br>

<a id="node-uft6tzf"></a>

<p align="center"><kbd><img src="assets/7akfwooc3ua.png" width="80%"></kbd></p>

<br>

<a id="node-nrn8hi1"></a>

## Quiz

<br>

<a id="node-jz4mvia"></a>

<p align="center"><kbd><img src="assets/ki6pmtar2rg.png" width="80%"></kbd></p>

<br>

<a id="node-7kqh036"></a>

<p align="center"><kbd><img src="assets/hd6ltvaico.png" width="80%"></kbd></p>

<br>

<a id="node-63cikjb"></a>

<p align="center"><kbd><img src="assets/0lv4cwjl5cp.png" width="80%"></kbd></p>

<br>

<a id="node-n9zy1rb"></a>

<p align="center"><kbd><img src="assets/qxro94l67oe.png" width="80%"></kbd></p>

> [!NOTE]
> a[l+2] = g(z[l+2] + a[l]) (a[l] bỏ trong activation
> function luôn)
>
>
>
> vì g hay dùng ReLU nên nếu z[l+2] = 0 thì a[l+2] =
> max(0, a[l]) = a[l]

<br>

<a id="node-722ety8"></a>

<p align="center"><kbd><img src="assets/41dki4n31ow.png" width="80%"></kbd></p>

<br>

<a id="node-5koegu5"></a>

<p align="center"><kbd><img src="assets/4qmolmj9n2i.png" width="80%"></kbd></p>

<br>

<a id="node-dcxob0u"></a>

<p align="center"><kbd><img src="assets/yebf6u3s45.png" width="80%"></kbd></p>

<br>

<a id="node-k5yg0w7"></a>

<p align="center"><kbd><img src="assets/9aavquhux5.png" width="80%"></kbd></p>

<br>

<a id="node-ilghzpk"></a>

<p align="center"><kbd><img src="assets/urtp3js7ilc.png" width="80%"></kbd></p>

<br>

<a id="node-k7crvu3"></a>

<p align="center"><kbd><img src="assets/ot8nhz7y58.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4hkg3tanhch.png" width="80%"></kbd></p>

<br>

<a id="node-69ejvtb"></a>

## Programming Assignment: Residual Networks

<br>

<a id="node-1lpzfrj"></a>

> [!NOTE]
> • Implement the basic building blocks of ResNets in a deep
> neural network using Keras
>
> • Put together these building blocks to implement and train a
> state-of-the-art neural network for image classification
>
> • Implement a skip connection in your network
>
> For this assignment, you'll use Keras.

<br>

<a id="node-w5m7hll"></a>

#### Residual Networks

<br>

<a id="node-28enh16"></a>

<p align="center"><kbd><img src="assets/bij48krp94.png" width="80%"></kbd></p>

<br>

<a id="node-96x6ref"></a>

#### 1 - Packages

<br>

<a id="node-036m7k2"></a>

<p align="center"><kbd><img src="assets/g8dwxdfa53u.png" width="80%"></kbd></p>

<br>

<a id="node-jkkisjj"></a>

> [!NOTE]
> 2 - The Problem of Very
> Deep Neural Networks:
>
> Đại khái là vấn đề Gradient Vanishing - params về 0 rất nhanh 
> khiến model stop learning Hoặc / Exploding - params trở nên rất lớn

<br>

<a id="node-p57g3sy"></a>

<p align="center"><kbd><img src="assets/qqhyz3eh15p.png" width="80%"></kbd></p>

<br>

<a id="node-9g80tff"></a>

> [!NOTE]
> 3 - Building a Residual Network:
>
> Nhắc lại rằng RestNet không những giúp giải quyết vấn đề
> Vanishing Gradient mà còn giúp tăng performance của
> network
>
> Có hai loại block trong ResNet là **Identity** block và
> **Convolutional** block

<br>

<a id="node-c581y8s"></a>

<p align="center"><kbd><img src="assets/lytwb47lz49.png" width="80%"></kbd></p>

<br>

<a id="node-m2mwqvo"></a>

> [!NOTE]
> 3.1 - The Identity Block:
>
> Đại khái là các step để tạo nên ResNet's
> identity block
>
> Nói đến việc sẽ thêm 1 bước BatchNorm để
> tăng tốc training, chỉ cần  một dòng code với
> Keras.
>
> Và trong bài này mình sẽ skip 2 layer chứ
> không phải 1 như trong lecture
>
> Có cái vụ
> BatchNormalization
> chưa hiểu lắm

<br>

<a id="node-ik0tnvf"></a>

<p align="center"><kbd><img src="assets/llaebo3kqb.png" width="80%"></kbd></p>

<br>

<a id="node-wvdy37p"></a>

<p align="center"><kbd><img src="assets/2s97o71hkcw.png" width="80%"></kbd></p>

<br>

<a id="node-bbpx471"></a>

> [!NOTE]
> Exercise 1 - identity_block: Đại khái là làm theo gợi ý lần lượt khai báo các
> layer
>
> Conv2D, BatchNorm, Activation (Relu),
>
> Conv2D, BatchNorm, Activation (Relu)
>
> Conv2D, BatchNorm, Add, Activation (Relu)
>
> Với input thằng sau là ouput thằng trước từ đó X được update qua các layer.
>
> Để ý thấy ở đây nó dùng keras.layer.Activation('relu') thay vì keras.layer.
> RELU()  như ở P.A tuần trước
>
> Và thao tác '**Skip Connection**' được thực hiện bằng cách save X_shortcut
> và add  với X ở layer **Add**

<br>

<a id="node-13skqfb"></a>

<p align="center"><kbd><img src="assets/zemloac7j8.png" width="80%"></kbd></p>

<br>

<a id="node-4ztvj55"></a>

<p align="center"><kbd><img src="assets/1pahk5eud3s.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/w37wcbmuh9.png" width="80%"></kbd></p>

<br>

<a id="node-yod9wce"></a>

<p align="center"><kbd><img src="assets/owh998gzey.png" width="80%"></kbd></p>

<br>

<a id="node-f3hqhpe"></a>

> [!NOTE]
> 3.2 - The Convolutional Block:
>
> Đại khái là cái này chỉ khác cái identity block ở chỗ nó có
> thêm bước dùng Conv2D để resize X_shortcut nhằm để
> X và X_shortcut cùng size cho bước Add, bước này đóng
> vai trò như \\/**Ws**\\/ trong lecture nói tới.
>
> Nói tới đại khái là không áp dụng Activation function vì
> mục đích chỉ là resize thôi
>
> Để ý thấy cho X và X_shortcut cùng size thì ở Conv2D
> cho layer thứ 3 và cho shortcut phải cùng số lượng filter
>
> Có cái vụ Glorot uniform
> seed là không hiểu

<br>

<a id="node-uaclxn3"></a>

<p align="center"><kbd><img src="assets/9hndoy9b8uj.png" width="80%"></kbd></p>

<br>

<a id="node-nmdxqpt"></a>

<p align="center"><kbd><img src="assets/suhph4foeg.png" width="80%"></kbd></p>

<br>

<a id="node-def4aty"></a>

> [!NOTE]
> Exercise 2 - convolutional_block
>
> Đại khái là làm theo gợi ý lần lượt khai báo các layer
>
> Conv2D, BatchNorm, Activation (Relu),
>
> Conv2D, BatchNorm, Activation (Relu)
>
> Conv2D, BatchNorm, Add, Activation (Relu)
>
> Với input thằng sau là ouput thằng trước từ đó X được
> update qua các layer.
>
> Chỉ có thêm cái Conv và Batch cho Shortcut với filter là
> F3

<br>

<a id="node-6p3nlks"></a>

<p align="center"><kbd><img src="assets/0qiu9a37bwe.png" width="80%"></kbd></p>

<br>

<a id="node-rsrel4p"></a>

<p align="center"><kbd><img src="assets/n55t16oituc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/dn9v9d5qwyr.png" width="80%"></kbd></p>

<br>

<a id="node-qc37jwd"></a>

<p align="center"><kbd><img src="assets/qo1dt69n64l.png" width="80%"></kbd></p>

<br>

<a id="node-65idkcp"></a>

> [!NOTE]
> 4 - Building Your First ResNet Model (50 layers)
>
> Đại khái là dùng các function ở trên để tạo một
> network  **so deep** có 50 layers (?!) có kiến trúc
> như hình

<br>

<a id="node-y8lqmxm"></a>

<p align="center"><kbd><img src="assets/b4ghalv169i.png" width="80%"></kbd></p>

<br>

<a id="node-xb5q31x"></a>

> [!NOTE]
> Exercise 3 - ResNet50
>
> Đại khái là cũng lần lượt define từng layer
> theo kiến trúc của network define trong sơ
> đồ.
>
> Và cuối cùng tạo model: model =
> Model(inputs = X_input, outputs = X)

<br>

<a id="node-hxm1y7k"></a>

<p align="center"><kbd><img src="assets/cqk79tmi0p.png" width="80%"></kbd></p>

<br>

<a id="node-d9t9frc"></a>

<p align="center"><kbd><img src="assets/hh3bzcxj7tf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/wfwc5ci2tr7.png" width="80%"></kbd></p>

<br>

<a id="node-wze4dca"></a>

<p align="center"><kbd><img src="assets/bo3mi6kpn97.png" width="80%"></kbd></p>

<br>

<a id="node-kn50oov"></a>

> [!NOTE]
> Compile và Load Data 
>
> Dùng **Adam** optimizers, 
> **categorical_crossentropy** loss function, 
> Metrics dùng **accuracy** Data là bộ **hand-sign data** bữa trước

<br>

<a id="node-s8z3ypu"></a>

<p align="center"><kbd><img src="assets/qidox4mqtd.png" width="80%"></kbd></p>

<br>

<a id="node-kdycfys"></a>

<p align="center"><kbd><img src="assets/dd07nnkalkh.png" width="80%"></kbd></p>

<br>

<a id="node-obqvk14"></a>

> [!NOTE]
> ..và train model dùng 10 epochs, batch size
> = 32

<br>

<a id="node-4z28wyj"></a>

<p align="center"><kbd><img src="assets/8a8nbq75cpf.png" width="80%"></kbd></p>

<br>

<a id="node-71h1byw"></a>

<p align="center"><kbd><img src="assets/2viawc95lp1.png" width="80%"></kbd></p>

<br>

<a id="node-6l4re7u"></a>

<p align="center"><kbd><img src="assets/qcz5829pcym.png" width="80%"></kbd></p>

<br>

<a id="node-dbs24rt"></a>

> [!NOTE]
> Submit và load pretrain model: Đại khái là ổng kêu thích thì train lại
> với nhiều  epoch hơn và load về cái model đã được train bằng GPU
> để chạy thử xem accuracy bao nhiêu.
>
> **What you should remember**:
>
> • Very deep "plain" networks don't work in practice because vanishing
> gradients make them hard to train.
>
> • Skip connections help address the Vanishing Gradient problem.
> They also make it easy for a ResNet block to learn an identity
> function.
>
> • There are two main types of blocks: The **identity block** and
> the **convolutional block**.
>
> • Very deep Residual Networks are built by stacking these blocks
> together.
>
> State of the art: HIện đại nhất. Ý là
> dùng cái này là hiện đại nhất rồi

<br>

<a id="node-2s4xf1o"></a>

<p align="center"><kbd><img src="assets/m8f26poo1h.png" width="80%"></kbd></p>

<br>

<a id="node-kvwrqq9"></a>

<p align="center"><kbd><img src="assets/kayicbae1hi.png" width="80%"></kbd></p>

<br>

<a id="node-firnt3d"></a>

> [!NOTE]
> 5 - Test on Your Own Image (Optional/Ungraded)
>
> Dùng hình tự chụp để test thử thấy hình như không đúng.
> Ổng có hỏi là h thử nghĩ xem tại sao ?
>
> Có thể liên quan đến 'distribution' Hình dùng để train là trên
> mạng, còn đây là hình tự  chụp dẫn đến training set và
> production set bị khác distribution
>
> Giải pháp là gì? Xem lại Course 3
>
> Giải pháp là gì -> Xem lại course 3

<br>

<a id="node-4lbvcvf"></a>

<p align="center"><kbd><img src="assets/ir98vw2gv8a.png" width="80%"></kbd></p>

<br>

<a id="node-hqfw8in"></a>

<p align="center"><kbd><img src="assets/45bcuzyduah.png" width="80%"></kbd></p>

<br>

<a id="node-wsh9quf"></a>

> [!NOTE]
> 6 - Bibliography
>
> This notebook presents the ResNet algorithm from He
> et al. (2015).  The implementation here also took
> significant inspiration and follows the structure given in
> the GitHub repository of Francois Chollet:
>
> • Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian
> Sun - \\_Deep Residual Learning for Image Recognition
> (2015) \\_
>
> • Francois Chollet's GitHub repository: \\_https://github.
> com/fchollet/deep-learning-models/blob/master/resnet50.
> py\\_

<br>

<a id="node-guh4bx4"></a>

## Programming Assignment: Transfer Learning With Mobilenet

<br>

<a id="node-gup2urj"></a>

<p align="center"><kbd><img src="assets/4fhceupahop.png" width="80%"></kbd></p>

> [!NOTE]
> Welcome to this week's assignment, where you'll be using transfer
> learning on a pre-trained CNN to build an Alpaca/Not Alpaca
> classifier! A pre-trained model is a network that's already been trained
> on a large dataset and saved, which allows you to use it to customize
> your own model cheaply and efficiently. The one you'll be using,
> MobileNetV2, was designed to provide fast and computationally
> efficient performance. It's been pre-trained on ImageNet, a dataset
> containing over 14 million images and 1000 classes. By the end of
> this assignment, you will be able to:
>
> • \\/Create a dataset\\/ from a directory
>
> • \\/Preprocess and augment data using the Sequential API\\/
>
> • Adapt a \\/pretrained model to new data\\/ and train a classifier using
> the Functional API and \\/MobileNet\\/
>
> • Fine-tune a classifier's final layers to improve accuracy

<br>

<a id="node-sn0yvw9"></a>

#### 1 - Packages

<br>

<a id="node-gw61jbi"></a>

<p align="center"><kbd><img src="assets/9gfxc8681ow.png" width="80%"></kbd></p>

<br>

<a id="node-l5qibl9"></a>

> [!NOTE]
> 1.1 Create the Dataset and Split it into Training and
> Validation Sets
>
> Đại khái là dùng \\/**image_dataset_from_directory**()
> của Keras để **load image từ  thư mục** \\/chỉ định,
> return một **TensorFlow Dataset**, quy định sẵn batch
> size, size để nó Resize image, tỉ lệ phân chia và tên
> các gói để phân chia.

<br>

<a id="node-2t3p8ab"></a>

<p align="center"><kbd><img src="assets/c5rkuj1ryf8.png" width="80%"></kbd></p>

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

<a id="node-0hna6cy"></a>

<p align="center"><kbd><img src="assets/xwu3suui6ub.png" width="80%"></kbd></p>

> [!NOTE]
> Có một số hình bị sai

<br>

<a id="node-pieeopn"></a>

> [!NOTE]
> 2 - Preprocess and Augment Training Data:
>
> Đại khái là nói về \\/**prefetch()**\\/ data đã từng dùng ở
> assignment  trước để kiểu như chuẩn bị để khi chạy
> G.D luôn có sẵn data. Lợi hại hơn nữa là nó có thể tối
> ưu số lượng data chuẩn bị sẵn giùm mình luôn bằng
> cách để \\/buffer_size = AUTOTUNE.
>
> Lợi hại hơn nữa là nó có thể làm cái vụ Data Augmentation nữa\\/

<br>

<a id="node-uezwll9"></a>

<p align="center"><kbd><img src="assets/qmihm90pjd.png" width="80%"></kbd></p>

<br>

<a id="node-8wzfdjv"></a>

> [!NOTE]
> Exercise 1 - data_augmenter:
>
> Đại khái đơn giản là khởi tạo 1 Sequential và bỏ vào 2 layer:
> RandomFlip và RandomRotation
>
> data_augmentation = tf.keras.Sequential()
> data_augmentation.add(RandomFlip('horizontal'))
> data_augmentation.add(RandomRotation(0.2))
>
> Sau đó xài thử trên một image xem chơi

<br>

<a id="node-c9q0yni"></a>

<p align="center"><kbd><img src="assets/uoh76inbq2.png" width="80%"></kbd></p>

<br>

<a id="node-h935dj0"></a>

<p align="center"><kbd><img src="assets/sqf9jyhlpff.png" width="80%"></kbd></p>

<br>

<a id="node-rcamk14"></a>

> [!NOTE]
> **What you should remember:**
>
> • When calling \\/image_data_set_from_directory\\/(), specify
> the train/val subsets and match the seeds to prevent
> overlap
>
> • Use \\/prefetch\\/() to prevent memory bottlenecks when
> reading from disk
>
> • Give your model more to learn from with simple data
> \\/augmentations\\/ like rotation and flipping.
>
> • When using a pretrained model, it's best to \\/reuse the
> weights\\/ it was trained on.

<br>

<a id="node-oq85r6q"></a>

<p align="center"><kbd><img src="assets/alfxoh105n.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng lại preprocess_input???

<br>

<a id="node-4qdoo9c"></a>

#### 3 - Using MobileNetV2 for Transfer Learning

<br>

<a id="node-r0t57e6"></a>

<p align="center"><kbd><img src="assets/44am3b1if5u.png" width="80%"></kbd></p>

<br>

<a id="node-zolljyn"></a>

#### 3.1 - Inside a MobileNetV2 Convolutional Building Block

<br>

<a id="node-429r9fe"></a>

> [!NOTE]
> Đại khái là nói lại về
> MobileNet v2 building block

<br>

<a id="node-pt7fbf3"></a>

<p align="center"><kbd><img src="assets/homz63w9vrn.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qnb7t4avo9.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói lại về MobileNet v2 building block

<br>

<a id="node-a16ador"></a>

<p align="center"><kbd><img src="assets/a2ioc6r81jj.png" width="80%"></kbd></p>

<br>

<a id="node-6zozv10"></a>

<p align="center"><kbd><img src="assets/osleh8lbgyc.png" width="80%"></kbd></p>

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

<a id="node-k2ugd8d"></a>

> [!NOTE]
> Đại khái là nó dùng lại cái MobileNet v2, \\/include_top\\/ =
> True tức là giữ nguyên layer cuối (Softmax), và
> weights đã được pretrained
>
> Summary xem thì nhận thấy :
>
> Đại khái là cấu trúc 1 Bottleneck layer thường sẽ như
> vầy
>
> -> Expand Conv - Expand BN - Expand Relu
> Depthwise - Depthwise BN - Depthwise Relu Project
> Conv - Project BN - Add (Skip connection) ->

<br>

<a id="node-lis91uj"></a>

<p align="center"><kbd><img src="assets/pq3nn8rfk2e.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó dùng lại cái MobileNet v2,
> include_top = True tức là giữ nguyên layer cuối
> (Softmax), và weights đã được pretrained
>
> Chưa hiểu IMAGE_SHAPE = IMG_SIZE + (3,) là sao

<br>

<a id="node-0fd6wqi"></a>

<p align="center"><kbd><img src="assets/8cagapki3ae.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là cấu trúc 1 Bottleneck layer thường sẽ như vầy
>
>
>
> -> Expand Conv - Expand BN - Expand Relu
> Depthwise - Depthwise BN - Depthwise Relu
> Project Conv - Project BN - Add (Skip connection) ->

<br>

<a id="node-qz27x1j"></a>

> [!NOTE]
> What you should remember:
>
> MobileNetV2's unique features are:
>
> Depthwise separable convolutions that provide lightweight
> feature filtering and creation Input and output bottlenecks
> that preserve important information on either end of the
> block
>
> Depthwise separable convolutions deal with both spatial
> and depth (number of channels) dimensions

<br>

<a id="node-zwr1ycj"></a>

> [!NOTE]
> Đại khái là Xem thử performance của cái pretrain
> network rao sao trên 1 batch data
>
> Kết quả không tốt do pretrain data không có
> alpaca, nên việc tiếp theo là bỏ layer cuối (top
> layer) mà train lại layer cuối

<br>

<a id="node-sy4d5z7"></a>

<p align="center"><kbd><img src="assets/qbf4omboe1m.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là lấy 1 batch data (32 cái) ra và nói về cái format của kết
> quả, trả về 2 con số probability cao nhất ứng với khả năng của 1
> hình thuộc về 2 loại

<br>

<a id="node-akwygcj"></a>

<p align="center"><kbd><img src="assets/02oqosvukw4u.png" width="80%"></kbd></p>

<br>

<a id="node-52lpet0"></a>

<p align="center"><kbd><img src="assets/lsikmurmugr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là kết quả không tốt do pretrain data không có alpaca, nên
> việc tiếp theo là bỏ layer cuối (top layer) mà train lại layer cuối

<br>

<a id="node-9psujm2"></a>

> [!NOTE]
> 3.2 - Layer Freezing with the Functional API
>
> Đại khái ta sẽ bỏ layer cuối và đóng băng (freez)
> cái pretrain network  đơn giản bằng cách set
> params \\/include_top = false và , model.trainable =
> false
>
> Sau đó add 1 layer và train nó.\\/

<br>

<a id="node-ls4zf1k"></a>

<p align="center"><kbd><img src="assets/cw9ux50ii3i.png" width="80%"></kbd></p>

<br>

<a id="node-f9loe37"></a>

> [!NOTE]
> Exercise 2 - alpaca_model:
>
> Theo gợi ý lần lượt define model mới, dùng
> lại Pretrain model  Add thêm layer cuối với
> GlobalAveragePooling2D, Dropout, và
> Dense với 1 unit
>
> Chỉ chưa hiểu tại sao layer cuối dùng Linear
> mà ko phải sigmoid

<br>

<a id="node-qf3w5m1"></a>

<p align="center"><kbd><img src="assets/td25yah5k7a.png" width="80%"></kbd></p>

> [!NOTE]
> Tại sao lại Linear ở cuối mà ko phải Sigmoid

<br>

<a id="node-60k3x03"></a>

<p align="center"><kbd><img src="assets/8x34mbdn1uf.png" width="80%"></kbd></p>

<br>

<a id="node-rw6fq0a"></a>

> [!NOTE]
> Compile & train model: Adam
> optimizer, BinaryCrossentropy loss
> function, accuracy

<br>

<a id="node-beytl4l"></a>

<p align="center"><kbd><img src="assets/77obyf16bn7.png" width="80%"></kbd></p>

<br>

<a id="node-ziv4znz"></a>

<p align="center"><kbd><img src="assets/isrytzwzgi.png" width="80%"></kbd></p>

<br>

<a id="node-dgxznv4"></a>

<p align="center"><kbd><img src="assets/wkiix5qsg3.png" width="80%"></kbd></p>

<br>

<a id="node-g6vb7oq"></a>

> [!NOTE]
> 3.3 - Fine-tuning the Model:
>
> Đại khái là gỡ băng 1 số layer cuối (bao nhiêu thì tuỳ
> nên phải thử) để nó train các 'high feature' với data
> của con alpaca, giữ nguyên các  'low feature'

<br>

<a id="node-3u9po8a"></a>

<p align="center"><kbd><img src="assets/0fdy7pw132zo.png" width="80%"></kbd></p>

<br>

<a id="node-aj3qypn"></a>

> [!NOTE]
> Exercise 3:
>
> Đại khái là lấy base_model ra (model2.
> layers[4]) sửa lại một chút như unfreez từ
> layer số 120 trở đi

<br>

<a id="node-8iiz7fw"></a>

<p align="center"><kbd><img src="assets/4lmna9dq3iw.png" width="80%"></kbd></p>

> [!NOTE]
> tại sao model2.layers[4] ???

<br>

<a id="node-bo0oaks"></a>

<p align="center"><kbd><img src="assets/5bngy26ptda.png" width="80%"></kbd></p>

> [!NOTE]
> Tốt hơn hẳn, validation_acc: 95%

<br>

<a id="node-tsuxdgk"></a>

<p align="center"><kbd><img src="assets/nbuzv3mz1dc.png" width="80%"></kbd></p>

<br>

<a id="node-7h47r78"></a>

<p align="center"><kbd><img src="assets/5tfxym6klbh.png" width="80%"></kbd></p>

<br>

<a id="node-39pyxyd"></a>

> [!NOTE]
> **What you should remember**:
>
> • To adapt the classifier to new data: Delete the top layer, add a new
> classification layer, and train only on that layer
>
> • When freezing layers, avoid keeping track of statistics (like in the batch
> normalization layer)
>
> • Fine-tune the final layers of your model to capture high-level details near
> the end of the network and potentially improve accuracy
>
> **Congratulations!** You've completed this assignment on transfer learning
> and fine-tuning. Here's a quick recap of all you just accomplished:
>
> • Created a dataset from a directory
>
> • Augmented data with the Sequential API
>
> • Adapted a pretrained model to new data with the Functional API and
> MobileNetV2
>
> • Fine-tuned the classifier's final layers and boosted the model's accuracy

<br>

