# 2.5.2 Nearest-neighbour methods

📊 **Progress:** `5` Notes | `10` Screenshots | `5` AI Reviews

---
<a id="node-1dy0iuq"></a>

<br>

<a id="node-hr4ynja"></a>

## 2.5.2 Nearest-neighbour methods

<p align="center"><kbd><img src="assets/20113f3hyyw.png" width="80%"></kbd></p>

> [!NOTE]
> Ta sẽ qua cách tiếp cận thứ hai sau kernel density estimation, đó là nearest neighbor.
>
>
>
> Đầu tiên gs nói rằng, cách làm của kernel densitiy nó có hạn chế là: h ở đâu cũng bằng nhau. Còn nhớ, h đại khái là phạm vi mà ta dùng để xác định tầm ảnh hưởng của một data point. Ví dụ như khi dùng hàm kernel là Parzen window, thì h là cạnh của một hyper-cube, để từ đó nếu khoảng cách của 𝐱 đến data point 𝐱i nhỏ hơn h/2, thì pdf tại x sẽ "bị ảnh hưởng bởi 𝐱i" (hàm parzen window kernel sẽ = 1, khiến pdf của x sẽ tăng thêm một khoảng do ảnh hưởng của 𝐱i). Với kernel function khác, như Normal kernel thì cũng vậy.
>
>
>
> Thế thì vấn đề là, việc h như nhau ở mọi nơi khiến cho nó bị cứng nhắc. Vì khi xét trong **vùng có nhiều data sample, thì nên cho h nhỏ lại, và ngược lại trong vùng thưa data sample thì nên cho h lớn lên**. Vì nếu trong vùng nhiều data sample mà h lớn quá quá sẽ khiến dẫn đến over-smoothing effect, xóa xạch các cấu trúc có thể được nắm bắt từ data. Ngược lại, nơi data density thấp mà h nhỏ quá sẽ khiến noisy. Nói chung **chỉ cần hiểu là h như nhau ở mọi nơi thì không tối ưu.**

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **98/100** · ✓ Move on</summary>

Ghi chú đã tóm tắt rất hiệu quả hạn chế chính của tham số 'h' cố định trong ước lượng mật độ kernel, giải thích rõ ràng hậu quả của nó trong các vùng mật độ dữ liệu cao và thấp. Việc bổ sung giải thích về tham số 'h' và các hàm kernel khác nhau đã giúp làm sâu sắc thêm sự hiểu biết về ngữ cảnh, rất đáng khen.

</details>

<br>

<a id="node-qpzx5xr"></a>

### Local Density Estimation Method

<p align="center"><kbd><img src="assets/hmhkyjju1zt.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/685f3dxcgbl.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/a6k6bve7uld.png" width="80%"></kbd></p>

> [!NOTE]
> Để hiểu cần recall lại chút (công thức 2.246: f(𝐱) ≈ K / NV)
>
>
>
> Nói chung là, công thức này cho ta một cách để estimate giá trị của hàm density (probability density, tức pdf) tại một điểm 𝐱. Với K, còn nhớ, là ∑i I\_(𝐱i ∈ R), là số data point (sample) rơi vào vùng R (lân cận 𝐱). V là volume của vùng R. Và N là kích thước sample.
>
>
>
> Thế thì dựa vào công thức này, bằng cách fixed V, và xác định K nhờ data, ta sẽ có cách tiếp cận non-parameteric đầu tiên của bài toán density estimation - kernel approach. Trong đó, ta sẽ dùng một hàm kernel để tính xem có bao nhiêu data point 𝐱i nằm trong phạm vi R của 𝐱 (mà cũng là có x nằm trong phạm vi của bao nhiêu data point, và nhân với) và từ đó sẽ định ra giá trị cao hay thấp của density tại 𝐱.
>
>
>
> Qua cách thứ hai, ta sẽ fix K, và dựa vào data để tính V, thì cách làm là: tại 𝐱 (nơi cần tính f(𝐱)), ta sẽ mở rộng vùng R (là một sphare - khối cầu) quanh nó ra cho đến khi chứa đủ K data sample 𝐱i, hoặc cũng có thể nhìn theo cách khác, mở rộng R (chính là tăng, hay xác định V) sao cho 𝐱 nằm trong vùng ảnh hưởng của K data sample 𝐱i.
>
>
>
> Dùng ví dụ trước để minh họa có thể thấy K sẽ ảnh hưởng đến độ mượt.
>
>
>
> K nhỏ sẽ khiến K-neighbor density không mượt (noisy) mà K lớn quá sẽ khiến nó quá mượt làm mất đi (không capture / nắm bắt được pattern) cấu trúc của hàm density thật (cụ thể là hai cái đỉnh (modal) của đường màu xanh lá cây)
>
>
>
> Ôn lại tí: Với kernel density, ta sẽ fixed V, và dựa vào K từ data để tính độ cao thấp của density. Với hàm Parzen window kernel, sự cao thấp của kernel density sẽ được quyết định bởi việc x nằm trong vùnh ảnh hưởng (hyper cubic) của bao nhiêu điểm data, và vì với Parzen window kernel là hàm binary, nên nó sẽ tạo ra hiệu ứng bậc thang, khiến hàm kernel density có dạng step function. Nên để làm trơn, ta có thể dùng Gaussian kernel, vẫn là việc x nằm trong vùng ảnh hưởng của nhiều data point hay không sẽ quyết định đến độ cao thấp của density, nhưng khác với Parzen window, nó có thêm tính chất là khi tới gần hay ra xa thì ảnh hưởng của một data point lên x sẽ lớn lên hay nhỏ lại. Nhưng dù vậy, cả hai đều có chung nguyên lý, nếu x nằm trong vùng ảnh hưởng của nhiều data point, thì density sẽ cao và ngược lại. Và ta sẽ cần hiểu, hàm Parzel window kernel hay Gaussian kernel đều chỉ quy định mức cao thấp tương đối của density, còn để có một density hợp lệ (valid) ta cần V đóng vai normalizing constant
>
>
>
> Vậy thì ở đây, gs nói, với K-nearest neighbor, khi ta fixed K và tính V, để từ đó tỉ số K/NV cao thấp tương đối so với nhau, thì vấn đề là, nó không có cái nào đóng vai normalizing constant cả,  do đó KNN density không phải là một valid pdf.

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **95/100** · ✓ Move on</summary>

Bài viết thể hiện sự hiểu biết sâu sắc về phương pháp K-nearest neighbour, phân biệt rõ ràng với kernel method và mô tả chính xác ảnh hưởng của K đến độ mượt. Để hoàn thiện hơn, hãy giải thích trực tiếp lý do nó không phải "true density model" là vì tích phân trên toàn không gian phân kỳ.


### Phân tích chi tiết

#### Điểm mạnh
*   **Nắm vững công thức cơ bản:** Bạn đã recall chính xác công thức 2.246 `f(x) ≈ K / NV` và các thành phần của nó (K là số điểm dữ liệu trong vùng R, V là thể tích vùng R, N là kích thước mẫu). Đây là nền tảng vững chắc để hiểu các phương pháp ước lượng mật độ.
*   **Phân biệt rõ ràng hai cách tiếp cận:** Bạn đã nhận diện đúng hai cách tiếp cận chính từ công thức:
    *   Cố định V và xác định K từ dữ liệu (phương pháp kernel).
    *   Cố định K và xác định V từ dữ liệu (phương pháp K-nearest neighbor).
*   **Giải thích chi tiết phương pháp K-nearest neighbor:** Mô tả của bạn về cách phương pháp K-nearest neighbor hoạt động rất chính xác, bao gồm việc mở rộng vùng R (khối cầu) quanh điểm `x` cho đến khi nó chứa đủ K điểm dữ liệu. Điều này thể hiện sự hiểu biết sâu sắc về cơ chế hoạt động.
*   **Hiểu rõ ảnh hưởng của K đến độ mượt:** Bạn đã giải thích rất tốt cách giá trị K ảnh hưởng đến độ mượt của ước lượng. Đặc biệt, việc bạn nhận ra rằng K nhỏ dẫn đến ước lượng nhiễu (noisy) và K lớn quá sẽ làm mất đi cấu trúc thực sự của hàm mật độ (cụ thể là làm mất các đỉnh của phân phối nhị thức - "hai cái đỉnh (modal) của đường màu xanh lá cây") là một điểm mạnh lớn, cho thấy bạn đã phân tích hình 2.26 một cách kỹ lưỡng.

#### Các điểm cần cải thiện
*   **Cơ chế Kernel:** Mặc dù bạn đã xác định đúng phương pháp "fixed V" là tiếp cận kernel, phần giải thích "Trong đó, ta sẽ dùng một hàm kernel để tính xem có bao nhiêu data point xi nằm trong phạm vi R của x (mà cũng là có x nằm trong phạm vi của bao nhiêu data point, và nhân với)" còn hơi mơ hồ. Hàm kernel thường *gán trọng số* cho các điểm dữ liệu dựa trên khoảng cách đến `x` thay vì chỉ đếm cứng nhắc trong một vùng `R` cố định (đây là cách tiếp cận đơn giản hơn như histogram). Cụm từ "mà cũng là có x nằm trong phạm vi của bao nhiêu data point, và nhân với" chưa thật sự rõ ràng và có thể gây hiểu nhầm về cách thức hoạt động của kernel.
*   **Hạn chế của K-nearest neighbor:** Bạn đã bỏ qua một chi tiết quan trọng được đề cập trong tài liệu tham khảo: "Note that the model produced by K nearest neighbours is not a true density model because the integral over all space diverges." Đây là một hạn chế lý thuyết quan trọng của phương pháp này cần được ghi nhận.
*   **Lỗi chính tả nhỏ:** Từ "sphare" nên là "sphere" (khối cầu).

#### Gợi ý để làm sâu sắc thêm sự hiểu biết
*   **Tìm hiểu thêm về hàm Kernel:** Để làm rõ hơn về phương pháp kernel, bạn có thể tìm hiểu cách các hàm kernel (ví dụ: Gaussian kernel, Epanechnikov kernel) được sử dụng để tạo ra "vùng ảnh hưởng" (bandwidth) linh hoạt xung quanh mỗi điểm dữ liệu và cách chúng gán trọng số cho các điểm lân cận.
*   **Ghi nhớ các giới hạn của mô hình:** Luôn chú ý đến các hạn chế lý thuyết của mỗi phương pháp. Việc K-nearest neighbor không phải là một mô hình mật độ "thực sự" vì tích phân trên toàn bộ không gian phân kỳ là một chi tiết quan trọng.
*   **Xem xét ảnh hưởng của khoảng cách:** Suy nghĩ về cách định nghĩa "gần" hoặc "phạm vi R" trong các không gian chiều cao hơn, và liệu việc sử dụng "khối cầu" có luôn là lựa chọn tốt nhất hay không.

> [!TIP]
> - Bạn đã nhận diện chính xác phương pháp "fixed V" là kernel approach, thể hiện kiến thức liên quan vượt ra ngoài phần chính của đoạn văn bản được highlight.

</details>

**🔗 See also:** [Density Estimate Formula](./251_kernel_density_estimators.md#node-a23maxi)

<br>

<a id="node-n40ednw"></a>

#### K-nearest-neighbour Classification using Bayes' Theorem

<p align="center"><kbd><img src="assets/52vntfda72y.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo, phần này gs Bishop sẽ nói về việc dùng KNN technique này để giải bài toán classification:
>
>
>
> Giả sử ta có N data sample 𝐗1,...𝐗N. Và 𝐱 là điểm cần classify. Cũng theo KNN technique: fixed K, dựa vào data tính V → ta dựng một quả cầu tâm 𝐱, chứa đủ K điểm data.
>
>
>
> Chỗ này lại một điểm như ông Bishop dùng kí hiệu khiến ta rất dễ lú: ông gọi Nk là số data point trong sample thuộc class Ck, làm ta dễ hiểu lầm là có K class. Sự thật là không phải vậy, nên mình gọi các class trong bài toán là C1,C2,....CM, tức là ta có C là một discrete random variable có M possible values C1,...CM.
>
>
>
> Và với điểm 𝐱 và quả cầu của nó, chứa K điểm data, thì ta gọi Kk là số điểm dữ liệu thuộc class Tk. Ta có Σk Kk = K.
>
>
>
> Với mỗi class Ck, ta sẽ xây dựng một K nearest neighbor (estimate) density function: f(𝐱|Ck)
>
>
>
> Y như công thức f(𝐱) = K/NV với K, dùng parzen window kernel, thì ta dùng hàm đếm xem có bao nhiêu điểm data 𝐱i nằm trong phạm vi của 𝐱 
>
>
>
> Vậy thì ta sẽ lập luận về f(𝐱|Ck) như sau
>
>
>
> Dù gs không nói, nhưng cần hiểu rằng, ta đang xét một random variable C (class), có các discrete possible value C1,...CK Và f(𝐱|Ck) dĩ nhiên là f(𝐱|C=Ck), tức, dựa trên event C=Ck thì pdf tại 𝐱 là gì.
>
>
>
> Để khỏi bối rối cái này mình cần nhớ lại định nghĩa cũng như ý nghĩa của conditional probability: P(A|B) = P(A,B)/P(B).
>
>
>
> Event A có bản chất là tập hợp: các possible outcome trong original sample space thuộc event A: A = {s ∈ Ω: s ∈ A}. Nên xét xác suất của event A, thực chất là xác suất của một tập hợp các s này: P(A) = P({s ∈ Ω: s ∈ A}) = Σ\_{s ∈ Ω: s ∈ A} P({s}). Và ta nhớ axiom 1 của probability theory nói rằng P(Ω) = 1.
>
>
>
> Thế thì khi xét xác suất của event A conditioned on B, tức là lúc này B đã xảy ra, thì ta sẽ xét tập những possible outcome thuộc B và A: Tức là (A, B) = {s ∈ B: s ∈ A}. Và xác suất của nó là P(A,B) = P({s ∈ B: s ∈ A}).
>
>
>
> Vấn đề là, nếu chỉ tính P(A|B) = P(A ∩ B) thì sẽ không hợp lệ. Lí do vì theo axiom của lí thuyết xác suất: P({s ∈ Ω}) = 1, nên lúc nếu sample space bây giờ chỉ còn là B, thì P(B) = P({s ∈ B}) = Σ\_{s ∈ B} P({s}) không bằng 1.
>
>
>
> Thành ra, để hợp lệ, P({s}) phải được scale bởi constant c để trở thành P'({s}) thỏa Σ{s ∈ B} P'({s}) = 1
>
>
>
> ⇔ Σ\_{s ∈ B} P({s}) c = 1
>
>
>
> ⇔ c Σ\_{s ∈ B} P({s}) = 1
>
>
>
> ⇔ c P(B) = 1
>
>
>
> ⇔ c = 1/P(B)
>
>
>
> Như vậy, P(A|B) = P({s ∈ B: s ∈ A}) = Σ\_{s ∈ B: s ∈ A} P'({s})
>
>
>
> = Σ\_{s ∈ B: s ∈ A} \[P({s})/P(B)\]
>
>
>
> = \[1/P(B)\] Σ\_{s ∈ B: s ∈ A} P({s}
>
>
>
> = \[1/P(B)\] P(A|B)
>
>
>
> = P(A|B)/P(B)
>
>
>
> Thế thì cũng như lập luận trên khi ta đã hiểu P(A|B) mang ý nghĩa là **khi B đã xảy ra thì sample space thu lại chỉ còn các possible outcome của B**, thì ở đây f(𝐱|C=Ck) cũng có ý nghĩa tương tự, do đó nếu f(𝐱) là K/NV thì f(𝐱|Ck) = Kk/(Nk×V) với ý nghĩa là ta **áp dụng công thức** K/NV **cho những data point thuộc class k thôi, bỏ hết các data point khác**. Nên Kk = **chỉ xét những điểm data thuộc class k, và sau đó trong số chúng, bao nhiêu điểm nằm trong phạm vi của** 𝐱. Và Nk là **số data point thuộc class k**
>
>
>
> (Ôn nhanh về K trong lập luận gốc, khi ta derive ra công thức f(𝐱) ≈ K/VN, thì K = Σi {I\_(𝐗i ∈ R}, với I\_(𝐗i ∈ 𝐑), hay I\_(𝐗i ∈ R(𝐱) là indicator function, gắn với event 𝐗i ∈ R(𝐱), mang giá trị bằng 1 khi 𝐗i nằm trong region lân cận 𝐱 và bằng 0 khi ngược lại. Để rồi, với việc fixed V, dùng data để tính K, ta có kernel density approach, trong đó ta có thể dùng hàm Parzen window k(u) = I\_|u ≤ 1/2| để đếm K = Σi=1:N k((𝐱i-𝐱)/h), hoặc Gaussian kernel để K = Σi=1:N \[(1/√2πh²) exp{-(𝐱-𝐱i)²/2h²}\]. Hoặc với việc fixed K, tính V từ data ta sẽ có KNN density approach)
>
>
>
> Vậy thì, tiếp theo với f(𝐱) = K/VN, ta sẽ dùng Bayes theorem:
>
>
>
> f(Ck|𝐱) = f(𝐱|Ck)f(Ck)/f(𝐱)
>
>
>
> f(Ck), tạm gọi là prior distribution của random variable C, evaluate tại Ck (là một discrete variable), sẽ tính bằng Nk/N tức số observed data thuộc class k / tổng số observed data.
>
>
>
> ⇨ f(Ck|𝐱) = f(𝐱|Ck)f(Ck)/f(𝐱) = (Kk/VNk) (Nk/N) / (K/VN)
>
>
>
> = Kk / K → 2.256

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **93/100** · ✓ Move on</summary>

Bạn đã nắm vững cách áp dụng kỹ thuật KNN cho bài toán phân loại và suy ra công thức cuối cùng một cách chính xác. Để note ngắn gọn và tập trung hơn, bạn có thể tóm lược phần giải thích sâu về xác suất có điều kiện và đảm bảo tính nhất quán trong ký hiệu.

</details>

<br>

<a id="node-mtmr0qc"></a>

##### K-Nearest Neighbor Classification

<p align="center"><kbd><img src="assets/mwwztw97q7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/iswbyvvfra.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì gs nói, với giá trị posterior f(Ck|𝐱) như vừa rồi (mình hiểu nó là hàm conditional pmf P(C=Ck|𝐗=𝐱) được estimate dựa trên KNN density approach) thì để có được một decision rule giảm thiểu mis-classificate rate, thì cái rule đó sẽ là: assign class k có f(Ck|𝐱) lớn nhất, tức Kk/K
>
>
>
> Dù nghe có vẻ hiển nhiên, như vì sao? → Cái này trong chap 1 đã học rồi (Xem link) và thực chất, hiểu sâu hơn kết nối với kiến thức Casella đây chính là decision rule giúp giảm thiểu Bayes risk:
>
>
>
> **CHỌN RA CÁI NÀO NHỎ NHẤT TRONG ĐÁM**: {Σk=1:K Lk1 f(x, Ck), Σk=1:K Lk2 f(x, Ck), ..Σk=1:K LkK f(x, Ck)} sau đó **LẤY INDEX** ĐỂ GÁN CLASS cho data point 𝐱.
>
>
>
> Và trong bài toán này, ta cho loss là như nhau (hệ số misclassification error là như nhau, tức coi như L = 1 hết), và f(𝐱, Ck) = f(Ck|𝐱)f(𝐱), nên so f(Ck|𝐱) cũng là so sánh f(Ck, 𝐱).
>
>
>
> Như vậy phân tích thì dài dòng chứ cuối cùng cái rule rất đơn giản: Xem trong K điểm data gần nhất với 𝐱, thì class k nào chiếm đa số thì dùng class đó để assign cho 𝐱
>
>
>
> Và khi K = 1, ta gọi nó là nearest neighbor: xem thằng gần nhất thuộc class gì thì kết luận class đó.

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **92/100** · ✓ Move on</summary>

Ghi chú thể hiện sự hiểu biết sâu sắc về mối liên hệ giữa KNN, xác suất hậu nghiệm và rủi ro Bayes, đặc biệt là trong trường hợp lỗi phân loại đồng đều. Tuy nhiên, việc trình bày công thức rủi ro Bayes có thể được làm rõ hơn để tránh sự nhầm lẫn về ký hiệu.

</details>

**🔗 See also:** [Luật quyết định Bayes tối ưu](./15_decision_theory.md#node-ym5yp89)

<br>

<a id="node-2ctjqyp"></a>

###### Figure 2.28 K-nearest-neighbour Algorithm

<p align="center"><kbd><img src="assets/2b9kzbbe9ua.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sm7yaovznfq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qjvdub8ryx.png" width="80%"></kbd></p>

> [!NOTE]
> Một ví dụ minh họa K thay đổi làm thay đổi độ mượt của decision boudary.
>
>
>
> Cuối cùng, đại ý gs nói là, cái này, tức KNN density estimator cũng như kernel density estimator đều không cần phải training gì hết, nhưng ta phải lưu trữ toàn bộ data, khiến sẽ là một hạn chế rất đáng kể khi data lớn.
>
>
>
> Và ông nói, tuy rằng bằng các thuật toán tree-based search ta có thể giúp tìm kiếm nearest neighbor nhanh, nhưng bản chất, nó vẫn rất hạn chế.
>
>
>
> Bên cạnh đó, chưa kể, ta đã thấy nó có nhiều vấn đề trong việc estimate distribution. Thành ra trong các chapter sau, ta sẽ bàn đến các cách tiếp cận khác, flexible hơn, với độ phức tạp có thể được kiểm soát một cách độc lập với kích thước training set.

<details>
<summary>🤖 AI Check — 🟢 Pass — ✅ **95/100** · ✓ Move on</summary>

Ghi chú này rất toàn diện và nắm bắt chính xác tất cả các điểm cốt lõi từ văn bản gốc, từ ví dụ minh họa về K đến các hạn chế của phương pháp. Để tăng thêm độ sâu, bạn có thể giải thích rõ hơn về bản chất 'không cần huấn luyện' của KNN liên quan đến việc nó là một phương pháp phi tham số.

</details>

<br>

