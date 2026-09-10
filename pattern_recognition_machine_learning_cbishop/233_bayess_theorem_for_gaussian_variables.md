# 2.3.3 Bayes's theorem for Gaussian variables

📊 **Progress:** `6` Notes | `9` Screenshots | `4` AI Reviews

---
<a id="node-647i5nk"></a>

<br>

<a id="node-x44e412"></a>

## Mô hình Gaussian Tuyến tính

<p align="center"><kbd><img src="assets/jwsklv9mz5t.png" width="80%"></kbd></p>

> [!NOTE]
> Qua phần này, đầu tiên gs nhắc lại, hai phần trước, ta bắt đầu với 𝐗 \~ Normal(**μ**, **Σ**), sau đó tách 𝐗 thành hai subvector **Xa**, **Xb**, để rồi ta chứng minh rằng f(**xa**|**xb**) và f(**xa**) đều là pdf của normal. Và trong quá trình đó, ta đã đề cập đến một điểm, mean f(**xa**|**xb**) là một hàm tuyến tính theo **xb**
>
>
>
> Xem link tới note trước, ta có **μa|b** = **μa** - **Λaa⁻¹ Λab** (**xb** - **μb**) thế thì vì sao nó là hàm tuyến tính với **xb**? à là vì nó có dạng \[matrix\] **xb** + constant, mà matrix nhân vector có bản chất là một linear transformation như đã học trong MIT 18.06.
>
>
>
> Mình nghĩ: như đã biết từ ee364a, nếu chặt chẽ, thì đây là affine function, ko phải linear function.
>
>
>
> Bên cạnh đó, covariance matrix, **Σa|b** = (**Λaa**)**inv**, thì không phụ thuộc **xb**, để rồi ông cho biết đây là một ví dụ của cái gọi là linear Gaussian model.
>
>
>
> Thế thì, trong bài toán này, cho rằng ta được cho f(𝐱) và f(𝐲|𝐱) đều là Normal trong đó mean của f(𝐲|𝐱) là hàm phụ thuộc 𝐱 và covariance matrix không phụ thuộc 𝐱. Đây là ví dụ của linear Gaussian model, và ta sẽ đi tìm f(𝐲) cũng như f(𝐱|𝐲). Và đại khái là đây là bài toán gặp nhiều trong các chap sau nên ta sẽ phân tích nó ở đây trước.

**🔗 See also:** [Mô hình Gaussian tuyến tính](./231_conditional_gaussian.md#node-usyapsm)

<br>

<a id="node-axpsoob"></a>

### Phân phối kết hợp Gaussian

<p align="center"><kbd><img src="assets/kpytdmukkt8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/oldani0onfa.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3x26fcigfs.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, như đã nói, ta có 𝐗 \~ Normal và 𝐘|𝐗 \~ Normal với mean là hàm tuyến tinh của 𝐱, và covariance không phụ thuộc 𝐱. Nên ta gọi distribution của 𝐗 là Normal(**μ**, **Λ⁻¹**) và **Y|X** \~ Normal(A𝐱+b, **L⁻¹**).
>
>
>
> (Chú ý, cách ghi của gs f(𝐱) = N(𝐱|**μ**, **Λ⁻¹**), chỉ cũng đồng nghĩa với việc nói hàm pdf của 𝐗 là hàm pdf của Normal(**μ**, **Λ⁻¹**), thì nó cùng ý nghĩa với việc nói distribution của 𝐗 là Normal(**μ**, **Λ⁻¹**), mình ít thấy cách ghi này trong Casella và Stat110)
>
>
>
> Một điểm lưu ý nữa, như đã biết, khi nói đến Normal(**μ**, **Σ**), thì Σ, như đã chứng minh, là covariance matrix, Cov(𝐗), và inverse của nó, **Σ⁻¹**, gọi là precision matrix. Nên nay khi ghi 𝐗 \~ Normal(**μ**, **Λ⁻¹**) thì **Λ⁻¹** chính là covariance matrix, và **Λ**, dĩ nhiên là precision matrix. Tương tự với **L⁻¹**, cũng là covariance matrix của f(𝐲|𝐱)
>
>
>
> Rồi, nói thêm rằng M, và D là số chiều (tức số phần tử) của 𝐗 và 𝐘. Và ta sẽ đi derive joint pdf của 𝐗, 𝐘.
>
>
>
> Một điểm có thể có bạn thấy bị ngáo: khi nói về random vector 𝐗 = (X1,...XM), thì nói về pdf của 𝐗, cũng chính là nói về joint pdf của X1,...XM. Tương tự, pdf của random vector 𝐘, cũng chính là joint pdf của các single random variable Y1,....YD. Vậy thì nay, nói đi tìm joint pdf của 𝐗, 𝐘 cũng chính là tìm joint pdf của X1,..XM, Y1,...YD. Hiểu vậy sẽ thấy việc ta tạo vector 𝐙 = \[𝐗; 𝐘\] (gắn nó lại thành vector M + D chiều) thì pdf của 𝐙 cũng chính là joint pdf của X1,..XM, Y1,...YD, hay joint pdf của 𝐗, 𝐘
>
>
>
> Thế thì như đã học trong Casella và Stat119, dùng Bayes theorem, cho ta: f(𝐱, 𝐲) = f(𝐲|𝐱)f(𝐱) (mà ta nhớ cái theorem này thực ra chỉ là hệ quả từ định nghĩa của conditional probability mà thôi)
>
>
>
> ⇨ f(𝐳) = f(𝐱,𝐲) = f(𝐲|𝐱)f(𝐱)
>
>
>
> Và ta mới xét log của f(𝐳): log f(𝐳) = log \[f(𝐲|𝐱)f(𝐱)\], dùng tính chất hàm log: log(ab) = log(a) + log(b).
>
>
>
> ⇨ log(f(𝐳)) = log f(𝐱) + log f(𝐲|𝐱)
>
>
>
> Tại sao tự nhiên gs Bishop lại lấy log?
>
>
>
> Mình hiểu: là để **dễ làm**, vì mục đích cuối cùng là chỉ ra rằng log f(𝐳) có dạng của log của một hàm số mà phần phụ thuộc 𝐳 có dạng kernel của pdf của một Normal distribution. khi đó, ta sẽ kết luận 𝐙 cũng là Normal variable.
>
>
>
>  Vì sao dễ làm, là vì với log f(𝐱) + log f(𝐲|𝐱), cùng với việc hai cái f đều có dạng: \[normalizing constant\] exp\[-(1/2) quadratic form\], thì ta có:
>
>
>
> Gọi C1, C2 là hai cái normalizing constant của hai cái Normal đó, ta có
>
>
>
> log {C1 exp\[-(1/2) (𝐱-**μ**)ᵀ**Λ**(𝐱-**μ**)\] } + log {C2 exp\[-(1/2)(𝐲-A𝐱-b)ᵀ𝐋(𝐲-A𝐱-b)\]}
>
>
>
> Dùng tính chất hàm log, tách ra:
>
>
>
> log {C1} + log exp\[-(1/2) (𝐱-**μ**)ᵀ**Λ**(𝐱-**μ**)\] } + log {C2} + log exp\[-(1/2)(𝐲-A𝐱-b)ᵀ𝐋(𝐲-A𝐱-b)\]}
>
>
>
> = -(1/2) (𝐱-**μ**)ᵀ**Λ**(𝐱-**μ**) -(1/2)(𝐲-A𝐱-b)ᵀ𝐋(𝐲-A𝐱-b) + log {C1} + log {C2}
>
>
>
>  = -(1/2) (𝐱-**μ**)ᵀ**Λ**(𝐱-**μ**) -(1/2)(𝐲-A𝐱-b)ᵀ𝐋(𝐲-**Ax**-b) + conts (hai term cuối ko dính gì đến 𝐱, 𝐲, ta ko care)
>
>
>
> = -(1/2) \[𝐱ᵀ**Λx** - **μ**ᵀ**Λx** - 𝐱ᵀ**Λμ** + **μ**ᵀ**Λμ** + 𝐲ᵀ**Ly** - 𝐱ᵀ𝐀ᵀ**Ly** - 𝐛ᵀ**Ly** - 𝐲ᵀ**LAx** + 𝐱ᵀ𝐀ᵀ**LAx** + 𝐛ᵀ**LAx** - 𝐲ᵀ**Lb** + 𝐱ᵀ𝐀ᵀ**Lb** + 𝐛ᵀ**Lb**\]
>
>
>
> Nhiệm vụ của là gom các term lại: Cái này thì chỉ là dài dòng, ko có gì khó:
>
>
>
> Đầu tiên kể ra các term bậc hai (tức có dính 2 cái 𝐱, 2 cái 𝐲 hoặc dính 𝐱 và 𝐲):
>
>
>
> = -(1/2) \[𝐱ᵀ**Λx** + 𝐲ᵀ**Ly** - 𝐱ᵀ𝐀ᵀ**Ly** - 𝐲ᵀ**LAx** + 𝐱ᵀ𝐀ᵀ**LAx**\]
>
>
>
> = -(1/2) \[𝐱ᵀ(**Λx** + 𝐀ᵀ**LA**)𝐱 + 𝐲ᵀ**Ly** - 𝐲ᵀ**LAx** - 𝐱ᵀ𝐀ᵀ**Ly**\]
>
>
>
> Bằng các xét cái matrix tạo bởi các block: \[**Λ** + 𝐀ᵀ**LA**, -𝐀ᵀ𝐋; -**LA**, 𝐋\], đặt là 𝐑, thì ta sẽ thấy cái trên chính là: -(1/2) 𝐳ᵀ**Rz**
>
>
>
> Tiếp, ra các term bậc một: (có dính tới 𝐱 hoặc 𝐲):
>
>
>
> \-(1/2) \[- **μ**ᵀ**Λx** - 𝐱ᵀ**Λμ** - 𝐛ᵀ**Ly** + 𝐛ᵀ**LAx** - 𝐲ᵀ**Lb** + 𝐱ᵀ𝐀ᵀ**Lb** + 𝐛ᵀ**Lb**\]
>
>
>
> = -(1/2) \[- 2**μ**ᵀ**Λx** - 2𝐛ᵀ**Ly** + 2𝐛ᵀ**LAx**\]
>
>
>
> = -(1/2) \[- 2(**μ**ᵀ**Λ**-𝐛ᵀ**LA**)𝐱 - 2𝐛ᵀ**Ly**\]
>
>
>
> = (**μ**ᵀ**Λ**-𝐛ᵀ**LA**)𝐱 + 𝐛ᵀ**Ly**
>
>
>
> Bằng cách define vector 𝐡 = \[(**μ**ᵀ**Λ**-𝐛ᵀ**LA**)ᵀ, (𝐛ᵀ𝐋)ᵀ\] = (**Λ**ᵀ**μ**-𝐀ᵀ𝐋ᵀ𝐛, 𝐋ᵀ𝐛) = (**Λμ**-𝐀ᵀ**Lb**, **Lb**) (do tính đối xứng của L, **Λ**) , ta sẽ thấy đây chính là 𝐡ᵀ𝐳
>
>
>
> Còn các term bậc 0, thì gom lại thành constant.
>
>
>
> và do đó, nó có dạng quadratic function của 𝐳: =(1/2)𝐳ᵀ**Rz** + 𝐡ᵀ𝐳 + const giúp kết luận rằng: Với việc log f(𝐳) **có dạng log** **exp** \[**quadratic function** của 𝐳\] ta **suy ra** f(𝐳) **có dạng exp\[quadratic function của z\] nhân some constant**, **và điều này đủ kết luận** **Z nhất định là random variable vector có phân phối Normal**.
>
>
>
> Đồng thời, với cách làm khớp mẫu như hai phần trước đã làm, ta sẽ suy ra mean và covariance của Normal này:
>
>
>
> Với công thức Normal μ, Σ tổng quát, quadratic form sẽ có dạng: -(1/2) \[𝐱ᵀ**Σ⁻¹x** - 2**μ**ᵀ**Σ⁻¹x** + **μ**ᵀ**Σ⁻¹μ**\]
>
>
>
> = -(1/2) 𝐱ᵀ**Σ⁻¹x** + **μ**ᵀ**Σ⁻¹x** -(1/2) **μ**ᵀ**Σ⁻¹μ**
>
>
>
> Khớp mẫu:
>
>
>
> 𝐳ᵀ**Rz** khớp với 𝐱ᵀ**Σ⁻¹x → Covariance matriz, Cov(Z) chính là R⁻¹, hay Precision matrix chính là R**
>
>
>
> **μ**ᵀ**Σ⁻¹x** khớp với 𝐡ᵀ**z ⇨** **μ**ᵀ**Σ⁻¹** khớp với 𝐡ᵀ ⇔ (**μ**\_𝐳)ᵀ𝐑 = 𝐡 ⇔ **μ**\_𝐳 = (**hR**inv)ᵀ = 𝐑invᵀ𝐡ᵀ = 𝐑inv𝐡
>
>
>
>  Nhân vào, kết quả sẽ ra (**μ**; **Aμ** + 𝐛)
>
>
>
> Và để tính ra covariance matrix, R⁻¹, ta có thể dùng công thức 2.76 Schur complement để tính inverse của 𝐑 = \[**Λ** + 𝐀ᵀ**LA**, -𝐀ᵀ𝐋; -**LA**, 𝐋\] = \[**Λ**inv, **Λ**inv𝐀ᵀ; **AΛ**inv, 𝐋inv + **AΛ**inv𝐀ᵀ\] (chỉ là bài toán đại số).

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Bài viết giải thích rất chi tiết và sâu sắc từng bước một, từ định nghĩa phân phối đến lý do chọn log và cách các hệ số kết hợp thành dạng bậc hai của Z, cho thấy sự hiểu biết vững chắc. Để hoàn thiện hơn, bạn có thể thử tự xây dựng tường minh vector mean và ma trận precision/covariance của Z khi nó đã được chứng minh là phân phối Gaussian.

**🔗 See also:** [Phân phối Gaussian có điều kiện](#node-2d1tmn5)

<br>

<a id="node-77d52im"></a>

#### Tính chất phân phối biên Gaussian

<p align="center"><kbd><img src="assets/flck50han1h.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, khi đã có joint distribution f(𝐳), cho thấy cũng là Normal. Ta sẽ đi tìm f(𝐲).
>
>
>
> Có lẽ nên dừng lại review chút xíu:
>
>
>
> Bữa giờ ta ta đã chứng minh:
>
>
>
> Nếu có random vector **X tách thành hai subvector Xa, Xb**, và joint distribution của chúng là Normal(**μ**, **Σ**) hay Normal(**μ**, **Λ⁻¹**), ứng với việc 𝐗 = \[**Xa**; **Xb**\] thì **Σ** và **Λ** (precision matrix) đều thể hiện ở dạng các matrix khối \[**Σaa, Σab; Σba, Σbb\]**, \[**Λaa, Λab; Λba, Λbb**\] thì f(**xa**|**xb**) và f(**xa**) đều là Gaussian. Trong đó với f(**xa**|**xb**) có covariance matrix thể hiện theo các matrix **Λ** sẽ gọn hơn là thể hiện theo **Σ**. Còn với f(**xa**) thì ngược lại, cụ thể ta còn **Xa** \~ Gaussian(**μa**, **Σaa**) (1) (công thức 2.92, 2.93, xem link).
>
>
>
> Sau đó, ta qua bài toán khác là có marginal và conditional đều là nornal: f(𝐱) là normal (**μ**, **Λ**inv), conditional f(𝐲|𝐱) cũng là normal(**Aμ** + 𝐛, L⁻¹), thì a đã chứng minh cho thấy joint distribution f(𝐳), 𝐳 = \[𝐱; 𝐲\] cũng là normal. Và tiếp tục ở đây, ta sẽ nói về marginal f(𝐲).
>
>
>
> Thế thì, lần này ko cần chứng minh gì, chỉ cần áp dụng kết luận đã làm: Vì ta đã có f(𝐳) là normal với mean E(𝐙) = \[**μ**; **Aμ** + 𝐛\] và covariance Cov(𝐙) = \[**Λ**inv, **Λ**inv𝐀ᵀ; **AΛ**inv, 𝐋inv + **AΛ**inv𝐀ᵀ\], theo ý (1) ở trên, có thể kết luận: marginal f(𝐲) cũng là Normal. Với tham số là:
>
>
>
> Mean là **Aμ** + **b.**
>
>
>
> Covariance matrix: Trong chứng minh trước **Σ** = \[**Σaa, Σab; Σba, Σbb\]** là cov(𝐗 = \[**Xa**; **Xb**\]) thì cov(**Xa**) là **Σaa**, nên ở đây Cov(Y) chính là 𝐋inv + **AΛ**inv𝐀ᵀ.
>
>
>
> ⇨ 𝐘 \~ Normal(**Aμ** + 𝐛, 𝐋inv + **AΛ**inv𝐀ᵀ)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Phân tích rất chính xác và sâu sắc, giải thích rõ ràng cách suy ra phân phối biên của y từ phân phối hợp Gaussian, khớp hoàn toàn với các công thức và ý tưởng trong hình ảnh. Việc tổng hợp các kiến thức nền trước đó cũng rất hữu ích và làm tăng độ sâu của ghi chú.

**🔗 See also:** [Hiệp phương sai phân phối biên Σaa](./232_marginal_gaussian.md#node-tmn4pn3)

<br>

<a id="node-15ryxvq"></a>

##### Convolution hai Gaussian

<p align="center"><kbd><img src="assets/sli7amqwvp.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, cùng tìm hiểu đoạn này là sao.
>
>
>
> Ôn lại bối cảnh một chút, bài toán đang làm là, cho marginal và conditional distribution đều là Normal (Gaussian) trong đó mean của f(𝐲|𝐱) là hàm tuyến tính theo 𝐱, còn covariance độc lập với 𝐱. Nên ta có f(𝐱) \~ Normal(**μ**, **Λ**inv) và f(𝐲|𝐱) \~ Normal(𝐀x+𝐛, 𝐋inv).
>
>
>
> Nhiệm vụ là tìm joint distribution, và ta đã thấy nó cũng là Gaussian. Một khi có joint distribution, ta sẽ áp dụng kết quả ở phần trước, để thấy marginal distribution f(𝐲) cũng là Gaussian, có mean là E\[𝐘\] = **Aμ** + 𝐛 và cov(𝐘) = 𝐋inv + 𝐀 **Λ**inv 𝐀ᵀ.
>
>
>
>  Thế thì ở đây mr Bishop nói rằng khi 𝐀 là **Identity matrix** thì distribution của Y hóa ra là convolution của hai Gaussian. Trong Stat110, thực sự thì gs Joe Blizstein chỉ nói rất sơ sơ về convolution. Cụ thể là ông cho ta biết convolution là tổng của hai random variable (ông nói convolution chỉ là một từ bóng bẩy của sum, tổng) X, Y. Có điều, ông chỉ nói nhiêu đó trong bối cảnh là nói về hàm MGF, rằng, MGF sẽ cho ta cách derive pdf của một tổng các random variable dễ hơn là dùng convolution, lợi dụng một tính chất của MGF đó là nếu X, Y độc lập thì MGF của X + Y = MGF của X nhân MGF của Y: M\_(X+Y)(t) = MX(t) × MY(t).
>
>
>
> Thế thì, thử suy nghĩ một chút: Như vậy có thể thấy bài toán thực ra là, ta có hai biến ngẫu nhiên X, Y, biết pdf, và muốn tìm distribution của Z = X + Y.
>
>
>
> Thì cái này, thực ra trong Casella đã học rồi, nó chính là bài toán đổi biến (change of variable): Một cách tổng quát, bài toán là ta có X, Y với joint pdf/pmf fX,Y(x,y). Và muốn tìm distribution của (U,V) = với U = g(X, Y), V = h(X,Y), với hàm g và h có tính chất mapping 1-1 giữa (x,y) trong support set của random variable vector (X,Y) và (u,v) trong support set của (U,V). (hiểu đại khái là, với (x,y) được map với (u,v) thì vẫn có thể có (x', y') khác được map với (u,v) nhưng với điều kiện (u', v') đó phải không được nằm trong support set của (X,Y) (tập các giá trị mà joint pdf fX,Y(x,y) dương). Khi đó: với u = g1(x,y), v = g2(x,y) thì x = h1(u,v), y = h2(u,v). (g, h là hàm nào đó, ko phải đạo hàm). Ta sẽ có:
>
>
>
> fU,V(u,v) = fX,Y(x, y) |∂(x, y)/∂(u, v)| = fX,Y(h1(u, v),h2(u, v)) |∂(x, y)/∂(u, v)|
>
>
>
> Với = |∂(x, y)/∂(u, v)| là trị tuyệt đối của det của Jacobian matrix (đạo hàm của hàm vector → vector (u, v) → (x, y), có hàng 1 là gradient ∇x(u,v): (∂x/∂u, ∂x/∂v), và hàng 2 là gradient ∇y(u,v) = (∂y/∂u, ∂y/∂v).
>
>
>
> Áp dụng vào đây, ta sẽ đặt vector (Z, X) là random vector có được bởi Z = g1(X, Y) = X + Y, V = g2(X, Y) = X (identity function) ⇨ X = h1(Z, V) = V, Y = h2(Z, V) = Z - V.
>
>
>
> Jacobinan: ∇x(z,v) = (∂x/∂z, ∂x/∂v)ᵀ =  (0, 1)ᵀ. ∇y(z,v) = (∂y/∂z, ∂y/v∂) = (1, -1)ᵀ
>
>
>
> ⇨ |det J| = |det \[0, 1; 1, - 1\]| = |1| = 1.
>
>
>
> ⇨ fZ,V(z,v) = fX,Y(x,y) = fX,Y(v, z-v)
>
>
>
> = fX,Y(x, z-x) (Thay v = x)
>
>
>
> Tới đây, cái ta đang có là joint pdf của Z, V (cũng là Z, X). Bằng cách marginalizing over mọi possible của X, ta sẽ có marginal pdf của Z:
>
>
>
> fZ(z) = ∫fZ,V(z,x) dx = ∫fX,Y(x, z-x) dx.
>
>
>
> CÁI NÀY CHÍNH LÀ CÔNG THỨC CỦA CONVOLUTION.
>
>
>
> Và nếu X, Y độc lập, ta có thể tách joint pdf của X, Y thành tích các marginal pdf:
>
>
>
> ⇨ fZ(z) = ∫ fX(x) fY(z-x) dx
>
>
>
> Rồi, nãy giờ là kiểu như để mình hiểu bản chất cái công thức convolution thật ra chỉ là đổi biến. Quay lại đây, ta sẽ cùng nhau xem thử vì sao gs lại nói "nói rằng khi 𝐀 là **Identity matrix** thì distribution của Y hóa ra là convolution của hai Gaussian"
>
>
>
>  Đầu tiên, ta đã kết luận 𝐘 given 𝐱, f(𝐲|𝐱) \~ Normal(**Ax**+𝐛, 𝐋inv), theo location scalae family theorem, khi random variable X \~ một pdf thuộc location scalar familty có location μ thì X - μ sẽ là random varialbe có pdf là standard member của familty đó, tức location = 0. Với normal, nó là một dạng location scale family, nên 𝐓 = 𝐘 - E𝐘 = 𝐘 - **Ax** - 𝐛 chính là một Normal(**0**, 𝐋inv).
>
>
>
> vậy ta có 𝐓 = 𝐘 - **Ax** - 𝐛 ⇔ 𝐘 = 𝐓 + **Ax** + 𝐛.
>
>
>
> Nếu 𝐀 = 𝐈, ta có 𝐘 = 𝐓 + 𝐱 + 𝐛
>
>
>
> Dĩ nhiên ta đang xét 𝐱 fixed, là một observed value của 𝐗.
>
>
>
> Bây giờ, nếu ta tính đến với 𝐗 là random variable, có distribution f(𝐱) là Normal(**μ**, **Λ**inv), thì theo location scale, ta cũng sẽ có 𝐔 = 𝐗 + 𝐛 sẽ là Normal(**μ** + 𝐛, **Λ**inv)
>
>
>
>  Lúc này, 𝐘 = 𝐓 + 𝐗 + 𝐛 = 𝐓 + **U chính là tổng của hai Normal:**
>
>
>
> 𝐓 \~ Normal(**0**, 𝐋inv) và U \~ Normal(**μ** + 𝐛, **Λ**inv)
>
>
>
> Nếu áp dụng công thức covolution ở trên, và giải cái tích phân f(𝐲) = ∫f𝐓(𝐭)f𝐔(𝐲-𝐭)d𝐭 thay công thức pdf của 𝐓 và 𝐔 vào, ta có thể chứng minh rằng quả thật đây là Gaussian có mean là tổng mean, covariance là tổng covariance. Hoặc làm như trong Stat110, dùng MGF, ta cũng có thể chứng minh điều này. Nhưng cái chính là, một khi đã chỉ ra 𝐘 là tổng của 𝐓, 𝐔 thì dùng tính linearity ta nhất định phải có mean bằng tổng mean. Và vì tính độc lập của T, U ta sẽ có covariance bằng tổng covariance:
>
>
>
> Và mean của 𝐘, E𝐘 = **μ** + 𝐛, bằng **0** + **μ** + **b =** E**T +** E𝐔.
>
>
>
> Còn covarinance Cov(𝐘) = 𝐋inv + **Λ**inv = Cov(𝐓) + Cov(𝐔)
>
>
>
> Và kết quả mà mình đã làm ở phần trước - marginal pdf của 𝐘, f(𝐲) cho thấy nó Normal(**Aμ** + 𝐛, 𝐋inv + **AΛ**inv𝐀ᵀ) , với 𝐀 = 𝐈, Normal(**μ** + 𝐛, 𝐋inv + **Λ**inv) đã xác nhận điều này.
>
>
>
> Do đó, gs mới nói, với 𝐀 = 𝐈 thì hóa ra 𝐘 chính là tổng của hai Normal random variable

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Bài viết rất chính xác và có chiều sâu vượt trội. Cách giải thích cặn kẽ về bản chất của phép tích chập (convolution) thông qua đổi biến, cùng với việc áp dụng chi tiết vào trường hợp A=I, giúp người đọc nắm vững kiến thức một cách toàn diện. Đây là một phân tích xuất sắc.

**🔗 See also:** [Variance of the Predictive Distribution](./332_predictive_distribution.md#node-w88dcdy)

<br>

<a id="node-2d1tmn5"></a>

###### Phân phối Gaussian có điều kiện

<p align="center"><kbd><img src="assets/gudg6jzgga8.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, cuối cùng là ta sẽ tìm f(𝐱|𝐲) (nhắc lại nhé, đề bài cho ta có f(𝐱) \~ Normal(**μ**, **Λ**inv), f(𝐲|𝐱) là Normal(**Ax**+𝐛, 𝐋inv), xong chứng minh f(𝐱,𝐲) và f(𝐲) cũng là Gaussian, giờ đến cái f(𝐱|𝐲):
>
>
>
> Thì nhờ đã có f(𝐱,𝐲) ta cũng chỉ dùng cái kết quả ở mấy phần trước, khi trong đó ta có 𝐗 = \[**Xa**; **Xb**\] có pdf Normal(**μ**, **Σ**) với **Σ** = \[**Σaa**, **Σab**; **Σba**, **Σbb**\] và **Σ**inv = **Λ** = \[**Λaa**, **Λab**; **Λba**, **Λbb**\], thì f(**xa**|**xb**) sẽ là Normal có **μa|b** = **μa** - **Λaa⁻¹ Λab** (**xb** - **μb**) và covariance matrix là **Σa|b** = (**Λaa**)⁻¹.
>
>
>
> Vậy thì áp dụng kết quả đó, cùng với ta có joint distribution của 𝐗, 𝐘 là Normal có mean = \[**μ**; **Aμ** + 𝐛\], precision = \[**Λ** + 𝐀ᵀ**LA**, -𝐀ᵀ𝐋; -**LA**, 𝐋\]
>
>
>
> và distribution của 𝐘 là Normal(**μ** + 𝐛, 𝐋inv + **Λ**inv)
>
>
>
> ⇨ **Λaa** ứng với **Λ** + 𝐀ᵀ**LA**, **Λ**ab ứng với -𝐀ᵀ𝐋, **xb** ứng với 𝐲, **μb** ứng với E\[𝐘\] =
>
> Rồi, cuối cùng là ta sẽ tìm f(𝐱|𝐲) (nhắc lại nhé, đề bài cho ta có f(𝐱) \~ Normal(**μ**, **Λ**inv), f(𝐲|𝐱) là Normal(**Ax**+𝐛, 𝐋inv), xong chứng minh f(𝐱,𝐲) và f(𝐲) cũng là Gaussian, giờ đến cái f(𝐱|𝐲):
>
>
>
> Thì nhờ đã có f(𝐱,𝐲) ta cũng chỉ dùng cái kết quả ở mấy phần trước, khi trong đó ta có 𝐗 = \[**Xa**; **Xb**\] có pdf Normal(**μ**, **Σ**) với **Σ** = \[**Σaa**, **Σab**; **Σba**, **Σbb**\] và **Σ**inv = **Λ** = \[**Λaa**, **Λab**; **Λba**, **Λbb**\], thì f(**xa**|**xb**) sẽ là Normal có **μa|b** = **μa** - **Λaa⁻¹ Λab** (**xb** - **μb**) và covariance matrix là **Σa|b** = (**Λaa**)⁻¹.
>
>
>
> Vậy thì áp dụng kết quả đó, cùng với ta có joint distribution của 𝐗, 𝐘 là Normal có mean = \[**μ**; **Aμ** + 𝐛\], precision = \[**Λ** + 𝐀ᵀ**LA**, -𝐀ᵀ𝐋; -**LA**, 𝐋\]
>
>
>
> và distribution của 𝐘 là Normal(**Aμ** + 𝐛, 𝐋inv + **AΛ**inv𝐀ᵀ)
>
>
>
> ⇨ **Λaa** ứng với **Λ** + 𝐀ᵀ**LA**, **Λ**ab ứng với -𝐀ᵀ𝐋, **xb** ứng với 𝐲, **μb** ứng với E\[𝐘\] = **Aμ** + 𝐛
>
>
>
> ta có thể nói ngay: f(𝐱|𝐲) cũng là pdf của Normal, có mean:
>
>
>
> E\[𝐗|𝐲\]  
>
>
>
> (sẽ áp vào công thức tương ứng với **μa** - **Λaa⁻¹ Λab** (**xb** - **μb**))
>
>
>
> = **μ** - (**Λ** + 𝐀ᵀ**LA**)\⁻¹ (-𝐀ᵀ𝐋)(𝐲 - **Aμ** - 𝐛)
>
>
>
> = **μ** + (**Λ** + 𝐀ᵀ**LA**)\⁻¹ (𝐀ᵀ𝐋)(𝐲 - **Aμ** - 𝐛) 
>
>
>
> = (**Λ** + 𝐀ᵀ**LA**)⁻¹(**Λ** + 𝐀ᵀ**LA**)**μ** + (**Λ** + 𝐀ᵀ**LA**)\⁻¹\[𝐀ᵀ𝐋(𝐲 - 𝐛) - 𝐀ᵀ**LAμ**\] 
>
>
>
> = (**Λ** + 𝐀ᵀ**LA**)⁻¹{(**Λ** + 𝐀ᵀ**LA**)**μ** + \[𝐀ᵀ𝐋(𝐲 - 𝐛) - 𝐀ᵀ**LAμ**\]}
>
>
>
> = (**Λ** + 𝐀ᵀ**LA**)⁻¹ \[**Λμ** + 𝐀ᵀ**LAμ** + 𝐀ᵀ𝐋(𝐲 - 𝐛) - 𝐀ᵀ**LAμ**\]
>
>
>
> = (**Λ** + 𝐀ᵀ**LA**)⁻¹ \[**Λμ** + 𝐀ᵀ𝐋(𝐲 - 𝐛)\]
>
>
>
> = (**Λ** + 𝐀ᵀ**LA**)⁻¹ \[𝐀ᵀ𝐋(𝐲 - 𝐛) + **Λμ**\] → Đây là 2.111
>
>
>
> Cov(𝐗|𝐲) 
>
>
>
> (sẽ áp vào công thức (**Λaa**)⁻¹) 
>
>
>
> = (**Λ** + 𝐀ᵀ**LA**)⁻¹ → Đây là 2.112

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Bài giải rất chi tiết, logic và chính xác từng bước một trong việc áp dụng kết quả từ phân phối Gaussian có điều kiện và ma trận độ chính xác, hoàn toàn khớp với hình ảnh gốc. Việc tự sửa lỗi nhỏ về phân phối biên của Y cho thấy sự cẩn trọng và hiểu biết sâu sắc.

**🔗 See also:** [Hiệp phương sai Gaussian điều kiện](./231_conditional_gaussian.md#node-mm664xt) · [Phân phối kết hợp Gaussian](#node-axpsoob)

<br>

<a id="node-zswmsts"></a>

###### Phân bố tiên nghiệm và hậu nghiệm

<p align="center"><kbd><img src="assets/3koe3k5kyqk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jvtbxctroo.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng, gs cho rằng ta có thể coi f(𝐱) như prior distribution của 𝐗 và f(𝐱|𝐲) là posterior distribution của 𝐗 dựa trên 𝐘 = 𝐲. 
>
>
>
> Và tóm tắt lại các kết quả ta đã tự làm trong bảng sau.

**🔗 See also:** [Bayesian Linear Regression Posterior Update](./331_bayesian_linear_regression.md#node-fv65lte) · [3.3.2 Predictive distribution](./332_predictive_distribution.md#node-wdjepxb) · [Tính toán hàm evidence](./351_evaluation_of_the_evidence_function.md#node-u15ayc8)

<br>

