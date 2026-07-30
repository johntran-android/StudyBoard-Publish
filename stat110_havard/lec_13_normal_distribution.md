# Lec 13: Normal Distribution

📊 **Progress:** `33` Notes | `42` Screenshots

---
<a id="node-3uqquog"></a>

## Lec 13: Normal Distribution

<br>

<a id="node-xnitk2d"></a>

## TÓM TẮT:

- TÍNH UNIVERSALITY CỦA UNIFORM PART 2:

Nếu X ~ F thì F(X) ~ U(0,1)

-  Cách hiểu đúng về F(X) với F(x) = 1 - e^-x phải là bỏ X vào x ở đây để
có F(X) = 1 - e^-X

- Áp dụng vào có thể dùng F(X) để xem thử nó có tuân theo Uniform hay
không, nếu không thì có thể có gì đó không đúng

- Áp dụng khác là giúp ta simulating các observed data ~ F, bằng cách
sampling từ U(0,1) và bỏ vào function Finv

- Tính chất symmetry của Uniform. Đó là, nếu U ~ Uniform
(0,1) thì 1-U cũng ~ Uniform (0,1)

- ĐỊNH NGHĨA CỦA INDEPENDENT R.VS DỰA TRÊN CDF

P(X1 ≤ x1, X2 ≤ x2, ... Xn ≤ xn) = P(X1 ≤ x1)*P(X2 ≤ x2)*..... P(Xn ≤ xn) thì Xj 
sẽ independent VỚI MỌI x1, x2,...xn

- Với discrete random variable thì cũng tương tự, nhưng ta sẽ làm với PMF:

Các X1, X2...Xn sẽ gọi là independent nếu:

JOINT PMF P(X1=x1, X2=x2...Xn=xn) = P(X1=x1)*P(X2=x2)*...P(Xn=xn) (tích các
PMF)

- Ví dụ để cho thấy tại sao pair-wise independent không đủ để kết luận independent. 

Cho X1, X2 là ~ Bern(0.5) và i.i.d và X3 = X1+X2. Xét từng cặp thì biết thằng
này không giúp biết thằng kia ⇨ pair-wise independent nhưng xét bộ 3 thì biết
X1, X2 biết ngay X3 ⇨ Nếu chỉ dựa vào pair-wise indepedent thì không đủ kết
luật cả đám independent

- Standard Normal distribution:

Thường dùng chữ Z để kí hiệu cho Normal distribution r.v

Gs cho rằng ta chỉ cần biết là f(z) có công thức này c*e^(-z^2/2),

- Chứng minh NORMALIZING CONSTANT là c = 1/√2π

- pdf: (1/√2π) e^-z^2/2

- CHỨNG MINH X ~ N(0,1) EX = 0 DỰA VÀO SYMMETRY

- CHỨNG MINH X ~ N(0,1) VarX = 1

- Φ(z) = tích phân từ -infinity tới x của [e^(-t^2/2)dt]

<br>

<a id="node-ow88gux"></a>

<p align="center"><kbd><img src="assets/j2id4resnpe.png" width="80%"></kbd></p>

> [!NOTE]
> Tếp nối bài trước, bữa trước ta đã biết **tính chất Universality của Uniform**
> distribution. Theo đó **nếu ta có một CDF function F** (bất cứ function nào
> **continuous**, **non-decreasing** (luôn tăng, hoặc đi ngang chứ không giảm) và
> **có giá trị từ 0 đến 1 khi input từ -inf đến inf**).
>
>
>
> Gs nói rằng ta **assume** F **strictly increasing** là để cho **dễ** thôi, chứ CDF
> **đương nhiên có thể có flat region.**
>
>
>
> Khi đó, nếu tìm **F_inverse** và **apply nó vào một Uniform (0,1) random
> variable** thì ta **sẽ có một random variable X tuân theo distribution có CDF là
> F**.
>
>
>
> Viết ngắn gọn là nếu **U ~ Unif(0,1), thì F_inv(U) ~ F**
>
>
>
> Thế thì nay gs cho biết: **ngược lại**, **nếu ta có X ~ F**. Thì **U = F(X) sẽ là
> random variable tuân theo Uniform (0,1)**
>
>
>
> Ở đây, X là random variable tuân theo CDF là F. Và gs cho rằng **ta có thể
> thấy lạ khi bỏ nó vào chính hàm F để có F(X)**.
>
>
>
> Nhưng điều này **hoàn toàn hợp lệ**. Vì **X LÀ RANDOM VARIABLE**, KHI
> APPLY **F LÊN NÓ ĐỂ CÓ U = F(X) THÌ U CŨNG LÀ MỘT RANDOM
> VARIABLE**.
>
>
>
> Và **theorem** này **cho ta khẳng định** rằng **U sẽ ~ Uniform (0, 1)**
>
> TÍNH UNIVERSALITY CỦA UNIFORM PART 2:
>
>
>
> Nếu **X ~ F thì F(X) ~ U(0,1)**

<br>

<a id="node-wzt6fs9"></a>

<p align="center"><kbd><img src="assets/z0s211iilha.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì **chỗ này** ta **cần giải nghĩa F(X)** cho đúng. Sẽ là **SAI** nếu interpret như vầy:
>
>
>
> CDF F(x) theo định nghĩa là P(X<=x), thì khi gắn X vào để có F(X) nó sẽ bằng
> P(X<=X). Mà **X<=X là event luôn xảy ra** nên P(X<=X) = 1 vậy **F(X) = 1**.
> Nhắc lại: Đây là cách hiểu **SAI** về F(X).

<br>

<a id="node-dc235q7"></a>

<p align="center"><kbd><img src="assets/3su6b1cfep2.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì cách **HIỂU ĐÚNG về F(X)** (tức **apply function F vào random variable
> X**, nó **khác với khi ta ghi F(x) thì chỉ là nói về bản thân hàm F**, lúc này x là dummy
> variable, có thể ghi F(t), F(u) đều được miễn là đang hiểu nó là hàm CDF của r.v X) 
>
>
>
> Đó là **ví dụ ta có function F(x) = 1 - e^-x** với x > 0, đây là một CDF quan trọng sẽ 
> học sau.
>
>
>
> Vậy cách **hiểu đúng về F(X)** phải là **bỏ X vào x ở đây để có F(X) = 1 - e^-X**
>
>
>
> Có nghĩa là ta phải **thể hiện F(x) ở dạng "làm gì đó lên x" và thay X vào x**. Chứ
> **không phải là thay X vào x trong P(X<=x)**.
>
>
>
> Hiểu nôm na, cái việc **F(x) = P(X<=x) là ý nghĩa của CDF**, nhưng **apply F lên X**
> thì phải **thay X vào công thức của hàm F** chứ không phải thay X vào x trong
> P(X<=x)
>
> Cách HIỂU ĐÚNG về F(X)

<br>

<a id="node-wkwlrzz"></a>

<p align="center"><kbd><img src="assets/9nnu76be8aq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là gs nói cái này **rất hữu ích**, ví dụ khi ta học qua lớp **Statistic
> 111** **Statistical Inference**. Nôm na là **có khi ta có một random variable
> phức tạp** X (ý là, một random variable có công thức phức tạp), và ta **có thể
> dùng F(X)** để **xem thử nó có tuân theo Uniform hay không**, **nếu không
> thì có thể có gì đó không đúng**

<br>

<a id="node-tlw1lgs"></a>

<p align="center"><kbd><img src="assets/px5si8lnywj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/y4mfk94jdjr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0jghs4ii64lh.png" width="80%"></kbd></p>

> [!NOTE]
> Gs quay lại nói rằng cái **Universality theorem** cũng **rất hữu ích**. Ví dụ như ta **có một CDF F(x)** như vầy F(x) = **1 - e^-x** 
> (nó là một distribution quan trọng mà ta sẽ học sau - **Exponential (1)**). Và **ta muốn simulate (kiểu như sampling)**
> **các random variable X thuộc distribution có CDF là F**.
>
>
>
> Thế thì **Universality theorem cho ta cách làm đơn giản**. Đầu tiên ta sẽ **tìm F_inv**. Đơn giản là **cho y = F(x) = 1-e^x**
> và **giải ra x = G(y)** thì khi đó **G(y) chính là F_inv**.
>
>
>
> Ở đây ta giải: y = 1 - e^x <=>  e^x = 1-y <=> (lấy ln base e hai vế) ln e^-x = ln(1-y) <=> -x = ln(1-y)
>
>
>
> <=> x = - ln(1-y) => F_inv là **-ln(1-y)**
>
>
>
> Từ đó **sampling một random variable Uniform (0,1)** và gắn vào ta sẽ có **X = - ln(1-U)** thì ta **sẽ có một random 
> variable ~ F.**
>
>
>
> Và **việc sampling từ Uniform (0,1) thì máy tính làm rất dễ**. Nên nhờ Universal theorem mà ta có thể **dễ dàng
> simulating các random variable từ một CDF F(x)** bất kì (**miễn là tìm được F_inv**)

<br>

<a id="node-kc3criv"></a>

<p align="center"><kbd><img src="assets/i6z1dfdot4q.png" width="80%"></kbd></p>

> [!NOTE]
> tiếp gs nói về **tính chất symmetry của Uniform**. Đó là, **nếu U ~ Uniform
> (0,1)** thì **1-U cũng ~ Uniform (0,1)**
>
> Tính chất symmetry của Uniform. Đó là, nếu U ~ Uniform
> (0,1) thì 1-U cũng ~ Uniform (0,1)

<br>

<a id="node-ls6gfok"></a>

<p align="center"><kbd><img src="assets/yfg333sehgd.png" width="80%"></kbd></p>

> [!NOTE]
> và **a + bU** **cũng là Uniform** với **interval nào đó**.
>
>
>
> Tuy nhiên **lưu ý**, **a + bU là linear transformatio**n nên **nó vẫn là Uniform**,
> nhưng **nếu apply một non-linearity lên U** thì ta sẽ **không còn là Uniform** nữa.
>
>
>
> Ví dụ **U^2 không còn là Uniform**
>
> a + bU cũng là Uniform
> với interval nào đó.

<br>

<a id="node-jus2iit"></a>

<p align="center"><kbd><img src="assets/7l6o06q4e6p.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/s42393rp5as.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây gs quay lại **chính thức nói về** khái niệm **INDEPENDENT RANDOM VARIABLES**:
>
>
>
> Những bài trước, ta đã được **biết sơ** về định nghĩa của independent r.v, khi đó gs nói rằng ta có thể **gắn nó với định nghĩa independent events**. 
> Và bữa trước là trong bối cảnh ta làm việc với các discrete r.v, nên sử dụng PMF. Để rồi **X,Y independent nếu các event X=x và Y=y independent**,  
> và cái này thì **chiếu theo định nghĩa của independent events** sẽ có nghĩa là **P(X=x, Y=y) = P(X=x)*P(Y=x)** mang ý nghĩa là Joint PMF = tích các PMF 
> tương ứng với xác suất của joint event bằng tích xác suất từng event)
>
>
>
> Thế thì ở đây ta cũng có thể có định nghĩa independent r.v nhưng dùng **CDF** trong bối cảnh ta đang xét **continuous** r.v
>
>
>
> Đó là nếu các random variable X1, X2...Xn có tính chất **P(X1 ≤ x1, X2 ≤ x2, ... Xn ≤ xn) = P(X1 ≤ x1)*P(X2 ≤ x2)*..... P(Xn ≤ xn) thì Xj sẽ independent**
> **VỚI MỌI x1, x2,...xn** 
>
>
>
> Thì ở đây **(X1 ≤ x1, X2 ≤ x2, ... Xn ≤ xn)** gọi là **JOINT CDF**,  [X1 ≤ x1, X2 ≤ x2, ... Xn ≤ xn] là **JOINT EVENT** (intersection của n event)
> như đã biết
>
>
>
> Như vậy các r.v **INDEPENDENT** nếu như **Joint CDF** = **tích các CDF**
>
>
>
> Thế thì gs chú ý là, cái này khi **so với định nghĩa của independent event** ta thấy nó **CÓ VẺ ĐƠN GIẢN HƠN**. Vì ta nhớ ví dụ với **3 events A, B, C**
> được gọi là **Independent** nếu thỏa các điều kiện sau:
>
>
>
> P(A,B,C) = P(A)*P(B)*P(C) ; P(A,B) = P(A)*P(B) ; P(B,C) = P(B)*P(C), P(A,C) = P(A)*P(C)
>
>
>
> Tương tự với 4 event, A,B,C,D thì phải có thêm các equation P(B,C,D) = P(B)*P(C)*P(D)...
>
>
>
> Tuy nhiên thật ra ở đây ta **chú ý đến vế "for all x1, x2....xn"** tức là **mọi possible value của X1, X2...Xn**
>
> ĐỊNH NGHĨA CỦA INDEPENDENT R.VS DỰA TRÊN CDF
>
>
>
> P(X1 ≤ x1, X2 ≤ x2, ... Xn ≤ xn) = P(X1 ≤ x1)*P(X2 ≤ x2)*..... P(Xn ≤ xn) thì Xj sẽ independent
> VỚI MỌI x1, x2,...xn

<br>

<a id="node-gfyor8l"></a>

<p align="center"><kbd><img src="assets/pzt6je9q8z.png" width="80%"></kbd></p>

> [!NOTE]
> Với **discrete** random variable thì cũng tương tự, nhưng ta sẽ làm với **PMF**:
>
>
>
> Các X1, X2...Xn sẽ gọi là independent nếu:
>
>
>
> **JOINT PMF** P(X1=x1, X2=x2...Xn=xn) = P(X1=x1)*P(X2=x2)*...P(Xn=xn) (tích các
> PMF)

**🔗 See also:** [linked note](./lec_18_mgf_continued.md#node-rvqmvgf)

<br>

<a id="node-qdyl86a"></a>

<p align="center"><kbd><img src="assets/8mnes8wvyp6.png" width="80%"></kbd></p>

> [!NOTE]
> Và gs cho biết **định nghĩa về Independent r.v như vậy** có nghĩa là v**iệc
> biết gía trị của một subset nào các random variables** cũng **không giúp ích
> gì cho ta biết giá trị của các random variable còn lại** (mà ta chưa biết)

<br>

<a id="node-l7k65ku"></a>

<p align="center"><kbd><img src="assets/983qb47bo39.png" width="80%"></kbd></p>

> [!NOTE]
> Gs cho **ví dụ** để cho thấy tại sao **pair-wise independent không đủ** để
> **kết luận independent**. 
>
>
>
> Cho **X1, X2 là ~ Bern(0.5) và i.i.d** và **X3 = X1+X2** 
>
>
>
> Thế thì chúng **pair-wise independent**, vì việc **biết X1, hoặc X2 riêng lẻ** **không
> cho thông tin gì về X3.**
>
>
>
> Nhưng **xét thành nhóm cả ba** thì **rõ ràng việc biết X1, X2 sẽ cho rất rõ
> giá trị của X3.** Do đó v**iệc independent từng cặp (pair-wise) không
> đủ để kết luận cả nhóm X1,X2,X3 independent**

<br>

<a id="node-aw3vg7m"></a>

<p align="center"><kbd><img src="assets/5xbw19x5qzj.png" width="80%"></kbd></p>

> [!NOTE]
> Ta học qua **Normal distribution**, có tên khác là **Gaussian** distribution.
>
>
>
> Tiếng Việt là **PHÂN PHỐI CHUẨN**
>
>
>
> mà theo gs là **distribution quan trọng nhất** trong statistic. Và sở dĩ nó 
> quan trọng như vậy là bởi liên quan đến **Central Limit Theorem**
>
> NORMAL DISTRIBUTION - PHÂN PHỐI CHUẨN

<br>

<a id="node-ws5suwd"></a>

<p align="center"><kbd><img src="assets/bt1pf3w3dgp.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là gs nói sơ về **Central Limit Theorem**, nói rằng **tổng
> của các i.i.d random variables** sẽ **tuân theo Normal distribution**

<br>

<a id="node-d4e6v2t"></a>

<p align="center"><kbd><img src="assets/wbe6goo0a5.png" width="80%"></kbd></p>

> [!NOTE]
> Ta sẽ **xét Normal N(0,1)** gọi là s**tandard normal distribution** có **mean**
> bằng **0** và **variance** **1** (Ta sẽ chứng minh điều này sau)

<br>

<a id="node-3n2mwsd"></a>

<p align="center"><kbd><img src="assets/zq9d2q9lsd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, người ta **thường dùng chữ Z** để kí hiệu cho **Normal
> distribution r.v**
>
>
>
> Gs cho rằng ta **chỉ cần biết** là f(z) có công thức này **c*****e^(-z^2/2),**
>
>
>
> Với **e^-z^2/2** xuất phát từ triển khai Taylor gì đó
>
>
>
> Và **constant c** đóng vai trò giúp **normalizing để tổng area bằng 1**.
>
>
>
> Và ta sẽ nhận xét rằng nó có tính **SYMMETRY**, khi **z âm hay dương** đều
> ra **kết quả giống nhau**. Và khi **z tiến về -infinity và +infinity** thì **f(z) tiến
> về 0 rất nhanh.**
>
> Z ~ N(0,1) f(z) có công thức
> này c*e^(-z^2/2),

<br>

<a id="node-t7l1bl3"></a>

<p align="center"><kbd><img src="assets/gbies7w1zww.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **ta sẽ đi tìm constant c**, thì đầu tiên ta sẽ **tìm [tích phân từ
> -infinity tới infinity của f(z)dz]**. Thì chính nó, đúng hơn là **1 chia cái này
> chính là c** vì **c là constant giúp normalize để area bằng 1**, mà **area
> chính là cái [tích phân từ -infinity tới infinity của f(z)dz]** (ví dụ area = 2 thì c
> = 1/2 để normalize area  = 2/2 = 1)
>
>
>
> Thế thì gs nói **nếu ta thử tính cái tích phân này** (để rồi lấy 1 chia cái đó để
> có c) thì **sẽ không làm được**. Dù có tiếp cận theo cách nào như tìm
> nguyên hàm F(z) của f(z) để áp dụng Fundamental Theorem of Calculus part
> 2 rằng tích phân từ a đến b của f(x)dx bằng F(b) - F(a) cũng sẽ không được.
>
>
>
> Thậm chí **có một định lý** gì đó **đã chứng minh không thể** tính tích phân
> không xác định của f(z) = e^(-z^2/2) (chính là cái ta đang muốn làm) ở dạng
> **closed-form.**
>
> Không thể tính tích phân không xác định của f(z) =
> e^(-z^2/2) ở dạng closed-form.

<br>

<a id="node-oybdapd"></a>

<p align="center"><kbd><img src="assets/u6n1kgh7led.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói tuy vậy ta **vẫn có thể dùng Taylor series**. Nên **khi nói ko thể làm
> được** thì  **ý** **là** không thể làm được ở dạng **closed-form thôi
>
>
>
> (Hiểu đại khái closed-form có nghĩa là ta có thể viết ra kết quả ở dạng
> một công thức hữu hạn, dùng các phép toán cơ bản và function quen 
> thuộc)**

<br>

<a id="node-qip3oo8"></a>

<p align="center"><kbd><img src="assets/filo0h1qkqc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/r1rcb9qmjtr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **tuy rằng không thể tìm được anti-derivative**, nhưng **vẫn có cách tìm tích phân** của bài toán này **không cần anti-derivative**
> (ý là không cần dựa vào FTC part 2)
>
>
>
> Gs cho biết **có một cách** vừa **stupid** vừa **brilliant** mà **không phải lúc nào cũng work** nhưng **work trong trường hợp này**. Đó là ta viết
> thêm (**NHÂN THÊM**) **một cái tích phân (mà ta không tính được) nữa.**
>
>
>
> Và vì **z** ở đây chỉ là **dummy variable**, tức là một kí hiệu, **có thể dùng chữ gì** cũng được, nên ta sẽ **thay cái đầu bằng x**, **cái sau bằng y**

<br>

<a id="node-5pwmnfa"></a>

<p align="center"><kbd><img src="assets/ekoc5thqm0u.png" width="80%"></kbd></p>

> [!NOTE]
> Thì nó **trở thành tích phân kép** như vầy.
>
>
>
> **∫-inf:inf ∫-inf:inf e^-(x^2+y^2)/2 dxdy**
>
>
>
> **Gs nói không có gì khác biệt** với cái trên [tích phân f(x)dx]*[tích phân f(y)dy] cả,
> vì đơn giản là:
>
>
>
> **Khi tính tích phân kép** này, **ta sẽ làm (tích tích phân) với x trước**, khi đó **giữ
> y là constant**. Và và **vì giữ y làm constant** nên **hòan toàn có thể đưa nó ra
> đằng trước** để trở thành dạng [tích phân f(y)dy]*[tích phân f(x)dx] như trên
>
>
>
> (Đây là kiến thức đã học trong bài về double integral của MIT 18.02)
>
>
>
> Tóm lại, ý nói hai cái trên thật ra là như nhau và không có gì phức tạp khi làm vậy

<br>

<a id="node-b5lfn9k"></a>

<p align="center"><kbd><img src="assets/m9n7wto1m2.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì gs nói là **dù vậy thì việc chuyển thành bài toán tính tích phân kép**
> cũng **có vẻ chẳng dễ hơn** **là mấy**.
>
>
>
> Nhưng gs cho rằng **điểm mấu chốt là x^2 + y^2**, ông nói **bất cứ khi nào ta
> thấy cái này** thì ta **nên liên tưởng đến định lý Pytagore**. (Pythagoras
> theorem).
>
>
>
> Và từ đó **gợi ý rằng** mình nên **chuyển sang POLAR COORDINATE** - biểu
> diễn một điểm bằng bán kính r và góc θ thay vì x, y (CARTESIAN)

<br>

<a id="node-0jzc33e"></a>

<p align="center"><kbd><img src="assets/hqdp0kjvo1i.png" width="80%"></kbd></p>

> [!NOTE]
> Và từ đó, ta **chuyển bài toán thành tích phân này**:
>
>
>
> ∫**0:2π ∫0:inf e^(-r^2/2) dr dθ**
>
>
>
> Soi sáng bởi 18.02 giúp ta hiểu thêm **tại sao bound inner integral (r) là
> 0:infinity**
>
>
>
> Trong bài 17 của 18.02 ta làm một ví dụ **tính tích phân kép trên area** là một
> **hình tròn** (**paraboloid** **z = 1 - x^2 - y^2** cắt mặt phẳng **xy** tại **đường
> tròn** bán **kính 1**, xuất phát từ bài toán tính thể tích của vùng nằm trong giới
> hạn bởi paraboloid và mặt xy),khi đó vì giới hạn trong area như vậy nên
> bound của inner integral r (mang ý nghĩa là khi giữ θ fixed thì r có range từ đâu
> tới đâu) được nhiên sẽ là từ 0 đến 1. Còn ở đây, tích phân gốc có bound của x,
> y đều là -infinity đến infinity tức **vùng đang tính tích phân là toàn bộ mặt
> phẳng**, do đó khi chuyển qua polar coordinate thì **bound của r sẽ là từ 0 đến
> infinity.**
>
>
>
> Còn đương nhiên bound của θ cũng từ 0 -> 2π để cover mọi hướng rồi.

<br>

<a id="node-cyfy2yd"></a>

<p align="center"><kbd><img src="assets/ifwdajm512p.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói rằng **kết quả nó sẽ cần thêm yếu tố Jacobian nữa**. (Cái này rõ ràng là
> mình sẽ cần đến bài **Polar Coordinate** của 1802 mới hiểu, hiểu sơ thì nó là **det
> của Jacobian matrix**, sẽ ra là **r**)
>
>
>
> Gs đề nghị xem lại math review handout. Và yếu tố Jacobian ở đây là r.
>
>
>
> ====
>
>
>
> Sau khi đã học xong 18.02 (lecture 17,18) có thể hiểu tại sao khi chuyển tích phân
> từ x, y sang u, v thì ta cần một scaling factor để liên hệ giữa dA (=dxdy) trong x, y
> coordinate với dA' trong u, v cooridnate.
>
>
>
> Thì trong 18.02 ta đã chứng minh để hiểu rằng scaling factor này chính là
> determinant của Jacobian matrix (matrix of partial derivative). Do đó khi chuyển từ
> x,y sang polar coordinate. J sẽ là:
>
>
>
> x = r*cos(θ), y = r*sin(θ). Nên J = [x_r, x_θ; y_r, y_θ] 
>
>
>
> (x_r là kí hiệu trong 18.02 cho partial derivative của x đối với r)
>
>
>
> = [cos(θ), r*(-sin(θ)) ; sin(θ), r*cos(θ)]
>
>
>
> Và det J = cos(θ)*r*cos(θ) - r*sin(θ)*sin(θ) = r(sin^2(θ) + cos^2(θ)) = **r
>
>
>
> Và r dương nên |det J| = r. Vậy scaling factor là r nên phải dùng r*dr*dθ**
>
>
>
> (nói thêm trong đó mình cũng biết ở bối cảnh đởi bíen tích phân thì người ta gọi
> **det của matrix Jacobian** là **Jacobian** luôn)

<br>

<a id="node-fs6brg7"></a>

<p align="center"><kbd><img src="assets/oqxkuakjaxj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zyg0s48w4s.png" width="80%"></kbd></p>

> [!NOTE]
> Và bài toán bây giờ đã trở nên dễ hơn. Ta sẽ **tính tích phân với r trước**, đặt **u = r^2/2** thì **du = rdr**
>
>
>
> Từ đó, nó trở thành **tích phân từ 0 đến infinity e^-u du**, và dùng **FTC part 2**, nó sẽ bằng 
> [nguyên hàm của e^-u](infinity) - [nguyên hàm của e^-u](0)  
>
>
>
> (nguyên hàm của e^-u là **-e^(-u)**, vì d [-e^(-u)] / du = -e^(-u)*(-1) = e^(-u)
>
>
>
> = -e^-infinity -(-e^0) = 0 - (-1) = **1**
>
>
>
> Tiếp, tính tích phân từ 0 đến 2*pi **1***d_theta = [nguyên hàm của 1] | từ 0 đến 2pi
>
>
>
> (nguyên hàm của 1 theo y) là y, vì dy/dy = 1
>
>
>
> = x | 0:2pi = 2pi - 0 = **2pi**

<br>

<a id="node-8j5zw4c"></a>

<p align="center"><kbd><img src="assets/cnp2yv6ife.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng ta **phải nhớ** là **ta đang tính BÌNH PHƯƠNG** của **tích phân từ
> -infinity tới infinity e^(-x^2/2) dx**
>
>
>
> Do đó, kết quả sẽ là **căn bậc 2 của 2π**
>
>
>
> Và đây chính là **NORMALIZING CONSTANT**
>
> NORMALIZING CONSTANT là √2π

<br>

<a id="node-430taui"></a>

<p align="center"><kbd><img src="assets/l666m27i5m.png" width="80%"></kbd></p>

> [!NOTE]
> Và như vậy, ta đã tìm ra c. Để PDF của Normal N(0,1) là:
>
>
>
> **(1/√2π) e^-z^2/2**
>
>
>
> Gs nói **nhờ vậy** mà **khi nhìn vào công thức** của **Normal distribution**
> ta có thể **hiểu chữ pi là từ đâu ra**:
>
>
>
> Nó chính là **xuất hiện khi ta chuyển từ Cartesian coordinates sang Polar
> coordinates**

**🔗 See also:** [linked note](#node-88g780u)

<br>

<a id="node-u3y0li3"></a>

<p align="center"><kbd><img src="assets/3a7ttaocacr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/2qwvl9ionnu.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6hbr6ymsk9p.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/bwgc6p0u5t8.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo ta sẽ chứng minh **mean (tức là average, expected value) N(0,1) là 0**. Theo định nghĩa, với continuous random
> variables **E(X) bằng tích phân từ -infinity tới infinity của x*f(x)dx**
>
>
>
> Vậy ở đây, là **tích phân -inf:inf z * f(z)dz** với **f(z) = [1/√(2π)] * e^(-z^2/2)**
>
>
>
> Thế thì cái này **đơn giản là bằng 0**, **khỏi cần tính toán**. Là bởi tính chất **SYMMETRY** trong đó nói rằng: Nếu g(x) là
> một **HÀM LẺ** (odd even) tức **g(-x) = -g(x)** thì **tích phân từ -a đến a g(x)dx bằng 0**
>
>
>
> Và gs nói ta có thể **dựa vào định lý này** hoặc **tự chứng minh lại** bằng cách **tính tích phân thành 2 phần  sẽ thấy
> chúng cancel nhau**
>
> CHỨNG MINH X ~ N(0,1) EX = 0
> DỰA VÀO SYMMETRY

**🔗 See also:** [linked note](./lec_18_mgf_continued.md#node-dfvtp2n)

<br>

<a id="node-87i4n8f"></a>

<p align="center"><kbd><img src="assets/rxwlmbdr9no.png" width="80%"></kbd></p>

> [!NOTE]
> Do đó E(X) = 0

<br>

<a id="node-ee1vgaz"></a>

<p align="center"><kbd><img src="assets/qu1u38rj5ng.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo ta tính **Variance**. Như đã biết nó là **average của sự phân tán**: **E[(Z-EZ)^2]**
> và khi triển khai ra ta có công thức thứ hai: **E(Z^2) - (EZ)^2**
>
>
>
> Thử triển khai lại như sau: E[(Z-EZ)^2] = E[Z^2-2ZEZ + (EZ)^2]. Theo **linearity**
> = E[Z^2] - E[2ZEZ] + E[(EZ)^2]
>
>
>
> E[2ZEZ] = 2EZ * E[Z] (ở đây vì 2 và EZ - mean của r.v là constant, nên đưa ra ngoài)
> thành ra nó là 2(EZ)^2
>
>
>
> E[(EZ)^2] cũng là (EZ)^2 vì (**EZ)^2 là constant**
>
>
>
> Vậy ta có E(Z^2) - 2(EZ)^2 + (EZ)^2 = E(Z^2) - (EZ)^2
>
>
>
> === 
>
>
>
> Thế thì ta sẽ **cần tính E(Z^2)**. Nhờ **Law Of Unconscious Statistician (LOTUS)** mà ta 
> có thể **không cần phải tìm PDF của Z^2**, và **chỉ việc dùng ngay PDF của Z**
>
>
>
> Nên E(Z^2) = tích phân từ -infinity đến infinity **z^2** f(z) dz với f(z) đã biết (có thể đưa 
> constant 1/√(2π) ra ngoài)

<br>

<a id="node-r1pxekn"></a>

<p align="center"><kbd><img src="assets/dv32kiv747h.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, **z^2*e^(-z^2/2)** cũng là **EVEN** FUNCTION (HÀM CHẴN, f(x) = f(-x))
>
>
>
> Đó đó ta có thể c**ho tích phân này (-inf:inf) bằng 2 lần tích phân từ 0 đến
> infinity**. Mục đích để **bớt phải làm việc với negative part.**

<br>

<a id="node-g3rctyr"></a>

<p align="center"><kbd><img src="assets/g1tp20uopvu.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì chi tiết có thể sẽ được **nói đến kĩ hơn trong 18.01** nhưng theo đây
> ta có thể hiểu là **partial integration** cho phép tính **tích phân từ a đến b của
> u(x)v'(x)dx = [u(x)v(x)] | a->b - tích phân từ a đến b của u'(x)v(x)dx**

<br>

<a id="node-88g780u"></a>

<p align="center"><kbd><img src="assets/jelmm17psuh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/2g8hblgw39j.png" width="80%"></kbd></p>

> [!NOTE]
> Đến đây ta phải dùng **tích phân từng phần** "**integration by part**" để tính.
>
>
>
> Ta có ở đây, cần tích tích phân z**^2e^(-z^2/2)dz** thì ta sẽ tách thành **z * z*e^(-z^2/2)dz**
>
>
>
> Và từ đó đặt **u = z**, **dv = z*e^(-z^2/2)** => z*e^(-z^2/2)dz = v'(z)dz 
>
>
>
> Vì khi đó cái ta cần tính trở thành tích phân (*) của **u(z) v'(z)dz**
>
>
>
> Và ý nghĩa của việc tách z^2 ra là để ta có v'(z) như vậy, **giúp ta có thể tìm đươc v**:
>
>
>
> **v(z) = -e^(-z^2/2)**. Có thể **check lại** bằng cách lấy **derivative của v** sẽ dễ thấy cho ra: 
>
>
>
> dv/dz = d[-e^(-z^2/2)] / dz = - [d[e^(-z^2/2)] / d(-z^2/2)] * d(-z^2/2) / dz = - [e^(-z^2/2)] * [-2z/2]
>
>
>
> = - [e^(-z^2/2)] * (-z) = **z*e^(-z^2/2)**
>
>
>
> ====
>
>
>
> Vậy từ đó ta có thể áp dùng Integration by part vừa nói:
>
>
>
> (2/√2pi) * tích phân u(z)v'(z)dz = [u(z)v(z)] | 0->infinity - tích phân từ 0-infinity u'(z)v(z)dz
>
>
>
> = (2/√2pi) * [u(z)v(z)] | 0->infinity - tích phân từ 0-infinity u'(z)v(z)dz
>
>
>
> i)  **[u(z)v(z)] | 0->infinity** = **u(infinity)*v(infinity) - u(0)v(0)** = infinity * -e^infinity^2/2 - 0 * -e^0^2/2
>
>
>
> = infinity * 0 - 0*1 = **0**
>
>
>
> ii) - tích phân từ 0-infinity [u'(z)v(z)dz] = - tích phân từ 0-infinity [**1*** -e^(-z^2/2) dz] (vì u = z => u'(z) = **1**)
>
>
>
> Đưa dấu - của e ra ngoài để cùng với dấu - có sẵn trỏ thành +
>
>
>
> = + **tích phân từ 0-infinity e^(-z^2/2) dz**
>
>
>
> Và nó **chính là 1/2 của cái mà ta vừa tính hồi nãy** (ra sqrt(2*pi))
>
>
>
> Vậy kết quả là (2/√2pi) * ( 0 + √2*pi / 2) = **1
>
>
>
> Vậy là ta đã chứng minh xong Variance của Z ~ Norm(0,1) = 1**
>
> CHỨNG MINH X ~ N(0,1) VarX = 1

**🔗 See also:** [linked note](#node-430taui)

<br>

<a id="node-j00lakx"></a>

<p align="center"><kbd><img src="assets/x9mro8gj27.png" width="80%"></kbd></p>

> [!NOTE]
> Mấy phút cuối gs nói về **một số notation**: Φ (capital fi) là kí hiệu để chỉ CDF của
> **Standard normal (Normal(0,1))**
>
>
>
> Như đã biết CDF của continuous random variable là **tích phân từ -infinity tới
> x của PDF**. Nên ở đây:
>
>
>
> Φ(z) = tích phân từ -infinity tới x của [e^(-t^2/2)dt] 
>
>
>
> = (1/√2*pi) * tích phân từ -infinity tới x của [e^(-t^2/2)dt] 
>
>
>
> (again t chỉ là dummy name, để tránh trùng với x, nhưng không quan trọng)

**🔗 See also:** [linked note](./lec_12_discrete_vs_continuous_the_uniform.md#node-px4qd31) · [linked note](./lec_12_discrete_vs_continuous_the_uniform.md#node-9i8dw33) · [linked note](./lec_20_multinomial_and_cauchy.md#node-ynmtz3o)

<br>

<a id="node-n0oxgsf"></a>

<p align="center"><kbd><img src="assets/1gdbsjo3wzm.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng là một tính chất của Φ: Φ(-z) = 1 - Φ(z) được rút ra
> từ tính **symmetry**. Gs nói tự tìm hiểu hoặc bài sau sẽ quay lại

<br>

