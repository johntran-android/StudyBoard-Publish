# 1.2.0 Probability theory

📊 **Progress:** `13` Notes | `21` Screenshots

---
<a id="node-ea2dyh1"></a>

<br>

<a id="node-4keka2e"></a>

## Xác suất và tính không chắc

<p align="center"><kbd><img src="assets/vqm58z7jxdg.png" width="80%"></kbd></p>

> [!NOTE]
> Mở đầu gs nói một ý mình nghĩ rằng rất quan trọng. Đó là, một yếu tố
> quan trọng của pattern recognition là tính uncertainty (tính không chắc).
> Và yếu tố này khởi nguồn có thể là từ nhiễu (noise) trong quá trình đo đạc
> (measurement) hoặc cũng có thể là từ việc ta chỉ có một mẫu với số
> lượng hữu hạn. Do đó, đại ý là ta cần lí thuyết xác suất, nó sẽ mang lại
> cho ta những công cụ để định lượng hóa cũng như là thao tác với các
> yếu tố uncertainty này. Để rồi kết hợp với lí thuyết ra quyết định sẽ giúp ta
> đưa ra những hành động, quyết định tối ưu trên cơ sở những thông tin
> mà ta có, kể cả khi nhưng thông tin này là không đầy đủ (incomplete) và
> mơ hồ (ambiguous)

<br>

<a id="node-uooqdjq"></a>

### Thí nghiệm xác suất hộp trái cây

<p align="center"><kbd><img src="assets/0d34g221fog7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/syjs0rcpwdk.png" width="80%"></kbd></p>

> [!NOTE]
> Gs sẽ dùng ví dụ đơn giản này để nói về các khái niệm nền tảng của xác suất:
> Nói ngắn gọn, có 2 hộp xanh đỏ. Hộp đỏ có 2 táo 6 cam, hộp xanh có 3 táo
> 1 cam. Rồi, làm thí nghiệm thế này: Chọn đại một hộp (ngẫu nhiên), rồi bốc đại
> một trái trong đó (dĩ nhiên cũng ngẫu nhiên). xem là trái gì rồi bỏ vào lại. Và
> lặp lại như vậy nhiều lần.
>
>
>
> Đến đây ta sẽ giả sử rằng (suppose) sau nhiều lần làm thì 40% ta chọn hộp đỏ
> 60% chọn hộp xanh (có nghĩa là xác suất chọn hộp đỏ nhỏ hơn). Nhưng khi
> chọn trái trong hộp nào thì xác suất chọn trái nào cũng như nhau (equally likely)

<br>

<a id="node-et53657"></a>

#### Đại lượng ngẫu nhiên và Bernoulli

<p align="center"><kbd><img src="assets/jja8epx4be.png" width="80%"></kbd></p>

> [!NOTE]
> Đến đây là gặp lại một trong những khái niệm nền tảng nhất của xác suất:
> random variable. Cụ thể là nếu quan tâm danh tính của cái hộp được
> chọn, thì nó là một đại lượng mang tính ngẫu nhiên (vì dĩ nhiên là ta đâu
> biết là hộp nào sẽ được chọn trước khi diễn ra hành động thử nghiệm),
> nhưng ta biết nó sẽ mang một trong hai giá trị: xanh hay đỏ.
>
>
>
> Trong xác suất, ta mới đặt nó là biến B, với hai possible value là r, b. Nhờ
> stat110 và Casella đã nhắc đi nhắc lại bản chất của B là MỘT
> FUNCTION: Function này maping một possible outcome s trong original
> sample space Ω với các possible value trong range của B. Trong trường
> hợp này, original sample space là không gian mẫu chứa các kết quả mà
> hành động thực hiện thử nghiệm có thể tạo ra: "chọn hộp, chọn trái" và
> range B= {r,b}. Để rồi nếu s là "chọn hộp xanh, chọn trái ..." thì B(s) = b,
> nếu s là "chọn hộp đỏ, chọn trái .." thì B(s) = r
>
>
>
> Tương tự, danh tính của trái mà ta chọn cũng là biến ngẫu nhiên, đặt là F,
> nó cũng sẽ có hai possible value là {a, o}. Để rồi nếu s là "(chọn hộp ... ,
> chọn trái táo" thì F(s) = a, nếu s là "chon hộp ...m chọn trái cam" thì F(s) =
> o
>
>
>
> Sẵn nói luôn, còn nhớ, rv với hai possible values thì nó chính là Bernoulli
> random variable. Nếu gọi chọn hộp đỏ là một success event, thì B ~
> Bern(0.4) còn F thì cũng là Bern(p). p bằng bao nhiêu thì ta sẽ phải dùng
> LOTP để  tính:
>
>
>
> P(F=a) = P(F=a, B=r) + P(F=a, B=b) (marginalizing joint pmf over mọi p.v
> của B)
>
>
>
> = P(F=a|B=r)P(B=r) + P(F=a|B=b)P(B=b) (conditional probability theorem)

<br>

<a id="node-erus8xi"></a>

##### Định nghĩa và Tiên đề Xác suất

<p align="center"><kbd><img src="assets/5ilo73g8cla.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/21u1paira8c.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp chỗ này gs Bishop thật ra đang định nghĩa xác suất theo trường phái cổ
> điển (Frequentist) khi ông nói ta sẽ define xác suất của một event là tỉ lệ xuất
> hiện của nó khi lặp lại vô hạn lần thử nghiệm. (nếu là trường phái Bayesian,
> xác suất của event sẽ phản ánh độ tin tưởng rằng event sẽ xảy ra)
>
>
>
> Và vì lúc nãy ta nói cho rằng thử nghiệm vô số lần thì 40% trong số đó sẽ
> chọn hộp đỏ, nên P(B=r) = 0.4, và P(B=b) = 0.6.
>
>
>
> Gs nói, theo định nghĩa, nó sẽ phải là con số trong [0,1]. Dễ hiểu là với cách
> định nghĩa này, thì nó là con số tỉ lệ, nên dĩ nhiên nó phải không âm và ≤ 1.
>
>
>
> mình nhớ, đây thực ra là từ Axiom 1,2 (2 trong 3 tiên đề của xác suất) : xác
> suất của một biến cố P(A) không âm với mọi A ∈ Ω và P(Ω) = 1.
>
>
>
> Câu cuối, gs nói nếu các event loại trừ lẫn nhau (mutually exclusive) và
> chứa mọi possible outcomes thì tổng xác suất sẽ = 1. Là sao?
>
>
>
> À thì đây chính là nói khi đó (B = r) và (B = p) sẽ làm thành một partition:
>
>
>
> (B = r) U (B = p) = Ω, (B = r) ∩ (B = b) = ∅ thì khi đó:
>
>
>
> P[(B = r) U (B = p)] = P(Ω) = 1 theo axiom 2.
>
>
>
> mà vế trái, là xác suất của một union của các disjoint event, nên theo axiom
> 3, nó sẽ là tổng xác suất đơn lẻ: 
>
>
>
> P[(B = r) U (B = p)] = P(B = r) + P(B = b)
>
>
>
> Do đó P(B = r) + P(B = b) = 1

<br>

<a id="node-spyv72h"></a>

###### Tiên đề xác suất

<p align="center"><kbd><img src="assets/ordj48vrf7.png" width="80%"></kbd></p>

> [!NOTE]
> Definition 1.2.4 sách Casella
> nêu 3 tiên đề xác suất

<br>

<a id="node-f9tubgx"></a>

###### Quy tắc Sum Product Xác suất

<p align="center"><kbd><img src="assets/llcwz6rbdk.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này tác giả đặt câu hỏi, làm sao ta có thể tính được xác suất của việc
> bốc được một trái táo. Hoặc một câu hỏi khác là nếu đã chọn trái cam thì xác
> xuất ta đã chọn hộp xanh là bao nhiêu.
>
>
>
> Thì ông cho rằng, hai cái rule quan trọng của xác suất là sum rule và product
> rule sẽ giúp ta trả lời hai câu hỏi này

<br>

<a id="node-zuag6aa"></a>

###### Quy tắc xác suất cơ bản

<p align="center"><kbd><img src="assets/36upmvnjyrt.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ul10en6rtr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/tf2z2xcfq6i.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là ông dùng ví dụ này để ta hiểu về sum rule và product rule: Cho X, Y là hai rvs
> với possible values là x1,....xM, và y1,...yL. Thực hiện thử nghiệm nào đó để có hai gía
> trị cụ thể của X, Y, và làm vậy N lần. (Có thể hình dung ném N viên bi vào một cái bảng
> có L cột và M hàng. Bi rơi vào ô ij, thì tức là X = xi, Y = yj).
>
>
>
> Trong đó gọi ci là số bi rơi vào hàng i (X = xi) (ví dụ c2 là số lần X ra bằng x2),  rj là số bi
> rơi vào cột j (số lần Y = yj) Và nij là số viên bi rơi vào hàng i, cột j (X = xi, Y = yj)
>
>
>
> Thế thì câu hỏi như hồi nãy đặt ra là ta muốn tính xác suất mà khơi khơi bốc được trái
> táo (ko biết bốc hộp nào), cũng chính là muốn tính P(B = a)
>
>
>
> Thì ở đây, nó tương ứng với việc ta đặt câu hỏi tính xác suất X = xi.
>
>
>
> Thế thì trong sách, gs Bishop dùng lập luận theo kiểu này, nhưng trước tiên mình có thể
> lập luận theo lối đã học trong Casella
>
>
>
> Về mặt bản chất như đã học trong Casella + Stat110:
>
>
>
> P(X = xi) = P({s ∈ Ω: X(s) = xi}), ý nghĩa tổng xác suất các biến cố (possible outcome)
> trong không gian mẫu mà map với X ra xi.
>
>
>
> Giờ xét cái tập {s ∈ Ω: X(s) = xi},
>
>
>
> Dĩ nhiên nó là tập con của Ω: {s ∈ Ω: X(s) = xi} ⊂ Ω
>
>
>
> Theo lí thuyết tập hợp: nếu A ⊂ B ⇨ A ∩ B = A
>
>
>
> ⇨ {s ∈ Ω: X(s) = xi} = {s ∈ Ω: X(s) = xi} ∩ Ω
>
>
>
> Thể hiện Ω = U{mọi possible value yj} {s ∈ Ω: Y(s) = yj}
>
>
>
> ⇨ {s ∈ Ω: X(s) = xi} ∩ Ω = {s ∈ Ω: X(s) = xi} ∩ [U{mọi possible value yj} {s ∈ Ω: Y(s) = yj}]
>
>
>
> Dùng distributive law: A ∩ (B U C) = (A ∩ B) U (A ∩ C):
>
>
>
> .. = U{mọi possible value yj} [{s ∈ Ω: X(s) = xi} ∩ {s ∈ Ω: Y(s) = yj}]
>
>
>
> = U{mọi possible value yj} {s ∈ Ω: X(s) = xi, Y(s) = yj}
>
>
>
> Viết lại {s ∈ Ω: X(s) = xi} = U{mọi possible value yj} {s ∈ Ω: X(s) = xi, Y(s) = yj}
>
>
>
> ⇨ P[{s ∈ Ω: X(s) = xi}] = P{U{mọi possible value yj} {s ∈ Ω: X(s) = xi, Y(s) = yj}]
>
>
>
> Vế phải, là xác suất của union của các disjoint events, nên theo Axiom 3:
>
>
>
> = Σ_{mọi possible value yj} P({s ∈ Ω: X(s) = xi, Y(s) = yj})
>
>
>
> Viết lại P[{s ∈ Ω: X(s) = xi}] = Σ_{mọi possible value yj} P({s ∈ Ω: X(s) = xi, Y(s) = yj})
>
>
>
> Và cái này chính là:
>
>
>
> P(X = xi) = Σj=1:L P(X = xi, Y = yj), là sum rule, hoặc gọi là marginalize joint pmf trên mọi
> possible value của Y, cũng là lí do ta P(X = xi) gọi là marginal distribution của X
>
>
>
> ====
>
>
>
> Còn trong sách gs Bishop đại khái là giải thích theo một cái kiểu rất thực nghiệm:
>
>
>
> Là nếu gọi nij là số viên bi (trong N viên bi) rơi vào ô X=xi, Y=yj, thì P(X=xi,Y=yj) = nij / N
> với điều kiện ta **phải ngầm hiểu là N → inf**.
>
>
>
> Rồi, tương tự ci là số viên bi rơi vào ô X=xi, thì P(X=xi) = ci / N (cũng ngầm hiểu N →
> inf)
>
>
>
> thì ci = Σj nij ⇨ P(X=xi) = ci / N = Σj nij / N = Σj P(X=xi, Y=yj)
>
>
>
> ⇨ P(X=xi) = Σj P(X=xi, Y=yj)
>
>
>
> Và ông nói cái này chính là sum rule của xác suất. (còn mình thì nhìn nó theo góc nhìn
> của stat110, Casella, để nói nó chính là **marginalizing joint distribution của X, Y để có
> marginal distribution  của X**)
>
>
>
> Tương tự, với P(X = xi, Y = yj) thì nó sẽ là nij / N (N → inf), và = (nij / ci) (ci / N)
>
>
>
> Thì nij / ci là: số bi rơi vào hàng i cột j trong tổng số bi rơi vào hàng i. Và ông cho rằng
> nó chính là P(Y = yj | X = xi)
>
>
>
> ⇨ P(X = xi, Y = yj) = P(Y = yj|X = xi)P(X = xi) và gs nói đây là minh họa của product rule.
>
>
>
> Còn mình theo phong cách Casella, Stat110 thì thấy đây chỉ là **định lí rút ra từ định
> nghĩa của conditional probability**: Định nghĩa của conditional probability P(A|B) = P(A,B) / P(B) 
>
>
>
> ⇨ P(A,B) = P(A|B)P(B)
>
>
>
> Nói chung, sách diễn giải này đậm tính trực giác, và chỉ giúp dễ hiểu, chứ ko mang tính
> tổng quát như cách diễn giải theo phong cách Casella

<br>

<a id="node-amgfpbh"></a>

###### Quy ước kí hiệu Bishop

<p align="center"><kbd><img src="assets/94fl88qy9k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/yods2zrvpiq.png" width="80%"></kbd></p>

> [!NOTE]
> Gs quy ước một chút về kí hiệu, p(B) sẽ chỉ distribution của B, p(r) sẽ chỉ  giá trị
> xác suất tại B = r.
>
>
>
> Và hai rule của xác suất sẽ thể hiện bởi:
>
>
>
> p(X) = ΣY p(X, Y)
>
>
>
> và p(X, Y) = p(Y|X)p(X)
>
>
>
> Đối chiếu với stat110, Casella:
>
>
>
> Thì đây là fX(x) = Σy fX,Y(x,y), cũng là marginalizing joint pdf/pmf, và cũng là,
> bản chất  chính là LOTP
>
>
>
> Và fX,Y(x,y) = fX|Y(x|y)fX(x)
>
>
>
> Chính là dựa định nghĩa của conditional probability: P(A|B) = P(A,B) / P(B) ⇨
> P(A,B) = P(A|B)P(B), cái này gs Joe Blizstein gọi nó là Conditional probability
> theorem.
>
>
>
> Tóm lại mình nên hiểu: **Chỗ này ông Bishop sẽ không theo lối kí hiệu chặt chẽ
> của toán thống kê.**
>
>
>
> Vì nếu theo đó, phải ghi rõ ra:
>
>
>
> Biến rời rạc:
>
>
>
> P(X=x) = Σy P(X=x, Y=y),
>
>
>
> P(X=x, Y=y) = P(X=x|Y=y)P(Y=y)
>
>
>
> Biến liên tục:
>
>
>
> fX(x) = ∫_range Y fX,Y(x,y)dy
>
>
>
> fX,Y(x,y) = fX|Y(x|y)fY(y)
>
>
>
> Còn ở đây, gs Bishop đặt lại quy định về kí hiệu:
>
>
>
> p(X) sẽ chỉ **HÀM DISTRIBUTION CỦA** X, (pmf hoặc pdf)
>
>
>
> p(x) sẽ là **GÍA TRỊ HÀM PMF/PDF CỦA X TẠI x
>
>
>
> Nếu ko nhớ convention này của gs Bishop thì rất dễ lú sau này**

<br>

<a id="node-uh641z5"></a>

###### Định lý Bayes và Chuẩn hóa

<p align="center"><kbd><img src="assets/ge7ca7c8ysf.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây nói về Bayes' theorem, stat110 ta đã biết nó chỉ là hệ quả của  định
> nghĩa về conditional probability.
>
>
>
> P(A|B) = P(A,B)/P(B) (định nghĩa conditional probability)
>
>
>
> ⇨ P(A,B) = P(A|B)P(B). Mà P(A,B) = P(B,A) = P(B|A)P(A)
>
>
>
> ⇨ Bayes theorem.
>
>
>
> Nhưng cái ý cuối là quan trọng: nói rằng cái mẫu số có thể coi như normalizing
> constant để đảm bảo tổng xác suất điều kiện = 1.
>
>
>
> Cái này có một case mà mình sẽ thấy hữu ích. Ví dụ như khi xây dựng
> posterior distribution của θ: π(θ|**x**), ta sẽ dùng Bayes theorem:
>
>
>
> π(θ|**x**) = f(**x**|θ) π(θ) / f(**x**)
>
>
>
> Khi ta đã có priori, π(θ), và joint distribution của random sample f(**x**|θ), thì
> mình sẽ cần care f(**x**), mà chỉ cần đối xử với nó như constant nào đó đảm
> bảo rằng khi sum π(θ|**x**) trên range của θ thì nó sẽ ra 1, nói cách khác,
> f(**x**) sẽ là constant nào đó đảm bảo π(θ|x) là một valid pdf/pmf, gọi là
> normalizing constant.
>
>
>
> Dĩ nhiên, ta còn nhớ định nghĩa của likelihood function L(θ|**x**) được định
> nghĩa chính là = f(**x**|θ), tức joint distribution của **X** tại overseved value **x**.

<br>

<a id="node-jfoiqx1"></a>

###### Mô hình hóa phân phối dữ liệu

<p align="center"><kbd><img src="assets/v2smjzh290f.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3vr83ycirjz.png" width="80%"></kbd></p>

> [!NOTE]
> Gs Bishop cho mình hình ảnh minh họa joint distribution của hai rv X, Y.
>
>
>
> Cũng ko có gì khó hiểu, chỉ lưu ý là: Cái này KHÔNG PHẢI LÀ hình ảnh của marginal distribution của X, Y.
>
>
>
> NÓ CHỈ LÀ GIÚP CHO TA MỘT Ý NIỆM NÀO ĐÓ VỀ DISTRIBUTION CỦA X, Y với N hữu hạn mà thôi, (gọi là **EMPIRICAL DISTRIBUTION**) vì để có distribution của X, Y, ta phải xét số lần thực hiện thử nghiệm N → infinity.
>
>
>
> (Và đây cũng là thứ mình không thấy nói trong Stat110, Casella)
>
>
>
> Để rồi sau đó, gs Bishop nói một ý quan trọng: việc **MÔ HÌNH HÓA DISTRIBUTION TỪ DỮ LIỆU (HỮU HẠN) ĐÓNG VAI TRÒ LÀ TRÁI TIM CỦA PATTERN RECOGNITION**: Câu nói này liên quan trực tiếp đến những gì đã học trong Casella: Ví dụ trong bài toán point estimator, cái ta làm chính là dựa trên giá trị quan sát được của sample **X**, để xây dựng một statistic δ(**X**) làm point estimator cho θ. Nó chính là ý gs Bishop nói ở đây.

**🔗 See also:** [Histogram Density Estimation](./25_non_parametric_model.md#node-qmfgqko)

<br>

<a id="node-93p43r7"></a>

###### Bài toán xác suất hộp trái cây

<p align="center"><kbd><img src="assets/xcpezale6nm.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/urdvn09ykqb.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/khtle8a1xyc.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này chỉ là ông quay lại áp mấy cái khái niệm, rule đã giới thiệu vào lại
> hai câu hỏi của bài táon hộp xanh, đỏ, cam táo. Ko có gì khó. Chỉ cần phải
> nhớ là khi nói xác suất của một event ở đây, ta đang ngầm hiểu nhiều thứ:
> Số experiment N → infinity. (đó là lí do mà gs phải nói rõ đề bài là, thực hiện
> nhiều lần thì 40% kết quả ra chọn hộp đỏ, 60% ra chọn hộp xanh).
>
>
>
> Do đó ta mới có quyền nói p(B = r) = 0.4, p(B = b) = 0.6
>
>
>
> Rồi, trong hộp đỏ có 1 táo 3 cam, thì cũng phải ngầm hiểu là vì đã nói khi thò
> tay vào chọn một trái thì việc bốc trúng trái nào là hoàn toàn ngẫu nhiên.
> Nên khi thực hiện vô số lần bốc, sẽ có 25% trong số đó sẽ chọn được táo,
> và 75% còn lại chọn được cam. Chứ ko phải là chỉ vì trong hộp có 4 trái trong
> đó có 1 táo, thì sẽ đồng nghĩa là xác suất bốc được táo khi đã chọn hộp đỏ 
> là 1/4 liền.
>
>
>
> Rồi, khi đó ta sẽ dùng các rule để tính xác suất chọn được táo (marginal)
>
>
>
> cũng như dùng Bayes rule để tính xác suất chọn hộp đỏ khi biết đã bốc ra cam

<br>

<a id="node-q0e9cty"></a>

###### Cập nhật niềm tin Bayes

<p align="center"><kbd><img src="assets/ztb3gjyldj.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này gs cho ta một cách hiểu quan trọng về Bayes theorem: Ta thấy
> p(B=r) = 4/10. Còn p(B=r|F=o) = 2/3.
>
>
>
> Nó phản ánh: Khi chưa có thông tin quan sát được là bốc được quả gì, thì
> niềm tin của việc ta chọn được hộp đỏ chỉ là 0.4, tức là, dựa trên dữ liệu đề
> bài cho nói rằng, khi thực hiện thử nghiệm vô số lần thì xác suất chọn được
> hộp đỏ chỉ là 40%.
>
>
>
> Nhưng một khi biết được ta đã chọn được quả cam, thì con số 2/3 nó phản
> ánh rất đúng một thực tế là: trong hai cái hộp thì hộp đỏ có nhiều cam hơn.
> Do đó, nếu ta biết điều này, và biết rằng đã bốc được cam, thì niềm tin của ta
> vào việc đã chọn được hộp đỏ sẽ tăng lên.
>
>
>
> Từ đó, ta có prior distribution của B chính là P(B) còn P(B|F) gọi là posterior
> distribution.
>
>
>
> Trong casella, như nãy đã nhắc lại, prior distribution của θ là π(θ) và
> posterior distribution của θ là π(θ|**x**)

<br>

<a id="node-qz6gnns"></a>

###### Biến cố độc lập, Biến ngẫu nhiên

<p align="center"><kbd><img src="assets/18c531iib.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng là gs nói qua khái niệm independent event và random 
> variable.

<br>

