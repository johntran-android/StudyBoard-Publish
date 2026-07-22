# Assignment 1 - 2 Layer Nn

📊 **Progress:** `28` Notes | `38` Screenshots

---
<a id="node-9qoed7i"></a>

## Assignment 1 - 2 Layer Nn

<br>

<a id="node-47jj0at"></a>

<p align="center"><kbd><img src="assets/9ok7wyhpyqo.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại khái là mình sẽ làm function forward() và backward() trong
> đó forward() sẽ tính output từ input và params, trong quá trình này ta sẽ
> lưu lại các intermediate value đặng còn xài khi backward trong cache
> còn backward sẽ tính downstream gradient (derivative of loss đối với
> input, params) dựa trên upstream gradient và cache

<br>

<a id="node-k8117yz"></a>

<p align="center"><kbd><img src="assets/2nmcft8cu0l.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là làm một cái fully connected layer, điểm chú ý là input có
> shape (N, d_1, ...d_k) thì N chính là số sample, còn (d_1, d_2,...d_k)
> là shape của một sample 'tensor' ví dụ hình màu CIFAR 10 thì nó là
> 3x32x32 hay 32x32x3 gì đó, tùy.
>
>
>
> Vậy ý tưởng đầu tiên là phải flatten nó ra, thành ra vector có
> d_1*d_2*..d_k = D units. Khi đó input sẽ có shape là (N, D)

<br>

<a id="node-h8j824d"></a>

<p align="center"><kbd><img src="assets/egko6fji96q.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/iu2t0eezha.png" width="80%"></kbd></p>

<br>

<a id="node-jydrk09"></a>

<p align="center"><kbd><img src="assets/2w05gs86omr.png" width="80%"></kbd></p>

> [!NOTE]
> có dout (hiểu nó là derivative of loss w.r.t output), cần tính downstream
> gradient dx, dw, b.
>
>
>
> Thế thì theo computational graph đơn giản của xw + b = out thì dx =
> dout(upstream gradient) * dout/dx (local gradient) dout/dx sẽ là w và
> transpose nếu cần sao cho dx cùng shape x
>
>
>
> **dx (N, D) = dout (N, M) @ w.T (M, D)**
>
>
>
> Tương tự dw = dout * dout/dw, với dout/dw = x
>
>
>
> **dw (D, M) =  x.t (D, N) @ dout (N, M)**
>
>
>
> Còn db = dout * dout/db thì dout/db = 1 tuy nhiên vì là b được
> broadcasting n ên phải phải lấy mean dout theo phương phù hợp (sum
> và chia N = số sample)

<br>

<a id="node-nka59ud"></a>

<p align="center"><kbd><img src="assets/keusazm36fg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/56lc872iazf.png" width="80%"></kbd></p>

> [!NOTE]
> Chú ý người ta yêu cầu shape của các x, dx, ở dạng ban
> đầu (khi chưa reshape) nên khi tính toán thì thực hiện
> reshape. Nhưng sau đó thì reshape dựa trên shape của x.
>
>
>
> Với db thì hãy dùng np.sum() thay vì inner sum của np
> array

<br>

<a id="node-gh2hmv9"></a>

<p align="center"><kbd><img src="assets/x2e95xnv4zk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/meanapxzitd.png" width="80%"></kbd></p>

> [!NOTE]
> np.maximum(x, 0) chứ ko phải dùng np.max() nhé, và x trước. Vì sao?

<br>

<a id="node-ne7t40q"></a>

<p align="center"><kbd><img src="assets/nbwe02bt0e.png" width="80%"></kbd></p>

> [!NOTE]
> relu backward()

<br>

<a id="node-b404pwk"></a>

<p align="center"><kbd><img src="assets/vvljt1ll04.png" width="80%"></kbd></p>

<br>

<a id="node-e232ien"></a>

<p align="center"><kbd><img src="assets/sapxcjrirgc.png" width="80%"></kbd></p>

> [!NOTE]
> Viết function tính svm_loss và d loss/ d input.
>
>
>
> Lập luận như sau: hinge loss của một sample, ta sẽ xem thử
>
>
>
> **(1) trong các predicted class score ứng với incorrect class, cái
> nào mà correct score chưa bỏ xa một đoạn delta = 1**, thì
>
>
>
> (2) tính tổng các distance giữa incorrect score cộng 1 và correct score.
>
>
>
> Như vậy để làm ý (1), ta sẽ check xem các vị trí có thỏa điều
> kiện này. Đó là bằng cách đầu tiên lấy ra correct score :
>
>
>
> correct_s = x[arange(len(y)), y],
>
>
>
> Sau đó cái này (correct_s - x) < 1.0 tương đương correct_s < 1 + x
> sẽ cho ra matrix mà chỗ nào thỏa sẽ là 1, ngược lại là 0. Gọi là
> matrix vị trí, sẽ được dùng 
>
>
>
> Rồi, ta sẽ chuẩn bị matrix các margin là score + 1 - correct score,
> và vì chỉ tính những incorrect score, nên cần set vào margin matrix
> này chỗ nào ứng với correct score thì cho bằng 0.
>
>
>
> Rồi dùng cái matrix vị trí ở trên, để mà lấy ra từ matrix margin mới tính
>
>
>
> rồi sum() để tổng lại, khỏi bỏ axis vì ta sẽ cần tổng lại hết theo hàng
> để ra L(i), nhưng sau đó cũng tổng lại các L(i) để có L(batch)
>
>
>
> Cuối cùng chia N (số sample) để có mean.

<br>

<a id="node-kxp1sr4"></a>

<p align="center"><kbd><img src="assets/nht62qq82hq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/89b70to5ft.png" width="80%"></kbd></p>

> [!NOTE]
> Còn về dx tức dL / d score, suy nghĩ như sau: correct score ví dụ s3 lần
> lượt tham gia với các incorrect score khác s1 để tính margin1, với s2 để
> tính margin2. Rồi trong các margin nếu cái nào thỏa sẽ tham gia vào  loss
> qua các phép cộng.
>
>
>
> Vậy, cái graph sẽ như trên, khi backprop, qua node (cộng) như đã biết
> gradient sẽ được phân bổ đều, và qua các nhánh dưới cũng là node cộng
> nên cũng lại phân bổ đều. Vậy **ds1, ds2 (incorrect class) đều bằng 1** còn
> với **correct class thì nó sum lại từ số nhánh** (trong C - 1 nhánh) có tham
> gia. Nên ta **phải xem có bao nhiêu nhánh tham gia**, bằng cách **check
> số margin thỏa điều kiện correct_s < incorrect score
> + 1.** Chú ý là với correct score thì phải nhân -1
>
>
>
> Vậy ta chỉ cần **xem margin nào thỏa correct_s < x + 1** như đã có sẵn lúc
> tính loss. Lúc này ta đã có một matrix 1 / 0, gán cho dx.
>
>
>
> Sau đó, **set vị trí ứng với correct class thành 0**, đặng sau đó **tổng theo
> axis=1 để ra SỐ LƯỢNG CÁC NHÁNH MÀ correct score  có tham gia** tính
> loss, và **lấy giá trị này set vào vị trí ứng với correct score trong dx. Là
> xong.
>
>
>
> Chú ý quan trọng là, phải chia cho N để lấy trung bình vì ta đang tính
> trên một batch**

<br>

<a id="node-ouok2yv"></a>

<p align="center"><kbd><img src="assets/v4gwqie1srl.png" width="80%"></kbd></p>

> [!NOTE]
> Thực tập (dòng suy nghĩ): lấy 2 sample, từ các scores, ta tính ra
> **margin (mg) = score + 1 - correct score,** trong đó mỗi row ta sét hai vị
> trí để ví dụ cho việc correct score ở đây đã bỏ xa incorrect score (ví trí 0,
> 0 và 1,1), tức là **margin hai chỗ này đã âm**
>
>
>
> Thành ra khi tạm matrix 'vị trí' sao cho chỗ nào margin dương hoặc
> bằng 0, mg = mg>=0 thì mọi vị trí đều true, trừ hai vị trí trên.
>
>
>
> Tới đây chỉ việc set vào margin chỗ nào ứng với correct class thành 0 là
> xong rồ**i dùng matrix vị trí để lấy ra**, sum lại là ra loss

<br>

<a id="node-x4a5pdm"></a>

<p align="center"><kbd><img src="assets/463rd9cfirb.png" width="80%"></kbd></p>

> [!NOTE]
> có thể thấy hồi làm linear_svm dài dòng
> hơn nhưng cơ bản cũng lập luận tương tự

<br>

<a id="node-65zzou9"></a>

<p align="center"><kbd><img src="assets/5085nh9mk45.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ozd5k2cbjq.png" width="80%"></kbd></p>

> [!NOTE]
> Dựa theo công thức L(i) = - log prob [yi] computation graph, từ s
> (predicted class scores), qua softmax ra class probabilities, tới đây
> chỉ correct class probability tham gia tính loss, với việc qua log, và
> lấy âm.
>
>
>
> Thì backprop, bắt đầu với dL/dL = 1, qua node (*-1) có local grad 
> d (-log p) / d log p = -1, và d log p / d p = 1/p nên ta có downstream
> gradient tại p3 là -1/p3 (p3 ở đây cho rằng là prob của correct class)

<br>

<a id="node-rl1za3b"></a>

<p align="center"><kbd><img src="assets/bs4b5l28syb.png" width="80%"></kbd></p>

> [!NOTE]
> phác thảo c.g từ s3 để tính ra p3 phải đi theo 2 nhánh, một
> nhánh ở tử số, một nhánh ở mẫu số, backprop về có thể thấy
> dp3/ds3 = tổng grad đi về theo 2 nhánh
>
>
>
> triêng lh

<br>

<a id="node-puhmp5e"></a>

<p align="center"><kbd><img src="assets/rwhc6p0yjrc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/z4qiysd148h.png" width="80%"></kbd></p>

> [!NOTE]
> tổng grad 2 nhánh về s3 ta có dp3/ds3 là (1 - p3)*p3
> hay **-(e^s2 + e^s1) / tổng j e^s_j chính là**
>
>
>
> **- (tổng các p_incorrect class)**
>
>
>
> ====
>
>
>
> Nếu tính **dp3 / ds1** thì grahp sẽ là: 
>
>
>
> s1 -> e^s1 -> sum e^sj -> 1/ sum -> * (e^s3)
> nên backprop sẽ là :
>
>
>
> dp3 / d {1/ sum} = e^s3
>
>
>
> d {1/sum} / dsum = -1/sum**2
>
>
>
> d {sum} / d e^s1 = 1
>
>
>
> d e^s1 / d s1 = e^s1
>
>
>
> Vậy d p3 / d s1 = e^s3 * (-1/sum**2) * e^s1
>
>
>
> = -e^s1*e^s3/sum**2 **chính là -p1*p3**
>
>
>
> **Nếu nhân thêm dL /dp3 ta sẽ có dL / ds1**:
>
>
>
>  (-1/p3)*[-e^s1*e^s3/sum**2] =  
> = (1/ [e^s3 / sum]) (e^s1*e^s3/sum**2)
> = (sum / e^s3)*(e^s1*e^s3/sum**2)
> = **e^s1/sum chính là p1**

<br>

<a id="node-9x5v4v1"></a>

<p align="center"><kbd><img src="assets/q55dgwtd3k.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi tới đây dừng lại chút, nói về việc hàm softmax nhận
> một vector, trả ra một vector, nên đạo hàm của hàm
> softmax d softmax (v) / dv sẽ là Jacobian matrix Trong đó
> mỗi hàng của nó là đạo hàm của từng phần tử của vector
> p đối với các phần tử của vector s
>
>
>
> Và như trên đã thấy nếu "cùng số", ví dụ dp3/ds3 thì sẽ là
> (1 - p3)p3, còn khác số như dp3/ds1 sẽ là p1
>
>
>
> Nên có thể ghi dp/ds (p, s là vector output, input):
>
>
>
> Matrix entry aij (hàng i, cột j) là d pi / d sj
>
>
>
> nếu **i bằng j: (1 - pi)*pi**
> nếu **i khác j**:  **-pi*pj**

<br>

<a id="node-evdk496"></a>

<p align="center"><kbd><img src="assets/yj4c8xrpxa8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/shkatj7ejj.png" width="80%"></kbd></p>

> [!NOTE]
> https://eli.thegreenplace.net/2016/the-softmax-function-and-its-derivative/
>
>
>
> Trùng kết quả với bài viết này, Si ở đây là Pi

<br>

<a id="node-050x7x9"></a>

<p align="center"><kbd><img src="assets/tev1x89z82l.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu chỉ cần tính dL / ds thì dễ hơn khi
> nhờ log và exp triệt nhau.
>
>
>
> Tóm lại: 
>
>
>
> dL/ds_correct là **- (tổng các p_incorrect)**
> dL/ds_incorrect **là p_incorrect**

<br>

<a id="node-cgpkqpa"></a>

<p align="center"><kbd><img src="assets/eyyfhe0gzvd.png" width="80%"></kbd></p>

> [!NOTE]
> "Softmax loss" tính đơn giản, chỉ bỏ các score qua hàm
> softmax, để ra probability, Sau đó dùng y để lấy ra prob ứng
> với correct class. Từ đó log, và sum và negative Chia N là ra
> loss.
>
>
>
> Tuy nhiên cách làm này, có chút chưa chuẩn, tuy ko sai, đó là
> cái vụ unstable Softmax, nên trong bài làm softmax classifier
> đã làm đó là trước khi tính prob Ta sẽ trừ đi một constant, lấy
> bằng thằng lớn nhất trong các score, sau đó mới  bỏ qua
> softmax tính prob. Chỉ vậy thôi còn lại y chang. Theo link để
> tới note nói về cái này
>
>
>
> Còn dx thì là d loss / d score, thì với correct score, **sẽ là 
> - (tổng các p incorrect). với incorrect score thì là p_incorrect.**
>
>
>
> Vậy ta chỉ việc bắt đầu (gán dx cho) bằng matrix prob.
> Xong, set 0 vào vị trí correct class , đặng tổng lại theo hàng
> (axis = 0) để rồi lấy giá trị đó sét vào vị trí correct class
>
> CHÚ Ý, COI CHỪNG LỘN: ở đây mình đã làm lại cái
> softmax_loss, chú thích là solution = ' two_layer_net',
> còn cái dưới là copy từ phần làm softmax classifier.
> Cũng như nhau thôi. Cái quan trọng nhất đó là khi tét
> softmax với random ini weight phải ra -log(num_classes)
> nếu là CIFAR-10 thì là 2.3

<br>

<a id="node-tq8i9dr"></a>

<p align="center"><kbd><img src="assets/ktkg14zq3xn.png" width="80%"></kbd></p>

> [!NOTE]
> svm_loss ra cỡ 9 là đúng, dx có sai số e-9. Cả solution mới làm và
> copy từ linear_svm đều ra đúng.
>
>
>
> softmax ra khoảng 2.3 tương đương **-log(num class =10)** là đúng

<br>

<a id="node-1dgfqyw"></a>

<p align="center"><kbd><img src="assets/y300ph68o5g.png" width="80%"></kbd></p>

> [!NOTE]
> tổng hợp lại, build cái two layer network model. ở
> bước ini, dùng np. randn(shape)*scale để khởi tạo các 
> weight matrix như đã học. 
>
>
>
> còn bias thì ini bằng 0,
>
>
>
> Set vào params dictionary (DLSpec cũng đã làm tương tự

<br>

<a id="node-sbqo2dl"></a>

<p align="center"><kbd><img src="assets/teruvy99978.png" width="80%"></kbd></p>

> [!NOTE]
> function loss này sẽ chịu trách nhiệm forward prop, để
> tính ra prediction (score) (nếu ở test mode thì trả ra
> prediction (score)).  Quá trình này chỉ việc lần lượt gọi
> các affine_forward, relu_forward xen kẽ nhau,  cuối
> cùng là softmax loss để có loss, và dL/dscore
>
>
>
> Ở đây ta phải là cái vụ regularization loss, cũng đơn
> giản, cộng dồn vào loss thôi. Chú ý phải có scale
> factor 0.5 **tức là ta tính (l2) reg loss theo công thức 0.
> 5*lambda*Sum w**2**

<br>

<a id="node-jsw97lj"></a>

<p align="center"><kbd><img src="assets/7uyebedknq7.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó backprop thì chỉ viêc gọi các relu_backward,
> affine_backward để có các dL/dW và dL/db
> **add reg loss grad** và gán vào grad dict

<br>

<a id="node-mo2o3kc"></a>

<p align="center"><kbd><img src="assets/tu678beti8s.png" width="80%"></kbd></p>

<br>

<a id="node-jlwfw2z"></a>

<p align="center"><kbd><img src="assets/61w1nx3twuu.png" width="80%"></kbd></p>

> [!NOTE]
> chạy cái này ra mọi
> relative error đều cỡ e-9
>
>
>
> và pass hết các test case

<br>

<a id="node-b8kdajr"></a>

<p align="center"><kbd><img src="assets/sy6w5l5qy58.png" width="80%"></kbd></p>

> [!NOTE]
> cái solver thì sẽ còn quay lại tự làm lại sau, ở đây người ta
> chỉ yêu cầu xem và dùng nó.

<br>

<a id="node-8jjfug2"></a>

<p align="center"><kbd><img src="assets/2j5beu284va.png" width="80%"></kbd></p>

> [!NOTE]
> khi train model với các h.p để sẵn, model cơ bản là underfit biểu hiện là
> hai đường train và val acc bám sát nhau và còn đang đi xuống
>
>
>
> (cái hình dưới là với best model, sau khi đã tuning thì thấy rằng model đã
> bắt đầu overfit khi val acc đang bắt đầu giảm.

<br>

<a id="node-6gdwc3h"></a>

<p align="center"><kbd><img src="assets/8g6wrm1j9xm.png" width="80%"></kbd></p>

> [!NOTE]
> với cái model chưa được finetune, visualize
> các hidden value chưa thấy rõ hình hài gì

<br>

<a id="node-zcof48i"></a>

<p align="center"><kbd><img src="assets/pdrivi7arq.png" width="80%"></kbd></p>

> [!NOTE]
> họ nói rằng nhìn vào plot có thể thấy lr đang nhỏ, model
> underfit và có thể cải thiện thêm. Ở đây ta sẽ cố gắn tuning
> để coi có đạt performance 52% như người ta hay ko

<br>

<a id="node-dwtjckb"></a>

<p align="center"><kbd><img src="assets/1y47opyknu9h.png" width="80%"></kbd></p>

> [!NOTE]
> thử với các hp,
> random search

<br>

<a id="node-puswrnu"></a>

<p align="center"><kbd><img src="assets/ilpblundxdr.png" width="80%"></kbd></p>

> [!NOTE]
> kết quả đã đạt 52% như họ nói và các hidden
> layer cũng đã show các pattern rất rõ

<br>

