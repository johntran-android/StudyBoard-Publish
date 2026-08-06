# C3w1_machine Learning Strategy 1

📊 **Progress:** `42` Notes | `47` Screenshots

---
<a id="node-rm48y2s"></a>

## C3w1_machine Learning Strategy 1

<br>

<a id="node-j3qt811"></a>

## Introduction To Ml Strategy

<br>

<a id="node-t3s1olx"></a>

### Why Ml Strategy

<br>

<a id="node-558nzl3"></a>

> [!NOTE]
> 1 The course teaches strategies for structuring a machine learning project to
> improve efficiency and quickly get systems working.
>
> 2 The example given is of improving a cat classification system with 90% accuracy.
>
> 3 There are many ideas to try to improve a deep learning system, but choosing the
> wrong approach can waste time.
>
> 4 The course teaches strategies for analyzing a machine learning problem to
> identify the most promising ideas to pursue.
>
> 5 The instructor will share lessons learned from building and shipping deep
> learning products.
>
> 6 The strategies taught in the course are unique and not commonly taught in
> university deep learning courses.
>
> 7 Machine learning strategy has changed with the emergence of deep learning
> algorithms.
>
> 8 The course aims to make learners more effective at getting deep learning
> systems to work.

<br>

<a id="node-fvxbghl"></a>

<p align="center"><kbd><img src="assets/dmyubci6juw.png" width="80%"></kbd></p>

> [!NOTE]
> Đâu là hướng đi khôn ngoan
> nhất để cải thiện model

<br>

<a id="node-753ejec"></a>

### Orthogonalization

<br>

<a id="node-cqk9mdf"></a>

> [!NOTE]
> In machine learning, "\\*orthogonalization\\*"
> refers to the principle of \\*separating
> concerns\\* so that changes in one aspect of
> the system do not affect other aspects.
>
> Specifically, it means breaking down the
> machine learning process into modular
> components, each of which has a specific
> responsibility, and ensuring that 
> \\*changes to one component do not have unintended
> consequences for other components\\*. This
> makes it easier to develop, debug, and
> maintain complex machine learning systems.

<br>

<a id="node-txu080w"></a>

<p align="center"><kbd><img src="assets/chebpez9gl.png" width="80%"></kbd></p>

> [!NOTE]
> Tách bạch mục tiêu ra để dễ kiểm soát

<br>

<a id="node-5b8s3jw"></a>

<p align="center"><kbd><img src="assets/l1q2pz63jcj.png" width="80%"></kbd></p>

> [!NOTE]
> In machine learning, "**orthogonalization**"
> refers to **the principle of separating
> concerns so that changes in one aspect of
> the system do not affect other aspects**.
>
>
>
> Specifically, it means **breaking down the
> machine learning process into modular
> components**, each of which has a **specific
> responsibility**, and ensuring that 
>
>
>
> **changes to one component do not have unintended
> consequences for other components**. This
> makes it easier to develop, debug, and
> maintain complex machine learning systems.

<br>

<a id="node-xnzs3dw"></a>

## Settng Up Your Goal

<br>

<a id="node-ik8rnum"></a>

### Single Number Evaluation Metric

<br>

<a id="node-9ixhmnn"></a>

> [!NOTE]
> 1 Using a \\*single evaluation metric\\* can help improve progress in a machine
> learning project by quickly determining if the new idea is working better or
> worse than the last one.
>
> 2 \\*Precision\\* and \\*recall\\* are reasonable ways to evaluate the performance of
> classifiers in terms of recognizing images of cats.
>
> 3 Using precision and recall as evaluation metrics can present a \\*problem of
> tradeoff\\*, making it difficult to determine which classifier is better if one classifier
> does better on recall while the other does better on precision.
>
> 4 \\*Combining precision and recall into a single evaluation metric\\* can help
> quickly select the better classifier. The standard way to combine precision and
> recall is using an F1 score, which is the harmonic mean of precision and recall.
>
> 5 Having \\*a well-defined dev set and a single evaluation metric allows\\* for
> quicker selection of the better classifier and speeds up the iterative process of
> improving the machine learning algorithm.
>
> 6 In building a cat app for cat lovers in four major geographies, using a single
> evaluation metric is necessary to compare the performance of two classifiers
> that have different errors for different geographies.

<br>

<a id="node-cw5nsjo"></a>

<p align="center"><kbd><img src="assets/p3kwj7n8b1a.png" width="80%"></kbd></p>

> [!NOTE]
> Có một metric để đo lường thì sẽ nhanh hơn nhiều metric.

<br>

<a id="node-0o3lu05"></a>

<p align="center"><kbd><img src="assets/as4z3l6oux.png" width="80%"></kbd></p>

<br>

<a id="node-0kay94f"></a>

### Satisficing And Optimizing Metric

<br>

<a id="node-159yk7s"></a>

> [!NOTE]
> 1 Introduction: It is \\*not always
> easy to combine\\* all the  things you care about into a single
> evaluation metric.
>
> 2 Setting up \\*satisficing\\* and \\*optimizing\\* metrics: It is sometimes
> useful to set up satisficing and optimizing metrics  to evaluate
> multiple factors. Satisficing metrics are those that\\* just need to be
> good enough\\*,  while optimizing metrics are those that you want to
> \\*maximize\\*.
>
> 3 Example 1: Combining accuracy and running time to evaluate a
> cat's classifier.
>
> 4 Example 2: Combining accuracy and false positives to evaluate
> a trigger word detection system.
>
> 5 Summary: If there are multiple things you care about, you can
> set up one as an optimizing metric and one or more as satisficing
> metrics to quickly evaluate multiple options.   
>
> 6 Evaluation metrics
> must be calculated on a\\* training set, development set, or test set.\\*

<br>

<a id="node-58bcjic"></a>

<p align="center"><kbd><img src="assets/yv8ot2i3n0g.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Nên đánh giá theo cách như thế này: 
> Có 1 cái metric để Optimize/ Maximize và những cái
> còn lại để 'Satisfy'

<br>

<a id="node-8ocxlee"></a>

### Train / Dev / Test Distributions

<br>

<a id="node-7vu5b0t"></a>

> [!NOTE]
> 1 Setting up training, development and test sets properly is \\*crucial\\* for
> maximizing team efficiency when building machine learning applications.
>
> 2 The \\*dev\\* set, also known as the development set, is \\*used to evaluate
> different models\\* and pick one to improve for the final test set.
>
> 3 \\/\\*Dev and test sets need to come from the same distribution\\*\\/ to avoid
> unexpected and unwanted results.
>
> 4 \\*Randomly shuffling all data into the dev and test sets\\* is the best way to
> ensure that both sets have data from all regions and the same distribution.
>
> 5 Teams can waste a lot of time and effort by setting up \\*dev\\* and \\*test\\* sets from
> different distributions or not taking into account all possible data sources they
> may encounter.
>
> 6 \\*Choose a dev set and test set to reflect data expected to be encountered in
> the future,\\* and consider important for the application's success.

<br>

<a id="node-xe8s5o3"></a>

<p align="center"><kbd><img src="assets/04fgk2xgjbf4.png" width="80%"></kbd></p>

> [!NOTE]
> So, having dev and test sets from different distributions is like 
> **setting a target**, having your team **spend months trying to 
> aim closer** and closer to bull's eye, only to realize after 
> months of work that, you'll say, "Oh wait, **to test it, I'm going 
> to move target over here**." And, the team might say, 
> "Well, why did you make us spend months optimizing for a 
> different bull's eye when suddenly, you can move the bull's eye to 
> a different location somewhere else?"

<br>

<a id="node-rtu3zma"></a>

<p align="center"><kbd><img src="assets/kvi7i4uz88l.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là phân chia dev/test set sai (ko cùng 1 distribution) sẽ
> dẫn đến sau khi train ngon rồi thì test sai bét.
>
>
>
> Do đó đây nói đến việc **định hướng train/dev set ban đầu rất
> quan trọng.**

<br>

<a id="node-tv21su5"></a>

<p align="center"><kbd><img src="assets/xec3y0clh9.png" width="80%"></kbd></p>

> [!NOTE]
> I recommend for setting up a **dev** set and **test** set is, choose
> a dev set and test set to **reflect data you expect to get in
> future** and consider important to do well on. And, in
> particular, the dev set and the test set here, should come
> from **the same distribution**. So, **whatever type of data you
> expect to get in the future, and want to do well o**n, **try to
> get data that looks like that**. /**And, whatever that data is, put
> it into both your dev set and your test set.**/
>
> **""And, whatever that data is, put
> it into both your dev set and your test set."**

<br>

<a id="node-6a4axn7"></a>

### Size Of The Dev Set And Test Sets

<br>

<a id="node-n6m1j8s"></a>

> [!NOTE]
> 1 Introduction  • Guidelines for setting up dev and test sets are changing in the era
> of Deep Learning.  • The old rule of thumb of a \\*70/30 split no longer applies\\*.  • Best
> practices are to \\*use more data for training and less for dev and tests\\*, especially
> when dealing with larger data sets.
>
> 2 Dev Set  • \\*Dev sets should come from the same distribution as the test set.\\*  • The
> size of the dev set should be big enough for its purpose, which helps evaluate
> different ideas and pick up from AOP better.  • When working with larger data sets,
> using a much smaller fraction of the data for the dev set is reasonable.
>
> 3 Test Set  • The purpose of the test set is to \\*evaluate the final system's
> performance\\*.  • The guideline is to set the test set big enough to give high
> confidence in the overall performance of the system.  • Having millions of examples
> in the test set may not always be necessary.  • The test set size could be much less
> than 30% of the data, depending on the application.
>
> 4 Train-Dev Set  • Some applications may not require a high level of confidence in
> the overall performance of the final system.  • Using a train-dev set and
> acknowledging the absence of a test set may be appropriate.  • It's not
> recommended, but \\*having a large dev set may allow for the absence of a separate
> test set.\\*
>
> 5 Changing Evaluation Metrics and Dev/Test Sets  • Sometimes, mid-way through a
> machine learning problem, it \\*may be necessary to change the evaluation metric or
> dev/test sets\\*.  • It's important to be aware of when to do this and how to properly set
> up the new evaluation metric and dev/test sets.

<br>

<a id="node-ik90tq4"></a>

<p align="center"><kbd><img src="assets/abe2fj7uuvu.png" width="80%"></kbd></p>

<br>

<a id="node-56bc7mx"></a>

<p align="center"><kbd><img src="assets/6t722smysvu.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là NGÀY NAY BIG DATA thì chỉ cần 1%,2% cho Dev / Test set
> là đủ cho MỤC ĐÍCH của nó rồi.
>
>
>
> Thậm chí có thể không cần Test set mặc dù ổng vẫn recommend 
> Train / Dev (CV) / Test set với Test set để cho ra con số performance
> trước khi ship đi.
>
> 1 The guidelines for **setting up dev and test sets are changing in the Deep
> Learning era**, especially because of the larger data set sizes we are
> working with.
>
>
>
> 2 In earlier eras of machine learning, a **70/30 or 60/20/20** split for training,
> dev, and test sets was reasonable, but **with larger data sets, it is now
> reasonable to use a much smaller fraction of data for dev and test sets**.
>
>
>
> 3 The purpose of the test set is to evaluate the performance of the final
> system, and it should be set to a size that **gives high confidence in the
> overall performance of the system**. For some applications, a smaller test
> set size may be sufficient.
>
>
>
> 4 For some applications, **a train and dev set without a test set may be
> sufficient** if a high confidence in the overall performance of the final system
> is not needed.
>
>
>
> 5 It is important to be rigorous about **calling the dev set a dev set** if it is
> being used for tuning rather than evaluation.
>
>
>
> 6 In the era of big data, the old **rule of thumb** for setting up dev and test
> sets **no longer applies**, and the trend is to **use more data for training
> and less for dev and test sets.**
>
>
>
> 7 It may be necessary to change the evaluation metric or the dev and test
> sets partway through a machine learning problem, depending on the
> progress made and the goals of the project.

<br>

<a id="node-ptflcuy"></a>

### When To Change Dev / Test Sets And Metrics

<br>

<a id="node-nw8lw4y"></a>

> [!NOTE]
> 1 \\*Evaluation metrics are essential\\* in ML projects for setting targets and
> enabling the team to achieve better results.
>
> 2 \\*Evaluation metrics should be changed when the original metric does not lead
> to the desired results\\*. Pornographic images and non-pornographic images
> should be treated differently in evaluation metrics.
>
> 3 \\*Orthogonalization\\* is a technique that can be used to break ML projects into
> separate steps to achieve better results. One step involves defining a metric that
> captures what one wants to do, while the other step involves placing the target
> accurately.
>
> 4 To achieve better results in ML projects, one needs to\\* focus on different steps
> and adjust the knobs\\* that correspond to these steps.

<br>

<a id="node-m930n0k"></a>

<p align="center"><kbd><img src="assets/876qc404hbq.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là kết quả ko như ý muốn thì ta cần thay đổi
>
>
>
> Model A ít sai hơn như khi sai lại nhận định có hình sex là mèo.
> Model B sai nhiều hơn nhưng ko có hình sex -> Phải sao cho nó ít
> nhận sai hình sex hơn
>
>
>
> Than đổi hàm J để nó nhấn mạnh sự quan trọng của việc Đánh giá
> sai đ/v Porn image bằng cách thêm tham số
>
>
>
> Đại ý là không cần stick với hàm cost thường dùng mà có thể điều
> chỉnh để thoả mãn nhu cầu
>
> For the purpose of this video, don't worry too much about the
> details of how we define a new error metric, the point is that
> **if you're not satisfied with your old error metric then don't
> keep coasting with an error metric you're unsatisfied with,
> instead try to define a new one that you think better
> captures your preferences in terms of what's actually a better
> algorithm.**
>
> So when this happens, when your evaluation metric is no longer
> correctly rank ordering preferences between algorithms, in this
> case is mispredicting that Algorithm A is a better algorithm, then
> that's a sign that you should change your evaluation metric or
> perhaps your development set or test set.

<br>

<a id="node-4dqdzqk"></a>

<p align="center"><kbd><img src="assets/triu7v8cra.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là đây là ví dụ minh hoạ cho '**Orthogonalization**'
> principle: Mỗi thứ 1 núm vặn độc lập với nhau.
>
>
>
> Cụ thể hơn:
>
>
>
> Step 1 là ta **define metric cho chính xác.**
> Step 2 là ta **làm sao để cải thiện metric này**.
>
>
>
> Đó đại khái hai bước độc lập, phù hợp với nguyên tắc
> **Mỗi lúc một việc hay mỗi núm 1 chức năng độc lập**
>
> In machine learning, "orthogonalization"
> refers to **the principle of separating
> concerns so that changes in one aspect of
> the system do not affect other aspects**.
>
>
>
> Specifically, it means **breaking down the
> machine learning process into modular
> components**, each of which has a **specific
> responsibility**, and ensuring that 
>
>
>
> **changes to one component do not have unintended
> consequences for other components**. This
> makes it easier to develop, debug, and
> maintain complex machine learning systems.

<br>

<a id="node-v7wxkdb"></a>

<p align="center"><kbd><img src="assets/677n0h6d7vr.png" width="80%"></kbd></p>

> [!NOTE]
> But the overall guideline is **if your current metric and data
> you are evaluating on doesn't correspond to doing well on
> what you actually care about, then change your metric
> and/or your dev/test set** to better capture what you need
> your algorithm to actually do well on.
>
>
>
> Đại khái đây nói đến trường hợp train model để (detect
> mèo) ngon rồi nhưng thực tế user xài ảnh của họ tự chụp
> khiến model chạy hết ngon thì  sẽ nói vấn đề này sau nhưng
> ý nói ở đây là phải thay đổi metric  và target

<br>

<a id="node-e5ajd0q"></a>

<p align="center"><kbd><img src="assets/vz35cl5cp0g.png" width="80%"></kbd></p>

> [!NOTE]
> Having an **evaluation metric and the dev set allows you to much
> more quickly make decisions** about is Algorithm A or Algorithm
> B better. It really speeds up how quickly you or your team can
> iterate. So my recommendation is, **even if you can't define the
> perfect evaluation metric and dev set, just set something up
> quickly and use that to drive the speed of your team iterating.**
>
> And if later down the line you find out that it wasn't a good one, you
> have better idea, change it at that time, it's perfectly okay. But what I
> recommend against for the most teams is to **run for too long without
> any evaluation metric and dev set** up because that can slow down
> the efficiency of what your team can iterate and improve your
> algorithm.

<br>

<a id="node-zxmkg4c"></a>

## Comparing To Human-level Performance

<br>

<a id="node-199ygpt"></a>

### Why Human-level Performance

<br>

<a id="node-dvpjg28"></a>

> [!NOTE]
> Main ideas of the lecture are as follows:
>
> 1 Machine learning teams are interested in comparing machine learning systems to
> human-level performance because of the advances in deep learning, and because the
> workflow is more efficient when the machine is trying to do something that humans can do.
>
> 2 Progress in accuracy for machine learning tasks tends to be relatively rapid as you
> approach human-level performance, but then slows down once you surpass it.
>
> 3 \\*Bayes optimal error\\* is the best possible error for any function mapping from x to y, and it is
> the theoretical limit that the machine learning algorithm \\*can approach but never surpass\\*.
>
> 4 Progress often slows down when you surpass human-level performance because the
> performance is not far from Bayes' optimal error, and \\*certain tactics for improving
> performance are harder to apply once the algorithm surpasses human-level performance\\*.
>
> 5 Comparing to human-level performance is helpful because machine learning algorithms
> tend to be good at replicating tasks that people can do and catching up to human-level
> performance.
>
> 6 How humans can help improve machine learning algorithms and why comparing algorithm
> performance to human performance is helpful. When humans are better at a task than the
> algorithm, labeled data can be obtained from humans to train the algorithm. Human error
> analysis can also be used to gain insights into improving algorithm performance. However,
> once the algorithm surpasses human performance, these tactics become harder to apply.
> Additionally, knowing how well humans can perform on a task can help to better understand
> how to balance reducing bias and reducing variance in the algorithm.

<br>

<a id="node-64qeomq"></a>

<p align="center"><kbd><img src="assets/ry694z930i.png" width="80%"></kbd></p>

> [!NOTE]
> Tăng nhanh, khi vượt qua H.L.P thì chậm lại và ko
> qua được Bayes Optimal Error

<br>

<a id="node-s2k7yh7"></a>

<p align="center"><kbd><img src="assets/pablbzyu7jj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là, nguyên nhân dẫn đến việc 'chậm' lại sau khi
> surpass H.L.P là vì trước đó ML có thể nhờ con người làm
> những việc con người giỏi như label data giùm, từ đó ML
> có thể học dc nhiều, Nhưng sau khi vượt rồi thì không còn
> biết nhờ ai nữa sự tiến bộ sẽ chậm lại

<br>

<a id="node-rdf2yjk"></a>

### Avoidable Bias

<br>

<a id="node-zxedazq"></a>

> [!NOTE]
> Trong bài giảng này, chúng ta tìm hiểu về khái niệm human-level
> performance, là một chỉ số để đo độ chính xác của một mô hình học máy so
> với con người. Với ví dụ phân loại hình ảnh mèo, nếu con người có độ chính
> xác gần như hoàn hảo thì human-level error là 1%. Nếu mô hình của chúng
> ta đạt được 8% lỗi trên tập huấn luyện và 10% lỗi trên tập phát triển, đó là
> một dấu hiệu cho thấy mô hình của chúng ta không hoạt động tốt trên tập
> huấn luyện. Trong trường hợp này, chúng ta cần tập trung vào giảm bias
> bằng cách tăng kích thước của mạng neural hoặc tăng thời gian huấn luyện.
>
> Tuy nhiên, nếu human-level error không phải là 1% mà thấp hơn do ảnh
> trong tập dữ liệu quá mờ hoặc không rõ ràng, chúng ta có thể tập trung vào
> giảm variance bằng cách sử dụng regularization hoặc tăng số lượng dữ liệu
> huấn luyện.
>
> Bên cạnh đó, ta còn có khái niệm \\*avoidable bias, là sự chênh lệch giữa lỗi
> tập huấn luyện và lỗi Bayes\\*, tức là lỗi tối thiểu mà chúng ta có thể đạt được.
> Nếu mô hình đang có avoidable bias, ta nên tập trung vào giảm bias bằng
> cách tăng kích thước mạng neural hoặc thời gian huấn luyện. Ngược lại,
> nếu mô hình đang có phần variance lớn hơn, ta nên tập trung vào giảm
> variance bằng cách sử dụng regularization hoặc tăng số lượng dữ liệu
> huấn luyện. (ChatGPT)
>
> Đại khái là **HLP gần bằng với Bayes Optimal Error**
> Khoảng cách giữa HLP và Training error là **Avoidable Bias** - Có 
> thể giảm được (bằng More complex model....)
>
>
>
> Khoảng cách giữa Dev error và Training error là **Variance** - Có
> thể giảm bằng những phương cách giảm vấn đề High variance
> như (Regularization, more data,,,)
>
>
>
> **Tuỳ trường hợp cái nào lớn giữa Avoidable Bias và. Variance 
> mà ta sẽ focus vô improve cái bias hay variance.**

<br>

<a id="node-iiglmpj"></a>

<p align="center"><kbd><img src="assets/ujmhglns49.png" width="80%"></kbd></p>

> [!NOTE]
> Tức là, tuỳ vào tính chất công việc (để đánh giá liệu H.L.P có tốt hay 
> không, có tiệm cận với Bayes error ko), tuỳ vào Khoảng cách giữa 
> training error với H.L.P và Dev error - training error.
>
>
>
> Ví dụ bên trái nếu Avoidable bias lớn hơn nhiều Variance,
> nên tập trung vào **giảm avoidable bias**
>
>
>
> Ví dụ ở bên phải:
> Nếu ta nghĩ rằng đ/v công việc này H.L.P đã rất tốt và do đó
> đã tiệm cận với Bayes error rồi thì ta nên cho rằng H.L.P ~=
> Bayes thì dù ta có improve để Training error từ 8 -> 7.5% 
> (giảm bias) cũng ko bằng tập trung vào improve 
> dev set từ 10 -> 8% (Giảm variance)
>
>
>
> Còn giả dụ với 7.5% error của H.L.P nhưng ta có cơ sở để tin rằng
> H.L.P chưa tiệm cận được Bayes error (giả định là 3% chẳng hạn) 
> thì ta nên tiếp tục improve Training error.

<br>

<a id="node-y7dn9sw"></a>

<p align="center"><kbd><img src="assets/lbnqx6158os.png" width="80%"></kbd></p>

> [!NOTE]
> Vẫn có những vấn đề H.L.P bằng thậm chí vượt Bayes
> và ngược lại thua xa Bayes, nơi mà máy tính có thể vuợt qua
> Do con nguoì bị hạn chế ở một số khả năng mà máy tính có
> thế mạnh hơn con người.

<br>

<a id="node-71oywi2"></a>

### Understanding Human-level Performance

<br>

<a id="node-yt4d5od"></a>

> [!NOTE]
> • The phrase "human-level performance" can be used casually in research
> articles, but it can be defined more precisely as an estimate of Bayes error.
>
> • The definition of human-level error can vary depending on the context, such as
> surpassing the performance of a typical doctor.
>
> • Defining human-level performance is important for analyzing bias and variance
> in machine learning projects.
>
> • A measure of avoidable bias can be calculated as the difference between the
> estimate of Bayes error and the training error.
>
> • The focus of improvement should be on reducing the larger issue between bias
> and variance in the learning algorithm.

<br>

<a id="node-3qwhuho"></a>

<p align="center"><kbd><img src="assets/7pnerzodap7.png" width="80%"></kbd></p>

> [!NOTE]
> ...

<br>

<a id="node-hst4kbc"></a>

<p align="center"><kbd><img src="assets/2mmkbebn9v5.png" width="80%"></kbd></p>

<br>

<a id="node-3vbb3q3"></a>

<p align="center"><kbd><img src="assets/t74o45qpr.png" width="80%"></kbd></p>

<br>

<a id="node-8dl3q86"></a>

### Surpassing Human-level Performance

<br>

<a id="node-fgm3l0n"></a>

> [!NOTE]
> 1 Many teams aim to surpass human-level performance on specific tasks, which can be exciting.
> However, as performance approaches or exceeds human-level, machine learning progress becomes
> more challenging.
>
> 2 The example of a problem with a team of humans achieving a 0.5% error rate, a single human 1%
> error rate, and an algorithm with 0.6% training error and 0.8% dev error illustrates the concept of
> avoidable bias. In this case, the Bayes error is estimated to be 0.5%, making the avoidable bias at
> least 0.1% with a variance of 0.2%.
>
> 3 In a more difficult example, where a team of humans and a single human have the same error
> rates as before, but the algorithm has 0.3% training error and 0.4% dev error, it's unclear whether to
> focus on reducing bias or variance, because the Bayes error is unknown.
>
> 4 Once a machine learning system surpasses human-level performance, it becomes harder to use
> human intuition to improve performance further. While progress is still possible, the tools for pointing
> in a clear direction may not be as effective.
>
> 5 Examples of problems where machine learning significantly surpasses human-level performance
> include online advertising, product recommendations, logistics, and predicting loan repayment.
> These are structured data problems where humans tend to be less skilled. However, surpassing
> human-level performance on natural perception tasks like computer vision, speech recognition, and
> natural language processing is more challenging.
>
> 6 Some medical tasks, such as reading ECGs, diagnosing skin cancer, and certain radiology tasks,
> have seen machines surpass human-level performance, but it's harder for machines to perform well
> on natural perception tasks due to the superior ability of humans in these areas.
>
> 7 Deep learning systems have surpassed human-level performance on some supervisory problems,
> but this is challenging as performance approaches human-level and requires vast amounts of data.

<br>

<a id="node-qm6bor6"></a>

<p align="center"><kbd><img src="assets/tw6f9y6ppca.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là một số trường hợp khó mà xác định được có thể improve được
> nữa hay không  (Xác định Avoidable bias là bao nhiêu). Ví dụ khi hiệu suất
> của model đã vượt nhóm con người

<br>

<a id="node-zbow5d1"></a>

<p align="center"><kbd><img src="assets/w6gj7bg1vkn.png" width="80%"></kbd></p>

<br>

<a id="node-perc7rb"></a>

### Improving Your Model Performance

<br>

<a id="node-6zm2h0b"></a>

> [!NOTE]
> Guidelines to improve the performance of your learning algorithm:
>
> 1 Address avoidable bias issues:  • Train a bigger model.  • Train longer.  • Use a
> better optimization algorithm such as ADS momentum, RMSprop, or Adam.  • Find a
> better neural network architecture or set of hyperparameters.
>
> 2 Address variance problems:  • Get more data to train on.  • Try regularization
> techniques such as L2 regularization, dropout, or data augmentation.  • Try various
> neural network architecture/hyperparameters search.
>
> 3 Use the difference between training error and proxy for Bayes error to estimate
> avoidable bias, and the difference between dev error and training error to estimate
> variance problems.
>
> 4 To reduce avoidable bias, increase the model size, train longer, or use a better
> optimization algorithm.
>
> 5 To address variance problems, get more data, try regularization techniques, or
> explore other neural network architecture/hyperparameters.
>
> Applying these guidelines systematically can make your machine learning team
> more efficient, systematic, and strategic in improving the performance of your
> learning algorithm.

<br>

<a id="node-xkzuqa2"></a>

<p align="center"><kbd><img src="assets/k6qhhqrn56o.png" width="80%"></kbd></p>

<br>

<a id="node-chkpe4v"></a>

<p align="center"><kbd><img src="assets/ijnpv5iknxc.png" width="80%"></kbd></p>

<br>

<a id="node-y0rdx2z"></a>

<p align="center"><kbd><img src="assets/oalgsaqhnh.png" width="80%"></kbd></p>

> [!NOTE]
> I think that this notion of bias or avoidable bias and variance
> is one of those things that's **easily learnt but tough to
> master. And if you're able to systematically apply the
> concepts from this week's video, you actually will be much
> more efficient and much more systematic and much more
> strategic than a lot of machine learning teams in terms of
> how to systematically go about improving the performance
> of your machine learning system**

<br>

<a id="node-s0f8hec"></a>

## Ml Flight Simulator

<br>

<a id="node-2omp9cr"></a>

<p align="center"><kbd><img src="assets/8in1oevb6z.png" width="80%"></kbd></p>

<br>

<a id="node-hhnz2sz"></a>

<p align="center"><kbd><img src="assets/7uyxbya9jn6.png" width="80%"></kbd></p>

<br>

<a id="node-cfznn79"></a>

<p align="center"><kbd><img src="assets/rdpkw4kuyt7.png" width="80%"></kbd></p>

<br>

<a id="node-8vcsjot"></a>

<p align="center"><kbd><img src="assets/7bsunideta.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là stakeholder chỉ define threshold cho
> Satisficing metric thôi, không đụng đến Optimizing. Câu
> này phải hiểu nó hỏi là: Có phải khác biệt chủ yếu giữa
> optimizing metric và. Satisficing metric là mức độ Priority
> mà thằng Stakeholder chỉ định hay không.
>
>
>
> Thì câu trả lời phải là không, vì thằng stkaeholder nó chỉ
> chỉ định cái threshold cho Satisficing metric thôi, không
> phải là bảo rằng cái này quan trọng hơn cái kia để mà
> phải tập trung vào cái này hơn  cái kia (đại loại vậy)
>
>
>
> Câu này sai là do mình hiểu sai ý câu hỏi

<br>

<a id="node-veqdpid"></a>

<p align="center"><kbd><img src="assets/9rz375r9fb.png" width="80%"></kbd></p>

> [!NOTE]
> ...

<br>

<a id="node-6z892c9"></a>

<p align="center"><kbd><img src="assets/oioegumt6c.png" width="80%"></kbd></p>

> [!NOTE]
> ...

<br>

<a id="node-hr9s30d"></a>

<p align="center"><kbd><img src="assets/eopaa9mc1gj.png" width="80%"></kbd></p>

> [!NOTE]
> ...

<br>

<a id="node-3s8bjcu"></a>

<p align="center"><kbd><img src="assets/h1aoh81hawp.png" width="80%"></kbd></p>

> [!NOTE]
> ...

<br>

<a id="node-own3tzy"></a>

<p align="center"><kbd><img src="assets/zgv9f1v9khd.png" width="80%"></kbd></p>

<br>

<a id="node-k9irhpw"></a>

<p align="center"><kbd><img src="assets/ece1pzon4f.png" width="80%"></kbd></p>

<br>

<a id="node-tb98aby"></a>

<p align="center"><kbd><img src="assets/4o6bellh79h.png" width="80%"></kbd></p>

<br>

<a id="node-uhahbrq"></a>

<p align="center"><kbd><img src="assets/6f9k5c554tp.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/aiotkyzcoy.png" width="80%"></kbd></p>

> [!NOTE]
> Hiểu đại khái là tăng Dev set để nó phản ánh
> đúng hơn với thực tế thì nó sẽ cho kết quả gần
> với test set hơn -> giảm Variance với Test set

<br>

<a id="node-u6rfpag"></a>

<p align="center"><kbd><img src="assets/aerl23ryil6.png" width="80%"></kbd></p>

<br>

<a id="node-tng0fcw"></a>

<p align="center"><kbd><img src="assets/o361jaf7g2b.png" width="80%"></kbd></p>

> [!NOTE]
> Khả năng là phải chọn Expand...vì cả hai solution 'reset' new
> metric đều sẽ làm giảm Accuracy vì nó sẽ vi phạm nguyên tắc
> Orthogonalization

<br>

<a id="node-qigo2vk"></a>

<p align="center"><kbd><img src="assets/x5cg1lbkgp.png" width="80%"></kbd></p>

> [!NOTE]
> ???

<br>

<a id="node-pftoxlh"></a>

<p align="center"><kbd><img src="assets/7ajpllydjo9.png" width="80%"></kbd></p>

> [!NOTE]
> ???

<br>

<a id="node-rxbtabh"></a>

<p align="center"><kbd><img src="assets/4m8f2e3mocq.png" width="80%"></kbd></p>

> [!NOTE]
> Cái Needing two week .... rõ ràng đúng, sao ko chọn ta

<br>

<a id="node-c72s4cv"></a>

<p align="center"><kbd><img src="assets/e3eyjjgbg3l.png" width="80%"></kbd></p>

<br>

<a id="node-g9nkec4"></a>

<p align="center"><kbd><img src="assets/qrr9hzdcfn.png" width="80%"></kbd></p>

<br>

<a id="node-nrewc2e"></a>

## Interview

<br>

