# 4.2.4 Exponential family

📊 **Progress:** `1` Notes | `2` Screenshots | `1` AI Reviews

---
<a id="node-1lbje7e"></a>

<br>

<a id="node-75dk469"></a>

## Section 4.2.4 Exponential Family

<p align="center"><kbd><img src="assets/ntdqzgx01r.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/343mwzikg4l.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên active recall chút: Bối cảnh bữa giờ ta ta muốn đi xây dựng mô hình xác suất class posterior f(𝒞|𝐱) thông qua cách làm là xây dựng joint distribution (gọi là generative distribution) f(𝐱, 𝒞). Để sau đó ta sẽ có f(𝒞k|𝐱) = f(𝐱, 𝒞k)/f(𝐱) = f(𝐱, 𝒞k)/Σj f(𝐱|𝒞j)f(𝒞j)
>
>
>
> Mà để xây dựng f(𝐱, 𝒞k) ta lại dùng conditional probability theorem để có f(𝐱|𝒞k)f(𝒞k).
>
>
>
> Từ đó, ta giả định dạng của f(𝐱|𝒞k) là Normal với 𝛍1, 𝛍2 khác nhau (K=2), share chung 𝚺, cũng như gọi π là tham số của f(𝒞) (K = 2 thì 𝒞 \~ Bern(π)) thì f(𝐱, 𝒞) sẽ phụ thuộc các tham số 𝛍1, 𝛍2, 𝚺, π. Để rồi từ đó ta mới đi giải bài toán point estimation với cách tiếp cận điển hình là MLE.
>
>
>
> Dĩ nhiên là sau khi có joint distribution, mục đích cuối cùng vẫn là tính f(𝒞k|𝐱), sẽ bằng f(𝐱, 𝒞k)/Σj f(𝐱|𝒞j)f(𝒞j) và dùng nó để ra quyết định gán loại nào cho 𝐱.
>
>
>
> Và đó là khi ta đang xét 𝐱 là feature mang giá trị liên tục.
>
>
>
> Sau đó, ta mới xét 𝐱 là feature mang giá trị rời rạc, ở phần trước, thì lúc này mô hình joint distrubution f(𝐱, 𝒞) sẽ có số lượng tham số tăng theo lũy thừa, nên cần đặt ra vài giả định (naive Bayes), và nói chung là cũng giúp ta có một dạng cụ thể của joint distribution, từ đó cũng dẫn đến bài toán point estimation cho các tham số.
>
>
>
> Vậy thì nay, quay lại xét việc 𝐱 là feature liên tục. Thì như hồi học Casella đã biết, Normal distribution vẫn chỉ là thành viên của một họ phân phối lớn hơn, gọi là exponential family (bao gồm cả exponential, poison, beta, normal,....)
>
>
>
> Vậy thì, ở phần này, đại ý là thay vì giả định (dạng của f(𝐱|𝒞k) là 𝒩(𝛍k, 𝚺k)) ta sẽ dùng phân phối khái quát và bao trùm hơn này (mà mục đích cũng chỉ là: để mà có cái gọi là parametric modal, có cái dạng của distribution, từ đó mới đi point estimate tham số của distribution. Chứ nếu không giả định, ta sẽ biết estimate cái gì bây giờ khi đó phải làm theo cái gọi là non-parametric model)
>
>
>
> Thế thì, với chapter 2 cũng đã được gs Bishop nói về công thức của exponential family: f(𝐱|𝛈) = h(𝐱)g(𝛈)exp{𝛈ᵀ𝐮(𝐱)}.
>
>
>
> Thì ở đây, ta sẽ đại ý là ta sẽ chọn 𝐮(𝐱) = 𝐱. Để từ đó, coi như ta tự giới hạn lại bớt (để cho model đơn giản bớt, bớt tham số lại, giống như ta giả định naive Bayes ở phần trước vậy), và dùng 𝛌 thay vì 𝛈 (chỉ là kí hiệu)
>
>
>
> ta có class-conditional density f(𝐱|𝒞k) = h(𝐱)g(𝛌)exp{𝛌ᵀ𝐱}.
>
>
>
> (Nó chỉ y chang như khi ta giả định class-conditional density f(𝐱|𝒞k) là Normal để rồi f(𝐱|𝒞k) = 𝒩(𝐱|𝛍k, 𝚺k) thôi, chẳng qua là ở đây ta dùng một giả định rộng hơn, mô hình sẽ flexible hơn vì bây giờ tham số sẽ gồm có 𝛌k, và dạng của hàm h và g nữa thay vì chỉ có 𝛍k, 𝚺k với dạng cụ thể là pdf của normal)
>
>
>
> Bên cạnh đó, dùng thêm sự thật rằng, f(𝐱|σ) = (1/σ)f(𝐱/σ) sẽ có chung dạng, chỉ khác nhau scale param.
>
>
>
> Do đó ta sẽ đưa thêm vào tham số scalar: s.
>
>
>
> f(𝐱| 𝛌k, s) = (1/s) h(𝐱/s) g(𝛌k)exp{𝛌kᵀ𝐱/s}
>
>
>
> Mục đích là gì: Mục đích là để đưa thêm vào một giả định nữa: f(𝐱| 𝛌k, s) đều có chung scale parameter.
>
>
>
> ---
>
>
>
> Thay vào 4.58: a = ln \[f(𝐱|𝒞1)f(𝒞1)/f(𝐱|𝒞2)f(𝒞2)\]
>
>
>
> = ln {\[(1/s) h(𝐱/s) g(𝛌1) exp{𝛌1ᵀ𝐱/s} f(𝒞1)\] / \[(1/s) h(𝐱/s) g(𝛌2) exp{𝛌2ᵀ𝐱/s} f(𝒞2)\]}
>
>
>
> = ln {\[g(𝛌1) exp{𝛌1ᵀ𝐱/s} f(𝒞1)\] / \[g(𝛌2) exp{𝛌2ᵀ𝐱/s} f(𝒞2)\]}
>
>
>
> = ln g(𝛌1) + ln exp{𝛌1ᵀ𝐱/s} + ln f(𝒞1) - ln g(𝛌2) - ln exp{𝛌2ᵀ𝐱/s} - ln f(𝒞2)
>
>
>
> = 𝛌1ᵀ𝐱/s - 𝛌2ᵀ𝐱/s + ln g(𝛌1) - ln g(𝛌2) + ln f(𝒞1) - ln f(𝒞2)
>
>
>
> = (1/s)(𝛌1 - 𝛌2)ᵀ𝐱 + ln g(𝛌1) - ln g(𝛌2) + ln f(𝒞1) - ln f(𝒞2)
>
>
>
> Kết quả cho thấy đây cũng là hàm linear đối với 𝐱
>
>
>
> ---
>
>
>
> Tương tự với K-class (K &gt; 2)
>
>
>
> ..

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=Ovmp-M7j5II)

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **92/100** · ✓ Move on
>
> Ghi chú rất tốt, thể hiện tư duy kết nối mạch lạc từ bài toán Generative Classifier đến họ Exponential Family và tự tay biến đổi đại số chính xác ra hàm tuyến tính a(x).
>
> **🟡 Minor issues**
>
> **1.** *"Vậy thì nay, quay lại xét việc 𝐱 là feature liên tục. Thì như hồi học Casella đã biết, Normal distribution vẫn chỉ là thành viên của một họ phân phối lớn hơn, gọi là exponential family"*
>
> Họ Exponential Family bao quát cả biến liên tục (Gaussian, Gamma, Beta...) lẫn biến rời rạc (Bernoulli, Poisson, Multinomial...). Bishop mở đầu mục này nhằm mục đích thống nhất cả 2 trường hợp biến liên tục (Gaussian) và biến rời rạc (discrete inputs) đã học ở các phần trước về cùng một khuôn khổ tổng quát, chứ không chỉ riêng cho biến liên tục.
>
>
> **✓ Strengths**
> - Khả năng hệ thống hóa kiến thức và active recall logic từ mô hình sinh (generative), bài toán ước lượng tham số (MLE) đến việc tính xác suất hậu nghiệm rất rõ ràng.
> - Tự thực hiện đầy đủ và chuẩn xác các bước biến đổi log-odds từ công thức (4.84) để chứng minh a(x) có dạng tuyến tính đối với x.
> - Nhận diện đúng vai trò của các giả định: chọn u(x) = x để tuyến tính hóa và giả định chung scale parameter s giữa các lớp để triệt tiêu số hạng phi tuyến h(x/s).
>
> **💡 Deeper notes**
> - Trong công thức (4.85) của Bishop, hệ số (1/s) không xuất hiện trước (λ1 - λ2)ᵀx. Biến đổi của bạn giữ lại (1/s) là hoàn toàn khớp với định nghĩa (4.84), trong khi sách Bishop ngầm hấp thu 1/s vào tham số λ hoặc giả định s = 1 mà không nói rõ.

**🔗 See also:** [2.4 The Exponential Family](./24_the_exponential_family.md#node-1hlelhn) · [Scale Invariance and Prior Distributions](./243_non_informative_priors.md#node-6t8ihcb)

<br>

