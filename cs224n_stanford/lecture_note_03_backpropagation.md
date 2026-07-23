# Lecture Note - 03
backpropagation

📊 **Progress:** `7` Notes | `24` Screenshots

---
<a id="node-2g835yv"></a>

## Lecture Note - 03
backpropagation

<br>

<a id="node-qc1cmrb"></a>

<p align="center"><kbd><img src="assets/zjx26ydo0b.png" width="80%"></kbd></p>

> [!NOTE]
> một số điểm chính
> trong document này

<br>

<a id="node-ou1d7sl"></a>

<p align="center"><kbd><img src="assets/28tpz4hfdlb.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái nói về việc ta đã đồng ý rằng cần phải có
> những mô hình mạnh hơn, complex hơn mới deal
> được với các dataset phức tạp thì neural network là
> model có thể làm được vậy

<br>

<a id="node-aa87uu0"></a>

<p align="center"><kbd><img src="assets/hqd7zwkqpss.png" width="80%"></kbd></p>

> [!NOTE]
> bộ não người phức tạp hơn nhiều, nên sẽ rất khập
> khiễng nếu so sánh tuy nhiên neural network được
> inspired bới biological neural network. Hình ảnh dưới
> cho thấy khả năng tạo decision boundary flexible giúp
> separate được hai bên

<br>

<a id="node-8342psl"></a>

<p align="center"><kbd><img src="assets/8tifmss4lqu.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/9klaiatai7o.png" width="80%"></kbd></p>

<br>

<a id="node-2mxtp91"></a>

<p align="center"><kbd><img src="assets/dcj9ehiqskj.png" width="80%"></kbd></p>

<br>

<a id="node-t444yjg"></a>

<p align="center"><kbd><img src="assets/b5quatz0m4a.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là dựa trên ý nghĩa của đạo hàm của hàm số là độ dốc của
> hàm số tại điểm đó, ta có thể tính toán giá trị xấp xỉ của đạo hàm bằng
> cách cho x thay đổi 1 khoảng 2 epsilon (x-epsilon, x+epsilon) và tính
> khoảng thay đổi của hàm số f(x+eps) - f(x-eps) và tính ra tỉ lệ. Cái này
> không thể dùng trong training vì rất tốn kém nên chỉ dùng để gradient
> check.

<br>

<a id="node-ullh74e"></a>

<p align="center"><kbd><img src="assets/k3za0sox9x.png" width="80%"></kbd></p>

<br>

<a id="node-jgw45sq"></a>

<p align="center"><kbd><img src="assets/5uebaiy8p8b.png" width="80%"></kbd></p>

<br>

<a id="node-r6909kl"></a>

<p align="center"><kbd><img src="assets/h7o3cgstt0d.png" width="80%"></kbd></p>

<br>

<a id="node-hcv3qy2"></a>

<p align="center"><kbd><img src="assets/3i460lw6t55.png" width="80%"></kbd></p>

<br>

<a id="node-4idksmc"></a>

<p align="center"><kbd><img src="assets/i8ywzbpo3wt.png" width="80%"></kbd></p>

<br>

<a id="node-t149bo6"></a>

<p align="center"><kbd><img src="assets/q8x8ui8vxr.png" width="80%"></kbd></p>

<br>

<a id="node-u4vdmcu"></a>

<p align="center"><kbd><img src="assets/oop04vf855.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái nói về l2 regularization - add thêm l2 loss term và
> cơ bản chỉ là tổng bình phương các params của weight
> matrix của mọi layer. Người ta không tính bias b vào hoặc 
> có cũng chẳng sao lí do như Andrew Ng có giải thích đó là
> có làm thì cũng không còn tác dụng.
>
>
>
> Theo Chat GPT thì bias nó chỉ là đảm bảo giúp y có giá trị
> khi feature weight = 0 hết, nó không ảnh hưởng đến việc 
> gây model overfit - cái mà chỉ là do các feature weight gây ra

<br>

<a id="node-au9qsa8"></a>

<p align="center"><kbd><img src="assets/q8kofn87url.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là như đã biết dropout ở DLSpec, nhưng ở đây nhắc
> nhớ lại rằng nó giúp như ta train một bộ nhiều simple neural
> network để rồi khi dự đoán (test với dropout không áp dụng) thì
> như ta xài ensemble method - lấy số đông kết quả của một bộ
> nhiều cái neural net

<br>

<a id="node-mfkb42a"></a>

<p align="center"><kbd><img src="assets/swqwewu8fur.png" width="80%"></kbd></p>

<br>

<a id="node-zjy5x5b"></a>

<p align="center"><kbd><img src="assets/hs6chc9381n.png" width="80%"></kbd></p>

<br>

<a id="node-0hk71df"></a>

<p align="center"><kbd><img src="assets/7y1veiatq0d.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là thông qua SVD, ta có U là matrix mà mỗi column là
> eigenvector của X'. Từ đó UX' thì ta có các feature mới (các cột
> của matrix UX') kiểu như là linear combination của các feature cũ
> nhưng có tính chất uncorrelated

<br>

<a id="node-3uzwr5a"></a>

<p align="center"><kbd><img src="assets/8tx7ly6pszg.png" width="80%"></kbd></p>

<br>

<a id="node-xqu0384"></a>

<p align="center"><kbd><img src="assets/p9lirjo8jdc.png" width="80%"></kbd></p>

<br>

<a id="node-tf36zd1"></a>

<p align="center"><kbd><img src="assets/7v9nnoek6oc.png" width="80%"></kbd></p>

<br>

<a id="node-krcgr1b"></a>

<p align="center"><kbd><img src="assets/nq0ydzhfapn.png" width="80%"></kbd></p>

<br>

<a id="node-6ue218e"></a>

<p align="center"><kbd><img src="assets/njebflt3p3.png" width="80%"></kbd></p>

<br>

<a id="node-b92qnzp"></a>

<p align="center"><kbd><img src="assets/leaowz8v1n.png" width="80%"></kbd></p>

<br>

