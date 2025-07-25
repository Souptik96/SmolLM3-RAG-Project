# 🤖 SmolLM3-RAG: A High-Performance, Low-Cost Hybrid-RAG System
An end-to-end Retrieval-Augmented Generation (RAG) project with hybrid search capabilities, demonstrating how a fine-tuned small language model (SLM) can achieve near state-of-the-art performance with significantly lower computational requirements through intelligent retrieval fusion.

## 🎯 Overview & Motivation
The goal of this project is to bridge the gap between large proprietary models and practical applications by combining:

* Hybrid Retrieval: BM25 + Vector search fusion

* 4-bit Quantization: Efficient inference

* Streaming Generation: Real-time responses

While models like GPT-4 are powerful, their API costs and latency can be prohibitive. This system demonstrates that a carefully engineered hybrid-RAG approach with a smaller open-source model can deliver superior quality at 1/10th the cost, providing a blueprint for building efficient, production-ready AI assistants that are both intelligent and economical.

## 🎬 Live Demo
Hybrid search in action - notice how it handles both keyword-heavy and semantic queries effectively.

----- Link/Gif to be pasted -----

## ✨ Key Features
### 🔍 Hybrid Search Engine
* Dual Retrieval: Combines BM25's precision with vector search's recall

* Dynamic Weighting: Auto-adjusts 
alpha (0.3-0.7) based on query type

* Cache Layer: 1-hour TTL for frequent queries (30% latency reduction)

### 🧠 Generation Pipeline
* 4-bit Quantization: 1.5GB memory footprint (vs 6GB FP16)

* Token Streaming: First token in <800ms on T4 GPU

* Structured Output: Markdown with verified sources

### ⚙️ Operational Efficiency
* Modular Design: Swappable components (try different embedders)

* Self-healing: Falls back to vector-only when BM25 fails

* Query Analysis: Automatic spell correction + term boosting

## 🏗️ Architecture & Training Details
The system follows a classic RAG pipeline, optimized for speed and efficiency.

<img width="3722" height="2454" alt="deepseek_mermaid_20250725_96f448" src="https://github.com/user-attachments/assets/4a37e3ed-bd4a-4d80-8ee7-00459ad95a0a" />

### Component Deep Dive
1. Hybrid Retrieval Layer

  * BM25 with NLTK tokenization

  * FAISS IVFFlat (384-dim embeddings)

  * Score fusion: combined = 0.5*BM25 + 0.5*Vector

2. Optimization Tricks

  * Query classification (keyword vs semantic)

  * Dynamic 
    alpha adjustment:

    alpha = 0.7 if query_length < 5 else 0.3

  * Cold start mitigation

  3. Fine-Tuning

  * Dataset: 12k QA pairs with hybrid-retrieved contexts

  * LoRA adapters: r=32, alpha=64

  * Special tokens: <|hybrid_result|> markers

## 🏆 Benchmark Results
The fine-tuned SmolLM3-RAG model shows remarkable performance on commonsense reasoning and knowledge-based QA tasks, approaching the accuracy of the much larger LLaMA-2 7B model while being significantly more efficient.

<img width="674" height="402" alt="Screenshot (5)" src="https://github.com/user-attachments/assets/f7585d09-d21e-49e6-955c-57b16a9e740b" />

<img width="701" height="228" alt="image" src="https://github.com/user-attachments/assets/e2bbd3a8-7e85-4481-bb10-c88ac25cb0b2" />

<img width="695" height="199" alt="image" src="https://github.com/user-attachments/assets/90e37845-b64c-4bec-9e59-53228c745d32" />

The fine-tuned SmolLM3-RAG model shows remarkable performance on commonsense reasoning and knowledge-based QA tasks, approaching the accuracy of the much larger LLaMA-2 7B model while being significantly more efficient.

## 🚀 Speed, Latency & Deployment
Performance is not just about accuracy. This project prioritizes a responsive user experience.

<img width="718" height="227" alt="image" src="https://github.com/user-attachments/assets/25f14883-74de-4dbf-aedd-47c429bf5e2d" />

### General Performance
* Tokens/Second: Achieves an average of ~35 tokens/second on a single NVIDIA T4 GPU.

* Quantization: NF4 quantization reduces the model size from ~6GB in FP16 to ~1.5GB in 4-bit.

* Streaming: Uses TextIteratorStreamer to begin showing the response to the user in under a second

## ▶️ How to Run
1. Clone the repository:

git clone https://github.com/your-username/SmolLM3-RAG-Project.git
cd SmolLM3-RAG-Project

2. Set up the environment:
This project was developed in a Kaggle environment. To replicate, follow the dependency installation steps in the run_notebook.ipynb.

# It is recommended to use the provided notebook to install exact versions
pip install -r requirements.txt 

3. Set up your Hugging Face Token:
You will need a Hugging Face token with access to the model. Store it as a secret accessible by the environment.

4. Run the application:

python app.py

The Gradio interface will be available at http://0.0.0.0:7860.

📂 Project Structure

<img width="544" height="373" alt="image" src="https://github.com/user-attachments/assets/665e1710-66cc-43fa-a779-1b25abd19459" />

## 📬 Get Involved / Contact
I am actively seeking feedback and collaboration opportunities. If you have any questions, suggestions, or are interested in leveraging this work, please feel free to reach out.

Email: souptikc80@gmail.com

LinkedIn: [https://linkedin.com/in/your-profile](https://www.linkedin.com/in/souptik-chakraborty-67385a18a/)

📜 License
This project is licensed under the MIT License. See the LICENSE file for details.
