# 4.3.5 Probit Regression

📊 **Progress:** `3` Notes | `5` Screenshots | `3` AI Reviews

---
<a id="node-de69sdj"></a>

<br>

<a id="node-hyepxp3"></a>

## 4.3.5 Probit Regression (bản sao)

<p align="center"><kbd><img src="assets/vri6vhne7x.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/r8iil9une1.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/a6yc00ulyhu.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên đại khái là nhắc lại câu chuyện bữa trước khi ta còn xét cái khung đi tạo class posterior distribution f(𝒞k|𝐱) hay f(𝒞k|Φ) từ generative distribution f(Φ|𝒞k)f(𝒞k)/f(Φ) thì ta đã biết cái vụ này: khi chọn giả định cho phân phối class conditional density f(𝐱|𝒞k) hay f(Φ|𝒞k), thì nếu ta chọn exponential family (trong đó điển hình là normal) có chung scale param (như normal có chung covariance matrix) thì kết quả sẽ thấy rằng class posterior f(𝒞k|𝐱) hay f(𝒞|Φ) có dạng **generalized linear model**, tức là một non-linear activation function (là sigmoid hoặc softmax) của một linear function của tham số và feature (hoặc transformed feature).
>
>
>
> Để rồi sau đó, ta mới chuyển sang cách làm trực tiếp, thay vì giả định phân phối của class conditional density, để có được generalize linear model, ta phang thẳng giả định rằng class posterior có dạng softmax hay sigmoid của hàm tuyến tính luôn.
>
>
>
> Và họ exponential family thì tuy rất rộng nhưng không phải bao trùm tất cả. Do đó, nếu ta chọn giả định khác cho class conditional density thì có thể kết quả không được như vậy. Nên ông mới nói có thể ta nên thử khám phá các cách tiếp cận khác, mong sao cũng cho ra dạng generalized linear model.
>
>
>
> Nên ở phần này, ta sẽ quay lại xét bài toán 2 class classification, với mô hình class posterior có dạng P(T=1|a) = f(a) với a = 𝐰ᵀΦ (cũng chính là f(𝒞1|Φ), mang ý nghĩa xác suất class 𝒞 = 𝒞1 given Φ)
>
>
>
> ---
>
>
>
> Thế thì, phần này bàn về một mô hình của class posterior P(T=1|a) = f(a)gọi là **noisy (stochastic) threshold model** có dạng:
>
>
>
> P(T=1|a) = g(a) và g define sao cho:
>
>
>
> Với T=1 khi a ≥ θ và T=0 khi a &lt; θ và θ \~ f(θ).
>
>
>
> Thế thì dĩ nhiên T=1 khi a ≥ θ nên P(T=1|a) = P(a ≥ θ) = P(θ ≤ a)
>
>
>
> ---
>
>
>
> Ôn lại tí kiến thức xác suất:
>
>
>
> định nghĩa của hàm cdf: F(x) = P(X ≤ x) = P(X ∈ (-∞, x\]) 
>
>
>
> còn định nghĩa của pdf: f(x) là hàm define bởi P(-inf ≤ X ≤ x) = ∫-inf:x f(t)dt.
>
>
>
> F(x) = ∫-inf:x f(t)dt
>
>
>
> Do đó P(X ≤ x) = P(-inf ≤ X ≤ x) = ∫-inf:x f(t)dt, và theo định nghĩa cdf ở trên, thì đây là F(x): F(x) = ∫-inf:x f(t)dt
>
>
>
> Mà theo FTC2: Nếu hàm G và f sao cho G(x) = ∫-inf:x f(t)dt thì G thì ta có G'(x) = f(x) và G gọi là nguyên hàm của f. Vậy vì kết quả trên nên ta có F là nguyên hàm của f: d/dx F(x) = f(x).
>
>
>
> ---
>
>
>
> Quay lại áp dụng vào đây, θ \~ pdf f(θ)
>
>
>
> Nên F(a) = P(θ ≤ a) = ∫-∞:a f(θ)dθ, ta có F(a) = ∫-∞:a f(θ)dθ, và theo định nghĩa của tích phân thì cái này chính là diện tích hàm pdf từ -inf tới a nên diện tích phần đồ thị hàm pdf bên trái mốc a chính là độ lớn hàm cdf tại a
>
>
>
> Và ta cũng hiểu d/dθ F(θ) = f(θ). Nên giá trị hàm pdf tại θ bất kì đều chính là độ dốc hàm F tại đó.
>
>
>
> Như vậy P(T=1|a) = g(a) = P(θ ≤ a) = ∫-∞:a f(θ)dθ = F(a), cho thấy với mô hình này hàm activation function f chính là hàm cdf của θ: f = F
>
>
>
> Vậy ý chính cần hiểu là trong noisy threshold model, P(T=1|a) = **f(a)** = P(θ ≤ a) = ∫-∞:a f(θ)dθ = **F(a)** thì ý chính cần thấy: trong mô hình này **cái hàm activation function chính là cdf của θ**.

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=bHTMl05EoAY)

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **95/100** · ✓ Move on
>
> Ghi chú nắm rất chắc và chính xác bản chất của noisy threshold model cũng như nguồn gốc dẫn dắt từ mô hình sinh sang mô hình phân biệt trong GLM. Điểm cần lưu ý duy nhất là việc lạm dụng ký hiệu chữ f cho cả activation function lẫn pdf.
>
> **🟡 Minor issues**
>
> **1.** *"θ ~ f(θ)... cho thấy với mô hình này hàm activation function f chính là hàm cdf của θ: f = F"*
>
> Có sự trùng lặp ký hiệu chữ cái 'f': trong sách, f(a) là hàm kích hoạt (activation function), còn mật độ xác suất của ngưỡng là p(θ). Việc bạn vừa ký hiệu pdf là f(θ) vừa ký hiệu hàm kích hoạt là f(a) rồi kết luận f = F dễ gây nhầm lẫn về mặt ký hiệu giữa pdf và hàm kích hoạt.
>
>
> **✓ Strengths**
> - Hiểu rõ động lực chuyển từ generative model (exponential family) sang mô hình phân biệt tổng quát hơn.
> - Giải thích chuẩn xác logic xác suất của noisy threshold model: P(T=1|a) = P(θ ≤ a) chính là tích phân diện tích dưới đường pdf từ -∞ đến a.
> - Liên hệ chính xác mối quan hệ giữa độ dốc của CDF và giá trị của PDF theo định lý cơ bản của giải tích (FTC).
>
> **💡 Deeper notes**
> - Trong GLM, nghịch đảo của hàm kích hoạt f(a) được gọi là link function g(a), tức a = g(μ). Khi chọn f(a) là CDF của phân phối chuẩn tắc (standard normal), ta sẽ thu được mô hình Probit regression kinh điển ở các mục tiếp theo.

<br>

<a id="node-cdwakw5"></a>

### Probit Function and Probit Regression

<p align="center"><kbd><img src="assets/9jdd7g9of6p.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì một ví dụ cụ thể, khi ta chọn distribution của θ là 𝒩(0,1) thì như activation function sẽ là F(a) = ∫-inf:a 𝒩(θ|0,1)dθ, và với normal 0,1 thì cdf được gán với chữ 𝚽, và cái này có tên là probit function.
>
>
>
> Ông cho biết nó có dạng chữ s giống như sigmoid
>
>
>
> Một điểm nữa là, khi ta dùng dạng khái quát hơn, thay vì standard normal thì nó không đổi model, mà chỉ tương đương với tác dụng rescale linear coefficient 𝐰. Là sao?
>
>
>
> Thử xem nếu dùng 𝒩(μ, σ²):
>
>
>
> F(a) = ∫-inf:a 𝒩(θ|μ, σ²)dθ
>
>
>
> = ∫-inf:a (1/√2πσ²) exp\[-(θ-μ)²/2σ²\] dθ
>
>
>
> = (1/√2πσ²) ∫-inf:a exp\[-(θ-μ)²/2σ²\] dθ
>
>
>
> Đặt z = (θ-μ)/σ ⇒ θ = z σ + μ ⇒ dθ = σ dz. Và cận tích phân thay đổi thành:
>
>
>
> θ → -∞ ⇔ z → -∞ ; θ = a → z = (a-μ)/σ
>
>
>
> Tích phân trở thành: (1/√2πσ²) ∫-inf:(a-μ)/σ  exp(-z²/2) σdz
>
>
>
> = (1/√2πσ²) σ ∫-inf:(a-μ)/σ  exp(-z²/2) dz
>
>
>
> = (1/√2π) ∫-inf:(a-μ)/σ  exp(-z²/2) dz
>
>
>
> Đưa (1/√2π) vào lại
>
>
>
> =  ∫-inf:(a-μ)/σ (1/√2π) exp(-z²/2) dz
>
>
>
> Ta thấy (1/√2π) exp(-z²/2) chính là pdf của 𝒩(0,1) nên tích phân này chính là cdf của Z \~ 𝒩(0,1) tại (a-μ)/σ, tức 𝚽((a-μ)/σ)
>
>
>
> Và thay a = 𝐰ᵀΦ ta có (a-μ)/σ = (𝐰ᵀΦ-μ)/σ 
>
>
>
> = 𝐰ᵀΦ/σ - μ/σ
>
>
>
> = (𝐰/σ)ᵀΦ - μ/σ
>
>
>
> = (𝐰/σ)ᵀΦ - μ/σ 
>
>
>
> ⇒ đây chỉ là việc ta scale 𝐰 bởi 1/σ và shift bởi μ/σ... 
>
>
>
> ..chứ model **vẫn là một generalize linear model với activation function là hàm** 𝚽 (probit function, cdf của 𝒩(0,1))
>
>
>
> ---
>
>
>
> Một ý nữa là có thể dùng eft function, là hàm quan hệ với 𝚽 bởi 4.116.
>
>
>
> Nói chung là, mô hình generalized linear model mà dùng hàm 𝚽 làm activation function, được gọi là **probit regression**.

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=no5efrUg8rs)

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **96/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, bạn đã tự mình chứng minh toán học tường minh cho khẳng định 'dùng Gaussian tổng quát chỉ tương đương rescale trọng số' mà sách chỉ nêu vắn tắt. Chỉ có một lỗi chính tả nhỏ khi gõ tên hàm erf.
>
> **🟡 Minor issues**
>
> **1.** *"Một ý nữa là có thể dùng eft function"*
>
> Lỗi gõ phím nhỏ: tên hàm chuẩn là 'erf function' (viết tắt của error function), không phải 'eft'.
>
>
> **✓ Strengths**
> - Tự thực hiện biến đổi tích phân đổi biến chính xác để giải thích vì sao Gaussian tổng quát N(μ, σ²) quy về được N(0,1).
> - Chỉ ra rõ ràng việc thay đổi tham số Gaussian tương đương với việc scale w bởi 1/σ và dịch bias bởi -μ/σ.
> - Nắm vững định nghĩa probit function và probit regression.
>
> **💡 Deeper notes**
> - Lưu ý rằng thành phần shift -μ/σ sẽ được hấp thu (absorbed) vào hệ số chệch w_0 (bias term) nếu ta gộp vector đặc trưng mở rộng, do đó cấu trúc mô hình hoàn toàn không đổi.

<br>

<a id="node-yeynirm"></a>

#### Probit vs Logistic Regression Outliers

<p align="center"><kbd><img src="assets/lyscslup7qe.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn cuối này đại ý là về cơ bản probit regression perform tương tự logistic, nó chỉ phát huy tác dụng khi ta qua Bayes approach ở phần sau.
>
>
>
> Một cái nữa, là nó nhạy cảm với outlier hơn logistic, nên với dataset có nhãn bị gán sai thì mô hình probit regression sẽ rất tệ

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ⚠️ **88/100** · ✓ Move on
>
> Ghi chú nắm rất tốt ý chính về sự tương đồng giữa probit và logistic regression cũng như độ nhạy của probit đối với outliers do đuôi phân phối suy giảm nhanh hơn.
>
> **🟡 Minor issues**
>
> **1.** *"nó chỉ phát huy tác dụng khi ta qua Bayes approach ở phần sau"*
>
> Cách diễn đạt hơi quá mức so với văn bản gốc. Sách dùng cụm 'find another use' (tìm thấy một ứng dụng/công dụng khác trong xử lý Bayes cho logistic regression), chứ không có nghĩa là probit 'chỉ' có tác dụng khi làm Bayes; bản thân mô hình probit vẫn hoạt động tốt và cho kết quả tương tự logistic khi dùng Maximum Likelihood.
>
>
> **✓ Strengths**
> - Nắm chuẩn xác việc probit regression nhạy cảm với dữ liệu nhiễu/outlier (như gán nhãn sai) hơn so với logistic regression.
> - Tóm lược đúng ý thực nghiệm: kết quả huấn luyện thường tương đương giữa hai mô hình khi dữ liệu chuẩn.
>
> **💡 Deeper notes**
> - Bản chất toán học giải thích cho sự khác biệt về độ nhạy outlier nằm ở tốc độ suy giảm ở đuôi (tail decay): logistic sigmoid giảm chậm theo bậc hàm exp(-x), trong khi hàm probit giảm rất nhanh theo hàm Gauss exp(-x^2), khiến điểm ngoại lai tác động mạnh hơn lên hàm mất mát/gradient.

<br>

