# 4.1.6 Fisher’s discriminant for multiple classes

📊 **Progress:** `2` Notes | `4` Screenshots | `1` AI Reviews

---
<a id="node-rb2zf3j"></a>

<br>

<a id="node-1sx9maq"></a>

## Fisher's Discriminant for Multiple Classes

<p align="center"><kbd><img src="assets/2vs3ay99i09.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/m6epjxi718.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/9s120hmz6yu.png" width="80%"></kbd></p>

> [!NOTE]
> Xem nào, đại ý ở đây là ta khái quát hóa Fisher's discriminant lên cho bài toán nhiều class hơn
>
>
>
> Giả sử số chiều dữ liệu gốc là D, và gọi D' là số "feature tuyến tính": yk = 𝐰kᵀ𝐱, k=1,...D' tức là sao? Tức là tương tự như khi ta chiếu (!) 𝐱 từ D chiều lên span {𝐰}, bằng cách tính y = 𝐰ᵀ𝐱, mang ý nghĩa là giảm chiều dữ liệu từ D còn thành 1 chiều, và đây là feature tuyến tính vì y là hàm tuyến tính đối với 𝐱 đơn giản vậy thôi (nhưng gợi ý ta rằng vài bữa ta sẽ có các feature phi tuyến?), thì ở đây, ta sẽ dùng D' vector: 𝐰1,...𝐰D', để chiếu data lên, tạo ra D' feature tuyến tính y1=𝐰1ᵀ𝐱,...,yD' = 𝐰D'ᵀ𝐱, gom lại thành vector D' chiều: 𝐲. Như vậy mang ý nghĩa, là, từ dữ liệu D chiều ban đầu, ta nén còn D' chiều..
>
>
>
> Và thể hiện compact bằng cách đặt các 𝐰1,.., 𝐰D' thành các cột của 𝐖. Khi đó 𝐲 = 𝐖ᵀ𝐱, cái này dễ hiểu (vì phần tử yj sẽ là dot product của hàng j của 𝐖ᵀ, cũng là cột j của 𝐖, chính là 𝐰j với 𝐱: yj = 𝐰jᵀ𝐱)
>
>
>
> ---
>
>
>
> (!) Chú ý, **nói là chiếu nhưng nên hiểu là linear mapping từ R^D sang R^D'** nhưng **không phải là chiếu vuông góc (orthogonal projection) như trong trực giác hình học của bài toán least square.**
>
>
>
> ---
>
>
>
> Tiếp, với hai class bữa trước, thì 𝐒1 = Σi∈𝒞1 (𝐱i - 𝐦1)(𝐱i - 𝐦1)ᵀ, 𝐒2 = Σi∈𝒞2 (𝐱i - 𝐦2)(𝐱i - 𝐦2)ᵀ
>
>
>
> thì nay khái quát của within-class covariance matrix cho case K class là:
>
>
>
> 𝐒w = Σk=1:K 𝐒k với 𝐒k = Σi∈𝒞k (𝐱i - 𝐦k)(𝐱i - 𝐦k)ᵀ và 𝐦k = (1/Nk) Σi∈𝒞k 𝐱i.
>
>
>
> Nhân tiện có thể thắc mắc vì sao đây lại là công thức của (within class) covariance matrix? hay, vì sao có công thức covariance matrix như vậy.
>
>
>
> Theo định nghĩa, nếu ta có random vector 𝐗, 𝐘 thì Cov(𝐗,𝐘) = E\[(𝐗-E(𝐗))(𝐘-E(𝐘))ᵀ\],
>
>
>
> (𝐗-E(𝐗))(𝐘-E(𝐘))ᵀ là random matrix có phần từ ij (Xi - E(Xi)) × (Yj - E(Yj))
>
>
>
> nên phần tử ij của Cov(𝐗, 𝐘) = E\[(Xi - E(Xi)) × (Yj - E(Yj))\]
>
>
>
> Cov(𝐗, 𝐗), ta viết gọn là Cov(𝐗) = E\[(𝐗-E(𝐗))(𝐗-E(𝐗))ᵀ\], thì phần tử ij là E\[(Xi - E(Xi))(Xj - E(Xj))\]
>
>
>
> Thế thì, để tính kì vọng, ta phải biết distribution: các possible value, và xác suất
>
>
>
> Vậy ta lập luận là: 𝐱1, ...𝐱N là các possible value của discrete uniform 𝐗, tức P(𝐗 = 𝐱1) = ...= P(𝐗 = 𝐱N) = 1/N
>
>
>
> E\[𝐗\] sẽ bằng: 𝐱1 × P(𝐗=𝐱1) + ...+ 𝐱N × P(𝐗=𝐱N) (định nghĩa kì vọng của discrete rv)
>
>
>
> = 𝐱1/N + ...+ 𝐱N/N = (Σi 𝐱i)/N, đặt là 𝐦 (sample mean)
>
>
>
> thì Cov(𝐗) = E\[(𝐗-E(𝐗))(𝐗-E(𝐗))ᵀ\] = (𝐱1-E(𝐗))(𝐱1-E(𝐗))ᵀ × P(𝐗=𝐱1) + ...+ (𝐱N-E(𝐗))(𝐱N-E(𝐗))ᵀ × P(𝐗=𝐱N)
>
>
>
> = (1/N) \[(𝐱1-E(𝐗))(𝐱1-E(𝐗))ᵀ + ...+ (𝐱N-E(𝐗))(𝐱N-E(𝐗))ᵀ\]
>
>
>
> = (1/N) \[(𝐱1-𝐦)(𝐱1-𝐦)ᵀ + ...+ (𝐱N-𝐦)(𝐱N-𝐦)ᵀ\]
>
>
>
> = (1/N) Σi (𝐱i-𝐦)(𝐱i-𝐦)ᵀ
>
>
>
> Bỏ 1/N đi, ta sẽ được cái gọi là scatter matrix, ta có Σi (𝐱i-𝐦)(𝐱i-𝐦)ᵀ. và những chỗ mà mr Bishop nói within-class hay between-class covariance matrix, thực chất không phải là covariance matrix mà là scatter matrix 
>
>
>
> Như vậy, đây đại ý là công thức covariance matrix khi ta coi như 𝐗, vốn chưa biết distribution nó thế nào, để mà tính E\[(𝐗-E(𝐗))(𝐗-E(𝐗))ᵀ\], ta coi nó như uniform discrete có các possible value 𝐱1,...𝐱N, rồi để tính với distribution này, gọi là **emprical distribution**.
>
>
>
> ---
>
>
>
> Tiếp, ta đặt 𝐒T, là total covariance matrix thì biến đổi đại số ta có thể tách 𝐒T thành 𝐒W + 𝐒B với 𝐒B theo công thức 𝐒B = Σk Nk(𝐦k - 𝐦)(𝐦k - 𝐦)ᵀ (4.46) (cái này chỉ là biến đổi đại số, **dài dòng nhưng không khó**, cứ tạm biết vậy)
>
>
>
> ---
>
>
>
> Như vậy, trong không gian gốc (nơi data là 𝐱1,...𝐱N, chia thành các class 𝒞1,...𝒞K), covariance matrix tổng là:
>
>
>
> 𝐒T = 𝐒W + 𝐒B với 𝐒W là tổng các within-class covariance matrix Σk=1:K 𝐒k có công thức 𝐒k = Σi∈𝒞k \[(𝐱i - 𝐦k)(𝐱i - 𝐦k)ᵀ\]
>
>
>
> Thì tương tự, trong không gian hình chiếu (nơi ta đã chiếu D-dimensional vector 𝐱1,...𝐱N thành các D' dimensional vector 𝐲1 = 𝐖ᵀ𝐱1, 𝐲2 = 𝐖ᵀ𝐱2,..., 𝐲N = 𝐖ᵀ𝐱N thì
>
>
>
> 𝐬W (within-class covariance matrix trong không gian chiếu), dùng chữ 𝐬 nhỏ
>
>
>
> = Σk=1:K 𝐬k, với 𝐬k = Σi∈𝒞k (𝐲i-𝛍k)(𝐱i-𝛍k)ᵀ (tương tự thôi)
>
>
>
> = Σk=1:K \[Σi∈𝒞k (𝐲i-𝛍k)(𝐲i-𝛍k)ᵀ\]
>
>
>
> Và cũng tương tự, 𝐬B = Σk Nk(𝛍k - 𝛍)(𝛍k - 𝛍)ᵀ
>
>
>
> ---
>
>
>
> Thế thì, trong case 2 class, mình còn nhớ Fisher criterion được đặt ra theo ý định đạt được hai thứ sau: Maximize sự phân tách của hai class sau khi chiếu, bằng cách maximize distance của hình chiếu của hai tâm của hai đám data thuộc hai class) và minimize sự chồng lấn bằng cách minimize mức phân tán của hình chiếu dữ liệu của mỗi class. Và với ý định đó, ta đặt ra criterion là \[between-class variance\] và \[within class variance\], và đây là một con số (scalar) phụ thuộc 𝐰, để rồi bằng cách maximize cái này theo 𝐰 ta sẽ tìm được 𝐰 tốt nhất cho mục tiêu trên.
>
>
>
> Thì điểm mình hiểu là, ta muốn thiết kế criterion là một scalar, để chi, để ta có bài toán tối ưu hàm mục tiêu là một hàm vector scalar, như vậy sẽ dễ hơn thay vì hàm mục tiêu là hàm vector - vector hay vector - matrix
>
>
>
> Thì ở đây tương tự vậy, mục tiêu cũng là như vậy, do đó ta mới thấy gs nói ta muốn construct một scalar sao cho khi nó lớn thì between-class covariance lớn và within class covariance nhỏ.
>
>
>
> Có thể hỏi vì sao ko làm như trước, lấy hai cái chia nhau: À thì là vì ở case 2 class, hai cái between / with variance chỉ là một con số (variance), nên chia nhau được. Còn ở đây, mức phân tán between-class / within-class được thể hiện bởi các covariance MATRIX, thì làm sao chia nhau được.
>
>
>
> Nhưng có một cách: Dùng trace: J(𝐖) = tr(𝐬W⁻¹ 𝐬B}. Vì sao lại dùng cái này?
>
>
>
> Vì trace, như đã biết là tổng các phần tử đường chéo, cũng là tổng các eigenvalue.
>
>
>
> Nên tr(𝐬W⁻¹ 𝐬B} là tổng eigenvalue của 𝐬W⁻¹ 𝐬B. Nếu 𝐬W nhỏ, thì 𝐬W⁻¹ sẽ lớn lại, khiến tr(𝐬W⁻¹ 𝐬B} lớn. Và nếu 𝐬B lớn, thì tr(𝐬W⁻¹ 𝐬B} cũng lớn. Do đó đây là objective mà khi nó lớn, ta sẽ bóp 𝐬W nhỏ → giảm withclass-covariance và 𝐬B lớn → răng between-class covariance.
>
>
>
> Dĩ nhiên đây vẫn là hàm gián tiếp phụ thuộc 𝐖, thay vào ta có công thức tường minh (explicit):
>
>
>
> 𝐬W = Σk \[Σi∈𝒞k (𝐲i-𝛍k)(𝐲i-𝛍k)ᵀ\]
>
>
>
> = Σk \[Σi∈𝒞k (𝐖ᵀ𝐱i-𝐖ᵀ𝐦k)(𝐖ᵀ𝐱i-𝐖ᵀ𝐦k)ᵀ\] (vì 𝐲i = 𝐖ᵀ𝐱i, 𝛍k là hình chiếu của 𝐦k, = 𝐖ᵀ𝐦k)
>
>
>
> = Σk \[Σi∈𝒞k 𝐖ᵀ(𝐱i-𝐦k)(𝐖ᵀ(𝐱i-𝐦k))ᵀ\]
>
>
>
> = Σk \[Σi∈𝒞k 𝐖ᵀ(𝐱i-𝐦k)(𝐱i-𝐦k)ᵀ𝐖\]
>
>
>
> = Σk 𝐖ᵀ \[Σi∈𝒞k (𝐱i-𝐦k)(𝐱i-𝐦k)ᵀ\] 𝐖
>
>
>
> = 𝐖ᵀ (Σk \[Σi∈𝒞k (𝐱i-𝐦k)(𝐱i-𝐦k)ᵀ\]) 𝐖
>
>
>
> Cái ở giữa chính là 𝐒W
>
>
>
> = 𝐖ᵀ (𝐒W) 𝐖
>
>
>
> 𝐬B = Σk Nk(𝛍k - 𝛍)(𝛍k - 𝛍)ᵀ, tương tự, biến đổi tí sẽ thấy nó là 𝐖ᵀ (𝐒B) 𝐖
>
>
>
> ⇒ J(𝐖) = tr(𝐬W⁻¹ 𝐬B}
>
>
>
> = tr(\[𝐖ᵀ (𝐒W) 𝐖\]⁻¹ 𝐖ᵀ (𝐒B) 𝐖)
>
>
>
> Đây là công thức 4.51. Hình như giáo sư Bishop viết sai chỗ này, vì 𝐲 = 𝐖ᵀ𝐱 thì biến đổi xong ở đầu phải là 𝐖ᵀ
>
>
>
> ---
>
>
>
> Như vậy cái ta cần làm là giải bài toán maximize over 𝐖 hàm J(𝐖) = tr(\[𝐖ᵀ (𝐒W) 𝐖\]⁻¹ 𝐖ᵀ (𝐒B) 𝐖)
>
>
>
> Và ông Bishop nói Fukunaga 1990 giải bài toán này, rất dài, kết quả cho ra các cột của 𝐖 là các eigenvector của 𝐒W⁻¹𝐒B tương ứng với D' eigenvalue lớn nhất. (cái này tạm biết vậy)

<details>
<summary>🌐 English translation of the original note</summary>

> *This is an AI-translated version of the original Vietnamese note above.*
>
> Let's see, the main idea here is that we generalize Fisher's discriminant to the problem with more classes
>
>
>
> Suppose the original data dimension is D, and call D' the number of "linear features": yk = 𝐰kᵀ𝐱, k=1,...D' what does that mean? That means similarly to when we project (!) 𝐱 from D dimensions onto span {𝐰}, by calculating y = 𝐰ᵀ𝐱, carrying the meaning of reducing data dimension from D down to 1 dimension, and this is a linear feature because y is a linear function with respect to 𝐱 as simple as that (but hinting to us that in a few days we will have nonlinear features?), then here, we will use D' vectors: 𝐰1,...𝐰D', to project data onto, creating D' linear features y1=𝐰1ᵀ𝐱,...,yD' = 𝐰D'ᵀ𝐱, grouped into a D'-dimensional vector: 𝐲. Thus carrying the meaning, that, from the initial D-dimensional data, we compress down to D' dimensions..
>
>
>
> And expressed compactly by setting 𝐰1,.., 𝐰D' as the columns of 𝐖. Then 𝐲 = 𝐖ᵀ𝐱, this is easy to understand (because element yj will be the dot product of row j of 𝐖ᵀ, which is also column j of 𝐖, namely 𝐰j with 𝐱: yj = 𝐰jᵀ𝐱)
>
>
>
> ---
>
>
>
> (!) Note, **saying projection but it should be understood as linear mapping from R^D to R^D'** but **not an orthogonal projection (orthogonal projection) as in the geometric intuition of the least square problem.**
>
>
>
> ---
>
>
>
> Next, with the two classes the other day, then 𝐒1 = Σi∈𝒞1 (𝐱i - 𝐦1)(𝐱i - 𝐦1)ᵀ, 𝐒2 = Σi∈𝒞2 (𝐱i - 𝐦2)(𝐱i - 𝐦2)ᵀ
>
>
>
> then now the generalization of within-class covariance matrix for the K class case is:
>
>
>
> 𝐒w = Σk=1:K 𝐒k with 𝐒k = Σi∈𝒞k (𝐱i - 𝐦k)(𝐱i - 𝐦k)ᵀ and 𝐦k = (1/Nk) Σi∈𝒞k 𝐱i.
>
>
>
> By the way one might wonder why this is the formula of the (within class) covariance matrix? or, why there is such a covariance matrix formula.
>
>
>
> By definition, if we have random vector 𝐗, 𝐘 then Cov(𝐗,𝐘) = E\[(𝐗-E(𝐗))(𝐘-E(𝐘))ᵀ\],
>
>
>
> (𝐗-E(𝐗))(𝐘-E(𝐘))ᵀ is a random matrix with element ij (Xi - E(Xi)) × (Yj - E(Yj))
>
>
>
> so element ij of Cov(𝐗, 𝐘) = E\[(Xi - E(Xi)) × (Yj - E(Yj))\]
>
>
>
> Cov(𝐗, 𝐗), we write shorthand as Cov(𝐗) = E\[(𝐗-E(𝐗))(𝐗-E(𝐗))ᵀ\], then element ij is E\[(Xi - E(Xi))(Xj - E(Xj))\]
>
>
>
> Then, to calculate expectation, we have to know the distribution: the possible values, and probability
>
>
>
> So we argue that: 𝐱1, ...𝐱N are the possible values of discrete uniform 𝐗, i.e. P(𝐗 = 𝐱1) = ...= P(𝐗 = 𝐱N) = 1/N
>
>
>
> E\[𝐗\] will be equal to: 𝐱1 × P(𝐗=𝐱1) + ...+ 𝐱N × P(𝐗=𝐱N) (definition of expectation of discrete rv)
>
>
>
> = 𝐱1/N + ...+ 𝐱N/N = (Σi 𝐱i)/N, set as 𝐦 (sample mean)
>
>
>
> then Cov(𝐗) = E\[(𝐗-E(𝐗))(𝐗-E(𝐗))ᵀ\] = (𝐱1-E(𝐗))(𝐱1-E(𝐗))ᵀ × P(𝐗=𝐱1) + ...+ (𝐱N-E(𝐗))(𝐱N-E(𝐗))ᵀ × P(𝐗=𝐱N)
>
>
>
> = (1/N) \[(𝐱1-E(𝐗))(𝐱1-E(𝐗))ᵀ + ...+ (𝐱N-E(𝐗))(𝐱N-E(𝐗))ᵀ\]
>
>
>
> = (1/N) \[(𝐱1-𝐦)(𝐱1-𝐦)ᵀ + ...+ (𝐱N-𝐦)(𝐱N-𝐦)ᵀ\]
>
>
>
> = (1/N) Σi (𝐱i-𝐦)(𝐱i-𝐦)ᵀ
>
>
>
> Dropping 1/N, we will get what is called scatter matrix, we have Σi (𝐱i-𝐦)(𝐱i-𝐦)ᵀ. and the places where mr Bishop says within-class or between-class covariance matrix, is actually not covariance matrix but scatter matrix 
>
>
>
> Thus, this is roughly the covariance matrix formula when we treat 𝐗, whose distribution is originally not yet known how it is, in order to calculate E\[(𝐗-E(𝐗))(𝐗-E(𝐗))ᵀ\], we treat it as uniform discrete having possible values 𝐱1,...𝐱N, then to calculate with this distribution, called **emprical distribution**.
>
>
>
> ---
>
>
>
> Next, we let 𝐒T, be the total covariance matrix then by algebraic transformation we can split 𝐒T into 𝐒W + 𝐒B with 𝐒B according to formula 𝐒B = Σk Nk(𝐦k - 𝐦)(𝐦k - 𝐦)ᵀ (4.46) (this is just algebraic transformation, **lengthy but not difficult**, just tentatively know it like that)
>
>
>
> ---
>
>
>
> Thus, in the original space (where data is 𝐱1,...𝐱N, divided into classes 𝒞1,...𝒞K), the total covariance matrix is:
>
>
>
> 𝐒T = 𝐒W + 𝐒B with 𝐒W being the sum of the within-class covariance matrices Σk=1:K 𝐒k having formula 𝐒k = Σi∈𝒞k \[(𝐱i - 𝐦k)(𝐱i - 𝐦k)ᵀ\]
>
>
>
> Then similarly, in the projected space (where we have projected D-dimensional vectors 𝐱1,...𝐱N into D' dimensional vectors 𝐲1 = 𝐖ᵀ𝐱1, 𝐲2 = 𝐖ᵀ𝐱2,..., 𝐲N = 𝐖ᵀ𝐱N then
>
>
>
> 𝐬W (within-class covariance matrix in projected space), using lowercase letter 𝐬
>
>
>
> = Σk=1:K 𝐬k, with 𝐬k = Σi∈𝒞k (𝐲i-𝛍k)(𝐱i-𝛍k)ᵀ (just similar)
>
>
>
> = Σk=1:K \[Σi∈𝒞k (𝐲i-𝛍k)(𝐲i-𝛍k)ᵀ\]
>
>
>
> And also similarly, 𝐬B = Σk Nk(𝛍k - 𝛍)(𝛍k - 𝛍)ᵀ
>
>
>
> ---
>
>
>
> Then, in the 2 class case, I still remember Fisher criterion was set up according to the intention of achieving the following two things: Maximize the separation of the two classes after projection, by maximizing distance of the projection of the two centers of the two data clusters belonging to the two classes) and minimize the overlap by minimizing the dispersion level of the projected data of each class. And with that intention, we set up the criterion as \[between-class variance\] and \[within class variance\], and this is a number (scalar) depending on 𝐰, so that by maximizing this with respect to 𝐰 we will find the best 𝐰 for the above objective.
>
>
>
> Then the point I understand is, we want to design the criterion to be a scalar, for what, so that we have the problem of optimizing an objective function that is a vector scalar function, which will be easier instead of the objective function being a vector - vector or vector - matrix function
>
>
>
> Then here similarly, the objective is also like that, therefore we only then see prof saying we want to construct a scalar such that when it is large, between-class covariance is large and within class covariance is small.
>
>
>
> One could ask why not do like before, divide the two by each other: Ah well because in the 2 class case, the two between / with variance are just a number (variance), so can be divided by each other. Whereas here, the between-class / within-class dispersion level is represented by covariance MATRIX, so how can they be divided by each other.
>
>
>
> But there is a way: Use trace: J(𝐖) = tr(𝐬W⁻¹ 𝐬B}. Why use this?
>
>
>
> Because trace, as is known is the sum of diagonal elements, also the sum of eigenvalues.
>
>
>
> So tr(𝐬W⁻¹ 𝐬B} is the sum of eigenvalues of 𝐬W⁻¹ 𝐬B. If 𝐬W is small, then 𝐬W⁻¹ will become large again, making tr(𝐬W⁻¹ 𝐬B} large. And if 𝐬B is large, then tr(𝐬W⁻¹ 𝐬B} is also large. Therefore this is the objective where when it is large, we will squeeze 𝐬W small → reduce withclass-covariance and 𝐬B large → tooth between-class covariance.
>
>
>
> Naturally this is still an indirect function depending on 𝐖, substituting in we have the explicit formula:
>
>
>
> 𝐬W = Σk \[Σi∈𝒞k (𝐲i-𝛍k)(𝐲i-𝛍k)ᵀ\]
>
>
>
> = Σk \[Σi∈𝒞k (𝐖ᵀ𝐱i-𝐖ᵀ𝐦k)(𝐖ᵀ𝐱i-𝐖ᵀ𝐦k)ᵀ\] (because 𝐲i = 𝐖ᵀ𝐱i, 𝛍k is the projection of 𝐦k, = 𝐖ᵀ𝐦k)
>
>
>
> = Σk \[Σi∈𝒞k 𝐖ᵀ(𝐱i-𝐦k)(𝐖ᵀ(𝐱i-𝐦k))ᵀ\]
>
>
>
> = Σk \[Σi∈𝒞k 𝐖ᵀ(𝐱i-𝐦k)(𝐱i-𝐦k)ᵀ𝐖\]
>
>
>
> = Σk 𝐖ᵀ \[Σi∈𝒞k (𝐱i-𝐦k)(𝐱i-𝐦k)ᵀ\] 𝐖
>
>
>
> = 𝐖ᵀ (Σk \[Σi∈𝒞k (𝐱i-𝐦k)(𝐱i-𝐦k)ᵀ\]) 𝐖
>
>
>
> The thing in the middle is precisely 𝐒W
>
>
>
> = 𝐖ᵀ (𝐒W) 𝐖
>
>
>
> 𝐬B = Σk Nk(𝛍k - 𝛍)(𝛍k - 𝛍)ᵀ, similarly, transforming a bit will see that it is 𝐖ᵀ (𝐒B) 𝐖
>
>
>
> ⇒ J(𝐖) = tr(𝐬W⁻¹ 𝐬B}
>
>
>
> = tr(\[𝐖ᵀ (𝐒W) 𝐖\]⁻¹ 𝐖ᵀ (𝐒B) 𝐖)
>
>
>
> This is formula 4.51. It seems professor Bishop wrote it wrong here, because 𝐲 = 𝐖ᵀ𝐱 then after transforming the beginning must be 𝐖ᵀ
>
>
>
> ---
>
>
>
> Thus what we need to do is solve the problem of maximize over 𝐖 the function J(𝐖) = tr(\[𝐖ᵀ (𝐒W) 𝐖\]⁻¹ 𝐖ᵀ (𝐒B) 𝐖)
>
>
>
> And Mr. Bishop said Fukunaga 1990 solved this problem, very long, the result gives the columns of 𝐖 as the eigenvectors of 𝐒W⁻¹𝐒B corresponding to the D' largest eigenvalues. (just know this for now)

---

**🤖 AI Check (English)**

Summary: Excellent notes, very firmly grasping the geometric, algebraic, and statistical nature of multiclass Fisher LDA. In particular, you yourself accurately detected the typographical notation error (erratum) in formula (4.51) of Bishop's book.

Minor issues:
1. "𝐬k = Σi∈𝒞k (𝐲i-𝛍k)(𝐱i-𝛍k)ᵀ (just similar)" — There is a small typo with the variable 𝐱i instead of 𝐲i in the second factor. Although right in the line below you rewrote it correctly as (𝐲i-𝛍k)(𝐲i-𝛍k)ᵀ, you should still correct this line to avoid confusion when rereading.
2. "J(𝐖) = tr(𝐬W⁻¹ 𝐬B}" — The expression with the existence of the inverse 𝐬W⁻¹ (and 𝐒W⁻¹) implicitly assumes that the within-class scatter matrix is invertible. This requires the number of data samples to be sufficiently large compared to the number of dimensions (N - K ≥ D), otherwise it will encounter the singularity phenomenon (small sample size problem) that requires regularization techniques (regularization).

Strengths:
• Extremely accurate detection of Professor Bishop's typographical error (official erratum) in formula (4.51) when swapping the positions between 𝐖 and 𝐖ᵀ.
• Very deep and intuitive reasoning about the origin of the covariance/scatter matrix through the empirical distribution (empirical distribution).
• Clear distinction between linear projection (linear projection/mapping) and orthogonal projection (orthogonal projection) in least squares.

Deeper notes:
• Because 𝐒B is the sum of K rank-1 matrices with the constraint that the weighted sum equals 0 (because the sum of Nk(𝐦k - 𝐦) = 0), the rank of 𝐒B is at most K - 1. Therefore, the number of non-zero eigenvalues of 𝐒W⁻¹𝐒B is at most K - 1, leading to the maximum compressed dimension D' meaningful for classification being K - 1.
• The case of more than 2 classes does not guarantee that projecting to 1 dimension is optimal, but rather requires projecting to D' dimensions (with 1 < D' ≤ K - 1).

</details>

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **96/100** · ✓ Move on
>
> Ghi chú xuất sắc, nắm rất vững bản chất hình học, đại số và thống kê của Fisher LDA đa lớp. Đặc biệt, bạn đã tự phát hiện chính xác lỗi in sai ký hiệu (erratum) trong công thức (4.51) của sách Bishop.
>
> **🟡 Minor issues**
> **1.** *"𝐬k = Σi∈𝒞k (𝐲i-𝛍k)(𝐱i-𝛍k)ᵀ (tương tự thôi)"* — Có một lỗi gõ nhầm nhỏ biến 𝐱i thay vì 𝐲i ở thừa số thứ hai. Dù ngay dòng dưới bạn đã viết lại chính xác là (𝐲i-𝛍k)(𝐲i-𝛍k)ᵀ, bạn vẫn nên chỉnh lại dòng này để tránh nhầm lẫn khi đọc lại.
> **2.** *"J(𝐖) = tr(𝐬W⁻¹ 𝐬B}"* — Biểu thức tồn tại nghịch đảo 𝐬W⁻¹ (và 𝐒W⁻¹) ngầm định rằng ma trận scatter trong lớp khả nghịch. Điều này đòi hỏi số lượng mẫu dữ liệu phải đủ lớn so với số chiều (N - K ≥ D), nếu không sẽ gặp hiện tượng kỳ dị (small sample size problem) cần kỹ thuật chính quy hóa (regularization).
>
> **✓ Strengths**
> - Phát hiện cực kỳ chuẩn xác lỗi sai in ấn (erratum chính thức) của giáo sư Bishop ở công thức (4.51) khi hoán đổi vị trí giữa 𝐖 và 𝐖ᵀ.
> - Lập luận rất sâu sắc và trực quan về nguồn gốc ma trận covariance/scatter thông qua phân phối thực nghiệm (empirical distribution).
> - Phân biệt rạch ròi giữa phép chiếu tuyến tính (linear projection/mapping) với phép chiếu vuông góc (orthogonal projection) trong bình phương tối thiểu.
>
> **💡 Deeper notes**
> - Do 𝐒B là tổng của K ma trận rank 1 có ràng buộc tổng trọng số bằng 0 (vì tổng Nk(𝐦k - 𝐦) = 0), rank của 𝐒B tối đa chỉ là K - 1. Vì vậy, số lượng eigenvalue khác 0 của 𝐒W⁻¹𝐒B tối đa chỉ là K - 1, dẫn tới số chiều nén D' tối đa có ý nghĩa phân lớp là K - 1.
> - Trường hợp nhiều hơn 2 lớp không đảm bảo chiếu về 1 chiều là tối ưu mà cần chiếu về D' chiều (với 1 < D' ≤ K - 1).

<br>

<a id="node-uxfgl6e"></a>

### Rank of Between-Class Scatter Matrix

<p align="center"><kbd><img src="assets/qfjupds917.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi đoạn cuối đại khái là nói 𝐒B, theo công thức hồi nãy = Σk Nk(𝐦k - 𝐦)(𝐦k - 𝐦)ᵀ, dễ thấy là tổng các rank 1 matrix Nk(𝐦k - 𝐦)(𝐦k - 𝐦)ᵀ
>
>
>
> Vì sao rank 1? À là vì đây là outer product của hai vector: Lập luận vầy sẽ thấy nó là rank 1: Giả sử A = abᵀ, có thể coi như đây là tích của hai matrix a, có m hàng, 1 cột và bᵀ có 1 hàng, n cột. Thì theo góc nhìn thứ hai của việc nhân hai matrix E = CD thì cột j của E là linear combination các cột của C bởi hệ số là các phần tử của cột j của D.
>
>
>
> Do đó, cột j của A là linear combination các cột của "matrix a" bởi hệ số là các các phần tử của cột j của "matrix b". Và matrix a chỉ có 1 cột cũng như cột j của b cũng chỉ có 1 phần tử, nên cột j của A là vector a × scalar bj. Như vậy, cột 1 của A là scalar b1 × vector a, cột 2 của A là scalar b2 × vector a,...Từ đó thấy ngay các cột của A đều bằng \[số gì đó\] × vector a, do đó chúng đều phụ thuộc tuyến tính vector a. Đồng nghĩa, trong các cột của A, chỉ có một vector độc lập (vì chúng đều chỉ có cùng một phương). Và như vậy, dimension của C(A) = 1 cũng là rank = 1.
>
>
>
> Như vậy, N1(𝐦1 - 𝐦)(𝐦1 - 𝐦)ᵀ sẽ giống như abᵀ, có các cột đều trùng hướng với 𝐦1 - 𝐦, nên chỉ có rank = 1.
>
>
>
> Và tổng chúng lại, nếu như 𝐦1 - 𝐦, 𝐦2 - 𝐦,...𝐦K - 𝐦 đều là các hướng khác nhau (độc lập tuyến tính) thì Σk Nk(𝐦k - 𝐦)(𝐦k - 𝐦)ᵀ sẽ có rank K.
>
>
>
> Vấn đề là vì 𝐦 = (Σk Nk𝐦k)/N (cái này dễ thấy)
>
>
>
> nên N𝐦 = (Σk Nk𝐦k) ⇒ (Σk 𝐦k) - N𝐦 = 0
>
>
>
> ⇔ Σk (Nk𝐦k - 𝐦) = 0
>
>
>
> ⇔ Σk=1:K-1 (Nk𝐦k - 𝐦) = -(𝐦K - 𝐦)
>
>
>
> và như vậy cho thấy (𝐦K - 𝐦) có thể được tạo ra bởi mấy thằng còn lại, nên theo MIT 1806 đã học, ta nói nó phụ thuộc tuyến tính mấy thằng đó.
>
>
>
> Như vậy, nhiều nhất, ta chỉ có K-1 vector độc lập (có thể còn ít hơn, vì có khi cả đám K vector nhưng chỉ có vài cái là độc lập)
>
>
>
> Vậy thì sao?
>
>
>
> Thì hậu quả là: Ở trên vừa nói giải bài toán tìm 𝐖 ta sẽ thấy chúng là D' eigenvector ứng với những eigevalue lớn nhất của của 𝐒W⁻¹𝐒B.
>
>
>
> Như vậy gọi u và λ là eigenvector và eigenvalue của 𝐒W⁻¹𝐒B ta có:
>
>
>
> 𝐒W⁻¹𝐒B u = λ u
>
>
>
> nên trong D cột, nó chỉ có K-1 cột độc lập, và sẽ có D-K+1 cột phụ thuộc, ứng với D-K+1 vector khác 0 trong nullspace.
>
> \
> Và điều này cho ta một kết luận rằng: Có K+1 vector độc lập 𝐯1,...𝐯D-K+1 thỏa:
>
>
>
> 𝐒B 𝐯j = 0, = 0 thì cũng là = 0 × 𝐯j
>
>
>
> điều này chính là nói, ta có D-K+1 eigenvector của 𝐒B ứng với cùng giá trị eigenvalue = 0.
>
>
>
> Và như vậy với các vector 𝐯j này thì 𝐒W⁻¹𝐒B 𝐯j cũng bằng 0, cho thấy 𝐒W⁻¹𝐒B cũng có D-K+1 eigenvector độc lập ứng với eigenvalue = 0.
>
>
>
> Do đó, 𝐒W⁻¹𝐒B sẽ chỉ có nhiều nhất là K-1 eigenvalue khác 0.
>
>
>
> (mai tiếp)

<details>
<summary>🌐 English translation of the original note</summary>

> *This is an AI-translated version of the original Vietnamese note above.*
>
> Then the last part roughly says 𝐒B, according to the formula earlier = Σk Nk(𝐦k - 𝐦)(𝐦k - 𝐦)ᵀ, is easy to see is the sum of rank 1 matrices Nk(𝐦k - 𝐦)(𝐦k - 𝐦)ᵀ
>
>
>
> Why rank 1? Ah it is because this is the outer product of two vectors: Reasoning like this will show it is rank 1: Suppose A = abᵀ, this can be considered as the product of two matrices a, having m rows, 1 column and bᵀ having 1 row, n columns. Then according to the second perspective of multiplying two matrices E = CD, column j of E is a linear combination of the columns of C with the coefficients being the elements of column j of D.
>
>
>
> Therefore, column j of A is a linear combination of the columns of "matrix a" with the coefficients being the the elements of column j of "matrix b". And matrix a has only 1 column just as column j of b also has only 1 element, so column j of A is vector a × scalar bj. As such, column 1 of A is scalar b1 × vector a, column 2 of A is scalar b2 × vector a,... From that, one sees immediately that the columns of A are all equal to [some number] × vector a, therefore they are all linearly dependent on vector a. Meaning, among the columns of A, there is only one independent vector (because they all only have the same direction). And as such, the dimension of C(A) = 1 is also rank = 1.
>
>
>
> As such, N1(𝐦1 - 𝐦)(𝐦1 - 𝐦)ᵀ will be like abᵀ, having columns that all coincide in direction with 𝐦1 - 𝐦, so it only has rank = 1.
>
>
>
> And summing them up, if 𝐦1 - 𝐦, 𝐦2 - 𝐦,...𝐦K - 𝐦 are all different directions (linearly independent) then Σk Nk(𝐦k - 𝐦)(𝐦k - 𝐦)ᵀ will have rank K.
>
>
>
> The problem is because 𝐦 = (Σk Nk𝐦k)/N (this is easy to see)
>
>
>
> so N𝐦 = (Σk Nk𝐦k) ⇒ (Σk 𝐦k) - N𝐦 = 0
>
>
>
> ⇔ Σk (Nk𝐦k - 𝐦) = 0
>
>
>
> ⇔ Σk=1:K-1 (Nk𝐦k - 𝐦) = -(𝐦K - 𝐦)
>
>
>
> and as such shows that (𝐦K - 𝐦) can be created by the remaining guys, so according to MIT 1806 studied, we say it is linearly dependent on those guys.
>
>
>
> As such, at most, we only have K-1 independent vectors (possibly even fewer, because sometimes the whole bunch of K vectors but only a few are independent)
>
>
>
> So what?
>
>
>
> Then the consequence is: Above it was just said solving the problem of finding 𝐖 we will see they are D' eigenvectors corresponding to the largest eigevalues of of 𝐒W⁻¹𝐒B.
>
>
>
> As such, calling u and λ the eigenvector and eigenvalue of 𝐒W⁻¹𝐒B we have:
>
>
>
> 𝐒W⁻¹𝐒B u = λ u
>
>
>
> so in D columns, it only has K-1 independent columns, and will have D-K+1 dependent columns, corresponding to D-K+1 non-zero vectors in the nullspace.
>
> \
> And this gives us a conclusion that: There are K+1 independent vectors 𝐯1,...𝐯D-K+1 satisfying:
>
>
>
> 𝐒B 𝐯j = 0, = 0 is also = 0 × 𝐯j
>
>
>
> this is precisely saying, we have D-K+1 eigenvectors of 𝐒B corresponding to the same eigenvalue value = 0.
>
>
>
> And as such with these vectors 𝐯j, 𝐒W⁻¹𝐒B 𝐯j also equals 0, showing that 𝐒W⁻¹𝐒B also has D-K+1 independent eigenvectors corresponding to eigenvalue = 0.
>
>
>
> Therefore, 𝐒W⁻¹𝐒B will only have at most K-1 eigenvalues different from 0.
>
>
>
> (continue tomorrow)

</details>

<br>

