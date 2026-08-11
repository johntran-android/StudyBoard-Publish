# 3.4 Bayesian Model Comparison

📊 **Progress:** `4` Notes | `4` Screenshots | `4` AI Reviews

---
<a id="node-8mjaf9g"></a>

## 3.4 Bayesian Model Comparison

<br>

<a id="node-4d86aho"></a>

## Section 3.4 Bayesian Model Comparison

<p align="center"><kbd><img src="assets/0ze59meze2vk.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là trong chapter 1 mình đã biết về overfit, cũng như việc sử dụng cross-validation technique để chọn giá trị của regularization parameters, mang ý nghĩa là, ta sẽ chọn ra giá trị quy định mức độ phức tạp của mô hình một cách phù hợp.
>
>
>
> Thì phần này, ta sẽ tiếp cận lại vấn đề này theo trường phái Bayesian.
>
>
>
> Tiếp theo ông nói sơ vài ưu điểm của trường phái Bayesian trong việc tiếp cận vấn đề overfit và model selection: Cụ thể với overfit, ta sẽ thấy, thay vì dùng ước lượng điểm (như MLE) để lắp vào hàm dự đoán, sẽ gây overfit, ta có thể làm cách khác, đó là marginalizing over mọi giá trị khả dĩ của tham số mô hình, và từ đó có một hàm prediction map trực tiếp giữa input và target, không phụ thuộc tham số mô hình nữa, cách làm này sẽ giảm overfit.
>
>
>
> Và các ưu điểm khác như cho phép so sánh giữa mô hình với nhau một cách trực tiếp dựa trên training data, không cần thông qua validation data, từ đó giúp giảm lãng phí data và giảm chi phí tính toán khi phải giải bài toán tìm regularization parameter tối ưu (dựa trên cross validation).
>
>
>
> Và một tính chất chưa hiểu lắm nhưng ta sẽ đào sâu ở chapter 7 - Relevance vector machine.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chú cực kỳ chi tiết, nắm bắt chính xác các ý cốt lõi như tránh over-fitting bằng cách marginalizing và lợi ích của việc không cần tập validation. Bạn chỉ cần lưu ý thêm ý về khả năng tự động xác định đồng thời nhiều tham số phức tạp (complexity parameters) trong quá trình huấn luyện.

<br>

<a id="node-mg5ehv8"></a>

### Bayesian Model Comparison

<p align="center"><kbd><img src="assets/tglphu0ktj.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đoạn này nói về đại ý của cách tiếp cận Bayesian đối với bài toán model comparision (hay selection, cũng như nhau)
>
>
>
> Có lẽ nên dừng lại tí nói về vì sao lại gọi là model comparision (so sánh model) hay selection (chọn model), và vì sao lại thường đi kèm với việc nói về overfit: Đầu tiên, nó thường đi kèm với overfit và cả underfit là vì đương nhiên là ta không muốn một mô hình bị overfit hay underfit. Nhưng trước hết, model, mô hình là cái quái gì cái đã. Mình hiểu, mô hình là một mô hình mô phỏng thực tế, là cái ta dựng lên, và tìm cách làm sao cho nó giống với thực tế nhất. Về mặt từ ngữ, thì ý nghĩa của từ mô hình là vậy. Ví dụ, ta mô hình hóa / dựng mô hình một toà nhà, thì dĩ nhiên ta tìm cách dựng nên một mô hình giống với tòa nhà nhất có thể. Thế thì ở đây, cái ta muốn, là dựng nên một mô hình mô phỏng sát nhất với cái quy luật chi phối dữ liệu ở ngoài đời thực mà dữ liệu ta quan sát thấy được sinh ra từ đó.
>
>
>
> Ví dụ, ta quan sát được một chuỗi số X1,.....Xn. Và ta muốn dựng mô hình cái quy luật sinh ra bộ giá trị này, thì cái quy luật này, chính là phân phối xác suất (population distribution), và nó chỉ là một cái hàm số, quy định rằng với giá trị nào đó, thì xác suất sinh ra data có giá trị đó nên cao hay thấp. Vậy ta dựng mô hình bằng cách nào. Có hai cách, một là mô hình có tham số (parametric model), trong đó ta dùng một hàm số, có quy luật bị chi phối bởi tham số: f(x|θ) và ta sẽ đi tìm cái tham số cũng như dạng của hàm f này và hai là, mô hình phi tham số (non-parametric model). 
>
>
>
> Vậy thì, bài toán đi tìm cái hàm f chi phối quy luật của data thật sự là rất phức tạp, vì ta không biết phải làm gì, hay dạng của f thật sự là gì cả. Do đó, ta mới tiếp cận theo lối: chấp nhận rủi ro, thông qua việc đặt ra vài giả định, nhằm đơn giản bớt bài toán. Ví dụ, ta giả định phân phối f là một phân phối có dạng nào đó, ví dụ normal(μ, σ^2), và từ đó dùng các cách tiếp cận như MLE, Bayes, ta đi tìm cách estimator ra μ, σ^2. Đây chính là bài toán inference - point estimation cho population parameter. Như vậy, đã giả định thì có thể sai, có thể phân phối gốc hoàn toàn không phải là normal, thì cái estimator của ta tìm ra dù có tốt mấy cũng thành sai. Từ đó mới đẻ ra các tiêu chí như Roburstness mà mình đang học ở Chapter 10 - Casella, đó là: dưới sự thật rằng giả định ban đầu bị sai thì estimator còn tốt không?
>
>
>
> Quay lại bối cảnh machine learning với bài toán regression, giả sử quan sát được bộ dữ liệu (**x**1, t1), ....(**x**n, tn), mục đích tối thượng cũng là, ta muốn mô phỏng cái quy luật giúp map **x** với t. Vậy thì để mô phỏng, ta cũng có thể dùng parametric model, đi tìm một hàm số y(**x**,**w**) với dạng và giá trị **w** sao cho hàm này phản ánh, mô phỏng sát nhất với quy luật thực tế giữa **x** và t. Hoặc cũng có thể dùng non-parametric model.
>
>
>
> Vậy thì giả sử chọn parametric model, ta cũng sẽ thấy bài toán đặt ra quá phức tạp, vì đâu có biết cái quy luật thực tế của **x** và t nó có hình thù ra sao. Do đó, ta cũng đơn giản hóa bài toán, bằng cách đặt ra các giả định. Ví dụ, ta cho rằng quy luật này là một hàm tuyến tính đối với **w**, và phi tuyến đối với **x**, để rồi theo các cách tiếp cận đã biết, ta đi tìm ra **w**.
>
>
>
> Tới đây ta đã hiểu model là cái gì - nó chỉ là mô hình ta muốn xây dựng để mô phỏng thực tế. Với bài toán population paramter inference, thì mô hình là cái hàm f(**x**|θ) mà ta muốn tìm dạng của nó và giá trị parameter θ. Với bài toán regression, mô hình là cái hàm y(**w**,**x**) mà ta muốn tìm **w**, cũng như dạng của nó và giá trị w của nó. Và trong cả hai, thường thì ta đặt ra giả định về dạng của nó (giả định f là normal, hay y là hàm tuyến tính của w) để giúp đơn giản hóa bớt, chỉ còn phải đi tìm tham số của nó (μ, σ^2, hay **w**) thôi.
>
>
>
> Vậy sao phải so sánh model với nhau. À thì là vì, ví dụ như trong bài toán regression, nếu data ít, và ta giả định dùng mô hình (hàm y(**w**,**x**) có độ phức tạp cao (ví dụ dùng nhiều hàm basis - cũng là nhiều tham số) thì kết quả prediction sẽ tệ (không generalize tốt) 
>
>
>
> Nhưng nếu gỉam số tham số, và basis function, thì kết quả lại có thể khiến mô hình bị underfit, không đủ độ phức tạp
>
>
>
> Khi đó, bằng kĩ thuật regularization, ta vẫn dùng mô hình có độ phức tạp cao, nhưng đi tối ưu một tham số (regularization) để chọn ra giá trị (giúp kiểm soát) mức độ phức tạp của mô hình phù hợp.
>
>
>
> Và việc ta chọn, đi tìm giá trị tối ưu của regularization parameter này chính là model selection / comparision (bởi lẽ đó chính là ta đang so sánh các mô hình với mức complexity khác nhau để mà chọn ra cái tốt nhất).
>
>
>
> ---
>
>
>
> Rồi, quay lại bài. ý tưởng của Bayesian trong bài toán model comparision rất đơn giản: Là ta cũng **thể hiện sự không chắc chắn nên dùng model nào thông qua việc coi nó như biến ngẫu nhiên**.
>
>
>
> Giả sử ta phải so sánh L model: {ℳ1, ...ℳL}
>
>
>
> Trước khi nói tiếp, gs Bishop nhấn mạnh một ý cực quan trọng: Model ở đây phải hiểu, là **cái phân phối xác suất chi phối giá trị của data mà ta đang dùng để mô phỏng quan hệ thật / phân phối thật của chúng**. Ví dụ như trong bài toán polynomial curve fitting ta làm bữa giờ, thì đó là distribution của **t**|**X**. (**X** là matrix observed data **x**1,...**x**N, tức coi **X** fixed, đã biết). Hay với model dạng khác, thì nó là joint distribution của **X**, và **t** (coi **X** như random variable luôn).
>
>
>
> Cái này y như cách tiếp cận Bayesian cho bài toán point estimator của tham số mô hình **w** vậy. Đó là, ta coi nó như random variable. Rồi chọn priori f(**w**), và dùng Bayes rule để có posterior distribution f(**w**|𝒟) ∝ f(𝒟|**w**) f(**w**). Có nghĩa là, nguyên lý chung của Bayesian, là cái gì mà ta ko chắc chắn thì cứ coi nó là biến ngẫu nhiên, rồi đi xây dựng posterior distribution cho nó, từ đó, dựa vào decision theory để mà ra quyết định.
>
>
>
> Và như vậy , thì ta sẽ **coi như ta có một random variable ℳ** (có các possible value là ℳ,...ℳL). Rồi cũng chọn prior distribution của nó f(ℳ), và dùng Bayes rule để xây dựng posterior distribution:
>
>
>
> f(ℳ|𝒟) = f(𝒟|**ℳ**) f(ℳ) / f(𝒟)

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **95/100**
>
> Ghi chép rất sâu sắc khi liên hệ được nền tảng thống kê cổ điển với bài toán so sánh mô hình theo quan điểm Bayesian một cách chính xác. Tuy nhiên, phần dẫn nhập có thể cô đọng hơn để người đọc nhanh chóng nắm bắt cơ chế cốt lõi của công thức Bayes áp dụng cho tập hợp mô hình.

<br>

<a id="node-5ef8t75"></a>

#### Model Evidence and Bayes Factor

<p align="center"><kbd><img src="assets/k9q5rh88uuj.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì f(ℳ) là cách để ta đưa vào PRERENCE / PRIOR BELIEF về mô hình- ý là, cũng là việc ví dụ như ta ưu ái những mô hình này hơn mô hình kia (thông qua việc đưa nó vào danh sách, và thông qua việc gán giá trị xác suất lớn nhỏ cho nó). 
>
>
>
> Và ở đây ta sẽ giả định các ℳ\_i đều có xác suất như nhau.
>
>
>
> Còn f(𝒟|**ℳ**\_i), được gọi là model evidence, thể hiện preference show bởi data cho các model khác nhau. Và có khi người ta gọi là **marginal likelihood** vì nó có thể được nhìn nhận theo kiểu là likelihood function over space of models, trong đó paramter được marginalized out.
>
>
>
> Đoạn này nghĩa là sao?
>
>
>
> Mình nghĩ để dễ hiểu cứ thử liên hệ nó với θ (là tham số mô hình, mà trong chương này ví dụ nó là **w**)
>
>
>
> posterior distribution của θ: π(θ|**x**) ∝ f(**x**|θ) π(θ) = L(θ|**x**) π(θ)
>
>
>
> thì π(θ) mang ý nghĩa là phản ánh niềm tin ban đầu của mình (experimenter) về giá trị của θ. Ví dụ như mình tin θ là biến rời rạc có các possible value θ1,..θL, nhưng ko favor thằng nào, khi đó ta cho priori là discrete uniform distribution.
>
>
>
> còn f(**x**|θ) = L(θ|**x**), như đã biết, thể hiện độ hợp lí của θ khi quan sát được giá trị của data.
>
>
>
> Vậy tương tự thôi
>
>
>
> posterior distribution của ℳ: f(ℳ|𝒟) ∝ f(𝒟|ℳ)f(**ℳ**)
>
>
>
> thì f(ℳ) mang ý nghĩa phản ánh niềm tin ban đầu của ta (preference của ta) về các giá trị mô hình khác nhau. Và ở đây ta tin biến ngẫu nhiên ℳ có L possible value ℳ1,...ℳL, nhưng ta cũng không chắc, không favor thằng nào nên cho chúng có xác suất như nhau
>
>
>
> còn f(𝒟|**ℳ**), tương tự như f(**x**|θ) = L(θ|**x**), ta cũng có thể gọi nó là L(ℳ|𝒟), marginal likelihood function mang ý nghĩa, độ hợp lí của model ℳ khi giá trị dữ liệu quan sát được là 𝒟.
>
>
>
> Còn sở dĩ gọi là marginal likelihood vì ý là, model ℳ thì nếu xét kĩ ra thì sẽ có phụ thuộc các giá trị của parameter nữa, nhưng ta marginalizing - tức lấy trung bình mọi giá trị khả dĩ của parameter, để không còn phụ thuộc parameter nữa.
>
>
>
> Và cuối cùng, tỉ lệ của hai model evidence f(𝒟|**ℳ**i)/f(𝒟|**ℳ**j) gọi là Bayes factor.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú của bạn rất xuất sắc, thể hiện sự hiểu sâu sắc khi tự liên hệ phép tương tự giữa cấp độ tham số và cấp độ mô hình để giải thích marginal likelihood. Để hoàn thiện hơn, bạn có thể viết rõ công thức toán học thể hiện việc tích phân loại bỏ (marginalize out) tham số w.

<br>

<a id="node-n24grkd"></a>

##### Predictive Distribution as Mixture

<p align="center"><kbd><img src="assets/kwccpvuo3k.png" width="80%"></kbd></p>

> [!NOTE]
> Và khi đã derive được posterior distribution f(ℳ|𝒟), ta sẽ xây dựng predictive distribution
>
>
>
> f(t|**x**, 𝒟) = Σi=1:L f(t|**x**, ℳi, 𝒟) f(ℳi|𝒟)
>
>
>
> Giải thích công thức này: Rất đơn giản, giống như ta có fX,Y(x,y) với X,Y là discrete random variable, thì bằng cách marginalizing joint pdf của X,Y over mọi possible value y1,...yK của Y ta sẽ có marginal distribution của X: fX(x) = Σi=1,2..K fX,Y(X,yi). Và f(X, yi) = f(X|yi)fY(yi). Nên:
>
>
>
>  fX(x) = Σi=1,2..K f(X|yi)fY(yi)
>
>
>
> với việc ta coi ℳ là random variable có các possible value ℳ1,...ℳL thì thì joint distribution của T|**x** và ℳ là f(t, ℳ|**x**, **𝒟**). Marginalizing joint pdf của T|**x** và ℳ, ta sẽ có pdf của T|**x**:
>
>
>
> f(t|**x**, 𝒟) = Σi=1:L f(t|**x**, ℳi, 𝒟) f(ℳi|𝒟)
>
>
>
> hoặc cũng có thể hiểu như sau:
>
>
>
> Trước đây predictive distribution f(t|**x**, 𝒟) thật ra là đang dựa trên một model cụ thể (ví dụ như mô hình linear với regularization factor là bao nhiêu đó), kí hiệu nó là **ℳ**, nên ta có thể ghi là f(t|**x**, ℳ, 𝒟) với ℳ chỉ là fix value, chỉ một mô hình cụ thể. Và với ℳ, 𝒟, **x** đều fix, thì f(t|**x**, ℳ, 𝒟) là một fixed value.
>
>
>
> Nhưng nay, với cách tiếp cận Bayesian, ta coi ℳ là random variable, và posterior distribution là f(ℳ|𝒟). Thì lúc này f(t|**x**, ℳ, 𝒟) không còn là fixed value nữa, nó là hàm của random variable ℳ nên bây giờ nó trở thành random variable luôn (nhớ thần chú thầy Joe mập trong Stat110: hàm của random variable là random variable). Và vì là random variable ta có thể lấy kì vọng:
>
>
>
> E\[f(t|**x**, ℳ, 𝒟)\] với chú thích đây là E\[g(ℳ)\] với g(ℳ) = f(t|**x**, ℳ, 𝒟) và **ℳ** \~ f(ℳ|𝒟)
>
>
>
> Dùng LOTUS (ôn nhanh, cho discrete X \~ f(x) có các possible value x1,...xN, thì với Y = g(X), LOTUS cho phép tính E\[Y\] = E\[g(X)\] = Σi=1:N g(xi)f(xi).
>
>
>
> Vậy ở đây, E\[g(ℳ)\] = Σi=1:L g(ℳi)f(ℳi|𝒟) 
>
>
>
> thế hàm g(ℳ) = f(t|**x**, ℳ, 𝒟) vô lại ta sẽ có:
>
>
>
> E\[f(t|**x**, ℳ, 𝒟)\] = Σi=1:L f(t|**x**, ℳi, 𝒟) f(ℳi|𝒟)
>
>
>
> Như vậy, góc nhìn này giúp ta thấy rõ hơn bản chất chỉ là ta đang lấy average (của f(t|**x**, ℳ, 𝒟) trên mọi possible value của ℳ (bản chất của kì vọng / expected value chỉ là lấy trung bình thôi có trọng số thôi)
>
>
>
> Và nhờ đó ta cũng hiểu câu dưới khi gs Bishop nói cái này là một ví dụ của MIXTURE DISTRIBUTION, trong đó ta averaging các predictive distribution f(t|**x**, ℳi, 𝒟) với trọng số (weight) là posterior distribution f(ℳi|𝒟).
>
>
>
> ---
>
>
>
> Ông cho biết thêm, lấy ví dụ, nếu ta có hai model ℳ1, ℳ2, có posterior equally likely (ý là xác suất bằng nhau). Và trong đó một cái cho ra predictive distribution f(t|**x**, ℳ1, 𝒟) có dạng tập trung quanh mốc t = a. Còn cái kia cho f(t|**x**, ℳ2, 𝒟) có dạng tập trung quanh mốc t = b. Thì cái overal predictive distribution sẽ là BI-MODAL (!) model - tức là một mô hình có 2 đỉnh tại a, b thay vì chỉ có một đỉnh tại (a+b)/2
>
>
>
> (!) Chú ý, ko phải binomial đâu nhé, đừng có bị nhầm.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú rất xuất sắc khi giải thích công thức dưới hai góc nhìn (marginalization và LOTUS) vô cùng trực quan và hiểu đúng bản chất bimodal. Để hoàn thiện hơn, bạn nên bổ sung giải thích tại sao điều kiện x biến mất ở f(ℳ_i|ᆒ) (do sự độc lập giữa mô hình và dữ liệu kiểm thử mới).

<br>

<a id="node-tmo40n6"></a>

