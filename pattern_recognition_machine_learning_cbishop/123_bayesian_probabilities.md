# 1.2.3 Bayesian probabilities

📊 **Progress:** `11` Notes | `14` Screenshots

---
<a id="node-g0j8l3h"></a>

<br>

<a id="node-dls8evk"></a>

## Xác suất Bayesian

<p align="center"><kbd><img src="assets/85bybs2d4s2.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là như hồi đầu đến giờ, thông qua mấy cái ví dụ như lấy cam táo từ
> trong  hộp xanh đỏ, ta nhớ và cũng đã nhận định rằng gs đang nhìn xác
> suất theo trường phái cổ điển (frequentist / classical)
>
>
>
> Trường phái này nhìn nhận xác suất của một event theo kiểu TỈ LỆ XUẤT
> HIỆN của event, nếu như ta lặp lại thử nghiệm vô số lần.
>
>
>
> (Trong Casella, ta cũng biết, theo trường phái này, tham số population θ
> của distribution là unknown fixed vs trường phái Bayesian coi nó là random
> variable)
>
>
>
> Trong khi đó, với Bayesian, xác suất của event phản ánh niềm tin mà event
> đó sẽ xảy ra.
>
>
>
> Điều này khiến nó phù hợp với các event kiểu như "băng sẽ tan hết ở hai
> cực cuối thế kỉ này" - vốn dĩ là một event khó mà nghĩ theo kiểu tỉ lệ xảy ra
> khi thực hiện vô số lần của Frequentist (vốn chỉ phù hợp với các event kiểu
> như tung đồng xu ra mặt ngửa)
>
>
>
> Thế thì với Bayesian approach, nó cho ta cách tiếp cận rất hay, đó là, giả
> sử ban đầu ta có một ý niệm nào đó về khả năng event băng tan sẽ xảy ra.
> Ví dụ, ta nghĩ nó khó xảy ra.
>
>
>
> Nhưng sau đó, với quan sát thực nghiệm khoa học, ta phát hiện ra rằng, tốc
> độ băng tan nhanh hơn ta nghĩ. Đó sẽ giống như bằng chứng, giúp ta cập
> nhật lại niềm tin về khả năng xảy ra của event này.
>
>
>
> Và thông qua Bayes rule, ta sẽ làm điều vừa nói (cập nhật lại niềm tin) bằng
> cách tính xác suất của event dựa trên sự kiện quan sát được. Từ đó, có thể
> dựa vào đó để đưa ra những quyết định tối ưu

<br>

<a id="node-5l04ilf"></a>

### Cơ sở xác suất Bayes

<p align="center"><kbd><img src="assets/grhdo465o4a.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này đại ý gs nêu vài luận điểm để biện minh cho việc ta có thể dùng
> xác suất để định lượng tính không chắc chắn của hiện tượng

<br>

<a id="node-fhacpjo"></a>

#### Xác suất Frequentist & Bayes

<p align="center"><kbd><img src="assets/lubdmdzoxvd.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/7ikt68n03v.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý, gs nói trong lĩnh vực pattern recognition, cũng sẽ là có ích nếu ta có
> **góc nhìn khái quát hơn về xác suất** (ám chỉ cần có góc nhìn theo Bayes)
>
>
>
> Ông nói đại ý là, lấy ví dụ của bài toán fitting hàm đa thức bữa trước, 
> thì với các giá trị quan sát tn, thì tính ngẫu nhiên của chúng, ta hoàn toàn
> có lí khi xem xét xác suất của chúng theo góc nhìn Frequentist.
>
>
>
> Nhưng, với tham số của mô hình, hay rộng hơn nữa, là bản thân cái mô
> hình dùng để mô hình hóa bài toán, cũng có tính chất uncertainty, và
> để deal với nó, ta sẽ cần góc nhìn Bayesian.

<br>

<a id="node-f3jh159"></a>

##### Bayes và Ước lượng Tham số

<p align="center"><kbd><img src="assets/pyuc0iy19vq.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này đại ý là gs Bishop nói là, y như trong ví dụ chọn táo chọn cam. Khi
> ta đặt vấn đề, là xác suất ta đã chọn được hộp đỏ là bao nhiêu. Thì nếu 
> chỉ hỏi khơi khơi, ta sẽ trả lời là 40%, vì đề bài cho, khi thực hiện thí nghiệm
> vô số lần, thì 40% trong số đó, ta sẽ chọn được hộp đỏ. Tuy nhiên, nếu 
> như được cung cấp thêm dữ liệu là, cái quả mà ta đã bốc được trong thí
> nghiệm (nhớ ko, thí nghiệm gồm 2 bước: chọn hộp, và bốc quả) là cam, thì
> dựa vào thông tin đó, niềm tin rằng đã chọn được hộp đỏ sẽ tăng lên (cao
> hơn, lên tới 2/3).
>
>
>
> Thế thì, Bayes rule cho phép ta tính toán với hiện tượng này, nó giúp ta 
> định lượng được sự thay đổi niềm tin của event dựa trên quan sát được
> sự kiện.
>
>
>
> Cái này trong Casella mình đã học rồi, và cũng đã nói nó note nào đó trước
> đây.
>
>
>
> Cụ thể là trong chương 7, về point estimator. Bài toán đặt ra là ta quan sát
> được giá trị của sample X1,....Xn iid ~ f(x|θ), và ta muốn inference giá trị
> của θ.
>
>
>
> Đầu tiên, theo định nghĩa chính thức, estimator của θ là "any function of
> sample" W(X), nói cách khác, any statistic đều có thể làm một estimator.
> Nhưng dĩ nhiên là, với cách định nghĩa này, nó quá mơ hồ, từ đó cần đến
> một vài phương pháp tiếp cận để giúp ta tìm được một estimator tốt, và
> trong sách Casella giới thiệu 3 cái: MoM (Method of Moment, MLE Maximum
> Likelihood Estimator, và Bayes estimator)
>
>
>
> Thế thì, nói về cái thứ hai, maximum likelihood estimator:
>
>
>
> Đầu tiên, ta nhớ lại định nghĩa của hàm likelihood, là một hàm của θ, phản
> ánh độ hợp lí của θ, khi quan sát được dữ liệu 𝐗 = 𝐱, kí hiệu bởiL(θ|𝐱), và nó được define bởi: f(𝐱|θ), tức là hàm joint pdf/pmf của 𝐗, evaluate
> tại x.
>
>
>
> Khi đó, maximum likelihood estimator của θsẽ được define như vầy:Ta sẽ giải bài toán: maximize_θ L(θ|𝐱), thì minimizer của bài toán này, chính
> là MLE, dĩ nhiên khi maximize L(θ|𝐱), ta sẽ được một hàm không còn phụ
> thuộc θ, chỉ còn phụ thuộc 𝐱.
>
>
>
> Nói cách khác, MLE, θ^_mle(𝐗) = argmax_θ L(θ|𝐗)
>
>
>
> và theo định nghĩa của likelihood function, L(θ|𝐱) = f(𝐱|θ)
>
>
>
> ⇨ θ^_mle(𝐗) = argmax_θ f(𝐗|θ), và vì tính iid của random sample 𝐗
>
>
>
> = argmax_θ Πi=1:n f(xi|θ) với f(xi|θ) là marginal distribution của sample Xi(và dĩ nhiên là giống như với mọi i, do tính iid)
>
>
>
> Nếu soi chiếu với định nghĩa của estimator - là any function of sample W(𝐗),
> thì với MLE, cái function đó chính là W(𝐱) = argmax_θ L(θ|𝐱)
>
>
>
> -----
>
>
>
> Nói về cái thứ hai, Bayes estimator, thì như đã nói ở note nào đó gần đây
> Ta sẽ coi θ như random variable, có prior distribution π(θ). Dựa vào Bayes
> theorem, ta xây dựng distribution của θ dựa trên việc quan sát 𝐗 = 𝐱:
>
>
>
> π(θ|𝐱) = f(𝐱|θ) π(θ) / f(𝐱)
>
>
>
> Và mới posterior distribution này của θ, ta sẽ lấy mean hoặc median để
> làm point estimator, đó chính là định nghĩa của Bayes estiamtor:
>
>
>
> θ^_B(𝐗) = E[θ|𝐗] với θ ~ π(θ|𝐱)soi chiếu theo định nghĩa của estimator, thì hàm W(𝐱) chính là hàm E[θ|𝐱]
> với θ ~ π(θ|𝐱)
>
>
>
> Thế thì ở đây, f(𝐱|θ), dĩ nhiên là joint distribution của 𝐗, tại 𝐱 và như trên đã
> thấy nó lại chính là likelihood function L(θ|𝐱).
>
>
>
> Nên posterior distribution của θ có thể ghi là π(θ|𝐱) = L(θ|𝐱) π(θ) / f(𝐱)
>
>
>
> -----
>
>
>
> Với hành trang đó của Casella, quay lại đây để xem gs Bishop nói gì. Thì
> chính là ông coi tham số của mô hình polynomial như θ. Và observed value
> 𝐗 = 𝐱 chính là D = {t1,...tn}
>
>
>
> Để rồi, trước khi quan sát / có data D, ta có thể dùng kinh nghiệm để chọn
> distribution của 𝐰, tức **prior distribution của** 𝐰, kí hiệu là p(𝐰) (tương ứng
> với việc ta dùng kinh nghiệm để chọn π(θ), mà phổ biến có thể là dùng
> Normal hay Unform) cho rằng.
>
>
>
> Sau đó, với giá trị quan sát thấy 𝐗 = 𝐱 (có D), ta sẽ cập nhật lại distribution
> của **w, để có posterior distribution của w**:
>
>
>
> p(𝐰|D) = p(D|𝐰) p(𝐰) / p(D)  (y chang như π(θ|𝐱) = f(𝐱|θ) π(θ) / f(𝐱) ở trên)
>
>
>
> Đây chính là công thức 1.43
>
>
>
> Và vì sự chuẩn bị trên, ta cũng dễ hiểu khi gs Bishop nói, với p(D|𝐰), nếu coi
> nó là hàm theo 𝐰, thì nó chính là likelihood function L(𝐰|D) (y như f(𝐱|θ) chính
> là L(θ|𝐱) vậy)
>
>
>
> Từ đó, có thể thấy dưới ánh sáng Casella, đoạn này của Bishop không có
> gì là khó hiểu.
>
>
>
> Nói thêm, trong Casella, ta cũng biết L(θ|𝐱) không phải là / sẽ là sai nếu diễn
> dịch là xác suất của θ given 𝐱, mà phải là độ hợp lí của θ dựa trên 𝐗 = 𝐱.
> Bởi vì, dù được định nghĩa = f(𝐱|θ), như L(θ|𝐱) là hàm theo θ, coi 𝐱 như cố
> định, không mắc mớ gì mà cho phép tự nhiên nó là một pdf. Hàm pdf/pmf
> phải là π(θ|𝐱).
>
>
>
> Hoặc như cách để check pdf, là dựa vào tính valid của pdf/pmf, thì chỉ cần
> summarize hàm L(θ|𝐱) trên mọi possible value của θ, thì nó không ra 1
> nên nó ko phải là pdf

<br>

<a id="node-ou7tcc1"></a>

###### Hằng số Chuẩn hóa Định lý Bayes

<p align="center"><kbd><img src="assets/22miw5omvi6.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này là sao. 
>
>
>
> Quay lại "bối cảnh Casella"
>
>
>
> π(θ|𝐱) = f(𝐱|θ) π(θ) / f(𝐱)
>
>
>
> ⇔ π(θ|𝐱) = L(θ|𝐱) π(θ) / f(𝐱) 
>
>
>
> Thế thì, với 𝐱, là observed value, vai trò của nó trong các term của đẳng thức 
> trên là fixed. Mà f(𝐱), là marginal pdf của 𝐗, evaluate tại 𝐱, dĩ nhiên, nó không
> âm (tính valid của pdf)
>
>
>
> nên có thể coi như vế trái = hàm theo θ (L(θ|𝐱) π(θ)) chia cho hằng số f(𝐱)
> không âm
>
>
>
> ⇨ vế trái sẽ tỉ lệ thuận với L(θ|𝐱) π(θ), đó là kí hiệu tỉ lệ thuận xuát hiện ở đây
>
>
>
> Và vì vế trái là π(θ|𝐱), là một pdf/pmf hợp lệ nên summarize trên range của θ, 
> ta phải được 1:
>
>
>
> ∫_{range_θ} π(θ|𝐱) dθ = 1
>
>
>
> ⇔ ∫_{range_θ} f(𝐱|θ) π(θ) / f(𝐱) dθ  = 1
>
>
>
> ⇔[ ∫_{range_θ} f(𝐱|θ) π(θ) dθ] / f(𝐱)  = 1 | Đưa hằng số ra khỏi tích phân
>
>
>
> ⇨ f(𝐱) =  ∫_{range_θ} f(𝐱|θ) π(θ) dθ]
>
>
>
> Và áp dụng cái này vào "bối cảnh Bishop" chính là công thức 1.45:
>
>
>
> p(D) = ∫p(D|𝐰)p(𝐰)d𝐰

<br>

<a id="node-h1ylwjp"></a>

###### Nguồn Gốc Bất Định: Frequentist Bayesian

<p align="center"><kbd><img src="assets/u1drtlto2q.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xfs4ab46aup.png" width="80%"></kbd></p>

> [!NOTE]
> đây có vẻ là một ý mới mà trong Casella mình chưa nghe. Trong Casella, khi
> nói đến Bayesian, mình chỉ nghe gs nói rằng, người ta coi θ như random
> variable, vs với Classic approach coi nó như fixed unknown.
>
>
>
> Còn ở đây, đại ý gs Bishop nói, sự khác biệt của hai trường phái, đó là:
> Trong Frequentist, ta sẽ coi w như fixed, và unknown, nên những sai sót sẽ
> đến từ data set D. Còn với Bayesian, thì lại coi data set là fixed, và w là
> random variables nên những tính uncertainty sẽ đến từ w.
>
>
>
> Để làm rõ ý này, hãy nhớ lại kiến thức đã học ở chap 9 Casella: confidence
> interval.
>
>
>
> Cụ thể là trong chap này, mình cũng đã thảo luận cách tiếp cận của cả hai
> trường phái:
>
>
>
> Với confidence interval (hay interval estimator), còn nhớ, theo định nghĩa, nó
> là bài toán mà ta muốn đưa ra một suy luận (inference) về θ theo kiểu θ ∈
> C(𝐗), tức là ước lượng một tập, mà trong phần lớn trường hợp, là một
> interval, có dạng [L(𝐗), U(𝐗)] mà ta đoán sẽ bao phủ được θ.
>
>
>
> Thế thì, sau đó để đánh giá (evaluate) chất lượng của interval estimator, ta
> mới xây dựng khái niệm coverage probability của một interval estimator,
> được định nghĩa là một hàm theo θ, define bởi P_θ[θ ∈ C(𝐗)]
>
>
>
> (Và lấy nhỏ nhất trên toàn param space Θ,  inf_θ ∈ θ P_θ[θ ∈ C(𝐗)] ta sẽ
> có confidence coefficient)
>
>
>
> Thế thì, cái chính muốn nói là, trong góc nhìn này, VIỆC TA KHÔNG CHẮC
> C(𝐗) sẽ chứa θ (để rồi mới đặt vấn đề thể hiện sự không chắc này bằng
> coverage probability) **ĐẾN TỪ BẢN THÂN TÍNH KHÔNG CHẮC CHẮN
> CỦA** C(𝐗).
>
>
>
> Vì bản chất nó là một random set, mà nếu set này là interval, nó sẽ được
> cấu thành bởi hai random variable  / statistic L(𝐗) và U(𝐗). Và 𝐗 thì
> ~ f(𝐱|θ) có distribution phụ thuộc θ, nên L(𝐗) và U(𝐗) cũng vậy, và
> xác suất này sẽ được tính dựa trên distribution của L(𝐗) và U(𝐗) → sẽ
> là một hàm phụ thuộc θ
>
>
>
> Và theo góc nhìn xác suất của Frequentist / Classical, thì như đầu sách đến
> giờ gs Bishop đã nói nhiều lần, góc nhìn đó sẽ là: Cho thử nghiệm vô số  lần
> thì TỈ LỆ XẢY RA LÀ BAO NHIÊU. Với góc nhìn này, ta sẽ hiểu theo kiểu:
> LẤY MẪU (SAMPLING) 𝐗 V**Ô SỐ LẦN** THÌ **TỈ LỆ MÀ TA CÓ ĐƯỢC
> KHOẢNG [L(X), U(X)] CHỨA θ TRONG ĐÓ LÀ BAO NHIÊU.
>
>
>
> Đây chính là ý đầu tiên gs Bishop nói trong đoạn này, là error bar, tính không
> chắc chắn sẽ đến từ distribution của data set D**
>
>
>
> Thế rồi, còn nhớ, sau đó, ta được học qua góc nhìn của Bayesian trong
> vấn đề này, như đã nói, coi θ như random variable.
>
>
>
> Thế thì lúc này, nếu quan sát được 𝐗 = 𝐱, ta sẽ xâu dựng posterior
> distribution của θ: π(θ|𝐱). Và với một set, C(𝐱), hay interval [L(𝐱),
> U(𝐱)], thì khi xét xác suất nó chứa / cover θ sẽ mang ý nghĩa khác:
>
>
>
> P_θ[θ ∈ C(𝐱)|𝐱] lại chính là xác suất của một event gắn với random
> variable θ, dưới phân phối π(θ|𝐱). Và dĩ nhiên, do đó, yếu tố ko chắc,
> hoàn tàon đến từ θ, chứ 𝐱 coi như cố định rồi. Và người ta gọi C(𝐱) là
> Credible set để phân biệt với Confidence set.
>
>
>
> Thì đây chính là tương ứng ý thứ hai trong đoạn này của gs Bishop

<br>

<a id="node-rcntpny"></a>

###### MLE và Hàm lỗi

<p align="center"><kbd><img src="assets/txct5cy3tla.png" width="80%"></kbd></p>

> [!NOTE]
> Nhờ ánh sách Casella mà cái này quá dễ hiểu. Và mình cũng đã review lại
> cái này ở note trước. Nói lại ko thừa:
>
>
>
> Cơ bản là trong Casella, hai cái point estimator quan trọng được dạy là:
> Maximum Likelihood estimator, và Bayes estimator.
>
>
>
> Định nghĩa của MLE: θ^_mle(𝐗) = argmax_θ L(θ|𝐗). Và đây, là estimator
> của trường phái Classical / Frequentist, coi θ như fixed, thì tìm θ khiến
> maximize hàm likelihood L(θ|𝐱) mà bản thân hàm này mang ý nghĩa là
> độ hợp lí của θ khi quan sát thấy 𝐗 = 𝐱. Nói cách ngắn gọn, khi observed
> 𝐗 = 𝐱 thì ML estimate θ^_mle(𝐱) là cái giá trị θ mà việc xuất hiện giá trị
> 𝐱 này của 𝐗 là hợp lí nhất.
>
>
>
> Thế thì ở đây, trước tiên phải nhắc lại, 𝐰 là tham số của hàm y(w, 𝐱) mà 
> giúp sinh ra giá trị quan sát D.
>
>
>
> Do đó **w chính là tương ứng với θ**,
>
>
>
> Để rồi, tương tự như MLE của θ, = argmax_θ L(θ|𝐱)
>
>
>
> thì MLE của w = argmax_w L(w|D).
>
>
>
> Và để giải tìm mle của w, ta sẽ giải bài toán tối ưu không ràng buộc:
>
>
>
> maximize L(w|D)
>
>
>
> Nhờ kiến thức đã học trong Boyd, Nocedal, mình biết về vụ equivalient
> problem:
>
>
>
> Ta chuyển bài toán maximize [something] thành minimize [- something]
>
>
>
> → để có bài toán: minimize  - L(w|D)
>
>
>
> Tiếp, kiến thức về equivalent problem còn nói: Nếu ta có hàm monotone
> increasing g(x)
>
>
>
> thì ta có thể chuyển bài toán minimize f(x) thành equivalient problem:
>
>
>
> minimize g(f(x))
>
>
>
> HIểu đơn giản, là vì g monotone increasing, nên nếu f(x1) ≤ f(x2) thì
> g(f(x1)) ≤ g(f(x2)). Nên tìm ra x* minimize g(f(x)) thì cũng chính là nó
> sẽ minimize f(x) 
>
>
>
> Và hàm log là một hàm monotone như vây
>
>
>
> Do đó ta sẽ chuyển sang giải bài toán minimize - log L(w|D), gọi là error
> function, kết quả vẫn sẽ là ML estimator của w.
>
>
>
> Còn vì sao xài hàm log, là vì, như trong CS231n, CS224n đã học, nó 
> sẽ giúp tăng ổn định khi đối mặt với các vấn đề như tràn số trong máy tính.

<br>

<a id="node-mul6va4"></a>

###### Bootstrap và Error Bars

<p align="center"><kbd><img src="assets/cq3hnl8beli.png" width="80%"></kbd></p>

> [!NOTE]
> Gs Bishop nói sơ đến khái niệm bootstrap, dùng để tính toán error bars theo
> trường phái frequentist (tính errors bars, tạm hiểu là tính toán chất lượng của
> mô hình)
>
>
>
> Cách làm đại khái là thực hiện sampling with replacement từ bộ data  gốc
> 𝐗 = {x1,....xN} L lần, để có L bộ data 𝐗B. Và dùng nó để đánh giá  chất
> lượng của parameter estimate bằng cách xem xét sự biến động của
> prediction giữa các bootstrap data set (Sau này gs sẽ nói rõ hơn)

<br>

<a id="node-7snt2ef"></a>

###### Ưu điểm Bayesian: Kiến thức tiên nghiệm

<p align="center"><kbd><img src="assets/kzs41j78iol.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này là sao.
>
>
>
> À ông nói Bayesian có ưu điểm hơn Frequentist ở chỗ nó "đưa vào / tích
> hợp" nhưng prior knowledge (tạm dịch là những kinh nghiệm, kiến thức có
> sẵn) vào trong mô hình một cách rất tự nhiên (thì bởi đã nói cách tiếp cận
> của nó có  bản chất đã là cập nhật lại niềm tin về khả năng xảy ra của sự
> kiện dựa trên thông tin mới, nhưng ban đầu, đã có cái nền là prior
> distribution - phản ánh niềm tin sẵn có)
>
>
>
> Lấy ví dụ nếu ta tung đồng xu 3 lần mà ra cả 3 head, thì nếu xây dựng ML
> estimator cho θ, thì ta sẽ ra xác suất ra head tiếp là 1, đồng nghĩa dự
> đóan tiếp theo mà tung nữa sẽ luôn ra 1. Trong khi đó điều này rõ ràng là
> ko đúng Thay vào đó nếu xây dưng Bayes estimator thì nó sẽ phản ánh
> prior belief rằng tung đồng xu sẽ chỉ có 50% khả năng ra head thôi, thì kết
> quả nó sẽ khác.
>
>
>
> Thử làm:
>
>
>
> Bối cảnh này, là bài toán ta có 𝐗 = X1, X2, X3 là iid ~ Bern(θ) và x1 =
> x2 = x3 = 1.
>
>
>
> Xây dựng MLE của θ: = argmax_θ L(θ|𝐱)
>
>
>
> Theo định nghĩa likelihood function L(θ|𝐱) = f(𝐱|θ) với f là joint pdf
> của X1, X2, X3
>
>
>
> (pmf của Bern(θ) f(x|θ) = θ^x(1-θ)^(1-x))
>
>
>
> vì tính iid, nó bằng Πi=1:3 f(xi|θ) = Πi=1:3 θ^xi(1-θ)^(1-xi)
>
>
>
> = Πi=1:3 θ^xi Πi=1:3 (1-θ)^(1-xi)
>
>
>
> = θ^Σixi (1-θ)^Σi(1-xi)
>
>
>
> Giải bài toán maximize L(θ|𝐱) = f(𝐱|θ) = θ^Σixi (1-θ)^Σi(1-xi)
>
>
>
> Như thường lệ, ta sẽ dùng hàm log để chuyển thành equivalent problem:
>
>
>
> maximize log L(θ|𝐱) = log [θ^Σixi (1-θ)^Σi(1-xi)]
>
>
>
> = log [θ^Σixi] + log [(1-θ)^Σi(1-xi)]
>
>
>
> = Σixi log θ + Σi(1-xi) log [1-θ], đặt hàm này là g(θ)
>
>
>
> Tới đây, để giải bài toán này, ta dùng calculus thôi, điều kiện cần tối ưu
> bậc nhất:
>
>
>
> g'(θ) = 0
>
>
>
> ⇔ d/dθ [Σixi log θ + Σi(1-xi) log [1-θ]] = 0
>
>
>
> ⇔ d/dθ Σixi log θ + d/dθ Σi(1-xi) log [1-θ]] = 0
>
>
>
> ⇔ Σixi d/dθ log θ + Σi(1-xi) d/dθ log [1-θ] = 0
>
>
>
> ⇔ Σixi (1/θ) + Σi(1-xi) [-1/(1-θ)] = 0
>
>
>
> ⇔ Σixi / θ - (n - Σixi) / (1-θ) = 0
>
>
>
> ⇔ (1-θ) Σixi / θ(1-θ) - θ(n - Σixi) / θ(1-θ) = 0
>
>
>
> ⇔ [(1-θ) Σixi - θ(n - Σixi)] / θ(1-θ) = 0
>
>
>
> ⇔ [Σixi - θΣixi - θn + θΣixi] / θ(1-θ) = 0
>
>
>
> ⇔ [Σixi - θn] / θ(1-θ) = 0
>
>
>
> ⇔ Σixi - θn = 0
>
>
>
> ⇔ Σixi = θn
>
>
>
> ⇔ (Σixi)/n = θ
>
>
>
> Như vậy MLE của θ chính là: sample mean: θ^_mle(𝐗) = Xbar
>
>
>
> Và với observed value x1 = x2 = x3 = 1 ⇨ dự đoán (ml esimate) cho θ =
> (1+1+1)/3 = 1
>
>
>
> Như vậy đồng nghĩa, với việc, dựa trên 3 lần tung ra Head, thì MLE dự
> đoán tham số mô hình là 1, có nghĩa là nó dự đoán lần tung tiếp theo
> cũng sẽ ra 1.
>
>
>
> -----
>
>
>
> Giờ ta sẽ đi tính Bayes estimator: θ^B(𝐗)
>
>
>
> Như đã ôn lại bữa trước, ta sẽ xây dựng posterior distribution của θ,
> π(θ|𝐱) và dùng mean / median để đóng vai trò là point estimator.
>
>
>
> Thế thì lẽ tự nhiên ta phải chỉ định prior distribution π(θ), sau đó mới dùng
> Bayes rule, để tính posterior:
>
>
>
> π(θ|𝐱) = f(𝐱|θ) π(θ) / f(𝐱)
>
>
>
> Giả sử chọn π(θ) = β(a=1,b=1) cũng chính là uniform(0,1). mang ý nghĩa,
> ban đầu ta ko biết xác suất tung đồng xu ra head là bao nhiêu, nên ta trải
> đều ra từ 0% → 100%.
>
>
>
> Khi đó:
>
>
>
> π(θ|𝐱) = [Πi f(xi|θ) [1/B(a, b)] θ^(a-1)(1-θ)^b-1 ] / f(𝐱)
>
>
>
> Xét tử số = [θ^Σixi (1-θ)^Σi(1-xi) [1/B(a, b)] θ^(a-1)(1-θ)^b-1
>
>
>
> = [1/B(a, b)] [θ^Σixi θ^(a-1) (1-θ)^Σi(1-xi) (1-θ)^b-1]
>
>
>
> = [1/B(a, b)] [θ^(Σixi+a-1) (1-θ)^[Σi(1-xi)+b-1]
>
>
>
> = [1/B(a, b)] θ^[(Σixi+a)-1] (1-θ)^[(n-Σixi+b)-1]
>
>
>
> ⇨ π(θ|𝐱) = [1/f(𝐱) B(a, b)] θ^[(Σixi+a)-1] (1-θ)^[(n-Σixi+b)-1]
>
>
>
> Và ta thấy nó có dạng [constant] θ^[(Σixi+a)-1] (1-θ)^[(n-Σixi+b)-1]
>
>
>
> với θ^[(Σixi+a)-1] (1-θ)^[(n-Σixi+b)-1]  chính là kernel của β(Σixi+a,
> n-Σixi+b).
>
>
>
> Nên  [1/f(x) B(a, b)] sẽ đóng vai trò normalizing constant.
>
>
>
> Từ đó kết luận posterior distribution của θ là β(Σixi+a, n-Σixi+b)
>
>
>
> Như vậy prior belief của ta về phân phối của θ, là theo phân phối β với
> tham số a, b thì việc quan sát thấy giá trị của 𝐗, giúp cập nhật lại tham
> số của β, trở thành Σixi+a và n-Σixi+b
>
>
>
> Thế thì như đã nói, với Bayesian approach, ta sẽ dùng mean hoặc
> median của distribution này để làm point estimator cho θ.
>
>
>
> Cụ thể là, nếu dùng mean. thì đó chính là Bayes estimator giúp minimize
> Bayes risk trong trường hợp loss function dùng squared error loss
>
>
>
> nếu dùng loss funciton là absolute error loss, thì Bayes estimator giúp
> minimize Bayes risk chính là median của posterior.
>
>
>
> Vậy thử lấy mean (Bayes estimator minimize Bayes risk với squared error
> loss):
>
>
>
> còn nhớ công thức mean của β(a,b) là a/a+b
>
>
>
> Kêt quả ta có: mean của β(Σixi+a, n-Σixi+b) = Σixi+a/ [Σixi+a + n-Σixi+b]
>
>
>
> = (3+1) / (3+1+3-3+1) = 0.8
>
>
>
> Như vậy, Bayes estimate cho θ chỉ là 0.8, chứ ko phải 1 như ML estimate.
> Cho thấy tác động của prior belief khiến cho estimate ko trở nên cực
> đoan.
>
>
>
> Đây chính là ý "less extreme conclusion mà gs Bishop nói ở  đoạn này".
>
>
>
> -----
>
>
>
> Nói thêm tí xíu, việc chọn prior là uniform(0,1), cũng là β(1,1) thể hiện
> rằng, ta ko biết gì về θ. Nhưng thật ra nếu phải lấy một con số để đoán
> giá trị của θ khi chưa biết gì này, thì chính là ta lấy mean của nó và nó
> chính là 0.5
>
>
>
> (mean của uniorm(0,1) = 0.5, mean của β(1,1) = 1/(1+1) cũng 0.5)
>
>
>
> Để rồi sau khi quan sát kết quả thí nghiệm, ta dần tin rằng đồng xu này có
> xu hướng ra head nhiều hơn, nên nó trở thành 0.8. Nhưng như đã nói ở
> trên, nó vẫn ko thành 1 một cách cực đoan là do prior ban đầu tin rằng nó
> là 0.5.
>
>
>
> Thế thì thằng Gemini nó chỉ cho mình một ý rất hay, mà sau này có thể sẽ
> gặp, đó là, ta có thể chọn β(a=100, b=100) tức là vẫn bằng nhau, nhưng
> lớn hơn thì khi đó đại khái là nó sẽ phản ánh niềm tin ban đầu rằng, θ = 0.
> 5 một cách mãnh liệt hơn.
>
>
>
> Cụ thể là khi ta tính mean của  β(Σixi+a, n-Σixi+b) với a = b = 100 thì nó
> sẽ là:
>
>
>
> (3+100) / (3+100+3-3+100) = 0.507
>
>
>
> con số này chả thay đổi mấy so với 0.5. Phản ảnh rằng, kết quả thử
> nghiệm ko đủ để lung lay niềm tin ban đầu.
>
>
>
> -----
>
>
>
> Một ý nữa, sở dĩ ta chọn β(1,1) làm prior là vì:
>
>
>
> θ mà ta muốn inference, là tham số của Bern distribution của mỗi Xi
> nhưng xét cả bài toán, thì nó chính là tham số của ΣXi ~ binomial(n, θ)
> với n = 3 đã biết.
>
>
>
> Và β là một distribution có tính là conjugate prior của binomial.
>
>
>
> Do đó nếu chọn β làm prior thì posterior của θ cũng sẽ là β với tham số
> cập nhật.

<br>

<a id="node-qiq9m0c"></a>

###### Tranh luận Frequentist Bayesian

<p align="center"><kbd><img src="assets/o7u9as3hbee.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn tiếp theo gs nói về vài tranh luận giữa hai trường phái xem cái nào
> tốt hơn.
>
>
>
> Frequentist thì chê là Bayesian mang tiếng là chọn prior để phản ánh
> những kinh nghiệm sẵn có thì thật ra lại thường chọn để dễ tính, khiến
> truyền cái thiên kiến sai lệch vào trong quá trình.
>
>
>
> Và việc chọn prior cũng gặp khó khăn, và nó lại rất ảnh hưởng.
>
>
>
> Trong khi đó Frequentest thì có những technique để tránh được tình trạng
> này, như cross-validation

<br>

<a id="node-ivoeaz5"></a>

###### Tiếp cận Bayesian hiện đại

<p align="center"><kbd><img src="assets/b1886c1p5bc.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zvrl3b9a1w.png" width="80%"></kbd></p>

> [!NOTE]
> Vài đề cập của tác giả, đến việc sách này sẽ phần lớn là đi theo trường
> phải Bayesian, nhưng vẫn dùng các khái niệm của Frequentist.
>
>
>
> Ông nhắc đến việc sức mạnh tính toán hiện nay cũng như kĩ thuật sampling
> như Monte-Carlo giúp các tiếp cận này được tháo gỡ những rào cản, giúp
> nó phát huy sức mạnh trong nhiều bài toán

<br>

