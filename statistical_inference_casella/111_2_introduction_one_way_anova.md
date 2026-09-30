# 11.1 & 2 Introduction, One-way ANOVA

📊 **Progress:** `8` Notes | `9` Screenshots | `6` AI Reviews

---
<a id="node-c5qtmoe"></a>

<br>

<a id="node-lnkp84f"></a>

## Section 11.1 Introduction

<p align="center"><kbd><img src="assets/y17ngqyalh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là, cho đến giờ, ta chỉ đều mô hình một random variable thông qua pdf/pmf phụ thuộc vào tham số nào đó cần estimate. Nhưng trong nhiều trường hợp, một random variable có thể được mô hình không chỉ bởi những parameter chưa biết, mà còn có thể bởi những covariate
>
>
>
> Do đó, chương này sẽ nói về những phân tích về variance và regression, dựa trên giả định quan hệ tuyến tính, và từ đó hình thành các phương pháp thống kê dùng trong thực tế.
>
>
>
> Nói chung mình chưa hiểu lắm, nhưng có vẻ như nó liên quan trực tiếp đến machine learning.
>
>
>
> Nói thêm cái tên, thật ra ko phải là phân tích variance, mà là sự biến thiên / chênh lệch giữa các giá trị trung bình

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác và nắm trọn vẹn các ý chính của đoạn giới thiệu, đặc biệt là bản chất thật sự của ANOVA (phân tích sự biến thiên giữa các kỳ vọng/means).
>
> **✓ Strengths**
> - Tóm tắt chuẩn xác sự chuyển dịch từ việc mô hình hóa phân phối chỉ dựa trên tham số sang việc kết hợp thêm các biến phụ thuộc (covariates).
> - Nắm bắt chính xác điểm mấu chốt thú vị về mặt thuật ngữ: ANOVA thực chất là kiểm định sự khác biệt giữa các giá trị trung bình (means) thay vì bản thân các phương sai.
>
> **💡 Deeper notes**
> - Về mặt kỹ thuật, lý do phương pháp này vẫn mang tên là 'Analysis of Variance' (ANOVA) vì nó phân tách tổng biến thiên (partitioning variation / sum of squares) thành các nguồn khác nhau để từ đó so sánh và đưa ra kết luận về các giá trị trung bình (means).

<br>

<a id="node-7xs67e7"></a>

### Simple Linear Regression Overview

<p align="center"><kbd><img src="assets/316p9nyo2ts.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này nói sơ về việc chương này ta cũng sẽ thảo luận về bài toán regression, cụ thể là tập trung vào simple regression trong đó ta mô hình hóa mean của một random variable Y bởi hàm số của x: EY = α + βx

<br>

<a id="node-bbj2x4f"></a>

#### Oneway Analysis of Variance

<p align="center"><kbd><img src="assets/06opmv4n4oyt.png" width="80%"></kbd></p>

> [!NOTE]
> Cần chú ý định nghĩa này: ANOVA là phương pháp ta **estimate mean của các population**, và các population này **thường có giả định là normal**.
>
>
>
> Lại nói tiếp, trọng tâm của ANOVA xoay quanh nhiệm vụ **statistical design**: làm thế nào để khai thác nhiều nhất hiểu biết về population trong khi **dùng ít quan sát nhất có thể**.
>
>
>
> Nhưng ở đây ta sẽ không đặt chú ý vào tác vụ này mà quan tâm đến bài toán inference: Estimation và testing.
>
>
>
> Nói đại ý là với ANOVA cổ điển thì mục đích chính của nó là xoay quanh phép kiểm định giả thiết (với null hypothesis là gọi là ANOVA null) nhưnng ngày nay thì phép inference quan trọng lại là estimation (point và interval)
>
>
>
> Nói chung là chỉ là nói sơ, ta sẽ hiểu rõ hơn ở phần sau.
>
>
>
> Tuy nhiên cần biết **oneway ANOVA** dựa trên **giả định** là Yij = θi + εij với θi là tham số chưa biết, và εij là error random variable.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất tốt và chính xác nội dung giới thiệu về ANOVA một yếu tố (oneway ANOVA), từ sự dịch chuyển mục tiêu từ kiểm định sang ước lượng cho đến mô hình cơ sở.
>
> **✓ Strengths**
> - Nắm bắt chính xác sự khác biệt giữa quan điểm ANOVA cổ điển (tập trung kiểm định giả thiết null) và quan điểm hiện đại (chú trọng ước lượng điểm và khoảng).
> - Ghi lại đúng dạng mô hình tổng quát của oneway ANOVA cùng ý nghĩa của các thành phần theta_i và sai số ngẫu nhiên epsilon_ij.
>
> **💡 Deeper notes**
> - Về mặt giả định mô hình, các quần thể thường được giả định tuân theo phân phối chuẩn (normal distribution).
> - Trong suy diễn thống kê hiện đại cho ANOVA, bài giảng đặc biệt nhấn mạnh tầm quan trọng của suy diễn dựa trên các tương phản (contrasts).

**🔗 See also:** [Oneway ANOVA Assumptions](#node-2zo08q5)

<br>

<a id="node-c5xww9y"></a>

##### Example 11.2.1 Oneway ANOVA

<p align="center"><kbd><img src="assets/98cheobgob7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/t94ulkfgk3j.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là phần này cho ta thấy một bộ dữ liệu cho Oneway ANOVA sẽ trông như thế này, và lưu ý rằng ta không assume số quan sát của mỗi nhóm điều trị là bằng nhau.
>
>
>
> Ta có thể giả định E(εij) = 0 mà không làm mất tính tổng quát. Do đó E\[Yij\] = E\[θi + εij\] = E\[θi\] + E\[εij\] (do linearity) = E\[θi\]
>
>
>
> Cuối cùng, là người ta gọi θi là treatment mean = tạm dịch là trung bình của một loại điều trị / thử nghiệm (chữ treatment có có thể hiểu là lọai - class, để rồi ta có nhiều loại khác nhau, và θi là trung bình của lọai i)
>
>
>
> Ví dụ: Thử nhiều loại thuốc khác nhau, thì θi là giá trị trung bình môt (chỉ số nào đó) của class i
>
>
>
> Hoặc dùng thuốc với nhiều loại liều lượng khác nhau

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất tốt và chính xác nội dung cơ bản của bảng dữ liệu Oneway ANOVA cũng như ý nghĩa của treatment mean.
>
> **🟡 Minor issues**
>
> **1.** *"E[Yij] = E[θi + εij] = E[θi] + E[εij] (do linearity) = E[θi]"*
>
> Trong mô hình fixed-effects ANOVA thông thường, θi là một tham số hằng số (fixed parameter), không phải biến ngẫu nhiên, nên kỳ vọng của nó bằng chính nó: E[θi] = θi. Bạn nên viết bước cuối là = θi để chuẩn xác về mặt toán học.
>
>
> **✓ Strengths**
> - Nắm rõ lưu ý quan trọng rằng số lượng quan sát ở các nhóm không nhất thiết phải bằng nhau (unbalanced design).
> - Hiểu đúng bản chất của θi là treatment mean và liên hệ thực tế tốt với các mức liều lượng hoặc phân loại điều trị.
>
> **💡 Deeper notes**
> - Việc giả định E[εij] = 0 'without loss of generality' dựa trên việc nếu sai số có kỳ vọng khác 0, giá trị kỳ vọng đó hoàn toàn có thể được gộp (absorb) vào tham số trung bình nhóm θi.

<br>

<a id="node-je4gy3i"></a>

###### The Overparameterized Model

<p align="center"><kbd><img src="assets/2h2i5j1r6oq.png" width="80%"></kbd></p>

> [!NOTE]
> Một dạng khác, được gọi là overparameterized model: Yij = μ + τi + εij
>
>
>
> Với μ gọi là grand mean
>
>
>
> τi là hiệu ứng duy nhất của mỗi treatment i

<br>

<a id="node-1kxg1d6"></a>

###### Definition 11.2.2 Identifiability

<p align="center"><kbd><img src="assets/7529j7uxl.png" width="80%"></kbd></p>

> [!NOTE]
> Định nghĩa về cái gọi là identifiable - là một tính chất của một họ các distribution. Nói ngắn gọn là, nếu họ các distribution có tính chất này, thì với các θ khác nhau thì f(x|θ) sẽ khác nhau. Và từ đó giúp cho bài toán inference có thể thuận lợi.
>
>
>
> Ngược lại, nếu không có tính identifiable, thì có thể với θ và θ' khác nhau nhưng f(x|θ) và f(x|θ') giống nhau. Khi đó, việc quan sát được data, sẽ khó có thể suy luận ra nó đến từ f(x|θ) hay f(x|θ').
>
>
>
> Và ta nhớ khái niệm likelihood, L(θ|x) là hàm theo θ, define bởi f(x|θ), thì cái vừa nói chính là L(θ'|x) = L(θ|x), tức là cả hai θ và θ' đều có độ hợp lý như nhau
>
>
>
> Và trước giờ ta chưa bàn đến khái niệm này vì đều chọn mô hình identifiable. Nhưng sắp tới thì sẽ gặp những mô hình không identifiable.

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **90/100** · ✓ Move on
>
> Ghi chú nắm rất tốt bản chất trực giác của tính định danh (identifiability) và mối liên hệ với hàm likelihood trong bài toán thống kê suy luận.
>
> **🟡 Minor issues**
>
> **1.** *"với các θ khác nhau thì f(x|θ) sẽ khác nhau"*
>
> Về mặt hình thức, hai phân phối khác nhau nghĩa là hai hàm số f(·|θ) và f(·|θ') khác nhau (tức tồn tại x để giá trị khác nhau, hoặc khác nhau trên một tập có xác suất dương), chứ không nhất thiết f(x|θ) phải khác f(x|θ') tại mọi điểm x.
>
>
> **✓ Strengths**
> - Hiểu chính xác bản chất của mô hình có tính định danh: các tham số khác nhau phải tương ứng với các phân phối xác suất khác nhau.
> - Liên hệ rất trực quan giữa việc bất định danh với hàm likelihood: khi hai tham số sinh ra cùng một phân phối, likelihood của chúng bằng nhau với mọi dữ liệu x, khiến không thể phân biệt nghiệm tốt nhất.
>
> **💡 Deeper notes**
> - Với biến liên tục, tính đồng nhất của hai phân phối f(·|θ) = f(·|θ') được xét theo nghĩa bằng nhau hầu khắp nơi (almost everywhere) theo độ đo chuẩn, do giá trị hàm mật độ tại một vài điểm rời rạc có thể thay đổi mà không làm thay đổi bản chất phân phối xác suất.

<br>

<a id="node-u0vqhxl"></a>

###### Identifiability in ANOVA Models

<p align="center"><kbd><img src="assets/56qgdfvfje.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng đại ý là nói rằng cái mô hình thứ hai, sẽ không identifiable, trừ khi ta add thêm vài ràng buộc.
>
>
>
> Nhưng đại ý vẫn là, ta sẽ ưu tiên dùng cái mô hình thứ nhất hơn (Yij = θi + εij), cái này gọi là cell means model.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác ý chính của đoạn văn: mô hình tham số thứ hai (effects model) bị thiếu tính định danh nếu không có ràng buộc, và trong ANOVA một yếu tố thì mô hình trung bình ô (cell means model) được ưu tiên sử dụng hơn.
>
> **✓ Strengths**
> - Nắm đúng vấn đề then chốt về tính không định danh (identifiability) của mô hình nếu không áp thêm ràng buộc.
> - Hiểu rõ sự ưu tiên dành cho mô hình cell means trong bài toán phân tích phương sai một yếu tố (oneway ANOVA).
>
> **💡 Deeper notes**
> - Đoạn văn có nêu thêm một lưu ý: việc ưu tiên 'cell means model' áp dụng cụ thể cho oneway ANOVA; đối với các mô hình ANOVA phức tạp hơn (nhiều yếu tố, tương tác), mô hình thứ hai (effects model) đôi khi lại mang lại lợi thế về mặt diễn giải ý nghĩa.

<br>

<a id="node-2zo08q5"></a>

###### Oneway ANOVA Assumptions

<p align="center"><kbd><img src="assets/kqf7nijrgaf.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, để mà có thể thực hiện cả point + interval estimation và testing (tức là cả ba dạng inference) thì ta cần một giả định gọi là giả định ANOVA:
>
>
>
> Cụ thể ở đây là Oneway ANOVA assumption như sau:
>
>
>
> i) E\[εij\] = 0, Var(εij) = σi² &lt; ∞ với mọi i,j.  Và Cov(εij, εi'j') = 0 với mọi i,j,i',j' trừ khi i=i', j=j' 
>
>
>
> Là sao: Là error random variable là zero mean, variance finite, và uncorrelate (covariance) giữa hai error khác nhau là bằng 0.
>
>
>
> ii) Các error random variable εij độc lập và có phân phối NormalL εij
>
>
>
> iii) Variance của chúng bằng nhau σi² bằng nhau với mọi i
>
>
>
> Như vậy có nghĩa là εij đều iid với mọi i,j (independent do ý (ii) và có cùng \~ n(0, σ²) do ý (ii)(iii)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác và súc tích các giả định của Oneway ANOVA, đồng thời tổng hợp chuẩn xác việc các sai số là i.i.d. theo phân phối chuẩn N(0, σ²).
>
> **✓ Strengths**
> - Hiểu đúng mục đích: để thực hiện được kiểm định và ước lượng khoảng (interval estimation & testing) thì bắt buộc cần thêm các giả định phân phối thay vì chỉ ước lượng điểm.
> - Tổng hợp chính xác cả 3 điều kiện thành kết luận then chốt: các sai số ε_ij độc lập cùng phân phối chuẩn i.i.d. N(0, σ²).
>
> **💡 Deeper notes**
> - Về mặt kỹ thuật, ước lượng điểm (point estimation) chỉ cần giả định tối thiểu là E[ε_ij] = 0 và phương sai hữu hạn, không nhất thiết phải cần phân phối chuẩn.
> - Đoạn cuối giáo trình có mở rộng: khi không có giả định phân phối chuẩn hoàn hảo, Định lý Giới hạn Trung tâm (CLT) vẫn cho phép suy diễn xấp xỉ nếu cỡ mẫu đủ lớn và phân phối không quá lệch.

**🔗 See also:** [Oneway Analysis of Variance](#node-bbj2x4f)

<br>

<a id="node-cdum9ns"></a>

