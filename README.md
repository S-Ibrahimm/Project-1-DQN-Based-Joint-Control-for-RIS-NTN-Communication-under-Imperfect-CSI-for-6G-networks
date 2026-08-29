# DQN-Based-Joint-Control-for-RIS-NTN-Communication-under-Imperfect-CSI-for-6G-networks

This repository contains the implementation of a Deep Q-Network (DQN) agent designed for real-time resource allocation and signal phase management in 6G Non-Terrestrial Networks (NTNs) assisted by Reconfigurable Intelligent Surfaces (RIS).

Developed as part of a capstone research project at the IPT lab.

📌 Problem Overview
In next-generation 6G wireless architectures, drone-assisted Non-Terrestrial Networks extend connectivity to remote regions and disaster zones. However, dynamic line-of-sight blockages and mobility introduce severe signal fading.

While Reconfigurable Intelligent Surfaces (RIS) act as controllable electromagnetic mirrors to route signals around physical obstacles, jointly optimizing dynamic transmission power, modulation schemes, and RIS reflection phase shifts in real time presents a highly complex combinatorial problem.

Standard optimization methods (e.g., brute-force or mathematical programming) scale poorly in dynamic environments. This project models the dynamic state space as a Markov Decision Process (MDP) and deploys a Deep Q-Learning framework to achieve optimal decision-making at near-instantaneous execution speeds.

⚙️ Key Features
Custom Gymnasium Environment: Simulates a 3D drone-to-ground communication channel under dynamic line-of-sight (LoS) and non-line-of-sight (NLoS) fading conditions.

Deep Q-Network (DQN) Architecture: Leverages PyTorch to model joint state representations and output discrete control actions for transmission power, modulation selection, and RIS element activation.

Baseline Benchmarking: Includes performance comparisons against:

Brute-Force Search: Exhaustive search across the full action space to establish theoretical upper bounds.

🛠️ Tech Stack & Dependencies
Language: Python 3.8+

Deep Learning Framework: PyTorch

RL Framework: Gymnasium / OpenAI Gym

Data Processing & Visualization: NumPy, Matplotlib, Pandas

Rule-Based Heuristics: Static thresholding algorithms mimicking traditional network controllers.

Low-Latency Inference: Demonstrates near-optimal decision quality while execution time is reduced by orders of magnitude compared to numerical optimization.
