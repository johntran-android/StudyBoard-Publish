# 4.4 Hierarchical Model &
mixture Distribution

📊 **Progress:** `11` Notes | `19` Screenshots

---
<a id="node-s5hrhdz"></a>

## 4.4 Hierarchical Model &
mixture Distribution

**🔗 See also:** [Mô hình phân cấp](#node-lytbbql) · [A0_casella](#node-yf9bh13)

<br>

<a id="node-lytbbql"></a>

## Mô hình phân cấp

<p align="center"><kbd><img src="assets/50cssb1aoan.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hdgvgc50t5l.png" width="80%"></kbd></p>

> [!NOTE]
> ở đây ta sẽ được biết khái niệm mới, đại khái là ví dụ như ta có bối cảnh là
> con gà (hay đàn gà) đẻ trứng, số trứng đẻ ra bao nhiêu thì ko biết (tức là nó
> là một random variable), đặt random variable cho cái này là Y. Thì thông
> thường ta sẽ assume nó là một Pois(λ) rv.
>
>
>
> Thế thì, giả sử các trứng đều có tỉ lệ nở là p và độc lập nhau, khi đó dễ thấy
> việc trứng có nở hay ko là một Bern(p) rv và ta có một chuỗi các Bern(p) iid
> và khi ta quan tâm tổng số trứng nở (dĩ nhiên cũng là rv) thì nó chính là bối
> cảnh của Binomial(Y, p) Để rồi ta sẽ "ghi như vầy":
>
>
>
> X|Y ~ binomial(Y, p) và Y ~ Pois(λ)
>
>
>
> Đây chính là một HIERARCHICAL MODEL, mang ý nghĩa là Y là một
> Pois(λ) rv, và nếu biết giá trị của Y thì X|Y là một binomial(Y, p) rvs
>
>
>
> Thế thì ƯU ĐIỂM CỦA CÁI NÀY LÀ NÓ GIÚP THỂ HIỆN MỘT QUÁ TRÌNH
> PHỨC TẠP BỞI MỘT CHUỖI CÁC MODEL ĐƠN GIẢN.

**🔗 See also:** [4.4 Hierarchical Model &
mixture Distribution](#node-s5hrhdz) · [Phân phối Poisson của X](#node-xtkaa4b)

<br>

<a id="node-xtkaa4b"></a>

### Phân phối Poisson của X

<p align="center"><kbd><img src="assets/k4x6xpo8ag.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vxqvby5hvv.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi k0 có gì khó hiểu, P(X = x) ta sẽ marginalizing over mọi possible value
> của X, Y:
>
>
>
> P(X = x) = Σ {mọi possible value y của Y} P(X = x, Y = y) mà Y như đã nói,
> là một Pois(λ), pmf = e^-λ λ^y / y!, với các y = 0,1,2...inf (again, đây là
> support set)
>
>
>
> ⇨ P(X = x) = Σy=0,1..inf  P(X = x, Y = y)
>
>
>
> Dùng theorem conditional event probability P(X = x, Y = y)
>
>
>
> = P(X = x | Y = y)P(Y = y)
>
>
>
> P(Y = y) chính là pmf của Y evaluate tại y: e^-λ λ^y / y!
>
>
>
> P(X = x | Y = y) thì như đã nói, X|Y ~ binomial(Y, p), hay X|Y=y ~ Binomial(y, p)
> ⇨ P(X = x | Y = y) = pmf của bin(y, p) evaluate tại x:
>
>
>
> (pmf của bin(n, p) f(k) = (n choose k)p^k(1-p)^(n-k))
>
>
>
> = (y choose x)p^x(1-p)^(y-x) [e^-λ λ^y / y!]
>
>
>
> ⇨ P(X = x) = **Σy=0,1..inf (y choose x)p^x(1-p)^(y-x) e^-λ λ^y / y!**
>
>
>
> Thu gọn cái này: (Làm sau) 
>
> ta sẽ có P(X=x) = **(λp)^x e^-(λp) / x! CHO THẤY X CHÍNH LÀ Pois(λp)
>
>
>
> Nhờ vậy ta biết ngay EX = λp (EX của Pois(λ) = λ)**
>
>
>
> và câu trả lời cho câu hỏi là trung bình có bao nhiêu trứng nở sẽ là λp

**🔗 See also:** [Mô hình phân cấp](#node-lytbbql) · [Luật Kỳ Vọng Toàn Phần](#node-3aseb34)

<br>

<a id="node-3aseb34"></a>

#### Luật Kỳ Vọng Toàn Phần

<p align="center"><kbd><img src="assets/k1exmnxr3e.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/po71v6g3yp.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bài trước ta đã biết E(X|Y) là random variable trong khi đó
> E(X|y) là function của y
>
>
>
> Vì sao, vì E(X|y) mang ý nghĩa là với Y =y, thì EX là bao nhiêu. cách tính
> vẫn là weight Σ mọi possible value của X với Y = y
>
>
>
> = ∫{mọi possible value xcủa X với Y=y} xfX|Y(x|y)
>
>
>
> Đây là hàm số theo y.
>
>
>
> Vậy với các giá trị khác nhau của Y thì hàm số này ra các giá trị khác
> nhau, nên nó cũng là một random variable. Hoặc nói cách khác, E(X|Y)
> là ta apply hàm số này cho random variable Y, nên dĩ nhiên được một rv
> mới
>
>
>
> Thế thì có theorem EX = E[E(X|Y)] chứng minh rất đơn giản:
>
>
>
> Trong sách làm với continuous, mình thử làm discrete
>
>
>
> EX = Σ{mọi x} xP(X=x)
>
>
>
> = Σ{mọi x} xΣ{mọi y} P(X=x, Y=y)    | P(X=x) = Σ{mọi y} P(X=x, Y=y)
>
>
>
> = Σ{mọi x} xΣ{mọi y} P(X=x|Y=y)P(Y=y) | conditional prob thoerem
>
>
>
> = Σ{mọi x} Σ{mọi y} xP(X=x|Y=y)P(Y=y) | có quyền đổi chỗ hai tổng
>
>
>
> = Σ{mọi y} P(Y=y) Σ{mọi x} xP(X=x|Y=y) | P(Y=y) không phụ thuộc x, đưa ra
>
>
>
> = Σ{mọi y} P(Y=y)E(X|y)
>
>
>
> = Σ{mọi y} E(X|y)P(Y=y) và như đã nói E(X|y) là function theo y, gọi là g(y)
>
>
>
> thì cái đang có ở đây chính là = Σ{mọi y} g(y)P(Y=y) và nó chính là E(g(Y))
>
>
>
> = E[E(X|Y)]
>
>
>
> Đã hiểu chứng minh này thì ta hiểu mấy chữ E này khác nhau chỗ nào.
>
>
>
> Vậy thì áp dụng theorem này EX cần tính sẽ = E[E(X|Y)] mà E(X|Y) là
> expected value của X|Y - là một bin(Y,p) ⇨ E(X|Y) = Yp
>
>
>
> ⇨ E[E(X|Y)] = E[Yp] 
>
>
>
> = pEY (linearity) 
>
>
>
> = pλ (do Y ~ Pois(λ) KẾT QUẢ CŨNG RA NHƯ HỒI NÃY KHI TA KIỂU NHƯ
> CHỨNG MINH X ~ POIS(λp)

**🔗 See also:** [Phân phối Poisson của X](#node-xtkaa4b) · [Định nghĩa phân phối hỗn hợp](#node-ux7w713)

<br>

<a id="node-ux7w713"></a>

##### Định nghĩa phân phối hỗn hợp

<p align="center"><kbd><img src="assets/yj9qtkrzuho.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là cái TERM MIXTURE DISTRIBUTION trong tựa đề phần này ám chỉ
> một DISTRIBUTION HIỆN LÊN TỪ CẤU TRÚC PHÂN TẦNG, (ví dụ như khi ta
> tìm ra rằng X sẽ là Pois(λp) nếu như X|Y ~ Bin(Y, p) (đọc là khi biết giá trị của
> Y thì X là một binomial (y,p), và Y là một Pois(λ))
>
>
>
> và tác giả nói rằng dù ko có định nghĩa chính thức về cái này nhưng ta sẽ chấp
> nhận định nghĩa rằngTA SẼ NÓI RẰNG X CÓ MIXTURE DISTRIBUTION NẾU
> NHƯ DISTRIBUTION CỦA NÓ PHỤ THUỘC VÀO MỘT ĐẠI LƯỢNG KHÁC
> MÀ BẢN THÂN ĐẠI LƯỢNG ĐÓ CŨNG CÓ DISTRIBUTION
>
>
>
> (Ví dụ như X có distribution Bin(Y,p), tức phụ thuộc vào đại lương Y, mà bản
> thân Y cũng có distribution (Pois(λ))
>
>
>
> Thế thì gs nói rằng ko lí do gì mà CHỈ CÓ 2 TẦNG, nhưng sẽ dễ hơn nếu ta
> xem xét một hệ nhiều tầng theo từng chuỗi 2 tầng

**🔗 See also:** [Luật Kỳ Vọng Toàn Phần](#node-3aseb34) · [Mô hình phân tầng](#node-d9y0usw)

<br>

<a id="node-d9y0usw"></a>

- **Mô hình phân tầng**

<p align="center"><kbd><img src="assets/z4kvhhjt1k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gbyebewkpss.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/lzgxnyqh26r.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi ví dụ này đại khái giả sử bối cảnh đẻ trứng (nãy mình dùng gà đẻ, thật ra
> ở đây đang nói về côn trùng) để cho rằng số trứng đẻ ra (cũng là random
> variable) sẽ ~ Pois(λ), thì bây giờ cho rằng ta sẽ bắt đầu với việc CHỌN MỘT
> CON GÀ MÁI TỪ NHIỀU GIỐNG GÀ KHÁC NHAU. Để rồi số trứng đẻ ra còn
> phụ thuôc  vào giống gà nữa.
>
>
>
> Có nghĩa là số trứng đẻ ra Y  ko phải là pois(λ) với λ cố định đã biết, mà nó
> cũng là random variable, phụ thuộc vào việc con gà mái thuộc giống nào
> được chọn (giả định là mỗi giống gà có tỉ lệ đẻ khác nhau)
>
>
>
> Lúc này cấu trúc phân tầng sẽ như sau:
>
>
>
> X|Y ~ binomial(Y, p) | biết Y thì số trứng nở sẽ ~ bin(Y,p)
>
>
>
> Y ~ Pois(Λ) | biết Λ thì tổng số trứng đẻ ra sẽ là một Pois(Λ)
>
>
>
> Λ ~ expo(β) và bản thân Λ sẽ ~ expo(β), mà giá trị của nó đến từ việc chọn
> một gà mái ngẫu nhiên
>
>
>
> Thế thì khi đó EX = E(EX|Y) = E(pY) = pEY như kết quả trên
>
>
>
> thì đến đây EY = E(EY|Λ) (vì distribution của Y sẽ phụ thuộc Λ
>
>
>
> = E(Λ) | vì E(Y|Λ) là expected value của một Pois(Λ), nên expected của nó là
> Λ
>
>
>
> ⇨ EX = pE(EY|Λ) =  pE(Λ)
>
>
>
> = pβ   | Do expected value của một  rv Λ ~ expo(β) = β
>
>
>
> ====
>
>
>
> Gs nói thêm trong ví dụ vừa rồi, mình có một mô hình (hierarchy model) mà
> trong đó vừa có cả discrete rv (X ~ binomial(Y, p), Y ~ Pois(Λ)) vừa có cả
> continuous rv (Λ ~ Expo(β)) nhưng ko vấn đề gì. Chỉ cần nhớ khi tính
> expected value hay marginalizing  thì với discrete rv ta sẽ Σ , còn continuous
> rv ta sẽ ∫

**🔗 See also:** [Định nghĩa phân phối hỗn hợp](#node-ux7w713) · [Mô hình ba cấp thành hai](#node-coenx9x)

<br>

<a id="node-coenx9x"></a>

- **Mô hình ba cấp thành hai**

<p align="center"><kbd><img src="assets/i06wzuozc0e.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo, đại khái là một mô hình 3 cấp có thể được chuyển thành mô
> hình 2 cấp bằng cách kết hợp hai cấp dưới.
>
>
>
> Ví dụ như ở đây Y ~ Pois(Λ), Λ ~ Expo(β), ta có thể kết hợp hai cấp
> này lại (cơ bản là với việc nếu biết giá trị Λ vốn là một Expo(β) rv, thì
> Y sẽ là một Pois(Λ) rv, thì bản thân nó (marginal) là một rv gì)
>
>
>
> Tức là ta tìm marginal pmf của Y:
>
>
>
> fY(y) = P(Y = y) bằng cách marginalizing joint distribution của Y, Λ over 
> mọi possible value của Λ: 
>
>
>
> Mà Λ ~ Expo(β) ⇨ support set của Λ là (0:inf) (nhắc lại ko thừa, thường
> thì ta có convention là nói về possible value của rv là nói về tập mà trong
> đó pdf/pmf dương (tức support set), nhưng cũng có sách nói khác, rằng
> possible value cũng có thể là giá trị mà pdf/pmf = 0. Nhưng dù thế nào,
> thì khi marginalizing over mọi possible value, thì dễ thấy rằng ta cũng sẽ
> chỉ tính những cái mà pdf/pmf dương. Nói cách khác, cũng chỉ là marginalizing
> trên support set.
>
>
>
> Vậy P(Y = y) = ∫0:inf fY,Λ(y,λ)dλ.
>
>
>
> Tất nhiên ta ko biết fY,Λ(y,λ) là cái gì nhưng có thể dùng conditional theorem:
>
>
>
> = ∫0:inf fY|Λ(y|λ)fΛ(λ) dλ.  
>
>
>
> fY|Λ(y|λ) là gì, như đã nói, NẾU BIẾT GIÁ TRỊ CỤ THỂ λ CỦA Λ, thì Y|Λ  ~ Pois(Λ)
> nên fY|Λ(y|λ) là pmf của Pois(λ) = e^-λ λ^y / y!
>
>
>
> Còn fΛ(λ) là marginal pdf của Λ, là một Expo(β), pdf fΛ(λ) = (1/β) e^-λ/β 
>
>
>
> ⇨ P(Y=y) = ∫0:inf [e^-λ λ^y / y!] (1/β) e^-λ/β dλ
>
>
>
> = (1/βy!) ∫0:inf e^-λ λ^y e^-λ/β dλ | đưa /βy! ko dính tới y ra ngoài
>
>
>
> = (1/βy!) ∫0:inf e^(-λ-λ/β) λ^y dλ 
>
>
>
> = (1/βy!) ∫0:inf e^-λ(1+1/β) λ^y dλ 
>
>
>
> = (1/βy!) ∫0:inf λ^y e^-λ(1+β^-1) dλ 
>
>
>
> Tới đây xem lại pdf của X ~ Γ(α, β) fX(x) = [1/Γ(α)β^α] x^(α-1)e^-x/β 
>
>
>
> nên λ^y có dạng của x^(α-1)
>
>
>
> e^-λ(1+β^-1) có dạng của e^-x/β 
>
>
>
> ⇨ ở đây ta có  e^-λ(1+β^-1) là kernel của Γ(y+1, 1/(1+β^-1)) 
>
>
>
> = Γ(y+1, 1/(1+1/β)) = Γ(y+1, β/(β+1))
>
>
>
> nên bằng cách nhân thêm và chia bớt cho normalizing constant:
>
>
>
> Γ(y+1) [β/(β+1)]^(y+1)  / Γ(y+1) [β/(β+1)]^(y+1) 
>
>
>
> ⇨ Γ(y+1) [β/(β+1)]^(y+1) ∫0:inf [1/ Γ(y+1) [β/(β+1)]^(y+1) ] λ^y e^-λ(1+β^-1) dλ 
>
>
>
> = Γ(y+1) [β/(β+1)]^(y+1)
>
>
>
> Và cộng với 1/βy! ở trước nữa ta có kết quả là
>
>
>
> P(Y=y) = (1/βy!) Γ(y+1) [β/(β+1)]^(y+1)    đây là như trong sách rồi, 
>
>
>
> chỉ là β/(β+1) = 1/(1+β^-1) thôi
>
>
>
> Thu gọn: (1/βy!) Γ(y+1) [β/(β+1)]^(y+1)
>
>
>
> Dùng identity: Γ(n) = (n-1)! 
>
>
>
> = (1/β**y!**) **y!** [β/(β+1)]^y [β/(β+1)]
>
>
>
> = (1/**β**) [1/(1+β^-1)]^y [**β**/(β+1)]
>
>
>
> = (1/1) [1/(1+β^-1)]^y [1/(β+1)]
>
>
>
> =  [1/(1+β^-1)]^y [1/(β+1)]
>
>
>
> = **[1/(β+1)] [1/(1+β^-1)]^y 
>
>
>
> Và đây chính là pmf của NEGATIVE BINOMIAL p = 1/(1+β) r = 1
>
>
>
> Do đó Y ~ negative binomial p = 1/(1+β) r = 1
>
>
>
> Và mô hình 3 tầng này cũng chính là mô hình 2 tầng: X ~ binomial(Y, p) 
>
>
>
> Y ~ negative bino(p = 1/(1+β) r = 1)
>
>
>
> NHƯNG DÙNG MÔ HÌNH 3 TẦNG THÌ DỄ HIỂU HƠN**

**🔗 See also:** [Mô hình phân tầng](#node-d9y0usw) · [Hỗn hợp Poisson-Gamma](#node-f2k0dv8)

<br>

<a id="node-f2k0dv8"></a>

- **Hỗn hợp Poisson-Gamma**

<p align="center"><kbd><img src="assets/pcd4od1maq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/uir7x1bb3h.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là khái quát hơn ví dụ vừa rồi Y ~ Pois(Λ), Λ ~ Expo(β) thì ta có
> Y ~ Pois(Λ), Λ ~ gamma(α, β)
>
>
>
> (Expo(β) chính là Γ(α, β) với α = 1)

**🔗 See also:** [Mô hình ba cấp thành hai](#node-coenx9x) · [Noncentral Chi-squared và mô hình tầng](#node-jaoa4am)

<br>

<a id="node-jaoa4am"></a>

- **Noncentral Chi-squared và mô hình tầng**

<p align="center"><kbd><img src="assets/fcam6jaascw.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/7knlk2dgqs5.png" width="80%"></kbd></p>

> [!NOTE]
> QUAY LẠI SAU,
>
>
>
> Nhưng đại ý là, một ví dụ minh họa cho việc mô hình phân tầng có ngoài tác
> dụng giúp ta hiểu hơn (kiểu như hiểu ví dụ như biết giá trị của Λ thì Y là rv
> có distrib gì, rồi biết giá trị của Y thì X là rv distrib gì) thì nó còn giúp đơn giản
> hóa tính toán.
>
>
>
> Ở đây đại khái là nói về một phân phối xác suất cũng hay gặp trong statistic
> là NONCENTRAL CHI SQUARED.
>
>
>
> pdf của nó nhìn rất phức tạp, nhưng nhìn kĩ vào sẽ thấy bản chất nó là một
> mô hình 2 tầng:
>
>
>
> X|K ~ Chi-Square tham số p + 2K
>
>
>
> và K ~ Pois(λ)
>
>
>
> Để từ đó nếu giả sử muốn tính EX ta chỉ việc áp dụng Adam's Law:
>
>
>
> EX = E[E(X|K)] 
>
>
>
> X|K là Chi-Square p + 2K, với Chi-Square(p) thì expected value = p 
>
>
>
> ⇨ E[X|K] = p + 2K
>
>
>
> Và ⇨ EX = E(p + 2K) = p + 2EK = p + 2λ  (expected value của Pois(λ) = λ)
>
>
>
> Nếu mà tính bằng cách dùng pmf thì rất khó

**🔗 See also:** [Hỗn hợp Poisson-Gamma](#node-f2k0dv8) · [Mô hình Beta-binomial](#node-5d9xmzc)

<br>

<a id="node-5d9xmzc"></a>

- **Mô hình Beta-binomial**

<p align="center"><kbd><img src="assets/x4ay51rth6.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng họ nói về một mô hình phân tầng nữa gọi là Βeta-binomial: Đại
> khái đó là khi ta cho success rate trong binomial(n, p) tức là p thay vì fixed
> thì nay cũng là một random variable ~ β(α,β) 
>
>
>
> Trong sách ghi X|P ~ binomial(P), i = 1,2...n (cứ hiểu là X|P ~ bin(n, P))
> và P ~ β(α, β)
>
>
>
> Nhớ lại pdf của β(α, β) f(x|α, β) = 1/Beta(α, β) x^(α-1) (1-x)^(β-1) với 
> 0 ≤ x ≤ 1, α > 0, β > 0
>
>
>
> thì again, ghi x ∈ [0,1] chính là nói về support set, đồng nghĩa chỉ có trên
> đoạn này thì pdf mới dương và cũng chính là nói giá trị của một β(α, β) chỉ
> có thể nằm trong đoạn 0,1 mà thôi.
>
>
>
> Từ đó mình hiểu rằng tại so P có thể được mô hình bởi một beta distribution
> vì dĩ nhiên vai trò của P là success rate của Bern trial nên nó phải ∈ [0,1]
>
>
>
> Thế thì với mô hình này thì EX là gì:
>
>
>
> Áp dụng EX = E[E(X|P)] với X|P là một binomial(n, P) ta biết story của nó
> là Σ của n Bern(P) trials
>
>
>
> ⇨ E(X|P) = Σi E(I_i|P) với I_i ~ Bern(P), có expected value là P (expected
> value của bern(p) là p)
>
>
>
> = nP
>
>
>
> ⇨ EX = E[nP] 
>
>
>
> = nEP | linearity
>
>
>
> = n α/(α + β) | mean của β(α, β) là α/(α + β)

**🔗 See also:** [Noncentral Chi-squared và mô hình tầng](#node-jaoa4am) · [Định lý phương sai toàn phần](#node-ivmktz5)

<br>

<a id="node-ivmktz5"></a>

- **Định lý phương sai toàn phần**

<p align="center"><kbd><img src="assets/6dqcu1altv7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3w7zgji9hni.png" width="80%"></kbd></p>

> [!NOTE]
> Qua một identity cũng đã từng gặp trong stat110:
>
>
>
> Var(X) = E(Var(X|Y)) + Var(E(X|Y))
>
>
>
> Chứng minh như vầy:
>
>
>
> Đầu tiên dùng công thức thứ 1 của Var(X):
>
>
>
> Var(X) = E[X - EX]^2
>
>
>
> cộng thêm trừ bớt E(X|Y)
>
>
>
> Var(X) = E[X - EX|Y + EX|Y - EX]^2
>
>
>
> = E[(X - EX|Y) + (EX|Y - EX)]^2
>
>
>
> = E{ (X - EX|Y)^2 + (EX|Y - EX)^2 + 2(X - EX|Y)(EX|Y - EX) } | khai triển (a + b)^2
>
>
>
> = E(X - EX|Y)^2 + E(EX|Y - EX)^2 + 2E(X - EX|Y)(EX|Y - EX) | linearity
>
>
>
> Xét E(X - EX|Y)(EX|Y - EX)
>
>
>
> Dùng identity EX = E[E(X|Y)]
>
>
>
> ⇨ E[(X - EX|Y)(EX|Y - EX)] = E[E[(X - EX|Y)(EX|Y - EX)|Y]] (Coi X = (X -
> EX|Y)(EX|Y - EX) )
>
>
>
> Thế thì nhìn cái này E[(X - EX|Y)(EX|Y - EX)|Y], ta lập luận như vầy:
>
>
>
> vì khi đã condition on Y, tức là biết giá trị của Y thì EX|Y như đã biết sẽ là một
> constant Bản thân EX|Y là random variable, cũng như EX|y là hàm số theo y, nhưng
> biết giá trị của Y thì EX|Y sẽ ko còn là random variable nữa, vì EX|Y chỉ là apply
> hàm EX|y lên Y. Và EX thì dĩ nhiên là constant. nên EX|Y - EX cũng là constant, do
> đó ta có thể đưa ra ngoài theo tính linearity
>
>
>
> Thành ra E[(X - EX|Y)(EX|Y - EX)|Y] = (EX|Y - EX) E[(X - EX|Y)|Y]
>
>
>
> Rồi xét E[(X - EX|Y)|Y] thì với việc biết Y như đã nói EX|Y là constant, do đó ta đang
> có  chính là E[(X + c)|Y] = EX|Y + Ec|Y = EX|Y + c
>
>
>
> ⇨ E[(X - EX|Y)|Y] = EX|Y - EX|Y = 0
>
>
>
> Vậy E[(X - EX|Y)(EX|Y - EX)|Y] = 0
>
>
>
> Và Var(X) = E(X - EX|Y)^2 + E(EX|Y - EX)^2
>
>
>
> Xét term đầu tiên:
>
>
>
> E[(X - EX|Y)^2] , cũng áp dụng EX = E[EX|Y]
>
>
>
> = E{E[(X - EX|Y)^2|Y]}
>
>
>
> Thì E[(X - EX|Y)^2|Y] chính là Var(X|Y)
>
>
>
> Vậy E[(X - EX|Y)^2] = E{E[(X - EX|Y)^2|Y]} = **E[Var(X|Y)]** 
>
>
>
> Đây là công thức đã được nói sơ qua ở Stat110, lecture 27. Nói chung là không có gì
> phức tạp, chỉ là ta mở rộng từ định nghĩa của variance Var(X) = EX^ - (EX)^2
> sang Var(X|Y) = EX^2|Y - (^2EX|Y)
>
>
>
> Hoặc Var(X) = E[X - EX]^2 sang Var(X|Y) = E[X - EX|Y]^2|Y
>
>
>
> Xét term thứ hai: E(EX|Y - EX)^2
>
>
>
> Như đã nói nhiều lần EX|Y là một random variable, thì mean của nó là gì, là E[EX|Y]
> mà theo Adam's Law chính là EX Vậy E(EX|Y - EX)^2 chính là E(EX|Y - E[EX|Y])^2
>
>
>
> và đây là công thức của variance **Var(EX|Y)**
>
>
>
> Vậy Var(X) = E(X - EX|Y)^2 + E(EX|Y - EX)^2
>
> **⇔ Var(X) = E[Var(X|Y)] - Var(EX|Y)**

**🔗 See also:** [Mô hình Beta-binomial](#node-5d9xmzc) · [Phương sai Binomial Beta](#node-tvfka2r) · [Định lý Rao-Blackwell](#node-aixo4xg) · [Example 10.1.10 Large-sample Mixture Variances](#node-slkl4m8)

<br>

<a id="node-tvfka2r"></a>

- **Phương sai Binomial Beta**

<p align="center"><kbd><img src="assets/qirp5x7a0wi.png" width="80%"></kbd></p>

> [!NOTE]
> Áp dụng identity này giúp ta tính VarX của mô hình phân cấp lúc nãy X ~ binomial(n, P)
> P ~ β(α, β)
>
>
>
> Var(X) = Var[E(X|P)] + E[Var(X|P)]
>
>
>
> X|P ~ binomial(n, P) mà binomial n,p thì ta biết có variance là npq
>
>
>
> và mean là np
>
>
>
> ⇨ Var[E(X|P)] = Var(nP) 
>
>
>
> = n^2Var(P) | Var(cX) = c^2 Var(X)
>
>
>
> Với P ~ β(α, β) ⇨ Var(P) = αβ/[(α+β)^2(α+β+1)]
>
>
>
> ⇨ n^2Var(P) = n^2 αβ/[(α+β)^2(α+β+1)]
>
>
>
> E[Var(X|P)] = E[nP(1-P)]  
>
>
>
> = nE[P(1-P)] 
>
>
>
> Để tính cái này thì dùng lotus thôi (đây là Eg(P) với g(P) = P(1-P)
>
>
>
> E[P(1-P)] = ∫0:1 p(1-p)fP(p)dp
>
>
>
> = ∫0:1 p(1-p) Γ(α+β)/Γ(α)Γ(β) p(1-p) p^(α-1)(1-p)^(β-1)dp
>
>
>
> ....QUAY LẠI SAU

**🔗 See also:** [Định lý phương sai toàn phần](#node-ivmktz5)

<br>

