# C1w3 - Vector Space Models

📊 **Progress:** `146` Notes | `122` Screenshots

---
<a id="node-rnlqp4z"></a>

## C1w3 - Vector Space Models

> [!NOTE]
> Vector space models capture semantic meaning and relationships between words. 
> You'll learn how to create word vectors that capture dependencies between words, 
> then visualize their relationships in two dimensions using PCA.
>
>
>
> Learning Objectives
>
>
>
>  • Covariance matrices
>  • Dimensionality reduction
>  • Principal component analysis
>  • Cosine similarity
>  • Euclidean distance
>  • Co-occurrence matrices
>  • Vector representations

<br>

<a id="node-aoauicq"></a>

## Introduction

<br>

<a id="node-ki6w52d"></a>

> [!NOTE]
> 1 Understanding v\\*ector spaces\\* in NLP
>
> 2 Representing \\*word\\* \\*vectors\\* as numerical codes
>
> 3 Two methods for \\*comparing different word vectors\\*:
> \\*Euclidean distance\\* and\\* cosine similarity\\*
>
> 4 \\*Plotting\\* high-dimensional word vectors in a \\*2D
> plane\\*
>
> 5 \\*Clustering\\* \\*similar words\\* together in the plot

<br>

<a id="node-kixnako"></a>

## Vector Space Models

<br>

<a id="node-h2pbrw3"></a>

> [!NOTE]
> 1 Introduction to \\*vector space\\* models and their applications in
> \\*NLP\\*.
>
> 2 \\*Vector space models\\* can \\*encode\\* different \\*types of information\\*
> and \\*capture word relationships\\*.
>
> 3 Examples of how \\*vector space\\* models can be used in question
> \\*answering\\*, \\*paraphrasing\\*, \\*summarization\\*, \\*information extraction\\*,
> \\*machine translatio\\*n, and \\*chat\\* programming.
>
> 4 \\*Representing words\\* and documents \\*as vectors\\* using \\*context\\*
> and \\*cooccurrence matrices\\*.
>
> 5 John Firth's quote\\* "You shall know a word by the company it
> keeps\\*" as a fundamental concept in NLP.
>
> 6 Next video will cover \\*building vector space models\\* from scratch
> using \\*cooccurrence matrices\\*.

<br>

<a id="node-1p965nx"></a>

<p align="center"><kbd><img src="assets/e98ewgpamza.png" width="80%"></kbd></p>

<br>

<a id="node-bb8f6y1"></a>

<p align="center"><kbd><img src="assets/2yhh1u4v51c.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **vector space** sẽ giúp giải quyết được vấn đề như
> này một cái là **2 câu gần như giống nhau** nhưng **nghĩa
> hoàn toàn khác xa** còn **2 câu nhìn thì khác xa** nhưng
> n**ghĩa lại giống nhau**

<br>

<a id="node-63dvohp"></a>

<p align="center"><kbd><img src="assets/hu69ofpt2kb.png" width="80%"></kbd></p>

> [!NOTE]
> Nó cũng sẽ giúp **nắm bắt được sự liên quan
> giữa các từ** trong câu và ứng dụng trong rất
> nhiều lĩnh vực

<br>

<a id="node-nd26rbz"></a>

<p align="center"><kbd><img src="assets/t0jul63o2cm.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là represent một word sao cho **nắm bắt được tất cả
> những thông tin context xung quanh nó** từ đó hiểu được trọn vẹn ý
> nghĩa của từ

<br>

<a id="node-h0wupbf"></a>

<p align="center"><kbd><img src="assets/r37p4v4iwke.png" width="80%"></kbd></p>

<br>

<a id="node-3yt60c4"></a>

<p align="center"><kbd><img src="assets/v0t85zhr06.png" width="80%"></kbd></p>

<br>

<a id="node-pmx0ue6"></a>

## Word By Word And Word By Doc

<br>

<a id="node-d95uhp0"></a>

> [!NOTE]
> 1 Introduction to \\*constructing vectors\\* based on \\*co-occurrence matrix\\*
>
> 2 \\*Different designs\\* for constructing vector space models for words and
> documents
>
> 3 \\*Co-occurrence\\* matrix and \\*vector representations\\* for words in the \\*corpus\\*
>
> 4 \\*Co-occurrence of words in documents\\* and \\*vector representations for
> documents in the corpus\\*
>
> 5 Creating a \\*vector space\\* by taking representations for multiple sets of
> documents or words
>
> 6 \\*Comparing\\* vector representations using \\*cosine similarity \\*and \\*Euclidean
> distance\\*
>
> 7 Importance of \\*similarity metrics\\* in vector spaces
>
> 8 Summary of the main ideas and a teaser for the next video on \\*Euclidean
> distance\\* similarity metric.

<br>

<a id="node-pg4ewy7"></a>

<p align="center"><kbd><img src="assets/ddbrbcgkqdn.png" width="80%"></kbd></p>

<br>

<a id="node-djha2mx"></a>

<p align="center"><kbd><img src="assets/p6u5zyx1h9.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là dựa vào nhận định ở bài trước, rằng ý nghĩa một từ có thể được
> xác định bằng các từ hay vây quanh nó, ta có thể có cách thức đầu tiên để
> xây dựng word vector như sau. Xét một corpus, ta sẽ thống kê xem trong
> một phạm vi nhất định, thì có bao nhiêu lần một từ xuất hiện trong phạm vi
> đó với một từ khác, để rồi tạo ra co-occurrence matrix. Và dựa vào các chỉ
> số thống kê này, để tạo word vector. Ví dụ trong corpus gồm 2 câu như trong
> hình, xây dựng vector cho từ "data" dựa trên số lần các từ khác xuất hiện
> trong phạm vi gần nó
>
>
>
> Cho k bằng 2 thì đv từ '**data**' thì trong khoảng **K** này các từ khác **xuất
> hiện nhiều hay ít** (mấy lần) từ đó xây dựng **vector represent** cho từ 'data'
> ..
>
>
>
> Với cách tạo vector này có thể thấy n**hững từ mà có liên quan đến nhau sẽ
> có xu hướng xuất hiện gần nhau** nhiều nên sẽ cao hơn

<br>

<a id="node-yc0dnvo"></a>

<p align="center"><kbd><img src="assets/2wtctrsiwq8.png" width="80%"></kbd></p>

> [!NOTE]
> Còn cái này thì đại khái cũng tạo vector bằng số lần từ này **xuất
> hiện trong 1 corpus thuộc lĩnh vực** nào đó. Như từ **data** với véctơ
> như vậy sẽ dễ thấy nó **liên quan nhiều đến máy tính** còn **film** thì
> **liên quan nhiều đến giải trí**

<br>

<a id="node-4go5x0w"></a>

<p align="center"><kbd><img src="assets/btw0k7sps9r.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là vẽ ra như này sẽ thấy **'data' có tính economy và ML
> còn film có tính entertainment nhiều hơn.**
>
>
>
> Đồng thời cũng cho thấy lĩnh vực **ML và Economy thì gần nhau
> hơn là ML với Entertainment**
>
>
>
> Và để cụ thể hoá tính chất gần nhau đó thì người ta dùng thước 
> đo **Angle** và **Distance** của các vector

<br>

<a id="node-eu5aroi"></a>

<p align="center"><kbd><img src="assets/5xc8isbknt4.png" width="80%"></kbd></p>

<br>

<a id="node-j6d6v76"></a>

<p align="center"><kbd><img src="assets/aoy02axc86q.png" width="80%"></kbd></p>

<br>

<a id="node-a2oxkhm"></a>

<p align="center"><kbd><img src="assets/8d4i6tg673a.png" width="80%"></kbd></p>

<br>

<a id="node-o965wvs"></a>

<p align="center"><kbd><img src="assets/xryk5y3oyp.png" width="80%"></kbd></p>

<br>

<a id="node-hduarl8"></a>

## Linear Algebra In Python With Numpy

<br>

<a id="node-nn2zqne"></a>

> [!NOTE]
> In this lab, you will have the opportunity to remember some
> \\*basic concepts \\*about \\*linear algebra\\* and how to use them in
> \\*Python\\*.
>
> \\*Numpy\\* is one of the \\*most used libraries\\* in Python for \\*arrays
> manipulation\\*. It adds to Python a set of functions that allows
> us to \\*operate on large multidimensional arrays\\* with just a few
> lines. So forget about writing nested loops for adding
> matrices! With NumPy, this is as simple as adding numbers.
>
> Let us \\*import\\* the numpy library and assign the alias \\*np\\* for it.
> We will follow this convention in almost every notebook in this
> course, and you'll see this in many resources outside this
> course as well.

<br>

<a id="node-gg4lsme"></a>

> [!NOTE]
> import numpy as \\*np\\*  # The swiss
> knife of the data scientist.

<br>

<a id="node-hhrwbl3"></a>

> [!NOTE]
> Defining lists and
> numpy arrays

<br>

<a id="node-p32yiaw"></a>

<p align="center"><kbd><img src="assets/7jghk39d84.png" width="80%"></kbd></p>

> [!NOTE]
> alist = [1, 2, 3, 4, 5]   # Define a python list. It looks like an np array
> narray = \\*np.array\\*([1, 2, 3, 4]) # Define a numpy array

<br>

<a id="node-wazh2d1"></a>

> [!NOTE]
> Algebraic operators on NumPy
> arrays vs. Python lists

<br>

<a id="node-xgpw8cj"></a>

> [!NOTE]
> One of the \\*common\\* beginner \\*mistakes\\* is to \\*mix up\\* the
> concepts of \\*NumPy\\* arrays and \\*Python lists\\*. Just observe
> the next example, where we \\*add\\* two objects of the two
> mentioned types.
>
> Note that the \\*'+'\\* operator on NumPy arrays perform an
> \\*element-wise addition\\*, while the same operation on \\*Python\\*
> \\*lists\\* results in a \\*list concatenatio\\*n. Be careful while coding.
> Knowing this can \\*save many headaches.\\*

<br>

<a id="node-il9wkya"></a>

> [!NOTE]
> print(narray \\*+\\* narray)
> print(alist \\*+\\* alist)
>
> [2 4 6 8]
> [1, 2, 3, 4, 5, 1, 2, 3, 4, 5]
>
> Đối với Numpy array là cộng
> vector element wise còn dv
> Python list thì là concat

<br>

<a id="node-9d8nu7l"></a>

> [!NOTE]
> It is the same as with the \\*product\\* operator, \\**\\*. In the first
> case, we \\*scale\\* the vector, while in the second case, we
> \\*concatenate three times\\* the same list.
>
> Be aware of the difference because, \\*within the same function\\*,
> \\*both\\* types of arrays can \\*appear\\*. \\*Numpy\\* arrays are designed for
> \\*numerical\\* and \\*matrix\\* operations, while lists are for more general
> purposes.

<br>

<a id="node-wikpnhn"></a>

> [!NOTE]
> print(narray * 3)
> print(alist * 3)
>
> [ 3  6  9 12]
> [1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5]
>
> Đối với Numpy array là nhân
> vector element wise còn dv
> Python list thì là concat 3 lần vãi thật

<br>

<a id="node-jbh8zkk"></a>

#### Matrix or Array of Arrays

<br>

<a id="node-ob5ucq0"></a>

> [!NOTE]
> In \\*linear algebra\\*, a \\*matrix\\* is a structure composed of \\*n rows\\*
> \\*by m columns\\*. That means each row must have the same number
> of columns. With NumPy, we have two ways to create a matrix:
>
> - Creating an array of arrays using \\*np.array\\* (recommended).
>
> - Creating a matrix using \\*np.matrix\\* (still available but might be
> removed soon). NumPy arrays or lists can be used to \\*initialize\\* a
> matrix, but the resulting matrix will be composed of NumPy arrays
> only.

<br>

<a id="node-tm1v203"></a>

> [!NOTE]
> npmatrix1 = \\*np.array\\*([narray, narray, narray]) # Matrix \\*initialized with NumPy arrays
> \\*npmatrix2 = \\*np.array\\*([alist, alist, alist]) # Matrix \\*initialized with lists\\*
> npmatrix3 = \\*np.array\\*([narray, [1, 1, 1, 1], narray]) # Matrix \\*initialized with both types
> \\*
> print(npmatrix1)
> print(npmatrix2)
> print(npmatrix3)

<br>

<a id="node-oa3zyuu"></a>

<p align="center"><kbd><img src="assets/5ijd0ka1y0r.png" width="80%"></kbd></p>

<br>

<a id="node-onod2is"></a>

> [!NOTE]
> However, when \\*defining a matrix\\*, be
> sure that \\*all the rows contain the same
> number of elements\\*. Otherwise, the
> linear algebra operations could lead to
> unexpected results.
>
> Analyze the following two examples:

<br>

<a id="node-87xci4z"></a>

> [!NOTE]
> # Example 1:
>
> okmatrix = \\*np.array\\*([[1, 2], [3, 4]]) # Define a 2x2 matrix
> print(okmatrix) # Print okmatrix
> print(okmatrix * 2) # Print a scaled version of okmatrix

<br>

<a id="node-wkyt0mf"></a>

<p align="center"><kbd><img src="assets/vc299lc6utk.png" width="80%"></kbd></p>

<br>

<a id="node-406xh2j"></a>

> [!NOTE]
> # Example 2:
>
> badmatrix = np.array([[1, 2], [3, 4], \\*[5, 6, 7]\\*]) # Define a matrix. Note the third row contains 3 elements
> print(badmatrix) # Print the malformed matrix
> print(badmatrix * 2) # It is supposed to scale the whole matrix
>
> ->
> [\\*list\\*([1, 2]) list([3, 4]) list([5, 6, 7])]
> [list([1, 2, 1, 2]) list([3, 4, 3, 4]) list([5, 6, 7, 5, 6, 7])]

<br>

<a id="node-g8qjjkq"></a>

#### Scaling and translating matrices

<br>

<a id="node-soubxt6"></a>

> [!NOTE]
> Now that you know how to build \\*correct NumPy
> arrays and matrices\\*, let us see how \\*easy\\* it is to
> \\*operate\\* with them in Python using the regular
> \\*algebraic operators\\* like + and -.
>
> Operations can be performed \\*between arrays\\*
> and arrays or between \\*arrays\\* and \\*scalars\\*.

<br>

<a id="node-g5iyhnx"></a>

> [!NOTE]
> # Scale by 2 and translate 1 unit the matrix
> result = okmatrix\\* * 2\\* + 1 # For each element in the matrix, multiply by 2 and add 1
> print(result)

<br>

<a id="node-o60bxcb"></a>

<p align="center"><kbd><img src="assets/dknsyup5yim.png" width="80%"></kbd></p>

<br>

<a id="node-4jlqv5d"></a>

> [!NOTE]
> # Add two compatible matrices
> result1 = okmatrix \\*+\\* okmatrix
> print(result1)
>
> # Subtract two compatible matrices. This is called the difference vector
> result2 = okmatrix\\* -\\* okmatrix
> print(result2)

<br>

<a id="node-nmrifkx"></a>

<p align="center"><kbd><img src="assets/fpin5frf3sr.png" width="80%"></kbd></p>

<br>

<a id="node-45u4gfe"></a>

> [!NOTE]
> result = okmatrix \\**\\* okmatrix # Multiply each element by itself
> print(result)

<br>

<a id="node-8063f6g"></a>

<p align="center"><kbd><img src="assets/hbl90suc7w8.png" width="80%"></kbd></p>

<br>

<a id="node-ewkbnr0"></a>

#### Transpose a matrix

<br>

<a id="node-5v0in1v"></a>

> [!NOTE]
> In linear algebra, the \\*transpose\\* of a matrix is an
> operator that \\*flips a matrix over its diagonal\\*, i.e., the
> transpose operator switches the row and column
> indices of the matrix producing another matrix. If the
> original matrix dimension is \\*n by m\\*, the resulting
> transposed matrix will be \\*m by n.\\*
>
> \\*T\\* denotes the t\\*ranspose operation\\*s with NumPy
> matrices.

<br>

<a id="node-h5rpvz2"></a>

> [!NOTE]
> matrix3x2 = np.array([[1, 2], [3, 4], [5, 6]]) # Define a 3x2 matrix
> print('Original matrix 3 x 2')
> print(matrix3x2)
> print('Transposed matrix 2 x 3')
> print(matrix3x2.T)

<br>

<a id="node-ckr5az8"></a>

<p align="center"><kbd><img src="assets/9khp2ptq8kw.png" width="80%"></kbd></p>

<br>

<a id="node-7yvkih5"></a>

> [!NOTE]
> nparray = np.array([1, 2, 3, 4]) # Define an array
> print('Original array')
> print(nparray)
> print('Transposed array')
> print(nparray.T)
>
> However, note that the transpose
> operation does not affect 1D arrays.

<br>

<a id="node-d254bsh"></a>

<p align="center"><kbd><img src="assets/vngnup7xct.png" width="80%"></kbd></p>

<br>

<a id="node-jdkr140"></a>

> [!NOTE]
> nparray = np.array([[1, 2, 3, 4]]) # Define a 1 x 4 matrix. Note the 2 level of square brackets
> print('Original array')
> print(nparray)
> print('Transposed array')
> print(nparray.T)

<br>

<a id="node-orj9ujc"></a>

<p align="center"><kbd><img src="assets/qyu93mx3dwe.png" width="80%"></kbd></p>

<br>

<a id="node-geufon4"></a>

> [!NOTE]
> Get the norm of a
> nparray or matrix

<br>

<a id="node-387cnuy"></a>

<p align="center"><kbd><img src="assets/10ft7030aow.png" width="80%"></kbd></p>

<br>

<a id="node-hl3932r"></a>

> [!NOTE]
> nparray1 = np.array([1, 2, 3, 4]) # Define an array
> norm1 = \\*np.linalg.norm\\*(nparray1)
>
> nparray2 = np.array([[1, 2], [3, 4]]) # Define a 2 x 2 matrix. Note the 2 level of square brackets
> norm2 = \\*np.linalg.norm\\*(nparray2) 
>
> print(norm1)
> print(norm2)
>
> -> 5.477225575051661
> 5.477225575051661

<br>

<a id="node-dwoz1k2"></a>

> [!NOTE]
> Note that without any other parameter, the
> norm function \\*treats the matrix as being just
> an array of numbers\\*. However, it is possible to
> get the norm \\*by rows\\* or by \\*columns\\*.
> The \\*axis\\* parameter controls the form of the
> operation:
>
> \\* • axis=0\\* means get the norm of each
> column \\*  • axis=1\\* means get the norm of
> each row.

<br>

<a id="node-iw7i6qp"></a>

> [!NOTE]
> nparray2 = np.array([[1, 1], [2, 2], [3, 3]]) # Define a 3 x 2 matrix. 
>
> normByCols = np.linalg.norm(nparray2, \\*axis=0\\*) # Get the norm for each \\*column\\*. Returns 2 elements
> normByRows = np.linalg.norm(nparray2, \\*axis=1\\*) # get the norm for each \\*row\\*. Returns 3 elements
>
> print(normByCols)
> print(normByRows)
>
> ->
> [3.74165739 3.74165739]
> [1.41421356 2.82842712 4.24264069]

<br>

<a id="node-xmybbqc"></a>

> [!NOTE]
> The dot product between
> arrays: All the flavors

<br>

<a id="node-v3afhhz"></a>

<p align="center"><kbd><img src="assets/jqw4qokr2p.png" width="80%"></kbd></p>

<br>

<a id="node-y6uakej"></a>

> [!NOTE]
> nparray1 = np.array([0, 1, 2, 3]) # Define an array
> nparray2 = np.array([4, 5, 6, 7]) # Define an array
>
> flavor1 = \\*np.dot\\*(nparray1, nparray2) # Recommended way
> print(flavor1)
>
> flavor2 = \\*np.sum\\*(nparray1 * nparray2) # Ok way
> print(flavor2)
>
> flavor3 = nparray1 \\*@\\* nparray2         # Geeks way
> print(flavor3)
>
> # As you never should do:             # Noobs way
> flavor4 = 0
> \\*for\\* a, b in\\* zip(nparray1, nparray2):\\*
>     flavor4 += a * b
>
> print(flavor4)

<br>

<a id="node-694e1e3"></a>

<p align="center"><kbd><img src="assets/6fwnhimcgeu.png" width="80%"></kbd></p>

<br>

<a id="node-am3ricf"></a>

> [!NOTE]
> \\*We strongly recommend using np.dot, since
> it is the \\_only method that accepts arrays and
> lists without problems\\*\\_

<br>

<a id="node-p38s3g0"></a>

> [!NOTE]
> norm1 = \\*np.dot\\*(np.array([1, 2]), np.array([3, 4])) # Dot product on nparrays
> norm2 = \\*np.dot\\*([1, 2], [3, 4]) # Dot product on python lists
>
> print(norm1, '=', norm2 )

<br>

<a id="node-af8241d"></a>

<p align="center"><kbd><img src="assets/x5h5h1hpze.png" width="80%"></kbd></p>

<br>

<a id="node-m69g47q"></a>

<p align="center"><kbd><img src="assets/gq2gyb4zouf.png" width="80%"></kbd></p>

<br>

<a id="node-50nw573"></a>

#### Sums by rows or columns

<br>

<a id="node-ehka6cw"></a>

> [!NOTE]
> Another general operation performed on
> matrices is the \\*sum by rows or columns\\*. Just
> as we did for the function norm,
> the \\*axis\\* parameter controls the form of the
> operation:
>
> \\* • axis=0\\* means to sum the elements of
> each column together. \\*  • axis=1\\* means to
> sum the elements of each row together.

<br>

<a id="node-g3nr2jd"></a>

> [!NOTE]
> nparray2 = np.array([[1, -1], [2, -2], [3, -3]]) # Define a 3 x 2 matrix. 
>
> sumByCols = \\*np.sum\\*(nparray2, axis=0) # Get the sum for each column. Returns 2 elements
> sumByRows = \\*np.sum\\*(nparray2, axis=1) # get the sum for each row. Returns 3 elements
>
> print('Sum by columns: ')
> print(sumByCols)
> print('Sum by rows:')
> print(sumByRows)

<br>

<a id="node-99wu8on"></a>

<p align="center"><kbd><img src="assets/52a414juztq.png" width="80%"></kbd></p>

<br>

<a id="node-ijjtjml"></a>

#### Get the mean by rows or columns

<br>

<a id="node-i3pe995"></a>

<p align="center"><kbd><img src="assets/kaahzej05bc.png" width="80%"></kbd></p>

<br>

<a id="node-5j5wcdn"></a>

> [!NOTE]
> nparray2 = np.array([[1, -1], [2, -2], [3, -3]]) # Define a 3 x 2 matrix. Chosen to be a matrix with 0 mean
>
> mean = \\*np.mean\\*(nparray2) # Get the mean for the whole matrix
> meanByCols = \\*np.mean\\*(nparray2, axis=\\*0\\*) # Get the mean for each column. Returns 2 elements
> meanByRows = \\*np.mean\\*(nparray2, axis=\\*1\\*) # get the mean for each row. Returns 3 elements
>
> print('Matrix mean: ')
> print(mean)
> print('Mean by columns: ')
> print(meanByCols)
> print('Mean by rows:')
> print(meanByRows)

<br>

<a id="node-bmv9my6"></a>

<p align="center"><kbd><img src="assets/auuqljj49ji.png" width="80%"></kbd></p>

<br>

<a id="node-9q59vzt"></a>

#### Center the columns of a matrix

<br>

<a id="node-qqv0k3c"></a>

> [!NOTE]
> \\*Centering the attributes\\* of a data matrix is another \\*essential
> preprocessing step\\*. Centering a matrix means to \\*remove
> the column mean to each element inside the column\\*. The
> mean by columns of a centered matrix is always 0.
>
> With NumPy, this process is as simple as this:

<br>

<a id="node-m9vwhan"></a>

> [!NOTE]
> nparray2 = np.array([[1, 1], [2, 2], [3, 3]]) # Define a 3 x 2 matrix. 
>
> nparrayCentered = nparray2 - \\*np.mean\\*(nparray2, axis=\\*0\\*) # \\*Remove the mean for each column
> \\*
> print('Original matrix')
> print(nparray2)
> print('Centered by columns matrix')
> print(nparrayCentered)
>
> print('New mean by column')
> print(nparrayCentered.mean(axis=0))

<br>

<a id="node-a7je8c0"></a>

<p align="center"><kbd><img src="assets/zly2sc4hpi8.png" width="80%"></kbd></p>

<br>

<a id="node-v8nop3z"></a>

> [!NOTE]
> \\*Warning\\*: This process \\*does not apply for row
> centering\\*. In such cases, consider \\*transposing\\* the
> matrix, \\*centering by columns\\*, and then \\*transpose
> back the result\\*.
>
> See the example below:

<br>

<a id="node-d9or02m"></a>

> [!NOTE]
> nparray2 = np.array([[1, 3], [2, 4], [3, 5]]) # Define a 3 x 2 matrix. 
>
> nparrayCentered = nparray2\\*.T\\* - \\*np.mean\\*(nparray2, axis=\\*1\\*) # \\*Remove the mean for each row
> \\*nparrayCentered = nparrayCentered\\*.T\\* # \\*Transpose back \\*the result
>
> print('Original matrix')
> print(nparray2)
> print('Centered by rows matrix')
> print(nparrayCentered)
>
> print('New mean by rows')
> print(nparrayCentered.mean(axis=1))

<br>

<a id="node-qiea90h"></a>

<p align="center"><kbd><img src="assets/k4ttp7oq71n.png" width="80%"></kbd></p>

<br>

<a id="node-51598p7"></a>

> [!NOTE]
> Note that some operations can be performed using
> static functions like \\*np.sum\\*() or \\*np.mean\\*(), or by using
> the \\*inner functions of the array\\*

<br>

<a id="node-8xbp4pl"></a>

> [!NOTE]
> nparray2 = np.array([[1, 3], [2, 4], [3, 5]]) # Define a 3 x 2 matrix. 
>
> mean1 = \\*np.mean\\*(nparray2) # Static way
> mean2 = nparray2\\*.mean()\\*   # Dinamic way
>
> print(mean1, ' == ', mean2)
>
> Even if they are equivalent, we **recommend
> the use of the static way** always.

<br>

<a id="node-dxpyczf"></a>

<p align="center"><kbd><img src="assets/qh6u9vpsqm.png" width="80%"></kbd></p>

<br>

<a id="node-6wx5a78"></a>

## Euclidean Distance

<br>

<a id="node-efl8a2a"></a>

> [!NOTE]
> 1 \\*Euclidean\\* \\*distance\\* is a \\*similarity metric\\* used to determine \\*how far two
> points or vectors are from each other.\\*
>
> 2 Euclidean distance can be used to calculate the \\*distance between two
> document vectors\\*, as well as v\\*ector spaces in higher dimensions\\*.
>
> 3 The formula for Euclidean distance involves finding the horizontal and
> vertical distance squared and adding them together.
>
> 4 The \\*Pythagorean theorem\\* is used to calculate the Euclidean distance
> between two points.
>
> 5 In \\*higher dimensions\\*, the Euclidean distance formula is \\*the norm of the
> difference between the vectors\\* being compared.
>
> 6 The implementation of Euclidean distance in Python can be done using
> the \\*linag\\* module from NumPy.
>
> 7 The primary takeaway of Euclidean distance is that it can be used to
> determine the \\*similarity between two documents or words.\\*
>
> 8 The next video will discuss \\*cosine\\* \\*similarity\\*, another popular similarity
> function.

<br>

<a id="node-56v0ns4"></a>

<p align="center"><kbd><img src="assets/kizpttcio2f.png" width="80%"></kbd></p>

> [!NOTE]
> Chiều dài đoạn thẳng nối 2 vector.
> Dễ dàng tính bằng Pythago

<br>

<a id="node-l9uv2im"></a>

<p align="center"><kbd><img src="assets/w4ofl0pa0wq.png" width="80%"></kbd></p>

> [!NOTE]
> Và nó cũng chính là norm của 'hiệu 2 vector'
>
>
>
> the norm of the difference between the vectors
>
>
>
> Norm của vector là **sqrt của tổng bình phương các element** của nó
>
>
>
> Norm ở đây nói chọn chứ đúng phải nói rõ ra là **L2 norm**, còn đv L1 norm thì
> (không sqrt) tổng các  absolute value các element
>
>
>
> Công thức chung là Ln norm = (a1**n + a2**n + ...)** (1/n)

<br>

<a id="node-qemn0oy"></a>

<p align="center"><kbd><img src="assets/mwwjj38y9ni.png" width="80%"></kbd></p>

> [!NOTE]
> Để tính (L2) norm trong Python
> thì dùng **np.linalg.norm**

<br>

<a id="node-9i4f9gm"></a>

<p align="center"><kbd><img src="assets/o7895dd42s.png" width="80%"></kbd></p>

<br>

<a id="node-rnbxfle"></a>

<p align="center"><kbd><img src="assets/mcuoxak0s7d.png" width="80%"></kbd></p>

<br>

<a id="node-5vlnat2"></a>

## Cosine Similarity: Intuition

<br>

<a id="node-ahc6bxb"></a>

> [!NOTE]
> 1 Introduction to \\*cosine similarity\\* as a \\*similarity metric\\* for comparing \\*vector
> representations.\\*
>
> 2 The \\*problem of using Euclidean distance\\* to compare vector
> representations of documents or corpora.
>
> 3 Example of how the Euclidean distance can be \\*problematic\\* in comparing
> \\*different sized corpora.\\*
>
> 4 The use of \\*cosine\\* \\*similarity\\* as a \\*better proxy\\* for \\*similarity between vector\\*
> representations than Euclidean distance.
>
> 5 Explanation of the main \\*advantage\\* of cosine similarity over Euclidean
> distance.
>
> 6 The intuition behind the use of cosine similarity as a metric to compare
> the \\*similarity between two vector representations.\\*
>
> 7 Advantages of cosine similarity when comparing documents of \\*different
> sizes.\\*
>
> 8 The opportunity to learn how to calculate cosine similarity.

<br>

<a id="node-43vnukg"></a>

<p align="center"><kbd><img src="assets/5bhjblmkbw7.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là **vấn đề với Euclidean** là nếu **chiều dài vector khác nhau nhiều**
> (corpus nhỏ - bộ từ trong 1 lĩnh vực đại khái vậy) thì **khoảng cách vector
> không phản ánh đúng độ giống giữa 2 vector** ví dụ Foot và Agriculture do
> chênh lệch kích thước corpus mà thành ra xa nhau hơn là Agriculture với
> History nếu đo bằng Euclidean (d1 > d2)
>
>
>
> Dùng hàm **cosine** **góc giữa 2 vector càng nhỏ** thì **chúng càng giống nhau**
> sẽ **nắm bắt tốt hơn sự giống nhau giữa các vector (alpha < beta)**

<br>

<a id="node-0qdqz16"></a>

<p align="center"><kbd><img src="assets/o7zn6sl50f.png" width="80%"></kbd></p>

<br>

<a id="node-h5imz29"></a>

## Cosine Similarity

<br>

<a id="node-j6v5a3f"></a>

> [!NOTE]
> 1 The video teaches how to compute the \\*dot product\\* and \\*norm
> of vectors\\* to calculate the cosine similarity score.
>
> 2 The \\*cosine similarity\\* score measures the \\*similarity of the
> directions of two vectors.\\*
>
> 3 The \\*cosine similarity\\* takes values \\*between 0 and 1\\* for the
> vector spaces seen so far.
>
> 4 The \\*closer the cosine similarity score is to 1\\*, the \\*more similar
> the vectors' directions are\\*.
>
> 5 A \\*cosine similarity score of 1\\* indicates \\*identical vectors,\\* while
> a score of \\*0 indicates orthogonal vectors.\\*
>
> 6 \\*Similar vectors\\* have \\*higher cosine similarity scores\\*.

<br>

<a id="node-gl47zg7"></a>

<p align="center"><kbd><img src="assets/oza27j3wani.png" width="80%"></kbd></p>

<br>

<a id="node-0lb817d"></a>

<p align="center"><kbd><img src="assets/pcu9fp82qg.png" width="80%"></kbd></p>

> [!NOTE]
> Ôn lại ha khái niệm
> **norm** và **dot product**

<br>

<a id="node-ud4m6mf"></a>

<p align="center"><kbd><img src="assets/mj5dj78iu8.png" width="80%"></kbd></p>

> [!NOTE]
> Công thức nó vầy rảnh
> thì chứng minh lại

<br>

<a id="node-8g44kg9"></a>

<p align="center"><kbd><img src="assets/a626yuw4t65.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là rất dễ hiểu tại sao lại dùng cosine làm thước đó đơn giản vì
> cosine giữa chúng càng lớn, 2 vector càng cùng hướng -> mà max
> cosine là 1 thì 2 véctơ trùng hướng luôn còn ngược lại thì cosine càng
> nhỏ thì 2 thằng càng khác hướng nhau mà min khi hai vector vuông góc
> gọi là **maximum dissimilar**. Nên cosine là thước đo tốt cho độ **direction
> similarity của 2 vectors, cosine càng lớn thì 2 thằng càng giống**

<br>

<a id="node-aakgz8o"></a>

<p align="center"><kbd><img src="assets/uvr6t2bvct7.png" width="80%"></kbd></p>

<br>

<a id="node-dsgld9i"></a>

## Manipulating Words In Vector Sapces

<br>

<a id="node-kl3cuuo"></a>

> [!NOTE]
> 1 Introduction: The video teaches how to \\*manipulate vectors\\* to \\*predict the capital city of a
> country.\\*
>
> 2 \\*Manipulating vector \\*representations: \\*Vector algebra\\* can be used to infer\\* unknown
> relationships among words.\\*
>
> 3 Finding \\*relationship between vectors\\*: Find the \\*difference between the vectors \\*of two related
> entities to determine \\*how many units on each dimension to move to find other related entities.\\*
>
> 4 Predicting capital of Russia: Adding the vector of Russia with the previously calculated vector
> will give the vector representation of its capital.
>
> 5 Finding the \\*closest representation\\*: \\*Compare the vector representations of all possible cities\\*
> with the vector representation obtained above \\*using Euclidean distances\\* or \\*cosine similarities\\*
> to d\\*etermine the most similar city\\*.
>
> 6 Importance of vector space: The process \\*can only be done in a vector space\\* that c\\*aptures
> the relative meaning of words\\*.
>
> 7 \\*Clustering\\* of vectors: The vectors of \\*words that occur in similar places in a sentence \\*will be
> encoded in a \\*similar\\* way.
>
> 8 \\*Identifying patterns:\\* Take advantage of the consistency encoding to identify patterns, such as
> finding the closest words to a given word by computing cosine similarity.
>
> 9 Plotting d-dimensional vectors on a 2D plane: Learn how to plot vectors on a 2D plane in the
> next video.

<br>

<a id="node-2be1al9"></a>

<p align="center"><kbd><img src="assets/dc2zoc2ckr.png" width="80%"></kbd></p>

<br>

<a id="node-v1vwm7t"></a>

<p align="center"><kbd><img src="assets/hnp5i24hytn.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là nếu ta biết  WD là thủ đô USA thì **chiều của vector WD - USA** cho ta biết
> **mối quan hệ của vector (encoded cho) nước và (encoded vector của) thủ đô phải
> như thế nào**
>
>
>
> Từ đó nếu có encoded vector của nước khác như **Russian** thì ta sẽ **predict** được
> en**coded vector của thủ đô của nó** dựa theo quan hệ của **WD-USA**
>
>
>
> Và khi chọn ra cái gần nhất - giống nhất (dựa trên metric cosine similarity hoặc
> Euclidean distance) với cái predict trong số các thủ đô thì ta sẽ thấy **Moscow** là gần
> nhất.
>
>
>
> Và tính sai lệch giữa predicted capital of Russia và actual (Moscow) bằng Euclidean
> distance hoặc Cosine similarity

<br>

<a id="node-svdxbx1"></a>

<p align="center"><kbd><img src="assets/ud2c1za884.png" width="80%"></kbd></p>

<br>

<a id="node-1k61rbo"></a>

<p align="center"><kbd><img src="assets/y5bll62gkt9.png" width="80%"></kbd></p>

> [!NOTE]
> Turkey (3,1) + (5, -1) = Predicted Capital: (8, 0)
>
>
>
> Actual (Ankara): (9,1)
>
>
>
> -> Euclidean distance = norm of (predicted - actual) 
>  square root of { (8-9)**2 + (0-1)**2 } = sqrt(2) = 1.41

<br>

<a id="node-5m5wmmi"></a>

<p align="center"><kbd><img src="assets/oepw8d5nkyk.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với 1 không gian vector kiểu như các từ đều được
> encoded thì các quan hệ giữa các từ gần nhau đã biết sẽ có thể
> cho phép ta đưa ra những dự đoán

<br>

<a id="node-w4uthj9"></a>

## Manipulating Word Embeddings

<br>

<a id="node-bh1t5zj"></a>

### Manipulating word embeddings

<br>

<a id="node-xtnq6fx"></a>

> [!NOTE]
> In this week's assignment, you are going to use a
> \\*pre-trained word embedding\\* for finding word analogies
> and equivalence. This exercise can be used as an
> \\*Intrinsic Evaluation\\* for the word embedding
> performance. In this notebook, you will apply linear
> algebra operations using NumPy to find analogies
> between words manually. This will help you to prepare
> for this week's assignment.
>
> Đại khái nói sẽ dùng 1 pre-trained word embedding để xem thử và từ
> đó hiểu được ý nghĩa của việc tạo các word embedding vector trong
> việc khắc hoạ được ý nghĩ và mối quan hệ của nó với các từ khác

<br>

<a id="node-m48dbe0"></a>

> [!NOTE]
> import pandas as pd # Library for Dataframes 
> import numpy as np # Library for math functions
> import pickle # Python object serialization library. Not secure
>
> \\*word_embeddings\\* = pickle.load( open( "./data/word_embeddings_subset.p", "rb" ) )
> len(word_embeddings) # there should be 243 words that will be used in this assignment

<br>

<a id="node-y5kx7vv"></a>

> [!NOTE]
> Now that the model is loaded, we can take a look at
> the word representations. First, note that
> \\*word_embeddings\\* is a Agriculture. Each word is the
> key to the entry, and the value is its corresponding
> vector presentation. Remember that \\*square
> brackets\\* allow access to any entry if the key exists.

<br>

<a id="node-7z4dkmt"></a>

> [!NOTE]
> countryVector = word_embeddings\\*['country']\\* # Get the \\*vector representation\\* for the word '\\*country\\*'
> print(type(countryVector)) # Print the type of the vector. Note it is a numpy array
> print(countryVector) # Print the values of the vector.

<br>

<a id="node-tc6851p"></a>

> [!NOTE]
> It is important to note that we store each vector as a
> NumPy array. It allows us to use the linear algebra
> operations on it.
>
> The vectors have a size of \\*300\\*, while the vocabulary
> size of Google News is around \\*3 million word\\*s!

<br>

<a id="node-73vqc8j"></a>

> [!NOTE]
> #Get the vector for a given word:
> def vec(w):
>     return word_embeddings[w]

<br>

<a id="node-u3gb9xi"></a>

> [!NOTE]
> Operating on word
> embeddings

<br>

<a id="node-bhkrzgf"></a>

> [!NOTE]
> Remember that \\*understanding the data\\* is one of the \\*most critical steps \\*in Data
> Science.\\* Word embeddings\\* are the result of \\*machine learning processe\\*s and will
> be part of the input for further processes. These word embedding needs to be
> \\*validated\\* or at least \\*understood\\* because the performance of the derived model
> will strongly depend on its quality.
>
> Word embeddings are \\*multidimensional arrays\\*, usually with \\*hundreds of
> attributes\\* that pose a challenge for its interpretation.
>
> In this notebook, we will \\*visually inspect\\* the \\*word embedding\\* of some words
> using a \\*pair of attributes\\*. Raw attributes are not the best option for the creation of
> such charts but will allow us to illustrate the mechanical part in Python.
>
> In the next cell, we make a beautiful \\*plot\\* for the \\*word embeddings of some words\\*.
> Even if plotting the dots gives an idea of the words, the arrow representations help to
> visualize the vector's alignment as well.
>
> Đại khái là word embedding vector thường có hàng trăm
> unit/feature/attribute/(dimension) là kết quả của một quá trình
> ML training (để tìm ra / khắc hoạ ra nghĩa, quan hệ của nó đv
> các từ khác trong không gian từ vựng) nhưng ở đây ta sẽ dùng
> 2 attributes để plot

<br>

<a id="node-er2dc0q"></a>

> [!NOTE]
> import matplotlib.pyplot as plt # Import matplotlib
> %matplotlib inline
>
> words = ['oil', 'gas', 'happy', 'sad', 'city', 'town', 'village', 'country', 'continent', 'petroleum', 'joyful']
>
> bag2d = np.array([vec(word) for word in words]) # \\*Convert each word to its vector representatio\\*n
>
> fig, ax = plt.subplots(figsize = (10, 10)) # Create custom size image
>
> \\*col1 = 3 \\*# \\*Select the column\\* for the x axis
> col2 = \\*2\\* # \\*Select the column\\* for the y axis
>
> # Print an arrow for each word
> for word in bag2d:
>     ax.arrow(0, 0, word[col1], word[col2], head_width=0.005, head_length=0.005, fc='r', ec='r', width = 1e-5)
>
>
> ax\\*.scatter\\*(bag2d[:, col1], bag2d[:, col2]); # Plot a dot for each word
>
> # Add the word label over each dot in the scatter plot
> for I in range(0, len(words)):
>     ax.annotate(words[I], (bag2d[I, col1], bag2d[I, col2]))
>
>
> plt.show()
>
> Đại khái là **chọn vài từ** rồi tạo (lấy ra từ word_embedding dictionary) **representation
> vectors** xong **chọn 2 attribute / feature** trong hàng trăm (**300) features** của nó để plot

<br>

<a id="node-bsxnid8"></a>

<p align="center"><kbd><img src="assets/1mdahqsdlcz.png" width="80%"></kbd></p>

> [!NOTE]
> Note that **similar words** like '**village**' and '**town**' or '**petroleum**', '**oil**', and 'gas'
> tend to point in the same direction. Also, note that **'sad' and 'happy' looks
> close to each other; however, the vectors point in opposite directions**.
>
>
>
> In this chart, one can figure out the **angles** and **distances** between the
> words. Some words are close in both kinds of distance metrics.
>
> Nhận xét thấy các từ mà ta hiểu nghĩa gần nhau (về
> bối cảnh như sad, happy là đều về emotion, village &
> town) thật sự xuất hiện gần nhau trên plot.
>
>
>
> Nhưng hướng của chúng lại thể hiện sự tương quan về ý nghĩa
> của từ, sad với happy đi hai hướng có góc gần với 90 thể hiện
> chúng đối nghĩa nhau

<br>

<a id="node-7k62xnq"></a>

### Word distance

<br>

<a id="node-qar1bkd"></a>

> [!NOTE]
> Now \\*plot\\* the words '\\*sad\\*', '\\*happy\\*', '\\*town\\*', and '\\*village\\*'. In this
> same chart, \\*display the vector from 'village' to 'town'\\* and the
> \\*vector from 'sad' to 'happy'\\*. Let us use NumPy for these
> linear algebra operations.

<br>

<a id="node-13zdxvn"></a>

> [!NOTE]
> words = ['sad', 'happy', 'town', 'village']
>
> bag2d = np.array([vec(word) for word in words]) # Convert each word to its vector representation
>
> fig, ax = plt.subplots(figsize = (10, 10)) # Create custom size image
>
> col1 = 3 # Select the column for the x axe
> col2 = 2 # Select the column for the y axe
>
> # Print an arrow for each word
> for word in bag2d:
>     ax.arrow(0, 0, word[col1], word[col2], head_width=0.0005, head_length=0.0005, fc='r', ec='r', width = 1e-5)
>
> # print the vector difference between village and town
> village = vec('village')
> town = vec('town')
> diff = town - village
> ax.arrow(village[col1], village[col2], diff[col1], diff[col2], fc='b', ec='b', width = 1e-5)
>
> # print the vector difference between village and town
> sad = vec('sad')
> happy = vec('happy')
> diff = happy - sad
> ax.arrow(sad[col1], sad[col2], diff[col1], diff[col2], fc='b', ec='b', width = 1e-5)
>
>
> ax.scatter(bag2d[:, col1], bag2d[:, col2]); # Plot a dot for each word
>
> # Add the word label over each dot in the scatter plot
> for I in range(0, len(words)):
>     ax.annotate(words[I], (bag2d[I, col1], bag2d[I, col2]))
>
>
> plt.show()

<br>

<a id="node-yhu8350"></a>

<p align="center"><kbd><img src="assets/v5feczbl4wq.png" width="80%"></kbd></p>

> [!NOTE]
> Sad và happy giống như vuông góc biểu thị
> quan hệ hoàn toàn trái ngược, vilage với
> town có vẻ cùng hướng hơn

<br>

<a id="node-eudhsd2"></a>

> [!NOTE]
> Linear algebra on
> word embeddings

<br>

<a id="node-4wrhx2u"></a>

> [!NOTE]
> print(\\*np.linalg.norm\\*(vec('town'))) # Print the norm of the word town
> print(\\*np.linalg.norm\\*(vec('sad'))) # Print the norm of the word sad
>
> 2.3858097
> 2.9004838
>
> In the lectures, we saw the analogies between words using
> **algebra** on word embeddings. Let us see how to do it in
> Python with Numpy.
>
>
>
> To start, get the norm of a word in the word embedding.

<br>

<a id="node-3shpds0"></a>

### Predicting capitals

<br>

<a id="node-s8ycmkx"></a>

> [!NOTE]
> Now, applying v\\*ector difference\\* and \\*addition\\*, one can
> create a \\*vector representation for a new word\\*. For
> example, we can say that the \\*vector difference
> between 'France' and 'Paris\\*' represents the \\*concept of
> Capital.\\*
>
> One can move from the city of Madrid in the direction
> of the concept of Capital, and obtain something close
> to the corresponding country to which Madrid is the
> Capital.
>
> **Hiệu hai vector France và Paris** sẽ đại diện cho **khái
> niệm thủ đô**. Thử tìm từ nào mà hợp với Madrid để
> tạo vector cùng chiều với vector đại diện cho khái
> niệm thủ đô này

<br>

<a id="node-rv0pqhk"></a>

> [!NOTE]
> Capital = vec('France') - vec('Paris')
> Country = vec('Madrid') + capital
>
> print(country[0:5]) # Print the first 5 values of the vector
>
> ->[-0.02905273 -0.2475586   0.53952026  0.20581055 -0.14862823]
>
>
> Tính ra vector của từ dự
> đoán sẽ là Spain này

<br>

<a id="node-jqyuudr"></a>

> [!NOTE]
> Diff = country - vec('Spain')
> print(diff[0:10])
>
> [-0.06054688 -0.06494141  0.37643433  0.08129883 -0.13007355 -0.00952148
>  -0.03417969 -0.00708008  0.09790039 -0.01867676]
>
>
> We can observe that the vector 'country' that
> we expected to be the same as the vector
> for Spain is n**ot exactly it**.
>
> Thì thấy nó không trùng khớp với
> Spain (different khác 0)

<br>

<a id="node-xjor3zv"></a>

> [!NOTE]
> # Create a dataframe out of the dictionary embedding. This facilitate the algebraic operations
> keys = word_embeddings.keys()
> data = []
> for key in keys:
>     data.append(word_embeddings[key])
>
> embedding = pd.\\*DataFrame\\*(data=data, index=keys)
> # Define a function to find the closest word to a vector:
> def find_closest_word(v, k = 1):
>     # Calculate the vector difference from each word to the input vector
>     diff = embedding.values - v 
>     # Get the squared L2 norm of each difference vector.
>     # It means the squared euclidean distance from each word to the input vector
>     delta = np.sum(diff * diff, axis=1)
>     # Find the index of the minimun distance in the array
>     I = np.argmin(delta)
>     # Return the row name for this item
>     return embedding.iloc[I].name
>
>
> So, we have to **look for the closest words** in the embedding that
> matches the candidate country. If the word embedding works as
> expected, the most similar word must be 'Spain'. Let us define a
> function that helps us to do it. We will store our word embedding as a
> DataFrame, which facilitate the lookup operations based on the
> numerical vectors.
>
> Nên thử tìm **từ gần nhấ**t với từ này
> trong data xem sao, ổng cho sẵn 1
> hàm **find_closest_word**

<br>

<a id="node-buk1n0m"></a>

<p align="center"><kbd><img src="assets/roe3viib0p9.png" width="80%"></kbd></p>

> [!NOTE]
> Thì tuy không ra chính xác Spain
> nhưng từ Spain là **từ 'gần nhất'** với
> vector từ prediction này

<br>

<a id="node-ejxl3cc"></a>

### Predicting other Countries

<br>

<a id="node-fqoakg1"></a>

<p align="center"><kbd><img src="assets/rdhlen17hv.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là thử với các quan hệ khác tìm từ mà quan hệ của nó với
> Madrid gần với quan hệ giữa Italy và Rome nhất sẽ ra Spain

<br>

<a id="node-ol3i3cn"></a>

### Represent a sentence as a vector

<br>

<a id="node-ewvdibc"></a>

<p align="center"><kbd><img src="assets/m0vsmeiftv.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là represented vector của 1
> **sentence** là **sum của các word vector**

<br>

<a id="node-2tf3mhf"></a>

<p align="center"><kbd><img src="assets/1ddzk0g6guv.png" width="80%"></kbd></p>

<br>

<a id="node-ttilqvo"></a>

## Visualization And Pca

<br>

<a id="node-m62t8ey"></a>

> [!NOTE]
> 1 Introduction to the \\*problem\\* of \\*high-dimensional vectors\\* and the
> need for \\*dimensionality reduction\\* for \\*visualization\\*.
>
> 2 Explanation of \\*principal component analysi\\*s (\\*PCA\\*) and how it can
> be used to \\*reduce the dimension \\*of \\*vector representations.\\*
>
> 3 Motivation for visualizing vector representations of words and using PCA
> to \\*identify relationships among words\\*.
>
> 4 Process of performing PCA on data to \\*obtain uncorrelated features\\*
> and \\*projecting data to a lower dimensional space.\\*
>
> 5 Importance of \\*retaining as much information as possible\\* during the
> dimensionality reduction process.
>
> 6 Review of the main ideas discussed, including the use of PCA for
> \\*visualizing data\\* and \\*transforming high-dimensional vectors\\* into\\* two
> dimensions\\* for \\*plotting\\*.

<br>

<a id="node-0b0s822"></a>

<p align="center"><kbd><img src="assets/ifa42jl2048.png" width="80%"></kbd></p>

<br>

<a id="node-2rncpr5"></a>

<p align="center"><kbd><img src="assets/wldavtnw10a.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với high dimension vector thì làm sao visualize ra mà
> xem khi mà nó có nhiều hơn 2 feature

<br>

<a id="node-ms9wvzt"></a>

<p align="center"><kbd><img src="assets/vg1pvhhm6wk.png" width="80%"></kbd></p>

> [!NOTE]
> Giải pháp như đã quá biết là dùng Principal Component Analysis để
> giảm từ nhiều dimension xuống còn 2 hay 3 features mà giữ tối đa thông
> tin để từ đó có thể plot trên không gian 2d hay 3d

<br>

<a id="node-u6doot6"></a>

<p align="center"><kbd><img src="assets/ki95xmtjbdq.png" width="80%"></kbd></p>

<br>

<a id="node-ave4i7k"></a>

<p align="center"><kbd><img src="assets/shb5q1h8ck.png" width="80%"></kbd></p>

<br>

<a id="node-xwrn6xh"></a>

<p align="center"><kbd><img src="assets/u0lre6muc0f.png" width="80%"></kbd></p>

> [!NOTE]
> Một điểm chú ý mà có thể những bài giảng về PCA trước có nói nhưng không
> để ý là '**uncorrelated features**', nhưng ở đây cũng chưa nói rõ tại sao hoặc là cái gì

<br>

<a id="node-ndwk9zb"></a>

<p align="center"><kbd><img src="assets/c06ruhhm4fu.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/0pa9dlhqwze.png" width="80%"></kbd></p>

> [!NOTE]
> Một số training algorithm khi learn words họ dùng cách identifying
> neighboring words nên encoding words vector với similar POS thường
> sẽ plot ra gần nhau
>
>
>
> Câu hỏi gợi mở là tại sao sad và joyful mang nghĩa trái ngược cùng gần
> nhau? -> Tại vì không gian ngữ cảnh của nó gần nhau cũng tính chất emotion

<br>

<a id="node-a4mcb72"></a>

## Pca Algorithm

<br>

<a id="node-as08y8h"></a>

> [!NOTE]
> 1 Introduction to \\*reducing the dimension of features \\*using \\*Eigenvalues\\* and
> \\*Eigenvectors\\*
>
> 2 Process for dimensionality reduction using \\*PCA\\*, including obtaining
> \\*uncorrelated features\\*, \\*normalizing data\\*, and performing \\*singular value
> decomposition\\*
>
> 3 Obtaining \\*Eigenvectors\\* and \\*Eigenvalues\\* from the \\*co-variance matrix\\* of
> \\*normalized data\\* for PCA
>
> 4 \\*Projecting data onto a new vector space\\* using Eigenvectors and Eigenvalue
>
> 5 Importance of organizing \\*Eigenvectors\\* and \\*Eigenvalues\\* in \\*descending order\\*
> to r\\*etain information\\*
>
> 6 Implementation of \\*PCA\\* in a \\*programming library\\* and its use in visualizing
> word representations
>
> 7 Future topic of learning about \\*vector spaces\\* and building a simple \\*machine
> translation\\* system

<br>

<a id="node-4dyt9wh"></a>

<p align="center"><kbd><img src="assets/ucg115bd91f.png" width="80%"></kbd></p>

<br>

<a id="node-mdsgbv1"></a>

<p align="center"><kbd><img src="assets/rz2589nikel.png" width="80%"></kbd></p>

> [!NOTE]
> **Eigenvector**: the resulting vectors, also known as the **uncorrelated** **features** of
> your data
>
>
>
> **Eigenvalue**: the **amount of information retained by each new feature**. You can
> think of it as the **variance** in the eigenvector.
>
>
>
> Also each **eigenvalue** has a **corresponding eigenvector**. The eigenvalue tells you
> **how much variance there is in the eigenvector.** Here are the steps required to
> compute PCA:

<br>

<a id="node-eeevfuy"></a>

<p align="center"><kbd><img src="assets/ozhu1bfl9t.png" width="80%"></kbd></p>

> [!NOTE]
> Cái này có thể mới hoặc đã học mà ko để ý là **eigenvector** là các
> **unrelated features** còn **eigenvalue** là phần thông tin **retained** by each
> feature

<br>

<a id="node-bfgqw0q"></a>

<p align="center"><kbd><img src="assets/mz15db8tlx.png" width="80%"></kbd></p>

> [!NOTE]
> Cách tính như vầy, nhưng ổng nói khỏi lo
> có lib tính giùm hiểu là được

<br>

<a id="node-zmx10qd"></a>

<p align="center"><kbd><img src="assets/hnui8uqdprv.png" width="80%"></kbd></p>

> [!NOTE]
> Thực hiện việc project tức là tính ra bộ data mới X' (ít feature hơn X) bằng cách
> dot product X với **matrix U lấy 2 cột đầu** **thôi** = 2 uncorrelated vector chứa
> nhiều thông tin nhất  (vì đang reduce về 2D mà, nếu về 3D thì lấy 3)
>
>
>
> Thì tính thử percentage of **retained variance** bằng tỉ lệ của 2 thằng đầu tiên
> trong đường chéo của matrix S (Sum S00+S11) và tổng các value trên đường
> chéo (Sum S00+S11+..Sdd)
>
>
>
> Ôn lại lại, matrix **U** là **eigenvector**, sẽ có **D cột** biểu thị cho  D feature
> (những đã chuyển thành D **uncorrelated feature**)  hay D dimension ban đầu,
> bây giờ muốn g**iảm xuống D' < D dimension thì lấy D' cột đầu thôi** và tương
> ứng với nó sẽ bị mất thông tin
>
>
>
> Again do đã học qua PCA ở ML Spec nên biết mấy cái này cũng  không khó.

<br>

<a id="node-h78x7q8"></a>

<p align="center"><kbd><img src="assets/wmzwc3uyonj.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là Eigenvector sẽ đại diện cho các
> **uncorrelated feature**, kiểu như SVD nó sẽ phân tích
> bộ data ban đầu với D feature (correlated) để tách
> thành D cái uncorrelated feature

<br>

<a id="node-rnguswe"></a>

## Another Explanation About Pca

> [!NOTE]
> Một số cái không hiểu, quay lại sau

<br>

<a id="node-i4etwjp"></a>

### Another explanation about PCA

<br>

<a id="node-885ahd8"></a>

> [!NOTE]
> In this lab, we are going to view another explanation about Principal Component
> Analysis(PCA). PCA is a \\*statistical technique\\* invented in 1901 by Karl Pearson that uses
> orthogonal transformations to \\*map a set of variables\\* into a set of \\*linearly uncorrelated
> variables\\* called \\*Principal Components.\\*
>
> PCA is based on the \\*Singular Value Decomposition (SVD) \\*of the \\*Covariance Matrix\\* of
> the original dataset. The \\*Eigenvectors\\* of such decomposition are used as a \\*rotation
> matrix\\*. The \\*Eigenvectors are arranged in the rotation matrix in decreasing order according
> to its explained variance\\*. This last term is related to the \\*EigenValues\\* of the SVD.
>
> PCA is a potent technique with applications ranging from \\*simple space transformation\\*,
> \\*dimensionality reduction\\*, and mixture separation from spectral information.
>
> Follow this lab to view \\*another explanation for PCA\\*. In this case, we are going to use the
> concept of \\*rotation matrices\\* applied to \\*correlated random data\\*, just as illustrated in the
> next picture.
>
> /"The **Eigenvectors are arranged in the rotation matrix in decreasing order
> according to its explained variance**." /
>
>
>
> ->À như vậy **rotation matrix** chính là **matrix U** đó mà **mỗi cột là một
> Eigenvector** sắp theo **thứ tự giảm dần của explained variance** cũng là cái có
> liên quan đến **Eigenvalue**
>
>
>
> Hiểu thêm / mới rằng đại khái là từ **D feature** ban đầu của **X**, phép **SVD**
> sẽ map data thành **D unrelated new features** mỗi features được **đại diện bằng
> 1 Eigenvector** theo thứ tự từ cái có e**xplained variance lớn nhất tới nhỏ nhất**.
> Để từ đó muốn giảm xuống (d**imensionality reduction**) còn **K < D** feature thì
> tính bằng cách nhân **X với K Eigenvector đầu thôi**
>
>
>
> Và PCA có nhiều ứng dụng mà ở đây sẽ **giải thích một cách khác** về PCA

<br>

<a id="node-zqyj8d2"></a>

<p align="center"><kbd><img src="assets/d491g9hffgh.png" width="80%"></kbd></p>

<br>

<a id="node-roiceif"></a>

> [!NOTE]
> import numpy as np                         # Linear algebra library
> import matplotlib.pyplot as plt            # library for visualization
> from \\*sklearn.decomposition\\* import \\*PCA\\*      # PCA library
> import pandas as pd                        # Data frame library
> import math                                # Library for math functions
> import random                              # Library for pseudo random numbers

<br>

<a id="node-1l3ra9w"></a>

> [!NOTE]
> np.random.seed(1)
> n = 1  # The amount of the correlation
> x = np.random.uniform(1,2,1000) # Generate 1000 samples from a uniform random variable
> y = x.copy() * n # Make y = n * x
>
> # PCA works better if the data is centered
> \\*x = x - np.mean(x)\\* # \\*Center x\\*. Remove its mean
> \\*y = y - np.mean(y)\\* # \\*Center y\\*. Remove its mean
>
> data = \\*pd.DataFrame\\*({'x': x, 'y': y}) # \\*Create a data frame with x and y\\*
> plt.\\*scatter\\*(data.x, data.y) # Plot the original correlated data in blue
>
> pca = \\*PCA\\*(\\*n_components=2\\*) # \\*Instantiate a PCA\\*. Choose to get 2 output variables
>
> # Create the\\* transformation model for this data\\*. \\*Internally\\*, it gets the \\*rotation\\* 
> # \\*matrix\\* and the\\* explained variance\\*
> pcaTr = pca.\\*fit\\*(data)
>
> rotatedData = pcaTr.\\*transform(data)\\* # \\*Transform the data\\* base on the \\*rotation matrix\\* of pcaTr
>
>
> # # \\*Create a data frame\\* with the \\*new variables\\*. We call these new variables \\*PC1\\* and \\*PC2\\*
> dataPCA = pd.DataFrame(\\*data = rotatedData\\*, \\*columns = ['PC1', 'PC2']\\*) 
>
> # Plot the transformed data in orange
> plt.\\*scatter\\*(\\*dataPCA.PC1\\*, \\*dataPCA.PC2\\*)
> plt.show()
>
> To start, let us consider a pair of random variables x, y.
> Consider the base case when **y = n * x**. The x and y
> variables will be **perfectly correlated to each other** since
> **y is just a scaling of x**.
>
> Tóm tắt lại cái này, rất đơn giản
>
>
>
> Ổng tạo bộ dataset với x random và, y = 1*x
>
>
>
> Đầu tiên PCA để work tốt hơn thì làm động tác centerlized data X,
> Y bằng cách trừ x cho mean x tức với mỗi dataset x(i), trừ từng
> feature x1 - mu1 (mean của feature 1), x2 - mu2 (mean feature 2).
> Bước này như khi normalizing thì thêm chia cho variance nữa thôi.
>
>
>
> Kế là tạo PCA model bằng Scikit-Learn với **n_compoent** là 2
>
>
>
> Xong dùng function fit để được pcaTr (PCA transformation) và
> transform để ..transform X.
>
>
>
> Và trong cái pcaTr này sẽ có **rotation matrix** và **explained
> variance** lưu trong **pcaTr.components_ và pcaTr.explained_variance_**
>
>
>
> kết quả ra rotatedData sẽ có 2 feature mới dùng pandas.
> DataFrame để tạo lại DataFrame đặt column (feature name) là
> PCA1, PCA2

<br>

<a id="node-e5ur5bt"></a>

<p align="center"><kbd><img src="assets/57h0nr67r06.png" width="80%"></kbd></p>

<br>

<a id="node-j37e4ko"></a>

> [!NOTE]
> Understanding the
> transformation model pcaTr

<br>

<a id="node-ouqiurp"></a>

> [!NOTE]
> As mentioned before, a \\*PCA model\\* is composed of a \\*rotation matrix \\*and its
> \\*corresponding explained variance\\*. In the next module, we will explain the details of the
> rotation matrices.
>
> \\*pcaTr.components_\\* has the \\*rotation matrix\\*
>
> \\*pcaTr.explained_variance_\\* has the \\*explained variance\\* of each \\*principal component\\*

<br>

<a id="node-b97csqc"></a>

<p align="center"><kbd><img src="assets/5u90603vvxp.png" width="80%"></kbd></p>

> [!NOTE]
> print('Eigenvectors or principal component: First row must be in the direction of [1, n]')
> print(pcaTr.\\*components_\\*)
>
> print()
> print('Eigenvalues or explained variance')
> print(pcaTr.\\*explained_variance_\\*)
>
> Nó nói First row must be in direction
> of [1, n] là sao không hiểu?

<br>

<a id="node-nqjy87v"></a>

<p align="center"><kbd><img src="assets/vtyorqzgld.png" width="80%"></kbd></p>

> [!NOTE]
> Hoàn toàn không hiểu

<br>

<a id="node-udsond0"></a>

> [!NOTE]
> Correlated Normal
> Random Variables.

<br>

<a id="node-o9g2qft"></a>

> [!NOTE]
> Now, we will use a \\*controlled dataset\\* composed of \\*2 random variables\\* with
> \\*different variances\\* and with a \\*specific Covariance\\* among them. The only way
> I know to get such a dataset is, first, create two \\*independent Normal random
> variables\\* with the \\*desired variances\\* and then \\*combine\\* them using a \\*rotation
> matrix\\*. In this way, the new resulting variables will be a linear combination of
> the original random variables and thus be dependent and correlated.

<br>

<a id="node-5ih8b2n"></a>

> [!NOTE]
> import matplotlib.lines as mlines
> import matplotlib.transforms as mtransforms
>
> np.random.seed(100)
>
> std1 = 1     # The \\*desired standard deviation\\* of our first random variable
> std2 = 0.333 # The d\\*esired standard deviation\\* of our second random variable
>
> x = np.\\*random.normal\\*(0, \\*std1\\*, 1000) # \\*Get 1000 samples from x ~ N(0, std1)\\*
> y = np.\\*random.normal\\*(0, std2, 1000)  # \\*Get 1000 samples from y ~ N(0, std2)\\*
> #y = y + np.random.normal(0,1,1000)*noiseLevel * np.sin(0.78)
>
> # PCA works better if the data is centered
> x = x - \\*np.mean(x)\\* # \\*Center x\\* 
> y = y - \\*np.mean(y)\\* # \\*Center y
> \\*
> #Define a pair of dependent variables with a desired amount of covariance
> n = 1 # Magnitude of covariance. 
> angle = \\*np.arctan\\*(\\*1 / n)\\* # Convert the covariance to and angle
> print('angle: ',  angle * 180 / math.pi)
>
> # Create a \\*rotation matrix\\* using the given angle
> \\*rotationMatrix\\* = np.array([[np.\\*cos(angle)\\*, np.\\*sin(angle)\\*],
>                  [-np.\\*sin(angle)\\*, np.\\*cos(angle)\\*]])
>
>
> print('rotationMatrix')
> print(rotationMatrix)
>
> xy = np.concatenate(([x] , [y]), axis=0).T # Create a matrix with columns x and y
>
> # \\*Transform the data using the rotation matrix\\*. It correlates the two variables
> data = \\*np.dot(xy, rotationMatrix)\\* # Return a nD array
>
> # Print the rotated data
> plt.scatter(data[:,0], data[:,1])
> plt.show()
>
> đại khái là nó đang muốn tạo
> một bộ data randomly nhưng (distribution sao cho) với
> standard deviation là 1 cho x và 0.333 cho y.

<br>

<a id="node-dzhaivq"></a>

<p align="center"><kbd><img src="assets/5pxb2pe5pav.png" width="80%"></kbd></p>

> [!NOTE]
> Sau khi đọc Rotation Matrix có thể hiểu khúc này. Rất
> đơn giản vì hệ số góc của y = x là 1 (y = 1*x) nên tan =
> 1, từ đó tìm ra lại góc bằng bao nhiêu thôi dùng hàm
> arctan -> angle là 45 đó
>
>
>
> Rồi ổng tạo Rotation Matrix với góc beta 45 độ này theo công thức 
> của case xoay ngược chiều kim đồng hồ

**🔗 See also:** [linked note](#node-eytvksr)

<br>

<a id="node-59u706n"></a>

<p align="center"><kbd><img src="assets/afcazdixxo5.png" width="80%"></kbd></p>

> [!NOTE]
> Sau khi đọc **Rotation Matrix** có thể hiểu tiếp là nhân
> rotation matrix với vector để xoay vector qua 1 góc
> beta ở đây là 45 (ở đây đúng hơn xoay 1000 cái
> vector - xy là matrix (1000,2) được tạo thành bỏi câu
> concate hai vector x và y đó)

<br>

<a id="node-ubm6j83"></a>

<p align="center"><kbd><img src="assets/oj0gvhwbg0c.png" width="80%"></kbd></p>

<br>

<a id="node-4sxud0r"></a>

> [!NOTE]
> plt.scatter(data[:,0], data[:,1]) # Print the original data in blue
>
> # Apply PCA. \\*In theory, the Eigenvector matrix must be the 
> \\*# \\*inverse of the original rotationMatrix\\*. 
> pca = PCA(n_components=2)  # Instantiate a PCA. Choose to get 2 output variables
>
> # Create the transformation model for this data. Internally it gets the rotation 
> # matrix and the explained variance
> pcaTr = pca.\\*fit\\*(data)
>
> # Create an array with the transformed data
> \\*dataPCA\\* = pcaTr.\\*transform\\*(data)
>
> print('Eigenvectors or principal component: First row must be in the direction of [1, n]')
> print(pcaTr.components_)
>
> print()
> print('Eigenvalues or explained variance')
> print(pcaTr.explained_variance_)
>
> # Print the rotated data
> \\*plt.scatter(dataPCA[:,0], dataPCA[:,1])\\*
>
> # Plot the\\* first component axe\\*. Use the \\*explained variance to scale the vector\\*
> plt.plot([0, rotationMatrix[0][0] * std1 * 3], [0, rotationMatrix[0][1] * std1 * 3], 'k-', color=\\*'red\\*')
> # Plot the \\*second component axe\\*. Use the \\*explained variance to scale the vector\\*
> plt.plot([0, rotationMatrix[1][0] * std2 * 3], [0, rotationMatrix[1][1] * std2 * 3], 'k-', color='\\*green\\*')
>
> plt.show()
>
> Let us print the original and the resulting transformed system using the
> result of the PCA in the same plot alongside with the 2 Principal
> Component vectors in red and blue
>
> Hiểu 70%
>
> Tới đây đã hiểu phần nào như sau
>
>
>
> Đaị khái là lúc đầu ổng nói cái gì muốn tạo 2 uncorrelated feature gì gì  đó thì
> mình nên hiểu là ổng muốn tạo dataset distributed theo 2 trục vuông góc nhau
> - vuông góc nhau thì chính là uncorrelated
>
>
>
> Rồi ổng nói gì không biết cách nào để làm vậy ngoài việc tạo riêng  2 cái rồi có
> lẽ chính là bước ổng define x random, y random với mỗi  cái mỗi giá trị
> standard deviation mong muốn
>
>
>
> Tới đây nếu plot bộ data ra trước khi 'xoay' có lẽ sẽ ra giống như màu  cam.
>
>
>
> Xong ổng define Rotation Matrix với góc 45 từ hệ số góc 1 trong y = x để xoay
> cái dataset.
>
>
>
> Rồi ổng dùng PCA, apply và plot ra lại cũng như in cái Eigenvector ra cho thấy
> kết quả là quay cái bộ data 1 góc cũng 45 độ về lại ban đầu và Eigenvector
> (trong field **eigenvector_** của pcaTr bằng đúng giá trị của Rotation Matrix
> làm từ góc 45.
>
>
>
> *Cái điểm muốn mình hiểu ở đây là
> 1. PCA nó thực hiện phép xoay bộ data sao đó ...
> 2. ...

<br>

<a id="node-3opffmt"></a>

<p align="center"><kbd><img src="assets/j55d90edzj.png" width="80%"></kbd></p>

> [!NOTE]
> Vẽ cái data hồi nãy ra lại bằng các
> chấm xanh cái này hiểu

<br>

<a id="node-bk6y5u6"></a>

<p align="center"><kbd><img src="assets/jbn2lw760tj.png" width="80%"></kbd></p>

> [!NOTE]
> Ở đây cái câu này gợi ý Eigenvector phải là inverse của
> Rotation Matrix, gợi ý rằng nếu apply PCA, thì nhân
> matrix data X với Eigenvector sẽ xoay X 1 góc ngược
> với của Rotation Matrix?

<br>

<a id="node-l7msxg4"></a>

<p align="center"><kbd><img src="assets/wmazy8d1ms.png" width="80%"></kbd></p>

> [!NOTE]
> Thì, hiện tượng ổng muốn nói là, Eigenvector đúng là
> đóng vai trò như Rotation Matrix, nó xoay bộ data 1
> góc bằng đúng cái góc 45 độ

<br>

<a id="node-9ypqdyo"></a>

<p align="center"><kbd><img src="assets/htlthclgn5l.png" width="80%"></kbd></p>

> [!NOTE]
> Hiểu 70%
>
> Nhắc lại việc đầu tiên tạo uncorrelated variables x, y - hiểu mơ hồ
> rằng nó sẽ tạo các điểm phân bố ngẫu nhiên nhưng cái distribution
> của nó ..kiểu như 2 trục vuông góc.
>
>
>
> Xong dùng Rotation Matrix với góc của hệ số y = 1*x để xoay
>
>
>
> Rồi nó apply PCA thì thấy PCA nó tìm ra lại đúng cái Rotation
> Matrix này và xoay ngược trở lại vị trí cũ
>
>
>
> và Eigenvalue chính là bình phương 2 chỉ số standard deviation ban
> đầu  Khi tạo x, y là 1 và 0.333 tức là Variance 1 và Variance 2
> (Variance = standard deviation (sigma) **2 nhớ không)

<br>

<a id="node-7odxdqp"></a>

> [!NOTE]
> PCA as a strategy for
> dimensionality reduction

<br>

<a id="node-873epbw"></a>

> [!NOTE]
> The principal components contained in the \\*rotation matrix\\*, are \\*decreasingly
> sorted\\* depending on its \\*explained Varianc\\*e. It usually means that \\*the first
> components retain most of the power\\* of the data to \\*explain the patterns\\* that
> generalize the data. Nevertheless, for some applications, we are interested in
> the patterns that explain much less Variance, for example, in novelty
> detection.
>
> In the next figure, we can see the original data and its corresponding
> projection using dimenson axes as principal components. In other words,
> data comprised of a single variable.
>
> Đoạn này hiểu nè đại khái là vì rotation matrix sắp xếp các Eigenvector
> Theo giảm dần độ variance nên cái đầu sẽ là cái quan trọng nhất
> Trong việc chứa đựng những thông tin pattern của data.
>
>
>
> Nhưng đ.v một số trường hợp ta cần check những cái less variance
> hơn ví dụ như '**novelty detection**' - kiểu như anomaly detection,
> Những thằng (data instance) ở ngoài rìa

<br>

<a id="node-y1dl5mv"></a>

> [!NOTE]
> nPoints = len(data)
>
> # Plot the original data in blue
> plt.scatter(data[:,0], data[:,1])
>
> #Plot the projection along the first component in orange
> plt.scatter(data[:,0], np.zeros(nPoints))
>
> #Plot the projection along the second component in green
> plt.scatter(np.zeros(nPoints), data[:,1])
>
> plt.show()

<br>

<a id="node-2yt4q3p"></a>

<p align="center"><kbd><img src="assets/i7r707vsj2.png" width="80%"></kbd></p>

> [!NOTE]
> Hiểu, sau khi PCA thì cái feature 1 là màu cam,
> feature 2 là màu xanh. Nếu mình giảm
> dimension xuống chỉ có 1 trục thì nó chỉ còn cái
> màu cam (nó chứa variance nhiều nhất)

<br>

<a id="node-bo83i2d"></a>

> [!NOTE]
> PCA as a strategy to
> plot complex data

<br>

<a id="node-8lgs7mi"></a>

> [!NOTE]
> The next chart shows a sample diagram \\*displaying a dataset of pictures of
> cats and dogs\\*. Raw pictures are composed of \\*hundreds or even thousands
> of feature\\*s. However, PCA allows us to \\*reduce that many features to only
> two\\*. In that \\*reduced space of uncorrelated variables\\*, we can easily
> separate cats and dogs.
>
> Hiểu, đại khái là trong không gian vector mỗi từ dc
> represented bởi hàng trăm hoặc hàng ngàn feature (tương
> ứng là số dimension của không gian) nhưng reduce xuống
> bằng PCA còn 2 thì plot ra dc để thấy chó với mèo nó gom
> gom lại thành 2 group

<br>

<a id="node-6jnoyze"></a>

<p align="center"><kbd><img src="assets/0hrg8upm76a6.png" width="80%"></kbd></p>

<br>

<a id="node-5swffgf"></a>

## The Rotation Matrix

<br>

<a id="node-gbu3m3b"></a>

<p align="center"><kbd><img src="assets/ig5mxijpzri.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái qua phép tính tính lượng giác có thể hiểu được khái
> niệm **Rotation matrix** là gì - Đại khái là cái **matrix** mà khi **nhân
> với vector** sẽ giúp **xoay vector đó 1 góc beta** (biến thành 1
> vector mới hợp với vector cũ 1 góc beta) Có điều chưa hiểu nó
> liên quan gì với PCA ở lab trước.

<br>

<a id="node-w9xa3bg"></a>

<p align="center"><kbd><img src="assets/o8bry6ly0w.png" width="80%"></kbd></p>

> [!NOTE]
> Hiểu, cạnh góc vuông bằng
> huyền * sin đối cos kề

<br>

<a id="node-q8599yi"></a>

<p align="center"><kbd><img src="assets/eahjgjvpctf.png" width="80%"></kbd></p>

> [!NOTE]
> Này là công thức
> lượng giác thôi.

<br>

<a id="node-y159s0r"></a>

<p align="center"><kbd><img src="assets/30t8aw74got.png" width="80%"></kbd></p>

> [!NOTE]
> Thay thế và khai triển

<br>

<a id="node-eytvksr"></a>

<p align="center"><kbd><img src="assets/uj3txw8rf4.png" width="80%"></kbd></p>

> [!NOTE]
> Đã hiểu rotation matrix

**🔗 See also:** [linked note](#node-dzhaivq)

<br>

<a id="node-pe80x75"></a>

<p align="center"><kbd><img src="assets/tnr2xa3yshn.png" width="80%"></kbd></p>

<br>

<a id="node-4iruphq"></a>

<p align="center"><kbd><img src="assets/b5jxg2520yf.png" width="80%"></kbd></p>

<br>

<a id="node-jco0aoi"></a>

<p align="center"><kbd><img src="assets/fslxfp2tu6w.png" width="80%"></kbd></p>

<br>

<a id="node-gdam624"></a>

<p align="center"><kbd><img src="assets/bkcpnwxj7dt.png" width="80%"></kbd></p>

<br>

<a id="node-px0nqzi"></a>

## Week Conclusion

<br>

<a id="node-fnmzzvs"></a>

> [!NOTE]
> 1 Introduction to \\*vector spaces\\* and \\*representing words as vectors\\*
>
> 2 \\*Comparing words\\* using \\*cosine similarity\\* and \\*Euclidean distance\\*
>
> 3 Programming assignment: \\*manipulating word vectors\\* to 
> \\*find countries from capital cities\\*
>
> 4 \\*Dimensionality reduction\\* of word vectors and \\*clustering similar words\\*
>
> 5 Preview of next week's topic: \\*machine translation\\*

<br>

<a id="node-1y6s3z8"></a>

## Quiz

<br>

<a id="node-ogroh9l"></a>

<p align="center"><kbd><img src="assets/r8f98kzno2.png" width="80%"></kbd></p>

<br>

<a id="node-g0tgnzf"></a>

<p align="center"><kbd><img src="assets/jdfx1pb0rxf.png" width="80%"></kbd></p>

<br>

<a id="node-lblgp2t"></a>

<p align="center"><kbd><img src="assets/11u7ti6w6xv9.png" width="80%"></kbd></p>

<br>

<a id="node-ktfwrnx"></a>

<p align="center"><kbd><img src="assets/48zjw516ln5.png" width="80%"></kbd></p>

<br>

<a id="node-vb7ea9d"></a>

<p align="center"><kbd><img src="assets/57r87tn3r54.png" width="80%"></kbd></p>

<br>

<a id="node-uo05oeg"></a>

<p align="center"><kbd><img src="assets/enh3kxyem6h.png" width="80%"></kbd></p>

<br>

<a id="node-by1yvzx"></a>

<p align="center"><kbd><img src="assets/yarzsz1lyt.png" width="80%"></kbd></p>

<br>

<a id="node-c86l29s"></a>

<p align="center"><kbd><img src="assets/162cusy2il6.png" width="80%"></kbd></p>

<br>

<a id="node-hoqfdse"></a>

<p align="center"><kbd><img src="assets/1ud9xvb7ytk.png" width="80%"></kbd></p>

<br>

<a id="node-z5gzoux"></a>

<p align="center"><kbd><img src="assets/rmzjc6bc2ir.png" width="80%"></kbd></p>

<br>

<a id="node-8bzdsu5"></a>

<p align="center"><kbd><img src="assets/9qqlmmo0tca.png" width="80%"></kbd></p>

<br>

<a id="node-t4jrqcm"></a>

## Programming Assignment: Vector Space Models

> [!NOTE]
> Có một chỗ chưa pass unit test dù vẫn pass assignment 4/5, quay lại sau

<br>

<a id="node-5uz0wk7"></a>

> [!NOTE]
> Welcome to this week's programming assignment of the specialization. In
> this assignment we will explore word vectors. In natural language
> processing, we \\*represent each word as a vector\\* consisting of numbers.
> \\*The vector encodes the meaning of the word\\*. These numbers (or
> weights) for each word \\*are learned using various machine learning
> models\\*, which we will explore in more detail later in this specialization.
> Rather than make you code the machine learning models from scratch,
> we will s\\*how you how to use the\\*m. \\*In the real world, you can always load
> the trained word vectors, and you will almost never have to train them
> from scratch\\*. In this assignment you will
>
> • \\*Predict analogies between words.\\*
>
> • Use \\*PCA\\* to\\* reduce the dimensionality \\*of the \\*word embeddings\\* and plot
> them in two dimensions.
>
> • Compare \\*word embeddings\\* by using a \\*similarity measure\\* (the\\* cosine
> similarity\\*).
>
> • Understand \\*how these vector space models work.\\*

<br>

<a id="node-1f45a9t"></a>

#### 1 - Predict the Countries from Capitals

<br>

<a id="node-el7zo50"></a>

##### 1.1 Importing the Data

<br>

<a id="node-pk3jyzx"></a>

> [!NOTE]
> # Run this cell to import packages.
> import pickle
> import numpy as \\*np\\*
> import pandas as \\*pd\\*
> import matplotlib.pyplot as plt
> import w3_unittest
>
> from utils import \\*get_vectors\\*
>
> As usual, you start by importing some essential Python
> libraries and the load dataset. The dataset will be loaded as
> a Pandas **DataFrame**, which is very a common method in
> data science. Because of the large size of the data, this may
> take a few minutes.

<br>

<a id="node-xqyc1x7"></a>

> [!NOTE]
> data = pd.read_csv('./data/capitals.txt', delimiter=' ')
> data.columns = ['city1', 'country1', 'city2', 'country2']
>
> # print first five elements in the DataFrame
> data.head(5)

<br>

<a id="node-wp7hgki"></a>

<p align="center"><kbd><img src="assets/7nvozi27hxb.png" width="80%"></kbd></p>

<br>

<a id="node-3wds5s9"></a>

> [!NOTE]
> \\*To Run This Code On Your Own Machine:
>
> \\*Note that because the \\*original google news word embedding dataset\\* is about \\*3.64
> gigabytes\\*, the workspace is not able to handle the full file set. So we've downloaded the
> full dataset, \\*extracted a sample of the words\\* that we're going to analyze in this
> assignment, and saved it in a \\*pickle file\\* called \\*word_embeddings_capitals.p\\* If you want
> to download the full dataset on your own and choose your own set of word embeddings,
> please see the instructions and some helper code.
>
> • Download the dataset from this \\_page\\_.
>
> • Search in the page for '\\*GoogleNews-vectors-negative300.bin.gz\\*' and click the link to
> download.
>
> • You'll need to \\*unzip\\* the file.
>
> \\*Copy-paste\\* the code below and run it on your local machine after downloading the
> dataset to the same directory as the notebook.

<br>

<a id="node-owgkjjr"></a>

> [!NOTE]
> import nltk
> from gensim.models import KeyedVectors
>
>
> embeddings = KeyedVectors.load_word2vec_format('./GoogleNews-vectors-negative300.bin', binary = True)
> f = open('capitals.txt', 'r').read()
> set_words = set(nltk.word_tokenize(f))
> select_words = words = ['king', 'queen', 'oil', 'gas', 'happy', 'sad', 'city', 'town', 'village', 'country', 'continent', 'petroleum', 'joyful']
> for w in select_words:
>     set_words.add(w)
>
> def get_word_embeddings(embeddings):
>
>     word_embeddings = {}
>     for word in embeddings.vocab:
>         if word in set_words:
>             word_embeddings[word] = embeddings[word]
>     return word_embeddings
>
>
> # Testing your function
> word_embeddings = get_word_embeddings(embeddings)
> print(len(word_embeddings))
> pickle.dump( word_embeddings, open( "word_embeddings_subset.p", "wb" ) )

<br>

<a id="node-b6m7si1"></a>

> [!NOTE]
> word_embeddings = pickle.load(open("./data/word_embeddings_subset.p", "rb"))
> len(word_embeddings)  # there should be 243 words that will be used in this assignment
>
> -> 243
>
> Now we will load the word embeddings as a Python
> dictionary. As stated, these have already been obtained
> through a machine learning algorithm.

<br>

<a id="node-fuz16lm"></a>

> [!NOTE]
> print("dimension: {}".
> format(word_embeddings['Spain'].
> shape[0]))
>
> ->dimension: 300
>
> Each of the word embedding is a
> 300-dimensional vector.

<br>

<a id="node-r08nja0"></a>

> [!NOTE]
> \\*Predict relationships among words
>
> \\*Now you will write a function that will \\*use the word embeddings\\* to \\*predict relationships\\* among words.
>
>  • The function will take as \\*input\\* \\*three words.\\*
>
>  • The \\*first two are related to each other.\\*
>
>  • It will \\*predict a 4th word\\* which is \\*related to the third word\\* in a \\*similar manner as the two first words\\* are related to each other.
>
>  • As an example, "Athens is to Greece as Bangkok is to \\*__\\*"?
>
>  • You will write a program that is capable of \\*finding the fourth word.\\*
>
>  • We will give you a hint to show you how to compute this.
>
> A similar analogy would be the following:

<br>

<a id="node-fhqrc7u"></a>

<p align="center"><kbd><img src="assets/gzf5lfzqfvs.png" width="80%"></kbd></p>

> [!NOTE]
> You will implement a function that can tell you the capital of a
> country. You should use the same methodology shown in the
> figure above. To do this, you'll first compute the **cosine similarity
> metric** or the **Euclidean distance**.

<br>

<a id="node-nvp5tgh"></a>

##### 1.2 Cosine Similarity

<br>

<a id="node-32oy15d"></a>

<p align="center"><kbd><img src="assets/df9brxix8kb.png" width="80%"></kbd></p>

<br>

<a id="node-s4dqie4"></a>

##### Exercise 1 - cosine_similarity (UNQ_C1)

<br>

<a id="node-v396bu9"></a>

<p align="center"><kbd><img src="assets/4b0q9zpu9i.png" width="80%"></kbd></p>

<br>

<a id="node-eurzv78"></a>

<p align="center"><kbd><img src="assets/4hrtgg2dk3t.png" width="80%"></kbd></p>

<br>

<a id="node-tzcsasi"></a>

##### 1.3 Euclidean Distance

<br>

<a id="node-96raznh"></a>

<p align="center"><kbd><img src="assets/lmqr3t2mra.png" width="80%"></kbd></p>

<br>

<a id="node-jrcxv8l"></a>

##### Exercise 2 - euclidean (UNQ_C2)

<br>

<a id="node-kwzootq"></a>

<p align="center"><kbd><img src="assets/gch9kzlbgq4.png" width="80%"></kbd></p>

<br>

<a id="node-sqhpqy4"></a>

<p align="center"><kbd><img src="assets/t0on0rt2i2.png" width="80%"></kbd></p>

<br>

<a id="node-c2rhh51"></a>

##### 1.4 Finding the Country of each Capital

<br>

<a id="node-jhpom1i"></a>

> [!NOTE]
> Now, you will use the previous functions to compute \\*similarities
> between vectors\\*, and use these to find the \\*capital cities of
> countries\\*. You will write a function that takes in three words, and the
> embeddings dictionary. Your task is to find the capital cities. For
> example, given the following words:
>
> • 1: Athens 2: Greece 3: Baghdad,
>
> your task is to predict the country 4: Iraq.

<br>

<a id="node-m3m8nyw"></a>

##### Exercise 3 - get_country (UNQ_C3)

<br>

<a id="node-l0vwvep"></a>

> [!NOTE]
> \\*Instructions\\*:
>
> 1 To predict the capital you might want to look at the \\/King - Man +
> Woman = Queen\\/ example above, and implement that scheme into a
> mathematical function, using the word embeddings and a similarity
> function.
>
> 2 \\*Iterate over the embeddings dictionar\\*y and compute the \\*cosine
> similarity score\\* between \\*your vector\\* and the \\*current word embedding\\*.
>
> 3 You should a\\*dd a check\\* to make sure that the word you return is not
> any of the words that you fed into your function. \\*Return the one with the
> highest score.\\*

<br>

<a id="node-drer4bt"></a>

<p align="center"><kbd><img src="assets/2vvw0dht5n2.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/e9rsqrf40vr.png" width="80%"></kbd></p>

> [!NOTE]
> Đại khái là với cái input city 1, country 1, country 2 (là tên) ta chuyển
> nó thành embedding vector nhờ cái embedding dictionary. Sau đó,
> dựa vào quan hệ giữa vector khái niệm Nước - Thủ đô với country 2
> ta predict embedding vector của city 2. Loop trong dataset, xem thử
> cái nào là cái gần nhất (dùng Cosine similarity) với cái predict vector

<br>

<a id="node-hcpm0d6"></a>

<p align="center"><kbd><img src="assets/f5ok8izan8h.png" width="80%"></kbd></p>

<br>

<a id="node-8nsw6pv"></a>

##### 1.5 Model Accuracy

<br>

<a id="node-0251ncg"></a>

<p align="center"><kbd><img src="assets/17tt8amo7oe.png" width="80%"></kbd></p>

<br>

<a id="node-om78f8e"></a>

##### Exercise 4 - get_accuracy (UNQ_C4)

<br>

<a id="node-txf00zx"></a>

<p align="center"><kbd><img src="assets/urxncge3ql.png" width="80%"></kbd></p>

> [!NOTE]
> Không có gì khó, chỉ đơn giản là loop qua các row của dataset, lấy ra
> cái country1, city1, country2 rồi predict cái thủ đô city2: Để rồi xem nó
> có đúng bằng cái city2 trong dataset không. Đúng thì +1. Xong hết chia
> tổng số correct cho tổng số hàng để ra. Accuracy percent

<br>

<a id="node-l8pl5wv"></a>

<p align="center"><kbd><img src="assets/fd1k072da8u.png" width="80%"></kbd></p>

<br>

<a id="node-703q2x3"></a>

#### 2 - Plotting the vectors using PCA

<br>

<a id="node-x4xyjfw"></a>

> [!NOTE]
> Now you will \\*explore the distance\\* between \\*word vectors\\* after \\*reducing their
> dimension\\*. The technique we will employ is known as \\*principal component
> analysis (PCA)\\*. As we saw, we are working in a \\*300-dimensional space\\* in this
> case. Although from a computational perspective we were able to perform a good
> job, it is\\* impossible to visualize results\\* in such high dimensional spaces.
>
> You can think of PCA as a method that \\*projects our vectors in a space of reduced
> dimension\\*, while \\*keeping the maximum information\\* about the original vectors in
> their reduced counterparts. In this case, \\*by maximum informatio\\*n we mean that the
> \\*Euclidean distance between the original vectors and their projected siblings is
> minima\\*l. Hence vectors that were originally close in the embeddings dictionary, will
> produce \\*lower dimensional vectors \\*that are \\*still close to each other\\*.
>
> You will see that when you map out the words,\\* similar words\\* will be \\*clustered\\* next
> to each other. For example, the words 'sad', ' happy', 'joyful' all describe emotion
> and are supposed to be near each other when plotted. The words: ' oil', 'gas', and '
> petroleum' all describe natural resources. Words like 'city', ' village', 'town' could
> be seen as synonyms and describe a similar thing.

<br>

<a id="node-kmr5b1e"></a>

> [!NOTE]
> Before plotting the words, you need to first be able to \\*reduce each word
> vector with PCA into 2 dimensions\\* and then plot it. The steps to
> compute PCA are as follows:
>
> 1 \\*Mean normalize\\* the data
>
> 2 \\*Compute the covariance matrix\\* of your data (Σ).
>
> 3 \\*Compute the eigenvectors\\* and the\\* eigenvalues of your covariance
> matrix\\*
>
> 4 Multiply the \\*first K eigenvectors\\* by \\*your normalized data\\*. The
> transformation should look something as follows:

<br>

<a id="node-qsd02jo"></a>

<p align="center"><kbd><img src="assets/kor1a5ekfto.png" width="80%"></kbd></p>

<br>

<a id="node-5e9dp5z"></a>

#### Exercise 5 - compute_pca (UNQ_C5)

<br>

<a id="node-c72x6d2"></a>

> [!NOTE]
> \\*Instructions\\*:
>
> Implement a program that takes in a data set where each row corresponds to a word vector.
>
> • The \\*word vectors are of dimension 300\\*.
>
> • Use \\*PCA\\* to change the 300 dimensions to \\*n_components\\* dimensions.
>
> • The new matrix should be of dimension \\*m, n_componentns.\\*
>
> • First \\*de-mean\\* the data
>
> • Get the \\*eigenvalues\\* using\\* linalg.eigh\\*. Use '\\*eigh\\*' rather than '\\*eig\\*' since R is symmetric. The
> performance gain when using \\*eigh\\* instead of \\*eig\\* is substantial.
>
> • \\*Sort the eigenvectors and eigenvalues by decreasing order of the eigenvalues.
>
> \\*• Get a subset of the \\*eigenvectors\\* (choose how \\*many principle components\\* you want to use
> using \\*n_components\\*).
>
> • Return the new transformation of the data by \\*multiplying the eigenvectors\\* with the \\*original data.\\*

<br>

<a id="node-ejwbp8m"></a>

> [!NOTE]
> Use \\*numpy.mean(a,axis=None)\\* which takes one required parameter. You need to specify the optional argument
> axis for this exercise: If you set axis = 0, you take the mean for each column. If you set axis = 1, you take the mean
> for each row. Remember that each row is a word vector, and the number of columns are the number of dimensions
> in a word vector.
>
> Use \\*numpy.cov(m, rowvar=True)\\* which takes one required parameter. You need to specify the optional argument
> rowvar for this exercise. This calculates the covariance matrix. By default \\*rowvar\\* is True. From the
> documentation: "If rowvar is True (default), then each row represents a variable, with observations in the columns."
> In our case, each row is a word vector observation, and each column is a feature (variable).
>
> Use \\*numpy.linalg.eigh(a, UPLO='L')\\*
>
> Use\\* numpy.argsort\\* sorts the values in an array from smallest to largest, then returns the indices from this sort.
>
> In order to reverse the order of a list, you can use: \\*x[::-1].\\*
>
> To apply the sorted indices to eigenvalues, you can use this format \\*x[indices_sorted].\\*
>
> When applying the sorted indices to \\*eigen\\* vectors, note that each column represents an eigenvector. In order to
> preserve the rows but sort on the columns, you can use this format \\*x[:,indices_sorted] \\* To transform the data
> using a subset of the most relevant principle components, take the matrix multiplication of the eigenvectors with the
> original data.
>
> The data is of shape \\*(n_observations, n_features).\\*
>
> The subset of eigenvectors are in a matrix of shape \\*(n_features, n_components)\\*.
>
> To multiply these together, take the transposes of both the eigenvectors \\*(n_components, n_features) \\*and the data
> (n_features, n_observations).
>
> The product of these two has dimensions\\* (n_components,n_observations)\\*. Take its transpose to get the shape
> \\*(n_observations, n_components).\\*

<br>

<a id="node-w62t1uo"></a>

<p align="center"><kbd><img src="assets/g99sh8lfdkr.png" width="80%"></kbd></p>

> [!NOTE]
> Vẫn sai chỗ nào mà pass 2/4 unit
> test. Quay lại kiểm tra sau
>
> Có nhiều cái mới biết:
>
>
>
> - demean,
>
>
>
> - tính covariance matrix bằng np.cov(..,rowVar),
>
>
>
> - tính Eigenvectors và Eigenvalues bởi np.linalg.
> eigh(cov_matrix, UPLO='L' ),
>
>
>
> - sort bằng np.argsort(),

<br>

<a id="node-ypl907k"></a>

<p align="center"><kbd><img src="assets/kujy45zzff.png" width="80%"></kbd></p>

<br>

<a id="node-sienj9d"></a>

<p align="center"><kbd><img src="assets/ovjmpurj9b.png" width="80%"></kbd></p>

> [!NOTE]
> What do you notice?
>
>
>
> The word vectors for gas, oil and petroleum appear related to
> each other, because their vectors are close to each other.
> Similarly, sad, joyful and happy all express emotions, and are
> also near each other.

<br>

