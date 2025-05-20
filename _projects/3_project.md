---
layout: page
title: Safe Reinforcement Learning for Multi-player Drone Racing
description:
img: assets\img\SRL_title.png
---

Drone racing has emerged as a high-stakes, internationally competitive sport. While reinforcement learning (RL) has successfully achieved time-optimal policies for single-agent racing, training autonomous RL strategies for multi-agent drone racing remains a significant challenge.

To address this, we introduce an RL-based approach that trains competitive and safety-conscious policies for multi-agent racing. Our method leverages curriculum learning with adaptive reward-coefficient adjustment, achieving superior convergence with enhanced competitiveness and a reduced crash rate. Notably, we:

- Generate diverse, competitive opponents through adversarial attacks and league play, improving robustness;

- Boost sampling efficiency by integrating suboptimal racing strategies, accelerating training;

- Mitigate data imbalance via task division and training separation, ensuring balanced learning;

- Increase survival rates from 45% to 70% versus baselines while maintaining high-speed performance.

We evaluate our method in a 3-player self-play scenario on a SplitS track, where it reduces crash rates by 47% (from 0.95 to 0.5) while maintaining high-speed performance (5.3s/lap)—significantly outperforming standard RL baselines in both safety and competitiveness. Furthermore, as below, the learned value distribution reveals an intelligent spatial awareness: it assigns lower values to states with nearby opponents, effectively capturing the underlying strategic dynamics of multi-agent racing.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets\img\SRL_visualization.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Value distribution of spatial awareness toward opponents
</div>

In our comparative study of SAC and PPO for drone racing applications, we observed distinct trade-offs between the two algorithms. PPO demonstrated greater robustness to reward shaping when the primary reward component was simple or clearly defined. However, its relies on more concentrated state-action sampling, limiting its ability to master sophisticated behaviors without an excessively large data buffer.

In contrast, while SAC exhibited slower convergence and higher sensitivity to hyperparameters, it proved more effective at discovering moderately safe, conservative policies. This suggests SAC’s superior suitability for scenarios requiring nuanced policy optimization, despite its steeper tuning requirements.





