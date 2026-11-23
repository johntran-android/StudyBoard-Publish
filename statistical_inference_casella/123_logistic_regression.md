# 12.3 Logistic Regression

📊 **Progress:** `6` Notes | `8` Screenshots | `6` AI Reviews

---
<a id="node-holzhx7"></a>

<br>

<a id="node-idv2zz5"></a>

## Section 12.3 Logistic Regression

<p align="center"><kbd><img src="assets/lat8kn7q8o9.png" width="80%"></kbd></p>

> [!NOTE]
> Trước tiên có thể ôn lại conditional normal model đã gặp ở 11.3.3. Đó là mô hình trong trong đó ta giả định dữ liệu (x1,y1), (x2,y2) ... sinh ra từ mô hình sau:
>
>
>
> x1,x2,....là các giá trị đã biết trước
>
>
>
> y1,y2,...là gía trị quan sát được của các random variable Y1, Y2,....độc lập. Và Yi \~ n(α + βxi, σ²)
>
>
>
> hoặc y1,y2....là giá trị quan sát được của Y1,Y2,...trong đó: Yi = α + βxi + εi với εi iid \~ n(0, σ²)
>
>
>
> Như vậy, có thể thấy, mô hình này giả định rằng mean của Y, tức E\[Y|x\] (gọi là regression population mean) là hàm tuyến tính đối với x với tham số α và β.
>
>
>
> Thế thì ở đây tác giả cho biết, conditional normal model chỉ là một ví dụ của cái gọi là mô hình tuyến tính tổng quát (generalized linear model). Được định nghĩa là: mô tả quan hệ giữa mean của response variable Y và independent variable x. Mà quan hệ này có thể phức tạp hơn nhiều so với conditional normal model. Và phần này ta sẽ tập trung vào một trong các mô hình GLM này, logistic regression.
>
>
>
> Khái niệm GLM trong chương 4 Bishop có nói đến, nhưng ở đây mình sẽ được học nó ở mức độ sâu hơn

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất tốt, tái hiện chính xác kiến thức nền tảng về conditional normal model và nắm bắt đúng tinh thần giới thiệu về GLM của giáo trình.
>
> **✓ Strengths**
> - Tái hiện chính xác và đầy đủ hai cách biểu diễn tương đương của conditional normal model (dạng phân phối điều kiện và dạng nhiễu Gauss cộng tính).
> - Hiểu đúng bản chất GLM là mở rộng mối quan hệ giữa kỳ vọng của biến mục tiêu E[Y|x] và biến độc lập x thay vì chỉ bó hẹp ở hàm tuyến tính trực tiếp.
>
> **💡 Deeper notes**
> - Về mặt toán học chuẩn của GLM, mối quan hệ phức tạp hơn này thường được mô hình hóa thông qua một hàm liên kết (link function) $g(\mu) = \alpha + \beta x$ với $\mu = E[Y|x]$, và phân phối của $Y|x$ thuộc họ hàm mũ (exponential dispersion family).

<br>

<a id="node-64gqvcq"></a>

### 12.3.1 The Model

<p align="center"><kbd><img src="assets/l0qtifn4abh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3gpo2o4ie4v.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái đoạn này mô tả một mô hình tuyến tính tổng quát (GLM): Gồm 3 thành phần (component):
>
>
>
> 1. Random component (tạm hiểu là cấu phần chứa tính chất ngẫu nhiên): Đó chính là các response variable Y1,..Yn. Giả định đặt ra là đây là những random variable độc lập, có chung dạng phân phối thuộc họ exponential nào đó như Poisson, normal, nhưng khác tham số, nên không identically distributed.
>
>
>
> 2. Systematic component: Chính là cái hàm số áp lên x trong quan hệ giữa E\[Y|x\] và x, ví dụ trong conditional normal model, hàm số này là α + βx
>
>
>
> 3. Link function g(μ), tạm hiểu là hàm số áp lên μ (hay E\[Y|x\]) trong quan hệ giữa E\[Y|x\] và x.
>
>
>
> Trong conditional normal model, g(μ) = μ, gọi là identity link function. Thành ra kết hợp với 2), quan hệ giữa Y và x thể hiện bởi:
>
>
>
> g(E\[Y|x\]) = E\[Y|x\] = α + βx

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=Ti80vUWcbrA)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác và mạch lạc cấu trúc 3 thành phần của GLM cùng ví dụ về mô hình hồi quy chuẩn có identity link.
>
> **✓ Strengths**
> - Hiểu đúng và giải thích rõ bản chất vì sao các biến phản hồi độc lập nhưng không cùng phân phối (cùng họ nhưng khác tham số do phụ thuộc vào x).
> - Áp dụng chính xác ví dụ hồi quy chuẩn có hàm liên kết đồng nhất (identity link) để minh họa mối liên hệ giữa ba thành phần.
>
> **💡 Deeper notes**
> - Về mặt thuật ngữ chuẩn, systematic component (thành phần hệ thống) thường được gọi là linear predictor (bộ dự báo tuyến tính), có đặc trưng cốt lõi là phải 'tuyến tính theo các tham số' (linear in parameters, ví dụ α + βx), thay vì chỉ là một hàm bất kỳ của x.

<br>

<a id="node-2jk3h1m"></a>

#### Logistic Regression as GLM

<p align="center"><kbd><img src="assets/h2abxjr6pl8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/lgy915o9fjd.png" width="80%"></kbd></p>

> [!NOTE]
> Nói sang mô hình logistic regression: Trong mô hình này, random component, các random variable Y1,Y2 ...là các biến ngẫu nhiên có phân phối Yi \~ Bern(πi).
>
>
>
> Trong đó πi sẽ được giả định là quan hệ với xi bởi:
>
>
>
> log(πi/(1-πi)) = α + βxi
>
>
>
> như vậy mô hình này giả định log-odds là hàm tuyến tính của x.
>
>
>
> Còn nhớ trong Bishop chương 4, cũng đã học về logistic regression, nhưng thể hiện khác chút xíu: Đó là mô hình này giả định các giá trị của y1,y2,...là giá trị quan sát của Y1,Y2,....với Yi \~ Bern(πi) với:
>
>
>
> P(Yi=1) = σ(α + βxi)
>
>
>
> thì thật ra (1) log(πi/(1-πi)) = α + βxi và (2) P(Yi=1) = πi = σ(α + βxi) cũng là một thôi:
>
>
>
> (1) log(πi/(1-πi)) = α + βxi
>
>
>
> ⇔ πi/(1-πi) = exp(α + βxi)
>
>
>
> ⇔ (1-πi)/πi = 1/exp(α + βxi)
>
>
>
> ⇔ 1/πi - 1 = 1/exp(α + βxi)
>
>
>
> ⇔ 1/πi = 1 + 1/exp(α + βxi)
>
>
>
> ⇔ 1/πi = \[exp(α + βxi) + 1\]/exp(α + βxi)
>
>
>
> ⇔ πi = exp(α + βxi)/\[exp(α + βxi) + 1\] = σ(α + βxi) ⇒ chính là (2)
>
>
>
> ---
>
>
>
> Và đây là một ví dụ của GLM, bằng cách phân tích như sau:
>
>
>
> i) ta sẽ chỉ ra rằng Bernouilly là một phân phối thuộc exponential family
>
>
>
> P(Yi = y) (pmf của Yi tại y) = (πi^y)\[(1-πi)^(1-y)\]
>
>
>
> = exp\[log(πi^y)\] exp \[log (1-πi)^(1-y)\]
>
>
>
> = exp\[log(πi^y) + log (1-πi)^(1-y)\]
>
>
>
>  = exp\[y log(πi) + (1-y) log (1-πi)\]
>
>
>
>  = exp\[y log(πi) + log (1-πi) - y log (1-πi)\]
>
>
>
>  = exp(log (1-πi)) exp\[y log(πi) - y log (1-πi)\]
>
>
>
>  = (1-πi) exp\[y(log(πi) - log (1-πi))\]
>
>
>
>  = (1-πi) exp\[y log(πi/(1-πi))\]
>
>
>
> Như vậy, pmf của Bern(πi) có dạng:
>
>
>
> f(x|𝛉) = h(x) c(𝛉) exp(Σi wi(𝛉)ti(x))
>
>
>
> với h(y) = 1, c(𝛉) = 1-πi, exp(Σi wi(𝛉)ti(x)) chính là exp\[y log(πi/(1-πi))\].
>
>
>
> Điều này cũng đồng nghĩa tham số của Bern(πi) dưới góc độ exponential family là log(πi/(1-πi), tức logit, hay log odds.
>
>
>
> ii) Theo mô tả của GLM, thì systematic và link function là gì?
>
>
>
> Ta có giả định của logistic regression model là: log(πi/(1-πi)) = α + βxi
>
>
>
> nên theo đó, systematic component chính là α + βxi
>
>
>
> và link function là log(πi/(1-πi))
>
>
>
> và vì đại khái là link function trong trường hợp này là chính là cái hàm h(πi) sao cho h(πi) cho ta cái tham số của exponential family, nên người ta gọi là canonical link (chính tắc)
>
>
>
> ---
>
>
>
> Còn conditional normal model?
>
>
>
> Conditional normal model giả định y1, y2, ...là giá trị quan sát được của Y1,Y2,..độc lập.Yi \~ n(α + βxi, σ²)
>
>
>
> Cũng có nghĩa là E\[Y|xi\] = α + βxi
>
>
>
> Chiếu theo GLM:
>
>
>
> Random component là Y1,Y2,...\~ n(α + βxi, σ²), là một exponential family:
>
>
>
> f(y|μ, σ²) = 1/√2πσ² exp(-(y-μ)²/2σ²)
>
>
>
> = 1/√2πσ² exp(-(y²-2yμ+μ²)/2σ²)
>
>
>
> = 1/√2πσ² exp(-y²/2σ²+2yμ/2σ²-μ²/2σ²)
>
>
>
> = 1/√2πσ² exp(-y²/2σ²+2yμ/2σ²)exp(-μ²/2σ²)
>
>
>
> = 1 × 1/√2πσ² exp(-μ²/2σ²) exp(-y²/2σ²+yμ/σ²)
>
>
>
> Theo công thức của exponential family:
>
>
>
> f(y|𝛉) = h(y) c(𝛉) exp(Σi wi(𝛉)ti(y))
>
>
>
> thì h(y) = 1
>
>
>
> c(𝛉) = 1/√2πσ² exp(-μ²/2σ²)
>
>
>
> Σi wi(𝛉)ti(y) chính là -y²/2σ²+yμ/σ²
>
>
>
> với w1(𝛉) = 1/σ², t1(y) = -y²/2
>
>
>
> w2(𝛉) = μ/σ², t2(y) = y
>
>
>
> Và systematic component là: α + βxi
>
>
>
> và link function là identity h(E\[Y|xi\]) = E\[Y|xi\]

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, hiểu sâu bản chất GLM khi tự liên hệ đối chiếu giữa cách biểu diễn logit và sigmoid (Bishop), tự biến đổi dạng họ hàm mũ (exponential family) và mở rộng chính xác sang mô hình hồi quy tuyến tính chuẩn (conditional normal model).
>
> **✓ Strengths**
> - Biến đổi đại số chính xác và chi tiết để chứng minh tương đương giữa logit link và hàm sigmoid trong Bishop.
> - Chứng minh chặt chẽ phân phối Bernoulli thuộc họ hàm mũ và chỉ ra chính xác natural parameter (canonical link).
> - Mở rộng tốt tư duy GLM sang mô hình Conditional Normal (phân phối chuẩn với identity link).
>
> **💡 Deeper notes**
> - Về mặt chặt chẽ trong họ hàm mũ, hàm cơ sở h(y) thường mang theo hàm chỉ thị tập giá trị (support) I_{0, 1}(y) đối với phân phối Bernoulli.
> - Trong GLM đối với phân phối chuẩn N(μ, σ²), σ² thường được coi là tham số phân tán (dispersion parameter φ). Khi đó natural parameter là θ = μ, và hàm liên kết chính tắc (canonical link) g(μ) = μ là hàm đồng nhất (identity link).

<br>

<a id="node-yvpngir"></a>

##### Logistic Regression Derivative and Symmetry

<p align="center"><kbd><img src="assets/s0ali1c4u1.png" width="80%"></kbd></p>

> [!NOTE]
> π(x) = exp(α + βx) / \[1 + exp(α + βx)\]
>
>
>
> Đại khái là có thể thấy π(x) &gt; 0 (do exp(..) &gt; 0 nên tử số và mẫu số đều dương) và tử số bé hơn mẫu số nên cái này cũng &lt; 1.
>
>
>
> Như vậy có vẻ nó là một công thức hợp lí, vì π(x), là P(Y=1) (nên π(x) là một giá trị xác suất)
>
>
>
> ---
>
>
>
> Tiếp, thử lấy đạo hàm hàm π(x) đối với x:
>
>
>
> π(x) = exp(α + βx) / \[1 + exp(α + βx)\]
>
>
>
> π(u,v) = u / v
>
>
>
> dπ = (du v - u dv)/v²
>
>
>
> u = exp(z) ⇒ du = exp(z) dz = u dz
>
>
>
> v = 1 + exp(z) ⇒ dv = exp(z) dz = u dz
>
>
>
> π = u/(1 + u) ⇒ 1 - π = 1 - u/(1 + u) = 1/(1 + u)
>
>
>
> z = α + βx ⇒ dz = β dx
>
>
>
> vậy dπ = (du v - u dv)/v²
>
>
>
> = (u dz v - u u dz)/v²
>
>
>
> = (uv - u²)dz/v²
>
>
>
> = (u(1+u) - u²)dz/(1+u)²
>
>
>
> = (u + u² - u²)dz/(1+u)²
>
>
>
> = \[u/(1+u)²\]dz
>
>
>
> = π/(1+u)dz
>
>
>
> = π(1-π)dz
>
>
>
> = π(1-π)βdx
>
>
>
> Vẫy dπ = π(1-π)βdx ⇒ dπ/dx = βπ(x)(1-π(x))
>
>
>
> ---
>
>
>
> Khi đó, có thể thấy nếu β dương, âm, =0, thì dπ/dx dương, âm, = 0, tương ứng hàm π(x) strictly increasing / strictly decreasing / là hàm hằng theo x (cụ thể = exp(α) / \[1 + exp(α)\])
>
>
>
> ---
>
>
>
> Thêm nữa:
>
>
>
> π(-α/β) = exp(α + β(-α/β)) / \[1 + exp(α + β(-α/β))\]
>
>
>
> = exp(0)/(1+exp(0))
>
>
>
> = 1/2, cái này dễ thấy
>
>
>
> ---
>
>
>
> π(c-α/β) + π(-c-α/β) = 1

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, tự diễn giải chi tiết từng bước đạo hàm và các tính chất đối xứng, đơn điệu của hàm hồi quy logistic một cách chính xác.
>
> **✓ Strengths**
> - Tự thực hiện đầy đủ và chính xác từng bước biến đổi đạo hàm dπ/dx bằng quy tắc đạo hàm phân thức.
> - Hiểu rõ và giải thích trực giác tốt miền giá trị 0 < π(x) < 1 dựa trên tính chất của hàm mũ.
> - Nắm vững tính đơn điệu của hàm theo dấu của hệ số β và tính chất đối xứng tâm quanh điểm x = -α/β.
>
> **💡 Deeper notes**
> - Điểm đối xứng x = -α/β chỉ xác định khi β ≠ 0; nếu β = 0 thì đồ thị là đường nằm ngang π(x) = exp(α)/(1 + exp(α)).
> - Mô hình logistic không bao giờ đạt giá trị chính xác 0 hoặc 1 với x hữu hạn (chỉ tiệm cận khi x tiến ra vô cực).

<br>

<a id="node-yj423vu"></a>

###### Logistic Regression Parameter Interpretation

<p align="center"><kbd><img src="assets/c534st5bxbs.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là đoạn này phân tích ý nghĩa của α, β.
>
>
>
> Nhắc lại giả định của logistic regression:
>
>
>
> y1,y2,...là các observed value của Y1,Y2,....độc lập có: Yn \~ Bern(π(xi)) với
>
>
>
> π(xi) = P(Y=1|xi), là hàm sao cho: π(xi) = σ(α + βxi)
>
>
>
> và cũng là log (π(xi) / \[1 - π(xi)) = α + βxi (1)
>
>
>
> Và soi chiếu theo mô hình GLM thì Y1,Y2,..độc lập \~ Bern(π(xi)) chính là tương ứng với exponential family có tham số là log (π(xi) / \[1 - π(xi)). link function là g(π(xi) = log (π(xi) / \[1 - π(xi)) và systematic component là α + βxi
>
>
>
> ---
>
>
>
> Vậy thì theo (1) thì:
>
>
>
> log (π(0) / \[1 - π(0)) = α
>
>
>
> ⇔ α = log \[P(Y=1|x=0)/P(Y=0|x=0)\]
>
>
>
> tức là log của odds of success, tỉ lệ giữa xác suất P(Y=1|x=0) và P(Y=0|x=0)
>
>
>
> ---
>
>
>
> Còn β: Nếu tính log (odd) tại x+1 trừ log odd tại x ta có:
>
>
>
> α + β(xi+1) - \[α + βxi\] = β
>
>
>
> Nên beta chính là mang ý nghĩa của mức thay đổi của log odd khi x tăng 1 đơn vị.
>
>
>
> (trong simple linear regression, E\[Y|x\] = α + βx, thì E\[Y|x+1\] - E\[Y|x\] = β nên ý nghĩa của β là mức thay đổi của mean Y khi x thay đổi 1 đơn vị)
>
>
>
> ---
>
>
>
> Tiếp, nếu từ
>
>
>
> log odd tại x+1 - log odd tại x = β
>
>
>
> exp(.) hai vế ta có:
>
>
>
> exp(log odd tại x+1 - log odd tại x) = exp(β)
>
>
>
> ⇔ exp(log odd tại x+1) / exp(log odd tại x) = exp(β)
>
>
>
> ⇔ odd tại x+1 / odd tại x = exp(β)
>
>
>
> Như vậy exp(β) là tỉ lệ odds tại x+1 và tại x
>
>
>
> ---
>
>
>
> Nói dễ hiểu: exp(β) là tỉ lệ giữa odds tại x+1: tỉ lệ xác suất success tại x+1 / xác suất failure tại x+1 với odds tại x

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, hiểu đúng và diễn giải cặn kẽ bản chất xác suất của alpha, beta và exp(beta), đồng thời mở rộng liên hệ chính xác với mô hình GLM.
>
> **✓ Strengths**
> - Diễn giải chính xác ý nghĩa log-odds của alpha tại x = 0 và mức thay đổi log-odds của beta khi x tăng 1 đơn vị.
> - Chứng minh và hiểu rõ exp(beta) là odds ratio (tỉ số odds) đại diện cho mức thay đổi nhân tử của odds.
> - Liên kết kiến thức tốt với lý thuyết GLM (họ phân phối hàm mũ, hàm liên kết logit, thành phần hệ thống).
>
> **💡 Deeper notes**
> - Cần lưu ý phân biệt giữa 'odds ratio' (tỉ số odds so với mốc trước đó) và 'xác suất' (probability), vì odds ratio tăng không đồng nghĩa với xác suất tăng tuyến tính do tính phi tuyến của hàm sigmoid.

<br>

<a id="node-7hcnyrb"></a>

###### Modeling Bernoulli Success Probability

<p align="center"><kbd><img src="assets/shy5mw2e26.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là:
>
>
>
> Nhắc lại logistic regression: giả định y1,y2,....là observed value của Y1,Y2,...độc lập sao cho:
>
>
>
> Yi \~ Bern(π(xi)) với:
>
>
>
> π(xi) = σ(α + βxi),  (1)
>
>
>
> σ(w) = exp(w) / \[1+exp(w)\], cũng là 1/\[1+exp(-w)\] là hàm logistic sigmoid, (hay như sách viết là hàm F(w))
>
>
>
> Thế thì ông nói rằng, hàm σ hay F, vốn dĩ ta đã gặp rồi, nó chính là CDF của phân phối logistic (0,1). Xem link
>
>
>
> Thế thì như vậy, nếu ta thay hàm σ/cdf của sigmoid trong giả định này bởi một hàm cdf khác, ta sẽ có mô hình khác:
>
>
>
> Ví dụ, thay bằng cdf của normal, Φ(w), ta sẽ có mô hình Probit regression, như sau:
>
>
>
> giả định y1,y2,...là observed values của Y1,Y2,...độc lập có:
>
>
>
> Yi \~ Bern(π(xi)) với
>
>
>
> π(xi) = P(Y=1|xi) = Φ(α + βxi) 
>
>
>
> Đây cũng là cái đã gặp trong chương 4 Bishop
>
>
>
> ---
>
>
>
> Tương tự, nếu thay bởi Gumbel cdf thì ta sẽ có mô hình khác, trong đó link function là log-log link.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác và mạch lạc nội dung từ giáo trình, đồng thời liên hệ tốt với các kiến thức đã học trước đó.
>
> **✓ Strengths**
> - Nắm vững bản chất việc mô hình hóa xác suất thành công π(x) thông qua hàm CDF liên tục.
> - Trình bày chuẩn xác mô hình Bernoulli và định nghĩa toán học của Probit regression.
> - Liên hệ tốt và nhất quán với kiến thức về hàm sigmoid và tài liệu tham khảo khác (Bishop).
>
> **💡 Deeper notes**
> - Hàm liên kết (link function) g(π) thực chất là hàm nghịch đảo của CDF được chọn, tức g(π) = F^(-1)(π); do đó với CDF Gumbel (loại cực trị), hàm nghịch đảo của nó sẽ cho ra log-log hoặc complementary log-log (cloglog) link.

**🔗 See also:** [Hàm phân phối Logistics](./15_distribution_function.md#node-b5jxnwe)

<br>

