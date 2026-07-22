# Note #4 Backpropagation

📊 **Progress:** `9` Notes | `13` Screenshots

---
<a id="node-idyw9h6"></a>

## Note #4 Backpropagation

<br>

<a id="node-5xs9dfx"></a>

<p align="center"><kbd><img src="assets/devko4k380d.png" width="80%"></kbd></p>

<br>

<a id="node-oqs5quk"></a>

<p align="center"><kbd><img src="assets/1gf8hpzdu5sh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về ý nghĩa của đạo hàm là tỉ lệ của khoảng thay
> đổi của hàm f trên khoảng thay đổi vô cùng nhỏ (infinitesimally)
> của x.
>
>
>
> Và kí hiệu df/dx không phải ý chia df cho dx mà là kí hiệu chỉ việc
> tính ra đạo hàm của hàm f w.r.t (đối với) x và nó cũng là một hàm
> số

<br>

<a id="node-fqz1r3v"></a>

<p align="center"><kbd><img src="assets/6m3qvr74fu.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là chính vì ý nghĩa đạo hàm như vậy nên có thể hiểu nó như
> **sự nhạy cảm** của function f (khi x thay đổi tác động đến f thay đổi
> nhiều hay ít ra sao)
>
>
>
> Tiếp theo như đã biết khi f là function của **hai  variable x, y** hay của
> một variable nhưng dưới dạng  **vector [x, y]** thì đạo hàm của f đối với
> input là **vector  các partial derivative.**
>
>
>
> Nói qua ý nghĩa của đạo hàm của hàm **f = x + y** đối với x, hay y đều
> bằng **1**. Vì rõ ràng với hàm sum như này thì **x thay đổi bao nhiêu thì f
> thay đổi bấy nhiêu**, thành ra **tỉ lệ  của hai khoảng thay đổi là 1.**
>
>
>
> Còn với hàm **max** (x, y) thì rõ ràng là vì **nếu y nhỏ hơn x**, thì **hàm f chỉ
> được tính bởi x**, do đó c**hỉ có x tác động lên f**, còn y thì không nên y
> có thay đổi (nhỏ) bao nhiêu thì f vẫn vậy nên đạo hàm của f đối với y
> là 0, và **với x là 1 (vì khi đó như hàm  f = x)**

<br>

<a id="node-dfyohxx"></a>

<p align="center"><kbd><img src="assets/x51g4qaeek.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là mô phỏng một cách đơn giản quá trình forward
> prop với việc tính q từ xây và f từ q, z và backprop với việc
> tính df/dx, df/dy, df/dz thông qua chain rule với df/dq
>
>
>
> Các công thức tính gradient thì như đã biết ở phần trên

<br>

<a id="node-r3a8e03"></a>

<p align="center"><kbd><img src="assets/p9vlqoni8o.png" width="80%"></kbd></p>

> [!NOTE]
> từ sau sẽ viết tắt
> dfdx là dx thôi

<br>

<a id="node-3ypkcva"></a>

<p align="center"><kbd><img src="assets/cwltcthvutb.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là backprop sẽ như cách các gate giao tiếp với nhau để kiểu
> như node sau báo cho node trước biết: à, mà mà tăng 1 khoảng chút
> xíu thì hệ quả f cuối sẽ tăng hay giảm khoảng như vậy. Từ đó cả đám
> sẽ dựa vào đó mà thay đổi sao đó để đạt mục đích chung

<br>

<a id="node-pj1svq4"></a>

<p align="center"><kbd><img src="assets/fe5vzax2tzi.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là cái khái niệm **gate (hay node)** ở trên về cơ bản có thể là bất
> kì một function nào mà **differentiable** nào. Và ta **có thể
> nhóm các gate lại (hay node)** thành một node bự hơn hoặc
> **chia nhỏ ra** để thuận tiện
>
>
>
> Cung cấp thêm một số công thức tính đạo hàm của các function
> với vụ **unary gate** ý nói các function f = x + c hay a*x là hàm đơn biến
> vì c với a là constant **nên chỉ có 1 nhánh input**

<br>

<a id="node-mxyrf4d"></a>

<p align="center"><kbd><img src="assets/qtp3jlmvp9.png" width="80%"></kbd></p>

> [!NOTE]
> ví dụ này đã triển
> khai ở bài trước

<br>

<a id="node-jgsojml"></a>

<p align="center"><kbd><img src="assets/hw8aly6oim5.png" width="80%"></kbd></p>

> [!NOTE]
> nói về đạo hàm của hàm sigmoid, và khi tính
> toán có thể coi sigmoid là 1 gate (gồm các gate
> nhỏ hơn) để khi backprop thì dùng công thức
> này để tính local gradient

<br>

<a id="node-6mn9pdq"></a>

<p align="center"><kbd><img src="assets/0xyy4m71srn.png" width="80%"></kbd></p>

> [!NOTE]
> Theo computational graph thì khi backprop, tại z (hay ở dưới là dot) input
> của sigmoid (= weighted sum của x và w) ta có df/dz là (1-f)*f. và local
> gradient tại node z = vector x.dot product với vector w, dz/dw sẽ là vector x,
> thành ra df/dw là ddot*x.
>
>
>
> Thì nhờ dùng local gradient của sigmoid tức là coi sigmoid là 1 node nên 
> việc tính toán gọn hơn

<br>

<a id="node-kb0gj6q"></a>

<p align="center"><kbd><img src="assets/1yquu82tnhh.png" width="80%"></kbd></p>

<br>

<a id="node-55ff3di"></a>

<p align="center"><kbd><img src="assets/not32a9lgt8.png" width="80%"></kbd></p>

<br>

<a id="node-7r0kdh7"></a>

<p align="center"><kbd><img src="assets/c5pntpi9yjr.png" width="80%"></kbd></p>

<br>

