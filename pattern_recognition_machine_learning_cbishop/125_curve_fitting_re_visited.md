# 1.2.5 Curve fitting re-visited.

📊 **Progress:** `9` Notes | `11` Screenshots

---
<a id="node-gdpz55o"></a>

<br>

<a id="node-21cf3yh"></a>

## Curve Fitting Góc Nhìn Xác Suất

<p align="center"><kbd><img src="assets/nma4ep8w7hp.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ta sẽ quay lại bài toán Curve fitting. Lúc trước, ta tiếp cận bài
> toán này ở góc độ là tìm cách (thay đổi tham số của hàm đa thức) để giảm
> thiểu  error.
>
>
>
> Còn trong lần này, ta sẽ tiếp cận nó dưới GÓC NHÌN XÁC SUẤT
> (probability perspective)
>
>
>
> Và từ đó ta sẽ bắt đầu hướng tới cách tiếp cận toàn diện theo trường phái
> Bayesian (như đã nói, sách này của mr Bishop sẽ chuyên về giải bài toán
> học máy theo góc nhìn Bayesian)

**🔗 See also:** [Khớp đường cong hàm đa thức](./11_example_polynomial_curve_fitting.md#node-79h9mtc)

<br>

<a id="node-2pnnmnh"></a>

### Mô hình xác suất khớp đường cong

<p align="center"><kbd><img src="assets/tnzkq2iuz9.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì như đã biết, mục tiêu của bài toán curve fitting (khớp đường cong) là
> ta muốn tái hiện / xây dựng một hàm đa thức mô phỏng hàm số ẩn đằng sau
> quy luật của bộ dữ liệu - vốn được tạo ra theo hàm số t = sin(2πx) + z với z là
> giá trị nhiễu lấy từ phân phối normal(0,1). Và mục đích mô phỏng được hàm
> số này (sin(2πx)) sẽ giúp ta dự đoán được giá trị t từ giá trị x mới một cách
> chính xác.
>
>
>
> Dựa trên cơ sở là ta có một training data set gồm N input (x1,...xn)ᵀ và n
> target value (t1,...tN).
>
>
>
> Thế thì tiếp theo gs Bishop nói một ý rất quan trọng mang tính chất bước
> ngoặt để mình có thể tiếp cận bài toán theo góc nhìn xác suất:
>
>
>
> Đó là: Ta sẽ **THỂ HIỆN TÍNH KHÔNG CHẮC CHẮN / NGẪU NHIÊN CỦA
> TARGET VARIABLE BẰNG CÁCH COI NÓ LÀ RANDOM VARIABLE** và dĩ
> nhiên gắn với random variable thì sẽ có distribution.
>
>
>
> Và ta sẽ đặt ra giả định là biến T (như đã nói, mình cứ theo notation của toán
> thống kê, viết hoa cho tên biến, viết thường cho giá trị) sẽ có phân phối
> Normal với mean là y(x, 𝐰) và variance là 1/β.
>
>
>
> Để rồi pdf của T: f(t | y(x,𝐰),1/β) sẽ là pdf của Normal(y(x, 𝐰),1/β),
>
>
>
> (gs Bishop dùng N kiểu để ý nói là normal pdf, mình hiểu là được)
>
>
>
> Và cũng có có thể ghi là f(t | x,w,β) để nhìn nó như hàm của t dựa trên các giá
> trị x, 𝐰, β (thông qua trung gian y(x, 𝐰) và 1/β)

<br>

<a id="node-ia6n6nm"></a>

#### Phân phối chuẩn điều kiện

<p align="center"><kbd><img src="assets/6ce6qsztfyk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/tfiycxzk77f.png" width="80%"></kbd></p>

> [!NOTE]
> Như vậy, với góc nhìn này, dựa trên x,
> 𝐰, β thì T ~ normal(y(𝐱, w), 1/β)

<br>

<a id="node-8u1p4w9"></a>

##### Phân phối chung và Likelihood

<p align="center"><kbd><img src="assets/81im1ohwcl7.png" width="80%"></kbd></p>

> [!NOTE]
> Đây là đoạn mấu chốt đây:
>
>
>
> Vừa rồi, ta COI gắn với x=x0 thì T  ~ Normal(y(x0, 𝐰), 1/β)
>
>
>
> để rồi pdf của nó là f_T(t| y(x0, 𝐰), 1/β)
>
>
>
> như vậy, với i = 1,2...N, để ta có x=x1,...xN thì ta cũng sẽ có N random variable
> T1, ...TN với:
>
>
>
> Ti ~ Normal(y(xi, 𝐰), 1/β), có (marginal) pdf f_Ti(ti | y(x0, 𝐰), 1/β)
>
>
>
> Và gs nói rằng, giả sử data được lấy mẫu theo lối independent và đều từ
> distribution 1.60 thì ...blah blah:
>
>
>
> Chỗ này cần hiểu vầy, rất quan trọng. Nên ôn lại chút về định nghĩa của random
> sample, trong Stat110 và Casella, đã được biết, random sample size n X1,...Xn
> là một bộ các random variable được thu thập sao cho chúng **mutually
> independent** và có chung một population distribution, gọi là **identically
> distributed**. Có nghĩa là marginal distribution của Xi ~ f(xi|θ) với mọi i (thằng
> nào cũng có chung pdf/pmf f(.|θ) hết.
>
>
>
> Vấn đề là, gs giả định đám Ti này độc lập thì ok đi. Nhưng có thể đặt câu hỏi là
> **chúng có cùng population distribution không**?
>
>
>
> Nguồn cơn thắc mắc là ở chỗ, mean của distribution của Ti lại là hàm phụ thuộc
> x: y(x, 𝐰). Nên rõ ràng là với x khác nhau, ETi = y(xi,w) sẽ khác nhau cho nên
> không thể nói T1 và T2 ứng với x1, x2 là cùng một distribution được.
>
>
>
> Do đó không thể hiểu như bối cảnh của Casella, rằng T1,...Tn đều có chung
> population distribution, chúng chỉ độc lập thôi. Nhưng thật ra, cái ý tiếp theo sau
> đây, **chỉ cần chúng độc lập** là đủ:
>
>
>
> Đó là, ta xét  **JOINT DISTRIBUTION**  của T1,...Tn
>
>
>
> fT1,...Tn(𝐭|x1,..xn,𝐰,β), hay f𝐓(𝐭|𝐱,𝐰,β)
>
>
>
> Vì T1,...Tn độc lập, nên joint distribution của chúng bằng tích marginal
> distribution:
>
>
>
> = fT1(t1|y(x1, 𝐰), 1/β) * fT2(t2|y(x2, 𝐰), 1/β) *...* fTn(tn|y(xn, 𝐰), 1/β)
>
>
>
> = Πi=1:n f(ti| y(xi, 𝐰), 1/β)
>
>
>
> viết theo notation của gs Bishop, chính là 1.61:
>
>
>
> p(𝐭 | 𝐱,𝐰,β) = Πi=1:n N(ti| y(xi, 𝐰), 1/β).
>
>
>
> Và như đã nhắc lại về định nghĩa của hàm likelihood trong các note trước, Với
> sample 𝐗 ~ f(𝐱|θ)thì likelihood là hàm số của θ, kí hiệu: L(θ|𝐱), có độ
> lớn  được đặt bởi độ lớn của hàm joint pdf của 𝐗 tại 𝐱: f(𝐱|θ), và mang ý
> nghĩa là độ hợp lí của θ khi ta quan sát thấy giá trị 𝐗 = 𝐱 (nói nôm na là:
> tao biết giá trị của **X bị quy định bởi θ**, vậy thì nếu tao thấy giá trị cụ thể x của
> nó, thì với các giá trị θ = θ1 thì có hợp lí không / độ hợp lí là bao nhiêu để giải
> thích hiện tượng này (quan  sát được giá trị này của X), thì cái độ hợp lí đó là
> L(θ1|x).
>
>
>
> Vậy ở đây, nói likelihood thì phải hiểu likelihood của cái gì?
>
>
>
> Theo định nghĩa trên, nó là likelihood của tham số θ, chi phối distribution của 𝐗.
> Vậy ở đây, dĩ nhiên là nói về likelihood của tham số chi phối distribution của 𝐓
> = (T1,...Tn). Và trong cái nùi Πi=1:n N(ti| y(xi, 𝐰), 1/β), dĩ nhiên tham số là 𝐰, và 
> β (còn x1,..xn đều là giá trị đã biết)
>
>
>
> Do đó, theo định nghĩa trên, ta sẽ có:
>
>
>
> L((𝐰,β)|**t,x**) = f𝐓(𝐭|𝐱,𝐰,β) = Πi=1:n f(ti| y(xi, 𝐰), 1/β)

**🔗 See also:** [Phân phối hậu nghiệm Normal](./126_bayesian_curve_fitting.md#node-6vqfvyl)

<br>

<a id="node-r1gqc9l"></a>

###### Ước lượng hợp lí cực đại

<p align="center"><kbd><img src="assets/ncvn51248xa.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, như vậy tiếp theo ta làm gì:
>
>
>
> Như hôm qua mình đã ôn lại về point estimator đã học trong Casella.
>
>
>
> Ôn nhanh: trong bài toán thống kê suy luận, point estimation là bài toán mà ta muốn xây dựng một estimator, được định nghĩa là một hàm của sample W(𝐗) để mục đích là với observed data 𝐗 = 𝐱, ta có estimate value W(𝐱) cho θ sao cho chính xác. Và những phương pháp chính bao gồm method of moment, maximum likelihood estimator và Bayes estimator.
>
>
>
> Với ML estimator, được định nghĩa là θ^\_mle(𝐗) = argmax\_θ L(θ|𝐗), mang ý nghĩa là θ khiến tối đa hóa độ hợp lí khi quan sát được giá trị của 𝐗
>
>
>
> Còn Bayes estimator, được định nghĩa là, mean hoặc median của phân phối posterior π(θ|𝐱).
>
>
>
> Vậy thì ở đây, θ chính là (𝐰, β), ta sẽ làm theo cách thứ nhất, xây dựng ML estimator của (𝐰, β). Để rồi lát nữa, ở phần sau ta sẽ làm theo Bayes estimator.
>
>
>
> Như vậy theo định nghĩa trên, ta cần giải bài toán tối ưu sau:
>
>
>
> maximize\_𝐰, β L(𝐰, β | 𝐭,𝐱) = Πi f(ti| y(xi, w), 1/β)
>
>
>
> Thế thì, tương tự như đã nói ở phần trước, ta có thể chuyển bài toán tối ưu gốc này sang các dạng tương đương (equivalent), là các bài toán mà solution của nó cũng là solution của bài toán gốc, mục đích là để dễ làm hơn
>
>
>
> Và ta có vài cách để chuyển, điển hình là thay việc tối ưu hàm mục tiêu f(x) bằng bài toán tối ưu hàm g(f(x)) với g là một hàm monotone. Nên ở đây, vì log(.) là hàm monotone increasing, nên maximize log L cũng là maximize L
>
>
>
> log L(w, β | 𝐭, 𝐱) = log Πi f(ti| y(xi, 𝐰), 1/β)
>
>
>
> Lôi công thức pdf của normal ra ráp vô
>
>
>
> = log { Πi \[1/√\[2π(1/β)\]\] exp\[-\[ti-y(xi,𝐰)\]²/2(1/β)\] }
>
>
>
> = log { \[1/β^(-1/2)√2π\]ⁿ exp\[Σi-\[ti-y(xi,𝐰)\]²/2(1/β)\] }
>
>
>
> = log { \[β^(1/2)/√2π\]ⁿ } + log exp\[Σi-\[ti-y(xi,𝐰)\]²)/2(1/β)\]
>
>
>
> = n log \[β^(1/2)/√2π\] - (β/2) Σi \[ti-y(xi,𝐰)\]²
>
>
>
> = n log β^(1/2) - n log√2π - (β/2) Σi \[ti-y(xi,𝐰)\]²
>
>
>
> = (n/2) log β - (n/2) log (2π) - (β/2) Σi \[ti-y(xi,𝐰)\]²
>
>
>
> = - (β/2) Σi \[ti-y(xi,𝐰)\]² + (n/2) log β - (n/2) log (2π), đây chính là 1.62
>
>
>
> ---
>
>
>
> Rồi, một kĩ thuật nữa để có equivalent (optimization) problem là, thay vì maximize hàm objective, ta có thể minimize \[- hàm objective\], cái này đơn giản. Cũng như khi maximize, hay minimize, ta bỏ đi các hằng số không dính đến biến, vì maximize f(x) thì cũng như maximize f(x) + c.
>
>
>
> Và một ý nữa như đã nói ở note trước (xem link), việc giải bài toán tối ưu hai biến, có thể làm theo từng biến lần lượt. Nên ở đây, ta có thể maximize over w trước, để tìm w\*. Sau đó maximize over β, để có β\*.
>
>
>
> Dĩ nhiên w\*, β\* chính là w_ML và β\_ML
>
>
>
> Thử làm:
>
>
>
> Như đã nói, ta sẽ chuyển thành bài toán tìm w\*:
>
>
>
> maximize_w - (β/2) Σi \[ti-y(xi,𝐰)\]² + (n/2) log β - (n/2) log (2π)
>
>
>
> ⇔ maximize_w - (β/2) Σi \[ti-y(xi,𝐰)\]² | bỏ constant
>
>
>
> ⇔ minimize_w (β/2) Σi \[ti-y(xi,𝐰)\]² | maximize objective = minimize negative objective
>
>
>
> ⇔ minimize_w (1/2) Σi \[ti-y(xi,𝐰)\]² | vì nhân objective cho cho constant 1/β
>
>
>
> Mục đích là để tới đây ta thấy cái hàm objective (của bài toán tương đương lúc này chính là SUM OF SQUARED ERROR (y như cách tiếp cận bài toán này bữa trước) để rồi giúp ta hiểu một điều quan trọng:
>
>
>
> **ĐI TÌM w BẰNG CÁCH MINIMIZE SUM OF SQUARED ERROR LOSS CŨNG CHÍNH LÀ VIỆC ĐI TÌM MAXIMUM LIKELIHOOD ESTIMATOR CỦA w VỚI GIẢ ĐỊNH GAUSSIAN NOISE**.
>
>
>
> Gaussian noise là sao?
>
>
>
> ta đã thấy gs giả định Ti \~ Normal(y(xi, 𝐰), 1/β)
>
>
>
> Thế thì, Ti - y(xi, 𝐰) chính là gì:
>
>
>
> Y như việc ta có X \~ Normal(μ, σ²) thì theo location scale theorem X - μ chính là một Normal(0, σ²).
>
>
>
> Vậy, Ti - y(xi, 𝐰) chính là random variable \~ Normal(0, 1/β)
>
>
>
> Như vậy rv có được bằng cách áp hàm error(Ti, y(xi, 𝐰)) = Ti - y(xi, 𝐰) sẽ chính là một random variable \~ Normal(0,1/β)
>
>
>
> Mà ta đã biết y(xi, w) là prediction của mô hình, thì e = error(ti, y(xi, 𝐰)) = ti-y(xi, 𝐰) là sai số của dự đoán.
>
>
>
> Như vậy với giả định Ti \~ Normal(y(xi, w), 1/β), **CŨNG CHÍNH LÀ TA ĐANG GIẢ ĐỊNH RẰNG SAI SỐ CỦA DỰ ĐOÁN SẼ CÓ PHÂN PHỐI NORMAL(0, 1/β)** Đó chính là ý "under the assumption of a Gaussian noise" của thầy Bishop.

**🔗 See also:** [MLE phân phối chuẩn](./124_the_gaussian_distribution.md#node-alwk6lh)

<br>

<a id="node-pbdo1sz"></a>

###### Ước lượng ML w và β

<p align="center"><kbd><img src="assets/papslfupags.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/yqrxkupiyad.png" width="80%"></kbd></p>

> [!NOTE]
> minimize_w (1/2) Σi [ti-y(xi,w)]²
>
>
>
> Rồi, thử đi tìm w_ML
>
>
>
> y(xi, w) = 𝐰ᵀΦ(xi) với Φ(xi) = [1, xi, xi²,...]
>
>
>
> ⇨ (1/2) Σi [ti - y(xi,𝐰)]² = (1/2) Σi [ti - 𝐰ᵀΦ(xi)]²
>
>
>
> = (1/2) (𝐭 - X𝐰)ᵀ(𝐭 - X𝐰) với row i của X = Φ(xi)ᵀ
>
>
>
> = (1/2) (𝐭ᵀ - 𝐰ᵀXᵀ)(𝐭 - X𝐰)
>
>
>
> = (1/2) (𝐭ᵀ𝐭 - 𝐰ᵀXᵀ𝐭 - 𝐭ᵀX𝐰 + 𝐰ᵀXᵀX𝐰)
>
>
>
> = (1/2) (𝐭ᵀ𝐭 - 2𝐭ᵀX𝐰 + 𝐰ᵀXᵀX𝐰)
>
>
>
> = (1/2)𝐰ᵀXᵀX𝐰 - 𝐭ᵀX𝐰 + (1/2) 𝐭ᵀ𝐭
>
>
>
> Đây là quadratic function của 𝐰.
>
>
>
> Với quadratic function f(x) = (1/2)xᵀPx + qᵀx + r (x là vector)
>
>
>
> thì gradient là Px + q
>
>
>
> ∇f(𝐰) = XᵀX𝐰 - Xᵀ𝐭
>
>
>
> Điều kiện cần tối ưu bậc nhất: ∇f(𝐰) = 0
>
>
>
> ⇔ XᵀX𝐰 - Xᵀ𝐭 = 0
>
>
>
> ⇔ 𝐰 = (XᵀX)⁻¹Xᵀ𝐭
>
>
>
> Và dĩ nhiên đây chỉ là critical point, cần check secondary test: Hessian tại w*
> có positive semi definite thì mới đủ kết luận w* là local minimum
>
>
>
> Dễ thấy Hessian chính là XᵀX, và đương nhiên nhờ MIT 1806 ta biết,  nó gọi là
> Gram matrix, chắc chắn là positive semi definite vì: Check quadratic form:
> zᵀ(XᵀX)z = (Xᵀz)ᵀ(Xᵀz) = ||Xz||² ≥ 0 ∀z.Và đây chính là 𝐰_ML, dĩ nhiên nó là hàm của 𝐭,𝐱 (vì 𝐗 là hàm
> của 𝐱)(nói vậy để soi chiếu kiến thức trong Casella: point estimator của θ  ,
> θ^_ml(𝐗) là hàm của sample 𝐗)
>
>
>
> Sau đó, ta tiếp tục giải bài toán minimize - log L(𝐰_ML, β|t,x) để tìm β_ML.
>
>
>
> Nhưng tiện thể nói thêm tí về w_ML = (XᵀX)_⁻¹Xᵀ𝐭
>
>
>
> Nó chính là cái gì nhỉ:
>
>
>
> Còn nhớ trong MIT 1806, nói về bài toán tìm projection matrix onto C(A). Lập
> luận như sau: giả sử có vector b, để tìm p là hình chiếu của b lên C(A) Ta làm
> như sau: p ∈ C(A) ⇨ p = Ax^ (p thuộc C(A) nên chắc chắn tồn tại linear
> combination các cột của A để tạo ra p). Phần dư e = b - p sẽ vuông góc với
> C(A), mà C(A) và left nullspace N(Aᵀ) orthogonal complement, nên e phải ∈
> N(Aᵀ), đồng nghĩa: Aᵀe = 0. Vậy Aᵀ(b-p) = 0 ⇔ Aᵀb = Aᵀp ⇔ Aᵀb = AᵀAx^. Đây
> chính là normal equation.
>
>
>
> Và nếu A full column rank, AᵀA sẽ full rank / invertible
>
>
>
> ⇨ x^ = (AᵀA)⁻¹Aᵀb ⇨ p^ = Ax^ = (AᵀA)⁻¹Aᵀb = Pb
>
>
>
> ⇨ P = A(AᵀA)⁻¹Aᵀ chính là projection onto C(A) matrix
>
>
>
> Vậy xem lại cái phương trình XᵀX𝐰 - Xᵀ𝐭 = 0 ở trên để thấy nó chính là
> normal equation, đi tìm 𝐰, là hệ số giúp linear combination các cột của XᵀX
> cho ra 𝐭.
>
>
>
> Và X𝐰 = chính là gì, chính là projection của 𝐭 lên C(𝐗)
>
>
>
> Mà X**w là gì nhìn lại coi:** Với X là matrix mà row i là Φ(xi)ᵀ thì X𝐰 chính là
> vector [Φ(x1)ᵀ𝐰, Φ(x2)ᵀ𝐰, ...]  = [y(x1,𝐰),...y(xn,𝐰)]
>
>
>
> Từ đó giúp mình hiểu bản chất của bài toán least square này cũng chỉ là t**ìm
> hình chiếu của vector** 𝐭 **lên không gian** C(𝐗), như trong MIT 1806 đã học
> với thầy Strang
>
> Tiếp, giải bài toán minimize - log L(𝐰_ML, β|t,x) để tìm 1/β_ML.
>
>
>
> Xét hàm objective - (β/2) Σi [ti-y(xi,𝐰_ML)]² + (n/2) log β - (n/2) log (2π), lúc này
>
>
>
> tương tự, ta sẽ chuyển về bài toán equivalent bằng cách bỏ các constant đi
>
>
>
> (chú ý (β/2) Σi [ti-y(xi,𝐰_ML)]² + (n/2) log β - (n/2) log (2π) đã đang là log L rồi,
> giờ ta chỉ thêm dấu trừ để chuyển maximize thành minimize và bỏ các constant
> đi thôi)
>
>
>
> minimize_β - { - (β/2) Σi [ti-y(xi,𝐰_ML)]² + (n/2) log β] }, đặt là f(β)
>
>
>
> df(β)/dβ = d/dβ {(β/2) Σi [ti-y(xi,𝐰_ML)]² - (n/2) log β]}
>
>
>
> = d/dβ { (β/2) Σi [ti-y(xi,𝐰_ML)]²} - d/dβ [(n/2) log β]
>
>
>
> = Σi [ti-y(xi,𝐰_ML)]² d/dβ (β/2) - (n/2) d/dβ (log β)
>
>
>
> = (1/2) Σi [ti-y(xi,𝐰_ML)]² - (n/2) 1/β
>
>
>
> Again, dùng first order optimality condition:
>
>
>
> df(β)/dβ = 0 ⇔ (1/2) Σi [ti-y(xi,𝐰_ML)]² - (n/2) 1/β = 0
>
>
>
> ⇔ Σi [ti-y(xi,𝐰_ML)]² - n/β = 0
>
>
>
> ⇔ Σi [ti-y(xi,𝐰_ML)]² = n/β 
>
>
>
> ⇔ (1/n) Σi [ti-y(xi,𝐰_ML)]² = 1/β
>
>
>
> Vậy 1/β_ml = (1/n) Σi [ti-y(xi, 𝐰_ML)]² chính là công thức 1.63 trong sách.

<br>

<a id="node-iw7c6u7"></a>

###### Ước lượng ML, Phân phối tiên đoán

<p align="center"><kbd><img src="assets/407bokzgphh.png" width="80%"></kbd></p>

> [!NOTE]
> Recall sơ lại một chút, so sánh với những gì mình học về ML estimator của
> Casella để soi sáng:
>
>
>
> Trong Casella, để thực hiện một inference point estimation cho θ, tham số chi phối
> phân phối xác suất của sample 𝐗: (X1,...,Xn) ~ f(𝐱|θ). Thì ta có ba phương
> pháp quan trọng. MoM, MLE và Bayes.
>
>
>
> Với MLE: được định nghĩa là θ^_mle(𝐗) = argmax_θ L(θ|𝐗),
>
>
>
> Với Bayes: Thì ta sẽ theo trường phái Bayesian để coi θ như random variable có
> prior và posterior distribution π(θ) và π(θ|𝐱), từ đó bằng cách lấy mean hoặc
> median của π(θ|𝐱): Ví dụ E[θ|𝐗], thì đó chính là Bayes estimator 
> minimize Bayes risk  với squared error loss 
>
>
>
> (Bayes risk = ∫R(θ, δ(𝐗))π(θ)dθ) = R(θ, δ(𝐗)) = E_θ[L(δ(𝐗), θ)])
>
>
>
> Thế thì đó là kíên thức ở bối cảnh lí thuyết thống kê. Còn sang áp dụng cho bài
> toán curve fitting. Mình cần làm rõ vài điểm để kết nối với kiến thức  nền ở trên:
>
>
>
> Ta thấy điểm quan trọng trong lập luận sẽ là: Ta thể hiện tính chất uncertainty theo
> góc nhìn xác suất, bằng cách giả định Ti là biến ngẫu nhiên tuân theo phân phối
> Normal(y(xi, 𝐰), 1/β), điều này đồng nghĩa ta cũng đang giả định sai số giữa dự
> đoán của mô hình y(xi, 𝐰) và Ti: error(Tn) = Ti - y(xi, 𝐰) là biến số tuân theo
> phân phối N(0, 1/β).
>
>
>
> Từ đó, ta mới nói về joint distribution của T1,...Tn, vì tính độc lập, nên
>
>
>
> f𝐓(𝐭|𝐰,β) = Πi f(ti|𝐰, β) = Πi N(ti|y(xi, 𝐰),1/β)
>
>
>
> Và từ đó ta xây dựng hàm likelihood của 𝐰, β: L(𝐰, β | 𝐭, 𝐱) = fT(t|𝐰,β)
>
>
>
> = Πi N(ti|y(xi, 𝐰),1/β)
>
>
>
> Và đi maximize hàm này ta sẽ có (𝐰, β)_ML(𝐗,𝐓) là ML estimator của
> (𝐰, β)  Và (w, β)_ML(𝐱, 𝐭) chính là ML estimate của (𝐰, β), mang ý
> nghĩa là với giá trị quan sát được (𝐱, 𝐭) thì (w, β)_ML(x, t) là giá trị của w, β
> có độ hơp lí cao nhất.
>
>
>
> Thế thì một điểm cần nhấn mạnh: Đây dĩ nhiên vẫn chỉ là làm theo trường phái cổ
> điển / Frequentist. Vì dù ra nói là coi Ti là biến, có distribution N(y(xi, w), 1/β) thì
> mean của distribution này, là y(xi, w) và variance 1/β **VẪN ĐANG ĐƯỢC COI
> NHƯ CÓ GIÁ TRỊ CỐ ĐỊNH NHƯNG CHƯA BIẾT (FIXED UNKNOWN**
>
>
>
> **Chỉ khi nào ta coi y(xi,w), 1/β như random variable, cũng là coi w, β là random
> variable, và xem xem posterior distribution của nó. Thì lúc đó mới là ta tiến sáng
> Bayesian approach.**
>
>
>
> Như vậy, giúp làm rõ chỗ dễ gây confuse này.
>
>
>
> Với việc dùng (w, β)_ML, ta sẽ có phân phối xác suất của Ti. Và cũng hiểu rằng,
> cũng như θ^_mle(x)  **chỉ là giá trị θ hợp lí nhất**  giải thích cho dữ liệu quan sát được
> X = x, chứ  **chưa chắc nó đã là giá trị chính xác của θ**.
>
>
>
> Nên phân phối N(y(xi, w_ML), 1/ β_ML) chỉ là phân phối tạm gọi là hợp lí nhất dựa
> trên quan sát được data (x,t) mà thôi
>
>
>
> Và nó được gọi là  **predictive distribution**  ta sẽ dùng nó để đưa ra dự đoán:
>
>
>
> Với một giá trị x mới, ta có predictive distribution của t: N(y(x, 𝐰_ML), 1/β_ML).
>
>
>
> Dĩ nhiên, mình có thể lấy mean của distribution này, vì đây là Normal nên nó là nơi
> có pdf cao nhất.
>
>
>
> ====
>
>
>
> Tới đây chợt nhớ đến language model: Trong các lớp NLP như NLP Spec,
> DLSpec, cs224n mình đã biết các mô hình ngôn ngữ, những mô hình xịn nhất hiện
> nay đều là dự đoạn token tiếp theo dựa trên context là những token xung quanh.
> Thế thì, cái mà ta cần dự đoán, trong bài toán đó, là một trong những từ trong
> dictionary (đã được tokenized), thì bây giờ nhìn lại, có thể thấy, nó chính là một
> multi-nomial random variable (phiên bản khái quát của binomial), vì  possible
> outcome của nó là một trong một dải các options - là các tokens trong dictionary,
> đúng hơn là id của chúng.
>
>
>
> Và cái distribution output ra, (bởi hàm softmax) chính là predictive distribution, để
> rồi từ đó người ta có thể chọn token có xác xuất cao nhất hoặc chọn random từ
> một set các token có xác suất cao nhất.
>
>
>
> Các mô hình ngôn ngữ lớn hiện nay (lõi transformer) vẫn là có cái lõi này.

**🔗 See also:** [Thành phần phương sai dự đoán](./126_bayesian_curve_fitting.md#node-ejt1ih6)

<br>

<a id="node-20mqbje"></a>

###### Phân phối Bayesian của w

<p align="center"><kbd><img src="assets/sgbuy6um7us.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đây mới là lúc tiến sang lãnh địa Bayesian. Như đã ôn lại ở note trước,
> trong Casella, khi ta coi θ là random variable để rồi chọn cho nó một prior
> distribution nào đó phản ảnh hiểu biết sơ khai của ta về nó, sau đó, dùng
> Bayes rule để xây dựng distribution của θ dựa trên quan sát 𝐗 = 𝐱, mang
> ý nghĩa là cập nhật lại hiểu biết của ta về θ nhờ quan sát thấy sự kiện 𝐗 =
> 𝐱 xảy ra. Và dùng cái distribution này để làm inference / estimator θ. Thì đó
> chính là Bayes estiamtor θ^_B(𝐗).
>
>
>
> Vậy nên, ở đây, ta sẽ bắt đầu coi w, β như random variable. và chọn prior
> distribution cho nó.
>
>
>
> Cụ thể là với w, gs Bishop cho rằng nó có phân phối Normal(0, α^-1 * 𝐈). Cái
> này là sao?
>
>
>
> Ta biết 𝐰, là **vector** các hệ số của hàm đa thức: [1, w1, w2,...wM] vì hàm
> đa thức là 1 + w1x^1 + w2x² + ...wMx^M. Nên giờ coi nó là random variable,
> thì tức là **w lúc này là vector of random variables [1, w1, w2,...wM]**  Đáng lẽ
> tới đây mình nên chuyển thành 𝐖 = [1, W1,...WM] để nhất quán với quy tắc
> kí hiệu của Casella: Chữ hoa cho tên biến, chữ thường cho giá trị biến.
>
>
>
> Thế thì, chọn phân phối Normal(0, α^-1 * 𝐈) cho 𝐖 chỉ đơn giản nói là: Wi
> đều có phân phối Normal(0, (1/α))
>
>
>
> Mấy phần trước gs đã nói về pdf của multivariate Normal, mình cũng đã tự
> derive lại để hiểu bản chất. thì covariance matrix Σ = (1/α) * 𝐈 cho thấy
> variance của W1,..WM đều bằng 1/α và covariance giữa chúng đều bằng 0.
>
>
>
> Ta còn nhớ trong Stat110 và Casella đã học: Covariance = 0 thì chưa chắc đã
> độc lập, nên ko thể gọi W1,..WM là iid được. Tuy nhiên, còn nhớ trong  Casella,
> bổ đề 5.3.3 giúp nói rằng, với Normal random variables, thì tính độc lập và
> covariance của chúng là là một, tức là, covariance bằng 0 sẽ đồng nghĩa rằng
> chúng độc lập. Do đó ở đây, W1,...WM có tính iid: độc lập và cùng distribution
> Normal(0, (1/α))
>
>
>
> Theo công thức 1.52 (xem link) pdf của N(**μ**, **Σ**)
>
>
>
> = [1/(2π)^D/2] (1/|**Σ**|^1/2) exp {-1/2(𝐱 - **μ**)ᵀ Σ⁻¹ (𝐱 - **μ**)}
>
>
>
> **Σ** = (1/α) 𝐈 ⇨det **Σ** = (1/α)^(M+1);
>
>
>
> pdf của W: f(𝐰|α) = N(𝐰|0, (1/α) 𝐈)
>
>
>
> = [1/(2π)^(M+1)/2] (1/1/α)^(M+1)) exp {-1/2(𝐰 - 0)ᵀ α (𝐰 - 0)}
>
>
>
> = [α/(2π)^(M+1)/2] exp {-(α/2)𝐰ᵀ𝐰} → đây là 1.65 trong sách
>
>
>
> -----
>
>
>
> α, là tham số chi phối tham số (variance) của distribution, nên người ta gọi nó
> là  siêu tham số (hyper-parameter).
>
>
>
> -----
>
>
>
> Tiếp, như đã biết đã có prior distribution π(θ), ta sẽ dùng Bayes rule để xây
> dựng posterior:
>
>
>
> π(θ|𝐱) = f(𝐱|θ) π(θ) / f(𝐱) với f(x|θ) là joint distribution của sample 𝐗,
> f(𝐱) có thể coi là prior distribution của 𝐗 cũng được nhưng thường ta không
> care nó, mà chỉ coi nó như hằng số, và nó đóng vai trò là normalizing constant,
> giúp đảm bảo tính valid của pdf π(θ|𝐱) (sum / integral over range θ ra được
> 1 và không âm)
>
>
>
> Do đó ta sẽ chuyển sang dùng kí hiệu tỉ lệ thuận:
>
>
>
> π(θ|𝐱) ∝ f(𝐱|θ) π(θ)
>
>
>
> Vậy thì ở đây cũng vậy:Gs Bishop nói rằng posterior distribution của 𝐰:
>
>
>
> π(𝐰|𝐱,𝐭,α,β) ∝ f(𝐭|𝐱,𝐰,β) π(𝐰|α) (mình vẫn dùng kí hiệu π, và f,
> chả sao)
>
>
>
> Mình có thể đặt câu hỏi:
>
>
>
> i) θ là tham số, ở đây tương ứng phải là cả w, và β chứ nhỉ.
>
>
>
> Nên ở đây có thể hiểu là ta chỉ đang xét Bayes estimator của w, chưa xét của
> β. nên β ở đây coi như đã biết.
>
>
>
> ii) vì sao lại là π(𝐰|α), prior trong casella là π(θ) thôi mà:
>
>
>
> → Là vì 𝐰 ~ Normal(0, (1/α) * 𝐈), nên nó vẫn phụ thuộc α, nhưng đây vẫn
> là prior distribution vì posterior là distribution dựa trên quan sát 𝐗 = 𝐱 (tức
> là 𝐓 = 𝐭) kìa.

<br>

<a id="node-8z48xwr"></a>

###### Ước lượng Bayes và MAP

<p align="center"><kbd><img src="assets/g9o488zi7x9.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, tới đây, với việc ta có π(𝐰|𝐱,𝐭,α,β) ∝ f(𝐭|𝐱,𝐰,β) π(𝐰|α)
>
>
>
> thì làm gì nữa?
>
>
>
> Đối chiếu với việc tìm Bayes estimator trong Casella: Với công thức posteriori
> π(θ|𝐱) = f(𝐱|θ) π(θ) / f(𝐱), mình sẽ áp công thức f(𝐱|θ) và π(θ) vô, triển khai
> ra và xác định được nó là kernel của pdf của distribution nào đó, và từ đó với f(𝐱)
> đóng vai normalizing constant thì ta sẽ kết luận distribution của θ given 𝐗 = 𝐱.Xong, ta sẽ lấy kì vọng của cái này E[θ|𝐱], và đó sẽ chính Bayes estimator giúp
> minimize sum squared error loss Bayes risk function.(nếu chọn loss là absolute error loss thì
> Bayes estimator minimize Bayes risk sẽ là median của π(θ|𝐱)
>
>
>
> Còn trong bài toán machine learning này, ta làm gì?
>
>
>
> → Ta sẽ thay f(𝐱|θ) = L(θ|𝐱) (cơ bản chỉ là đổi tên gọi, hay đổi góc nhìn từ việc
> xem nó là hàm pdf của 𝐗 tại 𝐱 sang góc nhìn là hàm likelihood của θ)
>
>
>
> Khi đó ta có π(θ|𝐱) = L(θ|𝐱) π(θ) / f(𝐱), xem nó như hàm g(θ|𝐱) nào đó. Và
> ta sẽ đi maximize over θ cái này.
>
>
>
> Đây gọi là **MAXIMIZE POSTERIORI**
>
>
>
> Chỗ này suy ngẫm tí xíu: Trong sách Casella khi nói về Bayes estimator thì thường
> **chỉ nói rằng ta sẽ lấy mean của posterior distribution**. Còn ở đây, trong machine
> learning, ta **lại đi tìm θ khiến maximize** π(θ|𝐱). Ngẫm lại, thì không phải
> distribution nào cái mean cũng là nơi có pdf cao nhất.
>
>
>
> Nhưng ví dụ với normal, thì mean cũng là nơi có pdf cao nhất.
>
>
>
> Và 1.2.6 gs Bishop sẽ nói về ý này.
>
>
>
> -----
>
>
>
> Rồi, quay lại bài toán này, làm như trên vừa nói, thay
>
>
>
> ta sẽ đi giải bài toán: maximize_𝐰 π(𝐰|𝐱,𝐭,α,β)
>
>
>
> nó sẽ tương đương maximize_𝐰 f(𝐭|𝐱,𝐰,β) π(𝐰|α)
>
>
>
> equivalent: maximize_𝐰 log [L(𝐰|𝐭,𝐱,β) π(𝐰|α)] = log L(𝐰|t,x,β) + log
> [π(𝐰|α)]
>
>
>
> term đầu tiên chính là 1.62: [- (β/2) Σi [ti-y(xi,𝐰)]² + (n/2) log β - (n/2) log (2π) ]
>
>
>
> term thứ hai: log { [α/(2π)^(M+1)/2] exp {-(α/2)𝐰ᵀ𝐰} }
>
>
>
> = log [α/(2π)^(M+1)/2] + log exp {-(α/2)𝐰ᵀ𝐰}
>
>
>
> = log [α/(2π)^(M+1)/2] - (α/2)𝐰ᵀ𝐰
>
>
>
> Bài toán trở thành: maximize objective function:
>
>
>
> \- (β/2) Σi [ti-y(xi,𝐰)]² + (n/2) log β - (n/2) log (2π) ] + log [α/(2π)^(M+1)/2 -
> (α/2)𝐰ᵀ𝐰
>
>
>
> và ta sẽ chuyển thành bài toán tương đương tiếp: bỏ các constant không dính tới w
> đi,  nhân cho constant dương 2/β, maximize_𝐰 { - Σi [ti-y(xi,𝐰)]² - (α/β) 𝐰ᵀ𝐰 }
>
>
>
> và chuyển tương đương lần cuối: maximize thành minimize negative:
>
>
>
> minimize_𝐰 { Σi [ti-y(xi,𝐰)]² + (α/β)𝐰ᵀ𝐰 }
>
>
>
> Và lúc này, nó hiện hình ra đây  **CHÍNH LÀ BÀI TOÁN MINIMIZE SUM SQUARED
> ERROR FUNCTION CÓ REGULARIZER**  mà trong phần 1 (xem link) mình đã làm:
> thêm regularizer vào total error để giúp giảm overfit, với regularizer hyperparam là λ =
> α / β
>
>
>
> Từ đó giúp mình hiểu được rằng: Khi ta giải bài toán curve fitting bằng cách minimize
> error function dùng sum squared error có regularizer là quadratic function của param
> thì thật ra ta đang giải bài toán maximizing posterior distribution với prior được chọn là
> Normal

**🔗 See also:** [Kỹ thuật Regularization và Shrinkage](./11_example_polynomial_curve_fitting.md#node-bwb4qwy) · [Iterative Estimation of Alpha](./352_maximizing_the_evidence_function.md#node-vstyyq2)

<br>

