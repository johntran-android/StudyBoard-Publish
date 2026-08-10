# 3.3.3 Equivalent kernel

📊 **Progress:** `2` Notes | `4` Screenshots | `1` AI Reviews

---
<a id="node-9bkb1me"></a>

## 3.3.3 Equivalent kernel

<br>

<a id="node-qgf9klh"></a>

## Section 3.3.3 Equivalent Kernel

<p align="center"><kbd><img src="assets/obce5vt6q1o.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là, đầu tiên gs nói rằng, cái posterior mean solution **m**N = β**S**N**Φ**T**t**, có một cách diễn giải thú vị, sẽ giúp chuẩn bị cho kernel method, bao gồm Gaussian process đã nhắc đến ở trên. (Dừng lại tí, vì sao gọi là posterior mean solution? À thì là vì, như đã giải thích trong ghi chú "Gaussian Prior and Posterior Parameters", khi đã có posterior, thì một cách để đưa ra point estimate cho **w** chính là dùng cái **w** khiến maximize posterior distribution)
>
>
>
> Như vậy, dùng wMAP, (tức là, tương tự như wML, viết tắt, ám chỉ cho w có được nhờ maximum likelihood, thì wMAP, là w khiến maximum posterior distribution) ta sẽ có hàm dự đoán là y(**w**, **x**) = (**w**MAP)TΦ(**x**) = (β**S**N**Φ**T**t**)TΦ(**x**) 
>
>
>
> Thế thì ta sẽ phân tích cái cục này để xem vì sao nó ra như 3.60:
>
>
>
> (β**S**N**Φ**T**t**)TΦ(**x**) 
>
>
>
> = β(**S**N**Φ**T**t**)TΦ(**x**) (β chỉ là scalar, bỏ nó ra khỏi khối matrix transpose)
>
>
>
> = β\[(**Φ**T**t**)T(**S**N)T\]Φ(**x**) (dùng identity (AB)T = BT AT)
>
>
>
> = β**t**T**Φ**(**S**N)TΦ(**x**)
>
>
>
> = β\[**t**T**Φ**(**S**N)TΦ(**x**)\]T (do **t**T**Φ**(**S**N)TΦ(**x**) là scalar, có thể transpose tự do)
>
>
>
> Mấy biến đổi dưới chỉ là dùng identity (AB)T = BT AT 
>
>
>
> = β\[**Φ**(**S**N)TΦ(**x**)\]T**t**
>
>
>
> = β\[Φ(**x**)T\[**Φ**(**S**N)T\]T\]**t**
>
>
>
> = βΦ(**x**)T(**S**N)**Φ**T**t**
>
>
>
> Tới đây ta phân tích như sau:
>
>
>
> Tiếp, **Φ**T là gì: còn nhớ **Φ**, là matrix có các hàng là các vector Φ(**x**1)T, ...Φ(**x**N)T, nên **Φ**T là matrix có các cột là Φ(**x**1), ...Φ(**x**N)
>
>
>
> Vậy **Φ**T**t,** theo góc nhìn thứ hai đã học trong MIT 1806 khi nhân matrix với vector, kết quả sẽ là linear combination các cột của **Φ**T với hệ số là các phần tử của **t**.
>
>
>
> **Φ**T**t** = Σn=1:N Φ(**x**n) tn 
>
>
>
> Nên βΦ(**x**)T(**S**N)**Φ**T**t** = βΦ(**x**)T(**S**N)\[Σn=1:N Φ(**x**n) tn\]
>
>
>
> = Σn=1:N {βΦ(**x**)T(**S**N)Φ(**x**n) tn} → 3.60
>
>
>
> Tiếp, phân tích kĩ hơn, βΦ(**x**)T(**S**N)Φ(**x**n) tn sẽ là tích của scalar βΦ(**x**)T(**S**N)Φ(**x**n) với target variable tn Nên cái 3.60 chính là linear combination của các scalar t1,...tN với bộ hệ số là βΦ(**x**)T(**S**N)Φ(**x**1),....βΦ(**x**)T(**S**N)Φ(**x**N)
>
>
>
> Và người ta đặt hàm k(**x**, **x**') = βΦ(**x**)T(**S**N)Φ(**x**') là k(**x**, **x**'), gọi là **smoother matrix**, hoặc **equivalent kernel**.
>
>
>
> thì bộ hệ số trên chính là k(**x**, **x**1), k(**x**, **x**2),...k(**x**, **x**N) 
>
>
>
> và từ đó 3.60 trở thành:
>
>
>
> y(**w**, **x**) = Σn=1:N {k(**x**, **x**n) tn}

**🔗 See also:** [Gaussian Prior and Posterior Parameters](./331_bayesian_linear_regression.md#node-nt82rck) · [Bias Parameter and Basis Function](./310_linear_regression_and_basis_functions.md#node-6p1u6u8)

<br>

<a id="node-8irf7ds"></a>

### Equivalent Kernel and Linear Smoothers

<p align="center"><kbd><img src="assets/e42pzur1y4.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/id5zpr8ybns.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/9mkjps5iqd.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, tiếp theo đại ý là như sau:
>
>
>
> Trong note trước mình đã hiểu vì sao có được kết qủa y(**w**, **x**) = Σn=1:N {k(**x**, **x**n) tn}, để thấy hàm y dự đoán t cho một input **x** sẽ đưa ra dự đoán bằng cách tổ hợp tuyến tính (linear combination) các giá trị target t trong data (t1,....tN), với hệ số tổ hợp quy định bởi hàm kernel k(**x**, **x**1),...k(**x**, **x**N).
>
>
>
> Mà phân tích kĩ hàm kernel, với công thức k(**x**, **x**') = β Φ(**x**)T**S**N Φ(**x**'), ta sẽ thấy nó có các đặc điểm sau:
>
>
>
> Thứ nhất, nó là scalar, tức là, nhận vào hai input (có thể là vector hoặc scalar) là **x** (input đang muốn dự đoán t) và **x**' (có thể là là input trong data, ví dụ **x**1,...**x**N), và nó sẽ dùng công thức trên để tính ra một scalar value. Muốn nhấn mạnh chỗ này vì nó nó làm rõ rằng các hàm k(x, x1), ...k(x, N) sẽ tạo ra một bộ hệ số, giúp tổ hợp tuyến tính các vector x1,..xN.
>
>
>
> Thứ hai, thông qua việc công thức của nó có **S**N, là posterior variance của **w**, mà posterior distribution, sẽ được xây dựng thông qua Bayes rule: f(w|data) = f(data|w)f(w)/f(data), nên đương nhiên là nó sẽ phụ thuộc data. Do đó, hàm kernel, cũng sẽ phụ thuộc data, chứ không phải là một hàm fixed, hay nói cách khác, tùy vào việc data như thế nào sẽ chi phối hàm kernel.
>
>
>
> Đặc điểm thứ ba đó là, khi x gần x'. kernel sẽ lớn, và ngược lại (tí nữa mình sẽ quay lại điểm này)
>
>
>
> Gs vẽ hình minh họa 3.10: Hiểu như sau:
>
>
>
> Bản đồ nhiệt bên phải chính là đồ thị hàm kernel(x, x') theo x, x'. Để rồi tại nơi x = x', bản đồ nhiệt có màu vàng đỏ biểu hiện hàm kernel có giá trị lớn, và ra xa đường chéo này (tức x khác x') thì màu xanh thể hiện hàm kernel nhỏ.
>
>
>
> Và từ đồ thị này, người ta cắt 3 mặt cắt (để chỉ còn vẽ hàm k(x,x') theo x tại 3 giá trị x' khác nhau.
>
>
>
> Với hình dưới cùng, khi x' nằm bên trái, thì đồ thị hàm k(x, x') sẽ cho thấy nếu x nằm bên trái, thì k sẽ cao, và ngược lại x ra xa (qua chính giữa hay bên phải) thì k sẽ giảm.
>
>
>
> Tương tự, với hình thứ hai, khi x' nằm giữa, thì đồ thị hàm k(x, x') theo x cũng cho thấy nếu x ở giữa, thì k lớn, và nhỏ lại khi x nhích ra trái hoặc phải.
>
>
>
> Và hình trên cùng cũng tương tự.
>
>
>
> Tóm lại, ý nói là: hành vi của hàm kernel(x, x') sẽ: có giá trị lớn nếu x gần x' và nhỏ khi ngược lại.
>
>
>
> Do đó khi phân tích cái tổ hợp y(**x**,**w**) = k(**x**,**x**1) t1 + k(**x**,**x**2) t2 + ....k(**x**,**x**N) tN ta sẽ thấy như đã nói, nó sẽ lấy tổ hợp tuyến tính của các t1,...tN để làm dự đoán cho input **x**, nhưng hệ số lấy như thế nào thì tùy xem **x** gần hay xa các **x**1,...**x**N.
>
>
>
> Cuối cùng gs nói, cái đặc điểm cục bộ này (ý chỉ cái tính chất ta nói vừa rồi - dùng trọng số lớn hay nhỏ tùy tao x cần dự đoán nằm gần hay xa điểm dữ liệu xj) cũng đúng với các basis function khác như non-local polynomial hoặc sigmoidal như hình 3.11.
>
>
>
> ---
>
>
>
>
>
> Chỗ này rất quan trọng cần nói rõ: Cục bộ là sao mà toàn cục là sao?
>
>
>
> Vì sao Gaussian kernel basis function lại là hàm cục bộ? là vì nó có dạng giống như cái chuông, có đỉnh tại một điểm nào đó. Để rồi nhận vào input x, nếu x nằm gần cái tâm này thì giá trị hàm sẽ cao, và khi x ở xa thì hàm sẽ nhỏ lại gần bằng 0. 
>
> \
> Và ta nói nó cục bộ là vì, giả sử ta có hàm Φ(x) như vậy, và nhân với trọng số w: wΦ(x) và ta sẽ điều chỉnh w. Khi đó có thể hình dung ràng, khi điều chỉnh w, thì ta chỉ làm thay đổi độ cao cái chuông chứ hoàn toàn không đổi được hành vi: khi ra xa cái tâm thì Φ(x) nhỏ về 0 kéo theo w Φ(x) cũng nhỏ về 0.
>
>
>
> Khi đó gỉa sử ta có hàm w1Φ1(x) + w2Φ2(x), thì hình dung đồ thị của nó giống như ta có hai cái chuông nối tiếp nhau vậy,  và giả sử ta muốn nắn lại hình dạng của độ thị tại khúc đầu bằng cách thay đổi w1, thì nó cũng không làm méo mó khúc sau, và ngược lại.
>
>
>
> Trong khi đó, với hàm đa thức, giả sử xét hàm Φ(x) = x^2. Thì nó sẽ có dạng đường cong phi tuyến (parabol) kéo dài đến vô cùng. Và nếu xét hàm w1 x^2 + w2 x^3,  thì nếu ta thay đổi w1, hay w2 thì giá trị của hàm y trên toàn bộ trục số sẽ thay đổi. Điều này hoàn toàn khác với hàm basis cục bộ ta ví dụ ở trên nơi mà khi thay đổi w1, hay w2 sẽ chỉ khiến đồ thị của hàm y thay đổi một cách cục bộ tại các vùng tương ứng thôi. Trong khi đó ở đây, nó việc thay đổi w1, w2 sẽ kéo theo đồ thị của y trên toàn trục số thay đổi. Đó chính là tính toàn cục.
>
>
>
> Như vậy, ở đây gs muốn nói đến một sự vi diệu, thông qua kernel function, thì dù basis function có là hàm toàn cục hay cục bộ, thì kết quả vẫn là: tính cục bộ - dùng giá trị target của data t1,...tN với trọng số lớn với các **x**j ở gần input **x** và trọng số nhỏ với **x**j ở xa input **x**.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Bài viết thể hiện sự thấu hiểu sâu sắc và giải thích trực quan rất tốt về đồ thị, đặc biệt là phần phân biệt tính cục bộ/toàn cục của basis functions. Bạn chỉ cần sửa một lỗi diễn đạt nhỏ ở đoạn 4: hệ số kernel dùng để tổ hợp tuyến tính các giá trị target $t_n$ chứ không phải các vector $x_n$.

<br>

