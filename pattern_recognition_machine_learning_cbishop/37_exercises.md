# 3.7 Exercises

📊 **Progress:** `3` Notes | `4` Screenshots | `3` AI Reviews

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

#### Ex 3.4 Regularization via Input Noise

<p align="center"><kbd><img src="assets/xlt2gwx6h2.png" width="80%"></kbd></p>

> [!NOTE]
> Cùng làm bài này, trước tiên là dịch sơ cái yêu cầu
>
>
>
> Ở đây gs xét linear model y(**x**, **w**) = w0 + Σi=0:D wixi
>
>
>
> với SSE function ED(**w**) = (1/2) Σn=1:N {y(**x**n, **w**) - tn}^2
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
> Trước khi làm nên làm rõ vài ý: Khi ông viết 3.105, ông ghi là y(x, **w**) = w0 + Σi wi xi. → chỗ gây lú: ông viết nét đậm cho **w**, ám chỉ nó là vector, nên dễ hiểu là wi là phần tử thứ i của vector **w**. Còn x, nó cũng là vector cơ mà (thể hiện qua Σi=1:D wi xi), sao ổng lại ko viết nét đậm, nên mình tự động viết nét đậm cho thấy **x** là vector.
>
>
>
> Như vậy bộ input sẽ là **x**1,**x**2,..**x**n...**x**N. và vector **x**n có các phần tử là xn1 xn2,...xnD.
>
>
>
> Tương tự, nhiễu (noise) εi cộng vào mỗi xi (của vector **x**) sẽ thì thì hợp lại với mỗi vector **x**1,**x**2,..**x**n...**x**N, nó sẽ được cộng một VECTOR **ε**1, **ε**2,...**ε**N. và vector **ε**n có các phần tử là εn1,...εnD.
>
>
>
> Tức là:
>
>
>
> Trước khi có noise: input là **x**1 = (x11,x12,..x1D), **x**2 = (x21, x22,...x2D) ...
>
>
>
> Sau khi cộng thêm noise: input là **x**1 = (x11 + ε11,x12 + ε12,..x1D + ε1D), ...
>
>
>
> Quy ước ở dưới (phòng khi mình quên viết bold / thường):
>
>
>
> **x**n vector input thứ n (n =1,...N), và xni là phần tử thứ i của nó 
>
> tương tự và vector noise **ε**n là vector noise add vào input **x**n, εni là phần tử thứ i của nó
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
> Cụ thể hơn: Thay **x**n bởi **x**n + **ε**n, lúc này E_D(**w**) = (1/2) Σn=1:N \[y(**x**n + **ε**n, **w**) - tn\]^2 **TRỞ THÀNH RANDOM VARIABLE.**
>
>
>
> (vì sao: Stat110 đã học, bất kì khi nào ta áp một function lên random variable thì ta có một random variable)
>
>
>
> Ta có thể thay kí hiệu là E_D(**w**, **ε**) để thể hiện giờ nó phụ thuộc **ε** = (ε1,...εN) nữa
>
>
>
> Và **vì nó là random variable ta sẽ lấy expected value của cái random variable** này và đây **cũng chính là động tác average out over noise distribution**.
>
>
>
> E\[E_D(**w**, **ε**)\] = E\[(1/2) Σn=1:N \[y(**x**n + **ε**n, **w**) - tn\]^2\]
>
>
>
> = (1/2) Σn=1:N E\[\[y(**x**n + **ε**n, **w**) - tn\]^2\]
>
>
>
> = (1/2) Σn=1:N E\[y(**x**n + **ε**n, **w**)^2 - 2y(xn + εn, **w**)tn + tn^2\]
>
>
>
> dùng tính linearity của kì vọng
>
>
>
> = (1/2) Σn=1:N {E\[y(**x**n + **ε**n, **w**)^2\] - E\[2y(xn + **ε**n, **w**)tn\] + E\[tn^2\]}
>
>
>
> = (1/2) Σn=1:N {E\[y(**x**n + **ε**n, **w**)^2\] - 2E\[y(xn + **ε**n, **w**)\]tn + tn^2}
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
> = w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)
>
>
>
> = w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)
>
>
>
> ⇒ E\[y(**x**n + **ε**n, w)\] = E\[w0 + Σi=1:D (xni wi) + Σi=1:D (εni wi)\]
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
> = y(**w**, **x**n)
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
> = \[y(**w**, **x**n) + Σi=1:D (εni wi)\]^2
>
>
>
> = y(**w**, **x**n)^2 + 2 y(**w**, **x**n) Σi=1:D (εni wi) + \[Σi=1:D (εni wi)\]^2
>
>
>
> ⇒ E{\[y(**x**n + **ε**n, **w**)\]^2}
>
>
>
> = E{ y(**w**, **x**n)^2 + 2 y(**w**, **x**n) Σi=1:D (εni wi) + \[Σi=1:D (εni wi)\]^2 }
>
>
>
> = E{ y(**w**, **x**n)^2 } + 2 y(**w**, **x**n) E{ Σi=1:D (εni wi) } + E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
> = y(**w**, **x**n)^2 + 2 y(**w**, **x**n) { Σi=1:D \[E(εni) wi\] } + E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
> = y(**w**, **x**n)^2 + 2 y(**w**, **x**n) { Σi=1:D \[0 × wi\] } + E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
> = y(**w**, **x**n)^2 + 0 + E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
> = y(**w**, **x**n)^2 + E{ \[Σi=1:D (εni wi)\]^2 }
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
> E\[E_D(**w**, **ε**)\] = (1/2) Σn=1:N {E\[y(**x**n + **ε**n, **w**)^2\] - 2E\[y(**x**n + **ε**n, **w**)\]tn + tn^2}
>
>
>
> = (1/2) Σn=1:N { y(**w**, **x**n) + E{ \[Σi=1:D (εni wi)\]^2 } - 2 y(**w**, **xn**) tn + tn^2}
>
>
>
> = (1/2) Σn=1:N { y(**w**, **x**n) - 2 y(**w**, **xn**) tn + tn^2 + E{ \[Σi=1:D (εni wi)\]^2 } }
>
>
>
> = (1/2) Σn=1:N { \[y(**w**, **x**n) - tn\]^2 + E{ \[Σi=1:D (εni wi)\]^2 } }
>
>
>
> = (1/2) Σn=1:N { \[y(**w**, **x**n) - tn\]^2 } + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]^2 } }
>
>
>
> = E_D(**w**) + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]^2 } }
>
> Như vậy tới đây ta có:
>
>
>
> E\[E_D(**w**, **ε**)\] = E_D(**w**) + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]^2 } }
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
> E{ \[Σi=1:D (εni wi)\]^2 }
>
>
>
> Xét cái tổng trước và tự hiểu là i chạy từ 1 tới D:
>
>
>
> (Σi (εni wi))^2
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
> = Σi (εni wi)^2 + 2 Σi≠j (εni wi)(εnj wj)
>
>
>
> = Σi εni εni (wi)^2 + 2 Σi≠j (εni εnj wiwj)
>
>
>
> Lấy kì vọng:
>
>
>
> E { Σi εni εni (wi)^2 + 2 Σi≠j (εni εnj wiwj) }
>
>
>
> = E\[Σi εni εni (wi)^2\] + E\[2 Σi≠j (εni εnj wiwj)\]
>
>
>
> = Σi (wi)^2 E\[εni εni\] + 2Σi≠j (wiwj) E\[εni εnj\]
>
>
>
> = Σi (wi)^2 E\[εni εni\] + 2Σi≠j (wiwj) E\[εni εnj\]
>
>
>
> Dùng cái đề bài cho:
>
>
>
> E\[εi εj\] = δij σ^2 và hàm δij = 1 khi i = j, và = 0 khi i ≠ j ta có
>
>
>
> = Σi (wi)^2 × (1 × σ^2) + 2Σi≠j (wiwj) × (0 × σ^2)
>
>
>
> = Σi (wi)^2 × σ^2
>
>
>
> = σ^2 Σi (wi)^2
>
>
>
> ---
>
>
>
> Thay vào E\[E_D(**w**, **ε**)\] = E_D(**w**) + (1/2) Σn=1:N E{ \[Σi=1:D (εni wi)\]^2 } }:
>
>
>
> = E_D(**w**) + (1/2) Σn=1:N \[σ^2 Σi (wi)^2\]
>
>
>
> = E_D(**w**) + (N/2) σ^2 Σi (wi)^2
>
>
>
> = E_D(**w**) + (Nσ^2/2) Σi (wi)^2
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
> E\[E_D(**w**, **ε**)\] = E_D(**w**) + (Nσ^2/2) Σi (wi)^2
>
>
>
> và có nghĩa là sao?
>
>
>
> Thì có nghĩa là, nếu ta đi minimize E\[E_D(**w**, **ε**)\] (đi tìm w để cái này có giá trị nhỏ nhất) thì tức ta sẽ thấy đây tương đương với bài toán minimize hàm error sau đây,
>
>
>
> Error function = E_D(**w**) + λ Σi (wi)^2 , λ = Nσ^2/2
>
>
>
> thì cái này chính là bài toán minimize sum square error (là cái E_D(w) đó) có thẹm L2 regularization (là cái Σi (wi)^2, chính là ||**w**||^2) với regularization coefficient là Nσ^2/2.
>
>
>
> Nói chung tóm lại, bài này chỉ là:
>
>
>
> Ta có hàm SSE E_D(**w**) = (1/2) Σi=1:N {y(**xi**, **w**) - ti}^2
>
>
>
> Xong ta thay **xi** = **x**i + **ε**i vì đề nói ta add noise εi vào
>
>
>
> Lúc này cái E_D(**w**), trở thành random variable: E_D(**w, ε**)
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
> Kết quả khi ra được tới E\[εni εni\] và E\[εni εnj\] thì dùng cái đề bài cho: E\[εi εj\] = δij σ^2. Và δij là kí hiệu của hàm Kronecker, = 1 khi i = j, và = 0 khi i khác j gs Bishop không nói.
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
> và với N là constant thì bài toán này cũng tương đương minimize (1/2) Σn=1:N \[y(xn, **w**) - tn\]^2 và đây chính là sum-of-squares error E_D(**w**)
>
>
>
> Cách lập luận này giúp ta có cái nhìn sâu hơn vào bản chất của cái hàm SSE để thấy nó chính là kì vọng của S = \[y(**w**, x) - T\]^2 với S là uniform discrete với N posible value s1,...sN.
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
> Đó là ta xét một khái niệm trong statistic gọi là likelihood, định nghĩa của nó là hàm của tham số (ở đây là **w**), thể hiện độ hợp lí của tham số khi dữ liệu quan sát có giá trị (observed data) ta đã thấy, kí hiệu L(**w**|observed data), Ở đây observed data chính là \[**x**1,...**x**N\], (t1,...tN). Và giá trị của nó tính bằng xác suất của event data mang giá trị observed data dựa trên **w**:
>
>
>
> L(**w**|observed data) = f(observed data|**w**)
>
>
>
> Cụ thể ở đây L(**w**|\[**x**1,...**x**N\], (t1,...tN)) = P(data = \[**x**1,...**x**N\], (t1,...tN)|**w**)
>
>
>
> với bài toán này ta chỉ coi T là random variable, thì:
>
>
>
> f(data = \[**x**1,...**x**N\], (t1,...tN)|**w**) = P(T1,...TN = (t1,...tN)|**w,** \[**x**1,...**x**N\])
>
>
>
> đặt **T** là vector (T1,...TN), matrix **X** matrix có các hàng là (**x**1)T,...(**x**N)T thì và f là pdf của của T, cũng là joint pdf của T1,...TN
>
>
>
> L(**w**|observed data) = f(**t**|**w**, **X**).
>
>
>
> Và cách làm / phương pháp nổi tiếng của Frequentist statistic, khi đi giải tìm point estimate cho w, chính là đi maximize cái hàm độ hợp lí này. Ta có bài toán:
>
>
>
> maximize (over **w**) f(**t**|**w**, **X**)
>
>
>
> Dùng tính iid f(**t**|**w**, **X**) = Πn=1:N f(tn|**w**, **xn**), bài toán trở thành.
>
>
>
> maximize (over **w**) Πn=1:N f(tn|**w**, **xn**)
>
>
>
> Và với bài toán tối ưu, ta có thể dùng hàm monotone để chuyển về bài toán tương đương dễ giải hơn và nghiệm của chúng giúp suy ra nghiệm của nhau (hoặc cùng nghiệm), cụ thể ta dùng ln, bài toán tương đương:
>
>
>
> maximize (over **w**) ln \[Πn=1:N f(tn|**w**, **xn**)\]
>
>
>
> Biến đổi hàm mục tiêu: ln \[Πn=1:N f(tn|**w**, **xn**)\] = Σn=1:N \[ln f(tn|**w**, **xn**)\]
>
>
>
> và thay pdf của Tn vô, dùng giả định là Tn \~ 𝒩(y(**x**n, **w**), 1/β),
>
>
>
> f(tn|w, xn) = \[constant c, là term dính tới β\] exp {-(tn - y(**x**n, **w**))^2/2(1/β)},
>
>
>
> hàm mục tiêu trở thành:
>
>
>
> Σn \[ln (c exp {-(tn - y(**x**n, **w**))^2/2(1/β) } \]
>
>
>
> = Σn \[ln c + ln exp {-(tn - y(**x**n, **w**))^2/2(1/β)} \]
>
>
>
> = Σn \[ln c\] + Σn ln exp {-(tn - y(**x**n, **w**))^2/2(1/β)}
>
>
>
> = Σn \[ln c\] + Σn {-(tn - y(**x**n, **w**))^2/2(1/β)}
>
>
>
> Tiếp tục chuyển thành bài toán tương đương bằng cách bỏ các constant (Σn \[ln c\] và β (là số dương) ta có:
>
>
>
>  maximize\_**w** Σn {-(tn - y(**x**n, **w**))^2/2(1/β) }
>
>
>
>  maximize\_**w** (-1/2) Σn (tn - y(**x**n, **w**))^2
>
>
>
> again, chuyển thành bài toán tối ưu tương đương bởi nguyên kí: maximize f ≡ minimize -f
>
>
>
> minimize \_**w** (1/2) Σn(tn - y(**x**n, **w**))^2
>
>
>
> Và đây chính là bài toán minimize Sum Of Square.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **100/100**
>
> Bài viết trình bày lời giải vô cùng chi tiết, chính xác và có tư duy ký hiệu rất mạch lạc khi phân biệt rõ vector và scalar. Các phần mở rộng liên hệ với LOTUS và Maximum Likelihood thể hiện sự hiểu biết sâu sắc và toàn diện về bản chất toán học của bài toán.

<br>

