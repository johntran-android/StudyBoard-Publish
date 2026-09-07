# 1.2.6 Bayesian curve fitting

📊 **Progress:** `6` Notes | `7` Screenshots

---
<a id="node-w90ruv4"></a>

<br>

<a id="node-ti0uy3l"></a>

## Xử lý Bayesian đầy đủ

<p align="center"><kbd><img src="assets/y1a88gne7j.png" width="80%"></kbd></p>

> [!NOTE]
> Đây, đây chính là chỗ gs giúp làm rõ cái thắc mắc hồi nãy đây. Lúc nãy mình
> có thắc mắc một điểm: Rõ ràng là trong Casella, khi nói về Bayes estimator
> của θ, ta sẽ đi tìm posterior, rồi lấy mean của nó (hoặc median), và đó mới
> là Bayes estimator: θ^_B(𝐗) = E[θ|𝐗]; θ ~ π(θ|𝐗). Còn khi nãy ta lại đi
> tìm θ khiến maximize π(θ|𝐗) thôi, nên nó chưa phải là Bayes estimator.
>
>
>
> Thì ở đây ông nói đúng vậy, ta chưa thật sự làm theo full Bayesian treatment,
> mà tí nữa sẽ thấy, khi có posteriori thì ta sẽ INTEGRATE over mọi possible
> value của 𝐰. Và cái việc này làm ở trái tim của Bayesian method

<br>

<a id="node-xay851g"></a>

### Phân phối dự đoán Bayes

<p align="center"><kbd><img src="assets/xjrn32psbfd.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, để hiểu phần này, mình sẽ cần ôn lại một kiến thức xác suất gọi là khi
> có joint pdf/pmf của hai random variable X, Y marginalizing over mọi possible
> values của Y, ta sẽ có marginal pmf của X.
>
>
>
> Lấy ví dụ, xét X, Y là hai discrete random variables có possible value {x1,x2. .}
> và {y1,y2....}. Khi đó:
>
>
>
> P(X = x) = Σi P(X = x, Y = yi)
>
>
>
> Dạng tương tự đối với continuous rvs: fX(x) = ∫_{range Y} f(x, y)dy
>
>
>
> Thế thì, tiếp tục dựa trên một theorem: conditional probability theorem:
>
>
>
> f(x, y) = f(x|y)f(y), ta có fX(x) = ∫_{range Y} f(x|y)f(y)dy
>
>
>
> Và ý nghĩa của nó đại khái là ta tổng hợp (marginalizing) mọi khả năng của (giá
> trị) y
>
>
>
> Vậy thì quay lại đây:
>
>
>
> Ta đã có posterior distribution của 𝐰: π(𝐰|𝐱,𝐭) (tương ứng với
> π(θ|𝐱) trong Casella)
>
>
>
> Nhưng, trong Casella, cái ta muốn (suy luận - inference - estimate) là θ, nên ta
> sẽ đi lấy mean để có point estimate cho θ, hoặc maximize posterior, cũng để có
> một point estimate của θ.
>
>
>
> Còn ở đây, trong bối cảnh bài toán curve fitting nói riêng và trong bài toán
> machine  learning nói chung, ta KHÔNG CẦN 𝐰. Cái ta cần là **predictive
> distribution**:
>
>
>
> f(t|x,𝐱,𝐭): tức là, ta chỉ cần tính xác suất của T dựa trên traing data 𝐱, **t
> thôi, không care w**
>
>
>
> Còn nhớ phân phối xác suất của Tn, ta đã assume là sẽ ~ normal(y(xi,𝐰),
> 1/β), có pdf là f(t|x,𝐰,β).
>
>
>
> Vì không cần 𝐰, nên ở đây, ta mới làm một động tác: marginalizing joint pdf
> của T và **W trên mọi possible value của W**. Để từ đó, ta có marginal pdf của T
> thôi:
>
>
>
> f(t) = ∫f(t,𝐰)d𝐰 (cái này tương tự như fX(x) = ∫_range Y f(x,y)dy
>
>
>
> và thay f(t,𝐰) = f(t|𝐰) f(𝐰) (tương tự f(x,y) = f(x|y)f(y))
>
>
>
> ta sẽ có: f(t) = ∫f(t|𝐰)f(𝐰)d𝐰
>
>
>
> Cái khung, cái ý tưởng chính là như vậy, ta marginalizing joint pdf của T và **W
> trên  mọi possible value của W, để có marginal pdf của T.**
>
>
>
> Nhưng để có hình hài đầy đủ của 1.68, ta sẽ hiểu rằng các pdf trên đều
> condition trên cái gì đó:
>
>
>
> ví dụ f(t|𝐰) phải là f(t|x,𝐰,β) vì distribution của Ti ~ normal(y(xi,𝐰), β) nên pdf
> của T cần thêm xi, β nữa. Nhưng vì β coi như đã biết, hoặc ở đây gs nói là ta bỏ
> đi bớt (omit) cho đỡ dài, nên ta chỉ ghi là f(t|x,𝐰) thôi.
>
>
>
> Tương tự f(𝐰) cũng sẽ trở thành f(𝐰|𝐱,𝐭) (hay nên dùng chữ π, vốn
> được quy ước thông thường trong thống kê kí hiệu để chỉ prior và posterior
> distribution π(w|𝐱,𝐭)) ở trên (đúng ra sẽ là π(𝐰|x,t,α) nữa, nhưng cũng
> bỏ bớt α cho đỡ dài.
>
>
>
> f(t|x,**x,t**) = ∫f(t|x,𝐰)π(𝐰|𝐱,𝐭)d𝐰. Đây là công thức 1.68
>
>
>
> -----
>
>
>
> Một ý nhỏ: ở đây ông Bishop nói có thể tìm thấy π(𝐰|𝐱,𝐭) (theo kí hiệu của ổng
> là p(𝐰|𝐱,𝐭)) bằng cách marginalizing vế bên phải của 1.66 là sao?
>
>
>
> → Thì đơn giản là vì: công thức đầy đủ posterior distribution được xây dựng từ
> Bayes theorem: π(θ|𝐱) = f(𝐱|θ)π(θ) / f(𝐱)
>
>
>
> Hay ở đây sẽ là π(𝐰|x,t,α,β) = f(t|x,𝐰,β) π(𝐰|α) / f(t|x)
>
>
>
> Nhưng vì cái mẫu số, chỉ là đóng vai trò normalizing constant, nên người ta
> thường bỏ qua nó, để chuyển thành kí hiệu tỉ lệ thuận.
>
>
>
> Nên nếu muốn có công thức đầy đủ của posterior, thì đừng quên là còn
> cái mẫu số này, mà mẫu số này thì không biết được là bao nhiêu, vì ta ko
> có f(t|x). Tuy nhiên, ta biết nó phải là giá trị c khiến [ ∫f(t|x,𝐰,β) π(𝐰|α) / c] d𝐰 = 1
> ⇨ c = ∫f(t|x,𝐰,β) π(𝐰|α)] d𝐰, đó chính là giá trị của f(t|x).

<br>

<a id="node-6vqfvyl"></a>

#### Phân phối hậu nghiệm Normal

<p align="center"><kbd><img src="assets/sulk7qhxq.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói trong phần sau, ta sẽ thấy posterior (với Prior giả định là Normal thì) hóa ra cũng sẽ là Normal. Cái này thì
> trong ví dụ 7.2.16 sách Casella mình đã làm rồi, với random sample X ~ normal(θ, σ²) và θ được giả định có prior
> distribution θ ~ normal(μ, τ²) thì khi mình xây dựng posterior ta cũng sẽ thấy nó là pdf của normal
>
>
>
> Vậy thì ở đây có thể làm luôn:
>
>
>
> π(𝐰|𝐱,𝐭), như phần trước đã biết, hay lúc nãy đã nhắc lại ∝ f(𝐭|𝐱,𝐰)π(𝐰|α)
>
>
>
> ∝ [Πi=1:n N(ti| y(xi, 𝐰), 1/β)] . [α/(2π)^(M+1)/2] exp {-(α/2)𝐰ᵀ𝐰}
>
>
>
> Xét N(t|y(x,𝐰), 1/β).
>
>
>
> y(x, 𝐰) = w0x^0 + w1x^1 + ...wmx^M = w0 + w1x^1 + ...wmx^M
>
>
>
> Như phần trước mình cũng đã làm, để thể hiện cái này ở dạng compact ta sẽ:
>
>
>
> Đặt Φ(x) là scalar → vector function: nhận vào scalar x, trả ra vector [1, x, x²,..,x^M]
>
>
>
> Khi đó với việc w đã biết là vector [w0,...wM] thì y(x, 𝐰) có thể thể hiện ở dạng vectorization: 𝐰ᵀΦ(x).
>
>
>
> N(t|y(x,𝐰), 1/β) = N(t|𝐰ᵀΦ(x), 1/β)
>
>
>
> = {1/√[2π(1/β)]} exp[-(t-𝐰ᵀΦ(x))²/2(1/β)]
>
>
>
> = {1/√[2π(1/β)]} exp[-(t-𝐰ᵀΦ(x))²/2(1/β)]
>
>
>
> Ráp vô:
>
>
>
> π(𝐰|𝐱,𝐭) ∝ {Πi=1:n {1/√[2π(1/β)]} exp[-(ti-𝐰ᵀΦ(xi))²/2(1/β)] } . { [α/(2π)^(M+1)/2] exp {-(α/2)𝐰ᵀ𝐰} }
>
>
>
> ∝ {1/√[2π(1/β)]}ⁿ [α/(2π)^(M+1)/2]  exp[-Σi (ti-𝐰ᵀΦ(xi))²/2(1/β)] . exp {-(α/2)𝐰ᵀ𝐰} }
>
>
>
> ∝ exp[-Σi (ti-𝐰ᵀΦ(xi))²/2(1/β) - (α/2)𝐰ᵀ𝐰]
>
>
>
> ∝ exp[-(β/2) Σi (ti-𝐰ᵀΦ(xi))² - (α/2)𝐰ᵀ𝐰]
>
>
>
> Xét phần bên trong exp[..]:
>
>
>
> -(β/2) Σi [(ti-𝐰ᵀΦ(xi))²] - (α/2)𝐰ᵀ𝐰
>
>
>
> Đặt 𝐗 là matrix mà hàng i là Φ(xi)ᵀ
>
>
>
> .. = -(β/2) ||(𝐭-**Xw**)||² - (α/2)𝐰ᵀ𝐰
>
>
>
> = -(β/2) (𝐭-**Xw**)ᵀ(𝐭-**Xw**) - (α/2)𝐰ᵀ𝐰
>
>
>
> = -(β/2) (𝐭ᵀ-𝐰ᵀ𝐗ᵀ)(𝐭-**Xw**) - (α/2)𝐰ᵀ𝐰
>
>
>
> = -(β/2) (𝐭ᵀ𝐭-𝐰ᵀ𝐗ᵀ𝐭-𝐭ᵀ**Xw**+𝐰ᵀ𝐗ᵀ**Xw**) - (α/2)𝐰ᵀ𝐰
>
>
>
> = -(β/2) (𝐭ᵀ𝐭 - 2𝐭ᵀ**Xw** + 𝐰ᵀ𝐗ᵀ**Xw**) - (α/2)𝐰ᵀ𝐰
>
>
>
> = -(1/2) (β𝐭ᵀ𝐭 - 2β𝐭ᵀ**Xw** + β𝐰ᵀ𝐗ᵀ**Xw** + α𝐰ᵀ𝐰)
>
>
>
> = -(1/2) (𝐰ᵀ(β𝐗ᵀ𝐗 + **α**I)𝐰 - 2β𝐭ᵀ**Xw** + β𝐭ᵀ𝐭)
>
>
>
> Như vậy bên trong exp(..) của posterior là hàm bậc hai theo 𝐰, điều này cho thấy posterior là Normal, để xác
> định được mean và covariance matrix, ta chỉ việc khớp nó với công thức multivariate Gaussian pdf nói bữa trước.
>
>
>
> Xét phần bên trong exp của multivariate Gaussian pdf: -(1/2)(𝐱 - **μ**)ᵀ Σ⁻¹ (𝐱 - **μ**)
>
>
>
> = -(1/2)(𝐱ᵀ Σ⁻¹ - **μ**ᵀ Σ⁻¹) (𝐱 - **μ**)
>
>
>
> = -(1/2)(𝐱ᵀ Σ⁻¹ 𝐱 - **μ**ᵀ Σ⁻¹ 𝐱 - 𝐱ᵀ Σ⁻¹ **μ** + **μ**ᵀ Σ⁻¹ **μ**)
>
>
>
> = -(1/2)(𝐱ᵀ Σ⁻¹ 𝐱 - 2 **μ**ᵀ Σ⁻¹ 𝐱 + **μ**ᵀ Σ⁻¹ **μ**)
>
>
>
> Tiến hành khớp pattern:
>
>
>
> β𝐗ᵀ𝐗 + α𝐈 = **Σ⁻¹** → Covariance matrix là (β𝐗ᵀ𝐗 + αI)⁻¹
>
>
>
> β𝐭ᵀ𝐗 = **μ**ᵀ Σ⁻¹ = **μ**ᵀ (β𝐗ᵀ𝐗 + α𝐈)
>
>
>
> ⇔ β𝐭ᵀ𝐗(β𝐗ᵀ𝐗 + αI)⁻¹ = **μ**ᵀ **Σ⁻¹** = **μ**ᵀ
>
>
>
> ⇔ [β𝐭ᵀ𝐗(β𝐗ᵀ𝐗 + α𝐈)⁻¹]ᵀ = **μ** 
>
>
>
> ⇔ **μ** = [(β𝐗ᵀ𝐗 + α𝐈)⁻¹]ᵀ(β𝐭ᵀ𝐗)ᵀ
>
>
>
> = (β𝐗ᵀ𝐗 - α𝐈)⁻¹(β𝐗ᵀ**t)**
>
>
>
> Posterior π(𝐰|𝐱,𝐭) là Normal((β𝐗ᵀ𝐗 + α𝐈)⁻¹β𝐗ᵀ𝐭,  (β𝐗ᵀ𝐗 + α𝐈)⁻¹)

**🔗 See also:** [Phân phối chung và Likelihood](./125_curve_fitting_re_visited.md#node-8u1p4w9)

<br>

<a id="node-ug53f6v"></a>

##### Đạo hàm phân phối dự đoán Bayesian

<p align="center"><kbd><img src="assets/nevoswj1xjc.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự, theo gs Bishop, ta có thể g**iải cái tích phân 1.68** (analytically tạm hiểu là có thể giải ra kết
> quả ở dạng closed form)
>
>
>
> Nhưng thật ra ta **có thể làm cách khác,** dựa trên lập luận sau.
>
>
>
> Cái ta đang muốn tìm là distribution của Ti không phụ thuộc 𝐖. Bằng cách  marginalizing joint pdf
> của Ti, 𝐖 (bản chất của cái tích phân 1.68 là vậy)
>
>
>
> Từ đầu đến giờ gs Bishop đang dùng một assumption: Ti ~ normal(y(xi,𝐰), 1/β)
>
>
>
> và ta đã từng nhận ra, điều này đồng nghĩa Ti - y(xi, 𝐰), chính là sai số của dự đoán, chính là một
> rv ~ Normal(0, 1/β) (do location scale theorem)
>
>
>
> Rồi, đó, là vẫn trong bối cảnh ta dùng trường phái cổ điển (Frequentist), để rồi coi 𝐰 như fixed và
> unknown.
>
>
>
> Sau đó, khi trong bối cảnh hiện tại, ta dùng trường phái Bayesian, thì **w lúc này được đối xử như
> random variable W** có distribution prior và posterior như đã thấy.
>
>
>
> Như vậy, lúc này ta có Zi = Ti - y(xi,𝐖) ~ normal(0, 1/β).
>
>
>
> À như vậy ta có Ti = Zi + y(xi, 𝐖),
>
>
>
> Ti là tổng của một normal(0, 1/β) với y(xi, 𝐖), lúc này (theo trường phái Bayesian) đã cũng là một
> random variable khác (được tạo bởi hàm y áp lên random variables 𝐖) có dạng cụ thể là
> 𝐖ᵀΦ(xi) (hay Φ(x)ᵀ𝐖 đều được vì nó là một scalar)
>
>
>
> Rồi, WᵀΦ(xi) dĩ nhiên có bản chất là linear combination của các phần tử của W bởi hệ số là các phần
> tử của Φ(xi):
>
>
>
> [1 * x^0 + W1 * x^1 + W2 * x² + ....WM * x^M]
>
>
>
> Mà W1,..WM là các random variable có distribution gì?
>
>
>
> Như vừa mới làm xong, W là random vector, có posterior distribution là multivariate
> Normal((β𝐗ᵀ𝐗 + α𝐈)⁻¹β𝐗ᵀ𝐭,  (β𝐗ᵀ𝐗 + α𝐈)⁻¹)
>
>
>
> Thì, đương nhiên các random variable W1,...WM cũng là những normal mà mean và variance của
> chúng sẽ là:
>
>
>
> EWi = [(β𝐗ᵀ𝐗 + α𝐈)⁻¹β𝐗ᵀ𝐭]_i, tức là phần tử thứ i của vector
>
>
>
> VarWi = (β𝐗ᵀ𝐗 + α𝐈)⁻¹)_ii, tức là entries thứ i trên đường chéo của covariance matrix
>
>
>
> --------------------
>
>
>
> Đến đây mới dùng một kiến thức trong Stat110 và Casella đã học: Tổng các normal sẽ là normal. Hay
> **linear combination các normal cũng là normal** (vì scale một normal rv với α dĩ nhiên cũng ra normal (do
> location scalar theorem)
>
>
>
> Như vậy [1 * x^0 + W1 * x^1 + W2 * x² + ....WM * x^M] sẽ là một normal:
>
>
>
> W1 * x^1 + W2 * x² + ....WM * x^M là normal, cộng với 1 *x^0 thì kết quả cũng là normal có location
> khác đi bởi 1.
>
>
>
> Vậy tóm lại, Φ(xi)ᵀ𝐖 là một normal random variable
>
>
>
> Thử xem mean và variance của nó:
>
>
>
> Mean: Dùng tính linearity của kì vọng thôi:
>
>
>
> E[Φ(xi)ᵀ𝐖]  = E[1 * x^0 + W1 * x^1 + W2 * x² + ....WM * x^M]
>
>
>
> = 1 + x^1 EW1 + x² EW2 + ..x^M EWM
>
>
>
> mà cũng chả cần làm kiểu này, cứ để dạng compact:
>
>
>
> E[Φ(xi)ᵀ𝐖] = Φ(xi)ᵀE[𝐖]
>
>
>
> Thay mean của posterior distribution của 𝐖 vào
>
>
>
> = Φ(xi) (β𝐗ᵀ𝐗 + αI)⁻¹β𝐗ᵀt
>
>
>
> Variance: Var[𝐖ᵀΦ(xi)]. Tí nữa quay lại cái này.
>
>
>
> Như vậy 𝐖ᵀΦ(xi) ~ normal(Φ(xi) (β𝐗ᵀ𝐗 + α𝐈)⁻¹β𝐗ᵀ𝐭, Var[𝐖ᵀΦ(xi)])
>
>
>
> --------------------
>
>
>
> Do đó, quay lại Ti = 𝐖ᵀΦ(xi) + Zi, thì cũng lại thấy Ti là tổng của hai normal.
>
>
>
> Suy ra Ti cũng là normal.
>
>
>
> Và again, chỉ việc dùng linearity để tính mean và variance:
>
>
>
> ETi = E[𝐖ᵀΦ(xi) + Zi] = E[𝐖ᵀΦ(xi)] + EZi
>
>
>
> = E[Φ(xi)ᵀW] + EZi
>
>
>
> = Φ(xi)ᵀ E𝐖 + 0
>
>
>
> =  Φ(xi)ᵀ [(β𝐗ᵀ𝐗 + α𝐈)⁻¹β𝐗ᵀ𝐭] + 0
>
>
>
> = Φ(xi)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ β𝐗ᵀ𝐭
>
>
>
> = βΦ(xi)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ 𝐗ᵀ𝐭
>
>
>
> Đây thật ra **chính là công thức của 1.70** m(x) **trong sách Bishop**.
>
>
>
> Trong sách, m(x) = βΦ(x)ᵀ 𝐒 Σn Φ(xn) tn
>
>
>
> với 𝐒inv = α𝐈 + β Σi Φ(xn) Φ(xn)ᵀ (gs Bishop viết thiếu chữ n trong Φ(x) cuối cùng, phải là Φ(xn))
>
>
>
> Phân tích: Σi=1:N Φ(xn) Φ(xn)ᵀ là tổng các outer product tại bởi Φ(xn) với Φ(xn).
>
>
>
> Cái này chính là 𝐗ᵀ**X như công thức của mình**, vì sao? 
>
>
>
> → Vì theo công thức của mình, mình đã đặt 𝐗 là matrix mà hàng thứ i là Φ(xi). 
>
>
>
> Nên 𝐗ᵀ**X,** theo góc nhìn nhân matrix vs matrix thứ 4 của thầy Strang: 
>
>
>
> Khi nhân A với B, nó là một tổng các rank 1 matrix tạo bởi outer product của một cột của A và một hàng
> của B. 
>
>
>
> Do đó 𝐗ᵀ𝐗 sẽ là Σi=1:N ([𝐗ᵀ]_cột i) (𝐗_hàng i)ᵀ, 
>
>
>
> và đây chính là Σi=1:N Φ(xi)Φ(xi)ᵀVậy nên 𝐒inv thật ra chính là β𝐗ᵀ𝐗 + αI, hay 𝐒 chính là (β𝐗ᵀ𝐗 + α𝐈)⁻¹.
>
>
>
> Vậy m(x) trong sách sẽ là βΦ(x)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ Σn Φ(xn) tn
>
>
>
> Còn cái đuôi Σn Φ(xn) tn, chính là 𝐗ᵀ𝐭 vì sao? Vì 𝐗 là matrix có các hàng là Φ(xn) thì 𝐗ᵀ là
> matrix có các cột là Φ(xn) ⇨ 𝐗ᵀ𝐭 theo góc nhìn 18.06, là **linear combination** các cột Φ(xn) của
> 𝐗ᵀ, với bộ hệ số là các phần tử của vector 𝐭: Σn Φ(xn) tn
>
>
>
> Vậy cho thấy βΦ(xi)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ 𝐗ᵀ𝐭 **đích thị là dạng compact của công thức 1.70**
>
>
>
> --------------------
>
>
>
> Còn cái Variance? Quay lại cái còn để ngỏ. Var[𝐖ᵀΦ(x)]
>
>
>
> W có covariance matrix (β𝐗ᵀ𝐗 + α𝐈)⁻¹ thì Variance của 𝐖ᵀu:
>
>
>
> = Var(𝐗ᵀc)= Var(c1X1 + c2X2 + ...cnXn)
>
>
>
> Công thức Var(X + Y) = VarX + VarY + 2Cov(X,Y)
>
>
>
> ⇨ Var(c1X1 + c2X2 + ...cnXn) 
>
>
>
> = Var(c1X1) + Var(c2X2) + ..Var(cnXn) + 2Cov(c1X1,c2X2) + 2Cov(c1X1,c3X3),,,
>
>
>
> = c1²Var(X1) + c2²Var(X2) + ..
>
>
>
> Và đây chính là cᵀCov(𝐗, 𝐗)c
>
>
>
> ⇨ Var[𝐖ᵀΦ(x)] = Φ(x)ᵀ Cov(𝐖,𝐖) Φ(x)
>
>
>
> = Φ(x)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ Φ(x)
>
>
>
> Và Ti = 𝐖ᵀΦ(xi) + Zi
>
>
>
> ⇨ Var(Ti) = Var[𝐖ᵀΦ(xi) + Zi] = Var[𝐖ᵀΦ(xi)] + Var[Zi] + 2Cov(𝐖ᵀΦ(xi), Zi)
>
>
>
> Cov(WᵀΦ(xi), Zi) = 0 do 𝐖ᵀΦ(xi) và Zi **độc lập**. Vì sao?
>
>
>
> Vì ta phải tự hiểu **đây là một assumption hiển nhiên**: Noise Z độc lập với tham số 𝐖
>
>
>
> ⇨ Var(Ti) = Var[𝐖ᵀΦ(xi)] + Var[Zi]
>
>
>
> = Φ(x)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ Φ(x) + 1/β 
>
>
>
> Và với việc mình đã chỉ ra S "của gs Bishop" chính là (β𝐗ᵀ𝐗 + α𝐈)⁻¹ "của mình"
>
>
>
> thì đây **chính là công thức s²(x) 1.71** trong sách.

<br>

<a id="node-ejt1ih6"></a>

###### Thành phần phương sai dự đoán

<p align="center"><kbd><img src="assets/dq2q72ju7ml.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là, khi nhìn vào variance của Ti ~ predictive distribution là normal(mean
> = βΦ(xi)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ 𝐗ᵀ𝐭, Variance = Φ(x)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ Φ(x) + 1/β
>
>
>
> Thì đại khái là, có 2 yếu tố / cấu phần: 1/β và Φ(x)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ Φ(x)
>
>
>
> Cấu phần thứ nhất 1/β, dĩ nhiên đến từ việc ta cho rằng sai số của dự đoán
> Ti - y(xi, 𝐰) là biến tuân theo Normal(0, 1/β)
>
>
>
> Thì cái này, đại ý là cũng tương tự như trong kết quả khi ta giải bài toán 
> maximum likelihood để tìm ML estimator của w và β: w_ML và β_ML 
>
>
>
> (1/β_ml = (1/n) Σi [ti-y(xi, w_ML)]²)
>
>
>
> Cái chính muốn nói, là, cái cấu phần thứ hai là kết quả đến từ việc ta tiếp
> cận theo Bayesian, để rồi coi 𝐰 như random variable 𝐖) nên kiểu như điều
> này khiến  **PHÁT SINH THÊM MỘT YẾU TỐ UNCERTAINTY NỮA**  (yếu tố
> uncertainty **do coi w là random variable**), và cái cấu phần thứ hai trong
> variance của Ti phản ánh điều này, quả thật, nó là một term liên quan đến
> covariance variance của posterior distribution của 𝐖

**🔗 See also:** [Ước lượng ML, Phân phối tiên đoán](./125_curve_fitting_re_visited.md#node-iw7c6u7)

<br>

<a id="node-enjiwzp"></a>

###### Phân phối dự đoán

<p align="center"><kbd><img src="assets/l92qod0f5fb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/duzgnl34vl.png" width="80%"></kbd></p>

> [!NOTE]
> hình ảnh minh họa predictive distribution.
>
>
>
> Đường màu đỏ chính là mean.
>
>
>
> Dĩ nhiên với x khác nhau ta sẽ có các normal(mean = βΦ(xi)ᵀ (βXᵀX +
> αI)⁻¹ Xᵀt, Variance = Φ(x)ᵀ (βXᵀX + αI)⁻¹ Φ(x) + 1/β) khác nhau
>
>
>
> thì tại một x = xn nào đó, ta sẽ có phân phối của Tn ~normal(mean = βΦ(xn)ᵀ (β𝐗ᵀ𝐗 +
> αI)⁻¹ 𝐗ᵀ𝐭, Variance = Φ(xn)ᵀ (β𝐗ᵀ𝐗 + α𝐈)⁻¹ Φ(xn) + 1/β)

<br>

