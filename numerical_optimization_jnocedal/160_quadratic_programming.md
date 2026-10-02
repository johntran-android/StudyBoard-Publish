# 16.0 Quadratic Programming

📊 **Progress:** `1` Notes | `2` Screenshots

---
<a id="node-sfegulm"></a>

<br>

<a id="node-2xunn6m"></a>

## Quadratic Programming Definition

<p align="center"><kbd><img src="assets/tv5of7bt08q.png" width="80%"></kbd></p>

<p align="center"><kbd><img src="assets/cpmm1bg1aq.png" width="80%"></kbd></p>

> [!NOTE]
> Rồi, chương 16 là nói về quadratic programming. Thì đại ý, bài toán này là một cái bài toán tối ưu mà cái hàm objective, tức là hàm mục tiêu, nó là hàm bậc hai. Còn những cái ràng buộc là hàm tuyến tính, kể cả là ràng buộc bất đẳng thức hay là ràng buộc đẳng thức. Và đây là một cái bài toán khá là quan trọng, rất là quan trọng. Tác giả cho biết là nó quan trọng với tư cách là một bài toán riêng lẻ hoặc là nó đóng vai trò là một cái bài toán phụ trong những cái thuật toán khác, những thuật toán mà tối ưu ràng buộc khác. Ví dụ như là sequential quadratic programming, hay là augmented Lagrangian method, hay là interior-point method. 
>
>
>
> Tác giả mới cho mình xem cái dạng của một cái bài toán quadratic programming là như thế nào. 
>
>
>
> Thì mình thấy ở cái 16.1a đó, thì hàm mục tiêu của nó là một cái hàm bậc hai, đúng không? Với cái ma trận Hessian là ma trận G, và các cái ràng buộc nó đều là những hàm tuyến tính
>
>
>
> Thế thì tác giả cũng cho biết đó là cái quadratic program, tạm hiểu là có thể được giải với một cái số lượng hữu hạn các phép tính. Tuy nhiên, cái chuyện mà chi phí để mà giải bài toán này nó nhiều hay ít nó còn phụ thuộc vào cái đặc điểm của cái hàm mục tiêu cũng như là số lượng những cái bất đẳng thức, những cái ràng buộc bất đẳng thức. Nói thêm là nếu như mà cái ma trận Hessian, ma trận G mà nó có tính chất là bán xác định dương đó, thì khi này mình sẽ có được một cái gọi là convex quadratic programming. Và cái chi phí tính toán của bài toán này, cái độ khó đó, nó sẽ tương đương như một cái bài toán linear program.
>
>
>
> Còn nếu không, nếu như mà ma trận Hessian nó là ma trận không xác định, indefinite á, thì cái bài toán nó trở nên khó hơn. Thì trong chương này là mình phần lớn sẽ tập trung chủ yếu vào cái bài toán convex quadratic program.

<br>

