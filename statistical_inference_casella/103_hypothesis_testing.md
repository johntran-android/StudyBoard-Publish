# 10.3 Hypothesis Testing

📊 **Progress:** `7` Notes | `8` Screenshots | `7` AI Reviews

---
<a id="node-zhfsuqo"></a>

<br>

<a id="node-zkjc4fc"></a>

## Section 10.3 Hypothesis Testing

<p align="center"><kbd><img src="assets/ukpfs7zs7x.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại ý là ta sẽ bàn về bài toán hypothesis testing trong các trường hợp phức tạp.
>
>
>
> Cụ thể là khi các bài toán không có optimal test, ví dụ như không có UMP test.
>
>
>
> Đã học hypothesis testing từ chap 8, có lẽ nên active recall chút xíu:
>
>
>
> Đầu tiên, bài toán hypothesis testing cũng là bài toán inference (model parameter), giống như bài toán point estimator. Với point estimation, trong đó, cho sample X1,...Xn \~ f(x|θ) (và ta giả định f(x|θ) là một dạng, một loại nào đó, và đây gọi là cách tiếp cận parameteric model) và mục tiêu là đi tìm một estimator - theo định nghĩa, là một hàm của sample W(**X**), để với observed value **x** của **X**, W(**x**) sẽ cho ta một point estimate của θ.
>
>
>
> Còn với hypothesis testing, nhiệm vụ cũng là đưa ra một hàm số của sample, nhưng thay vì tính ra point estimate của θ, hàm này sẽ đưa ra quyết định giữa một trong hai giả thuyết: θ nằm trong Θ0 (gọi là H0) hay θ nằm trong Θ0c (gọi là H1). Và để làm vậy, ta sẽ xây dựng một hypothesis testing, có bản chất là một hàm quyết định: nhận vào một possible value của sample, tính ra một hàm của sample (gọi là test statistic δ(**X**)), và từ giá trị của nó, ta sẽ đưa ra output: kết luận θ thuộc Θ0 hay θ thuộc Θ0c (ví dụ như so δ(**x**) với một ngưỡng nào đó)
>
>
>
> Và cũng đồng nghĩa, phép thử sẽ tạo ra một cái gọi rejection region R, chứa các input x khiến kết quả phép thử là reject H0 (tức kết luận cho rằng θ ∈ Θ0c): 
>
>
>
> R = {**x** ∈ **𝒳**: δ(**x**) = reject H0}
>
>
>
> Và từ đó, cũng như ta có các cách tiếp cận để có point estimator W(**X**) tối ưu, thì ở đây ta cũng sẽ đánh giá để tìm ra hypothesis testing tối ưu.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **90/100**
>
> Bạn đã tóm tắt chính xác ý chính và có tư duy liên hệ xuất sắc khi chủ động ôn lại các khái niệm nền tảng từ chương trước. Tuy nhiên, để đầy đủ hơn, bạn nên bổ sung hai phương pháp cụ thể được nhắc đến ở cuối bài là kiểm định tỷ số khả biến mẫu lớn và các kiểm định xấp xỉ mẫu lớn.

<br>

<a id="node-br8m56p"></a>

### Section 10.3.1 Asymptotic Distribution of LRTs

<p align="center"><kbd><img src="assets/tjl268i007c.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên gs nói rằng đại ý là một trong nhưng method hữu ích nhất cho các mô hình phức tạp là likelihood ratio method, vì nó cho ta một định nghĩa tường minh của test statistic, cũng như rejection region có dạng tường minh.
>
>
>
> Dừng lại chút ôn lại cái này: Như note trước mình vừa recall lại, rằng trong bài toán hypothesis testing, nhiệm vụ là đi tìm, xây dựng một test statistic để dựa vào giá trị của nó để đưa ra kết luận về θ thuộc Θ0 (H0) hay Θ0c (H1). Vậy thì một cách đó là dùng test statistic sau: likelihood ratio test (LRT) kí hiệu λ(**x**), có công thức là:
>
>
>
> λ(**x**) = sup\_{θ∈Θ0}  {L(**x**|θ)} / sup\_{θ∈Θ} {L(**x**|θ)}, có ý nghĩa là:
>
>
>
> với observed data **X** = **x**, thì tỉ số giữa độ hợp lí lớn nhất của θ tìm được trong tập Θ0 so với độ hợp lí lớn nhất của θ tìm được trong toàn không gian parameter space Θ là bao nhiêu.
>
>
>
> Và với LRT thì decision rule là: So với một threshold c nào đó, để nếu λ(**x**) ≤ c thì kết luận reject H0, và ngược lại. Và điều này mang ý nghĩa là "nếu tìm trong Θ0 mà kết quả chỉ có độ hợp lí quá nhỏ so với kết quả khi tìm trong toàn parameter space Θ, thì ta kết luận θ không nằm trong Θ0".
>
> Đương nhiên để hoàn thành một hypothesis test, ta vẫn phải chọn giá trị của c, nhưng cách thức là như vậy.
>
>
>
> Như vậy, với LRT, rejection region là: R = {**x** ∈ 𝒳: λ(**x**) ≤ c}.
>
>
>
> Dễ thấy cái mẫu số chính là là giá trị của likelihood tại MLE θ^, vì theo định nghĩa của MLE, θ^ chính là argmax\_Θ L(θ|**x**).
>
>
>
> Và theo gs Casella, dù cho việc tính hai cái đỉnh của hàm likelihood khi xét θ trong Θ0 hay Θ có thể không tính được theo lối analytic (ví dụ như dùng giải tích để có closed form formula để tính) thì ta vẫn có thể tính theo lối numerically (ám chỉ các thuật toán tối ưu). Do đó dù không có công thức tính tử số và mẫu số ta vẫn có thể tính giá trị của λ(**x**) dựa trên thuật toán.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú cực kỳ chi tiết và chính xác, thể hiện sự hiểu biết sâu sắc về mặt toán học cũng như ý nghĩa thực tiễn của phương pháp LRT. Bạn chỉ cần lưu ý một chút về ký hiệu truyền thống của hàm likelihood là L(\theta|\mathbf{x}) thay vì viết ngược lại, nhưng tổng thể bài viết là xuất sắc.

<br>

<a id="node-frcfkif"></a>

#### Level Alpha Test Definition

<p align="center"><kbd><img src="assets/oj3bpuwdtl9.png" width="80%"></kbd></p>

> [!NOTE]
> Và ở đây nhắc lại về khái niệm level-α test, cũng là dịp để active recall chút xíu:
>
>
>
> Như đã nói, cũng như với point estimator, ta sẽ có cách (tiêu chí) để evaluate chúng, thì với hypothesis test cũng vậy.
>
>
>
> Thế thì đối với test, nó có thể có hai loại error: Kết luận H0 khi θ ∈ Θ0c hoặc ngược lại kết luận H1 khi θ ∈ Θ0, gọi là Type I và Type II error.
>
>
>
> Như vậy, với LRT, event Type I error xảy ra khi λ(**X**) ≤ c khi θ ∈ Θ0, và xác suất mắc Type I error là: P(λ(**X**) ≤ c) khi θ ∈ Θ0. Tương tự event Type II error xảy ra khi λ(**x**) &gt; c khi θ thuộc Θ0c.
>
>
>
> Và từ đó ta có định nghĩa của level α test: Đó là phép thử mà xác suất mắc Type error I không vượt quá α: sup\_θ∈Θ0 P(λ(**X**) ≤ c) ≤ α.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú rất tốt và chính xác khi giải thích rõ mối liên hệ giữa sai lầm Loại I (Type I error) và định nghĩa của level-α test từ hình ảnh. Điểm cần lưu ý nhỏ là ở câu cuối bạn nên viết rõ là 'sai lầm Loại I' thay vì ghi chung chung là 'Type error' để tránh nhầm lẫn.

<br>

<a id="node-d1so0li"></a>

##### Asymptotic Distribution of the LRT

<p align="center"><kbd><img src="assets/wgkr53q5a7q.png" width="80%"></kbd></p>

> [!NOTE]
> Định lí 10.3.1, xét một bài toán testing giữa H0: θ = θ0 vs H1: θ ≠ θ0, cho X1,....Xn iid \~f(x|θ), với θ^ là MLE của θ, và f(x|θ) thỏa regularity condition. Khi đó, theorem nói rằng:
>
>
>
> Under H0 (tức là nếu θ = θ0), thì -2log λ(**X**) → (d) χ²\_1
>
>
>
> Chứng minh như sau:
>
>
>
> Đầu tiên, khai triển Taylor quanh θ^ đối với hàm log likelihood l(θ|**x**) = log L(θ|**x**):
>
>
>
> l(θ|**x**) = l(θ^|**x**) + l'(θ^|**x**)(θ-θ^) + (1/2)l''(θ^|**x**)(θ-θ^)^2 + ....
>
>
>
> = l(θ^|**x**) + 0 × (θ-θ^) + (1/2)l''(θ^|**x**)(θ-θ^)^2 + ....
>
>
>
> = l(θ^|**x**) + (1/2)l''(θ^|**x**)(θ-θ^)^2 + ....
>
>
>
> Thay θ = θ0:
>
>
>
> l(θ0|**x**) = l(θ^|**x**) + (1/2)l''(θ^|**x**)(θ0-θ^)^2 + ....
>
>
>
> ⇒ l(θ0|**x**) ≈ l(θ^|**x**) + (1/2)l''(θ^|**x**)(θ0-θ^)^2
>
>
>
> Tiếp, xét cái -2 log λ(**x**). Như đã ôn lại, λ(**x**) = sup\_Θ0 L(θ|**x**) / sup\_Θ L(θ|**x**),
>
>
>
> và θ^ là MLE của θ nên mẫu số chính là L(θ^|**x**) nên ta có:
>
>
>
> và gọi θ^0 là restricted MLE, tức là argmax\_Θ0 L(θ|**x**), và vì ở đây Θ0 = {θ0}, nên θ^0 = θ0
>
>
>
> ⇒ -2 log λ(**x**) = -2 log \[L(θ0|**x**) / L(θ^|**x**)
>
>
>
> = -2 (log L(θ0|**x**) - log L(θ^|**x**))
>
>
>
> = -2 (l(θ0|**x**) - l(θ^|**x**))
>
>
>
> Thay l(θ0|**x**) ≈ l(θ^|**x**) + (1/2)l''(θ^|**x**)(θ0-θ^)^2 vào:
>
>
>
> ..= -2 (l(θ^|**x**) + (1/2)l''(θ^|**x**)(θ0-θ^)^2 - l(θ^|**x**))
>
>
>
> = - l''(θ^|**x**)(θ0-θ^)^2
>
>
>
> Vậy ta có -2 log λ(**x**) ≈ - l''(θ^|**x**)(θ0-θ^)^2 = (θ0-θ^)^2 \[-l''(θ^|**x**)\]
>
>
>
> (chỗ này trong sách ghi là chia cho l''(θ^|**x**) mình cho là bị in lỗi thiếu ^(-1), tức mẫu số đúng phải là l''(θ^|**x**)\]^(-1))
>
>
>
> Vậy -2 log λ(**X**) ≈ (θ0-θ^)^2 \[- l''(θ^|**X**)\]
>
>
>
> ---
>
>
>
> Xét - l''(θ^|**X**):
>
>
>
> \- l''(θ^|**X**) = \[-∂^2/∂θ^2 log L(θ|**X**)\] | θ=θ^
>
>
>
> Xét -∂^2/∂θ^2 log L(θ|**X**)
>
>
>
> = -∂^2/∂θ^2 log f(**X**|θ)
>
>
>
> = - ∂^2/∂θ^2 log Πi f(Xi|θ)
>
>
>
> = - ∂^2/∂θ^2 (Σi log f(Xi|θ))
>
>
>
> = - Σi \[∂^2/∂θ^2 log f(Xi|θ)\]
>
>
>
> Nếu xét random variable -∂^2/∂θ^2 log f(X|θ) thì -∂^2/∂θ^2 log f(Xi|θ) với i=1,2....n sẽ làm một random sample iid size n
>
>
>
> và sample mean sẽ là:
>
>
>
> \-Σi \[∂^2/∂θ^2 log f(Xi|θ)\] / n
>
>
>
> (= -\[∂^2/∂θ^2 log L(θ|**X**)\]/n = -l''(θ^|**X**)/n)
>
>
>
> Theo luật số lớn nó sẽ hội tụ xác suất về true mean, tức:
>
>
>
> \-Σi \[∂^2/∂θ^2 log f(Xi|θ)\] / n → (p) E\_θ{-∂^2/∂θ^2 log f(X1|θ)}
>
>
>
> Và E\_θ{-∂^2/∂θ^2 log f(X1|θ)} theo bổ đề 7.3.11 (xem link) sẽ bằng E\_θ\[∂/∂θ log f(X1|θ)\]^2
>
>
>
> và cái này chính là I1(θ), tức information number của sample size 1
>
>
>
> Vậy -l''(θ|**X**)/n → (p) I1(θ)
>
>
>
> và vì θ^ → θ
>
>
>
> nên -l''(θ^|**X**)/n = -l''(θ|**X**)/n | θ=θ^ → (p) I1(θ)
>
>
>
> viết lại -l''(θ^|**X**)/n → (p) I1(θ)
>
>
>
> ---
>
>
>
> Đến đây, xét MLE θ^ theo định lý (...) là estimator hiệu quả tiệm cận, nên Avar(θ^) = 1/I1(θ), cũng là:
>
>
>
> √n(θ^ - θ) → (d) n(0, 1/I1(θ))
>
>
>
> ⇔ √I1(θ) √n(θ^ - θ) → (d) √I1(θ) n(0, 1/I1(θ)) = n(0, 1)
>
>
>
> ⇒ \[√I1(θ) √n(θ^ - θ)\]^2 → (d) χ²\_1
>
>
>
> ⇔ I1(θ) n (θ^ - θ)^2 → (d) χ²\_1
>
>
>
> ⇔ n (θ^ - θ)^2 → (d) χ²\_1 / I1(θ)
>
>
>
> ---
>
>
>
>  Vậy -2 log λ(**X**) ≈ (θ0-θ^)^2 \[- l''(θ^|**X**)\]
>
> = n(θ0-θ^)^2 \[- l''(θ^|**X**) / n\]
>
>
>
> i) n (θ^ - θ)^2 → (d) χ²\_1 / I1(θ)
>
>
>
> ii) -l''(θ^|**X**) / n → (p) I1(θ)
>
>
>
> Theo Slusky theorem (nói nếu Xn → (d) X, Yn → (p) Y thì XnYn → (d) XY
>
>
>
> ⇒ (θ0-θ^)^2 \[- l''(θ^|**X**)\] → (d) I1(θ) × χ²\_1 / I1(θ)
>
>
>
> ⇔ (θ0-θ^)^2 \[- l''(θ^|**X**)\] → (d) χ²\_1
>
>
>
> ⇔ -2 log λ(**X**)  → (d) χ²\_1

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Bài viết rất xuất sắc, trình bày cực kỳ chi tiết và chính xác từng bước chứng minh toán học của định lý, đặc biệt là việc phát hiện ra lỗi in ấn ở mẫu số trong sách giáo khoa và giải thích tường tận cách áp dụng Định lý Slutsky.

**🔗 See also:** [Bổ đề Tính toán Hàm mũ](./73_methods_of_evaluating_estimators.md#node-sttybm4) · [Delta Method Variance Approximation](./101_point_estimation.md#node-2mwxabg) · [Theorem 10.1.12 (Asymptotic efficiency of MLEs)](./101_point_estimation.md#node-n1mqtrr)

<br>

<a id="node-zvfelb6"></a>

###### Poisson Likelihood Ratio Test

<p align="center"><kbd><img src="assets/4l3usqy1ydq.png" width="80%"></kbd></p>

> [!NOTE]
> Áp dụng theorem 10.3.1, -2 log λ(**x**) sẽ hội tụ về một χ²\_1.
>
>
>
> Nên để ta có một leve α test, tức là test có P(Type I error) ≤ α
>
>
>
> ⇔ P(reject H0) ≤ α khi θ ∈ Θ0
>
>
>
> ⇔ P(λ(**X**) ≤ c) ≤ α khi θ ∈ Θ0
>
>
>
> ⇔ P(log λ(**X**) ≤ log c) ≤ α khi θ ∈ Θ0
>
>
>
> ⇔ P(-2log λ(**X**) ≥ - 2log c) ≤ α khi θ ∈ Θ0
>
>
>
> Và với việc khi n rất lớn thì -log λ(**X**) trở thành χ²\_1
>
>
>
> Ta có ⇔ P(χ²\_1 ≥ - 2log c) ≤ α khi θ ∈ Θ0
>
>
>
> Từ đó ta có thể tìm ra c1 (=-2log c) khiến thỏa P(χ²\_1 ≥ c1) ≤ α. Và đó chính là χ²\_1,α
>
>
>
> Như vậy level alpha sẽ test rule là reject H0 khi observed value **x** thỏa: -2log λ(**x**) ≥ χ²\_1,α

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú của bạn rất xuất sắc, trình bày logic chặt chẽ để chứng minh miền bác bỏ của kiểm định tỷ số khả trị (LRT) dựa trên định lý Wilks. Tuy nhiên, có một lỗi gõ nhỏ ở dòng gần cuối khi ghi thiếu số 2: '-log λ(X)' cần sửa thành '-2log λ(X)'.

<br>

<a id="node-goitpzx"></a>

###### Asymptotics of Poisson LRT Statistic

<p align="center"><kbd><img src="assets/7ccqr1glt2f.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, ở đây gs sẽ minh họa như sau:
>
>
>
> Như ta vừa đã hiểu, rằng test rule là reject H0 khi observed value **x** thỏa: -2log λ(**x**) ≥ χ²\_1,α, có nghĩa là, chỉ việc tính -2 log λ(**x**) và so nó với giá trị χ²\_1,α (ví dụ với α = 0.05 thì tra bảng xem con số χ²\_1,0.05 là bao nhiêu. Còn -2 log λ(**x**) thì trong bài toán đang xét ta đã có công thức.
>
>
>
> Như vậy, ở đây gs cho sampling 10.000 bộ sample size 25 từ f(x|λ0=5), và tính -2 log λ(**x**) từ 10.000 sample này, vẽ vẽ được histogram trong hình.
>
>
>
> Ta hiểu histogram được vẽ như sau: trục ngang chia thành những ô nhỏ bề rộng Δ. Với mỗi sample **x** (tổng cộng có 10.000 sample), là một bộ 25 con số (x1,...xn), ta sẽ tính -2 log λ(**x**) và xem giá trị của nó rơi vào ô nào thì cho chiều cao cột của ô đó trong histogram tăng lên một đơn vị, và sau cùng thì ta chia cho 10000Δ. Vậy chiều cao của các cột so với nhau của histogram tại một ô sẽ là tỉ lệ số lượng sample **x** có -2 log λ(**x**) rơi vào ô đó.
>
>
>
> (Ví dụ có 3 cột với chiều cao h1 = 1000/10000Δ, h2 = 7000/10000Δ, h3 = 2000/10000Δ) Tổng diện tích các cột = 1: h1 Δ + h2 Δ + h3 Δ = 1)
>
>
>
> Lúc này có thể coi như một pmf. Và tăng số lượng 10000 lên vô cùng, thì chiều cao tại đó sẽ trở thành:
>
>
>
> lim N → ∞ \[số điểm giá trị (của random variable Y = -2 log λ(**X**) rơi vào vùng có bề rộng Δ quanh mốc a\] / NΔ
>
>
>
> Và đây chính là định nghĩa theo trường phái cổ điển (Frequentist) của xác suất Y rơi vào vùng Δ quanh (mốc a nào đó): P(a ≤ Y ≤ a + Δ)
>
>
>
> Và khi cho Δ → 0, thì ta có: lim Δ → 0 P(a ≤ Y ≤ a + Δ) / Δ,
>
>
>
> và đây chính là định nghĩa của probability density pdf: f(a).
>
>
>
> Do đó ta có thể hiểu rằng histogram này là phiên bản chưa tiến hóa của pdf -log λ(**X**), khi số lượng sample là 10.000. Nếu cho con số 10.000 tăng lên vô hạn và cho bề rộng ô nhỏ lại về 0 thì histogram sẽ ngày càng mượt, trở thành đường cong pdf.
>
>
>
> Tiếp theo người ta lại vẽ pdf của χ²\_1 là đường cong màu đen.
>
>
>
> Kết quả thể hiện qua hình vẽ 10.3.1 cho thấy nó rất match với histogram dù đây chỉ là phiên bản chưa tiến hóa, nhưng các histogram thể hiện khá sát với pdf của χ²\_1. Và cũng thể hiện qua con số trong cái bảng bên dưới khi ta so các phân vị.
>
>
>
> Hiểu cái bảng đó như sau:
>
>
>
> Ví dụ percentile 0.8, theo định nghiã ví dụ percentile 0.80 thì có nghĩa là: Ta lấy cái order statistic mà 80% các sample còn lại đều nhỏ hơn (hoặc bằng). Và khi tính cho bảng này, ta sẽ coi như có sample với size 10.000: X1,...X10.000, rồi xếp từ nhỏ đến lớn thành bộ order statistic X\_{1}, ...X\_{10.000} và lấy ra cái order statistic mà 80% đều nhỏ hơn (hoặc bằng). Giá trị của order statsitic này chính là 1.630.
>
>
>
> Soi chiếu nó trên cái histogram, thì đây sẽ là cái mốc trên trục ngang mà tại đó: diện tích của caí histogram (tổng diện tích bằng 1) sẽ bị chia làm 2 phần với phần bên trái chiếm 80%. Vì sao? Vì như đã nói cách vẽ cái histogram này: chiều cao mỗi ô là là tỉ lệ của số sample trong 10.000 sample có giá trị -2log λ(**x**) rơi vào ô đó, chia cho 10.000. Vậy nếu giả sử ta có cái mốc a nào đó, thì tổng chiều cao các cột bên trái nó sẽ chính là tỉ lệ của số sample trong 10.000 sample có giá trị -2log λ(x) nhỏ hơn mốc a đó. Và để a đạt 80%. ta sẽ kéo nó về bên phải cho đến khi thỏa. Và dễ thấy là nó sẽ nằm trúng ngay cái order statistic X\_{8000} vì đây là nó sẽ hơn hoặc bằng 8000 thằng trong 10000 (lớn hơn 7999 thằng và kể cả nó là 8000).
>
>
>
> Vậy ta hiểu vì sao cái X\_{8000}, có giá trị 1.630, chính là cái mốc mà chia histogram thành hai phần tỉ lệ (theo diện tích, hay theo tổng hiểu cao đều được, vì các phần có bề rộng như nhau, nên ví dụ bên trái có 2 cột cao h1, h2 bên phải có 3 cột h3,4. thì tỉ lệ diện tích là (Δ h1 + Δ h2) / (Δ h3 + Δ h4) cũng chính là (h1 + h2) / (h3 + h4).
>
>
>
> Và khi ta làm vậy với pdf của χ²\_1: Lấy mốc chia diện tích của pdf thành hai phần tỉ lệ 80:20, nó ra con số 1.642. Rất gần với 1.63.
>
>
>
> Tương tự cho các mốc khác. Minh họa về mặt số liệu cho hình ảnh đường cong pdf của χ²\_1 match với đồ thị histogram.
>
>
>
> Điều này minh họa cho ý mà theorem vừa rồi đã tuyên bố, khi n tăng lên vô cùng thì -2 log λ(**X**) sẽ hội tụ phân phối về χ²\_1.
>
>
>
> Và thật ra cần hiểu thế này: Việc phiên bản chưa tiến hóa đã có thể match khá tốt đường pdf của χ²\_1 có ý nghĩa như sau:
>
>
>
> Có nghĩa là, từ nay về sau, cứ việc lôi χ²\_1 ra mà tính, tức là, cứ dùng bảng tra các mốc phân vị của χ²\_1 để dùng, hay nói cách khác, cứ coi -2 log λ(**X**) như biến χ²\_1.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú giải thích rất xuất sắc, chính xác và trực quan cả về lý thuyết thống kê (định lý Wilks) lẫn cách dựng histogram thực nghiệm. Một điểm lưu ý nhỏ là định nghĩa phân vị nên diễn đạt chặt chẽ hơn một chút (80% số quan sát nhỏ hơn hoặc bằng giá trị đó), nhưng tổng thể tài liệu cực kỳ chất lượng.

**🔗 See also:** [Quy ước làm tròn phân vị mẫu](./54_order_statistic.md#node-87bnmo9) · [Chứng minh P(X=x)=0](./16_pdf_pmf.md#node-29g5dq1)

<br>

<a id="node-pa8m0ub"></a>

###### Theorem 10.3.3 Likelihood Ratio Test

<p align="center"><kbd><img src="assets/ap3adni0r8c.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/bo0yzy52oq.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, từ cái theorem vừa rồi, khi đại ý nói rằng khi n lớn lên vô cùng thì - 2 log λ(**X**) sẽ trở thành một χ²\_1, do đó, theorem này mới đem áp dụng điều này vào bài toán hypothesis testing, cụ thể là như sau:
>
>
>
> Như bối cảnh bữa giờ là, ta quan tâm đến bài toán hypothesis testing: H0: θ ∈ Θ0 vs H1: θ ∉ Θ0, và một loại test khá hữu ích là Likelihood Ratio Test (LRT), với test rule là λ(**x**) ≤ c. Và λ(**x**) ≤ c ⇔ -2 log λ(**x**) ≥ -2 log(c)
>
>
>
> Và để có một level α test, thì c phải là mốc nào đó khiến khi θ ∈ Θ0 thì P(reject H0) = P(**X** ∈ Rejection region) = P(-2 log λ(**X**) ≥ -2 log(c)) ≤ α.
>
>
>
> Đặt c\* = -2 log(c), bài toán trở thành: tìm c\* để P(-2 log λ(**X**) ≥ c\*) ≤ α.
>
>
>
> Khi đó tính c từ c\*, thì ta sẽ có một level α LRT test: Reject H0 khi λ(**X**) ≤ c,
>
>
>
> hay cứ để theo c\* cũng được: Reject H0 khi -2 log λ(**x**) ≥ c\*
>
>
>
> Vấn đề là để tìm c\* thỏa P(-2 log λ(**X**) ≥ c\*) ≤ α rất khó.
>
>
>
> Vì, khi xét sự thật rằng đây là xác suất liên của một event liên quan đến statistic -2 log λ(**X**), và ta không biết distribution của nó. Ví dụ như nếu biết nó là Z \~ normal(0, 1) chẳng hạn, thì bài toán trở thành tìm c\* để P(Z ≥ c\*) ≤ α, ta chỉ việc tìm mốc phần diện tích pdf bên phải bằng α là xong, và ta có thể tra bảng để có mốc này, và nó chính là cái được kí hiệu bởi Z\_α.
>
>
>
> Nhưng sự thật thì ta không biết distribution của Y = -2 log λ(**X**) là gì.
>
>
>
> Tuy nhiên, một theorem đã chứng minh rằng Y = -2 log λ(**X**) là một random variable hội tụ phân phối về χ²\_1.
>
>
>
> Từ đó ta có thể xấp xỉ việc tìm c\* thỏa P(-2 log λ(**X**) ≥ c\*) ≤ α bằng bài toán:
>
>
>
> tìm c\* để P(χ²\_1 ≥ c\*) ≤ α, và như vậy, có thể tra bản để có mốc c\*, tương tự như Z\_α, thì ở đây chính là χ²\_1\_α.
>
>
>
> ---
>
>
>
> Tuy nhiên theorem này nói rằng, ta không cần dùng χ²\_1, tứcχ²\_ν với ν = 1, thay vào đó, ông nói ta có thể dùng ν theo định nghĩa trong theorem 10.3.3 mà mình sẽ nói sau (ở đây hiểu bức tranh toàn cảnh trước) Nhưng dù gì đi nữa, cơ bản chỉ là, dựa vào bảng tra của χ²\_ν, ta tra ra mốc χ²\_ν,α. Và đó chính là c\*
>
>
>
> Từ đó, ta có level α LRT test rule là: Reject H0 khi -2 log λ(**X**) ≥ χ²\_ν,α
>
>
>
> Và theorem này cũng nói rằng, khi n tăng lên, thì cái test này, không chỉ là level α test, mà nó thậm chí dần trở thành size α test, tức là xác suất mắc Type I error không chỉ ≤ α mà sẽ trở nên gần bằng α. Và gs Casella gọi là **Asymptotic size α test**.
>
>
>
> ---
>
>
>
> Recall chút về size α vs level α test. 
>
>
>
> Với level α test, với định nghĩa là test có xác suất mắc Type I error không lớn hơn α: Tức là sup\_θ∈Θ0 P(reject H0) ≤ α
>
>
>
> còn size α test, là test có sup\_θ∈Θ0 P(reject H0) = α
>
>
>
> Vậy thì gs lưu ý rằng, cái định nghĩa **asymptotic size α test** chỉ có nghĩa là: khi n → ∞ thì P(reject H0) → α với mỗi θ ∈ Θ, nhưng có thể chưa chắc (hay đôi khi thì không thỏa) n → ∞ thì sup\_θ∈Θ0 P(reject H0) = α (cái này hơi khó hiểu), nhưng đại ý gs nói là thực tế thì ta có thể coi như khi n → ∞ thì ta sẽ có size α test.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Bài viết giải thích rất trực quan, logic và nắm bắt xuất sắc bản chất việc chuyển từ phân phối chính xác sang phân phối tiệm cận chi-bình phương. Điểm cần lưu ý là định nghĩa chính xác của 'size' (kích thước) của kiểm định là supremum của xác suất sai lầm loại I trên tập giả thuyết không, chứ không chỉ đơn thuần là bằng $\alpha$.

<br>

