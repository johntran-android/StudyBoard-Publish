# Lecture 11/16 - Detection And
segmentation

📊 **Progress:** `108` Notes | `144` Screenshots

---
<a id="node-wsqi4hb"></a>

## Lecture 11/16 - Detection And
segmentation

<br>

<a id="node-s7a5fnu"></a>

## Segmentation

<br>

<a id="node-mt2j8nt"></a>

<p align="center"><kbd><img src="assets/y05rdyt2tzf.png" width="80%"></kbd></p>

> [!NOTE]
> Cho tới giờ ta chỉ làm bài toán image classification, với cnn xử lý
> một input image ví dụ vgg để rồi last fc layer output ra một vector
> 4096, được pass qua output layer 1000 unit để ra 1000 class scores

<br>

<a id="node-lp2uh39"></a>

<p align="center"><kbd><img src="assets/774jddvsgy8.png" width="80%"></kbd></p>

<br>

<a id="node-nmpfjee"></a>

<p align="center"><kbd><img src="assets/knjkr5ecnr.png" width="80%"></kbd></p>

> [!NOTE]
> đầu tiên là segmentation, trong đó thay vì chỉ classify cả bức ảnh nói chung
> thì ta muốn classify từng pixel. Để rồi label sẽ có dạng như vầy, được label
>
>
>
> Cái này có đặc điểm, ví dụ như (những pixel) chỗ hai con bò trong hình sẽ 
> đều được gán label là "cow" chứ không cần phân biệt con nào. Đây là nhược
> điểm mà qua Instance Segmentation sẽ được khắc phục.

<br>

<a id="node-g56ttpa"></a>

<p align="center"><kbd><img src="assets/om63niky1p.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là ta có thể dùng một image classification model để thực hiện bài toán
> segmentation theo cách sau: Ta sẽ dùng cách thức là sliding window có thể
> hiểu đại khái là ta sẽ train một classification model để map input là các crop
> window với class của cái pixel ở giữa window đó. Khi đó, ta sẽ dùng mô hình
> classification để tạo segmentation bằng cách slide cái window qua hết caí
> hình, mỗi lần thì forward cái crop Image qua classifier để predict ra class của
> pixel. Kết quả là ta sẽ cũng có được segmentation.

<br>

<a id="node-xk0ccyr"></a>

<p align="center"><kbd><img src="assets/zh7ynvtsivf.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên cách này rất không hiệu quả

<br>

<a id="node-s5va47l"></a>

<p align="center"><kbd><img src="assets/z97ecws0a2s.png" width="80%"></kbd></p>

> [!NOTE]
> cách làm thứ hai là Fully Convolutional, tức dùng convolution layer với chỉ ..
> conv  layer chứ không có pooling hay gì hết, với conv  layer cuối có output
> shape là (C,H,W) (tức cùng spatial size với input image) C là số class. Và
> một (tạm gọi là depth) vector (vector mà các unit là ở cùng  một vị trí trong
> các spatial map khác nhau) sẽ mang tính chất là chứa các  class scores mà
> model dự đoán cho pixel tại vị trí đó. Rồi cũng qua softmax để biến thành
> predicted probability distribution.
>
>
>
> Loss function sẽ là ta sẽ tính cross entropy loss giữa ground truth probability
> và predicted probability distribution. Để rồi sum / average loss trên mọi pixel
> để có cost function.
>
>
>
> Có câu hỏi đại ý là có phải ta sẽ giả định rằng là ta đã biết trước các class
> ko? -> Đúng vậy, giống như bài toán classification thôi

<br>

<a id="node-cg4fqh2"></a>

<p align="center"><kbd><img src="assets/r5ybhpsbw8.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là Justin cho biết nếu train một deep cnn model với cứ same
> padding trong suốt các layer thì nó tuy sẽ đạt hiệu suất tốt như lại vô
> cùng tốn kém về tính toán và memory.
>
>
>
> Ngoài ra Justin còn nhắc lại cái vụ khi ta stack nhiều conv layer lại thì
> effective receptive field sẽ mở rộng từ từ một cách tuyến tính vậy với
> cái kiểu mà ko dùng pooling thì phải cần rất nhiều conv layer thì
> effective receptive field mới  mở rộng đủ để cover hết image

<br>

<a id="node-disrcsi"></a>

<p align="center"><kbd><img src="assets/22j4kh23pen.png" width="80%"></kbd></p>

> [!NOTE]
> Do đó người ta thường dùng kiến trúc model mà trong đó phần đầu qua từng
> layer output sẽ ngày càng nhỏ lại bề W,H nhưng dày lên bề sâu giống như
> các kiến trúc cnn của classification. Nhưng phần hai, thì ngược lại để dần
> khôi phục spatial size và giảm depth.
>
>
>
> Thì cái này nhờ giảm spatial size nên cho phép receptive field có thể tăng lên
> nhanh hơn nhiều

<br>

<a id="node-dfy02t6"></a>

<p align="center"><kbd><img src="assets/y3urp6afwof.png" width="80%"></kbd></p>

> [!NOTE]
> Nói về cách để upsampling (tăng spatial size) thì đầu tiên là un-pooling,  có
> hai loại nearest neighbor trong đó nearest neighbor thì đơn giản là ta copy
> nó ra những vùng xung quanh. Còn bed of nails thì giá trị cũ cứ nằm ở góc,
> chèn mấy số 0 vào thôi (gọi là bed of nails vì chỉ có vài chỗ có giá trị, còn
> lại là ko giống như cái chân giường).

<br>

<a id="node-m45vp4n"></a>

<p align="center"><kbd><img src="assets/sijcknqm1rr.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, tương tự như cái bilinear interpolation ta đã làm hồi nãy RoI Aligned,
> thì ta cũng có thể áp dụng vào đây. Với các vị trí bed nails ta sẽ
> interpolate sang các vị trí khác để tạo ra một phiên bản max pooling
> mượt hơn

<br>

<a id="node-s3wif36"></a>

<p align="center"><kbd><img src="assets/tqk2q66moei.png" width="80%"></kbd></p>

> [!NOTE]
> Một cách khác nữa là Bicubic
> interpolation, có thể tìm hiểu sau

<br>

<a id="node-y2mlq86"></a>

<p align="center"><kbd><img src="assets/zs9fvpnudn8.png" width="80%"></kbd></p>

> [!NOTE]
> tiếp theo nói về khái niệm Max Unpooling, giải thích có thể dài dòng nhưng
> nhìn hình là hiểu liền. Đại khái là ví dụ lúc downsampling trong 4 ô 1,2,3, 5
> thì số 5 lớn nhất thì lúc Unpooling, ta cũng sẽ để số 1 nằm tại vị trí tương
> ứng với số 5 hồi nãy, thay vì nếu là pooling như hồi nãy thì cứ cho 1 nằm
> ở góc.
>
>
>
> Và một nguyên tắc đó là, lúc downsampling nếu dùng average pooling thì
> lúc upsampling nên dùng nearest neighbor unpooling. Còn lúc down
> sampling dùng max pooling thì lúc upsampling dùng max upsampling

<br>

<a id="node-peu5r9k"></a>

<p align="center"><kbd><img src="assets/ssvigunyt9q.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi là tại sao việc (tạm gọi là) "giữ lại vị trí gốc" như vừa rồi lại quan
> trọng: Thì đại khái là vì khi mã pooling, theo ý nghĩa nào đó thì ít nhiều thông
> tin ở chiều spatial đã bị mất, ví dụ như từ 4 'ô' [1,2,3,5] qua max pooling chỉ
> còn 5, thì kiểu như ta không biết số 5 này thật sự nằm chỗ nào trong 4 ô ban
> đầu. Mà với bài toán segmentation thì vị trí chính xác kiểu như quan trọng.
>
>
>
> Nên việc giữ được thông tin như vừa nói là quan trọng.
>
>
>
> =====
>
>
>
> Có câu hỏi là việc này có ảnh hưởng gì đến quá trình backprop không: Không
> vì việc giữ thêm vài con số (vị trí) chẳng nhằm nhò gì so với những thứ khác.

<br>

<a id="node-sqo9f0j"></a>

<p align="center"><kbd><img src="assets/9ws0oggfeik.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sf2x4isflwq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là phương pháp pooling kiểu như fixed function, còn cách thứ hai
> sắp nói tới là Transpose Convolution.
>
>
>
> Đại khái là review lại chút về convolution trong đó tại mỗi vị trí ta tính một
> phép dot-product giữa input và filter. Sau đó nhích qua vị trí tiếp
>
>
>
> Còn nếu stride = 2 thì nhích qua 2 ô, ko có gì phải nói cả. Và nó chính là
> tỉ lệ giảm spatial size.

<br>

<a id="node-o191oae"></a>

<p align="center"><kbd><img src="assets/w0y8at41prs.png" width="80%"></kbd></p>

> [!NOTE]
> còn với Transpose convolution, learnable filter sẽ nhân với input, input sẽ
> đóng vai trò của scalar để ra output. và cũng dùng stride để tăng kích
> thước, vùng overlap thì cộng lại. Cái này có thể có tên là Deconvolution.
>
>
>
> Fractionally strided convolution / Backward strided convolution

<br>

<a id="node-jjco6cl"></a>

<p align="center"><kbd><img src="assets/ib5reodgcp.png" width="80%"></kbd></p>

> [!NOTE]
> Minh họa 1D Transpose Convolution, learnable filter params sẽ được
> scale bởi input để ra kết quả, vùng chồng lấn sẽ sum lại.

<br>

<a id="node-j0fsr0i"></a>

<p align="center"><kbd><img src="assets/81hkfn4nz2v.png" width="80%"></kbd></p>

<br>

<a id="node-ze3670d"></a>

<p align="center"><kbd><img src="assets/325hiki4ozz.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hwxq95o72nn.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là ta có thể thực hiện phép convolution như một phép nhân matrix để "
> làm một phát một, chứ không phải slide cái filter rồi tính toán tuần tự" cái
> này mình đã biết qua việc tự làm qua assignment 3 - Pytorch

<br>

<a id="node-dein3d7"></a>

<p align="center"><kbd><img src="assets/njd81q6gs1d.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là convolution transpose với stride bằng 1 thì cũng co thể coi là
> giống một convolution thông thường khi ta cũng có thể thể hiện dưới
> dạng matrix multiplication.

<br>

<a id="node-or8iekj"></a>

<p align="center"><kbd><img src="assets/2234de7lule.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là với stride = 2 thì convolution transpose trở nên không còn là
> convolution thông thường nữa. Khi ta thấy kết quả ví dụ như ax, ay, ..
> không còn là kết quả của phép convol
>
>
>
> Nên tóm lại là muốn nói, cái tên transpose convolution không đúng lắm.

<br>

<a id="node-6vrcqdc"></a>

<p align="center"><kbd><img src="assets/ki7h0ayr48h.png" width="80%"></kbd></p>

> [!NOTE]
> câu hỏi đại khái là tại sao chỗ vùng chồng lấn ta lại sum chứ không
> average.
>
>
>
> Đó là bởi công thức của transpose convolution nó như vậy, tuy nhiên đúng
> là cách làm này gây ra các vấn đề như checker-board artifact (một dạng
> pattern kiểu bàn cờ mà mình đã thấy người ta nói đến trong GANSpec),
> do đó người ta dần tìm cách khắc phục bằng cách dùng 4x4 stride 2, hay
> 2x2 stride 2

<br>

<a id="node-e39u4f9"></a>

<p align="center"><kbd><img src="assets/v6gpwxlf70g.png" width="80%"></kbd></p>

> [!NOTE]
> tóm lại là ta sẽ dùng kiến trúc như này (gọi là U-Net) với phần đầu dùng
> convolution để giảm (spatial) size và tăng depth và phần sau dùng
> Transpose Convolution để tăng (spatial) size và giảm depth.
>
>
>
> Và train model với backpropagation như thông thường để mập input
> image với label output

<br>

<a id="node-7gyoyfk"></a>

## Classification +
localization

<br>

<a id="node-s4p9vzf"></a>

<p align="center"><kbd><img src="assets/66bl1civ4x6.png" width="80%"></kbd></p>

> [!NOTE]
> qua bài toán mở rộng thứ hai (mở rộng từ bài toán truyền thống
> classification) là classification + localization.
>
>
>
> Trong đó ta muốn classify đồng thời predict một bounding box quanh
> object.
>
>
>
> Bài toán này khác với object detection ở chỗ: Ta **giả định rằng  mình đã
> biết trước là sẽ có một hoặc vài object trong image** mà mình cần
> classify cũng như vẽ bounding box.
>
> the distinction here between this and object detection is that in the
> localization scenario **you assume ahead of time that you know there's
> exactly one object in the image that you're looking for** or **maybe more
> than one** but you **know ahead of time** that we're going to make some
> classification decision about this image and we're going to produce
> exactly one bounding box that's going to tell us where that object is
> located in the image

<br>

<a id="node-nu4qtq0"></a>

<p align="center"><kbd><img src="assets/8awlmv8nau.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là trong bài toán này, ta cũng tận dụng phần lớn một classification
> model như đã biết tới giờ (ý nói, những bài toán mở rộng từ bài toán gốc 
> classification đều kiểu như có thể giải quyết bằng cách chỉnh sửa đôi chút
> các mô hình classification)
>
>
>
> Cụ thể ở đây, output qua CNN, mà last layer cho ra một vector ví dụ như ở
> đây là fc7 của VGG16, cho ra vector 4096 unit, thì như bài toán classification
> nó sẽ qua một linear layer output ra 1000 class scores. Thì ở đây, nó sẽ cho
> qua thêm một linear layer nữa map nó với 4 scalar của bounding box.
>
>
>
> Tức là nó sẽ có 2 output. Và ứng với output 1 dùng cross entropy loss như
> cũ. Còn với output 2 thì dùng L2 loss (chính là MSE) hay L1 loss (MAE) của
> bài toán regression.

<br>

<a id="node-ooyvlaz"></a>

<p align="center"><kbd><img src="assets/8m1iewy4ktb.png" width="80%"></kbd></p>

> [!NOTE]
> câu hỏi là: Liệu làm như vậy, bắt model predict cùng lúc class và bounding 
> box liệu có hiệu quả không. 
>
>
>
> Justin: Đại khái là đây là một cách làm mà có thể mang lại hiệu quả nhất 
> định. Tuy nhiên người ta có thể làm cho nó phức tạp hơn một chút ví dụ
> như thay vì chỉ predict ra một bounding box, người ta cho predict ra mỗi
> class một bounding box, và chỉ apply loss đối với bounding box tương ứng
> với correct class. Và nó thể mang lại hiệu quả hơn

<br>

<a id="node-aoot5ml"></a>

<p align="center"><kbd><img src="assets/n4v154n44i.png" width="80%"></kbd></p>

> [!NOTE]
> câu hỏi khác đại khái là bây giờ có 2 loss, có khi nào gradient của một cái
> dominate cái kia không (giống như một cái có giá trị lớn khiến model chỉ
> ưu tiên cái đó mà phớt lờ cái kia)
>
>
>
> Justin: Đúng vậy, nên ta sẽ có kiểu như các trọng số như một dạng h.p 
> để weighted sum hai cái loss này. Tuy nhiên vì h.p này có thể trực tiếp
> thay đổi loss nên việc chọn ra weight khá là khó khăn.
>
>
>
> Nên giải pháp Justin đề nghị là dùng một metric khác mà ta quan tâm
> trong quá trình cross validation để chọn weight thay vì dùng validation loss.

<br>

<a id="node-j6lwah8"></a>

<p align="center"><kbd><img src="assets/r053xjbvh8.png" width="80%"></kbd></p>

> [!NOTE]
> câu hỏi khác đại khái là tại sao không fixed một cnn rồi train hai fc layer
> riêng lẻ cho hai đầu ra (classification và bounding box)
>
>
>
> Justin: Thật ra có người làm vậy, và đó cũng là thứ mà bạn nên thử khi gặp
> tình huống này. Tuy nhiên, nói qua của transfer learning thì có một nguyên
> tắc chung là, ta sẽ thu được hiệu quả cao hơn nếu như có thể train cả
> system (ý nói, train lại pretrained layer với các điều chỉnh cho bài toán mới).
> Và cách làm thường được cho là có hiệu quả tốt đó là ta sẽ freeze các
> pretrained layer và train các new layer cho đến khi converge. Sau đó
> unfreeze các pretrained layer và train tiếp cả hệ thống
>
> Yeah, so the question is why don't we fix the big network and then just only
> learn separate fully connected layers for these two tasks? People do do that
> sometimes and in fact that's probably the first thing you should try if you're
> faced with a situation like this but in general whenever you're doing transfer
> learning 38:54 you always get better performance if you fine tune the whole
> system jointly because there's probably some mismatch between the
> features, if you train on ImageNet and then you use that network for your
> data set you're going to get better performance on your data set if you can
> also change the network. 39:09 But one trick you might see in practice
> sometimes is that you might freeze that network then train those two things
> separately until convergence and then after they converge then you go back
> and jointly fine tune the whole system. So that's a trick that sometimes
> people do in practice in that situation.

<br>

<a id="node-5jmkfe6"></a>

<p align="center"><kbd><img src="assets/4xr5iqbzhow.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/t87wqo0v3ms.png" width="80%"></kbd></p>

> [!NOTE]
> mở rộng ra, ta hoàn toàn có thể làm các bài toán tương tự như Human
> Pose Estimation. Trong đó ta sẽ dự đoán các vị trí của các pose
>
>
>
> Và có thể thấy trong bài toan này chỉ dùng regression loss.

<br>

<a id="node-ialxa2w"></a>

## Object Detection

<br>

<a id="node-7ak10l8"></a>

### (slow) R-cnn

<br>

<a id="node-kouqr0e"></a>

<p align="center"><kbd><img src="assets/i44snhn2l5p.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, như đã nói classification + localization là khi ta đã biết trước có mấy loại
> Nhưng quan trọng là trong mỗi bức hình ta biết trước sẽ có 1 hoặc 2
> hoặc 3 con. Và ta muốn phân loại con nào là con gì và vẽ bounding box.
>
>
>
> Còn object detection tuy ta cũng có một bộ các class nhưng trong mỗi image
> ta không biết sẽ có mấy con. Nhiệm vụ của model sẽ là, cứ mỗi một con xuất
> hiện trong hình thì vẽ bounding box và classify nó là con gì.

<br>

<a id="node-uy54ocd"></a>

<p align="center"><kbd><img src="assets/hoids1ks1l.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là O.D đòi hỏi khó hơn Image Classification khi có nhiều
> output, và nhiều loại output cũng như phải xử lý large images

<br>

<a id="node-jk0f803"></a>

<p align="center"><kbd><img src="assets/8rsyi3q95k5.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là object detection là core task của computer vision nên người
> ta  theo dõi hiệu suất của nó rất sát. Biểu đồ cho thấy trước khi áp dụng
> Deep Learning thì hiệu suất của của các model chững lại 2012. Sau khi
> dùng Deep learning thì tăng tốc và ngày nay người ta cho rằng bộ
> dataset PASCAL VOC đã trở nên quá dễ với deep learning.

<br>

<a id="node-5xqoq92"></a>

<p align="center"><kbd><img src="assets/brxf28nfr3d.png" width="80%"></kbd></p>

> [!NOTE]
> như đã nói, khác với localization, trong bài toán detection, ta ko biết
> số object sẽ có thể có trong image. Nên mỗi image khác nhau số
> lượng output.

<br>

<a id="node-5jke7ey"></a>

<p align="center"><kbd><img src="assets/y9rqz1ypvna.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/7ccofuv4246.png" width="80%"></kbd></p>

> [!NOTE]
> một cách tiếp cận cho bài toán detection là dùng sliding window.
> đại ý là ta crop image và pass nó qua cnn, để classify background
> hay cat hay dog. Và mỗi lần slide window là ta lại làm vậy với crop
> image đó.

<br>

<a id="node-6fw7bt5"></a>

<p align="center"><kbd><img src="assets/uym3iisqgdi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/y941tjcf8d.png" width="80%"></kbd></p>

> [!NOTE]
> vấn đề của cách tiếp cận này là ko biết phải chọn size ntn cho window
> cả. Vì có thể có rất nhiều object xuất hiện với đủ mọi kích cỡ. Do đó
> cách này không hiệu quả.

<br>

<a id="node-svbyofe"></a>

<p align="center"><kbd><img src="assets/xa9xkz0r66s.png" width="80%"></kbd></p>

> [!NOTE]
> ý tưởng của Region Proposal đại khái là ta có thể **process cái image** để
> rồi (dựa trên thuật toán) **xác định được một đường viền đóng kín** từ đó
> **đề xuất một bounding box**. Để rồi ta sẽ **có khoảng 1000-2000 box**, để
> mà **check những bounding box này bởi một classification + localization
> cnn** để **xem có phải là có object hay ko** (thay vì với sliding window thì
> như đoán mò)
>
>
>
> cách làm này ko hẳn thuộc về deep learning mà là **traditional computer
> vision technique**.
>
>
>
> Cách làm này được cho là **tuy "propose" ra nhiều window không có
> object** **nhưng recall cao**, tức nếu **có object thì hầu như nó đều
> propose**.
>
>
>
> Chạy cũng nhanh.

<br>

<a id="node-p7pet6o"></a>

<p align="center"><kbd><img src="assets/t436ugsxbr.png" width="80%"></kbd></p>

> [!NOTE]
> đó chính xác là cơ chế của **R-CNN (Region-based CNN)** Trong đó đầu
> tiên **cái hình được xử lý qua một thuật toán Region Proposal** để
> **propose ra những box tiềm năng**
>
>
>
> Sau đó, chúng sẽ **được thay đổi kích thước** để phù hợp với input size
> mà classification & localization cnn yêu cầu.
>
>
>
> Để rồi sau khi forward qua CNN ta sẽ có **predicted class** cũng như
> **bounding box**. Hình ảnh minh họa đại ý là với các region tiềm năng, ta
> mới pass qua Conv-Net để dự đoán ra
>
>
>
> 1. **Classification head**: Dự đoán class
>
>
>
> 2. **B.box regression head**: Dự đoán "vị trí" chính xác của b.box có thể
> dưới dạng khoảng cách từ các cạnh của region tới cạnh tương ứng của
> box. Ý nghĩa của từ "regression" là vậy - thu nhỏ sai lệch giữa giá trị dự
> đoán (ví dụ tọa độ / vị trí 4 cạnh của region
> - vốn dĩ đóng vai trò là predicted box) với tọa độ / vị trí thật sự của
> bounding box - ground truth box.
>
>
>
> Bổ sung sau khi làm assignment, ta đã hiểu box regression sẽ  predict
> deltas. Có thể khác nhau tùy mô hình cụ thể.
>
>
>
> Như với FCOS tức One-stage detector, nó sẽ là khoảng cách từ location
> center  tới 4 cạnh của bounding box, ta dùng nó để xác định tọa độ hai
> điểm Top-Left, Bottom-Right của bounding box.
>
>
>
> Còn với Faster R-CNN, thì trong stage 2, Region Proposal Network - RPN,
> nó  là tx, ty, tw, ty: Trong đó tx, ty nôm na là giá trị cần để "shift" (chuyển
> dịch) tâm của anchor box (cũng là của location) / tới tâm của bounding box,
> và tw, th là scale factor để scale width và height của anchor box để thành
> width & height của ground truth box. Còn ở stage 2, hiện tại lúc ghi  những
> dòng này là mình vừa xong RPN của part 2, review để chuẩn bị làm stage
> 2, cụ thể là hoàn thành module Faster R-CNN, mà ngoài ra người ta nói vì
> để cho đơn giản, sẽ không "làm BoxRegression" ở stage hai nơi mà nếu là
> phiên bản đầy đủ của Faster R-CNN thì sẽ có bước này để tiếp tục refine
> cái proposal region (output / predict từ RPN) một lần nữa. Nhưng dù không
> làm, ta cũng có thể hình dung nếu có làm thì nó cũng sẽ giống như việc
> match anchor box và ground truth box trong RPN: predict ra reg box deltas

<br>

<a id="node-ffn2hnd"></a>

<p align="center"><kbd><img src="assets/1b2cr6ovobl.png" width="80%"></kbd></p>

> [!NOTE]
> câu hỏi:
>
>
>
> ? Region Proposal **có "learnable" không?**
>
>
>
> -> Không, nó kiểu như là một thuật toán **fixed**, nhưng tí nữa ta sẽ thấy có thể
> thay đổi điều này, làm cho nó **learnable**.
>
>
>
> ? Predicted bounding box **có luôn nằm trong proposed region không**?
>
>
>
> -> Không, kiểu như CNN model có thể predict rằng à đây là một người mà
> propose region lại chỉ có phần thân, thì model hoàn toàn có thể predict
> bounding box ở ngoài phạm vi của propose region.
>
>
>
> ? Có những propose region không có object thì sao?
>
>
>
> -> ta luôn có một class = background để predict cho những vùng ko có
> object.
>
>
>
> ? Dataset sẽ ntn: Mỗi image sẽ đều có bounding box với label

<br>

<a id="node-mdtflot"></a>

<p align="center"><kbd><img src="assets/d1jjq7ejg17.png" width="80%"></kbd></p>

> [!NOTE]
> rồi ở đây (như hình ảnh cho thấy vẫn đang trong Slow RCNN), ta sẽ nói về
> box regression
>
>
>
> **Proposal region output từ thuật toán Region Proposal** (fixed) sau đó sẽ
> được **map với ground truth box** qua box regression head **để train một 
> transformation**, đại khái là kiểu như **cho model học cách sửa lại / tinh 
> chỉnh lại proposal region**.
>
>
>
> ====
>
>
>
> Ví dụ **region proposed là có center là px, py, dài rộng là ph, pw**. Thì
> model sẽ dựa vào label - cái correct bounding box để **learn một Transform
> tx, ty, th, tw** mang **ý nghĩa là cần chỉnh lại cái region proposed** với các
> giá trị như vậy. Để rồi cái bounding box sẽ là bx, by, bh, bw.
>
>
>
> Cái ý **translate relative to box size**: **bx = px + pw.tx** có nghĩa là **nếu tx = 0, thì
> có ý nghĩa là vị trí của proposed box đã ok**, không cần chỉnh gì thêm. Còn
> nếu tx = 1  thì px (center của box) phải được điều chỉnh một khoảng bằng 1
> x chiều rộng của propose box.
>
>
>
> Hiểu tạm như vậy có thể vào assignment hoặc đọc paper ta sẽ thấy rõ hơn.

<br>

<a id="node-dy0t1i7"></a>

<p align="center"><kbd><img src="assets/v8tsodvr1vs.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/imtysu25s1e.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hs9pshpn8q.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/pl06t8cqgli.png" width="80%"></kbd></p>

> [!NOTE]
> cũng dễ hiểu thôi, trong mấy slide này định nghĩa cách transform từ
> anchor box (có dạng center x, center y, width, height)  và prediction của
> model (là phép transform quy định bởi tx, ty, tw, th)  để tính ra predicted
> box. (dưới dạng center x, center y, width, height)
>
>
>
> Ta sẽ dựa vào đây mà xây dựng công thức từ anchor box, và ground truth
> box để tính ra tx, ty, tw, th.
>
>
>
> Có điều trong function ta làm việc với anchor box có dạng XYXY  tức là
> x1, y1, x2, y2. Và gt box cũng vậy. Nên mình cần chuyển nó sang "dạng"
> (center x, center y, width, height) để tính.
>
>
>
> có thể hiểu model predict ra một phép transform để mà "biến đổi" một 
> anchor box thành một object box. Việc biến đổi này bao gồm 
>
>
>
> 1: là shift cái center của anchor box sang vị trí của "object" box. Và 
>
>
>
> 2: scale kích thước của anchor box để được object box. Mà trong công thức
> có exponential là mục đích để scaling factor luôn dương.
>
> Trong đây có thể hiểu ý họ nói là sở dĩ ta "thiết kế" như vậy (tức là để cho
> model learn  một phép transformation shift & scale) là vì nó có tính chất
> invariance, ý là model không biết/không thấy giá trị mang tính tuyệt đối
> của các box và gt box, nên nó không thể học không thể predict ra vị trí
> chính xác của object box, thay vào đó, nó sẽ học một quan hệ tương đối
> giữa anchor box và object box để rồi từ đó có ý nghĩa như là với một
> anchor box (có vai trò như một region proposal ban đầu / nháp) thì nó sẽ
> biết cách "sửa" lại để tạo thành một region proposal chính xác
>
> Với việc học ra phép transformation thì nếu 'predicted' transform = 0 thì tức
> là model thấy rằng không cần sửa cái "initial proposal region" (tức là cái anchor
> box) mà nó đã chính là cái output / cái proposal region chuẩn rồi.
>
> Và từ các công thức này ta có thể có công thức của phép biến đổi nếu có
> anchor box (proposal) và ground truth box (target output). Dùng nó cho việc
> hoàn thành function này

<br>

<a id="node-wanptio"></a>

<p align="center"><kbd><img src="assets/p88hf8u0u0j.png" width="80%"></kbd></p>

> [!NOTE]
> nói về lúc test,
>
>
>
> 1. Đưa image vô, region proposal layer sẽ propose các box.
>
>
>
> 2. Chúng sẽ được resize để thành kích thước yêu cầu để **pass qua cnn để
> predict class scores đồng thời predict bbox transform.**
>
>
>
> 3. Đại khái là với (say) 2000 cái bbox mỗi cái có một list các  predicted
> classes scores đó. thì đương nhiên ta phải chọn ra một vài cái để xài (ở
> downstream task) chứ không thể dùng hết được.
>
>
>
> Vậy thì có nhiều cách để chọn, ví dụ như có thể làm theo kiểu  yêu cầu bao
> nhiêu 10 object đó, lúc này ta sẽ threshold on background: tức là ta sẽ chọn
> 10 (hay bao nhiêu đó thì tùy) bbox  mà predicted class scores ứng với
> background là nhỏ nhất (có thể hình dung cách làm này là chọn 10 b.box mà
> khả năng có  object là cao nhất)
>
>
>
> Hoặc threshold on per-category, đại khái là chọn bbox mà probability score
> ứng với 1 class nào đó cao hơn threshold.
>
>
>
> ===
>
>
>
> Trong hình đương nhiên là ta hiểu rằng chỉ có một cnn xử lý hết mọi region
> proposal box nhé

<br>

<a id="node-f60gpdi"></a>

<p align="center"><kbd><img src="assets/s3c456adab.png" width="80%"></kbd></p>

> [!NOTE]
> Nhưng R-CNN có nhiều hạn chế như rất chậm cả training và
> inference và tốn memory. Rồi nó cũng dựa trên thuật toán region
> proposal fix, không learnable, cũng là một hạn chế.
>
>
>
> Justin nói về tốc độ thì quá trình inference một bức hình có khi
> tốn cả mấy chục phút / 1 tấm vì cnn phải forward hàng ngàn region.

<br>

<a id="node-7swf9nn"></a>

### Fast R-cnn

<br>

<a id="node-yd7lqxp"></a>

<p align="center"><kbd><img src="assets/ys21sehz4k.png" width="80%"></kbd></p>

> [!NOTE]
> cái Fast R-CNN cải tiến một chút, khắc phục nhược điểm chậm của
> R-CNN. Bằng cách **xử lý bức hình gốc bằng CNN trước**, rồi mới dùng
> region proposal algorithm để propose ra các "region of interest" (kiểu như
> những vùng mà nghi ngờ có object) "trên" feature map của CNN. Và việc
> này nên hiểu là không phải là ta "chạy" thuật toán Region Proposal trên /
> từ feature map, mà là ta project những proposed region từ raw image lên
> feature map. Có nghĩa là, ta sẽ luôn bắt đầu với việc chạy thuật toán RP
> trên raw image như một bước chuẩn bị, rồi với "Slow" RCNN thì ta pass
> các region này qua CNN như đã nói, còn với Fast RCNN thì ta kiểu như
> tạm để các region đó đã, forward raw image qua CNN trước, sau đó mới
> project các proposed region lên các feature map)
>
>
>
> Sau đó, vì vẫn phải **input vào một fixed size fc layer** nên các region sẽ
> được **resize** nhờ một layer gọi là **RoI Pooling**. RoI pooling nói ở
> phần dưới (Đi theo mũi tên)
>
>
>
> Sau đó qua **fc layer, classification head** (head ý là output layer) để cho
> ra **class  scores** và box regression head để có bounding box.
>
>
>
> Để rồi tính log loss (classification) và l1 loss (regression - bounding box)
> và gradient backprop để learn model param

**🔗 See also:** [linked note](#node-0c6np1a)

<br>

<a id="node-6nfl9s6"></a>

<p align="center"><kbd><img src="assets/j54cx5f5zzh.png" width="80%"></kbd></p>

<br>

<a id="node-51uut2t"></a>

<p align="center"><kbd><img src="assets/dy6pisyf02t.png" width="80%"></kbd></p>

> [!NOTE]
> So sánh với EECS 498-007, ý tưởng cũng vậy, chỉ biết thêm cái CNN mà
> ta sẽ **process raw image gọi là backbone network**, nó đương nhiên là
> một **pretrained - CNN** mà ta đã biết như AlexNet, VGG, ResNet.
>
>
>
> Sau đó, như cs231n (slide trước) **thuật toán Region Proposal như
> Selective Search sẽ được apply với output của CNN** = feature maps thay
> vì raw images
>
>
>
> Tiếp, chỗ này khác với cs231n trong đó proposed region sẽ pass qua một
> **ROI Pooling** rồi **FCs** để ra class **scores** và **bbox regressor** (tức
> là ra luôn predicted location của bbox)
>
>
>
> Thì ở đây ta sau khi qua **ROI Pooling** thì sẽ đến các **"tiny lightweight per
> region network"** để output ra **class scores** và **bbox transform - dùng
> để transform các propose box để có được predicted box**

<br>

<a id="node-i40vub5"></a>

<p align="center"><kbd><img src="assets/x0gku52jg0a.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là với cải tiến này nó sẽ rất nhanh, khi phần lớn sự tính toán đã được
> share trong backbone network nhờ đó giảm số lượng công việc của Region
> Proposal (RoI)

<br>

<a id="node-ylzvmlv"></a>

<p align="center"><kbd><img src="assets/ef7gm2394q.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6tfq7mo2dnv.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là nếu dùng AlexNet thì backbone sẽ là phần conv layers, và khúc
> Per-Region Network là phần đuôi gồm hai cái FC layer của ResNet
>
>
>
> Còn nếu là ResNet thì backbone cũng là khúc "đầu-mình", khúc đuôi
> với các layer cuối sẽ được dùng làm Per-Region network.
>
>
>
> Vậy **ý nói mọi khúc tính toán nhiều được xử lý lúc đầu với backbon**e,
> còn **các region dù nhiều chỉ cần pass qua các khúc đuôi vốn xử lý rất
> nhanh.**

<br>

<a id="node-r6dmgpn"></a>

<p align="center"><kbd><img src="assets/wdq0n0z1l6.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, thế thì một vấn đề nữa là cái phần Region of Interest này, trong đó **project ra
> các proposed region trên raw image lên CNN feature map** rồi  sau đó **crop +
> resize** (RoI pooling) để thành **fixed size theo yêu cầu của phần Per-Region
> network**.
>
>
>
> Vậy vì ta cần gradient backward về cả backbone CNN nên ta muốn khúc này
> **differentiable**.

<br>

<a id="node-sl46adm"></a>

<p align="center"><kbd><img src="assets/4f4gjreb2bl.png" width="80%"></kbd></p>

> [!NOTE]
> về cái ROI, justin bỏ qua sẽ quay lại saU, đại khái là
> nó cũng **giống giống như max pooling**

<br>

<a id="node-jrzd7x1"></a>

<p align="center"><kbd><img src="assets/ojabtudfs6.png" width="80%"></kbd></p>

> [!NOTE]
> So sánh hiệu suất của các model, SPP-Net (Justin ko nói nó là gì)  cho
> thấy Fast R-CNN rất nhanh, đến nỗi bottleneck chỉ còn là ở khúc tính
> region proposal, ý là chỉ mất thời gian chỗ này, chứ có region rồi thì
> Inference qua cnn rất nhanh.

<br>

<a id="node-6ziik3d"></a>

### Faster R-cnn = Train Rpn

<br>

<a id="node-dmpfyps"></a>

<p align="center"><kbd><img src="assets/xq2wtks59bf.png" width="80%"></kbd></p>

> [!NOTE]
> giải pháp khắc phục bottleneck này, Faster R-CNN **cho model tự học bước
> region proposal** luôn thay vì dùng một fixed algorithm.
>
>
>
> Từ raw image, qua CNN để có feature map, tới đây nó sẽ được một
> Region Proposal Network (có thể hiểu nó là một CNN con nằm trong
> CNN mẹ) predict ra các region cũng như là predict region đó có phải là
> object hay không.
>
>
>
> Sau đó predicted region lại được đi tiếp qua các bước tiếp theo như cũ.
>
>
>
> Như vậy thì có thể thấy nó có 4 losses như trong slide đã list ra, và việc
> cân bằng các loss này là một thách thức.

<br>

<a id="node-ojgzp0o"></a>

<p align="center"><kbd><img src="assets/qf1abiiyk6.png" width="80%"></kbd></p>

> [!NOTE]
> câu hỏi là làm sao để train cái Region Proposal Network khi ta không có
> ground truth label
>
>
>
> -> Cái này hơi rườm rà và có thể ta sẽ nói sau
>
>
>
> Classification loss của RPN là gì:
>
>
>
> -> Binary classification loss, vì RPN sẽ phải predict region phải hay không
> phải là object

<br>

<a id="node-cem68xi"></a>

<p align="center"><kbd><img src="assets/7x1ek95tio9.png" width="80%"></kbd></p>

> [!NOTE]
> Faster R-CNN rất nhanh. 
>
>
>
> và vì nó có cơ chế Region Proposal learnable nên nó đã khắc phục được
> một nhược điểm hồi nãy có nói là fixed region proposal algorithm
>
>
>
> và nó gọi là một họ các model dựa trên proposal region gọi là reigon-based 
> model

<br>

<a id="node-5qpw2ek"></a>

<p align="center"><kbd><img src="assets/g166jgc7gad.png" width="80%"></kbd></p>

> [!NOTE]
> cs231n thì không nói, nhưng EECS 498 thì có nói về việc train Region
> Proposal Network. như đã nói hồi nãy, mỗi vị trí trên feature map sẽ tương
> ứng với một vị trí của raw image. Tất nhiên spatial size của feature map
> nhỏ hơn.

<br>

<a id="node-q1z9llq"></a>

<p align="center"><kbd><img src="assets/kshuuc5z0po.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì, đại khái là RPN sẽ được train để predict **một fixed-size
> anchor box** (với center là một vị trí trên feature map) **xem nó có
> chứa một object hay là không**. (Binary classification)
>
>
>
> Đương nhiên là có thể output (với mỗi vị trí trên feature map) ra 2
> score ứng với 2 class - positive / negative để dùng softmax. Hoặc
> output ra 1 con số p(y=1) như bài toán logistic regression.

<br>

<a id="node-8165ugn"></a>

<p align="center"><kbd><img src="assets/0mxp92w7q3qe.png" width="80%"></kbd></p>

> [!NOTE]
> ví dụ cái anchor box xanh lá cây thì True, mấy cái khác thì False. Cho
> nên output có thể dùng một 1x1 conv để xuất ra một matrix cùng spatial
> size chứa các score Positive / Negative

<br>

<a id="node-ljf7xf4"></a>

<p align="center"><kbd><img src="assets/eee82wbgkkp.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì tất nhiên cái fixed size anchor box sẽ không đủ để đảm bảo tạo ra các
> bounding box đúng. Do đó **RPN còn learn ra BBox transform** giống như hồi
> đầu đã biết. Dùng regression loss. Để rồi ví dụ như trong hình, RPN predict ra
> rằng một anchor box có chứa object, thì cộng với **predicted bbox transform,**
>  nó sẽ **'adjust' anchor box** **để ra được object bounding box** (màu vàng)
>
>
>
> Ở đây chưa nói dùng cái target như thế nào để train cái regression loss này,
> nhưng sau khi làm part 2 assignment thì ta hiểu, đương nhiên là dùng cái
> ground truth box để làm target, nhưng phải có bước "gán": Và hiểu cách ngắn
> gọn là, nếu muốn (huấn luyện) model dự đoán ra cách transform một anchor
> box thành ra ground truth box, thì với một anchor box, và ground truth box, thì
> các thông số để transform là gì, thì việc deltas đó (tính từ anchor box và gt
> box) sẽ chính là target cho việc training box regression head của RPN

<br>

<a id="node-emlqqe7"></a>

<p align="center"><kbd><img src="assets/rxvf1vtb63.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì người ta thấy rằng **một anchor box không đủ hiệu quả** từ đó người
> ta **dùng K anchor box khác nhau**. Thành ra RPN sẽ output ra K*W*H
> probability score và 4k*W*H box transform.
>
>
>
> (Tại mỗi vị trí trên feature map có K anchor box (size khác nhau, mỗi cái
> cần predict một probability (có object) score nên W*H vị trí),  sẽ là W*H*K
> prob score)
>
>
>
> Và các anchor box size, K, đều là hyperparameter

<br>

<a id="node-n1j3x43"></a>

<p align="center"><kbd><img src="assets/paaxr5gbyt.png" width="80%"></kbd></p>

> [!NOTE]
> tổng hợp lại train cả hệ thống sẽ có **4 loại losses**:
>
>
>
> Đầu tiên là hai loại loss khi train RPN: một là mỗi anchor box  predict **có
> phải hay không là object** -> binary cross entropy loss.
>
>
>
> Mỗi anchor **box transform map anchor box với ground truth box ->
> regression loss.**
>
>
>
> Sau đó output của RPN sẽ pass qua phần còn lại để ra final prediction dự
> đoán **object thuộc loại gì (multi-class classification loss)** và **vị trí chính
> xác của bbox (regression loss) (cái này cũng mang ý nghĩa là refine** thêm
> một lần nữa predicted region từ RPN: map predicted region từ RPN với
> ground truth box
>
>
>
> Nếu không muốn, ta có thể dùng chính predicted region từ RPN làm final
> bounding box (giống như trong assignment vì lí do hạn chế tính toán của
> Colab). Hãy nhớ và để ý rằng Region Proposal Network predict ra propose
> region thì nó cũng là cái bounding box rồi.
>
>
>
> Đó là Justin còn chưa nói về vài thứ râu ria vì ko đủ thời gian, nên object
> detection là một bài toán phức tạp

<br>

<a id="node-g53gulg"></a>

<p align="center"><kbd><img src="assets/axj78g3p21d.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì Faster R-CNN còn gọi là **2-stage object detector**, khi stage 1 là "xử
> lý" (**MỘT)** bức ảnh gốc thông qua backbone CNN, và sau đó là Region
> Proposal Network để ra các predicted / proposed region/box.
>
>
>
> Còn stage 2 là pass **MỖI** proposal region qua RoI pool / align + Predict
> object class và (có thể) refine bbox một lần nữa

<br>

<a id="node-1nhji2n"></a>

### Training Slow /  Fast/ Faster R-cnn

<br>

<a id="node-z1n9237"></a>

<p align="center"><kbd><img src="assets/3f99g9f5dek.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là trong lecture này Justin sẽ nói rõ hơn về quá trình training
> vốn nói rất ít ở cả cs231n và lecture 15 EECS 498-007/598-005)
>
>
>
> Đầu tiên, những ô màu green là ground-true box, màu cyan là proposal
> region bởi thuật toán như Region Proposal như Selective Search

<br>

<a id="node-hfh1gfs"></a>

<p align="center"><kbd><img src="assets/wcdbsqetvai.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là ta sẽ phân loại các proposal region (P.R) dựa trên một threshold
> IoU nào đó với các ground truth (G.T) để xếp loại là Positive khi P.R cover
> khá tốt một g.t box, ngược lại ko overlap nhiều với G.T như cái ngoài góc
> thì xếp là negative còn không tốt cũng ko đến nỗi tệ như cái proposed box
> bao cái mặt con chó thì classify là Neutral

<br>

<a id="node-iapxgxn"></a>

<p align="center"><kbd><img src="assets/gs0x2nmb1pa.png" width="80%"></kbd></p>

> [!NOTE]
> Với những cái propose region đó ta sẽ bỏ qua các Neutral region, chỉ dùng
> những cái positive và negative để mà training.
>
>
>
> Với các positive region, target của nó sẽ là category đúng (cho biết bởi cái
> ground truth bbox tương ứng mà cái region có IoU lớn hơn threshold)  còn cái
> negative thì target sẽ là Background class
>
>
>
> Đây cũng là câu hỏi của 1 người học target class của region lấy ở đâu, thì
> chính là lúc ta xác định xem nó (một propose region) overlap với cái g.t box
> nào để gán nó là positive thì cũng sẽ cho biết target class của nó sẽ là gì. Vậy
> **trước khi ta bắt đầu training, ta sẽ run training set qua region proposal để có
> các regions, rồi làm cái bước classify thành positive / negative / neutral và
> chuẩn bị các target các kiểu. Justin nói rằng ta sẽ run offline quá trình này
> trước khi training.**
>
>
>
> Nhưng đó là với (Slow) R-CNN, nơi ta chỉ dùng fixed region proposal
> algorithm, còn với Fast R-CNN khi ta train luôn cả cái này tức là Region
> Proposal Network thì ta phải đại khái là làm cái bước preparation này online
> - ý là trong lúc training luôn.Cái thứ hai là ta cũng train một bbox transform (nhớ ko), thế thì target sẽ
> đương nhiên là cái ground truth box. Để rồi model sẽ phải h**ọc ra cách adjust
> propose box (bởi Region Proposal algorithm)** bởi bbox transform để có được
> cái "final" predicted bbox..
>
>
>
> Một ý nữa là với negative region thì target bbox sẽ là none. Điều này sẽ khiến
> việc tính loss trở nên hơi rắc rối khi một số sample (region) thì lại có regression
> loss, một số thì không. Và tỉ lệ positive/negative cũng là một h.p cần tuning.
>
> Và có thể hiểu rằng CNN không thật sự (học cách) generate / inventing cái bbox
> mà thật ra nó học cách adjusting cái box được propose bởi Regional Proposal.
>
>
>
> Và cũng vì vậy mà lúc testing, ta expect rằng ta dùng cùng cái thuật toán R.P
> mà lúc training ta xài, để rồi dùng cái bbox transform predict bởi CNN để adjust
> cái region. 
>
>
>
> Điều này trực tiếp dẫn đến là nếu lúc test ta dùng một thuật toán R.P khác thì
> model sẽ fail. Điều này cũng dễ hiểu khi liên hệ tới nguyên tắc quan trọng trong
> ML là data statistic của training set và test set phải giống nhau, cũng như yêu cầu
> preprocessing phải giống nhau vậy

<br>

<a id="node-sf0umw6"></a>

<p align="center"><kbd><img src="assets/i8qqcyqbx5a.png" width="80%"></kbd></p>

> [!NOTE]
> Với Faster R-CNN thì như đã biết ta **chỉ đổi chỗ**: ta sẽ **process raw
> image** với **CNN trước**, **rồi mới chạy R.P algorithm trên feature map**.
> Nhưng sau đó thì  các bước tiếp theo như khúc mapping để phân loại region
> như vừa rồi đều giống nhau.

<br>

<a id="node-udmwgm7"></a>

<p align="center"><kbd><img src="assets/d74bv4y4pga.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, nói qua việc training cái Faster R-CNN, mà ta biết thay đổi chính là
> **train cái RPN để predict ra propose region** thay vì dùng thuật toán
> fixed như **Selective Search**.
>
>
>
> Vậy đầu tiên, Justin cho rằng ta có thể hình dung cái này nó giống như
> việc ta **transform các anchor box** (mà như trong single-stage detector,
> mỗi vị trí của feature map sẽ có K cái anchor box với size fix, là một
> dạng h.p) thành region proposal. Ta hiểu đại ý là bởi vì ta đã nói là sẽ
> train cái RPN là cái sẽ làm thay việc của một Region Proposal mà.
>
>
>
> Và trong **stage 2 thì ta sẽ transform cái region proposal thành ra final
> output object box**

<br>

<a id="node-61j8sxp"></a>

<p align="center"><kbd><img src="assets/629ksy3j5ed.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì ta cũng làm cái bước **pairing** như hồi nãy, với từng anchor-box ta
> sẽ gán nó là **positive / negative / neutral dựa vào IoU với một ground  truth
> box**.
>
>
>
> Và sau đó ta cũng sẽ **chỉ quan tâm các positive & negative anchor box** và
> training RPN để **map từng anchor box với class target**. Và cái này thì
> không như hồi nãy khi ta map nó với target là class id. Ở đây thì chỉ map với
> binary  class True / False - có hay không object.
>
>
>
> Chỗ này chưa hiểu lắm, nếu đã xác định negative (do IoU của anchor box và
> ground truth box < threshold) thì đương nhiên target nó là false rồi còn
> ngược lại nếu đã là positive thì đương nhiên target nó sẽ là true (Ý nói, nội
> bản thân trạng thái pos / neg đã luôn tương đồng với target rồi). Nhưng có
> thể cũng chỉ là như vậy.
>
>
>
> Rồi, ở second stage thì cũng vẫn giống của Slow R-CNN, có điều như đã nói
> hồi này, chỉ khác là ta sẽ pair giữa cái propose region mà spit out bởi RPN
> với ground truth box. Những cái này sẽ rõ hơn khi **ta làm assignment 4**

**🔗 See also:** [linked note](./eecs_498_007598_005_2022_assignment_4_part_2_two_stage_detector.md#node-wvs5g6n)

<br>

<a id="node-u3cx2y1"></a>

<p align="center"><kbd><img src="assets/pxg63y1174.png" width="80%"></kbd></p>

> [!NOTE]
> Review lại một chút, với R-CNN, Region Proposal algorithm được áp
> dụng đối với raw image, sau đó, các region proposed mới được xử lý bởi
> CNN khiến nó rất chậm.
>
>
>
> Vậy thì Fast R-CNN thay đổi bằng cách đổi chỗ CNN và R.Proposal để
> dùng CNN xử lý raw image trước, rồi mới apply region proposal  trên
> feature map output từ CNN

<br>

<a id="node-j6nomu7"></a>

### Single Stage
detetor

<br>

<a id="node-w3zu4hr"></a>

<p align="center"><kbd><img src="assets/5xaaqm1axsq.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy thì người ta thấy rằng không cần phải có stage 2 làm gì, mà hoàn toàn có
> thể nhờ stage 1 làm hết. Bằng cách, **thay vì train RPN để predict một bài
> toán binary cho có hoặc không có object**, thì có thể **train nó luôn bài toán
> multi-class để nó predict class gì luôn**. Khi đó RPN từ việc output K*W*H tức
> với mỗi vị trí trên feature map (sẽ có K anchor box) cần dự đoán ra K chỉ số
> p(có object) thì bây giờ với mỗi box sẽ predict C class scores -> C*K*W*H.
>
>
>
> Và thật ra là có 1 class là background nữa nên là **(C+1)*K*W*H.**

<br>

<a id="node-gbgqk2p"></a>

<p align="center"><kbd><img src="assets/n0pcytv55o.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, còn với bbox transform, thì người ta thấy rằng **predict với mỗi class
> một transform khác nhau sẽ hiệu qủa hơn**. Nên từ việc output ra **4*K*W*H
> (mỗi box một bộ 4 giá trị transform)** thì bây giờ **mỗi box sẽ có C*4 giá trị
> transform -> C*4K*W*H**
>
>
>
> Thì đây chính là **YOLO** thuộc về Single Stage Object Detection

<br>

<a id="node-g4ow1aa"></a>

<p align="center"><kbd><img src="assets/2705jzubuy2.png" width="80%"></kbd></p>

> [!NOTE]
> YOLO, đã học bên DLSpec. Đại khái là, chia image thành một grid ví dụ 7x7
> với mỗi grid-cell, chọn B ví dụ 3, (là một h.p) base box tâm tại cell center.
>
>
>
> Để rồi predict ra với mỗi based box một bộ số gồm có dx, dy, dh, dw, và
> confidence score c. Vậy model output sẽ là tensor 7x7x(5*B+C). Với C là số
> class.
>
>
>
> Label tạo kiểu gì thì Justin nói hơi hairy, nhưng có thể đoán rằng nó cũng sẽ là
> một tensor 7x7x(5*B+C) như vậy để **train cả hệ thống với một 'giant cnn'** 
> Và thật sự phân tích kĩ sẽ thấy R-CNN thật ra cũng có điểm tương đồng với
> YOLO.
>
> And by the way, the region proposal network that gets used in faster
> R-CNN ends up looking quite similar to these where they have some
> set of base bounding boxes over some gridded image, another region
> proposal network does some regression plus some classification. So
> there's kind of some overlapping ideas here.

<br>

<a id="node-4d6p4xv"></a>

<p align="center"><kbd><img src="assets/e1jrt0yr8ef.png" width="80%"></kbd></p>

> [!NOTE]
> và có thể thấy O.D có rất nhiều biến số, nào là dùng phương pháp nào
> Faster-CNN hay R-FCN (ko có thời gian để nói) hay SSD (Single Stage
> Detector). Rồi nào là dùng backbone model nào rồi các thông số kích
> thước như anchor size, ......Do đó rất khó để so sánh hai O.D với nhau
>
>
>
> Có một paper họ cố gắng thử tất cả và so sánh chúng, nên Justin
> recommend nên đọc qua

<br>

<a id="node-5nzev5w"></a>

<p align="center"><kbd><img src="assets/rigg236amx9.png" width="80%"></kbd></p>

> [!NOTE]
> tóm lại Object Detection có rất nhiều biến số (để thử, kiểu như h.p)
> như base cnn model nào, dùng Region-based RCNN hay YOLO
> và các thông số kích thước như image size, region proposal....
>
>
>
> Justin mới đề xuất nên tham khảo paper dưới đây để trong đó kiểu
> như người ta so sánh hiệu suất của việc thử các variable này
>
>
>
> Nhưng kinh nghiệm là region-based chính xác hơn nhưng chậm
> hơn yolo.

<br>

<a id="node-cj0j7pg"></a>

<p align="center"><kbd><img src="assets/b67yh97lcj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4te0pi1b1qd.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/e6zfnlopfbb.png" width="80%"></kbd></p>

<br>

<a id="node-ntniju5"></a>

<p align="center"><kbd><img src="assets/u18inzguvh.png" width="80%"></kbd></p>

> [!NOTE]
> kết quả của paper đó đại khái là 2-stage detector tend to work chính
> xác hơn nhưng chậm hơn

<br>

<a id="node-0q9mqro"></a>

<p align="center"><kbd><img src="assets/7f9pnhsp4hg.png" width="80%"></kbd></p>

> [!NOTE]
> còn Single-stage thì nhanh hơn
> nhưng bớt chính xác hơn

<br>

<a id="node-q48in2h"></a>

<p align="center"><kbd><img src="assets/8nktdnyitpi.png" width="80%"></kbd></p>

> [!NOTE]
> và backbone network càng mạnh thì performance cũng càng
> tốt nhưng lại càng chậm

<br>

<a id="node-h3gcgki"></a>

<p align="center"><kbd><img src="assets/7dkpeoj1bky.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/e44q8feegzg.png" width="80%"></kbd></p>

> [!NOTE]
> những slide sau đại khái là nói về các bước tiến bộ sau vài năm kể từ 
> khi paper trên. Với những cải tiến như dùng **Feature Pyramid Network**
> (Ko có thời gian để nói), train lâu hơn đã đẩy mAP lên cao hơn nữa
>
>
>
> Đồng thời One-stage detector cũng không còn thua kém về accuracy
> So với 2-stage

<br>

<a id="node-uiga7ge"></a>

<p align="center"><kbd><img src="assets/7awqmqz1qkb.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi model càng bự thì càng
> chính xác hơn nữa.

<br>

<a id="node-d5ntyqs"></a>

<p align="center"><kbd><img src="assets/lzbvzfsgt8.png" width="80%"></kbd></p>

<br>

<a id="node-d9m4q4y"></a>

<p align="center"><kbd><img src="assets/uatzpgbs3pj.png" width="80%"></kbd></p>

> [!NOTE]
> rồi với big ensemble, train với nhiều data hơn cộng với kĩ thuật
> TTA **test-time agumentation** mà gb.Howard có nói đến trong
> lecture 6 fastai đã giúp performance lên rất tốt

<br>

<a id="node-ov89smr"></a>

<p align="center"><kbd><img src="assets/ctgfc1fwqte.png" width="80%"></kbd></p>

> [!NOTE]
> nói chung Justin cho rằng trừ Assignment 4 nơi ta sẽ
> làm from scratch cái này còn lại thì đừng tự làm mà
> hãy dùng các api của TF hay PT

<br>

<a id="node-jfzo870"></a>

<p align="center"><kbd><img src="assets/6uugkdzrvg3.png" width="80%"></kbd></p>

<br>

<a id="node-5prsbjl"></a>

### Rol Pooling & Roi Aligned Pooling

<br>

<a id="node-0c6np1a"></a>

<p align="center"><kbd><img src="assets/otaz258syd.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái ý ổng nói là **vì mỗi vị trí (spatial size) của feature map đương nhiên
> phải tương ứng với một vị trí trên raw image**, nên ta có thể "proposed region"
> trên raw image, từ đó ta **project lên feature map để có cái bbox trên feature
> map** 
>
>
>
> Và vì **feature map nhỏ hơn (bề rộng bề ngang) của hình gốc** nên sau khi
> project **nó sẽ không khớp với grid cell**, do đó phải **snap** - tức là **"dịch
> nó, kéo dãn, ép" nó phải khớp với grid cell trên feature map**
>
>
>
> Từ đó đương nhiên **dẫn đến vấn đề đó là proposed region trên feature map**
> **không hoàn toàn align với proposed region (đã làm trên raw image)**.
>
>
>
> Vậy thì **tạm gác lại cái vấn đề này** (vì ta sẽ khắc phục nó bằng cái **RoI Align**)
> để nói tiếp về **cách thực hiện IoR pooling**:
>
>
>
> Thì đầu tiên, ta sẽ **chia proposed region thành các subregion**, ví dụ 2x2 để
> **thực hiện max pooling**, đương nhiên sẽ có những vùng không khớp để rồi nó
> thành 3x2 chẳng hạn nhưng ko sao. Tiếp, **apply max pooling trên những
> subregion đó** để mỗi vùng 2x2x512 (512 là depth) sẽ **trở thành 1x1x512** tức là
> một 'depth' vector như đã biết.
>
>
>
> Rồi, cái subregion 3x2x512 sau khi max pooling **cũng cho ra 1x1x512**. Thành
> ra **output của việc ta max pooling cái proposal region sẽ luôn có spatial size
> hình vuông** và từ đó (**bằng cách chọn 2x2 hay 3x3** hay 7x7 thì **output của RoI
> pooling sẽ có size phù hợp với yêu cầu kích thước của stage 2** - cái **cnn hay 
> fc layer**

**🔗 See also:** [linked note](#node-yd7lqxp)

<br>

<a id="node-bj8uw82"></a>

<p align="center"><kbd><img src="assets/q5m1lv54dwi.png" width="80%"></kbd></p>

> [!NOTE]
> vậy thì RoI Align giúp khắc phục vấn đề "mis-aligned"

<br>

<a id="node-kb458om"></a>

<p align="center"><kbd><img src="assets/sl1h04jlw39.png" width="80%"></kbd></p>

> [!NOTE]
> Bài trước ta đã biết "cách làm" sẽ là mình sẽ dùng region proposed kết
> quả của việc **dùng thuật toán region proposal** như **selective search** apply
> **trên raw image**. Sau đó ta sẽ **PROJECT** **nó lên feature map** output từ
> CNN.
>
>
>
> Sau đó, trong bước gọi là **RoI pool**, ta mới chia các "projected
> proposal region trên feature map" thành các vùng. Ví dụ 7x7 (và "xem
> xem" nó như 8x7) để **thực hiện max-pooling**, kết quả **là một output có
> spatial size vuông**, và theo kích thước mà stage 2 khúc cnn hay fc layer
> map với class scores yêu cầu.

<br>

<a id="node-knap5na"></a>

<p align="center"><kbd><img src="assets/l7h13ll1pc.png" width="80%"></kbd></p>

> [!NOTE]
> Justin nói về **vần đề của RoI pooling**, đầu tiên là vấn đề **misalignment**
> xuất phát từ nguyên nhân là cái bước "**snap**".
>
>
>
> Cái bước "snap" nói xuyên suốt trong lecture này và lecture trước có nghĩa
> là: Ta **dùng thuật toán region proposal trên raw image**, để **tính ra tọa độ
> của 4 điểm của region proposed**. Sau đó ta **mới project lên feature map**.
> Mà feature map thì **nó nhỏ hơn raw image**, nên phải " snap" tức là **gán**
> / **ép buộc cái "region phóng chiếu" phải khớp với grid cell.** Thì đương
> nhiên như Justin nói ở đây, nếu ta lấy tâm của cái region sau khi được snap
> mà **phóng chiếu (project) ngược lại lên raw image thì hai cái region sẽ
> không khớp**.
>
>
>
> Người ta đã minh họa trong slide, cái **khung màu xanh lá** kiểu như là cái
> **region propose mà thuật toán vẽ ra trên raw image**. Sau đó ta mới
> **project "lên" feature map** được cái "màu xanh lá trên feature map" thì đại
> khái là **có thể thấy nó không khớp với grid cell**.(Có thể hiểu điều này, hình
> dung grid cell trên raw image là 1 pixel, còn feature map thì nhỏ hơn raw
> image nên chiếu cái region xuống nó sẽ ko khớp hoàn toàn với grid cell của
> feature map).
>
>
>
> Vậy nên phải **snap**, **để cho nó khớp**, thành ra **cái khung xanh dương
> ở trên feature map**. Thì rõ ràng là **nó bị lệch xong với khung xanh lá**, nên
> **phóng chiếu khung xanh dương của feature map lên lại hình gốc thì cái
> region xanh dương sẽ không trùng với region xanh lục của image gốc**.
>
>
>
> ====
>
>
>
> **Vấn đề thứ hai** đại khái là **nếu ta coi bước này như một function** nhận
> **input** là **feature map**, và **box coordinate** (được project từ region
> proposed từ raw image) để có được "region feature" thì quá trình
> **backprop** ta **chỉ có thể tính gradient của image feature** chứ **ko thể tính
> gradient của box coordinate** được.
>
>
>
> Thành ra cách khắc phục là **dùng RoI aligned** mà lecture trước ko có thời
> gian nên Justin bỏ qua kêu tự tìm hiểu, tuy nhiên vì ta sẽ phải làm nó trong
> assignment 4 thành ra ổng sẽ nói ở đây
>
> seems a little bit weird with this ROI pool operation if it is also related to
> the snapping one one so one way to look at what this cropping operation
> is doing is that it's a function that takes two inputs and produces one
> output the two inputs are the the feature map for the entire image and the
> coordinates of the bounding box at which we want to crop and the output
> are the features for the bounding before that bounding box but now
> because of the snapping **we cannot back propagate to the coordinates
> of the bounding box** because the coordinates of the bounding box were
> always snapped onto the grid cells of the feature map so in this roi pool
> operation we can **we can back propagate to the from the region
> features back to the image features** but there's **no way for us to back
> propagate from the region features back to the coordinates** of the
> bounding box at which we were doing this this computation
>
>
>
> so that also gives us a hint that maybe something is a **little bit weird**
> inside this are this roi pool operation because **normally we like to use
> operations that are fully differentiable** and can properly pass gradients
> between all of the inputs and all the outputs and that's not the case with
> this ROI pool operation
>
>
>
> **so the the fix for this is this ROI aligned operation** that we did not have
> time last time to talk about in detail but **I wanted to go over it today
> because you actually will be implementing it on your homework and
> assignments**

<br>

<a id="node-axy3b2z"></a>

<p align="center"><kbd><img src="assets/9w39hunzd9.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, thì **RoI Align** đại khái ý tưởng sẽ là như vầy: Đầu tiên ta **cũng sẽ
> project cái proposed region lên feature map**, và đương nhiên nó sẽ (có
> thể) không khớp với grid-cell (hình minh họa cho thấy khung màu xanh lá
> không khớp với grid-cell),
>
>
>
> rồi tiếp như đã nói **ta sẽ không  snapping gì hết** vì đây là cái gây vấn đề.
> Mà ta sẽ **chia cái region trên feature map** (gọi là **"feature region"** cho
> gọn đi) **thành những phần bằng nhau** (ví dụ như 2x2 như minh họa).

<br>

<a id="node-t5fip5g"></a>

<p align="center"><kbd><img src="assets/86a6cl2si8.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì **đương nhiên các ô này nó không khớp với feature map grid cell**
> nên ta sẽ tính giá trị các ô này bằng **linear interpolation**.
>
>
>
> Ví dụ trong hình, vị trí chấm màu xanh là giá trị cần tìm, ta sẽ **dựa vào
> khoảng cách của nó với các chấm màu đen** để **tính một linear combination**
> cụ thể là theo công thức **fxy = sum i, j f_i,j*max(0,1-|x-i|)*max(0,1-|y-j|)**
>
>
>
> nôm na là t**rong tất cả các điểm màu đen**, **chỉ xét 4 điểm gần nhất** (cái 
> max(0,...) mang ý nghĩa này, ví dụ nếu green dot có khoảng cách tới
> black dot theo phương x lớn hơn 1 thì max(0, 1 - |x-i|) sẽ = 0, tức là không
> xét những black dot có khoảng cách theo phương x tới green dot > 1)
>
>
>
> Vậy với 4 điểm (6,5), (7,5), (6,6), (7,6) thì khoảng các của nó theo phương
> x và y tới green dot lần lượt là (0.5, 0.8) (0.5, 0.8) (0.5, 0.2) (0.5, 0.2)
>
>
>
> Áp vô công thức ta sẽ có giá trị của green dot là:
>
>
>
> f6,5(1-0.5)(1-0.8) + f7,5(1-0.5)(1-0.8) + f6,6(1-0.5)(1-0.2) + f7,6(1-0.5)(1-0.8)
>
>
>
> = f6.5*0.5*0.2 + f7,5*0.5*0.2 + f6,6*0.5*0.8 + f7,6*0.5*0.8

<br>

<a id="node-tspn2qm"></a>

<p align="center"><kbd><img src="assets/3gy737kce7s.png" width="80%"></kbd></p>

<br>

<a id="node-wgctsk3"></a>

<p align="center"><kbd><img src="assets/2sf349jprek.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/9jjx7czdxk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/p94izzcwcp8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/bhm93uyfwy.png" width="80%"></kbd></p>

<br>

<a id="node-bjhvw54"></a>

<p align="center"><kbd><img src="assets/2ewb92nda4w.png" width="80%"></kbd></p>

> [!NOTE]
> và **quá trình tính toán này differentiable**, giúp
> khắc phục vấn đề hồi nãy nói

<br>

<a id="node-ub1bhmn"></a>

<p align="center"><kbd><img src="assets/9lm5521pvn4.png" width="80%"></kbd></p>

> [!NOTE]
> và nó **cũng giải quyết vấn đề misalignment**
> luôn vì ta **ko còn "snapping" nữa**

<br>

<a id="node-uqlhdn3"></a>

<p align="center"><kbd><img src="assets/9ksftyq4a3h.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là Justin đặt vấn đề liệu **có cách nào mà ta có thể thiết kế một
> object detector mà ta không phải dựa trên anchor box** hay không.
>
>
>
> Thì có một cách làm rất hay xuất phát từ chính đại học Michigan đó là
> **CornerNet**. Ý tưởng là, ta sẽ **train một mô hình trong đó một nhánh
> nó sẽ dự đoán xác suất một vị trí trên feature map** **là một upper-left
> corner** của một b. box. và **một nhánh khác dự đoán xác suất một vị trí
> trên feature map là một lower-right corner**. Và việc train sẽ dựa vào
> cross-entropy loss ở từng vị trí.
>
>
>
> Túc test phát sinh vấn đề là làm sao ghép các predicted upper-left và
> lower-right được thành một cặp, thì người ta **sẽ biểu diễn dưới dạng
> upper left và lower right embedding vector**. Để rồi **nếu hai vector gần
> nhau thì đó là một cặp, tạo thành một bounding box.**

<br>

<a id="node-k556g4g"></a>

### mAP & NMS

<br>

<a id="node-hi5qxu9"></a>

<p align="center"><kbd><img src="assets/k9t78786gsb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sij3y8t881.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là, ta cần một chỉ số để so sánh hai bbox để phục vụ cho bước 3
> trong đó ta cần chọn lọc những predicted bbox tốt nhất.  Ví dụ như khi so
> với target bbox Thì người ta dùng IoU, tỉ lệ giữa diện tích của phần
> intersection và phần union. Tỉ lệ càng cao thì đương nhiên càng tốt.

<br>

<a id="node-c55vbxy"></a>

<p align="center"><kbd><img src="assets/1dcitj06gj3.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/nfysttp0ue.png" width="80%"></kbd></p>

> [!NOTE]
> tiếp theo đại khái là nói về vấn đề khi một object có thể có nhiều box, ta cần
> dùng một quá trình hậu xử lý (post-processing) để loại bỏ bớt, chỉ giữ lại  cái
> tốt nhất. Có nhiều cách, nhưng phổ biến nhất là Non-Max Suppression
> (NMS) mà mình đã biết ở DLSpec.
>
>
>
> Vậy thuật toán này đại ý là : Bỏ đi những box có độ overlap cao (tức chỉ số
> IoU)  với cái box có probability cao nhất.
>
>
>
> Ví dụ ở hai con chó này, model predicted ra 4 box. Thì đầu tiên ta xem cái
> nào có p cao nhất -> cái màu xanh. Vậy xem thử trong những cái còn lại cái
> nào overlap với nó cao nhất, hay IoU cao, thì loại bỏ đi. Cao là bao nhiêu thì
> ta định ra threshold ví dụ 0.7. Vậy trong 3 cái cam, vàng, tím. Có cái cam là
> có iou với  box xanh là lớn hơn 0.7 -> Loại bỏ box cam. Trong thực tế nếu
> còn các box khác cũng có iou với box xanh lớn hơn 0.7 thì loại hết.
>
>
>
> Thế thì mang ý nghĩa đơn giản là, ta chỉ dùng cái box có probability cao
> nhất, và bất cứ caí box nào khác có sự trùng lặp lớn với cái đó (đương nhiên
> sẽ có p thấp hơn vì đã nói cái kia có p cao nhất rồi) sẽ đều được cho là bị
> dư, trùng, nên bỏ đi.
>
>
>
> Rồi, tiếp theo ta sẽ chuyển sang cái khác (tức là không xét cái box xanh
> nữa)  có p cao nhất và lặp lại.

<br>

<a id="node-h5qz3u8"></a>

<p align="center"><kbd><img src="assets/tp7ib06pvem.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên NMS vẫn có hạn chế chưa khắc phục được tại thời điểm bài giảng
> đó là với những bức hình có rất nhiều object, khả năng là nó sẽ loại bỏ cả
> những box tốt. Cộng đồng vẫn đang nghiên cứu cách tốt hơn để làm.

<br>

<a id="node-63q430i"></a>

<p align="center"><kbd><img src="assets/c225gwmqq2.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là so với bài toán classification trong đó để đánh giá hiệu  suất của
> classifier tương đối đơn giản với những công cụ như đã  Biết. Còn để đánh
> giá hiệu suất của Object Detectors ta cần một  chỉ số goị là Mean Average
> Precision, có liên quan đến Recall-Precision Curve mà ta đã được học ở
> HandsOnML A.Geron, trong đó nó cho biết tương quan của Precision và
> Recall với các threshold khác nhau.
>
>
>
> Vậy đầu tiên ta sẽ lấy object detector và inference các image của test set, rồi
> dùng NMS để loại đi các box dư như vừa nói.
>
>
>
> Bước 2: Với mỗi category, ta sẽ lấy ra hết các box gắn với category đó **trong 
> test set**, và sort theo p
>
>
>
> Ví dụ, mấy ô màu xanh đại diện cho các box có p_dog cao nhất của cả test
> set tức là trong test set, nhữn box nào thuộc về class dog, thì lấy ra sort theo
> p từ cao xuống thấp.
>
>
>
> Rồi, còn mấy ô cam đại diện các ground-truth boxed có "category = dog" **trong
> test set.**

<br>

<a id="node-ozo96fp"></a>

<p align="center"><kbd><img src="assets/abwxg4328x6.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo, ta mới lấy cái "dog box" có top score, xem thử nó có khớp với
> ground-truth "dog box" nào không bằng cách xét iou > 0.5
>
>
>
> Điều này thật ra có ý nghĩa là ta chọn một một **threshold (ngưỡng xác suất**
> mà ta quyết định rằng đó sẽ là "dog") **bằng 0.99, và xem thử với threshold
> này thì precision và recall là bao nhiêu (ta đang vẽ biểu đồ Precision Recall
> Curve mà)**
>
>
>
> giả sử thấy nó **match với một cái là ô cam ở giữa**. Tức là ta có 1 "True
> Positive"
>
>
>
> Khi đó ta sẽ "nói rằng" khi xét tại threshold 0.99 ta **có 1 dự đoán là positive
> thì nó " trúng" hết**, tức là Precision (độ chính xác là 1/1). Và mình liên hệ lại
> thì nó đương nhiên là tỉ lệ TP/(TP+FP): Trong những "cái" predict Positive thì
> đúng (True) được bao nhiêu %. Ở đây, xét "những cái có p dog cao nhất", dự
> đoán 1 cái thì đúng cả 1 nên Precision = 1.
>
>
>
> Còn trong 3 box là Positive thì chỉ "phát hiện được 1" nên độ nhạy Sensitivity
> hay Recall là 1/3.
>
>
>
> Từ đó ta vẽ được một điểm của Precision-Recall Curve.

<br>

<a id="node-24f62tq"></a>

<p align="center"><kbd><img src="assets/1tfi2na8yz5.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp ta check cái dog box có p = 0.5, cũng đồng ý nghĩa là ta hạ
> threshold xuống còn 0.95 và xem thử precision và recall bao nhiêu.
>
>
>
> Giả sử cái dog box 0.95 nó **match với thêm một ground truth nữa**.
> tức là thêm một True Positive nữa
>
>
>
> Vậy, trong "2 box được predict là positive" thì "trúng" cả 2 -> Precision
> = 2/2 = 1.
>
>
>
> Và trong 3 truth thì trúng dc 2, -> Sensitivity = Recall  = 2/3.
>
>
>
> Vẽ thêm 1 điểm nữa

<br>

<a id="node-ca39f5r"></a>

<p align="center"><kbd><img src="assets/j19ubpokiff.png" width="80%"></kbd></p>

> [!NOTE]
> tiếp, "hạ threshold" xuống 0.9, thì giả sử cái bbox có p = 0.9 không match với 
> truth box nào, tức là nó là False Positive. Vậy Precision trở thành 2/3
> và Sensitivity = 2/3.
>
>
>
> Tiếp hạ threshold xuống 0.5, cái bbox có p 0.5 giả sử cũng không match, vậy
> là thêm một false positive nữa -> Precision = 2/4, Sensitivity = 2/3
>
>
>
> Tiếp, với threshold = 0.1, giả sử cái bbox này lại match với true box, tức 
> là thêm một True Positive, nên Precision = 3/5, Sensitivity = 3/3.
>
>
>
> Ta vẽ được P.R curve.

<br>

<a id="node-98njv7i"></a>

<p align="center"><kbd><img src="assets/jjl0678as6.png" width="80%"></kbd></p>

> [!NOTE]
> và khi đó Area Under the Curve (AUC) chính là chỉ số mean Average Precision
> ta cần. Vậy để hiểu ý nghĩa của việc tại sao ta dùng chỉ số này để đánh giá  một
> Object Detector thì cần hình dung khi nào thì ta có mAP = 1.
>
>
>
> mAP = 1 khi, khi threshold giảm dần thì precision luôn = 1, và sensitivity sẽ dần
> dần -> 1: nôm na là, giảm dần ngưỡng thì các ngày càng nhiều dự đoán dương
> tính và cái nào cũng đúng đồng thời số case dương tính thật sự cũng dần được
> phát hiện đủ, để rồi khi phát hiện đầy đủ các case dương tính thật rồi tức là độ
> nhạy đã = 100% rồi thì độ chính xác vẫn = 100% (tức là tất cả những dự đoán
> dương tính đều đúng, hay vừa đủ, vừa đúng)
>
>
>
> Mà chiếu theo chuỗi box ở trên, muốn được vậy thì các box "trúng" (tức là
> match với orange box / hay true positive) sẽ đều phải nằm ở trước, để khi giảm
> threshold dần dần đều phát hiện được chúng. Điều này rõ ràng mang ý nghĩa
> rằng, các box dự đoán có p cao đều match với truth box, còn các box không
> match đều có p thấp. Được như vậy rõ ràng là một Object Detector tốt. 
>
>
>
> Justin nói thêm, thực tế cho thấy có những bài toán người ta cần precision cao
> ví dụ như trong xe tự lái, ta không muốn miss bất kì cái xe nào xung quanh, thì
> ở đây ta muốn độ nhạy sensitivity phải cao, dù có thể hi sinh precision (phát hiện
> hết các xe hơi xung quanh nhưng chấp nhận có những cái ko phải là xe)
>
>
>
> Tóm lại là tùy hoàn cảnh cụ thể mà ta có thể ưu tiên Precision hay Sensitivity
> nhưng P-R curve cho ta một đánh giá tổng thể khả năng của model. (nó giống
> việc ta đánh giá Classification model vậy)

<br>

<a id="node-7rz2zcd"></a>

<p align="center"><kbd><img src="assets/190lzud57v3.png" width="80%"></kbd></p>

> [!NOTE]
> và đương nhiên với mỗi category ta sẽ tính
> một cái như vậy,. Và average lại

<br>

<a id="node-6q6znx6"></a>

<p align="center"><kbd><img src="assets/u14tyjs7fn.png" width="80%"></kbd></p>

> [!NOTE]
> và đó cũng chỉ là ta đang dùng IoU threshold 0.5, người ta sẽ lặp lại với các
> threshold khác. Và average lại hết mới được cái mAP cuối cùng

<br>

<a id="node-a4djtzn"></a>

## Mở Rộng Hơn Nữa

<br>

<a id="node-dh55lqw"></a>

<p align="center"><kbd><img src="assets/7vg420ioge2.png" width="80%"></kbd></p>

> [!NOTE]
> Justin lướt qua một cái mà ổng làm với Andrej: Kết hợp
> object detect và image captioning

<br>

<a id="node-19edruj"></a>

<p align="center"><kbd><img src="assets/y1a23458iet.png" width="80%"></kbd></p>

<br>

<a id="node-uohsmpd"></a>

<p align="center"><kbd><img src="assets/pbtodjrafj.png" width="80%"></kbd></p>

> [!NOTE]
> But the idea here is that once you have this, **you
> can kind of tie together a lot of these ideas** and if
> you have **some new problem** that you're
> interested in tackling like **dense captioning**, you
> can **recycle a lot of the components  that you've
> learned from other problems** like object detection
> and image captioning and kind of **stitch together
> one end-to-end network** that produces the outputs
> that you care about for your problem

<br>

<a id="node-92dn9gq"></a>

<p align="center"><kbd><img src="assets/udt1gmqcema.png" width="80%"></kbd></p>

<br>

<a id="node-4otvxrc"></a>

<p align="center"><kbd><img src="assets/kudnvknk6l.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là người ta trong lĩnh vực cv phân biệt ra Things và Stuff. Things
> là những object mà ta sẽ muốn tách bạch từng cái, từng con
>
>
>
> còn stuffs thì ngược lại như bãi cỏ, bầu trời, cây cối...

<br>

<a id="node-z70fyfj"></a>

<p align="center"><kbd><img src="assets/wt3b1k4vb1s.png" width="80%"></kbd></p>

> [!NOTE]
> Cho nên ý nói, với object detection thì chỉ apply với things thôi, đương
> nhiên vì ko ai muốn detect từng ngọn cỏ cả. Còn với semantic segmentation
> thì cả things lẫn stuff

<br>

<a id="node-o4l2nm4"></a>

<p align="center"><kbd><img src="assets/ckdtnprz0rd.png" width="80%"></kbd></p>

> [!NOTE]
> nên Instance Segmentation là ta muốn detect từng object, và
> segmentation chúng

<br>

<a id="node-uongo4r"></a>

<p align="center"><kbd><img src="assets/77lzebihklf.png" width="80%"></kbd></p>

> [!NOTE]
> vậh đầu tiên có thể dùng object detector để xác định từng
> object sau đó pass nó qua segmentation object

<br>

<a id="node-gkdvebv"></a>

<p align="center"><kbd><img src="assets/4m2ym7ztfsm.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/2tauprqod7b.png" width="80%"></kbd></p>

> [!NOTE]
> vậy thì cái này chỉ cần dựa trên object detector model như Faster
> R-CNN nhưng có thêm một bước segmentation (mask prediction) nữa

<br>

<a id="node-cb40nu9"></a>

<p align="center"><kbd><img src="assets/wvqnfbjz96.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là khúc đầu cũng giống R-CNN - dự đoán ra các proposed region.
> Sau đó, với mỗi region. một nhánh predict class và bounding box như trên,
> nhưng thêm một nhánh predict một mask cho mỗi class trong C class
> - giống bài toán segmentation
>
>
>
> Nói chung ý tưởng chính là kết hợp hết những kiến trúc của các bài toán
> segmentation, localization (**unifies all of these different problems** that we'
> ve been talking about today i**nto one nice jointly end-to-end trainable
> model**)

<br>

<a id="node-jnh7mtc"></a>

<p align="center"><kbd><img src="assets/r78pwxoo80c.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là với cái này thì cái target để train cho cái mask sẽ
> kiểu như là cái mask trên propose region

<br>

<a id="node-982s7yy"></a>

<p align="center"><kbd><img src="assets/ihspd9amfhm.png" width="80%"></kbd></p>

<br>

<a id="node-6p8arb6"></a>

<p align="center"><kbd><img src="assets/ff0ys00bbhv.png" width="80%"></kbd></p>

> [!NOTE]
> thậm chí là kết hợp cáo
> pose prediction luôn

<br>

<a id="node-la9l7rq"></a>

<p align="center"><kbd><img src="assets/r51i2ievv69.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6i4x7bts4gf.png" width="80%"></kbd></p>

> [!NOTE]
> ngoài ra còn một task nữa mà người ta cũng làm là Panoptic segmentation,
> cũng như segmentation nhưng có phân biệt từng con bò (things) với nhau
> còn với stuff thì nó gộp chung

<br>

<a id="node-n7xmnr2"></a>

<p align="center"><kbd><img src="assets/rzk1loklcnk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xam3wfam7gs.png" width="80%"></kbd></p>

> [!NOTE]
> rồi còn có cái bài toán này, predict ra keypoints, tương tự chỉ
> cần mở rộng Faster R-CNN để nó predict thêm các keypoint
> positions

<br>

<a id="node-cnuzwb6"></a>

<p align="center"><kbd><img src="assets/xw4r1vmhno.png" width="80%"></kbd></p>

<br>

<a id="node-tqqyyts"></a>

<p align="center"><kbd><img src="assets/g9anjr2wc78.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/a1roed4zjd9.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/m8x6jl5dr2b.png" width="80%"></kbd></p>

> [!NOTE]
> ý tưởng chung là có thể mở rộng để trở
> thành nhiều mô hình khác

<br>

<a id="node-futwdnr"></a>

<p align="center"><kbd><img src="assets/w9t64r6p3hq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/j3fnr1h7uhn.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là có thể mở rộng hơn nữa để thành
> bài toán predict luôn 2D -> 3D

<br>

<a id="node-d08up6b"></a>

<p align="center"><kbd><img src="assets/6smv2q1ic3w.png" width="80%"></kbd></p>

<br>

