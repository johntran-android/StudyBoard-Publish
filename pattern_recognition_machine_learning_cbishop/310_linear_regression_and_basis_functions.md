# 3.1.0 Linear Regression and Basis Functions

📊 **Progress:** `7` Notes | `9` Screenshots | `6` AI Reviews

---
<a id="node-djmqx0o"></a>

<p align="center"><kbd><img src="assets/faq5gp78m16.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này đại ý là bữa giờ chủ yếu là ta tập trung vào unsupervied learning, thì chương này ta sẽ nói về supervied learning, cụ thể là bài toán regression - trong đó mục tiêu là dự đoán một giá trị hoặc vector các giá trị liên tục t, dựa trên input là vector D chiều.
>
>
>
> Ta đã gặp bài toán này trong ví dụ khớp hàm đa thức (polynomial curve fitting) rồi, và nó (tức polynomial function) là một ví dụ trong một tập rộng hơn các function, gọi là linear regression function (hàm hồi quy tuyến tính), mà chúng có điểm chung là: đều là hàm tuyến tính đối với các tham số có thể điều chỉnh được (adjustable parameter).
>
>
>
> Và ý chính muốn nói là, chương này ta sẽ vẫn bàn về các hàm này - tuyến tính đối với param, nhưng, ta có thể làm cho nó hiệu quả hơn bằng cách dùng hàm phi tuyến đối với inputs, bằng cách kết hợp tuyến tính các inputs, sử dụng các basis function.
>
>
>
> Nói ngắn gọn thì hiểu đơn giản, là, cái hàm dùng để dự đoán t, là hàm của cả param θ và input x. Thì ta sẽ luôn dùng các hàm tuyến tính đối với θ, có nghĩa là, coi x như constant, thì f(θ, x) = g(θ) là hàm tuyến tính, nhưng với input x thì hàm là phi tuyến. Ví dụ như f(x) = θ1 x1 + θ2 x2², là hàm tuyến tính theo θ = θ1, θ2 nhưng nhưng phi tuyến theo x = (x1, x2)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **92/100**
>
> Bạn đã tóm tắt rất chính xác về trọng tâm thay đổi sang học có giám sát và định nghĩa của hồi quy. Điểm mạnh lớn nhất là cách bạn giải thích và minh họa bằng ví dụ về việc hàm có thể tuyến tính theo tham số nhưng phi tuyến theo biến đầu vào, thể hiện sự hiểu biết sâu sắc. Chỉ cần lưu ý thêm rằng các 'basis function' thường là các hàm phi tuyến của biến đầu vào, và chúng ta kết hợp tuyến tính các hàm cơ sở này.

<br>

<a id="node-btnn2z0"></a>

## Predicting Values and Linear Models

<p align="center"><kbd><img src="assets/d062wn5ryx.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là, đề bài sẽ là. ta có N giá trị quan sát {𝐱1, ....𝐱N} (𝐱i là vector D chiều), cũng như đi kèm là các giá trị target t1, ...tN tương ứng. Mục tiêu sẽ là xây dựng hàm dựa đoán t từ một vector 𝐱 mới.
>
>
>
> Vậy thì đại khái là, ông nói, nếu làm đơn giản, ta có thể xây dựng hàm dự đoán y(𝐱) để dự đoán t một cách trực tiếp.
>
>
>
> Tuy nhiên, với góc nhìn xác suất, ta sẽ muốn xây dựng một cái gọi là predictive distribution (khái niệm đã gặp ở chap 1) f(t|𝐱), vì nó sẽ giúp thể hiện tính uncetainty. Và từ đó, ta sẽ đưa ra dự đoán t, theo cách thức giúp giảm thiểu giá trị trung bình của loss mà ta chọn. Phổ biến hay dùng là squared loss, khi đó, cái cách để đưa ra dự đoán t giúp giảm trung bình squared error loss chính là dùng mean của cái predictive distribution này (chính là cái mà gs nói - conditional expectation of t, E\[t|𝐱\], chính là mean của phân phối f(t|𝐱))
>
>
>
> Cuối cùng, ông nói tuy linear model có nhiều hạn chế đáng kể trong bài toán pattern recognition, ví dụ như khi input space là không gian cao chiều (D lớn), tuy nhiên, mô hình này có những đặc điểm tốt về mặt phân tích (analytical properties) và do đó, nó đóng vai trò nền tảng cho nhiều mô hình phức tạp sau này.
>
>
>
> ---
>
>
>
> Dù mình đoán gs Bishop cũng sẽ nhắc lại, nói lại về cái ý vừa nói ở trên - cái gì mà thay vì xây dựng hàm y(x) dự đoán t, ta xây dựng predictive distribution, và từ đó đưa ra dự đoán, theo cái cách thức nào đó giúp giảm kì vọng (trung bình) loss. Để rồi nếu làm theo cách phổ biến - dùng loss là squared loss thì ta sẽ lấy conditional expectation để dùng dự đoán cho t. Có thể nhớ lại cái này chút xíu:
>
>
>
> Đầu tiên, cái ý mà gs nói xây dựng hàm y(x) dự đoán thẳng ra t, thì đại ý là, ta xây dựng một function dựa trên tham số nào đó, để rồi với x đưa vào, lấy ra t luôn. Nhưng làm như vậy, không phản ánh được tính chất không chắc chắn. Ví dụ, làm sao để ta thể hiện ý "với x này, tôi đoán t sẽ bằng như này, nhưng không chắc lắm, nhưng tôi tin t sẽ bằng như kia hơn, tức tôi chắc chắn hơn". Do đó, để thể hiện cái ý rằng, sự dự đoán của ta có yếu tố không chắc, thì ta sẽ dùng một probability distribution, gọi là predictive distribution f(t|𝐱).
>
>
>
> Thế thì f(t|𝐱), tất nhiên, đã học xác suất từ Casella hay Stat110, nó là conditional probability distribution, hay nếu nói theo kiểu prior/posterior, thì nó chính là posterior distribution của T.
>
>
>
> Rồi, mình còn nhớ bài toán polynomial curfitting, cũng có bối cảnh chung của bài toán linear regression cho các observed data (𝐱1, t1), ....(𝐱N, tN).
>
>
>
> Đầu tiên sẽ có ích khi ôn lại bài toán point estimation của Casella: Cho random sample 𝐗 = (X1,....Xn) iid \~ f(x|θ). Nhiệm vụ là muốn xây dựng một hàm của sample W(𝐗), sao cho tại observed value của 𝐗, ta có W(𝐱) estimate tốt cho θ. Sau đó, vì định nghĩa của point estimator quá mơ hồ (bất cứ hàm của sample nào cũng có thể là một point estiamator cho θ (nhưng có là estimator tốt hay không thì chưa biết) nên ta mới có vài phương pháp tiếp cận chính: Method of Moment, Maximum Likelihood, Bayes estimator.
>
>
>
> Thế thì tạm gác lại hai cái đầu, mình nói luôn sang Bayes estimator. Đã đụng tới chữ Bayes, dĩ nhiên là ta dùng quan điểm (perspective) của trường phái Bayesian - coi θ không phải là fixed nhưng unknown như trường phải classic (hay Frequentist), mà ta coi nó là random variable (vector). Để rồi, khi chưa có data gì, ta chọn cho nó distribution nào đó, dựa vào niềm tin ban đầu (prior knowledge), ví dụ như kinh nghiệm hay sao đó, gọi là prior distribution của θ, f(θ), hay trong sách Casella dùng π(θ). Sau đó, dựa vào Bayes theorem, ta sẽ xây dựng posterior distribution của θ, chính là f(θ|𝐱), hay π(θ|𝐱) = f(x|θ)π(θ)/f(𝐱).
>
>
>
> Và lúc này, với một distribution, thì nhiệm vụ vẫn là, cần đưa ra một point estimator, là một hàm của sample W(𝐗). Vậy thì point estimator là cái gì đây?
>
>
>
> Câu trả lời, là, ta sẽ cần viện tới decision theory, trong đó ta sẽ tính có các khái niệm như loss function, risk function. Vì thứ mà ta có là một distribution, vốn phản ánh tính không chắc chắn, nên cần dựa vào lí thuyết này để đưa ra quyết định tối ưu.
>
>
>
> Vậy thì, loss function, là hàm của một estimator, được định nghĩa phản ánh độ sai lệch, của estimator và giá trị param. Cái này nó giống định nghĩa của MSE, MSE cũng là một hàm của estimator, được định nghĩa bằng trung bình của W(𝐗) - θ:
>
>
>
> Bias(W(𝐗) = E\_θ\[(W - θ)²\], để rồi triển khai ra, ta sẽ có:
>
>
>
> = E\_θ\[W² - 2Wθ + θ²\]
>
>
>
> = E\_θ\[W²\] - 2θE\[W\] + θ²
>
>
>
> = E\_θ\[W²\] - 2θE\[W\] + θ²
>
>
>
> Dùng Var(W) = E\[W²\] - (EW)² ⇨ E\[W²\] = Var(W) + (EW)²
>
>
>
> ..= Var(W) + (EW)² - 2θE\[W\] + θ²
>
>
>
> = Var(W) + (EW - θ)²
>
>
>
> = Var(W) + \[Bias(W)\]²
>
>
>
>  Quay lại với hàm loss, L(W, θ), như đã nói, có thể có nhiều loại, một loại cụ thể là ta có thể có square error loss: L(W(𝐗), θ) = (W(𝐗) - θ)²
>
>
>
> lấy trung bình: E\_θ\[L(W, θ)\], đây chính là risk function. (có nghĩa là với loss là squared error loss thì MSE chính là risk function thôi)
>
>
>
> Lưu ý, W(𝐗) là statistic, tức cũng là random variable, thì L(W(𝐗), θ) cũng là random variable, nên dĩ nhiên ta có quyền lấy trung bình / expected value của nó, và vì bản chất đều là function của sample 𝐗 \~ f(𝐱|θ), nên distribution của L(W(𝐗), θ) sẽ phụ thuộc θ, nên ta mới ghi là E\_θ\[L(W(𝐗), θ)\], ám chỉ kì vọng này, sẽ là hàm phụ thuộc θ do distribution của của L(W(𝐗), θ) sẽ phụ thuộc θ.
>
>
>
> Và với risk function, hay loss function, nó không phân biệt classic hay Bayessian, vì việc ta lấy kì vọng, là đang kì vọng của random variable L(W(𝐗), θ). Và điềy này mang ý nghĩa bằng lời là, ta đã biết loss của W(𝐗) khi estimate cho θ, thì bây giờ ta tính trung bình trên mọi giá trị của 𝐗:
>
>
>
> R(θ, W(𝐗)) = E\[L(W(𝐗), θ)\] = ∫L(W(𝐱), θ)f(𝐱|θ)d𝐱
>
>
>
> Thế thì, nếu giờ ta quay lại với việc đang xét Bayesian approach, và có θ \~ prior distribution f(θ).
>
>
>
> Thì lúc này E\_θ\[L(W(𝐗), θ)\], hay R(θ, W(𝐗)) với tư cách là function của θ, cũng lại là random variable. Từ đó ta được quyền lấy kì vọng của nó: E\[R(θ, W(𝐗))\] và lần này, đây là kì vọng của một random variable có được bằng cách áp một hàm lên θ, vốn dĩ là một random variable có phân phối π(θ). Và đây chính là **Bayes risk**, nó sẽ không còn là một random variable nữa, mà là một fixed number, vì ta đã intergrate mọi possible value của θ rồi.
>
>
>
> Bayes risk = ∫\[risk function\] π(θ) dθ = ∫R(θ, W(𝐗)) π(θ) dθ
>
>
>
> Điều này cũng có thể hiểu theo cách khác, là ta có L(W(𝐗), θ) là function của random variable 𝐗 và θ. Và kì vọng của nó chính là ta tính trung bình của L, dựa trên **joint distribution** của 𝐗 và θ
>
>
>
> E\[L(W(𝐗), θ)\] = ∫∫ L(W(𝐗), θ) f(𝐱, θ) d𝐱 dθ
>
>
>
> = ∫∫L(W(𝐗), θ) f(𝐱|θ) π(θ) d𝐱 dθ
>
>
>
> = ∫ \[∫L(W(𝐗), θ) f(𝐱|θ) d𝐱\] π(θ) d𝐱 dθ
>
>
>
> ∫L(W(𝐱), θ)f(𝐱|θ)d𝐱 chính là risk function R(W(𝐗), θ)
>
>
>
> .. = ∫ \[R(W(𝐗), θ)\] π(θ) dθ → Bayes risk
>
>
>
> Do đó nếu biến đổi tí ta sẽ thấy nó cũng là:
>
>
>
> ∫∫ L(W(𝐗), θ) f(𝐱|θ) π(θ) d𝐱 dθ
>
>
>
> = ∫ \[∫L(W(𝐗), θ) f(θ|𝐱) dθ\] f(𝐱) d𝐱
>
>
>
> Thì ∫L(W(𝐗), θ) f(θ|𝐱) dθ chính là **posterior expected loss**
>
>
>
> để rồi ta sẽ nhìn nhận bayes risk như việc ta tính trung bình posterior expected loss over mọi possible value của 𝐗.
>
>
>
> Và quay lại mục tiêu đưa ra point estimator từ posterior distribution, thì mục tiêu sẽ là giảm thiểu Bayes risk: minimize\_θ ∫ \[∫L(W(𝐱), θ) f(θ|𝐱) dθ\] f(𝐱) d𝐱
>
>
>
> Và điều này (với vài lập luận) sẽ tương đương minimize ∫L(W(𝐱), θ) f(θ|𝐱) dθ, tức minimize posterior expect loss.
>
>
>
> Ta có bài toán: minimize (over W(𝐱)) ∫L(W(𝐱), θ) f(θ|𝐱) dθ
>
>
>
> Giả sử dùng squared error loss: ∫L(W(𝐱), θ) f(θ|𝐱) dθ = ∫\[W(𝐱) - θ\]² f(θ|𝐱) dθ,
>
> dễ thấy, đây chính là E\[(W(𝐱) - θ)²\] với θ \~ f(θ|𝐱).
>
>
>
> Và bài toán lúc này tương đương: tìm a để E\[(X - a)²\] nhỏ nhất. Ta có E\[(X - a)²\] = E\[X² - 2aEX + a²\] = E\[X²\] - E\[2aEX\] + E\[a²\] = E\[X²\] - 2a(EX) + a². Để cái này nhỏ nhất, thì -2a EX + a² nhỏ nhất. Đây là hàm bậc hai của a. Đạo hàm: 2a - 2EX. Cho đạo hàm bằng 0, ta có a = EX, chính là minimizer.
>
>
>
> Áp dụng vào bài toán tìm W để E\[(W(𝐱) - θ)²\] nhỏ nhất với θ \~ f(θ|𝐱), thì solution là W(𝐗) = E\[θ\] với θ \~ f(θ|𝐱), thì cũng có thể ghi là W(𝐗) = E\[θ|𝐗\], tức posterior mean, và đây chính là Bayes estimator minimize Bayes risk với squared error loss 
>
>
>
> Vậy thì nãy giờ là nói về bài toán inference: suy luận θ từ data.
>
>
>
> Với bài toán prediction, ta không quan tâm θ, mà ta quan tâm đến việc dự đoán T, nên đại ý là ta sẽ xây dựng predictive distribution f(t|θ,𝐱)
>
>
>
> Và để ra quyết định tối ưu, hoàn toàn tương tự, ta cũng giải bài toán minimize expected loss, và kết quả nếu loss là squared error, sẽ là E\[t|𝐱\]

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Điểm mạnh: Bạn đã tóm tắt nội dung văn bản một cách cực kỳ chính xác và đi sâu vào giải thích các khái niệm phức tạp như kỳ vọng có điều kiện và hàm lỗi bình phương bằng cách liên hệ chặt chẽ với lý thuyết thống kê Bayesian. Điều này thể hiện sự hiểu biết sâu rộng, mặc dù một chi tiết nhỏ về ký hiệu f(t|θ,x) ở cuối có thể được làm rõ thêm.

**🔗 See also:** [Optimal Prediction with Gaussian Noise](./311_maximum_likelihood_and_least_squares.md#node-wsglxqn)

<br>

<a id="node-c0z2r6r"></a>

### Linear Basis Function Models

<p align="center"><kbd><img src="assets/wyve7do5ve.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là đầu tiên gs nói về một mô hình đơn giản nhất của bài toán regression: có dạng y(𝐱, 𝐰) = w0 + w1x1 + ...wDxD, là linear combinaton các input. (chỗ này, mình tự hiểu, cái cụm Σi wixi thì đúng là linear combination các xi, nhưng vì có thêm w0, nên đây là affine function, không hoàn toàn chính xác là linear function, điểm này trong nhiều lớp như CS224, CS231 cũng có nói tới)
>
>
>
> Với mô hình này, người ta gọi là linear regression, với đặc điểm dễ thấy là, nó là hàm tuyến tính (affine) của cả tham số 𝐰 = (w0, w1,...wD) và input 𝐱 = (x1, ....xD). Và gs cho rằng nó có những hạn chế nghiêm trọng.
>
>
>
> Thành ra, người ta sẽ mở rộng mô hình này, bằng cách thay vì dùng linear combination các input xi, ta sẽ dùng basis function Φi(𝐱) để tạo các non-linear function của 𝐱, và sau đó mới tổ hợp tuyến tính chúng với hệ số wi:
>
>
>
> y(𝐱, 𝐰) = w0 + w1 Φ1(𝐱) + ...+ wM-1 ΦM-1(𝐱) = w0 + Σj=1:M-1 wj Φj(𝐱).
>
>
>
> Như vậy, số tham số là M.
>
>
>
> Nói chung, điểm mấu chốt là, thay vì dùng 𝐱 = x1,...xD như input, và linear combination chúng lại, thì ta chế biến các x1,...xD thành một bộ input khác Φ1(x1,..xD), Φ2(x1,...xD),...là các hàm phi tuyến đối với 𝐱, khi đó tuy vẫn tổ hợp tuyến tính chúng lại với w0,w1,...: w0 + w1Φ1(𝐱) + w2Φ2(𝐱) + ...nhưng lúc này, đối với 𝐱, ta có hàm phi tuyếm, nhưng đối với 𝐰 vẫn là hàm tuyến tính. Và mô hình này sẽ mạnh hơn.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bạn đã nắm vững các khái niệm trọng tâm rất tốt, đặc biệt là sự phân biệt chính xác giữa hàm tuyến tính và hàm affine, điều này thể hiện sự hiểu biết sâu sắc. Cách bạn tóm tắt lại điểm mấu chốt của Basis Function Models cũng rất rõ ràng và đầy đủ.

<br>

<a id="node-6p1u6u8"></a>

#### Bias Parameter and Basis Function

<p align="center"><kbd><img src="assets/paqenetxj5.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, gs nói về w0, đại khái là vai trò của nó giúp ta có thể gán một mức offset cố định nào đó cho data, và thỉnh thoảng người ta gọi là bias parameter.
>
>
>
> Ông lưu ý ta đừng confuse với bias trong thống kê. Ý này có thể hiểu, như note vừa nãy, mình cũng đã nhắc đến khái niệm bias trong statsitic: Cụ thể là trong bài toán point estimator, bias của estimator W(𝐗) là hàm số của W(𝐗), định nghĩa bởi: Bias(W(𝐗)) = E\_θ\[W(𝐗)\] - θ, và nếu E\_θ\[W(𝐗)\] = θ, hay Bias(W(𝐗)) = 0, ta gọi W(𝐗) là unbiased estimator của θ.
>
>
>
> Rồi, ý sau cũng ko khó hiểu, y(𝐱, 𝐰) = w0 + Σj=1:M-1 wj × Φj(𝐱), thì sẽ thuận tiện hơn nếu ta đặt Φ0(𝐱) = 1, để w0 + Σj=1:M-1 wj × Φj(𝐱) = w0 × Φ0(𝐱) + Σj=1:M-1 wj × Φj(𝐱) = Σj=0:M-1 wj × Φj(𝐱), và dễ thấy, nếu đặt 𝐰 = \[w0, ....wM-1\]ᵀ và **Φ** = (Φ0(𝐱), ...ΦM-1(𝐱)), thì cái cụm trên chính là dot product của chúng 𝐰ᵀ**Φ**(𝐱)
>
>
>
> Ông nói đại ý rằng trong nhiều bài toán pattern reconition thực tế, thì ta thường có bước feature engineering hay pre-processing (như đã biết, đại khái là ta tiền xử lí data, hoặc chế cháo tạo các feature mới từ các feature gốc) thì khi đó, chúng có thể được thể hiện thông qua các basis function này. (nói đơn giản, là ta có thể hiểu hàm Φ sẽ đại diện cho các bước preprocessing hay feature engineering này trong thực tế)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Ghi chú rất chính xác và chi tiết, đặc biệt là phần giải thích về vai trò của φ₀(x) và sự khác biệt giữa "bias" trong mô hình và "bias" trong thống kê. Cách bạn liên hệ hàm cơ sở với feature engineering thực tế cũng rất rõ ràng.

**🔗 See also:** [Likelihood and Error Functions](./311_maximum_likelihood_and_least_squares.md#node-urnjdcs) · [Section 3.3.3 Equivalent Kernel](./333_equivalent_kernel.md#node-qgf9klh)

<br>

<a id="node-2e9r7fm"></a>

##### Gaussian Basis Functions

<p align="center"><kbd><img src="assets/12ucbwibcnm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là như đã nói, nhờ có basis function mà ta có thể có mô hình phi tuyến đối với input. Tuy nhiên, vẫn là hàm tuyến tính đối với tham số (𝐰) và đặc điểm này mang lại các lợi ích khi giải thích (kết quả) mô hình nhưng vẫn đi kèm vài nhược điểm - như nó hạn chế sức mạnh của mô hình.
>
>
>
> Sau đó, ông đề cập đến trong ví dụ polinomial curve fitting, thì ta còn nhớ dùng function y(𝐰,x) là hàm đa thức bậc M: w0 + w1x^1 + w2x² + ...wMx^M (xem link), thì dễ hiểu ở đây, basis function là Φj(x) = x^j. Cách làm này, có nhược điểm liên quan tới việc hàm φ là global function của input, để rồi có thể khắc phục bằng cách dùng spline funciton. Thì ý này đại khái là, ví dụ xét hàm y(x, w) = w × x³ đi, và muốn ép nó khớp với một nhóm data (xi, ti) thì có khi ta điều chỉnh w khiến w × φ(xi) khớp được vài điểm đầu, thì lại khiến nó rời xa nhóm khác, mà bắt nguồn là do cái hàm x³ nó là **hàm toàn cục, khi x trải dài từ -∞ đến ∞ thì f(x) ở đâu cũng là x³**, nên nếu thay đổi (điều chỉnh để cái hàm wx³) ở một vùng thì nó sẽ **thay đổi luôn những vùng khác**. Còn giả sử ta xét hàm Gaussian dưới đây, ta sẽ thấy, cái hàm này, nó chỉ có tính cục bộ, cụ thể là **nó chỉ tác động với các điểm quanh μ**, trong phạm vi nào đó (do s), như vậy, **giả sử ta điều chỉnh tham số w gắn với Φ(x) giúp nó khớp những điểm ở vùng cục bộ này, thì nó không ảnh hưởng với các vùng khác**. 
>
>
>
> Rồi, nói về Gaussian basis Φj(x) = exp{-(x-μj)²/2s²} với μj sẽ chi phối location của basis function trong input space và s chi phối spatial scale (cũng chưa hiểu lắm).
>
>
>
> Ông lưu ý, đại khái là cái này đừng coi nó hay đòi hỏi nó phải là một valid pdf, hay cũng đừng cho rằng nó có ý nghĩa xác suất gì, cái này có thể hiểu cũng giống như với Gaussian kernel, ta chỉ muốn hàm kernel có cái hành vi như đường cong cái chuông của phân phối Normal pdf mà thôi, chứ chả có hàm ý xác suất gì cả. Nên ở đây cũng vậy, ta sẽ ko đòi hỏi Φj(x) phải có các tính chất valid của một hàm pdf (như intergrate = 1). Hơn nữa, kiểu gì thì ta cũng sẽ nhân với hệ số wj.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú của bạn rất chính xác và sâu sắc. Đặc biệt, cách bạn giải thích sự khác biệt giữa hàm cơ sở toàn cục và cục bộ bằng ví dụ minh họa và phép so sánh với Gaussian kernel thể hiện sự hiểu biết sâu rộng. Một chút rõ ràng hơn về vai trò của 's' trong 'spatial scale' sẽ làm cho ghi chú trở nên hoàn hảo.

**🔗 See also:** [Khớp đường cong hàm đa thức](./11_example_polynomial_curve_fitting.md#node-79h9mtc)

<br>

<a id="node-lkqg58h"></a>

###### Sigmoidal and Tanh Functions

<p align="center"><kbd><img src="assets/70liydxof18.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/aufxlvui5mt.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, một hàm basis quan trọng nữa, là sigmoidal basis function:
>
>
>
> Φj(x) = σ\[(x - μj)/s\] với σ(a) = 1/\[1 + exp(-a)\].
>
>
>
> và một phiên bản equivalent (tương đương) là hàm tanh, có quan hệ với sigmoid: tanh(a) = 2 σ(a) - 1, có nghĩa là, có quan hệ tuyến tính giữa chúng, nên dễ hiểu khi gs nói rằng nhìn chung, một tổ hợp tuyến tính của các logistic sigmoid thì cũng là một tổ hợp tuyến tính các tanh (ví dụ, α σ1(a) + β σ2(a), là tổ hợp tuyến tính của các σ, thì thay tanh1(a) = 2 σ1(a) - 1 ⇨ σ1(a) = \[tanh1(a) + 1\]/2, và σ2(a) = \[tanh2(a) + 1\]/2 thì ta cũng sẽ có α \[tanh1(a) + 1\]/2 + β \[tanh2(a) + 1\]/2 = α tanh1(a) / 2 + α/2 + β tanh2(a)/2 + β/2, đây cũng là linear combination các tanh function (chính xác hơn là affine, nhưng như đã nói, ta coi như là linear combination luôn)
>
>
>
> Nói thêm chút về hàm sigmoid và tanh, mình đã gặp chúng trong các lớp machine learning của Andrew Ng, cũng như sau này với các lớp deep learning. Bây giờ gặp lại trong bối cảnh Bishop, thì mình được hiểu thêm chúng là thuộc loại basis function, là function nhằm tạo ra tính chất "non-linearity đối với input", mà nhờ đó, ta vẫn có linear model - là hàm tuyến tính đối với tham số, nhưng là hàm phi tuyến đối với input → giúp mạnh hơn.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Bạn đã ghi chú rất chính xác các định nghĩa và mối quan hệ giữa hàm sigmoid và tanh. Phần ví dụ minh họa chi tiết về tổ hợp tuyến tính cho thấy sự hiểu biết sâu sắc và khả năng áp dụng kiến thức của bạn.

<br>

<a id="node-4gh1zj2"></a>

###### Fourier Basis and Wavelets

<p align="center"><kbd><img src="assets/rwynkz58c0j.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/llzypauq3r.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn đầu nói sơ về một loại basis function gọi là Fourier basis, có thể tìm hiểu nó sau, chỉ cần biết đại ý là nó sẽ phù hợp với input có cấu trúc dạng chuỗi ví dụ như các điểm thời gian nối tiếp nhau hoặc các pixel trên bức ảnh.
>
>
>
> Cuối cùng, gs cho rằng, phần lớn các thảo luận trong chap này không care / phụ thuộc basis fuction cụ thể là gì. Nói cách, Φ là gì cũng được, kể cả là hàm identity Φ(𝐱) = 𝐱 Và để đơn giản, ta sẽ chỉ tập trung vào bài toán mà t là scalar, tức là target variable chỉ là scalar variable chứ ko phải vector.

<br>

