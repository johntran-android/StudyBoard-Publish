# 4.3.6 Canonical link function

📊 **Progress:** `1` Notes | `2` Screenshots | `1` AI Reviews

---
<a id="node-vnbkj4t"></a>

<br>

<a id="node-tn8x82z"></a>

## Section 4.3.6 Canonical Link Functions

<p align="center"><kbd><img src="assets/kudq7d2wnd.png" width="80%"></kbd></p>

> [!NOTE]
> Mở đầu, đại ý là, phần này tác giả sẽ chỉ cho ta thấy rằng cái pattern mà ta thấy xuất hiện nhiều lần trước đây:
>
>
>
> đạo hàm của hàm log likelihood (đối với 𝐰), đều có dạng là tổ hợp tuyến tính của của các feature vector
>
>
>
> Và lí do là, đây là kết qủa của việc ta giả định conditional distribution của target variable (tức T|𝐱, hay T|Φ) theo exponential family với activation function là hàm canonical link function

> [!TIP]
> 🤖 **AI Check** — 🟢 Pass — ✅ **95/100** · ✓ Move on
>
> Ghi chú nắm rất chuẩn và súc tích thông điệp mở đầu của mục 4.3.6: giải thích nguồn gốc dạng gradient đặc trưng (sai số nhân vector đặc trưng) thông qua họ phân phối mũ và hàm liên kết chính tắc (canonical link function).
>
> **✓ Strengths**
> - Khái quát hóa chính xác cấu trúc gradient chung cho Linear Regression, Logistic Regression và Softmax khi dùng negative log-likelihood.
> - Nắm đúng hai điều kiện cốt lõi tạo nên tính chất này: phân phối điều kiện thuộc họ exponential family và hàm kích hoạt được chọn là canonical link function.
>
> **💡 Deeper notes**
> - Sách gốc sử dụng negative log-likelihood (hàm mất mát), do đó gradient đóng góp từ điểm dữ liệu $n$ có dạng $(y_n - t_n)oldsymbol{\phi}_n$. Nếu lấy đạo hàm trực tiếp của log-likelihood thì dấu sẽ ngược lại là $(t_n - y_n)oldsymbol{\phi}_n$.
> - Về mặt thuật ngữ thống kê tổng quát (GLM), hàm kích hoạt (activation function) thực chất là hàm liên kết nghịch đảo (inverse link function), ánh xạ từ tổ hợp tuyến tính $a = \mathbf{w}^T \boldsymbol{\phi}$ sang kỳ vọng của biến mục tiêu.

**🔗 See also:** [Maximum Likelihood and Gradient](./311_maximum_likelihood_and_least_squares.md#node-ogc31vz) · [Gradient of Softmax Error Function](./434_multiclass_logistic_regression.md#node-8j52rv4) · [Gradient of Logistic Error Function](./432_logistic_regression.md#node-to86xxj)

<br>

<a id="node-tp0pbj6"></a>

### Conditional Mean in Exponential Family

<p align="center"><kbd><img src="assets/eggki7qvnjc.png" width="80%"></kbd></p>

**🔗 See also:** [2.4.1 Maximum likelihood & sufficient statistic](./241_maximum_likelihood_sufficient_statistic.md#node-niekuox)

<br>

