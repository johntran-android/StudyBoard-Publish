# Tóm tắt về repo này

Khoảng 3 năm trước mình bắt đầu học AI với các khóa của Andrew Ng trên Coursera như Machine Learning, Deep Learning và NLP Specialization. Sau đó, nhờ đọc blog của Huyền Chip, mình tiếp tục với CS231N và CS224N của Stanford và tự làm các assignment.

Trong quá trình đó mình nhận ra một điều: **làm được assignment không đồng nghĩa với việc thật sự hiểu những gì đang diễn ra bên dưới**. Có những lúc gặp một câu hỏi lý thuyết mà ngay cả câu hỏi đang hỏi gì mình cũng chưa hiểu rõ.

Từ đó mình quyết định quay lại học nền tảng bài bản hơn.

Về calculus, mình học MIT 18.01, 18.02 và 18.S096. Linear algebra là MIT 18.06 của giáo sư Gilbert Strang. Probability là Harvard Stat110 của giáo sư Joe Blitzstein. Sau đó mình tiếp tục với Statistical Inference của Casella & Berger, Convex Optimization của Boyd, Numerical Optimization của Nocedal & Wright, và hiện tại là Pattern Recognition and Machine Learning của Christopher Bishop.

Ý tưởng chung của lộ trình này là đi từ các lớp nền về **calculus, linear algebra, probability, statistics và optimization**, rồi mới dần tiến lên các tầng machine learning phía trên.

## Cách mình học

Từ đầu mình chủ yếu học theo một Feynman loop khá đơn giản:

**Đọc/xem → dừng lại → tự giải thích theo cách hiểu của mình → kiểm tra lại → sửa nếu cần → học tiếp.**

Trước đây mình dùng SimpleMind để quản lý các ghi chú vì thích cách mind map/canvas cho phép nhìn kiến thức như một bảng lớn với các ý liên kết với nhau, thay vì một chuỗi note tuyến tính.

Các note trong repo này vì vậy không phải sách, giáo trình hay tài liệu được viết với mục tiêu thay thế nguồn gốc. Chúng đơn giản là những ghi chú mình tích lũy trong quá trình học, bao gồm cách mình diễn giải lại kiến thức theo cách hiểu của mình tại thời điểm đó.

## StudyBoard

Bên cạnh việc học AI, background của mình vốn là kĩ sư xây dựng chuyển hướng app development vì thích làm sản phẩm công nghệ. Mình đã tự build, ship và duy trì các sản phẩm thực tế trong nhiều năm; một trong những app mình từng phát triển là [**Sentence Master**](https://play.google.com/store/apps/details?id=com.hungdaovuong.sentencemaster.en).

Kinh nghiệm làm sản phẩm đó cũng là một phần nền để mình bắt đầu build [**StudyBoard**](https://studyboard.app/landing.html) từ đầu năm nay, xoay quanh chính workflow học ở trên.

Mục tiêu ban đầu khá thực dụng: làm cho Feynman loop thuận tiện hơn — quản lý note trên canvas, viết toán dễ hơn, dùng AI để kiểm tra cách hiểu, đánh dấu những chỗ cần quay lại, và hỗ trợ việc **learning in public**.

Repo GitHub này cũng là một sản phẩm của workflow đó: StudyBoard có thể đưa các notebook và ghi chú mình đang học lên GitHub để lưu trữ và chia sẻ.

StudyBoard hiện tại được phát triển theo kiểu **dogfooding**: mình dùng chính nó để học mỗi ngày. Những bất tiện gặp phải trong quá trình học trở thành vấn đề cần giải quyết trong sản phẩm; ngược lại, những kiến thức AI/ML mình học được cũng dần được áp dụng trở lại để cải thiện StudyBoard.

Nói cách khác, ngoài Feynman loop trong việc học còn có thêm một vòng lặp khác:

**học → dùng StudyBoard → gặp vấn đề → cải thiện StudyBoard → áp kiến thức mới vào sản phẩm → quay lại học tốt hơn.**

## Tiếp theo

Các môn như MIT 18.06, Stat110, Casella, Nocedal và Bishop đối với mình chủ yếu vẫn là tầng nền.

Hướng tiếp theo là tiếp tục đi lên các lớp ML ở tầng cao hơn như CS229 và các chủ đề về AI/ML engineering, trong khi vẫn phát triển StudyBoard song song và dần đưa những kiến thức đã học vào một sản phẩm thực tế.

Repository này vì vậy chủ yếu là một **learning log** — dấu vết của quá trình đi từ nền tảng toán, probability, statistics và optimization lên machine learning, đồng thời là một phần của quá trình build StudyBoard..

**`~12,391 notes` · `~17,915 screenshots` · `18 notebooks`**

<!-- studyboard-toc:start -->
<a id="top-nav"></a>
### 🗺️ Quick Navigation

| Group | Notebooks |
|:---|:---|
| [📂 **Calculus**](#group-calculus) | [MIT 18.01 — Single Variable Calculus](#nb-a0_mit1801)<br>[MIT 18.02](#nb-mit_1802)<br>[MIT 18S096 Matrix Calculus for ML](#nb-mit_18s096_matrix_calculus_for_ml) |
| [📂 **Linear Algebra**](#group-linear-algebra) | [EE263A — Linear Dynamical Systems](#nb-ee263a)<br>[MIT 18.06 Book](#nb-mit_1806_book)<br>[MIT 18.06](#nb-mit1806_gstrang) |
| [📂 **Machine Learning & Deep Learning**](#group-machine-learning-deep-learning) | [CS224N_Stanford](#nb-cs224n_stanford)<br>[CS231N_Stanford](#nb-cs231n_stanford)<br>[DL Spec Coursera](#nb-dl_spec_coursera)<br>[NLP Spec Coursera](#nb-nlp_spec_coursera) |
| [📂 **Optimization**](#group-optimization) | [EE364a, Convex Optim_S.Boyd](#nb-ee364a_convex_optim_sboyd)<br>[Numerical Optimization_J.Nocedal](#nb-numerical_optimization_jnocedal) |
| [📂 **Machine Learning Foundation**](#group-machine-learning-foundation) | [Pattern Recognition Machine Learning_C.Bishop](#nb-pattern_recognition_machine_learning_cbishop) |
| [📂 **Probability & Statistics**](#group-probability-statistics) | [STAT110_Havard](#nb-stat110_havard)<br>[Statistical Inference - Casella](#nb-statistical_inference_casella) |
| [📂 **Other**](#group-other) | [LLM — Large Language Models](#nb-a1_llm)<br>[Deep Learning Specialization_Cousera_Andrew Ng](#nb-deep_learning_specialization_cousera_andrew_ng)<br>[Foundation of LLM](#nb-foundation_of_llm) |

🎬 [Xem Video Library ↓](#video-library)

🗺️ [Xem Video Roadmap ↓](#video-roadmap)

<!-- studyboard-toc:end -->

## 📚 Syllabus / Mục lục

<a id="group-calculus"></a>
### 📂 Calculus

<a id="nb-a0_mit1801"></a>
### MIT 18.01 — Single Variable Calculus
<!-- key: a0_mit1801 -->
<!-- group: Calculus -->
`317 notes · 331 screenshots · 12 sections`

> A comprehensive set of study notes for MIT 18.01 Single Variable Calculus, covering core topics from limits and derivatives to practical applications such as optimization, curve sketching, and approximation methods.
> Tập hợp chi tiết các ghi chép học tập cho khóa học Giải tích một biến MIT 18.01, bao gồm các chủ đề cốt lõi từ giới hạn, đạo hàm cho đến các ứng dụng thực tế như tối ưu hóa, khảo sát hàm số và các phương pháp xấp xỉ.

<details open>
<summary>📖 12 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [Lec 10: Curve Sketching](a0_mit1801/lec_10_curve_sketching.md) | 28 | 29 |
| [Lec 11: Max-min](a0_mit1801/lec_11_max_min.md) | 29 | 30 |
| [Lec 12: Related Rates](a0_mit1801/lec_12_related_rates.md) | 24 | 25 |
| [Lec 13: Newton's Method](a0_mit1801/lec_13_newtons_method.md) | 26 | 28 |
| [Lec 14: Mean](a0_mit1801/lec_14_mean_value_theorem.md) | 24 | 24 |
| [Lec 1: Rate Of Change](a0_mit1801/lec_1_rate_of_change.md) | 24 | 26 |
| [Lec 2: Limits](a0_mit1801/lec_2_limits.md) | 28 | 30 |
| [Lec 3: Derivatives](a0_mit1801/lec_3_derivatives.md) | 21 | 22 |
| [Lec 4: Chain Rule](a0_mit1801/lec_4_chain_rule.md) | 21 | 22 |
| [Lec 5: Implicit](a0_mit1801/lec_5_implicit_differentiaion.md) | 29 | 30 |
| [Lec 6: Exponential &](a0_mit1801/lec_6_exponential_log.md) | 36 | 37 |
| [Lec 9: Linear And Quadratic](a0_mit1801/lec_9_linear_and_quadratic_approximations.md) | 27 | 28 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-mit_1802"></a>
### MIT 18.02
<!-- key: mit_1802 -->
<!-- group: Calculus -->
`549 notes · 615 screenshots · 22 sections`

> This notebook contains study notes for MIT 18.02 (Multivariable Calculus), covering core topics such as vector algebra, matrices, partial derivatives, Lagrange multipliers, and double integrals.
> Vở ghi chép này tổng hợp các kiến thức môn Giải tích đa biến (MIT 18.02), bao gồm các chủ đề cốt lõi như đại số vector, ma trận, đạo hàm riêng, phương pháp nhân tử Lagrange và tích phân kép.

<details open>
<summary>📖 22 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [Lec 10: Second Derivative Test,](mit_1802/lec_10_second_derivative_test_boudaries_infinity.md) | 23 | 24 |
| [Lec 11: Differentials, Chain-rule](mit_1802/lec_11_differentials_chain_rule.md) | 20 | 21 |
| [Lec 12: Gradient, Directional](mit_1802/lec_12_gradient_directional_derivative_tangent_plane.md) | 30 | 37 |
| [Lec 13: Lagrange Multiplier](mit_1802/lec_13_lagrange_multiplier.md) | 33 | 36 |
| [Lec 14: Non-independent Random](mit_1802/lec_14_non_independent_random_variables.md) | 32 | 35 |
| [Lec 15: Partial Differentials Equations](mit_1802/lec_15_partial_differentials_equations.md) | 18 | 19 |
| [Lec 16: Double Integrals](mit_1802/lec_16_double_integrals.md) | 35 | 37 |
| [Lec 17: Double Integrals In](mit_1802/lec_17_double_integrals_in_polar_coordinates.md) | 21 | 21 |
| [Lec 18: Change Of Variables](mit_1802/lec_18_change_of_variables.md) | 33 | 36 |
| [Lec 19: Vector Fields](mit_1802/lec_19_vector_fields.md) | 36 | 44 |
| [Lec 1: Dot Products](mit_1802/lec_1_dot_products.md) | 0 | 4 |
| [Lec 20: Path Independence & Conservative Field](mit_1802/lec_20_path_independence_conservative_field.md) | 38 | 43 |
| [Lec 21: Gradient Field & Potential Function](mit_1802/lec_21_gradient_field_potential_function.md) | 35 | 35 |
| [Lec 22: Green's Theorem](mit_1802/lec_22_greens_theorem.md) | 26 | 29 |
| [Lec 2: Determinant, Cross Product](mit_1802/lec_2_determinant_cross_product.md) | 16 | 21 |
| [Lec 3: Matrix, Inverse Matrix](mit_1802/lec_3_matrix_inverse_matrix.md) | 26 | 31 |
| [Lec 4: Square System, Equation](mit_1802/lec_4_square_system_equation_of_plane.md) | 20 | 23 |
| [Lec 5: Parametric Equations For](mit_1802/lec_5_parametric_equations_for_lines_and_curves.md) | 23 | 24 |
| [Lec 6: Velocity, Acceleration,](mit_1802/lec_6_velocity_acceleration_keplers_second_law.md) | 27 | 28 |
| [Lec 7: Review](mit_1802/lec_7_review.md) | 16 | 17 |
| [Lec 8: Level Curves, Partial](mit_1802/lec_8_level_curves_partial_derivatives_tangent_plane.md) | 20 | 22 |
| [Lec 9: Max-min Problems, Least](mit_1802/lec_9_max_min_problems_least_squares.md) | 21 | 28 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-mit_18s096_matrix_calculus_for_ml"></a>
### MIT 18S096 Matrix Calculus for ML
<!-- key: mit_18s096_matrix_calculus_for_ml -->
<!-- group: Calculus -->
`210 notes · 221 screenshots · 19 sections`

> This notebook contains study notes and problem sets for MIT 18.S096 (Matrix Calculus for Machine Learning), covering core topics such as multidimensional derivatives, automatic differentiation, optimization, and computational graphs.
> Sổ tay ghi chép này tổng hợp bài học và bài tập từ khóa học MIT 18.S096 (Giải tích Ma trận cho Học máy), bao gồm các chủ đề cốt lõi như đạo hàm đa chiều, đạo hàm tự động, tối ưu hóa và đồ thị tính toán.

<details open>
<summary>📖 19 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [Lec 1 Part 1 Intro And Motivation](mit_18s096_matrix_calculus_for_ml/lec_1_part_1_intro_and_motivation.md) | 19 | 17 |
| [Lec 1 Part 2 Derivatives As Linear Operator](mit_18s096_matrix_calculus_for_ml/lec_1_part_2_derivatives_as_linear_operator.md) | 12 | 13 |
| [Lec 2 Part 1: Derivatives In Higher Dimensions: Jacobians And Matrix Functions](mit_18s096_matrix_calculus_for_ml/lec_2_part_1_derivatives_in_higher_dimensions_jacobians_and_matrix_functions.md) | 20 | 20 |
| [Lec 2 Part 2: Vectorization Of Matrix Function](mit_18s096_matrix_calculus_for_ml/lec_2_part_2_vectorization_of_matrix_function.md) | 3 | 3 |
| [Lec 3 Part 1 Kronecker Products And Jacobians](mit_18s096_matrix_calculus_for_ml/lec_3_part_1_kronecker_products_and_jacobians.md) | 24 | 26 |
| [Lec 3 Part 2 Finite-difference Approximations](mit_18s096_matrix_calculus_for_ml/lec_3_part_2_finite_difference_approximations.md) | 23 | 24 |
| [Lec 4 Part 1: Gradient And Inner Products In Other Vector Spaces](mit_18s096_matrix_calculus_for_ml/lec_4_part_1_gradient_and_inner_products_in_other_vector_spaces.md) | 18 | 16 |
| [Lec 4 Part 2: Nonlinear Rooting Finding, Optimization And Adjoint Gradient Methods](mit_18s096_matrix_calculus_for_ml/lec_4_part_2_nonlinear_rooting_finding_optimization_and_adjoint_gradient_methods.md) | 15 | 17 |
| [Lec 5 P1: Derivative Of Matrix Determinant And Invers](mit_18s096_matrix_calculus_for_ml/lec_5_p1_derivative_of_matrix_determinant_and_invers.md) | 7 | 6 |
| [Lec 5 P2: Forward Automatic Differentiation Via Dua Numbers](mit_18s096_matrix_calculus_for_ml/lec_5_p2_forward_automatic_differentiation_via_dua_numbers.md) | 22 | 23 |
| [Lec 5 P3 Differentiation On Computational Graphs](mit_18s096_matrix_calculus_for_ml/lec_5_p3_differentiation_on_computational_graphs.md) | 1 | 0 |
| [Lec 6 P1: Adjoint Differentiation On ODE Solutions](mit_18s096_matrix_calculus_for_ml/lec_6_p1_adjoint_differentiation_on_ode_solutions.md) | 1 | 0 |
| [Lec 6 P2: Calculus Of Variations & Gradient Of Functionals](mit_18s096_matrix_calculus_for_ml/lec_6_p2_calculus_of_variations_gradient_of_functionals.md) | 1 | 0 |
| [Lec 7 P1: Derivative Of Random Functions](mit_18s096_matrix_calculus_for_ml/lec_7_p1_derivative_of_random_functions.md) | 18 | 19 |
| [Lec 7 P2: Second Derivatives, Bilinear Form, Hessian](mit_18s096_matrix_calculus_for_ml/lec_7_p2_second_derivatives_bilinear_form_hessian.md) | 23 | 22 |
| [Lecture Note](mit_18s096_matrix_calculus_for_ml/lecture_note.md) | 2 | 4 |
| [Lec 8 P2: Automatic Differentiation On Computational Graph](mit_18s096_matrix_calculus_for_ml/lec_8_p2_automatic_differentiation_on_computational_graph.md) | 1 | 0 |
| [Problem Sets 1](mit_18s096_matrix_calculus_for_ml/problem_sets_1.md) | 0 | 3 |
| [Problem Sets 2](mit_18s096_matrix_calculus_for_ml/problem_sets_2.md) | 0 | 8 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="group-linear-algebra"></a>
### 📂 Linear Algebra

<a id="nb-ee263a"></a>
### EE263A — Linear Dynamical Systems
<!-- key: ee263a -->
<!-- group: Linear Algebra -->
`77 notes · 113 screenshots · 12 sections`

> This notebook delves into fundamental linear algebra concepts such as Gram-Schmidt orthogonalization, matrix inverses, and linear independence. It extensively covers the Least Squares problem, exploring its geometric interpretation, solution methods (including QR factorization and the normal equation), and applications in data fitting and regression, while also considering computational complexity.

<details open>
<summary>📖 12 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [10.1 Matrix matrix multiplication](ee263a/101_matrix_matrix_multiplication.md) | 4 | 5 |
| [11.1 Left Right Inverse](ee263a/111_left_right_inverse.md) | 6 | 7 |
| [11.2 Inverse](ee263a/112_inverse.md) | 9 | 9 |
| [11.3 Solving linear equation](ee263a/113_solving_linear_equation.md) | 5 | 6 |
| [11.5 Pseudo inverse](ee263a/115_pseudo_inverse.md) | 7 | 9 |
| [13.0 Least squares problem](ee263a/130_least_squares_problem.md) | 15 | 24 |
| [13.1 Least squares data fitting](ee263a/131_least_squares_data_fitting.md) | 14 | 20 |
| [1.5 Complexity of vector](ee263a/15_complexity_of_vector_computations.md) | 4 | 6 |
| [5.1 Linear Independent](ee263a/51_linear_independent.md) | 5 | 6 |
| [5.2 Basis](ee263a/52_basis.md) | 2 | 4 |
| [5.3 Orthonormal vectors](ee263a/53_orthonormal_vectors.md) | 4 | 5 |
| [5.4 Gram-Smidth algorithm](ee263a/54_gram_smidth_algorithm.md) | 2 | 12 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-mit_1806_book"></a>
### MIT 18.06 Book
<!-- key: mit_1806_book -->
<!-- group: Linear Algebra -->
`106 notes · 139 screenshots · 13 sections`

> A comprehensive compilation of study notes and solved problems for MIT 18.06 Linear Algebra, focusing on the four fundamental subspaces, matrix diagonalisation, singular value decomposition (SVD), and linear transformations.
> Tài liệu tổng hợp ghi chép lý thuyết và bài tập giải chi tiết môn Đại số Tuyến tính MIT 18.06, tập trung vào bốn không gian con cơ bản, chéo hóa ma trận, phân tích kỳ dị (SVD) và biến đổi tuyến tính.

<details open>
<summary>📖 13 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](mit_1806_book/_overview.md) | 0 | 1 |
| [6.2 Diagonalizing A Matrix](mit_1806_book/62_diagonalizing_a_matrix.md) | 17 | 22 |
| [6.3 System Of Differential Equations](mit_1806_book/63_system_of_differential_equations.md) | 3 | 6 |
| [6.4 Symmetric Matrices](mit_1806_book/64_symmetric_matrices.md) | 3 | 4 |
| [7.2 Basis And Matrices In Svd](mit_1806_book/72_basis_and_matrices_in_svd.md) | 3 | 6 |
| [7.3 Pca By Svd](mit_1806_book/73_pca_by_svd.md) | 4 | 7 |
| [7.4 Geometry Of Svd](mit_1806_book/74_geometry_of_svd.md) | 17 | 19 |
| [8.1 Idea Of A Linear Transformation](mit_1806_book/81_idea_of_a_linear_transformation.md) | 17 | 20 |
| [8.2 The Matrix Of Linear Transformation](mit_1806_book/82_the_matrix_of_linear_transformation.md) | 20 | 23 |
| [8.3 In Search Of Good Basis](mit_1806_book/83_in_search_of_good_basis.md) | 3 | 4 |
| [11.2 Norm & Condition Number](mit_1806_book/112_norm_condition_number.md) | 13 | 15 |
| [11.3 Iterative Method & preconditioner](mit_1806_book/113_iterative_method_preconditioner.md) | 4 | 6 |
| [3. Vector Spaces and Subspaces](mit_1806_book/3_vector_spaces_and_subspaces.md) | 2 | 6 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-mit1806_gstrang"></a>
### MIT 18.06
<!-- key: mit1806_gstrang -->
<!-- group: Linear Algebra -->
`1,181 notes · 1,269 screenshots · 36 sections`

> This notebook covers fundamental linear algebra concepts, from solving systems of equations and matrix operations to eigenvalues, SVD, and linear transformations, often emphasizing their geometric interpretations.
> Sổ tay này bao gồm các khái niệm cơ bản về đại số tuyến tính, từ giải hệ phương trình và các phép toán ma trận đến trị riêng, phân tích SVD và biến đổi tuyến tính, thường nhấn mạnh các diễn giải hình học của chúng.

<details open>
<summary>📖 36 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [18.03 Lec 25](mit1806_gstrang/1803_lec_25.md) | 27 | 28 |
| [Lecture 1: The Geometry Of Linear Equations](mit1806_gstrang/lecture_1_the_geometry_of_linear_equations.md) | 18 | 20 |
| [Lecture 2: Elimination With Matrices](mit1806_gstrang/lecture_2_elimination_with_matrices.md) | 30 | 31 |
| [Lecture 3: Multiplication And Inverse Matrices](mit1806_gstrang/lecture_3_multiplication_and_inverse_matrices.md) | 22 | 24 |
| [Lecture 4: Factorization Into A = Lu](mit1806_gstrang/lecture_4_factorization_into_a_lu.md) | 23 | 25 |
| [Lecture 5: Transpose, Permutations, Spaces R^n](mit1806_gstrang/lecture_5_transpose_permutations_spaces_rn.md) | 23 | 24 |
| [Lecture 6: Column Space And Null Space](mit1806_gstrang/lecture_6_column_space_and_null_space.md) | 24 | 24 |
| [Lecture 7: Solving Ax = 0: Pivot Variables, Special Solutions](mit1806_gstrang/lecture_7_solving_ax_0_pivot_variables_special_solutions.md) | 32 | 37 |
| [Lecture 8: Solving Ax = B: Row Reduced Form R](mit1806_gstrang/lecture_8_solving_ax_b_row_reduced_form_r.md) | 35 | 37 |
| [Lecture 9: Independece, Basis, And Dimension](mit1806_gstrang/lecture_9_independece_basis_and_dimension.md) | 35 | 37 |
| [Lecture 10: The Four Fundamental Subspaces](mit1806_gstrang/lecture_10_the_four_fundamental_subspaces.md) | 24 | 29 |
| [Lecture 11: Matrix Spaces; Rank 1; Small World Graphs](mit1806_gstrang/lecture_11_matrix_spaces_rank_1_small_world_graphs.md) | 33 | 34 |
| [Lecture 12: Graphs, Networks, Incidence Matrices](mit1806_gstrang/lecture_12_graphs_networks_incidence_matrices.md) | 37 | 40 |
| [Lecture 13: Quiz Review](mit1806_gstrang/lecture_13_quiz_review.md) | 36 | 40 |
| [Lecture 14: Orthogonal Vectors And Subspaces](mit1806_gstrang/lecture_14_orthogonal_vectors_and_subspaces.md) | 37 | 37 |
| [Lecture 15: Projections Onto Subspaces](mit1806_gstrang/lecture_15_projections_onto_subspaces.md) | 45 | 47 |
| [Lecture 16: Projection Matrices And Least Squares](mit1806_gstrang/lecture_16_projection_matrices_and_least_squares.md) | 38 | 43 |
| [Lecture 17: Orthogonal Matrices And Gram-schmidt](mit1806_gstrang/lecture_17_orthogonal_matrices_and_gram_schmidt.md) | 38 | 39 |
| [Lecture 18: Properties Of Determinants](mit1806_gstrang/lecture_18_properties_of_determinants.md) | 34 | 39 |
| [Lecture 19: Determinant Formulas And Cofactors](mit1806_gstrang/lecture_19_determinant_formulas_and_cofactors.md) | 39 | 41 |
| [Lecture 20: Cramer's Rule, Inverse Matrix And Volume](mit1806_gstrang/lecture_20_cramers_rule_inverse_matrix_and_volume.md) | 29 | 30 |
| [Lecture 21: Eigenvalues And Eigenvectors](mit1806_gstrang/lecture_21_eigenvalues_and_eigenvectors.md) | 38 | 39 |
| [Lecture 22: Diagonalization And Powers Of A](mit1806_gstrang/lecture_22_diagonalization_and_powers_of_a.md) | 40 | 42 |
| [Lecture 23: Differential Equations And Exp(at)](mit1806_gstrang/lecture_23_differential_equations_and_expat.md) | 50 | 56 |
| [Lecture 24: Markow Matrices; Fourier Series](mit1806_gstrang/lecture_24_markow_matrices_fourier_series.md) | 35 | 37 |
| [Lecture 24b: Quiz 2 Review](mit1806_gstrang/lecture_24b_quiz_2_review.md) | 29 | 34 |
| [Lecture 25: Symmetric Matrices And Positive Definiteness](mit1806_gstrang/lecture_25_symmetric_matrices_and_positive_definiteness.md) | 28 | 30 |
| [Lecture 26: Complex Matrices; Fast Fourier Transform](mit1806_gstrang/lecture_26_complex_matrices_fast_fourier_transform.md) | 27 | 30 |
| [Lecture 27: Positive Definite Matrices And Minima](mit1806_gstrang/lecture_27_positive_definite_matrices_and_minima.md) | 36 | 39 |
| [Lecture 28: Similar Matrices And Jordan Form](mit1806_gstrang/lecture_28_similar_matrices_and_jordan_form.md) | 32 | 32 |
| [Lecture 29: Singular Value Decomposition](mit1806_gstrang/lecture_29_singular_value_decomposition.md) | 33 | 37 |
| [Lecture 30: Linear Transformations And Their Matrices](mit1806_gstrang/lecture_30_linear_transformations_and_their_matrices.md) | 42 | 46 |
| [Lecture 31: Change Of Basis; Image Compression](mit1806_gstrang/lecture_31_change_of_basis_image_compression.md) | 35 | 36 |
| [Lecture 32: Quiz 3 Review](mit1806_gstrang/lecture_32_quiz_3_review.md) | 35 | 38 |
| [Lecture 33: Left And Right Inverse; Pseudoinverse](mit1806_gstrang/lecture_33_left_and_right_inverse_pseudoinverse.md) | 30 | 33 |
| [Lecture 34: Final Course Review](mit1806_gstrang/lecture_34_final_course_review.md) | 32 | 34 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="group-machine-learning-deep-learning"></a>
### 📂 Machine Learning & Deep Learning

<a id="nb-cs224n_stanford"></a>
### CS224N_Stanford
<!-- key: cs224n_stanford -->
<!-- group: Machine Learning & Deep Learning -->
`791 notes · 1,108 screenshots · 27 sections`

> A comprehensive study notebook for Stanford's CS224N (Natural Language Processing with Deep Learning) course, covering fundamental to advanced NLP concepts from word embeddings (Word2Vec, GloVe) to neural architectures like RNNs, Transformers, and RLHF.
> Sổ tay học tập toàn diện cho khóa học CS224N của Stanford (Xử lý Ngôn ngữ Tự nhiên với Học sâu), bao gồm các kiến thức từ cơ bản đến nâng cao từ biểu diễn từ (Word2Vec, GloVe) cho đến các kiến trúc mạng nơ-ron như RNN, Transformer và RLHF.

<details open>
<summary>📖 27 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](cs224n_stanford/_overview.md) | 1 | 1 |
| [Assignment 1](cs224n_stanford/assignment_1.md) | 18 | 29 |
| [Assignment 2 - Word2vec](cs224n_stanford/assignment_2_word2vec.md) | 22 | 56 |
| [Assignment 3 -](cs224n_stanford/assignment_3_dependency_parsing.md) | 31 | 47 |
| [Assignment 4 - NMT](cs224n_stanford/assignment_4_nmt.md) | 18 | 45 |
| [Assignment 5: Self-attention, Transformers And Pretraining](cs224n_stanford/assignment_5_self_attention_transformers_and_pretraining.md) | 9 | 9 |
| [Lec 9 Reading](cs224n_stanford/lec_9_reading.md) | 1 | 1 |
| [Lecture 10: Prompting & RLHF](cs224n_stanford/lecture_10_prompting_rlhf.md) | 51 | 63 |
| [Lecture 11: Question & Answering](cs224n_stanford/lecture_11_question_answering.md) | 46 | 55 |
| [Lecture 12: Natural Language Generation](cs224n_stanford/lecture_12_natural_language_generation.md) | 59 | 68 |
| [Lecture 13: Coreference Resolution](cs224n_stanford/lecture_13_coreference_resolution.md) | 50 | 52 |
| [Lecture 14: Insights Between NLP And Linguistic](cs224n_stanford/lecture_14_insights_between_nlp_and_linguistic.md) | 32 | 38 |
| [Lecture 15: Add Knowledge To Language Model](cs224n_stanford/lecture_15_add_knowledge_to_language_model.md) | 23 | 27 |
| [Lecture 2: Neural Classifiers](cs224n_stanford/lecture_2_neural_classifiers.md) | 58 | 74 |
| [Lecture 3: Backprop And Neural Networks](cs224n_stanford/lecture_3_backprop_and_neural_networks.md) | 29 | 54 |
| [Lecture 4: Syntactic Structure](cs224n_stanford/lecture_4_syntactic_structure_and_dependency_parsing.md) | 41 | 53 |
| [Lecture 5: Recurrent Neural Network](cs224n_stanford/lecture_5_recurrent_neural_network.md) | 15 | 21 |
| [Lecture 6: Simple And Lstm Rnns](cs224n_stanford/lecture_6_simple_and_lstm_rnns.md) | 39 | 58 |
| [Lecture 7: Translation, Seq2seq, Attention](cs224n_stanford/lecture_7_translation_seq2seq_attention.md) | 42 | 48 |
| [Lecture 8: Translation, Seq2seq, Attention](cs224n_stanford/lecture_8_translation_seq2seq_attention.md) | 8 | 17 |
| [Lecture 9: Pretraining](cs224n_stanford/lecture_9_pretraining.md) | 42 | 51 |
| [Lecture 9: Self-attention And Transformers](cs224n_stanford/lecture_9_self_attention_and_transformers.md) | 41 | 45 |
| [Lecture Note - 03](cs224n_stanford/lecture_note_03_backpropagation.md) | 7 | 24 |
| [Lecture Note 04 -](cs224n_stanford/lecture_note_04_dependency_parsers.md) | 13 | 17 |
| [Lecture Notes 05 Language](cs224n_stanford/lecture_notes_05_language_model_rnn_lstm_gru.md) | 38 | 77 |
| [Reading](cs224n_stanford/reading.md) | 0 | 1 |
| [Week 1: Intro & Word Vectors](cs224n_stanford/week_1_intro_word_vectors.md) | 57 | 77 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-cs231n_stanford"></a>
### CS231N_Stanford
<!-- key: cs231n_stanford -->
<!-- group: Machine Learning & Deep Learning -->
`1,603 notes · 2,702 screenshots · 46 sections`

> This notebook contains comprehensive study notes, lecture summaries, and programming assignments from Stanford's CS231n course on Convolutional Neural Networks for Visual Recognition.
> Cuốn sổ tay này tổng hợp các ghi chép học tập, tóm tắt bài giảng và bài tập thực hành từ khóa học CS231n của Đại học Stanford về Mạng nơ-ron tích chập cho Nhận dạng Thị giác.

<details open>
<summary>📖 46 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](cs231n_stanford/_overview.md) | 1 | 1 |
| [Assignment 1 - 2 Layer Nn](cs231n_stanford/assignment_1_2_layer_nn.md) | 28 | 38 |
| [Assignment 1 - KNN](cs231n_stanford/assignment_1_knn.md) | 31 | 45 |
| [Assignment 2 - Batch Normalization](cs231n_stanford/assignment_2_batch_normalization.md) | 18 | 35 |
| [Assignment 2 -](cs231n_stanford/assignment_2_convolutional_network.md) | 27 | 64 |
| [Assignment 2 - Dropout](cs231n_stanford/assignment_2_dropout.md) | 6 | 14 |
| [Assignment 2 - Fully Connected Nn](cs231n_stanford/assignment_2_fully_connected_nn.md) | 25 | 61 |
| [Assignment 2](cs231n_stanford/assignment_2_pytorch.md) | 22 | 32 |
| [Assignment 3 - Lstm Captioning](cs231n_stanford/assignment_3_lstm_captioning.md) | 9 | 34 |
| [Assignment 3 - RNN Captioning](cs231n_stanford/assignment_3_rnn_captioning.md) | 12 | 49 |
| [Assignment 4 - Transformer Image Captioning](cs231n_stanford/assignment_4_transformer_image_captioning.md) | 20 | 36 |
| [Eecs498-007 Lecture 17: 3d Vision](cs231n_stanford/eecs498_007_lecture_17_3d_vision.md) | 49 | 59 |
| [Eecs498-007](cs231n_stanford/eecs498_007_lecture_18_video.md) | 55 | 66 |
| [EECS 498-007/598-005 (2022) - ASSIGNMENT 4 (Part 1):](cs231n_stanford/eecs_498_007598_005_2022_assignment_4_part_1_one_state_object_detector.md) | 49 | 118 |
| [EECS 498-007/598-005 (2022) - ASSIGNMENT 4 (Part 2):](cs231n_stanford/eecs_498_007598_005_2022_assignment_4_part_2_two_stage_detector.md) | 33 | 123 |
| [Eecs 498-007_598-005 (2020) Assignment 4 (part 1):](cs231n_stanford/eecs_498_007_598_005_2020_assignment_4_part_1_single_stage_detector_yolo.md) | 43 | 158 |
| [Eecs 498-007_598-005 (2020) Assignment 4 (part 2):](cs231n_stanford/eecs_498_007_598_005_2020_assignment_4_part_2_two_stage_detector_faster_rcnn.md) | 14 | 90 |
| [Eecs 498-007_598-005 (2020) Assignment 6:](cs231n_stanford/eecs_498_007_598_005_2020_assignment_6_network_visualization.md) | 8 | 33 |
| [Eecs 498-007_598-005 (2020) Assignment 6:](cs231n_stanford/eecs_498_007_598_005_2020_assignment_6_style_transfer.md) | 10 | 39 |
| [Eecs 498-007_598-005 (2022) Assignment 6:](cs231n_stanford/eecs_498_007_598_005_2022_assignment_6_generative_adversarial_network.md) | 20 | 59 |
| [Eecs 498-007_598-005 (2022) Assignment 6:](cs231n_stanford/eecs_498_007_598_005_2022_assignment_6_variational_auto_encoder.md) | 18 | 43 |
| [Guess Lecture - Adversarial Machine Learning](cs231n_stanford/guess_lecture_adversarial_machine_learning.md) | 9 | 12 |
| [Lecture 10/16 - Recurrent Neural Network](cs231n_stanford/lecture_1016_recurrent_neural_network.md) | 67 | 86 |
| [Lecture 11/16 - Detection And](cs231n_stanford/lecture_1116_detection_and_segmentation.md) | 108 | 144 |
| [Lecture 1/16 - Introduction To CNN](cs231n_stanford/lecture_116_introduction_to_cnn.md) | 11 | 31 |
| [Lecture 12/16 - Visualization And](cs231n_stanford/lecture_1216_visualization_and_understanding.md) | 60 | 84 |
| [Lecture 13/16 - Generative Models](cs231n_stanford/lecture_1316_generative_models.md) | 72 | 86 |
| [Lecture 14/16 - Deep Reinforcement](cs231n_stanford/lecture_1416_deep_reinforcement_learning.md) | 24 | 29 |
| [Lecture 14/16 - Generative Models Ii](cs231n_stanford/lecture_1416_generative_models_ii.md) | 45 | 53 |
| [Lecture 2/16 - Image Classification](cs231n_stanford/lecture_216_image_classification.md) | 41 | 58 |
| [Lecture 3/16 - Loss Functions And Optimization](cs231n_stanford/lecture_316_loss_functions_and_optimization.md) | 117 | 154 |
| [Lecture 4/16 - Introduction To Neural Networks](cs231n_stanford/lecture_416_introduction_to_neural_networks.md) | 23 | 55 |
| [Lecture 5/16 - Convolutional Neural Networks](cs231n_stanford/lecture_516_convolutional_neural_networks.md) | 52 | 63 |
| [Lecture 6/16 - Training Neural Network I](cs231n_stanford/lecture_616_training_neural_network_i.md) | 65 | 105 |
| [Lecture 7/16 - Training Neural Network Ii](cs231n_stanford/lecture_716_training_neural_network_ii.md) | 70 | 90 |
| [Lecture 8/16 - Deep Learning Software](cs231n_stanford/lecture_816_deep_learning_software.md) | 89 | 107 |
| [Lecture 9/16 - CNN Architecture](cs231n_stanford/lecture_916_cnn_architecture.md) | 55 | 72 |
| [LECTURE NOTE: Image Classification:](cs231n_stanford/lecture_note_image_classification_data_driven_approach_k_nearest_neighbor_trainvaltest_splits.md) | 1 | 0 |
| [Lecture Note](cs231n_stanford/lecture_note_introduction_to_rnn.md) | 13 | 19 |
| [Lecture Note Nn P1](cs231n_stanford/lecture_note_nn_p1.md) | 1 | 14 |
| [Lecture X: Transformer](cs231n_stanford/lecture_x_transformer.md) | 41 | 47 |
| [Note #4 Backpropagation](cs231n_stanford/note_4_backpropagation.md) | 9 | 13 |
| [Note - Convolutional Net](cs231n_stanford/note_convolutional_net.md) | 22 | 31 |
| [Note - Neural](cs231n_stanford/note_neural_network_part_2.md) | 44 | 59 |
| [Note - Neural Network Part 3](cs231n_stanford/note_neural_network_part_3.md) | 49 | 61 |
| [Paper: Batch normalization](cs231n_stanford/paper_batch_normalization.md) | 17 | 32 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-dl_spec_coursera"></a>
### DL Spec Coursera
<!-- key: dl_spec_coursera -->
<!-- group: Machine Learning & Deep Learning -->
`1,083 notes · 1,827 screenshots · 19 sections`

> A comprehensive compilation of notes, quizzes, and programming assignments from the Coursera Deep Learning Specialization. It covers topics ranging from foundational neural networks to advanced computer vision, NLP architectures, and model optimization using TensorFlow.
> Tổng hợp toàn diện các ghi chép, bài trắc nghiệm và bài tập lập trình từ Chuyên ngành Deep Learning trên Coursera. Nội dung bao gồm từ các khái niệm mạng nơ-ron cơ bản đến các kiến trúc nâng cao về thị giác máy tính, NLP và tối ưu hóa mô hình bằng TensorFlow.

<details open>
<summary>📖 19 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](dl_spec_coursera/_overview.md) | 0 | 1 |
| [C1w1_introduction To N.n](dl_spec_coursera/c1w1_introduction_to_nn.md) | 7 | 24 |
| [C1w2_n.n Basic](dl_spec_coursera/c1w2_nn_basic.md) | 64 | 163 |
| [C1w3_shalow Neural Networks](dl_spec_coursera/c1w3_shalow_neural_networks.md) | 23 | 91 |
| [C1w4_deep Neural Network](dl_spec_coursera/c1w4_deep_neural_network.md) | 21 | 95 |
| [C2w1_practical Aspects Of Deep Learning](dl_spec_coursera/c2w1_practical_aspects_of_deep_learning.md) | 51 | 121 |
| [C2w2_optimization Algorithms](dl_spec_coursera/c2w2_optimization_algorithms.md) | 50 | 96 |
| [C2w3_hyperparamter Tuning, Batch Normalization & Programming Frameworks](dl_spec_coursera/c2w3_hyperparamter_tuning_batch_normalization_programming_frameworks.md) | 58 | 85 |
| [C3w1_machine Learning Strategy 1](dl_spec_coursera/c3w1_machine_learning_strategy_1.md) | 42 | 47 |
| [C3w2_machine Learning Strategy 2](dl_spec_coursera/c3w2_machine_learning_strategy_2.md) | 43 | 40 |
| [C4w1_foundations Of Convolutional Neural Network](dl_spec_coursera/c4w1_foundations_of_convolutional_neural_network.md) | 80 | 117 |
| [C4w2_deep Convolutional Models: Case Studies](dl_spec_coursera/c4w2_deep_convolutional_models_case_studies.md) | 88 | 118 |
| [C4w3_object Detection](dl_spec_coursera/c4w3_object_detection.md) | 59 | 138 |
| [C4w4_face Recognition & Neural Style Transfer](dl_spec_coursera/c4w4_face_recognition_neural_style_transfer.md) | 73 | 105 |
| [C5w1_recurrent Neural Networks](dl_spec_coursera/c5w1_recurrent_neural_networks.md) | 99 | 165 |
| [C5w2_natural Language Processing & Word Embeddings](dl_spec_coursera/c5w2_natural_language_processing_word_embeddings.md) | 59 | 103 |
| [C5w3_sequence Models & Attention Mechanism](dl_spec_coursera/c5w3_sequence_models_attention_mechanism.md) | 72 | 116 |
| [C5w4_transformer Network](dl_spec_coursera/c5w4_transformer_network.md) | 193 | 202 |
| [Untitled](dl_spec_coursera/untitled.md) | 1 | 0 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-nlp_spec_coursera"></a>
### NLP Spec Coursera
<!-- key: nlp_spec_coursera -->
<!-- group: Machine Learning & Deep Learning -->
`1,808 notes · 2,287 screenshots · 19 sections`

> A comprehensive collection of study notes, practical exercises, and implementations from the Coursera NLP Specialization, covering foundational NLP techniques, sequence models, and modern Transformer architectures.
> Cuốn sổ tay tổng hợp các ghi chép học tập, bài tập thực hành và mã nguồn từ khóa học Chuyên sâu về NLP trên Coursera, bao gồm các kỹ thuật NLP nền tảng, mô hình chuỗi và kiến trúc Transformer hiện đại.

<details open>
<summary>📖 19 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](nlp_spec_coursera/_overview.md) | 0 | 1 |
| [C1w1_logistic Regression](nlp_spec_coursera/c1w1_logistic_regression.md) | 64 | 113 |
| [C1w2 - Naive Bayes](nlp_spec_coursera/c1w2_naive_bayes.md) | 83 | 112 |
| [C1w3 - Vector Space Models](nlp_spec_coursera/c1w3_vector_space_models.md) | 146 | 122 |
| [C1w4 - Machine Translation & Document Search](nlp_spec_coursera/c1w4_machine_translation_document_search.md) | 108 | 115 |
| [C2_natural Language Processing With Probabilistic Models](nlp_spec_coursera/c2_natural_language_processing_with_probabilistic_models.md) | 0 | 1 |
| [C2w1_autocorrect](nlp_spec_coursera/c2w1_autocorrect.md) | 110 | 123 |
| [C2w2_part Of Speech Tagging And Hidden Markov Models](nlp_spec_coursera/c2w2_part_of_speech_tagging_and_hidden_markov_models.md) | 169 | 171 |
| [C2w3_autocomplete And Language Models](nlp_spec_coursera/c2w3_autocomplete_and_language_models.md) | 152 | 143 |
| [C3w1_neural Networks For Sentiment Analysis](nlp_spec_coursera/c3w1_neural_networks_for_sentiment_analysis.md) | 94 | 141 |
| [C3w2_recurrent Neural Networks For Language Modeling](nlp_spec_coursera/c3w2_recurrent_neural_networks_for_language_modeling.md) | 85 | 138 |
| [C3W3_LSTMs AND NAMED ENTITY REGCONITION:](nlp_spec_coursera/c3w3_lstms_and_named_entity_regconition.md) | 69 | 108 |
| [C3w4 - Siamese Network](nlp_spec_coursera/c3w4_siamese_network.md) | 82 | 122 |
| [C3w4_word Embeddings With Neural Networks](nlp_spec_coursera/c3w4_word_embeddings_with_neural_networks.md) | 173 | 211 |
| [C4_natural Language Processing With Attention Models](nlp_spec_coursera/c4_natural_language_processing_with_attention_models.md) | 0 | 1 |
| [C4w1_neural Machine Translation](nlp_spec_coursera/c4w1_neural_machine_translation.md) | 167 | 220 |
| [C4w2_text Summarization](nlp_spec_coursera/c4w2_text_summarization.md) | 86 | 145 |
| [C4w3 - Question Answering](nlp_spec_coursera/c4w3_question_answering.md) | 130 | 187 |
| [C4w4_chatbot](nlp_spec_coursera/c4w4_chatbot.md) | 90 | 113 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="group-optimization"></a>
### 📂 Optimization

<a id="nb-ee364a_convex_optim_sboyd"></a>
### EE364a, Convex Optim_S.Boyd
<!-- key: ee364a_convex_optim_sboyd -->
<!-- group: Optimization -->
`875 notes · 1,347 screenshots · 21 sections`

> A comprehensive collection of study notes and lecture summaries for Stephen Boyd's Convex Optimization course (EE364a), covering fundamental concepts such as convex sets and functions, duality theory, KKT conditions, and optimization algorithms.
> Bộ sưu tập chi tiết các ghi chép học tập và tóm tắt bài giảng cho khóa học Tối ưu hóa Lồi (EE364a) của Stephen Boyd, bao gồm các khái niệm nền tảng như tập hợp và hàm lồi, lý thuyết đối ngẫu, điều kiện KKT và các thuật toán tối ưu hóa.

<details open>
<summary>📖 21 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [Appendix A](ee364a_convex_optim_sboyd/appendix_a.md) | 5 | 15 |
| [Appendix C](ee364a_convex_optim_sboyd/appendix_c.md) | 43 | 63 |
| [Chap 10](ee364a_convex_optim_sboyd/chap_10.md) | 60 | 99 |
| [Chap 11:1,2,3,4,5](ee364a_convex_optim_sboyd/chap_1112345.md) | 53 | 95 |
| [Chap 11.6](ee364a_convex_optim_sboyd/chap_116.md) | 32 | 60 |
| [Chap 9.1 - 9.4](ee364a_convex_optim_sboyd/chap_91_94.md) | 34 | 68 |
| [Chap 9.5](ee364a_convex_optim_sboyd/chap_95.md) | 44 | 81 |
| [Lec 1](ee364a_convex_optim_sboyd/lec_1.md) | 51 | 63 |
| [Lec 10](ee364a_convex_optim_sboyd/lec_10.md) | 35 | 64 |
| [Lec 10b](ee364a_convex_optim_sboyd/lec_10b.md) | 33 | 60 |
| [Lec 11](ee364a_convex_optim_sboyd/lec_11.md) | 48 | 92 |
| [Lec 2](ee364a_convex_optim_sboyd/lec_2.md) | 34 | 49 |
| [Lec 3](ee364a_convex_optim_sboyd/lec_3.md) | 60 | 76 |
| [Lec 4](ee364a_convex_optim_sboyd/lec_4.md) | 39 | 43 |
| [Lec 5](ee364a_convex_optim_sboyd/lec_5.md) | 61 | 82 |
| [Lec 6](ee364a_convex_optim_sboyd/lec_6.md) | 31 | 36 |
| [Lec 7](ee364a_convex_optim_sboyd/lec_7.md) | 56 | 77 |
| [Lec 8 A](ee364a_convex_optim_sboyd/lec_8_a.md) | 45 | 59 |
| [Lec 8 B](ee364a_convex_optim_sboyd/lec_8_b.md) | 37 | 51 |
| [Lec 9](ee364a_convex_optim_sboyd/lec_9.md) | 48 | 64 |
| [Lec 9b](ee364a_convex_optim_sboyd/lec_9b.md) | 26 | 50 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-numerical_optimization_jnocedal"></a>
### Numerical Optimization_J.Nocedal
<!-- key: numerical_optimization_jnocedal -->
<!-- group: Optimization -->
<!-- videos: [{"url":"https://www.youtube.com/watch?v=PzLtTlIO-kE","title":"Tại sao Lagrangian lồi ngặt giúp nghiệm Dual giải bài toán Primal?","videoId":"PzLtTlIO-kE","uploadedAt":1790705388728},{"url":"https://www.youtube.com/watch?v=qSrfcPuiA4k","title":"Tại sao nghiệm KKT λ̃ làm cực đại hóa hàm đối ngẫu q(λ)?","videoId":"qSrfcPuiA4k","uploadedAt":1790430332543},{"url":"https://youtu.be/6g2qIzX9yO0","title":"Vì sao df/dε = -λ*||∇ci|| khi thay đổi ràng buộc ci(x)?","videoId":"6g2qIzX9yO0","uploadedAt":1789916409346},{"url":"https://www.youtube.com/watch?v=wy_PaBOEbnY","title":"Tại sao nhân tử Lagrange λ* = 0 khi ràng buộc không active?","videoId":"wy_PaBOEbnY","uploadedAt":1789858516690},{"url":"https://youtu.be/oS8uhtEOI9w","title":"Vì sao Projected Hessian Zᵀ∇²LZ giúp kiểm tra cực tiểu dễ hơn?","videoId":"oS8uhtEOI9w","uploadedAt":1789916587155},{"url":"https://www.youtube.com/watch?v=GtOATZjDGQs","title":"Theorem 12.11 Weak Duality","videoId":"GtOATZjDGQs","uploadedAt":1790393266298},{"url":"https://www.youtube.com/watch?v=UGddFxbogXU","title":"Tại sao hàm dual objective q(λ) luôn concave và domain 𝒟 lồi?","videoId":"UGddFxbogXU","uploadedAt":1790306878388}] -->
`428 notes · 620 screenshots · 37 sections`

> This notebook delves into core numerical optimization algorithms like line search, trust-region, quasi-Newton, and conjugate gradient methods, alongside essential concepts such as automatic differentiation, convergence analysis, and numerical linear algebra techniques.
> Sổ tay này đi sâu vào các thuật toán tối ưu hóa số cốt lõi như tìm kiếm đường thẳng, vùng tin cậy, quasi-Newton và gradient liên hợp, cùng các khái niệm thiết yếu như đạo hàm tự động, phân tích hội tụ và kỹ thuật đại số tuyến tính số.

<details open>
<summary>📖 37 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](numerical_optimization_jnocedal/_overview.md) | 1 | 1 |
| [2.1 Funds of Unconstrained Optim - What's Solution](numerical_optimization_jnocedal/21_funds_of_unconstrained_optim_whats_solution.md) | 15 | 21 |
| [2.2 Funds of Unconstrained Optim - Overview of Algorithms](numerical_optimization_jnocedal/22_funds_of_unconstrained_optim_overview_of_algorithms.md) | 24 | 36 |
| [3.1 Line Search Method: Step Length](numerical_optimization_jnocedal/31_line_search_method_step_length.md) | 13 | 20 |
| [3.2 Line Search Method: Convergence of Line Search Methods](numerical_optimization_jnocedal/32_line_search_method_convergence_of_line_search_methods.md) | 10 | 13 |
| [3.3 Line Search Method: Rate of Convergence](numerical_optimization_jnocedal/33_line_search_method_rate_of_convergence.md) | 19 | 23 |
| [3.4 Line Search Method: Newton’s Method with Hessian Modification](numerical_optimization_jnocedal/34_line_search_method_newtons_method_with_hessian_modification.md) | 24 | 29 |
| [3.5 Line Search Method: Step-Length Selection Algorithms](numerical_optimization_jnocedal/35_line_search_method_step_length_selection_algorithms.md) | 12 | 17 |
| [4.0 Trust-Region Methods: Outline of the Trust-Region Approach](numerical_optimization_jnocedal/40_trust_region_methods_outline_of_the_trust_region_approach.md) | 12 | 11 |
| [4.1 Trust-Region Methods: Algorithms Based on the Cauchy Point](numerical_optimization_jnocedal/41_trust_region_methods_algorithms_based_on_the_cauchy_point.md) | 11 | 17 |
| [4.2 Trust-Region Methods: Global Convergence](numerical_optimization_jnocedal/42_trust_region_methods_global_convergence.md) | 13 | 16 |
| [4.3 Trust-Region Methods: Iterative Solution of the Subproblem](numerical_optimization_jnocedal/43_trust_region_methods_iterative_solution_of_the_subproblem.md) | 16 | 26 |
| [4.4 Trust-Region Methods: Local Convergence of Trust-Region Newton Method](numerical_optimization_jnocedal/44_trust_region_methods_local_convergence_of_trust_region_newton_method.md) | 1 | 0 |
| [4.5 Trust-Region Methods: Other Enhancements](numerical_optimization_jnocedal/45_trust_region_methods_other_enhancements.md) | 5 | 8 |
| [5.1 Linear Conjugate Gradient](numerical_optimization_jnocedal/51_linear_conjugate_gradient.md) | 23 | 52 |
| [6.1 The BFGS Method](numerical_optimization_jnocedal/61_the_bfgs_method.md) | 20 | 27 |
| [6.2 The SR1 Method](numerical_optimization_jnocedal/62_the_sr1_method.md) | 6 | 15 |
| [6.4 Convergence Analysis](numerical_optimization_jnocedal/64_convergence_analysis.md) | 5 | 6 |
| [7.1 Inexact Newton Methods](numerical_optimization_jnocedal/71_inexact_newton_methods.md) | 22 | 28 |
| [7.2 Limited-Memory Quasi-Newton Methods](numerical_optimization_jnocedal/72_limited_memory_quasi_newton_methods.md) | 19 | 23 |
| [8.1 Finite-Difference Derivative Approx](numerical_optimization_jnocedal/81_finite_difference_derivative_approx.md) | 20 | 29 |
| [8.2 Automatic differentiation(*extremely important for AI)](numerical_optimization_jnocedal/82_automatic_differentiationextremely_important_for_ai.md) | 36 | 46 |
| [10.1 Least-square problem](numerical_optimization_jnocedal/101_least_square_problem.md) | 11 | 13 |
| [10.2 Linear Least-Square Problem](numerical_optimization_jnocedal/102_linear_least_square_problem.md) | 9 | 11 |
| [10.3 Algorithms for nonlinear least-squares problem](numerical_optimization_jnocedal/103_algorithms_for_nonlinear_least_squares_problem.md) | 14 | 23 |
| [10.4 Orthogonal Distance Regression (bỏ qua)](numerical_optimization_jnocedal/104_orthogonal_distance_regression_b_qua.md) | 1 | 1 |
| [12.0 Theory of Constrained Optimization](numerical_optimization_jnocedal/120_theory_of_constrained_optimization.md) | 5 | 8 |
| [12.1 Examples](numerical_optimization_jnocedal/121_examples.md) | 9 | 17 |
| [12.2 Tangent Cone & Constraint Qualification](numerical_optimization_jnocedal/122_tangent_cone_constraint_qualification.md) | 6 | 14 |
| [12.3 First Order Optimality Condition](numerical_optimization_jnocedal/123_first_order_optimality_condition.md) | 3 | 5 |
| [12.5  Second-Order Conditions](numerical_optimization_jnocedal/125_second_order_conditions.md) | 14 | 26 |
| [12.6 Other constraint qualification](numerical_optimization_jnocedal/126_other_constraint_qualification.md) | 2 | 2 |
| [12.8 Lagrange Multipliers and Sensitivity](numerical_optimization_jnocedal/128_lagrange_multipliers_and_sensitivity.md) | 3 | 5 |
| [12.9 Duality](numerical_optimization_jnocedal/129_duality.md) | 6 | 9 |
| [Appendix A](numerical_optimization_jnocedal/appendix_a.md) | 1 | 1 |
| [A.1 Error Analysis & Floating-Point Arithmetic](numerical_optimization_jnocedal/a1_error_analysis_floating_point_arithmetic.md) | 8 | 10 |
| [A.1 Matrix Factorizations: Cholesky, LU, QR](numerical_optimization_jnocedal/a1_matrix_factorizations_cholesky_lu_qr.md) | 9 | 11 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="group-machine-learning-foundation"></a>
### 📂 Machine Learning Foundation

<a id="nb-pattern_recognition_machine_learning_cbishop"></a>
### Pattern Recognition Machine Learning_C.Bishop
<!-- key: pattern_recognition_machine_learning_cbishop -->
<!-- group: Machine Learning Foundation -->
<!-- videos: [{"url":"https://www.youtube.com/watch?v=qAxY0gbf8rM","title":"Vì sao xấp xỉ tuyến tính Sigmoid biến Logistic Regression thành Least Squares?","videoId":"qAxY0gbf8rM","uploadedAt":1790377296587},{"url":"https://www.youtube.com/watch?v=uW9swHIgaPw","title":"Vì sao nghiệm IRLS lại có dạng Weighted Least Squares?","videoId":"uW9swHIgaPw","uploadedAt":1790291738339},{"url":"https://www.youtube.com/watch?v=E55dfUAdwjE","title":"Vì sao giáo sư Bishop gọi S1, S2 là covariance matrix","videoId":"E55dfUAdwjE","uploadedAt":1789680661454},{"url":"https://www.youtube.com/watch?v=OefUwDAl93Q","title":"Tại sao Newton-Raphson trong Logistic Regression lại ra Weighted Least Squares?","videoId":"OefUwDAl93Q","uploadedAt":1790282941701},{"url":"https://www.youtube.com/watch?v=W4pQ_271eXE","title":"Tại sao đạo hàm hàm Sigmoid lại bằng σ(1 - σ)?","videoId":"W4pQ_271eXE","uploadedAt":1790022243689},{"url":"https://www.youtube.com/watch?v=fuo5lM8PyCk","title":"Làm sao chọn threshold cho Fisher Discriminant nhờ CLT và MLE?","videoId":"fuo5lM8PyCk","uploadedAt":1788910581229},{"url":"https://www.youtube.com/watch?v=ZI3dek5QaCc","title":"Tại sao nghiệm MLE của 𝜍1 lại chính là trung bình mẫu?","videoId":"ZI3dek5QaCc","uploadedAt":1789592527015},{"url":"https://www.youtube.com/watch?v=Ovmp-M7j5II","title":"Vì sao họ Exponential với scale chung cho Log-odds tuyến tính?","videoId":"Ovmp-M7j5II","uploadedAt":1789683381098},{"url":"https://www.youtube.com/watch?v=FZ8WIyEcWwk","title":"Mẹo dùng vi phân vector để tìm ma trận Hessian của Logistic Regression chỉ trong 3 phút.","videoId":"FZ8WIyEcWwk","uploadedAt":1790220529722},{"url":"https://www.youtube.com/watch?v=SNbte9J7NL8","title":"Tại sao đạo hàm Cross-Entropy theo w_j bằng (y_nj - t_nj)Φ_n?","videoId":"SNbte9J7NL8","uploadedAt":1790716426862},{"url":"https://www.youtube.com/watch?v=AxZbMJ3AD1E","title":"Vì sao Least Squares lại cho cùng nghiệm w với Fisher Criterion?","videoId":"AxZbMJ3AD1E","uploadedAt":1788988069347},{"url":"https://www.youtube.com/watch?v=TSv9sh-O1Os","title":"Vì sao Least Squares phân loại kém do giả định Gaussian?","videoId":"TSv9sh-O1Os","uploadedAt":1788623614956},{"url":"https://www.youtube.com/watch?v=RfrcgvaQmgU","title":"Activation Derivative for Maximum Likelihood","videoId":"RfrcgvaQmgU","uploadedAt":1790626221283},{"url":"https://www.youtube.com/watch?v=-9YldVmpmPU","title":"Tại sao Class Posterior lại là Softmax tuyến tính của feature Φ?","videoId":"-9YldVmpmPU","uploadedAt":1790378986165},{"url":"https://www.youtube.com/watch?v=IJMvYy5NB-k","title":"Tại sao Cross-Entropy Loss thực chất là Negative Log-Likelihood?","videoId":"IJMvYy5NB-k","uploadedAt":1790031455474},{"url":"https://www.youtube.com/watch?v=D1LgZ77Hxgs","title":"Dự đoán \"Quá đúng\" lại bị SSE phạt nặng, hạn chế của mô hình phân loại tuyến tính theo least square ","videoId":"D1LgZ77Hxgs","uploadedAt":1788488738804},{"url":"https://www.youtube.com/watch?v=LNW4K9FY_As","title":"Learning with me: Maximum Likelihood on Linearly Separable Data ","videoId":"LNW4K9FY_As","uploadedAt":1790112160343},{"url":"https://www.youtube.com/watch?v=XzhGTA5AeNU","title":"Tại sao MLE làm norm của W tiến ra vô cực?","videoId":"XzhGTA5AeNU","uploadedAt":1790117348534},{"url":"https://www.youtube.com/watch?v=5kKAasvIeGI","title":"Vì Sao Basis Function ϕ(x) Biến Dữ Liệu Thành Linearly Separable?","videoId":"5kKAasvIeGI","uploadedAt":1789771898531},{"url":"https://www.youtube.com/watch?v=9rn2c18KCbI","title":"Tại sao vectơ chiếu w phải song song với đường nối hai tâm?","videoId":"9rn2c18KCbI","uploadedAt":1788632547156},{"url":"https://www.youtube.com/watch?v=kI2yukn25aQ","title":"Cách tự derive gradient và Hessian của hàm quadratic","videoId":"kI2yukn25aQ","uploadedAt":1790195064225},{"url":"https://www.youtube.com/watch?v=KQozp2d2dy8","title":"Vì sao Newton-Raphson giải Linear Regression chỉ trong đúng 1 bước?","videoId":"KQozp2d2dy8","uploadedAt":1790197183525},{"url":"https://youtu.be/S4kORpAgTsQ","title":"Từ Likelihood suy ra Multiclass Cross-Entropy Loss như thế nào?","videoId":"S4kORpAgTsQ","uploadedAt":1790632928275},{"url":"https://www.youtube.com/watch?v=OMWS53GIrUI","title":"Tại sao nên giả định trực tiếp f(C|x) thay vì ước lượng f(x|C)?","videoId":"OMWS53GIrUI","uploadedAt":1789766773670},{"url":"https://www.youtube.com/watch?v=YN8gyl1HEAA","title":"Tại sao Logistic Regression chỉ tốn M tham số thay vì M(M+5)/2+1?","videoId":"YN8gyl1HEAA","uploadedAt":1789775417418},{"url":"https://www.youtube.com/watch?v=yOm1k_DQ3K0","title":"Tại sao bước lặp Newton dùng xấp xỉ bậc hai cục bộ?","videoId":"yOm1k_DQ3K0","uploadedAt":1790121880818},{"url":"https://www.youtube.com/watch?v=STiYw1o_W1E","title":"Tại sao ma trận hiệp phương sai MLE chung lại bằng S?","videoId":"STiYw1o_W1E","uploadedAt":1789597319502},{"url":"https://www.youtube.com/watch?v=2Dy41xan6xg","title":"Vì sao ma trận hiệp phương sai chung Σ bằng S?","videoId":"2Dy41xan6xg","uploadedAt":1789610153199},{"url":"https://www.youtube.com/watch?v=PEL_sI4YGSg","title":"Tại sao không tối ưu Perceptron bằng số ca phân loại sai?","videoId":"PEL_sI4YGSg","uploadedAt":1789160475415},{"url":"https://www.youtube.com/watch?v=XWXHBKtAWK0","title":"Vì sao hướng tối ưu w của Fisher là Sw⁻¹(m2 - m1)?","videoId":"XWXHBKtAWK0","uploadedAt":1788839850967},{"url":"https://www.youtube.com/watch?v=jbPysqwE8nc","title":"Vì sao Naive Bayes giảm số tham số từ 2^D xuống D?","videoId":"jbPysqwE8nc","uploadedAt":1789678706927},{"url":"https://www.youtube.com/watch?v=Sz2QRKW9wLA","title":"Tại sao ma trận Hessian Multiclass gồm các block M×M?","videoId":"Sz2QRKW9wLA","uploadedAt":1790730933980}] -->
`443 notes · 673 screenshots · 71 sections`

> This notebook summarizes key concepts from C. Bishop's 'Pattern Recognition and Machine Learning,' covering foundational probability theory, Bayesian inference, common machine learning models, and essential mathematical tools.
> Sổ tay này tóm tắt các khái niệm chính từ sách 'Pattern Recognition and Machine Learning' của C. Bishop, bao gồm lý thuyết xác suất nền tảng, suy luận Bayes, các mô hình học máy phổ biến và những công cụ toán học thiết yếu.

<details open>
<summary>📖 71 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](pattern_recognition_machine_learning_cbishop/_overview.md) | 0 | 1 |
| [1.0 Into](pattern_recognition_machine_learning_cbishop/10_into.md) | 8 | 8 |
| [1.1 Example: Polynomial Curve Fitting](pattern_recognition_machine_learning_cbishop/11_example_polynomial_curve_fitting.md) | 13 | 20 |
| [1.2.0 Probability theory](pattern_recognition_machine_learning_cbishop/120_probability_theory.md) | 13 | 21 |
| [1.2.1&2 Probability densities & Expectations Covariances](pattern_recognition_machine_learning_cbishop/1212_probability_densities_expectations_covariances.md) | 14 | 18 |
| [1.2.3 Bayesian probabilities](pattern_recognition_machine_learning_cbishop/123_bayesian_probabilities.md) | 11 | 14 |
| [1.2.4 The Gaussian distribution](pattern_recognition_machine_learning_cbishop/124_the_gaussian_distribution.md) | 10 | 14 |
| [1.2.5 Curve fitting re-visited.](pattern_recognition_machine_learning_cbishop/125_curve_fitting_re_visited.md) | 9 | 11 |
| [1.2.6 Bayesian curve fitting](pattern_recognition_machine_learning_cbishop/126_bayesian_curve_fitting.md) | 6 | 7 |
| [1.3 Model Selection](pattern_recognition_machine_learning_cbishop/13_model_selection.md) | 5 | 6 |
| [1.4 The Curse Of Dimensionality](pattern_recognition_machine_learning_cbishop/14_the_curse_of_dimensionality.md) | 6 | 15 |
| [1.5 Decision Theory](pattern_recognition_machine_learning_cbishop/15_decision_theory.md) | 29 | 41 |
| [1.6 Information Theory](pattern_recognition_machine_learning_cbishop/16_information_theory.md) | 24 | 32 |
| [1.7 Excersices](pattern_recognition_machine_learning_cbishop/17_excersices.md) | 1 | 0 |
| [2.0 Intro](pattern_recognition_machine_learning_cbishop/20_intro.md) | 4 | 5 |
| [2.1 Binary Variables](pattern_recognition_machine_learning_cbishop/21_binary_variables.md) | 16 | 24 |
| [2.2 Multinomial Variables](pattern_recognition_machine_learning_cbishop/22_multinomial_variables.md) | 7 | 10 |
| [2.3.0 Gaussian Distribution](pattern_recognition_machine_learning_cbishop/230_gaussian_distribution.md) | 16 | 27 |
| [2.3.1 Conditional Gaussian](pattern_recognition_machine_learning_cbishop/231_conditional_gaussian.md) | 6 | 7 |
| [2.3.2 Marginal Gaussian](pattern_recognition_machine_learning_cbishop/232_marginal_gaussian.md) | 3 | 7 |
| [2.3.3 Bayes's theorem for Gaussian variables](pattern_recognition_machine_learning_cbishop/233_bayess_theorem_for_gaussian_variables.md) | 6 | 9 |
| [2.3.4 Maximum Likelihood for Gaussian](pattern_recognition_machine_learning_cbishop/234_maximum_likelihood_for_gaussian.md) | 4 | 4 |
| [2.3.5 Sequential  estimation](pattern_recognition_machine_learning_cbishop/235_sequential_estimation.md) | 5 | 8 |
| [2.3.6 Bayes inference for the Gaussian](pattern_recognition_machine_learning_cbishop/236_bayes_inference_for_the_gaussian.md) | 8 | 13 |
| [2.3.7 Studen's t-distribution](pattern_recognition_machine_learning_cbishop/237_studens_t_distribution.md) | 4 | 9 |
| [2.3.8 Periodic variables](pattern_recognition_machine_learning_cbishop/238_periodic_variables.md) | 7 | 17 |
| [2.3.9 Mixtures of Gaussians](pattern_recognition_machine_learning_cbishop/239_mixtures_of_gaussians.md) | 5 | 9 |
| [2.4 The Exponential Family](pattern_recognition_machine_learning_cbishop/24_the_exponential_family.md) | 6 | 9 |
| [2.4.1 Maximum likelihood & sufficient statistic](pattern_recognition_machine_learning_cbishop/241_maximum_likelihood_sufficient_statistic.md) | 4 | 4 |
| [2.4.4 Conjugate prior](pattern_recognition_machine_learning_cbishop/244_conjugate_prior.md) | 1 | 1 |
| [2.4.3 Non-informative priors](pattern_recognition_machine_learning_cbishop/243_non_informative_priors.md) | 7 | 8 |
| [2.5 Non-parametric model](pattern_recognition_machine_learning_cbishop/25_non_parametric_model.md) | 5 | 5 |
| [2.5.1 Kernel density estimators](pattern_recognition_machine_learning_cbishop/251_kernel_density_estimators.md) | 7 | 9 |
| [2.5.2 Nearest-neighbour methods](pattern_recognition_machine_learning_cbishop/252_nearest_neighbour_methods.md) | 5 | 10 |
| [3.1.0 Linear Regression and Basis Functions](pattern_recognition_machine_learning_cbishop/310_linear_regression_and_basis_functions.md) | 7 | 9 |
| [3.1.1 Maximum likelihood and least squares](pattern_recognition_machine_learning_cbishop/311_maximum_likelihood_and_least_squares.md) | 7 | 10 |
| [3.1.2 Geometry of least squares](pattern_recognition_machine_learning_cbishop/312_geometry_of_least_squares.md) | 1 | 2 |
| [3.1.3 Sequential Learning](pattern_recognition_machine_learning_cbishop/313_sequential_learning.md) | 1 | 2 |
| [3.1.5 Multiple outputs](pattern_recognition_machine_learning_cbishop/315_multiple_outputs.md) | 3 | 3 |
| [3.1.4 Regularized least squares](pattern_recognition_machine_learning_cbishop/314_regularized_least_squares.md) | 3 | 7 |
| [3.2.0 The Bias-Variance Decomposition](pattern_recognition_machine_learning_cbishop/320_the_bias_variance_decomposition.md) | 8 | 16 |
| [3.3.2 Predictive distribution](pattern_recognition_machine_learning_cbishop/332_predictive_distribution.md) | 6 | 10 |
| [3.3.1 Bayesian Linear Regression](pattern_recognition_machine_learning_cbishop/331_bayesian_linear_regression.md) | 8 | 12 |
| [3.3.3 Equivalent kernel](pattern_recognition_machine_learning_cbishop/333_equivalent_kernel.md) | 5 | 8 |
| [3.4 Bayesian Model Comparison](pattern_recognition_machine_learning_cbishop/34_bayesian_model_comparison.md) | 11 | 15 |
| [3.5.1 Evaluation of the evidence function](pattern_recognition_machine_learning_cbishop/351_evaluation_of_the_evidence_function.md) | 4 | 9 |
| [3.5 Evidence Approximation](pattern_recognition_machine_learning_cbishop/35_evidence_approximation.md) | 6 | 6 |
| [3.5.2 Maximizing the evidence function](pattern_recognition_machine_learning_cbishop/352_maximizing_the_evidence_function.md) | 3 | 4 |
| [3.5.3 Effective number of parameters](pattern_recognition_machine_learning_cbishop/353_effective_number_of_parameters.md) | 6 | 17 |
| [3.6 Limitations of Fixed Basis Functions](pattern_recognition_machine_learning_cbishop/36_limitations_of_fixed_basis_functions.md) | 1 | 2 |
| [3.7 Exercises](pattern_recognition_machine_learning_cbishop/37_exercises.md) | 6 | 7 |
| [4.0 Linear model for Classification](pattern_recognition_machine_learning_cbishop/40_linear_model_for_classification.md) | 4 | 5 |
| [4.1.2 Multiple Class](pattern_recognition_machine_learning_cbishop/412_multiple_class.md) | 3 | 7 |
| [4.1.1 Discriminant Functions](pattern_recognition_machine_learning_cbishop/411_discriminant_functions.md) | 1 | 3 |
| [4.1.3 Least squares for classification](pattern_recognition_machine_learning_cbishop/413_least_squares_for_classification.md) | 7 | 9 |
| [4.1.4 Fisher's linear discriminant](pattern_recognition_machine_learning_cbishop/414_fishers_linear_discriminant.md) | 3 | 9 |
| [4.1.5 Relation to least square](pattern_recognition_machine_learning_cbishop/415_relation_to_least_square.md) | 2 | 3 |
| [4.1.6 Fisher’s discriminant for multiple classes](pattern_recognition_machine_learning_cbishop/416_fishers_discriminant_for_multiple_classes.md) | 2 | 4 |
| [4.1.7 Perceptron](pattern_recognition_machine_learning_cbishop/417_perceptron.md) | 6 | 10 |
| [4.2 Probabilistic Generative Model](pattern_recognition_machine_learning_cbishop/42_probabilistic_generative_model.md) | 2 | 4 |
| [4.2.1 Continuous inputs](pattern_recognition_machine_learning_cbishop/421_continuous_inputs.md) | 3 | 7 |
| [4.2.2 Maximum likelihood solution](pattern_recognition_machine_learning_cbishop/422_maximum_likelihood_solution.md) | 4 | 6 |
| [4.2.4 Discrete features](pattern_recognition_machine_learning_cbishop/424_discrete_features.md) | 1 | 1 |
| [4.2.4 Exponential family](pattern_recognition_machine_learning_cbishop/424_exponential_family.md) | 1 | 2 |
| [4.3. Probabilistic Discriminative Models](pattern_recognition_machine_learning_cbishop/43_probabilistic_discriminative_models.md) | 1 | 2 |
| [4.3.1 Fixed basis functions](pattern_recognition_machine_learning_cbishop/431_fixed_basis_functions.md) | 2 | 5 |
| [4.3.2 Logistic regression](pattern_recognition_machine_learning_cbishop/432_logistic_regression.md) | 5 | 7 |
| [4.3.3 Iterative reweighted least squares](pattern_recognition_machine_learning_cbishop/433_iterative_reweighted_least_squares.md) | 6 | 9 |
| [4.3.4 Multiclass logistic regression](pattern_recognition_machine_learning_cbishop/434_multiclass_logistic_regression.md) | 5 | 8 |
| [Appendix C. Matrices](pattern_recognition_machine_learning_cbishop/appendix_c_matrices.md) | 19 | 23 |
| [Appendix D. Calculus of Variation](pattern_recognition_machine_learning_cbishop/appendix_d_calculus_of_variation.md) | 5 | 7 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="group-probability-statistics"></a>
### 📂 Probability & Statistics

<a id="nb-stat110_havard"></a>
### STAT110_Havard
<!-- key: stat110_havard -->
<!-- group: Probability & Statistics -->
`881 notes · 1,109 screenshots · 32 sections`

> This notebook explores foundational and advanced topics in probability and statistical inference, covering random variables, their distributions (discrete and continuous), expectation, variance, moment generating functions, and key theorems such as the Law of Large Numbers and Central Limit Theorem.
> Sổ tay này khám phá các chủ đề cơ bản và nâng cao trong lý thuyết xác suất và suy luận thống kê, bao gồm các biến ngẫu nhiên, các phân phối của chúng (rời rạc và liên tục), kỳ vọng, phương sai, hàm sinh moment, và các định lý quan trọng như Luật Số lớn và Định lý Giới hạn Trung tâm.

<details open>
<summary>📖 32 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](stat110_havard/_overview.md) | 0 | 1 |
| [Cheatsheet (nhờ Ai)](stat110_havard/cheatsheet_nh_ai.md) | 5 | 98 |
| [Lec 10: Expected Value](stat110_havard/lec_10_expected_value.md) | 34 | 41 |
| [Lec 11: Poisson Distribution](stat110_havard/lec_11_poisson_distribution.md) | 31 | 39 |
| [Lec 12: Discrete Vs](stat110_havard/lec_12_discrete_vs_continuous_the_uniform.md) | 42 | 49 |
| [Lec 13: Normal Distribution](stat110_havard/lec_13_normal_distribution.md) | 33 | 42 |
| [Lec 14: Location, Scale, Lotus](stat110_havard/lec_14_location_scale_lotus.md) | 41 | 47 |
| [Lec 15: Midterm Review](stat110_havard/lec_15_midterm_review.md) | 29 | 32 |
| [Lec 16: Exponential](stat110_havard/lec_16_exponential_distribution.md) | 19 | 25 |
| [Lec 17: Moment](stat110_havard/lec_17_moment_generating_functions.md) | 49 | 60 |
| [Lec 18: MGF Continued](stat110_havard/lec_18_mgf_continued.md) | 42 | 49 |
| [Lec 19: Joint, Conditional And](stat110_havard/lec_19_joint_conditional_and_marginal_distribution.md) | 38 | 41 |
| [Lec 1: Probability & Counting](stat110_havard/lec_1_probability_counting.md) | 17 | 17 |
| [Lec 20: Multinomial And Cauchy](stat110_havard/lec_20_multinomial_and_cauchy.md) | 31 | 44 |
| [Lec 21: Covariance & Correlation](stat110_havard/lec_21_covariance_correlation.md) | 31 | 38 |
| [Lec 22: Transformations & Convolution](stat110_havard/lec_22_transformations_convolution.md) | 22 | 28 |
| [Lec 23: Beta Distribution](stat110_havard/lec_23_beta_distribution.md) | 10 | 13 |
| [Lec 24: Gamma Distribution & Poisson](stat110_havard/lec_24_gamma_distribution_poisson.md) | 24 | 24 |
| [Lec 25: Order Statistic &](stat110_havard/lec_25_order_statistic_conditional_expectation.md) | 27 | 31 |
| [Lec 26 Conditional](stat110_havard/lec_26_conditional_expectation.md) | 30 | 33 |
| [Lec 27: Conditional](stat110_havard/lec_27_conditional_expectation_given_an_rv.md) | 26 | 36 |
| [Lec 28: Inequalities](stat110_havard/lec_28_inequalities.md) | 19 | 21 |
| [Lec 29: Law Of Large Numbers &](stat110_havard/lec_29_law_of_large_numbers_law_of_central_limit.md) | 35 | 36 |
| [Lec 2: Story Proofs,](stat110_havard/lec_2_story_proofs_axioms_of_probability.md) | 23 | 23 |
| [Lec 30: Chi-square, Student-t,](stat110_havard/lec_30_chi_square_student_t_multi_variate_gaussian.md) | 21 | 22 |
| [Lec 3: Birthday Problem,](stat110_havard/lec_3_birthday_problem_properties_of_probability.md) | 21 | 23 |
| [Lec 4: Conditional Probability](stat110_havard/lec_4_conditional_probability.md) | 26 | 26 |
| [Lec 5: Conditional Probability,](stat110_havard/lec_5_conditional_probability_law_of_total_probability.md) | 31 | 35 |
| [Lec 6: Monty Hall, Simpson's](stat110_havard/lec_6_monty_hall_simpsons_paradox.md) | 23 | 23 |
| [Lec 7: Gambler's Ruin &](stat110_havard/lec_7_gamblers_ruin_random_variables.md) | 29 | 35 |
| [Lec 8: Random Variables &](stat110_havard/lec_8_random_variables_their_distributions.md) | 32 | 36 |
| [Lec 9: Expectation, Indicator](stat110_havard/lec_9_expectation_indicator_random_variables_linearity.md) | 40 | 41 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-statistical_inference_casella"></a>
### Statistical Inference - Casella
<!-- key: statistical_inference_casella -->
<!-- group: Probability & Statistics -->
<!-- videos: [{"url":"https://www.youtube.com/watch?v=UmyowzIGpGE","title":"Large-Sample Binomial Tests","videoId":"UmyowzIGpGE","uploadedAt":1788452614121},{"url":"https://www.youtube.com/watch?v=UO_2KJVR6fY","title":"Tại sao nghịch đảo Score Test ra khoảng tin cậy cho p?","videoId":"UO_2KJVR6fY","uploadedAt":1790101523675},{"url":"https://www.youtube.com/watch?v=qi2c2LvaefU","title":"Vì sao dùng √λ tốt hơn S cho khoảng tin cậy Poisson?","videoId":"qi2c2LvaefU","uploadedAt":1790183894478},{"url":"https://www.youtube.com/watch?v=Z_OW_2fvLbE","title":"Làm sao xây dựng Generalized Wald Test từ M-estimator?","videoId":"Z_OW_2fvLbE","uploadedAt":1788902153576},{"url":"https://www.youtube.com/watch?v=nC7WkJULeTs","title":"Thế nào là point estimation, confidence interval và hypothesis testing","videoId":"nC7WkJULeTs","uploadedAt":1790004244242},{"url":"https://www.youtube.com/watch?v=OcJDysX87L0","title":"Cách đảo ngược acceptance region thành khoảng tin cậy cho μ?","videoId":"OcJDysX87L0","uploadedAt":1790009733415},{"url":"https://www.youtube.com/watch?v=beyWo5KCi6c","title":"Tại sao [h(θ̂) - h(θ)] / √Var^(h(θ̂)) hội tụ về N(0,1)?","videoId":"beyWo5KCi6c","uploadedAt":1789149772425},{"url":"https://www.youtube.com/watch?v=RBcsZYaHM-Q","title":"Vì Sao Kỳ Vọng Của Score Statistic E_θ[S(θ)] Bằng 0?","videoId":"RBcsZYaHM-Q","uploadedAt":1788566520328},{"url":"https://www.youtube.com/watch?v=t5L8jQeG_nU","title":"Cách lập phương trình bậc hai tìm khoảng tin cậy Binomial Score?","videoId":"t5L8jQeG_nU","uploadedAt":1789746141654}] -->
<!-- videoIdeas: [{"title":"Bản chất Neyman-Pearson: LRT thu nhỏ về hai điểm","score":83,"noteTitle":"Định lý Neyman-Pearson"},{"title":"Trực giác Neyman-Pearson: Nghệ thuật xài hết ngân sách rủi ro","score":95,"noteTitle":"Định lý Neyman-Pearson"},{"title":"Bí mật đằng sau tính liên tục phải của hàm CDF","score":89,"noteTitle":"Hàm phân bố tích lũy của X"},{"title":"Chứng minh Cauchy-Schwarz trong xác suất bằng tam thức bậc hai","score":85,"noteTitle":"Ước lượng không chệch tốt nhất duy nhất"},{"title":"Bí quyết chứng minh tính duy nhất của ước lượng không chệch tốt nhất","score":88,"noteTitle":"Ước lượng không chệch tốt nhất duy nhất"},{"title":"Tại sao lại chia cho ước lượng phương sai?","score":72,"noteTitle":"Chia ước lượng phương sai"},{"title":"Mẹo tính kỳ vọng Log-normal không cần tích phân","score":88,"noteTitle":"Đạo hàm PDF Log-normal"},{"title":"Nguồn gốc thừa số 1/x trong PDF Log-normal","score":80,"noteTitle":"Đạo hàm PDF Log-normal"},{"title":"Máy lọc Rao-Blackwell: Có thể lọc hai lần để giảm phương sai?","score":88,"noteTitle":"Ước lượng không chệch duy nhất"},{"title":"Khi Cramér-Rao bất lực: Làm sao tìm ra ước lượng tốt nhất?","score":82,"noteTitle":"Ước lượng không chệch duy nhất"},{"title":"Cách tìm PMF của Y = n - X từ không gian mẫu","score":78,"noteTitle":"Chứng minh PMF Binomial"},{"title":"Bản chất đằng sau công thức phân phối Nhị thức","score":88,"noteTitle":"Chứng minh PMF Binomial"},{"title":"Bayes vs MLE: Đâu là ước lượng tốt hơn khi mẫu nhỏ?","score":86,"noteTitle":"So sánh Risk Function Estimator"},{"title":"Chứng minh tham số θ của Cauchy là Median bằng tích phân arctan","score":86,"noteTitle":"Phân phối Cauchy: Median θ"},{"title":"Hiểu bản chất Median qua cặp đôi CDF và Inverse CDF","score":82,"noteTitle":"Phân phối Cauchy: Median θ"},{"title":"Nghịch lý Poisson: Khi cả X̄ và S² cùng là ước lượng không chệch","score":86,"noteTitle":"Ước lượng không chệch Poisson"},{"title":"Chứng minh Lehmann-Scheffé bằng Adam's Law","score":92,"noteTitle":"Ước lượng không chệch tốt nhất"},{"title":"Tại sao E(X) là con số dự đoán tốt nhất?","score":90,"noteTitle":"EX: Giá trị dự đoán tốt nhất"},{"title":"Nghịch lý mẫu vô hạn trong thống kê thực tế","score":78,"noteTitle":"Khái niệm hội tụ"},{"title":"Bí quyết chứng minh tính nhất quán: Từ Chebyshev đến Var tiến về 0","score":85,"noteTitle":"Tính nhất quán của phương sai mẫu"},{"title":"Bí quyết kéo lùi nghịch ảnh để tính P(Y in A)","score":82,"noteTitle":"Xác suất của biến đổi ngẫu nhiên"},{"title":"Khi nào tung đồng xu biến thành đường cong hình chuông?","score":88,"noteTitle":"Phân phối chuẩn xấp xỉ phân phối"},{"title":"Hội tụ hầu chắc chắn (Almost Surely) trong Luật số lớn","score":82,"noteTitle":"Luật số lớn mạnh"},{"title":"Delta Method Bậc Hai: Khi Phân Phối Chuẩn Hóa Chi-Square","score":88,"noteTitle":"Delta method bậc hai"},{"title":"Bẫy Ký Hiệu Phân Phối Mũ: Kỳ Vọng Là λ Hay 1/λ?","score":85,"noteTitle":"Giá trị kỳ vọng phân phối mũ"},{"title":"Từ Poisson Đến Exponential: Bản Chất Của Thời Gian Chờ","score":92,"noteTitle":"Giá trị kỳ vọng phân phối mũ"},{"title":"Statistic là Biến ngẫu nhiên, không phải một con số","score":82,"noteTitle":"Statistic và phân phối lấy mẫu"},{"title":"A và B độc lập thì phần bù có độc lập không?","score":85,"noteTitle":"Độc lập biến cố và phần bù"},{"title":"Bản chất công thức Nhị thức âm: Khóa vị trí chốt sổ","score":92,"noteTitle":"Lập luận PMF nhị thức âm"},{"title":"Từ PMF sang Likelihood: Cú lật ngược biến số và tham số","score":81,"noteTitle":"Lập luận PMF nhị thức âm"},{"title":"Phân biệt Phương sai Mẫu và Phương sai của Trung bình Mẫu","score":88,"noteTitle":"Phân phối và biến động trung bình mẫu"},{"title":"Nguồn gốc Thống kê t: Khi Phương sai Quần thể là Ẩn số","score":83,"noteTitle":"Phân phối và biến động trung bình mẫu"},{"title":"Có cần tính ma trận Hessian để chứng minh MLE?","score":75,"noteTitle":"Hessian log likelihood chuẩn"},{"title":"Tại sao Bayes Estimator lại là kỳ vọng hậu nghiệm (Posterior Mean)?","score":86,"noteTitle":"Lý thuyết và Ước lượng Bayesian"},{"title":"Credible Interval vs Confidence Interval: Đâu mới là khoảng xác suất thực sự?","score":93,"noteTitle":"Lý thuyết và Ước lượng Bayesian"},{"title":"Covariance = 0 Nghĩa Là Độc Lập: Đặc Quyền Riêng Của Biến Chuẩn","score":90,"noteTitle":"Hiệp phương sai Độc lập Biến Chuẩn"},{"title":"Độc Lập Từng Cặp Suy Ra Độc Lập Vector: Phép Màu Của Gaussian Vector","score":82,"noteTitle":"Hiệp phương sai Độc lập Biến Chuẩn"},{"title":"Khi nào khoảng HPD của Bayes trùng với Likelihood Region?","score":89,"noteTitle":"Vùng HPD và Likelihood"},{"title":"Bản chất hình học của vùng HPD: Vì sao cắt ngang cho khoảng ngắn nhất?","score":86,"noteTitle":"Vùng HPD và Likelihood"},{"title":"Bản chất toán học của Thống kê Đủ: Vì sao theta biến mất?","score":85,"noteTitle":"Định nghĩa Thống kê Đầy đủ"},{"title":"Bản chất thuật toán EM: Chia để trị bài toán MLE","score":78,"noteTitle":"Thuật toán EM"},{"title":"Bản chất chuẩn hóa Z qua họ Location-Scale","score":88,"noteTitle":"Phân phối chuẩn hóa Z"},{"title":"Bản chất hình học của họ phân phối Location-Scale","score":78,"noteTitle":"Xây dựng Family Phân phối Location/Scale"},{"title":"Chặn dưới Cramer-Rao: Giới hạn tối thượng của ước lượng","score":80,"noteTitle":"Bất đẳng thức Cramer-Rao"},{"title":"Cạm bẫy đổi thứ tự đạo hàm - tích phân trong Cramer-Rao","score":85,"noteTitle":"Bất đẳng thức Cramer-Rao"},{"title":"Hàm PDF có thể lớn hơn 1 không? Điều kiện hợp lệ của PMF và PDF","score":78,"noteTitle":"Điều kiện hợp lệ PMF/PDF"},{"title":"Hiểu bản chất Hội tụ hầu chắc qua ví dụ s + s^n","score":86,"noteTitle":"Hội tụ hầu chắc"},{"title":"Phân phối tiệm cận của 1/X̄ qua Phương pháp Delta","score":84,"noteTitle":"Phương pháp Delta 1/X̄"},{"title":"Frequentist vs Bayesian: Tham số là cố định hay ngẫu nhiên?","score":85,"noteTitle":"Phương pháp Bayesian"},{"title":"Bản chất hàm Power: Một công thức, hai bộ mặt","score":87,"noteTitle":"Đặc điểm kiểm định giả thuyết"},{"title":"Unbiased Test: Khi sai số Loại 1 cực thấp vẫn là kiểm định vô dụng","score":93,"noteTitle":"Đặc điểm kiểm định giả thuyết"},{"title":"Cực trị bị chặn trong LRT: Khi nào MLE rơi vào biên?","score":86,"noteTitle":"Kiểm định LRT Phân phối Chuẩn"},{"title":"Từ quy tắc LRT λ ≤ c đến Z-test: Bí mật đổi chiều và ngưỡng c'","score":84,"noteTitle":"Kiểm định LRT Phân phối Chuẩn"},{"title":"Kiểm tra Độc lập Giữa các Vector Ngẫu nhiên","score":82,"noteTitle":"Độc lập vector qua PDF chung"},{"title":"Tìm MLE không cần đạo hàm","score":93,"noteTitle":"Tìm MLE không đạo hàm"},{"title":"Vì sao kết quả của argmax lại là một Estimator?","score":82,"noteTitle":"Tìm MLE không đạo hàm"},{"title":"Khi 2 kiểm định một phía tạo thành LRT hai phía","score":78,"noteTitle":"Quan hệ UIT-LRT hai phía"},{"title":"Bí thuật khử tham số trong Fisher's Exact Test","score":92,"noteTitle":"Kiểm định chính xác Fisher"},{"title":"Định lý Phân rã có thực sự cần mẫu i.i.d?","score":86,"noteTitle":"Kiểm định chính xác Fisher"},{"title":"Chứng minh xác suất tại một điểm bằng 0","score":92,"noteTitle":"Chứng minh P(X=x)=0"},{"title":"Vì sao kiểm định hai phía không có UMP test?","score":90,"noteTitle":"Test mức alpha và kích thước"},{"title":"Level alpha vs Size alpha: Khác nhau ở đâu?","score":86,"noteTitle":"Test mức alpha và kích thước"},{"title":"Chiến lược thu hẹp không gian: Từ UMVUE đến Unbiased Test","score":86,"noteTitle":"Kiểm định, ước lượng và MSE"},{"title":"Nguồn gốc công thức MSE = Var + Bias^2","score":90,"noteTitle":"Kiểm định, ước lượng và MSE"},{"title":"Sai lầm kinh điển trong EM: Thay x bằng E[X]?","score":90,"noteTitle":"Thuật toán EM"},{"title":"Nghịch lý con gà - quả trứng trong bước E của thuật toán EM","score":85,"noteTitle":"Thuật toán EM"},{"title":"Ngưỡng c trong LRT: Khi nào bạn 'dễ tính' hay 'khắt khe' với H0?","score":90,"noteTitle":"Ngưỡng bác bỏ LRT"},{"title":"Mẹo cộng trừ x̄: Vì sao số hạng chéo luôn biến mất?","score":78,"noteTitle":"Ngưỡng bác bỏ LRT"},{"title":"Bí mật hàm sinh mô-men đằng sau CLT","score":75,"noteTitle":"CLT - Định lý giới hạn trung tâm "},{"title":"Tại sao lại có căn n trong công thức CLT?","score":86,"noteTitle":"CLT - Định lý giới hạn trung tâm "},{"title":"Bản chất khoảng tin cậy: Tập hợp các giả thuyết không bị bác bỏ","score":92,"noteTitle":"Xây dựng tập tin cậy"},{"title":"Tính đơn điệu của Pivot: Khi nào tập tin cậy là một khoảng đóng?","score":80,"noteTitle":"Xây dựng tập tin cậy"},{"title":"Mẹo dùng định lý FTC để chứng minh tính đầy đủ (Completeness)","score":89,"noteTitle":"Thống kê đầy đủ đồng nhất"},{"title":"Đối ngẫu Union-Intersection vs Intersection-Union Test","score":90,"noteTitle":"Phương pháp hợp-giao và giao-hợp"},{"title":"Cạm bẫy của Thống kê Đủ","score":85,"noteTitle":"Hạn chế Nguyên lý Thống kê Đủ"},{"title":"Bản chất hàm mất mát trong ước lượng khoảng","score":84,"noteTitle":"Hàm mất mát ước lượng khoảng"},{"title":"Xác suất bao phủ sai (False Coverage) là gì?","score":86,"noteTitle":"Định lý 9.3.5: UMA Confidence Set"},{"title":"Nghịch đảo UMP Test tạo ra khoảng UMA","score":90,"noteTitle":"Định lý 9.3.5: UMA Confidence Set"},{"title":"Nhóm biến đổi 2 phần tử và phép đối xứng qua trục","score":78,"noteTitle":"Xác minh nhóm biến đổi"},{"title":"Likelihood Principle: Hai thí nghiệm khác biệt, chung một kết luận?","score":88,"noteTitle":"Các nguyên lý nén dữ liệu"},{"title":"Bản chất của nén dữ liệu trong thống kê qua đẳng thức T(x) = T(y)","score":82,"noteTitle":"Các nguyên lý nén dữ liệu"},{"title":"Ước lượng nhị thức khi cả k và p đều chưa biết","score":83,"noteTitle":"Phương pháp moment nhị thức"},{"title":"Khi toán học ra số âm: Cạm bẫy của phương pháp moment","score":88,"noteTitle":"Phương pháp moment nhị thức"},{"title":"Cộng số 0 để soán ngôi ước lượng tốt nhất","score":90,"noteTitle":"Đánh giá Ước lượng Không Chệch Tốt nhất"},{"title":"Cái bẫy của MSE với tham số tỉ lệ","score":88,"noteTitle":"Hạn chế của MSE"},{"title":"Bản chất kiểm định Bayesian: Xác suất hậu định chính là Test Statistic","score":88,"noteTitle":"Kiểm định giả thuyết Bayesian"},{"title":"Trung bình mẫu là một con số hay biến ngẫu nhiên?","score":85,"noteTitle":"Tính chất trung bình phương sai mẫu"},{"title":"Tại sao phương sai mẫu chia cho n - 1?","score":92,"noteTitle":"Tính chất trung bình phương sai mẫu"},{"title":"Đồng phân bố nhưng không độc lập: Cạm bẫy Marginal và Conditional","score":90,"noteTitle":"Đồng phân bố nhưng không độc lập"},{"title":"Nguyên lý điều kiện (Conditionality Principle) qua bài toán tung đồng xu","score":82,"noteTitle":"Nguyên lý điều kiện"},{"title":"Vì sao tính phương sai chính xác của Odds là 'vô vọng'?","score":91,"noteTitle":"Phương sai Tỷ lệ Odd"},{"title":"Tính phương sai của Odds bằng Delta Method","score":86,"noteTitle":"Phương sai Tỷ lệ Odd"},{"title":"Mẹo tạo đại lượng chốt từ phân phối mũ sang Chi-bình phương","score":85,"noteTitle":"Đại lượng chốt phân phối mũ"},{"title":"Ước lượng phương sai: Vì sao không chệch chưa phải tối ưu?","score":88,"noteTitle":"Rủi ro phương sai chuẩn"},{"title":"Mẹo nhân thêm z biến tích phân bất khả thi thành cực dễ","score":85,"noteTitle":"Kỳ vọng và Phương sai Z"},{"title":"Kỹ thuật tách z² để chứng minh Var(Z) = 1","score":88,"noteTitle":"Kỳ vọng và Phương sai Z"},{"title":"Mẹo giải bài toán hội tụ xác suất của giá trị Max","score":87,"noteTitle":"X(n) hội tụ xác suất"},{"title":"Tắc kè hoa phân phối Beta","score":84,"noteTitle":"Phân phối Beta và F"},{"title":"Đừng học vẹt Tích phân từng phần: Nhớ trọn đời từ Quy tắc nhân đạo hàm","score":82,"noteTitle":"Hàm Gamma và Tính chất"},{"title":"Hàm Gamma: Cầu nối từ tích phân suy rộng đến giai thừa (n-1)!","score":88,"noteTitle":"Hàm Gamma và Tính chất"},{"title":"Mẹo Biến Cố Đối: Bí Quyết Xử Lý Bài Toán 'Ít Nhất Một'","score":88,"noteTitle":"Xác suất ít nhất một 6"},{"title":"Mẹo tìm Pivotal Quantity: Trừ cho Location, Chia cho Scale","score":88,"noteTitle":"Đại lượng then chốt và họ phân phối"},{"title":"Bản chất của Pivotal Quantity trong khoảng tin cậy","score":85,"noteTitle":"Đại lượng then chốt và họ phân phối"},{"title":"Bản chất toán học của Định lý Factorization (Chiều đủ)","score":88,"noteTitle":"Định lý Factorization: Điều kiện đủ"},{"title":"Bản chất Định lý Ánh xạ Liên tục","score":84,"noteTitle":"Định lý ánh xạ liên tục"},{"title":"Bản chất hình học của hệ số 1/σ trong họ Location-Scale","score":88,"noteTitle":"Phân phối TB mẫu Location-Scale"},{"title":"Bảo toàn tính i.i.d khi chuẩn hóa mẫu ngẫu nhiên Location-Scale","score":82,"noteTitle":"Phân phối TB mẫu Location-Scale"},{"title":"Khoảng tin cậy bằng phương pháp số","score":86,"noteTitle":"Khoảng tin cậy số"},{"title":"Bản chất của khoảng tin cậy: Tập hợp các giả thuyết không bị bác bỏ","score":90,"noteTitle":"Mối quan hệ Test Tập tin cậy"},{"title":"Từ Uniform sang Exponential: Tuyệt chiêu tính kỳ vọng E[-log(X)]","score":88,"noteTitle":"LOTUS và tích phân từng phần"},{"title":"Nguồn gốc công thức tích phân từng phần từ đạo hàm tích","score":78,"noteTitle":"LOTUS và tích phân từng phần"},{"title":"Bẫy biến rời rạc: Vì sao không thể lấy đúng mức ý nghĩa alpha?","score":88,"noteTitle":"Ngưỡng k(p0) kiểm định mức alpha"},{"title":"Chứng minh MSE = Var + Bias² trong 3 phút","score":90,"noteTitle":"Ưu điểm của MSE"},{"title":"Bí Quyết Nhớ Công Thức Phân Phối Chuẩn Từ Stat 110","score":86,"noteTitle":"Tích phân Gauss"},{"title":"Hàm lực kiểm định Power Function: Vì sao luôn tăng khi tham số dịch chuyển?","score":86,"noteTitle":"Hàm lực β(θ) phân phối chuẩn"},{"title":"Họ vị trí - tỉ lệ (Location-Scale): Bí mật đằng sau phép chuẩn hóa","score":79,"noteTitle":"Hàm lực β(θ) phân phối chuẩn"},{"title":"Tại sao lại đảo ngược kiểm định để tìm khoảng tin cậy?","score":84,"noteTitle":"Đảo ngược test ra khoảng tin cậy"},{"title":"Nghịch lý chuỗi máy đánh chữ: Hội tụ xác suất nhưng không hầu chắc","score":90,"noteTitle":"Hội tụ xác suất không hầu chắc"},{"title":"Likelihood Principle: Đồng xu có quan tâm bạn muốn dừng lúc nào?","score":90,"noteTitle":"Quy tắc Dừng: Thông tin dư thừa"},{"title":"Mẹo đặt biến giả W = V trong phép đổi biến ngẫu nhiên","score":85,"noteTitle":"Đạo hàm phân phối t-Student"},{"title":"Tuyệt chiêu nhận diện nhân (Kernel) phân phối Gamma","score":88,"noteTitle":"Đạo hàm phân phối t-Student"},{"title":"Trực giác chứng minh tính bất biến của MLE","score":88,"noteTitle":"Tính bất biến của MLE"},{"title":"Ước lượng Bayes chuẩn: Giằng co giữa niềm tin và dữ liệu","score":92,"noteTitle":"Ước lượng Bayes phân phối chuẩn"},{"title":"Bản chất tham số: Cổ điển vs Bayesian","score":86,"noteTitle":"Ước lượng Bayes phân phối chuẩn"},{"title":"Mẹo Kernel: Tìm Posterior không cần tính tích phân","score":82,"noteTitle":"Ước lượng Bayes phân phối chuẩn"},{"title":"Mẹo xác định cận tích phân chập cho biến ngẫu nhiên dương","score":88,"noteTitle":"Giới hạn tích phân chập"},{"title":"Mối liên hệ bất ngờ giữa độ dài khoảng tin cậy và xác suất phủ (Định lý Pratt)","score":90,"noteTitle":"Chứng minh kỳ vọng độ dài C(X)"},{"title":"Bí quyết Complete Likelihood: Thêm biến ẩn để giải toán dễ hơn","score":82,"noteTitle":"Likelihood Dữ liệu Thiếu/Đủ"},{"title":"Bản chất trực quan của hai biến cố độc lập","score":75,"noteTitle":"Sự kiện độc lập thống kê"},{"title":"Bản chất toán học của hàm Q trong thuật toán EM","score":86,"noteTitle":"Tính toán E-step EM"},{"title":"Mẹo rút gọn điều kiện phức tạp trong E-step","score":78,"noteTitle":"Tính toán E-step EM"},{"title":"Bản chất hình học của Scale Parameter","score":82,"noteTitle":"Họ phân phối Scale"},{"title":"Gỡ rối mức ý nghĩa α trong định lý Karlin-Rubin","score":82,"noteTitle":"Kiểm định UMP theo Karlin-Rubin"},{"title":"Nguồn gốc công thức điểm tới hạn trong kiểm định Z","score":86,"noteTitle":"Kiểm định UMP theo Karlin-Rubin"},{"title":"Căn bậc hai của S²: Vì sao tính vững được giữ nguyên còn tính không chệch lại mất?","score":88,"noteTitle":"Tính nhất quán và chệch S"},{"title":"Vì sao kiểm định hai phía không thể có UMP test?","score":86,"noteTitle":"Không tồn tại UMP test"},{"title":"Hàm lực lượng chữ U: Sự đánh đổi của kiểm định hai phía","score":90,"noteTitle":"Không tồn tại UMP test"},{"title":"Tại sao sai số bình phương thất bại khi ước lượng phương sai? (Stein Loss)","score":92,"noteTitle":"Ước lượng phương sai: Stein Loss"},{"title":"MSE thực chất chỉ là một trường hợp riêng của Risk Function","score":88,"noteTitle":"Ước lượng phương sai: Stein Loss"},{"title":"Ràng buộc đối xứng của hàm ước lượng qua hai nguyên lý Equivariance","score":85,"noteTitle":"Ước lượng tham số p"},{"title":"Restricted MLE trong LRT: Khi nào Likelihood Ratio bằng 1?","score":83,"noteTitle":"P-value một phía của LRT"},{"title":"Bản chất toán học của P-value: Tại sao Sup luôn đạt tại biên?","score":92,"noteTitle":"P-value một phía của LRT"},{"title":"Sai Lầm Khi Đánh Giá Credible Set Bằng Coverage Probability","score":88,"noteTitle":"Sai mục đích Credible Set"},{"title":"Cái bẫy Cramér-Rao: Khi nào không được tráo đổi đạo hàm và tích phân?","score":90,"noteTitle":"Giới hạn Định lý Cramer-Rao"},{"title":"Ước lượng phương sai đạt chặn Cramér-Rao: Cạm bẫy tham số μ","score":86,"noteTitle":"Ước lượng σ² tốt nhất"},{"title":"Tính bất biến của MLE trong trường hợp hàm 1-1","score":88,"noteTitle":"Chứng minh tính bất biến MLE"},{"title":"Bí mật triệt tiêu: Vì sao thông tin Fisher tăng tuyến tính theo n?","score":87,"noteTitle":"Bất đẳng thức Cramer-Rao iid"},{"title":"Tuyệt chiêu nhận diện hạt nhân để tính moment phân phối Beta","score":85,"noteTitle":"Tính moment phân phối Beta"},{"title":"Bước nhảy CDF: Cầu nối trực quan giữa PMF và xác suất khoảng","score":85,"noteTitle":"Định nghĩa và ứng dụng PMF"},{"title":"Bí mật đằng sau hệ số 1/sigma khi biến đổi hàm mật độ","score":88,"noteTitle":"Biến đổi hàm mật độ"},{"title":"Mẹo tránh ma trận Hessian khi tìm MLE phân phối chuẩn","score":86,"noteTitle":"MLEs phân phối chuẩn"},{"title":"Nghịch đảo kiểm định: Bản chất của Tautology Theorem","score":83,"noteTitle":"UMA từ kiểm định UMP"},{"title":"Từ UMP đến UMA: Tối đa lực kiểm định nghĩa là gì?","score":87,"noteTitle":"UMA từ kiểm định UMP"},{"title":"Bí quyết triệt tiêu θ trong MSE của ước lượng bất biến","score":92,"noteTitle":"MSE ước lượng bất biến"},{"title":"Bản chất nguyên lý Equivariance qua câu chuyện đổi thước đo","score":85,"noteTitle":"MSE ước lượng bất biến"},{"title":"Xác suất có điều kiện: Vũ trụ thu hẹp và 3 tiên đề Kolmogorov","score":88,"noteTitle":"Tiên đề xác suất có điều kiện"},{"title":"Bí quyết vi phân hàm tích lũy khi Y = X^2","score":88,"noteTitle":"Đạo hàm PDF của Y=X^2"},{"title":"Sức mạnh của Joint MLE: Vì sao ước lượng đồng thời lại xịn hơn riêng lẻ?","score":90,"noteTitle":"MLE Tham số β, τ"},{"title":"Độc lập nhưng không cùng phân phối: Cạm bẫy i.i.d. khi lập Likelihood","score":86,"noteTitle":"MLE Tham số β, τ"},{"title":"Vì sao rút không hoàn lại vẫn được coi là độc lập?","score":90,"noteTitle":"Độc lập gần đúng khi N lớn"},{"title":"Bản chất của biến ngẫu nhiên: Xử lý không gian mẫu 2^50","score":85,"noteTitle":"Tính xác suất biến ngẫu nhiên"},{"title":"Tại sao biến liên tục phải dùng P(X in A) thay vì P(X = x)?","score":79,"noteTitle":"Tính xác suất biến ngẫu nhiên"},{"title":"Thống kê phụ trợ nằm trong thống kê đủ: Cú lừa trực giác","score":90,"noteTitle":"Đủ tối thiểu và phụ trợ"},{"title":"Dùng Credible Interval làm Confidence Interval: Thảm họa độ phủ về 0","score":90,"noteTitle":"Độ phủ khoảng đáng tin"},{"title":"Trực quan hóa Thống kê đủ tối tiểu: Tại sao lại là phân hoạch thô nhất?","score":92,"noteTitle":"Thống kê đủ tối tiểu"},{"title":"Điều kiện dấu bằng Cramer-Rao từ góc nhìn Cauchy-Schwarz","score":85,"noteTitle":"Dấu bằng Cramer-Rao"},{"title":"Bản chất toán học của 'Cùng phân phối' (Identically Distributed)","score":85,"noteTitle":"Định nghĩa biến phân phối đồng nhất"},{"title":"Tính xác suất cho cả mẫu bằng Joint PDF","score":85,"noteTitle":"Tính xác suất bằng Joint PDF"},{"title":"Bí quyết kiểm tra UMVUE: Thử cộng với ước lượng của số 0","score":86,"noteTitle":"Thống kê đủ & Ước lượng tốt nhất"},{"title":"Rao-Blackwell bắt tay Completeness: Công thức săn lùng ước lượng vô địch","score":92,"noteTitle":"Thống kê đủ & Ước lượng tốt nhất"},{"title":"Khi chặn dưới Cramer-Rao sụp đổ: Nghịch lý Uniform(0, theta)","score":85,"noteTitle":"Thống kê đủ & Ước lượng tốt nhất"},{"title":"Bản chất của kiểm định giả thuyết dưới góc nhìn Decision Theory","score":86,"noteTitle":""},{"title":"Ước lượng Bayes có MSE phẳng: Tuyệt chiêu Minimax","score":84,"noteTitle":"MSE Bayes hằng số"},{"title":"Rút 4 lá hay rút 2 lá: Ảo giác không gian mẫu","score":88,"noteTitle":"Xác suất có điều kiện bốc Ách"},{"title":"Bản chất MSE: Sự giằng co giữa Bias và Variance","score":85,"noteTitle":"Độ lệch và MSE ước lượng"},{"title":"Bình phương phân phối Student t ra phân phối F","score":85,"noteTitle":"Tính chất phân phối F và t"},{"title":"Nghịch đảo của phân phối F vẫn là phân phối F","score":78,"noteTitle":"Tính chất phân phối F và t"},{"title":"Chặn dưới Cramer-Rao: Khi nào cận dưới không thể đạt tới?","score":90,"noteTitle":"Giới hạn Cramer-Rao phương sai chuẩn"},{"title":"Bản chất của tính đầy đủ (Completeness) trong thống kê","score":90,"noteTitle":"Tính đầy đủ và ước lượng"},{"title":"Bản chất của Thống kê mẫu: Vì sao X̄ là một hàm số?","score":88,"noteTitle":"Thống kê mẫu cơ bản"},{"title":"Đường tắt tính LRT bằng Thống kê đủ","score":88,"noteTitle":"Thống kê đủ và LRT"},{"title":"Bản chất thật sự của Phương pháp Moment","score":84,"noteTitle":"Phương pháp Moment"},{"title":"Bản chất toán học của Hàm sinh Moment (MGF)","score":86,"noteTitle":"Phương pháp Moment"},{"title":"Bản chất của 'Size α' trong kiểm định thống kê","score":80,"noteTitle":"Kiểm định tỉ số khả dĩ cỡ α"},{"title":"Vì sao không cần tính ngưỡng c trong LRT?","score":88,"noteTitle":"Kiểm định tỉ số khả dĩ cỡ α"},{"title":"Mẹo đặt biến phụ để chứng minh tích chập Z = X + Y","score":92,"noteTitle":"Công thức tích chập Z=X+Y"},{"title":"Hai giới hạn chết người của hàm sinh mô-men MGF","score":81,"noteTitle":"Công thức tích chập Z=X+Y"},{"title":"Biến đổi đa thức chứng minh thống kê đầy đủ cho phân phối nhị thức","score":86,"noteTitle":"Thống kê đầy đủ nhị thức"},{"title":"Phân biệt g(t) = 0 trên miền hỗ trợ và P(g(T) = 0) = 1","score":78,"noteTitle":"Thống kê đầy đủ nhị thức"},{"title":"Bản chất trực giác của giả định độc lập khi lấy mẫu","score":75,"noteTitle":"Giả định độc lập biến ngẫu nhiên"},{"title":"Cố định độ chệch: Khi bài toán MSE quy về phương sai","score":84,"noteTitle":"Ước lượng không chệch tốt nhất"},{"title":"Bí mật hàm hợp lý cảm ứng: Khi tính bất biến của MLE bị thử thách","score":88,"noteTitle":"Hàm hợp lý cảm ứng"},{"title":"Biến chuẩn: Khi trực giao hệ số tạo ra tính độc lập","score":88,"noteTitle":"Điều kiện độc lập tổ hợp Normal"},{"title":"Hiệp phương sai tổ hợp tuyến tính: Triệt tiêu tích chéo","score":78,"noteTitle":"Điều kiện độc lập tổ hợp Normal"},{"title":"Tại sao ước lượng Bayes lại lấy Posterior Mean?","score":89,"noteTitle":"MSE của ước lượng Bayes"},{"title":"Tham số cố định hay ngẫu nhiên? Trực giác trường phái Bayes","score":85,"noteTitle":"MSE của ước lượng Bayes"},{"title":"Đánh đổi Bias-Variance trong ước lượng Bayes","score":83,"noteTitle":"MSE của ước lượng Bayes"},{"title":"Biến đổi CDF rời rạc: Vì sao không ra Uniform?","score":90,"noteTitle":"Lật CDF thống kê rời rạc"},{"title":"Cạm bẫy lật CDF tìm khoảng tin cậy cho biến rời rạc","score":85,"noteTitle":"Lật CDF thống kê rời rạc"},{"title":"Mẹo tính kỳ vọng và phương sai dạng biến đổi vị trí - tỉ lệ","score":88,"noteTitle":"Kỳ vọng, phương sai biến đổi tuyến tính"},{"title":"Từ khoảng tin cậy đến hàm quyết định C(x)","score":80,"noteTitle":"Hàm quyết định C(x)"},{"title":"Biến đổi 1-1 của Thống kê đủ: Vì sao thông tin không mất?","score":82,"noteTitle":"Thống kê đủ và hàm một-một"},{"title":"Vượt qua 0-1 Loss: Khi lỗi loại I phụ thuộc vào khoảng cách sai lệch","score":88,"noteTitle":"Hàm tổn thất kiểm định"},{"title":"Vì Sao Tham Số μ Biến Mất Khỏi Hàm Rủi Ro?","score":82,"noteTitle":"Rủi ro ước lượng khoảng chuẩn"},{"title":"Thiết Kế Hàm Loss Cho Ước Lượng Khoảng","score":88,"noteTitle":"Rủi ro ước lượng khoảng chuẩn"},{"title":"Đại lượng then chốt (Pivot): Cách 'triệt tiêu' tham số khi tính khoảng tin cậy","score":82,"noteTitle":"Xây dựng khoảng tin cậy"},{"title":"Nghịch đảo kiểm định LRT: Bản chất hình học của hai điểm cắt a và b","score":86,"noteTitle":"Xây dựng khoảng tin cậy"},{"title":"Ai mới là biến ngẫu nhiên trong Khoảng tin cậy?","score":94,"noteTitle":"Hàm mất mát và rủi ro"},{"title":"Khoảng tin cậy và sự đánh đổi phong cách Regularization","score":90,"noteTitle":"Hàm mất mát và rủi ro"},{"title":"Nghịch đảo CDF tìm khoảng tin cậy: Cẩn thận tính đơn điệu","score":85,"noteTitle":"Khoảng tin cậy xoay CDF"},{"title":"Mẹo tính kỳ vọng Gamma không cần giải tích phân","score":90,"noteTitle":"Giá trị kỳ vọng phân phối Gamma"},{"title":"Bản chất biến ngẫu nhiên: Tại sao sự kiện X=x thực chất là một tập con?","score":78,"noteTitle":"Thống kê đủ và phân phối"},{"title":"Trực giác Thống kê đủ qua trò chơi hai người truyền tin","score":88,"noteTitle":"Thống kê đủ và phân phối"},{"title":"Bất biến hình thức: Khi toán học phớt lờ ngữ cảnh vật lý","score":84,"noteTitle":"Nguyên lý Equivariance: Bất biến hình thức"},{"title":"Điểm chung bất ngờ giữa Sufficiency, Likelihood và Equivariance","score":80,"noteTitle":"Nguyên lý Equivariance: Bất biến hình thức"},{"title":"Bản chất của khoảng tin cậy: Đảo ngược một bài toán kiểm định","score":88,"noteTitle":"Phương pháp ước lượng khoảng"},{"title":"Vì sao p-value hợp lệ chỉ cần thỏa P(p ≤ α) ≤ α?","score":78,"noteTitle":"P-value và phân phối Uniform"},{"title":"Tại sao P-value dưới H0 lại có phân phối Uniform(0,1)?","score":85,"noteTitle":"P-value và phân phối Uniform"},{"title":"Nghịch lý ba tù nhân và cái bẫy trực giác 1/2","score":94,"noteTitle":"Bài toán ba tù nhân"},{"title":"Bẫy đổi biến 2 chiều: Cách xác định miền giá trị mới","score":82,"noteTitle":"Phân phối Range Ancillary"},{"title":"Tại sao Range là Ancillary Statistic?","score":88,"noteTitle":"Phân phối Range Ancillary"},{"title":"Bí mật đằng sau phép biến đổi -log(X): Từ Uniform ra Exponential","score":84,"noteTitle":"Phân phối của -log(X)"},{"title":"Bí quyết tìm khoảng tin cậy ngắn nhất bằng nhát cắt ngang","score":90,"noteTitle":"Đoạn ngắn nhất PDF đơn đỉnh"},{"title":"Mẹo tìm Credible Interval cho phân phối Gamma qua Chi-square","score":91,"noteTitle":"Khoảng tin cậy Poisson Gamma"},{"title":"Kỹ thuật Kernel: Tìm Posterior Poisson-Gamma không cần tính mẫu số","score":83,"noteTitle":"Khoảng tin cậy Poisson Gamma"},{"title":"Vì sao E(W|T) là Statistic: Bí mật của Thống kê Đủ","score":90,"noteTitle":"Định lý Rao-Blackwell"},{"title":"Cơ chế 'nâng cấp' ước lượng của Định lý Rao-Blackwell","score":85,"noteTitle":"Định lý Rao-Blackwell"},{"title":"Mối nối bất ngờ: Bản chất của kiểm định Likelihood Ratio (LRT) chính là UIT","score":76,"noteTitle":"Kiểm định Hợp-Giao và Giao-Hợp"},{"title":"Nghịch lý tên gọi UIT vs IUT: Vì sao H0 là Giao thì Bác bỏ lại là Hợp?","score":88,"noteTitle":"Kiểm định Hợp-Giao và Giao-Hợp"},{"title":"Tại sao kiểm định Giao - Hợp (IUT) không làm tăng sai lầm loại I?","score":78,"noteTitle":"Định lý cỡ của IUT"},{"title":"Bản chất trực giác của Thống kê đủ (Sufficient Statistic)","score":86,"noteTitle":"Định nghĩa Thống kê đủ"},{"title":"Bí mật triệt tiêu tham số theta của Thống kê đủ","score":88,"noteTitle":"Thống kê đủ loại bỏ θ"},{"title":"Ẩn số σ² biến đi đâu khi chuẩn hóa Size α trong kiểm định t hai phía?","score":80,"noteTitle":"Kiểm định hợp-giao cỡ α"},{"title":"Kiểm định Hợp-Giao: Tại sao 'Giao' của giả thuyết lại thành 'Hợp' của miền bác bỏ?","score":88,"noteTitle":"Kiểm định hợp-giao cỡ α"},{"title":"Bản chất đại số tuyến tính của điều kiện cực đại hàm 2 biến","score":90,"noteTitle":"Điều kiện đủ cực đại"},{"title":"Nguyên lý Điều kiện: Thí nghiệm bạn không chọn có ảnh hưởng đến kết luận?","score":86,"noteTitle":"Nguyên lý Điều kiện qua Thí nghiệm"},{"title":"Tại sao chặn trên của Z lại biến thành chặn dưới của mu?","score":92,"noteTitle":"Tối ưu độ dài khoảng tin cậy"},{"title":"Khoảng tin cậy thực chất là gì? Góc nhìn đảo ngược miền chấp nhận","score":85,"noteTitle":"Tối ưu độ dài khoảng tin cậy"},{"title":"Tại sao Trung bình mẫu và Phương sai mẫu lại là biến ngẫu nhiên?","score":85,"noteTitle":"Tính chất Trung bình & Phương sai mẫu"},{"title":"Sự kỳ diệu của phân phối chuẩn: Khi Trung bình mẫu và Phương sai mẫu độc lập","score":88,"noteTitle":"Tính chất Trung bình & Phương sai mẫu"},{"title":"Mẹo tìm thống kê đủ bằng Định lý Phân rã","score":88,"noteTitle":"Tìm Thống kê đủ Factorization"},{"title":"Bản chất tối ưu hoá của Likelihood Ratio Test","score":84,"noteTitle":"Kiểm định Tỷ số Hợp lý"},{"title":"Chứng minh định lý Rao-Blackwell qua Luật phân tách phương sai","score":82,"noteTitle":"Định lý Rao-Blackwell"},{"title":"Cái bẫy điều kiện trong định lý Rao-Blackwell: Vì sao T phải là thống kê đủ?","score":90,"noteTitle":"Định lý Rao-Blackwell"},{"title":"Vì sao ước lượng không chệch chưa chắc đã tối ưu?","score":87,"noteTitle":"Ước lượng Tốt: Phương sai, Độ chệch"},{"title":"Cramér-Rao thực chất chỉ là Cauchy-Schwarz","score":88,"noteTitle":"Chứng minh Cramer-Rao từ Cauchy-Schwarz"},{"title":"Mẹo chứng minh kỳ vọng Score Function bằng 0","score":82,"noteTitle":"Chứng minh Cramer-Rao từ Cauchy-Schwarz"},{"title":"Mô hình hóa số đếm Poisson với tham số phơi nhiễm (Exposure)","score":80,"noteTitle":"Tỷ lệ Poisson đa"},{"title":"Hàm công suất lý tưởng và sự thống nhất hai loại sai lầm","score":85,"noteTitle":"Khái niệm hàm công suất kiểm định"},{"title":"Tại sao cải tiến ước lượng bắt buộc phải dùng thống kê đủ?","score":92,"noteTitle":"Điều kiện hóa thống kê không đủ"},{"title":"Ước lượng tham số phân phối chuẩn bằng phương pháp Moment","score":84,"noteTitle":"Phương pháp moment phân phối chuẩn"},{"title":"Story Proof: Tại sao tổng các phân phối Binomial lại là Binomial?","score":82,"noteTitle":"Ước lượng không chệch tốt nhất Binomial"},{"title":"Tuyệt chiêu Rao-Blackwell: Từ ước lượng 'ngớ ngẩn' đến ước lượng tốt nhất","score":88,"noteTitle":"Ước lượng không chệch tốt nhất Binomial"},{"title":"Mẫu IID: Đừng vội tính tích phân bội khi tính xác suất đồng thời","score":82,"noteTitle":"Xác suất mẫu độc lập đồng nhất"},{"title":"Nghịch lý Residual Plot và Thống kê Đủ","score":88,"noteTitle":"Dư lượng và nguyên lý đủ"},{"title":"Chứng minh phân phối của trung bình mẫu bằng hàm sinh mô-men","score":85,"noteTitle":"Phân phối trung bình mẫu"},{"title":"Vì sao ước lượng tốt nhất không thể tương quan với nhiễu?","score":90,"noteTitle":"Đặc điểm ước lượng không chệch tốt nhất"},{"title":"Bản chất tham số trong Bayes: Tại sao ước lượng lại là kỳ vọng Posterior?","score":90,"noteTitle":"Ước lượng Bayes Binomial"},{"title":"Mẹo tích phân nhận diện Kernel: Bí quyết tính Marginal Beta-Binomial","score":85,"noteTitle":"Ước lượng Bayes Binomial"},{"title":"Nghịch lý khi dùng định nghĩa để tìm thống kê đủ","score":84,"noteTitle":"Sử dụng định nghĩa thống kê đủ"},{"title":"Đối ngẫu hình học giữa Khoảng tin cậy C(x) và Vùng chấp nhận A(θ)","score":90,"noteTitle":"Mối quan hệ C(x) và A(θ)"},{"title":"Ý tưởng Satterthwaite: Khớp moment tìm bậc tự do hiệu dụng","score":88,"noteTitle":"Ước lượng bậc tự do Satterthwaite"},{"title":"Bản chất của Chi-bình-phương chia bậc tự do","score":83,"noteTitle":"Ước lượng bậc tự do Satterthwaite"},{"title":"Khi nào Bayes thắng MLE? Đọc hiểu qua đồ thị MSE","score":88,"noteTitle":"Chọn ước lượng Bayes MLE"},{"title":"Phân biệt Population Distribution và Sampling Distribution","score":75,"noteTitle":"Phân phối lấy mẫu"},{"title":"Tại sao hàm mật độ PDF bị chia cho sigma khi co giãn biến số?","score":85,"noteTitle":"Biến đổi PDF Location-Scale"},{"title":"Tại sao Sup Luôn Đạt Tại Biên Khi Kiểm Định Giả Thuyết?","score":91,"noteTitle":"Ảnh hưởng Θ0 trong kiểm định"},{"title":"Vì sao Rao-Blackwell bắt buộc cần Thống kê Đủ?","score":91,"noteTitle":"Rao-Blackwell và thống kê đủ"},{"title":"Bản chất tối ưu: Vì sao khoảng tin cậy t có kỳ vọng độ dài ngắn nhất?","score":85,"noteTitle":"Tối ưu hóa kỳ vọng độ dài"},{"title":"Cạm bẫy E(S) ≠ σ: Khi căn bậc hai phá vỡ tính không chệch","score":88,"noteTitle":"Tối ưu hóa kỳ vọng độ dài"},{"title":"Chi-bình phương thực chất là phân phối Gamma trá hình","score":75,"noteTitle":"Trường hợp Gamma đặc biệt"},{"title":"Bẫy tham số Rate vs Scale trong phân phối Mũ","score":85,"noteTitle":"Trường hợp Gamma đặc biệt"},{"title":"Bản chất trực quan của Tỉ số Khả năng Đơn điệu (MLR)","score":78,"noteTitle":"Định nghĩa Tỉ số Khả năng Đơn điệu"},{"title":"Mẹo tìm Complete Statistic siêu tốc bằng họ hàm mũ","score":85,"noteTitle":"Thống kê đầy đủ họ hàm mũ"},{"title":"Vì sao phân phối Cauchy đối xứng mà không có kỳ vọng bằng 0?","score":88,"noteTitle":"Đặc điểm phân phối Cauchy"},{"title":"Tại sao ném biến ngẫu nhiên vào CDF của chính nó lại ra Uniform(0,1)?","score":86,"noteTitle":"Biến đổi tích phân xác suất"},{"title":"Inverse Transform: Cách máy tính tạo ra mọi phân phối từ hàm rand()","score":90,"noteTitle":"Biến đổi tích phân xác suất"},{"title":"Kỹ thuật đảo ngược kiểm định để tìm khoảng tin cậy","score":82,"noteTitle":"Khoảng tin cậy không chệch"},{"title":"Joint PMF của phân phối đều rời rạc và bẫy điều kiện ẩn","score":80,"noteTitle":"Phân phối đều rời rạc"},{"title":"Tại sao kiểm định bằng thống kê đủ vẫn đạt UMP?","score":85,"noteTitle":"Chứng minh kiểm định UMP α"},{"title":"Thiết kế kiểm định LRT dựa trên Thống kê đủ","score":80,"noteTitle":"Thống kê đủ và kiểm định LRT"},{"title":"Ý nghĩa trực quan của Thống kê đủ (Sufficient Statistic)","score":86,"noteTitle":"Thống kê đủ và kiểm định LRT"},{"title":"Chứng minh phân phối của trung bình mẫu bằng hàm MGF","score":90,"noteTitle":"MGF trung bình mẫu"},{"title":"Ngộ nhận về mẫu S^2: Không chệch mọi nơi, nhưng phương sai thì kén chọn","score":88,"noteTitle":"Tính không chệch X̄ S^2"},{"title":"Nguồn gốc toán học của phân rã MSE = Phương sai + Chệch bình phương","score":87,"noteTitle":"Tính không chệch X̄ S^2"},{"title":"Bản chất ngẫu nhiên của khoảng tin cậy","score":90,"noteTitle":"Khái niệm xác suất bao phủ"},{"title":"Pivotal Quantity: Bí quyết triệt tiêu tham số","score":85,"noteTitle":"Khái niệm xác suất bao phủ"},{"title":"Phóng đại cực trị: Từ tiến về 1 đến phân phối Mũ","score":88,"noteTitle":"Hội tụ xác suất và phân phối"},{"title":"Story Proof: Đẳng thức chọn nhóm trưởng","score":92,"noteTitle":"Phương pháp tính kỳ vọng Binomial"},{"title":"Kỳ vọng Binomial: Sức mạnh của biến chỉ thị","score":86,"noteTitle":"Phương pháp tính kỳ vọng Binomial"},{"title":"Bản chất phân phối F: So sánh hai độ biến động","score":84,"noteTitle":"Phân phối F: Tỉ lệ phương sai"},{"title":"Nghịch đảo LRT để tạo Khoảng Tin cậy","score":85,"noteTitle":"LRT và Tập tin cậy"},{"title":"Bản chất xác suất của MSE: Tại sao lại cần kỳ vọng?","score":88,"noteTitle":"Sai số bình phương trung bình"},{"title":"Ước lượng số 0: Khái niệm kỳ lạ để tìm ước lượng tối ưu","score":80,"noteTitle":"Ước lượng không chệch của 0"},{"title":"Từ tích phân kỳ vọng bằng 0 đến hàm tuần hoàn chu kỳ 1","score":85,"noteTitle":"Ước lượng không chệch của 0"},{"title":"Equivariance: Bí quyết cắt đôi việc tìm Estimator","score":84,"noteTitle":"Lợi ích nguyên lí equivariance"},{"title":"Bản chất trực giác của Định lý Factorization","score":84,"noteTitle":"Định lý Factorization"},{"title":"Nghịch lý kiểm định: Khi thống kê 'quá đủ' làm sập Power","score":92,"noteTitle":""},{"title":"Triệt tiêu tham số trong p-value bằng thống kê đủ","score":82,"noteTitle":""},{"title":"Hàm CDF có thực sự xác định duy nhất mọi phân phối?","score":75,"noteTitle":"Borel Field và Hàm phân phối"},{"title":"Tìm miền bác bỏ LRT qua thống kê cực tiểu","score":82,"noteTitle":"Miền bác bỏ kiểm định tỉ số khả dĩ"},{"title":"CLT liệu có lỗi thời trước siêu máy tính?","score":84,"noteTitle":"Định lý Giới hạn Trung tâm"},{"title":"Bẫy phương sai hữu hạn của Định lý Giới hạn Trung tâm","score":90,"noteTitle":"Định lý Giới hạn Trung tâm"},{"title":"Trực giác đằng sau Kiểm định Tỉ số Hợp lý (LRT)","score":93,"noteTitle":"Nguyên lý Kiểm định tỉ số hợp lý"},{"title":"Phân biệt Miền chấp nhận và Khoảng tin cậy trên Đồ thị Tỷ số Hợp lý","score":90,"noteTitle":"Miền chấp nhận, khoảng tin cậy"},{"title":"MLE với tham số rời rạc: Khi không thể lấy đạo hàm","score":90,"noteTitle":"Binomial MLE K chưa biết"},{"title":"Khoảng tin cậy cho phương sai và cạm bẫy phân phối bất đối xứng","score":88,"noteTitle":"Khoảng tin cậy cho phương sai"},{"title":"Mối liên hệ giữa Kiểm định và Khoảng tin cậy qua Đại lượng trục","score":86,"noteTitle":"Khoảng tin cậy cho phương sai"},{"title":"Cách Likelihood Ratio Test 'thuần hóa' tham số gây nhiễu","score":84,"noteTitle":"LRT với tham số gây nhiễu"},{"title":"Vì sao kiểm định một phía đạt cực đại tại biên?","score":88,"noteTitle":"LRT với tham số gây nhiễu"},{"title":"Bí quyết tính MSE siêu tốc nhờ phân rã Bias-Variance","score":84,"noteTitle":"MSE của p^_mle"},{"title":"Tìm MLE cho phân phối Bernoulli bằng Log-Likelihood","score":78,"noteTitle":"MSE của p^_mle"},{"title":"Nghịch lý Conjugate Prior: Tiện tính toán hay phản bội niềm tin Bayes?","score":82,"noteTitle":"Gia đình liên hợp"},{"title":"Conjugate Prior: Biến tích phân Bayes thành phép cộng số liệu","score":88,"noteTitle":"Gia đình liên hợp"},{"title":"Bình phương phân phối chuẩn tắc ra cái gì?","score":85,"noteTitle":"Phân phối Chi-squared từ Y=X^2"},{"title":"Giải mã công thức tích xác suất Π f(xi|θ) trong Machine Learning","score":88,"noteTitle":"Phân phối kết hợp mẫu ngẫu nhiên"},{"title":"Vì sao không gian mẫu đều nhưng biến ngẫu nhiên lại lệch?","score":93,"noteTitle":"Xác suất cảm sinh biến ngẫu nhiên"},{"title":"Coverage Probability vs Confidence Coefficient: Bản chất của độ tin cậy","score":78,"noteTitle":"Đánh giá ước lượng khoảng"},{"title":"Hội tụ theo phân phối: Thứ gì thực sự đang hội tụ?","score":88,"noteTitle":"Hội tụ xác suất sang phân phối"},{"title":"Vì sao đỉnh đường cong Gauss luôn tại mu?","score":85,"noteTitle":"Cực đại hàm mật độ Normal"},{"title":"Mẹo nhìn hàm PDF để nhận diện Pivot","score":85,"noteTitle":"Pivot từ công thức PDF"},{"title":"Bí mật triệt tiêu Jacobian: Chứng minh định lý sinh Pivot","score":88,"noteTitle":"Pivot từ công thức PDF"},{"title":"Shortest Pivotal Interval vs Shortest Overall Interval","score":85,"noteTitle":"Khoảng ngắn nhất: Trục và Tổng thể"},{"title":"Credible vs Confidence: Vì sao khoảng Bayes lại ngắn hơn?","score":90,"noteTitle":"Khác biệt Credible Confidence"},{"title":"Bí mật đằng sau xấp xỉ Satterthwaite","score":85,"noteTitle":"Ước lượng Satterthwaite"},{"title":"Thống kê đủ và Nghịch lý quy tắc dừng","score":85,"noteTitle":"Tương đương thông tin thống kê đủ"},{"title":"Bản chất hình học của xác suất phủ sai","score":92,"noteTitle":"Xác suất phủ sai"},{"title":"Bản chất chiều dài khoảng tin cậy: Tổng xác suất bao phủ sai","score":88,"noteTitle":"Neyman-shortest: Chiều dài khoảng tin cậy"},{"title":"WLLN và Tính Nhất Quán của Ước Lượng","score":85,"noteTitle":"WLLN và nhất quán"},{"title":"Bản chất phân phối Geometric từ không gian mẫu vô hạn","score":88,"noteTitle":"Số lần tung đến Head"},{"title":"Tính CDF phân phối Geometric bằng chuỗi hình học","score":84,"noteTitle":"Số lần tung đến Head"},{"title":"Điều kiện a²f(a) = b²f(b) cho khoảng tin cậy tối ưu","score":90,"noteTitle":"Điều kiện khoảng tin cậy tối ưu"},{"title":"Tại sao khoảng tin cậy luôn chia đôi mức ý nghĩa thành alpha/2?","score":82,"noteTitle":"Khoảng tin cậy từ đại lượng pivot"},{"title":"Nguyên lý Pivot: Bản chất thực sự đằng sau công thức khoảng tin cậy","score":88,"noteTitle":"Khoảng tin cậy từ đại lượng pivot"},{"title":"Chứng minh kiểm định không chệch không cần đạo hàm","score":88,"noteTitle":"Kiểm định LRT không chệch"},{"title":"g(T|θ) trong Neyman-Fisher có thực sự là PDF của thống kê đủ?","score":90,"noteTitle":"Định lý LRT Thống kê đủ"},{"title":"LRT trên thống kê đủ: Thu gọn dữ liệu không làm mất kết quả kiểm định","score":84,"noteTitle":"Định lý LRT Thống kê đủ"},{"title":"Inverse Transform Sampling: Sinh mọi phân phối ngẫu nhiên từ Unif(0,1)","score":88,"noteTitle":"Biến đổi CDF sang Unif(0,1)"},{"title":"Tại sao đưa biến ngẫu nhiên qua chính hàm CDF lại ra Unif(0,1)?","score":85,"noteTitle":"Biến đổi CDF sang Unif(0,1)"},{"title":"Bẫy xác suất Ba tù nhân: Phân biệt sự thật và lời khai","score":86,"noteTitle":"Biểu đồ nhánh xác suất W"},{"title":"Vì sao chặn kích thước của IUT lại hữu ích hơn UIT?","score":83,"noteTitle":"Cấp độ kiểm định UIT, IUT"},{"title":"Phân biệt Level và Size trong kiểm định giả thuyết","score":90,"noteTitle":"Cấp độ kiểm định UIT, IUT"},{"title":"Kỹ thuật Đảo ngược Kiểm định tạo Tập tin cậy Không chệch","score":88,"noteTitle":"Tập tin cậy không chệch"},{"title":"Trực giác về Tập tin cậy Không chệch và False Coverage","score":85,"noteTitle":"Tập tin cậy không chệch"},{"title":"Họ Exponential Family: Lối tắt tìm Sampling Distribution","score":82,"noteTitle":"Phân phối thống kê hàm mũ"},{"title":"Bản chất của Statistic: Tại sao Trung bình mẫu lại có phân phối xác suất?","score":90,"noteTitle":"Phân phối thống kê hàm mũ"},{"title":"Nguồn gốc công thức: Vì sao Var(X) = E(X^2) - (EX)^2?","score":78,"noteTitle":"Tính toán Phương sai Gamma"},{"title":"Mẹo Kernel Trick: Tính E(X^2) phân phối Gamma không cần tích phân","score":90,"noteTitle":"Tính toán Phương sai Gamma"},{"title":"Bí mật tối ưu Bayes Risk: Tối ưu từng điểm thay vì toàn cục","score":91,"noteTitle":"Tìm quy tắc quyết định Bayes"},{"title":"Tại sao cặp (X̄, S²) gom trọn thông tin của phân phối chuẩn?","score":86,"noteTitle":"Thống kê đủ phân phối chuẩn"},{"title":"Nguồn gốc dấu giá trị tuyệt đối khi đổi biến PDF","score":90,"noteTitle":"Chuyển đổi PDF biến ngẫu nhiên"},{"title":"Bản chất tỉ số: Cầu nối giữa phân phối t và phân phối F","score":73,"noteTitle":"Phân phối F và Đối xứng Cầu"},{"title":"Phân phối F không cần chuẩn: Sức mạnh của đối xứng cầu","score":85,"noteTitle":"Phân phối F và Đối xứng Cầu"},{"title":"Tìm Thống Kê LRT Khi Hàm Likelihood Tăng Đơn Điệu","score":86,"noteTitle":"Tỷ số Hợp lý λ(x)"},{"title":"Bí mật đằng sau độ tin cậy: Kỹ thuật lật tập hợp để tạo khoảng tin cậy","score":90,"noteTitle":"Định nghĩa đại lượng then chốt"},{"title":"Pivotal Quantity vs Statistic: Bản nghịch lý có chứa theta","score":86,"noteTitle":"Định nghĩa đại lượng then chốt"},{"title":"Kỹ thuật tạo Pivot: Từ tổng Exponential đến Chi-square","score":81,"noteTitle":"Khoảng tin cậy λ phân phối mũ"},{"title":"Bẫy đảo chiều cận trong khoảng tin cậy phân phối mũ","score":90,"noteTitle":"Khoảng tin cậy λ phân phối mũ"},{"title":"Bản chất ước lượng Bayes: Giằng co trọng số giữa niềm tin và thực tế","score":90,"noteTitle":"Ước lượng Bayes và trọng số"},{"title":"Bản chất của Tính tương biến (Equivariance) qua bài toán lật đồng xu","score":89,"noteTitle":"Nguyên lý ước lượng tương biến"},{"title":"Phân biệt T, T(X) và T(x): Hàm số, Ước lượng hay Con số?","score":90,"noteTitle":"Nguyên lý ước lượng tương biến"},{"title":"Bẻ khóa công thức p-value hợp lệ: Từng bước biến mẫu dữ liệu thành xác suất","score":90,"noteTitle":"Định nghĩa p-value hợp lệ"},{"title":"Dữ liệu khác nhau nhưng bằng chứng như nhau: Trực giác về Thống kê đủ","score":84,"noteTitle":"Nguyên lý thống kê đủ"},{"title":"Bản chất 2 bước của kiểm định giả thuyết","score":86,"noteTitle":"Đánh giá chất lượng kiểm định giả thuyết"},{"title":"Trực giác hình học của Likelihood Ratio Test","score":84,"noteTitle":"Kiểm định giả thuyết thống kê"},{"title":"Union-Intersection Test: Phép giao giả thuyết sinh ra hàm sup thế nào?","score":90,"noteTitle":"Kiểm định giả thuyết thống kê"},{"title":"Nghịch lý Cramer-Rao: Khi phương sai nhỏ hơn cả cận dưới","score":92,"noteTitle":"Cramer-Rao: Vi phạm giả định"},{"title":"Tính chất bất biến của MLE: Cứ thay số, đừng đạo hàm lại","score":86,"noteTitle":"Tính bất biến của MLE đa biến"},{"title":"Tìm MLE đa biến: Cầu nối giữa Thống kê và Tối ưu hóa","score":78,"noteTitle":"Tính bất biến của MLE đa biến"},{"title":"Bẫy kiểm định luôn bác bỏ và bản chất của UMP Test","score":90,"noteTitle":"Kiểm định giả thuyết tối ưu"},{"title":"Equivariance: Đổi thước đo có làm lệch suy luận?","score":72,"noteTitle":"Equivariance: Phép đo và Hình thức"},{"title":"Bản chất hình học của ký hiệu giá trị tới hạn (Cutoff Points)","score":87,"noteTitle":"Điểm cắt phân phối xác suất"},{"title":"Chữ Uniformly trong kiểm định UMP nghĩa là gì?","score":84,"noteTitle":"Kiểm định UMP giả thuyết phức hợp"},{"title":"Nghịch lý lực lượng: Vì sao kiểm định 'yếu hơn' lại hữu ích?","score":88,"noteTitle":"Lợi ích kiểm định giao liên hiệp"},{"title":"Ưu thế chẩn đoán của kiểm định giao liên hiệp (UIT)","score":82,"noteTitle":"Lợi ích kiểm định giao liên hiệp"},{"title":"Fisher Information: Vì sao càng nhiều thông tin thì phương sai càng nhỏ?","score":88,"noteTitle":"Giới hạn dưới Cramer-Rao"},{"title":"Khi nào một ước lượng không thể bị đánh bại? (Chặn Cramér-Rao)","score":82,"noteTitle":"Giới hạn dưới Cramer-Rao"},{"title":"Kỳ vọng tổng không cần độc lập","score":85,"noteTitle":"Kỳ vọng và Phương sai Tổng Mẫu"},{"title":"Vì sao khoảng tin cậy có thể bị đứt đoạn? (Phương pháp Sterne)","score":92,"noteTitle":"Phương pháp Sterne"},{"title":"Bản chất thống kê đủ qua góc nhìn sinh dữ liệu","score":90,"noteTitle":"Phân phối biên qua tính đủ"},{"title":"Hiểu lầm kinh điển: Ước lượng Bayes có luôn là Posterior Mean?","score":92,"noteTitle":"Ước lượng Bayes và Hàm mất mát"},{"title":"Vì sao đã có Risk Function lại cần đẻ thêm Bayes Risk?","score":85,"noteTitle":"Ước lượng Bayes và Hàm mất mát"},{"title":"Mối liên hệ kỳ diệu giữa Gamma CDF và Poisson qua tích phân từng phần","score":88,"noteTitle":"Tích phân từng phần CDF Gamma"},{"title":"Bản chất của P(X = x): Hàm xác suất cảm sinh","score":86,"noteTitle":"Hàm xác suất cảm sinh"},{"title":"Khi phân phối Student's t hóa thân thành quái vật Cauchy","score":86,"noteTitle":"Phân phối t của Student"},{"title":"Tại sao dùng S lại tạo ra phân phối Student's t?","score":84,"noteTitle":"Phân phối t của Student"},{"title":"Thống kê đủ dạng vector: Khi một con số là không đủ","score":76,"noteTitle":"Thống kê đủ vector"},{"title":"Bản chất đằng sau công thức phân phối Student-t","score":90,"noteTitle":"Suy diễn phân phối t"},{"title":"Tại sao đạo hàm MLE phương sai lại ra n chứ không phải n-1?","score":80,"noteTitle":"Ước lượng chệch MSE"},{"title":"Nghịch lý thống kê: Vì sao ước lượng chệch lại xịn hơn không chệch?","score":92,"noteTitle":"Ước lượng chệch MSE"},{"title":"Chứng minh (X̄, S²) là thống kê đủ tối thiểu của phân phối Chuẩn","score":85,"noteTitle":"Thống kê đủ tối thiểu phân phối chuẩn"},{"title":"Phương sai của tổng: Cross-terms biến đi đâu?","score":84,"noteTitle":"Phương sai tổng hàm độc lập"},{"title":"Tại sao công thức phương sai phải có bình phương?","score":88,"noteTitle":"Phương sai tổng hàm độc lập"},{"title":"Bản chất toán học của phép đổi đơn vị đo lường","score":78,"noteTitle":"Định Nghĩa Nhóm Biến Đổi"},{"title":"Chứng minh Luật số lớn yếu (WLLN) chỉ bằng Bất đẳng thức Chebyshev","score":88,"noteTitle":"Luật số lớn yếu WLLN"},{"title":"Nghịch lý Neyman-Pearson: Muốn giỏi nhất phải 'tệ nhất'?","score":88,"noteTitle":"Chứng minh định lý Neyman-Pearson"},{"title":"Bất đẳng thức then chốt trong bổ đề Neyman-Pearson","score":86,"noteTitle":"Chứng minh định lý Neyman-Pearson"},{"title":"Bản chất hội tụ hầu chắc qua góc nhìn hàm số","score":88,"noteTitle":"Hội tụ hầu chắc"},{"title":"Hiểu Lầm Kinh Điển Về Tính Đầy Đủ (Completeness)","score":88,"noteTitle":"Định nghĩa Tính đủ"},{"title":"Tại sao số trung bình tối thiểu hóa sai số bình phương?","score":88,"noteTitle":"Tính chất trung bình phương sai mẫu"},{"title":"Chứng minh công thức tính nhanh phương sai chỉ bằng một phép thế","score":80,"noteTitle":"Tính chất trung bình phương sai mẫu"},{"title":"Tại sao MLE lại được gọi là một Estimator?","score":90,"noteTitle":"Maximum Likelihood Estimator"},{"title":"Nghịch lý S² và X̄: Công thức phụ thuộc nhưng xác suất lại độc lập","score":91,"noteTitle":"Chứng minh độc lập S^2 X̄"},{"title":"Mẫu ngẫu nhiên có phải là thống kê đủ?","score":88,"noteTitle":"Thống kê đủ tối thiểu"},{"title":"Kỹ thuật đảo ngược kiểm định (Test Inversion): Biến miền chấp nhận thành khoảng tin cậy","score":90,"noteTitle":"Khoảng tin cậy đảo ngược LRT"},{"title":"Bản chất Likelihood Ratio Test: So sánh khi 'bị trói tay' và khi 'tự do'","score":82,"noteTitle":"Khoảng tin cậy đảo ngược LRT"},{"title":"Tại sao giai thừa của 1/2 lại chứa số Pi?","score":90,"noteTitle":"Chứng minh Γ(1/2) = √π"},{"title":"Ước lượng điểm dưới lăng kính Decision Theory","score":82,"noteTitle":"Tối ưu hàm mất mát"},{"title":"Squared Error vs Absolute Error: Phạt sai số thế nào cho đúng?","score":88,"noteTitle":"Tối ưu hàm mất mát"},{"title":"Bản chất trực giác của Likelihood Ratio Test (LRT)","score":88,"noteTitle":"Kiểm định LRT Phân phối Chuẩn"},{"title":"Bẫy phân biệt MLE và Likelihood tại MLE trong LRT","score":82,"noteTitle":"Kiểm định LRT Phân phối Chuẩn"},{"title":"Bản chất chuẩn hóa Z qua góc nhìn Location-Scale Family","score":82,"noteTitle":"Kiểm định UMP tham số trung bình"},{"title":"Cú đảo dấu trong Kiểm định UMP cho Phân phối Chuẩn","score":88,"noteTitle":"Kiểm định UMP tham số trung bình"},{"title":"Bản chất định lý Taylor: Chỉ là MVT lặp lại","score":88,"noteTitle":"Khai triển Taylor"},{"title":"Kỹ thuật tìm phần dư tích phân Taylor bằng IBP","score":84,"noteTitle":"Khai triển Taylor"},{"title":"Ném vòng hay Bắt chim: Phân biệt Confidence và Credible Interval","score":95,"noteTitle":"Xác suất đáng tin cậy và độ phủ"},{"title":"Lấy mẫu có hoàn lại và điều kiện i.i.d","score":85,"noteTitle":"Lấy mẫu có hoàn lại"},{"title":"Mẹo tìm ước lượng tốt nhất từ một ước lượng bất kỳ","score":88,"noteTitle":"Tìm ước lượng không chệch tốt nhất"},{"title":"Bốc thăm trước hay sau: Bí mật phân phối biên","score":88,"noteTitle":"Xác suất lấy mẫu không hoàn lại"},{"title":"Plausible vs Probable: Likelihood không phải là xác suất","score":90,"noteTitle":"Nguyên lý Hợp lý"},{"title":"Nguyên lý Likelihood: Khi hai bộ dữ liệu cho cùng một kết luận","score":85,"noteTitle":"Nguyên lý Hợp lý"},{"title":"Nghịch lý hàm Loss trong ước lượng khoảng","score":82,"noteTitle":"Lý thuyết quyết định ước lượng khoảng"},{"title":"Định lý đổi biến: Vì sao chỉ cần ánh xạ 1-1 trên Support Set?","score":82,"noteTitle":"Độc lập biến chuẩn"},{"title":"Bí mật số hạng chéo: Vì sao Cov = 0 dẫn đến độc lập ở biến chuẩn?","score":88,"noteTitle":"Độc lập biến chuẩn"},{"title":"Vì sao đạo hàm Likelihood bằng 0 chưa chắc là MLE?","score":90,"noteTitle":"Điều kiện tìm MLE"},{"title":"Từ Neyman-Pearson đến Karlin-Rubin: Cầu nối sang kiểm định UMP","score":90,"noteTitle":"Thống kê đủ và kiểm định UMP"},{"title":"Giải mã MGF: Tại sao E[e^(tX)] lại là hàm theo t?","score":92,"noteTitle":"Phân phối lấy mẫu X̄"},{"title":"Bản chất Sampling Distribution: Vì sao X̄ có phân phối?","score":86,"noteTitle":"Phân phối lấy mẫu X̄"},{"title":"Bản chất hình học và đại số của Delta Method","score":90,"noteTitle":"Phương pháp Delta"},{"title":"Tính duy nhất của kiểm định UMP và ý nghĩa 'hầu khắp nơi'","score":85,"noteTitle":"Độc nhất UMP level α test"},{"title":"Nghịch lý đảo kiểm định: Vì sao giả thuyết 'nhỏ hơn' lại sinh ra chặn trên?","score":92,"noteTitle":"Giới hạn tin cậy trên"},{"title":"Khoảng tin cậy thực chất chỉ là kiểm định bị đảo ngược","score":92,"noteTitle":"Mối liên hệ Kiểm định - Khoảng tin cậy"},{"title":"Phân biệt Loss Function, Risk Function và MSE","score":92,"noteTitle":"Risk function: MSE"},{"title":"Thủ thuật điểm đại diện để chứng minh thống kê đủ","score":85,"noteTitle":"Chứng minh thống kê đủ"},{"title":"LP và Formal LP: Khác nhau ở đâu?","score":82,"noteTitle":"Mở rộng Nguyên lý Hợp lý"},{"title":"Định lý Birnbaum: Mẹo tung đồng xu hợp nhất hai thí nghiệm","score":92,"noteTitle":"Mở rộng Nguyên lý Hợp lý"},{"title":"Tư duy 'chạm sàn': Cách tìm ước lượng tốt nhất trong vô hạn","score":88,"noteTitle":"Ước lượng không chệch tối ưu"},{"title":"Bẫy tổ hợp lồi: Từ 2 thành vô số ước lượng không chệch","score":82,"noteTitle":"Ước lượng không chệch tối ưu"},{"title":"Hiểu Đúng Về Họ Phân Phối Bất Biến Qua Phân Phối Nhị Thức","score":85,"noteTitle":"Nguyên lý Equivariance và Bất biến"},{"title":"Trực quan hóa tỉ số Likelihood tìm Thống kê đủ tối thiểu","score":88,"noteTitle":"Thống kê đủ tối thiểu phân phối đều"},{"title":"Bí ẩn dấu giá trị tuyệt đối trong đổi biến ngẫu nhiên","score":90,"noteTitle":"Định lý biến đổi hàm mật độ"},{"title":"Tính xác suất Bayes cho Confidence Interval: Chuyện gì xảy ra?","score":88,"noteTitle":"Xác suất Credible & Tin cậy"},{"title":"Vì sao khoảng biến thiên (Range) không phụ thuộc tham số vị trí?","score":90,"noteTitle":"Thống kê khoảng biến thiên phụ"},{"title":"Dùng biến đổi PIT để tạo Pivot vạn năng từ hàm CDF","score":86,"noteTitle":"Phương pháp Khoảng Tin Cậy Pivot"},{"title":"Vì sao Pivot bắt buộc phải đơn điệu theo tham số θ?","score":90,"noteTitle":"Phương pháp Khoảng Tin Cậy Pivot"},{"title":"Kích thước kiểm định (Test Size) và độ tin cậy của kết luận","score":77,"noteTitle":"Kích thước test và p-value"},{"title":"Hội tụ theo xác suất nhưng không hội tụ hầu chắc chắn","score":90,"noteTitle":"Hội tụ hầu chắc chắn"},{"title":"Nghịch lý phương sai Odds Ratio và giải pháp Delta Method","score":87,"noteTitle":"Xấp xỉ kì vọng phương sai"},{"title":"Trực giác Delta Method: Xấp xỉ phương sai bằng tiếp tuyến","score":91,"noteTitle":"Xấp xỉ kì vọng phương sai"},{"title":"Tham số vị trí và tham số ngưỡng trong phân phối mũ","score":87,"noteTitle":"Họ phân phối vị trí mũ"},{"title":"Hạn chế của Cramer-Rao và vì sao cần Thống kê Đủ","score":85,"noteTitle":"Tiêu chí Sufficiency"},{"title":"Bất Biến Hình Thức Trong Thống Kê","score":75,"noteTitle":"Nguyên lý Bất biến Hình thức"},{"title":"Mối liên hệ giữa False Coverage và Độ dài Khoảng Tin cậy","score":72,"noteTitle":"Tối ưu chiều dài khoảng tin cậy"},{"title":"Ngộ nhận 90% về khoảng tin cậy","score":93,"noteTitle":"Diễn giải khoảng tin cậy"},{"title":"Đặc quyền nén dữ liệu của Exponential Family","score":90,"noteTitle":"Thống kê đủ: Giảm chiều dữ liệu"},{"title":"Thống kê đủ không phải lúc nào cũng nén dữ liệu","score":87,"noteTitle":"Thống kê đủ: Giảm chiều dữ liệu"},{"title":"Mẹo tìm Minimal Sufficient Statistic bằng tỉ số Likelihood","score":88,"noteTitle":"Định lý Minimal Sufficient Statistic"},{"title":"Bản chất của S² khi mẫu chỉ có 2 phần tử","score":85,"noteTitle":"Chứng minh S^2 Chi-square"},{"title":"Bẫy ngộ nhận về tính độc lập khi cộng bậc tự do Chi-square","score":88,"noteTitle":"Chứng minh S^2 Chi-square"},{"title":"ML Estimator hay ML Estimate: Bạn có đang dùng nhầm?","score":83,"noteTitle":"Khái niệm và nhược điểm MLE"},{"title":"Cạm bẫy tối ưu trong MLE: Khi lý thuyết gặp thực tế","score":88,"noteTitle":"Khái niệm và nhược điểm MLE"},{"title":"Bí quyết đặt H0: Luôn gán cho sai lầm đắt giá nhất","score":89,"noteTitle":"Ưu tiên tránh lỗi loại I"},{"title":"Alpha và ngưỡng c: Cách chốt một phép kiểm định duy nhất","score":84,"noteTitle":"Ưu tiên tránh lỗi loại I"},{"title":"Độc lập đôi một hay độc lập toàn thể trong lấy mẫu ngẫu nhiên?","score":80,"noteTitle":"Định nghĩa Lấy mẫu Ngẫu nhiên"},{"title":"Mẫu ngẫu nhiên: Biến ngẫu nhiên hay chỉ là dãy số?","score":86,"noteTitle":"Định nghĩa Lấy mẫu Ngẫu nhiên"},{"title":"Cạm bẫy Likelihood khi tham số nằm trong Support","score":92,"noteTitle":"Hàm hợp lí Exponential"},{"title":"Nguồn gốc số 12 trong phương sai phân phối đều","score":76,"noteTitle":"Tính toán Phân phối Đều"},{"title":"Mẹo thêm bớt x̄: Bí mật triệt tiêu số hạng chéo trong thống kê","score":82,"noteTitle":"Trung bình mẫu thống kê đủ cho μ"},{"title":"Chứng minh phân phối trung bình mẫu bằng hàm sinh mô-men (MGF)","score":88,"noteTitle":"Trung bình mẫu thống kê đủ cho μ"},{"title":"Tại sao mỗi quan sát mẫu lại là một biến ngẫu nhiên?","score":86,"noteTitle":"Mô hình Lấy mẫu Ngẫu nhiên"},{"title":"Nghịch lý tập độ đo 0 trong tối ưu khoảng tin cậy","score":88,"noteTitle":"Vấn đề hình dạng tập hợp"},{"title":"Bản chất P(A|B): Khi không gian mẫu bị thu hẹp","score":92,"noteTitle":"Phân biệt P(A) và P(A|B)"},{"title":"Tại sao khoảng tin cậy 95% không mang xác suất 95%?","score":91,"noteTitle":"Khoảng Tin Cậy và Đáng Tin Cậy"},{"title":"Nghịch lý Ancillary Statistic: Khi đại lượng 'vô dụng' lại chỉ điểm tham số","score":90,"noteTitle":"Suy luận tham số từ Ancillary"},{"title":"Mẹo Plug-in bằng Định lý Slutsky khi tham số chưa biết","score":86,"noteTitle":"Ước lượng Tham số Slutsky"},{"title":"Slutsky cần Thống kê Vững hay Không chệch?","score":88,"noteTitle":"Ước lượng Tham số Slutsky"},{"title":"Bước nhảy rủi ro tại ranh giới kiểm định UMP","score":86,"noteTitle":"Rủi ro kiểm định UMP"},{"title":"Xấp xỉ kỳ vọng hàm phi tuyến bằng Taylor bậc 1","score":82,"noteTitle":"Xấp xỉ kỳ vọng Taylor"},{"title":"Bí quyết triệt tiêu bậc 1: Khai triển Taylor MGF biến chuẩn hóa","score":82,"noteTitle":"Khai triển Taylor MGF Moment"},{"title":"Vì sao hàm MGF lại sinh ra Moment qua chuỗi Taylor?","score":85,"noteTitle":"Khai triển Taylor MGF Moment"},{"title":"So sánh UIT và LRT: Cái giá của sự tiện lợi","score":88,"noteTitle":"Quan hệ T(x) và λ(x)"},{"title":"MLE có ràng buộc: Khi đạo hàm bằng 0 cho nghiệm vô lý","score":90,"noteTitle":"MLE có ràng buộc"},{"title":"Hiểu đúng bản chất UMVUE qua hàm tham số","score":75,"noteTitle":"Ước lượng không chệch phương sai nhỏ nhất"},{"title":"Phương pháp Delta: Xấp xỉ phương sai của tỉ số X/Y","score":78,"noteTitle":"Xấp xỉ Mean Variance Tỉ số"},{"title":"Bẫy Cauchy: Vì sao tỉ số hai biến chuẩn không có kỳ vọng?","score":86,"noteTitle":"Xấp xỉ Mean Variance Tỉ số"},{"title":"Tại sao hội tụ phân phối bỏ qua điểm gián đoạn?","score":82,"noteTitle":"Hội tụ theo phân phối"},{"title":"Nguồn gốc sâu xa của t-test từ Likelihood Ratio Test","score":90,"noteTitle":"Kiểm định LRT cho trung bình"},{"title":"Vì sao phân phối Student-t không có hàm sinh moment (MGF)?","score":85,"noteTitle":"Giới hạn momen phân phối t"},{"title":"Cạm bẫy khoảng tin cậy ngắn nhất khi nghịch đảo Pivot","score":90,"noteTitle":"Khoảng tin cậy ngắn nhất β"},{"title":"Biết hay chưa biết phương sai: Cú lật kèo của thống kê đủ","score":78,"noteTitle":"Hai thống kê đủ chuẩn"},{"title":"Bản chất thống kê đủ tối thiểu qua ví dụ thu gọn dữ liệu","score":85,"noteTitle":"Hai thống kê đủ chuẩn"},{"title":"Bản chất toán học của Credible Interval dưới phân phối chuẩn","score":82,"noteTitle":"Khoảng tin cậy 1-α"},{"title":"Định lý LOTUS: Lối tắt thần kỳ để tính E[g(X)]","score":86,"noteTitle":"Giá trị kỳ vọng và LOTUS"},{"title":"Bản chất của kỳ vọng: Đừng để cái tên đánh lừa","score":80,"noteTitle":"Giá trị kỳ vọng và LOTUS"},{"title":"Tại sao phương sai mẫu chia cho n - 1 thay vì n?","score":92,"noteTitle":"Ước lượng không chệch"},{"title":"Cân bằng Độ rộng và Độ tin cậy bằng Hàm Rủi ro","score":87,"noteTitle":"Hàm rủi ro: Kiểm soát Trade-off"},{"title":"Giải mã công thức Phân phối Hậu nghiệm (Posterior)","score":86,"noteTitle":"Phân phối hậu nghiệm"},{"title":"Bẫy ký hiệu Bayes: Khi chữ thường là biến ngẫu nhiên","score":82,"noteTitle":"Phân phối hậu nghiệm"},{"title":"Bí quyết tìm phương sai hàm phi tuyến bằng xấp xỉ Taylor","score":85,"noteTitle":"Công thức phương sai hàm"},{"title":"Nhận diện Complete Statistic qua họ Exponential Family","score":80,"noteTitle":"Kỳ vọng theo Định lý Basu"},{"title":"Mẹo tính kỳ vọng tỷ lệ bằng Định lý Basu","score":92,"noteTitle":"Kỳ vọng theo Định lý Basu"},{"title":"Mẹo tam thức bậc hai chứng minh bất đẳng thức Cauchy-Schwarz","score":88,"noteTitle":"Bất đẳng thức Cauchy-Schwarz"},{"title":"Bản chất Location Family qua sai số đo lường","score":85,"noteTitle":"Location Family và Sai số đo"},{"title":"Bí kíp Location-Scale: Tìm phân phối trung bình mẫu không cần tích phân","score":82,"noteTitle":"Trung bình mẫu Location Scale"},{"title":"Nghịch lý Cauchy: Vì sao gom 1 triệu mẫu vẫn không giảm sai số?","score":92,"noteTitle":"Trung bình mẫu Location Scale"},{"title":"Bản chất trực quan của CDF và Hàm Phân Vị (Quantile)","score":88,"noteTitle":"Tính phổ quát của Uniform(0,1)"},{"title":"Khi CDF bị 'phẳng': Bí mật định nghĩa Infimum trong Hàm Phân Vị","score":92,"noteTitle":"Tính phổ quát của Uniform(0,1)"},{"title":"Mẫu số của định lý Bayes đến từ đâu?","score":85,"noteTitle":"Định lý Bayes: Các phiên bản"},{"title":"Khi khoảng tin cậy suy biến thành ước lượng điểm","score":82,"noteTitle":"Ước lượng khoảng tối ưu"},{"title":"Bản chất tối ưu của khoảng tin cậy","score":84,"noteTitle":"Ước lượng khoảng tối ưu"},{"title":"Phân biệt Probability và Odds trong 3 phút","score":86,"noteTitle":"Ước lượng Odds và Delta Method"},{"title":"Vì sao CLT là chưa đủ và ta cần tới Delta Method?","score":90,"noteTitle":"Ước lượng Odds và Delta Method"},{"title":"Kiểm định tối ưu UMP: Rút gọn không gian mẫu nhờ thống kê đủ","score":87,"noteTitle":"Kiểm định UMP với thống kê đủ"},{"title":"Bản chất xác suất của Sai lầm Loại I và II qua Miền bác bỏ","score":85,"noteTitle":"Sai lầm và vùng bác bỏ"},{"title":"Bản chất tính tuyến tính của kỳ vọng","score":75,"noteTitle":"Nguồn gốc tính chất kỳ vọng"},{"title":"Cực trị duy nhất trên miền mở: Khi nào không cần xét biên?","score":90,"noteTitle":"MLE Phân phối Chuẩn"},{"title":"Bản chất Second-Order Test: Khai triển Taylor giải thích Hessian âm","score":85,"noteTitle":"MLE Phân phối Chuẩn"},{"title":"Bất biến thang đo: Đo bằng mét hay inch thì kết luận có đổi?","score":72,"noteTitle":"Nguyên lý bất biến thang đo"},{"title":"Incomplete Data Likelihood: Đừng vứt bỏ dữ liệu thiếu","score":92,"noteTitle":"Hàm likelihood không đầy đủ"},{"title":"Nguồn gốc dấu trị tuyệt đối trong kiểm định t hai phía","score":90,"noteTitle":"Kiểm định t hai phía"},{"title":"Tại sao ước lượng điểm không thể đo lường độ tự tin?","score":85,"noteTitle":"Đảo ngược test statistic"},{"title":"Kỹ thuật đảo ngược kiểm định để tìm khoảng tin cậy","score":93,"noteTitle":"Đảo ngược test statistic"},{"title":"Bản chất toán học của biến thống kê (Statistic)","score":90,"noteTitle":"Biến Thống Kê Từ Mẫu"},{"title":"Tham số vị trí có thực sự là Mean? Bản chất của Location Family","score":88,"noteTitle":"Tạo Location Family từ PDF"},{"title":"Hiện tượng đường cong rủi ro cắt nhau","score":87,"noteTitle":"Hàm rủi ro ước lượng"},{"title":"Bản chất toán học của Risk Function","score":89,"noteTitle":"Hàm rủi ro ước lượng"},{"title":"Credible Set Không Phải Là Confidence Set","score":88,"noteTitle":"Tối ưu khoảng tin cậy Bayesian"},{"title":"Tổ hợp tuyến tính chuẩn: Khi hiệp phương sai bằng 0 đồng nghĩa với độc lập","score":85,"noteTitle":"Độc lập trung bình phương sai"},{"title":"Bẫy ký hiệu: Vì sao không được viết P(H0 đúng)?","score":84,"noteTitle":"Kiểm định giả thuyết nhị thức"},{"title":"Trực quan hóa đánh đổi Sai lầm Loại I và II bằng hàm Power","score":93,"noteTitle":"Kiểm định giả thuyết nhị thức"},{"title":"Biến ngẫu nhiên không phải là một biến số","score":90,"noteTitle":"Lí do định nghĩa biến ngẫu nhiên"},{"title":"Vì sao lấy mẫu không hoàn lại khiến biến ngẫu nhiên phụ thuộc?","score":85,"noteTitle":"Phụ thuộc trong lấy mẫu không hoàn lại"},{"title":"Bản chất trực quan của Continuity Correction (+/- 0.5)","score":88,"noteTitle":"Xấp xỉ Normal Binomial"},{"title":"Đảo ngược kiểm định để tìm khoảng tin cậy","score":84,"noteTitle":"Đảo ngược kiểm định"},{"title":"Từ Neyman-Pearson sang UMP: Phép màu triệt tiêu tham số nhờ MLR","score":88,"noteTitle":"Kiểm định UMP bằng MLR"},{"title":"Mẹo tập con và hàm lực: Mở rộng UMP sang giả thuyết phức H0: θ ≤ θ0","score":85,"noteTitle":"Kiểm định UMP bằng MLR"},{"title":"Cách tra bảng Z-table không bị hoa mắt","score":75,"noteTitle":"Quy tắc tra bảng Z"},{"title":"Cạm bẫy đổi biến ngẫu nhiên: Từ Gamma sang Inverse-Gamma","score":82,"noteTitle":"Phân bố Gamma ngược"},{"title":"Bản chất chứng minh Định lý Basu","score":85,"noteTitle":"Định lý Basu"},{"title":"Mẹo xử lý kỳ vọng phức tạp trong thuật toán EM","score":82,"noteTitle":"Tối đa hóa hàm likelihood"},{"title":"Likelihood vs Joint PDF: Cùng biểu thức, khác góc nhìn","score":84,"noteTitle":"Hàm khả năng biến liên tục"},{"title":"Bản chất Likelihood cho biến liên tục: Nghịch lý P(X=x)=0","score":88,"noteTitle":"Hàm khả năng biến liên tục"},{"title":"Nghịch đảo kiểm định: Biến miền chấp nhận thành khoảng tin cậy","score":89,"noteTitle":"Vùng chấp nhận và khoảng tin cậy"},{"title":"Biến đổi CDF thành Uniform trong kiểm định giả thuyết","score":84,"noteTitle":"Vùng chấp nhận và khoảng tin cậy"},{"title":"Chuẩn Hóa Phân Phối Hậu Nghiệm Bằng Họ Vị Trí - Tỉ Lệ","score":80,"noteTitle":"Phân phối hậu nghiệm Bayes Normal"},{"title":"Ước Lượng Bayes: Tại Sao Sách Lại Viết Hàm Của X̄ Thay Vì Mẫu X?","score":82,"noteTitle":"Phân phối hậu nghiệm Bayes Normal"},{"title":"Trực giác Story: Vì sao CDF của Poisson luôn nghịch biến theo lambda?","score":88,"noteTitle":"Khoảng tin cậy Poisson Chi-square"},{"title":"Giải mã ký hiệu phân vị Chi-square qua lăng kính Z-score","score":85,"noteTitle":"Khoảng tin cậy Poisson Chi-square"},{"title":"Tại sao phân phối Beta sinh ra là để dành cho tỉ lệ?","score":82,"noteTitle":"Phân phối Beta: Định nghĩa, ứng dụng"},{"title":"Bản chất toán học của MLE: Biến hàm số thành ước lượng","score":82,"noteTitle":"Kiểm định tỉ số khả dĩ"},{"title":"Chứng minh Thống kê đủ tối thiểu bằng Tỉ số Likelihood","score":83,"noteTitle":"Thống kê đủ tối thiểu"},{"title":"Bẫy đảo chiều khi tìm CDF của Y = g(X)","score":85,"noteTitle":"Phân phối Y=g(X) đơn điệu"},{"title":"Bản chất hình học của khoảng xác suất ngắn nhất","score":86,"noteTitle":"Chứng minh xác suất đoạn ngắn nhất"},{"title":"Kỹ thuật đưa Phân phối Chuẩn về Họ Hàm Mũ (Exponential Family)","score":82,"noteTitle":"Thống kê đủ và hoàn chỉnh X̄"},{"title":"Chứng minh X̄ và S² độc lập trong 3 phút bằng Định lý Basu","score":90,"noteTitle":"Thống kê đủ và hoàn chỉnh X̄"},{"title":"Bản chất đẳng thức Fisher Information","score":82,"noteTitle":"Bổ đề Tính toán Hàm mũ"},{"title":"Trực quan hóa hàm ngưỡng bậc thang k(p) trong kiểm định nhị thức","score":92,"noteTitle":"Khoảng Tin Cậy qua Đảo Kiểm Định"},{"title":"Bản chất của phép đảo kiểm định để tìm khoảng tin cậy","score":85,"noteTitle":"Khoảng Tin Cậy qua Đảo Kiểm Định"},{"title":"Phân phối Cauchy: Trông như chuông Normal nhưng không có kỳ vọng","score":85,"noteTitle":"Phân phối Cauchy"},{"title":"Vì sao tích phân hàm mật độ Cauchy bằng 1?","score":78,"noteTitle":"Phân phối Cauchy"},{"title":"Tham số vị trí và tỉ lệ có thực sự là Mean và Variance?","score":90,"noteTitle":"Ý nghĩa tham số Location-Scale"},{"title":"Nguyên lý đủ: Nén dữ liệu mà không sợ mất thông tin","score":86,"noteTitle":"Nguyên lý đủ"},{"title":"Cramér-Rao và đường tắt tìm ước lượng tối ưu cho Poisson","score":90,"noteTitle":"Cramer-Rao ước lượng Poisson"},{"title":"Đừng vứt dữ liệu khuyết: Trực giác về Marginal Likelihood","score":85,"noteTitle":"Hàm khả dĩ dữ liệu khuyết"},{"title":"Conjugate Prior: Tại sao mô hình Binomial luôn đi kèm phân phối Beta?","score":84,"noteTitle":"Ước lượng Bayes và Họ liên hợp"},{"title":"Ước lượng Bayes: Trò chơi kéo co giữa Dữ liệu và Niềm tin","score":92,"noteTitle":"Ước lượng Bayes và Họ liên hợp"},{"title":"Phân biệt Xác suất f(x|θ) và Khả năng L(θ|x)","score":92,"noteTitle":"Định nghĩa Hàm Khả Năng"},{"title":"Bẫy cực đại phẳng: Vì sao nghiệm MLE nhạy cảm với nhiễu?","score":86,"noteTitle":"Bất ổn định của ước lượng MLE"},{"title":"Bản chất Rejection Region và Sự Đổi Mặt của Power Function","score":86,"noteTitle":"Kiểm soát sai lầm kiểm định giả thuyết"},{"title":"Cách Tính Ngưỡng c và Cỡ Mẫu n để Khống Chế Cả 2 Loại Sai Lầm","score":90,"noteTitle":"Kiểm soát sai lầm kiểm định giả thuyết"},{"title":"Trực quan hóa Bổ đề Neyman-Pearson qua Phân phối Nhị thức","score":92,"noteTitle":"Kiểm định UMP nhị thức"},{"title":"Tại sao chỉ cần nhớ tổng số lần ngửa: Bản chất của Thống kê đủ","score":86,"noteTitle":"Thống kê đủ nhị thức"},{"title":"Bản chất phép cộng bậc tự do của Chi-square qua phân phối Gamma","score":79,"noteTitle":"Bổ đề Chi-square"},{"title":"Tại sao bình phương phân phối chuẩn là Chi-square(1)?","score":85,"noteTitle":"Bổ đề Chi-square"},{"title":"Biến kiểm định LRT thành khoảng tin cậy bằng lát cắt ngang","score":85,"noteTitle":"Khoảng tin cậy tối ưu"},{"title":"Bẫy chia đều hai đuôi α/2 khi tìm khoảng tối ưu","score":79,"noteTitle":"Khoảng tin cậy tối ưu"},{"title":"Tại sao dùng Set Estimation thay vì Interval Estimation?","score":80,"noteTitle":"Tối ưu hàm mất mát"},{"title":"Cân bằng độ dài và độ tin cậy bằng Lý thuyết Quyết định","score":84,"noteTitle":"Tối ưu hàm mất mát"},{"title":"Thí nghiệm tư duy 2 nhà khoa học: Bản chất của thống kê đủ","score":90,"noteTitle":"Thống kê đủ và thông tin θ"},{"title":"Bốc thăm không hoàn lại: Khi nào được xem như biến độc lập?","score":88,"noteTitle":"Phân phối siêu hình học"},{"title":"Hiểu bản chất công thức phân phối Siêu hình học trong 3 phút","score":85,"noteTitle":"Phân phối siêu hình học"},{"title":"Đảo ngược kiểm định để tìm khoảng tin cậy","score":88,"noteTitle":"Thiết lập khoảng tin cậy một phía"},{"title":"Bản chất toán học đằng sau công thức Z-score","score":86,"noteTitle":"Chuẩn hóa biến ngẫu nhiên chuẩn"},{"title":"Bản chất Định lý Slutsky và cạm bẫy hội tụ","score":85,"noteTitle":"Định lý Slutsky"},{"title":"Nghịch ảnh trong hàm biến ngẫu nhiên: Bí mật đằng sau P(Y in A)","score":90,"noteTitle":"Xác suất của hàm biến ngẫu nhiên"},{"title":"Bản chất biến ngẫu nhiên: Hàm số định danh không gian mẫu","score":85,"noteTitle":"Xác suất của hàm biến ngẫu nhiên"},{"title":"Bản Chất Biến Số Của Hàm Hợp Lý L(θ|x)","score":86,"noteTitle":"Hàm Hợp Lý Vector Rời Rạc"},{"title":"Bản chất đối ngẫu giữa Kiểm định và Khoảng tin cậy","score":88,"noteTitle":"Liên hệ Kiểm định - Tin cậy"},{"title":"Bayes Risk: Cách Bayesian biến đường cong rủi ro thành một con số","score":92,"noteTitle":"Rủi ro Bayes và Quy tắc Bayes"},{"title":"Conditionality Principle: Thí nghiệm bạn KHÔNG làm có ý nghĩa gì?","score":83,"noteTitle":"Chứng minh Định lý Birnbaum"},{"title":"Chứng minh Định lý Birnbaum qua thí nghiệm tung xu","score":88,"noteTitle":"Chứng minh Định lý Birnbaum"},{"title":"Bản chất trực quan của kiểm định không chệch (Unbiased Test)","score":85,"noteTitle":"Tính không chệch kiểm định ước lượng"},{"title":"Mẹo dãy con: Khôi phục hội tụ hầu chắc chắn từ xác suất","score":75,"noteTitle":"Định luật số lớn mạnh"},{"title":"Hội tụ hầu chắc chắn vs theo xác suất: Bản chất Luật số lớn Mạnh","score":88,"noteTitle":"Định luật số lớn mạnh"},{"title":"Vì sao hàm đơn điệu biến Pivot thành Khoảng Tin Cậy?","score":82,"noteTitle":"Pivot CDF và Confidence Set"},{"title":"Cạm bẫy khi chỉ tính Mean và Variance","score":89,"noteTitle":"Mean, Variance và Giả định Normal"},{"title":"Bản chất bình quân gia quyền của kỳ vọng hậu nghiệm Bayes","score":87,"noteTitle":"Ước lượng Bayes chuẩn"},{"title":"Bất ngờ khi hàm mất mát L1 và L2 cho cùng một ước lượng Bayes","score":93,"noteTitle":"Ước lượng Bayes chuẩn"},{"title":"Định lý Bayes và độ tin cậy tín hiệu Morse","score":88,"noteTitle":"Độ tin cậy tín hiệu Morse"},{"title":"Tìm PDF của Sample Mean bằng kỹ thuật CDF","score":90,"noteTitle":"Chứng minh PDF Sample Mean"},{"title":"Bản chất toán học đằng sau công thức Thống kê đủ","score":88,"noteTitle":"Định nghĩa thống kê đủ"},{"title":"Vì sao Bayes Estimator chống lại kết quả cực đoan tốt hơn MLE?","score":88,"noteTitle":"Ước lượng Bayes Loss Tuyệt đối"},{"title":"Mean hay Median: Hàm Loss quyết định ước lượng Bayes như thế nào?","score":84,"noteTitle":"Ước lượng Bayes Loss Tuyệt đối"},{"title":"Bản chất phương pháp Delta: Tuyến tính hóa hàm của trung bình mẫu","score":82,"noteTitle":"CLT ước lượng tỉ số"},{"title":"Chứng minh toán học tính Memoryless của phân phối mũ","score":82,"noteTitle":"Tính không trí nhớ của Expo"},{"title":"Trực giác về tính không trí nhớ: Geometric và Exponential","score":88,"noteTitle":"Tính không trí nhớ của Expo"},{"title":"Ước lượng phương sai: Tại sao chia cho n+1 lại tốt hơn n-1?","score":90,"noteTitle":"Ước lượng phương sai tối ưu"},{"title":"Nghịch lý thống kê phụ trợ (Ancillary Statistic)","score":84,"noteTitle":"Statistic phụ trợ"},{"title":"Chữ P trong F(x) = P(X ≤ x) thực chất là gì?","score":88,"noteTitle":"Cơ sở xác suất của CDF"},{"title":"Hàm Loss 0-1 Tổng Quát và Chi Phí Sai Lầm","score":87,"noteTitle":"Hàm loss 0-1 tổng quát"},{"title":"Tại sao khoảng tin cậy đối xứng lại ngắn nhất?","score":88,"noteTitle":"Khoảng tin cậy ngắn nhất"},{"title":"Hội tụ xác suất vs Hội tụ phân phối: Ngoại lệ hằng số","score":92,"noteTitle":"Hội tụ xác suất và phân phối"},{"title":"Bản chất thật sự của hàm Likelihood","score":88,"noteTitle":"Ước lượng Hợp lý Tối đa"},{"title":"Estimator: Cỗ máy chắt lọc thông tin","score":79,"noteTitle":"Ước lượng Hợp lý Tối đa"},{"title":"Khoảng tin cậy tối ưu: Đo độ dài hay đo giá trị sai?","score":82,"noteTitle":"Tính tối ưu liên quan kiểm định"},{"title":"Mẹo 'công tắc số mũ' để biến hàm if-else thành biểu thức khả vi","score":86,"noteTitle":"Ước lượng hợp lý cực đại Bernoulli"},{"title":"Nguồn gốc Binary Cross-Entropy từ MLE Bernoulli","score":95,"noteTitle":"Ước lượng hợp lý cực đại Bernoulli"},{"title":"Bản chất Statistic: Tại sao Likelihood Function lại là một Thống kê?","score":88,"noteTitle":"Hàm khả năng - Thu gọn dữ liệu"},{"title":"Tại sao Range là thống kê phụ trợ của tham số vị trí","score":85,"noteTitle":"Thống kê phụ trợ Range"},{"title":"Bayes Estimator vs UMVUE: Tư duy tối ưu hóa thay vì mò mẫm","score":88,"noteTitle":"Xây dựng Quy tắc Bayes"},{"title":"Bí quyết tối ưu Bayes Risk từng điểm quan sát","score":86,"noteTitle":"Xây dựng Quy tắc Bayes"},{"title":"Đảo kiểm định để tìm khoảng tin cậy","score":78,"noteTitle":"Chặn dưới p nhị thức"},{"title":"Dùng đường cong hàm lực để tính cỡ mẫu n","score":78,"noteTitle":"Xác định cỡ mẫu bằng hàm lực"},{"title":"Bản chất trực quan của Location Family","score":86,"noteTitle":"Định nghĩa Gia đình Location"},{"title":"Cramer-Rao Bound: Khi chặn dưới không thể chạm tới","score":89,"noteTitle":"Hạn chế Cramer-Rao Bound"},{"title":"Kỹ thuật giảm phương sai: Mẹo cộng thêm aU để tạo ước lượng xịn hơn","score":85,"noteTitle":"Ước lượng không chệch tốt nhất"},{"title":"Phân rã Pythagoras: Cách chứng minh ước lượng tốt nhất trong 3 dòng","score":90,"noteTitle":"Ước lượng không chệch tốt nhất"},{"title":"Bản chất tham số Scale trong phân phối Gamma qua phép đổi biến","score":86,"noteTitle":"Hàm Gamma và Phân phối Gamma"},{"title":"Từ UMP đến UMA: Cầu nối giữa Power và False Coverage","score":86,"noteTitle":"UMA từ Test UMP"},{"title":"Phép nghịch đảo kiểm định: Biến Test thành Khoảng tin cậy","score":90,"noteTitle":"UMA từ Test UMP"},{"title":"Nghịch lý UMA: Vì sao khoảng tin cậy 2 phía chuẩn lại không tối ưu?","score":82,"noteTitle":"UMA từ Test UMP"},{"title":"Mẹo tách hàm khi tham số nằm ở cận: Tìm thống kê đủ cho Discrete Uniform","score":88,"noteTitle":"Thống Kê Đủ Factorization"},{"title":"Tại sao Frequentist không tính được xác suất H0 đúng?","score":88,"noteTitle":"Xác suất H0/H1 trong Bayesian"},{"title":"Bằng chứng Thống kê Ev(E, x): Tại sao ước lượng đơn lẻ là chưa đủ?","score":84,"noteTitle":"Khái niệm Bằng chứng Thử nghiệm"},{"title":"Bí kíp nghịch đảo kiểm định: Khi không biết tìm khoảng tin cậy từ đâu","score":83,"noteTitle":"H1 và Dạng Tập Tin Cậy"},{"title":"H1 quyết định hình dạng: Tại sao kiểm định tạo ra khoảng tin cậy 1 phía hay 2 phía?","score":90,"noteTitle":"H1 và Dạng Tập Tin Cậy"},{"title":"Hiểu lầm kinh điển: EM thực sự hội tụ về đâu?","score":82,"noteTitle":"EM: Thay thế X1"},{"title":"Bản chất thuật toán EM: Thay giá trị khuyết bằng kỳ vọng","score":88,"noteTitle":"EM: Thay thế X1"},{"title":"Bản chất trực giác của Hội tụ xác suất","score":85,"noteTitle":"Hội tụ xác suất"},{"title":"Phân biệt f(x|y), f(y|x) và f(x,y) qua góc nhìn cố định biến","score":85,"noteTitle":"Đủ và không chệch"},{"title":"E(X|Y) là con số hay biến ngẫu nhiên?","score":88,"noteTitle":"Đủ và không chệch"},{"title":"Hiểu bản chất phân phối F qua hai biến Chi-Square","score":88,"noteTitle":"Phân phối F và phương sai"},{"title":"Tại sao tỉ số phương sai mẫu ước lượng được phương sai thật?","score":86,"noteTitle":"Phân phối F và phương sai"},{"title":"Hai nút thắt khi tìm phân phối Y = g(X)","score":85,"noteTitle":"Khó khăn tính phân phối Y=g(X)"},{"title":"HPD vs Equal-Tailed: Chọn Khoảng Tin Cậy Bayes Nào?","score":88,"noteTitle":"Vùng HPD Poisson"},{"title":"Tìm Thống Kê Đủ Của Họ Hàm Mũ Bằng Định Lý Phân Tích","score":84,"noteTitle":"Thống kê đủ gia đình mũ"},{"title":"Bản chất thật của p-value: Một Test Statistic ngẫu nhiên","score":89,"noteTitle":"Định nghĩa và tính chất p-value"},{"title":"Tại sao so sánh p-value với alpha lại kiểm soát được Sai lầm Loại 1?","score":87,"noteTitle":"Định nghĩa và tính chất p-value"},{"title":"Bí quyết tìm p-value: Khi bài toán tối ưu Supremum hóa thành hằng số","score":89,"noteTitle":""},{"title":"Tại sao Likelihood Ratio Test lại tự động sinh ra Student t-test?","score":86,"noteTitle":""},{"title":"Cạm bẫy khi dùng CLT làm xấp xỉ vạn năng","score":80,"noteTitle":"Stronger Central Limit Theorem"},{"title":"Vì sao CLT bản mạnh không cần MGF?","score":86,"noteTitle":"Stronger Central Limit Theorem"},{"title":"Tuyệt chiêu toạ độ cực tính tích phân Gauss","score":93,"noteTitle":"Tích phân Hàm mật độ Chuẩn"},{"title":"Tại sao công thức phân phối Chuẩn lại có 1/σ?","score":84,"noteTitle":"Tích phân Hàm mật độ Chuẩn"},{"title":"Cầu nối đại số của CLT: Biến trung bình mẫu thành lũy thừa MGF","score":78,"noteTitle":"Proof of Theorem 5.5.14"},{"title":"Định lý Location-Scale: Vì sao PDF lại bị chia thêm σ?","score":85,"noteTitle":"Proof of Theorem 5.5.14"},{"title":"Nghịch lý ước lượng viên bằng hằng số: Vì sao không có MSE tốt nhất?","score":92,"noteTitle":"Ước lượng viên không chệch tốt nhất"},{"title":"Mẹo Đại số tuyến tính tính định thức Jacobian n×n trong tích phân xác suất","score":90,"noteTitle":"X̄ và S^2 độc lập"},{"title":"Chiến lược tách biến: Vì sao S² chỉ cần n-1 bậc tự do?","score":84,"noteTitle":"X̄ và S^2 độc lập"},{"title":"Bốc 4 lá cùng lúc hay bốc từng lá: Bản chất có giống nhau?","score":87,"noteTitle":"Xác suất rút 4 lá Ách"},{"title":"Người rút bài thứ hai có bị thiệt thòi?","score":93,"noteTitle":"Xác suất rút 4 lá Ách"},{"title":"Vì sao PIT thất bại trên biến ngẫu nhiên rời rạc?","score":86,"noteTitle":"Khoảng tin cậy Poisson"},{"title":"Xây dựng khoảng tin cậy chính xác cho phân phối Poisson","score":85,"noteTitle":"Khoảng tin cậy Poisson"},{"title":"Nghịch đảo UMP để tìm tập tin cậy UMA","score":82,"noteTitle":"Tập tin cậy UMA và UMP"},{"title":"Cách thiết lập Joint PDF cho mẫu từ phân phối Mũ","score":70,"noteTitle":"Mẫu ngẫu nhiên phân phối mũ"},{"title":"Bản chất thật sự của Mẫu ngẫu nhiên (Random Sample)","score":75,"noteTitle":"Mẫu ngẫu nhiên phân phối mũ"},{"title":"Tổng của các biến Nhị thức Âm: Story Proof không cần đại số","score":80,"noteTitle":"Xấp xỉ Chuẩn Nhị thức Âm"},{"title":"Hiểu bản chất công thức Phân phối Nhị thức Âm qua câu chuyện","score":88,"noteTitle":"Xấp xỉ Chuẩn Nhị thức Âm"},{"title":"Bẫy biến đổi không đơn điệu: Tại sao CDF của sin²(X) lại phức tạp?","score":88,"noteTitle":"CDF của sin^2(X) phức tạp"},{"title":"Bẫy Cận Tích Phân Khi Nghịch Đảo Kiểm Định","score":89,"noteTitle":"Khoảng tin cậy mũ vị trí"},{"title":"Mẹo dùng hàm chỉ thị tìm thống kê đủ","score":88,"noteTitle":"Thống kê đủ bằng hàm chỉ thị"},{"title":"Tại sao Bayesian tính được xác suất giả thuyết đúng?","score":85,"noteTitle":"Kiểm định giả thuyết Bayesian"},{"title":"Nhìn đồ thị CDF để biết biến rời rạc hay liên tục","score":78,"noteTitle":"Định nghĩa biến liên tục, rời rạc"},{"title":"Vì sao kiểm định Bayesian tự động dẫn về mẫu trung bình X̄?","score":88,"noteTitle":"Luật quyết định kiểm định Bayesian"},{"title":"Thống kê đủ tối thiểu có thực sự duy nhất?","score":75,"noteTitle":"Thống kê đủ tối thiểu"},{"title":"Ý nghĩa hình học của họ phân phối Location-Scale","score":82,"noteTitle":"Họ phân phối Location-Scale"},{"title":"Mối liên hệ đối ngẫu giữa Kiểm định và Khoảng tin cậy","score":82,"noteTitle":"Khoảng tin cậy và Kiểm định"},{"title":"Bản chất của Estimator: Tại sao là một hàm số?","score":76,"noteTitle":"Phương pháp tìm Estimator"},{"title":"Phân biệt Size α và Level α trong kiểm định giả thuyết","score":88,"noteTitle":"Size và Level α test"},{"title":"Chiến lược 2 vòng để tìm phép kiểm định tối ưu","score":84,"noteTitle":"Size và Level α test"},{"title":"Bản chất hàm rủi ro trong kiểm định giả thuyết","score":88,"noteTitle":"Cách tính hàm rủi ro"}] -->
`887 notes · 1,158 screenshots · 51 sections`

> This notebook contains detailed study notes and proofs based on Casella and Berger's *Statistical Inference*, covering key topics in probability theory, estimation methods, hypothesis testing, and asymptotic properties.
> 
> Sổ tay học tập này tổng hợp các ghi chép và chứng minh chi tiết dựa trên giáo trình *Statistical Inference* của Casella và Berger, bao gồm các chủ đề cốt lõi về lý thuyết xác suất, phương pháp ước lượng, kiểm định giả thuyết và tính chất tiệm cận.

<details open>
<summary>📖 51 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](statistical_inference_casella/_overview.md) | 0 | 1 |
| [1.1 Set Theory](statistical_inference_casella/11_set_theory.md) | 6 | 9 |
| [1.2.1 Axiomatic Foundation](statistical_inference_casella/121_axiomatic_foundation.md) | 9 | 10 |
| [1.2.2 Calculus Of Probability](statistical_inference_casella/122_calculus_of_probability.md) | 5 | 9 |
| [1.2.3 Counting](statistical_inference_casella/123_counting.md) | 6 | 8 |
| [1.2.4 Enumerating Outcome](statistical_inference_casella/124_enumerating_outcome.md) | 10 | 14 |
| [1.3 Conditional Probability & Independence](statistical_inference_casella/13_conditional_probability_independence.md) | 12 | 16 |
| [1.4 Random Variables](statistical_inference_casella/14_random_variables.md) | 4 | 5 |
| [1.5 Distribution Function](statistical_inference_casella/15_distribution_function.md) | 9 | 11 |
| [1.6 PDF & Pmf](statistical_inference_casella/16_pdf_pmf.md) | 4 | 5 |
| [2.1 Distribution](statistical_inference_casella/21_distribution.md) | 15 | 21 |
| [2.2 Expected Value](statistical_inference_casella/22_expected_value.md) | 7 | 10 |
| [2.3 MGF](statistical_inference_casella/23_mgf.md) | 15 | 25 |
| [2.4 Differentiating under integral](statistical_inference_casella/24_differentiating_under_integral.md) | 11 | 19 |
| [2.5 Ex](statistical_inference_casella/25_ex.md) | 1 | 2 |
| [3.1&2 Discrete distribution](statistical_inference_casella/312_discrete_distribution.md) | 20 | 32 |
| [3.3 Continuous distribution](statistical_inference_casella/33_continuous_distribution.md) | 24 | 38 |
| [3.4 Exponential families](statistical_inference_casella/34_exponential_families.md) | 10 | 15 |
| [3.5 Location And Scale Families](statistical_inference_casella/35_location_and_scale_families.md) | 12 | 17 |
| [3.6 Inequalities](statistical_inference_casella/36_inequalities.md) | 9 | 12 |
| [4.1 Joint & Marginal Distribution](statistical_inference_casella/41_joint_marginal_distribution.md) | 13 | 19 |
| [4.2 Conditional Distributions & Independent](statistical_inference_casella/42_conditional_distributions_independent.md) | 18 | 27 |
| [4.3 Bivariate Transformation](statistical_inference_casella/43_bivariate_transformation.md) | 14 | 24 |
| [4.4 Hierarchical Model & Mixture Distribution](statistical_inference_casella/44_hierarchical_model_mixture_distribution.md) | 11 | 19 |
| [4.5 Covariance & Correlation](statistical_inference_casella/45_covariance_correlation.md) | 18 | 25 |
| [4.6 Multi-variate Distribution](statistical_inference_casella/46_multi_variate_distribution.md) | 22 | 28 |
| [4.7 Inequalities](statistical_inference_casella/47_inequalities.md) | 1 | 0 |
| [5.1 Basic Concepts Of Random Samples](statistical_inference_casella/51_basic_concepts_of_random_samples.md) | 13 | 16 |
| [5.2 Σ Of Random Variables From A Random Sample](statistical_inference_casella/52_of_random_variables_from_a_random_sample.md) | 18 | 26 |
| [5.3 Sampling From The Normal Distribution](statistical_inference_casella/53_sampling_from_the_normal_distribution.md) | 21 | 29 |
| [5.4 Order Statistic](statistical_inference_casella/54_order_statistic.md) | 12 | 16 |
| [5.5 Convergence Concepts](statistical_inference_casella/55_convergence_concepts.md) | 42 | 52 |
| [5.6 Generating Random Sample](statistical_inference_casella/56_generating_random_sample.md) | 31 | 43 |
| [6.1 Introduction](statistical_inference_casella/61_introduction.md) | 3 | 4 |
| [6.2 The Sufficient Principle](statistical_inference_casella/62_the_sufficient_principle.md) | 46 | 59 |
| [6.3 The Likelihood Principle](statistical_inference_casella/63_the_likelihood_principle.md) | 19 | 23 |
| [6.4 The Equivariance Principle](statistical_inference_casella/64_the_equivariance_principle.md) | 11 | 14 |
| [7.1 Introduction](statistical_inference_casella/71_introduction.md) | 3 | 3 |
| [7.2 Method Of Finding Estimators](statistical_inference_casella/72_method_of_finding_estimators.md) | 42 | 52 |
| [7.3 Methods Of Evaluating Estimators](statistical_inference_casella/73_methods_of_evaluating_estimators.md) | 63 | 74 |
| [8.1 Introduction](statistical_inference_casella/81_introduction.md) | 5 | 5 |
| [8.2 Method Of Finding Tests](statistical_inference_casella/82_method_of_finding_tests.md) | 21 | 26 |
| [8.3 Methods Of Evaluating Test](statistical_inference_casella/83_methods_of_evaluating_test.md) | 53 | 64 |
| [9.1 Introduction](statistical_inference_casella/91_introduction.md) | 9 | 9 |
| [9.2 Methods Of Finding Interval Estimators](statistical_inference_casella/92_methods_of_finding_interval_estimators.md) | 52 | 61 |
| [9.3 Methods Of Evaluating Interval Estimators](statistical_inference_casella/93_methods_of_evaluating_interval_estimators.md) | 34 | 35 |
| [10.1 Point Estimation](statistical_inference_casella/101_point_estimation.md) | 42 | 48 |
| [10.2 Robustness](statistical_inference_casella/102_robustness.md) | 16 | 20 |
| [10.3 Hypothesis Testing](statistical_inference_casella/103_hypothesis_testing.md) | 22 | 26 |
| [10.4 Interval Estimation](statistical_inference_casella/104_interval_estimation.md) | 15 | 23 |
| [11.1 & 2 Introduction, One-way ANOVA](statistical_inference_casella/111_2_introduction_one_way_anova.md) | 8 | 9 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="group-other"></a>
### 📂 Other

<a id="nb-a1_llm"></a>
### LLM — Large Language Models
<!-- key: a1_llm -->
`478 notes · 505 screenshots · 4 sections`

> This notebook explores Large Language Models, covering their architecture, fine-tuning techniques like PEFT and RLHF, model evaluation, responsible AI considerations, and deployment strategies.

<details open>
<summary>📖 4 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](a1_llm/_overview.md) | 0 | 1 |
| [Week3 - Rhhf](a1_llm/week3_rhhf.md) | 153 | 169 |
| [Week 1_introduction To Llms And The Generative Ai Project Lifecycle](a1_llm/week_1_introduction_to_llms_and_the_generative_ai_project_lifecycle.md) | 181 | 179 |
| [Week 2 - Finetuning And Evaluating Large Language Model](a1_llm/week_2_finetuning_and_evaluating_large_language_model.md) | 144 | 156 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-deep_learning_specialization_cousera_andrew_ng"></a>
### Deep Learning Specialization_Cousera_Andrew Ng
<!-- key: deep_learning_specialization_cousera_andrew_ng -->
`634 notes · 1,827 screenshots · 6 sections`

> This notebook provides a comprehensive overview of core deep learning concepts, optimization techniques, and regularization methods. It also dives into building and applying various neural network architectures, from CNNs and RNNs to Transformers, for tasks like image segmentation, object detection, and natural language processing.

<details open>
<summary>📖 6 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](deep_learning_specialization_cousera_andrew_ng/_overview.md) | 0 | 1 |
| [Course 1 - Neural Networks & Deep Learning](deep_learning_specialization_cousera_andrew_ng/course_1_neural_networks_deep_learning.md) | 73 | 373 |
| [Course 2 - Improving Deep Neural Networks:](deep_learning_specialization_cousera_andrew_ng/course_2_improving_deep_neural_networks_hyperparams_tuning_regularization_optimization.md) | 103 | 302 |
| [Course 3 - Structuring Machine Learning Projects](deep_learning_specialization_cousera_andrew_ng/course_3_structuring_machine_learning_projects.md) | 64 | 87 |
| [Course 4 - Convolutional Neural Network](deep_learning_specialization_cousera_andrew_ng/course_4_convolutional_neural_network.md) | 168 | 478 |
| [Course 5 - Sequence Models](deep_learning_specialization_cousera_andrew_ng/course_5_sequence_models.md) | 226 | 586 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<a id="nb-foundation_of_llm"></a>
### Foundation of LLM
<!-- key: foundation_of_llm -->
`40 notes · 64 screenshots · 3 sections`

> This notebook explores the foundations of Large Language Models (LLMs), covering various pre-training strategies, key architectures like Encoder-Decoder, and techniques for fine-tuning and adapting these powerful models.

<details open>
<summary>📖 3 sections</summary>

| Section | Notes | Screenshots |
|---|---:|---:|
| [📋 Overview](foundation_of_llm/_overview.md) | 0 | 1 |
| [Giới thiệu Mô hình ngôn ngữ lớn](foundation_of_llm/gii_thiu_m_hnh_ngn_ng_ln.md) | 22 | 28 |
| [Tiền huấn luyện tự giám sát](foundation_of_llm/tin_hun_luyn_t_gim_st.md) | 18 | 35 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<!-- studyboard-videos:start -->
<a id="video-library"></a>
### 🎬 Video Library

**`48 videos · 3 topics`**

<a id="videos-optimization"></a>
#### 📂 Optimization

<details open>
<summary>🎬 7 videos</summary>

| Video | Ngày đăng |
|---|---|
| [Tại sao Lagrangian lồi ngặt giúp nghiệm Dual giải bài toán Primal?](https://www.youtube.com/watch?v=PzLtTlIO-kE) | 29/09/2026 |
| [Tại sao nghiệm KKT λ̃ làm cực đại hóa hàm đối ngẫu q(λ)?](https://www.youtube.com/watch?v=qSrfcPuiA4k) | 26/09/2026 |
| [Theorem 12.11 Weak Duality](https://www.youtube.com/watch?v=GtOATZjDGQs) | 26/09/2026 |
| [Tại sao hàm dual objective q(λ) luôn concave và domain 𝒟 lồi?](https://www.youtube.com/watch?v=UGddFxbogXU) | 25/09/2026 |
| [Vì sao Projected Hessian Zᵀ∇²LZ giúp kiểm tra cực tiểu dễ hơn?](https://youtu.be/oS8uhtEOI9w) | 20/09/2026 |
| [Vì sao df/dε = -λ\*\|\|∇ci\|\| khi thay đổi ràng buộc ci(x)?](https://youtu.be/6g2qIzX9yO0) | 20/09/2026 |
| [Tại sao nhân tử Lagrange λ\* = 0 khi ràng buộc không active?](https://www.youtube.com/watch?v=wy_PaBOEbnY) | 19/09/2026 |

</details>

<a id="videos-machine-learning-foundation"></a>
#### 📂 Machine Learning Foundation

<details open>
<summary>🎬 32 videos</summary>

| Video | Ngày đăng |
|---|---|
| [Tại sao ma trận Hessian Multiclass gồm các block M×M?](https://www.youtube.com/watch?v=Sz2QRKW9wLA) | 30/09/2026 |
| [Tại sao đạo hàm Cross-Entropy theo w\_j bằng (y\_nj - t\_nj)Φ\_n?](https://www.youtube.com/watch?v=SNbte9J7NL8) | 29/09/2026 |
| [Từ Likelihood suy ra Multiclass Cross-Entropy Loss như thế nào?](https://youtu.be/S4kORpAgTsQ) | 28/09/2026 |
| [Activation Derivative for Maximum Likelihood](https://www.youtube.com/watch?v=RfrcgvaQmgU) | 28/09/2026 |
| [Tại sao Class Posterior lại là Softmax tuyến tính của feature Φ?](https://www.youtube.com/watch?v=-9YldVmpmPU) | 25/09/2026 |
| [Vì sao xấp xỉ tuyến tính Sigmoid biến Logistic Regression thành Least Squares?](https://www.youtube.com/watch?v=qAxY0gbf8rM) | 25/09/2026 |
| [Vì sao nghiệm IRLS lại có dạng Weighted Least Squares?](https://www.youtube.com/watch?v=uW9swHIgaPw) | 24/09/2026 |
| [Tại sao Newton-Raphson trong Logistic Regression lại ra Weighted Least Squares?](https://www.youtube.com/watch?v=OefUwDAl93Q) | 24/09/2026 |
| [Mẹo dùng vi phân vector để tìm ma trận Hessian của Logistic Regression chỉ trong 3 phút.](https://www.youtube.com/watch?v=FZ8WIyEcWwk) | 24/09/2026 |
| [Vì sao Newton-Raphson giải Linear Regression chỉ trong đúng 1 bước?](https://www.youtube.com/watch?v=KQozp2d2dy8) | 23/09/2026 |
| [Cách tự derive gradient và Hessian của hàm quadratic](https://www.youtube.com/watch?v=kI2yukn25aQ) | 23/09/2026 |
| [Tại sao bước lặp Newton dùng xấp xỉ bậc hai cục bộ?](https://www.youtube.com/watch?v=yOm1k_DQ3K0) | 23/09/2026 |
| [Tại sao MLE làm norm của W tiến ra vô cực?](https://www.youtube.com/watch?v=XzhGTA5AeNU) | 22/09/2026 |
| [Learning with me: Maximum Likelihood on Linearly Separable Data](https://www.youtube.com/watch?v=LNW4K9FY_As) | 22/09/2026 |
| [Tại sao Cross-Entropy Loss thực chất là Negative Log-Likelihood?](https://www.youtube.com/watch?v=IJMvYy5NB-k) | 21/09/2026 |
| [Tại sao đạo hàm hàm Sigmoid lại bằng σ(1 - σ)?](https://www.youtube.com/watch?v=W4pQ_271eXE) | 21/09/2026 |
| [Tại sao Logistic Regression chỉ tốn M tham số thay vì M(M+5)/2+1?](https://www.youtube.com/watch?v=YN8gyl1HEAA) | 18/09/2026 |
| [Vì Sao Basis Function ϕ(x) Biến Dữ Liệu Thành Linearly Separable?](https://www.youtube.com/watch?v=5kKAasvIeGI) | 18/09/2026 |
| [Tại sao nên giả định trực tiếp f(C\|x) thay vì ước lượng f(x\|C)?](https://www.youtube.com/watch?v=OMWS53GIrUI) | 18/09/2026 |
| [Vì sao họ Exponential với scale chung cho Log-odds tuyến tính?](https://www.youtube.com/watch?v=Ovmp-M7j5II) | 17/09/2026 |
| [Vì sao giáo sư Bishop gọi S1, S2 là covariance matrix](https://www.youtube.com/watch?v=E55dfUAdwjE) | 17/09/2026 |
| [Vì sao Naive Bayes giảm số tham số từ 2^D xuống D?](https://www.youtube.com/watch?v=jbPysqwE8nc) | 17/09/2026 |
| [Vì sao ma trận hiệp phương sai chung Σ bằng S?](https://www.youtube.com/watch?v=2Dy41xan6xg) | 17/09/2026 |
| [Tại sao ma trận hiệp phương sai MLE chung lại bằng S?](https://www.youtube.com/watch?v=STiYw1o_W1E) | 16/09/2026 |
| [Tại sao nghiệm MLE của 𝜍1 lại chính là trung bình mẫu?](https://www.youtube.com/watch?v=ZI3dek5QaCc) | 16/09/2026 |
| [Tại sao không tối ưu Perceptron bằng số ca phân loại sai?](https://www.youtube.com/watch?v=PEL_sI4YGSg) | 11/09/2026 |
| [Vì sao Least Squares lại cho cùng nghiệm w với Fisher Criterion?](https://www.youtube.com/watch?v=AxZbMJ3AD1E) | 09/09/2026 |
| [Làm sao chọn threshold cho Fisher Discriminant nhờ CLT và MLE?](https://www.youtube.com/watch?v=fuo5lM8PyCk) | 08/09/2026 |
| [Vì sao hướng tối ưu w của Fisher là Sw⁻¹(m2 - m1)?](https://www.youtube.com/watch?v=XWXHBKtAWK0) | 08/09/2026 |
| [Tại sao vectơ chiếu w phải song song với đường nối hai tâm?](https://www.youtube.com/watch?v=9rn2c18KCbI) | 05/09/2026 |
| [Vì sao Least Squares phân loại kém do giả định Gaussian?](https://www.youtube.com/watch?v=TSv9sh-O1Os) | 05/09/2026 |
| [Dự đoán "Quá đúng" lại bị SSE phạt nặng, hạn chế của mô hình phân loại tuyến tính theo least square](https://www.youtube.com/watch?v=D1LgZ77Hxgs) | 04/09/2026 |

</details>

<a id="videos-probability-statistics"></a>
#### 📂 Probability & Statistics

<details open>
<summary>🎬 9 videos</summary>

| Video | Ngày đăng |
|---|---|
| [Vì sao dùng √λ tốt hơn S cho khoảng tin cậy Poisson?](https://www.youtube.com/watch?v=qi2c2LvaefU) | 23/09/2026 |
| [Tại sao nghịch đảo Score Test ra khoảng tin cậy cho p?](https://www.youtube.com/watch?v=UO_2KJVR6fY) | 22/09/2026 |
| [Cách đảo ngược acceptance region thành khoảng tin cậy cho μ?](https://www.youtube.com/watch?v=OcJDysX87L0) | 21/09/2026 |
| [Thế nào là point estimation, confidence interval và hypothesis testing](https://www.youtube.com/watch?v=nC7WkJULeTs) | 21/09/2026 |
| [Cách lập phương trình bậc hai tìm khoảng tin cậy Binomial Score?](https://www.youtube.com/watch?v=t5L8jQeG_nU) | 18/09/2026 |
| [Tại sao \[h(θ̂) - h(θ)\] / √Var^(h(θ̂)) hội tụ về N(0,1)?](https://www.youtube.com/watch?v=beyWo5KCi6c) | 11/09/2026 |
| [Làm sao xây dựng Generalized Wald Test từ M-estimator?](https://www.youtube.com/watch?v=Z_OW_2fvLbE) | 08/09/2026 |
| [Vì Sao Kỳ Vọng Của Score Statistic E\_θ\[S(θ)\] Bằng 0?](https://www.youtube.com/watch?v=RBcsZYaHM-Q) | 05/09/2026 |
| [Large-Sample Binomial Tests](https://www.youtube.com/watch?v=UmyowzIGpGE) | 03/09/2026 |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<!-- studyboard-videos:end -->

<!-- studyboard-roadmap:start -->
<a id="video-roadmap"></a>
### 🗺️ Video Roadmap

> [!NOTE]
> Ý tưởng video điểm cao nhất **chưa quay** — top 50 mỗi chủ đề. Đây là kế hoạch, không phải video đã có.

<a id="roadmap-probability-statistics"></a>
#### 📂 Probability & Statistics

<details open>
<summary>🗺️ 50 ý tưởng sắp tới</summary>

| Điểm | Ý tưởng | Note gốc |
|---|---|---|
| `95` | *Trực giác Neyman-Pearson: Nghệ thuật xài hết ngân sách rủi ro* | Định lý Neyman-Pearson |
| `95` | *Ném vòng hay Bắt chim: Phân biệt Confidence và Credible Interval* | Xác suất đáng tin cậy và độ phủ |
| `95` | *Nguồn gốc Binary Cross-Entropy từ MLE Bernoulli* | Ước lượng hợp lý cực đại Bernoulli |
| `94` | *Ai mới là biến ngẫu nhiên trong Khoảng tin cậy?* | Hàm mất mát và rủi ro |
| `94` | *Nghịch lý ba tù nhân và cái bẫy trực giác 1/2* | Bài toán ba tù nhân |
| `93` | *Credible Interval vs Confidence Interval: Đâu mới là khoảng xác suất thực sự?* | Lý thuyết và Ước lượng Bayesian |
| `93` | *Unbiased Test: Khi sai số Loại 1 cực thấp vẫn là kiểm định vô dụng* | Đặc điểm kiểm định giả thuyết |
| `93` | *Tìm MLE không cần đạo hàm* | Tìm MLE không đạo hàm |
| `93` | *Trực giác đằng sau Kiểm định Tỉ số Hợp lý (LRT)* | Nguyên lý Kiểm định tỉ số hợp lý |
| `93` | *Vì sao không gian mẫu đều nhưng biến ngẫu nhiên lại lệch?* | Xác suất cảm sinh biến ngẫu nhiên |
| `93` | *Ngộ nhận 90% về khoảng tin cậy* | Diễn giải khoảng tin cậy |
| `93` | *Kỹ thuật đảo ngược kiểm định để tìm khoảng tin cậy* | Đảo ngược test statistic |
| `93` | *Trực quan hóa đánh đổi Sai lầm Loại I và II bằng hàm Power* | Kiểm định giả thuyết nhị thức |
| `93` | *Bất ngờ khi hàm mất mát L1 và L2 cho cùng một ước lượng Bayes* | Ước lượng Bayes chuẩn |
| `93` | *Tuyệt chiêu toạ độ cực tính tích phân Gauss* | Tích phân Hàm mật độ Chuẩn |
| `93` | *Người rút bài thứ hai có bị thiệt thòi?* | Xác suất rút 4 lá Ách |
| `92` | *Chứng minh Lehmann-Scheffé bằng Adam's Law* | Ước lượng không chệch tốt nhất |
| `92` | *Từ Poisson Đến Exponential: Bản Chất Của Thời Gian Chờ* | Giá trị kỳ vọng phân phối mũ |
| `92` | *Bản chất công thức Nhị thức âm: Khóa vị trí chốt sổ* | Lập luận PMF nhị thức âm |
| `92` | *Bí thuật khử tham số trong Fisher's Exact Test* | Kiểm định chính xác Fisher |
| `92` | *Chứng minh xác suất tại một điểm bằng 0* | Chứng minh P(X=x)=0 |
| `92` | *Bản chất khoảng tin cậy: Tập hợp các giả thuyết không bị bác bỏ* | Xây dựng tập tin cậy |
| `92` | *Tại sao phương sai mẫu chia cho n - 1?* | Tính chất trung bình phương sai mẫu |
| `92` | *Ước lượng Bayes chuẩn: Giằng co giữa niềm tin và dữ liệu* | Ước lượng Bayes phân phối chuẩn |
| `92` | *Tại sao sai số bình phương thất bại khi ước lượng phương sai? (Stein Loss)* | Ước lượng phương sai: Stein Loss |
| `92` | *Bản chất toán học của P-value: Tại sao Sup luôn đạt tại biên?* | P-value một phía của LRT |
| `92` | *Bí quyết triệt tiêu θ trong MSE của ước lượng bất biến* | MSE ước lượng bất biến |
| `92` | *Trực quan hóa Thống kê đủ tối tiểu: Tại sao lại là phân hoạch thô nhất?* | Thống kê đủ tối tiểu |
| `92` | *Rao-Blackwell bắt tay Completeness: Công thức săn lùng ước lượng vô địch* | Thống kê đủ & Ước lượng tốt nhất |
| `92` | *Mẹo đặt biến phụ để chứng minh tích chập Z = X + Y* | Công thức tích chập Z=X+Y |
| `92` | *Tại sao chặn trên của Z lại biến thành chặn dưới của mu?* | Tối ưu độ dài khoảng tin cậy |
| `92` | *Tại sao cải tiến ước lượng bắt buộc phải dùng thống kê đủ?* | Điều kiện hóa thống kê không đủ |
| `92` | *Story Proof: Đẳng thức chọn nhóm trưởng* | Phương pháp tính kỳ vọng Binomial |
| `92` | *Nghịch lý kiểm định: Khi thống kê 'quá đủ' làm sập Power* |  |
| `92` | *Bản chất hình học của xác suất phủ sai* | Xác suất phủ sai |
| `92` | *Nghịch lý Cramer-Rao: Khi phương sai nhỏ hơn cả cận dưới* | Cramer-Rao: Vi phạm giả định |
| `92` | *Vì sao khoảng tin cậy có thể bị đứt đoạn? (Phương pháp Sterne)* | Phương pháp Sterne |
| `92` | *Hiểu lầm kinh điển: Ước lượng Bayes có luôn là Posterior Mean?* | Ước lượng Bayes và Hàm mất mát |
| `92` | *Nghịch lý thống kê: Vì sao ước lượng chệch lại xịn hơn không chệch?* | Ước lượng chệch MSE |
| `92` | *Giải mã MGF: Tại sao E\[e^(tX)\] lại là hàm theo t?* | Phân phối lấy mẫu X̄ |
| `92` | *Nghịch lý đảo kiểm định: Vì sao giả thuyết 'nhỏ hơn' lại sinh ra chặn trên?* | Giới hạn tin cậy trên |
| `92` | *Khoảng tin cậy thực chất chỉ là kiểm định bị đảo ngược* | Mối liên hệ Kiểm định - Khoảng tin cậy |
| `92` | *Phân biệt Loss Function, Risk Function và MSE* | Risk function: MSE |
| `92` | *Định lý Birnbaum: Mẹo tung đồng xu hợp nhất hai thí nghiệm* | Mở rộng Nguyên lý Hợp lý |
| `92` | *Cạm bẫy Likelihood khi tham số nằm trong Support* | Hàm hợp lí Exponential |
| `92` | *Bản chất P(A\|B): Khi không gian mẫu bị thu hẹp* | Phân biệt P(A) và P(A\|B) |
| `92` | *Tại sao phương sai mẫu chia cho n - 1 thay vì n?* | Ước lượng không chệch |
| `92` | *Mẹo tính kỳ vọng tỷ lệ bằng Định lý Basu* | Kỳ vọng theo Định lý Basu |
| `92` | *Nghịch lý Cauchy: Vì sao gom 1 triệu mẫu vẫn không giảm sai số?* | Trung bình mẫu Location Scale |
| `92` | *Khi CDF bị 'phẳng': Bí mật định nghĩa Infimum trong Hàm Phân Vị* | Tính phổ quát của Uniform(0,1) |

</details>

<sub>[↑ Back to navigation](#top-nav)</sub>

<!-- studyboard-roadmap:end -->

---

*📚 Notes exported with [StudyBoard](https://studyboard.app/landing.html) — build your personal learning repository.*