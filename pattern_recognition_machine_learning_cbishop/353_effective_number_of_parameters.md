# 3.5.3 Effective number of parameters

📊 **Progress:** `1` Notes | `1` Screenshots

---
<a id="node-ca7uttw"></a>

<br>

<a id="node-2wanjgv"></a>

## Section 3.5.3 Effective Number of Parameters

<p align="center"><kbd><img src="assets/aiiljg5ul7.png" width="80%"></kbd></p>

> [!NOTE]
> Likelihood function là hàm L(**w**|𝒟), theo định nghĩa, nó bằng f(𝒟|**w**). Có nghĩa là, nó chính là f(𝒟|**w**) với tư cách là hàm theo **w**.
>
>
>
> Ta đang trong mô hình ℳi cụ thể: T|**x**\~ n(**w**TΦ(**x**), 1/β). Từ đó:
>
>
>
> f(𝒟|**w**) = f(**t**|**w**,β,**X**)
>
>
>
> = Πi=1:N 𝒩(ti|**w**TΦ(**x**i),1/β)
>
>
>
> và cái này ta đã derive ra kết quả chính là 𝒩(**Φw**, (1/β)**I**).
>
>
>
> Thế thì vẽ contour của f(𝒟|**w**) tức là ta cho nó bằng hằng số:
>
>
>
> 𝒩(**t**|**Φw**, (1/β)**I**) = c
>
>
>
> ⇔ \[(2π)^(-N/2)\] \[1/|((1/β)**I**)|^1/2\] exp\[-(**t** - **Φw**)T ((1/β)**I**)inv (**t** - **Φw**)/2\] = c
>
>
>
> |(1/β)**I**| = (1/β)^N = β^(-N) ⇒ 1/|((1/β)**I**)|^1/2 = β^(-N/2)
>
>
>
> ..⇔ \[(2π)^(-N/2)\] \[β^(-N/2)\] exp\[(-β/2)(**t** - **Φw**)T(**t** - **Φw**)\] = c
>
>
>
> ⇔ \[(2π)^(-N/2)\] \[β^(-N/2)\] exp\[(-β/2)(**t** - **Φw**)T(**t** - **Φw**)\] = c
>
>
>
> ⇔ exp\[(-β/2)(**t** - **Φw**)T(**t** - **Φw**)\] = c2 (nhập hằng số bên vế trái vào c bên phải)
>
>
>
> ⇔ (-β/2)(**t** - **Φw**)T(**t** - **Φw**) = c3 (lấy ln hai vế)
>
>
>
> ⇔ (**t** - **Φw**)T(**t** - **Φw**) = c4
>
>
>
> ⇔ **t**T**t** - **w**T**Φ**T**t** - **t**T**Φw** + **w**T**Φ**T**Φw** = c4
>
>
>
> ⇔ **w**T**Φ**T**Φw** - 2**t**T**Φw** + **t**T**t** = c4
>
>
>
> ⇔ **w**T**Φ**T**Φw** - 2**t**T**Φw** = c5
>
>
>
> và đây, với tư cách là phương trình theo của **w**, thì phương trình ....

**🔗 See also:** [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj)

<br>

