# 5.3.5 Hessian

📊 **Progress:** `3` Notes | `9` Screenshots | `2` AI Reviews

---
<a id="node-s2fd4av"></a>

<br>

<a id="node-ncnn80q"></a>

## 5.4 The Hessian Matrix

<p align="center"><kbd><img src="assets/bwmt6e9iu4.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3wsjoicqjs7.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại ý là nói về vai trò của Hessian, và backprop có thể dùng để tính Hessian
>
>
>
> Và một vấn đề cần cân nhắc khi tính Hessian là chi phí tính toán. Ta sẽ thấy, chi phí tính Hessian sẽ scale theo O(W²) (W là số tham số (weight + bias))

<br>

<a id="node-oap5h48"></a>

### 5.4.1 Diagonal Approximation

<p align="center"><kbd><img src="assets/vis49nchcxg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/tgsv8kes64f.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4945amf26bo.png" width="80%"></kbd></p>

> [!NOTE]
> 5.48: aj = Σi wji zi
>
>
>
> 5.49: zj = h(aj)
>
>
>
> 5.53: ∂En/∂w⁽¹⁾ji = δ⁽²⁾j z⁽¹⁾i
>
>
>
> với δ⁽²⁾j = ∂En/∂a⁽²⁾j
>
>
>
> 5.56: ∂En/∂a⁽²⁾j = h'(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> ---
>
>
>
> f(x,y,z), x(u,v), y(u,v), z(v)
>
>
>
> df = ∂f/∂x dx + ∂f/∂y dy + ∂f/∂z dz
>
>
>
> dx = ∂x/∂u du + ∂x/∂v dv
>
>
>
> dy = ∂y/∂u du + ∂y/∂v dv
>
>
>
> dz = z'(v) dv
>
>
>
> df = ∂f/∂x (∂x/∂u du + ∂x/∂v dv) + ∂f/∂y (∂y/∂u du + ∂y/∂v dv) + ∂f/∂z z'(v) dv
>
>
>
> df = (∂f/∂x ∂x/∂u + ∂f/∂y ∂y/∂u) du + (∂f/∂x ∂x/∂v + ∂f/∂y ∂y/∂v + ∂f/∂z z'(v)) dv
>
>
>
> ⇒ ∂f/∂u = ∂f/∂x ∂x/∂u + ∂f/∂y ∂y/∂u
>
>
>
> ∂f/∂v = ∂f/∂x ∂x/∂v + ∂f/∂y ∂y/∂v + ∂f/∂z z'(v)
>
>
>
> ---
>
>
>
>
>
> ∂²En/∂w⁽¹⁾ji²
>
>
>
> = ∂/∂w⁽¹⁾ji \[∂En/∂w⁽¹⁾ji\]
>
>
>
> Theo 5.53: ∂En/∂w⁽¹⁾ji = δ⁽²⁾j z⁽¹⁾i
>
>
>
> = ∂/∂w⁽¹⁾ji \[∂En/∂a⁽²⁾j z⁽¹⁾i\]
>
>
>
> (5.56: ∂En/∂a⁽²⁾j = h'(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k)
>
>
>
> = z⁽¹⁾i ∂/∂w⁽¹⁾ji \[∂En/∂a⁽²⁾j\]
>
>
>
> = z⁽¹⁾i (∂/∂a⁽²⁾j \[∂En/∂a⁽²⁾j\]) (∂a⁽²⁾j/∂w⁽¹⁾ji)
>
>
>
> = z⁽¹⁾i (∂²En/∂a⁽²⁾j²) (∂a⁽²⁾j/∂w⁽¹⁾ji)
>
>
>
> a⁽²⁾j = z⁽¹⁾1 w⁽¹⁾j1 + z⁽¹⁾2 w⁽¹⁾j2 + ... + z⁽¹⁾i w⁽¹⁾ji + ..
>
>
>
> ⇒ ∂a⁽²⁾j/∂w⁽¹⁾ji = z⁽¹⁾i
>
>
>
> ... = z⁽¹⁾i z⁽¹⁾i (∂²En/∂a⁽²⁾j²) = (∂²En/∂a⁽²⁾j²) z⁽¹⁾i² → 5.79
>
>
>
> ---
>
>
>
> ∂/∂a⁽²⁾j \[∂En/∂a⁽²⁾j\]
>
>
>
> Gọi ∂En/∂a⁽²⁾j là f
>
>
>
> thì theo 5.56 ở trên: ∂En/∂a⁽²⁾j = h'(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k, thì
>
>
>
> f là hàm của x, y:
>
>
>
> với x = x(a⁽²⁾j) = h'(a⁽²⁾j).
>
>
>
> dx = x'(a⁽²⁾j) da⁽²⁾j = h''(a⁽²⁾j) da⁽²⁾j
>
>
>
> và y(δ⁽³⁾1, δ⁽³⁾2,...) = Σk w⁽²⁾kj δ⁽³⁾k = w⁽²⁾1j δ⁽³⁾1 + w⁽²⁾2j δ⁽³⁾2 + ....
>
>
>
> ⇒ dy = ∂y/∂δ⁽³⁾1 dδ⁽³⁾1 + ∂y/∂δ⁽³⁾2 dδ⁽³⁾2 + ...
>
>
>
> = w⁽²⁾1j dδ⁽³⁾1 + w⁽²⁾2j dδ⁽³⁾2 + ...
>
>
>
> ⇒ df = ∂f/∂x dx + ∂f/∂y dy
>
>
>
> df = y h''(a⁽²⁾j) da⁽²⁾j + x (w⁽²⁾1j dδ⁽³⁾1 + w⁽²⁾2j dδ⁽³⁾2 + ...)
>
>
>
> ---
>
>
>
> Cách 1 (dù rằng sẽ ko chuẩn lắm, vì ta ko cho chia da⁽²⁾j): Chia hai vế cho da⁽²⁾j
>
>
>
> ⇔ df/da⁽²⁾j = y h''(a⁽²⁾j) + x (w⁽²⁾1j dδ⁽³⁾1/da⁽²⁾j + w⁽²⁾2j dδ⁽³⁾2/da⁽²⁾j + ...)
>
>
>
> ⇔ df/da⁽²⁾j = (Σk w⁽²⁾kj δ⁽³⁾k) h''(a⁽²⁾j) + h'(a⁽²⁾j) (w⁽²⁾1j dδ⁽³⁾1/da⁽²⁾j + w⁽²⁾2j dδ⁽³⁾2/da⁽²⁾j + ...)
>
>
>
> ⇔ df/da⁽²⁾j = (Σk w⁽²⁾kj δ⁽³⁾k) h''(a⁽²⁾j) + h'(a⁽²⁾j) Σk (w⁽²⁾kj dδ⁽³⁾k/da⁽²⁾j)
>
>
>
> ⇔ df/da⁽²⁾j = h'(a⁽²⁾j) Σk (w⁽²⁾kj dδ⁽³⁾k/da⁽²⁾j) + h''(a⁽²⁾j) (Σk w⁽²⁾kj δ⁽³⁾k)
>
>
>
> ---
>
>
>
> Cách 2:
>
>
>
>  df = y h''(a⁽²⁾j) da⁽²⁾j + x (w⁽²⁾1j dδ⁽³⁾1 + w⁽²⁾2j dδ⁽³⁾2 + ...) (1)
>
>
>
>  δ⁽³⁾1 =  δ⁽³⁾1(a⁽²⁾1, a⁽²⁾2,...)
>
>
>
> ⇒ dδ⁽³⁾1 = ∂δ⁽³⁾1/∂a⁽²⁾1 da⁽²⁾1+ ∂δ⁽³⁾1/∂a⁽²⁾2 da⁽²⁾2 + ... ∂δ⁽³⁾1/∂a⁽²⁾j da⁽²⁾j
>
>
>
> tương tự
>
>
>
> dδ⁽³⁾2 = ∂δ⁽³⁾2/∂a⁽²⁾1 da⁽²⁾1+ ∂δ⁽³⁾2/∂a⁽²⁾2 da⁽²⁾2 + ... ∂δ⁽³⁾2/∂a⁽²⁾j da⁽²⁾j
>
>
>
> ..
>
>
>
> Thế vào (1) nhân ra gom lại ta sẽ có:
>
>
>
> df = y h''(a⁽²⁾j) da⁽²⁾j + x \[w⁽²⁾1j (∂δ⁽³⁾1/∂a⁽²⁾1 da⁽²⁾1+ ...+ ... ∂δ⁽³⁾1/∂a⁽²⁾j da⁽²⁾j) + w⁽²⁾2j (∂δ⁽³⁾2/∂a⁽²⁾1 da⁽²⁾1+ ... ∂δ⁽³⁾2/∂a⁽²⁾j da⁽²⁾j) + ...)
>
>
>
> = y h''(a⁽²⁾j) da⁽²⁾j + x \[(w⁽²⁾1j ∂δ⁽³⁾1/∂a⁽²⁾j da⁽²⁾j) + w⁽²⁾2j (∂δ⁽³⁾2/∂a⁽²⁾j da⁽²⁾j) + ...\] + ...(những term gắn với da⁽²⁾1, da⁽²⁾2,..)
>
>
>
> = y h''(a⁽²⁾j) da⁽²⁾j + x \[(w⁽²⁾1j ∂δ⁽³⁾1/∂a⁽²⁾j) + w⁽²⁾2j ∂δ⁽³⁾2/∂a⁽²⁾j) da⁽²⁾j + ...\] + ...(những term gắn với da⁽²⁾1, da⁽²⁾2,..)
>
>
>
> = y h''(a⁽²⁾j) da⁽²⁾j + x \[Σk w⁽²⁾kj ∂δ⁽³⁾k/∂a⁽²⁾j\] da⁽²⁾j + ...\] + ...(những term gắn với da⁽²⁾1, da⁽²⁾2,..)
>
>
>
> df = {y h''(a⁽²⁾j) + x \[Σk w⁽²⁾kj ∂δ⁽³⁾k/∂a⁽²⁾j\] } da⁽²⁾j + ...\] + ...(những term gắn với da⁽²⁾1, da⁽²⁾2,..)
>
>
>
> ⇒ df/da⁽²⁾j = y h''(a⁽²⁾j) + x \[Σk w⁽²⁾kj ∂δ⁽³⁾k/∂a⁽²⁾j\]
>
>
>
> = Σk w⁽²⁾kj δ⁽³⁾k h''(a⁽²⁾j) + h'(a⁽²⁾j) \[Σk w⁽²⁾kj ∂δ⁽³⁾k/∂a⁽²⁾j\]
>
>
>
> = h'(a⁽²⁾j) \[Σk w⁽²⁾kj ∂δ⁽³⁾k/∂a⁽²⁾j\] + Σk w⁽²⁾kj δ⁽³⁾k h''(a⁽²⁾j)
>
>
>
> = h'(a⁽²⁾j) \[Σk w⁽²⁾kj ∂δ⁽³⁾k/∂a⁽²⁾j\] + h''(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> Ra kết quả như cách 1:
>
>
>
> ---
>
>
>
> ∂δ⁽³⁾k/∂a⁽²⁾j
>
>
>
> δ⁽³⁾k = ∂En/∂a⁽³⁾k = δ⁽³⁾k(a⁽³⁾1, a⁽³⁾2,...)
>
>
>
> dδ⁽³⁾k = ∂δ⁽³⁾k/∂a⁽³⁾1 da⁽³⁾1 + ∂δ⁽³⁾k/∂a⁽³⁾2 da⁽³⁾2 + ...
>
>
>
> = Σk' ∂δ⁽³⁾k/∂a⁽³⁾k' da⁽³⁾k' (2)
>
>
>
> ---
>
>
>
> a⁽³⁾k' = w⁽²⁾k'1 h(a⁽²⁾1) + w⁽²⁾k'2 h(a⁽²⁾2) +..+ w⁽²⁾k'j h(a⁽²⁾j) 
>
>
>
> da⁽³⁾k' = ∂a⁽³⁾k'/∂a⁽²⁾1 da⁽²⁾1 + ...+ ∂a⁽³⁾k'/∂a⁽²⁾j da⁽²⁾j
>
>
>
> ∂a⁽³⁾k'/∂a⁽²⁾1 = ∂a⁽³⁾k'/∂z⁽²⁾1 ∂z⁽²⁾1/∂a⁽²⁾1
>
>
>
> ∂a⁽³⁾k'/∂z⁽²⁾1 = ∂\[tổng\]/∂z⁽²⁾1 = \[∂(z⁽²⁾1w⁽²⁾11)/∂z⁽²⁾1 + ∂(z⁽²⁾2w⁽²⁾12)∂z⁽²⁾1 +... 
>
>
>
> = ∂\[z⁽²⁾1 w⁽²⁾11\]/∂z⁽²⁾1 = w⁽²⁾11
>
>
>
> = ∂a⁽³⁾k'/∂z⁽²⁾1 z⁽²⁾1/∂a⁽²⁾1 da⁽²⁾1 + ...+ ∂a⁽³⁾k'/∂a⁽²⁾j da⁽²⁾j
>
>
>
> = w⁽²⁾k'1 h'(a⁽²⁾1) da⁽²⁾1 + ...+ w⁽²⁾k'j h'(a⁽²⁾j) da⁽²⁾j
>
>
>
> Lắp da⁽³⁾k' vào (2):
>
>
>
> .. = Σk' ∂δ⁽³⁾k/∂a⁽³⁾k' \[w⁽²⁾k'1 h'(a⁽²⁾1) da⁽²⁾1 + ...+ w⁽²⁾k'j h'(a⁽²⁾j) da⁽²⁾j\]
>
>
>
> .= Σk' \[ ∂δ⁽³⁾k/∂a⁽³⁾k' w⁽²⁾k'1 h'(a⁽²⁾1) da⁽²⁾1 + ...+ ∂δ⁽³⁾k/∂a⁽³⁾k' w⁽²⁾k'j h'(a⁽²⁾j) da⁽²⁾j\]
>
>
>
> = Σk' \[ ∂δ⁽³⁾k/∂a⁽³⁾k' w⁽²⁾k'1 h'(a⁽²⁾1)\] da⁽²⁾1 + ...+ Σk' \[∂δ⁽³⁾k/∂a⁽³⁾k' w⁽²⁾k'j h'(a⁽²⁾j)\] da⁽²⁾j
>
>
>
> ⇒ ∂δ⁽³⁾k/∂a⁽²⁾j = Σk' \[∂δ⁽³⁾k/∂a⁽³⁾k' w⁽²⁾k'j h'(a⁽²⁾j)\]
>
>
>
> = Σk' \[∂(∂En/∂a⁽³⁾k)/∂a⁽³⁾k' w⁽²⁾k'j h'(a⁽²⁾j)\]
>
>
>
> = Σk' \[(∂²En/∂a⁽³⁾k∂a⁽³⁾k') w⁽²⁾k'j h'(a⁽²⁾j)\]
>
>
>
> = h'(a⁽²⁾j) Σk' \[w⁽²⁾k'j (∂²En/∂a⁽³⁾k∂a⁽³⁾k')\]
>
>
>
> Viết lại: ∂δ⁽³⁾k/∂a⁽²⁾j = h'(a⁽²⁾j) Σk' \[w⁽²⁾k'j (∂²En/∂a⁽³⁾k∂a⁽³⁾k')\]
>
>
>
> ---
>
>
>
> Vậy, thay vào lại: h'(a⁽²⁾j) \[Σk w⁽²⁾kj ∂δ⁽³⁾k/∂a⁽²⁾j\] + h''(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> = h'(a⁽²⁾j) \[Σk w⁽²⁾kj (h'(a⁽²⁾j) Σk' \[w⁽²⁾k'j (∂²En/∂a⁽³⁾k∂a⁽³⁾k')\])\] + h''(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> = h'(a⁽²⁾j) h'(a⁽²⁾j) \[Σk w⁽²⁾kj Σk' \[w⁽²⁾k'j (∂²En/∂a⁽³⁾k∂a⁽³⁾k')\])\] + h''(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> = h'(a⁽²⁾j)² \[Σk Σk' w⁽²⁾kj w⁽²⁾k'j (∂²En/∂a⁽³⁾k∂a⁽³⁾k')\] + h''(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> Đây là 5.80

📹 [Xem video trên YouTube](https://youtu.be/fvqdTDe0cek)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã tự chứng minh chi tiết và chính xác từng bước biến đổi từ quy tắc đạo hàm hợp (chain rule) để đi đến công thức (5.79) và (5.80) trong sách giáo trình.
>
> **🟡 Minor issues**
>
> **1.** *"df/da⁽²⁾j = y h''(a⁽²⁾j) + x (w⁽²⁾1j dδ⁽³⁾1/da⁽²⁾j + w⁽²⁾2j dδ⁽³⁾2/da⁽²⁾j + ...)"*
>
> Ở 'Cách 1', việc chia trực tiếp vi phân toàn phần df cho da_j trong hàm nhiều biến là thao tác hình thức (informal). Tuy nhiên, bạn đã nhận thức rõ điều này và bổ sung 'Cách 2' triển khai vi phân chính tắc rất chuẩn xác.
>
>
> **✓ Strengths**
> - Tự triển khai và chứng minh đầy đủ chi tiết công thức (5.79) và (5.80) thay vì chỉ chép lại kết quả.
> - Sử dụng công cụ vi phân toàn phần rất khéo léo để tách và tìm đạo hàm bậc hai của hàm hợp nhiều biến.
> - Ký hiệu chỉ số tầng (layer index) và trọng số liên kết rõ ràng, theo sát trực quan hình vẽ minh họa.
>
> **💡 Deeper notes**
> - Để đi từ (5.80) sang (5.81) (xấp xỉ đường chéo của LeCun), người ta giả định bỏ qua các phần tử ngoài đường chéo ∂²En/(∂a_k ∂a_k') khi k ≠ k', khi đó tổng kép Σ_k Σ_k' rút gọn chỉ còn tổng đơn Σ_k với w_kj².

**🔗 See also:** [Feed-Forward Network Unit Activation](./531_evaluation_of_error_function_derivatives.md#node-krbtnm2) · [Weight Derivative Evaluation](./531_evaluation_of_error_function_derivatives.md#node-noaxia8)

<br>

<a id="node-3pv5vv4"></a>

#### 5.4.1 Diagonal Approximation (bản sao)

<p align="center"><kbd><img src="assets/vis49nchcxg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/tgsv8kes64f.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4945amf26bo.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/llbfpy92wo.png" width="80%"></kbd></p>

> [!NOTE]
> 5.48: aj = Σi wji zi
>
>
>
> 5.49: zj = h(aj)
>
>
>
> 5.53: ∂En/∂w⁽¹⁾ji = δ⁽²⁾j z⁽¹⁾i
>
>
>
> với δ⁽²⁾j = ∂En/∂a⁽²⁾j
>
>
>
> 5.56: ∂En/∂a⁽²⁾j = h'(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> ---
>
>
>
> f(x,y,z), x(u,v), y(u,v), z(w)
>
>
>
> df = ∂f/∂x dx + ∂f/∂y dy + ∂f/∂z dz (total differenetial)
>
>
>
> dx = ∂x/∂u du + ∂x/∂v dv
>
>
>
> dy = ∂y/∂u du + ∂y/∂v dv
>
>
>
> dz = z'(w)dw
>
>
>
> df = ∂f/∂x (∂x/∂u du + ∂x/∂v dv) + ∂f/∂y (∂y/∂u du + ∂y/∂v dv) + ∂f/∂z z'(w)dw
>
>
>
> = (∂f/∂x ∂x/∂u + ∂f/∂y∂y/∂u) du + (∂f/∂x ∂x/∂v + ∂f/∂y ∂y/∂v) dv + ∂f/∂z z'(w) dw
>
>
>
> ∂f/∂u = ∂f/∂x ∂x/∂u + ∂f/∂y∂y/∂u
>
>
>
> ∂f/∂v = ∂f/∂x ∂x/∂v + ∂f/∂y ∂y/∂v
>
>
>
> ∂f/∂w = ∂f/∂z z'(w)
>
>
>
> ---
>
>
>
> i = 2:
>
>
>
> f(x), f'(x) = d/dx f(x), f''(x) = d/dx f'(x)
>
>
>
> ∂²En/∂w⁽¹⁾j2² = ∂/∂w⁽¹⁾j2 (∂En/∂w⁽¹⁾j2)
>
>
>
> 5.53: ∂En/∂w⁽¹⁾j2 = δ⁽²⁾j z⁽¹⁾2
>
>
>
> .. = ∂/∂w⁽¹⁾j2 (δ⁽²⁾j z⁽¹⁾2)
>
>
>
> = z⁽¹⁾2 ∂/∂w⁽¹⁾j2 (δ⁽²⁾j)
>
>
>
> = z⁽¹⁾2 ∂δ⁽²⁾j/∂a⁽²⁾j ∂a⁽²⁾j/∂w⁽¹⁾j2
>
>
>
> Xét ∂a⁽²⁾j/∂w⁽¹⁾j2
>
>
>
> = ∂(z⁽¹⁾1w⁽¹⁾j1 + z⁽¹⁾2w⁽¹⁾j2 + ...)/∂w⁽¹⁾j2
>
>
>
> = ∂(z⁽¹⁾2w⁽¹⁾j2)/∂w⁽¹⁾j2
>
>
>
> = z⁽¹⁾2
>
>
>
> ...= z⁽¹⁾2 ∂δ⁽²⁾j/∂a⁽²⁾j z⁽¹⁾2
>
>
>
> = (z⁽¹⁾2)² ∂δ⁽²⁾j/∂a⁽²⁾j
>
>
>
> = (z⁽¹⁾2)² ∂/∂a⁽²⁾j δ⁽²⁾j
>
>
>
> = (z⁽¹⁾2)² ∂/∂a⁽²⁾j \[∂En/∂a⁽²⁾j\]
>
>
>
> = (z⁽¹⁾2)² ∂²En/∂a⁽²⁾j²
>
>
>
> Viết lại: 
>
>
>
> ∂²En/∂w⁽¹⁾j2² = (z⁽¹⁾2)² ∂²En/∂a⁽²⁾j²
>
>
>
> thay 2 bởi i (nãy mượn i = 2 cho dễ): 
>
>
>
> ∂²En/∂w⁽¹⁾ji² = (z⁽¹⁾i)² ∂²En/∂a⁽²⁾j² → 5.79
>
>
>
> ---
>
>
>
> Derive 5.80:
>
>
>
> ∂²En/∂a⁽²⁾j² = ∂/∂a⁽²⁾j \[∂En/∂a⁽²⁾j\]
>
>
>
> 5.56: ∂En/∂a⁽²⁾j = h'(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> .. = ∂/∂a⁽²⁾j \[h'(a⁽²⁾j) Σk w⁽²⁾kj δ⁽³⁾k\]
>
>
>
> Dễ thấy h'(a⁽²⁾j) là hàm phụ thuộc a⁽²⁾j
>
>
>
> Σk w⁽²⁾kj δ⁽³⁾k, có các  δ⁽³⁾k, cũng là hàm phụ thuộc a⁽²⁾j do để có δ⁽³⁾k ta phải forward prop ra E.
>
>
>
> Nên đây là đạo hàm của tích hai hàm số phụ thuộc a⁽²⁾j, dùng product rule: (uv)' = u'v + uv'
>
>
>
> ..= ∂/∂a⁽²⁾j \[h'(a⁽²⁾j)\] (Σk w⁽²⁾kj δ⁽³⁾k) + h'(a⁽²⁾j) \[∂/∂a⁽²⁾j Σk w⁽²⁾kj δ⁽³⁾k\]
>
>
>
> Xét ∂/∂a⁽²⁾j \[h'(a⁽²⁾j)\] = h''(a⁽²⁾j)
>
>
>
> Hạng tử 1: h''(a⁽²⁾j) (Σk w⁽²⁾kj δ⁽³⁾k) Đấy chính là hạng tử 2 của 5.80
>
>
>
> ---
>
>
>
> Hạng tử 2: h'(a⁽²⁾j) \[∂/∂a⁽²⁾j Σk w⁽²⁾kj δ⁽³⁾k\]
>
>
>
> ---
>
>
>
> Xét ∂/∂a⁽²⁾j Σk w⁽²⁾kj δ⁽³⁾k
>
>
>
> = Σk ∂/∂a⁽²⁾j \[w⁽²⁾kj δ⁽³⁾k\]
>
>
>
> = Σk w⁽²⁾kj ∂/∂a⁽²⁾j \[δ⁽³⁾k\] (1)
>
>
>
> ---
>
>
>
> Xét ∂/∂a⁽²⁾j \[δ⁽³⁾k\]
>
>
>
> Tính ∂δ⁽³⁾k/∂z⁽²⁾j trước:
>
>
>
> ∂δ⁽³⁾k/∂z⁽²⁾j = ∂δ⁽³⁾k/∂a⁽³⁾1 ∂a⁽³⁾1/∂z⁽²⁾j + ∂δ⁽³⁾k/∂a⁽³⁾2 ∂a⁽³⁾2/∂z⁽²⁾j + ..
>
>
>
> = Σk' ∂δ⁽³⁾k/∂a⁽³⁾k' ∂a⁽³⁾k'/∂z⁽²⁾j
>
>
>
> ---
>
>
>
> Từ đó tính ∂δ⁽³⁾k/∂a⁽²⁾j:
>
>
>
> ∂δ⁽³⁾k/∂a⁽²⁾j = ∂δ⁽³⁾k/∂z⁽²⁾j ∂z⁽²⁾j/∂a⁽²⁾j
>
>
>
> (thay ∂δ⁽³⁾k/∂z⁽²⁾j ở trên vào)
>
>
>
> = (Σk' ∂δ⁽³⁾k/∂a⁽³⁾k' ∂a⁽³⁾k'/∂z⁽²⁾j) ∂z⁽²⁾j/∂a⁽²⁾j
>
>
>
> (do z⁽²⁾j = h(a⁽²⁾j) ⇒ ∂z⁽²⁾j/∂a⁽²⁾j = h'(a⁽²⁾j))
>
>
>
> = (Σk' ∂δ⁽³⁾k/∂a⁽³⁾k' ∂a⁽³⁾k'/∂z⁽²⁾j) h'(a⁽²⁾j)
>
>
>
> Viết lại: ∂δ⁽³⁾k/∂a⁽²⁾j = (Σk' ∂δ⁽³⁾k/∂a⁽³⁾k' ∂a⁽³⁾k'/∂z⁽²⁾j) h'(a⁽²⁾j)
>
>
>
> ta tính tiếp ∂δ⁽³⁾k/∂a⁽³⁾k' và ∂a⁽³⁾k'/∂z⁽²⁾j
>
>
>
> ---
>
>
>
>  Tính ∂δ⁽³⁾k/∂a⁽³⁾k':
>
>
>
> = ∂\[∂En/∂a⁽³⁾k\]/∂a⁽³⁾k'
>
>
>
> = ∂²En/(∂a⁽³⁾k∂a⁽³⁾k')
>
>
>
> ---
>
>
>
> Tính ∂a⁽³⁾k'/∂z⁽²⁾j: dễ thấy = w⁽²⁾k'j
>
>
>
> ---
>
>
>
> Vậy ∂δ⁽³⁾k/∂a⁽²⁾j = (Σk' ∂δ⁽³⁾k/∂a⁽³⁾k' ∂a⁽³⁾k'/∂z⁽²⁾j) h'(a⁽²⁾j)
>
>
>
> = (Σk' (∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) w⁽²⁾k'j) h'(a⁽²⁾j)
>
>
>
> ---
>
>
>
> Thế kết quả trên vào (1):
>
>
>
> ∂/∂a⁽²⁾j Σk w⁽²⁾kj δ⁽³⁾k = Σk w⁽²⁾kj **∂δ⁽³⁾k/∂a⁽²⁾j**
>
>
>
> = Σk w⁽²⁾kj Σk' {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) w⁽²⁾k'j) h'(a⁽²⁾j)}
>
>
>
> = Σk w⁽²⁾kj h'(a⁽²⁾j) Σk' {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) w⁽²⁾k'j }
>
>
>
> = h'(a⁽²⁾j) Σk w⁽²⁾kj Σk' {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) w⁽²⁾k'j }
>
>
>
> = h'(a⁽²⁾j) Σk Σk' w⁽²⁾kj {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) w⁽²⁾k'j }
>
>
>
> = h'(a⁽²⁾j) Σk Σk' w⁽²⁾kj w⁽²⁾k'j {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) }
>
>
>
> Hạng tử 2 còn đầy đủ: 
>
>
>
> h'(a⁽²⁾j) \[∂/∂a⁽²⁾j Σk w⁽²⁾kj δ⁽³⁾k\]
>
>
>
> = h'(a⁽²⁾j) h'(a⁽²⁾j) Σk w⁽²⁾kj w⁽²⁾k'j Σk' {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) }
>
>
>
> = h'(a⁽²⁾j)² Σk w⁽²⁾kj w⁽²⁾k'j Σk' {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) }
>
>
>
> = h'(a⁽²⁾j)² Σk Σk' w⁽²⁾kj w⁽²⁾k'j {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k')) }
>
>
>
> ---
>
>
>
> Vậy ∂²En/∂a⁽²⁾j² =
>
>
>
> h'(a⁽²⁾j)² Σk Σk' w⁽²⁾kj w⁽²⁾k'j {(∂²En/(∂a⁽³⁾k∂a⁽³⁾k'))}
>
>
>
> \+ h''(a⁽²⁾j) (Σk w⁽²⁾kj δ⁽³⁾k) → 5.80
>
>
>
> ---
>
>
>
> 5.81: (∂²En/(∂a⁽³⁾k∂a⁽³⁾k') = 0 với k khác k'
>
>
>
> Với k = k': ∂²En/∂a⁽³⁾k²
>
>
>
> ∂²En/∂a⁽²⁾j² =
>
>
>
> h'(a⁽²⁾j)² Σk w⁽²⁾kj² ∂²En/∂a⁽³⁾k² + h''(a⁽²⁾j) (Σk w⁽²⁾kj δ⁽³⁾k) → 5.81

📹 Video 1: [Vi phân toàn phần giúp tính đạo hàm cấp hai theo w_ji thế nào? (phần 2)](https://youtu.be/8ZRlA-FO5wg)

📹 Video 2: [Vì sao đạo hàm cấp hai theo w_ji cần quy tắc nhân? (phần 3)](https://www.youtube.com/watch?v=hHoCRcFo9tg)

📹 Video 3: [Làm sao lan truyền ngược đạo hàm cấp hai theo a_j? (phần 4)](https://www.youtube.com/watch?v=0ZCEjdG0CXs)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã tự chứng minh chi tiết từng bước cho các công thức (5.79), (5.80) và (5.81) trong sách của Bishop bằng quy tắc đạo hàm chuỗi (chain rule) và tích (product rule) một cách chuẩn xác.
>
> **✓ Strengths**
> - Chứng minh công thức (5.79) rất chặt chẽ thông qua việc tách đạo hàm cấp hai đối với trọng số liên kết.
> - Áp dụng quy tắc đạo hàm của tích (product rule) để tách thành hai hạng tử cho công thức (5.80) rất rõ ràng và mạch lạc.
> - Xử lý chuẩn xác quy tắc chuỗi đa biến để tính đạo hàm ∂δ_k/∂a_j qua các nút trung gian của tầng kế tiếp.
> - Hiểu đúng bản chất của xấp xỉ đường chéo (diagonal approximation) ở công thức (5.81) khi triệt tiêu các phần tử chéo ngoài k ≠ k'.
>
> **💡 Deeper notes**
> - Cần lưu ý rằng xấp xỉ đường chéo trong (5.81) là xấp xỉ cục bộ tầng kế tiếp (bỏ qua tương tác giữa các nút a_k và a_k' với k ≠ k'), giúp việc tính toán lan truyền ngược đạo hàm cấp 2 có độ phức tạp O(W) tương đương backprop thông thường, thay vì O(W^2) nếu giữ toàn bộ Hessian.

<br>

