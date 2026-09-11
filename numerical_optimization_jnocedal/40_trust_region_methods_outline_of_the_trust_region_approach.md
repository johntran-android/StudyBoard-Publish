# 4.0 Trust-Region Methods: Outline of the Trust-Region Approach

📊 **Progress:** `12` Notes | `11` Screenshots | `8` AI Reviews

---
<a id="node-i345wa4"></a>

> [!NOTE]
> Trust-Region Methods: Outline of the Trust-Region Approach

<br>

<a id="node-4pv6lgc"></a>

## Line search vs Trust Region

<p align="center"><kbd><img src="assets/iukui61j4gd.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên tác giả cho biết line search methods và trust region method đều có điểm chung là dựa vào việc ước lượng xấp xỉ hàm objective bởi một hàm bậc hai và từ đó tính toán ra hướng + độ lớn hướng di chuyển.
>
> Nhưng nó khác nhau ở cách làm. Cụ thể là line search sẽ tính ra direction trước, và tìm step size theo hướng đó sau. Còn trust-region method thì tìm toán một bán kính mà trong phạm vi đó có thể xem như hàm số hoạt động như hàm bậc hai, để từ đó tìm bước đi giúp minimize hàm bậc hai, và dùng nó để thực hiện bước nhảy. Nếu step tính ra không đạt nó sẽ thu hẹp lại trusted region và làm lại.
>
> Nhớ lại một chút về line search, mình đã biết có nhiều cách làm trong bước chọn direction có thể dùng các steepest gradient descent, hoặc Newton direction. Sở dĩ nói đây cũng là dựa trên việc xấp xỉ hàm số bởi hàm bậc hai là vì: Với Newton method thì rõ rồi, vì việc tính toán ra Newton step chính là dựa vào việc xấp xỉ hàm số bởi hàm bậc hai. Còn steepest gradient descent? 
>
> Đại khái là thế này: Quadratic approx của hàm f tại xk:
>
> f(xk + p) ≈ f(xk) + ∇f(xk)Tp + (1/2)pT∇^2f(xk)p
>
> Đặt vế phải là hàm mk(p) 
>
> Vậy thì đại khái là nếu trong phạm vi p hợp lý thì có thể xấp xỉ hàm f bởi hàm bậc hai.
>
> Và dựa vào đó ta xác định p là vector khiến minimize hàm bậc hai này.
>
> Viết lại mk(p) = fk + ∇fkTp + (1/2)pTHkp
>
> ∇mk(p) = Hkp + ∇fk
>
> First order condition: ∇mk(p) = 0 ⇔ Hkp + ∇fk = 0 ⇔ p = - ∇fk(Hk)inv. Đây chính là Newton step
>
> Nếu dùng Bk thay Hk, tức là một matrix xấp xỉ Hessian, thì ta sẽ có p = - ∇fk(Bk)inv, là quasi-newton step
>
> Còn nếu dùng (1/α) I thay cho Hk, tức là một hằng số nhân với Identity. Ta sẽ có:
>
> p = -∇fk (1/α I)inv  = -∇fk α = -α∇fk Thì đây chính là steepest gradient descent.
>
> Do đó thật ra đều là xấp xỉ hàm objective bởi quadratic, chẳng qua là khác nhau cách chọn dùng matrix Hessian. Nếu chọn cách tính chính xác Hessian, thì ta có Newton step, với việc có được thông tin về curvature dẫn đường thì dĩ nhiên là rất tốt. Còn nếu thay bởi xấp xỉ của Hessian cho giảm nhẹ tính toán thì ta có quasi Newton method, vẫn nhanh tuy không bằng Newton method xịn. Cuối cùng là coi như không dùng thông tin curvature thì ta có steepest gradient descent.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Bài phân tích rất chính xác các điểm chung và riêng giữa line search và trust-region methods như mô tả trong văn bản. Ngoài ra, bạn đã thể hiện sự hiểu biết sâu sắc về nền tảng toán học của việc xấp xỉ hàm bậc hai trong các phương pháp tối ưu, điều này vượt xa nội dung được cung cấp và là một điểm cộng lớn.

<br>

<a id="node-d70bo7e"></a>

### Điều chỉnh phạm vi tin cậy

<p align="center"><kbd><img src="assets/pxfynfhc1.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì vì ý tưởng của trust region là vậy - tìm một phạm vi mà trong đó hàm số có thể coi như giống một hàm bậc hai, để từ đó tìm ra bước đi. Do đó dĩ nhiên là bước này rất quan trọng.
>
> Nếu phạm vi này quá lớn, thì trong phạm vi đó hàm số không hoạt động đúng với hàm bậc hai, nên hướng đi sẽ trật, thể hiện bởi bước hậu kiểm sẽ fail, và phải thu nhỏ trust region lại để làm lại.
>
> Nếu phạm vi này quá nhỏ, thì lãng phí, vì giống như ta sẽ quá cẩn trọng, trong khi đáng lẽ có thể thực hiện những bước đi dài hơn giúp hội tụ nhanh hơn.
>
> Ta sẽ tính toán trust region dựa vào kết quả của bước iteration trước đó. Kiểu như là nếu trước đó cho thấy là tốt: cụ thể là bước hậu kiểm cho thấy chọn trust region là ok, giúp trong phạm vi đó hàm số hành xử giống hàm bậc hai, thì trong lần iterate kế tiếp có thể tăng trust region lên. Ngược lại thì thu hẹp lại.
>
> Vậy mới thấy rõ là trust region sẽ cơ bản là tìm step size trước (khi nào tìm được rồi, chính là , rồi mới chọn hướng đi.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ⚠️ **88/100** · ✓ Move on
>
> Bài phân tích cho thấy sự hiểu biết sâu sắc về vai trò và cách điều chỉnh kích thước vùng tin cậy, đặc biệt là các trường hợp quá lớn hoặc quá nhỏ, phản ánh tốt nội dung tài liệu. Tuy nhiên, việc bổ sung thông tin về thứ tự tìm kiếm bước đi không có trong văn bản gốc, cần tập trung hơn vào việc phân tích trực tiếp từ nguồn đã cho.

<br>

<a id="node-8bgm8ab"></a>

#### Vấn đề hướng Line Search

<p align="center"><kbd><img src="assets/siufrrkkra.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này đại ý tác giả muốn minh họa một hoàn cảnh mà có thể thấy Line search direction tệ hơn trust region direction.
>
> Cái contour plot của hàm objective là những đường méo mó, với điểm màu đỏ là x*. Và chấm đen đầu hai mũi tên là xk.
>
> Thế thì nếu là dùng line search method, như đã biết, ta sẽ coi như hàm f tại xk hành xử như hàm bậc hai. Để rồi đi theo Newton step sẽ dẫn ta xuống đáy cái parabol (các contour hình ellips gạch gạch) thì có thể thấy nó khiến hàm f tăng lên (điểm đen tâm của ellipse nằm ngoài đường đồng đẳng của của hàm f so với xk) Mà đó là ta dùng Newton step, tức là có dùng thông tin curvature cung cấp bởi Hessian tại xk rồi mà còn vậy, thì nếu dùng steepest gradient descent hay quasi Newton thì có thể còn tệ hơn.
>
> Trong khi đó, trust region, bằng cách tìm được một bán kính trust region mà trong đó hàm f xấp xỉ tốt bởi hàm bậc hai, nên bước đi của nó (mũi tên ở dưới, giúp hướng về optimizer x* tốt hơn so với line search).
>
> Mình có nhận xét thế này: Tới đây có thể thấy, khi ta xấp xỉ hàm số bởi hàm bậc hai, nhưng dĩ nhiên là phải có một phạm vi nào đó mà sự xấp xỉ này là tốt, bởi bản chất hàm f không phải lúc nào cũng là hàm bậc hai, và định lý Taylor đã cho ta biết khi nào thì được phép dùng dấu xấp xỉ để thay dấu bằng. Vậy thì rõ ràng phương pháp line search sau khi tính ra direction thì phải hết sức cẩn trọng trong việc chọn step size. Nhưng kể cả như vậy thì vấn đề là, cái direction nó có thể đã tệ ngay từ đầu rồi, nên chọn step size chỉ là vớt vát lại ít nhiều thôi.
>
> Trong khi đó, ưu tiên của trust region là chọn vùng an toàn, nơi mà có thể xấp xỉ tốt hàm bởi hàm bậc hai, từ đó mới tính direction, do đó direction của nó tốt hơn.

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ⚠️ **70/100** · ✓ Move on
>
> Phân tích về nguyên lý của phương pháp trust region và ưu điểm của nó so với line search rất sâu sắc và chính xác, thể hiện sự hiểu biết tốt về khái niệm cốt lõi. Tuy nhiên, nhận định về việc hàm f tăng lên khi sử dụng line search là sai lệch so với thông tin được cung cấp ('at most a small reduction'), và bài viết bị đứt đoạn ở cuối.

<br>

<a id="node-cgxjlmd"></a>

##### Ảnh hưởng bán kính vùng tin cậy

<p align="center"><kbd><img src="assets/5g58fzdwqhr.png" width="80%"></kbd></p>

> [!NOTE]
> Hiểu thế này, trust region khi đã tìm ra được vùng tin cậy, thì ta tìm trong những điểm trên hoặc trong tròn đó, điểm nào có hàm mk(p) nhỏ nhất.
>
> Nếu bán kính là lớn thì hướng này sẽ trùng với Newton step.
>
> Nếu bán kính nhỏ thì nó sẽ trùng với steepest gradient.
>
> (Những phần sau sẽ nói rõ)

<br>

<a id="node-9ozcgzk"></a>

###### #4.1, 4.2, 4.3

<p align="center"><kbd><img src="assets/hw6x333oen5.png" width="80%"></kbd></p>

> [!NOTE]
> Cùng đọc đoạn này. Tác giả nói trong phần này ta sẽ assume rằng tại mỗi iteration ta đều approx hàm f bởi quadratic function.
>
> Và cái này thì như đã biết từ các chương trước, xuất phát từ Taylor theorem:
>
> Nói rằng khi đi từ xk → xk + p, ta có:
>
> f(xk + p) = f(xk) + ∇f(xk)Tp + (1/2)pT ∇^2f(xk + tp)p for some t in (0,1) (4.1)
>
> Rồi, từ cái này mình sẽ lập luận rằng, nếu t nhỏ trong phạm vi nào đó thì Hessian tại xk + tp có thể coi như bằng Hessian tại xk. Từ đó ta có quadratic approximation:
>
> f(xk + p) ≈ f(xk) + ∇f(xk)Tp + (1/2)pT ∇^2f(xk)p
>
> Còn trong sách, tác giả nói nếu ta thay Hessian tại xk + tp bởi ma trận xấp xỉ Bk symmetric nào đó (mà nếu Bk là Hessian tại k thì ta có kết quả trên) thì ta sẽ có:
>
> f(xk + p) ≈ f(xk) + ∇f(xk)Tp + (1/2)pT Bk p 
>
> Và vế phải là hàm sẽ dùng để approx hàm f
>
> mk(p) =  f(xk) + ∇f(xk)Tp + (1/2)pT Bk p (4.2)
>
> Vậy thì sai khác giữa mk(p) và f(xk+p) sẽ là O(||p||^2) là vì sao?
>
> ⇨ Là vì f(xk + p) - mk(p) sẽ là (1/2)pT (Bk - H(xk+pt)) p. Và đây là O(||p||^2)
> vì nó có dạng Σ αi pi^2
>
> Thì là vì f(xk + p) - mk(p) = (1/2)pT(Bk - ∇^2f(xk+tp)) p
>
> Rồi tại sao khi Bk chính xác là Hessian thì ta sẽ có sai khác O(||p^3||)???
>
> (Quay lại sau)
>
> ====
>
> Tiếp, tác gỉa nói để đảm bảo tính khái quát của trust region method thì ta sẽ chỉ giả định rất ít về Bk, ngoại trừ việc nó đối xứng và "uniform boundedness"???
>
> Rồi, thế thì tại mỗi step, ta sẽ giải bài toán tối ưu:
>
> minimize mk(p) subject to ||p|| ≤ Δk (4.3)
>
> Và vì ||.|| ở đây là L2 norm, nên về cơ bản là ta giải bài toán minimize quadratic function với constraint cũng quadratic vì ||p|| ≤ Δk thì tương đương pTp ≤ Δk^2)
>
> Rồi nếu Bk xác định dương và ||Bkinv gk|| ≤ Δk thì ta có solution là pk_B = - (Bk)inv gk Và trong trường hợp này pk_B gọi là full step.
>
> ?? Vì sao?  Dễ thôi, vì minimizer của mk(p) dễ thấy sẽ là -(Bk)inv gk (y như công thức quasi Newton step đó). Và nếu như  ||(Bk)inv gk|| ≤ Δk (feasible) thì dĩ nhiên chính là thỏa constraint ⇨ là solution của bài toán. 
>
> Và vì nó là solution, nên dùng nó để đi ngay từ xk đến đấy luôn, tức là vector dài nhiêu thì đi theo đó bấy nhiêu nên gọi là full step. 
>
> Còn vì sao phải xác định dương thì là bởi đây là điều kiện đủ bậc hai mình đã biết ở chương 2 
>
> Còn trong trường hợp khác (ko thỏa Bk xác định dương và ||Bkinv gk|| ≤ Δk) thì ta sẽ tìm cách giải bằng các ước lượng.
>
> #4.1, 4.2, 4.3

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ⚠️ **88/100** · ✓ Move on
>
> Phân tích của bạn rất sâu sắc và chi tiết, đặc biệt là phần giải thích về 'full step' và điều kiện xác định dương của Bk, cho thấy sự hiểu biết vững chắc về lý thuyết. Tuy nhiên, khi tính sai khác f(xk + p) - mk(p), hãy cẩn trọng hơn về dấu của các thành phần trong biểu thức; và lần tới cần hoàn thiện các phần "Quay lại sau" để đạt điểm tối đa.

**🔗 See also:** [4.3 Iterative Solution Of The Subproblem](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-gal0ace)

<br>

<a id="node-464kbau"></a>

###### Outline of the trust-region method

<p align="center"><kbd><img src="assets/h292a77ve1h.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là phần này sẽ nói về cách tiếp cận đối với trust-region, vì bước xác định trust region là bước quan trọng đầu tiên cần làm.
>
> Ôn lại một chút về **phương pháp trust region**: So sánh với line search method, thì cả hai có **điểm chung** là (tại một bước update / một iteration để đang đứng ở xk, thực hiện bước đi đếm xk+1) thì về bản chất **đều là xem / coi như hàm objective là hàm bậc hai**, hay nói cách khác, ta dùng một hàm bậc hai để approximate hàm objective. 
>
> Để rồi dựa vào đó, **line search sẽ xác định direction, và step size**. Còn **trust region thì làm ngược thứ tự lại, xác định step size trước** (chính xác hơn thì xác định phạm vi của step size trước, tức trust region), sau đó, mới giải bài toán tối ưu - minimize hàm quadratic với constraint là trong phạm vi trust region để **tìm direction**.
>
> Thế thì, nếu đánh giá về line search, ta sẽ thấy rằng, vấn đề của nó là, nó **dựa vào việc estimate hàm objective bởi quadratic (mk(p) = fk + gkTp + (1/2)pTAp**, để rồi với việc dùng **A = I hay Hessian tại k hay matrix xấp xỉ Hessian tại k, Bk, mà ta có steepest gradient descent, quasi-newton hay Newton method)**, để từ đó giải bài toán minimize hàm mk(p) để xác định direction
>
> Thì điểm không ổn là theo Taylor theorem nói rằng, **trừ khi hàm f là hàm quadratic, còn không thì việc xấp xỉ này chỉ đúng trong một phạm vi nhỏ mà thôi**. Do đó, ngay cả khi dùng Newton method, thì nó chỉ tỏ ra hiệu quả khi xk đã tới gần x*, khiến cho việc ước lượng tại đó, và giải tìm minimizer của hàm mk nó diễn ra trong một phạm vi nhỏ, dẫn đến bảo đảm việc xấp xỉ là chấp nhận được, nên phương pháp phát huy hiệu quả, và dẫn đến tốc độ hội tụ bậc hai.
>
> Ngược lại, **khi xk còn xa x*, thì solution của bài toán minimizing mk method sẽ tạo ra direction có thể rất tệ**, vì nó vi phạm điều kiện của xấp xỉ bậc hai nói trên, rằng chỉ có thể xấp xỉ tốt trong phạm vi nào đó mà thôi.
>
> Ý muốn chỉ ra rằng, **nhược điểm của line search**, hiểu nôm na là **quá tự tin trong việc xác định direction**, và dù rằng bước tìm kiếm step length theo sau có thể cũng đảm bảo cho việc update có tiến triển nào đó, nhưng direction có thể đã tệ thì bước tìm step length cũng không gỡ gạc lại được.
>
> Từ đó ta mới nghĩ về trust region method, nó muốn **khắc phục bằng cách quyết định một trust region trước**, và cơ chế của nó nhằm mục đích, **nếu lần iterate trước có vẻ không ổn, thì sẽ thu hẹp trust region lại, và ngược lại thì sẽ mở rộng ra thêm**. 
>
> **Điều này giống như một người đi đường cẩn trọng, khi họ quyết định sẽ bước ngắn hơn nếu lần trước cảm thấy bị hụt chân v(vì nó cho thấy họ đang đoán sai về địa hình phía trước). Nhưng sẽ bước dài hơn nếu họ không thấy bị hụt chân hay chông chênh, chứng tỏ họ đang đoán đúng địa hình.**
>
> Tất nhiên, trust region **cũng xác định hướng đi bằng cách minimize hàm mk, nhưng ràng buộc bởi bán kính, khiến nó (pk) nó sẽ khác với hướng pk giải ra bởi bài toán minimize mk không ràng buộc.**
>
> Và đoạn này nói về việc **check tỉ số ρk chính là xem thử độ hụt**, hay cảm giác bị hụt chân / hay khựng (tưởng tượng bạn bước xuống cầu thang, khi bạn đoán nó thấp hơn thực tế bạng sẽ bị khựng, ngược lại, bạn sẽ bị cảm giác hụt chân) chính là **tỉ lệ giữa độ giảm của hàm f (từ xk → xk + pk) và độ giảm của hàm mk (mk tại 0. tức xk và tại pk, tức xk + pk).**
>
> **Nếu tỉ lệ này gần bằng 1**: Đây chính là **cảm giác chắc chắn**. cho thấy dự đoán đúng thực tế, ta tự tin sải bước dài hơn (tăng Δk, tức lần sau cho Δk+1 lớn hơn)
>
> Ngược lại, **nếu nó gần 0 hoặc âm**, có nghĩa là rất tệ, mà ở đây nói, nếu nó âm thì có nghĩa là hàm mục tiêu thậm chí còn đang đi lên → không thể chấp nhận được.  Khi đó ta sẽ giảm Δk.
>
> Còn **nếu nó vẫn dương nhưng không gần 1, thì cứ giữ Δ** vì cũng ko quá tốt cũng không quá tệ.
>
> Tóm lại, nếu **ví von hai phương pháp như cách ngừơi mù đi xuống thung lũng**. Thì, với line search: Ổng **sờ định hình dưới chân để đoán hướng đi**, rồi **dò dẫm để chọn sải bước**. 
>
> Còn với trust region, thì **ổng dựa vào cảm giác hụt chân hay bị khựng ở bước trước đó để quyết định sải bước**, sau đó **tìm hướng đi giúp xuống thấp nhất trong phạm vi sải bước đó**.
>
> #Công thức 4.4 ρk = f(xk) - f(xk + pk)] / [mk(0) - mk(pk)]

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Bản phân tích của bạn cực kỳ kỹ lưỡng và sâu sắc, vượt xa việc tóm tắt nội dung trực tiếp từ văn bản, thể hiện sự hiểu biết vững chắc về các phương pháp tối ưu. Tuy nhiên, bạn có thể đề cập rõ hơn đến tính chất luôn không âm của predicted reduction để đảm bảo độ chính xác tuyệt đối.

**🔗 See also:** [Chứng minh theorem 4.5](./42_trust_region_methods_global_convergence.md#node-oli585n)

<br>

<a id="node-c4gu30d"></a>

###### Algorithm 4.1 (Trust Region)

<p align="center"><kbd><img src="assets/f8e57f8ux2.png" width="80%"></kbd></p>

> [!NOTE]
> Algorithm 4.1 (Trust Region)
>
> Iteratively lặp lại các bước k'th
>
> Tính pk là solution của bài toán minimizing over pk {mk(pk) = f(xk) + gkTpk + (1/2)pkBkpk s.t ||pk|| ≤ Δ
>
> Tính ρk = [f(xk) - f(xk + pk)] / [mk(0) - mk(pk)]
>
> Nếu ρk < 1/4 thì có nghĩa là hụt chân, vì mức giảm quá lớn so với thực tế → giảm trust region lại
>
> Nếu ρk > 3/4 và ||pk|| = Δ → chắc chân → tăng trust region
>
> còn ca ở giữa thì cứ giữ nguyên.
>
> Cuối cùng, nếu pk thỏa điều kiện > η (là giá trị chọn trước ∈ [0, 1/4]) thì mới thực hiện bước update xk+1 = xk + pk còn ngược lại thì giữ nguyên xk+1 = xk
>
> Chỉ có để ý là, nó chỉ tăng trust region lên nếu như ở bước trước đó, ||pk|| = Δk, có nghĩa nôm na là việc tìm kiếm ra điểm thấp nhất trong phạm vi cho phép cho ra điểm ngay trên biên. Điều này cùng với việc tỉ số ϱk "đạt" thì ta mới mở rộng trust region.

**🔗 See also:** [Hội tụ toàn cục điểm Cauchy](./42_trust_region_methods_global_convergence.md#node-edr7lqw) · [Convergence to Stationary Points](./42_trust_region_methods_global_convergence.md#node-k0era47) · [Thuật toán SR1 Vùng tin cậy](./62_the_sr1_method.md#node-fsif7wv) · [Phương pháp Trust-Region Newton CG](./71_inexact_newton_methods.md#node-8tkd9oh) · [Triển khai Levenberg-Marquardt](./103_algorithms_for_nonlinear_least_squares_problem.md#node-gb1ww4r)

<br>

<a id="node-4oyhvi4"></a>

###### Bài toán (4.5) sẽ là minimize mk(p) = fk + gkTp + (1/2)pTBkp subject to ||pk|| ≤ Δk

<p align="center"><kbd><img src="assets/3grwxoweoot.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì trong thuật toán vừa rồi, thì bước đầu tiên là giải bài toán tìm pk, (sau khi đã có trust region radius Δk
>
>
>
> Như đã biết, tại iteration k, đứng ở xk, ta tìm cách đến xk+1.
>
>
>
> Thì bài toán (4.5) sẽ là minimize mk(p) = fk + gkTp + (1/2)pTBkp subject to ||pk|| ≤ Δk
>
>
>
> (gk là gradient tại k, ∇f(xk), Bk thì có khi là I, có thể là xấp xỉ của Hessian ∇^f(xk) hoặc có thể là ∇^f(xk))
>
>
>
> Cho gọn thì ta tạm bỏ đi subscript:
>
>
>
> minimize f + gTp + (1/2)pTBp subject to ||p|| ≤ Δ 
>
>
>
> Thì đại ý là, để giải bài toán này, ta sẽ dùng một theorem mà ta sẽ chứng minh sau, theorem này nói rằng: nếu p\* là solution của bài toán 4.5 thì nó sẽ thõa:
>
>
>
> (B + λI)p\* = -g (4.6)
>
>
>
> #4.5, 4.6

**🔗 See also:** [4.3 Iterative Solution Of The Subproblem](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-gal0ace) · [Proof of theorem 4.1: Lemma 4.7](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-k08q2ml) · [Convergence of algorithms based on nearly exact solution](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-tr8868m)

<br>

<a id="node-6p1mgzb"></a>

###### Theorem 4.1

<p align="center"><kbd><img src="assets/pi2ghxbi63c.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ofzcvtgq4i.png" width="80%"></kbd></p>

> [!NOTE]
> Theorem 4.1
>
> Rồi, theorem vừa nhắc đến, nó rằng p* là global solution của bài toán minimize m(p) = f + gTp + (1/2)pTBp s.t ||p|| ≤ Δ KHI VÀ CHỈ KHI p* feasible và tồn tại λ ≥ 0 thỏa:
>
> (B + λI)p* = -g (4.8a)
>
> λ(Δ - ||p*||) = 0 (4.8b)
>
> (B + λI) xác định bán dương. (4.8c)
>
> Như đã nói, tác giả sẽ chưa chứng minh theorem này. Mà ta sẽ phân tích vài hệ quả trước. (sau đó, trước khi đọc tiếp, mình sẽ ôn lại KKT condition học ở Convex Optimization S.Boyd để chỉ ra thực ra mấy cái trên chính là KKT conditions)
>
> Vài nhận định cũng dễ hiểu thôi:  
>
> Thứ nhất: 
>
> vì thỏa 4.8b, λ(Δ - ||p*||) = 0 nên nếu Δ - ||p*|| > 0 thì λ phải = 0, và nếu λ > 0 thì (Δ - ||p*||) phải = 0 (cái này rõ ràng chính là complementary slackness)
>
> Thì ý nghĩa của nó, là, khi solution p* nằm TRONG trust region, tức ||p*|| < Δ ⇔ Δ - ||p*|| > 0 thì λ phải = 0, dẫn đến cùng với 4.8a và c ta phải có:
>
> Bp* = - g và B xác định bán dương.
>
> Còn ngược lại nếu minimizer xảy ra tại biên, ||p*|| = Δ thì λ phải dương. Khi đó 4.8a ⇔ Bp* + λp* = -g ⇔ λp* = - Bp* - g ⇔ λp* = - (Bp* + g)
>
> và đây chính là gradient của mk tại p* (không có gì khó hiểu sau khi đã học MIT 18s096)
>
> Vậy λp* = - ∇m(p*)
>
> Và phương trình này cho thấy p* CÙNG PHƯƠNG với nagative gradient, và mình thì đã biết gradient sẽ vuông góc với contour plot, nên ta kết luận p* sẽ vuông góc với contour plot.
>
> Có chỗ dễ gây lú: 
>
> Ta đứng tại xk, và giải bài toán minimize mk(p) = fk + gkTp + (1/2)pTBkp s.t ||p|| ≤ Δ, để có mk(p*) là điểm thấp nhất trong phạm vi cho phép.
>
> Thì thật ra bản chất ý nghĩa của việc xấp xỉ f(xk + p) ≈ f(xk) + gkTp + (1/2)pT Hk p nói rằng khi đi từ xk → ra khỏi xk thì trong phạm vi nào đó thì ta có thể xem nó hành xử như hàm quadratic.
>
> và nếu mình tìm ra p* là cái giảm thiểu cái này, thì cũng chính là p* dẫn ta từ xk đi đến xk + p* là điểm thấp nhất
>
> Nếu có thêm constraint thì có nghĩa là p* là hướng di chuyển (và sải bước) giúp ta đi từ xk đến xk + p* thấp nhất có thể trong phạm vi hình tròn (xk, Δk).
>
> Nên p* là hướng, là vector, vậy thì  ∇mk(p*) có nghĩa là sao? Đây là chỗ có thể gây bối rối.
>
> Câu trả lời đơn gỉan là: Thì nó có nghĩa là gradient của hàm mk tại p* chứ sao. Nhưng ở trên hình thì nó chính là xk + p*.
>
> Nói rõ hơn: mình phải nhận thức rõ, hàm mk(p), vì là hàm của p, mà bản chất là gì, là x - xk, vì mk(p) vốn xuất thân từ xấp xỉ bậc 2, cũng là Taylor expansion của f xung quanh xk:
>
> f(x) ≈ f(xk) + ∇f(xk)T(x-xk) + (1/2)(x-xk)T ∇^2f(xk) (x-xk) 
>
> Rồi ta mới lấy vế phải, đặt p = x - xk, và đăt hàm mk(p) = f(xk) + ∇f(xk)Tp + (1/2)p ∇^2f(xk) p
>
> Thì theo đó, sự tương ứng sẽ là: **Trong hệ quy chiếu x, ta đi từ xk → xk + p*, thì tương ứng với trong hệ quy chiếu p, thì ta đi từ p = 0, đến p = p***
>
> Nên nói về gradient của mk(.) tại p*, thì nó sẽ tương ứng với điểm xk + p* trong hệ quy chiếu x.
>
> Nói chung hiểu rõ như vậy thì ta sẽ không còn thắc mắc kiểu như ủa p* là hướng, ko phải là điểm (như xk, hay xk + p*) mà lại có ∇mk(p). Mà có thể hiểu p*, chính là tương ứng với xk + p* trong hệ trục tuyệt đối.
>
> Nên nếu ∇f(x)|x=xk + p* là vector gradient của hàm f thì ∇mk(p*) là vector gradient của hàm mk.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú của bạn rất chính xác và thể hiện sự nắm vững xuất sắc các điều kiện của bài toán con vùng tin cậy, bao gồm cả hiểu biết sâu sắc về các phép biến đổi tọa độ cơ bản và sắc thái của việc diễn giải gradient.
> ### Phân tích chi tiết
>
> #### Điểm mạnh
>
> *   **Tái hiện chính xác Định lý 4.1:** Bạn đã tái hiện hoàn toàn chính xác Định lý 4.1 cùng với các điều kiện (4.8a), (4.8b), (4.8c) như trong tài liệu tham khảo.
> *   **Diễn giải điều kiện bù trừ (Complementary Slackness) rõ ràng:** Bạn đã giải thích rất rõ ràng và chính xác điều kiện `λ(Δ - ||p*||) = 0` (4.8b) là điều kiện bù trừ, phân tích cụ thể hai trường hợp khi giải pháp nằm bên trong vùng tin cậy (`||p*|| < Δ`) hoặc trên biên (`||p*|| = Δ`).
> *   **Phân tích trường hợp xuất sắc:**
>     *   **Khi `||p*|| < Δ`:** Bạn đã suy luận chính xác rằng `λ = 0`, từ đó dẫn đến `Bp* = -g` và `B` là ma trận xác định bán dương, phù hợp hoàn toàn với văn bản gốc.
>     *   **Khi `||p*|| = Δ`:** Bạn đã chứng minh đúng `λ > 0` và suy ra `λp* = -Bp* - g`. Việc nhận diện biểu thức này chính là `-∇m(p*)` là hoàn toàn chính xác.
> *   **Hiểu biết về mối quan hệ giữa `p*` và gradient:** Bạn đã kết luận đúng rằng `p*` cùng phương với negative gradient và vuông góc với các đường contour, thể hiện sự hiểu biết vững chắc về tính chất hình học của gradient.
> *   **Phần giải thích 'chỗ dễ gây lú' nổi bật:** Đây là điểm mạnh đặc biệt xuất sắc. Việc bạn nhận ra và giải thích cặn kẽ sự khác biệt giữa `p*` là một vector hướng và `∇m(p*)` là gradient tại một điểm `p*` trong không gian `p`, cũng như mối liên hệ với `x_k + p*` trong không gian `x`, cho thấy một mức độ hiểu biết rất sâu sắc và khả năng suy nghĩ phản biện. Sự phân tích về việc chuyển đổi hệ quy chiếu từ `x` sang `p` thông qua `p = x - x_k` là hoàn hảo.
> *   **Tích hợp kiến thức ngoài chính xác:** Việc bạn nhận ra rằng các điều kiện (4.8a)-(4.8c) chính là các điều kiện KKT (Karush-Kuhn-Tucker) từ 'Convex Optimization' của S. Boyd, và việc đề cập đến khóa học MIT 18s096, cho thấy bạn có kiến thức nền tảng rộng và khả năng kết nối các khái niệm từ nhiều nguồn khác nhau một cách hiệu quả.
> *   **Sự tinh tế trong diễn giải gradient:** Lời nhận xét ở cuối rằng `∇f(x)|x=xk + p*` và `∇mk(p*)` 'dĩ nhiên chúng ko bằng nhau' nhưng là sự tương ứng, là một quan sát rất sắc sảo. `∇m(p*)` là gradient của mô hình bậc hai, vốn là một xấp xỉ của `∇f(x_k + p*)`. Điều này chứng tỏ bạn không chỉ hiểu các công thức mà còn hiểu rõ bản chất xấp xỉ của mô hình.
>
> #### Các lĩnh vực cần cải thiện
>
> *   **Hoàn thiện câu cuối cùng:** Câu cuối cùng của bạn "dĩ nhiên chúng ko bằng nhau, ý là đang nói đó là sự" bị ngắt quãng. Mặc dù ý bạn rất rõ ràng và chính xác, việc hoàn thiện câu này sẽ tăng cường sự rõ ràng và tính chuyên nghiệp của ghi chú.
>
> #### Gợi ý để đào sâu hiểu biết
>
> *   **Hoàn thành ý tưởng về sự không bằng nhau của gradient:** Bạn có thể mở rộng ý cuối cùng bằng cách giải thích rằng `∇m(p*)` là gradient của mô hình bậc hai, trong khi `∇f(x_k + p*)` là gradient thực sự của hàm `f` tại điểm đó. `∇m(p*)` chính là thành phần tuyến tính của chuỗi Taylor của `∇f(x_k + p*)` xung quanh `x_k` (tức là `g_k + B_k p*`), do đó chúng chỉ bằng nhau nếu các số hạng bậc cao hơn trong chuỗi Taylor của `∇f` là bằng không hoặc `p*` đủ nhỏ.
> *   **Thêm nhận xét về tính lồi:** Bạn có thể thêm một ghi chú ngắn gọn về cách điều kiện `(B + λI)` là xác định bán dương đảm bảo tính lồi của mô hình bậc hai, điều này rất quan trọng để đảm bảo rằng `p*` thực sự là một điểm cực tiểu toàn cục của bài toán con vùng tin cậy.
>
> #### Điểm thưởng
>
> *   Nhận diện các điều kiện (4.8a)-(4.8c) là điều kiện KKT (Karush-Kuhn-Tucker) từ môn Tối ưu lồi (Convex Optimization).
> *   Tham khảo khóa học MIT 18s096 khi diễn giải gradient.
> *   Khả năng phân tích sâu sắc về sự khác biệt giữa `∇m(p*)` và `∇f(x_k+p*)` trong ngữ cảnh của phép xấp xỉ Taylor và chuyển đổi hệ tọa độ.
>
>
> **⭐ Bonus points**
> - Nhận diện các điều kiện (4.8a)-(4.8c) là điều kiện KKT từ Convex Optimization (S. Boyd).
> - Tham khảo khóa học MIT 18s096 khi diễn giải gradient.
> - Phân tích sâu sắc mối quan hệ giữa gradient của mô hình bậc hai và gradient thực của hàm mục tiêu sau khi chuyển đổi tọa độ.

**🔗 See also:** [4.3 Iterative Solution Of The Subproblem](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-gal0ace) · [The Hard Case: Khi q1Tg = 0](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-ty435bj) · [Proof of theorem 4.1: Lemma 4.7](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-k08q2ml) · [Proof of theorem 4.1: Chứng minh điều kiện đủ](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-csqy8ix) · [Convergence of algorithms based on nearly exact solution](./43_trust_region_methods_iterative_solution_of_the_subproblem.md#node-tr8868m) · [Lemma 10.2: Trust-Region Solution](./103_algorithms_for_nonlinear_least_squares_problem.md#node-za3zjv6) · [Solving Least-Squares Subproblem](./103_algorithms_for_nonlinear_least_squares_problem.md#node-1z7vmo9)

<br>

<a id="node-do3f7ba"></a>

###### Lập luận lại KKT conditions.

> [!NOTE]
> Lập luận lại cái KKT nhé:
>
>
>
> Đầu tiên, nhớ ý quan trọng này, **đối diện với bài toán inequality + equality constraint opt problem** có dạng:
>
> minimize x {f0(x)} s.t fi(x) ≤ 0, hi(x) = 0, i = 1,2...
>
>
>
> Thì solution của bài toán này sẽ là một điểm x\* feasible (thoả các constraint) và khiến f0(x) nhỏ nhất.
>
>
>
> Thì cái **lí luận của việc xây dựng Lagrangian function** đó là vì\*\* ta muốn "tích hợp" cái constraint vào, để đưa về bài toán unconstraint\*\*. Và ta làm bằng cách, gắn trọng số vào các inequality:
>
>
>
> Generalized Lagrangian function: L(x, λ, v) = f0(x) + Σi λi fi(x) + Σi vihi(x)
>
>
>
> Thế thì tuy tích hợp vào để thành bài toán unconstraint, nhưng **phải làm sao đó để phản ánh được constraint**, đó là ta muốn **fi(x) ≤ 0** và hi(x) = 0.
>
>
>
> Vậy làm sao để khi minimize L theo x thì nó khiến fi(x) âm. Câu trả lời là phải \*\*ràng buộc λi ≥0 \*\*. Vì nếu không, quá trình tối ưu khi muốn minimize L sẽ đẩy fi(x) càng dương càng tốt vì điều này dẫn đến λifi(x) càng âm.→ Và fi(x) dương sẽ khiến vi phạm constraint.
>
>
>
> Do đó ta có một trong KKT conditions: λi ≥ 0, hay viết là λ ≽ 0 (vector λ)
>
>
>
> Thế thì, để minimize L over x, dĩ nhiên sẽ dẫn ta đến gradient của L wrt x = 0, vì đây là điều kiện cần bậc 1. Nên ta mới có ∇L(x\*, λ, v) = ∇f0(x\*) + Σi λi ∇fi(x\*) + Σi vi ∇hi(x\*) = 0. Đó chính là điều kiện KKT tiếp theo.
>
>
>
> Tiếp, khi mà ta đã minimize over x hàm Lagrangian, **thì Lagrangian tại đó, (tức tại x là solution của bài toán minimize over x hàm Lagrangian) sẽ không còn phụ thuộc vào x nữa**, nó là hàm theo λ và v. Đây là định nghĩa của **dual function**: g(λ, v) = inf x L(x, λ, v)
>
>
>
> và ta sẽ có một inequality:
>
>
>
> g(λ, v) ≤ L(x, λ, v) **với mọi x** do định nghĩa của dual function.
>
>
>
> Rồi. Tới đây nhận định thế này, nếu gọi x là solution của primal problem\*, tức là **feasible point + minimize f0(x)** thì ta có:
>
>
>
> g(λ, v) ≤ L(x\*, λ, v) = f0(x\*) + Σi λi fi(x\*) + Σi νi hi(x\*) (1)
>
>
>
> điều này là **đương nhiên, vì inequality này thỏa với mọi x** cơ mà.
>
>
>
> Và vì x\* thỏa constraint (x\* trước hết phải là feasible point), nên:
>
>
>
> λi × fi(x\*) ≤ 0, (a) và
>
>
>
> vi × hi(x\*) = 0. (b)
>
>
>
> Giúp ta có:
>
>
>
> g(λ, v) ≤ L(x\*, λ, v) = f0(x\*) + Σi λi fi(x\*) + Σi νi hi(x\*)
>
>
>
> = f0(x\*) + Σi λi fi(x\*) + 0 (do (b))
>
>
>
> ≤ f0(x\*) (do (a))
>
>
>
> Vậy g(λ, v) ≤ f0(x\*)
>
>
>
> Mang ý nghĩa dual function là lower bound của optimal value p = f0(x)
>
>
>
> Vậy thì câu chuyện tiếp theo sẽ là, nếu đã nhận định g(λ, v) là lower bound của p\*, tức f0(x\*), thì ta \*\*muốn tìm cái lower bound tốt nhất (tức cao nhất). \*\*Bằng cách maximize over λ, v đối với g(λ,v), bài toán này gọi là **dual problem**.
>
>
>
> gọi d\* là sup λ ≽ 0, v {g(λ, v)}. gọi là **dual optimal value**. Thì ta sẽ lại có inequality:
>
>
>
> d\* ≤ p\*
>
>
>
> Điều này chỉ là hệ quả của g(λ, v) ≤ p\* ⇨ max của nó vẫn sẽ ≤ p\*
>
>
>
> Và p\* - d\* gọi là **duality gap**
>
>
>
> Tới đây, **có một theorem nói rằng** nếu như **trong bối cảnh convex problem** và **thỏa một số điều kiện gọi là qualification constraint**, thì ta sẽ có **strong duality**: d\* = p\*, hay zero duality gap (p\* - d\* = 0)
>
> d\* = p\*
>
>
>
> cũng là g(λ\*, v\*) = f0(x\*)
>
>
>
> tức f0(x\*) + Σi λifi(x) + Σi vihi(x) = f0(x\*)
>
>
>
> mà dĩ nhiên là hi(x\*) = 0 vì x\* là primal optimal nên dĩ nhiên feasible nên cái trên chỉ còn **Σi λifi(x) = 0**
>
>
>
> và với fi(x\*) ≤ 0, thì cái này cho thấy nếu fi(x\*) âm thì λi phải bằng 0 và ngược lại nếu λi &gt; 0 thì fi(x\*) phải = 0.
>
>
>
> Và đây chính là một điều kiện KKT nữa, có tên là **complementary slackness**.
>
>
>
> Do đó KKT conditions bao gồm:
>
>
>
> Gradient của Lagrangian đối với x tại x\* = 0 . Đây gọi là **stationary condition**
>
>
>
> **Complementary slackess**: Σi λifi(x) = 0 với mọi i
>
>
>
> λi\* ≥ 0, đây gọi là **dual constraint**, tức constraint của dual problem
>
>
>
> fi(x\*) ≤ 0, hi(x\*) = 0. gọi là **primal constraint**, constraint của primal problem.
>
>
>
> Và một điểm lưu ý quan trọng:
>
>
>
> Nếu như **bài toán lồi và thỏa constraint qualification**, ví dụ điển hình là Slater's condition. **Giải KKT giúp kết luận x là global optimal** (tức là coi như điều kiện cần + đủ)
>
>
>
> Còn theo Gemini mới dạy mình, là v**ới bài toán khác, vẫn có thể dùng KKT condition**, nhưng **chỉ được dùng như điều kiện cần** (chứ chưa đủ)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ⚠️ **80/100** · ✓ Move on
>
> Bài phân tích KKT của bạn thể hiện sự hiểu biết sâu sắc và mạch lạc về hầu hết các khía cạnh lý thuyết. Tuy nhiên, cần chỉnh sửa lại một số lập luận cốt lõi để đạt được sự chính xác tuyệt đối.
> # Đánh giá Chi Tiết Phân Tích KKT
>
> Bạn đã trình bày một phân tích rất chi tiết và có cấu trúc tốt về điều kiện Karush-Kuhn-Tucker (KKT). Mạch lập luận từ việc xây dựng Lagrangian đến các điều kiện cuối cùng được thể hiện rõ ràng. Tuy nhiên, với tư cách là một giáo sư nghiêm khắc, tôi nhận thấy một số điểm cần được cải thiện đáng kể về độ chính xác lý thuyết.
>
> ## Điểm Mạnh
>
> *   **Cấu trúc và Mạch Lập Luận:** Bạn đã trình bày các khái niệm một cách rất có hệ thống, từ định nghĩa hàm Lagrangian, vai trò của nó, đến việc dẫn xuất các điều kiện KKT. Mạch suy luận từ weak duality đến strong duality và complementary slackness rất rõ ràng và dễ theo dõi.
> *   **Hiểu Biết Về Dual Function:** Bạn nắm vững ý nghĩa của hàm đối ngẫu (dual function) như một cận dưới của giá trị tối ưu bài toán gốc (primal optimal value) và vai trò của bài toán đối ngẫu (dual problem) trong việc tìm cận dưới tốt nhất.
> *   **Complementary Slackness:** Giải thích về complementary slackness, đặc biệt là mối quan hệ giữa λi và fi(x*), rất chính xác và sâu sắc.
> *   **Điều Kiện Cần và Đủ:** Việc phân biệt rõ ràng KKT là điều kiện cần cho bài toán tổng quát và trở thành điều kiện cần và đủ cho bài toán lồi (convex problem) khi thỏa mãn Constraint Qualification (ví dụ Slater's condition) là một điểm cộng lớn, cho thấy sự hiểu biết vững chắc về phạm vi ứng dụng.
> *   **Đề Cập Constraint Qualification:** Việc bạn đề cập đến Constraint Qualification nói chung và Slater's condition nói riêng chứng tỏ bạn đã tìm hiểu vượt ra ngoài kiến thức cơ bản.
>
> ## Các Lĩnh Vực Cần Cải Thiện
>
> *   **Lý Giải Về Ràng Buộc λi ≥ 0:** Đây là điểm yếu đáng kể nhất trong bài phân tích của bạn. Lập luận "*Vì nếu không, fi(x) càng dương thì λifi(x) càng âm, → vi phạm constraint*" là chưa đủ chặt chẽ và có thể gây hiểu lầm. Lý do chính xác cho điều kiện `λi ≥ 0` là để đảm bảo tính hợp lệ của weak duality (g(λ, v) ≤ p*). Nếu λi < 0, một giá trị fi(x) dương (tức là vi phạm ràng buộc) sẽ làm giảm Lagrangian, điều này đi ngược lại mong muốn tìm kiếm giải pháp thỏa mãn ràng buộc khi tối thiểu hóa L(x,λ,v). Ràng buộc này xuất phát từ việc đảm bảo hàm đối ngẫu là lồi và cung cấp cận dưới hợp lệ cho bài toán gốc.
> *   **Khái Niệm "Unconstraint" (Bài Toán Không Ràng Buộc):** Phát biểu "*đưa về bài toán unconstraint*" khi nói về việc tích hợp ràng buộc vào hàm Lagrangian có thể gây nhầm lẫn. Bài toán gốc (primal problem) vẫn là bài toán có ràng buộc. Hàm Lagrangian chỉ là một công cụ để tìm kiếm các điểm dừng thỏa mãn ràng buộc, và nó là cơ sở để xây dựng bài toán đối ngẫu (dual problem), mà bản thân bài toán đối ngẫu này có thể có dạng không ràng buộc hoặc có ràng buộc đơn giản hơn (ví dụ: λ ≥ 0).
> *   **Cách Diễn Đạt Complementary Slackness:** Mặc dù bạn đã giải thích ý nghĩa rất chính xác, nhưng việc viết "*Σi λ*ifi(x*) = 0 với mọi i*" cho điều kiện complementary slackness hơi thiếu trực tiếp. Chuẩn xác hơn nên là "*λ*i fi(x*) = 0 cho MỌI i = 1, 2, ..." Điều này nhấn mạnh rằng mỗi cặp ràng buộc và nhân tử Lagrange tương ứng phải thỏa mãn điều kiện này, không chỉ tổng của chúng.
>
> ## Đề Xuất Để Nâng Cao Hiểu Biết
>
> *   **Nghiên Cứu Sâu Hơn Về Dual Problem:** Tìm hiểu kỹ hơn về cách chứng minh λi ≥ 0 một cách hình thức từ lý thuyết hàm đối ngẫu và tính lồi/lõm của nó. Điều này sẽ củng cố nền tảng lý thuyết cho một trong những điều kiện cốt lõi của KKT.
> *   **Phân Biệt Lagrangian và Bài Toán Đối Ngẫu:** Làm rõ trong tư duy của bạn về vai trò của hàm Lagrangian trong việc xử lý bài toán gốc có ràng buộc, và vai trò của bài toán đối ngẫu như một bài toán tối ưu hóa độc lập (thường dễ giải hơn) cung cấp thông tin về bài toán gốc.
> *   **Ví Dụ Thực Tế:** Áp dụng KKT vào giải một vài bài toán tối ưu hóa cụ thể (cả lồi và không lồi) để củng cố sự hiểu biết về từng điều kiện và khi nào chúng là cần hay cần đủ.
>
> Bạn đã đi được một chặng đường rất dài trong việc nắm bắt KKT. Việc chỉnh sửa các điểm nhỏ nhưng quan trọng này sẽ giúp bạn đạt được sự tinh thông hoàn toàn về chủ đề này.
>
> **⭐ Bonus points**
> - Đề cập Slater's condition như một ví dụ cụ thể của Constraint Qualification.
> - Phân biệt rõ ràng KKT là điều kiện cần (tổng quát) và cần đủ (bài toán lồi với CQ).

<br>

<a id="node-4u120q2"></a>

###### Nói sơ về nội dung sắp tới

<p align="center"><kbd><img src="assets/gl2cj321imf.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý phần này nói sơ về nội dung sắp tới. 
>
> Section 4.1 sẽ bàn về cách giải solution của bài toán 4.3 - tức là bài toán minimize over p mk(p) constraint ||p|| ≤ Δ (mà ý nghĩa là từ xk đi tới đâu trong phạm vi vòng tròn chop phép đề xuống được thấp nhất nếu coi như đang đi trên cái bát quadratic mk). Thì có vài cách để giải bài toán này, tùy theo là Bk có tính chất gì.
>
> (nhớ lại: mk(p) = fk + ∇fkTp + (1/2)pT Bk p. Và Bk có thể chọn là ma trận xấp xỉ Hessian tại k hoặc cũng có thể là Hessian tại k, và mỗi cách chọn nó sẽ cho ra phương pháp khác)
>
> Thì nếu Bk xác định dương thì ta sẽ dùng phương pháp "dogleg"
>
> Nếu Bk không xác định thì dùng phương pháp "2D subspace minimization" 
>
> Và còn phương pháp thứ 3 nữa qua chương 7 mới nói, liên quan đến conjugate gradient.
>
> Qua phần 4.2 sẽ bàn về tốc độ hội tụ của mấy cái này.
>
> 4.3 thì bàn về một chiến thuật để dùng cách tiếp cận iterative để tính ra λ thỏa 4.6 (tức là (B + λI)p* = -g)
>
> 4.3 thì bàn về trust-region Newton method, chính là khi mà dùng Hessian tại k cho Bk nói ở trên. Và ta sẽ nói về đặc điểm của cái này là khi thuật toán này converge về một điểm x* có tính chất là thỏa điều kiện đủ bậc hai (tức là Hessian tại đó xác định dương đó) thì tốc độ hội tụ sẽ là siêu tuyến tính.

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ❌ **65/100** · ✓ Move on
>
> Bài làm cho thấy sự hiểu biết khá tốt về các phương pháp giải quyết bài toán phụ, nhưng mắc lỗi nghiêm trọng trong việc phân biệt nội dung giữa các phần, đặc biệt là Phần 4.3 và 4.4.
> ## Phân tích chi tiết
>
> ### Điểm mạnh
> *   **Hiểu biết cốt lõi về bài toán phụ:** Sinh viên đã nắm vững mục đích của bài toán phụ trong tối ưu hóa miền tin cậy và vai trò của nó (tìm điểm giảm giá trị hàm trong phạm vi cho phép).
> *   **Nắm rõ điều kiện áp dụng phương pháp:** Sinh viên đã mô tả chính xác khi nào nên sử dụng phương pháp `dogleg` (khi $B_k$ xác định dương) và `two-dimensional subspace minimization` (khi $B_k$ không xác định).
> *   **Kiến thức nền tảng vững chắc:** Việc nhớ lại công thức của $m_k(p)$ và khả năng lựa chọn $B_k$ là xấp xỉ Hessian hoặc Hessian thực cho thấy sinh viên có kiến thức nền tảng tốt về chủ đề này, vượt ra ngoài nội dung trực tiếp của đoạn văn.
> *   **Hiểu biết về điều kiện hội tụ:** Sinh viên đã giải thích đúng đặc điểm hội tụ siêu tuyến tính của phương pháp Newton miền tin cậy khi đạt điểm thỏa mãn điều kiện đủ bậc hai, bao gồm cả giải thích đúng về điều kiện Hessian xác định dương.
>
> ### Các điểm cần cải thiện
> *   **Nhầm lẫn nghiêm trọng giữa Phần 4.3 và 4.4:** Đây là lỗi lớn nhất. Sinh viên đã gán nội dung của Phần 4.4 (phương pháp Newton miền tin cậy) cho Phần 4.3, trong khi Phần 4.3 thực sự bàn về chiến lược lặp để tìm $\lambda$. Điều này cho thấy sự hiểu sai cấu trúc và mục đích của các phần trong tài liệu.
> *   **Thiếu điều kiện cho phương pháp gradient liên hợp:** Đối với chiến lược thứ ba (liên quan đến `conjugate gradient`), sinh viên đã bỏ sót điều kiện quan trọng là khi ma trận $B$ `large and sparse` (lớn và thưa).
> *   **Mô tả chưa chính xác về Phần 4.2:** Phần 4.2 tập trung vào việc chứng minh `global convergence results` (kết quả hội tụ toàn cục), không chỉ đơn thuần là `tốc độ hội tụ` chung chung của các phương pháp. Mặc dù liên quan, nhưng từ ngữ cần chính xác hơn theo tài liệu tham khảo.
> *   **Bỏ qua điểm Cauchy:** Sinh viên chưa đề cập đến `Cauchy point` - một khái niệm quan trọng được nhắc đến trong Phần 4.1 như một tiêu chuẩn so sánh cho các chiến lược xấp xỉ.
>
> ### Gợi ý để hiểu sâu hơn
> *   **Đọc kỹ tiêu đề và tóm tắt mỗi phần:** Để tránh nhầm lẫn cấu trúc, sinh viên nên dành thời gian đọc và ghi nhớ rõ ràng nội dung chính của từng phần (ví dụ: Phần 4.3 là về tìm $\lambda$, Phần 4.4 là về phương pháp Newton miền tin cậy).
> *   **Chú ý đến các điều kiện cụ thể:** Luôn ghi nhận các điều kiện áp dụng hoặc đặc điểm của từng phương pháp (ví dụ: $B$ `large and sparse` cho `conjugate gradient`).
> *   **Liên kết các khái niệm chính:** Cố gắng kết nối các khái niệm như `Cauchy point` với vai trò của chúng trong việc đánh giá hiệu quả của các chiến lược giải bài toán phụ.
> *   **Thực hành phân tích cấu trúc tài liệu:** Thường xuyên luyện tập việc tóm tắt nội dung từng phần nhỏ để củng cố khả năng nắm bắt cấu trúc logic của một tài liệu khoa học.
>
> **⭐ Bonus points**
> - Sinh viên đã nhớ lại chính xác công thức của hàm quadratic $m_k(p) = f_k + \nabla f_k^T p + (1/2)p^T B_k p$.
> - Sinh viên nhận ra rằng $B_k$ có thể là ma trận xấp xỉ Hessian hoặc Hessian thực, và mỗi lựa chọn dẫn đến các phương pháp khác nhau.
> - Sinh viên biết rằng điều kiện $(B + \lambda I)p^* = -g$ là một phương trình quan trọng liên quan đến việc tìm $\lambda$ trong bài toán miền tin cậy.
> - Sinh viên giải thích đúng rằng điều kiện đủ bậc hai tương đương với Hessian tại điểm đó xác định dương.

**🔗 See also:** [Trust Region Newton CG](./71_inexact_newton_methods.md#node-4fbrszp) · [Phương pháp Trust-Region Newton CG](./71_inexact_newton_methods.md#node-8tkd9oh)

<br>

