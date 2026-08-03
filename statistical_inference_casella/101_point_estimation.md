# 10.1 Point Estimation

📊 **Progress:** `37` Notes | `43` Screenshots | `18` AI Reviews

---
<a id="node-2ixm3r0"></a>

## 10.1 Point Estimation

<br>

<a id="node-wapn3q2"></a>

## Đánh giá tiệm cận

<p align="center"><kbd><img src="assets/xsbujc3lv3.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bữa giờ ta xét các hành vi của các quy trình suy luận trong bối cảnh là **finite-sample**, tức là mẫu có số lượng hữu hạn. Chapter này sẽ xem xét tính asymptotic - tính chất mô tả hành vi của quy trình khi kích thước mẫu tăng lên infinite.
>
>
>
> Ta sẽ đánh giá tính chất này của cả 3 quy trình suy luận chính: point estimation, hypothesis testing và interval estimation. Đặc biệt tập trung vào các phương pháp liên quan đến maximum likelihood

<br>

<a id="node-ozps89j"></a>

### Giá trị tiệm cận

<p align="center"><kbd><img src="assets/pgt1cb77ef.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là, gs nói sơ về giá trị của cái này là nó khiến việc tính toán trở nên đơn giản hóa khi ta cho phép số lượng mẫu tăng lên indefinite.
>
>
>
> Có những cách đánh giá trở nên bất khả thi khi xét trong bối cảnh finite-sample nhưng trở nên khả thi khi xét trong bối cảnh infinte bao gồm các technique nổi tiếng như bootstrap và M-estimation.

<br>

<a id="node-eqqhqsv"></a>

#### Tính nhất quán chuỗi ước lượng

<p align="center"><kbd><img src="assets/1djij1bol1i.png" width="80%"></kbd></p>

> [!NOTE]
> Xét vấn đề đánh giá tiệm cận với phương pháp suy luận thuộc loại point 
> estimation. Đầu tiên nói về tính chất nhất quán (consistency)
>
>
>
> Thì đại ý là, cái này nó nền tảng đến nỗi nếu một estimator mà inconstent
> thì có thể phải đặt câu hỏi là có đáng để dùng không.
>
>
>
> Thế thì đầu tiên, gs nói trong bối cảnh đánh giá tiệm cận, thật ta ta nên
> hiểu là ta sẽ  **XÉT MỘT CHUỖI CÁC ESTIMATOR**, **CHỨ KHÔNG PHẢI
> LÀ MỘT CÁI ĐƠN LẺ DÙ CHO KHI NÓI THÌ TA NÓI "CONSISTENT 
> ESTIMATOR**" trông có vẻ như là tính chất của một estimator đơn lẻ.
>
>
>
> Tức là hình dung, với sample X1,X2,...Xn thì kiểu như ta dùng cùng một
> quy trình inference để xây dựng một chuỗi các point estimator với kích
> thước mẫu tăng dần. W1(X1), W2(X1,X2),....Wn(X1,...Xn)
>
>
>
> ví dụ, lấy Xbar đi (nó là point estimator cho population mean như đã biết)
>
>
>
> thì ta có Xbar1(X1) = X1, Xbar2(X1,X2) = (X1+X2)/2, Xbar_n(X1,..Xn)
> = (Σi=1:n Xi) / n
>
>
>
> Mình ghi Xbar1(X1) là hoàn toàn hợp lệ, vì gs Casella trong mấy chương
> trước đã nói, Xbar, hay S^2 thật ra chỉ là ghi cho gọn, ghi rõ phải là Xbar(**X**)
> hay S^2(**X**) để thể hiện nó là function của sample **X**

<br>

<a id="node-tpmiims"></a>

##### Chuỗi Estimator Nhất Quán

<p align="center"><kbd><img src="assets/0jrw9jv6li8l.png" width="80%"></kbd></p>

> [!NOTE]
> Ta được học định nghĩa của cái gọi là một chuỗi các estimator có tính nhất 
> quán (consistent) đó là nếu như Wn thỏa: lim n → inf P_θ(|Wn - θ| < ε) = 1.
> Mang ý nghĩa là khi kích thước mẫu tăng lên vô hạn thì xác suất mà estimator
> khác với θ sẽ cực kì nhỏ, hay, xác suất estimator sẽ có giá trị chính xác với θ 
> là cực lớn.
>
>
>
> Dừng lại chút xíu, vì sao P_θ(|Wn - θ| < ε) lại là hàm theo θ?
>
>
>
> À, đơn giản là vì Wn ở đây là estimator của θ, theo định nghĩa, là một function 
> của sample **X** = (X1,...Xn), cũng còn gọi là một statistic. Và vì vậy, nó là một
> random variable, có distribution sẽ phụ thuộc θ luôn. Nên xác suất của |Wn - θ|
> < ε dĩ nhiên là xác suất của một event liên quan đến rv Wn có distribution
> phụ thuộc θ nên đương nhiên nó phải phụ thuộc θ. Đó mới là lí do có chữ θ 
> ở dưới, chứ ko phải là vì θ xuất hiện trong |Wn - θ|

<br>

<a id="node-4pzd0to"></a>

- **Hội tụ xác suất thống kê**

<p align="center"><kbd><img src="assets/2e24ssorah.png" width="80%"></kbd></p>

> [!NOTE]
> Nhờ hiểu bản chất chữ θ ở dưới chân chữ P (P_θ(..)) nên ta hiểu đoạn này
> như vầy:
>
>
>
> Đại ý là trong định nghĩa 5.5.1, có nói về khái niệm gọi là CONVERGENCE
> IN PROBABILITY: như vầy: Chuỗi các random variable X1,...Xn được gọi là 
> converge in probability to X nếu như lim n → inf P(|Xn - X| < ε) = 1.
>
>
>
> Nhưng ở đây, mình hiểu đoạn này nói vầy:
>
>
>
> Khi mình nói chuỗi X1,...Xn hội tụ xác suất về X, thì thực ra chúng ta đang
> xét trong một distribution f(x|θ) với θ mang giá trị nào đó.
>
>
>
> Còn khi nói chuỗi W1, ...Wn hội tụ xác suất về θ, thì ta đang nói trong bất kì
> một θ nào.
>
>
>
> Có nghĩa là, dù giá trị thực sự của θ là bao nhiêu, thì chuỗi các estimator
> W1,..Wn (nhắc lại, là các point estimator được xây dựng từ cùng một "công
> thức", chỉ là với mẫu X có số lượng tăng dần đến infinite) cũng phải hội
> tụ về đó
>
>
>
> Thành ra trong bối cảnh của chương 10 này, kiểu như với mỗi θ ta sẽ có
> một thành viên cụ thể trong một họ các distribution index bởi θ. Và trong
> họ nào, thì cũng xảy ra hiện tượng W1,...Wn converge về θ hết.

**🔗 See also:** [Hội tụ xác suất](./55_convergence_concepts.md#node-ybskg1i)

<br>

<a id="node-yx0vqu9"></a>

- **Tính nhất quán của Xbar**

<p align="center"><kbd><img src="assets/3cll4olsoft.png" width="80%"></kbd></p>

> [!NOTE]
> Qua ví dụ này, cho X1,X2,...iid ~ n(θ, 1) và xét chuỗi các sample mean của 
> random sample size n: Xbar_n = (Σi Xi) / n.
>
>
>
> Còn nhớ, ta đã chứng minh, sample mean Xbar của random sample X1,...
> Xn ~ normal(μ, σ^2) sẽ có distribution normal(μ, σ^2/n). Nên ở đây Xbar_n
> sẽ là random variable ~ normal(θ, 1/n)
>
>
>
> Ôn lại mấy bài trước chút xíu: Ta đang bàn về tính consistency của một
> point estimator. Theo định nghĩa là khi khi kích thước mẫu tăng lên đến vô hạn 
> thì ta có một chuỗi các estimator (mỗi cái dựa trên mẫu size tương ứng)
> sẽ converge in probability về θ thể hiện bởi lim n → inf P(|Wn - θ| < ε) = 1
>
>
>
> Vậy ở đây ta xét xác suất P_θ(|Xbar_n - θ| < ε).
>
>
>
> ⇨ P_θ(|Xbar_n - θ| < ε) = P_θ(-ε < Xbar_n - θ < ε)
>
>
>
> = P_θ(-ε√n < Xbar_n - θ/(1/√n) < ε√n)
>
>
>
> Ở trên ta đã nói Xbar_n ~ normal(θ, 1/n) thì theo location scale theorem, 
> (Xbar_n - θ)/(1/√n) sẽ là rv ~ normal(0, 1)
>
>
>
> ⇨ P_θ(-ε√n < Z < ε√n), với Z = Xbar_n - θ/(1/√n), là normal(0,1)
>
>
>
> Vậy thì tới đây dễ thấy khi n → inf, thì P_θ(-ε√n < Z < ε√n) → P_θ(-inf < Z < inf) = 1
>
>
>
> Vậy theo định nghĩa Xbar là consistent estimator của θ

<br>

<a id="node-u07qsmw"></a>

- **Điều kiện vững ước lượng**

<p align="center"><kbd><img src="assets/rpgc3s7hqf.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đại ý là gs nói rằng thường thì ta cũng chẳng cần phải chứng minh
> một estimator là consistency theo kiểu chứng minh cái nó hội tụ xác suất
> về θ như trong định nghĩa. Mà có cách khác dễ làm hơn như sau.
>
>
>
> Thứ nhất, cần ôn lại cái bất đẳng thức Chebyshev: P(g(X) ≥ r) ≤ Eg(X) / r
>
>
>
> Chứng minh rất dễ, làm lại luôn cho vui: 
>
>
>
> Xét vế trái, Eg(X), dĩ nhiên LOTUS cho ta tính nó bằng:
>
>
>
> Eg(X) = ∫g(x)f(x)dx với f(x) là pdf của X và tích phân là trên toàn miền -inf:inf.
>
>
>
> mà tích phân vốn có ý nghĩa là phần diện tích dưới đồ thị hàm số trong 
> khoảng đang xét.
>
>
>
> nên ∫g(x)f(x)dx ≥ ∫_{x: g(x) > r} g(x)f(x)dx 
>
>
>
> Và vì đang xét trên miền {x: g(x) > r} nên 
>
>
>
>  ∫_{x: g(x) > r} g(x)f(x)dx ≥ ∫_{x: g(x) > r} rf(x)dx = r ∫_{x: g(x) > r} f(x)dx
>
>
>
> và cái này chính là r P(g(X) > r).
>
>
>
> Vậy Eg(X) ≥ r P(g(X) > r) ⇨ P(g(X) > r) < Eg(X) / r.
>
>
>
> Quay lại đây, áp dụng vào random variable (Wn - θ)^2, ta cũng có 
>
>
>
> P_θ((Wn - θ)^2 ≥ ε^2) ≤ E_θ[(Wn - θ)^2] / ε^2.
>
>
>
> ⇔ P_θ(|Wn - θ| ≥ ε) ≤ E_θ[(Wn - θ)^2] / ε^2.
>
>
>
> -----
>
>
>
> Thế thì, tới đây nếu ta chứng minh được Wn thỏa E_θ[(|Wn - θ|)^2] / ε^2 → 0
> khi n → inf thì dĩ nhiên vế trái cũng → 0.
>
>
>
> Từ đó ta chỉ cần quan tâm vế trái E_θ[(Wn - θ)^2]
>
>
>
> Còn nhớ, theo công thức VarX = EX^2 - (EX)^2 ⇨ EX^2 = Var X + (EX)^2
>
>
>
> ⇨ E_θ[(Wn - θ)^2] = Var(Wn - θ) + [E_θ(Wn - θ)]^2
>
>
>
> = Var(Wn) + [E_θ(Wn - θ)]^2   | Var(X + c) = Var(X)
>
>
>
> Và cái E_θ(Wn - θ) = E_θ[Wn] - θ, chính là định nghĩa của Bias(Wn).
>
>
>
> ⇨ E_θ[(Wn - θ)^2] = Var(Wn - θ) + [Bias(Wn)]^2
>
>
>
> Và như vậy dĩ nhiên chỉ cần chứng minh Var(Wn - θ) → 0 và Bias(Wn) → 0
> khi n → inf, thì E_θ[(Wn - θ)^2] sẽ → 0 → P_θ(|Wn - θ| ≥ ε) → 0, và ta có
> consistent sequence of estimator Wn của θ

**🔗 See also:** [Bất đẳng thức Markov và chứng minh](./36_inequalities.md#node-u9zgfoi)

<br>

<a id="node-47kutgs"></a>

- **Tính nhất quán của Xbar**

<p align="center"><kbd><img src="assets/zrgxsperwp.png" width="80%"></kbd></p>

> [!NOTE]
> Áp dụng theorem này, quay lại ví dụ hồi nãy thì chỉ cần lập luận như sau:
>
>
>
> Vì Xbar_n ~ normal(θ, 1/n) ⇨ dĩ nhiên E_θ[Xbar_n] = θ → Bias(Xbar_n) = 0
>
>
>
> Và Var(Xbar_n) = 1/n ⇨ khi n → inf dĩ nhiên Var(Xbar_n) → 0
>
>
>
> Vậy theo theorem vừa rồi Xbar_n là consistent.
>
>
>
> HƠn nữa trong ví dụ đó, là cho X1,...Xn ~ normal(θ, 1) thì ta biết Xbar_n
>  ~ normal(θ, 1/n)
>
>
>
> Nhưng theorem 5.2.6 ta đã học, nói rằng X1,...Xn ko nhất thiết là normal
> mà chỉ cần có mean μ và variance hữu hạn σ^2.
>
>
>
> Thì khi đó E[Xbar] cũng là μ và Var(Xbar) cũng bằng σ^/n.
>
>
>
> Và theo đó, Xbar cũng là consistent estimator của μ 
>
>
>
> Như vậy, mọi Xbar_n của một sample iid có population với variance hữu
> hạn sẽ đều là consistent estimator của μ

**🔗 See also:** [Tính chất trung bình phương sai mẫu](./52_of_random_variables_from_a_random_sample.md#node-411jdqg)

<br>

<a id="node-itwfbr1"></a>

- **Định lý ước lượng nhất quán**

<p align="center"><kbd><img src="assets/jv63p5nsi2p.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là, gs nói rằng, hồi đầu ta đã đề cập đến việc, có đáng để phải để tâm đến một inconsistent estimator không. Thì ở đây ông nói đại ý là, sở dĩ nói vậy là vì theoerem sau đây ta sẽ thấy là, nếu Wm là một consistent estimator thì với chuỗi a1,a2,...và b1,b2,...thỏa điều kiện chuỗi a hội tụ về 1, chuỗi b hội tụ về 0 thì Un = anWn + bn sẽ cũng là một consistent estimator. Ý nói, có rất nhiều consistent estimator, nên ko việc gì phải xem xét một inconsistent

<br>

<a id="node-d19dn75"></a>

- **Tính nhất quán của MLE**

<p align="center"><kbd><img src="assets/5qh7s62fw0s.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jjkpmvkmzz.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, cuối cùng, gs nói về một theorem nói rằng, bất kì một ML estimator θ^ml(**X**) của một parameter θ nào cũng là consistent sequence of estimator của θ, và ông nói đây là lần đầu tiên ta gặp một trường hợp trong đó một cách tiếp cận cụ thể lại đảm bảo ta sẽ có được một estimator có được một tiêu chí tối ưu nào đó. (ông nói vậy là vì, cho đến nay, các phương pháp mà ta học để đi xây dựng một estimator chưa đảm bảo là nó sẽ là cái tốt nhất theo các tiêu chí nào đó, thì ở đây, với tiêu chí consistent, thì MLE approach lại đảm bảo là ta sẽ có được một consistent estimator)
>
>
>
> Theorem 10.1.6 nói rằng, nếu hàm likelihood mà thỏa tính chất gọi là "regularity conditions" thì: τ(θ^) sẽ hội tụ xác suất về τ(θ), thể hiện bởi lim n → inf P\_θ(|τ(θ^) - τ(θ)| ≥ ε) = 0 
>
>
>
> Và theo định nghĩa của consistent sequence of estimator rằng: Nếu chuỗi Wn, là estimator của θ hội tụ xác suất về θ thì Wn là consistent sequence of estimator của θ.
>
>
>
> Thì dĩ nhiên ở đâu nếu ta có chuỗi τ(θ^) hội tụ xác suất về τ(θ) thì chuỗi τ(θ^) sẽ là consistent sequence of estimator của τ(θ).
>
>
>
> Quay lại xem kĩ hơn phần chứng minh và regularity condition sau.

**🔗 See also:** [Theorem 10.1.12 (Asymptotic efficiency of MLEs)](#node-n1mqtrr) · [10.1.3 Calculations and Comparisons](#node-iwgmm5t) · [Theorem 10.1.6 on Consistent Estimators](#node-cpdjv2x) · [Asymptotic Efficiency of Estimator p̂](#node-ct81g3i)

<br>

<a id="node-e2xtw8s"></a>

- **Tính nhất quán và hiệu quả**

<p align="center"><kbd><img src="assets/f5biezgmq1f.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là đánh giá chuỗi estimator theo tiêu chí consistency là nói đến tính chất liên quan đến việc estimator đó chính xác đến mức nào trong việc estimate cái param mà nó đang estimate.
>
>
>
> Để rồi, ta sẽ xét một tiêu chí khác, đánh giá estimator ở khía cạnh: asymptotic variance của nó.
>
>
>
> Có nghĩa là, hiểu đại khái là consistency nói đến việc: à, chuỗi estimator (với sample size tăng dần) sẽ có thể ngày càng estimate chính xác giá trị của param không. Thì efficiency sẽ đánh giá rằng khi sample size tăng dần thì mức biến động của estimator sẽ thế nào.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **92/100**
>
> Bài làm thể hiện sự hiểu biết sâu sắc và chính xác về các khái niệm consistency và efficiency như được trình bày. Tuy nhiên, cần sử dụng ngôn ngữ học thuật trang trọng hơn thay vì các cụm từ không chính thức để nâng cao chất lượng trình bày.

<br>

<a id="node-62aug4x"></a>

- **Phương sai tiệm cận và giới hạn**

<p align="center"><kbd><img src="assets/u9uk00unw4.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/uatx3rz9lok.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/72ycte4wacu.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì gs nói đại khái là khi tính **phương sai tiệm cận (asymptotic variance)**, ta có thể sẽ **bị cám dỗ bởi (tempting) cách làm như sau**: Gọi Tn là estimator (dựa trên sample size n), thì Var(Tn) là variance của Tn, khi đó ta xem xét variance của Tn tại limit:
>
>
>
> lim n → ∞ {kn Var(Tn)}
>
>
>
> Với kn là chuỗi các constant đóng vai trò normalizing constant (chưa hiểu lắm)
>
>
>
> Thế thì ta định nghĩa ra một khái niệm khác: giới hạn phương sai (limiting variance) được định nghĩa bởi: Nếu một (sequence of estimator) có phương sai tiệm cận lim n→∞ kn Var(Tn) = τ^2 < ∞, thì τ^2 được gọi là **limiting variance**.
>
>
>
> Lấy ví dụ, Xbar_n, là sample mean của iid normal(μ, σ^2) sample size n, như đã biết, nó sẽ một normal(μ, σ^2/n). Như vậy Var(Xbar_n) = σ^2/n ⇨ n Var(Xbar_n) = σ^2. Do đó, với Xbar_n thì lim n → ∞ n Var(Xbar_n) = σ^2, là con số hữu hạn (finite), < ∞. Do đó theo định nghĩa trên, σ^2 chính là limiting variance. (trong trường hợp này, chuỗi {kn} chính là {1,2,....n}.
>
>
>
> ---
>
>
>
> Thế thì đại ý là, việc đánh giá asymptotic variance bằng cách lấy giới hạn của variance của Tn sẽ không vấn đề gì khi Tn là sample mean, vì lim n → inf Var(Tn) = lim n → inf σ^2/n = 0. Và với một số Tn khác cũng vậy.
>
>
>
> Nhưng nếu ta quan tâm đến asymtotic variance của Tn = 1/Xbar_n, thì ta sẽ gặp vấn để vì Var(Tn) sẽ = inf, vì sao nhỉ?
>
>
>
> Chỉ cần hiểu đại khái, theo định nghĩa Var(Tn) = E\[Tn^2\] - (ETn)^2 = E\[(1/Xbar_n)^2\] - \[E(1/Xbar_n)\]^2
>
>
>
> Với E\[(1/Xbar_n)^2\], theo LOTUS, = ∫(1/xbar_n)^2 f(xbar_n) d(xbar_n) với f là pdf của xbar_n. Ta đã biết, Xbar_n của sample \~ normal(μ, σ) sẽ có limiting distribution là normal(μ, σ^2/n), tức là Xbar_n sẽ hội tụ distribution về một rv thuộc phân phối normal(μ, σ^2). thế thì với phân phối này, trong tích phân ∫(1/xbar_n)^2 f(xbar_n) d(xbar_n) đang nói, tồn tại xác suất dương nào đó để xbar_n = 0, khiến tích phân này = inf (explode), vì sao, vì range của normal là từ -inf, inf, nên có nghĩa là tại xbar_n=0, vẫn tồn tại giá trị pdf không âm.
>
>
>
> Không cần xét cái term thứ hai, lập luận trên cũng đủ để nói Var(1/Xbar_n) = ∞.
>
>
>
> ---
>
>
>
> Vấn đề là, trong ví dụ 5.5.23, mình đã học về Delta method giúp ta có công thức tính xấp xỉ mean và variance của 1/Xbar_n, có thể ôn lại chút xíu như sau:
>
>
>
> Delta method rất đơn giản thôi: Giả sử ta đang muốn xem xét random variable g(T) (T là random variable nào đó \~ f(t|μ). Thì lập luận như vầy: Theo giải tích, nếu xét phạm vi t \~ μ, thì ta có xấp xỉ bậc một: g(t) ≈ g(μ) + g'(μ)(t-μ)
>
> Áp dụng hai cái hàm số xấp xỉ nhau này lên random variable T, ta sẽ có hai random variable xấp xỉ:\
> \
> g(T) ≈ g(μ) + g'(μ)(T-μ)
>
>
>
> Thế thì xét E\_μ\[g(T)\], vì xấp xỉ trên nên ta có:
>
>
>
> E\_μ\[g(T)\] ≈ E\_μ\[g(μ) + g'(μ)(T-μ)\] = E\_μ\[g(μ)\] + E\_μ\[g'(μ)(T-μ)\]
>
>
>
> = g(μ) + g'(μ) E\_μ\[T-μ\]
>
>
>
> = g(μ) + g'(μ) (E\_μ\[T\]-μ)
>
>
>
> = g(μ) + g'(μ) (μ-μ)
>
>
>
> = g(μ)
>
>
>
> Vậy E\_μ\[g(T)\] ≈ g(μ)
>
>
>
> Còn Var\_μ\[g(T)\] = E\_μ{g(T) - E\_μ\[g(T)\]}^2
>
>
>
> ≈ E\_μ{g(T) - g(μ)}^2 (thay E\_μ\[g(T)\] ≈ g(μ))
>
>
>
> ≈ E\_μ{g(μ) + g'(μ)(T-μ) - g(μ)}^2 (thay g(T) ≈ g(μ) + g'(μ)(T-μ))
>
>
>
> = E\_μ\[g'(μ)(T-μ)\]^2
>
>
>
> = (g'(μ))^2 E\_μ\[(T-μ)\]^2
>
>
>
> = (g'(μ))^2 Var\_μ\[T\]
>
>
>
> Áp dụng với T = Xbar_n là có mean E(Xbar_n) = μ và variance Var(Xbar_n) và g(Xbar_n) = 1/Xbar_n:
>
>
>
> ⇨ g'(t) = -1/t^2
>
>
>
> E\[1/Xbar_n\] = 1/E\[Xbar_n\] = 1/μ 
>
>
>
> Var\[1/Xbar_n\] = (-1/μ^2)^2Var\_μ\[Xbar\] = **(1/μ^4) Var\_μ\[Xbar\]**
>
>
>
> Và như vậy, ý chính muốn nói, với Tn = 1/Xbar_n, thì khi ta t**ính chính xác variance của nó, được ∞**. Nhưng tính xấp xỉ, thì lại là **(1/μ^4) Var\_μ\[Xbar\]**
>
>
>
> ---
>
>
>
> Như vậy, tóm lại, việc tính asymptotic variance của Tn theo kiểu lấy Variance của Tn tại limit (lim n → inf Var(Tn), gọi là limiting variance không ổn, trong khi đó, dùng cách làm xấp xỉ thì lại thực tế hơn và hữu ích hơn. Thành ra ta sẽ có **định nghĩa chính thức của asymptotic variance** như sau:
>
>
>
> đó là, cho chuỗi estimator (dựa trên sample size n) Tn: sao cho kn (Tn - τ(θ)) hội tụ phân phối về n(0, σ^2), khi đó σ^2 gọi là asymptotic variance của Tn. Có nghĩa là, thì **thay vì dùng Var(Tn) tại limit, ta dùng variance của cái phân phối normal là limit distribution của** kn (Tn - τ(θ)) **làm asymptotic variance**. Như vậy, với Tn = 1/Xbar, thay vì dùng Var(1/Xbar) tại limit (=inf), ta dùng (1/μ^4) Var\_μ\[Xbar\]
>
>
>
> Và một điểm thú vị nữa, đó là asymptotic variance thì luôn nhỏ hơn limiting variance.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú của bạn rất chính xác và có chiều sâu đáng kinh ngạc. Bạn không chỉ tóm tắt nội dung mà còn giải thích chi tiết lý do tại sao Var(1/Xbar_n) lại là vô cùng và tự mình chứng minh lại phương pháp Delta, thể hiện sự hiểu biết sâu sắc và khả năng suy luận tốt.

**🔗 See also:** [Phương sai Tỷ lệ Odd](./55_convergence_concepts.md#node-44z7xj9) · [Definition 10.1.11 Asymptotic Efficiency](#node-bgijdqy)

<br>

<a id="node-slkl4m8"></a>

- **Example 10.1.10 Large-sample Mixture Variances**

<p align="center"><kbd><img src="assets/h6lw6s2q3q.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ này ta có một hierarchical modal:
>
>
>
> Yn|Wn = wn \~ n(0, wn + (1-wn)σn^2)
>
>
>
> Wn \~ Bern(pn)
>
>
>
> Đã gặp cái này ở mấy chương trước có nghĩa là nếu biết giá trị của Wn (= wn) thì Yn là normal mean 0 có variance wn + (1-wn) σn^2. Và bản thân Wn thì là một rn \~ Bern(pn).
>
>
>
> Vậy thì ở đây, gs nói cái này cũng chính là mixture model khi ta thấy Yn \~ n(0,1) với xác suất pn và Yn \~ n(0, σn^2) với xác suất 1 - pn. Là sao ta:
>
>
>
> Khái niệm mixture model, trong sách này (Casella) cho đến giờ chưa được nghe. Nhưng, quachapter 2 của PRML của C.Bishop đã biết khái niệm mixture model, cũng đơn giản, đại khái như sau: f(x) = convex combination của các fi(x): ∑i αi fi(x). với fi(x) là các pdf của distribution. Ví dụ f(x|**μ**, **σ^2**) = αi fi(x|μi, σi^2) với fi là pdf của Normal(μi, σi^2), và αi ≥ 0 ∀i, và ∑i αi = 1, thì ta sẽ có một Gaussian (normal) mixture.
>
>
>
> Vậy thì ở đây, ta có f1(x|0,1) là pdf của Normal(0,1) và f2(x|0, σn^2) là pdf của Normal(0, σn^2) và convex combination coefficient là α1 = pn và α2 = 1-pn.
>
>
>
> Chú ý là Yn|(Wn=wn) \~ n(0, wn + (1 - wn) σn^2) & Wn \~ Bern(pn), cũng là cái Gaussian mixture nói trên, KHÔNG PHẢI LÀ MỘT NORMAL DISTRIBUTION có variance là wn + (1 - wn) σn^2. Mà cách viết n(0, wn + (1 - wn) σn^2) chỉ có nghĩa là, nếu Wn = 1 (vốn là sự kiện có xác suất xảy ra là pn) thì Yn|Wn=1 sẽ là rv \~ normal(0,1), và nếu Wn = 0, là sự kiện có xác suất xảy ra là 1-pn, thì Yn|Wn=1 sẽ là rv \~ normal(0, σn^2). Nên gs mới nói câu "ta quan sát thấy Yn \~n(0,1) với xác suất pn và Yn\~n(0, σn^2) với xác suất 1-pn.
>
>
>
> Dùng công thức 4.4.7 (xem link) ta có thể có công thức của Var(Yn) = pn + (1 - pn)σn^2, để rồi ta sẽ nhận định rằng cái này tại limit (tức limiting variance) chỉ hữu hạn nếu giá trị tại limit của (1 - pn)σn^2 cũng hữu hạn.
>
>
>
> Nhưng với asymptotic variance thì ta sẽ tính được = 1. Thử xem họ tính vậy là sao?
>
>
>
> P(Yn < a) = pnP(Z < a) + (1-pn) P(Z < a/σn), dòng này là sao?
>
>
>
> P(Yn < a) tức là FYn(a) (cdf của Yn tại a)
>
>
>
> gọi fYn là pdf của Yn, ta biết theo định nghĩa của cdf và pdf, ta có:
>
>
>
> FYn(a) = ∫-inf:a fYn(t)dt
>
>
>
> Vì Yn \~ Gaussian mixture → fYn(t) = pn N(t|0,1) + (1-pn) N(t|0, σn^2)
>
>
>
> ⇨ FYn(a) = ∫-inf:a fYn(t)dt = ∫-inf:a\[pn N(t|0,1) + (1-pn) N(t|0, σn^2)\] dt
>
>
>
> = ∫-inf:a \[pn N(t|0,1)\] dt + ∫-inf:a \[(1-pn) N(t|0, σn^2)\] dt
>
>
>
> = pn ∫-inf:a N(t|0,1) dt + (1-pn) ∫-inf:a N(t|0, σn^2) dt
>
>
>
> = pn ∫-inf:a N(t|0,1) dt + (1-pn) ∫-inf:a N(t|0, σn^2) dt
>
>
>
> ∫-inf:a N(t|0,1) dt chính là cdf tại a của Z \~ normal(0,1), tức FZ(a), cũng là P(Z < a)
>
>
>
> còn ∫-inf:a N(t|0, σn^2) dt chính là cdf tại a của W \~ normal(0, σn^2), tức FW(a), và cũng là P(W < a)
>
>
>
> Mà theo location scale theorem ta cũng biết W chính là Zσn, nên P(W < a) = P(Zσn < a) = P(Z < a/σn)
>
>
>
> Vậy ta có P(Yn < a) = pn P(Z < a) + (1-pn) P(Z < a/σn).
>
>
>
> ---
>
>
>
> Thế thì, hồi nãy, với limiting variance ta nói, chỉ khi (1-pn)σn^2 → giá trị hữu hạn khi n → inf thì limiting variance mới finite.
>
>
>
> Vậy thì ở đây, ta thử cho (1-pn)σn^2 → inf luôn (bằng cách cho pn → 1 và σn → ∞, thì ta sẽ thấy khi đó:
>
>
>
> P(Yn < a) = pn P(Z < a) + (1-pn) P(Z < a/σn) sẽ → 1 × P(Z < a) + 0 × P(Z < 0) = P(Z < a)
>
>
>
> Mà P(Yn < a) → P(Z < a) tức là FYn(a) → FZ(a), theo định nghĩa cuả hội tụ phân phối (converge in distribution), đây chính là nói Yn → (d) Z. Và theo định nghĩa của asysmtotic variance, là variance của limiting distribution, thì ta có asymtotic variance của Yn = Var(Z) = 1.
>
>
>
> Như vậy, khi ta cho pn → 1, σn → ∞ thì:
>
>
>
> limiting variance = inf (vì pn + (1-pn)σn^2 → inf)
>
>
>
> nhưng
>
>
>
> asymptotic variance = 1
>
>
>
> Và điều này chỉ rõ một điều nói ở trên: là dùng limiting variance (tức giá trị của Var(Tn) tại limit) là không hữu ích và cũng không thực tế bằng việc dùng asymptotic variance (variance của limiting distribution). Mà việc khi ta cho pn → 1 và σn → ∞ với hai kết quả trái ngược nhau ở trên có ý nghĩa rất hay như sau:
>
>
>
> Cho pn → 1, tức là cho xác suất chọn được n(0,1) là rất rất lớn, đồng nghĩa rất rất hiếm xảy ra việc chọn được n(0, σn^2). Nhưng đồng thời cho σn → ∞ tức là cho nó rất rất lớn. Thì cái limiting variance ngu ngốc ở chỗ, nó vẫn cho rằng có xác suất dương nào đó (dù vô cùng nhỏ) xảy ra việc chọn cái normal có variance khổng lồ, nên nó cho rằng variance tổng (ý là limiting variance) là khổng lồ. Trong khi đó, thực tế thì, thật ra với xác suất cực lớn của việc chọn được n(0,1) thì variance = 1 sẽ hợp lí hơn, cũng là nói asymptotic variance sẽ thực tế hơn.

**🔗 See also:** [Định lý phương sai toàn phần](./44_hierarchical_model_mixture_distribution.md#node-ivmktz5)

<br>

<a id="node-bgijdqy"></a>

- **Definition 10.1.11 Asymptotic Efficiency**

<p align="center"><kbd><img src="assets/nerfte3qyul.png" width="80%"></kbd></p>

> [!NOTE]
> Nói ngắn gọn, ở đây người ta **định nghĩa** ra cái gọi là khi nào thì **chuỗi estimator Wn** được gọi là **ASYMPTOTICALLY EFFICIENT** của một parameter τ(θ), đó là nếu như **asymptotic variance của nó có thể đạt được giá trị variance nhỏ nhất được thể hiện bởi giá trị chặn dưới Cramer-Rao (lower bound)**.
>
>
>
> Để hiểu cái này, ta sẽ cần liên hệ lại (nhớ lại) kiến thức về Cramer-Rao Lower Bound là cái gì), đã học ở chap 7, trong phần đánh giá chất lượng của các point estimator. Nói ngắn gọn, khi cần phải đánh giá các estimator (evaluating estimator quality), thì một tiêu chí quan trọng là MSE, được định nghĩa là một hàm của estimator: MSE(W(**X**)) = E\_θ\[(W(**X**) - θ)^2\], và ta muốn cái này càng nhỏ càng tốt. Sau đó, bằng cách biến đổi chút, ta sẽ cho thấy nó = Var\_θ \[W(**X**)\] + \[Bias(W(**X**)\]^2 với Bias(W(**X**)) = E\_θ\[W(**X**)\] - θ. Để rồi, câu chuyện tiếp theo là, giả sử ta **xét một đám các estimator có cùng bias** (đồng nghĩa có cùng kì vọng E\_θ\[W(**X**)\]), thì thằng nào có Var\_θ\[W(**X**)\] nhỏ nhất sẽ là tốt nhất.
>
>
>
> Thế thì, việc tính variance có thể phức tạp, và quan trọng hơn, trong nhiều trường hợp, ta cũng không thể biết được rằng, một estimator có variance nào đó có phải là nhỏ nhất hay không. Từ đó, mới nói đến một công cụ cho vấn đề này: **Cramer Rao Lower Bound**. Đây chỉ đơn giản là một theorem, nói rằng, giả sử ta có bối cảnh thỏa mãn yêu cầu đề ra nào đó (xem cụ thể trong theorem) thì khi đó, ta có thể **xác định được cái lower bound của** Var\_θ(W(**X**)), từ đó, **nếu ta có một estimator có variance bằng với chặn dưới này, thì có thể kết luận nó chính là cái tốt nhất** (cái tốt nhất trong đám các estimator có chung bias, và nếu đang xét đám các unbiased estiamtor thì ta gọi nó là uniformly minimum variance unbiased estimator)
>
>
>
> ---
>
>
>
> Cramer Rao Inequality:
>
>
>
> Var\_θ(W(**X**)) ≥ \[d/dθ E\_θ\[W(**X**)\]\]^2 / E\_θ\[(∂/∂θ log f(**X**|θ))^2\]
>
>
>
> = \[d/dθ E\_θ\[W(**X**)\]\]^2 / In(θ)
>
>
>
> với In(θ) = E\_θ\[(∂/∂θ log f(**X**|θ))^2\], do iid = n E\_θ\[(∂/∂θ log f(Xi|θ))^2\] = n I1(θ)
>
> \
> Vậy Var\_θ(W(**X**)) ≥ \[d/dθ E\_θ(W(**X**))\]^2 / n I1(θ)
>
>
>
> Và CRLB của Var\_θ(W(**X**)) là \[d/dθ E\_θ(W(**X**))\]^2 / n I1(θ)
>
>
>
> ---
>
>
>
> Quay lại đây, định nghĩa Wn của chuỗi estimator cho τ(θ) có tính tiệm cận hiệu quả đó là khi √n(Wn - τ(θ)) → (d) n(0, \[τ'(θ)\]^2 / I1(θ))
>
>
>
> Mà theo định nghĩa Wn (là estimator của τ(θ)) có phương sai tiệm cận là σ^2: nếu kn(Wn - τ(θ)) → (d) n(0, σ^2). Nên ở đây việc ta có √n(Wn - τ(θ)) → (d) n(0, \[τ'(θ)\]^2 / I1(θ)) chính là nói AsympVar(Wn) = \[τ'(θ)\]^2 / I1(θ)
>
>
>
>  Nếu Wn là unbiased estimator cho τ(θ): E\[Wn\] = τ(θ) ⇨ τ'(θ) = d/dθ E\[Wn\], và từ đó việc √n(Wn - τ(θ)) → (d) n(0, \[τ'(θ)\]^2 / I1(θ)) chính là nói rằng:
>
>
>
> AsympVar(Wn) = \[d/dθ E(Wn)\]^2 / I1(θ), và cái này thì bằng n × \[d/dθ E(Wn)\]^2 / nI1(θ), tức n × CRLB.
>
>
>
> Vậy thì thế quái nào trong sách lại tương vào câu "that is, asym var(Wn) archivese CRLB, trong khi nó gấp n lần CRLB?
>
>
>
> Câu trả lời là ông Casella buộc ta hiểu đang nói đến không phải là CRLB của Var(Wn) có công thức \[d/dθ E\[Wn\]\]^2 / n I1(θ). Mà sự thật là đang nói về CRLB của √n Wn, có công thức là \[d/dθ E\[Wn\]\]^2 / I1(θ).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Bài giải thích rất sâu sắc và chi tiết, làm rõ định nghĩa về ước lượng hiệu quả tiệm cận (asymptotically efficient) bằng cách liên hệ chặt chẽ với Cramér-Rao Lower Bound, bao gồm cả bối cảnh và công thức. Độ chính xác và chiều sâu của kiến thức được trình bày rất ấn tượng.

**🔗 See also:** [Bất đẳng thức Cramer-Rao](./73_methods_of_evaluating_estimators.md#node-1qs416c) · [10.1.3 Calculations and Comparisons](#node-iwgmm5t) · [Phương sai tiệm cận và giới hạn](#node-62aug4x)

<br>

<a id="node-n1mqtrr"></a>

- **Theorem 10.1.12 (Asymptotic efficiency of MLEs)**

<p align="center"><kbd><img src="assets/yel24x532d9.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, tiếp theo là một theorem nói rằng, dưới một số điều kiện nhất định (xem thêm trong phần Miscellanea) của hàm f(x|θ) và gọi θ^ là ML estimator của θ, τ là hàm liên tục nào đó. Theorem này nói rằng:
>
>
>
> √n (τ(θ^) - τ(θ)) sẽ hội tụ phân phối về n(0, ν(θ)) với ν(θ) là Cramer Rao Lower Bound (1)
>
>
>
> Điều này có nghĩa là dưới những điều kiện nhất định nói trên, thì **τ(θ^)** **sẽ là một consistent và asymptotically efficient estimator** **của** **τ(θ)**.
>
>
>
> Nên hiểu, (1) hàm ý hai thứ:
>
>
>
> i) τ(θ^) → (p) τ(θ), và theo định nghĩa, đây cho thấy τ(θ^) là consistent sequence of estimator của τ(θ). Chứng minh nhanh:
>
>
>
> Ta có √n (τ(θ^) - τ(θ)) → (d) n(0, ν(θ)) thì phải hiểu là √n (τ(θ^) - τ(θ)) → (d) Z \~ n(0, ν(θ)) (√n (τ(θ^) - τ(θ)) sẽ trở thành một random variable có phân phối n(0, ν(θ)).
>
>
>
> Và 1/√n → 0 (đơn giản là vì lim n→inf 1/√n = 0
>
>
>
> Theo Slusky theorem: nếu Xn → (d) X, Yn → constant a thì XnYn → (d) aX, vậy áp dụng vào đây √n (τ(θ^) - τ(θ)) × 1/√n → (d) 0 × Z = 0.
>
>
>
> Mà theo một theorem 5.5.13, nói rằng, nếu Xn → (d) constant μ ⇔ Xn → (p) constant μ. Nên áp dụng theorem này, ta có √n (τ(θ^) - τ(θ)) × 1/√n = τ(θ^) - τ(θ) cũng → (p) contant 0. Và theo định nghĩa của consistent sequence of estimator, nếu P\_θ(|Wn - θ| < ε) = 1 ∀ε, cũng chính là nói Wn → (p) θ, thì Wn là consistent sequence of estimator. Vậy, theo đó, τ(θ^) là consistent sequence of estimator của τ(θ)
>
>
>
> (nói là chuỗi là bởi vì phải tự hiểu θ^ là MLE, có bản chất cũng là một statistic, một hàm của sample size n).
>
>
>
> ii) phân phối đích có variance là ν(θ), tức là cái này chính là asymptotically variance của τ(θ^), mà cái này là CRLB, thì theo định nghĩa của asymtoptically efficient, thì τ(θ^) chính là một asymtoptically efficient sequence of estimator của τ(θ)
>
>
>
> Và nhờ phân tích trên mình cũng sẽ thấy rằng, thật ra efficient chính là sẽ consistent. Là sao? Là vì theo định nghĩa của efficient: √n (τ(θ^) - τ(θ)) sẽ hội tụ phân phối về n(0, ν(θ)) với ν(θ) là Cramer Rao Lower Bound, thì dựa vào cái định nghĩa này, ta chứng minh như ở trên để cho thấy tính consistent. Vậy thì một sequence estimator thỏa định nghĩa này, sẽ là efficient và cũng tự nhiên là consistent, nên nói cách khác, efficient bao hàm consistent, thành ra nói vừa efficient vừa consistent là thừa (redundant), mà trong phần sau gs nói chính là này.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú giải thích Theorem 10.1.12 rất chi tiết và chính xác, đặc biệt là phần chứng minh tính consistency bằng định lý Slutsky. Để hoàn thiện hơn, bạn có thể bổ sung giới hạn n → ∞ vào định nghĩa tính consistent.

**🔗 See also:** [Tính nhất quán của MLE](#node-d19dn75) · [Định lý Slutsky](./55_convergence_concepts.md#node-uwbmbt7) · [Hội tụ xác suất và phân phối](./55_convergence_concepts.md#node-wqcasc6) · [Giới hạn dưới Cramer-Rao](./73_methods_of_evaluating_estimators.md#node-ihoar4m) · [CLT - Định lý giới hạn trung tâm](./55_convergence_concepts.md#node-32vkewg) · [Chuẩn tiệm cận, nhất quán, hiệu quả](#node-v1s5jks)

<br>

<a id="node-ucl78tu"></a>

- **Chứng minh Hiệu quả Ước lượng MLE**

<p align="center"><kbd><img src="assets/y2x6re1hg58.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/tb0uu0e48t9.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây sẽ chứng minh τ(θ^) = θ^ là efficient sequence of estimator cho θ:
>
>
>
> Đầu tiên, ta kí hiệu l(θ|**x**) là hàm log likelihood, thì đạo hàm của nó là l'(θ|**x**). ta mới linear approx tại θ0 (gọi true value của θ là θ0)
>
>
>
> l'(θ|**x**) ≈ l'(θ0|**x**) + l''(θ0|**x**)(θ - θ0)
>
>
>
> Tiếp, thay θ^ (MLE của θ) vô hai vế. Nhưng phải đặt câu hỏi: Vì sao có thể thay vào?
>
>
>
> Phải hỏi vậy là vì, sở dĩ cái phương trình xấp xỉ trên, chỉ valid khi θ ≈ θ0, thì liệu θ^ có ≈ θ0 không? Sẽ quay lại câu hỏi này sau, tạm thời chấp nhận, ta có:
>
>
>
> l'(θ^|**x**) ≈ l'(θ0|**x**) + l''(θ0|**x**)(θ^ - θ0) 
>
>
>
> Vế trái lúc này, có thể hiểu, chính là d/dθ \[log L(θ|**x**)\]|θ=θ^, mà vì định nghĩa của MLE, là solution của bài toán maximize\_θ L(θ|**x**), nên theo điều kiện cần bậc nhất, d/dθ \[L(θ|**x**)\]|θ=θ^ phải bằng 0, cũng là d/dθ \[log L(θ|**x**)\]|θ=θ^. Vậy vế trái = 0, ta có:
>
>
>
> 0 ≈ l'(θ0|**x**) + l''(θ0|**x**)(θ^ - θ0) 
>
>
>
> ⇔ l''(θ0|**x**)(θ^ - θ0)  ≈ -l'(θ0|**x**)
>
>
>
> ⇔ (θ^ - θ0)  ≈ -l'(θ0|**x**)/l''(θ0|**x**)
>
>
>
> ⇔ √n(θ^ - θ0)  ≈ √n\[-l'(θ0|**x**)/l''(θ0|**x**)\]
>
>
>
> ⇔ √n(θ^ - θ0)  ≈ √n\[-(1/√n)l'(θ0|**x**)\] / \[(1/√n)l''(θ0|**x**)\]
>
>
>
> ⇔ √n(θ^ - θ0)  ≈ \[-(1/√n)l'(θ0|**x**)\] / \[(1/n)l''(θ0|**x**)\] → 10.1.5
>
>
>
> Tới đây đặt I(θ0) = E\[l'(θ0|X)\]^2 = 1/ν(θ) và nói rằng nó là information number của một observation. Là sao ta?
>
>
>
> → l là hàm log likelihood, nên l'(θ0|X) = d/dθ \[log L(θ|X)\]|θ=θ0
>
>
>
> và cũng là d/dθ \[log f(X|θ0)\]. Và cái này, dĩ nhiên là random variable, có được từ việc áp hàm d/dθ \[log f(x|θ0)\] lên X, bình phương lên, cũng là random variable, thành ra có thể lấy kì vọng.
>
>
>
> Vậy vì sao E\[l'(θ0|X)\]^2 = E\[d/dθ \[log L(θ|X)\]|θ=θ0\]^2 = E\[d/dθ \[log L(θ0|X)\]\]^2 lại được ông gọi là information number của một observation?
>
>
>
> Nhớ lại bất đẳng thức Cramer Rao, giúp ta có lower bound của variance của estimator:
>
>
>
> Var\_θ\[W(**X**)\] ≥ {d/dθ E\_θ\[W(**X**)\]}^2 / E\_θ\[(∂/∂θ log f(**X**|θ)^2\] 
>
>
>
>  thì cái đại lượng E\_θ\[(∂/∂θ log f(**X**|θ))^2\] được gọi là **information number** hoặc **Fisher information**
>
>
>
> Vậy thì theo đó, mình sẽ tạm hiểu rằng, E\_θ\[(∂/∂θ log f(Xi|θ))^2\] là information number của một observation Xi (còn ở trên, là của mọi, hay n observation X1,...Xn).
>
>
>
>  ---
>
>  (Quay lại sau)

> [!TIP]
> **🤖 AI Feedback** — ❌ Score: **0/100**
>
> Vui lòng nhập lời giải thích của bạn để được chấm điểm.

**🔗 See also:** [Giới hạn dưới Cramer-Rao](./73_methods_of_evaluating_estimators.md#node-ihoar4m)

<br>

<a id="node-v1s5jks"></a>

- **Chuẩn tiệm cận, nhất quán, hiệu quả**

<p align="center"><kbd><img src="assets/hplvktj6ciw.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này như trong note trước đã hiểu rồi

**🔗 See also:** [Theorem 10.1.12 (Asymptotic efficiency of MLEs)](#node-n1mqtrr)

<br>

<a id="node-iwgmm5t"></a>

- **10.1.3 Calculations and Comparisons**

<p align="center"><kbd><img src="assets/9pfq0mb66la.png" width="80%"></kbd></p>

> [!NOTE]
> Cùng giải nghĩa đoạn này:
>
>
>
> Đại ý là, từ các mảnh ghép: i) CRLB của Wn, ii) định nghĩa của một estimator hiệu quả tiệm cận và iii)
>
> MLE là estimator hiệu quả tiệm cận thì ta có thể dùng chúng để giải quyết vấn đề sau đây: Estimate,
>
> ước lượng xấp xỉ giá trị của variance của một MLE, θ^, hoặc nói chung hơn, là h(θ^).
>
>
>
> Lập luận như sau:
>
>
>
> Đầu tiên, cùng ôn lại CRLB, nói đơn giản, theorem này cho biết, nếu ta có một statistic Wn là estimator
>
> của θ thỏa vài điều kiện nhất định thì Var(Wn) ≥ \[d/dθ E\[Wn\]\]^2 / In(θ) với In(θ) là information number
>
> của n observation. Công thức của nó có thể nhìn trong sách, nhưng viết In(θ) cho gọn, và không khó
>
> để thấy nhờ tính iid, In(θ) = n I1(θ).
>
>
>
> Gút lại, kết quả này chỉ là: nếu ta có Wn là estimator của θ thì CRLB của Var(Wn) là \[d/dθ E\[Wn\]\]^2 / n
>
> I1(θ), và nếu xét Wn có E\[Wn\] = h(θ) thì cái CRLB là **\[h'(θ)\]^2 / n I1(θ)**.
>
>
>
> Kết quả này chỉ là để đây tí nữa xài.
>
>
>
> Tiếp theo ta xét định nghĩa của một Wn estimator **hiệu quả tiệm cận** của g(θ), thì theo định nghĩa:
>
>
>
> √n(Wn - θ) → (d) n(0, ν(θ)) với ν(θ) = \[g'(θ)\]^2 / I1(θ).
>
>
>
> Và ta lại đã chứng minh mle θ^ của θ, cũng coi như của g(θ) với g là identity function, là một estimator
>
> hiệu quả tiệm cận (cũng là nhất quán (consistent) luôn), nên theo định nghĩa trên ta có:
>
>
>
> √n(θ^ - θ) → (d) n(0, 1/I1(θ)), và với định nghĩa của phương sai tiệm cậnv thì đây cũng chính là nói
>
> Avar(θ^) = 1/I1(θ))
>
>
>
> Rồi, tiếp, ta xét delta method theorem, nó nói rằng:
>
>
>
> nếu √n(Yn - θ) → (d) n(0, σ^2) thì √n(g(Yn) - g(θ)) → (d) n(0, \[g'(θ)\]^2 σ^2))
>
>
>
> Và cái trên cũng tương đương với việc nói Avar(Yn) = σ^2 thì Avar(g(Yn)) = \[g'(θ)\]^2 σ^2 = \[g'(θ)\]^2
>
> Avar(Yn)
>
>
>
> Và việc nói Avar(g(Yn)) = \[g'(θ)\]^2 Avar(Yn) thì cũng có nghĩa là
>
>
>
> khi n lớn thì Var(g(Yn)) ≈ \[g'(θ)\]^2 Avar(Yn) / n
>
>
>
> vì sao, vì √n(g(Yn) - g(θ)) → (d) n(0, \[g'(θ)\]^2 σ^2)) = n(0, \[g'(θ)\]^2 Avar(Yn))) có bản chất ý nghĩa là: khi
>
> n vô cùng thì random variable √n(g(Yn) - g(θ)) sẽ có distribution là n(0, \[g'(θ)\]^2 Avar(Yn))).
>
>
>
> Nên dĩ nhiên khi n lớn thì ta có xấp xỉ:
>
>
>
> Var\[√n(g(Yn) - g(θ))\] ≈ \[g'(θ)\]^2 Avar(Yn)
>
>
>
> (ủa ko phải sao, vì nói distribution khi n vô cùng của X là n(μ, ε^2), tức cũng là nói khi n lớn X có
>
> distribution là normal, mean là μ, variance là ε^2, vậy thì khi n lớn ta sẽ có Var(X) ≈ ε^2 chứ, hoàn toàn
>
> logic)
>
>
>
> ⇔ n Var(g(Yn)) - n Var(g(θ)) ≈ \[g'(θ)\]^2 Avar(Yn)
>
>
>
> ⇔ n Var(g(Yn)) - 0 ≈ \[g'(θ)\]^2 Avar(Yn)
>
>
>
> ⇔ Var(g(Yn)) ≈ \[g'(θ)\]^2 Avar(Yn) / n
>
>
>
> Như vậy, nếu ta áp dụng delta method cho Yn = θ^ và g = h thì sao:
>
>
>
> Var(h(θ^)) ≈ \[h'(θ)\]^2 Avar(θ^) / n.
>
>
>
> Và với việc ta đã chỉ ra với θ^ là mle của θ, nên là estimator hiệu quả tiệm cận, nên Avar(θ^) = 1/I1(θ)
>
>
>
> ⇨ Var(h(θ^)) ≈ \[h'(θ)\]^2 (1/I1(θ)) / n
>
>
>
> ⇔ Var(h(θ^)) ≈ **\[h'(θ)\]^2 /nI1(θ))**, đây chính là 10.1.7
>
>
>
> Và vế phải như trên đã nói, chính là CRLB của một estimator Wn nào đó có E\[Wn\] = h(θ)
>
>
>
> **Từ đó ta có thể tính CRLB của một estimator Wn nào đó có E\[Wn\] = h(θ), và dùng nó để estimate cho**
>
> **Var(h(θ^))**
>
>
>
> Tóm lại, nếu nói cực ngắn gọn thì chỉ là 3 bước lập luận:
>
>
>
> i) Delta method cho Avar(h(θ^)) = \[h'(θ)\]^2 Avar(θ^).
>
>
>
> Và cái này cũng là cho ta: khi n lớn, Var(h(θ^)) ≈ \[h'(θ)\]^2 Avar(θ^) / n
>
>
>
> ii) θ^ là mle của θ, nên hiệu quả tiệm cận, theo định nghĩa của hiệu quả tiệm cận cho ta: Avar(θ^) =
>
> 1/I1(θ))
>
>
>
> i) và ii) ⇨ khi n lớn, Var(h(θ^)) ≈ \[h'(θ)\]^2 \[1/I1(θ))\] / n = \[h'(θ)\]^2/ nI1(θ))
>
>
>
> ⇔ Var(h(θ^)) ≈ \[h'(θ)\]^2/ nI1(θ)) (1)
>
>
>
> Cuối cùng:
>
>
>
> iii) CRLB theorem nói rằng với Wn thỏa vì điều kiện Var(Wn) ≥ \[d/dθ E\_θ\[Wn\]\]^2 / nI1(θ).
>
>
>
> nên nếu chọn Wn có E\_θ\[Wn\] = h(θ) thì:
>
>
>
> CRLB của Var(Wn) = \[h'(θ)\]^2 / nI1(θ) (2)
>
>
>
> Từ (1) và (2), ta suy ra Var(h(θ^)) ≈ CRLB của Var(Wn) với Wn có E\_θ\[Wn\] = h(θ).
>
>
>
> Phần tiếp theo chỉ là dùng công thức để thế vào In(θ), nhưng ý tưởng chính thì mình đã thông.

**🔗 See also:** [Phương pháp Delta](./55_convergence_concepts.md#node-lo99k23) · [Tính nhất quán của MLE](#node-d19dn75) · [Definition 10.1.11 Asymptotic Efficiency](#node-bgijdqy) · [Bất đẳng thức Cramer-Rao](./73_methods_of_evaluating_estimators.md#node-1qs416c)

<br>

<a id="node-2mwxabg"></a>

- **Delta Method Variance Approximation**

<p align="center"><kbd><img src="assets/01kuzyikwazi.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, ôn lại nhanh cái lập luận bữa trước để cho phép ta dùng CRLB để estimate cho variance:
>
>
>
> rất đơn giản thôi, dựa trên các điểm sau đây:
>
>
>
> i) Với một Wn, là estimator của g(θ) thì CRLB của variance của nó: Var(Wn) ≥ \[d/dθ E\_θ\[Wn\]\]^2 / nI1(θ) (với I1(θ) là information number của 1 observation)
>
>
>
> nên nếu ta chọn Wn có E\[Wn\] = h(θ), thì CRLB của nó là \[h'(θ)\]^2 / nI1(θ)
>
>
>
> ii) Theo theorem của Delta method nói rằng nếu Avar(Yn) = σ^2 thì Avar(g(Yn)) = \[g'(θ)\]^2 σ^2 = \[g'(θ)\]^2 Avar(Yn). Và biểu thị toán học của của Avar(g(Yn)) = \[g'(θ)\]^2 Avar(Yn) đó là √n(g(Yn) - g(θ)) → (d) n(0, \[g'(θ)\]^2 Avar(Yn)), và cái này có nghĩa là nếu n lớn ta có Var\[√n(g(Yn) - g(θ))\] ≈ \[g'(θ)\]^2 Avar(Yn)) ⇔ Var\[g(Yn)\] ≈ \[g'(θ)\]^2 Avar(Yn)) / n.
>
>
>
> iii) Và giả sử ta có θ^ là mle của θ, thì nó sẽ có tính hiệu quả tiệm cận, theo định nghĩa, có nghĩa là:
>
>
>
> Avar(θ^) = 1/I1(θ). Nên nếu áp dụng điều ii) với Yn = θ^ và hàm h, thì ta sẽ có Var\[h(θ^)\] ≈ \[h'(θ)\]^2 / nI1(θ), và cái này theo (i) thì chính là CRLB của Wn có E\[Wn\] = h(θ)
>
>
>
> Vậy có nghĩa là, nếu ta muốn estimate variance của h(θ^), ta có thể dùng CRLB của một estimator Wn nào đó có E\[Wn\] = h(θ): Var\[h(θ^)\] ≈ CRLB của Var(Wn) = \[h'(θ)\]^2 / nI1(θ).
>
>
>
> Và tới đây, cách làm sẽ như sau:
>
>
>
> i) Dùng công thức xấp xỉ trên, sẽ cho phép ta dùng CLRB của Var(Wn) (với E\[Wn\] = h(θ)) = \[h'(θ)\]^2 / nI1(θ) để làm xấp xỉ cho Var(h(θ^).
>
>
>
> Nhưng bản thân cái xấp xỉ này ta cũng không biết vì nó dính θ, thành ra ta sẽ có bước 2:
>
>
>
> ii) Dùng estimator của θ, tức θ^ trong công thức xấp xỉ, như vậy:
>
>
>
> Estimator Var(h(θ^)) ≈ \[h'(θ^)\]^2 / nI1(θ^)
>
>
>
> Tóm lạ.
>
>
>
> Var(h(θ^)) ≈ \[h'(θ)\]^2 / In(θ), đây là công thức có được nhờ Delta method, và định nghĩa của efficient estimator.
>
>
>
> Với In(θ), thì dùng bổ đề 7.3.11 ta có công thức tính.
>
>
>
> Sau đó, ta dùng θ^ thay cho θ, và chuyển thành dấu xấp xỉ lần nữa.
>
>
>
> Var(h(θ^)) ≈ \[h'(θ^)\]^2 / In(θ^), hay Var(h(θ^)) ≈ \[h'(θ)\]^2 / In(θ) | θ = θ^
>
>
>
> nên kí hiệu là Var\_ θ^\[h(θ^)\] ý là hàm Var(h(θ^)) ≈ \[h'(θ)\]^2 / In(θ) evaluate tại θ^
>
>
>
> hoặc Var^(h(θ^)).
>
>
>
> Đây cũng là ý gs nói khúc cuối.
>
>
>
> ---
>
>
>
> Quay lại nói về cái vụ dùng Lemma 7.3.11:
>
>
>
> Như đã biết, trong phần CRLB, thhì E\_θ{\[∂/∂θ log f(**X**|θ)\]^2}, được kí hiệu là In(θ), information number của n observation (xem link).
>
>
>
> thì theo Lemma 7.3.11 nói rằng nếu f(x|θ) thỏa d/dθ E\_θ\[∂/∂θ log f(**X**|θ)\]
>
>
>
> = ∫ ∂/∂θ\[(∂/∂θ log f(x|θ)d(x|θ)\] dx thì E\_θ{\[∂/∂θ log f(**X**|θ)\]^2} = - E\_θ\[∂^2/∂θ^2 log f(**X**|θ)\]
>
>
>
>  Nên In(θ) ở đây = E\_θ{\[∂/∂θ log f(**X**|θ)\]^2}
>
>
>
> = - E\_θ\[∂^2/∂θ^2 log f(**X**|θ)\]
>
>
>
> = - E\_θ\[∂^2/∂θ^2 log L(θ|**X**)\] (do L(θ|**X**) = f(**X**|θ))
>
>
>
> Tới đây, một lần nữa người ta **bỏ kì vọng** chuyển sang dùng -∂^2/∂θ^2 log L(θ^|**X**) và gọi nó là **observed information number**, là cái mà ông nói thật ra ngon hơn (superior) so với expected information number (In(θ))
>
>
>
> = - E\_θ\[∂^2/∂θ^2 log L(θ|**X**)\] (do L(θ|**X**) = f(**X**|θ))
>
>
>
> ≈ -∂^2/∂θ^2 log L(θ^|**X**)
>
>
>
> Nói tóm lại lần nữa.
>
>
>
> Nhờ Delta method, định nghĩa của hiệu quả tiệm cận nên ta có công thức xấp xỉ:
>
>
>
> Var(h(θ^)) ≈ CRLB của Wn, với E\[Wn\] = h(θ), = h'(θ) / In(θ), In(θ) là expected information number.
>
>
>
> Tiếp, ta sẽ estimate cái xấp xỉ này, bằng cách evaluate công thức trên tại θ^ (vì ko biết θ). Đồng thời thay cái expected information number bằng observed information number luôn.
>
>
>
> Var(h(θ^)) ≈ \[h'(θ) / -∂^2/∂θ^2 log L(θ|**X**)\] | θ=θ^. Và đây là cách ta estimate variance của một hàm của một mle.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bài giải thích rất chi tiết và sâu sắc các lập luận để ước lượng phương sai của h(θ̂) bằng CRLB, liên kết chặt chẽ các khái niệm về định lý Delta Method, hiệu quả tiệm cận của MLE và CRLB, hoàn toàn khớp với nội dung trong ảnh. Em đã nắm vững cách áp dụng các công thức và ý nghĩa của chúng.

**🔗 See also:** [Giới hạn dưới Cramer-Rao](./73_methods_of_evaluating_estimators.md#node-ihoar4m) · [Bổ đề Tính toán Hàm mũ](./73_methods_of_evaluating_estimators.md#node-sttybm4)

<br>

<a id="node-cpdjv2x"></a>

- **Theorem 10.1.6 on Consistent Estimators**

<p align="center"><kbd><img src="assets/p70gp9yp7qr.png" width="80%"></kbd></p>

> [!NOTE]
> Còn một ý, nói -(1/n) ∂^2/∂θ^2 log L(θ|**X**)|θ=θ^ là consistent estimator của I(θ), Là sao ta?
>
>
>
> Vì ∂^2/∂θ^2 log L(θ|**X**) = ∂^2/∂θ^2 log f(**X**|θ)
>
>
>
> = ∂^2/∂θ^2 log Πi f(Xi|θ)
>
>
>
> = ∂^2/∂θ^2 Σi \[log f(Xi|θ)\]
>
>
>
> = Σi \[∂^2/∂θ^2 log f(Xi|θ)\]
>
>
>
> Dĩ nhiên ∂^2/∂θ^2 log f(Xi|θ) là một random variable. Và với iid random sample X1,...Xn thì ta cũng có một random sample Y1, ...Yn với Yi = ∂^2/∂θ^2 log f(Xi|θ)
>
>
>
> Do đó Ybar = (Σi Yi)/n = (1/n) Σi \[∂^2/∂θ^2 log f(Xi|θ)\]
>
>
>
> và theo LLN, Ybar → (p) E\_θ\[Yi\] = E\_θ\[∂^2/∂θ^2 log f(Xi|θ)\]
>
>
>
> và cái này thì chính là -Ii(θ), tức information number của observation i'th.
>
>
>
> Do đó, -Ybar = (1/n) Σi \[∂^2/∂θ^2 log f(Xi|θ)\] → (p) Ii(θ)
>
>
>
> Kết quả này thì có nghĩa là gì?
>
>
>
> Có nghĩa là cái xấp xỉ lúc nãy:
>
>
>
>  Var(h(θ^)) ≈ \[h'(θ^)^2 / -∂^2/∂θ^2 log L(θθ^|**X**)\] có đặc địểm:
>
>
>
> mẫu số -∂^2/∂θ^2 log L(θθ^|**X**)  = -n Ybar là consistent estimator của n Ii(θ), tức là In(θ)
>
>
>
> Vậy Var(h(θ^)) = nominator / denominator. Mà denominator là consistent estimator của In(θ).
>
>
>
> Còn nominator \[h'(θ^)\]^2 cũng sẽ hội tụ về \[h'(θ)\]^2 vì n → inf, θ^ → θ (do mle là consistant estimator của θ)
>
>
>
> Vậy suy ra Var(h(θ^)) cũng → (p) \[h'(θ)\]^2 / In(θ), tức là công thức xấp xỉ ban đầu mà ta lập luận từ Delta method và định nghĩa hiệu quả tiệm cận.
>
>
>
> Tóm lại, ý nói, cái việc ta dùng θ^ thay cho θ, và dùng observed information number thay cho expected information number In(θ). thì ta vẫn đang có một consistent estimator: Var^(h(θ^)), hay Var\_θ^(h(θ^)) là consistent estimator của Var\_θ(h(θ^))

**🔗 See also:** [Tính nhất quán của MLE](#node-d19dn75)

<br>

<a id="node-ytulpwg"></a>

- **Approximate binomial variance**

<p align="center"><kbd><img src="assets/vbhae5v8tcq.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì, hôm qua đã học về đại khái là cách để estimate variance của một mle θ^ - maximum likelihood estimator của θ, chính xác hơn là variance của h(θ^).
>
>
>
> Recall nhanh lần nữa cho nhớ:
>
>
>
> Đại khái là theo định nghĩa của (cái gọi là một estimator hiệu quả tiệm cận) đó là: nếu Yn là estimator hiệu quả tiệm cận của θ, thì Avar(Yn) = 1/I1(θ) với I1(θ) là infomation number of 1 observation. Và biểu thị toán học là √n(Yn - θ) → (d) (1, 1/I1(θ))
>
>
>
> Rồi, theo Delta method, nếu Avar(Yn) = σ^2 thì Avar(g(Yn)) = \[g'(θ)\]^2 σ^2 = \[g'(θ)\]^2 Avar(Yn). Như vậy, giả sử ta có Yn là estimator hiệu quả tiệm cận ở trên thì Avar(g(Yn)) = \[g'(θ)\] (1/I1(θ)). Và cái này thì có nghĩa là √n(g(Yn) - g(θ)) → (d) n(0, \[g'(θ)\] (1/I1(θ))), nên nếu n lớn, ta có Var\[√n(g(Yn) - g(θ)\] ≈ \[g'(θ)\] (1/I1(θ)) ⇔ Var(g(Yn)) ≈ \[g'(θ)\] / nI1(θ)
>
>
>
> Và vế phải, \[g'(θ)\] / nI1(θ), theo CRLB theorem, nói rằng, nếu ta có Wn là estimator của g(θ), thì Var(Wn) ≥ \[d/dθ E\_θ(Wn)\]^2 / In(θ). Nên nếu Wn có Eθ\[Wn\] = g(θ), thì Var(Wn) ≥ \[g'(θ)\]^2 / In(θ) = \[g'(θ)\]^2 / nI1(θ)
>
>
>
> Như vậy có thể thấy, với việc Var(g(Yn)) ≈ \[g'(θ)\] / nI1(θ) và Var(Wn) ≥ \[g'(θ)\]^2 / In(θ) = \[g'(θ)\]^2 / nI1(θ) thì như vậy ta có thể dùng CRLB của Wn có kì vọng = g(θ) để xấp xỉ cho Var(g(Yn))
>
>
>
> Áp dụng với θ^ là mle của θ, theo bữa trước đã chứng minh, thì mle là một estimator hiệu quả tiệm cận cũng như consistent. Nên theo trên, ta có: Var\[h(θ^)\] có thể tính xấp xỉ bởi CRLB của Var(Wn) có E\[Wn\] = h(θ) = \[h'(θ)\]^2 / nI1(θ),
>
>
>
> Và ta gọi cái này là Var\_θ(h(θ^))
>
>
>
> Tuy nhiên, công thức xấp xỉ này cũng vô dụng vì ta không biết θ. Nên tới đây, ta mới đi thêm một bước nữa: Dùng chính θ^ để estimate cho θ trong công thức \[h'(θ)\]^2 / nI1(θ)
>
>
>
> Và sau đó, khi xét In(θ) có công thức là E\_θ{\[∂/∂θ log f(**X**|θ)\]^2}, thì dùng một Lemma, ta thấy nó bằng - E\_θ\[∂^2/∂θ^2 log f(**X**|θ)\] = - E\_θ\[∂^2/∂θ^2 log L(θ|**X**)\].
>
>
>
> Thế thì, E\_θ{\[∂/∂θ log f(**X**|θ)\]^2} là expected information number, còn -∂^2/∂θ^2 log L(θ|**X**) là observed information number và ta sẽ dùng observed information number.
>
>
>
> Như vậy Var\_θ(h(θ^)) với việc dùng observed information number cũng như là dùng θ^ thay cho θ, ta sẽ có:
>
>
>
> Var\_θ(h(θ^)) ≈ Var\_θ^(h(θ^)), hay Var^\_θ(h(θ^)) = \[h'(θ)\]^2|θ=θ^ / \[-∂^2/∂θ^2 log L(θ|**X**)\]|θ=θ^, chính là cách mà ta sẽ estimate công thức xấp xỉ cho Var(h(θ^))
>
>
>
> ---
>
>
>
> Trên cơ sở vừa ôn lại lí thuyết này xong, ta sẽ áp dụng vào ví dụ 10.1.14:
>
>
>
>  Ở đây ta có p^ = (Σi Xi)/n là MLE của p với bối cảnh bài toán là ta có random sample X1, X2,...Xn iid \~ Bern(p).
>
>
>
> Và tính Var(p^) một cách trực tiếp thì ta tính ra được = p(1-p)/n 
>
>
>
> (Cái này chỉ đơn giản là với sample mean, ta đã chứng minh Var(Xbar) = Var(X) / n, nên ở đây Var(Xbar), tức Var(p^) = Var(Xi) / n. Variance của Bern(p) có thể chứng minh nhanh: = EX^2 - (EX)^2 = 1^2 × p + 0^2 × (1-p) - p^2 = p(1-p). Nên Var(p^) = p(1-p)/n)
>
>
>
> và dùng p^ thay cho p trong công thức Var_p(p^), ta sẽ có Var^(p^) (hay Var_p^(p^) công thức xấp xỉ của Var_p(p^)):
>
>
>
>  Var^(p^) = p^(1-p^)/n

<br>

<a id="node-ct81g3i"></a>

- **Asymptotic Efficiency of Estimator p̂**

<p align="center"><kbd><img src="assets/i4lgaqfthyn.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, bây giờ ta áp dụng công thức Var^(h(θ^)) ≈ \[h'(θ)\]^2|θ=θ^ / \[-∂^2/∂θ^2 log L(θ|**x**)\]|θ=θ^
>
>
>
> Với h(θ) = θ thì:
>
>
>
> Tử số: \[h'(θ)\]^2|θ=θ^ = 1
>
>
>
> Mẫu số: \[-∂^2/∂θ^2 log L(θ|**x**)\]|θ=θ^
>
>
>
> Để tính mẫu số ta xét cái này trước:
>
>
>
> log L(θ|**x**) = log f(**x**|θ) = log Πi f(xi|θ) = Σi \[log(p^xi (1-p)^(1-xi))\]
>
>
>
> = Σi {log(p^xi) + log\[(1-p)^(1-xi)\]}
>
>
>
> = Σi {xi log(p) + (1-xi) log(1-p)}
>
>
>
> = Σi {xi log(p) + (1-xi) log(1-p)}
>
>
>
> = Σi {xi log(p)} + Σi{(1-xi) log(1-p)}
>
>
>
> = log(p) Σi xi + log(1-p) Σi (1-xi)
>
>
>
> = log(p) np^ + log(1-p) (n-Σixi)
>
>
>
> = log(p) np^ + log(1-p) (n-np^)
>
>
>
> = log(p) np^ + log(1-p) n(1-p^)
>
>
>
> ⇨ ∂/∂p \[log(p) np^ + log(1-p) n(1-p^)\]
>
>
>
> = ∂/∂p \[log(p) np^\] + ∂/∂p\[log(1-p) n(1-p^)\]
>
>
>
> = np^ ∂/∂p \[log(p)\] + n(1-p^) ∂/∂p\[log(1-p)\]
>
>
>
> = np^ (1/p) + n(1-p^) \[-/(1-p)\]
>
>
>
> Và ∂^2/∂p^2 \[log(p) np^ + log(1-p) n(1-p^)\]
>
>
>
> = ∂/∂p \[np^ (1/p) + n(1-p^) \[-1/(1-p)\]\]
>
>
>
> = ∂/∂p \[np^ (1/p)\] + ∂/∂p \[n(1-p^) \[-1/(1-p)\]\]
>
>
>
> = np^ × (-1/p^2) + ∂/∂p \[n(1-p^) \[1/(1-p)^2\]\]
>
>
>
> = -np^/p^2 + n(1-p^)/(1-p)^2
>
>
>
> Vậy -∂^2/∂θ^2 log L(θ|**x**) = -\[-np^/p^2 + n(1-p^)/(1-p)^2\]
>
>
>
> = np^/p^2 + n(1-p^)/(1-p)^2
>
>
>
> (chú ý, np^/p^2 là n p_hat chia p bình phương, coi chừng nhìn nhầm và rút gọn thành n/p^ là sai)
>
>
>
> Evaluate tại p = p^:
>
>
>
> \[-∂^2/∂p^2 log L(p|**x**)\]|p=p^
>
>
>
> = np^/(p^)^2 + n(1-p^)/(1-p^)^2
>
>
>
> = n/p^ + n/(1-p^)
>
>
>
> = \[n(1-p^)/p^(1-p^) + np^/p^(1-p^)
>
>
>
> = n/p^(1-p^)
>
>
>
> Và như vậy Var^(h(p^)) ≈ \[h'(p)\]^2|p=p^ / \[-∂^2/∂p^2 log L(p|**x**)\]|p=p^
>
>
>
> ⇔ Var^(p^) ≈ 1 / \[n/p^(1-p^)\]
>
>
>
> ⇔ Var^(p^) ≈ p^(1-p^)/n
>
>
>
> Và công thức này thì giống công thức Var^(p^) = p^(1-p^)/n mà ta đã tính hồi nãy (thế p^ thay cho p, trong công thức Var(p) = p(1-p)/n
>
>
>
> Ý quan trọng muốn nhấn mạnh đó là: Trong bài toán này, ta biết mle thật sự sẽ có công thức là Var(p^) (hay Var_p(p^), để thể hiện nó là hàm theo p) = p(1-p)/n. Để rồi từ đó, bằng cách dùng p^ thay p, ta có ước lượng của variance Var^(p^) = p^(1-p^)/n.
>
>
>
> Sau đó, bằng cách tiếp cận dựa trên lí thuyết nói rằng Var^(h(θ^)) ≈ \[h'(θ)\]^2|θ=θ^ / \[-∂^2/∂θ^2 log L(θ|**x**)\]|θ=θ^, ta cũng tính ra được cùng kết quả Var^(p^) ≈ p^(1-p^)/n.
>
>
>
> Như vậy có nghĩa là: **Giả sử ta không có công thức** **Var(θ^) theo θ, kí hiệu Var\_θ(θ^), để từ đó thế θ^ vào để có Var^(θ^), là xấp xỉ của Var\_θ(θ^). Thì ta có thể dùng cách tiếp cận thứ hai nói trên**: Chỉ việc tính:
>
>
>
> i) \[h'(θ)\]^2|θ=θ^, mà ở đây khi đang tính Var(θ^) thì tức là h(.) = identity function, \[h'(θ)\]^2|θ=θ^ = 1.
>
>
>
> ii) Tính -∂^2/∂θ^2 log L(θ|**x**)\]|θ=θ^, tức là derive công thức đạo hàm bậc hai của log likelihood L(θ|**x**), sẽ ra một hàm theo θ, lấy dấu âm, và thế θ^ vào.
>
>
>
> iii) Khi đó 1/\[kết quả mẫu số\], chính là cũng sẽ cho ra Var^(θ^), mà trong ví dụ cụ thể này, đó là Var^(p^) ≈ p^(1-p^)/n

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **90/100**
>
> Bài làm rất chi tiết và có chiều sâu, giải thích rõ ràng từng bước và mục đích của việc áp dụng công thức xấp xỉ phương sai, đồng thời so sánh kết quả với công thức đã biết. Tuy nhiên, trong quá trình tính đạo hàm bậc hai của hàm log likelihood, bạn đã mắc lỗi về dấu ở thành phần thứ hai (∂/∂p [n(1-p^) [-1/(1-p)]] phải là -n(1-p^)/(1-p)^2 chứ không phải dương), dù kết quả cuối cùng vẫn chính xác.

**🔗 See also:** [Tính nhất quán của MLE](#node-d19dn75) · [Giới hạn dưới Cramer-Rao](./73_methods_of_evaluating_estimators.md#node-ihoar4m)

<br>

<a id="node-suvnj6h"></a>

- **Asymptotic Efficiency of Estimator p̂ (bản sao)**

<p align="center"><kbd><img src="assets/rp734ayvn4.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, đoạn này nói rằng vì p^, hay θ^ là mle, được theo theorem nào đó, là một estimator có tính hiệu quả tiệm cận và consistent.
>
>
>
> √n(p^ - p) → (d) n(0, 1/I1(p))
>
>
>
> với I1(p) = E_p\[(∂/∂p log f(X|p))^2\]
>
>
>
> log f(X|p) = log\[p^X (1-p)^(1-X)\]
>
>
>
> = X log(p) + (1-X)l og(1-p)
>
>
>
> ⇨ d/dp \[X log(p) + (1-X) log(1-p)\]
>
>
>
> = X/p + (1-X) \[-1/(1-p)\]
>
>
>
> = X/p - (1-X)/(1-p)
>
>
>
> = X(1-p)/p(1-p) - p(1-X)/p(1-p)
>
>
>
> = \[X(1-p) - p(1-X)\]/p(1-p)
>
>
>
> = \[X - Xp - p + pX)\]/p(1-p)
>
>
>
> = (X-p)/p(1-p)
>
>
>
> E_p\[(∂/∂p log f(X|p))^2\] = E_p\[((X-p)/p(1-p))^2\]
>
>
>
> = E_p\[((X-p))^2\] / \[p(1-p)\]^2
>
>
>
> = Var_p(X) / \[p(1-p)\]^2
>
>
>
> = p(1-p) / \[p(1-p)\]^2
>
>
>
> = 1 / p(1-p)
>
>
>
>  Như vậy **√n(p^-p) → (d) n(0, 1/I1(p)) = n(0, p(1-p))**
>
>
>
> Lại cộng với Slusky theorem: Xn → (d) X, Yn → (p) a ⇨ XnYn → (d) aX
>
>
>
> Ta có ở trên √n(p^-p) → (d) n(0, p(1-p)),
>
>
>
> và 1/√\[p^(1-p^)\] → (p) 1/√\[p(1-p)\] do p^ → (p) p
>
>
>
> nên √n(p^-p) × \[1/√\[p^(1-p^)\]\] → (d) n(0, p(1-p)) × 1/√\[p(1-p)\])
>
>
>
> Mà với Z \~ n(0, σ^2), tức là một thành viên của location scale family ứng với scale = σ, thì theo location scale family, Z/σ sẽ \~ n(0,1). Vậy n(0, p(1-p)) /√\[p(1-p)\] sẽ \~ n(0,1)
>
>
>
> Vậy √n(p^-p)/√\[p(1-p)\] → (d) n(0, 1).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Phân tích của bạn rất sâu sắc và chính xác, đặc biệt là phần dẫn xuất Fisher Information để chứng minh phương sai. Bạn đã giải thích rất rõ ràng cách áp dụng Định lý Slutsky và chuẩn hóa phân phối để đạt được kết quả cuối cùng.

<br>

<a id="node-13p5sy2"></a>

- **Section 10.1 Point Estimation**

<p align="center"><kbd><img src="assets/f2f54o58ynm.png" width="80%"></kbd></p>

> [!NOTE]
> Mình thấy cần thiết phải ôn lại cái lập luận dẫn đến cách tiếp cận để giải quyết được bài toán estiamte variance của một mle vì thật sự đây là kiến thức rất khó và quan trọng.
>
>
>
> Đầu tiên cần nhấn mạnh, yêu cầu đặt ra là estiamte được variance của một mle θ^, của θ. Ta sẽ dựa trên các công cụ sau đây:
>
>
>
> Đầu tiên là khái niệm phương sai tiệm cận (asymptotically variance), kí hiệu Avar, được định nghĩa là phương sai của phân phối chuẩn mà √n(Wn - θ) hội tụ (distribution) về. Tức là, nếu ta có √n(Wn - θ) → (d) n(0, σ^2), thì Avar(Wn) = σ^2.
>
>
>
> Rồi, tiếp theo, là Delta method theorem, nói rằng nếu √n(Wn - θ) → (d) n(0, σ^2), thì √n(g(Wn) - g(θ)) → (d) n(0, g'(θ)^2 σ^2). Điều này cũng đồng nghĩa nói đơn giản hơn là nếu Wn có phương sai tiệm cận là Avar(Wn) thì Avar\[g(Wn)\] = \[g'(θ)\]^2 Avar(Wn).
>
>
>
> Kế đến, là công cụ nữa: Khái niệm thế nào là một estimator có tính hiệu qủa tiệm cận: Định nghĩa nói rằng, nếu estimator Wn của θ có Avar(Wn) = 1/I1(θ), thì nó là estiamator hiệu quả tiệm cận, đồng thời cũng imply consistent.
>
>
>
> Và công cụ tiếp theo là theorem nói rằng ML estimator của θ hay h(θ) thì sẽ là estimator hiệu quả tiệm cận.
>
>
>
> Với tất cả các công cụ trên ta sẽ lập luận như sau:
>
>
>
> Xét θ^, là MLE của θ và ta như ban đầu đã nói, ta muốn estimate variance của h(θ^).
>
>
>
> Thế thì, vì θ^ là MLE của θ, nên nó là estimator hiệu quả tiệm cận: Do đó Avar(θ^) = 1/I1(θ), I1(θ) là information number của 1 observation. Và theo định nghĩa của phương sai tiệm cận thì ta có √n(θ^ - θ) → (d) n(0, 1/I1(θ)).
>
>
>
> Rồi, theo Delta method theorem, khi θ^ có phương sai tiệm cận là Avar(θ^) thì Avar\[h(θ^)\] = \[h'(θ)\]^2 Avar(θ^), thay kết quả trên vào ta có:
>
>
>
> Avar\[h(θ^)\] = \[h'(θ)\]^2 \[1/I1(θ)\]
>
>
>
> Và theo định nghĩa của phương sai tiệm cận thì ta có:
>
>
>
> √n\[h(θ^) - h(θ)\] → (d) n(0, \[h'(θ)\]^2 \[1/I1(θ)\])
>
>
>
> Và điều này, ý nghĩa của nó là, khi n lớn đến vô hạn thì random variable √n\[h(θ^) - h(θ)\] sẽ có distribution là n(0, \[h'(θ)\]^2 \[1/I1(θ)\]).
>
>
>
> Vậy nếu xét n đủ lớn, thì ta có thể nói Var\[ √n\[h(θ^) - h(θ)\]\] ≈ \[h'(θ)\]^2 \[1/I1(θ)\]
>
>
>
> ⇔ n \[Var\[h(θ^)\] + 0\] ≈ \[h'(θ)\]^2 \[1/I1(θ)\] (khai triến vế trái theo tính chất của phương sai Var(c1X + c2) = c1^2Var(X).
>
>
>
> ⇔ Var\[h(θ^)\] ≈ \[h'(θ)\]^2 \[1/I1(θ)\] / n
>
>
>
> ⇔ Var\[h(θ^)\] ≈ \[h'(θ)\]^2 / nI1(θ)
>
>
>
> Tới đây là ta đã có công thức để tính xấp xỉ variance của h(θ^) rồi.
>
>
>
> Và với việc biết về theorem Cramer Rao Lower Bound, nói rằng, nếu ta có Wn là chuỗi estimator của θ, thì phương sai của nó không thể nhỏ hơn CRLB: Var\_θ(Wn) ≥ \[d/dθ E\_θ\[Wn\]^2/ In(θ). Và nếu ta có Wn là estiamtor có E\[Wn\] = h(θ) thì Var\_θ(Wn) ≥ \[h'(θ)\]^2/ In(θ) = \[h'(θ)\]^2/ nI1(θ) chính là cái trên. Do đó ta mới nói:
>
>
>
> Var\[h(θ^)\] ≈ \[h'(θ)\]^2 / nI1(θ) là CRLB của một estimator Wn có E\[Wn\] = h(θ)
>
>
>
> Rồi, thế thì tuy là ta có công thức để mà estimate Var(h(θ^)) ≈ \[h'(θ)\]^2 / nI1(θ) nhưng công thức này vô dụng vì dù sao ta cũng không thể biết θ là gì. Do đó, ta sẽ làm hai động tác để lại mang ý nghĩa là ta sẽ ước lượng (estimate) cái công thức xấp xỉ (approximate) trên:
>
>
>
> i) Động tác đầu tiên là chỗ nào có θ thì ta dùng θ^.
>
>
>
> ii) Động tác thứ hai, là nói về cái In(θ), vốn có công thức cần phải tính kì vọng: E\_θ{\[∂/∂θ log f(**X**|θ)\]^2}, nên nó gọi là expected information number.
>
>
>
> Phân tích cái này: Đầu tiên hãy hiểu rằng f(**X**|θ) là random variable có được bởi việc áp joint pdf của **X**: f(**x**|θ) lên random variable vector **X**, và sau đó là áp hàm log, rồi lấy đạo hàm theo θ, rồi bình phương, nên cuối cùng ta vẫn là có một random variable. Hay nói cách khác, ta có thể coi như đây là random variable có được bằng cách áp hàm g(**x**) = {d/dθ \[log f(**x**|θ)\]}^2, lên **X**. Và vì là random variable, nên ta có quyền lấy kì vọng. Và thêm nữa vì đây là random variabel có được từ việc áp dụng hàm g lên **X**, mà ông **X** có distribution phụ thuộc θ: **X** \~ f(**x**|θ) nên dĩ nhiên g(**X**) cũng vậy, và do đó expected value của nó phải là hàm phụ thuộc θ, nên nó mới có cái chữ θ ở dưới chân: E\_θ{\[∂/∂θ log f(**X**|θ)\]^2}. Nói chung hiểu bản chất của hắn ta sẽ dễ hiểu mấy khúc sau.
>
>
>
> Rồi, Theo Lemma 7.3.11 nói rằng nếu f(x|θ) thỏa d/dθ E\_θ\[∂/∂θ log f(**X**|θ)\] = ∫ ∂/∂θ\[(∂/∂θ log f(x|θ)d(x|θ)\] dx thì:
>
>
>
> E\_θ{\[∂/∂θ log f(**X**|θ)\]^2} = - E\_θ\[∂^2/∂θ^2 log f(**X**|θ)\]
>
>
>
> Và để tính kì vọng cuả cái này, thì vì ko biết θ, nên cũng không thể tính được. Do đó, ta sẽ không dùng kì vọng, mà thay bằng cái gọi là **observed information number**.
>
>
>
> Tức là thay - E\_θ\[∂^2/∂θ^2 log f(**X**|θ)\]
>
>
>
> bằng: - ∂^2/∂θ^2 log f(**x**|θ) 
>
>
>
> (chú ý, ở trên, là **X**, vì đây là random variable, và ta tính kì vọng của cái ∂^2/∂θ^2 log f(**X**|θ), cũng là random variable. Còn ở dưới, là ta thế observed value vào, bỏ kì vọng)
>
>
>
> Và với hai động tác đó, ta có công thức estimate cái công thức approximate:
>
>
>
> Var\[h(θ^)\] ≈ \[h'(θ)\]^2 / nI1(θ)
>
>
>
> ≈ \[h'(θ)\]^2|θ=θ^ / \[-∂^2/∂θ^2 log f(**x**|θ)\]|θ=θ^
>
>
>
> Và dĩ nhiên f(**x**|θ) = L(θ|**x**)
>
>
>
> ≈ \[h'(θ)\]^2|θ=θ^ / \[-∂^2/∂θ^2 logL(θ|**x**)\]|θ=θ^
>
>
>
> ---
>
>
>
> Rồi. thế thì ở đây nhắc đến trong bài tập 5.5.22 mình đã dùng Delta Method để approximate var(p^/(1-p^)). Thì như vừa ôn lại Delta method ở trên, theorem này nói rằng nếu Wn có Avar(Wn) thì g(Wn) có Avar(g(Wn)) = \[g'(θ)\]^2 Avar(Wn). Nên áp dụng cái này, ta sẽ coi như g(p^) = p^/(1-p^) để rồi:
>
>
>
> Avar\[p^/(1-p^)\] = \[g'(p)\]^2 Avar(p^)
>
>
>
> và với cái này thì ta có thể có Var\[p^/(1-p^)\] ≈ \[g'(p)\]^2 Avar(p^)/n
>
>
>
> Thế thì mình biết với random sample X1, X2,... Xn có mean μ và variance σ^2 thì CLT (central limit theorem) cho ta biết rằng √n(Xbar - μ)/σ → (d) n(0, 1), cũng chính là √n(Xbar - μ) → n(0, σ^2).
>
>
>
> Vậy áp dụng CLT ta sẽ có √n(p^ - p) → n(0, true variance) với true variance trong bài toán này là p(1-p). Vậy nên Avar(p^) = p(1-p).
>
>
>
> Còn \[g'(p)\]^2: g(p) = p/(1-p)
>
>
>
> ⇨ g'(p) = { \[d/dp p\](1-p) - p \[d/dp (1-p)\] } / (1-p)^2
>
>
>
> = \[(1-p) + p\] / (1-p)^2
>
>
>
> = 1 / (1-p)^2
>
>
>
> Vậy thay vô ta có: Var\[p^/(1-p^)\] ≈ \[g'(p)\]^2 Avar(p^)/n
>
>
>
> = \[1 / (1-p)^2\]^2 × p(1-p) / n
>
>
>
> = \[1 / (1-p)^4\] × p(1-p) / n
>
>
>
> = p / n(1-p)^3\]
>
>
>
> Vậy Var\[p^/(1-p^)\] ≈ p / n(1-p)^3\] và đây chính là ta đã giải lại bài tập 5.5.22 tính Var\[p^/(1-p^)\] theo Delta method. Và dĩ nhiên ta lại không có p, nên dùng cách thay p^ vào p, để có estimate của cái xấp xỉ này:
>
>
>
> Var^\[p^/(1-p^)\] ≈ Var_p\[p^/(1-p^)\]|p=p^ = p/n(1-p)^3|p=p^
>
>
>
> = **p^/n(1-p^)^3**
>
>
>
> ---
>
>
>
> Giờ, ta sẽ dùng cái kiến thức hồi nãy vừa ôn lại để tính cái này theo cách đó.
>
>
>
> Đó là Var(g(p^)) ≈ \[g'(p)\]^2|p=p^ / \[-∂^2/∂θ^2 log L(p|**x**)\]|p=p^
>
>
>
> Tử số: \[g'(p)\]^2 như trên đã tính = 1/(1-p)^4 
>
>
>
> ⇨ 1/(1-p)^4|p=p^ = 1/(1-p^)^4
>
>
>
> Mẫu số: -∂^2/∂θ^2 log L(p|**x**) note trước mình đã tính = np^/p^2 + n(1-p^)/(1-p)^2
>
>
>
> Evaluate tại p^: np^/p^2 + n(1-p^)/(1-p)^2|p=p^
>
>
>
> = np^/p^2 + n(1-p^)/(1-p^)^2
>
>
>
> = n/p^ + n/(1-p^)
>
>
>
> = n/p^(1-p^)
>
>
>
> Vậy Var(g(p^)) = \[1/(1-p^)^4\] / \[n/p^(1-p^)\]
>
>
>
> = \[1/(1-p^)^4\] × \[p^(1-p^)/n\]
>
>
>
> = **p^/n(1-p^)^3**
>
>
>
> Kết quả y chang cách 1 dùng Delta method.

<br>

<a id="node-0d20ljz"></a>

- **MLE Variance Approximation Limitations**

<p align="center"><kbd><img src="assets/depno1k7k9o.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này đại ý là tuy phương pháp ước lượng xấp xỉ variance của MLE hoạt động khá tốt trong nhiều trường hợp, nhưng nó không phải là không thể fail. Đặc biệt là khi hàm h(θ^) không monotone. Trong những trường hợp như vậy, đạo hàm h'sẽ đổi dấu, và điều này sẽ dẫn đến việc underestimate - đánh giá giá trị của variance thấp hơn thực tế.
>
>
>
> Ông nói thêm, vốn dĩ, việc dùng CRLB để ước lượng xấp xỉ cho variance của h(θ^) vốn dĩ đã có thể dễ dẫn dến under estimate rồi. Nhưng với hàm không monotone thì vấn đề có thể tệ hơn.

<br>

<a id="node-irc30cd"></a>

- **Example 10.1.15 Bernoulli Variance**

<p align="center"><kbd><img src="assets/q9l4csikf6.png" width="80%"></kbd></p>

> [!NOTE]
> Quay lại sau, nhưng đại ý đoạn này là minh họa rằng khi h(θ^) ko monotone thì giá trị xấp xỉ của variance Var(h(θ^)) có thể bị thấp hơn giá trị thật.

<br>

<a id="node-2y7vyqf"></a>

- **Asymptotic Relative Efficiency**

<p align="center"><kbd><img src="assets/qf9p6fgkwop.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái đoạn này nói rằng, tính chất hiệu quả tiệm cận rõ ràng cho ta một thước đo tiêu chuẩn mà một estimator hướng tới: Ý là, xét trên diện phương sai tiệm cận, thì tốt nhất chính là đặt được cái Cramer Rao Lower Bound (1/I1(θ)), để được gọi là estimator hiệu quả tiệm cận.
>
>
>
> Thì bên cạnh vai trò trên, ta sẽ bàn qua một tác dụng nữa của tính hiệu quả tiệm cận: Đó là dùng để so sánh các estimator.
>
>
>
> Để làm việc này, ta sẽ có định nghĩa của hiệu quả tiệm cận tương đối - asymptotic relative efficiency.
>
>
>
> Định nghĩa như sau:
>
>
>
> nếu ta có hai estimator Wn và Vn thỏa:
>
>
>
> √n(Wn - τ(θ)) → (d) n(0, σW^2) và
>
>
>
> √n(Vn - τ(θ)) → (d) n(0, σV^2)
>
>
>
> thì ARE của Vn wrt Wn được định nghĩa là ARE(Vn, Wn) = σW^2 / σV^2
>
>
>
> Suy nghĩ chút về cái định nghĩa này:
>
>
>
> Ta đã biết định nghĩa của phương sai tiệm cận: Đó là nếu √n(Wn - τ(θ)) → (d) n(0, σ^2) thì phương sai tiệm cận của Wn chính là σ^2: Avar(Wn) = σ^2.
>
>
>
> Vậy thì ở đây có thể hiểu định nghĩa của hiệu quả tiệm cận tương đối của Vn đối với Wn chính là tỉ lệ của Avar(Wn) và Avar(Vn) thôi chứ có gì đâu: 
>
>
>
> ARE(Vn, Wn) = Avar(Wn) / Avar(Vn)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bài giải thích rất rõ ràng, bám sát nội dung gốc và còn mở rộng thêm chiều sâu bằng cách liên hệ với Cramer-Rao Lower Bound và định nghĩa phương sai tiệm cận (Avar), giúp người đọc dễ hiểu hơn về bản chất của Hiệu quả tiệm cận tương đối (ARE). Không có điểm yếu đáng kể, đây là một ghi chú xuất sắc.

**🔗 See also:** [Estimating a Gamma Mean](#node-dv9sls8)

<br>

<a id="node-eej3duv"></a>

- **Example 10.1.17 Poisson Estimators**

<p align="center"><kbd><img src="assets/ontzebnie1s.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ này sẽ giúp ta thấy công dụng của ARE (hiệu quả tiệm cận tương đối). Đầu tiên, bài toán là cho X1, X2,... iid Poisson(λ). Và ta muốn estimate xác suất 0.
>
>
>
> Hiểu đại khái Xác suất 0, tức là xác suất X \~ pois(λ), bằng 0. Tức P(X = 0), và với pdf của Pois, thì P(X = 0) là e^-λ. Và ta hiểu thế này: ta ko biết λ thật bằng bao nhiêu, và ta muốn estimate cái hàm h(λ) = e^-λ này.
>
>
>
> Và đây cũng chỉ là bài toán point estimation thôi, thay vì estimate λ, ta estimate h(λ).
>
>
>
> Thế thì, mình nghĩ, ủa, thì nói mẹ nó là estimate λ đi, khi mày estimate được λ, ví dụ có λ^ (mle của λ) thì e^-λ^ sẽ là estimate cho "xác suất 0" không đúng sao.
>
>
>
> Nhưng cứ đọc tiếp: Thì tiếp theo, đại khái là gs nói rằng một cách đơn giản để estimate h(λ) đó là đặt Yi = I(Xi = 0), và dùng τ^ = (ΣYi)/n để estimate cho h(λ).
>
>
>
> Chỗ này mình hiểu: Có nghĩa là, cách làm naive và đơn giản là xem thử trung bình thì có bao nhiêu observed data = 0. Vì cái ta muốn estiamte là xác suất X = 0 mà. Nên ta sẽ đếm xem số event Xi = 0, hay số observed data có giá trị 0, và lấy trung bình.
>
>
>
> Và tức là mình hiểu Y1, ..Yn là các statistic: Y1 = I(X1 = 0), ..Yn = I(Xn = 0) và vì X1,..Xn iid \~ pois(λ) nên Y1,...Yn cũng tạo thành random sample iid \~ Bern(P(X = 0)), tức Bern(e^-λ) và τ^ chính là sample mean của random sample này.
>
>
>
> Nên ta có thể ghi là τ^(**Y**), mà thậm chí cũng có thể ghi là τ^(**X**), vì anyway, **Y** vẫn là hàm theo **X**: **Y** = \[I(X1 = 0, ...I(Xn = 0)\]
>
>
>
> Trong các chap trước mình đã biết với X \~ Bern(p) thì EX = p, Var(X) = p(1-p).
>
>
>
> Và ta cũng đã biết E\[Xbar\] = EX, Var(Xbar) = Var(X)/n
>
>
>
> Nên áp dụng vào đây, E\[τ^\] = EYi = e^-λ và Var(τ^) = (e^-λ)(1-e^-λ)/n
>
>
>
>  Nói thêm một ý, τ^, tức τ^(**Y**), là sample mean của sample Y1,...Yn như đã nói ở trên, nên theo CLT: √n(τ^ - E(Yi)) → (d) n(0, Var(Yi))
>
>
>
> ⇔ √n(τ^ - e^-λ) → (d) n(0, (e^-λ)(1-e^-λ), tí nữa ta sẽ dùng cái này.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Phân tích của bạn rất sâu sắc và chính xác, thể hiện sự hiểu rõ các khái niệm và khả năng đặt câu hỏi phản biện. Bạn đã giải thích rất rõ ràng nguồn gốc và ý nghĩa của các công thức, làm nền tảng vững chắc cho việc tìm hiểu về AREs.

<br>

<a id="node-jiyzyog"></a>

- **MLE of e-lambda with Delta Method**

<p align="center"><kbd><img src="assets/5w17dcipotv.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo, gs nhắc đến mle của λ, là sample mean λ^ = (Σi Xi) / n cũng như nói e^-λ^ sẽ là mle của e^λ. Cùng tìm hiểu ý này.
>
>
>
> Đầu tiên là công thức mle. Có thể đi chứng minh lại nhanh:
>
>
>
> ML estimator, λ^(**x**) = argmax L(λ|**x**) = argmax f(**x**|λ)
>
>
>
> tức là ta cần giải bài toán tối ưu: maximize\_λ L(λ|**x**)
>
>
>
> f(**x**|λ) = L(λ|**x**) = Πi f(xi|λ) = Πi \[e^-λ λ^xi / xi!\]
>
>
>
> = (e^-λ)^n λ^(Σi xi) / (Πi xi!)
>
>
>
> Chuyển sang bài toán tương đương dùng hàm log
>
>
>
> ⇨ log L(λ|**x**) = log {(e^-λ)^n λ^(Σi xi) / (Πi xi!)}
>
>
>
> = log(e^-nλ) + log\[λ^(Σi xi)\] - log\[Πi xi!\]
>
>
>
> = -nλ +(Σi xi) log(λ) - log(Πi xi!)
>
>
>
> Again, chuyển sang bài toán tương đương tiếp tiếp theo, bằng cách bỏ đi constant:
>
>
>
> maximize\_λ {g(λ) = -nλ +(Σi xi) log(λ)}
>
>
>
> d/d g(λ) = 0 ⇔ -n + (Σi xi) 1/λ = 0 ⇔ λ = (Σi xi)/n, đây là stationary point. Và hàm (Σi xi) log(λ) là hàm concave, -nλ là hàm affine, vừa concave vừa convex ⇨ tổng hai hàm là concave function. Vậy stationary point chính là maximum ⇨ λ^ = (Σi xi)/n
>
>
>
> Còn ý thứ hai khi nói e^-λ^ cũng là mle của e^-λ là vì ta có theorem trong chap 7 nói về tính invariance của MLE (xem link)
>
>
>
> Như vậy là đã làm rõ câu đầu.
>
>
>
> ---
>
>
>
>  Tiếp, ông dùng Delta method để có E\[e^-λ^\] ≈ e^-λ và Var(e^-λ^) ≈ λ e^-2λ/n. Thử làm lại:
>
>
>
> i) Chứng minh: Var(e^-λ^) ≈ λ e^-2λ/n. Dùng Delta method theorem:
>
>
>
> Delta method theorem nói ngắn gọn là: nếu Wn có Avar(Wn) thì Avar(g(Wn)) = \[g'(θ)\]^2 Avar(Wn)
>
>
>
> Với g(λ) = e^-λ, thì g'(λ) = -e^-λ
>
>
>
> ⇔ Avar(e^(-λ^)\] = \[-e^-λ\]^2 Avar(λ^)
>
>
>
> Tiếp, CLT nói rằng với random sample X1,...Xn có EXi = μ và Var(Xi) = σ^2 &lt; inf thì √n(Xbar - μ)/σ → (d) n(0,1). Cũng chính là √n(Xbar - μ) → (d) n(0, σ^2).
>
>
>
> Nên ta sẽ có √n(λ^ - λ) → (d) n(0, Var(Xi)). Và Var(Xi) với Xi \~ Pois(λ), cũng là λ.
>
>
>
> Vậy ta có Avar(λ^) = λ
>
>
>
> ⇨ Avar(e^(-λ^)\] = \[-e^-λ\]^2 λ = λe^(-2λ)
>
>
>
> Tức √n(e^(-λ^) - e^(λ)) → n(0, λe^(-2λ))
>
>
>
> Và cái này có nghĩa là khi n lớn thì Var\[√n(e^(-λ^) - e^(-λ))\] ≈ λe^(-2λ)
>
>
>
> ⇔ n Var\[(e^(-λ^)\] ≈ λe^(-2λ)
>
>
>
> ⇔ Var\[e^(-λ^)\] ≈ λe^(-2λ) / n
>
>
>
> ---
>
>
>
> ii) Chứng minh E\[e^-λ^\] ≈ e^-λ:
>
>
>
> Cũng là delta method: dùng xấp xỉ tuyến tính của hàm g(λ) tại λ^, vì tính consistent (LLN nói rằng sample mean sẽ → (p) về true mean λ, và theo định nghĩa của consistent thì λ^ chính là consistent estimator của λ) chính là khi nên khi n → ∞ thì λ^ sẽ → λ, cho phép ta xấp xỉ tuyến tính g(λ) tại λ':
>
>
>
> g(λ^) ≈ g(λ) + g'(λ)(λ^ - λ)
>
>
>
> Tới đây nên nhớ λ^, có thể viết là λ^(**X**), cũng chỉ là một statistic, là một random variable, có được bởi áp một hàm số lên random sample **X**.
>
>
>
> Nên với việc ta xấp xỉ g(λ^) ≈ g(λ) + g'(λ)(λ^ - λ) thì do đó:
>
>
>
> g(λ^(**X**)) ≈ g(λ) + g'(λ)(λ^(**X**) - λ)
>
>
>
> Và vế trái là một random variable, vế phải cũng vậy (do đều là hàm áp lên **X**) và do đó mới có chuyện xét kì vọng của g(λ^(**X**)), cũng như là vì ta đang có hai hàm số xấp xỉ nhau, nên lấy trung bình cũng sẽ giữ dấu xỉ, và kết quả vẫn là hàm phụ thuộc λ do gốc rễ Xi \~ Pois(λ)
>
>
>
> E\_λ\[g(λ^(**X**))\] ≈ E\_λ\[g(λ) + g'(λ)(λ^(**X**) - λ)\].
>
>
>
> Hiểu bản chất rồi thì bỏ **X** đi cho gọn
>
>
>
> ⇔ E\_λ\[e^-(λ^)\] ≈ E\_λ\[g(λ)\] + E\_λ\[g'(λ)(λ^ - λ)\].
>
>
>
> ⇔ E\_λ\[e^-(λ^)\] ≈ g(λ) + g'(λ) E\_λ(λ^ - λ)
>
>
>
> ⇔ E\_λ\[e^-(λ^)\] ≈ g(λ) + g'(λ) \[E\_λ(λ^) - E\_λ(λ)\]
>
>
>
> ⇔ E\_λ\[e^-(λ^)\] ≈ e^-λ -e^-λ \[λ - λ\] (do E(λ^) = λ)
>
>
>
> ⇔ E\_λ\[e^-(λ^)\] ≈ e^-λ → Xong.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Bài giải này cực kỳ chính xác và chi tiết, không chỉ nhắc lại các công thức mà còn chứng minh từng bước một. Độ sâu phân tích vượt xa thông tin được cung cấp trong hình ảnh, thể hiện sự hiểu biết vững chắc về các khái niệm.

**🔗 See also:** [Chứng minh tính bất biến MLE](./72_method_of_finding_estimators.md#node-6d46egj) · [Stronger Central Limit Theorem](./55_convergence_concepts.md#node-yngnkwh)

<br>

<a id="node-wgjpxiz"></a>

- **Asymptotic Relative Efficiency Analysis**

<p align="center"><kbd><img src="assets/2q7cynwhz6u.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/k334xlkgwiq.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, như vậy, phần đầu ta đã có:
>
>
>
> √n(τ^ - e^-λ) → (d) n(0, (e^-λ)(1-e^-λ)/n), tức Avar(τ^) = (e^-λ)(1-e^-λ)
>
>
>
> Phần sau, ta đã tự chứng minh lại để thấy E\[e^-λ^\] ≈ e^-λ và Var(e^-λ^) ≈ λ e^-2λ/n, cũng là Avar(e^(-λ^)\] = λe^(-2λ)
>
>
>
> Nên ráp vào định nghĩa của ARE(τ^,  e^(-λ^)) = Avar(e^(-λ^)\] / Avar(τ^)
>
>
>
> = λe^(-2λ) / \[(e^-λ)(1-e^-λ)\]
>
>
>
> = λe^(-2λ) / \[(e^-λ)(1-e^-λ)\]
>
>
>
> = λe^(-λ) / (1-e^-λ)
>
>
>
> = λ / (1/e^(-λ)-1)
>
>
>
> = λ / \[e^(λ) - 1\]
>
>
>
> Và ông nói nếu ta phác thảo cái hàm này sẽ thấy nó giảm liên tục đến gía trị lớn nhất = 1, khi λ = 0, sau đó giảm nhanh chóng.
>
>
>
>
>
> Rồi như vậy thì cái kết quả về cái sự biến động của cái hàm ARE đó gọi là đồ thị hiệu quả tiệm cận tương đối của hai cái estimator một cái τ^ và một cái là MLE. Thì kết quả này cho thấy rõ là với một cái estimator nào đó khác không phải MLE thì variance của nó, tức là cái variance tiệm cận của nó, asymptotically variance sẽ luôn luôn không thể nào vượt quá, tức là không thể nào nhỏ hơn cái phương sai tiệm cận của MLE được. 
>
>
>
> Và điều này về cơ bản là nó là điều mình đã đoán trước. Bởi vì MLE là một estimator có tính chất hiệu quả tiệm cận, asymptotically efficient. Mà theo định nghĩa của một cái estimator hiệu quả tiệm cận đó thì phương sai tiệm cận của nó sẽ đạt cái mức Cramer-Rao, mức chặn dưới. Tức là nó sẽ đạt cái mức nhỏ nhất có thể của một cái một cái estimator. Thành thử ra là cái kết quả trên nó là minh chứng hoặc là minh họa cho cái nhận định này. Để thấy rằng rõ ràng là thông qua cái chỉ số ARE đó thì mình sẽ thấy rằng là nó sẽ không thể nào mà vượt quá số một được. 
>
>
>
> (Phương sai tiệm cận của MLE ≤ phương sai tiệm cận của τ^ nên tỉ lệ không thể nào quá một)
>
>
>
> Thì cái đoạn cuối giáo sư nói rằng là cái MLE đó, cái tính chất hiệu quả tiệm cận nó cho mình một cái tiêu chí để mà so sánh các estimator.
>
>
>
> Tuy nhiên, là trong một số tình huống khác thì những estimator khác tuy có phương sai tiệm cận lớn hơn phương sai tiệm cận của MLE nhưng có thể nó sẽ tốt hơn MLE ở những tiêu chí khác ví dụ như robustness mà ở phần tiếp theo là mình sẽ nói. thử ra trong những cái tình huống như vậy giáo sư kết luận rằng cái tính hiệu quả của MLE nó trở thành một một yếu tố có thể khiến mình phải đắn đo trong cái việc là sử dụng những estimator khác: kiểu như nếu dùng cái khác thì phải hi sinh bao nhiêu mức efficient

> [!TIP]
> **🤖 AI Feedback** — ⚠️ Score: **85/100**
>
> Bài làm đã thể hiện sự hiểu biết sâu sắc về cách tính toán và rút gọn biểu thức ARE, các bước đạo hàm và rút gọn đại số đều chính xác. Tuy nhiên, mô tả về hành vi của hàm số chưa hoàn toàn đúng; hàm ARE này thực tế là giảm nghiêm ngặt thay vì tăng liên tục đến giá trị lớn nhất.

<br>

<a id="node-dv9sls8"></a>

- **Estimating a Gamma Mean**

<p align="center"><kbd><img src="assets/qv079363zf8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/917jged40as.png" width="80%"></kbd></p>

> [!NOTE]
> Quay lại ví dụ này sau, nhưng đại ý là minh họa rằng, đôi khi việc chịu khó tính mle là đáng, vì các estimator khác dễ tính toán hơn như method of moment ở đây ko tốt bằng.
>
>
>
>  Nhớ lại ARE(Vn, Wn) = Avar(Wn) / Avar(Vn) là tỉ số của Avar của estimator này với estimator kia. Với MLE, là cái có tính chất hiểu quả tiệm cận, có Avar đạt CRLB, thì tỉ số AVar của estimatorkhac1 so với Avar của MLE estimator  luôn ≥ 1. Và đồ thị cho thấy điều này.

**🔗 See also:** [Asymptotic Relative Efficiency](#node-2y7vyqf)

<br>

<a id="node-gumecun"></a>

- **Bootstrap Standard Errors**

<p align="center"><kbd><img src="assets/pjzm3ffj69.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này sẽ giới thiệu về **Bootstrap Standard Error**:
>
>
>
> Đại ý là vầy: Bootstrap dựa trên một ý tưởng là: Trong statistic, ta tìm cách hiểu về một population distribution dựa trên việc lấy mẫu (sample).
>
>
>
> Thế thì, vì sample sẽ đại diện cho population, nên nếu ta có thể tìm thấy các đặc điểm tương tự giữa nhiều sample, thì nó sẽ giúp ta inference về đặc điểm của population.
>
>
>
> Và để có nhiều sample phục vụ cho việc tìm ra những đặc điểm tương tự, người ta sẽ làm động tác là take các **resample** (tạm hiểu là **lấy mẫu từ mẫu ban đầu**) theo lối **sampling with replacement**.

> [!TIP]
> **🤖 AI Feedback** — ⚠️ Score: **85/100**
>
> Ghi chú đã nắm bắt rất tốt ý tưởng cốt lõi của Bootstrap, từ việc sử dụng mẫu để hiểu quần thể cho đến quá trình resample với việc bổ sung chi tiết 'sampling with replacement' rất giá trị. Tuy nhiên, ghi chú có thể hoàn thiện hơn nếu đề cập rõ ràng hơn về mục đích chính của Bootstrap là một phương pháp thay thế để tính toán sai số chuẩn.

**🔗 See also:** [Example 1.2.20 Calculating Average](./124_enumerating_outcome.md#node-pl75v3r)

<br>

<a id="node-f5aaasl"></a>

- **Bootstrapping a variance**

<p align="center"><kbd><img src="assets/0tths2o6fcvl.png" width="80%"></kbd></p>

> [!NOTE]
> Ok, sau khi đã ôn lại 1.2.20, mình có thể tóm tắt lại bối cảnh của phần này như sau:
>
>
>
> Bài toán là, ta có tập 4 con số {2,4,9,12} và thực hiện việc lấy mẫu 4 số theo lối có hoàn lại (with replacement) từ 4 con số này, và tính trung bình, gán cho X. Câu hỏi đặt ra là X có bao nhiêu possible value, và pmf tương ứng là bao nhiêu.
>
>
>
> Thế thì việc trả lời câu hỏi thứ nhất, trở thành bài toán đếm số possible outcome khi sampling with replacement 4 lần từ 4 con số trên, và ta không care thứ tự, ví dụ coi (2,4,4,9) cũng giống (2,9,4,4). Và bài toán này khớp với frame của bài toán khái quát là: Có n item khác nhau 1,2,...n, bốc r lần theo lối sampling có hoàn lại, thì có bao nhiêu possible outcome khác nhau trong đó ta không care thứ tự. Và công thức cho kết quả sẽ là (n + r - 1 choose r)
>
>
>
> Còn để trả lời cho câu hỏi sau: pmf là bao nhiêu, tức là tính xác suất của event, ta phải tính theo order sample. mà trong note của phần đó, mình đã thấy rằng, nếu tính theo unordered sample space, kết quả sẽ là xác suất các possible outcome (cũng là giá trị các pmf P(X = xi)) đều là 1/ (n + r - 1 choose r) (và ở đây, với r = n, sẽ là 1 / (n + n - 1 choose r) = 1/(7!/4!3!) = 1/35).
>
>
>
> Kết quả đúng phải là tính theo ordered sample space thì (4,2,4,4) cũng phải khác so với (2,4,4,4), và số possible outcome chính là (4 × 4 × 4 × 4) = 4^4. Do đó, xác suất của mọi outcome sẽ là 1/4^4.
>
>
>
> Thế thì: ở đây, ông nói cái ví dụ trên chính là dạng đơn giản của kĩ thuật **bootstrap** - gọi là **non-parametric bootstrap** một kĩ thuật quan trọng trong statistic.
>
>
>
> Và cụ thể là cái mà ta làm (sampling with replacement) 4 item từ set {2,4,9,12} **và tính trung bình** chính là ta đã **resample các possible values của sample mean**.
>
>
>
> Ta thấy như ở trên đã nhắc lại, rằng X sẽ có 35 possible values (cũng là số possible outcome khi xét unorder sample space của thử nghiệm), nhưng mỗi value có xác suất khác nhau (không equally likely, hay nói ở trong sách là không equiprobable, cũng là nghĩa đó).
>
>
>
> Còn 4^4, số possible outcome khi xét order sample space, thì chúng equally likely và ở đây nói "**có thể đối xử với 4^4 = 256 possible outcome này như random sample"** ("**can be treat as random sample"**) là sao?
>
>
>
> Có nên hiểu ý của gs Casella là: **TREAT NÓ NHƯ TOÀN BỘ SAMPLE SPACE**, và vì vậy, nó **CŨNG CHÍNH LÀ MỘT RANDOM SAMPLE**.
>
>
>
> Hiểu như vầy: Vì 256 outcomes này là **mọi khả năng có thể có** khi (sampling 4 lần từ 4 numbers {2,4,9,12}), để rồi tạo nên mọi possible value của con số X (trung bình 4 con số kết qủa cuả mỗi outcome). Do đó, cái tập 256 outcome này, chính là một **ORIGINAL SAMPLE SPACE S** (hay Ω) của một experiment.
>
>
>
> Thế thì với **random sample**, hãy nhớ lại định nghĩa của nó: Đó là, ta quan sát một đại lượng ngẫu nhiên nào đó n lần, giá trị mỗi lần sẽ được đại diện bởi một random variable Xi, và việc quan sát sẽ được thực hiện sao cho các random variable X1,...Xn này độc lập (mutually independent) và có cùng distribution (identically distributed).
>
>
>
> Vậy thì, giả sử ta lấy mẫu từ cái original sample space S, với n = 256, thì nếu quan sát thấy X1 = g(s1), X2 = g(s2),...với s1,..s256 là các outcome nói trên, và g(.) là hàm tính trung bình. Thì rõ ràng đây vẫn là một random sample hợp lệ.
>
>
>
> Và do đó, bản thân cái sample space - nói đúng hơn, là tập {g(s1), g(s2),....g(s256)}, hay {g(s): s ∈ S} cũng là một valid observed value của một random sample size n = 256.
>
>
>
> Như vậy ta có thể hiểu đại khái ý của gs khi ông nói có thể coi "4^4, số possible outcomes" như một random sample là vậy.
>
>
>
> Thế thì vì sao tập 35 unordered outcomes lại không phải là random sample.
>
>
>
> → Có thể trả lời là bởi vì tập này không phải là original sample space, chúng chứa các outcome (gọi là các event cũng được, vì ta nhớ định nghĩa của event chỉ là một tập các outcome trong original sample space) chứa các original (ordered) outcome: Ví dụ ta đã thấy trong (phần 1.2.4 - xem link) {2,4,4,9} sẽ "chứa" / "tương ứng" với 12 ordered original outcome.
>
>
>
> Và như vậy, không thể coi nó là original sample space, thì ko thể coi nó là random sample được, vì với định nghĩa của random sample như nói trên, thì original sample space có thể coi như một version đặc biệt của random sample, khi **có size bằng đúng original sample space size**, và các observed value của các random variable **chứa đủ mọi possible value của original sample space** - đây chẳng phải là một **random sample lí tưởng** sao - khi chắc chắn nó chính là cái có kích thước nhỏ nhất nhưng chứa đủ mọi thông tin của population.

> [!TIP]
> **🤖 AI Feedback** — ⚠️ Score: **88/100**
>
> Bạn đã tóm tắt và phân tích rất tốt bối cảnh bài toán, sự khác biệt giữa 35 giá trị trung bình phân biệt và 256 mẫu con có thứ tự, cũng như vai trò của tính đồng xác suất. Tuy nhiên, phần diễn giải về "có thể coi như một random sample" cho 256 mẫu con có thể đơn giản hơn, tập trung vào việc mỗi mẫu con có thứ tự đều có xác suất xuất hiện như nhau (1/256), tạo nên một không gian mẫu đồng xác suất.

**🔗 See also:** [Đếm mẫu tính xác suất](./124_enumerating_outcome.md#node-q02rbqh)

<br>

<a id="node-3dm7cfv"></a>

- **Point Estimation: Variance Estimation**

<p align="center"><kbd><img src="assets/rozddooqopg.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì khi đã coi như 256 possible values có được bằng cách xét 256 possible outcomes của thử nghiệm (sampling with replacement 4 số từ tập {2,4,9,12}) là một random sample (dĩ nhiên size 256). Và ta kí hiệu với resample thứ i là xbar\*\_i.
>
>
>
> Như vậy, có thể viết lại tương tự như cách viết thông thường của random sample như sau:
>
>
>
> (kiểu như "ta có random sample size n: X1,..Xn iid có observed value x1,...xn")
>
>
>
> Ta có random sample size n = 256: Xbar\*\_1, Xbar\*\_2,....,Xbar\*\_n, có observed value xbar\*\_1,...xbar\*\_n.
>
>
>
> Và với random sample X1,...Xn, mình đã quen thuộc với việc, ta có thể tính **sample variance**: S^2 = \[1/(n-1)\] Σi {(Xi - Xbar)^2})
>
>
>
> Thì ở đây cũng vậy, với random sample Xbar\*\_1, Xbar\*\_2,...Xbar\*\_256, ta có thể tính sample variance
>
>
>
> = \[1/(256 - 1)\] Σi=1:256 {(Xbar\*\_i - (Xbar\*)bar)^2}
>
>
>
> Làm rõ: (Xi - Xbar)^2 với Xbar = Σi Xi, thì sẽ ứng với Xbar\*\_i - (Xbar\*)bar với (Xbar\*)bar = Σi Xbar\*\_i
>
>
>
> Và con số 256 ở đây là chính là n^n (vì cái bài toán gốc là sampling with replacement 4 số từ tập có 4 số {2,4,9,12} để rồi order sample space có size 4^4, thì khái quát là sampling with replacement n số từ tập có n số, thì order sample space có size n^n)
>
>
>
> Như vậy ta hiểu cái công thức Var\*(Xbar) = \[1/(n^n - 1)\] Σi=1:n^n {(Xbar\*\_i - (Xbar\*)bar)^2} có bản chất là:
>
>
>
> Sample variance của một random sample size n^n, mà bản thân random sample này, chính là original sample space của thử nghiệm: sampling with replacement n item từ set có n item.
>
>
>
> Như vậy ta có thể tóm tắt lại, như cách để giải thích ngắn gọn lại cái công thức trên là cái quái gì:
>
>
>
> Bài toán lớn đặt ra là: Ta có một sample size n, và muốn estimate Variance của sample mean Xbar: Var(Xbar), mà trong các phần trước của chương này, ta đã có một số cách tiếp cận.
>
>
>
> Thế thì ở đây Bootstrap cho ta một cách làm như sau:
>
>
>
> Ví dụ, sample size n ban đầu có n giá trị quan sát được x1,...xn. Thì từ đó ta đặt ra một experiment như sau: Sampling with replacement n (items, hay sample) từ sample size n ban đầu.
>
>
>
> Và mỗi một "sample từ sample" như vậy, (mà ta gọi là resample) có n con số, và đem tính trung bình.
>
>
>
> Thế thì, xét cái original sample space của thử nghiệm này, tức là, tập chứa mọi possible outcome, trong đó ta có phân biệt thứ tự các item, sẽ có kích thước là n^n. Và mỗi outcome đều equally likely.
>
>
>
> Như vậy, nếu gọi s_1,...s_n^n là các possible outcome trong original sample space này, thì tập g(s_1), ...g(s_n^n) với hàm g là hàm tính trung bình của n con số của mỗi outcome, ta sẽ có thể coi nó là một random sample size N = n^n - là một random sample Xbar\*1, Xbar\*2,....Xbar\*\_N
>
>
>
> vì sao: Vì nếu ta lấy random sample size m từ original sample space này, thì cơ bản theo định nghĩa, chỉ là ta sẽ sampling từ original sample space này m lần, mỗi lần đại diện bởi một random variable X1,...Xm. Thế thì, nếu ta cho m = N, và X1 = g(s_1), X2 = g(s_2),...XN = g(s_N) thì nó vẫn hoàn toàn hợp lệ là một random sample:
>
>
>
> X1,...XN đều có cùng distribution, do P(X1 = g(s_i)) đều bằng 1/n^n với mọi i. P(X2 = g(s_i)) = 1/n^n với mọi i. Nên X1,...XN đều có cùng distributionn là discrete uniform P(X = g(s_i)) = 1/n^n với mọi i từ 1,2....n^n.
>
>
>
> Và ta kí hiệu random sample này là Xbar\*\_1, Xbar\*\_2,....Xbar\*\_N. Từ đó có thể dùng công thức để tính sample variance. Mà sample variance là một estimator cho variance của population, mà với population này, lại là population / sample space của các sample mean (Xbar\*\_1, Xbar\*\_2,....). Như vậy, ta sẽ có thể dùng nó để có estimate cho variance của sample mean, thông qua phương pháp bootstrap: Var\*(Xbar)
>
>
>
> Nếu ta xét unordered sample space, ví dụ {w_1, w_2,...w_K} nơi các outcome không equally likely thì bản thân nó không thể được coi là random sample theo nghĩa sau đây: 
>
> Ví dụ nếu ta coi như X1,...XK có các observed value là g(w_1),....g(w_K) thì 
>
>
>
> P(X1 = g(w_i)) = P(w_i)  với i = 1,2,...K
>
>
>
> P(X2 = g(w_i)) = P(w_i) với i = 1,2,...K. 
>
>
>
> ...
>
>
>
> Như vậy thì X1,X2,...XK cũng có chung distribution (distribution này không phải là uniform discrete thôi)
>
>
>
> Có điều khi mình cho rằng X1,X2,....XK mang observed value là g(w_1), g(w_2),..., g(w_K) thì sẽ xảy ra vấn đề:
>
>
>
> Nó không phản ánh đúng phân phối xác suất thực tế của sample space. Nói rõ hơn, ta sẽ liên hệ lại order sample space.
>
>
>
> Vì 256 outcome của order sample space có xác suất như nhau, nên bộ observed value X1 = g(s_1), X2 = g(s_2),....X256 = g(s_256) hoàn toàn có thể xảy ra. (Dĩ nhiên, X1, X2,...X256 là các random variable, nên mỗi thằng có thể có 256 possible values, nhưng vì 256 possible values này các xác suất như nhau, nên việc một bộ observed value là (g(s_1), g(s_2),....g(s_N)) là hoàn toàn bình thường. Và bộ giá trị quan sát này, trong đó mỗi possible value g(s_i) đều xuất hiện 1 lần, phản ánh được đặc điểm của phân phối gốc của order sample space - là discrete uniform.
>
>
>
> Trong khi đó, với unorder sample space, 35 possible outcome w_1,...w_35 này lại có xác suất RẤT KHÁC NHAU. Thành ra, tuy rằng khi xét một bộ random variable X1,X2,...X35, trong đó X1, X2,...độc lập, và P(X1 = g(w_i)) cũng bằng P(X2 = g(w_i)) = ...P(XK = g(w_i)) và đều bằng xác suất xảy ra của outcome w_i, tức là X1,...XK cũng cùng distribution, do đó X1,...XK vẫn là một random sample. Tuy nhiên, nếu mình xét một bộ observed value là X1 = g(w_1), X2 = g(w_2), ...XK = g(w_K) thì ta lại đang tạo ra một bộ observed value KHÔNG PHẢN ÁNH ĐÚNG PHÂN PHỐI XÁC SUẤT CỦA CÁC OUTCOME TRONG UNORDER SAMPLE SPACE. Vì với bộ observed value này, mỗi possible value lại xuất hiện một lần, đều nhau, trong khi xác suất của chúng trong sample space gốc là khác nhau.
>
>
>
> Tóm lại, phải hiểu ý nghĩa của việc nói "có thể treat bộ observed value (g(s_1), g(s_2), ...g(s_N)) là một random sample thì ý là, vì bộ giá trị quan sát được này, nó phản ánh được phân phối xác suất của sample space. Còn nếu dùng unordered value thì không.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bài giải thích rất sâu sắc và chi tiết về bản chất của công thức ước lượng phương sai bootstrap, đặc biệt là việc làm rõ vì sao tập hợp các giá trị trung bình từ không gian mẫu có thứ tự (n^n resamples) có thể được coi là một mẫu ngẫu nhiên để tính phương sai. Bạn đã đi sâu vào lý thuyết và giải thích rõ ràng các khái niệm phức tạp.

**🔗 See also:** [Tính chất trung bình phương sai mẫu](./52_of_random_variables_from_a_random_sample.md#node-411jdqg) · [Thống kê mẫu cơ bản](./52_of_random_variables_from_a_random_sample.md#node-8bhfv8j)

<br>

<a id="node-6duo97a"></a>

- **Bootstrap Mean and Variance**

<p align="center"><kbd><img src="assets/h8pcm17myto.png" width="80%"></kbd></p>

> [!NOTE]
> Ôn lại nhanh, về bootstrap:
>
>
>
> Câu chuyện là, ta có 4 con số {2,4,9,12}. Và muốn tính variance của sample mean Var(Xbar).
>
>
>
> Có hai góc nhìn về 4 con số này:
>
>
>
> i) Góc nhìn 1: Có thể hiểu 4 con số này là một observed value của một random sample X1, X2, X3, X4, được sampling từ population distribution. Và như vậy Xbar = Σi Xi có observed value là = (2 + 4 + 9 + 12) / 4 = 27/4 = **6.75**
>
>
>
> Và ta muốn ước lượng variance của Xbar: Var(Xbar)
>
>
>
> Mà Var(Xbar), theo công thức, ta có σ^2/n với σ^2 là phương sai của population, là Var(X1)
>
>
>
> Do không có σ^2, ta có thể dùng S^2, sample variance = \[1/(n-1)\] Σi (Xi - Xbar)^2. Nên ở đây với observed value **x** = (2,4,9,12) ta có S^2(**x**) = (1/3) \[(2-6.75)^2 + (4-6.75)^2 + (9-6.75)^2 + (12-6.75)^2\] = 20.9167 ⇒ Var(Xbar) ≈ S^2/n = 20.9167/4 = **5.23**
>
>
>
> Và cái **Var(Xbar) nhưng dùng S^2 để estimate cho σ^2** này ta kí hiệu là Var^(Xbar): **Var^(Xbar)** = 5.23
>
>
>
> ---
>
>
>
> ii) Góc nhìn thứ hai: Coi {2,4,9,12} là một population, gọi là **empirical population**. Có nghĩa là nó là một **sample space** **chứa mọi possible outcome**.
>
>
>
> Và đối với cái empirical population này, người ta mới thực hiện động tác: Sampling with replacement 4 con số - tức là, đây chính là drawing một sample từ population, nhưng vì đây bản thân là một sample trong population gốc, nên ta gọi kết quả drawing này là resample (vẫn có ý nghĩa là một random sample từ empirical distribution).
>
>
>
> Vậy thì, xét cái empirical population này, ta có thể hiểu nó như distribution của một discrete random variable X, có 4 possible value 2, 4, 9, 12, với xác suất pmf bằng nhau, = 1/4.
>
>
>
> Và dựa trên công thức mean và variance ta có thể tính mean và variance của population này:
>
>
>
> Mean của empirical population: EX = Σ{2,4,9,12} xi × P(X=xi) = (1/4) (2 + 4 + 9 + 12) = 27/4 = **6.75**
>
>
>
> Variance của empirical population: VarX = E\[(X-EX)^2\] = Σ\_{mọi possible value của X} P(X=x)(x - xbar)^2
>
>
>
> = (1/4) \[(2-6.75)^2 + (4-6.75)^2 + (9-6.75)^2 +(12-6.75)^2\] = **15.6875**
>
>
>
> Và với cái empirical population này, như đã nói, ta sẽ drawing các resample: sampling with replacement 4 số từ đó. Với mỗi kết quả, ta tính mean (tức là sample mean). Và ý tưởng lớn sẽ là:
>
>
>
> **BOOTSTRAP SẼ CHO PHÉP TA DÙNG VARIANCE CỦA SAMPLE MEAN NÀY** (**VARIANCE CỦA RESAMPLE MEAN**, **HAY CÒN GỌI LÀ** **BOOTSTRAP SAMPLE MEAN** **Var\*(Xbar)** để mà **ESTIMATE CHO VARIANCE CỦA CÁI SAMPLE MEAN** của population gốc Var(Xbar) (mà trong đó {2,4,9,12} chỉ là một sample).
>
>
>
> Thế thì, áp dụng công thức Variance của bootstrap sample mean Var\*(Xbar) = \[bootstrap population variance, chính là **15.6875**\] / \[resample size, = 4, (vì sampling 4 số từ {2,4,9,12}\] (đây chính là công thức σ^2/n, theorem chương 5, về mean và variance của Xbar thôi) = **15.6875** / 4 = **3.921875**.
>
>
>
> ---
>
>
>
> Thế thì tiếp theo ta sẽ làm như sau, để cũng ra con số **3.921875**: Và đây mới là phương pháp bootstrap (con số trên chỉ là vì ta đã biết empirical population variance = **15.6875** mà **NGUYÊN NHÂN SÂU XA CŨNG LÀ VÌ TA ĐÃ BIẾT CÔNG THỨC VARIANCE VarX = E(X-EX)^2**. Mục đích là ta sẽ thấy cách tính boostrap cũng ra được con số này, để hiểu rằng nó có thể dùng để tính Variance của các đại lượng khác (không phải sample mean, mà là những cái khác). Cách làm ngắn gọn như sau:
>
>
>
> Ta xét tập chứa mọi order outcome của việc bốc có hoàn lại 4 con số từ {2,4,9,12}. Và vì random sampling with replacement, và ta có phân biệt thứ tự tên tập các possible outcome sẽ có cả (2,2,2,2), hoặc (2,4,9,12) hoặc (4,2,12,9). Và số lượng (cũng là kích thước order sample space) sẽ là: 4^4 (kết quả này ko khó để đếm theo step rule: bước 1 chọn số thứ nhất, có 4 khả năng, bước 2 chọn số thứ hai, cũng có 4 khả năng, ... → có 4^4 khả năng, và xác suất của mỗi khả năng đều là (1/4)^4.
>
>
>
> Như vậy, order sample space có 4^4 = 256 possible outcome với xác suất bằng nhau. gọi chúng là {s1,...sN} với N = 4^4 (Mà khi khái quát lên, trong random sample có size n (mà trong ví dụ này, là 4 ({2,4,9,12}), thì order sample space sẽ có size N = n^n)
>
>
>
> Và với mỗi outcome (là một bộ 4 số), ta bỏ vào hàm g(s) để tính trung bình 4 số này.
>
>
>
> Như vậy, lập luận mấu chốt là: Vì order sample space, lúc bấy giờ, ta có thể coi như là một population nữa (hồi nãy đã coi {2,4,9,12} là một empirical population, giờ lại coi {g(s1),...g(sN)} là một population, có xác suất bằng nhau.
>
>
>
> Thế thì, tiếp theo, nếu ta tiến hành sampling từ cái population này, ví dụ tạo một random sample size N: X1,...XN. Và thay vì dùng kí hiệu X, ta dùng Xbar\*, vì g(s) mang ý nghĩa là trung bình 4 số, trung bình của resample, resample mean. Như vậy ta có random sample size N: Xbar\*1, ....Xbar\*N, iid, có chung distribution, và dễ thấy đây là discrete uniform, có 256 possible value, pmf bằng nhau và bằng 1/256.
>
>
>
> Và vì population này có distribution discrete uniform, nên khi ta dùng bộ observed value: {Xbar\*1 = g(s1), Xbar\*2 = g(s2), ..., Xbar\*N = g(sN)}, thì nó có thể phản ánh distribution của order sample space.
>
>
>
> Và vì vậy, người ta mới nói, có thể đối xử với bộ observed value này {g(s1), g(s2),...g(sN)} như một random sample.
>
>
>
> Và ta sẽ dùng công thức của sample variance của random sample này:
>
>
>
> Trước tiên tính mean của sample này: (1/N) (Xbar\*1 + Xbar\*2 + ..Xbar\*N), và ta kí hiệu là (Xbar\*)bar (là cái x\* có 2 gạch trên đầu trong sách)
>
>
>
> 1/(N-1) Σi=1:N \[Xbar\*i - (Xbar\*)bar\]^2
>
>
>
> Và đây, đây chính là công thức tính VARIANCE CỦA SAMPLE MEAN THEO BOOTSTRAP, GỌI LÀ BOOTSTRAP VARIANCE CỦA SAMPLE MEAN. Và theo gs, nếu ta thế kết quả vào: Cho i lần lượt bằng 1, 2, ...256. \]
>
>
>
> Sau tính xbar\*i = g(si). Rồi tính (xbar\*)bar, và thế vào công thức trên ta sẽ ra kết quả là:
>
>
>
> (xbar\*)bar = **6.75**
>
>
>
> Var\*(Xbar) = **3.94**
>
>
>
> VÀ Ý QUAN TRỌNG TÁC GIẢ MUỐN NÓI
>
>
>
> Bootstrap sample mean (Xbar\*)bar (**6.75)**
>
>
>
> BẰNG Y CHANG
>
>
>
> Mean của empirical population (**6.75)**
>
>
>
> Và:
>
>
>
> Bootstrap variance của sample mean Var\*(Xbar) = **3.94**
>
>
>
> GẦN NHƯ BẰNG
>
>
>
> Variance của bootstrap sample mean Var\*(Xbar) **3.921875**.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bài viết này rất chi tiết và chính xác trong việc giải thích phương pháp bootstrap, đặc biệt là cách tính toán mean và variance của bootstrap sample. Các giá trị số liệu trong bài khớp hoàn toàn với ví dụ được cung cấp, thể hiện sự hiểu biết sâu sắc. Để hoàn hảo hơn, có thể cân nhắc cô đọng một số đoạn giải thích để bài viết mạch lạc và dễ tiếp thu hơn.

<br>

<a id="node-uvh5j60"></a>

- **Bootstrap Variance Formula**

<p align="center"><kbd><img src="assets/84vigtv9ler.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì, trong note vừa rồi ta đã hiểu bootstrap giúp mang đến một phương pháp để estimate variance của sample mean.
>
>
>
> Cần phải nhắc lại lần nữa để làm rõ mục đích của bootstrap:
>
>
>
>  Giả sử ta có một observed value của một random sample draw từ một population P nào đó, mang giá trị {2,4,9,12}. Dĩ nhiên, nếu gọi Xbar là sample mean của sample size 4, thì (2+4+9+12)/4 chính là một observed value của cái statistic Xbar này. Thế thì mong muốn cuối cùng là, ta muốn estimate Var(Xbar).
>
>
>
> Rồi, thế thì ta mới nhớ đến việc đã học một điểm kiến thức ở chap 5 (theorem 5.2.4 xem link), đã chứng minh rằng Var(Xbar) = σ^2/n, tức population variance / n. Nhưng dĩ nhiên là ta làm gì biết population variance để mà tính theo công thức này.
>
>
>
> Rồi, nếu có σ^2 thì ta sẽ có Var(Xbar) chính xác. Thì nay không có, ta có thể dùng sample variance S^2, thì ta sẽ có estimate cho Var(Xbar): Var^(Xbar) = S^2 / n. Với S^2 = (1/(n-1)) Σi (Xi - Xbar)^2.
>
>
>
> Tiếp, ta sẽ tiếp cận theo một hướng khác: Đó là, ta coi {2,4,9,12} là một empirical population. Có nghĩa là, nó là một sample space, chứ các possible outcome là 2,4,9,12. Giống như, ta có một thử nghiệm nào đó, ví dụ đó lường giá trị của X, và kết quả là X có 4 possible value là 2,4,9,12 với xác suất bằng nhau = 1/4. Khi đó, population này có mean là EX, đương nhiên theo định nghĩa của mean, = Σ{xi = 2,4,9,12} P(X=xi) × xi, và tương tự, có thể tính variance của X, tức variance của empirical population này.
>
>
>
> Thế thì, khi đó, câu chuyện là: Người ta sampling từ cái empirical population này, gọi là resample, có size 4. Ví dụ gọi là X'1, X'2, X'3, X'4. Và tính sample mean: (Σi X'i)/4, kí hiệu là Xbar\*. Và ta mới xét cái Variance của cái "sample mean từ empirical distribution này": Var(Xbar\*). Thì bởi vì với cái empirical population này, ta biết variance của nó, nên có thể tính chính xác Var(Xbar\*) = \[variance của empirical population\] / n = Var(X'1) / 4.
>
>
>
> Và câu chuyện là, người ta sẽ lấy cái Var(X\*bar) = Var(X'1) / 4 ĐỂ MÀ ESTIMATE CHO Var(Xbar) (**1**) ở trên. Nói cách khác: Người ta dùng phương sai của sample mean (trong đó sample được sampling từ empirical population {2,4,9,12}) để mà estiamte cho phương sai của sample mean (trong đó, {2,4,9,12} là một observed value của cái sample sampling từ distribution gốc P nào đó)
>
>
>
>  Và như vậy, đến đây ta có 2 cách để estimate Var(Xbar) (phương sai của sample mean của sample sampling từ population P):
>
>
>
> i) Dùng S^2/n =S^2/4, và ta tính ra là **5.23**
>
>
>
> ii) Dùng Var(Xbar\*) = **3.921875**.
>
>
>
>  Thế thì, vấn đề là, để ra con số 3.92, trong đó ta coi {2,4,9,12} là một empirical population, rồi xét sample mean của sample drawing từ population này, và từ đó dùng công thức chính xác Var(Xbar) = σ^2/n trong đó ta có σ^2 rồi (chỉ việc tính cái variance của cái empirical distribution này), thì mấu chốt là: TA ĐÃ CÓ CÔNG THỨC CỦA Var(Xbar) = σ^2 / n.
>
>
>
> Chứ **nếu như, ta muốn estimate không phải là variance của sample mean, mà là variance của một estimator nào đó khác**, thì **LÀM GÌ CÓ CÔNG THỨC** tính như Var(Xbar) = σ^2 / n. Ví dụ, estimator là sample median, thì làm gì có công thức của Var(sample median) = một hàm gì gì đó của population variance / hay population mean, để mà tính.
>
>
>
> Từ đó, ta mới thấy vai trò của bootstrap: Đó là, bằng cách xét một population khác: chứa mọi possible outcome khi sampling with replacement 4 số từ cái empirical distribution (gọi là order sample space), và theo cách tính đã biết, ta có thể tính ra con số **3.94** rất gần với 3.92187 (và con số này, bản chất chính là sample variance của random sample (Xbar\*1 = g(s1), Xbar\*2 = g(s2), ...Xbar\*N = g(sN)) với g(s) là hàm tính trung bình của cái kết quả sampling with replacement 4 số từ {2,4,9,12})
>
>
>
> Và như vậy, gs muốn nói rằng: **À, CÓ THỂ THẤY, BOOTSTRAP CÓ THỂ GIÚP TÍNH RA CON SỐ 3.92187, LÀ ESTIMATE VARIANCE CỦA SAMPLE MEAN** (nói ở ý (**1**) ở trên). VÀ NÓ CŨNG **CÓ THỂ DÙNG ĐỂ ESTIMATE VARIANCE CỦA CÁC LỌAI ESTIMATOR KHÁC NỮA**
>
>
>
>  (Ở đây mình biết thêm rằng variance của sample mean, khi lấy căn bậc hai, chính là **standard deviation của sample mean**, và cái này gọi là **STANDARD ERROR**: √Var(Xbar). Mà trong trường hợp này gs nói là ta dùng bootstrap để tính nhưng thật ra đây là cái ta không cần (vì vốn dĩ chỉ cần dùng hai công thức i) và ii)) ở trên là đủ rồi. Nhưng mục đích, như đã nói, là để giới thiệu khả năng của Bootstrap.
>
>
>
> Như vậy, với một estimator θ^ nào đó, và ta muốn estiamte Variance của nó, ta cũng sẽ làm như vậy:
>
>
>
> Đầu tiên, nhớ lại rằng, Xbar, sample mean cũng chỉ là một cái function áp lên các random variable của sample. Với Xbar thì thật ra ta có thể viết là Xbar(**X**) = Xbar(X1,...Xn) = (X1+...Xn)/n.
>
>
>
> Vậy thì một estimator θ^ nào đó thì bản chất cũng chỉ là cái hàm nào đó θ^(**X**).
>
>
>
> Thế thì ta sẽ đi lại phương pháp bootstrap và tính Var(θ^) như sau:
>
>
>
> i) Như đã nói, điểm khởi đầu là ta xét order sample space chứa mọi outcome khi sampling with replacement 4 số từ {2,4,9,12}. Nó sẽ chứa 4^4 = 256 possible outcome s1,...s256. Và map mỗi outcome với một giá trị nào đó bởi hàm θ^, ta sẽ có 256 possible value {θ^(s1),...θ^(s256)}
>
> Và, như đã hiểu, các outcome s1,..s256 đều equally likely, giúp cho {θ^(s1),...θ^(s256)} có thể được treat như một bộ observed value của random sample size 256, sampling từ cái order sample space này
>
>
>
> Và ta mới dùng công thức sample variance áp lên observed value của random sample:
>
>
>
> Var(θ^) = θ^(s1), θ^(s2), ...θ^(s256):
>
>
>
> Thay kí hiệu: θ^\*i = θ^(si)
>
>
>
> Var\*(θ^) = (1/256-1) Σi (θ^\*i - θ^\*\_bar)^2,
>
>
>
> với 256 chính là n^n.
>
>
>
> θ^\*\_bar = Σi (θ^\*i) / 256.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bạn đã giải thích rất chi tiết và dễ hiểu về phương pháp bootstrap, đặc biệt là việc làm rõ ưu điểm thực sự của nó khi áp dụng cho các ước lượng tổng quát. Việc sử dụng ví dụ số học cụ thể giúp minh họa các khái niệm một cách xuất sắc, và công thức bootstrap variance được trình bày rất chính xác.

**🔗 See also:** [Tính chất trung bình phương sai mẫu](./52_of_random_variables_from_a_random_sample.md#node-jhe69j5)

<br>

<a id="node-1gfsb6x"></a>

- **Bootstrapping a Binomial Variance**

<p align="center"><kbd><img src="assets/jlmeoqita8.png" width="80%"></kbd></p>

> [!NOTE]
> Active recall về Bootstrap method:
>
>
>
>  Bài toán đặt ra là: Ta có một bộ 4 con số: {2,4,9,12}. Có thể coi như là một observed value của một random sample size n = 4, sampling từ một distribution P gốc nào đó có. Nói cách khác, ta có một random sample **X** = (X1,X2,X3,X4) với observed value là x1 = 2, x2 = 4, x3 = 9, x4 = 12.
>
> Và bài toán đặt ra là estimate Var(Xbar).
>
>
>
> Dĩ nhiên, Xbar, là một hàm của sample: Xbar(**X**) = Σi=1:n Xi. Nó cũng là một statistic, một random variable. Và xbar = (2 + 4 + 9 + 12)/4 = 6.75 chính là một observed value của nó.
>
>
>
> Thế thì, với Xbar, đây là một statistic đặc biệt quan trọng, nên nó có công thức để tính ra phương sai chính xác rồi:
>
>
>
> Var(Xbar) = Var(Xi) / n. Tức là, population variance σ^2 chia sample size (ở đây chính là n, = 4).
>
>
>
> Dĩ nhiên, nếu ta đã biết distribution của X1,X2,X3,X4, ví dụ như biết chúng là \~ n(0, 10) thì ta cũng có ngay variance của Xbar = 10/4 = 2.5
>
>
>
> Vấn đề là, giả sử ta không biết population variance thì sao?
>
>
>
> Câu trả lời là, ta có thể dùng (observed value của) sample variance để thay chỗ của population variance, từ đó, thay vì ta có công thức chính xác Var(Xbar) = σ^2 / n, ta có công thức ước lượng: Var(Xbar) ≈ s^2/n. Và với observed value của sample, thì ta có observed value của S^2: s^2 = \[1/(n-1)\] Σi=1:n (xi - xbar)^2. Thế giá trị vào ta tính ra con số **5.23**, là ước lượng của Xbar variance.
>
>
>
> Var(Xbar) = σ^2/n ≈ Var^(Xbar) = s^2/n = **5.23** (chú ý kí hiệu Var^, var có mũ, thể hiện đây là giá trị estimate cho Var(Xbar) chính xác)
>
>
>
> Đó là cách thứ nhất: Dùng sample mean thế chỗ cho population mean trong công thức chính xác của Var(Xbar).
>
>
>
> ---
>
>
>
> Cách thứ hai: Ta sẽ coi như population gốc là một uniform discrete và {2, 4, 9, 12} chính là 4 possible value. Tức là distribution gốc có dạng discrete với P(X=2) = P(X=4) = P(X=9) = P(X=12) = 1/4. Thế thì vì 4 possible value đều có xác suất xảy ra bằng nhau, nên ta nói rằng: Có thể coi bộ 4 số {2,4,9,12} là một observed value của một random sample size 4. Lí do nói vậy là vì phân phối gốc cho phép các possible value xuất hiện với xác suất bằng nhau nên hoàn toàn hợp lệ nếu như ta có một bộ quan sát chứa cả 4 số này. (để thấy rõ hơn, ta có thể giả sử phân phối gốc của discrete variable Y có 3 possible value {1,3,4} là f(1) = f(3) = 0.5, f(4) = 0. Thì sẽ không thể cho rằng {1,3,4} là một observed value của random sample size 3 sampling từ distribution fY được, vì không thể xảy ra observed value như vậy)
>
>
>
> Rồi, thế thì với cơ sở là ta cho rằng population gốc là discrete có 4 possible value equally likely và một observed value của sample size 4: x1, x2, x3, x4) = (2, 4, 9, 12). Thì observed value của sample mean cũng là xbar = (2 + 4 + 9 + 12)/4 = 6.75
>
>
>
> (y như lúc nãy, chỉ khác là ở đây ta đang giả định distribution gốc là discrete uniform với 4 possible value)
>
>
>
> Để tính variance của Xbar., thì tới đây sẽ khác với lúc nãy:
>
>
>
> Nhắc lại lúc nãy: Khi vẫn chỉ dùng đúng bản chất, là coi {2,4,9,12} là một observed value của random sample size 4 sampling từ distribution gốc, và ta không biết population gốc là gì cả.
>
>
>
> Khi đó ta thay sample variance s^2 vào thế chỗ của population variance σ^2 để có ước lượng cho Var(Xbar) = σ^2/n ≈ Var^(Xbar) = s^2/n = **5.23**
>
>
>
> Còn bây giờ, khi ta đã giả định population gốc là X \~ discrete uniform với 4 possible value equally likely {2, 4, 9, 12} rồi thì ta sẽ có population mean và population variance chính xác:
>
>
>
> EX = Σ{x=2,4,9,12} xP(X=x) = Σ{x=2,4,9,12} x (1/4) = 6.75
>
>
>
> σ^2 = E\[(X - EX)^2\] = (LOTUS) = Σ{x=2,4,9,12} (x - 6.75)^2 P(X = x)
>
>
>
> = Σ{x=2,4,9,12} (x - 6.75)^2 (1/4)
>
>
>
> = 15.6875
>
>
>
> Và với việc có population variance (dù là population variance pha ke - vì ta đã giả định nó là discrete uniform), ta sẽ tính Var(Xbar) theo công thức "chính xác" = 15.6875/n = 15.6875/4 = 3.921875
>
>
>
> (dù nói là công thức "chính xác" nhưng dĩ nhiên đây cũng chỉ là estimate cho giá trị thật variance của Xbar, vì ta đã giáng cấp population gốc thành discrete uniform)
>
>
>
> Như vậy, ta có cách estimate thứ hai của Var(Xbar): Cũng kí hiệu Var^
>
>
>
> Var^(Xbar) = **3.92**
>
>
>
> (Var^(Xbar) của cách 1 là **5.23)**
>
>
>
> ---
>
>
>
> Thế thì, bootstrap cho ta một cách tính khác: Ý tưởng chính là vầy: Với 4 số {2, 4, 9, 12}. Sampling with replacement 4 số. Số possible outcome (có phân biệt thứ tự) dễ thấy có thể tính theo step rule: Chọn số thứ 1 có 4 khả năng, chọn số thứ 2 có 4 khả năng,.. → 4 × 4 × 4 × 4 = 4^4. Gọi ordered sample space là {s1,....sN}, N = 4^4. Và si đều có xác suất bằng nhau. Gọi xbar\*(s) là hàm phụt ra con số trung bình. Thì xbar\*1 = xbar\*(s1), xbar\*2 = xbar\*(2), ...,xbar\*256 = xbar\*(s256) sẽ chính là 256 possible value của random variable Xbar\*, có distribution uniform discrete.
>
>
>
> Và vì distribution của Xbar là discrete uniform nên ta có thể được phép coi **x** = xbar\*1,....xbar\*N là một observed value của random sample sampling từ distribution của Xbar\*. Điều này giống như, X có 3 possible value 1,2,3 có xác suất bằng nhau, nên **x** = (x1 = 1, x2 = 2, x3 = 3) có thể valid là một random sample bởi trong đó mỗi giá trị khả dĩ đều xuất hiện một lần. Mặt khác, nếu X có 3 possible value 1,2,3 với xác suất là P(X=1) = P(X=2) = 0.5, và P(X=3) = 0 thì bộ 3 giá trị cụ thể (1,2,3) không thể được xem là obsrevation của một random sample được, vì lí do là nó không phản ánh đúng phân phối thực khi xuất hiện con số 3 trong khi phân phối thực P(X = 3) = 0.
>
>
>
> Và vì coi như ta có một observed value của random sample **X**: **x** = (xbar\*1, ....xbar\*N). Nên ta có thể dùng công thức sample variance S^2: = 1/(256 - 1) Σi=1:N \[xbar\*i - (xbar\*)bar\]^2. Và ta sẽ lấy giá trị này để estimate cho variance của sample mean Var(Xbar), kí hiệu là Var(Xbar)\*
>
>
>
> Và theo công thức này, kết quả ra được là: Var(Xbar)\* = **3.94**
>
>
>
> Kết quả này rất sát với approach #2.
>
>
>
> Khiến cho ta có thể áp dụng nó để tính Variance của các statistic (estimator khác):
>
>
>
> Sở dĩ ta có thể theo approach #2 là vì ta đang tính variance của Xbar (estimator của true mean), và cái statistic này thì có công thức chính xác: \[population variance\] / n.
>
>
>
> Nhưng nếu ta muốn estimate variance của một statistic khác, W(**X**), là estimator của population parameter khác (ví dụ như population odd ratio, median) ...thì nhưng cái này chúng không có công thức tính từ population paramter như cách mà Var(Xbar) = population variance / n có. Khi đó, ta không thể có approach 2 được, và dễ thấy, cũng không có approach 1 luôn (vì bản chất approach 1 vẫn chỉ là dùng sample mean variance thay cho population variance để thành công thức ước lượng)
>
>
>
> Còn bootstrap, thì lại luôn cho phép làm được. Thành ra ta có thể dùng bootstrap để estimate variance của các estimator bất kì.
>
>
>
> ---
>
>
>
> Và với chừng đó recall, ta quay lại screenshot này, ví dụ như ở đây, ta cần estimate variance của statistic sau đây: W(**X**) = p^(1-p^) với p^ là cũng là Xbar (vì p^ ở đây là MLE estimator của Binomial(n, p), mà ta đã chứng minh, chính là Xbar). Nên estimator W(**X**) này, có thể nhìn nhận, là một hàm của Xbar, dĩ nhiên, Xbar, hay hàm của Xbar thì cũng đều là statistic hết.
>
>
>
> Thế thì, giá mà có công thức chính xác nào của Var(p^(1-p^)), ví dụ như = hàm g(p) nào đó chẳng hạn. Khi đó, ta có thể theo approach 1, 2: 
>
>
>
> Ví dụ approach 1: Không có p, ta dùng p^ thay vào, để từ công thức chính xác = g(p), ta có công thức ước lượng: = g(p^).
>
>
>
> Hoặc approach 2: Ta cũng coi distribution là uniform discrete, có các observed value chính là các possible value, với equally likely. Từ đó tính ra population mean p  và thế vào g(p).
>
>
>
> Nhưng thực tế thì không có hàm g(p) nào cả. Và bootstrap sẽ giải cứu:
>
>
>
> ---
>
>
>
> Cũng làm y như với xbar:
>
>
>
> Giả sử n observed value (như {2,4,9,12}) là x1,x2....xn.
>
>
>
> Theo quy trình: sampling n item with replacement, ta sẽ có n^n ordered possible value: s1,....sN, mỗi cái đều có xác suất bằng nhau = 1/N
>
>
>
> Gọi hàm xbar\*(s) = lấy trung bình mấy số của một outcome s. Thì ta sẽ có {xbar\*(s1),...xbar\*(sN)} là n^n possible value của một uniform discrete random variable Xbar\*. 
>
>
>
> Và do xác suất các possible value đều bằng nhau, nên ta có thể coi bộ số {xbar\*1 = xbar\*(s1),..., xbar\*N = xbar\*(sN)} là một observed value của một random sample sampling từ empirical distribution của Xbar\* này.
>
>
>
> Có nghĩa là coi như ta có một Xbar \~ empirical distribution uniform discrete có n^n possible value equally likely. Và random sample có observed value là xbar\*1, ...xbar\*N. 
>
>
>
> Nên sample variance = \[1/(n^n - 1)\] Σi=1:n^n \[xbar\*j - (xbar\*)bar\]^2
>
>
>
> ---
>
>
>
> Vậy thì ở đây tương tự:
>
>
>
> Giả sử n observed value (như {2,4,9,12}) là x1,x2....xn.
>
>
>
> Theo quy trình: sampling n item with replacement, ta sẽ có n^n ordered possible value: s1,....sN, mỗi cái đều có xác suất bằng nhau = 1/N
>
>
>
> Đặt hàm w\*(.) = \[p^(1-p^)\]\*(.) là hàm nhận cái bộ số của một outcome, và đi tính trung bình, rồi tính 1 - trung bình, rồi nhân lại với nhau.
>
>
>
> (đây là chỗ cực dễ lú: Nhờ học qua Stat110 mình để hiểu bản chất nên mới không lú chỗ này: ở đây ta treat \[p^(1-p^)\]\*() như tên hàm, y như xbar\*(.) ở trên vậy. 
>
>
>
> xbar\*(s): nhận vào s, là một dãy số, phụt ra số trung bình
>
>
>
> \[p^(1-p^)\]\*(s) : nhận vào s, là một dãy số: đi tính trung bình nhân với (1 - trung bình)
>
>
>
> Như vậy với n^n equally likely possible outcome s1,...sN ta có n^n possible values của một uniform discrete random variable W = \[p^(1-p^)\].
>
>
>
> Tương tự, vì equally likely, nên ta coi {w1 = \[p^(1-p^)\](s1), ...wN = \[p^(1-p^)\](sN)} là một observed value của một random sample sampling từ empirical distribution của W.
>
>
>
> Nên theo công thức sample variance:
>
>
>
> sample variance của W = \[1/(n^n-1)\] Σi=1:n^n (w\*j - w\*bar)^2
>
>
>
> Và nếu ta dùng \[p^(1-p^)\] làm cái tên của statitisc W luôn thì nó sẽ đẻ ra cái công thức kinh dị trong sách:
>
>
>
> sample variance của \[p^(1-p^)\], và ta định nghĩa cái này là bootstrap variance: 
>
>
>
> Var\*(\[p^(1-p^)\]:
>
>
>
> = \[1/(n^n-1)\] Σi=1: n^n (\[p^(1-p^)\]\*j - \[p^(1-p^)\]\*bar)^2

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú cực kỳ chi tiết, chính xác và thể hiện sự hiểu biết sâu sắc về phương pháp Bootstrap cũng như cách giải thích ký hiệu toán học trong sách. Bạn chỉ cần lưu ý thêm rằng trong thực tế khi n lớn, người ta thường dùng mô phỏng Monte Carlo (chọn B mẫu ngẫu nhiên) thay vì tính toàn bộ $n^n$ trường hợp vì giới hạn tính toán.

<br>

