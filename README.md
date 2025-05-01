# TopicModelling Research papers with BERTopic
This project uses BERTopic along with OpenAI's GPT-4o-mini to generate meaningful topic names and analyze 63,000+ research papers. 

The project is split into 3 efficient, modular parts to ensure reusability and fast experimentation.

## 🧠 Project Structure

### 🔹 Part 1: Topic Modeling Pipeline + Caching  
- Load the [`neuralwork/arxiver`](https://huggingface.co/datasets/neuralwork/arxiver) dataset.
- Preprocess abstracts.
- Apply **BERTopic** for topic modeling.
- Use **GPT-4o-mini** to assign **descriptive topic names**.
- Save results (`info, topic, topic name`) and visualisations into a CSV in Google Drive — so you **never have to re-run** this compute-heavy step again.

### 🔹 Part 2: Final Dataset Construction  
- Download original dataset (full metadata: `id, title, abstract, authors, date, link, markdown`).
- Merge with saved topic modeling results from Part 1.
- Final DataFrame format: `id | title | abstract | authors | published_date | link | markdown | topic | Topic Name`

### 🔹 Part 3: Insights & Analysis  
- Visualizations:
- `topic_model.visualize_barchart()`
- `visualize_heatmap()`
- `visualize_topics()`
- `visualize_hierarchy()`
- Key Analyses:
1. **Top 10 Topics by Paper Count**
   - Most frequent: `Astrophysics of Neutrinos and Black Holes` (9561 papers)
   - Least frequent: `Renewable Energy and Grid Management` (509 papers)
    ![image](https://github.com/user-attachments/assets/df207f4a-c519-4319-90c6-f42c33c2e0c4)

     
2. **Papers Published Per Month**
   - 📈 **Peak month**: May 2023 (4701 papers)
   - 📉 **Lowest month**: Sept 2022 (1 paper)
     ![image](https://github.com/user-attachments/assets/fa8d0eca-31bc-415a-a1c4-4d9c68e51b0d)

3. **Monthly Trends of Top 5 Topics**
   - Trends shown for:
     - Astrophysics of Neutrinos and Black Holes
     - Audio Recognition and Analysis
     - Deep Neural Network Optimization Techniques
     - Medical Imaging Segmentation and Diagnosis
     - Quantum Phase Transitions and Spin Dynamics
     ![image](https://github.com/user-attachments/assets/9dc42b9c-62c1-4f33-b8d7-e729dbccc9bf)

---

## 🗂️ Dataset Details
- **Source**: [neuralwork/arxiver](https://huggingface.co/datasets/neuralwork/arxiver)
- **Fields**: ID, Title, Abstract, Authors, Date, Markdown, Link.
- **Size**: 63,357 papers (September 2022 – October 2023)
  
---

## 🛠️ Model & Config
- **Embedding**: `all-MiniLM-L6-v2`
- **UMAP**:
- `n_neighbors=10`, `min_dist=0.1`
- **HDBSCAN**:
- `min_cluster_size=60`, `min_samples=15`
- **Topic Naming**:
- **GPT-4o-mini** used to summarize top words from each topic into **reader-friendly labels**

---

## 📊 Visualizations
(Open the notebook to view interactive graphs)

| Type | Sample |
|------|--------|
| **Bar Chart** | ![image](https://github.com/user-attachments/assets/c1b108ee-9ec4-4c9f-8f5c-f6b6a41b971a)|
| **Heatmap** | ![image](https://github.com/user-attachments/assets/cf15866c-cfb0-4ef9-af34-5261414c0412)|
| **Inter-Topic Distance** | ![image](https://github.com/user-attachments/assets/d41eb35f-eaf4-47e9-b662-c01aebd5b2a7)|

---

## 🧪 Sample Analysis (Top 5 Topics)

| Topic Name | Peak Month | Trough Month | Total Papers |
|------------|------------|--------------|--------------|
| Astrophysics of Neutrinos and Black Holes | Jul 2023 (1089) | Oct 2022 (1) | 9561 |
| Audio Recognition and Analysis | May 2023 (190) | Dec 2022 (3) | 1166 |
| Deep Neural Network Optimization | Oct 2023 (94) | Dec 2022 (2) | 787 |
| Medical Imaging & Diagnosis | Mar 2023 (183) | Dec 2022 (2) | 1412 |
| Quantum Phase Transitions | Mar 2023 (842) | Nov 2022 (1) | 7659 |

---
## 💡 Why This Matters

- **Faster Iteration**: Cached outputs (topics + names) make it easy to rerun analysis anytime.
- **Human-Centric Topics**: GPT-4o naming boosts clarity and presentation value.
- **Topic Evolution**: Monthly trends reveal emerging or fading fields.
- **Customizable**: You can easily extend this notebook to:
- Add new months
- Train on more papers
- Refine topic naming
---


