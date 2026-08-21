# 3.5.3 Effective number of parameters

📊 **Progress:** `1` Notes | `1` Screenshots | `1` AI Reviews

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
> Và đây, với tư cách là phương trình theo của **w**, biến đổi thêm ta sẽ thấy nó chính là phương trình đường ellipse.  
>
>
>
> Đặt A = **Φ**T**Φ**, **b** = **Φ**T**t**, phương trình trở thành:
>
>
>
> **w**T**Aw** - 2**b**T**w** = c5
>
>
>
> ---
>
>
>
> Tới đây, đổi biến ta sẽ thấy theo biến mới, nó sẽ trở thành phương trình ellipsoid. Và để biết đổi biến thế nào, ta sẽ làm theo kiểu ép kiểu (tức là đi từ kết quả ra ngược lại hiện tại).
>
>
>
> Thì trong phương trình theo cái biến mới, sẽ có dạng **u**T**Au** = c6 với **u** = **w** - **m** (giá trị m là cái cần tìm)
>
>
>
> Thế thì bắt đầu với cái đích mong muốn (**w** - **m**)T**A**(**w** - **m**) = c6.
>
>
>
> Khai triển vế trái ta có **w**T**Aw** - **m**T**Aw** + **w**T**Am** - **m**T**Am**
>
>
>
> = **w**T**Aw** - 2**m**T**Aw** - **m**T**Am**
>
>
>
> Cho -2**b**T**w** = - 2**m**T**Aw**, ta suy ra **b**T = **m**T**A** ⇔ **A**T**m** = **b**
>
>
>
> ⇔ **m** = (**A**T)inv **b** = **A**inv **b** =(**Φ**T**Φ**)inv **Φ**T**t**
>
>
>
> Như vậy, tới đây ta đã biết cách biến đổi: Đó là:
>
>
>
> Từ **w**T**Aw** - 2**b**T**w** = c5
>
>
>
> Ta sẽ cộng thêm hai vế cho (- **m**T**Am**) với **m** = **A**inv **b** =(**Φ**T**Φ**)inv **Φ**T**t**, ta có:
>
>
>
> **w**T**Aw** - 2**b**T**w** - **m**T**Am** = c5 - **m**T**Am**
>
>
>
> Khi đó vế trái sẽ trở thành (**w** - **m**)T**A**(**w** - **m**), và vế phải vẫn là constant, đặt là c6. Ta có:
>
>
>
> (**w** - **m**)T**A**(**w** - **m**) = c6.
>
>
>
> Và đặt **z** = **w** - **m** thì, phương trình trên là **z**T**Az** = c6.
>
>
>
> Tới đây làm thêm vài bước nữa ta sẽ thấy cái này chính là phương trình của một ellipsoid:
>
>
>
> Thay **A** = **Φ**T**Φ** vào lại:
>
>
>
> **z**T**Φ**T**Φz** = c6.
>
>
>
> ---
>
>
>
> Nhớ lại trong MIT 18.06 đã học, là với symmetric matrix size n × n thì luôn tồn tại đủ bộ eigenvector độc lập, và hơn thế nữa, ta còn luôn có thể chọn được một bộ orthogonal eigenvector. Do đó matrix này luôn có thể phân tách nó thành **Q** **Λ** **Q**T với **Q** là orthogonal matrix có các cột là bộ orthonormal eigenvector (vuông góc, và đã chuyển về unit norm) và **Λ** là diagonal matrix chứa các eigenvalue trên đường chéo. Vậy thì **A** = **Φ**T**Φ** đương nhiên là matrix đối xứng (vì (**Φ**T**Φ**)T = **Φ**T(**Φ**T)T = **Φ**T**Φ**). Nên ta có **Φ**T**Φ** = **Q** **Λ** **Q**T
>
>
>
> Khi đó, phương trình trở thành **z**T**Q** **Λ** **Q**T**z** = c6.
>
>
>
> Đặt **y** = **Q**T**z**, ta có **y**T**Λy** = c6.
>
>
>
> và với **Λ** là diagonal matrix mà đường chéo là các eigenvalue λ1,....λM của ΦTΦ thì **y**T**Λy** = Σi=1:M λi × yi^2. Ta có:
>
>
>
> λ1 × y1^2 + λ2 × y2^2 + ...λM × yM^2 = c6
>
>
>
> Chia hai vế cho c6:
>
>
>
> λ1/c6 × y1^2 + λ2/c6 × y2^2 + ...λM/c6 × yM^2 = 1
>
>
>
> ⇔ y1^2 / (c6/λ1) + y2^2/(c6/λ2) + ...+ yM^2/(c6/λM) = 1
>
>
>
> Đây chính là phương trình ellipsoid có dạng tổng quát trong 3D đã học hồi cấp 3 là: x^2/a^2 + y^2/b^2 + z^2/c^2 = 1.
>
>
>
> ---
>
>
>
> Tóm lại, quả thật cái contour của f(𝒟|**w**) tức là ta cho nó bằng hằng số: 𝒩(**t**|**Φw**, (1/β)**I**) = c
>
>
>
> biến đổi đại số một hồi, ta ra được
>
>
>
> ⇔ **w**T**Φ**T**Φw** - 2**t**T**Φw** = c5
>
>
>
> Sau khi đổi biến hai lần:
>
>
>
> Đặt **z** = **w** - **m**, với **m** = **A**inv **b** =(**Φ**T**Φ**)inv **Φ**T**t**, có thể thấy đây chính là phép tịnh tiến
>
>
>
> Và **y** = **Q**T**z**, với Q là orthogonal matrix, ta biết đây là phép (biến đổi tuyến tính) xoay
>
>
>
> thì kết quả ta có **y**T**Λy** = c6, là phương trình của ellipsoid.
>
>
>
> ---
>
>
>
> Giờ nói thêm chút về cái bước y = **Q**T**z**.
>
>
>
> Cũng là dịp để ôn kiến thức đã học trong MIT 18.06: Linear transformation. Sẽ giúp ta hiểu rõ vì sao nói **cái ellipse nói trên nó axis aligned với eigenvector ui** (eigenvectorcủa **Φ**T**Φ**):
>
>
>
> Cụ thể đây chính là lúc mình áp dụng kiến thức về Change of basis matrix:
>
>
>
> Đầu tiên, ta đã được biết, thế nào gọi là phép biến đổi tuyến tính (linear transformation): Là phép biến đổi thỏa mãn tính chất T(c**u** + d**v**) = cT(**u**) + dT(**v**) (c, d ở đây là scalar, **u**, **v** là vector). Thế thì từ đó, ta thấy nếu lấy phép biến đổi T(**v**) là là: Lấy **A** nhân vector **u**, T(**u**) = **Au** thì T(c**u** + d**v**) = **A**(c**u** + d**v**) cũng bằng c × A**u** + d × A**v** = c T(**u**) + d T(**v**). Do đó phép nhân matrix **A** với vector **u** cũng là một linear transformation.
>
>
>
> Thế thì câu hỏi là, giả sử ta có matrix **A**, ta sẽ thực hiện phép biến đổi bởi nó thì dễ rồi. Nhưng nếu ta có phép biến đổi tuyến tính, và muốn biết matrix **A** đứng sau nó là gì thì sao. Ví dụ, phép xoay một góc α, ta biết nó là phép biến đổi tuyến tính, vậy matrix **A** của nó là gì?
>
>
>
> **Hiểu cái này rất quan trọng: nói A đại diện, thì tức là giả sử ta có vector x có tọa độ trong basis v's là a1, a2,...Thì biến đổi bởi T(.), để thành T(a). Và ta lấy tọa độ của kết qủa này theo basis w's của output space, thì A làm hết mọi chuyện này, tức là Ax sẽ cho ta cái tọa độ của T(x) trong basis w's. Nên:**
>
>
>
> **Ax** là tọa độ của vector T(**x**) trong basis w's: **Ax** = \[T(**x**)\]\_w's. Nhớ: Đây là hai vector tọa độ, khác vector x là vector trừu tượng, trong input space, T(x) trong output space.
>
>
>
> Và ta sẽ có cách lập luận để tìm **A** đại diện cho / đứng sau phép biến đổi tuyến tính T(.) như sau:
>
>
>
> Gọi **v**1,...**v**n và **w**1,...**w**m là basis của input space và output space
>
>
>
> Xét vector **a** có tọa độ (a1,...an) trong input space, kí hiệu \[**a**\]\_v's. Ta có:
>
>
>
> **a** = a1 **v**1 + a2 **v**2 + ...an **v**n.
>
>
>
> Biến đổi **a** bởi T(.), ta có T(**a**)
>
>
>
> Vì T(.) là phép biến đổi tuyến tính, nên:
>
>
>
> T(**a**) = T(a1 **v**1 + a2 **v**2 + ...an **v**n) = a1 T(**v**1) + a2 T(**v**2) + ... + an T(**v**n)
>
>
>
> Ở đây ta có vector T(**a**) của vế trái = vector (là tổng của các vector a1 T(**v**1) + a2 T(**v**2) + ... + an T(**v**n)) bên vế phải. Mà hai vector bằng nhau, thì tọa độ của chúng trong một hệ tọa độ phải bằng nhau. **Nên tọa độ trong basis w's của chúng bằng nhau**, ta có:
>
>
>
> ⇒ \[T(**a**)\]\_w's = \[a1 T(**v**1) + a2 T(**v**2) + ... + an T(**v**n)\]\_w's
>
>
>
> mà vế phải là **tọa độ của một tổng các vector**, sẽ là **tổng các tọa độ**. Ví dụ α\[u1, u2\]T + β\[v1, v2\]T = \[αu1 + βv1, αu2 + βv2\]T. Nên ta có:
>
>
>
> \[T(**a**)\]\_w's = \[a1 T(**v**1)\]\_w's + \[a2 T(**v**2)\]\_w's + ... + \[an T(**v**n)\]\_w's
>
>
>
> ⇔ \[T(**a**)\]\_w's = a1 × \[T(**v**1)\]\_w's + a2 × \[T(**v**2)\]\_w's + ... + an × \[T(**v**n)\]\_w's
>
>
>
> ---
>
>
>
> Rồi, lại xét **Aa**, theo góc nhìn nhân matrix với vector, chính là linear combination các **vector cột** của matrix A (đặt là các vector **c**1, **c**2,..) bởi hệ số là các phần tử của **a** (cũng là tọa độ a1, a2,...của vector **a**)
>
>
>
> **Aa** = a1 **c**1  + a2 **c**2 + ... an **c**n
>
>
>
> Và kết qủa của việc linear combination này, sẽ là một column vector.
>
>
>
> Mà giá trị của column vector này chính là tọa độ của T(**a**) trong basis w's vì ta đang đi xây dựng matrix **A** đại diện cho phép biến đổi tuýến tính T(), nên theo định nghĩa nó sẽ giúp tính ra tọa độ của T(**a**) trong basis w's
>
>
>
> **Aa** = \[T(**a**)\]\_w's
>
>
>
> nên
>
>
>
> a1 × \[vector cột 1\]  + a2 × \[vector cột 2\] + ... an × \[vector cột n\]
>
>
>
> = a1 × \[T(**v**1)\]\_w's + a2 × \[T(**v**2)\]\_w's + ... + an × \[T(**v**n)\]\_w's
>
>
>
> Vậy \[vector cột 1\] của **A** chính là \[T(**v**1)\]\_w's, \[vector cột 2\] của **A** chính là \[T(**v**2)\]\_w's....
>
>
>
> Từ đó ta có cái rule như sau:
>
>
>
> Chuẩn bị input basis **v**1,**v**1.... Biến đổi **v**1,**v**2... bởi T(.), và lấy tọa độ của chúng trong basis **w**'s. 
>
> Thì **cột j của A** chính là tọa độ của T(**v**j) trong basis **w**'s.
>
>
>
> \[Cột j của A\]  = \[T(**v**j)\]\_w's
>
>
>
> ---
>
>
>
> Tiếp ta sẽ xét phép biến đổi identity: T(**x**) = **x**, tức là không làm gì, chỉ thay basis từ v's sang w's
>
>
>
> Thì theo rule đó matrix A giúp thay đổi basis sẽ được xây dựng như sau
>
>
>
> Biến đổi **v**1, thể hiện nó trong basis **w**'s, tọa độ của nó trong basis w's chính là giá trị cột 1 của A:
>
>
>
> \[Cột 1 của A\] = \[T(**v**1)\]\_w's
>
>
>
> Tương tự vậy:
>
>
>
> \[Cột 2 của A\] = \[T(**v**2)\]\_w's
>
>
>
> Mà T(**v**1) = **v**1, T(**v**2) = **v**2,...do T(.) đang xét là phép biến đổi identity.
>
>
>
> Nên: (theo nguyên tắc vector = vector thì tọa độ = toạ độ)
>
>
>
> \[T(**v**1)\]\_w's = \[**v**1\]\_w's, \[T(**v**2)\]\_w's = \[**v**2\]\_w's,...
>
>
>
> Vậy \[Cột 1 của A\] = \[**v**1\]\_w's, \[Cột 2 của A\] = \[**v**2\]\_w's,...
>
>
>
> Mà \[Cột 1 của A\] = \[**v**1\]\_w's, nói bằng lời thì có nghĩa là giá trị cột 1 của matrix A là tọa độ của vector **v**1 trong basis w's. 
>
>
>
> suy ra **v**1 = linear combination của **w**1,...**w**m với hệ số là cột 1 của A.
>
>
>
> Đặt **W** là matrix các cột **w**1, **w**2,...thì điều này chính là **v**1 = **W** **c**1
>
>
>
> Tương tự
>
>
>
> \[Cột 2 của A\] = \[**v**2\]\_w's nên **v**2 = **W** **c**2.
>
>
>
> ...
>
>
>
> Và đặt **v**1, **v**2 vào thành các cột của matrix **V** ta sẽ có **V** = **W** **A**
>
>
>
> ⟹ **A** = **W**inv **V**
>
>
>
> Và do đó, nếu input space là basis e's, **V** = **I**, thì change of basis sang basis w's chính là **W**inv.
>
>
>
> ---
>
>
>
> Từ đó, quay lại bài này, ta sẽ thấy **Q**T**z** là cái gì? 
>
>
>
> **z** chính là vector **w**-**m**, có tọa độ vẫn là tọa độ trong basis e's.
>
>
>
> Còn **Q**T, do **Q** là orthogonal matrix, nên **Q**T = **Q**inv: **Q**T chính là **Q**inv
>
>
>
> Và như đã hiểu ở trên, tọa độ của **Q**inv **u**, chính là chuyển tọa độ của vector **z** từ basis e's sang basis **q**1, **q**2 (hay **u**1, **u**2....) là các cột của **Q**, và chúng chính là các eigenvector của **Φ**T**Φ**. 
>
>
>
> Và với việc ta thấy phương trình trở thành phương trình ellipse, giúp ta hiểu được rằng: **trong hệ trục gốc, cái ellipse này nằm xéo (bị xoay)** nên khi xoay hệ trục về thẳng góc với các eigenvector thì cái ellipse này nằm thẳng (axis aligne)
>
>
>
> Còn 1 cách giải thích khác:
>
>
>
> Gọi **q**1,**q**2,.. (trong sách là **u**1,**u**2,..) là các orthogonal eigenvector của **Φ**T**Φ**.
>
>
>
> Thử tìm kết quả của phép chiếu lên span{**q**1,**q**2,..}.
>
>
>
> Xét vector **a** có tọa độ **a**1,**a**2,...trong basis e's
>
>
>
> Chiếu **a** lên span{q1,q2,..} Thì ta có p, với p = linear combination của q's bởi hệ số x1,x2,.. nào đó **p** = **q**1x1 + **q**2x2 + ...
>
>
>
> Tuy nhiên, sự thật là **Q** full rank, nên a vốn đã nằm trong span{**q**1,**q**2,..}. Nên hình chiếu của a lên subspace này là chính nó. Ta có
>
>
>
> **a** = **Qx** với **x** là vector tọa độ của **a** (cũng là p) trong basis q's.
>
>
>
> Nhân hai vế cho QT:
>
>
>
> QTa = QTQx 
>
>
>
> ⇔ x = QTa
>
>
>
> À như vậy, ta thấy QTa chính là tọa độ của a trong basis q1,q2,..
>
>
>
> Thì y như vậy, QTz sẽ chính là ta chiếu tọa độ của z lên các eigenvector q1,q2,..để có tọa độ mới. Thì đây cũng chính là cùng ý nghĩa với xoay hệ trục để đổi tọa độ sang basis q's (hay u's, là eigenvector của design matrix)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Ghi chú vô cùng chi tiết và chính xác, tự chứng minh mạch lạc từ phân phối Gaussian đến phương trình ellipsoid và giải thích rất rõ ràng bản chất đại số tuyến tính của phép xoay trục tọa độ theo eigenvectors. Không có điểm gì cần cải thiện thêm.

**🔗 See also:** [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj) · [Chuyển tọa độ eigenvector](./230_gaussian_distribution.md#node-c9cpfzj)

<br>

