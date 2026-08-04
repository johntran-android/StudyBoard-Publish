# 3.3 Bayesian Linear Regression

📊 **Progress:** `4` Notes | `4` Screenshots | `4` AI Reviews

---
<a id="node-2o000zc"></a>

## 3.3 Bayesian Linear Regression

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

