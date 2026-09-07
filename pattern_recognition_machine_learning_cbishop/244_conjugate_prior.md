# 2.4.4 Conjugate prior

📊 **Progress:** `1` Notes | `1` Screenshots | `1` AI Reviews

---
<a id="node-6al8ljb"></a>

<br>

<a id="node-5f0a4fj"></a>

## 2.4.2 Conjugate priors

<p align="center"><kbd><img src="assets/ylavqwzofti.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói đại khái là mình đã quen với khái niệm prior distribution rồi. Ôn nhanh: Nói về prior distribution / posterior distribution thì thường là sẽ đang đi qua trường phái Bayesian khi coi tham số θ (ở đây là **η**) là random variable (vector), để rồi từ việc chọn một prior distribution cho nó (thường sách toán Casellla kí hiệu π(θ) ta sẽ dùng Bayes theorem để xây dựng posterior distribution π(θ|𝐱) = f(𝐱|θ)π(θ)/f(𝐱). Thế thì khi prior được chọn là một distribution thuộc loại conjugate prior với distribution của sample f(x|θ) thì khi đó, posterior sẽ cho ra kết quả là cùng một loại với prior distribution, tạo ra nhiều thuận lợi trong tính toán và diễn giải.
>
>
>
> Vậy thì vài ví dụ đã gặp, như khi f(x|θ) là Bernuoilly, thì conjugate prior của population mean θ chính là beta distribution. Còn khi f(x|μ, σ²) là pdf của normal μ, σ², thì conjugate prior của μ cũng là Normal, và conjugate prior của precision (1/σ²) là Wishart distribution.
>
>
>
> Vậy thì ở đây ta bàn về conjugate prior (cho **η**) họ exponential family, gs cho biết nó là distribution có dạng như sau:
>
>
>
> f(**η**|**χ**, ν) = f(**χ**, ν)g(**η**)^ν exp{ν**η**ᵀ**χ**}
>
>
>
> Để chứng minh, chỉ việc derive posterior và chỉ ra nó cũng có dạng này.
>
>
>
> Còn nhớ pdf của exponential family:
>
>
>
> f(𝐱|**η**) = h(𝐱)g(**η**)exp{**η**ᵀ𝐮(𝐱)}
>
>
>
> ⇨ Joint pdf của mọi data point f(𝐱1,..,𝐱N|**η**), như đã biết do tính iid, tách thành tích các marginal pdf:
>
> f(𝐱1,..,𝐱N|**η**) = Πi=1:N h(𝐱i)g(**η**)exp{**η**ᵀ𝐮(𝐱i)}
>
>
>
> Posterior distribution của **η**: 
>
>
>
> f(**η**|𝐱1,...𝐱N,**χ**, ν) (trong sách là p(**η**|𝐗,**χ**, ν)) = f(𝐱1,...**,x**N|**η**) × f(**η**|**χ**, ν) / f(𝐱1,...**,x**N)
>
>
>
> Như thường lệ, ta sẽ dùng kí hiệu proportional để chỉ quan tâm đến những term chứa **η**, phần constant sẽ tham gia vào normalizing cosntant:
>
>
>
> f(**η**|𝐱1,...𝐱N,**χ**, ν) ∝ f(𝐱1,...**,x**N|**η**) × f(**η**|**χ**, ν)
>
>
>
> = Πi=1:N \[ h(𝐱i)g(**η**)exp{**η**ᵀ𝐮(𝐱i)} \] × f(**χ**, ν)g(**η**)^ν exp{ν**η**ᵀ**χ**}
>
>
>
> = \[Πi=1:N h(𝐱i)\] × g(**η**)^N × exp{**η**ᵀ\[∑i 𝐮(𝐱i)\]} × f(**χ**, ν) × g(**η**)^ν × exp{ν**η**ᵀ**χ**}
>
>
>
> = \[Πi=1:N h(𝐱i)\] × f(**χ**, ν) × g(**η**)^N × g(**η**)^ν × exp{**η**ᵀ\[∑i 𝐮(𝐱i)\]} × exp{ν**η**ᵀ**χ**}
>
>
>
> ∝ g(**η**)^(N+ν) × exp{**η**ᵀ\[∑i 𝐮(𝐱i)\] + ν**η**ᵀ**χ**}
>
>
>
> ∝ g(**η**)^(N+ν) × exp{**η**ᵀ\[∑i 𝐮(𝐱i) + ν**χ**\]}
>
>
>
> Tới đây, có thể thấy posteriori có dạng của priori với param là ∑i 𝐮(𝐱i) + ν**χ** (so với ν**χ** của priori) và N+ν (so với ν của priori).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **97/100**
>
> Ghi chú của bạn rất chính xác và có chiều sâu, đặc biệt là phần chứng minh chi tiết dạng của phân phối hậu nghiệm cho họ hàm mũ. Để hoàn thiện hơn, bạn có thể bổ sung thêm ý nghĩa của tham số "ν" như là số lượng quan sát giả định hiệu quả từ prior.

<br>

