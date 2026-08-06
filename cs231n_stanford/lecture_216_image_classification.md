# Lecture 2/16 - Image Classification

📊 **Progress:** `41` Notes | `58` Screenshots

---
<a id="node-zxvracm"></a>

## Lecture 2/16 - Image Classification

<br>

<a id="node-eae738h"></a>

<p align="center"><kbd><img src="assets/gy64iml86ru.png" width="80%"></kbd></p>

> [!NOTE]
> http://cs231n.github.io/python-numpy-tutorial/

<br>

<a id="node-qzqhhf2"></a>

<p align="center"><kbd><img src="assets/zi6rmz1lfgk.png" width="80%"></kbd></p>

> [!NOTE]
> http://cs231n.github.io/gce-tutorial/

<br>

<a id="node-e76lehv"></a>

<p align="center"><kbd><img src="assets/bs2otlglclg.png" width="80%"></kbd></p>

<br>

<a id="node-sjxnzl6"></a>

<p align="center"><kbd><img src="assets/h4lh7chyg5.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với máy tính thì nó chỉ thấy một
> tensor các con số. Làm sao để có thể học dc
> những pattern của con mèo

<br>

<a id="node-xf9nbu0"></a>

<p align="center"><kbd><img src="assets/9li09ebl38i.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là khi shift cái camera qua chút xíu,
> con mèo vẫn y nguyên nhưng các valie của
> các pixel sẽ hoàn toàn khác. Và model phải
> Vẫn detect được là mèo

<br>

<a id="node-go0bj9t"></a>

<p align="center"><kbd><img src="assets/28srfbmzscm.png" width="80%"></kbd></p>

<br>

<a id="node-bsg1kh5"></a>

<p align="center"><kbd><img src="assets/bzdol46fqh.png" width="80%"></kbd></p>

<br>

<a id="node-ze7nyld"></a>

<p align="center"><kbd><img src="assets/zgw054mbnr.png" width="80%"></kbd></p>

<br>

<a id="node-zijt22v"></a>

<p align="center"><kbd><img src="assets/i9g99ca4odr.png" width="80%"></kbd></p>

<br>

<a id="node-8njixqt"></a>

<p align="center"><kbd><img src="assets/hlout1tezrn.png" width="80%"></kbd></p>

<br>

<a id="node-a6shcrw"></a>

<p align="center"><kbd><img src="assets/ursi20jp28g.png" width="80%"></kbd></p>

<br>

<a id="node-h1qh0xf"></a>

<p align="center"><kbd><img src="assets/hjjouwdn98s.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là có thể thử dùng các corner, viết một rule,
> combination các rule cho edge, corner sao sao đó thì là mèo.
> Nhưng kiểu này không ổn, không scalable vì với con chó phải
> làm lại. Mà cũng ko hiệu quả

<br>

<a id="node-7qrb2o2"></a>

<p align="center"><kbd><img src="assets/2b7rj57kxgb.png" width="80%"></kbd></p>

<br>

<a id="node-1g36zbr"></a>

<p align="center"><kbd><img src="assets/9ywqbxyjiim.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dùng KNN có nghĩa bước 1 là nhớ tất cả các
> image. Bước 2 khi prediction thì lấy ra image gần với
> image cần predict nhất (dùng KKN). Từ đó cho ra
> prediction class của nó.

<br>

<a id="node-kwrosvn"></a>

<p align="center"><kbd><img src="assets/rmu5dq5kyum.png" width="80%"></kbd></p>

> [!NOTE]
> Nói về bộ Cifar hay dùng cho việc thử
> nghiệm các ml model

<br>

<a id="node-j2zh6if"></a>

<p align="center"><kbd><img src="assets/0lnafqnk05v.png" width="80%"></kbd></p>

> [!NOTE]
> Thì đại khái là tuy cách này có vẻ hơi stupid
> nhưng ít nhiều nó cũng có tính reasonable.

<br>

<a id="node-otdjq35"></a>

<p align="center"><kbd><img src="assets/nk60h0d3z9.png" width="80%"></kbd></p>

> [!NOTE]
> Thì dẫn đến cách thức để so sánh/ tính distance giữa hai image để
> có thể dùng KNN. Thì đơn giản nhất là dùng **L1 distance** hay
> **Manhattan distance.** Cơ bản nó là **tổng pixel wise difference giữa
> hai image**. Tức là lấy hai tensor trừ nhau và sum lại

<br>

<a id="node-3lf6d89"></a>

<p align="center"><kbd><img src="assets/fkkdfzd0bm.png" width="80%"></kbd></p>

<br>

<a id="node-hxfhgdc"></a>

<p align="center"><kbd><img src="assets/bjbjn2umha8.png" width="80%"></kbd></p>

> [!NOTE]
> Thì code cho KNN model rất đơn giản, đại khái là nó nhớ / giữ
> nguyên bộ training dataset. (self.Xtr = X,  self.ytr = y). Khi inference
> (make prediction) thì chỉ việc là nó tính difference giữa các image
> vector (là các row của Xtr) và image cần predict sau đó lấy cái
> class nào mà difference nhỏ nhất.
>
>
>
> Cụ thể là loop trong N = X.shape[0] image cần predict (tensor X)
> với mỗi image X[i,:] , tính difference của các image trong Xtr Xtr -
> X[i,:] sẽ ra được một matrix MxN trong đó mỗi row là vector chứa N
> item là hiệu của vector Xtr[i,:] và X[i,:]
>
>
>
> Xong mới tính abs thì cơ bản là lấy trị tuyệt đối mọi vị trí, và sum
> axis = 1 để sum theo từng row để thành ra 1 vector cột N item, mỗi
> vị trí là L1 distance giữa các image trong Xtr và X[i,:].
>
>
>
> Và cuối cùng lấy argmin để ra cái index mà có distance nhỏ nhất,
> đối chiếu với ground true ytr (là vector cột N item chứa label của
> các image row vector trong Xtr) để kết luận.
>
>
>
> Vậy tóm lại cách này là nó xem trong bộ training data, cái hình con
> gì có L1 distance nhỏ nhất với cái image cần classify thì cho nó là
> con  đó.

<br>

<a id="node-396b7tq"></a>

<p align="center"><kbd><img src="assets/81zaphj5rr9.png" width="80%"></kbd></p>

<br>

<a id="node-klxojid"></a>

<p align="center"><kbd><img src="assets/u839gjr2do.png" width="80%"></kbd></p>

<br>

<a id="node-9oj7i7m"></a>

<p align="center"><kbd><img src="assets/vd3q8bwjhnh.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy câu hỏi là Training và Inference  Big O mấy.
>
>
>
> Thì rõ ràng training chả làm gì, O(1), có 1 triệu dataset
> cũng O(1) = 1 bước nhớ (save) Xtr, ytr.
>
>
>
> Nhưng inference thì với mỗi image cần prediction, ta phải
> tính N chỉ số distance của nó với các image trong Xtr.
> nên nó là O(N)
>
>
>
> ====
>
>
>
> Thì ổng nói đại khái điều này không ổn, vì ta muốn inference 
> phải nhanh nhưng training thì có thể chậm được.

<br>

<a id="node-f38cloc"></a>

<p align="center"><kbd><img src="assets/rlcw2e7i1m.png" width="80%"></kbd></p>

<br>

<a id="node-kdh49hf"></a>

<p align="center"><kbd><img src="assets/7mrzim52agw.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là plot ra kết quả nó như thế này, nhận xét có nhiều cái
> chưa ổn, như cái ốc đảo màu vàng trong đám màu xanh trong khi
> khả năng cao là nó thuộc class màu xanh luôn., và cái pattern
> kiểu ngón tay (finger shape)

<br>

<a id="node-4eepr72"></a>

<p align="center"><kbd><img src="assets/t51z0j1b6g.png" width="80%"></kbd></p>

> [!NOTE]
> Vì vậy thay vì dùng Nearest Neighbor tức chỉ "lấy thằng gần nhất" (để dùng
> class của nó để gán cho cái cần predict) thì ta có thể **dùng voting result
> của K thằng gần nhất**, ví dụ **10 cái, và xem trong 10 cái đó, class nào chiếm
> số đông** thì lấy gán cho các cần predict. Đó chính là KNN classifier.
>
>
>
> Kết qủa là với K lớn hơn thì các vấn đề ốc đảo và finger swap không còn
> decision boundary đã kiểu như smooth hơn

<br>

<a id="node-6bgzffu"></a>

<p align="center"><kbd><img src="assets/6j4pam4srh2.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây in thử ra prediction của
> các image,

<br>

<a id="node-m6oqdl6"></a>

<p align="center"><kbd><img src="assets/7fujktkhoz5.png" width="80%"></kbd></p>

> [!NOTE]
> Thì thấy nó dù là KNN thì
> performance cũng ko cao khi
> nhiều cái hình bị classify sai

<br>

<a id="node-k2ck3nc"></a>

<p align="center"><kbd><img src="assets/zwvdhowlcg.png" width="80%"></kbd></p>

> [!NOTE]
> Một vấn đề là nên dùng L1 distance hay L2 distance. Thì ổng nói là thật
> ra nên thử cả hai, nhưng nhưng intuitive đó là nếu các feature của vector
> có ý nghĩa cụ thể và ta quan trọng nó thì dùng L1, ví dụ vector feature của
> housing dataset, trong đó các item value có thể là diện tích, chiều dài, số
> phòng...tức là mỗi value có 1 ý nghĩa cụ thể
>
>
>
> còn nếu feature vector chỉ là các vector chung chung, trừu tượng trong
> không gian, nơi nà mỗi unit (dimension) không gắn với một ý nghĩa nào
> thì dùng L2. Trường hợp này thì giống như word embedding vector

<br>

<a id="node-3gkubhj"></a>

<p align="center"><kbd><img src="assets/gafugiwk3bj.png" width="80%"></kbd></p>

> [!NOTE]
> Đây là plotting của việc thử
> hai loại distance metric

<br>

<a id="node-8j3aqeq"></a>

<p align="center"><kbd><img src="assets/n3ldd7ysuxm.png" width="80%"></kbd></p>

> [!NOTE]
> Ổng nói có thể vọc vạch cái này - là cái page
> ổng làm để hiểu thêm KNN với các h.p khác
> nhau như L1 hay L2, số K sẽ ảnh hưởng đến
> kết quả như thế nào

<br>

<a id="node-a4wokob"></a>

<p align="center"><kbd><img src="assets/upgwzkef8ba.png" width="80%"></kbd></p>

> [!NOTE]
> Nói về hyperparams thì mình biết rồi, đại khái là
> nó không được train từ dataset mà là human chọn

<br>

<a id="node-1dvhi5j"></a>

<p align="center"><kbd><img src="assets/twka1cj0vu.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy câu hỏi là làm sao để chọn các
> hyperparams này: Hyperparam tuning.

<br>

<a id="node-4j2ca3l"></a>

<p align="center"><kbd><img src="assets/rzug6r4n4w.png" width="80%"></kbd></p>

> [!NOTE]
> Thì đại khái ideas 1 là chọn h.p sao cho training performance tốt
> nhất, thì ổng nói cách này là **bad ideas.** Vì mục đích tối thượng
> của ML là work trên new data không phải trên training set. Nếu
> dùng training set để h.p tuning thì sẽ **overfit**, nó work best trên
> trainning set nhưng chưa chắc trên new data

<br>

<a id="node-2s7ww9b"></a>

<p align="center"><kbd><img src="assets/sdkzz0k8zac.png" width="80%"></kbd></p>

<br>

<a id="node-b917x60"></a>

<p align="center"><kbd><img src="assets/9w6ys78wkij.png" width="80%"></kbd></p>

> [!NOTE]
> Ideas hai là chia làm trainning/test set. **Cũng bad ideas**, vì
> như vậy ta sẽ overfit với test set. Có nghĩa nó chỉ là bộ h.p 
> khiến model work best trên test set, chứ chưa chắc là tốt trên 
> new dataset.

<br>

<a id="node-ohb44bk"></a>

<p align="center"><kbd><img src="assets/3wwlynb0qt.png" width="80%"></kbd></p>

<br>

<a id="node-7rqo4zh"></a>

<p align="center"><kbd><img src="assets/ks6qd9ijm7.png" width="80%"></kbd></p>

> [!NOTE]
> Mà cách nên dùng là train/validation/test set. Train model trên
> training set, h.p trên validation set và chỉ **dùng test set để conclude
> model performance.**
>
>
>
> Nói chung nguyên tắc là **không đụng đến test set trong quá trình
> "làm"** mà chỉ dùng nó ở bước cuối để test model performance trước
> khi công bố

<br>

<a id="node-4dhkefw"></a>

<p align="center"><kbd><img src="assets/betnbt8wwyr.png" width="80%"></kbd></p>

> [!NOTE]
> Nói về một cái mà đã biết là **K-fold Cross-Validation**. K ở đây ví dụ 5 thì 
> Ta chỉ training data thành 4 phần, dùng 4 phần train model và 1 phần 
> còn lại để làm validation set cho việc h.p tuning.
>
>
>
> Thì họ nói cái này thường chỉ dùng cho small dataset, với deep learning thì
> không.

<br>

<a id="node-ny974sc"></a>

<p align="center"><kbd><img src="assets/mydudnqhwnb.png" width="80%"></kbd></p>

> [!NOTE]
> Thì đại khái là quá trình h.p tuning ta plot Performance theo h.p, như hình là
> K, từ đó chọn ra K tốt nhất. Như ở đây khoảng K = 7 là nó ok, cao hơn thì
> performance (cross-validation accuracy giảm dần)

<br>

<a id="node-o3dlamx"></a>

<p align="center"><kbd><img src="assets/1sjp13sjzmh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thật ra ta sẽ không xài cái KNN này vì những hạn chế của
> nó như chậm (inference), và performance cũng ko tốt.
>
>
>
> Như trong slide ổng nói là tui change cái hình đủ kiểu nhưng some
> how L2 distance vẫn không đổi. Ý là **L2 distance không phải là biểu
> thị tốt cho việc hai cái hình giống hay khác nhau về mặt nội dung.**

<br>

<a id="node-9gpevd4"></a>

<p align="center"><kbd><img src="assets/h7wako9m409.png" width="80%"></kbd></p>

> [!NOTE]
> Một vấn đề nữa cũng hay là T**he Curse Of Dimensionality.**
>
>
>
> Đại khái là cái KNN này work tốt thì không gian vector phải được lấp đầy data point
> Tuy nhiên, điều này rất khó.
>
>
>
> Vì ví dụ với 1D space thì chỉ 4 điểm là đủ để lấp đầy, qua 2D cần 4^2 = 16 điểm,
> qua 3D cần 4^3 = 64 điểm mới lấp đầy không gian.
>
>
>
> Vậy với image vector có hàng trăm, nghìn dimension (ví dụ hình 100x100 = 10000)
> thì để lấp đầy không gian thì phải có con số data point khổng lồ. Điều này là bất khả 
> thi, nôm na là không thể có nhiều data sample như vậy được.
>
>
>
> Thành ra trong image vector space, data nó phân bố rất trống trải (curse) nên KNN
> và vài dạng model khác không thể work tốt được

<br>

<a id="node-xusozdn"></a>

<p align="center"><kbd><img src="assets/3ztlo5bwtn3.png" width="80%"></kbd></p>

> [!NOTE]
> Tóm lại KNN classification đơn giản là giữ / hold toàn bộ training dataset.
> Sau đó khi inference, thì chỉ là predict class của một new sample dựa trên 
> class của K thằng gần nhất với nó.
>
>
>
> K và loại distance metric dùng là hyperparams, dùng validation set hoặc
> Cross-validation để tuning.

<br>

<a id="node-j1wrd9y"></a>

<p align="center"><kbd><img src="assets/3a2x71pg2fv.png" width="80%"></kbd></p>

<br>

<a id="node-bd7vlx7"></a>

### Mạng nơ-ron: Lắp ghép phân loại

<p align="center"><kbd><img src="assets/cjmd8agqi2.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái Neural network chỉ như là lắp
> ghép của nhiều Linear classifier

<br>

<a id="node-k51mntu"></a>

#### Ghép khối LEGO mô tả ảnh

<p align="center"><kbd><img src="assets/jca2vyfdjot.png" width="80%"></kbd></p>

> [!NOTE]
> Nói sơ về việc có thể ghép block các loại lego
> block khác nhau để làm cái image description
> model như này

<br>

<a id="node-v496ms7"></a>

##### Kết hợp CNN-RNN trong AI

<p align="center"><kbd><img src="assets/itmfrkit2yg.png" width="80%"></kbd></p>

> [!NOTE]
> Trong đó kết hợp CNN trong
> computer vision và RNN trong NLP

<br>

<a id="node-q3aeb00"></a>

- **Nghiên cứu bộ CIFAR10**

<p align="center"><kbd><img src="assets/3vmmae0oc7q.png" width="80%"></kbd></p>

> [!NOTE]
> QUay lại bộ CIFAR10.

<br>

<a id="node-hn985bg"></a>

- **Phân loại tuyến tính và KNN**

<p align="center"><kbd><img src="assets/zsw0gfpdowk.png" width="80%"></kbd></p>

> [!NOTE]
> Thì đại khái cái Linear Classification này là một cái **parametric model**, tức
> là có param.
>
>
>
> Khác với **KNN không có param**, chỉ là nhớ toàn bộ training set, còn ở đây
> kiểu như  dùng training để train ra param W, sau đó có thể vứt training set, và
> chỉ dùng những kiến thức thể hiện trong W để make prediction.

<br>

<a id="node-5drod4b"></a>

<p align="center"><kbd><img src="assets/hp6ksbmlyy8.png" width="80%"></kbd></p>

> [!NOTE]
> Và ở cấp đơn giản nhất Linear Classifier chỉ đơn giản là train một cái
> matrix W, để khi make prediction thì chỉ dot product Image vector với
> W để ra vector có 10 (no. classes) chứa 10 số (ko phải probability
> nhé, vì chưa có activation function e.g softmax) tạm gọi là class scores.

<br>

<a id="node-fkapcve"></a>

<p align="center"><kbd><img src="assets/2pw68uhwn4e.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ image 32x32x3 (ảnh màu) thì flatten ra thành 3072D vector,
> Thì W sẽ có shape = 10x3072, để khi tính f = Wx sẽ được 10D vector.

<br>

<a id="node-9igq6pt"></a>

<p align="center"><kbd><img src="assets/2j9vqyjs18a.png" width="80%"></kbd></p>

> [!NOTE]
> Có thể cộng thêm bias b,
> cũng là vector 10 unit

<br>

<a id="node-0gt4n2o"></a>

<p align="center"><kbd><img src="assets/bkqezh9mysc.png" width="80%"></kbd></p>

> [!NOTE]
> Sau quá trình training thì kiểu như mỗi hàng của W sẽ biểu thị/là pattern
> indicator của một class,  Image feature vector khi nhân với từng hàng (Wx)
> sẽ ra các class score.

<br>

<a id="node-8pg6oqb"></a>

<p align="center"><kbd><img src="assets/56f9fsviv3f.png" width="80%"></kbd></p>

<br>

<a id="node-ley4zob"></a>

- **Ý nghĩa hàng ma trận W**

<p align="center"><kbd><img src="assets/r1foriodu4.png" width="80%"></kbd></p>

> [!NOTE]
> Thì ổng nói là có thể in mỗi hàng của W ra, vốn bằng shape với image
> feature vector (3071) và reshape lại và in ra xem thử thì đại khái là
>
>
>
> Ta có thể thấy model nó tweak các row của W  sao đó khiến nó kiểu
> như ..khó diễn tả nhưng với linear model, ta nên nhớ rằng kết quả
> class score sẽ chỉ là phép dot product của feature vector và W's row
> vector. Nên model sẽ dần dần tweek các row vector này sao cho nó
> mang dáng dấp chung chung của cái class tương ứng
>
>
>
> Nói chung ở đây ổng chưa nói cách train, và cũng sẽ không dùng kiểu
> này vì linear classification không work tốt

<br>

<a id="node-t6fi6cz"></a>

<p align="center"><kbd><img src="assets/277xgeda45k.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dễ thấy linear classification không
> thể work tốt với bài toán image classification
> được vì nó quá đơn giản

<br>

<a id="node-xyskkju"></a>

<p align="center"><kbd><img src="assets/gnl90s2o5n.png" width="80%"></kbd></p>

> [!NOTE]
> Dễ dàng chế ra vài bộ dataset có thể khiến linear
> classification fail hoàn toàn

<br>

<a id="node-gkx2w51"></a>

<p align="center"><kbd><img src="assets/dko6lbw95uv.png" width="80%"></kbd></p>

<br>

<a id="node-k5m29bu"></a>

<p align="center"><kbd><img src="assets/f0mn6bravzu.png" width="80%"></kbd></p>

> [!NOTE]
> Thì qua tuần sau sẽ nói về việc train linear
> classifier với loss function, optimization
> (gradient descent) và ConvNet

<br>

