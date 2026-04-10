# Assignement-7---Capstone-Project
Deployment and Execution Guide : Google Colab
Prerequisites: Environment Setup
Before execution, the following credentials must be added to the Google Colab Secrets
(🔑 icon on the left sidebar):
1. HF_TOKEN: A Hugging Face Read-Access token (required to download the
gated Mistral model).
2. NGROK_AUTH_TOKEN: Your personal authtoken from the Ngrok Dashboard.
Ensure the "Notebook Access" toggle is turned ON for both secrets.
3. Change runtime type to T4 GPU
Steps to Run the Model:
1. Initialize the Environment: Run all setup cells to install dependencies (Streamlit,
Transformers, Pyngrok) and define the app.py script.
2. Authentication & Loading: Execute the final deployment cell. This script securely
retrieves your tokens from Colab Secrets and initiates the model download from
the Hugging Face Hub.
3. Monitor Model Initialization: * The LLM (Mistral-7B-Instruct-v0.3) is loaded in 4-bit
quantization to fit within the 16GB T4 VRAM.
4. Establish Tunnel: The script executes ngrok.connect(8501), which creates a
secure, high-bandwidth gateway and provides a public URL (e.g.,
https://your-unique-id.ngrok-free.app).
5. Once you open the URL wait for the model to download should take 7-10
minutes
User Interaction:
● Execution: * Select a news source (Google News or BBC World) from the
sidebar.
○ Adjust the Clustering Sensitivity slider (lower values create more specific
clusters; higher values group broader topics).
○ Click the “🚀 Fetch, Summarize & Evaluate” button.
● Real-Time Processing: The request is sent back to the Colab GPU. The system
performs embedding-based clustering via the CPU and generates summaries
using the GPU. Each cluster will display a 5-word headline, a 3-sentence
summary, and performance metrics (Latency, Compression Ratio, and
ROUGE-L).
