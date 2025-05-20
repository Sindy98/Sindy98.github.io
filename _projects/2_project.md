---
layout: page
title: Conditional Predictive Reinforcement Learning for Driving Policy
description:
img: assets/img/cpc_title.png
importance: 2
category: work
---

In this project, I developed a deep reinforcement learning (RL) framework for conditional driving policy learning in the CARLA simulator. The system takes visual inputs and high-level navigational commands to determine driving actions, making it highly applicable to real-world autonomous driving scenarios.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/cpc_network.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Overview of the Conditional Predictive Control (CPC) Network Architecture. The network receives RGB visual input and high-level navigational commands. On the top, the command selects an Actor-Critic branch to sample driving actions. On the bottom, the prediction module forecasts future semantic segmentation, speed, and collision events. 
</div>

To enhance policy learning, I designed a Conditional Predictive Control (CPC) framework based on an Actor-Critic architecture. The CPC framework integrates reward shaping and leverages auxiliary prediction tasks—including semantic segmentation, speed estimation, and collision forecasting—to improve feature representation from visual observations.

My implementation achieved:

- 90% accuracy in predicting traffic-related events using visual features,

- An 85% route completion rate on the NoCrash benchmark, and

- Competitive performance compared to methods relying on expert demonstrations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/cpc_demo.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Driving example in a test crowded town.
</div>

This work demonstrates the potential of deep RL with auxiliary tasks in improving autonomous driving systems under complex, real-world situations. 

Through this project, I discovered that long-tail data distribution significantly affects the action prediction module. For instance, in the (speed, traffic light, action) space, the state where speed = 0, traffic light = green, and action = acceleration is extremely rare. In contrast, more common scenarios like high speed with green light and no action change dominate the dataset. As a result, the network fails to learn appropriate responses for underrepresented transitions—such as accelerating from a full stop at a green light—leading to behaviors like the car indefinitely waiting at an intersection.

To mitigate this issue, we introduced action turbulence and applied data augmentation to better illustrate these rare transitions. However, these strategies only partially alleviated the problem. The network still struggles with causal reasoning in such edge cases. I believe that a more balanced and well-curated dataset could significantly improve the model’s generalization and responsiveness in these critical but rare scenarios.