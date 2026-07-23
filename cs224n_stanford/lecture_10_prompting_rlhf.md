# Lecture 10: Prompting & RLHF

📊 **Progress:** `51` Notes | `63` Screenshots

---
<a id="node-abd4qiy"></a>

## Lecture 10: Prompting & RLHF

<br>

<a id="node-573uuqm"></a>

<p align="center"><kbd><img src="assets/ur09pmgexup.png" width="80%"></kbd></p>

<br>

<a id="node-dasn0pi"></a>

<p align="center"><kbd><img src="assets/0yfdp8n73f1.png" width="80%"></kbd></p>

<br>

<a id="node-zjptpdh"></a>

<p align="center"><kbd><img src="assets/sqhgr5glig.png" width="80%"></kbd></p>

<br>

<a id="node-vcd21li"></a>

<p align="center"><kbd><img src="assets/eyjrn8hcu0w.png" width="80%"></kbd></p>

<br>

<a id="node-ctq6bw7"></a>

<p align="center"><kbd><img src="assets/104z0k23k4wg.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi là làm sao ta có thể huấn luyện một language
> model từ việc chỉ dự đoán từ tiếp theo, có thể trở thành một
> multi-task assistant như ChatGPT?

<br>

<a id="node-uglakh8"></a>

<p align="center"><kbd><img src="assets/h4nzwjb55jv.png" width="80%"></kbd></p>

<br>

<a id="node-iflbuyb"></a>

<p align="center"><kbd><img src="assets/n9fikya2duk.png" width="80%"></kbd></p>

> [!NOTE]
> nhắc lại một chút về llm khi mô hình GPT của openAI, với kiến trúc
> thuần túy transformer decoder, được huấn luyện với nhiệm vụ predict
> next word trên BooksCorpus dataset.
>
>
>
> Điểm chính muốn nhấn mạnh là sự thành công của GPT cho thấy một
> tiềm năng của llm khi chỉ thông qua cơ chế Pretrained-Finetuning, với
> bước  Pretrain trên nhiệm vụ dự đoán từ tiếp theo theo lối
> self-supervised và finetune  trên nhiệm vụ vụ thể theo lối supervised
> đã cho thấy mô hình đạt được hiệu suất rất tốt trên nhiệm vụ đó, hơn
> là khi chỉ được supervised với một nhiệm  vụ cụ thể ngay từ đầu.

<br>

<a id="node-exzescz"></a>

<p align="center"><kbd><img src="assets/qbz2qw3m7pq.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó GPT2 ra đời 2019, với kiến trúc lớn hơn 1.5B params, train với dữ
> liệu nhiều hơn nhiều cũng như là thay vì lấy từ internet một cách không
> kiểm soát thì ở đây họ có cơ chế mang tính chất nôm na là "ít nhiều có sự
> đánh giá của human" trong chất lượng của bài viết kiểu như chỉ lấy những
> bài viết có ít nhất 3 votes của reddit.

<br>

<a id="node-903ntku"></a>

<p align="center"><kbd><img src="assets/l08tsiy3oea.png" width="80%"></kbd></p>

> [!NOTE]
> nói về một khả năng nổi bật của GPT-2 là zero-shot learning, được định nghĩa
> đại khái là khả năng của llm có thể thực hiện nhiều task khác nhau mặc dù
> không hề có ví dụ (no example), hay fine-tuning cụ thể cho nhiệm vụ đó (no
> gradient-updates)
>
>
>
> ví dụ như ở đây, ta có thể hỏi LLM: "Con mèo không vừa với cái nó vì nó quá
> to" thì từ "nó" chỉ cái nón hay con mèo? Thế thì cơ bản là LLM sẽ tính xác
> suất của hai câu "...vì con mèo quá to" và "...vì cái nón quá to" để rồi nó cho 
> ra kết luận là "con mèo". 
>
>
>
> Ý chính là muốn nhấn mạnh dù pretraining hay finetuning không hề có một
> câu hỏi tương tự vậy, nhưng llm vẫn có khả năng trả lời được.

<br>

<a id="node-ttv92bw"></a>

<p align="center"><kbd><img src="assets/damrzt7qr8i.png" width="80%"></kbd></p>

> [!NOTE]
> cụ thể là gtp2 k(chỉ pretrained, chưa finetuning với task cụ thể nào) vẫn có
> thể vượt khả năng của mô hình SoTA trong những benchmark như
> LAMBADA (là nhiệm vụ dự đoán từ được thiết kế để làm tốt mô hình cần
> nắm bắt long-range dependency tốt)

<br>

<a id="node-fo8f2p5"></a>

<p align="center"><kbd><img src="assets/f04cxjnt17j.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi một ví dụ rất thú vị là về task summarization, dù GPT2 như đã nói  chưa hề
> được finetuning ở nhiệm vụ này, nhưng nó vẫn có thể làm tốt.
>
>
>
> Lí do là bởi trong training set (pretraining), có những chỗ (ví dụ như trên
> Reddit, người ta viết theo kiểu
>
>
>
> ...(một bài viết dài) ....TL;DR: ..(một bài ngắn tóm tắt lại).. (TL,DR viết tắt  của
> Too long, didn't read:)
>
>
>
> là khi người ta tóm tắt lại bài viết dài (nhằm để **người khác xem cho dễ**,
> đừng có lộn với việc con người chuẩn bị data cho việc finetuning llm nhé)
>
>
>
> Thì ý là lúc pretraining, LLM trong nhịệm vụ dự đoán từ tiếp theo đã gặp và
> được huấn luyện cho nhiệm vụ summarization này rồi, vì tuy là dưới hình thức
> dự đoán next token, nhưng để làm đúng ở "khúc này" thì nó phải hiểu, và tóm
> tắt được đoạn văn trước đó, vì như đã nói, khúc này "target" là một đoạn tóm
> tắt mà người dùng reddit tóm tắt lại.
>
>
>
> ===
>
>
>
> Và anh này nói đây cũng **chính là một kiểu như "dấu hiệu" / "dạng" của kĩ
> thuật prompting** phổ biến hiện nay, **khi ta có thể bằng một cách đặt câu hỏi
> khéo léo** có thể **giúp model hành xử theo cách mà ta muốn** nó làm. Ví dụ
> như ở đây, vì **khi pretraining nó đã làm cái việc tóm tắt khi nó thấy chữ "TL;
> DR:"** thì khi xài nó, nếu mình pass cho nó câu hỏi gồm 1 đoạn và kết thúc  với
> chữ TL;DR: thì đương nhiên **có thể hiểu được là tại sao model biết mình
> muốn nó tóm tắt** nội dung
>
>
>
> ===
>
>
>
> So sánh ROUGE score của nó với các mô hình được huấn luyện chuyên cho
> nhiệm vụ summarization thì tuy nó chưa hơn được, nhưng rõ ràng cho ta thấy
> những tiềm năng của vịệc một llm chỉ với pretrained cũng có thể làm được
> những nhiệm vụ khó.

<br>

<a id="node-of58zyj"></a>

<p align="center"><kbd><img src="assets/9jt4epatt.png" width="80%"></kbd></p>

> [!NOTE]
> GPT 3 lớn hơn nữa 175B và 600GB data.

<br>

<a id="node-najl7k8"></a>

<p align="center"><kbd><img src="assets/73qzs13e1fj.png" width="80%"></kbd></p>

> [!NOTE]
> GPT 3 làm nổi lên khả năng gọi là few-shot learning: Được định nghĩa là
> việc ta có thể "dạy" cho model biết dạng công việc chỉ bằng cách đưa cho
> nó ví dụ trong prompt.
>
>
>
> Cái này còn gọi là in-context learning, để nhấn mạnh rằng không có việc
> update parameters gì cả.

<br>

<a id="node-i992pa2"></a>

<p align="center"><kbd><img src="assets/ah59tpynvqi.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/saimu2yqt9.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/2qv8sh8mjdp.png" width="80%"></kbd></p>

> [!NOTE]
> đánh giá trên SuperGLUE benchmark cho thấy performance tăng dần khi từ
> zero-shot -> one-shot -> few-shot learning

<br>

<a id="node-ev96rj9"></a>

<p align="center"><kbd><img src="assets/2g2raxt22vl.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là họ nói rằng khả năng few-shot learning, mà ta thấy rằng trong
> đó, ta "dạy" cho model cái dạng nhiệm vụ mà ta muốn nó làm chỉ
> bằng cách cho nó một vì ví dụ, thì cái này có thể lập luận rằng do 
> trong training set đâu đó, đã xuất hiện một dạng câu hỏi kiểu như vậy
> chăng, để rồi model đã được train cho việc này.
>
>
>
> Nhưng với thử nghiệm dùng một dạng task gọi là "word scrambling"
> mà anh ấy nói rằng ta giảm đi khả năng có một cái task giống vậy trong
> training set. Thì ta thấy model vẫn làm tốt hơn nếu nó lớn hơn.
>
>
>
> Thì đại ý là họ tin rằng có cơ sở để cho rằng llm đã phát triển được
> khả năng suy luận logic - reasoning.

<br>

<a id="node-1npfaqf"></a>

<p align="center"><kbd><img src="assets/lwb5cre2h9n.png" width="80%"></kbd></p>

> [!NOTE]
> từ đó sản sinh ra một khái niệm mới, gọi là prompting LMs
> So sánh với trước đây khi muốn llms làm tốt một task cụ thể nào đó,
> Ta phải finetune nó với supervised learning, sau khi đã pretrained.
>
>
>
> Còn khi mô hình lớn hơn rất nhiều lần, thì sau khi pretrained, chỉ cần
> zero/few-shot prompting là đủ để nó hiểu nhiệm vụ mình muốn là gì
> và làm tốt

<br>

<a id="node-g9g7avd"></a>

<p align="center"><kbd><img src="assets/2ob043xzi08.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên, prompting vẫn có hạn chế đó là với những task phức tạp thì model
> không làm tốt được. Nhất là đối với những nhiệm vụ cần nhiều bước suy luận
>
>
>
> Cần chú ý là với con người thì những task kiểu này cũng thấy khó nữa là

<br>

<a id="node-6y0a8r1"></a>

<p align="center"><kbd><img src="assets/pxekgeo7vtg.png" width="80%"></kbd></p>

> [!NOTE]
> Thế thì có giải pháp giúp cải thiện việc này đơn giản là thay đổi prompt.
> Dùng prompt có một hoặc vài ví dụ trong mô tả các bước tính toán / suy
> luận chi tiết. Thì với cách này, llm có thể "bắt chước" cách suy luận thành
> từng bước, từ đó làm tốt nhiệm vụ. Đây gọi là "chain-of-thought" prompting.

<br>

<a id="node-3b39ziz"></a>

<p align="center"><kbd><img src="assets/6jr09fcvl2x.png" width="80%"></kbd></p>

> [!NOTE]
> So sánh các model trên GSM8K - benchmark đánh giá khả năng suy luật
> bởi các câu hỏi toán trung học cho thầy Chain of thought prompting giúp
> model làm tốt hơn là standard prompting. Cũng như mô hình càng lớn thì
> khả năng này càng tỏ ra nổi bật

<br>

<a id="node-w6kxcio"></a>

<p align="center"><kbd><img src="assets/y1x0m7c3ti.png" width="80%"></kbd></p>

> [!NOTE]
> Sau đó người ta thử thay vì show ví dụ về các bước suy luận, thì chỉ
> đơn giản là bảo nó hãy suy luận qua từng bước.
>
>
>
> Để cho rõ hơn, trong slide, cách cũ của Chain-of-thought prompting
> cơ bản vẫn là ta cho nó xem một ví dụ của một câu hỏi (Roger has 5 ..)
> và câu trả lời mẫu, và trong này câu trả lời có dạng lập luận theo từng
> Bước. Điều này cho model học được 2 thứ, một là ta muốn nó làm gì
> - trả lời câu hỏi, và hai là trả lời theo kiểu gì (lập luận từng bước)
>
>
>
> Sau ví dụ gồm câu hỏi và câu trả lời mẫu thì mới tới câu hỏi "thiệt". Và
> kết thúc với A: để sau đó model sẽ "viết tiếp"
>
>
>
> ====
>
>
>
> Thế thì mới khám phá ra rằng ta không cần đưa ra ví dụ luôn, chỉ cần
> mớm trước cho nó A: "Let's think step by step". thì khi viết tiếp câu trả
> lời, nó sẽ lập luận từng bước.

<br>

<a id="node-uh32hvz"></a>

<p align="center"><kbd><img src="assets/n31jazeu34n.png" width="80%"></kbd></p>

> [!NOTE]
> Kết quả là nó vẫn làm tốt

<br>

<a id="node-msm9j87"></a>

<p align="center"><kbd><img src="assets/e4b3quib87.png" width="80%"></kbd></p>

> [!NOTE]
> đánh giá với benchmark có thể thấy: Chain of thought prompting luôn
> cho kết quả tốt hơn so với prompt thông thường, khi zero-shot-CoT (tức
> là chain of thought nhưng không cần ví dụ như vừa rồi) vẫn tốt hơn là
> few shot prompting (prompt với ví dụ)
>
>
>
> Có thể thấy cái nữa là few-shot CoT vẫn tốt hơn là Zero-shot CoT, tức
> là, cho nó xem ví dụ của các bước lập luận, sẽ tốt hơn là bảo nó tự lập
> luận.
>
>
>
> Nhận xét cuối cùng là càng nhiều example thì càng tốt.

<br>

<a id="node-06u748u"></a>

<p align="center"><kbd><img src="assets/kyohb6mbxt.png" width="80%"></kbd></p>

> [!NOTE]
> điều thú vị là trong paper này họ thử nhiều prompt khác nhau chứ không
> chỉ một, để rồi họ thấy rằng, prompt tốt nhất là "Let's work this out in a step
> by step...."

<br>

<a id="node-b72smgy"></a>

<p align="center"><kbd><img src="assets/1oqrwecwec4.png" width="80%"></kbd></p>

> [!NOTE]
> đại ý là nó mở ra một loại "nghệ thuật hắc ám" (dark art) về prompt
> engineering, khi mà người ta liên tục tìm hiểu và khai phá ra các
> cách prompt để cho ra những kết quả khác nhau.

<br>

<a id="node-z3inqw5"></a>

<p align="center"><kbd><img src="assets/yjn47aa8497.png" width="80%"></kbd></p>

> [!NOTE]
> và xuất hiện cả khái niệm
> Prompt engineering

<br>

<a id="node-bhivx2k"></a>

<p align="center"><kbd><img src="assets/6o891wcc1j7.png" width="80%"></kbd></p>

> [!NOTE]
> Vậy tóm lại zero-shot và Few-shot in-context learning ám chỉ việc ta chỉ
> "dạy" cho model biết nhiệm vụ mà ta muốn nó làm thông qua việc cung
> cấp cho thêm context (prompt). 
>
>
>
> Ưu điểm của cách này là không cần update parameters, nhưng hạn chế
> là nó đương nhiên là hạn chế của context window, nói ngắn gọn là prompt
> không thể quá dài được.
>
>
>
> Ngoài ra hạn chế nữa đó là các tác vụ phức tạp vẫn không thể đáp ứng
> được yêu cầu nếu chỉ dùng cách này, Từ đó qua Instruction finetuning.

<br>

<a id="node-h4gm96p"></a>

<p align="center"><kbd><img src="assets/jk4c9jfcqlh.png" width="80%"></kbd></p>

> [!NOTE]
> vậy thì vấn đề của llm đó là, nó là một ..language model, được huấn luyện
> để dự đoán từ tiếp theo, dựa trên nhưng gì trước đó.
>
>
>
> thế thì ví dụ với prompt là câu hỏi này "Explain the moon landing...." đương
> nhiên một cách tự nhiên đó là nó sẽ tìm chuỗi từ có xác suất cao nhất để
> nối tiếp câu này.
>
>
>
> Vậy thì với những gì nó được huấn luyện lúc pretraining, khả năng là nó sẽ
> trả lời như vầy, tức là những câu tương tự, có thể là dạng có xác suất cao
> nhất mà nó học được trong training set (kiểu như trong training set có
> những list câu tương tự nhau ví dụ vậy)
>
>
>
> Thế thì ý chính ở đây đó là, câu trả lời của llm trong một số tác vụ chưa
> TƯƠNG THÍCH (align) với mong muốn của con người.

<br>

<a id="node-v7b6gzr"></a>

<p align="center"><kbd><img src="assets/00vsdsfjx3nt.png" width="80%"></kbd></p>

> [!NOTE]
> vậy solution đơn giản là dạy
> nó thêm để nó cho ra câu trả
> lời như mong muốn

<br>

<a id="node-1sxbjla"></a>

<p align="center"><kbd><img src="assets/r77w7w13au.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/03d1c9wxgzqn.png" width="80%"></kbd></p>

> [!NOTE]
> thế thì quay lại cơ chế pretrain-finetuning đã biết, có điều thay vì ta
> chỉ fine-tuning với một tác vụ cụ thể nào đó - trong đó ta chỉ cần ít
> labeled data. Thì đây, ta sẽ finetune với nhiều task cùng lúc (do đó
> cần nhiều labeled data) để hi vọng rằng sau khi finetuning, nó có
> thể genralize tốt hơn nữa, làm tốt ở cả những task không được
> train.

<br>

<a id="node-oas32zs"></a>

<p align="center"><kbd><img src="assets/f9v110o2scv.png" width="80%"></kbd></p>

> [!NOTE]
> vậy thì ta sẽ collect example (labeled data) trên nhiều tác vụ khác
> nhau, và finetune LLM theo lối supervised learning. Rồi đánh giá nó
> trên nhưng unseen task.

<br>

<a id="node-tt631er"></a>

<p align="center"><kbd><img src="assets/tefkw07ti3d.png" width="80%"></kbd></p>

> [!NOTE]
> nói chung công thức là model to hơn, data nhiều hơn luôn giúp tăng
> performance. ví dụ dataset Super-NaturalInstructions có tới 1.6K tasks
> hơn 3 triệu examples. 
>
>
>
> Và có thể coi đó không chỉ là finetuning nữa, mà giống như pretrain lần
> nữa với các data tập trung hơn vào các tác vụ cụ thể. 
>
>
>
> Câu hỏi là làm sao để evaluate

<br>

<a id="node-43q3tl2"></a>

<p align="center"><kbd><img src="assets/lobc872wly.png" width="80%"></kbd></p>

> [!NOTE]
> để đánh giá người ta xây dựng MMLU, bao gồm 57 task khác
> nhau, để không chỉ đánh giá model với các task như sentiment
> analysis, NER nữa mà là những môn học của học sinh trung học
> như Đại số, Thiên văn,,,,,

<br>

<a id="node-26gstuq"></a>

<p align="center"><kbd><img src="assets/066isgmzb26.png" width="80%"></kbd></p>

> [!NOTE]
> hoặc BIG-Bench với
> hơn 200 tasks.

<br>

<a id="node-dx8wom1"></a>

<p align="center"><kbd><img src="assets/ae5mupvbfzo.png" width="80%"></kbd></p>

> [!NOTE]
> Trong đó có những task như convert kanji sang ASCII art và bảo llm đoán
> nghĩa của nó. Có thể thấy đây là những task rất khó

<br>

<a id="node-qg83lbx"></a>

<p align="center"><kbd><img src="assets/dwzjsdgrsq.png" width="80%"></kbd></p>

> [!NOTE]
> vậy Instruction finetuning có hiệu quả không?
>
>
>
> Đánh giá mô hình Flan-T5 (tức mô hình T5 đã được fine-tuned) cho thấy, trên
> thước đo trung bình của BIG-bench và MMLU có thể thấy là instruction
> finetuning có hiệu quả. Và mô hình càng lớn, thì fine-tuning càng có tác dụng
>
>
>
> Một điểm đáng chú ý nữa là một mô hình không quá lớn, nếu được (instruction)
> finetuning vẫn có thể có hiệu rất tốt hơn một mô hình lớn không finetuning.

<br>

<a id="node-v8j4nc1"></a>

<p align="center"><kbd><img src="assets/y2w7lq0hbf.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/r7ize1dlrcl.png" width="80%"></kbd></p>

> [!NOTE]
> ví dụ của kết quả trước và sau khi finetuning. Ta có thể thử với
> FLAN-T5 trên HuggingFace

<br>

<a id="node-wo24rqm"></a>

<p align="center"><kbd><img src="assets/4rqeme9amu2.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy vậy instruction finetuning vẫn có những hạn chế: Dễ thấy nhất là nó
> cần labeled data, do đó việc cần rất nhiều data sẽ rất tốn tiền
>
>
>
> Bên cạnh đó, vẫn có những tác vụ mà khó có thể train model với cách này.
> Ví dụ, những task có tính chất mở, không giới hạn trong một khuôn khổ
> nhất định và có thể sáng tạo như bảo nó viết một câu chuyện. thì  ta không
> muốn đưa cho model vài ví dụ của một câu chuyện để từ đó nó chỉ tập
> trung xác suất vào các cách đặt chuyện tương tự như vậy.
>
>
>
> Vấn đề thứ hai, xuất phát từ bản chất của language model có tính chất
> penalizing mọi mistake khi generate token đều như nhau. Trong ví dụ
> người ta đưa ra đại ý là model đoán sai hai chỗ: adventure và musical thì
> nó coi mức độ sai sót của hai chỗ đó là như nhau. Trong khi đó, thực ra
> nếu là human thì ta sẽ đánh giá chỗ sai của musical là nghiêm trọng hơn
> (vì kiểu như là nói Avatar là chương trình TV thuộc loại phiêu lưu thì cũng
> được, nhưng nói Avatar là chương trình âm nhạc thì sẽ sai nặng.
>
>
>
> Vậy nói chung, vấn đề thứ hai liên quan đến việc prediction của model 
> không align với mong muốn của human.

<br>

<a id="node-pvdremy"></a>

<p align="center"><kbd><img src="assets/zzmj5gywrt.png" width="80%"></kbd></p>

> [!NOTE]
> từ đó dẫn ta tới cách tiếp cận tiếp theo để khắc phục
> hạn chế này đó là RLHF

<br>

<a id="node-aiayuiv"></a>

<p align="center"><kbd><img src="assets/dj8fa2ntxt.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là lấy ví dụ ta muốn train một language model cho nhiệm vụ
> summarization. Thế thì giả sử có thể xây dựng được một human reward
> function giúp chấm điểm được result của llm, theo các tiêu chí của
> human để nếu nó càng align với human reference thì điểm càng cao.
>
>
>
> Như vậy mục tiêu của model khi training là tối đa được expected reward
> khi tính từ llm result. Công thức E s^ ~ p_theta(s) [R(s^)] có nghĩa là:
>
>
>
> với các s^ lấy từ dự đoán của model với prompt s, thì giá trị kì vọng /
> trung bình của các reward score tính bởi R(s^) là bao nhiêu. Thì ta muốn
> train model  Để maximize gía trị kì vọng này.
>
>
>
> Ở đây để đơn giản thì ta kiểu như đang dùng model với một prompt s

<br>

<a id="node-gt0av39"></a>

<p align="center"><kbd><img src="assets/oussyv3m4ce.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói sơ về RL, dù nó cũng đã có từ lâu, cũng như là nổi lên lại
> trong những năm 2013 trở đi nổi bật là những thành tựu của DeepMind.
>
>
>
> Với LLM thì nó tỏ ra khó khăn hơn, tuy nhiên với các  bước tiến của RL thì
> cho phép nó áp dụng với LM như PPO

<br>

<a id="node-rg61xnc"></a>

<p align="center"><kbd><img src="assets/bgy91qgfi9.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là có những thách thức đặt ra cho việc train LM parameters để
> maximize được objective này, như giả sử ta dùng các tiếp cận quen thuộc
> là gradient ascent, thì làm sao ta estimate được objective function? Và hơn
> nữa, sẽ ra sao nếu reward function không differentiable?
>
>
>
> Thế thì, có một phương pháp gọi là Policy gradient methods in RL, cung cấp
> cho chúng ta công cụ để estimate và optimizing objective function.
>
>
>
> Đương nhiên để hiểu sâu về RL mình sẽ đợi đến khi qua course RL của Google
> DeepMind hoặc ở đây suggest cs234

<br>

<a id="node-txtyyj1"></a>

<p align="center"><kbd><img src="assets/tvwutoqhl1.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, về mặt toán học, ta đã nói là mình muốn tính gradient của objective function
> để mà thay đổi model param giúp tối đa objective function E s^~ p_theta(s)[R(s^)]
>
>
>
> Kí hiệu là ∇_theta of E s^~ p_theta(s)[R(s^)]:
>
>
>
> Thế thì đầu tiên, objective function là expectation, vậy **dựa trên định nghĩa của
> expectation**: **E X~P(x) [f(X)]** có ý nghĩa là: Với **random variable X** **tuân
> theo phân phối xác suất P(x)**, thì **giá trị trung bình, giá trị kì vọng của f(X) là
> bao nhiêu**.
>
>
>
> Theo định nghĩa nó bằng ∑ **[p(x)*f(X)]** tức là: **tổng mọi giá trị của
> f(X=x)**, được **weight bởi xác suất P(X=x)**
>
>
>
> Vậy, tương tự E s^~p_theta(s)[R(s^)] mang ý nghĩa là với **s tuân theo phân phối
> xác suất p_theta(s)** (*), thì **giá trị trung bình của R(s) là sẽ là tổng các R(s)**,
> được  trọng số bằng xác suất xảy ra chuỗi s, chính là p_theta(s)
>
>
>
> E s^~p_theta(s)[R(s^)] = **∑s [R(s) * p_theta(s)]**
>
>
>
> *Vì sao **s^~p_theta(s)**: bởi vì **với một chuỗi s**, **lm tính toán ra xác suất của
> chuỗi s này**  (đây là **tính chất cơ bản của language model**). Nên s tuân theo
> phân phối xác suất quy định bởi p_theta(s).
>
>
>
> ===
>
>
>
> Vậy ∇_theta of E s^~ p_theta(s)[R(s^)] = ∇_theta ∑s [R(s) * p_theta(s)]
>
>
>
> Tiếp theo, dựa vào tính chất đạo hàm của tổng bằng tổng đạo hàm nên  
>
>
>
> ∇_theta ∑s [R(s) * p_theta(s)] = ∑s ∇_theta [R(s) * p_theta(s)] 
>
>
>
> = **∑s R(s)[∇_theta p_theta(s)]**  (1)
>
>
>
> (vì R(s) không phụ thuộc theta, nên ∇_theta [R(s) * p_theta(s)] = R(s)[∇_theta p_theta(s)]) 
>
>
>
> ===
>
>
>
> Tiếp theo, dùng một trick gọi là log-derivative trick, cơ bản chỉ là dựa vào chain-rule
> để mục đích muốn tính ra ∇_theta p_theta(s):
>
>
>
> Ta sẽ tính log [∇_theta p_theta(s)]. Dưa vào chain-rule: d log(f(x)) = [1/f(x)] df(x) nên 
>
>
>
> ∇_theta log [p_theta(s)] = [1/p_theta(s)] ∇_theta p_theta(s)
>
>
>
> <=> {∇_theta log [p_theta(s)] } * p_theta(s) = /**∇_theta p_theta(s)** /(2)Vậy từ (1) ta có
>
>
>
> ∇_theta ∑s [R(s) * p_theta(s)] = ∑s R(s)[/**∇_theta p_theta(s)**/]Thay (2) vào:
> ∇_theta ∑s [R(s) * p_theta(s)] = ∑s R(s)[   {∇_theta log [p_theta(s)] } * p_theta(s)  ]
>
>
>
> **= ∑s p_theta(s) * R(s) [ ∇_theta log [p_theta(s)] ]**
>
>
>
> Đây chính là định nghĩa của **Expectation s^~p_theta(s) { R(s) [ ∇_theta log [p_theta(s)] }
>
>
>
> ========**
>
>
>
> Tóm lại dùng cái trick, ta đã chuyển việc **cần tính ∇_theta of E s^~ p_theta(s)[R(s^)]**
>
>
>
> thành ra cần tính 
>
>
>
> **Expectation s^~p_theta(s) { R(s^) [ ∇_theta log [p_theta(s^)] }**

<br>

<a id="node-kjicr2o"></a>

<p align="center"><kbd><img src="assets/htbftglzyo.png" width="80%"></kbd></p>

> [!NOTE]
> Tóm lại dùng cái trick, ta đã chuyển việc cần tính
>
>
>
> ∇_theta of E s^~ p_theta(s)[R(s^)] (1)
>
>
>
> thành ra cần tính
>
>
>
> Expectation s^~p_theta(s) { R(s^) [ ∇_theta log [p_theta(s^)] } (2)
>
>
>
> Thì mục đích là vì không / khó tính cái (1), nhưng có thể tính ước lượng cái (2)
> bằng cách dùng Monte Carlo samples để có:
>
>
>
> Expectation s^~p_theta(s) { R(s^) [ ∇_theta log [p_theta(s^)] }
>
>
>
> **~= (1/m) Sum i=1:m R(s_i) [ ∇_theta log [p_theta(s_i)]**
>
>
>
> **Có nghĩa đại khái ban đầu cần tính Đạo hàm của một hàm expectation,  thì
> việc này khó / không tính được, nên ta chuyển nó thành expectation của một
> hàm số khác trong đó có thể tính được vì có thể tính đạo hàm theo theta của
> p_theta.
>
>
>
> Và mô ta công thức trên như sau: ta sẽ sampling một số lượng hữu hạn (m)
> các  sample s_i từ model - tức là dùng m result generate bởi language model.
> Và tính ra reward function của các sample đó R(s_i) nhân với đạo hàm của log
> p_theta(s_i) w.r.t theta. Cộng lại và chia cho m.
>
>
>
> Thì ta sẽ có giá trị ƯỚC LƯỢNG CHO ĐẠO HÀM CỦA OBJECTIVE
> FUNTION  để mà update theta.

<br>

<a id="node-fo0fgv1"></a>

<p align="center"><kbd><img src="assets/0rk40q1ysl4.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên câu hỏi là, nếu reward function là một binary function (output
> là 1 or 0) ví dụ như nếu s là một câu có chứa từ "cat", R(s) = 1, còn ngược
> lại thì R(s) = 0. Thì cách làm này sẽ có vấn đề gì?
>
>
>
> Đơn giản đó là gradient sẽ trở thành một indicator function. Là sao?
>
>
>
> Vì khi đó mọi sample s_i không chứa từ "cat" sẽ có reward = 0, trừ những
> sample có từ "cat".
>
>
>
> Chưa hiểu ý gv nói khúc này.

<br>

<a id="node-soibf9k"></a>

<p align="center"><kbd><img src="assets/k4bqwupdf.png" width="80%"></kbd></p>

> [!NOTE]
> Ý nghĩa cần hiểu của kết quả này là:
>
>
>
> Nếu một sample s_i generate bởi model mà có R(s_i) dương, tức là tốt, thì
> gradient sẽ mang dấu dương, để nếu update theta, nó sẽ tăng xác xuất của
> p_theta (s_i), mang ý nghĩa là **tăng cường khả năng xuất hiện chuỗi s_i.**
>
>
>
> **Vì objective function như đã nói, nó là ∑s [R(s) * p_theta(s)]  nên update
> theta theo gradient ascent đương nhiên sẽ đẩy giá trị kì vọng này lên, đồng
> nghĩa đẩy p(s_i) lên.** 
>
>
>
> Ngược lại nếu một sample có reward âm, thì gradient ascent update  sẽ làm
> **giảm objective functio**n chính là **giảm đi xác xuất suất hiện chuỗi s_i mà có
> reward âm** (không aligned với human reference đó)

<br>

<a id="node-sxy3qrv"></a>

<p align="center"><kbd><img src="assets/mz0ga9nhp4i.png" width="80%"></kbd></p>

> [!NOTE]
> tiếp, đại khái là trước khi train language model với objective function vừa 
> nói, còn một thách thức đặt ra nữa, đó là reward function R(s). Sẽ rất tốn
> kém để mà đưa human vào trong vòng lặp training này (đánh giá, chấm
> điểm model prediction một cách thủ công).
>
>
>
> Do đó, giải pháp là thay vì hỏi trực tiếp human để biết reward cao hay thấp
> thì ta sẽ huấn luyện một reward model RM_phi(s) có nhiệm vụ đưa ra reward
> score theo sở thích của human, nói cách khác, ta sẽ dùng nó đại diện cho 
> human trong vòng lặp trainning LM.
>
>
>
> Và để train reward model ta sẽ dùng một labeled dataset phản ánh reference
> của human.

<br>

<a id="node-2suxygg"></a>

<p align="center"><kbd><img src="assets/k7bs29nrdh.png" width="80%"></kbd></p>

> [!NOTE]
> vấn đề nữa đó là, những sự đánh giá của con người không mang 
> tính tuyệt đối, ý là nếu muốn có target để train reward model thì khó
> mà làm theo kiểu "summary #1" - reward = 4.1 được vì khó hỏi một 
> người và bảo họ cho điểm kiểu tuyệt đối như vậy.
>
>
>
> Giải pháp là thay vì bảo annotator cho điểm, thì bảo họ so sánh xem
> cái nào là tốt hơn.

<br>

<a id="node-ry45tqw"></a>

<p align="center"><kbd><img src="assets/h6zfkv0l3do.png" width="80%"></kbd></p>

> [!NOTE]
> Từ đó ta có label theo kiểu s1 thì tốt hơn s2, s2 tốt hơn s3.
>
>
>
> Để rồi ta sẽ train reward model: Cần nhắc Reward model cũng là một
> language model, nhưng output của nó sẽ là reward score. Thế thì đương
> nhiên target khi train reward model là nếu nó nhận s1 thì reward RM(s1) sẽ
> cao hơn RM(s2). Do đó, người ta thiết kế loss function như vầy:
>
>
>
> Hiểu đại khái là với loss như vậy, để giảm loss thì tăng khả năng RM(s_win)
> lớn hơn RM(s_lose): tức là để giảm loss, model phải cho reward của câu tốt
> hơn cao hơn reward của câu tệ.
>
>
>
> Loss function như vậy là sao:
>
>
>
> Training set sẽ là các cặp [s_winning, s_losing]. Thế thì, với mỗi sample như
> vậy ta sẽ tính hiệu của hai reward RM(s_w) - RM(s_l). Để rồi nếu nó ra dương
> với giá trị lớn (đồng nghĩa là model đang đúng khi cho reward của s_win cao
> hơn nhiều s_lose) thì qua sigmoid, nó sẽ gần 1, dẫn đến log (~1) sẽ gần 0,
> tức loss nhỏ.
>
>
>
> Ngược lại nếu khoảng cách này nhỏ, thì sigmoid sẽ là 0.5, hoặc thậm chí nếu
> khoảng cách này âm thì sigmoid sẽ ra gần 0 -> log ~= 0 sẽ về âm vô cùng, thì
> loss (có dấu trừ phí trước) sẽ -> lớn.
>
>
>
> Nói chung là loss sẽ encourage model thay đổi parameters để s_winning vượt
> xa s_losing.

<br>

<a id="node-b23dkvc"></a>

<p align="center"><kbd><img src="assets/1l54muv7vl8.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là vì quan điểm của mỗi người mỗi khác, nên tập hợp quan điểm
> của nhiều người (ensemble of humans) sẽ chính xác hơn là của một người
>
>
>
> Tuy nhiên với một RM train trên dữ liệu đủ lớn thì ta có thể tiếp cận được
> performance của human baseline để có thể dùng nó như đại diện của human
> preference

<br>

<a id="node-8k2iyvi"></a>

<p align="center"><kbd><img src="assets/xlrk2xzjf1f.png" width="80%"></kbd></p>

> [!NOTE]
> Ok, tới đây là đã có đủ các component cho RLHF: Ta đã có một
> pretrained (đương nhiên là pretrained với self-supervised learning và có
> thể đã instruction-finetuned luôn)
>
>
>
> Đã có reward model đại diện cho human preference. Và phương pháp
> training (cái objective function hồi nãy).
>
>
>
> Vậy quá trình RLHF bắt đầu với việc ta sẽ clone một copy của pretrain
> model.
>
>
>
> Objective function để train RLHF đương nhiên là muốn maximize
> reward: RM(s). Tuy nhiên có thêm một vế, mà ta muốn khống chế nó
> nhỏ, đó là log của tỉ lệ giữa xác suất của chuỗi s tính bởi model mới
> (Train với RLHF) và model cũ (pretrain model). Giữ cho vế này nhỏ thì
> quá trình training theta của model mới phải giữ tỉ lệ này ~= 1, để log (~1)
> = 0
>
>
>
> Với ý nghĩa là ngăn cản hai phân phối xác suất này diverge (xa cách,
> phân kì) nhau khiến câu trả lời cảu RLHF model không còn đúng nữa.
>
>
>
> Cái vế này xuất phát từ công thức Kullback-Leibler tính divergence giữa
> hai phân phối xác suất mà mình đã biết qua ở bên GAN Specializaion.
> Sẽ còn gặp lại ở hai lecture về Generative model của
> cs231n/EECS498-007

<br>

<a id="node-k33xpuh"></a>

<p align="center"><kbd><img src="assets/nqi2oyqzpul.png" width="80%"></kbd></p>

> [!NOTE]
> biểu đồ minh họa cho kết quả của RLHF thật sự giúp lm có thể tăng tỉ lệ đưa
> ra các đáp án aligned với human preference, mà pretrained only model hay
> Supervised learning (instruction tuning) model không đạt được
>
>
>
> Có question là có thể từ pretraining làm luôn RLHF không? 
>
>
>
> -> Good question, có thể, tuy vậy cách tiếp cận phổ biến thường là finetuning
> để model đạt được một khả năng nào đó trong nhiệm vụ của nó rồi mới RLHF

<br>

<a id="node-wgpo9cd"></a>

<p align="center"><kbd><img src="assets/g9xg4eo3x4f.png" width="80%"></kbd></p>

> [!NOTE]
> và cái mô hình đứng sau ChatGPT chính là được train với RLHF nhưng
> ở quy mô lớn hơn nhiều:
>
>
>
> Bước 1 là thu thập "demonstration data", với hơn 30 nghìn task khác
> nhau, dùng để instruction-finetuning GPT-3
>
>
>
> Bước 2 là thu thập "comparison data" để train reward model.
>
>
>
> Bước 3 là RLHF

<br>

<a id="node-3v9zmp0"></a>

<p align="center"><kbd><img src="assets/duxd6h270la.png" width="80%"></kbd></p>

> [!NOTE]
> Q: Train reward model cùng lúc hay trước khi RLHF, và reward model label lấy
> từ đâu ra?
>
>
>
> A: Đúng ta sẽ train reward model trước rồi freeze nó, dùng nó để train RLHF.
>
>
>
> Nhưng quá trình sẽ là iteratively:
>
>
>
> Bươc 1: Đầu tiên ta sẽ sample LM (cái pretrained model mà cần finetune với
> RLHF) để có các prediction, answer của nó.
>
>
>
> Bước 2: Sau đó ta mới cho human rate các answer này (để tạo comparison
> data).
>
>
>
> Bước 3: Dùng data này để train Reward model.
>
>
>
> Bước 4: Và dùng Reward model để train RLHF.
>
>
>
> Quay lại bước 1+ sampling LM, nhưng là cái đã được finetune theo RLHF một
> chút ở trên, rồi ->2->3->4. Như vậy có thể thấy quá trình lặp đi lặp lại sẽ cải
> thiện cả Reward model và LM.

<br>

<a id="node-v8sc4cw"></a>

<p align="center"><kbd><img src="assets/nvyxr5it4hn.png" width="80%"></kbd></p>

<br>

<a id="node-1x0baox"></a>

<p align="center"><kbd><img src="assets/0juvekv6psmm.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/jmf94njjvbg.png" width="80%"></kbd></p>

> [!NOTE]
> Kết quả là lm có thể align với
> human preference.

<br>

<a id="node-8yzaf9m"></a>

<p align="center"><kbd><img src="assets/sqcqadv3sac.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy vậy còn RLHF vẫn có những
> nhược điểm

<br>

<a id="node-bjob5hd"></a>

<p align="center"><kbd><img src="assets/u0sw5upo0up.png" width="80%"></kbd></p>

> [!NOTE]
> là những nhược điểm của bản thân phương pháp RL và vấn
> đề Reward hacking

<br>

<a id="node-hxj9wn5"></a>

<p align="center"><kbd><img src="assets/27lrx8v4stki.png" width="80%"></kbd></p>

<br>

