# 🤖 SmolLM3-RAG: A High-Performance, Low-Cost RAG System
An end-to-end Retrieval-Augmented Generation (RAG) project demonstrating how a fine-tuned small language model (SLM) can achieve near state-of-the-art performance with significantly lower computational and memory requirements.

## 🎯 Overview & Motivation
The goal of this project is to bridge the gap between large, expensive proprietary models and practical, real-world applications. While models like GPT-4 are powerful, their API costs and latency can be prohibitive. This project demonstrates that a carefully fine-tuned, smaller open-source model can deliver a high-quality user experience for complex Q&A tasks at a fraction of the cost.

This system is designed to be a blueprint for building efficient, production-ready AI assistants that are both intelligent and economical.

## 🎬 Live Demo
Here is a quick look at the Gradio interface in action, providing a structured, sourced answer to a user's query.

----- Link/Gif to be pasted -----

## ✨ Key Features
✍️ High-Quality Responses: Fine-tuned to provide structured, detailed, and factual answers.

⚡ Low Latency: Implements real-time streaming of tokens for an interactive user experience.

💰 Cost-Effective: Utilizes 4-bit quantization (bitsandbytes) to drastically reduce the memory footprint, allowing deployment on consumer-grade or free-tier cloud GPUs.

🌐 Up-to-Date Information: Integrates a live web search component to ground responses in current information.

📦 Modular & Reproducible: The entire pipeline, from data retrieval to model generation, is broken down into clear, reusable Python modules.

## 🏗️ Architecture & Training Details
The system follows a classic RAG pipeline, optimized for speed and efficiency.

(Note: Create a simple diagram using a tool like Excalidraw or draw.io and upload it.)

Search & Retrieval: User queries are sent to a web search engine (ddgs).

Vector Indexing: The retrieved text snippets are encoded into vectors using all-MiniLM-L6-v2 and indexed with a FAISS vector database for efficient semantic search.

Context Stuffing: The most relevant snippets are selected and injected into a carefully engineered prompt.

Generation: The soupstick/smollm3-fixed model, running in 4-bit precision, generates the response, which is streamed back to the user.

Fine-Tuning: The base model was fine-tuned on a curated dataset of high-quality question-answer pairs to improve its ability to follow instructions and generate structured, Markdown-formatted output.

## 🏆 Benchmark Results
The fine-tuned SmolLM3-RAG model shows remarkable performance on commonsense reasoning and knowledge-based QA tasks, approaching the accuracy of the much larger LLaMA-2 7B model while being significantly more efficient.

<img width="674" height="402" alt="Screenshot (5)" src="https://github.com/user-attachments/assets/f7585d09-d21e-49e6-955c-57b16a9e740b" />


## 🚀 Speed, Latency & Deployment
Performance is not just about accuracy. This project prioritizes a responsive user experience.

Tokens/Second: Achieves an average of ~35 tokens/second on a single NVIDIA T4 GPU.

Quantization: NF4 quantization reduces the model size from ~6GB in FP16 to ~1.5GB in 4-bit.

Streaming: Uses TextIteratorStreamer to begin showing the response to the user in under a second.

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
