# 12.1 Examples

📊 **Progress:** `2` Notes | `2` Screenshots | `2` AI Reviews

---
<a id="node-frx2ram"></a>

## 12.1 Examples

<br>

<a id="node-ukukd7b"></a>

## Definition 12.1: The Active Set

<p align="center"><kbd><img src="assets/d6cagri7evw.png" width="80%"></kbd></p>

> [!NOTE]
> Trướới tiên, giáo sư dẫn dắt chúng ta qua một loạt định nghĩa về các khái niệm cốt lõi sẽ xuất hiện xuyên suốt chương này. Đầu tiên là định nghĩa về tập hoạt động (active set), ký hiệu là 𝒜(x).
>
>
>
> Dù định nghĩa này có vẻ phức tạp, chúng ta có thể làm rõ thông qua một số ý chính sau:
>
>
>
> Thứ nhất, active set là một **tập hợp phụ thuộc vào một điểm khả thi** (feasible point) x. Với mỗi điểm x khác nhau, chúng ta sẽ có các tập active set khác nhau.
>
>
>
> Thứ hai, active set là **tập hợp chứa các chỉ số (index numbers)**, chứ không chứa bản thân điểm x hay các vectơ x.
>
>
>
> Thứ ba, các chỉ số này **bao gồm toàn bộ chỉ số thuộc tập ℰ** (đại diện cho các ràng buộc đẳng thức - equality constraints) ..
>
>
>
> ..**hợp với** ...
>
>
>
> ..**các chỉ số thuộc tập I** (đại diện cho các ràng buộc bất đẳng thức - inequality constraints) nhưng chỉ lấy những chỉ số mà tại đó ràng buộc đạt giá trị bằng 0.
>
>
>
> Sở dĩ định nghĩa này dễ gây bối rối là do cách tiếp cận khái quát hóa bài toán tối ưu có ràng buộc. Thông thường, chúng ta không cần gọi tên cụ thể từng hàm ràng buộc là f1, f2, f3, f4. Chẳng hạn, trong cuốn sách "Convex Optimization" của Stephen Boyd, tác giả định nghĩa hàm mục tiêu (objective function) là f0, các ràng buộc bất đẳng thức là f1, f2, f3 &lt;= 0, và các ràng buộc đẳng thức là h1 = 0, h2 = 0.
>
>
>
> Trong khi đó, tác giả cuốn sách này sử dụng một hệ thống ký hiệu khác nhưng có cùng bản chất: hàm mục tiêu là f, và các hàm ràng buộc là ci với i là chỉ số.
>
>
>
> Giả sử chúng ta có 10 hàm ràng buộc từ c1, c2 đến c10. Trong đó, các ràng buộc đẳng thức có dạng c1(x) = 0, c3(x) = 0, c10(x) = 0.
>
>
>
> Các hàm còn lại là ràng buộc bất đẳng thức, tức là C2(x) &gt;= 0, C4(x) &gt;= 0, C6(x) &gt;= 0, ..
>
>
>
> Để phân chia thành hai nhóm, người ta gom các chỉ số của ràng buộc đẳng thức vào tập ℰ (viết tắt của equality constraints), ví dụ như {1, 3, 10}, và các chỉ số còn lại thuộc tập ℐ (inequality constraints).
>
>
>
> Nên với cách này, người ta chỉ cần nói minimize f(x) với constraint ci(x) = 0 với i ∈ ℰ = {1,3, 10} và ci(x) ≥ 0 với i ∈ ℐ = {2, 4,..}
>
>
>
> ---
>
>
>
> Quay trở lại định nghĩa, **tập 𝒜(x) luôn bằng tập ℰ hợp với một tập con của ℐ.**
>
>
>
> Do đó, bước đầu tiên là lấy **toàn bộ chỉ số của ℰ các ràng buộc đẳng thức** (như 1, 3, 10 trong ví dụ trên).
>
>
>
> Sau đó, chúng ta **xét tiếp các chỉ số thuộc tập ràng buộc bất đẳng thức tại điểm x cụ thể xem cái nào là = 0**. Tức là, cới điểm khả thi x, **tất cả các hàm ràng buộc bất đẳng thức như c2, c4, c5 đều đã phải ≥ 0**. Tuy nhiên, chúng ta c**hỉ lọc ra những chỉ số mà tại đó hàm ràng buộc bằng đúng 0**. Ví dụ, nếu c2(x) = 0 và c5(x) = 0 trong khi c4(x) &gt; 0, ta sẽ lấy các chỉ số {2, 5} để hợp với tập ℰ, từ đó tạo thành tập hoạt động (active set) 𝒜(x) cho điểm x.
>
>
>
> Cuối cùng nói thêm một ý nữa:
>
>
>
> Đối với các ràng buộc bất đẳng thức trong tập ℐ, tại điểm khả thi x, giá trị của chúng luôn không âm: ci(x) ≥ 0 ∀ i ∈ ℐ. **Nếu tại x, hàm ràng buộc bằng đúng 0**, ta gọi ràng buộc đó là r**àng buộc hoạt động (active constraint)**. Ví dụ trong ví dụ ta nói ở trên, vì C2(x) = 0 nên ràng buộc c2 đang hoạt động (active). Ngược lại, vì c4(x) &gt; 0 nên ràng buộc C4 &gt;= 0 không hoạt động (inactive).

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **98/100**
>
> Ghi chú rất xuất sắc, giải thích chính xác và trực quan định nghĩa về tập hoạt động (active set) kèm ví dụ minh họa rõ ràng và so sánh hệ thống ký hiệu với sách của Stephen Boyd. Bạn chỉ cần lưu ý chỉnh sửa một vài lỗi chính tả nhỏ để bài viết thêm phần hoàn thiện.

<br>

<a id="node-wamf4mj"></a>

### Equality Constrained Optimization Example

<p align="center"><kbd><img src="assets/2u99oxt6qvr.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo, giáo sư đưa ra một ví dụ về việc tối thiểu hóa hàm số x1 + x2. Đây là bài toán tối ưu hóa hai biến với một ràng buộc đẳng thức là x1^2 + x2^2 - 2 = 0. 
>
>
>
> Chiếu theo ngôn ngữ định nghĩa tổng quát của bài toán tối ưu có ràng buộc, hàm mục tiêu (objective function) f chính là x1 + x2. Do chỉ có một ràng buộc đẳng thức, tập chỉ số ℐ chứa các ràng buộc bất đẳng thức dĩ nhiên là tập rỗng. Trong khi đó, tập chỉ số ký hiệu bởi chữ E viết hoa, ℰ chứa các ràng buộc đẳng thức chỉ có một phần tử duy nhất là {1}. Hàm ràng buộc này chính là c1(x) = x1^2 + x2^2 - 2, với ràng buộc đẳng thức tương ứng là c1(x) = 0.
>
>
>
> Với bài toán này, chúng ta **có thể vẽ được tập khả thi (feasible set)**. Theo định nghĩa, tập khả thi là tập hợp các điểm thỏa mãn ràng buộc. Trong trường hợp này, đó là tập hợp các điểm x thỏa mãn phương trình x1^2 + x2^2 = 2. Khi biểu diễn trực quan, tập hợp này **chính là đường tròn có tâm tại gốc tọa độ và bán kính bằng căn 2**. Giáo sư đặc biệt nhấn mạnh rằng **tập khả thi ở đây chỉ là đường tròn chứ không phải hình tròn**.
>
>
>
> Như vậy, bản chất của bài toán này là **tìm các điểm nằm trên đường tròn sao cho tổng hai tọa độ của chúng là nhỏ nhất**. Nghiệm của bài toán rất dễ nhận thấy chính là điểm có tọa độ (-1, -1). Chúng ta có thể suy nghĩ thêm lý do tại sao giáo sư lại khẳng định điều này là rõ ràng để nhận thấy.
>
>
>
> Để hình dung trực quan, khi di chuyển trên đường tròn này, nếu đang ở góc phần tư phía trên bên phải, cả hai tọa độ đều mang giá trị dương. Để giảm tổng tọa độ, chúng ta phải di chuyển về phía góc phần tư phía trên bên trái hoặc góc phần tư phía dưới bên phải, khi đó sẽ có một tọa độ âm. Và dĩ nhiên, khi xuống góc phần tư phía dưới bên trái, cả hai tọa độ đều âm, giúp tổng hai tọa độ giảm xuống nhiều hơn nữa. Từ đó, có thể xây dựng một lập luận để giải thích vì sao điểm (-1, -1) lại cho tổng nhỏ nhất.
>
>
>
> Một ý nữa được giáo sư đề cập là **khi đứng ở một điểm bất kỳ trên đường tròn này, ta cũng dễ dàng tìm thấy một hướng đi để vừa đảm bảo tính khả thi** (nghĩa là vẫn di chuyển trên đường tròn) **vừa làm giảm giá trị của hàm f**. Ví dụ, nếu đang đứng ở điểm chấm màu xanh có tọa độ (0, căn 2), bằng cách di chuyển xuống góc phần tư phía dưới bên phải để tọa độ x2 bắt đầu âm và tọa độ x1 cũng giảm xuống, tổng x1 + x2 rõ ràng sẽ giảm. Nhìn chung, giáo sư muốn sử dụng ví dụ này để mang lại một hình ảnh trực quan về tập khả thi và bài toán tối ưu có ràng buộc.

> [!TIP]
> **🤖 AI Feedback** — ✅ Score: **92/100**
>
> Bản ghi chép rất chi tiết, chính xác và thể hiện sự hiểu bài sâu sắc về khái niệm tập khả thi cũng như cách xác định nghiệm tối ưu bằng trực quan. Tuy nhiên, bạn đã nhầm lẫn điểm ví dụ từ tọa độ $(\sqrt{2}, 0)^T$ trong sách thành $(0, \sqrt{2})$, dẫn đến lập luận hướng di chuyển giảm hàm mục tiêu chưa hoàn toàn chính xác.

<br>

