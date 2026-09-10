# 3.1.2 Geometry of least squares

📊 **Progress:** `1` Notes | `2` Screenshots | `1` AI Reviews

---
<a id="node-6e545fx"></a>

<p align="center"><kbd><img src="assets/o8a5bu6pa0d.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hl5espm95c5.png" width="80%"></kbd></p>

> [!NOTE]
> Qua góc nhìn hình học, phần lớn đều đã hiểu (trong mấy note trước đã có nói rồi).
>
>
>
> Đầu tiên, xét vector 𝐭 = (t1,....tN), tức là tất cả target observation, sẽ là vector trong N-dimensional sapce.
>
>
>
> Thế thì hàm basis Φj() j = 0,1,...M. Ta còn nhớ là gì không? → là hàm dùng để tạo "tính chất phi tuyến", khiến cho mô hình y(𝐰, 𝐱) = w0 Φ0(𝐱) + w1 Φ1(𝐱) + .. wM-1 ΦM-1(𝐱) trở thành hàm phi tuyến theo 𝐱, (và vẫn tuyến tính theo 𝐰). Và nếu gom Φ1(𝐱1), Φ1(𝐱2),...Φ1(𝐱N), thành vector **Φ**1 thì dĩ nhiên vẫn là một N-dimensional vector, nên nó cũng nằm trong vector space với vector 𝐭 ở trên.
>
>
>
> (nói thêm chút, còn nhớ, ta define matrix **Φ**, chính là matrix có các hàng, là vector **Φ**(𝐱i) = \[Φ0(𝐱i), Φ1(𝐱i), Φ2(𝐱i),...ΦM-1(𝐱i)\]. Nên vector **Φ**1 nói trên là cột 1 của matrix này. Tóm lại, các cột của design matrix **Φ** là các cột **Φ**0, **Φ**1,...**Φ**M-1. Với **Φ**j = \[Φj(𝐱1), Φj(𝐱2),...Φj(𝐱N)\]ᵀ. Còn các hàng là vector Φ(𝐱i) = \[Φ0(𝐱i), Φ2(𝐱i),...ΦM-1(𝐱i))
>
>
>
> Thế thì, như vậy ta có M cột của design matrix, là các R^N vector **Φ**0, **Φ**1,...**Φ**M-1. Theo MIT 1806 đã học, với M vector thì trong trường hợp chúng đậc lập thì cùng lắm chỉ tạo một basis của một M-dimensional subspace của R^N thôi, cũng là nói chúng cùng lắm là chỉ span được một M-D subspace của R^N thôi. Nhưng nếu không độc lập, thì thậm chí dimension của span {**Φ**0, **Φ**1,...**Φ**M-1} còn nhỏ hơn M. Trong sách gs gọi subspace này là S. (dù ông nói nó có dimensionality là M, nhưng nhờ MIT 1806, mình hiểu điều này chỉ xảy ra khi **Φ**0, **Φ**1, **Φ**2,...**Φ**M-1 linearly independent như nói trên)
>
>
>
> Rồi, tiếp theo ta đặt vector 𝐲 = \[y(𝐱1, 𝐰), y(𝐱2, 𝐰),...y(𝐱N, 𝐰)\]ᵀ, đương nhiên, nó cũng là một N-dimensinal vector, cũng nằm trong R^N. Tuy nhiên, ta còn có thể thấy rằng:
>
>
>
> y(𝐱1, 𝐰) = 𝐰ᵀ**Φ**(𝐱1), y(𝐱2, 𝐰) = 𝐰ᵀ**Φ**(𝐱2),..
>
>
>
> nên với việc đặt design matrix **Φ** là matrix có các hàng là **Φ**(𝐱1), **Φ**(𝐱2),..như trên đã nói thì ta sẽ có thể thấy theo góc nhìn thứ nhất nhân matrix với vector được học trong MIT 1806 nói rằng Ax = b thì phần tử bi là dot product của hàng i của A và vector x, từ đó ta thấy 𝐲 = **Φw**. Và từ đó, tiếp tục dùng góc nhìn thứ hai của việc nhân matrix với vector: Ax là linear combination các cột của A bởi hệ số là phần tử của x, thì ta lại thấy y chính là linear combination các cột **Φ**0, **Φ**1,...**Φ**M-1, bởi bộ hệ số là w0, w1, ...wM-1. Và điều này, theo định nghĩa của linear combination, sẽ có nghĩa là 𝐲 phải nằm trong column space của **Φ**, là cái subspace span bởi **Φ**0, **Φ**1,...**Φ**M-1, chính là S ở trên (nên gs Bishop nới nói y có thể nằm anywhere trên M-dimensional subspace S này)
>
>
>
> Vậy thì sum of square error có công thức là = Σi \[ti - y(𝐰, 𝐱i)\]², dễ thấy với việc có vector 𝐭 và vector 𝐲, thì đây chính là ||𝐭 - 𝐲||², là squared L2 norm, cũng còn chính là bình phương Euclidean distance giữa 𝐭 và 𝐲.
>
>
>
> Từ đó góc nhìn hình học này giúp ta nhìn nhận việc muốn đi giảm thiểu cái sum of squared error chính là muốn đi minimize cái L2 distance giữa 𝐭 và 𝐲.
>
>
>
> Thế thì, vấn đề là 𝐲 = **Φw**, là vector nằm đâu đó trong C(**Φ**) = S = span{**Φ**0,..**Φ**M-1}, và với các giá trị w khác nhau thì ta có có vector 𝐲 chạy vòng vòng trong cái subspace này. Trong khi đó 𝐭 thì sao? nó là R^N vector, là cái vector space mẹ, chứa cái subspace S, vì đang nói M < N, nên S không thể lấp đầy R^N này. Thành ra sẽ có hai trường hợp: **t nằm trong S** **hoặc không**. Do đó cái bài toán này chính là: tìm điểm nằm trong S sao cho gần với t nhất. Nói tìm điểm thực chất là tìm bộ hệ số w0,...wM-1 để dùng nó làm linear combination các cột của **Φ**, giúp ta có 𝐲 = **Φw** gần với 𝐭 nhất. Và đây chính là đi tìm hình chiếu của 𝐭 lên C(**Φ**), hay S.
>
>
>
> Nói thêm, dĩ nhiên nếu hên, 𝐭 nằm sẵn trong S, thì hình chiếu của 𝐭 lên S là chính nó, khi đó việc minimize ||𝐭 - 𝐲||² sẽ có thể giảm cái này về 0, và solution đơn giản chỉ là nghiệm của **Φw** = 𝐭.
>
>
>
> Còn nếu 𝐭 không nằm trong S, thì cái không thể giảm ||𝐭 - 𝐲||² về 0 được, mà giá trị nhỏ nhất chỉ là phần dư residual ||𝐭 - 𝐩||² với 𝐩 là hình chiếu của 𝐭 lên S. Solution của bài toán lúc này là nghiệm của **Φw** = 𝐩.
>
>
>
> Như mấy bữa đã từng nói rồi, dùng đặc điểm là phần dư 𝐫 = 𝐭 - 𝐩 vuông góc với S, hay C(**Φ**), thì điều này có nghĩa r thuộc cái subspace mà complement orthogonal với C(**Φ**), chính là left nullspace: N(**Φ**ᵀ) (trong MIᵀ 1806 đã học có 2 cặp subspace orthogonal complement là column space C(A) với left nullspace N(Aᵀ), và row space C(Aᵀ) với nullspace N(A)), từ đó ta có **Φ**ᵀ𝐫 = 0 ⇔ **Φ**ᵀ(𝐭 - 𝐩) = 0 ⇔ **Φ**ᵀ𝐭 = **Φ**ᵀ𝐩. Tới đây ta thay **Φw** = 𝐩 vào thì có **Φ**ᵀ𝐭 = **Φ**ᵀ**Φw**, chính là normal equation. Để rồi nếu **Φ** full column rank (cũng là các cột Φ0,...ΦM-1 của chúng độc lập, cũng là dimension của S là M) thì khi đó **Φ**ᵀ**Φ** full rank, ta có thể có 𝐰 = (**Φ**ᵀ**Φ**)^-1 **Φ**ᵀ𝐭. Và còn nhớ cái này **chính là** 𝐰ML, nơi ta giải phương trình gradient của hàm ln likelihood = 0 bữa trước.
>
>
>
> Chú ý là dù trong case t ∈ S để w là solution của **Φw** = **t, thì ta vẫn có thể nhân hai vế cho Φ**^(+), để có w = **Φ**^(+)𝐭 (chỉ là trong case này residual r = 0)
>
>
>
> Vậy thì ở đây gs Bishop nói đại ý là ta có thể "xác nhận" điều này (tức là **xác nhận việc giải bài toán minimize sum squared error chính là bài toán projection**) bằng cách lôi cái solution ra: 𝐰ML, để thấy nó chính là solution của bài toán tìm 𝐰 giúp ta có được p là hình chiếu của 𝐭 lên S.
>
>
>
> Và cái này thì mình đã xác nhận bên trên rồi, khi solution của bài toán projection là 𝐰 = (**Φ**ᵀ**Φ**)^-1 **Φ**ᵀ𝐭 có được **bằng cách lập luận đại số tuyến tính**, thì **cũng chính là wML có được bằng cách giải điều kiện tối ưu bậc nhất** - cho gradient của hàm log likelihood bằng 0 bữa trước đó.
>
>
>
> Đoạn cuối, ông nói đại khái là việc giải nghiệm trực tiếp có thể gặp khó khăn khi **Φ**ᵀ**Φ** gần singular. Là sao?
>
>
>
> → Cũng dễ hiểu, vì cái công thức 𝐰 = (**Φ**ᵀ**Φ**)^-1 **Φ**ᵀ**t, như đã nói trên, yêu cầu Φ**ᵀ**Φ** phải full rank / non-singular / invertible. Nên nếu **Φ**ᵀ**Φ** không invertible thì dĩ nhiên ko thể dùng công thức này.
>
>
>
> Hơn nữa, nhờ đọc Nocedal mình cũng được biết, giả sử ngay cả khi **Φ**ᵀ**Φ** invertible thì việc tính ra w cũng không phải là ta đi tính **Φ**ᵀ**Φ**, rồi tính inverse của nó (**Φ**ᵀ**Φ**)⁻¹, sau đó nhân với **Φ**ᵀ𝐭. Vì làm vậy rất tốn kém.
>
>
>
> Thay vào đó, thật ra là ta sẽ giải normal equation **Φ**ᵀ**Φw** = **Φ**ᵀ𝐭 theo các cách khác: Cái này chính là trong chap 10 của Numerical Optimization của J. Nocedal, nói rằng, nếu bài toán không quá lớn (large scale), ta có thể dùng các direct algorithm, dựa trên đại số tuyến tính, như các phương pháp dựa trên Cholesky factored, QR factoed, SVD, mỗi cái có ưu nhược điểm khác nhau. Còn nếu bài toán quy mô lớn, thì phải dùng trùm cuối - thuật toán Conjugate Gradient.
>
>
>
> Vậy thì ở đoạn này mình nhận ra chính là gs Bishop nói đến trường hợp đó, khi **Φ**ᵀ**Φ** gần singular, tức tồn tại các eigenvector rất nhỏ ≈ 0, sẽ khiến không thể giải bằng Cholesky factor based method được. Khi đó ta có thể giải bằng thuật toán dựa trên SVD
>
>
>
> (có nghĩa là gs Bishop ko nhắc đến, nhưng nhờ học Nocedal, nên mình biết chính xác ông nói SVD, ngoài ra còn biết về QR factor và conjugate gradient nữa)
>
>
>
> Và cũng nhờ MIT 1806 nên mình cũng hiểu đoạn ông Bishop nói vì sao có khi **Φ**ᵀ**Φ** gần singular. Đại khái là, như đã nói trên rằng khi các cột của **Φ**, độc lập, thì **Φ**ᵀ**Φ** sẽ full rank / invertivle / non-singular. Vậy thì ngược lại, nếu chúng phụ thuộc thì **Φ**ᵀ**Φ** sẽ singular. mà cột phụ thuộc là sao → tức là có thể xảy ra tình trạng có cột **Φ**i nào đó **CÓ THỂ ĐƯỢC TẠO RA BỞI MẤY CỘT KHÁC**, ví dụ **Φ**1 = 5**Φ**2, hoặc Φ1 = **Φ**2 + 3**Φ**5. Ví dụ như **Φ**1 = 5**Φ**2, thì trên không gian R^N, hai vector trùng nhau. Lúc này matrix Φ tồn tại nullspace vector khác 0, và cũng chính là tồn tại eigenvalue = 0.
>
>
>
> Vậy thì gần singular là sao? → Thì là khi ví dụ như Φ1 không bằng α Φ2 nhưng cũng rất gần bằng α Φ2, dẫn đến trong không gian, hai vector gần như trùng phương. Và eigenvalue gần bằng 0. Đó chính ý nghĩa của từ co-linear.
>
>
>
> Và gs nói hiện tượng này cũng ko phải là ít xảy ra trong các dataset thực, cũng như việc có thêm các regularization term sẽ đảm bảo ko thể xảy ra hiện tượng này

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Phân tích cực kỳ sâu sắc và chi tiết, không chỉ nắm vững nội dung bài đọc mà còn mở rộng kiến thức từ đại số tuyến tính (MIT 1806) và tối ưu hóa số (Nocedal) để làm rõ từng khái niệm. Khả năng liên kết các ý tưởng phức tạp, đặc biệt là về phương trình chuẩn và các vấn đề tính toán liên quan đến ma trận gần suy biến, là rất ấn tượng và mang lại giá trị gia tăng đáng kể. 

**🔗 See also:** [Ex 3.2 Orthogonal Projection and Least Squares](./37_exercises.md#node-2dv7p1f)

<br>

