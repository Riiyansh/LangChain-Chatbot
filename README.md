# Project Prototype – Chat with PDF (LangChain + Hugging Face)

This repository contains the prototype developed during the internship.  
The main work is inside the Jupyter Notebook (`project_prototype.ipynb`) file.  

---

## 📥 Downloading the Notebook

1. Click on the notebook file (`project_prototype.ipynb`) in this repository.  
2. On the top-right corner of the file preview, click **Download raw file**.  
   - Alternatively, clone the repository using:  
     ```bash
     git clone <repo-link>
     cd <repo-name>
     ```
   - The notebook will be available inside the cloned folder.  

---

## ▶️ Running the Notebook

You can run the notebook in **Google Colab** or **Jupyter Notebook**.

### Option 1: Run on Google Colab  
1. Open [Google Colab](https://colab.research.google.com/).  
2. Click on **File > Upload Notebook**.  
3. Select the downloaded `.ipynb` file.  
4. Run the cells in sequence.  

### Option 2: Run Locally (Jupyter Notebook)  
1. Make sure you have Python installed (≥3.8).  
2. Install Jupyter Notebook if not already installed:  
   ```bash
   pip install notebook
Navigate to the project folder and start Jupyter:

bash
Copy code
jupyter notebook
Open the .ipynb file and run all cells.

---

### ⚙️ Dependencies
The notebook installs most libraries automatically. Key packages include:

langchain + langchain-community (PDF loading, vector search, conversational chain)

faiss-cpu (vector database for embeddings)

sentence-transformers (MiniLM embeddings)

transformers (Hugging Face models & pipelines)

accelerate (optimizations for Hugging Face)

pypdf (PDF reading)

---

## 🔍 How the Model Works
This prototype allows you to chat with a PDF using LangChain and Hugging Face models.

PDF Upload & Splitting

Uploads a PDF via Colab.

Splits content into overlapping chunks (500 chars, 50 overlap).

Embedding + Vector Store

Uses all-MiniLM-L6-v2 sentence embeddings.

Stores them in a FAISS vector database for efficient retrieval.

LLM (FLAN-T5)

Loads google/flan-t5-large from Hugging Face.

Runs as a text generation pipeline.

Custom Prompt

Ensures answers are concise and based only on PDF context.

Responds with “I don’t know” if answer isn’t found.

Conversational Retrieval Chain

Maintains chat history with ConversationBufferMemory.

Uses LangChain’s ConversationalRetrievalChain to combine context + history.

Interactive Q&A

User can repeatedly ask questions.

Answers are generated dynamically from PDF + conversation history.

---

## 📊 Example Flow
Upload a PDF.

Ask: “What is the main topic of this document?”

Model retrieves relevant chunks → FLAN-T5 generates concise answer.

Continue chatting while context + history are remembered.

---

## 🚀 Future Enhancements
This project is built using the LangChain framework, making it highly extensible.
In the future, you can:

Swap the Hugging Face model (FLAN-T5) with more powerful paid LLMs such as OpenAI GPT or Google Gemini.

Since LangChain abstracts away the underlying model, you only need to slightly modify the code (change the LLM initialization) to use these alternatives.

Add support for larger PDFs, multi-file Q&A, or improved vector databases.

