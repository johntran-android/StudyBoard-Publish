# C4w3_object Detection

📊 **Progress:** `59` Notes | `138` Screenshots

---
<a id="node-r4ci5qm"></a>

## C4w3_object Detection

<br>

<a id="node-tw3mvr9"></a>

## Object Localization

<br>

<a id="node-32fe5z1"></a>

> [!NOTE]
> Đại khái là bài toán bây giờ là không những chỉ phân loại -vd. có phải
> xe hơi hay không (**classification)** mà còn vẽ cái box xung quanh cái
> xe (**classification with localization)**. Và mở rộng hơn là detect nhiều
> object khác loại trên cùng 1 image (**Object detection**)
>
> Đại khái là muốn localize thì ta **sửa cái output layer**, v.d đang là 
> Softmax ra 4 unit tương ứng 4 loại khả dĩ của cái hình, để
> **thêm vào 4 chỉ số nữa là bx, by, bw, bh** = Vị trí của cái object.
>
> Bằng cách **có thêm 4 thông số này trong training set,** đại khái
> là ta có thể khiến cho network có thể học được cách xác định
> được 4 chỉ số này trong các mẫu mới -> Localize được cái xe.
>
> Đại khái là label (y) ngoài 4 unit (để chỉ ra 4 loại xe, người,
> moto, nền, hoặc 4 thông số probability tương ứng) thì bây
> giờ sẽ có thêm  Pc - 1 là object, 0 là nền (bx, by, bh, bw) -
> vị trí cái object nếu có hoặc bỏ trống (?) nếu không, và C1
> C1 C3 - class label hoặc Probability class
>
> Cuối cùng là define Loss function có thể dùng **square của
> từng cặp tương ưng giữa y^ và y** hoặc kĩ hơn thì dùng
> từng hàm khác nhau  đ/v các chỉ số khác nhau như
>
> - Binary Cross Entropy đ.v pC,
> - Squared Error đ.v bx, by, bh, bw
> - Log (Categorical Cross Entropy) đ.v C1, C2, C3

<br>

<a id="node-tk6kqaf"></a>

<p align="center"><kbd><img src="assets/lgvkltrkewl.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bài toán bây giờ là không những chỉ phân loại -vd. có phải
> xe hơi hay không (**classification)** mà còn vẽ cái box xung quanh cái
> xe (**classification with localization)**. Và mở rộng hơn là detect nhiều
> object khác loại trên cùng 1 image (**Object detection**)

<br>

<a id="node-hmridoz"></a>

<p align="center"><kbd><img src="assets/v9rcyj935d.png" width="80%"></kbd></p>

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

<a id="node-u5664mm"></a>

<p align="center"><kbd><img src="assets/5mk7uys4a1f.png" width="80%"></kbd></p>

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

<a id="node-zekerc7"></a>

## Landmark Detection

<br>

<a id="node-nw89z3r"></a>

> [!NOTE]
> Đại khái là ta có thể dạy cho máy tính cách xác định các key point
> trên khuôn mặt bằng cách tạo unit của output layer cho 'toạ độ' của
> các  điểm đó l1x, l1y, l2x, l2y....
>
> Dĩ nhiên label (Y train) cũng phải có những landmark này và công
> việc xác định các điểm này tốn nhiều công sức (**laborious**)
>
> Ứng dụng của cái này lấy ví dụ như chuyển khuôn mặt cười thành
> khóc, những hiệu ứng của Snapchat như đội nón đều dựa trên
> việc xác định được các landmark của khuôn mặt. **Recognize emotion**
>
> Một ví dụ khác là xác định bộ khung - tư thế người.

<br>

<a id="node-033zcnl"></a>

<p align="center"><kbd><img src="assets/tk2ui3lcv7c.png" width="80%"></kbd></p>

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

<a id="node-kgv6sy9"></a>

## Object Detection

<br>

<a id="node-nho8xhj"></a>

> [!NOTE]
> Đại khái là chạy (sliding) check từng ô đó xem có phải là xe hay không
> (bằng cách bỏ vào bài toán classification).
>
> Nhưng nhược điểm là với Deep Learning thì cách làm kiểu Sliding
> Window này rất **tốn computational resource**.
>
> Cách này đã có từ lâu khi Machine Learning còn thô sơ và người ta dùng
> với very simple algorithm như Linear regression và nó cũng tạm được.
>
> Nhưng h n.n với ConvNet rất tốn kém nên cách này không dùng được

<br>

<a id="node-i10dp8w"></a>

<p align="center"><kbd><img src="assets/idubffrpciq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là đầu tiên người ta train 1
> convNet để classify xe trước với các
> training set là hình xe crop sát với cái xe

<br>

<a id="node-x7l1tp1"></a>

<p align="center"><kbd><img src="assets/0e0i26b499ud.png" width="80%"></kbd></p>

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

<a id="node-9pqws7z"></a>

> [!NOTE]
> CONVOLUTIONAL IMPLEMENTATION
> OF SLIDING WINDOWS

<br>

<a id="node-eh5lawe"></a>

> [!NOTE]
> Đại khái là có thể thay cái 400 unit FC layer bằng Conv layer
> 1x1x400 bằng cách dùng 400 filter 5x5x16. Về mặt toán học tính
> toán thì như nhau.
>
> Tương tự với layer softmax
>
> Vi diệu
>
> Đại khái là thay vì dùng **sliding window** để cắt ra từng ô rồi bỏ
> vào convNet để forward ra 1 kết quả xem có phải cái xe hay
> không, làm vậy phải slide và forward 4 lần
>
> Thay vì vậy, **cứ bỏ cái hình bự vào luôn** dùng cái **convNet**
> nó sẽ tính ra kết quả cuối cùng chính là **chứa đựng kết quả của
> 4 lần riêng lẻ.**

<br>

<a id="node-e43qxkt"></a>

<p align="center"><kbd><img src="assets/06c3j8u6zc8j.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là có thể thay cái 400 unit FC layer bằng
> Conv layer 1x1x400 bằng cách dùng 400 filter
> 5x5x16. Về mặt toán học tính toán thì như nhau.
>
>
>
> Tương tự với layer softmax

<br>

<a id="node-dmptz6m"></a>

<p align="center"><kbd><img src="assets/h55gpthqrf9.png" width="80%"></kbd></p>

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

<a id="node-m79t35p"></a>

<p align="center"><kbd><img src="assets/8n6tda4xqpq.png" width="80%"></kbd></p>

<br>

<a id="node-txcpesc"></a>

## Bounding Box Predictions

<br>

<a id="node-svk15sp"></a>

> [!NOTE]
> 1 Sliding windows have a **problem with accurate bounding box**
> predictions **even with a convolutional implementation.**
>
> 2 The **YOLO** (You Only Look Once) algorithm offers a way to **output
> more accurate bounding boxes** by **applying image classification and
> localization algorithms** to a grid system.
>
> 3 The grid system divides the input image into cells, and for each
> cell, a target label vector Y is defined, with the first output
> representing whether there is an image in that grid cell.
>
> 4 **The target label vector Y includes PC, BX, BY, BH, BW** to specify
> the bounding box and C1, C2, C3 to specify the object class.
>
> 5 The total volume of the target output is 3 by 3 by 8 because the
> image is divided into a 3 by 3 grid system, and for each grid cell,
> there is an eight-dimensional target vector Y.
>
> 6 To train the neural network, the input is the image, and the output
> is the target label vector Y.

<br>

<a id="node-11grk5v"></a>

<p align="center"><kbd><img src="assets/br3kve6g98r.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là làm sao để detect chính xác **bounding box -** một
> problem của Sliding window dù cho có áp dụng **Convolutional
> implementation vẫn chưa khắc phục được**. Kiểu như có thể B.B đúng phải hình chữ nhật nhưng window chỉ
> có hình vuông nên ko thể chính xác được

<br>

<a id="node-aj131xi"></a>

<p align="center"><kbd><img src="assets/ablsc2pdtk6.png" width="80%"></kbd></p>

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

<a id="node-95lzfz7"></a>

<p align="center"><kbd><img src="assets/tmiqcayzwud.png" width="80%"></kbd></p>

<br>

<a id="node-dlgnmc4"></a>

## Intersection Over Union

<br>

<a id="node-eg57ag6"></a>

> [!NOTE]
> Đại khái là tính ra chỉ số **Itersection / Unit (giao hợp)** và quyết
> định môt threshold để xem nó có correct hay không
>
> 1 Introduction to Intersection Over Union (IoU) function for
> evaluating object detection algorithms.
>
> 2 IoU computes the overlap between the ground-truth bounding
> box and the predicted bounding box.
>
> 3 Conventionally, an IoU of 0.5 or greater is considered correct,
> but more stringent criteria can also be used.
>
> 4 IoU can be used to measure the overlap between any two
> bounding boxes and is a way to measure similarity.
>
> 5 IoU is used in non-max suppression, which is a tool to improve
> the performance of object detection algorithms.
>
> 6 IoU is not to be confused with the promissory note concept in
> IoU.

<br>

<a id="node-shezjol"></a>

<p align="center"><kbd><img src="assets/5o9lfp9wzxc.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tính ra chỉ số Itersection / Unit (giao hợp)
> và quyết định môt threshold để xem nó có correct hay 
> không
>
>
>
> Thường ta lấy 0.5 nhưng có thể tăng lên nếu muốn strict hơn

<br>

<a id="node-j4v75px"></a>

## Non-max Suppression

<br>

<a id="node-entrdj3"></a>

> [!NOTE]
> Main ideas:  1 Object detection algorithms may find multiple
> detections of the same object.
>
> 2 Non-max suppression is a method to ensure that object
> detection algorithms only detect each object once.
>
> 3 Non-max suppression works by **selecting the most confident
> detection** and then **suppressing overlapping detections.**
>
> 4 The first step of non-max suppression is to **discard all boxes
> with a probability less than or equal to some threshold.**
>
> 5 The next step is to repeatedly **pick the box with the highest
> probability** and **output it as a prediction** and **suppress all box
> that overlap it** until there are no more boxes left.

<br>

<a id="node-32h41bh"></a>

<p align="center"><kbd><img src="assets/nqz4j31azvh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là trong quá trình có thể nhiều cell cùng detect rằng nó
> chứa center của cái xe từ đó thành ra nó detect cái xe nhiều lần

<br>

<a id="node-lq1smtj"></a>

<p align="center"><kbd><img src="assets/ivr563wmc8.png" width="80%"></kbd></p>

> [!NOTE]
> Cái Non-max Suppresion sẽ làm là với mỗi object, nó xác định cái B.B
> có Pc lớn nhất và xác định các b.b khác mà overlap nhiều với cái đầu
>
>
>
> Cái tên thể hiện hết: Suppression - Bỏ đi, Non-max là không  phải cái lớn
> nhất (về Probability).

<br>

<a id="node-rvzk1ye"></a>

<p align="center"><kbd><img src="assets/5b5yaixte0b.png" width="80%"></kbd></p>

<br>

<a id="node-qr97hwl"></a>

<p align="center"><kbd><img src="assets/o6hommtu8xi.png" width="80%"></kbd></p>

<br>

<a id="node-kwjnmsd"></a>

<p align="center"><kbd><img src="assets/h8genesgtro.png" width="80%"></kbd></p>

<br>

<a id="node-fz03vst"></a>

<p align="center"><kbd><img src="assets/xjk7cn560c.png" width="80%"></kbd></p>

<br>

<a id="node-wnxqwzc"></a>

## Anchor Boxes

<br>

<a id="node-ev61tpi"></a>

> [!NOTE]
> 1 Object detection with grid cells has a **limitation of detecting only
> one object per cell**.
>
> 2 Anchor boxes are **pre-defined shapes used to associate multiple
> predictions with different anchor boxes.**
>
> 3 Anchor boxes **allow for detecting objects with different shapes
> and sizes in a single grid cell**.
>
> 4 The **target label** with anchor boxes consists of a **3 by 3 grid and
> anchor box pair, with each pair containing 8 dimensions for object
> detection.**
>
> 5 Anchor boxes are assigned to the same grid cell as before, but
> with the highest Intersection over Union (IoU) with the object's
> shape. -> ???
>
> 6 The output Y is 3 by 3 by 16 with two anchor boxes or 3 by 3 by
> 24 with three anchor boxes.
>
> 7 Anchor boxes allow for better object detection and localization
> within a single grid cell.

<br>

<a id="node-31trxyk"></a>

<p align="center"><kbd><img src="assets/zs16h6xnytj.png" width="80%"></kbd></p>

<br>

<a id="node-kf4p58h"></a>

<p align="center"><kbd><img src="assets/9bo2wlmokyf.png" width="80%"></kbd></p>

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

<a id="node-mx6r6tu"></a>

<p align="center"><kbd><img src="assets/7s2uw6ik0pt.png" width="80%"></kbd></p>

> [!NOTE]
> Chưa hiểu lắm, hiểu là anchor box nó define
> như vậy nhưng cụ thể làm gì thì chưa rõ

<br>

<a id="node-zpe4lbl"></a>

## Yolo Algorithm

<br>

<a id="node-czc593x"></a>

> [!NOTE]
> 1 The YOLO object detection algorithm combines various components of
> object detection.
>
> 2 To construct the training set, the appropriate **target vector y is formed
> for each of the nine grid cells.**
>
> 3 The final output volume is 3 by 3 by 16, but in practice, it may be more
> like 19 by 19 by 16 or 19 by 19 by 24 if more anchor boxes are used.
>
> 4 The neural network makes predictions by outputting a 3 by 3 by 2 by 8
> volume, where for each of the nine grid cells, a vector is obtained.
>
> 5 Non-max suppression is run to get rid of low probability predictions, and
> independently run non-max suppression for each of the three classes of
> objects to detect pedestrians, cars, and motorcycles.

<br>

<a id="node-ul56r3t"></a>

<p align="center"><kbd><img src="assets/qq9g0xsa9g.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là training label sẽ có dạng như vậy với 2 object là
> (3x3) x (số anchor) x (5 + số class) Thực tế có thể là 19x19

<br>

<a id="node-34xswbg"></a>

<p align="center"><kbd><img src="assets/6k1fkpv6zvm.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi sau khi train, và predict new image thì: Chỉ số đầu pc
> của mỗi cell sẽ cho biết có object hay không, Nếu có thì
> các thông số sẽ là vị trí và class của nó

<br>

<a id="node-le0ngby"></a>

<p align="center"><kbd><img src="assets/g2lliwx4m8p.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/a53mmt1ib6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/8y5zpuws38t.png" width="80%"></kbd></p>

<br>

<a id="node-ido7lnb"></a>

<p align="center"><kbd><img src="assets/zsey9p4o1wj.png" width="80%"></kbd></p>

> [!NOTE]
> Xong tiếp theo là làm quy trình non-max
> đv mỗi class để xoá đi các bounding box

<br>

<a id="node-iz08qk0"></a>

## Region Proposals

<br>

<a id="node-zn1ga3d"></a>

> [!NOTE]
> 1 Introduction to region proposals in object detection
>
> 2 Comparison between sliding windows and region
> proposals
>
> 3 R-CNN algorithm and its implementation of region
> proposals
>
> 4 Improvements to the R-CNN algorithm, including Fast
> R-CNN and Faster R-CNN
>
> 5 The influence of region proposals in computer vision
>
> 6 The potential for a single-step approach in object
> detection, similar to the You Only Look Once (YOLO)
> algorithm.

<br>

<a id="node-sshhqm2"></a>

<p align="center"><kbd><img src="assets/cbe9y7o4ikn.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái idea là thay vì chạy (Sliding window + classification) hoặc Sliding
> window with ConvNet, trong đó ta đều check những cell mà rõ ràng là
> không có khả năng có object, thì ta sẽ dùng một cái gọi là **Segmentation
> algorithm** để xác định các **vùng có khả năng có object nhất sau đó chỉ
> run trên những vùng này**

<br>

<a id="node-6i1njff"></a>

<p align="center"><kbd><img src="assets/wn72alulhg.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái cái R-CNN nó chậm do bước
> Region Proposal  nên có vài cách khác
> dùng Conv để tăng tốc việc này.

<br>

<a id="node-v8txocl"></a>

## Semantic Segmentation With U-net

<br>

<a id="node-1o45f90"></a>

> [!NOTE]
> 1. Semantic segmentation là gì?
>
> Semantic segmentation là một kỹ thuật thị giác máy tính liên quan đến gán nhãn cho mỗi
> pixel trong hình ảnh với một nhãn lớp tương ứng. Mục tiêu của semantic segmentation là
> tạo ra một đường viền chi tiết của một đối tượng, để chúng ta biết chính xác những pixel
> thuộc về đối tượng và những pixel nào không thuộc về đối tượng đó.
>
> 2. Ứng dụng của semantic segmentation:
>
> Semantic segmentation có nhiều ứng dụng thương mại, bao gồm xe tự lái, hình ảnh y học
> và lập kế hoạch phẫu thuật. Ví dụ, trong xe tự lái, semantic segmentation có thể được sử
> dụng để xác định các bề mặt lái được, giúp cho xe dễ dàng di chuyển.
>
> 3.Làm thế nào semantic segmentation hoạt động?
>
> Trong semantic segmentation, mục tiêu là gán nhãn lớp cho mỗi pixel trong hình ảnh. Để
> làm được điều này, chúng ta cần sửa đổi kiến trúc của một mạng neural tích chập (CNN).
> Các lớp cuối cùng của CNN được loại bỏ và mạng được sửa đổi để tăng dần kích thước
> đầu ra, sao cho nó phù hợp với kích thước của hình ảnh đầu vào.
>
> 4.Làm thế nào để phân đoạn hình ảnh bằng semantic segmentation?
>
> Để phân đoạn một hình ảnh bằng semantic segmentation, CNN tạo ra một ma trận nhãn
> lớp cho mỗi pixel trong hình ảnh. Số hàng và cột trong ma trận tương ứng với chiều cao và
> chiều rộng của hình ảnh đầu vào, trong khi số kênh tương ứng với số nhãn lớp. Ví dụ, nếu
> chúng ta muốn phân đoạn một hình ảnh thành các ô tô và tòa nhà, chúng ta sẽ có hai kênh:
> một cho ô tô và một cho tòa nhà.
>
> 5.Transpose convolution:
>
> Để tăng kích thước ma trận đầu ra trong semantic segmentation, chúng ta sử dụng một
> phép toán gọi là transpose convolution. Transpose convolution được sử dụng để "hoàn
> ngược" quá trình giảm mẫu xuất hiện ở các lớp trước của CNN. Đầu ra của một transpose
> convolution có cùng hình dạng với đầu vào, nhưng v

<br>

<a id="node-p0hse8i"></a>

<p align="center"><kbd><img src="assets/9f4rg9glo95.png" width="80%"></kbd></p>

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

<a id="node-emejxl8"></a>

<p align="center"><kbd><img src="assets/wxp0zmuu1k.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là một số ứng dụng của cái
> này, sẽ giúp ích rất nhiều

<br>

<a id="node-as0l5we"></a>

<p align="center"><kbd><img src="assets/odzrafrc8jd.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/2irt4mop81d.png" width="80%"></kbd></p>

> [!NOTE]
> N.n phải output 1 matrix như này: mỗi pixel
> trong image đều được label

<br>

<a id="node-15mmkck"></a>

<p align="center"><kbd><img src="assets/vmycrdjpqt.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qxwxtegyb0q.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là để làm segmentation phải thay mấy cái layer cuối theo kiểu
> tăng cái size lên như này để về lại size ban đầu của input image. Cái này
> cần tới **Transpose Operation**

<br>

<a id="node-sfdne4r"></a>

## Transpose Convolutions

<br>

<a id="node-ogmz3k7"></a>

> [!NOTE]
> Trong bài giảng này, người giảng giải thích về khái niệm transpose
> convolution, là một phần quan trọng trong kiến trúc đơn vị. Để làm
> cho đầu vào kích thước 2x2 được phóng to lên kích thước 4x4, ta
> có thể sử dụng transpose convolution. Khác với convolution thông
> thường, transpose convolution sử dụng một bộ lọc (filter) để phóng
> to dữ liệu đầu ra thay vì áp dụng bộ lọc lên đầu vào. Bài giảng cung
> cấp một ví dụ chi tiết về cách sử dụng transpose convolution với
> đầu vào 2x2, bộ lọc 3x3, padding 1 và stride 2 để phóng to đầu vào
> thành đầu ra 4x4. Một vài bước tính toán được trình bày để minh
> họa quá trình phóng to. Cuối cùng, transpose convolution được cho
> là một cách hiệu quả để phóng to dữ liệu đầu vào nhỏ hơn lên kích
> thước lớn hơn trong bối cảnh của thuật toán học sâu.

<br>

<a id="node-celvmrd"></a>

<p align="center"><kbd><img src="assets/ax1yvle6wq.png" width="80%"></kbd></p>

<br>

<a id="node-zzrqfzz"></a>

<p align="center"><kbd><img src="assets/kfvefkhp4ra.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vewq8irq8wr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/e2tpzugsxv.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vjarifzk09p.png" width="80%"></kbd></p>

<br>

<a id="node-l7zodqk"></a>

<p align="center"><kbd><img src="assets/ada7zyx5ko8.png" width="80%"></kbd></p>

<br>

<a id="node-hsmprdy"></a>

## U-net Architecture Intuition

<br>

<a id="node-p5733dv"></a>

> [!NOTE]
> - Đại khái là sử dụng **convolution thông thường phần
> đầu** của mạng nơ-ron.
>
> - Sử dụng **transpose convolution trong phần thứ hai
> của mạng nơ-ron để khôi phục lại kích thước ảnh gốc.**
>
> - Giới thiệu **skip connections** từ các lớp trước đến
> các lớp sau để cải thiện hiệu suất bằng cách **cung cấp
> thông tin bối cảnh cấp cao và thông tin kết cấu cấp
> thấp** để cho phép mạng nơ-ron bắt được thông tin
> không gian chi tiết, tinh vi.

<br>

<a id="node-44n2m6g"></a>

<p align="center"><kbd><img src="assets/d6xyc48pd1m.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dùng Transpose Conv ở những layer cuối và **Skip
> Connection** cho phép cung cấp **những low-level feature nhưng
> chi tiết** để cộng với những **high-level feature nhưng chung
> chung** để tạo nên kết quả cuối cùng

<br>

<a id="node-gyv5nq9"></a>

## U-net Architecture

<br>

<a id="node-knq7rkt"></a>

> [!NOTE]
> 1. Qua 1 vài lớp Conv layer (Conv Relu) giữ nguyên kích thước  (với
> same padding) nhưng tăng dimensions (tăng số filter lên)
>
> 2,3,4. Dùng (Max) Pooling, giảm kích thước xuống rồi lại qua vài lớp
> Conv-reLu để tăng dimension
>
> 5. Dùng Transpose Conv để (chưa tăng kích thước) mà giảm
> dimensions xuống rồi ghép với cái Skip Connection từ bước 4.
>
> 6,7,8. Dùng Transpose Conv để tăng kích thước + giảm dimensions
> xuống rồi ghép với cái Skip Connection từ bước 3,2,1
>
> 9. Dùng Conv ReLU cho những layer cuối lúc này kích thước đã  phục hồi ban
> đầu, layer cuối dùng Conv (1x1) để xuất ra kết quả cuối cùng.

<br>

<a id="node-w7z70eg"></a>

<p align="center"><kbd><img src="assets/8urpqa1atb7.png" width="80%"></kbd></p>

> [!NOTE]
> Đây là một trong những cái kết trúc
> neural network nền tảng quan trọng
> nhất của Computer Vision

<br>

<a id="node-vts59xp"></a>

<p align="center"><kbd><img src="assets/0msikm0ksbcq.png" width="80%"></kbd></p>

<br>

<a id="node-k2t06gl"></a>

<p align="center"><kbd><img src="assets/4xainrken2.png" width="80%"></kbd></p>

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

<a id="node-0xmmtvt"></a>

## Quiz

<br>

<a id="node-apyc7hf"></a>

<p align="center"><kbd><img src="assets/7dgrw3zk4xi.png" width="80%"></kbd></p>

<br>

<a id="node-edzcu2j"></a>

<p align="center"><kbd><img src="assets/70md00oj98d.png" width="80%"></kbd></p>

<br>

<a id="node-ucfda4d"></a>

<p align="center"><kbd><img src="assets/udtzzglg23.png" width="80%"></kbd></p>

<br>

<a id="node-rdnlw5p"></a>

<p align="center"><kbd><img src="assets/ik2im78dfga.png" width="80%"></kbd></p>

<br>

<a id="node-nzvpa0z"></a>

<p align="center"><kbd><img src="assets/aswqbqddhho.png" width="80%"></kbd></p>

<br>

<a id="node-924rngs"></a>

<p align="center"><kbd><img src="assets/rydr92myqxa.png" width="80%"></kbd></p>

<br>

<a id="node-zshf8kx"></a>

<p align="center"><kbd><img src="assets/lsso7xewjn.png" width="80%"></kbd></p>

<br>

<a id="node-1hoxtgl"></a>

<p align="center"><kbd><img src="assets/7mfp7ksuygs.png" width="80%"></kbd></p>

<br>

<a id="node-o81safm"></a>

<p align="center"><kbd><img src="assets/pdfkvzca6fq.png" width="80%"></kbd></p>

<br>

<a id="node-hn5hfk1"></a>

<p align="center"><kbd><img src="assets/cz6r0x7b197.png" width="80%"></kbd></p>

<br>

<a id="node-v24qsia"></a>

## Programming Assignment

<br>

<a id="node-b26h0kt"></a>

<p align="center"><kbd><img src="assets/6klzs1ovgde.png" width="80%"></kbd></p>

> [!NOTE]
> By the end of this assignment, you'll be able to:
>
> Detect objects in a car detection dataset
> Implement non-max suppression to increase accuracy
> Implement intersection over union
> Handle bounding boxes, a type of image annotation popular in deep learning

<br>

<a id="node-dkntm00"></a>

#### \\*..\\*

<br>

<a id="node-vb0rmtz"></a>

##### Packages

<br>

<a id="node-53jj3qb"></a>

<p align="center"><kbd><img src="assets/2cniprbeo6w.png" width="80%"></kbd></p>

<br>

<a id="node-2c0a8kz"></a>

##### 1 - Problem Statement

<br>

<a id="node-q5w5b9p"></a>

<p align="center"><kbd><img src="assets/8yrk4s521xc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sdv6i6dy3va.png" width="80%"></kbd></p>

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

<a id="node-019imvt"></a>

##### 2 - Yolo

<br>

<a id="node-ntlw3of"></a>

> [!NOTE]
> YOLO: Đại khái là nó (algorithm) chỉ cần look qua cái
> image 1 lầnm lúc forward  propagation để predict

<br>

<a id="node-lj71t4w"></a>

- **2.1 - Model Details**

<br>

<a id="node-ndsoyqy"></a>

<p align="center"><kbd><img src="assets/xj3fc1vyki.png" width="80%"></kbd></p>

<br>

<a id="node-eczp2vw"></a>

<p align="center"><kbd><img src="assets/ewaqh22tv5w.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/kh16s57e45.png" width="80%"></kbd></p>

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

<a id="node-41h75b6"></a>

<p align="center"><kbd><img src="assets/oesgggnrx9g.png" width="80%"></kbd></p>

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

<a id="node-lvs0vc0"></a>

<p align="center"><kbd><img src="assets/iqov0td5y9g.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/1r8v4os5xe3.png" width="80%"></kbd></p>

<br>

<a id="node-04lxj7b"></a>

> [!NOTE]
> 2.2 - Filtering with a Threshold on Class Scores
>
> Đại khái là thay vì để chung các thông số của 1 box trong 1 vector
>
> [Pc, bx, by, bh, bw, c1, c2...c80]
>
> thì ta chia ra thành 3 vector:
>
> - Box confidence: Pc
>
> - Boxes: bx, by, bh, bw
>
> - Boxes class probability: c1, c2, ...c80
>
> 19x19x (số box) x (1 object probability + 4 thông số vị trí object
>
> + 80 thông số class prob)
>
> tách thành
>
> - Box confidence: 19x19x (số box) x (1 object probability)
>
> - Boxes: bx, by, bh, bw: 19x19x (số box) x (4 thông số vị trí object)
>
> - Boxes class probability: c1, c2, ...c80: 19x19x (số box) x (80 thông
> số class prob)

<br>

<a id="node-mua8n5t"></a>

<p align="center"><kbd><img src="assets/6r82v04gstc.png" width="80%"></kbd></p>

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

<a id="node-n4kkdzk"></a>

<p align="center"><kbd><img src="assets/71jsmp7f3k4.png" width="80%"></kbd></p>

<br>

<a id="node-khq2ytb"></a>

- **Exercise 1 - yolo_filter_boxes**

<br>

<a id="node-uku1u9j"></a>

<p align="center"><kbd><img src="assets/dx5n5intunw.png" width="80%"></kbd></p>

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

<a id="node-hi132ov"></a>

<p align="center"><kbd><img src="assets/3cmbbzj81t1.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/99rleca00hc.png" width="80%"></kbd></p>

<br>

<a id="node-ywod4z3"></a>

<p align="center"><kbd><img src="assets/m3m28lva64d.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/5g2gclhm0dm.png" width="80%"></kbd></p>

<br>

<a id="node-pmq5wuw"></a>

<p align="center"><kbd><img src="assets/6tjyfkxii2o.png" width="80%"></kbd></p>

<br>

<a id="node-38dnzv5"></a>

<p align="center"><kbd><img src="assets/5nsmg9qy3z.png" width="80%"></kbd></p>

<br>

<a id="node-fpf1ned"></a>

- **2.3 - Non-max Suppression**

<br>

<a id="node-xx4ce5y"></a>

<p align="center"><kbd><img src="assets/3b4mcp6685b.png" width="80%"></kbd></p>

<br>

<a id="node-ki559jw"></a>

- **Exercise 2 - iou**

<br>

<a id="node-e4cu1gn"></a>

<p align="center"><kbd><img src="assets/nhwimmb5g7a.png" width="80%"></kbd></p>

<br>

<a id="node-abrz3bw"></a>

<p align="center"><kbd><img src="assets/7izwzyoxlr8.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu hai box không overlap nhau, thì intersection phải bằng
> 0  -> inter_width  = max(0, inter_area's width) inter_height  =
> max(0, inter_area's height)

<br>

<a id="node-yrg53m5"></a>

<p align="center"><kbd><img src="assets/uym25fh3op.png" width="80%"></kbd></p>

<br>

<a id="node-bwwt56d"></a>

- **2.4 - YOLO Non-max Suppression**

<br>

<a id="node-hyjms6v"></a>

<p align="center"><kbd><img src="assets/e1go39csswe.png" width="80%"></kbd></p>

<br>

<a id="node-7i7kwiv"></a>

- **Exercise 3 - yolo_non_max_suppression**

<br>

<a id="node-98ek4k5"></a>

<p align="center"><kbd><img src="assets/6av69r6101f.png" width="80%"></kbd></p>

<br>

<a id="node-etgx46m"></a>

<p align="center"><kbd><img src="assets/d7psr5z1b5t.png" width="80%"></kbd></p>

<br>

<a id="node-w7u83po"></a>

<p align="center"><kbd><img src="assets/htd9ewrkou9.png" width="80%"></kbd></p>

<br>

<a id="node-t6ntqn0"></a>

- **2.5 - Wrapping Up the Filtering**

<br>

<a id="node-mg98ytz"></a>

<p align="center"><kbd><img src="assets/won53hweqo.png" width="80%"></kbd></p>

<br>

<a id="node-rujyrft"></a>

- **Exercise 4 - yolo_eval**

<br>

<a id="node-1hidvot"></a>

<p align="center"><kbd><img src="assets/8udb15has.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zfbqi5nnii.png" width="80%"></kbd></p>

<br>

<a id="node-rjdixxd"></a>

<p align="center"><kbd><img src="assets/zkeg0ed7ct.png" width="80%"></kbd></p>

<br>

<a id="node-wvltuol"></a>

> [!NOTE]
> 3 - Test YOLO Pre-trained Model on Images: Đại khái là
> dùng Pretrained YOLO model để detect

<br>

<a id="node-b93h2wg"></a>

- **3.1 - Defining Classes, Anchors and Image Shape**

<br>

<a id="node-tfihs8j"></a>

<p align="center"><kbd><img src="assets/oawzrxcu60m.png" width="80%"></kbd></p>

<br>

<a id="node-x7lskt3"></a>

- **3.2 - Loading a Pre-trained Model**

<br>

<a id="node-wxf3fgy"></a>

<p align="center"><kbd><img src="assets/9qvx27gmomg.png" width="80%"></kbd></p>

<br>

<a id="node-4aec129"></a>

- **3.3 - Convert Output of the Model to Usable Bounding Box Tensors**

<br>

<a id="node-lzznf0d"></a>

<p align="center"><kbd><img src="assets/tcxsfuehdb.png" width="80%"></kbd></p>

<br>

<a id="node-75pg22x"></a>

- **3.4 - Filtering Boxes**

<br>

<a id="node-dio64ry"></a>

<p align="center"><kbd><img src="assets/ytlfd24lz7.png" width="80%"></kbd></p>

<br>

<a id="node-vbe4x3i"></a>

- **3.5 - Run the YOLO on an Image**

<br>

<a id="node-9104ujv"></a>

<p align="center"><kbd><img src="assets/0xuy8lz0lu8c.png" width="80%"></kbd></p>

<br>

<a id="node-i3fusco"></a>

<p align="center"><kbd><img src="assets/f2y496yl3j.png" width="80%"></kbd></p>

<br>

<a id="node-ccbamor"></a>

<p align="center"><kbd><img src="assets/rjv0eyanle.png" width="80%"></kbd></p>

<br>

<a id="node-spa271a"></a>

<p align="center"><kbd><img src="assets/2j7uyrgl06.png" width="80%"></kbd></p>

<br>

<a id="node-jebd2p1"></a>

<p align="center"><kbd><img src="assets/mq0joxqolg8.png" width="80%"></kbd></p>

<br>

<a id="node-m9e3zxg"></a>

- **4 - Summary for YOLO**

<br>

<a id="node-76ap5qy"></a>

<p align="center"><kbd><img src="assets/xtrf2tpuic.png" width="80%"></kbd></p>

<br>

<a id="node-o49ajll"></a>

- **5 - References**

<br>

<a id="node-gs0oe94"></a>

<p align="center"><kbd><img src="assets/pryr2k7fnvl.png" width="80%"></kbd></p>

<br>

<a id="node-uqnnqqa"></a>

## PROGRAMMING ASSIGNMENT: \\*Image Segmentation with U-Net\\*

<br>

<a id="node-8wwwf3p"></a>

<p align="center"><kbd><img src="assets/87we9p2tdu9.png" width="80%"></kbd></p>

> [!NOTE]
> Welcome to the final assignment of Week 3 in Course 4 of the Deep Learning
> Specialization! You'll be building your own U-Net, a type of CNN designed for
> quick, precise image segmentation, and using it to predict a label for every
> single pixel in an image - in this case, an image from a self-driving car dataset.

<br>

<a id="node-uajlz8p"></a>

#### Image Segmentation with U-Net

<br>

<a id="node-6ud4nhp"></a>

<p align="center"><kbd><img src="assets/pjc1xs5lvet.png" width="80%"></kbd></p>

<br>

<a id="node-u6ky4ak"></a>

#### 1 - Packages

<br>

<a id="node-5vxqvgi"></a>

<p align="center"><kbd><img src="assets/y6hy8l0jr5s.png" width="80%"></kbd></p>

<br>

<a id="node-8984gfp"></a>

#### 2 - Load and Split the Data

<br>

<a id="node-3x54xzi"></a>

<p align="center"><kbd><img src="assets/qfsfzolnkm.png" width="80%"></kbd></p>

<br>

<a id="node-v10gc3r"></a>

<p align="center"><kbd><img src="assets/h7oktr0x7da.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/uisrssy55ya.png" width="80%"></kbd></p>

<br>

<a id="node-jb6owao"></a>

> [!NOTE]
> 2.1 - Split Your Dataset into
> Unmasked and Masked Images

<br>

<a id="node-ryb3r3x"></a>

<p align="center"><kbd><img src="assets/j9h92qm1rli.png" width="80%"></kbd></p>

<br>

<a id="node-n4fx98x"></a>

#### 2.2 - Preprocess Your Data

<br>

<a id="node-tgwlx6j"></a>

<p align="center"><kbd><img src="assets/ejvnp9wgrkt.png" width="80%"></kbd></p>

<br>

<a id="node-wt467f7"></a>

#### 3 - U-Net

<br>

<a id="node-77uons4"></a>

<p align="center"><kbd><img src="assets/irgcqz984so.png" width="80%"></kbd></p>

<br>

<a id="node-zdt2xk4"></a>

#### 3.1 - Model Details

<br>

<a id="node-obh2onf"></a>

<p align="center"><kbd><img src="assets/zl4ke814fyf.png" width="80%"></kbd></p>

<br>

<a id="node-x84av36"></a>

<p align="center"><kbd><img src="assets/jiml5pfar2p.png" width="80%"></kbd></p>

<br>

<a id="node-5zkkfwz"></a>

<p align="center"><kbd><img src="assets/93e08bn6wln.png" width="80%"></kbd></p>

<br>

<a id="node-6nk9hhj"></a>

#### 3.2 - Encoder (Downsampling Block)

<br>

<a id="node-9fetklh"></a>

<p align="center"><kbd><img src="assets/14jhhkso7ts.png" width="80%"></kbd></p>

<br>

<a id="node-19pm309"></a>

#### Exercise 1 - conv_block

<br>

<a id="node-hw0omph"></a>

<p align="center"><kbd><img src="assets/ei6gt4t70e.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xfcvryjso48.png" width="80%"></kbd></p>

<br>

<a id="node-4sqq0bb"></a>

<p align="center"><kbd><img src="assets/w32z4ijjyz.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zcnl7u72r7m.png" width="80%"></kbd></p>

<br>

<a id="node-w12qhq5"></a>

<p align="center"><kbd><img src="assets/m5nz5yasrbb.png" width="80%"></kbd></p>

<br>

<a id="node-84zu9oh"></a>

#### 3.3 - Decoder (Upsampling Block)

<br>

<a id="node-9zi6cl4"></a>

<p align="center"><kbd><img src="assets/q4nv6kyscxk.png" width="80%"></kbd></p>

<br>

<a id="node-1l3mxyl"></a>

#### Exercise 2 - upsampling_block

<br>

<a id="node-jd5v09k"></a>

<p align="center"><kbd><img src="assets/1vedonx8jnq.png" width="80%"></kbd></p>

<br>

<a id="node-5iap8qi"></a>

<p align="center"><kbd><img src="assets/ckse1f1b6mp.png" width="80%"></kbd></p>

<br>

<a id="node-bxn3813"></a>

<p align="center"><kbd><img src="assets/sc0hyl1md9.png" width="80%"></kbd></p>

<br>

<a id="node-79keb2c"></a>

#### 3.4 - Build the Model

<br>

<a id="node-vfgcud5"></a>

<p align="center"><kbd><img src="assets/tfibc8oyid.png" width="80%"></kbd></p>

<br>

<a id="node-bmujj0c"></a>

#### Exercise 3 - unet_model

<br>

<a id="node-7rdfwh1"></a>

<p align="center"><kbd><img src="assets/1utisdzy8f7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ik3zcmpajk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3w8xtzfllf7.png" width="80%"></kbd></p>

<br>

<a id="node-gpnar1z"></a>

<p align="center"><kbd><img src="assets/k0nm2kukl9m.png" width="80%"></kbd></p>

<br>

<a id="node-kp8v5nr"></a>

#### 3.5 - Set Model Dimensions

<br>

<a id="node-nce7gye"></a>

<p align="center"><kbd><img src="assets/j971h740prr.png" width="80%"></kbd></p>

<br>

<a id="node-0coplmd"></a>

<p align="center"><kbd><img src="assets/wld1yzujy2p.png" width="80%"></kbd></p>

<br>

<a id="node-737ec6u"></a>

<p align="center"><kbd><img src="assets/cjo30k5ikq.png" width="80%"></kbd></p>

<br>

<a id="node-gteql4v"></a>

#### 3.6 - Loss Function: SparseCategoricalCrossentropy

<br>

<a id="node-q047bvd"></a>

<p align="center"><kbd><img src="assets/lmiz72fybsd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là mỗi pixel là 1 vector 11 dimensions (do có 11 classes)
> và gía trị mỗi item trong vector là class probabilities của pixel đó.

<br>

<a id="node-gx52ado"></a>

<p align="center"><kbd><img src="assets/c3ky9oo1wqq.png" width="80%"></kbd></p>

> [!NOTE]
> Output 128x128x11

<br>

<a id="node-wj9x33h"></a>

> [!NOTE]
> 3.7 - Dataset Handling: Display input
> image và true-mask (đại khái là cái y) hình
> có segmentation dùng để train và y^ muốn
> đạt được

<br>

<a id="node-8rr4y5r"></a>

<p align="center"><kbd><img src="assets/4ubmk5wbsna.png" width="80%"></kbd></p>

<br>

<a id="node-cya8qht"></a>

<p align="center"><kbd><img src="assets/khi063ukgae.png" width="80%"></kbd></p>

<br>

<a id="node-4u5zpzv"></a>

#### 4 - Train the Model

<br>

<a id="node-zh3nura"></a>

<p align="center"><kbd><img src="assets/j8edyduytg.png" width="80%"></kbd></p>

<br>

<a id="node-5x7q455"></a>

#### 4.1 - Create Predicted Masks

<br>

<a id="node-mttzesm"></a>

<p align="center"><kbd><img src="assets/brkn47zn5du.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bước này nó sẽ xác định cái class
> của từng pixel thuộc về đây, dùng argument max

<br>

<a id="node-uzr9la7"></a>

#### 4.2 - Plot Model Accuracy

<br>

<a id="node-dbufj7q"></a>

<p align="center"><kbd><img src="assets/yoz4r7d1p4g.png" width="80%"></kbd></p>

<br>

<a id="node-64cdf18"></a>

#### 4.3 - Show Predictions

<br>

<a id="node-5hnmojg"></a>

<p align="center"><kbd><img src="assets/y31omapx9r.png" width="80%"></kbd></p>

<br>

<a id="node-dc214sa"></a>

<p align="center"><kbd><img src="assets/scprzrjhiks.png" width="80%"></kbd></p>

<br>

<a id="node-egfx6e4"></a>

<p align="center"><kbd><img src="assets/ji64bp9nqmb.png" width="80%"></kbd></p>

<br>

<a id="node-o0jl14i"></a>

> [!NOTE]
> Conclusion You've come to the end of this assignment. Awesome work
> creating a state-of-the art model for semantic image segmentation! This is a
> very important task for self-driving cars to get right. Elon Musk will surely be
> knocking down your door at any moment. ;)
>
> What you should remember:
>
> - Semantic image segmentation predicts a label for every single pixel in an
> image
> - U-Net uses an equal number of convolutional blocks and transposed
> convolutions for downsampling and upsampling
> - Skip connections are used to prevent border pixel information loss and
> overfitting in U-Net

<br>

