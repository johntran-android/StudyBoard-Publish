# 4.3.3 Iterative reweighted least squares

📊 **Progress:** `1` Notes | `2` Screenshots | `1` AI Reviews

---
<a id="node-89ydraa"></a>

<br>

<a id="node-q3zyd3g"></a>

## Iterative Reweighted Least Squares

<p align="center"><kbd><img src="assets/s7lsn2zoqyh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý đoạn này nói rằng trong linear regression ở chapter 3, với giả định Gaussian noise thì bài toán tìm MLE trở nên có closed form solution, mà nguyên chủ yếu là do hàm log likelihood là hàm bậc hai của 𝐰, thành ra khi đạo hàm và cho bằng 0 (điều kiện cần bậc nhất) ta có phương trình tuyến tính theo 𝐰 để rồi có thể có công thức nghiệm (closed form solution)
>
>
>
> Review nhanh sẽ thấy ý này:
>
>
>
> Trong bài toán đó, ta giả định Ti|𝐱i \~ 𝒩(y(𝐱i, 𝐰), 1/β) (cũng là εi = Ti-y(𝐱i, 𝐰) \~ 𝒩(0,1/β)). Nên likelihood L(𝐰, β|t1,..tn, 𝐱1,...𝐱n) = L(𝐰, β|𝐭, 𝐗) = f(𝐭|𝐰,β,𝐗) = Πi f(ti|𝐰, β, 𝐱i) = Πi 𝒩(ti|𝐰ᵀΦ(𝐱i), 1/β) = Πi \[constant\] exp\[(-β/2)(ti-𝐰ᵀΦ(𝐱i))²\].
>
>
>
> Từ đó ln likelihood = ln Πi \[c1\] exp\[(-β/2)(ti-𝐰ᵀΦ(𝐱i))²\]
>
>
>
> = Σi ln {\[c1\] exp\[(-β/2)(ti-𝐰ᵀΦ(𝐱i))²\]}
>
>
>
> = Σi ln {\[c1\]} + Σi ln exp\[(-β/2)(ti-𝐰ᵀΦ(𝐱i))²\]}
>
>
>
> = c2 - (β/2) Σi (ti-𝐰ᵀΦ(𝐱i))², là hàm bậc hai theo 𝐰
>
>
>
> ---
>
>
>
> Thì ở logistic regression, tác giả Bishop nói ta không còn có thể có closed form solution nữa, mà nguyên nhân là do tính phi tuyến của hàm sigmoid.
>
>
>
> Tuy nhiên ta sẽ thấy đại khái là ở bài toàn này, vẫn có unique solution do hàm error negative ln likelihood là concave function (có lẽ sách in sai, vì là hàm convex mới đúng chứ nhỉ) mà ta sẽ sớm chứng minh.
>
>
>
> ---
>
>
>
> Tiếp theo, đại ý là, như note trước mình đã dự đoán, ta sẽ giải tìm solution thông qua thuật toán tối ưu, mang tên Newton-Raphson, vốn dựa trên việc ta xấp xỉ bậc hai hàm hàm ln likelihood, mà bước update có dạng như sau:
>
>
>
> 𝐰(new) = 𝐰(old) - 𝐇⁻¹ ∇E(𝐰) với 𝐇 là Hessian.
>
>
>
> Nhờ đã học Nocedal và Boyd, nên mình nhận ra đây (- 𝐇⁻¹ ∇E(𝐰)) chính là Newton step, và cái này chỉ là Newton method thôi có gì lạ đâu.
>
>
>
> Active recall chỗ này (đây là lúc mà thời gian cày Nocedal và Boyd trả lãi):
>
>
>
> Nguyên lý rất đơn giản: Ta có hàm objective f(𝐱) là hàm muốn minimize, và bài toán này không có ràng buộc. Vấn đề là f(𝐱) là hàm phi tuyến phức tạp, để rồi nếu dùng điều kiện cần bậc nhất, ta sẽ có ∇f(𝐱) = 0 là một hệ phương trình phi tuyến phức tạp không giải nổi. Thì thuật toán iterative này giải bài toán này với nguyên lý như sau:
>
>
>
> Bắt đầu tại 𝐱0 nào đó, ta sẽ "coi hàm f(𝐱) hành xử như hàm bậc hai", và theo đó, ta đi đến điểm giúp minimize hàm bậc hai này. Đây cũng chính là cách nói khác của: Ta không dùng hàm f(𝐱), mà dùng g(𝐱) là hàm xấp xỉ bậc hai của f(𝐱) tại 𝐱0:
>
>
>
> f(𝐱) ≈ g(𝐱) = f(𝐱0) + ∇f(𝐱0)ᵀ(𝐱-𝐱0) + (1/2)(𝐱-𝐱0)ᵀ∇²f(𝐱0)(𝐱-𝐱0)
>
>
>
> Đổi biến sang 𝐝 = 𝐱 - 𝐱0, ta có hàm g(𝐝) = f(𝐱0) + ∇f(𝐱0)ᵀ𝐝 + (1/2)𝐝ᵀ∇²f(𝐱0)𝐝
>
>
>
> (Với h(𝐱) = (1/2)𝐱ᵀ𝐏𝐱 + 𝐪ᵀ𝐱 + r
>
>
>
> Thì gradient ∇h(𝐱) = 𝐏ᵀ𝐱 + 𝐪, ∇²h(𝐱) = 𝐏)
>
>
>
> Và ta sẽ đi giải bài toán subproblem: minimize\_𝐝 g(𝐝)
>
>
>
> Và đây là hàm bậc hai theo 𝐝, nên chỉ việc theo điều kiện cần bậc nhất:
>
>
>
> ∇g(𝐝) = 0
>
>
>
> ⇔ \[∇²f(𝐱0)\]ᵀ𝐝 + ∇f(𝐱0) = 0
>
>
>
> ⇔ \[∇²f(𝐱0)\]ᵀ𝐝 = -∇f(𝐱0)
>
>
>
> ⇔ ∇²f(𝐱0)𝐝 = -∇f(𝐱0)
>
>
>
> ⇔ 𝐝 = -\[∇²f(𝐱0)\]⁻¹ ∇f(𝐱0)
>
>
>
> Đây chính là Newton step.
>
>
>
> Và như vậy từ 𝐱0, ta nhảy đển 𝐱1 = 𝐱0 -\[∇²f(𝐱0)\]⁻¹ ∇f(𝐱0). Và lặp lại các bước này.
>
>
>
> ---
>
>
>
> Áp vào đây, hàm objective f(𝐰) ở đây là - ln likelihood, hay cross entropy E(𝐰)
>
>
>
> Nên Newton step để update từ 𝐰0 sang 𝐰1 sẽ là -\[∇²E(𝐰)\]⁻¹ ∇E(𝐰0):
>
>
>
> 𝐰1 = 𝐰0 -\[∇²E(𝐰0)\]⁻¹ ∇E(𝐰0)
>
>
>
> Hay viết gọn là 𝐇(𝐰0), Hessian của hàm E(𝐰) tại 𝐰0, để có:
>
>
>
> 𝐰1 = 𝐰0 -\[𝐇(𝐰0)\]⁻¹ ∇E(𝐰0)
>
>
>
> Do đó 4.92 phải hiểu là Hessian và gradient ∇E tại 𝐰(old)

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=yOm1k_DQ3K0)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú xuất sắc, hiểu sâu sắc bản chất vấn đề từ hồi quy tuyến tính sang hồi quy logistic, tự suy diễn chuẩn xác phép xấp xỉ Taylor bậc hai cho thuật toán Newton-Raphson và phát hiện rất tinh tế lỗi in sai thuật ngữ (concave/convex) trong sách của Bishop.
>
> **✓ Strengths**
> - Tái hiện chính xác cơ chế vì sao log-likelihood của Linear Regression lại có nghiệm closed-form (do phụ thuộc bậc hai theo tham số w).
> - Phát hiện rất chuẩn xác lỗi in ấn trong sách gốc Bishop khi viết 'error function is concave' thay vì 'convex' để có unique minimum (lỗi này đã được Bishop đính chính trong errata chính thức).
> - Trình bày chi tiết, mạch lạc bản chất của phương pháp Newton-Raphson từ khai triển Taylor bậc 2 và bài toán tối ưu xấp xỉ cục bộ (quadratic model subproblem).
>
> **💡 Deeper notes**
> - Khi giải bước Newton d = -[∇²f(x0)]⁻¹ ∇f(x0), nghiệm này đảm bảo là điểm cực tiểu cục bộ duy nhất của hàm xấp xỉ g(d) với điều kiện ma trận Hessian ∇²f(x0) là xác định dương (positive definite). May mắn là với hàm cross-entropy trong logistic regression, Hessian luôn bán xác định dương/xác định dương (nếu ma trận dữ liệu full rank).

<br>

<a id="node-m7p2qhb"></a>

### Newton-Raphson for Linear Regression

<p align="center"><kbd><img src="assets/djri8kw7c5a.png" width="80%"></kbd></p>

<br>

