# 3.5.1 Evaluation of the evidence function

📊 **Progress:** `4` Notes | `9` Screenshots | `4` AI Reviews

---
<a id="node-xdok45p"></a>

<br>

<a id="node-u15ayc8"></a>

## Tính toán hàm evidence

<p align="center"><kbd><img src="assets/pf71nr2lt7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/unlta074jgk.png" width="80%"></kbd></p>

> [!NOTE]
> Qua phần này, đại khái là ta sẽ evaluate evidence function. Đầu tiên, có lẽ nên ôn lại chút xíu về marginal likelihood f(𝐭|α, β) và để hiểu rõ bản chất mình nên viết tường minh đầy đủ các yếu tố phụ thuộc thay vì bỏ bớt cho gọn (nhưng sẽ dễ khiến ta hiểu sai).
>
>
>
> Theo định nghĩa, model evidence hay marginal likelihood là xác suất của observed data 𝒟 dưới giả định mô hình phân phối gốc là ℳi: f(𝒟|**ℳ**i).
>
>
>
> Và dưới một model ℳi, để sinh ra data 𝒟 ta còn phải xét đến giá trị tham số 𝐰 cụ thể, vậy thì f(𝒟|ℳi) chính là kết quả mang ý nghĩa ta trung bình f(𝒟|**ℳ**i, 𝐰) trên mọi possible value của 𝐰 với 𝐰 \~ phân phối nào đó.
>
>
>
> f(𝒟|**ℳ**i,α) = ∫f(𝒟|**ℳ**i,𝐰)\[hàm probability distribution của 𝐰\]d𝐰
>
>
>
> Và phân phối của 𝐰 ở đây là distribution f(𝐰|α)
>
>
>
> f(𝒟|**ℳ**i,α) = ∫f(𝒟|**ℳ**i,𝐰)f(𝐰|α)d𝐰
>
>
>
> Tới đây, xét thực tế ta chỉ coi target variable là random variable, nên viết lại thành:
>
>
>
> f(𝐭|**ℳ**i,α,𝐗) = ∫f(𝐭|**ℳ**i,𝐰,𝐗)f(𝐰|α)d𝐰
>
>
>
> và nếu xét mô hình ℳi cụ thể nơi ta giả định T \~ n(y(𝐰,x), 1/β) thì ta sẽ bỏ đi ℳi, cái trên trở thành:
>
>
>
> f(𝐭|α,β,𝐗) = ∫f(𝐭|𝐰,β,𝐗)f(𝐰|α)d𝐰
>
>
>
> Và bỏ nốt 𝐗 đi cho gọn (dù luôn phải hiểu nó phải nằm ở đó)
>
>
>
> f(𝐭|α, β) = ∫f(𝐭|𝐰,β)f(𝐰|α)d𝐰. Đây chính là 3.77
>
>
>
> Do đó, ta sẽ cần hiểu rõ 3.77 là model evidence, hay marginal likelihood
>
>
>
> f(𝒟|**ℳ**i,α) = ∫f(𝒟|**ℳ**i,𝐰)f(𝐰|α)d𝐰, **với trường hợp rất cụ thể khi mô hình ℳi là**: T \~ n(y(𝐰,𝐱), 1/β) và prior là f(𝐰|α)
>
>
>
> ---
>
>
>
> Rồi, tiếp, để mà tính cái tích phân này, tác giả cho rằng ta có thể xài kết quả 2.115 (xem link), mà đại khái trong đó mình đã kết luận về công thức tham số của mô hình Normal là kết quả của nhân hai (pdf của) normal với nhau. Cụ thể là khi f(𝐱) = 𝒩(𝐱|**μ**, **Λ**inv), f(𝐲|𝐱) = 𝒩(𝐲|**Ax**+𝐛, 𝐋inv). Thì f(𝐲) sẽ là 𝒩(𝐲|**Aμ** + 𝐛, 𝐋inv + 𝐀 **Λ**inv 𝐀ᵀ)
>
>
>
> Vậy thì ở đây, nếu dùng kết quả này thì ta sẽ có
>
>
>
> f(𝐰|α) = 𝒩(𝐰|**0**,(1/α)𝐈) (chính là 3.52), cái này tương ứng với f(𝐱) = 𝒩(𝐱|**μ**, **Λ**inv)
>
>
>
> Tức **μ** = **0**, **Λ**inv = (1/α)𝐈
>
>
>
> f(𝐭|β,𝐰) thì là joint pdf của T1.....TN, với Ti \~ 𝒩(ti|𝐰ᵀΦ(𝐱), 1/β), nên theo tính iid, f(𝐭|β,𝐰) = Πi=1:N 𝒩(ti|𝐰ᵀΦ(𝐱), 1/β).
>
>
>
> và trước đây ta đã làm cái này, nó chính là 𝒩(𝐭|**Φw**, (1/β)𝐈).
>
>
>
> Và cái này tương ứng với f(𝐲|𝐱) = 𝒩(𝐲|**Ax**+𝐛, 𝐋inv), tức
>
>
>
> 𝐭 = 𝐲
>
>
>
> 𝐰 = 𝐱
>
>
>
> **Ax** + 𝐛 = **Φw** + **0**
>
>
>
> 𝐋inv = (1/β)𝐈
>
>
>
> ---
>
>
>
> Vậy ∫f(𝐭|𝐰,β)f(𝐰|α)d𝐰 sẽ là 𝒩(𝐲|**Aμ** + 𝐛, 𝐋inv + 𝐀 **Λ**inv 𝐀ᵀ)
>
>
>
> = 𝒩(𝐭|**Φ0** + **0**, (1/β)𝐈 + **Φ** (1/α)𝐈 **Φ**ᵀ)
>
>
>
> = 𝒩(𝐭|**0**, (1/β)𝐈 + (1/α)**ΦΦ**ᵀ)
>
>
>
> Vậy f(𝐭|α, β) = 𝒩(𝐭|**0**, (1/β)𝐈 + (1/α)**ΦΦ**ᵀ)
>
>
>
> Đặt **Σ** = (1/β)𝐈 + (1/α)**ΦΦ**ᵀ, ta có f(𝐭|α, β) = 𝒩(𝐭|**0**, **Σ**)
>
>
>
> Thay pdf của multivariate normal (1.52 xem link, nói rằng 𝒩(𝐱|**μ**, **Σ**) = \[1/(2π)^D/2\] \[1/|**Σ**|^1/2\] exp {-0.5(𝐱-**μ**)ᵀ **Σ**inv (𝐱-**μ**)}
>
>
>
> ..= \[1/(2π)^N/2\] \[1/|**Σ**|^1/2\] exp {-0.5(𝐭)ᵀ **Σ**inv (𝐭)}
>
>
>
> ---
>
>
>
> Tuy nhiên, ở đây mr Bishop lại không làm theo lối này (dùng kết quả 2.115), thay vào đó ông lại dùng cách khác - là dùng cách complete the square, để ra kết quả 3.78:
>
>
>
> Có nghĩa là ta có:
>
>
>
> ∫𝒩(𝐭|**Φw**, (1/β)𝐈)𝒩(𝐰|**0**,(1/α)𝐈) d𝐰
>
>
>
> = ∫𝒩(𝐭|**Φw**, (1/β)𝐈) 𝒩(𝐰|**0**,(1/α)𝐈) d𝐰
>
>
>
> Xét 𝒩(𝐭|**Φw**, (1/β)𝐈) 𝒩(𝐰|**0**,(1/α)𝐈)
>
>
>
> Với 𝒩(𝐭|**Φw**, (1/β)𝐈) = \[1/(2π)^N/2\] \[1/|(1/β)𝐈|^1/2\] exp {-0.5(𝐭-**Φw**)ᵀ ((1/β)𝐈)⁻¹ (𝐭-**Φw**)}
>
>
>
> = \[1/(2π)^N/2\] \[1/|(1/β)𝐈|^1/2\] exp {-0.5β(𝐭-**Φw**)ᵀ(𝐭-**Φw**)}
>
>
>
> = \[1/(2π)^N/2\] \[β^N/2\] exp {-0.5β(𝐭-**Φw**)ᵀ(𝐭-**Φw**)} (do determinant của (1/β)𝐈 với 𝐈 là identity matrix N × N = (1/β)^N = 1/β^N
>
>
>
> = \[(β/2π)^N/2\] exp {-0.5β(𝐭-**Φw**)ᵀ(𝐭-**Φw**)}
>
>
>
> Còn 𝒩(𝐰|**0**,(1/α)𝐈) = 𝒩(𝐱|**μ**, **Σ**) = \[1/(2π)^M/2\] \[1/|(1/α)𝐈|^1/2\] exp {-0.5(𝐰-**0**)ᵀ ((1/α)𝐈)⁻¹ (𝐰-**0**)}
>
>
>
> = \[1/(2π)^M/2\] \[α^M/2\] exp {-0.5α𝐰ᵀ𝐰} (do determinant của (1/α)𝐈 với 𝐈 là identity matrix M × M = (1/α)^M = 1/α^M
>
>
>
> = \[(α/2π)^M/2\] exp {-0.5α𝐰ᵀ𝐰}
>
>
>
> Vậy:
>
>
>
> ∫𝒩(𝐭|**Φw**, (1/β)𝐈)𝒩(𝐰|**0**,(1/α)𝐈) d𝐰
>
>
>
> = ∫\[(β/2π)^N/2\] exp {-0.5β(𝐭-**Φw**)ᵀ(𝐭-**Φw**)} \[(α/2π)^M/2\] exp {-0.5α𝐰ᵀ𝐰} d𝐰
>
>
>
> = \[(β/2π)^N/2\] \[(α/2π)^M/2\] ∫ exp {-0.5β(𝐭-**Φw**)ᵀ(𝐭-**Φw**)} exp {-0.5α𝐰ᵀ𝐰} d𝐰
>
>
>
>
>
> ---
>
>
>
> Tới đây, xét ∫ exp {-0.5β(𝐭-**Φw**)ᵀ(𝐭-**Φw**)} exp {-0.5α𝐰ᵀ𝐰} d𝐰, xem nó là cái gì
>
>
>
> Cục (𝐭-**Φw**)ᵀ(𝐭-**Φw**), dễ thấy chính là ||**Φw**-𝐭||² (hay ||𝐭-**Φw**||²)
>
>
>
> và 𝐰ᵀ𝐰 thì là ||𝐰||², nên ta có:
>
>
>
> ∫ exp {-0.5β(𝐭-**Φw**)ᵀ(𝐭-**Φw**)} exp {-0.5α𝐰ᵀ𝐰} d𝐰
>
>
>
> = ∫ exp {-0.5β||𝐭-**Φw**||²} exp {-0.5α||𝐰||²} d𝐰
>
>
>
> Dùng tính chất hàm mũ: e^a × e^b = e^(a+b)
>
>
>
> = ∫ exp {-0.5β||𝐭-**Φw**||² -0.5α||𝐰||²} d𝐰
>
>
>
> Và bằng cách **DEFINE** E_D\[𝐰\] = (1/2) ||𝐭-**Φw**||²
>
>
>
> E_W(𝐰) = 0.5||𝐰||² = 0.5 𝐰ᵀ𝐰
>
>
>
> và E(𝐰) = βE_D\[𝐰\] + α E_W\[𝐰\] thì:
>
>
>
> f(𝐭|α,β) = ∫𝒩(𝐭|**Φw**, (1/β)𝐈)𝒩(𝐰|**0**,(1/α)𝐈) d**w chính là:**
>
>
>
> \[(β/2π)^N/2\] \[(α/2π)^M/2\] ∫ exp {-E(𝐰)} d𝐰, → 3.78
>
>
>
> Mình hiểu E ở đây là Error, chứ ko phải kì vọng (Expectation của 𝐰) nhé.

---

🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on

Ghi chú vô cùng chi tiết, chính xác và thể hiện sự hiểu biết sâu sắc về cả hai phương pháp tính tích phân (dùng công thức phân phối Gaussian tuyến tính và biến đổi trực tiếp qua hàm năng lượng). Các bước phân tích rõ ràng và việc làm tường minh các biến phụ thuộc ẩn rất xuất sắc.

**🔗 See also:** [Phân bố tiên nghiệm và hậu nghiệm](./233_bayess_theorem_for_gaussian_variables.md#node-zswmsts) · [Likelihood and Error Functions](./311_maximum_likelihood_and_least_squares.md#node-urnjdcs) · [Gaussian Prior and Posterior Parameters](./331_bayesian_linear_regression.md#node-nt82rck) · [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj)

<br>

<a id="node-vpu7vqs"></a>

### Hessian of Regularized Error Function

<p align="center"><kbd><img src="assets/pl4dcze1369.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp nối note trước, ta đang có:
>
>
>
> f(𝐭|α,β) = \[(β/2π)^N/2\] \[(α/2π)^M/2\] ∫ exp {-E(𝐰)} d𝐰
>
>
>
> Mà mình đã biết rằng, bằng cách dùng kết quả từ chap 2, ta sẽ có đây chính là pdf của 𝒩(𝐭|**0**, **Σ**), **Σ** = (1/β)𝐈 + (1/α)**ΦΦ**ᵀ
>
>
>
> Còn ở đây, ta sẽ đại ý là đi làm động tác complete the square: tức là biến đổi cái cục trong exp(...) để cho ra kết quả có dạng là quadratic function của 𝐰, và từ đó kết luận đây là pdf của normal, rồi dùng khớp mẫu, ta sẽ xác định được mean và covariance (mà kết qủa sẽ ra cái vừa nói: 𝒩(𝐭|**0**, **Σ**), **Σ** = (1/β)𝐈 + (1/α)**ΦΦ**ᵀ). Có nghĩa là thay vì áp dụng kết quả từ chapter 2, ta đi làm lại vậy.
>
>
>
> ---
>
>
>
> Xét E(𝐰) = βE_D\[𝐰\] + α E_W\[𝐰\] với E_D\[𝐰\] = (1/2) ||𝐭-**Φw**||² và E_W(𝐰) = 0.5||𝐰||² = 0.5 𝐰ᵀ𝐰, ta có:
>
>
>
> E(𝐰) = β\[(1/2) ||𝐭-**Φw**||²\] + α (1/2) 𝐰ᵀ𝐰
>
>
>
> = (β/2) (𝐭-**Φw**)ᵀ(𝐭-**Φw**) + (α/2) 𝐰ᵀ𝐰
>
>
>
> = (β/2) (𝐭ᵀ - 𝐰ᵀ**Φ**ᵀ)(𝐭 - **Φw**) + (α/2) 𝐰ᵀ𝐰
>
>
>
> = (β/2) (𝐭ᵀ𝐭 - 𝐰ᵀ**Φ**ᵀ𝐭 - 𝐭ᵀ**Φw** + 𝐰ᵀ**Φ**ᵀ**Φw**) + (α/2) 𝐰ᵀ𝐰
>
>
>
> = (β/2) (𝐭ᵀ𝐭 - 2𝐭ᵀ**Φw** + 𝐰ᵀ**Φ**ᵀ**Φw**) + (α/2) 𝐰ᵀ𝐰
>
>
>
> = (β/2) 𝐭ᵀ𝐭 - (β/2)2𝐭ᵀ**Φw** + (β/2) 𝐰ᵀ**Φ**ᵀ**Φw** + (α/2) 𝐰ᵀ𝐰
>
>
>
> = (β/2) 𝐭ᵀ𝐭 - β𝐰ᵀ**Φ**ᵀ𝐭 + (β/2) 𝐰ᵀ**Φ**ᵀ**Φw** + (α/2) 𝐰ᵀ𝐰
>
>
>
> = (β/2) 𝐭ᵀ𝐭 - β𝐰ᵀ**Φ**ᵀ𝐭 + 𝐰ᵀ\[(β/2)**Φ**ᵀ**Φ**\]𝐰 + 𝐰ᵀ\[(α/2)𝐈\]𝐰
>
>
>
> = (β/2) 𝐭ᵀ𝐭 - β𝐰ᵀ**Φ**ᵀ𝐭 + 𝐰ᵀ\[(β/2)**Φ**ᵀ**Φ**+(α/2)𝐈\]𝐰
>
>
>
> Đặt 𝐀 = β**Φ**ᵀ**Φ**+α𝐈 
>
>
>
> = (1/2)𝐰ᵀ**Aw** - β𝐰ᵀ**Φ**ᵀ𝐭 + (β/2) 𝐭ᵀ𝐭
>
>
>
> ---
>
>
>
> Đến đây lập luận là, ta sẽ muốn biến đổi cái trên để trở thành dạng (1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N) + C
>
>
>
> = (1/2)(𝐰ᵀ**Aw** - (𝐦N)ᵀ**Aw** - 𝐰ᵀ**Am**N + (𝐦N)ᵀ**Am**N) + C
>
>
>
> = (1/2)(𝐰ᵀ**Aw** - 2𝐰ᵀ**Am**N + (𝐦N)ᵀ**Am**N) + C
>
>
>
> = (1/2)𝐰ᵀ**Aw** - 𝐰ᵀ**Am**N + (1/2)(𝐦N)ᵀ**Am**N) + C
>
>
>
> Thực hiện động tác "khớp mẫu":
>
>
>
> i) β𝐰ᵀ**Φ**ᵀ𝐭 = 𝐰ᵀ**Am**N ⇒ β**Φ**ᵀ𝐭 = **Am**N
>
>
>
> ⇔ 𝐦N = 𝐀inv β**Φ**ᵀ𝐭 = β𝐀inv **Φ**ᵀ𝐭 → đây là 3.84
>
>
>
> ii) (β/2) 𝐭ᵀ𝐭 = (1/2)(𝐦N)ᵀ**Am**N) + C
>
>
>
> ⇔ C = -(1/2)(𝐦N)ᵀ**Am**N) + (β/2) 𝐭ᵀ𝐭
>
>
>
> ⇔ C = - (𝐦N)ᵀ**Am**N) + (1/2)(𝐦N)ᵀ**Am**N) + (β/2) 𝐭ᵀ𝐭
>
>
>
> Thay β**Φ**ᵀ𝐭 = **Am**N, và 𝐀 = β**Φ**ᵀ**Φ**+α𝐈
>
>
>
> ⇔ C = - (𝐦N)ᵀ(β**Φ**ᵀ𝐭) + (1/2)(𝐦N)ᵀ(β**Φ**ᵀ**Φ**+α𝐈)𝐦N) + (β/2) 𝐭ᵀ𝐭
>
>
>
> ⇔ C = (β/2) 𝐭ᵀ𝐭 - (𝐦N)ᵀ(β**Φ**ᵀ𝐭) + (1/2)(𝐦N)ᵀ(β**Φ**ᵀ**Φ**+α𝐈)𝐦N
>
>
>
> ⇔ C = (β/2) 𝐭ᵀ𝐭 - β(𝐦N)ᵀ**Φ**ᵀ𝐭 + (1/2)(𝐦N)ᵀ(β**Φ**ᵀ**Φ**)𝐦N + (1/2)(𝐦N)ᵀ(α𝐈)𝐦N
>
>
>
> ⇔ C = (β/2) 𝐭ᵀ𝐭 - β(𝐦N)ᵀ**Φ**ᵀ𝐭 + (β/2)(𝐦N)ᵀ**Φ**ᵀ**Φm**N + (α/2)(𝐦N)ᵀ𝐦N
>
>
>
> ⇔ C = (β/2) \[𝐭ᵀ𝐭 - 2(𝐦N)ᵀ**Φ**ᵀ𝐭 + (𝐦N)ᵀ**Φ**ᵀ**Φm**N\] +(α/2)(𝐦N)ᵀ𝐦N)
>
>
>
> ⇔ C = (β/2) ||𝐭 - **Φm**N||² + (α/2)(𝐦N)ᵀ𝐦N) → Đặt là E(𝐦N)
>
>
>
> ---
>
>
>
> Kết quả sau khi complete the square ta có: E(𝐰) = E(𝐦N) + (1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)
>
>
>
> ---
>
>
>
> Tác gỉa lưu ý: A chính là Hessian của E(𝐰), kí hiệu ∇∇E(𝐰). Là sao?
>
>
>
> Trả lời đơn giản là vì ta E(𝐰) = (1/2)𝐰ᵀ**Aw** - β𝐰ᵀ**Φ**ᵀ𝐭 + (β/2) 𝐭ᵀ𝐭, Mà với quadratic function của 𝐰: (1/2)𝐰ᵀ**Pw** + **q**ᵀ𝐰 + r, nên với Hessian chính là 𝐏, nên Hessian của E(𝐰) chính là 𝐀.
>
>
>
> ---
>
>
>
> Ý tiếp theo ông Bishop dùng kết quả 3.54 trong đó nói rằng: Khi prior của 𝐰 chọn là N(0, (1/α)𝐈), và dưới mô hình ta giả định T \~ N(𝐰ᵀΦ(𝐱), (1/β)) thì:
>
>
>
> posterior distribution của 𝐰 sẽ là Normal (𝐦N, 𝐒N⁻¹) với:
>
>
>
> 𝐦N = β**S𝐍Φ**ᵀ𝐭 (3.53)
>
>
>
> 𝐒N⁻¹ = α𝐈 + β **Φ**ᵀ**Φ** (3.54)
>
>
>
> Vậy thì ở đây 𝐀 cũng là matrix được ta đặt cho β**Φ**ᵀ**Φ**+α𝐈. Do đó 𝐀 = 𝐒N⁻¹.
>
>
>
> Và như vậy cái mN ta đặt ở trên: 𝐦N = 𝐀inv β**Φ**ᵀ𝐭 sẽ bằng (𝐒N⁻¹)⁻¹ β**Φ**ᵀ𝐭 = 𝐒N β**Φ**ᵀ𝐭 = β**S𝐍Φ**ᵀ𝐭, **CHÍNH LÀ MEAN CỦA POSTERIOR DISTRIBUTION 3.53**

---

🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on

Ghi chú rất chi tiết, tự biến đổi toán học xuất sắc và giải thích rõ ràng mối liên hệ giữa ma trận Hessian với các công thức posterior trước đó. Tuy nhiên, bạn lưu ý một lỗi gõ nhỏ ở bước cuối cùng khi bị thiếu hệ số 1/2 ở thành phần alpha trong công thức của E(m_N).

**🔗 See also:** [Gaussian Prior and Posterior Parameters](./331_bayesian_linear_regression.md#node-nt82rck) · [Section 3.5.2 Maximizing the Evidence Function](./352_maximizing_the_evidence_function.md#node-nc5qxnz)

<br>

<a id="node-ddcs0pi"></a>

#### Log Marginal Likelihood Derivation

<p align="center"><kbd><img src="assets/rj6zq21cue.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, tới đây, quay lại nhiệm vụ chính (nên nhớ ta vẫn đang muốn tính cái tích phân f(𝐭|α,β) = \[(β/2π)^N/2\] \[(α/2π)^M/2\] ∫ exp {-E(𝐰)} d𝐰)
>
>
>
> Xét ∫ exp {-E(𝐰)} d𝐰, thay E(𝐰) = E(𝐦N) + (1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)
>
>
>
> = ∫ exp {-\[E(𝐦N) + (1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰
>
>
>
> = ∫ exp {-\[E(𝐦N) + (1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰
>
>
>
> = ∫ exp {-E(𝐦N) - \[(1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰
>
>
>
> Dùng tính chất hàm mũ, tách ra:
>
>
>
> = ∫ exp {-E(𝐦N)} exp{-\[(1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰
>
>
>
> exp {-E(𝐦N)} không dính 𝐰, đưa ra tích phân
>
>
>
> = exp {-E(𝐦N)} ∫ exp{-\[(1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰
>
>
>
> Viết lại: ∫ exp {-E(𝐰)} d𝐰  = exp {-E(𝐦N)} ∫ exp{-\[(1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰
>
>
>
> ---
>
>
>
> Tới đây sao nữa: Lập luận như sau, xét cái tích phân ∫ exp{-\[(1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰, nó có dạng là kernel của một Normal(𝐦N, 𝐀inv) do đó, bằng cách nhân thêm normalizing constant của pdf này, tạm gọi là C1. 
>
>
>
> Ta sẽ có: (1/C1) ∫ C1 exp{-\[(1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰.  
>
>
>
> Để rồi do tính valid của pdf, ∫ C1 exp{-\[(1/2)(𝐰 - 𝐦N)ᵀ𝐀(𝐰 - 𝐦N)\]} d𝐰 phải bằng 1.
>
>
>
> nên ∫ exp {-E(𝐰)} d𝐰 = exp {-E(𝐦N)} (1/C1), chỉ việc thay C1 vô, C1 là gì?
>
>
>
> theo công thức pdf D-dimensional Normal(𝐱|**μ**, **Σ**) = \[(2π)^-D/2\] \[1/|**Σ**|^1/2\] exp\[(𝐱 - **μ**)ᵀ**Σ**inv(𝐱 - μ)/2\], thì normalizing constant C1 của M-dimensional Normal (vì 𝐰 có M phần tử) ở đây chính là:
>
>
>
> C1 = \[(2π)^-M/2\] (|𝐀inv|^-1/2) 
>
>
>
> ⇒ ∫ exp {-E(𝐰)} d𝐰 = exp {-E(𝐦N)} \[(2π)^M/2\] (|𝐀inv|^1/2)
>
>
>
> Nhớ tính chất det matrix đã học trong MIT 1806: |A⁻¹| = 1/|A|, nên:
>
>
>
> ∫ exp {-E(𝐰)} d𝐰 = exp {-E(𝐦N)} \[(2π)^M/2\] (|𝐀|^-1/2) → 3.85
>
>
>
> ---
>
>
>
> Vậy f(𝐭|α,β) = \[(β/2π)^N/2\] \[(α/2π)^M/2\] ∫ exp {-E(𝐰)} d𝐰)
>
>
>
> ⇔ f(𝐭|α,β) = \[(β/2π)^N/2\] \[(α/2π)^M/2\] exp {-E(𝐦N)} \[(2π)^M/2\] (|𝐀|^-1/2)
>
>
>
> ⇒ ln f(𝐭|α,β) = ln { \[(β/2π)^N/2\] \[(α/2π)^M/2\] exp {-E(𝐦N)} \[(2π)^M/2 (|𝐀|^-1/2)\]
>
>
>
> = ln \[(β/2π)^N/2\] + ln \[(α/2π)^M/2\] + ln \[exp {-E(𝐦N)} \[(2π)^M/2 (|𝐀|^-1/2)\]
>
>
>
> = (N/2) ln (β/2π) + (M/2) ln (α/2π) + ln \[exp {-E(𝐦N)}\] + ln \[(2π)^M/2 (|𝐀|^-1/2)\]
>
>
>
> = (N/2) \[ln (β) - ln(2π)\] + (M/2) \[ln(α) - ln (2π)\] - E(𝐦N) + ln \[(2π)^M/2\] + ln \[(|𝐀|^-1/2)\]
>
>
>
> = (N/2) ln (β) - (N/2) ln(2π) + (M/2) ln(α) - (M/2) ln (2π) - E(𝐦N) + (M/2) ln (2π) -1/2 ln |𝐀|
>
>
>
> = (N/2) ln (β) - (N/2) ln(2π) + (M/2) ln(α)  - E(𝐦N) - 1/2 ln |𝐀|
>
>
>
> = (M/2) ln(α) + (N/2) ln (β) + - E(𝐦N) - 1/2 ln |𝐀|  - (N/2) ln(2π) 
>
>
>
> Đây là kết quả 3.86

---

🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on

Ghi chú của bạn cực kỳ chi tiết, mạch lạc và chính xác tuyệt đối trong từng bước biến đổi toán học để chứng minh (3.85) và (3.86). Việc giải thích tường minh hằng số chuẩn hóa Gaussian và cách triệt tiêu các đại lượng logarit là một điểm cộng rất lớn giúp người đọc dễ dàng theo kịp.


### Điểm mạnh
- **Hiểu sâu bản chất toán học:** Bạn đã nhận diện rất tốt phần nhân (kernel) của phân phối Gaussian nhiều chiều và dùng phương pháp nhân/chia hằng số chuẩn hóa để giải tích phân một cách thông minh mà không cần tính toán trực tiếp phức tạp.
- **Biến đổi đại số chính xác:** Quá trình khai triển hàm logarit của tích các số hạng ở công thức (3.86) được thực hiện rất cẩn thận, từng bước rõ ràng và triệt tiêu chính xác các số hạng đối nhau như $\frac{M}{2}\ln(2\pi)$.
- **Liên kết kiến thức thực tế:** Áp dụng rất tốt tính chất định thức của ma trận nghịch đảo $|\mathbf{A}^{-1}| = |\mathbf{A}|^{-1}$ từ kiến thức hình học/đại số tuyến tính.

### Điểm cần lưu ý và cải thiện
- **Ký hiệu tạm thời dễ gây nhầm lẫn:** Ở dòng gần giữa bài viết, bạn có ghi: 
  `⇒ f(t|α,β) = exp {-E(mN)} [(2
u)^M/2] (|Ainv|^1/2)`
  Thực chất đây mới chỉ là giá trị của tích phân $\int \exp\{-E(\mathbf{w})\} \mathrm{d}\mathbf{w}$ chứ chưa phải là marginal likelihood $f(\mathbf{t}|\alpha, \beta)$. Dù ngay dòng dưới bạn đã sửa lại và nhân thêm các hệ số chuẩn hóa của $t$ để ra $f(\mathbf{t}|\alpha,\beta)$ chính xác, nhưng việc viết nhầm ký hiệu ở bước trung gian có thể gây bối rối khi đọc lại sau này.

### Gợi ý phát triển thêm
- Hãy tìm hiểu thêm về ý nghĩa của ma trận $\mathbf{A}$ trong ngữ cảnh này. Ma trận $\mathbf{A}$ chính là ma trận Hessian (đạo hàm bậc hai) của hàm năng lượng $E(\mathbf{w})$ tại điểm cực trị $\mathbf{m}_N$. Việc tính tích phân này thực chất là một bước trong phương pháp **Xấp xỉ Laplace (Laplace Approximation)** để xấp xỉ phân phối posterior dưới dạng phân phối chuẩn.

> [!TIP]
> - Áp dụng chính xác tính chất định thức của ma trận nghịch đảo để đơn giản hóa biểu thức chứa ma trận A.
> - Liên hệ thành công phương pháp tính tích phân bằng cách đưa về hàm mật độ xác suất Gaussian chuẩn hóa.

**🔗 See also:** [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj) · [Section 3.5.2 Maximizing the Evidence Function](./352_maximizing_the_evidence_function.md#node-nc5qxnz)

<br>

<a id="node-4tg7rkk"></a>

##### Figure 3.14 Model Evidence Plot

<p align="center"><kbd><img src="assets/v3ef393hnoa.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/9i5l4yymze8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hftb50pdlsb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/uux1eh20za.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4o7z8kl333x.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp tục phần cuối, dựa vào kết quả ta đã có của ln f(𝐭|α, β) = (M/2) ln(α) + (N/2) ln (β) - E(𝐦N) - 1/2 ln |𝐀| - (N/2) ln(2π), gs mới ốp vào bài toán polynomial curve fitting đã học.
>
>
>
> Trước hết mình sẽ nói lại tí về ý nghĩa của f(𝐭|α, β), là model evidence, hay marginal likelihood, mà như các note trước mình đã hiểu bản chất của nó chính là: f(𝒟|**ℳ**i), hay f(𝐭|ℳi,𝐗) với ℳi là mô hình cụ thể trong đó ta cho T \~ n(y(𝐰,𝐱), 1/β). Và f(𝒟|**ℳ**i) = f(𝐭|ℳi,𝐗) được hiểu là kết quả có được khi ta marginalizing f(𝒟|**ℳ**i, 𝐰) = f(t|ℳi, 𝐰, 𝐗) over mọi possible value của 𝐰, với 𝐰 \~ n(0, 1/α)𝐈).
>
>
>
> Do đó f(𝒟|**ℳ**i), cũng là f(𝐭|ℳi,𝐗), và viết thêm sự phụ thuộc vào α, β ta có f(𝐭|ℳi, α, β, 𝐗), cũng như bỏ đi ℳi, 𝐗 cho gọn (vì đã xét ℳi cụ thể cũng như tự biết sẽ phải phụ thuộc 𝐗) ta sẽ có f(𝐭|α, β). Và bản chất của nó mang ý nghĩa là: Giả định mô hình phân phối của data là ℳi, với tham số 𝐰 có giả định prior như vậy, thì khi ta lấy trung bình trên mọi giá trị của 𝐰, thì xác suất quan sát được bộ data set 𝒟 là bao nhiêu.
>
>
>
> Vậy thì với việc ta đã ra được kết quả:
>
>
>
> ln f(𝐭|α, β) = (M/2) ln(α) + (N/2) ln (β) - E(𝐦N) - 1/2 ln |𝐀| - (N/2) ln(2π). Người ta mới vẽ nó là hàm theo M, để có hình 3.14. Và tương ứng với hình 1.4, 1.4 Ta sẽ có thể giải thích bản chất.
>
>
>
> Đầu tiên, nhìn vào công thức ta vừa làm, phân tích một chút như sau:
>
>
>
> (M/2) ln(α) + (N/2) ln (β) - E(𝐦N) - 1/2 ln |𝐀| - (N/2) ln(2π)
>
>
>
> = - E(𝐦N) + (M/2) ln(α) + (N/2) ln (β) - 1/2 ln |𝐀| - (N/2) ln(2π)
>
>
>
> = - (β/2) ||𝐭 - **Φm**N||² - (α/2) 𝐦Nᵀ𝐦N + (M/2) ln(α) + (N/2) ln (β) - 1/2 ln |𝐀| - (N/2) ln(2π)
>
>
>
> Xét term - (β/2) ||𝐭 - **Φm**N||² = - (β/2) ||𝐭 - **Φm**N||²:
>
>
>
> Với 𝐦N = β**S𝐍Φ**ᵀ𝐭 mà ta nhận định chính là posterior mean của 𝐰, thì **Φm**N chính là gì? Chính là **Φw**MAP, và - (1/2) ||𝐭 - **Φm**N||² chính là sum squared error của mô hình khi dùng 𝐰MAP để lắp vào hàm dự đoán y(𝐰, 𝐱) = 𝐰ᵀΦ(𝐱). Và bữa trước ta cũng đã biết, khi có posterior distribution của 𝐰, thì một cách point estimate tốt cho 𝐰 là dùng 𝐰MAP (mà ta gọi là làm Bayesian kiểu nửa mùa đó).
>
>
>
> Như vậy - (β/2) ||𝐭 - **Φm**N||² chính là (negative) của β × sum square error. Dĩ nhiên khi model fit data càng tốt thì sum square error càng nhỏ → - (β/2) ||𝐭 - **Φm**N||² càng bớt âm, đồng nghĩa sẽ kéo f(𝐭|α, β) tăng lên.
>
>
>
> ---
>
> Xét -(α/2) 𝐦Nᵀ𝐦N = -(α/2) ||𝐦N||², đây chỉ là penalty của regularization loss khi dùng 𝐰MAP, đương nhiên nó là norm của vector 𝐰MAP, nên nếu M càng lớn, thì norm vector cũng sẽ tăng, từ đó dấu trừ phía trước sẽ kéo cục này giảm, do đó, kéo f(𝐭|α, β) giảm
>
>
>
> Xét - 1/2 ln |𝐀|. Thì 𝐀 như đã nói ở note trước, chính là nghịch đảo covariance của posterior của 𝐰, hay, chính là posterior precision matrix. Khi M càng lớn, thì det của matrix covariance đương nhiên càng nhỏ (vì càng nhiều data thì phương sai hậu nghiệm sẽ nhỏ lại → det càng nhỏ → det precision matrix |𝐀| càng lớn → ln |𝐀| sẽ càng lớn , và thêm dấu trừ đằng trước thì - 1/2 ln |𝐀| sẽ càng nhỏ 
>
>
>
> Xét (M/2) ln(α), với α là số nhỏ, thì ln α âm, khiến term này nó cũng sẽ nhỏ lại khi M lớn lên.
>
>
>
> Như vậy, tóm lại, khi M thay đổi trong công thức của model evidence có hai phe đấu đá nhau: 
>
>
>
> Khả năng fit của model tăng sẽ kéo sum square error nhỏ xuống → tăng model evidence. Nhưng M tăng sẽ khiến các term khác kéo model evidence tăng lên, và chúng mang ý nghĩa sẽ phạt mô hình phức tạp (M lớn)
>
>
>
> Và điều này giúp ta giải thích các hình đồ thị như sau:
>
>
>
> Khi M nhỏ, = 0, 1.4 cho thấy một model quá đơn giản (constant), không khớp tốt data → SSE lớn → model evidence nhỏ.
>
>
>
> Nguyên lí chung khi M tăng lên, lực kéo model evidence xuống sẽ tăng liên tục, nên ăn thua là xem lực kéo lên do giảm SSE có đủ để bù hay không.
>
>
>
> Khi M tăng lên 1, nó khớp tốt hơn data, giúp kéo SSE xuống và dù M tăng lên cũng khiến phe kia kéo model xuống nhưng sự tăng của phe SSE vượt trội → model evidence tăng lên (cái đỉnh thứ nhất của hình 3.14)
>
>
>
> Khi M tăng lên 2, dựa trên sự thật là data sinh ra từ hàm sin, có bản chất là hàm lẻ, nên hiểu đại khái là dùng polynomial bậc hai (w0 + w1x + wx²) không giúp tạo ra model fit tốt hơn hơn data này. Do đó, SSE ko giảm bao nhiêu → không kéo model evidence lên bao nhiêu dẫn lực kéo lên bị yếu thế so với lực kéo model xuống → model evidence bị kéo xuống, tạo nên cái thung lũng ở hình 3.14.
>
>
>
> Khi M tăng lên 3, với bậc 3, hàm đa thức fit tốt data sinh ra bởi hàm sin, thành ra, SSE giảm mạnh, lực kéo lên vượt trội, khiến 3.14 tạo đỉnh thứ hai (cao nhất). Hình 1.4 ta thấy đường cong bậc 3 màu đỏ khớp khá tốt đường màu xanh.
>
>
>
> Khi M tăng lên 4 và hơn nữa, SSE không giảm bao nhiêu, lực kéo lên bắt đầu thua, model evidence bắt đầu đi xuống liên tục. Và với M = 9, thì phe kéo model xuống để phạt model có M cao đã vượt xa lực kéo lên của SSE, model evidence giảm rất thấp. Và đây chính là khi model bị overfit với hình 1.4 cuối, nó đi qua hết data perfectly nhưng hoàn toàn không capture được đường hình sin.
>
>
>
> Và như vậy câu chốt một ý quan trọng, đó là nếu chỉ nhìn hình 1.5, ta sẽ thấy khi M = 3 → 7, thì ra sẽ ko biết nên dùng M bao nhiêu (vì khi dựa vào test performance (màu đỏ), nó đi ngang. Nhưng nếu dùng hình 3.14 thì rõ ràng là ta sẽ chọn M = 3, nơi có model evidence cao nhất.

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Ghi chép cực kỳ xuất sắc, giải thích rất sâu sắc và chính xác bản chất toán học của các thành phần trong công thức model evidence cùng sự liên hệ hoàn hảo với các đồ thị. Để hoàn thiện hơn, bạn có thể giải thích rõ hơn về mặt toán học tại sao định thức của ma trận precision A tăng lên khi số chiều M tăng.

<br>

