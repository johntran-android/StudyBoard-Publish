# 2.3.0 Gaussian Distribution

📊 **Progress:** `16` Notes | `27` Screenshots | `15` AI Reviews

---
<a id="node-dp9al6u"></a>

<br>

<a id="node-arii2cl"></a>

## Phân phối Gaussian

<p align="center"><kbd><img src="assets/ska6rlgua1s.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này ta sẽ nói về Gaussian (hay Normal distribution), là distribution khá quan quen thuộc sau khi học xong Stat110 và Casella. Công thức của case đơn biến hay đa biến thì mình cũng đã đều bíết rồi. Đặc biệt trong chap 1 mình đã derive lại công thức Normal đa biến để hiểu công thức 2.43 rồi.
>
>
>
> Thế thì gs nói đây là distribution hay dùng, và nó xuất hiện trong nhiều bối cảnh. Ví dụ như trong chap 1 mình đã thấy nó chính là **distribution có entropy lớn nhất**.

> [!TIP]
> **🤖 AI Feedback** — ⚠️ Score: **80/100**
>
> Ghi chú đã nắm bắt chính xác các thuộc tính chính của phân phối Gaussian, bao gồm tên gọi khác, ứng dụng rộng rãi và đặc biệt là đặc tính cực đại hóa entropy. Để tăng cường độ sâu, bạn có thể bổ sung các định nghĩa về tham số (như μ, σ², Σ) và lưu ý về việc phân phối này áp dụng cho "biến liên tục" từ văn bản.

**🔗 See also:** [Tối ưu Entropy và Hàm Lagrangian](./16_information_theory.md#node-hhyh07u) · [Phân phối chuẩn entropy tối đa](./16_information_theory.md#node-71bnwai) · [Biến đổi Gaussian độc lập](#node-1vavixz) · [3.1.5 Multiple outputs](./315_multiple_outputs.md#node-5d9hd8j)

<br>

<a id="node-cp5ac1u"></a>

### Định lý giới hạn trung tâm

<p align="center"><kbd><img src="assets/rs45bp77mq8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hogi7vb33l.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/nudldnc307.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là gs Bishop nói một trường hợp nữa mà ta thấy sự xuất hiện của
>
> Normal đó là, Central Limit Theorem, còn nhớ trong Stat110 và Casella,
>
> theorem này nói rằng, xét một random sample size n X1,X2,...Xn \~ distribution
>
> có mean μ và variance σ² thì sample mean  Xbar sẽ converge in distribution
>
> về một normal(μ, σ²/n).
>
>
>
> Và hình ảnh minh họa cho thấy, X1, ..Xn là uniform, và người ta plot giá trị của
>
> sample mean Xbar.
>
>
>
> Hiểu như sau. Ban đầu ta sẽ chỉ in Xbar của sample size N=1: tức là lấy
>
> random sample size N = 1 nhiều lần, mỗi lần tính ra Xbar, và plot ra, khi đó có
>
> thể thấy distribution của Xbar cũng chỉ là uniform.
>
>
>
> Nhưng ta làm vậy với N lớn dần thì sẽ thấy distribution của Xbar dần dần có
>
> dạng của normal.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú của bạn giải thích rất chính xác và chi tiết về Định lý Giới hạn Trung tâm, bao gồm cả công thức cụ thể cho phân phối của trung bình mẫu. Để toàn diện hơn, bạn có thể bổ sung thêm về sự hội tụ của phân phối nhị thức đã được đề cập.

**🔗 See also:** [Histogram Density Estimation](./25_non_parametric_model.md#node-qmfgqko)

<br>

<a id="node-ee1i4nk"></a>

#### Dạng hình học phân phối Gaussian

<p align="center"><kbd><img src="assets/2m5fz68d47f.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zeqvppzqy8j.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là gs nói rằng phần này ta sẽ cần nhiều kiến thức về matrixmà ông có nói đến trong Appendix C. Tuy nhiên ông khuyến khích người học nên trở nên thành thạo trong việc biến đổi liên quan đến phân phối Normal với các kĩ thuật sẽ nói đến ở đây. Vì như vậy sẽ giúp cho ta có thể hiểu được các mô hình phức tạp hơn giới thiệu trong các chương sau.
>
>
>
> Đầu tiên ta sẽ xem xét khía cạnh hình học của phân phối Gaussian. 
>
>
>
> Thế thì, ông nói, đại khái là, phân phối Gaussian sẽ phụ thuộc vào x thông qua quadratic form (𝐱 - **μ**)ᵀ Σ⁻¹ (𝐱 - **μ**), đặt là Δ². Ý ông nói vậy có nghĩa là, ta thấy trong pdf của multivariate Normal, thì có thể thấy nó phụ thuộc với x thông qua cái cụm này, chỉ vậy thôi. Và cụm này, có dạng của zᵀAz, như đã biết trong MIT 1806, gọi là quadratic form (cũng chính là cái mà nếu ta có thể chỉ ra zᵀAz &gt; 0 với mọi z thì ta sẽ kết luận A là positive definite matrix đó).
>
>
>
> Rồi, ở đây mình được biết một ý mới, rằng Δ được gọi là Mahalanobis distance của **μ** và 𝐱. Và khi Σ là identity matrix I, thì Δ trở thành (𝐱 - **μ**)ᵀ(𝐱 - **μ**), dĩ nhiên đây chính là ||𝐱 - **μ**||², là L2 hay Eucledean distance của 𝐱 và **μ**.
>
>
>
> Cuối cùng, đương nhiên ta cũng hiểu ý cuối, là nếu cái cụm này mà là constant, thì dĩ nhiên hàm pdf Gaussian cũng là constant theo 𝐱.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú của bạn rất chi tiết, chính xác và thể hiện sự hiểu sâu sắc về nội dung, bao gồm cả khả năng liên hệ kiến thức với các môn học khác. Tiếp tục duy trì cách phân tích và ghi chú này để củng cố kiến thức một cách vững chắc.

<br>

<a id="node-ubkik90"></a>

##### Tính đối xứng của ma trận Σ

<p align="center"><kbd><img src="assets/cdbd2fg9wmk.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì chỗ này gs nói matrix Σ có thể coi như là symmetric (đối xứng), mà không mất tính tổng quát vì mọi thành phần bất đối xứng đều bị biến mất bởi exponent. Là sao ta?
>
>
>
> Sau khi thảo luận với gemini, mình hiểu thế này: Một matrix A được gọi là đối xứng khi Aᵀ = A (A tranpose, chuyển vị, bằng chính nó). Còn nếu Aᵀ = -A thì nó gọi là anti-symmetric matrix.
>
>
>
> Thế thì giả sử ta xét một matrix A bình thường (bất kì, bằng cách biến đổi chút ta sẽ có: A = (1/2)A + (1/2)A
>
>
>
> = (1/2)A + (1/2)Aᵀ + (1/2)A - (1/2)Aᵀ
>
>
>
> = (1/2)(A + Aᵀ) + (1/2)(A - Aᵀ)
>
>
>
> Khi đó ta có (1/2)(A + Aᵀ) là matrix đối xứng, vì (1/2)(A + Aᵀ)ᵀ = (1/2)(Aᵀ + A) = (1/2)(A + Aᵀ)
>
>
>
> Còn (1/2)(A - Aᵀ) là matrix anti-symmetric vì (1/2)(A - Aᵀ)ᵀ = (1/2)(Aᵀ - A) = -(1/2)(A - Aᵀ)
>
>
>
> Như vậy có thể hiểu mọi matrix Σ bất kì đều có thể thể hiện bởi tổng của một matrix symmetric và một matrix antisymmetric.
>
>
>
> Thế thì như vậy, nếu ta xét Σ trong Gaussian là matrix bất kì, thì cái cụm quadratic form sẽ trở thành (𝐱 - **μ**)ᵀ Σ⁻¹ (𝐱 - **μ**)
>
>
>
> = (𝐱 - **μ**)ᵀ \[Σ⁻¹_sym + Σ⁻¹_asym\] (𝐱 - **μ**)
>
>
>
> = (𝐱 - **μ**)ᵀ Σ⁻¹_sym (𝐱 - **μ**) + (𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**)
>
>
>
> Xét hạng tử thứ hai: 
>
>
>
> (𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**)
>
>
>
> như đã biết, quadratic form thì là một scalar, nên:
>
>
>
> (𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**) = \[(𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**)\]ᵀ
>
>
>
> ⇔ (𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**) = (𝐱 - **μ**)ᵀ (Σ⁻¹_asym)ᵀ (𝐱 - **μ**)
>
>
>
> ⇔ (𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**) = (𝐱 - **μ**)ᵀ (-Σ⁻¹_asym) (𝐱 - **μ**)
>
>
>
> ⇔ (𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**) = -(𝐱 - **μ**)ᵀ (Σ⁻¹_asym) (𝐱 - **μ**)
>
>
>
> Như vậy,  nếu coi vế trái là c thì ta có c = -c, suy ra c = 0.
>
>
>
> Vậy (𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**) = 0
>
>
>
> ⇨ (𝐱 - **μ**)ᵀ Σ⁻¹_sym (𝐱 - **μ**) + (𝐱 - **μ**)ᵀ Σ⁻¹_asym (𝐱 - **μ**)
>
>
>
> = (𝐱 - **μ**)ᵀ Σ⁻¹_sym (𝐱 - **μ**) 
>
>
>
> Do đó, dù có xét Σ có không đối xứng thì quadratic form (𝐱 - **μ**)ᵀ Σ⁻¹ (𝐱 - **μ**) cũng chỉ còn lại phần đối xứng của nó. Thành ra gs mới nói là ta coi Σ là matrix đối xứng mà không sợ mất tính tổng quát (loss of generality)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Phân tích của bạn rất sâu sắc và chính xác, giải thích rõ ràng lý do tại sao thành phần phản đối xứng biến mất khỏi biểu thức bậc hai. Việc phân tích từng bước này thể hiện sự hiểu biết vững chắc về đại số tuyến tính.

<br>

<a id="node-ulmctg7"></a>

###### Phân rã Eigen hiệp phương sai

<p align="center"><kbd><img src="assets/efqvqjj52w5.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo, nhờ MIT 1806 cũng như kiến thức về đại số tuyến tính mà gs Bishop cung cấp ở Appendix C, ko có gì khó hiểu ở đoạn này. Là như vầy:
>
>
>
> Như đã biết, nếu gọi ui và λi, i = 1,....D là các eigenvector và eigenvalue tương ứng của Σ, thì vì định nghĩa của eigenvector/value, ta có Σui = λiui.
>
>
>
> Nhưng với Σ, là matrix số thực, và đối xứng thì ta cũng biết rằng nó có tính chất đặc biệt hơn đó là mọi eigenvalue sẽ đều là số thực, và tồn tại, có thể chọn một bộ eigenvector orthogonal, và bộ vector này đương nhiên là độc lập nhau, nhưng hơn thế nữa, nó còn đủ số lượng (theo cách nói của gs Strang trong MIT 1806: matrix đối xứng A shape nxn, luôn có đủ n eigenvector độc lập, và điều này có nghĩa là chúng sẽ đủ sức tạo một basis của Rⁿ) để tạo một basis của R^D, hay, nói cách khác: span được toàn bộ R^D.
>
> Và cũng nên tự hiểu là chúng được normalize để có unit norm (length = 1), để vừa orthogonal + unit norm = orthonormal. Tóm lại, với Σ, các eigenvector ui của chúng có tính chất: 
>
>
>
> Unit norm ⇨ ||ui|| = 1, cũng là ||ui||² = 1 ⇔ uiᵀui = 1. 
>
>
>
> Orthogonal: uiᵀuj = 0, i ≠ j → đây chính là 2.46
>
>
>
> Và như trong MIT18.06 đã học, ta gom ui thành các cột của matrix U thì U là một orthogonal matrix: UᵀU = UUᵀ = I ⇨ Uᵀ = U⁻¹.
>
>
>
> Thế thì công thức 2.48 là sao?
>
>
>
> Là vầy: Bản chất là từ các equation Σu1 = λ1u1, Σu2 = λ2u2, ...ΣuD = λDuD.
>
>
>
> Thì nếu ta gom các u1,...uD thành các cột của matrix U nói trên, và λ1u1, λ2u2,...là các cột của matrix V khi đó, dựa vào góc nhìn thứ 3 khi nhân hai matrix AB: cột j của AB = linear combination các cột của A bởi bộ hệ số là cột j của B, thì ta sẽ thấy ngay rằng hệ các phương trình trên có thể được thể hiện compact bởi: AU = V.
>
>
>
> Và tương tự, cũng dựa vào góc nhìn đó, ta sẽ thấy cột j của V, tức λj uj chính là linear combination các cột u1,..uD với bộ hệ số là 0,0...1,..0 với số 1 nằm ở vị trí thứ j, Để từ đó có thể thấy V = U diag(λ1,..λD), đặt diag(λ1,..λD) = Λ, ta có:
>
>
>
> Vậy AU = UΛ, đây chính là identity của phân rã eigenvalue (eigenvalue decomposition).
>
>
>
> Rồi, vì Uᵀ = U⁻¹, nên nhân bên phải hai vế cho Uᵀ, ta có A = U Λ Uᵀ.
>
>
>
> Tiếp, với phân tích cái vế phải,  theo góc nhìn là nhân hai matrix: (U Λ) với Uᵀ theo góc nhìn thứ 4: tổng các rank 1 matrix. Theo góc nhìn đó, giả sử ta có AB, thì có thể xem nó là tổng các rank 1 matrix tạo bởi \[cột j của A\] outer product \[hàng j của B\], j = 1,2,...
>
>
>
> Nên A = Σj=1:D \[cột j của UΛ\] outer product \[hàng j của Uᵀ\]
>
>
>
> Mà cột j của UΛ chính là λjuj. và hàng j của Uᵀ thì cũng là \[cột j của U lật ngang lại\], tức \[cột j của U\]ᵀ, hay ujᵀ. Vậy A = Σj=1:D λjujujᵀ, → 2.48.
>
>
>
> (giải thích dài dòng để hiểu bản chất)
>
>
>
> Hoàn toàn tương tự với Σ⁻¹: Ta dùng kiến thức, nếu u,λ là eigenvector/value của A thì u, 1/λ chính là eigenvector/value của A⁻¹. Nên eigenvalue và vector của Σ⁻¹ chính là u1, 1/λi, i=1,2...D.
>
>
>
> Nên áp dụng lập luận tương tự, ta sẽ thấy A⁻¹ = Σj=1:D ujujᵀ/λj

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Bạn đã giải thích các khái niệm và công thức một cách cực kỳ chi tiết và chính xác, thể hiện sự hiểu biết sâu sắc về đại số tuyến tính. Cách bạn liên hệ các kiến thức từ MIT 18.06 và các tính chất của ma trận đối xứng để chứng minh các công thức 2.48 và 2.49 là rất ấn tượng và có giá trị.

<br>

<a id="node-c9cpfzj"></a>

###### Chuyển tọa độ eigenvector

<p align="center"><kbd><img src="assets/tpqdysnql6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/bjy16glpx1.png" width="80%"></kbd></p>

> [!NOTE]
> Thay Σ⁻¹ = Σj=1:D ujujᵀ/λj vào (𝐱 - **μ**)ᵀ Σ⁻¹ (𝐱 - **μ**) ta có:
>
>
>
> = (𝐱 - **μ**)ᵀ \[Σj ujujᵀ/λj\] (𝐱 - **μ**)
>
>
>
> = Σj \[(𝐱 - **μ**)ᵀujujᵀ(𝐱 - **μ**)/λj\] | đưa (𝐱 - **μ**)ᵀ và (𝐱 - **μ**) vào trong tổng.
>
>
>
> Đặt yj = (𝐱 - **μ**)ᵀuj (cũng là ujᵀ(𝐱 - **μ**) vì cái này là scalar), ta có:
>
>
>
> = Σj (yjᵀyj/λj) = Σj (yj²/λj) → 2.51
>
>
>
> Thế thì với y1 = (𝐱 - **μ**)ᵀu1, y2 = (𝐱 - **μ**)ᵀu2,...mình có thể thấy: y1 = dot product của 𝐱 - **μ** với u1, y2 là dot product của 𝐱 - **μ** với y2,...thì với việc gs Bishop đặt U là matrix có các hàng là u1, u2,...để rồi Uᵀ là matrix có các cột là u1, u2... Thì ta sẽ thấy 𝐲 = (y1, y2...)ᵀ chính là U(𝐱-**μ**).  
>
> ⇨ 𝐲 = U(𝐱 - **μ**)
>
>
>
> ---
>
>
>
> Rồi, chỗ này dùng kiến thức về **change of basis** đã học trong MIT 1806: Ôn lại nhanh:
>
>
>
> Trong MIT 1806, bài linear transformation, đại khái là mình đã học rằng, một phép biến đổi T(.) được gọi là linear transformation là khi nó thỏa mãn: T(c𝐮 + d𝐯) = cT(𝐮) + dT(𝐯) (c, d là scalar, u, v là vector) Và vì A(c𝐮 + d𝐯) = cA𝐮 + dA𝐯, nên quả thật việc nhân A với vector 𝐱, chính là một phép biến đổi tuyến tính. T(𝐱) = A𝐱.
>
>
>
> Thế thì sau đó gs mới nói về việc, giả sử có một linear transformation T(.), thì làm sao xác định matrix A đại diện cho nó? Tức là, giả sử ta có vector 𝐱 trong input basis v's, và kết quả T(𝐱) trong output basis u's, thì làm sao tìm A khiến T(𝐱) = A𝐱. Câu trả lời là lập luận như sau:
>
>
>
> Gọi **v1**,...**vn** là các basis của input space. Thì tọa độ của 𝐱 đang được thể hiện theo (linear combination của) basis này, có nghĩa là, 𝐱 = x1**v1** + x2**v2** + ...xn**vn** = Σi xi**vi** (x1,x2...là các tọa độ của 𝐱)
>
>
>
> Thế thì, T(𝐱), có tọa độ trong output basis T(𝐱)1, T(𝐱)2,...T(𝐱)m:
>
>
>
> T(𝐱) = Σj=1:m T(𝐱)j \* **uj**
>
>
>
> Và T(𝐱) = A𝐱 = Σi=1:n xi 𝐚i
>
>
>
> ⇨ Σi=1:n xi 𝐚i = Σj=1:m T(𝐱)j \* 𝐮j
>
>
>
> vì T(.) là linear transformation, nên T(𝐱) = T(Σi=1:n xi𝐯i) = Σi=1:n xi T(𝐯i).
>
>
>
> ⇔ Σi=1:n xi 𝐚i = Σj=1:m { \[Σi=1:n xi T(𝐯i)\]j 𝐮j }
>
>
>
> Xét \[Σi=1:n xi T(𝐯i)\]j có nghĩa là linear combine các T(𝐯1), T(𝐯2).. với hệ số x1,x2.., được một vector, rồi lấy phần tử thứ j của nó. Thì cái này cũng y như lấy phần tử thứ j của T(𝐯1), T(𝐯2),...rồi linearly combine với hệ số x1,x2...
>
>
>
> ⇨ \[Σi=1:n xi T(𝐯i)\]j = Σi=1:n xi T(𝐯i)j
>
>
>
> ...⇔ Σi=1:n xi 𝐚i = Σj=1:m { \[Σi=1:n xi T(𝐯i)j\] 𝐮j }
>
>
>
> Tiếp, xét cụm \[Σi=1:n xi T(𝐯i)j\] 𝐮j ở bên trong tổng j. ta có thể đưa uj vào trong tổng i, vì nó chỉ là thừa số chung:
>
>
>
> ⇨ \[Σi=1:n xi T(𝐯i)j\] 𝐮j = Σi=1:n \[xi T(𝐯i)j 𝐮j\]
>
>
>
> ...⇔ Σi=1:n xi 𝐚i = Σj=1:m { \[Σi=1:n xi T(𝐯i)j 𝐮j\] }
>
>
>
> Tiếp, ta đang có dạng Tổng j của tổng i, có quyền swap hai dấu tổng:
>
>
>
> ...⇔ Σi=1:n xi 𝐚i = Σi=1:n { Σj=1:m \[xi T(𝐯i)j 𝐮j\] }
>
>
>
> Đến đây xét cái tổng Σj=1:m \[xi T(𝐯i)j 𝐮j\], có quyền đưa xi ra ngoài:
>
>
>
> ⇔ Σi=1:n xi 𝐚i = Σi=1:n xi { Σj=1:m \[ T(𝐯i)j 𝐮j\] }
>
>
>
> Như vậy tới đây có thể suy ra:
>
>
>
> ⇨ 𝐚i = Σj=1:m T(𝐯i) 𝐮j
>
>
>
> Và từ đó ta có quy tắc xây dựng matrix A đại diện cho phép biến đổi tuyến tính T(𝐱) từ 𝐱 trong input space basis 𝐯's sang T(𝐱) trong output space basis 𝐮's:
>
>
>
> Biến đổi các basis 𝐯i's và thể hiện chúng trong tọa độ basis 𝐮's. Khi đó tọa độ của T(𝐯1),..T(𝐯n) chính là là hệ số các cột của A.
>
>
>
> ---
>
>
>
> Từ đó ta xét phép biến đổi identity: Tức T(𝐱) = 𝐱:
>
>
>
> Vì đã nói cột i của A là tọa độ của T(𝐯i) trong basis u's, nên: \
> \
> T(𝐯i) = linear combination các 𝐮1,...𝐮m bởi các hệ số là cột i của A, đặt U là matrix các cột 𝐮1,..𝐮m thì ta có T(𝐯i) = U \[cột i của A\]
>
>
>
> Xét phép biến đổi identity: T(𝐯i) = 𝐯i. Ta có:
>
>
>
> 𝐯i = U\[cột i của A\], i = 1,..n 
>
>
>
> Gom 𝐯1, 𝐯2...𝐯n thành các cột của V, thì 𝐯i = U\[cột i của A\], i = 1,..n chính là V = UA
>
>
>
> Và nhân hai vế cho U⁻¹: U⁻¹V = A, đây chính là công thức của "change of basis" / matrix chuyển cơ sở từ cơ sở v's sang cơ sở u's: A = U⁻¹V.
>
>
>
> Xét một case đặc biệt, khi input basis là standard basis: 𝐯1, 𝐯2,... = 𝐞1, 𝐞2,...Hay cũng là V = I. Ta sẽ có:
>
>
>
> A = U⁻¹ I = U⁻¹. Từ đây giúp kết luận, khi có **x là vector có tọa độ trong standard basis**, thì A𝐱 = U⁻¹ 𝐱, chính là động tác tính ra tọa độ của nó trong basis 𝐮's.
>
>
>
> ---
>
>
>
> Rồi, quay lại công thức y = U(𝐱-**μ**):
>
>
>
> Đầu tiên chú ý là trong phần ôn lại ở trên, mình nói U là vector tạo bởi các **cột** là các basis u's.
>
>
>
> Còn trong bài này, U ở đây được gs Bishop định nghĩa là là **matrix có các các hàng là các orthogonal eigenvector ui**. Như vậy **Uᵀ là orthogonal matrix**, **có các cột là orthogonal eigenvector ui.** Và với orthogonal matrix Q thì Qᵀ = Q⁻¹, nên (Uᵀ)ᵀ = Uᵀinv ⇔ U = (Uᵀ)⁻¹
>
>
>
> ⇨ 𝐲 = U(𝐱-**μ**) = (Uᵀ)⁻¹(𝐱-**μ**)
>
>
>
> Và phần ôn lại ở trên giúp ta hiểu rõ bản chất của cái này chính là:
>
>
>
> **CHUYỂN TỌA ĐỘ CỦA** **x (SAU KHI SHIFT BỞI μ) TỪ CƠ SỞ CHUẨN (BASIS e's) SANG HỆ TỌA ĐỘ CƠ SỞ LÀ CÁC CỘT CỦA Uᵀ, CHÍNH LÀ ui = CÁC EIGENVECᵀOR CỦA Σ!**
>
>
>
> Hơn nữa, với Uᵀ là orthogonal matrix,  (để rồi U = (Uᵀ)⁻¹) thì UᵀU = Uᵀ (Uᵀ)⁻¹ = I, điều này cho thấy U cũng là orthogonal matrix. Và ta biết với orthogonal matrix, thì phép biến đổi bởi nó thực chất là phép xoay trục.
>
>
>
> Như vậy có 2 ý quan trọng cần hiểu rút ra từ phân tích trên:
>
>
>
> i) y = U(𝐱-**μ**) = (Uᵀ)⁻¹(𝐱-**μ**) có bản chất là: **chuyển tọa độ của (x-μ) từ basis e's sang basis tạo bởi các cột của Uᵀ, chính là các vector ui, là eigenvector của Σ**.
>
>
>
> ii) Và Uᵀ là orthogonal matrix thì U cũng vậy, nên đây cũng là **phép xoay hệ trục tọa độ**.
>
>
>
> Gom lại hai ý này, ta sẽ hình dung **bản chất chỉ là tính lại tọa độ của x-μ bằng cách xoay trục tọa độ thẳng góc với các eigenvector của Σ.**

> [!TIP]
> **🤖 AI Feedback** — ⚠️ Score: **75/100**
>
> Bạn đã thể hiện sự hiểu biết sâu sắc về đại số tuyến tính qua việc phân tích chuyển đổi dạng toàn phương và khái niệm thay đổi cơ sở. Tuy nhiên, kết luận về lỗi của công thức (2.52) trong sách là không chính xác do bạn đã bỏ qua định nghĩa tường minh của tác giả Bishop về ma trận U (các hàng của U là u_i^T).

**🔗 See also:** [Section 3.5.3 Effective Number of Parameters](./353_effective_number_of_parameters.md#node-2wanjgv)

<br>

<a id="node-ucnx12w"></a>

###### Đường đồng mức Gaussian

<p align="center"><kbd><img src="assets/74bjy2kdpz.png" width="80%"></kbd></p>

> [!NOTE]
> Nhờ việc phân tích ở note trước, ta có thể hiểu đoạn sau: Đại ý là như trước đây đã nói, pdf của multivariate Gaussian sẽ phụ thuộc **x chỉ thông qua cái cụm quadratic form (x-μ)ᵀ Σ⁻¹ (x-μ), nên dĩ nhiên tập hợp các điểm x trong input space sao cho cụm này bằng constant, thì tương ứng sẽ chính là những điểm có cùng mật độ xác suất pdf.**
>
>
>
> Thế thì xét một tập hợp như vậy: (𝐱-**μ**)ᵀ Σ⁻¹ (𝐱-**μ**) = constant c, thì như vừa nói sẽ tương ứng với một level set (tập các điểm của f(𝐱|**μ**, **Σ**), hay N(𝐱|**μ**, **Σ**)), câu hỏi đặt ra là nó có hình dạng thế nào.
>
>
>
> Thế thì như note trước, (𝐱-**μ**)ᵀ Σ⁻¹ (𝐱-**μ**) = constant c
>
>
>
> ⇔ Σj (yj²/λj) = c
>
>
>
> Ta sẽ xét trong case 2 chiều, tức D=2, 𝐱 là vector (x1,x2)ᵀ, nó sẽ là:
>
>
>
> y1² / λ1 + y2² / λ2 = c
>
>
>
> Còn nhớ cấp hai đã học, phương trình của đường ellips trong mặt phải xOy là x²/a² + y²/b² = 1. (a, b gọi là độ dài bán trục lớn và nhỏ). Thì chia hai vế cho c, (1) ⇔ y1² / cλ1 + y2² / cλ2 = 1. Cho thấy **level set này chính là một hình elipse**.
>
>
>
> y là tọa độ của x-μ trong hệ trục tọa độ eigenvector u1, u2.
>
>
>
> Vậy ọa độ của tâm ellipse, là 0,0 trong hệ trục này, chính là ứng với điểm nào trong hệ tọa độ gốc (basis e's)?
>
>
>
> Dùng công thức chuỷển ngược lại thôi: Nãy ta dùng (Uᵀ)⁻¹ để chuyển từ basis e's về basis eigenvector u's thì ((Uᵀ)⁻¹)⁻¹ = Uᵀ sẽ chuyển ngược lại: đương nhiên Uᵀ**0** (ý là U tranpose nhân vector zero **O**) cũng bằng **0**, Nhưng sau đó ta sẽ phải shift lại: + **μ**: 0 + **μ** = **μ** Vậy, tâm của ellipse chính là tại 𝐱 = **μ** trong hệ tọa độ ban đầu.
>
>
>
> Còn trục của ellipse? Như đã nói, chính là hai vector u1, u2.
>
>
>
> Tóm lại, đường đồng mức của Gaussian (level set, nơi có giá trị hàm pdf bằng nhau) trong case 2D, sẽ chính là một đường elipse có trục trùng với phương của các eigenvector của Σ, và tâm thì nằm tại **μ**
>
>
>
> Khái quát lên n-D, nó là ellipsoid trong không gian n chiều, cũng có tâm tại μ và trục trùng với eigenvector.
>
>
>
> ---
>
>
>
> Trong hình 2.7, gs vẽ level set với của pdf với level ứng với exp(-1/2) (chú ý, tự hiểu là giá trị pdf là \[hằng số gì đó (normalizing constant)\] exp(-1/2), chứ ko phải pdf = exp(-1/2) nhé)
>
>
>
> Ta có exp {-\[y1² / λ1 + y2² / λ2\]} = exp(-1/2)
>
>
>
> (chú ý, đầu giờ chỉ nói đến cái cụm quadratic form nhưng khi bỏ vào exp() của hàm pdf của Normal thì trước cái cụm quadratic form phải có dấu trừ)
>
>
>
> ⇔ -{y1² / λ1 + y2² / λ2} = -1/2
>
>
>
> ⇔ y1² / (λ1/2) + y2² / (λ2/2) = 1
>
>
>
> và ông vẽ cái đường màu đỏ chính là hình ellipse với a = λ1/2, b = λ2/2

<br>

<a id="node-1mvawof"></a>

###### Eigenvalues Ma trận Hiệp phương sai

<p align="center"><kbd><img src="assets/ubfq8ck4isc.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, đại ý là, covariance matrix của phân phối multivarate Normal, tức Σ có một đặc điểm nhằm đảm bảo rằng phân phối này được define đúng (**well defined**). Đó là **mọi eigenvalues của Σ đều dương.**
>
>
>
> **Vì sao**? Ở đây có một ý rất hay mà gs Bishop không nói kĩ: Như trong note trước, ta đã hiểu cái level set (đường đồng mức của hàm 2D Gaussian là một đường ellipse) ứng với exp(-1/2) có tâm tại **μ** và có trục ellipse theo phương của các eigenvector với độ dài bán trục là λ1/2 và λ2/2.
>
>
>
> Thì như vậy ta sẽ nhận thấy một sự thật rằng: λi chính là phản ánh **mức độ phân tán** (**spreading**) **của pdf theo phương eigenvector** 𝐮i, và đó chính là gì: và như vậy, nó phản ánh **variance theo phương u**i.
>
>
>
> HIểu nôm na về mặt hình học là vậy, còn ta sẽ **lập luận lại từ định nghĩa của Covariance matrix**:
>
>
>
> Ở đây tạm quay lại kí hiệu chuẩn toán với việc dùng **X viết hoa** để chỉ random variable vector 𝐗. (**μ**, hay 𝐮 thì cũng là vector như là vector fixed value, không phải random variable)
>
>
>
> Theo định nghĩa, Σ = Cov(𝐗, 𝐗) = E\[(𝐱 - **μ**)(𝐱 - **μ**)ᵀ\]
>
>
>
> (covariance của hai random variable X, Y: Cov(X,Y) = E\[(X-EX)(Y-EY)\])
>
>
>
> Thế thì ta gọi λ và 𝐮 là eigenvalue và eigenvector của Σ, ta có Σ𝐮 = λ𝐮.
>
>
>
> ⇔ 𝐮ᵀΣ𝐮 = 𝐮ᵀλ𝐮 (nhân trái hai vế cho 𝐮ᵀ (𝐮 transpose))
>
>
>
> ⇔ 𝐮ᵀΣ𝐮 = λ𝐮ᵀ𝐮 (λ là scalar, move tự do)
>
> \
> ⇔ 𝐮ᵀΣ𝐮 = λ (vì ta đang luôn làm việc với bộ eigenvector orthogonal và unit norm → 𝐮ᵀ𝐮 = ||𝐮||² = 1)
>
>
>
> ⇔ 𝐮ᵀ E\[(𝐗-**μ**)(𝐗-**μ**)ᵀ\] 𝐮 = λ
>
>
>
> Thế thì E\[...\] là kì vọng là liên quan đến random variable vector 𝐗, nên 𝐮 chỉ là vector fixed value, hay constant, đưa vào kì vọng nhờ tính linearity: E\[cX\] = cE\[X\] 
>
>
>
> ⇔ E\[𝐮ᵀ(𝐗-**μ**)(𝐗-**μ**)ᵀ𝐮\] = λ
>
>
>
> Tới đây, ta đặt Z = (𝐗 - **μ**)ᵀ**u ⇨** E\[ZᵀZ\] = E\[Z²\] = λ 
>
>
>
> Vậy λ = E\[Z²\] Và từ đây suy ra hai thứ:
>
>
>
> Nhưng trước tiên cần hiểu Z **cũng là một random variable** (scalar, ko phải random vector).
>
> Z = (𝐗-μ)ᵀ𝐮, chính là áp hàm g(𝐱) = (x-μ)ᵀu lên random variable vector 𝐗, đương nhiên, theo Stat110, thầy Joe đã luôn nhắc ta khi áp một hàm số lên một random variable (vector) ta luôn được một random variable (vector) mới), do đó ta  có được random variable scalar Z. Sở dĩ phải nói vậy là vì nhờ đó mới bàn tới kì vọng / trung bình của Z: E\[Z²\], chứ nếu Z ko phải random variable, thì điều này vô nghĩa. Và dĩ nhiên Z² cũng lại là một random variable, có giá trị không âm
>
>
>
> i) Như vậy λ là **trung bình / kì vọng của một biến ngẫu nhiên không âm** nên sẽ luôn **không âm**.
>
>
>
> ii) Ý thứ hai quan trọng hơn nhiều: λ = E\[Z²\], mà Z = (𝐗 - **μ**)ᵀ𝐮 có bản chất hình học là gì?
>
>
>
>  → Ta biết trong đại số tuyến tính phép tích vô hướng aᵀb chính là ||a|| ||b|| cos(a,b), và nếu b là unit vector q, thì aᵀq chính là hình chiếu của a lên q, có giá trị là tọa độ của a theo trục q. Như vậy ở đây u là unit vector. Chính là **hình chiếu** của (𝐱-**μ**) lên trục tọa độ là **eigenvector** 𝐮.
>
>
>
> Và thật ra ta đã có cùng kết luận này từ trong note trước, khi ta làm phân tích cái quadratic form (𝐱-**μ**) Σ⁻¹ (𝐱-**μ**) = Σi (yiᵀyi/λi) = Σi yi²/λi với yi = uiᵀ(𝐱-**μ**), cũng là vector 𝐲 = U(𝐱-**μ**). Thì ta đã hiểu ý nghĩa của cái này chính là chuyển tọa độ 𝐱 bằng cách dời hệ trục về gốc tại **μ**, sau đó xoay hệ trục để trùng với các eigenvector ui. Nên y1, y2,...chính là tọa độ của x trong hệ trục mới: tâm tại mu, trục trùng với eigenvector **u1**, **u2**,..Mà điều này dĩ nhiên có nghĩa là y1 chính là hình chiếu của vector 𝐗 - **μ** lên trục **u1**,  y2 là hình chiếu của vector 𝐗 - **μ** lên trục **u2**,...Cùng chính là cùng kết luận ở trên.
>
>
>
> Xét tiếp EZ = E\[(𝐗-μ)ᵀ𝐮\] = E\[𝐗-μ\]ᵀ𝐮 = (E𝐗-E**μ**)ᵀ𝐮 = (**μ**-**μ**)ᵀ𝐮 = **0**ᵀ𝐮 = 0.
>
>
>
> Như vậy E\[Z²\] thật ra chính là E\[Z² - (EZ)²\] và đây chính là **VARIANCE** của **Z:** Var(𝐙).
>
> Và với ý nghĩa của Z là hình chiếu của (𝐗 - **μ**) lên trục eigenvector 𝐮, thì như vậy ta có thể hiểu vì sao E\[Z²\], **CŨNG LÀ** **EIGENVALUE** **λ**, **CHÍNH LÀ PHƯƠNG SAI CỦA DISTRIBUTION THEO PHƯƠNG EIGENVECTOR** 𝐮, và dĩ nhiên, again, phương sai thì không âm cũng giúp khẳng định lại λ phải không âm.
>
>
>
> ---
>
>
>
> Rồi, ở trên ta đã hiểu λi của Σ chính là phương sai của distribution theo phương eigenvector ui, và do đó  nó phải không âm. Nhưng thậm chí nó phải dương luôn. Lí do có thể tạm hiểu nhanh là vì trong công thức pdf của Normal, Σ xuất hiện ở dạng inverse Σ⁻¹. Mà để invertible, thì Σ phải non-singular / full-rank. Do đó mọi eigenvalue phải khác 0.
>
>
>
> Và như vậy, từ MIT 1806 (cũng như phần Appendix C đã nhắc lại), mọi eigenvalues dương là một trong những cách để check điều kiện matrix là một positive definite matrix (bên cạnh các cách khác như check quadratic form,..)
>
>
>
> Gs cũng nói trong chap 12 ta sẽ làm việc với một phân phối Normal có covariance không đảm bảo mọi eigenvalue đều dương, mà chỉ không âm thôi, khi đó chỉ là positive semi definite. Và, nếu có eigenvalue = 0, thì matrix Σ sẽ singular. Vì sao singular, singular là sao?
>
>
>
> Ôn lại kiến thức trong MIT 18.06: singular là khi matrix tồn tại nonzero vector trong nullspace hoặc left nullspace. Khi đó vector khác 0 đó sẽ bị biến thành 0 bởi matrix. Thế thì, nếu tồn tại eigenvalue bằng 0, thì như đã biết, nếu λ và u là eigenvalue và eigenvector tương ứng, thì ta có Au = λu, vậy nếu λ = 0, thì u chính là vector bị biến thành 0 bởi A: Au = 0u = 0. Nên nó chính là non-zero vector trong nullspace, như vậy nullspace có dimension khác 0, cũng đồng nghĩa các cột của A không độc lập, cũng đồng nghĩa luôn là rank của A nhỏ hơn số hàng số cột, và matrix A không full-rank, không invertible, hay và gọi là matrix suy biến (singular).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú này rất chính xác và thể hiện sự hiểu biết sâu sắc về các khái niệm. Bạn không chỉ tái hiện thông tin từ văn bản gốc mà còn bổ sung thêm các lập luận toán học chặt chẽ và giải thích trực quan về ý nghĩa hình học của các eigenvalues, giúp làm rõ lý do tại sao chúng phải dương. Đây là một cách học tập rất hiệu quả.

<br>

<a id="node-1j3i0ue"></a>

###### Ma trận Jacobian Gaussian

<p align="center"><kbd><img src="assets/brcb013iryt.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì tiếp theo gs nói là ta sẽ xem xét dạng của Gaussian trong hệ trục tọa độ mới. Là sao?
>
>
>
> Có nghĩa là, như đã hiểu khi ta ôn lại kiến thức change of basis matrix trong MIT 1806 ở note trước, việc ta đặt 𝐲 = U(𝐱-**μ**) chính là = (Uᵀ)⁻¹(𝐱-**μ**), có bản chất là ta đã chuyển hệ trục tọa độ về gốc tọa độ mới là **μ** và trục tọa độ bây giờ là các eigenvector, và một điểm có tọa độ 𝐱 trong hệ trục gốc (tức basis 𝐞's) bây giờ sẽ có tọa độ 𝐲 trong basis 𝐮's.
>
>
>
> Và trong bối cảnh ở đây là hàm pdf, thì ta lại liên hệ với kiến thức đã học trong Stat110: Change of variable: Ôn lại nhanh: Khi ta có random variable X \~ fX(x), và áp dụng hàm g(x) lên nó để có một random variable mới: Y = g(X) sao cho ta có mapping 1-1 giữa x belong range X và y belong range Y, đồng nghĩa nếu y = g(x) ⇔ x = g⁻¹(y), thì ta sẽ có theoerem cho phép xây dựng pdf của Y: fY(y) = fX(x) |dx/dy| = fX(g⁻¹(y) |d/dy g⁻¹(y)|.
>
>
>
> Sau đó, tương tự, khái quát lên cho random variable **VECTOR**: 𝐗, và 𝐘 = g(𝐗) thì f𝐘(𝐲) = f𝐗(𝐱) |d𝐱/d𝐲| = f𝐗(𝐱) |d/d𝐲 g⁻¹(𝐱)| Lúc này với việc 𝐲 = g(𝐱) và g⁻¹(𝐲) là vector → vector function, nên đạo hàm của g⁻¹(y) đối với y sẽ là gì: Theo kiến thức đã học trong MIT 18s096, đó sẽ là một matrix, có mỗi hàng là một gradient vector: hàng i sẽ là vector các partial derivative của xi = g⁻¹(y)\_i (phần tử thứ i của vector 𝐱) đối với vector **y:** (∂xi/∂y1, ∂xi/∂y2,....).
>
>
>
> Và matrix này gọi là Jacobian matrix, nên với case này thì change of variable theorem, ta có: f𝐘(𝐲) = f𝐗(𝐱) |J| (thật ra là | |J| |, hay |det(J)| với ý nghĩa: giá trị tuyệt đối của determinant của matrix Jacobian).
>
>
>
> Thế thì quay lại đây (sách Bishop), chính là ta đang đối mặt với bài toán đổi biến (change of variables), khi ta có 𝐗 (hay gs Bishop viết thường 𝐱, như nói nhiều lần, gs Bishop viết thường đối với tên biến có thể gây lú lẫn), có pdf là hàm Gaussian pdf f𝐗(𝐱|**μ**,Σ) = (công thức 2.43). Và nay ta có random variable vector **Y có được bằng cách áp hàm g(x) lên X, với g(x) =** U(𝐱-**μ**), tức là 𝐘 = U(𝐗 - **μ**). Vậy thì áp dụng điều trên ta sẽ có pdf của 𝐘:
>
>
>
> f𝐘(𝐲) = f𝐗(𝐱|**μ**,Σ) |J|
>
>
>
> Vậy J, trong trường hợp này, cụ thể nó sẽ là thế nào: Ta có thể theo định nghĩa đã nói trên, đi tìm Jij, là ∂xi/∂yj. Nhưng MIT 18s096 cho ta một cách làm dễ hơn nhiều - tìm đạo hàm theo lối hoslistically:
>
>
>
> Ta có hàm 𝐲 = U(𝐱 - **μ**) ⇨ 𝐱 = U⁻¹𝐲 + **μ**, = g(𝐲) nếu có thể chỉ ra dg(𝐲) = một linear operator của d𝐲, thì ta sẽ thấy ngay công thức đạo hàm. Làm như sau:
>
>
>
> dg = g(𝐲+d𝐲) - g(𝐲) = U⁻¹(𝐲 + d𝐲 + **μ**) - U⁻¹(𝐲 + **μ**) = U⁻¹d𝐲. Và đây chính là linear operator act on d𝐲, nên đơn giản ta kết luận ngay d/dy g(𝐲), chính là Jacobian = U⁻¹.
>
>
>
> Vậy J = U⁻¹ Nên det J = det U⁻¹, mà U là matrix gì, còn nhớ, gs Bishop, đã define U là matrix mà các hàng là các eigenvector ui của Σ, nên Uᵀ là matrix tạo bởi các cột là các eigenvector ui, và đám này lại orthogonal, và unit norm. Đồng thời mình trong note trước cũng cũng đã nói, với orthogonal matrix thì transpose của nó cũng vậy. Như vậy Uᵀ là orthogonal matrix, thì U cũng vậy. Và như vậy U⁻¹ = Uᵀ (tính chất của orthogonal matrix)
>
>
>
> Như vậy Jacobian **J chính là Uᵀ**, đây chính là **giải thích cho công thức 2.53**: Jij = Uji (chú ý thứ tự ij ngược nhau, vì Uji thực chất chính là (Uᵀ)ij, nên chính là ông đang nói J = Uᵀ)
>
>
>
> Rồi, thế thì tới đây nếu ta còn nhớ kiến thức trong MIT 1806 sau đây thì có thể kết luận luôn |det J| = |det Uᵀ| = 1: determinant, hay tiếng việt là định thức, có ý nghĩa là gì? là tỉ lệ của thể tích của một khối lập phương cạnh bằng 1 sau khi bị linear transform bởi matrix J so với thể tích ban đầu của nó (= 1). Hay trong 2D, thì nó là tỉ lệ của diện tích của hình vuông cạnh = 1 sau khi bị tranform bởi J. Thế thì, ta vừa nói J (chính là Uᵀ) là orthogonal matrix, nên **phép biến đổi tuyến tính bởi J chỉ là PHÉP XOAY, nó bảo tồn diện tích**. Thành ra tỉ lệ này dĩ nhiên là 1. ⇨ det J = det Uᵀ = 1.
>
>
>
> Còn trong sách, gs tính det J² trước, (det J)² = (det Uᵀ)²
>
>
>
> = (det Uᵀ)(det Uᵀ)
>
>
>
> = (det Uᵀ)(det U) (do det A = det Aᵀ)
>
>
>
> = det(Uᵀ U) (det (AB) = det A) (det B))
>
>
>
> = det (I) (do U orthogonal → UᵀU = I)
>
>
>
> = 1.
>
>
>
> Vậy (det J)² = 1 ⇨ det J = +/-1. Nhưng trong công thức change of variable nói trên, như đã nói, thật ra ta lấy trị tuyệt đối của det, nên kết quả là 1.
>
>
>
> Như vậy ta hiểu rõ hai công thức 2.53, và 2.54 cũng như đoạn này nói gì.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Ghi chú của bạn thể hiện sự hiểu biết sâu sắc và toàn diện về ma trận Jacobian và định thức của nó trong ngữ cảnh thay đổi biến cho phân phối Gaussian. Bạn đã giải thích rất chi tiết và chính xác cả hai công thức (2.53) và (2.54) bằng cách liên hệ với các kiến thức nền tảng vững chắc.

<br>

<a id="node-1vavixz"></a>

###### Biến đổi Gaussian độc lập

<p align="center"><kbd><img src="assets/bpuuihrupy7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/l5v9sgibww8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/mjoueeexi2o.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, thử xem vì sao gs nói |Σ| có thể thể hiện bởi tích các eigenvalues?
>
>
>
>  Là vì đơn giản đây là công thức của det thôi: det A = tích các eigenvalue của nó. Và vì các eigenvalue của Σ như vừa nói, đều dương nên ta có |det Σ| = det Σ = Πi λi.
>
>
>
> ⇨ √\[det Σ\] (hay |Σ|^(1/2) = √\[Πi λi\] = (Πi λi)^1/2 = Πi λi^1/2
>
>
>
> Rồi, như vậy ta đã có đủ nguyên liệu để ráp vào công thức đổi biến để có pdf của 𝐘 = U(𝐗 - **μ**):
>
>
>
>  f𝐘(𝐲) = f𝐗(𝐱|**μ**,Σ) |J| với:
>
>
>
> |J| = 1
>
>
>
> f𝐗(𝐱|**μ**,Σ) = công thức 2.43 = \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] exp\[-1/2(𝐱-**μ**)ᵀ Σ⁻¹(𝐱-**μ**)\]
>
>
>
> = \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] exp\[-1/2(U⁻¹𝐲+**μ**-**μ**)ᵀ Σ⁻¹(U⁻¹𝐲+**μ**-**μ**)\]
>
>
>
> = \[1/(2π)^(D/2)\] 1/\[Πi λi^1/2\] exp\[-1/2(Uᵀ𝐲)ᵀ Σ⁻¹(Uᵀ𝐲)\]
>
>
>
> = \[1/(2π)^(D/2)\] 1/\[Πi λi^1/2\] exp\[-(1/2)𝐲ᵀU Σ⁻¹ Uᵀ𝐲\]
>
>
>
>  Xét cụm này: (1/2)𝐲ᵀU Σ⁻¹ Uᵀ𝐲 (bữa trước ta đã phân tích, gọi nó là Δ², và thu gọn nó là thành Σj (yj²/λj)
>
>
>
> Ghi lại đoạn đó: "Thay Σ⁻¹ = Σj=1:D ujujᵀ/λj vào (𝐱 - **μ**)ᵀ Σ⁻¹ (𝐱 - **μ**) ta có:
>
>
>
> = (𝐱 - **μ**)ᵀ \[Σj ujujᵀ/λj\] (𝐱 - **μ**)
>
>
>
> = Σj \[(𝐱 - **μ**)ᵀujujᵀ(𝐱 - **μ**)/λj\] | đưa (𝐱 - **μ**)ᵀ và (𝐱 - **μ**) vào
>
> trong tổng.
>
>
>
> Đặt yj = (𝐱 - **μ**)ᵀuj (cũng là ujᵀ(𝐱 - **μ**) vì cái này là scalar), ta có:
>
>
>
> = Σj (yjᵀyj/λj) = Σj (yj²/λj) → 2.51"
>
>
>
> Nhưng ở đây mình có thể làm theo cách khác cũng ra: Xét 𝐲ᵀU Σ⁻¹ Uᵀ𝐲, ta phân tách trị riêng (eigenvalue decomposition) đối với Σ⁻¹ = Q H Qᵀ với Q là orthogonal matrix có các cột là eigenvector của Σ⁻¹, và như đã biết, Σ và Σ⁻¹ có chung bộ eigenvector : tức là nếu λ, u là eigenvalue, eigenvector của Σ thì 1/λ, u cũng là eigenvalue, eigenvector của Σ⁻¹. Nên Q chính là Uᵀ. Còn H là diagonal matrix có đường chéo là các eigenvalue của Σ⁻¹. Vậy thì vì ta đang gọi λ1, λ2,... là các eigenvalue của Σ nên eigenvalue của Σ⁻¹ là 1/λ1, 1/λ2,.... ⇨ H chính là diag(1/λ1, 1/λ2,...,1/λD). Vậy ta có Σ⁻¹ = Q H Qᵀ = Uᵀ diag(1/λ1, 1/λ2,...,1/λD) U.
>
>
>
> Thay vào 𝐲ᵀU Σ⁻¹ Uᵀ𝐲 = 𝐲ᵀU Uᵀ diag(1/λ1, 1/λ2,...,1/λD) U Uᵀ 𝐲
>
>
>
> với U thì ta đã biết Uᵀ = U⁻¹ nên biểu thức trên = 𝐲ᵀ diag(1/λ1, 1/λ2,...,1/λD) 𝐲,
>
>
>
> và cái này chính là Σi=1:D yi²/λi.
>
>
>
> Vậy tóm lại, f𝐘(𝐲) (trong sách gs Bishop ghi là p(𝐲)) là:
>
>
>
> \[1/(2π)^(D/2)\] 1/\[Πi=1:D λi^1/2\] exp\[-(1/2)Σi=1:D yi²/λi\]
>
>
>
> = \[Πi=1:D\[1/(2π)^(1/2)\] 1/\[Πi=1:D λi^1/2\] exp\[-(1/2)Σi=1:D yi²/λi\]
>
>
>
> = Πi=1:D \[1/(2πλi)^(1/2)\] exp\[-Σi=1:D yi²/2λi\]
>
>
>
> = Πi=1:D { \[1/(2πλi)^(1/2)\] exp\[-yi²/2λi\] } (cái tổng trong exp(), tách ra thành tích các exp luôn: e^(a+b) = e^a e^b)
>
>
>
> → **Và** **đây chính là 2.56**
>
>
>
> ---
>
>
>
> Và nhận xét quan trọng đó là: xét một thừa số trong tích:
>
>
>
> 1/(2πλi)^(1/2)\] exp\[-yi²/2λi\]
>
>
>
> Có thể thấy, nó chính là công thức pdf của Normal(0, λi), nhớ ko, với normal(μ, σ²) thì pdf là \[1/√(2πσ²)\] exp\[-(x-μ)/2σ\].
>
>
>
> Đến đây ta lập luận như sau: Dùng kiến thức của Stat110 đã học: Xét joint pdf của các random variable X1,X2,...Xn. f𝐗(x1,x2,..), nếu có thể factor nó thành tích các marginal pdf: fX1(x1)fX2(x2)...fXn(xn). Thì có thể suy ra các random variable X1,X2,...Xn **ĐỘC LẬP**. (independent)
>
>
>
> Vậy ở đây, f𝐘(𝐲), thật ra chính là joint pdf của D random variable Y1, Y2,...YD (các phần tử của vector 𝐘). Và cái công thức 2.57, là joint pdf của chúng, như đã thấy, lại chính là tích các marginal pdf của các random variable Y1,Y2....YD đơn lẻ.
>
>
>
> **NHƯ VẬY KẾT LUẬN: Y1, Y2,....YD LÀ CÁC RANDOM VARIABLE ĐỘC LẬP.**
>
>
>
> **Và ý nghĩa của điểu này chính là: Việc đổi biến, từ X sang Y, bằng cách shift bởi μ và xoay trục sao cho trùng với các eigenvector của Σ đã giúp cho trong hệ trục tọa độ mới, các tọa độ trở nên hoàn toàn độc lập nhau. Đây chính là ý mà gs Bishop nói ở đây** "*eigen- vectors therefore define a new set of shifted and rotated **coordinates** with respect to which the joint probability distribution factorizes into a product of independent distributions"*
>
>
>
> ---
>
>
>
> Ý cuối chỉ là gs nói về việc khi ta marginalizing pdf của 𝐘 over toàn bộ range 𝐘, thì bằng cách đưa tích phân của tích thành tích các tích phân, và các tích phân này đều bằng 1 do tính valid của pdf nên kết quả là tích của các số 1, nên bằng 1. Cho thấy pdf của Y là một valid pdf. Ví dụ, để dễ hiểu thì ta có thể xét case hai biến Y1,Y2:
>
>
>
> ta có f𝐘(𝐲) = f𝐘(y1,y2) = Πi=1:2 { \[1/(2πλi)^(1/2)\] exp\[-yi²/2λi\] }
>
>
>
> = \[1/(2πλ1)^(1/2)\] exp\[-y1²/2λ1\] \[1/(2πλ2)^(1/2)\] exp\[-y2²/2λ2\]
>
>
>
> = f(y1) f(y2).
>
>
>
> Và xét tích phân trên toàn bộ range 𝐘, trong trường hợp này là toàn mặt phẳng 2D:
>
>
>
> ∫-inf:inf∫-inf:inf f𝐘(𝐲) d𝐲 = ∫-inf:inf∫-inf:inf f𝐘(y1,y2) dy1dy2
>
>
>
> = ∫-inf:inf∫-inf:inf f(y1) f(y2) dy1dy2
>
> \
> Tính tích phân theo y1 trước, thì vì f(y2) ko dính gì tới y1 nên đưa ra ngoài:
>
> = ∫-inf:inf \[∫-inf:inf f(y1)  dy1\] f(y2) dy2
>
> Tíếp, xét tích phân theo y2, thì vì \[∫-inf:inf f(y1)  dy1\], ko dính gì đến y2, nên đưa ra ngoài 
>
>
>
> = \[∫-inf:inf f(y1) dy1\] \[∫-inf:inf f(y2) dy2\]
>
>
>
> Và mỗi cách tích phân này, theo tính valid của một pdf, nên bắt buộc phải bằng 1.
>
>
>
> kết quả là 1 x 1 = 1.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bạn đã thể hiện sự hiểu biết sâu sắc và toàn diện về chủ đề này. Các bước chứng minh chi tiết và logic, đặc biệt là việc sử dụng hai phương pháp để đơn giản hóa số mũ và liên hệ kết quả với ý nghĩa về sự độc lập của các biến ngẫu nhiên là rất xuất sắc. Việc bạn kết nối trực tiếp các công thức toán học với các phát biểu lý thuyết của Bishop cho thấy một sự nắm vững kiến thức vững chắc.

**🔗 See also:** [Phân phối Gaussian](#node-arii2cl)

<br>

<a id="node-tx5105q"></a>

###### Chứng minh Mean Gaussian

<p align="center"><kbd><img src="assets/nfec6grlboc.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, có thể hiểu đoạn này là gs nói rằng ta sẽ xem xét các moment của nó. Từ Stat110 mình đã biết, nói về moment, khái niệm moment của distribution, được define như sau: moment bậc n là E\[Xⁿ\]. Và như vậy **moment bậc 1, chính là mean** của distribution, EX. Còn **moment bậc 2**, EX², sẽ giúp ta tính **variance** với công thức VarX = EX² - (EX)².
>
>
>
> Thế thì dù mình vẫn hay mặc định là nói với X \~ normal(μ, σ²) thì μ chính là mean EX. Nhưng thực ra phải chứng minh. Như trong Stat110 đã làm, ta sẽ dựa vào định nghĩa của kì vọng, để chứng minh mean của Z\~ Normal(0, 1) là 0 trước, làm như sau: (đây cũng là ôn lại, nhưng sẽ cho ta thấy cái mà gs Bishop làm ở đoạn này thật ra là y chang)
>
>
>
> EZ = ∫-inf:inf zfZ(z) dz = ∫-inf:inf z \[1/√(2π)\] exp(-z²/2) dz
>
>
>
> = \[1/√(2πσ²)\] ∫-inf:inf z exp(-z²/2σ²) dz (đưa constant ra ngoài tích phân)
>
>
>
> Thế thì biểu xét biểu thức trong tích phân, coi nó như hàm g(z) = z exp(-z²/2σ²) thì nó là một hàm có tính chất:
>
>
>
> g(-z) = -z exp(-(-z)²/2σ²) = -z exp(-z²/2σ²) = -g(z)
>
>
>
> Vậy nó là một hàm lẻ (odd function). Mà với hàm lẻ, khi ta tích phân từ -inf tới inf, thì các giá trị sẽ cancel out nhau (hủy nhau). Nên kết quả là 0.
>
>
>
> ⇨ EZ = 0. Và từ đó, dùng location scale theorem, nói rằng nếu ta có Z \~ standard member của một location scale family, thì σZ + μ sẽ là thành viên ứng với location μ và scale σ. Với normal, nó là một location scalar family, thành ra theo đó, X = σZ + μ chính là một normal có location μ và scale σ: X \~ normal(μ, σ²)
>
>
>
> Chứng minh cũng dễ: X = σZ + μ = g(Z) ⇨ Z = (X-μ)/σ = g⁻¹(X). Dùng change of variable theorem, tính pdf của X:
>
>
>
> fX(x) = fZ(z) |dz/dx| = fZ(g⁻¹(x)) |d/dx g⁻¹(x)|
>
>
>
> = fZ((x-μ)/σ) |d/dx \[(x-μ)/σ\]|
>
>
>
> = (1/√2π) exp\[-((x-μ)/σ)²/2\] |1/σ|
>
>
>
> = (1/√2π) exp\[-(x-μ)/2σ²\] (1/σ)
>
>
>
> = (1/√2πσ²) exp\[-(x-μ)/2σ²\] → đây chính là pdf của normal(μ, σ²).
>
>
>
> Đến đây ta sẽ dùng linearity để tính EX: EX = E(σZ + μ) = σE(Z) + E(μ) = σ0 + μ = μ. Giúp kết luận với normal(μ, σ²) thì location μ chính là mean của distribution.
>
>
>
> Chú ý, thường thì ta cứ nghe người ta nói rằng nói normal(μ, σ²) thì mean là μ, variance là σ². Tuy nhiên, đó là kết luận, ta phải chứng minh. Và việc chứng minh chính là như trên vừa làm: Chứng minh nếu X có pdf là 1/√(2πσ²) exp\[-(x-μ)²/2σ\] thì EX = μ.
>
>
>
> ---
>
>
>
> Rồi, quay lại đây, cái gs Bishop làm cũng là tương tự, ta có 𝐗 có pdf:
>
>
>
> f(𝐱) = \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] exp\[-1/2(𝐱-**μ**)ᵀ Σ⁻¹(𝐱-**μ**)\],
>
>
>
> ta sẽ phải chứng minh E𝐗 = **μ**.
>
>
>
> Theo định nghĩa của kì vọng:
>
>
>
> E𝐗 = ∫𝐱f(𝐱)d𝐱 = ∫𝐱 \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] exp\[-1/2(𝐱-**μ**)ᵀ Σ⁻¹(𝐱-**μ**)\] d𝐱
>
>
>
> = \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] ∫𝐱 exp\[-1/2(𝐱-**μ**)ᵀ Σ⁻¹(𝐱-**μ**)\] d𝐱
>
>
>
> Tới đây, ông Bishop đổi biến tích phân bằng cách đặt 𝐳 = 𝐱 - **μ** thì thực ra cái ổng làm cũng chính là lặp lại những gì ta làm ở trên, chẳng qua là nó hơi khó để thấy, như sau:
>
>
>
> Đặt 𝐳 = 𝐱 - **μ ⇨** d𝐳 = d𝐱, và cận của tích phân thì vẫn vậy (vẫn là toàn miền R^D)
>
>
>
>  Khi đó, E𝐗 = \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] ∫ (𝐳+**μ**) exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳
>
>
>
> = \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] ∫ 𝐳 exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳 +
>
>   \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] ∫ **μ** exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳
>
>
>
> Xét term thứ nhất, và xét cái cụm ∫ 𝐳 exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳, ta sẽ thấy mr Bishop dùng lập luận y chang: vì hàm exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] là hàm chẵn, do exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] = exp\[-(1/2) (-𝐳)ᵀ Σ⁻¹ (-𝐳)\], nên 𝐳 exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] là hàm lẻ. Và vì vậy khi tích phân trên toàn miền sẽ ra 0.
>
>
>
> (Chú ý nhé, ông nói "exponent is an even function of the components of z" là đang nói  cái cục exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] làm hàm chẵn. nhưng ở ngoài còn thằng 𝐳 nữa, nên 𝐳 exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] là hàm lẻ, và khi đó thì tích phân trên toàn miền nó mới bị triệt tiêu (vanish) do tính đối xứng (symmetry))
>
>
>
> Nên ông mới nói "*the term in z in the factor (z + μ) will vanish by symmetry*" là vậy.
>
>
>
> Và hãy nhìn kĩ cái term thứ nhất, \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] ∫ 𝐳 exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳, ta sẽ thấy nó chính là E𝐙.
>
>
>
> Vậy chỉ còn cái term thứ 2: \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] ∫ **μ** exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳
>
>
>
> Để làm tiếp, đưa μ ra ngoài tích phân, thật ra là đưa hẳn ra ngoài luôn
>
>
>
> **μ** { \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] ∫ exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳 }
>
>
>
> đưa cái cụm constant vào trong tích phân lại:
>
>
>
> **μ** { ∫ \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳 }
>
>
>
> thì lúc này, cái cụm { ∫ \[1/(2π)^(D/2)\] \[1/|Σ|^1/2\] exp\[-(1/2) 𝐳ᵀ Σ⁻¹ 𝐳\] d𝐳 } chính là marginalizing pdf của Z over R^D. nên theo tính valid của pdf, nó phải bằng 1.
>
>
>
> Kết quả term 2 bằng **μ**. giúp ta có E𝐗 = **μ**, giúp chứng minh μ chính là mean của Normal(**μ**, Σ).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Phân tích rất chi tiết và chính xác, giải thích cặn kẽ từng bước và cung cấp bối cảnh vững chắc từ Stat110, làm rõ hoàn toàn ý tưởng 'biến mất do đối xứng' mà tài liệu gốc chỉ trình bày ngắn gọn. Đây là một ghi chú xuất sắc giúp hiểu sâu sắc hơn về việc chứng minh kỳ vọng của phân phối Gaussian.

<br>

<a id="node-b5enpfj"></a>

###### Kì vọng XXᵀ Gaussian

<p align="center"><kbd><img src="assets/wfu7ulrdn68.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo xét qua second orther moment. Như nãy đã nói, n'th order moment của X là E\[Xⁿ\], nên 2nd order moment là E\[X²\]. Tuy nhiên với D-dimensional random variable vector 𝐗 (có D variables X1, X2,...XD) thì ta sẽ biết thêm một kiến thức đó là, sẽ có D² cái 2nd order moment, mỗi cái là E\[XiXj\] với i,j=1,2...D. Và có thể gom lại để thể hiện cả đám ở dạng matrix E\[**XX**ᵀ\].
>
>
>
> > Dừng lại chút để nói rõ thêm về cái này: Vì sao E\[**XX**ᵀ\] là matrix? → à đơn giản là vì **XX**ᵀ (𝐗 nhân với 𝐗 transpose), thì đây chính là outer product của vector 𝐗 và chính nó, kết quả, như đã biết trong MIT 1806, sẽ là một rank 1 matrix. (sẵn nói luôn cho vui, vì sao rank 1? Là vì ta sẽ coi đây là phép nhân hai matrix có shape D-1 nhân với matrix 1-D, theo góc nhìn thứ hai khi nhân matrix A với B, thì cột j của AB là linear combination các cột của A bởi hệ số là cột j của B. Vậy thì A=𝐗 là matrix có mỗi 1 cột, nên cột j của AB=**XX**ᵀ sẽ là chỉ là phần tử thứ j của vector 𝐗 nhân với cột của A, tức là vector 𝐗, như vậy có thể thấy mọi cột của **XX**ᵀ đều chỉ là vector 𝐗 nhân với một số nào đó, là phần tử của vector 𝐗, vậy nên chắc chắn nó chỉ có duy nhất một cột độc lập ⇨ rank = 1.)
>
>
>
> Tiếp, thế thì **XX**ᵀ là matrix, và vì 𝐗 là random variable vector, nên **XX**ᵀ là một random variable matrix. Và kì vọng của nó, sẽ là matrix có các component là kì vọng của từng phần tử của matrix, nên dĩ nhiên E\[**XX**ᵀ\] là matrix.
>
>
>
> (Lại phải nhắc lại phòng khi có người đọc bản note của mình đó là ở sách này gs Bishop ko dùng cách quy ước kí hiệu thông thường của toán học thống kê xác suất như trong sách Casella, Stat110 - Havard đó là viết hoa với tên biến, viết thường với giá trị biến, tuy vậy ông vẫn viết đậm ở vector, viết nét mảnh ở biến scalar. Cách làm này có thể có chút tiện lợi nhưng với mình là người học Stat110 và Casella, việc này khiến nó thấy sao sao á, nên mình sẽ vẫn theo kí hiệu của Stat110 và Casella, trong đó ngoài chuyện viết hoa, thường, mình sẽ thường dùng chữ f để chỉ phân phối xác suất thay vì p. Có thể qua bối cảnh khác ở những chương sau, ta sẽ có lúc phải theo cách ghi của gs Bishop.)
>
>
>
> Rồi, thế thì vì sao có công thức E\[**XX**ᵀ\] dài thòng lòng như trong đoạn này?
>
>
>
> Thật ra chỉ là theo định nghĩa của kì vọng và LOTUS, EX là weighted average của các possible value của X, với weight là xác suất tương ứng: P(X=x) (giả sử xét discrete random variable X) ⇨ EX = Σ{mọi possible value x của X} xP(X=x), và với continous variable thì EX = ∫xfX(x)dx với fX(x) là pdf của X.
>
>
>
> Thế thì, giả sử ta có Y = g(X), thì đáng lẽ để tính EY ta phải tìm pdf/pmf của Y. Nhưng LOTUS cho phép tính EY mà chỉ việc xài luôn pdf/pmf của X: EY = Eg(X) = ∫g(x)fX(x)dx.
>
>
>
> Tiếp, giả sử ta có hai biến X,Y. và muốn tính kì vọng của Z với Z = g(X,Y). Thì ta cũng có cái gọi là 2D LOTUS, cho phép tính EZ mà chỉ cần dùng joint pdf của X, Y kí hiệu fX,Y(x,y) chứ khỏi phải dùng pdf/pmf của Z: EZ = ∫∫g(x,y)fX,Y(x,y)dxdy.
>
>
>
> Vậy thì quay lại đây cũng y chang vậy, như đã nói, E\[XXᵀ\] là matrix mà mỗi phần tử ij là E\[XiXj\]. Vậy thì E\[XiXj\] có thể thấy nó chính là E\[g(Xi,Xj)\] với g(xi,xj) = xixj. Nên theo 2D LOTUS, ta có E\[XiXj\] = ∫∫xixj fXiXj(xi,xj)dxidxj.
>
>
>
> Tuy nhiên, ta có thể coi XiXj là một hàm của X1,X2,...XD luôn: ví dụ g(x1,x2,...xD) = x1x2, vẫn được, để rồi khi đó thay vì 2D LOTUS, ta có D-D LOTUS luôn: E\[XiXj\] = E\[g(X1,X2,...XD)\]
>
>
>
> = ∫..∫ g(x1,x2,..xD) f(x1,x2...xD) dx1dx2...dxD
>
>
>
> (f(x1,..xD) là joint pdf của X1,..XD), nói cách khác chính là f𝐗(𝐱), mà đang xét ở đây là pdf của N(**μ**, **Σ**) đó
>
>
>
> viết gọn lại thành:
>
>
>
> ∫ xixj f(𝐱)d𝐱.
>
>
>
> Như vậy phần tử ij của E\[**XX**ᵀ\] sẽ có dạng ∫xixj f(𝐱)d𝐱
>
>
>
> > Và, như vậy ta sẽ thể hiện E\[**XX**ᵀ\] = ∫ **xx**ᵀ f(𝐱)d𝐱. Vì sao, hiểu thế này: **xx**ᵀ là matrix DxD có phần tử ij là xixj. Còn f(𝐱) thì là scalar, là giá trị pdf tại 𝐱, nên **xx**ᵀ f(𝐱) là matrix nhân scalar = matrix, có phần tử ij là \[xixj f(𝐱)\]. Còn việc lấy tích phân, thì ∫ **xx**ᵀ f(𝐱)d𝐱 sẽ chỉ là tổng của vô số matrix, để kết qủa là matrix có phần tử ij là tổng của vô số phần tử ij của các matrix đó, chính là ∫ xixj f(𝐱)d𝐱.
>
>
>
> Như vậy khi đã hiểu E\[**XX**ᵀ\] = ∫ **xx**ᵀ f(𝐱)d𝐱, chỉ việc thay f(𝐱) pdf của Normal(**μ**, Σ) vào:
>
>
>
> E\[**XX**ᵀ\] = ∫ **xx**ᵀ \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] exp {-(1/2)(𝐱-**μ**)ᵀ Σ⁻¹ (𝐱-**μ**)} d𝐱
>
>
>
> và đưa các constant ra ngoài tích phân ta sẽ có:
>
>
>
> \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **xx**ᵀ exp {-(1/2)(𝐱-**μ**)ᵀ Σ⁻¹ (𝐱-**μ**)} d𝐱, đây chính là hàng trên của cái công thức trong đoạn này.
>
>
>
> Và làm tương tự như khi tính E\[𝐗\], đặt 𝐳 = 𝐱 - **μ**, và đổi biến tích phân sang 𝐳, ta có:
>
>
>
> \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ (𝐳+**μ**)(𝐳+**μ**)ᵀ exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳
>
>
>
>  → Là ta đã hiểu hết được đoạn này.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bài phân tích rất sâu sắc và chính xác về các khái niệm moment bậc hai cho biến ngẫu nhiên đa chiều và ma trận hiệp phương sai. Việc giải thích chi tiết về định nghĩa E[XX^T] và cách thức áp dụng LOTUS cho biến ngẫu nhiên ma trận là điểm mạnh nổi bật, thể hiện sự nắm vững kiến thức. Bạn chỉ cần chú ý một lỗi nhỏ chính tả ở từ "orther" thay vì "order".

<br>

<a id="node-4n8u0a8"></a>

###### E[XXᵀ] Phân tích Eigen

<p align="center"><kbd><img src="assets/ovdcek71dg9.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/csomiytvs3v.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/opmpzodewzd.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/emiod0tpr1g.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì, ta đang có E\[**XX**ᵀ\] = \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ (𝐳+**μ**)(𝐳+**μ**)ᵀ exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳
>
>
>
>  Tiếp theo ta sẽ mở cái tích (𝐳+**μ**)(𝐳+**μ**)ᵀ ra: = (𝐳+**μ**)(𝐳ᵀ+**μ**ᵀ) = **zz**ᵀ+**μz**ᵀ+ **zμ**ᵀ+**μμ**ᵀ, vậy thì chú ý ở đây ko phải mr Bishop nói hai cục **μz**ᵀ và **zμ**ᵀ cancel nhau đâu nhé, mà phải hiểu là, ta tách cái tích phân này thành tổng của 4 cái tích phân:
>
>
>
> \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **zz**ᵀ exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳 +
>
>
>
> \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **μz**ᵀ exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳 +
>
>
>
> \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **zμ**ᵀ exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳 +
>
>
>
> \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **μμ**ᵀ, exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳 +
>
>
>
> Và xét cái thứ 2, và 3, ta sẽ thấy hàm trong tích phân là hàm lẻ, nên tích phân trên toàn miền sẽ bằng 0, đây mới là ý của gs khi nói "the cross-term involving **μz**ᵀ và **zμ**ᵀ will again vanish by symmetry"
>
>
>
> Còn cái thứ 4, vì **μμ**ᵀ ko dính tới 𝐳, nên đưa ra ngoài, đồng thời đưa hai cụm constant vào trong lại, để có:
>
>
>
> **μμ**ᵀ ∫ \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳
>
>
>
> và cái tích phân này, chính là hành động marginalizing một hàm pdf của Z \~ Normal(0, **Σ**) trên toàn miền, nên theo tính valid của pdf, thì nó phải bằng 1 (đây chính là khúc ổng nói "**which itself is unity, because Gaussian distribution is normalized**". Vậy term 4 chỉ còn **μμ**ᵀ, để nó ở đó.
>
>
>
> Giờ quay lại term 1 trong 4 cái ở trên: \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **zz**ᵀ exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳
>
>
>
> Gs mới nói tiếp, ta sẽ dùng kết quả của việc phân tách eigendecomposition (cái chữ decomposition vốn có nghĩa là phân tách, phân rã) đối với matrix covariance Σ. Là sao?
>
>
>
> Là vầy, làm lại cho nhớ ko thừa, ta đã biết Σ là symmetric, và Σ⁻¹ cũng vậy. Theo MIT 1806 đã học, một khi ta có matrix đối xứng thì eigenvalue của nó chắc chắn có giá trị thực và luôn có thể chọn một bộ eigenvector orthognormal với đủ số lượng để span toàn bộ R^D (D là kích thước matrix). Và ở đây ta đã gọi 𝐮1,...𝐮D là bộ eigenvector như vậy của Σ (và cũng là của Σ⁻¹), đặt nó thành các hàng của U, cũng là các cột của Uᵀ, thì ta sẽ có phép eigendecomposition của Σ sẽ là: Σ⁻¹ = (Uᵀ)ᵀ Λ⁻¹ Uᵀ = U Λ⁻¹ Uᵀ với Λ là diag(1/λ1,..1/λD), diagonal matrix có các eigenvalues của Σ⁻¹ (cũng là nghịch đảo các eigenvalue của Σ) trên đường chéo.
>
>
>
> (Chỗ này có chút dễ confuse do cách mr Bishop gọi U là matrix có các hàng là các eigenvector 𝐮1,..𝐮D thay vì đặt chúng làm cột của U, cách làm này khiến Uᵀ mới là matrix có các cột là eigenvector. Và theo lí thuyết MIT 1806, thì khi Q là matrix có các cột là eigenvector của A, Λ là matrix các eigenvalues, thì ta có A = Qᵀ Λ Q. Vậy áp dụng vào Σ thì Σ = (Uᵀ)ᵀ Λ⁻¹ Uᵀ, và tiếp tục = U Λ⁻¹ Uᵀ)
>
>
>
> Tiếp, xét bản chất của Uᵀ Λ⁻¹ U, có thể hiểu theo góc nhìn nhân hai matrix Uᵀ, và Λ⁻¹U, với Uᵀ có các cột như đã nói, là eigenvectors 𝐮1,...𝐮D. Và Λ⁻¹U là matrix có các hàng là 𝐮1/λ1, 𝐮2/λ2,.... (chú ý, phải hiểu 𝐮1/λ1 là lấy scalar 1//λ1 nhân vector = vector). Theo 4 góc nhìn nhân hai matrix thầy Strang đã dạy thì góc nhìn thứ 4 sẽ thấy nó là tổng các rank 1 matrix tạo bởi các outer product của một cột của Uᵀ và một hàng của Λ⁻¹ U. Từ đó ta có:
>
>
>
> Σ⁻¹ = Uᵀ Λ⁻¹ U = Σi=1:D 𝐮i (λ𝐮i)ᵀ = Σi=1:D 𝐮i𝐮iᵀ/λi, viết gọn là Σi 𝐮i𝐮iᵀ/λi
>
>
>
> Vậy thế vào \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **zz**ᵀ exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳, ta có:
>
>
>
> \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **zz**ᵀ exp {-(1/2)𝐳ᵀ (Σi 𝐮i𝐮iᵀ/λi) 𝐳} d𝐳
>
>
>
> Xét cái cục này 𝐳ᵀ (Σi 𝐮i𝐮iᵀ/λi) 𝐳, đưa 𝐳 vào trong tổng, = Σi \[𝐳ᵀ(𝐮i𝐮iᵀ/λi)𝐳\] = Σi \[(𝐳ᵀ𝐮i)(𝐮iᵀ𝐳)/λi\]
>
>
>
> Đặt yi = 𝐳ᵀ𝐮i, chú ý, nó là scalar, kết quả của dot product của hai vector 𝐳 và 𝐮i, và vì là scalar nên yi = yiᵀ,
>
>
>
> .. = Σi \[(yi yiᵀ)/λi\] = Σi \[(yi yi)/λi\] = Σi (yi²/λi), hay chuyển index variable thành k (tất nhiên vẫn hiểu k=1:D) để chuẩn bị cho lát nữa, ta có
>
>
>
> 𝐳ᵀ (Σi 𝐮i𝐮iᵀ/λi) 𝐳 = Σk (yk²/λk)
>
>
>
> Rồi, nãy giờ, ta chỉ mới dùng cái ý mà gs Bishop nói "make use of eigenvector expansion of covariance matrix" để mà giải thích vì sao 𝐳ᵀ (Σi 𝐮i𝐮iᵀ/λi) 𝐳 = Σk (yk²/λk), giúp ta hiểu ở đâu ra có cái cục Σk (yk²/2λk) trong công thức 2.61 trong sách.
>
>
>
> Thế thì sau ý đó ông nói "together with the completeness of the eigenvectors set". Là sao? Thật ra ko có gì khó, nó chính là nói cái ý mà ta nói ở trên, rằng, theo thầy Strang đã dạy trong MIT 1806, matrix A size nxn đối xứng thì luôn có thể có một bộ eigenvector orthogonal và hơn nữa chúng còn đủ số lượng n vector độc lập. Có nghĩa là, không chỉ chúng có một bộ eigenvector orthogonal, mà chúng còn có đủ n vector. Phải nhấn mạnh ý này là vì, không phải cứ là matrix vuông size nxn thì sẽ luôn có đủ n eigenvector độc lập, vì nếu như nó bị defective, là khi có eigenvalue trùng nhau, thì khi đó trong n eigenvector, thì sẽ có những cái phụ thuộc nhau (trùng phương nhau), dẫn đến ta ko có một bộ n vector độc lập, và dẫn đến chúng không thể span được toàn bộ Rⁿ, cũng là cách nói của việc, chúng không làm thành basis của Rⁿ, và cũng đồng nghĩa luôn với việc nếu chỉ lấy các vector độc lập, và orthogonal đó ra, đặt các vector đó vào các cột của Q, thì Q không phải là orthogonal matrix, là cho dù bộ vector đó vẫn được gọi là orthogonal, nhưng vì không đủ n vector, nên Q không vuông, nên dù vẫn có các cột orthogonal, hoặc chuẩn hóa thành unit norm, để thành orthonormal thì nó vẫn không được gọi là orthogonal matrix, mà chỉ đơn giản gọi là matrix có các cột orthonormal mà thôi.
>
>
>
> Vậy thì quay lại đây, việc Σ đối xứng giúp không những eigenvector orthogonal mà còn có đủ D cái. Thành ra chúng sẽ tạo một basis để span toàn bộ R^D Đây chính là ý "completeness of the eigenvectors set" của ngày Bishop. Và như vậy, bất kì vector 𝐳 nào cũng đều có thể được thể hiện bởi linear combination của các basis vector 𝐮i này.
>
>
>
> Thế thì, quay lại nói về vector 𝐳, vừa rồi mình đã có đặt yi = 𝐳ᵀ𝐮i. Thì chỗ này ta sẽ dùng một kiến thức nữa của MIT 1806: Là khi ta có một unit vector **q**, thì 𝐚ᵀ**q**, chính là độ dài của a trên q, và vì q có độ dài đơn vị, nên đây cũng chính là tọa độ của a trên trục q. Và nếu ta có một orthogonal basis **q**1, **q**2,...**q**n, thì 𝐚ᵀ**q**1, 𝐚ᵀ**q**2,....𝐚ᵀ**q**n chính là tọa độ của a trong hệ tọa độ basis **q**1, **q**2,.., đồng nghĩa: 𝐚 = (𝐚ᵀ**q**1) **q**1 + (𝐚ᵀ**q**2) **q**2 + ...+ (𝐚ᵀ**q**n) **q**n
>
>
>
> (Nếu muốn nói rõ hơn thì có thể sẵn tiện ôn lại cái gốc của nó: Phép chiếu Gram-Smidth mình sẽ ghi ở cuối)
>
> Như vậy, y1,...yD chính là tọa độ của 𝐳 trong basis 𝐮1,...𝐮D.  Và do đó: 𝐳 = y1 𝐮1 + y2 𝐮2 + .. = Σj=1:D yj𝐮j, viết gọn Σj yj𝐮j → đây chính là 2.60.
>
>
>
> Vậy thì tới đây đã đủ nguyên liệu, ráp vào, và bây giờ tích phân cũng trở thành theo 𝐲 thay vì **z.** Ta có
>
>
>
> \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **zz**ᵀ exp {-(1/2)𝐳ᵀ (Σi 𝐮i𝐮iᵀ/λi) 𝐳} d𝐳
>
>
>
> = \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ (Σj yj𝐮j) (Σj yj𝐮j)ᵀ exp {-(1/2) \[Σk (yk²/λk)\] } d𝐲
>
>
>
> Xét ∫ (Σj yj𝐮j) (Σj yj𝐮j)ᵀ exp {-(1/2) \[Σk (yk²/λk)\] } d𝐲:
>
>
>
> để dễ thấy ta xem D = 2 thì cái này là:
>
>
>
> ∫ (y1𝐮1 + y2𝐮2)(y1𝐮1 + y2𝐮2)ᵀ \[scalar h(𝐲)\] d𝐳, với (h(𝐲) = exp{...})
>
>
>
> Ta sẽ thấy, bằng cách tách cái tích (y1𝐮1 + y2𝐮2)(y1𝐮1 + y2𝐮2)ᵀ, ta sẽ tách cái tích phân này thành tổng của 4 tích phân mà mỗi cái gắn với một trong 4 term:
>
> (y1²)𝐮1(𝐮1T), y1y2𝐮1(𝐮2T), y2y1𝐮2(𝐮1T), (y2²)𝐮2(𝐮2T).
>
>
>
> Có nghĩa là ta sẽ có Σi=1:2 Σj=1:2 ∫ yi yj 𝐮i 𝐮jᵀ h(𝐲) d𝐲
>
>
>
> Vậy nên \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\]∫ (Σj yj𝐮j) (Σj yj𝐮j)ᵀ exp {-(1/2) \[Σk (yk²/λk)\] } d𝐲
>
>
>
> = \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] Σi=1:D Σj=1:D ∫ yi yj 𝐮i 𝐮jᵀ exp {-\[Σk (yk²/λk)\] } d𝐲
>
>
>
> Đưa yiyj ra cuối, và đưa uiuj ra ngoài tích phân
>
>
>
> = \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] Σi=1:D Σj=1:D 𝐮i 𝐮jᵀ ∫ exp {-\[Σk (yk²/λk)\] } yi yj d𝐲
>
>
>
> → đây chính là kết quả trong sách (cái dấu = thứ 2)
>
>
>
> ---
>
>
>
> Để làm tiếp, ông nói ta sẽ xài kết quả 1.50, 2.55 và 2.48. Là như sau:
>
>
>
> Ta đưa cái cụm hằng số vào lại trong tổn và vào luôn trong tích phân:
>
>
>
> = Σi=1:D Σj=1:D 𝐮i 𝐮jᵀ ∫ \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] exp {-\[Σk (yk²/λk)\] } yi yj d𝐲
>
>
>
>  Xét cụm này: ∫ \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] exp {-\[Σk (yk²/λk)\] } yi yj d𝐲
>
>
>
> Dùng 2.55 |Σ|^(1/2) = Πj=1:D λj^(1/2)
>
>
>
> = ∫ \[1/(2π)^(D/2)\] \[1/(Πj=1:D λj^(1/2))\] exp {-\[Σk (yk²/λk)\] } yi yj d𝐲
>
>
>
> = ∫ Πj=1:D \[1/(√(2πλj)\] exp {-\[Σk (yk²/λk)\] } yi yj d𝐲
>
>
>
> nếu i khác j:
>
>
>
> = ∫ Πj=1:D \[1/(√(2πλj)\] exp {-\[Σk (yk²/λk)\] } yi yj dy1dy2...dyD
>
>
>
> = ∫ Πj=1:D \[1/(√(2πλj)\] exp {-y1²/λ1}...exp {-yD²/λD} yi yj dy1dy2...dyD
>
>
>
> = ∫ Πj=1:D \[1/(√(2πλj)\] exp {-y1²/λ1} y1 ...exp {-yD²/λD} yi yj dy1dy2...dyD
>
>
>
> khi đó ta sẽ tách thành tích các tích phân: 
>
>
>
> \[ ∫ 1/(√(2πλ1) exp {-y1²/λ1} y dy1 \] \[∫1/(√(2πλ2) exp {-yD²/λD} dy2\] ...\[∫ 1/(√(2πλi)exp {-yi²/λi} yi dyi\]... \[ ∫ 1/(√(2πλj) exp {-yj²/λj} yj dyj \]...
>
>
>
> Và trong cái tích này, hai cái tích phân ∫ 1/(√(2πλi) exp {-yi²/λi} yi dyi, và ∫ 1/(√(2πλj) exp {-yj²/λj} yj dyj đều là tích phân của hàm lẽ trên toàn miền, nên đều = 0, hoặc có thể nhìn ra nó đều là mean E(Yi) của Yi \~ normal(0, λi) và E(Yj) của normal(0, λj). Còn những cụm khác đều có dạng của tích phân hàm normal(0, λi) trên toàn miền, nên đều bằng 1. Nhưng dù sao, thì vì có thừa số - 0, nên cả cái tích này bằng: 1\*1\*...\*0\*0\*1\*1 = 0.
>
>
>
> Còn nếu i = j, thì nó sẽ trở thành 1\*1\*...\*\[∫ 1/(√(2πλi) exp {-yi²/λi} (yi²)dyi\]\*1\*...\*1
>
>
>
> = ∫ 1/(√(2πλi) exp {-yi²/λi} yi² dyi
>
>
>
> và đây chính là có dạng của việc tính ∫yi² f(yi)dx với f(yi) là pdf của normal(0, λi). Nên kết quả chính là second moement, E\[Yi²\] với Yi\~ Normal(0, λj). Mà ta biết VarX (=λi) = EYi² - (EYi)² ⇨ EYi² = VarYi + (EYi)² = λi + 0 = λi. Nên kết quả tích phân này là bằng λi.
>
>
>
>  Như vậy, quay lại đây, ta thấy khi xét cụm Σi=1:D Σj=1:D 𝐮i 𝐮jᵀ ∫ \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] exp {-\[Σk (yk²/λk)\] } yi yj d𝐲, thì bản chất của nó là một cái tổng lớn, mà khi i khác j thì cái tích phân = 0, nên hạng tử cũng bằng 0. Còn i = j thì tích phân bằng λi.
>
>
>
> Do đó, cái tổng này chỉ còn lại:
>
>
>
> Σi=1:D 𝐮i 𝐮iᵀ λi
>
>
>
> Và, má ơi, đây chính là gì, chính là Σ, mà ta đã phân tích ở 2.48 hoặc cũng phân tích lại ở đầu cái note này.
>
>
>
> Như vậy cái term 1, \[1/(2π)^(D/2)\] \[1/|Σ|^(1/2)\] ∫ **zz**ᵀ exp {-(1/2)𝐳ᵀ Σ⁻¹ 𝐳} d𝐳 = Σ.
>
>
>
> Và như vậy ta đã hiểu hết toàn bộ bước chứng minh E\[**XX**ᵀ\] với 𝐗 \~ Normal(**μ**, Σ) chính là = Σ + **μμ**ᵀ
>
>
>
> ---
>
>
>
> (Ôn lại phần chiếu Gramd Smith với orthogonal basis giúp giải thích vì sao 𝐚 = Σi=1:n (𝐚iᵀ**q**i) **q**i:
>
>
>
> Ta có vector 𝐚 và muốn thể hiện nó trong orthogonal basis **q**'s: 𝐚 = a1 **q**1 + a2 **q**2 + .. an **q**n.
>
>
>
> Đầu tiên, chiếu 𝐚 lên **q**1. gọi 𝐩1 là hình chiếu của a lên **q**1, cũng chính là nói 𝐩1 ∈ span {**q**1}: p1 = α**q**1. Và phần dư 𝐫1 = 𝐚 - 𝐩1 = 𝐚 - α**q**1 sẽ vuông góc với span {**q**1}, và do đó, nó nằm trong orthogonal complement của span {**q**1}
>
>
>
> ⇨ 𝐫1T**q**1 = 0 ⇔ (𝐚 - α**q**1)ᵀ**q**1 = 0 ⇔ 𝐚ᵀ**q**1 = α**q**1T**q**1 ⇔ 𝐚ᵀ**q**1/**q**1T**q**1 = α ⇔ 𝐚ᵀ**q**1/1 (do q1 là unit vector → q1Tq1 = ||q1||² = 1) = 𝐚ᵀ**q**1. Vậy α = 𝐚ᵀ**q**1. Nên a = 𝐩1 + 𝐫1 = α**q**1 + 𝐫1 = (𝐚ᵀ**q**1) **q**1 + 𝐫1.
>
>
>
> Tiếp theo, xét 𝐫1, nó nằm trong orthogonal complent của span {**q**1}, cũng chính là span {**q**2,..**q**n}, ta sẽ chiếu tách nó thành 𝐩2 là hình chiếu của 𝐫1 lên span {**q**2} và phần dư 𝐫2 = 𝐫1 - 𝐩2.
>
>
>
> Tương tự, 𝐩2 ∈ span {**q**2} nên 𝐩2 = β **q**2 phần dư 𝐫2 sẽ orthogonal với **q**2: (𝐫1 - 𝐩2)ᵀ**q**2 = 0 ⇔ 𝐫1T**q**2 = 𝐩2T**q**2 ⇔ 𝐫1T**q**2 = β **q**2T**q**2 ⇔ 𝐫1T**q**2 = β (do q2 unit vector. ||**q**2|| = 1) Vậy β = 𝐫1T**q**2 = (𝐚 - 𝐩1)ᵀ**q**2 = (𝐚 - α**q**1)ᵀ**q**2 = 𝐚ᵀ**q**2 - α**q**1T**q**2, và cái này thì bằng 𝐚ᵀ**q**2 do q1,q2 vuông góc (bởi đã nói q1,..qn là bộ orthogonal basis). Vậy β = 𝐚ᵀ**q**2.
>
>
>
> Nên đến đây ta đã có 𝐚 = α**q**1 + 𝐫1 = α**q**1 + β**q**2 + 𝐫2 = (𝐚ᵀ**q**1) **q**1 + (aᵀ**q**2) **q**2 + 𝐫2 với cái đầu là hình chiếu của 𝐚 lên **q**1, cái sau là hình chiếu của phần dư 𝐫1 lên **q**2, nhưng vì bộ orthogonal basis, nên nó cũng đồng thời chính là hình chiếu của 𝐚 lên **q**2.
>
>
>
> Và tiếp tục như vậy ta sẽ thấy kết quả là: a sẽ tách thành Σi=1:n (𝐚iᵀ**q**i) **q**i
>
>
>
> Và đây là điều chỉ có được nếu ta dùng một orthogonal basis.)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **99/100**
>
> Bài giải thích này rất chi tiết, chính xác và có chiều sâu, giải thích cặn kẽ từng bước và liên kết tốt các khái niệm trong bài đọc. Cách bạn đi sâu vào cả những kiến thức nền tảng như eigendecomposition và tính đối xứng là rất ấn tượng.

<br>

<a id="node-gig7x9a"></a>

###### Ma trận hiệp phương sai Σ

<p align="center"><kbd><img src="assets/h92028te82g.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, tới đây ta đã có E\[**XX**ᵀ\] = **μμ**ᵀ + Σ
>
>
>
> Thế thì dừng lại chút, để nhớ rằng thứ ta đang cố gắng tính, E\[**XX**ᵀ\], là matrix các second moment của 𝐗, là random vector \~ Normal (**μ**, Σ).
>
>
>
> Vậy thì ta còn nhớ, với single random variable X, khi học về variance Var(X), thì công thức đầu tiên được học là VarX = E\[(X - EX)²\], thì nếu nhìn kĩ vào đây, ta sẽ thấy nó chính là việc đặt một biến Z = X - EX, và lấy second moment của nó: E\[Z²\], cho nên đây là ý của gs Bishop khi nói "subtracted the mean before taking second mo-ments in order to define a variance".
>
>
>
> Thế thì với với random variable vector 𝐗, ta cũng làm tương tự: trừ đi mean: E\[𝐗\], và lấy second moment, mà second moment đối với random variable vector thì như đã nói, sẽ là một matrix, (ví dụ second moment của 𝐗 là matrix E\[**XX**ᵀ\]), nên second moment của 𝐗 - E𝐗 là E\[(𝐗 - E𝐗)(X - E𝐗)ᵀ\], và cái này **được gọi là covariance** của 𝐗.
>
>
>
> Dừng lại chút xíu để suy ngẫm rằng: Có thể thấy đây là một cách dẫn dắt khiến mình thấy hơi lạ. Trong Stat110 hay Casella, mình chưa từng được nghe về second moment của một random variable vector, nhưng đã được học về khái niệm covariance giữa hai random variable: Cov(X,Y) được define bởi E\[(X-EX)(Y-EY)\]. Tuy nhiên, mình nhớ là gs Joe trong Stat110 hay trong sách Casella cũng không nói đến covariance matrix, để rồi mình chỉ hiểu một cách đại khái là, với random variable vector 𝐗, là vector tạo bởi các random variable X1,...Xn, thì covariance matrix là matrix mà các phần tử sẽ là covariance của các cặp random variable Xi, Xj mà thôi. Hiểu vậy thì vẫn đúng. Nhưng ý muốn nói ở đây là, với đoạn này của sách Bishop, mình nhận ra ông đang cho ta biết về định nghĩa của **covariance của một random vector**, đó là: Covariance của vector X được define là second moment của vector 𝐗 - E𝐗, và với second moment của vector 𝐔, được define bởi E\[**UU**ᵀ\] thì covariance của vector 𝐗 sẽ là E\[(𝐗-E𝐗)(𝐗-E𝐗)ᵀ\]. Như vậy từ nay khi nói về covariance matrix, mình sẽ hiểu thêm một tầng, đó là nó chính là **second moment của** (𝐗 - E𝐗).
>
>
>
> Tiếp, gs nói tiếp, vì đang xét 𝐗 \~ Normal(**μ**, Σ), mà ở trên ta đã chứng minh E𝐗 = **μ.** Nên covariance của 𝐗:
>
>
>
> cov(𝐗) = E\[(𝐗 - **μ**)(𝐗 - **μ**)ᵀ\]
>
>
>
> Triển khai ra: E\[(𝐗 - **μ**)(𝐗 - **μ**)ᵀ\] = E\[(𝐗 - **μ**)(𝐗ᵀ - **μ**ᵀ)\] = E\[**XX**ᵀ - **μX**ᵀ - **Xμ**ᵀ + **μμ**ᵀ\]
>
>
>
> = E\[**XX**ᵀ\] - E\[**μX**ᵀ\] - E\[**Xμ**ᵀ\] + E\[**μμ**ᵀ\]
>
>
>
> = E\[**XX**ᵀ\] - E\[**μX**ᵀ\] - E\[**Xμ**ᵀ\] + E\[**μμ**ᵀ\]
>
>
>
> = E\[**XX**ᵀ\] - **μ**E\[𝐗ᵀ\] - E\[𝐗\]**μ**ᵀ + E\[**μμ**ᵀ\]  (dùng tính linearity E\[**μX**ᵀ\] = **μ**E\[𝐗ᵀ\], E\[**Xμ**ᵀ\] = E\[𝐗\]**μ**ᵀ)
>
>
>
> = E\[**XX**ᵀ\] - **μ**(E\[𝐗\]ᵀ) - **μμ**ᵀ + **μμ**ᵀ  (**μμ**ᵀ là constant ⇨ E\[**μμ**ᵀ\] = **μμ**ᵀ)
>
>
>
> = E\[**XX**ᵀ\] - **μ**(**μ**ᵀ) - **μμ**ᵀ + **μμ**ᵀ
>
>
>
> = E\[**XX**ᵀ\] - **μμ**ᵀ
>
>
>
> Vậy Cov(𝐗) = E\[**XX**ᵀ\] - **μμ**ᵀ, mà kết quả 2.62 cho ta E\[**XX**ᵀ\] = **μμ**ᵀ + Σ
>
>
>
> ⇨ Cov(𝐗) = **μμ**ᵀ + Σ - **μμ**ᵀ = Σ
>
>
>
> Như vậy là ta đã chứng minh rằng: **COVARIANCE** CỦA RANDOM VECTOR 𝐗, có định nghĩa là second moment của (𝐗 - E𝐗), và với việc X \~ Normal(**μ**, Σ), THÌ NÓ CHÍNH LÀ Σ. 
>
>
>
> Và từ đây ta mới hiểu sâu hơn là vì sao khi nói về pdf của Normal(μ, Σ) thì Σ lại được gọi là **COVARIANCE MATRIX.**

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Bài phân tích rất xuất sắc, vừa chính xác từng chi tiết vừa thể hiện sự đào sâu và kết nối kiến thức một cách sâu sắc. Cách bạn suy ngẫm và liên hệ với các nguồn khác cho thấy sự hiểu biết toàn diện về khái niệm ma trận hiệp phương sai.

<br>

<a id="node-35ylf7v"></a>

###### Ma trận hiệp phương sai Normal

<p align="center"><kbd><img src="assets/di2wfqqwwxg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/5nu5ybt8d8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/bvl3can0ar.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, gs nói về nhược điểm của phân phối (multivariate) Normal: Nói ngắn gọn là tốn quá nhiều parameter, cụ thể là với D-dimension, thì ta có D parameters của **μ** và D(D+1)/2 là số parameter của Σ (ko phải DxD là vì Σ là matrix đối xứng). Như vậy tổng cộng là D(D+3)/2, tức là với D lớn, số params cũng như chi phí tính toán sẽ tăng theo O(D²).
>
>
>
> Để khắc phục, người ta có thể đưa vào vài ràng buộc với Σ, đánh đổi việc sẽ làm hạn chế bớt khả năng biểu diễn các pattern trong data để đổi lấy việc giảm chi phí tính toán (tính toán nhanh hơn). Trong đó một cách là dùng Σ chỉ có dạng diagonal, dĩ nhiên khi đó số param chỉ là D, khiến tổng cộng chỉ là 2D.
>
>
>
> Hoặc là dùng Σ có dạng αI, có nghĩa là chỉ tốn một param cho Σ, để tổng cộng là D+1 params, và case này gọi là isotropic covariance.
>
>
>
> Thế thì thử giải thích vì sao có 3 hình dạng khác nhau trong hình a, b, c.
>
>
>
> Với hình a, là Σ bình thường. Thì note trước mình đã hiểu, với một level set của hàm pdf, sẽ tương ứng với level set của hàm exponent: exp\[-(1/2)(𝐱-**μ**)ᵀ Σ⁻¹(𝐱-**μ**)\] = c thì nó sẽ có dạng là một đường ellipse có tâm tại **μ**, và các trục trùng với eigenvector 𝐮i của Σ, và độ dài bán trục là cλ1/2, cλ2/2
>
>
>
> Thế thì nếu Σ trở thành diagonal matrix diag(σ1, σ2...) thì sao? Hay vì sao các hình ellipse trở nên thẳng góc với các trục xi?
>
>
>
> Rất đơn giản nếu như ta đã hiểu trục của ellipse là các eigenvector của Σ, thì **khi Σ là diag(σ1, σ2,...) thì eigenvector của nó là gì**? → Nó **chính là các basis vector** 𝐞1,𝐞2,....Vì sao:
>
>
>
> Là vì **với diagonal matrix, eigenvector của nó chính là nằm trên đường chéo**: Nên λ1, λ2,...cũng chính là σ1, σ2,....
>
>
>
> Nếu gọi **u1** là eigenvector của Σ ứng với eigenvector λ1, ta có:
>
>
>
> Σ **u1** = λ1 **u1** ⇔ diag(σ1, σ2,...) **u1** = λ1 **u1**
>
>
>
> Xét vế trái, dễ thấy nó sẽ là vector (λ1 **u1**1, λ2 **u1**2,...). còn vế phải là vector (λ1 **u1**1, λ1 **u1**2,...). Nên ta có hệ phương trình: λ1 **u1**1 = λ1 u**1**1, λ2 **u1**2 = λ1 **u1**2, ...,λD **u1**D = λ1 **u1**D,.... và cái này suy ra **u1**1 = 1, u12 = u13 = ...= 0, nói cách khác **u1** chính là **e1** = \[1,0,0,..0\] 
>
>
>
> Tương tự, **u2** chính là **e2**
>
>
>
> Như vậy cái eigenvector của diagoal(σ1,...σD) chính là các trục ban đầu (basis 𝐞's) thành ra các ellipse thẳng trục như hình b.
>
>
>
> Còn hình c), là khi Σ = αI, khi đó đơn giản là **mọi eigenvalue đều bằng nhau** và bằng α, nên các ellipse có **độ dài bán trục bằng nhau, nên thành hình tròn** hết (với D &gt; 2 thì các level set là các mặt cầu, spherical surface)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bài ghi chú của bạn thể hiện sự hiểu biết sâu sắc và chính xác về các hạn chế của phân phối Gaussian cùng với các giải pháp khắc phục, đặc biệt là phần giải thích chi tiết về hình dạng các đường đồng mức dựa trên cấu trúc ma trận hiệp phương sai. Đây là một phân tích rất đầy đủ và có chiều sâu, vượt xa nội dung bề mặt trong tài liệu gốc.

<br>

<a id="node-56jy7fs"></a>

###### Phân phối Gaussian và biến ẩn

<p align="center"><kbd><img src="assets/nuj3d99mpwt.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi đại khái là phần cuối cùng này nói về một cái nhược điểm, một cái hạn chế nữa của cái phân phối Gaussian, phân phối normal đó. Đó là về cơ bản nó **về mặt nội tại của nó là một cái phân phối gọi là unimodal**. Có nghĩa là nó chỉ có một cái đỉnh thôi. Chính vì vậy nó không thể mô hình hóa được, không thể xấp xỉ hóa được những cái distribution trong tự nhiên mà vốn nó có nhiều đỉnh, nó gọi là multi-modal distribution. Do đó về mặt mình có thể hiểu nôm na là cái normal distribution nó **vừa quá flexible, nếu như mình xét ở khía cạnh nó quá nhiều parameters**, quá nhiều tham số. Nhưng nó cũng lại quá có **cái tính chất là không đủ flexible** khi mà xét ở khía cạnh nó chỉ là một cái **unimodal** **distribution**. 
>
>
>
> Thành thử ra là nó có cái hạn chế ở chỗ đó. 
>
>
>
> Đồng thời, những cái chương sau mình sẽ học rằng là bằng cách giới thiệu những cái đưa vào những cái **biến ẩn** gọi là **latent variable** hoặc gọi là **hidden variable** thì người ta **có thể khắc phục được chuyện này**. Và nó sẽ dẫn đến một số những cái mô hình, ví dụ như gọi là **Markov random field**, là một cái mô hình mà trong đó người ta đưa vào thêm một cái biến ẩn thuộc dạng rời rạc discrete. Cũng như là **linear dynamical system**. 
>
>
>
> Nói chung là đây là những cái mà trong những cái chương sau mình sẽ học và trong chương 8 mình sẽ học một cái rất là mạnh, một cái cách kết hợp của những cái dạng này, nó gọi là probabilistic graphical model.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Phần tóm tắt đã nắm bắt rất tốt các hạn chế của phân phối Gaussian và các giải pháp sử dụng biến ẩn cùng các ví dụ liên quan. Để đạt độ chính xác cao hơn, bạn có thể bổ sung chi tiết về mô hình hỗn hợp Gaussian khi nói về biến ẩn rời rạc.

<br>

