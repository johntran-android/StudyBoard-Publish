# 2.3.1 Conditional Gaussian

📊 **Progress:** `6` Notes | `7` Screenshots | `4` AI Reviews

---
<a id="node-o5ua58c"></a>

<br>

<a id="node-1xniye5"></a>

## Chia tách vector ngẫu nhiên Gaussian

<p align="center"><kbd><img src="assets/o58pp3q8s3.png" width="80%"></kbd></p>

> [!NOTE]
> Mở đầu phần này, gs nói đại khái là phân phối multivariate Normal có một tính chất quan trọng, đó là nếu ta có hai set random variables mà jointly Gaussian (tức là mình hiểu là joint distribution của chúng là Gaussian) thì khi đó, distribution của một set dựa trên set kia, cũng là Gaussian. Và thêm nữa, marginal distribution của mỗi set cũng là Gaussian.
>
>
>
> Lấy ví dụ ta sẽ xét random vector 𝐗 có D-dimensions, dĩ nhiên có nghĩa là ta có D random variable X1,...XD. Và 𝐗 \~ Normal(**μ**, **Σ**), tức X1,...XD có joint distribution là Normal(**μ**, **Σ**).
>
>
>
> Sau đó, ta mới tách random vector 𝐗 thành **Xa** và **Xb**, với **Xa** là M phần tử đầu tiên của 𝐗, **Xb** là phần còn lại. Dĩ nhiên **Xa** là M-dimensinal random variable vector và **Xb** là D-M dimensional random variables vector.
>
>
>
> Tiếp, ta mới define vector **μ**, cũng tách thành hai phần, **μa** và **μb**. Cũng như covariance matrix **Σ** sẽ có dạng block matrix: \[**Σaa Σab; Σba Σbb**\]
>
>
>
> Suy ngẫm chút xíu: Vì sao 𝐗 = \[**Xa**; **Xb**\] thì **μ** = \[**μa; μb**\] và **Σ =** \[**Σaa Σab; Σba Σbb**\]
>
>
>
> **μ** là location của distribution Normal(**μ**, **Σ**), và ta đã chứng minh nó chính là mean của X: E𝐗 = **μ**, nên khi X tách ra thành Xa và Xb, để 𝐗 = \[**Xa**; **Xb**\] thì EX dĩ nhiên cũng tách thành E\[**Xa**; **Xb**\] = \[E(**Xa**); E(**Xb**)\] và người ta đặt E(**Xa**) là **μa**, E(**Xa**) là **μb**. Nên **μ** = \[**μa; μb**\]
>
>
>
> Còn **Σ**, là thứ mà hôm qua ta đã thấy gs chứng minh rằng nó là covariance matrix. Ở đây mình nên hiểu thế này. Do quá quen với việc khi nghe nói về Normal(

<br>

<a id="node-dlkfo98"></a>

### Ma trận độ chính xác phân hoạch

<p align="center"><kbd><img src="assets/9murfka4f98.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, gs nói rằng trong nhiều tình huống ta sẽ thấy làm việc với inverse của covariance **Σ** thì tiện hơn **Σ**, ta đặt nó là **Λ**. Dĩ nhiên **Λ** cũng đối xứng. Và ta gọi nó là **precision matrix**.
>
>
>
> Và với việc 𝐗 = \[**Xa**; **Xb**\], **Λ** cũng tách thành \[**Λaa Λab; Λba Λbb**\] 
>
>
>
> Một chú ý là chưa chắc **Λaa, và Λbb đã là inverse của Σaa, Σbb.**

<br>

<a id="node-r2n5k6m"></a>

#### Chứng minh Gaussian điều kiện

<p align="center"><kbd><img src="assets/ervbp1q35y.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, ta sẽ bắt đầu chứng minh rằng nếu ta có hai bộ random variable có joint distribution là multivariate Gaussian thì pdf của một random variable set condition set khác cũng sẽ là Gaussian, bằng cách thử derive pdf của f(**xa**|**xb**).
>
>
>
> Thế thì đại khái là, gs nói rằng ta có thể bắt đầu với joint pdf f(**xa**, **xb**), tại giá trị fixed nào đó của **xb** và sau đó normalizing để có conditional distribution f(**xa**|**xb**). Có thể hiểu ý này thế nào?
>
>
>
> Mình nghĩ cái này đơn giản chỉ là gs đang nói đến định nghĩa của conditional distribution. Ta biết theo định nghĩa, giả sử ta có hai random variable X, Y: thì fX|Y(x|y) = fX,Y(x, y) / fY(y). Áp dụng với trường hợp này, ta có f(**xa**|**xb**) = f(**xa**, **xb**) / f(**xb**). Thì như vậy nếu ta có joint pdf của f(**xa**, **xb**) với evaluate tại **xb** (tức là joint pdf **Xa**, **Xb**, cũng là pdf của 𝐗, f(**xa**, **xb**) chỉ là hàm theo **xa**) và chia nó f(**xb**) là joint pdf của **Xb** tại **xb**, thì ta sẽ có conditional pdf của **xa** given **xb**. Và cái bước chia cho f(**xb**) này chính là bước normalizing the resulting expression mà gs Bishop nói đến.
>
>
>
> Tuy nhiên, ông nói thêm thay vì ta làm vậy, gọi là theo lối tường minh (explicitly), ta sẽ làm theo cách mà mình hiểu đại ý là giống như trong Casella hay làm, đó là **chỉ quan tâm cái kernel (hạt nhân, tức cái phần mà dính đến biến) của pdf** thôi, trong case này, chính là cái quadratic form hay còn gọi là cái term exponent công thức Gaussian, để rồi nếu ta có thể dựa vào đó để chứng minh dạng của distribution, và không cần phải quan tâm cái normalizing constant, hoặc quan tâm đến nó sau.
>
>
>
> Thế thì phần kernel của pdf của 𝐗 là exp\[-(1/2)(𝐱-**μ**)ᵀ **Σ⁻¹** (𝐱-**μ**)\]
>
>
>
> Xét cái quaratic form: -(1/2)(𝐱-**μ**)ᵀ **Σ⁻¹** (𝐱-**μ**)
>
>
>
> = -(1/2)(𝐱-**μ**)ᵀ **Λ** (𝐱-**μ**)
>
>
>
> = -(1/2)(𝐱-**μ**)ᵀ \[**Λaa**, **Λab**; **Λba**, **Λbb**\] (𝐱-**μ**)
>
>
>
> = -(1/2)(𝐱-**μ**)ᵀ \[**Λaa**, **Λab**; **Λba**, **Λbb**\] (𝐱-**μ**)
>
>
>
> = -(1/2)\[**xa**-**μa**; **xb**-**μb**\]ᵀ \[**Λaa**, **Λab**; **Λba**, **Λbb**\] \[**xa**-**μa**; **xb**-**μb**\]
>
>
>
> = -(1/2)(**xa**-**μa**)ᵀ**Λaa**(**xa**-**μa**) - (1/2)(**xa**-**μa**)ᵀ**Λab**(**xb**-**μb**) - (1/2)(**xb**-**μb**)**Λba**(**xa**-**μa**) - (1/2)(**xb**-**μb**)**Λbb**(**xb**-**μb**)
>
>
>
> Và tới đây lập luận chỉ đơn giản là, nếu ta coi **xb** là fixed, để rồi cái quadratic form này chỉ là hàm theo **xa**, thì nó có còn là quadratic form không, nếu có thì có thể kết luận ngay rằng kernel của f(**xa**|**xb**) cũng có dạng kernel của một Normal, và giúp kết luận ngay nó là một Normal, còn mean và covariance là gì thì tính sau.
>
>
>
> Nhắc lại, đây là cách làm mà mình thường thấy trong Casella, đó là khi xét tìm dạng của pdf, ta thường chỉ cần chỉ ra kernel của nó có dạng kernel của một phân phối nào đó, là đủ để có thể kết luận dạng của distribution. Sau đó, ta sẽ dùng cách bước khớp mẫu, để tìm ra giá trị của parameters. Và do đó thậm chí cũng khỏi cần quan tâm cái constant bên ngoài, vì kiểu gì thì chúng cũng đóng vai trò normalizing constant.

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **100/100** · ✓ Move on</summary>

Bạn đã hiểu rất chính xác và sâu sắc phương pháp Bishop đề xuất, đặc biệt là vai trò của việc tập trung vào "kernel" của phân phối để xác định dạng. Các bước phân tích và mở rộng dạng bậc hai cũng hoàn toàn khớp với tài liệu.

</details>

<br>

<a id="node-mm664xt"></a>

##### Hiệp phương sai Gaussian điều kiện

<p align="center"><kbd><img src="assets/2ukmkl8ok24.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/bln82ndpiz4.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo, đại khái là vầy, xét cái cụm này: (**xa**-**μa**)ᵀ**Λaa**(**xa**-**μa**) + (**xa**-**μa**)ᵀ**Λab**(**xb**-**μb**) + (**xb**-**μb**)ᵀ**Λba**(**xa**-**μa**) + (**xb**-**μb**)ᵀ**Λbb**(**xb**-**μb**), nếu ta triển khai ra và chỉ quan tâm những cái có dính đến **xa**, ta sẽ có:
>
>
>
> Coi cục (**xb**-**μb**)**Λbb**(**xb**-**μb**) là const, không care
>
>
>
> .. = **xa**ᵀ**Λaaxa** - **μa**ᵀ**Λaaxa** - **xa**ᵀ**Λaaμa** + **μa**ᵀ**Λaaμa** + **xa**ᵀ**Λabxb** - **μa**ᵀ**Λabxb** - **xa**ᵀ**Λabμb**+**μa**ᵀ**Λabμb** + (**xb**ᵀ**Λbaxa** - **μb**ᵀ**Λbaxa** - **xb**ᵀ**Λbaμa** + **μb**ᵀ**Λbaμa** + const
>
>
>
> Nhập tất cả các cụm không dính đến **xa** vào const luôn
>
>
>
> .. = **xa**ᵀ**Λaaxa** - 2**μa**ᵀ**Λaaxa** + **xa**ᵀ**Λabxb** - **xa**ᵀ**Λabμb** + **xb**ᵀ**Λbaxa** - **μb**ᵀ**Λbaxa** + const
>
>
>
> **xa**ᵀ**Λabxb** là scalar nên nó = (**xa**ᵀ**Λabxb**)ᵀ = **xb**ᵀ (**Λab**)ᵀ **xa** = **xb**ᵀ**Λba** **xa**, nhập với **xb**ᵀ**Λbaxa** thành 2**xb**ᵀ**Λbaxa**
>
>
>
> **xa**ᵀ**Λabμb**, là scalar, nên nó = (**xa**ᵀ**Λabμb**)ᵀ = **μb**ᵀ (**Λab**)ᵀ **xa** = **μb**ᵀ **Λba** **xa**, nhập với **μb**ᵀ**Λbaxa** thành 2**μb**ᵀ**Λbaxa**
>
>
>
> ..= **xa**ᵀ**Λaaxa** - 2**μa**ᵀ**Λaaxa** + 2**xb**ᵀ**Λbaxa** - 2**μb**ᵀ**Λbaxa** + const
>
>
>
> = **xa**ᵀ**Λaaxa** + 2(**xb**ᵀ**Λba** - **μa**ᵀ**Λaa** - **μb**ᵀ**Λba**)**xa** + const
>
>
>
> Vậy nếu viết đầy đủ cái kernel (có thêm exp\[(-1/2)..\] thì ta có:
>
>
>
> exp{(-1/2)\[**xa**ᵀ**Λaaxa** + 2(**xb**ᵀ**Λba** - **μa**ᵀ**Λaa** - **μb**ᵀ**Λba**)**xa** + const\]}
>
>
>
> Dùng e^(ab) = e^a e^b, đưa const ra, và ko care đến nó nữa, vì nó nhập vào cái normalizing constant ở ngoài, nên ta có
>
>
>
> exp{(-1/2)\[**xa**ᵀ**Λaaxa** + 2(**xb**ᵀ**Λba** - **μa**ᵀ**Λaa** - **μb**ᵀ**Λba**)**xa**\]} (1)
>
>
>
> Tới đây, ta mới xét... cái kernel của multi Normal (**μ**, **Σ**): exp\[-(1/2)(𝐱-**μ**)ᵀ Σ⁻¹ (𝐱-**μ**)\] và triển khai cái cụm -(1/2)(𝐱-**μ**)ᵀ Σ⁻¹ (𝐱-**μ**) này ra:
>
>
>
> \-(1/2)(𝐱-**μ**)ᵀ Σ⁻¹ (𝐱-**μ**) = -(1/2)(𝐱ᵀ**Σ⁻¹x** - **μ**ᵀ**Σ⁻¹x** - 𝐱ᵀ**Σ⁻¹μ** + **μ**ᵀ**Σ⁻¹μ**)
>
>
>
> = -(1/2)(𝐱ᵀ**Σ⁻¹x** - 2**μ**ᵀ**Σ⁻¹x** + **μ**ᵀ**Σ⁻¹μ**) (2)
>
>
>
> Thế thì so sánh cái ta có ở trên (1) và (2)
>
>
>
> exp{(-1/2)\[**xa**ᵀ**Λaaxa** + 2(**xb**ᵀ**Λba** - **μa**ᵀ**Λaa** - **μb**ᵀ**Λba**)**xa**\]}
>
>
>
> exp{-(1/2)(𝐱ᵀ**Σ⁻¹x** - 2**μ**ᵀ**Σ⁻¹x** + **μ**ᵀ**Σ⁻¹μ**)}
>
>
>
> Thì ta sẽ thấy **Λaa** tương ứng với **Σ⁻¹**, và **xb**ᵀ**Λba** - **μa**ᵀ**Λaa** - **μb**ᵀ**Λba** tương ứng với -**μ**ᵀ**Σ⁻¹ ⇨ μ**ᵀ ứng với -(**xb**ᵀ**Λba** - **μa**ᵀ**Λaa** - **μb**ᵀ**Λba**)(**Λaa**\_**inv**)
>
>
>
> Nói chung là từ đó, ta có thể cộng thêm và trừ bớt cho cụm **μ**ᵀ**Σ⁻¹μ**, và đưa phần dư ra ngoài lại, ta sẽ có thể đưa cái cụm trong exp về dạng quadratic form. Và từ đó kết luận đây là một multi-Normal.
>
>
>
> Và để xác định tham số, thì thật ra cũng là cái ta vừa làm đó. Gọi **μa|b**, và **Σa|b** là mean và covariance matrix của distribution Gaussian này, thì với việc **Λaa** khớp với **Σ⁻¹**, ta có thể kết luận:
>
>
>
> **Σa|b**\⁻¹ **CHÍNH LÀ Λaa**, ⇔ **Σa|b** = (**Λaa**)⁻¹ ⇨ đây là kết luận 2.73 trong sách.
>
>
>
> Và với việc μT ứng với -(**xb**ᵀ**Λba** - **μa**ᵀ**Λaa** - **μb**ᵀ**Λba**)(**Λaa**\_**inv**), thì ta cũng kết luận cái cụm này chính là (**μa|b**)ᵀ
>
>
>
> ⇨ **μa|b =** \[-(**xb**ᵀ**Λba** - **μa**ᵀ**Λaa** - **μb**ᵀ**Λba**)(**Λaa**\_**inv**)\]ᵀ
>
>
>
> = \[-**xb**ᵀ**ΛbaΛaa**\_**inv** + **μa**ᵀ + **μb**ᵀ**ΛbaΛaa**\_**inv**\]ᵀ
>
>
>
> = \[-**xb**ᵀ**ΛbaΛaa**\_**inv** + **μa**ᵀ + **μb**ᵀ**ΛbaΛaa**\_**inv**\]ᵀ
>
>
>
> = \[-**Λaa⁻¹**ᵀ**Λba**ᵀ**xb** + **μa**ᵀ + **Λaa**\_**inv**ᵀ**Λba**ᵀ**μb**
>
>
>
> = **μa** - **Λaa⁻¹**ᵀ**Λba**ᵀ**xb** + **Λaa**\_**inv**ᵀ**Λba**ᵀ**μb**
>
>
>
> = **μa** - **Λaa⁻¹ Λab xb** + **Λaa**\_**inv** **Λab μb** (dùng tính đối xứng của **Λaa⁻¹**, và (**Λba**)ᵀ = **Λab**)
>
>
>
> = **μa** - **Λaa⁻¹ Λab** (**xb** - **μb**)
>
>
>
> Vậy, **μa|b** = **μa** - **Λaa⁻¹ Λab** (**xb** - **μb**) → Đây chính là 2.75.
>
>
>
> Nói tóm lại, miễn là ta thấy phần bên trong exp, nếu xét là hàm quadratic của **xa**, thì là đã đủ để kết luận đây f(**xa**|**xb**) nhất định là Gaussian. Và bằng cách khớp với công thức Gassian tổng quát, ta có thể chỉ ra đâu là mean và covariance matrix.
>
>
>
> Để rồi ta có thể kết luận f(**xa**|**xb**) chính là pdf của Gaussian có mean là **μa|b** = **μa** - **Λaa⁻¹ Λab** (**xb** - **μb**) và covariance matrix là **Σa|b** = (**Λaa**)⁻¹

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **100/100** · ✓ Move on</summary>

Ghi chú của bạn cực kỳ chi tiết và chính xác, làm rõ hoàn toàn quá trình suy luận để đạt được các kết quả (2.73) và (2.75) mà sách chỉ trình bày vắn tắt. Việc bạn triển khai từng bước các phép tính ma trận và so sánh với dạng tổng quát của Gaussian là rất xuất sắc, cho thấy sự hiểu biết sâu sắc.

</details>

**🔗 See also:** [Phân phối Gaussian có điều kiện](./233_bayess_theorem_for_gaussian_variables.md#node-2d1tmn5)

<br>

<a id="node-su2e8a4"></a>

###### Schur complement: Biến đổi hiệp phương sai

<p align="center"><kbd><img src="assets/yeyvxh0k06.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn tiếp theo không có gì phức tạp. Hai kết quả trên đã thể hiện giá trị trung bình và ma trận hiệp phương sai của phân phối có điều kiện của **xa** dựa trên **xb**, thông qua các matrix khối con (tạm dịch từ partitioned) của **precision matrix** của phân phối đồng thời joint distribution. Cụ thể hơn, chúng dựa trên các ma trận con (partitioned matrices) của ma trận **precision**. 
>
>
>
> Thế thì bằng cách sử dụng một công thức được gọi là **Schur complement**, chúng ta cũng có thể **chuyển sang dạng thể hiện bởi các ma trận con (partitioned matrices) của ma trận hiệp phương sai** (covariance matrix). Đây chính là bước áp dụng đẳng thức này để biến đổi hai công thức đã chứng minh sang một dạng thể hiện khác, sử dụng các ma trận khối con của ma trận hiệp phương sai thay vì các ma trận khối con của ma trận nghịch đảo. Đây chính là một bài toán biến đổi đại số.

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **90/100** · ✓ Move on</summary>

Ghi chú của bạn đã tóm tắt chính xác mục đích và phương pháp được mô tả trong đoạn văn, đặc biệt là việc chuyển đổi từ ma trận độ chính xác (precision matrix) sang ma trận hiệp phương sai (covariance matrix) bằng cách sử dụng bổ đề Schur (Schur complement). Để sâu sắc hơn, bạn có thể đề cập rõ ràng hơn đến việc sử dụng đẳng thức (2.76) về nghịch đảo của ma trận khối, vốn là công cụ chính cho phép áp dụng bổ đề Schur trong ngữ cảnh này.

</details>

<br>

<a id="node-usyapsm"></a>

###### Mô hình Gaussian tuyến tính

<p align="center"><kbd><img src="assets/u8vni82mqi.png" width="80%"></kbd></p>

> [!NOTE]
> Và cụ thể là bằng cách dùng Schur complement, ta có thể thể hiện **Λaa** và **Λab** theo các matrix **Σaa, Σab, Σbb** để rồi thay vài **μa|b** và **Σa|b ta sẽ có hai công thức 2.81 và 2.82**:
>
>
>
> **μa|b** = **μa** + **Σab** **Σbb_inv** (**xb** - **μb**)
>
>
>
> **Σa|b** = **Σaa** - **Σab Σbb_inv Σba**
>
>
>
> Và từ đó ta có nhận xét là so với
>
>
>
> **μa|b** = **μa** - **Λaa_inv Λab** (**xb** - **μb**)
>
>
>
> **Σa|b** = (**Λaa**)**inv**
>
>
>
> thì 2.79 và 2.80 dài dòng hơn, tức là **thể hiện bằng partitioned precision ở dưới nãy sẽ gọn hơn.**
>
>
>
> Một lưu ý cuối, đó là dựa vào cả hai công thức đều thấy **μa|b là hàm tuyến tính theo xb, cũng như Σa|b hoàn toàn không phụ thuộc xa. Và ông nói đây là một ví dụ của cái gọi là LINEAR-GAUSSIAN model (có thể sẽ được học ở các chap sau)**

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **95/100** · ✓ Move on</summary>

Bài làm của bạn rất chính xác và sâu sắc. Bạn không chỉ chép đúng công thức mà còn nắm vững các nhận xét quan trọng về tính chất của mô hình và đưa ra so sánh đúng đắn về độ đơn giản của các dạng biểu diễn. Để bài làm hoàn hảo hơn, bạn nên đảm bảo các tham chiếu số công thức khớp với tài liệu gốc hoặc giải thích rõ ràng hơn về chúng.

</details>

**🔗 See also:** [Phân phối Gaussian phân tách có điều kiện](./232_marginal_gaussian.md#node-qwpga8o) · [Mô hình Gaussian Tuyến tính](./233_bayess_theorem_for_gaussian_variables.md#node-x44e412)

<br>

