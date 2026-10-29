# 16.2 Direct solution of KKT system

📊 **Progress:** `2` Notes | `3` Screenshots | `2` AI Reviews

---
<a id="node-bstsx53"></a>

<br>

<a id="node-2efo5ov"></a>

## Direct Solution of KKT System

<p align="center"><kbd><img src="assets/jmhwjlkw2f.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/1ys79wd7bdk.png" width="80%"></kbd></p>

> [!NOTE]
> Qua đây ta sẽ học về một phương pháp hiệu quả để giải hệ KKT (nhắc nhanh: Là hệ phản ánh KKT conditions, điều kiện cần bậc nhất, mà nếu có thể yếu tố reduced Hessian ZᵀGZ xác định dương thì nghiệm của hệ cũng là nghiệm duy nhất và cũng sẽ thỏa điều kiện đủ bậc hai để trở thành nghiệm duy nhất của bài toán QP luôn, do đó nếu có các yếu tố đó, giải hệ sẽ có ngay nghiệm bài toán QP).
>
>
>
> Thế thì đầu tiên là một theorem nói rằng: Nếu matrix A (m × n), m ≥ 1 full row rank thì matrix KKT indefinite.
>
>
>
> Theorem đại khái là nói inertia(K) = inertia(reduced Hessian) + (m, m, 0)
>
>
>
> Nên nếu reduced Hessian xác định dương, mà nó là matrix có kích thước n-m × n-m, nên sẽ có n-m trị riêng dương, inertia = (n-m,0,0). Kết quả là K sẽ có inertia = (n, m, 0), mà có trị riêng cả âm cả dương thì tức là K không xác định.
>
>
>
> Nói thêm tí về reduced Hessian: ZᵀGZ:
>
>
>
> Ta biết G là Hessian của objective. Vì sao ZᵀGZ gọi là reduced Hessian?
>
>
>
> QP: minimize f(x) = (1/2) xᵀGx + cᵀx s.t Ax = b (A full rank, rank = m)
>
>
>
> ∇²f(x) = G: Hessian
>
>
>
> Lấy ví dụ x = \[x1, x2\]ᵀ là R² vector:
>
>
>
> ∇f(x) = \[∂f/∂x1, ∂f/∂x2\]ᵀ = \[độ dốc theo phương x1, độ dốc theo phương x2\]
>
>
>
> = \[slop x1, slope x2\]
>
>
>
> ∇²f(x) = \[∂²f/∂x1², ∂²f/∂x1x2; ∂²f/∂x1x2, ∂²f/∂x2²\]
>
>
>
> = \[curvature x1, curvature x1x2; curvature x2x1, curvature x2\]
>
>
>
> Xét dᵀ∇²f(x)d, hay \[d1,d2\]ᵀ\[∂²f/∂x1², ∂²f/∂x1x2; ∂²f/∂x1x2, ∂²f/∂x2²\]\[d1,d2\]
>
>
>
> = \[d1, d2\]\[∂²f/∂x1² d1 + ∂²f/∂x1x2 d2; ∂²f/∂x1x2 d1 + ∂²f/∂x2² d2\]
>
>
>
> = \[d1, d2\]\[cur_x1 d1 + cur_x1x2 d2; cur_x2x1 d1 + cur_x2 d2\]
>
>
>
> = cur_x1 d1² + cur_x1x2 d1d2 + cur_x2x1 d1d2 + cur_x2 d2²
>
>
>
> d = (1,0): dᵀ∇²f(x)d = cur_x1: độ cong tại theo phương x1 tại x
>
>
>
> d = (0,1): dᵀ∇²f(x)d = cur_x2: độ cong tại theo phương x2 tại x
>
>
>
> d = (1,1): dᵀ∇²f(x)d = cur_x1 + 2 curx1x2 + cur_x2: độ cong tại theo phương x1 & x2 tại x.
>
>
>
> ---
>
>
>
> Vậy thì giờ xét matrix G' = ZᵀGZ:
>
>
>
> Vì Z là matrix có các cột là basis của nullspace N(A) nên: d = Zu luôn là vector thuộc N(A) với mọi u bất kì.
>
>
>
> Điều này có nghĩa là, với u bất kì, uᵀ(ZᵀGZ)u sẽ sẽ luôn cho thông tin độ cong theo hướng nullspace vector d = Zu, ta không thể có thông tin độ cong theo hướng khác.
>
>
>
> Ví dụ như ở đây để dễ hình dung, giả sử ta có matrix A = \[1,1; 2,2\]  (chỉ là minh họa để dễ hình dung nullspace, còn theorem thì A phải full row rank) basis C(Aᵀ) = {(1,1)ᵀ}, basis N(A) = {(1,-1)ᵀ}
>
>
>
> Khi đó Z = (1,-1)ᵀ (matrix có 1 cột)
>
>
>
> với mọi d, Zu ví dụ u = 2, 2Z sẽ là vector trong nullspace, và (2Z)ᵀG(2Z) sẽ cho ra thông tin độ cong theo hướng vector (2,-2).
>
>
>
> Chính vì vậy, chữ reduce hiểu như là: Ta giảm từ matrix G cho phép có thông tin độ cong trong không gian biến số ban đầu: R², dimension = 2, xuống còn chỉ cho thông tin độ con trong nullspace: N(A), dimension = 1.

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=rqNag5i113c)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, không chỉ nắm đúng định lý về inertia của ma trận KKT mà còn xây dựng trực giác hình học rất chuẩn xác về reduced Hessian và không gian nullspace.
>
> **✓ Strengths**
> - Hiểu và diễn giải chính xác công thức định lý 16.3: inertia(K) = inertia(ZᵀGZ) + (m, m, 0) và hệ quả khi ZᵀGZ xác định dương thì inertia(K) = (n, m, 0).
> - Trực giác về reduced Hessian rất rõ ràng: giải thích cặn kẽ vì sao phép chiếu ZᵀGZ tương đương với việc thu hẹp thông tin độ cong về các hướng khả dĩ trong nullspace N(A).
> - Có ý thức phản biện tốt khi tự lưu ý rằng ví dụ minh họa nullspace không thỏa điều kiện full row rank của định lý.
>
> **💡 Deeper notes**
> - Về mặt thuật ngữ tối ưu hóa, các vector d = Zu trong N(A) còn được gọi là các hướng khả dĩ (feasible directions) đối với ràng buộc đẳng thức tuyến tính Ax = b, do A(x + d) = Ax + Ad = b + 0 = b.
> - Một lỗi chính tả nhỏ không ảnh hưởng bản chất: 'độ con trong nullspace' (độ cong) và 'slop x1' (slope).

<br>

<a id="node-6f6qfnq"></a>

### Factoring the Full KKT System

<p align="center"><kbd><img src="assets/vhx7zodxyy.png" width="80%"></kbd></p>

> [!NOTE]
> Một cách làm để giả hệ KKT là: factor matrix thành tích matrix tam giác rồi backsub.
>
>
>
> Mà một cách điển hình chính là khử Gauss: Đưa matrix K về dạng U: Và đó cũng chính là K = UR, khi đó hệ KKT sẽ trở thành hệ phương trình mà matrix hệ số là tam giác, việc giải chỉ là thế ngược: backsubstitution.
>
>
>
> Và đây cũng chính là thuật toán có thể dùng, vì thuật toán factor nổi tiếng khác là Cholesky chỉ work với matrix xác định dương, trong khi K xác định âm như theorem vừa rồi đã nói.
>
>
>
> Có điều nếu dùng khử Gauss, ta sẽ bỏ lãng phí việc K là matrix đối xứng, ý nói, có thể dùng cách khử Gauss, nhưng có thể có cách khác tốt hơn

> [!TIP]
> 🤖 **AI Check** — 🔴 Critical issues — ❌ **60/100** · ✗ Fix first
>
> Bạn đã nắm được ý chính về việc dùng phân tích tam giác thay cho Cholesky và nhược điểm bỏ phí tính đối xứng của khử Gauss. Tuy nhiên, bạn đã hiểu sai tính chất cốt lõi 'indefiniteness' (không xác định dấu) thành 'xác định âm', đây là sai lệch bản chất quan trọng của hệ KKT.
>
> **🔴 Critical issues**
>
> **1.** *"trong khi K xác định âm như theorem vừa rồi đã nói"*
>
> Từ gốc 'indefiniteness' có nghĩa là 'không xác định dấu' (indefinite - ma trận có cả trị riêng dương và âm), hoàn toàn khác với 'xác định âm' (negative definite). Nếu ma trận thực sự xác định âm, ta chỉ cần nhân $-1$ là dùng được Cholesky; chính vì ma trận KKT không xác định dấu (indefinite / hệ điểm yên ngựa) nên Cholesky mới không áp dụng được.
>
>
> **🟡 Minor issues**
>
> **1.** *"K = UR, khi đó hệ KKT sẽ trở thành hệ phương trình mà matrix hệ số là tam giác, việc giải chỉ là thế ngược: backsubstitution"*
>
> Khử Gauss (Gaussian elimination) phân tích ma trận thành dạng $LU$ (hoặc $PLU$ với partial pivoting), không phải $UR$. Ngoài ra, việc giải hệ gồm cả thế tiến (forward substitution với $L$) và thế ngược (backward substitution với $U$), chứ không chỉ riêng thế ngược.
>
>
> **✓ Strengths**
> - Hiểu đúng việc không thể áp dụng trực tiếp phân tích Cholesky tiêu chuẩn cho hệ KKT.
> - Nắm được nhược điểm của phép khử Gauss thông thường là bỏ qua tính đối xứng của ma trận KKT.
>
> **💡 Deeper notes**
> - Để vừa khai thác tính đối xứng vừa giải quyết được tính không xác định dấu (indefinite) của ma trận KKT, các phương pháp trực tiếp thường dùng phân tích đối xứng không xác định $P K P^T = L D L^T$ (với $D$ gồm các khối $1 \times 1$ và $2 \times 2$, theo thuật toán Bunch-Parlett hoặc Bunch-Kaufman).

<br>

