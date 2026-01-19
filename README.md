# UTR-DynaPro
PyTorch code for UTR-DynaPro: A CNN–Transformer Multimodal Language Model for Decoding 5′UTR Regulatory Mechanisms

UTR-DynaPro is a multimodal deep learning framework designed to predict translation dynamics. It integrates genomic sequence information with biophysical features (e.g., MFE, uORFs) using a parallel CNN-Transformer architecture.

🛠 Key Architectural Features

Feature Fusion Module: The model utilizes non-autoregressive parallel branches (CNN & Transformer) for feature refinement and multi-scale integration. (Renamed from "Decoder" to better reflect its functional role).

K-mer Specific MoE: Incorporates a Mixture of Experts layer to capture regulatory motifs at varied k-mer scales (k=3, 5, 7, 9).

Frame-Aware Pooling: Captures frame-specific regulatory signals to enhance MRL prediction accuracy.

Multimodal Integration: Fuses raw sequence embeddings with biophysical properties and experimental indicators.


🚀 Training and Implementation Details

Hardware: All models were trained on a single NVIDIA GeForce RTX 4090 GPU (24 GB).

Optimization Setup:Framework: PyTorch

Optimizer: SGD (Momentum: 0.9, Weight Decay: 1 *10^{-4})

Loss Function: Huber Loss

Learning Rate: Initialized at 1* 10^{-4}


Model Configuration:

Refinement Block (formerly Decoder): Consists of 3 stacked Parallel Convolution–Transformer Layers.

Multi-head Attention: 16 heads per Transformer branch.

Convolution Branch: 1D convolution with kernel size k=7 and symmetric padding.

Robustness: Each experiment was conducted 6 times to ensure statistically significant average results.


📂 Data Availability
The datasets used in this study are publicly available across the following repositories:

TE and EL Tasks: The datasets for Translation Efficiency (TE) and Expression Level (EL) tasks, including training data for the pre-trained model, are accessible at https://codeocean.com/capsule/6711822.

MRL Task (Endogenous Dataset): The Mean Ribosome Load (MRL) task data, including our multi-species 5′UTR database, have been deposited in the OMIX database (accession number: OMIX008723). This database is part of the Genome Sequence Archive (GSA) at the China National Center for Bioinformation at https://ngdc.cncb.ac.cn/omix.


🛡️ Data Integrity & Anti-Leakage Measures
To ensure rigorous evaluation and prevent data leakage due to sequence homology:

Cross-Species Deduplication: A stringent deduplication pipeline was applied across all seven species (Human, Chimp, Bonobo, etc.). Any identical 5′UTR sequences shared between species were collapsed into a single unique entry.

Synthetic Control: The model's generalization was independently validated using the Random_Vary dataset, consisting of entirely synthetic sequences with zero evolutionary ancestry.
