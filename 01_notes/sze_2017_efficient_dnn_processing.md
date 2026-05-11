---
title: "Efficient Processing of Deep Neural Networks: A Tutorial and Survey"
authors:
  - Sze, Vivienne
  - Chen, Yu-Hsin
  - Yang, Tien-Ju
  - Emer, Joel
year: 2017
source: sze_2017_efficient_dnn_processing
tags:
  - deep-learning
  - machine-learning
status: read
---

# Sze et al. 2017 — Efficient Processing of Deep Neural Networks: A Tutorial and Survey

## Title and Authors
**Efficient Processing of Deep Neural Networks: A Tutorial and Survey**
Vivienne Sze, Yu-Hsin Chen, Tien-Ju Yang, Joel Emer — *arXiv/IEEE Proceedings of the IEEE*, 2017

## Quick Overview
- **Why is it relevant?** Foundational tutorial on DNN computation efficiency, covering all aspects of how neural networks consume compute and memory, relevant for understanding the practical deployment challenges of large time series models in RS.
- **What was done?** Comprehensive tutorial on DNN architectures, hardware platforms, and techniques to reduce computational complexity of DNNs without sacrificing accuracy — covering compression, pruning, quantisation, and hardware co-design.
- **What is the main outcome?** A taxonomy of efficiency techniques (from pure hardware to joint algorithm-hardware co-design) with evaluation metrics framework; identifies energy efficiency and throughput as primary constraints for DNN deployment.

## Main Goal and Fundamental Concept
Deep neural networks achieve state-of-the-art accuracy across AI tasks but at high computational cost in memory, energy, and time. This tutorial explains how DNNs work computationally, what makes them expensive, and how to make them run efficiently on diverse hardware — from cloud GPUs to edge devices — without sacrificing accuracy.

## Technical Approach
Tutorial structure:
- **DNN background:** History, applications, key architectural components (convolutions, pooling, FC layers, activations)
- **Hardware platforms:** CPUs, GPUs, FPGAs, ASICs, near-data processing with novel memory technologies
- **Pure hardware optimisations:** Data reuse strategies, dataflow designs (weight stationary, output stationary, etc.)
- **Joint algorithm-hardware:** Network pruning, weight sharing, quantisation (fixed-point), knowledge distillation, efficient architectures (SqueezeNet, MobileNet)
- **Evaluation metrics:** FLOPS, memory footprint, energy per inference, throughput, latency

## Distinctive Features
- Written by MIT hardware researchers, giving an unusual hardware-centric perspective on DNN efficiency
- Provides formal treatment of dataflow in DNN accelerators — important for understanding GPU/TPU behaviour
- Covers both inference and training efficiency
- Introduces benchmarking framework for comparing DNN designs

## Key Concepts
- **Compute bottleneck:** Convolutions dominate FLOPs; matrix multiplications dominate FC layers
- **Memory bandwidth bottleneck:** Data movement (DRAM reads) often dominates energy, not computation
- **Compression hierarchy:** Pruning > weight sharing > quantisation > knowledge distillation in terms of impact
- **Dataflow choice:** How data is scheduled through compute units critically affects throughput and energy
- **Hardware co-design:** Algorithm and hardware must be co-optimised for maximum efficiency gains

## Advantages and Limitations
- **Advantages:** Comprehensive; well-structured tutorial format; bridges algorithm and hardware; widely cited foundation
- **Limitations:** Primarily focused on CNN/FC architectures; transformer efficiency not covered (pre-dates transformer dominance); hardware landscape has evolved significantly post-2017

## Conclusion
Efficient DNN processing requires understanding both algorithmic structure (sparsity, redundancy, approximability) and hardware constraints (memory hierarchy, bandwidth, parallelism). The key insight is that energy and memory bandwidth are the primary practical constraints, not raw FLOP count. This tutorial provides the conceptual foundation for understanding why model compression and efficient architectures matter for deploying DL models in practical RS workflows.

## Related pages
- [[neural_network_training]]
- [[transfer_learning_remote_sensing]]
