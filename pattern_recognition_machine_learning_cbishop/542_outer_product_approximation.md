# 5.4.2 Outer product approximation

📊 **Progress:** `1` Notes | `1` Screenshots

---
<a id="node-u0cqcsg"></a>

<br>

<a id="node-4mv1qsv"></a>

## Outer Product Approximation

<p align="center"><kbd><img src="assets/q4izhcvg4zh.png" width="80%"></kbd></p>

> [!NOTE]
> E = (1/2) Σn (yn - tn)²
>
>
>
> ∇E = ∇\[(1/2) Σn (yn - tn)²\]
>
>
>
> = (1/2) ∇\[Σn (yn - tn)²\]
>
>
>
> = (1/2) Σn \[∇(yn - tn)²\]
>
>
>
> = (1/2) Σn \[d/d(yn - tn) (yn - tn)² . ∇(yn - tn)\]
>
>
>
> ∇E = Σn \[(yn - tn) ∇yn\]
>
>
>
> 𝐇 = ∇∇E = ∇\[Σn \[(yn - tn) ∇yn\]\]
>
>
>
> = Σn ∇\[(yn - tn) ∇yn\]
>
>
>
> = Σn \[∇(yn - tn) × ∇yn + (yn - tn) ∇∇yn\]
>
>
>
> = Σn \[∇yn × ∇yn + (yn - tn) ∇∇yn\]
>
>
>
> = Σn ∇yn ∇yn + Σn (yn - tn) ∇∇yn → 5.83

📹 [Xem video trên YouTube](https://www.youtube.com/watch?v=uF2pBk9VPxg)

<br>

