# 4.3.4 Multiclass logistic regression

📊 **Progress:** `3` Notes | `3` Screenshots | `3` AI Reviews

---
<a id="node-o27ixba"></a>

<br>

<a id="node-fbzfqyw"></a>

## Multiclass Logistic Regression

<p align="center"><kbd><img src="assets/iwoiyq6g1yp.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý mở đầu tác giả nhắc lại chút cái ta đã biết ở mấy phần trước, nói rằng "với rất nhiều loại distribution" thì class posterior f(𝒞k|Φ) có dạng một softmax transformation của một hàm tuyến tính của feature Φ. Là sao nhỉ?
>
>
>
> Active recall tí xíu:
>
>
>
> Ta có f(𝒞k|Φ) = f(Φ|𝒞k)f(𝒞k)/f(Φ) (Bayes rule)
>
>
>
> = f(Φ|𝒞k)f(𝒞k)/ Σj f(Φ|𝒞j)f(𝒞j)
>
>
>
> = \[exp ln \[f(Φ|𝒞k)f(𝒞k)\] / Σj exp ln f(Φ|𝒞j)f(𝒞j)
>
>
>
> = exp(ak) / Σj exp(aj), với aj = ln \[f(Φ|𝒞j)f(𝒞j)\]
>
>
>
> ---
>
>
>
> Thế thì, aj này vẫn là hàm phi tuyến đối với Φ. Nhưng nếu xét class conditional density f(Φ|𝒞j) là thành viên của exponential có chung scale param, mà một ví dụ cụ thể là chúng đều là 𝒩(𝛍j, 𝚺) (cùng chung covariance matrix), thì khi đó:
>
>
>
> \[exp ln \[f(Φ|𝒞k)f(𝒞k)\] / Σj exp ln f(Φ|𝒞j)f(𝒞j) sẽ trở thành:
>
>
>
> {exp \[ln f(Φ|𝒞k) + ln f(𝒞k)\]} / Σj exp {ln f(Φ|𝒞j) + ln f(𝒞j)}
>
>
>
> = {exp \[ln f(Φ|𝒞k)\] exp ln f(𝒞k)} / Σj \[exp ln f(Φ|𝒞j)\] exp ln f(𝒞j)
>
>
>
> = exp \[ln f(Φ|𝒞k)\] f(𝒞k) / Σj \[exp ln f(Φ|𝒞j)\] f(𝒞j) (1)
>
>
>
> ---
>
>
>
> Xét exp \[ln f(Φ|𝒞k)\] = exp \[ln \[c(𝚺) exp(-(1/2)(Φ-𝛍k)ᵀ𝚺⁻¹(Φ-𝛍k)\]\]
>
>
>
> = exp \[ln c(𝚺) + ln exp(-(1/2)(Φ-𝛍k)ᵀ𝚺⁻¹(Φ-𝛍k)\]
>
>
>
> = exp \[ln c(𝚺) - (1/2)(Φ-𝛍k)ᵀ𝚺⁻¹(Φ-𝛍k)\]
>
>
>
> = exp \[ln c(𝚺)\] exp\[-(1/2)(Φ-𝛍k)ᵀ𝚺⁻¹(Φ-𝛍k)\]
>
>
>
> = c(𝚺) exp\[-(1/2)(Φᵀ𝚺⁻¹-𝛍kᵀ𝚺⁻¹)(Φ-𝛍k)\]
>
>
>
> = c(𝚺) exp\[-(1/2)(Φᵀ𝚺⁻¹Φ-𝛍kᵀ𝚺⁻¹Φ-Φᵀ𝚺⁻¹𝛍k+𝛍kᵀ𝚺⁻¹𝛍k)\]
>
>
>
> = c(𝚺) exp\[-(1/2)(Φᵀ𝚺⁻¹Φ-2Φᵀ𝚺⁻¹𝛍k+𝛍kᵀ𝚺⁻¹𝛍k)\]
>
>
>
> = c(𝚺) exp\[-(1/2)Φᵀ𝚺⁻¹Φ\] exp\[-(1/2)(-2Φᵀ𝚺⁻¹𝛍k+𝛍kᵀ𝚺⁻¹𝛍k)\]
>
>
>
> = c(𝚺) exp\[-(1/2)Φᵀ𝚺⁻¹Φ\] exp\[Φᵀ𝚺⁻¹𝛍k-(1/2)𝛍kᵀ𝚺⁻¹𝛍k)\]
>
>
>
> Tương tự các cục exp ln f(Φ|𝒞j) ở mẫu cũng sẽ bằng:
>
>
>
> c(𝚺) exp\[-(1/2)Φᵀ𝚺⁻¹Φ\] exp\[Φᵀ𝚺⁻¹𝛍j-(1/2)𝛍jᵀ𝚺⁻¹𝛍j)\]
>
>
>
> Nên: Từ (1), rút gọn có ở cả tử lẫn mẫu số:
>
>
>
> exp\[Φᵀ𝚺⁻¹𝛍k-(1/2)𝛍kᵀ𝚺⁻¹𝛍k)\]f(𝒞k) / Σj exp\[Φᵀ𝚺⁻¹𝛍j-(1/2)𝛍jᵀ𝚺⁻¹𝛍j)\]f(𝒞j)
>
>
>
> =exp\[Φᵀ𝚺⁻¹𝛍k-(1/2)𝛍kᵀ𝚺⁻¹𝛍k)\] exp \[ln f(𝒞k)\] / Σj exp\[Φᵀ𝚺⁻¹𝛍j-(1/2)𝛍jᵀ𝚺⁻¹𝛍j)\] exp \[lnf(𝒞j)\]
>
>
>
> = exp\[Φᵀ𝚺⁻¹𝛍k-(1/2)𝛍kᵀ𝚺⁻¹𝛍k)+ln(f(𝒞k))\] / Σj exp\[Φᵀ𝚺⁻¹𝛍j-(1/2)𝛍jᵀ𝚺⁻¹𝛍j)+ln f(𝒞j)\]
>
>
>
> và đặt lại ak = Φᵀ𝚺⁻¹𝛍k-(1/2)𝛍kᵀ𝚺⁻¹𝛍k+ln(f(𝒞k))
>
>
>
> ta có exp(ak) / Σj exp(aj), với ak là hàm tuyến tính của Φ.

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=-9YldVmpmPU)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, tự giác suy luận và chứng minh lại tại sao mô hình sinh (với phân phối Gauss cùng ma trận hiệp phương sai) lại dẫn đến hàm softmax dạng tuyến tính theo đúng tinh thần của sách.
>
> **✓ Strengths**
> - Tự giác thực hiện active recall giải thích cặn kẽ nhận định 'for a large class of distributions' của tác giả thay vì chỉ học vẹt công thức.
> - Khai triển đại số chính xác với giả định phân phối chuẩn đa biến cùng ma trận hiệp phương sai, triệt tiêu thành công số hạng bậc hai để thu được hàm tuyến tính đối với biến đặc trưng.
>
> **💡 Deeper notes**
> - Trong công thức (4.105), tác giả Bishop quy ước vector đặc trưng phi đã bao gồm phần tử bias (dummy feature phi_0 = 1) nên a_k được viết gọn là w_k^T phi; trong khai triển của bạn, hằng số -(1/2)mu_k^T Sigma^-1 mu_k + ln P(C_k) chính là trọng số định kiến (bias w_{k0}) đó.
> - Việc lấy exp(ln(...)) rồi lại tách ra có phần hơi thừa bước đại số (chỉ cần triệt tiêu trực tiếp phần tử chung từ f(Phi|C_k)), nhưng kết quả cuối cùng hoàn toàn chính xác.

**🔗 See also:** [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj)

<br>

<a id="node-bhochq3"></a>

### Activation Derivative for Maximum Likelihood

<p align="center"><kbd><img src="assets/bvuyg7ivvi.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, đại ý là như ta đã hiểu, với cách tiếp cận đi xây class posterior f(𝒞k|Φ) theo lối gián tiếp:
>
>
>
> Ta áp giả định phù hợp cho các class conditional density f(Φ|𝒞1),..f(Φ|𝒞K) thì kết quả mới có được là class posterior f(𝒞k|Φ) mới có dạng softmax transform của các activation là hàm tuyến tính của feature (như note trước vừa thấy). Đó là cái thứ nhất.
>
>
>
> Và để có được hình dạng của class posterior, tức inference ra class posterior parameter thì ta phải đi đường vòng:
>
>
>
> Tức là đầu tiên đi inference class conditional density f(Φ|𝒞k), rồi prior f(𝒞k) (dùng MLE, để estimator cái cái tham số như 𝛍1,..𝛍K, 𝚺, và tham số của f(𝒞k) mà trong case K=2, ta gọi là π, là f(𝒞1) đó)
>
>
>
> Cuối cùng mới dùng Bayes rule để có f(𝒞k|Φ)
>
>
>
> ---
>
>
>
> Thế thì có thể hiểu cách làm gián tiếp này chính là một cách gián tiếp, ta đã estimate tham số 𝐰 của f(𝒞k|Φ) = exp(ak)/Σj exp(aj) với ak = 𝐰kᵀΦ
>
>
>
> Cho nên, nay ta sẽ chuyển qua inference trực tiếp 𝐰, mà ý nghĩa của nó là, ta khỏi cần áp giả định phù hợp lên các class conditional density để có được dạng ak là hàm tuyến tính của Φ nữa, mà ta phang luôn giả định này vào class posterior, và chỉ việc đi estimate 𝐰 luôn.
>
>
>
> ---
>
>
>
> Vậy thì trong mô hình f(𝒞k|Φ) = exp(ak)/Σj exp(aj) với ak = 𝐰ᵀkΦ, nó đi qua hàm softmax nên sẽ cần chuẩn bị đạo hàm:
>
>
>
> Nên nhớ, với input Φ ta sẽ có output là một vector (y1,....yK)ᵀ, với yk = f(𝒞k|Φ) = exp(ak)/Σj exp(aj) và ak = 𝐰kᵀΦ. Do đó, yk là một hàm số vector → scalar yk(a1,...aK). Nên phải chuẩn bị gradient của hàm này, ∇yk.
>
>
>
> yk = f(𝒞k|Φ) = exp(ak)/Σj exp(aj)
>
>
>
> Xét ∂/∂ak yk:
>
>
>
> = ∂/∂ak \[exp(ak)/Σj exp(aj)\]  
>
>
>
> Dùng quotient rule | (u/v)' = (u' v - u v')/v²
>
>
>
> = {\[∂/∂ak exp(ak)\] Σj exp(aj) - exp(ak) \[∂/∂ak Σj exp(aj)\]} / \[Σj exp(aj)\]²
>
>
>
> = {exp(ak) Σj exp(aj) - exp(ak) exp(ak)} / \[Σj exp(aj)\]²
>
>
>
> = {exp(ak) Σj exp(aj) - exp(ak) exp(ak)} / \[Σj exp(aj)\]²
>
>
>
> = {exp(ak) \[Σj exp(aj) - exp(ak)\]} / \[Σj exp(aj)\]²
>
>
>
> = \[exp(ak) / Σj exp(aj)\] \[Σj exp(aj) - exp(ak)\] / Σj exp(aj)
>
>
>
> = yk \[1 - exp(ak) / Σj exp(aj)\]
>
>
>
> = yk (1 - yk)
>
>
>
> ---
>
>
>
> Xét ∂/∂aj yk, với j ≠ k:
>
>
>
> ∂/∂aj \[exp(ak)/Σi exp(ai)\]
>
>
>
> = {\[∂/∂aj exp(ak)\] Σi exp(ai) - exp(ak) \[∂/∂aj Σi exp(ai)\]} / \[Σi exp(ai)\]²
>
>
>
> = \[0 × Σi exp(ai) - exp(ak) exp(aj)\] / \[Σi exp(ai)\]²
>
>
>
> = \[- exp(ak) exp(aj)\] / \[Σi exp(ai)\]²
>
>
>
> = \[-exp(ak)/ Σi exp(ai)\] × \[exp(aj)\] / Σi exp(ai)\]
>
>
>
> = -yk yj
>
>
>
> Vậy ∂/∂ak yk = yk (1 - yk) và ∂/∂aj yk = -yk yj, ta ghi = yk (0 - yj) với j ≠ k
>
>
>
> Để thể hiện kết ∂/∂aj yk một cách khái quát cho cả case j=k và j khác k ta viết thành:
>
>
>
> ∂/∂aj yk = yk (I\_{k=j} - yj), với I\_{k=j} = 1 khi k=j và 0 khi k khác j
>
>
>
> Và nếu dùng matrix 𝐈 (vốn dĩ là matrix có 𝐈kj = 1 khi k=j và bằng 0 khi k≠j thì ta có công thức trên trở thành ∂/∂aj yk = yk (𝐈kj - yj)

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=RfrcgvaQmgU)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã đối chiếu rất rõ ràng giữa mô hình sinh (generative) và mô hình phân biệt (discriminative), đồng thời tự chứng minh chi tiết từng bước đạo hàm hàm softmax thay vì chỉ chép lại công thức.
>
> **✓ Strengths**
> - Hiểu sâu sắc sự khác biệt cốt lõi giữa tiếp cận gián tiếp (generative - ước lượng prior và class-conditional density rồi dùng Bayes) và trực tiếp (discriminative - giả định trực tiếp dạng hàm posterior rồi ước lượng tham số w bằng MLE).
> - Tự triển khai đạo hàm hàm softmax theo quy tắc đạo hàm phân thức (quotient rule) đầy đủ và chính xác cho cả hai trường hợp j = k và j ≠ k.
> - Tổng hợp khéo léo kết quả hai trường hợp về dạng chuẩn sử dụng phần tử của ma trận đơn vị Ikj (hoặc ký hiệu Kronecker delta).
>
> **💡 Deeper notes**
> - Ký hiệu phần tử ma trận đơn vị Ikj trong toán học và học máy thường được gọi là ký hiệu Kronecker delta (ký hiệu là δkj), mang ý nghĩa bằng 1 khi k = j và bằng 0 khi k ≠ j.
> - Do các yk có tổng bằng 1 (ràng buộc simplex), ma trận Jacobian ∂y/∂a thực chất bị suy biến (rank tối đa là K - 1), phản ánh tính chất redundant/over-parameterized của hàm softmax nếu không cố định một w làm mốc.

<br>

<a id="node-ndts6t4"></a>

#### Multiclass Cross-Entropy Error Function

<p align="center"><kbd><img src="assets/z9v5hlijwwq.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo là đi xây dựng likelihood function.
>
>
>
> Viết lại cái khung của bài toán point estimation tham số θ của sample X1,...Xn iid \~ f(x|θ). Ta sẽ đi tìm θ sao cho maximize hàm likelihood L(θ|𝐱), mang ý nghĩa là độ hợp lý của θ khi quan sát thấy giá trị của 𝐗 là bằng 𝐱, và giá trị hàm L(θ|𝐱) theo định nghĩa = f(𝐱|θ) = f(x1,x2..xn|θ), nhờ tính independent của X1,...Xn, = Πi f(xi|θ).
>
>
>
> Vậy ở đây một observation (tức một data point) sẽ là một cặp (Φ, class của nó), và class variable, ta sẽ dùng cách thể hiện 1-of-K coding scheme, tức thể hiện giá trị của target variable bởi một vector K chiều có số 1 tại vị trí tương ứng với class number của data point, còn lại là 0. Nên ta có data point thứ ith sẽ biểu thị bởi (Φi, 𝐭i) (và ta có i = 1,2...N)
>
>
>
> Nên joint distribution f(𝐱|θ) ở đây sẽ là f(Φ1,Φ2,...ΦN,𝐭1,𝐭2,..𝐭N|θ) (tạm dùng θ để chỉ tất cả tham số)
>
>
>
> Tiếp ta làm động tác tương tự như trong bài toán regression: sẽ chỉ coi 𝐭 là random variable, để chuyển joint distribution này thành f(𝐭1,𝐭2,..𝐭N|θ,Φ1,Φ2,...ΦN)
>
>
>
> Dùng tính chất độc lập của data, tách f(𝐭1,𝐭2,..𝐭N|θ,Φ1,Φ2,...ΦN) thành:
>
>
>
> f(𝐭1,𝐭2,..𝐭N|θ,Φ1,Φ2,...ΦN) = f(𝐭1|θ,Φ1)f(𝐭2|θ,Φ2)....f(𝐭N|θ,ΦN) (vẫn đang mượn θ,...để chỉ tham số của distribution) (1)
>
>
>
> Rồi, tới đây mới dùng việc ta đang giả định distribution của 𝐭, để xem f(𝐭1|θ,Φ1),f(𝐭2|θ,Φ2),.... hay f(𝐭|θ,Φ) là cái gì:
>
>
>
> ---
>
>
>
> Ta đã nói rằng ta sẽ phang thẳng giả định rằng: f(𝒞k|Φ) = P(C = 𝒞k|Φ) = yk = exp(ak) / Σj exp(aj) với ak = 𝐰kᵀΦ
>
>
>
> và cái này chính là giả định P(Tk=1|Φ) = yk = exp(ak) / Σj exp(aj) với ak = 𝐰kᵀΦ
>
>
>
> Và P(Tk=1|Φ) thì cũng chính là P(𝐓=\[one hot vector có số 1 tại vị trí k\]|Φ) = P(T1=0, T2=0,...,Tk=1,...,TK=0). Vì sao?
>
>
>
> Đơn giản là vì theo one-of-K coding scheme thì Tk = 1 ⇔ 𝐓=\[one hot vector có số 1 tại vị trí k\]
>
>
>
> Nên ta có P(𝐓=\[one hot vector có số 1 tại vị trí k\]|Φ) = yk
>
>
>
> Và để thể hiện một cách tổng quát, ta thể hiện như sau: P(𝐓=𝐭|Φ) = Πk=1:K (yk^tk)
>
>
>
> ghi rõ ra yk phụ thuộc Φ, 𝐰1,...𝐰K: P(𝐓=𝐭|Φ) = Πk=1:K (yk(Φ, 𝐰1,..𝐰K)^tk) để thấy rõ tham số của distribution này là 𝐰1,..𝐰K
>
>
>
> Và P(𝐓=𝐭|Φ) này chính là f(𝐭|θ,Φ) ở trên, nên lúc này ta sẽ ghi là f(𝐭|𝐰1,𝐰2,...𝐰K, Φ)
>
>
>
> ---
>
>
>
> Từ đó quay lại (1), ta có:
>
>
>
> f(𝐭1,𝐭2,..𝐭N|θ,Φ1,Φ2,...ΦN) = f(𝐭1|𝐰1,𝐰2,...𝐰K, Φ1) × f(𝐭2|𝐰1,𝐰2,...𝐰K, Φ2) × ... × f(𝐭N|𝐰1,𝐰2,...𝐰K, ΦN)
>
>
>
> = Πk=1:K (y1k^t1k) × Πk=1:K (y2k^t2k) × ....× × Πk=1:K (yNk^tNk)
>
>
>
> = Πn=1:N \[Πk=1:K (ynk^tnk)\] → chính là 4.107.
>
>
>
> Đương nhiên giờ ta có thể thay θ = 𝐰1,...𝐰K và gom 𝐭1,...𝐭N thành matrix 𝐓, để có:
>
>
>
> f(𝐓|𝐰1,𝐰2,...𝐰K,Φ1,Φ2,...ΦN) = Πn=1:N \[Πk=1:K (ynk^tnk)\]
>
>
>
> và làm động tác giản lược bớt bằng cách cố tình không ghi Φ1,Φ2,...ΦN ra, nhưng phải nhớ nó có phụ thuộc
>
>
>
> Và đây chính là cái f(𝐱|θ) trong cái khung ở trên, nên cũng chính là likelihood (khi coi nó là hàm của 𝐰1,...𝐰K):
>
>
>
> L(𝐰1,...𝐰K|𝐓) = Πn=1:N \[Πk=1:K (ynk^tnk)\]
>
>
>
> ---
>
>
>
> Tương tự như đã quen, ta sẽ lấy ln, (để chuyển thành bài toán tương đương maximize ln likelihood do ln là hàm monotone increasing)
>
>
>
> ln L = ln \[Πn=1:N \[Πk=1:K (ynk^tnk)\]\]
>
>
>
> = Σn=1:N ln \[Πk=1:K (ynk^tnk)\]
>
>
>
> = Σn=1:N Σk=1:K \[ln(ynk^tnk)\]
>
>
>
> = Σn=1:N Σk=1:K \[tnk ln(ynk)\] → 4.108
>
>
>
> Và lấy dấu âm, để chuyển thành bài toán minimize objective, cái ta có chính là cross entropy loss (error) function (bữa trước là binary cross entropy)
>
>
>
> E(𝐰) = - Σn=1:N Σk=1:K \[tnk ln(ynk)\]

📹 [Xem video trên YouTube](https://youtu.be/S4kORpAgTsQ)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã giải thích và diễn giải tường minh từng bước từ mô hình xác suất có điều kiện (Multinoulli), tính độc lập giữa các mẫu, dạng tích lũy thừa của 1-of-K coding cho đến hàm Cross-Entropy nhiều lớp.
>
> **✓ Strengths**
> - Diễn giải cực kỳ rõ ràng vì sao phân phối xác suất của vector 1-of-K lại viết được dưới dạng tích lũy thừa P(T=t|Φ) = Π y_k^{t_k}.
> - Nêu bật được bản chất đây là conditional likelihood (mô hình discriminative coi t là biến ngẫu nhiên và điều kiện hóa trên Φ).
> - Các bước biến đổi đại số từ tích sang tổng logarit và đổi dấu để thành hàm mất mát (loss function) hoàn toàn chính xác.
>
> **💡 Deeper notes**
> - Hàm phân phối này thực chất là phân phối Categorical (hay Multinoulli / Generalized Bernoulli). Dạng tích lũy thừa Π y_k^{t_k} tương tự như Bernoulli (y^t (1-y)^{1-t}) nhưng mở rộng cho K classes với ràng buộc vector t có đúng một phần tử bằng 1 và tổng y_k bằng 1.

<br>

