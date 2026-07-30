# Lec 24: Gamma Distribution & Poisson

📊 **Progress:** `24` Notes | `24` Screenshots

---
<a id="node-15h5whs"></a>

## Lec 24: Gamma Distribution & Poisson

<br>

<a id="node-txytdzp"></a>

<p align="center"><kbd><img src="assets/8eufdpmnzp7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là gs cho rằng ta nên biết về **công thức Sterling**, trong đó
> nó cho phép tính **xấp xỉ của n! = [√(2π*n)](n/e)^n**

<br>

<a id="node-vlpe8st"></a>

<p align="center"><kbd><img src="assets/d35t9u07sof.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì bài toán đặt ra, là nếu ta phải **tìm một đường**, **nối các điểm rời rạc**,
> mỗi điểm là kết quả của **1!, 2!, 3!...n!**
>
>
>
> Đương nhiên ta **có vô số cách để vẽ** đường nối các điểm này.
>
>
>
> Thế thì c**ó một cách tiêu chuẩn** để làm điều này, nó gọi là **Gamma function**.
>
>
>
> Đại khái là bài trước ta đã biết **Beta** distribution, dù chưa xong và ta còn quay
> lại nhưng nó có **liên hệ gần gũi với Gamma function**.
>
>
>
> Gs nói thêm **Gamma là một trong những function nổi tiếng nhất** của toán học

<br>

<a id="node-tg90580"></a>

<p align="center"><kbd><img src="assets/kderuhs8apl.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì **Gamma function** G(a) có công thức là
>
>
>
> G(a) = **∫ 0:inf x^a e^-x dx / x** . Và function này **xác định** với **a là  số
> thực dương.**
>
>
>
> *(do trong note mình dùng tạm kí tự G cho nhanh, chứ gs dùng kí tự
> Gamma viết hoa)
>
>
>
> Gs cho rằng vì **một số lí do** mà ta sẽ **giữ 1/x** chứ không gom
> **x^a/x = x^(a-1)**

**🔗 See also:** [linked note](#node-97f2xof)

<br>

<a id="node-0rf6fyg"></a>

<p align="center"><kbd><img src="assets/vb53ib9f3yp.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là gs nói về việc **tại sao a = 0** hoặc **âm** thì hàm Gamma này, tức
> integration này **không xác định**. Đại khái là việc này giống như mình **tìm limit
> của một dãy số có vô số hạng tử** (với số hạng tổng quát là x^a * e^-x / x với
> x = vô số giá trị từ 0 đến infinity vậy
>
>
>
> Cái này cũng liên quan đến việc **xác định dãy số có hội tụ (converge) hay
> không** tức là, tổng của dãy số có thể được biểu diễn bởi một con số tổng
> quát hay không.
>
>
>
> Thì đây cũng vậy, bản chất của tích phân cũng là một tổng. Do đó, có thể
> tích phân không converge. Giống như ở đây nếu như a <= 0 thì tích phân sẽ
> không hội tụ.
>
> Nói chung là khúc này liên quan đến **điều kiện hội tụ của tích phân**. Ta sẽ
> quay lại chỗ này sau khi học 18.01

<br>

<a id="node-i9dsus7"></a>

<p align="center"><kbd><img src="assets/us3tmbynquq.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì, như đã nói **G(n)** chỉ xấp xỉ **n!** Vì thật ra nó G(n) = (n-1)!
>
>
>
> Và một công thức recursive là G(x+1) = x*G(x)
>
>
>
> Đại khái là gs **nói ta cũng không cần biết nhiều về gamma function** trong
> class này. **Chỉ cần biết công thức của nó như trên** và hai công thức này là
> đủ

<br>

<a id="node-o7l8llf"></a>

<p align="center"><kbd><img src="assets/eq6khu4y9he.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là có thêm 1 cái nữa ta nên biết là **gamma(1/2) = sqrt(π)**. Gs giải
> thích sơ, sở dĩ như vậy là do nó có **liên quan đến Normal distribution**. (nói
> chung ông cũng chỉ nói sơ, không rõ lắm)
>
>
>
> Còn Gamma (3/2) thì theo Identity trên **Gamma(n+1) = nGamma(n)** thì ta có
> Gamma (3/2) = Gamma(1/2+1) = 1/2Gamma(1/2)

**🔗 See also:** [linked note](./lec_25_order_statistic_conditional_expectation.md#node-6ikcoq7)

<br>

<a id="node-lgsbimy"></a>

<p align="center"><kbd><img src="assets/2i9mw5bz1sw.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là gs nói đó là **tất cả những gì cần biết về Gamma function**. Thế thì
> bây giờ ta sẽ **quay lại nói về gamma distribution**. Câu hỏi là làm sao x**ây dựng
> pdf** của Gamma distribution từ Gamma function.
>
>
>
> Câu trả lời đơn giản là, ta sẽ **normalizing Gamma function để cho integrate của
> nó bằng 1** để thỏa mãn điều kiện valid của PDF.
>
>
>
> Và ta làm điều đó bằng cách, **chia Gamma function cho chính giá trị của Gamma**
> thì từ đó nó sẽ **lòi ra PDF**
>
>
>
> Nói rõ hơn, ta có Gamma function G(a) = **∫ 0:inf (x^a e^-x / x) dx**
>
>
>
> Vậy nếu **chia hai vế cho G(a)** ta sẽ có :
>
>
>
> 1 = [1/G(a)] * ∫ 0:inf (x^a e^-x / x) dx. 
>
>
>
> Vì đ**ây là tích phân theo x**, nên 1/G(a) là constant do đó có thể **đưa G(a) vào tích 
> phân**
>
>
>
> Để được 1 = ∫ 0:inf [1/G(a)] (x^a * e^-x / x) dx
>
>
>
> Khi đó **[1/G(a)] (x^a * e^-x / x)** chính là **PDF** của Gamma distribution **Gamma(a, 1)**
>
> X ~Gamma(a,1) PDF f(x) = [1/G(a)] (x^a * e^-x / x)

<br>

<a id="node-0gj5s98"></a>

<p align="center"><kbd><img src="assets/bssehsp2fjo.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, gs cho biết **Gamma** rất **closely related** với **Exponential** distribution
> trong đó ta nhớ với Expo distribution, nếu **X ~ Expo(1)** thì Y = **X/λ sẽ ~ Expo(λ)**.
>
>
>
> Thì ở đây cũng vậy, **nếu ta có X ~ Gamma(a, 1) thì Y = X / λ  sẽ ~ Gamma(a, λ).**
>
>
>
> Cụ thể là, ta đã biết cái vụ **transformation**. Đó là nếu **Y = g(X)** thì ta sẽ tìm **g_inv**: 
> X = g_Inv(Y) thì khi đó PDF của Y sẽ là **f_Y(y) = f_X(x) dx/dy**
>
>
>
> Và ta cũng nhớ là **có thể dùng dx/dy** hoặc **(dy/dx)^-1**, cái nào **dễ thì dùng**.
>
>
>
> Thế thì y = x/λ <=> x = yλ => **dx/dy = λ,** và ở đây ta đã có x = g_inv(y) = yλ
>
>
>
> Vậy f_Y(y) = f_X(x) * dx/dy = [(1/G(a)) (**x**^a) * (e^-**x**) * (1/**x**)] * λ.
>
>
>
> Đương nhiên ta không quên thay **x = g_inv(y)** để có **function theo y** vì đây là
> PDF của Y:
>
>
>
> f_Y(y) = (1/G(a)) (**λy**)^a * e^-(**λy**) (1/**λy**) * λ.
>
>
>
> = (1/G(a)) (λy)^a * e^-(λy) * (1/**λ**y) * **λ**.
>
>
>
> = **(1/G(a)) (λy)^a * e^-(λy) * (1/y).**
>
>
>
> Vậy PDF của Y~Gamma(a, λ) là: f_Y(y) = **(1/G(a)) (λy)^a * e^-(λy) * (1/y).**
>
> Nếu X ~ Expo(1) thì Y = X/λ sẽ ~ Expo(λ).
>
>
>
> Cũng vậy, nếu ta có X ~ Gamma(a, 1) thì Y = X / λ  sẽ ~ Gamma(a, λ) 
>
>
>
> PDF của Y~Gamma(a, λ) là: f_Y(y) = (1/G(a)) (λy)^a * e^-(λy) * (1/y).

**🔗 See also:** [linked note](#node-hk2er7p)

<br>

<a id="node-dahxnei"></a>

<p align="center"><kbd><img src="assets/1iiqb09v14t.png" width="80%"></kbd></p>

> [!NOTE]
> Thì ví dụ hồi nãy thật ra chưa nói rõ **quan hệ giữa Gamma và Expo**
>
>
>
> Bây giờ gs mới nói về **quan hệ giữa Gamma và Exponential** distribution. Đầu
> tiên review lại một bài toán mà bữa trước đã làm. Và mà nay ta biết nó gọi là 
> **POISSON** **PROCESS**.
>
>
>
> Trong đó ta cho rằng (gỉa định rằng), **số email nhận được** trong **khoảng thời
> gian từ 0 cho đến mốc t**, gọi là **Nt**, là một **Poisson (λt)** r.v. Và yêu cầu **tìm**
> **distribution của T** là **khoảng thời gian cho đến khi nhận email đầu tiên**.
>
>
>
> Ngoài ra có thêm một **giả định nữa** đối với **Poisson** **Process** là **số email nhận
> được trong khác khoảng thời gian không chồng lấn** (disjoint) là **độc lập nhau**
> (trong ví dụ bữa trước khi lần đầu tiên nói về Poisson process hình như không
> nói về giả định thứ 2 này)
>
> POISSON PROCESS

**🔗 See also:** [linked note](./lec_15_midterm_review.md#node-9pnvzz0)

<br>

<a id="node-nqm2i0z"></a>

<p align="center"><kbd><img src="assets/kpnntdpkh6.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là trong lần làm bài toán này bữa trước, gs nói ta **đã thấy nó quan hệ với
> Exponential distribution**. Cụ thể là, ta đã chứng minh, rằng gọi T (như vừa nhắc lại, là **độ dài
> của khoảng thời gian trước khi có email đầu tiên**) thì **T chính là ~ Expo(λ)**
>
>
>
> Và ta chứng minh bằng cách **xây dựng CDF**, để **lấy derivative** cho ra **PDF**. CDF F(t) chính là
> **P(T<=t)**. Thì trong bài toán này ta t**ìm complement** của nó sẽ dễ hơn: **P(T>t).**
>
>
>
> (Again, t, hay u hay x không quan trọng, vì nó chỉ là dummy variable. Cái chính là  hiểu ý
> nghĩa của CDF. ví dụ CDF của X, tức F(t) thì ý nghĩa  là P(X<=t), là tích phân từ 0 đến t của
> f(x) dx với f(x) là PDF. Còn gọi là F(x) cũng được, thì phải hiểu nó là P(X<=x) và bằng tích
> phân từ -inf: x f(x) dx với f(x) là PDF. Nhưng mà như vậy thì dễ lẫn lộn giữa x trong limit tích
> phân và f(x). Thành ra ta nên dùng, cũng như gs hay dùng là F(x) = tích phân -inf đến x
> f(t)dt Vì trong cái kí hiệu tích phân f(t)dt thì t chỉ là dummy variable, cái chính là hiểu f làm
> hàm PDF của X. Chứ gọi tích phân. ...f(z)dz cũng được không sao cả.)
>
>
>
> Quay lại đây, **lí luận mấu chốt** là event [**thời gian cho đến khi nhận email đầu tiên T > t**] 
> cũng chính là / **đồng nghĩa** với event [**từ 0 đến t chả có email nào**]
>
>
>
> Do đó **(T>t)** = **(Nt = 0)**. Vì Nt như đã nói, là **số email nhận dc từ 0 đến mốc t, là một Pois(**λt)
>
>
>
> (** Cái này gọi là **COUNT-TIME DUALITY**)
>
>
>
> Vậy **P(T>t) = P(Nt=0)** (hai event là một thì xác suất đương nhiên bằng nhau)
>
>
>
> Thế mà ta đã assume **Nt ~ Pois(λt)**, nên ta biết PMF **P(Nt=k) = e^(-λt) (λt)^k / k!**
>
>
>
> Vậy P(Nt = 0) = e^(-λt) (λt)^0 / 0! = **e^(-λt) => P(T>t) = e^(-λt)**
>
>
>
> Vậy CDF của T: **F_T(t)** = **P(T<=t)** = 1 - P(T>t) = **1 - e^(-λt)**
>
>
>
> Và như đã nói nó cũng chính là **∫-inf:t f_T(a)da**  (again, a là dummy variable, ta chỉ
> cần hiểu **f_T là PDF của T**)Do đó theo FTC Part 1, derivative của F (đương nhiên đối với t) chính là f(t) (PDF của T evaluate
> tại t)
>
>
>
> Vậy **lấy đạo hàm** theo t của F_T:
>
>
>
> d/dt F_T(t) = f_T(t) 
>
>
>
> <=> f_T(t) = d/dt [1 - e^(-λt)] = d/dt [ - e^(-λt)] = - d/dt [e^(-λt)]
>
>
>
> = - d/d(-λt) [e^(-λt)] * d/dt (-λt) = - e^(-λt) * -λ = λ*e^(-λt)
>
>
>
> Và **f_T(t) =** **λ*e^(-λt) có dạng của PDF của Expo(λ)
>
>
>
> Vậy nên ta kết luận T là Exponential r.v**
>
> Nếu 
>
>
>
> [Nt = Số email nhận được trong khoảng thời gian t] là một Pois(λt) 
>
>
>
> ta có thể chứng minh 
>
>
>
> [T1 = Thời gian chờ cho đến khi nhận email thứ 1] là một Expo(λ)
>
> (**) Ở đây nói thêm, trong bài giảng gs ko nói, nhưng trong sách, cái này được
> gọi là **COUNT-TIME DUALITY**, là sự **KẾT NỐI** GIỮA MỘT **CONTINUOUS** R.V
> VÀ **DISCRETE** R.V.
>
>
>
> Khái quát hơn, Tn>t = Nt < n với ý nghĩa: 
>
>
>
> **[Thời gian chờ email thứ n] > t** 
>
>
>
> thì cũng chính là:
>
>
>
> **[Số email nhận được từ đầu đến t] nhỏ hơn n**

<br>

<a id="node-chn9vfm"></a>

<p align="center"><kbd><img src="assets/n54mvktpmb.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đại khái là, sau khi **nhận email đầu tiên**, thì khoảng thời gian **từ đó
> đến email thứ 2** dễ thấy **cũng lại là Expo(λ)**, vì giống như reset lại, ta
> vẫn có cùng bài toán. (Đây là tính chất **Memorylessness**)
>
>
>
> Do vậy, các [**khoảng thời gian giữa những lần nhận email**] (gọi là **inter-arrival**
> times) là các **i.i.d Expo(λ) random variables**. (i.i.d là vì nó **độc lập nhau**
> và **identical**: cùng là **Expo(λ)**. Gọi chúng là **Xj**.
>
> [X1 = T1 Thời gian chờ cho đến khi nhận email thứ 2] là một Expo(λ)
>
>
>
> [X2 = T2-T1: Thời gian chờ sau khi nhận email thứ 1 cho đến khi nhận email thứ 2]
> là một Expo(λ)
>
>
>
> [X3 = T3-T2: Thời gian chờ sau khi nhận email thứ 2 cho đến khi nhận email thứ 3]
> là một Expo(λ)
>
>
>
> ..
>
>
>
> X1, X2, X3...là i.i.d Expo(λ)

<br>

<a id="node-h0opgo1"></a>

<p align="center"><kbd><img src="assets/c1w6ejfbsm.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, tiếp theo, nếu ta quan tâm **Tn**, tức [**khoảng thời gian từ đầu đến
> email thứ n]**. 
>
>
>
> Giống như T1 là khoảng thời gian từ đầu cho đến email đầu
> tiên, T2 là thời gian từ đầu đến email thứ 2....) thì dễ thấy T2 = X1 + X2
> T3 = X1 + X2 + X3,...
>
>
>
> **Tn = ∑ j=1:n Xj**
>
>
>
> Xj là các khoảng thời gian giữa các lần nhận email, X1 trùng với T1, 
> như đã nói **Xj i.i.d ~ Expo(λ)**

<br>

<a id="node-kjg1zee"></a>

<p align="center"><kbd><img src="assets/5p9s33r763r.png" width="80%"></kbd></p>

> [!NOTE]
> Thì khi đó **Tn ~ Gamma(n, λ)**
>
>
>
> Và đây là **story quan trọng nhất của Gamma distribution.**
>
>
>
> Tất nhiên ta sẽ **chứng minh** điều này ở phần tiếp
>
>
>
> Gs cho biết ta đã biết **Geometric** là **số lần fail trước khi success lần đầu**.
> Và với **Negative** **Binomial** là **số lần fail cho đến khi success k lần**. 
>
>
>
> Thì có thể coi Negative Binomial là **tổng của nhiều Geometric** (số lần fail trước
> khi success lần đầu, sau đó reset lại ...)
>
>
>
> Thế thì **Expo** là **phiên bản (continuous)** tương đương của **Geometric** (discrete)
> thì có thể coi **Gamma là tương đương với Negative Binomial**
>
> X1=T1: thời gian chờ đến khi có email 1
>
>
>
> X2=T2-T1: thời gian chờ sau khi email 1 đến khi có email 2
>
>
>
> ...
>
>
>
> X1, X2,...Xn là i.i.d Expo(λ) THÌ: 
>
>
>
> Tn - thời gian chờ đến khi có email thứ n
>
>
>
> = X1 + X2 + ...Xn 
>
>
>
> Tn CHÍNH LÀ ~ Gamma(n, λ)

**🔗 See also:** [linked note](./lec_25_order_statistic_conditional_expectation.md#node-8y9uhek)

<br>

<a id="node-ijjvh6u"></a>

<p align="center"><kbd><img src="assets/9n6c2oszx37.png" width="80%"></kbd></p>

> [!NOTE]
> Ta sẽ đi chứng minh rằng **tổng của n các i.i.d Expo(1)** r.v Xj là một
> **Gamma(n,1)**
>
>
>
> Gs cho rằng khi ta có thể **chứng minh với Expo(1)** thì sẽ **dễ dàng chứng
> minh  với Expo(λ)**
>
>
>
> Ta có thể dùng **CONVOLUTION**, tức là **tìm CDF, PDF của TỔNG các r.v**
> như bài trước đã biết để chứng minh T là Gamma.
>
>
>
> Tuy nhiên ta **còn có công cụ MGF**, vốn rất phù hợp để làm chuyện đó vì **ở
> đây** ta có các **Xj independent**. Cũng như những bài trước ta đã chứng minh
> MGF của Expo
>
>
>
> Thêm nữa ta **chỉ cần làm với Expo(1) cho gọn** vì sau đó **rất dễ dàng mở
> rộng** nó với **Expo(λ)** vì như đã biết Expo(λ) rv chỉ là bằng Expo(1) / λ

<br>

<a id="node-v9cm6ey"></a>

<p align="center"><kbd><img src="assets/t3ul06jgiod.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì bài trước ta đã chứng minh **MGF** của Expo(1): M(t) = **1/(1-t)** (t<1)
>
>
>
> Vì các **Xj INDEPENDENT**. Nên **theorem** của MGF cho phép: 
>
>
>
> MGF của **TỔNG** của chúng sẽ bằng **TÍCH** các MGF cũa mỗi cái.
>
>
>
> Vậy nên MGF của Tn với Tn = X1+X2+...Xn sẽ là: 
>
>
>
> M_(X1+X2+..Xn)(t) = M_X1(t)*M_X2(t)*....M_Xn(t) = [**1/(1-t)]^n**  (t<1)

**🔗 See also:** [Moment Generating Function Derivation](./lec_18_mgf_continued.md#node-9510dh2) · [linked note](#node-fhsrfg7)

<br>

<a id="node-oiihl32"></a>

<p align="center"><kbd><img src="assets/s4er3vozz78.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì **để chứng minh Tn ~ Gamma(n,1)** ta phải **chứng minh Gamma(n,1)
> cũng có MGF có công thức này** như vừa rồi.
>
>
>
> **Áp dụng định nghĩa của MGF**, như đã biết, là E[e^tY]. 
>
>
>
> (Chỗ này ta lại nhắc lại để nhớ, **Y là r.v**, thì với một giá trị của t thì **e^tY, tức là
> apply hàm f(u) = e^tu vào r.v Y,** thì **kết quả cũng là random variable**, nên ta 
> **đương nhiên có thể nói về / tính expected value** của nó (e^tY).
>
>
>
> Thì expected value đó, với một giá trị của t, chính là giá trị của hàm MGF tại
> t, M(t))
>
>
>
> Thế thì, áp dụng **định nghĩa của expected value**, EX là **weighted** **sum** của 
> **mọi possible values** của X, với **weight** là **xác suất X mang possible value** đó.
>
>
>
> Thì với **continuous**, nó sẽ là: 
>
>
>
> EX = ∫-inf:inf x*f(x)dx, với f(x) là pdf. 
>
>
>
> Vậy thì để tính **E(g(X))**, **LOTUS** cho phép ta tính **E(g(X)) =** **∫-inf:inf g(x)f(x)dx**
> (có nghĩa là **không cần phải tìm PDF của g(X)** mà dùng luôn pdf của X)
>
>
>
> Vậy nên ta có **E(e^tY)** = **[1/G(n)] ∫0:inf e^ty * y^n * e^-y * (1/y) * dy**
>
>
>
> (limit tích phân từ **0:inf** thay vì **-inf:inf** là vì **pdf của Y ~ Gamma(n,1)** chỉ khác 0 
> từ 0:inf, và bằng 0 với -inf:0, và pdf của Y f(y) = [1/G(n)] y^n e^-y / y

<br>

<a id="node-i1pwau3"></a>

<p align="center"><kbd><img src="assets/0gsl4ye85zab.png" width="80%"></kbd></p>

> [!NOTE]
> Thu gọn lại ta có **[1/G(n)] ∫0:inf y^n e^[-(1-t)y] (1/y) dy**
>
>
>
> Đến đây gs cho rằng, ở class này thực ra **không quan trọng** rằng ta **giỏi**
> t**ính tích phân bằng** **Integration by Part**, hay **U-substitution** giỏi cỡ
> nào.
>
>
>
> Mà cái quan trọng là **Pattern Recognition**, nhận ra các pattern. Ví dụ ở đây,
> có thể thấy **bên trong tích phân lại có dạng của PDF của một  Gamma**
>
>
>
> Vì pdf của X~ Gamma(a,1) là **x^a e^-x / x**

<br>

<a id="node-fhsrfg7"></a>

<p align="center"><kbd><img src="assets/q1doicok5ki.png" width="80%"></kbd></p>

> [!NOTE]
> **Đặt x = (1-t)y** =>  y = -x/(1-t) 
>
>
>
> <=> **y^n** = (-1/(1-t))^n * x^n = **(1-t)^(-n) * x^n**
>
>
>
> Cũng từ x = (1-t)y , **lấy vi phân hai vế**: **dx = (1-t)dy** => **dy = dx / [(1-t)]**
>
>
>
> Vậy [1/(G(n))] tích phân 0:inf y^n e^[-(1-t)y] dy / y
>
>
>
> = [1/(G(n))] tích phân 0:inf **(1-t)^(-n)** * **x^n** * **e^-x** * [dx / (1-t)] / [x / (1-t)]
>
>
>
> i) Xét dx / [(1-t)] / [x/(1-t)] = **dx / x**
>
>
>
> nên tiếp tục ở trên 
>
>
>
> = **[1/(G(n))] tích phân 0:inf (1-t)^(-n) * x^n * e^-x * dx / x]**
>
>
>
> Đưa (1-t)^(-n) ra ngoài tích phân vì không phụ thuộc x
>
>
>
> = [(1-t)^(-n) / (G(n))] tích phân 0:inf  **x^n * e^-x * dx / x**]
>
>
>
> **limit** của tích phân **vẫn là 0:inf** vì x = (1-t)*y với t < 1 thì 1-t > 0, nên khi y từ 0->inf 
> thì x cũng từ 0->inf
>
>
>
> Và **[1 / (G(n))] tích phân 0:inf  * x^n * e^-x * dx / x]** 
>
>
>
> **CHÍNH LÀ** 
>
>
>
> **tích phân -inf:inf của pdf của gamma r.v**, thì theo yêu cầu về tính valid của pdf, 
> nó **phải bằng 1**
>
>
>
> Vậy ta còn lại **(1-t)^(-n)** hay **[1/ (1-t)]^n** 
>
>
>
> Và y như kết quả MGF của Tn
>
>
>
> **Và điều này đã chứng minh Tn là ~ Gamma(n,1)**
>
> CHỨNG MINH Tn CHÍNH
> LÀ ~ Gamma(n, λ)

**🔗 See also:** [linked note](#node-v9cm6ey)

<br>

<a id="node-dsy5w0h"></a>

<p align="center"><kbd><img src="assets/8dbvzlrv5ff.png" width="80%"></kbd></p>

> [!NOTE]
> gs nói thêm là trong phần chứng minh trên, ta **không có chỗ nào** **assume**
> là **n là integer**. Do đó nó **đúng cả với n real positive number**

<br>

<a id="node-5hq84js"></a>

<p align="center"><kbd><img src="assets/splofxy58pm.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, ta sẽ tìm **moment**. Gs nói ta tuy có thể dùng **MGF**, nhưng ở đây sẽ **dễ**
> **hơn** nếu dùng trực tiếp **LOTUS**
>
>
>
> Cụ thể là ta sẽ tìm **E[X^c]** với **c không nhất thiết là integer**. Nhưng với c = 1
> ta biết đó là 1st moment, chính là mean, c=2, ta có second moment, E[X^2]
> giúp tính variance...

<br>

<a id="node-97f2xof"></a>

<p align="center"><kbd><img src="assets/2g99aafwghv.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì dùng **LOTUS**. ta có E(X^c) = tích phân 0:inf **x^c** [**pdf của Gamma(a,1)**] dx
>
>
>
> = (**1/Gamma(a)**) tích phân 0:inf **x^c x^a e^-x dx/x**.
>
>
>
> **Gom** **x^c và x^a**, .. = (1/Gamma(a)) tích phân 0:inf **x^(c+a) e^-x dx / x**. (1)
>
>
>
> Tới đây ta có thể lập luận rằng **tích phân 0:inf x^(c+a) e^-x dx/x CHÍNH LÀ 
> hàm Gamma() EVALUATE TẠI a+c.**
>
>
>
> Vì ta biết **hàm Gamma** có công thức: **G(a) = tích phân 0:inf x^a e^-x dx / x**, nên
> Gamma(a+c) = tích phân 0:inf x^(a+c) e^-x dx / x
>
>
>
> Và từ đó (1) chính là = **Gamma(a+c) / Gamma(a)**
>
>
>
> Hoặc cũng có thể lập luận là (1/Gamma(a)) tích phân 0:inf x^(c+a) e^-x dx/x
>
>
>
> = [Gamma(a+c)/Gamma(a)] * **[1/Gamma(a+c)]  tích phân 0:inf x^(c+a) e^-x dx/x**
>
>
>
> để rồi **phần in đậm** chính là **tích phân từ 0:inf của [PDF của Gamma(a+c, 1) r.v]** 
> thì nó **sẽ phải là 1**. để rồi kết quả còn lại cũng là **Gamma(a+c) / Gamma(a)
>
>
>
> ====**
>
>
>
> Gs nói đó chính là **pattern recognition**, giúp ta **không cần tính tích phân chút
> nào**. Và cũng qua đó ta thấy **nice property của Gamma, và Beta**, mà ta sẽ quay
> lại cũng có đặc điểm này
>
> c'th moment của Gamma(a,1) 
>
>
>
> E[x^c] = Gamma(a+c) / Gamma(a)

**🔗 See also:** [linked note](#node-tg90580)

<br>

<a id="node-o5aro1n"></a>

<p align="center"><kbd><img src="assets/yjvr1h8aks.png" width="80%"></kbd></p>

> [!NOTE]
> Gs lưu ý, **luôn phải ghi điều kiện xác định là a+c dương** vì
> **Gamma(a,1) chỉ xác định với a dương**
>
>
>
> Từ đó cho phép ta tính **EX (tức c=1) = Gamma(a+1) / Gamma(a)**
>
>
>
> Mà ta đã biết một **Identity** rằng **Gamma(a+1) = a*Gamma(a)**
>
>
>
> Nên **EX = a**.
>
>
>
> GS nói đại khái là, dù a không cần phải là integer như đã nói, nhưng
> ta có thể dùng trường hợp a là integer để nhận xét kết quả trên là
> hợp lí. 
>
>
>
> Vì với a integer, X ~ Gamma(a,1) mang story là **tổng** của **a** **Xj ~ Expo(1)**
> r.v i.i.d. 
>
>
>
> Mà **E(Tổng các r.v)** theo **linearity** = **Tổng các Expect value**
>
>
>
> Và expected value của một Expo(1) đã chứng minh là bằng 1. 
> (EX của X ~ Expo(λ) = λ) 
>
>
>
> Nên với tổng a cái E(Xj) = a*1 = a
>
> X~Gamma(a,1): EX = a

<br>

<a id="node-dqoexfa"></a>

<p align="center"><kbd><img src="assets/5p0kxeybc5w.png" width="80%"></kbd></p>

> [!NOTE]
> Tính second moment E(X^2). Tương tự:
>
>
>
> E(X^2) = G(a+2)/G(a) = G(a+1+1)/G(a) = (a+1)G(a+1)/G(a)
>
>
>
> = a(a+1)G(a)/G(a) = a(a+1) = **a^2 + a**
>
>
>
> Từ đó Var(X) = E(X^2) - (EX)^2 = a^2 +a - a^2 = **a**
>
>
>
> Kết quả này ta **thấy giống Poisson** khi **mean** BẰNG **variance** nhưng
> gs cho biết nó **chỉ có khi Gamma(a,1)** tức λ = 1
>
> X~Gamma(a,1): VarX = a

<br>

<a id="node-hk2er7p"></a>

<p align="center"><kbd><img src="assets/ckd5x3fp2ql.png" width="80%"></kbd></p>

> [!NOTE]
> Và xong xuôi thì ta có thể tính **mean** và **variance** của **Gamma(a, λ)**
>
>
>
> Như đã chứng minh (link tím), Gamma(a, λ) r.v chỉ là = Gamma(a,1) / λ
>
>
>
> Nên với Y ~ Gamma(a, λ). **EY = E(X / λ)** = EX / λ = **a / λ** theo linearity
>
>
>
> Và VarY = Var(X / λ) = **VarX / λ^2** = **a / λ^2**
>
>
>
> (theo tính chất của variance Var(cX) = c^2 VarX mà ta đã học)
>
> X~Gamma(a, λ): EX = a / λ VarX = a / λ^2

**🔗 See also:** [linked note](#node-0gj5s98)

<br>

