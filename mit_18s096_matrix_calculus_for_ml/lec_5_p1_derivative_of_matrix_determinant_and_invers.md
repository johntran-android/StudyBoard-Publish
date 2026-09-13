# Lec 5 P1: Derivative Of Matrix Determinant And Invers

📊 **Progress:** `7` Notes | `6` Screenshots | `6` AI Reviews

---
<a id="node-6mechld"></a>

> [!NOTE]
> LEC 5 P1: DERIVATIVE OF MATRIX DETERMINANT
> AND INVERS

<br>

<a id="node-18hca7g"></a>

## Chuẩn và đạo hàm

<p align="center"><kbd><img src="assets/a2vinf2fyvl.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là bài trước ta còn nhớ rằng để mở rộng khái niệm gradient
> ra đối với các vector space khác (ví dụ matrix) thì ta cần define phép
> inner product. Vì như ta đã biết, khi x thay đổi chút xíu dx kéo theo
> f(x) thay đổi df = f(x + dx) - f(x) thì sự thay đổi này là một linear operator
> act on dx: df = f'(x)[dx]. và khi x, dx là vector thì linear operator act on
> dx để cho ra df là scalar thì nó chỉ có thể là phép inner product của
> một vector nào đó (chính là gradient vector) với dx.
>
>
>
> Do đó, để tính đạo hàm, hay tìm gradient vector đối với function nhận
> vector ở dạng mở rộng (ví dụ matrix) output ra scalar f thì ta chỉ cần
> cho thấy df = [vector gì đó] . dx. Và do đó ta cần xác định phép inner
> product giữa hai vector với nhau (ví dụ giữa hai matrix)
>
>
>
> Thế thì bài trước ta đã làm việc này, đã biết inner product giữa hai matrix
> là gì rồi chính là = Σij Aij * Bij = tr(AᵀB).
>
>
>
> Thì nay, gs nhắc đến ta còn phải có thêm một thứ nữa, đó là norm của 
> vector (còn nhớ khi vector space đã định nghĩa phép inner product thì
> nó gọi là Hilbert space, thì nay nếu có thêm norm thì nó là Banach space,
> đây chỉ là những cái tên bóng bẩy, chứ không có gì ghê gớm)
>
>
>
> RỒi gs cũng nói về norm, là bất cứ vector -> scalar function nào thỏa
> 3 tính chất như không âm (trừ khi vector 0), scaling, và triangle inequality
>
>
>
> Và thật ra khi ta định nghĩa ra inner product của hai vector thì ta đã có 
> luôn norm rồi. ||u|| = √(u.u)
>
>
>
> Cuối cùng gs nói về lí do ngầm ẩn khiến ta cần có norm là vì như đã biết
> khi x thay đổi một khoảng nhỏ (không phải infinitesimal dx) δx thì f(x) thay
> đổi δf = f(x + δx) - f(x) thì nó không phải là hàm tuyến tính theo δx mà có
> thể nó còn những term bậc cao nữa:
>
>
>
> f(x + δx) - f(x) = f'(x)[δx] + o(δx).
>
>
>
> Nhưng vấn đề là khi δx rất nhỏ, ta có thể bỏ đi những term bậc cao này
> vì chúng cũng rất rất nhỏ để rồi: ta có xấp xỉ f(x + δx) - f(x) ≈ f'(x)[δx]
>
>
>
> và khi δx vô cùng nhỏ (dx) thì ta có f(x + dx) - f(x) = f'(x)[dx]
>
>
>
> Vậy, khi nói o(δx) (với δx là vector) thì đây là những vector function mà 
> norm của nó trở nên rất nhỏ khi norm của δx nhỏ (tương tự như với scalar
> case là o(δx) rất nhỏ khi δx nhỏ vậy). Và do đó có thể thấy ta cần norm

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ⚠️ **88/100** · ✓ Move on
>
> Ghi chú nắm rất tốt trực giác toán học và hiểu rõ lý do bản chất vì sao cần chuẩn (norm) để định nghĩa đạo hàm trên không gian vector. Có một vài điểm chưa thật chuẩn xác về định nghĩa toán học của ký hiệu o nhỏ và phân loại không gian giải tích.
>
> **🟡 Minor issues**
>
> **1.** *"còn nhớ khi vector space đã định nghĩa phép inner product thì nó gọi là Hilbert space, thì nay nếu có thêm norm thì nó là Banach space"*
>
> Khái niệm bị đảo ngược: Không gian Banach là không gian vector có chuẩn (norm) và đầy đủ (complete). Nếu không gian đó có thêm tích vô hướng cảm sinh ra chuẩn thì nó là không gian Hilbert. Mọi không gian Hilbert đều là không gian Banach, chứ không phải có tích vô hướng rồi thêm chuẩn mới thành Banach.
>
> **2.** *"đây là những vector function mà norm của nó trở nên rất nhỏ khi norm của δx nhỏ"*
>
> Định nghĩa tiểu o (little-o) đòi hỏi sai số này phải triệt tiêu nhanh hơn bậc một của ||δx||, tức là tỷ số sai số trên bước nhảy phải tiến về 0: lim (||o(δx)|| / ||δx||) = 0, chứ không chỉ đơn thuần là trở nên nhỏ khi ||δx|| nhỏ.
>
>
> **✓ Strengths**
> - Nắm bắt chính xác vai trò của norm trong đạo hàm: dùng để đo lường độ lớn và định nghĩa khái niệm 'nhỏ' (khoảng cách/tiến về 0) trên không gian vector.
> - Kết nối rất logic với kiến thức bài trước về biểu diễn toán tử tuyến tính qua tích vô hướng và ma trận.
> - Hiểu đúng bản chất của đạo hàm như một xấp xỉ tuyến tính địa phương kèm theo phần dư bậc cao.
>
> **💡 Deeper notes**
> - Đạo hàm yêu cầu chuẩn trên cả hai không gian: trong biểu thức lim ||o(δx)|| / ||δx|| = 0, chuẩn ở mẫu nằm trên không gian đầu vào (input space) còn chuẩn ở tử nằm trên không gian đầu ra (output space).

<br>

<a id="node-s7yw4k5"></a>

### Gradient của định thức

<p align="center"><kbd><img src="assets/vetc4944ne.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, ta sẽ xét qua gradient của det A (tức derivative của f(A) wrt A với f(A) = det A
>
>
>
> Thì đại khái là thầy Steve cho biết một số công thức của nó là cofactor(A), hay det A . (A⁻¹)ᵀ hay adj(Aᵀ)
>
>
>
> Trước khi ta đi chứng minh những công thức trên thì nên biết một số định nghĩa như:
>
>
>
> A⁻¹ = adj(A) / det(A) = cofactor(A)ᵀ / det(A)
>
>
>
> ⇨ adj(A) = det(A) A⁻¹
>
>
>
> ⇨ cofactor(A) = (A⁻¹)ᵀ  det(A) = adj(A)ᵀ

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **95/100** · ✓ Move on
>
> Ghi chú nắm rất chính xác và đầy đủ các công thức liên hệ giữa gradient của định thức, ma trận phụ hợp (adjugate) và cofactor.
>
> **🟡 Minor issues**
>
> **1.** *"A⁻¹ = adj(A) / det(A) = cofactor(A)ᵀ / det(A)"*
>
> Các công thức chứa A⁻¹ ngầm định ma trận A là khả nghịch (det(A) ≠ 0). Khi A suy biến (det(A) = 0), gradient của det(A) vẫn tồn tại và bằng cofactor(A) hay adj(Aᵀ), nhưng không thể biểu diễn qua A⁻¹.
>
>
> **✓ Strengths**
> - Ghi chép chính xác mối quan hệ giữa gradient của det(A), cofactor(A) và adj(Aᵀ).
> - Nhận diện đúng mối liên hệ chuyển vị giữa cofactor matrix và adjugate matrix.
>
> **💡 Deeper notes**
> - Đẳng thức ∇(det A) = adj(Aᵀ) luôn đúng với mọi ma trận vuông (kể cả khi det(A) = 0), trong khi dạng (det A)A⁻ᵀ chỉ áp dụng được khi A khả nghịch.

<br>

<a id="node-xi67snz"></a>

#### Đạo hàm của định thức

<p align="center"><kbd><img src="assets/h6ndxqhgftu.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi để chứng minh ∇f(A) = cofactor(A) có thể rất dễ:
>
>
>
> Nhờ MIT 18.06 ta đã biết công thức tính det A theo cofactor formula:
>
>
>
> Ta có thể chọn một row, hoặc một cột bất kì (ví dụ chọn row i) và tính det A bằng: Σj Aij \* Cij
>
>
>
> với Aij là các components của row i của A
>
>
>
> còn Cij là cofactor của aij, được định nghĩa là determinant của matrix bỏ đi row i, column j nhân với +1 hoặc -1 tùy vào việc i+j là chẵn hay lẻ.
>
>
>
> Dĩ nhiên có thể thấy nó là scalar (vì là det của một matrix)
>
>
>
> Thế thì, từ đó có thể thấy rằng:
>
>
>
> Xét partial derivative ∂/∂Aij \[det(A)\] thì chính là bằng Cij, bởi vì:
>
>
>
> det A = Ai1Ci1 + Ai2Ci2 + ...AinCin
>
>
>
> Do đó, derivative của det A wrt A sẽ là matrix mà component ij (là ∂det(A) / ∂Aij) = Cij.
>
>
>
> Vậy nên derivative của det(A) wrt A là matrix C:
>
>
>
> ∇det(A) = cofactor(A)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất chính xác, nắm bắt hoàn hảo bản chất của phép khai triển Laplace (cofactor expansion) để suy ra đạo hàm của định thức theo ma trận.
>
> **🟡 Minor issues**
>
> **1.** *"Xét partial derivative ∂det(A)/Aij thì chính là bằng Cij"*
>
> Ký hiệu bị thiếu ký hiệu đạo hàm riêng ở mẫu số, viết chuẩn phải là ∂det(A)/∂Aij thay vì ∂det(A)/Aij.
>
>
> **✓ Strengths**
> - Hiểu chính xác định nghĩa và công thức khai triển Laplace của định thức theo hàng/cột.
> - Nhận thức rõ cofactor C_ij không phụ thuộc vào phần tử A_ij (do đã bỏ đi hàng i và cột j), từ đó việc lấy đạo hàm riêng theo A_ij trực tiếp cho ra C_ij.
> - Kết luận chuẩn xác về cấu trúc ma trận gradient là ma trận các cofactor.
>
> **💡 Deeper notes**
> - Ma trận chuyển vị của ma trận cofactor chính là ma trận phụ hợp: adj(A) = C^T. Do đó, ∇det(A) = C = (adj(A))^T = det(A) * (A^(-1))^T khi A khả nghịch (đây chính là công thức Jacobi).

<br>

<a id="node-zkgdo8d"></a>

##### Đạo hàm của định thức

<p align="center"><kbd><img src="assets/wvc8c1ku1k.png" width="80%"></kbd></p>

> [!NOTE]
> det (λ𝐈 + M)
>
>
>
> Thế thì xét det(λ𝐈 - M)
>
>
>
> Đại khái là ta có công thức sau đây (cái này chấp nhận thôi):
>
>
>
> Hiểu thế này, gọi μ1, μ2,...μn là eigenvalues của M. Thì λ + μ1, λ + μ2, ...là eigenvalues của λ𝐈 + M.
>
>
>
> (Chứng minh nhanh: gọi x là eigenvector của M ứng với eigenvalue μ: Ta có Mx = μx. Cộng hai vế cho λx: λx + Mx = λx + μx ⇔ λ𝐈x + Mx = (λ + μ)x ⇔ (λ𝐈 + M)x = (λ + μ)x. Cái này giúp kết luận: λ + μ là eigenvalue của λ𝐈 + M, với cùng eigenvector x)
>
>
>
> Và det(A) ta đã biết bằng tích cách eigenvalues của A, nên:
>
>
>
> det(λ𝐈 + M) = (λ + μ1)(λ + μ2)...(λ + μn) = Πi=1:n (λ + μi)
>
>
>
> Expand cái này ra ta sẽ có tổng của những term mà mỗi term là tích của n thừa số thuộc một trong hai loại: Hoặc là λ hoặc là μi.
>
>
>
> Từ đó gom lại các term này theo bậc của λ ta sẽ dễ thấy như sau:
>
>
>
> λ^n sẽ chỉ có một term, đó là tích của n thừa số mà mỗi cái đều là λ
>
>
>
> λ^n-1 sẽ là những term mà gồm tích của n-1 λ và một cái là (μi). Có n μi do đó có n term như vậy:
>
>
>
> λ^n-1(μ1) + λ^n-1(μ2) + ...λ^n-1(μn)
>
>
>
> = λ^n-1(Σi μi). Và Σi μi chính là tr(M) Vậy ta có hạng tử thứ 2 là: tr(M) λ^n-1
>
>
>
> λ^n-2 sẽ là những term bởi tích của (n-2) λ và 2 cái (μi), (μj). Vậy hạng tử thứ 3 là: λ^n-2 \* Σi&lt;j (μiμj)
>
>
>
> ....
>
>
>
> λ^0 sẽ là những term chỉ gồm n μi, và dễ thấy cũng chỉ có 1 term như vậy: do đó nó tạo thành hạng tử cuối: Πi μi, đây chính là det(M)
>
>
>
> Từ đó giúp ta hiểu công thức này:
>
>
>
> det(λ𝐈 + M) = λ^n + tr(M) λ^n-1 + (μ1μ2 + μ1μ3 +...) λ^n-2 + ... + det(M)
>
>
>
> Đầu tiên tìm hiểu det(I + dA), áp dụng công thức trên cho λ = 1, M là dA ta có:
>
>
>
> det(I + dA) = 1^n + tr(dA) 1^n-1 + ...+ det(dA)
>
>
>
> Thì ta lập luận như sau: nếu dA là matrix các thay đổi vô cùng nhỏ của A, tức là các component rất nhỏ. Thì eigenvalues μi của nó cũng rất nhỏ. Ta sẽ dễ dàng thấy rằng các coefficient gắn với các term λ^n-2, λ^n-3.. sẽ là tổng của những hạng tử bậc 2 trở lên của μi (ví dụ λ^n-2 có hệ số gắn với nó là (μ1μ2 + μ1μ3 +...) là tổng các bậc 2 của những số vô cùng nhỏ μi)
>
>
>
> Do đó ta có thể bỏ nó đi khi xây dựng công thức tính đạo hàm
>
>
>
> Do đó det(I + dA) = 1^n + tr(dA) = **1 + tr(dA)**
>
>
>
> ---
>
>
>
> Tới đây ta có thể bắt đầu tính đạo hàm của f(A) = det(A)
>
>
>
> f(A + dA) = det(A + dA) = det(A + AA⁻¹dA) = det\[A(I + A⁻¹dA)\]
>
>
>
> Dùng công thức det(AB) =det(A)det(B)
>
>
>
> ⇨ ...= det(A)det(I + A⁻¹dA)
>
>
>
> = det(A)(1 + tr(A⁻¹dA) | dùng công thức trên det(I + A⁻¹dA) = 1 + tr(A⁻¹dA)
>
>
>
> ⇨ df = f(A + dA) - f(A)
>
>
>
> = det(A)\[1 + tr(A⁻¹dA)\] - det(A)
>
>
>
> = det(A) + det(A)tr(A⁻¹dA) - det(A)
>
>
>
> = det(A)tr(A⁻¹dA) (1)
>
>
>
> Dùng A . B = tr(AᵀB) ⇨ tr(A⁻¹dA) = tr\[((A⁻¹)ᵀ)ᵀdA\]
>
>
>
> = (A⁻¹)ᵀ . dA
>
>
>
> ⇨ (1) = det(A) (A⁻¹)ᵀ dA
>
>
>
> Vậy df = det(A) (A⁻¹)ᵀ . dA
>
>
>
> Cái này có dạng là **inner product** của vector dA (dĩ nhiên vector theo nghĩa mở rộng, ở đây là matrix) với một vector khác là det(A) (A⁻¹)ᵀ
>
>
>
> Do đó theo bài trước ta đã học, gradient ∇f chính là vector này:
>
>
>
> Vậy gradient của det(A) là **∇f = det(A) (A⁻¹)ᵀ**

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, giải thích trực quan và chặt chẽ nguồn gốc khai triển của định thức qua trị riêng cũng như dẫn xuất chi tiết đạo hàm Jacobi của hàm định thức.
>
> **🟡 Minor issues**
>
> **1.** *"Ta sẽ dễ dàng thấy rằng các coefficient gắn với các term λ^n-1, λ^n-2.. sẽ là tổng của những hạng tử bậc 2 trở lên của μi"*
>
> Nhầm lẫn nhỏ về chỉ số: hệ số đi với λ^(n-1) là tr(M) (bậc 1 theo μ_i), chỉ từ các số hạng gắn với λ^(n-2), λ^(n-3),... trở đi mới là tổng các tích bậc 2 trở lên của μ_i.
>
> **2.** *"det(A + dA) = det(A + AA⁻¹dA)"*
>
> Bước biến đổi này ngầm giả định ma trận A khả nghịch để A⁻¹ tồn tại. Với A suy biến (singular), công thức vi phân tổng quát sử dụng ma trận phụ hợp adjugate: d(det(A)) = tr(adj(A) dA).
>
>
> **✓ Strengths**
> - Hiểu rất rõ và tự chứng minh được mối liên hệ giữa trị riêng của (λI + M) và khai triển đa thức đặc trưng.
> - Bản chất của phép vi phân ma trận df = tr(...) và liên hệ chính xác với tích vô hướng Frobenius để suy ra gradient.
>
> **💡 Deeper notes**
> - Việc dùng ma trận nghịch đảo A⁻¹ là cách tiếp cận phổ biến cho A khả nghịch, tuy nhiên gradient của det(A) luôn tồn tại với mọi ma trận A (kể cả khi không khả nghịch) và bằng chính ma trận cofactor: ∇det(A) = cof(A) = det(A)(A⁻¹)ᵀ.
> - Chứng minh bằng trị riêng thực chất đòi hỏi xét trên trường số phức ℂ (để đa thức đặc trưng luôn có đủ n nghiệm tính cả bội số đại số), dù vậy trực giác mà bạn đưa ra hoàn toàn đúng bản chất.

<br>

<a id="node-k3i9hxw"></a>

###### Đạo hàm det(x𝐈-A)

<p align="center"><kbd><img src="assets/l3wo0vjp56h.png" width="80%"></kbd></p>

> [!NOTE]
> Và ta sẽ ứng dụng kết quả này để tính derivative của f(x) = det(x𝐈 - A), gọi là characteristic polynomial của A
>
>
>
> Đầu tiên để cho dễ mình sẽ dùng kí hiệu giống như note trước, là det(λ𝐈 - A), và μi là eigenvalues của A.
>
>
>
> Yêu cầu là tính derivative của f(λ) = det(λ𝐈 - A), Chú ý là đây là hàm theo λ.
>
>
>
> Thế thì đầu tiên là tính theo freshman calculus (ý là tính theo cách cơ bản):
>
>
>
> Thế thì như đã nói vừa rồi, det(λ𝐈 - A) = Πi (λ - μi)
>
>
>
> Đặt zi(λ) = λ - μi ⇨ f(z1,z2,...zn) = Πi zi.
>
>
>
> zi = λ - μi cũng suy ra dzi = dλ
>
>
>
> total differentiation:
>
>
>
> df = ∂f/∂z1 dz1 + ...∂f/∂zn dzn
>
>
>
> = ∂f/∂z1 dλ + ...∂f/∂zn dλ = (∂f/∂z1 + ...∂f/∂zn)dλ
>
>
>
> = (z2z3..zn + z1z3..zn + ... \_ z1z2...zn-1) dλ
>
>
>
> = Σi=1:n ( Πj≠i zj ) dλ
>
>
>
> = Σi=1:n \[ Πj≠i (λ - μj) \] dλ
>
>
>
> ⇨ df/dλ = Σi=1:n \[ Πj≠i (λ - μj) \] Đây là kết quả ở đầu tiên trong slide
>
>
>
> trong cái tổng, mỗi hạng tử Πj≠i (λ - μj) có thể viết thành:
>
>
>
> \[Πj (λ - μj)\] / (λ - μi) (tức là, ví dụ a1a3a4 = a1a2a3a4/a2)
>
>
>
> Để rồi ta có df/dλ = Σi=1:n {\[Πj (λ - μj)\] / (λ - μi)}
>
>
>
> và Πj (λ - μj) đều giống nhau ở mọi hạng tử (không phụ thuộc i) nên đưa ra:
>
>
>
> = Πj (λ - μj) { Σi=1:n 1 / (λ - μi) }
>
>
>
> = Πj (λ - μj) { Σi=1:n (λ - μi)^-1 }
>
>
>
> Đây chính là kết quả trong slide. Thay lại dùng x thay cho λ, và λ𝐈 thay cho μi sẽ thấy:
>
>
>
> df/dx = Πj (x - λj) { Σi=1:n (x - λ𝐈)^-1 }
>
> Thế thì ta có thể áp dụng công thức gradient của det(A) để tính derivative của f(x) = det(x𝐈 - A) như sau.
>
>
>
> Đầu tiên coi U = x𝐈 - A.
>
>
>
> ta có f(U) = det(U). và ta đã biết gradient của nó: ∇f(U) = det(U)(U⁻¹)ᵀ
>
>
>
> Viết df(U) ở dạng inner product của f'(U) = ∇f(U)ᵀ với dU
>
>
>
> ⇨ df(U) = det(U) U⁻¹ . dU
>
>
>
> Rồi tới đây ta nhóm U⁻¹ . dU , vì det(U) là scalar:
>
>
>
> df(U) = det(U) (U⁻¹ . dU)
>
> = det(U) \[((U⁻¹)ᵀ)ᵀ . dU\]
>
>
>
> = det(U) tr((U⁻¹)ᵀdU) | Dùng công thức: A . B = tr(AᵀB)
>
>
>
> Vậy ta có df(U) = det(U) tr((U⁻¹)ᵀdU).
>
>
>
> Tiếp từ U = x𝐈 - A, ta có dU(x) = \[(x+dx)I - A\] - (x𝐈 - A) = dx𝐈 = dx
>
>
>
> Vậy dU = dx
>
>
>
> Thay lại U = x𝐈 - A và dU = dx
>
>
>
> \*\*df(U) = d(det(x𝐈 - A)) = det(x𝐈 - A) tr\[((x𝐈 - A)⁻¹)ᵀd(x𝐈 - A)\]
>
>
>
> = det(x𝐈 - A) tr\[((x𝐈 - A)⁻¹)ᵀdx\]\*\*
>
>
>
> Tiếp, xét tr\[((x𝐈 - A)⁻¹)ᵀdx\], nó là tr(matrix nhân dx) thì vì dx là scalarnên tr(Mdx) = tr(M) dx. Chứng minh rất dễ, tr(M α) là tổng entries đường chéo của M α thì cũng bằng tổng entries trên đường chéo của M lại trước rồi nhân α sau, chính là tr(M) \* α
>
>
>
>
>
> Do đó tr\[((x𝐈 - A)⁻¹)ᵀdx\] = tr\[((x𝐈 - A)⁻¹)ᵀ\]dx
>
>
>
> Vậy ta có d(det(x𝐈 - A)) = det(x𝐈 - A)tr\[((x𝐈 - A)⁻¹)ᵀ\]dx
>
>
>
> kết quả này cho thấy derivative của det(x𝐈 - A) wrt x là
>
>
>
> det(x𝐈 - A)tr\[((x𝐈 - A)⁻¹)ᵀ\]
>
>
>
> Và với det(x𝐈 - A) = Πi (x - λ𝐈) và
>
>
>
> tr\[((x𝐈 - A)⁻¹)ᵀ\] thì cũng là tr\[(x𝐈 - A)⁻¹)\] (vì tr(A) = tr(Aᵀ))
>
>
>
> =tổng đường chéo cũng là = tổng eigenvalues của (x𝐈 - A)⁻¹.
>
>
>
> Mà eigenvalues của (x𝐈 - A)⁻¹ có thể chứng minh chính là nghịch đảo eigenvalues của x𝐈 - A
>
>
>
> Vậy tr\[(x𝐈 - A)⁻¹)\] = Σj (x - λj)^-1
>
>
>
> Kết quả này cho thấy solution của hai cách là 1:
>
>
>
> det(x𝐈 - A)tr\[((x𝐈 - A)⁻¹)ᵀ\] = Πi (x - λ𝐈) Σj (x - λj)^-1

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **92/100** · ✓ Move on
>
> Ghi chú rất tốt, trình bày mạch lạc cả 2 cách: đạo hàm giải tích cổ điển (freshman calculus) và vi phân ma trận. Lập luận chặt chẽ và kết nối chính xác hai kết quả với nhau.
>
> **🟡 Minor issues**
>
> **1.** *"dU(x) = [(x+dx)I - A] - (xI - A) = dxI = dx 

 Vậy dU = dx"*
>
> Có sự nhầm lẫn về kiểu dữ liệu (type mismatch): $dx I$ là một ma trận đường chéo $n \times n$ ($dx \cdot I_n$), không thể đồng nhất trực tiếp bằng vô hướng $dx$. Dù sau đó bạn vẫn đưa $dx$ ra ngoài trace chính xác, viết $dU = dx I$ sẽ chuẩn xác và chặt chẽ hơn.
>
> **2.** *"Viết df(U) ở dạng inner product của f'(U) = ∇f(U)T với dU ⇨ df(U) = det(U) Uinv . dU"*
>
> Theo quy ước chuẩn của vi phân ma trận, vi phân toàn phần được định nghĩa trực tiếp qua Frobenius inner product với gradient: $df = \langle \nabla f(U), dU \rangle = \text{tr}(\nabla f(U)^T dU) = \det(U)\text{tr}(U^{-1} dU)$. Việc bạn định nghĩa qua $f'(U) = \nabla f(U)^T$ làm phát sinh thêm một lần chuyển vị không cần thiết (dù sau đó triệt tiêu nhờ tính chất $\text{tr}(M^T) = \text{tr}(M)$).
>
>
> **✓ Strengths**
> - Chứng minh cách 1 bằng vi phân toàn phần và quy tắc tích rất trực quan, biến đổi chính xác ra dạng tổng nghịch đảo.
> - Nắm vững tính chất trace bằng tổng các eigenvalues và mối liên hệ giữa eigenvalue của ma trận nghịch đảo với ma trận ban đầu.
> - Hiểu bản chất tính chất tuyến tính của trace khi đưa vi phân vô hướng $dx$ ra ngoài dấu trace.
>
> **💡 Deeper notes**
> - Công thức $\text{tr}((xI - A)^{-1})$ yêu cầu điều kiện $x$ không phải là eigenvalue của $A$ ($x \notin \sigma(A)$) để nghịch đảo tồn tại; khi $x = \lambda_i$, biểu thức này gặp điểm kỳ dị, nhưng đẳng thức đa thức ban đầu vẫn đúng với mọi $x$ nhờ tính liên tục hoặc thông qua ma trận phụ hợp (Jacobi's formula: $d(\det(M)) = \text{tr}(\text{adj}(M) dM)$).

<br>

<a id="node-l0pnip6"></a>

###### Vi phân hàm log(det(A))

<p align="center"><kbd><img src="assets/ymptljf17s.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp tính thử df = d{log[det(A)]}
>
>
>
> Đặt g = det(A) ta đã biết dg = det(A) (A⁻¹)ᵀ . dA
>
>
>
> với g = det(A) ⇨ f = log(g) ⇨ df = (1/g) dg
>
>
>
> = (1/g) det(A) (A⁻¹)ᵀ . dA
>
>
>
> = 1/det(A) det(A) (A⁻¹)ᵀ . dA = A⁻¹ . dA
>
>
>
> Vậy df = (A⁻¹)ᵀ . dA
>
>
>
> ⇨ ∇f = (A⁻¹)ᵀ
>
>
>
> Trong note ghi sai, gs ghi là tr(A⁻¹)dA là SAI
> đúng phải là tr(A⁻¹dA) từ đó =tr((A⁻¹)ᵀᵀdA)
>
>
>
> = (A⁻¹)ᵀ dA (A . B = tr(AᵀB))
>
>
>
> ⇨ ∇f = (A⁻¹)ᵀ 
>
>
>
> (chú ý ko cần transpose lần nữa như case của
> column vector Rn -> R)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, hiểu sâu bản chất vi phân ma trận và phát hiện chính xác lỗi đánh máy trong slide của giáo sư.
>
> **🟡 Minor issues**
>
> **1.** *"= 1/det(A) det(A) AinvT . dA = Ainv . dA"*
>
> Có một lỗi typo nhỏ làm rơi mất ký hiệu chuyển vị T ở biểu thức trung gian (viết thành Ainv . dA), nhưng ngay dòng dưới đã ghi lại chính xác là AinvT . dA nên không ảnh hưởng đến kết quả cuối cùng.
>
>
> **✓ Strengths**
> - Áp dụng quy tắc chuỗi (chain rule) cho vi phân vô hướng f = log(g) và vi phân ma trận dg = det(A) tr(A^-1 dA) rất chuẩn xác.
> - Rất nhạy bén và hiểu sâu khi nhận diện đúng lỗi typo trên slide giáo sư: slide viết tr(A^-1)dA nhưng bản chất phải là trace của tích tr(A^-1 dA).
> - Xác định gradient ma trận qua tích vô hướng Frobenius <A^-T, dA> = tr(A^-1 dA) một cách chặt chẽ.
>
> **💡 Deeper notes**
> - Công thức yêu cầu điều kiện ma trận A khả nghịch (det(A) != 0) và đối với hàm log thực thông thường thì cần det(A) > 0 (hoặc xét log(|det(A)|)).

<br>

