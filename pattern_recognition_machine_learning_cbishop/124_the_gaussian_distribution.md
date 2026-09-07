# 1.2.4 The Gaussian distribution

📊 **Progress:** `10` Notes | `14` Screenshots

---
<a id="node-6omzny8"></a>

<br>

<a id="node-7gzn07s"></a>

## Phân phối Gaussian

<p align="center"><kbd><img src="assets/u1ru4xd7xxq.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói qua về Gaussian distribution, loại phân phối sẽ rất phổ biến trong sách
> này.
>
>
>
> Cái này thì biết rồi, nhưng đây là cơ hội để nhìn lại những gì đã học trong
> Stat110 và Casella về cái này.
>
>
>
> Trong Stat110, gs Joe Blizstein nói về Normal(0,1) từ standard normal trước,
> có pdf là f(z) = 1/√2π exp[-z²/2]
>
>
>
> Rồi ông nói công thức này dễ nhớ hơn, để từ đó ta mới dùng location scale
> family để derive công thức pdf của normal(μ, σ). Location scale theorem nói
> rằng: nếu ta có X ~ f(x) là pdf thuộc location scale family, ứng với location μ,
> scale σ thì Z = (X - μ) / σ sẽ là random variable có pdf thuộc family ứng với
> location 0, scale = 1 gọi là standard member. Ngược lại nếu Z là rv ~ pdf
> standard member thì σZ + μ  sẽ là thành viên ứng với location μ, scale σ
>
>
>
> Và normal là loại của một location scale family, với location trùng với mean, và
> scale trùng với standard deviation.
>
>
>
> Nên ở đây ta có f(z) là standard member thì X = σZ + μ sẽ là thành viên có
> location μ, scale σ
>
>
>
> Dùng transformation theorem ta derive pdf của X = σZ + μ như sau:
>
>
>
> với x = g(z) = σz + u ⇨ z = g⁻¹(x) = (x - μ) / σ
>
>
>
> fX(x) = fZ(z) |dz/dx|
>
>
>
> fZ(g⁻¹(x)) |d/dx g⁻¹(x)|
>
>
>
> = 1/√2π exp[-[(x-μ)/σ]²/2] . (1/σ)
>
>
>
> = 1/√2π exp[-(x-μ)²/2σ²] . (1/σ)
>
>
>
> = 1/σ√2π exp[-(x-μ)²/2σ²]
>
>
>
> Và đây là pdf của X, là thành viên trong họ location scale, ứng với location μ,
> scale σ, Mà như đã nói, với Normal thì location cũng là mean, scale cũng là
> standard deviation. Do đó, đây chính là pdf của normal(μ, σ).
>
>
>
> Ở đây có thể có điểm mà có thể Casella đã nói nhưng ít để ý, 1/σ² gọi là
> precision.

<br>

<a id="node-4gtwvy6"></a>

### Kì vọng Phân phối Chuẩn

<p align="center"><kbd><img src="assets/bn013vjz9fi.png" width="80%"></kbd></p>

> [!NOTE]
> Dĩ nhiên nó là một valid pdf nên nó phải thỏa hai tính chất, sum trên toàn miền
> phải  = 1 và không âm.
>
>
>
> Và mr Bishop để cập đến mean của distribution là μ.
>
>
>
> Còn ở đây, dĩ nhiên để tính mean, tức EX với X ~ normal(μ, σ) có pdf như vậy, thì
> ta sẽ theo định nghĩa của kì vọng mà tính: ∫x f(x)dx
>
>
>
> Để cho dễ ta có thể tính EZ (Z ~ normal(0,1)) trước:
>
>
>
> EZ = ∫-inf:inf zfZ(z)dz = ∫-inf:inf z (1/√2π) e^-z²/2 dz
>
>
>
> = (1/√2π)∫-inf:inf z e^-z²/2 dz
>
>
>
> = (1/√2π) [nguyên hàm của z e^-z²/2] | -inf:inf
>
>
>
> nguyên hàm của z e^-z²/2 chính là -e^-z²/2, 
>
>
>
> vì d/dz (-e^-z²/2) = - d(-z²/2) e^-z²/2 . d/dz -z²/2 (chain rule)
>
>
>
> = - e^-z²/2  (-z)
>
>
>
> = z e^-z²/2
>
>
>
> = (1/√2π) [e^-z²/2] | -inf:inf
>
>
>
> z → -inf → -z²/2 → -inf → [e^-z²/2] → 0
>
>
>
> z → inf → -z²/2 → -inf → [e^-z²/2] → 0
>
>
>
> → kết quả tích phân = 0.
>
>
>
> Cách nhanh hơn là nhận xét hàm k(z) = zfZ(z) là hàm lẻ, vì:
>
>
>
> k(-z) = (-z)fZ(-z) = -z (1/√2π) e^-(-z)²/2 = -z (1/√2π) e^-z²/2 = -k(z)
>
>
>
> Và như vậy thì tích phân từ -inf với inf cũng sẽ = 0.
>
>
>
> Vậy EX = E(σZ + μ), theo tính linearity của kì vọng, = σEZ + μ = 0 + μ = μ 
>
>
>
> Ở đây mình nhắc lại, Normal distribution là một họ distribution thuộc loại location
> scale family, nhưng nó có tính chất đặc biệt là location chính là mean. và scale
> chính là standard deviation. Nói vậy là vì trong Casella ta đã biết, có những
> location scale familly khác thì location chưa chắc đã là mean.

<br>

<a id="node-rfebos3"></a>

#### MGF, moment, phương sai Chuẩn

<p align="center"><kbd><img src="assets/chadgrr3ic.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, còn nhớ trong stat110 và Casella đã học khái niệm mgf (moment generating
> function) - hàm sinh moment. Với moment được định nghĩa là EX là first moment, EX²
> là second moment.
>
>
>
> Hàm mgf, được định nghĩa là mX(t) = E[e^tX].
>
>
>
> Thế thì có thể tính second moment bằng cách dùng lotus: ∫x²fX(x)dx
>
>
>
> Cũng có thể derive công thức mgf của X, để rồi Taylor expansion và lấy hệ số của term
> bậc hai, thì nó cũng chính là second moment.
>
>
>
> Tính theo cách 1: E[X²] = ∫x²fX(x)dx (fX(x) là pdf của normal(μ, σ) nếu muốn ghi rườm
> ra thì ghi là f(x|μ, σ) như trong sách này gs Bishop kí hiệu là chữ N hoa luôn)
>
>
>
> = ∫x² (1/σ√2π) exp[-(x-μ)²/2σ²] dx
>
>
>
> = (1/σ√2π) ∫x² exp[-(x-μ)²/2σ²] dx
>
>
>
> Để tính cái này cần dùng kĩ thuật integration by part
>
>
>
> Để nhớ lại coi, mình nhớ "story" của cái kĩ thuật này vốn chỉ là bắt nguồn từ product rule
> của gỉai tích:
>
>
>
> d(uv) = udv + vdu ⇨ udv = d(uv) - vdu
>
>
>
> ⇨ ∫udv = ∫d(uv) - ∫vdu
>
>
>
> Ta đã giải cái này trong stat110, Casella rồi, ko viết lại nữa.
>
>
>
> Còn làm theo cách kia, thì mgf của X là exp[μt + (1/2)σ²t²]
>
>
>
> Lấy đạo hàm bậc 1 (cũng chính là expand Taylor và lấy hệ số gắn với term bậc 1)
> evaluate tại t = 0 thì ta có fisrt moment (EX)
>
>
>
> d/dt [exp[μt + (1/2)σ²t²]]
>
>
>
> = d/d[μt + (1/2)σ²t²] exp[μt + (1/2)σ²t²] . d/dt [μt + (1/2)σ²t²]
>
>
>
> = exp[μt + (1/2)σ²t²] . (μ + σ²t)
>
>
>
> ⇨ d/dt [exp[μt + (1/2)σ²t²]] | t = 0 =  exp[0] . (μ) = μ
>
>
>
> Lấy đạo hàm bậc 2, evaluate tại t = 0 ta sẽ có second moment, EX²:
>
>
>
> d/dt [đạo hàm bậc nhất] = d/dt [exp[μt + (1/2)σ²t²] . (μ + σ²t)]
>
>
>
> = { d/dt exp[μt + (1/2)σ²t²] } (μ + σ²t)] + [exp[μt + (1/2)σ²t²]  d/dt  (μ + σ²t)] |
> product rule
>
>
>
> = { đạo hàm bậc nhất } (μ + σ²t)] + [exp[μt + (1/2)σ²t²]  σ²]
>
>
>
> ⇨ [đạo hàm bậc 2] | t = 0 = { đạo hàm bậc nhất | t=0} (μ)] + [exp[0]  σ²]
>
>
>
> = [μ (μ)] + [exp[0]  σ²]
>
>
>
> = μ² + σ² → như trong sách
>
>
>
> Và dùng công thức thứ hai của Variance: VarX = EX² - (EX)² = μ² + σ² - μ² = σ².
>
>
>
> ====
>
>
>
> Cái ý mà gs Bishop nói rằng với Normal thì mode trùng với mean là một ý mới mà mình
> chưa nghe trong Casella

<br>

<a id="node-40ke7sj"></a>

##### PDF Gaussian Đa Biến

<p align="center"><kbd><img src="assets/bx1a2il2cy.png" width="80%"></kbd></p>

> [!NOTE]
> Sự thật thì mình nhớ cả Stat110 và Casella đều chưa từng nói về công thức này.
>
>
>
> Nhưng có thể xây dựng công thức của trường hợp iid standard normal trước, tức là joint pdf của iid Zi \~n(0,1) Khi đó 𝐙 sẽ có mean E𝐙 = **0** và covariance matrix Cov(𝐙) = 𝐈.
>
>
>
> Từ đó, đổi biến 𝐗 = A𝐙 + **μ** để E𝐗 = μ và covariance matrix Cov(𝐗) = Σ
>
>
>
> Đầu tiên xây dựng joint pdf của 𝐙:
>
>
>
> f(z1,...zn) = Πi f(zi) (do tính iid) = Πi (1/√2π) exp\[-zi²/2\]
>
>
>
> = \[(2π)^-n/2\] Πi exp\[-zi²/2\]
>
>
>
> = \[(2π)^-n/2\] exp\[-Σizi²/2\]
>
>
>
> Thể hiện dưới dạng vector: Σizi² = 𝐳ᵀ𝐳
>
>
>
> .. = \[(2π)^-n/2\] exp\[-𝐳ᵀ𝐳/2\]
>
>
>
> Thế thì, tất nhiên E𝐙 = \[EZ1, EZ2,...EZd\] = \[0, ...0\] = **0** Bữa trước đã nói covariance của hai random variable vector 𝐗, 𝐘 sẽ là một matrix: Cov(𝐗, 𝐘) = E\[(𝐗 - E𝐗)(𝐘 - E𝐘)ᵀ\], để rồi phần tử hàng i cột j: ij sẽ là E\[(Xi - EXi)(Yj - EYj)\] chính là Cov(Xi, Yj)
>
>
>
> ⇨ Cov(𝐙, 𝐙), có thể viết tắt là Cov(𝐙), = E\[(𝐙 - E𝐙)(𝐙 - E𝐙)ᵀ\]
>
>
>
> = E\[**ZZ**ᵀ\] (kì vọng của 𝐙 outer product với 𝐙)
>
>
>
> Và matrix này sẽ có phần tử thứ ij là Cov(Zi, Zj). Và phần tử trên đường chéo ii chính là Var(Zi) (Cov(Zi, Zi) chính là Var(Zi))
>
>
>
> Vấn đề là Zi, Zj độc lập, do ta đang xét iid Zi: Nhớ lại định nghĩa iid đã học trong Stat110 và Casella: Random sample of size n X1,....Xn \~ f(x|θ) được định nghĩa là: Ta thực hiện quan sát một đại lượng ngẫu nhiên nào đó, n lần Mỗi lần giá trị của nó sẽ được đại diện bằng random variables Xi. Và cách thực hiện đảm bảo sao cho các rvs Xi MUTUALLY INDEPENDENT, và chúng đều có chung population distribution f(x|θ), gọi là IDENTICALLY DISTRIBUTED.
>
>
>
> Và đã biết nếu X, Y độc lập thì E(XY) = EXEY ⇨ Cov(X, Y) = 0. Vậy Cov(Zi, Zj) = 0 ∀ i ≠ j.
>
>
>
> Còn Var(Zi) thì vì Zi \~ n(0,1), nên nó bằng 1.
>
>
>
> Do đó Cov(𝐙,𝐙) CHÍNH LÀ IDENTITY MATRIX.
>
>
>
> Rồi, ta sẽ
>
>
>
> Đổi biến 𝐗 = g(𝐙) = **AZ** + **μ** với **Σ = AA**ᵀ là covariance matrix mong muốn, **μ** là vector \[μ1, ...,μn\]. Và ta sẽ xây dựng pdf của 𝐗, mà ta cho rằng nó sẽ chính là pdf của multivariate Normal(**μ**, **Σ**)
>
>
>
> Do đó cần làm rõ hai điểm:
>
>
>
> 1. Đổi biến như vậy, thì 𝐗 có phải là normal không.
>
>
>
> 2. Mean và covariance có phải là **μ** và **Σ** không.
>
>
>
> Trả lời ý 1:
>
>
>
> Điều này đồng nghĩa với việc Xi có phải là normal distribution nữa không.
>
>
>
> Với 𝐗 = **AZ** + **μ**, Xi = \[hàng i của A\]ᵀZ + μi
>
>
>
> = Σj=1:d aij Zi + μi
>
>
>
> tức là một affine combination của Zi (ko phải là linear combination nhé)
>
>
>
> Thế thì hồi Stat110 đã học, nếu X, Y đều là normal rv thì X + Y cũng là normal
>
>
>
> Chứng minh thì cũng dễ thôi, dùng một theorem liên quan MGF: Đó là nếu X, Y độc lập thì với U = X + Y thì ΜU(t) = MX(t)\*MY(t). Chứng minh rất dễ:
>
>
>
> Theo định nghĩa, moment generating function mgt của X, kí hiệu là MX(t) được định nghĩa là = E\[e^tX\].
>
>
>
> ⇨ Μ(t) = E\[e^tU\] = E\[e^t(X+Y)\] = E\[e^tX \* e^tY\]
>
>
>
> Và theo 2D LOTUS, ta tính cái này: ∫∫ e^tx e^ty fXY(x,y)dxdy (fXY(.) là joint pdf của X, Y)
>
>
>
> Mà X, Y độc lập thì joint pdf = tích marginal pdf:
>
>
>
> ∫∫ e^tx e^ty fXY(x,y)dxdy = ∫∫ e^tx e^ty fX(x)fY(y)dxdy
>
>
>
> = ∫e^tyfY(y) \[∫e^tx fX(x)dx\] dy | tính tích phân theo x trước coi term liên quan đến y như constant, đưa ra
>
>
>
> = ∫e^tx fX(x)dx ∫e^tyfY(y)dy | tính tích phân theo y thì coi ∫e^tx fX(x)dx như constant, đưa ra
>
>
>
> = Đây chính là E\[e^tX\] E\[e^tY\]
>
>
>
> cũng chính là MX(t) \* MY(t).
>
>
>
> Áp dụng theorem này, nếu X \~ normal(μ1, σ1²) và Y \~ normal(μ2, σ2²)
>
>
>
> và với normal μ, σ ta biết mgf có dạng: exp(μt + σ²t²/2)
>
>
>
> thì ΜU(t) = MX(t) \* MY(t) = exp(μ1t + σ1²t²/2) exp(μ2t + σ2²t²/2)
>
>
>
> = exp(μ1t+μ2t + σ1²t²/2 + σ2²t²/2)
>
>
>
> = exp\[(μ1+μ2)t + \[σ1²/2 + σ2²/2\]t²)
>
>
>
> có dạng một mgf của normal(μ1 + μ2, σ1² + σ2²)
>
>
>
> và như đã biết trong Stat110, hay Casella, MGF, cũng như CDF, PDF, PMF có thể định nghĩa một distribution. Có nghĩa là ta có thể kết luận U = X + U chính là một normal(μ1 + μ2, σ1² + σ2²).
>
>
>
> Vậy thì quay lại đây:
>
>
>
> Đầu tiên phải nói a1i Zi, với việc Zi \~ normal(0,1), tức standard normal, mà như đã biết, normal là một location scale family, với điểm đặc biệt là location trùng với mean, scale cũng chính là standard deviation. Và theo lí thuyết location scale family, thì nếu ta có Z là standard member, tức là pdf có location 0, scale 1, thì σZ + μ sẽ là rv có pdf thuộc family nhưng ứng với location μ, scale σ.
>
>
>
> Vậy ở đây a1iZi chính là thành viên ứng với location 0, scale a1i. Cũng đồng nghĩa, nó là normal(0, a1i²) với với i = 1,...,d.
>
>
>
> Vậy thì xét a11Z1 + a12Z2, đây là tổng của hai rvs: a11Z1\~ normal(0, a11²) và a12Z2 \~ normal(0, a12²)
>
>
>
> Nên theo điều vừa ôn lại, nó chính là rv \~ normal(0+0, a11² + a12²)
>
>
>
> Và lặp lại lập luận này, ta sẽ có Σj a1jZj chính là một normal(0, Σj a1j²), tức là variance của rv này là tổng các phần từ hàng 1 của A.
>
>
>
> Tiếp, ta, theo location scale cũng dễ thấy Σj a1jZj + μ1 cũng là một normal(μ1, Σj a1j²)
>
>
>
> Vậy X1 là normal(μ1, Σj a1j²), ..
>
>
>
> Xi \~ normal(μi, Σj aij²)
>
>
>
> Như vậy ta sẽ trả lời ý 2 luôn:
>
>
>
> Với Xi \~ normal(μi, Σj aij) ⇨ E\[𝐗\] = \[EX1,...EXd\] = \[μ1, ..μd\] = **μ**.
>
>
>
> Cov(𝐗, 𝐗) = E\[(𝐗 - E𝐗)(𝐗 - E𝐗)ᵀ\]
>
>
>
> = E\[(𝐗 - E𝐗)(𝐗ᵀ - (E𝐗)ᵀ)\]
>
>
>
> = E\[(A𝐙 + **μ** - **μ**)((A𝐙 + **μ**)ᵀ - **μ**ᵀ)\]
>
>
>
> = E\[(A𝐙)(𝐙ᵀ𝐀ᵀ + μT - μT)\]
>
>
>
> = E\[**AZZ**ᵀ𝐀ᵀ\]
>
>
>
> = 𝐀E\[**ZZ**ᵀ\]𝐀ᵀ (Linearity)
>
>
>
> Xét E\[**ZZ**ᵀ\]: Để thấy nó là cái gì, ta xét Cov(𝐙,𝐙) = E\[(𝐙-E𝐙)(𝐙-E𝐙)ᵀ\] = E\[(𝐙 - **0**)(𝐙ᵀ - **0**ᵀ\] (**0** là vector zero)
>
>
>
> = E\[**ZZ**ᵀ\]. À như vậy,E\[ZZᵀ\] = Cov(**Z,Z**) và như ở trên mình đã biết, nó là Identity matrix: I
>
>
>
> Vậy.. = A I Aᵀ = AAᵀ và như đã nói, ta chọn A sao cho Σ (covariance matrix mong muuốn) = AAᵀ
>
>
>
> ⇨ Cov(𝐗,𝐗) = **Σ**
>
>
>
> =====
>
>
>
> Tới đây ta đã chứng minh xong 𝐗 sẽ là normal(**μ**, **Σ**). Việc bây giờ là xây dựng pdf của X
>
>
>
> Tất nhiên là ko thể tích các marginal pdf của Xi được, vì Xi KHÔNG ĐỘC LẬP, COVARIANCE MATRIX KO PHẢI LÀ DIAGONAL MATRIX (các term ngoài đường chéo, là covariance các Xi, Xj)
>
>
>
> Ta sẽ dùng công cụ transformation:Thế thì, đã học trong Casella, nếu ta có random vector (vector of random variable) \[X,Y\] và thông qua một phép biến đổi để có \[U,V\] = \[g1(X,Y), g2(X,Y)\]
>
>
>
> Sao cho mapping giữa (X,Y) ∈ support set của \[X,Y\] và (U,V) là 1-1.
>
>
>
> (support set của X còn nhớ, đại khái là subset của range X sao cho tại đó / trên đó pdf/pmf của X dương, vậy thì support set của random vector \[X, Y\], là subset của R², sao cho trên đó joint pdf fX,Y(x,y) dương)
>
>
>
> Có nghĩa là, với U,V ∈ support set của \[U,V\] ta có thể tìm được (X, Y) = \[h1(U,V), h2(U,V)\] thuộc support set của random vector \[X,Y\])
>
>
>
> Thì khi đó ta có transformation theorem cho phép tính joint pdf của U,V từ joint pdf của X,Y:
>
>
>
> fU,V(u,v) = fX,Y(x,y) |J|
>
>
>
> = fX,Y(h1(u,v), h2(u,v)) |∂(x,y) /∂(u,v)|
>
>
>
> Như đã biết từ MIT 18.02, kí hiệu này ∂(x,y) /∂(u,v) nhằm chỉ Jacobian matrix, mà hàng 1 sẽ là ∂x/∂u, ∂x/∂v hàng 2 sẽ là ∂y/∂u, ∂y/∂v.
>
>
>
> Thế thì giả sử \[U,V\]ᵀ = A \[X,Y\]ᵀ + μ (tức là cũng là một affine transformation)
>
>
>
> Ôn lại kiến thức giải tích nếu ta có f(x) = Ax + b là Rⁿ → R^m function ⇨ ∇f(x), cũng là Jacobian.
>
>
>
> Theo MIT 18s096, ta có thể tính ∇f(x) như sau: df = f(x + dx) - f(x) = Ax + Adx + b - Ax - b = Adx linear operation act on dx, Và bản chất của đạo hàm bậc nhất là một linear operation act on dx : f'(x)\[dx\] Từ đó suy ra matrix Jacobian chính là A.
>
>
>
> Nếu A invertible, ta có quan hệ ngược lại: x = A⁻¹(f - b) = A⁻¹f - A⁻¹b
>
>
>
> Và khi đó ∇x(f), là Jacobian của phép biến đởi f → x chính là A⁻¹.
>
>
>
> Vậy thì quay lại đây nếu gọi vector **f** = \[u,v\]ᵀ và 𝐱 = (x,y) thì Jacobian ∂(x,y) / ∂(u,v) chính là A⁻¹.
>
>
>
> Và cái ta cần là determinant của nó: |det A|
>
>
>
> Và ta cũng đã biết trong MIT 1806: det A⁻¹ = 1/ det A. Chứng minh rất dễ: AA⁻¹ = A⁻¹ A = I ⇨ det(AA⁻¹) = det I = 1 (tính chất đầu tiên của det thầy Strang dạy trong bài định thức chính là det I = 1)
>
>
>
> Rồi det(AB) = det A det B ⇨ det (AA⁻¹) = det A det A⁻¹ = 1 ⇨ det A⁻¹ = 1 / det A
>
>
>
> Vậy cái cần |∂(x,y) /∂(u,v)|, chính là 1 / |det A|
>
>
>
> ====
>
>
>
> Tiếp tục: fU,V(u,v) = fX,Y(x,y) |J|
>
>
>
> Công thức này (bivariate case) cũng sẽ khát quát lên cho multivariate case.
>
>
>
> Nên áp dụng nó, với random vector X = A Z + μ
>
>
>
> fX(x) = fZ(z) |J|
>
>
>
> Và ta đã hiểu |J| cũng chính là 1/ |det A|
>
>
>
> Thay fZ(z) vô: = \[(2π)^-d/2\] exp\[-𝐳ᵀ𝐳/2\]
>
>
>
> Với 𝐱 = A𝐳 + **μ** ⇨ z = A⁻¹𝐱 - A⁻¹**μ**
>
>
>
> ⇨ 𝐳ᵀ𝐳 = (A⁻¹𝐱 - A⁻¹**μ**)ᵀ(A⁻¹𝐱 - A⁻¹**μ**)
>
>
>
> = (𝐱ᵀA⁻¹ - **μ**ᵀA⁻¹ᵀ)(A⁻¹𝐱 - A⁻¹**μ**)
>
>
>
> = 𝐱ᵀA⁻¹ᵀA⁻¹𝐱 - **μ**ᵀA⁻¹ᵀA⁻¹𝐱 - 𝐱ᵀA⁻¹ᵀA⁻¹**μ** + **μ**ᵀA⁻¹ᵀA⁻¹**μ**
>
>
>
> Dùng hai identity:
>
>
>
> (AB)⁻¹ = B⁻¹A⁻¹ (nếu A, B invertible). chứng minh dễ ẹt: (AB)(B⁻¹A⁻¹) = A I A⁻¹ = AA⁻¹ = I ⇨ invert của AB chính là B⁻¹A⁻¹
>
>
>
> Và (A⁻¹)ᵀ = (Aᵀ)⁻¹, cũng dễ chứng minh: AA⁻¹ = I ⇔ (AA⁻¹)ᵀ = I ⇔ A⁻¹ᵀ Aᵀ = I ⇨ inverse của Aᵀ chính là A⁻¹ᵀ
>
>
>
> ⇨ A⁻¹ᵀA⁻¹ = (Aᵀ)⁻¹A⁻¹ = (AAᵀ)⁻¹ = Σ⁻¹
>
>
>
> ⇨ 𝐱ᵀA⁻¹ᵀA⁻¹𝐱 - μTA⁻¹ᵀA⁻¹𝐱 - 𝐱ᵀA⁻¹ᵀA⁻¹**μ** + **μ**ᵀA⁻¹ᵀA⁻¹**μ**
>
>
>
> = (𝐱ᵀ - μT)Σ⁻¹𝐱 - (𝐱ᵀ- **μ**ᵀ)Σ⁻¹**μ**
>
>
>
> = (𝐱ᵀ - **μ**ᵀ)(Σ⁻¹𝐱 - Σ⁻¹**μ**)
>
>
>
> = (𝐱ᵀ - **μ**ᵀ)Σ⁻¹(𝐱 - **μ**)
>
>
>
> = (𝐱 - **μ**)ᵀΣ⁻¹(𝐱 - **μ**)
>
>
>
> Vậy f𝐗(𝐱) = \[(2π)^-d/2\] exp\[-(𝐱 - **μ**)ᵀΣ⁻¹(𝐱 - **μ**)/2\] \[1 / |det A|\]
>
>
>
> = \[(2π)^-d/2\] \[1/|det A|\] exp\[-(𝐱 - **μ**)ᵀΣ⁻¹(𝐱 - **μ**)/2\]
>
>
>
> Và Σ = AAᵀ ⇨ det Σ = det A det Aᵀ
>
>
>
> Và det A = det Aᵀ: Vì sao?
>
>
>
> Theo MIT 1806, trong bài 18. phần cuối gs Strang có nói vần đề này. Đại khái là vầy:
>
>
>
> Khi khử Gaussian đưa A → U, ta có A = LU. ⇨ det A = det L det U.
>
>
>
> L và U đều là lower triangular matrix: det = tích đường chéo (tính chất chung của det của triangular matrix)
>
>
>
> Và L là matrix đường chéo = 1, vì sao? ⇨ det L = 1
>
>
>
> ⇨ det A = det U
>
>
>
> Aᵀ = (LU)ᵀ = Lᵀ Uᵀ ⇨ det (Aᵀ) = det Lᵀ det Uᵀ
>
>
>
> = 1 \* det Uᵀ = det U
>
>
>
> Vậy det A = det Aᵀ vì đều bằng det U
>
>
>
> VẬY det Σ = det A det Aᵀ = (det A)² ⇨ |det A| = (det Σ)^1/2
>
>
>
> Và kết quả cuối cùng là f𝐗(𝐱) = \[(2π)^-d/2\] \[1/(det Σ)^1/2\] exp\[-(𝐱 - **μ**)ᵀΣ⁻¹(𝐱 - **μ**)/2\]
>
>
>
> trong sách gs Bishop dùng R^D vector, và |Σ| chính là kí hiệu của det như đã biết
>
>
>
> nên ta có công thức trong sách.
>
>
>
> \[(2π)^-D/2\] \[1/|Σ|^1/2\] exp\[-(𝐱 - **μ**)ᵀΣ⁻¹(𝐱 - μ)/2\]
>
>
>
> =====
>
>
>
> Cuối cùng để chặt chẽ, ta cần nói về việc vì sao có thể tồn tại A
>
>
>
> Σ = AAᵀ, lí do có thể phân tách Σ, hay nói cách khác, có thể tìm được A thỏa điều này là vì Σ là matrix xác định dương (positive definite)

**🔗 See also:** [Tính toán hàm evidence](./351_evaluation_of_the_evidence_function.md#node-u15ayc8) · [Log Marginal Likelihood Derivation](./351_evaluation_of_the_evidence_function.md#node-ddcs0pi) · [Section 3.5.3 Effective Number of Parameters](./353_effective_number_of_parameters.md#node-2wanjgv) · [Ex 3.6  MLE Hồi quy Đa biến](./37_exercises.md#node-cq8t94f) · [Ex 3.7 Posterior Distribution in Linear Basis Models](./37_exercises.md#node-97teyoh)

<br>

<a id="node-yyj622u"></a>

###### Ký hiệu vector và mẫu ngẫu nhiên

<p align="center"><kbd><img src="assets/z4ghx6oil9d.png" width="80%"></kbd></p>

> [!NOTE]
> Dưới ánh sáng của Casella thì đoạn này không có gì khó hiểu:
>
>
>
> Như trong cái note vừa rồi mình derive công thức pdf của multivariate Gaussian cũng đã
> ôn lại khái niệm iid: random sample là một bộ các random variable X1,..Xn có cùng
> population distribution f(x|θ) (identically distributed) và chúng mutually independent
>
>
>
> Khi đó xét random vector 𝐗 = [X1,...Xn] có pdf, cũng là joint pdf của X1,..Xn f(𝐱).
> Do tính iid, = Πi=1:n f(xi|θ)
>
>
>
> Thì chỗ này gs Bishop có một ý có thể gây confuse đây:
>
>
>
> ông nói x = (x1,....xD)ᵀ để chỉ một observed value của random variable vector.
>
>
>
> Còn 𝐱 = (x1,....xN) là chỉ một tập các observed value được drawn iid từ Normal (μ,
> σ²)
>
>
>
> Hồi nãy, khi xây dựng công thức multivariate Gaussian (**μ**, **Σ**), mình đã bắt đầu với
> 𝐙 = (Z1,...ZD) là random variable vector, với Zi ~ normal(0,1). Để rồi đổi biến với X =
> A𝐙 + **μ** ta có 𝐗 là vector (X1,...XD)
>
>
>
> Thế thì theo đó (x1,...xD) đúng là một observed value của 𝐗, là một R-D dimensional
> random variable vector ~ Normal(**μ**, **Σ**).
>
>
>
> Thật ra nếu theo notation Casella, thì nếu đặt x = (x1,...xD) thì ta cũng sẽ viết x bold vì
> quy ước luôn là bold cho vector, thường cho scalar. Nên 𝐱 = (x1,... xD)
>
>
>
> Còn ở đây, 𝐗 = (X1,...,Xn) chính là một random sample, như định nghĩa vừa nhắc lại
> ở trên. Do đó vector thì lúc này 𝐱 = (x1,...xn) lại là vector các observed values tức là
> X1 = x1, X2 = x2,...
>
>
>
> Nên X trong bối cảnh sau và bối cảnh trước nó hơi khác nhau.
>
>
>
> Nhưng nếu cứ theo toán mà làm, thì thật ra cũng đều là 𝐗, random variable vector và
> 𝐱 là giá trị quan sát được của nó.
>
>
>
> Và sự thật thì distribution của 𝐗 trong bối cảnh sau cũng là N-dimensional Normal chỉ
> có điều μ và Σ = diag(σ²) = σ² I (vì các biến X1,...Xn độc lập, nên Covariance matrix
> sẽ là matrix chéo có đường chéo là variance của các Xi, đều là σ², còn ngoài đường
> chéo thì = 0 hết do Cov(Xi, Xj) = 0
>
>
>
> Do đó, đoạn này gs phân biệt như vậy, có thể gây khó hiểu.
>
>
>
> Tóm lại ngắn gọn thế này:
>
>
>
> Nếu ta có 𝐗 là một D-dimensional Normal(**μ, Σ**), thì một observed value của nó, sẽ
> là vector:
>
>
>
> thì X là vector các random variable [X1,...XD] trong đó:
>
>
>
> Xi sẽ có distribution là Normal(μi, Σii),
>
>
>
> Xj có distribution là Normal(μj, Σjj)
>
>
>
> Cov(Xi, Xj) = Σij
>
>
>
> Và x = (x1,...xD)là vector các possible value / observed values của X1,...XD
>
>
>
> -----
>
>
>
> Rồi, nếu bây giờ, đổi distribution của X đi chút, để nó là **D-dimensional Normal**(μ
> **1**, σ² 𝐈)
>
>
>
> μ***1** có nghĩa là nhân scalar μ cho vector 1 = [1,...1] để có vector [μ,...μ]
>
>
>
> σ² * 𝐈 có nghĩa là nhân scalar σ² cho Identity matrix để có matrix với diagonal là
> [σ², ...σ²]
>
>
>
> Thì khi đó, Xi sẽ ~ Normal(μ, σ²) ∀i, và Cov(Xi, Xj) = 0
>
>
>
> Và x = (x1, ...xD) cũng là vector các possible value của X1,...XD
>
>
>
> ------
>
>
>
> Nhưng nếu, ta có **1-dimensional distribution Normal**(μ, σ²), và ta sampling từ nó N
> lần, để tạo random sample size N: X1,..Xn, independent identically distributed.
>
>
>
> Thì khi đó Xi cũng ~ Normal (μ, σ²) với mọi i
>
>
>
> Và nếu gom tụi nó lại, để có vector 𝐗' = (X1,...XN) thì VỀ BẢN CHẤT, X' SẼ CÓ
> DISTRIBUTION LÀ Normal(μ * **1**, σ² * I) y như ở case trên
>
>
>
> Chẳng qua chỉ khác đây là **N-dimensional Normal**(μ * **1**, σ² * I).
>
>
>
> ====
>
>
>
> Rồi, thế thì như vậy giúp hoàn toàn rõ ràng rằng, ở đây ta có 𝐗 (mà gs dùng chữ
> 𝐱, vốn là đã khiến ta mệt mỏi, vì ông làm vậy ông đã không còn theo quy tắc đặt tên
> của toán rồi nhưng may mà mình học Casella nên hiểu rõ để ko bị lú. Nên cứ viết theo
> notation của Stat110 hay Casella: Viết hoa cho biến, viết thường cho giá trị biến, chữ
> đậm cho vector, chữ ốm cho scalar) là random sample của các X1,...XN có population
> distribution là Normal (μ, σ²) (và như đã nói, đồng nghĩa 𝐗 = (X1,..Xn) sẽ ~
> N-dimensional Normal(μ * **1**, σ² * I) Để rồi sampling từ cái 1-dimensional Normal(μ,
> σ²) n lần để có 𝐱 = (x1,...xn) thì cũng Y CHANG sampling đúng một lần, từ
> N-dimensional Normal(μ * **1**, σ² * I) để có 𝐱 = (x1,...xn)
>
>
>
> Và đó chính là data set, và tới đây CHÚ Ý CỤM TỪ NÀY CỦA mr BISHOP:
>
>
>
> **PROBABILITY OF THE DATA SET**
>
>
>
> Ý ông là sao?
>
>
>
> → Nó chính là ông đang nói: 
>
>
>
> GIÁ TRỊ JOINT PDF CỦA RANDOM SAMPLE 𝐗 = (X1,.. XN) TẠI OBSERVED VALUE 𝐗 = 𝐱
>
>
>
> Và vì hai cách hiểu trên hoàn toàn phản ánh cùng bản chất, nên ta có thể làm theo lối
> hay làm trong Casella:
>
>
>
> f𝐗(x1,...xn|μ,σ²), với X1,...Xn iid, tức independent, nên joint pdf  = tích marginal pdf:
>
>
>
> = f(x1|μ,σ²)f(x2|μ,σ²)...f(xN|μ,σ²)
>
>
>
> = Πi=1:N f(xi|μ,σ²) với f(x|μ, σ²) là pdf của Normal(μ, σ²)
>
>
>
> Còn nếu theo góc nhìn là giá trị của pdf của **X, ~ N-dimensional Normal**(μ * **1**, σ²
> * I), tại 𝐗 = 𝐱, thì ta có:
>
>
>
> f𝐗(𝐱) với f𝐗(𝐱) là pdf của 𝐗 ~ N-dimensional Normal(μ * 1, σ² * I)
>
>
>
> và nó là công thức vector mà ta chứng minh hồi nãy chỉ thay μ = μ * 1 và Σ = σ² * I vô
> thôi
>
>
>
> Dĩ nhiên HAI GÓC NHÌN ĐỀU PHẢN ÁNH CÙNG MỘT BẢN CHẤT VÀ NÓ LÀ MỘT
>
>
>
> Nên nến dùng chữ /N/ (N kiểu)  làm pdf của Normal như trong sách, thì ta có:
>
>
>
> Πi=1:N /N/(xi| μ, σ²) cũng chính là N(𝐱| μ***1**, σ²*𝐈)

<br>

<a id="node-xm5nidw"></a>

###### Hàm hợp lý và phân phối Chuẩn

<p align="center"><kbd><img src="assets/rrlibhsewk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hous6aym2b.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì, đã nhắc lại vài lần trong các note trước, trong Casella, ta đã biết
> khái niệm likelihood function, nó làm hàm của θ, (mang ý nghĩa độ hợp lí của θ
> nếu như observed value là 𝐱), kí hiệu L(θ|𝐱) và hàm này được định nghĩa
> là L(θ|𝐱) = f(𝐱|θ), tức joint pdf của random sample tại 𝐱.
>
>
>
> Do đó mới nói, cái mà ta có vưa rồi, **XÁC SUẤT CỦA DATA SET**,
>
>
>
> N(𝐱 | μ**1**, σ²*I) = Πi=1:N N(xi | μ, σ²)  **CHÍNH LÀ** **LIKELIHOOD
> FUNCTION CỦA** θ = (μ***1,** σ²*I) **TẠI X = x**
>
>
>
> L(μ***1**, σ²*I | 𝐱), hoặc coi là hàm theo scalar μ, σ² thôi cũng được
> L((μ, σ²)| 𝐱)
>
>
>
> = N(𝐱 | μ**1**, σ²*I) = Πi=1:N N(xi| μ, σ²)
>
>
>
> -----
>
>
>
> Và người ta mới vẽ cái hình này là sao.
>
>
>
> Chú ý, đường màu đỏ: KHÔNG PHẢI LÀ ĐỒ THỊ HÀM LIKELIHOOD.
>
>
>
> Vì hàm likelihood là hàm của (μ, σ²)
>
>
>
> Cái hình đó, người ta đang vẽ cái gì:
>
>
>
> Với các đỉem x1, ....xn
>
>
>
> giá trị marginal pdf của Normal(μ, σ²) tại đó f(x1| μ, σ²),...f(xn | μ, σ²) là các
> đoạn xanh lá)
>
>
>
> THÌ **TÍCH CỦA CHÚNG**, MỚI LÀ GIÁ TRỊ CỦA LIKELIHOOD TẠI (μ, σ²):
> L((μ, σ²) | 𝐱)
>
>
>
> Vậy đường màu đỏ là gì, thực ra nó rất dễ confuse
>
>
>
> NÓ KO PHẢI LÀ ĐỒ THỊ CỦA LIKELIHOOD, RẤT NHẢM NHÍ NẾU NGHĨ VẬY.
>
>
>
> NÓ CŨNG KHÔNG PHẢI LÀ ĐỒ THỊ CỦA POPULATION NORMAL N(μ, σ²)
> VÌ BẢN CHẤT TA KO BIẾT μ, σ² là bao nhiêu.
>
>
>
> SỰ THẬT, NÓ CHỈ LÀ MINH HỌA CHO ĐỒ THỊ CỦA NORMAL
> TẠI MỘT CẶP (μ, σ²) **NÀO ĐÓ**.
>
>
>
> ĐỂ RỒI TA SẼ ĐI MAXIMIZE CÁI LIKELIHOOD, CHÍNH LÀ ĐI TÌM MỘT
> CẶP (μ, σ²) SAO CHO TÍCH CỦA MẤY CÁCH ĐOẠN MÀU XANH LÁ NÀY
> LỚN NHẤT.
>
>
>
> Vì với mỗi 1 cặp μ, σ², ta sẽ có f(x1|μ, σ²), f(x2|μ, σ²) khác nhau, và nhân
> tụi nó lại để được L(μ, σ²|𝐱) khác nhau. Và sẽ có 1 cặp nào đó maximize
> giá trị này.
>
>
>
> Và đó chính là MAXIMUM LIKELIHOOD ESTIMATOR CỦA θ = (μ, σ²)

<br>

<a id="node-0k0d9g2"></a>

###### Ước lượng Tham số Likelihood

<p align="center"><kbd><img src="assets/xmicg2sfvxj.png" width="80%"></kbd></p>

> [!NOTE]
> đoạn ông nói một tiêu chí (criterion) để tìm ra parameter của một distribution
> dựa trên  giá trị observed data đó là tìm param khiến maximize likelihood.
>
>
>
> Và có thể thấy lạ, vì đáng lí thì phải maximize distribution của param dựa
> trên observed data chứ sao lại maximize likelihood, nhưng thực ra thì nó có
> liên hệ nhau"
>
>
>
> Như đã biết, dựa vào Bayes rule, ta xây dựng posterior distribution của θ:
> π(θ|𝐱) = f(𝐱|θ) π(θ) / f**(**x) và với f(𝐱|θ) = L(θ|𝐱) nên  π(θ|𝐱) = L(θ|𝐱) π(θ) / f(𝐱)
> và nếu π(θ) chọn là uniform, tức π(θ) = constant thì maximize L(θ|𝐱) cũng
> chính là maximize π(θ|𝐱)

<br>

<a id="node-alwk6lh"></a>

###### MLE phân phối chuẩn

<p align="center"><kbd><img src="assets/jduciam1g1b.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qth6ji8fxv.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là, vừa rồi nói rằng ta sẽ đi tìm θ để sao cho maximize cái π(θ|𝐱) và ta sẽ thấy rằng
> nó có liên hệ với việc maximize L(θ|𝐱) sau.
>
>
>
> Còn giờ, ta thử đi tìm θ maximize likelihood L(θ|𝐱) trước, cụ thể là với θ là params của normal
> distribution: θ = (μ, σ²).
>
>
>
> Thì thật đây chính là cái ví dụ mình đã làm trong Casella: Đi tìm MLE của Normal, đây là cơ hội để
> làm lại ví dụ này.
>
>
>
> Đầu tiên ôn lại chút, bối cảnh chương 7 sách Casella là ta deal với bài toán: point estimator - Dựa
> trên giá trị quan sát được của random sample 𝐗 ~ f(𝐱|θ) ta muốn thực hiện một suy luận về
> giá trị của θ, và mục tiêu là xây dựng một point estimator, được định nghĩa là một hàm của sample,
> một statistic W(𝐗)  bất kì (tức là bất kì hàm số nào của random sample thì đều có thể đóng vai
> một point estimator của θ)
>
>
>
> Dĩ nhiên, theo định nghĩa trên thì việc tìm point estimator tốt sẽ rất mơ hồ Do đó ta mới bàn đến vài
> cách tiếp cận - 3 phương pháp đề cập trong sách Casella: method of moment, maximum likelihood,
> Bayes:
>
>
>
> Thế thì, với MLE, định nghĩa của nó là: ta sẽ maximize hàm likelihood L(θ|𝐱) là hàm của θ, define
> bởi L(θ|𝐱) = f(𝐱|θ), nên θ^_mle(𝐱) = argmax_θ L(θ|𝐱) = argmax_θ f(𝐱|θ), và vì tính iid
> của random sample, f(x|θ) = Πi=1:n f(xi|θ) ⇨ θ^_mle(𝐱) = argmax_θ Πi=1:n f(xi|θ)
>
>
>
> Và từ đó, maximum likelihood estimator của θ, như định nghĩa nói trên, là một function của random
> sample: W(𝐗), thì ở đây nó chính là:
>
>
>
> argmax_θ f(𝐗|θ) = argmax_θ Πi=1:n f(Xi|θ)
>
>
>
> Vậy thì ở đây, ta sẽ đi giải bài toán:
>
>
>
> maximize_(μ, σ²) { L[(μ,σ²)|𝐱) }
>
>
>
> = maximize_(μ, σ²) { f(𝐱|μ, σ²) }
>
>
>
> L[(μ,σ²)|𝐱) = f(𝐱|μ, σ²) (kí hiệu như sách là p(𝐱|μ, σ²) nhưng mình cứ dùng kí hiệu
> chuẩn toán học cho dễ)
>
>
>
> = Πi=1:n f(xi|μ, σ²)
>
>
>
> = Πi=1:n (1/σ√2π) exp[-(xi-μ)²/2σ²]
>
>
>
> = (1/σ√2π)ⁿ Πi=1:n exp[-(xi-μ)²/2σ²] (tích n cái cục (1/σ√2π))
>
>
>
> = (1/σ√2π)ⁿ exp[Σi=1:n -(xi-μ)²/2σ²] (e^a * e^b = e^(a+b))
>
>
>
> = (1/σ√2π)ⁿ exp[(1/2σ²) Σi=1:n -(xi-μ)²]
>
>
>
> Tiếp, như đã biết trong Casella, ta luôn nên dùng log để chuyển thành bài toán tối ưu tương đương
> (equivalent), lí do là hàm log monotone increasing, và việc này sẽ khiến tính toán dễ, cũng như
> trong thực tế học máy, sẽ giúp giảm các nguy cơ về lỗi tính toán máy tính
>
>
>
> Nên bài toán tối ưu tương đương cần giải sẽ có objective là:
>
>
>
> log L(𝐱|μ, σ²) = log { (1/σ√2π)ⁿ exp[(1/2σ²) Σi=1:n -(xi-μ)²] }
>
>
>
> = log { (1/σ√2π)ⁿ } + log { exp[(1/2σ²) Σi=1:n -(xi-μ)²] }
>
>
>
> = n log (1/σ√2π) + (1/2σ²) Σi=1:n -(xi-μ)²
>
>
>
> = n log (σ√2π)^-1 + (1/2σ²) Σi=1:n -(xi-μ)²
>
>
>
> = -n log (σ√2π) + (1/2σ²) Σi=1:n -(xi-μ)²
>
>
>
> Đây chỉ là bài toán tối ưu không ràng buộc, ta sẽ dùng Calculus, điều kiện cần tối ưu bậc nhất:
> Gradient hàm objective, đặt là F đi, = **0**:
>
>
>
> ∇F(μ, σ²) = **0**
>
>
>
> ⇔ [∂F(μ, σ²)/∂μ, ∂F(μ, σ²)/∂σ²] = 0
>
>
>
> Tính hai cái partial derivative trước:
>
>
>
> ∂F(μ, σ²)/∂μ
>
>
>
> = ∂/∂μ [-n log (σ√2π) + (1/2σ²) Σi=1:n -(xi-μ)²]
>
>
>
> Tính đạo hàm theo μ thì coi σ² như constant:
>
>
>
> = (1/2σ²) ∂/∂μ [Σi=1:n -(xi-μ)²]
>
>
>
> = (1/2σ²)  [Σi=1:n -∂/∂μ (xi-μ)²]
>
>
>
> = (1/2σ²)  [Σi=1:n -∂/∂(xi-μ) (xi-μ)² . ∂/∂μ (xi-μ)] | chain rule
>
>
>
> = (1/2σ²)  [Σi=1:n -2(xi-μ) . (-1)]
>
>
>
> = (1/2σ²)  [Σi=1:n 2(xi-μ)]
>
>
>
> = (1/σ²)  [Σi=1:n (xi-μ)]
>
>
>
> = (1/σ²)  (Σixi-nμ)
>
>
>
> ∂F(μ, σ²)/∂σ²:
>
>
>
> = ∂/∂σ² [-n log (σ√2π) + (1/2σ²) Σi=1:n -(xi-μ)²]
>
>
>
> = -n ∂/∂σ² [log (σ√2π)] + ∂/∂σ² [(1/2σ²) Σi=1:n -(xi-μ)²]
>
>
>
> = -n ∂/∂σ² [log (√2πσ²)] + [Σi=1:n -(xi-μ)²] ∂/∂σ² (1/2[σ²])
>
>
>
> = -n [∂/∂(√2πσ²) log (√2πσ²) . ∂/∂σ² (√2πσ²)] + (1/2) [Σi=1:n -(xi-μ)²] ∂/∂σ² (1/(σ²)) }
>
>
>
> = -n [1/(√2πσ²) . √2π ∂/∂σ² (σ²)^1/2] + (1/2) [Σi=1:n -(xi-μ)²] (-1/(σ²)²)
>
>
>
> = -n [1/(√2πσ²) . √2π (1/2) (σ²)^-1/2] + (-1/2(σ⁴)) [Σi=1:n -(xi-μ)²]
>
>
>
> = -n [1/2σ . (σ^-1)]  - (1/2σ⁴) [Σi=1:n -(xi-μ)²]
>
>
>
> = -n/2σ²  - (1/2σ⁴) [Σi=1:n -(xi-μ)²]
>
>
>
> Giải hai phương trình:
>
>
>
> ∂F(μ, σ²)/∂μ = 0 ⇔ (1/σ²)  (Σixi-nμ) = 0
>
>
>
> ⇔ (Σixi-nμ) = 0 ⇔ Σixi = nμ ⇔ μ =Σixi/n ⇨ μ = xbar
>
>
>
> ∂F(μ, σ²)/∂σ² = 0 ⇔ -n/2σ²  - (1/2σ⁴) [Σi=1:n -(xi-μ)²] = 0
>
>
>
> Thay μ = xbar
>
>
>
> ⇔ -(1/2σ⁴) n σ² - (1/2σ⁴) [Σi-(xi - xbar)²] = 0
>
>
>
> ⇔ -(1/2σ⁴) [n σ² + Σi-(xi - xbar)²] = 0
>
>
>
> ⇨ n σ² + Σi-(xi - xbar)² = 0
>
>
>
> ⇔ n σ² = Σi(xi - xbar)²
>
>
>
> ⇔ σ² = Σi(xi - xbar)² / n
>
>
>
> Và đây chính là công thức **biased sample variance**: [Σi (Xi - Xbar)²] / n
>
>
>
> vs **unbiased sample variance** S² = [Σi (Xi - Xbar)²] / (n - 1)
>
>
>
> ====
>
>
>
> Dĩ nhiên đây mới chỉ là critical point, nơi đạo hàm vanish
>
>
>
> Để chứng minh nó là maximizer, ta sẽ phải chứng minh Hessian tại (μ^_mle, (σ²)^_mle) xác định
> âm (để tại đó hàm số cong xuống). Và để làm vậy thì việc tính toán rất dài.  Phải chứng minh det
> của Hessian âm. Nên trong sách Casella ở ví dụ 7.2.12 đề cập đến  điều này, trong đó ông cũng ko
> làm việc này, mà chỉ nói sự thật thì kết quả trên chính là normal MLE.
>
>
>
> =====
>
>
>
> Như vậy
>
>
>
> μ_ML(𝐗) = Xbar, sample mean
>
>
>
> (Mình cũng có thể viết Xbar(𝐗), viết vậy để nhớ trong Casella từng nói, Xbar chỉ là viết tắt của
> Xbar(𝐗) vì nó là một hàm của sample 𝐗)
>
>
>
> Giờ mới viết theo notation của Bishop:
>
>
>
> μ_ML = (1/N) Σi=1:N (xi) / N
>
>
>
> (σ²)_ml = [Σi (Xi - Xbar)²] / n
>
>
>
> Viết như Bishop:
>
>
>
> (σ²)_ml = [Σi=1:N (xi - μ_ML)²] / N
>
>
>
> ------
>
>
>
> Khúc cuối gs Bishop đại ý là nói, như ta làm ở trên, chính là maximize likelihood cùng lúc over μ,
> σ² Nhưng trong EE364a, ta biết cái vụ nếu ta có hàm f(x, y), thì có thể maximize over x trước sau
> đó maximize over y: sup_x,y f(x,) = sup_x [sup_y f(x,y)] = sup_y [sup_x f(x,uy)]. Có thể là ông đang 
> nói đến việc ta có thể giải bài toán maximize over μ  trước rồi giải bài toán maximize over σ² sau.

**🔗 See also:** [Ước lượng hợp lí cực đại](./125_curve_fitting_re_visited.md#node-r1gqc9l)

<br>

<a id="node-1g51yok"></a>

###### Sai lệch phương sai MLE

<p align="center"><kbd><img src="assets/ask2cz14tfa.png" width="80%"></kbd></p>

> [!NOTE]
> Đạon này ông nói về việc MLE có những hạn chế. Cụ thể là như mình vừa làm
> xong, μ_ML(𝐗) = Xbar, theo Casella đã biết, gọi là unbiased estimator của
> μ, còn (σ²)_ML(𝐗) = (1/n) Σi (Xi - Xbar)² thì lại là biased estimator của σ².
>
>
>
> Còn nhớ, là vì, ta có đã học khái niệm Bias của một estimator, được định
> nghĩa trong sách Casella là 7.32 là:
>
>
>
> Bias_θ(W(𝐗)) = E[W(𝐗)] - θ,
>
>
>
> để rồi nếu kì vọng E[W(𝐗)] mà  = θ thì gọi là unbiased estimator còn không thì là
> biased estimatoe
>
>
>
> Xem thử μ_ML và σ²_ML có phải là biased estimator không:
>
>
>
> ====
>
>
>
> Nên Bias_μ[Xbar] = E_μ,σ²[Xbar] - μ = E_μ[(ΣiXi)/n] - μ 
>
>
>
> = Σi E_μ,σ² (Xi)/n - μ (linearity)
>
>
>
> = (Σiμ) /n - μ = μ - μ = 0 Do đó **Xbar** là **unbiased** **estimator của μ** 
>
>
>
> ====
>
>
>
> Bias_σ²[(σ²)_ML] = E_μ,σ²[(1/n) Σi (Xi - Xbar)²] - σ²
>
>
>
> Để tính kì vọng của (1/n) Σi (Xi - Xbar)², theo sách Casella, sẽ 
>
>
>
> khai triển Σi (xi - a)² như sau: 
>
>
>
> Σi (xi - a)² = Σi (xi - xbar + xbar - a)² 
>
>
>
> = Σi [(xi - xbar)² + 2(xi - xbar)(xbar - a) + (xbar - a)²]
>
>
>
> =  Σi (xi - xbar)² + 2Σi [(xi - xbar)(xbar - a)] + Σi (xbar - a)²
>
>
>
> =  Σi (xi - xbar)² + 2(xbar - a) Σi [(xi - xbar)] + Σi (xbar - a)²
>
>
>
> =  Σi (xi - xbar)² + 2(xbar - a) [(n xbar - n xbar)] + Σi (xbar - a)²
>
>
>
> =  Σi (xi - xbar)² + 2(xbar - a) * 0 + Σi (xbar - a)²
>
>
>
> =  Σi (xi - xbar)² + Σi (xbar - a)²
>
>
>
> Viết lại: Σi (xi - a)² = Σi (xi - xbar)² + Σi (xbar - a)²
>
>
>
> Từ đây, nếu muốn cái này nhỏ nhất thì a chính là xbar, đó là ý a) của Thereom
> 5.2.4 Casella
>
>
>
> Và áp dụng a = 0, thì ta sẽ có công thức: Σi (xi)² = Σi (xi - xbar)² + Σi (xbar)²
>
>
>
> ⇔ Σi (xi - xbar)² = Σi (xi)² - Σi (xbar)², đây là ý b) của Theorem 5.2.4 Casella.
>
>
>
> Và ta sẽ dùng ý này để làm tiếp.
>
>
>
> Như vậy E[(1/n) Σi (Xi - Xbar)²]
>
>
>
> = E[(1/n) [Σi (Xi)² - Σi (Xbar)²]]
>
>
>
> = (1/n) E[Σi (Xi)² - Σi (Xbar)²] | linearity E[cX] = cEX
>
>
>
> = (1/n) [Σi E(Xi)² - Σi E(Xbar)²] | linearity E[X + Y] = EX + EY (1)
>
>
>
> Tới đây ta cần E(Xi)² và E(Xbar)²
>
>
>
> Xét E(Xi)², ta đã biết công thức hai của VarX = EX² - (EX)² ⇨ EX² = Var(X) + (EX)²
>
>
>
> ⇨ E(Xi)² = Var(Xi) + (EXi)² 
>
>
>
>  = σ² + μ²
>
>
>
> (Dĩ nhiên vì X1,...Xn là các rv ~ normal(μ, σ²) nên EXi chính là μ, VarXi = σ²)
>
>
>
> Tương tự E(Xbar)² = Var(Xbar) + [E(Xbar)]²
>
>
>
> Với Xbar, Casella cho ta theorem 5.2.6:
>
>
>
> EXbar = μ, Var(Xbar) = σ²/n, chứng minh dễ:
>
>
>
> EXbar = E[(Σi Xi) / n] = (Σi EXi) / n = n μ / n = μ 
>
>
>
> Var[Xbar] = E[Xbar - EXbar]² = E[Xbar - μ]² = E[(Σi Xi) / n - μ]²
>
>
>
> = E[(Σi Xi - n μ) / n]²
>
>
>
> = E[Σi (Xi - μ) / n]²
>
>
>
> = (1/n²) E[Σi (Xi - μ)]²
>
>
>
> = (1/n²) Σi Var(Xi)
>
>
>
> = (1/n²) n σ² = σ² / n
>
>
>
> ⇨ E(Xbar)² = Var(Xbar) + [E(Xbar)]²
>
>
>
> = σ² / n + μ²
>
>
>
> Vậy, tiếp tục (1), ta có: 
>
>
>
> (1/n) [Σi E(Xi)² - Σi E(Xbar)²]
>
>
>
> = (1/n) [Σi [σ² + μ²] - Σi [σ² / n + μ²]]
>
>
>
> = (1/n) [nσ² + nμ² - σ² - nμ²]
>
>
>
> = (1/n) [(n - 1)σ² ]
>
>
>
> = [(n - 1)/n]σ² 
>
>
>
> Vậy Bias_σ²[(σ²)_ML] = E_μ,σ²[(1/n) Σi (Xi - Xbar)²] - σ²
>
>
>
> = [(n - 1)/n]σ² - σ², khác 0 nên (**σ²)_ML là biased estimator của σ²**
>
>
>
> Phiên bản unbiased như đã biết, chính là S², sample variance = (1/n-1) Σi (Xi - Xbar)²
> (nếu tính kì vọng sẽ ra đúng bằng σ²)
>
>
>
> ====
>
>
>
> Thành ra gs Bishop nói rằng, **trung bình** mà nói thì **maximum likelihood** sẽ cho ta **giá trị
> đúng của μ** nhưng cho **giá trị underestimate của true variance σ²**.

**🔗 See also:** [Bayesian and Maximum Likelihood Variance](./353_effective_number_of_parameters.md#node-tdezntx)

<br>

<a id="node-wki4nv2"></a>

###### Ước lượng không chệch phương sai

<p align="center"><kbd><img src="assets/u7lm7lp7d7i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/w66oyre84vi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/o106u371tb.png" width="80%"></kbd></p>

> [!NOTE]
> Như vừa nói,  (1/(n-1))Σi (Xi - Xbar), tức sample variance (theo sách Casella) mới là **unbiased estimator cho σ²**
>
>
>
> Gs Bishop cho rằng nếu ta giải bài toán theo Bayesian thì ta sẽ ra kết quả này thay vì kết quả biased vừa rồi.
>
>
>
> Cuối cùng, đại ý cũng dễ hiểu là khi N lớn (số data sample) thì biased này không nghiêm trọng mấy. Nhưng trong sách này ta sẽ phân tích những trường hợp mà biased này có thể tạo ra những sai sót nghiêm trọng
>
>
>
> Ông cũng nói thêm, ta sẽ thấy, biased này có bản chất là hiện tượng **overfit**mà ta đã gặp trong bài toán polynomial fitting.

**🔗 See also:** [Bayesian and Maximum Likelihood Variance](./353_effective_number_of_parameters.md#node-tdezntx)

<br>

