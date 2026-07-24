# Week 2 - Finetuning And Evaluating Large Language Model

📊 **Progress:** `144` Notes | `156` Screenshots

---
<a id="node-79rvfvg"></a>

## Week 2 - Finetuning And Evaluating Large Language Model

<br>

<a id="node-utvame4"></a>

## Introduction Week 2

<br>

<a id="node-mn1aruo"></a>

> [!NOTE]
> 1. Introduction to Instructors and Topics: The passage begins with the host welcoming two instructors, Mike
> and Shelby. They discuss the topics covered in the previous week, which include transformer networks and
> the Generative AI project Life Cycle. They mention that this week's topics are **instruction** **tuning of large language
> models** and **efficient fine-tuning.**
>
> 2. Instruction Fine-Tuning: **Instruction fine-tuning** is explained as a process used to **modify the behavior of a
> pre-trained language model**. While the **base mode**l **has knowledge** about the world, it may **not know how to
> respond to specific prompts or questions**. Instruction fine-tuning **helps the model adapt its behavior to be more
> helpful for specific tasks**.
>
> 3. **Breakthrough** of Instruction Fine-Tuning: The instructors highlight that **instruction fine-tuning** is a **significant
> breakthrough** in the history of large language models. **Pretraining a model on general text from the internet
> may not enable it to follow instructions accurately**. However, **instruction fine-tuning** allows a large language
> model to **be trained on a smaller dataset containing specific instructions**.
>
> 4. **Addressing Catastrophic Forgetting**: Catastrophic forgetting is a **challenge** during instruction fine-tuning,
> where the **model forgets previously learned information when trained on new data**. The course discusses
> techniques to combat this problem, such as **using a broad range of instruction types** during fine-tuning.
>
> 5. **Types of Fine-Tuning**: There are **two main types of fine-tuning** discussed - **instruction fine-tuning** for **specific
> tasks** and **parameter-efficient fine-tuning** (**PEFT**) for **specialized applications**. PEFT involves **freezing original
> model weights** or **adding adaptive layers to reduce memory** and **compute requirements.**
>
> 6. Parameter-Efficient Fine-Tuning Techniques: The use of techniques like **LoRA** (**Low Rank Approximation**) is
> highlighted as an effective method for **parameter-efficient fine-tuning**. LoRA uses **low-rank matrices**, achieving
> good performance results with **lower computational and memory demands**.
>
> 7. Developers' Approaches: Different developers use various approaches. **Some start with prompting**, while
> others **turn to fine-tuning techniques like PEFT**, especially **when prompting reaches performance limits**. The
> cost of using **giant models** and the **importance of model size for data control** are also discussed.
>
> 8. Excitement and Accessibility: **PEFT techniques make fine-tuning generative AI models accessible** to
> **everyday users with cost constraints**. This allows **developers to achieve good performance results without the
> excessive costs associated with full fine-tuning**.
>
> Overall, the main ideas **revolve around the concepts of instruction fine-tuning**, **parameter-efficient fine-tuning,
> and how these techniques are valuable for unlocking better performance** and **accessibility of large language
> models.**

<br>

<a id="node-8trbtra"></a>

## Fine-tuning With Instruction

<br>

<a id="node-jw1wzfo"></a>

### Instruction Fine-tuning

<br>

<a id="node-jnznfv5"></a>

> [!NOTE]
> Main ideas:
>
> 1. Introduction: The passage begins by **recapping the previous week's topics**, including the **generative AI project
> lifecycle**, **example use cases for large language model**s, and the **tasks they can perform.** 
> 2. **Purpose of the Lesson**: The lesson **aims to teach methods to improve the performance** of an existing model for
> **specific use cases** and introduces **important metrics for evaluating** the performance of a **fine-tuned large language
> model (LLM).**
>
> 3. **Fine-Tuning with Instruction Prompts**: The passage discusses fine-tuning as a **supervised learning** process
> where a **data set of labeled examples (prompt completion pairs**) is used to **update the weights of the LLM**.
> Fine-tuning focuses on **improving the model's ability** to **generate relevant completions for specific tasks.**
>
> 4. Instruction Fine-Tuning: A strategy known as **instruction fine-tuning** is introduced, which trains the model using
> **examples demonstrating how it should respond to specific instructions**. For various tasks, the data set contains
> **prompt completion pairs** wit**h clear instructions**.
>
> 5. **Full Fine-Tuning**: When **all the model's weights are updated** during fine-tuning, it is referred to as **full fine-tuning**.
> This process r**esults in a new version of the model with updated weights.**
>
> 6. **Memory** and **Compute Considerations**: **Similar to pre-training**, **full fine-tuning requires sufficient memory** and
> **compute budget** to store and process all the **gradients, optimizers, and other components**. **Memory optimization**
> and **parallel computing strategies** are recommended.
>
> 7. **Preparing Training Data**: Developers can use **publicly available datasets** and **prompt template libraries** to create
> **instruction prompt datasets for fine-tuning**. These libraries include **templates for different tasks and data sets.** 
> 8. **Fine-Tuning Proces**s: The passage outlines the **steps for fine-tuning**, which involves **dividing the data into
> training, validation, and test splits**. During fine-tuning, the **model generates completions for prompts**, and t**hese
> completions are compared to the labeled responses** in the training data to c**alculate loss and update the model
> weights**.
>
> 9. **Evaluation**: The fine-tuning process includes **evaluation steps** using the **validation and test data sets** to measure
> the model's performance. The aim is to achieve **improved performance on specific tasks** with the new instruct
> model.
>
> 10. Conclusion: The passage clarifies that when referring to **fine-tuning** in the context of large language models, it
> is synonymous with **instruction fine-tuning.**

<br>

<a id="node-jj6hbwd"></a>

<p align="center"><kbd><img src="assets/9s6yhy02cwe.png" width="80%"></kbd></p>

> [!NOTE]
> Nói chung là week 2 sẽ tập trung vào
> **Fine-tuning và evaluate fine-tuned  LLM**

<br>

<a id="node-8xho55p"></a>

<p align="center"><kbd><img src="assets/s4igf3n6uo.png" width="80%"></kbd></p>

> [!NOTE]
> Nhắc lại về i**n-context learning và một số hạn chế của nó**
> như k**hông hiệu quả với model nhỏ** và **bị giới hạn bởi
> context window** khiến k**hông thể cứ prompt dài thiệt dài**
> được. Đó là lúc cần phải **fine-tune**

<br>

<a id="node-cirhryo"></a>

<p align="center"><kbd><img src="assets/i8gpt0ktg6.png" width="80%"></kbd></p>

> [!NOTE]
> **pre-training** là **train model với self-supervised
> learning** với **số lượng lớn unstructured textual data**

<br>

<a id="node-amthhy0"></a>

<p align="center"><kbd><img src="assets/xpqfl8wzrdq.png" width="80%"></kbd></p>

> [!NOTE]
> **Fine-tuning** thì là **supervised learning**,
> train model với **data là prompt và label** là
> **completion mong muốn.**

<br>

<a id="node-bxht6ef"></a>

<p align="center"><kbd><img src="assets/43gqbebwpqy.png" width="80%"></kbd></p>

<br>

<a id="node-ndnqjka"></a>

<p align="center"><kbd><img src="assets/qjgtkfb7aco.png" width="80%"></kbd></p>

<br>

<a id="node-wnz81je"></a>

<p align="center"><kbd><img src="assets/sooz6giyebl.png" width="80%"></kbd></p>

> [!NOTE]
> **tuỳ vào specific task** mà **label -
> có dạng một câu trả lời đạt tiêu
> chuẩn cho task đó.**

<br>

<a id="node-swm25j9"></a>

<p align="center"><kbd><img src="assets/wm0l3jcu0uh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **bước một là phải chuẩn bị data,**
> ta **có thể dùng các bộ data có sẵn như của
> Amazon product review**

<br>

<a id="node-qozttoy"></a>

<p align="center"><kbd><img src="assets/d4pmxhbofj.png" width="80%"></kbd></p>

> [!NOTE]
> **Chuẩn bị data xong** thì bước tiếp
> theo là **train-valid-test split.**

<br>

<a id="node-4bxq5l0"></a>

<p align="center"><kbd><img src="assets/7hhis2mmvkk.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi quá trình **fine-tuning cơ bản là supervised learning**.
> Bắt đầu với **prompting (x trong training set), bỏ vào model
> để nó trả lời**. Dùng **label là một đáp án chuẩn để tính loss**
> (cross entropy) để **update model's weights bằng backprop
> như thường lệ,**

<br>

<a id="node-t26u578"></a>

<p align="center"><kbd><img src="assets/ow82czdyn3.png" width="80%"></kbd></p>

> [!NOTE]
> Và khi training xong, **dùng validation để h.p tuning**
> và tính ra **validation accuracy.** Sau cùng là dùng
> **test set tính test_accuracy**

<br>

<a id="node-polbuwf"></a>

<p align="center"><kbd><img src="assets/hgftybr3e9u.png" width="80%"></kbd></p>

> [!NOTE]
> Kết quả là " **instructed model"** có khả năng làm **tốt hơn original
> model ở specific task**

<br>

<a id="node-efnhbxn"></a>

### Fine-tuning On A Single Task

<br>

<a id="node-yp92lz3"></a>

> [!NOTE]
> 1. While **large language models (LLMs)** are known for **their ability to perform multiple language
> tasks**, some **applications may only require performing a single task.**
>
> 2**. Fine-tuning a pre-trained model** is a technique to **improve the model's performance on a specific
> task** of interest **using a dataset with examples related to that task**.
>
> 3. Fine-tuning can **lead to good results** even with a **relatively small number of examples**, contrary
> to the massive amount of text the model saw during pre-training.
>
> 4. A **potential drawback** of fine-tuning is **catastrophic forgetting**, where the **model's performance
> on other tasks may degrade** after fine-tuning.
>
> 5. To avoid catastrophic forgetting, it's **essential to assess whether maintaining multitask capabilities
> is crucial** for the application.
>
> 6. One option is **multitask fine-tuning**, where the model is **fine-tuned on multiple tasks
> simultaneously**, which **requires more data** and **computational resources.**
>
> 7. Another option is **parameter efficient fine-tuning (PEFT),** which **preserves the original LLM
> weights** and **trains only small task-specific adapter layers and parameters**. PEFT is **more robust
> to catastrophic forgetting**.
>
> 8. PEFT is an **active area of research** and is **aimed at addressing the challenges of fine-tuning and
> multitask learning.**
>
> 9. The text mentions that **multitask fine-tuning will be discussed in more detail in subsequent
> content**, and the focus will move on to **exploring multitask fine-tuning in the next video.**

<br>

<a id="node-rs5ctm5"></a>

<p align="center"><kbd><img src="assets/dhh8y1ofm1.png" width="80%"></kbd></p>

> [!NOTE]
> Ý là **dù LLM có thể perform nhiều loại task khác nhau** nhưng **có thể mình chỉ cần nó
> làm tốt trên một task cụ thể nào đó** ví dụ **Summarization** thôi. Lúc này ta sẽ
> **fine-tuning LLM với training data của specific task đó** và **không cần nhiều chỉ 500-1000
> sample cũng có thể đủ** để cải thiện đáng kể khả năng của model trong task mong muốn.
> Tuy nhiên c**ó một hiện tượng có thể xẩy ra là "Catastrophic forgeting"**

<br>

<a id="node-jbqi897"></a>

<p align="center"><kbd><img src="assets/x5puzvq7ogh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/mnvo45mrfk.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dù **giúp cải thiện khả năng của model trong task mong muón**
> nhưng lại dẫn đến **ảnh hưởng giảm performance trên các task khác.**

<br>

<a id="node-mqdoana"></a>

<p align="center"><kbd><img src="assets/knxh8nd5ymo.png" width="80%"></kbd></p>

> [!NOTE]
> Như **trước khi fine-tuning model đối
> với task sentiment analysis** có thể làm
> tốt câu hỏi "nhớ tên" này

<br>

<a id="node-u1gugzg"></a>

<p align="center"><kbd><img src="assets/8e673a82s1i.png" width="80%"></kbd></p>

> [!NOTE]
> Nhưng **sau khi fine-tuning, nó không
> còn trả lời đúng nữa**, **mà lại trả lời theo
> kiểu sentiment analysis**

<br>

<a id="node-fpowyqw"></a>

<p align="center"><kbd><img src="assets/cl2hg2b3y5r.png" width="80%"></kbd></p>

> [!NOTE]
> Giải pháp:
>
>
>
> 1 là **khỏi care** những task khác có tệ thế nào **nếu ta chỉ cần nó làm tốt thứ
> ta muốn**.
>
>
>
> 2 là **fine-tuning với nhiều task cùng lúc** cách này **phải chuẩn bị data
> nhiều** (cho nhiều task) cùng với đó sẽ là **compute budget** ..
>
>
>
> 3 tốt nhất, đại khái là một technique có tên là **PEFT** giúp **thay vì tweak
> toàn bộ params (gọi là full-training)** thì nó sẽ **chỉ thay đổi các param liên
> quan đến task đang fine-tuning thôi**. Từ đó **giảm thiểu tác động đến các task
> khác.**

<br>

<a id="node-fhhcmh1"></a>

<p align="center"><kbd><img src="assets/jyuja1abpo.png" width="80%"></kbd></p>

<br>

<a id="node-cuy6hkv"></a>

### Multi-task Instruction Fine-tuning

<br>

<a id="node-8ju59c4"></a>

> [!NOTE]
> 1. Multitask Fine-Tuning: It **extends single task fine-tuning** by **using a training dataset that includes
> examples for multiple tasks**. The goal is to **improve the model's performance on various tasks
> simultaneously** and **prevent catastrophic forgetting**.
>
> 2. FLAN Family of Models: **FLAN** stands for **Fine-Tuned Language Net.** **FLAN models are fine-tuned**
> using **multitask instruction fine-tuning**. They are **capable of handling multiple tasks** and have been **trained
> on diverse datasets** from different models and papers.
>
> 3. **SAMSum Dataset**: An example of a **prompt dataset used for summarization tasks** in FLAN-T5. It
> consists of **messenger-like conversations with summaries crafted by linguists** to generate a high-quality
> training dataset for language models.
>
> 4. **Additional Fine-Tuning**: While FLAN-T5 is a good general-purpose model, it may **still need improvement
> for specific tasks**. Additional **fine-tuning with domain-specific datasets**, such as **dialogsum**, can enhance
> the model's performance for targeted tasks.
>
> 5. **Custom Fine-Tuning**: Companies can **benefit from fine-tuning with their own internal data**, such as
> **customer support chat conversations**, to **train models tailored to their specific needs**.
>
> 6. Evaluation of Model Completions: To **assess the quality of fine-tuned models**, **various metrics and
> benchmarks can be used** to compare their performance with the original base model.

<br>

<a id="node-z7c7q3l"></a>

<p align="center"><kbd><img src="assets/hi002j4zvnv.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **fine-tuning với data trên nhiều task**. Giúp **cải thiện khả năng
> model trên nhiều task đó và tránh hiện tượng catastrophic forgeting**.
> Nhược điểm là yêu cầu nhiều data và compute budget tương ứng.

<br>

<a id="node-4ru3uhy"></a>

<p align="center"><kbd><img src="assets/g2m5ir1k4kh.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nói về cái tên FLAN model thật ra là để chỉ **những model khác
> nhau** được f**ine tune với specific set of instructions**. FLAN viết tắt của
> **F**ine-tuned **LAnguage N**et.

<br>

<a id="node-b3qa5lo"></a>

<p align="center"><kbd><img src="assets/ud14fggbktn.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ **FLAN-T5 là based model T5
> được instruction Fine-tuned**

<br>

<a id="node-kvdabls"></a>

<p align="center"><kbd><img src="assets/xswt3bmcdug.png" width="80%"></kbd></p>

> [!NOTE]
> FLAN-T5 được instructed
> fine-tuned với **rất nhiều dataset
> cho rất nhiều specific task**

<br>

<a id="node-1b6tog3"></a>

<p align="center"><kbd><img src="assets/i48xa31zpmr.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ một trong những **dataset** dùng để fine-tuned đó, là
> **SAMsum** - Gồm có các **dialog và summarization**

<br>

<a id="node-kvn2tb7"></a>

<p align="center"><kbd><img src="assets/1p4i4hisxcx.png" width="80%"></kbd></p>

> [!NOTE]
> Hàng chục ngàn dialog được
> summarize bởi các linguist

<br>

<a id="node-1fw1eup"></a>

<p align="center"><kbd><img src="assets/5on2ti6gruw.png" width="80%"></kbd></p>

> [!NOTE]
> Ví dụ một **prompt template** như sau ta thấy đều có dạng: **Dialog - Câu hỏi (yêu
> cầu) - Câu trả lời chuẩn**. Nhưng **câu hỏi thì có nhiều kiểu** khác nhau. Mục
> đích là để **dạy cho model biết là những dạng yêu cầu có nội dung như vậy thì
> phải summarize như vậy.**

<br>

<a id="node-t0e9qz1"></a>

<p align="center"><kbd><img src="assets/9fps4av65dm.png" width="80%"></kbd></p>

> [!NOTE]
> Tuy nhiên vì **SAMsum dataset chỉ là những dialog chủ yếu là giữa bạn bè**
> nên nếu muốn **cải thiện hơn nữa khả năng summarization đối với các task
> cụ thể ví dụ như chăm sóc khách hàng** của công ty mình thì **ta có thể
> fine-tuning tiếp với các data của mình.**

<br>

<a id="node-l93h8jo"></a>

<p align="center"><kbd><img src="assets/f9uyq8zukoo.png" width="80%"></kbd></p>

> [!NOTE]
> Trong P.A ta sẽ làm việc đó, tức là **fine-tune để tiếp
> tục cải thiện hơn khả năng summarization của FLAN
> T5 với bộ dialogsum dataset**

<br>

<a id="node-5tc7uun"></a>

<p align="center"><kbd><img src="assets/r4dcltdyqg.png" width="80%"></kbd></p>

> [!NOTE]
> Một **ví dụ** cho thấy câu trả lời của model FLAN-T5 
> trước và sau khi fine-tuning với **dialogsum**

<br>

<a id="node-yd90aqs"></a>

<p align="center"><kbd><img src="assets/ol4zlftsv3h.png" width="80%"></kbd></p>

<br>

<a id="node-lahzxqc"></a>

<p align="center"><kbd><img src="assets/9yn3zkkvn2.png" width="80%"></kbd></p>

> [!NOTE]
> Cho thấy sau khi tuned
> model **summarize tốt hơn**

<br>

<a id="node-gnojei0"></a>

<p align="center"><kbd><img src="assets/poepcnsiciq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái nói là có thể fine-tuned tiếp với
> **data của mình** để cải thiện model hơn nữa phù
> hợp với l**ĩnh vực cụ thể**

<br>

<a id="node-753z2mu"></a>

### Scaling Instruct Models

<br>

<a id="node-57c5ags"></a>

> [!NOTE]
> This paper\\/ https://arxiv.org/abs/2210.11416\\/
>
>  introduces FLAN (Fine-tuned LAnguage Net), an instruction
> finetuning method, and presents the results of its application. The study
> demonstrates that by fine-tuning the 540B PaLM model on 1836 tasks while
> incorporating Chain-of-Thought Reasoning data, FLAN achieves improvements
> in generalization, human usability, and zero-shot reasoning over the base
> model. The paper also provides detailed information on how each these aspects
> was evaluated.

<br>

<a id="node-onbp7l7"></a>

<p align="center"><kbd><img src="assets/kkmtgdqen.png" width="80%"></kbd></p>

> [!NOTE]
> Here is the image from the lecture slides that illustrates the fine-tuning tasks and datasets employed
> in training FLAN. The task selection expands on previous works by incorporating dialogue and
> program synthesis tasks from Muffin and integrating them with new Chain of Thought Reasoning
> tasks. It also includes subsets of other task collections, such as T0 and Natural Instructions v2. Some
> tasks were held-out during training, and they were later used to evaluate the model's performance on
> unseen tasks

<br>

<a id="node-dc1zi88"></a>

### Model Evaluation

<br>

<a id="node-sax3140"></a>

> [!NOTE]
> 1. The speaker discusses the challenge of evaluating the performance of large language models,
> particularly in **non-deterministic** and **language-based tasks**.
>
> 2. **Traditional machine learning** metrics like **accuracy** are **not sufficient for language models** due
> to the **complexity of language** and the **non-deterministic nature of their outputs.**
>
> 3. Two widely used evaluation metrics for language models are **ROUGE** (**Recall Oriented
> Understudy for Gisting Evaluation**) and **BLEU** (**Bilingual Evaluation Understudy**).
>
> 4. **ROUGE** measures the **quality of automatically generated summaries** by **comparing them to
> human-generated reference summaries**, while **BLEU evaluates the quality of machine-translated
> text.**
>
> 5. **ROUGE-1** focuses on **individual words (unigrams)**, **ROUGE-2** takes **bigrams into account**, and
> **ROUGE-L** considers the **longest common subsequence** between the **generated and reference
> outputs**.
>
> 6. Both **ROUGE** and **BLEU** have **limitations**, such as **rewarding repeated words** and **not
> considering the ordering of words**.
>
> 7. **Pre-written libraries**, like those from **Hugging Face**, make it easy to calculate **ROUGE**  and
> **BLEU** scores for **model evaluation**.
>
> 8. While ROUGE and BLEU can be used as **diagnostic evaluation tools**, they should not be the
> **sole basis for reporting the final evaluation of a large language model.**
>
> 9. Researchers use **evaluation benchmarks** to provide a **more comprehensive** and **robust**
> assessment of a language model's performance.

<br>

<a id="node-dpj4mec"></a>

<p align="center"><kbd><img src="assets/99nc1e0kdq5.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **traditional model** thường dùng các metric như **accuracy** để đánh giá vì nó là các
> **deterministic** - tức là những **vấn đề có thể định lượng là đúng hay sai một cách tuyệt đố**i.
> Trong khi đó **LLM** thường giải quyết c**ác vấn đề un-deterministic liên quan đến ngôn ngữ** -
> nôm na là **không có định nghĩa tuyệt đối là đúng hay sai nên để evaluate LLM khó hơn**

<br>

<a id="node-cmolhcm"></a>

<p align="center"><kbd><img src="assets/dc1xxfh0jk.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với các vấn đề liên quan đến **language** của LLM thì **đôi khi chỉ khác
> có 1 chữ thôi** ý nghĩa đã khác hoàn toàn. Hoặc cùng **một ý nhưng có câu hay câu
> dở**. Não người dễ dàng nhận ra khác biệt nhưng máy tính thì không. Ta cần phải có
> những **metric để đánh giá khả năng của model một cách có hệ thống.**

<br>

<a id="node-p8bak26"></a>

<p align="center"><kbd><img src="assets/z8mow1rvl0j.png" width="80%"></kbd></p>

> [!NOTE]
> Hai thông số trong đó **BLEU** score mình đã gặp trong
> DLSpec dùng để **đánh giá Translation Model**. Đại khái nó
> sẽ **so sánh kết quả của model với con người,**

<br>

<a id="node-nf9hzdu"></a>

<p align="center"><kbd><img src="assets/8o6uynuvw59.png" width="80%"></kbd></p>

> [!NOTE]
> Nhắc lại một chút các khái niệm **uni-gram**,
> **bi-gram** và **n-gram** trong language model là
> những cụm 1 2 hoặc n từ sát nhau

<br>

<a id="node-72mfceu"></a>

<p align="center"><kbd><img src="assets/9lpt638wq9v.png" width="80%"></kbd></p>

> [!NOTE]
> Cách tính **ROUGE 1** khá **naive** chỉ quan tâm đến **độ '
> matching' của các từ đơn lẻ** trong model output **so với
> human output.** **Không quan tâm đến thứ tự**

<br>

<a id="node-cradnd7"></a>

<p align="center"><kbd><img src="assets/264r1gmxzll.png" width="80%"></kbd></p>

<br>

<a id="node-vq2sqib"></a>

<p align="center"><kbd><img src="assets/vwnavzqfmf9.png" width="80%"></kbd></p>

> [!NOTE]
> Và cách này bộc lộ nhiều **nhược điểm** khi như ví dụ này
> có c**hữ "not" khiến ý nghĩa hai câu hoàn toàn trái ngược**
> nhưng **ROUGE của model vẫn cao**

<br>

<a id="node-1qj7l07"></a>

<p align="center"><kbd><img src="assets/luieqwrxzdg.png" width="80%"></kbd></p>

> [!NOTE]
> Thay vì dùng uni-gram thì có thể **dùng bi-gram để cải thiện hơn chút**
> ít cách đánh gía khi **có tính thêm một ít yếu tố thứ tự của từ**. Ta thấy
> chỉ số **ROUGE-2 nhỏ hơn so với ROUGE-1**

<br>

<a id="node-ffu3dhs"></a>

<p align="center"><kbd><img src="assets/q2ru7vy04x8.png" width="80%"></kbd></p>

> [!NOTE]
> Một cách khác là **tìm những subset dài
> nhất mà hai output match nhau.** Ví dụ "
> it is" và "cold outside"

<br>

<a id="node-rqqap2q"></a>

<p align="center"><kbd><img src="assets/c5qjvd6xk7a.png" width="80%"></kbd></p>

> [!NOTE]
> Và tính chỉ số ROUGE-L. Tuy nhiên, các chỉ số
> ROUGE c**hỉ có thể compare các model có chung 1
> task.**

<br>

<a id="node-k792dvm"></a>

<p align="center"><kbd><img src="assets/a5lg9rbdg6p.png" width="80%"></kbd></p>

> [!NOTE]
> ROUGE có nhược điểm như đã nói là có
> thể **model tệ mà vẫn có điểm cao. Ví dụ
> hai trường hợp dưới**

<br>

<a id="node-nr3ysxw"></a>

<p align="center"><kbd><img src="assets/lz84hage0j.png" width="80%"></kbd></p>

<br>

<a id="node-w9zxjsc"></a>

<p align="center"><kbd><img src="assets/9tzqyrr2jfd.png" width="80%"></kbd></p>

> [!NOTE]
> BLUE thì **tính trung bình chỉ số
> precision trên tất cả các n-gram**

<br>

<a id="node-ntay0a3"></a>

### Benchmarks

<br>

<a id="node-w2leexj"></a>

> [!NOTE]
> 1. **Evaluating Language Models (LLMs)** requires **more comprehensive benchmark**s beyond simple
> metrics like rouge and blur scores.
>
> 2. **Pre-existing datasets and associated benchmarks** established by LLM researchers help measure
> and compare LLMs holistically.
>
> 3. **Selecting the right evaluation dataset** is crucial to **accurately assess an LLM's performance** and
> **understand its true capabilities.**
>
> 4. Benchmarks like **GLUE** (General Language Understanding Evaluation) and **SuperGLUE** cover
> **various natural language tasks**, encouraging the development of models that can **generalize across
> multiple tasks**.
>
> 5. As models get larger, **their performance against benchmarks like SuperGLUE approaches
> human-level ability on specific tasks**, but they **still fall short in general human-like performance.**
>
> 6. Recent benchmarks like **Massive Multitask Language Understanding** (**MMLU**) and **BIG-bench**
> push LLMs further, testing models on **tasks that require extensive world knowledg**e and
> **problem-solving abilities.**
>
> 7. The **Holistic Evaluation of Language Models** (**HELM**) is a **benchmark framewor**k that aims to
> i**mprove model transparency** and **offers guidance on model selection for specific tasks**.
>
> 8. HELM employs a **multimetric approach**, measuring **seven metrics** across **16 core scenario**s,
> including **fairness, bias, and toxicity**, which are crucial as LLMs become more capable of human-like
> language generation.
>
> 9. HELM is a l**iving benchmark** that continuously evolves with the **addition of new scenarios, metrics,
> and models, providing valuable insights for project needs.**

<br>

<a id="node-1g4sbxn"></a>

<p align="center"><kbd><img src="assets/fw26z7ynwin.png" width="80%"></kbd></p>

> [!NOTE]
> 1. Language Model (LLM) evaluation **requires more comprehensive metrics** than simple ones
> like rouge and blur scores to **fully understand a model's capabilities**.
>
>
>
> 2. To measure and compare LLMs effectively, researchers often **use pre-existing datasets** and
> **associated benchmarks** **specifically designed for LLM evaluation**.
>
>
>
> 3. **Choosing the right evaluation dataset** is **crucial** to **accurately assess an LLM's performance**
> and **understand its true capabilities**.
>
>
>
> 4. **Evaluation datasets** may **focus on specific model skills**, such as **reasoning** or **common sense**
> knowledge, or **address potential risks** like **disinformation or copyright infringement.**
>
>
>
> 5. An **important consideration** is whether the LLM has been **exposed to the evaluation data**
> during training. **Evaluating the model on unseen data** provides a **more accurate and useful
> understanding of its capabilities.**
>
> Đại khái là để đánh giá LLM **cần nhiều hơn là chỉ dựa vào các chỉ số như ROUGE hay
> BLEU scores**. Do đó người ta phát triển các **benchmark** - gọi là **thước đo chuẩn hoá để
> giúp đánh giá model** trên **nhiều khả năng khác nhau**.
>
>
>
> Và một việc quan trọng phải làm đó là **chọn được cái benchmark và evaluation dataset** để
> đo chính xác khả năng của model trong một tác vụ cụ thể.
>
>
>
> Nhưng evaluation dataset này **được thiết kế để test một khả năng nào đó của model như
> reasoning, disinformation,..**
>
>
>
> Cuối cùng một điểm quan trọng cần chú ý là p**hải đảm bảo model chưa từng được thấy
> dataset đó trong lúc training** vì như vậy sẽ khiến việc đánh giá không còn chính xác.

<br>

<a id="node-peiobv2"></a>

<p align="center"><kbd><img src="assets/8hzdjqrc8hm.png" width="80%"></kbd></p>

> [!NOTE]
> Một số các benchmark
>
> Benchmarks, such as GLUE, SuperGLUE, or Helm, cover a **wide range of tasks
> and scenarios**. They do this by **designing or collecting datasets** that **test specific
> aspects of an LLM.**

<br>

<a id="node-r62xg9o"></a>

<p align="center"><kbd><img src="assets/xdgfbcdyvd.png" width="80%"></kbd></p>

> [!NOTE]
> **GLUE**, or **General Language Understanding Evaluation**, was introduced in 2018.
> GLUE is a **collection of natural language tasks**, such as **sentiment analysis** and
> **question-answering**. GLUE was created to encourage the development of models
> that can **generalize across multiple tasks**, and you **can use the benchmark to
> measure and compare the model performance**.
>
> Đại khái là GLUE được tạo ra nhằm mục đích đánh gía **KHẢ NĂNG HIỂU
> NGÔN NGỮ NÓI CHUNG** của model đối với các task như sentiment
> analysis, question-answering.

<br>

<a id="node-sgts106"></a>

<p align="center"><kbd><img src="assets/njyjvjss7go.png" width="80%"></kbd></p>

> [!NOTE]
> As a **successor** to GLUE, **SuperGLUE** was introduced in 2019, to **address
> limitations** in its predecessor. It consists of a series of tasks, some of which
> are not included in GLUE, and some of which are **more challenging versions**
> of the same tasks. SuperGLUE includes **tasks such as multi-sentence
> reasoning**, and **reading comprehension**
>
> SuperGLUE nhằm **mục đích tăng độ khó** cũng như **khắc phục những
> nhược điểm của GLUE** và **mở rộng thêm các task** như **khả năng đọc
> hiểu, multi-sentence reasoning**

<br>

<a id="node-e1jg360"></a>

<p align="center"><kbd><img src="assets/4a7ipvh5xzk.png" width="80%"></kbd></p>

> [!NOTE]
> Both the GLUE and SuperGLUE benchmarks have **leaderboards** that can
> be used to c**ompare and contrast evaluated models**. The results page is
> another **great resource for tracking the progress of LLM**
>
> As models get larger, their **performance against benchmarks** such
> as **SuperGLUE** start to **match human ability** on specific tasks.
> That's to say that models are able to **perform as well as humans on
> the benchmarks tests**, but subjectively we can see that they're not
> performing at human level at tasks in general. There is **essentially an
> arms race between the emergent properties of LLMs**, and the
> **benchmarks that aim to measure them**
>
> Cả hai đều có leaderboard đánh giá các
> LLM trên những benchmark này
>
> Ý nói khi các model ngày càng phát triển, thì các
> benchmark ngày càng tiệm cận con người.

<br>

<a id="node-ita6w4k"></a>

<p align="center"><kbd><img src="assets/hdyyafx1cch.png" width="80%"></kbd></p>

> [!NOTE]
> 1. **Massive Multitask Language Understanding (MMLU)** is a benchmark designed specifically
> for **modern Language Models (LLMs)** to evaluate their e**xtensive world knowledge and
> problem-solving abilities**.
>
>
>
> 2. MMLU includes tasks that **go beyond basic language understanding**, such as **elementary
> mathematics**, **US history, computer science, law,** and more.
>
>
>
> 3. **BIG-bench** is another recent **benchmark** that encompasses a wide range of **204
> tasks**, covering areas **like linguistics, childhood development, math, common sense
> reasoning, biology, physics, social bias, and software development.**
>
>
>
> 4. BIG-bench offers **three different sizes of benchmarks** to manage **inference costs,** as
> running these large benchmarks can be **computationally expensive.**
>
> **MMLU** được design để **đánh giá các khả năng vượt ra phạm vi language như toán
> cơ bản, lịch sử** ,....Hoặc **BIG-bench** bao gồm **204 tasks như math, social bias,
> physic**s...Nó có nhiều v**ersion to nhỏ khác nhau để khách hàng chọn lựa**

<br>

<a id="node-i5ck2k9"></a>

<p align="center"><kbd><img src="assets/zbpzygazheh.png" width="80%"></kbd></p>

> [!NOTE]
> 1. The **Holistic Evaluation of Language Models** (HELM) is a **benchmark framework** designed to
> improve the **transparency** of language models and guide model selection for specific tasks.
>
>
>
> 2. HELM adopts a **multimetric approach**, using **seven metrics across 16 core scenarios** to provide
> a **comprehensive evaluation of language models**, revealing **trade-offs between models and
> metrics.**
>
>
>
> 3. HELM goes **beyond basic accuracy measures** and includes **metrics for precision, F1 score,
> fairness, bias, and toxicity**, which are essential for assessing **potential harmful behavior** as
> language models become more human-like.
>
>
>
> 4. **HELM** is a **dynamic benchmark** that continuously evolves by incorporating new scenarios,
> metrics, and models.
>
>
>
> 5. **Researchers and practitioners** can explore the HELM results page to browse evaluated
> language models and review scores relevant to their project's requirements.
>
> Còn HELM là một bm khác được design để **cải thiện transparency của language
> model.** Nó tiếp cận theo hướng **multi-centric approach** sử dụng **7 metrics trải rộng 16
> core scenarios** nhằm giúp **đánh giá khả năng ngôn ngữ của model**. Nó bao gồm cả các
> metric khư p**recisions, F1 score, fairness, bias và toxicity.** Helm liên tục được nâng cấp

<br>

<a id="node-jrdu3we"></a>

## Parameter Efficient Fine-tuning

<br>

<a id="node-s4gb5yy"></a>

### Peft

<br>

<a id="node-i8fg6lx"></a>

> [!NOTE]
> The passage discusses the concept of **Parameter Efficient Fine-Tuning** (PEFT) in the context of training
> Language Model Models (LLMs). The main ideas extracted from the text are as follows:
>
> 1. **Full fine-tuning** of LLMs is **computationally intensive** due to the **large memory requirements** for
> storing model **weights**, **optimizer states, gradients, forward activations, and temporary memory**
> throughout the training process.
>
> 2. **PEFT** is a method that **updates only a small subset of parameters** during **fine-tuning**,
> **reducing the memory requirements** significantly compared to full fine-tuning.
>
> 3. **PEFT** can **freeze most of the model weights**, focusing on fine-tuning **only a subset of existing
> model** **parameters**, or **add a small number of new parameters or layers** and fine-tune only the new
> components.
>
> 4. By using PEFT, the number of trained parameters becomes **much smaller** than the number of
> parameters in the original LLM, making the **memory requirements more manageabl**e, and in some
> cases, it can be performed on a **single GPU.**
>
> 5. PEFT is **less prone to catastrophic forgetting** problems that can occur during full fine-tuning.
>
> 6. Full fine-tuning **results in a new version of the model for every task**, leading to **expensive storage
> problems** when fine-tuning for multiple tasks.
>
> 7. PEFT allows **efficient adaptation of the original LLM** to multiple tasks by **training only a small
> number of weights** and **combining them with the original LLM weights** for inference.
>
> 8. There are t**hree main classes** of PEFT methods: s**elective methods, reparameterization methods,
> and additive methods.**
>
> 9. **Selective methods** fine-tune **only a subset of the original LLM parameters,** but they have **mixed
> performance** and **trade-offs** between parameter efficiency and compute efficiency.
>
> 10. **Reparameterization** methods **create new low rank transformations** of the original network
> weights, **reducing the number of parameters to train.**
>
> 11. **Additive** methods k**eep all of the original LLM weights frozen** and introduce **new trainable
> components,** such as **adapter** methods that **add new trainable layers** or **soft prompt method**s
> that **manipulate the input** to achieve better performance.
>
> 12. **Prompt tuning** is a **specific soft prompt techniqu**e that will be explored in the next lesson.
>
> Overall, the passage highlights the challenges of fine-tuning large LLMs and presents PEFT as an efficient
> approach to handle memory requirements and adapt models to multiple tasks effectively. It also outlines
> the different methods within the PEFT framework and their respective trade-offs.

<br>

<a id="node-iuny5p8"></a>

<p align="center"><kbd><img src="assets/762uuwq5fbq.png" width="80%"></kbd></p>

> [!NOTE]
> As you saw in the first week of the course, **training LLMs is computationally intensive**.
> **Full fine-tuning requires memory** not just to store the **model**, but various **other
> parameters** that are required during the training process. Even if your computer can hold
> the model weights, which are now on the order of **hundreds of gigabytes** for the largest
> models, you must also be able to allocate memory for **optimizer states, gradients,
> forward activations, and temporary memor**y throughout the training process
>
> Đại khái là nói rằng việc **full-fine tuning** - trong đó **mọi model's weight đều được tuned** /
> updated cũng **rất tốn memory** khi không chỉ cần chứa đủ **model mà còn là các
> optimizers states, gradients.**....Tổng cộng lại **có thể gấp 10 đến 20 lần model's weight**s

<br>

<a id="node-pcvj4m0"></a>

<p align="center"><kbd><img src="assets/3kxa2h64a2h.png" width="80%"></kbd></p>

> [!NOTE]
> In contrast to full fine-tuning where **every model weight is updated** during
> supervised learning, **parameter efficient fine tuning** methods **only update a
> small subset of parameters**. Some path techniques **freeze most of the
> model weight**s and **focus on fine tuning a subset of existing model
> parameters**, for example, particular **layers** or components.
>
> Đại khái là **PEFT** thì tiếp cận theo cách khác, **không cần update toàn
> bộ model's params** mà **chỉ một số thô**i. Có thể bằng cách **đóng băng
> phần lớn params** (hay layers), chỉ **chừa ra và fine tune một số khác**

<br>

<a id="node-unh2ix2"></a>

<p align="center"><kbd><img src="assets/8vyxeoehvgb.png" width="80%"></kbd></p>

> [!NOTE]
> Cách khác thì **hoàn toàn không động tới params cũ luôn** mà **thêm
> vào các trainable layers mới** và **update các params đó.**
>
> Other techniques **don't touch the original model weights** at all, and
> instead **add a small number of new parameters or layers** and
> **fine-tune only the new components**

<br>

<a id="node-vfwvtww"></a>

<p align="center"><kbd><img src="assets/q7s50ervh5.png" width="80%"></kbd></p>

> [!NOTE]
> With PEFT, most if not all of the **LLM weights are kept frozen**. As a result,
> the number of **trained parameters is much smaller** than the number of
> parameters in the original LLM. In some cases, just **15-20% of the original
> LLM weights**. This makes the **memory requirements for training much more
> manageable.** In fact, PEFT can often be performed on a **single GPU**. And
> because the original LLM is only slightly modified or left unchanged, PEFT is
> **less prone to the catastrophic forgetting** problems of full fine-tuning
>
> Đại khái là nhờ vậy mà **số params phải tune thấp hơn nhiều** nên cũng
> **giảm gánh nặng bộ nhớ** đòi hỏi đồng thời **giảm thiểu hiện tượng
> catastrophic forgetting** bởi vì **phần lớn hoặc tất cả các params cũ đều
> được giữ nguyên**

<br>

<a id="node-sm3gt59"></a>

<p align="center"><kbd><img src="assets/1lvmny5qskw.png" width="80%"></kbd></p>

> [!NOTE]
> Full fine-tuning **results in a new version of the model for every
> task** you train on. Each of these is the **same size** as the
> original model, so it can **create an expensive storage problem**
> if you're fine-tuning for multiple tasks.
>
> Đại khái là với full fine tuning thì **mỗi task được tune
> sẽ tạo một model có size tương đương**, thành ra để
> handle tất cả các task, ta phải **tăng khả năng lưu
> trữ lên tương xứng**

<br>

<a id="node-dzanlkv"></a>

<p align="center"><kbd><img src="assets/f1t366vwtsg.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ul3g6z0xais.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/und0mvdea9.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái với PEFT, **mỗi task kiểu như chỉ tạo thêm một số layers hay weights**.
> Và nó **sẽ được kết hợp với model cũ**. Tuy nhiên v**ới mỗi task khác nhau, kiểu
> như ta có thể rút cái này ra gắn cái kia vào** từ đó **không cần phải tốn quá nhiều
> storage để lưu trữ như full finetuning**

<br>

<a id="node-1g4r2fg"></a>

<p align="center"><kbd><img src="assets/1mymu176sgo.png" width="80%"></kbd></p>

> [!NOTE]
> Có nhiều cách làm với các ưu
> nhược điểm khác nhau

<br>

<a id="node-2bf104x"></a>

<p align="center"><kbd><img src="assets/ng2yx9rt79.png" width="80%"></kbd></p>

> [!NOTE]
> Selective methods are those that fine-tune **only a subset of the original LLM
> parameters**. There are **several approaches** that you can take to identify which
> parameters you want to update. You have the option to **train only certain
> components** of the model or specific layers, or even **individual parameter types**.
> Researchers have found that the **performance of these methods is mixed and
> there are significant trade-offs between parameter efficiency and compute
> efficiency.**
>
> Kiểu này đại khái là **chỉ lựa một subset các params** của LLM
> để f.t thôi, có nhiều cách làm nhưng **trade off giữa hiệu quả
> và compute efficiency khá cao** nên sẽ không nói tới ở đây

<br>

<a id="node-tq5djj3"></a>

<p align="center"><kbd><img src="assets/0x50l8qvqa7.png" width="80%"></kbd></p>

> [!NOTE]
> **Reparameterization** methods also **work with the original LLM parameters**, but r**educe
> the number of parameters to train** by \_**creating new low rank transformations of the
> original network weights**\_. A commonly used technique of this type is **LoRA**, which we'll
> explore in detail in the next video. Lastly, additive methods carry out fine-tuning by
> keeping all of the original LLM weights frozen and introducing new trainable
> components. Here there are two main approaches. **Adapter** methods a**dd new trainable
> layers** to the architecture of the model, typically inside the **encoder or decoder**
> components after the attention or feed-forward layers. **Soft prompt methods**, on the
> other hand, **keep the model architecture fixed** and frozen, and **focus on manipulating
> the input** to achieve better performance. This can be done by **adding trainable
> parameters to the prompt embeddings** or keeping the input fixed and **retraining the
> embedding weights**. In this lesson, you'll take a look at a specific soft prompts
> technique called prompt tuning
>
> Cái **Reparameterization** **cũng làm với model params** nhưng kiểu như **tạo một cái low
> rank transformation của cái model weights** **rồi mới update** điển hình nhất là **LoRA**. Sẽ
> nói rõ ở các bài sau
>
>
>
> Cuối cùng là **additive** kiểu như **add thêm layers vào, freeze cái model weights** và **chỉ
> update cái added layer's weight.** Có thể thêm vào Encoder hoặc Decoder.
>
>
>
> Còn cách **Soft Prompt** là nó sẽ **chỉ thay đổi cái input**, tức là nó t**rain lại cái embedding
> của iiput hoặc cái prompt**

<br>

<a id="node-0ohfoq6"></a>

### PEFT TECHNIQUES 1: LoRA

<br>

<a id="node-tf5ozag"></a>

> [!NOTE]
> 1. **LoRA** (**Low-rank Adaptation**) is a **parameter-efficient fine-tuning** technique falling into the
> **re-parameterization category**.
>
> 2. LoRA **reduces the number of parameters to be trained** during fine-tuning by **introducing
> low-rank decomposition matrices** alongside the **original weights in self-attention layers** of a
> language model.
>
> 3. The **dimensions of the low-rank matrice**s are set so that **their product approximates the
> attention weights being modified**.
>
> 4. During fine-tuning, the **original model parameters are frozen**, and only the **low-rank matrices
> are updated** using s**upervised learning**.
>
> 5. LoRA fine-tuning results in a **significant reduction in trainable parameters** while **achieving good
> performance gains**, making it **computationally efficient**.
>
> 6. **LoRA matrices are small**, allowing **fine-tuning for multiple task**s, with the ability to **switch out
> matrices at inference time**.
>
> 7. The **choice of rank for LoRA matrices** **impacts model performance**, and **ranks in the range
> of 4-32** offer a **good trade-off between parameter reduction** and **performance preservation**.
>
> 8. LoRA **can be applied to various models** beyond language models.
>
> 9. **Researchers** have found that **LoRA performs well and is a powerful fine-tuning method.**
>
> 10. **LoRA principles** can be **useful in other domains and models**.
>
> 11. The final path method, which focuses on training input text, will be explored next.

<br>

<a id="node-aa32umv"></a>

<p align="center"><kbd><img src="assets/9akfsrpctaw.png" width="80%"></kbd></p>

> [!NOTE]
> As a quick reminder, here's the diagram of the t**ransformer architecture**
> that you saw earlier in the course.

<br>

<a id="node-akjhr88"></a>

<p align="center"><kbd><img src="assets/7rdojgp9zw9.png" width="80%"></kbd></p>

> [!NOTE]
> The **input prompt is turned into tokens**, which are then
> **converted to embedding vectors**

<br>

<a id="node-f2sad7b"></a>

<p align="center"><kbd><img src="assets/adehks28f0d.png" width="80%"></kbd></p>

> [!NOTE]
> and **passed into the encoder
> and/or decoder parts of the transformer.**

<br>

<a id="node-gnd6swq"></a>

<p align="center"><kbd><img src="assets/2xo2foikt1n.png" width="80%"></kbd></p>

> [!NOTE]
> In both of these components, there are **two kinds of neural networks;
> self-attention** and **feedforward networks**. The **weights of these
> networks** are **learned during pre-training.**

<br>

<a id="node-3m4tuvt"></a>

<p align="center"><kbd><img src="assets/che37l4o36w.png" width="80%"></kbd></p>

> [!NOTE]
> After the **embedding** vectors are created, they're **fed into the
> self-attention layers** where a **series of weights are applied to
> calculate the attention scores.**

<br>

<a id="node-3k8uf3w"></a>

<p align="center"><kbd><img src="assets/v1wgz6thxi.png" width="80%"></kbd></p>

> [!NOTE]
> During **full fine-tunin**g, **every parameter
> in these layers is updated.**
>
> Đại khái là nói lại về **Transformer model** có **3 chỗ** chính có **weight được
> trained** đó là **Embedding** và **Self-Attention** và **Fully-connected layer**.
>
>
>
> Và trong **Full-Finetuning**, **toàn bộ các params** này đều được **update**

<br>

<a id="node-ohiz9vp"></a>

<p align="center"><kbd><img src="assets/2pnvvjiq9nu.png" width="80%"></kbd></p>

> [!NOTE]
> **LoRA** is a strategy that **reduces the number of parameter**s to be trained during
> fine-tuning by **freezing all of the original model parameters** and then \_**injecting a pair of
> rank decomposition matrices alongside the original weights.**\_
>
> Thì đại khái với **loRA**, nó **sẽ không đụng tới các params cũ**, mà chỉ kiểu như nó tạo một **Low
> rank decomposition matrices** - là một khái niệm trong toán học mô ta cách **dùng matrix U (m, k)
> và V (k, n)** với **k nhỏ hơn nhiều so với m và n** để tính **U.V xấp xỉ cho A (m, n)**. Thì loRa sẽ dùng
> cái phương pháp này với **weight matrix của model's Self-Attention layers**.

<br>

<a id="node-nqzr9mc"></a>

> [!NOTE]
> Low-rank decomposition, also known as low-rank approximation, is a **mathematical technique**
> used to **approximate a given matrix** with **two or more lower-dimensional matrices**. It is a way of
> **compressing information in the original matrix** while **retaining its essential features**. The resulting
> **lower-dimensional matrices** are called **low-rank decomposition matrices.**
>
> In the context of neural networks and language models like LLMs, low-rank decomposition can
> be applied to r**educe the complexity and computational cost of the model**. It is particularly useful
> when **dealing with large matrices**, as it can **significantly reduce the number of parameters** to be
> trained while **preserving important patterns and relationships within the data.**
>
> Suppose we have an original matrix **A** of size **m x n.** Low-rank decomposition approximates this
> matrix u**sing two smaller matrices, U and V,** with dimensions **m x k** and **k x n**, respectively, where
> k is typically much smaller than both m and n. The **product of U and V (U x V) is an
> approximation of the original matrix A.**
>
> Mathematically, low-rank decomposition can be represented as:
>
> **A ≈ U x V**
>
> where "≈" denotes the approximation.
>
> The key idea behind low-rank decomposition is to **represent the original matrix A** as a **sum of
> outer products of columns from U and rows from V**. This allows us to approximate A with a
> reduced number of parameters (k x (m + n)) instead of the original number of parameters (m x
> n).
>
> The process of finding the low-rank decomposition involves optimization techniques that seek to
> minimize the reconstruction error between the original matrix A and its approximation U x V.
>
> In the context of LLM fine-tuning with LoRA (Low-Rank Approximation), low-rank decomposition
> matrices are introduced alongside the original attention weight matrices in the self-attention
> layers. These low-rank matrices have reduced dimensions, and their product approximates the
> attention weights, allowing for efficient fine-tuning with fewer parameters to be updated. By using
> low-rank decomposition, the fine-tuning process becomes more computationally efficient without
> sacrificing the performance of the model.

<br>

<a id="node-v6mw1mh"></a>

<p align="center"><kbd><img src="assets/2krh6dgbt8z.png" width="80%"></kbd></p>

> [!NOTE]
> The **dimensions of the smaller matrices** are set so that
> **their product is a matrix** with the **same dimensions as
> the weights they're modifying**.

<br>

<a id="node-phl19c3"></a>

<p align="center"><kbd><img src="assets/4gohdpqe3v5.png" width="80%"></kbd></p>

> [!NOTE]
> You then **keep the original weights of the LLM frozen** and
> \_**train the smaller matrices**\_ using the **same supervised learning
> process you saw earlier this week.**
>
> Sau đó nó sẽ **train cái low rank decomposition matrices này**
> bằng **supervised learning** trong quá trình fine-tuning như đã biết

<br>

<a id="node-k7naq39"></a>

<p align="center"><kbd><img src="assets/2yfrpol89jb.png" width="80%"></kbd></p>

> [!NOTE]
> For inference, the **two low-rank matrices** are
> **multiplied together** to create a **matrix with the same
> dimensions as the frozen weights.**
>
> Đến khi **inference** (là lúc làm việc - predict) nó sẽ **nhân hai cái low
> rank matrices này lại (U.V)** để **add vào cái original matrix (ví dụ A).**

<br>

<a id="node-ullxq79"></a>

<p align="center"><kbd><img src="assets/3sjp1rszft3.png" width="80%"></kbd></p>

> [!NOTE]
> You then **add this to the original weights** and **replace
> them in the model with these updated values**.

<br>

<a id="node-t2u9fjl"></a>

<p align="center"><kbd><img src="assets/0udjrf5629rc.png" width="80%"></kbd></p>

> [!NOTE]
> You now have a LoRA fine-tuned model that can carry out your specific task.
>
>
>
> Because this model has the same number of parameters as the original, there is
> little to no impact on inference latency.
>
>
>
> Researchers have found that **applying LoRA to just the self-attention layers** of the
> model is **often enough to fine-tune** for a task and achieve performance gains.
>
>
>
> However, **in principle**, you can **also use LoRA on other components like the
> feed-forward layers.**
>
>
>
> But since **most of the parameters of LLMs are in the attention layers**, you get the
> **biggest savings in trainable parameters by applying LoRA to these weights
> matrices.**
>
> Thì đại khái là theo nghiên cứu thì c**hỉ cần apply loRA với Self-Attention
> layer là đủ** vì nó **chứa phần lớn params của model**. Tuy nhiên cũng
> **không hại gì khi làm luôn cho các component khác** như **Feed Forward
> layers** phía sau Self Attention

<br>

<a id="node-brqkv86"></a>

<p align="center"><kbd><img src="assets/ytugrw18bn.png" width="80%"></kbd></p>

> [!NOTE]
> Let's look at a practical example using the **transformer architecture** described in
> the **Attention is All You Need paper.** The paper specifies that the **transformer
> weights** have dimensions of **512 by 64**. This means that each **weights matrix has
> 32,768 trainable parameters**. If you use LoRA as a fine-tuning method with the
> rank equal to 8, you will instead train two small rank decomposition matrices
> whose small dimension is 8. This means that Matrix A will have dimensions of
> 8 by 64, resulting in **512** total parameters. Matrix B will have dimensions of 512 by
> 8, or **4,096** trainable parameters. By updating the weights of these new low-rank
> matrices instead of the original weights, you'll be training 4,608 parameters
> instead of 32,768 and **86% reduction**
>
> Đại khái là lấy ví dụ từ một layer của b**ase Transformer model** được
> giới thiệu lần đầu tiên năm **2017** trong nghiên cứu mang tên **Attention
> is All You Need**. Trong đó với **weight matrix có shape 512x64** sẽ có
> **32768 params**. Với loRa, số params phải train chỉ còn lại là **512 +
> 4096,** **thấp hơn rất nhiều  - giảm 86%**

<br>

<a id="node-6qnc0m3"></a>

<p align="center"><kbd><img src="assets/rwd5598xf6c.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/djwcdwb11te.png" width="80%"></kbd></p>

> [!NOTE]
> Ý là với cách này, ta **chỉ có thêm một ít weight cần lưu trữ** (thay vì với **mỗi
> task lại đẻ ra một cái model sẽ dẫn đến gánh nặng cho việc lưu trữ** tất cả
> model này). Nên ta **tha hồ mà làm với các task khác nhau**, **mỗi task thành
> một bộ đồ chơi để gắn vào model gốc khi cần inference.**

<br>

<a id="node-z2tym9l"></a>

<p align="center"><kbd><img src="assets/k5y7x8fmcv.png" width="80%"></kbd></p>

> [!NOTE]
> Cho thấy các chỉ số **ROUGE metrics** của LoRA fine-tuning model
> **không kém bao nhiêu so với full tuning model** nhưng lại **giảm
> rất nhiều số params phải train.**

<br>

<a id="node-6y2z3qd"></a>

<p align="center"><kbd><img src="assets/9pnq7tsd20t.png" width="80%"></kbd></p>

> [!NOTE]
> Câu hỏi về **rank nên chọn** đang được **active research**, theo nghiên cứu
> mới nhất với các mức Rank khác nhau và các chỉ số **val_loss**, **BLEU** và
> **ROUGE** scores....cho thấy từ **2-16 là mang lại lợi ích** còn **trở lên nữa
> như ta thấy val_loss không giảm là bao**.

<br>

<a id="node-q29ve4m"></a>

### Peft Techniques 2: Soft Prompt

<br>

<a id="node-a94xxnf"></a>

> [!NOTE]
> Main ideas from the text:
>
> 1. Introduction to **Parameter Efficient Fine Tuning** (PEFT): The text introduces **PEFT**, a method **aimed
> at efficiently updating model weights** or **improving model performance without training every parameter
> again**. PEFT includes two methods: **LoRA** and **Prompt Tuning.**
>
> 2. **Prompt Engineering** vs. **Prompt Tuning**: Prompt Engineering involves **manually crafting language
> prompts** to improve model completions, which can be **time-consuming** and **limited** by the **context
> window.** Prompt Tuning, on the other hand, **adds additional trainable tokens called soft prompts** to the
> prompt and a**llows the supervised learning process to determine their optimal values**, making it more
> efficient.
>
> 3. **Soft Prompts**: Soft prompts are **virtual tokens** in the **continuous multidimensional embedding space**,
> and the model **learns their values during supervised learning** to maximize performance for a given
> task. Soft prompts are **small** on disk and allow **easy swapping of tasks during inference**.
>
> 4. **Performance of Prompt Tunin**g: In comparison to full fine tuning, prompt tuning may **not perform as
> well for smaller language models (LLMs)**, but its performance i**mproves as the model size increases.**
> For LLMs with around **10 billion parameters**, **prompt tuning can be as effective as full fine tuning**,
> offering a significant performance boost over prompt engineering alone.
>
> 5. **Interpretability** of Soft Prompts: A potential concern is the i**nterpretability of learned virtual tokens**.
> While they **don't correspond to known tokens**, words, or phrases in the vocabulary, an analysis shows
> that the **nearest neighbor tokens to soft prompt location**s **form** t**ight semantic clusters**, **suggesting that
> the prompts are learning word-like representations.**
>
> 6. Recap of Week 2: The text briefly summarizes the content covered in week 2, including **instruction
> fine-tuning**, **prompt templates**, e**valuation metrics** (**ROUGE** and **HELM**), and the **effectiveness of PEFT**
> in reducing compute and memory resources during fine-tuning.
>
> Overall, PEFT, particularly **Prompt Tunin**g and **LoRA**, provides **efficient methods** for fine-tuning
> language models, making it **possible to achieve improved performance with reduced computational
> costs.**

<br>

<a id="node-4edu0yb"></a>

<p align="center"><kbd><img src="assets/xkh5tt5m3gp.png" width="80%"></kbd></p>

> [!NOTE]
> With **LoRA**, the goal was to **find an efficient way to update the weights** of the model
> **without having to train every single parameter again**. There are also **additive
> methods** **within PEFT** that aim to improve model performance without changing the
> weights at all. In this video, you'll explore a **second parameter efficient fine tuning
> method** called **prompt tuning**.
>
>
>
> Now, prompt tuning sounds a bit like **prompt engineering**, but they are quite different
> from each other. With prompt engineering, you **work on the language of your prompt** to
> get the completion you want. This could be as simple as **trying different words or
> phrases** or more complex, like **including examples** for **One or Few-shot Inference**.
> The goal is to **help the model understand the nature of the task you're asking** it to carry
> out and to **generate a better completion**. However, there are **some limitations** to
> prompt engineering, as it can **require a lot of manual effort to write and try different
> prompts**. You're also **limited by the length of the context window**, and at the end of the
> day, you may **still not achieve the performance you need** for your task
>
> Đại khái là nói về cách thứ 2 trong PEFT là **Prompt Tuning**. Trước hết nói lại
> về **Prompt Engineering** trong đó mình sẽ **thử các cách prompt khác nhau**
> như thử các **từ**, **phrase khác**, hoặc t**hêm example (One-shot)** hay **nhiều
> example (Few-shot inference)** mục đích **để model nó hiểu mình cần nó làm
> gì.** Tuy nhiên **hạn chế của context window** cũng như việc **phải manually thử
> đi thử lại nhiều lần** mà có khi vẫn không đạt được kết quả như ý muốn.

<br>

<a id="node-t0tu8or"></a>

<p align="center"><kbd><img src="assets/p43sf1zrcip.png" width="80%"></kbd></p>

> [!NOTE]
> With **prompt tuning**, you add **additional trainable tokens** to your prompt
> and **leave it up to the supervised learning process** to determine their
> **optimal values**. The set of trainable tokens is called a **soft prompt**, and
> it gets \_**prepended to embedding vectors that represent your input text**\_.
> The soft prompt vectors have the **same length as the embedding
> vectors** of the language tokens. And including somewhere between **20
> and 100 virtual tokens** can be sufficient for good performance
>
> Đại khái là **tạo thêm 20-100 cái embedding
> vector đại diện cho Soft-prompt** và **gắn vào
> embedding tensor** của input words.

<br>

<a id="node-i0qja83"></a>

<p align="center"><kbd><img src="assets/e4e2s8gwdxq.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/8uksr2xqrv7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/polkahssf7j.png" width="80%"></kbd></p>

> [!NOTE]
> The tokens that represent natural language are hard in the sense that they each correspond
> to a **fixed location in the embedding vector space**. However, the **soft prompts are not
> fixed discrete words** of **natural language**. Instead, you can **think of them as virtual
> tokens that can take on any value within the continuous multidimensional embedding space.**
>
>
>
> And through **supervised learning**, the model **learns the values for these virtual tokens**
> that **maximize performance for a given task**.
>
> Chưa hiểu lắm nhưng đại khái **không như prompt thông thường** là các **từ cụ thể** thì
> **soft prompt** sẽ **không phải là một discrete fixed words** **trong ngôn ngữ** kiểu như một
> / những từ cụ thể nào đó, mà nó **là một vector / dãy con số nào đó trong
> embedding space**.

<br>

<a id="node-rpj22mk"></a>

<p align="center"><kbd><img src="assets/lm7rvjgrb9i.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/sg850wtib1l.png" width="80%"></kbd></p>

> [!NOTE]
> In full fine tuning, the training data set consists of **input prompts and output
> completions or labels**. The weights of the large language model are updated
> during supervised learning. In contrast with prompt tuning, the **weights of the
> large language model are frozen** and the underlying model does not get updated.
> Instead, the **embedding vectors of the soft prompt gets updated over time to
> optimize the model's completion of the prompt.** Prompt tuning is a very parameter
> efficient strategy because **only a few parameters are being trained**. In contrast
> with the millions to billions of parameters in full fine tuning, similar to what you
> saw with LoRA. You can train a **different set of soft prompts for each task and
> then easily swap them out at inference time.**
>
> Đại khái là giống lora, quá trì**nh fine-tuning chỉ train/update các giá trị của của
> soft-prompt embedding**, **không động tới LLM weights**. Vì mỗi
> bộ soft prompt được train rất nhẹ và **có thể train nhiều task** để tạo **các bộ
> soft-prompt khác nhau để switch qua lại khi perform các task khác nhau lúc inference**

<br>

<a id="node-878zvks"></a>

<p align="center"><kbd><img src="assets/znp8hnk97i.png" width="80%"></kbd></p>

> [!NOTE]
> You can **train a set of soft prompts for one task** and **a different set for
> another**. To use them for inference, you **prepend your input prompt with the
> learned tokens** to switch to another task, you **simply change the soft
> prompt**. Soft prompts are **very small on disk,** so this kind of fine tuning is
> **extremely efficient and flexible**
>
> Switch qua lại có nghĩa là **với các task khác
> nhau**, lúc inference, ta **chỉ việc gắn bộ
> soft-prompt khác vào input embedding**

<br>

<a id="node-8k8zewq"></a>

<p align="center"><kbd><img src="assets/wernjxs24ch.png" width="80%"></kbd></p>

> [!NOTE]
> Kết quả cho thấy với **small LLM thì prompt-tuning không
> bằng** nhưng với **LLM lớn hơn thì nó ngang ngửa Full-fine
> tuning**. Và **vượt xa prompt engineering**

<br>

<a id="node-hgccceb"></a>

<p align="center"><kbd><img src="assets/3jprnod27db.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là như ta đã nói, **soft-prompt sau khi train** là một v**ector nằm trong embedding
> space** không phải là / ta k**hông biết được nó là hay có represent những từ cụ thể nào**
> trong ngôn ngữ không - nên mới gọi là **virtual token vì nó có thể là bất cứ giá trị nào
> trong không gian liên tục**
>
>
>
> (Kiểu như mỗi từ được embedding thành 1 vector, nhưng bốc 1 vector trong embedding
> space ra thì chưa chắc nó map với một từ thuộc ngôn ngữ mình dùng )
>
>
>
> nhưng n**ghiên cứu những từ lân cận cho thấy model learn được soft-prompt là "dạng
> dạng" của những từ này**
>
> One potential issue to consider is the **interpretability** of **learned** **virtual tokens.**
> Remember, because the **soft prompt tokens \_can take any value within the continuous
> embedding vector space**\_. The \_**trained tokens don't correspond to any known
> token**\_, word, or phrase in the vocabulary of the LLM. However, an analysis of the
> **nearest neighbor tokens** to the soft prompt location **shows that they form tight
> semantic clusters**. In other words, the **words closest to the soft prompt tokens have
> similar meanings**. The words identified usually have \_**some meaning related to the
> task, suggesting that the prompts are learning word like representations**\_

<br>

<a id="node-21rlpqg"></a>

<p align="center"><kbd><img src="assets/fvowwsy2m7p.png" width="80%"></kbd></p>

> [!NOTE]
> You explored two PEFT methods in this lesson **LoRA**, which uses **rank
> decomposition matrices** to update the model parameters in an efficient way. And
> **Prompt Tuning,** where **trainable tokens are added to your prompt** and the model
> weights are left untouched. Both methods **enable you to fine tune model**s with the
> potential for improved performance on your tasks while using **much less compute
> than full fine tuning methods**. LoRA is b**roadly used** in practice because of the
> **comparable performance to full fine tuning** for many tasks and data sets, and you'
> ll get to try it out for yourself in this week's lab.
>
> Nói chung **LoRA** và **Prompt tuning** là **hai phương pháp của PEFT** giúp fine
> tune model giúp n**ó cải thiện các task cụ thể một cách hiệu quả** và **tiết kiệm** so
> với **full tuning.** Trong đó **loRa được sử dùng rộng rãi hơn** vì khả năng của nó
> cho thấy **không kém cạnh gì full fine tuning**

<br>

<a id="node-6fqc6k7"></a>

<p align="center"><kbd><img src="assets/3btge7iou35.png" width="80%"></kbd></p>

<br>

<a id="node-jx6bq33"></a>

### Lab 2 Walktrhough

<br>

<a id="node-2m15dbp"></a>

> [!NOTE]
> Certainly, here are the main ideas extracted from the provided text:
>
> 1. **Lab Introduction and Goals:**
>    - This week's lab involves **trying out fine-tuning with PEFT and LoRA** to enhance the 
> **summarization ability** of the **Flan-T5 model.**
>    - Chris, a colleague, will guide through the lab activities.
>
> 2. **Lab 2 Overview and **Hands-On Approach**:**
>    - Lab 2 focuses on **hands-on experience** with **full fine-tuning** and **Parameter-Efficient 
> Fine-Tuning (PEFT)** using **prompt instructions**.
>    - Goal is to **improve Flan-T5 model** for **summarization** with personalized prompts.
>
> 3. **Model Fine-Tuning:**
>    - For f**ull fine-tuning**, individual model **weights are modified for summarization task** 
> using dataset.
>    - SageMaker instance type: **8 CPU, 32GB (ml.m5.2xl).**
>    - Required libraries installation: **torch, torchdata, evaluates, LoRA, PEFT.**
>
> 4. **Library and Model Setup:**
>    - **Load datasets**, **original model**, and **tokenizer**.
>    - Define **convenience functions** for **data handling and tokenization**.
>
> 5. ****Full Fine-Tuning**:**
>    - **Tokenize** and **create prompts** for dataset elements.
>    - **Utilize TrainingArguments** and **Trainer** from **transformers library** for training.
>    - **Evaluate model performance using ROUGE metric.**
>
> 6. ****Comparative Evaluation**:**
>    - **Compare summaries** generated by **original Flan-T5**, **instruction fine-tuned model**, and 
> **PEFT model**.
>    - **Qualitative assessment** of sample inputs.
>    - Quantitative assessment using **ROUGE metrics.** 
> 7. **Parameter-Efficient Fine-Tuning (**PEFT**):**
>    - Introduction of PEFT and its efficiency in resource usage.
>    - **Utilize LoRA rank parameter for PEFT configuration**.
>    - Limit training to only a small portion of model parameters (1.4%).
>
> 8. **Resource Management and Inference:**
>    - Set **is_trainable flag to false** to indicate **inference-only operation**.
>    - This **minimizes resources needed for prediction**, **reducing memory, and computation footprint.**
>
> 9. **Comparison of Model Outputs:**
>    - **Compare human baseline, original Flan-T5, instruction fine-tuned, and PEFT fine-
> tuned model outputs**.
>    - Use **ROUGE** metrics to q**uantitatively evaluate summarization** quality.
>
> 10. **PEFT Performance Evaluation:** **- Show PEFT's slightly lower ROUGE performance compared to full fine-tuning**.
>      - Emphasize **PEFT's efficiency in terms of resource usage** and **time savings** for larger 
> datasets.
>
>
> These main ideas cover the lab's content, including the introduction, the objectives of Lab 
> 2, hands-on fine-tuning, resource-efficient PEFT, model comparison, and evaluation 
> using ROUGE metrics.

<br>

<a id="node-pbig85y"></a>

<p align="center"><kbd><img src="assets/bldhxsdf4tb.png" width="80%"></kbd></p>

<br>

<a id="node-zsv2hyb"></a>

<p align="center"><kbd><img src="assets/8fwwbyr12ko.png" width="80%"></kbd></p>

<br>

<a id="node-277qz1j"></a>

<p align="center"><kbd><img src="assets/uuwv56n33rs.png" width="80%"></kbd></p>

> [!NOTE]
> đại khái là để rút ngắn thời gia, download cái pre-train
> (checkpoint) được train với thời gian lâu hơn

<br>

<a id="node-o98qed4"></a>

<p align="center"><kbd><img src="assets/ya2hdqky5a.png" width="80%"></kbd></p>

<br>

<a id="node-9n8nvt4"></a>

<p align="center"><kbd><img src="assets/vtxhri6z8cr.png" width="80%"></kbd></p>

> [!NOTE]
> Cho thấy Full-fine tuning model
> đã cải thiện hơn original model ở
> summarization task

<br>

<a id="node-cn3p134"></a>

<p align="center"><kbd><img src="assets/pz0570af3uk.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp, đánh giá
> bằng ROUGE

<br>

<a id="node-w6mc7f2"></a>

<p align="center"><kbd><img src="assets/da2gxgnqd7j.png" width="80%"></kbd></p>

> [!NOTE]
> Lấy 10 câu trong tét
> sét để đánh giá

<br>

<a id="node-ko5iq1x"></a>

<p align="center"><kbd><img src="assets/698jmniw39b.png" width="80%"></kbd></p>

> [!NOTE]
> Cho thấy ROUGE score cao
> hơn original model

<br>

<a id="node-u1p3h64"></a>

<p align="center"><kbd><img src="assets/ofdlt3wo2ga.png" width="80%"></kbd></p>

> [!NOTE]
> Đánh giá tiếp với nhiều data hơn save
> trong csv file này/ cho thấy ROUGE
> score cao hơn khá rõ

<br>

<a id="node-4mq5udd"></a>

<p align="center"><kbd><img src="assets/wa48sivl7h.png" width="80%"></kbd></p>

> [!NOTE]
> rồi xem thử Improvement
> theo percentage

<br>

<a id="node-wj2gyb6"></a>

<p align="center"><kbd><img src="assets/ad140qq76h4.png" width="80%"></kbd></p>

<br>

<a id="node-eypfdo8"></a>

<p align="center"><kbd><img src="assets/sxqd464g31.png" width="80%"></kbd></p>

> [!NOTE]
> Rank 32

<br>

<a id="node-aj6fjwt"></a>

<p align="center"><kbd><img src="assets/mowf5xf2r4g.png" width="80%"></kbd></p>

> [!NOTE]
> một convenient function của Peft lib tiện cho viêc tạo
> lora model với lora config và original model

<br>

<a id="node-tbjqwwj"></a>

<p align="center"><kbd><img src="assets/7pmu92npoag.png" width="80%"></kbd></p>

> [!NOTE]
> Số trainable
> param chỉ co 1.4%

<br>

<a id="node-1ck4fao"></a>

<p align="center"><kbd><img src="assets/g9yn55v0jx.png" width="80%"></kbd></p>

<br>

<a id="node-agf7ol7"></a>

<p align="center"><kbd><img src="assets/f5vyfgye5v.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự, cũng pretrained
> trước, load ra cho nhanh

<br>

<a id="node-lf9efzf"></a>

<p align="center"><kbd><img src="assets/xw76irpgt3e.png" width="80%"></kbd></p>

> [!NOTE]
> Cho thấy chỉ có 14 megabyte
>
>
>
> Khúc này nói ta phải merge vào original model trước khi inference
>
>
>
> Và có thể swap các PEFT adapter khi cần cho những task khác nhau

<br>

<a id="node-38lz0h9"></a>

<p align="center"><kbd><img src="assets/qm36j28gi8h.png" width="80%"></kbd></p>

> [!NOTE]
> Khúc này nhấn mạnh khi inference
> thì set is_trainable = False để tiết
> kiệm compute resource

<br>

<a id="node-594hbx6"></a>

<p align="center"><kbd><img src="assets/5wrvyc0h3gp.png" width="80%"></kbd></p>

<br>

<a id="node-zfczlmp"></a>

<p align="center"><kbd><img src="assets/3a15svi931w.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự test bằng mắt
> người trước, thấy nó ok

<br>

<a id="node-iosq30e"></a>

<p align="center"><kbd><img src="assets/iu0cdb3mjc.png" width="80%"></kbd></p>

> [!NOTE]
> test băng ROUGE score thấy nó kém
> full fine-tuning nhưng không tệ khi nó
> nhẹ hơn nhiều

<br>

<a id="node-pu98lid"></a>

<p align="center"><kbd><img src="assets/2fzfiva91tj.png" width="80%"></kbd></p>

<br>

<a id="node-4kdlegq"></a>

> [!NOTE]
> LAB 2 - FINE-TUNE A GENERATIVE AI
> MODEL FOR DIALOGUE SUMMARIZATION

<br>

<a id="node-l5got3y"></a>

> [!NOTE]
> In this notebook, you will fine-tune an existing **LLM** from **Hugging Face**
> for **enhanced dialogue summarization**. You will use the **FLAN-T5** model, which provides a **high quality instruction tuned model** and can
> summarize text out of the box. To improve the inferences, you will
> explore a **full fine-tuning approac**h and **evaluate the results** with
> **ROUGE** metrics. Then you will perform **Parameter Efficient
> Fine-Tuning (PEFT),** evaluate the resulting model and see that the
> benefits of PEFT outweigh the slightly-lower performance metrics.

<br>

<a id="node-uehzdiq"></a>

> [!NOTE]
> 1 - Set up Kernel, Load Required
> Dependencies, Dataset and LLM

<br>

<a id="node-1epi1fw"></a>

> [!NOTE]
> 1.1 - Set up Kernel and
> Required Dependencies

<br>

<a id="node-olo5xfq"></a>

<p align="center"><kbd><img src="assets/5iow2ih4axg.png" width="80%"></kbd></p>

<br>

<a id="node-uvps3ds"></a>

<p align="center"><kbd><img src="assets/vt3uhd855gp.png" width="80%"></kbd></p>

<br>

<a id="node-0s889l1"></a>

<p align="center"><kbd><img src="assets/j5022u6ecao.png" width="80%"></kbd></p>

> [!NOTE]
> Install các lib cần thiết torch, transformer,
> datasets, evaluate, rouge_score, lorallib, peft.

<br>

<a id="node-wkvguoy"></a>

<p align="center"><kbd><img src="assets/w7qukltt6xn.png" width="80%"></kbd></p>

<br>

<a id="node-xb7vlce"></a>

##### 1.2 - Load Dataset and LLM

<br>

<a id="node-5zng1mi"></a>

<p align="center"><kbd><img src="assets/72whn7yv3sh.png" width="80%"></kbd></p>

> [!NOTE]
> Tiếp tục làm việc với **DialogSum dataset** của **Hugging Face** có
> **10.000 dialogues** được **labeled với summaries và topics**

<br>

<a id="node-6qgqfbl"></a>

<p align="center"><kbd><img src="assets/0c4ck1656e3d.png" width="80%"></kbd></p>

<br>

<a id="node-5wu97pl"></a>

<p align="center"><kbd><img src="assets/vrehnmlajor.png" width="80%"></kbd></p>

> [!NOTE]
> Bộ dataset có cấu trúc như vầy là
> dictionary chứa ba dataset
> train/validation/test. Mỗi bộ có 4 features

<br>

<a id="node-1pdcc5c"></a>

<p align="center"><kbd><img src="assets/5okll837muu.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là ta sẽ load cái **pre-trained LLM là FLAN-T5** và cái **tokenizer**
> tương ứng từ **HuggingFace** library. Chỉ dùng phiên bản nhỏ của nó, và
> **set memory type** với câu lệnh **torch_dtype = torch.bfloat16**

<br>

<a id="node-dwnjy8b"></a>

<p align="center"><kbd><img src="assets/35wtqnob38j.png" width="80%"></kbd></p>

> [!NOTE]
> Cho một function để xem s**ố lượng trainable parameter của model**.
>
>
>
> Xem sơ qua thì cơ bản là **loop trong các params của model** bằng function model.
> **named_parameters**() và xem cái cái có var **requires_grad** = True thì tính cộng thêm
> vào số lượng **trainable param**s bằng **param.numel()**
>
>
>
> Kết quả cho thấy **FLAN-T5** này có 247 triệu trainable params

<br>

<a id="node-hg3jqns"></a>

> [!NOTE]
> 1.3 - Test the Model with
> Zero Shot Inferencing

<br>

<a id="node-hfdpzdu"></a>

> [!NOTE]
> Test the model with the zero shot inferencing. You can see
> that the **model struggles to summarize the dialogue
> compared to the baseline summary**, but it **does pull out some
> important information** from the text which indicates the model
> **can be fine-tuned to the task at hand**

<br>

<a id="node-wmw9r6w"></a>

<p align="center"><kbd><img src="assets/a2q445vwt6a.png" width="80%"></kbd></p>

> [!NOTE]
> **Lấy trong bộ test set,** dùng index=200 lấy ra data sample, lấy cái cột 
> 'dialogue' sẽ dùng để đưa vào model để predict và 'summary' là summary
> do người tạo, sẽ dùng để so sánh cũng như là finetuning
>
>
>
> Tạo prompt theo dạng: 
>
>
>
> "Summarize the ...: 
> + dialog +
> Summary:"
>
>
>
>
> Bỏ qua **tokenizer()** function của H.F để tokenize.
>
>
>
> Bỏ vào model để **predict (generate)** 
>
>
>
> In ra kết quả và human's summary để so sánh

<br>

<a id="node-27kj2ne"></a>

<p align="center"><kbd><img src="assets/4avt5v3hjze.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái ta nhận xét là nó trả lời **khá tệ** khi
> cơ bản không phải là summarization.

<br>

<a id="node-9zace5d"></a>

##### 2 - Perform Full Fine-Tuning

<br>

<a id="node-143d6bd"></a>

##### 2.1 - Preprocess the Dialog-Summary Dataset

<br>

<a id="node-te5vm47"></a>

<p align="center"><kbd><img src="assets/aadeyksuibk.png" width="80%"></kbd></p>

> [!NOTE]
> Convert cái **dialog-summary pairs**
> thành dạng **explicit instructions.**

<br>

<a id="node-jyjuqiz"></a>

<p align="center"><kbd><img src="assets/oig3iorkdal.png" width="80%"></kbd></p>

> [!NOTE]
> Function **tokenize_function()** sẽ nhận một dataset giúp:  Dùng list comprehension,
> loop qua các dialogue trong cột 'dialogue' của dataset để tạo prompt theo dạng:
>
>
>
> "Summarize the ...",   dialog  "Summary":
>
>
>
> Bỏ kết qủa **vào tokenizer của Hugging Face** với các hyper-params như padding dùng
> max_length, truncation=True có lẽ là cho phép cắt bớt câu dài. Kết qủa sẽ là list prompt được
> tokenized (thành dạng index)
>
>
>
> Sau đó, **gán thành một cột mới 'input_ids'** vào dataset (example)
>
>
>
> Lấy cột 'summary' của dataset ra, tokenize tương tự rồi assign vào cột mới có tên '**labels**'
>
>
>
> ===
>
>
>
> map function này với dataset, như vậy nó sẽ dùng function này để tạo ra hai column mới
> như trên đã nói 'input_ids' chứa tokenized prompt data và 'labels' chứa tokenized 'label' là
> cái human-based summary.
>
>
>
> Cuối cùng là drop đi các cột id, topic, dialogue, summary. Chỉ còn lại 2 cột trên

<br>

<a id="node-igf6ar0"></a>

<p align="center"><kbd><img src="assets/s599iydnge.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây để cho giảm thời gian người ta dùng filter để **tạo bộ subdata
> nhỏ hơn** kiểu như cứ 100 cái thì lấy 1 cái.
>
>
>
> Có thể thấy, Dataset bây giờ chỉ còn có 2 column, là iput_ids và labels
> và số row chỉ = 1/100 bộ gốc

<br>

<a id="node-0ebveqn"></a>

> [!NOTE]
> Certainly! This piece of code is part of a data preprocessing pipeline for 
> fine-tuning a Large Language Model, such as GPT-3, on a summarization task. 
> Summarization tasks involve generating concise and coherent summaries of 
> longer pieces of text, like conversations in this case. Let's break down the code 
> and explain its context step by step:
>
> 1. **Import Libraries and Set Up Tokenizer:**
>    Before this code snippet, you would need to import the necessary libraries, 
> including the Hugging Face `transformers` library, which provides pre-trained 
> language models and tokenization functions. The code assumes that you have already 
> imported the required libraries and initialized the `tokenizer` variable.
>
> 2. **Tokenize Function:**
>    The `tokenize_function` is defined to process a single example from your dataset. 
> The input to this function is an example, which seems to be a dictionary containing at least the following keys:
>    - `"dialogue"`: A list of strings representing the conversation/dialogue.
>    - `"summary"`: A string representing the summary of the conversation.
>
> 3. **Start and End Prompts:**
>    The function first creates a `start_prompt` and an `end_prompt`. 
>    These prompts are added to the dialogue to form the input for the model. 
>    The `start_prompt` is added before each dialogue, and the `end_prompt` is added after each dialogue.
>
> 4. **Tokenization and Padding:**
>    - The `prompt` list is constructed by combining each dialogue with the start 
> and end prompts.
>    - The `tokenizer` is then used to tokenize the combined prompts. Tokenization 
> involves breaking the text into smaller units (tokens) that the language model can 
> understand.
>    - `padding="max_length"` ensures that the tokenized sequences are padded to the 
> maximum length within a batch, which is required for efficient batch processing during 
> training.
>    - `truncation=True` handles cases where the text is longer than the maximum token 
> limit, by truncating it to fit.
>    - The tokenized sequences are returned as PyTorch tensors, specifically the `input_ids` 
> which are the numerical representations of the tokens.
>
> 5. **Label Tokenization:**
>    The summary text is tokenized in a similar manner as the prompt, and its tokenized `input_ids` 
> are extracted. These tokenized summaries will serve as the labels during training, where the 
> model's task is to generate similar sequences.
>
> 6. **Updating Example:**
>    The `input_ids` for both the prompt and summary are added to the example dictionary.
>
> 7. **Return Processed Example:**
>    The modified example dictionary, now including tokenized inputs and labels, is returned 
> by the `tokenize_function`.
>
> 8. **Dataset Preprocessing:**
>    - The `map` function applies the `tokenize_function` to each example in the dataset in batches.
>    - The `remove_columns` function removes unnecessary columns like `'id'`, `'topic'`, `'dialogue'`, 
> and `'summary'` from the processed dataset.
>    - The `filter` function is applied to further downsample the dataset. It retains only every 100th 
> example, discarding the rest. This can be useful for speeding up experimentation.
>
> The overall purpose of this code is to process the raw dialogue and summary data into a format 
> suitable for fine-tuning the language model on the summarization task. It tokenizes the text, prepares 
> input-output pairs (prompt-dialogue, summary), and creates a dataset that is then ready for training 
> the language model.

<br>

<a id="node-z1du8po"></a>

> [!NOTE]
> 2.2 - Fine-Tune the Model with the
> Preprocessed Dataset

<br>

<a id="node-my9ud8c"></a>

<p align="center"><kbd><img src="assets/8rcjz6xq1om.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là sử dụng **HuggingFace's Trainer class**. Đầu tiên là tạo TrainingArguments 
> với một số parameters khác qua thử nghiệm người ta thấy vậy là good (learning rate, 
> num_train_epochs, ...)
>
>
>
> Khởi tạo Trainer với **preprocessed data (train và eval set)**, **original model** và training
> argument.

<br>

<a id="node-xhecdkm"></a>

<p align="center"><kbd><img src="assets/4idcxhsvtg4.png" width="80%"></kbd></p>

> [!NOTE]
> Gọi train() để start training

<br>

<a id="node-5atgjk5"></a>

<p align="center"><kbd><img src="assets/cyduv91ikn8.png" width="80%"></kbd></p>

> [!NOTE]
> Thì đại khái là train mất nhiều thời gian, nên họ sẽ **load pre-trained (checkpoint) để dùng**.
>
>
>
> Và sẽ dùng tên gọi **instruct model** để chỉ cái model này - cái model được **full - finetuning**
>
>
>
> Để ý dùng **AutoModelForSeq2SeqLM.from_pretrained**(file path chứa cái model checkpoint)

<br>

<a id="node-9iz1hve"></a>

<p align="center"><kbd><img src="assets/k7jj1tp9dg.png" width="80%"></kbd></p>

> [!NOTE]
> Cái checkpoint download về đây,

<br>

<a id="node-ylikywf"></a>

> [!NOTE]
> 2.3 - Evaluate the Model
> Qualitatively (Human Evaluation)

<br>

<a id="node-vtx94lo"></a>

<p align="center"><kbd><img src="assets/a0mv9pdd9c7.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/qoclzp2qncj.png" width="80%"></kbd></p>

> [!NOTE]
> Chú ý là ở trên ta chỉ tạo bộ dataset với hai cột mới, còn dataset cũ nó vẫn còn đó.
>
>
>
> Lấy index = 200. Lấy **dialogue** và cái **ground truth human-based label** của nó từ cột
> '**summary**' ra từ bộ **test set.** 
>
>
>
> Tạo prompt theo pattern như trên 
> (Summary the following + dialog + Summary:)
>
>
>
> Dùng **tokenizer để tokenize cái prompt thành input_ids**
>
>
>
> Bỏ vào **model.generate()** với **generation config**. 
>
>
>
> Dùng **tokenizer để decode nó ra text để xem.**
>
>
>
> Kết quả cho thấy model **đã cải thiện** được khả năng đối với task summarization này
> Khi kết quả có thể thấy nó đã có vẻ như là một summary

<br>

<a id="node-csl6la1"></a>

> [!NOTE]
> 2.4 - Evaluate the Model
> Quantitatively (with ROUGE Metric)

<br>

<a id="node-ycxdm5u"></a>

<p align="center"><kbd><img src="assets/3m0evw4wo9m.png" width="80%"></kbd></p>

> [!NOTE]
> Kế tiếp dùng **ROUGE** metric để **đánh gía một cách hệ thống** hơn vì
> không thể cứ in ra rồi ngồi check được. Thì ROUGE nó sẽ so sánh
> model's prediction với các ground truth label là summary do human
> tạo ra.
>
>
>
> Đầu tiên l**oad cái rouge model từ evaluate lib**

<br>

<a id="node-bptez0g"></a>

<p align="center"><kbd><img src="assets/y7n0ptmlyr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **lấy 10 data sample** đầu tiên từ test set để đưa vào model (original) (tương tự như ở trên chỉ
> khác loop trong 10 cái lần lượt, tạo prompt, tokenize đưa cho model predict và dùng tokenizer
> để decode ra dạng text và bỏ vào cái list original_model_summaries
>
>
>
> Làm tương tự nhưng với instruct model - cái đã full fine-tuning
>
>
>
> Cũng chuẩn bị 1 list chứa human summary. 
>
>
>
> Như vậy ta có bộ summary chuẩn, bộ summary do original model và do full fine tuning model
>
>
>
> Xong zip lại và dùng Panda để show ra

<br>

<a id="node-6vz2vml"></a>

<p align="center"><kbd><img src="assets/ut6lv1qr3gb.png" width="80%"></kbd></p>

<br>

<a id="node-sdjs15h"></a>

<p align="center"><kbd><img src="assets/l9n39sd4dv.png" width="80%"></kbd></p>

> [!NOTE]
> Dùng **rouge library** để check **ROUGE** metric, bỏ vào function **compute ()**
> original model prediction và human summary để xem Rouge score của 
> original model
>
>
>
> Và tương tự compute() với instructed model prediction và human summary
> để xem rouge score của fine tunned model
>
>
>
> Cho thấy chỉ số của prediction do **Instruct model** cao hơn của **original model**

<br>

<a id="node-o6fofot"></a>

<p align="center"><kbd><img src="assets/13kbtz9e7jwh.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/ipiy3gewp1d.png" width="80%"></kbd></p>

> [!NOTE]
> Check với nhiều câu hơn chứa trong file csv,

<br>

<a id="node-xb445gq"></a>

<p align="center"><kbd><img src="assets/sqthzsbmcx8.png" width="80%"></kbd></p>

> [!NOTE]
> Xem thử improvement theo % cho thấy
> Instruct model quả thật cải thiện hơn

<br>

<a id="node-qvwxgv7"></a>

> [!NOTE]
> 3 - Perform Parameter
> Efficient Fine-Tuning (PEFT)

<br>

<a id="node-xqhuw5h"></a>

<p align="center"><kbd><img src="assets/bz17cc6m3ne.png" width="80%"></kbd></p>

> [!NOTE]
> Như đã biết trong lecture, PEFT cho phép fine tuning model để kiểu **không tác
> động tới original pre-trained params** của LLM, mà thay vào đó nó **chỉ train ra thêm
> một bộ params nhỏ** - mà với phương pháp LoRA thì người ta gọi là **LoRA adapter.**
>
>
>
> Và vì **nó nhỏ**, nên việc training (fine-tuning) cũng **không tốt kém quá nhiều compute
> expense** cũng như là **yêu cầu lưu trữ** cho những extra newly trained params này.
>
>
>
> Với cách làm này, thì **với mỗi specific task khác nhau**, sẽ **tạo ra một bộ params khác
> nhau** và khi dùng người ta sẽ ..kiểu như **gắn nó vào cùng với pre-train params cũ** của
> LLM. Tuy hơn bất tiện nhưng cũng đồng nghĩa là **với task khác nhau người ta chỉ cần
> thay thế bộ LoRa adapter khác**.
>
>
>
> Nói thêm là k**hi nhắc đến PEFT khả năng cao người ta đang nói tới LoRA**

<br>

<a id="node-52l4qnv"></a>

> [!NOTE]
> 3.1 - Setup the PEFT/LoRA
> model for Fine-Tuning

<br>

<a id="node-t01v6pp"></a>

<p align="center"><kbd><img src="assets/qhhar5nqxsp.png" width="80%"></kbd></p>

> [!NOTE]
> Đầu tiên ra sẽ set up configuration cho LoRa, thông số rank. 
>
>
>
> Như đã
> biết trong lecture, phương pháp này đại khái là ví dụ như LLM weight
> matrix là A (m,n) thì nó sẽ train 2 matrix U (m,r) và V(r,n) với r là rank nhỏ
> hơn nhiều m, n. Dẫn tới là U và V có số params nhỏ hơn nhiều A
>
>
>
> Ví dụ A = 1000x1000 = 1 triệu params. 
> U = 1000x10: 10.000 params, V = 10x1000 = 10.000 params -> UV chỉ
> có 20.000 parasm nhỏ hơn rất nhiều lần so với 1 triệu.
>
>
>
> Và khi train xong, khi dùng Inference, ta sẽ cộng UV (m,r x r,n = m,n)
> vào A.
>
>
>
> ===
>
>
>
> Các hyper-params khác có thể hiểu sơ như lora_dropout có thể là dropout rate
> liên quan đến việc dùng Dropout để regularization, task_type là SEQ2SEQ vì
> Đang làm task text summarization là sequence to sequence
>
>
>
> ===
>
>
>
> Cuối cùng là dùng function get_peft_model Theo video walkthrough nói là
> Convenient function của lora giúp tạo một 'lora model' dựa vào model cũ và lora
> config.
>
>
>
> In ra xem số trainable params cho thấy số lora params chỉ chiếm 1% của toàn bộ

<br>

<a id="node-xpf2c15"></a>

##### 3.2 - Train PEFT Adapter

<br>

<a id="node-1qjfyxc"></a>

<p align="center"><kbd><img src="assets/k5t2cwvc1.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự, cũng dùng Hugging Face's trainer để train. Với lora model, và
> bộ preprocessed data (bộ data với 2 columns input_ids và labels

<br>

<a id="node-ul8dgov"></a>

<p align="center"><kbd><img src="assets/ycm0n7u966c.png" width="80%"></kbd></p>

> [!NOTE]
> Tương tự load pre-trained
> checkpoint cho nhanh

<br>

<a id="node-lm4dcxu"></a>

> [!NOTE]
> 3.3 - Evaluate the Model
> Qualitatively (Human Evaluation)

<br>

<a id="node-315jn0n"></a>

> [!NOTE]
> 3.4 - Evaluate the Model
> Quantitatively (with ROUGE Metric)

<br>

<a id="node-u14r6ks"></a>

### Week 2 Quiz

<br>

<a id="node-8r82k3b"></a>

<p align="center"><kbd><img src="assets/dqe7xlyt8y.png" width="80%"></kbd></p>

<br>

<a id="node-ykk7kv5"></a>

<p align="center"><kbd><img src="assets/naqyz4e7od.png" width="80%"></kbd></p>

<br>

<a id="node-pj69pfn"></a>

<p align="center"><kbd><img src="assets/fhkpah09nb6.png" width="80%"></kbd></p>

<br>

<a id="node-elqkn3r"></a>

<p align="center"><kbd><img src="assets/2296ld3912di.png" width="80%"></kbd></p>

<br>

<a id="node-bsxscm9"></a>

<p align="center"><kbd><img src="assets/xcksih6631.png" width="80%"></kbd></p>

<br>

<a id="node-pghj5qb"></a>

<p align="center"><kbd><img src="assets/70tb9wukopv.png" width="80%"></kbd></p>

<br>

<a id="node-eu3ypj2"></a>

<p align="center"><kbd><img src="assets/ijal94qndph.png" width="80%"></kbd></p>

<br>

<a id="node-6x3s5uc"></a>

<p align="center"><kbd><img src="assets/y8v3epa5f6.png" width="80%"></kbd></p>

<br>

<a id="node-zjsvozk"></a>

<p align="center"><kbd><img src="assets/wbs4t4onys.png" width="80%"></kbd></p>

<br>

<a id="node-m02gv1m"></a>

<p align="center"><kbd><img src="assets/v2ffbj5ujoj.png" width="80%"></kbd></p>

<br>

<a id="node-ru85roi"></a>

### Week 2 Res

<br>

