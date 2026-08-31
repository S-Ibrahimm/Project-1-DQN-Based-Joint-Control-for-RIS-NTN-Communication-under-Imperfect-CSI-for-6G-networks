# DQN-Based Joint Control for RIS-NTN Communication under Imperfect CSI for 6G Networks

This repository contains the implementation of a Deep Q-Network (DQN) agent designed for real-time resource allocation and signal phase management in 6G Non-Terrestrial Networks (NTNs) assisted by Reconfigurable Intelligent Surfaces (RIS).

Developed as part of a capstone research project at the IPT lab.

## 📌 Problem Overview

In next-generation 6G wireless architectures, drone-assisted Non-Terrestrial Networks extend connectivity to remote regions and disaster zones. However, dynamic line-of-sight blockages and mobility introduce severe signal fading.

While Reconfigurable Intelligent Surfaces (RIS) act as controllable electromagnetic mirrors to route signals around physical obstacles, jointly optimizing dynamic transmission power, modulation schemes, and RIS reflection phase shifts in real time presents a highly complex combinatorial problem.

Standard optimization methods (e.g., brute-force or mathematical programming) scale poorly in dynamic environments. This project models the dynamic state space as a Markov Decision Process (MDP) and deploys a Deep Q-Learning framework to achieve optimal decision-making at near-instantaneous execution speeds.

## ⚙️ Key Features

- **Custom Gymnasium Environment**: Simulates a 3D drone-to-ground communication channel under dynamic line-of-sight (LoS) fading conditions, with a ground-deployed RIS providing a secondary reflected path.
- **Deep Q-Network (DQN) Architecture**: Leverages PyTorch to model joint state representations and output discrete control actions for transmission power, modulation selection, and RIS sub-array activation.
- **Baseline Benchmarking**: Includes performance comparisons against:
  - **Brute-Force Search**: Exhaustive search across the full action space to establish theoretical upper bounds.
  - **Rule-Based Heuristics**: Static thresholding algorithms mimicking traditional network controllers.
  - **Random Policy**: Lower-bound sanity check.
- **Low-Latency Inference**: Demonstrates near-optimal decision quality while execution time is reduced by roughly one to two orders of magnitude compared to exhaustive numerical optimization.

## 🔍 Key Finding: When RIS Actually Helps

Beyond training the agent, this project includes a quantitative check on whether the RIS was contributing meaningful signal gain — not just whether it was selected. The result: in this scenario's geometry (kilometre-scale distances, strong line-of-sight, RIS positioned far from both drone and user), the RIS-reflected path was consistently **16–60 dB weaker** than the direct link, a known effect in the RIS literature called **double path loss**— a two-hop reflected path pays the path-loss penalty twice, which the RIS's array gain can't fully offset at long range.

This means the RIS's occasional selection by the brute-force baseline reflected the reward function imposing no cost on activating it, not a physically meaningful contribution — and the DQN agent's near-minimal RIS usage was, if anything, the more physically sensible policy of the two. This finding directly motivated a follow-up project modeling RIS-assisted sensing under a *blocked* line-of-sight, where the RIS becomes physically necessary rather than optional — consistent with how RIS is expected to matter in the literature (blocked-LoS rescue, not already-strong-LoS links).

## 🛠️ Tech Stack & Dependencies

- **Language**: Python 3.8+
- **Deep Learning Framework**: PyTorch
- **RL Framework**: Gymnasium / OpenAI Gym
- **Data Processing & Visualization**: NumPy, Matplotlib, Pandas
