# 10.3 Hypothesis Testing

📊 **Progress:** `6` Notes | `6` Screenshots | `5` AI Reviews

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
> Như ta vừa đã hiểu, rằng test rule là reject H0 khi observed value **x** thỏa: -2log λ(**x**) ≥ χ²\_1,α, có nghĩa là, chỉ việc tính -2 log λ(**x**) và so nó với giá trị χ²\_1,α (ví dụ với α = 0.05 thì tra bản xem con số χ²\_1,0.05 là bao nhiêu. Còn -2 log λ(**x**) thì trong bài toán đang xét ta đã có công thức.
>
>
>
> Như vậy, ở đây gs cho sampling 10000 bộ sample size 25 từ f(x|λ0=5), và tính -2 log λ(**x**) từ 10.000 sample này, vẽ vẽ được histogram trong hình.
>
>
>
> Sau đó ông vẽ đường pdf của χ²\_1 là đường nét liền
>
>
>
> Kết quả cho thấy quả thật với n = 25 thôi, nhưng các histogram thể hiện khá sát với pdf của χ²\_1. Minh họa cho ý -2 log λ(**X**) → (d) χ²\_1 mà Theorem lúc nãy đã nói.

<br>

