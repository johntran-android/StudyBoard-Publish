# 2.4.1 Maximum likelihood & sufficient statistic

📊 **Progress:** `4` Notes | `4` Screenshots | `3` AI Reviews

---
<a id="node-niekuox"></a>

<p align="center"><kbd><img src="assets/7swge4ekywk.png" width="80%"></kbd></p>

> [!NOTE]
> Qua phần này, ta sẽ bàn về việc estimate parameter **η** của exponential family thông qua phương pháp MLE. Cũng đã quen với MLE, chỉ nhắc lại nha, MLE vốn dĩ là một trong các phương pháp để giải bài toán point estimation - là một trong những bài toán suy luận thống kê: Cho random sample 𝐗 = (X1,...Xn), có giá trị quan sát được là 𝐱 = (x1,x2,...xn), là các random varialle independent & identically distributed - iid \~ f(𝐱|θ) (θ là parameter của population distribution). Nhiệm vụ của bài toán point estimation là tìm một hàm W(𝐗), để với giá trị quan sát được của 𝐗: 𝐗 = 𝐱, thì W(𝐱) sẽ là estimate tốt cho θ. Phải nói thêm, với cách tiếp cận MLE, thì nó thuộc trường phái Classic hay Frequentist, vì ta chỉ xem θ như giá trị cố định nhưng chưa biết, chứ không xem nó như biến ngẫu nhiên.
>
>
>
> Vậy thì theo sách Casella, estimator, có thể là bất kì function nào của sample, và với một định nghĩa mơ hồ như vậy, ta cần có những phương pháp tiếp cận để dẫn đến một estimator tốt, và tiêu biểu là MoM (method of moment). MLE (maximum likelihood estimator) và Bayes estimator. Thế thì, với MLE, nói ngắn gọn, cái hàm W(𝐗) mà ta dùng sẽ là hàm số sau: W(𝐱) = argmax (over θ) L(θ|𝐱), với L(θ|𝐱) là likelihood function, là hàm số theo θ, được define (có giá trị bởi) f(𝐱|θ), tức giá trị của likelihood L(θ|𝐱) tại θ được tính bằng giá trị của joint pdf của sample tại observed value 𝐱. 
>
>
>
> (Chú ý, L(θ|𝐱) cũng chính là L(θ|(x1,x2,...xn), và f(𝐱|θ) cũng là f(x1,x2,...xn|θ), mà nhờ tính chất iid sẽ tách thành f(x1|θ)f(x2|θ)...f(xn|θ))
>
>
>
> Và viết W(𝐱) = argmax (over θ) L(θ|𝐱) có ý nghĩa là ta sẽ giải bài toán tối ưu: maximize over θ L(θ|𝐱), cũng là maximize f(𝐱|θ), cũng là f(x1,x2,...xn), và với tính chất iid của X1,...Xn, thì f(𝐱|θ) = f(x1,...xn|θ) có thể được tách thành tích các marginal pdf: f(𝐱|θ) = f(x1,...xn|θ) = f(x1|θ) × f(x1|θ) × .. f(xn|θ) = Πi=1:n f(xi|θ)
>
>
>
> Quay lại đây, express theo cái khung của bài toán point estimation trên thì ta sẽ nói thế này: cho 𝐗1, ...𝐗N là iid \~ f(𝐱|**η**), và muốn tìm ML estimator cho **η**. Thì theo định nghĩa, likelihood function là hàm theo **η**, được define bởi giá trị của joint pdf của sample tại observed value. do đó, likelihood tại **η**, kí hiêu7 tính bằng f(𝐱1, 𝐱2,....𝐱N|**η**). Hay gom các random vector 𝐗1, ...𝐗N, lại thành random matrix 𝐗, có observed value là 𝐱, hay mình ghi là \[**matrix x**\] cho dễ phân biệt.
>
>
>
> Khi đó, likelihood sẽ kí hiệu là L(**η**|\[**matrix** 𝐱\]) = f(\[**matrix x**\]|**η**) = f(𝐱1,𝐱2,..,𝐱N|**η**) = f(𝐱1|**η**)f(𝐱2|**η**)...f(𝐱N|**η**) = Πi=1:N f(𝐱i|**η**).
>
>
>
> Nên bài toán tối ưu cần giải để có MLE của **η** là:
>
>
>
> maximize over **η** {Πi=1:N f(𝐱i|**η**)} với f(𝐱i|**η**) = h(𝐱i)g(**η**)exp{**η**ᵀ𝐮(𝐱i)}
>
>
>
> (trong sách, gs Bishop dùng 𝐗 để chỉ observed value của mọi sample, tức là tương ứng \[**matrix x**\] của mình, (vì đã nói nhiều lần, gs Bishop ko theo chuẩn kí hiệu thông thường, việc dùng X rất dễ gây lầm lẫn là một random vector X nào đó)
>
>
>
> ---
>
>
>
> Quay lại đây, trước khi giải, đầu tiên gs Bishop sẽ chuẩn bị cho việc giải bài toán này, bằng cách dùng tính chất:
>
>
>
> ∫f(𝐱|**η**) d𝐱 = 1, để rồi, đạo hàm hai vế thế **η**, ta sẽ có một kết quả đó là - ∇ln g(**η**) = E\[u(𝐱)\] đặng tí nữa dùng. Thử xem các bước như thế nào mà ra kết quả này:
>
>
>
> ∫f(𝐱|**η**) d𝐱 = 1
>
>
>
> ⇨ d/d**η** \[∫f(𝐱|**η**) d𝐱\] = d/d**η** \[1\]
>
>
>
> ⇔ d/d**η** \[∫h(𝐱)g(**η**)exp{**η**ᵀ𝐮(𝐱)} d𝐱\] = 0
>
>
>
> ⇔ d/d**η** \[g(**η**) ∫h(𝐱)exp{**η**ᵀ𝐮(𝐱)} d𝐱\] = 0
>
>
>
> Dùng product rule:
>
>
>
> ⇔ d/d**η** \[g(**η**)\] × ∫h(𝐱)exp{**η**ᵀ𝐮(𝐱)} d𝐱\] + g(**η**) d/d**η**\[∫h(𝐱)exp{**η**ᵀ𝐮(𝐱)} d𝐱\] = 0
>
>
>
>  ⇔ ∇g(**η**) × ∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} d𝐱 + g(**η**) × d/d**η**\[∫h(𝐱)exp{**η**ᵀ𝐮(𝐱)} d𝐱\] = 0
>
>
>
> Xét cái d/d**η**\[∫h(𝐱)exp{**η**ᵀ𝐮(𝐱)} d𝐱\] trong term thứ 2: Đây là ta đang đạo hàm theo η của một cái tích phân theo 𝐱, được phép đưa đạo hàm vào trong, vì biên của tích phân không phụ thuộc **η**, cái này giống như ta đạo hàm theo **η** của một cái tổng các hàm số thôi.
>
>
>
> d/d**η**\[∫h(𝐱)exp{**η**ᵀ𝐮(𝐱)} d𝐱\] = ∫d/d**η**\[h(𝐱)exp{**η**ᵀ𝐮(𝐱)}\] d𝐱
>
>
>
> = ∫h(𝐱) d/d**η**\[exp{**η**ᵀ𝐮(𝐱)}\] d𝐱
>
>
>
> Dùng chain rule: d/d**η**\[exp{**η**ᵀ𝐮(𝐱)}\] = d/d\[**η**ᵀ𝐮(𝐱)\]\[exp{**η**ᵀ𝐮(𝐱)}\] . d/d**η** \[**η**ᵀ𝐮(𝐱)\]
>
>
>
> = ∫h(𝐱) d/d\[**η**ᵀ𝐮(𝐱)\]\[exp{**η**ᵀ𝐮(𝐱)}\] . d/d**η** \[**η**ᵀ𝐮(𝐱)\] d𝐱
>
>
>
> Dùng đạo hàm hàm sơ cấp: d/dx e^x = e^x, d/dx xᵀa = a
>
>
>
> = ∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} 𝐮(𝐱)d𝐱
>
>
>
> Vậy kết qủa tới đây là:
>
>
>
> ∇g(**η**) × ∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} d𝐱 + g(**η**)∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} 𝐮(𝐱)d𝐱 = 0 → đây là 2.224
>
>
>
>  ⇔ ∇g(**η**) \[1/g(**η**)\] g(**η**) ∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} d𝐱 = - g(**η**)∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} 𝐮(𝐱)d𝐱
>
>
>
> Dùng tiếp cái kết quả 2.195: g(**η**)∫h(𝐱)exp{**η**ᵀ𝐮(𝐱)} d𝐱 d𝐱 = 1
>
>
>
> ⇔ ∇g(**η**) \[1/g(**η**)\] × 1 = - g(**η**)∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} 𝐮(𝐱)d𝐱
>
>
>
>  ⇔ -\[1/g(**η**)\] ∇g(**η**) = g(**η**)∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} 𝐮(𝐱)d𝐱
>
>
>
> và đồng thời nhận định vế phải chính là gì?
>
>
>
> g(**η**)∫h(𝐱) exp{**η**ᵀ𝐮(𝐱)} 𝐮(𝐱)d𝐱 = ∫h(𝐱) g(**η**) exp{**η**ᵀ𝐮(𝐱)} 𝐮(𝐱)d𝐱 chính là = ∫𝐮(𝐱)f(𝐱|**η**)d𝐱, còn nhớ kiến thức về LOTUS, khi ta có X \~ pdf f(x), và Y = g(X), thì EY = Eg(X) = ∫g(x)f(x)dx. Nên tương tự, ta sẽ thấy ở đây cái ta đang có chính là E\[u(𝐗)\]
>
>
>
> Vậy -\[1/g(**η**)\] ∇g(**η**) = E\[𝐮(𝐗)\]
>
>
>
> Và vế trái, lại là - d/d**η** ln g(**η**), vì theo chain rule, - d/d**η** ln g(**η**) = - d/dg(**η**) ln g(**η**) . d/d**η** g(**η**) = - 1/g(**η**) ∇g(**η**).
>
>
>
> Vậy ta có kết quả để dành tí nữa xài: - 1/g(**η**) ∇g(**η**) = E\[𝐮(𝐗)\] → 2.226
>
>
>
> (nhiệm vụ của ta vẫn là giải bài toán tối ưu: maximize ln L(**η**|𝐱))

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Phân tích cực kỳ chi tiết và sâu sắc, giải thích rõ ràng từng bước trong quá trình suy luận và các quy tắc toán học áp dụng, vượt xa nội dung được trình bày trong hình ảnh gốc. Độ chính xác cao và kiến thức nền được củng cố vững chắc.

**🔗 See also:** [2.4 The Exponential Family](./24_the_exponential_family.md#node-1hlelhn)

<br>

<a id="node-z1b3dzz"></a>

## Moments by Differentiation

<p align="center"><kbd><img src="assets/vmb0w0netqn.png" width="80%"></kbd></p>

> [!NOTE]
> Quay lại ý này sau

<br>

<a id="node-fm5kia1"></a>

### Maximum Likelihood Estimator Condition

<p align="center"><kbd><img src="assets/g76tikenfww.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, tiếp tục, như đã nói, ta sẽ giải bài toán maximize  L(**η**|\[**matrix x**\]), cũng là
>
>
>
> maximize over η {ln Πi=1:N f(𝐱i|**η**)}
>
>
>
> Xét hàm likelihood, L(η|\[**matrix x**\]) = Πi=1:N f(𝐱i|**η**)
>
>
>
> thay công thức vô:
>
>
>
> = Πi=1:N h(𝐱i)g(**η**)exp\[**η**ᵀ𝐮(𝐱i)\]
>
>
>
> = \[Πi=1:N h(𝐱i)\] \[g(**η**)\]^N {Πi=1:N exp\[**η**ᵀ𝐮(𝐱i)\]}
>
>
>
> = \[Πi=1:N h(𝐱i)\] \[g(**η**)\]^N exp{∑i=1:N\[**η**ᵀ𝐮(𝐱i)\]} → đây là 2.227
>
>
>
> Và bài toán maximize likelihood sẽ equivalient maximize ln likelihood
>
>
>
> Hàm ln likelihood:
>
>
>
> = ln \[Πi=1:N h(𝐱i)\] \[g(**η**)\]^N exp{∑i=1:N\[**η**ᵀ𝐮(𝐱i)\]}
>
>
>
> = ln \[Πi=1:N h(𝐱i)\]  + ln \[g(**η**)\]^N  + ln exp{∑i=1:N\[**η**ᵀ𝐮(𝐱i)\]}
>
>
>
> = ln \[Πi=1:N h(𝐱i)\]  + N ln \[g(**η**)\]  + ∑i=1:N\[**η**ᵀ𝐮(𝐱i)\]
>
>
>
> bài toán maximize ln likelihood tiếp tục tương đương với: 
>
>
>
> maximize (over η) {N ln \[g(**η**)\] + ∑i=1:N\[**η**ᵀ𝐮(𝐱i)\] (tức là ta bỏ constant ln \[Πi=1:N h(𝐱i)\] đi)
>
>
>
> Tới đây, dùng first order neccessary condition, cho gradient (đạo hàm theo η) của objective bằng 0 để giải ra stationary point (sau đó cần check secondary test để xác nhận là cực tiểu hay cực đại, theo kiến thức đã học ở MIT 18.01). Vậy đầu tiên tính gradient:
>
>
>
> d/dη \[N ln \[g(**η**)\] + ∑i=1:N\[**η**ᵀ𝐮(𝐱i)\]
>
>
>
> = N d/dη \[ln \[g(**η**)\] + d/dη ∑i=1:N\[**η**ᵀ𝐮(𝐱i)\]
>
>
>
> = N \[1/g(**η**)\] ∇g(**η**) + ∑i=1:N d/dη \[**η**ᵀ𝐮(𝐱i)\]
>
>
>
> = N \[∇g(**η**)/g(**η**)\]  + ∑i=1:N d/dη 𝐮(𝐱i)
>
>
>
> cho cái này bằng 0:
>
>
>
> N \[∇g(**η**)/g(**η**)\] + ∑i=1:N 𝐮(𝐱i) = 0
>
>
>
> ⇔ N \[-∇g(**η**)/g(**η**)\] = ∑i=1:N 𝐮(𝐱i) 
>
>
>
> ⇔  \[-∇g(**η**)/g(**η**)\] = (1/N) ∑i=1:N 𝐮(𝐱i) 
>
>
>
> → đây chính là 2.228 (vì ta đã thay d/dη \[ln \[g(**η**)\] = ∇g(**η**)/g(**η**))

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Bài giải cực kỳ chi tiết, chính xác và thể hiện sự hiểu biết sâu sắc về các bước tính toán từ hàm likelihood đến điều kiện đạo hàm bằng 0. Cách bạn tách rời các thành phần và áp dụng quy tắc logarit, cùng với việc nhận diện hằng số, là rất ấn tượng. Chỉ có một chi tiết nhỏ về ký hiệu đạo hàm của tổng có thể được làm rõ hơn, nhưng kết quả cuối cùng hoàn toàn đúng.

<br>

<a id="node-5ny151v"></a>

#### Sufficient Statistic Property

<p align="center"><kbd><img src="assets/bln6x5jci7l.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy thì đại khái là từ kết quả ta đã có \[-∇g(**η**)/g(**η**)\] = (1/N) ∑i=1:N u(xi), có nghĩa là, giải cái này ra ta sẽ tìm được stationary **η**, và hàm - ln likelihood, có thể chứng minh là convex, nên **η** này cũng chính là maximizer của nó → ta có maximum likelihood **η**ML. (gs Bishop ko nói gì, nhưng phải hiểu, điều kiện gradient = 0 chưa đủ để kết luận η thỏa cái gradient = 0 là maximizer, phải check thêm đạo hàm bậc hai hoặc lập luận chỉ ra hàm objective là hàm lồi)
>
>
>
> Vậy thì, có thể thấy, **η**ML chỉ là hàm phụ thuộc ∑i u(xi), và đây lại chính là một sufficient statistic. Cái này mình đã nói trước đây (xem link) trong Casella, đã học đại khái là, nếu một statistic T(𝐗) được định nghĩa là nếu T(𝐗) có tính chất đó là khiến f(𝐱|T(𝐗) = T(𝐱)) không còn là hàm phụ thuộc θ, thì nó chính là sufficient statistic. Và nhờ Factorization theorem nói rằng nếu pdf f(𝐱|θ) có thể tách thành g(T(𝐱)|θ)h(𝐱), tức một hàm h(𝐱) ko phụ thuộc θ chỉ phụ thuộc 𝐱, và hàm g phụ thuộc cả θ và 𝐱 nhưng chỉ phụ thuộc 𝐱 thông qua một statistic T(𝐱) thì T(𝐗) chính là sufficient statistic.
>
>
>
> Vậy thì xét joint pdf của sample:
>
>
>
> f(\[matrix 𝐗\]|**η**) = Πi=1:N f(𝐱i|**η**)
>
>
>
> = Πi=1:N h(𝐱i)g(**η**)exp{ηTu(𝐱i)}
>
>
>
> = \[Πi=1:N h(𝐱i)\] \[g(**η**)\]^N Πi=1:N exp{**η**ᵀu(𝐱i)}
>
>
>
> = \[Πi=1:N h(𝐱i)\] \[g(**η**)\]^N exp{∑i=1:N **η**ᵀu(𝐱i)}
>
>
>
> = \[Πi=1:N h(𝐱i)\] \[g(**η**)\]^N exp{**η**ᵀ\[∑i=1:N u(𝐱i)\]}
>
>
>
> ta thấy đúng là có thể tách thành h(𝐱) g(T(𝐱), **η**) với:
>
>
>
> h(𝐱) = h(x1,x2...xN) = \[Πi=1:N h(xi)\]
>
>
>
> T(𝐱) = T(x1, x2, ...xN) = ∑i=1:N u(xi)
>
>
>
> Do đó, theo **Factorization theorem**, T(X1,X2,...) ∑i=1:N u(Xi) **chính là sufficient statistic**.
>
>
>
> Và trong Casella mình đã biết ý nghĩa của sufficient statistic, đó là **inference về θ dựa trên một sufficient statistic T(x) cũng y như inference về θ dựa trên sample X**. Và thường thì sufficient statistic có kích thước nhỏ hơn sample X, nên ta có thể dùng T(x), vất bỏ đi observed data x.
>
>
>
> Làm cụ thể với Bern(μ) distribution, f(𝐱|μ) = Πi=1:N f(xi|μ) = Πi=1:N μ^xi ×(1-μ)^(1-xi)
>
>
>
> = Πi=1:N {(1-μ) exp {ln\[μ/(1-μ)\] x} (chuyển pmf của Bern(μ) về dạng exponential family, kết quả bữa trước)
>
>
>
> = (1-μ)ⁿ Πi=1:N exp {ln\[μ/(1-μ)\] xi}
>
>
>
> = (1-μ)ⁿ exp {∑i=1:N ln\[μ/(1-μ)\] xi}
>
>
>
> = (1-μ)ⁿ exp {ln\[μ/(1-μ)\] ∑i=1:N xi}
>
>
>
> kết qủa này có dạng h(𝐱)g(T(𝐱), μ) với h(𝐱) = 1, g(T(𝐱), μ) = (1-μ)ⁿ exp {ln\[μ/(1-μ)\] ∑i=1:N xi}, và T(𝐱) = ∑i=1:N xi
>
>
>
> Do đó theo Factorization theroerm, đối với Bern(μ) thì sufficient statistic là ∑i=1:N xi, → nên gs Bishop nói với Bern distribution thì ta chỉ cần giữ lại tổng của các data point.
>
>
>
> Còn với Normal, pdf (đã triển khai) = ..
>
>
>
> f(x|μ, σ²) = \[1/√(2πσ²)\] exp{-μ²/2σ²} exp{(-1/2σ²)x²+(μ/σ²)x}
>
>
>
> ⇨ f(𝐱|μ, σ²) = Πi=1:n f(xi|μ, σ²)
>
>
>
> = Πi=1:n { \[1/√(2πσ²)\] exp{-μ²/2σ²)} exp{(-1/2σ²)xi²+(μ/σ²)xi}}
>
>
>
> = \[1/√(2πσ²) exp{-μ²/2σ²)}\]ⁿ exp{∑i=1:n(-1/2σ²)xi² + ∑i=1:n(μ/σ²)xi}
>
>
>
> = \[1/√(2πσ²) exp{-μ²/2σ²)}\]ⁿ exp{(-1/2σ²)∑i=1:n xi² + (μ/σ²)∑i=1:nxi}
>
>
>
> Kết quả này có dạng h(𝐱)g(T(x), μ, σ²)
>
>
>
> với h(𝐱) = 1
>
>
>
> g(T(𝐱), μ, σ²) = \[1/√(2πσ²) exp{-μ²/2σ²)}\]ⁿ exp{(-1/2σ²)∑i=1:n xi² + (μ/σ²)∑i=1:nxi}
>
>
>
> và T(𝐱) = (∑i=1:n xi², ∑i=1:nxi)
>
>
>
> Nên theo Factorization theorem, sufficient statistic là T(𝐗) = \[∑i=1:n 𝐗i², ∑i=1:n 𝐗i\]
>
>
>
> do đó gs Bishop nói với Normal ta cần giữ lại cả tổng xi và tổng bình phương xi là vậy (should keep both the sum of {xn} and the sum of {xn²})
>
>
>
>
>
>  Một ý nữa, đại ý là lúc nãy ta đã đi đến kết quả này:
>
>
>
>   Kết quả 2.226: ∇g(**η**)/g(**η**) = E\[u(𝐗)\]
>
>
>
> còn ở note trước ta có ηML sẽ thỏa: \[-∇g(**η**)/g(**η**)\] = (1/N) ∑i=1:N u(𝐱i)
>
>
>
> Evaluate hai vế của phương trình trên tại limit N → inf:
>
>
>
> lim N→∞ \[-∇g(**η**ML)/g(**η**ML)\] = lim N→∞ \[(1/N) ∑i=1:N u(𝐱i)\]
>
>
>
> Vế phải, cái ta có chính là sample mean size n: u_bar_n, theo luật số lớn (WLLN, Weak Law Of Large Number đã học trong Casella), bất kì Xbar_n = (Σi=1:n Xi)/n nào đều hội tự về population mean E\[Xi\].
>
>
>
> Nên lim N→∞ \[(1/N) ∑i=1:N u(xi)\] = E\[u(xi)\].
>
>
>
> như vậy lim N→∞ \[-∇g(**η**ML)/g(**η**ML)\] = ∇g(η)/g(η), điều này cho thấy **η**ML converge về **η**, tức population parameters. Và điều này có nghĩa là gì?
>
>
>
> Như đã học về khái niệm consistency trong Casella, định nghĩa của cái gọi là một chuỗi các estimator có tính nhất quán (consistent) đó là nếu như Wn thỏa: lim n → inf P\_θ(|Wn - θ| < ε) = 1. Mang ý nghĩa là khi kích thước mẫu tăng lên vô hạn thì xác suất mà estimator khác với θ sẽ cực kì nhỏ, hay, xác suất estimator sẽ có giá trị chính xác với θ là cực lớn.
>
>
>
> Nôm na là, lim n → inf Wn(x) = θ
>
>
>
> khi đó thì chuỗi Wn(𝐗) được gọi là một sequence of **consistent** estimator của θ. Vậy thì ở đây, dựa trên kiến thức này, ta thấy ML estimator của **η**, tức **η**ML chính là một consistent estimator của **η**.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Bài phân tích rất chi tiết, sâu sắc và chính xác, chứng minh rõ ràng các khái niệm bằng Định lý Factorization và áp dụng cụ thể cho các phân phối. Bạn thể hiện sự hiểu biết vững chắc về lý thuyết, bao gồm cả việc bổ sung điều kiện lồi cho MLE, mặc dù có thể mở rộng thêm một chút về ứng dụng trong Bayesian inference.

<br>

