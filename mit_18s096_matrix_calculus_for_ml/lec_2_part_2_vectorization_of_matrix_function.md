# Lec 2 Part 2: Vectorization Of Matrix Function

📊 **Progress:** `3` Notes | `3` Screenshots | `2` AI Reviews

---
<a id="node-ighv0k4"></a>

<br>

<a id="node-7r0x4t1"></a>

## Đạo hàm ma trận

<p align="center"><kbd><img src="assets/p115vlyh7w.png" width="80%"></kbd></p>

> [!NOTE]
> đầu tiên gs Steve gợi nhớ lại trong 18.06 thầy Strang có nói vector trong vector space **không chỉ nói về column vector**, mà còn **có thể là matrix, function.**..miễn sao nó thỏa điều kiện là **i) add hai vector**trong space vẫn tạo vector nằm trong space và ii) **scale vector với scalar** thì vẫn nằm trong space
>
>
>
> Thì ở đây gs sẽ nói về **function nhận input là matrix và output matrix**. ví dụ như function **nhận vào matrix A**, trả ra **A⁻¹**, **A^3** hoặc trả ra kết quả sau khi **elimination A đưa nó về dạng U** - upper triangular hoặc reduce echelon form.
>
>
>
> Hoặc có thể **output ra scalar** ví dụ như function **tính determinant**hoặc **trace của matrix**
>
>
>
> Đương nhiên là ta sẽ nói về **cách tính derivative của các function này**

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất tốt, nắm bắt chính xác ý tưởng mở rộng đạo hàm sang các không gian vector tổng quát (đặc biệt là ma trận) và liên hệ chuẩn xác với kiến thức từ khóa học 18.06.
>
> **✓ Strengths**
> - Hiểu đúng bản chất không gian vector tổng quát không chỉ giới hạn ở vector cột mà bao gồm cả ma trận và hàm số.
> - Phân loại rõ ràng hai nhóm hàm số: hàm nhận ma trận trả về ma trận và hàm nhận ma trận trả về scalar.
> - Nắm đúng mục tiêu trọng tâm của bài giảng là tính đạo hàm cho các hàm ma trận này.
>
> **💡 Deeper notes**
> - Trên bài giảng còn có ví dụ scalar output là giá trị suy biến lớn nhất $\sigma_1(A)$ (largest singular value).
> - Đối với hàm $f(A) = A^{-1}$, ngầm định điều kiện ma trận $A$ khả nghịch (khác 0 về định thức), và đạo hàm của các hàm như phép khử Gauss hay giá trị suy biến có thể gặp điểm không khả vi.

<br>

<a id="node-7wwf5cv"></a>

### Vi phân ma trận A^3

<p align="center"><kbd><img src="assets/j9br9ye4kjm.png" width="80%"></kbd></p>

> [!NOTE]
> Ta tính df với f(A) = A^3. Kết qủa là **df = dA.A^2 + A.dA.A + A^2.dA**
>
>
>
> Ở đây chú ý **PHẢI HIỂU f'(A) [dA] LÀ OPERATOR f'(A) ACT ON dA** và cụ
> thể là **dA.A^2 + A.dA.A + A^2.dA**
>
>
>
> Tại sao ra công thức này thì dễ thôi ta cứ làm theo cách làm bữa giờ:
>
>
>
> **df** = f(A+dA) - f(A) = **(A+dA)^3 - A^3**
>
>
>
> Thế thì **(A+dA)^3** phải triển khai là **(A+dA)(A+dA)(A+dA)**
>
>
>
> = (A.A + dA.A + A.dA + dA.dA)(A + dA)
>
>
>
> = A.A.A + dA.A.A + A.dA.A + dA.dA.A + A.A.dA + dA.A.dA + A.dA.dA + dA.
> dA.dA
>
>
>
> = A^3 + dA.A^2 + A.dA.A + dA^2.A + A^2.dA + dA.A.dA + A.dA^2 + dA^3
>
>
>
> Từ đó df = A^3 + dA.A^2 + A.dA.A + dA^2.A + A^2.dA + dA.A.dA + A.dA^2 +
> dA^3 - A^3
>
>
>
> = **dA.A^2** + **A.dA.A** + /dA^2.A/ + **A^2.dA** + /dA.A.dA/ +/ A.dA^2/
> + /dA^3/
>
>
>
> Và ta sẽ **bỏ đi các higher order term**
>
>
>
> = **dA.A^2 + A.dA.A + A^2.dA**
>
>
>
> Và gs chú ý phép nhân matrix không **commutative** - tức không thể thay
> đổi thứ tự phép nhân được do đó không thể chuyển AdAA thành AAdA =
> A^2dA và da.A^2 = A^2.dA để rồi cộng ba cái thành 3A^2dA
>
>
>
> Trừ khi việc nhân A,dA có tính chất **commutative** hoặc **khi ta chuyển chúng
> thành vector**.
>
> df với f(A) = A^3

<br>

<a id="node-ms9bk9i"></a>

#### Vi phân ma trận nghịch đảo

<p align="center"><kbd><img src="assets/f1unq3dbck.png" width="80%"></kbd></p>

> [!NOTE]
> gs nói một ví dụ khác. tính df của **f(A) = A⁻¹**
>
>
>
> Thế thì để làm vậy ta sẽ để ý là **d(A⁻¹A) = d(I) = 0**. Lí do là bởi dù 
> có perturb A như thế nào thì **f(A) = A⁻¹A luôn bằng I**. 
>
>
>
> Tức df (ý là của f(A) = A⁻¹A) luôn bằng 0
>
>
>
> Thứ hai là dựa vào product rule: **d(AB) = (dA)B + AdB**
> ta có **d(A⁻¹A) = dA⁻¹A + A⁻¹dA**
>
>
>
> Và kết hợp hai cái ta có **dA⁻¹A + A⁻¹dA = 0**
>
>
>
> <=> **dA⁻¹.A = - A⁻¹.dA** 
>
>
>
> Nhân A⁻¹ vào bên phải hai vế
>
>
>
> <=> dA⁻¹.A.A⁻¹ = -A⁻¹.dA.A⁻¹
>
>
>
> <=> **dA⁻¹ = -A⁻¹.dA.A⁻¹**
>
> f(g,h) = g*h 
>
>
>
> df(g,h) = f(g+dg, h+dh) - f(g,h)
>
>
>
> = (g+dg)(h+dh) - gh
>
>
>
> = gh + g(dh) + (dg)h + dg dh - gh
>
>
>
> = g(dh) + (dg)h
>
> df, với f(A) = A⁻¹:
>
>
>
> dA⁻¹ = -A⁻¹.dA.A⁻¹

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **95/100** · ✓ Move on
>
> Ghi chú nắm rất chắc và chính xác toàn bộ quá trình biến đổi để tìm vi phân của ma trận nghịch đảo, đặc biệt chú ý đúng thứ tự nhân ma trận.
>
> **🟡 Minor issues**
>
> **1.** *"= gh + g(dh) + (dg)h + dg dh - gh 

 = g(dh) + (dg)h"*
>
> Khi khai triển vi phân tích, số hạng bậc hai `dg dh` bị triệt tiêu vì là vô cùng bé bậc cao (o(||dg|| + ||dh||)), bạn nên chú thích rõ điều này thay vì viết dấu '=' trực tiếp.
>
>
> **✓ Strengths**
> - Hiểu chính xác việc lấy vi phân hai vế từ đẳng thức A^(-1)A = I để tìm df.
> - Bảo toàn đúng thứ tự phép nhân ma trận (nhân A^(-1) vào bên phải cả hai vế), tránh được lỗi nhầm lẫn giao hoán.
> - Tự suy luận lại quy tắc vi phân của tích (product rule) cho tích ma trận.
>
> **💡 Deeper notes**
> - Phép vi phân này ngầm định A nằm trong tập mở các ma trận khả nghịch GL(n, R), đảm bảo lân cận của A cũng khả nghịch.
> - Kết quả df = -A^(-1)(dA)A^(-1) biểu diễn đạo hàm Fréchet f'(A) dưới dạng một ánh xạ tuyến tính tác động lên bước nhiễu dA.

**🔗 See also:** [Phương pháp vi phân Adjoint](./lec_4_part_2_nonlinear_rooting_finding_optimization_and_adjoint_gradient_methods.md#node-ne1rah0)

<br>

