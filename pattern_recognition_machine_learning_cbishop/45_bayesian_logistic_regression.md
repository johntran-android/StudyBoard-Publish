# 4.5 Bayesian Logistic Regression

📊 **Progress:** `2` Notes | `3` Screenshots | `2` AI Reviews

---
<a id="node-9n6kt5p"></a>

<br>

<a id="node-1plrjxe"></a>

## Bayesian Logistic Regression

<p align="center"><kbd><img src="assets/wya54giw9pa.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này hiểu thế nào?
>
>
>
> Tác gỉa nói đại ý là khi tiếp cận logistic regression theo Bayesian, thì nếu làm chính xác sẽ không thể được (intractable), vì để tính posterior sẽ cần phải chuẩn hóa tích của prior distribution và likelihood function mà bản thân nó vốn chứa tích các hàm sigmoid.
>
>
>
> Tương tự, việc tính predictive distribution cũng không tính được luôn. Do đó ta sẽ ứng dụng phép xấp xỉ Laplace.
>
>
>
> Là sao nhỉ?
>
>
>
> ---
>
>
>
> Đầu tiên, Bayesian logistic regression là sao?
>
>
>
> Mình đã biết logistic regression model cho bài toán phân loại: P(T=1|Φ) = σ(𝐰ᵀΦ)
>
>
>
> Thì với Bayesian, ta sẽ coi 𝐰 như random variable. Sau đó chọn prior distribution f(𝐰), và dùng Bayes rule, tính ra posteriori f(𝐰|data) ∝ f(data|𝐰)f(𝐰) (data = (𝐱i, ti), i=1,2...N
>
>
>
> Từ đó, thay vì lắp một ước lượng điểm của 𝐰 vào P(T=1|Φ) = σ(𝐰ᵀΦ) (ví dụ 𝐰\_mle), ta tích phân theo phân phối này:
>
>
>
> P(T=1|Φ) = ∫σ(𝐰ᵀΦ) f(𝐰|data)d𝐰, đây là predictive distribution, trong đó tao không còn care 𝐰 nữa, vì đã lấy trung bình theo mọi giá trị 𝐰 dựa trên posterior của 𝐰.
>
>
>
> Giống như trong linear regression: f(t|𝐱) = ∫f(t|𝐰,β,𝐱)f(𝐰|𝐗,𝐭,α,β)d𝐰 (𝐗,𝐭 chính là data).
>
>
>
> Cụ thể, trong đó ta giả định prior f(𝐰) là 𝒩(0,(1/α)𝐈), từ đó có posterior:
>
>
>
> f(𝐰|data) ∝ f(data|𝐰)f(𝐰)
>
>
>
> = f(𝐭|𝐰,β𝐗)f(𝐰) = \[Πi f(ti|𝐰,β,𝐱i)\] f(𝐰) = \[Πi 𝒩(ti|𝐰ᵀΦ(𝐱i),1/β)\] f(𝐰)
>
>
>
> = \[Πi 𝒩(ti|𝐰ᵀΦ(𝐱i),1/β)\] 𝒩(𝐰|0,1/α)
>
>
>
> và vì normal prior là conjugate prior của likelihood (cũng là normal), nên posterior hóa ra cũng là normal.
>
>
>
> Ti|𝐱i \~ 𝒩(y(𝐰,𝐱i), 1/β)
>
>
>
> Và vì viết nó là normal nên ta chỉ cần biết (thông qua khớp mẫu) để xác định được tâm và covariance của posterior, đồng nghĩa là biết được hoàn toàn phân phối posterior của 𝐰
>
>
>
> Đây chính là cái là logistic không có, vì sao, vì nếu dùng giả định gì cho prior, thì vì likelihood của logistic đều là tích các hàm có dính đến hàm sigmoid:
>
>
>
> T|Φ \~ Bern(σ(𝐰ᵀΦ)) ⇒ P(T=t|𝐰) = \[σ(𝐰ᵀΦ)\]ᵗ × \[1-σ(𝐰ᵀΦ)\]¹⁻ᵗ
>
>
>
> f(𝐭|𝐰) = P(T1=t1,T2=t2,...|𝐰,Φ1,Φ2...) = Πi P(Ti=ti|Φi)
>
>
>
> = Πi σ(𝐰ᵀΦi)^ti × \[1-σ(𝐰ᵀΦi)\]^(1-ti)
>
>
>
> ...nên không thể cho ra kết quả posterior là phân phối gì đã biết (để từ đó suy luận ra được phân phối posterior hoàn chỉnh.
>
>
>
> Lưu ý, khi dùng Bayes để tính f(𝐰|data) = f(data|𝐰)f(𝐰)/f(data) thì ta hoàn toàn ko biết f(data), thành ra nếu như có thể khớp mẫu để xác định được f(data|𝐰)f(𝐰) là kernel của một phân phối đã biết nào đó, ta mới có thể mặc kệ f(data), coi nó như một phần của normalizing constant.
>
>
>
> ∫f(𝐰|data)d𝐰 = 1 ⇔ ∫f(data|𝐰)f(𝐰)/f(data) d𝐰 = 1
>
>
>
> ⇔ \[∫f(data|𝐰)f(𝐰)d𝐰\]/f(data) = 1
>
>
>
> ⇔ \[∫f(data|𝐰)f(𝐰)d𝐰\] = f(data)
>
>
>
> Còn ngược lại, để có hàm posterior, ta phải tính được hằng số chuẩn hóa, tức là, tính ∫f(data|𝐰)f(𝐰)d𝐰, nếu tính được, thì f(data|𝐰)f(𝐰)/Z sẽ valid pdf, và ta có hoàn chỉnh posterior của 𝐰. Ngặt nỗi, cái tích phân này cũng không tính được luôn (lại là do dính cái hàm sigmoid)
>
>
>
> Vậy, ta hiểu vì sao việc tính ra posterior của 𝐰 là intractable.
>
>
>
> Tiếp, nếu ko thể có posterior, thì làm sao có predictive distribution P(T=1|Φ) = ∫σ(𝐰ᵀΦ) f(𝐰|data)d𝐰. Mà giả sử có, thì tính cái tích phân này lại cũng không thể tính nổi, do nó lại dính hàm sigmoid σ(𝐰ᵀΦ)

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=qsnFuqhhQhI)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú giải thích rất xuất sắc và chính xác bản chất tại sao suy diễn Bayes cho hồi quy logistic lại không khả thi (intractable), so sánh đối chiếu chuẩn xác với hồi quy tuyến tính.
>
> **✓ Strengths**
> - Giải thích rất rõ ràng nguồn gốc tính intractable của posterior: không có phân phối tiên nghiệm liên hợp (conjugate prior) tương ứng với tích các hàm sigmoid, dẫn đến tích phân tính hằng số chuẩn hóa (normalizing constant / evidence) không thể giải dưới dạng đóng (closed-form).
> - Phân biệt chính xác giữa ước lượng điểm (như MLE/MAP) và suy diễn Bayes thuần túy thông qua tích phân tính phân phối dự đoán (predictive distribution).
> - So sánh đối chiếu rất trực quan với mô hình hồi quy tuyến tính Gauss-Gauss để làm nổi bật sự khác biệt về tính khả thi trong tính toán.
>
> **💡 Deeper notes**
> - Để giải quyết tích phân bất khả thi ở phân phối dự đoán sau khi đã xấp xỉ posterior bằng Laplace (dạng Gauss), người ta thường xấp xỉ hàm sigmoid bằng hàm probit scaling, biến tích phân chập giữa Gauss và sigmoid thành dạng xấp xỉ đóng.

**🔗 See also:** [3.3.2 Predictive distribution](./332_predictive_distribution.md#node-wdjepxb) · [Cross-Entropy Error Function Gradient](./432_logistic_regression.md#node-gvw6cdv)

<br>

<a id="node-yfe12aa"></a>

<a id="node-gnv598k"></a>

### 4.5.1 Laplace Approximation

<p align="center"><kbd><img src="assets/zra0ummmbhb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zfqlr64pfgo.png" width="80%"></kbd></p>

> [!NOTE]
> Nhớ lại chút xíu cách làm Laplace approx:
>
>
>
> Có hàm f(𝐳), chuẩn hóa để có p(𝐳) = f(𝐳)/Z. Ta muốn tìm một Gaussian xấp xỉ p(z):
>
>
>
> g(𝐳) = ln f(𝐳)
>
>
>
> g(𝐳) ≈ g(𝐳0) + ∇g(𝐳0)ᵀ(𝐳 - 𝐳0) + (1/2)(𝐳-𝐳0)ᵀ∇²g(𝐳0)(𝐳-𝐳0)
>
>
>
> ∇g(𝐳0)ᵀ(𝐳 - 𝐳0), vì đang xét 𝐳0 là đỉnh của f(𝐳), cũng là của g(𝐳) nên ∇g(𝐳0) = 𝟎
>
>
>
> ln f(𝐳) ≈ ln f(𝐳0) + (1/2) (𝐳-𝐳0)ᵀ\[∇²ln f(𝐳0)\](𝐳-𝐳0)
>
>
>
> ⇔ ln f(𝐳) ≈ ln f(𝐳0) - (1/2) (𝐳-𝐳0)ᵀ\[-∇²ln f(𝐳0)\](𝐳-𝐳0)
>
>
>
> ⇔ ln f(𝐳) ≈ ln f(𝐳0) + ln exp\[(-1/2) (𝐳-𝐳0)ᵀ\[-∇²ln f(𝐳0)\](𝐳-𝐳0)\]
>
>
>
> ⇔ ln f(𝐳) ≈ ln {f(𝐳0) exp\[(-1/2) (𝐳-𝐳0)ᵀ\[-∇²ln f(𝐳0)\](𝐳-𝐳0)\]}
>
>
>
> ⇔ f(𝐳) ≈ f(𝐳0) exp\[(-1/2) (𝐳-𝐳0)ᵀ\[-∇²ln f(𝐳0)\](𝐳-𝐳0)\]
>
>
>
> Đặt 𝐀 = -∇²ln f(𝐳0), ta có Gaussian xấp xỉ p(𝐳) là 𝒩(𝐳0, 𝐀⁻¹), 𝐀 phải xác định dương 
>
>
>
> ---
>
>
>
> Rồi, quay lại đây, ta giả định prior của 𝐰 là 𝒩(𝐦0, 𝐒0)
>
>
>
> Theo Bayes, posteriori của 𝐰: f(𝐰|data) ∝ f(data|𝐰)f(𝐰) với data ở đây là 𝐭 = t1,t2,.... (vì cũng như trong linear regression, ta mô hình phân phối của T|𝐱 (thay vì joint distribution T, 𝐗)
>
>
>
> Nên ta có f(𝐰|𝐭) = f(𝐭|𝐰)f(𝐰)/f(𝐭)
>
>
>
> ⇔ ln f(𝐰|𝐭) = ln f(𝐭|𝐰) + ln f(𝐰) - ln f(𝐭)
>
>
>
> ⇔ ln f(𝐰|𝐭) = ln Πi f(ti|𝐰) + ln 𝒩(𝐰|𝐦0, 𝐒0) + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = Σi ln f(ti|𝐰) + ln 𝒩(𝐰|𝐦0, 𝐒0) + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = Σi ln P(Ti=ti|𝐰) + ln 𝒩(𝐰|𝐦0, 𝐒0) + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = Σi ln \[(yi^ti)((1-yi)^(1-ti)\] + ln 𝒩(𝐰|𝐦0, 𝐒0) + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = Σi \[ln (yi^ti) + ln((1-yi)^(1-ti)\] + ln 𝒩(𝐰|𝐦0, 𝐒0) + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = Σi \[ti ln (yi) + (1-ti) ln(1-yi)\] + ln 𝒩(𝐰|𝐦0, 𝐒0) + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = Σi \[ti ln (yi) + (1-ti) ln(1-yi)\] + ln {const exp\[-(1/2)(𝐰-𝐦0)ᵀ𝐒0⁻¹(𝐰-𝐦0)\]} + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = Σi \[ti ln (yi) + (1-ti) ln(1-yi)\] + ln const + ln exp\[-(1/2)(𝐰-𝐦0)ᵀ𝐒0⁻¹(𝐰-𝐦0)\] + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = Σi \[ti ln (yi) + (1-ti) ln(1-yi)\] - (1/2)(𝐰-𝐦0)ᵀ𝐒0⁻¹(𝐰-𝐦0) + const
>
>
>
> ⇔ ln f(𝐰|𝐭) = - (1/2)(𝐰-𝐦0)ᵀ𝐒0⁻¹(𝐰-𝐦0) + Σi \[ti ln (yi) + (1-ti) ln(1-yi)\] + const → 4.142

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=BOlKZldjLic)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã tự ôn lại và chứng minh rất chi tiết, chặt chẽ cả công thức xấp xỉ Laplace tổng quát lẫn từng bước suy dẫn ra phương trình (4.142) từ tiên nghiệm Gauss và likelihood Bernoulli.
>
> **✓ Strengths**
> - Tự diễn giải và biến đổi rất rõ ràng chuỗi Taylor bậc 2 của log-posterior quanh cực trị để ra dạng phân phối chuẩn xấp xỉ.
> - Chứng minh chi tiết, mạch lạc từng bước từ hàm likelihood Bernoulli kết hợp với prior Gauss để thu được chính xác công thức (4.142).
>
> **💡 Deeper notes**
> - Để biểu thức hoàn toàn khớp với sách, bạn có thể ghi chú thêm định nghĩa $y_n = \sigma(\mathbf{w}^\mathrm{T}\boldsymbol{\phi}_n)$ và điều kiện ngầm định là likelihood có điều kiện trên tập vector đặc trưng $\mathbf{X}$ (hay $\boldsymbol{\Phi}$).

<br>

