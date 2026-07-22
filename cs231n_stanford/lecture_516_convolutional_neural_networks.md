# Lecture 5/16 - Convolutional Neural Networks

📊 **Progress:** `52` Notes | `63` Screenshots

---
<a id="node-orwtv2c"></a>

## Lecture 5/16 - Convolutional Neural Networks

<br>

<a id="node-04349q7"></a>

<p align="center"><kbd><img src="assets/tie9w7tt97.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên đại khái là tiếp nối tuần trước, ta đã hiểu hidden layer đóng vai trò
> giống như giúp học thêm / tạo thêm nhiều hơn các template từ đó giúp
> classify tốt hơn

<br>

<a id="node-ao8j954"></a>

<p align="center"><kbd><img src="assets/dmxvaoatao6.png" width="80%"></kbd></p>

> [!NOTE]
> Tuần này là
> Convolution NN

<br>

<a id="node-b8x7gpc"></a>

<p align="center"><kbd><img src="assets/hy8ozmw4ldu.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý nói về Mark I Perceptron, trong đó không có việc sử dùng
> backprop hay gradient descent để update weight mà chỉ là update
> weight theo một hướng nào đó giúp giảm sai sót.
>
>
>
> Mô hình này cũng dùng công thức weight sum,  các feature được nhân
> (scale) với weight w và sum lại. Nhưng không có activation function mà
> chỉ là so sánh kết quả đó với một threshold để từ đó quyết định output
> là 1 hoặc 0. Gọi là threshold function.

<br>

<a id="node-h894q3e"></a>

<p align="center"><kbd><img src="assets/b6uaxjo34bj.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó là Adaline trong đó, người ta stack các "layer" lại để bắt đầu
> hình thành cái giống như hidden layer nhưng vẫn chưa có backrprop
> có 1 cách thức / principle để train

<br>

<a id="node-hbmlpq0"></a>

<p align="center"><kbd><img src="assets/3gifkes1jz5.png" width="80%"></kbd></p>

> [!NOTE]
> phải đến khi Rumehard thì mới phổ
> biến backprop để có cách thức train
> ra các giá trị của weight

<br>

<a id="node-4f22ocb"></a>

<p align="center"><kbd><img src="assets/sun8fccv13.png" width="80%"></kbd></p>

> [!NOTE]
> Giai đoạn ~2006 nhóm nghiên cứu của gs Hinton thực
> hiện cách làm là pretrain và dùng giá trị đó initialize
> trước khi dùng backprop để finetune

<br>

<a id="node-x0k370i"></a>

<p align="center"><kbd><img src="assets/kri55c9etya.png" width="80%"></kbd></p>

> [!NOTE]
> đến 2012 với việc ra đời của AlexNet, đạt performance rất tốt
> trên ImageNet dataset để bắt đầu đánh dấu cột mốc của
> ConvNet và DeepLearning

<br>

<a id="node-0y7xrox"></a>

<p align="center"><kbd><img src="assets/t3po4pidzih.png" width="80%"></kbd></p>

> [!NOTE]
> Ngược về 1950, người ta làm thí nghiệm đại khái là cho con
> mèo nhìn các hình ảnh khác nhau như đường chéo hay dấu
> tròn để đo tín hiệu não của nó

<br>

<a id="node-0h21rjk"></a>

<p align="center"><kbd><img src="assets/e3qre5eayl.png" width="80%"></kbd></p>

> [!NOTE]
> Kết quả đại ý là cho thấy não bộ cũng sử dụng cấu
> trúc phân tầng (hierarchical) khi hoạt động

<br>

<a id="node-n2qxt8u"></a>

<p align="center"><kbd><img src="assets/8mi6ldym2nj.png" width="80%"></kbd></p>

> [!NOTE]
> cụ thể là các (neuron) cell đầu tiên / simple sẽ chịu trách nhiệm "
> nhận ra" các thay đổi về light orientation để sau đó các complex
> cell sẽ response về orientation và movement

<br>

<a id="node-wphrfjf"></a>

<p align="center"><kbd><img src="assets/252u65n94uc.png" width="80%"></kbd></p>

> [!NOTE]
> đến 1980 cái này là lần đầu cho thấy kiểu kiểu của
> neural network với các layer simple và complex cell

<br>

<a id="node-x1df67j"></a>

<p align="center"><kbd><img src="assets/arsen78e6k6.png" width="80%"></kbd></p>

> [!NOTE]
> đến 1998, Yan LeCun phát triển LeNet-5 dùng gradient based learning
> để học cách nhận diện được chữ số viết tay ứng dụng vào các hệ thống
> đọc mã bưu chính postal code nhưng nó vẫn gặp khó Khi muốn scale
> lên qua các nhiệm vụ khác khó hơn như nhận diện hình ảnh phức tạp
> hơn

<br>

<a id="node-8zkkq6j"></a>

<p align="center"><kbd><img src="assets/vhikjcg398m.png" width="80%"></kbd></p>

> [!NOTE]
> So với Lenet thì AlexNet cũng không quá khác biệt nhưng
> thành công của nó, việc nó sâu hơn, nhiều layer được cho
> phép bởi sự dồi dào của data hơn (ImageNet) và
> computational resource nhiều hơn

<br>

<a id="node-oynnml9"></a>

<p align="center"><kbd><img src="assets/6q7wu636rbl.png" width="80%"></kbd></p>

> [!NOTE]
> Kề từ đó thì ConvNets đã đóng góp rất lớn vào các tiến
> bộ của Computer Vision như các task classification,
> retrieval, detection và segmentation

<br>

<a id="node-v5xlup5"></a>

<p align="center"><kbd><img src="assets/m5hvvby2a3.png" width="80%"></kbd></p>

<br>

<a id="node-qh79t5q"></a>

<p align="center"><kbd><img src="assets/j4sl6kpzyy.png" width="80%"></kbd></p>

<br>

<a id="node-y9y12te"></a>

<p align="center"><kbd><img src="assets/ecdmnjt3lnt.png" width="80%"></kbd></p>

<br>

<a id="node-vtbartg"></a>

<p align="center"><kbd><img src="assets/8gno3mmq8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6oia592iqoy.png" width="80%"></kbd></p>

<br>

<a id="node-yfal3sc"></a>

<p align="center"><kbd><img src="assets/gjzrdvqr2us.png" width="80%"></kbd></p>

<br>

<a id="node-uob7uy7"></a>

<p align="center"><kbd><img src="assets/8k7gnpoy2ic.png" width="80%"></kbd></p>

<br>

<a id="node-klkcxa5"></a>

<p align="center"><kbd><img src="assets/9cpsmdofmpi.png" width="80%"></kbd></p>

> [!NOTE]
> Ôn lại về cách làm của fully connected layer, đó là nó thực hiện phép
> nhân vector input với mỗi hàng của matrix W để ra một activation,
> matrix có mấy hàng thì vector output có mấy phần tử
>
>
>
> Trước đó để có vector input thì image 32x32x3 đã được flatten  thành
> vector

<br>

<a id="node-0wg3t8e"></a>

<p align="center"><kbd><img src="assets/w752ol5d0ec.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là với Conv layer, không **flatten imag**e nữa mà
> giữ nghiên **spatial shape**. Và weight của layer sẽ là
> một tensor (gọi là filter) như này

<br>

<a id="node-9207zsy"></a>

<p align="center"><kbd><img src="assets/q3tlmeel8w.png" width="80%"></kbd></p>

> [!NOTE]
> và filter luôn cùng số channel với image (hoặc input
> tensor)

<br>

<a id="node-yzvbc7d"></a>

<p align="center"><kbd><img src="assets/1syii8rwxx6.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó phép tính toán chính là việc tính dot product của filter và cái vùng
> cùng shape của cái image.
>
>
>
> Có người hỏi wTx là sao thì cơ bản đó chỉ là notation (cách kí hiệu) của
> phép tính dot product. để thể hiện phép tính phải có compatible shape 1xn.
> nx1
>
>
>
> Và có thể hiểu là lấy cái vùng cùng shape với filter của cái image ra, flatten
> (hay stretch out) và lấy cái filter cũng flatten ra, rồi dot product hai thằng đó.

<br>

<a id="node-jq0eb42"></a>

<p align="center"><kbd><img src="assets/p7cbbbr5arj.png" width="80%"></kbd></p>

> [!NOTE]
> Filter sẽ bắt đầu từ top left corner và slide trái sang phải trên
> xuống dưới, mỗi lần nó thực hiện phép tính để ra 1 số. Có thể
> có bước slide tùy vào stride. Và như đã biết ở DLSpec,
> spatial size kết quả có thể bằng hoặc nhỏ hơn cái hình cũ tùy
> vào cách padding

<br>

<a id="node-yqve5wg"></a>

<p align="center"><kbd><img src="assets/j5m4v4i43l.png" width="80%"></kbd></p>

> [!NOTE]
> và với filter khác thì lại ra một output
> thứ 2 (gọi là activation map)

<br>

<a id="node-9eebwhe"></a>

<p align="center"><kbd><img src="assets/qer7bnudsmo.png" width="80%"></kbd></p>

> [!NOTE]
> với 6 cái filter thì ta có 6 cái activation maps. Stack
> lại với nhau thành ra 1 tensor 28x28x6 ("new image")

<br>

<a id="node-53e2zyn"></a>

<p align="center"><kbd><img src="assets/a6tnmzo8ht9.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó apply non-linear activation function với các output này
> trước khi tiếp tục với các layer sau. Cơ bản convNet là chuỗi
> các convolutional layers xen kẽ là các activation function
>
>
>
> Số lượng các filter mỗi layer, stride, padding là tùy vào cách
> Design (hyper-params)

<br>

<a id="node-xwd5zat"></a>

<p align="center"><kbd><img src="assets/ggzd172kcql.png" width="80%"></kbd></p>

> [!NOTE]
> và qúa trình huấn luyện model sẽ train các filter để một cách nôm na
> là chúng đảm nhiệm việc detect được các feature từ đơn giản đến
> phức tạp qua từng layer
>
>
>
> Và ta sẽ được học các xem các hình ảnh này ở các phần sau.
>
>
>
> Trong slide là visualization của các low & high level feature của
> VGG-16 từ các layer đầu đến các layer sau
>
>
>
> Và ở cuối cùng linearly separable classifier có thể dùng các high level
> feature này để classify

<br>

<a id="node-u6r4599"></a>

<p align="center"><kbd><img src="assets/tzekf773a1r.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nó tương đồng với nghiên cứu của Wisel đó là
> qúa trình ConvNet nó học chính là nó detect các feature
> từ đơn giản đến phức tạp

<br>

<a id="node-exiyttc"></a>

<p align="center"><kbd><img src="assets/spupbuo5ovl.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là hình ảnh khác của
> các convolution filter

<br>

<a id="node-if0c5hq"></a>

<p align="center"><kbd><img src="assets/jz5v47396d.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là kiến trúc (hoặc kiểu kiểu của một convNet) sẽ
> có thêm các pooling layer trước khi qua Conv+(relu) tiếp
> theo. Cuối cùng sẽ là một fully connected layer để
> flatten out trước khi output

<br>

<a id="node-ygm9h5s"></a>

<p align="center"><kbd><img src="assets/djuqoh02n7s.png" width="80%"></kbd></p>

<br>

<a id="node-7cgutys"></a>

<p align="center"><kbd><img src="assets/b5kt349i8qh.png" width="80%"></kbd></p>

> [!NOTE]
> với phép convol stride = 1 thì
> từ 7x7 output sẽ ra 5x5

<br>

<a id="node-ldw9esw"></a>

<p align="center"><kbd><img src="assets/02bp2urjqlij.png" width="80%"></kbd></p>

> [!NOTE]
> với stride 2 thì
> output sẽ là 3x3

<br>

<a id="node-jk7ihrv"></a>

<p align="center"><kbd><img src="assets/ooc7tyhahjh.png" width="80%"></kbd></p>

> [!NOTE]
> với stride 3 thì vì nó không fit nên ko thể apply stride = 3

<br>

<a id="node-9uhi2s9"></a>

<p align="center"><kbd><img src="assets/liym5tjl0bq.png" width="80%"></kbd></p>

> [!NOTE]
> khái quát với công thức
> tính output size

<br>

<a id="node-xlyn2zk"></a>

<p align="center"><kbd><img src="assets/tunrei95hx.png" width="80%"></kbd></p>

> [!NOTE]
> với padding ta có thể khắc phục tình trạng
> không fit hoặc output nhỏ đi

<br>

<a id="node-fsnbnib"></a>

<p align="center"><kbd><img src="assets/x8fjzvwyo4e.png" width="80%"></kbd></p>

> [!NOTE]
> Q1: Depth của output?
>
>
>
> -> A: Là số filter
>
>
>
> Q2: ..
>
>
>
> -> A: Đại khái là trong hình trước chỉ là để cho đơn giản thì chỉ thể hiện
> việc tính toán ở 1 "channel"/"slice" còn sự thật thì phải tính trên hết các "
> depth"
>
>
>
> Q3: Nếu dài và rộng khác nhau thì có thể dùng stride khác  nhau hay
> không.
>
>
>
> -> A: Đại khái là hoàn toàn có thể nhưng thường người ta chỉ làm việc với
> square input và dùng cùng một stride

<br>

<a id="node-m6zxo6q"></a>

<p align="center"><kbd><img src="assets/4zhm3rnyo4g.png" width="80%"></kbd></p>

> [!NOTE]
> Q: Why zero padding?
>
>
>
> A: Khi ta muốn output vẫn có cùng size với input
> hoặc muốn apply filter để detect info tại corner

<br>

<a id="node-yv3bd3s"></a>

<p align="center"><kbd><img src="assets/vviisccp2pb.png" width="80%"></kbd></p>

> [!NOTE]
> phổ biến người ta dùng filter 3x3, 5x5,7x7 với các zero padding
> tương ứng 1,2,3 để keep size

<br>

<a id="node-j8n4lco"></a>

<p align="center"><kbd><img src="assets/61mzdpru6m.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là nếu không dùng padding, qua
> nhiều layer cái spatial size (width &
> height) sẽ giảm nhanh chóng

<br>

<a id="node-c70wafg"></a>

<p align="center"><kbd><img src="assets/t91616jpgp8.png" width="80%"></kbd></p>

<br>

<a id="node-z8wyz1l"></a>

<p align="center"><kbd><img src="assets/4it1lacnhlf.png" width="80%"></kbd></p>

> [!NOTE]
> Theo công thức là tính được size (w & h) và vì có 10 filter nên depth sẽ là 10.
>
>
>
> Câu hỏi là có bao nhiêu params?

<br>

<a id="node-snoal1e"></a>

<p align="center"><kbd><img src="assets/fp2dg41zkxv.png" width="80%"></kbd></p>

> [!NOTE]
> Mỗi filter có 3 channel, nên có 5x5x3 số,
> mỗi cái nó có kèm 1 bias nữa là 5x5x3+1
> = 76. 10 cái filter là 760

<br>

<a id="node-0tz724b"></a>

<p align="center"><kbd><img src="assets/jjnstqn9e5i.png" width="80%"></kbd></p>

> [!NOTE]
> một số kí hiệu

<br>

<a id="node-42zlab2"></a>

<p align="center"><kbd><img src="assets/p1835h9aksb.png" width="80%"></kbd></p>

> [!NOTE]
> và các setting phổ biến

<br>

<a id="node-cev89td"></a>

<p align="center"><kbd><img src="assets/jw7hkkuky99.png" width="80%"></kbd></p>

> [!NOTE]
> 1x1 filters, mỗi cái tạo ra 1 miếng vẫn
> giữ shape của input. 32 cái filter tạo
> ra 32 miếng stack lại

<br>

<a id="node-d7rlkk5"></a>

<p align="center"><kbd><img src="assets/us60tmm7grn.png" width="80%"></kbd></p>

> [!NOTE]
> ví dụ về Conv layer
> trong Torch và Café

<br>

<a id="node-u2ox6th"></a>

<p align="center"><kbd><img src="assets/zco9ya2tr47.png" width="80%"></kbd></p>

<br>

<a id="node-bjjmlq5"></a>

<p align="center"><kbd><img src="assets/ycslttbkl4g.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi là dùng stride lớn để làm gì?-> Có tác dụng như pooling, giúp
> giảm spatial size và nhờ đó có thể giảm số params khi chuyển qua
> fully connected layer.
>
>
>
> Nói chung là stride một dạng hyperparams,
>  cân nhắc trade-off giữa model size, số params, overfit...

<br>

<a id="node-5btvc3u"></a>

<p align="center"><kbd><img src="assets/rsb0lrmoevp.png" width="80%"></kbd></p>

> [!NOTE]
> ý nói vẫn là "cái kiểu giống giống" như neuron thần kinh nhưng
> khác ở chỗ nó (mỗi filter) chỉ look at a local region thay vì toàn bộ cái hình

<br>

<a id="node-gn8q8zq"></a>

<p align="center"><kbd><img src="assets/g9pqpslgchn.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là một thuật ngữ hay dùng/gặp khác cho filter là **receptive field**
>
>
>
> Và chú ý rằng dù là filter sẽ slide và tính cho mọi  vùng của image
> nhưng nó xài chung một bộ params.
>
>
>
> Điều này giúp ta hiểu nếu có nghe về shared params

<br>

<a id="node-4t0yh4a"></a>

<p align="center"><kbd><img src="assets/vi34wvkd69n.png" width="80%"></kbd></p>

> [!NOTE]
> một cách hiểu theo kiểu brain/neuron với Conv layer nữa đó là mỗi
> filter giống như một neuron quét qua khắp các input region để rồi 5
> neuron đều nhìn vào cùng 1 vùng và xem xét các pattern nào đó
> mà mỗi cái nó chịu trách nhiệm
>
>
>
> Và mỗi value của output chỉ connect với 1 vùng của input  chứ
> không như Fully Connected layer

<br>

<a id="node-vpdadl3"></a>

<p align="center"><kbd><img src="assets/je023ygqvxq.png" width="80%"></kbd></p>

> [!NOTE]
> Pooling chỉ giảm spatial size của activation map chứ giữ nguyên depth

<br>

<a id="node-0zpxuvd"></a>

<p align="center"><kbd><img src="assets/use0uaszdmb.png" width="80%"></kbd></p>

> [!NOTE]
> có thể hiểu nôm na tác dụng của max pooling là nó khuếch
> đại / làm rõ các thông tin / signal mà filter detect được

<br>

<a id="node-mf4ea9t"></a>

<p align="center"><kbd><img src="assets/ez1hqbw4ksc.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái câu hỏi là dùng stride có thể cũng giảm size vậy thì có thể
> dùng stride được ko?
>
>
>
> -> Được

<br>

<a id="node-1hjbilo"></a>

<p align="center"><kbd><img src="assets/5k9u3itmo3b.png" width="80%"></kbd></p>

<br>

<a id="node-47ndb57"></a>

<p align="center"><kbd><img src="assets/yge2246mtho.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là mấy cái hình nhỏ nhỏ ở dưới chính là activation map
> output, và, pooling layer chỉ giảm size xuống (down sampling)
> bằng cách lấy giá trị lớn nhất ở mỗi location. Để ý layer cuối sẽ rõ.
>
>
>
> Layer đầu sẽ detect "how much a edge pattern is fired", ý nói, nó sẽ
> tính ra giá trị lớn nếu nó detect được pattern như "edge"
> Để rồi layer tiếp theo nó sẽ detect "how much a corner is fired", giống
> như nó sẽ "filter" để tìm ra các pattern phức tạp hơn.
> Để rồi ở layer cuối nó sẽ kiểu như tính toán ra "how much a pattern
> phức tạp (high level feature) được detect.
> Và FC layer sẽ giống như tổng hợp lại hết để quyết định xem lấy cái nào
> mỗi cái bao nhiêu để đưa ra quyết định cuối cùng

<br>

<a id="node-lrku2nd"></a>

<p align="center"><kbd><img src="assets/tl93du9r65.png" width="80%"></kbd></p>

> [!NOTE]
> Q: Chọn pooling như thế nào, ý là làm sao để biết nên dùng
> pooling đến đâu để giảm size xuống?
>
>
>
> A: Cái này là hyperparams, cũng như các yếu tố khác của kiến
> trúc model, phải thử sai thôi (Hyperparams tuning)

<br>

<a id="node-t60fdj5"></a>

<p align="center"><kbd><img src="assets/nronrzqlqlg.png" width="80%"></kbd></p>

> [!NOTE]
> Nói về cái demo của ConvNet train với CIFAR-10 của Andrey Karpathy. 
> Chú ý là khi nhìn vào các activation map in ra thì với những layer đầu
> có thể ta sẽ thấy hiểu hiểu hình ảnh đó là gì nhưng với những layer
> sau sâu hơn thì nếu thấy khó hiểu thì cũng đừng lo vì với các high level
> Feature, model nó học / detect các pattern gì thì chỉ nó mới biết

<br>

<a id="node-xc2npoy"></a>

<p align="center"><kbd><img src="assets/ovj1eg5ks4.png" width="80%"></kbd></p>

> [!NOTE]
> tóm lại, convnet stack các conv, pool, fc layer lại. Khuynh hướng các filter
> nhỏ hơn ngày càng được sử dụng. Khuynh hướng bỏ pool/fc layer và kiến
> trúc điển hình của ConvNet là nhiều block Conv-Relu-...Conv-Relu-Pool,
> sau đó là vài block fc-relu trước khi out với softmax

<br>

