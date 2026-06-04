---
layout: post
title: "Position: Neural Approximation Is Rarely Justified for Hard Combinatorial Problems"
date: 2026-06-02
permalink: /posts/2026/06/neural-combinatorial-blog/
use_mathjax: true
tags:
  - icml
  - combinatorial optimization
  - position paper
---

The last decade has seen a steady stream of neural approaches to NP-hard combinatorial problems — TSP, maximum clique, subgraph isomorphism, vehicle routing. The pitch is usually the same: faster inference, or better solution quality, compared to classical solvers. In this position paper, we push back on that framing, as the conditions under which these neural approaches are genuinely useful are much narrower than the literature implies.

---

## What prior papers aren't telling you

For supervised methods, generating ground-truth labels means running the corresponding classical solvers over (possibly large) datasets of combinatorial instances. Examples include pointer networks (Vinyals et al., 2015), which use the Held-Karp algorithm and the Christofides heuristic to label training instances, and graph-based TSP methods (Joshi et al., 2019) which generate a *million* training instances all labeled by the Concorde solver. These are not negligible costs, yet they are often treated as either one-time or not worth mentioning. For reinforcement learning methods, training costs are just as steep — Bello et al. train over a million episodes; POMO performs multiple greedy rollouts during both training and inference. In all cases, the accounting is rarely explicit.

Yet another issue is the use of synthetic training data, which is not sampled from real-world distributions. One example of this is in neural TSP methods that spawn their instances by sampling points uniformly at random in the plane. This is a dealbreaker because the hardness of a combinatorial instance may depend on its structural properties — for e.g., graph planarity, treewidth, perfectness, geometric regularity. For Euclidean TSP, near-optimal polynomial-time approximation algorithm (PTAS) results are well-known (Arora, 1998). Maximum clique and graph coloring are polynomial-time on perfect graphs (Grotschel et al., 1984). Subgraph isomorphism simplifies on bounded-treewidth graphs (Eppstein, 2002). Thus, without characterizing where these synthetic instances sit in this landscape, one cannot tell whether they are evaluating neural methods on *genuinely hard instances* at all, or on distributions that classical methods already handle efficiently.

Our position paper develops a costs-and-guarantees accounting framework for such neural surrogates. We omit that in this blog and instead focus on pertinent problems with existing neural approaches. Our goal is to draw attention to the gaps that have been overlooked so far.

---

## The decoder problem

A recurring pattern that the community has largely overlooked: most neural combinatorial methods attach a classical algorithm at the end — beam search, greedy decoding, local search, branch-and-bound — to convert continuous neural outputs into feasible discrete solutions. The neural component handles representation; the decoder handles the hard part of actually constructing a valid solution. Empirical evaluations almost never ablate the decoder's contribution.

We tested this directly on the clique number estimation problem, using the corresponding decoders from three recent methods - DIFUSCO (Sun et al. 2023), EGN (Karalias et al. 2020), and SCT (Minskiy et al., 2022) - and replacing the neural scores with simple structural inputs: uniform random scores, node degrees, and core numbers.

**Table 1.** MSE for clique number estimation (lower is better). *Neural* is the original published method; *Random*, *Degree*, and *Core* feed non-neural inputs directly to the same decoder. Best score per method–dataset pair is **bolded**.

<div style="overflow-x:auto; margin: 1.5em 0;">
<table style="border-collapse:collapse; width:100%; font-size:0.9em;">
  <thead>
    <tr style="border-bottom:2px solid #ccc;">
      <th style="text-align:left; padding:8px 14px;">Method</th>
      <th style="text-align:left; padding:8px 14px;">Variant</th>
      <th style="text-align:right; padding:8px 14px;">IMDB</th>
      <th style="text-align:right; padding:8px 14px;">RB</th>
      <th style="text-align:right; padding:8px 14px;">Brock</th>
      <th style="text-align:right; padding:8px 14px;">DSJC</th>
      <th style="text-align:right; padding:8px 14px;">MUTAG</th>
      <th style="text-align:right; padding:8px 14px;">Enzymes</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding:6px 14px;">DIFUSCO</td><td style="padding:6px 14px;">Neural</td><td style="text-align:right; padding:6px 14px;">1.361</td><td style="text-align:right; padding:6px 14px;">55.630</td><td style="text-align:right; padding:6px 14px;">10.590</td><td style="text-align:right; padding:6px 14px;">1.560</td><td style="text-align:right; padding:6px 14px;">10.965</td><td style="text-align:right; padding:6px 14px;">0.950</td></tr>
    <tr><td style="padding:6px 14px;">DIFUSCO</td><td style="padding:6px 14px;">Random</td><td style="text-align:right; padding:6px 14px;">2.796</td><td style="text-align:right; padding:6px 14px;">82.180</td><td style="text-align:right; padding:6px 14px;">93.180</td><td style="text-align:right; padding:6px 14px;">140.110</td><td style="text-align:right; padding:6px 14px;">11.900</td><td style="text-align:right; padding:6px 14px;">1.109</td></tr>
    <tr><td style="padding:6px 14px;">DIFUSCO</td><td style="padding:6px 14px;">Degree</td><td style="text-align:right; padding:6px 14px;">2.991</td><td style="text-align:right; padding:6px 14px;">47.335</td><td style="text-align:right; padding:6px 14px;">6.245</td><td style="text-align:right; padding:6px 14px;"><strong>0.680</strong></td><td style="text-align:right; padding:6px 14px;">8.785</td><td style="text-align:right; padding:6px 14px;"><strong>0.504</strong></td></tr>
    <tr style="border-bottom:1px solid #eee;"><td style="padding:6px 14px;">DIFUSCO</td><td style="padding:6px 14px;">Core</td><td style="text-align:right; padding:6px 14px;"><strong>0.102</strong></td><td style="text-align:right; padding:6px 14px;">69.565</td><td style="text-align:right; padding:6px 14px;">53.730</td><td style="text-align:right; padding:6px 14px;">65.885</td><td style="text-align:right; padding:6px 14px;"><strong>10.535</strong></td><td style="text-align:right; padding:6px 14px;">0.706</td></tr>
    <tr><td style="padding:6px 14px;">EGN</td><td style="padding:6px 14px;">Neural</td><td style="text-align:right; padding:6px 14px;">0.102</td><td style="text-align:right; padding:6px 14px;">15.615</td><td style="text-align:right; padding:6px 14px;">1.310</td><td style="text-align:right; padding:6px 14px;">0.030</td><td style="text-align:right; padding:6px 14px;">1.010</td><td style="text-align:right; padding:6px 14px;">0.109</td></tr>
    <tr><td style="padding:6px 14px;">EGN</td><td style="padding:6px 14px;">Random</td><td style="text-align:right; padding:6px 14px;"><strong>0.000</strong></td><td style="text-align:right; padding:6px 14px;"><strong>3.270</strong></td><td style="text-align:right; padding:6px 14px;"><strong>0.560</strong></td><td style="text-align:right; padding:6px 14px;"><strong>0.035</strong></td><td style="text-align:right; padding:6px 14px;">2.715</td><td style="text-align:right; padding:6px 14px;"><strong>0.008</strong></td></tr>
    <tr><td style="padding:6px 14px;">EGN</td><td style="padding:6px 14px;">Degree</td><td style="text-align:right; padding:6px 14px;">3.065</td><td style="text-align:right; padding:6px 14px;">47.745</td><td style="text-align:right; padding:6px 14px;">17.640</td><td style="text-align:right; padding:6px 14px;">0.815</td><td style="text-align:right; padding:6px 14px;">9.320</td><td style="text-align:right; padding:6px 14px;">0.538</td></tr>
    <tr style="border-bottom:1px solid #eee;"><td style="padding:6px 14px;">EGN</td><td style="padding:6px 14px;">Core</td><td style="text-align:right; padding:6px 14px;">0.111</td><td style="text-align:right; padding:6px 14px;">66.975</td><td style="text-align:right; padding:6px 14px;">52.240</td><td style="text-align:right; padding:6px 14px;">61.655</td><td style="text-align:right; padding:6px 14px;">10.675</td><td style="text-align:right; padding:6px 14px;">0.782</td></tr>
    <tr><td style="padding:6px 14px;">SCT</td><td style="padding:6px 14px;">Neural</td><td style="text-align:right; padding:6px 14px;">4.102</td><td style="text-align:right; padding:6px 14px;">50.230</td><td style="text-align:right; padding:6px 14px;">35.885</td><td style="text-align:right; padding:6px 14px;">92.675</td><td style="text-align:right; padding:6px 14px;">11.105</td><td style="text-align:right; padding:6px 14px;">0.891</td></tr>
    <tr><td style="padding:6px 14px;">SCT</td><td style="padding:6px 14px;">Random</td><td style="text-align:right; padding:6px 14px;"><strong>0.000</strong></td><td style="text-align:right; padding:6px 14px;"><strong>14.705</strong></td><td style="text-align:right; padding:6px 14px;"><strong>1.370</strong></td><td style="text-align:right; padding:6px 14px;">2.590</td><td style="text-align:right; padding:6px 14px;">3.950</td><td style="text-align:right; padding:6px 14px;"><strong>0.042</strong></td></tr>
    <tr><td style="padding:6px 14px;">SCT</td><td style="padding:6px 14px;">Degree</td><td style="text-align:right; padding:6px 14px;">2.185</td><td style="text-align:right; padding:6px 14px;">40.955</td><td style="text-align:right; padding:6px 14px;">6.605</td><td style="text-align:right; padding:6px 14px;"><strong>0.740</strong></td><td style="text-align:right; padding:6px 14px;">8.740</td><td style="text-align:right; padding:6px 14px;">0.269</td></tr>
    <tr><td style="padding:6px 14px;">SCT</td><td style="padding:6px 14px;">Core</td><td style="text-align:right; padding:6px 14px;">0.074</td><td style="text-align:right; padding:6px 14px;">49.935</td><td style="text-align:right; padding:6px 14px;">42.240</td><td style="text-align:right; padding:6px 14px;">54.160</td><td style="text-align:right; padding:6px 14px;">7.190</td><td style="text-align:right; padding:6px 14px;">0.311</td></tr>
  </tbody>
</table>
</div>

The pattern is consistent: across most method–dataset combinations, the decoder performs competitively or better when given simple structural heuristics than when given the neural scores from the published method.

---

## The distribution shift problem

The distribution sensitivity of neural combinatorial methods is well-known in principle but underexamined in practice. We constructed an out-of-distribution split of the PTC-MM dataset by partitioning by instance size, so that test graphs are larger than training graphs.

**Table 2.** Clique number estimation MSE on PTC-MM under default and OOD (out-of-distribution by instance size) splits. Best score per row is **bolded**.

<div style="overflow-x:auto; margin: 1.5em 0;">
<table style="border-collapse:collapse; font-size:0.9em;">
  <thead>
    <tr style="border-bottom:2px solid #ccc;">
      <th style="text-align:left; padding:8px 20px;">Method</th>
      <th style="text-align:left; padding:8px 20px;">Split</th>
      <th style="text-align:right; padding:8px 20px;">Neural</th>
      <th style="text-align:right; padding:8px 20px;">Random</th>
      <th style="text-align:right; padding:8px 20px;">Degree</th>
      <th style="text-align:right; padding:8px 20px;">Core</th>
      <th style="text-align:right; padding:8px 20px;">ClusterCoef</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding:6px 20px;">EGN</td><td style="padding:6px 20px;">Default</td><td style="text-align:right; padding:6px 20px;"><strong>0.284</strong></td><td style="text-align:right; padding:6px 20px;">0.745</td><td style="text-align:right; padding:6px 20px;">2.396</td><td style="text-align:right; padding:6px 20px;">1.943</td><td style="text-align:right; padding:6px 20px;">0.859</td></tr>
    <tr style="border-bottom:1px solid #eee;"><td style="padding:6px 20px;">EGN</td><td style="padding:6px 20px;">OOD</td><td style="text-align:right; padding:6px 20px;">3.260</td><td style="text-align:right; padding:6px 20px;"><strong>1.359</strong></td><td style="text-align:right; padding:6px 20px;">4.255</td><td style="text-align:right; padding:6px 20px;">3.513</td><td style="text-align:right; padding:6px 20px;">1.160</td></tr>
    <tr><td style="padding:6px 20px;">SCT</td><td style="padding:6px 20px;">Default</td><td style="text-align:right; padding:6px 20px;">1.802</td><td style="text-align:right; padding:6px 20px;"><strong>0.402</strong></td><td style="text-align:right; padding:6px 20px;">1.838</td><td style="text-align:right; padding:6px 20px;">1.072</td><td style="text-align:right; padding:6px 20px;">0.556</td></tr>
    <tr><td style="padding:6px 20px;">SCT</td><td style="padding:6px 20px;">OOD</td><td style="text-align:right; padding:6px 20px;">1.256</td><td style="text-align:right; padding:6px 20px;">0.818</td><td style="text-align:right; padding:6px 20px;">3.406</td><td style="text-align:right; padding:6px 20px;">1.707</td><td style="text-align:right; padding:6px 20px;"><strong>0.636</strong></td></tr>
  </tbody>
</table>
</div>

EGN's neural MSE increases more than tenfold under shift (0.284 → 3.260), while the random baseline degrades far more gracefully (0.745 → 1.359). SCT's behavior is even more striking: its MSE actually *decreases* under OOD shift. This is not a sign of robustness — it reflects the opacity of neural generalization. Unlike, for e.g., a branch-and-bound solver, which provides a duality gap and well-understood failure modes at every point during execution, neural surrogates can fail silently and unpredictably.

The response to distribution shift is also costly: since labels must be regenerated and the model retrained for each new instance regime, the "one-time cost" defense of training expense collapses the moment the deployment distribution drifts. The table below makes this concrete.

**Table 3.** Per-instance inference time vs. total training time for EGN and DIFUSCO on the clique number estimation problem, trained with early stopping on a single RTX A6000.

<div style="overflow-x:auto; margin: 1.5em 0;">
<table style="border-collapse:collapse; font-size:0.9em;">
  <thead>
    <tr style="border-bottom:2px solid #ccc;">
      <th style="text-align:left; padding:8px 20px;">Method</th>
      <th style="text-align:left; padding:8px 20px;">Dataset</th>
      <th style="text-align:right; padding:8px 20px;">Inference / query (s)</th>
      <th style="text-align:right; padding:8px 20px;">Training time</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding:6px 20px;">EGN</td><td style="padding:6px 20px;">IMDB</td><td style="text-align:right; padding:6px 20px;">0.117</td><td style="text-align:right; padding:6px 20px;">~26 h</td></tr>
    <tr><td style="padding:6px 20px;">EGN</td><td style="padding:6px 20px;">DSJC</td><td style="text-align:right; padding:6px 20px;">0.152</td><td style="text-align:right; padding:6px 20px;">~19 h</td></tr>
    <tr><td style="padding:6px 20px;">EGN</td><td style="padding:6px 20px;">RB</td><td style="text-align:right; padding:6px 20px;">0.201</td><td style="text-align:right; padding:6px 20px;">~15.5 h</td></tr>
    <tr style="border-bottom:1px solid #eee;"><td style="padding:6px 20px;">EGN</td><td style="padding:6px 20px;">MUTAG</td><td style="text-align:right; padding:6px 20px;">0.473</td><td style="text-align:right; padding:6px 20px;">~23 h</td></tr>
    <tr><td style="padding:6px 20px;">DIFUSCO</td><td style="padding:6px 20px;">IMDB</td><td style="text-align:right; padding:6px 20px;">0.789</td><td style="text-align:right; padding:6px 20px;">~1 h</td></tr>
    <tr><td style="padding:6px 20px;">DIFUSCO</td><td style="padding:6px 20px;">Brock</td><td style="text-align:right; padding:6px 20px;">0.796</td><td style="text-align:right; padding:6px 20px;">~3.5 h</td></tr>
    <tr><td style="padding:6px 20px;">DIFUSCO</td><td style="padding:6px 20px;">MUTAG</td><td style="text-align:right; padding:6px 20px;">0.827</td><td style="text-align:right; padding:6px 20px;">~14.5 h</td></tr>
  </tbody>
</table>
</div>

Training times range from 1 to 26 hours even with early stopping, while per-instance inference is sub-second throughout. The amortization argument requires the deployment distribution to remain stable — also known as the no-distribution-shift assumption - failing which these costs are borne repeatedly.

---

## When neural methods *are* justified

We don't claim neural approaches to hard combinatorial problems are useless — we claim the community has been asking the wrong question. The right question is not "can a neural method match or beat a classical solver?", but "is there a genuine requirement for a neural method here?"

We elicit three situations that genuinely justify the use of neural methods:

**End-to-end differentiability.** When a combinatorial problem appears as an intermediate step in a larger learning pipeline, a classical solver blocks gradient propagation. Neural gadgets that approximate the combinatorial layer and support backprop are justified here even if they are slower or less accurate than a standalone solver. Graph retrieval is a clean example: the downstream objective is relevance ranking, and backpropagating through the subgraph matching layer allows fine-tuning encoders end-to-end.

**System-level serving constraints.** Large-scale retrieval and recommendation systems cannot issue a solver call per query at inference time. The serving stack requires embedding functions compatible with approximate nearest-neighbor indices and fast vector operations — user or query objects are mapped to vectors, corpus items are pre-indexed, and scoring operates via inexpensive vector similarity operations. In this regime the neural surrogate is not competing with a classical solver on solution quality; it is compressing a complex utility function into an embedding space so that approximate nearest neighbour algorithms can be applied. The combinatorial problem gets solved offline, at index construction time, or on a small filtered candidate set. However, the online path must be neural.

We illustrate where this justification holds using a graph retrieval system (Chakraborty et al., 2025) as a concrete example. A FAISS-based LSH index built on neural embeddings filters the full corpus down to a small candidate set; those candidates are then re-scored by an oracle combinatorial solver. This setup is compared to full-corpus oracle scoring.

**Table 4.** Full-corpus oracle scoring vs. LSH+Oracle on PTC datasets. The neural index provides a 20–40× speedup while preserving near-perfect MAP@100.

<div style="overflow-x:auto; margin: 1.5em 0;">
<table style="border-collapse:collapse; font-size:0.9em;">
  <thead>
    <tr style="border-bottom:2px solid #ccc;">
      <th style="text-align:left; padding:8px 20px;">Dataset</th>
      <th style="text-align:right; padding:8px 20px;">Oracle time / query (s)</th>
      <th style="text-align:right; padding:8px 20px;">LSH+Oracle time / query (s)</th>
      <th style="text-align:right; padding:8px 20px;">LSH+Oracle MAP@100</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding:6px 20px;">PTC-FR</td><td style="text-align:right; padding:6px 20px;">26.07</td><td style="text-align:right; padding:6px 20px;">0.915</td><td style="text-align:right; padding:6px 20px;">1.00</td></tr>
    <tr><td style="padding:6px 20px;">PTC-FM</td><td style="text-align:right; padding:6px 20px;">49.34</td><td style="text-align:right; padding:6px 20px;">1.153</td><td style="text-align:right; padding:6px 20px;">0.98</td></tr>
    <tr><td style="padding:6px 20px;">PTC-MR</td><td style="text-align:right; padding:6px 20px;">26.75</td><td style="text-align:right; padding:6px 20px;">1.146</td><td style="text-align:right; padding:6px 20px;">1.00</td></tr>
  </tbody>
</table>
</div>

The justification for neural approximation stops there, however — it does not extend to replacing the oracle scorer with a neural one. Swapping the oracle for a neural scorer at the scoring stage yields another 6× speedup, but MAP@100 drops by 0.35–0.50:

**Table 5.** LSH+Oracle vs. LSH+Neural scoring on PTC datasets (100K corpus, 100 test queries, candidate subset ≤ 2500). The oracle already operates under one second per query on the filtered set; the quality cost of neural scoring is not worth the marginal speedup.

<div style="overflow-x:auto; margin: 1.5em 0;">
<table style="border-collapse:collapse; font-size:0.9em;">
  <thead>
    <tr style="border-bottom:2px solid #ccc;">
      <th style="text-align:left; padding:8px 20px;">Dataset</th>
      <th style="text-align:right; padding:8px 20px;">LSH+Oracle time / q (s)</th>
      <th style="text-align:right; padding:8px 20px;">LSH+Oracle MAP@100</th>
      <th style="text-align:right; padding:8px 20px;">LSH+Neural time / q (s)</th>
      <th style="text-align:right; padding:8px 20px;">LSH+Neural MAP@100</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding:6px 20px;">PTC-FR</td><td style="text-align:right; padding:6px 20px;">0.915</td><td style="text-align:right; padding:6px 20px;">1.00</td><td style="text-align:right; padding:6px 20px;">0.149</td><td style="text-align:right; padding:6px 20px;">0.62</td></tr>
    <tr><td style="padding:6px 20px;">PTC-FM</td><td style="text-align:right; padding:6px 20px;">1.153</td><td style="text-align:right; padding:6px 20px;">0.98</td><td style="text-align:right; padding:6px 20px;">0.152</td><td style="text-align:right; padding:6px 20px;">0.50</td></tr>
    <tr><td style="padding:6px 20px;">PTC-MR</td><td style="text-align:right; padding:6px 20px;">1.146</td><td style="text-align:right; padding:6px 20px;">1.00</td><td style="text-align:right; padding:6px 20px;">0.174</td><td style="text-align:right; padding:6px 20px;">0.63</td></tr>
  </tbody>
</table>
</div>

The neural index is justified; the neural scorer is not. Such scrutiny should be applied more often before developing neural surrogates for hard problems.

**Neural augmentation inside solvers.** Using a neural policy to guide branching in branch-and-bound, or to warm-start local search, is more defensible than outright solver replacement. The solver retains optimality certification; the neural component influences the search trajectory. The costs from our framework still apply — supervision is expensive, policies trained on one problem family may not transfer — but the failure mode is controllable in a way that end-to-end replacement is not.

---

## A checklist

Before building or crediting a neural combinatorial method, we propose five questions:

1. Is there a discrete layer posing a gradient bottleneck in a larger learning pipeline?
2. Do system-level serving constraints impose the need for neural embeddings?
3. Could the combinatorial solver itself be augmented with neural capabilities, rather than replaced?
4. If replacement is attempted: are all costs (label generation, training, retraining under shift) explicitly accounted for? Are any guarantees provided? [[see paper](https://openreview.net/pdf?id=kTNN55uS0W)]
5. Have the combinatorial decoder (if present) and simple structural heuristics been tested as baselines?

If the answer to (1) and (2) is no, and (3) has not been considered, the bar for (4) and (5) should be very high. In practice, it rarely is.

---

## Contact

If you have any questions, feel free to reach out to <a href="mailto:pritish@cse.iitb.ac.in">Pritish</a>.
