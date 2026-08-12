# Lecture 2: Elimination With
matrices

📊 **Progress:** `30` Notes | `31` Screenshots

---
<a id="node-7bup4vs"></a>

## Lecture 2: Elimination With
matrices

<br>

<a id="node-iu19hqa"></a>

## Phương pháp khử hệ phương trình

<p align="center"><kbd><img src="assets/grdqo554hs.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bài này ta sẽ giải system of equation
> này với **phương pháp elimination.**

<br>

<a id="node-jbt8gkh"></a>

### Pivot đầu tiên trong hệ phương trình

<p align="center"><kbd><img src="assets/9i894g44484.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên ta nhận định **s**ố 1 (coefficient của
> x ở equation thứ 1: a11) gs gọi nó là **pivot đầu tiên**

<br>

<a id="node-rf8yqmg"></a>

#### Bước (2,3) khử a21

<p align="center"><kbd><img src="assets/p46h2pg9.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp thep ta sẽ muốn loại bỏ a21 của equation 2, ta
> **trừ equation 2 cho equation 1 nhân cho 3 (hệ số của
> hàng 2 cột 3)**. Gọi đây là **bước (2,3)**

<br>

<a id="node-h9qov8q"></a>

##### Tạm bỏ vế phải

<p align="center"><kbd><img src="assets/50dhc5hxr4g.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nói tạm thời đừng
> quan tâm vế bên phải

<br>

<a id="node-ftpzuie"></a>

- **Khử hệ số ma trận**

<p align="center"><kbd><img src="assets/bqk69rby1t.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo là **bước (3,1)** (ý là **hủy đi hệ số tại vị trí hàng
> 3, cột 1**. Nhưng vì **nó (a31) đã = 0 sẵn rồi.**
>
>
>
> Ta sẽ làm **bước (3,2): hủy a32 đang bằng 4** bằng cách
> trừ hàng 3 cho 2*hàng 2

<br>

<a id="node-5jfuigm"></a>

- **Tích pivot tính định thức**

<p align="center"><kbd><img src="assets/7x33y001eqf.png" width="80%"></kbd></p>

> [!NOTE]
> Gs cho biết **pivot phải khác 0**. Và ở đây **ta có một case
> rất tốt khi cả 3 pivot đều khác 0**.
>
>
>
> Và ở trường hợp này, để tính **determinant** chỉ việc
> **nhân các pivot lại với nhau,** ra bằng 10 
>
>
>
> (me: qua bài về determinant ta sẽ có chứng minh tại sao
> det của triangular matrix là tích các pivot)

**🔗 See also:** [linked note](./lecture_18_properties_of_determinants.md#node-o9kzca1)

<br>

<a id="node-xw4qqql"></a>

- **Thất bại ma trận do số 0**

<p align="center"><kbd><img src="assets/axm1kzoq207.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là gs nói về **case failure**. Thì có **temporary
> fail** khi ví dụ **như number tại 1,1 hoặc 2,2 bằng 0**. Thì
> **ta luôn có thể exchange/switch row để "thoát ra"**.
>
>
>
> Ví dụ 1,1 bằng 0 mà 2,1 hoặc 3,1 khác 0 thì ta **chỉ việc
> đổi vị trí các equation**. Rồi lại làm tiếp.
>
>
>
> Nhưng **nếu làm tới hàng 2 mà 2,2 và 3,2 đều bằng 0**
> hoặc **tới hàng 3 mà 3,3 = 0** thì sẽ **ko còn row nào mà
> đổi nữa**.
>
>
>
> **Khi đó sẽ là failure**, ta sẽ có **non-inversible matrix**

<br>

<a id="node-wvucdql"></a>

- **Chuyển đổi vế phải thành c**

<p align="center"><kbd><img src="assets/4nzpvu2eiuw.png" width="80%"></kbd></p>

> [!NOTE]
> Kế tiếp ta sẽ **làm lại những bước biến đổi (nãy giờ ở
> vế trái) đối với vế phải để thành vector c**

<br>

<a id="node-sgjdv0i"></a>

- **Hệ phương trình và thay thế ngược**

<p align="center"><kbd><img src="assets/bgwi7kgmsie.png" width="80%"></kbd></p>

> [!NOTE]
> Và đến đây, chỉ việc **viết lại equation system** gọi nó là **Ux=c**. 
>
>
>
> **Back substitution**: tính z, thay vào 2 tính y, thay vào 1 tính x

<br>

<a id="node-cbidsa4"></a>

- **Tích ma trận vector theo cột**

<p align="center"><kbd><img src="assets/g8u4s8fe74w.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo gs nhắc lại việc **nhân matrix cho vector**,
> như bài trước đã học ở **góc nhìn theo column** thì nó
> là **linear combination của các column** bởi các **coeff là
> các giá trị của vector**

<br>

<a id="node-596cn5u"></a>

- **Phép nhân ma trận và tổ hợp**

<p align="center"><kbd><img src="assets/xx032xuhcm.png" width="80%"></kbd></p>

> [!NOTE]
> **matrix** A @ **col x** là **linear combination** của các
> matrix column, với **coeff là components của x** nên sẽ
> **được column**
>
>
>
> **row x @ matrix A** thì sẽ là **linear combination của các
> row của matrix A** với **coeff là components của x**, nên
> sẽ **được row.**

**🔗 See also:** [linked note](./lecture_7_solving_ax_0_pivot_variables_special_solutions.md#node-2hcturd)

<br>

<a id="node-bb6donm"></a>

- **Ma trận biến đổi hàng sơ cấp**

<p align="center"><kbd><img src="assets/5agbctfm3fo.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi là **nhân matrix gì cho matrix A** **để tương đương
> với bước thứ nhất trong quá trình eliminating** hồi
> nãy: **trừ hàng 2 cho 3*hàng 1**

<br>

<a id="node-cm4or4d"></a>

- **Tính hàng ma trận cần tìm**

<p align="center"><kbd><img src="assets/xgka7nofqbf.png" width="80%"></kbd></p>

> [!NOTE]
> Để trả lời ta sẽ đơn giản hiểu rằng **hàng thứ 1 của matrix
> cần tìm sẽ nhân với matrix A** để **ra hàng thứ 1 của
> matrix kết quả**.
>
>
>
> Vậy, vì như đã nói **row (row vector) nhân matrix** thì sẽ
> là **linear combination các matrix's row** nên **để hàng 1
> của matrix kết quả  bằng hàng 1 của A** thì **ta sẽ cần:
>
>
>
> 1** * row 1 của A + **0** * row 2 của A + **0** * row 3 của A
>
>
>
> Vậy **row 1 của** matrix cần tìm là **[1 0 0]**

<br>

<a id="node-wi2iape"></a>

<p align="center"><kbd><img src="assets/oiroe2o38c.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự, hàng 3 của matrix cần tìm sẽ nhân A để vẫn
> ra kết qủa vẫn bằng hàng 3 của A nên **hàng 3 của matrix**
> cần tìm sẽ là **[0 0 1]**

<br>

<a id="node-ols4hv1"></a>

- **Tính chất ma trận đơn vị**

<p align="center"><kbd><img src="assets/qv5q9seuh9.png" width="80%"></kbd></p>

> [!NOTE]
> Đến đây gs hỏi, **thế thì matrix gì sẽ ko thay đổi A**:
> dễ thấy nó sẽ là **Identity matrix**

<br>

<a id="node-vs9k0ap"></a>

- **Tổ hợp tuyến tính hàng ma trận**

<p align="center"><kbd><img src="assets/bqvwebml1o6.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy **nhờ cách hiểu linear combination of A's row** nên ta
> dễ thấy ta cần **(-3)*row 1+ 1*row 2+ 0*row 3**. Nên **row thứ
> 2 của matrix cần tìm là [-3 1 0]**

<br>

<a id="node-zi97w9p"></a>

- **Phần tử ma trận tích**

<p align="center"><kbd><img src="assets/rm8craomt7.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi đặt ra là **làm sao để check một entry của matrix**
> **kết quả,** ví dụ **hàng 2, cột 3.**
>
>
>
> Là vầy: Hàng 2 của "matrix kết quả" sẽ đến từ **việc nhân
> hàng 2** của "matrix đầu" (ví dụ gọi là matrix M) cho matrix A.
> Tức **nó là linear combination của các row của matrix A**
> với coefficients là các component của hàng 2 của matrix M.
>
>
>
> Vậy vị trí đang nói chính là dot product của **hàng 2 matrix
> M** với **col 3 matrix A**

<br>

<a id="node-115obvu"></a>

<p align="center"><kbd><img src="assets/0d8689pfw4k.png" width="80%"></kbd></p>

> [!NOTE]
> Tạm gọi nó là matrix **E_21**, E là **eliminate,** 21 là
> vì nó giúp **eliminate vị trí hàng 2 cột 1 của matrix A**

<br>

<a id="node-s9rlcic"></a>

<p align="center"><kbd><img src="assets/rca1fducvm.png" width="80%"></kbd></p>

> [!NOTE]
> Step 2, tương tự, ta sẽ **cần hàng 1 và 2 giữ nguyên** nên
> r**ow 1, 2 của E_32** sẽ là **[1 0 0], [0 1 0]**
>
>
>
> Còn **hàng 3 sẽ là [0 -2 1]** để nó "cộng hàng 3 của A với
> -2*hàng 1 của A" nhờ vậy sẽ khử đi A_32

<br>

<a id="node-f5qp0jc"></a>

<p align="center"><kbd><img src="assets/zix92p8j43.png" width="80%"></kbd></p>

<br>

<a id="node-szgupqg"></a>

<p align="center"><kbd><img src="assets/4wzwm7fvy0x.png" width="80%"></kbd></p>

> [!NOTE]
> Tóm gọn lại các **phép biến đổi** từ **A thành U
> nãy giờ chính là vầy**
>
>
>
> E21A để khử A21
>
>
>
> E32(E21A) để khử tiếp A32

<br>

<a id="node-pwjwrwl"></a>

<p align="center"><kbd><img src="assets/d2kcqx0dzhw.png" width="80%"></kbd></p>

> [!NOTE]
> Gs đặt câu hỏi là **matrix nào biến A
> thành U**

<br>

<a id="node-gxgmk0r"></a>

<p align="center"><kbd><img src="assets/khbabvgmv4.png" width="80%"></kbd></p>

> [!NOTE]
> Câu trả lời **đó là**: **ta có thể thay đổi vị trí dấu ngoặc**, tức là
> ta có thể t**ính E32*E21 trước**, rồi **nhân nó cho A**.
>
>
>
> Đây chính là **associated law (luật kết hợp)**

<br>

<a id="node-rpr9msy"></a>

<p align="center"><kbd><img src="assets/ahmsa9of5mp.png" width="80%"></kbd></p>

> [!NOTE]
> Thử suy nghĩ **matrix nào sẽ giúp switch/exchange 2
> row của matrix thứ 2.**
>
>
>
> Để **dc hàng thứ 1** ra **[c d]** ta cần hàng thứ 1 của
> matrix abcd * 0 + hàng thứ 2 của abcd * 1 -> **row 1
> của matrix cần tìm là [0 1]**
>
>
>
> Tương tự, **dễ thấy row 2 của matrix cần tìm là [1 0]**

<br>

<a id="node-swa33vs"></a>

<p align="center"><kbd><img src="assets/2brhnu6i75d.png" width="80%"></kbd></p>

> [!NOTE]
> Đó gọi là **permutations matrix**, **exchange các row của
> identity matrix** thì ta sẽ có **matrix giúp exchange row**

<br>

<a id="node-slwolcs"></a>

<p align="center"><kbd><img src="assets/9ztuihm86k.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp theo **matrix nào
> giúp switch column?**

<br>

<a id="node-b1vx0pe"></a>

<p align="center"><kbd><img src="assets/00tyz3tz8ems.png" width="80%"></kbd></p>

> [!NOTE]
> Câu trả lời là **cũng P matrix nhưng để bên phải**
>
>
>
> Cụ thể: col 1 của AP sẽ là linear combination của A's columns
> với coefficients là col 1 của P. Nên để đổi chỗ hai columns của
> A thì col 1 của P sẽ là [0 1] và [1 0]

<br>

<a id="node-bvqtt2v"></a>

<p align="center"><kbd><img src="assets/tlqwlczu1h.png" width="80%"></kbd></p>

> [!NOTE]
> Gs nhắc nhở rằng **nhân matrix phải theo thứ tự, A@B
> KHÔNG BẲNG B@A**
>
>
>
> hay **commutative law ko áp dụng**

<br>

<a id="node-c45tfqh"></a>

<p align="center"><kbd><img src="assets/pnn7f37l3p.png" width="80%"></kbd></p>

> [!NOTE]
> Đoạn này gs muốn nói về **inverse**, và cho biết nãy
> giờ các matrix ví dụ đều là **invertible matrix**, b**ữa
> sau sẽ bàn đến failure case.**

<br>

<a id="node-5hkmnie"></a>

<p align="center"><kbd><img src="assets/i6ut9ryx9i.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, nếu **từ identity matrix**, ta **trừ hàng 2 cho 3 lần hàng 1**
> để được matrix mới (gọi là E đi) mà hàng 2 là [-3 1 0], hai hàng kia giữ
> nguyên [1 0 0] và [0 0 1].
>
>
>
> Thế thì, **matrix nào sẽ giúp đảo ngược quá trình đó**. Hay nói cách
> khác **matrix nào nhân A để cho ra lại I.**
>
>
>
> Thế thì đương nhiên quá trình đảo ngược sẽ là **cộng hàng 2 của A**
> **cho 3 lần hàng 1 của A**. Nên **hàng 2 của matrix cần tìm sẽ là [3 1
> 0]**.
>
>
>
> Còn hàng 1 và 3 của A và I như nhau nên hàng 1 và 3 của matrix cần
> tìm sẽ là [1 0 0] và [0 0 1]

<br>

<a id="node-e8b965t"></a>

<p align="center"><kbd><img src="assets/wjb0j72lbvi.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì ta kí hiệu matrix này là là **E^-1**

<br>

