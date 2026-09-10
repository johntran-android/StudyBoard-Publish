# 3.2.0 The Bias-Variance Decomposition

📊 **Progress:** `8` Notes | `16` Screenshots | `7` AI Reviews

---
<a id="node-0nolzxg"></a>

<p align="center"><kbd><img src="assets/y54wc6qlvqb.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại ý là vầy: Mấy phần trước cũng như liên hệ với bên Casella mình đã thấy nhược điểm của MLE khi data ít, nó sẽ đại khái là cho ra những kết quả cực đoan, và trong bối cảnh machine learning chính là thứ ta gọi là overfit - khi ta dùng model phức tạp với ít data.
>
>
>
> Rồi ông có nhắc đến việc ta thảo luận về linear model - có dạng cũng như số basis function không đổi. Ý này là sao? → Tức là ta đang nói về linear model có dạng y(𝐱, 𝐰) = 𝐰ᵀΦ(𝐱) với w = (w0, w1, ...wM-1)ᵀ và Φ(𝐱) = (1, Φ1(𝐱), ...ΦM-1(𝐱))ᵀ, đương nhiêi với M là giá trị cố định nào đó, thì ta có một giá trị cố định các tham số cũng như các basis function. Ý muốn và ta nhớ, đây vẫn là hàm tuyến tính đối với 𝐰 dù cho nhờ hàm basis, y trở thành hàm phi tuyến đối với 𝐱, và do đó vẫn gọi là linear model là vậy.
>
>
>
> Thế thì tại sao lại nhắc đến số basis function? ⇨ Mình hiểu rằng, số basis function sẽ quyết định độ phức tạp của mô hình, vì số basis function càng lớn, và basis function lại mang ý nghĩa là tạo các non-linear feature, những feature mới tạo thành bằng cách kết hợp phi tuyến các feature gốc, sẽ giúp mô hình tăng độ phức tạp, từ đó có thể đủ năng lực để capture các pattern của data.
>
>
>
> Như vậy quay lại vấn đề mle approach, nếu dùng complex model, và trong trường hợp ít data, sẽ dẫn đến overfit. Thì ta có thể nghĩ đến giảm số basis function lại để giảm độ complex của mô hình lại. Nhưng điều này lại có thể dẫn đến là, mô hình không đủ complex để capture các pattern trong data (mà mình biết gọi là underfit)
>
>
>
> Từ đó, để giải quyết, ta mới có công cụ: regularization term, add thêm vào error function một regularization term giúp tạo thêm một objective nữa: khống chế độ lớn của parameter bên cạnh main objective là giảm error function. Và sự tương quan giữa mức độ quan trọng của hai objective sẽ được kiểm soát bởi một hệ số, ví dụ λ (gọi là regularization hyperparameter). Với regularization, ta có thể dùng complex model, để train một bài toán ít data mà không sợ overfit.
>
>
>
> Nhưng cách này lại phát sinh vấn đề: chọn giá trị của regularization coefficient. Như vậy có thể thấy là, nó vẫn chưa giải quyết hoàn toán vấn đề đau đầu.
>
>
>
> Và nói thêm, nếu ta nghĩ đến việc training mô hình cùng lúc với cả weight và λ thì sẽ dẫn đến λ = 0. Vì sao? 
>
>
>
> Đơn giản là vì λ vốn có ràng buộc ≥ 0, và để minimize E_D(𝐰) + λE_W(𝐰) với E_W(𝐰) ≥ 0 thì đây là hàm tuyến tính theo λ, E_D(𝐰) + λE_W(𝐰), có dạng a λ + b, và với λ ≥ 0, thì và a = E_W(𝐰) cũng > 0 thì hàm này cực tiểu khi λ = biên của \[0, ∞), tức λ = 0.

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Bài ghi chú thể hiện sự hiểu biết sâu sắc về các khái niệm, giải thích chính xác nội dung văn bản và cung cấp những phân tích bổ sung tuyệt vời, đặc biệt là lý do tại sao λ=0 khi tối ưu hóa đồng thời. Đây là một bài phân tích rất chi tiết và chính xác.

**🔗 See also:** [Iterative Estimation of Alpha](./352_maximizing_the_evidence_function.md#node-vstyyq2)

<br>

<a id="node-897hybe"></a>

## Bias-Variance Trade-off Overview

<p align="center"><kbd><img src="assets/jcvn4w23vog.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đại khái là, gs nói vấn đề overfit là nhược điểm của maximum likelihood, chứ nếu làm **theo Bayesian approach, thì ta sẽ không bị vấn đề này** (đã nói nhiều về cái này, cũng như trong Casella cũng đã nói, nguyên nhân ngắn gọn là vì Bayesian approach, ta cói paramter là random variable, và từ đó đặt ra prior distribution của parameter π(θ) và chính cái này giúp cho khi ta đi xây dựng posterior π(𝐱|θ) cũng như đi maximum posterior cũng chính là maximum L(θ|𝐱) π(θ), thì prior distribution sẽ giúp cho kết quả không bị extreme khi data ít như cách làm của mle (chỉ maximum L(θ|𝐱)).
>
>
>
>  Cho nên trong chapter này ta sẽ bàn sâu hơn về Bayesian approach. Tuy nhiên trước đó, gs sẽ dẫn dắt ta về một **góc nhìn về vấn đề overfit trong phạm vi vẫn thuộc trường phái cổ điển**: **Bias Variance trade-off**. Và cái này sẽ mở rộng cả các phạm vi khác chứ không riêng gì bài toán linear basis function model

<br>

<a id="node-a09r921"></a>

### Optimal Prediction with Squared Loss

<p align="center"><kbd><img src="assets/80hlynvklfv.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đoạn này đại khái là, nhắc lại một điểm đã nói trước đây: rằng, giả sử ta đã có predictive distribution, tức f(t|𝐱). Thì dự đoán tối ưu cho giá trị của T sẽ là gì.
>
>
>
> Mình sẽ ôn lại nhanh chỗ này:
>
>
>
> Bài toán này nếu nói rõ ra thì là thế này: Nó giống y như cái vụ đưa ra point estimator (của θ) theo cách tiếp cận Bayesian (Bayes estimator) vậy.
>
>
>
> Đầu đuôi câu chuyện là: Với Bayesian, ta coi θ như random variable. Mà đã là random variable, thì nó có probability distribution. Thế thì, marginal distribution của θ, mà với θ, thì người ta gọi là prior distribution π(θ), là thứ mà ta sẽ chọn, dựa vào kinh nghiệm nào đó, nhằm phản ánh một hiểu biết nào đó của ta về θ. Để rồi dùng Bayes rule ta xây dựng π(θ|𝐱) = f(𝐱|θ) π(θ) / f(𝐱), gọi là posterior distribution. Thế thì, vấn đề là, đây vẫn là một distribution, trong khi có thể ta cần đưa ra một point estimation cho θ thì sao? mà theo định nghĩa, point estimator là một hàm số của sample W(𝐗), nên yêu cầu là ta cần rút ra một hàm số từ cái distribution này.
>
>
>
> Và đây chính là lúc ta cần viện tới công cụ thuộc lĩnh vực decision theory: Giúp đưa ra quyết định trong điều kiện không chắc chắn (making decision under uncertainty): Tính không chắc chắn phản ánh bởi một probability distribution π(θ|𝐱), và ra quyết định ở đây chính là đưa ra một ước lượng điểm W(𝐗) cho θ từ đó.
>
>
>
> Và trong decision theory, ta sẽ cần lựa chọn loss function: Là hàm số của estimator: L(W(𝐗), θ), phản ánh một cách thức nào đó mà ta trừng phạt các sai sót. Phổ biến được dùng là square error loss (W(𝐗) - θ)². và absolute error loss |W(𝐗) - θ|.
>
>
>
> Cần hiểu điều quan trọng này: Giả sử với θ fixed, thì L(W(𝐱), θ) chỉ phản ánh error của W(𝐱) với một giá trị 𝐱 cụ thể. Cho nên ta sẽ đi tính trung bình error trên mọi possible value của 𝐗. Hoặc nhìn theo cách khác, với θ fixed nào đó, thì L(W(𝐗), θ) vẫn là môt random variable có được bằng cách áp hàm L(W(𝐮), θ) lên random variable 𝐗. Và vì vậy, ta có quyền nói về kì vọng / mean / expected value của nó. E\[L(W(𝐗), θ)\], và vì distribution của L(W(𝐗), θ) sẽ phụ thuộc θ do bản chất là 𝐗 \~ f(𝐱|θ), nên ta ghi là E\_θ\[L(W(𝐗), θ)\], để thể hiện, đây sẽ là hàm số phụ thuộc θ.
>
>
>
> Và cái này chính là định nghĩa của risk function: R(W(𝐗), θ) = E\_θ\[L(W(𝐗), θ)\], nếu dùng LOTUS, ta sẽ dễ hiểu nó là: ∫L(W(𝐱), θ) f(𝐱|θ) d𝐱.
>
>
>
> Tới đây, nếu ta đi thêm một bước để bước chân qua Bayesian approach, coi θ như random variable, thì cái risk function trên vẫn sẽ là một random variable (có được bởi áp hàm g(θ) = E\_θ\[L(W(𝐗), θ)\], lên random variable θ). Để rồi nếu ta lấy expected value của nó, ta sẽ có một con số cố định cuối cùng, không còn phụ thuộc ai. Đó chính là Bayes risk:
>
>
>
> Bayes risk = E{E\_θ\[L(W(𝐗), θ)\]} = ∫ E\_θ\[L(W(𝐗), θ)\] π(θ) dθ
>
>
>
> Nếu biến đổi tí xíu, dùng Bayes rule: .. = ∫ \[∫ L(W(𝐱), θ)\] f(𝐱|θ) d𝐱 π(θ)\] dθ
>
>
>
> = ∫ \[∫ L(W(𝐱), θ)\] f(𝐱|θ)π(θ) d𝐱\] dθ
>
>
>
> = ∫ \[∫ L(W(𝐱), θ)\] π(θ|𝐱)f(𝐱) d𝐱\] dθ (thay f(𝐱|θ)π(θ) bởi π(θ|𝐱)f(𝐱))
>
>
>
> = ∫ \[∫ L(W(𝐱), θ)\] π(θ|𝐱) dθ\] f(𝐱)d𝐱 (tính tích phân theo θ trước)
>
>
>
> thì lúc này, ∫ L(W(𝐱), θ)\] π(θ|𝐱) dθ chính là E\[L(W(𝐱), θ)\] với θ \~ π(θ|𝐱), tức là, với giá trị nào đó của 𝐗 = 𝐱, ta có θ \~ posterior π(𝐱|θ) và tính kì vọng của L(W(𝐱), θ) với θ có distribution này. Thì cái này gọi là **posterior expected loss**.
>
>
>
> Rồi, với tất cả các định nghĩa trên, giờ ta mới đi quay lại nói về việc tìm point estimator của θ sao cho tối ưu.
>
>
>
> Nói bài toán Bayesian trước: θ là random variable, thì ta sẽ đi tìm W(𝐗) minimize Bayes risk, và vì Bayes risk là tích phân over mọi 𝐱 của posterior expected risk, nên bài toán này tương đương đi minimize posterior expected risk:
>
>
>
> minimize_W ∫ L(W(𝐱), θ)\] π(θ|𝐱) dθ
>
>
>
> ∫ L(W(𝐱), θ)\] π(θ|𝐱) dθ = ∫ \[W(𝐱) - θ\]² π(θ|𝐱) dθ
>
>
>
>  ∂/∂W \[∫ \[W(𝐱) - θ\]² π(θ|𝐱) dθ\] = ∫ { ∂/∂W \[W(𝐱) - θ\]² } π(θ|𝐱) dθ
>
> = ∫ 2 \[W(𝐱) - θ\] π(θ|𝐱) dθ
>
>
>
> = 2 ∫\[W(𝐱) - θ\] π(θ|𝐱) dθ
>
>
>
> First order condition: 2 ∫\[W(𝐱) - θ\] π(θ|𝐱) dθ = 0
>
>
>
> ⇔ ∫\[W(𝐱)π(θ|𝐱) dθ - ∫θπ(θ|𝐱) dθ = 0
>
>
>
> ⇔ ∫W(𝐱)π(θ|𝐱) dθ = ∫θπ(θ|𝐱) dθ
>
>
>
> ⇔ W(𝐱) ∫π(θ|𝐱) dθ = E\[θ\] (θ \~ π(θ|𝐱))
>
>
>
> ⇔ W(𝐱) = E\[θ|𝐱\] (θ \~ π(θ|𝐱))
>
>
>
> → Khi 𝐗 = 𝐱, và θ \~ f(θ|𝐱) thì W(𝐱) khiến minimize posterior expected loss với chính là mean của posterior.
>
> \
> Vậy nên W(𝐗) = E\[θ|𝐗\] chính là point estimator của θ với θ \~ f(θ|𝐗) giúp minimize Bayes risk với square error loss.
>
>
>
> ---
>
>
>
> Nếu θ là fixed unknown, tức theo trường phái cổ điển, thì ta sẽ giải bài toán minimize risk function:
>
>
>
> minimize_W E\_θ\[L(W(𝐗), θ)\] = ∫ L(W(𝐱), θ) f(𝐱|θ) d𝐱, = (nếu dùng square error loss) = ∫ \[W(𝐱) - θ\]² f(𝐱|θ) d𝐱
>
>
>
> Và cái này, ∫ \[W(𝐱) - θ\]² f(𝐱|θ) d𝐱, tức E\_θ\[(W(𝐗) - θ)²\], ta nhớ chính là định nghĩa của MSE, để rồi ta sẽ phân tích nó thành Bias(W(𝐗)² + Var(W(𝐗). Từ đó đi tìm W(𝐗) giúp giảm cái này, dẫn tới các cách tiếp cận như xét trong các unbiased estiamtor, xem cái nào có Variance nhỏ nhất, và variance thế nào thì nhỏ nhất lại dẫn đến công cụ là Cramer Rao Lower Bound,...
>
>
>
> ---
>
>
>
> Với chừng đó ôn tập, mình quay lại cái bài toán trong sách này, là đưa ra predict tối ưu của T khi có T \~ f(t|𝐱)
>
>
>
> Thì cái này y chang việc có π(θ|𝐱), và cần estimate tối ưu cho θ thôi:
>
>
>
> Ta cũng đi giải bài toán: minimize_h(𝐱) Risk function = ∫ L(h(𝐱), t) f(t|𝐱) dt = ∫(h(𝐱) - t)² f(t|𝐱) dt
>
>
>
>  ∂/∂y \[∫(h(𝐱) - t)² f(t|𝐱) dt\] = ∫ \[∂/∂y \[(h(𝐱) - t)²\] f(t|𝐱) dt
>
>
>
> = ∫ 2(h(𝐱) - t) f(t|𝐱) dt
>
>
>
> = 2∫ (h(𝐱) - t) f(t|𝐱) dt
>
>
>
> Fisrt order optimality condition: 2∫ (h(𝐱) - t) f(t|𝐱) dt = 0
>
>
>
> ⇔ ∫(h(𝐱) - t) f(t|𝐱) dt = 0
>
>
>
> ⇔ ∫h(𝐱)f(t|𝐱) dt - ∫t f(t|𝐱) dt = 0
>
>
>
> ⇔ h(𝐱) ∫f(t|𝐱) dt = E\[T|𝐱\]
>
>
>
> ⇔ h(𝐱) = E\[T|𝐱\]
>
>
>
> Như vậy, optimal point estimator cho T khi T \~ f(t|𝐱) chính là posterior mean: E\[T|𝐱\] → Đây chính giúp ta hoàn toàn hiểu 3.36.

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Bài giải thích cực kỳ chi tiết và sâu sắc, vượt xa nội dung ảnh để cung cấp một nền tảng vững chắc về lý thuyết quyết định và ước lượng Bayes. Mặc dù rất toàn diện, có thể tóm tắt các phần ôn tập một cách ngắn gọn hơn nếu mục tiêu là chỉ tập trung vào giải thích công thức 3.36.

<br>

<a id="node-s3i1j2i"></a>

#### Expected Squared Loss Decomposition

<p align="center"><kbd><img src="assets/87zodxs4od8.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, tiếp theo chỗ này dễ lú, nên cần giải thích rõ khi ông nói ta cần phải phân biệt có hai loại squared loss, trong rất giống nhau, một cái là trong bối cảnh decision theory và còn lại là trong bài toán MLE. Là sao ta?
>
>
>
> Hiểu đại khái vầy: Nói đến decision theory, là vì, như note trước ta vừa mới làm: Rằng, trong bài toán này, khi ta làm theo probabilistic perspective, coi T như random variable, có predictive distribution f(t|𝐱) thì câu hỏi đặt ra là, khi đã có f(t|𝐱) rồi, thì nên lấy giá trị bao nhiêu để dự đoán (vì yêu cầu của bài toán cuối cùng vẫn là cho 𝐱, dự đoán t, chứ không phải là tính ra f(t|𝐱)). Và đối mặt với câu hỏi này, ta cần đến decision theory giúp đỡ, nó sẽ cho ta cách làm như sau: Ta sẽ chọn loss function: L(T, h(𝐱)), ví dụ square error loss, = (T - h(𝐱))², đây sẽ là random variable (hàm của T). Và tính risk function, mang ý nghĩa là average của loss over all T \~ f(t|𝐱):
>
>
>
> Risk function = E\[T - h(𝐱)\] = ∫(t - h(𝐱))² f(t|𝐱)dt
>
>
>
> Và đi tìm h để mininimize cái risk function thì kết quả là h(𝐱) = E\[T|𝐱\].
>
>
>
> Đó là nói về square loss function trong decision theory, nói ngắn gọn, nó giúp ta đưa ra optimal point estimation của T với T \~ f(t|𝐱).
>
>
>
> Thế còn sum squared error trong MLE?
>
>
>
> Là vầy: Nói về MLE, tức là ta nói về bài toán tìm point estimation cho PARAMETER θ: tìm estimator, là hàm theo data W(𝐗, 𝐭) sao cho maximize L(θ|𝐗, 𝐭) (𝐗, 𝐭 ở đây là observed data: 𝐗 = matrix tạo bởi các vector 𝐱1, ...𝐱N và 𝐭 là vector các observed data t1, t2,...tN và có thể gọi chung là D (data) cho gọn) và θ đại diện cho tất cả parameter nói chung.
>
>
>
> Trong bài toán cụ thể ở đây, nếu ta dùng linear model dự đoán cho T \~ normal(y(𝐰,𝐱), 1/β) thì θ chính là (𝐰, β). Và bài toán để giải MLE của (w, β) sẽ là:
>
>
>
> maximize (over 𝐰, β) L(𝐰, β|𝐗,𝐭) = f(𝐭|𝐰, β, 𝐗).
>
>
>
> nhờ tính independent của T1,....Tn nên f(𝐭|𝐰, β, 𝐗) = Πi=1:N normal(𝐭i|𝐰, β, 𝐱i) và dùng hàm log là hàm monotone để chuyển thành bài toán tối ưu tương đương:
>
>
>
> maximize (over 𝐰, β) ln L(𝐰, β|𝐗,𝐭) = ln {Πi=1:N normal(𝐭i|y(𝐰, 𝐱i),β)}
>
>
>
> Xét hàm objective, thay pdf normal vào:
>
>
>
> ln {Πi=1:N normal(𝐭i|𝐰, β, 𝐱i) = ln {Πi=1:N \[1/√2π(1/β) exp{-(ti - y(𝐰,𝐱i))²/2(1/β)}\]}
>
>
>
> = ln {Πi=1:N \[1/√2π(1/β)\]} + ln {Πi=1:N exp{-(ti - y(𝐰,𝐱i))²/2(1/β)}\]}
>
>
>
> Tới đây ta có thể giải theo 𝐰 trước, tức là coi β như constant, từ đó chuyển thành bài toán tương đương tiếp theo bằng cách bỏ constant:
>
>
>
> maximize (over 𝐰) ln {Πi=1:N exp{-(ti - y(𝐰,𝐱i))²/2(1/β)}\]}
>
>
>
> ⇔ maximize over 𝐰 Σi=1:N ln {exp{-(ti - y(𝐰,𝐱i))²/2(1/β)}\]}
>
>
>
> ⇔ maximize over 𝐰 Σi=1:N \[-(ti - y(𝐰,𝐱i))²/2(1/β)\]
>
>
>
> ⇔ maximize over 𝐰 Σi=1:N \[(-β/2)(ti - y(𝐰,𝐱i))²\]
>
>
>
> ⇔ maximize over 𝐰 (-β/2) Σi=1:N \[(ti - y(𝐰,𝐱i))²\]
>
>
>
> ⇔ minimize over 𝐰 (1/2) Σi=1:N \[(ti - y(𝐰,𝐱i))²\]
>
>
>
> Và đây chính là bài toán mininize hàm sum square error function. Giải thích cho ý gs nói sum-squares error function xuất hiện (arose) in MLE.
>
>
>
> Nhưng cái 3.37, lại xuất phát từ 1.5.5:
>
>
>
> E\[L\] = ∫∫L(t, y(𝐱)) f(t,𝐱) d𝐱 dt
>
>
>
> mà để hiểu công thức này thì phải thấy cả T và 𝐗 đều là random variable:
>
>
>
> Và Loss = L(t, y(𝐱)) = \[t - y(𝐱)\]², thì L(𝐓, y(𝐗)) cũng là random variable, do đó có thể lấy kì vọng, và theo LOTUS:
>
>
>
> E\[L\] = ∫∫L(t, y(𝐱)) f(t,𝐱) d𝐱 dt
>
>
>
> = ∫∫(t - y(𝐱))² f(t|𝐱)f(𝐱) d𝐱 dt (Bayes rule: f(t,𝐱) = f(t|𝐱)f(𝐱))
>
>
>
> = ∫∫(y(𝐱) - t)² f(t|𝐱)f(𝐱) d𝐱 dt
>
>
>
> cộng thêm và trừ bớt cho h(𝐱) = E\[t|𝐱\]
>
>
>
> = ∫∫(y(𝐱) - h(𝐱) + h(𝐱) - t)² f(t|𝐱)f(𝐱) d𝐱 dt
>
>
>
> = ∫∫{\[y(𝐱) - h(𝐱)\]² +2\[y(𝐱) - h(𝐱)\]\[h(𝐱) - t\] + \[h(𝐱) - t\]²} f(t|𝐱)f(𝐱) d𝐱dt
>
>
>
> = ∫∫\[y(𝐱) - h(𝐱)\]² f(t|𝐱) f(𝐱) d𝐱 dt + 2∫∫\[y(𝐱) - h(𝐱)\]\[h(𝐱) - t\]f(t|𝐱) f(𝐱) d𝐱dt + ∫∫\[h(𝐱) - t\]²} f(t|𝐱) f(𝐱) d𝐱dt
>
>
>
>  Xét term thứ 2: 2∫∫\[y(𝐱) - h(𝐱)\]\[h(𝐱) - t\]f(t|𝐱) f(𝐱) d𝐱dt
>
>
>
> Đổi chỗ d𝐱, dt, tính tích phân theo t trước (1802 đã học gặp tích phân kép∫f(x,y)dxdy, thì tính tích phân theo cái nào trước cũng được vì ở đây range đều là toàn bộ mặt phẳng)
>
>
>
> = 2∫ \[∫(y(𝐱) - h(𝐱))(h(𝐱) - t)f(t|𝐱)dt\] f(𝐱)d𝐱
>
>
>
> Và vì đang tính tích phân theo t, ta đưa (y(𝐱) - h(𝐱)) không phụ thuộc t ra:
>
>
>
> = 2(y(𝐱) - h(𝐱)) ∫ \[∫(h(𝐱) - t)f(t|𝐱)dt\] f(𝐱)d𝐱
>
>
>
> Xét ∫(h(𝐱) - t)f(t|𝐱)dt, nó chính là E\[h(𝐱) - T|𝐱\] theo linearity = E\[h(𝐱)\] - E\[T|𝐱\] = E\[T|𝐱\] - E\[T|𝐱\] = 0.
>
>
>
> Vậy term thứ 2 = 0. Ta chỉ còn term 1, 3:
>
>
>
> ∫∫\[y(𝐱) - h(𝐱)\]² f(t|𝐱) f(𝐱) d𝐱 dt + ∫∫\[h(𝐱) - t\]² f(t|𝐱) f(𝐱) d𝐱dt
>
>
>
> Và đều chuyển thành tích phân của t trước, ta sẽ thấy nó là:
>
>
>
> = ∫(y(𝐱) - h(𝐱))² \[∫f(t|𝐱)dt\] f(𝐱)d𝐱 + ∫ \[∫\[h(𝐱) - t\]² f(t|𝐱)dt\] f(𝐱)d𝐱 
>
>
>
> ∫f(t|𝐱)dt = 1 vì tính valid của pdf
>
>
>
> ∫\[h(𝐱) - t\]² f(t|𝐱)dt = E\[(h(𝐱) - T)²|𝐱\]
>
>
>
> = ∫(y(𝐱) - h(𝐱))² f(𝐱)d𝐱 + ∫ \[∫\[h(𝐱) - t\]² f(t|𝐱)dt\] f(𝐱)d𝐱 
>
>
>
> Đưa ∫ \[∫\[h(𝐱) - t\]² f(t|𝐱)dt\] f(𝐱)d𝐱 trở lại thành ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt
>
>
>
> Kết qủa ta có ∫(y(𝐱) - h(𝐱))² f(𝐱)d𝐱 + ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt → Đây chính là 3.37
>
>
>
> Dừng chút để nhận định lạ: Có nghĩa là square error xuất hiện ở 3 case khác nhau:
>
>
>
> Trong case 1: Khi có T \~ f(t|𝐱), thì h(𝐱) = E\[T|𝐱\] sẽ minimize E\[L(h(𝐱), T)\] với T\~f(𝐱|t), L(h(𝐱), T) = (h(𝐱) - T)²
>
>
>
> Trong case 2: Khi assume noise ε \~ n(0, 1/β) cũng là T \~ n(y(𝐰,𝐱), 1/β), thì 𝐰ML chính là minimizer của ln L(𝐰|𝐗,𝐭,β) cũng là minimizer của (1/2) Σi=1:N \[y(𝐰, 𝐱i) - ti\]², là sum squared error.
>
>
>
> Trong case 3: Khi ta xét Loss của bài toàn regression: L(y(𝐗), T) = \[y(𝐗) - T\]², là một random variable (hàm của random variable 𝐗 và T), và xét kì vọng của nó: E\[L\] = ∫∫ L(y(𝐱), t) f(𝐱, t) d𝐱 dt và triển khai ra ta có E\[L\] = ∫(y(𝐱) - h(𝐱))² f(𝐱)d𝐱 + ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt
>
>
>
> Điểm giống nhau của 1, và 3: Đều là trong bối cảnh decision theory, khi ta xét expected loss. Để rồi trong 1), minimize expected loss thì ta sẽ có h(𝐱) = E\[T|𝐱).
>
>
>
> Còn trong 3, ta cũng muốn (tìm y(𝐱) để minimize E\[L\] thì ta sẽ thấy bài toán sẽ ≡ mininimize ∫(y(𝐱) - h(𝐱))² f(𝐱)d𝐱 và kết quả sẽ cho solution y(𝐱) = h(𝐱)(tức = E\[T|𝐱\]), cũng chính là quay lại bài toán nếu ta có predictive distribution: f(t|𝐱) thì point estimator tối ưu cho T chính là E\[T|𝐱\].
>
>
>
> Và ý chính gs Bishop muốn nói: Đi tìm f(t|𝐱) (chính là ví dụ như khi mình tìm 𝐰ML) thì không nhất thiết ta phải dùng MLE, mà có thể dùng các các tiếp cận khác như fully Bayesian. Còn khi đã có f(t|𝐱), thì theo decision theory, point estimation tối ưu cho T khi dùng squared loss là E\[T|𝐱\]
>
>
>
> ---
>
>
>
> Tiếp tục, đoạn ghi chú màu xanh cũng là nói ý trên: Để tìm y(𝐱) minimize E\[L\] thì chỉ tương đương tìm y(𝐱) minimize term 1, vì term 2 không phụ thuộc y, và vì nó không âm nên mininimize khi y(𝐱) = h(𝐱) như nói trên.
>
>
>
> Vậy vì sao ông nói term 2 xuất phát từ noise nội tại (intrisic) và đại diện cho phần ko thể giảm được nữa, cũng là cái nhỏ nhất mà E\[L\] có thể đạt được (ý là với y\*(𝐱), tối ưu) thì chỉ có thể giúp term 1 bằng 0, và E\[L} vẫn còn term 2?
>
>
>
> Là vì: xem xét, ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt, thay h(x) = E\[T|𝐱\]:
>
>
>
> = ∫∫\[t - E\[T|𝐱\]\]² f(t,𝐱) d𝐱 dt
>
>
>
> = ∫∫\[t - E\[T|𝐱\]\]² f(t|𝐱) f(𝐱) d𝐱 dt
>
>
>
> = ∫∫\[t - E\[T|𝐱\]\]² f(t|𝐱) dt f(𝐱) d𝐱
>
>
>
> Xét riêng cụm này: ∫\[t - E\[T|𝐱\]\]² f(t|𝐱) dt, nó chính là Var\[T|𝐱\], tức Var(T) với T \~ f(T|𝐱). Và như vậy:
>
>
>
> ∫∫\[t - E\[T|𝐱\]\]² f(t|𝐱) dt f(𝐱) d𝐱 = ∫ Var\[T|𝐱\] f(𝐱) d𝐱
>
>
>
> và như vậy, nó chính là đến từ **mức biến động nội tại của data**, không phải sao? vì bản chất là T **đã có mức biến động nội tại nào đó**, chính là **thể hiện thông qua variance** của f(t|𝐱), mà trong bài toán đi tìm y(𝐱) tối ưu, ta sẽ không để can thiệp làm giảm cái phần loss do variance của T này. Ví dụ nôm na là: cho trước x, thì T có distribution n(μ, σ²), thì khi y(x, 𝐰) = μ = E\[T|𝐱) thì ta đã làm tốt nhất rồi (còn lại cái phần loss do variance của T thì chịu, không thêm làm gì khác).
>
>
>
> ---
>
>
>
> Và ở đoạn cuối cùng, mình hiểu ý gs Bishop như vầy: Xét cái term 1, là cái thứ ta có thể minimize được bằng cách tìm ra y(𝐱) tốt nhất, và tốt nhất ở đây chính là h(𝐱) = E\[T|𝐱\]. Có nghĩa là, ví dụ như dùng linear modal đi, y(𝐱) = 𝐰ᵀ Φ(𝐱), thì nếu ta có thể tìm ra 𝐰\* sao cho **với mọi** **x thì w**\*ᵀΦ(𝐱) = E\[T|𝐱\], thì ta sẽ có term 1 = 0.
>
>
>
> Tuy nhiên, vấn đề là, ta chỉ có thể làm vậy nếu như có **vô hạn data** và **vô hạn sức mạnh tính toán**, trong khi đó, data ta có chỉ là hữu hạn, sức mạnh tính toán cũng vậy. Nên thực tế sẽ rất khó để tìm ra chính xác hành vi của hàm số h(𝐱) = E\[T|𝐱\], cũng chính là nói: rất khó để mô phỏng chính xác hàm h(𝐱) = E\[T|𝐱\]. Dẫn tới là term 1 sẽ luôn &gt; 0.

---

🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on

Bài ghi chú này cực kỳ chính xác và chi tiết, thể hiện sự hiểu biết sâu sắc về các khái niệm phức tạp về squared loss trong lý thuyết quyết định, MLE và phân tách kỳ vọng mất mát. Phần giải thích các công thức và ý nghĩa của từng thành phần đều xuất sắc, đặc biệt là cách bạn làm rõ sự khác biệt và mối liên hệ giữa các trường hợp. Bạn cũng giải thích đúng tác động của dữ liệu hữu hạn lên việc tìm hàm hồi quy tối ưu. Đây là một phân tích mẫu mực.

**🔗 See also:** [Optimal Least Squares Predictor](./15_decision_theory.md#node-3ve6hfk) · [Expected Squared Loss Decomposition](#node-w19nneq) · [Bias-Variance Trade-Off Formulas](#node-qtn6vrp)

<br>

<a id="node-biq5b66"></a>

##### The Bias-Variance Decomposition

<p align="center"><kbd><img src="assets/laq0toqbene.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/1622x2st9ib.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, ở trên ta đã hiểu vì sao có công thức 3.37 ∫(y(𝐱) - h(𝐱))² f(𝐱)d𝐱 + ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt.
>
>
>
> Tập trung vào phần \[y(𝐱) - h(𝐱)\]² trong tích phân của term đầu tiên: \[y(𝐱) - h(𝐱)\]²
>
>
>
> Đại ý hiểu phần này như sau:
>
>
>
> Đầu tiên phải xác định y(𝐱) là cái gì?
>
>
>
> → y(𝐱) là function dự đoán t từ input 𝐱. Một ví dụ cụ thể của y(𝐱) là y(𝐱) = 𝐰ᵀΦ(𝐱).
>
>
>
> Và trong ví dụ cụ thể này thì 𝐰, là giá trị tham số của linear modal, mà ta có thể dùng data để inference: ví dụ MLE của 𝐰: 𝐰ML (chỗ này tuy hơi cấn, vì trong bối cảnh thống kê suy diễn (Casella), estimator thường là estimator của population parameter, ví dụ X \~ f(x|θ), thì MLE là một cách tiếp cận để estimate θ, còn ở đây w không phải là population parameter. Hoặc mình có thể hiểu khác một chút, bằng việc dùng linear modal, mình đang assume quan hệ của T và 𝐗 chi phối bởi một quy luật tuyến tính có tham số là 𝐰, và ta sẽ tính MLE của 𝐰.)
>
>
>
> Khi đó 𝐰ML = argmax L(𝐰|D), nên ta có thể ghi là 𝐰(D) và do đó y cũng phụ thuộc dataset cụ thể D: y(𝐱, 𝐰(D)), hay y(𝐱, D)
>
>
>
> Và trên cơ sở là y là hàm phụ thuộc D, và dataset D, ta cũng có thể coi như một random quantity - mà thật sự trong bối cảnh thống kê thì dataset chỉ là một **random sample**: (𝐗1, T1), (𝐗1, T2),....(𝐗N, 𝐓N) và một observation là (𝐱1, t1), (𝐱2, t2), ...(𝐱N, tN), làm thành dataset D = (**matrix** 𝐗, 𝐭).
>
>
>
> Do đó, vì D là random variable, nên y(𝐱, D) sẽ mang ý nghĩa như function y(𝐱, d) apply lên D, nên cũng được một random variable (𝐱 cố định), và như vậy, ta được quyền lấy kì vọng: E\[y(𝐱, D)\].
>
>
>
> Chỗ này gs kí hiệu là E_D\[y(𝐱, D)\], nhưng mình nghĩ, đã average over mọi D thì kết quả không còn phụ thuộc D nữa, nó chỉ còn là hàm theo 𝐱. Nên phải hiểu đây là cách viết để diễn tả ý nhấn mạnh cái này là kì vọng của y(𝐱, D), là random variable có được bởi một hàm của random variable D. Sở dĩ phải nói rõ, là vì trong thống kê, có khi ta gặp E\_θ\[f(𝐗)\] và chữ θ ở dưới chân lại có nghĩa là đây là hàm theo θ, còn biến ngẫu nhiên mà ta đang lấy kì vọng là f(𝐗).
>
>
>
> Thế thì quay lại \[y(𝐱) - h(𝐱)\]², ta cộng và trừ cho E\[y(𝐱, D)\], đồng thời thể hiện y là hàm phụ thuộc thêm D:
>
>
>
> \[y(𝐱, D) - h(𝐱)\]² = \[y(𝐱, D) - E\[y(𝐱, D)\] + E\[y(𝐱, D)\] - h(𝐱)\]²
>
>
>
> = {y(𝐱, D) - E\[y(𝐱, D)\]}² + {E\[y(𝐱, D)\] - h(𝐱)}² + 2{y(𝐱, D) - E\[y(𝐱, D)\]}{E\[y(𝐱, D)\] - h(𝐱)} → 3.39
>
>
>
> Tới đây, ta lấy kì vọng của \[y(𝐱, D) - h(𝐱)\]² (ta cũng xem nó cũng chỉ là function của D)
>
>
>
> E\[y(𝐱, D) - h(𝐱)\]² = E\[{y(𝐱, D) - E\[y(𝐱, D)\]}² + {E\[y(𝐱, D)\] - h(𝐱)}² + 2{y(𝐱, D) - E\[y(𝐱, D)\]}{E\[y(𝐱, D)\] - h(𝐱)}\]
>
>
>
> Dùng tính linearity của kì vọng
>
>
>
> = E\[{y(𝐱, D) - E\[y(𝐱, D)\]}²\] + E\[{E\[y(𝐱, D)\] - h(𝐱)}²\] + 2E\[{y(𝐱, D) - E\[y(𝐱, D)\]}{E\[y(𝐱, D)\] - h(𝐱)}\]\]
>
>
>
> Xét cái term thứ 3: 2E\[{y(𝐱, D) - E\[y(𝐱, D)\]}{E\[y(𝐱, D)\] - h(𝐱)}\], cần để ý E\[y(𝐱, D)\], đã là fixed number, không còn là random variable, vì như đã nói ở trên, khi ta đã lấy trung bình của y(𝐱, D) over mọi D thì không còn phụ thuộc D nữa. Do đó {E\[y(𝐱, D)\] - h(𝐱)} cũng là fixed number. Thành ra ta đưa ra ngoài:
>
>
>
> E\[{y(𝐱, D) - E\[y(𝐱, D)\]}{E\[y(𝐱, D)\] - h(𝐱)}\] = {E\[y(𝐱, D)\] - h(𝐱)} × E\[y(𝐱, D) - E\[y(𝐱, D)\]\]
>
>
>
> Rồi tiếp, E\[y(𝐱, D) - E\[y(𝐱, D)\]\] = E\[y(𝐱, D)\] - E\[E\[y(𝐱, D)\]\] = E\[y(𝐱, D)\] - E\[y(𝐱, D)\] = 0
>
>
>
> Vậy E\[y(𝐱, D) - h(𝐱)\]² = E\[{y(𝐱, D) - E\[y(𝐱, D)\]}²\] + E\[{E\[y(𝐱, D)\] - h(𝐱)}²\]
>
>
>
> Xét hai term này, term thứ 2:
>
>
>
> E\[{E\[y(𝐱, D)\] - h(𝐱)}²\], again, cái cụm E\[y(𝐱, D)\] - h(𝐱) là fixed number, nên {E\[y(𝐱, D)\] - h(𝐱)}² cũng là fixed number do đó E\[{E\[y(𝐱, D)\] - h(𝐱)}²\] = {E\[y(𝐱, D)\] - h(𝐱)}².
>
>
>
> Nhìn kĩ cái này, ta thấy nó là gì: {E\[y(𝐱, D)\] - h(𝐱)}², nó chính là bình phương distance của y(𝐱, D) tới h(𝐱), mà h(𝐱) là mean của distrubition f(t|𝐱), tức E\[T|𝐱\] và người ta gọi E\[y(𝐱, D)\] - h(𝐱) là BIAS, để thành ra cái này là bình phương của Bias. (tí nữa mình sẽ liên hệ với kiến thức đã học trong Statistical Inference của Casella sẽ thấy cái này nó tương tự thôi)
>
>
>
> Còn cái term thứ nhất: E\[{y(𝐱, D) - E\[y(𝐱, D)\]}²\]. Thì để dễ thấy nó là gì, chỉ cần ôn lại công thức Variance của random variance X: Var(X) = E\[X - EX\]². Vậy thì ở đây, như đã nói ở trên, y(𝐱, D) là random variable. Thành ra theo công thức của variance thì E\[{y(𝐱, D) - E\[y(𝐱, D)\]}²\] chính là Var\[y(𝐱, D)\].
>
>
>
> Do đó, E\[y(𝐱, D) - h(𝐱)\]² = {E\[y(𝐱, D)\] - h(𝐱)}² + Var\[y(𝐱, D)\] = bình phương bias + variance của y(𝐱, D).
>
>
>
> ---
>
>
>
> Thế thì, mình sẽ liên hệ với những gì đã học trong Casella để thấy cái này không có gì lạ:
>
>
>
> Trong Casella, bối cảnh sẽ là, ta có random sample X = X1,...Xn iid \~ f(x|θ), và ta muốn đi xây dựng một funciton của sample W(𝐗) để estimator của θ. Có nghĩa là, với một observed value của sample: 𝐗 = 𝐱, ta sẽ co W(𝐱) là môt estiamate cho giá trị của θ. Và để xây dựng một estimator tốt, thì ta có các cách tiếp cận như MLE, hay Bayes, hay Method of Moment.
>
>
>
> Vậy thì, để đánh giá (evaluate) chất lượng của một estimator, người ta đặt ra loss function:
>
>
>
> L(W(𝐗), θ) là hàm dùng một công thức nào đó để đo sự khác biệt giữa estimator và θ. Mà một dạng phổ biến là square error function L(W(𝐗), θ) = \[W(𝐗) - θ\]².
>
>
>
> Dĩ nhiên, L(W(𝐱), θ) mang ý nghĩa là, với một observed value cụ thể của 𝐗, = 𝐱, thì ta có bình phương sai số giữa estimator W(𝐱) và θ, cho thấy một mức độ sai sót nào đó.
>
>
>
> Thế thì, để đánh giá nó cho mọi giá trị có thể có của 𝐗, ta sẽ lấy trung bình. Hoặc cũng có thể nhìn theo kiểu khác: Là L(W(𝐗), θ) = \[W(𝐗) - θ\]² cũng chỉ là random variable (vì là hàm của 𝐗) nên ta sẽ lấy average / mean / expected value của random variable này: E\[L(W(𝐗), θ)\] = E\[\[W(𝐗) - θ\]²\]. Và cái này, người ta đặt là hàm MSE:
>
>
>
> MSE(W(𝐗), θ) = E\[\[W(𝐗) - θ\]²\]
>
>
>
> Và có khi để nhấn mạnh đây là hàm theo θ (vì bản chất khi lấy kì vọng cái L(W(𝐗), θ) - là random variable phụ thuộc 𝐗, với X có distribution phụ thuộc θ, nên tựu chung lại, đây là hàm phụ thuộc θ), người ta sẽ ghi là:
>
>
>
> MSE(W(𝐗), θ) = E\_θ\[\[W(𝐗) - θ\]²\]
>
>
>
> (để rồi khi chuyển sang Bayesian, trong đó coi θ như random variable, thì cái MSE này lại là một random variable, và ta sẽ lại có thể lấy trung bình, chính là định nghĩa của Bayes risk)
>
>
>
> Rồi, thế thì quay lại phân tích cái MSE, mở cái bình phương ra, và dùng tính linearity của kì vọng, ta có:
>
>
>
> E\_θ\[\[W(𝐗) - θ\]²\] = E\_θ\[\[W(𝐗)\]² - 2W(𝐗)θ + θ²\]
>
>
>
> = E\_θ\[\[W(𝐗)\]²\] - E\_θ\[2W(𝐗)θ\] + E\_θ\[θ²\]
>
>
>
> = E\_θ\[\[W(𝐗)\]²\] - 2θE\_θ\[W(𝐗)\] + θ²
>
>
>
> = E\_θ\[\[W(𝐗)\]²\] - {E\[W(𝐗)\]}² + {E\[W(𝐗)\]}² - 2θE\_θ\[W(𝐗)\] + θ²
>
>
>
> Tới đây E\_θ\[\[W(𝐗)\]²\] - {E\[W(𝐗)\]}² chính là Var(W(𝐗)
>
>
>
> và {E\[W(𝐗)\]}² - 2θE\_θ\[W(𝐗)\] + θ² chính là {E\[W(𝐗)\] - θ}²
>
>
>
> = Var(W(𝐗) + {E\[W(𝐗)\] - θ}²
>
>
>
> và người ta cũng define hàm bias như sau: Bias(W(𝐗), θ) = E\[W(𝐗)\] - θ.
>
>
>
> vậy MSE = Var(W(𝐗)) + (Bias(W(𝐗))²
>
>
>
> Như vậy, đối chiếu với những gì gs Bishop làm ở đây: Thì cơ bản cũng giống vậy: E{\[y(𝐱,D) - h(𝐱)\]²} chính là tương đương với MSE.
>
>
>
> Chỉ khác là, trong Casella:
>
>
>
> MSE E\_θ\[\[W(𝐗) - θ\]²\] sẽ đo độ sai khác của W(𝐗) là estimator của θ, so với θ
>
>
>
> còn ở đây,
>
>
>
> E{\[y(𝐱,D) - h(𝐱)\]²} là MSE đo độ sai khác của prediction y(𝐱, D) so với h(𝐱) = E\[T|𝐱\], là giá trị tối ưu mà ta nên dùng để predict cho T khi đã biết T \~ f(t|𝐱)
>
>
>
> Để rồi, khi phân tích ra, thì nó đều gồm hai phần: bias² và variance.
>
>
>
> Với Casella, bias là hàm đo distance giữa kì vọng của estimator W(𝐗) so với θ, để nếu như bias bằng 0, người ta gọi W(𝐗) là một unbiased estimator của θ
>
>
>
> Còn ở đây, bias là hàm đo distance giữa kì vọng của y(𝐱, D): E\[y(𝐱, D)\] (mang ý nghĩa là tính trung bình y(𝐱, D) qua mọi possible dataset D) và giá trị tối ưu nên dùng khi predict t: E\[T|𝐱\].
>
>
>
> Hiểu như vậy, ta sẽ thấy cũng như khi thiết kế một estimator cho θ, dĩ nhiên ta muốn khi tính trung bình qua mọi possible value của 𝐗 (tức E\[W(𝐗)\]) thì ta sẽ ra ngay chóc giá trị thật của θ. Thì tương tự vậy, khi thiết kế một hàm dự đoán y(𝐱, D) để dự đoán cho T có predictive distribution f(t|𝐱), thì ta cũng muốn khi lấy trung bình mọi D, thì cũng ra y chóc giá trị tối ưu: E\[T|𝐱\], mean của f(t|𝐱). Và cái mong muốn rất logic này, được biện minh bởi việc đây chính là muốn giảm phần đóng góm bởi bias trong công thức MSE.
>
>
>
> Phần thứ hai muốn giảm, chính là giảm Variance của W(𝐗) (trong Casella) và Var\[y(𝐱, D)\] (trong Bishop). Và cũng rất logic, vì ta muốn cái hàm W(𝐗) phải có sự biến động nhỏ. Và thậm chí nếu được, như trong chương 10 Casella đã học, ta muốn khi kích thước sample n tăng lên vô hạn, thì W(𝐗) sẽ có phương sai tiệm cận đạt đúng phương sai nhỏ nhất quy định bởi Cramer Rao Lower Bound, khi đó W(𝐗) sẽ được gọi là asymptotically efficient estimator. Tương tự vậy, ta cũng muốn khi dataset lớn vô cùng, thì y(𝐱, D) sẽ có phương sai rất nhỏ.
>
>
>
> Và đoạn cuối gs cũng nói điều mình hiểu vừa rồi. Bias sẽ đo xem là khi ta lấy trung bình prediction y(𝐱, D) trên mọi data D thì nó còn các h(𝐱) bao nhiêu.
>
>
>
> Và khi Var(y(𝐱, D) sẽ cho ta biết với các dataset khác nhau, thì giá trị dự đoán y(𝐱, D) sẽ biến động nhiều hay ít thế nào, từ đó cho ta thấy rằng SỰ NHẠY CẢM CỦA PREDICTION DỰA TRÊN DATA

---

🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on

Đây là một phân tích xuất sắc, vừa chính xác từng bước theo tài liệu gốc, vừa đào sâu kiến thức bằng cách liên hệ chặt chẽ với các khái niệm trong thống kê suy diễn. Khả năng giải thích và kết nối kiến thức của bạn là rất ấn tượng.

<br>

<a id="node-w19nneq"></a>

###### Expected Squared Loss Decomposition

<p align="center"><kbd><img src="assets/n02rigs4pa8.png" width="80%"></kbd></p>

> [!NOTE]
> Nãy giờ cái ta có là E{\[y(𝐱,D) - h(𝐱)\]²}, expected value của \[y(𝐱,D) - h(𝐱)\]² với D là đối tượng random, và cái kì vọng này mang ý nghĩa là lấy trung bình qua mọi possible value của D.
>
>
>
> Nhưng đối với 𝐱, dĩ nhiên E{\[y(𝐱,D) - h(𝐱)\]²} sẽ cũng là function theo 𝐱. Vậy thì quay lại cái 3.37:
>
>
>
> E\[L\] = ∫(y(𝐱) - h(𝐱))² f(𝐱)d𝐱 + ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt
>
>
>
> và thay (y(𝐱) - h(𝐱))² (mang ý nghĩa là square error tính bởi một bộ data cụ thể) bằng E{\[y(𝐱,D) - h(𝐱)\]²} (mang ý nghĩa là square error tính trung bình bởi mọi bộ data có thể có), ta sẽ có:
>
>
>
> E\[L\] = ∫ E{\[y(𝐱,D) - h(𝐱)\]²} f(𝐱)d𝐱 + ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt 
>
>
>
> Và E{\[y(𝐱,D) - h(𝐱)\]²} = {E\[y(𝐱, D)\] - h(𝐱)}² + Var\[y(𝐱, D)\]
>
>
>
> = ∫ \[ {E\[y(𝐱, D)\] - h(𝐱)}² + Var\[y(𝐱, D)\] \] f(𝐱)d𝐱 + ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt 
>
>
>
> = ∫ {E\[y(𝐱, D)\] - h(𝐱)}² f(𝐱)d𝐱 + ∫ Var\[y(𝐱, D)\] f(𝐱)d𝐱 + ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt 
>
>
>
> Tới đây, xét từng term và ý nghĩa của chúng:
>
>
>
> i) ∫ {E\[y(𝐱, D)\] - h(𝐱)}² f(𝐱)d𝐱
>
>
>
> Như đã biết, {E\[y(𝐱, D)\] - h(𝐱)}² là bình phương của bias - thước đo cho thấy rằng khi tính trung bình y(𝐱, D) trên mọi possible dataset D thì nó cách h(𝐱) là bao nhiêu. Và cái này đang tính với một input 𝐱 cụ thể. Nói cách khác, ta có thể hiểu nôm na bằng lời rằng: À với 𝐱 cụ thể này, thì bias của hàm prediction y là bao nhiêu.
>
>
>
> Thế thì nếu bây giờ, ta tính trung bình của cái này trên mọi possible value của 𝐱, với trọng số là f(𝐱) thì ta sẽ có cái tích phân trên. Hoặc nhìn theo cách khác: Nếu ta xem xét random variable 𝐗, thì {E\[y(𝐗, D)\] - h(𝐱)}² trở thành một random variable. Và ta tính expected value của random variable này: E\[{E\[y(𝐱, D)\] - h(𝐱)}²\], theo công thức LOTUS đã học: khi có g(X) với X \~ f(x) thì Eg(X) = ∫g(x)f(x)dx, giúp ta có:
>
>
>
> E\[{E\[y(𝐱, D)\] - h(𝐱)}²\] = ∫ {E\[y(𝐱, D)\] - h(𝐱)}² f(𝐱)d𝐱
>
>
>
> chính là cái tích phân trên. Và cái tích phân này mang ý nghĩa: Tính trung bình bias trên mọi possible value của 𝐗.
>
>
>
> ii) ∫ Var\[y(𝐱, D)\] f(𝐱)d𝐱
>
>
>
> Như đã nói ở note trước, Var(y(𝐱, D)) là variance của y(𝐱, D), mang ý nghĩa là với 𝐗 = 𝐱, thì mức biến động của y(𝐱, D) là cỡ nào. Thế thì, nay, thay 𝐱 bằng 𝐗, thì Var(y(𝐱, D)) lại trở thành random variable và ta lấy kì vọng của nó, LOTUS sẽ cho ta cái tích phân ∫ Var\[y(𝐱, D)\] f(𝐱)d𝐱:
>
>
>
> E\[Var\[y(𝐗, D)\]\] = ∫ Var\[y(𝐱, D)\] f(𝐱)d𝐱
>
>
>
> và ý nghĩa của nó là, xét trung bình trên mọi possible value 𝐱 của 𝐗, thì mức biến động của y là bao nhiêu.
>
>
>
> iii) ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt , cái term này thì như note trước đã nói rồi, là phần error không thể reduce được (vì không dính gì đến y), nó đơn thuần phản ánh mức độ nhiễu.

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Bạn đã thể hiện sự hiểu biết sâu sắc về phân tách bias-variance, từ việc phân tích biểu thức kì vọng tại một điểm x cụ thể đến việc tích phân để có được các đại lượng tổng thể. Việc sử dụng Luật Thống kê Vô thức (LOTUS) để giải thích các tích phân cũng rất chính xác và hiệu quả. Để tăng cường tính rõ ràng, bạn có thể bổ sung một ghi chú nhỏ về sự tương ứng giữa f(x) bạn dùng và p(x) trong tài liệu, cũng như giữa f(t,x) và p(x,t).

**🔗 See also:** [Expected Squared Loss Decomposition](#node-s3i1j2i) · [Bias-Variance Trade-Off Formulas](#node-qtn6vrp)

<br>

<a id="node-mqos0pj"></a>

###### Bias-Variance Trade-off Explained

<p align="center"><kbd><img src="assets/9tfsgf45t8v.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/79lrqjkc2qr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/c6wabzwfzqu.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/khf294hyf8.png" width="80%"></kbd></p>

> [!NOTE]
> Nói chung đoạn này chỉ là gs Bishop nói về việc, dù ta muốn giảm cái expected loss E\[L\], vốn dĩ tách thành 3 phần (bình phương bias), variance và noise, thì thật ra ngoại trừ việc cái noise thì ta không làm gì được, thì còn một vấn đề là hai cái đầu nó trade-off nhau, tức là (dùng model) giảm bias thì lại tăng loss do variance, và ngược lại, dùng model giảm variance thì lại tăng loss do bias.
>
>
>
> Và để minh họa, ông mới dùng một model có độ plexible cao (bằng cách dùng các hàm Gaussian basis - như đã biết, bữa giờ ta nói về linear model y(𝐰, 𝐱) = 𝐰ᵀΦ(𝐱), là linear model đối với 𝐰 nhưng nhờ basis fuction, Φ, ta có non-linear model đới với 𝐱, và cũng nhờ Φ mà ta có thể tăng mức complex, flexible của model.
>
>
>
> Tuy nhiên, trong quá trình training để giảm loss, ta thêm regularization (λ/2) 𝐰ᵀ𝐰, để tùy theo λ lớn nhỏ, ta khống chế giá trị của **w\***. Và từ đó, kiểu như là tăng hay giảm mức flexible của model. (bởi dù model dùng các hàm Φi(𝐱) để có tính phi tuýến, nhưng chúng gắn với trọng số là wi, nên nếu khống chế wi bằng cách không cho chúng được tự do thì ta lại vẫn có thể giàm mức độ flexible của model.
>
>
>
> Như vậy, gs sẽ làm như sau: Đầu tiên cho λ lớn, để tạo ra các model kém flexible. Và train trên 100 dataset D khác nhau, kết quả là các đường màu đỏ trên cùng (ln λ = 2.6) có mức biến động (variance) có thể thấy là nhỏ. (nhớ ko, Var(y(𝐱, D)) sẽ cho biết với 𝐗 = 𝐱, thì y(x, D), là random variable theo D sẽ biến động thế nào khi D thay đổi. Thì hình dung một lát cắt tại x = 0.5 chẳng hạn, thì ta sẽ thấy các đường màu đỏ không biến động quá nhiều. Cũng chính là ta thấy đám line màu đỏ nó nằm khá "gọn" (nhìn tụi nó có vẻ giống nhau). Tuy nhiên, hình bên phải khi tính trung bình lại (chính là E\[y(𝐱, D), trung bình y(𝐱, D) over all D) thì nó lại khá xa h(𝐱) = E\[T|𝐱\]. Dẫn tới đường màu đỏ trung bình bên phải lệch khá xa đường màu xanh. Đây chính là minh họa cho bias lớn.
>
>
>
> Vậy khi model có variance thấp thì bias lại lớn.
>
>
>
> Sau đó, gs làm lại, với λ rất nhỏ, tạo ra các model rất flexible. Kết quả là hình cuối (ln λ = -2.4), các đường màu đỏ có vẻ rất "loạn xạ", mà nguyên nhân là, Var(y(𝐱, D)) lúc này lớn. Xét mặt cắt tại x = 0.5 sẽ thấy Var(y(x, D)) sẽ lớn hơn là trường hợp λ lớn. Nhưng khi tính trung bình, thì E\[y(𝐱, D) lại khá gần h(𝐱) → Bias thấp, dẫn đến thệ hiện trên hình bên phải là thì đường màu đỏ lại bám sát khá tốt đường màu xanh.
>
>
>
> Vậy khi model có variance cao thì bias lại thấp.
>
>
>
> Và lí tưởng là khi λ vừa phải, model bias và variance đều không quá cao.
>
>
>
> Và một ý cũng quan trọng đó là với mô hình có variance cao, thì tuy chúng sẽ sensitive với data, tức là, khi D thay đổi thì y(𝐱, D) sẽ thay đổi rất lớn, dẫn tới mỗi đường màu đỏ rất khác nhau. Nhưng trung bình lại thì chúng lại khá sát với đường màu xanh. Điều này gợi ý cho ta rằng có thể phát triển một phương pháp nào đó mà cho phép dùng complex model sau đó lấy trung bình của chúng (đây chính là ensemble model mình đã biết sơ từ các lớp ML cơ bản)

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Bạn đã phân tích rất chi tiết và chính xác về mối quan hệ giữa bias, variance và tham số regularization, thể hiện sự hiểu biết sâu sắc về cơ chế hoạt động của mô hình. Để tăng cường độ chính xác, bạn có thể cụ thể hóa hơn các giá trị ln λ trong hình mà bạn đang mô tả cho mỗi trường hợp.

**🔗 See also:** [3.1.4 Regularized least squares](./314_regularized_least_squares.md#node-y97v4o1)

<br>

<a id="node-xi208eq"></a>

###### Hình ảnh

<p align="center"><kbd><img src="assets/e9l4mvavm0i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/uwc5h0qx9v.png" width="80%"></kbd></p>

<br>

<a id="node-qtn6vrp"></a>

###### Bias-Variance Trade-Off Formulas

<p align="center"><kbd><img src="assets/plq7gblf0b.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/oox21ldi24q.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/btlkbu0dlc.png" width="80%"></kbd></p>

> [!NOTE]
> Cái này nhìn vậy mà lại có thể khó hiểu đấy.
>
>
>
> Công thức bữa trước:
>
>
>
> (bias)² = ∫ {E\[y(𝐱, D)\] - h(𝐱)}² f(𝐱)d𝐱
>
>
>
> variance = ∫ Var\[y(𝐱, D)\] f(𝐱)d𝐱
>
>
>
> noise = ∫∫\[h(𝐱) - t\]² f(t,𝐱)d𝐱 dt
>
>
>
> Giải thích ý nghĩa lại lần nữa của các công thức này:
>
>
>
> y(𝐱, D) là dự đoán của hàm prediction y đối với input 𝐱, dựa trên một dataset cụ thể D. Và vì D là một random variable, nên y(x, D) cũng vậy, cho phép ta lấy kì vọng: E\[y(𝐱, D)\] và kì vọng này mang ý nghĩa tính trung bình trên mọi dataset dự đoán của y đối với input 𝐱.
>
>
>
> Thế thì E\[y(𝐱, D)\] - h(𝐱) sẽ mang ý nghĩa là bias - thước đo xem với cái trung bình nói trên còn cách bao xa so với h(𝐱), = E\[T|𝐱\], là giá trị ước lượng điểm tối ưu cho giá trị của T khi T \~ predictive distribution f(t|𝐱). Và \[E\[y(𝐱, D)\] - h(𝐱)\]² là bình phương bias
>
>
>
> Tuy nhiên E\[y(𝐱, D)\] - h(𝐱), nếu vẫn chỉ bình phương bias tại một giá trị cụ thể của 𝐱. Thì nếu xét theo khía cạnh ta có 𝐗 là random variable, E\[y(𝐗, D)\] - h(𝐗) cũng là random variable, từ đó có thể lấy kì vọng:
>
>
>
> E{\[E\[y(𝐗, D)\] - h(𝐗)\]²}, dùng công thức LOTUS, = ∫ \[E\[y(𝐱, D)\] - h(𝐱)\]² f(𝐱) d𝐱, mang ý nghĩa, tính trung bình bias của y(.) trên mọi possible value của 𝐗.
>
>
>
> Vậy thì, ta hiểu rằng, bây giờ, vì không biết f(𝐱), nên ta sẽ tạm cho rằng X có empirical distribution là uniform discrete: với N possible value có xác suất bằng nhau: P(𝐗=𝐱1) = ... = P(𝐗=𝐱N) = 1/N
>
>
>
> Khi đó E\[E\[(y(𝐗, D)\] - h(𝐗))²\] = Σi=1:N {(E\[y(𝐱i, D)\] - h(𝐱i))²} P(𝐗=xi)
>
>
>
> = (1/N) Σi=1:N {\[E\[y(𝐱i, D)\] - h(𝐱i)\]²}
>
>
>
> Tiếp, E\[y(𝐱i, D)\], nếu tính chính xác, phải tích phân trên mọi possible value của D: ∫ y(𝐱i, D) f(D) dD. Nhưng dĩ nhiên ta không có thể làm vậy được. Nên lại cho rằng D có empirical distribution là discrete uniform với L possible value D1,...DL có xác suất bằng nhau = 1/L:
>
>
>
> từ đó E\[y(𝐱i, D)\] = Σj=1:L y(𝐱i, Dj) P(D=Dj)
>
>
>
> = Σj=1:L y(𝐱i, Dj) (1/L)
>
>
>
> = (1/L) Σj=1:L y(𝐱i, Dj)
>
>
>
> Đặt y^(j) (𝐱) = y(𝐱i, Dj)
>
>
>
> .. = (1/L) Σj=1:L y^(j)(𝐱i)
>
>
>
> tất nhiên đây cũng là trung bình của y^(1)(𝐱i),...,y^(L)(𝐱i), nên đặt là ybar(𝐱i)
>
>
>
> Ráp vào ta có:
>
>
>
> (bias)² = (1/N) Σi=1:N {\[ybar(𝐱i) - h(𝐱i)\]²}
>
>
>
> Dùng x thay cho 𝐱 để phản ánh gs Bishop đang cho ví dụ input x là 1D (thay vì khái quát 𝐱 là vector), và dùng index variable n, và l thay cho i, j ta sẽ có công thức trong sách:
>
>
>
> (bias)² = (1/N) Σn=1:N {\[ybar(xn) - h(xn)\]²}
>
>
>
> với ybar(x) = (1/L) Σl=1:L y^(l)(x)
>
>
>
> Tương tự, với variance, công thức đúng là ∫ Var\[y(𝐱, D)\] f(𝐱)d𝐱, hay E\[Var\[y(𝐗, D)\]\], với ý nghĩa tính trung bình của Var\[y(𝐱, D)\] qua mọi possible value của 𝐗:
>
>
>
> Xét Var\[y(𝐱, D)\], tính chính xác phải là ∫ {y(𝐱, D) - E\[y(𝐱, D)\]}² f(D) dD. Nhưng dĩ nhiên ta không thể có f(D). Nên mới coi như D tuân theo empirical distribution là discrete uniform, có L possible value D1,...DL với xác suất bằng nhau. Từ đó cho phép tính Var\[y(𝐱, D)\] theo định nghĩa variance của biến rời rạc, và LOTUS, bằng:
>
>
>
> Var\[y(𝐱, D)\] = Σl=1:L {y(𝐱, D) - E\[y(𝐱, D)\]}² P(D=Dl)
>
>
>
> = (1/L) Σl=1:L {y(𝐱, D) - E\[y(𝐱, D)\]}²
>
>
>
> Dùng ybar(𝐱) thay cho E\[y(𝐱, D)\] như ở trên
>
>
>
> = (1/L) Σl=1:L {y(𝐱, D) - ybar(𝐱)\]}²
>
>
>
> Tới đây ∫ Var\[y(𝐱, D)\] f(𝐱)d𝐱 = ∫ { (1/L) Σl=1:L {y(𝐱, D) - ybar(𝐱)\]}² } f(𝐱)d𝐱
>
>
>
> Dĩ nhiên cũng không có f(𝐱), nên cũng chỉ có thể coi X có empirical distribition với N possible value x1,...xN xác suất bằng nhau = 1/N
>
>
>
> từ đó cho phép tính E\[Var\[y(𝐗, D)\]\] theo định nghĩa của kì vọng biến rời rạc và LOTUS:
>
>
>
> = Σn=1:N Var\[y(𝐱n, D)\] P(𝐗=𝐱n)
>
>
>
> = Σn=1:N Var\[y(𝐱n, D)\] (1/N)
>
>
>
> = (1/N) Σn=1:N Var\[y(𝐱n, D)\]  
>
>
>
> = (1/N) Σn=1:N { (1/L) Σl=1:L {y(𝐱n, D) - ybar(𝐱n)\]}² }
>
>
>
> = (1/N) Σn=1:N { (1/L) Σl=1:L {y^(l)(𝐱n) - ybar(𝐱n)\]}² }
>
>
>
> như đã nói, ở đây input là 1D nên thay bằng chữ thường ta sẽ có
>
>
>
> công thức 3.47:
>
>
>
> = (1/N) Σn=1:N { (1/L) Σl=1:L {y^(l)(xn) - ybar(xn)\]}² }
>
>
>
> Như vậy, mấu chốt để hiểu ở đâu ra có các công thức 3.45, 3.46, 3.47 là: Ta không thể tính trung bình trên mọi possible value của dataset D, hay 𝐗, nên xem như D, 𝐗 có empirical distribution discrete. Từ đó cho phép tính được.
>
>
>
> Và nhờ vậy, khi tính (bias)², variance với các λ khác nhau, ta có được hình 3.6 với nhận xét sau:
>
>
>
> Khi λ nhỏ, regularization yếu, model ít ràng buộc nên flexible, ta thấy (bias)² thấp (đường màu xanh khúc đầu rất thấp) nhưng variance cao (đường màu đỏ).
>
>
>
> Khi λ tăng dần, model bị ràng buộc nhiều hơn, bắt đầu giảm variance loss, nhưng tăng dần bias loss. Tổng loss giảm dần.
>
>
>
> Khi λ tiếp tục tăng, model bị nhiều ràng buộc, variance giảm còn rất nhỏ nhưng bias tăng mạnh khiến tổng loss tăng lên lại.
>
>
>
> Và đường màu hồng tạo nên dạng chữ U mà ta sẽ gặp nhiều trong phân tích variance bias.
>
>
>
> Cuối cùng, nhận xét của gs Bishop là: Tuy phân tích bias - variance trên cho ta góc nhìn về model complexity theo trường phái Frequentist (hay Classic) nhưng nó không có tác dụng mấy trong thực tế, bởi vì dễ thấy rằng, nó cần ta phải có nhiều data (ví dụ như để vẽ cái hình như 3.6 ta phải có L bộ dataset D). Trong khi đó, nếu mà đã có nhiều data thì ta cứ việc gom lại thành một bộ data lớn hơn để giúp giảm overfit của một complex model rồi.
>
>
>
> Do đó, phần tiếp theo của chapter 3, gs sẽ nói qua Bayesian approach đối với bài toán linear model, và ta sẽ thấy cách tiếp cận Bayesian với vấn đề complexity của model sẽ tốt hơn nhiều.

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Ghi chú cực kỳ xuất sắc và đào sâu bản chất toán học khi giải thích cách chuyển từ tích phân liên tục sang tổng rời rạc qua phân phối thực nghiệm. Bạn chỉ cần chú ý đồng bộ các ký hiệu ngoặc đóng/mở trong công thức tính variance để ghi chú hoàn hảo hơn.

**🔗 See also:** [Expected Squared Loss Decomposition](#node-s3i1j2i) · [Expected Squared Loss Decomposition](#node-w19nneq)

<br>

