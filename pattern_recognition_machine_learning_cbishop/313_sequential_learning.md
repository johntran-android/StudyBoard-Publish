# 3.1.3 Sequential Learning

📊 **Progress:** `1` Notes | `2` Screenshots | `1` AI Reviews

---
<a id="node-9o3hhga"></a>

<p align="center"><kbd><img src="assets/jdxsi8mjfj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/i7xw0no18y.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại khái là vầy:
>
>
>
> Đầu tiên ông maximum likelihood solution là một dạng của batch technique, mình hiểu đại ý là, nói về kĩ thuật mà ta dùng một gói data (observation) để mà "làm" (ví dụ như với maximum likelihood, cơ bản là ta tìm θ giúp maximile hàm likelihood L(θ|𝐱), và cái hàm này thì được define bởi f(𝐱|θ), tức joint pdf của data tại các observation có được, thì dĩ nhiên ta cần có một batch / gói, các observation)
>
>
>
> Thế thì ông nói tiếp đại ý rằng, có khi việc xử lí một lần toàn bộ cái bộ dataset này sẽ rất tốn kém, hoặc cũng có khi data có được không phải có liền một cục, mà đến từng cái một. Thì khi đó, trong chapter 1 ta đã học một cái gọi là sequential learning, giúp ta có thể thực hiện việc update param từ từ một cách liên tục khi có thêm data mới.
>
>
>
> Mình hiểu cái này tuy rất giống như có điểm phải phân biệt với iterative method trong tối ưu hóa. Nó giống ở chỗ ta cũng update tham số từng bước, nhưng nó khác ở chỗ cái này là **do data ta phải xài từng batch data do phải chia nhỏ để giảm chi phí tính toán hoặc do data đến theo từng batch** còn trong các thuật toán tối ưu, việc update từng bước là do **ta ko biết cách nào, hoặc quá tốn kém để nhảy một phát tới đích (solution) ngay**
>
>
>
> Nói rõ hơn, với bối cảnh tối ưu hóa, thì ta có 1 cục data, và có khả năng xử lí hết một lần, nhưng vì hàm mục tiêu quá phức tạp, ta không thể có một closed form solution (ví dụ như normal equation solution của bài toán least square này) để mà một phát tính ra ngay nghiệm của bài toán, thành ra ta phải dùng các cach tiếp cận iterative, như line search và trust region method để mà dò dẫm từng bước đi tới đích.
>
>
>
> Trái ngược với bối cảnh tối ưu hóa, ở đây, ta có thừa khả năng tính một phát ra nghiệm tối ưu, tức là có closed form solution, nhưng ngặt nỗi data lại đến từ từ từng cái. Mà dù rằng ta có thể làm theo cách sau: Cứ mỗi khi có data thêm, thì ta cập nhật bộ data đó, rồi đi tính closed form solution lại. Tuy nhiên, cách đó cũng không giúp giải quyết được vấn đề là ta tuy có closed form solution nhưng không thể tính một phát một bằng cách xử lí toàn bộ data, ví dụ ram chứa ko hết. Thành ra phải dùng kiểu iterative này.
>
>
>
> ---
>
>
>
> Vậy thì công thức update 3.22 là sao?
>
>
>
> Mình hiểu: công thức này rất đơn giản
>
>
>
> Ví dụ như data thứ n vừa đến", đồng nghĩa ta có data set (𝐱1,...𝐱n), (t1,...tn). Đặt ra bài toán:
>
>
>
> minimize over 𝐰 f(𝐰) = error En(𝐰) = (1/2) (tn - 𝐰ᵀΦ(𝐱n)\]²
>
> \
> Có nghĩa là hàm objective chỉ là bình phương difference giữa tn và 𝐰ᵀΦ(𝐱n).
>
>
>
> Và cơ bản là ta đang dùng một dạng steepest descent algorithm đơn giản: đứng tại vị trí hiện tại 𝐰\_τ (tức giá trị 𝐰 hiện có), ta sẽ đi theo hướng dốc nhất (steepest descent direction) = - ∇f(𝐰\_τ), và đi theo hướng này với **step size η**, để đến được điểm tiếp theo:
>
>
>
> 𝐰\_(τ+1) = 𝐰\_τ + η \[- ∇f(𝐰\_τ)\]
>
>
>
> ⇔ 𝐰\_(τ+1) = 𝐰\_τ - η ∇f(𝐰\_τ)
>
>
>
> Vì sao - ∇f(𝐰\_τ) là hướng dốc nhất thì nhờ học Boyd hay Nocedal thì đã biết rồi.
>
>
>
> Thế thì ∇f(𝐰\_τ) là gradient của objective function evaluate tại 𝐰\_τ, với objective function = En = (1/2) \[tn - 𝐰ᵀΦ(𝐱n)\]² thì:
>
>
>
> ∇En = (1/2) d/d𝐰 \[tn - 𝐰ᵀΦ(𝐱n)\]²
>
>
>
> = (1/2) d/d\[tn - 𝐰ᵀΦ(𝐱n)\] \[tn - 𝐰ᵀΦ(𝐱n)\]² . d/d𝐰 \[tn - 𝐰ᵀΦ(𝐱n)\] (chain rule)
>
>
>
> = \[tn - 𝐰ᵀΦ(𝐱n)\] . d/d𝐰 \[- 𝐰ᵀΦ(𝐱n)\]
>
>
>
> = \[tn - 𝐰ᵀΦ(𝐱n)\] . \[-Φ(𝐱n)\]
>
>
>
> = - \[tn - 𝐰ᵀΦ(𝐱n)\] Φ(𝐱n)
>
>
>
> Ráp vào công thức:
>
>
>
> 𝐰\_(τ+1) = 𝐰\_τ - η ∇f(𝐰\_τ)
>
>
>
> ⇔ 𝐰\_(τ+1) = 𝐰\_τ - η \[- \[tn - 𝐰ᵀΦ(𝐱n)\] Φ(𝐱n)\] |𝐰=𝐰\_τ
>
>
>
> ⇔ 𝐰\_(τ+1) = 𝐰\_τ + η\[tn - 𝐰\_τTΦ(𝐱n)\] Φ(𝐱n)\]
>
>
>
> đây chính là 3.23
>
>
>
> Và thuật toán này gọi là least-mean-squares, hay LMS.
>
>
>
> Mình nhờ học Nocedal nên biết cái này chỉ là steepest gradient descent, và do đó cũng hiểu việc chọn η rất quan trọng. Lí do là vì, đi theo hướng steepest chỉ đảm bảo ta sẽ đi xuống nếu như có thể kiểm soát bước nhảy trong phạm vi nào đó, vì về cơ bản, cái này dựa trên linear approximation.
>
>
>
> Trong Nocedal mình cũng được biết các thuật toán để chọn bước nhảy như exact line search hoặc backtracking line search.
>
>
>
> Nhưng trong machine learning như ở đây vài bữa gs sẽ nói về cái này kĩ hơn.

---

🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on

Phân tích của bạn rất sâu sắc và chính xác, đặc biệt là việc làm rõ sự khác biệt giữa học tuần tự và các phương pháp tối ưu hóa lặp, cùng với việc đạo hàm công thức (3.23) một cách hoàn hảo. Bạn thể hiện khả năng kết nối kiến thức và hiểu biết vững chắc về các khái niệm.

<br>

