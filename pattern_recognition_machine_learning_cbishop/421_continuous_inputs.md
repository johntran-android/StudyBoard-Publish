# 4.2.1 Continuous inputs

📊 **Progress:** `1` Notes | `4` Screenshots | `1` AI Reviews

---
<a id="node-6fsg97x"></a>

<br>

<a id="node-gsbsdud"></a>

## Section 4.2.1 Continuous Inputs

<p align="center"><kbd><img src="assets/6iczyb70t1.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ne903ep6lff.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qel4j06cbi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/65dy2phvlti.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên, ta sẽ giả định class-conditional densities là phân phối Gaussian.Và một giả định thêm nữa là các class-conditional densities của các class đều có chung covariance.
>
>
>
> (class-conditional densities, tức là f(𝐱|𝒞k), là cái mà ý nghĩa nôm na là cho ta biết, "một tấm hình chụp chó sẽ trông như thế nào", hay nếu bảo đây là hình chụp chó (𝒞k) thì xác suất nó trong giống như thế này (𝐱) là cao hay thấp (f(𝐱|𝒞k))")
>
>
>
> Nên ta có f(𝐱|𝒞k) = 1/(2π)^(D/2) × 1/(|𝚺|^1/2) × exp{-(1/2)(𝐱-𝛍k)ᵀ𝚺⁻¹(𝐱-𝛍k)}
>
>
>
> Xét bài toán K=2 trước, với 4.57 và 4.57, tức f(𝒞1|𝐱) = σ(a) và a = ln \[f(𝐱|𝒞1)f(𝒞1)/f(𝐱|𝒞2)f(𝒞2)\], ta có:
>
>
>
> a = ln \[f(𝐱|𝒞1)f(𝒞1)/f(𝐱|𝒞2)f(𝒞2)\] 
>
>
>
> = ln {\[f(𝐱|𝒞1)/f(𝐱|𝒞2)\] × \[f(𝒞1)/f(𝒞2)\]}
>
>
>
> = ln {\[f(𝐱|𝒞1)/f(𝐱|𝒞2)\]} + ln \[f(𝒞1)/f(𝒞2)\]
>
>
>
> Xét cục f(𝐱|𝒞1)/f(𝐱|𝒞2), thế pdf ở trên vô, các term 1, 2 sẽ triệt tiêu nhau (do có cùng covariance, tức 𝚺 bằng nhau) chỉ còn: 
>
>
>
> exp{-(1/2)(𝐱-𝛍1)ᵀ𝚺⁻¹(𝐱-𝛍1)}/exp{-(1/2)(𝐱-𝛍2)ᵀ𝚺⁻¹(𝐱-𝛍2)} 
>
>
>
> ⇒ ln {\[f(𝐱|𝒞1)/f(𝐱|𝒞2)\]} = ln {exp{-(1/2)(𝐱-𝛍1)ᵀ𝚺⁻¹(𝐱-𝛍1)}/exp{-(1/2)(𝐱-𝛍2)ᵀ𝚺⁻¹(𝐱-𝛍2)}}
>
>
>
> = ln {exp{-(1/2)(𝐱-𝛍1)ᵀ𝚺⁻¹(𝐱-𝛍1)}} - ln{exp{-(1/2)(𝐱-𝛍2)ᵀ𝚺⁻¹(𝐱-𝛍2)}}
>
>
>
> = -(1/2)(𝐱-𝛍1)ᵀ𝚺⁻¹(𝐱-𝛍1) + (1/2)(𝐱-𝛍2)ᵀ𝚺⁻¹(𝐱-𝛍2)
>
>
>
> = -(1/2)\[(𝐱-𝛍1)ᵀ𝚺⁻¹(𝐱-𝛍1) - (𝐱-𝛍2)ᵀ𝚺⁻¹(𝐱-𝛍2)\]
>
>
>
> = -(1/2)\[(𝐱ᵀ𝚺⁻¹-𝛍1ᵀ𝚺⁻¹)(𝐱-𝛍1) - (𝐱ᵀ𝚺⁻¹-𝛍2ᵀ𝚺⁻¹)(𝐱-𝛍2)\]
>
>
>
> = -(1/2)\[(𝐱ᵀ𝚺⁻¹𝐱-𝛍1ᵀ𝚺⁻¹𝐱-𝐱ᵀ𝚺⁻¹𝛍1+𝛍1ᵀ𝚺⁻¹𝛍1 - (𝐱ᵀ𝚺⁻¹𝐱-𝛍2ᵀ𝚺⁻¹𝐱-𝐱ᵀ𝚺⁻¹𝛍2+𝛍2ᵀ𝚺⁻¹𝛍2)\]
>
>
>
> = -(1/2)(𝐱ᵀ𝚺⁻¹𝐱-𝛍1ᵀ𝚺⁻¹𝐱-𝐱ᵀ𝚺⁻¹𝛍1+𝛍1ᵀ𝚺⁻¹𝛍1 - 𝐱ᵀ𝚺⁻¹𝐱+𝛍2ᵀ𝚺⁻¹𝐱+𝐱ᵀ𝚺⁻¹𝛍2-𝛍2ᵀ𝚺⁻¹𝛍2)
>
>
>
> (để ý chỗ này, quan trọng, các quadratic term 𝐱ᵀ𝚺⁻¹𝐱 sẽ triệt tiêu, là nhờ ta đang xài cùng một 𝚺)
>
>
>
> (Và xét 𝛍1ᵀ𝚺⁻¹𝐱, vì là scalar, nên = (𝛍1ᵀ𝚺⁻¹𝐱)ᵀ = 𝐱ᵀ(𝚺⁻¹)ᵀ𝛍1 = 𝐱ᵀ𝚺⁻¹𝛍1 (do 𝚺 đối xứng do là covariance), nên -𝛍1ᵀ𝚺⁻¹𝐱-𝐱ᵀ𝚺⁻¹𝛍1 = -2𝛍1ᵀ𝚺⁻¹𝐱)
>
>
>
> = -(1/2)(-2𝛍1ᵀ𝚺⁻¹𝐱 + 2𝛍2ᵀ𝚺⁻¹𝐱 + 𝛍1ᵀ𝚺⁻¹𝛍1 - 𝛍2ᵀ𝚺⁻¹𝛍2)
>
>
>
> = 𝛍1ᵀ𝚺⁻¹𝐱 - 𝛍2ᵀ𝚺⁻¹𝐱 -(1/2)(𝛍1ᵀ𝚺⁻¹𝛍1 - 𝛍2ᵀ𝚺⁻¹𝛍2)
>
>
>
> = (𝛍1ᵀ𝚺⁻¹ - 𝛍2ᵀ𝚺⁻¹)𝐱 -(1/2)(𝛍1ᵀ𝚺⁻¹𝛍1 - 𝛍2ᵀ𝚺⁻¹𝛍2)
>
>
>
> = (𝚺⁻¹𝛍1 - 𝚺⁻¹𝛍2)ᵀ𝐱 -(1/2)(𝛍1ᵀ𝚺⁻¹𝛍1 - 𝛍2ᵀ𝚺⁻¹𝛍2)
>
>
>
> = \[𝚺⁻¹(𝛍1 - 𝛍2)\]ᵀ𝐱 -(1/2)(𝛍1ᵀ𝚺⁻¹𝛍1 - 𝛍2ᵀ𝚺⁻¹𝛍2)
>
>
>
> Vậy a = ln {\[f(𝐱|𝒞1)/f(𝐱|𝒞2)\]} + ln \[f(𝒞1)/f(𝒞2)\] 
>
>
>
> = \[𝚺⁻¹(𝛍1 - 𝛍2)\]ᵀ𝐱 -(1/2)(𝛍1ᵀ𝚺⁻¹𝛍1 - 𝛍2ᵀ𝚺⁻¹𝛍2) + ln \[f(𝒞1)/f(𝒞2)\] 
>
>
>
> Và ta đặt 𝐰 = 𝚺⁻¹(𝛍1 - 𝛍2) (chính là 4.66) và w0 = -(1/2)(𝛍1ᵀ𝚺⁻¹𝛍1 - 𝛍2ᵀ𝚺⁻¹𝛍2) + ln \[f(𝒞1)/f(𝒞2)\] (chính là 4.67) thì a chính là 𝐰ᵀ𝐱 + w0.
>
>
>
> Mình nhận xét: Như vậy là sao? Ý nghĩa gì? → Có nghĩa là bằng cách giả định f(𝐱|𝒞k) là phân phối normal và mọi k đều có chung covariance matrix thì a (= ln của tỉ lệ f(𝐱, 𝒞1) / f(𝐱, 𝒞2)) hóa ra là một hàm tuyến tính của 𝐱 và 𝐰. Để rồi f(𝒞1|𝐱) = σ(𝐰ᵀ𝐱 + w0). 
>
>
>
> Và hình 4.10 minh họa ý nghĩa của kết quả trên: Bên trái là hai quả chuông normal của class-conditional densities f(𝐱|𝒞1) và f(𝐱|𝒞2), có mean khác nhau, nhưng độ mập và hình dáng giống nhau (do chung covariance).
>
>
>
> Và mình hình dung thế này, khi :
>
>
>
> "đi từ nơi có f(𝐱|𝒞1) cao, f(𝐱|𝒞2) thấp tới nơi có f(𝐱|𝒞1) thấp f(𝐱|𝒞2) cao, thì 
>
>
>
> tỉ số f(𝐱|𝒞1)/f(𝐱|𝒞2) sẽ thay đổi từ rất lớn (+∞) → rất nhỏ (0) (sự thay đổi này là phi tuyến đối với x)
>
>
>
> thì a = ln \[f(𝐱|𝒞1)/f(𝐱|𝒞2)\] cũng thay đổi từ +∞ → -∞ (sự thay đổi này là **tuyến tính** đối vói 𝐱)
>
>
>
> dẫn đến σ(a) sẽ từ ≈ 1 → 0
>
>
>
> Và trực giác của cái này có gì đó rất hợp lý: Đi từ (thay đổi 𝐱) nơi (gọi là 𝐱A) có f(𝐱|𝒞1) cao tới nơi có f(𝐱|𝒞2) cao (gọi là 𝐱B đi) 
>
>
>
> Giống như dùng photoshop cái hình A đang trả lời cho câu hỏi: "Nếu là hình chó thì nên trông như thế nào" chuyển sang hình B là cái hình trả lời cho câu hỏi "Nếu là hình mèo thì nên trông như thế nào". Thì khi đó, đương nhiên là nếu ném caí hình đang biến đổi từ A sang B đó vào câu hỏi "xác suất hình này là chó là bao nhiêu" thì ta sẽ có một sự biến chuyển từ "rất cao" sang "rất thấp"
>
>
>
> Một điểm mấu chốt cần để ý, sở dĩ hàm a = ln \[f(𝐱|𝒞1)/f(𝐱|𝒞2)\] là hàm tuyến tính theo 𝐱 là nhờ việc ta đang giả định rằng f(𝐱|𝒞1) và f(𝐱|𝒞2) đều là Gaussian có chung covariance matrix.
>
>
>
> ---
>
>
>
> Một ý rất hay nữa, là, với f(𝒞1|𝐱) = σ(𝐰ᵀ𝐱 + w0) = σ(\[𝚺⁻¹(𝛍1 - 𝛍2)\]ᵀ𝐱 -(1/2)(𝛍1ᵀ𝚺⁻¹𝛍1 - 𝛍2ᵀ𝚺⁻¹𝛍2) + ln \[f(𝒞1)/f(𝒞2)\]) như vậy, thì decision boundary sẽ là:
>
>
>
> f(𝒞1|𝐱) = f(𝒞1|𝐱) = 0.5
>
>
>
> ⇔ σ(𝐰ᵀ𝐱 + w0) = 0.5
>
>
>
> ⇔ 𝐰ᵀ𝐱 + w0 = 0
>
>
>
> ⇔ 𝐰ᵀ𝐱 + w0  = 0, và như vậy, đây là phương trình của một hyperplane (trong hình minh họa với 𝐱 ∈ R² và đồ thị f(𝐱|𝒞1), f(𝐱|𝒞1) trong R³ thì nơi mà hai quả chuông này giao nhau làm thành 1 đường cong mà khi chiếu xuống mặt  R² sẽ thành một đường thẳng.
>
>
>
> Và một ý rất hay nữa, là ở trong w0 có cục ln \[f(𝒞1)/f(𝒞2)\]) chứ yếu tố prior distribution của mỗi class (cái này kiểu như trả lời câu hỏi, trong tự nhiên thì (hình) chó hay mèo nhiều hơn / phổ biến hơn). Do đó, ảnh hưởng priori sẽ chỉ đóng vai trò dịch chuyển cái đường decision boudary này một cách song song (về phía nào mà prior nhỏ hơn)

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **95/100** · ✓ Move on
>
> Ghi chú xuất sắc, biến đổi đại số ma trận rất chặt chẽ và trực giác hình học/xác suất rất sâu sắc. Chỉ có vài lỗi gõ phím nhỏ (typo) không ảnh hưởng đến bản chất.
>
> **🟡 Minor issues**
>
> **1.** *"với 4.57 và 4.57, tức f(𝒞1|𝐱) = σ(a)..."*
>
> Lỗi gõ nhầm số hiệu công thức: trong sách gốc là (4.57) và (4.58).
>
> **2.** *"f(𝒞1|𝐱) = f(𝒞1|𝐱) = 0.5"*
>
> Lỗi typo ký hiệu, vế chính xác phải là f(𝒞1|𝐱) = f(𝒞2|𝐱) = 0.5.
>
> **3.** *"nơi mà hai quả chuông này giao nhau sẽ làm thành 1 mặt phẳng, chiếu xuống R² sẽ thành một đường thẳng."*
>
> Về mặt hình học trong không gian 3 chiều (x1, x2, z), giao tuyến giữa 2 mặt Gauss là một đường cong không gian (nằm trên mặt phẳng đứng wᵀx + w0 = 0) chứ bản thân vết cắt không phải là một mặt phẳng.
>
>
> **✓ Strengths**
> - Biến đổi đại số ma trận cực kỳ chi tiết, khai triển chuẩn xác tính chất đối xứng của ma trận hiệp phương sai để triệt tiêu số hạng bậc hai.
> - Hiểu rõ vai trò của giả định cùng covariance matrix đối với tính tuyến tính của log-odds và decision boundary.
> - Trực giác trực quan hóa rất tốt về việc thay đổi prior sẽ tịnh tiến mặt phân chia song song về phía class có prior nhỏ hơn.
>
> **💡 Deeper notes**
> - Nếu hai lớp không dùng chung ma trận hiệp phương sai (𝚺1 ≠ 𝚺2), các số hạng bậc hai xᵀ𝚺⁻¹x sẽ không bị triệt tiêu, dẫn đến hàm bậc hai theo x trong sigmoid và ta thu được Quadratic Discriminant Analysis (QDA) với biên phân chia phi tuyến (quadratic boundary).

**🔗 See also:** [Section 4.2 Probabilistic Generative Models](./42_probabilistic_generative_model.md#node-dutlk1o) · [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj)

<br>

