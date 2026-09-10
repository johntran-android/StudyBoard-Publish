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
> Giả sử số chiều dữ liệu gốc là D, và gọi D' là số "feature tuyến tính": yk = 𝐰kᵀ𝐱, k=1,...D' tức là sao? Tức là tương tự như khi ta chiếu (!) 𝐱 từ D chiều lên span {𝐰}, bằng cách tính y = 𝐰ᵀ𝐱, mang ý nghĩa là giảm chiều dữ liệu từ D còn thành 1 chiều, và đây là feature tuyến tính vì y là hàm tuyến tính đối với 𝐱 đơn giản vậy thôi (nhưng gợi ý ta rằng vài bữa ta sẽ có các feature phi tuyến?), thì ở đây, ta sẽ dùng D' vector: 𝐰1,...𝐰D', để chiếu data lên, tạo ra D' feature tuyến tính y1=𝐰1ᵀ𝐱,...,yD' = 𝐰D'ᵀ𝐱, gom lại thành vector D' chiều: 𝐲. Như vậy mang ý nghĩa, là, từ dữ liệu D chiều ban đầu, ta nén còn D' chiều.
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
> (!) Vì sao gọi là chiếu: Là vì 𝐱1 nằm trong R^D, thì sau khi nhân với 𝐖ᵀ, 𝐲1 nằm trong column space của 𝐖ᵀ, với việc ta chỉ có D' cột, và D' &lt; D, thì cơ bản là ta đã chỉ còn một subspace của R^D.
>
>
>
> Chú ý, **nói là chiếu** nhưng **không phải là chiếu vuông góc**, tức vì chiếu vuông góc thì matrix chiếu lên C(𝐖) sẽ là khác: Là 𝐖(𝐖ᵀ𝐖)⁻¹𝐖ᵀ, và matrix chiếu lên C(𝐖ᵀ) sẽ là 𝐖ᵀ(𝐖𝐖ᵀ)⁻¹𝐖 Và trong trường hợp các cột của 𝐖ᵀ orthonormal.)
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
> Bỏ 1/N đi, nó chỉ là scalar, ta có Σi (𝐱i-𝐦)(𝐱i-𝐦)ᵀ
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

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú rất xuất sắc, thể hiện tư duy phân tích sâu sắc, tự suy diễn mạch lạc về mặt thống kê và đặc biệt phát hiện chính xác lỗi in sai kinh điển trong sách của Bishop.

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

<br>

