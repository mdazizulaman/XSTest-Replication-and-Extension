# 📘 XSTest Replication and Extension  
### *Evaluating Exaggerated Safety Behaviours in Modern Large Language Models*

This repository contains the full codebase, datasets, annotation guidelines, and analysis pipeline used in the project **“XSTest Replication and Extension: Evaluating Exaggerated Safety Behaviours in LLMs.”**  
The project systematically replicates the NAACL 2024 XSTest benchmark and extends it by constructing new diagnostic datasets and evaluating modern instruction-tuned LLMs.

Exaggerated safety refers to **unjustified refusals on safe prompts**, a growing alignment issue that affects the usefulness, trustworthiness, and practical deployment of contemporary LLMs.

---

---

## 🚀 What This Project Does

### **1. Replicates XSTest (NAACL 2024)**
- Full Kaggle-based completion generation (T4×2 GPUs).  
- Manual annotation following original definitions.  
- Automated classification via string-match and GPT-based classifier.  
- Trend comparison with original Llama-2, GPT-4, and Mistral models.

### **2. Evaluates Modern LLMs**
Models tested:
- **Llama-3.0**
- **Llama-3.1**
- **Mistral-7B-Instruct (MistrI)**
- **Mistral-7B-Guard (MistrG)**
- **GPT-4o-mini**

### **3. Builds a New Diagnostic Dataset**
- 250 safe prompts  
- 200 unsafe contrasts  
- Designed using:
  - FalseReject, DNA, SST, OverKill
  - Online dictionaries
  - GPT-5 for controlled prompt generation  
- Independent dual annotation  
  Agreement: **95–98%**, κ = **0.84–0.96**

### **4. Provides Reproducible Pipelines**
- Completion generation  
- Dual manual annotation  
- GPT-based and string-match classifiers  
- Analysis notebooks for producing tables and figures  

---

## 📦 Installation

git clone https://github.com/mdazizulaman/XSTest-Replication-and-Extension
cd XSTest-Replication-and-Extension


## Running the Pipelines

The full workflow consists of four main stages:  
1) Completion Generation → 2) Manual Annotation → 3) Automated Annotation → 4) Analysis and Result Aggregation.  
Each stage is modular and can be run independently.

---

### 1. Completion Generation

This step produces raw model outputs for all prompts.

**Notebook:**  

**Instructions:**
1. Open the notebook in Kaggle (recommended GPU: **T4×2**).  
2. Upload `xstest_prompts.csv` or any dataset following the same schema.  
3. Configure the model ID (e.g., `llama-3-70b-instruct`, `mistral-7b-instruct`, `openai/gpt-4o-mini`).  
4. Set the hyperparameters (as in the XSTest paper):  
   - `max_new_tokens = 256`  
   - `temperature = 0.0`  
5. Run the notebook to generate completion files.  
6. Save outputs 

### 2. Manual Annotation

Annotators classify each completion into:  
**full compliance**, **full refusal**, or **partial refusal**.

### 3. Automated annotation
* python classify_completions_strmatch.py
* python classify_completions_gpt.py

### Load the manual and automated annotated file using analysis.ipynb 
You can see the results.
