# Lecture 3: Backprop And Neural Networks

📊 **Progress:** `29` Notes | `54` Screenshots

---
<a id="node-jphx3id"></a>

## Lecture 3: Backprop And Neural Networks

<br>

<a id="node-a8jux7o"></a>

<p align="center"><kbd><img src="assets/b46rhommjda.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về bài toán NER - phân biệt các từ trong
> đoạn văn là "loại gì" - tên riêng, location,....

<br>

<a id="node-rh4drsv"></a>

<p align="center"><kbd><img src="assets/g2jq038jvq5.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là để làm cái này, cách làm là người ta sẽ train nhiều cái "
> classifier" (mỗi cái xác định 1 loại - ví dụ cái thì xem có phải là location
> hay không, cái thì xem có phải là personal name không). Và các
> classifier này sẽ được train bằng Supervised learning với hand-labeled
> data.
>
>
>
> Quá trình training sẽ là lấy 1 window các từ, trong đó có từ cần Predict ở
> giữa và các từ context quanh nó, lấy tất cả các word Vector của từ đó,
> concatenate lại thành 1 vector (ví dụ window chứa 5 từ thì thành 5D
> vector)
>
>
>
> Đưa vào classifier - thường chỉ là logistic regression model. Và tính loss,
> update model weight bằng gradients như thông thường.
>
>
>
> Như vậy khi train được các classifier cho mỗi loại, khi inference, ta sẽ chỉ
> đơn giản là chạy classifier qua các window của document để predict.

<br>

<a id="node-h7bq9fi"></a>

<p align="center"><kbd><img src="assets/yrxik6sitgp.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái như đã nói, ở đây chỉ là một logistic regression model có dạng như
> một neural network đơn giản với 1 hidden layer  với parameters matrix W,
> b. Nó sẽ nhận vector của "window" có dạng token, hay one hot vector Sau
> đó chuyển thành word embedding (có thể là bằng cách lấy từ bộ
> pre-trained word  embedding vector và concate như đã nói
>
>
>
> Tiếp đó thực hiện  phép nhân matrix với W và b, sau đó cho qua  activation
> function, để rồi pass kết quả qua layer cuối có 1 unit, sigmoid để Predict ra
> probability từ (+context) đưa vào có phải là loại mà classifier này  đang đảm
> nhiệm phân biệt hay không

<br>

<a id="node-zs9dgqb"></a>

<p align="center"><kbd><img src="assets/dy4twtmoc9.png" width="80%"></kbd></p>

> [!NOTE]
> Và như ta đã biết có thể trong qúa trình training,
> ta update luôn các word vector luôn chứ không
> chỉ là các model's params

<br>

<a id="node-mwu54db"></a>

<p align="center"><kbd><img src="assets/u4xxzzd84kp.png" width="80%"></kbd></p>

> [!NOTE]
> Slide này không thấy có trong bài giảng, đại khái là
> giới thiệu, hoặc nhắc lại một số activation function
> như sigmoid, tanh, relu.....

<br>

<a id="node-gy3xn28"></a>

<p align="center"><kbd><img src="assets/40sje7145kb.png" width="80%"></kbd></p>

> [!NOTE]
> Slide này cũng ko nói đến, đại khái là nói về tầm quan trọng
> của việc sử dụng non-linear activation function. Như mình đã
> biết nếu không có nó, thì cả hệ thống các layer chỉ như một
> linear model. Các layer với non-linear function giúp capture
> các complex pattern hay nói cách khác là giúp model có 
> độ flexible cao giúp nó có thể nắm bắt các pattern phức tạp

<br>

<a id="node-nsq01kz"></a>

<p align="center"><kbd><img src="assets/bq1k6uh598c.png" width="80%"></kbd></p>

> [!NOTE]
> Slide này giáo sư cũng không nói đến, đại khái là nhắc đến loss function,
> Trong bài toán classification, ta sẽ dùng cross entropy để xây dựng loss
> function mang ý nghĩa là cần phải giảm sự khác nhau giữa hai probability
> distribution p và q.

<br>

<a id="node-2kc0ko5"></a>

<p align="center"><kbd><img src="assets/nv0cdcb40il.png" width="80%"></kbd></p>

<br>

<a id="node-24qy1gs"></a>

<p align="center"><kbd><img src="assets/08s8x1n312hl.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ý nghĩa của đạo hàm (derivative) của
> hàm số tại một điểm là độ dóc của hàm số tại đó,
> mang ý nghĩa là tỉ lệ thay đổi của hàm số so với sự
> thay đổi của biến số

<br>

<a id="node-ymfhhfa"></a>

<p align="center"><kbd><img src="assets/eqxg4xbky6p.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu f là function của vector x thì đạo hàm
> của f w.r.t x là vector các đạo hàm của f w.r.t
> các phần tử của vector x

<br>

<a id="node-opypere"></a>

<p align="center"><kbd><img src="assets/ia2b4pmgc1.png" width="80%"></kbd></p>

> [!NOTE]
> Còn nếu output của function là vector thì derivative
> của f w.r.t x sẽ là matrix gọi là Jacobian matrix, trong
> đó mỗi hàng là vector đạo hàm của phần tử tương
> ứng của output với vector x

<br>

<a id="node-w2z00qh"></a>

<p align="center"><kbd><img src="assets/562i6hpbpn.png" width="80%"></kbd></p>

<br>

<a id="node-ty17221"></a>

<p align="center"><kbd><img src="assets/azrowaex0u.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ z là vector Rn sau khi qua function f (ví dụ là sigmoid) tính
> ra h, vì phép tính là element-wise nên h cũng là vector Rn. Do đó
> derivative của f w.r.t z sẽ là jacobian matrix trong đó, mỗi hàng,
> là đạo hàm của phần tử tương ứng của h w.r.t vector z. Và vì ví
> dụ phần tử thứ 8 của h chỉ bị tác động bởi phần tử thứ 8 của z
> thành ra trong jacobian matrix, ở hàng thứ 8 chỉ có phần tử thứ 8
> là có gì đó, còn lại bằng 0. Như vậy ta có matrix vuông và chéo.

<br>

<a id="node-rax1ylt"></a>

<p align="center"><kbd><img src="assets/qxftleb2c0a.png" width="80%"></kbd></p>

> [!NOTE]
> Khuyến khích thử làm lại xem có
> ra được không.
>
> Nếu coi u là nằm ngang thì cái này cũng hợp
> lí, đạo hàm của s đối với h phải là
> vector ngang, nên phải là h.T

<br>

<a id="node-4mcu6zn"></a>

<p align="center"><kbd><img src="assets/f3idt4szpx.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái nhắc lại rằng ở đây param là W, b, u (u là weight của layer cuối
> vì chỉ có ra 1 unit, nên nó có dạng là 1 vector)
>
>
>
> Và giáo sư nói là có thể tính luôn word vector vì như đã nói ta có thể
> tuning nó thêm để giúp perform tốt hơn
>
>
>
> Và ở đây rõ ràng chỉ là đơn giản với derivative của score (tức là chưa bỏ
> qua sigmoid, và chưa tính loss) w.r.t params mang tính chất minh họa
> thôi. Chứ đúng ra là phải tính derivative của loss w.r.t params

<br>

<a id="node-dh81wje"></a>

<p align="center"><kbd><img src="assets/sqoglfnrplh.png" width="80%"></kbd></p>

> [!NOTE]
> nên track kĩ các shape

<br>

<a id="node-v41dtio"></a>

<p align="center"><kbd><img src="assets/ptquj5eznnm.png" width="80%"></kbd></p>

<br>

<a id="node-1tkl6d7"></a>

<p align="center"><kbd><img src="assets/9l0w4e6rjm.png" width="80%"></kbd></p>

<br>

<a id="node-bij65a0"></a>

<p align="center"><kbd><img src="assets/ltqaevfovlh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là áp dụng 3 cái "case" công thức ở trên: 
>
>
>
> 1. Đạo hàm của phép nhân vector uTh w.r.t vector u, 
>
>
>
> 2. Đạo hàm của element-wise non-linear activation function f(z) 
> w.r.t vector z và 
>
>
>
> 3.Đạo hàm của phép Wx+b w.r.t b.
>
>
>
> Và kí hiệu giữa uT và diag(f'(z)) chính là Hadamard product, 
> là nhân element wise vector u và vector đường chéo của matrix
> diag(f'(z))

<br>

<a id="node-dki30w5"></a>

<p align="center"><kbd><img src="assets/n549kv4j3v.png" width="80%"></kbd></p>

> [!NOTE]
> Và tương tự ta sẽ tính
> derivative của s w.r.t W

<br>

<a id="node-zwwnpei"></a>

<p align="center"><kbd><img src="assets/uf0kqatpd5k.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là quá trình này cũng tương tự và nó
> lặp lại bước tính ds/dh . dh/dz

<br>

<a id="node-ssken6s"></a>

<p align="center"><kbd><img src="assets/2knhur0wxci.png" width="80%"></kbd></p>

> [!NOTE]
> Do đó người ta define "Delta" là. cái ds/dh .
> dh/dz và như đã tính ở slide trước, nó bằng u.T
> hardamard product với f'(z)
>
>
>
> Và vì dz/db là I = identity matrix (giống như 1) nên
> ds/db là Delta
>
>
>
> Và. để tính ds/dW ta còn phải tính dz/dW

<br>

<a id="node-o3yju8z"></a>

<p align="center"><kbd><img src="assets/o9fojau83wo.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây giáo sư nói là ds/dW với s là real number còn W là nm
> matrix thì đúng theo toán học ds/dW sẽ là một row vector có
> m*n phần tử
>
>
>
> Nhưng như vậy thì sẽ khó update W khi ta muốn dW cũng
> shape với W

<br>

<a id="node-21uzibk"></a>

<p align="center"><kbd><img src="assets/8vux2jogn7i.png" width="80%"></kbd></p>

> [!NOTE]
> Thành ra chỗ này mới gọi là "rời bỏ pure
> math" để dùng shape convention, cho
> dW cùng shape với W

<br>

<a id="node-1nkze0n"></a>

<p align="center"><kbd><img src="assets/gztfai61bov.png" width="80%"></kbd></p>

<br>

<a id="node-rv2kra6"></a>

<p align="center"><kbd><img src="assets/al2cn2h5cm.png" width="80%"></kbd></p>

> [!NOTE]
> zi (element thứ i của z) được tính bằng hàng thứ
> i của W (kí hiệu Wi) với vector x và cộng với
> phần tử thứ i của vector b (bi)
>
>
>
> Nên ghi dz_i/dW_ij là d(Wi.x + bi)/dWij
>
>
>
> Và đương nhiên là ví dụ Wi.x + bi = Wi1*x1 + Wi2*x2 + ...Wid*xd + bi 
> nên d (của cái cụm trên) w.r.t các phần tử Wi1, Wi2,...Wid sẽ lần lượt
> là x1, x2...xd

<br>

<a id="node-69dk00x"></a>

<p align="center"><kbd><img src="assets/026otg49x7sx.png" width="80%"></kbd></p>

<br>

<a id="node-khcri23"></a>

<p align="center"><kbd><img src="assets/ygrptek6rag.png" width="80%"></kbd></p>

<br>

<a id="node-tkomlkm"></a>

<p align="center"><kbd><img src="assets/2zuu6tclu8a.png" width="80%"></kbd></p>

<br>

<a id="node-oym7c2m"></a>

<p align="center"><kbd><img src="assets/3tv4gj3xhi5.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là có thể theo cách bám sát jacobian form nhất có thể và
> reshape lại (theo shape convention) khi tính xong. Đây chính là
> cái mà họ đang làm, thành ra kết quả là delta transpose (để nó
> trở thành vector cột như b)

<br>

<a id="node-q1wx6gl"></a>

<p align="center"><kbd><img src="assets/8lpuj16m18i.png" width="80%"></kbd></p>

<br>

<a id="node-z5edl3q"></a>

<p align="center"><kbd><img src="assets/aiuk88f5i1.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là cơ bản nãy giờ (phần 1) là đã nói về backpropagation
> rồi. Chính là việc ta dùng chain rule, để tính đạo hàm của loss
> function đối với các vector, matrix params. Trong quá trình đó ta
> cần re-use các phần tính toán nào mà có thể xài chung được để
> hiệu quả hơn.

<br>

<a id="node-7e3ewm0"></a>

<p align="center"><kbd><img src="assets/g802q1dqf3k.png" width="80%"></kbd></p>

<br>

<a id="node-6medd95"></a>

<p align="center"><kbd><img src="assets/rjnh5m510d.png" width="80%"></kbd></p>

<br>

<a id="node-7ugwtxg"></a>

<p align="center"><kbd><img src="assets/gy2k3mbc36n.png" width="80%"></kbd></p>

<br>

<a id="node-i24305h"></a>

<p align="center"><kbd><img src="assets/kqo8upn6xhi.png" width="80%"></kbd></p>

<br>

<a id="node-lkm96mq"></a>

<p align="center"><kbd><img src="assets/7okexm9txzh.png" width="80%"></kbd></p>

<br>

<a id="node-sq1ntyb"></a>

<p align="center"><kbd><img src="assets/frb7io5438j.png" width="80%"></kbd></p>

<br>

<a id="node-u2b5qs4"></a>

<p align="center"><kbd><img src="assets/r6n7k2413l.png" width="80%"></kbd></p>

<br>

<a id="node-h3x8kbq"></a>

<p align="center"><kbd><img src="assets/fsqjtpamqx7.png" width="80%"></kbd></p>

> [!NOTE]
> tại đây giáo sư có cho một ví dụ để minh họa ý
> nghĩa của df/dy = 5 là như thế nào: Cho y wiggle một
> khoảng nhỏ e.g 0.01, tính tỉ lệ khoảng thay đổi của y
> so với 0.01 sẽ thấy ~ 5

<br>

<a id="node-5g730k7"></a>

<p align="center"><kbd><img src="assets/2h2j4ewhw95.png" width="80%"></kbd></p>

> [!NOTE]
> với kiểu phân nhánh khi forward thì
> sum gradient lại khi backward

<br>

<a id="node-xlk94em"></a>

<p align="center"><kbd><img src="assets/44bzlvup2y4.png" width="80%"></kbd></p>

<br>

<a id="node-ql0lkx4"></a>

<p align="center"><kbd><img src="assets/jsfn5pqkf5f.png" width="80%"></kbd></p>

> [!NOTE]
> Một số pattern

<br>

<a id="node-x7aevji"></a>

<p align="center"><kbd><img src="assets/4hghtt6n02k.png" width="80%"></kbd></p>

<br>

<a id="node-m4vjg1c"></a>

<p align="center"><kbd><img src="assets/2uiwp4yeo0z.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là sẽ duplicate tính toán khi làm
> backprop kiểu này - từng cái

<br>

<a id="node-9edaz6j"></a>

<p align="center"><kbd><img src="assets/lje3lfzjsg.png" width="80%"></kbd></p>

> [!NOTE]
> mà cách hiệu quả là phải làm đồng loạt, để
> tận dụng việc dùng chung các bước trung gian

<br>

<a id="node-i38her2"></a>

<p align="center"><kbd><img src="assets/clmci054wt.png" width="80%"></kbd></p>

<br>

<a id="node-dn7q5pg"></a>

<p align="center"><kbd><img src="assets/zapv0a8r9dr.png" width="80%"></kbd></p>

<br>

<a id="node-s47bkf6"></a>

<p align="center"><kbd><img src="assets/0wqinm14p1wh.png" width="80%"></kbd></p>

<br>

<a id="node-s7faxbt"></a>

<p align="center"><kbd><img src="assets/h9gqwwws3xl.png" width="80%"></kbd></p>

<br>

<a id="node-zqzi7m4"></a>

<p align="center"><kbd><img src="assets/nuahsvuavzs.png" width="80%"></kbd></p>

<br>

<a id="node-z0mzte8"></a>

<p align="center"><kbd><img src="assets/iyjp9z9y9nr.png" width="80%"></kbd></p>

> [!NOTE]
> nói về dùng numerical gradient để check analytic
> gradient. Tuy nhiên với việc dùng các framework
> ngày nay thì có thể bớt quan trọng

<br>

<a id="node-1ksvzud"></a>

<p align="center"><kbd><img src="assets/ctn1rpszych.png" width="80%"></kbd></p>

<br>

<a id="node-ch8q1q7"></a>

<p align="center"><kbd><img src="assets/fapbpu4noe.png" width="80%"></kbd></p>

<br>

