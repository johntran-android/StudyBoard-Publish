# 3.3.1 Bayesian Linear Regression

📊 **Progress:** `7` Notes | `11` Screenshots | `7` AI Reviews

---
<a id="node-2o000zc"></a>

## 3.3.1 Bayesian Linear Regression

<p align="center"><kbd><img src="assets/lfdkvgqkwyh.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn mở đầu này đại ý là vầy: Trong các cuộc thảo luận khi ta nói về cách tiếp cận maximum likelihood trong việc chọn giá trị của parameter của linear model (chính là **w** của y(**w**, **x**) = **w**TΦ(**x**)) thì ta đã thấy rằng, bằng cách dùng hàm basis function Φ(**x**), ta có thể tăng mức độ complexity của model (vì còn nhớ, Φ(**x**) giúp biến hàm y(**w**,**x**) = **w**TΦ(**x**) thành hàm phi tuyến theo **x**, dù vẫn là tuyến tính đối với **w**). Tuy nhiên, mức độ complexity cần phải được kiểm soát vì đã thấy trong các phần trước rằng MLE sẽ dẫn đến overfit khi data ít. Từ đó, ta được học rằng cũng có thể dùng reguarization để kiểm soát mức complexity hiệu quả của model.
>
>
>
> Tuy nhiên, cách làm này lại đặt ra vấn đề là phải chọn mức độ regularization thông qua việc chọn regularization coefficient (hay hyperparamter) λ. Và cái λ này, ta cũng đã từng nói, lại không thể dùng data để mà train, vì nếu làm vậy, again, nó cũng sẽ chọn λ khiến maximum likelihood → overfit.
>
>
>
> Để đối phó với vấn đề phát sinh trên, một cách làm là tách riêng một bộ data để dùng cho việc chọn λ. Tuy nhiên, cách này cũng không tối ưu khi ta phải hi sinh data vốn chứa thông tin hữu ích cho việc training model cũng như phát sinh thêm chi phí tính toán cho bước chọn λ.
>
>
>
> Thành ra, qua phần này, ta sẽ thảo luận qua Bayesian approach, và gs nói rằng, nó sẽ giúp tránh được vấn đề overfit, cũng như có thể dẫn đến một phương pháp tự quyết định mức complexity của model thông qua training data (mà ko cần dành riêng data cho validation).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bản ghi chú vô cùng xuất sắc khi giải thích rất sâu sắc, liên hệ chính xác các công thức toán học đã học để làm rõ nghĩa cho đoạn văn bản. Để hoàn hảo hơn, bạn có thể bổ sung ý nhỏ của tác giả về tầm quan trọng của việc lựa chọn số lượng và dạng thức của basis functions đối với hành vi của mô hình.

<br>

<a id="node-59lqws3"></a>

## Section 3.3.1 Parameter Distribution

<p align="center"><kbd><img src="assets/a9dlhrw9zhk.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, trước khi nói về nội dung này, mình có thể tranh thủ ôn lại chút xíu về Bayesian approach, mà được học lần đầu trong Casella.
>
>
>
> Trong Casella, với bối cảnh là bài toán point estimation: Tìm một statistic W(**X**) để estimate cho population parameter θ (dựa trên cơ sở là ta có một random sample **X** = X1,...Xn iid sampling từ population f(**x**|θ).Thế thì, Classic (hay Frequentist) approach chỉ khác Bayesian approach ở chỗ: Frequentist coi θ là cố định nhưng chưa biết, còn Bayesian coi θ là random variable. Và vì coi θ là random variable, nên nó sẽ có probability distribution. Và chia làm hai loại: f(θ), hay người ta thường dùng π(θ), gọi là prior distribution, là distribution khi chưa dựa trên data. Thường người ta sẽ chọn dựa trên niềm tin, kiến thức nào đó về θ. Và π(θ|**x**), posterior distribution, là distribution của θ conditioned on **X** = **x**. Và dùng Bayes theorem, ta sẽ có π(θ|**x**) = f(**x**|θ) π(θ) / f(**x**), (do đó mới gọi là Bayesian approach). Thế thì, khi đã có posterior distribution của θ, đối với bài toán point estimation với yêu cầu là đưa ra một hàm W(**X**), thì ta có thể dùng W(**X**) = θ^\_B(**X**) = E\[θ|**x**\], đây chính là mean của posterior, cũng là Bayes estimator khiến minimize posterior expected loss hay minimize Bayes risk với square error loss function.
>
>
>
> Quay lại đây, như đã nói, ta sẽ dùng Bayesian approach cho bài toán đi tìm tham số **w** của linear model. Thì như đã nói ở trên, với Frequentist approach, người ta không coi θ như random variable, mà chỉ là fixed & unknown, do đó, bữa giờ, khi ta đi tìm ML estimator của **w**, ta không hề coi nó là random variable, nên không hề nói về distribution của nó. Vậy thì nay, với Bayesian approach, ta **COI w NHƯ RANDOM VARIABLE**, từ đó mới đưa vào (introducing) **PRIOR DISTRIBUTION** f(**w**) (hay trong sách là p(**w**), tương ứng với π(θ) ở trên).
>
>
>
> Rồi, một điểm nữa, lúc nãy mình nói người ta thường chọn priori (viết tắt của prior distribution) của θ dựa trên kiến thức kinh nghiệm trải nghiệm của experimenter về θ. Nhưng người ta cũng thường chọn nó sao cho việc tính toán trở nên thuận lợi: Đó là, chọn priori là conjugate prior của likelihood. Là sao?
>
>
>
> Likelihood function, là function của θ, được kí hiệu là L(θ|**x**), mang ý nghĩa là, với quan sát được **X** = **x** thì độ hợp lí của θ là bao nhiêu. Và độ hợp lí này được định nghĩa = f(**x**|θ), tức joint pdf của random sample **X**, tại observed value **x**. Thế thì thông qua Bayes rule như nói ở trên: π(θ|**x**) = f(**x**|θ) π(θ) / f(**x**), thì đại khái là, nếu như prior distribution π(θ) mà là conjugate prior của f(**x**|θ), tức likelihood L(θ|**x**), thì posterior π(θ|**x**) SẼ CŨNG TRỞ NÊN CÙNG MỘT LOẠI VỚI PRIORI. Ví dụ, nếu f(**x**|θ) là Binomial, thì khi chon priori là Beta distribution, thì posterior cũng sẽ ra là distribution của Beta, chỉ khác param. Do đó Beta là conjugate prior của Binomial. Tương tự, ta có nhiều cặp khác, Gaussian là conjugate prior của Gaussian,....
>
>
>
> Chính vì lí do đó, ở đây, gs Bishop mới nói về conjugate prior, cụ thể là như sau:
>
>
>
> Đầu tiên cần nhớ rằng, ta đang muốn xây dựng posterior distribution của **w**: f(**w**|Data) với Data bao gồm các observed value, là các cặp data (**x1**, t1),....(**x**N, tn) (**x** là vector, t là scalar), và gom các vector **x**1,...**x**N lại thành design matrix **X**, cũng như t1,...tN thành vector **t**. Thế thì, theo Bayes theorem:
>
>
>
> f(**w**|Data) = f(**w**|**X**,**t**) = f(Data|**w**) f(**w**) / f(Data)
>
>
>
> và f(Data|**w**) ở đây sẽ là f(**X**, **t**|w).
>
>
>
> Có điều, trong bài toán regression, người ta sẽ không coi **X** là random variable, mà chỉ coi nó là fixed value do đó ta chỉ coi T là random variable.
>
>
>
> nên f(Data|**w**) là f(**t**|**X**,**w**), và như đã nói ở đâu đó trước đây trong sách, ta sẽ bỏ qua không kể **X** cho gọn, nên chỉ còn là f(**t**|**w**).
>
>
>
> Vậy nên ta có f(**w**|**t**) = f(**t**|**w**) f(**w**) / f(**t**).
>
>
>
> Và f(**t**|**w**) ở đây, theo 3.10, chính là Πi=1:N N(ti|**w**TΦ(**x**i), 1/β). Giải thích sơ lại cái này:
>
>
>
> ---
>
>
>
> Trong bài toán này, ta đặt ra giả định rằng noise sẽ tuân theo Normal(0, 1/β), đồng nghĩa, Ti - y(**x**i, **w**) sẽ \~ normal(y(**x**i, w), 1/β).
>
>
>
> Như vậy, với việc ta có data set **X**, **t**, cũng chính là ta có một observed value của **T** (=T1,....TN) = **t** = (t1,...tN)).
>
>
>
> Thì likelihood L(**w**|**t**), theo định nghĩa nói trên, = f(**t**|**w**)
>
>
>
> và vì T1,...TN independent, nên joint pdf của **T** tách thành tích các marginal pdf của T1,....TN:
>
>
>
> f(**t**|**X**, **w**) = f(t1|**x**1, **w**) ×... × f(tN|**x**N, **w**) = Πi=1:N f(ti|**x**i, **w**)
>
>
>
> Do đó L(**w**|**t**) = f(**t**|**w**) = Πi=1:N f(ti|**x**i, **w**)
>
>
>
> = Πi=1:N f(ti|**w**) nêú muốn không nhắc đến **x** cho gọn)
>
>
>
> và f(ti|**w**) là pdf của normal(y(**x**i, w), 1/β)
>
>
>
> =  Πi=1:N N(ti|y(**x**i, **w**), 1/β)
>
>
>
> =  Πi=1:N N(ti|**w**TΦ(**x**i), 1/β) (chính là 3.10)
>
>
>
> ---
>
>
>
> Thế thì N(ti|**w**TΦ(**x**i), 1/β), là pdf của N(**w**TΦ(**x**i), 1/β), nó sẽ có dạng \[1/√2π(1/β)\] × exp{-\[ti - **w**TΦ(**x**i)\]^2/2(1/β)}
>
>
>
> Nên Πi=1:N N(ti|**w**TΦ(**x**i), 1/β) = \[1/√2π(1/β)\]^N × Πi=1:N exp{-\[ti - **w**TΦ(**x**i)\]^2/2(1/β)}
>
>
>
> = \[1/√2π(1/β)\]^N × exp {Σi=1:N \[-(ti - **w**TΦ(**x**i))^2/2(1/β)\]}
>
>
>
> Xét cái term trong exp: Σi=1:N \[-(ti - **w**TΦ(**x**i))^2/2(1/β)\]
>
>
>
> = - \[1/2(1/β)\] Σi=1:N \[(ti - **w**TΦ(**x**i))^2\]
>
>
>
> = - \[1/2(1/β)\] ||**Φw** - **t**||^2
>
>
>
> = - \[1/2(1/β)\] (**Φw** - **t**)T(**Φw** - **t**)
>
>
>
> = - (1/2) (**Φw** - **t**)T (β**I**) (**Φw** - **t**)
>
>
>
> ⇒ Πi=1:N N(ti|**w**TΦ(**x**i), 1/β) = \[1/√2π(1/β)\]^N exp\[- (1/2) (**Φw** - **t**)T (β**I**) (**Φw** - **t**)\]
>
>
>
> = \[1/√2π\]^N \[1/√(1/β)\]^N exp\[- (1/2) (**Φw** - **t**)T (β**I**) (**Φw** - **t**)\]
>
>
>
> = \[1/(2π)^(N/2)\] \[1/√|**Σ**|\] exp\[- (1/2) (**t** - **Φw**)T (**Σ**inv) (**t** - **Φw**)\]
>
>
>
> với **Σ**inv = β**I** ⇔ **Σ** = (1/β)**I**
>
>
>
> Và như vậy, f(**t**|**w**) sẽ có dạng của Gaussian và do đó vì Gaussian là conjugate prior của Gaussian nên ta sẽ chọn priori là Gaussian: f(w) = N(**w**|**m**0, **S**0) (**m**0, **S**0 là mean và covariance matrix của prior distribution này)
>
>
>
> Ghi chú nhỏ: Trong sách, gs nói cái likelihood function của 3.10 là hàm exponential của quadratic function của **w**, mục đích chính cũng chỉ là muốn chỉ ra rằng hàm prior phải là Gaussian với lập luận tương tự như sau:
>
>
>
> vì bên trong exp của f(**t**|**w**) có dạng exp (quadratic function của **w**). thì nếu ta chọn prior f(**w**) là normal(**m**0, **S**0) thì pdf sẽ cũng có dạng exp (quadratic function của **w**). Để rồi khi nhân lại f(t|**w**) f(**w**) / f(**t**) thì dùng tính chất hàm exp, cái tử cũng sẽ nhập lại, để rồi trở thành dạng exp \[quadratic function cuả **w**\], còn cái mẫu, như đã biết, sẽ chỉ là nó sẽ nhập vào các phần constant để trở thành normalizing constant của posterior, và như vậy, posterior cũng sẽ có cùng dạng với prior distribution.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú cực kỳ chi tiết, chính xác và có chiều sâu khi kết nối từ lý thuyết nền tảng đến các bước biến đổi toán học cụ thể của hàm likelihood. Điểm lưu ý nhỏ duy nhất là bạn viết nhầm ký hiệu vector kỳ vọng của prior thành w0 thay vì m0 như trong sách (phương trình 3.48).

**🔗 See also:** [Likelihood and Error Functions](./311_maximum_likelihood_and_least_squares.md#node-urnjdcs)

<br>

<a id="node-fv65lte"></a>

### Bayesian Linear Regression Posterior Update

<p align="center"><kbd><img src="assets/4ucseett3a4.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì với việc đã chọn prior của **w** là N(**m**0, **S**0), thì ở đây, đại ý gs Bishop nói là, ta sẽ theo Bayes theorem để mà derive ra f(**w**|**t**), kết quả chắc chắn sẽ ra dạng của một Normal (có parameter khác). Và nhờ những gì ta đã chuẩn bị ở chương 2 (xem link) - trong phần đó, đại ý là mình cũng đã kinh qua việc dùng kĩ thuật completing the square cũng như là nhận diện mẫu, để kiểu như là với prior f(**x**) là normal có param này, f(**y**|**x**) cũng là normal có param kia thì f(**x**|**y**) cũng sẽ ra là normal có param nọ. Nên nay ta chỉ việc áp dụng thôi, khỏi cần tự làm:
>
>
>
> Cụ thể, theo link tới note trong chap 2, ta có bảng tóm tắt sau:
>
>
>
> Cho f(**x**) = N(**x**|**μ**, **Λ**inv),
>
>
>
> f(**y**|**x**) = N(**y**|**Ax** + **b**, **L**inv)
>
>
>
> thì f(**y**) = N(**y**|**Aμ** + **b**, **L**inv + **A** **Λ**inv **A**T)
>
>
>
> và f(**x**|**y**) = N(**x**| **Σ**{**A**T**L**(**y** - **b**) + **Λμ**}, **Σ**) với **Σ** = (**Λ** + **A**T **L** **A**)inv
>
>
>
> Vậy thì, ở đây, ta có
>
>
>
> và f(**w**) = N(**w**|**m**0, **S**0) (tương đương **μ** = **m**0, **Λ**inv = **S**0 → **Λ** = **S**0inv
>
>
>
> f(**t**|**w**) là N(**t**|**Φw**, (1/β)**I**) (tương đương **A** = **Φ**, **b** = 0, Linv = 1/β)**I** → **L** = β**I**)
>
>
>
> nên f(**w**|**t**) sẽ là Normal có mean và variance là:
>
>
>
> Covariance matrix, **S**N, tức là **Σ**, áp dụng công thức trên: (**Λ** + **A**T **L** **A**)inv: thay **Λ** = **S**0inv, **A** = **Φ**, **L** = β**I**
>
>
>
> = (**S**0inv + **Φ**T (β**I**) **Φ**)inv
>
>
>
> = (**S**0inv + β**Φ**T**Φ**)inv
>
>
>
> ⇔ **S**Ninv = **S**0inv + β**Φ**T**Φ** → 3.51.
>
>
>
> Mean: **m**N, áp dụng công thức **Σ**{**A**T**L**(**y** - **b**) + **Λμ**}
>
>
>
> = **S**N{**Φ**T(β**I**)(**t** - **0**) + **S**0inv **m**0}
>
>
>
> = **S**N{β**Φ**T**t** + **S**0inv **m**0}
>
>
>
> = **S**N{**S**0inv **m**0 + β**Φ**T**t**} → 3.50
>
>
>
> Nói chung là áp dụng công thức thôi

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Ghi chú cực kỳ chính xác và chi tiết khi liên kết thành công công thức tổng quát từ Chương 2 để chứng minh công thức Chương 3 một cách tường minh. Để hoàn hảo hơn, bạn có thể bổ sung thêm giải thích ngắn gọn về ý nghĩa vật lý của các tham số đóng vai trò là độ chính xác (precision) trong việc cập nhật phân phối.

**🔗 See also:** [Phân bố tiên nghiệm và hậu nghiệm](./233_bayess_theorem_for_gaussian_variables.md#node-zswmsts)

<br>

<a id="node-fs2bcmg"></a>

#### Maximum A Posteriori Estimation

<p align="center"><kbd><img src="assets/z5b6x2u043.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, đoạn này là sao:
>
>
>
> Thì đại ý là, sau khi đã có posterior distribution của **w**, là normal(mN, SN_inv) thì ta làm gì nữa? Tại sao lại nói đến maximize log của posterior distribution?
>
>
>
> Thế thì, chỗ này để hiểu rõ cần phải nhắc lại maximum likelihood, rồi ta sẽ liên hệ qua lại cái này.
>
>
>
> Đầu tiên, cần nhấn mạnh, nói đến maximum likelihood, thì ta đang trong trường phái Frequentist. Vì trong trường phái này, ta coi tham số, tức **w** là giá trị cố định nhưng chưa biết. Và ta muốn đi tìm một function của data để estimate ra giá trị **w**. Và MLE chỉ là một cách tiếp cận phổ biến, trong đó ta sẽ dùng cái function sau đây để làm estimator cho **w**: **w**ML(data) = argmax\_**w** L(**w**|data). Có nghĩa là, ta sẽ giải bài toán tối ưu:
>
>
>
> maximize over **w** {L(**w**|data)}. Với data ở đây là **t**, matrix **X**
>
>
>
> và hàm likelihood là hàm của **w**, được mang ý nghĩa là độ hợp lí của **w** dựa trên / giải thích cho giá trị quan sát được của data, có giá trị = f(data|**w**), ở đây, tức là f(**t**|**X**, **w**), hay f(**t**|**w**).
>
>
>
> và để giải bài toán tối ưu ta có thể dùng hàm ln để chuyển thành bài toán tương đương trong đó ta maximize hàm ln likelihood: ln L(**w**|data) = ln f(**t**|**w**). Và với f(t|**w**) là pdf của normal, kết quả một lần nữa chuyển thành minimize sum square error như đã biết.
>
>
>
> Thế thì, ý chính là, khi ta maximize hàm likelihood L(**w**|**t**) thì ta đang tìm w để maximize hàm L(**w**|**t**)
>
>
>
> Vậy thì quay lại đây, khi ta đã có posterior f(**w**|**t**) = f(**t**|**w**) f(**w**) / f(**t**) thì hoàn toàn tương tự, ta cũng có thể đi tìm **w** để maximize f(**w**|**t**) cũng là maximize f(**t**|**w**) f(**w**) / f(**t**)
>
>
>
> Và xét bài toán maximize over **w** {f(**t**|**w**) f(**w**) / f(**t**)}
>
>
>
> thì vì f(**t**) không âm , và dùng hàm ln để có bài toán tối ưu tương đương:
>
>
>
> maximize over **w** {ln \[f(**t**|**w**) f(**w**)\]}
>
>
>
> dùng tính chất hàm log: ln \[f(**t**|**w**) f(**w**)\] = ln f(**t**|**w**) + ln f(**w**)
>
>
>
> Thay công thức của f(**t**|**w**) (y như ở trên) và f(**w**), và gom constant lại ta sẽ thấy nó thành bài toán:
>
>
>
> minimize (β/2) sum square error + α **w**T**w** + constant
>
>
>
> Tuy nhiên vì ta biết f(**w**|**t**) là normal có mean mN, nên ta cũng biết w khiến maximize f(**w**|**t**) rồi: chính là **m**N.
>
>
>
> Có nghĩa là giải bài toán trên ta sẽ ra **w** là **m**N
>
>
>
> Nhưng ý quan trọng muốn nói, là bài toán minimize hàm sum square error với L2 regularization loss chính là việc ta đi tìm w khiến maximize posterior distribution, dù rằng trong trường hợp này ta biết solution chính là mean **m**N
>
>
>
> Suy ngẫm một chút, mình nhớ, trong Casella, khi đã đi theo Bayesian approach, để đi xây dựng cái gọi là Bayes estimator của θ, và sau khi đã có được posterior distribution π(θ|**x**), thì hình như người ta không làm theo lối đi tìm θ khiến maximize π(θ|**x**). Mà thay vào đó, họ sẽ dùng decision theory: chọn loss function, L(W(**X**), θ), ví dụ square error loss = \[W(**X**) - θ\]^2. 
>
>
>
> Rồi, tính risk function: E\_θ\[L(W(**X**), θ)\] = ∫ L(W(**x**), θ) f(**x**|θ) d**x**. 
>
>
>
> Và Bayes risk: E\[E\_θ\[L(W(**x**), θ)\]\] = ∫E\_θ\[L(W(**x**), θ)\] π(θ)dθ. Từ đó đi minimize cái Bayes risk này, và bài toán sau một chút biến đổi, sẽ cũng là minimize ∫L(W(**x**), θ) π(θ|**x**) dθ, gọi là posterior expected loss. Và kết quả sẽ cho ra là E\[θ|**x**\], tức mean của posterior
>
>
>
> Nếu so với việc tìm θ có π(θ|**x**) lớn nhất, thì kết quả có thể sẽ khác. Tuy rằng trong trường hợp posterior là Normal thì hai kết quả sẽ giống nhau, vì mean của posterior cũng là nơi có π(θ|**x**) lớn nhất.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú cực kỳ xuất sắc, thể hiện sự hiểu biết sâu sắc và chính xác về mối liên hệ giữa tối đa hóa hậu nghiệm (MAP) và việc giảm thiểu sai số có Regularization L2. Bạn chỉ cần lưu ý thêm hệ số 1/2 ở phần phạt L2 (tức là α/2 thay vì α) để công thức hoàn toàn đồng nhất với tài liệu học.

<br>

<a id="node-ek7ydwk"></a>

##### Bayesian Linear Regression Example

<p align="center"><kbd><img src="assets/e0lxfmqww39.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ở đây với mục đích là muốn minh họa và so sánh kết quả thu được khi dùng cách tiếp cận Bayesian đối với bài toán linear model, tác giả sẽ đặt ra một bối cảnh như sau:
>
>
>
> Ta sẽ tạo ví dụ N = 100 điểm data theo quy luật sau:
>
>
>
> Sampling X1,....X100 từ Uniform(-1,1)
>
>
>
> Dùng hàm f(x, **a**) = a0 + a1x = -0.3 + 0.5x.
>
>
>
> Và sampling ε1,...ε100 từ N(0, (0.2)^2)
>
>
>
> Và tính t1 = f(x1, **a**) + ε1, ...,t100 = f(x100, **a**) + ε100
>
>
>
> Như vậy, có nghĩa là gì?
>
>
>
> Có nghĩa là, các giá trị t1,...tN sẽ là observed value của T|x sẽ tuân theo phân phối Normal(f(x, **a**), (0.2)^2). Vì sao? Vì ε \~ Normal(0, (0.2)^2), thì ε + f(x, **a**) sẽ là một Normal(f(x,**a**), (0.2)^2).
>
>
>
> Do đó, nếu ta dùng một linear model có basis function đơn giản: tuyến tính: Φ(x) = x, để linear model sẽ là: y(x, **w**) = w0 + w1x, và đặt ra assumption là T|x \~ normal(y(x, **w**), (0.2)^2) thì ta đang giả định đúng distribution của T. Khi đó, nếu làm tốt, để tìm ra được **w** = **a**, thì khi dùng hàm y(x, **w**=**a**) để dự đoán giá trị t của một x mới, sai số error sẽ chỉ còn là sai số đơn thuần do nhiễu ngẫu nhiên - là phần không thể loại bỏ được.
>
>
>
> Chý ý là, vì ở đây ta chủ động tạo noise theo normal có variance 0.2^2, và mục đích là tập trung vào **w**, nên trong giả định về distribution normal(y(x, **w**), (0.2)^2) của T|x thì ta coi như biết variance luôn, chứ nếu không, variance cũng là một tham số cần phải đi tìm (estimator, dựa trên data)
>
>
>
> Và còn một parameter nữa, đó là vì sẽ chọn prior distribution cho **w**, là N(0, 1/α). Trong trường hợp này, ta cũng cho rằng nó là 2. (Nói chung là để chỉ còn parameter là **w** là chưa biết thôi).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú của bạn rất chính xác và thể hiện sự hiểu biết sâu sắc về quá trình sinh dữ liệu giả lập cũng như mô hình Bayesian Regression. Bạn chỉ cần lưu ý làm rõ mô hình sử dụng hai hàm cơ sở là phi_0(x) = 1 và phi_1(x) = x để tránh nhầm lẫn khi định nghĩa vector basis function.

<br>

<a id="node-cpf6sek"></a>

- **Bayesian Linear Regression**

<p align="center"><kbd><img src="assets/rtt82qjmkbb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/f48m4xtjxra.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vvvwba1pei.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/35k7zbl32uv.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/7d62x33pqef.png" width="80%"></kbd></p>

> [!NOTE]
> Đây là cái hình quan trọng nhất cuốn sách này. Nó minh họa giúp ta có sự hình dung về quá trình data giúp nhào nặn lại distribution của **w**
>
>
>
> Hàng đầu tiên: Trạng thái chưa có observation (x,t) nào. Hình đầu tiên (cột 1) trống trơn. Tuy nhiên ta sẽ hiểu nó sẽ thể hiện đồ thị của hàm likelihood (dĩ nhiên là theo w0, w1) dựa trên data point mới nhất. 
>
>
>
> Còn nhớ, likelihood, là hàm theo w, kí hiệu bởi L(**w**|data), mang ý nghĩa độ hợp lí của w dựa trên giá trị quan sát data, và được định nghĩa là có độ lớn tính bởi f(data|**w**) tức joint pdf của random sample tại observed value của nó. Vậy thì ở đây, giả sử ta có một observed data - là một cặp giá trị (x, t). Thì, hàm L(**w**|data) = L(w0, w1|x, t) = f(t|x, w0, w1). Và với pdf của T là n(y(x, **w**), 0.2^2), thì f(t|x, w0, w1) 
>
>
>
> = \[1/√2π(0.2)^2\] exp{-\[t-y(x,**w**)\]^2/2(0.2)^2} 
>
>
>
> = \[1/√2π(0.2)^2\] exp{-\[t-w0-w1x\]^2/2(0.2)^2}
>
>
>
> = \[constant1\] exp{-\[t-w0-w1x\]^2/ \[constant 2\]}
>
>
>
> Và cột 1 chính là vẽ đồ thị hàm L(w0, w1|x, t) = \[constant1\] exp{-\[t-w0-w1x\]^2/ \[constant 2\]} theo w0, w1. Ta sẽ quay lại khi nói về hàng thứ hai, sau khi đã có observation đầu tiên.
>
>
>
> Thế thì, cột hai của hàng 1 chính là prior distribution của **w**, là một normal(0, 1/α = 1/2)), nên ta thấy nó có dạng cái chuông (dĩ nhiên nhìn từ trên cao xuống, đỉnh chuông là tại mean (0, 0). Vì sao các dải màu lại có dạng các đường tròn đồng tâm? → đơn giản là cho n(**w**|0,1/2) = c, ta sẽ thấy nó có dạng của phương trình đường tròn.
>
>
>
> Còn cột 3: Chính là ta sẽ sampling các **w** = (w0, w1) từ distribution của cột 2, và với các **w** đó, ta vẽ đồ thị của hàm số y = w0 + w1x để ra các đường màu đỏ.
>
>
>
> ---
>
>
>
> Qua hàng 2: Đã có một cặp (x1, t1), điểm data (x,t) màu xanh ở hình bên phải hàng 2.
>
>
>
> Thì hình bên trái (cột 1), như đã nói, sẽ vẽ đồ thị hàm likelihood. Thì lúc này, nó sẽ là đồ thị (dĩ nhiên cũng là nhìn từ trên cao xuống) của hàm L(**w**|x1,t1) = \[constant1\] exp{-\[t1-w0-w1x1\]^2/ \[constant 2\]}: 
>
>
>
> L sẽ đạt giá trị lớn nhất, nếu như -\[t1-w0-w1x1\]^2 đạt giá trị lớn nhất (vì hàm exp đồng biến). Và điều này tương đương \[t1-w0-w1x1\]^2 nhỏ nhất ⇔ t1-w0-w1x1 = 0 ⇔ w0+w1x1 = t1. Như vậy, level set của hàm L(**w**|x1, t1) ứng với giá trị lớn nhất của L sẽ là đường thẳng w0 + w1x1 = t1, và đó chính là đường màu đỏ đậm trong hình bên trái.
>
>
>
> Khi c tăng lên từ 0, t1-w0-w1x1 = c sẽ là level set của hàm L với giá trị nhỏ dần. Tạo nên các đường song song màu đỏ tươi, vàng, xanh lá.
>
>
>
> Có nghĩa, là ta hình dùng đây là nhìn từ trên cao của đồ thị hàm L(**w**|x1,t1) có dạng giống như con sóng vậy Mà mặt cắt của con sóng sẽ là một hình chuông, có standard deviation chính là 0.2. Cũng có nghĩa là cái bề rộng của giả mày đỏ vàng xanh lá này chính là quy định bởi con số 0.2 này.
>
>
>
> Rồi, hình ở giữa (cột 2) của hàng 2 lúc này chính là contour plot của hàm posterior f(**w**|x1,t1), như đã biết, cũng là một normal. Tuy nhiên, sự hữu ích của mấy cái hình này ở đây mới phát huy tác dụng: Đó là: **Cái ellipse dẹp lép này chính là hệ quả của việc nhân cái prior tròn quay ở trên với cái con sóng likelihood nói trên.** 
>
>
>
> Và sampling từ cái posterior f(**w**|x1,t1) lúc này, sẽ vẽ nên các đường y = w0 + w1x bên phải bắt đầu không còn xay tứ phía như khi chưa có data (sampling từ priori) nữa, mà chúng đều đi gần điểm data (x1, t1) màu xanh.
>
>
>
> ---
>
>
>
> Qua hàng 3: Khi có thêm data point (x2, t2)
>
>
>
> Xét cái hình bên trái hàng 3, nên nhớ ta đã nói nó sẽ chỉ là contour plor của hàm L(**w**|data point mới nhất). Nên đây chính là của L(**w**|x2, t2). Tương tự như của L(**w**|x1, t1), đồ thị của nó sẽ nếu nhìn trong 3D sẽ là con sóng nằm chéo, mà tâm sóng nơi sóng cao nhất là cái đường w0 + w1x2 = t2 trong mặt phẳng w0w1
>
>
>
> Qua hình 2, lúc này, là contour plot của posterior f(w|x1,t1,x2,t2) mà về mặt lý thuyết ta cũng đã biết nó là một normal lúc này có dạng của cái chuông không còn dẹt dài mà trở thành tròn và nhọn hơn nhiều, nên cái contour plot trở thành cái ellipse tương đối tròn nhưng nhỏ hơn rất nhiều so với cái prior f(**w**), và posterior f(**w**|x1,t1).
>
>
>
> Và again, caí hay là: nó chính là kết quả khi ta áp cái con sóng của L(**w**|x2,t2) lên cái ellipse dẹt f(**w**|x1,t1).
>
>
>
> Và khi sampling từ distribution f(w|x1,x2,t1,t2), các đường y = w0 + w1x trở lúc này đều đi gần hai điểm (x1,t1), (x2,t2). Mà như vậy dẫn đến chúng lúc này khá giống nhau (điều mà trước đây, khi chỉ có observed (x1, t1) chưa làm được, khi lúc đó tuy các đường màu đỏ đều đi gần (x1, t1) nhưng chúng vẫn có hướng rất khác nhau.
>
>
>
> ---
>
>
>
> Thế thì một điểm quan trọng đó là: Nếu ta bỏ qua hàng 2, mà vẽ likelihood L(w|x1, t1, x2, t2). Rồi áp nó lên (ý là nhân với) cái contour plor của prioro trên cùng, thì ta cũng sẽ có cáii hình giữa của hàng 3. Mà theo tóan học, nó chính là: 
>
>
>
> f(**w**| data point 1) = f(data point 1|**w**) f(**w**)
>
>
>
> f(**w**|data point 1,2) = f(data point 2|**w**) f(**w**| data point 1)
>
>
>
> và f(**w**|data point 1,2) cũng = f(data point 1, 2|**w**) f(**w**).
>
>
>
> ---
>
>
>
> Và cuối cùng, khi có 20 data point, cái contour plot của posterior (hình giữa hàng 4) f(w|x1,..x20, t1,..t20) trở nên rất nhỏ, rất focus và rất gần cái dấu cross màu trắng (nãy giờ quên nói, chính là **a** = (a0, a1), tức giá trị thật sự mà ta muốn tìm ra cho w0, w1.
>
>
>
> Và khi sampling từ posterior này, các đường y = w0 + w1x (hình phải hàng 4) trở nên cực kì giống nhau, có độ biến động nhỏ hơn nhiều.
>
>
>
> Và nếu ta tăng data lên vô hạn, thì cái plot của posterior nó sẽ trở thành 1 cái delta function - tức là giống như cây kim nhọn hoắc ngay vị trí white cross (a0, a1).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú của bạn cực kỳ xuất sắc, thể hiện sự hiểu biết sâu sắc khi tự giải thích được bản chất toán học đằng sau các hình ảnh trực quan của đồ thị likelihood và posterior. Để hoàn thiện hơn nữa, bạn có thể bổ sung thêm giải thích về ký hiệu toán học cụ thể của nhiễu precision ̢͂ beta để liên kết chặt chẽ hơn với văn bản gốc.

<br>

<a id="node-s30ywpk"></a>

- **Generalized Gaussian Prior Distribution**

<p align="center"><kbd><img src="assets/eprp3s513b9.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng, đại ý là gs cho biết ta có thể dùng một phiên bản khái quát hơn của Gaussian để làm priori cho **w**, với pdf có dạng 3.56, trong đó khi q = 2 thì pdf này chính là Gaussian.
>
>
>
> Và gs nói lại điều đã biết, khi tìm maximum của posterior distribution, thì nó sẽ tương đương với việc giải bài toán minimize error function có regularization term, để rồi khi priori là Gaussian (khi q trong 3.56 = 2) thì posterior cũng là Gaussian, và w khiến maximize posterior chính là mean của posterior. (nếu q khác 2, 3.56 không phải Gaussian, khi đó chưa chắc posterior đã là Gaussian, vì như likelihood là Gaussian, có conjugate prior là Gaussian)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú rất chính xác và thể hiện sự hiểu biết sâu sắc về mối liên hệ giữa hàm prior khái quát hóa, tính liên hợp (conjugate) và các đặc trưng của phân phối posterior (mean và mode). Việc bạn tự suy luận hệ quả khi $q \neq 2$ dựa trên kiến thức về conjugate prior là một điểm cộng lớn.

<br>

