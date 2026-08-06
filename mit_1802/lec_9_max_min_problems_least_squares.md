# Lec 9: Max-min Problems, Least
squares

📊 **Progress:** `21` Notes | `28` Screenshots

---
<a id="node-7vcu50t"></a>

## Lec 9: Max-min Problems, Least
squares

<br>

<a id="node-q20s5wi"></a>

<p align="center"><kbd><img src="assets/26qnu23efgv.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp bài trước về **partial derivative**, ta quay lại với **approximation
> formula** (linear approximation)
>
>
>
> Câu hỏi là với **function 2 biến x, y** thì công thức sẽ ntn:
>
>
>
> Câu trả lời là nếu **x ~> x + ∆x**, **y ~> y + ∆y** thì z = f(x, y) sẽ
> thay đổi một khoảng xấp xỉ  **f_x*∆x + f_y*∆y** với f_x, f_y là 
> partial derivative
>
>
>
> Tức là linear approximation đối với bivariate function f(x, y) là:
>
>
>
> **∆f ~= f_x*∆x + f_y*∆y** 
>
>
>
> So sánh với hàm một biến: 
>
>
>
> **∆f ~= f'*∆x** (hay f(x) - f(x0) ~= f'(x0)(x-x0) 
>
>
>
> <=> **f(x) ~= f(x0) + f'(x)(x-x0)**
>
>
>
> Và intuition là: khi **x thay đổi delta_x** nó khiến f**unction f thay đổi** một
> khoảng bằng **delta_x** **nhân** với **rate of change f_x**: **f_x*delta_x**
>
>
>
> khi **y thay đổi delta_y** nó khiến function **thay đổi một khoảng delta_y**
> **nhân** với **rate of change f_y**: **f_y*delta_y**.
>
>
>
> Thế thì khi thay đổi cả x, y ta **xấp xỉ** khoảng thay đổi của f bằng **tổng
> hai khoảng thay đổi** do y và do x

**🔗 See also:** [linked note](./lec_11_differentials_chain_rule.md#node-w4i69mr)

<br>

<a id="node-8zbmwg3"></a>

<p align="center"><kbd><img src="assets/6dlmase8u9t.png" width="80%"></kbd></p>

> [!NOTE]
> Review lại **một chút ý nghĩa của partial derivative** của f w.r.t x:
>
>
>
> Đó là ta sẽ **giữ y = y0 fixed**, để rồi điều này **giống như ta sẽ cắt đồ
> thị hàm f với plane song song với xz plane**, khi đó ta có
> **intersection** là đồ thị của **hàm số f(x, y0)**.
>
>
>
> Thì hàm số mang giá trị là **độ dốc của f(x, y0)** chính là **derivative
> của f(x, y0)**, và nó chính là **partial derivative của f đối với x:
> f_x()**

<br>

<a id="node-vds8v0a"></a>

<p align="center"><kbd><img src="assets/k9ymofu84b.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, tiếp theo ta sẽ justify (**biện minh**) cho c**ông thức
> approximation**  vừa rồi.
>
>
>
> Ta sẽ đã biết **f_x, f_y** là **slope của 2 đường tiếp tuyến**

<br>

<a id="node-61urdxt"></a>

<p align="center"><kbd><img src="assets/cds198sr4kr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/kmzhvxkt37.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì đại khái là **nếu ta có f_x(x0, y0) = a** ta có **đường tiếp tuyến** nằm t**rong mặt phẳng
> song song với xz,** **cắt trục y tại** **y0** và có **độ dốc tại x0 là a**, và phương trình của nó là **z -
> z0 = a(x - x0)** mang ý nghĩa là khi x thay đổi từ x0 -> x, z thay đổi từ z0 -> z với rate
> (z-z0)/(x-x0) = a
>
>
>
> Tương tự với **tiếp tuyến thứ hai**, **độ dốc tại (x0,y0) là b**, nó nằm **trong mặt phẳng song 
> song với yz**, **cắt x tại x0** và có phương trình:
>
>
>
> x = x0; z - z0 = b(y - y0)

<br>

<a id="node-exxpd4e"></a>

<p align="center"><kbd><img src="assets/9hwcf2j6nt.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì **L1, L2 đều là tiếp tuyến của đồ thị hàm z = f(x,y)**. Chúng
> **TẠO THÀNH MỘT PLANE** plane **z = z0 + a(x-x0) + b(y-y0)**
>
>
>
> Thì đây là phương trình mặt phẳng với x*constant + y*constant +
> constant và nếu giữ y, thay đổi x ta có phương trình của tangent line
> thứ 1 (ý là cho y = y0 ko đổi thì phương trình trở thành z = z0 + a(x -
> x0)) và ngược lại, giữ x thay đổi y thì ta có phương trình tangent line
> thứ 2
>
>
>
> Gs nói rằng **để có phương trình này** ta có thể **dùng cách khác** liên
> quan đến việc dùng **cross product** và **normal vecto**r, ta cũng sẽ ra
> equation này.

<br>

<a id="node-11x8o3h"></a>

<p align="center"><kbd><img src="assets/u3h0m3dfotl.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì gs cho biết **ý nghĩa** của **linear approximation đối với hàm
> hai biến** chính là **nói rằng** **đồ thị hàm số f (tất nhiên chỉ xét trong
> một khoảng x~=x0) có thể coi như trùng với tangent plane**.
>
>
>
> Nếu ta **di chuyển trên tangent plane** thì **delta_z = linear function
> của delta_x và delta_y (fx*delta_x + fy*delta_y)**.
>
>
>
> Nhưng vì **thực tế** đồ thị của f **chỉ là gần bằng tangent plane** nên
> ta dùng dấu **xấp xỉ ~=**

<br>

<a id="node-b40h0pw"></a>

<p align="center"><kbd><img src="assets/ay3kijwz32w.png" width="80%"></kbd></p>

<br>

<a id="node-h4cgh1l"></a>

<p align="center"><kbd><img src="assets/c61uy9gcluf.png" width="80%"></kbd></p>

<br>

<a id="node-nfrs8y3"></a>

<p align="center"><kbd><img src="assets/06xovfoyd5l2.png" width="80%"></kbd></p>

> [!NOTE]
> Ứng dụng của partial derivative là **optimization**
> problem **tìm min max của function f(x,y)**

<br>

<a id="node-e1purmr"></a>

<p align="center"><kbd><img src="assets/byi0l2nrwk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/fzkg69sev2.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì gs nói rằng tại l**ocal min hoặc max thì cả fx
> và fy đều bằng 0.**
>
>
>
> Và ta khi đó **tangent plane sẽ nằm ngang (song
> song với xy plane)**

<br>

<a id="node-ag7d52x"></a>

<p align="center"><kbd><img src="assets/i7t2zm5rm0l.png" width="80%"></kbd></p>

> [!NOTE]
> và ta có cái tên cho điểm mà tại đó mọi partial derivative đều bằng 0:
> **CRITICAL POINT (cực trị)**.
>
>
>
> Gs cho biết nó **chưa thỏa điều kiện đủ** để xác định là **max hoặc
> min** vì **có những điểm khác mà mọi partial derivative cũng bằng
> 0**

<br>

<a id="node-nm21wxd"></a>

<p align="center"><kbd><img src="assets/doftjvsjraw.png" width="80%"></kbd></p>

> [!NOTE]
> nói nó **chưa đủ để kết luận** min hay max là vì s**addle point
> cũng có mọi partial derivative bằng 0**. Nhưng tùy ta đi hướng nào
> (thay đổi x hay y) thì function sẽ tăng lên hay giảm xuống
>
>
>
> Bài sau ta sẽ xác định maximum hay saddle point bằng cách dùng
> đạo hàm cấp 2 (**second** **partial** **derivative**)

<br>

<a id="node-im1hjzl"></a>

<p align="center"><kbd><img src="assets/nx0dj0rwywe.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì có **3 khả năng như vậy**, như vừa nói **bữa sau** ta sẽ dùng
> **đạo hàm cấp hai để xác định**. Còn ở đây ta sẽ dùng phương pháp
> **COMPLETING THE SQUARE**

<br>

<a id="node-51s6vti"></a>

<p align="center"><kbd><img src="assets/87k7mmvcvr2.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/kko8luoccgj.png" width="80%"></kbd></p>

> [!NOTE]
> Bằng cách **đưa f về tổng các bình phương**, thì **ta xác định f sẽ >= -1**
>
>
>
> và nó **bằng -1 khi y = 0**, và x-y = -1 -> **x = -1**. Do đó đây là **minimum**

<br>

<a id="node-s7nkwfi"></a>

<p align="center"><kbd><img src="assets/cpzt57rsb2f.png" width="80%"></kbd></p>

> [!NOTE]
> gs nói qua **bài toán Least Square**, như đã biết là trong bài toán này ta 
> sẽ muốn **tìm line y = ax + b** **fit tốt nhất** với các data point **(xj, yj)**

<br>

<a id="node-fps3qax"></a>

<p align="center"><kbd><img src="assets/3hbyd2hunrc.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là gs giải thích về việc **để có best line**, thì ta **phải định nghĩa
> best là như thế nào**. Thế thì c**ó nhiều kiểu định nghĩa**, để rồi mỗi
> cái sẽ cho ra một best line khác nhau.
>
>
>
> Nhưng một **giải pháp là dùng sum bình phương của các error**.
> Gs cho rằng cái này được **sử dụng phổ biến** vì thứ nhất nó c**ho ra
> kết quả best line** là đường đi khá tốt, **sát với data points**.
>
>
>
> Và thứ hai là nó **khiến bài toán trở nên đơn giản**, dễ giải.

<br>

<a id="node-kz2qv2m"></a>

<p align="center"><kbd><img src="assets/3a5ywwhi5ly.png" width="80%"></kbd></p>

> [!NOTE]
> như đã nói bài toán **Least Square**, ta sẽ tìm cách **minimize** D =
> **Tổng bình phương của residual** (difference giữa "predicted value"
> ax_i + b và y_i)

<br>

<a id="node-pqf0pv3"></a>

<p align="center"><kbd><img src="assets/a6swo5l4ex8.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đầu tiên ta sẽ đi tìm **CRITICAL POINT**, bằng cách **solve
> các equation**: **Partial derivative của D w.r.t a và b bằng 0**.
>
>
>
> Việc **tính partial derivative** khá **đơn giản**. Với việc dùng
> **chain rule**

<br>

<a id="node-c3vgtor"></a>

<p align="center"><kbd><img src="assets/3lxwmh5a5lb.png" width="80%"></kbd></p>

> [!NOTE]
> **Simplify** một chút ta có như vầy, gs lưu ý rằng ta có thể
> thấy đây **vẫn là các linear equation of a, b**

<br>

<a id="node-kguyqhl"></a>

<p align="center"><kbd><img src="assets/auyjtmo0vu4.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo, nôm na là ta **có thể phân phối dấu tổng** (cơ bản
> chỉ là **sắp xếp lại các term**). Và bài toán **hoàn toàn chỉ là
> giải hệ hai phương trình tuyến tính**

<br>

<a id="node-y4t6o9k"></a>

<p align="center"><kbd><img src="assets/62lhtq24rrc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xlvto4guaq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/u4nq3w8mgkp.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, đại khái gs cho một ví dụ khác, trong đó data points
> không có vẻ gì là có quy luật tuyến tính
>
> Nhưng khi dùng giá trị **log** của y, thì nó có thể thấy là tuân
> theo linear pattern
>
> và sự thật pattern của
> nó là exponential

<br>

<a id="node-lc17la9"></a>

<p align="center"><kbd><img src="assets/0at6z3uw82ji.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì **true pattern** có dạng **y = c*e^ax**, để **tìm c và a** giúp
> tạo được đường **fit tốt nhất với data** này thì rất **khó**. Nhưng **chỉ
> cần lấy ln hai vế**. Ta sẽ có  thể thấy **bài toán trở thành least
> square**
>
>
>
> ln(c*e^ax) = ln(c) + ln(e^ax) = ln(c) + ax ln(e) = ln(c) + ax

<br>

<a id="node-9smtjki"></a>

<p align="center"><kbd><img src="assets/f4m4wnlimgi.png" width="80%"></kbd></p>

> [!NOTE]
> Hay để fit được quadratic pattern thì cũng hoàn toàn dùng least
> square để solve a, b, c bình thường. Và ta sẽ vẫn có hệ 3 phương 
> trình TUYẾN TÍNH đối với a, b, c

<br>

