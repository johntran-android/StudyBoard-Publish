# 1.5 Decision Theory

📊 **Progress:** `29` Notes | `41` Screenshots

---
<a id="node-0es6zw7"></a>

<br>

<a id="node-ugcaq47"></a>

## Lý thuyết Quyết định và Bất định

<p align="center"><kbd><img src="assets/js3jr5b4eqq.png" width="80%"></kbd></p>

> [!NOTE]
> Mở đầu gs cho biết ta đã thấy trong những phần trước lí thuyết xác suất đã
> cung cấp cho ta một framework để định lượng và thao tác với tính
> uncertainty. Thì nay, kết hợp với decision theory, sẽ cho ta một công cụ để
> giúp đưa ra  những quyết định hợp lí trong bối cảnh uncertainty

<br>

<a id="node-keqwbdj"></a>

### Suy diễn thống kê

<p align="center"><kbd><img src="assets/ffy6lygz9ov.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, giả sử ta có input vector 𝐱, tương ứng là vector 𝐭, và mục
> đích là dự đoán t từ new value x. Thì với bài toán regression, t sẽ là biến
> liên tục. còn classification, t sẽ là class label.
>
>
>
> Khi đó joint probability của 𝐗,𝐓 (ở đây mình cứ theo quy tắc Casella,
> biến thì viết hoa, cũng như xài chữ f cho quen thuộc) f(𝐱,𝐭) sẽ phản
> ánh toàn diện mọi tính uncertainty gắn với các random variables này. Và
> bài toán đi xác định phân phối xác suất của 𝐗,𝐓 được gọi là
> **INFERENCE**.
>
>
>
> Có thể hiểu ý này, vì xuyên suốt cuốn Statistical Inference của Casella,
> mình chính là deal với bài toán này: cho random sample X = (X1,...Xn) ~
> f(𝐱|θ) thì mục tiêu của ta là suy đoán giá trị của θ, tham số chi phối phân
> phối xác suất của 𝐗, và 3 bài toán lớn là
>
>
>
> i) point estimation - tìm cách đưa ra một function của sample W(𝐗) sao
> cho với giá trị quan sát 𝐗 = 𝐱 thì ta có một estimate W(𝐱) cho θ.
>
>
>
> ii) hypothesis testing - tìm cách đưa ra một nhận định rằng θ ∈ Θ0 hoặc θ ∈
> Θ0c, và cụ thể là đi xây dựng một rejection region R = {𝐱: reject H0}
> cũng  chính là một hypothesis test, có bản chất là một decision rule: nhận
> vào 𝐱, tính toán giá trị của test statistic và dùng nó để quyết định xem
> nên tuyên bố θ ∈ Θ0 hay Θ0c.
>
>
>
> iii) interval estimator - tìm cách xây dựng một random interval hay khái quát
> hơn là random set C(𝐗) để khi quan sát 𝐗 = 𝐱 ta sẽ đưa ra một
> nhận định là θ ∈ C(𝐗)
>
>
>
> Quay lại đây, gs Bishop cho rằng đây vốn là bài toán rất khó, và sẽ là chủ
> đề xuyên suốt của cuốn sách này. Tuy nhiên, trong những bài toán thực tế,
> ta thường muốn dự đoán t dựa trên giá trị của x hoặc rộng hơn, mục đích
> của ta thường là đưa ra một hành động tốt nhất dựa trên giá trị mà t có khả
> năng cao nhất dựa trên input x

<br>

<a id="node-pnlj8xg"></a>

#### Lý thuyết quyết định y khoa

<p align="center"><kbd><img src="assets/kdzb3izwnoj.png" width="80%"></kbd></p>

> [!NOTE]
> Lấy ví dụ bài toán y khoa, ta muốn dựa trên input x là vector các giá trị điểm
> ảnh của ảnh chụp x quang, để dự đoán t mang một trong hai giá trị 0 hoặc 1
> để đại diện là C1 và C2 là tên hai class: có bị ung thư hay không bị. Thì ở
> đây nếu ta tìm được phân phối xác suất f(𝐱, t) hay f(𝐱, Ck)
>
>
>
> (chỗ này mình nghĩ ông gs Bishop làm cho rách việc ra thêm bằng cách
> dùng kí hiệu Ck, mình cho là cứ dùng t cũng được, chỉ cần biết nó là
> discrete mang hai  possible value 0 hoặc 1 thôi. Vốn dĩ việc ổng thoát li khỏi
> quy ước kí hiệu bên toán như xài chữ p thay cho f, viết thường cho tên biến
> thay vì viết hoa vốn đã gây dễ lú rồi. Nên ở đây mình sẽ cứ dùng t, f, và tuân
> theo quy ước viết hoa cho tên biến)
>
>
>
> thì đó chính là bài toán inference, tuy nhiên sau hết, mục đích vẫn là đưa ra
> quyết định là làm gì tiếp theo, thì đây chính là địa hạt của decision theory, nó
> sẽ giúp ta đưa ra quyết định tối ưu dựa trên xác suất tính toán được.
>
>
>
> Và gs cho biết thường thì bước make decision sẽ tương đối đơn giản một
> khi ta đã giải được bài toán inference.

<br>

<a id="node-mnh7wrs"></a>

##### Quyết định dựa trên Xác suất

<p align="center"><kbd><img src="assets/4bcy15y6f28.png" width="80%"></kbd></p>

> [!NOTE]
> Trước đi đi vào phân tích chi tiết, ta sẽ xem xét một cách không chính thức
> làm cách nào để ta thấy rằng xác suất sẽ đóng vai trò giúp ta quyết định
> thông qua ví dụ dễ hiểu.
>
>
>
> Như nãy đã nói, trong bối cảnh bài toán ta muốn dựa trên tấm ảnh chụp 
> x quang để đưa ra dự đoán bệnh hay không bệnh. Thì ta sẽ muốn xem
> xét f(t|𝐱) 
>
>
>
> Theo Bayes theorem: f(t|𝐱) = f(𝐱|t) f(t) / f(𝐱)
>
>
>
> Y như trong Bayesian approach ta coi θ là random variable để gán cho nó
> prior distribution π(θ), và dựa vào Bayes theorem để cập nhật xác suất
> của θ dựa trên 𝐗 = 𝐱, để có posterior distribution π(θ|𝐱). Thì ở đây, f(t)
> (trong sách là p(Ck) cũng sẽ là prior distribution của T, và f(t|𝐱) là posterior
> distribution, với ý nghĩa là:
>
>
>
> Khi chưa biết kết quả x-ray thì xác suất một người mắc bệnh (T mang giá
> trị gì) sẽ được quy định bởi prior distribution f(t).
>
>
>
> Nhưng sau khi có x-ray thì xác suất của T sẽ do f(t|𝐱) quyết định.
>
>
>
> Như vậy, để giảm thiểu khả năng phán bệnh sai, lẽ thường ta sẽ dùng
> kết quả của posterior distribution, là trong hai giá trị khả dĩ của T, thì cái
> nào có posterior probability cao hơn.
>
>
>
> Vậy thì ở đây, tính được f(t, 𝐱) coi như là bài toán inference, khi đó, ta
> sẽ tính được f(t|𝐱) và việc lấy giá trị nào có posterior cao hơn để gán / báo 
> cho bệnh nhân chính là bước dựa vào decision theory để take action

<br>

<a id="node-xhvr2pu"></a>

###### Giảm thiểu tỉ lệ phân loại nhầm

<p align="center"><kbd><img src="assets/jzfufhvi8ob.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đại ý là nếu như mục tiêu của ta là giảm thiểu tỉ lệ phân loại nhầm
> (misclassification rate) thì ta sẽ cần một bộ quy tắc để gán giá trị cho của 𝐱 cho
> một trong các class đang xét.
>
>
>
> Trước khi nói tiếp, mình tranh thủ recall lại kiến thức trong Casella: Hypo thesis
> testing:
>
>
>
> Như lúc nãy cũng đã review lại sơ sơ: Bài toán hypothesis testing là bài toán suy
> luận thống kê mà trong đó ta muốn xây dựng một cái hypothesis test - có bản
> chất chỉ là một decision rule: dựa vào gía trị quan sát của 𝐗, tính toán ra test
> stastisic λ(𝐗) và theo một cái rule nào đó để đưa ra kết luận rằng H0: θ ∈ Θ0,
> gọi là accept null hypothesis, hay kết luận H1: θ ∈ Θ0c gọi là reject null
> hypothesis.
>
>
>
> Thế thì, như vậy việc định ra một cái test, cũng chính là định ra cái rule, để rồi áp
> dụng cái rule này với mọi 𝐱 ∈ range 𝐗, nó sẽ chia range 𝐗 thành hai
> phần, Rejection region R = {𝐱 ∈ range 𝐗: reject H0} và Rc = {𝐱 ∈ range
> 𝐗: accept H0}, gọi là Acceptance region.
>
>
>
> Để rồi, khi đó, khi bàn tới việc đánh giá một hypothesis test, ta sẽ muốn giảm
> thiểu hai loại sai sót: Type I error, là khi θ ∈ Θ0 nhưng lại reject H0 (𝐗 ∈ R), và
> Type II error, là khi θ ∈ Θ0c nhưng lại accept H0 (𝐗 ∈ Rc).
>
>
>
> Để rồi từ đó ta có các khái niệm như power function: β(θ) = P_θ(𝐗 ∈ R), với
> định nghĩa này, ta sẽ muốn một cái test có Type I error thấp thì có nghĩa là với θ ∈
> Θ0 β(θ) nên thấp, từ đó ta có định nghĩa level α test là test mà:
>
>
>
> sup_θ∈Θ0 P_θ(𝐗 ∈ R) ≤ α.
>
>
>
> Và định nghĩa size α test, là test có sup_θ∈Θ0 P_θ(𝐗 ∈ R) = α.
>
>
>
> Và khi đã xét một đám có xác suất Type I error thấp, ví dụ leve α test.
>
>
>
> Ta sẽ muốn tìm thằng có xác suất mắc Type II error thấp nhất trong đó, cũng là
> thằng mà khi θ ∈ Θ0c thì xác suất reject H0 là cao nhất mọi thằng khác, đó chính
> là most power level α test, với power function chính là định nghĩa bởi β(θ) =
> P_θ(𝐗 ∈ R): một test gọi là most power trong các test level α là khi với mọi θ ∈
> Θ0c, thì β(θ) của nó luôn ≥ β'(θ) của mọi test khác trong đám đó.
>
>
>
> Review chút xíu cho nhớ, giờ quay lại bài toán này.
>
>
>
> ------
>
>
>
> Để thực hiện bước phân loại, ta cũng sẽ muốn một cái decision rule, cũng  giống
> như hypothesis test, ta cũng sẽ cần một cái function, để nhận vào x, và trả ra kết
> quả là predict là class nào. Khi đó nó cũng sẽ chia range X thành các vùng, gọi là
> DECISION REGIONS
>
>
>
> (không nhất thiết phải là 2 vùng rejection region R và decision region R, mà tùy
> vào số possible class / cũng là số possible values của T, nhưng ở đây thì đúng là
> có 2 vùng, vì T có 2 possible values, gọi là R1, và R2)
>
>
>
> Và biên giới phân tách các decision regions gọi là DECISION BOUNDARY.
>
>
>
> Thế thì khi nói về event "mắc sai lầm / phân loại sai", nếu trong bối cảnh bài toán
> Hypothesis testing, thì nó sẽ là:
>
>
>
> (θ ∈ Θ0, reject H0) hoặc (θ ∈ Θ0c, accept H0)
>
>
>
> cũng là (θ ∈ Θ0, 𝐗 ∈ R) hoặc (θ ∈ Θ0c, 𝐗 ∈ Rc)
>
>
>
> Tương tự, ở đây, một event "phân loại sai" sẽ là:
>
>
>
> (T = C1, phân loại C2) hoặc (t = C2, phân loại C1)
>
>
>
> cũng là (T = C1, 𝐗 ∈ R2) hoặc T = C2, 𝐗 ∈ R1)
>
>
>
> Thế thì xét xác suất của event "mắc sai lầm" này, ta sẽ thấy.
>
>
>
> Với bài toán hypothesis testing, phải chú ý rằng, vì theo Frequentist approach, ta
> không coi θ như random variable, cho nên xác suất mắc Type 1 Error không phải
> là P_θ(θ ∈ Θ0, 𝐗 ∈ R) mà phải define là P_θ(𝐗 ∈ R) khi θ ∈ Θ0, mang ý
> nghĩa: Khi giá trị của θ, vốn là fixed và unknown, thật sự là ∈ Θ0 thì P_θ(𝐗 ∈ R)
> chính là xác suất mắc Type I error. (vì sao có chữ θ ở dưới P: P_θ(...) thì là vì
> 𝐗 ~ f(𝐱|θ) nên dĩ nhiên xác suất này phụ thuộc θ)
>
>
>
> Tương tự, xác suất mắc Type II error sẽ được định nghĩa là:
>
>
>
> P_θ(𝐗 ∈ Rc) khi θ ∈ Θ0c.
>
>
>
> Nhưng với bài toán này, vì 𝐗 và T đều là random variable / random vectors,
>
>
>
> (Chú ý, 𝐗 là random vectors, nên trong sách gs Bishop dùng bold font, nhưng
> như đã nói ông ko theo convention nữa, nên viết chữ thường (vẫn in đậm, nhưng
> chữ thường 𝐱) còn mình thì theo convention của Casella, nên in đậm, chữ hoa
> 𝐗)
>
>
>
> nên xác suất của event mắc sai lầm sẽ là:
>
>
>
> P[(T = C1, 𝐗 ∈ R2) or (T = C2, 𝐗 ∈ R1)]
>
>
>
> = P[(T = C1, 𝐗 ∈ R2) U (T = C2, 𝐗 ∈ R1)]
>
>
>
> Đây là union của hai disjoint event, nên theo axiom 2 của lí thuyết xác suất, ta
> tách nó thành tổng của:
>
>
>
> = P(T = C1, 𝐗 ∈ R2) + P(T = C2, 𝐗 ∈ R1)
>
>
>
> Và đây là xác suất của joint event liên quan đến T, và 𝐗, nên ta sẽ dùng thể
> hiện nó / tính toán nó bởi joint distribution của T và 𝐗:
>
>
>
> f(t,𝐱) | t=C1, 𝐱∈R2 + f(t,𝐱) | t=C2, 𝐱∈R1
>
>
>
> Để thấy bước tiếp theo quen thuộc ta nhớ trong Casella hay Stat110, khi xét joint
> distribution của X,Y f(x,y), và xét xác suát của event X ∈ A, Y ∈ B, ta sẽ lấy tích
> phân ∫A∫B f(x,y)dxdy.
>
>
>
> Ở đây nó hơi lạ là đây là joint distribution của một biến discrete và một biến liên
> tục nhưng nguyên lí cũng  vậy thôi, có thể coi cái ta cần tính ở đây là xác suất của
> event T ∈ {C1}, 𝐗 ∈ R2 **⇨** ∫{C1}∫R2 f(t, 𝐱)d𝐱 dt = ∫R2 f(C1, 𝐱)d𝐱
>
>
>
> nên ta có:
>
>
>
> ∫R2 f(C1,𝐱)d𝐱 + ∫R1 f(C2,𝐱)d𝐱

<br>

<a id="node-6papqg6"></a>

###### Tối ưu hóa vùng quyết định

<p align="center"><kbd><img src="assets/jqtwov9vxyd.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/69517zqjbhb.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, cùng tìm hiểu sao ông Bishop nói dễ thấy là cái rule mà sẽ giúp ta giảm thiểu
> xác suất mistake này sẽ là cái rule sau đây: gán cho 𝐱 cái class nào mà f(𝐱,
> Ck) nhỏ hơn. Ví dụ nếu f(𝐱, C1) < f(𝐱, C2) thì kết luận C2, ngược lại thì kết luận C1.
>
>
>
> Mình sẽ nhìn bài toán này theo góc nhìn bài toán tối ưu hóa:
>
>
>
> nói bằng lời là:
>
>
>
> tìm cái decision rule sao cho dưới cái rule đó, xác suất sai lầm là nhỏ nhất.
>
>
>
> Vấn đề là,  với bài toán tối ưu, thì phải xác định biến tối ưu (optimization variable)  là
> gì. Thế thì ở đây, cái cần tìm là một decision rule, ko phải tìm x, y gì cả.
>
>
>
> Vậy thì cái biến tối ưu ở đây, là decision rule. Mà decision rule thì làm sao mà thể
> hiện theo toán học đây.
>
>
>
> À, như đã biết trong bài toán Hypothesis testing, nói về một cái test, hay test rule,
> thì bản chất cũng chính là nói về cái rejection region hay acceptance region. Vì một
> cái rule, sẽ gắn với cái rejection region có được khi áp cái rule đó để mà chia range
> 𝐗 thành R và Rc.
>
>
>
> Nên ở đây cũng vậy, bản chất một cái decision rule, chính là thể hiện qua  các
> decision region R1, R2. Vì tương tự như trên, mỗi một cái decision rule khác nhau
> sẽ tạo ra một bộ decision region khác nhau.
>
>
>
> Do đó bài toán tối ưu sẽ được thể hiện như sau:
>
>
>
> minimize_R1,R2 {∫R2 f(C1,𝐱)d𝐱 + ∫R1 f(C2,𝐱)d𝐱}
>
>
>
> (chỗ này vì X là vector nên ta phải hiểu đây là tích phân đa biến ∫...∫ nếu ghi
> chặt chẽ theo toán học, chỉ là ghi ∫ cho gọn, cũng như range 𝐗 đây là subset của Rⁿ
> chứ ko phải R)
>
>
>
> Tuy nhiên, R1,R2 sẽ có ràng buộc: R1 U R2 = range 𝐗, và R1, R2 disjoint:  R1 ∩
> R2 = ∅
>
>
>
> Nhưng tích phân trên miền R2, có thể được tách thành tích phân trên toàn miền trừ
> tích phân trên miền R1: ∫R2 f(C1,𝐱)d𝐱 = ∫{Range 𝐗} f(C1,𝐱)d𝐱 - ∫R1
> f(C1,𝐱)d𝐱
>
>
>
> Và xét cái này ∫{Range 𝐗} f(C1,𝐱)d𝐱, Ta biết là marginalizing joint pdf/pmf
> của 𝐗, T trên toàn miền xác định của 𝐗 ta sẽ được marginal pdf/pmf của T.
>
>
>
> Do đó ∫{Range 𝐗} f(C1,𝐱)d𝐱 chính là f(t)|t=C1, tức prior distribution của T,
> evaluate tại t = C1
>
>
>
> Vậy bài toán tối ưu lúc này là:
>
>
>
> minimize_R1 {f(C1) - ∫R1 f(C1,𝐱)d𝐱 + ∫R1 f(C2,𝐱)d𝐱} = {f(C1) + ∫R1 [f(C2,
> 𝐱) - f(C1,𝐱)]d𝐱 }
>
>
>
> Và f(C1) thì ko phụ thuộc R1, nên ta chuyển thành bài toán tương đương:
>
>
>
> minimize_R1 { ∫R1 [f(C2,𝐱) - f(C1,𝐱)]d𝐱 }
>
>
>
> Đến đây, nói bằng lời, ta muốn tìm R1, sao cho minimize cái tích phân này
>
>
>
> Nếu là bối cảnh bài toán tối ưu với biến 𝐱 thông thường, có lẽ tới đây mình sẽ dùng
> first order necessary condition để tìm 𝐱 khiến gradient = 0, để ra critical point rồi xét
> phép thử bậc hai các kiểu.
>
>
>
> Còn ở đây, biến tối ưu lại là một cái region, vậy phải làm sao?
>
>
>
> Ta sẽ dựa vào lập luận: mục đích là tìm vùng R1 sao cho minimize tích phân này.
> Mà bản chất tích phân này là tổng: tổng các giá trị [f(C2,𝐱) - f(C1,𝐱)] trên miền
> R1 ∈ range 𝐗
>
>
>
> Nên có thể diễn dịch yêu cầu là tìm trong miền 𝐗, để nhặt ra, gom lại những
> giá trị 𝐱 nào đó sao cho tổng [f(C2,𝐱) - f(C1,𝐱)] trên tập đó là nhỏ nhất.
>
>
>
> Để làm được điều này, về trực giác, ta sẽ chọn các 𝐱 khiến cái cụm này âm, thì
> khi đó, tổng của một đám mang giá trị âm mới khiến đẩy giá trị ngày càng nhỏ
> lại.
>
>
>
> Và ta cũng chỉ có thể lập luận như vậy, để kết luận R1 tối ưu nên là tập các 𝐱 ∈ range 𝐗
> sao cho [f(C2,𝐱) - f(C1,𝐱)] < 0 ⇔ f(C2,𝐱) < f(C1,𝐱).
>
>
>
> Nhờ vậy giúp ta hiểu vì sao gs Bishop nói vậy trong đoạn này. (ông nói clearly
> nhưng mình thấy chả clearly chút nào nếu ko phân tích như trên).
>
>
>
> Vậy optimal decision rule (theo tiêu chí minimize misclassification rate) là:
>
>
>
> Assign class C1 nếu f(C2,𝐱) < f(C1,𝐱) và ngược lại.
>
>
>
> Và cũng dễ hiểu rằng vì f(t,𝐱) = f(t|𝐱)f(𝐱) **⇨** f(C2,𝐱) = f(C2|𝐱)f(𝐱)
>
>
>
> và f(C1,𝐱) = f(C1|𝐱)f(𝐱)
>
>
>
> nên decision rule tối ưu cũng là: Assign class C1 nếu f(C2|𝐱) (tức posterior pdf
> tại C2) < f(C1|𝐱)

<br>

<a id="node-oaenu4z"></a>

###### Giảm thiểu lỗi phân loại

<p align="center"><kbd><img src="assets/kjgaatltwb8.png" width="80%"></kbd></p>

> [!NOTE]
> Minh họa bằng hình ảnh này. Vẽ đồ thị của hàm f(C1, 𝐱) và f(C2, 𝐱) theo 𝐱.
>
>
>
> Mình phải nói trước: hình ảnh chỉ nên hiểu mang tính minh họa, vì 𝐱 vốn
> đang là vector, ko thể thể hiện nó trên 1 trục như vậy được, hay nói cách
> khác, ở đây coi như 𝐱 chỉ là vector 1-D, do nên ta thấy gs Bishop dùng
> kí hiệu x thường (ko phải x bold: 𝐱 như trong phần trước)
>
>
>
> Xác suất của event "phân loại" sai, như vừa phân tích được tính bởi
>
>
>
> P(Mistake) = ∫R1 f(C2,x) dx + ∫R2 f(C1,x)dx
>
>
>
> Và dĩ nhiên như đã học trong MIT 1801, ý nghĩa của tích phần ∫a:b f(t)dt là
> diện tích của phần đồ thị bên dưới hàm f(t) từ a đến b.
>
>
>
> Nên (Mistake) là tổng diện tích của phần đồ thị hàm f(C2,x) với x ∈ R1 và
> diện tích của phần đồ thị hàm f(C1,x) với x trong R2. chính là phần xanh
> đỏ và xanh  lá
>
>
>
> Và bài toán đặt ra là tìm R1, R2 giúp minimize cái tổng diện tích này, và
> điều này đồng nghĩa nhích cái decision boundary tại x^ qua lại.
>
>
>
> Thế thì đại ý rất dễ thấy đó là, khi dịch chuyển cái x^, thì tổng diện tích
> vùng  xanh lá, xanh dương ko đổi. Nó chỉ thay đổi diện tích vùng đỏ. Và tại
> x^ = x0 thì diện tích vùng đỏ là nhỏ nhất (= 0), đó chính là nơi mà từ tại đó,
> ta có optimal decision rule:
>
>
>
> Assign C1 nếu f(C2|x) < f(C1|x) và ngược lại.
>
>
>
> Có nghĩa là cái optimal rule sẽ là: Assign C1 nếu x < x0 và ngược lại.

<br>

<a id="node-11mro6g"></a>

###### Phân loại Bayes K lớp

<p align="center"><kbd><img src="assets/lcinhi9o1rb.png" width="80%"></kbd></p>

> [!NOTE]
> Nói qua khái quát bài toán lên K classes thay vì 2 classes, ông cho rằng sẽ
> dễ hơn nếu ta đặt objective cho việc tìm rule tối ưu là maximize xác suất
> phân loại đúng thay vì minimize xác suất phân loại sai.
>
>
>
> Là sao? À đơn giản là vì đây là hai event disjoint và bù nhau, nên P("mistake"
> ) = 1 - P(" correct"). Mà với bài toán tối ưu thì ta biết rồi, minimize hàm f(x) thì
> cũng là maximize hàm -f(x). Đo đó, minimize P("mistake") tương đương
> maximize
> \- P("mistake"), và cũng tương đương maximize 1 - P("mistake") (cộng hằng
> số vào objective thì cũng được bài toán tương đương), và đây chính là
> maximize P("correct")
>
>
>
> Như vậy minimize P("mistake") cũng chính là maximize P("correct")
>
>
>
> Nhưng vì sao maximize P("correct") lại dễ hơn.
>
>
>
> Là vì, event "correct" dễ định nghĩa hơn event "mistake" trong trường hợp có
> nhiều classes.
>
>
>
> Ví dụ có K classes, dĩ nhiên event correct sẽ là:
>
>
>
> ([T = C1, decision rule phán là C1] hoặc [T = C2, decision rule phán là C2] ..
>
>
>
> hoặc [T = CK, decision rule phán là CK])
>
>
>
> viết theo toán học gọn hơn thì sẽ là:
>
>
>
> "Correct" = (T = C1, 𝐗 ∈ R1) hoặc (T = C2, 𝐗 ∈ R2) ,...(T = CK, 𝐗 ∈
> Rk)
>
>
>
> ⇨ P("Correct") = P[(T = C1, 𝐗 ∈ R1) U (T = C2, 𝐗 ∈ R2) U...U( T = CK,
> 𝐗 ∈ Rk)]
>
>
>
> tương tự, đây là union của các disjoint events nên theo axiom 2 (hay 3 nếu
> theo sách Casella)
>
>
>
> .. = P[(T = C1, 𝐗 ∈ R1) + P(T = C2, 𝐗 ∈ R2) +...+ P(T = CK, 𝐗 ∈ Rk)]
>
>
>
> và tương tự như hồi nãy, nó chính là ∫R1 f(C1,𝐱)d𝐱 + ...∫RK f(CK,
> 𝐱)d𝐱
>
>
>
> = Σk=1:K ∫Rk f(Ck,𝐱)d𝐱
>
>
>
> Và tương tự như khi K = 2, cái decision rule khiến maximize P("correct") có
> thể đoán được cũng sẽ chính là cái rule này: Assign class Ck nếu joint  pdf
> f(Ck, 𝐱) và cũng là posterior pdf f(Ck|𝐱) là cao nhất trong các k = 1,..K
>
>
>
> =====
>
>
>
> Vậy ở đây giúp ta hiểu sâu hơn như sau: Nếu tiêu chí của ta, mục tiêu của
> ta là giảm thiểu tỉ lệ sai xót tổng thể, thì cách phân loại tốt nhất chính là
> dựa trên posterior probability

<br>

<a id="node-1uqmzls"></a>

###### Phân loại và ưu tiên lỗi

<p align="center"><kbd><img src="assets/i2en93qrj8n.png" width="80%"></kbd></p>

> [!NOTE]
> Qua đây, đại ý là, trong nhiều trường hợp, mục tiêu không đơn giản chỉ là
> giảm tỉ lệ sai sót nói chung.
>
>
>
> Quay lại ví dụ việc xác định bệnh nhân có bệnh hay không, đôi khi hai
> loại lỗi nó có mức độ hậu qủa khác nhau. Ví dụ như không có ung thư mà
> phán là có, thì có thể cùng lắm là khiến bệnh nhân lo lắng và xét nghiệm
> thêm các kiểu tốn tìền. Nhưng nếu có ung thư mà chẩn đoán là không thì
> người ta có thể sẽ chết vì không được chữa trị.
>
>
>
> Lúc này, mục tiêu của ta có thể là ưu tiên loại error thứ hai, chấp nhận
> error thứ nhất (ý là nếu so sánh performance của các quy trình chẩn đoán
> thì có thể ưu tiện chọn cái có tỉ lệ error thứ hai nhỏ nhất, dù error thứ nhất
> nó ko phải là nhỏ nhất)
>
>
>
> Lại liên hệ nó với hypothesis testing cho vui. Mình đã review lại một ít
> trong các note trước, rằng trong bài toán này, ta cũng sẽ có hai loại error:
> Type I error, là khi θ thật sự thuộc Θ0, nhưng lại kết luận là reject H0, hay
> 𝐗 ∈ R và Type II error là khi θ ∈ Θ0c mà lại kết luận là accept H0: 𝐗
> ∈ Rc.
>
>
>
> Thì còn nhớ, trong sách Casella, ta đã nghe là, trong thực tế, người ta sẽ
> dành Type I error để chỉ lại sai lầm mà ta muốn  tránh bằng mọi giá, ưu
> tiên tránh, vì mang lại hậu quả lớn. Ví dụ như trong nghiên cứu thuốc
> mới, nếu thuốc gây tác dụng phụ nguy hiểm mà kết quả test lại kết luận
> thuốc không có tác dụng phụ gì, thì hậu quả sẽ rất lớn. Do đó, ta sẽ đặt
> H0: θ ∈ Θ0 ứng với: Thuốc có tác dụng phụ. Để rồi Type I error sẽ là:
> thuốc có tác dụng phụ mà lại công bố là không.
>
>
>
> Khi đó, bằng cách định nghĩa như vầy, ta sẽ tập trung xây dựng level α
> test, ví dụ level 0.001 test, theo định nghĩa, là các test có xác suất mắc lỗi
> loại I cao nhất cũng không bao giờ vượt quá 0.001.
>
>
>
> Sau đó, ta mới đi tìm trong các level 0.001 test, cái nào có xác suất mắc
> Type II error thấp nhất.
>
>
>
> Đây là một cách tiếp cận của việc đánh giá (evaluating) hypothesis test
>
> Thế thì vừa rồi mình đã ôn lại cách tiếp cận vấn đề đánh giá một hypothesis testing trong
> Casella, dĩ nhiên còn vài vấn đề khác, ví dụ như khi không tồn tại Uniformly Most Powerful
> test, rồi p-values.
>
>
>
> Recall thêm chút nữa:
>
>
>
> Trong thống kê cổ điển như cuốn Casella, mình nhớ là với Point estimator, Hypothesis
> testing, Interval estimator đều nói đến cách tiếp cận của decision theory để đánh giá (7.3.
> 4, 8.3.5, 9.3.4)
>
>
>
> Ôn lại vài khái niệm liên quan đến decision theory đã học trong phần Point estimation và
> Interval estimation Casella: Đầu tiên, đối với point estimator thì khi dẫn dắt ta về cái này,
> gs Casella nói rằng, trong decision theory, action space là không gian những action, mà áp
> vào bối cảnh point estimation thì action đó là "(đưa ra) một estimation của θ", để rồi action
> space, là tập hợp mọi estimation của θ. Thế thì, theo decision theory, một action sẽ tạo ra
> một loss, và hàm loss sẽ là hàm được định nghĩa để phản ánh mức độ nghiêm trọng của
> action. Với bài toán estimation, thì loss có thể dùng **squared error loss** L(θ, δ(𝐱)) =
> (δ(𝐱)-θ)² hoặc **absolute error loss** L(θ,δ(𝐱)) = |δ(𝐱) - θ|
>
>
>
> Và như vậy thì, với loss function, ta sẽ có một hàm số phụ thuộc θ phản ánh chất lượng
> của estimator δ(𝐗) ứng với θ cụ thể nào đó.
>
>
>
> Và để có một con số duy nhất, không phụ thuộc 𝐗, phản ánh chất lượng của estimator
> δ(𝐗) nói chung, ta sẽ định nghĩa cái gọi là risk function:
>
>
>
> R(δ(𝐗), θ) = E_θ[L(δ(𝐗), θ)], với phân tích ý nghĩa như sau:
>
>
>
> L(δ(𝐗), θ) sẽ là một random variable, vì nó là kết quả do áp một function lên δ(𝐗)
> nên phụ thuộc δ(𝐗), nên phụ thuộc 𝐗.
>
>
>
> Lấy kì vọng cái random variable này, thì tính cái này, thì ta sẽ dùng distribution của
> L(δ(𝐗),θ), mang ý nghĩa là marginalizing mọi giá trị khả dĩ của L, nên kết quả sẽ là fix,
> không còn là random variable nữa, không phụ thuộc 𝐗 nữa. nhưng nó vẫn là hàm theo
> θ.
>
>
>
> Và bằng cách tìm cái δ(𝐗) có risk nhỏ nhất với mọi θ thì ta sẽ có cái estimator tốt nhất,
> tức là minimum risk estimator.
>
>
>
> Và có thể thấy, nếu loss là squared error loss thì:
>
>
>
> R(δ(𝐗), θ) = E_θ[(δ(𝐗) - θ)²] thì đây chính là định nghĩa của hàm MSE:
>
>
>
> MSE củan estimator W(𝐗), define bởi: MSE(W(𝐗),θ) = E_θ[(W(𝐗) - θ)²].
>
>
>
> Từ đó, ta mới liên hệ với việc tìm estimator **minimize MSE cũng chính là tìm estimator
> minimize square error loss risk function**.
>
>
>
> Và triển khai thêm tí nữa:
>
>
>
> Dùng VarX = EX² - (EX)² ⇨ Var[W(𝐗) - θ] = E[(W(𝐗) - θ)²] - E[W(𝐗) - θ])²
>
>
>
> Do đó MSE(W(𝐗), θ) = R(W(𝐗), θ)_squared error loss = E_θ[(W(𝐗) - θ)²]
>
>
>
> = Var[Var(𝐗) - θ] + (E[W(𝐗) - θ])²
>
>
>
> = Var[Var(𝐗)] + (E[W(X) - θ])²
>
>
>
> Và E[W(𝐗) - θ] lại chính là definition của Bias(W(X), θ)
>
>
>
> ⇨ MSE(W(𝐗), θ) = Var[W(𝐗)] + [Bias(W(𝐗), θ)]²
>
>
>
> Nếu là theo trường phái Bayesian với Bayes estimator, thì từ risk function R(δ(𝐗), θ) 
> người ta sẽ lấy trung bình trên mọi possible value của θ:
>
>
>
> ∫R(δ(𝐗), θ) π(θ) dθ, đây gọi là Bayes risk
>
>
>
> Thay R(δ(𝐗), θ) = E_θ[L(δ(𝐗), θ)] = ∫_/𝐗 /L(δ(𝐱), θ) f(𝐱|θ) d𝐱 vào:
>
>
>
> Bayes risk = ∫_Θ ∫_/𝐗/ L(δ(𝐱), θ) f(𝐱|θ) d𝐱 π(θ) dθ 
>
>
>
> = ∫_Θ ∫_/𝐗/ L(δ(𝐱), θ) [f(θ|𝐱) f(𝐱)/π(θ)] / d𝐱 π(θ) dθ
>
>
>
> = ∫_Θ ∫_𝐗 L(δ(𝐱), θ) f(θ|𝐱) f(𝐱) d𝐱 dθ
>
>
>
> = ∫_𝐗 [ ∫_Θ L(δ(𝐱), θ) f(θ|𝐱) dθ ] f(𝐱) d𝐱 
>
>
>
> Thì cái ∫_Θ L(δ(𝐱), θ) f(θ|𝐱) dθ = E[L(δ, θ)|𝐗=𝐱] được gọi là **posterior expected loss**
>
>
>
> -----
>
>
>
> Sang tới interval estimator, thì lúc này loss function cần phản ánh hai thứ: độ chính xác
> (C(𝐗) chứa θ và kích thước C(𝐗). Do đó, loss sẽ là kết hợp  của một indicator
> function I_{C(𝐗) chứa θ} (= 0 khi C(𝐗) chứa và bằng 1 khi  C(𝐗) không chứa θ) và
> Size(C(𝐗)) với một tham số b giúp điều chỉnh tương quan giữa hai sub-objective này:
>
>
>
> L(C(𝐗), θ) = I_{θ ∈ C(𝐗)} + b Size(C(𝐗)), thể hiện: nếu C(𝐗) chứa θ và có size
> nhỏ thì loss sẽ nhỏ.
>
>
>
> Và ta cũng sẽ đặt ra risk function của interval estimator là kì vọng của loss này. Để rồi tìm
> cách tìm estimator mà giảm thiểu risk:
>
>
>
> R(C(𝐗), θ) = E_θ[L(C(𝐗), θ)].
>
>
>
> -----
>
>
>
> Còn với bài toán Hypothesis testing, trong 8.3.5 Casella ta được biết rằng, với bài toán
> này, action sẽ chỉ là một trong hai: a0, a1 biểu diễn kết luận của test rule là accept H0 hay
> reject H0. Và ta cũng sẽ define loss function, gọi là 1-0 loss để phản ảnh hậu quả:
>
>
>
> L(θ, a0) = 0 nếu θ ∈ Θ0, = 1 nếu θ ∈ Θ0c
>
>
>
> L(θ, a1) = 0 nếu θ ∈ Θ0c, = 1 nếu θ ∈ Θ0,
>
>
>
> Và risk cũng sẽ là function lấy trung bình loss:
>
>
>
> Chỗ này cần nói rõ cho dễ hiểu: Định nghĩa của loss, luôn gắn với một action. Với point
> estimator, loss kí hiệu là L(δ(𝐗), θ), để rồi nó là một random variable, mà khi nhận giá trị
> 𝐗 = 𝐱, kéo theo δ(𝐗) mang giá trị estimate cho θ: δ(𝐱) (là một action), kéo theo
> phát sinh loss L(δ(𝐱), **θ**) từ action này. Và vì L(δ(𝐗), θ) là random variable, nên
> risk = lấy kì vọng, chính là dựa trên distribution của cái thằng L này, và truy nguyên nguòn
> gốc thì c**ũng chỉ là xuất phát từ distribution của X**: f(𝐱|θ), do đó risk mới là hàm phụ
> thuộc θ.
>
>
>
> Tương tự, với interval estimator, thì action là một interval C(𝐱), loss L(C(𝐗), θ) cũng
> là random variable, mà yếu tố random của nó đến từ C(𝐗). Khi quan sát 𝐗 = 𝐱,
> C(𝐗) mang giá trị C(𝐱), thì nó mang ý nghĩa là một action được đưa ra: một interval
> được dự đoán sẽ chứa θ, và với action đó, phát sinh loss: L(C(𝐱), θ). Nên lấy kì vọng
> cái này để có risk, thì ta sẽ dựa trên **distribution của C(X)**, tất nhiên, C(𝐗), nếu là
> random interval, thì cũng sẽ được cấu thành bởi hai random variable L(𝐗), U(𝐗), nên
> tương tự, cũng chỉ là xuất phát từ distribution của 𝐗
>
>
>
> Còn trong hypothesis testing, action là một kết luận mang một trong hai giá trị a0 hoặc a1,
> nên ta có thể thể hiện nó bởi λ(𝐗) nào đó, là một Bernoulli random variable, để rồi khi
> quan sát 𝐗 = 𝐱, λ(𝐗) ghi nhận giá trị cụ thể λ(𝐱) (= a0 hoặc a1), loss ghi nhận
> giá trị cụ thể L(θ, λ(𝐱)) (là L(θ, a0) hoặc L(θ, a1)).
>
>
>
> Nhờ vậy, ta hiểu trong hypothesis testing, loss L(θ, λ(𝐗)) là một Bernoulli random
> variable
>
>
>
> nên khi lấy trung bình, dĩ nhiên ta sẽ dựa trên distribution của Bernoulli:
>
>
>
> R(θ, λ(𝐗)) = E_θ[L(θ, λ(𝐗)]
>
>
>
> = L(θ, a0) * P_θ[L(θ, λ(𝐗)) = L(θ, a0)] + L_θ(θ, a1) * P[L(θ, λ(𝐗) = L(θ, a1)]
>
>
>
> = L(θ, a0) * P_θ(λ(𝐗) = a0) + L_θ(θ, a1) * P(λ(𝐗) =  a1)
>
>
>
> = L(θ, a0) * P_θ(𝐗 ∈ Acceptance region Rc) + L(θ, a1) * P_θ(𝐗 ∈ Rejection region R)
>
>
>
> Và tùy vào θ ở đâu:
>
>
>
> θ ∈ Θ0 ⇨ R = 0 * P_θ(𝐗 ∈ Rc) + 1 * P_θ(𝐗 ∈ R) = β(θ)
>
>
>
> θ ∈ Θ0c = R = 1 * P_θ(𝐗 ∈ Rc) + 0 * P_θ(𝐗 ∈ R) = P_θ(𝐗 ∈ Rc) = 1 - β(θ)
>
>
>
> Cuối cùng, nếu muốn thay đổi tương quan giữa hậu quả của hai loại Type I và II error, ta
> có thể thay đổi định nghĩa của loss, gọi là generalized 1-0 loss
>
>
>
> L(θ, a0) = 0 nếu θ ∈ Θ0, = cII nếu θ ∈ Θ0c
>
>
>
> L(θ, a1) = 0 nếu θ ∈ Θ0c, = cI nếu θ ∈ Θ0,
>
>
>
> Khi đó R(θ, λ(𝐗)):
>
>
>
> Khi θ ∈ Θ0: R = cI * P_θ(𝐗 ∈ R) + 0 * P_θ(X ∈ Rc) = cI * β(θ)
>
>
>
> Khi θ ∈ Θ0c: R = cII * P_θ(𝐗 ∈ R) + 0 * P_θ(X ∈ Rc) = cII * (1 - β(θ))

<br>

<a id="node-b12udmg"></a>

###### Hàm mất mát và rủi ro Bayes

<p align="center"><kbd><img src="assets/i4bga48z0z.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/96j7nj1zgb.png" width="80%"></kbd></p>

> [!NOTE]
> Quay lại đây, trong bối cảnh machine learning, gs Bishop giới thiệu về cách tiếp
> cận decision theory: Ta sẽ dùng loss function (hay cost function) để phản ánh
> những hậu quả do các quyết định tạo ra. Thì có thể thấy nó y chang những gì đã
> học trong Casella. Chỉ khác là ta mở rộng lên K class, tức là decision rule không
> còn chỉ đưa ra một trong hai action a0 a1 nữa. Mà là a1,...aK, hay như trong
> sách, là C1,...Ck
>
>
>
> Và định nghĩa của loss, phải thể hiện bằng môt loss matrix:
>
>
>
> phần từ Lkj sẽ mang ý nghĩa là: [sự thật: T = k, decision rule gán cho class j],
> nên:
>
>
>
> khi k = j, tức là phần từ Lkk trên đường chéo, thì ta cho giá trị bằng 0: vì lúc này
> decision rule đoán đúng.
>
>
>
> còn k khác j, thì ta cho nó một giá trị dương ckj phản ảnh mức độ nghiêm trong
> của việc "đoán sai là class j trong khi thật sự là class k" này.
>
>
>
> Tất nhiên với K = 2, thì cái matrix loss này cũng chỉ cách thể hiện matrix cái hàm
> generalized loss mà ta vừa ôn trong Casella, đây nhé:
>
>
>
> Vừa nãy mới nói, ta define generalized loss:
>
>
>
> L(θ, a0) = 0 khi θ ∈ Θ0 và = cII khi θ ∈ Θ0c
>
>
>
> L(θ, a1) = 0 nếu θ ∈ Θ0c, = cI nếu θ ∈ Θ0,
>
>
>
> Thì loss matrix sẽ là:
>
>
>
> L11 = 0: phân loại đúng: θ ∈ Θ0, dự đoán a0: θ ∈ Θ0
>
>
>
> L12 = cI, thể hiện loss khi θ ∈ Θ0 và dự đoán lại là a1: θ ∈ Θ0c, đây là Type I
> error
>
>
>
> L22 = 0: phân loại đúng: θ ∈ Θ0c, dự đoán a1: θ ∈ Θ0c
>
>
>
> L21 = cII, thể hiện loss khi θ ∈ Θ0c mà dự đoán là a0: θ ∈ Θ0, đây là Type II error
>
>
>
> Nhưng lưu ý, θ **tuy đóng vai trò của** T **ở đây** nhưng **trong bối cảnh
> Casella, nó là fixed but unknown**. Do đó mới có vụ phải chia công thức của Risk
> function ra làm hai trường hợp ứng với θ nằm ở đâu.
>
>
>
> Còn **trong bối cảnh Bishop**, T **cũng là random variable**. Nên **ứng với mỗi ô
> trong loss matrix, là một joint event** của T và 𝐗.
>
>
>
> Ví dụ, ô Lkj sẽ là loss của event: T = k (class thật là j) và "mô hình phân lại là
> class j" , cũng là 𝐗 ∈ Rj
>
>
>
> Vậy thì ở đây gs Bishop chính là đang tính Bayes risk: Trong Casella, khi ta 
> xét Bayes estimator, thì ngoài risk function R(δ(𝐗), θ), người ta còn average nó,
> theo prior distribution của θ: Nghĩa là, hàm risk function, vốn dĩ đã chỉ còn phụ
> thuộc θ, vì theo trường phái Bayes, lúc này θ là random variable, nên risk function
> cũng thành random variable nốt, ta mới đi average nó, đặt là Bayes risk:
>
>
>
> Bayes risk của δ(𝐗): E[R(θ, δ(𝐗)] = ∫_Θ R(θ, δ(𝐗)) π(θ) dθ 
>
>
>
> Lắp R(θ, δ(𝐗)) = E_θ[L(δ(𝐗), θ)] = ∫_/𝐗 /L(δ(𝐱), θ) f(𝐱|θ) d𝐱 vào.
>
>
>
> Bayes risk của δ(𝐗): = ∫_Θ ∫_/𝐗/ L(δ(𝐱), θ) f(𝐱|θ) d𝐱 π(θ) dθ 
>
>
>
> Tới đây biến đổi chút xíu (thay f(𝐱|θ) = π(θ|𝐱) f(𝐱) / π(θ), ta sẽ thấy nó 
> trở thành ∫_/𝐗 /[/**∫**/_Θ L(δ(𝐱), θ) π(θ|𝐱) dθ] f(𝐱) d𝐱, trong đó ∫_Θ L(δ(𝐱), θ) π(θ|𝐱) dθ
> chính là E[L(δ(X),θ)|𝐗=𝐱], là kì vọng của loss dưới phân phối posterior: posterior
> expected loss. (hiểu nó thế này: với 𝐗 = 𝐱, L(δ(𝐗), θ) là random variable tạo bởi
> θ, và θ ~ posterior π(θ|𝐱) ⇨ lấy kì vọng, theo lotus)
>
>
>
> Nhưng nếu làm tiếp từ ∫_Θ ∫_/𝐗/ L(δ(𝐱), θ) f(𝐱|θ) d𝐱 π(θ) dθ, nhập f(𝐱|θ) π(θ)
> lại = f(𝐱, θ), ta sẽ có:
>
>
>
> ∫_Θ ∫_/𝐗/ L(δ(𝐱), θ) f(𝐱, θ) d𝐱 dθ 
>
>
>
> Đây chính là gì? **CHÍNH LÀ** **LẤY TRUNG BÌNH CỦA LOSS DỰA TRÊN
> JOINT DISTRIBUTION CỦA** 𝐗 và θ
>
>
>
> Để rồi ta sẽ thấy **CHÍNH XÁC LÀ** **NGÀI BISHOP ĐANG TÍNH BAYES RISK** (tính **kì
> vọng của loss (tổng loss) trên joint distribution của** T **và** 𝐗)

<br>

<a id="node-jfiv67u"></a>

###### Cấu trúc hàm mất mát

<p align="center"><kbd><img src="assets/4a2jgmogvng.png" width="80%"></kbd></p>

> [!NOTE]
> Từ đó giúp ta hiểu bản chất của cái công thức 1.80: chỉ là Bayes risk trong Casella mà thôi,
>
>
>
> Còn cụ thể **vì sao dạng công thức của 1.80 là như vậy?**
>
>
>
> Phải hiểu thế này: Ta đang tính kì vọng của Loss, hàm nghĩa Loss là một random variable.
>
>
>
> Mà giá trị khả dĩ (possible value) của nó, sẽ phụ thuộc T và decision rule, và ta dùng cái loss matrix để liệt kê các possible
> value này. Ví dụ,
>
>
>
> Loss = L12 khi "class thật là 1, phân loại của decision rule là 2", thể hiện toán học của event này: (T = 1, 𝐗 ∈ R2).
>
>
>
> Tượng tự,
>
>
>
> Loss = Lkj khi (T = k, 𝐗 ∈ Rj)
>
>
>
> Nên Loss, là một **DISCRETE** random variable mà được **tạo ra bởi việc áp một hàm số sau đây** lên T, và 𝐗:
>
>
>
> g(t,𝐱) = Lkj (giá trị của matrix loss tại hàng k, cột j) khi T = t, 𝐗 = 𝐱.
>
>
>
> Nói cách khác, ta hãy nhìn loss matrix chính là định nghĩa một hàm số g(t,𝐱):
>
>
>
> i) nhận vào input là t, và 𝐱, nó sẽ hỏi xem:
>
>
>
> t bằng mấy (C1 hay ...CK), ví dụ là Ck đi)
>
>
>
> 𝐱 thuộc R mấy (R1, R2 hay RK), ví dụ bằng Rj
>
>
>
> ii) output ra giá trị hàng Lkj
>
>
>
> Nên hiểu g(t,𝐱) = Lkj là như vậy.
>
>
>
> Hay g(t,𝐱) = Lkj với k là index từ 1,..K sao cho t = Ck, j là index từ 1,..K sao cho 𝐱 ∈ Rj
>
>
>
> Thể hiện theo toán học dùng **indicator function:**
>
>
>
> I_(t = Ck), có giá trị = 1 khi t = Ck, = 0 kh t ≠ Ck
>
>
>
> I_(𝐱 ∈ Rj), có giá trị = 1 khi 𝐱 ∈ Rj, = 0 khi x không thuộc Rj
>
>
>
> g(t, 𝐱) = Σk=1:K Σj=1:K Lkj I_(t = Ck) I_(𝐱 ∈ Rj)
>
>
>
> Từ đó giúp ta thấy rõ, việc tính cái kì vọng của cái biến ngẫu nhiên Loss này, đơn giản là dùng LOTUS:
>
>
>
> Nhớ lại LOTUS, nó nói rằng, khi ta có biến ngẫu nhiên Y được tạo thành bằng cách áp hàm g(x) lên biến ngẫu nhiên X, thì
> ta có thể tính EY bằng cách dùng pmf/pdf của X: EY = Σ{possible  x của X} g(x)P(X=x) hoặc ∫_{range X} g(x)f(x)dx
>
>
>
> Mà dù là tích phân hay sum thì đều có nghĩa là: marginalizing over mọi possible value của X đối với cụm g(x)f(x)
>
>
>
> Vậy thì đây, ta có LOSS, là **biến ngẫu nhiên có được bằng cách áp hàm** g(t,𝐱) lên hai biến ngẫu nhiên T, 𝐗, thì việc
> tính E[LOSS] **cũng theo LOTUS**:
>
>
>
> E[LOSS] = marginalizing mọi possible value của T và 𝐗 đối với g(t,𝐱)f(t,𝐱).
>
>
>
> Và để thực hiện cái việc marginalizing, vì ở đây T là biến rời rạc, nhận các giá trị possible value C1, C2,... CK. Còn 𝐗 là
> biến liên tục. nên công thức sẽ là:
>
>
>
> Σ_{mọi possible value Cm của T} ∫_range_𝐗 g(t, 𝐱) f(t, 𝐱) d𝐱
>
>
>
> = Σ_{mọi possible value Cm của T} ∫_range_𝐗 [Σk=1:K Σj=1:K Lkj I_(t = Ck) I_(𝐱 ∈ Rj)] f(t, 𝐱) d𝐱
>
>
>
> = Σ_{mọi possible value Cm của T} ∫_range_𝐗 [Σk=1:K Σj=1:K Lkj I_(t = Ck) I_(𝐱 ∈ Rj)] | t=Cm f(Cm, 𝐱) d𝐱
>
>
>
> Với t = Cm, [Σk=1:K Σj=1:K Lkj I_(t = Ck) I_(𝐱 ∈ Rj)] | t=Cm = [Σj=1:K Lkj I_(𝐱 ∈ Rj)]
>
>
>
> = Σ_{mọi possible value Cm của T} ∫_range_𝐗 [Σj=1:K Lmj I_(𝐱 ∈ Rj)] f(Cm, 𝐱) d𝐱
>
>
>
> = Σ_m=1:K ∫_range_𝐗 [Σj=1:K Lmj I_(𝐱 ∈ Rj)] f(Cm, 𝐱) d𝐱
>
>
>
> Tách cái tích phân trên toàn range 𝐗 thành tổng tích phân các vùng R1,... RK
>
>
>
> = Σ_m=1:K Σn=1,..K ∫_Rn [ Σj=1:K Lmj I(𝐱 ∈ Rj) ] f(Cm,𝐱) d𝐱
>
>
>
> với việc đã xét n=1,...K ở miền ngoài tích phân thì cái tổng [ Σj=1:K Lmj I_(t = Ck) I(𝐱 ∈ Rj) ] bên trong vòng lặp này chỉ
> còn [ Σj=1:K Lmj I_(t = Ck) I(𝐱 ∈ Rj) ] | j=n ] chỉ còn là [ Lmn ]
>
>
>
> = Σ_m=1:K Σn=1,..K ∫_Rn [  Lmn ] f(Cm,𝐱) d𝐱
>
>
>
> Và và vì m, n chỉ là dummy name, đặt lại tên biến là k, j ta có
>
>
>
> Σ_k=1:K Σj=1,..K ∫_Rj Lkj f(Ck,𝐱) d𝐱
>
>
>
> Đây chính là 1.80
>
>
>
> Nhờ việc hiểu bản chất Loss là biến ngẫu nhiên define bởi hàm g, thì áp dụng kiến thức LOTUS, giúp ta hiểu vì sao công
> thức E[Loss] lại là như vậy.
>
>
>
> Còn nhờ học Casella, ta hiểu thấu bản chất đây chỉ là Bayes risk mà thôi.

<br>

<a id="node-wfazk8i"></a>

###### Bayes risk và ước lượng Bayes

<p align="center"><kbd><img src="assets/4pji888h68n.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì, tiếp theo, mục tiêu sẽ làm giảm cái E[L] này, mà vừa rồi ta đã hiểu bản chất của nó chính là Bayes risks, cũng như vì sao nó có công thức như
> vậy.
>
>
>
> Lại recall liên kết với Casella chút xíu:
>
>
>
> Trong Casella, mình được nghe về khái niệm Bayes risk khi nói về việc đánh giá (evaluate) Bayes estimator của θ: δ^B(𝐗). Như đã ôn lại ở các note
> trước, risk function là function được định nghĩa bằng trung bình của loss function. R(δ(𝐗), θ) = E_θ[L(δ(𝐗), θ], nên với risk function, trước tiên ta cần
> biết đang dùng loss gì (ví dụ squared error hay absolute error). Thế thì, ta cũng nhớ, khi nói về Bayes estimator, điểm quan trọng là hiểu rằng ta đang theo
> trường phái Bayesian, nên coi θ như biến ngẫu nhiên và từ đó đi xây dựng posterior distribution của θ. Và với distribution này, khi cần một point estimator
> cho θ, ta có thể nghĩ đến mean của nó: E[θ|𝐗] Tuy nhiên, chưa chắc nó luôn là mean của posterior. Mà sự thật là: E[θ|𝐗] chỉ là Bayes estimator khiến
> minimize Bayes risk ∫_Θ E_θ[L(δ(𝐗), θ)] π(θ) dθ  với L(δ(𝐗), θ) đang dùng là squared error loss. Còn nếu loss là absolute error thì Bayes estimator khiến minimize
> Bayes risk sẽ là median của posterior.
>
>
>
> Vậy thì ở đây, việc ta đi minimize cái Bayes risk này, hoàn toàn tương ứng với việc ta đi tìm Bayes estimator giúp minimize risk function trong bối cảnh
> Casella. Nói vậy để thấy có sự liên kết giữa Casella và Bishop.
>
>
>
> Rồi, vậy thì như đã nói, khi đặt vấn đề minimize E[L] với công thức 1.80, biến số tối ưu ở đây là: **Cách chia range** 𝐗 ra **thành một phân hoạch**
> (partition): R1,....RK.
>
>
>
> Có nghĩa là, không giống như trong bài toán tối ưu quen thuộc, trong đó ta đi tìm trong các giá trị cho phép của x để có được giá trị x* khiến hàm f(x*) là nhỏ
> nhất
>
>
>
> Thì ở đây ta lại đi tìm trong số các phân hoạch [R1,...RK] (định nghĩa phân hoạch: R1 U R2 U ...Rk = range X và intersection của chúng là tập rỗng) sao cho
> E[L] có giá trị nhỏ nhất
>
>
>
> Mà điều này cũng là vì bản chất là cũng vì, ta đang làm việc với bài toán classification, nơi mà mục tiêu của nó, là tìm được một quy tắc phân loại sao cho
> chính xác nhất, gỉam thiểu được sai lầm phân loại sai. Để rồi cũng y như trong bài toán Hypothesis testing, nơi mà thứ chúng ta tìm kiếm, cũng là một cái
> rule - giúp đưa ra quyết định rằng nên reject hay accept H0 tốt nhất, và cái rule này, cũng được thể hiện bởi việc nó sẽ phân chia range X thành rejection
> region R và acceptance region Rc.
>
>
>
> Nói vậy để thấy, việc ta đụng bài toán tối ưu mà trong đó thứ cần tìm (biến số tối ưu) là một phân hoạch không phải nay mới gặp.
>
>
>
> Quay lại đây ta có bài toán:
>
>
>
> minimize_{phân hoạch R1,...RK} Σk=1:K Σj=1,..K ∫_Rj Lkj f(Ck,𝐱) d𝐱
>
>
>
> Biến đổi objective chút xíu:
>
>
>
> Σk=1:K Σj=1,..K ∫_Rj Lkj f(Ck,𝐱) d𝐱
>
>
>
> Tích phân của tổng = tổng tích phân, bản chất tích phân chỉ là cái tổng, và  với các kí hiệu các tổng của tổng thì cứ thay đổi vị trí thoải mái:
>
>
>
> = Σj=1,..K ∫_Rj Σk=1:K Lkj f(Ck,𝐱) d𝐱
>
>
>
> = Σj=1,..K ∫_Rj  [Σk=1:K Lkj f(Ck,𝐱)] d𝐱
>
>
>
> Đặt hàm gj(𝐱) = Σk=1:K Lkj f(Ck,𝐱), ta sẽ xem xét ý nghĩa của cái cụm này sau.
>
>
>
> = Σj=1,..K ∫_Rj  gj(𝐱) d𝐱
>
>
>
> Dùng **indicator** **function** để chuyển tổng tích phân trên các vùng Rj thành tích phân trên toàn range 𝐗: Ij(𝐱) = I_(𝐱 ∈ Rj), mang giá trị 1 hoặc 0
> tùy vào 𝐱 ∈ Rj hay không
>
>
>
> ⇨..= Σj=1,..K ∫_range_𝐗  Ij(𝐱) gj(𝐱) d𝐱 Đưa nốt tổng j vào tích phân:=  ∫_range_𝐗 Σj=1,..K Ij(x) gj(x) dx  Đến đây viết lại bài toán:Tìm kiếm bộ phân hoạch R1,..RK / cũng là cái decision rule để gán class cho các data point 𝐱 ∈ range 𝐗  sao cho minimize ∫_range_𝐗 Σj=1,..K
> Ij(𝐱) gj(𝐱) d𝐱
>
>
>
> Để dễ hiểu, ta sẽ xem xét ý nghĩa của từng thành phần trong cái objective này:
>
>
>
> i) gj(𝐱) = Σk=1:K Lkj f(𝐱, Ck) là cái gì, ý nghĩa là gì?
>
>
>
> Để thấy cái này là gì, hãy nhớ về định nghĩa của kì vọng, trong Stat110, gs Joe Blizstein dạy ta rằng, bản chất của kì vọng của random variable X, chỉ là GIÁ
> TRỊ TRUNG BÌNH của nó. Ví dụ như nó là một biến rời rạc, có các giá trị khả dĩ x1,x2,...xn với xác suất mà nó (X) mang các giá trị đó quy định bởi P(X=x1),
> P(X=x),...Thì EX chỉ là weighted average - trung bình của X có gắn trọng số bởi xác suất tương ứng: Σi xi P(X=xi)
>
>
>
> Vậy thì ở đây trong công thức trên Lkj là mức phạt quy định khi gán 𝐱 có T = k vào class j
>
>
>
> Và f(𝐱, Ck) về cơ bản cũng có thể tương đương với xác suất mà T = Ck xảy ra.
>
>
>
> Nên Σk=1:K Lkj f(𝐱, Ck) = Σk=1:K [mức phạt khi gán một data point thuộc class Ck vào class j] * [Xác xuất data point thuộc class Ck]
>
>
>
> và nó mang ý nghĩa là **Trung bình mức phạt khi gán data point x vào class Cj**
>
>
>
> Vậy gj(𝐱): mức phạt trung bình khi gán data point x vào class Cj
>
>
>
> -------
>
>
>
> ii) Σj=1:K Ij(𝐱)gj(𝐱) là cái gì:
>
>
>
> triển khai ra, = I1(𝐱)g1(𝐱) + I2(𝐱)g2(𝐱) + ..IK(𝐱)gK(𝐱)
>
>
>
> và nó sẽ có kết quả chỉ là một hạng tử trong đám này. Cái nào thì tùy vào **CÁCH PHÂN LOẠI ĐANG GÁN** 𝐱 **CHO RỔ NÀO TRONG R1,..RK**, ví dụ
> gán x cho R2, thì I2(x) = 1, mấy cái khác = 0 ⇨ tổng này = 1*g2(𝐱) = g2(𝐱)
>
>
>
> Như vậy, nếu gj(𝐱) là **mức phạt trung bình khi gán x vào class Cj**, mang ý nghĩa là: Mức phạt được **QUY ĐỊNH TRONG LUẬT**
>
>
>
> thì Σj=1:K Ij(𝐱) gj(𝐱) là **mức phạt THỰC TẾ, ghi nhận được khi mô hình THỰC HIỆN PHÂN LOẠI MỘT DATA POINT x.**
>
>
>
> iii) Vậy ∫_range_𝐗 Σj=1:K Ij(𝐱)gj(𝐱) là gì?
>
>
>
> Nó CHÍNH LÀ **TỔNG MỨC PHẠT THỰC TẾ**, ghi nhận được khi mô hình **THỰC HIỆN PHÂN LOẠI TOÀN BỘ x TRONG RANGE X**
>
>
>
> VẬY THÌ TỪ ĐÓ DỄ HIỂU RẰNG, **CÁI TỔNG MỨC PHẠT THỰC TẾ TRÊN TOÀN BỘ DỮ LIỆU SẼ NHỎ NHẤT** NẾU **MỨC PHẠT THỰC TẾ TRÊN
> TỪNG ÔNG x LÀ NHỎ NHẤT.**
>
>
>
> Ví dụ tổng mức phạt trên tập range X = {x1, x2, x3} sẽ dĩ nhiên là nhỏ nhất khi mức phạt trên từng ông là nhỏ nhất. Vì mấy ông này đâu có liên quan mẹ gì
> nhau. Nó sẽ chỉ không đúng nếu như: giảm mức phạt của ông x1 lại khiến tăng mức phạt của ông x2 chẳng hạn, thì khi đó, việc giảm mức phạt của từng
> ông mới khiến chưa chắc tổng mức phạt cả đám giảm. Nhưng ở đây thì chúng không liên quan gì nhau.
>
>
>
> Đó là lí do mà ta có thể chuyển bài toán tối ưu minimize ∫rangeX Σj=1:K Ij(𝐱)gj(𝐱) thành minimize Σj=1:K Ij(𝐱)gj(𝐱)
>
>
>
> Và như vậy, kiểu như ta sẽ có vô số bài toán tối ưu, mỗi cái ứng với với mỗi 𝐱:
>
>
>
> minimize Σj=1:K Ij(𝐱)gj(𝐱)
>
>
>
> ⇔ minimize Σj=1:K Ij(𝐱)gj(𝐱)
>
>
>
> = I1(𝐱) g1(𝐱) + ... + IK(𝐱) gK(𝐱)
>
>
>
> Và nên nhớ biến tối ưu là phân hoạch R1,...RK, hay cũng là bộ các hàm I1(𝐱), I2(𝐱),...Ik(𝐱),
>
>
>
> Vì là một phân hoạch nên ràng buộc của chúng là: Chỉ một trong số các indicator function được  phép bằng 1. Ví dụ I1(𝐱) = 1, thì I2(𝐱) = ...IK(𝐱) = 0,
> thể hiện rằng decision rule assign data point x cho class 1.
>
>
>
> Như vậy, đến đây **bài toán trở thành y như đặt vấn đề là**: 
>
>
>
> **TRONG SỐ CÁC HÀM INDICATOR** Ij(𝐱) j = 1...K thì **CHO CÁI NÀO BẰNG 1 ĐỂ RA KẾT QUẢ NHỎ NHẤT**.
>
>
>
> Thì cũng chính là đồng nghĩa với: 
>
>
>
> **CHỌN CÁI NÀO ĐỂ CÓ KẾT QUẢ NHỎ NHẤT TRONG ĐÁM {g1(x),...gK(x)**
>
>
>
> cũng là
>
>
>
> **CHỌN RA CÁI NÀO NHỎ NHẤT TRONG ĐÁM:** **{Σk=1:K Lk1 f(x, Ck), Σk=1:K Lk2 f(x, Ck), ..Σk=1:K LkK f(x, Ck)}**
>
>
>
> **VÀ ĐÓ CHÍNH LÀ Ý CỦA GS BISHOP KHI NÓI WE SHOULD MINIMIZE Σk Lkj p(x, Ck)**
>
>
>
> **trong câu nói "...which implies that for each x we should minimize Σk Lkj p(x, Ck)"**

<br>

<a id="node-ym5yp89"></a>

###### Luật quyết định Bayes tối ưu

<p align="center"><kbd><img src="assets/i870mw765vb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/9csrqmrvp99.png" width="80%"></kbd></p>

> [!NOTE]
> Như vậy đến đây ta đã hiểu là cái optimal decision rule đó là:
>
>
>
> **CHỌN RA CÁI NÀO NHỎ NHẤT TRONG ĐÁM**: {Σk=1:K Lk1 f(x, Ck), Σk=1:K
> Lk2 f(x, Ck), ..Σk=1:K LkK f(x, Ck)} sau đó **LẤY INDEX** ĐỂ GÁN CLASS cho
> data point 𝐱.
>
>
>
> Gọi là j = argmin_{Σk=1:K Lkj f(𝐱, Ck)}, mang ý nghĩa là **trong K cục** Σk=1:K
> Lkj f(x, Ck) j = 1,2..K thì **cục nhỏ nhất ứng với j bằng mấy**
>
>
>
> **Gán data point x cho Cj**, và **làm vậy với mọi x**.
>
>
>
> (ví dụ trong K cục trên, cái thứ 2 là nhỏ nhất, thì j = 2, decision rule tối ưu sẽ
> gán data point vào class 2)
>
>
>
> Thì đó **chính là một phân hoạch / decision rule tạo ra Bayes risk nhỏ nhất**.
>
>
>
> Và vì f(𝐱, Ck) = f(Ck|𝐱)f(𝐱) nên f(x) là như nhau và không âm
>
>
>
> xem trong đám {Σk=1:K Lkj f(𝐱, Ck)} j =1,...K cái nào nhỏ nhất
>
>
>
> thì cũng là xem trong đám {Σk=1:K Lkj f(Ck|𝐱)} j =1,...K cái nào nhỏ nhất
>
>
>
> Tóm lại cái optimal (minimize Bayes risk) decision rule là:
>
>
>
> Với mỗi 𝐱, gán cho nó class Cj với j = argmin Σk=1:K Lkj f(Ck|𝐱)

**🔗 See also:** [K-Nearest Neighbor Classification](./252_nearest_neighbour_methods.md#node-mtmr0qc)

<br>

<a id="node-vgqxms7"></a>

###### Tuỳ chọn từ chối

<p align="center"><kbd><img src="assets/jskp9rvfhwj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xd2cl6cxhn.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là, như ta đã thấy vừa rồi, cái decision rule / hay classifier tối ưu xét theo
> tiêu chí giảm thiểu Bayes risk là cái mà ta assign class Ck cho data point 𝐱
> với k = argmin_j [trung bình loss khi assign class j cho **x,** = Σk Lkj f(Ck|𝐱)]
>
>
>
> Nếu các mức penalty cho các loại error đều cho bằng nhau = 1 Lkj = 1 với mọi k
> khác j và bằng 0 khi k = j thì decision rule nói trên trở thành:
>
>
>
> Khi đó, gj(x) = Σk=1:K Lkj f(Ck|𝐱) = Σk≠j f(Ck|𝐱) = 1 - f(Cj|𝐱) (do Σk
> f(Ck|𝐱) = 1)
>
>
>
> ⇨ rule trở thành:
>
>
>
> Assign Ck cho 𝐱, với k = argmin_j [1 - f(Cj|𝐱)]
>
>
>
> cũng là k = argmax_j [f(Cj|𝐱) - 1]
>
>
>
> = argmax_j f(Cj|𝐱)
>
>
>
> có ngghĩa là trở thành cái rule mà giúp giảm misclassification error (không coi
> trọng loại error nào hơn cái nào): gán class nào thì dựa vào posterior f(t|x) nào
> lớn nhất
>
>
>
> Tuy vậy, không có gì chắc đây là rule tuyệt đối đúng.
>
>
>
> Có nghĩa là, cái Ck với k = argmax_j f(Cj|𝐱) không có gì đảm bảo chính là
> class thật sự của 𝐱.
>
>
>
> Do đó, vẫn có thể có misclassification error.
>
>
>
> Và nó xảy ra khi: ví dụ với **x1,** posterior f(C2|𝐱) là cao nhất, nhưng nó
> không vượt trội, để rồi, f(C1|𝐱) cũng ko nhỏ. Và sự thật thì C1 mới là class
> đúng.
>
>
>
> Nên lúc này, khi f(C2|𝐱) và f(C1|𝐱) xem xem nhau, tuy f(C2|𝐱) là lớn nhất. Và
> cũng đồng nghĩa là f(C2|𝐱) cách khá xa mức tuyệt đối (=1, gs Bishop gọi là
> unity).
>
>
>
> Và đây là khi misclassification error có thể xảy ra.
>
>
>
> Nói chung là, ta chỉ có thể đảm bảo misclassification error không xảy ra khi
> f(C2|𝐱) = 1, để rồi assign class C2 cho data point x thì sẽ đảm bảo chính xác.
> Tuy nhiên chỉ cần f(C2|𝐱) < 1, thì đồng nghĩa vẫn có xác suất class đúng là class
> khác chứ ko phải C2.
>
>
>
> Thành ra, ta có thể đưa ra option thứ 3: (giả sử đang dự đoán giữa hai class C1
> vs C2) là: Không biết - Từ chối đoán - bằng cách sau khi tính posterior của các
> class thì không dựa vào việc cái nào có lớn nhất để đưa ra phân loại ngay lập
> tức, mà xem posterior có lớn hơn một cái threshold (α, hay trong sách là θ) hay
> không, ví dụ, chỉ kết luận nếu posterior lớn nhất lớn hơn 80%. Còn không thì
> đưa ra option: Từ chối phân loại, ko biết, mời bạn đoán.
>
>
>
> Tương tự, ta cũng có thể làm vậy bài toán có loss matrix (ý là có ưu tiên loại
> error này hơn error kia)

<br>

<a id="node-qyo3xob"></a>

###### Lựa chọn từ chối phân loại

<p align="center"><kbd><img src="assets/tl813zhd0c.png" width="80%"></kbd></p>

> [!NOTE]
> HÌnh minh họa cho thấy vùng giữa hai đường xanh lá, nơi đó posterior tại  hai class
> (ý là f(t|x)|t=C1 và f(t|x)|t=C2)  có giá trị khác biệt không lớn. Và ta sẽ từ chối đưa ra
> quyết định phân loại

<br>

<a id="node-zxhy7ux"></a>

###### Inference và Decision

<p align="center"><kbd><img src="assets/fgd3dfdfraw.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/welwmx6viim.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái gs nói là bữa giờ ta đang tiếp cận bài toán classification theo hai
> bước: bước một là dựa trên data, đi xây dựng posterior distribution f(t|𝐱)
> (trong sách là p(Ck|𝐱)), đây chính là bước gọi là inference state
>
>
>
> (liên hệ với Statistical Inference - Casella,  bài toán inference là bài toán đi
> xây dựng một suy đoán về tham số của population distribution, có thể là một
> point estimator W(𝐗) để estimate giá trị của θ, hypothesis test  để đưa ra
> suy đoán về θ nằm ở Θ0 hay Θ0c, hoặc một interval estimator C(𝐗) để
> estimate một khoảng / một set mà có thể chứa θ, thì nói chung, ta hiểu
> inference là việc ta muốn suy đoán về sự thật của phân phối xác suất chi
> phối dữ liệu quan sát thấy)
>
>
>
> Sau đó, ta mới dựa trên posterior để thông qua decision theory giúp đưa ra
> prediction, đây gọi là decision stage.
>
>
>
> Thế thì, ông cho biết, có một cách làm khác, không cần chia ra hai bước,
> mà làm luôn trong một lần: vừa "học" ra / suy luận / inference posterior
> và vừa đưa ra dự đoán luôn, thông qua hình thức là học một function map
> giữa input và decision, gọi là DISCRIMINANT function**.**
>
>
>
> Dừng lại chút, mình vừa hiểu ra một việc: Lấy ví dụ một neural network,
> hay deep learning model, thì bằng cách training một mapping function
> giữa ảnh đầu vào và phân loại ảnh đầu ra, mình có thể hiểu bên trong nó
> đang làm hai việc cùng lúc: học ra posterior distribution và thực hiện
> decision. Nhưng có những loại khác, nó ko tìm cách học posterior, mà
> chỉ học luôn cái mapping function, gọi là discriminant function nói trên.
> Hay, ví dụ như mình đã từng học về VAE trong cs231n cũng vậy, encoder
> là cái khúc nó sẽ học ra posterior distribution, và decoder là một mô hình
> đóng vai trò sampling từ posterior distribution đó.

<br>

<a id="node-dlnliou"></a>

###### Mô hình Generative

<p align="center"><kbd><img src="assets/7gekk5ortgi.png" width="80%"></kbd></p>

> [!NOTE]
> Có ba cách tiếp cận cho bài toán decision (tạm hiểu là classification). 
>
>
>
> Loại thứ nhất: Đầu tiên, ta giải bài toán inference: 
>
>
>
> Học / xây dựng f(𝐱|t) với từng possible value của t: C1,...CK. (tức là
> theo kí hiệu của gs Bishop: p(𝐱|Ck).
>
>
>
> Học / xây dựng f(𝐭).
>
>
>
> Dùng Bayes theorem, chuyển nó thành posterior của T:
>
>
>
> f(t|𝐱) = f(𝐱|t) f(t) / f(𝐱).
>
>
>
> Với f(𝐱) có thể dùng LOTP để tách thành:
>
>
>
> Σ{mọi possible value của t} f(𝐱, t)
>
>
>
> = Σ{mọi possible value của t} f(𝐱|t)f(t)
>
>
>
> Từ đó, ta có giá trị của f(t|x) với mỗi giá trị của {C1,...CK} của t
>
>
>
> Và cho phép ta dùng decision theory như đã biết để make decision.
>
>
>
> Mình có thể nhận ra đây chính là Naive Bayes
>
>
>
> Gs cho biết những cách tiếp cận mà trong đó ta thực hiện bước suy luận về
> **distribution của input và** output, tức là học ra f(t, 𝐱) thì gọi là **generative** model.
> Vì, nếu ta có distribution của input, ta có thể thực hiện sampling từ đó,
> để có thể có một dạng dữ liệu synthetic (ý là ví dụ như ảnh do ta tạo ra, 
> không phải ảnh chụp ở ngoài đời thật, ví dụ mấy mô hình tảo ảnh hiện nay
> như diffusion model)

<br>

<a id="node-o0cwsv1"></a>

###### Mô hình phân biệt

<p align="center"><kbd><img src="assets/2ymhk9wtcrz.png" width="80%"></kbd></p>

> [!NOTE]
> Cách tiếp cận thứ hai, là inference ra trực tiếp posterior f(t|𝐱) và sau đó thì
> dùng nó để make decision. 
>
>
>
> Nó khác cái trước ở chỗ, ta không cần học ra f(𝐱|t) f(t). Mà chỉ học thẳng
> ra f(t|𝐱) thôi.
>
>
>
> Cái này như bữa giờ đang làm, gọi là discriminative models

<br>

<a id="node-odscyh7"></a>

###### Hàm phân biệt

<p align="center"><kbd><img src="assets/zknjsj3iwbq.png" width="80%"></kbd></p>

> [!NOTE]
> Và cuốn cùng là discriminant function như nãy nói. Cái này nó ko cần học
> phân phối xác suất gì hết, nó chỉ là tìm ra cái mapping function giữa t và x.
> t = f(x). Xác suất ko có vai trò gì hết

<br>

<a id="node-3xzksfu"></a>

###### Ưu điểm Cách 1: Phát hiện bất thường

<p align="center"><kbd><img src="assets/qadxk3honq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/327cb9i1ae9.png" width="80%"></kbd></p>

> [!NOTE]
> Bàn một chút về ưu nhược diểm của 3 cách làm này.
>
>
>
> Cách đầu tiên, đại khái là vì ta dù implicitly hay explicitly (tường minh hoặc
> ngầm định) xây dựng joint distribution f(t,𝐱) (vì infer f(𝐱|t), f(t) thì cũng là
> xây f(𝐱,t)) thì đều cần nhiều data.
>
>
>
> Ưu điểm là, ta có thể có f(𝐱) (bằng cách marginalizing f(𝐱, t) over range T
> và cái này, là prior distribution của x. Do đó có thể dùng nó để tính  xác suất
> của một input. Và áp dụng vào bài toán phát hiện bất thường.
>
>
>
> Nói rõ hơn tí, thì đại ý là: ví dụ trong bài toán phân loại ảnh, thì input x, là
> ảnh, t là phân loại (class), thì ý nghĩa của f(𝐱) là hàm xác suất của ảnh,
> công dụng là, bỏ vào một 𝐱 - vector đại diện của một ảnh, nó sẽ cho biết xác
> suất là cao hay thấp. Vậy ta có thể dùng nó như một hàm check để phát
> hiện khi nào thì ta có một x có xác suất thấp → thì đó chính là một tấm ảnh
> có sự bất thường gọi là outlier

<br>

<a id="node-fks3wq7"></a>

###### Hiệu quả phương pháp phân loại

<p align="center"><kbd><img src="assets/x6a7gktwko.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/24w3qveb6wr.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên, nếu như ta chỉ muốn làm bài toán classification thì việc học ra joint 
> distribution f(𝐱, t) là quá lãng phí. Vì như đã biết, cũng như trong cách b, 
> để phân loại, ta chỉ cần dựa trên posterior f(t|𝐱). 
>
>
>
> Nên sẽ ít tốn kém hơn nếu ta học trực tiếp hàm posterior thay vì đi tìm f(𝐱, t)
> rồi mới dùng để có posterior.
>
>
>
> Ông nó nói cái ý, f(𝐱|t) với t = C1,...CK có những cấu trúc ít ảnh hưởng đến 
> posterior, thì ý là do đó việc làm theo cách a) để tiếp cận bài toán classification
> là không mang lại lợi ích gì cả.
>
>
>
> Ví dụ như trong minh họa bài toán có 2 class C1, C2 và input 1D x này.
>
>
>
> Đồ thị của f(x|C1) và f(x|C2) ở bên trái cho thấy có các đỉnh.
>
>
>
> Nhưng đồ thị của posterior f(C1|x), f(C2|x) thì lại chẳng phản ánh gì tương
> ứng tại các đỉnh này. Đó là ý gs Bishop nói những structure của class
> conditional density chả có đóng góp gì cho posterior cả.
>
>
>
> Còn cái cách (c), thì chả cần posterior gì, chỉ là học cái mapping function
> nhận vào x, nhả ra C1 hay C2...
>
>
>
> MInh họa trong hình gs nói, nó sẽ tương ứng với việc ta tìm cách học ra
> function: f(x) sau đây: f(x) = C1 nếu x < c, và C2 nếu x > c với c là cái điểm
> ứng với đường màu xanh lá, chính là nơi mà nếu dùng nó để assign class,
> ta sẽ minimize misclassification rate

<br>

<a id="node-ir8w5wg"></a>

###### Lợi ích của Posterior

<p align="center"><kbd><img src="assets/rlr5mrbu46k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0m8zl9m85qo9.png" width="80%"></kbd></p>

> [!NOTE]
> Với c, tuy vậy, ta sẽ ko có posterior,  mà cái này thì rất hữu dụng.
>
>
>
> Ví dụ, ví dụ như bài toán mấy bữa nay làm, khi ta define ra cái loss matrix
> quy định mức phạt khác nhau cho các loại error khác nhau. Nếu ta làm
> theo cách làm bữa trước, thì khi muốn thay đổi loss matrix, thì chỉ việc thay
> đổi, cái posterior sẽ được cập nhật theo rất đơn giản (trivially). Còn nếu ta
> làm theo cách c, ta phải train lại từ đầu (afresh)
>
>
>
> Hơn nữa, posterior sẽ giúp ta có thể reject, ko đưa ra quyết định khi cảm
> thấy ko chắc

<br>

<a id="node-1ps2hou"></a>

###### Điều chỉnh phân phối hậu nghiệm

<p align="center"><kbd><img src="assets/gw7iqzvzyhs.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi đoạn này nói về một ý nữa mà việc dùng posterior sẽ mang lại lợi ích
> mà  cách làm (c) ko có:
>
>
>
> Ví dụ như trong bài toán phân loại cancer hay ko cancer từ ảnh chụp X
> quang mà ta đang làm bữa giờ. thì có có vấn đề này (là cái mà mr Andrew
> Ng đã nói trong MLSpec: **Skewed dataset**). Trong thực tế, số ca cancer là ít
> hơn nhiều so với không cancer (này nói ở đâu chứ ko phải Việt Nam). Nên
> dễ hiểu là giả sử tỉ lệ cancel trong dân số chỉ là 0.1%, thì một cái mô hình
> tào lao nhận vào input x và luôn trả ra là ko cancer, sẽ vẫn có thể có kết
> quả chính xác rất cao.
>
>
>
> Rồi, và vì số ca cancer ít, nên x-ray cancer cũng ít hơn x-ray ko cancer,
> nên nếu dùng chúng để training mô hình thì có thể sẽ không hiệu quả. Khi
> đó ta có thể tạo một dataset cân bằng hơn giữa có và không cancer.
>
>
>
> Nhưng vấn đề là, posterior, f(t|𝐱) theo bayes rule = f(𝐱|t)f(t)/f(𝐱), nên dễ thấy
> nó sẽ tỉ lệ thuận với f(t) - tức priori.
>
>
>
> Thành ra, một khi mà ta đã "chỉnh sửa": bằng cách tạo dataset cân bằng
> hơn, ta đã thay đởi prior distribution.
>
>
>
> Do đó, cách làm là, sau khi dùng data cân bằng để học ra posterior, ta  sẽ
> lấy cái posterior scale lại với tỉ lệ của prior, và normalizing lại. Vầy nè:
>
>
>
> Giải sử có C1, C2, Trong đó f(C1) = 0.9 f(C2) = 0.1 (tức hàm ý, 10 người
> thì 9 ca ko cancer, 1 người có cancer)
>
>
>
> sau khi dùng một dataset cân bằng (50% là hình có cancer, 50% là hình
> không cancer) để train ra posterior f(t|𝐱)
>
>
>
> Ta sẽ điều chỉnh lại:
>
>
>
> f^(C1|𝐱) = f(C1|𝐱) * 0.9/c
>
>
>
> và
>
>
>
> f^(C2|𝐱) =  f(C2|𝐱) * 0.1/c
>
>
>
> với c là normalizing constant giúp f^(C1|𝐱) + f^(C2|𝐱) = 1
>
>
>
> như vậy lúc này posterior sau điều chỉnh đã phản ánh lại được tỉ lệ mắc
> bệnh / không mắc bệnh của prior.
>
>
>
> Nên cái này gọi là Đền bù (compensate) lại class prior
>
>
>
> Mấu chốt là, nếu làm theo (c) ta sẽ ko làm vậy được

<br>

<a id="node-lm3a6ad"></a>

###### Naive Bayes và độc lập điều kiện

<p align="center"><kbd><img src="assets/ykjpnie4t4.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/y5mrxchcvih.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là, một công dụng nữa của cách tiếp cận posterior là ta giải quyết một bài
> toán phức tạp bằng cách tách nó ra thành các bài toán đơn  gỉan hơn.
>
>
>
> Ví dụ: Dự đoán bệnh cancer hay không dựa trên ảnh X-quang và kết  quả xét
> nghiệm máu. Khi đó ta muốn xây dựng posterior: f(t|𝐱I, 𝐱B)  distribution
> của T dựa trên vector X-ray image 𝐱I, và kết quả xét nghiệm máu 𝐱B
>
>
>
> thì đại khái là, bằng cách đặt assumption rằng f(𝐱I,𝐱B|Ck) =
> f(𝐱I|Ck)f(𝐱B|Ck) ta sẽ dựa trên Bayes rule như thường lệ để xây dựng
> posterior:
>
>
>
> f(t|**xI**,**xB**) = f(**xI**,**xB**|Ck)f(Ck)/f(**xI**,**xB**)
>
>
>
> ∝ f(**xI**,**xB**|Ck)f(Ck)
>
>
>
> ∝ f(**xI**|Ck)f(**xB**|Ck)f(Ck)
>
>
>
> ∝ [f(Ck|**xI**)f**(xI**)/f(Ck)] [f(Ck|**xB**)f(**xB**)/f(Ck)] f(Ck) | dùng Bayes rule với f(xI|Ck),
> f(xB|Ck)
>
>
>
> ∝ f(Ck|**xI**) f(**xI**) f(Ck|**xB**) f(**xB**) / f(Ck)
>
>
>
> ∝ f(Ck|**xI**) f(Ck|**xB**) / f(Ck) | bỏ f(**xI**), f(**xB**) là constant
>
>
>
> f(Ck), prior của T thì có thể xấp xỉ bằng cách dùng tỉ lệ class Ck trong data.
>
>
>
> Như vậy là ta đã có thể có f(t|**xB**,**xI**). Đây chính là Naive Bayes. 
>
>
>
> Nói nó Naive
> (ngây thơ) là vì, ta đang giả định là dựa trên T = Ck thì 𝐗_image và 𝐗_blood
> độc lập. Nhưng sự thật đâu phải vậy, ví dụ, nếu đã biết là Ck rồi, thì việc biết
> ảnh **X_image** có thể đoán được chỉ số máu **X_blood**

<br>

<a id="node-pgy5or6"></a>

###### Loss functions for regression

<p align="center"><kbd><img src="assets/fdhzp1y5yur.png" width="80%"></kbd></p>

> [!NOTE]
> Chuyển qua bài toán decision theory trong linear regression. Trong đó,  ta
> đưa ra dự đóan t = y(𝐱) cho mỗi input 𝐱, mỗi một dự đoán như vậy, tạo
> ra loss L(t, y(𝐱)). Và average loss E[L] theo công thức 1.86. Vì sao?
>
>
>
> Đơn giản, L(𝐭,y(𝐱)) là hàm, nên Loss = L(𝐓, y(𝐗)) là random
> variable   tạo ra bởi việc áp một hàm số lên hai random variable T, 𝐗. Và
> như đã học ở Stat110, Casella, 2D LOTUS cho phép ta tính EZ của Y = g(X,
> Y) dựa theo joint pdf/pmf f(x,y) của X, Y:
>
>
>
> EZ = Eg(X,Y) = ∫∫g(x,y)f(x,y)dxdy
>
>
>
> Vậy thì đây cũng vậy, LOTUS cho phép tính EL dựa theo joint distribution
> của T, 𝐗
>
>
>
> E[L] = ∫∫L(t, y(𝐱)) f(t,𝐱) d𝐱 dt

<br>

<a id="node-hh6bwri"></a>

###### Minimizing Squared Loss Function

<p align="center"><kbd><img src="assets/ogib0z5b2sf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/5whe6nton69.png" width="80%"></kbd></p>

> [!NOTE]
> Một lựa chọn phổ biến cho loss trong regression problem là squared loss, L(t, y(𝐱)) = (y(𝐱) - t)²
>
>
>
> khi đó E\[L\] = ∫∫\[y(𝐱) - t\]² f(𝐱, t) d𝐱 dt
>
>
>
> Đến đây, mình hiểu là ta sẽ coi E\[L\], như một hàm g(y, t) để thử derive y khiến minimize g(y, t).
>
>
>
> Dùng đạo hàm, điều kiện cần tối ưu bậc nhất: đạo hàm đối y của g = 0 để tìm critical point:
>
>
>
> ∂/∂y g(t,y) = 0
>
>
>
> ⇔ ∂/∂y ∫∫\[y(x) - t\]² f(𝐱, t) d𝐱 dt = 0
>
>
>
> Đạo hàm của tích phân, mình còn nhớ trong Casella có nói đến theorem nói rằng trong một số điều kiện, có thể đổi chỗ hai cái này, (trường hợp này là khi cận tích phân ko phụ thuộc y(𝐱))
>
>
>
> Ở đây có lẽ là thỏa điều kiện đó.
>
>
>
> ⇔ ∫∫ ∂/∂y(𝐱) {\[y(𝐱) - t\]² f(𝐱, t)} d𝐱 dt = 0
>
>
>
> ⇔ ∫∫ \[∂/∂y(𝐱) \[y(𝐱) - t\]²\] f(𝐱, t) d𝐱 dt = 0
>
>
>
> Xét ∂/∂y(x) \[y(x) - t\]²
>
>
>
> = ∂/∂\[y(𝐱)-t\] \[y(𝐱) - t\]² . d/dy(𝐱) \[y(𝐱) - t\]
>
>
>
> = 2\[y(𝐱) - t\]
>
>
>
> .. ⇔ ∫∫ 2\[y(𝐱) - t\] f(𝐱, t) d𝐱 dt = 0
>
>
>
> ⇔ 2 ∫∫ \[y(𝐱) - t\] f(𝐱, t) dx dt = 0
>
>
>
> ⇔ ∫∫ y(𝐱) f(𝐱, t) d𝐱 dt - ∫∫ t f(𝐱, t) d𝐱 dt = 0
>
>
>
> ⇔ ∫∫ y(𝐱) f(𝐱, t) d𝐱 dt = ∫∫ t f(𝐱, t) d𝐱 dt
>
>
>
> Xét vế trái:
>
>
>
> ∫∫ y(𝐱) f(𝐱, t) d𝐱 dt = ∫\_range X ∫\_range_T y(𝐱) f(𝐱, t) dt d𝐱
>
>
>
> = ∫*range*𝐗 y(x) {∫*range*𝐓 f(𝐱, t) dt} d𝐱
>
>
>
> ∫\_range_T f(x, t) dt chính là marginalizing joint pdf của 𝐗, T với mọi mọi T, sẽ được marginal pdf của 𝐗
>
>
>
> .. = ∫*range*𝐗 y(𝐱) f(𝐱) d𝐱
>
>
>
> Xét vế phải:
>
>
>
> ∫∫ t f(𝐱, t) d𝐱 dt = ∫\_range 𝐗 \[∫\_range 𝐓 t f(𝐱, t) dt \] d𝐱 Vậy phương trình trở thành ∫*range*𝐗 y(𝐱) f(𝐱) d𝐱 = ∫\_range 𝐗 \[∫\_range T t f(𝐱, t) dt \] d𝐱
>
>
>
> Vì tính chất complete flexible của y(𝐱), cho phép:
>
>
>
> ⇔ y(𝐱) f(𝐱)= ∫\_range T t f(𝐱, t) dt
>
>
>
> ⇔ y(𝐱) = \[∫\_range T t f(𝐱, t) dt\] / f(𝐱)
>
>
>
> = \[∫\_range T t f(t|𝐱) f(𝐱) dt\] / f(𝐱)
>
>
>
> = \[∫\_range T t f(t|𝐱) dt\] f(𝐱) / f(𝐱)
>
>
>
> = ∫\_range T t f(t|𝐱) dt
>
>
>
> Đây chính là E(T|𝐱), trung bình của T \~ posterior distribution f(t|𝐱)
>
>
>
> Như vậy, khi dùng squared loss thì cái hàm y(𝐱) giúp minimize trung bình loss E\[L\] chính là cái hàm y(𝐱) dùng mean của posterior f(t|𝐱) để dự đoán.
>
>
>
> Thật ra cái này trong Casella đã học rồi cụ thể là khi ta học về Bayes estimator cho θ, thì ta đi tìm posterior π(θ|𝐱).
>
>
>
> Lúc này nếu muốn có point estimator cho θ, ta có thể lấy mean, hoặc median, và chúng đều là Bayes estimator.
>
>
>
> Nhưng mean, E\[θ|𝐱\] sẽ là cái Bayes estimator giúp **minimize Bayes risk khi loss là square error loss**. Còn median của posterior sẽ là Bayes estimator giúp **giảm Bayes risk là absolute error loss**.
>
>
>
> Ôn lại chút loss function, risk function, Bayes risk trong Casella:
>
>
>
> Loss function, là hàm của estimator L\_θ(δ(𝐗), θ), có thể là square error loss: \[δ(𝐗) - θ\]² hoặc absolute error loss: |δ(𝐗) - θ|.
>
>
>
> Risk function: E\_θ\[L(δ(𝐗), θ)\], mang ý nghĩa: Average loss over mọi 𝐗, để còn lại là hàm theo θ, để so với nhau giúp evaluate δ(𝐗).
>
>
>
> Bayes risk = ∫\_Θ R(δ(𝐗), θ) π(θ) dθ = ∫*Θ* ∫𝐗 L(δ(𝐱), θ) f(θ, 𝐱) d𝐱 dθ
>
>
>
> Vậy ở đây cũng y chang, cái E\[L\] mà gs Bishop nói ở đây chính là tương đương với Bayes risk (lấy kì vọng của Loss dưới joint distribution của T và 𝐗 f(𝐱, t))
>
>
>
> Do đó kết quả cũng là: khi ta muốn từ posterior f(t|𝐱) để đưa ra một point estimator cho T thì mean E\[T|𝐱\] sẽ là cái giúp giảm thiểu E\[L\], y như E\[θ|𝐱\] là point estimator cho θ giúp giảm thiểu Bayes risk khi loss là squared error vậy
>
>
>
> và ở trong sách Bishop đoạn này, dù ko nói, ta cũng đoán được, nếu muốn giảm thiểu average absolute loss, thì nên dùng median của posterior.
>
>
>
> Và từ đây cũng giúp mình nhớ lại để hiểu vì sao trong bài revising curve fitting, ta thấy gs Bishop assume Ti \~ Normal(y(xi,𝐰), 1/β), hành động này chính là dùng mean của posterior f(ti|xi), tức E\[Ti|xi\] để làm point estimate cho t, và theo decision theory, nó là tối ưu. Nếu ông dùng median của posterior để point estimate cho T thì nó sẽ cũng là tối ưu nhưng theo tiêu chí giảm thiểu average absolute error loss.
>
> Sẵn tiện đang nói bài toán linear regression, sẽ có ích nếu ta ôn lại chút.
>
>
>
> Nhớ lại một nhận định khi ta làm bài toán curve-fitting theo Bayesian approach và cũng đã thấy rằng maximize likelihood chính là giải bài toán curve fitting với error function là sum squared error. Để thấy rằng vì sao khi đó:
>
>
>
> Còn nhớ, trong bài toán đó, cụ thể là phần Revisiting curve fitting problem, nơi mà gs Bishop dắt ta quay lại xem xét bài toán polynomial curve fitting theo góc nhìn xác suất thì ông đưa ra những thay đổi sau: đầu tiên, ứng với mỗi xi, coi Ti là một random varible, để phản ánh tính uncertainty của nó.
>
>
>
> Và assume distribution của nó là Ti \~ Normal(y(xi, 𝐰), 1/β)
>
>
>
> và cái assumption này cũng chính là assume Ei = Ti - y(xi, 𝐰), tức sai số của dự đoán và giá trị thật sẽ là một Normal(0, 1/β).
>
>
>
> Chú ý, cho tới đây, 𝐰, tham số của polynomial function, vẫn đang được coi như fixed & unknown, nên y(xi, 𝐰) cũng vậy, fixed & unknown, báo hiệu rằng ta vẫn đang ở trong trường phái cổ điển.
>
>
>
> Rồi, từ đó, ta mới xây dựng joint distribution của T1,...TM f𝐓(𝐭). Nhờ tính chất độc lập của các cặp (xi, Ti) ta mới phân tách joint probability bằng tích marginal probability
>
>
>
> fT(𝐭) = Πi=1:N f(ti)
>
>
>
> Thể hiện sự phụ thuộc với xi, 𝐰, β ta sẽ có:
>
>
>
> f𝐓(𝐭|𝐱, 𝐰, β) = Πi=1:N f(ti|𝐰, xi, β)Tới đây sao nữa? Nhớ lại các cách tiếp cận trong Casella trong bài toán point estimator cụ thể là maximum likelihood estimator.
>
>
>
> Theo định nghĩa θ^\_ml(𝐗) = argmax\_θ L(θ|𝐗), là θ giúp giải thích hợp lí nhất cho gía trị quan sát được của 𝐗. Với hàm likelihood được định nghĩa là L(θ|𝐱) = f(𝐱|θ) Do đó θ^\_ml(X) = argmax\_θ f(𝐱|θ).
>
>
>
> Vậy thì ở đây, để đi tìm 𝐰 (cũng chính là tìm y(xi,𝐰), ta cũng có thể đi theo hướng này, đó là, tìm 𝐰 giúp giải thích hợp lí nhất cho giá trị quan sát được t1,t2..tNứng với x1,..xN (chú ý, chỉ có T là random variable, chứ 𝐗 thì không, nên vector 𝐱 không phải là giá trị quan sát được của vector random variable 𝐗 nào cả.
>
>
>
> 𝐰*ML = argmax*𝐰 L(𝐰|𝐭)
>
>
>
> và likelihood L(𝐰|𝐭) cũng define bởi f(𝐭|**x,w**,β) = Πi=1:N f(ti|xi,𝐰,β) với f là pdf của Normal(y(xi, 𝐰), 1/β)
>
>
>
> nên bài toán là: maximize Πi=1:N f(ti|xi,𝐰,β)
>
>
>
> và cũng dùng các trick để đưa về bài toán tối ưu tương đương, như thay maximize objective likelihood bằng minimize - log likelihood,..ta sẽ giải ra 𝐰\_ML. và tương tự (1/β)\_ML
>
>
>
> Và khi làm vậy ta sẽ thấy, bài toán tối ưu tương đương giúp tìm w_ML chính là đi minimize error function là sum squared error Σi (y(𝐰,xi) - ti)² mà trong phần đầu tiên, khi làm quen với bài toán polynomial curve fitting ta đã làm (lúc đó chưa theo góc nhìn xác suất gì cả)
>
>
>
> ---
>
>
>
> Trước khi recall tiếp phần Bayesian inference, ta nhắc lại nhận định rút ra được trong note liền trước (khi có posterior f(t|x) thì dùng mean của nó để point estimator cho T chính là cách để minimize average squared error loss)
>
>
>
> Khi gs Bishop giả định Ti \~ Normal(y(xi,𝐰), 1/β) thì chính là dùng mean của posterior f(ti|xi): E\[Ti|xi\] để làm point estimate cho T thì **theo decision theory**:
>
>
>
> Nếu theo tiêu chí giảm thiểu **average square error loss** của decision theory: lấy E\[Ti|xi\], tức **mean** của f(ti|xi)
>
>
>
> Nếu theo tiêu chí giảm thiểu **average absolute error** **loss** thì ta cần lấy **median** của f(ti|xi)
>
>
>
> Nhưng việc nhắc đến square loss của decision theory vừa rồi không liên quan gì đến việc khi ta maximize likelihood dưới giả định Ti \~ normal(y(xi,𝐰),1/β) ta thấy nó hóa ra cũng là minimize sum squared error, cái này chỉ là trùng hợp.
>
>
>
> Vì giả sử ta assume Ti là expo(y(xi,𝐰)), hay distribution nào khác: tức cũng là mean của posterior f(ti|xi), để rồi đi maximize likelihood, khi đó, ta sẽ thấy nó chưa chắc đã là minimize sum squared error. Tuy nhiên, miễn là ta lấy mean của posterior f(ti|xi) để làm point estimator cho T thì theo decision theory, đó vẫn là tốt nhất theo tiêu chí giảm average squared error loss.
>
>
>
> ---
>
>
>
> Sẵn trớn recall lại luôn: Sau đó, qua phần Bayesian inference, gs Bishop bắt đầu mới nói về việc trong Bayesian, ta sẽ coi tham số **w, cũng là random variable nốt**, từ đó viết hoa 𝐖 để chỉ random variable vector. Mà cái này như mình đã biết ở Casella, khi ta bước sang trường phái Bayesian, thì ta cũng coi θ là random quantity. Để rồi nó sẽ có prior distribution π(θ), thường được chọn do kinh nghiệm của experimenter, sau đó dùng Bayes theorem, ta tìm distribution của θ khi đã biết 𝐗 = 𝐱: π(θ|𝐱) = f(𝐱|θ) π(θ) / f(𝐱). Áp dụng vài bài toán curve fitting. Ta sẽ chọn Normal(0, (1/α)𝐈) làm priori.
>
>
>
> Áp dụng Bayes theorem, xây dựng posterior:
>
>
>
> π(𝐰|𝐭,𝐱,β,α) = f(𝐭|𝐱,𝐰,β) π(𝐰|α) / f(𝐭|𝐱)
>
>
>
> Với f(𝐭|𝐱,𝐰,β) là joint distribution của T1,..Ti, = Πi=1:N f(ti|xi,𝐰,β) = Πi=1:N Normal(ti|y(xi,𝐰),1/β)
>
>
>
> Còn π(𝐰|α) là priori = Normal(𝐰|0,(1/α)\*𝐈)
>
>
>
> Đến đây, nếu trong Casella, khi nói về Bayes estimator, sau khi xây dựng posterior xong, ta sẽ lấy mean hay median của nó để làm point estimator cho θ. Cụ thể, E\[θ|𝐱\] chính là Bayes estimator giúp minimize Bayes risk function khi loss dùng squared error loss. Còn khi loss dùng absolute error thì Bayes estimator giúp minimize Bayes risk sẽ là median của posterior distribution.
>
>
>
> Còn trong Bishop, một hướng đi, là ta đi tìm 𝐰 giúp maximize cái posterior π(𝐰|t,x) này. Mà thực ra, trong bài toán này p**osterior hóa ra cũng là Gaussian**, nên tìm w có posterior lớn nhất **cũng là lấy mean của posterior** thôi
>
>
>
> Và khi đó ta sẽ thấy cách làm này cũng sẽ chính là tương đương với giải bài toán regularized least square: tức là minimize sum squared error với regularization term là hàm bậc hai của 𝐰.
>
>
>
> Và khi có 𝐰\* maximize posterior rồi thì ta có thể dùng nó để dự đoán cho new x: y(x, 𝐰\*)
>
>
>
> Cũng đồng nghĩa là lấy mean của f(t|x,𝐰\*) là Normal(y(x, 𝐰\*), 1/β) để dự đoán cho t.
>
>
>
> Nhưng cách làm Bayesian toàn diện hơn: là bằng cách marginalizing over 𝐰 của f(t,𝐰|x,**x,t**) ta sẽ có f(t|x, 𝐱,𝐭) không phụ thuộc 𝐰, tức là predictive distribution:
>
>
>
> f(t|x,𝐱,𝐭) = ∫f(t,𝐰|x,𝐱,𝐭)d𝐰 = ∫f(t|x, 𝐰) π(𝐰|𝐱,𝐭) d𝐰 với π(𝐰|𝐱,𝐭) là posterior của 𝐰.

<br>

<a id="node-3ve6hfk"></a>

###### Optimal Least Squares Predictor

<p align="center"><kbd><img src="assets/6w9531itl2u.png" width="80%"></kbd></p>

> [!NOTE]
> Vì ta đang deal với những công thức rất phức tạp, cảm thấy cần thiết phải liên tục liên kết các kiến thức Bishop với Casella nên mình nên tóm tắt bối cảnh chút xíu: Phần này đang nói về decision theory apply cho bài toán regression. Như đã biết, quá trình giải bài toán học máy thường sẽ bao gồm giai đoạn inference, và dựa trên đó, kết hợp với decision theory để đưa ra quyết định sao cho tối ưu.
>
>
>
> Giai đoạn inference, đối với bài toán regression, có thể coi như là đi tìm predictive distribution, f(t|𝐱), là posterior distribution của t (vs prior distribution là f(t) - phân phối marginal của t).
>
>
>
> Và dựa trên đây, decision theory sẽ cho ta biết sẽ nên dự đoán T là gì.
>
>
>
> Thế thì giống như trong Casella, khi nói về Bayes estimator cho θ, ta bắt đầu coi θ là random variable, để rồi đi tìm posterior của nó π(θ|𝐱). Khi đó, câu hỏi là, vậy ta nên point estimate cho θ thế nào, vì yêu cầu vẫn là point estimate. Câu trả lời là, mình mới nói về loss và risk function trước: Loss function L(δ(𝐱), θ) được định nghĩa là hàm phản ánh sai số giữa estimate δ(𝐱) và θ, có thể dùng squared difference \[δ(𝐱) - θ\]² hoặc absolute difference |δ(𝐱) - θ|. Và ý nghĩa của L(δ(𝐱), θ) là: với observed 𝐗= 𝐱 như vậy, và θ như vậy, thì theo quy trình của δ(**.**) để tính ra δ(𝐱) estimate cho θ, thì sai số là bao nhiêu.
>
>
>
> Để rồi sau đó, ta muốn đánh giá khả năng của δ(𝐗) một cách tổng quát,xét trên mọi giá trị khả dĩ 𝐱 của 𝐗 luôn, bằng cách tính trung bình của loss trên mọi 𝐱: E\_θ\[L(δ(𝐗), θ\], đây chính là risk function, và nó chỉ còn là một hàm theo θ. Từ đó, ta có thể so sánh risk function của δ(𝐗) này với risk function của δ(𝐗) khác, xem với θ cụ thể thì cái nào nhỏ hơn (có nghĩa là estimator đó tốt hơn), và từ đó, bằng cách minimize cái risk, ta sẽ có được cái tốt nhất.
>
>
>
> Nhưng nếu tiếp cận theo Bayesian, θ cũng là biến, khi đó R(δ(X), θ) cũng là biến ngẫu nhiên tạo bởi θ, nên ta có thể tính kì vọng của nó, dưới phân phối prior của θ, E\[R(δ(𝐗), θ)\] = ∫\_Θ R(δ(𝐗), θ)) π(θ) dθ, đây là Bayes risk biến đổi chút nó sẽ bằng
>
>
>
> i) ∫\_X \[ ∫\_Θ L(θ, δ(𝐱)) π(θ|𝐱) dθ \] f(𝐱) d𝐱, thì ∫\_Θ L(θ, δ(𝐱)) π(θ|𝐱) dθ là E\[L(θ, δ(𝐱)|𝐗=𝐱\] là posterior expected loss (kì vọng của loss, là hàm theo θ, với θ \~ posterior)
>
>
>
> ii) ∫\_X ∫\_Θ L(θ, δ(𝐱) f(𝐱, θ) d𝐱 dθ, đây là kì vọng của loss, dưới joint distribution của X và θ.
>
>
>
> Và khi ta giải bài toán minimize Bayes risk với loss là squared error thì δ(x) tìm được sẽ chính là mean của posterior E\[θ|𝐱\].
>
>
>
> Vậy thì ở phần này trong sách Bishop, ông đang đặt vấn đề tương tự: Ta có posterior distribution f(t|𝐱) thì nên predict T bằng mấy thì sẽ tối ưu theo decision theory? (cũng chính là y chang trong Casella rằng ta đã có posterior π(θ|𝐱) thì nên point estimate cho θ bằng bao nhiêu để tối ưu)
>
>
>
> Để trả lời, ông Bishop mới tính kì vọng của loss với loss tính bằng squared error dưới joint distribution của 𝐗, T f(𝐱, t). Dưới ánh sáng của cuốn Casella, mình thấy rõ đây chính là tương ứng với Bayes risk.
>
>
>
> Và ta mới đi minimize cái E\[L\] này bằng giải tích, kết quả cho ra y như trong Casella: Là mean của posterior E\[T|𝐱\]
>
>
>
> Trong Casella, khi mininize Bayes risk để chứng minh kết quả tương tự, ta làm hơi khác: là xem xét Bayes risk theo công thức i) để rồi, thứ cần minimize là cái posterior expected loss E\[L(θ, δ(𝐱)|𝐗=𝐱\] (vì nó mới dính tới δ)
>
>
>
> minimize E\[(δ(𝐱) - θ)²\] |𝐗=𝐱\], và ví dụ 2.2.6 Chap 2 của Casella nói rằng b khiến minimize E\[(X - b)²\] chính là b = EX nên sẽ cho phép kết luận δ(x) khiến minimize E\[(δ(𝐱) - θ)²\] |𝐗=𝐱\] chính là E\[θ|𝐱\].
>
>
>
> (Trong ví dụ đó, mình cũng chứng minh bằng 2 cách, calculus và cách thứ hai sẽ cũng chính là cách mà phần này gs Bishop nói tới)
>
>
>
> Do đó, để có thể hiểu là gs Bishop làm gì ở đây, mình sẽ viết lại cách chứng minh thứ hai:
>
>
>
> Chứng minh minimize_b E\[(X - b)²\]
>
>
>
> Xét hàm mục tiêu E\[(X - b)²\] = E\[(X - EX + EX - b)²\]
>
>
>
> = E\[(X - EX)² + (EX - b)² +2(X - EX)(EX - b)\]
>
>
>
> = E\[(X - EX)²\] + E\[(EX - b)²\] +2E\[(X - EX)(EX - b)\]
>
>
>
> Xét: E\[(X - EX)(EX - b)\]
>
>
>
> Với phép tính này, thì EX-b coi như constant, nên dùng tính linearity của expectation: E\[cX\] = cEX ⇨ E\[(X - EX)(EX - b)\] = (EX - b) E\[(X - EX)\] = (EX - b)(EX- E\[EX\]) = (EX - b)(EX - EX) = (EX - b)\*(0) = 0
>
>
>
> ⇨ .. = E\[(X - EX)²\] + E\[(EX - b)²\]
>
>
>
> Bài toán trở thành minimize_b E\[(X - EX)²\] + E\[(EX - b)²\]
>
>
>
> tương đương minimize_b E\[(EX - b)²\] (bỏ term ko liên quan biến tối ưu b đi)
>
>
>
> và cái này là kì vọng của một hàm không âm, nên cũng không âm, do đó, giá trị nhỏ nhất của nó là = 0, xảy ra khi b = EX. Chứng minh xong.
>
>
>
> Áp dụng y chang để chứng minh E\[θ|𝐱\] cũng là minimizer của Bayes risk:
>
>
>
> minimize\_δ(𝐱) ∫\_𝐗 \[ ∫\_Θ L(θ, δ(𝐱)) π(θ|𝐱) dθ \] f(𝐱) d𝐱
>
>
>
> dĩ nhiên tương đương minimize\_δ(𝐱) ∫\_Θ L(θ, δ(𝐱)) π(θ|𝐱) dθ, vì chỉ có cái nhân này mới phụ thuộc biến tối ưu δ(𝐱), nếu nó nhỏ nhất, thì tích phân trên toàn miền range X cũng sẽ nhỏ nhất.
>
>
>
> Và again, cũng là minimize E\[L(δ(𝐱), θ)|𝐗=𝐱\], tức posterior expected loss.
>
>
>
> Với L(δ(𝐱), θ) = \[δ(𝐱) - θ\]² thì bài toán có thể chứng minh y chang theo cách trên:
>
>
>
> E\[L(δ(𝐱), θ)|𝐗=𝐱\] = E\[\[δ(𝐱) - θ\]²|𝐗=𝐱\]
>
>
>
> = E\[\[δ(𝐱) - E(θ|𝐗=𝐱) + E(θ|𝐗=𝐱) - θ\]²|𝐗=𝐱\]
>
>
>
> = E\[\[δ(𝐱) - E(θ|𝐗=𝐱)\]² + \[E(θ|𝐗=𝐱) - θ\]² + 2(δ(𝐱) - E(θ|𝐗=𝐱))(E(θ|𝐗=𝐱) - θ) |𝐗=𝐱\]
>
>
>
> = E{\[δ(𝐱) - E(θ|𝐗=𝐱)\]² |𝐗=𝐱} + E{\[E(θ|𝐗=𝐱) - θ\]²|𝐗=𝐱} + 2E{(δ(x) - E(θ|𝐗=𝐱))(E(θ|𝐗=𝐱) - θ) |𝐗=𝐱}
>
>
>
> Xét 2E{(δ(𝐱) - E(θ|𝐗=𝐱))(E(θ|𝐗=𝐱) - θ) |𝐗=𝐱}
>
>
>
> = 2(δ(𝐱) - E(θ|𝐗=𝐱) E{E(θ|𝐗=𝐱) - θ |𝐗=𝐱}
>
>
>
> = 2(δ(𝐱) - E(θ|𝐗=𝐱) {E\[E(θ|𝐗=𝐱)\] - E\[θ|𝐗=𝐱\]}
>
>
>
> = 2(δ(𝐱) - E(θ|𝐗=𝐱) {E(θ|𝐗=𝐱) - E\[θ|𝐗=𝐱\]}
>
>
>
> = 2(δ(x) - E(θ|X=x) {0}
>
>
>
> = 0
>
>
>
> Và bài toán cũng trở thành minimize\_δ(𝐱) = E{\[δ(𝐱) - E(θ|𝐗=𝐱)\]² |𝐗=𝐱} + E{\[E(θ|𝐗=𝐱) - θ\]²|𝐗=𝐱}
>
>
>
> tương đương minimize\_δ(x) E{\[δ(𝐱) - E(θ|𝐗=𝐱)\]² |𝐗=𝐱}
>
>
>
> kết qủa là δ(𝐱) = E(θ|𝐗=𝐱), là mean của posterior π(θ|𝐱).
>
>
>
> nói chung chỉ là nhìn nó rắc rối là do nó đeo thêm cái đuôi conditional on 𝐗=𝐱 để nhắc nhở rằng θ là biến ngẫu nhiên đang tuân theo distribution là posterior π(θ|𝐱) thôi.
>
>
>
> Và giờ mình xét qua phần trình bày của giáo sư Bishop để chỉ ra hoàn toàn y hệt:
>
>
>
> ---
>
>
>
> Giải bài toán tìm y(x) giúp minimize E\[L(y(x), t)\] dưới phân phối joint f(t,x)
>
>
>
> PHẦN DƯỚI ĐÂY XIN QUY ƯỚC TẤT CẢ CHỮ x ĐỀU TỰ HIỂU LÀ VIẾT ĐẬM (𝐱) ĐỂ ĐỠ MẤT THỜI GIAN GÕ,
>
>
>
> Hàm mục tiêu E\[L(y(x), t)\] = ∫∫ L(y(x),t) f(x,t)dxdt (tự hiểu hai cái tích phân là theo range T và 𝐗, y như tích phân ∫\_X ∫\_Θ ở trên vậy)
>
>
>
> Thay squared error loss vào:
>
>
>
> Hàm mục tiêu = ∫∫ {y(x) - t}² f(x,t)dxdt
>
>
>
> = ∫∫ {y(x) - t}² f(t|x)f(x)dxdt
>
>
>
> = ∫∫ {y(x) - t}² f(t|x)f(x)dtdx
>
>
>
> = ∫ \[ ∫ {y(x) - t}² f(t|x)dt \] f(x)dx
>
>
>
> Bài toán minimize hàm mục tiêu ∫ \[ ∫ {y(x) - t}² f(t|x)dt \] f(x)dx
>
>
>
> trở thành tương đương minimize cái cụm này, minimize ∫ {y(x) - t}² f(t|x)dt
>
>
>
> Và cái cụm này, chính là kì vọng của (y(x) - T)² dưới posterior distribution f(t|x): E\[(y(x) - T)²|X=x\]
>
>
>
> (Cái cụm ∫ {y(x) - t}² f(t|x)dt cũng chính là tương đương với ∫\_Θ L(δ(𝐱), θ) π(θ|𝐱) dθ = E\[L(δ(𝐱), θ)|𝐗=𝐱\], posterior expected loss ở trên)
>
>
>
> Và như để nhắc ta nhớ đây là tính kì vọng dưới posterior distribution của t, chứ ko phải là joint distribution T, X nữa, nên ông Bishop mới nói trong sách "we use E\[t|x\] to denote E_t\[t|x\]" nhằm nhấn mạnh chỗ này, vì kí hiệu nó đã trở nên quá phức tạp nhưng nhờ đối chiếu với Casella nên mình hiểu bản chất.
>
>
>
> Rồi, thế thì bài toán là minimize_y(x) {E\[(y(x) - T)²|X=x\]}, để bớt phải đeo cái đuôi X=x nhằm nhắc nhớ T \~ f(t|x), khiến công thức trở nên phức tạp như trên đã thấy ta cứ tạm bỏ cái đuôi này, với chú thích T \~ f(t|x) ở cuối là được.
>
>
>
> Ta cũng làm tương tự, biến đổi hàm mục tiêu:
>
>
>
> E\[(y(x) - T)²\] = E\[(y(x) - ET + ET - T)²\]
>
>
>
> = E\[(y(x) - ET)² + E\[(ET - T)²\] + 2E\[(y(x) - ET)(ET - T)\]
>
>
>
> Xét cái hạng tử cross term: 2E\[(y(x) - ET)(ET - T)\]
>
>
>
> Vì đây là đang tính kì vọng theo posterior f(t|x), nên y(x) - ET là constant, đưa ra ngoài, theo tính linearity:
>
>
>
> 2E\[(y(x) - ET)(ET - T)\] = 2(y(x) - ET) E\[(ET - T)\]
>
>
>
> = 2(y(x) - ET) \[E(ET) - ET\]
>
>
>
> = 2(y(x) - ET) \[ET - ET\]
>
>
>
> = 2(y(x) - ET) . 0
>
>
>
> = 0
>
>
>
> Đây chính là ứng với câu "Substituting into the loss function and performing the integral over t, we see that the cross-term vanishes" của gs Bishop.
>
>
>
> Kết quả còn lại: E\[(y(x) - ET)² + E\[(ET - T)²\] (T \~ f(t|x))
>
>
>
> Nếu tại đây ta lắp E\[(y(x) - ET)² + E\[(ET - T)²\] (T \~ f(t|x)) = ∫ \[y(x) - E(T|X=x\]² f(t|x) dt + ∫ \[E(T|X=x) - t\]² f(t|x) dt
>
>
>
> vô lại ∫ \[ hàm mục tiêu \] f(x)dx thì ta sẽ có công thức 1.90 trong sách:
>
>
>
> ∫ \[ ∫ \[y(x) - E(T|X=x\]² f(t|x) dt + ∫ \[E(T|X=x) - t\]² f(t|x) dt \] f(x)dx
>
>
>
> ∫∫ \[y(x) - E(T|X=x\]² f(t|x) f(x) dt dx + ∫∫ \[E(T|X=x) - t\]² f(t|x) f(x) dt dx
>
>
>
> ∫∫ \[y(x) - E(T|X=x\]² f(t, x) dt dx + ∫∫ \[E(T|X=x) - t\]² f(t|x) f(x) dt dx
>
>
>
> Xét cụm thứ nhất, cái cụm \[y(x) - E(T|X=x\]² ko phụ thuộc t, nên khi tính tích phân theo t, ta đưa ra
>
>
>
> Cụm thứ nhất = ∫\_X \[y(x) - E(T|X=x\]² ∫\_T f(t, x) dt dx
>
>
>
> Và ∫\_T f(t, x) dt, là marginalizing joint pdf của T, X over range T, sẽ được marginal pdf f(x)
>
>
>
> ⇨ Cụm thứ nhất = ∫\_X \[y(x) - E(T|X=x\]² f(x) dx
>
>
>
> .. = ∫\_X \[y(x) - E(T|X=x\]² f(x) dx + ∫∫ \[E(T|X=x) - t\]² f(t|x) f(x) dt dx ⇨ Đây chính là 1.90
>
>
>
> ---
>
>
>
> Trong sách, term thứ hai của 1.90 là ∫ {E\[T|X=x\] - t}² f(x) dx. Mình cho rằng: **term thứ hai có vẻ bị viết tắt** hoặc **thiếu phần tích phân theo t**.
>
>
>
> Dạng đầy đủ về mặt toán học nên là ∫∫ \[E(T|X=x) - t\]² f(t|x) f(x) dt dx,
>
>
>
> và nhờ vậy mới giúp giải thích khúc dưới.
>
>
>
> ---
>
>
>
> Còn nếu giải tiếp bài tóan tối ưu đang làm thì kết quả như đã biết, sẽ ra y(x) giúp minimize cái này, là E(T|X=x)
>
>
>
> (Ứng với câu trong sách "The function y(x) we seek to determine enters only in the first term, which will be minimized when y(x) is equal to E\[t|x\], in which case this term will vanish", nhắc lại, mình luôn theo notation của chuẩn toán, viết hoa với tên biến ngẫu nhiên, viết thường với giá trị biến, còn ông Bishop thì viết thường hết ráo khiến gây lú)
>
>
>
> Để rồi trong 1.90, ∫\_X \[y(x) - E(T|X=x\]² f(x) dx sẽ = 0,
>
>
>
> chỉ còn lại ∫∫ \[E(T|X=x) - t\]² f(t|x) f(x) dt dx
>
>
>
> Và đây chính là gì? Để nhìn ra nó là cái gì, hãy phân tích từng cái:
>
>
>
> E(T|X=x) chính là mean của posterior f(t|x)
>
>
>
> Vậy đây là \[E(T|X=x) - t\]² hàm tính ra bình phương của difference giữa T, \~ f(t|x) và mean E\[T|X=x)
>
>
>
> Nên ∫∫ \[E(T|X=x) - t\]² f(t|x) f(x) dt dx
>
>
>
> = ∫*{range x} \[ ∫*{range t} \[E(T|X=x) - t\]² f(t|x) dt \] f(x) dx
>
>
>
> Cụm ∫\_{range t} \[E(T|X=x) - t\]² f(t|x) dt chính là Variance của T dưới phân phối posterior f(t|x): Var(T|X=x)
>
>
>
> Và ta mới lấy trung bình trên mọi x, ∫\_{range x} \[Var(T|X=x) \] f(x) dx
>
>
>
> Thì cái này, gs Bishop gọi nó Variance của distribution của T lấy trung bình trên mọi x. ("The second term is the variance of the distribution of t, averaged over x.")
>
>
>
> Và theo gs Bishop, cái này nó phản ảnh độ nhiễu động nội tại của target data, và có thể coi như nhiễu (noise).
>
>
>
> Và vì cái này nó HOÀN TOÀN KHÔNG DÍNH GÌ / PHỤ THUỘC y(x), NÊN NÓ ĐẠI DIỆN GIÁ TRỊ NHỎ NHẤT, LÀ PHẦN KHÔNG THỂ GIẢM HƠN NỮA CỦA LOSS FUNCTION.

**🔗 See also:** [Expected Squared Loss Decomposition](./320_the_bias_variance_decomposition.md#node-s3i1j2i)

<br>

<a id="node-nfr9orb"></a>

###### Các Phương Pháp Ước Lượng

<p align="center"><kbd><img src="assets/8dkw46p60cf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6rw53dm4lhq.png" width="80%"></kbd></p>

> [!NOTE]
> Cũng tương tự như classification problem, cũng có các approaches:
>
>
>
> a) Inference joint pdf f(t,x). Rồi marginalizing ra posterior f(t|x). Và make
> decision:  lấy mean E(T|x)
>
>
>
> b) Inference trực tiếp ra posterior f(t|x). Và make decision: lấy mean
> E(T|x)
>
>
>
> c) Học trực tiếp hàm mapping y(x), không cần inference

<br>

<a id="node-ip8foqy"></a>

###### Hàm mất mát Minkowski và q

<p align="center"><kbd><img src="assets/dqv79e2ntrc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/58zu01zfwgo.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng, đại ý là, có những tình huống hàm squared loss sẽ cho ra
> kết quả tệ. Ta phải design hàm loss khác. Một ví dụ là Minkowski loss
>
>
>
> L(y(x), t) = |y(x) - t|^q mà với q = 2 thì nó là squared loss.
>
>
>
> Nhận xét, là với q khác nhau thì hình phạt đối với sai số sẽ khác nhau.
> Vói q = 0.3, có thể thấy loss chỉ nhỉ khi y(x) ≈ t, còn lại thì đều cao.
> q = 1 thì loss sẽ tăng tuyến tính theo sai số. q = 2 thì loss tăng quadratic
> theo sai số. q = 10 thì thì loss nhỏ khi y(x) nằm trong lân cận nào đó
> quanh t, nhưng xa hơn thì tăng rất nhanh.

<br>

