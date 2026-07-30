# Lec 20: Multinomial And Cauchy

📊 **Progress:** `31` Notes | `44` Screenshots

---
<a id="node-cezegd2"></a>

## Lec 20: Multinomial And Cauchy

<br>

<a id="node-ec0n4e8"></a>

<p align="center"><kbd><img src="assets/2i8koyiaz8b.png" width="80%"></kbd></p>

> [!NOTE]
> Bài này ta sẽ tiếp tục một ví dụ tương tự như bữa trước, là **tính expected
> value** của **distance** giữa hai random variable **Z1, Z2 ~ N(1, 0): E|Z1-Z2|**
>
>
>
> Thế thì gs cho biết ta **có thể dùng 2D LOTUS** mà bài trước đã nói, giúp tính
> E(g(x,y)) bằng tích phân kép **∫-inf:inf ∫-inf:inf g(x,y) f(x,y)dxdy**
> với **f(x,y) là JOINT PDF của X, Y**
>
>
>
> Và vì ta có điều kiện **hai r.v X, Y Independent**, nên **Joint PDF f(x,y)** có thể
> được tính bởi **tích của hai marginal PDF fX(x) và fY(y)**.
>
>
>
> Nói vậy để thấy **đó là một hướng để giải** bài toán này. Tuy nhiên gs cho rằng
> có cách tốt hơn. 
>
>
>
> Đó là dựa trên một nhận định mà ta chưa chứng minh, đó là **TỔNG CỦA HAI 
> NORMAL R.V LÀ MỘT NORMAL**
>
> TỔNG CỦA 2 NORMAL R.V LÀ MỘT NORMAL: 
>
>
>
> X ~ N(μ1, σ1^2), Y ~ N(μ2, σ2^2) thì X+Y ~ N(μ1+μ2, σ1^2 + σ2^2)

<br>

<a id="node-c5j80et"></a>

<p align="center"><kbd><img src="assets/hxhl29q7ajp.png" width="80%"></kbd></p>

> [!NOTE]
> Cụ thể theorem đó là: Cho **X, Y là hai r.v Normal distribution**:  
>
>
>
> **X ~ N(μ1, σ1^2)**, **Y ~ N(μ2, σ2^2)**
>
>
>
> Và **X, Y  independent** thì **Tổng X+Y cũng sẽ là r.v ~ Normal distribution**
> với mean là **tổng mean**, và variance là **tổng variance**:
>
>
>
> **X+Y ~ N(μ1+μ2, σ1^2 + σ2^2)**
>
>
>
> Để rồi nếu là đang quan tâm difference X-Y, thì ta cũng sẽ coi như là tổng
> của hai r.v X+(-Y) với **-Y** cũng là **Normal rv với mean -μ2, variance
> σ2^2**

<br>

<a id="node-frusjsi"></a>

<p align="center"><kbd><img src="assets/qrnubt1ess.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì để **chứng minh theorem này**, trong bối cảnh ta **đã biết về một Theorem về
> MGF** của **independent** random variable X,Y đó là **MGF của (X+Y)** sẽ bằng **tích
> MGF của chúng (chú ý là ta vẫn chưa chứng minh theorem này)**:
>
>
>
> E[e^t(X+Y)] = E(e^tX) * E(e^tY)
>
>
>
> Bữa trước ta đã chứng minh **MGF của N(0,1)** là **e^t^2/2**, thì gs cho rằng ta cũng
> sẽ **dễ dàng chứng minh MGF** của **N(μ, σ^2)** là **e^[μt + (σ^2)(t^2)/2]
>
>
>
> Ta sẽ chứng minh như sau.**
>
>
>
> Ta có MGF của Z (Z ~ N(0,1) là M(t), theo định nghĩa sẽ là E(e^tZ) và ta đã chứng
> minh  là đối với Z thì M(t) = **e^t^2/2**.
>
>
>
> Thế thì như ta đã biết nếu **X = μ + σZ** thì **X ~ N(μ, σ^2)**
>
>
>
> Vậy MGF của nó là:
>
>
>
> E[e^tX] = E[e^(t(μ+σZ))] = E[e^(tμ+tσZ)]= E[e^(tμ) * e^(tσZ)] Vì e^(tμ) là **constant**, vì nó **không phụ thuộc Z** nên áp dụng **Linearity** EcX = cEX
>
>
>
> **= e^(tμ) * E[e^(tσZ)]  (i)
>
>
>
> Xét E[e^(tσZ)]** thì có thể thấy nó là **E[e^(tσ)Z] và nó chính là M_Z(tσ), với M_Z(t)**
> đã biết **= E(e^tZ) = e^t^2/2**  =>E[e^(tσZ)] = e^(σt)^2/2
>
>
>
> Vậy (i) = e^(tμ) * e^(σt)^2/2 = **e^[μt + (σt)^2/2]**
>
>
>
> ⇨ **MGF của X ~ N(μ, σ^2): M_X(t)** = **e^(μt + (1/2)(σ^2)*(t^2))**
>
>
>
> ======
>
>
>
> Còn bây giờ **áp dụng Theorem** trên:
>
>
>
> Tích của MGF của X, Y: M_(X+Y)(t) = M_X(t) * M_Y(t)
>
>
>
> = e^[μ1t + σ1^2t^2/2] * e^[μ2t + σ2^2t^2/2]
>
>
>
> = e^[μ1t + σ1^2t^2/2 + μ2t + σ2^2t^2/2]
>
>
>
> = e^[μ1t + μ2t  + σ1^2t^2/2 + σ2^2t^2/2]
>
>
>
> = e^[(**μ1 + μ2**)t  + (**σ1^2 + σ2^2**)t^2/2]
>
>
>
> Và vế phải, **có dạng e^(μt+σ^2*t^2/2)** với μ = μ1 + μ2; σ^2 = σ1^2 + σ2^2  cho ta kết
> luận rằng:
>
>
>
> **X+Y cũng là ~ Normal distribution** với mean là μ = μ1 + μ2    và variance σ^2 = σ1^2
> + σ2^2.
>
>
>
> Bởi vì như đã biết, MGF cũng có **công dụng tương tự PDF, CDF đó là giúp xác định
> distribution.**

**🔗 See also:** [linked note](./lec_17_moment_generating_functions.md#node-3j4ghan) · [linked note](./lec_17_moment_generating_functions.md#node-cc2zxo3)

<br>

<a id="node-gllm99h"></a>

<p align="center"><kbd><img src="assets/pqwiv15emrp.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì quay lại bài toán này (tính **E(|Z1-Z2|**).
>
>
>
> Thì đầu tiên ta sẽ lập luận rằng **Z1 - Z2** = Z1 + (-Z2) là **tổng của 2
> Standard Normal** r.v.s: **Z1 ~ N(0,1)** và **-Z2 cũng ~ N(0,1)** 
>
>
>
> (Bữa trước, theo link màu cam, đã chứng minh nếu Z ~ N(0,1) thì -Z
> cũng ~ N(0,1))
>
>
>
> Do đó **Z1-Z2 cũng là Normal** với **mean là tổng mean = 0**, và variance
> bằng **tổng variance = 1 + 1 = 2**

**🔗 See also:** [linked note](./lec_14_location_scale_lotus.md#node-uaqngmf)

<br>

<a id="node-xelv2qn"></a>

<p align="center"><kbd><img src="assets/v5sahc20gr.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy, vì **Z1-Z2 ~ N(0, 2)** nên việc **tính E|Z1-Z2|** cũng **SẼ GIỐNG NHƯ
> TÍNH MEAN CỦA MỘT |N(0, 2)| rv**
>
>
>
> Tức là nếu đặt U = Z1 - Z2 thì E|Z1 - Z2| = E|U|
>
>
>
> với U ~ N(0, 2)
>
>
>
> Mà ta đã biết X = μ + σZ sẽ ~ N(μ, σ^2) nên X = (0 + √2Z) = √2Z sẽ **~ N(0, 2)** 
>
>
>
> Nên U = Z1-Z2 có cùng distribution của với X = √2Z
>
>
>
> Vậy nên E|Z1-Z2| = E|U| = E|X| = E(√2Z)

<br>

<a id="node-bxs4fye"></a>

<p align="center"><kbd><img src="assets/ua48l2dmdn.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/kjtnk3lsd3.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì do **Linearity**, ta đưa √2 ra ngoài để chỉ còn **E|Z|**. Và đến đây **chỉ việc dùng LOTUS**: 
>
>
>
> Again, LOTUS cho phép tính **E(g(X))** bằng cách **dùng ngay PDF/PMF của X** thay vì phải tìm 
> PDF/PMF của g(X)
>
>
>
> Nên ở đây E(Z) theo định nghĩa = ∫-inf:inf z f(z)dx với f(z) là pdf của N(0,1) = (1/√2π)
> e^(-z^2/2)
>
>
>
> Thì theo LOTUS:
>
>
>
> E|Z| = ∫-inf:inf **|z|** f(z)dz = **∫-inf:inf |z| (1/√2π) * e^(-z^2/2) dz**

<br>

<a id="node-q70ozzn"></a>

<p align="center"><kbd><img src="assets/qd1amtdzb8.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, để tính tích phân này, đầu tiên ta nhận xét hàm số trong tích phân là 
> hàm **chẵn (g(-x) = g(x))**, nên **tích phân từ -inf:inf trở thành 2* tích phân 
> từ 0:inf**, và khi đó **có thể bỏ dấu trị tuyệt đối**
>
>
>
> **2 * ∫ 0:inf  z * (1/√2π) * e^(-z^2/2) dz**
>
>
>
> = **2 * (1/√2π)** * ∫ 0:inf z * e^(-z^2/2) dz (i)
>
>
>
> Tới đây ta mới dụng một kĩ thuật trong tích phân gọi **U-SUBSTITUTION**:
> (Đã học trong MIT 18.01)
>
>
>
> Đặt u = -z^2/2 ⇨ du = -zdz ⇔ zdz = -du
>
>
>
> z = 0 ⇨ u = 0; z -> infinity ⇨ u -> -infinity
>
>
>
> Xét ∫ 0:inf z * e^(-z^2/2) dz
>
>
>
> = ∫ 0:-inf e^u zdz
>
>
>
> = **- ∫0:-inf e^u du** 
>
>
>
> Theo **Fundamental Theorem of Calculus Part 2**
>
>
>
> = - [nguyên hàm của e^u] | 0:-infinity = - [e^(-infinity) - e^0] = - [0 - 1] = **1**
>
>
>
> Vậy tích phân cần tính có kết quả là 2* (1/√2π) * 1 = 2* (1/√2π) = 2/√2π) = **√(2/π)**

<br>

<a id="node-1eheyrs"></a>

<p align="center"><kbd><img src="assets/g92ga6gl8wf.png" width="80%"></kbd></p>

> [!NOTE]
> Gs cho rằng đây là một ví dụ nữa cho thấy ta **không nhất thiết lúc nào cũng
> phải dùng 2D LOTUS** khi gặp function 2 variable

<br>

<a id="node-mzxy5ua"></a>

<p align="center"><kbd><img src="assets/kevt1exa2.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/engzxft5yqr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gzqfyiqwlj.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo ta sẽ qua một trong hai **Multi-variate distribution** quan trọng là **Multinomial** (cái kia là **Multi-normal**).
>
>
>
> Thế thì Kí hiệu là **Mult(n, p)** giống như **Binomial (n, p)** có điều **p** bây giờ là **VECTOR** **các xác suất pj, j=1,2...k**
>
>
>
> Và vì vậy pj thỏa hai điều kiện: 1) **Không âm** và 2) **Tổng pj bằng 1**
>
> Multinomial distribution

<br>

<a id="node-t0yxx0o"></a>

<p align="center"><kbd><img src="assets/k2p7nepu2xq.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì **Mult(n,p) là sự mở rộng của Bin(n, p)**. Trong Binomial, ta nhớ bối
> cảnh là **n Bern(p) i.i.d trials** và **X là số trial success**. Thì như vậy mỗi
> trial  chỉ có 2 possible outcome là **success** hoặc **failure**, tức là 2 categories.
>
>
>
> Thì với **Mult(n, p)** các trial sẽ có **k possible values**, với **xác suất tương ứng
> là p1,...pk**

<br>

<a id="node-75hzl6i"></a>

<p align="center"><kbd><img src="assets/xi6115fkpd8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/z90347rpf.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì với **Bin(n, p)** r.v **X chỉ là một NUMBER**, mang giá trị là **số Bern(p) trial success**.
>
>
>
> Còn ở đây, khi nhìn nhận một trial **có thể cho k possible outcomes**, ta có thể **thay** chuỗi n
> **trial** bằng n **object** cần phân loại thành k loại.
>
>
>
> Thì khi đó **X1** là **số object thuộc loại 1**, **Xk là số object thuộc loại k**.
>
>
>
> Để rồi X sẽ là **VECTOR**: (X1, X2...Xk)
>
>
>
> Và như đã nói **p_j** sẽ là **xác suất trial có outcome là j**, hay xác suất object thuộc loại j

<br>

<a id="node-zzb8yre"></a>

<p align="center"><kbd><img src="assets/x8icj2fpjcl.png" width="80%"></kbd></p>

> [!NOTE]
> Và từ đó ta có **JOINT DISTRIBUTION** (**JOINT PMF**):
> **P(X1=n1, X2=n2, ... Xk=nk)**

<br>

<a id="node-9bgfgci"></a>

<p align="center"><kbd><img src="assets/pdwr8hfvry.png" width="80%"></kbd></p>

> [!NOTE]
> Ta sẽ lập luận như sau, gs đề nghị ta **hình dung** **chuỗi số** **23311112221** là **kết quả của n
> trials / objects với n = 11**
>
>
>
> Thì đây là **n independent events**, theo **định nghĩa của independent events:**
>
>
>
> **P của chuỗi kết quả cụ thể** như trên = P(intersection của các events) = **tích của P mỗi events:**
>
>
>
> Nói rõ hơn: Chuỗi kết qủa cụ thể của 11 trial (chú ý bây giờ không còn là Bern (p) trial đâu nhé
> vì mỗi trial có tới k possible outcomes) 23311112221 sẽ là intersection của
>
>
>
> (1st trial ra 2, x,x,x....x) ∩ (x, 2nd trial ra 3, x,...x) ∩ (x, x, 3rd trial ra 3) ∩ ...
>
>
>
> Trong đó (1st trial ra 2, x, x, x....x) là event: {s ∈ S: "1st trial = 2"} thể hiện set mọi possible
> outcome khi thực hiện 11 trials sao cho lần thứ nhất đều ra 2. Đây là ta đang cố diễn đạt event
> này trong original sample space.
>
>
>
> Dĩ nhiên (1st trial ra 2, x, x, x....x) có thể thể hiện bởi event (1st trial ra 2) vốn dĩ là một event
> trong sample space chỉ có k possible outcome. Nhưng hai event này matching 1-1 với nhau, vì
> khi lần thứ nhất ra 2 thì đồng nghĩa event (1st trial ra 2, x, x, x....x) xảy ra và ngược lại.
>
>
>
> Do đó ta được phép tính P(1st trial ra 2, x, x, x....x) = P(1st trial ra 2) và nó bằng p2 (trial có k
> possible outcome với xác suất là p1, p2...pk)
>
>
>
> Tương tự (x, 2nd trial ra 3, x,...x) = p3 Rồi, P("23311112221") = P[(1st trial ra 2, x,....x) ∩ (x,
> 2nd trial ra 3, x,...x) ∩ (x, x, 3rd trial ra 3) ∩ ...]
>
>
>
> = P(1st trial ra 2, x,....x) * P(x, 2nd trial ra 3, x,...x) * P(x, x, 3rd trial ra 3) ∩ .. | Do các event đều
> độc lập do đề nói các trial là độc lập.
>
>
>
> = P(1st trial ra 2)*P(2nd trial ra 3)*.....*P(n'st trial ra 1) = p2*p3*...p1
>
>
>
> Thế rồi, **trong n events đó**, có:
>
>
>
> **n1 (=5) events** outcomelà **loại 1** với xác suất xảy ra là **p1**.
>
>
>
> **n2 (=4) events** outcome là l**oại 2** với xác suất xảy ra là **p2**....
>
>
>
> Vậy tích n của P các events = [**p1*p1..(n1=5 lần)**] * [**p2*p2*..(n2=4 lần)**] ...
>
>
>
> = **p1^n1 * p2^n2 *...pk^nk**
>
>
>
> Event (X1=n1(=5), X2=n2(=3),..Xk=nk) **không chỉ có một chuỗi cụ thể** như trên mà có thể có
> **chuỗi khác** với cùng các con số nhưng s**ắp xếp thứ tự khác nhưng đều có n1=5 lần ra loại 1**
> (tức là trong chuỗi có 5 số 1), và đều có n2=3 lần ra loại 2 (tức là có 4 con số 2)..
>
>
>
> Ví dụ 12121211332 là một outcome như vậy cũng thuộc event (X1=n1(=5), X2=n2(=3),..Xk=nk)
>
>
>
> Do đó event (X1=n1,...Xk=nk) là **Union** của các **Disjoint event**, mà mỗi event là một cách
> sắp xếp khác nhau của các kết quả.
>
>
>
> Vậy ta cần ĐẾM **SỐ CÁCH SẮP XẾP** này, hay, số disjoint event nói trên
>
>
>
> Thế thì đầu tiên là ta sẽ **nhân cho số hoán vị** khi coi mọi object là khác nhau: n!
>
>
>
> Nhưng vì có n1 object 1, n2 object 2...và ta **không quan tâm thứ tự của các object cùng loại**,
> nên ta sẽ adjust bằng cách **chia bớt cho n1!, n2!...**
>
>
>
> Như vậy event (X1=n1, ..Xk=nk) là Union của **n!/ (n1!n2!...)** Disjoint events
>
>
>
> Theo **axiom 2**:
>
>
>
> **P(X1=n1, ..Xk=nk) = Tổng của n!/ (n1!n2!...) xác suất của mỗi event,**
>
>
>
> mà chúng **đều có giá trị là p1^n1 * p2^n2 *... pk^nk** (vì như đã nói chúng chỉ khác cách  sắp
> xếp của các kết quả
>
>
>
> Do đó kết qủa là **P(X1=n1, ..Xk=nk)** =  [**p1^n1 * p2^n2 *...pk^nk] *n!/ (n1!n2!...)**
>
>
>
> Với điều kiện là **n1+n2..nk = N**, nếu không thì P(X1=n1, ..Xk=nk) = 0 vì không thể có khả
> năng nào mà n1+n2..nk khácN
>
> MULT(N, p) JOINT PMF: P(X1=n1, ..Xk=nk) =  [p1^n1 * p2^n2 *...pk^nk] *n!/ (n1!n2!...)
> (n1+n2+...= N). p = (p1, p2, ...pn)

<br>

<a id="node-4zrhw1f"></a>

<p align="center"><kbd><img src="assets/ll1ihwipa6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0t48t7tzlgz.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp sau khi có công thức **Joint PMF**. Ta sẽ thử tìm **Marginal PMF**
>
>
>
> Thế thì nếu **X ~ Mult k (n, p), (k là chỉ có k class),** **Marginal distribution of Xj sẽ là gì** gs yêu cầu thử suy nghĩ
>
>
>
> Thử trả lời: **Xj**, như định nghĩa, là số trial có kết quả, hay **object thuộc loại j trong n trials / objects**.
>
>
>
> Do đó, khi xét distribution của Xj, tức là ta đang chỉ quan tâm đến câu hỏi trong n trials, tổng số trials có kết quả là
> loại j  là bao nhiêu
>
>
>
> Vậy điều này tương đương, trong n trials, ta chỉ quan tâm mỗi trial outcome **có phải là loại j hay không**.
>
>
>
> Từ đó có thể xem như ta có n trial mà mỗi trial có hai possible value là success với **xác suất success** là **p_j**
> và failure với xác suất là 1 - p_j. Có nghĩa là các trial **Bern(p_j)**. Vậy **Xj ~ Binomial (n, p_j)**
>
> MARGINAL DISTRIBUTION Xj SẼ LÀ BIN(N, p_j)

<br>

<a id="node-2131y2l"></a>

<p align="center"><kbd><img src="assets/7xxae392kka.png" width="80%"></kbd></p>

> [!NOTE]
> Gs: Correct. Lập luận đó cũng là story proof

<br>

<a id="node-5qbvjob"></a>

<p align="center"><kbd><img src="assets/5xumzb919n9.png" width="80%"></kbd></p>

> [!NOTE]
> Và từ đó ta cũng **có ngay E(Xj)** là **n*p_j** và **Var(Xj)** = **n*p_j*(1-p_j)** mà ta
> đã chứng minh ở Bin(n, p)

<br>

<a id="node-9d0h8ia"></a>

<p align="center"><kbd><img src="assets/z9h4pgc7yug.png" width="80%"></kbd></p>

<br>

<a id="node-ztd7cty"></a>

<p align="center"><kbd><img src="assets/s07ne8mh4j.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/7lqjag2qqna.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo gs nói về một **Property** khác của **Multinomial**, gs lấy ví dụ **một đất nước** có **10 đảng phái** và ta có **n người dân**, mỗi
> người **THUỘC DUY NHẤT VÀ ĐỀU THUỘC MỘT ĐẢNG**
>
>
>
> Khi đó ta có **X = (X1, X2...X10)** ~ **Mult (n, (p1,p2...p10))**. Thế thì bây giờ câu chuyện đặt ra là **giả sử có 2 đảng lớn**
> là **1, 2**. Và ta muốn **gom các đảng còn lại làm một đảng thứ 3**. Tức **Y = (X1, X2, X3+X4+...X10)**
>
>
>
> Thì câu hỏi là **Y sẽ có distribution như thế nào**.
>
>
>
> Thì đơn giản là: Ta vẫn c**ùng một câu chuyện**, chỉ khác là bây giờ **có 3 loại**. Và **xác suất một object thuộc loại 3
> sẽ là tổng xác suất p3+p4...p10**. Còn hai loại kia thì vẫn vậy.
>
>
>
> Nên Y = [X1, X2, X3+X4..X10] ~ **Mult(n, [p1, p2, p3+p4+...p10])**
>
>
>
> Gs nói thêm điều kiện phải là mỗi object chỉ thuộc về một category duy nhất
>
> X = (X1, X2...X10) ~ Mult (n, (p1,p2...p10)) thì Y = (X1, X2, X3+X4+...X10) sẽ
> có distribution ra sao

<br>

<a id="node-swgw9kp"></a>

<p align="center"><kbd><img src="assets/j40kxod56bf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/fg6ft82n9gk.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo là một ví dụ nữa về **property** của **Multinomial distribution.**
>
>
>
> Đó là cho **X ~ Mult_k (n, p)** Đương nhiên với multinomial ta **tự hiểu X là vector** có **k
> component** **[X1, X2...Xk]** và **p** cũng là vector **[p1, p2...pk]** mang giá trị ví dụ **p_j** là **xác
> suất của việc object / trial thuộc loại j tương ứng**. Để **Xj sẽ là số object/trial thuộc loại j trong n
> objects**
>
>
>
> Bài toán đặt ra là, **biết X1=n1**. Ta cần **tìm distribution của (X2, ...Xk)**.
>
>
>
> Thế thì gs cho rằng ta sẽ thấy là vì **bản chất bài toán không thay đổi**, nên  **(X2,...Xk) vẫn là r. v
> (vector) ~ Multinomial**, có điều, **tham số của nó sẽ khác**.
>
>
>
> Đó là nó sẽ là **n-n1 thay vì n**, điều này dễ hiểu, vì "coi như" **chỉ còn n-n1 trials / objects**  Và
> **xác suất cũng thay đổi**, vì sẽ là **SAI** nếu ta để **p = [p2, ...pk]** vì tổng của chúng **KHÔNG
> CÒN BẰNG 1**. Do đó ta **phải tính lại**, gọi là [**p'2, p'3...p'k**]
>
>
>
> Thế thì, ví dụ xét **p'2**, ta sẽ lập luận như sau:
>
>
>
> **p'2** sẽ là **xác suất một object không phải loại 1**, **thuộc loại 2**. Hay nói cách khác, là **xác
> suất một object là loại 2** nếu, **dựa trên** việc **nó không phải là loại 1**.
>
>
>
> **p'2 = P(thuộc loại 2 | không phải loại 1)**
>
>
>
> Thì theo **định nghĩa** **conditional probability**, ta sẽ có
>
>
>
> **P(thuộc loại 2 | không phải loại 1)** = **P(thuộc loại 2, không thuộc loại 1) / P(không thuộc loại 1)**
>
>
>
> i) **P(thuộc loại 2, không thuộc loại 1)** thì là **intersection** của **hai sự kiện** nhưng **[thuộc loại
> 2**] thì **đồng** **nghĩa** [**không thuộc loại 1**] rồi 
>
>
>
> (tức là một possible outcome mà thuộc event /subset [loại 2] cũng đương nhiên thuộc 
> event/subset [không phải loại 1]), nên **intersection** của hai sự kiện này = **event "thuộc loại 2"**
>
>
>
> Hay: (thuộc loại 2) ⊂ (không thuộc loại 1) 
>
>
>
> ⇨ **(thuộc loại 2, không thuộc loại 1) = (thuộc loại 2)**
>
>
>
> để từ đó **P(thuộc loại 2, không thuộc loại 1) = P(thuộc loại 2)**
>
>
>
> ii) **P(không thuộc loại 1)** = **1-p1** = **p2 + p3 + ...pk**
>
>
>
> Do đó **p'2 = p2 / (p2 + p3 + ...pk)** và tương tự p'3, p'4 cũng vậy vì các loại khác có vai trò như nhau
> (symmetry)
>
>
>
> Vậy (X2, X2..Xk) sẽ ~ **Mult k-1 (n-n1, p=(p'2, p'3, ...p'k))**
>
>
>
> Và đó chính là **RENORMALIZING.** Gs nói thêm qua ví dụ trên ta thấy chỉ cần dựa vào lập luận
> để suy ra distribution mà không cần tính toán

<br>

<a id="node-pereckz"></a>

<p align="center"><kbd><img src="assets/fb1y3d14m1f.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ckw9mrbkche.png" width="80%"></kbd></p>

> [!NOTE]
> Bài toán tiếp theo, ta sẽ biết về **Cauchy** **distribution**.
>
>
>
> Cho **X, Y ~ N(0,1)**, **i.i.d** thì distribution của **T = X/Y** gọi là **Cauchy** distribution ta sẽ **đi tìm PDF** của nó
>
>
>
> Đầu tiên gs nói cái Cauchy distribution này nó **không có mean**, khi ta **tính E(T) thì nó sẽ blow up**, không tính
> đươc. Và do Var(T) = E[(T - ET)^2] hay ET^2 - (ET)^2, nên không có mean thì **cũng không có variance.**
>
> CAUCHY DISTRIBUTION

<br>

<a id="node-dvnya0v"></a>

<p align="center"><kbd><img src="assets/nzviv7ugf4.png" width="80%"></kbd></p>

> [!NOTE]
> gs nói tính chất **không có mean, không variance** cũng chưa phải là điểm
> khiến Cauchy được gọi là **EVIL** DISTRIBUTION (vì **cũng có những cái
> khác** có tính chất này).
>
>
>
> Mà sự thật là khi ta học qua **Định luật số lớn (Law of Large Number)** thì ta
> sẽ biết rằng, nếu **tính trung bình của một số lượng lớn các i.i.d r.v** thì  nó
> sẽ **dần dần gần với mean**. (tất nhiên qua bài đó mới hiểu)
>
>
>
> Nhưng ở đây gs nói **Cauchy nó không tuân theo định luật** này. Mà ví von
> như khi ta **thu thập thêm càng nhiều dữ liệu** thì **thường** nó sẽ **cho ta
> có thể kết luận** về thông tin gì đó.
>
>
>
> Nhưng **với Cauchy thì không**, dù có average nhiều Cauchy r.v thì nó vẫn là
> Cauchy (Chưa hiểu lắm nhưng gs chỉ nói sơ)

<br>

<a id="node-uygnycf"></a>

<p align="center"><kbd><img src="assets/gxhq1vox42j.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì để **tìm PDF**, gs cho rằng ta **hoàn toàn có thể dùng LOTP -
> Law Of Total Probability** và **conditioned on Y**, để tính.
>
>
>
> Nhưng ông sẽ **dùng cách tiếp cận khác**, tính **CDF**, và như đã
> biết khi có CDF, lấy **derivative** sẽ cho ta **PDF**

**🔗 See also:** [linked note](#node-mafpvdr)

<br>

<a id="node-kagfwqx"></a>

<p align="center"><kbd><img src="assets/f2mk3fi0sa6.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên gs dựa trên **tính chất Symmetry của N(0,1)** mà ta đã chứng minh
> rằng với **Z~N(0,1)** thì **(-Z) cũng ~ N(0,1)**, gs lập luận rằng vì vai trò của X,
> Y như nhau (symmetry) và tính symmetry của N(0,1) nên
>
>
>
> **KHÚC NÀY CHƯA HIỂU**
>
>
>
> P(X/Y ≤ t) = P(X/|Y| ≤ t)

<br>

<a id="node-uim6914"></a>

<p align="center"><kbd><img src="assets/men3i0zu0o8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gx1f9zdm1mv.png" width="80%"></kbd></p>

> [!NOTE]
> Từ đó cho phép ta đưa **X/|Y| ≤ t** ⇔ **X ≤ t|Y|** (again, hiểu đây cùng là một event)
>
>
>
> Và ta sẽ tính **P(X ≤ t|Y|)**
>
>
>
> Thế thì ta cần nhớ rằng, **PDF** của Joint Distribution định nghĩa rằng:
>
>
>
> **P((X, Y) thuộc vùng A) = tích phân kép trên A f(x,y)dxdy**
>
>
>
> Và X/Y ≤ t mà ta đã chứng minh nó tương đương X ≤ t|Y| chính là xác định một vùng A như vậy:
> Hay nói cách khác P(X ≤ t|Y|) là P(X,Y thuộc vùng A sao cho X ≤ t|Y|)
>
>
>
> Nên **P(X ≤ t|Y|)** có thể được tính = **∫∫A f_X,Y(x,y)dxdy**
>
>
>
> Thế thì như gs đã nói nhiều lần, cái chính, **cái khó là xác định limit của tích phân kép** này. Như
> ví dụ trước gs cũng đã dạy rằng tích phân dxdy hay dydx gì cũng được nhưng nếu dxdy, (tức "làm"
> với x trước, thì cái tích phân ở ngoài là "của" y, và limit của tích phân ở ngoài luôn phải là number,
> còn cái tích phân ở trong là "của" x, làm trước, thì limit có thể phụ thuộc y.
>
>
>
> Do đó, ta xác định limit của tích phân ở ngoài là **-inf:inf** và limit của tích phân của x là **-inf : t|y|**
> vì đang xét vùng A là vùng mà X ≤ t|Y|

**🔗 See also:** [linked note](./lec_19_joint_conditional_and_marginal_distribution.md#node-o82ibj6)

<br>

<a id="node-ydfssgd"></a>

<p align="center"><kbd><img src="assets/exbb6k1v8h7.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo f(x,y) như đã biết, là JOINT PDF của X,Y. Mà vì **đã nói X,Y i.i.d**
> tức là Independent. Do đó, dựa vào định nghĩa của Independent r.v.s về
> **JOINT** và **MARGINAL** **distribution** cho ta biết **JOINT PDF f_X,Y(x, y)** bằng 
> **TÍCH** của **MARGINAL PDF** f_X(x) và f_Y(y)
>
>
>
> f_XY(x, y) = f_X(x)*f_Y(y)
>
>
>
> Chú ý ghi f_X(x) là ý chỉ marginal PDF của X, cũng chính là PDF của X.
> (marginal PDF  của X chỉ là ám chỉ việc tính PDF của X bằng cách
> marginalizing Joint PDF mà thôi)
>
>
>
> Mà với **Z ~ N(0,1)** ta biết PDF của nó **f(z) = (1/√2π) * e^(-z^2/2)**
>
>
>
> Nên Marginal PDF của X, Y tức là PDF của X, Y ~ N(0,1) ta có công thức là:
>
>
>
> f_X(x) = **(1/√2π) * e^(-x^2/2)**  và f_Y(x) = **(1/√2π) * e^(-y^2/2)**
>
>
>
> Đưa vào tích phân sẽ là:
>
>
>
> **∫-inf:inf ∫-inf:t|y| (1/√2π) * e^(-x^2/2) * (1/√2π) * e^(-y^2/2) dxdy**
>
>
>
> Thì khi tính tích phân của x, ta coi y như constant, nên những gì không dính
> đến x,  và những term liên quan đến y có thể đưa ra ngoài tích phân
>
>
>
> **(1/√2π) ∫-inf:inf  e^(-y^2/2) ∫ -inf:t|y|  (1/√2π) * e^(-x^2/2) * dxdy**

<br>

<a id="node-ynmtz3o"></a>

<p align="center"><kbd><img src="assets/4i6omatsddu.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, xét cái inner integral đối với x:
>
>
>
> ∫ -inf:t|y|  (1/√2π) * e^(-x^2/2) * dx
>
>
>
> gs nhắc lại rằng, ta đã từng nói là **không thể tính được tích phân** này ở dạng
> **closed form** (search "không thể  tính" )
>
>
>
> Nhưng sau đó ta đã biết **có thể tính được bằng cách khác** khá rắc rối. Hơn
> nữa, ta cũng đã biết đây chính là **Φ(t|y|)** - ý nghĩa là hàm Φ là **CDF** của
> **Standard Normal N(0,1)**, evaluated tại t|y| (theo link màu cam)

**🔗 See also:** [linked note](./lec_13_normal_distribution.md#node-j00lakx) · [linked note](#node-u5syd2o)

<br>

<a id="node-4v3e2cq"></a>

<p align="center"><kbd><img src="assets/91oxa6petuh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/io0ocvu6sg9.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, thay cái tích phân của x bằng **Φ(t|y|)**. 
>
>
>
> (1/√2π) ∫-inf:inf  e^(-y^2/2) **[** ∫ **-inf:t|y|  (1/√2π) * e^(-x^2/2) * dx ]** dy 
>
>
>
> = (1/√2π) ∫-inf:inf  e^(-y^2/2) **Φ(t|y|)** dy (1)
>
>
>
> Ta sẽ nhận định tiếp rằng function trong dấu tích phân y tức:
>
>
>
> **e^(-y^2/2) Φ(t|y|)**,
>
>
>
> Bây giờ là **hàm chẵn** (vì nó có dạng g(y^2, |y|) nên g(-a) = g(a) thành ra ta sẽ **thay tích phân -inf:inf**
> bằng **2 * tích phân từ 0:inf** và **bỏ dấu trị tuyệt đối của y**
>
>
>
> Để rồi ở ngoài là 2 nhân với 1/√(2π) = **√(2/π)
>
>
>
> (1) = (2/√2π) ∫0:inf  e^(-y^2/2) Φ(ty) dy**

<br>

<a id="node-f968zqv"></a>

<p align="center"><kbd><img src="assets/kdlduhfo1vo.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo đại khái là, ta bị kẹt ở chỗ không biết tính tiếp theo như thế nào.
>
>
>
> Nhưng có một sự thật là **ta thực ra đang tìm PDF của Cauchy r.v V = X/Y,**
> chẳng qua là đang dùng cách tiếp cận là **tìm CDF của U trước**, rồi **take
> derivative  để có PDF**.
>
>
>
> Do đó gs cho rằng ta sẽ đi **lấy derivative của cái tích phân mà ta chưa làm
> xong này.**
>
>
>
> ====Ôn lại kiến thức Calculus, bài trước theo link ta đã biết **FTC** đã cho biết:
>
>
>
> Nếu F(x = ∫-a:x f(t)dt thì d/dx F(x) = f(x).
>
>
>
> Vậy thì, bây giờ mới nói qua quan hệ của CDF và PDF. Giả sử r.v X có pdf là
> f(x). Thì định nghĩa của **CDF của r.v X** là F(t) = P(X ≤ t) cũng là P(-inf < X ≤ t)
>
>
>
> Và theo định nghĩa ta có: P(-inf < X ≤ t) và với continuous rv với pdf f(x) thì
> dựa trên định nghĩa này thì xác suất của event X ∈ (-inf, t] sẽ là tích phân
> trên đoạn này của pdf: ∫-inf:t f(t)dt. 
>
>
>
> Vậy ta có (chỉ là dựa định nghĩa của pdf): P(X ≤ t) = P(-inf < X ≤ t) = ∫-inf:t f(x)dx
>
>
>
> Mà P(X ≤ t) theo định nghĩa của CDF, = F(t), nên ta có F(t) = ∫-inf:t f(x)dx
>
>
>
> Tới đây ta mới dựa trên FTC 2 để suy ra F'(t) = f(t)
>
>
>
> ====
>
>
>
> Quay lại bài toán này, ta đang có xây dựng CDF **F_V(t)** của Cauchy r.v V =
> X/Y  thì bây giờ đ**ương nhiên ta cũng lấy đạo hàm theo t** để có PDF của V
> **f_V(t): F'(t) = f(t) chỉ là ta đang đang có F(t) ở dạng tích phân**

**🔗 See also:** [linked note](./lec_12_discrete_vs_continuous_the_uniform.md#node-xyq3zk4)

<br>

<a id="node-31f2lmn"></a>

<p align="center"><kbd><img src="assets/fauljr8261k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/n6u48ctxyhs.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì cái nãy giờ ta đang làm, như đã nói là Joint PDF **P((x,y) thuộc A)** với **A area mà X<=t|Y| và bản chất** là 
> đó là CDF của V=X/Y, và là hàm theo t: F(t) = P(X/Y<=t)
>
>
>
> Vậy thì khi l**ấy derivative đối với t** này, mà function đang có dạng của một cái tích phân. Thì gs cho biết **có
> một Theorem nói rằng nếu cái hàm số trong tích phân well-behave, thì theorem cho phép "đạo hàm của tích
> phân = tích phân của đạo hàm"** (đại khái là vậy, cái này cũng tương tự như đạo hàm của tổng bằng tổng
> đạo hàm vậy vì bản chất tích phân là tổng)
>
>
>
> Nên thành ra để ta sẽ tính **đạo hàm THEO t** của **[ √(2/π) ∫ 0:inf e^-y^2/2 Φ(ty) dy]**
>
>
>
> Ta sẽ chuyển thành **√(2/π) ∫ 0:inf của [đạo hàm theo t của e^-y^2/2 Φ(ty)] dy** (**1)**
>
>
>
> Xét [**đạo hàm theo t của e^-y^2/2 Φ(ty)**]:
>
>
>
> thì tính đạo hàm theo t thì **e^-y^2/2 là hằng số, đưa ra ngoài đạo hàm**. **(2)** 
>
>
>
> F'(t) = √(2/π) ∫ 0:inf e^-y^2/2 [**đạo hàm theo t của Φ(ty)**] dy
>
>
>
> Còn **đạo hàm theo t của Φ(ty)** tính như sau:
>
>
>
> Theo chain rule: dΦ(ty)/dt = d Φ(ty) / d(ty) * d(ty) / dt = **d Φ(ty) / d(ty) * y** **(3)**
>
>
>
> Và **d Φ(ty) / d(ty) thì là g**ì? 
>
>
>
> Đã biết Φ(x) là CDF của Standard Normal X ~N(0,1), = P(X ≤ x) và ta có Φ'(x) / dx = f(x) ⇨ d Φ(ty) / d(ty)
> = f(ty) với f là PDF của Standard Normal, = 1/(√2π) e^-(ty)^2/2 **= 1/(√2π) e^-t^2y^2/2 (4)
>
>
>
> Vậy từ (1) (2) (3) (4) ta có: 
>
>
>
> F'(t) = √(2/π) Tích phân 0:inf của {e^-y^2/2 * y * [1/(√2π) e^-t^2y^2/2] } dy**

**🔗 See also:** [linked note](./lec_22_transformations_convolution.md#node-9vpzcjt)

<br>

<a id="node-9ytpjgf"></a>

<p align="center"><kbd><img src="assets/khgbzm9xcwl.png" width="80%"></kbd></p>

> [!NOTE]
> F'(t) = √(2/π) Tích phân 0:inf của {e^-y^2/2 * y * [1/(√2pi) e^-t^2y^2/2] } dy
>
>
>
> Rút gọn ta có
>
>
>
> i) √(2/π) * 1/(√2π) = 1/π
>
>
>
> ii) e^(-y^2/2) * e^(-t^2y^2/2) = e^[-(1+t^2)y^2/2
>
>
>
> Nên F'(t) =
>
>
>
> **(1/π) Tích phân 0:inf của {y * e^[-(1+t^2)y^2/2} dy**
>
>
>
> ===
>
>
>
> Tới đây thì ta có một tích phân **CÓ THỂ giải được**, bởi để ý thấy "y^2/2" và y ở
> dưới chính là gợi ý cho ta dùng **U-SUBSTITUTION (1801 sẽ học)**
>
>
>
> Đặt u = -(1+t^2)y^2/2 => du = -(1+t^2)2y/2 = -(1+t^2)ydy
>
>
>
> <=> ydy = -[1/(1+t^2)]du
>
>
>
> Tính lại biên: y=0 => u=0, y -> infinity => u-> -infinity
>
> Tích phân trên trở thành 
>
>
>
> (1/π) Tích phân 0:-inf của e^udu
>
>
>
> = (1/π) * -[1/(1+t^2)] * Tích phân 0:-inf của e^udu
>
>
>
> = -1 / [π*(1+t^2)] * [nguyên hàm của e^u (= e^u)] | 0: -inf
>
>
>
> = -1 / [π*(1+t^2)] * [e^(-inf) - e^0] 
>
>
>
> = -1 / [π*(1+t^2)] * [0-1] 
>
>
>
> = -1 / [π*(1+t^2)] * (-1) 
>
>
>
> **= 1 / [π*(1+t^2)]**

<br>

<a id="node-gxhyke5"></a>

<p align="center"><kbd><img src="assets/uuio0mbufqg.png" width="80%"></kbd></p>

<br>

<a id="node-mafpvdr"></a>

<p align="center"><kbd><img src="assets/h1folo1om7.png" width="80%"></kbd></p>

> [!NOTE]
> vài phút cuối gs nói về **cách làm thứ 2** áp dụng **Law of Total Probability** mà gs cho rằng
> cũng có thể dùng hồi nãy
>
>
>
> Với cách tiếp cận **wishful** như đã biết ta **ước rằng, đã biết y**, để mà **conditioned on y**. Thì
> P(X ≤ t|Y|) trở thành 
>
>
>
> **tích phân -inf:inf P(X ≤ t|Y| | Y=y)**
>
>
>
> Tới thời điểm này có thể đã khá quen với lập luận vì sao mà ta có cái này (cũng chính là
> Law of Total Probability), nhưng cứ lập luận lại cho nhớ lâu:
>
>
>
> Đó là bởi nếu X, Y discrete thì:
>
>
>
> X ≤ t|Y| sẽ = [Union của (X<=t|Y|, Y=y) với mọi possible value y of Y]
>
>
>
> Đây là kết quả từ **logic của set theory** rằng event A = **union** của **mọi (intersection**
> giữa A và các disjoint part của B):
>
>
>
> A = (A,B1) U (A,B2)....(A, Bn) với B1, B2, ... là các disjoint event và B1 U B2 ..U Bn = B
>
>
>
> Do đó P(A) = P[(A,B1) U (A,B2)....U (A, Bn)]
>
>
>
> Và vì các Bj với j=1,2..n disjoint, nên các (A,Bj) với j=1,2...n cũng disjoint
>
>
>
> Do đó theo **Axiom 2** của probability: P[(A,B1) U (A,B2)....U (A, Bn)] = Tổng j=1,2.. P[(A, Bj)]
>
>
>
> Do đó P(X<=t|Y|) = P[Union của (X<=t|Y|, Y=y) với mọi possible value y of Y]
>
>
>
> = Tổng {mọi possible value của y} P(X<=t|Y|, Y=y)
>
>
>
> Áp dụng thêm **conditional theorem**: P(X<=t|Y|, Y=y) = P(X<=t|Y| | Y=y) * P(Y=y)
>
>
>
> Nên **P(X<=t|Y|) = Tổng {mọi possible value của y}:  P(X<=t|Y| | Y=y) * P(Y=y)**
>
>
>
> Trong discrete case như đã biết P(Y=y) là PMF của y
>
>
>
> ====
>
>
>
> Còn với continuous case thì nó sẽ tương đương:
>
>
>
> **P(X ≤ t|Y|) = tích phân -inf:inf P(X ≤ t|Y| | Y=y) f_Y(y)dy,** 
>
>
>
> trong đó f_Y(y) mà gs ghi là Φ(y) là **PDF của y,** và Y như đã biết là N(0,1)

**🔗 See also:** [linked note](#node-uygnycf)

<br>

<a id="node-u5syd2o"></a>

<p align="center"><kbd><img src="assets/keo3meoq1ui.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, vì X ≤ t|Y| dựa trên condition on Y=y thì ta có thể **thay thế y vào |Y|**
>
>
>
> Hay nói cách khác **event (X ≤ |Y| | Y = y)** chính là **event X ≤ ty**
>
>
>
> nên P(X ≤ t|Y| | Y = y) = P(X ≤ ty | Y=y)
>
>
>
> Và ở đây ta được học một lập luận quan trọng là: **Nếu X,Y independent thì
> khi đã gắn giá trị Y=y vào thì X ≤ ty | Y = y ta có thể bỏ đi phần condition**
>
>
>
> Tức là (X ≤ ty | Y=y) = (X ≤ ty)
>
>
>
> Và khi đó ta có **P(X ≤ ty)**, và vì **X~N(0,1)** nên **P(X ≤ ty) chính là Φ(ty)** và bài
> toán trở thành:
>
>
>
> **tích phân -inf:inf f Φ(ty) f_Y(y)dy**
>
>
>
> giải tiếp tại đây như hồi nãy (theo link xanh)

**🔗 See also:** [linked note](#node-ynmtz3o)

<br>

