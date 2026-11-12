# 5.5.1 Consistent Gaussian priors

📊 **Progress:** `3` Notes | `7` Screenshots | `3` AI Reviews

---
<a id="node-vq3vs93"></a>

<br>

<a id="node-v9n8uuf"></a>

## Consistent Gaussian Priors

<p align="center"><kbd><img src="assets/ndokuysk5i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vi3y01kpssh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jwhi1dt49js.png" width="80%"></kbd></p>

> [!NOTE]
> Để dễ hiểu, tốt nhất là lấy ví dụ một neural net đơn giản:
>
> z = h(w⁽¹⁾x)
>
> y = w⁽²⁾z
>
> gỉa sử x là bề dài, y là giá nhà. Và neural net đã được train để đoán đúng:
>
> căn nhà 10 mét với giá 5 (tỷ): y = f(𝐰, 10) = w⁽²⁾ h(w⁽¹⁾ × 10) = 5
>
> giả sử chiều dài nhà bây giờ là cm, x̃ = 100 x
>
> để mô hình có tính nhất quán, mô hình sẽ điều chỉnh giá trị của 𝐰 sao cho
>
> w̃⁽²⁾ h(w̃⁽¹⁾x̃ ) = y
>
> ⇔ w̃⁽²⁾ h(w̃⁽¹⁾100x) = y
>
> ⇔ w̃⁽²⁾ h(w̃⁽¹⁾100x) = y
>
> để có tính nhất quán, hai biểu thức tính y theo x phải đồng nhất với nhau ∀x
>
> w̃⁽²⁾h(w̃⁽¹⁾100x) = w⁽²⁾ h(w⁽¹⁾x) ∀x
>
> Điều này xảy ra khi w̃⁽¹⁾100x = w⁽¹⁾x và w̃⁽²⁾ = w⁽²⁾
>
> ⇔ w̃⁽¹⁾ = w⁽¹⁾/100 và w̃⁽²⁾ = w⁽²⁾
>
> ---
>
> Vấn đề là, nếu có regularizer:
>
> Reg loss cũ: (λ/2)\[(w⁽¹⁾)² + (w⁽²⁾)²\]
>
> Reg loss mới: (λ/2)\[(w⁽¹⁾/100)² + (w⁽²⁾)²\]
>
> điều này sẽ khiến reg loss chỉ hầu như còn là đóng góp của w⁽²⁾, khiến cho regularizer sẽ ưu tiên tập trung vào w⁽²⁾ và bỏ qủa w⁽¹⁾ từ đó sẽ ưu tiên 𝐰 mà w⁽²⁾ nhỏ.
>
> Từ đó, nó sẽ không scale w như trên để network có tính consistent
>
> Đây là ý arbitrarily favours one solution over another solution
>
> ---
>
> Khái quát:
>
>
>
> Nếu ta có mạng:
>
>
>
> zj = h(Σi wjixi + wj0)
>
>
>
> yk = Σj wkjzj + wk0 
>
>
>
> yk = Σj wkj h(Σi wjixi + wj0) + wk0
>
>
>
> x1 → y1
>
>
>
> x2 → y2
>
>
>
> và ta biến đổi tuyến tính x, y:
>
>
>
> x̃ i = axi + b
>
>
>
> ỹk = cyk + d
>
>
>
> ỹk = Σj w̃ kj h(Σi w̃ ji x̃i + w̃ j0) + w̃ k0 (1)
>
>
>
> để giữ nguyên hàm mapping thì network với tham số w̃ phải map x với y với mọi cặp vector x,y:
>
>
>
> (1) ⇔ cyk + d = Σj w̃ kj h(Σi w̃ ji (axi + b) + w̃ j0) + w̃ k0
>
>
>
> ⇔ cyk = Σj w̃ kj h(Σi w̃ ji (axi + b) + w̃ j0) + w̃ k0 - d
>
>
>
> ⇔ yk = Σj (w̃ kj/c) h(Σi w̃ ji (axi + b) + w̃ j0) + w̃ k0/c - d/c
>
>
>
> ⇔ yk = Σj (w̃ kj/c) h(Σi (w̃ ji axi + w̃ ji b) + w̃ j0) + w̃ k0/c - d/c
>
>
>
> ⇔ y1k = Σj (w̃ kj/c) h(Σi a w̃ ji x1i + Σi w̃ ji b + w̃ j0) + w̃ k0/c - d/c
>
>
>
> y1k = Σj wkj h(Σi wjix1i + wj0) + wk0
>
>
>
> để đạt (2) ta phải có:
>
>
>
> ⇔ Σj (w̃ kj/c) h(Σi a w̃ ji xi + Σi b w̃ ji + w̃ j0) + w̃ k0/c - d/c
>
>
>
> = Σj wkj h(Σi wjixi + wj0) + wk0 **với mọi x**
>
>
>
> Điều này tương đương:
>
>
>
> Σi a w̃ ji xi + Σi b w̃ ji + w̃ j0 = Σi wji xi + wj0
>
>
>
> (w̃ kj/c) = wkj
>
>
>
> w̃ k0/c - d/c = wk0
>
>
>
> ⇔
>
>
>
> a w̃ ji = wji ⇔ w̃ ji = wji/a → 5.116
>
>
>
> Σi b w̃ ji + w̃ j0 = wj0 ⇔ w̃ j0 = wj0 - Σi b w̃ ji = wj0 - Σi b wji/a = wj0 - (b/a) Σi wji → 5.117
>
>
>
> w̃ kj = c wkj → 5.119
>
>
>
> w̃ k0/c - d/c = wk0 ⇔ w̃ k0 = c wk0 + d → 5.120
>
>
>
> ---
>
>
>
> Vậy có nghĩa là sao?
>
>
>
> Là để mạng vẫn biểu diễn cùng một mapping, weight của layer 1 phải scale nhỏ lại a lần (ví dụ a,b,c,d đều là số &gt; 1 ví dụ 2,3,4,5)
>
>
>
> weight của layer 2 phải scale to lên c lần
>
>
>
> bias của layer 1 phải shift một khoảng: -(b/a) Σi wji
>
>
>
> bias của layer 2 được scale bởi c và shift một khoảng d: + c wk0 + d
>
>
>
> Nếu chỉ có main loss SSE, mạng sẽ điều chỉnh đúng như vậy để giữ main loss ko đổi.
>
>
>
> Nhưng nếu có L2 regularizer: (λ/2) Σ w² thì việc điều chỉnh như vậy sẽ khiến L2 regularization loss bị hiện tượng như trong ví dụ cụ thể ở trên đã thấy: đóng góp của một loại nào đó sẽ có thể bị trở nên quá nhỏ so với loại còn lại. Khiến cho hiệu ứng của regularization sẽ thiên vị một loại này hơn loại kia, ví dụ chỉ ưu tiên khống chế weight của layer này mà bỏ mặc layer kia tạo nên cái gọi là "favor solution này hơn solution khác một cách tùy tiện"

📹 Video 1: [Vì sao weight decay không nhất quán khi co giãn đầu vào? (phần 1)](https://www.youtube.com/watch?v=W_XXQCusF6Q)

📹 Video 2: [Vì sao cần lambda riêng cho từng layer trong L2 regularization?](https://www.youtube.com/watch?v=fGd-ViSTpuo)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã tự diễn giải trực quan bằng ví dụ thực tế và biến đổi đại số đầy đủ, chính xác từng bước cho các công thức (5.116) - (5.120), đồng thời nắm rất vững bản chất vì sao regularizer L2 thông thường lại phá vỡ tính nhất quán này.
>
> **✓ Strengths**
> - Dùng ví dụ cụ thể (đổi đơn vị mét sang cm) giúp hình dung trực quan bản chất của việc scale trọng số giữa các tầng.
> - Tự triển khai phép biến đổi đại số đầy đủ và chính xác từ định nghĩa hàm ánh xạ tới các công thức (5.116) đến (5.120) trong sách.
> - Hiểu rất rõ và giải thích chuẩn xác lý do weight decay truyền thống (với một hệ số λ chung) làm lệch mục tiêu tối ưu khi quy mô dữ liệu thay đổi.
>
> **💡 Deeper notes**
> - Trong thực tế, người ta thường không áp dụng weight decay lên các tham số bias (w_0) vì bias chỉ dịch chuyển vị trí mà không ảnh hưởng trực tiếp đến độ mượt của hàm số, tuy nhiên ngay cả với riêng các ma trận trọng số w, việc dùng chung một hệ số λ giữa các tầng khác nhau vẫn vi phạm tính nhất quán này.

<br>

<a id="node-coru8dg"></a>

### Section 5.5 Regularization in Neural Networks

<p align="center"><kbd><img src="assets/gkyrydswsrg.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là với mong muốn có một regularizer "tốt hơn" khắc phục vấn đề này, một giải pháp là:
>
>
>
> (λ/2) Σ w²
>
>
>
> (λ1/2) Σ\_w∈𝒲1 w² + (λ2/2) Σ\_w∈𝒲2 w²
>
>
>
> tức là: dùng λ khác nhau cho hai layer và không đưa vào bias.
>
>
>
> Vì sao nó tốt hơn?
>
>
>
> Ví dụ:
>
>
>
> Reg loss cũ: (λ1/2) Σ\_w∈𝒲1 w² + (λ2/2) Σ\_w∈𝒲2 w²
>
>
>
> Reg loss mới: (λ1/2) Σ\_w∈𝒲1 (w/a)² + (λ2/2) Σ\_w∈𝒲2 (cw)²
>
>
>
> = (λ1/2a²) Σ\_w∈𝒲1 w² + (c²λ2/2) Σ\_w∈𝒲2 w²
>
>
>
> Như vậy, để trọng số cứ việc scale lên/xuống như mong muốn mà reg loss như cũ chỉ cần thay λ1 bằng λ1 × a² và λ2 thay bằng λ2/c²
>
>
>
> (hình như trong sách in sai)
>
>
>
> Còn bias cũng được điều chỉnh như mong muốn (vì nó ko bị regularizer khống chế)
>
>
>
> ---
>
>
>
> Và đại khái regularizer này tương ứng với việc dùng prior distribution của 𝐰 là:
>
>
>
> p(𝐰|α1,α2) ∝ exp(-(α1/2) Σ\_w∈𝒲1 w² - (α2/2) Σ\_w∈𝒲2 w²) (tìm hiểu sau)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, bạn không những nắm đúng bản chất về việc chia regularization parameter riêng cho từng layer và bỏ qua bias, mà còn rất sắc bén khi phát hiện ra lỗi in ấn chính thức trong sách của Bishop.
>
> **✓ Strengths**
> - Hiểu chính xác nguyên lý: không phạt bias và cần dùng các hệ số phạt khác nhau (λ1, λ2) cho từng layer để bảo toàn tính bất biến đối với biến đổi tuyến tính của input/output.
> - Biến đổi đại số chính xác và phát hiện đúng lỗi in sai của sách PRML (trong bản gốc sách in nhầm lũy thừa 1/2 và -1/2 thay vì 2 và -2, đã được xác nhận trong errata chính thức của Bishop).
>
> **💡 Deeper notes**
> - Về mặt ý nghĩa đầy đủ: việc regularizer bất biến (sau khi scale λ tương ứng) nhằm đảm bảo nghiệm tối ưu của toàn bộ hàm mục tiêu (Data Loss + Reg Loss) cho ra các dự đoán mạng nơ-ron hoàn toàn đồng nhất khi dữ liệu đầu vào hoặc đầu ra bị biến đổi affine.

<br>

<a id="node-wbjhok5"></a>

#### Improper Priors on Bias Parameters

<p align="center"><kbd><img src="assets/067nls38qb5u.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vq234j1gmx.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng đại ý là, cách làm này sẽ gây vấn đề khi ta làm công tác model comparision với Bayesian framework.
>
>
>
> Cụ thể là phân phối tiên nghiệm của bias sẽ trở thành improper. Khiến sinh vấn đề
>
>
>
> Là sao?
>
>
>
> Đầu tiên hãy nhớ lại trong linear regression với Bayesian, ta sẽ coi 𝐰 (bao gồm mọi weight bias) là random variable hết.
>
>
>
> Để rồi ta chọn prior distribution của 𝐰: f(𝐰) hay p(𝐰|α). Ví dụ, chọn 𝒩(𝟎, (1/α)𝐈)
>
>
>
> posterior distribution của 𝐰: p(𝐰|𝐭) ∝ p(𝐭|𝐰)p(𝐰|α)
>
>
>
> t1,t2,...là giá trị quan sát được của T1,T2,.. độc lập.: Ti \~ 𝒩(𝐰ᵀΦ(𝐱i), 1/β)
>
>
>
> p(𝐭|𝐰, β) = p(t1,t2,...|𝐰, β) = Πi p(ti|𝐰, β) = Πi 𝒩(ti|𝐰ᵀΦ(𝐱i), 1/β)
>
>
>
> Từ đó:
>
>
>
> p(𝐰|𝐭) ∝ p(𝐭|𝐰)p(𝐰|α) = \[Πi 𝒩(ti|𝐰ᵀΦ(𝐱i), 1/β)\] 𝒩(𝐰|𝟎, (1/α)𝐈)
>
>
>
> ⇔ p(𝐰|𝐭) ∝ \[Πi 𝒩(ti|𝐰ᵀΦ(𝐱i), 1/β)\] 𝒩(𝐰|𝟎, (1/α)𝐈)
>
>
>
> ⇔ p(𝐰|𝐭) ∝ \[Πi C1 exp{-(β/2)(ti-𝐰ᵀΦ(𝐱i))²}\] C2 exp\[-(α/2)𝐰ᵀ𝐰\]
>
>
>
> ⇔ p(𝐰|𝐭) ∝ \[C exp{-(β/2) Σi(ti-𝐰ᵀΦ(𝐱i))²} C2 exp\[-(α/2)𝐰ᵀ𝐰\]
>
>
>
> ⇔ p(𝐰|𝐭) ∝ C3 exp{-(β/2) Σi(ti-𝐰ᵀΦ(𝐱i))²} exp\[-(α/2)𝐰ᵀ𝐰\]
>
>
>
> ⇔ p(𝐰|𝐭) ∝ C3 exp{-(β/2) Σi(ti-𝐰ᵀΦ(𝐱i))² -(α/2)𝐰ᵀ𝐰}
>
>
>
> Do bên trong exponential là hàm bậc hai của 𝐰 nên posterior là normal
>
>
>
> Chọn/tìm 𝐰 sao p(𝐰|𝐭) lớn nhất, Maximum A Posteriori 𝐰MAP:
>
>
>
> maximize\_𝐰 {exp{-(β/2) Σi(ti-𝐰ᵀΦ(𝐱i))² -(α/2)𝐰ᵀ𝐰}}
>
>
>
> ≡ maximize\_𝐰 {ln exp{-(β/2) Σi(ti-𝐰ᵀΦ(𝐱i))²) -(α/2)𝐰ᵀ𝐰}}
>
>
>
> ≡ maximize\_𝐰 {-(β/2) Σi(ti-𝐰ᵀΦ(𝐱i))²) -(α/2)𝐰ᵀ𝐰}
>
>
>
> ≡ minimize\_𝐰 {β\[(1/2) Σi(ti-𝐰ᵀΦ(𝐱i))²) + (α/2β)𝐰ᵀ𝐰\]}
>
>
>
> ≡ minimize\_𝐰 {(1/2) Σi(ti-𝐰ᵀΦ(𝐱i))²) + (α/2β)𝐰ᵀ𝐰\]}
>
>
>
> ≡ minimize\_𝐰 {(1/2) Σi(ti-𝐰ᵀΦ(𝐱i))²) + (λ/2)𝐰ᵀ𝐰\]} với λ = α/β
>
>
>
> Kết quả này ta hiểu rằng:
>
>
>
> Niềm tin ban đầu rằng w đều nhỏ (quanh 0): xác suất w mang giá trị nhỏ quanh 0 là lớn, xác xuất w lớn xa mốc 0 là rất nhỏ. Điều này phản ánh vào reg loss: w lớn, reg loss sẽ lớn.
>
>
>
> Từ đó, nếu mình không đưa bias (wi0, wk0,..) vào reg loss sẽ tương đương việc ta tin rằng bias có thể mang giá trị bao nhiêu cũng được: điều này chính là p(bias) = c
>
>
>
> Việc ko đưa bias vào Regularizer ⇔ niềm tin (prior belief) p(bias) = c
>
>
>
> Và một distribution như vậy sẽ không thỏa hai yêu cầu valid của hàm pdf:
>
>
>
> f(x) = c ≥ 0
>
>
>
> ∫f(x)dx = 1
>
>
>
> ∫-∞:∞ c dx = c ∫-∞:∞ dx = ∞
>
>
>
> ---

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú giải thích rất xuất sắc và trực quan bản chất của improper prior: việc không phạt bias trong hàm mất mát tương đương với việc gán cho nó phân phối đều trên toàn trục số thực, dẫn đến tích phân phân kỳ.
>
> **✓ Strengths**
> - Dẫn dắt bài bản từ MAP trong Bayesian Linear Regression để liên hệ trực tiếp giữa số hạng chuẩn hóa (regularizer) và phân phối tiên nghiệm (prior).
> - Giải thích chính xác vì sao bias không bị ràng buộc tương ứng với prior phẳng p(bias) = c và chứng minh được tích phân phân kỳ (improper prior).
>
> **💡 Deeper notes**
> - Để hoàn thiện hơn câu mở đầu về 'model comparison', lý do kỹ thuật là hằng số chuẩn hóa của improper prior bị triệt tiêu/không xác định, khiến cho evidence (marginal likelihood p(D)) triệt tiêu hoặc phụ thuộc vào hằng số tùy ý, dẫn đến tỷ số Bayes (Bayes factor) để so sánh mô hình không còn dùng được.

<br>

<a id="node-wsg2852"></a>

<p align="center"><kbd><img src="assets/043dk0e8uqim.png" width="80%"></kbd></p>

