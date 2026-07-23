# Lecture 2: Neural Classifiers

📊 **Progress:** `58` Notes | `74` Screenshots

---
<a id="node-70u7cna"></a>

## Lecture 2: Neural Classifiers

<br>

<a id="node-ckcq28q"></a>

## Lecture 2: Neural Classifiers

<br>

<a id="node-011il1a"></a>

<p align="center"><kbd><img src="assets/zcztfyfttqi.png" width="80%"></kbd></p>

> [!NOTE]
> "Mục tiêu là sau lecture này các bạn sẽ tự tin mà
> đọc các paper như word2vec, glovec...." Chris Manning

<br>

<a id="node-fhzwmgc"></a>

<p align="center"><kbd><img src="assets/3r336r74j7h.png" width="80%"></kbd></p>

> [!NOTE]
> Như bài trước đã học, bằng cách cho máy tính **dự đoán từ context** **dựa
> trên từ center word**, và quá trình training nó tìm cách **giảm loss** define
> bằng **log likelihood** nó sẽ **"learn" bộ word embedding** sao cho **các từ
> vựng nằm gần nhau** sẽ có ý nghĩa giống nhau mà hơn nữa còn **nắm bắt
> được các yếu tố ngữ nghĩa** cũng như các hướng vector có ý nghĩa (ví dụ
> man - woman sẽ mang ý nghĩa giới tính)

<br>

<a id="node-9kzysbt"></a>

<p align="center"><kbd><img src="assets/f32so5iwss.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là những phương pháp này gọi là **bag of words models**. Nôm
> na là nó **không quan tâm nhiều lắm đến vị trí của các context word là
> trước  hay sau**...Nó c**hỉ quan tâm các từ có xuất hiện gần nhau hay
> không**
>
>
>
> Và một điều là ta sẽ không nói đến các giá trị p 0.3, 0.5 mà sẽ là những
> giá trị nhỏ như 0.01, vì có rất nhiều từ có thể xuất hiện cùng nhau (nôm na
> là **cho một center word thì sẽ có rất nhiều từ có thể xuất hiện trong
> context của nó**) nên **chia ra thì  P rất nhỏ** (dù là so sánh tương đối với
> các từ ít xuất hiện quanh từ center  word đó là cao)

<br>

<a id="node-ux8l3yk"></a>

<p align="center"><kbd><img src="assets/8x3wsgnfjz6.png" width="80%"></kbd></p>

> [!NOTE]
> Đại ý là Word2Vec algorithm trong quá trình training sẽ tìm cách
> **tweak các params (mà ở đây chỉ là các word embedding)** sao cho
> **những từ gần nghĩa nhau** sẽ **nằm gần nhau trong vector space** thì
> sẽ khiến giảm loss và đạt objective function.
>
>
>
> Và thầy Manning lưu ý ta rằng ở đây mình đang xem là dùng **PCA** để
> giảm chiều xuống 2D, tuy nhiên **trong không gian high dimension của
> word embedding thì có thể nó sẽ khác** - 2 từ gần nhau ở 2D có thể thật
> ra là cách rất xa nhau trong không gian gốc

<br>

<a id="node-3qoqt6q"></a>

<p align="center"><kbd><img src="assets/zrx6abv7q1.png" width="80%"></kbd></p>

> [!NOTE]
> Về G.D đã biết rồi khỏi nói lại

<br>

<a id="node-xaixlyl"></a>

<p align="center"><kbd><img src="assets/rjmfbcajmq.png" width="80%"></kbd></p>

<br>

<a id="node-8srupyt"></a>

<p align="center"><kbd><img src="assets/j9ifkz4ypjs.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là như ta đã biết bên **MLSpec** đó là **gradient descent** nếu nói
> chính xác thì đó **batch gradient descent** - tức là ta sẽ **tính gradient**  =
> **derivative của loss** w.r.t **params** với l**oss tính trên toàn bộ data
> sample** mà ở đây là **toàn bộ center words**, và cũng đồng nghĩa là
> **toàn bộ training corpus** và có thể lên tới hàng trăm nghìn từ.
>
>
>
> Thì làm vậy như ta cũng đã biết là sẽ khiến **một lần tính để update params
> sẽ mất rất nhiều thời gian**. Tuy là kiểu như ta **sẽ đi theo hướng đúng
> nhất** về đáy thung lũng n**hưng mỗi bước sẽ phải tính rất lâu**.
>
>
>
> Thì do vậy mà thay vào đó nên dùng **stochastic G.D** hoặc **mini-batch
> G.D** trong đó ta tính gradient (derivative của loss function w.r.t params)
> **dựa trên một hoặc vài data sample thôi, và gọi nó là ước lượng của
> gradient (chính xác)**
>
>
>
> Và vì **chỉ là ước lượng** của gradient chính xác (mà muốn tính phải tính
> trên toàn bộ training set) nên **nó sẽ không chính xác**, **có lúc rất sai**,
> nhưng cũng có lúc đúng và dẫn đến **nó khiến ra đi xuống đồi theo nhiều
> hướng khác nhau mỗi lần**, mà trong đó có thể có những lúc đi rất sai (so
> với hướng đúng phải đi).
>
>
>
> Nhưng **được cái là ta sẽ tốn rất ít thời gian cho một lần "đi"**. Và vì **dù đi
> rất nhiều bước chệch choạc nhưng đi nhiều lần nhìn chung vẫn giúp ta
> xuống đồi nhanh hơn là "suy nghĩ một hồi lâu thiệt lâu chọn ra hướng đi
> đúng nhất" rồi mới bước.**

<br>

<a id="node-v779lih"></a>

<p align="center"><kbd><img src="assets/lvx1geow4i.png" width="80%"></kbd></p>

> [!NOTE]
> Và thêm một ý là mr Chris nói dù SGD có vẻ như là
> hack/trick nhưng thật ra không phải vậy, sự noisy của
> nó thật sự có thể giúp model học tốt hơn chứ không
> chỉ là converge nhanh hơn

<br>

<a id="node-yvi88pm"></a>

<p align="center"><kbd><img src="assets/v9wvh0f8h4j.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với SGD vì **mỗi lần ta chỉ "tính trên 1 sample = 1
> center words"** để ra gradient (partial derivative) của loss đối với
> params = word embedding của vài từ context của center word
> đó. Nên **vector derivative vốn sẽ chứa tất cả params = tất 
> cả các word embedding của các words sẽ phần lớn là 0.**
>
>
>
> Nên rất **sparse** = trống trải.

<br>

<a id="node-98qgqwu"></a>

<p align="center"><kbd><img src="assets/x0vaze2fp2d.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thầy nói nếu chỉ **nghĩ theo phương diện toán học** thì **cứ
> việc thực hiện phép tính cộng trừ vector hay matrix** trên matrix (V,
> d) mỗi row là một word embedding vector.
>
>
>
> Nhưng **để tối ưu tính toá**n thì ta phải **nghĩ đến việc làm sao chỉ
> thực hiện việc update trên vài row mà đang "tính" thôi.**
>
>
>
> Và một chi tiết nữa là trong **Pytorch mỗi word embedding là một
> row**
>
>
>
> Và một điểm đáng chú ý nữa đó là thầy nói nếu các bạn biết về 
> memory thì sẽ hiểu tại sao người ta làm vậy vì khi đó **mỗi row chứa
> một vector của data sample sẽ nằm trên các byte kế tiếp nhau** trên
>  memory máy tính giúp **hiệu quả hơn**

<br>

<a id="node-luzu5xt"></a>

<p align="center"><kbd><img src="assets/crnx74qyfh.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên đại khái là ta cuối cùng ta sẽ **average hai vector của mỗi từ**  một
> cái khi từ đó đóng vai center word, một cái khi nó đóng vai context word, để
> **trở thành một vector duy nhất cho từ đó.**
>
>
>
> Thứ hai, thày nói là **thật ra có thể dùng chỉ một vector cho một từ và thật
> sự làm vậy hiệu quả hơn** nhưng có cái là khiến quá trình thực hiện t**rở
> nên rối khi ta tính đạo hàm.**
>
>
>
> Rồi tiếp theo thì đại khái là không chỉ có một algorithm duy nhất mà thật ra
> **có nhiều cách làm**, trong số đó là **skip gram** như thầy vừa nói mấy bữa
> nay và **CBOW** là cái mình đã học trong NLPSpec trong đó thay vì cho
> trước center  word bắt đoán outer context word thì ta sẽ cho model đoán
> center word dựa trên bag of context words. Cả hai **đều cho cùng kết quả.**
>
>
>
> Cuối cùng đó là tuy lí thuyết là vậy nhưng thực tế khi tính với softmax như
> trên thì sẽ **không hiệu quả (tính toán)**. Do đó thực tế người ta dùng **"
> negative sampling"**

<br>

<a id="node-78y6d6t"></a>

<p align="center"><kbd><img src="assets/3b251ug3tbn.png" width="80%"></kbd></p>

> [!NOTE]
> Thì đại khái là vầy, ta **vẫn muốn maximize độ giống nhau giữa hai word 
> vector của center word và context word**, bằng cách **maximize
> dot product giữa chúng**. Tuy nhiên **thay vì xây dựng objective function
> là maximize P(o|c) bằng softmax** trong đó ta **phải tính dot product của 
> center word với mọi từ khác trong vocab**, **rất tốn kém**, thì ở đây ta sẽ
> xây objective function **với hàm sigmoid** như vầy.
>
>
>
> Trong đó việc maximize function này sẽ **encourage model maximize
> uoTvc bởi vế đầu giúp khiến context word và center word vector
> giống nhau**. Còn vế sau ta hiểu là ta sẽ **lấy random k từ NOT context
> word**, và model sẽ **minimize độ giống nhau của center word và các từ
> "sai" này.**
>
>
>
> Chú ý ở đây là objective function **Jt(theta) với mỗi center word t** , 
> và objective function (cho mọi word) sẽ là **average của mọi Jt(theta)**
>
>
>
> ====
>
>
>
> Nói thêm rằng dù khi chọn k random words có thể ta vẫn đôi khi chọn được
> từ vốn là cũng nên similar với context word (vì có thể nó cùng xuất hiện với
> trong bối cảnh center-context khác) nhưng 99% là ta sẽ chọn những từ "không
> context" nên mọi việc vẫn ok.

<br>

<a id="node-p7c329a"></a>

<p align="center"><kbd><img src="assets/aex180be42k.png" width="80%"></kbd></p>

> [!NOTE]
> Và c**huyển objective function thành cost function**
>
>
>
> Có **một vài trick** mà trong DLSpec ông Andrew cũng có nói đó là người
> ta sẽ **dùng cách sample sao cho giảm việc các từ quá thông dùng được
> chọn và tăng khả năng chọn của các từ hiếm**. Thầy Cris cũng chỉ nói
> lướt qua sơ sơ là bằng cách dùng **unigram distribution** = tính toán
> bằng **tần suất xuất hiện của từ**. Và **lũy thừa 3/4 như vậy để thu hẹp
> khoảng cách giữa các từ hiếm và thông dụng** giúp khi random sampling
> không bị chỉ chọn toàn từ thông dụng.

<br>

<a id="node-bu2yxf3"></a>

<p align="center"><kbd><img src="assets/iglyvebt2ph.png" width="80%"></kbd></p>

> [!NOTE]
> Xong mới đặt câu hỏi là sao không làm đơn giản là t**hống kê
> các lần các từ xuất hiện cùng nhau** để tạo thành co-occurrence
> table

<br>

<a id="node-jtfdkld"></a>

<p align="center"><kbd><img src="assets/be0g5p48658.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ như cái **co-occurrence table** như này. đơn giản chỉ là đếm số lần các
> từ xuất hiện cùng nhau, có thể trong context window là vài từ hoặc cả
> document
>
>
>
> Thì đại khái là nếu dùng dạng window, tức chỉ "tính" phạm vi hẹp vài từ thì ta
> có thể có được "**syntactic & semantic information**" - tức là nó cũng có thể
> giúp ta nắm bắt được ít nhiều thông tin về ngữ nghĩa, cú pháp của từ vựng
>
>
>
> Còn nếu dùng ở "**cấp document**" thì nôm na là ta sẽ có thông tin về sự gần
> gũi của các từ ở cấp "topic", tức là các từ nào cũng trong một phạm vi một
> chủ đề nào đó. Dẫn đến một lĩnh vực gọi là Latent Semantic Analysis

<br>

<a id="node-t9rpstd"></a>

<p align="center"><kbd><img src="assets/zwsckvz22b.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên nếu dùng vector bằng cách này (ví dụ như bảng trên, mỗi hàng
> là  vector của một từ) thì sẽ **rất "sparse"** = trống khi ta thấy nó sẽ **rất nhiều
> số 0 và nó rất dài** (bằng số lượng vocab) = **số dimension rất lớn**.
>
>
>
> Hệ quả là như ta cũng đã nghe nói (dù chưa hiểu rõ lắm) đó là **một số
> model làm việc không tốt với sparse vector.**
>
>
>
> Từ đó ta quay lại khẳng định rằng thực tế chứng minh rằng **dùng "dense"
> vector thấp chiều hơn, "dense" hơn (mà được tạo bằng các phương pháp
> như word2vec) sẽ mang lại hiệu quả hơn.**

<br>

<a id="node-ynuy23w"></a>

<p align="center"><kbd><img src="assets/bv4uyh3lq1q.png" width="80%"></kbd></p>

> [!NOTE]
> Nói về phương pháp dùng SVD để giảm chiều vector
> (dimensionality reduction)

<br>

<a id="node-rv6596y"></a>

<p align="center"><kbd><img src="assets/zy8amcvysu.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu dùng **raw-counts** tức là bảng thống kê co-occurrence 
> nguyên gốc thì sẽ không work tốt, lí do là có quá nhiều từ mang ý nghĩa 
> **"chung chung"** như the, he, has sẽ có tần suất xuất hiện cao, khiến gây
> nhiễu thông tin. Do đó mới nói là **sẽ tốt hơn nếu scale các chỉ số lại
> ví dụ như dùng log**, dùng cách giới hạn hạn mức hoặc là bỏ luôn các từ
> chung chung như vậy (function words) 
>
>
>
> Một số cách khác nữa là dùng window nhỏ, và use **Pearson correlation**

<br>

<a id="node-7fxwvpo"></a>

<p align="center"><kbd><img src="assets/i7w0vh9k7f.png" width="80%"></kbd></p>

> [!NOTE]
> Thì đại khái là cũng cho thấy một số kết qủa mang hơi
> hướng giống như king-queen-man-woman

<br>

<a id="node-yzmdzdo"></a>

<p align="center"><kbd><img src="assets/ehm6ezeb69.png" width="80%"></kbd></p>

<br>

<a id="node-wix2l85"></a>

<p align="center"><kbd><img src="assets/7bmmzx2yfpx.png" width="80%"></kbd></p>

<br>

<a id="node-pcsmjat"></a>

<p align="center"><kbd><img src="assets/7rhwglqm8q.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về một nhận định quan trọng trong nỗ lực tìm cách " **thể hiện các
> khái niệm trừu tượng**" gọi là "meaning component" ví dụ như **hướng thay đổi từ
> man sang woman** (mang ý niệm giới tính), hay **solid sang gas**, mang **ý niệm trạng
> thái vật lí.**
>
>
>
> Thì đại khái là nếu ta chỉ dùng (cách tính) xác suất một từ xuất hiện gần từ "ice" là
> một từ mang thể rắn trong vậy lí- P(solid | ice) và lập luận rằng vì solid mang giá
> trị cao để thể  hiện rằng nó **mang ý nghĩa của thể rắn** thì sẽ không ổn. Vì như đây
> ta thấy với "water" thì nó cũng hay xuất hiện bên cạnh "ice" nên P(water|ice) cũng
> cao trong khi đó water có thể là dạng hơi hoặc dạng lỏng nữa.
>
>
>
> Tương tự, nếu chỉ dựa vào P(gas|steam) cao thì nôm na là **chưa đủ để biểu thị  ý
> nghĩa gas là thể hơi**. Vì P(water|steam) cũng cao.
>
>
>
> Tuy nhiên người ta nhận thấy **nếu dựa vào tỉ lệ của P(x|ice)/P(x|steam)** thì ta sẽ
> thấy rõ ràng rằng với solid, nó có tỉ lệ cao, với gas nó có tỉ lệ rất nhỏ. Còn water và
> fashion thì đều ~= 1
>
>
>
> Từ đó cho thấy rằng dùng tỉ lệ, sẽ làm rõ thông tin rằng **từ solid là từ mang ý nghĩa
> rắn rất cao**, và **gas là từ mang ý nghĩa hơi** (như steam) rất cao còn **water thì
> fashion là trung tính**, không thiên hẵn về bên nào.
>
>
>
> Và tóm lại ta có thể **dựa vào tỉ lệ này để xem thử 1 từ thiên về hướng nào trong
> spectrum từ solid -> gas**

<br>

<a id="node-6aaetkl"></a>

<p align="center"><kbd><img src="assets/ma4kinci8q.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là vì ta đã biết dot product của hai vector uo, vc sẽ thể hiện **xác suất của
> việc chúng xuất hiện cùng nhau**, đúng hơn là log của xác suất vì khi ta tính xác
> suất, p(o|c) ta dùng softmax, trong đó ta exp(uoTvc). Mà nói lại cho nhớ thêm đó
> là bởi ta xuất phát từ một nhận định quan trọng đó là **ý nghĩa của một từ sẽ được
> định nghĩa bằng các từ gần nó**, từ đó **nếu hai từ hay xuất hiện gần nhau thì ý
> nghĩa của chúng cũng gần gũi nhau, giống nhau**. Nên từ đó ta xây dựng
> objective function sao cho nếu xác xuất chúng xuất hiện cùng nhau cao thì **hai
> vector của chúng phải trở nên giống nhau**,  gần gũi nhau trong không gian
> embedding vector. Thì hai vector gần nhau thì dot product của chúng sẽ lớn
> (cũng như khi tính Cosine similarity trong đó có dot product)
>
>
>
> Do đó để tính P(x|a)/P(x|b) sẽ bằng **wx.(wa-wb)**
>
>
>
> Thì đại khái là GloVec muốn **kết hợp cái gọi là Co-occurrence matrix** trong các
> phương pháp xây dựng word vector theo thống kê (statistic) như mấy cái bên trái
> của cái bảng trước. **Và phương pháp xác suất như CBOW,  Word2Vec** ở bên
> phải bảng trước. Do đó học xây dựng objective function như vầy.
>
>
>
> Cái f(Xij) từ từ nói, nói cái Xij trước, nó là chỉ số co-occurrence của từ w_i và từ
> w_j trong co-occurrence matrix. Thì đương nhiên nếu hai từ hay xuất hiện cùng
> nhau thì chỉ số này cao.
>
>
>
> Thì vế bên phải mang ý định nôm na là: À, hay tweak word embedding vector
> của w_i và w_j sao cho **nếu hay từ này xuất hiện cùng nhau nhiều** thì **dot
> product của chúng phải cao tương ứng** (để rồi trừ nhau mới nhỏ lại). Bình
> phương lên để kiểu **khuếch đại error lên như trong MSE**. Hai cái **b là bias term**
> không  có gì, đương nhiên model cũng sẽ tìm ra hai chỉ số này.
>
>
>
> Cuối cùng quay lại f**(Xij)** đại khái chỉ là một function để ta **khống chế các từ thông
> dụn**g, bên DLSpec có nói đó là để g**iảm chênh lệch giữa các từ thông dụng và
> các từ ít thông dụn**g.Theo GPT thì người ta hay dùng **sigmoid**, trong đây Crist có
> nói **f(Xij)** dùng để **"cap" mức ảnh hưởng của các từ thông dụng**. Nhìn công thức
> mình hiểu rằng, **nếu (những từ wi và wj mà có Xij lớn thì phải cho model tập
> trung vào nó, tức là dùng Xịj như trọng số để ưu tiên hơn / nhấn mạnh hơn các
> cặp từ hay xuất hiện cùng nhau)**. Nhưng **phải hạn chế nó, bằng cách dùng f(Xij)
> để cho nó (Xij) có lớn mấy thì mức ảnh hưởng vào objective function cũng chỉ =
> 1 thôi**
>
>
>
> Và một cái ở đây Crish không nói nhưng Andrew có nói đó là tránh việc X**ij = 0
> sẽ khiến logXij = log0 bị lỗi**

<br>

<a id="node-y6hnkbs"></a>

<p align="center"><kbd><img src="assets/ptd17nojif.png" width="80%"></kbd></p>

> [!NOTE]
> Và kết quả là nó cho word vector rất tốt khi những từ
> này (gần nhau trong không gian) thì đúng đều là những
> loài ếch khác nhau

<br>

<a id="node-hu5tqoa"></a>

- **Ở đây có người hỏi đại khái là tại sao việc dùng các chỉ số statistic
(co-occurrence matrix) lại là cons là ưu điểm hỗ trợ cho Skip-gram

Thì đại khái đó là vì, trong skipgram như ta đã thấy, quá trình sẽ là ta
di chuyển các window qua hết corpus, để tại mỗi window ta có center
word và context words. Để rồi nôm na là tại mỗi window ta mới biết từ
nào là hay xuất hiện với từ nào.

Còn bằng cách sử dụng co-occurrence matrix, ta đã có sẵn à là từ
này hay xuất hiện nhiều với từ kia, nên sẽ kiểu như "trực tiếp hơn", ta
khỏi phải đi từng window mà có thể làm "at once" dẫn đến hiệu quả
hơn trong training**

<br>

<a id="node-xpu7k98"></a>

<p align="center"><kbd><img src="assets/cbaigtc08w.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về các cách để đánh giá word vector mà cũng là các khía
> cạnh khác trong ML.
>
>
>
> Cái này cũng đã biết qua bên MLOpsSpec, thì đại khái là intrinsic nôm na
> là ta đánh giá bằng các task cụ thể (specific) được thiết kế riêng cho việc
> đánh giá word vector. Ưu điểm là nhanh, nhưng nhược điểm là nó mang
> tính cục bộ, ta không biết được kiểu như là à, word vector đánh giá bằng
> cách này ok rồi, nhưng liệu khi mang nó vào các ứng dụng ngoài đời
> thực thì nó có giúp cải thiện performance của chúng không.
>
>
>
> Còn extrinsic thì ngược lại, đó là đánh giá chất lượng của word vector
> thông qua việc xem nó có giúp cải thiện các ứng dụng cụ thể thực tế
> (như dịch thuật, semantic search) Nhược điểm là phải xâu dựng ứng
> dụng cuối thì mới đánh giá được, nên lâu. Và nếu performance có tốt lên
> hay dở đi thì cũng không chắc là do word vector tốt lên hay đơn giản chỉ
> vì những cái component khác làm việc tốt hơn so với cái cũ

<br>

<a id="node-tejp9r4"></a>

<p align="center"><kbd><img src="assets/ck9av62dtkk.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ điển hình của intrinsic evaluation là có có man to woman thì từ
> king tìm ra cái gì, và ta expect sẽ ra queen.
>
>
>
> Ở đây mr Chris nói một cái trick đó là,  khi các bạn tính wMan -
> wWoman + wKing rồi tìm nearest neighbor của kết quả đó thì khả
> năng đó là bạn sẽ lại thấy từ King, nên cái trick là là đừng có include
> từ king khi search.

<br>

<a id="node-30erbkg"></a>

<p align="center"><kbd><img src="assets/6erxrpk139t.png" width="80%"></kbd></p>

<br>

<a id="node-7t40bdw"></a>

<p align="center"><kbd><img src="assets/eg0xg4gn3tb.png" width="80%"></kbd></p>

<br>

<a id="node-a5zfcgv"></a>

<p align="center"><kbd><img src="assets/mlbvhsaatxj.png" width="80%"></kbd></p>

<br>

<a id="node-u7f9ms8"></a>

<p align="center"><kbd><img src="assets/mza71g208tt.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là bảng tính các chỉ số đánh giá word vector ở khía
> cạnh Semantic và Syntatic. Cho thấy GloVe đạt performance
> cao nhất, sau đó là SkipGram và CBOW
>
>
>
> Ở khúc trên SVD (bài trước đã nói, là dùng phương pháp 
> dựa trên co-occurence table, cho thấy nếu không scale, tức
> giảm ảnh hưởng của các từ thông dụng xuống thì performance
> rất tệ, nhưng khi scale thì cải thiện hơn hẳn

<br>

<a id="node-xdqx997"></a>

<p align="center"><kbd><img src="assets/1v52fnjvqe1.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về ảnh hưởng của **data lên performance**. Khi model
> train trên **Wiki data** có **semantic scores cao hơn** còn model train trên
> **google news** thì có **syntactic score cao hơn**. Và model train bằng web
> crawl (lấy hết data trên internet) thì tốt hơn cả ở hai khía cạnh.

<br>

<a id="node-nqzaohm"></a>

<p align="center"><kbd><img src="assets/0pvkrjnb3vdi.png" width="80%"></kbd></p>

> [!NOTE]
> Còn cái biểu đồ này cho thấy tại sao ta hay thấy người
> ta dùng dimension 300. Vì nhiều hơn thì  nó không hẳn
> là tốt hơn nữa

<br>

<a id="node-cb5klzj"></a>

<p align="center"><kbd><img src="assets/kbwvmt3405f.png" width="80%"></kbd></p>

> [!NOTE]
> Một cách intrinsic word vector evaluation nữa đó là dựa trên
> các đánh gía (do con người làm) về độ tương đồng của các từ

<br>

<a id="node-l2xew5a"></a>

<p align="center"><kbd><img src="assets/s6ifku2axs9.png" width="80%"></kbd></p>

<br>

<a id="node-80ybdad"></a>

<p align="center"><kbd><img src="assets/dp4kjjyom7q.png" width="80%"></kbd></p>

<br>

<a id="node-v8xt2h2"></a>

<p align="center"><kbd><img src="assets/bwn7m31euub.png" width="80%"></kbd></p>

> [!NOTE]
> Nói đến vấn đề đặt ra là **từ vựng thường có nhiều nghĩa khác nhau** khi
> ở các n**gữ cảnh khác nhau** thì làm sao 1 vector có thể capture mọi ý
> nghĩa đó

<br>

<a id="node-nke0xiu"></a>

<p align="center"><kbd><img src="assets/ll57bouq17f.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ như từ pike có nhiều nghĩa khi ở các
> ngữ cảnh, lĩnh vực khác nhau

<br>

<a id="node-cfj6bux"></a>

<p align="center"><kbd><img src="assets/y81wd2j6o5c.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói đến việc dùng mỗi word vector cho
> mỗi khía cạnh / trường nghĩa / lĩnh vực khác nhau
> của từ

<br>

<a id="node-m4idlm3"></a>

<p align="center"><kbd><img src="assets/7cjy9fefhep.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là một cách đó là weighted sum tụi nó lại theo weight tính bởi
> frequency
>
>
>
> Và sparse coding đại khái nói là trong vector space thật sự ra hóa ra là
> Ta có thể phân tách từ vector spice chung chung (weighted sum) thành
> các component cho các nghĩa của nó. Kiểu như nếu nói 17 là sum của 3
> số thì trong không gian 1D ta không thể biết 17 là tổng của 3 số nào
> nhưng trong không gian cao chiều hơn thì hóa ra có thể làm cái việc
> phân tách này.
>
>
>
> Ví dụ tie có thể được phân tách ra thành các sub vector mà trong đó
> người ta thấy nó gần gủi với các vector của các từ trong các cột từ đó
> cho thấy các nghĩa khác nhau của từ tie

<br>

<a id="node-zn4l0pm"></a>

## Lecture Note: Glove, Evaluation & Training

<br>

<a id="node-s2pf94p"></a>

<p align="center"><kbd><img src="assets/oohjbwzi36b.png" width="80%"></kbd></p>

<br>

<a id="node-zaa1mek"></a>

<p align="center"><kbd><img src="assets/zqv0cknuml.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/hglwsbfutd.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là các word vector tạo bởi các mode**l dựa trên các thông số thống kê
> statistic như LSA, HAL làm tốt trên các task thể hiện được  độ giống nhau giữa
> các từ nhưng lại không làm tốt được các task về word analogy.**
>
>
>
> Ngược lại các model như CBOW, SkipGram c**ó thể làm tốt trong việc tạo các
> word vector phản ánh được các semantic meaning** của từ vựng thì lại **không
> tận dụng được các chỉ số thống kê như co-occurence matrix**.
>
>
>
> Thì **GloVe model kết hợp cả hai** giúp khắc phục được nhược điểm của các
> model trên.

<br>

<a id="node-ttwsy2v"></a>

<p align="center"><kbd><img src="assets/ciy5rduroa8.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về việc **tạo co-occurence matrix X** trong đó **Xij là số
> lần xuất hiện của từ wj bên cạnh (gần) từ wi**
>
>
>
> Và nếu mình tính **tổng hàng i của X**, để rồi **chia các giá trị trong hàng
> i của X cho tổng Xi** này ta sẽ có c**ác chỉ số tổng = 1**, mang hình hài
> là **xác suất của các từ trong V xuất hiện bên cạnh từ w_i.**
>
>
>
> Thì đây là **xác suất tính theo statistic**, khác với **xác suất do model 
> train / learn được.**
>
>
>
> thì nôm na với cách tạo c.o matrix này thì vớ**i bộ dữ liệu lớn sẽ rất tốn
> kém nhưng nó chỉ phải làm lần đầu thôi**

<br>

<a id="node-vkux2ro"></a>

<p align="center"><kbd><img src="assets/0anivw5b3oqr.png" width="80%"></kbd></p>

> [!NOTE]
> Diễn giải loss function J sẽ là: (Âm) Tổng: Với **mỗi từ thứ i** trong
> corpus, và **với mỗi từ j trong cùng context với thứ i**, ta tính **log
> Qij** và tổng lại hết. Và tổng lại hết với mọi i. Q là xác suất có điều
> kiện Q(w_i | w_j) (ở đây dùng chữ Q vì đặng tí nữa ý nói ta sẽ thu
> hẹp khác biệt giữa hai phân phối xác suất P,Q)

<br>

<a id="node-w77pal7"></a>

<p align="center"><kbd><img src="assets/6xhm9gjfe0y.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì đại khái là với việc các **cặp từ i, j cùng xuất hiện với nhau** trong cùng
> context **ở nhiều chỗ trong corpus**, nên ta **lấy tổng** số lần chúng xuất hiện cùng
> nhau từ C.O matrix **Xij** **nhân với logOij** (và tổng với mọi từ) thì cũng chính là J.
>
>
>
> Hiểu nôm na là trong công thức trước là tính TỔNG, 1 lần xuất hiện cùng nhau
> ở đây (nhân với logQij), cộng 1 lần nữa xuất hiện cùng nhau ở kia (nhân với
> logOij), thì cơ bản chính là lấy 2 lần xuất hiện cùng nhau (từ C. O matrix) (nhân
> với logOij)
>
>
>
> Thế thì nhắc lại cái như đã biết, để tính Qij theo công thức softmax thì ta phải
> tính "với mọi từ trong vocab - phép uw.vc" rất tốn kém. Nên người ta nghĩ ra kiểu
> khác.

<br>

<a id="node-iz0lsjy"></a>

<p align="center"><kbd><img src="assets/e3ri2bj2e0q.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái người ta nảy ra ý tưởng đó là "ta sẽ giảm loss, sao cho ta sẽ
> **giảm cách biệt giữa phân phối xác suất thật** (mà hai từ i, j xuất hiện
> cùng lúc) và **phân phối xác suất đang tính bởi các word vector từ U và V**
>
>
>
> Nói đúng hơn là **ước lượng phân phối xác suất thật** (nên người ta mới
> để **P^ij**, vì ta **không thể có xác suất thật mà chỉ có thể ước lượng** dựa vào
> **chỉ số statistic từ C.O matrix (P^ij = Xij)**. 
>
>
>
> Và **Qij** bây giờ **cũng thành "ước lượng" luôn** Q^ij ta **chỉ dùng cái "vế" tử số
> trong công thức là exp(uj.ui)**, bỏ cái mẫu số đi, trên **tinh thần là "ước lượng" 
> vì để xác suất nó cao thì tử số cũng phải cao**. Còn **mẫu số tạm thời không care**
>
> Và để gọi là **penalize error** thì người ta b**ình phương sai khác giữa P^ij
> và Qij** lên giống như MSE vậy. Nên gọi là **least square**
>
>
>
> Và **Xi** (tổng các gía trị của hàng i trong X) được hiểu nôm na họ muốn
> dùng nó làm **trọng số "weighted" cho từ i**. Kiểu như là **"từ nào mà có chỉ
> số này lớn tức là từ đó sẽ có tình trạng có nhiều từ vây quanh hơn**, **"nhiều
> bạn hơn" thì tập trung (khi giảm loss) nhấn mạnh vào các từ này hơn.**
>
>
>
> Ví dụ như có từ A và từ B, trong đó A thì có nhiều bạn, số từ hay xuất hiện 
> cùng nó thì cũng có nghĩa là từ A phổ biến trong ngôn ngữ hơn là một từ
> hiếm khi xuất hiện B. Vậy thì model hãy tập trung improve các từ A hơn
>
>
>
> Thế nhưng dùng chỉ số của Xịj  thường lớn nên gây khó cho bài toán optimization
> thành ra người ta dùng log

<br>

<a id="node-kn8jnqb"></a>

<p align="center"><kbd><img src="assets/cgezg8h0pnj.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì nó ra vầy, và **vì đã square lên nên đổi chỗ hai thằng** không sao
> Và vì **log Q^ij = log exp uj.ui = uj.ui.** (Như nói ở bên kia, ta đã tạm thời
> không care cái mẫu số nữa rồi nên Q^ij (mà các bài trước ta gọi là
> Pij hay P(w_i|w_j) sẽ chỉ là exp(u_wi.v_wj) thôi)
>
>
>
> Và cuối cùng đó là người ta nói nếu để Xi = tổng các Xij của hàng i làm
> weight để n**hấn mạnh / ưu tiên giảm loss ở các từ thông dụng** thì còn một
> vấn đề không ổn đó là ta **cũng nhấn mạnh vào những từ quá thông dụng** 
> như những từ chung chung the, an, he, she. Thế là người ta **dùng function
> f(Xij) để khống chế trọng số sao cho nó vẫn tăng ảnh hưởng vào loss của
> các từ thông dụng hơn** những từ hiếm **nhưng đừng quá nhấn mạnh các 
> từ quá thông dụng**
>
>
>
> Và function f này có thể tùy trường hợp mà áp dụng các công thức khác nhau

<br>

<a id="node-0qqy1ej"></a>

<p align="center"><kbd><img src="assets/zxl6vrfeoe.png" width="80%"></kbd></p>

> [!NOTE]
> Tóm lại cái GloVe model **vừa xài các statistical information** từ Có
> và dùng nó trong cách train ra word vector bằng probabilistic model
> giúp khắc phục các nhược điểm của cả hai phương pháp.
>
>
>
> Performance của nó tốt hơn của Word2Vec model khác như SkipGram
> CBOW

<br>

<a id="node-70ogiba"></a>

<p align="center"><kbd><img src="assets/5cb59ntj13w.png" width="80%"></kbd></p>

<br>

<a id="node-z20nu25"></a>

<p align="center"><kbd><img src="assets/ye4lfx7fkg.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu muốn check chất lượng của các word vector một
> cách dựa vào kết quả cuối, trong đó ta đưa nó vào, sử dụng nó
> trong một hệ thống học máy để làm một tác vụ nào đó như Q&A
>
>
>
> Thế thì vấn đề là khi đó ta phải cơ bản là hyper-param tuning các
> h.p như word dimension trong hệ thống lớn này luôn thì mới hiệu quả
> nhưng việc training một mô hình từ đến cuối vậy rất lâu và tốn kém
> dẫn đến việc này sẽ không khả thi.

<br>

<a id="node-uem2ip5"></a>

<p align="center"><kbd><img src="assets/n19rnkc95w.png" width="80%"></kbd></p>

> [!NOTE]
> Thứ hai nữa là vì sử dụng trong hệ thống lớn có thể liên quan nhiều bộ
> phận khác cũng sẽ khiến việc đánh giá performance của word vector
> khó hơn.
>
>
>
> Do đó người ta tìm các tạo các intrinsic evaluation giúp đánh giá vector
> nhanh hơn

<br>

<a id="node-eadidyg"></a>

<p align="center"><kbd><img src="assets/zv1o4c983ld.png" width="80%"></kbd></p>

<br>

<a id="node-wf50lry"></a>

<p align="center"><kbd><img src="assets/0q1h56f205fd.png" width="80%"></kbd></p>

<br>

<a id="node-xjs1yk4"></a>

<p align="center"><kbd><img src="assets/vyg9mfyek5h.png" width="80%"></kbd></p>

<br>

<a id="node-cjf5xc3"></a>

<p align="center"><kbd><img src="assets/a1d13stf15.png" width="80%"></kbd></p>

<br>

<a id="node-uafzvkg"></a>

<p align="center"><kbd><img src="assets/2b0v1xbxped.png" width="80%"></kbd></p>

<br>

<a id="node-tl6ojtr"></a>

<p align="center"><kbd><img src="assets/3eop5zvhvyd.png" width="80%"></kbd></p>

> [!NOTE]
> kết quả ví dụ về
> Syntactic - cú pháp

<br>

<a id="node-p20i374"></a>

<p align="center"><kbd><img src="assets/3dcva4qv3sg.png" width="80%"></kbd></p>

> [!NOTE]
> So sách các model với
> các hp khác nhau

<br>

<a id="node-kfwawvu"></a>

<p align="center"><kbd><img src="assets/ege4fe7g7wi.png" width="80%"></kbd></p>

> [!NOTE]
> 3 nhận xét, một là các model khác nhau thì performance cũng
> khác, điều này là dễ hiểu vì mỗi cái có một cách làm
>
>
>
> Thứ hai là khi corpus càng lớn thì performance càng tốt, điều 
> này cũng dễ hiểu
>
>
>
> Thứ ba là nếu dimension vector nhỏ quá thì cũng không tốt
> đại khái là giống như vấn đề bias dùng model đơn giản quá 
> cho bài toán phức tạp sẽ khiến không đủ sức để nắm bắt 
> quy luật

<br>

<a id="node-trs2p2q"></a>

<p align="center"><kbd><img src="assets/q6maxzg7cdd.png" width="80%"></kbd></p>

> [!NOTE]
> biểu đồ này cho thấy training time sẽ
> giúp cải thiện performance

<br>

<a id="node-s7k31h1"></a>

<p align="center"><kbd><img src="assets/0h3q1at3dfhm.png" width="80%"></kbd></p>

> [!NOTE]
> Corpus lớn khiến
> performance tăng

<br>

<a id="node-nkosh5v"></a>

<p align="center"><kbd><img src="assets/kqgxihb7w5i.png" width="80%"></kbd></p>

> [!NOTE]
> Cho thấy dimension vector tầm 300 là ok, cao hơn nữa
> cũng không tăng thêm mấy nhưng sẽ gây tốn kém tính toán

<br>

<a id="node-gbh8ggi"></a>

<p align="center"><kbd><img src="assets/rlplil0v56e.png" width="80%"></kbd></p>

> [!NOTE]
> Window size tầm 8 là ổn

<br>

<a id="node-6cnvmwf"></a>

<p align="center"><kbd><img src="assets/8xzt9mwgojt.png" width="80%"></kbd></p>

> [!NOTE]
> 1 cách khác là dùng
> human để đánh giá

<br>

<a id="node-coy7gr3"></a>

<p align="center"><kbd><img src="assets/yosekwagpu.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/n40whwjmoom.png" width="80%"></kbd></p>

<br>

<a id="node-4yf40ho"></a>

<p align="center"><kbd><img src="assets/quf5apv2euj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về extrinsic task trong đó ta sẽ dùng các nhiệm vụ cuối để
> đánh giá model. Nhưng ở đây là nói về một cái mà mình cũng từng để ý
> đó là thông qua việc training một vấn đề cuối (mang tính ứng dụng) là
> giúp tạo ra hoặc cải thiện bộ word vector.
>
>
>
> Ví dụ người ta sẽ xây dựng model cho task classification cụ thể như là
> NER hay sentiment analysis, với labeled dataset. Để rồi không như các 
> mô hình học máy điển hình khác trong đó ta giữ training set fixed, và chỉ
> Thay đổi weights trong quá trình training. Còn ở đây nó sẽ re-train input
> word vector bên cạnh train bộ params

<br>

<a id="node-44b6xfd"></a>

<p align="center"><kbd><img src="assets/2wxj35k4uh2.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên có chú ý quan trọng đó là nếu sử dụng bộ pre-train word vector
> (ví dụ như từ SkipGram hay GloVe) và re-train trong một mô hình với
> extrinsic task như vậy thì phải đảm bảo dataset phải đủ lớn nếu không thì
> ta sẽ làm hư bộ word vector. Lí do là vì word vector pre-train với large corpus
> thì nó phản ánh phân phối xác suất ước lượng của từ vựng (xuất hiện bên cạnh
> nhau)
>
>
>
> Tuy nhiên nếu retrain lại với small dataset - trong đó phân phối xác suất không
> đúng (do ít data quá không mang tính đại diện) có thể làm thay đổi word vector.

<br>

<a id="node-5xe34ak"></a>

<p align="center"><kbd><img src="assets/w2z8oeodfi.png" width="80%"></kbd></p>

> [!NOTE]
> Không có gì khó hiểu, đây là nói về việc tính xác suất input x là/thuộc 
> một class trong C class (hay viết theo kiểu khác là xác suất giá trị tại j 
> trong C giá trị của vector y là 1) sẽ dùng hàm softmax với input là logit
> là score tính từ phép dot product của vector hàng thứ j trong matrix W
> và vector x (cái này là linear classifier như đã học ở tuần 1 bên CS231N)
>
>
>
> Thế thì loss sẽ dùng cross entropy loss: SUM y*log(y^) và vì y là one-hot
> vector, nên công thức có thể viết thành - log y^[k] với k là index của class
> đúng.
>
>
>
> Và tính loss cho mọi datapoint ta sẽ có loss function, trong đó người ta
> dùng k(i) ý là function tính ra index của correct class của data sample x(i)

<br>

<a id="node-8ezeztu"></a>

<p align="center"><kbd><img src="assets/yx1ljv6g8in.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với một simple linear classifier như này với chỉ matrix W và b
> (hay viết gộp là W khi cho b thành 1 cột của W luôn) thì ta sẽ có số
> params của model là Cxd vì W có shape là C hàng, mỗi hàng như bên
> CS224 đã học là một linear classifier cho một class. Vã d là số cột chính
> là số feature cũng là embedding vector dimension. (tức input là word vector)
>
>
>
> Rồi như đã nói ở đây ta cũng re-train lại word vector, thành ra với |V| từ, mỗi từ
> là d-dimension vector thì có |V|*d params phải retrain.
>
>
>
> CỘng lại ta có C*d + |V|*d params là rất lớn, thì họ nói với số params nhiều
> vậy thì model rất dễ bị overfit

<br>

<a id="node-1iof6xl"></a>

<p align="center"><kbd><img src="assets/fjjpdvbw4d.png" width="80%"></kbd></p>

> [!NOTE]
> Thành ra có thể dùng regularization để giảm overfit Ở đây họ nói một ý
> mà bên Cs231 ko nói đó là 'theo Bayesian" thì params mà nhỏ thì tốt
> hơn. Trong công thức này không có gì lạ, như bên cs231 đã học, 
> họ dùng L2 regularization - đó là add reg term vào loss, trong đó tính sum
>  square mọi params . Tham số hp lambda phải h.p tuning

<br>

<a id="node-bldunnv"></a>

<p align="center"><kbd><img src="assets/q8xw9cbacl.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/cnlf28s67og.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái ý tưởng là việc dùng single word cho training không thực tế
> lắm khi thực sự thì bối cảnh (context) của từ cũng đóng vai trò quan
> trọng trong việc xác định meaning cuả nó
>
>
>
> Nên ý tưởng ở đây là họ sẽ dùng một input là array cụm word vector
> bao gồm cả center word và vài context word gọi là window classification
>
> Để rồi khi tính derivative của loss ư.r. t vector các từ trong
> cụm này và dùng nó để update word vector của chúng

<br>

<a id="node-zqnaoka"></a>

<p align="center"><kbd><img src="assets/ep2d89hpiv.png" width="80%"></kbd></p>

> [!NOTE]
> Giới thiệu qua non-linear
> classifier như NN

<br>

<a id="node-w7f443a"></a>

## Reading: Glovec:  Global Vectors For Word Representation
(glove Paper)

> [!NOTE]
> Quay lại sau

<br>

<a id="node-mtnecqd"></a>

## Reading: Improving Distributional Similarity With Lessions
learned From Word Embeddings

> [!NOTE]
> Quay lại sau

<br>

<a id="node-0nimboz"></a>

## Reading: Evaluation Methods For Unsupervised Word Embeddings

> [!NOTE]
> Quay lại sau

<br>

