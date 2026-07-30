# Lec 18: MGF Continued

📊 **Progress:** `42` Notes | `49` Screenshots

---
<a id="node-74uu9a0"></a>

## Lec 18: MGF Continued

<br>

<a id="node-l1t6b99"></a>

## TÓM TẮT:

- Tính MGF M(t) của Expo(1) = 1/(1-t) t < 1

- Khi đã có MGF, như bài trước ta đã biết các lí do mà MGF quan trọng
trong đó có reason #1 đó là ta chỉ cần tính đạo hàm cấp n của nó sẽ cho
ta n'th moment.

- Dù ta có thể tính đạo hàm nhiều lần để có 1st, 2nd moment nhưng có
cách hay hơn. Bằng cách nhận ra 1/(1-t) liên quan đến Geometric series

a + ar + ar^2 = Tổng k=0:infinity a*r^k với |r| < 1 sẽ converge về a/[1-r]

Nên 1/1-t chính là Tổng n=0:infinity t^n với |t| < 1

Thế thì theo gs, từ đây cho phép ta KHỎI CẦN TÍNH ĐẠO HÀM CẤP N
ĐỂ CÓ MOMENT THỨ N LÀM GÌ CHO MỆT, mà chỉ cần ĐỌC NÓ RA
THÔI

Cụ thể là ta đã biết ở bài trước rằng, n'th moment = đạo hàm cấp n của
M(t) (là coefficient của (t^n / n!) khi expand M(t) theo Taylor series tại 0)

Do đó, bằng cách tạo ra (t^n / n!) thì BẤT CỨ CÁI GÌ GẮN VỚI NÓ
CHÍNH LÀ COEFFICIENT, VÀ CHÍNH LÀ N'TH MOMENT

Do đó ta sẽ nhân thêm n! và chia n! để có (t^n / n!). Như vậy cái lòi ra làm
coefficient của t^n/n! ở đây là n! CHÍNH LÀ N'TH MOMENT.

Từ đó cho phép ta ĐỌC LUÔN RẰNG: 1ST MOMENT (EX) LÀ 1!, 2ND
MOMENT E(X^2) LÀ 2!

N'TH MOMENT CỦA EXPO(1) E(X^n) = n!

-  đây là tính chất RẤT MẠNH CỦA MGF. Vì ví dụ như khi tính n'th
moment (E[X^n]) thì nếu dùng LOTUS, ta phải TÍNH TÍCH PHÂN
(INTEGRAL) VÀ CÓ THỂ GẶP NHỮNG TÍCH PHÂN RẤT PHỨC TẠP.

Trong khi đó, nếu ta có MGF, để có nth moment, ta CHỈ CẦN TÍNH
DERIVATIVE MÀ DERIVATIVE THÌ THƯỜNG DỄ HƠN LÀ TÍNH TÍCH
PHÂN

-Từ n'th moment của Expo(1) ta dễ dàng có n'th moment của Y ~ Expo(λ):
E[Y^n] = n! / λ^n

- N'TH MOMENT CỦA N(0,1) VỚI N LẺ ĐỀU BẰNG 0

- MGF CỦA POIS(λ) = e^[λ(e^t-1)]

- Nếu Y ~ Pois(µ) và X~Pois(λ) và biết X, Y INDEPENDENT thì X+Y ~
Pois(λ+µ)

<br>

<a id="node-ly17nqq"></a>

<p align="center"><kbd><img src="assets/z9g4zld4av8.png" width="80%"></kbd></p>

> [!NOTE]
> Bài này ta sẽ **tiếp tục thảo luận về MGF**, cụ thể là tiếp tục đi qua **MGF**
> của **các distribution quan trọng,** đầu tiên là **Exponential**.
>
>
>
> Thế thì như đã nói ở bài giảng về **Exponential**, nếu **X ~ Expo(λ)** thì chỉ
> bằng cách nhân X cho λ: **Y = λX** thì **Y sẽ ~ Expo(1)** (link hồng)
>
>
>
> Nên ta **sẽ làm việc với X ~ Expo(1)** để cho đơn giản (λ = 1) và khi muốn
> làm việc với Expo(λ) thì chỉ việc thay bằng X = X/λ
>
>
>
> và ta sẽ **đi tìm MGF** và **moments** của nó.
>
>
>
> gs nói sơ rằng chữ **moments**, có xuất xứ từ **vật lý** (Physic) và sự thật
> có **rất nhiều điểm tương đồng giữa variance** (trong **statistic**) với
> **moment of inertia** (mô men quán tính)

<br>

<a id="node-k9xqo34"></a>

<p align="center"><kbd><img src="assets/ne9dvvthfqs.png" width="80%"></kbd></p>

> [!NOTE]
> Như đã biết **MGF** của r.v **X**, **M(t)** theo định nghĩa chỉ là **expected
> value của e^tX**: E(e^tX)
>
>
>
> Gs nói lại một điều đã nói bữa trước, đó là t chỉ là **dummy** **variable**, ta
> **có thể dùng s, w gì cũng được**. Cái ý quan trọng cần nhấn mạnh đó là **X
> là random variable** nên **apply một function f(x) vào nó** f(X) này là tên hay
> dùng để chỉ function chứ không nói gì tới pdf đâu nhé) thì **ta sẽ có một
> random variable.**
>
>
>
> Và function f(x) đó ở đây có công thức là e^tX. Chú ý, luôn phải viết hoa
> chữ X, vì X ám chỉ random variable X. Và ý nghĩa của MGF M(t) của r.v X là,
> nó là hàm số được tính bằng cách i) **apply hàm e^tx lên X**, để có **e^tX**,
> và như đã biết, đây là **một r.v mới**, từ đó ta sẽ ii) Tính mean của nó:
> E(e^tX).
>
>
>
> Nhớ rằng  khi **apply function vào random variable X** ta có f(X) = e^tX
> **cũng là random variable** nên đương nhiên **có thể hợp lệ để tính
> expected value**.
>
>
>
> Nên function theo t, M(t) này mang ý nghĩa là, **định nghĩa ra một function
> f(x) = e^tx** để rồi **apply nó lên random variable X** để có một random
> variable mới, và **lấy expected value của random variable này**

<br>

<a id="node-6zjo8tb"></a>

<p align="center"><kbd><img src="assets/sbkbww9zbgi.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì để tính **EX** với X là **continuous** random variable, ta sẽ theo công thức
> đã biết đó là **weighted sum các possible value của** X với **weight là xác suất
> mang giá trị đó**. Với continuous r.v thì nó có dạng:
>
>
>
> ∫-infinity:infinity **x f(x)dx** (1) với f(x) là PDF 
>
>
>
> Với Expo(λ) thì PDF là fX(x) = λe^-λx với x ∈ [0, inf) 
>
>
>
> ⇨ **X ~ Expo(1)** thì **f(x) = e^-x** nếu **x > 0** và **bằng 0 nếu x <= 0** nên tích phân 
> từ -infinity tới infinity **chỉ còn** là từ **0-infinity**
>
>
>
> nên (1) =∫0:infinity **x * e^(-x) dx**
>
>
>
> Nhưng giờ ta cần tính **E(g(X)) = E[e^tX]** nên theo **LOTUS** cho phép **dùng ngay 
> PDF của X** thay vì phải tìm PDF của g(X)
>
>
>
> = tích phân từ 0 đến infinity của **g(x) * e^(-x) dx**
>
>
>
> = tích phân từ 0 đến infinity của **e^(tx) * e^(-x) dx**
>
>
>
> = tích phân từ 0 đến infinity của **e^(tx - x)** dx
> = tích phân từ 0 đến infinity của **e^[x(t - 1)]** dx
>
>
>
> **= tích phân từ 0 đến infinity của e^[-x(1 - t)] dx**

<br>

<a id="node-9510dh2"></a>

- **Moment Generating Function Derivation**

<p align="center"><kbd><img src="assets/gg07dk26wne.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì tích phân này **gs cho rằng cũng dễ giải**, nhưng có thể khỏi cần giải mà
> chỉ cần nhận định **nếu nhân (1-t)** vào e^[-x(1-t)]
>
>
>
> Thì nếu t < 1 để **(1 - t) > 0**  ta sẽ có **(1-t) e^[-x(1-t)]** chính là **PDF của
> Expo(1-t)** (tức là Expo(λ) với **λ = 1-t dương**
>
>
>
> (Xem lại định nghĩa bài trước ta đã biết PDF của Expo(λ) là λe^(-λx), và PDF của
> Expo(1) dễ thấy sẽ là e^-x như đã nói hồi nãy)
>
>
>
> nên **nhân và chia bớt cho (1-t),** tích phân từ 0 đến infinity của e^[-x(1-t)] dx sẽ
> là
>
>
>
> **(1/1-t)** * ∫0:inf(**1-t) e^[-x(1-t)] dx**
>
>
>
> và tích phân này **đương nhiên là bằng 1** vì nó là tích phân -inf:inf của PDF
> của Expo(1-t) theo tính chất, **để valid thì nó phải bằng 1**.
>
>
>
> Vậy cái tích phân mình cần tính là **1/(1-t) với điều kiện t<1**
>
> - Tính MGF M(t) của Expo(1) = 1/(1-t) t < 1

**🔗 See also:** [Exponential Distribution PDF](./lec_16_exponential_distribution.md#node-4qgm8vv)

<br>

<a id="node-90onk9j"></a>

<p align="center"><kbd><img src="assets/yz1cyp6199e.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, nếu **t > 1** ta **sẽ có vấn đề** khi **tích phân này sẽ blow up** (chỗ này chưa
> hiểu lắm) nhưng gs nói, điều này không sao, vì theo bài trước ta đã nghe gs
> nói **đại khái là (để MGF hữu ích)** **chỉ cần** nó finite trong một khoảng **(-a, a) a>0
> nào đó quanh 0.**
>
>
>
> Thì trong trường hợp này, khoảng đó là **(-infinity, 1)** hoặc ta có thể nói rằng trong 
> (**-1, 1)**. (có nghĩa là yêu cầu t<1 cho phép function finite trong khoảng (-1, 1) nên
> thỏa yêu cầu về tính valid của MGF

<br>

<a id="node-w083rf5"></a>

<p align="center"><kbd><img src="assets/0au6ry5ugieh.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi thế thì **khi đã có MGF**, như bài trước ta đã biết **các lí do mà MGF
> quan trọng** trong đó có reason #1 đó là ta c**hỉ cần tính đạo hàm cấp n**
> của nó **sẽ cho ta n'th moment.**
>
>
>
> Và **1st moment là EX**, nên bằng cách lấy đạo hàm cấp 1 của M(t) = 1/(1-t)
> ta sẽ có EX chính là mean.
>
>
>
> và bằng cách lấy **đạo hàm cấp 2**, ta sẽ có **2nd moment** chính là **E(X^2)**
> và từ đó giúp ta tính Var(X) = E(X^2) - (EX)^2
>
>
>
> Và ta có thể làm như vậy để check với các kết quả đã tính EX, Var(X) bữa
> trước.

<br>

<a id="node-yuqk5xe"></a>

<p align="center"><kbd><img src="assets/czqz9zeyqen.png" width="80%"></kbd></p>

> [!NOTE]
> tương tự như vậy ta có thể
> tính 3nd, 4th moment ...

<br>

<a id="node-x1gqp0q"></a>

<p align="center"><kbd><img src="assets/cy6gequgrne.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói dù ta có thể **tính đạo hàm nhiều lần để có 1st, 2nd** moment nhưng **có**
> **cách hay hơn**. Bằng cách **nhận ra 1/(1-t)** liên quan đến **Geometric** series
>
>
>
> gs: **Bất cứ khi nào ta thấy 1 chia cho 1 trừ cái gì đó thì ta nên luôn nghĩ đến
> Geometric series**.
>
>
>
> Và ta có thể **dùng nó theo 2 hướng**:
>
>
>
> 1) là **có một Geometric series result**, ta sẽ **expand** nó thành **Geometric
> series** hoặc
>
>
>
> 2) ngược lại **có Geometric series** ta sẽ **collapse** nó thành dạng **Geometric
> series result**

<br>

<a id="node-afbqqmv"></a>

<p align="center"><kbd><img src="assets/kskel9561dp.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/wj0oy29ywhn.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/mxfdupt7do.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gb8ttn3seju.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì lý thuyết của Geometric series cho ta biết
>
>
>
> a + ar + ar^2 = Tổng k=0:infinity a*r^k với |r| < 1 sẽ converge về a/[1-r]
>
>
>
> Nên 1/1-t chính là **Tổng n=0:infinity t^n** với |t| < 1
>
>
>
> Thế thì theo gs, từ đây cho phép ta **KHỎI CẦN TÍNH ĐẠO HÀM CẤP N ĐỂ CÓ MOMENT THỨ
> N LÀM GÌ CHO MỆT**, mà chỉ cần **ĐỌC NÓ RA THÔI**
>
>
>
> Cụ thể là ta đã biết ở bài trước rằng, **n'th moment** = **đạo hàm cấp n của M(t)** (là **coefficient
> của (t^n / n!) khi expand M(t) theo Taylor series tại 0)
>
>
>
> Do đó, bằng cách tạo ra (t^n / n!) thì BẤT CỨ CÁI GÌ GẮN VỚI NÓ CHÍNH LÀ COEFFICIENT, VÀ
> CHÍNH LÀ N'TH MOMENT**
>
>
>
> Do đó ta sẽ **nhân thêm n!** và **chia n!** để có (t^n / n!). Như vậy cái **lòi ra làm coefficient của
> t^n/n!** ở đây là **n! CHÍNH LÀ N'TH MOMENT.**
>
>
>
> Từ đó cho phép ta **ĐỌC LUÔN RẰNG: 1ST MOMENT (EX) LÀ 1!, 2ND MOMENT E(X^2) LÀ 2!**

<br>

<a id="node-4s1og1h"></a>

<p align="center"><kbd><img src="assets/jbwjo1b2pjo.png" width="80%"></kbd></p>

> [!NOTE]
> Gs cho biết đây là **tính chất RẤT MẠNH CỦA MGF**. Vì ví dụ như khi **tính n'th
> moment (E[X^n])** thì nếu dùng **LOTUS**, ta phải **TÍNH TÍCH PHÂN (INTEGRAL)**
> VÀ **CÓ THỂ GẶP NHỮNG TÍCH PHÂN RẤT PHỨC TẠP.**
>
>
>
> Trong khi đó, nếu ta có MGF, để có nth moment, ta CHỈ CẦN TÍNH DERIVATIVE
> MÀ **DERIVATIVE THÌ THƯỜNG DỄ HƠN LÀ TÍNH TÍCH PHÂN**
>
> N'TH MOMENT CỦA EXPO(1) E(X^n) = n!

<br>

<a id="node-rlr7teg"></a>

<p align="center"><kbd><img src="assets/8ho7ol44pv.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo ta sẽ thảo luận vấn đề này với khái quát của **Exponential**: Expo(λ)
>
>
>
> Thế thì cho Y ~ Expo(λ). Thì X = λY thì X sẽ ~ Expo(1). Ông nói bí quyết để
> nhớ là **hãy nhớ Expo(λ) có mean = 1/λ**.
>
>
>
> Nên nếu Y ~ Expo(λ) thì mean Y tức EY = 1/λ, thì để có random variable có
> mean = 1 thì ta phải nhân với λ. Nên X = λ*Y sẽ là ~ Expo(1)

<br>

<a id="node-a14rr6j"></a>

<p align="center"><kbd><img src="assets/flv31j8sgx7.png" width="80%"></kbd></p>

> [!NOTE]
> Từ đó X = λY <=> Y = X/λ 
>
>
>
> nên dẫn đến Y^n = X^n / λ^n
>
>
>
> Do đó E[Y^n] = E[X^n / λ^n]  
>
>
>
> theo **linearity** bỏ 1 / λ^n ra ngoài
>
>
>
> E[Y^n] = E[X^n] / λ^n
>
>
>
> **E[Y^n] = n! / λ^n**
>
>
>
> Như vậy là ta đã có **n'th moment của Y ~ Expo(λ)**
>
> N'TH MOMENT CỦA
> EXPO(λ) E(Y^n) = n!/λ^n

<br>

<a id="node-pxqpg73"></a>

<p align="center"><kbd><img src="assets/qzluiztapg.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự như vậy bữa trước ta đã **tìm MGF của standard normal Z ~ N(0,1)** thì
> bằng cách đặt **X = μ + σZ** thì ta **có thể tính MGF của mọi normal N(μ, σ^2) r.v**

<br>

<a id="node-dfvtp2n"></a>

<p align="center"><kbd><img src="assets/oliq8227mvg.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp ta sẽ thảo luận **moment của N(0,1)**
>
>
>
> Thế thì vì **mean là 0** và **variance là 1** nên ta đã biết **1st moment EX = 0, 
> và 2nd moment EX^2 = Var(X) + (EX)^2 = 1 + 0 = 1** 
>
>
>
> Và bữa trước ta đã dùng **symmetry** ta cũng đã nhận định rằng **n'th moment
> với n lẻ sẽ bằng 0**. Bởi vì dùng **LOTUS**, khi tính n'th moment sẽ là 
>
>
>
> E[X^n] = tích phân -inf:inf **z^n** **f(z)**dz với f(z) = e^(-z^2/2)/√(2π)
>
>
>
> Để rồi ta nhận định rằng: 
>
>
>
> i) **(-z)^n** = **-z^n** với n lẻ nên 
>
>
>
> ii) **f(-z) = f(z)** 
>
>
>
> g(z) = z^n * f(z) là hàm lẻ, vì **g(-z)** = (-z)^n f(-z) = -z^n f(z) = **- g(z) 
>
>
>
> Và khi g(z) = - g(z) ta kết luận g(z) là hàm lẻ (odd function)
>
>
>
> và dùng tích chất symmetry, tích phân từ -a đến a của g(z)dz luôn bằng 0
>
>
>
> Kết luận N'TH MOMENT CỦA N(0,1) VỚI N LẺ ĐỀU BẰNG 0**
>
> N'TH MOMENT CỦA N(0,1)
>
>
>
> VỚI N LẺ ĐỀU BẰNG 0

<br>

<a id="node-6gpq9ff"></a>

<p align="center"><kbd><img src="assets/8mtgiazqsac.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì để **tính n'th moment** với n **chẵn**, gs cho rằng ta sẽ phải **đối
> mặt với nhiều bài toán tích phân phức tạp**
>
>
>
> **Do đó ta sẽ dùng MGF**. Như bài trước đã chứng minh **MGF của Z ~ N(0,
> 1) là M(t) = e^(t^2/2)**
>
>
>
> Thế thì gs nói thêm, bằng các công cụ như **chain rule**, **product rule**, ...
> thì ta **luôn có thể tính derivative**. Trong khi **có những bài toán tích phân
> không thể giải được**. Do đó việc **tính derivative luôn dễ hơn là tích phân**
>
>
>
> Thế thì gs nói nếu ta **lấy đạo hàm lần đầu**, **t sẽ nhảy xuống**:
>
>
>
> (d/dt) e^t^2/2 = (**t**^2/2)*e^(**t**^2/2 - 1)
>
>
>
> Sau đó để lấy **đạo hàm lần 2** ta sẽ **phải dùng product rule ((uv)' = u'v + uv')** 
> vì khi đó nó có dạng u(t)*v(t). 
>
>
>
> Và tiếp tục lấy đạo hàm lần 3 thì sẽ **ngày càng tedious** để làm,
> **DÙ LÀ VẪN LÀM ĐƯỢC**

<br>

<a id="node-hf5ofd9"></a>

<p align="center"><kbd><img src="assets/jckvvexrp8e.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì **một cách dễ hơn** đó là gs **dùng Taylor expansion của e^x**
>
>
>
> Ta có **e^x** theo **Taylor expansion** = Tổng n=0:infinity **x^n / n!**
>
>
>
> Vì Taylor series **hội tụ ở mọi x**, nên có thể ngay lập tức **thay x = t^2/2** vào
> (Đây là kiến thức mà 1801 sẽ bổ sung)
>
>
>
> => e^(t^2/2) = Tổng n=0:infinity (t^2/2)^n / n! = Tổng n=0:infinity t^(2n) / 2^n / n!
>
>
>
> = Tổng n=0:infinity t^(2n) / (2^n * n!)
>
>
>
> Thế thì như ví dụ trước, ta sẽ **cần các hạng tử có dạng:** [**coefficent_n**] * **t^n** / **n!**
> hay ở đây, sẽ là **coefficient_2n** * **t^(2n)** / **(2n)!** 
>
>
>
> Thì để có (2n)! chỉ việc nhân thêm (2n)! và chia bớt (2n)!:
>
>
>
> Thì hạng tử trở thành (2n)! * t^(2n) / (2^n * n!) / (2n)!
>
>
>
> = **[ (2n)! / (2^n * n!) ]** * t^(2n) / (2n)!
>
>
>
> Khi đó **những thứ gắn với t^(2n) / (2n)!** , tức là [ (2n)! / (2^n * n!) ] chính là 
> **coefficient của (2n)'th moment**  - tức moment thứ 2n (là **moment chẵn**)
>
>
>
> Vậy (2n)'th moment, hay E(z^2n) = **(2n)! / (2^n * n!)**
>
> Cần kiến thức về convergence của series từ 18.01 nhưng hiểu đại khái là
> **với bất kì giá trị nào của x** thì tổng của chuỗi x^n/n! sẽ converge = e^x

<br>

<a id="node-4erubqh"></a>

<p align="center"><kbd><img src="assets/f2cwjhi295s.png" width="80%"></kbd></p>

> [!NOTE]
> Kiểm tra lại với n = 1, xem nó có ra E(X^2) = 1 không. THật vậy
> (2*1)!/(2^1*1!) = 1 
>
>
>
> Kết quả trên là đúng vì với X~N(0,1) Var(X) = 1, theo công thức variance
> thứ 2: Var(X) = EX^2 - (EX)^2 = EX^2 (vì EX = 0), => EX^2 = 1

<br>

<a id="node-h2vajys"></a>

<p align="center"><kbd><img src="assets/dabehcv9ef.png" width="80%"></kbd></p>

> [!NOTE]
> Và với n=2 (**4'th moment**) và n=3 (**6'th moment**) thì sẽ lần lượt là 3, 15.  Và gs
> nói ta hãy để ý pattern sẽ là 3 = **1*3**, 15 = **1*3*5**
>
>
>
> Nên có thể dự đoán n=4 (**8'th moment**) là **1*3*5*7**, **10'th moment** = **1*3*5*7*9**
>
>
>
> Và gs nói nếu ta đã làm một **strategic practice** liên quan đến bài toán **đếm số
> cách chia một nhóm thành các nhóm nhỏ** thì ta sẽ thấy nó có **kết quả y như
> thế này**.
>
>
>
> Ông nói nó có một **phân tích sâu để giải thích cho chuyện này** nhưng gs
> không nói ở đây

<br>

<a id="node-cl67m54"></a>

<p align="center"><kbd><img src="assets/t0o9ihbji3h.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì ông nói là bài trước ta đã biết **3 lí do tại sao MGF lại quan trọng**  và
> qua các ví dụ vừa rồi  ta có thể hiểu tại sao nó gọi là **MOMENT**
> **GENERATING** **FUNCTION** đơn giản vì nó **giúp generate mọi moment**
>
>
>
> Thì tiếp theo ta sẽ thảo luận **MGF của Poisson**, mà như ta đã biết
> **Pois(lambda)** r.v có **mean** và **variance** đều là **lambda**

<br>

<a id="node-mqvx1hy"></a>

<p align="center"><kbd><img src="assets/rldek3h6wj.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì như đã quen thuộc, **xây dựng M(t)** chỉ là xây dựng **E(e^(tX))**
>
>
>
> review một chút, để tính EX, ta tính weighted sum mọi possible value
> x của X, weight bởi PMF (đối với discrete r.v):
>
>
>
> **EX = ∑ x: x*P(X=x)**, với continuous rv, EX sẽ có dạng tương đương là:
>
>
>
> **∫ -inf:inf x f(x)dx (f là PDF)**
>
>
>
> Thế thì nếu chiếu theo đó để tính E(g(X)), g(X) là function g apply lên
> r.v X, nên cũng là một rv) thì ta sẽ cầm PMF/PDF của g(X), tức là:
>
>
>
> E(g(X)) = ∑ mọi possible value g của g(X): g*P(g(X)=g)
>
>
>
> nhưng **LOTUS** cho phép chỉ cần dùng lại PMF/PDF của X:
>
>
>
> E(g(X)) = ∑ mọi possible value x của X: **g(x)***P(X=x)
>
>
>
> Vậy áp dụng ở đây:
>
>
>
> E(e^tx)  = ∑ {mọi possible value x của X} **e^tx** * **P(X=x)**
>
>
>
> P(X=x) là PMG của Poisson = **e^-λ * λ^k / k!**
>
>
>
> với poisson, ta đã biết X chỉ c**ó các possible value dương 0, 1, 2...**
>
>
>
> **E (e^tX) = ∑ k=0:infinity** **e^(tk) * e^-λ * λ^k / k!**

<br>

<a id="node-dogthiy"></a>

<p align="center"><kbd><img src="assets/s4bqiheas9r.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/9fxry5y07bb.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, b**ỏ e^-λ ra ngoài vì nó không dính tới k**
>
>
>
> Thì còn lại e^(tk) * λ^k / k! = (e^t)^k) * λ^k / k! = **[(e^t)*λ]^k** **/ k!** 
>
>
>
> thì gs nói **chỉ cần ta quen thuộc với dạng của Taylor series của e^x** 
> thì ngay lập tức ta thấy rằng cái này chính là:
>
>
>
> Tổng [(e^t)*λ]^k / k! có dạng của **Tổng k=0:infinity x^k/k!** chính là **Taylor 
> series của e^x** với **x = (e^t) * λ** 
>
>
>
> Vậy Tổng [e^t * λ]^k / k! = **e^(e^t * λ)**
>
>
>
> Do đó **E[e^tx] = e^(-λ) e^(λ * e^t) = e^[λ(e^t-1)]**
>
> MGF CỦA POIS(λ) = e^[λ(e^t-1)]

<br>

<a id="node-5uo67q6"></a>

<p align="center"><kbd><img src="assets/rlv5zgb0gnr.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói thêm cái này **valid** với **mọi t** vì **Taylor** **series** của **e^x converge
> everywhere** (again tức là với mọi x thì Tổng n=0:infinity x^n / n! đều
> converge về e^x).
>
>
>
> Và ta có thể **lấy đạo hàm cấp n của M(t)** để có n'th moment, hoặc **expand** 
> (Taylor expansion) nó ra để có các **coefficient của t^n/n!** để có **n'th moment.**
>
>
>
> Nhưng gs muốn dành thời gian để nói về cái khác

<br>

<a id="node-quky9sd"></a>

<p align="center"><kbd><img src="assets/mcsuvo6862n.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/bb317evjemj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu ta có thêm **Y ~ Pois(µ)** bên cạnh **X ~ Pois(λ)** và biết **X, Y độc lập**. Câu hỏi là **tìm
> distribution của X+Y**. Gs nói việc **cộng hai random variable** gọi là **CONVOLUTION**, và có thể trở nên rất
> khó khăn.
>
>
>
> Nhưng bài trước ta đã biết, nếu **X, Y INDEPENDENT** thì ta có một **theorem** (chưa chứng minh) rằng:
>
>
>
> **M_X+Y(t) = M_X(t) * M_Y(t)** (tức là MGF của X+Y sẽ là tích của MGF của mỗi r.v X,Y)
>
>
>
> Do đó ta có: M_(X+Y)(t) = e^[**λ**(e^t-1)] * e^[**µ**(e^t-1)] = **e^[(λ+µ)(e^t-1)]**

<br>

<a id="node-qm2eavg"></a>

<p align="center"><kbd><img src="assets/khlzsop8a9b.png" width="80%"></kbd></p>

> [!NOTE]
> Và gs cho biết **có một theorem** cho phép rằng **nếu có điều này**, thì ta có thể
> kết luận **X+Y là ~ Pois(λ+µ)**
>
>
>
> Gs nói thêm đại khái là đây cũng là **một tính chất hay ho của Poisson**, vì
> **tổng hai Poisson vẫn là Poisson**. Không phải distribution nào cũng có tính
> chất đó
>
> Nếu Y ~ Pois(µ) và X~Pois(λ) và biết X, Y
> INDEPENDENT thì X+Y ~ Pois(λ+µ)

<br>

<a id="node-6ksl6wc"></a>

<p align="center"><kbd><img src="assets/w9zp5rd0nke.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hevki5jr78g.png" width="80%"></kbd></p>

> [!NOTE]
> gs nhấn mạnh điều kiện cho phép cái này là X, Y phải **INDEPENDENT**. ông lấy một ví dụ của
> X, và Y **dependent**, mà ở cấp độ cao nhất chính là X = Y
>
>
>
> Khi đó, **X + Y = 2X**. **Đây không phải là Poisso**n r.v
>
>
>
> Lí do đơn giản đó là **2X chỉ mang giá trị chẵn** trong khi đó **Poisson có thể có mọi giá trị
> dương**. Hoặc có thể dễ thấy E(2X) = 2EX = **2λ** còn Var(2X) = 4Var(X) = **4λ** Điều này càng
> chứng minh 2X không phải Poisson vì ta biết **Poisson r.v có EX = Var(X)**
>
>
>
> Do đó qua ví dụ này để thấy cái việc **tổng hai Poisson X, Y ra một Poisson r.v X+Y chỉ đúng
> nếu X,Y INDEPENDENT.**

<br>

<a id="node-rvqmvgf"></a>

<p align="center"><kbd><img src="assets/3yhirxtuy9q.png" width="80%"></kbd></p>

> [!NOTE]
> Ta sẽ qua một chủ đề lớn tiếp theo, là **JOINT** **DISTRIBUTION**. 
>
>
>
> gs cho biết ta **đã biết qua chút ít** về joint distribution, là distribution của
> nhiều random variable. Và biết sơ rằng nếu các r.v **INDEPENDENT**, thì
> joint distribution của việc **NHÂN** PDF, CDF, PMF của các r.v
>
> JOINT DISTRIBUTION

<br>

<a id="node-d56c7j8"></a>

<p align="center"><kbd><img src="assets/jwyvh6r5tac.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là ta sẽ cố gắng **hiểu thật rõ** một bài toán đơn giản nhất trước,
> đó là có **2 Bernoulli r.v X, Y** (có thể **independent** hoặc **không**)
>
>
>
> Thì ta có 4 ô, để điền 4 giá trị xác suất. Ví dụ như ô đầu bên trên là 
> P(X=0, Y=0) là xác suất cả hai rv X, Y đều bằng 0.
>
>
>
> Ô thứ 2 bên trên là P(X=0, Y=1). Tương tự như vậy.
>
>
>
> Thế thì gs nói ta **miễn là điền vào 4 con số ko âm** và **tổng bằng 1** thì
> đó là một **valid joint distribution**

<br>

<a id="node-m79cahp"></a>

<p align="center"><kbd><img src="assets/desj9vcrar8.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây gs định nghĩa:
>
>
>
> - **JOINT** **CDF**: Với hai r.v X, Y. Joint CDF là **F(x,y) = P(X<=x, Y<=y)**
>
>
>
> - **JOINT** **PMF** (discrete) là **P(X=x, Y=y)**
>
>
>
> Và như đã nói, nếu X, Y independent thì ta có thể tách 
> **F(x,y) = P(X<=x, Y<=y)** ra thành **P(X<=x) * P(Y<=y)**
>
>
>
> **P(X=x, Y=y) = P(X=x) * P(Y=y)**
>
>
>
> **MARGINAL CDF**: Và **P(X<=x)** gọi là **marginal** **CDF of X** cũng như **P(Y<=y)**
> gọi là **marginal CDF of Y.**
>
>
>
> Nên nếu X, Y independent ta có thể nói **JOINT CDF BẰNG TÍCH
> MARGINAL CDF**

<br>

<a id="node-qhnhvlr"></a>

<p align="center"><kbd><img src="assets/myamfmq8odo.png" width="80%"></kbd></p>

> [!NOTE]
> Với **continuous** r.v thì ta có **JOINT** PDF: **f(x,y)** mang ý nghĩa là:
>
>
>
> **P((x,y) thuộc B)** = **∫∫B f(x,y)dxdy**
>
>
>
> gs nói đây là lần đầu tiên ta thấy **tích phân kép** ở class này, nhưng
> ông cho biết phần lớn ta **chỉ cần coi như lấy 2 lần tích phân** mỗi lần
> **theo một biến vậy**
>
> Với CONNTINUOS r.v thì ta có JOINT PDF: f(x,y) mang ý nghĩa là:
>
>
>
> P((x,y) thuộc B) = ∫∫B f(x,y)dxdy

<br>

<a id="node-qpqn9zg"></a>

<p align="center"><kbd><img src="assets/rx20jya3c8e.png" width="80%"></kbd></p>

> [!NOTE]
> Và ta again có thêm **một định nghĩa nữa về independence**: Đó là hai r.v X, Y
> gọi là **independence** khi và chỉ khi **F_XY(x, y) = F_X(x) * F_Y(y)**
>
>
>
> Có nghĩa là :
>
>
>
> **Joint CDF = tích các Marginal CDF**
>
>
>
> tương tự như vậy với PMF và PDF
>
>
>
> **Joint PMF = tích các Marginal PMF 
>
>
>
> Joint PDF = tích các Marginal PDF**
>
> X, Y INDEPENDENT KHI VÀ CHỈ KHI JOINT CDF,
> PMF, PDF = TÍCH CÁC MARGINAL CDF, PMF, PDF

<br>

<a id="node-pscrrh7"></a>

<p align="center"><kbd><img src="assets/kg0rpoqdziq.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì quay lại đây, gs cho rằng ta có thể điền các con số này vào
> bảng như vầy, đều không âm và tổng bằng 1. 
>
>
>
> Câu hỏi đặt ra là: X, Y CÓ INDEPENDENT KHÔNGZ?

<br>

<a id="node-azfokej"></a>

<p align="center"><kbd><img src="assets/sx8joils3qa.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì để trả lời câu hỏi rằng X, Y có Independent không, dựa trên định nghĩa về
> independent random variable với Joint & margin distribution cho biết rằng X,Y sẽ
> independent khi và chỉ khi joint CDF/PMF của chúng bằng tích của marginal
> CDF/PMF
>
>
>
> Thành ra, trong trường hợp này ta sẽ đ**i tính Marginal PMF** của từng cái.
>
>
>
> **Marginal PMF của X**, theo định nghĩa, là **P(X=x)** ta sẽ lập luận như sau:
>
>
>
> **(X=x)** = ∪ {mọi possible value y của Y} (X=x, Y=y) đây là dựa vào set theory:
>
>
>
> (X=x) ⊂ S ⇨ (X=x) ∩ S = (X=x) ⇔ (X=x) = (X=x) ∩ (∪ {mọi possible value y của Y} Y=y))
>
>
>
> ⇔ X=x = ∪ {mọi possible value y của Y} (X=x ∩ Y=y)
>
>
>
> Do đó **P(X=x) = P[**∪ **{mọi possible value y của Y} (X=x ∩ Y=y)]**
>
>
>
> Và với các possible value khác nhau thì các **event (X=x, Y=y) disjoint** do đó
> theo **Axiom 2**:
>
>
>
> P[∪ {mọi possible value y của Y} (X=x ∩ Y=y)] 
>
>
>
> = **Σ {mọi possible value y của Y} P(X=x, Y=y)**
>
>
>
> Vậy **P(X=x) = Σ {mọi possible value y của Y} P(X=x, Y=y)
>
>
>
> Chú ý phải hiểu rằng MARGINAL PMF CỦA X = P(X=x) được tính bằng  cách
> sum mọi giá trị khả dĩ của Y của JOINT PMF**
>
> P(X=x) = ∑ y P(X=x, Y=y)

<br>

<a id="node-cbvzozl"></a>

<p align="center"><kbd><img src="assets/6s1rzc0z8d9.png" width="80%"></kbd></p>

> [!NOTE]
> Gs cho biết chính vì ta s**um lại mọi possible value của Y** gọi là
> **MARGINALIZING** nên nó có cái tên marginal
>
>
>
> Với nếu là continuous, thì ví dụ **marginal pdf của Y** sẽ là như vầy
>
>
>
> tích phân từ **-infinity đến infinity fxy(x,y)dx** ; và cũng chính là động tác **sum
> mọi possible value của X với JOINT PDF fxy(x,y)**

<br>

<a id="node-e60gkl2"></a>

<p align="center"><kbd><img src="assets/1cjj1y2e4k4.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là ta thấy rằng ta đi từ **Joint distribution** đến **Marginal distribution**.
> Nhưng **không thể đi theo hướng ngược lại**. Đó là đi từ marginal distribution
> tới joint distribution. Bởi lẽ **nếu ta chỉ có marginal distribution của X P(X=x)**
> thì ta **không biết gì về Y** để mà tính ra **joint distribution P(X=x, y=y)**

<br>

<a id="node-porw019"></a>

<p align="center"><kbd><img src="assets/8jb8vk2ji0u.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/t9ksftv3i4b.png" width="80%"></kbd></p>

> [!NOTE]
> Áp dụng vào đây ta tính **marginal PMF**:
>
>
>
> i) của X:
>
>
>
> P(X=0) = Tổng y=0,1 P(X=0, Y=y) = 2/6 + 1/6 = 3/6
>
>
>
> P(X=1) = Tổng y=0,1 P(X=1, Y=y) = 2/6 + 1/6 = 3/6
>
>
>
> ii) của Y:
>
>
>
> P(Y=0) = Tổng x=0,1 P(X=x, Y=0) = 2/6 + 2/6 = 4/6
>
>
>
> P(Y=1) = Tổng x=0,1 P(X=x, Y=1) = 1/6 + 1/6 = 2/6
>
>
>
> Có thể thấy khi ta làm vậy, các giá trị của marginal PMF được ghi ở bên lề
> (**MARGIN**) chính vì vậy nó có tên là **MARGINAL**

<br>

<a id="node-vdsi85o"></a>

<p align="center"><kbd><img src="assets/2kixzbwhiky.png" width="80%"></kbd></p>

> [!NOTE]
> Và khi thử **nhân marginal PMF của X và Y** ta sẽ thấy nó **bằng** **joint** **PMF**:
>
>
>
> P(X=0) * P(Y=0) = 3/6 * 4/6 = 12/36 = 1/3 đúng bằng  P(X=0, Y=0) = 2/6
>
>
>
> P(X=1) * P(Y=1) = 3/6 * 2/6 = 6/36 = 1/6 đúng bằng P(X=1, Y=1) = 1/6
>
>
>
> Do đó dựa trên định nghĩa về independent r.v có thể **kết luận X,Y independent**

<br>

<a id="node-55r42tp"></a>

<p align="center"><kbd><img src="assets/qjfipag4scn.png" width="80%"></kbd></p>

> [!NOTE]
> trong ví dụ thứ 2, thì ta sẽ thấy hai r. v X,Y không
> independent.

<br>

<a id="node-fse1w2c"></a>

<p align="center"><kbd><img src="assets/856n4v0cfb6.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ này đại khái là, ta có một trường hợp, mà một cặp gía trị x, y của hai r.v
> X, Y mà lọt trong hình vuông này, tức là nếu 0 ≤ x, y ≤ 1 thì **xác suất
> của các event (X=x, Y=y) tức P(X=x, Y=y) = constant c**
>
>
>
> Và với x,y nằm ngoài hình vuông này, tức x<0 hoặc >1 và y<0 hoặc >1 thì
> P(X=x, Y=y) = 0

<br>

<a id="node-z88yp5r"></a>

<p align="center"><kbd><img src="assets/8b6c0sjb4l5.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì tương tự như với **X~Unif(0,1)**:
>
>
>
> tích phân từ 0 đến 1 của f(x)dx  = tích phân từ 0 đến 1 của c*dx
>
>
>
> (vì định nghĩa của Unif(0,1) là PDF f(x) = c khi x thuộc [0, 1], f(x) = 0 otherwise)
>
>
>
> = c*[x]|0:1 = c*(1-0) = c
>
>
>
> Và **để pdf valid**, **tích phân này phải bằng 1** từ đó => **c = 1**
>
>
>
> Thì ở đây,
>
>
>
> tích phân của **joint pdf** trong đoạn **vùng (area square unit này)** cũng phải
> bằng 1.
>
>
>
> Xét tích phân kép trong vùng A (unit square) của f(x,y)dxdy
>
>
>
> = ∫∫A f(x,y)dxdy = ∫∫A c*dxdy = c*∫∫A dxdy = c*{diện tích của vùng A} = c*1
>
>
>
> tích phân kép trong vùng A (unit square) của dxdy theo **1802** ta đã biết, nó
> **chính là diện tích của vùng A**, và đây là **unit square** nên **area = 1**
>
>
>
> = **c*{diện tích của vùng A} = c*1**
>
>
>
> Vậy để **valid** thì như đã nói **∫∫A f(x,y)dxdy phải bằng 1** => **c = 1**

<br>

<a id="node-kgeps8b"></a>

<p align="center"><kbd><img src="assets/hfghdxnlkqh.png" width="80%"></kbd></p>

> [!NOTE]
> Và dễ hiểu là **Marginal** distribution của X, Y: P(X=x), và P(Y=y) cũng **đều là
> Uniform(0,1)**. Và **X, Y independent**

<br>

<a id="node-r47qktm"></a>

<p align="center"><kbd><img src="assets/qajxlze4mm.png" width="80%"></kbd></p>

> [!NOTE]
> một ví dụ khác, đó là **Uniform** trong cái dĩa (hình tròn) **x^2 + y^2 <= 1** này
> again, điều này mang ý nghĩa đó là nếu x^2+y^2<=1 thì xác suất (X=x,Y=y) là như
> nhau.
>
>
>
> Nên diễn dịch điều này dưới dạng PDF:
>
>
>
> Thì f(x,y) = 1/π nếu x^2+y^2<=1 và f(x,y) = 0 nếu x^2+y^2>1
>
>
>
> 1/π là ở đâu ra, đó là ta cũng lập luận rằng nếu x^2+y^2<=1 thì xác suất (X=x,
> Y=y) là như nhau và bằng constant c. Thì đưa vào **điều kiện pdf valid** ta sẽ có
> tích phân trong toàn mặt phẳng của f(x,y)dxdy phải bằng 1:
>
>
>
> ∫∫f(x,y)dxdy = 1
>
>
>
> và vì **f(x,y) bằng 0** với **x,y ở ngoài hình tròn** nên tích phân trên **trở thành**
> tích phân trong toàn vùng bao bởi đường tròn trên của f(x,y)dxdy phải bằng 1
>
>
>
> <=> ∫∫A f(x,y)dxdy = 1 (A là vùng bao quanh bởi circle unit)
>
>
>
> <=> ∫∫A c*dxdy = 1 <=> c ∫∫A dxdy = 1 <=> c {Diện tích của A} (*) = c*π*r^2 = cπ = 1
>
>
>
> <=> c = **1/π
>
>
>
> (*) Again, sau khi học MIT 18.02 thì đã hiểu tại sao ∫∫A dxdy là diện tích của A**

<br>

<a id="node-lxxpzkt"></a>

<p align="center"><kbd><img src="assets/w9pv5n90pki.png" width="80%"></kbd></p>

> [!NOTE]
> gs nhắc nhở rằng, trong trường hợp này **X,Y DEPENDENT**. vì dễ thấy rằng,
> **không như trong hình vuông** hồi nãy, với **một giá trị nào đó của X**, thì **Y vẫn
> tự do có mọi giá trị trong khoảng 0,1.**
>
>
>
> Còn ở đây nếu **X = 1**, thì **Y sẽ chỉ có thể bằng 0**, còn nếu **X = 0** thì **Y có thể 
> mang các giá trị khác nhau từ 0 đến 1**. Điều này cho thấy rõ **X, Y dependent
> nhau**
>
>
>
> còn gs ghi ở đây ý là X=x, thì Y phải rằng buộc trong khoảng [-sqrt(x^2) và sqrt(x^2)]

<br>

