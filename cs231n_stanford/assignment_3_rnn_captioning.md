# Assignment 3 - RNN Captioning

📊 **Progress:** `12` Notes | `49` Screenshots

---
<a id="node-pmrs1d0"></a>

## Assignment 3 - RNN Captioning

<br>

<a id="node-zs6vrjq"></a>

<p align="center"><kbd><img src="assets/wb6zzb49e.png" width="80%"></kbd></p>

<br>

<a id="node-4f9u1nj"></a>

<p align="center"><kbd><img src="assets/0s7x7pttl72k.png" width="80%"></kbd></p>

> [!NOTE]
> chạy dòng code có sẵn để chạy cái script tải bộ dữ liệu coco về

<br>

<a id="node-idp1w8q"></a>

<p align="center"><kbd><img src="assets/viuz43nii3f.png" width="80%"></kbd></p>

> [!NOTE]
> không hiểu sao lần này khi nó chạy tới from cs231n.rnn_layers
> import * và mấy dòng import sau đều bị lỗi, thử nhiều cách,
> cuối cùng thấy thêm cái path dẫn tới cs231n vào sys.path giúp
> giải quyết được lỗi này.

<br>

<a id="node-hlwqkvj"></a>

<p align="center"><kbd><img src="assets/moz7ahs3zx.png" width="80%"></kbd></p>

> [!NOTE]
> Nói về COCO dataset, người ta cho biết đây là bộ dữ liệu tiêu chuẩn cho bài
> toán "image captioning". Bộ dữ liệu chứ 80.000 training images và 40000
> validation images. Mỗi bức hình có 5 dòng caption được viết bởi con người sử
> dụng nền tảng Amazon Mechanical Turk.
>
>
>
> Image feature: Thì đại ý là **người ta đã extract feature sẵn**, mà như đã nói
> trong bài giảng, người ta **"đưa image qua" một CNN** để có được một
> **embedding feature vector**, mang thông tin của bức hình trước khi được
> chuyển vào RNN để generate caption. Thì ở đây người ta đã làm bước này, với
> mô hình **VGG16**, và cụ thể là họ dùng **output của cái fully-connection layer
> fc7**, là một vector có số **dimension là 4096** (dễ hiểu fc7 có **4096** neuron).
> Thế, các image từ training set và validation set đã được chuyển thành các
> embedding vector, lưu trong file tương ứng.
>
>
>
> Thêm một bước nữa, họ dùng PCA để giảm chiều không gian / "nén" từ 4096-d
> vector thành **512-d** để nếu cần có thể dùng nó để tiết kiệm memory và compute.
>
>
>
> Ngoài ra, trong đây do dung lược của bộ hình gốc quá lớn tới 20GB, nên họ chỉ
> để các url, để cần dùng thì mở ra xem. Vì hình ảnh này thì cũng trên Flicker chứ
> đâu
>
>
>
> ===
>
>
>
> Phần caption, họ đã chuẩn bị vocab dict để mình chuyển một từ thành ra id
> Cũng như function để làm ngược lại. Cái này là để encode-decode input và
> output của RNN
>
>
>
> ===
>
>
>
> Cuối cùng là nói về các special token, họ cũng đã giúp ta thêm <START> và
> <END> token vào đầu và cuối câu (caption). Cũng như là pad các câu ngắn với
> <NULL> token để mình đã có các sequence dài bằng nhau cho việc  Batching.

**🔗 See also:** [linked note](./assignment_4_transformer_image_captioning.md#node-qlza70c)

<br>

<a id="node-qfn133i"></a>

<p align="center"><kbd><img src="assets/t5ynenh0gr.png" width="80%"></kbd></p>

> [!NOTE]
> Có thể thấy train_caption đã được tokenized và (zero) padded sẵn
> cho mình rồi
>
>
>
> Dùng function idx_to_word để chuyển token ra lại word string.

<br>

<a id="node-0i4wv2f"></a>

<p align="center"><kbd><img src="assets/xxpebi1jyw9.png" width="80%"></kbd></p>

<br>

<a id="node-6c6m5vn"></a>

<p align="center"><kbd><img src="assets/ra1yk78mqk.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/08bjoh0t8q5.png" width="80%"></kbd></p>

<br>

<a id="node-lh91ddg"></a>

<p align="center"><kbd><img src="assets/0xd3k755stw.png" width="80%"></kbd></p>

> [!NOTE]
> cơ bản là dễ, chỉ có điều cần
> xử lý shape cho đúng

<br>

<a id="node-8cek8wb"></a>

<p align="center"><kbd><img src="assets/tk3tpyxfin.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4vtvijtiqym.png" width="80%"></kbd></p>

<br>

<a id="node-vqdz3zd"></a>

<p align="center"><kbd><img src="assets/rtbfgm9kzbs.png" width="80%"></kbd></p>

> [!NOTE]
> Theo computation graph thôi, transpose matrix để ra shape phù
> hợp.
>
>
>
> Nhớ rằng b được broadcast, nên nó tham gia với mọi w_i.x_i (+ b)
> để ra z_i nên db = sum(dz)

<br>

<a id="node-94w32q8"></a>

<p align="center"><kbd><img src="assets/yhkvdyss0pn.png" width="80%"></kbd></p>

<br>

<a id="node-gnly8w2"></a>

<p align="center"><kbd><img src="assets/6yo7ucss0yo.png" width="80%"></kbd></p>

<br>

<a id="node-048g8rj"></a>

<p align="center"><kbd><img src="assets/ql3zhx8dfp.png" width="80%"></kbd></p>

<br>

<a id="node-x42hluu"></a>

<p align="center"><kbd><img src="assets/lb0y0trxsxo.png" width="80%"></kbd></p>

<br>

<a id="node-fe6drd1"></a>

<p align="center"><kbd><img src="assets/jpl7i3eqgwl.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0odw6b92j23.png" width="80%"></kbd></p>

> [!NOTE]
> 1. Đại ý tại mỗi step, dùng rnn_step_backward để từ upstream grad tính các
> dWx, dWh, dxt,  dh_prev
>
>
>
> Thì, đảm bảo upstream grad (là dh<t>) là tổng của gradient do L<t> mà h<t>
> "Trực tiếp tham gia" và  gradient do các L sau mà h<t> gián tiếp tham gia khi 
> tính h<t+1> . Biểu hiện bằng mũi tên màu hồng.
>
>
>
> 2. Vì Wh (Wx tương tự) tham gia tính toán tại mỗi time-step nên đơn giản
> là tại mỗi rnn_step_backward tính được dWh thì cộng dồn vào.
> Và nếu muốn suy nghĩ sâu xa hơn thì vì upstream gradient là "đã gồm ảnh
> hưởng tới L<t> và cả các L sau đó) nên đã có phần gradient của Wh khi nó
> "Trực tiếp tính Lt" và "gián tiếp tính các L sau đó" (Ý là không sợ thiếu gradient
> cho W) nếu đảm bảo ý 1.
>
>
>
> 3. Cho dxt thì dễ rồi tại step nào thì assign vào t của dx đó.

<br>

<a id="node-pbhx9yb"></a>

<p align="center"><kbd><img src="assets/ag2xh9aqdir.png" width="80%"></kbd></p>

<br>

<a id="node-u5dofyq"></a>

<p align="center"><kbd><img src="assets/j0rj2nuap5k.png" width="80%"></kbd></p>

<br>

<a id="node-1tw5anz"></a>

<p align="center"><kbd><img src="assets/fj3i49l5djv.png" width="80%"></kbd></p>

<br>

<a id="node-v3p4mwj"></a>

<p align="center"><kbd><img src="assets/z0f7f84t77.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/24voil4jqmw.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/f14ob0942r.png" width="80%"></kbd></p>

<br>

<a id="node-q773pnf"></a>

<p align="center"><kbd><img src="assets/qary3cem4i.png" width="80%"></kbd></p>

<br>

<a id="node-tdhfkjy"></a>

<p align="center"><kbd><img src="assets/lkbggbkduo8.png" width="80%"></kbd></p>

> [!NOTE]
> Cái này chỉ là affine transform từ
> ht->y^t nên họ làm giùm

<br>

<a id="node-32gw2po"></a>

<p align="center"><kbd><img src="assets/bxcus5xazcp.png" width="80%"></kbd></p>

<br>

<a id="node-74z50ji"></a>

<p align="center"><kbd><img src="assets/p92axstd12m.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/xvzo63my55f.png" width="80%"></kbd></p>

> [!NOTE]
> cái này người ta ko bắt làm nhưng vẫn làm
> lại vì nó có vụ T cũng như mask

<br>

<a id="node-ma3lr0q"></a>

<p align="center"><kbd><img src="assets/ii68f98jxw.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/93otyvs2umu.png" width="80%"></kbd></p>

> [!NOTE]
> Solution chuẩn của Standford có thể học theo

<br>

<a id="node-buo68s5"></a>

<p align="center"><kbd><img src="assets/8fhiycx10qv.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/k0khoynvdmk.png" width="80%"></kbd></p>

<br>

<a id="node-p7gso1h"></a>

<p align="center"><kbd><img src="assets/wa6ivs6gc6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/8icfhwjzad9.png" width="80%"></kbd></p>

<br>

<a id="node-f5vhxgs"></a>

<p align="center"><kbd><img src="assets/9phlopcfwaw.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/841jwjmboew.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/gttd0ju0v5j.png" width="80%"></kbd></p>

<br>

<a id="node-se8eft4"></a>

<p align="center"><kbd><img src="assets/g2bjuhg429.png" width="80%"></kbd></p>

<br>

<a id="node-jopu4zu"></a>

<p align="center"><kbd><img src="assets/28umwd7rvnq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/oggyb3mbl9.png" width="80%"></kbd></p>

<br>

<a id="node-qapf0q1"></a>

<p align="center"><kbd><img src="assets/tlnceurosf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/59exsdxgmhb.png" width="80%"></kbd></p>

<br>

<a id="node-g4b1axz"></a>

<p align="center"><kbd><img src="assets/fh7bcz79cyu.png" width="80%"></kbd></p>

<br>

<a id="node-2283mkx"></a>

<p align="center"><kbd><img src="assets/4cca7161m89.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/4femucfj5xo.png" width="80%"></kbd></p>

> [!NOTE]
> Affine layer chuyển image embedding thành h0,
> Chuẩn bị (một batch) các <START> token id.
> Pass qua embedding layer để chuyển thành các
> word encoding vector đưa vào as x0.
>
>
>
> Sau đó lần lượt gọi function rnn_step_forward để
> tính ht, dùng affine để chuyển thành y^ và Argmax
> để lấy ra in tương ứng từ có p cao nhất, assign
> vào captions (chú ý không cần chuyển qua word
> string, captions yêu cầu chứa word id)
>
>
>
> Tiếp tục ht tính bước tiếp theo cùng với từ được
> chọn ở time-step trước

<br>

<a id="node-08qkn5s"></a>

<p align="center"><kbd><img src="assets/cpcjnnhf0rf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sm885gsj2xb.png" width="80%"></kbd></p>

<br>

<a id="node-h4s3gl0"></a>

<p align="center"><kbd><img src="assets/w9v5bhczsz.png" width="80%"></kbd></p>

> [!NOTE]
> trả lời vài ý, quay lại sau, giờ làm qua
> LSTM Captioning luôn

<br>

