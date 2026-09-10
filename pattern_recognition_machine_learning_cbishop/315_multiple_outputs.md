# 3.1.5 Multiple outputs

📊 **Progress:** `3` Notes | `3` Screenshots | `3` AI Reviews

---
<a id="node-5d9hd8j"></a>

<p align="center"><kbd><img src="assets/e50rzm6m55l.png" width="80%"></kbd></p>

> [!NOTE]
> Cũng nhau giải thích lại đoạn này: Đại khái là ở đây gs bàn qua bài toán regression trong đó ta không chỉ dự đoán scalar t từ input vector 𝐱, mà là dự đoán một vector 𝐭 = (t1,...tK) từ 𝐱. Có nghĩa là, lúc này, ta muốn xây dựng hàm dự đoán y(parameter, 𝐱) sẽ là hàm có output là vector (tức y là vector)
>
>
>
> Vậy thì đại khái là, với single t, thì bữa giờ đã đang xét về linear model - tức là y(𝐰, 𝐱) = w0 + w1x1 + ..wM-1 xM-1. Đặt 𝐰 = (w0, w1,...wM-1)ᵀ, và dùng hàm basis Φ(𝐱) = (Φ0(𝐱) = 1, Φ1(𝐱), Φ2(𝐱), ...ΦM-1(𝐱))ᵀ để biến hàm y thành phi tuyến đối với input 𝐱 (dù vẫn tuyến tính đối với 𝐱), ta có y(𝐰, 𝐱) = 𝐰ᵀΦ(𝐱)
>
>
>
> Vậy thì ở đây, đại ý là, ta sẽ vẫn theo lối đó, vẫn dùng Φ(𝐱), chỉ là lúc này, với K target t1,...tK cần predict thì ta sẽ có K bộ (vector) parameter **w1**, **w2**,...**wK**. Đặt thành các **cột** của matrix 𝐖. Và mô hình lúc này sẽ là 𝐲(𝐖, 𝐱) = 𝐖ᵀΦ(𝐱).
>
>
>
> Đương nhiên, 𝐲 sẽ là vector có K components, và như đã biết về góc nhìn thứ nhất khi nhân matrix với vector được học trong MIᵀ 1806, thì 𝐖ᵀΦ(𝐱) sẽ là vector có phần tử thứ i là hàng i của 𝐖ᵀ tức cột i của 𝐖, tức **wi**, dot product với vector Φ(𝐱).
>
>
>
> Tiếp, lại so sánh với single t scenario, ta còn nhớ, trong bài toán này, với cách tiếp cận xác suất ta sẽ coi target là random variable, tức là xem xét giá trị target là các observed value của random variable T (nhưng ko care distribution của 𝐗, không coi 𝐗 là random variable), và ta muốn tìm distribution của T|𝐱. (còn trong cách tiếp cận không xác suất thì chỉ việc xây dựng hàm dự đoán từ 𝐱 ra t, chẳng cần xây dựng distribution của T gì cả)
>
>
>
> Để rồi, khi đó, để làm tiếp, ta sẽ đặt ra một giả định đại khái là: giả sử ta có thể dự đoán chính xác t, thì vẫn tồn tại sai số không thể giảm được, và sai số này tuân theo Normal(0, 1/β) với β là precision mang giá trị nào đó. Khi đó dựa vào location scale theorem, giả định này đồng nghĩa ta đang giả định T \~ normal(y(𝐰,𝐱), 1/β), mang ý nghĩa là, với 𝐰 tốt nhất, ta sẽ tính được mean của distribution của T, và variance của nó đến từ variance của irreducible noise.
>
>
>
> Vậy thì quay lại, đây, hoàn toàn tương tự, chỉ là lúc này ta có nhiều t, gom lại thành vector 𝐭. Thì ta cũng sẽ giả định nó là một distribution nào đó: Và ta sẽ gỉa định là: các random variable Ti đều độc lập, và Ti \~ normal(y(**wi**, 𝐱) = **wi**ᵀΦ(𝐱), 1/β) (**wi** là hàng i của 𝐖). Từ đó, ta sẽ có joint distribution, của T1,..TK, tức distribution của random vector 𝐓 như sau:
>
>
>
> f(𝐭|𝐖, 𝐗, β) = f(t1, t2,..tK|𝐖, 𝐗, β)
>
>
>
> nhờ tính độc lập của T1,...TK ta có thể tách joint pdf thành tích marginal pdf (chú ý, chúng độc lập, nhưng không identically distributed, vì khác mean)
>
>
>
> = Πi=1:K f(ti|𝐖, 𝐗, β)
>
>
>
> = Πi=1:K N(ti|**wi**, **xi**, β) (thay kí hiệu N, vì như đã nói, ta assume Ti \~ normal(y(**wi**, 𝐱) = **wi**ᵀΦ(**xi**), 1/β)
>
>
>
> = Πi=1:K \[1/√2π(1/β)\] exp\[-(ti - **wi**ᵀΦ(**xi**))²/2(1/β)\]
>
>
>
> = Πi=1:K \[2π(1/β)\]^(-1/2) exp\[-β(ti - **wi**ᵀΦ(**xi**))²/2\]
>
>
>
> = \[2π(1/β)\]^(-K/2) Πi=1:K {exp\[-β(ti - **wi**ᵀΦ(**xi**))²/2\] }
>
>
>
> = \[2π(1/β)\]^(-K/2) exp{Σi=1:K \[-β(ti - **wi**ᵀΦ(**xi**))²/2\]}
>
>
>
> = \[2π(1/β)\]^(-K/2) exp{Σi=1:K \[-β(ti - **wi**ᵀΦ(**xi**))²/2\]}
>
>
>
> = \[1/(2π)^K/2\] \[1/ |(1/β)𝐈|^1/2\] exp{-(1/2)(ti - **wi**ᵀΦ(**xi**))ᵀ \[(1/β)𝐈\]⁻¹ (ti - **wi**ᵀΦ(**xi**)}
>
>
>
> và đây chính là pdf của 𝐓 \~ N(𝐖ᵀΦ(𝐱), (1/β)𝐈) → 3.32
>
>
>
> Như vậy, tương đương với scalar t case, trong đó ta assume T \~ normal(𝐰ᵀΦ(𝐱), 1/β) thì ở vector 𝐭 case ta sẽ assume 𝐓 \~ N(𝐖ᵀΦ(𝐱), (1/β)𝐈)
>
>
>
> Rồi, như vậy bước tiếp theo, trong scalar case, với việc ta có các observation (𝐱i, ti), nhờ ánh sáng của Casella, mình hiểu, đây là một random sample iid T1, T2,....TN độc lập, và có chung distribution Ti \~ normal(𝐰ᵀΦ(**xi**), 1/β). Nên joint distribution của chúng sẽ là f(t1,t2,...tN|𝐰, 𝐱1, 𝐱2...𝐱N) = Πi=1:N N(𝐱i, 𝐰ᵀΦ(𝐱i), và từ đó xét hàm likelihood.
>
>
>
> Thì ở đây cũng vậy, ta phải hiểu rằng, N cặp giá trị quan sát được (𝐭1, 𝐱1), (𝐭2, 𝐱2), ...(𝐭N, 𝐱N) cũng sẽ cho ta một random sample iid 𝐓1, 𝐓2,...𝐓N, với 𝐓i \~ N(𝐖ᵀΦ(𝐱i), (1/β)𝐈). Để rồi joint pdf của chúng sẽ là:
>
>
>
> f(𝐓1,....𝐓N|𝐖, 𝐱1, 𝐱2...𝐱N, β) = Πi=1:N N(𝐓i|𝐖ᵀΦ(𝐱i), (1/β)𝐈)
>
>
>
> Và khi đã có joint pdf của T1,...TN, ta mới nói đến likelihood (vì ta sẽ lại theo cách tiếp cận phổ biến - maximum likelihood estimation):
>
>
>
> Ôn lại chút, theo định nghĩa của hàm likelihood trong bối cảnh thống kê đã học trong Casella: khi ta có random sample X1, X2,...Xn iid \~ f(xi|θ), có observation x1,x2,...xn thì hàm likelihood là hàm của θ, kí hiệu L(θ|x1,x2,..xn) hay L(θ|𝐱) sẽ mang ý nghĩa là độ hợp lí của θ giúp giải thích cho giá trị quan sát được x1,x2,...xn của X1,X2...Xn, và người ta định nghĩa giá trị hàm này = f(x1,x2,...xn|θ) hay f(𝐱|θ).
>
>
>
> Do đó, quay lại đây, likelihood của 𝐖, β là: L(𝐖, β|𝐓1,...𝐓N) = f(𝐓1, 𝐓2...𝐓N|𝐖, β, 𝐱1,...𝐱N)
>
>
>
> = Πi=1:N N(𝐓i|𝐖ᵀΦ(𝐱i), (1/β)𝐈)
>
>
>
> Rồi, trước khi ráp công thức pdf của Ti vô, ta lại chuẩn bị sẵn ln likelihood
>
>
>
> ln L(𝐖, β|𝐓1,...𝐓N) = ln {Πi=1:N N(𝐓i|𝐖ᵀΦ(𝐱i), (1/β)𝐈)}
>
>
>
> = Σi=1:N { ln N(𝐓i|𝐖ᵀΦ(𝐱i), (1/β)𝐈) }
>
>
>
> Thay pdf N(𝐓i|𝐖ᵀΦ(𝐱i), (1/β)𝐈) = \[1/(2π)^(K/2)\] \[1/|**Σ**|^(1/2)\] exp{-(1/2)\[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ **Σ**inv \[𝐭i - 𝐖ᵀΦ(𝐱i)\] với **Σ** = (1/β)𝐈
>
>
>
> = Σi=1:N { ln { \[1/(2π)^(K/2)\] \[1/|**Σ**|^(1/2)\] exp{-(1/2)\[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ **Σ**inv \[𝐭i - 𝐖ᵀΦ(𝐱i)\] }}}
>
>
>
> = Σi=1:N { ln \[1/(2π)^(K/2)\] + ln \[1/|**Σ**|^(1/2)\] + ln exp{-(1/2)\[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ **Σ**inv \[𝐭i - 𝐖ᵀΦ(𝐱i)\] }}
>
>
>
> = Σi=1:N { (K/2) ln \[1/(2π)\] + (1/2) ln \[1/|**Σ**|\] + {-(1/2)\[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ **Σ**inv \[𝐭i - 𝐖ᵀΦ(𝐱i)\] }}
>
>
>
> = Σi=1:N { (K/2) ln \[1/(2π)\] } + (N/2) ln \[1/||**Σ**||\] + Σi=1:N{-(1/2)\[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ **Σ**inv \[𝐭i - 𝐖ᵀΦ(𝐱i)\] }
>
>
>
> = (NK/2) ln \[1/(2π)\] + (N/2) ln \[1/|**Σ**|\] + Σi=1:N{-(1/2)\[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ **Σ**inv \[𝐭i - 𝐖ᵀΦ(𝐱i)\] }
>
>
>
> **Σ** = (1/β) 𝐈 = β⁻¹ 𝐈 → del(**Σ**) = det (β⁻¹ 𝐈). Và dùng tính chất của định thức đã học trong MIT 18.06, thì giả sử có matrix A, và scale một hàng của A bởi α, để được B, thì det B = α det A. Và từ đó ta có thể thấy det (β⁻¹ 𝐈) = (β⁻¹)^K × det I = (β⁻¹)^K = 1/β^K
>
>
>
> .. = (NK/2) ln \[1/(2π)\] + (N/2) ln \[1/β^K\] -(1/2) Σi=1:N{ \[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ (β⁻¹ 𝐈)⁻¹ \[𝐭i - 𝐖ᵀΦ(𝐱i)\] }
>
>
>
> = (NK/2) ln \[1/(2π)\] + (NK/2) ln β -(1/2) Σi=1:N{ \[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ β 𝐈inv \[𝐭i - 𝐖ᵀΦ(𝐱i)\] }
>
>
>
> = (NK/2) ln \[β/(2π)\] -(β/2) Σi=1:N{ \[𝐭i - 𝐖ᵀΦ(𝐱i)\]ᵀ\[𝐭i - 𝐖ᵀΦ(𝐱i)\] }
>
>
>
> = (NK/2) ln \[β/(2π)\] -(β/2) Σi=1:N{ ||𝐭i - 𝐖ᵀΦ(𝐱i)||²}
>
>
>
> Đây chính là 3.33

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **99/100** · ✓ Move on</summary>

Bài giải thích của bạn cực kỳ chi tiết và chính xác, đặc biệt là các bước suy luận toán học để đi đến công thức (3.32) và (3.33) đều rất rõ ràng và dễ hiểu. Độ sâu phân tích này thể hiện sự nắm vững kiến thức đáng kinh ngạc, rất tốt!

</details>

**🔗 See also:** [Phân phối Gaussian](./230_gaussian_distribution.md#node-arii2cl)

<br>

<a id="node-n01dmjr"></a>

## Maximum Likelihood Regression Solution

<p align="center"><kbd><img src="assets/ettqsr41g9f.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, như vậy với ln likelihood, ta sẽ lại giải bài toán tìm 𝐖, **β** maximize cái ln likelihood này, để có được ML Estimator của 𝐖.
>
>
>
> maximize (over 𝐖, β) {(NK/2) ln \[β/(2π)\] -(β/2) Σi=1:N{ ||𝐭i - 𝐖ᵀΦ(𝐱i)||²} }
>
>
>
> và như đã nói trước đây, ta có thể giải theo biến tối ưu 𝐖 trước, khi đó ta coi β như constant nên ta sẽ chuyển thành bài toán tương đương bằng cách bỏ đi constant
>
>
>
> maximize (over 𝐖) { -Σi=1:N { ||𝐭i - 𝐖ᵀΦ(𝐱i)||²} }
>
>
>
> equivalent
>
>
>
> minimize (over 𝐖) { Σi=1:N { ||𝐭i - 𝐖ᵀΦ(𝐱i)||²} }
>
>
>
> Xét cái objective: Σi=1:N { ||𝐭i - 𝐖ᵀΦ(𝐱i)||² } m thử xem có thể thể hiện gọn hơn ko: Ta thấy nó có dạng tổng các scalar - mỗi scalar là square norm của một vector (𝐭i - 𝐖ᵀΦ(𝐱i)). Và tổng các scalar ta sẽ nghĩ đến trace. Nếu ta có AᵀA thì đường chéo của nó chính là chứa các dot product của row i của Aᵀ với column i của A, cũng là giữa column i của A với column i của A, tức ||column i của A||².
>
>
>
> Vậy ta sẽ nghĩ đến matrix nào đó mà các cột là 𝐭i - 𝐖ᵀΦ(𝐱i). gọi nó là matrix 𝐌 đi, thì objective chính là trace(𝐌ᵀ𝐌).
>
>
>
> Vậy thì thì nếu đặt các 𝐭i thành các **hàng** của matrix 𝐓, thì 𝐓ᵀ là matrix có các cột là 𝐭i 𝐖
>
>
>
> Và Φ(𝐱i) thành các **hàng** của matrix **Φ** (đây chính là design matrix bữa trước) thì **Φ**ᵀ là matrix có các cột là Φ(𝐱i) và matrix có các cột là 𝐖ᵀΦ(𝐱1), 𝐖ᵀΦ(𝐱2)... chính là 𝐖ᵀ **Φ**ᵀ vì theo MIᵀ 1806, 𝐖ᵀ **Φ**ᵀ sẽ có cột i là 𝐖ᵀ \[cột i của **Φ**ᵀ\].
>
>
>
> Vậy matrix có các cột là 𝐭i - 𝐖ᵀΦ(𝐱i) chính là matrix 𝐓ᵀ - 𝐖ᵀ **Φ**ᵀ, tức (𝐓 - **ΦW**)ᵀ. Và như vậy 𝐌 = (𝐓 - **ΦW**)ᵀ. Và objective = tr(𝐌ᵀ𝐌) = tr((𝐓 - **ΦW**)(𝐓 - **ΦW**)ᵀ)
>
>
>
> và theo tính chất cycling của trace: tr(AB) = tr(BA) thì ta có objective cũng là tr((𝐓 - **ΦW**)ᵀ(𝐓 - **ΦW**))
>
>
>
> Tới đây, dùng điều kiện tối ưu cần bậc nhất, nên chuẩn bị gradient (d/d𝐖 tr((𝐓 - **ΦW**)ᵀ(𝐓 - **ΦW**))
>
>
>
> tr((𝐓 - **ΦW**)ᵀ(𝐓 - **ΦW**) = tr((𝐓ᵀ - 𝐖ᵀ**Φ**ᵀ)(𝐓 - **ΦW**) = tr((𝐓ᵀ𝐓 - 𝐖ᵀ**Φ**ᵀ𝐓 - 𝐓ᵀ**ΦW** + 𝐖ᵀ**Φ**ᵀ**ΦW**)
>
>
>
> = tr(𝐓ᵀ𝐓 - 2𝐓ᵀ**ΦW** + 𝐖ᵀ**Φ**ᵀ**ΦW**)
>
>
>
> = tr(𝐓ᵀ**T)** - 2tr(𝐓ᵀ**ΦW**) + tr(𝐖ᵀ**Φ**ᵀ**ΦW**) (dùng tính liearity của trace)
>
>
>
> ⇨ d/d𝐖 objective = -2d/d𝐖 \[tr(𝐓ᵀ**ΦW**)\] + d/d𝐖 tr(𝐖ᵀ**Φ**ᵀ**ΦW**)
>
>
>
> Tới đây dùng công thức đạo hàm hàm trace:
>
>
>
> Xét X, A là matrix và hàm matrix → scalar f(X) = tr(AX). df = tr(AX + AdX) - tr(AX) = tr(AdX). Và cái này, chính là Aᵀ . dX, tức inner product của matrix Aᵀ và matrix dX. Vậy ta có df = Aᵀ . dX, là một linear operator act on dX, theo định nghĩa của đạo hàm f'(X) dX cũng là một linear operator act on dX, từ đó ta suy ra nên d/dX f(X) = Aᵀ
>
>
>
> Áp dụng vào đây ta sẽ có d/d𝐖 \[tr(𝐓ᵀ**ΦW**)\] = (𝐓ᵀ**Φ**)ᵀ = **Φ**ᵀ𝐓.
>
>
>
> Còn d/d𝐖 tr(𝐖ᵀ**Φ**ᵀ**ΦW**) thì dài dòng hơn, tí ta sẽ quay lại, = 2**Φ**ᵀ**ΦW**
>
>
>
> Vậy gradient = -2**Φ**ᵀ𝐓 + 2**Φ**ᵀ**ΦW**
>
>
>
> gradient = 0 ⇔ -2**Φ**ᵀ𝐓 + 2**Φ**ᵀ**ΦW** = 0 ⇔ **Φ**ᵀ**ΦW** = **Φ**ᵀ𝐓
>
>
>
> ⇔ 𝐖ML = \[**Φ**ᵀ**Φ**\]⁻¹**Φ**ᵀ𝐓 → 3.34
>
>
>
>  và như vậy các cột của 𝐖, tức 𝐰i sẽ chính là \[**Φ**ᵀ**Φ**\]⁻¹**Φ**ᵀ𝐭i
>
>
>
> với việc bữa trước mình đã nói về pseudo matrix, \[**Φ**ᵀ**Φ**\]⁻¹**Φ**ᵀ, tức left inverse của **Φ**, thì ta hiểu vì sao kết quả 3.35 ghi là 𝐰i = **Φ**^(+) 𝐭i
>
>
>
> Và như vậy nhận định quan trọng là: Đại khái là, hóa ra, việc ta chuyển thành bài toán predict vector 𝐭 gồm các t1,...tK độc lập thì hóa ra solution (ML estimator) chỉ là: Thay vì kết quả ta có vector 𝐰ML = **Φ**^(+) 𝐭, thì nay ta có K vector 𝐰ML_i = **Φ**^(+) 𝐭i. Tức là, chúng hoàn toàn tách biệt (decouple), chứ không dính với nhau, dẫn tới giống như là ta giải nhiều bài toán predict t1, t2,..riêng với input là chỉ dùng chung Φ(𝐱) và với các vector wi tương ứng.
>
>
>
> Và như vậ ta chỉ cần chuẩn bị matrix **Φ**^(+) để rồi lần lượt nhân với 𝐭i để có 𝐰ML_i.

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **100/100** · ✓ Move on</summary>

Ghi chú của bạn cung cấp một cách suy luận cực kỳ kỹ lưỡng và chính xác về ước lượng hợp lý tối đa cho W, hoàn toàn khớp với các phương trình (3.34) và (3.35) đã cho. Bạn đã trình bày rất rõ ràng khái niệm "decoupling" và cách ma trận giả nghịch đảo được dùng chung, cho thấy sự hiểu biết sâu sắc. Để hoàn thiện tuyệt đối, bạn có thể cân nhắc trình bày chi tiết hơn bước đạo hàm cho tr(W^T Φ^T ΦW).

</details>

<br>

<a id="node-ecayn6k"></a>

### Maximum Likelihood for Gaussian Mean

<p align="center"><kbd><img src="assets/tbjqombfp8n.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi đoạn cuối cùng thì đại khái ông nói rằng là hồi nãy giờ là mình giải cái đặt bài toán với việc giả định rằng các cái vector T nó tuân theo cái phân phối đa biến có cái ma trận hiệp phương sai có dạng là một cái ma trận identity nhân với một chia beta. Thì bây giờ ông nói rằng mình có thể mở rộng nó ra với mô hình đa biến có cái ma trận hiệp phương sai bất kỳ. Và kết quả sẽ cũng cho thấy rằng bài toán được trở thành ra là giống như việc giải nhiều bài toán dự đoán độc lập. Tức là nó tách ra thành những bài toán dự đoán một con số độc lập thay vì nó dính với nhau. Và cái lý do là bởi vì trong cái phần hai mình đã thấy rằng là cái nghiệm mà maximum likelihood vốn dĩ là nó có một cái tính chất là nó chỉ nó không có phụ thuộc vào cái covariance mà trận hiệp phương sai. Cho nên là dù ma trận hiệp phương sai nó là cái gì á thì kết quả nó cũng chỉ tương tự như ở trên. Có nghĩa là thay vì mình tức là thay vì mình dự đoán một cái T thì bây giờ mình dự đoán nhiều T nhưng mà về cơ bản là nó chỉ là giống như giải nhiều bài toán dự đoán một T cùng lúc thôi.

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **95/100** · ✓ Move on</summary>

Bạn đã tóm tắt rất chính xác các điểm chính và giải thích rõ ràng lý do đằng sau việc phân tách bài toán. Để tăng cường độ chính xác, bạn có thể cân nhắc đề cập trực tiếp đến các tham số cụ thể như 'W' được nhắc đến trong văn bản.

</details>

<br>

