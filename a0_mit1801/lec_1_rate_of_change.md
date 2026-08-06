# Lec 1: Rate Of Change

📊 **Progress:** `24` Notes | `26` Screenshots

---
<a id="node-thnw9qi"></a>

## Lec 1: Rate Of Change

<br>

<a id="node-jozr6qx"></a>

## Finding Tangent Lines Analytically

<p align="center"><kbd><img src="assets/png8c81xd9j.png" width="80%"></kbd></p>

> [!NOTE]
> về khía cạnh hình học, bài toán là tìm đường tiếp tuyến
> với function y = f(x) tại P. Thì gs vẽ đường này và cho
> rằng bằng cách nào đó ông đã làm xong. Nhưng vấn đề
> là làm sao để tìm nó analytically để máy tính cũng có
> thể làm được

<br>

<a id="node-dcvlkcv"></a>

### Tangent Line Equation and Derivative

<p align="center"><kbd><img src="assets/fo145alo1wl.png" width="80%"></kbd></p>

> [!NOTE]
> Dựa vào kiến thức highschool, phương trình đường tiếp tuyến tại
> P (x0, y0) sẽ có dạng như vầy. Ta sẽ cần tìm P và độ dốc (slope)
> m, và slope độ dốc của đường thẳng tại P (x0, y0) được gọi là
> derivative f'(x0)

<br>

<a id="node-un3u1dj"></a>

#### Derivative as Tangent Slope

<p align="center"><kbd><img src="assets/nj9u3fb3gtn.png" width="80%"></kbd></p>

> [!NOTE]
> Ta có định nghĩa f'(x0) là derivative của hàm f tại x(0)
> chính là độ dốc của đường tiếp tuyến với hàm f(x) tại P (x0, y0)

<br>

<a id="node-kvg51wl"></a>

##### Tangency and Multiple Intersections

<p align="center"><kbd><img src="assets/hjw3yd4ha9p.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì gs đặt vấn đề là, làm sao để biết một line như đường màu
> cam không phải là tangent. Ông cho rằng không phải vì nó cắt f tại 2
> điểm P, Q mà nói nó không phải tangent, bởi lẽ function có thể wiggly.

<br>

<a id="node-iblnmky"></a>

- **Tangent Line as Secant Limit**

<p align="center"><kbd><img src="assets/ybfc08ek63.png" width="80%"></kbd></p>

> [!NOTE]
> và thực tế tangent line chính là đường
> secant line khi Q -> P với P cố định

<br>

<a id="node-9j9jpam"></a>

- **Limit Definition of Tangent Slope**

<p align="center"><kbd><img src="assets/5bgoh5v59ol.png" width="80%"></kbd></p>

> [!NOTE]
> tiếp theo gs vẽ lại secant line, gọi delta_x (xQ - xP) là khoảng
> thay đổi của x, delta_f= f(Q) - f(P) là khoảng thay đổi của f
>
>
>
> thì độ dốc của tangent theo định nghĩa (gs cho rằng lim có thể áp
> dụng cho cả line và độ dốc) sẽ là limit của delta_f / delta_x khi
> delta_x nhỏ vô cùng

<br>

<a id="node-vjsjsoe"></a>

- **Formal Derivative Definition**

<p align="center"><kbd><img src="assets/9q9jjzgobx.png" width="80%"></kbd></p>

> [!NOTE]
> và ta với việc thay delta_x = f(x0+delta_x) - f(x0) ta có định
> nghĩa chính thức của derivative of f tại x0: f'(x0)

<br>

<a id="node-hmphcem"></a>

- **Difference Quotient Limit**

<p align="center"><kbd><img src="assets/b0zgz1487o.png" width="80%"></kbd></p>

> [!NOTE]
> và biểu thức cần tìm limit có tên gọi là
> **DIFFERENCE QUOTIENT**

**🔗 See also:** [linked note](./lec_3_derivatives.md#node-s2734rr)

<br>

<a id="node-zryukyt"></a>

- **Derivative of 1/x Tangent**

<p align="center"><kbd><img src="assets/2uy6oi0w5gl.png" width="80%"></kbd></p>

> [!NOTE]
> Ta sẽ áp dụng để tìm derivative của f(x) = 1/x. Ông cho rằng ta
> sẽ chọn 1 điểm x0. Và kết quả là ta sẽ tìm được tangent line
> của hyperbolla này

<br>

<a id="node-89qh1xl"></a>

- **Derivative Setup and Simplification**

<p align="center"><kbd><img src="assets/071w31nh24ih.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì ta sẽ thiết lập delta_f/delta_x
> như vầy. Và thu gọn nó lại

<br>

<a id="node-0auw0gh"></a>

<p align="center"><kbd><img src="assets/6mfbs0hkw86.png" width="80%"></kbd></p>

> [!NOTE]
> Mục đích là khử đi delta_x ở tử và mẫu thoát khỏi dạng 0/0 (khi
> delta_x -> 0)
>
>
>
> Kết quả cuối cùng, là -1/(x0 + delta_x)x0. Và để có lim khi delta_x
> -> 0  chỉ việc thế delta_x = 0, Ta có **-1/x0^2**
>
>
>
> Dễ thấy đây cũng chính là công thức tính đạo hàm của hàm 1/x
> Thì ở đây chính là ta tìm lại công thức của nó theo định nghĩa đạo
> hàm

<br>

<a id="node-62hc2b0"></a>

<p align="center"><kbd><img src="assets/igyztdr227r.png" width="80%"></kbd></p>

> [!NOTE]
> nhận xét là tangent của hàm 1/x chúi xuống vì slope âm. Và khi x0 ->
> vô cùng, tức là điểm tiếp tuyến càng xa thì độ dốc càng nhỏ lại
>
>
>
> ý nói cái mà ta tìm ra phù hợp với hình ảnh của tangent của hyperbol

<br>

<a id="node-hzyr7dm"></a>

<p align="center"><kbd><img src="assets/s5d1zjc3j3h.png" width="80%"></kbd></p>

> [!NOTE]
> gs giải thích khi tìm limit của biểu thức này khi delta_x -> 0, điều
> ta làm thật sự chỉ là bỏ 0 vào delta_x thôi

<br>

<a id="node-5gy7iuo"></a>

<p align="center"><kbd><img src="assets/9i268u1axx6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/52xyi07e8vx.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp ta sẽ thử giải bài toán này: tìm diện tích của hình tạo bởi
> tangent của f(x) = 1/x và 2 trục. Nó là vấn đề calculus vì nó có dính
> đến tangent.

<br>

<a id="node-ma6w6hg"></a>

<p align="center"><kbd><img src="assets/caxnk4nab9.png" width="80%"></kbd></p>

> [!NOTE]
> Gọi x0,y0 là điểm tiếp xúc
>
>
>
> Thế thì rõ ràng ta cần tìm base và height thể hiện bằng 2 điểm
> line cắt 2 trục
>
>
>
> Thế thì ta đã có phương trình đường tangent với độ dốc đã NHỜ
> CALCULUS MÀ TÍNH ĐƯỢC = -1/x^2.
>
>
>
> Gs gọi nó là yếu tố duy nhất của calculus trong bài toán này

<br>

<a id="node-4fi5gxs"></a>

<p align="center"><kbd><img src="assets/4eio0vgqm0u.png" width="80%"></kbd></p>

> [!NOTE]
> Và để tìm hai giao điểm của tangent line với 2 trục ta cho y = 0 để
> tìm điểm thứ nhất, và x = 0 để tìm điểm thứ 2.
>
>
>
> Từ đó ta có height và base của tam giác

<br>

<a id="node-p0ytzc8"></a>

<p align="center"><kbd><img src="assets/ffk8ap1v90s.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái gs có thể làm nhanh hơn bằng cách
> dùng tính đối xứng của x và y

<br>

<a id="node-7xcj14b"></a>

<p align="center"><kbd><img src="assets/w2swxf77l2f.png" width="80%"></kbd></p>

> [!NOTE]
> và từ base và  height ta tính ra area của tam giác và vì y0 = 1/x0,
> diện tích không còn phụ thuộc x0, y0 nữa ( = 2)

<br>

<a id="node-hx8rkar"></a>

<p align="center"><kbd><img src="assets/32evvd7cjph.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói thêm một số notation: đó là derivative có thể dùng **f'(x)**, và đó
> là notation của **Newton**. Hoặc **df/dx** là **Leibniz**
>
> NOTATION CỦA DERIVATIVE:
>
>
>
> NEWTON: f'
>
>
>
> LEIBNIZ: df/dx, hoặc (d/dx) f

<br>

<a id="node-099szyy"></a>

<p align="center"><kbd><img src="assets/oc539sexucb.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ 2. tìm derivative của f(x) = x^n.
>
>
>
> Thế thì ta cũng sẽ thiết lập biểu thức delta_f / delta_x Nhưng gs cho
> rằng ta không còn cần dùng notation x0 nữa. Mà chỉ cần biết x là fixed
> - là điểm cần tìm derivative và delta x là khoảng thay đổi của x từ đó

<br>

<a id="node-sgne3px"></a>

<p align="center"><kbd><img src="assets/h3a5aphfvbe.png" width="80%"></kbd></p>

<br>

<a id="node-7grl4ur"></a>

<p align="center"><kbd><img src="assets/rgnvguoumy.png" width="80%"></kbd></p>

> [!NOTE]
> Gs cho rằng ta sẽ vận dụng Binomial theorem (nhị thức newton) để
> triển khai
>
>
>
> (x+delta_x)^n = x^n + x^(n-1)*delta_x + O(delta_x^2)
>
>
>
> Có nghĩa là binomial theorem,sẽ giúp ta triển (x+y)^n thành một tổng
> các biểu thức của x và y.
>
>
>
> Thế thì với x+delta_x ta **chỉ cần hai cái đầu** và gọi tất cả các term
> mà dính tới bậc cao hơn 1 của delta_x là O(delta_x^2)
>
>
>
> Đương nhiên ta hiểu rằng là m vậy là vì trong bài toán này ta sẽ tìm lim
> của nó khi  delta_x -> 0 thì O(detal_x^2) ~= 0

<br>

<a id="node-tcrmsbp"></a>

<p align="center"><kbd><img src="assets/ezbjvswk1a.png" width="80%"></kbd></p>

> [!NOTE]
> và triển khai như trước ,thế delta_f = f(x+delta_x) - f(x) và rút gọn
> ta có n*x^(n-1) + O(delta_x)

<br>

<a id="node-kj69uny"></a>

<p align="center"><kbd><img src="assets/cp4ltwnlzrm.png" width="80%"></kbd></p>

> [!NOTE]
> và khi tìm limit khi delta_x -> 0 Thì
> O(delta_x) = 0 và chỉ còn n*x^(n-1)

<br>

<a id="node-drh1ddx"></a>

<p align="center"><kbd><img src="assets/n61k8e0h2fi.png" width="80%"></kbd></p>

> [!NOTE]
> và ta sẽ có thể áp dụng
> nó như thế này

<br>

