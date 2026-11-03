# 5.3.5 Hessian

📊 **Progress:** `1` Notes | `3` Screenshots

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

**🔗 See also:** [Feed-Forward Network Unit Activation](./531_evaluation_of_error_function_derivatives.md#node-krbtnm2)

<br>

