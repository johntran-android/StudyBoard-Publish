# 3.2.0 The Bias-Variance Decomposition

📊 **Progress:** `4` Notes | `4` Screenshots | `3` AI Reviews

---
<a id="node-0nolzxg"></a>

## 3.2.0 The Bias-Variance Decomposition

<p align="center"><kbd><img src="assets/y54wc6qlvqb.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại ý là vầy: Mấy phần trước cũng như liên hệ với bên Casella mình đã thấy nhược điểm của MLE khi data ít, nó sẽ đại khái là cho ra những kết quả cực đoan, và trong bối cảnh machine learning chính là thứ ta gọi là overfit - khi ta dùng model phức tạp với ít data.
>
>
>
> Rồi ông có nhắc đến việc ta thảo luận về linear model - có dạng cũng như số basis function không đổi. Ý này là sao? → Tức là ta đang nói về linear model có dạng y(**x**, **w**) = **w**TΦ(**x**) với w = (w0, w1, ...wM-1)T và Φ(**x**) = (1, Φ1(**x**), ...ΦM-1(**x**))T, đương nhiêi với M là giá trị cố định nào đó, thì ta có một giá trị cố định các tham số cũng như các basis function. Ý muốn và ta nhớ, đây vẫn là hàm tuyến tính đối với **w** dù cho nhờ hàm basis, y trở thành hàm phi tuyến đối với **x**, và do đó vẫn gọi là linear model là vậy.
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
> Đơn giản là vì λ vốn có ràng buộc ≥ 0, và để minimize E_D(**w**) + λE_W(**w**) với E_W(**w**) ≥ 0 thì đây là hàm tuyến tính theo λ, E_D(**w**) + λE_W(**w**), có dạng a λ + b, và với λ ≥ 0, thì và a = E_W(**w**) cũng > 0 thì hàm này cực tiểu khi λ = biên của \[0, ∞), tức λ = 0.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bài ghi chú thể hiện sự hiểu biết sâu sắc về các khái niệm, giải thích chính xác nội dung văn bản và cung cấp những phân tích bổ sung tuyệt vời, đặc biệt là lý do tại sao λ=0 khi tối ưu hóa đồng thời. Đây là một bài phân tích rất chi tiết và chính xác.

<br>

<a id="node-897hybe"></a>

## Bias-Variance Trade-off Overview

<p align="center"><kbd><img src="assets/jcvn4w23vog.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đại khái là, gs nói vấn đề overfit là nhược điểm của maximum likelihood, chứ nếu làm **theo Bayesian approach, thì ta sẽ không bị vấn đề này** (đã nói nhiều về cái này, cũng như trong Casella cũng đã nói, nguyên nhân ngắn gọn là vì Bayesian approach, ta cói paramter là random variable, và từ đó đặt ra prior distribution của parameter π(θ) và chính cái này giúp cho khi ta đi xây dựng posterior π(**x**|θ) cũng như đi maximum posterior cũng chính là maximum L(θ|**x**) π(θ), thì prior distribution sẽ giúp cho kết quả không bị extreme khi data ít như cách làm của mle (chỉ maximum L(θ|**x**)).
>
>
>
>  Cho nên trong chapter này ta sẽ bàn sâu hơn về Bayesian approach. Tuy nhiên trước đó, gs sẽ dẫn dắt ta về một **góc nhìn về vấn đề overfit trong phạm vi vẫn thuộc trường phái cổ điển**: **Bias Variance trade-off**. Và cái này sẽ mở rộng cả các phạm vi khác chứ không riêng gì bài toán linear basis function model

<br>

<a id="node-a09r921"></a>

### Optimal Prediction with Squared Loss

<p align="center"><kbd><img src="assets/80hlynvklfv.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đoạn này đại khái là, nhắc lại một điểm đã nói trước đây: rằng, giả sử ta đã có predictive distribution, tức f(t|**x**). Thì dự đoán tối ưu cho giá trị của T sẽ là gì.
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
> Đầu đuôi câu chuyện là: Với Bayesian, ta coi θ như random variable. Mà đã là random variable, thì nó có probability distribution. Thế thì, marginal distribution của θ, mà với θ, thì người ta gọi là prior distribution π(θ), là thứ mà ta sẽ chọn, dựa vào kinh nghiệm nào đó, nhằm phản ánh một hiểu biết nào đó của ta về θ. Để rồi dùng Bayes rule ta xây dựng π(θ|**x**) = f(**x**|θ) π(θ) / f(**x**), gọi là posterior distribution. Thế thì, vấn đề là, đây vẫn là một distribution, trong khi có thể ta cần đưa ra một point estimation cho θ thì sao? mà theo định nghĩa, point estimator là một hàm số của sample W(**X**), nên yêu cầu là ta cần rút ra một hàm số từ cái distribution này.
>
>
>
> Và đây chính là lúc ta cần viện tới công cụ thuộc lĩnh vực decision theory: Giúp đưa ra quyết định trong điều kiện không chắc chắn (making decision under uncertainty): Tính không chắc chắn phản ánh bởi một probability distribution π(θ|**x**), và ra quyết định ở đây chính là đưa ra một ước lượng điểm W(**X**) cho θ từ đó.
>
>
>
> Và trong decision theory, ta sẽ cần lựa chọn loss function: Là hàm số của estimator: L(W(**X**), θ), phản ánh một cách thức nào đó mà ta trừng phạt các sai sót. Phổ biến được dùng là square error loss (W(**X**) - θ)^2. và absolute error loss |W(**X**) - θ|.
>
>
>
> Cần hiểu điều quan trọng này: Giả sử với θ fixed, thì L(W(**x**), θ) chỉ phản ánh error của W(**x**) với một giá trị **x** cụ thể. Cho nên ta sẽ đi tính trung bình error trên mọi possible value của **X**. Hoặc nhìn theo cách khác, với θ fixed nào đó, thì L(W(**X**), θ) vẫn là môt random variable có được bằng cách áp hàm L(W(**u**), θ) lên random variable **X**. Và vì vậy, ta có quyền nói về kì vọng / mean / expected value của nó. E\[L(W(**X**), θ)\], và vì distribution của L(W(**X**), θ) sẽ phụ thuộc θ do bản chất là **X** \~ f(**x**|θ), nên ta ghi là E\_θ\[L(W(**X**), θ)\], để thể hiện, đây sẽ là hàm số phụ thuộc θ.
>
>
>
> Và cái này chính là định nghĩa của risk function: R(W(**X**), θ) = E\_θ\[L(W(**X**), θ)\], nếu dùng LOTUS, ta sẽ dễ hiểu nó là: ∫L(W(**x**), θ) f(**x**|θ) d**x**.
>
>
>
> Tới đây, nếu ta đi thêm một bước để bước chân qua Bayesian approach, coi θ như random variable, thì cái risk function trên vẫn sẽ là một random variable (có được bởi áp hàm g(θ) = E\_θ\[L(W(**X**), θ)\], lên random variable θ). Để rồi nếu ta lấy expected value của nó, ta sẽ có một con số cố định cuối cùng, không còn phụ thuộc ai. Đó chính là Bayes risk:
>
>
>
> Bayes risk = E{E\_θ\[L(W(**X**), θ)\]} = ∫ E\_θ\[L(W(**X**), θ)\] π(θ) dθ
>
>
>
> Nếu biến đổi tí xíu, dùng Bayes rule: .. = ∫ \[∫ L(W(**x**), θ)\] f(**x**|θ) d**x** π(θ)\] dθ
>
>
>
> = ∫ \[∫ L(W(**x**), θ)\] f(**x**|θ)π(θ) d**x**\] dθ
>
>
>
> = ∫ \[∫ L(W(**x**), θ)\] π(θ|**x**)f(**x**) d**x**\] dθ (thay f(**x**|θ)π(θ) bởi π(θ|**x**)f(**x**))
>
>
>
> = ∫ \[∫ L(W(**x**), θ)\] π(θ|**x**) dθ\] f(**x**)d**x** (tính tích phân theo θ trước)
>
>
>
> thì lúc này, ∫ L(W(**x**), θ)\] π(θ|**x**) dθ chính là E\[L(W(**x**), θ)\] với θ \~ π(θ|**x**), tức là, với giá trị nào đó của **X** = **x**, ta có θ \~ posterior π(**x**|θ) và tính kì vọng của L(W(**x**), θ) với θ có distribution này. Thì cái này gọi là **posterior expected loss**.
>
>
>
> Rồi, với tất cả các định nghĩa trên, giờ ta mới đi quay lại nói về việc tìm point estimator của θ sao cho tối ưu.
>
>
>
> Nói bài toán Bayesian trước: θ là random variable, thì ta sẽ đi tìm W(**X**) minimize Bayes risk, và vì Bayes risk là tích phân over mọi **x** của posterior expected risk, nên bài toán này tương đương đi minimize posterior expected risk:
>
>
>
> minimize_W ∫ L(W(**x**), θ)\] π(θ|**x**) dθ
>
>
>
> ∫ L(W(**x**), θ)\] π(θ|**x**) dθ = ∫ \[W(**x**) - θ\]^2 π(θ|**x**) dθ
>
>
>
>  ∂/∂W \[∫ \[W(**x**) - θ\]^2 π(θ|**x**) dθ\] = ∫ { ∂/∂W \[W(**x**) - θ\]^2 } π(θ|**x**) dθ
>
> = ∫ 2 \[W(**x**) - θ\] π(θ|**x**) dθ
>
>
>
> = 2 ∫\[W(**x**) - θ\] π(θ|**x**) dθ
>
>
>
> First order condition: 2 ∫\[W(**x**) - θ\] π(θ|**x**) dθ = 0
>
>
>
> ⇔ ∫\[W(**x**)π(θ|**x**) dθ - ∫θπ(θ|**x**) dθ = 0
>
>
>
> ⇔ ∫W(**x**)π(θ|**x**) dθ = ∫θπ(θ|**x**) dθ
>
>
>
> ⇔ W(**x**) ∫π(θ|**x**) dθ = E\[θ\] (θ \~ π(θ|**x**))
>
>
>
> ⇔ W(**x**) = E\[θ|**x**\] (θ \~ π(θ|**x**))
>
>
>
> → Khi **X** = **x**, và θ \~ f(θ|**x**) thì W(**x**) khiến minimize posterior expected loss với chính là mean của posterior.
>
> \
> Vậy nên W(**X**) = E\[θ|**X**\] chính là point estimator của θ với θ \~ f(θ|**X**) giúp minimize Bayes risk với square error loss.
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
> minimize_W E\_θ\[L(W(**X**), θ)\] = ∫ L(W(**x**), θ) f(**x**|θ) d**x**, = (nếu dùng square error loss) = ∫ \[W(**x**) - θ\]^2 f(**x**|θ) d**x**
>
>
>
> Và cái này, ∫ \[W(**x**) - θ\]^2 f(**x**|θ) d**x**, tức E\_θ\[(W(**X**) - θ)^2\], ta nhớ chính là định nghĩa của MSE, để rồi ta sẽ phân tích nó thành Bias(W(**X**)^2 + Var(W(**X**). Từ đó đi tìm W(**X**) giúp giảm cái này, dẫn tới các cách tiếp cận như xét trong các unbiased estiamtor, xem cái nào có Variance nhỏ nhất, và variance thế nào thì nhỏ nhất lại dẫn đến công cụ là Cramer Rao Lower Bound,...
>
>
>
> ---
>
>
>
> Với chừng đó ôn tập, mình quay lại cái bài toán trong sách này, là đưa ra predict tối ưu của T khi có T \~ f(t|**x**)
>
>
>
> Thì cái này y chang việc có π(θ|**x**), và cần estimate tối ưu cho θ thôi:
>
>
>
> Ta cũng đi giải bài toán: minimize_h(**x**) Risk function = ∫ L(h(**x**), t) f(t|**x**) dt = ∫(h(**x**) - t)^2 f(t|**x**) dt
>
>
>
>  ∂/∂y \[∫(h(**x**) - t)^2 f(t|**x**) dt\] = ∫ \[∂/∂y \[(h(**x**) - t)^2\] f(t|**x**) dt
>
>
>
> = ∫ 2(h(**x**) - t) f(t|**x**) dt
>
>
>
> = 2∫ (h(**x**) - t) f(t|**x**) dt
>
>
>
> Fisrt order optimality condition: 2∫ (h(**x**) - t) f(t|**x**) dt = 0
>
>
>
> ⇔ ∫(h(**x**) - t) f(t|**x**) dt = 0
>
>
>
> ⇔ ∫h(**x**)f(t|**x**) dt - ∫t f(t|**x**) dt = 0
>
>
>
> ⇔ h(**x**) ∫f(t|**x**) dt = E\[T|**x**\]
>
>
>
> ⇔ h(**x**) = E\[T|**x**\]
>
>
>
> Như vậy, optimal point estimator cho T khi T \~ f(t|**x**) chính là posterior mean: E\[T|**x**\] → Đây chính giúp ta hoàn toàn hiểu 3.36.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bài giải thích cực kỳ chi tiết và sâu sắc, vượt xa nội dung ảnh để cung cấp một nền tảng vững chắc về lý thuyết quyết định và ước lượng Bayes. Mặc dù rất toàn diện, có thể tóm tắt các phần ôn tập một cách ngắn gọn hơn nếu mục tiêu là chỉ tập trung vào giải thích công thức 3.36.

<br>

<a id="node-s3i1j2i"></a>

#### Expected Squared Loss Decomposition

<p align="center"><kbd><img src="assets/87zodxs4od8.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, tiếp theo chỗ này dễ lú, nên cần giải thích rõ khi ông nói ta cần phải phân biệt có hai loại squared loss, trong rất giống nhau, một cái là trong bối cảnh decision theory và còn lại là trong bài toán MLE. Là sao ta?
>
>
>
> Hiểu đại khái vầy: Nói đến decision theory, là vì, như note trước ta vừa mới làm: Rằng, trong bài toán này, khi ta làm theo probabilistic perspective, coi T như random variable, có predictive distribution f(t|**x**) thì câu hỏi đặt ra là, khi đã có f(t|**x**) rồi, thì nên lấy giá trị bao nhiêu để dự đoán (vì yêu cầu của bài toán cuối cùng vẫn là cho **x**, dự đoán t, chứ không phải là tính ra f(t|**x**)). Và đối mặt với câu hỏi này, ta cần đến decision theory giúp đỡ, nó sẽ cho ta cách làm như sau: Ta sẽ chọn loss function: L(T, h(**x**)), ví dụ square error loss, = (T - h(**x**))^2, đây sẽ là random variable (hàm của T). Và tính risk function, mang ý nghĩa là average của loss over all T \~ f(t|**x**):
>
>
>
> Risk function = E\[T - h(**x**)\] = ∫(t - h(**x**))^2 f(t|**x**)dt
>
>
>
> Và đi tìm h để mininimize cái risk function thì kết quả là h(**x**) = E\[T|**x**\].
>
>
>
> Đó là nói về square loss function trong decision theory, nói ngắn gọn, nó giúp ta đưa ra optimal point estimation của T với T \~ f(t|**x**).
>
>
>
> Thế còn sum squared error trong MLE?
>
>
>
> Là vầy: Nói về MLE, tức là ta nói về bài toán tìm point estimation cho PARAMETER θ: tìm estimator, là hàm theo data W(**X**, **t**) sao cho maximize L(θ|**X**, **t**) (**X**, **t** ở đây là observed data: **X** = matrix tạo bởi các vector **x**1, ...**x**N và **t** là vector các observed data t1, t2,...tN và có thể gọi chung là D (data) cho gọn) và θ đại diện cho tất cả parameter nói chung.
>
>
>
> Trong bài toán cụ thể ở đây, nếu ta dùng linear model dự đoán cho T \~ normal(y(**w**,**x**), 1/β) thì θ chính là (**w**, β). Và bài toán để giải MLE của (w, β) sẽ là:
>
>
>
> maximize (over **w**, β) L(**w**, β|**X**,**t**) = f(**t**|**w**, β, **X**).
>
>
>
> nhờ tính independent của T1,....Tn nên f(**t**|**w**, β, **X**) = Πi=1:N normal(**t**i|**w**, β, **x**i) và dùng hàm log là hàm monotone để chuyển thành bài toán tối ưu tương đương:
>
>
>
> maximize (over **w**, β) ln L(**w**, β|**X**,**t**) = ln {Πi=1:N normal(**t**i|y(**w**, **x**i),β)}
>
>
>
> Xét hàm objective, thay pdf normal vào:
>
>
>
> ln {Πi=1:N normal(**t**i|**w**, β, **x**i) = ln {Πi=1:N \[1/√2π(1/β) exp{-(ti - y(**w**,**x**i))^2/2(1/β)}\]}
>
>
>
> = ln {Πi=1:N \[1/√2π(1/β)\]} + ln {Πi=1:N exp{-(ti - y(**w**,**x**i))^2/2(1/β)}\]}
>
>
>
> Tới đây ta có thể giải theo **w** trước, tức là coi β như constant, từ đó chuyển thành bài toán tương đương tiếp theo bằng cách bỏ constant:
>
>
>
> maximize (over **w**) ln {Πi=1:N exp{-(ti - y(**w**,**x**i))^2/2(1/β)}\]}
>
>
>
> ⇔ maximize over **w** Σi=1:N ln {exp{-(ti - y(**w**,**x**i))^2/2(1/β)}\]}
>
>
>
> ⇔ maximize over **w** Σi=1:N \[-(ti - y(**w**,**x**i))^2/2(1/β)\]
>
>
>
> ⇔ maximize over **w** Σi=1:N \[(-β/2)(ti - y(**w**,**x**i))^2\]
>
>
>
> ⇔ maximize over **w** (-β/2) Σi=1:N \[(ti - y(**w**,**x**i))^2\]
>
>
>
> ⇔ minimize over **w** (1/2) Σi=1:N \[(ti - y(**w**,**x**i))^2\]
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
> E\[L\] = ∫∫L(t, y(**x**)) f(t,**x**) d**x** dt
>
>
>
> mà để hiểu công thức này thì phải thấy cả T và **X** đều là random variable:
>
>
>
> Và Loss = L(t, y(**x**)) = \[t - y(**x**)\]^2, thì L(**T**, y(**X**)) cũng là random variable, do đó có thể lấy kì vọng, và theo LOTUS:
>
>
>
> E\[L\] = ∫∫L(t, y(**x**)) f(t,**x**) d**x** dt
>
>
>
> = ∫∫(t - y(**x**))^2 f(t|**x**)f(**x**) d**x** dt (Bayes rule: f(t,**x**) = f(t|**x**)f(**x**))
>
>
>
> = ∫∫(y(**x**) - t)^2 f(t|**x**)f(**x**) d**x** dt
>
>
>
> cộng thêm và trừ bớt cho h(**x**) = E\[t|**x**\]
>
>
>
> = ∫∫(y(**x**) - h(**x**) + h(**x**) - t)^2 f(t|**x**)f(**x**) d**x** dt
>
>
>
> = ∫∫{\[y(**x**) - h(**x**)\]^2 +2\[y(**x**) - h(**x**)\]\[h(**x**) - t\] + \[h(**x**) - t\]^2} f(t|**x**)f(**x**) d**x**dt
>
>
>
> = ∫∫\[y(**x**) - h(**x**)\]^2 f(t|**x**) f(**x**) d**x** dt + 2∫∫\[y(**x**) - h(**x**)\]\[h(**x**) - t\]f(t|**x**) f(**x**) d**x**dt + ∫∫\[h(**x**) - t\]^2} f(t|**x**) f(**x**) d**x**dt
>
>
>
>  Xét term thứ 2: 2∫∫\[y(**x**) - h(**x**)\]\[h(**x**) - t\]f(t|**x**) f(**x**) d**x**dt
>
>
>
> Đổi chỗ d**x**, dt, tính tích phân theo t trước (1802 đã học gặp tích phân kép∫f(x,y)dxdy, thì tính tích phân theo cái nào trước cũng được vì ở đây range đều là toàn bộ mặt phẳng)
>
>
>
> = 2∫ \[∫(y(**x**) - h(**x**))(h(**x**) - t)f(t|**x**)dt\] f(**x**)d**x**
>
>
>
> Và vì đang tính tích phân theo t, ta đưa (y(**x**) - h(**x**)) không phụ thuộc t ra:
>
>
>
> = 2(y(**x**) - h(**x**)) ∫ \[∫(h(**x**) - t)f(t|**x**)dt\] f(**x**)d**x**
>
>
>
> Xét ∫(h(**x**) - t)f(t|**x**)dt, nó chính là E\[h(**x**) - T|**x**\] theo linearity = E\[h(**x**)\] - E\[T|**x**\] = E\[T|**x**\] - E\[T|**x**\] = 0.
>
>
>
> Vậy term thứ 2 = 0. Ta chỉ còn term 1, 3:
>
>
>
> ∫∫\[y(**x**) - h(**x**)\]^2 f(t|**x**) f(**x**) d**x** dt + ∫∫\[h(**x**) - t\]^2 f(t|**x**) f(**x**) d**x**dt
>
>
>
> Và đều chuyển thành tích phân của t trước, ta sẽ thấy nó là:
>
>
>
> = ∫(y(**x**) - h(**x**))^2 \[∫f(t|**x**)dt\] f(**x**)d**x** + ∫ \[∫\[h(**x**) - t\]^2 f(t|**x**)dt\] f(**x**)d**x** 
>
>
>
> ∫f(t|**x**)dt = 1 vì tính valid của pdf
>
>
>
> ∫\[h(**x**) - t\]^2 f(t|**x**)dt = E\[(h(**x**) - T)^2|**x**\]
>
>
>
> = ∫(y(**x**) - h(**x**))^2 f(**x**)d**x** + ∫ \[∫\[h(**x**) - t\]^2 f(t|**x**)dt\] f(**x**)d**x** 
>
>
>
> Đưa ∫ \[∫\[h(**x**) - t\]^2 f(t|**x**)dt\] f(**x**)d**x** trở lại thành ∫∫\[h(**x**) - t\]^2 f(t,**x**)d**x** dt
>
>
>
> Kết qủa ta có ∫(y(**x**) - h(**x**))^2 f(**x**)d**x** + ∫∫\[h(**x**) - t\]^2 f(t,**x**)d**x** dt → Đây chính là 3.37
>
>
>
> Dừng chút để nhận định lạ: Có nghĩa là square error xuất hiện ở 3 case khác nhau:
>
>
>
> Trong case 1: Khi có T \~ f(t|**x**), thì h(**x**) = E\[T|**x**\] sẽ minimize E\[L(h(**x**), T)\] với T\~f(**x**|t), L(h(x), T) = (h(**x**) - T)^2
>
>
>
> Trong case 2: Khi assume noise ε \~ n(0, 1/β) cũng là T \~ n(y(**w**,**x**), 1/β), thì **w**ML chính là minimizer của ln L(**w**|**X**,**t**,β) ≡ (1/2) Σi=1:N \[y(**w**, **x**i) - ti\]^2, là sum squared error.
>
>
>
> Trong case 3: Khi ta xét Loss của bài toàn regression: L(y(**X**), T) = \[y(**X**) - T\]^2, là một random variable (hàm của random variable **X** và T), và xét kì vọng của nó: E\[L\] = ∫∫ L(y(**x**), t) f(**x**, t) d**x** dt và triển khai ra ta có E\[L\] = ∫(y(**x**) - h(**x**))^2 f(**x**)d**x** + ∫∫\[h(**x**) - t\]^2 f(t,**x**)d**x** dt
>
>
>
> Điểm giống nhau của 1, và 3: Đều là trong bối cảnh decision theory, khi ta xét expected loss. Để rồi trong 1), minimize expected loss thì ta sẽ có h(**x**) = E\[T|**x**).
>
>
>
> Còn trong 3, ta cũng muốn (tìm y(**x**) để minimize E\[L\] thì ta sẽ thấy bài toán sẽ ≡ mininimize ∫(y(**x**) - h(**x**))^2 f(**x**)d**x** và kết quả sẽ cho solution y(**x**) = h(**x**)(tức = E\[T|**x**\]), cũng chính là quay lại bài toán nếu ta có predictive distribution: f(t|**x**) thì point estimator tối ưu cho T chính là E\[T|**x**\].
>
>
>
> Và ý chính gs Bishop muốn nói: Đi tìm f(t|**x**) (chính là ví dụ như khi mình tìm **w**ML) thì không nhất thiết ta phải dùng MLE, mà có thể dùng các các tiếp cận khác như fully Bayesian. Còn khi đã có f(t|**x**), thì theo decision theory, point estimation tối ưu cho T khi dùng squared loss là E\[T|**x**\]
>
>
>
> ---
>
>
>
> Tiếp tục, đoạn ghi chú màu xanh cũng là nói ý trên: Để tìm y(**x**) minimize E\[L\] thì chỉ tương đương tìm y(**x**) minimize term 1, vì term 2 không phụ thuộc y, và vì nó không âm nên mininimize khi y(**x**) = h(**x**) như nói trên.
>
>
>
> Vậy vì sao ông nói term 2 xuất phát từ noise nội tại (intrisic) và đại diện cho phần ko thể giảm được nữa, cũng là cái nhỏ nhất mà E\[L\] có thể đạt được (ý là với y\*(**x**), tối ưu) thì chỉ có thể giúp term 1 bằng 0, và E\[L} vẫn còn term 2?
>
>
>
> Là vì: xem xét, ∫∫\[h(**x**) - t\]^2 f(t,**x**)d**x** dt, thay h(x) = E\[T|**x**\]:
>
>
>
> = ∫∫\[t - E\[T|**x**\]\]^2 f(t,**x**) d**x** dt
>
>
>
> = ∫∫\[t - E\[T|**x**\]\]^2 f(t|**x**) f(**x**) d**x** dt
>
>
>
> = ∫∫\[t - E\[T|**x**\]\]^2 f(t|**x**) dt f(**x**) d**x**
>
>
>
> Xét riêng cụm này: ∫\[t - E\[T|**x**\]\]^2 f(t|**x**) dt, nó chính là Var\[T|**x**\], tức Var(T) với T \~ f(T|**x**). Và như vậy:
>
>
>
> ∫∫\[t - E\[T|**x**\]\]^2 f(t|**x**) dt f(**x**) d**x** = ∫ Var\[T|**x**\] f(**x**) d**x**
>
>
>
> và như vậy, nó chính là đến từ **mức biến động nội tại của data**, không phải sao? vì bản chất là T **đã có mức biến động nội tại nào đó**, chính là **thể hiện thông qua variance** của f(t|**x**), mà trong bài toán đi tìm y(**x**) tối ưu, ta sẽ không để can thiệp làm giảm cái phần loss do variance của T này. Ví dụ nôm na là: cho trước x, thì T có distribution n(μ, σ^2), thì khi y(x, **w**) = μ = E\[T|**x**) thì ta đã làm tốt nhất rồi (còn lại cái phần loss do variance của T thì chịu, không thêm làm gì khác).
>
>
>
> ---
>
>
>
> Và ở đoạn cuối cùng, mình hiểu ý gs Bishop như vầy: Xét cái term 1, là cái thứ ta có thể minimize được bằng cách tìm ra y(**x**) tốt nhất, và tốt nhất ở đây chính là h(**x**) = E\[T|**x**\]. Có nghĩa là, ví dụ như dùng linear modal đi, y(**x**) = **w**T Φ(**x**), thì nếu ta có thể tìm ra **w**\* sao cho **với mọi** **x thì w**\*TΦ(**x**) = E\[T|**x**\], thì ta sẽ có term 1 = 0.
>
>
>
> Tuy nhiên, vấn đề là, ta chỉ có thể làm vậy nếu như có vô hạn data và **vô hạn sức mạnh tính toán**, trong khi đó, data ta có chỉ là hữu hạn, sức mạnh tính toán cũng vậy. Nên thực tế sẽ rất khó để tìm ra chính xác hành vi của hàm số h(**x**) = E\[T|**x**\] / cũng chính là nói : rất khó để mô phỏng chính xác hàm h(**x**) = E\[T|**x**\]. Dẫn tới là term 1 sẽ luôn &gt; 0.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Bài ghi chú này cực kỳ chính xác và chi tiết, thể hiện sự hiểu biết sâu sắc về các khái niệm phức tạp về squared loss trong lý thuyết quyết định, MLE và phân tách kỳ vọng mất mát. Phần giải thích các công thức và ý nghĩa của từng thành phần đều xuất sắc, đặc biệt là cách bạn làm rõ sự khác biệt và mối liên hệ giữa các trường hợp. Bạn cũng giải thích đúng tác động của dữ liệu hữu hạn lên việc tìm hàm hồi quy tối ưu. Đây là một phân tích mẫu mực.

**🔗 See also:** [Optimal Least Squares Predictor](./15_decision_theory.md#node-3ve6hfk)

<br>

<a id="node-mqes87t"></a>

