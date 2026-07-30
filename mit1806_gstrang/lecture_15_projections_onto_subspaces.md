# Lecture 15: Projections
onto Subspaces

📊 **Progress:** `45` Notes | `47` Screenshots

---
<a id="node-l9qi36h"></a>

## Lecture 15: Projections
onto Subspaces

<br>

<a id="node-wv5up5i"></a>

<p align="center"><kbd><img src="assets/7x9pd2onabk.png" width="80%"></kbd></p>

<br>

<a id="node-lzzbmqo"></a>

<p align="center"><kbd><img src="assets/fzhh8lpvj1.png" width="80%"></kbd></p>

> [!NOTE]
> gs cho rằng đây là một bài **rất quan trọng** khi ta sẽ nói về
> **projection lên subspace** 
>
>
>
> Đầu tiên, gs dùng ví dụ trong **1D dimension subspace** - đó là 
> **đường thẳng a**: **tìm điểm trên a sao cho gần nhất với b**

<br>

<a id="node-ztclrq9"></a>

<p align="center"><kbd><img src="assets/14zb0qucscl.png" width="80%"></kbd></p>

> [!NOTE]
> ok thế thì với bài toán này, ta biết rằng, mình cần **tìm
> điểm (vector p) như hình vẽ**, và **e (viết tắt của error)** sẽ
> thể hiện **difference giữa b và p**, cho ta biết **sai số ta sẽ
> chịu khi project b lên a**.
>
>
>
> Và **vector p nằm trên phương vector a**, ta có **p = xa** và 
> bài toán trở thành **tìm p** tức là tìm ra x.

<br>

<a id="node-624nhj2"></a>

<p align="center"><kbd><img src="assets/guasfbp2jv.png" width="80%"></kbd></p>

> [!NOTE]
> Mọi thứ (cái vụ vuông góc) thể hiện qua equation này: 
>
>
>
> aTe = 0 <=> aT(b-p) = 0 <=> aT(b-xa) = 0 <=> aT(b-xa) = 0

<br>

<a id="node-h9vivir"></a>

<p align="center"><kbd><img src="assets/nai626pb8ub.png" width="80%"></kbd></p>

> [!NOTE]
> triển khai ra, chuyển vế ta có thế này:
>
>
>
> aT(b-xa) = 0 <=> aTb-aTxa = 0
>
>
>
> <=> aTb = aTxa = xaTa (vì x là scalar nên move đi đâu cũng
> được)

<br>

<a id="node-95k4jaz"></a>

<p align="center"><kbd><img src="assets/4x8af1nwlm6.png" width="80%"></kbd></p>

> [!NOTE]
> và chia hai vế cho aTa, ta có x = aTb / aTa 
>
>
>
> Và đó là cái cần tìm khi giải bài toán tìm projection của 
> b trên a

<br>

<a id="node-kvzzr6s"></a>

<p align="center"><kbd><img src="assets/eh8yy6es1ev.png" width="80%"></kbd></p>

> [!NOTE]
> thay x vào p = ax ta có p tính theo a, b như vầy.
> Gs đặt câu hỏi **gỉa sử cho b scale lên thành 2b**
> thì **projection của nó trên a sẽ ra sao**. 
>
>
>
> Me: sẽ scale lên **thành 2p**

<br>

<a id="node-gf35byx"></a>

<p align="center"><kbd><img src="assets/c0jdiybjz3s.png" width="80%"></kbd></p>

> [!NOTE]
> gs: Correct. Thế nếu double a lên?
>
>
>
> Thì nó không thay đổi gì. Như công thức có thể thấy a
> thành 2a thì cả tử và mẫu cũng đều x4, và nó sẽ
> cancel nhau nên p không thay đổi gì

<br>

<a id="node-a7h11fc"></a>

<p align="center"><kbd><img src="assets/1a62o8hhrcn.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì gs cho biết ta có thể **biểu diễn phép projection bởi
> một matrix**, gọi nó là **Projection matrix P**, và **thông qua
> nó ta sẽ tìm được projection của vector b**

<br>

<a id="node-alp188n"></a>

<p align="center"><kbd><img src="assets/8i9txq96566.png" width="80%"></kbd></p>

> [!NOTE]
> Và **aaT/aTa chính là matrix P**, mẫu số là một
> **scalar** (dot product của a với chính nó) và **aaT
> là một cols x một row** -> như ta đã biết nó là
> một **RANK 1 MATRIX**

<br>

<a id="node-u1oddq3"></a>

<p align="center"><kbd><img src="assets/iyvv1vggp5.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây gs cho biết m**ột điểm tuy dễ hiểu** nhưng kiểu như
> ta **có thể chưa để ý tới** đó là **column space của matrix
> P** sẽ là **subspace** mà khi ta n**hân P với một vector nào
> đó**, **kết quả sẽ luôn nằm trong columns space của P.** Và
> đương nhiên không chỉ Projection matrix P mà là bất kì
> matrix nào
>
>
>
> Điều này dễ hiểu, vì khi **nhân matrix A với vector u** nào đó
> thì kết quả đương nhiên là một **linear combination các cols
> của A** , và nó **sẽ là một vector thuộc columns space**.
>
>
>
> Vậy gs hỏi rằng **columns space của P là gì**, hay nói cách
> khác, khi tôi n**hân P với vector b thì kết quả ở đâu?**
>
>
>
> -> matrix **P là rank 1 matrix**, có **cols space với dim = 1**,
> và vector a chính là vector duy nhất trong basis. Nên **cols
> space của P chính là line đi qua vector a**. Nên kết quả của
> **Pb sẽ vẫn nằm trên line này**

**🔗 See also:** [linked note](#node-5su5cq6)

<br>

<a id="node-e87h0ke"></a>

<p align="center"><kbd><img src="assets/m6yrc1nd9me.png" width="80%"></kbd></p>

> [!NOTE]
> Gs: Đúng vậy

<br>

<a id="node-xra2vuk"></a>

<p align="center"><kbd><img src="assets/vd8k607eus.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp gs cho rằng rất tự nhiên để hỏi tiếp **matrix này có
> symmetric không?**
>
>
>
> Có, vì PT = **(aaT/aTa)T** = (aaT)T/(aTa) = aTTaT/aTa 
>
>
>
> = **aaT/aTa** = P
>
>
>
> => tức là vẫn transpose bằng chính nó, nên nó mà 
> **symmetric** matrix

<br>

<a id="node-eo7tabw"></a>

<p align="center"><kbd><img src="assets/5ef2nutgm4h.png" width="80%"></kbd></p>

> [!NOTE]
> Gs hỏi tiếp nếu ta **project lần thứ hai** thì ta sẽ có gì.
>
>
>
> -> Rõ ràng ta **sẽ vẫn ở đó**. Vậy là **P**2 = P**

<br>

<a id="node-ltdmtzs"></a>

<p align="center"><kbd><img src="assets/fc4kwsud19.png" width="80%"></kbd></p>

> [!NOTE]
> Từ đó ta có hai tính chất của
> matrix P: **P.T = P và P**2 = P**

<br>

<a id="node-pdkvpdd"></a>

<p align="center"><kbd><img src="assets/q15xs3fxkca.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp gs nói về **lí do** mà ta muốn **nghiên cứu về
> Projection**
>
>
>
> Đó là vì ở đầu bài ta đã nói là ta đang **deal với một
> equation system Ax=b** mà trong đó **khả năng cao là
> KHÔNG CÓ SOLUTION**, vì lí do có thể như ta có matrix A
> là matrix CAO, ỐM (khi trong các bài toán thực tế ta có
> nhiều sample hơn feature, nhiều equation hơn là số
> variable)
>
>
>
> Và matrix CAO, ỐM dẫn đến là **không đủ số cols (n) để
> span được toàn bộ không gian R^m**. Nên luôn có thể **có
> b nằm ngoài cols space** khiến Ax=b vô nghiệm
>
>
>
> Thành ra để giải quyết, ta có thể **GIẢI MỘT BÀI TOÁN
> KHÁC GẦN VỚI BÀI TOÁN GỐC: Ax^ = p**, với p là b
> project lên Cols space của A C(A). Và điều này cũng có
> nghĩa là p **CHẮC CHẮN NẰM TRONG C(A) ĐỂ TỪ ĐÓ
> Ax^ = p CHẮC CHẮN SOLVABLE**
>
>
>
> Kí hiệu x^ để ám chỉ solution này là của bài toán gần với
> bài toán gốc

<br>

<a id="node-katlkhi"></a>

<p align="center"><kbd><img src="assets/as9mhib99e9.png" width="80%"></kbd></p>

> [!NOTE]
> Nhân tiện gs cũng đang **move từ 1D subspace**, project
> b lên line qua vector a hồi nãy sang **higher dimension**
> subspace - **a plane**

<br>

<a id="node-eb13jz9"></a>

<p align="center"><kbd><img src="assets/f746i5dzlgq.png" width="80%"></kbd></p>

> [!NOTE]
> Và ta cũng sẽ đi **tìm projection
> của b lên plane này**

<br>

<a id="node-ay9m7hh"></a>

<p align="center"><kbd><img src="assets/o57b8um5qq.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đầu tiên gs đề nghị ta **định nghĩa plane**. Thì ta đã
> biết, một plane, cụ thể hơn trong ví dụ đang là 2D plane
> trong R3 Thì nó là **2D subspace của R3** thì nó sẽ có 2
> basis vector (hay nói đúng hơn là **cần 2 vector độc lập**
> **để có một basi**s của subspace này). Ta gọi nó là {a1, a2}
>
>
>
> Gs cũng cho biết **a1 a2 không nhất thiết vuông góc nhau**,
> vì có vô số basis - và như ta còn nhớ **miễn là chúng là hai
> vector độc lập** (khác phương) là đủ thành basis rồi.
>
>
>
> Và plane này là columns space của matrix A. **Đồng nghĩa
> a1, a2 là basis của C(A)** - và ta xài luôn **hai cols của A
> luôn** vì ta đang coi như có hai column độc lập (để C(A) là
> một plane)
>
>
>
> Còn b thì không nằm trong columns space
>
>
>
> #lec15

<br>

<a id="node-tzxgy7w"></a>

<p align="center"><kbd><img src="assets/90qiqj5nwar.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói n**ếu b nằm trong C(A) thì khỏe rồ**i,
> **projection của b lên A sẽ chỉ là chính nó**

<br>

<a id="node-2m11r3f"></a>

<p align="center"><kbd><img src="assets/gszcued21wh.png" width="80%"></kbd></p>

> [!NOTE]
> Nhưng **b không nằm trong C(A)**, nên ta **gọi e là
> khoảng cách từ b với p**. Xong gs cho rằng, từ trực
> giác ta có **e = b-p sẽ perpendicular với plane**
>
>
>
> (giống như e perpendicular với line a hồi nãy)

<br>

<a id="node-lqy8n3u"></a>

<p align="center"><kbd><img src="assets/rf6c2wz2umi.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì như đã nói **p là projection của b trên C(A)** nên **p
> thuộc column space** thành ra **CHẮC CHẮN NÓ LÀ MỘT
> LINEAR COMBINATION CỦA HAI BASIS VECTOR a1, a2**. 
>
>
>
> Và 2 coefficient trong linear combination này CHÍNH LÀ x^: 
> **[x^1, x^2]**
>
>
>
> **p = x^1*a1 +x^2*a2** hay ghi thế này cũng được **p = Ax^**

<br>

<a id="node-w56zol2"></a>

<p align="center"><kbd><img src="assets/qhovmbdcp7n.png" width="80%"></kbd></p>

> [!NOTE]
> Và từ đó cho ta định nghĩa của problem ta đang gỉải quyết:
>
>
>
> Việc tìm projection của b trên C(A) sẽ là **TÌM x^ SAO CHO e
>  = b-p VUÔNG GÓC VỚI C(A)**

<br>

<a id="node-b1uxrli"></a>

<p align="center"><kbd><img src="assets/xzjlhx5mfgh.png" width="80%"></kbd></p>

> [!NOTE]
> Viết lại bài toán đặt ra: tìm x^ sao cho
> **e = b-p = b-Ax^ vuông góc với plane
> C(A)**

<br>

<a id="node-a8lsbxf"></a>

<p align="center"><kbd><img src="assets/j0dflsgzgs.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì **e vuông góc với plane** thì cũng có nghĩa là **nó vuông
> vóc với mọi vector trong plane** (lưu ý plane này là plane của
> một subspace, nó có đi qua gốc O)
>
>
>
> Như vậy **e cũng vuông góc với vector a1, và a2**

<br>

<a id="node-v78hdi2"></a>

<p align="center"><kbd><img src="assets/1a3zkxnfl9z.png" width="80%"></kbd></p>

> [!NOTE]
> Từ đó ta có **dot product của
> e và a1, a2 bằng 0**

<br>

<a id="node-5su5cq6"></a>

<p align="center"><kbd><img src="assets/u59zbvx3kqq.png" width="80%"></kbd></p>

> [!NOTE]
> Xong gs muốn thể hiện hai equation trên dưới dạng matrix
>
>
>
> a1T và a2T - tức là transpose hai columns của A, đương nhiên 
> sẽ có matrix AT, ta có: **AT(b-Ax^) = 0**
>
>
>
> để ý rằng hồi nãy, equation ta có là **aTe = aT(b-Ax^) = 0**
> còn bây giờ ta có hai vector a1 a2 basis của C(A) nên ta
> có : **AT(b-Ax^) = 0**

**🔗 See also:** [linked note](#node-u1oddq3)

<br>

<a id="node-jksn63q"></a>

<p align="center"><kbd><img src="assets/o6y76936t9e.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, gs đề nghị ta, vì bây giờ đã biết về 4 subspace, thì ta
> hãy đưa nó vào đây.
>
>
>
> Đầu tiên đó là, trong AT(b-Ax^) = 0, thì e=b-Ax^ connect với
> subspace nào?
>
>
>
> Me: Đương nhiên V**Ì e LÀ SOLUTION CỦA ATy=0** nên nó
> chính là **nằm trong nullspace của A.T,** HAY CÒN **GỌI LÀ
> LEFT NULLSPACE** **CỦA A**

<br>

<a id="node-skstct8"></a>

<p align="center"><kbd><img src="assets/sotam9ye729.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp equation ATe = 0 có nghĩa là **e nằm trong nullspace
> của AT**, và vì vậy **nó sẽ vuông góc với columns space
> của A** vì bài trước ta đã biết các **cặp subspace
> orthogonal** là (nullspace of A và rowspace of A),
> (nullspace of A.T và columspace of A)

<br>

<a id="node-zyfgurd"></a>

<p align="center"><kbd><img src="assets/mkww9e2rchf.png" width="80%"></kbd></p>

> [!NOTE]
> nhân AT vào (b-Ax^), chuyển ATb qua bên
> phải ta có equation **ATAx^ = ATb**

<br>

<a id="node-sa91oui"></a>

<p align="center"><kbd><img src="assets/dk9fioeezyq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qguoooienz.png" width="80%"></kbd></p>

> [!NOTE]
> gs nhận xét rằng, hồi nãy với 1 dimension, ta có **aTa là
> scalar**, aTb cũng là scalar, và x sẽ là một factor giữa hai con
> số đó. Còn bây giờ ta có **ATA là nxn matrix.**

<br>

<a id="node-73wd1s0"></a>

<p align="center"><kbd><img src="assets/zgzuhl7rj6o.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì câu hỏi là **x^ là gì**, và **projection p là gì**.
>
>
>
> Vậy thì từ **ATAx^ = ATb**, **nhân hai vế cho (ATA)_inv** ta sẽ có 
> **x^** = **(ATA)_invATb**
>
>
>
> Và p = Ax^ (hồi nãy đã nói, p là projection của b lên column
> space của A nên p là linear combination của các A cols hay **p
> = Ax^**)
>
>
>
> Giờ **có x^ rồi** thì thế vào ta có **p = A(ATA)^-1ATb**
>
>
>
> Và gs liên hệ nó với trường hợp 1D hồi nãy, a là vector, thì
> **p = aaT/aTab** còn bây giờ A là matrix thì công thức là vậy.
>
>
>
> Thì nó cũng như nhau thôi vì **1/aTa cũng chính là (aTa)^-1**
>  - có thể coi là inverse của aTa

<br>

<a id="node-e4ftlh2"></a>

<p align="center"><kbd><img src="assets/qkwz0z7286l.png" width="80%"></kbd></p>

> [!NOTE]
> và projection matrix P
> chính là **A(ATA)invAT**

<br>

<a id="node-n45i2ju"></a>

<p align="center"><kbd><img src="assets/w5ikmp5fdzr.png" width="80%"></kbd></p>

> [!NOTE]
> tiếp, gs **GIẢ BỘ RẰNG ta tuân theo rule**:
>
>
>
> (ATA)inv = Ainv(AT)inv
>
>
>
> thì khi đó P sẽ hóa ra AAinv(AT)invAT = I.I = I
>
>
>
> Rõ ràng là **sai**. Và gs cho rằng, ta sai là bởi **A không
> phải là square invertible matrix**, vì như đã nói ban đầu **A
> là LONG & THIN MATRIX** có vài cols nhưng nhiều row.
>
>
>
> **DO ĐÓ Ainv KHÔNG TỒN TẠI.**
>
>
>
> Và **cái rule ở (ATA)inv = Ainv(AT)inv chỉ đúng khi A square
> & invertible matrix** mà thôi

<br>

<a id="node-qiqdgem"></a>

<p align="center"><kbd><img src="assets/epzzqxkf1qt.png" width="80%"></kbd></p>

> [!NOTE]
> gs: Thế thì **nếu A square invertible** thì sao?
>
>
>
> khi đó **cols space của A là gì.**
>
>
>
> -> **Rn**, vì khi đó **mọi n cols và n rows của A đều là
> independent**, chúng sẽ **span toàn bộ Rn**

<br>

<a id="node-b7ooxnt"></a>

<p align="center"><kbd><img src="assets/smo3sa07r4k.png" width="80%"></kbd></p>

> [!NOTE]
> Gs: correct. Thế thì **khi đó**, **Projection** **matrix** (tức là cái
> matrix **giúp làm cái việc projection**) sẽ là gì khi ta
> project b LÊN COLS SPACE CỦA A, MÀ LÚC NÀY LÀ
> THE WHOLE SPACE R^N
>
>
>
> Me: Đương nhiên **b đã nằm trong Rn** rồi mà **giờ project
> nó "lên" Rn** thì đương nhiên **chả cần làm gì**, tức là 
> chỉ cần nhân với Identity matrix -> **P = I**

<br>

<a id="node-v5ijbff"></a>

<p align="center"><kbd><img src="assets/ef1m9lqjrr.png" width="80%"></kbd></p>

> [!NOTE]
> Gs: Đúng vậy, khi A invertible, và **C(A) CHÍNH LÀ TOÀN
> BỘ Rn** thì ta **được phép triển khai như vừa rồi** và **sẽ
> thấy rằng P chính là I**
>
>
>
> Nhưng khi C(A) không phải là R^n mà chỉ là một subspace
> của R^n thì ta không được làm vậy

<br>

<a id="node-ai915ln"></a>

<p align="center"><kbd><img src="assets/g7pm6yp6ys.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, gs cho rằng ta **vẫn sẽ có 2 tính chất của
> projection** matrix P đó là **symmetric**.
>
>
>
> Điều này dễ thấy vì **(ATA)inv**  sẽ symmetric vì **ATA
> symmetric**. Nên [**A(ATA)invAT]T sẽ vẫn bằng
> A(ATA)invAT thôi**

<br>

<a id="node-zgn8vgy"></a>

<p align="center"><kbd><img src="assets/239aumwa2d4.png" width="80%"></kbd></p>

> [!NOTE]
> và **tính chất thứ hai là projection** của projection thì vẫn
> vậy. Và dễ dàng thấy điều này là đúng khi **nhân P với P
> vẫn ra lại P: 
>
>
>
> PP =** A(ATA)inv**AT A(ATA)inv**AT = A(ATA)invAT = P

<br>

<a id="node-bol8nlz"></a>

<p align="center"><kbd><img src="assets/oeicdajkuat.png" width="80%"></kbd></p>

> [!NOTE]
> và gs cho rằng **ta sẽ bắt đầu "xài" matrix P** này, trong các
> bài toán mà ta cần **solve một system of equation** có **rất
> nhiều equation**. Và một application điển hình **chính là bài
> toán LEAST SQUARE**

<br>

<a id="node-kbg3it8"></a>

<p align="center"><kbd><img src="assets/svu78blumj.png" width="80%"></kbd></p>

> [!NOTE]
> Và bài toán là ta cần vẽ, **tìm một đường thẳng** sao cho
> nó **fit được với 3 điểm này**

<br>

<a id="node-fxsorpf"></a>

<p align="center"><kbd><img src="assets/mfrh76oi9ua.png" width="80%"></kbd></p>

> [!NOTE]
> sao cho các
> error nhỏ nhất

<br>

<a id="node-0g08keg"></a>

<p align="center"><kbd><img src="assets/gc8spkz0z2q.png" width="80%"></kbd></p>

> [!NOTE]
> gs đề nghị đầu tiên hãy tìm matrix thể hiện bài toán này.
>
>
>
> Vậy ta gọi đường thẳng cần tìm là **b = C + D*t**
>
>
>
> Vậy dựa vào việc **ta muốn nó đi qua 3 điểm** trên nên
> ta có
>
>
>
> t = 1, b = 1 ->  C + D = 1 
>
>
>
> t = 2, b = 2 -> C + 2D = 2 
>
>
>
> t = 3, b = 2 -> C + 3D = 2
>
>
>
> Đương nhiên nếu system of equation này giải được thì
> ta đã có solution (C, D) tức là xác định được đường
> thẳng đi qua 3 điểm rồi.

<br>

<a id="node-0qt5wk4"></a>

<p align="center"><kbd><img src="assets/2jr0czfudg5.png" width="80%"></kbd></p>

> [!NOTE]
> và cái matrix A ở đây sẽ là matrix 3x2 (cao ốm) có hai
> cols là [1, 1, 1].T và [1 2 3].T,
>
>
>
> hai variable C, D,
>
>
>
> và vector b là [1, 2, 2].T

<br>

<a id="node-a3x13xo"></a>

<p align="center"><kbd><img src="assets/8aqutf2knot.png" width="80%"></kbd></p>

> [!NOTE]
> Và gs cho rằng, đây (Ax=b) như dễ thấy là một equation với no
> solution. Ta sẽ không thể tìm ra C, D
>
>
>
> Nhưng ta sẽ vẫn muốn LÀM TỐT NHẤT CÓ THỂ, mang ý
> nghĩa là tuy không thể vẽ được, tìm được đường thẳng đi qua
> cả 3 điểm, giúp error đều = 0, nhưng ta có thể tìm ra phương
> án tốt nhất có thể BẰNG CÁCH GIẢI MỘT BÀI  TOÁN KHÁC
> GẦN NHẤT VỚI NÓ mà bài toán đó CÓ  SOLUTION
>
>
>
> Đó là **thay vì giải equation Ax = b**, ta sẽ **giải equation ATAx^ =
> ATb**

<br>

<a id="node-g1vtz0j"></a>

<p align="center"><kbd><img src="assets/e4s0ym8heg7.png" width="80%"></kbd></p>

> [!NOTE]
> Khi đó ta sẽ có được **x^**, và từ đó ta có **best projection** 
> Nội dung này sẽ tiếp tục ở lecture 16

<br>

