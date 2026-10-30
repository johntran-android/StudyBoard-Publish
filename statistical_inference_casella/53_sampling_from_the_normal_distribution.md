# 5.3 Sampling From The Normal Distribution

📊 **Progress:** `21` Notes | `29` Screenshots | `16` AI Reviews

---
<a id="node-lmu32b0"></a>

<br>

<a id="node-fw0jsmz"></a>

## Lấy mẫu từ phân phối chuẩn

<p align="center"><kbd><img src="assets/71t5l8fymzt.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại ý là sẽ nói về việc ta xem xét sampling distribution của các 
> statistic của random sample có population là normal distribution. Đây dĩ
> nhiên là một trong các statistical model phổ biến nhất.
>
>
>
> Việc sampling từ normal distribution có nhiều tính chất hữu ích, cũng như là
> sampling distribution của các statistic từ normal sẽ có dạng quen thuộc là
> những mô hình xác suất nổi tiếng

<br>

<a id="node-aytwme7"></a>

### Tính chất Trung bình & Phương sai mẫu

<p align="center"><kbd><img src="assets/s7hlqf53e8.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, cái này đại khái là, họ nói ta đã biết cách tính mean, và variance của X̄ và S² nói chung. Bây giờ, với việc thêm vào gỉa định là ta biết population distribution thuộc loại normal distribution. Thì ta có thể derive (cho thấy) hoàn chỉnh **distribution của sample mean và sample variance**.
>
>
>
> Theorem 5.3.1: Đại khái nói là, ta có một random sample X1,X2...Xn từ một population và lần này ta biết nó là normal (μ, σ²). Vì với sample mean X̄, sample variance S² (mà công thức thì ta đã biết từ những phần trước rồi)
>
>
>
> Khi đó theorem này nói rằng:
>
>
>
> a) Hai cái random variable này, tức X̄ và S², **độc lập nhau.**
>
>
>
> b) Cái sampling distribution của sample mean X̄  là **normal (μ, σ²/n)**
>
>
>
> c) (n-1)S²/ σ² có sampling distribution là **chi-square với n-1 bậc tự do**
>
>
>
> Một vài suy nghĩ:
>
>
>
> i) Tại sao tác giả lại nói đền "additional assumption of normality" (tạm hiểu là có thêm giả định là normality): Mình nghĩ có thể hiểu rằng, thực tế, ta thường không biết cái population mà mình thực hiện lấy mẫu (sampling) có distribution là lọai gì. Nên ở đây, ta giả định nó là normal distribution.
>
>
>
> ii) Ôn lại chút về việc tại sao Sample mean X̄ và sample variance S² lại là random variable (Để rồi ở đây nói chúng độc lập): Thì đó là vì ta đã biết, định nghĩa của chúng, nói ngắn gọn, là, chúng là kết quả của việc ta dùng một function nào đó, để tính toán với các random variable X1,..Xn trong random sample. Cụ thể với X̄ thì nó là X̄ = g1(X1,..Xn) với g1 có công thức là g1(x1,..xn) = (x1 + x2 + ...xn)/n. Mà ta đã biết khi apply một function lên một (hoặc một đám) random variable thì ta cũng có một random variable mới.
>
>
>
> Thêm nữa, vì X1,...Xn là các random variable của một random sample. nên người ta gọi các random variable có được khi apply các function lên bộ random variable này là statistic.
>
>
>
> Và again, các statistic là random variable, nên nó cũng có distribution. Và người ta dùng cái tên SAMPLING DISTRIBUTION, để phân biệt với distribution của các random variable X1,...Xn vốn là distribution có sẵn (population distribution)
>
>
>
> Vậy thì thử xem ta có thể chứng minh theorem này ra sao.

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=8oEGxDhqdME)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất tốt và chính xác nội dung định lý 5.3.1 cùng các tính chất phân phối mẫu. Phần liên hệ và giải thích trực giác về statistic cũng như sampling distribution rất rõ ràng, chuẩn xác.
>
> **✓ Strengths**
> - Nắm trọn vẹn và chính xác ba kết luận then chốt của Định lý 5.3.1 về phân phối mẫu của X̄ và S² dưới giả định chuẩn.
> - Giải thích bản chất thống kê lượng (statistic) là hàm của các biến ngẫu nhiên trong mẫu và làm rõ khái niệm sampling distribution rất chuẩn xác.
>
> **💡 Deeper notes**
> - Cụm từ 'in general' ở phần đầu bài học có ý nghĩa quan trọng: các kết quả trước đó về kỳ vọng và phương sai (E[X̄]=μ, Var(X̄)=σ²/n, E[S²]=σ²) đúng với mọi phân phối có kỳ vọng và phương sai hữu hạn, không cần giả định chuẩn. Giả định chuẩn ('normality') chỉ cần thiết khi muốn suy ra trọn vẹn dạng phân phối (exact distributions) và tính độc lập giữa X̄ và S².

**🔗 See also:** [Chứng minh S² Chi-square](#node-nh8m52t) · [Suy diễn phân phối t](#node-iwzyu9l) · [Khoảng tin cậy từ đại lượng pivot](./92_methods_of_finding_interval_estimators.md#node-g9mg0da) · [Pooled Estimator and Student t Distribution](./111_2_introduction_one_way_anova.md#node-680r0w1)

<br>

<a id="node-dg373v9"></a>

#### MGF trung bình mẫu

<p align="center"><kbd><img src="assets/qplkhlwyg79.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên phần b đã được chứng minh rồi, thử làm lại nhanh.
>
>
>
> Đại khái là ta sẽ chứng mgf của X̄ có dạng là mgf của normal (μ, σ²/n)
>
>
>
> Thế thì, ôn lại về mgf (moment generating function), mgf của X, kí hiệu M_X(t) có bản chất công thức là E\[e^tX\], tức là, tạo một random variable mới Y = e^tX và lấy kì vọng (expected value) của nó.
>
>
>
> ---
>
>
>
> MX(t) = E\[e^tX\] = E\[g(X)\] với g(x) = e^tx
>
>
>
> MX(t)|t=1 = E\[e^X\]
>
>
>
> MX(t)|t=2 = E\[e²X\]
>
>
>
> MX(t)|t=100 = E\[e^100X\]
>
>
>
> ---
>
>
>
> ⇨ mgf của X̄, kí hiệu M_X̄ (t), có bản chất là E\[e^tX̄ \]
>
>
>
> Với X̄ = (Σi Xi)/n, ta có:
>
>
>
> E\[e^tX̄ \] = E\[e^(t(Σi Xi)/n)\] (e mũ \[t(Σi Xi)/n\])
>
>
>
> = E\[e^\[(t/n)(Σi Xi)\] \]
>
>
>
> = E\[e^\[(t/n)(X1 + X2 + ..Xn)\] \] | ghi rõ Σ ra
>
>
>
> = E\[e^\[(t/n)X1 + (t/n)X2 + ..(t/n)Xn\] \] | phân phối t/n vô
>
>
>
> Dùng tính chất hàm mũ e^(a+b) = e^a × e^b
>
>
>
> ..= E \[e^(t/n)X1 × e^(t/n)X2 × ....× e^(t/n)Xn \]
>
>
>
> Tới đây, đại khái ta có thể lập luận lại hoặc cho nhanh thì dùng một theorem đã chứng minh: nếu X1, X2...mutually independent thì E(X1X2.. Xn) = EX1 × EX2 ...× EXn
>
>
>
> ---
>
>
>
> (Chứng minh lại cũng dễ: Gọi f(x), f(y), f(x,y) là marginal pdf và joint pdf:
>
>
>
> E\[XY\] = E\[Z = g(X,Y)\] với g(x,y) = xy; theo 2D LOTUS, = ∫∫g(x,y)f(x,y)dxdy = ∫∫xyf(x,y)dxdy = ∫∫xyf(x)f(y)dxdy = ∫yf(y)(∫xf(x)dx)dy = ∫yf(y)(EX)dy = E\[X\] ∫yf(y)dy = E\[X\]E\[Y\])
>
>
>
> Ôn nhanh LOTUS:
>
>
>
> X \~ fX(x), Y = g(X).
>
>
>
> Theo định nghĩa, EX = weighted average các possible value với weight là xác suất tương ứng
>
>
>
> Nên với biến rời rạc X có possible values x1,x2,x3: EX = P(X=x1) x1 + P(X=x2)x2 + P(X=x3)x3, với biến liên tục: EX = ∫xf(x)dx
>
>
>
> Nhưng LOTUS cho phép tính EY mà không cần tìm pdf/pmf của Y: EY = ∫g(x)f(x)dx
>
>
>
> ---
>
>
>
> và ở đây, vì X1, X2....Xn là các random variables của một random sample, theo định nghĩa chúng sẽ mutually independent.
>
>
>
> Mà khi X1,X2...Xn independent thì g(X1), g(X2)...g(Xn) tức là các random variable có được bằng cách apply hàm g lên các random variable này, cũng sẽ mutually independent.
>
>
>
> Do đó E \[e^(t/n)X1 × e^(t/n)X2 × ....× e^(t/n)Xn\]
>
>
>
> = E\[e^(t/n)X1\] × E\[e^(t/n)X2\] × ....× E\[e^(t/n)Xn\]
>
>
>
> Rồi, tới đây xem xét E\[e^(t/n)X1\] là cái gì?
>
>
>
> Như lúc nãy đã nhắc lại định nghĩa mgf MX(t) = E\[e^tX\]. Vậy thì MX(t/n) = E\[e^(t/n)X\]
>
>
>
> (có nghĩa là, bản chất của hàm mgf của X evaluate tại t, là ta apply hàm g(x) = e^tx lên random variable X, để có một random variable mới: Y = e^tX. Rồi đem lấy kì vọng: E\[Y\] thì đó chính là MX(t). Vậy thì, nếu ta muốn evaluate tại t/n. thì dĩ nhiên là ta apply hàm khác g(x) = e^\[(t/n)x\] lên random variable X, để có Y = g(X) = e^\[(t/n)X\], ròi lấy kì vọng.
>
>
>
> Như vậy, quay lại đây E\[e^(t/n)X1\], chính là MX1(t/n).
>
>
>
> tương tự E\[e^(t/n)X2\] = MX2(t/n)
>
>
>
> ⇨ cái tích trên = MX1(t/n) MX2(t/n)....MXn(t/n)
>
>
>
> Rồi, tới đây, ta lại dùng định nghĩa của random sample, ôn nhanh, đó là các random variable X1,...Xn sẽ là các giá trị quan sát được của một biến số nào đó. Và chúng độc lập lẫn nhau (mutually independent) như đã nói, nhưng ngoài ra, chúng cũng có CHUNG MỘT MARGINAL DISTRIBUTION. Do đó pdf, hay pmf, hay cdf, hay mgf của chúng là giống nhau.
>
>
>
> Vậy cái tích trên có thể thay bằng \[MX1(t/n)\]ⁿ, hay gọi MX(t) là mgf của population distribution, ta có M_X̄ (t) = \[MX(t/n)\]ⁿ
>
>
>
> Tới đây ta dùng cái đề bài cho là sample có population distribution là normal(μ, σ²), thì mgf của một normal(μ, σ²) có thể nhớ hoặc tra bảng = e^\[μt + (1/2) σ²t²\]
>
>
>
>  Thay vào, **nhớ là đang evaluate tại t/n**
>
>
>
> ⇨ M_X̄ (t) = \[MX(t/n)\]ⁿ
>
>
>
> = {e^\[μ(t/n) + (1/2) σ²(t/n)²\]}ⁿ
>
>
>
> Ở đây, nhìn một nùi vậy chứ chỉ là (e^u)ⁿ, ta dùng tính chất hàm mũ: (aⁿ)ᵐ = aᵐⁿ
>
>
>
> = e^\[n\[μ(t/n) + (1/2) σ²(t/n)²\]\]
>
>
>
> = e^\[nμ(t/n) + n(1/2) σ²(t/n)²\] | phân phối n vô thôi
>
>
>
> = e^\[μt + (1/2) σ²(t²/n)\] | cancel n bớt
>
>
>
> = e^\[μt + (1/2) (σ²/n)t²\] | đổi chỗ thôi
>
>
>
> Tới đây, nhớ lại ta vừa nói random variable \~ normal(μ, σ²) sẽ có
>
>
>
> mgf M(t) = e^\[μt + (1/2) σ²t²\]
>
>
>
> nên normal(μ, σ²/n) sẽ có mgf là M(t) = e^\[μt + (1/2) (σ²/n)t²\]
>
>
>
> Cả pdf, cdf,pmf,mgf đều có thể dùng để xác định phân phối
>
>
>
> Chính là kết quả trên ta đang có,
>
>
>
> Từ đó có thể kết luận **sampling distribution của** **sample mean X̄ là normal(μ, σ²/n)**
>
>
>
> (vì như đã biết, mgf, cũng như cdf, pdf pmf, đều có thể giúp xác định loại của một distribution)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú xuất sắc khi tự chứng minh lại đầy đủ và chính xác phân phối của trung bình mẫu X̄ thông qua hàm sinh mô-men (mgf). Lập luận chặt chẽ, các bước biến đổi đại số rõ ràng và bản chất xác suất được nắm rất vững.
>
> **✓ Strengths**
> - Tự triển khai hoàn chỉnh từng bước suy dẫn hàm mgf của X̄ từ định nghĩa mẫu ngẫu nhiên i.i.d mà không bỏ sót bước biến đổi nào.
> - Hiểu rõ bản chất hàm sinh mô-men, nguyên lý hàm của biến ngẫu nhiên độc lập và tính duy nhất của mgf để nhận diện phân phối chuẩn.
>
> **💡 Deeper notes**
> - Định lý xác định duy nhất phân phối qua mgf yêu cầu mgf phải tồn tại trong một khoảng mở chứa điểm 0; đối với phân phối chuẩn, mgf hội tụ trên toàn bộ R nên điều kiện này luôn được đảm bảo.
> - Về mặt thuật ngữ chặt chẽ trong thống kê toán, X1, ..., Xn là các biến ngẫu nhiên (chưa thực hiện phép đo), còn các giá trị thực nhận x1, ..., xn sau khi lấy mẫu mới là các giá trị quan sát (realized values).

<br>

<a id="node-z2xp2q0"></a>

##### X̄ và S² độc lập

<p align="center"><kbd><img src="assets/pkzk4o7u59g.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/58ub89t6w9.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0g1eesvavq9d.png" width="80%"></kbd></p>

> [!NOTE]
> Để chứng minh ý b): X̄ và S² độc lập, nhìn khá khoai. Nhưng chiến lược
> hay ý tưởng là dùng cái theorem (..) đã học ở những chương trước nói rằng:
> nếu như X, Y là hai random variable độc lập thì g(X), h(Y) cũng độc lập nhau.
> (tức là apply function g và h lên X và Y để có hai random variable mới, thì chúng
> cũng độc lập)
>
>
>
> Và cụ thể thì ta sẽ cho thấy rằng Y1 = X̄, sẽ độc lập với Y2,...Yn Và S² chỉ
> là function theo Y2,...Yn ⇨ cũng độc lập với Y1, tức X̄.
>
>
>
> Đầu tiên họ sẽ chứng minh cho thấy S² chỉ là function của Y1,...Yn 
>
>
>
> (Y1 = X1 - X̄)
>
>
>
> Dựa vào: 
>
>
>
> Σi (Xi - X̄) = 0 (cái này dễ thấy)
>
>
>
> (X1 - X̄) + Σi=2:n (Xi - X̄) = 0
>
>
>
> ⇔ (X1 - X̄) = - Σi=2:n (Xi - X̄)
>
>
>
> ⇨ (X1 - X̄)² = [Σi=2:n (Xi - X̄)]²
>
>
>
> S² = [1/(n-1)] Σi (Xi - X̄)²
>
>
>
> = [1/(n-1)] [(X1 - X̄)² + Σi=2:n (Xi - X̄)²]
>
>
>
> = [1/(n-1)] [[Σi=2:n (Xi - X̄)]² + Σi=2:n (Xi - X̄)²]
>
>
>
> ⇨ S² chỉ là hàm phụ thuộc X2-X̄,....Xn-X̄
>
>
>
> Và sau đó ta sẽ chứng minh các rv này independent với X̄ thì như vậy
> S² là hàm của các biến mà chúng độc lập với X̄, thì như Y = g(Z) mà Z
> độc lập với X thì Y độc lập với X
>
>
>
> Và người ta chứng minh điều này bằng cách xuất phát từ joint pdf của X1,...Xn
>
>
>
> Sau đó đặt Y1 = X̄, Y2 = X2 - X̄,....Yn = Xn - X̄
>
>
>
> ta sẽ xây dựng joint pdf của Y1, ...Yn và cho thấy nó có dạng là tích của 
> một hàm theo y1, và một hàm theo y2,....yn. Từ đó kết luận Y1 độc lập với Y2,..Yn
>
>
>
> Từ đó chứng minh xong.
>
>
>
> Sau đây sẽ là mình làm chi tiết bước này:
>
>
>
> joint pdf của X1,...Xn:
>
> Sau đây sẽ là mình làm chi tiết bước này:
>
>
>
> joint pdf của X1,...Xn:
>
>
>
> Vì X1,...Xn độc lập nên joint pdf = tích marginal pdf (là pdf của normal(0, 1)
>
>
>
> fX1(x) = [1/√(2π)] e^-x² / 2
>
>
>
> ⇨ f(x1,...xn) = Πi=1:n [1/√(2π)] e^-xi² / 2
>
>
>
> = [1/√(2π)]^n Πi=1:n e^-xi² / 2
>
>
>
> = [1/√(2π)]^n e^[Σi=1:n -xi² / 2]
>
>
>
> = [1/√(2π)]^n e^[(1/2)Σi=1:n -xi²]
>
>
>
> Đổi biến:
>
>
>
> Y1 = X̄, Y2 = X2 - X̄
>
>
>
> y1 = x̄
>
>
>
> y2 = x2 - x̄
>
>
>
> y3 = x3 - x̄
>
>
>
> ..
>
>
>
> (x1 - x̄) = - Σi=2:n (xi - x̄)
>
>
>
> ⇨ x1 = x̄ - Σi=2:n (xi - x̄) = y1 - Σi=2:n yi
>
>
>
> ⇨ ∂x1/∂y1 = 1, ∂x1/∂y2 = ∂x1/∂yn = -1
>
>
>
> x2 = y2 + x̄ = y2 + y1
>
>
>
> ⇨ ∂x2/∂y1 = ∂x2/∂y2 = 1, ∂x2/∂y3 = ...∂x2/∂yn = 0
>
>
>
> x3 = y3 + y1
>
>
>
> ⇨ ∂x3/∂y1 = ∂x3/y3 = 1, ∂x3/∂y2 và các cái khác = 0
>
>
>
> ...
>
>
>
> ⇨ ta có Jacobinan có dạng:
>
>
>
> [1 -1 -1...-1]
> [1 1 0...0]
> [1 0 1...0]
> ...
> [1 0 0...1]
>
>
>
> Tới đây chưa vội tính det cái này, mà dùng một tính chất đã học ở mit1806
> thay 1 hàng bằng cách trừ nó cho 1 hàng khác (nhân scalar) thì det ko
> đổi. Nên lần lượt ta biến đổi matrix qua một chuỗi các matrix mà mỗi bước
> ta lần lượt lấy hàng 1 = hàng 1 + hàng 2, rồi hàng 1 = hàng 1 + hàng 3,...
> để cuối cùng ta có:
>
>
>
> [n 0 0...0]
> [1 1 0...0]
> [1 0 1...0]
> ...
> [1 0 0...1]
>
>
>
> Tới đây dùng cofactor formula: 
>
>
>
> Tính theo hàng 1, thì nó bằng a11. (+) det matrix M11 (M11 là matrix bỏ
> hàng 1 cột 1), chính là I, có det = 1 (tính chất đầu tiên của det) 
>
>
>
> ⇨ det J = a11*1 = a11 = n
>
>
>
> Transformation theorem:
>
>
>
> f𝐘(y1, y2,..yn) = f𝐗(x1,x2...xn) | J | = [1/√(2π)]^n e^[(1/2)Σi=1:n -xi²] n
>
>
>
> Tiếp thế x1 = y1 - Σi=2:n yi
>
>
>
> x2 = y2 + y1, x3 = y3 + y1, ... xn = yn + y1
>
>
>
> ... = [1/√(2π)]^n e^[(1/2)Σi=1:n -xi²] n
>
>
>
> = (n/[√(2π)]^n) e^[(1/2)Σi=1:n -xi²]
>
>
>
> = (n/[√(2π)]^n) e^(1/2)[-x1² + Σi=2:n -xi²]
>
>
>
> = (n/[√(2π)]^n) e^(-1/2)[x1² + Σi=2:n xi²]
>
>
>
> Thay x1 = y1 - Σi=2:n yi = y1 - S (đặt S = Σi=2:n yi)
>
>
>
> x2 = y2 + y1, ...
>
>
>
> = (n/[√(2π)]^n) e^(-1/2)[(y1 - S)² + Σi=2:n (yi + y1)²]
>
>
>
>
>
>
>
> a) (y1 - S)² = y1² - 2y1S + S²
>
>
>
> b) Σi=2:n (yi + y1)² = Σi=2:n (yi² + y1² + 2yiy1)
>
>
>
> = Σi=2:n yi² + Σi=2:n y1² + Σi=2:n 2yiy1
>
>
>
> = Σi=2:n yi² + (n-1) y1² + 2y1 Σi=2:n yi
>
>
>
> = Σi=2:n yi² + (n-1) y1² + 2y1S
>
>
>
> ⇨ (y1 - S)² + Σi=2:n (yi + y1)²
>
>
>
> = y1² - 2y1S + S² + Σi=2:n yi² + (n-1) y1² + 2y1S
>
>
>
> = y1² + (n-1) y1² + S² + Σi=2:n yi² 
>
>
>
> = n y1² + S² + Σi=2:n yi² 
>
>
>
> = n y1² + (Σi=2:n yi)² + Σi=2:n yi² 
>
>
>
> ⇨ (n/[√(2π)]^n) e^(-1/2)[(y1 - S)² + Σi=2:n (yi + y1)²]
>
>
>
> = (n/[√(2π)]^n) e^(-1/2)[n y1² + (Σi=2:n yi)² + Σi=2:n yi² ]
>
>
>
> = (n/[√(2π)]^n)    e^(-1/2)[n y1²]    e^[(Σi=2:n yi)² + Σi=2:n yi² ]
>
>
>
> là tích của  e^(-1/2)[n y1²]  chỉ chứa y1
>
>
>
> và e^[(Σi=2:n yi)² + Σi=2:n yi² ] chỉ chứa y2,...yn
>
>
>
> mà nhớ là đây là joint pdf của Y1,...Yn ⇨ Y1 độc lập với Y2,...Yn
>
>
>
> ⇨ Y1 cũng độc lập với S² (là function của Y2,...Yn)
>
>
>
> ⇨ X̄ (=Y1)  cũng độc lập với S² (là function của Y2,...Yn)

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **92/100** · ✓ Move on
>
> Ghi chú rất xuất sắc khi tự mình tính toán chi tiết định thức Jacobian (vận dụng kiến thức MIT 18.06) và khai triển đại số ở số mũ mà sách giáo khoa bỏ qua. Có một vài sơ suất nhỏ về ký hiệu và thiếu hệ số -1/2 khi chép lại số mũ ở bước cuối nhưng không ảnh hưởng tới bản chất suy luận độc lập.
>
> **🟡 Minor issues**
>
> **1.** *"= (n/[√(2π)]^n)    e^(-1/2)[n y1^2]    e^[(Σi=2:n yi)^2 + Σi=2:n yi^2 ]"*
>
> Khi tách tích hai hàm mũ, bạn bị sót hệ số -1/2 ở số mũ của thừa số thứ hai. Đúng ra phải là e^(-1/2)[(Σ yi)^2 + Σ yi^2]. Dù vậy, hàm này vẫn chỉ phụ thuộc vào (y2,...,yn) nên tính chất phân rã độc lập vẫn giữ nguyên.
>
> **2.** *"Để chứng minh ý b): X̄ và S^2 độc lập"*
>
> Trong giáo trình, việc chứng minh X̄ và S^2 độc lập là ý (a) (To prove part (a)...), còn ý (b) đã được chứng minh từ ví dụ trước.
>
> **3.** *"Đầu tiên họ sẽ chứng minh cho thấy S^2 chỉ là function của Y1,...Yn 

(Y1 = X1 - X̄)"*
>
> Đoạn nháp này hơi nhầm lẫn ký hiệu ban đầu khi gán Y1 = X1 - X̄, tuy nhiên ngay sau đó bạn đã chỉnh lại chuẩn xác biến đổi theo (X2 - X̄, ..., Xn - X̄) và đặt Y1 = X̄.
>
>
> **✓ Strengths**
> - Tự lực giải quyết trọn vẹn bước tính định thức Jacobian của phép đổi biến ngược bằng cách biến đổi hàng và khai triển Laplace theo hàng 1, giải thích rõ ràng tại sao lại xuất hiện hệ số n.
> - Nắm rất vững chiến lược cốt lõi: phân rã joint pdf của (Y1, ..., Yn) thành tích g(y1)h(y2,...,yn) để suy ra Y1 độc lập với nhóm (Y2,...,Yn), từ đó kéo theo tính độc lập với S^2.
> - Khai triển đại số chi tiết và chính xác cho tổng bình phương ở số mũ.
>
> **💡 Deeper notes**
> - Sách ghi 'Jacobian equal to 1/n' vì họ đang xét Jacobian của phép biến đổi thuận (từ x sang y), còn khi thay vào công thức đổi biến joint pdf ta cần Jacobian của phép biến đổi ngược (từ y sang x) nên định thức bằng n (hoặc lấy nghịch đảo 1/(1/n) = n). Ghi chú của bạn tính trực tiếp ma trận ngược này là hoàn toàn chuẩn xác.
> - Chứng minh này ngầm dựa trên giả thiết mẫu ngẫu nhiên từ phân phối chuẩn N(0, 1) (không mất tính tổng quát nhờ tính chất họ vị trí - tỉ lệ scale-location family).

<br>

<a id="node-udtt0nq"></a>

###### Bổ đề Chi-square

<p align="center"><kbd><img src="assets/11d0h51r0h5c.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6f6c09mgmsv.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là ta sẽ lạc đề tí, bàn qua Chi-square một chút trước khi quay lại vì distribution này có tầm quan trọng trong việc triển khai ra pdf của sample variance S².
>
>
>
> Phần trước mình đã biết qua Chi-square là một trường hợp đặc biệt của Gamma, có pdf là:
>
>
>
> f(x) = \[1/Γ(p/2)2^(p/2)\] x^\[(p/2)-1\] e^(-x/2), 0 &lt; x &lt; ∞, p là bậc tự do
>
>
>
> Thì bổ đề này cho biết đại ý là:
>
>
>
> a) Nếu Z là normal (0, 1) thì Z² sẽ là Chi-square 1 bậc tự do, kí hiệu χ²\_1
>
>
>
> b) nếu ta có X1, X2,....Xn là các Chi-square rv độc lập với các bậc tự do tương ứng Xi \~ χ²\_pi, thì tổng của chúng cũng là Chi-square và bậc tự do thì cộng lại
>
>
>
> ---
>
>
>
> Chứng minh: 
>
>
>
> Phần a thì dựa trên ví dụ trong chương 2, nơi mình đã tìm pdf của Y = g(X) = X². Từ đó áp dụng sự thật là X là normal(0,1) thì bỏ pdf của nó vô ta sẽ có pdf của Y là pdf của χ²\_1
>
>
>
> Dùng kết quả của Example 2.1.7, ta có fY(y) = (1/2√y) fX(√y) + (1/2√y) fX(-√y)
>
>
>
> Nếu X \~ n(0,1), fX(x) = (1/√2π) exp(-x²/2) ⇒ fX(√y) = (1/√2π) exp(-y/2) và fX(-√y) cũng vậy
>
>
>
> → fY(y) = (1/2√y) (1/√2π) exp(-y/2) + (1/2√y) (1/√2π) exp(-y/2)
>
>
>
> = (1/√y) (1/√2π) exp(-y/2)
>
>
>
> = (1/√2π) (1/√y) exp(-y/2) 
>
>
>
> theo công thức f(x) = \[1/Γ(p/2)2^(p/2)\] x^\[(p/2)-1\] e^(-x/2), 0 &lt; x &lt; ∞, p là bậc tự do
>
>
>
> thì đây chính là Chi-square với p = 1, χ²\_1:
>
>
>
> Để thấy rõ, nhắc lại vài tính chất hàm Gamma: Γ(a) = ∫0:inf t^(a-1)e^(-t) dt, Γ(1) = 1, Γ(1/2) = √π
>
>
>
> \[1/Γ(1/2)2^(1/2)\] x^\[(1/2)-1\] e^(-x/2)
>
>
>
> = (1/√π√2) (1/√x) e^(-x/2)
>
>
>
> = (1/√2π) (1/√x) e^(-x/2)
>
>
>
> ---
>
>
>
> Bên cạnh đó, ta cũng PDF của Gamma(α, β) = 1/\[Γ(α)β^α\] x^(α-1) e^(-x/β)
>
>
>
> Nên χ²\_1 chính là Gamma(1/2,2)
>
>
>
> ---
>
>
>
> Còn phần b thì dựa trên ví dụ trong chương 4 đã làm để thấy tổng của các Γ cũng là Γ, với tham số cộng lại. Ở đây gs nói vì Chi-square là một loại Γ cụ thể là Γ(p/2, 2) nên dĩ nhiên nó cũng đúng.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, không chỉ tóm tắt chính xác nội dung bổ đề mà còn chủ động giải chi tiết lại phép biến đổi biến ngẫu nhiên và chứng minh tính tương đương giữa Gamma(1/2, 2) và Chi-bình phương 1 bậc tự do.
>
> **✓ Strengths**
> - Nắm vững và diễn giải trực quan, chính xác hai tính chất quan trọng của phân phối Chi-bình phương trong Bổ đề 5.3.2.
> - Tự triển khai đầy đủ và chính xác công thức đạo hàm hàm mật độ qua phép đổi biến Y = X² từ phân phối chuẩn tắc.
> - Chứng minh mạch lạc sự trùng khớp giữa Chi-square(1) và Gamma(1/2, 2) thông qua giá trị hàm Gamma tại 1/2 là √π.
>
> **💡 Deeper notes**
> - Ở phần (b), tính chất cộng của các biến ngẫu nhiên Gamma (tổng các biến Gamma độc lập là một biến Gamma với shape parameter cộng lại) chỉ đúng khi tất cả các biến đó có cùng scale parameter β. Trong trường hợp Chi-bình phương, điều này luôn thỏa mãn vì mọi χ²_p đều có chung β = 2.

**🔗 See also:** [PDF của Y=X²](./21_distribution.md#node-6yi0r3h) · [Tổng biến ngẫu nhiên Gamma](./46_multi_variate_distribution.md#node-08ciur5) · [Ước lượng Satterthwaite](./72_method_of_finding_estimators.md#node-fosb15b) · [Pooled Estimator and Student t Distribution](./111_2_introduction_one_way_anova.md#node-680r0w1) · [Hàm Gamma và Tính chất](./33_continuous_distribution.md#node-4frhl19) · [Phân phối Chi-squared từ Y=X²](./21_distribution.md#node-f14tr9i) · [Hàm Gamma và Phân phối Gamma](./33_continuous_distribution.md#node-xt1ypib)

<br>

<a id="node-nh8m52t"></a>

###### Chứng minh S² Chi-square

<p align="center"><kbd><img src="assets/ozwzrjiuv89.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/d32ijmy0cdd.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này gs chứng minh vế cuối của theorem: là nếu X1,...Xn là random sample từ normal(μ, σ²) thì
>
>
>
> c): (n-1)S²/σ² sẽ là Chi-square n-1 (χ²\_n-1)
>
>
>
> Ko làm mất tính khái quát ta có thể xét normal (0,1) (vì sao?)
>
>
>
> Có nghĩa là cần chứng minh (n-1)S² sẽ là χ²\_n-1
>
>
>
> Đầu tiên phải ta sẽ chấp nhận (nội dung bài tập 5.15) công thức sample variance của mẫu size n sẽ quan hệ với sample variance của mẫu size n-1 bởi:
>
>
>
> (n - 1)S²\_n = (n - 2)S²\_n-1 + (n-1)/n (Xn - X̄\_n-1)²
>
>
>
> X̄\_n-1 là sample mean của mẫu size n-1, (X1,...Xn-1)
>
>
>
> ---
>
>
>
> X1,...Xn \~ n(0,1)
>
>
>
> Chứng minh (n-1)S²/σ² sẽ là χ²\_n-1
>
>
>
> Chứng minh nó đúng với n=2, tức chứng minh (2-1)S²\_2/1 =  (2-1)S²\_2 (sample variance của bộ có 2 cái X1, X2) là một χ²\_1
>
>
>
> Thì S²\_2 = 1/(2-1) \[(X1 - X̄)² + (X2 - X̄)²\] triển khai ra sẽ = (1/2)(X2 - X1)²
>
>
>
> Và vì X2, X1 đều là normal(0,1) nên X2 - X1 cũng là normal rv, vì sao?
>
>
>
> Vì theorem trước đây đã có nói (theo link), tổng của hai rv independent normal sẽ cũng là một normal, với param mean = tổng mean và variance = tổng variance. Ở đây X1, X2 là independent normal(0,1), thì -X1 cũng là normal(0, 1) và (-X1) + X2 \~ normal(0,2)
>
>
>
> ---
>
>
>
> Vì sao -X1 cũng là normal(0, 1)? → Dùng location scale? nó nói nếu Z \~ standard pdf f(x), thì σZ + μ sẽ là family member có location μ và scale param σ. với normal thì location và scale cũng là mean và standard deviation nên σZ + μ sẽ có mean μ, variance σ², ở đây -X1 = (-1) × X1 + 0 ⇨ -X1 distribution cũng là thành viên với location = mean là 0, scale = |-1| = 1 ⇨ variance = (-1)² = 1
>
>
>
> ---
>
>
>
> (Chứng minh nhanh X \~ n(μ1, σ1²) và Y \~ n(μ2, σ2²), X,Y độc lập thì X+Y \~ n(μ1+μ2,σ1²+σ2²)) bằng mgf:
>
>
>
> MGF của X \~ normal(μ, σ²): M(t) = E\[exp(tX)\] = exp(μ1t + σ1²t²/2)
>
>
>
> M(t) = E\[exp(tX)\] = exp(μt + σ²t²/2)
>
>
>
> MGF của X+Y: M(X+Y)(t) = E\[exp(t(X+Y))\] = E\[exp(tX+tY))\]
>
>
>
> = E\[exp(tX)exp(tY)\] 
>
>
>
> = E\[exp(tX)\]E\[exp(tY)\] (do X,Y độc lập) 
>
>
>
> U,V: E\[UV\] = ∫∫uvf(u,v)dudv = ∫∫uvf(u)f(v)dudv = ∫vf(v)(∫uf(u)du)dv = ∫vf(v)(EU)dv = EU ∫vf(v)dv = EUEV
>
>
>
> = MX(t)MY(t) = exp(μ1t + σ1²t²/2) exp(μ2t + σ2²t²/2) = exp(μ1t + σ1²t²/2 + μ2t + σ2²t²/2) 
>
>
>
> = exp\[(μ1+μ2)t + (σ1²+σ2²)t²/2\] 
>
>
>
> = exp\[at + b²t²/2\] 
>
>
>
> đây chính là mgf của một n(μ1+μ2,σ1²+σ2²) nên kết luận X+Y là n(μ1+μ2,σ1²+σ2²))
>
>
>
> ---
>
>
>
> Vậy X2 - X1 là normal(0 + 0, 1 + 1) = normal(0, 2).
>
>
>
> Z \~ n(0,1) thì  X=Zσ + μ \~ n(μ, σ²) thì ngược lại X \~ n(μ, σ²) thì (X - μ)/σ \~ n(0,1)
>
>
>
> Tiếp, xét (X2 - X1)/√2 thì cũng lại dùng location scale theorem: Nói rằng nếu X \~ thành viên có location μ, scale σ thì Z = (X - μ)/ σ sẽ là thành viên chuẩn (location 0, scale 1). Nên ở đây (X2 - X1) là thành viên location 0, scale √2 ⇨ \[(X2 - X1) - 0\]/√2 chính là sẽ ra thành viên chuẩn (location 0, scale 1) mà xét trong bối cảnh normal thì sẽ là mean 0, std 1 ⇨ normal(0,1)
>
>
>
> Vậy (X2 - X1)/√2 là normal(0,1) ⇨ \[(X2 - X1)/√2\]² = (X2 - X1)²/2 là χ²\_1
>
>
>
> ⇔ (2-1) S²\_2 \~ χ²\_1
>
>
>
> Cũng là (n-1)S²\_n với n = 2 là χ²\_1
>
>
>
> ---
>
>
>
> Thế thì, theo quy nạp, ta sẽ giả sử điều đang cần chứng minh đúng ở mẫu size k thì nếu ta chứng minh nó cũng đúng ở mẫu size k+1 thì sẽ có thể theo nguyên lí quy nạp (induction) mà kết luận nó đúng với mọi size
>
>
>
> Vậy thì ta **giả sử nó đúng với mẫu size k**, tức là: (k-1)S²\_k \~ χ²\_(k-1)
>
>
>
> Theo công thức (n - 1)S²\_n = (n - 2)S²\_n-1 + (n - 1)/n (Xn - X̄\_n-1)²
>
>
>
> thay n = k+1:
>
>
>
> (k+1-1)S²\_k+1 = (k+1-2)S²\_k+1-1 + (k+1-1)/(k+1) (X_k+1 - X̄\_k+1-1)²
>
>
>
> ⇔ kS²\_k+1 = (k-1)S²\_k + (k/k+1) (X_k+1 - X̄\_k)²
>
>
>
> Với việc đã giả thiết (k-1)S²\_k/σ² là χ²\_(k-1) thì ta cần chứng minh kS²\_k+1/σ² là χ²\_k
>
>
>
> ---
>
>
>
> Xét term thứ 2: (k/k+1) (X_k+1 - X̄\_k)²
>
>
>
> Đại khái là: X_k+1 - X̄\_k = X_k+1 - Σi Xi / k.
>
>
>
> Xi \~ n(0,1) ⇒ Xi / k \~ n(0, 1/k²) (location scale family: Z là standard member thì Zσ \~ location 0, scale σ)
>
>
>
> Nên cái này là tổng của các normal (X_k+1, -X1/k, -X2/k,.. đều là normal, chỉ khác param)
>
>
>
> ⇨ X_k+1 - (X1 + X2 + ...Xk) / k \~ normal(0 + ..0, 1 + 1/k² +...+ 1/k²) = normal(0, 1 + k/k²)
>
>
>
> tức là variance của nó: = 1 + k/k² = 1 + 1/k = (k+1)/k
>
>
>
> ---
>
>
>
> Làm cho vui: Xác nhận kết quả variance này theo cách khác: Vì X_k+1, -X1/k, -X2/k,... mutually independent ⇒ covariance bằng 0:
>
>
>
> Var(X_k+1 - X̄\_k) = Var(X_k+1 - Σi Xi / k) = Var(X_k+1) + Σi Var(-Xi/k)
>
>
>
> = 1 + Σi (1/k²) Var(Xi) = 1 + Σi (1/k²) = 1 + k/k² = 1 + 1/k = (k+1)/k
>
>
>
> ---
>
>
>
> Tiếp, vậy X_k+1 - X̄\_k là n(0, (k+1)/k), nên lại theo location scale theorem:
>
>
>
> (Chú ý nói X_k+1 - X̄\_k là normal (0, (k+1)/k) thì tức là nó là member có location 0, scale √\[(k+1)/k\] = √(k+1)/√k\] nhé, vì normal family là một loại location scale family với scale param là std, location là mean)
>
>
>
> \[(X_k+1 - X̄\_k) - 0\] / \[√(k+1)/√k\] sẽ là standard member có location 0, scale 1, tức normal(0,1)
>
>
>
> ⇨ (X_k+1 - X̄\_k) √k / √(k+1) \~ normal (0,1)
>
>
>
> ⇒ (X_k+1 - X̄\_k)² k / (k+1) \~ χ²\_1
>
>
>
> ⇒ \[(k/k+1)\](X_k+1 - X̄\_k)² \~χ²\_1
>
>
>
> ---
>
>
>
> Vậy quay lại đây kS²\_k+1 = (k-1)S²\_k + (k/k+1) (X_k+1 - X̄\_k)²
>
>
>
> Ta đã có: theo giả thiết là (k-1)S²\_k \~ χ²\_(k-1)
>
>
>
> Nay đã chứng minh: (k/k+1) (X_k+1 - X̄\_k)² là χ²\_1
>
>
>
> nên kS²\_k+1 là tổng của χ²\_(k-1) và χ²\_1
>
>
>
> Vậy dùng cái theorem  nãy, nói là **tổng của các χ² độc lập sẽ là χ² với bậc tự do cộng lại**.
>
>
>
> ⇒ χ²\_(k-1) và χ²\_1 \~ χ²\_k
>
>
>
> ⇒ Chứng minh xong kS²\_k+1 là χ²\_k
>
>
>
> ---
>
>
>
> (Phải nói rõ là các Chi-square độc lập thì mới áp dụng theorem tổng Chi-square cũng là Chi-square nhé. Nên ở đây trong sách giáo sư Casella có chỉ ra S²\_k độc lập với X_k+1 - X̄\_k)
>
>
>
> Và vì sao chúng độc lập?
>
>
>
> Là vì vế a) của theorem 5.3.1 nói rằng với X1,..Xn là random sample từ normal(μ, σ²) thì X̄ và S² độc lập nhau.
>
>
>
> Nên với random sample size k từ normal(0, 1) thì sample mean X̄\_k và sample variance S²\_k cũng độc lập nhau.
>
>
>
> X̄\_k độc lập với S²\_k
>
>
>
> X_k+1 độc lập với S²\_k vì X_k+1 độc lập X1,....Xk nên độc lập với S²\_k (là hàm của X1,....Xk)
>
>
>
> X_k+1 độc lập X̄\_k
>
>
>
> Nên mọi hàm của X_k+1 và X̄\_k, ví dụ (X_k+1 - X̄\_k) đều độc lập với S²\_k
>
>
>
> ---
>
>
>
> Cuối cùng, kết quả (n-1)S²\_n \~ χ²\_n-1 là đối với Xi \~ n(0,1), đổi tên lại thành Zi, và S²\_n này là sample variance của đám Zi \~ n(0,1)
>
>
>
> Ta có:
>
>
>
> (n-1)S²\_n \~ χ²\_n-1 với S²\_n = Σi (Zi-Z̄)²/(n-1)
>
>
>
> Xi ban đầu \~ n(μ, σ²), nên Xi = σZi + μ ⇔ Zi = (Xi - μ)/σ
>
>
>
> Z̄ = (Σi Zi) / n = \[Σi (Xi - μ)/σ\]/n = \[(1/σ)(Σi Xi - Σiμ)\]/n = (1/σ)(Σi Xi - nμ)/n = (1/σ)((Σi Xi)/n - μ) = (1/σ)(X̄ - μ) = (X̄ - μ)/σ
>
>
>
> ... ⇔ (n-1)S²\_n = (n-1) Σi ((Xi - μ)/σ-Z̄ )²/(n-1) \~ χ²\_n-1
>
>
>
> ⇔ = (n-1) Σi \[(Xi - μ)/σ-(X̄ - μ)/σ\]²/(n-1) \~ χ²\_n-1
>
>
>
> ⇔ = (n-1) Σi \[(Xi - μ)-(X̄ - μ)\]²/σ²(n-1) \~ χ²\_n-1
>
>
>
> ⇔ = (n-1) Σi (Xi - μ - X̄ + μ)²/σ²(n-1) \~ χ²\_n-1
>
>
>
> ⇔ = (n-1) Σi (Xi - X̄ )²/σ²(n-1) \~ χ²\_n-1
>
>
>
> ⇔ = (n-1) Σi \[(Xi - X̄ )²/(n-1)\]/σ² \~ χ²\_n-1
>
>
>
> ⇔ = (n-1) Σi \[(Xi - X̄ )²/(n-1)\]/σ² \~ χ²\_n-1
>
>
>
> Σi \[(Xi - X̄ )²/(n-1)\] bây giờ là S², random sample của đám Xi \~ n(μ, σ²)
>
>
>
> Vậy ta có (n-1) S²/σ² \~ χ²\_n-1, chứng minh xong ý c).

📹 Video 1: [Chứng minh S² Chi-square — Statistical Inference - Casella](https://www.youtube.com/watch?v=V4s75gq78PI)

📹 Video 2: [Ôn nhanh location scale family.](https://www.youtube.com/watch?v=4QKRIw9ZxL8)

📹 Video 3: [Chứng minh X,Y ~ normal độc lập thì X+Y cũng là normal](https://www.youtube.com/watch?v=ZqHWCkV8iG0)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú cực kỳ chi tiết, giải thích tường tận từng bước từ trường hợp cơ sở, bước quy nạp đến tính độc lập và phép đổi biến tổng quát hóa. Tư duy toán học rất mạch lạc và chuẩn xác.
>
> **✓ Strengths**
> - Hiểu rất rõ và tự giải thích chi tiết bước chuẩn hóa biến ngẫu nhiên về N(0,1) cũng như quy đổi ngược lại về tổng quát N(μ, σ²).
> - Chứng minh chặt chẽ phân phối của hiệu X_{k+1} - X̄_k theo cả quy tắc tổ hợp tuyến tính và tính phương sai độc lập.
> - Bổ sung dẫn chứng MGF và họ vị trí - tỉ lệ (location-scale family) để làm rõ bản chất các bước biến đổi mà sách giáo khoa lược giản.
>
> **💡 Deeper notes**
> - Về tính độc lập giữa vector (X_{k+1}, X̄_k) và S_k²: Trong lý thuyết xác suất, A độc lập C và B độc lập C không mặc nhiên suy ra (A, B) độc lập C. Tuy nhiên ở đây tính chất này hoàn toàn đúng vì X_{k+1} độc lập với toàn bộ vector mẫu (X_1, ..., X_k), và bản thân X̄_k độc lập với S_k² (theo định lý 5.3.1a).

**🔗 See also:** [MGF của tổng phân phối chuẩn](./42_conditional_distributions_independent.md#node-tk1wnj7) · [Tính chất Trung bình & Phương sai mẫu](#node-aytwme7)

<br>

<a id="node-qx3kch2"></a>

###### Độc lập trung bình phương sai

<p align="center"><kbd><img src="assets/900tplcxb4.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là tác giả nói có thể chứng minh sample mean và sample variance độc lập bằng cách khác, thay vì như lúc nãy ta đã làm là chứng minh joint pdf của chúng tách ra. Thì đầu tiên sẽ biết qua bổ đề sau:
>
>
>
> Đại khái nó nói là: cho X1,...Xn là các rv \~ normal(μj, σj²) j = 1,...n độc lập
>
>
>
> thì với các constant aij, brj với j=1,...n, i = 1,...k, r = 1,...m. Ta định nghiã:
>
>
>
> Ui = Σj aij Xj
>
>
>
> và
>
>
>
> Vr = Σj brj Xj
>
>
>
> Có nghĩa là ta có các random variable mới Ui, tạo ra bởi linear combination các random variable X1,..Xn
>
>
>
> Khi đó:
>
>
>
> a)Ui và Vr độc lập khi và chỉ khi Cov(Ui, Vr) = 0 và hơn nữa Cov(Ui, Vr) = Σj aijbrj σj²
>
>
>
> b) random vector (U1,...Uk) và (V1,...Vm) độc lập khi và chỉ khi Ui độc lập với Vr với mọi cặp i, r

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **92/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác nội dung và ý nghĩa của Bổ đề 5.3.3 về tính độc lập của các tổ hợp tuyến tính từ mẫu chuẩn.
>
> **🟡 Minor issues**
>
> **1.** *"thì với các constant aij, brj với j=1,...n, i = 1,...k, r = 1,...m."*
>
> Ghi chú đã bỏ sót điều kiện ràng buộc về số chiều k + m ≤ n được nêu trong bổ đề gốc.
>
>
> **✓ Strengths**
> - Nắm bắt chính xác bản chất Ui và Vr là các tổ hợp tuyến tính (linear combinations) của các biến ngẫu nhiên chuẩn độc lập.
> - Tóm tắt đúng và đầy đủ hai kết quả trọng tâm: độc lập tương đương với hiệp phương sai bằng 0, và tính độc lập của hai vector tương đương với sự độc lập đôi một giữa từng thành phần.
>
> **💡 Deeper notes**
> - Bổ đề này vận dụng tính chất đặc thù của phân phối chuẩn nhiều chiều: đối với các biến ngẫu nhiên có phân phối chuẩn đồng thời, không tương quan (Cov = 0) tương đương với độc lập, điều vốn không tự động đúng ở các phân phối tổng quát.

**🔗 See also:** [Lemma 11.3.2 Covariance of Linear Combinations](./113_simple_linear_regression.md#node-26ktgyo)

<br>

<a id="node-91dxhtz"></a>

###### Điều kiện độc lập tổ hợp Normal

<p align="center"><kbd><img src="assets/c1025ux777n.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xfe12q43zkg.png" width="80%"></kbd></p>

> [!NOTE]
> đầu tiên giáo sư cho rằng có thể chứng minh bổ đề này với μi = 0, σi² = 1 ta sẽ quay lại ý này sau.
>
>
>
> Còn bây giờ ôn lại vài cái đã học:
>
>
>
> X, Y independent thì Cov(X, Y) = 0. Đại khái là vì (tức là lập luận để chứng minh) Cov(X,Y) = E\[(X - EX)(Y - EY)\] = triển khai ra ta sẽ có công thức thứ 2:
>
>
>
> = E\[XY - (EX)Y - XEY + EXEY\]
>
>
>
> = E(XY) - E\[(EX)Y\] - E\[XEY\] + E(EXEY)
>
>
>
> = E(XY) - EXEY - EYEX + EXEY | linearity
>
>
>
> = E(XY) - EXEY
>
>
>
> Mà với X, Y independent thì E(XY) = EXEY (chứng minh bằng cách dùng 2D lotus, sau đó phân tách joint pdf thành tích marginal pdf để đưa về tích hai tích phân ⇨ EX EY)
>
>
>
> Vậy ⇨ Cov(X,Y) = 0
>
>
>
> Tiếp, chứng minh ý a2: Cov(Ui, Vr) = Σj aij brj σj²
>
>
>
> Ui = Σj aij Xj, Vr = Σj brj Xj
>
>
>
> Cov(Ui, Vr) = E\[(Ui - EUi)(Vr - EVr)\]
>
>
>
> EUi = E\[Σj aij Xj\] = Σj aij EXj (do linearity) = Σj aij μj
>
>
>
> Ui - EUi = Σj aij Xj - Σj aij μj = Σj aij (Xj - μj)
>
>
>
> EVr = E\[Σj brj Xj\] = Σj brj EXj = Σj brj μj
>
>
>
> Vr - EVr = Σj brj Xj - Σj brj μj = Σj brj (Xj - μj)
>
>
>
> ⇨ Cov(Ui, Vr) = E\[Σj aij (Xj - μj) Σj brj (Xj - μj)\]
>
>
>
> = E\[\[ai1(X1 - μ1) + ai2(X2 - μ2) + ...\]\[br1(X1 - μ1) + br2(X2 - μ2) + ...\]\]
>
>
>
> = E\[ ai1br1(X1 - μ1)² + ai2br2(X2 - μ2)² + ... ai1br2(X1 - μ1)(X2 - μ2) + ... (các cross term)\]
>
>
>
> = E\[Σj=1:n aijbrj (Xj - μj)² + Σk=1:n, h=1:n, k≠h aik brh (Xk - μk)(Xh - μh) \]
>
>
>
> Dùng linearity
>
>
>
> = Σj=1:n aijbrj E(Xj - μj)² + Σk=1:n, h=1:n, k≠h aik brh E(Xk - μk)(Xh - μh)
>
>
>
> Các E(Xk - μk)(Xh - μh) = Cov(Xk, Xh) đều bằng 0 do Xk, Xh độc lập
>
>
>
> Còn E(Xj - μj)² = Var(Xj) = σj²
>
>
>
> ⇨ Cov(Ui, Vr) = Σj=1:n aijbrj σj² . Chứng minh xong
>
>
>
> ---
>
>
>
>
>
> Và cuối cùng, Hệ quả 4.6.10 (theo link xanh) ta có tổ hợp tuyến tính các normal rv cũng là normal
>
>
>
> Vậy thì nói thêm một chút:
>
>
>
> Ở đây, ta sẽ chứng minh lemma này với μi = 0, σi² = 1.
>
>
>
> Và cái ý a của Lemma đại khái là:
>
>
>
> Cho Xj \~ normal(μj, σj²) độc lập và ta có các Ui, Vr là các random variable tạo bởi tổ hợp tuyến tính của các rv Xj. Thì chúng sẽ độc lập khi và chỉ khi covariance của chúng bằng 0.
>
>
>
> Vậy thì cái ta cần chứng minh là cho thấy joint pdf của Ui, Vr phân tách thành tích các marginal pdf
>
>
>
> Và ta làm điều này với cái đã có là covariance của chúng = 0.
>
>
>
> Mà covariance của Ui, Vr như đã làm vừa rồi, = Σj=1:n aijbrj σj²
>
>
>
> Mà đã nói, ta sẽ đang chứng minh với σi = 1 ⇨ Σj=1:n aijbrj σj² = Σj=1:n aijbrj
>
>
>
> ⇨ điều kiện ta đang có để dùng là Σj=1:n aijbrj = 0
>
>
>
> Đây chính là cái ràng buộc (restriction) đối với các constant mà giáo sư nói tới trong phần tiếp theo

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất xuất sắc và chi tiết; bạn đã tự tay thực hiện đầy đủ các bước biến đổi mà giáo trình chỉ lướt qua hoặc để dưới dạng bài tập.
>
> **✓ Strengths**
> - Tự triển khai tường minh và chính xác phép chứng minh Cov(Ui, Vr) = Σ a_ij b_rj σ_j² bằng cách tách số hạng chéo (cross-terms) dựa trên tính độc lập của các biến X_j.
> - Chứng minh lại chuẩn xác tính chất độc lập suy ra hiệp phương sai bằng 0 qua 2D LOTUS và tích các kỳ vọng biên.
> - Hiểu rõ việc chuẩn hóa về μ_i = 0 và σ_i² = 1 dẫn đến điều kiện trực giao giữa các hệ số Σ a_ij b_rj = 0.
>
> **💡 Deeper notes**
> - Để suy ra 'Cov = 0 kéo theo độc lập' cho biến phân phối chuẩn, điều kiện cần là cặp (Ui, Vr) phải có phân phối chuẩn đồng thời (bivariate/joint normal), chứ không chỉ riêng rẽ từng biến có phân phối chuẩn biên (marginal normal). Ở đây điều này luôn thỏa mãn vì cả Ui và Vr đều là tổ hợp tuyến tính từ cùng một vector các biến độc lập X_j.

**🔗 See also:** [Định lý Độc lập Hiệp phương sai](./45_covariance_correlation.md#node-o2ergsg) · [Chứng minh tổng biến chuẩn](./46_multi_variate_distribution.md#node-uaywczk) · [linked note](./57_ex.md#node-vmjgiar)

<br>

<a id="node-l2y727n"></a>

###### Độc lập biến chuẩn

<p align="center"><kbd><img src="assets/vmi5qtu1ufk.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, giáo sư nói tiếp, ta sẽ chứng minh lemma với n = 2, vì phần chứng minh với khái quát n cũng tương tự.
>
>
>
> Chứng minh với n = 2 tức là chứng minh: ta có X1 \~ n(μ1 = 0, σ1² = 1) X2 \~ n(0, 1)
>
>
>
> (again, nhắc lại là giáo sư mở đầu đã nói ta có thể chứng minh với μj = 0, σj = 1),
>
>
>
> Và Ui = Σj=1:2 aijXj = ai1X1 + ai2X2, tất nhiên có nhiều Ui, i = 1,...k
>
>
>
> Vr = Σj=1:2 brjXj = br1X1 + br2X2, r = 1,2...m
>
>
>
> Và ta sẽ chứng minh nếu cov(Ui, Vr) = 0
>
>
>
> (điều này tương đương Σj=1:n aij brj σj² = Σj=1:n aij brj = 0)
>
>
>
> thì joint pdf của Ui, Vr sẽ factored, tức chúng độc lập
>
>
>
> ---
>
>
>
> Rồi: Đơn giản là dùng transformation theorem thôi:
>
>
>
> Nhưng sẵn ôn lại tí: Bài toán đặt ra là ta triển khai ra joint pdf của U, V từ joint pdf đã có của X, Y.
>
>
>
> Vấn đề là để dùng theorem này, ta cần có MAPPING 1-1 TỪ SUPPORT SET CỦA X, Y TỚI ẢNH CỦA NÓ: Là sao?
>
>
>
> 𝒜 là support set của X,Y, đơn giản là tập (con của R², vì (X,Y) là R² random variable vector) mà trong đó joint pdf của X,Y dương.
>
>
>
> Dĩ nhiên là thông qua hàm g1, g2, thì U = g1(X,Y), V = g2(X, Y) thì các giá trị khả dĩ (x,y) của X, Y sẽ được map với u,v trong R². Nhưng mà ta sẽ chỉ quan tâm tới (x,y) trong 𝒜, vì tại đó mới là nơi "có thể xảy ra" (ý là giá trị của X,Y)
>
>
>
> Ảnh của 𝒜 tức là ℬ = {(u,v) ∈ R²: u = g1(x, y), v = g2(x, y) for some (x,y) ∈ 𝒜}
>
>
>
> Và mapping 1-1 giữa 𝒜 và ℬ tức là:
>
>
>
> với một (u,v) trong ℬ thì chỉ tìm thấy duy nhất một (x,y) trong 𝒜 mà thôi.
>
>
>
> (Và điều này không ngăn cản việc có thể có điểm (x,y) khác trong R² nằm ngoài 𝒜 được map với (u,v) nhưng vì tại (x,y) khác này, joint pdf của X,Y = 0 nên ko ảnh hưởng gì, nên theorem chỉ cần mapping 1-1 giữa 𝒜 với ℬ là đủ)
>
>
>
> ---
>
>
>
> Khi thỏa yêu cầu đó, thì từ (u,v) trong ℬ, như đã nói ta có thể tìm thấy (x,y) trong 𝒜: x = h1(u, v), y = h2(u,v) mà nếu điều kiện mapping 1-1 ko thỏa thì ta ko biết x, y là gì hết.
>
>
>
> Khi đó ta có thể có joint pdf của U,V từ joint pdf của X, Y như sau:
>
>
>
> fU,V(u,v) = fX,Y(x,y) |∂(x, y)/∂(u, v)|
>
>
>
> = fX,Y(h1(u,v), h2(u,v)) |∂(h1(u,v), h2(u,v))/∂(u, v)|
>
>
>
> ---
>
>
>
> Áp dụng vào bài toán này, nhắc lại, ta cần chứng minh Ui và Vr độc lập với Ui = Σj=1:2 aijXj tức, = ai1X1 + ai2X2 và Vr = Σj=1:2 brj Xj = br1X1 + br2X2
>
>
>
> Cho i = 1, r = 1, tức là ta sẽ chứng minh U1, V1 độc lập,
>
>
>
> Cho gọn ta gọi là U, V với U = a1X1 + a2X2, V = b1X1 + b2X2 và "thành lập" random variable vector (U, V)
>
>
>
> (và sẽ chứng minh joint pdf của U, V factored, từ joint pdf của X1, X2)
>
>
>
> ---
>
>
>
> Vậy thì ở đây, U = g1(X1, X2) và V = g2(X1, X2) với g1(x1,x2) = a1x1 + a2x2, g2(x1,x2) = b1x1 + b2x2
>
>
>
> Check điều kiện mapping 1-1: Ta thấy có thể giải tìm x, y từ u = g1(x,y), v = g2(x,y):
>
>
>
> u = a1x1 + a2x2; v = b1x1 + b2x2
>
>
>
> ⇒ x1 = (b2u - a2v) / (a1b2 - b1a2),
>
>
>
> Và x2 = (a1v - b1u) / (a1b2 - b1a2) (đây chính là h1, h2)
>
>
>
> Nếu a1b2 - b1a2 khác 0, từ (u,v) có thể tìm (x1,x2) do đó đây là thỏa điều kiện mapping 1-1 ở trên
>
>
>
> ---
>
>
>
> Từ đó ta có Jacobian: ∂(x1,x2)/∂(u,v)
>
>
>
> Row 1: \[∂x1/∂u, ∂x1/∂v\] = \[ b2 / (a1b2 - b1a2), -a2 / (a1b2 - b1a2) \]
>
>
>
> Row 2: \[∂x2/∂u, ∂x2/∂v\] = \[ -b1 / (a1b2 - b1a2), a1 / (a1b2 - b1a2)\]
>
>
>
> ⇨ det(J) = \[b2 / (a1b2 - b1a2)\] \[a1 / (a1b2 - b1a2)\] - \[-a2 / (a1b2 - b1a2)\] \[-b1 / (a1b2 - b1a2)\]
>
>
>
> = (b2a1 - b1a2) / (a1b2 - b1a2)²
>
>
>
> = **1 / (a1b2 - b1a2)**
>
>
>
> ⇒ |det(J)| = 1 / |a1b2 - b1a2|
>
>
>
> ---
>
>
>
> Thế vào theorem:
>
>
>
> fU,V(u,v) = fX1,X2(x1,x2) |det J|
>
>
>
> Mà X1, X2 độc lập nên joint pdf factored:
>
>
>
> = fX1(x1) fX2(x2) |J|
>
>
>
> = fX1((b2u - a2v) / (a1b2 - b1a2)) fX2((a1v - b1u) / (a1b2 - b1a2)) |J|
>
>
>
> pdf cuả n(0,1) f(x1) = \[1/√2π\] exp{-x1²/2} và f(x2) = \[1/√2π\] exp{-x2²/2}
>
>
>
> = \[1/√2π\] exp{-\[(b2u - a2v) / (a1b2 - b1a2)\]²/2} \[1/√2π\] exp{-\[(a1v - b1u) / (a1b2 - b1a2)\]²/2} |J|
>
>
>
> = \[1/2π\] exp{-\[(b2u - a2v) / (a1b2 - b1a2)\]²/2} exp{-\[(a1v - b1u) / (a1b2 - b1a2)\]²/2} |J|
>
>
>
> = \[1/2π\] exp{ -(1/2) (\[(b2u - a2v) / (a1b2 - b1a2)\]² + \[(a1v - b1u) / (a1b2 - b1a2)\]²) } |J|
>
>
>
> = \[1/2π\] exp{ -1 / \[2(a1b2 - b1a2)²\] \[(b2u - a2v)² + (a1v - b1u)²\] } |J| (1)
>
>
>
> Xét \[(b2u - a2v)² + (a1v - b1u)²\]
>
>
>
> triển khai ra ta sẽ có (b1² + b2²)u² + (a1² + a2²)v² - 2(a1b1 + a2b2)uv
>
>
>
> Và TA DÙNG cái ràng buộc của các constant được suy ra từ covariance = 0: a1b1 + a2b2 = 0
>
>
>
> ⇨ chỉ còn (b1² + b2²)u² + (a1² + a2²)v²
>
>
>
> Như vậy (1) = \[1/2π\] exp{ -1 / \[2(a1b2 - b1a2)²\] \[(b1² + b2²)u² + (a1² + a2²)v²\] } |J|
>
>
>
> = \[1/2π\] exp{ -1 / \[2(a1b2 - b1a2)²\] \[(b1² + b2²)u² } × exp {-1 / \[2(a1b2 - b1a2)²\]\[a1² + a2²)v²\] } |J|
>
>
>
> Tới đây là đủ để thấy joint pdf của U, V phân tách ⇨ U, V độc lập ⇨ Chứng minh xong phần a)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, hiểu sâu sắc định lý biến đổi biến ngẫu nhiên và tự tay tính toán chi tiết định thức Jacobian cũng như các bước biến đổi đại số một cách chuẩn xác.
>
> **✓ Strengths**
> - Tự tính toán tường minh ma trận Jacobian và định thức Jacobian thay vì chỉ chép lại kết quả từ tài liệu.
> - Nắm rất vững điều kiện ánh xạ 1-1 trên tập giá trị (support) cần thiết cho định lý đổi biến nhiều chiều.
> - Khai triển đại số chính xác phần số mũ và chỉ rõ cách triệt tiêu số hạng chéo (cross-term) nhờ điều kiện covariance bằng 0.
>
> **💡 Deeper notes**
> - Về điều kiện mẫu số khác 0: Ta có đồng nhất thức Lagrange $(a_1 b_2 - a_2 b_1)^2 + (a_1 b_1 + a_2 b_2)^2 = (a_1^2 + a_2^2)(b_1^2 + b_2^2)$. Vì $a_1 b_1 + a_2 b_2 = 0$, nếu $a_1 b_2 - a_2 b_1 = 0$ thì $(a_1^2 + a_2^2)(b_1^2 + b_2^2) = 0$, nghĩa là một trong hai biến $U$ hoặc $V$ triệt tiêu thành hằng số 0 (trường hợp suy biến). Do đó với các tổ hợp tuyến tính không tầm thường, mẫu số luôn khác 0.

<br>

<a id="node-25t5b1y"></a>

###### Độc lập vector qua PDF chung

<p align="center"><kbd><img src="assets/0c7m7lf7hrye.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là phần b, giáo sư cho là cũng có thể làm tương tự, là ta sẽ tìm joint pdf của random variable vector (U1,..Uk) và (V1,.. Vm) chú ý (joint pdf của hai random variable vector nhé) tức gọi 𝐔 = (U1,...Uk), 𝐕 = (V1,...Vm). thì joint pdf của chúng: f𝐔,𝐕(**u**,**v**) (viết bold hết để thể hiện là vector).
>
>
>
> Sau đó ta có thể dùng theorem 4.6.11 nói rằng nếu joint pdf của các random vector **X1**, **X2**, ...**Xn** mà factored, tức là có thể tách hàm f**X1**,**X2**,...**Xn**(**x1,**...**xn**) thành tích các hàm g1(**x1**)g2(**x2**)...gn(**xn**)
>
>
>
> (có nghĩa là hàm f**X1,X2,...Xn**(**x1**,...**xn**) là function nhận vào bộ vector **x1,..xn**có thể tách thành tích các function gi mà mỗi cái apply riêng lên vector **xi** thì khi đó các rv Vector **X1,...Xn** là độc lập

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt và giải thích rất chính xác ý tưởng chứng minh trong bài đọc, đặc biệt là việc làm rõ bản chất hàm mật độ đồng thời phân tích thành nhân tử (factorization) để suy ra tính độc lập giữa các vector ngẫu nhiên.
>
> **✓ Strengths**
> - Hiểu đúng và phân biệt rõ ràng giữa biến ngẫu nhiên vô hướng và vector ngẫu nhiên khi xét joint pdf.
> - Giải thích chuẩn xác định lý phân tích nhân tử (factorization theorem) cho vector ngẫu nhiên nhiều chiều.
>
> **💡 Deeper notes**
> - Đoạn trích còn có ý kết luận quan trọng cho phân phối chuẩn: tính độc lập giữa hai vector U và V tương đương với việc mọi cặp thành phần Ui và Vr độc lập với nhau (hay hiệp phương sai bằng 0).
> - Định lý phân tích nhân tử thường kèm điều kiện miền xác định (support) phải là tích Descartes của các miền xác định thành phần (với phân phối chuẩn đa biến thì điều này luôn thỏa do support là toàn không gian thực).

**🔗 See also:** [Khái quát tính độc lập biến ngẫu nhiên](./46_multi_variate_distribution.md#node-hvcrd7p)

<br>

<a id="node-1d7jfyb"></a>

###### Hiệp phương sai Độc lập Biến Chuẩn

<p align="center"><kbd><img src="assets/l5y3sp0oz2i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/l2mhrdhi9j.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy đại ý là cái bổ đề vừa rồi: Nó cho phép: KHI TA BẮT ĐẦU VỚI CÁC **NORMAL RANDOM VARIABLES ĐỘC LẬP** (X1,....Xn) thì **COVARIANCE** VÀ TÍNH CHẤT **INDEPENDENT** của các linear function của đám rvs này (Ui,Vr) sẽ là tương đương.
>
>
>
> Từ đó cho phép ta check xem các linear function của đám rvs này tức Ui, **có độc lập hay không bằng cách xem Covariance của chúng có bằng 0 hay không** (đó là ứng dụng của part a)
>
>
>
> Còn part b, khi lemma nói nếu Ui độc lập Vr với mọi i và r thì suy ra **vector U độc lập vector R**. Điều này cho phép khi ta có các random vector normal 
>
>
>
> (hiểu ko: (U1,...Uk) mà mỗi cái là linear function của đám normal X1,..Xn thì U1,...Uk như đã nói trong phần chứng minh lemma, cũng là normal, nên (U1,..Uk) gọi là normal vector hay random variable vector mà mỗi cái đều là normal rv)
>
>
>
> ..thì ta có thể kết luận các vector này độc lập bằng cách **check xem các phần tử (Ui, và Vr có độc lập từng cặp (pair wise) với nhau không**.
>
>
>
> Và **DUY CHỈ CÓ KHI TA DÙNG NORMAL DISTRIBUTION THÌ MỚI CÓ TÍNH CHẤT NÀY**

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **92/100** · ✓ Move on
>
> Ghi chú nắm rất chắc và chính xác các ý cốt lõi từ tài liệu: sự tương đương giữa hiệp phương sai bằng 0 và tính độc lập cho tổ hợp tuyến tính của các biến chuẩn độc lập, cũng như việc kiểm tra tính độc lập theo từng cặp suy ra tính độc lập của các vector.
>
> **🟡 Minor issues**
>
> **1.** *"Và DUY CHỈ CÓ KHI TA START VỚI NORMAL THÌ MỚI CÓ TÍNH CHẤT NÀY"*
>
> Tài liệu chỉ nói 'a property that does not hold for general random variables' (tính chất này nói chung không đúng với các biến ngẫu nhiên tổng quát), không đồng nghĩa với việc khẳng định biến chuẩn là phân phối duy nhất thỏa mãn điều này.
>
> **2.** *"COVARIANCE VÀ TÍNH CHẤT INDEPENDENT của các linear function của đám rvs này (Ui,Vr) sẽ là một"*
>
> Cách diễn đạt hơi thiếu chặt chẽ về mặt toán học. Chuẩn xác là: hiệp phương sai bằng 0 tương đương với tính độc lập (Cov = 0 <=> độc lập), chứ bản thân 'hiệp phương sai' (một giá trị số) và 'tính độc lập' (một quan hệ xác suất) không phải là một.
>
>
> **✓ Strengths**
> - Hiểu đúng và nêu rõ được điều kiện nền tảng: các biến ban đầu phải là biến chuẩn độc lập.
> - Nắm chuẩn ý nghĩa thực hành: chuyển việc kiểm tra độc lập phức tạp thành phép tính hiệp phương sai bằng 0 đơn giản.
> - Hiểu chính xác bản chất phần (b): kiểm tra độc lập từng cặp (pairwise) đủ để suy ra độc lập toàn phần giữa hai vector ngẫu nhiên.
>
> **💡 Deeper notes**
> - Một vector có các thành phần đều mang phân phối chuẩn riêng lẻ (marginal normal) chưa chắc đã là một vector chuẩn nhiều chiều (multivariate normal). Tuy nhiên, vì ở đây các thành phần đều là tổ hợp tuyến tính của các biến chuẩn độc lập ban đầu, nên vector tạo thành thực sự là multivariate normal.

<br>

<a id="node-jkt5q0l"></a>

###### Chứng minh độc lập S² X̄

<p align="center"><kbd><img src="assets/hjy1nwe3o2.png" width="80%"></kbd></p>

> [!NOTE]
> QUAY LẠI SAU
>
>
>
> Nhưng đại ý là ta có thể dùng bổ đề vừa rồi để chứng minh S² độc lập với
> X̄ theo cách khác nếu như sampling là normal sampling (X1,..Xn là sample
> size n từ population ~ normal distrbution)
>
>
>
> Thì như lemma này nói với Ui Vr là tổ hợp tuyến tính (hay linear function)
> của X1,...Xn mà có population là normal thì chỉ cần chứng minh Covariance
> của Ui và và Vr = 0 là đủ kết luận chúng độc lap
>
>
>
> Vậy ở đây X̄ là Σi (1/n)Xi , là một tổ hợp.
>
>
>
> Xi  - X̄ cũng vậy, cũng là các tổ hợp tuyến tính của X1,...Xn
>
>
>
> Giáo sư mới chứng minh các Xi  - X̄ đều có covariance = 0 vói X̄:
>
>
>
> Cov(X1 - X̄, X̄) = 0,...Cov(Xn - X̄, X̄) = 0
>
>
>
> Từ đó theo bổ đề ta suy ra X1-X̄ độc lập X̄, X2-X̄ độc lập X̄, ...
>
>
>
> mà trước đây đại khái là có theorem nói rằng nếu X, Y độc lập thì apply các hàm
> vào thì ta vẫn có các rv độc lập.
>
>
>
> Nên ở đâu S² = là function của (X1 - X̄, X2 - X̄,...)
> nên nó cũng độc lập X̄

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **90/100** · ✓ Move on
>
> Ghi chú nắm rất chắc và tóm tắt rành mạch mạch tư duy logic của chứng minh: từ tổ hợp tuyến tính, hiệp phương sai bằng 0 suy ra tính độc lập, đến việc hàm số của các biến độc lập cũng độc lập.
>
> **🟡 Minor issues**
>
> **1.** *"Từ đó theo bổ đề ta suy ra X1-X̄ độc lập X̄, X2-X̄ độc lập X̄, ... mà trước đây đại khái là có theorem nói rằng nếu X, Y độc lập thì apply các hàm vào thì ta vẫn có các rv độc lập. Nên ở đâu S² = là function của (X1 - X̄, X2 - X̄,...) nên nó cũng độc lập X̄"*
>
> Về mặt toán học chặt chẽ, việc từng biến $X_i - \bar{X}$ độc lập riêng lẻ với $ar{X}$ (pairwise) chưa đủ để áp hàm nhiều biến $S^2 = g(X_1 - \bar{X}, \dots, X_n - \bar{X})$ độc lập với $ar{X}$. Ở đây ta cần vector độ lệch $(X_1 - \bar{X}, \dots, X_n - \bar{X})$ độc lập đồng thời (jointly) với $ar{X}$ — điều này được đảm bảo do chúng có phân phối chuẩn đồng thời và hiệp phương sai với $\bar{X}$ đều bằng 0.
>
>
> **✓ Strengths**
> - Nắm chuẩn điều kiện tiên quyết của Bổ đề 5.3.3 là các biến ngẫu nhiên mẫu phải tuân theo phân phối chuẩn để tính không tương quan tương đương với độc lập.
> - Hiểu rõ vai trò biểu diễn $\bar{X}$ và $X_j - \bar{X}$ dưới dạng các tổ hợp tuyến tính để áp dụng bổ đề.
> - Tóm tắt chính xác luận điểm kết bài: vì $S^2$ là hàm của các độ lệch và các độ lệch độc lập với $\bar{X}$, nên $S^2$ độc lập với $\bar{X}$.
>
> **💡 Deeper notes**
> - Trong tài liệu gốc có nhấn mạnh $S^2$ chỉ cần viết dưới dạng hàm của $n - 1$ độ lệch vì bậc tự do của mẫu chỉ là $n - 1$ do $\sum (X_i - \bar{X}) = 0$.
> - Phép tính hiệp phương sai bằng 0 cũng ngầm giả định các $X_i$ độc lập và có cùng phương sai $\sigma^2$ (i.i.d normal).

<br>

<a id="node-153vzn2"></a>

###### Phân phối và biến động trung bình mẫu

<p align="center"><kbd><img src="assets/h7e5i0wibo.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là vầy: giáo sư Casella nói phần trước, khi ta tìm cách derive distribution (của các statistic như sample mean, sample variance) với giả định là random sampling từ normal là bởi vì (đại khái là) trong thực hành phân tích thống kê thì bước đầu tiên chính là giả định tính normality.
>
>
>
> Cụ thể hơn, trong hầu hết các case thực tế, thì ta KHÔNG BIẾT σ² (tức population variance của population normal distribution.
>
>
>
> Thế thì để mà chuyển qua phân tích về TÍNH BIẾN ĐỘNG CỦA SAMPLE MEAN X̄, thì ta cần phải estimate variance σ².
>
>
>
> (variability của sample mean, tức là sao? Là vì sampling mean ta đã biết là một random variable, có distribution, mà ta gọi là sampling distribution, vậy thì sắp tới ta quan tâm VARIANCE CỦA NÓ, chú ý, nó hoàn toàn khác với SAMPLE VARIANCE nhé, cái này nhắc lại là variance của sample mean)
>
>
>
> Vậy thì giáo sư cho biết, nếu X1.....Xn là random sample từ n(μ, σ²), thì ta đã biết (X̄ - μ) / σ/√n sẽ \~ n(0,1). Tại sao?
>
>
>
> Đầu tiên, ôn lại random sample là cái gì: Theo định nghĩa random sample size n từ population f tức là ta sẽ tiến hành quan sát giá trị của một biến số nào đó n lần, mỗi lần giá trị sẽ được đại diện bởi một random variable X_i
>
>
>
> Và các random variables X1,...Xn sẽ mutually independent, cũng như là identically distributed, tức có chung marginal distribution là population distribs
>
>
>
> Vậy thì trong phần trước mình đã biết rằng, sample mean X̄, với random sample từ normal(μ, σ²) thì X̄ cũng là normal, nhưng là normal(μ, σ²/n)
>
>
>
> Thế thì mới nói tới location scale theorem ta đã biết, nói rằng: nếu Z là random variable có pdf f(z), tức là thành viên chuẩn của location scale family, thì random variable X = σZ + μ sẽ là thành viên của family với location μ, và scale σ
>
>
>
> Và ngược lại nếu X là thành viên có location μ, scale σ thì (X - μ) / σ sẽ là thành viên chuẩn tức có location 0, scale 1.
>
>
>
> Mà ta cũng biết với normal, thì location là mean và scale là standard deviation.
>
>
>
> nên mới nói X̄ là normal(μ, σ²/n) thì (X̄ - μ) / √(σ²/n) sẽ là một normal(0,1)
>
>
>
> ---
>
>
>
> Thế thì, đại khái là với việc biết (X̄ - μ) / √(σ²/n) sẽ là một normal(0,1) thì ta có thể đo X̄, và nếu biết σ² (population variance) thì khi đó ta có thể làm cơ sở để SUY LUẬN RA μ (population mean).
>
>
>
> TUY NHIÊN, như đã nói, hầu hết ta đều không biết σ²,
>
>
>
> THÀNH RA, NGHIÊN CỨU CỦA ÔNG STUDENT, sẽ là quan sát distribution của (X̄ - μ) / S/√n (dùng sample standard deviation thay cho σ). Nhằm làm cơ sở cho việc **suy luận ra μ mà ko cần biết variance σ**

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất tốt, thể hiện sự hiểu bài sâu sắc từ động lực thực tế (chưa biết σ²) đến bản chất toán học của việc chuẩn hóa biến ngẫu nhiên qua họ location-scale.
>
> **✓ Strengths**
> - Nắm rất vững động lực thực tế dẫn đến phân phối Student: trong thực tế không biết phương sai tổng thể σ² nên phải thay thế bằng độ lệch chuẩn mẫu S để suy diễn về μ.
> - Phân biệt chính xác giữa phương sai của mẫu (sample variance) và phương sai của trung bình mẫu (variance of sample mean).
> - Giải thích logic và chặt chẽ vì sao (X̄ - μ)/(σ/√n) ~ n(0,1) thông qua tính chất của phân phối chuẩn và định lý họ vị trí - tỉ lệ (location-scale family).
>
> **💡 Deeper notes**
> - Khi thay thế hằng số σ bằng độ lệch chuẩn mẫu S, mẫu số trở thành một biến ngẫu nhiên. Vì vậy, phân phối của tỉ số này không còn là phân phối chuẩn nữa mà phụ thuộc vào phân phối của S và tính độc lập giữa X̄ và S² (đặc trưng của mẫu từ phân phối chuẩn), dẫn đến phân phối t với (n - 1) bậc tự do.

**🔗 See also:** [Kiểm định LRT cho trung bình](./82_method_of_finding_tests.md#node-ouhenhy) · [Pooled Estimator and Student t Distribution](./111_2_introduction_one_way_anova.md#node-680r0w1)

<br>

<a id="node-iwzyu9l"></a>

###### Suy diễn phân phối t

<p align="center"><kbd><img src="assets/vcmhn3i47.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đại ý là distribution của cái này (X̄ - μ) / S/√n thật ra là ko khó để derive:
>
>
>
> Biến đổi chút xíu:
>
>
>
> (X̄ - μ) / (S/√n)
>
>
>
> = (X̄ - μ)/(σ/√n) / (S/√n)/(σ/√n) (chia tử và mẫu cho (σ/√n))
>
>
>
> = (X̄ - μ)/(σ/√n) / (S/√n)(√n/σ)
>
>
>
> = (X̄ - μ)/(σ/√n) / (S/σ)
>
>
>
> = (X̄ - μ)/(σ/√n) / √(S²/σ²)
>
>
>
> Tới đây, tử số là n(0,1) như đã nói.
>
>
>
> X̄  \~ n(μ, σ²/n), STD(X̄ ) = σ/√n, E(X̄ ) = μ.
>
>
>
> location scale. Z: location = 0, scale = 1
>
>
>
> aZ + b = X, X location = b, scale a
>
>
>
> X \~ n(μ, σ²) location = mean, scale = std
>
>
>
> (X - μ)/σ = Z  \~ location = 0, scale = 1 \~ n(0, 1)
>
>
>
>
>
>
>
>
>
>
>
> Còn mẫu, thì bài trước ta đã biết, Sn², tức là sample variance của một random sample size n từ normal thì sẽ có tính chất:
>
>
>
> (n-1) S²\_n / σ² là một Chi-square n-1, kí hiệu χ²\_n-1
>
>
>
> Vậy thì S²\_n / σ² dĩ nhiên là χ²\_n-1/(n-1)
>
>
>
> nên mẫu số là √\[χ²\_n-1/(n-1)\]: căn bậc hai của một Chi-square chia cho bậc tự do của nó.
>
>
>
> Và cái mẫu số này này độc lập với tử số, vì S² đã được chứng minh là độc lập với X̄ theo ý a) của Theorem 5.3.1
>
>
>
> Như vậy tử số là một n(0,1), mẫu số có dạng căn bậc hai của Chi-square chia cho bậc tự do, và hai thằng độc lập.
>
>
>
> Do đó, nếu gọi tử số là U như đã biết, là một n(0,1), và V = χ²\_p, thì mẫu số là √(V/p) thì việc tìm distribution của (X̄ - μ) / (S/√n) cũng chỉ là tìm distribution của U/√(V/p) với U, V độc lập.
>
>
>
> Do đó có thể giải bài toán để tìm distribution của U/√(V/p)
>
>
>
> V là Chi-square p, thì ta có thể tìm distribution của √(V/p), rồi U là n(0,1) thì nói chung ta có thể tìm được distribution của U/√(V/p)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất tốt, giải thích chi tiết và mạch lạc từng bước biến đổi đại số cũng như cơ sở lý thuyết (phân phối Chi-bình phương, tính độc lập giữa trung bình mẫu và phương sai mẫu) để đưa thống kê t về dạng chuẩn U/√(V/p).
>
> **✓ Strengths**
> - Khai triển chi tiết từng bước đại số từ biểu thức ban đầu đến tỉ số chuẩn tắc, làm rõ hơn sách giáo khoa.
> - Nắm vững và liên hệ chính xác tính độc lập giữa tử số và mẫu số dựa trên tính chất độc lập giữa trung bình mẫu và phương sai mẫu trong phân phối chuẩn.
> - Xác định đúng bản chất mẫu số là căn bậc hai của một biến Chi-bình phương chia cho bậc tự do tương ứng.
>
> **💡 Deeper notes**
> - Trong bài toán cụ thể này, bậc tự do p của biến ngẫu nhiên Chi-bình phương V ở mẫu số chính là p = n - 1.

**🔗 See also:** [Tính chất Trung bình & Phương sai mẫu](#node-aytwme7)

<br>

<a id="node-isdevob"></a>

###### Phân phối t của Student

<p align="center"><kbd><img src="assets/r22vor23fbe.png" width="80%"></kbd></p>

> [!NOTE]
> Ta có định nghĩa: Cho random sample X1,...Xn từ n(μ, σ²), thì:
>
>
>
> **Phân phối của** (X̄ - μ) / S/√n **được định nghĩa là student's t**, với **n - 1 degree of freedom.**
>
>
>
> Như vậy sau này nên nhớ, story của Student t distribution là: là phân phối của (X̄ - μ) / (S/√n) với X̄ và S là sample mean và sample std của random sample \~ n(μ, σ²)
>
>
>
> Và nếu nói T là random variable \~ Student's t với p bậc tự do, thì ta kí hiệu là T \~ t_p. Và nó có pdf như vầy:
>
>
>
> fT(t) = Γ((p+1)/2)/Γ(p/2) × 1/√(pπ) × 1/\[(1+t²/p)^((p+1)/2)\]
>
>
>
> **Với p = 1 thì nó chính là pdf của Cauchy distribution:**
>
>
>
> fT(t) = \[Γ(1)/Γ(1/2)\] \[1/√(π)\] \[1/(1+t²)\]
>
>
>
> = \[1/√π\] (1/√(π)) \[1/(1+t²)\]
>
>
>
> = (1/π) \[1/(1+t²)\]  → xem link để thấy ta đã biết pdf của Cauchy f(x|θ) = (1/π) (1/(1+(x-θ)²) (-∞ &lt; x &lt; ∞, -∞ &lt; θ &lt; ∞)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất chính xác, tóm tắt rõ ràng định nghĩa phân phối Student's t và tự kiểm tra biến đổi chi tiết khi p = 1 để ra phân phối Cauchy chuẩn.
>
> **✓ Strengths**
> - Nắm chuẩn bản chất và 'story' của phân phối Student's t xuất phát từ mẫu chuẩn có độ lệch chuẩn mẫu S.
> - Tự thực hiện đầy đủ các bước tính toán với các giá trị hàm Gamma để chứng minh t_1 chính là phân phối Cauchy chuẩn.
>
> **💡 Deeper notes**
> - Trường hợp p = 1 chính xác là phân phối Cauchy chuẩn (standard Cauchy) với tham số vị trí θ = 0 và tham số tỉ lệ γ = 1.

**🔗 See also:** [Kiểm định hợp-giao cỡ α](./83_methods_of_evaluating_test.md#node-aruspge) · [Tối ưu hóa kỳ vọng độ dài](./93_methods_of_evaluating_interval_estimators.md#node-cu30bvl) · [Phân phối Cauchy](./33_continuous_distribution.md#node-sy5tj8j)

<br>

<a id="node-5eltn4g"></a>

###### Derive pdf của phân phối t-Student

<p align="center"><kbd><img src="assets/oweb6o4iaa.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/htfs3tajgbl.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thử làm theo, derive pdf của Student's t:
>
>
>
> Như đã nói, bài toán chính là tìm pdf của U/√(V/p) với U là n(0,1), V là χ²\_p. Và U, V độc lập
>
>
>
> Thế thì: đầu tiên là xây dựng joint pdf của U, V:
>
>
>
> Vì U, V độc lập, nên fU,V(u,v) = fU(u)fV(v)
>
>
>
> = 1/√(2π) exp(-u²/2) × 1/ \[Γ(p/2) 2^(p/2)\] v^\[(p/2)-1\] exp(-v/2),
>
>
>
> \-inf &lt; u &lt; inf, 0 &lt; v &lt; inf
>
>
>
> ---
>
>
>
> Ôn lại nhanh **transformation** **theorem**:
>
>
>
> 1D: khi Y = g(X) với X \~ fX(x), và g là hàm invertible để mapping giữa x ∈ 𝓧 tới g(x) ∈ 𝒴 (ảnh của 𝓧) là 1-1: y = g(x) ∈ image của 𝓧 ⇔ x = g⁻¹(y) ∈ 𝓧 thì ta có transformation theorem:
>
>
>
> fY(y) = fX(x) |dx/dy|
>
>
>
> ⇔ fY(y) = fX(g⁻¹(y)) |d/dy g⁻¹(y)|
>
>
>
> 2D: Với random vector (X,Y) có joint pdf f(x,y): và (U,V) với U = g(X,Y), V = h(X,Y) sao cho mapping giữa (x,y) với (u,v) là 1-1: Mấu chốt: Có thể có (u,v) ∈ ℬ là ảnh của 𝒜 sao cho tồn tại (x1,y1) và (x2,y2) đều thỏa \[g(x,y), h(x,y)\] = (u,v) nhưng chỉ được phép một trong số đó thuộc 𝒜: tức tại đó joint pdf &gt; 0. Khi đó transformation theorem cho ta:
>
>
>
> fU,V(u,v) = fX,Y(x,y) |J| = fX,Y(g⁻¹(u,v),h⁻¹(u,v)) |J|
>
>
>
> **Chú ý:** J là matrix Jacobian (đạo hàm cấp 1) của hàm vector - vector: (x,y) = \[m(u,v), n(u,v)\]
>
>
>
> và |J| thật ra là |(|J|)| hay | det J| tức trị tuyệt đối của det J
>
>
>
> Và cách làm điển hình để có pdf của một rv V = hàm của hai rvs X,Y đó là: ta chọn đại U = X, (hoặc Y), để dựa trên cái này có joint pdf của U,V. Rồi marginalizing over U để có V
>
>
>
> Ta cần mapping 1-1 từ support set của (U,V) tới ảnh của nó.
>
>
>
> ---
>
>
>
> Rồi, ta sẽ define transformation:
>
>
>
> T = g1(U, V) với g1(u,v) = u / √(v/p). W = g2(U,V) , g2(u,v) = v
>
>
>
> Ở đây với t = g1(u,v) = u / √(v/p), w = v thì xem thử có thể giải ra u, v từ t, w không
>
>
>
> w = v ⇨ v = w
>
>
>
> t = u / √(v/p) ⇨ u = t √(v/p) = t √(w/p)
>
>
>
> Như vậy là mapping là 1-1 nên ta có thể dùng transformation theorem.
>
>
>
> ---
>
>
>
> Xây dựng Jacobian: ∂(u,v)/∂(t,w)
>
>
>
> Row 1: \[∂u/∂t, ∂u/∂w\]
>
>
>
> u = t √(w/p) ⇨ ∂u/∂t = √(w/p),
>
>
>
> ∂u/∂w = ∂/∂w \[ t √(w/p)\] = t ∂/∂w \[√(w/p)\]
>
>
>
> = t ∂/∂(w/p) \[√(w/p)\] . ∂/∂w (w/p)
>
>
>
> (d/dz √z = d/dz z^(1/2) = (1/2) z^(-1/2)
>
>
>
> = t (1/2) \[1/(√w/p)\] (1/p)
>
>
>
> = t (1/2) (√p/√w) (1/p)
>
>
>
> = (t/√p) (1/2√w)
>
>
>
> = t/2√(pw)
>
>
>
> Row 2: \[∂v/∂t, ∂v/∂w\]
>
>
>
> v = w ⇨ ∂v/∂t = 0, ∂v/∂w = 1
>
>
>
> ⇨ J = \[√(w/p), t/2√(pw); 0, 1\] ⇨ |J| = √(w/p)
>
>
>
> ---
>
>
>
>
>
> Tiếp: joint pdf của T, W:
>
>
>
> fT,W(t,w) = fU,V(u,v) |J|
>
>
>
> fU,V(u,v) = fU(u)fV(v)
>
>
>
> fT,W(t,w) = \[1/√(2π) exp(-u²/2)\] \[1/ \[Γ(p/2) 2^(p/2)\] v^\[(p/2)-1\] exp(-v/2) √(w/p)\] 
>
>
>
> Và để tìm pdf của T thì ta chỉ việc marginalizing over mọi possible value của W:
>
>
>
> fT(t) = ∫ fU,V(u,v) |J| dw
>
>
>
> = ∫0:∞ 1/√(2π) exp(-u²/2) . 1/ \[Γ(p/2) 2^(p/2)\] v^\[(p/2)-1\] exp(-v/2) √(w/p) dw
>
>
>
> = 1/√(2π) 1/ \[Γ(p/2) 2^(p/2)\] ∫0:∞ exp(-u²/2) × v^\[(p/2)-1\] exp(-v/2) √(w/p) dw
>
>
>
> (đưa constant ra)
>
>
>
> Xét ∫0:∞ exp(-u²/2) × v^\[(p/2)-1\] exp(-v/2) √(w/p) dw
>
>
>
> = ∫0:∞ exp(-u²/2) × v^\[(p/2)-1\] exp(-v/2) √(w/p) dw
>
>
>
> = ∫0:∞ exp(-(t √(w/p))²/2) × w^\[(p/2)-1\] exp(-w/2) √(w/p) dw
>
>
>
> = ∫0:∞ exp(-wt²/2p) × w^\[(p/2)-1\] exp(-w/2) √(w/p) dw
>
>
>
> = ∫0:∞ exp(-wt²/2p) × w^\[(p/2)-1\] exp(-w/2) √(w/p) dw
>
>
>
> ---
>
>
>
> Để đỡ rối: xét và gom hai cục exp(...): exp(-wt²/2p)exp(-w/2) = exp(-wt²/2p-w/2)
>
>
>
> = exp(-w(t²/2p+1/2)) = exp(-w(t²/2p+p/2p)) = exp(-w(t²+p)/2p)) = exp(-w/β') với β' = 2p/(t²+p) = 2/\[(t²/p)+1\].
>
>
>
> ---
>
>
>
> Xét tiếp w^\[(p/2)-1\] √(w/p) = w^\[(p/2)-1\] w^(1/2)/√p = (1/√p) w^\[(p/2)-1+1/2)\] = (1/√p) w^\[(p/2)+(1/2)-1\]
>
>
>
> = (1/√p) w^\[(p+1)/2 - 1\] = (1/√p) w^(α'-1) với α' = (p+1)/2
>
>
>
> ---
>
>
>
> Vậy trong tích phân ở trên là: (1/√p) w^(α'-1)exp(-w/β')
>
>
>
> Đưa (1/√p) ra ngoài tích phân, ta còn lại w^(α'-1)exp(-w/β')
>
>
>
> và xem lại pdf của Gamma:
>
>
>
> Γ(x|α, β) = \[1/Γ(α)βᵅ\] x^(α-1) exp(-x/β),
>
>
>
> Do đó, nó có dạng kernel của Γ(α', β') với α' = (p+1)/2 và β' = 2/\[(t²/p)+1\]
>
>
>
> Nên bằng cách nhân thêm và chia bớt hằng số chuẩn hóa là \[1/Γ(α')β'ᵅ'\], tích phân trở thành 1 theo tính valid của pdf. Còn lại: (1/√p) chia cho \[1/Γ(α')β'ᵅ'\]
>
>
>
> ∫0:∞ exp(-wt²/2p) × w^\[(p/2)-1\] exp(-w/2) √(w/p) dw = (1/√p) chia cho \[1/Γ(α')β'ᵅ'\]
>
>
>
> = Γ(α')β'ᵅ'/√p
>
>
>
> ---
>
>
>
> Cuối cùng, còn nhớ ta còn hai cục const ở trước: 1/√(2π) 1/ \[Γ(p/2) 2^(p/2)\]
>
>
>
> Vậy là kết qủa marginalizing joint pdf của t,w over w, (chính là f(t)):
>
>
>
> f(t) = 1/√(2π) 1/ \[Γ(p/2) 2^(p/2)\] Γ(α')β'ᵅ'/√p
>
>
>
> = 1/(2π)^(1/2) × 1/ \[Γ(p/2) 2^(p/2) p^(1/2)\] × Γ((p+1)/2) × β'ᵅ' với α' = (p+1)/2 và β' = 2/\[(t²/p)+1\]
>
>
>
> Đây chính là công thức pdf của Student t p bậc tự do,

📹 Video 1: [Derive pdf của phân phối t-Student — Statistical Inference - Casella](https://www.youtube.com/watch?v=rrOrZFTeyVE)

📹 Video 2: [Làm sao suy ra pdf Student's t từ tỉ số U/√(V/p) (cont)?](https://www.youtube.com/watch?v=MRIIRaMOWAs)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã tự tay triển khai toàn bộ các bước tính đạo hàm riêng của ma trận Jacobian, gom các số hạng và tính tích phân qua hàm Gamma một cách chuẩn xác.
>
> **🟡 Minor issues**
>
> **1.** *"fT,W(t,w) = [1/√(2π) exp(-u²/2)] [1/ [Γ(p/2) 2^(p/2)] v^[(p/2)-1] exp(-v/2) √(w/p)]"*
>
> Về mặt ký hiệu, hàm mật độ đồng thời f_{T,W}(t,w) cần được viết hoàn toàn theo biến mới (t, w) thay vì để lẫn các biến cũ u, v (dù ở các dòng tích phân ngay sau đó bạn đã thay u, v thành t, w rất chính xác).
>
>
> **✓ Strengths**
> - Thực hiện đầy đủ và chính xác đạo hàm riêng từng phần tử để lập ma trận Jacobian 2x2 thay vì chép lại kết quả có sẵn.
> - Tách và ghép các thành phần lũy thừa của w và số mũ exp rất cẩn thận để nhận dạng đúng dạng hạt nhân (kernel) của phân phối Gamma.
> - Nắm vững định lý biến đổi biến ngẫu nhiên nhiều chiều và kỹ thuật marginalize để tìm hàm mật độ biên.
>
> **💡 Deeper notes**
> - Nếu rút gọn thêm cụm hằng số (hạ 2^{(p+1)/2} từ tử số của [2/(1+t^2/p)]^{(p+1)/2} xuống triệt tiêu với 2^{1/2} và 2^{p/2} ở mẫu), bạn sẽ thu được trực tiếp dạng rút gọn kinh điển của hàm mật độ Student-t.

**🔗 See also:** [Hàm Gamma và Phân phối Gamma](./33_continuous_distribution.md#node-xt1ypib)

<br>

<a id="node-ouu5cht"></a>

###### Giới hạn momen phân phối t

<p align="center"><kbd><img src="assets/rkmoi7hubdh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Student's t distribution không có hàm mgf. Vì ko phải mọi moment 
> nào cũng có. 
>
>
>
> Cụ thể thì nó có moment, nhưng ko có hết. Chính xác là với p bậc tự do thì
> chỉ có p - 1 moment.
>
>
>
> Nên student's t p = 1 thì ko có mean, tức là ko có moment bậc 1
>
>
>
> student's t  p = 2 thì có mean, nhưng ko có variance (moment bậc 2)
>
>
>
> Và ta cũng có công thức của mean (với p > 1) : ETp = 0
>
>
>
> variance với p > 2 VarTp = p / (p - 2)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú nắm rất chính xác và đầy đủ các ý chính từ tài liệu: lý do phân phối Student-t không có mgf, điều kiện tồn tại moment theo bậc tự do p, cùng công thức của kỳ vọng và phương sai.
>
> **✓ Strengths**
> - Hiểu chính xác mối liên hệ: nếu hàm sinh moment (mgf) tồn tại quanh 0 thì mọi moment đều phải tồn tại, do đó việc thiếu các moment bậc cao dẫn đến không có mgf.
> - Tóm tắt đúng và trực quan các trường hợp cụ thể: p = 1 không có mean, p = 2 có mean nhưng không có variance.
> - Ghi lại chính xác điều kiện và công thức cho E(T_p) và Var(T_p).
>
> **💡 Deeper notes**
> - Về mặt toán học, hàm mgf M(t) = E[e^(tX)] không tồn tại với t khác 0 vì phân phối t là phân phối đuôi dày (heavy-tailed, mật độ suy giảm theo hàm đa thức bậc âm thay vì hàm mũ âm), khiến e^(tX)f(x) phân kỳ khi tích phân ra vô cùng.

**🔗 See also:** [Kiểm định hợp-giao cỡ α](./83_methods_of_evaluating_test.md#node-aruspge)

<br>

<a id="node-dl1mlxm"></a>

###### Phân phối F: Tỉ lệ phương sai

<p align="center"><kbd><img src="assets/7tlnh2e8wx5.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là, ta sẽ biết một distribution quan trọng nữa F distributin.
>
>
>
> Động lực của cái này, đó là ta muốn tìm distribution của một "tỉ lệ của
> variances"
>
>
>
> Cho X1,..Xn là random sample n(μX, σX²) và Y1,...Ym là random sample
> n(μY, σY²). Và ta quan tâm đến việc / MUỐN SO SÁNH  ĐỘ BIẾN ĐỘNG
> (VARIABILITY) của hai population. Dĩ nhiên lẽ tự nhiên là ta muốn quan tâm
> đến ratio σX² / σY².
>
>
>
> Thì thông tin về ratios này chứa đựng trong S²X / S²Y (tỉ lệ của hai
> sample variance)
>
>
>
> Thế thì chỗ này phải hiểu là, sở dĩ ta có thể dùng tỉ lệ giữa hai sample
> variance để suy luận, suy đoán cho tỉ lệ giữa hai true population variance
> σX²/σY² là vì / là nhờ vào một loại distribution có tên là F distribution.
> Mà, cụ thể là, cái random variable sau đây sẽ là một F random variable
>
>
>
> S²X/S²Y / σ²X/σ²Y
>
>
>
> Để rồi, tí nữa ta sẽ thấy, khi tính kì vọng của cái random variable này,
> thì ta sẽ thấy nó bằng 1 khi m lớn. Từ đó ý nghĩa là, hay cho phép kết luận
> là, hay có cơ sở để nói là, SX² / SY² ≈ σX² / σY²

<br>

<a id="node-hd9jnpj"></a>

###### Phân phối F và Đối xứng Cầu

<p align="center"><kbd><img src="assets/mqv389ctaxp.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/l8ehfruolw.png" width="80%"></kbd></p>

> [!NOTE]
> Định nghĩa này nói rằng, với random sample size n từ n(μX, σX²)
> và random sample size m từ n(μY, σY²) thì random variable F
> với F = (SX²/σX²)(SY²/σY²) sẽ tuân theo distribution có tên
> là Snedecor's F distribution với bậc tự do là n-1 và m-1
>
>
>
> Và nó có pdf là như trong sách (khá là dài)
>
>
>
> Vậy thì ở đây, giáo sư Casella cho biết  variance ratios có thể có F
> distribution ngay cả khi population không phải normal mà chỉ cần nó có
> tính đối xứng (spherical symmetry)
>
>
>
> Và việc chứng minh ra công thức pdf của F distribution có thể làm 
> tương tự như khi derive pdf của t distribution (nhớ lại, với t distribution,
> thì ta dựa vào định nghĩa của nó là U/√(V/p) với U là normal(0,1) V là
> Chi-square p

<br>

<a id="node-ydb31kk"></a>

###### Phân phối F và phương sai

<p align="center"><kbd><img src="assets/4j73ps0pq9.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp nối phần lập luận ở Example 5.3.5
>
>
>
> ...Thế thì chỗ này phải hiểu là, sở dĩ ta có thể dùng tỉ lệ giữa hai sample
> variance để suy luận, suy đoán cho tỉ lệ giữa hai true population variance
> σX²/σY² là vì / là nhờ vào một loại distribution có tên là F distribution. Mà, cụ
> thể là, cái random variable sau đây sẽ là một F random variable
>
>
>
> S²X/S²Y / σ²X/σ²Y
>
>
>
> Để rồi, tí nữa ta sẽ thấy, khi tính kì vọng của cái random variable này, thì ta sẽ
> thấy nó bằng 1 khi m lớn. Từ đó ý nghĩa là, hay cho phép kết luận là, hay có cơ
> sở để nói là, SX² / SY² ≈ σX² / σY²
>
>
>
> Vừa rồi, đã nói, định nghĩa của distribution của một random variable có được
> bởi (SX²/σX²)(SY²/σY²) là một Fn-1,m-1 random variable, và ta có pdf của
> F rồi.
>
>
>
> Thế thì, xét E[Fn-1,m-1], tức là, ý là xét kì vọng của môt random variable thuộc
> Fn-1,m-1 distribution.
>
>
>
> mà theo định nghĩa, ví dụ như gọi F là một random variable ~ Fn-1,m-1
>
>
>
> thì nó là (kết quả của) lấy SX² / σX² chia cho SY² / σY².
>
>
>
> Mà SX² / σX² thì ta có định nghĩa:
>
>
>
> (n - 1) Sn² / σ² sẽ là một Chi-square n - 1
>
>
>
> Câu này có nghĩa là, nếu ta có random sample size n từ normal(μ, σ²)  thì cái
> random variable được tạo bằng cách lấy hàm g(z) = (n-1) z / σ² apply lên
> sample variance S², thì cái random variable đó sẽ có distribution đã biết, có tên
> là Student t, và nói đã biết tức là ta biết pdf của nó.
>
>
>
> Nếu gọi J = (n - 1) Sn² / σ², thì Sn² / σ² =  J / (n - 1)
>
>
>
> Và đặt U = Sn² / σ², và ta quan tâm đến distribution của thằng rv K này, thì ta
> có thể derive distribution của nó dựa vào transformation K = J / (n-1) và người ta
> gọi K là một Chi-square (n-1) / n - 1 thì có nghĩa là vậy
>
>
>
> Tương tự, nếu gọi V = SY² / σY², thì ta gọi nó là Chi-square (m-1) / (m-1)
>
>
>
> Rồi, tới đây ta lại quan tâm đến distribution của một random variable
>
>
>
> F = U / V, nên ta nói F là một
>
>
>
> [Chi-square (n-1) / n - 1] / [Chi-square (m-1) / (m-1)]
>
>
>
> để từ đó, dựa vào quan hệ này, giúp ta tìm ra pdf của F
>
>
>
> Cái này cũng chỉ y như khi ta có X, Y với pdf đã biết fX, fY, hoặc biết joint pdf
> của chúng fX,Y, và ta quan tâm đến một random variable U tạo ra bởi việc apply
> function g1 lên X, Y. Thì ta ko biết pdf của U, và nhờ transformation theorem ta
> có thể tìm ra được.
>
>
>
> Vậy thì ở đây cũng thế thôi, CÁI VIỆC TA NÓI RẰNG:
>
>
>
> "F là một  [Chi-square (n-1) / n - 1] / [Chi-square (m-1) / (m-1)]"
>
>
>
> CHÍNH LÀ NÓI RẰNG: À, TA CÓ X, Y LÀ HAI RANDOM VARIABLE ĐÃ BIẾT
> PDF (LÀ PDF CỦA CHI-SQUARE), VÀ BÂY GIỜ, MUỐN TÌM PDF CỦA F =
> g(X,Y)
>
>
>
> nên phải hiểu khi nói vậy tức là NHẤN MẠNH VÀO QUAN HỆ, HAY, CÁCH
> TRANSFORMATION.
>
>
>
> Rồi, như vậy việc tìm distribution của F chính là gỉai bài toán (1) ở trên, nhưng
> mình sẽ thay X,Y bằng U, V cho giống trong sách. U là Chi-square n-1, V là
> Chi-square m - 1, và F = g(U,V) = [U/(n-1)]/[V/(m-1).
>
>
>
> Nhưng mà n-1, hay m-1 chỉ là con số cụ thể, ta có thể khái quát nó thành bài
> toán, ta có U là Chi-square p, V là Chi-square q, và F = (U/p) / (V/q), và ta sẽ tìm
> distribution của F. Và đó là phần Exersice 5.17, nhưng cái chính là mình hiểu
> như vậy
>
>
>
> Thế thì cái thằng F mà ta tìm ra pdf của nó từ U, V, người ta gọi distribution của
> nó là F n-1, m-1
>
>
>
> Hoặc khái quát, Fp,q, và ta hiểu Fp,q sẽ là distribution của một random variable
> X nào đó mà được tạo ra bởi g(U,V) = (U/p) / (V/q) với U, V là Chi-squares p, và
> Chi-square q
>
>
>
> Vậy quay lại đây, họ ghi :
>
>
>
> E[Fn-1,m-1] = E{[Chi-square (n-1) / (n-1)] / [Chi-square (m-1) / (m-1)]}
>
>
>
> thì có thể hiểu là, đây giống như nói tắt, đáng là phải nói:
>
>
>
> Cho F ~ Fn-1,m-1, thì nhất định F là một random variable tạo bởi U/p / V/q với
> U, V độc lập và U ~ Chi-square p, V ~ Chi-square q, p = n-1, q = m-1
>
>
>
> EF = E[(U/q) / (V/q)]
>
>
>
> Và do U V độc lập nên U/q và 1/[(V/q)] cũng độc lập
>
>
>
> ... = E[(U/p)] . E[1/(V/q)] = EU/p . qE[1/V]
>
>
>
> = EU/(n-1) . (m-1)E(1/V)
>
>
>
> tiếp theo đó dựa trên việc đã biết pdf của U, V ta tính ra:
>
>
>
> thì có két quả (m - 1)/(m - 3)
>
>
>
> Và do đó nếu m lớn thì EF ≈ 1
>
>
>
> Như vậy kì vọng của một random variable có distribution là Fn-1,m-1 với m lớn,
> sẽ là 1.
>
>
>
> Mà đã nói (SX² / σX²) / (SY² / σY²) với SX là sample variance của random
> sample size n, từ normal(μX, σX²) và SY là sample variance của một random
> sample size m từ normal(μY, σY²) SẼ LÀ MỘT RANDOM VARIABLE CÓ
> DISTRIBUTION Fn-1,m-1
>
>
>
> NHƯ VẬY, với m lớn thì:  E[(SX² / σX²) / (SY² / σY²)] = 1
>
>
>
> Suy ra SX²/SY² ≈ σX²/σY² LÀM CƠ SỞ CHO VIỆC TA CÓ THỂ DÙNG TỈ
> SỐ CỦA HAI SAMPLE VARIANCE ĐỂ SUY LUẬN CHO TỈ SỐ CỦA HAI
> POPULATION VARIANCE

<br>

<a id="node-85e946b"></a>

###### Tính chất phân phối F và t

<p align="center"><kbd><img src="assets/bjahnif90f7.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng là theorem nói đại khái là nghịch đảo của một F rv cũng là 
> một F rv (cái distribution này tên là F, khiến ta dễ lú lẫn, ví dụ mình có thể
> ghi là cho F ~ F, có nghĩa là đặt một random variable F, có distribution F)
>
>
>
> Nếu X là một Student's t có q bậc tự do thì X² là một F 1,q

<br>

