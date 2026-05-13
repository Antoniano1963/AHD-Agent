
# 

<div align="center">


<h1 style="display: flex; justify-content: center; align-items: center; gap: 10px; margin: 0;">
  AHD Agent: Agentic Reinforcement Learning for Automatic Heuristic Design
</h1><p><em>Haoze Lv*, Ning Lu*, Ziang Zhou, Shengcai Liu📧</em></p>

<p align="center">
  <div align="center">
  <a href="figure/framework.png">
    <img src="figure/framework.png" width="85%" alt="Traditional LLM-based AHD vs. AHD Agent">
  </a>
  </div>

[![Paper](https://img.shields.io/badge/paper-A42C25?style=for-the-badge&logo=arxiv&logoColor=white)](https://arxiv.org/pdf/2605.08756) 
[![alphaXiv](https://img.shields.io/badge/discussion-A42C25?style=for-the-badge&logo=arxiv&logoColor=white&color=blue
)](https://www.alphaxiv.org/abs/2605.08756)
[![Github](https://img.shields.io/badge/AHD%20AGENT-000000?style=for-the-badge&logo=github&logoColor=000&logoColor=white)](https://github.com/Antoniano1963/AHD-Agent)

</div>
</p>


<p align="center">
  <strong>A tool-integrated, multi-turn LLM agent trained with reinforcement learning for automatic heuristic design.</strong>
</p>

------

## Highlights

- **Tool-using AHD agent:** Proactively uses tools in multi-turn heuristic generation.
- **Agentic RL training:** Learns from synthesized AHD environments with multi-domain training.
- **Efficient and generalizable:** A 4B agent outperforms larger-model baselines across various domains.

---

## Agent Loop


AHD Agent keeps an interaction history and makes state-dependent decisions over multiple turns. The agent can:

1. generate or revise a heuristic,
2. evaluate the candidate heuristic on a design set,
3. call tools to collect targeted feedback,
4. continue the design process or return the final heuristic.

<p align="center">
  <a href="figure/workflow.png">
    <img src="figure/workflow.png" width="90%" alt="AHD Agent workflow">
  </a>
</p>

<p align="center">
  <em>AHD Agent workflow: the model iteratively uses feedback, tools, and evaluations to improve heuristics.</em>
</p>




## Results

We evaluate AHD Agent across eight settings spanning constructive heuristics, ant-colony-optimization heuristics, held-out combinatorial domains, and cost-aware Bayesian optimization.

### Efficient Design-Time Convergence

On RL training domains, the agent reaches competitive or superior gaps with only about **11-15 evaluator calls** in the short setting. The design-time convergence curves show that AHD Agent improves quickly under limited evaluation budgets and continues to benefit when the budget is expanded.

<p align="center">
  <a href="figure/training_curves.png">
    <img src="figure/training_curves.png" width="70%" alt="Training curves during design">
  </a>
</p>

<p align="center">
  <em>AHD Agent converges faster and achieves better performance under larger evaluation budgets.</em>
</p>

### Potential from Stronger Backbones

AHD Agent has strong potential to improve with stronger LLM backbones. Model scaling produces more consistent gains for the agentic multi-turn paradigm than for fixed-workflow AHD methods, suggesting that stronger reasoning ability is better converted into heuristic-design performance when the model controls the design process.

<p align="center">
  <a href="figure/model_scaling.png">
    <img src="figure/model_scaling.png" width="70%" alt="Model scaling">
  </a>
</p>

<p align="center">
  <em>Performance improves as the backbone model becomes stronger.</em>
</p>

### Cross-Domain Generalization

The RL-trained agent generalizes beyond the domains used during training. As the number of RL training domains increases, performance improves not only on in-domain tasks but also on held-out domains, indicating that cross-domain RL training learns transferable heuristic-design behavior.

<p align="center">
  <a href="figure/cross_domain_training.png">
    <img src="figure/cross_domain_training.png" width="60%" alt="Cross-domain RL training">
  </a>
</p>

<p align="center">
  <em>Held-out performance improves as the training mixture covers more domains.</em>
</p>

### Inference-Time Scaling

AHD Agent can also be enhanced at inference time by increasing the evaluator budget. Continuing one coherent multi-turn trajectory can be more effective than aggregating independent short trajectories, because later revisions can exploit accumulated feedback from earlier turns.

<p align="center">
  <a href="figure/inference_time_scaling.png">
    <img src="figure/inference_time_scaling.png" width="70%" alt="Inference-time scaling">
  </a>
</p>

<p align="center">
  <em>Sequential refinement benefits from accumulated feedback under larger evaluation budgets.</em>
</p>



## Contact

For questions about the paper, please contact Shengcai Liu at <liusc3@sustech.edu.cn>.
