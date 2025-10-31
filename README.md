# UF-Boolean-Network-Research-Overview
This repository is an overview of my research on Boolean networks (BNs), conducted alongside fellow high school researcher Matthew Jones and our mentors, Dr. Matthew Wheeler and Dr. Sai Bavisetty from the University of Florida. My actual repository is private.

### Project Overview

Imagine a network of interconnected light switches, where the state of each switch (on or off) depends on the state of the switches connected to it. A Boolean network is a mathematical model of such a system. BNs are used to model complex systems in biology, like gene regulatory networks, where the "switches" are genes turning each other on and off.

The long-term behavior of these networks always settles into a repeating pattern, called an **attractor** (which can be a steady state, called a **fixed point**, or a repeating cycle). The central question of our research is:

**How does the "wiring diagram" (the network's structure) determine the number and lengths of these attractors?**

Our goal is to move beyond computer simulations and develop formal mathematical proofs to predict the behavior of these complex systems.

### Our Methodology

We use a two-pronged approach:
1.  **Computational Simulation-** We write Python scripts (using libraries like `NetworkX`) to build and simulate thousands of random Boolean networks on specific wiring diagrams. This allows us to gather statistical data and uncover surprising patterns
2.  **Analytical Proof -** We use techniques from abstract algebra, combinatorics, and number theory to formally prove the patterns we observe. Our proofs are written in LaTeX and prepared in a collaborative Overleaf document

---
### Key Findings & Discoveries

We've successfully characterized the attractor landscapes for several fundamental classes of network topologies.

#### 1. Directed Acyclic Graphs (DAGs)
For networks without feedback loops, we proved that the attractor landscape is always one of two simple cases:
*   The network has **$2^k$ fixed points** and no cycles
*   The network has **0 fixed points** and **$2^{k-1}$ cycles**, all of which are 2-cycles

#### 2. Simple N-Node Cycles (A Single Feedback Loop)
For networks consisting of a single ring, the behavior is determined by the parity of negations ("NOT" gates) in the update rules.
*   **Even Negations -** we proved that this case is dynamically equivalent to a simple rotation. The number and lengths of all attractors are given by a classic combinatorial formula for counting necklaces (Moreau's necklace-counting function).
*   **Odd Negations -** This case is more complex and has no fixed points. We proved that the formula for its attractors is equivalent to counting "antipalindromic" necklaces, a result we derived from first principles and connected to established combinatorial theory

#### 3. Maximal Length Cycles in Complex Networks
Our most exciting discovery came from exploring more complex topologies, such as an N-cycle with a "chord" (an extra connection that creates interacting feedback loops).

While simulating a 7-node cycle with a `1->3` chord, we found that **approximately one-third of all randomly generated networks produced a massive limit cycle of length 127.**

A 7-node network has only $2^7 = 128$ possible states. A 127-cycle is a *maximal length cycle* that visits every single state except for one, which exists as a single fixed point.

**The mechanism -** We proved that this highly structured behavior emerges when the network's non-linear rules can be decomposed into a special mathematical form known as an **affine transformation (`Ax + b`)**. We showed that the maximal length cycle is guaranteed to occur if the characteristic polynomial of the linear part (`A`) is a **primitive polynomial** over the finite field $\mathbb{F}_2$. We successfully identified the primitive polynomial `x⁷ + x + 1` as the algebraic "signature" for this phenomenon in our simulations.

---

### My Role and Contributions

As a high school researcher on this team since September 2024, I've been deeply involved in all aspects of the project. My specific contributions include:
*   **Developing and running computational experiments** using Python to analyze thousands of network configurations
*   **Analyzing experimental data** to identify patterns, formulate hypotheses, and validate our theoretical findings
*   **Co-authoring the formal mathematical proofs** for our key results in a collaborative LaTeX document, including the rigorous proofs for the combinatorial identity at the heart of the simple N-cycle problem.
*   **Leading the investigation into the 127-cycle discovery**, from capturing the specific rules that caused it to proving the underlying algebraic mechanism involving affine transformations and primitive polynomials


My actual repository (private) contains the core code and analysis for our research.
*   `run_attractor_experiment.py`: The main Python script used to run simulations on fixed network topologies
*   `bn_utils.py` & `attractor_analysis.py`: Utility scripts containing the core functions for generating networks and finding attractors
*   `BN_Experiment_Analysis.ipynb`: A Jupyter Notebook containing the data, visualizations, and formal proofs for our key findings, including the complete proof for the maximal length cycle mechanism

Thank you for your interest in my research.

Sincerely,
**Julian Vignes**
