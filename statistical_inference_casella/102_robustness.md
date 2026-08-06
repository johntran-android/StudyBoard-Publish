# 10.2 Robustness

📊 **Progress:** `3` Notes | `3` Screenshots | `3` AI Reviews

---
<a id="node-wah0nty"></a>

## 10.2 Robustness

<p align="center"><kbd><img src="assets/kmefret33e.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là gs cho biết, khi xây dựng estimator, ta đã luôn dựa trên một giả định về dạng của distribution. Ví dụ, cho random sample size n X1,...Xn có observed value x1,...xn, có population distribution f(x|θ), thì để bắt đầu đi xây dựng estimator của θ (theo MLE hay Bayes approach) thì đầu tiên ta phải giả định f có dạng phân phối gì cái đã. Ví dụ như normal(μ, σ^2), rồi từ đó mới đi derive (μ)ml và (σ^2)ml.
>
>
>
> Thế thì vì lí do đó, nên mới nói là khi ta đi evaluate chất lượng của một estimator, thì dĩ nhiên sự đánh giá này cũng đang dựa trên giả định trên. Mà giả định thì có thể sai. Cho nên ý chính muốn nói là, giả sử ta tìm ra W1(**X**) là một estimator rất tốt cho θ, và nó là cái tốt nhất, nên nó ngon hơn W2(**X**) Nhưng hóa ra giả định là sai, mà sự thật là, nếu dựa trên giả định đúng, thì W2(X) mới là cái tốt hơn.
>
>
>
> Như vậy, từ vấn đề này (chất lượng của estimator đang dựa trên giả định ban đầu nào đó về dạng của population distribution), nên người ta mới đặt vấn đề: Liệu có thể hi sinh chút xíu tính chất tối ưu của một estimator, nhưng tăng thêm tính chất khác: Đó là, nếu giả định sai, thì ta sẽ bớt bị ảnh hưởng hơn.
>
>
>
> Có nghĩa là, ta đặt ra một tính chất mới mà ta mong muốn ở estimator: Đó là mức độ chống chịu của nó khi giả định ban đầu là sai.
>
>
>
> Vậy hình dung thế này, W1(**X**), như đã nói, là cái tốt nhất dựa trên các tiêu chí tối ưu, và cái W2(**X**) chỉ xếp sau. Tuy nhiên, nếu giả định là sai, thì estimate của W1(**X**) là thảm họa, tụt dốc không phanh, trong khi đó, nếu giả định là sai, thì W2(**X**) vẫn là một estimator không đến nỗi nào. Khi đó, người ta sẽ cân nhắc việc dùng W2(**X**) thay vì W1(**X**), và như vậy, ta hi sinh chút tính chất optimality nhưng đổi lại được tính chất "chống chọi với giả định sai". Và tính chất này, người ta gọi là Robustness.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Your explanation is exceptionally clear and uses fantastic, concrete examples comparing W1 and W2 to perfectly capture the trade-off between optimality and robustness. To make it even more precise, you could note that robust estimators specifically guard against small-to-medium deviations from the assumed model rather than any complete model failure.

<br>

<a id="node-xdhfotf"></a>

## Huber's Criteria for Robustness

<p align="center"><kbd><img src="assets/bkhgj3ek6x.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là ba cái ý này nó sẽ mô tả cho cái tính chất robustness. 
>
>
>
> Thứ nhất đó là nó nên có một cái độ hiệu quả tương đối tốt. Mà độ hiệu quả, tức là efficiency đó, thì theo mình đoán hoặc là theo mình nhớ một cái khái niệm mà mình đã học ở trong cái phần 10.1, nó gọi là asymptotically efficient, tức là hiệu quả tiệm cận. Tức là khi mà số lượng mẫu tăng lên vô hạn thì phương sai của cái estimator nó sẽ giảm về cái mốc nhỏ nhất (CRLB) Nói chung là cái mức biến động sẽ nhỏ đi khi mà tăng số lượng mẫu lên. Vậy thì có thể hiểu ý một đó là nó phải đủ tốt, nó phải có một cái độ tốt tương đối, reasonably good. 
>
>
>
> Cái thứ hai mới quan trọng, đó là cái tính chất robust nó sẽ phải thể hiện ở chỗ này. Đó là một cái sự deviation nhỏ, một cái sự biến động chút xíu trong cái giả định ban đầu, có nghĩa là nó không còn đúng, tức là nó không chính xác, cái giả định ban đầu nó hơi sai, thì một robust estimator phải không bị ảnh hưởng mấy, thể hiện qua cái cụm là impair the performance only slightly, tức là cái sự sai lệch nhỏ trong cái giả định của ban đầu nó chỉ ảnh hưởng nhỏ đến cái estimator thôi. 
>
>
>
> Và ý thứ ba đó là ngay cả một cái sự sai lệch lớn, ví dụ như ban đầu giả định như vậy nhưng mà nó sai hoàn toàn, thì đối với một cái robust estimator đó, cái điều đó nó không ảnh hưởng đến mức gây ra thảm họa. Thì ba cái ý đó nó chính là mô tả cho một cái khái niệm là robustness.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú phân tích rất xuất sắc và có chiều sâu khi liên hệ chính xác khái niệm 'efficiency' với tính hiệu quả tiệm cận (asymptotic efficiency) và CRLB. Để hoàn thiện hơn, bạn có thể lấy thêm ví dụ thực tế (như trung vị vs trung bình khi có outliers) để minh họa trực quan cho ý (2) và (3).

<br>

<a id="node-3pctii6"></a>

### Robustness of the Sample Mean

<p align="center"><kbd><img src="assets/8286i3qtyc3.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi đặt ra là, sample mean Xbar (như đã biết, là một trong những estimator quan trọng nhất) có roburst không. Thì gs nói rằng để trả lời, ta phải có thước đo độ robusrt mới được.
>
>
>
> Lấy ví dụ ta có X1,...Xn iid \~ normal(μ, σ^2), thì đại khái là, như ta còn nhớ, với Xbar, thì ta có công thức cho variance của nó: Var(Xbar) = populaton variance/n, và ở đây, với population variance là σ^2 thì Var(Xbar) = σ^2/n (chú ý, công thức này, đúng với cả các population khác)
>
>
>
> Và gs nói đây chính là CRLB. tức giới hạn phương sai nhỏ nhất mà Variance của một estimator có thể có, do đó, nó thỏa tiêu chí 1): Bản thân robust estimator là một estimator hiệu quả (hoặc ít nhất là tương đối tốt)
>
>
>
> Ở đây mình có thể tranh thủ ôn lại về CRLB để xem vì sao σ^2/n lại là CRLB?
>
>
>
> CRLB theorem nói rằng, với W(**X**), là estimator thỏa điều kiện (xem trong link của theorem) thì ta có:
>
>
>
> Var(W(**X**)) ≥ \[∂/∂θ Eθ\[W(**X**)\]^2 / nI1(θ)
>
>
>
> với I1(θ) là information number hay Fisher information  của sample size 1.
>
>
>
> Áp dụng vào đây, W(**X**) là Xbar
>
>
>
> Eθ\[W(**X**)\] = Eμ\[W(**X**)\] = μ ⇒ d/dμ Eμ\[W(**X**)\] = 1
>
>
>
> I1(θ) = E\_θ\[(∂/∂θ log f(X|θ))^2\]:
>
>
>
> log f(X|θ) = log \[1/√(2πσ^2) exp {-(X-μ)^2/2σ^2}
>
>
>
> = log \[1/√(2πσ^2)\] + log exp {-(X-μ)^2/2σ^2}
>
>
>
> = log \[1/√(2πσ^2)\] - (X-μ)^2/2σ^2
>
>
>
> ⇒ ∂/∂θ log f(X|θ) = ∂/∂μ \[log \[1/√(2πσ^2)\] - (X-μ)^2/2σ^2\]
>
>
>
> = ∂/∂μ \[-(X-μ)^2/2σ^2\]
>
>
>
> = (-1/2σ^2) ∂/∂μ \[(X-μ)^2\]
>
>
>
> = 2(1/2σ^2) (X-μ)
>
>
>
> = (X-μ)/σ^2 
>
>
>
> ⇒ (∂/∂θ log f(X|θ))^2 = (X-μ)^2/σ^4 
>
>
>
> ⇒ E\_θ\[(∂/∂θ log f(X|θ))^2\] = E\_θ\[(X-μ)^2/σ^4\]
>
>
>
> = E\_θ\[(X-μ)^2\]/σ^4
>
>
>
> = Var(X)/σ^4
>
>
>
> = σ^2/σ^4
>
>
>
> = 1/σ^2
>
>
>
> Vậy CRLB ở đây = \[∂/∂θ Eθ\[W(**X**)\]^2 / nI1(θ) = 1/n(1/σ^2)
>
>
>
> = σ^2/n
>
>
>
> Như vậy đúng là Var(Xbar) đạt Cramer Rao Lower Bound.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú rất xuất sắc và chi tiết khi bạn đã chủ động tự chứng minh lại định lý Cramer-Rao Lower Bound để làm rõ ví dụ trong sách. Có một lỗi nhỏ về dấu ở bước trung gian khi lấy đạo hàm theo $\mu$, nhưng kết quả biến đổi cuối cùng vẫn hoàn toàn chính xác.

**🔗 See also:** [Bất đẳng thức Cramer-Rao](./73_methods_of_evaluating_estimators.md#node-1qs416c) · [Giới hạn dưới Cramer-Rao](./73_methods_of_evaluating_estimators.md#node-ihoar4m)

<br>

