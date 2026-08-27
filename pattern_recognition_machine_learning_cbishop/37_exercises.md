# 3.7 Exercises

📊 **Progress:** `3` Notes | `4` Screenshots | `2` AI Reviews

---
<a id="node-rasw876"></a>

<br>

<a id="node-2dv7p1f"></a>

## Orthogonal Projection and Least Squares

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
> Trong bài nói về projection matrix thầy Strang giúp ta lập luận ra cái công thức của matrix projection onto C(A) rất dễ như sau, ta có matrix A size m × n. Thì C(A), column space, theo định nghĩa chính là subspace tạo bởi mọi linear combination của các column vector của matrix A. Thế thì, xét một vector b ∈ R^m, khi chiếu nó lên C(A), được p, thì dĩ nhiên p ∈ C(A), nên theo định nghĩa của C(A), p phải là linear combination các vector column của A vói hệ số tổ hợp nào đó, ta gọi là x, tức p = Ax. Và phần dư, e = b - p, theo góc nhìn hình học sẽ phải vuông góc với C(A) (như việc ta chiếu 1 điểm trong R^3 lên mặt phẳng, thì vector b tách thành 2 phần, 1 nằm trong mặt phẳng, một vuông góc với mặt phẳng vậy). Như vậy, e ⊥ C(A) mà theo định lý cơ bản của của đại số tuyến tính, nói rằng ta có hai cặp subspace bù nhau và vuông góc đó là column space và left nullspace, rowspace và nullspace. Vậy thì theo đó, khi e ⊥ C(A) suy ra e ∈ left nullspace N(AT). Điều này đồng nghĩa phương trình e là nghiệm của ATx = 0, tức ATe = 0 (A transpose e = 0, trong cách ghi chú của mình, mình luôn dùng T là cho transpose cho gọn, khi nào cần dùng chữ T thì sẽ ghi rõ). Vậy ta có:
>
>
>
> ATe = 0 ⇔ AT(b - p) = 0 ⇔ ATb = ATp ⇔ ATb = ATAx đây chính là normal equation.
>
>
>
> Tiếp, khi A full column rank, thì ATA sẽ full rank cũng là invertible khiến ta có thể nhân hai vế cho (ATA)inv, ta sẽ có: x = (ATA)inv ATb, và p = Ax = A(ATA)inv ATb, đặt P = A(ATA)inv AT, ta có p = Pb, đồng nghĩa, projection giúp chiếu b lên C(A) chính là P = A(ATA)inv AT
>
>
>
> Vậy tới đây ta chỉ việc áp dụng kết quả này, để có matrix giúp chiếu v lên space spanned bởi columns của **Φ** (cái này chính là column space của **Φ** thôi, tức C(**Φ**)) sẽ là: **Φ**(**Φ**T**Φ**)inv **Φ**T.
>
>
>
> Trong bài giảng đó, thấy thầy cũng check lại hai tính chất của projection matrix, là PP = P (chiểu b lên C(A) rồi thì chiếu lần nữa sẽ giữ nguyên, và PT = P) ta thử xem: 
>
>
>
> \[**Φ**(**Φ**T**Φ**)inv **Φ**T\] \[**Φ**(**Φ**T**Φ**)inv **Φ**T\] 
>
>
>
> = **Φ**(**Φ**T**Φ**)inv **Φ**T**Φ**(**Φ**T**Φ**)inv **Φ**T
>
>
>
> = **Φ I** (**Φ**T**Φ**)inv **Φ**T
>
>
>
> = **Φ** (**Φ**T**Φ**)inv **Φ**T → đúng là PP = P
>
>
>
> Và Xét \[**Φ**(**Φ**T**Φ**)inv **Φ**T\]T, dùng rule (AB)T = BT AT:
>
>
>
> = (**Φ**T)T \[**Φ**(**Φ**T**Φ**)inv\]T\]
>
>
>
> = **Φ** \[(**Φ**T**Φ**)inv\]T **Φ**T\]
>
>
>
> = **Φ** \[(**Φ**T**Φ**)inv\] **Φ**T\] (do **Φ**T**Φ** đối xứng nên **(Φ**T**Φ**)inv cũng vậy.
>
>
>
>
>
> ---
>
>
>
> Và như vậy, công thức 3.15, tức MLE của **w**, **w**ML:\*\* = (**Φ**T**Φ**)inv **Φ**T**t** thì **Φw**ML sẽ là:
>
>
>
> **Φ**(**Φ**T**Φ**)inv **Φ**T**t**, chính là tương ứng với p = A(ATA)inv ATb hình chiếu của b lên C(A), thì cái này chính là hình chiếu của **t lên** C(**Φ**) chứ gì nữa.
>
>
>
> Như vậy **w**ML sẽ là có vai trò như **x** ở trên đó là BỘ HỆ SỐ TỔ HỢP GIÚP LINEARLY COMBINE CÁC COLUMN VECTOR CỦA **Φ** ĐỂ ĐƯỢC PROJECTION CỦA **t** LÊN C(**Φ**).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Ghi chú xuất sắc, kết hợp rất tốt kiến thức Đại số tuyến tính từ MIT 18.06 để giải thích trực quan và chứng minh chặt chẽ cả hai yêu cầu của bài toán. Các bước chứng minh tính chất ma trận hình chiếu và liên hệ với lời giải tối ưu w_ML đều hoàn toàn chính xác.

**🔗 See also:** [3.1.2 Geometry of least squares](./312_geometry_of_least_squares.md#node-6e545fx) · [Maximum Likelihood and Gradient](./311_maximum_likelihood_and_least_squares.md#node-ogc31vz)

<br>

<a id="node-tu3cct2"></a>

### Lagrange Multipliers in Regularization

<p align="center"><kbd><img src="assets/8np4ha463u5.png" width="80%"></kbd></p>

> [!NOTE]
> Bài tập này muốn ta chỉ ra hai bài toán tối ưu sau là equivalent:
>
>
>
> (3.29): minimize (over **w**) (1/2 E_D(**w**) + (λ/2) Σj |wj|^q
>
>
>
> minimize (3.12) E_D(**w**) = Σi {(ti-**w**TΦ(**x**i))^2/2} với ràng buộc (3/30) Σj |wj|^q ≤ η
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
> Đầu tiên xét tại x\*, định lý Taylor cho phép ta rằng, khi x đủ gần x\*, thì hàm f(x) ≈ f(x\*) + ∇f(x\*)T(x-x\*), ý nghĩa là, trong phạm vi lân cận x\*, hàm f (có thể là hàm phi tuyến) hành xử gần giống hàm tuyến tính f^(x) = f(x\*) + ∇f(x\*)T(x-x\*).
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
> Còn để s là feasible direction, ta sẽ cần c1(x + s) vẫn ≥ 0, với s nhỏ, c1(x + s) cũng hành xử gần giống hàm tuyến tính, nên điều kiện trở thành c1(x) + ∇c1(x)Ts ≥ 0 (2)
>
>
>
> Vậy lập luận như sau, yêu cầu là: ta chia hai trường hợp:
>
>
>
> Case i) Gỉa sử tại x\*, constraint đang inactive: c1(x\*) &gt; 0, khi đó, dễ thấy là để thỏa tồn tại feasible direcition s: c1(x\*) + ∇c1(x\*)Ts ≥ 0, thì thật ra s có thể là vector có hướng tùy ý, miễn là giả sử nếu hướng của nó khiến ∇c1(x)Ts âm, thì chỉ cần khống chế độ lớn của s để giá trị âm ko quá nhỏ, giúp c1(x\*) dương vẫn đủ gánh. Như vậy có thể nói trong trường hợp này luôn tồn tại s giúp x\* + s vẫn feasible. Vậy câu hỏi để tìm candidate là, điểm x\* này nên như thế nào thì không thể đi theo s bất kì giúp giảm f^? Câu trả lời đó là: x\* là điểm mà gradient hàm f tại đó đang = 0. Vì khi đó f^(x\* + s) = f(x\*) + ∇f(x\*)Ts = f(x\*) bất kể s có là gì.
>
>
>
> Vậy, khi x\* có c1(x\*) &gt; 0 thì điều kiện để nó là candidate cho solution là ∇f(x\*) = 0
>
>
>
>
>
> Case ii) Tại x\*, constraint đang active: c1(x\*) = 0. Lúc này, điều kiện c1(x\*) + ∇c1(x\*)Ts ≥ 0 ⇔ ∇c1(x\*)Ts ≥ 0, tức s hợp góc nhọn hoặc tù với ∇c1(x\*). Trong khi đó, để thỏa việc giảm f^, thì ∇f(x\*)Ts phải &lt; 0 tức s hợp với ∇f(x\*) góc tù. Như vậy, cách duy nhất để tại x\* không thể tồn tại s thỏa hai cái này chính là ∇f(x\*) trùng hướng ∇c1(x\*). vì khi đó ko thể có s vừa hợp góc tù | nhọn với vector ∇f(x\*) mà lại vừa hợp góc tù với ∇f(x\*) được. Và điều kiện này thể hiện theo toán học là:
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
> Xét bài toán 1: minimize (over **w**) (1/2 E_D(**w**) + (λ/2) Σj |wj|^q, đây là bài toán unconstraint nên điều kiện cần tối ưu bậc nhất đơn giản là: gradient của objective = 0:
>
>
>
> ∇\_**w** \[(1/2 E_D(**w**) + (λ/2) Σj |wj|^q\] = 0
>
>
>
> ⇔ ∇\_**w** (1/2 E_D(**w**)\] + ∇\_**w** \[(λ/2) Σj |wj|^q\] = 0
>
>
>
> ⇔ 1/2 ∇\_**w** \[E_D(**w**)\] + (λ/2) ∇\_**w** \[ Σj |wj|^q\] = 0 (a)
>
>
>
> Còn bài toàn 2: minimize (3.12) E_D(**w**) = Σi {(ti-**w**TΦ(**x**i))^2/2} với ràng buộc (3/30) Σj |wj|^q ≤ η
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
> Lagrangian: ℒ(**w**, λ) = E_D(**w**) - λ\[η - Σj |wj|^q\]
>
>
>
> Stationary conditiion:
>
>
>
> ∇\_**w** ℒ(**w**, λ) = 0 ⇔ ∇\_**w** \[E_D(**w**) - λ\[η - Σj |wj|^q\]\] = 0
>
>
>
> ⇔ ∇\_**w** E_D(**w**) - ∇\_**w** λ\[η - Σj |wj|^q\]\] = 0
>
>
>
> ⇔ ∇\_**w** E_D(**w**) - λ ∇\_**w** \[η - Σj |wj|^q\]\] = 0
>
>
>
> ⇔ ∇\_**w** E_D(**w**) - λ ∇\_**w** \[η\] + λ ∇\_**w** \[Σj |wj|^q\] = 0
>
>
>
> ⇔ ∇\_**w** E_D(**w**) - 0 + λ ∇\_**w** \[Σj |wj|^q\] = 0 (đạo hàm theo w của constant η dĩ nhiên = 0)
>
>
>
> ⇔ (1/2) ∇\_**w** E_D(**w**) + (1/2) λ ∇\_**w** \[Σj |wj|^q\] = 0 (b) (nhân thêm 1/2)
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
> E_D(**w**) là hàm lồi vì là hàm bậc hai theo w.
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
> Nếu ta tăng hệ số regularization λ, điều này sẽ khiến giảm E_w(**w**) = Σj |w\*j|^q, và vì η = E_w(**w**) nên η sẽ giảm.
>
>
>
> Còn nếu ta cho hệ số regularization = 0, tức là không penalized khi **w** lớn, thì E_w(**w**) có thể sẽ lớn, khiến η với yeu cầu ≥ E_W(**w**) nên sẽ lớn lên.
>
>
>
> Như vậy quan hệ của λ và η là: λ lớn thì η nhỏ và ngược lại.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Lời giải rất xuất sắc, không chỉ chứng minh đầy đủ sự tương đương toán học thông qua điều kiện KKT mà còn giải thích trực quan rất sâu sắc về KKT. Phần thảo luận về mối quan hệ nghịch biến giữa ̹Η và ̹Λ cũng hoàn toàn chính xác.

**🔗 See also:** [General Regularizer and Lasso](./314_regularized_least_squares.md#node-1msg8km) · [Likelihood and Error Functions](./311_maximum_likelihood_and_least_squares.md#node-urnjdcs)

<br>

<a id="node-y5iamw4"></a>

#### Regularization via Input Noise

<p align="center"><kbd><img src="assets/xlt2gwx6h2.png" width="80%"></kbd></p>

> [!NOTE]
> Cùng làm bài này, trước tiên là dịch sơ cái yêu cầu
>
>
>
> Ở đây gs xét linear model y(x, **w**) = w0 + Σi=0:D wixi
>
>
>
> với SSE function ED(**w**) = (1/2) Σi=1:N {y(xi, **w**) - ti}^2 
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
> Đọc cái đề bài thì tạm hiểu là vầy:
>
>
>
> Nói ngắn gọn, thì gs đề xuất ta thử add noise εi vào input. Để hiểu rõ hơn, nên ôn lại chút về cách mà ta thấy gs Bishop làm trong suốt chapter 3, có thể tóm gọn trong vài ý chính thế này:
>
>
>
> Ta dùng / giả định data tuân theo một mô hình phân phối như sau, và ta chỉ coi target là random variable: Ti|xi \~ n(y(**w**, xi), 1/β)
>
>
>
> Và giả định này cũng chính là giả định noise εi = y(xi, **w**) - Ti sẽ \~ n(0, 1/β) 
>
>
>
> (Ti|xi \~ n(y(**w**, xi), 1/β) ⇔ εi = Ti - y(xi, **w**) sẽ \~ n(0, 1/β) là do dùng location scale theorem, đã học trong Statistical Inference Casella, ngắn gọn như sau: Khi ta có X có distribution thuộc location family ứng với location là μ, thì X - μ sẽ chính random variable thuộc standard member của family đó, tức là location = 0. Nên ở đây, normal là một distribution thuộc loại này, nên khi Ti \~ n(y(**w**, xi), 1/β) thì Ti - y(xi, **w**), tức εi sẽ chính là một n(0, 1/β))
>
>
>
> Vậy bây giờ, theo đề bài, ta sẽ add noise vào input, tức là thay xi bởi xi + εi, và đi minimizing E_D over distribution của εi. Là sao nhỉ.
>
>
>
> Đầu tiên nhìn vào E_D, = (1/2) Σi=1:N {y(xi, **w**) - ti}^2
>
>
>
> Mình hiểu thế này: Bài toán ban đầu là ta có bộ data set (x1, t1), (x2,t2) ...(xN, tN), hay đặt các vector x1,..xN vào vector **x**, và đặt t1,...tN vào vector **t**. Thì ta thể hiện observed data bởi (**x**, **t**).
>
>
>
> Và với việc coi target variable là random variable (còn input thì không), thì **t** chính là observed value của random sample **T** = (T1, T2,...TN).
>
>
>
> Như vậy, (y(x, **w**) - T)^2 là hàm số của random variable T, nên dĩ nhiên cũng là random variable.
>
>
>
> Và vì nó là random variable, ta có thể đặt vấn đề xét trung bình của nó, tức expected value:
>
>
>
> E\[(y(x, **w**) - T)^2\]
>
>
>
> Thế thì tuy ta đang giả định y(x, **w**) - T \~ n(0, 1/β), nhưng \[y(x, **w**) - T\]^2 thì ta không biết là phân phối gì. Nên không thể tính E\[(y(x, **w**) - T)^2\], để ra một hàm theo **w**, từ đó đi minimize over **w** cái này.
>
>
>
> Thay vì vậy, ta xem S = (y(x, **w**) - T) đến từ một uniform discrete distriution có các discrete value là s1 = y(x1, **w**) - t1,..., sN = y(xN, **w**) - tN.
>
>
>
> Từ đó, E\[(y(x, **w**) - T)^2\] có thể tính cái này nhờ LOTUS
>
>
>
> = Σn=1:N \[y(xn, **w**) - tn\]^2 P(S = sn)
>
>
>
> = (1/N) Σn=1:N \[y(**x**n, **w**) - tn\]^2 
>
>
>
> Và từ đó ta đi minimize over **w** hàm objective E\[(y(**x**, **w**) - T)^2\] = (1/N) Σn=1:N \[y(xn, **w**) - tn\]^2
>
>
>
> và với N là constant thì bài toán này cũng tương đương minimize (1/2) Σn=1:N \[y(xn, **w**) - tn\]^2
>
> và đây chính là sum-of-squares error E_D(**w**)
>
>
>
> Cách lập luận này giúp ta có cái nhìn sâu hơn vào bản chất của cái hàm SSE để thấy nó chính là kì vọng của S = y(**w**, x) - T với S là uniform discrete với N posible value s1,...sN. 
>
>
>
> ---
>
>
>
> Còn ở đây đề bài nói là giả sử thêm noise \~ 𝒩(0, σ²) vào input xi, rồi đi "minimizing E_D average out over noise distribution" thì ta nên hiểu là: "À, có data như vậy, và thiết lập hàm SSE như vậy, thì nay, với viêc xi có thêm noise, nó trở thành một random variable, và ta sẽ tính kì vọng của random variable E_D này, rồi đi minimize nó."
>
>
>
> Cụ thể hơn: Thay xn bởi xn + εn, lúc này E_D(**w**) = (1/2) Σn=1:N \[y(xn + εn, **w**) - tn\]^2 trở thành random variable.
>
>
>
> Ta có thể thay kí hiệu là E_D(**w**, **ε**) để thể hiện giờ nó phụ thuộc **ε** = (ε1,...εN) nữa
>
>
>
> Và vì nó là random variable ta sẽ lấy expected value của cái random variable này (cũng chính là động tác average out over noise distribution). 
>
>
>
> E\[E_D(**w**, **ε**)\] = E\[(1/2) Σn=1:N \[y(xn + εn, **w**) - tn\]^2\]
>
>
>
> = (1/2) Σn=1:N E\[\[y(xn + εn, **w**) - tn\]^2\]
>
>
>
> = (1/2) Σn=1:N E\[y(xn + εn, **w**)^2 - 2y(xn + εn, **w**)tn + tn^2\]
>
>
>
> dùng tính linearity của kì vọng
>
>
>
> = (1/2) Σn=1:N {E\[y(**x**n + εn, **w**)^2\] - E\[2y(xn + εn, **w**)tn\] + E\[tn^2\]}
>
>
>
> = (1/2) Σn=1:N {E\[y(**x**n + εn, **w**)^2\] - 2E\[y(xn + εn, **w**)\]tn + tn^2}
>
>
>
> Với y(**x**, **w**) = w0 + Σi=1:D xi wi
>
>
>
> ⇒ y(**x**n + **ε**n, **w**) = w0 + Σi=1:D (xni + εni) wi)
>
>
>
> = w0 + Σi=1:D (xni wi)  + Σi=1:D (εni wi)
>
>
>
> = w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)
>
>
>
> ⇒ E\[y(xn + **ε**n, w)\] = E\[w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)\]
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
> = y(**w**, **xn**)
>
>
>
> ---
>
>
>
> \[y(**x**n + **ε**n, **w**)\]^2 = \[w0 + Σi=1:D (xni + εni) wi\]^2
>
>
>
> = \[w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)\]^2
>
>
>
> = \[y(**w**, **xn**) + Σi=1:D (εni wi)\]^2
>
>
>
> = y(**w**, **xn**)^2 + 2 y(**w**, **xn**) Σi=1:D (εni wi) + \[Σi=1:D (εni wi)\]^2
>
>
>
> ⇒ E{\[y(**x**n + **ε**n, **w**)\]^2}
>
>
>
>  = E{ y(**w**, **xn**)^2 + 2 y(**w**, **xn**) Σi=1:D (εni wi) + \[Σi=1:D (εni wi)\]^2 }
>
>
>
>  = E{ y(**w**, **xn**)^2 } + 2 y(**w**, **xn**) E{ Σi=1:D (εni wi) } + E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
>  = y(**w**, **xn**)^2 + 2 y(**w**, **xn**) { Σi=1:D \[E(εni) wi\] } + E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
>  = y(**w**, **xn**)^2 + 2 y(**w**, **xn**) { Σi=1:D \[0 × wi\] } + E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
>  = y(**w**, **xn**)^2 + 0 + E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
>  = y(**w**, **xn**)^2 + E{ \[Σi=1:D (εni wi)\]^2 }
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
> E\[E_D(**w**, **ε**)\] = (1/2) Σn=1:N {E\[y(**x**n + εn, **w**)^2\] - 2E\[y(xn + εn, **w**)\]tn + tn^2}
>
>
>
> = (1/2) Σn=1:N { y(**w**, **xn**) + E{ \[Σi=1:D (εni wi)\]^2 } - 2 y(**w**, **xn**) tn + tn^2}
>
>
>
> = (1/2) Σn=1:N { y(**w**, **xn**) - 2 y(**w**, **xn**) tn + tn^2 + E{ \[Σi=1:D (εni wi)\]^2 } }
>
>
>
> = (1/2) Σn=1:N { \[y(**w**, **xn**) - tn\]^2 + E{ \[Σi=1:D (εni wi)\]^2 } }
>
>
>
> = (1/2) Σn=1:N { \[y(**w**, **xn**) - tn\]^2 } + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]^2 } }
>
>
>
> = E_D(**w**) + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]^2 } }
>
>
>
> Như vậy tới đây ta có:
>
>
>
> E\[E_D(**w**, **ε**)\] = E_D(**w**) + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]^2 } }
>
>
>
> Xét tiếp cái kì vọng trong tổng của cụm thứ hai:
>
>
>
> E{ \[Σi=1:D (εni wi)\]^2 }

<br>

