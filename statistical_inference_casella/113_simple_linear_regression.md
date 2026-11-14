# 11.3 Simple Linear Regression

📊 **Progress:** `32` Notes | `59` Screenshots | `32` AI Reviews

---
<a id="node-m4lr6nj"></a>

<br>

<a id="node-0xbdf1h"></a>

## Simple Linear Regression

<p align="center"><kbd><img src="assets/l65ztblrfym.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là, phần trước, với ANOVA, ta học cách phân tích tác động của các yếu tố lên mean của response variable.
>
>
>
> Phần này ta sẽ học về simple linear regression - để hiểu sự phụ thuộc của một variable lên variable khác.
>
>
>
> Cụ thể thể, ta có quan hệ: Yi = α + βxi + εi
>
>
>
> Với Yi và εi là random variable. Với E\[εi\] thường được assume = 0
>
>
>
> α, β là fixed và unknown parameter (gọi là intercept và slope)
>
>
>
> còn xi là observable variable (có thể hiểu là đây là giá trị sẽ quan sát được, không coi là random varible)
>
>
>
> Khi đó, E\[Y\] với tư cách là hàm số của x được gọi là population regression function.
>
>
>
> ---
>
>
>
> Liên hệ chút với chương 3 sách Bishop, trong đó ta giả định T|𝐱 \~ 𝒩(𝐰ᵀΦ(𝐱), 1/β), để rồi theo decision theory, ta dùng y(𝐱) = 𝐰ᵀΦ(𝐱) để dự đoán target cho input 𝐱. Đương nhiên y(𝐱) chính là E\[T|𝐱\], nên ở đây có thể hiểu thêm cái này chính là population regression function.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác các khái niệm mở đầu của hồi quy tuyến tính đơn và có liên hệ sâu sắc, chuẩn xác với hàm hồi quy kỳ vọng có điều kiện E[T|x] trong sách Bishop.
>
> **✓ Strengths**
> - Nắm bắt chính xác vai trò của các thành phần trong mô hình hồi quy (biến ngẫu nhiên Y và sai số, tham số cố định alpha, beta, và biến giải thích x).
> - Liên hệ rất tốt với góc nhìn xác suất và Decision Theory trong machine learning (sách Bishop), nhận diện đúng population regression function chính là hàm kỳ vọng có điều kiện.
>
> **💡 Deeper notes**
> - Trong thống kê cổ điển (fixed design), x_i thường được xem là các giá trị cố định được chọn trước thay vì biến ngẫu nhiên. Khi chuyển sang góc nhìn tổng quát hơn (random design như trong Bishop), ta viết rõ là kỳ vọng có điều kiện E[Y|X=x].

**🔗 See also:** [Best Linear Unbiased Estimators](#node-l6jbbvb)

<br>

<a id="node-jc8c4m4"></a>

### Population Regression Function and Variables

<p align="center"><kbd><img src="assets/s86b3cclu9d.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với bài toán regression, mục đích chính là dự đoán Yi từ input xi.
>
>
>
> Thế thì người ta gọi Yi là dependent variable, còn xi là independent variable ám chỉ trong quan hệ Yi = α + βxi + εi ở trên, Yi phụ thuộc xi.
>
>
>
> Có điều tác giả cho rằng, cách gọi này gây khó hiểu, vì TA THƯỜNG KHÔNG COI x LÀ RANDOM VARIBLE. Thành ra như vậy thì sẽ không mắc mớ gì dùng chữ independent (kiểu như hai random variable independent)
>
>
>
> Do đó ta sẽ dùng reponse variable và predictor variable (giống trong ISL)
>
>
>
> ---
>
>
>
> Và ta sẽ ghi E\[Yi|xi\] để nhấn mạnh sự phụ thuộc vào xi
>
>
>
> Đây cũng chính là cái mình thấy trong Bishop, y(𝐱) = E\[T|𝐱\] = 𝐰ᵀ𝐱 chính là cách ghi để nhấn mạnh rằng, ta lấy kì vọng của conditional distribution của T|𝐱 \~ 𝒩(𝐰ᵀ𝐱, 1/β) để dự đoán.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú tóm tắt rất tốt, nắm bắt chính xác lý do tác giả đề xuất tránh dùng thuật ngữ 'independent variable' để không nhầm lẫn với tính độc lập trong xác suất thống kê.
>
> **✓ Strengths**
> - Hiểu chính xác lý do cốt lõi: x_i thường được xem là các giá trị cố định (không nhất thiết là biến ngẫu nhiên), nên việc dùng từ 'independent' dễ gây hiểu nhầm sang khái niệm biến ngẫu nhiên độc lập.
> - Nắm trọn vẹn thuật ngữ chuẩn thay thế được khuyên dùng là 'response variable' và 'predictor variable', có liên hệ tốt với kiến thức sách ISL.
>
> **💡 Deeper notes**
> - Trong kinh tế lượng hoặc hồi quy cổ điển, mô hình thường giả định 'fixed design' (x là hằng số cố định được chọn trước). Dù trong một số bài toán hiện đại (random design) x cũng có thể là biến ngẫu nhiên, việc dùng cặp từ 'predictor - response' vẫn giúp phân biệt rõ vai trò dự báo thay vì ngụ ý tính độc lập xác suất.

<br>

<a id="node-5swaigg"></a>

#### Linear Regression and Conditional Expectation

<p align="center"><kbd><img src="assets/b42zcctzlw4.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/580ach0syvx.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này tác giả nhấn mạnh cách ta nên hiểu về chữ regression: Có thể hiểu cụm "regression của Y on X" là E\[Y|X=x\]. Nhưng khái quát hơn, chữ regression của Y on X thể hiện quan hệ của Y đối với giá trị x của X.
>
>
>
> Nên nói "regression của Y on X là linear function" thì hiểu là: quan hệ giữa giá trị của Y đối với giá trị x của X là hàm tuyến tính, hay E\[Y|X=x\] là một hàm tuyến tính f(x) nào đó.
>
>
>
> Và E\[Yi|xi\] = α + βxi có thể dùng cho cả hai case: xi là giá trị cố định nào đó, hoặc xi là giá trị cụ thể của một random variable Xi nào đó.
>
>
>
> ---
>
>
>
> Một ý quan trọng:
>
>
>
> Nói regression is linear thì như đã nói, ám chỉ E\[Y|X=x\] = α + βx là hàm tuyến tính đối với x
>
>
>
> Còn **linear regression** thì lại chỉ E\[Y|X=x\] là **hàm tuyến tính đối với tham số α và β**. Do đó
>
>
>
> E\[Y|X=x\] = α + βx² là LINEAR REGRESSION nhưng REGRESSION CỦA Y ON X KHÔNG LINEAR.
>
>
>
> Cuối cùng, là chữ regression ra đời khi đại ý là ông nhà sinh vật học Galton quan sát thấy hiện tượng cha lùn thì sin con lùn như có xu hướng cao lên còn cha cao sinh con cao như có khuynh hướng lùn đi. Ông gọi là "quay về với trung bình" thì chữ regression chính là mang ý "quay về" - "hồi quy"

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=26Q9kLHdbkc)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, nắm bắt trọn vẹn và chính xác các điểm cốt lõi trong đoạn văn bản, đặc biệt là sự phân biệt giữa 'regression that is linear' (tuyến tính theo biến độc lập) và 'linear regression' (tuyến tính theo tham số).
>
> **✓ Strengths**
> - Phân biệt chính xác giữa khái niệm hàm hồi quy tuyến tính theo x và mô hình hồi quy tuyến tính theo tham số (linear in parameters).
> - Hiểu đúng bản chất của x_i dù là giá trị thiết kế cố định (fixed) hay là quan sát từ biến ngẫu nhiên X_i.
> - Nắm rõ nguồn gốc lịch sử và ý nghĩa của thuật ngữ 'hồi quy về giá trị trung bình' (regression toward the mean) của Galton.
>
> **💡 Deeper notes**
> - Dù phương trình điều kiện E(Y|x) có cùng dạng giải thích khi x_i cố định hay ngẫu nhiên, việc suy diễn thống kê (inference) sẽ có sự khác biệt khi xét đến phân phối đồng thời của (X, Y) thay vì chỉ phân phối có điều kiện của Y|X.

**🔗 See also:** [Error Function for Regression *(Pattern Recognition Machine Learning_C.Bishop)*](../pattern_recognition_machine_learning_cbishop/52_training.md#node-y877d09)

<br>

<a id="node-o9p0cdo"></a>

##### Example 11.3.1 Predicting Grape Crops

<p align="center"><kbd><img src="assets/dnuasxfww9a.png" width="80%"></kbd></p>

> [!NOTE]
> Một ví dụ về một bộ data: x là số chùm nho, và Y là kết quả thu hoạch của mùa nho. Năm 1972 bị thiếu do bão. Đại khái là nếu vẽ ra, ta sẽ thấy regression của Y on x (E\[Y|x\]) rõ ràng là tuyến tính.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất tốt và chính xác nội dung ví dụ từ sách, đồng thời liên hệ trực tiếp mối quan hệ tuyến tính với hàm hồi quy $E[Y|x]$.
>
> **✓ Strengths**
> - Xác định đúng các biến số: biến dự báo $x$ (số chùm) và biến mục tiêu $Y$ (sản lượng).
> - Ghi nhận chính xác chi tiết dữ liệu khuyết thiếu của năm 1972.
> - Liên hệ tốt giữa việc trực quan hóa dữ liệu (scatter plot) với giả định hàm hồi quy tuyến tính $E[Y|x]$.
>
> **💡 Deeper notes**
> - Trên thực tế, đồ thị phân tán quan sát được (scatter plot) chỉ thể hiện mối quan hệ tuyến tính mạnh giữa các điểm mẫu; việc kết luận $E[Y|x]$ là tuyến tính là một giả định mô hình hồi quy (linear regression model) được hỗ trợ bởi dữ liệu đó.

<br>

<a id="node-73smgnz"></a>

###### Section 11.3 Simple Linear Regression

<p align="center"><kbd><img src="assets/8b6llhokbai.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6ykcye83xi8.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, khi ta dùng phương trình E\[Yi|xi\] = α + βxi thì ta đã **NGẦM GIẢ ĐỊNH** REGRESSION CỦA Y ON X LINEAR.
>
>
>
> hoặc ít nhất, ta **ĐANG HI VỌNG / GIẢ ĐỊNH** rằng E\[Yi|xi\] ≈ α + βxi CÓ THỂ LÀ **MỘT PHÉP XẤP XỈ TỐT**
>
>
>
> Và nếu ta bắt đầu với giả định mạnh là: (X,Y) \~ bivariate normal, thì khi đó đương nhiên E\[Y|X=x\] chính là linear function theo x: xem link, tới note chương 4, nói rằng nếu ta có X, Y có joint pdf là bivariate normal với mean (μX,μY), variance σ²X,σ²Y và correlation ρ, thì given X = x, conditional distribution của Y là n(μY + ρ(σY/σX)(x - μX), σ²Y(1-ρ²))
>
>
>
> ---
>
>
>
> Tiếp theo
>
>
>
>  Rằng khi làm regression analysis - chính là mô tả việc nghiên cứu quan hệ giữa predictor và response ta sẽ thấy có hai bước:
>
>
>
> Bước 1 thuần túy là data-oriented, đại khái là ta sẽ tính toán gì đó, nhưng ý chính nhấn mạnh là bước này không phải là bước inference, do đó, chưa giả định gì về tham số cả.
>
>
>
> Bước 2 mới là inference. Và ta sẽ giả định rằng slope và intercept (α và β trong E\[Y|x\] = α + βx) là thứ có tồn tại trong quan hệ của response và predictor. Tức là, ta giả định rằng quả thật quan hệ của E\[Y|x\] và x có thể được ước lượng bởi hàm tuyến tính: E\[Y|x\] ≈ α + βx mà hàm số này bị chi phối bởi hai tham số α và β (chính là giả định ở trên)
>
>
>
> Dựa trên giả định đó, ta mới đi inference hai tham số này

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=V-6BNavEGgU)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú nắm bắt rất chính xác và sâu sắc toàn bộ nội dung trong tài liệu, từ bản chất giả định tuyến tính đến sự phân biệt giữa bước tóm tắt dữ liệu (data fitting) và suy diễn thống kê (inference).
>
> **✓ Strengths**
> - Hiểu chính xác rằng mô hình hồi quy tuyến tính ngầm giả định kỳ vọng có điều kiện E[Y|X] là tuyến tính hoặc ít nhất xấp xỉ tuyến tính đủ tốt.
> - Liên kết xuất sắc kiến thức từ phân phối chuẩn hai biến (bivariate normal) để chỉ ra nguồn gốc lý thuyết của hàm hồi quy tuyến tính.
> - Phân biệt rành mạch giữa bước mô tả dữ liệu thuần túy (không cần giả định tham số) và bước suy diễn thống kê cho tổng thể (cần giả định về sự tồn tại của các tham số).
>
> **💡 Deeper notes**
> - Ở bước suy diễn thống kê (bước 2), để thiết lập các kiểm định và khoảng tin cậy chính xác cho các tham số tổng thể α và β, ta thường giả định quan hệ kỳ vọng trong tổng thể thỏa mãn chính xác E[Y|X=x] = α + βx (đi kèm giả định về sai số) thay vì chỉ là xấp xỉ.

**🔗 See also:** [Phân phối chuẩn hai biến](./45_covariance_correlation.md#node-ljt1bsi) · [Hội tụ phân phối có điều kiện](./45_covariance_correlation.md#node-g2hs1nk)

<br>

<a id="node-7ilb1oo"></a>

###### Two Steps of Regression Analysis

<p align="center"><kbd><img src="assets/uff97moaxxj.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/u41qkns543.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là dữ liệu quan sát được sẽ bao gồm n cặp giá trị (x1,y1),....(xn,yn)
>
>
>
> Đoạn này sẽ lược dịch ý vì cơ bản là tác giả đang mô tả những gì sẽ làm (nên chả có gì mà phải suy nghĩ, đọc và biết vậy thôi)
>
>
>
> và trong phần này ta sẽ xem xét qua vài **mô hình** của dữ liệu này, mà mỗi mô hình sẽ mang trong mình **những giả định khác nhau** về việc x hay y hay cả hai là giá trị quan sát của biến ngẫu nhiên X,Y (chưa hiểu lắm ý này, nhưng mình đoán là: có thể trong các mô hình khác nhau này, ta có thể chỉ coi X hoặc chỉ Y hoặc cả hai X,Y đều là biến ngẫu nhiên.
>
>
>
> Rồi, kế tới nói n data point này ko mằm chính xác trên đường thẳng, nhưng mình muốn summarizing sample information bằng cách khớp một đường thẳng vào chúng. Và ta sẽ thấy các approach khác nhau dẫn ta tới cùng 1 đường thẳng.
>
>
>
> tính toán vài thứ, như sample mean, x̄, ȳ
>
>
>
> sum of squares Sxx = Σi (xi - x̄)², Syy = Σi (yi - ȳ)²
>
>
>
> sum of cross-products: Sxy = Σi (xi - x̄)(yi - ȳ)
>
>
>
> Và đây là estimate phổ biến nhất cho α và β (mà ta sẽ lần lượt biện minh dưới các mô hình khác nhau):
>
>
>
> b = Sxy/Sxx; a = ȳ - bx̄

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác và đầy đủ nội dung đoạn mở đầu, nắm bắt trọn vẹn cả công thức lẫn các ý định tiếp cận của tác giả.
>
> **✓ Strengths**
> - Dự đoán trực giác rất chính xác về việc x, y có thể là biến ngẫu nhiên hoặc giá trị cố định (fixed design vs random predictor).
> - Ghi chép lại chính xác và cô đọng các công thức định nghĩa trung bình mẫu, tổng bình phương sai lệch và ước lượng tham số a, b.
>
> **💡 Deeper notes**
> - Công thức hệ số góc $b = S_{xy} / S_{xx}$ ngầm giả định $S_{xx} > 0$, tức các điểm dữ liệu $x_i$ không hoàn toàn trùng nhau (ít nhất có hai giá trị $x$ khác nhau).

**🔗 See also:** [BLUE of Linear Estimators](#node-s1vw0l4) · [Estimation with Normal Errors](#node-c6564df)

<br>

<a id="node-g2r7hr9"></a>

###### Figure 11.3.1 Vertical Distances for RSS

<p align="center"><kbd><img src="assets/qy9dy0fuh2.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xrdqc9czacl.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qeiemws0suq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4zqpjvd23g8.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái nói là, quá trình ta **tìm ra estimate đầu tiên** cho α và β hoàn toàn **không cần giả định nào về distribution của data (xi, yi)**, i=1,2,...n
>
>
>
> Cách làm như sau: Tìm cách vẽ đường thẳng đi xuyên qua đám mây dữ liệu sao cho "as close as possible" - theo vertical distance
>
>
>
> Và để làm cái vụ as close as possible này, ta mới định nghĩa ra cái gọi là RSS: Residual Sum of Squares, có thể hiểu là hàm số của các đường thẳng: c + dx, tức với c, d khác nhau, RSS sẽ khác nhau.
>
>
>
> RSS = Σi (yi - (c + dxi))²
>
>
>
> Và từ đó c,d giúp minimize RSS được gọi là **LEAST SQUARE ESTIMATE** CHO α, β:
>
>
>
> α̂, β̂ = argmin_c,d Σi (yi - (c + dxi))²
>
>
>
> cũng là Σi (yi - (α̂ + β̂ xi))² = min_c,d Σi (yi - (c + dxi))²
>
>
>
> ---
>
>
>
> Để giải bài toán tối ưu này (minimize c,d Σi (yi - (c + dxi))², như đã biết, có thể giải theo từng biến giải theo c trước (giữ d fix):
>
>
>
> Biến đổi tí: Σi (yi - (c + dxi))² = Σi ((yi - dxi) - c)²
>
>
>
> Đạo hàm theo c: d/dc \[Σi ((yi - dxi) - c)²\] = Σi d/dc \[((yi - dxi) - c)²\] = Σi \[2((yi - dxi) - c) . d/dc ((yi - dxi) - c)\]
>
>
>
> = Σi \[2((yi - dxi) - c) . (-1)\] = -2 Σi ((yi - dxi) - c)
>
>
>
> Cho đạo hàm bằng 0 tìm điểm dừng: -2 Σi ((yi - dxi) - c) = 0 ⇔ Σi ((yi - dxi) - c) = 0 ⇔ c = (1/n) Σi (yi - dxi)
>
>
>
> ⇔ c = (Σi yi)/n - d(Σi xi)/n = ȳ - d x̄
>
>
>
> Đạo hàm cấp 2: d/dc \[-2 Σi ((yi - dxi) - c) \] = 2n &gt; 0 ⇒ điểm dừng chính là cực tiểu.
>
>
>
> ---
>
>
>
> Lắp c\* vào và giải tìm d:
>
>
>
> Σi \[(yi - dxi) - ȳ + dx̄ \]² = Σi \[yi - dxi - ȳ + dx̄ \]² = Σi \[(yi - ȳ) - d(xi - x̄ )\]²
>
>
>
> = Σi \[(yi - ȳ)² - 2d(yi - ȳ)(xi - x̄ ) + d²(xi - x̄ )²\]
>
>
>
> = Σi(yi - ȳ)² - 2d Σi(yi - ȳ)(xi - x̄ ) + d² Σi(xi - x̄ )²
>
>
>
> = Syy - 2d Sxy + d² Sxx
>
>
>
> d/dd (Syy - 2d Sxy + d² Sxx) = - 2Sxy + 2d Sxx
>
>
>
> d/dd (Syy - 2d Sxy + d² Sxx) = 0
>
>
>
> ⇔ - 2Sxy + 2d Sxx = 0
>
>
>
> ⇔ d = Sxy/Sxx
>
>
>
> Đạo hàm cấp 2: 2Sxx &gt; 0 nên điểm dừng là minimizer
>
>
>
> Vậy α̂ (hay a) = ȳ - β̂ x̄ và β̂ (hay b) = Sxy/Sxx chính là LEAST-SQUARE ESTIMATE của α và β

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, hiểu đúng bản chất không tham số/phân phối của phương pháp bình phương tối thiểu và tự thực hiện chi tiết từng bước đạo hàm tối ưu hóa đầy đủ, chính xác.
>
> **✓ Strengths**
> - Nắm vững bản chất phương pháp bình phương tối thiểu thuần túy về mặt hình học/đại số mà không cần giả định phân phối xác suất.
> - Tự triển khai chi tiết các bước đạo hàm riêng và kiểm tra đạo hàm bậc hai để xác nhận cực tiểu thay vì chỉ chấp nhận công thức có sẵn.
>
> **💡 Deeper notes**
> - Điều kiện $2S_{xx} > 0$ để đạo hàm bậc hai dương và chia được cho $S_{xx}$ ngầm đòi hỏi các giá trị $x_i$ không hoàn toàn bằng nhau (tức có ít nhất hai điểm dữ liệu có hoành độ khác nhau).

<br>

<a id="node-2hdz214"></a>

###### Horizontal Distance Least Squares Line

<p align="center"><kbd><img src="assets/31qvzbnlr2.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/v8dklzv2aom.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/5vy8civi2sd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý đoạn này là: nếu ta đổi sang dùng thước đo distance RSS trong đó residual là ri = xi - (c + dyi) (tức là đường thẳng bây giờ là x = c + dy, và dùng horizontal distance.
>
>
>
> Thì giả sử gọi c,d minimize RSS lúc này là a', b'. Ta sẽ có đường x = a' + b'y ⇔ y = x/b' - a'/b'. Đây gọi là regression của x on y. Và nó thường sẽ khác với đường y = a + bx (với a,b là least square estimate của α, β)
>
>
>
> Tác giả đại khái là viện tới bất đẳng thức Holder's Inequality để chứng minh điều này:
>
>
>
> Nếu muốn hai đường trùng nhau thì ta cần hệ số góc bằng nhau cái đã:
>
>
>
> 1/b' = b ⇔ b / (1/b') = 1 ⇔ bb' = 1
>
>
>
> Mà b = Sxy/Sxx, b' (gỉai tương tự như note trước, ta sẽ có Sxy/Syy)
>
>
>
> ⇔ Sxy² / SxxSyy
>
>
>
> và bất đẳng thức Holder đại ý là chứng minh Sxy² / SxxSyy ≤ 1 nên trừ trường hợp đặc biệt khi bất đẳng thức bằng, còn lại là nó sẽ &lt; 1 đồng nghĩa hai đường regression trên sẽ khác nhau.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác và mạch lạc bản chất của hồi quy x theo y, việc so sánh hai đường hồi quy qua hệ số góc và ứng dụng bất đẳng thức Hölder (Cauchy-Schwarz) để chỉ ra hai đường này thường không trùng nhau.
>
> **✓ Strengths**
> - Hiểu đúng bản chất residual theo khoảng cách ngang và cách biểu diễn lại đường hồi quy x theo y dưới dạng y = f(x).
> - Chỉ ra chính xác điều kiện bằng nhau của hai hệ số góc dẫn tới tích bb' = (Sxy)² / (Sxx Syy).
> - Nắm rõ vai trò của bất đẳng thức Hölder/Cauchy-Schwarz khi chỉ ra (Sxy)² / (Sxx Syy) ≤ 1 và kết luận hai đường nói chung là khác nhau.
>
> **💡 Deeper notes**
> - Trường hợp đặc biệt xảy ra dấu bằng chính là khi toàn bộ các điểm dữ liệu nằm chính xác trên một đường thẳng (tương quan tuyến tính tuyệt đối |r| = 1).
> - Cả hai đường hồi quy (y theo x và x theo y) đều luôn đi qua điểm trung bình mẫu (x̄, ȳ), do đó khi hệ số góc khác nhau thì chúng cắt nhau ngay tại điểm trọng tâm này.

<br>

<a id="node-p6369qb"></a>

###### Least Squares Solutions vs Estimates

<p align="center"><kbd><img src="assets/pyq23c1dgea.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đại ý đoạn này là: nếu ta nói x là predictor variable, và y là response variable, thì mong muốn dự đoán y từ x sẽ khiến việc dùng RSS với vertical distance trở nên hợp lí, vì rõ ràng là nó đo sai khác giữa dự đoán (ŷi = c + dxi) và target yi.
>
>
>
> Tuy nhiên, nếu như TA HOÀN TOÀN KHÔNG CÓ NHU CẦU DỰ ĐOÁN y TỪ x, thì ta sẽ không có gì để biện minh cho việc nên dùng vertical distance hay horizontal distance, mà hai cái này lại cho ra hai regression line khác nhau. Đại khái là đây là một bất cập.
>
>
>
> Thêm nữa, tác giả nói rất rõ: Trong việc đưa đến estiamate cho α β bằng least square như vừa rồi, rõ ràng là ta không dựa trên bất cứ giả định nào của distribution của data. Do đó, đây không phải là STATISTICAL INFERENCE, do đó, chỉ nên gọi chúng là LEAST SQUARE SOLUTION, KHÔNG NÊN GỌI LÀ LEAST SQUARE ESTIMATE. Vì estimate ám chỉ kết quả có được từ bài toán statistical inference (ví dụ maximum likelihood estimate)
>
>
>
> Tuy vậy, ta sẽ thấy least square solution có vài đặc điểm tối ưu

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác và nắm bắt trọn vẹn bản chất các luận điểm của tác giả về vai trò của biến, sự khác biệt giữa bài toán tối ưu hình học thuần túy và suy diễn thống kê.
>
> **✓ Strengths**
> - Hiểu chính xác lý do tại sao RSS đo khoảng cách thẳng đứng lại hợp lý khi dự đoán y từ x, và tại sao việc không phân định biến lại dẫn đến sự mơ hồ giữa khoảng cách ngang và dọc.
> - Nắm rất vững sự phân biệt tinh tế giữa 'least squares solution' (nghiệm của bài toán tối ưu hình học thuần túy) và 'least squares estimate' (ước lượng bắt nguồn từ một mô hình thống kê có suy diễn).
>
> **💡 Deeper notes**
> - Khi không phân biệt vai trò giữa x và y (cả hai đều có sai số ngẫu nhiên đối xứng), phương pháp bình phương tối thiểu toàn phần (Total Least Squares / Orthogonal Regression) hoặc PCA thường được dùng để tối thiểu hóa khoảng cách vuông góc (perpendicular distance).
> - Khái niệm 'statistical model' ở đây bao hàm việc đặt ra cấu trúc xác suất $Y = eta_0 + eta_1 X + \varepsilon$ cùng các giả định về sai số (ví dụ: kỳ vọng bằng 0, không đổi phương sai, độc lập), điều kiện cần thiết để xây dựng khoảng tin cậy và kiểm định giả thuyết thay vì chỉ khớp đường thẳng.

<br>

<a id="node-l6jbbvb"></a>

###### Best Linear Unbiased Estimators

<p align="center"><kbd><img src="assets/7yzz0mpqg7f.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/oyl4bmgxic.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, qua phần này, ta sẽ tiếp tục biện minh cho giá trị estimate cho α và β với công thức 11.3.8 theo một mô hình khác. còn nhớ, phần trước ta đã thấy đó chính là giá trị của c, d giúp minimize SSE - tạo ra đường thẳng đi sát nhất với data theo tiêu chí vertical distance. Và còn nhớ tác giả nói, kết quả đó hoàn toàn chưa phải là một statistical inference, vì ta chưa dựa trên giả định gì về phân phối của data.
>
>
>
> Còn ở đây, đại ý là ta sẽ làm statistical inference thật sự, và cũng cho ra công thức đó.
>
>
>
> Thế thì giả định về phân phối của data như sau, mà theo tác giả là một giả định rất khiêm tốn:
>
>
>
> Đối chiếu với một bài toán point estimation điển hình, nơi đề bài cho:
>
>
>
> Các random varible X1, X2,....Xn \~ n(μ, σ²) iid, và quan sát được giá trị của chúng: x1,x2,...xn. Thì đây chính là nói ta giả định x1,x2,...xn là giá trị quan sát được của đám biến ngẫu nhiên X1,...Xn độc lập và có cùng phân phối là n(μ, σ²)
>
>
>
> Thì ở đây, đề bài là ta có:
>
>
>
> Random variable Y1, Y2,....Yn, có giá trị quan sát y1, y2,...yn.
>
>
>
> Và không như giả định X1,X2,....\~ n(μ, σ²), ở đây ta chỉ giả định E\[Yi\] = α + βxi, và Y1,....Yn uncorrelate và Var(Yi) = σ² ∀i.
>
>
>
> Nói vậy để thấy, giả định của ta rất khiêm tốn, khi ko giả định dạng của phân phối, mà chỉ là dạng của hai moment đầu tiên.
>
>
>
> Và cái giả định này hoàn toàn có thể thể hiện bởi kiểu khác:
>
>
>
> y1,...yn là giá trị quan sát của Y1,...Yn với 
>
>
>
> Yi = α + βxi + εi, εi uncorrelate
>
>
>
> và E\[εi\] = 0, Var(εi) = σ²
>
>
>
> Thêm nữa, trong mô hình (giả định) này, x1,x2,...xn không phải là giá trị quan sát của biến ngẫu nhiên X gì hết, nó chỉ là giá trị fix có sẵn. Còn y1,y2,...mới là observed value của biến ngẫu nhiên Y
>
>
>
>
>
> ---
>
>
>
> Dừng lại tí xíu, có thể sẽ lú, vì hình như mình đã gặp cái này rồi, chẳng phải là ở phần đầu khi nói về simple linear regression đã nói rồi sao?
>
>
>
> Thì đúng là như vậy, đây chính là nhắc lại chuyện đó: có nghĩa là trong simple linear regression, ta giả định regression của Y on X, tức E\[Y|X=x\] là hàm tuyến tính theo x và theo tham số: E\[Y|x\] = α + βx, bên cạnh đó còn giả định ràng Var(Y|x) là σ², cố định, không phụ thuộc x. Nhưng ở đây, có thêm giả định: y1, y2,...là gía trị quan sát của Y1, Y2,....và đám này uncorrelate.
>
>
>
> Nói cách khác, simple linear regression vốn đã giả định Y = α + βx + ε với E\[ε\] = 0, Var(ε) = σ². Thì qua đây, ta CÓ THÊM GIẢ ĐỊNH NỮA: y1,y2,...là gía trị quan sát của Y1, Y2,....và đám Yi này uncorrelate.
>
>
>
> ---

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú nắm rất chắc và chính xác bản chất thống kê của mô hình: phân biệt rõ giữa bình phương tối thiểu thuần túy (hình học) và suy diễn thống kê, hiểu đúng vai trò của các biến $x_i$ (giá trị cố định) so với $Y_i$ (biến ngẫu nhiên), cũng như nhận thức sâu sắc việc mô hình Gauss-Markov chỉ yêu cầu hai moment đầu tiên mà không cần giả định phân phối cụ thể.
>
> **✓ Strengths**
> - Phân biệt rất rõ ràng giữa tối thiểu hóa SSE thuần túy hình học ở phần trước và mô hình suy diễn thống kê ở phần này.
> - Hiểu chính xác rằng $x_1, \dots, x_n$ là các giá trị cố định (fixed design) được chọn trước chứ không phải biến ngẫu nhiên.
> - Nắm được tính 'khiêm tốn' nhưng mạnh mẽ của giả định Gauss-Markov: chỉ cần giả định về hai moment đầu (kỳ vọng tuyến tính, phương sai không đổi và không tương quan) mà không cần phân phối chuẩn.
>
> **💡 Deeper notes**
> - Trong thiết kế thực nghiệm với $x_i$ cố định (fixed-X design), việc các sai số $\epsilon_i$ không tương quan dẫn trực tiếp đến các $Y_i$ không tương quan; nếu mở rộng sang mô hình $X$ ngẫu nhiên (random design), ta thường cần điều kiện kỳ vọng có điều kiện $E[\epsilon|X]=0$ và các cặp $(X_i, Y_i)$ độc lập.

**🔗 See also:** [Simple Linear Regression](#node-0xbdf1h)

<br>

<a id="node-9e061wl"></a>

###### Linear Unbiased Estimator for Slope

<p align="center"><kbd><img src="assets/vm8bd7fm619.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/g563p68lzyh.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, đại khái là ta sẽ học một class / lớp / loại estimator gọi là estimator tuyến tính (linear estimator). được định nghĩa là estimator (của β) có dạng:
>
>
>
> W(𝐘) = Σi di Yi
>
>
>
> vì sao ghi W(𝐘), vì estimator về bản chất chỉ là hàm số của sample, sample ở đây chính là Y1,...Yn, y như tìm point estimator của θ trong bài toán point estimator là đi tìm hàm W(𝐗), để khi lắp observed value 𝐱 vào, 𝐖(𝐱) sẽ có một point estimate cho θ.
>
>
>
> Rồi, ta sẽ lại chỉ giới hạn tìm kiếm trong những unbiased estimator. Nhớ lại trong chương 7, nếu E\[W(𝐗)\] = θ, thì đó gọi là unbiased estimator của θ.
>
>
>
> Vậy thì ở đây, unbised linear estimator, chính là W(𝐘) có: E\[W(𝐘)\] = β với mọi giá trị của β và α
>
>
>
> ⇔ E\[Σi di Yi\] = β
>
>
>
> ⇔ Σi di EYi = β
>
>
>
> ⇔ Σi di (α + βxi) = β
>
>
>
> ⇔ Σi di α + Σi di βxi = β
>
>
>
> ⇔ α Σi di  + β Σi di xi = β
>
>
>
> Và như vậy Σi di phải bằng 0 và Σi di xi phải bằng 1 để E\[W(𝐘)\] = β với mọi giá trị của β và α
>
>
>
> Do đó công thức của unbiased linear estimator là W(𝐘) = Σi di Yi, Σi di = 0 và Σi di xi = 1

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất tốt, trình bày chuẩn xác và tường minh từng bước biến đổi đại số cũng như liên kết rất tốt với bản chất của ước lượng điểm đã học ở chương trước.
>
> **✓ Strengths**
> - Hiểu rất rõ bản chất của một estimator là hàm của mẫu số liệu và liên hệ chính xác với khái niệm W(X) ở chương ước lượng điểm.
> - Tự diễn giải và triển khai đầy đủ, mạch lạc từng bước biến đổi đại số từ kỳ vọng đến hệ điều kiện của d_i.
>
> **💡 Deeper notes**
> - Trong mô hình hồi quy tuyến tính cổ điển, các giá trị x_i được xem là các hằng số đã biết (fixed constants), tương tự như các hệ số d_i, do đó chúng không bị ảnh hưởng bởi toán tử lấy kỳ vọng E.

<br>

<a id="node-xyldl8i"></a>

###### Best Linear Unbiased Estimator (BLUE)

<p align="center"><kbd><img src="assets/chu05f305s4.png" width="80%"></kbd></p>

> [!NOTE]
> Active recall tí xíu về best unbiased estimator:
>
>
>
> Bài toán point estimation đại khái là có đề bài như sau:
>
>
>
> Cho random sample 𝐗 = X1,...Xn có giá trị quan sát được là 𝐱 = (x1,...xn) iid \~ f(x|θ), ví dụ n(μ, 1). Nhiệm vụ là đi tìm good estimator của θ, tức μ.
>
>
>
> Point estimator của θ được định nghĩa là: hàm số của sample W(𝐗), để khi lắp 𝐱 vào, ta có point estimate cho θ
>
>
>
> W(𝐱) = argmax\_θ L(θ|𝐱)
>
>
>
> W(𝐗) = argmax\_θ L(θ|𝐗)
>
>
>
> Bias(W) = E\[W(𝐗)\] - θ
>
>
>
> Bias(W) = 0 ⇔ E\_θ\[W(𝐗)\] = θ, thì W(𝐗) được gọi là unbiased estimator của θ.
>
>
>
> Square Loss L(W(𝐗),θ) = \[W(𝐗) - θ\]²
>
>
>
> MSE: E\_θ\[L(W(𝐗),θ)\] = E\_θ\[(W(𝐗) - θ)²\]
>
>
>
> Xét (W(𝐗) - θ)² = W(𝐗)² - 2W(𝐗)θ + θ²
>
>
>
> E\_θ\[(W(𝐗) - θ)²\] = E\_θ\[W(𝐗)² - 2W(𝐗)θ + θ²\]
>
>
>
> = E\_θ\[W(𝐗)²\] - E\_θ\[2W(𝐗)θ\] + E\_θ\[θ²\] 
>
>
>
> (linearity của kì vọng: E(aX + bY + c) = aEX + bEY + c)
>
>
>
> = E\_θ\[W(𝐗)²\] - 2θ E\_θ\[W(𝐗)\] + θ² + (E\_θ\[W(𝐗)\])² - (E\_θ\[W(𝐗)\])²
>
>
>
> = E\_θ\[W(𝐗)²\] - (E\_θ\[W(𝐗)\])² + (E\_θ\[W(𝐗)\])²  - 2θ E\_θ\[W(𝐗)\] + θ² 
>
>
>
> ---
>
>
>
> Xét (E\_θ\[W(𝐗)\])²  - 2θ E\_θ\[W(𝐗)\] + θ²
>
>
>
> = {E\_θ\[W(𝐗)\] - θ}²
>
>
>
> = Bias(W(𝐗))²
>
>
>
> ---
>
>
>
> E\_θ\[W(𝐗)²\] - (E\_θ\[W(𝐗)\])²
>
>
>
> Nhớ lại công thức Var(X) = E\[(X-EX)²\]
>
>
>
> = E\[(X²-2X(EX) + (EX)²\]
>
>
>
> = E\[X²\]-E\[2X(EX)\] + E\[(EX)²\]
>
>
>
> = E(X²) - (EX)²
>
>
>
> ---
>
>
>
> E\_θ\[W(𝐗)²\] - (E\_θ\[W(𝐗)\])² chính là Var\[W(𝐗)\] 
>
>
>
> Như vậy MSE(W(𝐗)) =  Var\[W(𝐗)\] + Bias(W(𝐗))²
>
>
>
> Bây giờ nếu như mình có unbiased estimator của θ: Bias(W(𝐗)) = 0
>
>
>
> Khi đó MSE(W(𝐗)) = Var\[W(𝐗)\]
>
>
>
> Best unbiased estimator của θ: có variance nhỏ nhất.

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=0QxT5Qi1RfE)

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **92/100** · ✓ Move on
>
> Ghi chú rất tốt, tự suy dẫn trọn vẹn phân rã MSE = Var + Bias² để làm sáng tỏ lý do vì sao ước lượng không chệch tốt nhất (best) lại tương đương với phương sai nhỏ nhất. Có một điểm nhỏ cần lưu ý là không nên đồng nhất ước lượng điểm nói chung với công thức của MLE.
>
> **🟡 Minor issues**
>
> **1.** *"Point estimator của θ được định nghĩa là: hàm số của sample W(𝐗), để khi lắp 𝐱 vào, ta có point estimate cho θ

W(𝐱) = argmax_θ L(θ|𝐱)"*
>
> Đoạn này dễ gây nhầm lẫn: hàm cực đại hóa likelihood (MLE) chỉ là một phương pháp tìm ước lượng cụ thể, không phải là định nghĩa tổng quát của mọi ước lượng điểm W(X).
>
>
> **✓ Strengths**
> - Tự chứng minh đầy đủ, chính xác từng bước phân rã MSE thành tổng của Variance và Bias².
> - Hiểu rõ bản chất vì sao khi một ước lượng là không chệch (Bias = 0) thì tiêu chí tối thiểu hóa MSE đồng nhất với việc tìm ước lượng có phương sai nhỏ nhất (Best Unbiased Estimator).
>
> **💡 Deeper notes**
> - Trong bối cảnh bài học ở sách giáo khoa (BLUE - Gauss-Markov Theorem), chữ 'Linear' (tuyến tính) giới hạn không gian tìm kiếm chỉ trong các hàm tuyến tính của biến phản hồi Y; do đó BLUE là ước lượng có phương sai nhỏ nhất trong lớp ước lượng tuyến tính không chệch, chứ không nhất thiết là nhỏ nhất trên toàn bộ không gian ước lượng phi tuyến (UMVUE).

<br>

<a id="node-s1vw0l4"></a>

###### BLUE of Linear Estimators

<p align="center"><kbd><img src="assets/chu05f305s4.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4qhgxrpeyf3.png" width="80%"></kbd></p>

> [!NOTE]
> b = Sxy / Sxx
>
>
>
> a = ȳ - bx̄
>
>
>
> Ok, đại khái ta đã biết để có một unbiased linear estimator, thì W(𝐘) = Σi diYi phải có kì vọng bằng β với mọi α,β. Dẫn tới hai ràng buộc là Σi di = 0 và Σi di xi = 1
>
>
>
> Thế thì như note trước vừa ôn lại, với point estimator của θ, để có cái gọi là the best unbiased estimator của θ thì Var(W(𝐗)) phải nhỏ nhất trong đám các unbiased estimator.
>
>
>
> Tương tự như vậy, để gọi là the best unbiased estimator của β thì Var(W(𝐘)) phải nhỏ nhất.
>
>
>
> ---
>
>
>
> Xét Var(W(𝐘)) = Var(Σi diYi)
>
>
>
> Áp dụng công thức Var(X1+X2+...Xn) = Var(X1) + ..Var(Xn) + 2Cov(X1,X2) + 2Cov(X1,X3)....
>
>
>
> = Σi Var(Xi) + Σi,j,i≠j 2Cov(Xi,Xj)
>
>
>
> Nếu Xi, Xj uncorrelate, tức Cov(Xi,Xj)/STD(Xi)STD(Xj) = 0 ⇔ Cov(Xi,Xj) = 0
>
>
>
> Do đó, vì Yi uncorrelate nên Var(Σi diYi) = Σi Var(diYi)
>
>
>
> = Σi di² Var(Yi) (tính chất variance: Var(cX) =  c²Var(X))
>
>
>
> = Σi di² σ² (Var(Yi) = σ² ∀i, đây là giả định của simple linear regression)
>
>
>
> = σ² Σi di² 
>
>
>
> ---
>
>
>
> Như vậy, để Var(W(𝐘)) nhỏ nhất thì Σi di²  phải nhỏ nhất.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **90/100** · ✓ Move on
>
> Ghi chú đã ghi lại chính xác công thức tính hệ số góc $b$ và hệ số chặn $a$ trong hồi quy tuyến tính đơn giản. Tuy nhiên, ghi chú khá ngắn gọn và chưa đề cập đến bản chất BLUE (ước lượng tuyến tính không chệch tốt nhất) được trình bày trong tài liệu.
>
> **✓ Strengths**
> - Ghi lại chính xác công thức chuẩn cho ước lượng hệ số góc b = Sxy / Sxx và hệ số chặn a = ȳ - bx̄.
>
> **💡 Deeper notes**
> - Tài liệu gốc sử dụng ký hiệu S_{xY} (với Y viết hoa) để nhấn mạnh đây là biến ngẫu nhiên / ước lượng (estimator), phụ thuộc vào các biến ngẫu nhiên Y_i, khác với giá trị mẫu cụ thể S_{xy}.
> - Đoạn văn bản chủ yếu tập trung chứng minh b là ước lượng tuyến tính không chệch tốt nhất (BLUE) của β dựa trên việc tối thiểu hóa tổng d_i^2.

**🔗 See also:** [Two Steps of Regression Analysis](#node-7ilb1oo)

<br>

<a id="node-fgu25fe"></a>

###### Lemma 11.2.7 Contrast Maximization

<p align="center"><kbd><img src="assets/h550a9c9c8m.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0uaahjjodw6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ujn0b7b9bdc.png" width="80%"></kbd></p>

> [!NOTE]
> Cov(X,Y) = E\[(X-EX)(Y-EY)\]
>
>
>
> = E\[XY-(EX)Y-X(EY)+(EX)(EY)\]
>
>
>
> = E(XY) - (EX)(EY) - (EX)(EY) + (EX)(EY)
>
>
>
> = E(XY) - (EX)(EY)
>
>
>
> ---
>
> Bất đẳng thức Cauchy-Schwarz:
>
>
>
> E\[(U-tV)²\] ≥ 0 ∀t
>
>
>
> ⇔ E\[U² - 2U(tV) + (tV)²\] ≥ 0
>
>
>
> ⇔ E\[U²\] - E\[2U(tV)\] + E\[(tV)²\] ≥ 0
>
>
>
> ⇔ E\[U²\] - 2tE\[UV\] + t²E\[V²\] ≥ 0
>
>
>
> ⇔ E\[V²\]t² - 2E\[UV\]t + E\[U²\] ≥ 0 ∀t (1)
>
>
>
> Xét hàm f(t) = E\[V²\]t² - 2E\[UV\]t + E\[U²\]
>
>
>
> d/dt f(t) = 2E\[V²\]t - 2E\[UV\]
>
>
>
> Điều kiện tối ưu cần bậc nhất: d/dt f(t) = 0 ⇔ 2E\[V²\]t - 2E\[UV\] = 0
>
>
>
> ⇔ t = E\[UV\]/ E\[V²\] (giả định E\[V²\] &gt; 0)
>
>
>
> d/dt \[2E\[V²\]t - 2E\[UV\]\] = 2E\[V²\] ≥ 0 với t
>
>
>
> Suy ra hàm số đạt cực tiểu tại t0 = E\[UV\] / E\[V²\]
>
>
>
> (1) ⇔ f(t0) ≥ 0
>
>
>
> E\[V²\](E\[UV\]/ E\[V²\])² - 2E\[UV\](E\[UV\]/ E\[V²\]) + E\[U²\] ≥ 0
>
>
>
> ⇔ (E\[UV\])²/ E\[V²\] - 2(E\[UV\])²/ E\[V²\] + E\[U²\] ≥ 0
>
>
>
> ⇔ -(E\[UV\])²/ E\[V²\] + E\[U²\] ≥ 0
>
>
>
> ⇔ E\[U²\] ≥ (E\[UV\])²/ E\[V²\]
>
>
>
> ⇔ E\[U²\]E\[V²\] ≥ (E\[UV\])²
>
>
>
> đây chính là bất đẳng thức Cauchy-Schwarz:
>
>
>
> (E\[UV\])² ≤ E\[U²\]E\[V²\]
>
>
>
> ---
>
>
>
> Áp dụng cho U = (X - EX), V = (Y - EY)
>
>
>
> (E\[(X - EX)(Y - EY)\])² ≤ E\[(X - EX)²\]E\[(Y - EY)²\]
>
>
>
> (Cov(X,Y))² ≤ Var(X)Var(Y)
>
>
>
> ⇔ -STD(X)STD(Y) ≤ (Cov(X,Y)) ≤ STD(X)STD(Y)
>
>
>
> ⇔ -1 ≤ Cov(X,Y) / STD(X)STD(Y) ≤ 1
>
>
>
> ⇔ -1 ≤ Corr(X,Y) ≤ 1
>
>
>
> ---
>
>
>
> Bổ đề nói rằng cho (v1,...vk) là constant và (c1,...ck) là constant dương. Và 𝒜 = {𝐚=(a1,...ak): Σiai = 0} thì khi đó:
>
>
>
> max\_𝐚∈𝒜 {(Σi aivi)² / (Σi ai²/ci)} = Σi ci(vi - v̄c)² với v̄c = Σi civi / Σici
>
>
>
> Và maximum sẽ đạt tại 𝐚 có dạng ai = Kci(vi-v̄c) với K là constant khác 0
>
>
>
> ---
>
>
>
> Chứng minh đại khái như sau:
>
>
>
> Đặt ℬ = {𝐛: (b1,...bk): Σi bi = 0 và Σi bi²/ci = 1}. Với mọi 𝐚 ∈ 𝒜, đặt 𝐛 sao cho:
>
>
>
> bi = ai/√(Σj aj²/cj) (1)
>
>
>
> ⇒ bi² = ai² / (Σj aj²/cj)
>
>
>
> Dễ thấy khi đó Σi bi²/ci = Σi \[ai² / (Σj aj²/cj)\] / ci = \[1/ (Σj aj²/cj)\] Σi ai²/ci = (Σi ai²/ci)/(Σj aj²/cj) = 1
>
>
>
> và Σi bi = Σi ai/√(Σj aj²/cj) = 0
>
>
>
> ---
>
>
>
> (1) cũng suy ra ai = bi √(Σj aj²/cj) 
>
>
>
> ⇒ Σi ai vi = Σi bivi √(Σj aj²/cj) = (Σi bivi) √(Σj aj²/cj)
>
>
>
>  ⇔ (Σi ai vi)² = (Σi bivi)² (Σj aj²/cj)
>
>
>
>  ⇔ (Σi ai vi)²/ (Σi ai²/ci)= (Σi bivi)² (Σj aj²/cj) / (Σi ai²/ci) 
>
>
>
>  ⇔ (Σi ai vi)²/ (Σi ai²/ci) = (Σi bivi)² 
>
>
>
> ---
>
>
>
> Nhắc nhớ rằng, ta cần chứng minh chính là  là max\_𝐚∈𝒜 {vế trái ở trên} = Σi ci(vi - v̄c)²
>
>
>
> Nên nay ta cần chứng minh max\_𝐚∈𝒜 {vế phải ở trên, tức (Σi bivi)² } = Σi ci(vi - v̄c)²
>
>
>
> ---
>
>
>
> Vậy bài toán là maximize (Σi bivi)² , thì cơ bản là ta xem thử nó ≤ cái gì (tìm upperbound)
>
>
>
> Và đại khái là thì (Σi bivi)² chính là (E\[BV\])². 
>
>
>
> Đã ôn lại ở trên Cov(X,Y) = E(XY) - (EX)(EY)
>
>
>
> Mà E\[B\] = 0, nên Cov(B,V) = E\[BV\]
>
>
>
> Nên theo Cauchy Schwart inequality: \[Cov(B,V)\]² ≤ Var(B)Var(V)
>
>
>
> ⇔ (E\[BV\])² ≤ Var(B)Var(V)
>
>
>
> Giờ làm rõ vì sao Σi bivi lại là E\[BV\]:
>
>
>
> Là bởi vì nếu đặt U là random variable = BV với B là rv có possible values; b1/c1,...bk/ck, V là rv có possible values v1,...vk Và joint pmf của B,V là P(B=bi/ci, V=vi) = ci/C (Σi ci/C = 1) thì 
>
>
>
> Hãy nhìn U ở dạng: hàm của B,V: U = g(B,V) = B × V
>
>
>
> khi đó theo LOTUS:
>
>
>
> E\[U\] = E\[BV\] = Σi (bi/ci) vi P(Bi=bi/ci, Vi=vi)
>
>
>
> = Σi (bi/ci)vi ci/C
>
>
>
> Vậy E\[BV\] = Σi (bi/ci)vi ci/C 
>
>
>
> ⇔ C × E\[BV\] = Σi bivi 
>
>
>
> ⇔ E\[BV\] = Σi bivi / C
>
>
>
> ---
>
>
>
> (E\[BV\])² ≤ Var(B)Var(V)
>
>
>
> ⇔ (Σi bivi)²/C²  ≤ Var(B)Var(V)
>
>
>
> Var(B) = E\[(B-EB)²\] = Σi (bi/ci - 0)² × P(B=bi/ci) = Σi (bi/ci)² × (ci/C) 
>
>
>
> Var(V)  = E\[(V-EV)²\]
>
>
>
> EV = Σi vi P(V=vi) = Σi vi ci/C = (Σi vici) / (Σi ci), đặt là v̄c
>
>
>
> ⇒ Var(V) = Σi (vi-v̄)² (ci/C)
>
>
>
> ---
>
>
>
> .. ⇔ (Σi bivi)²/C² ≤ \[Σi (bi/ci)² × (ci/C)\] \[Σi (vi-v̄c)² (ci/C)\]
>
>
>
> ⇔ \[Σi bivi\]²/C² ≤  \[Σi (bi/ci)² × (ci/C)\] \[Σi (vi-v̄c)² (ci/C)\]
>
>
>
> Dùng Σi bi²/ci = 1 ⇔ Σi \[(bi²/ci²) × ci\] = 1 ⇔ Σi \[(bi²/ci²) × ci/C\] = 1/C
>
>
>
> .. ⇔ \[Σi bivi\]²/C² ≤  (1/C) \[Σi (vi-v̄c)² (ci/C)\]
>
>
>
> ⇔ \[Σi bivi\]²≤  Σi \[(vi-v̄c)² ci\]
>
>
>
> ⇔ \[Σi bivi\]²≤  Σi \[ci(vi-v̄c)²\] → 11.2.11
>
>
>
> ---
>
>
>
> Cuối cùng, đại khái là khi dùng vector 𝐚 với ai = Kci(vi-v̄c) thì ta thấy: 𝐚 ∈ 𝒜 đồng thời lắp vô Σi bivi thì ra được kết quả là √vế phải, chứng minh xong rằng nó chính là solution của maximize\_ 𝐚∈𝒜 \[Σi bivi\]² và tại đó \[Σi bivi\]² cũng là {(Σi aivi)² / (Σi ai²/ci)} sẽ đặt max = Σi ci(vi - v̄c)²

📹 Video 1: [Lemma 11.2.7 Contrast Maximization — Statistical Inference - Casella](https://www.youtube.com/watch?v=BnLldZjJnlc)

📹 Video 2: [Chứng minh bất đẳng thức Cauchy-Schwarz không cần học thuộc lòng.](https://www.youtube.com/watch?v=gpURGn0c_74)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, trình bày đầy đủ từ việc chứng minh lại bất đẳng thức Cauchy-Schwarz đến từng bước biến đổi chi tiết của Bổ đề 11.2.7 thông qua góc nhìn biến ngẫu nhiên.
>
> **✓ Strengths**
> - Tự suy biến và chứng minh chặt chẽ bất đẳng thức Cauchy-Schwarz bằng phương pháp tối ưu hàm bậc hai f(t) trước khi áp dụng vào bài.
> - Hiểu rất rõ và diễn giải rành mạch cách chuyển đổi tổng trọng số sang kỳ vọng toán học E[BV] cùng luật LOTUS theo phân phối xác suất ci/C.
> - Chứng minh rõ ràng tính tương đương giữa bài toán gốc và bài toán tối ưu trên tập B thông qua phép chuẩn hóa.
>
> **💡 Deeper notes**
> - Trường hợp E[V²] = 0 khi chứng minh Cauchy-Schwarz là suy biến (V = 0 hầu chắc chắn), khi đó E[UV] = 0 và bất đẳng thức hiển nhiên trở thành đẳng thức 0 ≤ 0.
> - Khi kiểm tra điều kiện đạt dấu bằng với ai = K ci (vi - v̄c), nếu K < 0 thì √(K²) = -K, dẫn đến ∑ bi vi = -√(∑ ci(vi - v̄c)²); tuy nhiên khi bình phương lên giá trị cực đại vẫn giữ nguyên là ∑ ci(vi - v̄c)².

<br>

<a id="node-q19qd3o"></a>

###### Application of Lemma 11.2.7

<p align="center"><kbd><img src="assets/ld8gf90z8nq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/o42hbu3jxk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ugd5sknwsaf.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp nối note trước: Như vậy, để Var(W(𝐘)) nhỏ nhất thì Σi di² phải nhỏ nhất.
>
>
>
> Note liền trước ta đã học bổ đề 11.2.7, nói rằng:
>
>
>
> Bổ đề nói rằng cho (v1,...vk) là constant và (c1,...ck) là constant dương. Và 𝒜 = {𝐚=(a1,...ak): Σi ai = 0} thì khi đó:
>
>
>
> max\_𝐚∈𝒜 {(Σi aivi)² / (Σi ai²/ci)} = Σi ci(vi - v̄c)² với v̄c = Σi civi / Σici
>
>
>
> Và maximum sẽ đạt tại 𝐚 có dạng ai = Kci(vi-v̄c) với K là constant khác 0
>
>
>
> Vậy áp dụng vào đây: cho k = n, vi = xi, ci = 1, ai = di, v̄c = Σi xi / n = x̄
>
>
>
> khi đó maximize {𝐝 thỏa Σi di = 0} của {(Σi dixi)² / (Σi di²)} sẽ bằng Σi (xi-x̄)² và đạt được maximum khi 𝐝 = (d1,..dn) sao cho di = K(xi-x̄)
>
>
>
> Bên cạnh đó, đại ý là vì tập {𝐝 = (d1,...dn): Σi di = 0, Σi dixi = 1} ⊂ {𝐝 = (d1,...dn): Σi di = 0}
>
>
>
> nên nếu 𝐝 với di = K(xi-x̄) với K khác 0 như trên là solution của maximize\_𝐝 {(Σi dixi)² / (Σi di²)} s.t Σi di = 0
>
>
>
> thì với nếu xét trên không gian biến hẹp hơn (thêm ràng buộc  Σi dixi = 1) thì chỉ cần nó thỏa ràng buộc, thì dĩ nhiên nó cũng sẽ là solution của maximize\_𝐝 {(Σi dixi)² / (Σi di²)} s.t Σi di = 0, Σi dixi = 1
>
>
>
> ---
>
>
>
> Vậy thì với 𝐝 = (d1,..dk) với di = K(xi-x̄)
>
>
>
> Σi dixi = Σi K(xi-x̄)xi = K Σi (xi-x̄)xi  = K Sxx
>
>
>
> (Sxx = Σi (xi-x̄)xi)
>
>
>
> để thỏa Σi dixi = 1 ⇔ K Sxx = 1 ⇔ K = 1/Sxx
>
>
>
> Vậy, với K = 1/Sxx, thì 𝐝: di = K(xi-x̄) = (xi-x̄)/Sxx sẽ thỏa ràng buộc Σi dixi = 1
>
>
>
> do đó theo lập luận trên nó sẽ maximize (Σi dixi)² / (Σi di²), s.t Σi di = 0, Σi dixi = 1
>
>
>
> ---
>
>
>
> Cuối cùng, để ý nếu 𝐝 thỏa Σi di = 0, Σi dixi = 1 thì (Σi dixi)² / (Σi di²) sẽ = 1/(Σi di²)
>
>
>
> Vậy nên maximize (Σi dixi)² / (Σi di²) s.t  Σi di = 0, Σi dixi = 1
>
>
>
> sẽ tương đương minimize (Σi di²) s.t  Σi di = 0, Σi dixi = 1 (chú ý ko được bỏ constraint)
>
>
>
> mà Σi di² nhỏ nhất ⇔ Var(W(𝐘)) nhỏ nhất  
>
>
>
> Như vậy 𝐝: di = (xi-x̄)/Sxx sẽ minimize (Σi di²), cũng là minimize Var(W(𝐘))
>
>
>
> Do đó W(𝐘) = Σi diYi với di = (xi-x̄)/Sxx, chính là Best Unbiased Linear Estimator
>
>
>
> Hay Σi (xi-x̄)Yi/Sxx = SxY/Sxx là Best Linear Unbiased Estimator của β 
>
>
>
> và Σi (xi-x̄)yi/Sxx = Sxy/Sxx là Best Linear Unbiased Estimate của β

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, lập luận chặt chẽ và giải thích rõ ràng từng bước từ việc thu hẹp không gian tối ưu cho đến phép đổi bài toán max sang min.
>
> **🟡 Minor issues**
>
> **1.** *"Vậy thì với 𝐝 = (d1,..dk) với di = K(xi-x̄)"*
>
> Lỗi gõ phím nhỏ (typo): số chiều ở đây là n phần tử 𝐝 = (d1,...,dn) thay vì k.
>
>
> **✓ Strengths**
> - Nắm rất vững logic tối ưu trên tập con: nếu nghiệm của bài toán trên tập lớn thuộc tập con thì nó cũng là nghiệm tối ưu trên tập con đó.
> - Hiểu rõ mối liên hệ nghịch đảo giữa việc cực đại hóa tỉ số 1/(Σ di²) và cực tiểu hóa phương sai Σ di² dưới ràng buộc.
> - Phân biệt chính xác giữa Estimator (ước lượng - biến ngẫu nhiên Y) và Estimate (giá trị ước lượng cụ thể - quan sát y).
>
> **💡 Deeper notes**
> - Điều kiện tồn tại K = 1/Sxx ngầm định rằng Sxx = Σ (xi - x̄)² > 0, nghĩa là các điểm dữ liệu xi không được hoàn toàn trùng nhau (không suy biến).

**🔗 See also:** [Theorem 11.3.3 Sampling Distributions of Estimators](#node-gytarq0)

<br>

<a id="node-be2name"></a>

###### Geometric Description of BLUE

<p align="center"><kbd><img src="assets/wjf86fkamz.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/00rzczae3115j.png" width="80%"></kbd></p>

> [!NOTE]
> Về mặt hình học, thì {di} định ra BLUE của β: Σi diYi như sau:
>
>
>
> Phải thỏa Σi di xi = 1 nên nó 𝐝 phải nằm trên plane này
>
>
>
> Phải thỏa Σi di = 0 nên nó phải nằm trên plane này luôn
>
>
>
> Nên nó phải là trên giao tuyến của hai plane.
>
>
>
> Và bài toán là tìm 𝐝 trên giao tuyến giúp minimize Σi di², mà cái này chính là bình phương norm vector 𝐝. Vậy nên 𝐝 chính là hình chiếu của 𝟎 lên giao tuyến này.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất chuẩn xác và súc tích, nắm bắt hoàn hảo bản chất hình học của bài toán tìm BLUE: giao tuyến của hai siêu phẳng và hình chiếu trực giao từ gốc tọa độ.
>
> **✓ Strengths**
> - Hiểu chính xác mỗi ràng buộc tuyến tính của ước lượng không chệch tương ứng với một mặt phẳng trong không gian.
> - Kết luận rất chuẩn xác rằng cực tiểu hóa tổng bình phương các tọa độ chính là tìm điểm gần gốc tọa độ nhất, tương đương hình chiếu trực giao của gốc tọa độ 0 lên đường giao tuyến.
>
> **💡 Deeper notes**
> - Hình học biểu diễn không gian 3 chiều với 2 mặt phẳng cắt nhau tại một đường thẳng (tương ứng trường hợp mẫu n = 3). Trong trường hợp tổng quát với mẫu cỡ n, không gian sẽ là n chiều và giao của hai siêu phẳng là một không gian afin (n-2) chiều.

<br>

<a id="node-akqu751"></a>

###### Optimal Design for Slope Estimator

<p align="center"><kbd><img src="assets/2cf9flekq5g.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là với optimal 𝐝, để có BLUE của β: Var(b_BLUE) = σ² Σi di² = σ²/Sxx thì  vì Sxx phụ thuộc 𝐱 nên experimenter đại khái là có thể chọn 𝐱 sao cho Sxx lớn nhất từ đó có b_BLUE có variance nhỏ nhất
>
>
>
> Lấy ví dụ xbi chỉ được chọn trong \[e, f\] thì đại khái là có thể chọn một nửa số xi = e và một nửa bằng f (giả sử n chẵn). Khi đó, có thể chứng minh rằng Sxx lúc này sẽ lớn nhất.
>
>
>
> Có điều, chỉ khi ta rất chắc chắn giả định của simple regression là đúng thì mới nên làm vậy: tức giả định Yi = α + βxi + εi với E\[εi\] = 0, Var(εi) σ² còn nếu không, giả sử E\[Yi|xi\] không phải là hàm tuyến tính theo xi (α + β xi) thì cách làm này sẽ không ổn

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **90/100** · ✓ Move on
>
> Ghi chú nắm rất tốt ý tưởng thiết kế thực nghiệm để tối thiểu hóa phương sai của ước lượng hệ số góc, cũng như hiểu rõ rủi ro của thiết kế hai điểm (two-point design). Chỉ có một vài sơ suất nhỏ về ký hiệu và diễn đạt.
>
> **🟡 Minor issues**
>
> **1.** *"Yi = αi + βxi + εi"*
>
> Trong mô hình hồi quy tuyến tính đơn, hệ số chặn là hằng số α chung cho toàn bộ mẫu, viết αi là nhầm lẫn ký hiệu khiến mỗi quan sát có một hệ số chặn riêng.
>
> **2.** *"cách làm này sẽ không chính xác"*
>
> Diễn đạt chưa thật sát với bản chất trong sách: khi chỉ đo tại hai điểm e và f, ta hoàn toàn không thể kiểm tra hoặc phát hiện tính phi tuyến (nonlinearity) của mô hình từ dữ liệu thu thập được.
>
>
> **✓ Strengths**
> - Hiểu chính xác cơ chế: chọn các giá trị x_i để tối đa hóa S_xx nhằm cực tiểu hóa Var(b).
> - Nắm đúng kết quả tối ưu trong khoảng [e, f] với n chẵn là chia đều nửa ở e và nửa ở f.
> - Nắm được lý do thực tế ít dùng thiết kế này: cần giả định mô hình tuyến tính đúng, nếu không sẽ không phát hiện được phi tuyến.
>
> **💡 Deeper notes**
> - Thiết kế hai điểm thực chất là trường hợp đặc biệt của D-optimal design trong lý thuyết quy hoạch thực nghiệm (optimal design theory).
> - Để vừa có phương sai ước lượng nhỏ vừa kiểm tra được tính tuyến tính (lack-of-fit test), trong thực tế người ta thường bổ sung thêm các điểm ở giữa (chẳng hạn tại tâm (e+f)/2).

<br>

<a id="node-8ao1cbi"></a>

###### Gauss-Markov Theorem and BLUE

<p align="center"><kbd><img src="assets/6kkxpt5n8aj.png" width="80%"></kbd></p>

> [!NOTE]
> Cuối cùng, với α, tương tự, ta cũng có thể chứng minh a = ȳ - bx̄ là BLUE của intercept α

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú chính xác và súc tích; ước lượng bình phương tối thiểu a = ȳ - bx̄ quả thực là ước lượng tuyến tính không chệch tốt nhất (BLUE) của hệ số chặn α theo định lý Gauss-Markov.
>
> **✓ Strengths**
> - Nắm đúng kết luận trọng tâm từ tài liệu tham khảo rằng ước lượng OLS cho hệ số chặn a là BLUE của α.
>
> **💡 Deeper notes**
> - Để chứng minh a là BLUE, ước lượng tuyến tính dạng ∑ d_i y_i cần thoả mãn hai điều kiện không chệch: ∑ d_i = 1 và ∑ d_i x_i = 0, sau đó cực tiểu hóa phương sai dưới các giả định của định lý Gauss-Markov (phương sai sai số không đổi và sai số không tương quan).

<br>

<a id="node-a17n579"></a>

###### Models and Distribution Assumptions

<p align="center"><kbd><img src="assets/2d3duq4fkn4.png" width="80%"></kbd></p>

> [!NOTE]
> Phần này đại ý là:
>
>
>
> Hai phần trước, 11.3.1 từ data {(xi, yi)} ta có được cái gọi là least square estimate (của α và β), cái này không dựa trên giả định gì (về phân phối xác suất của data), mà chỉ là bài toán tối ưu thuần túy, nên không có gì để nói - ví dụ như, ko thể nói về variance của estimator, vì không có estimator nào cả, và đây không phải là kết quả của một bài toán suy luận thống kê.
>
>
>
> Sau đó, 12.3.2, ta giả định rằng các giá trị quan sát được {(xi, yi)} là giá trị quan sát được của Yi = α + βxi + εi với E\[εi\] = 0, Var(εi) = σ² và Cov(εi, εj) = 0 với i ≠ j, cũng chính là giả định E\[Yi|xi\] = α + βxi và Var(Yi) = σ², chính là giả định hai moment đầu tiên của Yi. Và từ đó, ta có thể nói b = SxY/Sxx là estimator của β, Ȳ - bx̄ là estimator của α. Cũng như chứng minh rằng chúng là Best Unbiased Linear Estimator của β và α.
>
>
>
> (Chú ý, nếu không giả định gì về phân phối của Y, hay nói cách khác, như cách làm least square, ta không giả định {(xi, yi)} là giá trị quan sát của random variable Yi, hay Xi gì cả, thì lấy gì mà gọi là estimator, vì estimator thì phải là hàm số của random variable) Và không có estimator thì ko đánh giá variance hay kì vọng gì cả.
>
>
>
> Vậy thì nay, đại ý là, ta sẽ giả định thêm về phân phối của data chứ ko chỉ là hai moment.

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chuẩn xác bức tranh tổng thể về mặt tư duy thống kê: từ tối ưu hình học thuần túy không có mô hình xác suất, đến giả định 2 moment đầu tiên (BLUE), và lý do cần giả định phân phối đầy đủ để xây dựng khoảng tin cậy hay kiểm định.
>
> **🟡 Minor issues**
>
> **1.** *"Sau đó, 12.3.2"*
>
> Lỗi gõ nhầm số mục tham chiếu, trong giáo trình đây là mục 11.3.2 chứ không phải 12.3.2.
>
> **2.** *"Best Unbiased Linear Estimator"*
>
> Thuật ngữ chuẩn của từ viết tắt BLUE là 'Best Linear Unbiased Estimator' (ước lượng tuyến tính không chệch tốt nhất).
>
>
> **✓ Strengths**
> - Nắm rất vững bản chất: một ước lượng (estimator) phải là một biến ngẫu nhiên (hàm của dữ liệu mẫu ngẫu nhiên), nên nếu chỉ tối ưu thuần túy trên tập điểm cố định thì không thể bàn về kì vọng hay phương sai.
> - Hiểu rõ sự phân cấp giữa các tầng giả định: không giả định -> giả định 2 moment đầu (đủ để có BLUE) -> giả định toàn bộ phân phối (cần thiết để suy diễn, kiểm định và lập khoảng tin cậy chính xác).
>
> **💡 Deeper notes**
> - Dưới các giả định về 2 moment (định lý Gauss-Markov), ta chứng minh được tính tối ưu BLUE mà không cần biết phân phối cụ thể của sai số. Tuy nhiên, để tìm được phân phối chính xác của các thống kê kiểm định (như phân phối t của Student hay phân phối F) và khoảng tin cậy ở cỡ mẫu hữu hạn, ta bắt buộc phải giả định phân phối chuẩn cho sai số εi.

<br>

<a id="node-lur3wot"></a>

###### Conditional Normal Model

<p align="center"><kbd><img src="assets/nm7mmpnti3n.png" width="80%"></kbd></p>

> [!NOTE]
> Đây rồi, đây chính là lần đầu tiên mình chính thức được học về kiến thức làm nền tảng cho những thứ đã học trước đây bên Bishop, ISL: Conditional normal model
>
>
>
> Giả định của model này là như sau:
>
>
>
> x1,x2,...vẫn là hằng số cố định
>
>
>
> y1,y2,...là giá trị quan sát được của các random variable Y1,Y2,... độc lập
>
>
>
> Và Yi có phân phối xác suất: n(α + βxi, σ²)
>
>
>
> ---
>
>
>
> Mô hình này cũng có thể thể hiện theo cách khác:
>
>
>
> x1,x2,...vẫn là hằng số cố định
>
>
>
> y1,y2,...là giá trị quan sát được của các random variable Y1,Y2,..
>
>
>
> Và Yi = α + βxi + εi với εi độc lập có phân phối n(0, σ²)
>
>
>
> ---
>
>
>
> Và dĩ nhiên cũng dưới mô hình này, E\[Yi|xi\] = α + βxi
>
>
>
> Đây chính là mô hình phổ biến nhất, trong chương 3 Bishop, mà ta đã gặp trong linear regression
>
>
>
> ---
>
>
>
> Dĩ nhiên dễ hiểu đây là special case của mô hình trong 13.3.2: giả định Yi uncorrelate, có E\[Yi|xi\] = α + βxi, Var(Yi) = σ², trong đó ta chỉ giả định về dạng của hai moment đầu tiên. Còn ở đây dĩ nhiên ta cũng có giả định này, nhưng có thêm dạng chính xác của Yi: n(α + βxi, σ²). Và uncorrelate thay bằng independence, là gỉa định mạnh hợn.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú nắm rất chắc và chính xác bản chất của conditional normal model, bao gồm hai cách biểu diễn tương đương cũng như mối liên hệ chặt chẽ hơn so với mô hình tổng quát trước đó.
>
> **🟡 Minor issues**
>
> **1.** *"mô hình trong 13.3.2"*
>
> Lỗi gõ phím nhỏ: trong giáo trình là Section 11.3.2 chứ không phải 13.3.2.
>
>
> **✓ Strengths**
> - Hiểu đúng và nêu đủ hai cách biểu diễn của mô hình: phân phối trực tiếp của Y_i và thông qua sai số ngẫu nhiên epsilon_i iid.
> - Nắm rất chuẩn sự khác biệt cốt lõi so với phần trước: nâng từ không tương quan (uncorrelated) lên độc lập (independent), và từ việc chỉ biết 2 moment đầu tiên sang xác định rõ toàn bộ hàm phân phối chuẩn.
>
> **💡 Deeper notes**
> - Khi viết dạng $Y_i = \alpha + \beta x_i + \epsilon_i$, các $\epsilon_i$ cần nhấn mạnh tính cùng phân phối (identically distributed) ngoài tính độc lập (i.i.d.), nhằm đảm bảo tính đồng nhất phương sai (homoscedasticity) $\sigma^2$ xuyên suốt mọi $x_i$.

<br>

<a id="node-q4wudzl"></a>

###### Joint PDF for Linear Regression

<p align="center"><kbd><img src="assets/6702ditiqb5.png" width="80%"></kbd></p>

> [!NOTE]
> rất dễ hiểu, với giả định independent, ta có joint pdf của Yi = tích marginal pdf. Và ta sẽ dùng cái này để thực hiện các quy trình suy luận như tìm MLE của α, β, và σ²: Thấy gì không, đây chính xác là thứ mà ta làm trong Bishop: tìm MLE của 𝐰 của mô hình: giả định Ti \~ n(𝐰ᵀ𝐱i, 1/β)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú nắm rất chắc bản chất: nhận diện đúng tính độc lập dẫn đến việc nhân các hàm mật độ, đồng thời có liên hệ trực tiếp và chính xác với mô hình hồi quy tuyến tính trong sách PRML của Bishop.
>
> **✓ Strengths**
> - Hiểu đúng bản chất của hàm hợp xác suất (joint pdf) dưới giả thiết độc lập là tích các pdf thành phần.
> - Liên hệ rất tốt với kiến thức trong sách Bishop (PRML) về bài toán hồi quy tuyến tính với giả định nhiễu Gauss.
>
> **💡 Deeper notes**
> - Lưu ý về sự trùng lặp ký hiệu: trong sách Bishop, ký hiệu β thường được dùng để chỉ độ chính xác (precision, tức 1/σ²), trong khi ở tài liệu này β là hệ số hồi quy (slope). Tránh nhầm lẫn vai trò của ký hiệu β giữa hai ngữ cảnh.
> - Về mặt bản chất, các mật độ xác suất ở đây là mật độ có điều kiện theo biến đầu vào x (conditional pdf p(y|x, θ)), dù giáo trình dùng thuật ngữ 'marginal pdf' do đang xem các giá trị x là cố định.

<br>

<a id="node-efv27w1"></a>

###### Bivariate Normal Model

<p align="center"><kbd><img src="assets/nvkt4fr1ih.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/x2yrid49jd8.png" width="80%"></kbd></p>

> [!NOTE]
> rồi, có khi {xi} thật ra không phải các gía trị hằng số chọn sẵn, mà cũng là observed value của một đại lượng ngẫu nhiên nào đó. Khi đó ta sẽ phải phát triển mô hình trong đó: {(xi,yi)} là observed value của random variable (Xi, Yi)
>
>
>
> Vậy ở đây ta giả định: {(xi,yi)} là observed value của random vector (Xi, Yi) độc lập, có joint distribution là bivariate normal: bivariate normal (μx, μy, σ²x, σ²y, ρ), là distribution mình đã học trong chap4.
>
>
>
> Và joint pdf của (X1,Y1), (X2,Y2),.. cũng sẽ là tích các joint pdf

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác động lực chuyển sang mô hình phân phối chuẩn hai chiều (khi biến dự báo cũng là biến ngẫu nhiên) cùng các giả định cốt lõi về tính độc lập và hàm mật độ đồng thời.
>
> **✓ Strengths**
> - Nắm vững lý do cốt lõi: biến dự báo x_i trên thực tế thường là giá trị quan sát của biến ngẫu nhiên thay vì hằng số cố định chọn trước.
> - Tóm tắt đầy đủ các giả thiết quan trọng: các cặp (X_i, Y_i) độc lập, tuân theo phân phối chuẩn hai chiều cùng tham số và hàm mật độ đồng thời của mẫu là tích các hàm mật độ thành phần.
>
> **💡 Deeper notes**
> - Mặc dù các vector (X_i, Y_i) độc lập với nhau giữa các quan sát khác nhau (i != j), bản thân X_i và Y_i trong cùng một quan sát lại có tương quan với nhau thông qua hệ số tương quan rho.

<br>

<a id="node-3wizpa4"></a>

###### Bivariate Normal Regression Model

<p align="center"><kbd><img src="assets/1xg46xfncz5.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/k3ueom6qie.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, đoạn này đại ý là, dù là trong case này, ta phải coi xi là giá trị quan sát được của random variable Xi, nhưng bài toán chủ yếu vẫn là mong muốn dự đoán Y từ x. Vậy thì, như đã biết ở chương 4 rằng, nếu có X, Y \~ bivariate normal, thì marginal pdf của X, hay Y cũng là normal, và conditional pdf của Y|X=x cũng là normal, cụ thể là n(μy + ρ(σy/σx)(x-μx), ...)
>
>
>
> Do đó, nếu ta đã giả định (xi, yi) là giá trị quan sát được của (Xi,Yi) \~ bivariate normal thì DĨ NHIÊN POPULATION REGRESSION: E\[Y|X=x\] SẼ IMPLY (Ý LÀ TỰ NHIÊN SẼ PHẢI) là MỘT hàm tuyến tính theo x: E\[Y|X=x\] = ρ\[σy/σx\] x + \[μy - ρ(σy/σx)μx\], và ta không cần giả định này (vì nó là kết quả của giả định bivariate normal rồi)
>
>
>
> Và mô hình này cũng sẽ giống conditional normal ở chỗ: Var(Y|x) = không phụ thuộc x.
>
>
>
> ---
>
>
>
> Cuối cùng, đại ý là ngay cả khi ta dùng bivariate normal model, thì phần lớn ta sẽ vẫn chỉ dùng conditional distribution của (Y1,...Yn) dựa trên (X1=x1,X2=x2,....). Có nghĩa là, khi đó nó cũng chỉ y như mô hình conditional normal.
>
>
>
> Nói cách khác, một khi ta đã dựa trên giá trị cụ thể x1,x2,... thì việc nó là observed value của các biến ngẫu nhiên X1, ...Xn hay là fixed value ngay từ đầu không khác gì nhau. 
>
>
>
> Do đó, trong simple linear regression, TA KHÔNG DÙNG CÁI YẾU TỐ PHÂN PHỐI JOINT CỦA X,Y LÀ BIVARIATE NORMAL, TRỪ VIỆC DÙNG NÓ ĐỂ ĐỊNH NGHĨA RA CONDITIONAL DISTRIBUTION.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú nắm rất chắc và diễn giải chính xác bản chất của mô hình hồi quy tuyến tính dưới giả định phân phối chuẩn hai biến (bivariate normal).
>
> **✓ Strengths**
> - Hiểu đúng điểm mấu chốt: tính tuyến tính của E[Y|x] là hệ quả tất yếu suy ra từ giả định chuẩn hai biến chứ không cần phải giả định thêm như mô hình hồi quy trước đó.
> - Nắm chuẩn tính chất phân phối có điều kiện Y|X=x cũng có dạng chuẩn và phương sai có điều kiện Var(Y|x) độc lập với x (không đổi theo x).
>
> **💡 Deeper notes**
> - Phương sai có điều kiện cụ thể là Var(Y|x) = σ_Y^2 (1 - ρ^2), cho thấy mối tương quan ρ càng mạnh (|ρ| càng gần 1) thì độ bất định (phương sai) của Y khi đã biết x càng giảm.

<br>

<a id="node-c6564df"></a>

###### Estimation with Normal Errors

<p align="center"><kbd><img src="assets/dw7q6b2eosu.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/autcnqa56a5.png" width="80%"></kbd></p>

> [!NOTE]
> Conditional normal model:
>
>
>
> (x1,y1),... (xn,yn)
>
>
>
> x1,x2,...xn là các hằng cố định có sẵn.
>
>
>
> y1,y2,...yn là observed value của Y1, Y2,...Yn độc lập
>
>
>
> Yi \~ normal(α+βxi, σ²)
>
>
>
> ---
>
>
>
> x1,x2,...xn là các hằng cố định có sẵn.
>
>
>
> y1,y2,...yn là observed value của Y1, Y2,...Yn
>
>
>
> Yi = α + βxi + εi, với εi \~ normal(0, σ²), εi độc lập
>
>
>
> ---
>
>
>
> Tìm Maximum Likelhood estimator cho α, β, σ²:
>
>
>
> ---
>
>
>
> Y như trong trong Bishop: (t1,𝐱1), (t2,𝐱2)...
>
>
>
> t1, t2 ... là observed value của các random variable T1, T2,....Ti độc lập \~ normal(𝐰ᵀΦ(𝐱i), 1/β)
>
>
>
> cũng tương đương giả định: residual error εi \~ normal(0, 1/β)
>
>
>
> và đi tìm MLE của 𝐰, β
>
>
>
> ---
>
>
>
> Likehood = L(θ|𝐱) = f(𝐱|θ)
>
>
>
> L(α, β, σ²|𝐱, 𝐲) = f(y1,y2,...yn|α, β, σ²,𝐱)
>
>
>
> Vì tính độc lập: f(y1,y2,...yn|α, β, σ²,𝐱) = Πi f(yi|α, β, σ²,𝐱)
>
>
>
> Với Yi \~ n(α + βxi, σ²)
>
>
>
> thì pdf: f(yi|xi, α, β, σ²) = (1/√2πσ²) exp{-(yi-α - βxi)²/2σ²}
>
>
>
> ..= Πi f(yi|α, β, σ²,𝐱)
>
>
>
> = Πi (1/√2πσ²) exp{-(yi-α - βxi)²/2σ²}
>
>
>
> log Likelihood:
>
>
>
> log Πi (1/√2πσ²) exp{-(yi-α - βxi)²/2σ²}
>
>
>
> = Σi log (1/√2πσ²) exp{-(yi-α - βxi)²/2σ²}
>
>
>
> = Σi log (1/√2πσ²) + Σi log exp{-(yi-α - βxi)²/2σ²}
>
>
>
> = Σi log (2πσ²)^(-1/2) + Σi {-(yi-α - βxi)²/2σ²}
>
>
>
> = (-1/2) Σi log (2π) + (-1/2) Σi log(σ²) + (1/2σ²) Σi {-(yi - α - βxi)²}
>
>
>
> = - (n/2) log (2π) - n/2) log(σ²) - (1/2σ²) Σi (yi - α - βxi)²
>
>
>
> ---
>
>
>
> Như vậy bài toán:
>
>
>
> maximize\_α, β, σ² {- (n/2) log (2π) - n/2) log(σ²) - (1/2σ²) Σi (yi - α - βxi)²}
>
>
>
> equivalent:
>
>
>
> maximize\_α, β, σ² { -(n/2) log(σ²) - (1/2σ²) Σi (yi - α - βxi)²}
>
>
>
> fixed σ² fixed:
>
>
>
> maximize\_α, β { -(n/2) log(σ²) - (1/2σ²) Σi (yi - α - βxi)²}
>
>
>
> equivalent:
>
>
>
> maximize\_α, β {-Σi (yi - α - βxi)²}
>
>
>
> equivalent
>
>
>
> minimize\_α, β {Σi (yi - α - βxi)²}
>
>
>
> Gỉải theo β trước:
>
>
>
> minimize\_β {Σi (yi - α - βxi)²}
>
>
>
> d/dβ \[Σi (yi - α - βxi)²\]
>
>
>
> = Σi d/dβ \[(yi - α - βxi)²\]
>
>
>
> = Σi d/d(yi - α - βxi) \[(yi - α - βxi)²\] . d/dβ (yi - α - βxi)
>
>
>
> = Σi 2(yi - α - βxi) (-xi)
>
>
>
> = - Σi 2xi(yi - α - βxi)
>
>
>
> Điều kiện cần tối ưu bậc nhất: - Σi 2xi(yi - α - βxi) = 0
>
>
>
> ⇔ - Σi xi(yi - α - βxi) = 0
>
>
>
> ⇔ - (Σi xiyi - Σixiα - Σi βxi²) = 0
>
>
>
> ⇔ Σi xiyi - Σixiα - Σi βxi² = 0
>
>
>
> ⇔ Σi xiyi - Σixiα = Σi βxi²
>
>
>
> ⇔ (Σi xiyi - Σixiα)/Σi xi² = β
>
>
>
> ⇔ Σi xi(yi - α)/Σi xi² = β (1)
>
>
>
> ---
>
>
>
> Giải theo α:
>
>
>
> minimize\_α {Σi (yi - α - βxi)²}
>
>
>
> d/dα \[Σi (yi - α - βxi)²\]
>
>
>
> = Σi d/dα (yi - α - βxi)²
>
>
>
> = Σi d/d(yi - α - βxi) (yi - α - βxi)² . d/dα (yi - α - βxi)
>
>
>
> = 2 Σi (yi - α - βxi) (-1)
>
>
>
> = -2 Σi (yi - α - βxi)
>
>
>
> Điều kiện cần bậc nhất: -2 Σi (yi - α - βxi) = 0
>
>
>
> ⇔ Σi (yi - α - βxi) = 0
>
>
>
> ⇔ Σi yi - Σi α - Σiβxi = 0
>
>
>
> ⇔ (1/n) (Σi yi - βΣixi) = α
>
>
>
> ⇔ α = (Σi yi)/n - β(Σixi)/n
>
>
>
> ⇔ α = ȳ - βx̄
>
>
>
> Thay vào (1): Σi xi(yi - ȳ + βx̄)/Σi xi² = β
>
>
>
> (Σi xiyi - Σi xiȳ + Σi xiβx̄)/Σi xi² = β
>
>
>
> Σi xiyi - Σi xiȳ + Σi xiβx̄ = βΣi xi²
>
>
>
> Σi xiyi - ȳ Σixi + x̄ β Σixi = βΣi xi²
>
>
>
> Σi xiyi - ȳ Σixi = βΣi xi² - x̄ β Σixi
>
>
>
> Σi xiyi - ȳ Σixi = β(Σi xi² - x̄ Σixi)
>
>
>
> Σi (xiyi - ȳxi) = βΣi (xi² - x̄ xi)
>
>
>
> ---
>
>
>
> Xét Σi (xi² - x̄ xi) = Σi (xi² - 2x̄ xi + x̄ xi + x̄ ² - x̄ ²)
>
>
>
> = Σi (xi² - 2x̄ xi + x̄ ² + x̄ xi - x̄ ²)
>
>
>
> = Σi \[(xi - x̄ )² + x̄ (xi - x̄ )\]
>
>
>
> = Σi (xi - x̄ )² + Σi \[x̄ (xi - x̄ )\]
>
>
>
> = Σi (xi - x̄ )² + x̄ (Σi xi - Σi x̄ )
>
>
>
> = Σi (xi - x̄ )² = Sxx
>
>
>
> ---
>
>
>
> Xét Σi (xiyi - ȳxi) = Σi (xiyi - ȳxi + x̄ yi - x̄ yi + x̄ ȳ - x̄ ȳ)
>
>
>
> = Σi (xiyi - ȳxi - x̄ yi + x̄ ȳ + x̄ yi - x̄ ȳ)
>
>
>
> = Σi (xiyi - ȳxi - x̄ yi + x̄ ȳ) + Σi(x̄ yi - x̄ ȳ)
>
>
>
> = Σi (xi - x̄ )(yi - ȳ) + x̄ (Σiyi - Σi ȳ)
>
>
>
> = Σi (xi - x̄ )(yi - ȳ) = Sxy
>
>
>
> β\_ML = Sxy/Sxx = b
>
>
>
> α\_ML = ȳ - βML x̄ = a

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=dQ-blTqxLaM)

> [!TIP]
> 🤖 **AI Check** — 🟡 Minor issues — ✅ **90/100** · ✓ Move on
>
> Ghi chú rất xuất sắc khi tự chứng minh chi tiết nghiệm OLS/MLE cho α và β từ hàm log-likelihood thay vì chỉ chấp nhận kết quả sẵn có. Bạn chỉ cần hoàn thiện nốt bước tìm MLE cho tham số σ² như dự định ban đầu.
>
> **🟡 Minor issues**
>
> **1.** *"Tìm Maximum Likelhood estimator cho α, β, σ²:"*
>
> Ghi chú đặt mục tiêu tìm MLE cho cả α, β và σ², nhưng phần sau mới chỉ giải đến α và β mà chưa thực hiện tiếp bước tối ưu hóa hàm log-likelihood theo σ² để tìm σ̂².
>
>
> **✓ Strengths**
> - Biểu diễn chính xác hàm likelihood và log-likelihood cho mô hình hồi quy tuyến tính dưới giả định sai số chuẩn.
> - Liên hệ tốt giữa bài toán cực đại hóa likelihood (MLE) với cực tiểu hóa tổng bình phương phần dư (RSS) khi cố định σ².
> - Tự triển khai đạo hàm riêng và đại số rút gọn cho α và β rất chặt chẽ, biến đổi chuẩn xác đưa về dạng Sxy và Sxx.
>
> **💡 Deeper notes**
> - Để tìm nghiệm MLE của σ², bạn thay α̂ và β̂ vừa tìm được vào log-likelihood, lấy đạo hàm theo σ² (hoặc σ) và cho bằng 0 sẽ thu được công thức σ̂² = (1/n) RSS. Chú ý rằng đây là ước lượng chệch (biased), khác với ước lượng không chệch s² = RSS / (n - 2).

**🔗 See also:** [Two Steps of Regression Analysis](#node-7ilb1oo) · [Regression and Residual Sum of Squares](#node-71s1z11)

<br>

<a id="node-26ktgyo"></a>

###### Lemma 11.3.2 Covariance of Linear Combinations

<p align="center"><kbd><img src="assets/f33qm04tbcj.png" width="80%"></kbd></p>

> [!NOTE]
> Bổ đề này nói đại ý rằng: Nếu có Y1,...Yn uncorrelated với Var(Yi) = σ² và c1,...cn, d1,...dn là các constants. 
>
>
>
> Thì khi đó:
>
>
>
> Cov(Σi ci Yi, Σi di Yi) = (Σi cidi) σ²
>
>
>
> Chứng minh sau

> [!TIP]
> 🤖 **AI Check** — 🔴 Critical issues — ❌ **0/100** · ✗ Fix first
>
> Vui lòng nhập lời giải thích của bạn để được chấm điểm.

**🔗 See also:** [Độc lập trung bình phương sai](./53_sampling_from_the_normal_distribution.md#node-qx3kch2) · [Independence of Regression Estimators and S2](#node-0c21ixk)

<br>

<a id="node-zj557yy"></a>

###### Residuals and Bias in Variance

<p align="center"><kbd><img src="assets/kk4dyxx4n6e.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/izoxzuknf3h.png" width="80%"></kbd></p>

> [!NOTE]
> Quay lại sau: Đại ý là tính toán để chứng minh MLE của σ̂ ² = (1/n) Σi (yi - α̂ - β̂ xi)² là một biased estimator của σ², vì:
>
>
>
> E\[σ̂ ²\] = \[(n-2)/n\] σ²
>
>
>
> Nên từ đó người ta lấy S² = \[n/(n-2)\] σ̂ ² để tạo một unbiased estimator cho σ².
>
>
>
> Ý nghĩa của cái này là gì:
>
>
>
> Chính là giúp ta thấy trong bài toán machine learning (giả định Ti \~ normal(𝐰ᵀ𝐱i, 1/β) thì MLE của 1/β chính là một biased estimator của 1/β

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú tóm tắt rất chính xác kết quả suy dẫn từ tài liệu và liên hệ đúng với bài toán hồi quy trong Machine Learning (ước lượng hợp lý cực đại của phương sai là ước lượng chệch).
>
> **✓ Strengths**
> - Nắm bắt chính xác kết quả kỳ vọng E[σ̂²] = [(n-2)/n]σ² và công thức hiệu chỉnh không chệch S².
> - Liên hệ rất tốt giữa mô hình hồi quy tuyến tính cổ điển với cách ký hiệu tham số độ chính xác (precision) β trong Machine Learning (như trong giáo trình của Bishop).
>
> **💡 Deeper notes**
> - Trong bài toán ML tổng quát Ti ~ Normal(wᵀxi, 1/β) với w có d chiều, số bậc tự do bị mất bằng d (thay vì 2 như trong hồi quy đơn biến), khi đó E[1/β_ML] = [(n-d)/n](1/β).

**🔗 See also:** [Independence of Regression Estimators and S2](#node-0c21ixk) · [Regression and Residual Sum of Squares](#node-71s1z11)

<br>

<a id="node-gytarq0"></a>

###### Theorem 11.3.3 Sampling Distributions of Estimators

<p align="center"><kbd><img src="assets/axddywm7j15.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gq46anpxf0l.png" width="80%"></kbd></p>

> [!NOTE]
> Qua phần này bắt đầu nói về việc ta xem xét sampling distribution của các estimator này
>
>
>
> Ôn lại chút: Sampling distribution là sao? Đơn giản là distribution của các statistic - có bản chất là hàm của sample: W(𝐗), hay ở đây là W(𝐘), ví dụ β̂. là một linear estimator W(𝐘) = Σi di Yi (cụ thể hơn thì nó là best unbiased linear estimator (với bộ hệ số di khiến nó có phương sai nhỏ nhất). Thế thì người ta gọi distribution của biến ngẫu nhiên này là sampling distribution để phân biệt với population distribution. Và ta bàn về distribution của chúng là để bắt đầu nói về bài toán testing và interval estimation (hai bài toán suy luận thứ hai và 3 sau khi đã bàn về bài toán suy luận đầu tiên: point estimation)
>
>
>
> ---
>
>
>
> Nhắc lại tí xíu, bữa giờ ta đã làm gì:
>
>
>
> Đầu tiên là tác giả ném cho mình hai công thức estimate sau đây cho α và β (của mô hình simple linear regression giả định yi là gía trị quan sát được của Y1,...Yn \~ n(α + β xi, σ²) với Yi uncorrelate (và với normal thì cũng là independent).
>
>
>
> β̂ = Sxy/Sxx
>
>
>
> α̂ = ȳ - β̂ x̄
>
>
>
> với Sxx = Σi (xi - x̄)², Sxy = Σi (xi - x̄)(yi - ȳ)
>
>
>
> Sau đó, ông mới dẫn ta đi biện minh cho công thức này theo 3 kiểu: Nói cách khác, 3 cách để dẫn đến cùng một công thức trên:
>
>
>
> Thứ nhất: Nếu đặt ra bài toán khớp đường thẳng đơn thuần là bài toán tối ưu: minimize α, β SSE (=Σi (yi - α - βxi)²) thì ta sẽ ra kết quả trên. Và điều này có nghĩa là, kết quả trên hoàn toàn không cần dựa trên giả định nào về phân phối xác suất của dữ liệu quan sát được. Do đó, kết quả này, theo cách biện minh này, hoàn toàn không phải là kết quả của một bài toán suy luận thống kê.
>
>
>
> ---
>
>
>
> Thứ hai: Ông bắt đầu đặt ra bài toán suy luận thống kê (point estimation), với giả định sau đây: x1,x2,...là những giá trị cố định cho trước. y1,y2,...là giá trị quan sát được của các biến ngẫu nhiên Y1,Y2,...có E\[Yi\] = α + βxi và Var(Yi) = σ². Và Y1,Y2,...uncorrelate.
>
>
>
> Với giả định này, ta mới xét linear estimator W(𝐘) = Σi diYi và chỉ ra rằng, nếu áp cái hàm Sxy/Sxx lên 𝐘, ta sẽ có một linear estimator (của β) có tính chất: β̂ là Best Linear Unbiased Estimator - BLUE. Và tương tự, α̂ = Ȳ - β̂ x̄ cũng là BLUE của α.
>
>
>
> ---
>
>
>
> Cuối cùng: Ông dùng giả định đầy đủ: xi là giá trị cố định, yi là giá trị quan sát được của các biến ngẫu nhiên Y1,Y2...\~ n(α + βxi, σ²) uncorrelated (đồng nghĩa độc lập vì đây là normal). Và ta đi tìm point estimator của α và β theo các truyền thống: MLE. Và hóa ra β̂ và α̂ cũng là MLE của β và α. Còn MLE của σ² thì là cái này:
>
>
>
> σ̂ ² = (1/n) Σi (Yi - α̂ - β̂ xi)²
>
>
>
> Cái này thì ko như β̂, α̂. Không phải là unbiased estimator của σ².
>
>
>
> ---
>
>
>
> Theorem nói cả α̂, β̂ đều là biến ngẫu nhiên normal: Nói chung dùng Hệ quả 4.6.10 giải thích được hết.
>
>
>
> Với β̂. Đầu tiên hãy nhớ, trước khi nó là best unbiased linear estimator, thì nó là linear estimator trước đã: β̂ = Σi diYi, (và với di = (xi-x̄)/Sxx khiến ta có the best unbiased) Mà Yi \~ n(α + βxi, σ²) nên theo bổ đề 4.6.10 mình đã học bữa trước (có video), thì **tổng các linear function của các normal độc lập thì cũng là normal**: β̂ cũng là một normal:
>
>
>
> n(Σi \[di E(Yi)\], Σi di²σ²)
>
>
>
> = n(E\[Σi diYi\], σ² Σi di²)
>
>
>
> = n(E\[β̂\], σ²/Sxx)
>
>
>
> = n(β, σ²/Sxx) do đã chứng minh β̂ là unbiased linear estimator
>
>
>
> ---
>
>
>
>
>
> Với α̂: Ȳ - β̂ x̄
>
>
>
> = (1/n) Σi Yi - (Σi di Yi) x̄, với di = (xi-x̄)/Sxx
>
>
>
> = Σi (1/n)Yi - Σi diYix̄
>
>
>
> = Σi \[(1/n)Yi - diYix̄\]
>
>
>
> = Σi \[(1/n) - di x̄ \] Yi
>
>
>
> = Σi ci Yi với ci = (1/n) - di x̄
>
>
>
> Như vậy có thể thấy α̂ cũng là **tổng các linear function của các Yi là các normal độc lập**. Nên nó cũng là normal có:
>
>
>
> E\[α̂ \] = Σi ci E\[Yi\] = Σi ci (α + β xi) = Σi \[(1/n) - di x̄ \] (α + β xi)
>
>
>
> = Σi {\[(α/n) - \[(xi-x̄)/Sxx\] x̄ α + (β xi/n) - \[(xi-x̄)/Sxx\] x̄ β xi\]
>
>
>
> = Σi(α/n) - Σi \[(xi-x̄)/Sxx\] x̄ α + Σi(β xi/n) - Σi \[(xi-x̄)/Sxx\] x̄ β xi\]
>
>
>
> = Σi(α/n) - (x̄ α/ Sxx) Σi (xi-x̄) + (β/n) (Σi xi) - (β/Sxx) Σi \[(xi-x̄) x̄ xi\]
>
>
>
> = Σi(α/n) - 0 + (β/n) (Σi xi) - (β/Sxx) x̄ Σi \[(xi-x̄) xi\]
>
>
>
> = Σi(α/n) + (β/n) (Σi xi) - (β/Sxx) x̄ Σi \[(xi² - x̄xi) \]
>
>
>
> = Σi(α/n) + (β/n) (Σi xi) - (β/Sxx) x̄ Σi \[(xi² - 2x̄xi + x̄ ² + x̄xi - x̄ ²) \]
>
>
>
> = Σi(α/n) + (β/n) (Σi xi) - (β/Sxx) x̄ Σi \[(xi - x̄)² + x̄(xi - x̄ )\]
>
>
>
> = Σi(α/n) + (β/n) (Σi xi) - (β/Sxx) x̄ {Σi \[(xi - x̄)²\] + Σi x̄(xi - x̄ )}
>
>
>
> = Σi(α/n) + (β/n) (Σi xi) - (β/Sxx) x̄ {Σi \[(xi - x̄)²\] + x̄ Σi (xi - x̄ )}
>
>
>
> = Σi(α/n) + (β/n) (Σi xi) - (β/Sxx) x̄ Σi (xi - x̄)²
>
>
>
> = Σi(α/n) + (β/n) (Σi xi) - (β/Sxx) x̄ Sxx
>
>
>
> = Σi(α/n) + (β/n) (Σi xi) - βx̄
>
>
>
> = Σi(α/n) + βx̄ - βx̄
>
>
>
> = Σi(α/n)
>
>
>
> = α
>
>
>
> ---
>
>
>
>
>
> Var(α̂ ) = Σi ci ² Var(Yi)
>
>
>
> = Σi \[(1/n) - di x̄ \]² σ²
>
>
>
> = σ² Σi \[(1/n²) - 2di x̄/n + di² x̄ ²\]
>
>
>
> = σ² \[Σi (1/n²) - 2 (x̄/n) Σi di + Σi di² x̄ ²\]
>
>
>
> = σ² \[Σi (1/n²) - 2 (x̄/n) Σi \[(xi-x̄)/Sxx\] + x̄ ² Σi di² \]
>
>
>
> = σ² \[Σi (1/n²) - 2 (x̄/n) Σi \[(xi-x̄)\] /Sxx + x̄ ² /Sxx \]
>
>
>
> = σ² \[Σi (1/n²) - 2 (x̄/n) × 0 / Sxx + x̄ ² /Sxx \]
>
>
>
> = σ² \[(1/n) + x̄ ² /Sxx \]
>
>
>
> = σ² (Sxx + nx̄ ²) /nSxx
>
>
>
> = (σ²/nSxx) (Σi (xi - x̄)² + nx̄ ²)
>
>
>
> = (σ²/nSxx) (Σi (xi² - 2 xix̄ + x̄²) + nx̄ ²)
>
>
>
> = (σ²/nSxx) (Σi xi² - 2 x̄ Σi xi + n x̄² + nx̄ ²)
>
>
>
> = (σ²/nSxx) (Σi xi² - 2n x̄ ² + nx̄² + nx̄ ²)
>
>
>
> = σ²\[Σixi² /nSxx)
>
>
>
> ---
>
>
>
> Cuối cùng là Cov(α̂, β̂). Dùng bổ đề 11.3.2 (làm sau)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú xuất sắc, nắm rất vững bức tranh tổng thể từ 3 góc độ tiếp cận (Tối ưu hình học, BLUE/Gauss-Markov, MLE/Normal) và tự thực hiện biến đổi đại số chi tiết, chính xác cho kỳ vọng và phương sai của các ước lượng.
>
> **✓ Strengths**
> - Tổng kết cực kỳ rõ ràng và mạch lạc 3 góc độ tiếp cận mô hình hồi quy tuyến tính đơn (tối ưu hóa thuần túy SSE, định lý Gauss-Markov/BLUE, và mô hình xác suất Normal/MLE).
> - Tự triển khai đầy đủ các bước đại số để tính kỳ vọng và phương sai của alpha mũ thay vì chỉ chép lại kết quả cuối cùng từ sách.
> - Hiểu đúng bản chất của phân phối chọn mẫu (sampling distribution) là phân phối của thống kê mẫu đóng vai trò biến ngẫu nhiên.
>
> **💡 Deeper notes**
> - Khi xét tính độc lập từ tính không tương quan (uncorrelated), điều kiện cần là các biến ngẫu nhiên phải có phân phối chuẩn đồng thời (jointly normal); trong mô hình hồi quy, điều này được đảm bảo do giả định các sai số/quan sát độc lập ngay từ đầu.
> - Đoạn cuối bạn ghi chú sẽ dùng Bổ đề 11.3.2 để tính Cov(alpha mũ, beta mũ), lưu ý bổ đề này thường dựa trên công thức Cov(sum a_i Y_i, sum b_i Y_i) = sigma^2 sum a_i b_i khi các Y_i độc lập.

**🔗 See also:** [Application of Lemma 11.2.7](#node-q19qd3o)

<br>

<a id="node-0c21ixk"></a>

###### Independence of Regression Estimators and S2

<p align="center"><kbd><img src="assets/fyxcnrtygot.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0z740q5v1uf.png" width="80%"></kbd></p>

> [!NOTE]
> Phần chứng minh α̂, β̂ và S² (unbiased estimator của σ²) độc lập ta sẽ tìm hiểu sau nhưng đại ý là vầy:
>
>
>
> Theo định nghĩa 11.3.27 ε̂ i = Yi - (α̂ + β̂ xi) (gọi là Residual )
>
>
>
> ε̂ i = Yi - (α̂ + β̂ xi) = Yi - α̂ - β̂ xi
>
>
>
> với β̂ = Σj djYj và α̂ = Σj cjYj
>
>
>
> (dj = (xj-x̄)/Sxx, cj = (1/n) - dj x̄ ))
>
>
>
> ⇒ .. = Yi - α̂ - β̂ xi = Yi - Σj cjYj - Σj djYj xi
>
>
>
> = Yi - Σj cjYj - Σj djxiYj
>
>
>
> = Yi + Σj \[- cjYj - djxiYj\]
>
>
>
> Viết Yi = 0 × Y1 + 0 × Y2 + ....+ 1 × Yj + ... = Σj δijYi 
>
>
>
> = Σj δijYi + Σj \[- cjYj - djxiYj\]
>
>
>
> = Σj \[δijYj - cjYj - djxiYj\]
>
>
>
> = Σj \[(δij - cj - djxi)Yj\]
>
>
>
> Theo lemma 11.3.2, Cov(ε̂ i, α̂ ) = 0, Cov(ε̂ i, β̂ ) = 0, nên
>
>
>
> Theo bổ đề 5.3.3 thì:
>
>
>
> ε̂ i, α̂ , β̂ đều là tổng các linear function của các biến Yi là các normal độc lập.
>
>
>
> Đồng thời Cov(ε̂ i, α̂ ) = 0, Cov(ε̂ i, β̂ ) = 0
>
>
>
> Nên theo ý a của bổ đề, ε̂ i và α̂ độc lập và ε̂ i, β̂ độc lập.
>
>
>
> ---
>
>
>
> Và S² (còn nhớ, nó là unbiased estimator của σ² = \[n/(n-2)\] σ̂ ²
>
>
>
> = \[1/(n-2)\] (Σi ε̂ i²)
>
>
>
> do là hàm số của ε̂ i, nên S² sẽ độc lập với α̂ và β̂
>
>
>
> ---
>
>
>
> Cuối cùng là chứng minh (n-2)S²/σ² \~ χ²\_n-2: quay lại sau

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú rất tốt, bạn đã tự triển khai chi tiết các bước biến đổi đại số để đưa phần dư về dạng tổ hợp tuyến tính của các biến Y_j (điều mà giáo trình đã lược bớt), đồng thời nắm vững trực giác dẫn đến tính độc lập.
>
> **✓ Strengths**
> - Tự chứng minh chi tiết công thức biểu diễn ε̂_i theo hàm tuyến tính của Y_j mà sách giáo trình nhảy bước.
> - Nắm rõ logic cốt lõi: các thống kê là tổ hợp tuyến tính của các biến phân phối chuẩn độc lập, do đó hiệp phương sai bằng 0 suy ra tính độc lập.
> - Hiểu chính xác việc hàm số của các phần dư (cụ thể là S²) sẽ độc lập với α̂ và β̂.
>
> **💡 Deeper notes**
> - Để suy ra S² độc lập với (α̂, β̂), về mặt chặt chẽ cần vector phần dư (ε̂₁, ..., ε̂_n) độc lập đồng thời (jointly independent) với (α̂, β̂), chứ không chỉ là độc lập đôi một (pairwise independence). Tuy nhiên, vì đây là vector chuẩn nhiều chiều nên hiệp phương sai bằng 0 với mọi thành phần đảm bảo được tính độc lập đồng thời này.

**🔗 See also:** [Độc lập trung bình phương sai](./53_sampling_from_the_normal_distribution.md#node-qx3kch2) · [Lemma 11.3.2 Covariance of Linear Combinations](#node-26ktgyo) · [Residuals and Bias in Variance](#node-zj557yy)

<br>

<a id="node-tgodcuh"></a>

###### Inference on Linear Regression Parameters

<p align="center"><kbd><img src="assets/o5eftls78k.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý đoạn này là:
>
>
>
> Ta có kết quả ((n-2) ε̂ i²/σ² \~ χ²\_n-2 (mình tạm bỏ qua chứng minh, và để chứng minh cần dùng Cochran's Theorem)
>
>
>
> Rồi. Đồng thời cũng đã biết sampling distribution của α̂, β̂ là:
>
>
>
> α̂ \~ n(α, σ²\[(1/nSxx)Σi xi²\])
>
>
>
> β̂ \~ n(β, σ²/Sxx)
>
>
>
> Và nhớ lại **định nghĩa của phân phối student t** bậc tự do p là phân phối của biến ngẫu nhiên tạo bởi một **normal(0,1)** chia cho (**căn bậc 2** của một **chi-square chia bậc tự do p của nó**) và bậc tự do của student t là bậc tự do của chi-square. Và biến normal và chi-square phải **độc lập**
>
>
>
> Nên ở đây ta có:
>
>
>
> Do α̂ \~ n(α, σ²\[(1/nSxx)Σi xi²\])
>
>
>
> ⇒ (α̂ - α)/σ√(Σixi²/nSxx) \~ n(0,1) theo location scale family
>
>
>
> ((n-2)S²/σ² \~ χ²\_n-2 ⇒ √S²/σ² (= S/σ) chính là căn bậc hai của một χ²\_n-2 chia bậc tự do n-2 của nó
>
>
>
> Vậy (α̂ - α)/σ√(Σixi²/nSxx) / S/σ \~ t_n-2
>
>
>
> ⇔ (α̂ - α) / S√(Σixi²/nSxx) \~ t_n-2
>
>
>
> ---
>
>
>
> Tương tự:
>
>
>
> β̂ \~ n(β, σ²/Sxx)
>
>
>
> ⇒ (β̂ - β)/ (σ/√Sxx) \~ n(0,1)
>
>
>
> ((n-2)S²/σ² \~ χ²\_n-2 nên √S²/σ² = S/σ là căn bậc hai của một χ²\_n-2 chia bậc tự do của nó
>
>
>
> ⇒ (β̂ - β)/ (σ/√Sxx) / (S/σ) \~ t_n-2
>
>
>
> ⇔ (β̂ - β) / (S/√Sxx) \~ t_n-2
>
>
>
> ---
>
>
>
> Và ta sẽ dùng sampling distribution t_n-2 này để suy luận về α và β (tức là nói đến hai bài toán suy luận test và interval estimation, còn point estimation thì đã là α̂ và β̂ rồi)
>
>
>
> ---
>
>
>
> Ông nói thêm, joint distribution của hai cái biến t_n-2 ở trên gọi là bivariate Student's t. Có thể dùng để suy luận đồng thời cả α và β tuy nhiên ở đây ta sẽ suy luận từng cái.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, hiểu rõ bản chất định nghĩa phân phối Student's t và tự diễn giải từng bước triệt tiêu độ lệch chuẩn σ để ra công thức chuẩn mực trong sách.
>
> **✓ Strengths**
> - Hiểu chính xác và áp dụng đúng định nghĩa của phân phối Student's t từ biến chuẩn hóa N(0,1) và biến Chi-bình phương.
> - Tự triển khai đầy đủ các bước đại số biến đổi tỉ số để triệt tiêu tham số nhiễu σ thay vì chỉ chép lại công thức cuối.
> - Nêu rõ điều kiện quan trọng về tính độc lập giữa tử số (chuẩn tắc) và mẫu số (chi-square).
> - Nắm bắt chính xác vai trò của phân phối t trong suy luận thống kê (khoảng tin cậy và kiểm định) cũng như khái niệm bivariate Student's t distribution.
>
> **💡 Deeper notes**
> - Tính độc lập giữa ước lượng hệ số (α̂, β̂) và phương sai mẫu S² đến từ Định lý 11.3.3 (suy rộng từ Định lý Cochran trong mô hình hồi quy tuyến tính).

<br>

<a id="node-0czbau8"></a>

###### Section 11.3 Simple Linear Regression

<p align="center"><kbd><img src="assets/ji04haxl3dr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/vzwhnx8md1.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là ta thường quan tâm đến suy luận về β hơn là α.
>
>
>
> Vì E\[Y|x\] = α + βx nên α chỉ là E\[Y|x=0\], mà cái này thì tùy bài toán, có thể ta có hoặc không quan tâm đến.
>
>
>
> Còn β là độ dốc của hàm population regression E\[Y|x\] (rate of change, đạo hàm), nó sẽ giúp biết được khi x thay đổi 1 đơn vị thì E\[Y|x\] thay đổi thế nào. Do đó ta đặc biệt quan tâm β. Và cũng đặc biệt muốn suy luận (bài toán testing) rằng β có bằng 0 hay không.
>
>
>
> Nếu β = 0, đồng nghĩa E\[Y|x\] = α, cũng chính là Y \~ n(α, σ²), population regression function không còn phụ thuộc x nữa. Và như đã nói, ta **muốn biết** điều này có đúng không.
>
>
>
> ---
>
>
>
> Như vậy, xét bài toán kiểm định cho hypothesis: H0: β = 0 vs H1: β ≠ 0. Ta xây dựng phép kiểm định level α như sau:
>
>
>
> Đại khái là với 2-sided test, H0: θ = θ0, còn nhớ cái rule sẽ là: reject H0 khi T(𝐱) quá nhỏ hoặc quá lớn hơn một mốc nào đó: T(𝐱) ≤ mốc nào đó, hoặc T(𝐱) ≥ mốc nào đó. Và đại khái là để cho tiện, ta sẽ thể hiện bởi: |T(𝐱)| ≥ k. Dĩ nhiên cần tìm k.
>
>
>
> Nên hiểu: Theo LRT method để derive một test rule, ta sẽ ra kết quả là: Reject H0 khi |(X̄ - θ0) / √(S²/n)| &gt; k. Và với việc (X̄ - θ0) / √(S²/n) là biến t_n-1, ta sẽ chọn k = t_n-1,α/2 để có level α test.
>
>
>
> Ở đây cũng y chang vậy, LRT test sẽ là: Reject H0 khi |(β̂ - β) / (S/√Sxx)| &gt; k
>
>
>
> Và như phần trước đã biết (β̂ - β) / (S/√Sxx) \~ t_n-2
>
>
>
> nên ta sẽ chọn k để có level alpha test: t_n-2, α/2
>
>
>
> Nhiệm vụ là tìm k để có level alpha test:
>
>
>
> ⇔ sup\_Θ0 P\_θ(reject H0) ≤ α
>
>
>
> ⇔ sup\_β∈{β0=0} P\_β(|(β̂ - β) / (S/√Sxx)| &gt; k) ≤ α
>
>
>
> ⇔ P\_β0(|(β̂ - β0) / (S/√Sxx)| &gt; k) ≤ α
>
>
>
> ⇔ P\_β0(|β̂ / (S/√Sxx)| &gt; k) ≤ α
>
>
>
> ⇔ P(|T_n-2| &gt; k) ≤ α
>
>
>
> ⇔ P(T_n-2 &lt; -k ∪ T_n-2 &gt; k) ≤ α
>
>
>
> ⇔ P(T_n-2 &lt; -k) + P(T_n-2 &gt; k) ≤ α
>
>
>
> ⇔ 2P(T_n-2 &gt; k) ≤ α
>
>
>
> ⇔ P(T_n-2 &gt; k) ≤ α/2
>
>
>
> ⇒ k = t_n-2,α/2
>
>
>
> Nên cái level α test để reject H0: β = 0 là: |β̂ / (S/√Sxx)| &gt; t_n-2,α/2
>
>
>
> Bên cạnh đó:
>
>
>
> Với β̂ / (S/√Sxx) \~ t_n-2 thì \[β̂ / (S/√Sxx)\]² \~ F1,n-2
>
>
>
> nên ta cũng có thể chọn k theo F distribution:
>
>
>
> P\_β0(|β̂ / (S/√Sxx)| &gt; k) ≤ α
>
>
>
> do |β̂ / (S/√Sxx)| &gt; k ⇔ \[β̂ / (S/√Sxx)\]² &gt; k²
>
>
>
> ⇔ P\_β0(\[β̂ / (S/√Sxx)\]² &gt; k²) ≤ α
>
>
>
> ⇔ P\_β0(F_1,n-2 &gt; k²) ≤ α
>
>
>
> ⇒ k² = F_1,n-2,α
>
>
>
> Nên ta có thể dùng test rule sau: Reject H0 khi \[β̂ / (S/√Sxx)\]² &gt; F_1,n-2,α

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, không chỉ tóm tắt đúng ý nghĩa thực tế của việc kiểm định tham số beta so với alpha mà còn tự suy diễn chi tiết và chặt chẽ quy tắc bác bỏ H0 cho cả hai dạng thống kê t và F.
>
> **✓ Strengths**
> - Giải thích trực quan và chính xác ý nghĩa thực tế của việc kiểm định beta = 0 so với việc ước lượng intercept alpha.
> - Tự triển khai và chứng minh chi tiết các bước tìm giá trị tới hạn k từ định nghĩa mức ý nghĩa (size/level) của kiểm định hai phía đối xứng.
> - Nắm vững mối liên hệ giữa phân phối Student và phân phối Fisher (T^2 ~ F_1,df) để chỉ ra tính tương đương giữa kiểm định t và kiểm định F.
>
> **💡 Deeper notes**
> - Ký hiệu alpha bị trùng lặp giữa hệ số chặn (intercept) của hồi quy tuyến tính và mức ý nghĩa kiểm định (significance level). Khi viết công thức tính xác suất lỗi loại I, nên ký hiệu phân biệt (ví dụ alpha_level hoặc alpha_0) để tránh nhầm lẫn.
> - Trong không gian tham số H0: beta = 0, H0 là giả thuyết phức (composite hypothesis) do còn chứa các tham số phụ (nuisance parameters) là alpha (intercept) và sigma^2; tuy nhiên do thống kê kiểm định là một pivotal quantity dưới H0 nên xác suất không phụ thuộc vào các tham số này.

**🔗 See also:** [Phân phối F và Đối xứng Cầu](./53_sampling_from_the_normal_distribution.md#node-hd9jnpj) · [Tính chất phân phối F và t](./53_sampling_from_the_normal_distribution.md#node-85e946b) · [Testing Linear Combinations of Means](./111_2_introduction_one_way_anova.md#node-gjyj05b)

<br>

<a id="node-71s1z11"></a>

###### Regression and Residual Sum of Squares

<p align="center"><kbd><img src="assets/dii0sy1jhxk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/6dfzvyig6qt.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/90ga055x8a.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/nrrfx8sm3.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/dzvlp95324q.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp nối note trước, ta đã có level α test để test H0: β = 0 vs H1: β ≠ 0
>
>
>
> Reject H0 khi |β̂ / (S/√Sxx)| &gt; t_n-2,α/2 (1)
>
>
>
> hay cũng là
>
>
>
> \[β̂ / (S/√Sxx)\]² &gt; F_1,n-2,α (2)
>
>
>
> Và cái này có nghĩa là, để có phép kiểm định có xác suất mắc lỗi loại I cao nhất là 5%, thì ta sẽ reject H0 khi \[β̂ / (S/√Sxx)\]² &gt; F_1,n-2,0.05
>
>
>
> ---
>
>
>
> Thế thì xét β̂ / (S/√Sxx)
>
>
>
> với β̂ = Sxy / Sxx. Còn nhớ, đây là MLE, cũng là BLUE của β.
>
>
>
> và S² = \[1/(n-2)\] Σi ε̂\_i², cũng còn nhớ, đây là unbiased estimator của σ²
>
>
>
> và Σi ε̂\_i², còn nhớ, cũng là Residual Sum of Square: RSS
>
>
>
> ⇒ S² = RSS / (n-2)
>
>
>
> ⇒ \[β̂ / (S/√Sxx)\]² = \[(Sxy)² / (Sxx)²\] / {\[RSS / (n-2)\] / Sxx}
>
>
>
> = \[(Sxy)² / (Sxx)\] / \[RSS / (n-2)\]
>
>
>
> ---
>
>
>
> Vậy thì cái tử số (Sxy)² / (Sxx), tí nữa ta sẽ chứng minh, nó chính là Σi (ŷi - ȳ)², được đặt tên là Regression Sum of Square: RegSS. Và ta sẽ hiểu vì sao có cái cái tên này cũng như ý nghĩa của nó sau.
>
>
>
> Còn ở đây, chỉ cần biết: cái test statistic \[β̂ / (S/√Sxx)\]² trong test rule (2), (mà ta cũng đã biết nó có phân phối F_1,n-2 đó, nên ta cũng gọi nó là F-test statistic) sẽ bằng RegSS/\[RSS/(n-2)\].
>
>
>
> Mà hay hơn nữa, RegSS, thật ra là RegSS/1
>
>
>
> nên cái F-test statistic cũng chính là (RegSS/1) / (RSS/(n-2))
>
>
>
> Và việc ta so sánh F-test statistic với ngưỡng F_1,n-2,α để reject H0 thật ra có ý nghĩa như sau sau khi thể hiện lên bản ANOVA:
>
>
>
> Nói ngắn gọn là:
>
>
>
> nếu RegSS/1 (cũng là MS(Reg), Mean Square Regression) lớn hơn nhiều lần RSS/(n-2) (cũng là MSResid, Mean Square Residual) để F-statistic &gt; threshold thì khi đó có nghĩa là lượng biến động trong data mà ta giải thích được bằng regression line (chính là RegSS, Σi (ŷi - ȳ)² mà ta sẽ chứng minh nó là (Sxy)² / (Sxx)) lớn gấp nhiều lần lượng biến động trong data mà ta còn tồn đọng (RSS/(n-2)). Khi đó, có nghĩa là đại khái là ta có thể tin rằng β khác 0.
>
>
>
> Và lấy ví dụ 11.3.4, tính toán F statistic cho thấy = 50.23, như trên vừa nói, có nghĩa là lượng biến động (trên mỗi bậc tự do) có thể giải thích bởi regression line lớn gấp 50 lần lượng biến động tồn đọng (trên mỗi bậc tự do), và cũng là F statistic sẽ vượt xa các ngưỡng cần thiết để có level α test với α rất nhỏ. Do do, cả theo F statistic test và cả theo ý nghĩa, ta sẽ phải bác giả thiết β = 0, cũng là công nhận rằng tồn tại quan hệ tuyến tính giữa E\[Y|x\] và x.
>
>
>
> ---
>
>
>
> Cuối cùng, đại khái là, tác giả nói về một điểm tương đồng nữa với ANOVA (nội dung hai phần mà mình tạm bỏ qua), nhưng đại ý là:
>
>
>
> Total Sum of Squares: Σi (yi - ȳ)²
>
>
>
> sẽ bằng
>
>
>
> Regression Sum of Squares: Σi (ŷi - ȳ)², và tí nữa ta sẽ chứng minh nó chính là (Sxy)² / Sxx
>
>
>
> cộng với
>
>
>
> Residual Sum of Squres: Σi (ŷi - yi)²
>
>
>
> Trong đó RegSS: đo sự biến động của giá trị dự đoán ŷi so với grand mean ȳ.
>
>
>
> và RSS đo sự biến động của dự đoán so với observed value
>
>
>
> ---
>
>
>
> Và vì RSS = TSS - RegSS, mà RSS, như vừa nói: đo sự biến động của dự đoán so với observed value, nên nó mang ý nghĩa là lượng biến động trong data còn tồn đọng mà không thể giải thích bởi regression line.
>
>
>
> Và như vậy TSS - RSS sẽ dĩ nhiên mang ý nghĩa là lượng biến động trong data ĐÃ GIẢI QUYẾT ĐƯỢC, ĐÃ GIẢI THÍCH ĐƯỢC bởi regression line.
>
>
>
> Từ đó, người ta dùng statistic sau: r² = RegSS / TSS, mang ý nghĩa: tỉ lệ giữa mức biến động đã giải thích được so với mức biến động tổng cộng. Và dễ thấy r² càng lớn thì có nghĩa là regression line càng tốt.

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **98/100** · ✓ Move on
>
> Ghi chú rất xuất sắc, nắm bắt trọn vẹn và chuẩn xác mối liên hệ giữa t-test, F-test trong bảng ANOVA hồi quy, ý nghĩa hình học/thống kê của phân tích phương sai (TSS = RegSS + RSS) và bản chất của hệ số xác định r².
>
> **✓ Strengths**
> - Hiểu rất rõ và tự biến đổi tường minh mối liên hệ giữa t-statistic bình phương và F-statistic trong phân tích hồi quy đơn biến.
> - Nắm bắt chính xác bản chất của F-statistic là tỉ số giữa biến động giải thích được trên mỗi bậc tự do (MS(Reg)) và biến động sai số trên mỗi bậc tự do (MS(Resid)).
> - Giải thích chuẩn xác ý nghĩa của đẳng thức phân rã tổng bình phương sai lệch (TSS = RegSS + RSS) cũng như vai trò của hệ số xác định r².
>
> **💡 Deeper notes**
> - Đẳng thức phân rã tổng bình phương TSS = RegSS + RSS chỉ giữ được khi mô hình có hệ số chặn (intercept α̂), bởi vì hệ số chặn đảm bảo điều kiện trực giao (cross-term biến mất: Σ (ŷi - ȳ)(yi - ŷi) = 0).
> - Trong hồi quy tuyến tính đơn, r² trùng với bình phương hệ số tương quan mẫu của Pearson giữa x và y: r² = Sxy² / (Sxx * Syy).

**🔗 See also:** [Estimation with Normal Errors](#node-c6564df) · [Residuals and Bias in Variance](#node-zj557yy)

<br>

<a id="node-ph4z8v7"></a>

###### Inference for Slope Parameter Beta

<p align="center"><kbd><img src="assets/iyao39u4uzq.png" width="80%"></kbd></p>

> [!NOTE]
> Kết qủa (β̂ - β) / (S/√Sxx) \~ t_n-2 cũng có thể dùng để xây dựng 100(1-α)% confidence interval cho β 11.3.37. Là sao?
>
>
>
> Ôn lại thế nào là một 1-α confidence interval / set estimation
>
>
>
> Đó là C(𝐗) sao cho inf\_θ∈Θ P\_θ(C(𝐗) chứa θ) ≥ 1-α, ví dụ α = 0.05 thì đây sẽ là set có xác suất chứa θ không bao giờ nhỏ hơn 95%
>
>
>
> Vậy để có 1-α confidence interval cho β ta sẽ cần L(𝐘), U(𝐘) sao cho:
>
>
>
> inf\_β P\_β(L(𝐘) ≤ β ≤ U(𝐘)) ≥ 1-α
>
>
>
> ---
>
>
>
> Ôn nhanh lí thuyết:
>
>
>
> Giả sử ta có một có test rule sao cho với bất kì θ0 nào, khi xét bài toán kiểm định
>
>
>
> H0: θ = θ0 vs H1: θ ≠ θ0, thì test rule này đều luôn là một level α test.
>
>
>
> level α test
>
>
>
> test?
>
>
>
> H0: θ ∈ Θ0 vs H1: θ ∈ Θ0c (Θ0 U Θ0c)
>
>
>
> f(𝐱): { W(𝐱)
>
> W(𝐗) ≤ c → H0 ngược lại → H1
>
>
>
> λ(𝐱) = sup\_Θ0 L(θ|𝐱) / sup\_Θ L(θ|𝐱)
>
>
>
> λ(𝐱) ≤ c → Reject H0
>
> }
>
>
>
> Rejection region: ℛ = {𝐱: reject H0}
>
>
>
> Acceptance region: 𝒜 = {𝐱: not reject H0}
>
>
>
> Level α test
>
>
>
> Type I error: Reject H0 (𝐗 ∈ ℛ) khi θ ∈ Θ0
>
>
>
> P\_θ(𝐗 ∈ R) khi θ∈Θ0
>
>
>
> sup\_θ∈Θ0 P\_θ(𝐗 ∈ R) ≤ α (vd 0.05)
>
>
>
> khi level α test
>
>
>
> H0: θ = 1 vs H1: θ khác 1: P\_θ0(𝐗 ∈ R(1)) ≤ α | 𝐱=𝐱1: reject H0, 𝐱=𝐱2: accept H0
>
> H0: θ = 2 vs H1: θ khác 2: P\_θ0(𝐗 ∈ R(2)) ≤ α | 𝐱=𝐱1: accept H0, 𝐱=𝐱2: accept H0
>
> H0: θ = 3 vs H1: θ khác 3: P\_θ0(𝐗 ∈ R(3)) ≤ α | 𝐱=𝐱1: accept H0, 𝐱=𝐱2: reject H0
>
> ..
>
> H0: θ = θ0 vs H1: θ khác θ0: P\_θ0(𝐗 ∈ R(θ0)) ≤ α
>
>
>
> ⇔ 1 - P\_θ0(𝐗 ∈ R(θ0)) ≥ 1 - α
>
>
>
> ⇔ P\_θ0(𝐗 ∈ A(θ0)) ≥ 1 - α
>
>
>
> A(θ0) = {𝐱: accept H0: θ=θ0}
>
>
>
> A(1) = {𝐱: accept θ0=1}
>
> A(2) = {𝐱: accept θ0=2}
>
> A(3) = {𝐱: accept θ0=3}
>
>
>
> C(𝐱) = {θ0: 𝐱 ∈ A(θ0)}
>
>
>
> C(𝐱1) = {2,3}
>
>
>
> C(𝐱2) = {1,2}
>
>
>
> 2 ∈ C(𝐱2) ⇔ 𝐱2 ∈ A(2)
>
>
>
> 1 ∈ C(𝐱2) ⇔ 𝐱2 ∈ A(1)
>
>
>
> θ0 ∈ C(𝐱) ⇔ 𝐱 ∈ A(θ0)
>
>
>
> θ0 ∈ C(𝐗) ⇔ 𝐗 ∈ A(θ0)
>
>
>
> P\_θ0(𝐗 ∈ A(θ0)) = P\_θ0(C(𝐗) chứa θ0) ≥ 1-α với mọi θ0
>
>
>
> Với mọi θ, P\_θ(C(𝐗) chứa θ) ≥ 1-α
>
>
>
> C(𝐗) là một 1-α confidence interval.
>
>
>
> ---
>
>
>
> Quay lại đây, xét bài toán testing H0: β = β0 vs not H0, thì phép thử:
>
>
>
> Reject H0 khi |(β̂ - β0) / (S/√Sxx)| ≥ t_n-2,α/2
>
>
>
> Với mọi β0, sup\_β∈{β0} P\_β(𝐘 ∈ ℛ(β0)) = P\_β0(𝐘 ∈ ℛ(β0))
>
>
>
> = P\_β0(|(β̂ - β0) / (S/√Sxx)| ≥ t_n-2,α/2)
>
>
>
> = P\_β0(|T_n-2| ≥ t_n-2,α/2)
>
>
>
> = P\_β0(T_n-2 ≤ -t_n-2,α/2 or T_n-2 ≥ t_n-2,α/2)
>
>
>
> = P\_β0(T_n-2 ≤ -t_n-2,α/2) + P(T_n-2 ≥ t_n-2,α/2)
>
>
>
> = α/2 + α/2 = α
>
>
>
> Vậy sup\_β∈β0 P\_β(𝐘 ∈ ℛ(β0)) = P\_β0(𝐘 ∈ ℛ(β0)) = α với mọi β0
>
>
>
> nên đây là size α test với mọi bài toán kiểm định H0: β = β0
>
>
>
> ⇒ ∀β0 P\_β0(𝐘 ∈ 𝒜(β0)) = 1-α
>
>
>
> Đặt C(𝐲) = {β0: 𝐲 ∈ 𝒜(β0)} thì β0 ∈ C(𝐘) ⇔ 𝐲 ∈ 𝒜(β0)
>
>
>
> Nên P\_β0(β0 ∈ C(𝐘)) = P\_β0(𝐘 ∈ 𝒜(β0)), và = 1-α, và điều này đúng với mọi β0
>
>
>
> nên P\_β(β ∈ C(𝐘)) = 1-α
>
>
>
> Vậy C(𝐘) với C(𝐲) define như trên là 1-α interval estimation.
>
>
>
> Giờ ta viết cụ thể C(𝐲): như đã nói, là tập các β0 sao cho 𝐲 ∈ 𝒜(β0)
>
>
>
> ℛ(β0) = {𝐲: |(β̂(𝐲) - β0) / (S(𝐲)/√Sxx)| ≥ t_n-2,α/2}
>
>
>
> 𝒜(β0) = {𝐲: |(β̂(𝐲) - β0) / (S(𝐲)/√Sxx)| ≤ t_n-2,α/2}
>
>
>
> 𝒜(β0) = {𝐲: |(β̂(𝐲) - β0) / (S(𝐲)/√Sxx)| ≤ t_n-2,α/2}
>
>
>
> ⇒ C(𝐲) = {β0: |(β̂ (𝐲)- β0) / (S(𝐲)/√Sxx)| ≤ t_n-2,α/2}
>
>
>
> = {β0: -t_n-2,α/2 ≤ (β̂ (𝐲)- β0) / (S(𝐲)/√Sxx) ≤ t_n-2,α/2}
>
>
>
> = {β0: -t_n-2,α/2 × (S(𝐲)/√Sxx) ≤ β̂ (𝐲) - β0 ≤ t_n-2,α/2 × (S(𝐲)/√Sxx)}
>
>
>
> = {β0: t_n-2,α/2 × (S(𝐲)/√Sxx) + β̂ (𝐲) ≥ β0 ≥ β̂ (𝐲) - t_n-2,α/2 × (S(𝐲)/√Sxx)}
>
>
>
> = {β0: β̂ (𝐲) - t_n-2,α/2 × (S(𝐲)/√Sxx) ≤ β0 ≤ β̂ (𝐲) + t_n-2,α/2 × (S(𝐲)/√Sxx)}
>
>
>
> Và như vậy C(𝐘):
>
>
>
> \[β̂ (𝐘) - t_n-2,α/2 × (S(𝐘)/√Sxx), β̂ (𝐘) + t_n-2,α/2 × (S(𝐘)/√Sxx)\]
>
>
>
> là 100(1-α)% confidence interval cho β.

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=K8f2yncHnxg)

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **100/100** · ✓ Move on
>
> Ghi chú xuất sắc! Bạn đã giải thích bản chất mối liên hệ giữa kiểm định giả thuyết và khoảng tin cậy thông qua phương pháp đảo ngược miền chấp nhận (test inversion) một cách cực kỳ chi tiết, chuẩn xác và mạch lạc.
>
> **✓ Strengths**
> - Nắm vững và diễn đạt chính xác nguyên lý đối ngẫu giữa kiểm định giả thuyết mức alpha và khoảng tin cậy 1 - alpha (test inversion theorem).
> - Thực hiện đầy đủ các bước đại số từ bất đẳng thức của miền chấp nhận để suy ra công thức khoảng tin cậy của tham số độ dốc beta.
>
> **💡 Deeper notes**
> - Vì thống kê T tuân theo phân phối liên tục (Student's t), việc lấy dấu bất đẳng thức ngặt (<, >) hay không ngặt (≤, ≥) ở biên không làm thay đổi độ đo xác suất cũng như độ tin cậy của khoảng.

**🔗 See also:** [Liên hệ Kiểm định - Tin cậy](./92_methods_of_finding_interval_estimators.md#node-v7ov102)

<br>

