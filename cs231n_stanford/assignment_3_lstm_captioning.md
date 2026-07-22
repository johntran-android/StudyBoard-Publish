# Assignment 3 - Lstm Captioning

📊 **Progress:** `9` Notes | `34` Screenshots

---
<a id="node-shx4e0v"></a>

## Assignment 3 - Lstm Captioning

<br>

<a id="node-nna205o"></a>

<p align="center"><kbd><img src="assets/v8bm0h8weyn.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/nchjb72vhza.png" width="80%"></kbd></p>

> [!NOTE]
> ở đây lại không bị cái vụ lỗi import như ở RNN captioning, cũng như
> trong notebook đó ta cũng sẽ dùng COCO dataset

<br>

<a id="node-cf3iuap"></a>

<p align="center"><kbd><img src="assets/nx3aqxpy4a8.png" width="80%"></kbd></p>

> [!NOTE]
> mô tả lại cách "làm" LSTM, như đã biết, nhưng chú ý là ở đây trong cs231n,
> khác với DLSpec hay NLPSpec, ta sẽ "gộp" các matrix W (cho các gate) thành
> matrix lớn, để rồi khi tính, cơ bản là ta tính một lượt từ xt, ht-1, ra luôn 4 vector
> dưới dạng một vector a dài 4H, sau đó cắt ra và apply các function sigmoid /
> tanh khác nhau để có các gate vector.
>
>
>
> Sau đó thì tính ct, ht thì biết rồi.

<br>

<a id="node-8ltmc50"></a>

<p align="center"><kbd><img src="assets/dxhooqpkm36.png" width="80%"></kbd></p>

<br>

<a id="node-wg2s0ha"></a>

<p align="center"><kbd><img src="assets/aufccitu5mr.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ng3dawiofa.png" width="80%"></kbd></p>

> [!NOTE]
> forward tương đối đơn giản, theo mô tả đã rất rõ
> không cần phải note gì nhiều

<br>

<a id="node-hnqxfb7"></a>

<p align="center"><kbd><img src="assets/xe5mmus7mul.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/it6anbyv73.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0elnrzj78fpp.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/yhtk7cl5ctf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jkxgy2bvwsm.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/8dt2cig1jpg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ckqrhzb25r8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0eu7855d4b3k.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/3bka45kzpb9.png" width="80%"></kbd></p>

> [!NOTE]
> dnext_c input chỉ là 1 nhánh, ct có tham gia tính ht,nên phải có 
> gradient của nhánh đó nữa.
>
>
>
> dnext_c += dnext_h * cache['o'] * (1-np.tanh(cache['next_c'])**2) 
>
>
>
> dprev_c = dnext_c * cache['f']
>
> df = dnext_c * cache['prev_c']   # (N,H)*(N,H) = (N,H)
>
> di = dnext_c * cache['g']  # (N,H)*(N,H) = (N,H)
>
> dg = dnext_c * cache['I']  # (N,H)*(N,H) = (N,H)
>
> do = dnext_h * np.tanh(cache[' next_c']) #(N,H)*(N,H)

<br>

<a id="node-kdehn5d"></a>

<p align="center"><kbd><img src="assets/ljgga081wup.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/yce0yg7h6p.png" width="80%"></kbd></p>

> [!NOTE]
> You should see errors on the
> order of e-7 or less.

<br>

<a id="node-8i65vp9"></a>

<p align="center"><kbd><img src="assets/1ke193socre.png" width="80%"></kbd></p>

<br>

<a id="node-blo3osx"></a>

<p align="center"><kbd><img src="assets/lu938todnnf.png" width="80%"></kbd></p>

> [!NOTE]
> You should see an error on
> the order of e-7 or less

<br>

<a id="node-idxex2p"></a>

<p align="center"><kbd><img src="assets/9ienk3hv2l.png" width="80%"></kbd></p>

> [!NOTE]
> Hoàn toàn tương tự cái rnn_backward()

<br>

<a id="node-n3r5378"></a>

<p align="center"><kbd><img src="assets/135xc3fwyp9r.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/b5vye4nmpyo.png" width="80%"></kbd></p>

<br>

<a id="node-hmuouqn"></a>

<p align="center"><kbd><img src="assets/r6mn9q80etq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/smf8sliimdh.png" width="80%"></kbd></p>

<br>

<a id="node-o93gnp8"></a>

<p align="center"><kbd><img src="assets/g5i2k5ie6ed.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/c2aiaojcgbn.png" width="80%"></kbd></p>

> [!NOTE]
> Update thêm case lstm

<br>

<a id="node-v9lx7yl"></a>

<p align="center"><kbd><img src="assets/3ppir2zhqj7.png" width="80%"></kbd></p>

> [!NOTE]
> update thêm case của
> lstm cho sample()

<br>

<a id="node-2l7s8fz"></a>

<p align="center"><kbd><img src="assets/s8pqmstyd8.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/31fo9jdnh88.png" width="80%"></kbd></p>

<br>

<a id="node-6n79g9x"></a>

<p align="center"><kbd><img src="assets/qfzuojs9ih.png" width="80%"></kbd></p>

<br>

<a id="node-hd9ng5b"></a>

<p align="center"><kbd><img src="assets/3uuxbon6my.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/taxgmd0w1zo.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hh19wt1z1xq.png" width="80%"></kbd></p>

<br>

<a id="node-tgxnwee"></a>

<p align="center"><kbd><img src="assets/w7satarr8oe.png" width="80%"></kbd></p>

<br>

