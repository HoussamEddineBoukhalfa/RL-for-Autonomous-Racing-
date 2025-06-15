# 🚗 Reinforcement Learning for Autonomous Racing  
**ENSIA – Project 12 | Reinforcement Learning Project 2025 Submission**  
**Team Lead:** Houssam-Eddine Boukhalfa (houssam-eddine.boukhalfa@ensia.edu.dz)

This repository presents our solution for the **Reinforcement Learning for Autonomous Racing** project. We implemented a self-driving car simulation trained using a **Deep Q-Learning (DQN)** algorithm, built in **Python** using **Pygame** for the environment and **PyTorch** for the deep learning component.

---

## 🧠 Project Summary

The agent is trained to autonomously drive a car on a custom track using sensor inputs and a reward-based learning system. By simulating multiple cars from random starting configurations, we improved the agent’s generalization and robustness. The environment supports both training and testing modes, allowing us to analyze and visualize policy performance.

---

## 🏎️ Autonomous Car Logic

The `AutonomousCar` class manages the simulation of the car’s physics and perception:

- **State Update (`update`)**: Handles movement, rotation, speed changes, and physics like friction.
- **Collision Detection (`check_collision`)**: Detects collisions using bounding box logic against track borders.
- **Sensors and Perception (`perceive`, `get_state`)**: Returns distance-based sensor data for RL input.
- **Checkpoint Logic (`checkpoint`)**: Tracks progression through laps and rewards forward movement.
- **Rendering (`draw`)**: Visualizes the car and its sensors during training or testing.

The class also supports randomized or fixed initial positions based on the training/testing context.

---

## 🌍 Environment Setup

The `Environment` module contains:

- **SimulationEnvironment**: For multi-car parallel training (improves exploration and robustness).
- **RacingEnvironment**: For single-car simulation with a learned policy (evaluation phase).

Key methods include:

- **`step(action)`**: Applies actions, returns next state, reward, and done flag.
- **`draw()`**: Renders barriers, checkpoints, and cars on the Pygame window.

---

## 🧪 Training Process

The training loop (in `main.py`) runs for a fixed number of episodes (adjustable via `settings.py`). It uses:

- **Experience Replay** for efficient memory usage and stability.
- **Episodic Training** with randomized initial conditions.
- **Multiple Cars** per episode for better policy generalization.

We observed that training with only one car led to poor generalization. Allowing multiple agents to explore the track simultaneously from varied positions enabled the DQN to learn more transferable behaviors.

---

## 🎮 Testing and Evaluation

The `main_test.py` file evaluates the learned policy. The agent runs on the track with fixed starting points, and we track lap completions and collision events. The configuration can be adjusted in `settings.py`.

---

## ✅ Results

- ✅ Robust navigation across diverse starting points.
- ✅ Checkpoint progression and collision avoidance behavior successfully learned.
- 🚧 Minor failure cases in tight curves from stationary start.
- 🚀 Future improvement: Introduce **reward shaping** for **lap time minimization** to encourage more efficient driving lines.

---

## 📹 Demonstration

<p align="center">
    <img src="https://github.com/user-attachments/assets/9812c99b-a132-42f7-8aca-ce9360e018c9" alt="RL_Car Testing" width="500"><br>
  <i>Training simulation with multiple cars</i>
</p>

<p align="center">

  <img src="https://github.com/user-attachments/assets/a507e87f-fc9a-4f89-9cdd-5b76bad8ec1a" alt="RL_Car Training" width="500"><br>
  <i>Learned policy in action</i>
</p>

---

## 📁 Repository Structure

├── AutonomousCar.py # Car simulation class
├── Environment.py # Training/testing environment
├── DQN.py # Deep Q-learning logic
├── main.py # Training script
├── main_test.py # Testing script
├── settings.py # Parameters & configuration
├── assets/ # Track images, car sprites
└── README.md # This file
---

## 👨‍🎓 Academic Context

This project was completed as part of the ENSIA capstone module on reinforcement learning. The implementation aligns with the goal of applying RL to a **realistic autonomous driving scenario**, leveraging classical DQN techniques with modern improvements like experience replay and policy testing under stochastic initial conditions.
