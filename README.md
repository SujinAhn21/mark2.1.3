# mark2.1.3 - Audio Classification based on ViLD-inspired Architecture

# Overview
▪ The mark2.1.3 project is a ViLD-inspired audio classification model developed to distinguish impact (thumping) noise from other environmental sounds, particularly for applications such as inter-floor noise monitoring. The model leverages a two-stage architecture (teacher-student) where the teacher uses embedding similarity, and the student is trained via supervised learning.

▪ Initially, the model was built with a semi-supervised approach using soft labels derived from cosine similarity between audio and text embeddings. However, the architecture evolved toward a hard label-based supervised model due to issues with soft label ambiguity.

# Model Architecture
▪ Teacher Model
- Audio Encoder: Simple CNN-based Mel spectrogram encoder
- Text Encoder: SentenceTransformer (e.g., all-MiniLM)
- Labeling: Cosine similarity -> soft label (or top-1 -> hard label)

▪ Student Model
- Input: Mel spectrogram
- Label: Hard label only
- Loss Function: CrossEntropyLoss
- Output: Softmax for binary classification (positive vs. negative)

# Learning Strategy Evolution
▪ Initial
- Method: Soft Label (Semi-supervised)
- Summary: Used cosine similarities between audio-text embeddings. Generalized well but suffered from label ambiguity and weak convergence.  

▪ Refactored
- Method: Hard Label (Supervised)
- Summary: Converted top-1 similarity into hard labels. Improved accuracy, loss convergence, and reduced overfitting.

# Results
▪ After switching to hard label training:
- Faster and more stable loss convergence
- Improved classification metrics: precision, recall, f1-score
- Proper early stopping and reduced overfitting

# Future Work
- Introduce pseudo-labeling or consistency training to leverage unlabeled data
- Extend classification beyond binary to multi-class (e.g., mark2.1~2.4 combined)
- Explore pretrained audio encoders (e.g., AudioCLIP, AST) for better representations  

# License
- This project is licensed under the PolyForm Noncommercial License 1.0.0.  
- Commercial use is not permitted.
- See the [LICENSE](./LICENSE) file for details.

# Acknowledgements
- This work is inspired by the ViLD paper (Zero-shot Visual Search via Vision-Language Distillation), and reimagines the core concepts for audio classification. 
- All implementations are original and developed by Sujin Ahn.

