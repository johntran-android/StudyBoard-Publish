# 4.2.2 Maximum likelihood solution

📊 **Progress:** `3` Notes | `5` Screenshots | `3` AI Reviews

---
<a id="node-cw9ndyg"></a>

<br>

<a id="node-18gm3s7"></a>

## 4.2.2 Maximum Likelihood Solution

<p align="center"><kbd><img src="assets/zbar1d0of38.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/1jc2lt705zwh.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, qua phần này đại khái là ta sẽ nói về việc training - tức đi xác định giá trị của tham số 𝐰, w0, của f(𝒞k|𝐱) cũng như prior f(𝒞k). Và như thường lệ, ta sẽ dùng cách tiếp cận phổ biến: Maximum Likelihoood.
>
>
>
> Có lẽ nên ôn lại tí về MLE, dù đã nói nhiều lần trước đây nhưng ôn lại để đặt ra cái khung sẽ giúp mình dễ làm hơn: Bài toán đặt ra là ta có observed data của môt random sample X1,....Xn, iid \~ f(x|θ). θ là tham số của population distribution, còn iid nghĩa là các random variable X1,..Xn đều độc lập nhau (gọi là multually independent) và có cùng chung distribution f(x|θ), tức pdf của X1, f(x1|θ) cũng là hàm pdf của X2, f(x2|θ) (chú ý, đừng có nhầm là f(x1|θ) = f(x2|θ) nhé, f(x1|θ) chỉ là nói về hàm pdf của X1, và f(x2|θ) chỉ là nói về hàm pdf của X2, ...và chúng là cùng một hàm số, distribution của chúng có chung một dạng, ví dụ đều là normal(μ, σ²) chẳng hạn)
>
>
>
> Thế thì ta sẽ muốn đi tìm một estimator của θ, theo định nghĩa, là hàm số của sample W(𝐗) = W(X1,..,Xn), để với observed data 𝐗 = 𝐱 thì ta có một estimate value của θ: W(𝐱). Vậy thì MLE chỉ là một phương pháp để ta đi tìm cái estimator tương đối tốt, chứ không phải là duy nhất. Và trong phương pháp này, ta sẽ chọn hàm W(𝐗) là hàm argmax\_θ L(θ|𝐱) với L(θ|𝐱) là likelihood function, mang ý nghĩa là thấy data như vậy (𝐱) thì với input θ hàm L(θ|𝐱) cho biết độ hợp lý của θ khi data khi đóng vai trò giải thích cho data như vậy là bao nhiêu. 
>
>
>
> Và giá trị của nó được define bởi f(𝐱|θ): Độ hợp lí của θ khi data quan sát được là 𝐱 được cho, được định nghĩa bởi chính giá trị joint pdf của 𝐗 tại 𝐱, L(θ|𝐱) = f(𝐱|θ).  Ta có thể coi như hai hàm này là đều là một hàm của cả θ và 𝐱 nhưng khi coi θ là fixed, thì ta có hàm của 𝐱 là joint pdf, còn khi coi 𝐱 là fixed, ta có hàm của θ là hàm likelihood.
>
>
>
> Dùng tính iid của X1,...Xn, ta có thể tách joint pdf/pmf của X1,...Xn thành tích các marginal pdf/pmf:
>
>
>
> L(θ|𝐱) = f(𝐱|θ) = Πi=1:n f(xi|θ)
>
>
>
> Tóm lại ta giải bài toán tối ưu: maximize (over θ) L(θ|𝐱) = Πi=1:n f(xi|θ). Và để dễ, toán tối ưu cho phép ta dùng hàm monotone, điển hình là ln() để chuuyển thành bài toán tương đương: maximize \[ln L(θ|𝐱)\] = ln Πi=1:n f(xi|θ), dùng tính chất hàm ln = Σi ln f(xi|θ).
>
>
>
> ---
>
>
>
> Rồi, cái phần vừa rồi sẽ làm thành cái khung để mình áp vào bài toán này.
>
>
>
> Quay lại đây, ta sẽ có thể hiểu vì sao để làm ML, ta cần data (tương ứng với 𝐗 = 𝐱 ở framework trên), và data ở đây sẽ là các cặp (𝐱n, tn) với tn là target value, mang giá trị 1 khi 𝐱n là thuộc 𝒞1, và 0 nếu là 𝒞2. (ta đang xét bài toán K = 2 trước)
>
>
>
> Bên cạnh đó, class prior f(𝒞), tức class prior distribution, ta cũng sẽ gọi tham số là π, tức f(𝒞), hay f(t) \~ Bern(π), tức P(𝒞=C1) = P(T=1) = π, đương nhiên P(𝒞=C2) = P(T=0) = 1-π 
>
>
>
> Tới đây ta cần xây dựng hàm likelihood: Mà để hiểu likelihood là cái nào thì cần nhìn lại, ta đang muốn ML estimator cho cái gì?
>
>
>
> Trả lời: ta đang muốn tìm tham số của phân phối này đây f(𝒞, 𝐱) hay cũng là f(t, 𝐱)
>
>
>
> Chú ý, cần nhớ lại phần trước gs đã nói, ta đang đi theo lối "generative", xây dựng joint distribution: f(𝐱, 𝒞k), và cái này thì bằng f(𝐱|𝒞k)f(𝒞k) (theo định lý conditional probability) để sau đó mới đi dùng Bayes theorem để có class posterior: f(𝒞k|𝐱) = f(𝐱|𝒞k)f(𝒞k)/f(𝐱) = f(𝐱|𝒞k)f(𝒞k)/ Σj f(𝐱|𝒞j)f(𝒞j). Nên ở đây, việc ta đang làm là đi giải bài toán point estimation cho tham số của f(𝐱, 𝒞k) theo cách tiếp cận maximum likelihood.
>
>
>
> (f(𝒞, 𝐱) hay f(t, 𝐱) như nhau, nếu gọi 𝒞 là class variable, nó sẽ có 2 possible value 𝒞1, 𝒞2 tương ứng với T là binary target variable có 2 possible value 1, 0: và P(𝒞 = 𝒞1) = P(T = 1), P(𝒞 = 𝒞2) = P(T = 0) nên f(𝒞|𝐱) hay f(t|𝐱) và f(𝒞) hay f(t) đều là một. 
>
>
>
> f(𝒞,𝐱) = f(𝐱|𝒞)f(𝒞)
>
>
>
> hay cũng là f(t,𝐱) = f(𝐱|t)f(t)
>
>
>
> Với f(𝐱|𝒞k) = f(𝐱|t) thì ta đang assume là Gaussian: 
>
>
>
> f(𝐱|𝒞1) = f(𝐱|t=1) = 𝒩(𝐱|𝛍1, 𝚺), 
>
>
>
> f(𝐱|𝒞2) = f(𝐱|t=0) = 𝒩(𝐱|𝛍2, 𝚺)
>
>
>
> Và prior: 
>
>
>
> f(𝒞1) = f(t)|t=1 (chính là P(T=1) = π, và f(𝒞2) = f(t)|t=0 = 1- π
>
>
>
> Do đó f(𝒞, 𝐱), hay f(t, 𝐱) sẽ phụ thuộc 𝛍k và π, ta viết f(𝒞, 𝐱| 𝛍1, 𝛍2, 𝚺, π) hay f(t, 𝐱| 𝛍1, 𝛍2, 𝚺, π):
>
>
>
> f(1, 𝐱| 𝛍1, 𝚺, π) = 𝒩(𝐱|𝛍1, 𝚺) π 
>
>
>
> f(0, 𝐱| 𝛍2, π) = 𝒩(𝐱|𝛍2, 𝚺) (1-π) 
>
>
>
> hay gom lại thành:
>
>
>
> f(t, 𝐱| 𝛍1, 𝛍2, 𝚺, π) = 𝒩(𝐱| I\_{t=1} 𝛍1 + I\_{t=0} 𝛍2, 𝚺) f(t) 
>
>
>
> hoặc có thể ghi vầy cũng được: 
>
>
>
> f(t, 𝐱| 𝛍1, 𝛍2, 𝚺, π) = \[𝒩(𝐱|𝛍1, 𝚺)\]^t × \[𝒩(𝐱|𝛍2, 𝚺)\]^(1-t) × f(t) 
>
>
>
> vì khi t = 1 thì \[𝒩(𝐱|𝛍1, 𝚺)\]^t × \[𝒩(𝐱|𝛍2, 𝚺)\]^(1-t) = \[𝒩(𝐱|𝛍1, 𝚺)\]^1 ×  \[𝒩(𝐱|𝛍2, 𝚺)\]^0 = 𝒩(𝐱|𝛍1, 𝚺)
>
>
>
> khi t = 0 thì \[𝒩(𝐱|𝛍1, 𝚺)\]^t × \[𝒩(𝐱|𝛍2, 𝚺)\]^(1-t) = \[𝒩(𝐱|𝛍1, 𝚺)\]^0 ×  \[𝒩(𝐱|𝛍2, 𝚺)\]^1 = 𝒩(𝐱|𝛍2, 𝚺)
>
>
>
> ---
>
>
>
> Tương tự, với f(t) thì f(t)|t=1 = P(T=1) = π và f(t)|t=0 = P(T=0) = 1-π thì f(t) sẽ được thể hiện bởi:
>
>
>
> f(t) = (π^t) (1-π)^(1-t)
>
>
>
> ---
>
>
>
> Như vậy tương ứng với trong framework ở trên:
>
>
>
> θ : chính là: 𝛍1, 𝛍2, 𝚺, π 
>
>
>
> 𝐱: trong L(θ|𝐱) sẽ là observed data: (𝐱1, t1), (𝐱2, t2),...(𝐱N, tN), đặt thành matrix 𝐗 và vector 𝐭.
>
>
>
> Nên hàm likelihood là L(𝛍1, 𝛍2, 𝚺, π|𝐗, 𝐭), và theo định nghĩa, giá trị của nó bằng: f(𝐗, 𝐭|𝛍1, 𝛍2, 𝚺, π) (tương tự như L(θ|𝐱) = f(𝐱|θ))
>
>
>
> Và tương tự, như nhờ tính iid của các data point: 
>
>
>
> f(𝐗, 𝐭|𝛍1, 𝛍2, 𝚺, π) = Πn=1:N f(𝐱n, tn | 𝛍1, 𝛍2, 𝚺, π)
>
>
>
> = Πn=1:N f(𝐱n, tn | 𝛍1, 𝛍2, 𝚺, π)), dùng tính chất hàm log log(AB) = log(A) + log(B)
>
>
>
> Tới đây thay f(𝐱n, tn | 𝛍1, 𝛍2, 𝚺, π) = \[𝒩(𝐱|𝛍1, 𝚺)\]^t × \[𝒩(𝐱|𝛍2, 𝚺)\]^(1-t) × f(t)
>
>
>
> và f(t) = (π^t) (1-π)^(1-t)
>
>
>
> ⇒ ...= Πn=1:N f(𝐱n, tn | 𝛍1, 𝛍2, 𝚺, π)
>
>
>
> = Πn=1:N \[𝒩(𝐱|𝛍1, 𝚺)\]^tn × \[𝒩(𝐱|𝛍2, 𝚺)\]^(1-tn) × (π^tn) × (1-π)^(1-tn) 
>
>
>
> = Πn=1:N \[𝒩(𝐱|𝛍1, 𝚺)\]^tn × (π^tn) × \[𝒩(𝐱|𝛍2, 𝚺)\]^(1-tn) × (1-π)^(1-tn) 
>
>
>
> = Πn=1:N \[π 𝒩(𝐱|𝛍1, 𝚺)\]^tn × \[(1-π) 𝒩(𝐱|𝛍2, 𝚺)\]^(1-tn) 
>
>
>
> Viết lại hoàn chỉnh likelihood:
>
>
>
> L(𝛍1, 𝛍2, 𝚺, π|𝐗, 𝐭) = f(𝐗, 𝐭|𝛍1, 𝛍2, 𝚺, π) = Πn=1:N \[π 𝒩(𝐱n|𝛍1, 𝚺)\]^tn × \[(1-π) 𝒩(𝐱n|𝛍2, 𝚺)\]^(1-tn) 
>
>
>
> Nhận xét: Ở đây tác giả Bishop đã làm theo cái kiểu bỏ bớt 𝐗 để ghi thành p(𝐭|π,𝛍1, 𝛍2, 𝚺), nhưng phải hiểu là phải có 𝐗 vì không thể tự nhiên lại bỏ mất 𝐗.
>
>
>
> ---
>
>
>
> Bài toán tối ưu cần giải ở đây: maximize hàm likelihood, như thường lệ, ta chuyển sang bài toán tương đương dùng hàm ln likelihood, và cũng bỏ đi các constant không phụ thuộc các biến tối ưu:
>
>
>
> ln L(𝛍1, 𝛍2, 𝚺, π|𝐗, 𝐭)
>
>
>
> = ln { Πn=1:N \[π 𝒩(𝐱n|𝛍1, 𝚺)\]^tn × \[(1-π) 𝒩(𝐱n|𝛍2, 𝚺)\]^(1-tn) }
>
>
>
> = Σn=1:N { ln \[π 𝒩(𝐱n|𝛍1, 𝚺)\]^tn × \[(1-π) 𝒩(𝐱n|𝛍2, 𝚺)\]^(1-tn) }
>
>
>
> = Σn=1:N { ln \[π 𝒩(𝐱n|𝛍1, 𝚺)\]^tn + ln { \[(1-π) 𝒩(𝐱n|𝛍2, 𝚺)\]^(1-tn) }
>
>
>
> = Σn=1:N { tn ln \[π 𝒩(𝐱n|𝛍1, 𝚺)\] + (1-tn) ln { \[(1-π) 𝒩(𝐱n|𝛍2, 𝚺)\] }
>
>
>
> ---
>
>
>
> Tới đây, ta sẽ giải theo từng biến (toán tối ưu cho phép ví dụ như maximize f(x,y) thì ta có thể maximize f(x, y) theo x trước (coi y như fixed), tìm ra x\*, sau đó maximize f(x\*, y) theo y để tìm y\*)
>
>
>
> Nên ở đây ta giải tìm π trước, do đó, ta sẽ tách các term không dính tới π ra, và bỏ đi (tức là chuỷển thành bài toán tương đương bằng cách bỏ đi constant ko liên quan biến tối ưu)
>
>
>
> maximize\_π ln likelihood = Σn=1:N { tn ln π + tn ln 𝒩(𝐱n|𝛍1, 𝚺) + (1-tn) ln (1-π) + (1-tn) ln \[𝒩(𝐱n|𝛍2, 𝚺)\] }
>
>
>
> equivalent:
>
>
>
> maximize\_π  Σn=1:N { tn ln π + (1-tn) ln (1-π) }   (chính là 4.72)
>
>
>
> Để giải, như thường lệ, dùng điều kiện cần tối ưu bậc nhất: Đạo hàm tại solution phải = 0:
>
>
>
> d/dπ \[Σn=1:N { tn ln π + (1-tn) ln (1-π) }\] = 0
>
>
>
> ⇔ Σn=1:N { d/dπ \[tn ln π + (1-tn) ln (1-π)\] } = 0
>
>
>
> ⇔ Σn=1:N { tn/π - (1-tn)/(1-π)\] } = 0
>
>
>
> ⇔ (1/π) Σn=1:N tn = (1/(1-π)) Σn=1:N (1-tn)
>
>
>
> ⇔ (1/π) Σn=1:N tn = (1/(1-π)) (N - Σn=1:N tn) 
>
>
>
> Σn=1:N {tn} chính là gì: chính là N1: số data point thuộc class 𝒞1, có target t =1
>
>
>
> .. ⇔ (1/π) N1 = (1/(1-π)) (N - N1) 
>
>
>
> ⇔ (1/π) N1 = (1/(1-π)) N2
>
>
>
> ⇔ (1/π) N1 - (1/(1-π)) N2 = 0
>
>
>
> biến đổi chút sẽ ra π = N1/(N1+N2)
>
>
>
> Vậy maximum likelihood estimator của π, kí hiệu πML = N1/(N1+N2), kết quả này rất hợp lý về trực giác, khi nó lấy tỉ lệ của data point thuộc class 𝒞1 trong dataset làm estimate cho π vốn dĩ là xác suất (prior) của việc một data point thuộc class 𝒞1.
>
>
>
> Trong Casella mình cũng giải bài toán tìm ML estimator của Bern(p), kết quả chính là sample mean.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, nắm rất vững bản chất của mô hình generative và phương pháp Maximum Likelihood cho phân phối đồng thời (joint likelihood). Các bước biến đổi đạo hàm để tìm MLE cho π hoàn toàn chính xác và trực quan.
>
> **🟡 Minor issues**
>
> **1.** *"f(0, 𝐱| 𝛍2, π) = 𝒩(𝐱|𝛍2, 𝚺) (1-π)"*
>
> Thiếu ký hiệu tham số ma trận hiệp phương sai 𝚺 ở vế trái (đúng ra là f(0, 𝐱| 𝛍2, 𝚺, π)). Đây chỉ là sơ suất gõ phím nhỏ.
>
> **2.** *"Để giải, như thường lệ, dùng điều kiện cần tối ưu bậc nhất: Đạo hàm tại solution phải = 0"*
>
> Về mặt toán học chặt chẽ, đạo hàm bậc nhất bằng 0 chỉ là điều kiện cần (stationary point). Để khẳng định nghiệm là điểm cực đại toàn cục (maximum), cần kiểm tra thêm điều kiện đạo hàm bậc hai âm (tính lõm của hàm log-likelihood theo π).
>
>
> **✓ Strengths**
> - Phân biệt rất rõ bản chất mô hình Generative tiếp cận thông qua phân phối đồng thời f(x, t) = f(x|t)f(t) thay vì phân phối có điều kiện f(t|x) như Discriminative.
> - Nhận xét rất tinh tế và chuẩn xác về việc công thức (4.71) của Bishop ghi p(t|...) thực chất là joint likelihood của cả X và t nhưng tác giả viết giản lược/tắt đi X.
> - Dẫn dắt các bước tối ưu hóa log-likelihood cho tham số prior π mạch lạc, chi tiết và liên hệ tốt với ước lượng MLE của phân phối Bernoulli.
>
> **💡 Deeper notes**
> - Sở dĩ bài toán tối ưu có thể tách riêng biệt việc tìm π mà không phụ thuộc vào 𝛍1, 𝛍2, 𝚺 là do không gian tham số phân tách (decoupled parameter spaces) và hàm log-likelihood tách thành tổng các hàm mục tiêu độc lập giữa tham số prior và class-conditional.

<br>

<a id="node-71dks0j"></a>

### MLE for Class Mean Vectors

<p align="center"><kbd><img src="assets/bxo9bog0qb.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, sau khi đã giải ra MLE của π, tức πML, ta giải tiếp các variable khác: 𝛍1 và 𝛍2. Trước tiên là 𝛍1. Tương tự, giải bài toán tối ưu theo 𝛍1 thì coi các biến khác là fixed (1) (với π thì giờ có thể lắp πML vào)
>
>
>
> Viết lại hàm
>
>
>
> ln L(𝛍1, 𝛍2, 𝚺, π|𝐗, 𝐭)
>
>
>
> = Σn=1:N { tn ln \[π 𝒩(𝐱n|𝛍1, 𝚺)\] + (1-tn) ln { \[(1-π) 𝒩(𝐱n|𝛍2, 𝚺)\] }
>
>
>
> Vì ý (1), ta biến đổi thêm tí để tách các term không dính tới 𝛍1 ra để chuyển thành bài toán tương đương bằng cách bỏ các term này (hoặc cũng có thể hiểu cách khác là đạo hàm của chúng đối với 𝛍1 bằng 0)
>
>
>
> .. = Σn=1:N { tn ln (π) + tn ln \[𝒩(𝐱n|𝛍1, 𝚺)\] + (1-tn) ln (1-π) + (1-tn) ln \[𝒩(𝐱n|𝛍2, 𝚺)\] }
>
>
>
> Bỏ các constant đối với 𝛍1, ta còn Σn=1:N { tn ln \[𝒩(𝐱n|𝛍1, 𝚺)\] }
>
>
>
> thay công thức của 𝒩(𝐱n|𝛍1, 𝚺)\] vào:
>
>
>
> Σn=1:N { tn ln \[1/(2π)^(D/2) × 1/√|𝚺| × exp\[(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] }
>
>
>
> = Σn=1:N { tn ln \[1/(2π)^(D/2)\] + tn ln (1/√|𝚺|) + tn ln exp\[(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] }
>
>
>
> và tiếp tục bỏ các constant gồm normalizing constant và term dính tới det của 𝚺, còn lại:
>
>
>
> Σn=1:N { tn ln exp\[(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] }
>
>
>
> = Σn=1:N { tn (-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] }
>
>
>
> = (-1/2) Σn=1:N { tn(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] }
>
>
>
> Như vậy bài toán chỉ còn là maximize over 𝛍 hàm số (-1/2) Σn=1:N { tn(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] }
>
>
>
> Nhân phân phối vào: tn(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1) = tn(𝐱nᵀ 𝚺⁻¹-𝛍1ᵀ 𝚺⁻¹) (𝐱n-𝛍1)
>
>
>
> = tn(𝐱nᵀ 𝚺⁻¹𝐱n-𝛍1ᵀ 𝚺⁻¹𝐱n-𝐱nᵀ 𝚺⁻¹𝛍1+𝛍1ᵀ 𝚺⁻¹𝛍1)
>
>
>
> Do (𝛍1ᵀ 𝚺⁻¹𝐱n)ᵀ = 𝐱nᵀ(𝛍1ᵀ 𝚺⁻¹)ᵀ = 𝐱nᵀ(𝚺⁻¹)ᵀ(𝛍1ᵀ)ᵀ = 𝐱nᵀ(𝚺⁻¹)𝛍1 = 𝐱nᵀ 𝚺⁻¹𝛍1)
>
>
>
> = tn (𝐱nᵀ 𝚺⁻¹𝐱n - 2𝐱nᵀ 𝚺⁻¹𝛍1 + 𝛍1ᵀ𝚺⁻¹𝛍1)
>
>
>
> = tn𝐱nᵀ 𝚺⁻¹𝐱n - 2tn 𝐱nᵀ 𝚺⁻¹𝛍1 + tn 𝛍1ᵀ𝚺⁻¹𝛍1
>
>
>
> = (1/2) 𝛍1ᵀ (2tn𝚺⁻¹) 𝛍1 - 2tn 𝐱nᵀ 𝚺⁻¹𝛍1 + tn𝐱nᵀ 𝚺⁻¹𝐱n
>
>
>
> = (1/2) 𝛍1ᵀ (2tn𝚺⁻¹) 𝛍1 + \[-2tn(𝚺⁻¹)ᵀ𝐱n\]ᵀ 𝛍1 + tn𝐱nᵀ 𝚺⁻¹𝐱n
>
>
>
> ⟹ (-1/2) Σn=1:N \[(1/2) 𝛍1ᵀ (2tn𝚺⁻¹) 𝛍1 + \[-2tn(𝚺⁻¹)ᵀ𝐱n\]ᵀ 𝛍1 + tn𝐱nᵀ 𝚺⁻¹𝐱n\]
>
>
>
> Đây là hàm bậc hai của 𝛍1. Với hàm f(𝐱) = (1/2)𝐱ᵀ𝐏𝐱 + 𝐪ᵀ𝐱 + r, thì ∇f(𝐱) = 𝐏ᵀ𝐱 + 𝐪
>
>
>
> ---
>
>
>
> Active recall chút đã học trong MIT 18s096 cách tìm gradient của hàm f(𝐱) = (1/2)𝐱ᵀ𝐏𝐱 + 𝐪ᵀ𝐱 + r (giả định 𝐏 đối xứng)
>
>
>
> Ta sẽ đưa df về dạng một linear operator của d𝐱, ở đây sẽ là một dot product của gradient vector và d𝐱:
>
>
>
> df = (1/2)(𝐱+d𝐱)ᵀ𝐏(𝐱+d𝐱) + 𝐪ᵀ(𝐱+d𝐱) + r - (1/2)𝐱ᵀ𝐏𝐱 - 𝐪ᵀ𝐱 - r
>
>
>
> = (1/2)(𝐱ᵀ𝐏𝐱 + 2𝐱ᵀ𝐏d𝐱 + d𝐱ᵀ𝐏d𝐱) + 𝐪ᵀ𝐱 + 𝐪ᵀd𝐱 + r - (1/2)𝐱ᵀ𝐏𝐱 - 𝐪ᵀ𝐱 - r
>
>
>
> = (1/2)(𝐱ᵀ𝐏𝐱 + 2𝐱ᵀ𝐏d𝐱 + d𝐱ᵀ𝐏d𝐱) + 𝐪ᵀd𝐱 - (1/2)𝐱ᵀ𝐏𝐱
>
>
>
> = (1/2)𝐱ᵀ𝐏𝐱 + 𝐱ᵀ𝐏d𝐱 + (1/2)d𝐱ᵀ𝐏d𝐱 + 𝐪ᵀd𝐱 - (1/2)𝐱ᵀ𝐏𝐱
>
>
>
> = 𝐱ᵀ𝐏d𝐱 + 𝐪ᵀd𝐱
>
>
>
> = (𝐱ᵀ𝐏 + 𝐪ᵀ)d𝐱
>
>
>
> = (𝐏ᵀ𝐱 + 𝐪)ᵀd𝐱 ⇒ ∇f(𝐱) = 𝐏ᵀ𝐱 + 𝐪)
>
>
>
> ---
>
>
>
>
>
> Đạo hàm đối với 𝛍1 là: (-1/2) Σn=1:N\[(2tn𝚺⁻¹)ᵀ𝛍1 -2tn(𝚺⁻¹)ᵀ𝐱n\]
>
>
>
> = (-1/2) Σn=1:N {2tn𝚺⁻¹𝛍1 - 2tn𝚺⁻¹𝐱n}
>
>
>
> ((2tn𝚺⁻¹)ᵀ = (𝚺⁻¹)ᵀ(2tn)ᵀ = (𝚺⁻¹)(2tn) = (2tn)(𝚺⁻¹) (do tn là scalar, tranpose bằng chính nó, còn 𝚺⁻¹ là nghịch đảo của covariance matrix 𝚺, đương nhiên là matrix đối xứng)
>
>
>
> Cho đạo hàm bằng 0 (điều kiện cần tối ưu bậc nhất):
>
>
>
> (-1/2) Σn=1:N {2tn𝚺⁻¹𝛍1 - 2tn𝚺⁻¹𝐱n} = 0
>
>
>
> ⇔ Σn=1:N (tn𝚺⁻¹𝛍1) = Σn=1:N (tn𝚺⁻¹𝐱n)
>
>
>
> Vế trái, đem 𝚺⁻¹𝛍1 ra ngoài tổng. Vế phải chuyển tn vào giữa, vì scalar được phép di chuyển thứ tự tự do, rồi đem 𝚺⁻¹ ra ngoài tổng.
>
>
>
> ⇔ 𝚺⁻¹𝛍1 (Σn=1:N tn) = Σn=1:N (𝚺⁻¹ tn 𝐱n)
>
>
>
> ⇔ 𝚺⁻¹𝛍1 (Σn=1:N tn) = 𝚺⁻¹ Σn=1:N (tn 𝐱n)
>
>
>
> (Σn=1:N tn) là N1, vì sao? vì các data point thuộc 𝒞1 sẽ có target = 1, của 𝒞2 sẽ có target t = 0, nên tổng này chính là số các số 1, là số các data point thuộc 𝒞1.
>
>
>
> ⇔ 𝛍1 N1 = Σn=1:N (tn 𝐱n)
>
>
>
> ⇔ 𝛍1 = (1/N1) Σn=1:N (tn 𝐱n) → 4.75
>
>
>
> Vậy Maximum Likelihood estimator của 𝛍1 là (1/N1) Σn=1:N (tn 𝐱n)
>
>
>
> Σn=1:N (tn 𝐱n)? Ngẫm sẽ thấy, chính là tổng các 𝐱 của các data point thuộc class 𝒞1, vậy chia cho N1, chính là ta có sample mean các input 𝐱 của các data point thuộc class 𝒞1.
>
>
>
> ---
>
>
>
> Việc giải tìm MLE của 𝛍2 hoàn toàn tương tự, sẽ ra (1/N2) Σn=1:N (1-tn) 𝐱n và với Σn=1:N (1-tn) 𝐱n, again, cũng có ý nghiã là sample mean của các input 𝐱 của data point thuộc class 𝒞2.

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, tự lực biến đổi chi tiết từ hàm log-likelihood đến nghiệm đóng MLE của kỳ vọng mà không chỉ chép lại sách. Phần vi phân ma trận được giải thích rõ ràng.
>
> **🟡 Minor issues**
>
> **1.** *"= (1/2)(𝐱ᵀ𝐏𝐱 + 2𝐱ᵀ𝐏d𝐱 + d𝐱ᵀ𝐏d𝐱) ... (𝐏ᵀ𝐱 + 𝐪)ᵀd𝐱 ⇒ ∇f(𝐱) = 𝐏ᵀ𝐱 + 𝐪)"*
>
> Khi khai triển (𝐱+d𝐱)ᵀ𝐏(𝐱+d𝐱) thành 𝐱ᵀ𝐏𝐱 + 2𝐱ᵀ𝐏d𝐱, bạn đã ngầm thừa nhận 𝐏 đối xứng (để 𝐱ᵀ𝐏d𝐱 = d𝐱ᵀ𝐏𝐱). Trong trường hợp tổng quát nếu 𝐏 không đối xứng thì gradient là 1/2(𝐏 + 𝐏ᵀ)𝐱 + 𝐪. Tuy nhiên trong bài toán này 𝐏 = 2tn𝚺⁻¹ là ma trận đối xứng nên kết quả cuối cùng hoàn toàn chuẩn xác.
>
>
> **✓ Strengths**
> - Biến đổi đại số ma trận tỉ mỉ từ khai triển Gauss, cô lập thành phần chứa μ1 cho đến dạng toàn phương.
> - Tự chứng minh đạo hàm hàm bậc hai nhiều biến bằng vi phân ma trận (differential form) rất chặt chẽ.
> - Hiểu rõ bản chất ý nghĩa thống kê của tổng biến chỉ thị Σ tn = N1 và sample mean của từng lớp.
>
> **💡 Deeper notes**
> - Việc nhân cả hai vế với 𝚺 để triệt tiêu 𝚺⁻¹ ngầm dựa trên giả định ma trận hiệp phương sai 𝚺 là khả nghịch (dương xác định).

**🔗 See also:** [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj)

<br>

<a id="node-ruxkjon"></a>

#### MLE for Shared Covariance Matrix

<p align="center"><kbd><img src="assets/x21d80n3v7s.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ca461jjgnk.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, cuối cùng làm với 𝚺:
>
>
>
> Bắt đầu từ chỗ này của note trước:
>
>
>
> ln likelihood = Σn=1:N { tn ln (π) + tn ln \[𝒩(𝐱n|𝛍1, 𝚺)\] + (1-tn) ln (1-π) + (1-tn) ln \[𝒩(𝐱n|𝛍2, 𝚺)\] }
>
>
>
> Bỏ các term không dính tới 𝚺
>
>
>
> Σn=1:N { tn ln \[𝒩(𝐱n|𝛍1, 𝚺)\] + (1-tn) ln \[𝒩(𝐱n|𝛍2, 𝚺)\] }
>
>
>
> Thay công thức pdf vô:
>
>
>
> 1/(2π)^(D/2) × 1/√|𝚺| × exp\[(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)
>
>
>
> Σn=1:N { tn ln \[1/(2π)^(D/2) × 1/√|𝚺| × exp\[(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] +
>
>
>
> (1-tn) ln \[1/(2π)^(D/2) × 1/√|𝚺| × exp\[(-1/2)(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2)\] }
>
>
>
> = Σn=1:N { tn ln \[1/(2π)^(D/2)\] + tn ln \[1/√|𝚺|\] + tn ln exp\[(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] +
>
>
>
> (1-tn) ln \[1/(2π)^(D/2)\] + (1-tn) ln (1/√|𝚺|) + (1-tn) ln exp\[(-1/2)(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2)\] }
>
>
>
> (dùng tính chất hàm lg: ln(AB) = ln(A) + ln(B))
>
>
>
> Bỏ các term không dính 𝚺
>
>
>
> = Σn=1:N { tn ln \[1/√|𝚺|\] + tn ln exp\[(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] + (1-tn) ln (1/√|𝚺|) + (1-tn) ln exp\[(-1/2)(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2)\] }
>
>
>
> = Σn=1:N { tn ln \[1/√|𝚺|\] + tn(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1) + (1-tn) ln (1/√|𝚺|) + (1-tn) (-1/2)(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2) }
>
>
>
> = Σn=1:N { tn ln \[|𝚺|^(-1/2)\] + (1-tn) ln (|𝚺|^(-1/2)) + tn(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1) + (1-tn) (-1/2)(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2) }
>
>
>
> = Σn=1:N { tn (-1/2) ln |𝚺| + (1-tn) (-1/2) ln |𝚺| + tn(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1) + (1-tn) (-1/2)(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2) }
>
>
>
> = Σn=1:N { (-1/2) ln |𝚺| + tn(-1/2)(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1) + (1-tn) (-1/2)(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2) }
>
>
>
> Áp dụng 𝐱ᵀ𝐀𝐱 = Trace(𝐱ᵀ𝐀𝐱) = tr(𝐀𝐱𝐱ᵀ) | tr(AB) = tr(BA)
>
>
>
> = Σn=1:N { (-1/2) ln |𝚺| + tn(-1/2) Tr\[(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] + (1-tn)(-1/2) Tr\[(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2)\] }
>
>
>
> Tr\[(𝐱n-𝛍1)ᵀ 𝚺⁻¹ (𝐱n-𝛍1)\] = Tr\[𝚺⁻¹(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ\] (tính xoay vòng của Trace)
>
>
>
> Tr\[(𝐱n-𝛍2)ᵀ 𝚺⁻¹ (𝐱n-𝛍2)\] = Tr\[𝚺⁻¹ (𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]
>
>
>
> ... = Σn=1:N { (-1/2) ln |𝚺| + tn(-1/2) Tr\[𝚺⁻¹(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ\] + (1-tn)(-1/2) Tr\[𝚺⁻¹ (𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\] }
>
>
>
> = Σn=1:N { (-1/2) ln |𝚺| + (-1/2) Tr\[𝚺⁻¹tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ\] + (-1/2) Tr\[𝚺⁻¹(1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\] } (dùng tính linearity của Trace)
>
>
>
> = Σn=1:N { (-1/2) ln |𝚺| + (-1/2) Tr\[𝚺⁻¹tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + 𝚺⁻¹(1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\] }
>
>
>
> = (-1/2) { \[Σn=1:N ln |𝚺|\] + Σn=1:N Tr{𝚺⁻¹ \[tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + (1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]} }
>
>
>
> = (-1/2) { N ln |𝚺| + Σn=1:N Tr{𝚺⁻¹ \[tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + (1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]} }
>
>
>
> = (-1/2) N ln |𝚺| - (1/2) Tr{ 𝚺⁻¹ Σn=1:N { \[tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + (1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\] } }
>
>
>
> = (-N/2) ln |𝚺| - (1/2) Tr{ 𝚺⁻¹ Σn=1:N { \[tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + (1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\] } } (2)
>
>
>
> ---
>
>
>
> Xét Σn=1:N { \[tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + (1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]
>
>
>
> = Σn=1:N \[tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + Σn=1:N \[(1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]
>
>
>
> = Σn∈𝒞1 \[1 × (𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + Σn∈𝒞2 \[0 × (𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + Σn∈𝒞1 \[(1-1)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\] + Σn∈𝒞2 \[(1-0)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]
>
>
>
> = Σn∈𝒞1 \[(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + Σn∈𝒞2 \[(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]
>
>
>
> Đặt 𝐒1 = (1/N1) Σn∈𝒞1 \[(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ
>
>
>
> 𝐒2 = (1/N2) Σn∈𝒞2 \[(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]
>
>
>
> .. = N1 𝐒1 + N2 𝐒2
>
>
>
> Viết lại Σn=1:N { \[tn(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ + (1-tn)(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\] = N1 𝐒1 + N2 𝐒2
>
>
>
> ---
>
>
>
> (2) = (-N/2) ln |𝚺| - (1/2) Tr{ 𝚺⁻¹ (N1 𝐒1 + N2 𝐒2) } }
>
>
>
> Đặt 𝐒 = (N1 𝐒1 + N2 𝐒2)/N ⇒ (N1 𝐒1 + N2 𝐒2) = N 𝐒
>
>
>
> .. = (-N/2) ln |𝚺| - (1/2) Tr(𝚺⁻¹ N 𝐒)
>
>
>
> = (-N/2) ln |𝚺| - (N/2) Tr(𝚺⁻¹ 𝐒) → Chính là 4.77
>
>
>
> Đạo hàm của (-N/2) ln |𝚺| - (N/2) Tr(𝚺⁻¹ 𝐒) đối với 𝚺
>
>
>
> ---
>
>
>
> f(𝐀) = Tr(𝐀𝐁) 
>
>
>
> df = f(𝐀 + d𝐀) - f(𝐀) =
>
>
>
> = Tr\[(𝐀+ d𝐀)𝐁\] - Tr(𝐀𝐁) = Tr(𝐀𝐁 + d𝐀𝐁) - Tr(𝐀𝐁)
>
>
>
> = Tr(𝐀𝐁) + Tr(d𝐀 𝐁) - Tr(𝐀𝐁)
>
>
>
> =  Tr(d𝐀 𝐁)
>
>
>
> 𝐱 . 𝐲 = Σi 𝐱i × 𝐲i = 𝐱ᵀ𝐲
>
>
>
> Ta có định nghĩa của inner product của hai matrix 𝐗, 𝐘: 𝐗 . 𝐘 = Σi,j (𝐗ij × 𝐘ij)
>
>
>
> mà cái này cơ bản là = Σ{các cột i=1,2,..} (cột i của 𝐗) dot product (cột i của 𝐘)
>
>
>
> mà Tr(d𝐀 𝐁) = Tr(𝐁 d𝐀) 
>
>
>
> = Σ{các hàng i=1,2...của 𝐁} \[hàng i của 𝐁\] \[cột i của d𝐀\] 
>
>
>
> = Σ{các cột i của 𝐁ᵀ} \[cột i của 𝐁ᵀ\] \[cột i của 𝐀\] 
>
>
>
> = 𝐁ᵀ . d𝐀 
>
>
>
> Do đó Tr(d𝐀 𝐁) = 𝐁ᵀ . d𝐀, là một linear operator của d𝐀 nên 
>
>
>
> ⇒ ∇f(𝐀) = 𝐁ᵀ
>
>
>
> ---
>
>
>
> f(𝐀) = Tr(𝐀⁻¹ 𝐁) ⇒ df = Tr(d𝐀⁻¹ 𝐁)
>
>
>
> d(𝐀⁻¹) ?
>
>
>
> f(𝐀) = 𝐀⁻¹
>
>
>
> 𝐀 𝐀⁻¹ = 𝐈
>
>
>
> ⇔ d𝐀 𝐀⁻¹ + 𝐀 d(𝐀⁻¹) = 0 
>
>
>
> ⇔ - d𝐀 𝐀⁻¹ = 𝐀 d(𝐀⁻¹) 
>
>
>
> ⇔ - 𝐀⁻¹ d𝐀 𝐀⁻¹ = d(𝐀⁻¹) 
>
>
>
> ⇒ d(𝐀⁻¹) = - 𝐀⁻¹ d𝐀 𝐀⁻¹
>
>
>
> ⇒ df = Tr(d𝐀⁻¹ 𝐁) = Tr(-𝐀⁻¹ d𝐀 𝐀⁻¹ 𝐁)
>
>
>
> = - Tr(𝐀⁻¹ d𝐀 𝐀⁻¹ 𝐁)
>
>
>
> = - Tr(𝐀⁻¹ 𝐁 𝐀⁻¹ d𝐀)
>
>
>
> = - Tr(d𝐀 𝐀⁻¹ 𝐁 𝐀⁻¹)
>
>
>
> = - \[𝐀⁻¹ 𝐁 𝐀⁻¹\]ᵀ . d𝐀
>
>
>
> ⇒ Vậy f(𝐀) = Tr(𝐀⁻¹ 𝐁) thì ∇f(𝐀) = - \[𝐀⁻¹ 𝐁 𝐀⁻¹\]ᵀ
>
>
>
> nên f(𝚺) = Tr(𝚺⁻¹ 𝐒) thì ∇f(𝚺) = - \[𝚺⁻¹ 𝐒 𝚺⁻¹\]ᵀ = -𝚺⁻¹ 𝐒 𝚺⁻¹
>
>
>
> d/d𝚺 (ln |𝚺|) = (𝚺⁻¹)ᵀ
>
>
>
> Nên đạo hàm của (-N/2) ln |𝚺| - (N/2) Tr(𝚺⁻¹ 𝐒) đối với 𝚺 :  
>
>
>
>  (-N/2) (𝚺⁻¹)ᵀ - (N/2) (-𝚺⁻¹ 𝐒 𝚺⁻¹)
>
>
>
> =  (-N/2) (𝚺⁻¹)ᵀ + (N/2) 𝚺⁻¹ 𝐒 𝚺⁻¹
>
>
>
> Cho đạo hàm bằng 0:
>
>
>
> (-N/2) (𝚺⁻¹)ᵀ + (N/2) 𝚺⁻¹ 𝐒 𝚺⁻¹ = 0
>
>
>
> ⇔ (N/2) 𝚺⁻¹ 𝐒 𝚺⁻¹ = (N/2) (𝚺⁻¹)ᵀ
>
>
>
> ⇔ 𝚺⁻¹ 𝐒 𝚺⁻¹ = (𝚺⁻¹)ᵀ
>
>
>
> ⇔ 𝚺⁻¹ 𝐒 𝚺⁻¹ = 𝚺⁻¹ 
>
>
>
> ⇔ 𝚺⁻¹ 𝐒  = 𝐈
>
>
>
> ⇔ 𝚺 = 𝐒
>
>
>
> ---
>
>
>
> Kết quả này cho thấy 𝚺\_ML là weighted average của 𝐒1, và 𝐒2. Với 
>
>
>
> 𝐒1 = (1/N1) Σn∈𝒞1 \[(𝐱n-𝛍1)(𝐱n-𝛍1)ᵀ
>
>
>
> 𝐒2 = (1/N2) Σn∈𝒞2 \[(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ\]
>
>
>
> Khúc cuối gs nói ta cũng sẽ có kết quả này tương tự khi xét bài toán K &gt; 2 class
>
>
>
> Và ML estimator không có tính robust.

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **96/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã tự mình chứng minh chi tiết từ việc biến đổi hàm log-likelihood về dạng Trace (4.77) cho đến việc đạo hàm ma trận vi phân để tìm ra nghiệm Σ = S mà sách giáo khoa bỏ qua.
>
> **🟡 Minor issues**
>
> **1.** *"(1-tn)D(𝐱n-𝛍2)(𝐱n-𝛍2)ᵀ"*
>
> Lỗi gõ phím thừa ký tự 'D' trong biểu thức, dù các dòng biến đổi sau đó bạn vẫn tính toán chính xác.
>
> **2.** *"⇔ 𝚺⁻¹ 𝐒 𝚺⁻¹ = (𝚺⁻¹)ᵀ ⇔ 𝚺⁻¹ 𝐒 𝚺⁻¹ = 𝚺⁻¹"*
>
> Bước chuyển từ (𝚺⁻¹)ᵀ sang 𝚺⁻¹ dựa trên giả thiết ma trận hiệp phương sai 𝚺 đối xứng (𝚺 = 𝚺ᵀ). Nên ghi chú rõ điều này để chặt chẽ về mặt toán học.
>
>
> **✓ Strengths**
> - Tự triển khai đầy đủ và chính xác đạo hàm ma trận bằng phương pháp vi phân (differential) d(A⁻¹) = -A⁻¹ dA A⁻¹ thay vì chỉ chấp nhận kết quả sẵn có từ giáo trình.
> - Sử dụng thành thạo và chuẩn xác các tính chất của Trace (cyclic property, tính tuyến tính) để rút gọn biểu thức bình phương khoảng cách về công thức 4.77.
>
> **💡 Deeper notes**
> - Khi đạo hàm theo một ma trận đối xứng, nếu xét theo quy tắc đạo hàm có ràng buộc đối xứng (symmetric matrix derivative), các phần tử ngoài đường chéo sẽ có thêm hệ số 2. Tuy nhiên khi giải phương trình đạo hàm bằng 0 với S là ma trận đối xứng, nghiệm cực trị vẫn cho ra chính xác 𝚺 = S.

**🔗 See also:** [Vi phân hàm log(det(A)) *(MIT 18S096 Matrix Calculus for ML)*](../mit_18s096_matrix_calculus_for_ml/lec_5_p1_derivative_of_matrix_determinant_and_invers.md#node-l0pnip6) · [Đạo hàm det(x𝐈-A) *(MIT 18S096 Matrix Calculus for ML)*](../mit_18s096_matrix_calculus_for_ml/lec_5_p1_derivative_of_matrix_determinant_and_invers.md#node-k3i9hxw)

<br>

