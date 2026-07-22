# Lec 14: Mean
value Theorem

📊 **Progress:** `24` Notes | `24` Screenshots

---
<a id="node-zkuth7s"></a>

## Lec 14: Mean
value Theorem

<br>

<a id="node-mkrkyqc"></a>

<p align="center"><kbd><img src="assets/z1ks1yvtusf.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên đại khái gs review lại Newton's method. Ta nhớ bài toán đặt
> ra là ta cần tìm solution của equation f(x) = x^2 - 5 = 0, để có thể tìm
> căn  bậc hai của 5.
>
>
>
> Thế thì bài để solve equation này đương nhiên là ta cần tìm x nơi
> function  f(x) cắt trục y.
>
>
>
> Vậy cách làm là, ta sẽ bắt đầu bằng initial guess x0. Từ đó vẽ (thiết
> lập) tiếp tuyến với hàm f(x) tại x0 và tìm giao điểm của nó với trục y.
> Đây sẽ  là next guess x1. Tiếp tục làm vậy, dần dần ta sẽ tiến về giao
> điểm của  f(x) và trục y

<br>

<a id="node-m7xz9ev"></a>

<p align="center"><kbd><img src="assets/fniulbanw3.png" width="80%"></kbd></p>

> [!NOTE]
> Phương trình tiếp tuyến tại x0 của f(x) thì biết rồi: y - y0 = f'(x0)(x-x0)
> từ đó, giải tìm giao điểm của nó với f(x) tức y = 0, ta có x = x0 - f(x0)/f'(x0)
> và đó là x1 (second guess)
>
>
>
> Tương tự vậy, công thức của mỗi guess sẽ là x_n+1 = x_n - f(x_n)/f'(x_n)

<br>

<a id="node-6xo0lfe"></a>

<p align="center"><kbd><img src="assets/wjpomv1bl4.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo ta sẽ xem xét error sẽ như
> thế nào sau mỗi lần guess.

<br>

<a id="node-e9qkzfq"></a>

<p align="center"><kbd><img src="assets/pl8q727pss.png" width="80%"></kbd></p>

> [!NOTE]
> Gs cho biết E2 = E1^2 (không rõ tại sao)

<br>

<a id="node-9m7co2s"></a>

<p align="center"><kbd><img src="assets/eiiyws5a2j7.png" width="80%"></kbd></p>

> [!NOTE]
> Và do đó số digit của độ chính xác
> sẽ double sau mỗi step

<br>

<a id="node-hcp17gl"></a>

<p align="center"><kbd><img src="assets/g9pp41pnju.png" width="80%"></kbd></p>

> [!NOTE]
> Một số điều kiện để Newton method có tác dụng, là:
>
>
>
> f' không quá nhỏ, f'' không quá lớn và x0 bắt đầu ở gần x

<br>

<a id="node-j37hkgz"></a>

<p align="center"><kbd><img src="assets/xdf3cw42ui.png" width="80%"></kbd></p>

> [!NOTE]
> Nó có thể fail. theo cách này, nếu ta  bắt đầu ở điểm này thì
> thay vì nó tìm ra điểm cần tìm là √5, thì nó lại tìm ra -√5

<br>

<a id="node-g1j3ihn"></a>

<p align="center"><kbd><img src="assets/4iayopazrda.png" width="80%"></kbd></p>

> [!NOTE]
> nếu bắt đầu (x0) ở tại điểm này, nới có f' = 0 thì ta cũng sẽ fail,
> vì khi đó tangent sẽ song song với trục x, không thể tìm được
> x1

<br>

<a id="node-cc2bu29"></a>

<p align="center"><kbd><img src="assets/c4kv96vxbt.png" width="80%"></kbd></p>

> [!NOTE]
> Và theo công thức cũng có thể thấy f'
> (x0) = 0 khiến denominator = 0

<br>

<a id="node-f22lv7i"></a>

<p align="center"><kbd><img src="assets/jagwe273x5b.png" width="80%"></kbd></p>

> [!NOTE]
> Và một case nữa mà phương pháp này có thể fail là khi hàm f
> có dạng wiggle như thế này.
>
>
>
> Khi đó x0 -> x1, x1 lại tìm ra next guess chính là x0, trở thành
> vòng lặp

<br>

<a id="node-uyatdfl"></a>

<p align="center"><kbd><img src="assets/37ha2xanmeu.png" width="80%"></kbd></p>

> [!NOTE]
> Ta qua Mean Value Theorem:
>
>
>
> Đại khái là nếu ta đi từ A đến B cách nhau 3000 cây, trong 6
> tiếng, thì chắc chắn phải có lúc nào đó ta bay với tốc độ trung
> bình = 3000/6 = 500

<br>

<a id="node-snfiy1m"></a>

<p align="center"><kbd><img src="assets/in0dzs58gs.png" width="80%"></kbd></p>

> [!NOTE]
> Thể hiện theo toán học:
>
>
>
> Là độ dốc trung bình từ a đến b (∆f/∆x = [f(b)-f(a)]/[b-a]) bằng độ dốc tại
> điểm nào c nào đó trong đoạn a, b: f'(c)

<br>

<a id="node-ryi8748"></a>

<p align="center"><kbd><img src="assets/b4g5dgbokdm.png" width="80%"></kbd></p>

> [!NOTE]
> Điều kiện là hàm f khả vi trên a, b (tức tồn tại đạo hàm tại mọi
> điểm trên [a, b] cũng như là hàm liên tục trên đoạn này

<br>

<a id="node-a3nt7r7"></a>

<p align="center"><kbd><img src="assets/8gi6p52ylui.png" width="80%"></kbd></p>

> [!NOTE]
> Chứng minh MVT: như sau, cho rằng hàm f có đường cong như vầy 
> trong đoạn a,b.
>
>
>
> Thì độ dốc của secant line (nối hai điểm đầu), dễ thấy chính là vế trái
> của phương trình cần chứng minh
>
>
>
> Để tìm c, ta sẽ cho một đường song song với secant line, và di chuyển
> từ từ cho đến khi chạm vào đường cong funcion, Thì khi đó ta đã tìm 
> ra c
>
>
>
> Và khi làm vậy ta cũng ignore các điểm nằm ngoài đoạn a,b, chỉnh xét
> những phần bên trong a,b. Ý là, có thể khi chưa chạm vào f thì đường 
> song song này đã cắt f ở đâu đó ngoài đoạn a,b (ý là giữa hai điểm
> (a, f(a)) và (b, f(b)) rồi

<br>

<a id="node-cxozn8u"></a>

<p align="center"><kbd><img src="assets/0lxqdqvkm04.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên có thể sinh ra vấn đề là ta gặp đường cong thế này, thì
> khi đường song song chạm vào f cũng là khi nó trùng secant line
>
>
>
> Cách khắc phục là khi đó ta làm ngược lại, xuất phát từ phía trên
> và đi dần xuông

<br>

<a id="node-411970n"></a>

<p align="center"><kbd><img src="assets/t8eeyoixt3q.png" width="80%"></kbd></p>

> [!NOTE]
> gs cho rằng phải thỏa mãn các giả thiết ban đầu là hàm số khả
> vi và liên tục trên đạon a,b thì định lí này mới đúng.

<br>

<a id="node-tff5tmu"></a>

<p align="center"><kbd><img src="assets/ym7ho5b1hvn.png" width="80%"></kbd></p>

> [!NOTE]
> 3 ứng dụng, hay có thể coi là các hệ quả của địh lí
> này mà gs cho rằng ta đã biết rồi

<br>

<a id="node-msmuxqn"></a>

<p align="center"><kbd><img src="assets/9kb386r2wc4.png" width="80%"></kbd></p>

> [!NOTE]
> Để chứng minh 3 cái hệ quả trên ta sẽ viết lại
> như vầy

<br>

<a id="node-qdz10op"></a>

<p align="center"><kbd><img src="assets/qwf0l0bi0s.png" width="80%"></kbd></p>

> [!NOTE]
> Từ đó quá dễ thấy rằng tùy vào f'(c) có dấu như thế nào mà ta có
> thể kết luận hàm tăng hay giảm hay constant
>
>
>
> Sau đó là một loạt các câu hỏi, tuy nhiên có vẻ mean value
> theorem không quan trọng lắm nên bỏ qua có gì quay lại sau

<br>

<a id="node-n8g6cye"></a>

<p align="center"><kbd><img src="assets/wclde7uu4xm.png" width="80%"></kbd></p>

> [!NOTE]
> Phần cuối gs áp dụng MVT để chứng minh bất đẳng
> thức. Ví dụ e^x > 1 + x với x > 0.

<br>

<a id="node-x2bf4eq"></a>

<p align="center"><kbd><img src="assets/l2ryv27gh8i.png" width="80%"></kbd></p>

> [!NOTE]
> Cách làm là đặt f(x) = e^x - 1+x
>
>
>
> Khi đó f(0) = e^0 - 1 + 0 = 0.
>
>
>
> f'(0) = e^x - 1, và vì với x > 0 thì e^x > 1 nên f'(x) LUÔN DƯƠNG
> KHI X > 0
>
>
>
> Từ đó dựa vào MVT kết luận HÀM SỐ LUÔN TĂNG KHI X > 0
>
>
>
> Do đó đương nhiên f(x) > f(0) với x > 0 
>
>
>
> Và do đó e^x - 1 + x > 0 với x > 0 . Chứng minh xong

<br>

<a id="node-f4ksyhv"></a>

<p align="center"><kbd><img src="assets/tubh4boosp9.png" width="80%"></kbd></p>

> [!NOTE]
> Bài toán thứ hai là chứng minh e^x > 1 + x + x^2. Hoàn toàn
> tương tự, ta sẽ đặt g(x) = e^x - (1 + x + x^2/2)
>
>
>
> Sau đó tính g(0) ra bằng 0

<br>

<a id="node-6fwptsc"></a>

<p align="center"><kbd><img src="assets/nm0amlb8fa.png" width="80%"></kbd></p>

> [!NOTE]
> và xét g'(x) thấy nó = e^x - (1+x) và cái này từ ví dụ 1, đã cho
> thấy nó luôn > 0 với x > 0.
>
>
>
> Từ đó theo MVT g(x) luôn tăng khi x > 0 => g(x) > g(0) => e^x -
> (1 + x + x^2/2) > 0 => chứng minh xong

<br>

<a id="node-nl9im7k"></a>

<p align="center"><kbd><img src="assets/f09vdaqaevq.png" width="80%"></kbd></p>

> [!NOTE]
> Và gs nói mọi chuyện sẽ tương tự tiếp tục như vậy để ta có thể
> tiếp tục chứng minh e^x > 1 + x + x^2/2
> + x^3/(3*2) + x^4/(4*3*2)....
>
>
>
> và ông nói vế phải khi kéo dài tới vô cùng số hạng thì cuối cùng
> sẽ bằng vế trái e^x
>
>
>
> Và ta sẽ quay lại cái này ở các bài cuối (Taylor series)

<br>

