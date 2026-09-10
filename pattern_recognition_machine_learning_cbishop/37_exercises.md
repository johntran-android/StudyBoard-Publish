# 3.7 Exercises

📊 **Progress:** `5` Notes | `6` Screenshots | `5` AI Reviews

---
<a id="node-rasw876"></a>

<br>

<a id="node-2dv7p1f"></a>

## Ex 3.2 Orthogonal Projection and Least Squares

<p align="center"><kbd><img src="assets/lg2vx7zrt3.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/1jbwnpklc2o.png" width="80%"></kbd></p>

> [!NOTE]
> Bài này thì thật ra quá trình note Feynman trong lúc học mục 3.1.2 thì mình đã làm rồi. (xem link)
>
>
>
> Nói sơ lại nhanh vì đây cũng là bài ta áp dụng kiến thức từ MIT 18.06 rất hay:
>
>
>
> Trong bài nói về projection matrix thầy Strang giúp ta lập luận ra cái công thức của matrix projection onto C(A) rất dễ như sau, ta có matrix A size m × n. Thì C(A), column space, theo định nghĩa chính là subspace tạo bởi mọi linear combination của các column vector của matrix A. Thế thì, xét một vector b ∈ R^m, khi chiếu nó lên C(A), được p, thì dĩ nhiên p ∈ C(A), nên theo định nghĩa của C(A), p phải là linear combination các vector column của A vói hệ số tổ hợp nào đó, ta gọi là x, tức p = Ax. Và phần dư, e = b - p, theo góc nhìn hình học sẽ phải vuông góc với C(A) (như việc ta chiếu 1 điểm trong R³ lên mặt phẳng, thì vector b tách thành 2 phần, 1 nằm trong mặt phẳng, một vuông góc với mặt phẳng vậy). Như vậy, e ⊥ C(A) mà theo định lý cơ bản của của đại số tuyến tính, nói rằng ta có hai cặp subspace bù nhau và vuông góc đó là column space và left nullspace, rowspace và nullspace. Vậy thì theo đó, khi e ⊥ C(A) suy ra e ∈ left nullspace N(Aᵀ). Điều này đồng nghĩa phương trình e là nghiệm của Aᵀx = 0, tức Aᵀe = 0 (A transpose e = 0, trong cách ghi chú của mình, mình luôn dùng T là cho transpose cho gọn, khi nào cần dùng chữ T thì sẽ ghi rõ). Vậy ta có:
>
>
>
> Aᵀe = 0 ⇔ Aᵀ(b - p) = 0 ⇔ Aᵀb = Aᵀp ⇔ Aᵀb = AᵀAx đây chính là normal equation.
>
>
>
> Tiếp, khi A full column rank, thì AᵀA sẽ full rank cũng là invertible khiến ta có thể nhân hai vế cho (AᵀA)⁻¹, ta sẽ có: x = (AᵀA)⁻¹ Aᵀb, và p = Ax = A(AᵀA)⁻¹ Aᵀb, đặt P = A(AᵀA)⁻¹ Aᵀ, ta có p = Pb, đồng nghĩa, projection giúp chiếu b lên C(A) chính là P = A(AᵀA)⁻¹ Aᵀ
>
>
>
> Vậy tới đây ta chỉ việc áp dụng kết quả này, để có matrix giúp chiếu v lên space spanned bởi columns của **Φ** (cái này chính là column space của **Φ** thôi, tức C(**Φ**)) sẽ là: **Φ**(**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ.
>
>
>
> Trong bài giảng đó, thấy thầy cũng check lại hai tính chất của projection matrix, là PP = P (chiểu b lên C(A) rồi thì chiếu lần nữa sẽ giữ nguyên, và Pᵀ = P) ta thử xem: 
>
>
>
> \[**Φ**(**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ\] \[**Φ**(**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ\] 
>
>
>
> = **Φ**(**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ**Φ**(**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ
>
>
>
> = **Φ I** (**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ
>
>
>
> = **Φ** (**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ → đúng là PP = P
>
>
>
> Và Xét \[**Φ**(**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ\]ᵀ, dùng rule (AB)ᵀ = Bᵀ Aᵀ:
>
>
>
> = (**Φ**ᵀ)ᵀ \[**Φ**(**Φ**ᵀ**Φ**)⁻¹\]ᵀ\]
>
>
>
> = **Φ** \[(**Φ**ᵀ**Φ**)⁻¹\]ᵀ **Φ**ᵀ\]
>
>
>
> = **Φ** \[(**Φ**ᵀ**Φ**)⁻¹\] **Φ**ᵀ\] (do **Φ**ᵀ**Φ** đối xứng nên **(Φ**ᵀ**Φ**)⁻¹ cũng vậy.
>
>
>
>
>
> ---
>
>
>
> Và như vậy, công thức 3.15, tức MLE của 𝐰, 𝐰ML:\*\* = (**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ𝐭 thì **Φw**ML sẽ là:
>
>
>
> **Φ**(**Φ**ᵀ**Φ**)⁻¹ **Φ**ᵀ𝐭, chính là tương ứng với p = A(AᵀA)⁻¹ Aᵀb hình chiếu của b lên C(A), thì cái này chính là hình chiếu của **t lên** C(**Φ**) chứ gì nữa.
>
>
>
> Như vậy 𝐰ML sẽ là có vai trò như 𝐱 ở trên đó là BỘ HỆ SỐ TỔ HỢP GIÚP LINEARLY COMBINE CÁC COLUMN VECTOR CỦA **Φ** ĐỂ ĐƯỢC PROJECTION CỦA 𝐭 LÊN C(**Φ**).

---

🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on

Ghi chú xuất sắc, kết hợp rất tốt kiến thức Đại số tuyến tính từ MIT 18.06 để giải thích trực quan và chứng minh chặt chẽ cả hai yêu cầu của bài toán. Các bước chứng minh tính chất ma trận hình chiếu và liên hệ với lời giải tối ưu w_ML đều hoàn toàn chính xác.

**🔗 See also:** [3.1.2 Geometry of least squares](./312_geometry_of_least_squares.md#node-6e545fx) · [Maximum Likelihood and Gradient](./311_maximum_likelihood_and_least_squares.md#node-ogc31vz)

<br>

<a id="node-tu3cct2"></a>

### Ex 3.5 Lagrange Multipliers in Regularization

<p align="center"><kbd><img src="assets/8np4ha463u5.png" width="80%"></kbd></p>

> [!NOTE]
> Bài tập này muốn ta chỉ ra hai bài toán tối ưu sau là equivalent:
>
>
>
> (3.29): minimize (over 𝐰) (1/2 E_D(𝐰) + (λ/2) Σj |wj|^q
>
>
>
> minimize (3.12) E_D(𝐰) = Σi {(ti-𝐰ᵀΦ(𝐱i))²/2} với ràng buộc (3/30) Σj |wj|^q ≤ η
>
>
>
> Again, mình cũng đã giải một phần trong quá trình ghi chú kiểu Feynman rồi, xem link tới note của 3.1.4, ở đây làm rõ thêm chút:
>
>
>
> Để hiểu cái này dễ nhất là vận dụng kiến thức đã học trong cuốn Numerical Optimization, chapter 12, bài toán tối ưu hàm f có ràng buộc, trong đó, ta được học về định lý điều kiện cần bậc nhất, còn gọi là KKT conditions:
>
>
>
> Và cách hay nhất để nhớ KKT condition là dựa vào lập luận trực giác sau: Giả sử ta có bài toán minimize f(x) với ràng buộc c1(x) ≥ 0. Thì để tìm nghiệm của bài toán này, tức là tìm x sao cho f(x) nhỏ nhất nhưng x vẫn thỏa ràng buộc c1(x), ta sẽ phải làm từng bước. Và bước đầu tiên đó là, tìm các ứng cử viên trước, bằng cách loại bỏ bớt các điểm không thể là solution. Và cách làm này sẽ dẫn dắt ta xây dựng được điều kiện cần KKT mà không phải học thuộc lòng. Lập luận như sau:
>
>
>
> Ta sẽ loại bỏ những điểm sau đây: là những điểm mà từ đó vẫn có thể đi theo hướng nào đó giúp vẫn feasible (thỏa constraint) đồng thời giảm hàm linearized f(x). Là sao?
>
>
>
> Đầu tiên xét tại x\*, định lý Taylor cho phép ta rằng, khi x đủ gần x\*, thì hàm f(x) ≈ f(x\*) + ∇f(x\*)ᵀ(x-x\*), ý nghĩa là, trong phạm vi lân cận x\*, hàm f (có thể là hàm phi tuyến) hành xử gần giống hàm tuyến tính f^(x) = f(x\*) + ∇f(x\*)ᵀ(x-x\*).
>
>
>
> Vậy thì, nếu như giả sử ta có điểm x1, mà tại đó tồn tại vector s có độ dài rất nhỏ khiến f^ giảm, tức:
>
>
>
> f^(x1 + s) &lt; f^(x1)
>
>
>
> và như vừa nói trong phạm vi s + s1 rất gần x1 thì hàm f hành xử giống f^, nên điều này rõ ràng sẽ khiến f(x1 + s) &lt; f(x1), như vậy x1 chắc chắn không phải là solution. vì còn có điểm x1 + s vẫn feasible mà objective lại nhỏ hơn. Nên ta sẽ loại bỏ x1 ra khỏi danh sách ứng cử viên.
>
>
>
> Ngược lại, nếu tại x2, không thể tìm được s giống như trên thì x2 sẽ là ứng cử viên cho solution. (vì sao chưa chắc là solution, là vì ta chỉ đang lập luận dựa trên ý chính là: nếu còn có thể đi theo hướng nào đó để giảm xấp xỉ bậc 1 của f, thì chắc chắn là sẽ có thể giảm f, nên ko phải solution. Nhưng ngược lại, nếu không thể đi theo hướng nào giúp giảm xấp xỉ bậc 1 của f, thì cũng chưa chắc nó là solution, vì có thể khi xét thêm điều kiện bậc 2 thì candidate cũng bị loại, đây sẽ là lập luận cho điều kiện đủ bậc 2)
>
>
>
> Còn để s là feasible direction, ta sẽ cần c1(x + s) vẫn ≥ 0, với s nhỏ, c1(x + s) cũng hành xử gần giống hàm tuyến tính, nên điều kiện trở thành c1(x) + ∇c1(x)ᵀs ≥ 0 (2)
>
>
>
> Vậy lập luận như sau, yêu cầu là: ta chia hai trường hợp:
>
>
>
> Case i) Gỉa sử tại x\*, constraint đang inactive: c1(x\*) &gt; 0, khi đó, dễ thấy là để thỏa tồn tại feasible direcition s: c1(x\*) + ∇c1(x\*)ᵀs ≥ 0, thì thật ra s có thể là vector có hướng tùy ý, miễn là giả sử nếu hướng của nó khiến ∇c1(x)ᵀs âm, thì chỉ cần khống chế độ lớn của s để giá trị âm ko quá nhỏ, giúp c1(x\*) dương vẫn đủ gánh. Như vậy có thể nói trong trường hợp này luôn tồn tại s giúp x\* + s vẫn feasible. Vậy câu hỏi để tìm candidate là, điểm x\* này nên như thế nào thì không thể đi theo s bất kì giúp giảm f^? Câu trả lời đó là: x\* là điểm mà gradient hàm f tại đó đang = 0. Vì khi đó f^(x\* + s) = f(x\*) + ∇f(x\*)ᵀs = f(x\*) bất kể s có là gì.
>
>
>
> Vậy, khi x\* có c1(x\*) &gt; 0 thì điều kiện để nó là candidate cho solution là ∇f(x\*) = 0
>
>
>
>
>
> Case ii) Tại x\*, constraint đang active: c1(x\*) = 0. Lúc này, điều kiện c1(x\*) + ∇c1(x\*)ᵀs ≥ 0 ⇔ ∇c1(x\*)ᵀs ≥ 0, tức s hợp góc nhọn hoặc tù với ∇c1(x\*). Trong khi đó, để thỏa việc giảm f^, thì ∇f(x\*)ᵀs phải &lt; 0 tức s hợp với ∇f(x\*) góc tù. Như vậy, cách duy nhất để tại x\* không thể tồn tại s thỏa hai cái này chính là ∇f(x\*) trùng hướng ∇c1(x\*). vì khi đó ko thể có s vừa hợp góc tù | nhọn với vector ∇f(x\*) mà lại vừa hợp góc tù với ∇f(x\*) được. Và điều kiện này thể hiện theo toán học là:
>
>
>
> Tồn tại λ\*1 sao cho ∇f(x\*) = λ\*1 ∇c1(x\*), λ\*1 ≥ 0.
>
>
>
> Tổng hợp lại:
>
>
>
> Nếu c1(x\*) &gt; 0 thì điều kiện để x\* là candidate là ∇f(x\*) = 0
>
>
>
> Nếu c1(x\*) = 0 thì điều kiện để x\* là candidate là Tồn tại λ1 sao cho ∇f(x\*) = λ1 ∇c1(x\*), λ1 ≥ 0.
>
>
>
> Và người ta đặt ra hàm Lagrangian ℒ(x, λ) = f(x) - λ1 c1(x). Ta có thể thể hiện cả hai case trên như sau (sẽ giải thích ở dưới)
>
>
>
> x\* phải thỏa:
>
>
>
> ∇\_x ℒ(x\*, λ\*) = 0 ⇔ ∇f(x\*) - λ1 ∇c1(x\*) = 0 ⇔ ∇f(x\*) = λ1 ∇c1(x\*)
>
>
>
> Cái này chính là stationary condition của KKT condition
>
>
>
> λ\*1 c1(x\*) = 0
>
>
>
> Cái này chính là complementary slackness condition của KKT
>
>
>
> λ\*1 ≥ 0.
>
>
>
> Cái này gọi là dual feasible
>
>
>
> và thêm constrain ban đầu c1(x) ≥ 0, gọi là primal feasible
>
>
>
> gom lại ta có đủ KKT condition.
>
>
>
> Giải thích vì sao nói "Ta có thể thể hiện cả hai case trên như sau"
>
>
>
> Xét c1(x\*) &gt; 0, thì từ complemetary condition ta suy ra λ\*1 = 0, khiến stationary condition trở thành ∇f(x\*) = 0 → chính là điều kiện của case 1 hồi nãy.
>
>
>
> Xét c1(x\*) = 0, thì stationary condition chính là điều kiện của case 2 hồi nãy.
>
>
>
> ---
>
>
>
> Rồi, với lập luận trên về cơ bản ta đã hiểu cách derive KKT condition, quay lại bài tập 3.5 này như sau:
>
>
>
> Để chứng minh chúng tương đương, chỉ việc chỉ ra rằng điều kiện cần để giảm tìm nghiệm của hai bài toán này là như nhau:
>
>
>
> Xét bài toán 1: minimize (over 𝐰) (1/2 E_D(𝐰) + (λ/2) Σj |wj|^q, đây là bài toán unconstraint nên điều kiện cần tối ưu bậc nhất đơn giản là: gradient của objective = 0:
>
>
>
> ∇\_𝐰 \[(1/2 E_D(𝐰) + (λ/2) Σj |wj|^q\] = 0
>
>
>
> ⇔ ∇\_𝐰 (1/2 E_D(𝐰)\] + ∇\_𝐰 \[(λ/2) Σj |wj|^q\] = 0
>
>
>
> ⇔ 1/2 ∇\_𝐰 \[E_D(𝐰)\] + (λ/2) ∇\_𝐰 \[ Σj |wj|^q\] = 0 (a)
>
>
>
> Còn bài toàn 2: minimize (3.12) E_D(𝐰) = Σi {(ti-𝐰ᵀΦ(𝐱i))²/2} với ràng buộc (3/30) Σj |wj|^q ≤ η
>
>
>
> Chuyển ràng buộc thành dạng c1(w) ≥ 0: η - Σj |wj|^q ≥ 0
>
>
>
> điều kiện cần của nó chính là KKT ta mới ôn lại:
>
>
>
> Lagrangian: ℒ(𝐰, λ) = E_D(𝐰) - λ\[η - Σj |wj|^q\]
>
>
>
> Stationary conditiion:
>
>
>
> ∇\_𝐰 ℒ(𝐰, λ) = 0 ⇔ ∇\_𝐰 \[E_D(𝐰) - λ\[η - Σj |wj|^q\]\] = 0
>
>
>
> ⇔ ∇\_𝐰 E_D(𝐰) - ∇\_𝐰 λ\[η - Σj |wj|^q\]\] = 0
>
>
>
> ⇔ ∇\_𝐰 E_D(𝐰) - λ ∇\_𝐰 \[η - Σj |wj|^q\]\] = 0
>
>
>
> ⇔ ∇\_𝐰 E_D(𝐰) - λ ∇\_𝐰 \[η\] + λ ∇\_𝐰 \[Σj |wj|^q\] = 0
>
>
>
> ⇔ ∇\_𝐰 E_D(𝐰) - 0 + λ ∇\_𝐰 \[Σj |wj|^q\] = 0 (đạo hàm theo w của constant η dĩ nhiên = 0)
>
>
>
> ⇔ (1/2) ∇\_𝐰 E_D(𝐰) + (1/2) λ ∇\_𝐰 \[Σj |wj|^q\] = 0 (b) (nhân thêm 1/2)
>
>
>
> Tới đây ta thấy nó y chang (a)
>
>
>
> Như vậy điều kiện cần là giống nhau. Và nếu làm thêm bước nữa, chỉ ra rằng cả hai là bài toán lồi thì kết luận luôn là chúng là tương đương, vì với bài toán tối ưu lồi, điều kiện KKT cũng là điều kiện đủ.
>
>
>
> E_D(𝐰) là hàm lồi vì là hàm bậc hai theo w.
>
>
>
> (λ/2) Σj |wj|^q cũng là hàm lồi (nếu q ≥ 1, chứng minh thì hơi dài nên tạm bỏ qua)
>
>
>
> nên objective của bài toán unconstraint là hàm lồi nên nó là bài toán lồi
>
>
>
> còn với bài toán constraint thì objective lồi, constraint cũng lồi nên nó cũng là bài toán lồi.
>
>
>
> ---
>
>
>
> Còn một ý bài tập yêu cầu: Thảo luận quan hệ giữa η và λ:
>
>
>
> Thì ta sẽ dùng complementary condition của bài toán constraint:
>
>
>
> λ\* × \[η - Σj |w\*j|^q\] = 0
>
>
>
> Với quan hệ này:
>
>
>
> nếu λ\* &gt; 0 thì \[η - Σj |w\*j|^q\] phải = 0.
>
>
>
> và λ\* = 0 thì η - Σj |w\*j|^q ≥ 0 ⇔ η ≥ Σj |w\*j|^q
>
>
>
> Và ý nghĩa của nó là:
>
>
>
> Nếu ta tăng hệ số regularization λ, điều này sẽ khiến giảm E_w(𝐰) = Σj |w\*j|^q, và vì η = E_w(𝐰) nên η sẽ giảm.
>
>
>
> Còn nếu ta cho hệ số regularization = 0, tức là không penalized khi 𝐰 lớn, thì E_w(𝐰) có thể sẽ lớn, khiến η với yeu cầu ≥ E_W(𝐰) nên sẽ lớn lên.
>
>
>
> Như vậy quan hệ của λ và η là: λ lớn thì η nhỏ và ngược lại.

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Lời giải rất xuất sắc, không chỉ chứng minh đầy đủ sự tương đương toán học thông qua điều kiện KKT mà còn giải thích trực quan rất sâu sắc về KKT. Phần thảo luận về mối quan hệ nghịch biến giữa ̹Η và ̹Λ cũng hoàn toàn chính xác.

**🔗 See also:** [General Regularizer and Lasso](./314_regularized_least_squares.md#node-1msg8km) · [Likelihood and Error Functions](./311_maximum_likelihood_and_least_squares.md#node-urnjdcs)

<br>

<a id="node-y5iamw4"></a>

#### Ex 3.4 Regularization via Input Noise

<p align="center"><kbd><img src="assets/xlt2gwx6h2.png" width="80%"></kbd></p>

> [!NOTE]
> Cùng làm bài này, trước tiên là dịch sơ cái yêu cầu
>
>
>
> Ở đây gs xét linear model y(𝐱, 𝐰) = w0 + Σi=0:D wixi
>
>
>
> với SSE function ED(𝐰) = (1/2) Σn=1:N {y(𝐱n, 𝐰) - tn}²
>
>
>
> Và cho rằng noise εi \~ N(0, σ²), được add độc lập vào input variable xi.
>
>
>
> Dùng E\[εi\] = 0 (cái này là do nói εi \~ N(0, σ²)) và E\[εi εj\] = δij σ², yêu cầu chỉ ra rằng minimize ED có được khi average out over noise distirbution sẽ tương đương bài toán mininize SSE mà ko có noise, nhưng có thêm regularization weight-decay, với w0 bỏ ra khỏi regularizer.
>
>
>
> ---
>
>
>
> Trước khi làm nên làm rõ vài ý: Khi ông viết 3.105, ông ghi là y(x, 𝐰) = w0 + Σi wi xi. → chỗ gây lú: ông viết nét đậm cho 𝐰, ám chỉ nó là vector, nên dễ hiểu là wi là phần tử thứ i của vector 𝐰. Còn x, nó cũng là vector cơ mà (thể hiện qua Σi=1:D wi xi), sao ổng lại ko viết nét đậm, nên mình tự động viết nét đậm cho thấy 𝐱 là vector.
>
>
>
> Như vậy bộ input sẽ là 𝐱1,𝐱2,..𝐱n...𝐱N. và vector 𝐱n có các phần tử là xn1 xn2,...xnD.
>
>
>
> Tương tự, nhiễu (noise) εi cộng vào mỗi xi (của vector 𝐱) sẽ thì thì hợp lại với mỗi vector 𝐱1,𝐱2,..𝐱n...𝐱N, nó sẽ được cộng một VECTOR **ε**1, **ε**2,...**ε**N. và vector **ε**n có các phần tử là εn1,...εnD.
>
>
>
> Tức là:
>
>
>
> Trước khi có noise: input là 𝐱1 = (x11,x12,..x1D), 𝐱2 = (x21, x22,...x2D) ...
>
>
>
> Sau khi cộng thêm noise: input là 𝐱1 = (x11 + ε11,x12 + ε12,..x1D + ε1D), ...
>
>
>
> Quy ước ở dưới (phòng khi mình quên viết bold / thường):
>
>
>
> 𝐱n vector input thứ n (n =1,...N), và xni là phần tử thứ i của nó 
>
> tương tự và vector noise **ε**n là vector noise add vào input 𝐱n, εni là phần tử thứ i của nó
>
>
>
> ---
>
>
>
> Đọc cái đề bài thì tạm hiểu là vầy:
>
>
>
> Đề bài nói là giả sử thêm noise \~ 𝒩(0, σ²) vào input xi, rồi đi "minimizing E_D average out over noise distribution" thì ta nên hiểu là: "À, có data như vậy, và thiết lập hàm SSE như vậy, thì nay, với viêc xi có thêm noise, nó trở thành một random variable, và ta sẽ tính kì vọng của random variable E_D này, rồi đi minimize nó."
>
>
>
> Cụ thể hơn: Thay 𝐱n bởi 𝐱n + **ε**n, lúc này E_D(𝐰) = (1/2) Σn=1:N \[y(𝐱n + **ε**n, 𝐰) - tn\]² **TRỞ THÀNH RANDOM VARIABLE.**
>
>
>
> (vì sao: Stat110 đã học, bất kì khi nào ta áp một function lên random variable thì ta có một random variable)
>
>
>
> Ta có thể thay kí hiệu là E_D(𝐰, **ε**) để thể hiện giờ nó phụ thuộc **ε** = (ε1,...εN) nữa
>
>
>
> Và **vì nó là random variable ta sẽ lấy expected value của cái random variable** này và đây **cũng chính là động tác average out over noise distribution**.
>
>
>
> E\[E_D(𝐰, **ε**)\] = E\[(1/2) Σn=1:N \[y(𝐱n + **ε**n, 𝐰) - tn\]²\]
>
>
>
> = (1/2) Σn=1:N E\[\[y(𝐱n + **ε**n, 𝐰) - tn\]²\]
>
>
>
> = (1/2) Σn=1:N E\[y(𝐱n + **ε**n, 𝐰)² - 2y(xn + εn, 𝐰)tn + tn²\]
>
>
>
> dùng tính linearity của kì vọng
>
>
>
> = (1/2) Σn=1:N {E\[y(𝐱n + **ε**n, 𝐰)²\] - E\[2y(xn + **ε**n, 𝐰)tn\] + E\[tn²\]}
>
>
>
> = (1/2) Σn=1:N {E\[y(𝐱n + **ε**n, 𝐰)²\] - 2E\[y(xn + **ε**n, 𝐰)\]tn + tn²}
>
>
>
> Với y(𝐱, 𝐰) = w0 + Σi=1:D xi wi
>
>
>
> ⇒ y(𝐱n + **ε**n, 𝐰) = w0 + Σi=1:D (xni + εni) wi)
>
>
>
> = w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)
>
>
>
> = w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)
>
>
>
> ⇒ E\[y(𝐱n + **ε**n, w)\] = E\[w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)\]
>
>
>
> = E\[w0 + Σi=1:D (xni wi)\] + E\[Σi=1:D (εni wi)\]
>
>
>
> w0 + Σi=1:D (xni) là constant, và dùng tính linearity của E\[.\]
>
>
>
> = \[w0 + Σi=1:D (xni wi)\] + Σi=1:D E\[εni wi\]
>
>
>
> = \[w0 + Σi=1:D (xni wi)\] + Σi=1:D (E\[εni\] wi)
>
>
>
> = \[w0 + Σi=1:D (xni wi)\] + Σi=1:D (0 × wi) | do E\[εni\] = 0
>
>
>
> = w0 + Σi=1:D (xni wi)
>
>
>
> = y(𝐰, 𝐱n)
>
>
>
> ---
>
>
>
> \[y(𝐱n + **ε**n, 𝐰)\]² = \[w0 + Σi=1:D (xni + εni) wi\]²
>
>
>
> = \[w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)\]²
>
>
>
> = \[y(𝐰, 𝐱n) + Σi=1:D (εni wi)\]²
>
>
>
> = y(𝐰, 𝐱n)² + 2 y(𝐰, 𝐱n) Σi=1:D (εni wi) + \[Σi=1:D (εni wi)\]²
>
>
>
> ⇒ E{\[y(𝐱n + **ε**n, 𝐰)\]²}
>
>
>
> = E{ y(𝐰, 𝐱n)² + 2 y(𝐰, 𝐱n) Σi=1:D (εni wi) + \[Σi=1:D (εni wi)\]² }
>
>
>
> = E{ y(𝐰, 𝐱n)² } + 2 y(𝐰, 𝐱n) E{ Σi=1:D (εni wi) } + E{ \[Σi=1:D (εni wi)\]² }
>
>
>
> = y(𝐰, 𝐱n)² + 2 y(𝐰, 𝐱n) { Σi=1:D \[E(εni) wi\] } + E{ \[Σi=1:D (εni wi)\]² }
>
>
>
> = y(𝐰, 𝐱n)² + 2 y(𝐰, 𝐱n) { Σi=1:D \[0 × wi\] } + E{ \[Σi=1:D (εni wi)\]² }
>
>
>
> = y(𝐰, 𝐱n)² + 0 + E{ \[Σi=1:D (εni wi)\]² }
>
>
>
> = y(𝐰, 𝐱n)² + E{ \[Σi=1:D (εni wi)\]² }
>
>
>
> ---
>
>
>
> Vậy:
>
>
>
> E\[E_D(𝐰, **ε**)\] = (1/2) Σn=1:N {E\[y(𝐱n + **ε**n, 𝐰)²\] - 2E\[y(𝐱n + **ε**n, 𝐰)\]tn + tn²}
>
>
>
> = (1/2) Σn=1:N { y(𝐰, 𝐱n) + E{ \[Σi=1:D (εni wi)\]² } - 2 y(𝐰, **xn**) tn + tn²}
>
>
>
> = (1/2) Σn=1:N { y(𝐰, 𝐱n) - 2 y(𝐰, **xn**) tn + tn² + E{ \[Σi=1:D (εni wi)\]² } }
>
>
>
> = (1/2) Σn=1:N { \[y(𝐰, 𝐱n) - tn\]² + E{ \[Σi=1:D (εni wi)\]² } }
>
>
>
> = (1/2) Σn=1:N { \[y(𝐰, 𝐱n) - tn\]² } + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]² } }
>
>
>
> = E_D(𝐰) + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]² } }
>
> Như vậy tới đây ta có:
>
>
>
> E\[E_D(𝐰, **ε**)\] = E_D(𝐰) + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]² } }
>
>
>
> ---
>
>
>
> Xét tiếp cái kì vọng trong tổng của cụm thứ hai:
>
>
>
> E{ \[Σi=1:D (εni wi)\]² }
>
>
>
> Xét cái tổng trước và tự hiểu là i chạy từ 1 tới D:
>
>
>
> (Σi (εni wi))²
>
>
>
> Bung cái tổng này ra thì ta sẽ có:
>
>
>
> (εn1 w1)(εn1 w1) + (εn1 w1)(εn2 w2) + ..(εn1 w1)(εnD wD) + (εn2 w2)(εn1 w1) + (εn2 w2)(εn2 w2) + ...(εn2 w2)(εnD wD) + ....
>
>
>
> = Σi (εni wi)² + 2 Σi≠j (εni wi)(εnj wj)
>
>
>
> = Σi εni εni (wi)² + 2 Σi≠j (εni εnj wiwj)
>
>
>
> Lấy kì vọng:
>
>
>
> E { Σi εni εni (wi)² + 2 Σi≠j (εni εnj wiwj) }
>
>
>
> = E\[Σi εni εni (wi)²\] + E\[2 Σi≠j (εni εnj wiwj)\]
>
>
>
> = Σi (wi)² E\[εni εni\] + 2Σi≠j (wiwj) E\[εni εnj\]
>
>
>
> = Σi (wi)² E\[εni εni\] + 2Σi≠j (wiwj) E\[εni εnj\]
>
>
>
> Dùng cái đề bài cho:
>
>
>
> E\[εi εj\] = δij σ² và hàm δij = 1 khi i = j, và = 0 khi i ≠ j ta có
>
>
>
> = Σi (wi)² × (1 × σ²) + 2Σi≠j (wiwj) × (0 × σ²)
>
>
>
> = Σi (wi)² × σ²
>
>
>
> = σ² Σi (wi)²
>
>
>
> ---
>
>
>
> Thay vào E\[E_D(𝐰, **ε**)\] = E_D(𝐰) + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]² } }:
>
>
>
> = E_D(𝐰) + (1/2) Σn=1:N \[σ² Σi (wi)²\]
>
>
>
> = E_D(𝐰) + (N/2) σ² Σi (wi)²
>
>
>
> = E_D(𝐰) + (Nσ²/2) Σi (wi)²
>
>
>
> ---
>
>
>
> Như vậy:
>
>
>
> E\[E_D(𝐰, **ε**)\] = E_D(𝐰) + (Nσ²/2) Σi (wi)²
>
>
>
> và có nghĩa là sao?
>
>
>
> Thì có nghĩa là, nếu ta đi minimize E\[E_D(𝐰, **ε**)\] (đi tìm w để cái này có giá trị nhỏ nhất) thì tức ta sẽ thấy đây tương đương với bài toán minimize hàm error sau đây,
>
>
>
> Error function = E_D(𝐰) + λ Σi (wi)² , λ = Nσ²/2
>
>
>
> thì cái này chính là bài toán minimize sum square error (là cái E_D(w) đó) có thẹm L2 regularization (là cái Σi (wi)², chính là ||𝐰||²) với regularization coefficient là Nσ²/2.
>
>
>
> Nói chung tóm lại, bài này chỉ là:
>
>
>
> Ta có hàm SSE E_D(𝐰) = (1/2) Σi=1:N {y(**xi**, 𝐰) - ti}²
>
>
>
> Xong ta thay **xi** = 𝐱i + **ε**i vì đề nói ta add noise εi vào
>
>
>
> Lúc này cái E_D(𝐰), trở thành random variable: E_D(**w, ε**)
>
>
>
> Ta mới đi tính kì vọng của cái random variable này (tính kì vọng, theo định nghĩa, chính là lấy trung bình dựa trên distribution)
>
>
>
> Dùng tính tuyến tính của kì vọng nhiều lần, tuy dài nhưng cơ bản chỉ là xoay quanh tính tuyến tính, nói rằng nếu X là random variable, α, β là constant thì E\[αX + β\] = αEX + β
>
>
>
> Và khi làm dù là rất nhiều term nhưng chỉ có cái nào dính tới ε thì nó mới là random variable, còn lại là constant hết.
>
>
>
> Kết quả khi ra được tới E\[εni εni\] và E\[εni εnj\] thì dùng cái đề bài cho: E\[εi εj\] = δij σ². Và δij là kí hiệu của hàm Kronecker, = 1 khi i = j, và = 0 khi i khác j gs Bishop không nói.
>
>
>
> Và kết qủa sẽ thấy quả nhiên nó đúng là cái loss function có L2 regularization.
>
>
>
> ---
>
>
>
> Phần dưới là mình active recall chút, ko liên quan bài tập, nhưng giúp hiểu sâu hơn
>
>
>
> Mình hiểu thế này: Bài toán ban đầu là ta có bộ data set (x1, t1), (x2,t2) ...(xN, tN), hay đặt các vector x1,..xN vào vector 𝐱, và đặt t1,...tN vào vector 𝐭. Thì ta thể hiện observed data bởi (𝐱, 𝐭).
>
>
>
> Và với việc coi target variable là random variable (còn input thì không), thì 𝐭 chính là observed value của random sample 𝐓 = (T1, T2,...TN).
>
>
>
> Như vậy, (y(x, 𝐰) - T)² là hàm số của random variable T, nên dĩ nhiên cũng là random variable.
>
>
>
> Và vì nó là random variable, ta có thể đặt vấn đề xét trung bình của nó, tức expected value:
>
>
>
> E\[(y(x, 𝐰) - T)²\]
>
>
>
> Thế thì tuy ta đang giả định y(x, 𝐰) - T \~ n(0, 1/β), nhưng \[y(x, 𝐰) - T\]² thì ta không biết là phân phối gì. Nên không thể tính E\[(y(x, 𝐰) - T)²\], để ra một hàm theo 𝐰, từ đó đi minimize over 𝐰 cái này.
>
>
>
> Thay vì vậy, ta xem S = (y(x, 𝐰) - T) đến từ một uniform discrete distriution có các discrete value là s1 = y(x1, 𝐰) - t1,..., sN = y(xN, 𝐰) - tN.
>
>
>
> Từ đó, E\[(y(x, 𝐰) - T)²\] có thể tính cái này nhờ LOTUS
>
>
>
> = Σn=1:N \[y(xn, 𝐰) - tn\]² P(S = sn)
>
>
>
> = (1/N) Σn=1:N \[y(𝐱n, 𝐰) - tn\]²
>
>
>
> Và từ đó ta đi minimize over 𝐰 hàm objective E\[(y(𝐱, 𝐰) - T)²\] = (1/N) Σn=1:N \[y(xn, 𝐰) - tn\]²
>
>
>
> và với N là constant thì bài toán này cũng tương đương minimize (1/2) Σn=1:N \[y(xn, 𝐰) - tn\]² và đây chính là sum-of-squares error E_D(𝐰)
>
>
>
> Cách lập luận này giúp ta có cái nhìn sâu hơn vào bản chất của cái hàm SSE để thấy nó chính là kì vọng của S = \[y(𝐰, x) - T\]² với S là uniform discrete với N posible value s1,...sN.
>
>
>
> ---
>
>
>
> Góc nhìn thứ hai là maximum likelihood.
>
>
>
> Đó là ta xét một khái niệm trong statistic gọi là likelihood, định nghĩa của nó là hàm của tham số (ở đây là 𝐰), thể hiện độ hợp lí của tham số khi dữ liệu quan sát có giá trị (observed data) ta đã thấy, kí hiệu L(𝐰|observed data), Ở đây observed data chính là \[𝐱1,...𝐱N\], (t1,...tN). Và giá trị của nó tính bằng xác suất của event data mang giá trị observed data dựa trên 𝐰:
>
>
>
> L(𝐰|observed data) = f(observed data|𝐰)
>
>
>
> Cụ thể ở đây L(𝐰|\[𝐱1,...𝐱N\], (t1,...tN)) = P(data = \[𝐱1,...𝐱N\], (t1,...tN)|𝐰)
>
>
>
> với bài toán này ta chỉ coi T là random variable, thì:
>
>
>
> f(data = \[𝐱1,...𝐱N\], (t1,...tN)|𝐰) = P(T1,...TN = (t1,...tN)|**w,** \[𝐱1,...𝐱N\])
>
>
>
> đặt 𝐓 là vector (T1,...TN), matrix 𝐗 matrix có các hàng là (𝐱1)ᵀ,...(𝐱N)ᵀ thì và f là pdf của của T, cũng là joint pdf của T1,...TN
>
>
>
> L(𝐰|observed data) = f(𝐭|𝐰, 𝐗).
>
>
>
> Và cách làm / phương pháp nổi tiếng của Frequentist statistic, khi đi giải tìm point estimate cho w, chính là đi maximize cái hàm độ hợp lí này. Ta có bài toán:
>
>
>
> maximize (over 𝐰) f(𝐭|𝐰, 𝐗)
>
>
>
> Dùng tính iid f(𝐭|𝐰, 𝐗) = Πn=1:N f(tn|𝐰, **xn**), bài toán trở thành.
>
>
>
> maximize (over 𝐰) Πn=1:N f(tn|𝐰, **xn**)
>
>
>
> Và với bài toán tối ưu, ta có thể dùng hàm monotone để chuyển về bài toán tương đương dễ giải hơn và nghiệm của chúng giúp suy ra nghiệm của nhau (hoặc cùng nghiệm), cụ thể ta dùng ln, bài toán tương đương:
>
>
>
> maximize (over 𝐰) ln \[Πn=1:N f(tn|𝐰, **xn**)\]
>
>
>
> Biến đổi hàm mục tiêu: ln \[Πn=1:N f(tn|𝐰, **xn**)\] = Σn=1:N \[ln f(tn|𝐰, **xn**)\]
>
>
>
> và thay pdf của Tn vô, dùng giả định là Tn \~ 𝒩(y(𝐱n, 𝐰), 1/β),
>
>
>
> f(tn|w, xn) = \[constant c, là term dính tới β\] exp {-(tn - y(𝐱n, 𝐰))²/2(1/β)},
>
>
>
> hàm mục tiêu trở thành:
>
>
>
> Σn \[ln (c exp {-(tn - y(𝐱n, 𝐰))²/2(1/β) } \]
>
>
>
> = Σn \[ln c + ln exp {-(tn - y(𝐱n, 𝐰))²/2(1/β)} \]
>
>
>
> = Σn \[ln c\] + Σn ln exp {-(tn - y(𝐱n, 𝐰))²/2(1/β)}
>
>
>
> = Σn \[ln c\] + Σn {-(tn - y(𝐱n, 𝐰))²/2(1/β)}
>
>
>
> Tiếp tục chuyển thành bài toán tương đương bằng cách bỏ các constant (Σn \[ln c\] và β (là số dương) ta có:
>
>
>
>  maximize\_𝐰 Σn {-(tn - y(𝐱n, 𝐰))²/2(1/β) }
>
>
>
>  maximize\_𝐰 (-1/2) Σn (tn - y(𝐱n, 𝐰))²
>
>
>
> again, chuyển thành bài toán tối ưu tương đương bởi nguyên kí: maximize f ≡ minimize -f
>
>
>
> minimize \_𝐰 (1/2) Σn(tn - y(𝐱n, 𝐰))²
>
>
>
> Và đây chính là bài toán minimize Sum Of Square.

---

🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on

Bài viết trình bày lời giải vô cùng chi tiết, chính xác và có tư duy ký hiệu rất mạch lạc khi phân biệt rõ vector và scalar. Các phần mở rộng liên hệ với LOTUS và Maximum Likelihood thể hiện sự hiểu biết sâu sắc và toàn diện về bản chất toán học của bài toán.

<br>

<a id="node-cq8t94f"></a>

##### Ex 3.6  MLE Hồi quy Đa biến

<p align="center"><kbd><img src="assets/orzwo0hrgqn.png" width="80%"></kbd></p>

> [!NOTE]
> Giải nhanh bài này, bài này là bối cảnh bài toán dự đoán (từ một input vector 𝐱) ra nhiều target value, có nghĩa là ta sẽ có 𝐭 = y(𝐱) là vector.
>
>
>
> Quy ước: Xuyên suốt repo này để khỏi gõ Latext rườm ra, mình gõ thường và quy ước nhau T nếu đứng sau matrix 𝐖 tự hiểu là **"W** **tranpose"**. Còn 𝐓, hay T1, T2,...là chỉ random variable
>
>
>
> Đề bài nói rằng là ta sẽ vẫn dựa trên giả định: 𝐓 \~ f(𝐭|𝐖, **Σ**) = 𝒩(𝐭|y(𝐖,𝐱), **Σ**) với y(𝐖,𝐱) = 𝐖TΦ(𝐱).
>
>
>
> Đi tìm MLE của 𝐖
>
>
>
> Đầu tiên nên nói vài lời liên hệ với bài toán point estimation của Statistical Inference Casella để: Trong chapter 9, ta học về point estimation, với vấn đề đặt ra là, giả sử ta có một observed value 𝐱 của random sample 𝐗 = (X1,..Xn) với Xi \~ f(x|θ), làm sao để estimate θ. Đây gọi là bài toán point estimation, vì nhiệm vụ là đi xây dựng một hàm số của sample W(𝐗) (gọi là estimator) để lắp giá trị quan sát được của 𝐗 vào thì ta có W(𝐱) là estimate cho θ.
>
>
>
> Vậy thì theo định nghĩa của estimator, bất cứ cái hàm nào của sample cũng có thể dùng, nhưng tốt hay không thì chưa chắc. Do đó, trong sách Casella dạy ta về 3 loại: Method of Moment estimator, Maximum Likelihood estimator và Bayes estimator.
>
>
>
> Thế thì như định nghĩa, estimator W(𝐗) đơn giản chỉ là một function của sample 𝐗, vậy ML estimator là function gì? Câu trả lời là function này: argmax\_Θ L(θ|𝐗). ý nghĩa: Nhận input 𝐗, tìm θ ∈ Θ (parameter space) sao cho L(θ|𝐗) đạt giá trị max thì trả ra. Đồng nghĩa, estimator này là nghiệm của bài toán tối ưu: maximize (over θ ∈ Θ) L(θ|𝐗). Và ta thấy, đây vẫn chỉ là một hàm số của 𝐗 (nhận vào 𝐗, tìm θ sao cho maximize L, trả θ đó ra)
>
>
>
> Vậy L(θ|𝐗) là gì. Theo định nghĩa, người ta đặt ra hàm L(θ|𝐱), là hàm của θ (tức input là θ) mang ý nghĩa là: với θ đưa vào, thì dựa trên data quan sát được thấy 𝐗 = 𝐱 thì độ hợp lí của θ là bao nhiêu. Ví dụ, L(θ=3|𝐱=(1,2)) = α sẽ được hiểu là dựa trên việc ta thấy x = (1,2) thì độ hợp lí của θ = 3 là α, với θ = 4 thì có thể độ hợp lí cao hơn. Và ta muốn tìm θ có độ hợp lí cao nhất.
>
>
>
> Và đó là ý nghĩa của độ hợp lí, còn giá trị của nó, thì người ta đặt (vì họ định nghĩa nên họ có quyền) là bằng f(𝐱|θ). Là sao? Có nghĩa là độ hợp lý của θ dựa trên quan sát 𝐗=𝐱 sẽ bằng giá trị của joint pdf của 𝐗 tại observed data 𝐱.
>
>
>
> Thành ra bài toán tìm θ^ML sẽ là maximize\_θ f(𝐱|θ). Và với tính iid, các random sample X1,..Xn đều mutually independent, và identically distributed, tức là có cùng distributoin. Thành ra f(𝐱|θ) có thể tách thành tích các marginal pdf (y như X, Y độc lập thì fX,Y(x,y) = fX(x) fY(y) và fX, fY lại là cùng một hàm pdf): f(𝐱|θ) = Πi=1:n f(xi|θ)
>
>
>
> Vậy quay lại bài toán này, ta cơ bản ta đang giả định rằng, ra có một random sample (𝐓1, 𝐗1), (𝐓2, 𝐗2),...(𝐓N, 𝐗N) có observed data là (𝐭1, 𝐱1), (𝐭2, 𝐱2)...(𝐭N, 𝐱N), và (𝐓i, 𝐗i) tuân theo một population distribution f(𝐭,𝐱|θ) nào đó. Và ta sẽ đi giải bài toán point estimate θ.
>
>
>
> Tuy nhiên, với bối cảnh ta cần đưa ra hàm dự đoán t từ một input x đã biết chứ không phải là đi xây một generative model giúp sampling ra các giá trị t,X mới, nó sẽ là bài toán khác. Nên ta sẽ COI 𝐗 NHƯ FIX, VÀ chỉ coi T là random variable thôi. Nên bài toán trở thành ta có random sample sẽ là 𝐓|𝐱1,..𝐱N = 𝐓1|𝐱1, 𝐓2|𝐱2,....𝐓n|𝐱n có observed data là 𝐭|𝐱1,..𝐱N = 𝐭1|𝐱1,...𝐭N|𝐱N. Đeo theo 𝐱 chỉ là thể hiện sự phụ thuộc của 𝐭 vào từng 𝐱, chứ không có gì phức tạp cứ coi như ta có random sample 𝐓 = (𝐓1,...𝐓n) với observed data 𝐭 = (𝐭1,....𝐭n) (cho giống setup của bài toán thống kê suy luận ở trên, để ta thấy cách làm thật ra là y như nhau, nhờ đó thấy bài toán machine learning này chỉ là bài toán point estimation của statistial inference)
>
>
>
> (điểm chú ý là vì 𝐓1,...𝐓N ở đây là random vector, nên khi gom chúng lại, thì 𝐓 là một random matrix, nhưng cũng ko quan trọng)
>
>
>
> Điểm thứ hai, với bài toán inference ra θ, ta phải giả định f(x|θ) là (pdf/pmf) của phân phối gì. thì đó mới có hàm f mà xài. Ví dụ ta giả định f là normal pdf, thì θ là μ, σ² và f(x|θ) = (1/√2πσ²) exp(-(x-μ)²/2σ²), để mà hình dạng (công thức) của hàm likelihood. Thì ở đây cũng vậy, ta sẽ giả định dạng của để bài toán trở nên khả thi, ta phải đặt ra giả định của phân phối T. Và giả định đó chính là: 𝐓 \~ f(𝐭|𝐖, **Σ**) = 𝒩(𝐭|y(𝐖,𝐱), **Σ**) với y(𝐖,𝐱) = 𝐖TΦ(𝐱)
>
>
>
> Và như vậy bài toán cứ theo phương pháp của bài toán statistical inference nói ở trên mà làm thôi:
>
>
>
> θ của f(x|θ) ở đây tương ứng với cặp matrix 𝐖, **Σ**.
>
>
>
> observed data 𝐱 thì ở đây chính là giá trị của (𝐭1 𝐱1), (𝐭2, 𝐱2),....(𝐭N, 𝐱N)
>
>
>
> Và θ^ML là solution của bài toán maximize L(θ|𝐱) = f(𝐱|θ) = Πi=1:N f(xi|θ)
>
>
>
> thì ở đây tương ứng với:
>
>
>
> 𝐖^\_ML, **Σ**^\_ML sẽ là solution của bài toán maximize L(𝐖, **Σ**|(𝐭1 𝐱1), (𝐭2, 𝐱2),....(𝐭N, 𝐱N))
>
>
>
> = f(𝐭1, 𝐭2,...,𝐭N | 𝐖, **Σ**, 𝐱1,..𝐱N)
>
>
>
> Và cũng vì 𝐓1,...𝐓N iid nên join pdf của chúng cũng tách thành tích marginal pdf:
>
>
>
> .. = Πi=1:N f(𝐭i | 𝐖, **Σ**, 𝐱i)
>
>
>
> Vậy bài toán tối ưu cần giải là:
>
>
>
> maximize (over 𝐖, **Σ**) {Πi=1:N f(𝐭i | 𝐖, **Σ**, 𝐱i)}
>
>
>
> ---
>
>
>
> Và để giải bài toán tối ưu, một cách ta luôn làm là dùng hàm monotone để chuyển bài toán thành tương đương dễ giải hơn, để giải bài này sẽ suy ra nghiệm bài gốc. ở đây ta dùng hàm ln: bài toàn tương đương là maximize ln likelihood:
>
>
>
> maximize (over 𝐖, **Σ**) **ln** {Πi=1:N f(𝐭i | 𝐖, **Σ**, 𝐱i)}
>
>
>
> Xét hàm objective, dùng tính chát hàm ln: ln của tích = tổng của ln:
>
>
>
> ln {Πi=1:N f(𝐭i | 𝐖, **Σ**, 𝐱i)} = Σi=1:N ln {f(𝐭i | 𝐖, **Σ**, 𝐱i)}
>
>
>
> đổi sang biến chạy là n và tự hiểu n chạy từ 1 tới N cho gọn
>
>
>
> Σn ln {f(𝐭n | 𝐖, **Σ**, 𝐱n)}
>
>
>
> bỏ pdf của 𝐭 vô: f(𝐭n | 𝐖, **Σ**, 𝐱n) = 𝒩(𝐭| 𝐖TΦ(𝐱), **Σ**)
>
>
>
> (Xem link tới note của phần nói về pdf hàm D-dimensional normal)
>
>
>
> = \[(2π)^-D/2\] \[1/|**Σ**|^1/2\] exp\[-(𝐭 - 𝐖TΦ(𝐱))ᵀ **Σ**inv (𝐭 - **μ**)/2\]
>
>
>
> Đặt \[(2π)^-D/2\] là c1 cho gọn,
>
>
>
> Ta có:
>
>
>
> Σn ln { f(𝐭n | 𝐖, **Σ**, 𝐱n) }
>
>
>
> = Σn ln { c1 \[1/|**Σ**|^1/2\] exp\[-(𝐭n - 𝐖TΦ(𝐱n))ᵀ **Σ**inv (𝐭n - 𝐖TΦ(𝐱n))/2\] }
>
>
>
> = Σn ( ln c1 + ln \[|**Σ**|^-1/2\] + ln exp\[-(𝐭n - 𝐖TΦ(𝐱n))ᵀ **Σ**inv (𝐭n - 𝐖TΦ(𝐱n))/2\] } )
>
>
>
> = N ln c1 + Σn (-1/2 ln |**Σ**|) - Σn \[ (𝐭n - 𝐖TΦ(𝐱n))ᵀ **Σ**inv (𝐭n - 𝐖TΦ(𝐱n))/2 \]
>
>
>
> = N ln c1 - (N/2) ln |**Σ**| - (1/2) Σn (𝐭n - 𝐖TΦ(𝐱n))ᵀ **Σ**inv (𝐭n - 𝐖TΦ(𝐱n)
>
>
>
> Tiếp tục chuyển thành bài toán tương đương bằng cách bỏ constant
>
>
>
> = - (N/2) ln |**Σ**| - (1/2) Σn (𝐭n - 𝐖TΦ(𝐱n))ᵀ **Σ**inv (𝐭n - 𝐖TΦ(𝐱n)
>
>
>
> Tới đây, bài toán là maximize {-(N/2) ln |**Σ**| - (1/2) Σn (𝐭n - 𝐖TΦ(𝐱n))ᵀ **Σ**inv (𝐭n - 𝐖TΦ(𝐱n) }
>
>
>
> Với bài toán tối ưu, ta có thể giải theo từng biến, tức maximize over 𝐖 trước để tìm 𝐖\_ML và khi làm vậy ta coi **Σ** như constant. Do đó lại tiếp tục bỏ constant đi
>
>
>
> maximize\_𝐖 {-(1/2) Σn (𝐭n - 𝐖TΦ(𝐱n))ᵀ **Σ**inv (𝐭n - 𝐖TΦ(𝐱n) }
>
>
>
> Biến đổi hàm objective, để cho gọn 𝐀 = 𝐖TΦ(𝐱n) ⇒ 𝐀T = Φ(𝐱n)ᵀ𝐖, 𝐁 = **Σ**inv
>
>
>
> \-(1/2) Σn (𝐭n - 𝐀)ᵀ 𝐁 (𝐭n -𝐀) = -(1/2)\[(𝐭n)ᵀ𝐁 - 𝐀T𝐁)(𝐭n -𝐀)\]
>
>
>
> = -(1/2) Σn \[(𝐭n)ᵀ**Bt**n - 𝐀T**Bt**n - (𝐭n)ᵀ**BA** + 𝐀T**BA**\]
>
>
>
> 𝐀T**Bt**n là scalar, nên = \[𝐀T**Bt**n\]ᵀ = (𝐭n)ᵀ𝐁T𝐀, và vì 𝐁 là **Σ**inv, nên nó đối xứng do covariance matrix đối xứng và nghịch đảo của matrix đối xứng cũng đối xứng nên .. = (𝐭n)ᵀ**BA**
>
>
>
> = -(1/2) Σn \[(𝐭n)ᵀ**Bt**n - **2**(𝐭n)ᵀ**BA** + 𝐀T**BA**\]
>
>
>
> = -(1/2) Σn \[𝐀T**BA** - **2**(𝐭n)ᵀ**BA** + (𝐭n)ᵀ**Bt**n\]
>
>
>
>  Thay 𝐀, 𝐁 vào lại:
>
>
>
> = -(1/2) Σn \[Φ(𝐱n)ᵀ **W Σ**inv 𝐖T Φ(𝐱n) - **2**(𝐭n)ᵀ **Σ**inv 𝐖T Φ(𝐱n) + (𝐭n)ᵀ **Σ**inv 𝐭n\]
>
>
>
> (nhớ quy ước T ở đây đều là 'tranpose', không phải biến T gì đâu, và Σ đầu là tổng, **Σ** đậm mà matrix **Σ**)
>
>
>
> = -(1/2) Σn \[Φ(𝐱n)ᵀ **W Σ**inv 𝐖T Φ(𝐱n) - **2**(𝐭n)ᵀ **Σ**inv 𝐖T Φ(𝐱n) + (𝐭n)ᵀ **Σ**inv 𝐭n\]
>
>
>
> ---
>
>
>
> Nhiệm vụ bây giờ là dùng điều kiện tối ưu bậc nhất để cho stationary point: Cho đạo hàm theo 𝐖 của hàm trên = 0
>
>
>
> Để tìm đạo hàm đối với matrix 𝐖 của hàm objective dài thòn này, là sao đây?
>
>
>
> Để cho gọn mắt, ta lại mượn các kí hiệu 𝐀, 𝐁, 𝐮, 𝐯, 𝐳 để ta xét hàm sau đây: f(𝐀) = 𝐮ᵀ 𝐀 𝐁 𝐀T 𝐮 - 2 𝐯ᵀ 𝐁 𝐀T 𝐳
>
>
>
> Giải tìm ∇f theo cách làm đã học trong MIT 18s096: Cố gắng đưa df thành dạng linear operator act on d𝐀:
>
>
>
> df = 𝐮ᵀ (𝐀 + d𝐀) 𝐁 (𝐀 + d𝐀)ᵀ 𝐮 - 2 𝐯ᵀ 𝐁 (𝐀 + d𝐀)ᵀ 𝐳 - \[𝐮ᵀ 𝐀 𝐁 𝐀T 𝐮 - 2 𝐯ᵀ **B A\*\*ᵀ 𝐳 \]
>
>
>
> = 𝐮ᵀ (**A B** + d**A B**) \[𝐀T + (d𝐀)ᵀ\] 𝐮 - 2 𝐯ᵀ 𝐁 \[𝐀T + (d𝐀)ᵀ\] 𝐳 - 𝐮ᵀ 𝐀 𝐁 𝐀T 𝐮 + 2 𝐯ᵀ **B A\*\*ᵀ 𝐳
>
>
>
> = (𝐮ᵀ **A B** + 𝐮ᵀ d**A B**) \[𝐀T 𝐮 + (d𝐀)ᵀ 𝐮\] - 2 𝐯ᵀ **B A\*\*ᵀ 𝐳 - 2 𝐯ᵀ 𝐁 (d𝐀)ᵀ 𝐳 - 𝐮ᵀ 𝐀 𝐁 𝐀T 𝐮 + 2 𝐯ᵀ **B A\*\*ᵀ 𝐳
>
>
>
> = 𝐮ᵀ **A B A\*\*ᵀ 𝐮 + 𝐮ᵀ d**A B A\*\*ᵀ 𝐮 + 𝐮ᵀ **A B** (d𝐀)ᵀ 𝐮 + 𝐮ᵀ d**A B** (d𝐀)ᵀ 𝐮 - 2 𝐯ᵀ **B A\*\*ᵀ 𝐳 - 2 𝐯ᵀ 𝐁 (d𝐀)ᵀ 𝐳 - 𝐮ᵀ 𝐀 𝐁 𝐀T 𝐮 + 2 𝐯ᵀ **B A\*\*ᵀ 𝐳
>
>
>
> Cancel out, và bỏ đi term bậc cao 𝐮ᵀ d**A B** (d𝐀)ᵀ 𝐮
>
>
>
> = 𝐮ᵀ d**A B A\*\*ᵀ 𝐮 + 𝐮ᵀ **A B** (d𝐀)ᵀ 𝐮 - 2 𝐯ᵀ 𝐁 (d𝐀)ᵀ 𝐳
>
>
>
> hai cái term đầu là scalar, và transpose cái đầu sẽ ra cái sau
>
>
>
> = 2 𝐮ᵀ **A B** (d𝐀)ᵀ 𝐮 - 2 𝐯ᵀ 𝐁 (d𝐀)ᵀ 𝐳
>
>
>
> = 2 𝐮ᵀ **A B** (d𝐀)ᵀ 𝐮 - 2 𝐯ᵀ 𝐁 (d𝐀)ᵀ 𝐳
>
>
>
> Tới đây nhận thấy cả term cuối cũng là scalar, nên nguyên cụm df trên cái trên là scalar, và với scalar α thì α = trace(α), nên ta có df =:
>
>
>
> tr\[2 𝐮ᵀ **A B** (d𝐀)ᵀ 𝐮 - 2 𝐯ᵀ 𝐁 (d𝐀)ᵀ 𝐳\]
>
>
>
> dùng tính tuyến tính của trace
>
>
>
> = tr\[2 𝐮ᵀ **A B** (d𝐀)ᵀ 𝐮\] - tr\[2 𝐯ᵀ 𝐁 (d𝐀)ᵀ 𝐳\]
>
>
>
> Dùng tính xoay vòng của trace
>
>
>
> = tr\[2 **uu\*\*ᵀ **A B** (d𝐀)ᵀ\] - tr\[2 **zv\*\*ᵀ 𝐁 (d𝐀)ᵀ \]
>
>
>
> = tr\[2 **uu\*\*ᵀ **A B** (d𝐀)ᵀ - 2 **zv\*\*ᵀ 𝐁 (d𝐀)ᵀ \]
>
>
>
> = tr\[2 (**uu\*\*ᵀ **A B** - **zv\*\*ᵀ 𝐁) (d𝐀)ᵀ \]
>
>
>
> Dùng tính chất trace(𝐗) = tr(𝐗T)
>
>
>
> = tr\[2 (d𝐀) (**uu\*\*ᵀ **A B** - **zv\*\*ᵀ 𝐁)ᵀ\]
>
>
>
> lại dùng tính xoay vòng
>
>
>
> = tr\[2 (**uu\*\*ᵀ **A B** - **zv\*\*ᵀ 𝐁)ᵀ (d𝐀)\]
>
>
>
> Tới đây dùng kiến thức tr(𝐗T 𝐘) chính là 𝐗 . 𝐘 (inner product của hai matrix X và Y) (xem link tới bài giảng của MIT 18s096) do đó ở trên chính là
>
>
>
> 2(**uu\*\*ᵀ **A B** - **zv\*\*ᵀ 𝐁) . (d𝐀)
>
>
>
> Và đây inner product của chính là linear operator, nên kết quả này chính là một linear operator act on d𝐀, giúp cho phép kết luận ∇f = -(1/2) Σn 2 (**uu\*\*ᵀ **A B** - **zv\*\*ᵀ 𝐁) = - Σn (**uu\*\*ᵀ **A B** - **zv\*\*ᵀ 𝐁)
>
>
>
> ---
>
>
>
> Áp dụng kết quả này, gradient của objective là:
>
>
>
> \- Σn (**uu\*\*ᵀ **A B** - **zv\*\*ᵀ 𝐁)  
>
>
>
> Thay 𝐮 = Φ(𝐱n), 𝐀 = 𝐖, 𝐁 = **Σ**inv, 𝐳 = Φ(𝐱n), 𝐯 = 𝐭n
>
>
>
> \- Σn (Φ(𝐱n) Φ(𝐱n)ᵀ **W Σ**inv - Φ(𝐱n) (𝐭n)ᵀ **Σ**inv)   
>
>
>
> Cho bằng 0: Σn (Φ(𝐱n) Φ(𝐱n)ᵀ **W Σ**inv - Φ(𝐱n) (𝐭n)ᵀ **Σ**inv) = 0
>
>
>
> ⇔ Σn Φ(𝐱n) Φ(𝐱n)ᵀ **W Σ**inv = Σn Φ(𝐱n) (𝐭n)ᵀ **Σ**inv
>
>
>
> ⇔ \[ Σn Φ(𝐱n) Φ(𝐱n)ᵀ \] **W Σ**inv = \[Σn Φ(𝐱n) (𝐭n)ᵀ\] **Σ**inv
>
>
>
> ⇔ \[ Σn Φ(𝐱n) Φ(𝐱n)ᵀ \] 𝐖 = \[Σn Φ(𝐱n) (𝐭n)ᵀ\]
>
>
>
> ⇔ 𝐖 = \[Σn Φ(𝐱n) Φ(𝐱n)ᵀ\]⁻¹ \[Σn Φ(𝐱n) (𝐭n)ᵀ\]
>
> Đây chính là 𝐖\_ML
>
>
>
> ---
>
>
>
> So với kết quả 3.15, 𝐰ML = (**Φ𝐓Φ**)⁻¹ **Φ𝐓t**
>
>
>
> Hiểu như sau, còn nhớ trong MIT 18.06, trong 4 góc nhìn nhân matrix AB, góc nhìn thứ 4 là ta coi AB là tổng các rank 1 matrix tạo bởi cột i của A và hàng i của B: Σi \[cột i của A\] outer product \[hàng i của B\], giúp ta nhìn ra **Φ𝐓Φ cũng chính là** Σn Φ(𝐱n) Φ(𝐱n)ᵀ, vì design matrix được define là các hành của nó chính là Φ(𝐱1)ᵀ, Φ(𝐱2)ᵀ,..., nên các cột của **Φ\*\*ᵀ chính là Φ(𝐱1), Φ(𝐱2).
>
>
>
> Như vậy 𝐖 = (**Φ𝐓Φ**)⁻¹ \[Σn Φ(𝐱n) (𝐭n)ᵀ\]
>
>
>
> Lại dùng góc nhìn đó ta thấy Σn Φ(𝐱n) (𝐭n)ᵀ chính là **Φ\*\*ᵀ \[matrix có các hàng là (𝐭1)ᵀ,...(𝐭N)ᵀ\]
>
>
>
> Đặt matrix có các hàng là (𝐭1)ᵀ,...(𝐭N)ᵀ là matrix 𝐇, thì ta có: 
>
>
>
> 𝐖\_ML = (**Φ𝐓Φ**)⁻¹ **Φ\*\*ᵀ 𝐇, có thể thấy nó giống (**Φ𝐓Φ**)⁻¹ **Φ𝐓t**, chỉ là thay matrix 𝐇 bởi 𝐭 
>
>
>
> Tới đây coi như giải xong phần 1, tính MLE của 𝐌

---

🤖 **AI Check** — 🟢 Pass — ⚠️ **85/100** · ✓ Move on

Bài viết rất xuất sắc và chi tiết trong việc giải thích bản chất thống kê cũng như biến đổi vi phân ma trận cực kỳ chuẩn xác để tìm ra W_ML. Tuy nhiên, bạn mới chỉ hoàn thành phần 1 mà chưa giải quyết yêu cầu thứ hai của đề bài là chứng minh công thức ước lượng MLE cho ma trận hiệp biến Γ.

**🔗 See also:** [Maximum Likelihood and Gradient](./311_maximum_likelihood_and_least_squares.md#node-ogc31vz) · [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj) · [linked note *(MIT 18S096 Matrix Calculus for ML)*](../mit_18s096_matrix_calculus_for_ml/lec_4_part_1_gradient_and_inner_products_in_other_vector_spaces.md#node-pkow4ed)

<br>

<a id="node-97teyoh"></a>

###### Ex 3.7 Posterior Distribution in Linear Basis Models

<p align="center"><kbd><img src="assets/4a3ntypxntu.png" width="80%"></kbd></p>

> [!NOTE]
> Ok, bài 3.7 là cơ hội để mình luyện tập kĩ thuật gọi là "completing the square" lần nữa.
>
>
>
> Đề bài muốn ta dùng kĩ thuật này để verify (xác nhận) kết quả 3.49 là f(𝐰|𝐭) = 𝒩(𝐰|𝐦N, 𝐒N) với (3.50) 𝐦N = 𝐒N{𝐒0inv 𝐦0 + β**Φ**ᵀ𝐭} và (3.51) 𝐒N⁻¹ = 𝐒0inv + β**Φ**ᵀ**Φ**
>
>
>
> Ôn lại chút xíu bối cảnh bài toán này cũng như completing the square là cái gì?
>
>
>
> Đại ý thế này, bài này là trong bối cảnh là ta đang đi tìm 𝐰, tham số của mô hình T \~ 𝒩(y(𝐰,𝐱), 1/β) theo Bayesian approach trong đó ta coi 𝐰 như random variable (vector), với prior distribution f(𝐰), mà ta sẽ chọn dựa trên niềm tin ban đầu về phân phối của 𝐰 để sau đó dùng Bayes theorem giúp ta có f(𝐰|data) gọi là posterior distribution. Rồi từ cái distribution này, ta sẽ có thể dùng các cách làm nào đó để đưa ra ước lượng điểm của 𝐰
>
>
>
> Hiểu thế này: Ước lượng điểm là gì, là một hàm số mà bỏ giá trị data vào, thì ta có được giá trị ước lượng của vector tham số 𝐰. Thế thì khi ta có posterior distribution, thì nó là cái probability distribution, nói như giáo sư Joe Blizstein của Stat110, thì nó là một bản thiết kế (blueprint) cho ta biết với giá trị này thì xác suất 𝐰 mang giá trị nào là bao nhiêu, với giá trị kia thì xác suất là bao nhiêu. Nên để từ cái posterior distribution, muốn cho ra một point estimation, ta có thể dùng giá trị của 𝐰 có probability cao nhất, và có khi nó là mean của distribution, nhưng cũng có khi dùng median của distribution thì tốt hơn. Nên cái lí thuyết gọi là decision theory sẽ giúp ta đưa ra ước lượng điểm tối ưu dựa trên posterior distribution.
>
>
>
> Quay lại đây, lại nói về prior, thì như đã nói, ta chọn theo niềm tin ban đầu, nhưng bên cạnh đó, người ta cũng chọn những loại distribution có tính conjugate prior với loại distribution của likelihood, vì khi đó, khi ta derive ra posterior sẽ thấy nó cũng cùng chung một loại với prior, từ đó thuận lợi hơn trong tính toán.
>
>
>
> Và bài này cơ bản là ta có prior là 𝐰 \~ 𝒩(𝐦0, 𝐒0) và likelihood (tức L(𝐰|data), mà theo định nghĩa cũng chính là hàm joint pdf của data f(data|𝐰)) là cũng là normal, mà normal lại là conjigate prior của chính nó, nên posterior sẽ cũng ra là normal, và cái ta cần làm là dùng completing square để chứng minh cái posterior normal có mean và covariance như 3.50, 3.51.
>
>
>
> Vậy completing the square là sao?
>
>
>
> Đơn giản là vầy: Nói đủ hơn là completing the square và khớp mẫu (pattern matching): Ví dụ ta biết pdf của univariate normal 𝒩(μ, σ²) = 1/√2πσ² exp{-(x-μ)²/2σ²}, vậy thì giả sử ta đang derive pdf của posterior distribution mà ra được có dạng \[cái gì đó\] nhân exp (hàm bậc hai của μ) thì lập tức có thể kết luận đây là pdf của normal (lí thuyết xác suất cho phép). Và từ đó, bằng cách khớp mẫu, ta sẽ có thể kết luận mean và variance của posterior.
>
>
>
> Rồi, bắt đầu làm:
>
>
>
> Ta có priori: f(𝐰) = 𝒩(𝐰|𝐦0, 𝐒0)
>
>
>
> Posteriori: f(𝐰|data), ở đây chính là f(𝐰|𝐭,𝐗) (𝐭, 𝐗 là giá trị của data: các 𝐭 = (t1,...tn) còn các vector input 𝐱1,...𝐱N gom thành matrix 𝐗)
>
>
>
> Bayes theorem cho ta: f(𝐰|data) = f(data|𝐰)f(𝐰)/f(data)
>
>
>
> vì f(data) chỉ là constant không âm, ta không quan tâm đến nó, để rồi thay "=" bởi "∝":
>
>
>
> f(𝐰|data) ∝ f(data|𝐰)f(𝐰) (f(data|𝐰) nếu xem như hàm của 𝐰 thì cũng chính là likelihood L(𝐰|data)
>
>
>
> ⇔ f(𝐰|𝐭,𝐗) ∝ f(𝐭|𝐰,𝐗) f(𝐰)
>
>
>
> và f(𝐭|𝐰,𝐗), là joint pdf của T1,...Tn độc lập và có cùng distribution là 𝒩(y(𝐰, 𝐱), 1/β) nên cũng phụ thuộc β, và tách f(𝐭|𝐰,𝐗) thành Πn f(tn|𝐰,𝐗), nên cái trên trở thành
>
>
>
> ⇔ f(𝐰|𝐭,𝐗,β,α) ∝ Πn f(tn|𝐰,𝐱n) f(𝐰)
>
>
>
> Thay công thức của f(tn|𝐰,𝐱n) là 𝒩(tn|𝐰ᵀΦ(𝐱n), 1/β) = 1/√2π(1/β) exp{-(tn-𝐰ᵀΦ(𝐱n))²/2(1/β)}
>
>
>
> ⇒ Πn f(tn|𝐰,𝐱n) = Πn 1/√2π(1/β) exp{-(tn-𝐰ᵀΦ(𝐱n))²/2(1/β)}
>
>
>
> = Πn {\[2π(1/β)\]^(-1/2) exp{-(tn-𝐰ᵀΦ(𝐱n))²/2(1/β)}}
>
>
>
> = \[2π(1/β)\]^(-n/2) Πn exp{-(tn-𝐰ᵀΦ(𝐱n))²/2(1/β)}
>
>
>
> =  c1 exp{-(β/2) Σn (tn-𝐰ᵀΦ(𝐱n))²}
>
>
>
> và f(𝐰) = 𝒩(𝐰|𝐦0, 𝐒0) = \[(2π)^-M/2\] \[1/|𝐒0|^1/2\] exp\[-(1/2)(𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)\]
>
>
>
> = c2 \[|𝐒0|^-1/2\] exp\[-(1/2)(𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)\] (Đặt c2 = (2π)^-M/2)
>
>
>
> = c2 c3 exp\[-(1/2)(𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)\] (Đặt c3 = \[|𝐒0|^-1/2\])
>
>
>
> Như vậy
>
>
>
> f(𝐰|𝐭,𝐗,β,α)∝ Πn f(tn|𝐰,𝐱n) f(𝐰)
>
>
>
> = c1 exp{-(β/2) Σn (tn-𝐰ᵀΦ(𝐱n))²} c2 c3 exp\[-(1/2)(𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)\]
>
>
>
> = c1 c2 c3 exp{-(β/2) Σn (tn-𝐰ᵀΦ(𝐱n))²} exp\[-(1/2)(𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)\] (1)
>
>
>
> ---
>
>
>
> Xét riêng cụm Σn (tn-𝐰ᵀΦ(𝐱n))² chút xíu:
>
>
>
> Có thể thấy nó chính là ||𝐭 - **Φw**||², vì sao? vì design matrix **Φ** được define là matrix có các hàng là \[Φ(𝐱1)\]ᵀ, \[Φ(𝐱2)\]ᵀ,...\[Φ(𝐱N)\]ᵀ. Nên **Φw** chính là vector có các phần tử là \[Φ(𝐱1)\]ᵀ𝐰 (cũng là 𝐰ᵀΦ(𝐱1)), \[Φ(𝐱2)\]ᵀ𝐰,.. Và dẫn đến 𝐭 - **Φw** chính là vector có các phần tử là t1-𝐰ᵀΦ(𝐱1), t2-𝐰ᵀΦ(𝐱2),...tn-𝐰ᵀΦ(𝐱n)
>
>
>
> Và vì ||u|| = uᵀu nên ||𝐭 - **Φw**||² cũng là (𝐭 - **Φw**)ᵀ(𝐭 - **Φw**)
>
>
>
> ---
>
>
>
> Vậy (1) = c1 c2 c3 exp{-(β/2) (𝐭 - **Φw**)ᵀ(𝐭 - **Φw**)} exp\[-(1/2)(𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)\] 
>
>
>
>  = c4 exp{-(β/2) (𝐭 - **Φw**)ᵀ(𝐭 - **Φw**) -(1/2)(𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)} (đặt c4 = c1,c2,c3)
>
>
>
>  = c4 exp{-(1/2) \[(𝐭 - **Φw**)ᵀ (β𝐈) (𝐭 - **Φw**) + (𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)\] }
>
>
>
>  = c4 exp{-(1/2) \[(𝐭 - **Φw**)ᵀ (β𝐈) (𝐭 - **Φw**) + (𝐰 - 𝐦0)ᵀ 𝐒0inv (𝐰 - 𝐦0)\] }
>
>
>
>  = c4 exp{-(1/2) \[(𝐭ᵀβ𝐈 - 𝐰ᵀ**Φ**ᵀβ𝐈)(𝐭 - **Φw**) + (𝐰ᵀ𝐒0inv - 𝐦0T𝐒0inv)(𝐰 - 𝐦0)\] }
>
>
>
>  = c4 exp{-(1/2) \[𝐭ᵀβ**It** - 𝐰ᵀ**Φ**ᵀβ**It** - 𝐭ᵀβ**IΦw** + 𝐰ᵀ**Φ**ᵀβ**IΦw** + 𝐰ᵀ𝐒0inv𝐰 - 𝐦0T𝐒0inv𝐰 - 𝐰ᵀ𝐒0inv𝐦0 + 𝐦0T𝐒0inv𝐦0\] }
>
>
>
>  = c4 exp{-(1/2) \[β𝐭ᵀ𝐭 - β𝐰ᵀ**Φ**ᵀ𝐭 - β𝐭ᵀ**Φw** + β𝐰ᵀ**Φ**ᵀ**Φw** + 𝐰ᵀ𝐒0inv𝐰 - 𝐦0T𝐒0inv𝐰 - 𝐰ᵀ𝐒0inv𝐦0 + 𝐦0T𝐒0inv𝐦0\] }
>
>
>
>  = c4 exp{-(1/2) \[β𝐭ᵀ𝐭 - 2β𝐭ᵀ**Φw** + β𝐰ᵀ**Φ**ᵀ**Φw** + 𝐰ᵀ𝐒0inv𝐰 - 2𝐦0T𝐒0inv𝐰 + 𝐦0T𝐒0inv𝐦0\] }
>
>
>
>  = c4 exp{-(1/2) \[β𝐰ᵀ**Φ**ᵀ**Φw** + 𝐰ᵀ𝐒0inv𝐰 - 2β𝐭ᵀ**Φw** - 2𝐦0T𝐒0inv𝐰 + 𝐦0T𝐒0inv𝐦0 + β𝐭ᵀ𝐭\] }
>
>
>
>  = c4 exp{-(1/2) \[𝐰ᵀ\[β**Φ**ᵀ**Φ**+𝐒0inv\]𝐰 - 2(β𝐭ᵀ**Φ** + 𝐦0T𝐒0inv)𝐰 + (𝐦0T𝐒0inv𝐦0 + β𝐭ᵀ𝐭)\] } (2)
>
>
>
> Rồi tới đây ta mới thực hiện khớp mẫu:
>
>
>
> Nhớ lại công thức khái quát của 𝒩(𝐱|**μ**, **Σ**) = \[(2π)^-D/2\] \[1/|**Σ**|^1/2\] exp\[-(𝐱 - **μ**)ᵀ **Σ**inv (𝐱 - μ)/2\]
>
>
>
> và ta sẽ chỉ cần quan tâm -(𝐱 - **μ**)ᵀ **Σ**inv (𝐱 - μ)/2, 
>
>
>
> = -(𝐱ᵀ**Σ**inv - **μ**ᵀ**Σ**inv)(𝐱 - μ)/2
>
>
>
> = -(𝐱ᵀ**Σ**inv𝐱 - **μ**ᵀ**Σ**inv𝐱 - 𝐱ᵀ**Σ**inv**μ** + **μ**ᵀ**Σ**inv**μ**)/2
>
>
>
> = -(𝐱ᵀ**Σ**inv𝐱 - 2**μ**ᵀ**Σ**inv𝐱 + **μ**ᵀ**Σ**inv**μ**)/2
>
>
>
> Và lập luận rằng,  vì (2) cũng có dạng quadratic function của 𝐰, nên đủ kết luận posterior f(𝐰|data) là normal
>
>
>
> Và để xác định mean và covariance ta thực hiện khớp:
>
>
>
> 𝐱ᵀ**Σ**inv𝐱 sẽ ứng với 𝐰ᵀ\[β**Φ**ᵀ**Φ**+𝐒0inv\]𝐰 → **Σ**inv ứng với β**Φ**ᵀ**Φ**+𝐒0inv. 
>
>
>
> Như vậy tới đây đã có thể kết luận inverse của covariance matrix của posterior distribution 𝐒N⁻¹ = β**Φ**ᵀ**Φ**+𝐒0inv, → đây chính là (3.51)
>
>
>
> Tiếp - 2**μ**ᵀ**Σ**inv𝐱 sẽ khớp với - 2(β𝐭ᵀ**Φ** + 𝐦0T𝐒0inv)𝐰 → **μ**ᵀ**Σ**inv khớp với (β𝐭ᵀ**Φ** + 𝐦0T𝐒0inv)
>
>
>
> ⇔ **μ**ᵀ**Σ**inv khớp với (β𝐭ᵀ**Φ** + 𝐦0T𝐒0inv)
>
>
>
> nên β𝐭ᵀ**Φ** + 𝐦0T𝐒0inv chính là 𝐦Nᵀ𝐒N⁻¹: β𝐭ᵀ**Φ** + 𝐦0T𝐒0inv = 𝐦Nᵀ𝐒N⁻¹
>
>
>
> ⇔ β𝐭ᵀ**Φ** + 𝐦0T𝐒0inv = 𝐦Nᵀ𝐒N⁻¹
>
>
>
> ⇔ β**Φ**ᵀ𝐭 + 𝐒0invᵀ𝐦0 = 𝐒N⁻¹ᵀ𝐦N
>
>
>
> ⇔ β**Φ**ᵀ𝐭 + 𝐒0inv𝐦0 = 𝐒N⁻¹𝐦N (các covariance matrix đối xứng nên bỏ tranpose)
>
>
>
> Nhân hai vế cho 𝐒N:
>
>
>
> ⇔ 𝐒N(β**Φ**ᵀ𝐭 + 𝐒0invᵀ𝐦0) = 𝐦N
>
>
>
> **⇔ m**N = 𝐒N{𝐒0inv 𝐦0 + β**Φ**ᵀ𝐭} → Đây chính là 3.50
>
>
>
> Tới đây ta đã làm xong bài.
>
> \
> Nên tóm lại, nói là complete the square nhưng thật ra là làm theo kiểu khớp mẫu sẽ dễ hơn.
>
>
>
>
>
>
>
>
>
> ---

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Bài làm rất chi tiết, giải thích rõ ràng cả về bối cảnh lý thuyết lẫn phương pháp hoàn thành bình phương (completing the square). Các bước biến đổi và khớp mẫu (pattern matching) được thực hiện chính xác để đi đến kết quả cuối cùng.

**🔗 See also:** [Bayesian Linear Regression Posterior Update](./331_bayesian_linear_regression.md#node-fv65lte) · [PDF Gaussian Đa Biến](./124_the_gaussian_distribution.md#node-40ke7sj)

<br>

<a id="node-3ldsqi5"></a>

