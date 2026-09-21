# 6.2 The Sufficient Principle

📊 **Progress:** `46` Notes | `59` Screenshots | `2` AI Reviews

---
<a id="node-yxj3s29"></a>

<br>

<a id="node-t9iuvx6"></a>

## Nguyên lý đủ

<p align="center"><kbd><img src="assets/vtwpw89ksm.png" width="80%"></kbd></p>

> [!NOTE]
> Định nghĩa của sufficient statistic của một parameter θ, là statistic mà **nắm 
> bắt mọi thông tin về θ chứa trong sample**. Mọi thông tin khác, chứa trong
> sample đều ko chứa thêm thông tin nào nữa về θ.
>
>
>
> Và từ đó ta có **SUFFICIENT PRINCIPLE**: Nói rằng, T(𝐗) là sufficient statistic
> của θ thì mọi suy luận về θ  nên chỉ dựa vào sample 𝐗 thông qua T(𝐗) mà 
> thôi. Đồng nghĩa, hay nói rõ hơn, nếu mà 𝐱 và 𝐲 là hai sample (hai bộ giá
> trị quan sát được cụ thể của X1,..Xn) thì **việc suy luận về θ sẽ giống nhau**,
> dù cho ta dùng bộ giá trị nào. X1,..Xn = x1,..xn hay X1,...Xn = y1,...yn

**🔗 See also:** [Nguyên lý thống kê đủ](./63_the_likelihood_principle.md#node-hr9vr6y)

<br>

<a id="node-aog81op"></a>

### Định nghĩa Thống kê đủ

<p align="center"><kbd><img src="assets/wpnjcsz1fwr.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, mình qua cái loại đầu tiên: **SUFFICIENT STATISTIC**
>
>
>
> Định nghĩa chính thức là, một statistic T(𝐗) được gọi là sufficient statistic của 
> θ nếu như **conditional distribution** của sample 𝐗 given giá trị của T(𝐗) **ko 
> phụ thuộc θ**
>
>
>
> Hiểu nôm na là, biết được T(𝐗) là coi như có đủ thông tin về θ, nên distribution
> của 𝐗 hoàn toàn được hiểu biết đầy đủ, đếch cần θ nữa.
>
>
>
> Gs cho rằng để mà hiểu được đầy đủ cái định nghĩa này thì ta cần phải dùng
> đến một các hiểu phức tạp hơn của conditional probability hơn là những
> gì được học ở chapter 1 vì khi T(𝐗) có giá trị liên tục thì như đã biết P(T(𝐗) = t)
> sẽ luôn bằng 0 bất kể t.
>
>
>
> Do đó ở đây gs đề nghị ta **chỉ xét discrete** T(𝐗) và chỉ ra những điểm tương
> đồng với continuous case

**🔗 See also:** [Thống kê đủ loại bỏ θ](./73_methods_of_evaluating_estimators.md#node-ap81sh3) · [linked note](./83_methods_of_evaluating_test.md#node-e7v2aj1)

<br>

<a id="node-1j0q4qh"></a>

#### Định nghĩa Thống kê Đầy đủ

<p align="center"><kbd><img src="assets/g575panygwf.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì gọi t là một possible value của T(𝐗), mà gs cho biết điều này có
> nghĩa là P_θ(T(𝐗) = t) > 0.
>
>
>
> Dừng lại chút xíu, để ý kí hiệu P_θ(T(𝐗) = t) > 0. Cái subscript θ là sao nhỉ?
>
>
>
> Có lẽ phải ôn lại chút: Ta có một population mà ta dùng θ  để chỉ distribution
> parameter của nó.
>
>
>
> Từ population này, mình thực hiện random sampling: quan sát giá trị của một
> biến số nào đó (tuân theo population distribution trên) n lần, để có một bộ
> random variable X1,...Xn. Viết là 𝐗. Và T(𝐗) là một statistic = kết quả
> của việc apply function T(.) lên 𝐗, dĩ nhiên 𝐗 là random variable
> (vectors) nên T(𝐗) cũng là random variable.
>
>
>
> Và vì là random variable, nên ta "có quyền" nói đến distribution của nó. Tuy
> nhiên những bài trước gs Casella cũng đã nói, vì T(𝐗), là một random
> variable tạo ra từ các random variable trong random sample, nên distribution
> của nó mình gọi là **SAMPLING DISTRIBUTION**, để phân biệt nó với
> population distribution, là marginal distribution của X1,...Xn
>
>
>
> Vậy thì ở đây, khi nói đến P(T(𝐗) = t), dĩ nhiên là ta đang nói đến **sampling
> distribution** này.
>
>
>
> Thế thì, vấn đề là, như đã nói T(𝐗) được sinh ra từ X1,...Xn. có distribution
> với param θ. Nên **SAMPLING DISTRIBUTION, SẼ PHỤ THUỘC θ** 
>
>
>
> Có nghĩa là, với các θ khác nhau, thì sampling distribution sẽ khác nhau.
>
>
>
> ===
>
>
>
> Và gs cho biết rằng, nhắc đến P_θ(T(𝐗) = t) nhưng cái ta sẽ quan tâm
> chính là conditional probability P_θ(𝐗 = 𝐱 | T(𝐗) = t) như trong định
> nghĩa của sufficient statistic.
>
>
>
> Dĩ nhiên giá trị xác suất này, sẽ cũng phụ thuộc θ, vì đây là probability
> distribution của random sample 𝐗.
>
>
>
> Thế thì, đại ý là, nếu T(𝐱) khác t, thì  P_θ(𝐗 = 𝐱 | T(𝐗) = t) = 0. Vì
> sao?
>
>
>
> ⇨ Là vì cái này, theo định nghiã của conditional probability:
>
>
>
> = P_θ(𝐗 = 𝐱, T(𝐗) = t) / mẫu
>
>
>
> và cái tử số là joint event của hai event disjoint: 𝐗 = **x,** T(𝐗) = t, nên nếu
> **X = x xảy ra thì T(X) = T(x) chắc chắn phải xảy ra, đồng nghĩa T(X) = t 
> với t khác T(x) sẽ  không thể xảy ra ⇨ xác suất = 0**
>
>
>
> Do đó mình chỉ quan tâm các giá trị của 𝐱 mà T(𝐱) = t. Tức là:
>
>
>
> P_θ(𝐗 = 𝐱 | T(𝐗) = t = T(𝐱))
>
>
>
> Thế thì tại đây mình mới dừng lại để nhận định thế này: Theo định nghĩa,
> statistic T(𝐗) muốn được gọi là một sufficient statistic, thì conditional probability
> của 𝐗, given T(𝐗) không được còn depend vào θ nữa.
>
>
>
> Vậy, có nghĩa là cái P_θ(𝐗 = 𝐱 | T(𝐗) = T(𝐱)) ở trên sẽ không còn depend θ 
> nữa, và ta bỏ cái subscript θ đi P(𝐗 = 𝐱 | T(𝐗) = T(𝐱))

<br>

<a id="node-umvmbmt"></a>

##### Thống kê đủ và thông tin θ

<p align="center"><kbd><img src="assets/6pszy50dsti.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qk522kcs75j.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi chỗ này phải đọc kĩ: Đầu tiên, như vậy sufficient statistic nắm bắt mọi
> thông tin về θ theo cách hiểu này.
>
>
>
> Vì hãy nghĩ đến ý nghĩa của việc P(𝐗=𝐱 | T(𝐗)=T(𝐱)) không phụ
> thuộc θ nữa:  nó có nghĩa là:  Khi đã biết giá trị cụ thể của statistic T(𝐗) ,
> tức T(𝐱), thì, sẽ biết  được xác suất của việc 𝐗 = 𝐱,vốn dĩ là
> một sample - các random variable X1,.. Xn đến từ population distribution có
> tham số θ mà ta chưa biết.
>
>
>
> Thế thì đại khái là gs mô tả hai bức tranh: Có hai ông:
>
>
>
> Ông 1: Biết được giá trị 𝐗,= 𝐱, và dĩ nhiên apply hàm T(.) lên thì
> ổng có T(𝐗), = T(𝐱). Và gs nói ổng sẽ dùng thông tin event 𝐗=𝐱
> và T(**X)**=T(𝐱) đã xảy ra để mà suy luận (inference) về θ. (tạm hiểu
> là, bằng cách tính toán nào đó)
>
>
>
> Còn ông 2: Chỉ biết T(𝐗) có giá trị cụ thể là T(**x),** tức là chỉ biết / có
> giá trị T(𝐱),  chứ ko biết giá trị 𝐱 của 𝐗. (Tức là, ông 1 biết 𝐱, và
> và T(𝐱) tức là biết cả giá trị cụ thể của 𝐗 và T(𝐗)., còn ông 2 chỉ
> biết T(𝐱), không biết 𝐱)
>
>
>
> Tuy nhiên, vì T(𝐗) là một sufficient statistic, nên như đã nói ta biết
> P(𝐗=𝐱|T(𝐗)=T(𝐱)) không phụ thuộc θ.
>
>
>
> Nên, ông 2 ổng có thể biết được f(𝐲) = P(𝐗=𝐲 | T(𝐗)=T(𝐱))
> bằng cánh tính toán nào đó trên tập A_T(𝐱) = {y: T(𝐲) = T(𝐱)}
>
>
>
> Rồi khi đó ổng có thể dùng một cái cơ chế ngẫu nhiên nào đó để mà
> generate 𝐘 đến từ distribution này sao cho 
> P(𝐘=𝐲 |T(𝐗)=T(𝐱)) = P(𝐗=𝐲 | T(𝐗)=T(𝐱)).
>
>
>
> Và hóa ra, với mỗi giá trị của θ, 𝐗, **Y CÓ CHUNG UNCONDITIONAL
> PROBABILITY DISTRIBUTION** mà mình sẽ chứng minh ngay sau đây.
>
>
>
> Nhưng cái chính là, ông 1 biết 𝐗, ông 2 biết 𝐘, thì cả hai đều có thông
> tin của θ.
>
>
>
> Nhưng ông Y, tất cả những gì ổng có, chỉ là từ T(𝐗) = **x,** hoàn toàn ko
> có / biết 𝐱 nhưng vẫn có đủ thông tin về θ như ông 1, là người biết giá
> trị 𝐱 của **X.**
>
>
>
> Nói rõ hơn, thì ông 1 ổng có một bộ các giá trị quan sát thấy của **X:**
> X1 = x1, X2 = x2, ...Xn = xn. Và các X1,X2...Xn ~ population θ 
>
>
>
> Nhưng ông 2, bằng cách dựa vào việc T là sufficient statistic ổng tạo
> ra một random sample Y: Y1 = y1, Y2 = y2,....Yn = Yn. Mà ổng nói rằng
> cái bộ này, dù được tạo ra bởi random device lại cũng có cùng population
> distribution với X1,...Xn.
>
>
>
> Nếu điều này đúng, thì có nghĩa là việc biết giá trị T(𝐱) của T(𝐗), đã nắm bắt
> được mọi thông tin của θ rồi.

<br>

<a id="node-9z7xkqn"></a>

###### Thống kê đủ và phân phối

<p align="center"><kbd><img src="assets/itolun8e7e.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì. Hôm qua mình dừng lại ở định nghĩa về sufficient statistic:
>
>
>
> Ôn lại chút xíu về bối cảnh cho đến nay:
>
>
>
> Ta biết về định nghĩa của random sample. X1,X2...Xn là các random variables
> mang giá trị đại diện cho việc quan sát một biến cố ngẫu nhiên nào đó trong
> một population. X1,..Xn sẽ iid: có chung marginal distribution, và độc lập.
>
>
>
> Đặt nó vào vector 𝐗: (X1,...Xn). và gọi một giá trị cụ thể của chúng: x1,x2...
> xn là vector **x.**
>
>
>
> Thế thì nói về statistic, thì nó là một random variable có được khi apply hàm
> T lên các random variable T(X1,...Xn), hay T(𝐗) cho gọn.
>
>
>
> Và nếu như statistic T này, tức hàm T này, có tính chất sao cho:
>
>
>
> dựa trên việc biết một giá trị cụ thể của rv T(𝐗), tức T(𝐱) thì xác suất của 𝐗 ko
> còn phụ thuộc parameter của population nữa:
>
>
>
> P(𝐗 = 𝐱 |T(𝐗) = T(𝐱)), không còn phụ thuộc θ nữa.
>
>
>
> Thì khi đó T(𝐗) gọi là sufficient statistic.
>
>
>
> Và bức tranh của hai ông 1, 2: Ông 1 ổng có được một bộ các giá trị của
> random sample  X1=x1, X2=x2....Xn=xn, tức là ổng có 𝐗,= 𝐱, và dĩ
> nhiên ổng cũng sẽ biết T(𝐗), = T(𝐱)Nhưng ông 2, ổng chỉ có đúng một cái: T(x1,...xn) = T(𝐱), ví dụ như ông 1
> tính T(𝐗) bằng cách apply hàm T lên 𝐱 (vì ổng có giá trị 𝐱 của 𝐗
> như đã nói) và đưa sang cái T(𝐱) cho ông 2.Nên ông 2 không biết 𝐗, hay (X1, X2...Xn) có giá trị gì (là cái 𝐱 mà ông 1
> biết),  mà nhờ ông 1 đưa sang cho cái T(𝐱) nên ông 2 biết được giá trị
> T(𝐱) của T(𝐗) mà  thôi
>
>
>
> (cái rắc rối của cái này chỉ là vấn đề kí hiệu)
>
>
>
> Lấy ví dụ dễ hiểu: Ông 1 biết X1 = 1 X2 = 3. Tức biết 𝐗 =(1, 3), hay 𝐱
> là (1, 3) Rồi ổng tính T(X1, X2) = cách apply hàm T lên giá trị 1,3. Để ổng có
> T(1,3)  = 5 chẳng hạn. Đây chính là T(𝐗), mà giá trị 5 chính là T(𝐱).
>
>
>
> Ổng đưa số 5 này sang cho ông 2. Thì ông 2 chỉ biết con số 5, là giá trị của 
> T(𝐗), chứ ko biết X1 bằng mấy, X2 bằng mấy.
>
>
>
> ====
>
>
>
> Thế thì câu chuyện là T(𝐗) (nhấn vào T) là một sufficient statistic, thì từ việc
> định nghĩa của sufficient statistic cho ta biết rằng biết giá trị của T(𝐗) thì sẽ
> biết giá trị xác suất của 𝐗, mà ko cần θ nữa...
>
>
>
> (mà nếu ko có điều này, thì biết giá trị của T(𝐗) cũng ko cho phép tính xác
> suất của 𝐗,  vì bản thân xác suất T(𝐗) cũng phụ thuộc θ)
>
>
>
> ...nên ổng (ông 2) mới xây dựng được phân phối xác suất điều kiện của 𝐗
> dựa trên T(𝐗) đã biết. =T(𝐱) mà ở ví dụ này đang = 3 đó, tức là ông 2
> xây dựng đượcmột hàm số f(𝐱) mà bỏ 𝐱 nào đóvào, ta sẽ có
> được P(𝐗 = 𝐱 | T(𝐗) = T(𝐱))
>
>
>
> Rồi, sau khi ông 2 có cái hàm f(𝐱) thì ổng mới dùng cách nào đó để
> generating các random variable 𝐘, có phân phối xác suất pmf f𝐘, hay P(𝐘 =
> 𝐲) mà ta chưa biết nhưng ta vẫn có thể có cách tạo ra sao cho giá trị của
> P(𝐘 = y | T(𝐗) = T(𝐱))  (tức là xác suất của việc 𝐘 = 𝐲, dựa trên việc biết
> T(𝐗) = T(𝐱)) bằng với f(𝐲) ở trên.
>
>
>
> Có nghĩa là khúc này ta tạm chấp nhận là có thể tạo ra Y sao cho:
>
>
>
> P(𝐘 = 𝐱 | T(𝐗) = T(𝐱))  = P(𝐗 = 𝐱 | T(𝐗) = T(𝐱))
>
>
>
> Và điều hay ho là, 𝐘, tức Y1, Y2,...Yn cũng có marginal distribution là cùng
> một thứ  với X1, X2...
>
>
>
> ====
>
>
>
> Cần chú ý, sự rối rắm, khó hiểu chủ yếu đến từ các kí hiệu.
>
>
>
> Khi nói về P(𝐗 = 𝐱 | T(𝐗) = 𝐱), thì ta hiểu rằng, đây là một hàm phụ
> thuộc 𝐱, tức là, nó là cái hàm f(𝐱) nào đó, mà gía trị f(𝐱), tức là bỏ 𝐱
> vô, tính ra f(𝐱). Sẽ cho ta biết giá trị mang ý nghĩa là "nếu biết T(𝐗) =
> 𝐱, thì xác suất (của việc) 𝐗 = 𝐱 là bao  nhiêu)
>
>
>
> Còn nói về P(𝐘 = 𝐱 | T(𝐗) = 𝐱), thì tương tự, sẽ là function g(𝐱)
> nào đó, mà khi bỏ 𝐱 vào, thì lại cho ta biết, à, nếu dựa trên việc quan sát,
> bắt được giá trị của T(𝐗) (= 𝐱) thì xác suất 𝐘 = 𝐱 là bao nhiêu.
>
>
>
> Nhưng, khi nói, ta tạo ra 𝐘, sao cho g(𝐲) = f(𝐲), thì chính là: 𝐘 là
> một random  variable khác, khác với 𝐗, nhưng ta tạo 𝐘 sao cho tại 𝐲
> thì g(𝐲) bằng với f(𝐲)
>
> Vậy thì cơ sở cho cái này, ta sẽ phải chứng minh P(𝐘=𝐱) , tức pmf của 𝐘
> (tức joint  pmf của Y1,....Yn) tại x, phải bằng pmf của 𝐗 tại 𝐱: P(𝐗=𝐱)
>
>
>
> Xét event 𝐗 = 𝐱 **là subset của** T(𝐗) = T(𝐱). Vì sao?
>
>
>
> 𝐗 = **x,** mình hiểu bản chất của nó là {s ∈ Ω: 𝐗(s) = 𝐱}
>
>
>
> là sao, bản chất của random variable là function. Nên X1, X2,...là các function
> map từ sample space Ω tới tập số thực.
>
>
>
> Do đó 𝐗 = (X1,...Xn) cũng chỉ là function, mapping từ s trong Ω tới R^n vector 𝐗(s)
> = (X1(s),... Xn(s))
>
>
>
> Nên event 𝐗 = 𝐱, cũng là X1=x1, X2=x2,... thật ra chính là event:
>
>
>
> {s ∈ Ω: X1(s) = x1,...Xn(s) = xn}, đó chính là {s ∈ Ω: 𝐗(s)= 𝐱}
>
>
>
> Rồi, thế thì nếu X1(s) = x1 ⇨ T(X1(s)) = T(x1),....Xn(s) = xn ⇨ T(Xn(s)) = T(xn)
>
>
>
> Hay gom chung lại 𝐗(s) = 𝐱 ⇨ T(𝐗(s)) = T(𝐱)
>
>
>
> Vậy s ∈ {s ∈ Ω: 𝐗(s) = 𝐱} thì s cũng thuộc  {s ∈ Ω: T(𝐗(s)) = T(𝐱)}
>
>
>
> nên tập {s ∈ Ω: 𝐗(s) = 𝐱} ⊂ {s ∈ Ω: T(𝐗(s)) = T(𝐱)}
>
>
>
> Và đây chính là {𝐗 = 𝐱}⊂{T(𝐗) = T(𝐱)}
>
>
>
> =====
>
>
>
> Rồi, xét {𝐘 = 𝐱}, về bản chất cũng là {s ∈ Ω: 𝐘(s) = 𝐱},
>
>
>
> Thế thì trước khi đi tiếp ta phải ôn lại **CÁCH TẠO RA** 𝐘:
>
>
>
> 𝐘 được tạo ra, tức là nó mang giá trị 𝐲, sao cho: 
>
>
>
> P(𝐘 = 𝐲 | T(𝐗) = T(𝐱)) = P(𝐗 = 𝐲 | T(𝐗) = T(𝐱))
>
>
>
> Giả sử đặt T(𝐱) = t0 đi, thì việc tạo được 𝐘 = 𝐲, **hàm** **ý là:** **xác suất event này dương**,
> vì nếu ko dương, thì nó đã không xảy ra.
>
>
>
> Nhắc lại ý quan trọng: Tạo được 𝐘 = 𝐲, ⇨ chứng tỏ P(𝐘 = 𝐲 | T(𝐗) = T(𝐱)) **dương**
>
>
>
> ⇨ P(𝐗 = 𝐲 | T(𝐗) = T(𝐱)) > 0 
>
>
>
> Như vậy 𝐲 phải là một giá trị nằm trong một partition At0 = {𝐱: T(𝐱) = t0}, vì nếu ko, 
> event 𝐗 = 𝐲 , T(𝐗) = t0 ko thể xảy ra, do ta biết xác suất của event 𝐗 = 𝐲 | T(𝐗) = T(𝐱)
> = xác suất của joint event 𝐗 = 𝐲, T(𝐗) = T(𝐱) = t0, và nó chỉ dương khi 𝐲 ∈A_t0
> là preimage của {t = t0}, tức {**z** ∈ range 𝐗: T(**z**) = t0}
>
>
>
> P(𝐗 = 𝐲 | T(𝐗) = T(𝐱)) > 0 ⇔ 𝐲 ∈ A_t0 = {**z** ∈ **range X**: T(**z**) = t0 = T(𝐱)}
>
>
>
> Vậy 𝐲 luôn thuộc A_t0, hay, A_T(𝐱), cũng là nói, **mọi possible value của Y đều
> thuộc A_t0**, hay A_T(𝐱)
>
>
>
> Quay lại, xét event {𝐗 = 𝐱}, {𝐘 = 𝐱}
>
>
>
> bản chất là {s ∈ Ω: 𝐗(s) = 𝐱} và {s ∈ Ω: 𝐘(s) = 𝐱} 
>
>
>
> Rồi xét tập {T(𝐗) = T(𝐱) = t0} có bản chất là {s: T(𝐗(s) = T(𝐱) = t0)
>
>
>
> thì như đã lập luận ở trên {𝐗 = 𝐱} ⊂ {T(𝐗) = T(𝐱) = t0}
>
>
>
> ====
>
>
>
> Còn {𝐘 = 𝐱}, = {mọi possible value 𝐲 của 𝐘 sao cho 𝐲 = 𝐱}
>
>
>
> = {s ∈ Ω: 𝐘(s) = 𝐱} 
>
>
>
> Để chứng minh {𝐘 = 𝐱} ⊂ {T(𝐗) = T(𝐱) = t0} ta sẽ chứng minh phản chứng:
>
>
>
> Giả sử tồn tại s' ∈ {𝐘 = 𝐱} nhưng không ∈ {T(𝐗) = T(𝐱) = t0}
>
>
>
> Tức là s' ∈ A = {s ∈ Ω: 𝐘(s) = 𝐱} nhưng không ∈ B = {T(𝐗(s)) = T(𝐱) = t0}
>
>
>
> s' không thuộc B ⇨ T(𝐗(s')), đặt là t' sẽ khác T(𝐱), tức khác t0: t' ≠ t0
>
>
>
> s' thuộc A ⇨ 𝐘(s') = 𝐱
>
>
>
> Mà, xét quá trình tạo ra 𝐘: s' xảy ra (vì đã nói Y = 𝐱, xảy ra với outcome 
> gốc là s'⇨Y(s') = 𝐱 xảy ra)
>
>
>
> Mà s' xảy ra thì giá trị cụ thể quan sát được của 𝐗 sẽ là 𝐗(s'), apply statistic T(.)
> ta có T(𝐗(s')), như trên ta đã đặt = t'
>
>
>
> Rồi theo quy trình tạo 𝐘, giá trị cụ thể 𝐲 của 𝐘, được tạo ra từ một phân phối mà
> ông 2 xây dựng: P(𝐘 = 𝐲 | T(𝐗) = T(𝐱)) = P(𝐗 = 𝐲 | T(𝐗) = T(𝐱))
>
>
>
> Thế thì giá trị của 𝐘 ở đây đang nói, là **x, và gía trị của T(X) đang là t'** nên:
>
>
>
> **Giá trị cụ thể x (của Y) được tạo ra bởi** P(𝐘 = 𝐱 | T(𝐗) = t') = P(𝐗 = 𝐱 | T(𝐗) = t')
>
>
>
> và ý quan trọng đó là 𝐘 = 𝐱 đã xảy ra, nên xác suất P(𝐘 = 𝐱 | T(𝐗) = t') dương
>
>
>
> ⇨ P(𝐗 = 𝐱 | T(𝐗) = t') > 0
>
>
>
> ⇨ P(𝐗 = 𝐱 , T(𝐗) = t') > 0
>
>
>
> Điều này là vô lí. Vì 𝐗 = 𝐱 ⇔ T(𝐗) = T(𝐱) = t0.
>
>
>
> ⇨ P(𝐗 = 𝐱 , T(𝐗) = t') = P(T(𝐗) = T(𝐱) = t0 , T(𝐗) = t') và cái này phải = 0 vì t' khác t0
>
>
>
> Do đo mâu thuẫn giả thiết nói trên là s' ∈ {𝐘 = 𝐱} nhưng không thuộc {T(𝐗) = T(𝐱)}
>
>
>
> Do đó s' thuộc A thì nó cũng phải thuộc B ⇨ A subset của B. Chứng minh xong
> {𝐘 = 𝐱} ⊂ {T(𝐗) = T(𝐱)}
>
>
>
> Vậy ta hiểu vì sao {𝐘 = 𝐱} và {𝐗 = 𝐱} đều ⊂ {T(𝐗) = T(𝐱)}
>
>
>
> Đồng thời cũng hiểu vì sao P(𝐗 = 𝐱 | T(𝐗) = T(𝐱)) = P(𝐘 = 𝐱 | T(𝐗) = T(𝐱))

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ⚠️ **88/100** · ✓ Move on
>
> Ghi chú thể hiện sự hiểu biết sâu sắc và bản chất về không gian mẫu và ánh xạ của biến ngẫu nhiên khi tự chứng minh mối quan hệ tập con mà sách chỉ nêu lướt qua. Cần lưu ý một vài lỗi ký hiệu nhỏ và hoàn thiện nốt bước cuối cùng (nhân xác suất) để kết luận phân phối vô điều kiện bằng nhau.
>
> **🟡 Minor issues**
>
> **1.** *"Khi nói về P(𝐗 = 𝐱 | T(𝐗) = 𝐱)..."*
>
> Lỗi gõ nhầm ký hiệu: điều kiện ở đây phải là T(𝐗) = T(𝐱) (hoặc một giá trị t cụ thể của statistic), không phải T(𝐗) = 𝐱 vì T(𝐗) là hàm gom thông tin (thường là scalar hoặc vector số chiều thấp hơn 𝐱).
>
> **2.** *"X1(s) = x1 ⇨ T(X1(s)) = T(x1),....Xn(s) = xn ⇨ T(Xn(s)) = T(xn)"*
>
> Hàm thống kê T nhận toàn bộ vector mẫu 𝐗 = (X1,...,Xn) làm đầu vào, không áp dụng riêng lẻ lên từng biến T(X_i(s)) như cách viết tách ở đây (dù câu ngay sau bạn đã gom lại đúng thành 𝐗(s) = 𝐱 ⇨ T(𝐗(s)) = T(𝐱)).
>
> **3.** *"Vậy thì cơ sở cho cái này, ta sẽ phải chứng minh P(𝐘=𝐱) , tức pmf của 𝐘 ... phải bằng pmf của 𝐗 tại 𝐱: P(𝐗=𝐱)"*
>
> Bạn đã chứng minh rất tốt 2 tiền đề (tập con và xác suất có điều kiện), nhưng chưa chốt hạ dòng cuối cùng bằng công thức nhân xác suất: P(𝐗=𝐱) = P(𝐗=𝐱, T(𝐗)=T(𝐱)) = P(𝐗=𝐱 | T(𝐗)=T(𝐱)) P(T(𝐗)=T(𝐱)) để suy ra P(𝐗=𝐱) = P(𝐘=𝐱).
>
>
> **✓ Strengths**
> - Tư duy rất vững về bản chất xác suất: hiểu biến ngẫu nhiên là hàm ánh xạ từ không gian mẫu Ω để làm rõ quan hệ tập con.
> - Lập luận phản chứng để giải thích việc tạo biến ngẫu nhiên 𝐘 thỏa mãn {𝐘=𝐱} ⊂ {T(𝐗)=T(𝐱)} thông qua support của phân phối điều kiện rất trực quan và thuyết phục.
> - Nắm rất rõ câu chuyện hai nhà thống kê (Statistician 1 và 2) để hiểu ý nghĩa thực tế của sufficiency.
>
> **💡 Deeper notes**
> - Sau khi có {𝐗 = 𝐱} ⊂ {T(𝐗) = T(𝐱)}, ta có {𝐗 = 𝐱} ∩ {T(𝐗) = T(𝐱)} = {𝐗 = 𝐱}. Khi đó P(𝐗=𝐱) = P(𝐗=𝐱 | T(𝐗)=T(𝐱)) · P(T(𝐗)=T(𝐱)). Vì cả hai thành phần đều bằng nhau đối với 𝐗 và 𝐘, ta lập tức suy ra P(𝐗=𝐱) = P(𝐘=𝐱).

<br>

<a id="node-imixp1w"></a>

###### Phân phối biên qua tính đủ

<p align="center"><kbd><img src="assets/razqcsykbme.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, tiếp tục,
>
>
>
> P_θ(𝐗 = 𝐱)
>
>
>
> vì đã hiểu vì sao {𝐗 = 𝐱} ⊂ {T(𝐗) = T(𝐱)} nên
>
>
>
> .. = P_θ(𝐗 = 𝐱, T(𝐗) = T(𝐱)} (do A ⊂ B thì P(A ∩ B) = P(A)
>
>
>
> dùng conditional probability theorem:
>
>
>
> .. = P_θ(𝐗 = 𝐱 | T(𝐗) = T(𝐱)) P(T(𝐗) = T(𝐱))
>
>
>
> và vì P_θ(𝐗 = 𝐱 | T(𝐗) = T(𝐱)) **ko phụ thuộc θ** nữa theo định
> nghĩa của sufficient statistic
>
>
>
> .. = P(𝐗 = 𝐱 | T(𝐗) = T(𝐱)) P(T(𝐗) = T(𝐱)) (bỏ kí hiệu θ dưới
> chân P)
>
>
>
> và vì P(𝐗 = 𝐱 | T(𝐗) = T(𝐱)) = P(𝐘 = 𝐱 | T(𝐗) = T(𝐱))
> như theo định nghĩa về cách tạo 𝐲, là 𝐲 được sinh ra sao cho P(𝐘 =
> 𝐲 | T(𝐗) = T(𝐱)) = P(𝐗 = 𝐲 | T(𝐗) = T(𝐱))
>
>
>
> .. = P(𝐘 = 𝐱 | T(𝐗) = T(𝐱)) P(T(𝐗) = T(𝐱))
>
>
>
> = P_θ(𝐘 = 𝐱, T(𝐗) = T(𝐱))
>
>
>
> = P_θ(𝐘 = 𝐱)
>
>
>
> Và ta đã **chứng minh xong là marginal distribution của X, Y là GIỐNG NHAU
>
>
>
> Tóm tắt lại:
>
>
>
> Nãy giờ nhằm chứng minh là:**
>
>
>
> Giả sử ta chỉ biết giá trị của sufficient statistic T(𝐗) = T(𝐱) (chứ ko biết
> 𝐱), thì  bằng cách generate giá trị 𝐲 của 𝐘 sao cho P(𝐘 = 𝐲 |
> T(𝐗) = T(𝐱)) = P(𝐗 = 𝐱 | T(𝐗) = T(𝐱)) thì ta vẫn sẽ có được
> các giá trị của **y giống y như được lấy từ marginal P(Y = y)  giống y phân
> phối marginal P(X = x)**. Điều này chứng tỏ rằng việc biết được T(𝐱)  đã
> đủ để mô tả phân phối population của 𝐗, nói cách khác, giá trị quan sát
> của T(𝐱) đã chứa đầy đủ thông tin về θ rồi.

<br>

<a id="node-vw80nut"></a>

###### Định nghĩa thống kê đủ

<p align="center"><kbd><img src="assets/nuyij2dfnnk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/02ez9zixd6at.png" width="80%"></kbd></p>

> [!NOTE]
> Lập luận tiếp theo ở đây là, để **xác nhận** T(𝐗) là **sufficient statistic** của / cho
> θ. Thì ta **phải verify** rằng, **với bất kì fixed values của** 𝐱 và t thì c**onditional
> probability** P_θ(𝐗 = 𝐱 | T(𝐗) = t) **đều giống nhau với mọi value của** θ, có nghĩa
> là **nó không phụ thuộc θ.**
>
>
>
> Rồi, xét P_θ(𝐗 = 𝐱 | T(𝐗) = t), = P_θ(𝐗 = 𝐱, T(𝐗) = t) / P(T(𝐗) = t)
>
>
>
> thì tử số, vì 𝐗 = 𝐱 ⊂ T(𝐗) = t (= T(𝐱)) như đã nói / biết trong note trước.
>
>
>
> Nên P_θ(𝐗 = 𝐱, T(𝐗) = t) = P_θ(𝐗 = 𝐱)  (A ⊂ B ⇨ A ∩ B = A ⇨ P(A ∩ B) = P(A))
>
>
>
> Nên ta có P_θ(𝐗 = 𝐱) / P(T(𝐗) = t)
>
>
>
> và tử số, dĩ nhiên chính là joint pmf của 𝐗 tức X1,X2,....Xn. ta kí hiệu là p(𝐱|θ)
>
>
>
> còn mẫu số là pmf của random variable T(𝐗), kí hiệu là q(T(𝐗) | θ)
>
>
>
> Và như vậy để conditional probability ở trên ko phụ thuộc θ thì cái tỉ số này 
> **XÉT Ở GÓC ĐỘ CỦA MỘT HÀM SỐ THEO θ PHẢI LÀ MỘT CONSTANT** 
>
>
>
> Và đó là nội dung của theorem 6.2.2. 
>
>
>
> Một lưu ý đã từng nói, đại khái để hoàn toàn hiểu theorem này, ta phải có
> cách hiểu toàn diện hơn về conditional probability hơn là theo những gì chap1
> đã học vì với 𝐗, T(𝐗) continuous thì P(𝐗 = 𝐱), P(T(𝐱) = t) sẽ bằng 0. Nhưng
> đại khái nói chung là **vẫn có thể dùng** cái này để xác định T(𝐗) có phải sufficient
> statistic cho θ hay không, tức là vẫn dùng p(𝐱|θ), lúc này là joint pdf của 𝐗 và
> ở mẫu số là pdf của T(𝐗)
>
>
>
> Từ đó, những phần sau ta sẽ dùng điều kiện này để xét lại xem một số statistic
> thông dụng có phải là sufficient statistic

<br>

<a id="node-ubmvdfc"></a>

###### Thống kê đủ nhị thức

<p align="center"><kbd><img src="assets/z1hgeb1v25a.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên, xét random sample 𝐗: X1,...Xn ~ Bern(θ). Và ta sẽ chứng minh
> rằng T(𝐗) = X1 + ..Xn chính là một **SUFFICIENT STATISTIC của θ**.
>
>
>
> Thế thì, như đã nói, theo theorem vừa rồi ta cần chứng minh tỉ số p(𝐱|θ) /
> q(T(𝐱)|θ)  là constant.
>
>
>
> p(𝐱|θ), tức P_θ(𝐗 = 𝐱) = P(X1 = x1, ....Xn = xn)
>
>
>
> Mà X1,...Xn là các random variable của một random sample, dĩ nhiên ta biết
> chúng iid. ⇨ joint pmf = tích các marginal pmf, và là pmf của Bern(θ): P(X=1)  =
> θ và P(X=0) = 1 - θ
>
>
>
> ⇨ P(X=x) = θ^x(1 - θ)^(1-x) Cái này ko khó hiểu.
>
>
>
> ⇨ P_θ(𝐗 = 𝐱) = Πi=1:n θ^xi(1 - θ)^(1-xi)
>
>
>
> = θ^(Σixi) (1 - θ)^[Σi(1-xi)]
>
>
>
> = θ^t (1 - θ)^(n - t)
>
>
>
> Còn P_θ(T(𝐗) = t)
>
>
>
> Với T(𝐗) = X1 + ...Xn thì dễ thấy nó có story là số Bern trial success trong
> chuỗi iid Bern(θ) trial, Stat110 đã dạy ta rằng, T(𝐗) là một Binomial(n, θ)
>
>
>
> ⇨ P(T(𝐗) = t) = (n choose t) θ^t (1 - θ)^(1 - t)
>
>
>
> ⇨ Tỉ số đang xét = [θ^t (1 - θ)^(n - t) / (n choose t)] [θ^t (1 - θ)^(1 - t)]
>
>
>
> = [(1 - θ)^(n - t) / (n choose t)] [(1 - θ)^(1 - t)]
>
>
>
> = **1 / (n choose t)
>
>
>
> kết quả này rõ ràng hoàn toàn không phụ thuộc θ nữa.** Do đó T(𝐗) = X1 + ..
> .+Xn là sufficient statistic của θ

**🔗 See also:** [Ước lượng không chệch tốt nhất Binomial](./73_methods_of_evaluating_estimators.md#node-brmf2r9)

<br>

<a id="node-nqvdq30"></a>

###### Trung bình mẫu thống kê đủ cho μ

<p align="center"><kbd><img src="assets/8a6oshein6c.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/pjna5q751oh.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự, với X1,....Xn là random sample ~ n(μ, σ²) với σ đã biết.
>
>
>
> Thì ta sẽ chứng minh **sample mean** T(𝐗) = (X1 + ...Xn) / n là sufficient statistic
> của / cho μ
>
>
>
> Thế thì, như đã quen ta cần check tỉ số p(𝐱|θ) và q(T(𝐱)|θ)
>
>
>
> Tương tự, như đã nói, dù đây là **biến liên tục** cần phải hiểu / xét conditional
> probability P(𝐗 = 𝐱 | T(𝐗) = t) theo cách khác, nhưng cái điều kiện mà ta có
> ở theorem 2: p(𝐱|θ) và q(T(𝐱)|θ) vẫn có thể được dùng để xem xét sufficient
> statistic
>
>
>
> Nên ở đây p(𝐱|θ) sẽ là joint pdf của X1,...Xn iid
>
>
>
> = tích các marginal pdf, 
>
>
>
> với X ~n(μ, σ²) ta biết fX(x) = (1/2πσ²)^(-1/2) exp[-(x - μ)^2 / 2σ²]
>
>
>
> ⇨ f𝐗(𝐱) = Πi=1:n (1/2πσ²)^(-1/2) exp[-(xi - μ)^2 / 2σ²]
>
>
>
> = [(1/2πσ²)^(1/2)]^n {exp Σi[-(xi - μ)^2 / 2σ²]}
>
>
>
> = [(1/2πσ²)^(n/2)] {exp Σi[-(xi - μ)^2 / 2σ²]}
>
>
>
> = [(1/2πσ²)^(n/2)] {exp (1/2σ²) [-Σi (xi - μ)^2]}
>
>
>
> = [(1/2πσ²)^(n/2)] {exp (1/2σ²) [-Σi (xi - x̄ + x̄ - μ)^2]}
>
>
>
> = [(1/2πσ²)^(n/2)] {exp (1/2σ²) [-Σi [(xi - x̄) + (x̄ - μ)]^2]}
>
>
>
> = [(1/2πσ²)^(n/2)] {exp (1/2σ²) [-Σi [(xi - x̄)^2 + (x̄ - μ)^2 + 2(xi - x̄)(x̄ - μ)]]}
>
>
>
> = [(1/2πσ²)^(n/2)] {exp (1/2σ²) [-[Σi(xi - x̄)^2 + Σi(x̄ - μ)^2 + 2Σi(xi - x̄)(x̄ - μ)]]}
>
>
>
> = [(1/2πσ²)^(n/2)] {exp (1/2σ²) [-[Σi(xi - x̄)^2 + n(x̄ - μ)^2 + 2Σi(xi - x̄)(x̄ - μ)]]}
>
>
>
> Xét riêng cái này Σi(xi - x̄)(x̄ - μ) = (x̄ - μ) Σi(xi - x̄) = (x̄ - μ) (nx̄ - nx̄) 
> = 0
>
>
>
> ... = [(1/2πσ²)^(n/2)] {exp (1/2σ²) [-[Σi(xi - x̄)^2 + n(x̄ - μ)^2]]}
>
>
>
> Còn mẫu số q(T(𝐱)|θ), tức = q(T(𝐱)|μ)
>
>
>
> Thì gs nhắc rằng ta đã biết sample mean T(𝐗) = (X1 + ... Xn) / n
>
>
>
> chính là một n(μ, σ²/n) random variable.
>
>
>
> Vì sao nhỉ? Có thể chứng minh nhanh:
>
>
>
> mgf của X~ n(μ, σ²): MX(t) có bản chất ý nghĩa là E[e^Xt], tức apply hàm g(u) = e^tu
> lên X để có random variable mới e^tX, và lấy kì vọng.
>
>
>
> Và ta sẽ nhớ công thức của nó là MX(t) = e^(μt + σ²t^2/2)
>
>
>
> ⇨ M(X1+..Xn)/n (t) = E[e^(X1+..Xn)t/n] = E[e^X1t/n*....e^Xnt/n]
>
>
>
> Mà X1,...Xn độc lập thì các rvs e^X1t/n, ...e^Xnt/n cũng vậy
>
>
>
> Và với X, Y độc lập thì E(XY) = EXEY
>
>
>
> ⇨ E[e^X1t/n*....*e^Xnt/n] = E[e^X1t/n] *...* E[e^Xnt/n]
>
>
>
> = MX1(t/n) *...*MXn(t/n) 
>
>
>
> và vì X1,..Xn đều có chung marginal distribution 
>
>
>
> = e^(μt/n + σ²t^2/2n^2)*...*e^(μt/n + σ²t^2/2n^2) 
>
>
>
> = e^(μt/n + σ²t^2/2n^2)^n 
>
>
>
> = e^(μt + σ²t^2/2n)
>
>
>
> = e^(**μ**t + (**σ²/n**) t^2/2)
>
>
>
> Và đây có dạng mgf của một normal(μ, σ²/n) ⇨ X̄ của normal (μ, σ²) ~ normal(μ, σ²/n)
>
>
>
> Do đó q(T(𝐱)|μ) = như trong sách.
>
>
>
> Và tỉ số này rút gọn lại ko còn μ nữa.
>
>
>
> ⇨ sample mean là sufficient statistic của μ đv normal

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **92/100** · ✓ Move on
>
> Ghi chú rất tốt, tự khai triển chi tiết hằng đẳng thức triệt tiêu số hạng chéo và chủ động chứng minh phân phối của sample mean bằng hàm sinh mômen (MGF) thay vì chỉ thừa nhận.
>
> **🟡 Minor issues**
>
> **1.** *"fX(x) = (1/2πσ²)^(-1/2) exp[-(x - μ)^2 / 2σ²]"*
>
> Nhầm lẫn dấu số mũ ở hằng số chuẩn hóa: phải là (2πσ²)^(-1/2) hoặc (1/(2πσ²))^(1/2), viết (1/2πσ²)^(-1/2) sẽ thành căn bậc hai của 2πσ² ở trên tử số.
>
> **2.** *"Do đó q(T(x)|μ) = như trong sách. Và tỉ số này rút gọn lại ko còn μ nữa."*
>
> Bỏ qua bước đặt tỉ số f(x|μ)/q(T(x)|μ) và triệt tiêu cụm exp(-n(x̄ - μ)²/(2σ²)) một cách tường minh, dù kết luận và hướng lập luận hoàn toàn chính xác.
>
>
> **✓ Strengths**
> - Tự khai triển chi tiết từng bước biến đổi đại số của tổng bình phương và chứng minh rõ ràng số hạng chéo triệt tiêu về 0.
> - Chủ động dùng MGF để chứng minh phân phối của Xbar thay vì chỉ chép lại tính chất có sẵn trong sách.
>
> **💡 Deeper notes**
> - Định lý 6.2.2 (tiêu chuẩn tỉ số p/q) yêu cầu tập giá trị mà q(T(x)|θ) > 0 phải bao hàm các điểm x mà f(x|θ) > 0; với phân phối chuẩn trên toàn trục số thực thì điều kiện này hiển nhiên thỏa mãn.

**🔗 See also:** [Thống kê đủ và hoàn chỉnh X̄](#node-st8akyc)

<br>

<a id="node-n7hexnk"></a>

###### Thống kê đủ: Giảm chiều dữ liệu

<p align="center"><kbd><img src="assets/2mh4mwn5ips.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại ý giáo sư Casella là thế này. Nãy giờ, với các vị dụ về Binomial và
> Normal, thì ta thấy sample sum, sample mean là sufficient statistic. Mà điều
> này có nghĩa là, thay vì phải lưu trữ n con số (giá trị của các  random
> variable X1,...Xn) thì **chỉ cần một con số** sample mean / sum cũng đủ phản
> ánh population param θ rồi.
>
>
>
> Và đó chính là việc ta **đã nén được data** (data reduction) hiệu quả.
>
>
>
> Nhưng qua ví dụ này, khi ta có random sample X1,...Xn chỉ biết ~ pdf f thì
> ông nói rằng: **cái tốt nhất mà ta làm được**, chỉ là **bỏ đi thứ tự** xuất hiện của
> X1,...Xn (bằng cách **chỉ xét giá trị của chúng theo thứ tự nhỏ đến lớn**)
>
>
>
> Để rồi **CÁI BỘ** n random variables X(1),...X(n), là các order statistic như đã
> biết, **CHÍNH LÀ MỘT SUFFICIENT STATISTIC**.
>
>
>
> CÓ NGHĨA LÀ, **không như hai case trước**, nơi mà ta đã thấy sufficient
> statistic là **MỘT RANDOM VARIABLE DUY NHẤT** ví dụ sample sum, hay
> X̄ (sample mean), hoặc có thể coi như một random variable vector CHỈ
> CÓ MỘT COMPONENT, MỘT CHIỀU, DIM = 1
>
>
>
> Còn ở đây, **SUFFICIENT STATISTIC, VẪN LÀ MỘT RANDOM VARIABLE
> VECTOR** CÓ n RVS, DIM VẪN BẰNG n. Tức là, ta **vẫn phải lưu trữ n** con
> số, **CHẲNG QUA LÀ KO CẦN CARE THỨ TỰ** XUẤT HIỆN CỦA CHÚNG
> mà thôi
>
>
>
> Do đó gs mới nói trong case này, nói data reduction thì **cũng ko reduce** mấy.
> nhưng điều này cũng hợp lí t**rong bối cảnh ta ko biết f (population
> distribution) là cái cóc khô gì.**
>
>
>
> Và ông nói **HÓA RA,** **CHỈ DUY NHẤT CÁI EXPONENTIAL FAMILY** (mà
> binomial, normal là thành viên) L**À CÓ THỂ CÓ SUFFICIENT STATISTIC
> DIMENSION NHỎ HƠN KÍCH THƯỚC CỦA SAMPLE MÀ THÔI** (ví dụ như
> từ n → 1)
>
>
>
> Còn **với các family khác** (như Cauchy, Logistic) thì **ORDER STATISTIC LÀ
> CÁI TỐT NHẤT RỒI.**

**🔗 See also:** [Miền bác bỏ kiểm định tỉ số khả dĩ](./82_method_of_finding_tests.md#node-efq5sem)

<br>

<a id="node-cadv7we"></a>

###### Sử dụng định nghĩa thống kê đủ

<p align="center"><kbd><img src="assets/ptcxbw00xh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6u80sl3v2r.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là gs cho rằng ta nếu ta **dùng định nghĩa** của sufficient statistic để
> **chứng minh** một statistic T(.) là sufficient statistic thì có thể sẽ rất **cồng
> kềnh** (unwieldly) vì ta sẽ phải làm các bước sau: 
>
>
>
> 1) **Đoán hay chọn hàm số** dùng để tạo một statistic T(.) mà ta nghi là sufficient
>
>
>
>
> 2) **Tìm pdf và pmf** của T(.) 
>
>
>
> (bởi vì mình cần phải chứng minh tỉ số  p(𝐱|θ) / q(T(𝐱)|θ) với p là joint pmf của 𝐗 
> và q là pmf của T(𝐗) là ko phụ thuộc θ, tức là constant)
>
>
>
> Tuy nhiên tiếp theo theorem sẽ cho ta cách khác gọn hơn

<br>

<a id="node-dyi91g8"></a>

###### Định lý Factorization

<p align="center"><kbd><img src="assets/olyc9ad4u1f.png" width="80%"></kbd></p>

> [!NOTE]
> **Factorization theorem**, nói rằng: gọi f(𝐱|θ) là joint pmf/pdf của sample 𝐗. Một
> statistic T(𝐗) được gọi là sufficient statistic cho θ **nếu và chỉ nếu** tồn tại các
> function g(t|θ) và h(𝐱) sao cho: Với mọi sample point 𝐱, và mọi parameter
> points θ ta đều có:
>
>
>
> Nói ngắn gọn: là ta có thể tách f(x|θ) thành tích của một hàm không phụ thuộc
> θ nữa (h(𝐱)) với một hàm phụ thuộc 𝐱 và θ nhưng nhưng chỉ phụ thuộc 𝐱 
> thông qua statistic T(𝐱) mà thôi.
>
>
>
> f(𝐱|θ) = g(T(𝐱)|θ)h(𝐱)
>
>
>
> Để chứng minh chiều đi điều kiện cần, ta giả sử T(𝐱) là một sufficient statistic:
>
>
>
> Thì xét f(𝐱|θ), và đang chứng minh cho discrete case, thì đây là joint pmf
> của 𝐗: P_θ(𝐗 = 𝐱)
>
>
>
> Ta đã biết {𝐗 = 𝐱} ⊂ {T(𝐗) = T(𝐱)} ⇨ {𝐗 = 𝐱, T(𝐗) = T(𝐱)} = {𝐗 = 𝐱}Nên P_θ(𝐗 = 𝐱) = P_θ(𝐗 = 𝐱, T(𝐗) = T(𝐱)}
>
>
>
> = P_θ(𝐗 = 𝐱|T(𝐗) = T(𝐱))*P_θ(T(𝐗) = T(𝐱)) (conditional probability theorem)
>
>
>
> Thế thì cái term thứ nhất, theo định nghĩa của sufficient statistic (là statistic 
> mà P(𝐗=𝐱|T(𝐗)=T(𝐱)) không còn phụ thuộc θ) thì nó sẽ
> không phụ thuộc θ nữa. Nên nó là P(𝐗 = 𝐱|T(𝐗) = T(𝐱)), là một hàm chỉ phụ
> thuộc x: h(𝐱)
>
>
>
> Còn P_θ(T(𝐗) = T(𝐱)), dĩ nhiên đây chính là pmf của statistic T(𝐗), evaluate
> tại T(𝐱), và T(𝐗) là là random variable có distribution vẫn phụ thuộc θ. 
> Ta kí hiệu nó là g(T(𝐱)|θ) 
>
>
>
> Vậy là đã chứng minh xong chiều đi: nếu T(𝐗) là sufficient static, thì 
> f(𝐱|θ) = g(T(𝐱)|θ)h(𝐱)

**🔗 See also:** [Chứng minh Định lý Birnbaum](./63_the_likelihood_principle.md#node-vayutvo) · [Định lý LRT Thống kê đủ](./82_method_of_finding_tests.md#node-gfm4olm) · [Kiểm định chính xác Fisher](./83_methods_of_evaluating_test.md#node-29b2q27)

<br>

<a id="node-4nmqg93"></a>

###### Định lý Factorization: Điều kiện đủ

<p align="center"><kbd><img src="assets/1rjs107l2yt.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/r0zull4dmul.png" width="80%"></kbd></p>

> [!NOTE]
> Để chứng minh chiều về (điều kiện đủ):
>
>
>
> Ta giả sử tồn tại g và h sao cho g(𝐱|θ) = g(T(𝐱)|θ)h(𝐱) ta sẽ chứng
> minh T(𝐗) là sufficient statistic, theo định nghĩa, bằng cách chứng minh tỉ số
> p(𝐱|θ) / q(T(𝐱)|θ) bằng constant nếu xem là function theo θ.
>
>
>
> Rồi, xét tỉ số này, p(𝐱|θ) / q(T(𝐱)|θ) = g(T(𝐱)|θ) h(𝐱) / q(T(𝐱)|θ)
>
>
>
> Định ra A_T(𝐱), là pre-image của {t = T(𝐱)}, tức là tập {𝐲 ∈ R^n: T(𝐲)
> = T(𝐱)}
>
>
>
> Khi đó xét q(T(𝐱)|θ), tức P_θ(T(𝐗) = T(𝐱))
>
>
>
> Đặt T(𝐱) = t0, thì cái mẫu số là P_θ(T = t0)
>
>
>
> {T = t0} ⊂ {T = t0 ∩ Ω} = {T = t0 ∩ (U_z {𝐗 = **z**}) | U_**z**: union qua mọi
> possible value **z** của 𝐗
>
>
>
> = U_**z** (T = t0 ∩ 𝐗 = **z**) (tính chất phân phối (A ∩ (B U C) = (A ∩ B) U
> (A ∩ C))
>
>
>
> = [U_{**z** ∈ At0} (T = t0 ∩ 𝐗 = **z**)] U [U_{**z** không thuộc At0} (T = t0 ∩
> 𝐗 = **z**)]
>
>
>
> ⇨ P(T = t0) = P[U_{**z** ∈ At0} (T = t0 ∩ 𝐗 = **z**)] + P[U_{**z** !∈ At0} (T =
> t0 ∩ 𝐗 = **z**)]
>
>
>
> (Theo axiom 3, xác suất union của hai disjoint event)
>
>
>
> = Σ**z** ∈ At0 P_θ(T = t0 ∩ 𝐗 = **z**) + 0
>
>
>
> = Σ**z** ∈ At0 P_θ(T = t0 ∩ 𝐗 = **z**)
>
>
>
> Đổi dummy variable z thành y cho tiện
>
>
>
> = Σ𝐲 ∈ At0 P_θ(T = t0 ∩ 𝐗 = 𝐲)
>
>
>
> = Σ𝐲 ∈ At0 P_θ(T = t0 | 𝐗 = 𝐲) P(𝐗 = 𝐲)
>
>
>
> = Σ𝐲 ∈ At0 P_θ(T(𝐗) = t0 | 𝐗 = 𝐲) P(𝐗 = 𝐲)
>
>
>
> = Σ𝐲 ∈ At0 [1 * P_θ(𝐗 = 𝐲)]
>
>
>
> Vì X đã bằng y ∈ At0, hay X = y ∈ At0 đã xảy ra, nên dựa trên đó, thì T(𝐗)
> chắc chắn là bằng t0 ⇨ P_θ(T(𝐗) = t0 | 𝐗 = 𝐲) = 1
>
>
>
> = Σ𝐲 ∈ At0 P_θ(𝐗 = 𝐲)
>
>
>
> = Σ𝐲 ∈ At0 f(𝐲|θ)
>
>
>
> Và theo assumption là tồn tại g, h sao cho f(𝐱|θ) = g(T(𝐱)|θ)h(𝐱)
>
>
>
> ⇨ ..= Σ𝐲 ∈ At0 g(T(𝐲)|θ)h(𝐲)
>
>
>
> ⇨ ratio = p(𝐱|θ) / q(T(𝐱)|θ)
>
>
>
> = g(T(𝐱)|θ) h(𝐱) / Σ𝐲 ∈ At0 g(T(𝐲)|θ)h(𝐲)
>
>
>
> Mà trong cái sum này Σ𝐲 ∈ At0 g(T(𝐲)|θ)h(𝐲) thì g(T(𝐲)|θ) là hằng
> số, vì với mọi 𝐲 ∈ At0 thì T(𝐲) luôn bằng t0 (tức T(𝐱))
>
>
>
> ⇨ Σ𝐲 ∈ At0 g(T(𝐲)|θ)h(𝐲) = Σ𝐲 ∈ At0 g(t0|θ)h(𝐲) 
>
>
>
> = g(t0|θ) [Σ𝐲 ∈ At0 h(𝐲)]
>
>
>
> = g(T(𝐱)|θ) Σ𝐲 ∈ At0 h(𝐲)
>
>
>
> ⇨ ratio = g(T(𝐱)|θ) h(𝐱) / g(T(𝐱)|θ) Σy ∈ At0 h(𝐲)
>
>
>
> = h(𝐱) / Σ𝐲 ∈ At0 h(𝐲)
>
>
>
> Kết quả này **không còn phụ thuộc θ nữa**, tức là constant theo θ.
>
>
>
> ⇨ Chứng minh xong

<br>

<a id="node-b24e26s"></a>

###### Tìm Thống kê đủ Factorization

<p align="center"><kbd><img src="assets/hfq9z05bl9r.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/el496kmg7rm.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là. Để áp dụng theorem này trong việc tìm ra sufficient statistic của
> một population parameter θ. Ta sẽ chỉ cần:
>
>
>
> 1) Factor joint pdf/pmf của sample f(𝐱|θ) thành tích của hai phần:
>
>
>
> Một phần không phụ thuộc θ nữa, là h(𝐱)
>
>
>
> Một phần phụ thuộc θ 
>
>
>
> Thì trong cái phần phụ thuộc θ này, ta sẽ xem thử nó phụ thuộc sample **x thông
> qua hàm số nào, thì hàm số đó chính là sufficient statistic.**
>
>
>
> Trong ví dụ này, joint pdf/pmf của sample 𝐗, nhưđã biết từ ví dụ 6.2.4
>
>
>
> và thấy nó có thể được factor thành:
>
>
>
> f(𝐱|μ) = (2πσ²)^(-n/2) exp[-Σ(xi-x̄)^2/(2σ²)] exp(-n(x̄-μ)^2/(2σ²)
>
>
>
> Thế thì cái phần đầu ko dính tới μ, hính là h(𝐱)
>
>
>
> Còn cái phần sau, còn dính tới μ:  exp(-n(x̄-μ)^2/(2σ²)
>
>
>
> thì ta thấy rằng nó chính là hàm g(x̄|μ), tức là nó sẽ phụ thuộc sample value 𝐱
> thông qua T(𝐱) = x̄. Do đó, theo theorem này, T(𝐗) = X̄ chính là sufficient
> statistic cho μ

<br>

<a id="node-dasngh9"></a>

###### Phân phối đều rời rạc

<p align="center"><kbd><img src="assets/fb1oq5dm9vb.png" width="80%"></kbd></p>

> [!NOTE]
> X1,...Xn là random sample từ **discrete uniform** distribution 1,....θ. 
>
>
>
> là sao?
>
>
>
> Có nghĩa là các random variables X1,X2,...Xn là các discrete rvs
> có các possible values là 1,2...θ với x**ác suất bằng nhau**.
>
>
>
> Vậy ví dụ xét X1. Ta biết rằng Σx=1,2...θ P(X1 = x) = 1 theo axiom 2
>
>
>
> ⇔ θ P(X1 = x) = 1 Vì với mọi x = 1,2...θ thì P(X1 = x) đều bằng nhau
>
>
>
> ⇨ P(X1 = x) = 1/θ, x = 1,2..θ 
>
>
>
> Và đây chính là pmf của X1, dĩ nhiên cũng là của X2,....Xn.
>
>
>
> Do đó mới nói pmf của Xj là f(x|θ) = 1/θ với x = 1,2....θ và = 0 otherwise
>
>
>
> Rồi, với việc X1,...Xn iid thì joint pmf = tích marginal pmf
>
>
>
> ⇨ P(𝐗 = 𝐱) = P(X1=x1)*...P(Xn=xn)
>
>
>
> = f(x1|θ)*...f(xn|θ)
>
>
>
> = (1/θ)^n = 1/θ^n = θ^-n khi xi ∈ {1,2,....θ} và = 0 otherwise

<br>

<a id="node-xxwct63"></a>

###### Thống Kê Đủ Factorization

<p align="center"><kbd><img src="assets/69l1arl8y1p.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, vừa rồi mình đã hiểu joint pmf của 𝐗: f(𝐱|θ) = θ^-n với xi ∈ {1,2..,θ} và 0
> otherwise.
>
>
>
> Thế thì, như đã nói, nay nhắc lại cho nhớ, để tìm sufficient statistic của
> θ theo theorem vừa rồi, ta sẽ cần chứng minh f(𝐱|θ) có thể tách thành 
> g(T(𝐱)|θ)h(𝐱), tức là một hàm h(𝐱) không phụ thuộc θ và một hàm còn dính
> đến θ và phụ thuộc **x thông qua một hàm T nào đó, khi đó T(X) chính là
> sufficient statistic.**
>
>
>
> Vậy thì để thấy g, h là gì. Mình sẽ đặt T(𝐱) = maxi xi
>
>
>
> Khi đó, nói xi ∈ {1,2..,θ} đồng nghĩa với nói xi ∈ {1,2....} và maxi xi (tức T(𝐱))
> ≤ θ.
>
>
>
> Đặt h(𝐱) = 1 khi xi ∈ {1,2,..} và 0 otherwise 
>
>
>
> và đặt g(t|θ) = θ^-n khi t ≤ θ và 0 otherwise
>
>
>
> f(𝐱|θ) = θ^-n khi xi ∈ {1,2,..,θ} và 0 otherwise có thể được thể hiện bởi: 
>
>
>
> = g(t|θ)h(𝐱) với mọi 𝐱, và θ
>
>
>
> Vì sao: 
>
>
>
> Xét trường hợp 1: khi xi ∈ {1,2...} và maxi xi ≤ θ thì lúc này:
>
>
>
> h(𝐱) = 1 
>
>
>
> t ≤ θ (vì t = max_i xi) giúp g(t|θ) = θ^-n
>
>
>
> Từ đó ⇨ g(t|θ)h(𝐱) = θ^-n, điều này khớp với việc khi xi ∈{1,2,...θ} thì f(𝐱|θ) 
> = θ^-n
>
> Xét trường hợp 2: Khi xi không thuộc {1,2..θ}, tức xi > θ hoặc xi ≤ 0 thì:
>
>
>
> Trường hợp 2a) xi ≤ 0 thì h(𝐱) = 0, dẫn đến g(t|θ)h(𝐱) = 0
>
>
>
> Trường hợp 2b) xi > θ thì tức max_i xi > θ ⇔ t > θ ⇨ theo định nghĩa hàm 
> g(t|θ), lúc này nó bằng 0, cũng dẫn đến g(t|θ)h(𝐱) = 0.
>
>
>
> Như vậy là ở trường hợp 2 này thì f(𝐱|θ) cũng bằng g(t|θ)h(𝐱)
>
>
>
> Do đó f(x|θ) có thể được factor thành g(t|θ)h(𝐱) với h(𝐱) không phụ thuộc
> θ và hàm g(t|θ) còn phụ thuộc θ và 𝐱 nhưng trong đó phụ thuộc x thông qua
> hàm T(𝐱) = maxi_xi
>
>
>
> Như vậy T(𝐗) = maxi Xi chính là sufficient statistic của θ

**🔗 See also:** [Thống kê đầy đủ đồng nhất](#node-3b33zu7)

<br>

<a id="node-zgc9bub"></a>

###### Thống kê đủ bằng hàm chỉ thị

<p align="center"><kbd><img src="assets/06ptt0uy9r0v.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, ta có thể có cách chứng minh khác rõ ràng hơn bằng cách dùng indicator
> function: Đại khái là vầy. Ta biết I_A(x) sẽ là function mang giá trị 1 khi x ∈ A
> và 0 nếu ngược lại. Vậy thì gọi N là tập các số tự nhiên dương {1,2,...}
> và Nθ = {1,2...θ}.
>
>
>
> Khi đó ta sẽ có thể thể hiện joint pmf của sample 𝐗 theo cách khác:Cách cũ f(𝐱|θ) = P(X1=x1)...P(Xn=xn) = Πi=1:n θ^-1 
>
>
>
> = (θ^-1)^n nếu x1,x2..xn ∈ {1,2..θ} và = 0 otherwise
>
>
>
> Cách mới: f(𝐱|θ) = Πi=1:n θ^-1 I_Nθ(xi) 
>
>
>
> = θ^-n Πi=1:n I_Nθ(xi) 
>
>
>
> Thế rồi, lại xét riêng cái này: Πi=1:n I_Nθ(xi) 
>
>
>
> Đây, như đã biết là tích của I_Nθ(x1) * I_Nθ(x2) * ...* I_Nθ(xn) 
>
>
>
> Rồi, như nói ở trên xi ∈ {1,2..θ} sẽ tương đương nói xi ∈ {1,2..} và
> maxi xi ≤ θ 
>
>
>
> ⇨ Πi=1:n I_Nθ(xi) = Πi=1:n I_N(xi) I_Nθ(maxi xi)
>
>
>
> tức Πi=1:n I_N(xi) I_Nθ(T(𝐱))
>
>
>
> từ đó f(x|θ) = θ^-n Πi=1:n I_N(xi) I_Nθ(T(x))
>
>
>
> = θ^-n I_Nθ(T(x)) Πi=1:n I_N(xi)
>
>
>
> ⇨ Πi=1:n I_N(xi) đóng vai h(𝐱)
>
>
>
> và θ^-n I_Nθ(T(𝐱)) đóng vai g(T(𝐱)|θ)
>
>
>
> Do đó theo Factorization theorem, thì T(𝐗) = maxi Xi là sufficient statistic

<br>

<a id="node-iti6fjz"></a>

###### Thống kê đủ vector

<p align="center"><kbd><img src="assets/dtv5qxfsitt.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại ý là những ví dụ vừa rồi đều là ta thấy **sufficient statistic** T(𝐗), là 
> **scalar**.
>
>
>
> Điều này có nghĩa là, **trong những tình huống này, mọi thông tin của sample
> có thể được gói gọn trong một con số.**
>
>
>
> Tuy nhiên, **có khi** sufficient statistic **lại là nhiều con số** như không phải một.
> Mà thường thường điều này **xảy ra khi population parameter lại là vector**
> chứ không phải scalar.
>
>
>
> Khi đó T(𝐗) là random variable vectors.
>
>
>
> ví dụ 6.2.9 sẽ áp dụng Factorization theorem để chứng minh / tìm sufficient
> statistic cho case này

<br>

<a id="node-hbgg43q"></a>

###### Thống kê đủ phân phối chuẩn

<p align="center"><kbd><img src="assets/0jx0n8dlwgj6.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là xét lại random sample size n X1,X2...Xn ~ n(μ, σ²) với cả hai
> param đều chưa biết. ⇨ ta có vector param Θ = (μ, σ²)
>
>
>
> Joint pdf của sample 𝐗:
>
>
>
> f(𝐱|Θ) = [(1/2πσ²)^(n/2)] {exp (1/2σ²) [-[Σi(xi - x̄)^2 + n(x̄ - μ)^2]]}
>
>
>
> = [(2πσ²)^(-n/2)] exp {(1/2σ²) [-[Σi(xi - x̄)^2 + n(x̄ - μ)^2]]}
>
>
>
> Theo **Factorization theorem**, ta phải chỉ ra nó có dạng của g((T(𝐱)|θ)h(𝐱)
> trong đó hàm h(𝐱) không phụ thuộc Θ. Còn T(𝐱) **SẼ LÀ VECTOR RANDOM
> VARIABLE** để g, còn dính đến Θ và phụ thuộc sample 𝐱 bởi T(). Khi đó
> T(𝐗) sẽ là sufficient statistic cho Θ
>
>
>
> Ở đây ta thấy:
>
>
>
>  Ta chỉ cần quan tâm [-[Σi(xi - x̄)^2 + n(x̄ - μ)^2]]}, vì sao, vì mình cần
> xem thử là đâu là cái hàm còn dính tới Θ, và 𝐱, nhưng chỉ dính đến **x THÔNG
> QUA FUNCITON NÀO ĐÓ**
>
>
>
> Vậy thì, [-[Σi(xi - x̄)^2 + n(x̄ - μ)^2]]}
>
>
>
> Nếu đặt T1(𝐱) = x̄
>
>
>
> và đặt T2(𝐱) = Σi(xi - x̄)^2 / (n-1)
>
>
>
> ⇨  -[ Σi(xi - x̄)^2 + n(x̄ - μ)^2 ]
>
>
>
> =  -[ (n-1)T2(𝐱) + n(T1(𝐱) - μ)^2 ]
>
>
>
> và cả đám đó, chính là: 
>
>
>
> [(2πσ²)^(-n/2)] exp {- [ (n-1)T2(𝐱) + n(T1(𝐱) - μ)^2 ] / 2σ² }
>
>
>
> Thì đây chính là g(T(𝐱)|Θ)
>
>
>
> với T(𝐱) = (T1(𝐱), T2(𝐱)) = (X̄(𝐱)**,** S^2(𝐱))
>
>
>
> Nhớ lại, giáo sư Casella đã từng nói, bản chất X̄, ta phải hiểu nó là **function**
> (apply lên các random variable X1,..Xn để ta có một statistic) nên **hoàn toàn
> có thể ghi** là X̄(𝐱) để chỉ cái function này sẽ tính trung bình cộng
> của các phần tử xi của 𝐱. tương tự như vậy với sample variance S^2
>
>
>
> Như vậy, chỉ việc chọn h(𝐱) = 1
>
>
>
> Thì ta đã show ra rằng f(𝐱|Θ) = g(T(𝐱)|Θ)h(𝐱)
>
> **TỪ ĐÓ** Factorization theorem cho phép **KẾT LUẬN** (X̄(𝐱), S^2(𝐱)) **CHÍNH LÀ
> SUFFICIENT STATISTIC CỦA** sample 𝐗 ~ normal(μ, σ²)

<br>

<a id="node-vofbsvc"></a>

###### Mean, Variance và Giả định Normal

<p align="center"><kbd><img src="assets/nzqkkiueqfm.png" width="80%"></kbd></p>

> [!NOTE]
> Ok. đây là ý quan trọng: gs cho biết, kết quả trên đã **BIỆN MINH CHO
> VIỆC NẾU NHƯ POPULATION THẬT SỰ LÀ NORMAL**, thì việc ta **tính
> sample mean và sample variance là đã đủ để chứa mọi thông tin trong
> sample**.
>
>
>
> Tuy nhiên gs lưu ý, điều này **có thể không đúng với các distribution
> khác**. Có nghĩa là, nếu như với **sample từ distribution khác**, mà ta chỉ
> dùng **sample mean và sample variance** thì có thể ta đã **BỎ SÓT THÔNG
> TIN CHỨA TRONG ĐÓ RỒI.**
>
>
>
> Tương tự, **khi đối diện với một sample**, mà ta **lại chỉ tính sample mean và
> sample variance** thì TA CŨNG **ĐÃ QUÁ DỰA DẪM VÀO GIẢ ĐỊNH RẰNG
> POPULATION LÀ NORMAL**

**🔗 See also:** [Hạn chế Nguyên lý Thống kê Đủ](./63_the_likelihood_principle.md#node-3fske3j)

<br>

<a id="node-yl0xsvo"></a>

###### Thống kê đủ gia đình mũ

<p align="center"><kbd><img src="assets/r9be8t3jpor.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ này cho thấy **sufficient statistic của expo family.**  Rất dễ thấy, là vì cái
> dạng tổng quát của f(x|**θ**) exponential family:
>
>
>
> f(x|θ) = h(x)c(**θ**)exp{Σi wi(**θ**)ti(x)}
>
>
>
> joint pdf của sample ~ expo familty:
>
>
>
> f(𝐱|**θ**) = Πj=1:n h(xj)c(**θ**)exp{Σi wi(**θ**)ti(xj)}
>
>
>
> = Πj h(xj) Πj c(θ) exp{Σi wi(**θ**)ti(xj)}
>
>
>
> phần đầu chính đặt là H(𝐱) = Πj h(xj)
>
>
>
> xét phần sau: Πj c(θ) exp{Σi wi(θ)ti(xj)}
>
>
>
> = Πj c(θ) exp{Σj [Σi wi(θ)ti(xj)] }
>
>
>
> = Πj c(θ) exp{Σi Σj wi(θ)ti(xj) }
>
>
>
> = Πj c(θ) exp{Σj w1(θ)t1(xj) + Σj w2(θ)t2(xj) + ....}
>
>
>
> = Πj c(θ) exp{w1(θ) Σjt1(xj) + w2(θ) Σjt2(xj) + ....}
>
>
>
> = Πj c(θ) exp{w1(θ) T(𝐱)_1 + w2(θ) T(𝐱)_2 + ....}
>
>
>
> với T(𝐱) = (Σjt1(xj), Σjt2(xj),...)
>
>
>
> Và như vậy Πj c(θ) exp{Σi wi(θ)ti(xj)}
>
>
>
> có dạng của g(T(𝐱)|θ) với T(𝐱) là sufficient statistic:
>
>
>
> T(𝐗) = (Σjt1(Xj), Σjt2(Xj),...)

<br>

<a id="node-jul7u6g"></a>

###### Thống kê đủ tối thiểu

<p align="center"><kbd><img src="assets/axukp52nh4j.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/bk43gxmmqcl.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là những phần vừa qua ta đã tìm ra một sufficient statistic đối với
> mỗi model (probability distribution). Nhưng điều ngạc nhiên là, thật ra với 
> bất cứ model nào thì **CŨNG CÓ NHIỀU SUFFICIENT STATISTIC CHỨ
> KHÔNG CHỈ CÓ MỘT.**
>
>
>
> Và ngạc nhiên hơn thì b**ản thân một random sample** 𝐗, bất kì, **đều cũng
> là một sufficient statistic.**
>
>
>
> Lí do là vì, xét joint pdf/pmf của 𝐗: f(𝐱|θ) thì ta chỉ việc coi nó là g(T(𝐱)|θ)h(𝐱)
> với T(𝐱) = 𝐱, và h(𝐱) = 1. Thì khi đó theo Factorization Theorem thì T(𝐗) = **X
> ĐÍCH THỊ LÀ MỘT SUFFICIENT STATISTIC CỦA θ**
>
>
>
> Như vậy, bất kì một random sample 𝐗, nào cũng là một sufficient statistic

<br>

<a id="node-9eienhx"></a>

###### Thống kê đủ và hàm một-một

<p align="center"><kbd><img src="assets/c4pikgfp8pu.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, hệ quả nữa đó là, nếu T(𝐗) là sufficient statistic thì với mọi function
> one-to-one (tức scalar→ scalar) function r, thì rinv(T(𝐗)) cũng là sufficient
> statistic luôn.
>
>
>
> Vì sao?
>
>
>
> đặt T*(𝐗) = r(T(𝐗)) ⇨ T(𝐗) = r_inv(T*(𝐗))
>
>
>
> Vì với T(𝐗) là sufficient statistic như đã biết ta có thể factor f(𝐱|θ) = g(T(𝐱)|θ)h(𝐱)
>
>
>
> = g(r_inv(T*(𝐗))|θ)h(𝐱)
>
>
>
> Như vậy, theo Factorization Theorem, joint pdf/pmf f(𝐱|θ) đã có thể factor thành
> dạng g(T*(𝐗)|θ)h(𝐱), thì như vậy T*(𝐗) cũng là sufficient statistic cho θ
>
>
>
> Vậy thì với nhiều sufficient statistic như vậy, câu hỏi đặt ra sẽ là cái nào là tốt
> nhất.
>
>
>
> Gs nhắc lại ta rằng, mục đích của sufficient statistic là làm sao chứa trọn thông
> tin về population parameter chứa trong random sample, do đó ta sẽ bàn tới
> câu trả lời cho câu hỏi này

<br>

<a id="node-7cxqd8x"></a>

###### Thống kê đủ tối tiểu

<p align="center"><kbd><img src="assets/j9fa1dvf3ei.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái định nghĩa của một **MINIMAL SUFFICIENT STATISTIC**:
>
>
>
> Đó là vầy, T(𝐗) gọi là minimal sufficient statistic nếu như **với mọi
> sufficient statistic** T'(𝐗) **khác thì** T(𝐗) **ĐỀU LÀ FUNCTION CỦA**
> T'(𝐗). Hiểu điều này như sau: Vì T(𝐗) minimal, nên nó là cái gọn nhất
> trong số những cái chứa  đủ thông tin θ (sufficient statistic). Và như vậy,
> kiểu như là những thằng T'(𝐗) chưa đủ gọn, nên có thể cắt gọt chúng nó
> hơn nữa, bởi một function nào đó, để có cái tinh chất / gọn nhất T(𝐗). Do
> đó mọi thằng T(𝐗) đều có thể có một function nào đó apply lên nó và tạo
> ra T(𝐗) ⇨ Đây chính là ý T(𝐗) luôn là một function của T'(𝐗)
>
>
>
> Rồi, lại nói, nếu như mình có hai điểm 𝐱 và 𝐲, có cùng giá trị T': Tức T'
> (𝐱)= T'(𝐲), thì vì T(𝐗) luôn là function g nào đó của T'(𝐗):
> T(𝐗) = g(T(𝐗)) Vậy thì dĩ nhiên là với T'(𝐱) = T'(𝐲) thì g(T'(𝐱))
> = g(T'(𝐲)), tức T(𝐱) = T(𝐲).
>
>
>
> Và hệ quả của nó chính là cái vụ partition.
>
>
>
> Vì ta biết / nhớ cái định nghĩa của A_t: {𝐱 ∈R^n**:** T(𝐱) = t} thì với
> các giá trị khác nhau của t, thì A_t sẽ tạo nên một partition của sample
> space (tức range của 𝐗)
>
>
>
> Vậy thì ở đây, nếu **x,y** ∈B_t', tức {**z** ∈R^n: T'(z) = t' ∈ 𝒯}
> thì như trên ta có T'(𝐱) = T'(𝐲) = t', và g(T'(𝐱)) = g(T'(𝐲)) ⇔
> T(𝐱) = T(𝐲) = g(t). Như vậy điều này chứng tỏ ràng, nếu ông 𝐱, 𝐲
> mà nằm trong A_t' thì chúng cũng nằm trong một partition của T(𝐗) luôn,
> là A_t = A_g(t'). Do đó, cái partition Bt' phải là tập con của At. Và như vậy,
> hình dung ta có cái blob, và chia nó thành 5 phần Bt' thì At sẽ ví dụ như là
> chia nó ra thành những phần to hơn, chứa 5 phần Bt', ví dụ At chia làm 2:
> At1 chứa Bt'1,Bt'2,Bt'3 và At2 chứ hai cái còn lại.
>
>
>
> Bởi vậy mới nói partition gắn với minimal sufficient statistic là cái
> **COARSEST**

<br>

<a id="node-p1f0kzg"></a>

###### Hai thống kê đủ chuẩn

<p align="center"><kbd><img src="assets/ejzic1bp29u.png" width="80%"></kbd></p>

> [!NOTE]
> Ok, đoạn này đại khái nói là: Với ví dụ 6.2.4 nơi ta có sample 𝐗 tứcX1,
> X2... Xn ~ n(μ, σ²) với σ² biết.
>
>
>
> Và ta đã chứng minh rằng sample mean T(𝐗) = X̄(𝐗) (đến đây mình
> có thể hiểu vì sao ghi là X̄(𝐗) rồi) chính là sufficient statistic.
>
>
>
> Nhớ lại thế này, nếu muốn chứng minh lại, sử dụng factorization theorem ta sẽ
> viết joint pdf của sample 𝐗 f(𝐱|θ)ra, và cho thấy nó là một cái tích function của
> một function ko dính tới 𝐱 mà trong case này đơn giản là 1. Và g(T(𝐱)|μ)
> là function dính tới μ và 𝐱 nhưng thông qua T(𝐱), tức X̄(𝐱) = x̄.
> Để từ đó theo factorization theorem ta kết luận T(𝐗) = X̄(X) chính là một
> sufficient statistic.
>
>
>
> Tuy nhiên ta còn nhớ, trong biến đổi đó, nếu mình lôi thêm S^2 vào, tức là thể
> hiện cái joint pdf theo dạng g(T(𝐱) | μ)
>
>
>
> = g((T1(𝐱), T2(𝐱)) | μ)
>
>
>
> = g(X̄(𝐱),S^2(𝐱) | μ) thì ta cũng có thể kết luận random variable
> VECTOR T(𝐗) = (X̄, S^2) cũng là sufficient statistic.
>
>
>
> Thế thì qua đây, đối chiếu với cái định nghĩa của minimal sufficient statistic ta
> thấy quả thật T(𝐗) = X̄(𝐗) (mà ta viết tắt là X̄) chính là một function
> / kết quả của một function app lên T'(𝐗) = (X̄, S^2). Và đó là function:
> r((a,b)) = a.
>
>
>
> Trong bài toán này (trong ví dụ sau ta sẽ thấy) có thể đoán thì X̄ chính là
> minimal sufficient statistic cho θ, tức μ, σ² với σ đã biết. Nên X̄ **có thể luôn
> là function của các sufficient statistic khác**.
>
>
>
> Nhưng nếu σ chưa biết, thì một T(𝐗) = X̄ dĩ nhiên KHÔNG PHẢI LÀ
> SUFFICIENT STATISTIC CỦA Θ = (μ, σ²).

<br>

<a id="node-nbwuekj"></a>

###### Định lý Minimal Sufficient Statistic

<p align="center"><kbd><img src="assets/hj5556bq9j6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xptlxeyfv4.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là, y như định nghĩa của sufficient statistic, nếu như dùng 
> định nghĩa để chứng minh / tìm statistic là một sufficient statistic thì
> sẽ rất khó. Nhớ lại, theo định nghĩa đó, T(𝐗) sẽ là sufficient statistic
> nếu như P(𝐗=𝐱|T(𝐗)=T(𝐱)) không phụ thuộc θ
>
>
>
> Thì từ đó, để dễ hơn, ta mới nhờ đến factorization theorem, nói rằng
> chỉ cần chỉ ra joint pmf/pdf f(𝐱|θ) có thể factored thành g(T(𝐱)|θ)h(𝐱)
> là xong.
>
>
>
> Vậy thì ở đây cũng vậy, ta sẽ nhờ theorem này để chứng minh T(𝐗) là
> minimal sufficient statistic:
>
>
>
> Đại khái là, cho rằng có T(𝐱) thỏa tính chất: Xét hai điểm 𝐱, và 𝐲 thì:
>
>
>
> Nếu như tỉ số f(𝐱|θ) / f(𝐲|θ) = constant khi và chỉ khi T(𝐱) = T(𝐲) **thì khi đó**
> T(𝐗) sẽ chính là minimal sufficient statistic

<br>

<a id="node-m2iuwpb"></a>

###### Chứng minh thống kê đủ

<p align="center"><kbd><img src="assets/mtrkzo0c4ph.png" width="80%"></kbd></p>

> [!NOTE]
> Để chứng minh, đầu tiên ta sẽ giả định rằng f(𝐱|θ) > 0 với mọi 𝐱 ∈X_curl và θ  Mình hiểu: X_curl là range của 𝐗, tức là mọi output khi map
> một possible  outcome s trong original sample space Ω với R^n: X_curl =
> {𝐗(s) for s ∈ Ω}
>
>
>
> Và ở đây, người ta giả định rằng f(𝐱|θ) > 0 với 𝐱 ∈X_curl tức là ta
> hiểu X_curl là **SUPPORT SET** của **X.**
>
>
>
> Rồi, kế tiếp là ta gọi T_curl là image của X_curl bởi statistic T(𝐗):
> {T(𝐱): for some 𝐱 ∈X_curl}
>
>
>
> Thế thì như đã biết, các giá trị khác nhau t của T(𝐱) với 𝐱 ∈ X_curl nó sẽ
> tạo  ra một partition At: {𝐱 ∈ X_curl: T(𝐱) = t} (ví dụ At1 và At2 disjoint vì
> ko thể nào có 𝐱 nào đó mà T(𝐱) vừa = t1 vừa = t2 được)
>
>
>
> Từ đó người ta gọi: 𝐱t là một điểm cố định của mỗi partition At.
>
>
>
> Và với mọi 𝐱 ∈X_curl thì 𝐱_T(𝐱) là cái điểm mà cũng cùng trong
> partition với 𝐱: Chỗ này đại khái là: Với 𝐱 thì ảnh của nó qua T(𝐗):
> T(𝐱) và do đó nó nằm trong cùng partition với A_T(𝐱) = {**z** ∈X_curl:
> T(**z**) = T(𝐱)}, và người ta gọi 𝐱_T(𝐱) hay mình có thể đặt là
> **z**_T(𝐱) cho dễ, là chỉ những điểm trong A_T(𝐱), dĩ nhiên là cũng
> chung partition với 𝐱
>
>
>
> Thế thì: như vậy 𝐱 và 𝐱_T(𝐱) cũng nằm chung một partition là
> A_T(𝐱): nên T(𝐱) = T(𝐱_T(𝐱))
>
>
>
> Xét f(𝐱|θ) và f(𝐱_T(𝐱)|θ) tức là joint pdf của 𝐗 evaluate tại hai điểm
> 𝐱 và 𝐱_T(𝐱):
>
>
>
> Và định lý này ta đang cần chứng minh chiều đi, tức là nếu như: xét hai
> sample point 𝐱 và 𝐲 thì f(𝐱|θ) / f(𝐲|θ)= constant ⇔ T(𝐱) = T(𝐲) thì T sẽ là 
> minimal sufficient statistic. 
>
>
>
>
> Vậy thì ở đây ta giả sử là có tính chất "f(𝐱|θ) / f(𝐲|θ) = constant ⇔ T(𝐱) = T(𝐲)"
> thì ta sẽ chứng minh T là minimal sufficient statistic
>
>
>
> Do đó, từ việc ta đang có T(𝐱) = T(𝐱_T(𝐱)). Ta suy ra = f(𝐱|θ) / f(𝐱_T(𝐱)|θ) là 
> constant (nên tác giả nói tỉ số f(𝐱|θ) / f(𝐱_T(𝐱)|θ) là constant as a function of θ)
>
>
>
> Nên ta sẽ đặt ra hàm h(𝐱) =  f(𝐱|θ) / f(𝐱_T(𝐱)|θ), với ý chính nhấn
> mạnh đây là hàm constant nếu coi như là hàm theo θ.
>
>
>
> Khi đó, ta xét f(𝐱|θ), nhân và chia cho f(𝐱_T(𝐱)|θ):
>
>
>
> f(𝐱|θ) = f(𝐱_T(𝐱)|θ) f(𝐱|θ) / f(𝐱_T(𝐱)|θ)
>
>
>
> = f(𝐱_T(𝐱)|θ) h(𝐱)
>
>
>
> Và đặt hàm g(t|θ) = f(𝐱t|θ): Tức là với một giá trị t, thì g(t|θ) = f(𝐱t|θ) với
> 𝐱t như đã nói ở trên, là điểm cố định mà ta chọn trong mỗi partition At. Ví
> dụ tính g(t1|θ) thì lôi thằng 𝐱_t1 ra, và evaluate joint pmf/pdf tại đó
> f(𝐱_t1|θ).
>
>
>
> Khi đó ta sẽ thấy f(𝐱_T(𝐱)|θ) chính là g(T(𝐱)|θ)
>
>
>
> Từ đó có thể cho thấy f(𝐱_T(𝐱)|θ) h(𝐱) là g(T(𝐱)|θ) h(𝐱)
>
>
>
> Như vậy f(𝐱|θ) = **g**(T(𝐱)|θ) h(𝐱). thì theo Factorization theorem, ta
> có thể kết luận T(𝐗) là **SUFFICIENT STATISTIC**

<br>

<a id="node-seo4hb5"></a>

###### Thống kê đủ tối thiểu

<p align="center"><kbd><img src="assets/sz1y0xiem3h.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, thế thì vừa rồi ta đã chứng minh rằng nếu T(𝐗) là statistic thỏa:
>
>
>
> khi xét 𝐱, 𝐲 là hai điểm mà f(𝐱|θ) / f(𝐲|θ) = constant ⇔ T(𝐱) =
> T(𝐲) thì T(𝐗) nhất định là sufficient statistic.
>
>
>
> Còn giờ ta sẽ chứng minh thêm là T(𝐗) cũng sẽ là minimal:
>
>
>
> Nhớ lại chút xíu về định nghĩa của minimal sufficient statistic: Đó là với mọi T'
> (𝐗) là sufficient statistic bất kì, thì T(𝐗) sẽ đều là một function của T'
> (𝐗), mà cách thể hiện của chuyện này, theo toán học chính là xét 𝐱, 𝐲
> thì nếu T'(𝐱) = T'(𝐲) thì T(𝐱) = T(𝐲) (1)
>
>
>
> (vì theo định nghĩa nếu T(𝐱) phải bằng hàm g nào đó của T'(𝐱): T(x) = g(T'(𝐱)) 
> thì khi vì T'(𝐱) = T'(𝐲) **dĩ nhiên** g(T'(𝐱)) = g'(T'(𝐲)) tức T(𝐱) = T(𝐲)
>
>
>
> Vậy thì, ta sẽ xét 𝐱, 𝐲 là hai điểm sao cho T'(𝐱) = T'(𝐲):
>
>
>
> Và vì đang nói T'(𝐗) là sufficient statistic, nên có thể factor f(𝐱|θ) thành 
> tích của hàm g'(T'(𝐱)|θ) và h'(𝐱) nào đó
>
>
>
> f(𝐱|θ) = g'(T'(𝐱)|θ)h'(𝐱) 
>
>
>
> và f(𝐲|θ) =  g'(T'(𝐲)|θ)h'(𝐲)
>
>
>
> ⇨ f(𝐱|θ) / f(𝐲|θ) = g'(T'(𝐱)|θ)h'(𝐱) / g'(T'(𝐲)|θ)h'(𝐲)
>
>
>
> = h'(𝐱)/h'(𝐲) (do T'(𝐱) = T'(𝐲) ⇨ g'(T'(𝐱)|θ) = g'(T'(𝐲)|θ)
>
>
>
> và cái này không phụ thuộc θ
>
>
>
> Và theo điều mà ta có khi đang chứng minh định lí này:
>
>
>
> "x, y là hai điểm mà f(𝐱|θ) / f(𝐲|θ) = constant ⇔ T(𝐱) = T(𝐲)"  ⇨ T(𝐗) là minimal
> sufficient statistic
>
>
>
> thì ta có quyền từ việc đang có T'(𝐱) = T'(𝐲) ⇨ h'(𝐱)/h'(𝐲) không phụ thuộc θ
> từ đó suy ra T(𝐱) = T(𝐲) và theo (1) giúp kết luận T(𝐗)
> luôn là một function của T'(𝐗) bất kì ⇨ T(𝐗) **LÀ MINIMAL TRONG CÁC
> SUFFICIENT STATISTIC**

<br>

<a id="node-j3awosq"></a>

###### Thống kê đủ tối thiểu phân phối chuẩn

<p align="center"><kbd><img src="assets/apzni7lo44d.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, qua ví dụ này. Cho X1, ...Xn iid ~ n(μ, σ²) và cả hai đều chưa biết.
> Cho 𝐱,  𝐲 là hai sample point và (x̄, s^2_x) và (ybar, s^2_y) là
> sample mean và  variance.
>
>
>
> Dừng lại chút để giải thích chỗ này:
>
>
>
> Ta nhớ lại định nghĩa của random sample size n ~ một population có
> pdf/cdf f hay  F là ta sẽ qua sát một biến cố nào đó n lần. Giá trị quan sát
> được mỗi lần sẽ được  đại diện bởi một random variable Xi. Và các rv X1,..
> .Xn mutually independent  cũng như là identically distributed: có cũng
> marginal pdf/cdf là f/F
>
>
>
> Thế thì, dĩ nhiên các random variable 𝐗 = X1,...Xn vẫn sẽ mang một giá
> trị cụ thể nào đó. Và đó chính là một bộ giá trị quan sát thấy, của một lần
> lấy mẫu (sampling). Và kí hiệu là 𝐱 = (x1,...xn). Tuy nhiên, nếu ta
> sampling lần nữa, X1, ...Xn sẽ mang giá trị khác. Ta sẽ có giá trị cụ thể của
> 𝐗 lần này là **y,** tức (y1,....yn)
>
>
>
> Rồi từ đó ta sẽ có sample mean x̄ và ybar cũng như sample variance
>
>
>
> Thế thì nhớ lại theorem giúp xác định minimal sufficient statistic thay vì
> dùng định nghĩa mà ta vừa chứng minh, nói rằng: Nếu như T(X) là statistic
> thỏa tính chất này: Đó là đối với hai điểm 𝐱, 𝐲. Thì tỉ số f(𝐱|θ) / f(𝐲|θ) là 
> hằng số nếu xét vai trò là function của θ  khi và chỉ khi T(𝐱) = T(𝐲), thì khi
> đó T(X) sẽ là minimal sufficient statistic.
>
>
>
> Vậy thì ta xét  f(𝐱|θ) / f(𝐲|θ).
>
>
>
> = (2πσ²)^(-n/2) exp { - [n(x̄ - μ)^2 + (n-1)sx^2] / (2σ²) }
> / (2πσ²)^(-n/2) exp { - [n(x̄ - μ)^2 + (n-1)sx^2] / (2σ²) }
>
>
>
> = exp([-n(x̄^2 - ybar^2) + 2nμ(x̄ - ybar) - (n - 1)(sx^2 - sy^2) / (2σ²)])
>
>
>
> (Tính chất hàm mũ)
>
>
>
> Và lập luận sẽ là. Để mà cái này không phụ thuộc σ và μ (tức là constant
> as a function of μ và σ ) thì chỉ xảy ra khi x̄ = ybar, và sx^2 = sy^2
> (vì khi đó kết quả trở thành 1 là constant). Như vậy theo theorem này, thì
> T(𝐗)= (X̄, S^2) chính là minimal sufficient statistic

<br>

<a id="node-m5hnxtp"></a>

###### Thống kê đủ tối thiểu phân phối đều

<p align="center"><kbd><img src="assets/r4bno71jesm.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, qua ví dụ này, sample ~ uniform(θ, θ + 1) -inf < θ < inf
>
>
>
> Khi đó joint pdf của 𝐗:
>
>
>
> f(𝐱|θ) = 1 khi θ < xi < θ + 1, với i = 1,2...n và f(𝐱|θ) = 0 otherwise
>
>
>
> Vậy thì: Đại ý là pdf có thể viết thành:
>
>
>
> f(𝐱|θ) = 1 khi max_i xi - 1 < θ < min_i xi (vì đây đồng nghĩa với mọi xi đều
> nằm trong (θ, θ + 1)
>
>
>
> Tương tự, f(𝐲|θ) cũng sẽ bằng 1 khi max_i yi < θ < min_i yi và bằng 0 nếu
> ngược lại.
>
>
>
> Cứ hiểu đơn giản là vầy:
>
>
>
> Giả sử min_i xi, max_i xi là 2, 5 và min_i yi, max_i yi là 3, 6 thì:
>
>
>
> khi đó tùy vào θ nằm trong các khoảng khác nhau mà tỉ số trên sẽ thay đổi:
>
>
>
> Giả sử / giả bộ bỏ qua cái vụ chia 0 ko hợp lệ đi.
>
>
>
> (-inf, 2): 0/0 = 1
>
>
>
> (2, 3): 1/0 = inf
>
>
>
> (3, 5):  1/1 = 1
>
>
>
> (5, 6): 0/1 = 0
>
>
>
> (6, inf): 0/0 = 1
>
>
>
> ⇨ tỉ số lúc thì bằng 0 / 1 / inf, tùy theo / phụ thuộc θ
>
>
>
> Còn hai cái đầu đít trùng nhau , ví dụ đều là 2, 5
>
>
>
> thì tỉ số này sẽ là:
>
>
>
> (-inf, 2): 0/0 = 1
>
>
>
> (2, 5): 1/1 = 1
>
>
>
> (5, inf): 0/0 = 1
>
>
>
> Có nghĩa là, tỉ số này luôn là constant, ko phụ thuộc θ.
>
>
>
> ====
>
>
>
> Như vậy, cái ta đang có ở đây đó là:
>
>
>
> xét hai điểm 𝐱, 𝐲, thì f(x|θ) / f(y|θ) là constant as a function of θ ⇔ min_i
> 𝐱 = min_i 𝐲, và max_i 𝐱 = max_i 𝐲.Mà ta nhớ lại theorem đi:
>
>
>
> nó nói nếu như ta lập luận được / có kết luận rằng: xét hai điểm x, y thì  f(x|θ) /
> f(y|θ) là constant as a function of θ ⇔ T(x) = T(y), thì khi đó theorem này cho
> phép nói T(X) là minimal sufficient statistic
>
>
>
> Như vậy chiếu theo đó, rõ ràng ở đây T(𝐗) = (min_i 𝐗, max_i 𝐗) chính
> là minimal sufficient statistic (vì T(𝐱) chính là vector (min_i 𝐱, max_i 𝐱)
> và T(𝐲) chính là vector (min_i 𝐲, max_i 𝐲)

<br>

<a id="node-zlo20p1"></a>

###### Thống kê đủ tối thiểu

<p align="center"><kbd><img src="assets/2kjyk7tap5d.png" width="80%"></kbd></p>

> [!NOTE]
> Ý cuối là **minimal sufficient statistic cũng ko unique**. Nếu **apply một 1-1
> function** nào vào **minimal sufficient statistic** ta **cũng được một sufficient
> statistic**

<br>

<a id="node-wi56xcm"></a>

###### Statistic phụ trợ

<p align="center"><kbd><img src="assets/97jhlnpdsc9.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là, ta sẽ học qua một loại statistic khác. Gọi là statistic phụ trợ 
> (**ancillary**). Định nghĩa của nó đại khái là một **statistic** mà distribution
> của nó **KHÔNG CÒN PHỤ THUỘC** vào θ nữa.
>
>
>
> Thì ý chính là, cái loại statistic này, dù distribution không còn phụ thuộc
> θ nhưng nghịch lí thay (paradoxically) là **KHI ĐƯỢC LIÊN HỢP VỚI
> CÁC STATISTIC KHÁC, THÌ NÓ LẠI CÓ THỂ GIÚP SUY LUẬN RA
> θ**. Do đó phần này ta sẽ xem vài ví dụ của loại statistic này và phần sau 
> sẽ bàn về cái vừa nói

<br>

<a id="node-abmssuo"></a>

###### Phân phối Range Ancillary

<p align="center"><kbd><img src="assets/420uld9zdtf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xpx2nqjyumk.png" width="80%"></kbd></p>

> [!NOTE]
> Vài điểm chính: Joint pdf của X(1) và X(n) được cho bởi Theorem 5.4.7 (không phải
> là 5.5.7), trong phần đó gs cũng không chứng minh. Nhưng ta ráp công thức này thì
> ta có joint pdf của X(1) và X(n) cũng không khó hiểu lắm, để có g(x(1), x(n)|θ) =
> n(n-1)(x(n) - x(1))^n-2 nếu θ < x(1) < x(n) < θ + 1 và = 0 otherwise
>
>
>
> Dĩ nhiên ta hiểu x(1), x(n) là dummies variable thôi, biểu thị hai input của hàm g sẽ là
> giá trị cụ thể của random variable X(1), và X(n).
>
>
>
> Rồi, xét R, gọi là Range, = X(n) - X(1) và M = [X(1) + X(n)]/2, đương nhiên cũng là
> hai random variables. Áp dụng transformation theorem ta sẽ tìm joint pdf của R,M.
>
>
>
> Review chút xíu về transformation theorem.
>
>
>
> Câu chuyện là ta có joint pdf của X,Y. fXY(x,y). tạo thành random variable vector (X,
> Y). Và (U,V) là kết quả của việc apply một vector → vector function nào đó lên  (X,Y):
> k(X,Y) = (g1(X,Y), g2(X,Y)) sao cho mapping giữa support set của X,Y, kí hiệu là
> A_curl (là tập con của R^2 mà fX,Y(x,y) tại mọi điểm trong đó đều dương) với ảnh
> của nó qua k, tức {(u,v) ∈ R^2: u = g1(x,y), v = g2(x,y) for some x,y ∈ A_curl} là
> mapping 1-1. Nói rõ hơn, có nghĩa là với một (x,y) trong A_curl thì chỉ mapping với
> một (u,v) trong ảnh của A_curl thôi và ngược lại, một (u,v) trong ảnh của A_curl chỉ
> map với đúng một điểm (x,y) trong A_curl thôi (có thể map thêm với một (x,y) khác
> ngoài A_curl, nhưng không thể có hai điểm trong A_curl cùng map với một điểm
> trong ảnh của A_curl)
>
>
>
> Khi đó, từ (u,v) = k(x,y) = g1(x,y), g2(x,y) ta có thể tìm ra (x,y) = h1(u,v), h2(u,v) Và
> transformation theorem cho phép ta tìm joint pdf của U,V từ joint pdf của X, Y:
>
>
>
> fU,V(u,v) = fX,Y(x,y) |∂(x,y)/∂(u,v)|
>
>
>
> = fX,Y(h1(u,v), h2(u,v) |∂(x,y)/∂(u,v)|
>
>
>
> Ở đây. R = X(n) - X(1), tức R = g1(X(1), X(n)) với r = g1(x(1),x(n)) = x(n) - x(1)
>
>
>
> và M = [X(1) + X(n)]/2 ⇨ M = g2(X(1), X(n)) với m = g2(x(1), x(n)) = [x(n) + x(1)]/2
>
>
>
> ⇔ 2m = x(n) + x(1); r = x(n) - x(1) ⇔ 2m - r = 2x(1) ⇔ x(1) = (2m - r)/2
>
>
>
> Và ⇨ x(n) = r + x(1) = r + m - r/2 = (2m + r)/2
>
>
>
> Vậy X(1) = (2M - R)/2 và X(n) = (2M + R)/2
>
>
>
> tức h1(m,r) = (2m - r)/2 và h2(m,r) = (2m + r)/2
>
>
>
> Nên ta có Jacobian: ∂(x,y)/∂(m,r) = [∂/∂m h1(m,r) ∂/∂r h1(m,r); ∂/∂m h2(m,r) ∂/∂r h2(m,
> r)]
>
>
>
> = [1 -1/2;1 1/2] ⇨ |detJ| = |1/2 - (-1/2)| = |1/2 + 1/2| = |1| = 1
>
>
>
> ⇨ fR,M(r,m) = fX(1)X(n)(x(1),x(n)) |J|
>
>
>
> = n(n-1)(x(n) - x(1))^(n-2) * 1 nếu θ < x(1) < x(n) < θ + 1 và = 0 otherwise
>
>
>
> = n(n-1)((2m + r)/2 - (2m - r)/2)^(n-2)   (thế x(1), x(n) vào)
>
>
>
> nếu θ < (2m - r)/2 < (2m + r)/2 < θ + 1 và = 0 otherwise (cũng thế x(1), x(n) vào)
>
>
>
> = n(n-1)(m + r/2 - m + r/2)^(n-2)  nếu 0 < r < 1, θ + (r/2) < m < θ + 1 - r/2
>
>
>
> và = 0 otherwise
>
>
>
> **= n(n-1)r^(n-2)**  nếu 0 < r < 1, θ + (r/2) < m < θ + 1 - r/2 và = 0 otherwise
>
>
>
> ====
>
>
>
> Rồi, tới đây để có marginal pdf của R, ta sẽ marginalizing theo M:
>
>
>
> fR(r) = ∫-inf:inf  fR,M(r,m) dm
>
>
>
> Nhưng fR,M thì chỉ dương khi m từ θ + r/2 đến θ + 1 - r/2:
>
>
>
> ⇨ ... = ∫(θ+r/2) : (θ+1-r/2) fR,M(r,m) dm
>
>
>
> = ∫(θ+r/2) : (θ+1-r/2) n(n-1)r^(n-2) dm
>
>
>
> = n(n-1)r^(n-2) [m|(θ+r/2) : (θ+1-r/2)]
>
>
>
> = n(n-1)r^(n-2) [(θ+1-r/2) - (θ+r/2)]
>
>
>
> = n(n-1)r^(n-2) [θ+1-r/2 - θ-r/2]
>
>
>
> = n(n-1)r^(n-2)(1-r) với 0 < r < 1
>
>
>
> ====
>
>
>
> Thế thì kết quả này có dạng của β pdf với α = n - 1, β = 2
>
>
>
> Và quan trọng là pdf này không phụ thuộc θ. DO ĐÓ R LÀ MỘT ANCILLARY

**🔗 See also:** [PDF đồng thời thống kê thứ tự](./54_order_statistic.md#node-xnvn76c)

<br>

<a id="node-mcs07q3"></a>

###### Thống kê khoảng biến thiên phụ

<p align="center"><kbd><img src="assets/nnqtya4giv.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, gs cho một ý rất hay. Đại khái ông nói là cái kết quả mà ta vừa
> cho thấy, là range R có distribution, tức marginal pdf không phụ thuộc
> vào θ, cho dù nó là một statistic, vốn là một random variable có được 
> từ việc apply một function vào các random variable của random sample
> mà đám này có distribution dĩ nhiên là phụ thuộc θ, tức population parameter
>
>
>
> Thế thì kết quả này không ngẫu nhiên, mà thực ra, nó sẽ  đúng với mọi θ 
> đóng vai trò là location parameter.
>
>
>
> Gemini giải thích chỗ này như sau (và ví dụ sau trong sách sẽ làm rõ hơn)
>
>
>
> Đại khái là ta đã biết location family: thì nếu f(z) là pdf của member chuẩn
> (standard pdf) ứng với location = 0 thì một member khác ứng với location
> θ sẽ có pdf là fX(x) = fZ(x - θ)
>
>
>
> Như vậy, pdf của X sẽ phụ thuộc θ, còn Z thì ko.
>
>
>
> Trong chương trước (location scale family) mình đã học theorem này:
>
>
>
> Z là rv ~ f(z) ⇔ X = σZ + μ sẽ ~ fX(x) = f[(x - μ)/σ] / σ
>
>
>
> Nói bằng lời đó là nếu ta có Z là một random variable thành viên chuẩn
> (location = 0, scale 1) của một location scale family, thì X = σZ + μ sẽ là 
> thành viên có location là μ, scale σ). Ngược lại, nếu ta có X là random
> variable thuộc thành viên có location μ, scale σ thì Z = (X - μ)/σ sẽ là
> thành viên chuẩn.
>
>
>
> Nếu ta có random sample X1,...Xn. và các order statistic X(1),...X(n)
>
>
>
> Thì với mọi random variable Xi, là thành viên có location θ 
>
>
>
> Thì Zi = Xi - θ chính là thành viên chuẩn, có location 0
>
>
>
> Thế thì xét rang R = X(n) - X(1), dĩ nhiên nó cũng sẽ là Xi - Xj nào đó
> và = Zi + θ - (Zj + θ) = Zi - Zj
>
>
>
> Như vậy, R là random variable tạo bởi áp dụng một function lên hai random
> variable có distribution KHÔNG PHỤ THUỘC θ. Do đó R đương nhiên
> có distribution không phụ thuộc θ.

<br>

<a id="node-x76aniu"></a>

###### Thống kê phụ trợ Range

<p align="center"><kbd><img src="assets/fcb2m285xwi.png" width="80%"></kbd></p>

> [!NOTE]
> Thật ra cái example 6.2.18 cũng chính là cái vừa nói.
>
>
>
> Ta hiểu là trong ví dụ này cũng chính là lập luận theo  cái mình vừa lập luận
> nhỉ? Chỉ có điều là ta thấy hơi ngáo chỗ này: 
>
>
>
> Theo thoerem 3.5.6 thì nó
> nói như nãy ta nói, tức là nếu f(z) là pdf  của thằng Z thuộc member chuẩn,
> có location 0, thì pdf của X thuộc  member có location μ sẽ là f(x - μ). Nhưng
> mà trong ví dụ này, ta giả  lại lập luận với cdf. Như vậy ta cần hiểu là cái
> theorem đó cũng apply với cdf à?
>
>
>
> Tức là, nếu F(z) là cdf của thằng Z thuộc member chuẩn có location 0, thì
> cdf của thằng X cùng family nhưng có location μ sẽ là F(x - μ)?
>
>
>
> Chắc cũng ko khó để chứng minh:
>
>
>
> Nếu Z có pdf là fZ(z) là rv thuộc thành viên chuẩn thì Z là rv thuộc gia đình
> ứng với thành viên có location μ và sẽ có pdf là fX(x) = fZ(x - μ) Thế thì từ
> fX(x) = fZ(x - μ), suy ra cdf của X:
>
>
>
> FX(x) = ∫-inf:x fX(t)dt = ∫-inf:x fZ(t - μ)dt
>
>
>
> Đặt u = t - μ ⇨ du = dt và cận tích phân đổi thành -inf - μ = -inf và x - μ   ⇨
> tích phân trở thành ∫-inf:(x-μ) fZ(u)du
>
>
>
> Và đây chính là FZ(x - μ)
>
>
>
> Vậy là theorem trên cũng đúng với cdf.
>
>
>
> Do đó ở đây họ dùng cdf:
>
>
>
> Cách lập luận cũng y như nãy mình làm:
>
>
>
> X1,....Xn là iid từ một location parameter family có location θ. Nên theo
> theorem 3.5.6 thì với Xi ~ member location θ, thì với Zi = Xi - θ sẽ là thành
> viên chuẩn. Và nếu gọi F là cdf của Zi, thì cdf của Xi sẽ là F(x - θ)
>
>
>
> Từ đó, ta xét Range R, = X(n) - X(1). Cụ thể là xét cdf của nó:
>
>
>
> FR(r|θ), có bản chất là P_θ(R ≤ r)
>
>
>
> = P_θ(max_i Xi - min_i Xi ≤ r)
>
>
>
> = P_θ(max_i (Zi + θ) - min_i (Zi + θ) ≤ r)   |  Vì đã nói Xi - θ = Zi là rv ~
> member chuẩn
>
>
>
> = P_θ(max_i (Zi) + θ - min_i (Zi) + θ) ≤ r)  | đưa θ là hằng số ra khỏi max_i,
> min_i
>
>
>
> = P_θ(max_i Zi  - min_i Zi ≤ r)   | khử θ
>
>
>
> và kết quả này ko phụ thuộc θ nữa vì Zi có distribution với location 0, ko phụ
> thuộc θ nữa

**🔗 See also:** [Biến đổi PDF Location-Scale](./35_location_and_scale_families.md#node-cs2rm3i)

<br>

<a id="node-e10it2g"></a>

###### Quan hệ thống kê đủ, phụ trợ

<p align="center"><kbd><img src="assets/i64j0fral.png" width="80%"></kbd></p>

> [!NOTE]
> CÒN VÍ DỤ NÓI VỀ MỘT LẠI ANCILLARY STATISTIC TƯƠNG TỰ ĐỐI
> VỚI CÁC LOCATION FAMILY QUAY LẠI SAU. NHƯNG ĐẠI KHÁI LÀ
> PHẦN SAU SẼ NÓI VỀ QUAN HỆ GIỮA SUFFICIENT  STATISTIC VÀ
> ANCILLARY STATISTIC

**🔗 See also:** [Kỳ vọng theo Định lý Basu](#node-pswxn93)

<br>

<a id="node-7589927"></a>

###### Đủ tối thiểu và phụ trợ

<p align="center"><kbd><img src="assets/u7ntaih9tsb.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, mở đầu gs nhắc ta lại về khái niệm minimal sufficient statistic, đó là nó
> là statistic đạt được mức độ data reduction tốt nhất mà vẫn giữ được mọi
> thông tin về tham số θ. Một cách dễ hiểu thì nó là cái loại bỏ đi hết các thông
> tin thừa thải, không giúp ích gì cho việc suy luận giá trị của tham số θ.
>
>
>
> Còn ancillary statistic như vừa biết, là statistic mà distribution của nó không
> phụ thuộc vào θ. Nên ta có thể nghĩ rằng ancillary statistic và minimal sufficient
> statistic không liên quan đến nhau. Nhưng kì thực không phải vậy. Và phần 
> này sẽ tập trung bàn về quan hệ của chúng.
>
>
>
> Trong ví dụ 6.2.15 thì ta thấy X1,...Xn là iid observation từ uniform(θ, θ + 1)
> và đã chứng minh (X(n) - X(1), (X(n) + X(1))/2) là minimal sufficient statistic
> và rồi trong ví dụ 6.2.17 thì ta thấy X(n) - X(1) lại là ancillary statistic.
>
>
>
> Như vậy có nghĩa là trong trường hợp này ancillary statistic là một phần tạo
> nên minimal sufficient statistic.
>
>
>
> Do đó dĩ nhiên là chúng không độc lập nhau.

<br>

<a id="node-o5sgryc"></a>

###### Suy luận tham số từ Ancillary

<p align="center"><kbd><img src="assets/se724hfmkld.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái ví dụ này mục đích là để cho thấy rằng ancillary statistic có thể giúp
> suy luận ra giá trị của parameter θ dù cho distribution của nó không phụ thuộc
> θ.
>
>
>
> Xét một bộ hai random variable  X1, X2 iid có population distribution với pmf:
> P_θ(X = θ) = P_θ(X = θ + 1) = P_θ(X = θ + 2) = 1/3. với θ chưa biết.
>
>
>
> Và gọi X(1), X(2) là order statistic.
>
>
>
> Thế thì đại ý là ta có thể chứng minh theo cách tương tự như ví dụ trước đây
> để cho thấy rằng random variable vector (R, M) = (X(2)-X(1), [X(1)+X(2)]/2)
> là minimal sufficient statistic. (Chứng minh bằng cách dùng cái theorem 
> bữa trước đó, nói là nếu ta có thể chứng minh statistic T(𝐗) có tính chất giúp
> thỏa: Với hai điểm 𝐱, 𝐲 thì f(𝐱|θ) / f(𝐲|θ) không phụ thuộc θ nếu xét nó như
> function of θ khi và chỉ khi T(𝐱) = T(𝐲) thì khi đó T(𝐗) là minimal sufficient statistic.
>
>
>
> Rồi, và  ta có thể dùng cách tương tự như ví dụ trước để chứng minh distribution
> của rang R không phụ thuộc θ, nên nó là ancillary statistic
>
>
>
> Thế thì, lập luận để cho thấy biết giá trị  của R (ancillary statistic) có thể giúp cho 
> biết / suy luận giá trị của parameter θ:
>
>
>
> Giả sử xét một điểm (r, m) (một giá trị của (R, M):
>
>
>
> Thì, đại khái là, nếu mà ta QUAN SÁT THẤY giá trị này của (R, M). Thì dĩ nhiên
> đồng nghĩa là joint probability của nó dương.
>
>
>
> Tức là event R = r, M = m xảy ra.
>
>
>
> Mà M = m xảy ra ⇔ (X(1)+X(2))/2 = (X1+X2)/2 = m xảy ra.
>
>
>
> Thế thì xét X, nó có 3 possible values: θ, θ + 1, θ + 2.
>
>
>
> Nên để (X1 + X2)/2 = m có thể xảy ra thì ta có thể luận ra một ràng buộc nào đó
> của θ: 
>
>
>
> θ không thể là m + 1 trở lên, vì khi đó X giá trị nhỏ nhất chỉ có thể bằng m + 1
> thì trung bình cộng không thể bằng m được.
>
>
>
> θ cũng không thể bằng m - 3 trở xuống. Vì khi đó thằng lớn nhất chỉ có thể = m. 
> thì trung  bình cộng cũng ko thể bằng m (vì một thằng = m, một thằng nhỏ hơn m)
>
>
>
> Vậy θ sẽ có các giá trị có thể có là m-2, m-1, m.
>
>
>
> Như vậy việc biết được giá trị của M, giúp khoanh vùng phạm vi tìm kiếm cho θ.
>
>
>
> Nhưng bây giờ, nói đến range R, là ancillary statistic, dù cho ta nói distribution
> của nó không phụ thuộc θ, nhưng nếu ta biết R = r = 2. Thì ngay lập tức có:
>
>
>
> [X(1) + X(2)]/2 = m ⇔ X(1) + X(2) = 2m
>
>
>
> X(2) - X(1) = r
>
>
>
> ⇨ 2X(2) = 2m + r ⇔ X(2) = m + r/2 = m + 1
>
>
>
> ⇨ X(1) = 2m - m - 1 = m - 1
>
>
>
> Vậy để mà (R, M) = (2, m) thì X(1), X(2) = m - 1, m + 1
>
>
>
> Mà như vậy thì θ không thể bằng m-2 (vì khi đó X1,X2 có thể bằng m-2,m-1,m,
> không thể có cái nào bằng m+1)
>
>
>
> Tương tự θ  không thể bằng m (vì khi đó X1,X2 có thể bằng m, m+1,m+2, không thể
> có cái nào bằng m-1)
>
>
>
> Do đó biết R = 2 giúp kết luận suy luận giá trị của θ cho dù R chỉ là ancillary statistic

<br>

<a id="node-jcf9e90"></a>

###### Định nghĩa Tính đủ

<p align="center"><kbd><img src="assets/0xj82ysns3nm.png" width="80%"></kbd></p>

> [!NOTE]
> Ta qua một khái niệm quan trọng: Tính đủ: **Completeness**.
>
>
>
> Theo định nghĩa, MỘT FAMILY CÁC PDF/PMF f(t|θ) CỦA MỘT STATISTIC
> T(𝐗) sẽ được gọi là **complete**, nếu như:
>
>
>
> Với mọi θ, **E_θ(g(T)) = 0** thì **PHẢI DẪN ĐẾN g(T) = 0**, hoặc **ĐÍCH THỊ LÀ g(T)
> phải là zero function**. Chứ **không thể nào có một g(T) khác 0 nào mà khiến
> điều trên xảy ra được**.
>
>
>
> Và cái ý g(T) = 0 một cách tuyệt đối được **thể hiện theo toán** bởi xác suất nó
> bằng 0 phải là 1: **P(g(T) = 0) = 1**.
>
>
>
> Thế thì đầu tiên ta mới **xét một statistic**, mà statistic thì dĩ nhiên là một
> random variable có được nhờ **apply một hàm số vào một random sample**.
>
>
>
> Vậy thì ví dụ như ta xét random sample size n=1: 𝐗 = (X1) ~ n(θ, 1). 
>
>
>
> Và xét T(𝐗) = 𝐗 = X1
>
>
>
> Thế thì ta sẽ thấy trong trường hợp này, cái family / gia đình các pdf của T:
> f(t|θ), dĩ nhiên **cũng là family n(θ,1)** sẽ **thỏa điều kiện để được gọi là
> complete** family
>
>
>
> Vì theo định nghĩa, nếu muốn là complete, thì việc E_θ(g(T)) = 0 với mọi θ chỉ
> có thể suy ra g(T) = 0, hay, chỉ có hàm zero function mới có thể khiến điều
> này xảy ra.
>
>
>
> Và trong toán học có cách để chứng minh với n(θ,1) thì muốn điều này xảy ra
> với mọi θ thì chỉ có g(T) = 0 mới được, nên T(𝐗) = X là complete statistic
> và family pdf của nó là một family complete.
>
>
>
> ====
>
>
>
> Còn trong sách gs lấy ví dụ rằng X ~ n(0,1), thì nếu xét g(x) = x, thì Eg(X) = 0
> nhưng đây thật ra **chỉ là một thành viên cụ thể** trong họ. Chứ **nếu xét trong cả
> họ thì việc Eg(X) = 0 ko đúng**. Ví dụ E_θ=10 g(X) = E_θ=10 (X) = 10. Ý nói,
> để mà xét tính complete thì đầu tiên **hồ sơ ứng tuyển phải là: có ông g(T(X))
> nào đó khiến E_θ[g(T)] = 0 với mọi θ**.
>
>
>
> Và theo đó thì ở đây ko thể bắt đầu quy trình xét duyệt với g(x) = x được. Vì
> nó không thỏa E_θg(T) = 0 với mọi θ.
>
>
>
> Nhưng để được duyệt là complete thì **phải chứng minh là nếu mà có cái g(T)
> nào đó khiến E_θ g(T) = 0 thì phải suy ra g(T) = 0**.  Thì **khi đó T(X) mới được
> phong là complete statistic**. Và cái ý cuối gs nói "rằng ta sẽ thấy rằng nếu X
> ~ n(θ,1) thì không có hàm của X nào, TRỪ KHI NÓ LÀ ZERO FUNCTION, thỏa
> E_θ(g(X)) = 0 với mọi θ. Nên n(θ,1) là họ complete

**🔗 See also:** [Tính đầy đủ và ước lượng](./73_methods_of_evaluating_estimators.md#node-8bbly0i)

<br>

<a id="node-8w0tig6"></a>

###### Thống kê đầy đủ nhị thức

<p align="center"><kbd><img src="assets/w22tc6nuz9t.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/s1bf64pt1ei.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, áp dụng vô ví dụ này xét T cho rằng nó có distribution loại binomial(n,p)
> 0 < p < 1. Và cho g là một function mà Ep g(T) = 0. Ta sẽ chứng minh T là 
> complete statistic, đồng nghĩa cũng là nói cả gia đình các pmf f(t|p) = Pp(T = t)
> là một complete family.
>
>
>
> Vậy thì đề bài cho ta có / gọi g là hàm số sao cho Ep[g(T)] = 0. Thì ta phải
> chứng minh rằng: nếu Ep[g(T)] = 0 VỚI MỌI p THÌ PHẢI SUY RA g(T) là 
> hàm zero.
>
>
>
> Rồi, thế thì, ta có Ep[g(T)] = 0, hàm ý là nó bằng 0 với mọi p 
>
>
>
> Theo LOTUS, ta biết ⇔ Σ{mọi possible value t của T} g(t)P(T=t) = 0
>
>
>
> Với T là binomial(n,p), ta nhớ (và có thể dễ dàng derive pmf của nó)
> là P_p(T=t), hay f(t|p) = (n choose t) p^t(1-p)^(n-t)
>
>
>
> ⇨ E_p[g(T)] = Σt=0:n g(t) (n choose t) p^t(1-p)^(n-t)
>
>
>
> Nhân thêm chia bớt (1-p)^n:
>
>
>
> .. = (1-p)^n Σt=0:n g(t) (n choose t) p^t(1-p)^(n-t-n)
>
>
>
> = (1-p)^n Σt=0:n g(t) (n choose t) p^t(1-p)^(-t)
>
>
>
> = (1-p)^n Σt=0:n g(t) (n choose t) p^t/(1-p)^t
>
>
>
> = (1-p)^n Σt=0:n g(t) (n choose t) [p/(1-p)]^t
>
>
>
> Đặt r = p/(1-p)
>
>
>
> = (1-p)^n Σt=0:n g(t) (n choose t) r^t
>
>
>
> Rồi vậy ta có (1-p)^n Σt=0:n g(t) (n choose t) r^t = 0
>
>
>
> Mà (1 - p)^n với 0 < p < 1 sẽ luôn khác 0
>
>
>
> ⇨ .. ⇔ Σt=0:n g(t) (n choose t) r^t = 0
>
>
>
> Nhận xét, đây là một ĐA THỨC BẬC n của r, nên 
>
>
>
> cái tổng này bằng 0 khi và chỉ khi g(t) = 0 với mọi t = 0,1...n
>
>
>
> Vậy là ta đã chứng minh rằng E_p[g(T)] = 0 với mọi p thì g(t) phải = 0
>
>
>
> do đó T là complete statistic.
>
>
>
> Trong sách có nói thêm cái vụ g(t) là hàm zero theo chuẩn trong định nghĩa:
> là P(g(T) = 0) = 1: 
>
>
>
> Dễ thôi:
>
>
>
> Vì T có các possible value là 0,1...n
>
>
>
> Mà đã kết luận g(t) = 0 với mọi t = 0,1...n
>
>
>
> ⇨ g(T) = 0 với mọi possible value của T
>
>
>
> Xét P(g(T) = 0), dĩ nhiên đây là pmf của g(T), evaluate tại 0. Nhưng mình đâu
> có biết hàm g là gì nên ko thể tìm pmf của g(T).
>
>
>
> Nhưng {g(T) = 0} ⊂ Ω
>
>
>
> ⇨ g(T) = 0 ∩ Ω = g(T) = 0
>
>
>
> ⇔ {g(T) = 0} = (g(T) = 0) ∩ (T = 0 U T = 1 U .. U T = n)
>
>
>
> ⇔ {g(T) = 0} = (g(T) = 0 ∩ T = 0) U (g(T) = 0 ∩ T = 1) U ....(g(T) = 0 ∩ T = n)
>
>
>
> ⇨ P(g(T) = 0) = P{(g(T) = 0 ∩ T = 0) U (g(T) = 0 ∩ T = 1) U ....(g(T) = 0 ∩ T = n)}
>
>
>
> mà vế phải là xác suất của ∪ các disjoint event, nên theo axiom 3:
>
>
>
> = Σt=0:n P(g(T) = 0 ∩ T = t)
>
>
>
> Mà xét hai event T = t và g(T) = 0. thì có bản chất là:
>
>
>
> A = {s ∈ Ω: T(s) = t} và B = {s ∈ Ω: g(T)(s) = g(T(s)) = 0}
>
>
>
> Mà xét s ∈ A, tức T(s) = t thì g(T(s)) = g(t), mà ta đã nói g(t) = 0 với mọi t = 0,..n
> nên s cũng thuộc B. Vậy A ⊂ B ⇨ {T = t} ∩ {g(T) = 0} = {T = t} (vì A ⊂ B 
>
>
>
> ⇨ A ∩ B = A)
>
>
>
> Vậy ta có .. = Σt=0:n P(T = t) và đây dĩ nhiên là bằng 1 vì tính valid của pmf.
>
>
>
> Kết luận P_p(g(T) = 0) = 1 với mọi p. nên T là complete statistic

**🔗 See also:** [Chứng minh PDF thống kê thứ tự](./54_order_statistic.md#node-1zc19ro)

<br>

<a id="node-3b33zu7"></a>

###### Thống kê đầy đủ đồng nhất

<p align="center"><kbd><img src="assets/bjzdk32oiv7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vkq0h3nlhen.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, qua ví dụ này X1, ...Xn là iid uniform (0, θ) với 0 < θ < inf.
>
>
>
> Ở đây không chứng minh lại nhưng ta có thể biết T(𝐗) = max_i Xi là một
> sufficient statistic (cách chứng minh đơn giản thôi, ta dùng factorization  theorem,
> nói rằng, nếu có thể chỉ ra hàm joint pdf của 𝐗: f(𝐱|θ) có thể factor thành
> g(T(𝐱)|θ)h(𝐱). Tức là gồm hàm h(𝐱) không còn phụ thuộc θ, và
> g(T(𝐱)|θ)  còn phụ thuộc θ và cả 𝐱 nhưng chỉ phụ thuộc 𝐱 thông qua một
> hàm số T(𝐱) nào đó. Thì khi đó cái statistic T(𝐗) đấy chính là sufficient
> statistic. Nên ở đây, ta  sẽ trước tiên là tìm ra pdf của 𝐗, f(𝐱|θ) = θ^-n khi xi ∈
> {1,2...θ) và f(𝐱|θ) = 0 nếu ngược lại. Rồi đặt hàm h(𝐱) = 1 nếu xi ∈ {1,2...} và
> = 0 otherwise. Và đặt g(t|θ) với t = max_i xi, sao cho g(t|θ) = θ^n nếu t ≤ θ và g(t|θ)
> = 0 nếu t > θ. Khi đó, với cách set up này, ta sẽ xét hai case, là khi xi∈ {1,2..θ}
> và khi xi không thuộc tập này, để chỉ ra rằng à trong case hai case thì f(𝐱|θ) và
> g(t|θ)h(𝐱) đều bằng nhau, giúp kết luận T(𝐗) = max_i Xi chính là sufficient
> statistic.
>
>
>
> Rồi, tiếp, tác giả nhắc đến Theorem 5.4.4 mà ta đã tìm ra pdf của order statistic
> nên vận dụng nó ta có pdf của T(𝐗) (tức là max_i Xi, cũng chính là X(n)) sẽ là:
>
>
>
> f(t|θ) = nt^(n-1)θ^-n khi 0 < t < θ  và f(t|θ) = 0 otherwise.
>
>
>
> Thế thì quay lại đây, mục đích là ta muốn chứng minh tính COMPLETENESS.
>
>
>
> Ôn lại tí xíu: Định nghĩa của complete statistic nói rằng: Nếu như ta có một
> statistic với family các pdf/pmf là g(t|θ) mà nó thỏa tính chất:
>
>
>
> Chỉ có hàm g(t) = 0 mới khiến cho E_θ[g(T)] = 0 với mọi θ,
>
>
>
> Mà phát biểu theo toán học là nếu mà E_θ([g(T)] = 0 với mọi θ thì nó phải imply
> (tạm dịch là đồng nghĩa) rằng chắc chắn g(t) phải bằng 0 với mọi giá trị của θ:
>
>
>
> P_θ(g(T) = 0) = 1
>
>
>
> thì khi đó đây là một complete family và T(𝐗)  là một complete statistic.
>
>
>
> Vậy thì ta sẽ cho rằng (suppose) g(t) là một function thỏa E_θ(g(T)) = 0 với mọi θ.
> Ta thử chứng minh rằng g(t) phải là zero function, g(t) = 0 với mọi t
>
>
>
> Thế thì xét E_θ(g(T)) như vừa mới suppose, đó là g(t) nó khiến E_θ[g(T)] **= 0 với
> mọi θ**, vậy thì đương nhiên đồng nghĩa khi ta xem E_θ[g(T)] là một  function theo
> θ thì nó là constant function, vì θ bao nhiêu thì nó cũng bằng 0.
>
>
>
> Do đó ta mới được quyền nói đạo hàm của cái hàm này theo θ phải bằng 0.
>
>
>
> d/dθ E_θ[g(T)] = 0
>
>
>
> Thể hiện E_θ[g(T)], theo LOTUS: = ∫-inf:inf g(t)f(t|θ)dt
>
>
>
> = ∫0:θ g(t)nt^(n-1)θ^(-n)dt    (Thay pdf của T vô thu cận tích phân chỉ còn 0→θ)
>
>
>
> = θ^(-n) ∫0:θ g(t)nt^(n-1)dt   (θ^(-n) không phụ thuộc t đưa ra ngoài tích phân)
>
>
>
> ⇨ d/dθ E_θ[g(T)] = 0
>
>
>
> ⇔ d/dθ [θ^(-n) ∫0:θ g(t)nt^(n-1)dt] = 0
>
>
>
> Dùng product rule vì đây là tích của hai tern phụ thuộc θ:
>
>
>
> ⇔ d/dθ [θ^(-n)] ∫0:θ g(t)nt^(n-1)dt + θ^(-n) d/dθ ∫0:θ g(t)nt^(n-1)dt
>
>
>
> Xét term 2 trước: θ^(-n) d/dθ ∫0:θ g(t)nt^(n-1)dt
>
>
>
> Nhớ lại FTC1 nói rằng: Nếu G(x) được định nghĩa bởi ∫-inf:x f(t)dt thì G là nguyên
> hàm (anti-derivative) của f và ta có d/dx G(x) = f(x).
>
>
>
> Còn FTC2 nói rằng, nếu G là nguyên hàm của f thì ta có ∫a:b f(x)dx = G(b) - G(a)
>
>
>
> Vậy Nếu ta xét cái function ∫0:θ g(t)nt^(n-1)dt là hàm theo θ, gọi nó là G(θ) thì theo
> FTC1, G(t) chính là nguyên hàm của f(t) = g(t)nt^(n-1), từ đó ta có:
>
>
>
> d/dθ G(θ) = f(θ) = g(θ)nθ^(n-1)
>
>
>
> Như vậy d/dθ ∫0:θ g(t)nt^(n-1)dt chính là g(θ)nθ^(n-1)
>
>
>
> ⇨ term 2 = θ^(-n)g(θ)nθ^(n-1)
>
>
>
> Rồi, xét term 1: d/dθ [θ^(-n)] ∫0:θ g(t)nt^(n-1)dt
>
>
>
> thì khỏi cần xét cái đạo hàm của θ^-n. Tập trung vào ∫0:θ g(t)nt^(n-1)dt, thì nó
> chính là ∫0:θ g(t)f(t|θ)dt, tức là E_θ[g(T)], mà như đã nói, cái này bằng 0.
>
>
>
> Vậy kết quả ta có: d/dθ E_θ[g(T)] = 0 + θ^(-n)g(θ)nθ^(n-1) = θ^(-n)g(θ)nθ^(n-1)
>
>
>
> = θ^(-1)ng(θ)
>
>
>
> Và cái này d/dθ E_θ[g(T)] = 0 ⇨ θ^(-1)ng(θ) = 0,
>
>
>
> trong khi đó θ^(-1)n khác 0
>
>
>
> nên suy ra g(θ) phải bằng 0 với mọi θ. Kết luận f(t|θ) là complete family
>
>
>
> ====
>
>
>
> Cuối cùng đại khái tác giả lưu ý là phần chứng minh trên ta đã áp dụng FTC, vốn
> chỉ được apply với các function gọi là Riemann-integrable. Tuy nhiên, thực tế ta
> có thể chấp nhận vì đại ý là hầu như mọi function có thể nghĩ ra đều là
> Reiman-integrable

**🔗 See also:** [Thống Kê Đủ Factorization](#node-xxwct63)

<br>

<a id="node-rrvib6m"></a>

###### Định lý Basu

<p align="center"><kbd><img src="assets/yeicwa5lyi.png" width="80%"></kbd></p>

> [!NOTE]
> Basu's Theorem: Nói rằng, nếu T(𝐗) complete và minimal sufficient statistic
> thì T(𝐗) sẽ độc lập với mọi ancillary statistic khác.
>
>
>
> Để chứng minh thì đầu tiên gọi S(𝐗) là một ancillary statistic bất kì, theo định
> nghĩa, thì distribution của nó sẽ không phụ thuộc θ.
>
>
>
> Nên xét pmf (gs nói ta sẽ chỉ chứng minh cho discrete case) P(S(𝐗) = s) sẽ
> không phụ thuộc θ, cái này dễ hiểu.
>
>
>
> Rồi, xét P(S(𝐗) = s | T(𝐗) = t), thì xét event {S(𝐗) = s | T(𝐗) = t}, có bản chất
> là {o in Ω, T(𝐗)(o) = t: S(𝐗)(o) = s} = {o in Ω, T(𝐗)(o) = t: S(𝐗(o)) = s}
>
>
>
> = {o in Ω, T(𝐗(o)) = t: 𝐗(o) = 𝐱 & S(𝐱) = s}
>
>
>
> = {𝐗 ∈{𝐱: S(𝐱) = s} | T(𝐗) = t}
>
>
>
> ⇨ P(S(𝐗) = s | T(𝐗) = t) = P(𝐗 ∈{x: S(x) = s} | T(𝐗) = t)
>
>
>
> Mục đích là, để chuyển thành conditional pdf của 𝐗.Khi đó sử dụng định nghĩa của sufficient statistic T(𝐗): P(𝐗 = 𝐱 | T(𝐗) = T(𝐱))
> không phụ thuộc θ nữa.
>
>
>
> Nên P(𝐗 ∈ {𝐱: S(𝐱) = s} | T(𝐗) = t) không phụ thuộc θ
>
>
>
> ===
>
>
>
> Rồi, để chứng minh S(𝐗) và T(𝐗) độc lập ta có thể chứng minh:
>
>
>
> P(S(𝐗) = s | T(𝐗) = t) = P(S(𝐗) = s) (Stat110 đã học, vì khi đó chứng tỏ T(𝐗) = t
> không bổ sung thêm bất cứ thông tin gì về xác suất của event S(𝐗) = s)
> Hoặc P(A|B) = P(A) chứng tỏ P(A|B)P(B) = P(A)P(B) ⇔ P(A ∩ B) = P(A)P(B)
> đây là định nghĩa của independent event)
>
>
>
> Thế thì xét P(S(𝐗) = s)
>
>
>
> có bản chất là  P({o ∈ Ω: S(𝐗(o)) = s})
>
>
>
> Dĩ nhiên {o ∈ Ω: S(𝐗(o)) = s} ⊂ Ω 
>
>
>
> ⇨ {o ∈ Ω: S(𝐗(o)) = s} = {o ∈ Ω: S(𝐗(o)) = s} ∩ {o ∈ Ω} 
>
>
>
> = {o ∈ Ω: S(𝐗(o)) = s} ∩ U_{mọi possible value t của T} {o ∈ Ω: T(o) = t}
>
>
>
> Dùng distributive law:
>
>
>
> = U_{mọi possible value t của T} [ {o ∈ Ω: S(X(o)) = s} ∩ {o ∈ Ω: T(o) = t}
>
>
>
> đây cũng chính là 
>
>
>
> = U_{mọi possible value t của T} (S(𝐗) = s, T(𝐗) = t)
>
>
>
> ⇨ P(S(𝐗) = s) = P[U_{mọi possible value t của T} (S(𝐗) = s, T(𝐗) = t)]
>
>
>
> Mà vế phải là unions của các disjoint event, theo axiom 3
>
>
>
> = Σ_{mọi possible value t của T} P(S(𝐗) = s, T(𝐗) = t)
>
>
>
> Dùng theorem conditional probability, chú ý P(T(𝐗) = t) có phụ thuộc θ 
>
>
>
> = Σ_{mọi possible value t của T} P(S(𝐗) = s | T(𝐗) = t)P_θ(T(𝐗) = t)
>
>
>
> = Σ_t ∈ T_curl P(S(𝐗) = s | T(𝐗) = t)P_θ(T(𝐗) = t)
>
>
>
> Vậy tới đây ta có:
>
>
>
> P(S(𝐗) = s) = Σ_t ∈ T_curl P(S(𝐗) = s | T(𝐗) = t)P_θ(T(𝐗) = t) (1)
>
>
>
> Rồi, tiếp theo: 
>
>
>
> Tác giả nói Σ_t ∈ T_curl P_θ(T(𝐗) = t) = 1, điều này đơn giản là vì
>
>
>
> Bản chất vế trái là Σ_t ∈ T_curl P_θ({o ∈ Ω: T(X)(o) = t)) 
>
>
>
> = P(U_t ∈ T_curl {o ∈ Ω: T(o) = t}) = P({o ∈ Ω}) = P(Ω) = 1 theo axiom 1
>
>
>
> Nên P(S(𝐗) = s) = P(S(𝐗) = s) * 1 
>
>
>
> = P(S(𝐗) = s) * Σ_t ∈ T_curl P_θ(T(𝐗) = t) (vì cái tổng này bằng 1)
>
>
>
> = Σ_t ∈ T_curl P(S(𝐗) = s)P_θ(T(𝐗) = t) (đưa cái P(S(X) = s) vô trong tổng)
>
>
>
> Vậy P(S(𝐗) = s) = Σ_t ∈ T_curl P(S(𝐗) = s)P_θ(T(𝐗) = t) (2)
>
>
>
> Viết lại (1) và (2) gần nhau:
>
>
>
> P(S(𝐗) = s) = Σ_t ∈ T_curl P(S(𝐗) = s | T(𝐗) = t)P_θ(T(𝐗) = t)
>
>
>
> P(S(𝐗) = s) = Σ_t ∈ T_curl P(S(𝐗) = s)P_θ(T(𝐗) = t) 
>
>
>
> Trừ vế theo vế:
>
>
>
> 0 = Σ_t ∈ T_curl { P(S(𝐗) = s | T(𝐗) = t)P_θ(T(𝐗) = t) - P(S(𝐗) = s)P_θ(T(𝐗) = t) }
>
>
>
> ⇔ 0 = Σ_t ∈ T_curl { [P(S(𝐗) = s | T(𝐗) = t) - P(S(𝐗) = s)] * P_θ(T(𝐗) = t) }
>
>
>
> Và nếu lấy cái term này ra P(S(𝐗) = s | T(𝐗) = t) - P(S(𝐗) = s), và xem nó như
> hàm theo t. g(t)
>
>
>
> thì ta sẽ có vế phải = Σ_t ∈ T_curl { g(t) * P_θ(T(𝐗) = t) }
>
>
>
> và đây chính là gì? Chính là công thức LOTUS tính E_θ[g(T)]
>
>
>
> Vậy ta có 0 = E_θ[g(T)] với mọi θ 
>
>
>
> =====
>
>
>
> Rồi, thế thì ta đang có T(𝐗) là complete statistic (và minimal sufficient statistic)
> nên dĩ nhiên theo định nghĩa của complete statistic, điều trên đồng nghĩa g(t)
> phải bằng 0 với mọi possible value t của T.
>
>
>
> Mà g(t) là gì, ở trên ta đặt nó là hàm theo t, dĩ nhiên g(T) là một statistic:
>
>
>
> g(**T**) = P(S(𝐗) = s | T(𝐗) = t) - P(S(𝐗) = s)
>
>
>
> Và kết luận vừa rồi g(**T**) = 0 nên
>
>
>
> P(S(𝐗) = s | T(𝐗) = t) - P(S(𝐗) = s) = 0
>
>
>
> ⇔ P(S(𝐗) = s | T(𝐗) = t) = P(S(𝐗) = s)
>
>
>
> Giúp kết luận S(𝐗) và T(𝐗) independent

<br>

<a id="node-d4sl8g4"></a>

###### Thống kê đầy đủ họ hàm mũ

<p align="center"><kbd><img src="assets/orbz3t1be.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/abvfpy3yn07.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Basu theorem sẽ rất hữu ích, và nó cho phép ta chứng minh tính
> độc lập của hai statistic mà không cần tìm joint distribution của hai statistic.
> Tuy nhiên để mà dùng nó thì ta cần phải chứng minh cho thấy rằng statistic
> là complete statistic mà quá trình này có khi phức tạp.
>
>
>
> May mắn là ta có một theorem dưới đây cover hầu như phần lớn trường
> hợp
>
>
>
> Cho X1,...Xn là iid observations từ một exponential family với pdf hoặc pmf
> có dạng f(x|**θ**) = h(x)c(**θ**)exp(Σj=1:k wj(**θ**)tj(x))
>
>
>
> Với **θ** = (θ1,...θk). Khi đó statistic T(𝐗) = (Σi=1:n t1(Xi), Σi=1:n t2(Xi),...
> Σi=1:n tk(Xi))
>
>
>
> Chính là complete statistic miễn là parameter space Θ chứa tập mở trong
> R^k.
>
>
>
> Như đã nói. gs sẽ không chứng minh theorem này, chỉ nói thêm là sở dĩ phải
> đưa ra rằng buộc rằng parameter space Θ chứa một open set trong R^k
> là để tránh một số trường hợp.

<br>

<a id="node-pswxn93"></a>

###### Kỳ vọng theo Định lý Basu

<p align="center"><kbd><img src="assets/h0kri149moo.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/8p2eit5zhn.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại khái là ở đây cho biết X1,...Xn là iid exponential (θ). Và ta muốn
> tính kì vọng của g(𝐗) = Xn / (X1 + ... Xn)
>
>
>
> Đầu tiên, vì exponential family là scale parameter family nên theo example
> 6.2.19 thì g(𝐗) là ancillary statistic (chỗ này tạm biết vậy vì mình đã skip
> ví dụ 6.2.19). Còn nhớ lại ancillary statistic là vì g(𝐗) có distribution
> không phụ thuộc θ.
>
>
>
> Và exponential distribution thì cũng tạo nên một exponential family với t(x) =
> x, nên theo theorem 6.2.25 thì T(𝐗) = Σi Xi là complete statistic, và theorem 
> 6.2.10 T(𝐗) là sufficient statistic. Là sao ta?
>
>
>
> Đầu tiên nhớ lại pdf của X ~ expo(θ): fX(x) = (1/λ) e^(-x/λ) với x > 0
>
>
>
> = (1/λ) exp[(-1/λ)(x)], với x > 0
>
>
>
> Và cái này chính là, có thể ghi là:
>
>
>
> = I{x > 0} (1/λ) exp[(-1/λ)(x)]
>
>
>
> Đặt h(x) = I{x > 0}, **θ** = (λ), c(**θ**) = 1/λ, k = 1, w1(**θ**) = w1(λ) = -1/λ
>
>
>
> tj(x) = x
>
>
>
>  ... = h(x) c(**θ**) exp[Σj=1:k wj(**θ**) tj(x)] 
>
>
>
> Và đây là dạng của exponential family 
>
>
>
> Vậy nên dĩ nhiên expo distribution là một thành viên của expo family.
>
>
>
> ====
>
>
>
> Rồi, xét joint pdf của X1,...Xn ~ expo(λ), vì iid nên joint pdf = tích marginal pdf:
>
>
>
> f𝐗(𝐱) = fX1(x1)...fXn(xn) 
>
>
>
> = Πi=1:n { h(xi) c(**θ**) exp[Σj=1:k wj(**θ**) tj(xi)] }
>
>
>
> Đặt h(xi) = I{xi > 0}, **θ** = (λ), c(**θ**) = 1/λ, k = 1, w1(**θ**) = w1(λ) = -1/λ, tj(xi) = xi
>
>
>
> = Πi=1:n { h(xi) } [c(**θ**)]^n Πi=1:n exp[Σj=1:k wj(**θ**) tj(xi)] }
>
>
>
> Đặt H(𝐱) = Πi=1:n { h(xi) }
>
>
>
> Đặt C(**θ**) = [c(**θ**)]^n
>
>
>
> = H(𝐱) C(**θ**) Πi=1:n exp[Σj=1:k wj(**θ**) tj(xi)] 
>
>
>
> = H(𝐱) C(**θ**) exp[Σi=1:n Σj=1:k wj(**θ**) tj(xi)] 
>
>
>
> Đặt Tj(𝐱) = Σi=1:n tj(xi)
>
>
>
> = H(𝐱) C(**θ**) exp[Σj=1:k wj(**θ**) Tj(𝐱)] (1)
>
>
>
> Tới đây ra nhắc lại dáng của exponential family: 
>
>
>
> f(x|**θ**) = h(x) c(**θ**) exp[Σj=1:k wj(**θ**) tj(x)] 
>
>
>
> mà nếu như với x là vector 𝐱 thì dạng của nó sẽ là: 
>
>
>
> f(𝐱|θ) = h(𝐱) c(θ) exp[Σj=1:k wj(**θ**) tj(𝐱)] (2)
>
>
>
> Vậy (1) so với (2) sẽ thấy tj(𝐱) (của (2) chính là 
>
>
>
> Tj(𝐱) = Σi=1:n tj(xi) (tj của (0), tj(x) = x) 
>
>
>
> = Σi=1:n (xi)
>
>
>
> Do đó, theo Theorem 6.2.25, nói rằng nếu X1,...Xn là iid ~ exponential family
> có pdf/pmf có dạng f(𝐱|θ) = h(x) c(**θ**) exp[Σj=1:k wj(**θ**) tj(x)] thì... 
>
>
>
> statistic T(𝐗) = (Σi=1:n t1(Xi), Σi=1:n t2(Xi),...Σi=1:n tk(Xi))
>
>
>
> sẽ là complete statistic (as long as...blah blah tính sau)
>
>
>
> Vậy thì đối chiếu vào ví dụ này, thì ta có k = 1, vì vector **θ**, từ đầu đến giờ chỉ 
> nói, đã hiểu, chỉ có một λ mà thôi. Và tj(x) = x, hay cũng là t1(x) chính là = x
>
>
>
> ⇨ T(𝐗) = Σi=1:n t1(Xi) chính là Σi=1:n Xi
>
>
>
> Vậy nên T(𝐗) = Σi=1:n Xi chính là complete statistic (lưu ý, ta chỉ là phân tích
> để thấy tại sao joint pdf của X1,..Xn, có dạng của exponential family, để thấy
> các thành phần h, c, t, k là gì. Và mục đích cũng là giúp khi áp dụng theorem, 
> thì thấy cái nào là complete statistic. Trong suốt quá trình, nhớ rằng, với expo
> distribution (vốn chỉ là một trong các thành viên của expo family) thì nó chỉ có
> một param λ, nên k = 1. Và cái hàm tj(x) là identity fucntion: tj(x) = x.
>
>
>
> ====
>
>
>
> Vậy thì T(𝐗) = Σi=1:n Xi là complete statistic.
>
>
>
> Và nó cũng sufficient statistic theo theorem 6.2.25.
>
>
>
> Nên theo theorem Basu thì T(𝐗) (complete statistic) và g(𝐗) (ancillary statistic)
> sẽ độc lập, điều này sẽ giúp ta tính được câu hỏi là Eg(𝐗)
>
>
>
> Vì ta có g(𝐗)T(𝐗) = [Xn / (Σi Xi)] (Σi Xi) = Xn
>
>
>
> ⇨ E[g(𝐗)T(𝐗)] = EXn = θ (hay cũng là λ đó)
>
>
>
> ⇔ Eg(𝐗) ET(𝐗) = θ (vì g(𝐗), T(𝐗) độc lập nên kì vọng của tích = tích kì vọng)
>
>
>
> ⇔ Eg(𝐗) = θ / ET(𝐗) = θ / (nθ) (vì ET(𝐗) = E(ΣXi) = Σ EXi = Σθ = nθ)
>
>
>
> = 1/n

**🔗 See also:** [Quan hệ thống kê đủ, phụ trợ](#node-e10it2g)

<br>

<a id="node-st8akyc"></a>

###### Thống kê đủ và hoàn chỉnh X̄

<p align="center"><kbd><img src="assets/3bi4ml45de5.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là 6.2.4 ta đã chứng minh X̄ (sample mean) của iid n(μ, σ²)
> random sample là sufficient statistic, bằng cách dùng theorem (6.2.2) nói rằng
> nếu f(𝐱|θ) / f(T(𝐱)|θ) không phụ thuộc θ, hoặc, là một constant nếu xem như
> là một function of θ, với mọi 𝐱. Thì có thể kết luận X̄ là sufficient statistic.
>
>
>
> Rồi, tác giả nói dùng Theorem 6.2.25 có thể chứng minh X̄ là complete
> statistic, thử làm xem sao:
>
>
>
> Đầu tiên là phân tích xem tại sao pdf của Xi ~ n(μ, σ²) sẽ khớp với exponential
> family từ đó áp dụng cái theorem này.
>
>
>
> pdf của n(μ, σ²)
>
>
>
> f(x|μ,σ²) = [1/√(2πσ)] exp[-(x-μ)^2/(2σ²)]
>
>
>
> Mình cần cho thấy dạng của expo family h(x)c(**θ**)exp[Σj=1:k wj(**θ**)tj(x)]
>
>
>
> = [1/√(2πσ)] exp[-(x^2 - 2xμ + μ²)/(2σ²)]
>
>
>
> = [1/√(2πσ)] exp[(-x^2 + 2xμ - μ²)/(2σ²)]
>
>
>
> = [1/√(2πσ)] exp[-x^2/(2σ²) + 2xμ/(2σ²) - μ²/(2σ²)]
>
>
>
> = [1/√(2πσ)] exp[-x^2/(2σ²)] exp[2xμ/(2σ²)] exp[-μ²/(2σ²)]
>
>
>
> = [1/√(2πσ)] exp[-μ²/(2σ²)] exp[-x^2/(2σ²) + 2xμ/(2σ²)]
>
>
>
> = [1/√(2πσ)] exp[-μ²/(2σ²)] exp[ -1/(2σ²) . x^2 + 2μ/(2σ²) . x]
>
>
>
> = [1/√(2πσ)] exp[-μ²/(2σ²)] exp[2μ/(2σ²) . x -1/(2σ²) . x^2]
>
>
>
> Đặt h(x) = 1, **θ**=(μ, σ), c(**θ**) = exp[-μ²/(2σ²)]/√(2πσ)
>
>
>
> w1(**θ**) =2μ/(2σ²), t1(x) = x
>
>
>
> w2(**θ**) = -1/(2σ²), t2(x) = x^2
>
>
>
> ⇨ pdf = h(x)c(**θ**)exp[Σj=1:k wj(**θ**)tj(x)], nên normal là thành viên của exponential
> family
>
>
>
> Rồi, xét joint pdf, cũng bằng tích marginal pdf:
>
>
>
> f(𝐱|θ, σ²) = Πi=1:n [1/√(2πσ)] exp[-μ²/(2σ²)] exp[2μ/(2σ²) . xi -1/(2σ²) . xi^2]
>
>
>
> = Πi=1:n [1/√(2πσ)] exp[-μ²/(2σ²)] Πi=1:n exp[2μ/(2σ²) . xi -1/(2σ²) . xi^2] (***)
>
>
>
>
> Đặt C(**θ**) = Πi=1:n [1/√(2πσ)] exp[-μ²/(2σ²)]
>
>
>
> .. = C(**θ**) exp {Σi=1:n [2μ/(2σ²) . xi -1/(2σ²) . xi^2]}
>
>
>
> = C(θ) exp { [2μ/(2σ²)] Σi=1:n xi - [1/(2σ²)] Σi=1:n xi^2 }
>
>
>
>
> Đặt T1(𝐱) = Σi=1:n xi, T2(𝐱) = Σi=1:n xi^2, h(𝐱) = 1
>
>
>
> joint pdf có dạng:
>
>
>
> h(𝐱) C(**θ**) exp [ w1(**θ**) T1(𝐱) + w2(**θ**) T2(𝐱) ] 
>
>
>
> ⇨ Cũng chính dạng là exponential family 
>
>
>
> Và qua đó cho thấy ứng với theorem 6.2.25, thì vector (T1(𝐗), T2(𝐗)) 
>
>
>
> = (Σi Xi,  Σi Xi^2) là **complete statistic**.
>
>
>
> ====
>
>
>
> Vấn đề là, trong sách, đang nói trường hợp ta biết σ²/n, thì ta sẽ có thể cho thấy
> family n(μ, σ²/n) là complete family, và vì đây là distribution của X̄, nên nó là
> complete statistic của μ. Chỗ này phải cẩn thận, nên cần ôn lại một chút.
>
>
>
> Cái phân tích ở trên, là mình đang dựa vào theorem 6.2.25, để mình kết luận rằng
> (T1(𝐗), T2(𝐗)) = (Σi Xi,  Σi Xi^2) là complete statistic. Vậy thì, nhớ rằng, theo định
> nghĩa, complete là tính chất của một family of distribution. Nên nói (Σi Xi,  Σi Xi^2)
> là complete statistic, tức là nói family of distribution của nó, là complete family.
> Và ngay ở đây, mình chưa biết cái distribution của (Σi Xi,  Σi Xi^2) là gì, nhưng
> nếu gọi **θ** là vector parameters của cái distribution này, thì (Σi Xi,  Σi Xi^2) chính
> là complete statistic của **θ.**
>
>
>
> Rồi, quay lại đoạn trên mà mình đang làm rõ. Thì theo sách, nói rằng ta có thể
> chứng minh theo theorem 6.2.25 để chỉ ra n(μ, σ²/n) là một complete family,
> để rồi vì đây là distribution của X̄, nên dĩ nhiên X̄ là complete statistic của
> μ (vì μ, với σ²/n đã biết thì nó chính là θ - ý là parameter)
>
>
>
> Như vậy, để dùng 6.2.25, thì mình sẽ phân tích cái pdf của n(μ, σ²/n), để chỉ ra
> nó ứng với exponential family với t, h, c, k là gì. Khi đó theorem này sẽ giúp kết 
> luận được complete statistic là gì. Dĩ nhiên dự đoán nó sẽ là X̄. Xong rồi ta
> mới nói rằng: vì n(μ, σ²/n) cũng chính là distribution của X̄, nên n(μ, σ²/n)
> cũng là complete family. Mạch logic sẽ là như vậy.
>
>
>
> Cách 1: Dùng kết quả trên thay bởi việc biết σ² / n:
>
>
>
> Tiếp nói từ chỗ (***):
>
>
>
> = Πi=1:n [1/√(2πσ)] exp[-μ²/(2σ²)] Πi=1:n exp[2μ/(2σ²) . xi - 1/(2σ²) . xi^2]
>
>
>
> Vì đã biết σ²/n nên tách ra nốt, đưa lên trước đóng vai trò của h(x)
>
>
>
> = Πi=1:n [1/√(2πσ)] exp[-μ²/(2σ²)] Πi=1:n exp[2μ/(2σ²) . xi] / exp [1/(2σ²) . xi^2]
>
>
>
> = Πi=1:n [1/√(2πσ)] exp[-μ²/(2σ²)] / exp [1/(2σ²) . xi^2] Πi=1:n exp[2μ/(2σ²) . xi] 
>
>
>
> Đặt C(**θ**) = Πi=1:n [1/√(2πσ)] exp[-μ²/(2σ²)]
>
>
>
> H(𝐱) = 1 / {Πi=1:n exp [1/(2σ²) . xi^2]}
>
>
>
> Xét cái phần còn lại: Πi=1:n exp[2μ/(2σ²) . xi] 
>
>
>
> = Πi=1:n exp[ μ/(σ²) . xi] 
>
>
>
> = exp[ Σi=1:n μ/(σ²) . xi] 
>
>
>
> = exp[ μ/(σ²) . Σ xi] 
>
>
>
> = exp(w1(**θ**)t1(𝐱)) với w1(**θ**) = μ/σ² , T1(𝐱) = Σ xi
>
>
>
> ⇨ T(𝐗) = (T1(X)) (chỉ có 1 param) = ΣXi chính là complete statistic của **θ** = (μ)
>
>
>
> ⇨ ΣXi/n (X̄) cũng là complete statistic (theo Gemini nó nói là apply hàm 1-1
> vào complete statistic cũng cho ra complete statistic) 
>
>
>
> Cách 2: Dùng sự thật đã biết là X̄ ~ n(μ, σ²/n), ta sẽ chứng minh nó là complete 
> statistic của **θ** = (μ) (đã biết σ²/n) 
>
>
>
> f(x|μ,σ²) = [1/√(2π(σ²/n))] exp[-(x-μ)^2/(2(σ²/n))]
>
>
>
> Đặt t^2 = σ²/n 
>
>
>
> = [1/√(2πt^2)] exp[-(x-μ)^2/(2(t^2))]
>
>
>
> = [1/√(2πt^2)] exp[-(x-μ)^2/(2t^2)]
>
>
>
> = [1/√(2πt^2)] exp[-(x^2 - 2xμ + μ²)/(2t^2)]
>
>
>
> = [1/√(2πt^2)] exp[- x^2/(2t^2) + 2xμ/(2t^2) - μ²/(2t^2)]
>
>
>
> = [1/√(2πt^2)] exp[- x^2/(2t^2)] exp[2xμ/(2t^2)] / exp[μ²/(2t^2)]
>
>
>
> = [1/√(2πt^2)] [1/ exp[μ²/(2t^2)]] exp[- x^2/(2t^2)] exp[2xμ/(2t^2)] 
>
>
>
> c(**θ**) chính là [1/√(2πt^2)] [1/ exp[μ²/(2t^2)]]
>
>
>
> h(x) chính là exp[- x^2/(2t^2)]
>
>
>
> và ta có c(**θ**) h(x) exp[2xμ/(2t^2)]
>
>
>
> = c(**θ**) h(x) exp[μ . x/(t^2)]
>
>
>
> w1(**θ**) = μ/t^2
>
>
>
> t1(x) = x
>
>
>
> = c(**θ**) h(x) exp[w1(**θ**) . t1(x)]
>
>
>
> ⇨ là dạng expo family. và theo theorem
>
>
>
> T(𝐗) = (t1(X))  = (X) (vector chỉ có 1 phần tử) chính là complete statistic
>
>
>
> Mà đang xét n(μ, σ²/n) là pdf của X̄, tức X ở đây là X̄
>
>
>
> Nên qua đó cho thầy X̄ là complete statistic của distribution param, là μ  
>
>
>
> Nhưng phân tích trên cũng cho thấy X̄ / t^2 cũng là complete statistic 
> nếu coi w1(θ) = μ, t1(x) = x/t^2
>
>
>
> ====
>
>
>
> Rồi, cuối cùng, là dùng ví dụ 6.2.18 đã cho thấy S^2 sample variance là ancillary
> statistic. Nên theo Basu Theorem, X̄ (complete statistic) và S^2 (ancillary)
> độc lập

**🔗 See also:** [Trung bình mẫu thống kê đủ cho μ](#node-nqvdq30)

<br>

<a id="node-bbbhmwa"></a>

<p align="center"><kbd><img src="assets/3h268ahyag.png" width="80%"></kbd></p>

> [!NOTE]
> QUAY LẠI SAU

<br>

