# Assignment 2 - Dropout

📊 **Progress:** `6` Notes | `14` Screenshots

---
<a id="node-wegbym1"></a>

## Assignment 2 - Dropout

<br>

<a id="node-zojt1wh"></a>

<p align="center"><kbd><img src="assets/px1cbf4z5bd.png" width="80%"></kbd></p>

<br>

<a id="node-obps5cz"></a>

<p align="center"><kbd><img src="assets/f4amwlaxhxv.png" width="80%"></kbd></p>

> [!NOTE]
> Dropout module thực ra rất đơn giản
>
>
>
> chú ý là nếu làm theo kiểu x*= mask, out = x thì
> sẽ không pass test do x đã bị thay đổi.

<br>

<a id="node-lhzcs4v"></a>

<p align="center"><kbd><img src="assets/mrrb51e045.png" width="80%"></kbd></p>

<br>

<a id="node-jr3qytn"></a>

<p align="center"><kbd><img src="assets/qiv5p0vmnlf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/lskg3bzea.png" width="80%"></kbd></p>

<br>

<a id="node-uvbf1cs"></a>

<p align="center"><kbd><img src="assets/3hklro8es6a.png" width="80%"></kbd></p>

> [!NOTE]
> Error should be around
> e-10 or less: Passed
>
> câu hỏi là nếu ko chia cho p thì sao?

<br>

<a id="node-dj866ge"></a>

<p align="center"><kbd><img src="assets/6ok5u4hehy6.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ui2g5o13vg.png" width="80%"></kbd></p>

> [!NOTE]
> Relative errors should be around e-6 or less.
> Note that it's fine if for dropout_keep_ratio=1
> you have W2 error be on the order of e-5.

<br>

<a id="node-62k8lgs"></a>

<p align="center"><kbd><img src="assets/wp5rul80re.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/o8s6sy2g1uq.png" width="80%"></kbd></p>

> [!NOTE]
> Nếu có dropout thì
> apply nó trước relu,

<br>

<a id="node-mqeicop"></a>

<p align="center"><kbd><img src="assets/ry4f4szbex.png" width="80%"></kbd></p>

<br>

<a id="node-hvsbfqh"></a>

<p align="center"><kbd><img src="assets/0hhyxxgattj.png" width="80%"></kbd></p>

> [!NOTE]
> Có thể thấy rõ với dropout giúp giảm overfit
> nên val acc tốt hơn (đương nhiên là train acc
> kém hơn)

<br>

<a id="node-6y32hol"></a>

<p align="center"><kbd><img src="assets/tcvjnzfpm5i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/zyifstvyetr.png" width="80%"></kbd></p>

> [!NOTE]
> đồ thì cho thấy khi có dropout thì training performance giảm,
> nhưng validation performance thì tốt hơn cho thấy dropout đã
> khắc phục tình trạng overfit

<br>

