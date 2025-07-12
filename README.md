
# 🧠 Natural Language to SQL Queries

## 📘 Project Overview

**Aim:**  
To convert natural language questions (e.g., *"List all students who scored above 90"*) into their corresponding **SQL queries** using Natural Language Processing and models trained on datasets like **Spider** or **WikiSQL**.

This project explores the field of **Text-to-SQL translation**, bridging human-friendly questions and database-friendly queries.

---

## 🚀 Features

- 🔤 **Natural Language Understanding**: Accepts questions in plain English.
- 🗃️ **SQL Query Generation**: Automatically generates corresponding SQL.
- 📊 **Schema Awareness**: Handles complex DB schema involving multiple tables and joins.
- 🧠 **Pretrained Language Models**: Utilizes models like **T5** or **BERT** for semantic mapping.
- ⚙️ **Custom Fine-Tuning**: Trained on benchmarks like Spider/WikiSQL.
- 🔍 **Interactive Notebook**: A Jupyter notebook workflow for experimentation and testing.


---

## 🧪 Workflow Summary

1. **Input**: Natural language question  
   🗣️ *"Show all employees hired after 2020"*

2. **Model**: Encoder-decoder model processes the input using schema context.

3. **Output**:  
   🧾 `SELECT * FROM employees WHERE hire_date > "2020-01-01";`

---

## 🔧 Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/yourusername/nl2sql-project.git
cd nl2sql-project
```

### 2. Install Dependencies

Create a virtual environment and install requirements:

```bash
pip install library_name
```

Example dependencies:
```
transformers
datasets
torch
sentencepiece
scikit-learn
unsloth
```

---

## 🧠 Model Details

| Component       | Description                                    |
|----------------|------------------------------------------------|
| Language Model | T5-base / BART / GPT-style encoder-decoder     |
| Input Format   | NL question + DB schema context                |
| Output Format  | Valid SQL query                                 |
| Dataset        | Spider / WikiSQL                                |

---

## 📓 Notebook Highlights (`Text_to_sql_(1).ipynb`)

| Section                     | Purpose                                                                 |
|----------------------------|-------------------------------------------------------------------------|
| Data Loading               | Prepares and tokenizes natural language & SQL pairs                     |
| Model Loading/Fine-tuning  | Loads pretrained T5 and fine-tunes it on the dataset                    |
| Evaluation Metrics         | Measures accuracy, exact match, and execution match                     |
| Inference Cell             | Allows real-time testing of your own NL questions                       |

---

## 📊 Sample Usage

```python
# Input
question = "List all departments where employee count > 100"
schema = {
    "tables": ["departments", "employees"],
    "foreign_keys": [("departments.id", "employees.department_id")]
}

# Output
SQL: SELECT name FROM departments WHERE (SELECT COUNT(*) FROM employees WHERE employees.department_id = departments.id) > 100;
```

---

## 🛠️ Tech Stack

- **Language**: Python
- **Notebook Interface**: Jupyter
- **Libraries**: Transformers, Datasets, Torch
- **Datasets**: Spider, WikiSQL
- **Model**: T5 / BART / LLaMA

---

## 📂 Sample Dataset (Spider Format)

```json
{
  "question": "How many stadiums are there?",
  "query": "SELECT count(*) FROM stadium",
  "db_id": "sports_database"
}
```

---

## ✅ How to Run

### Open Notebook
Launch Jupyter and open:

```bash
jupyter notebook Text_to_sql_(1).ipynb
```

Follow the cell execution in order:
1. Load & preprocess data
2. Load/fine-tune model
3. Run inference

---

## 📌 Tips

- Preprocess your schema in a **linearized format**:  
  *"Table: employees, Columns: id, name, hire_date"*

- Use `transformers.Trainer` for easy fine-tuning

- For production, wrap inference in a simple Flask API

---

## 🔬 Future Enhancements

- 🔗 Add schema linking and question clarification support.
- 📚 Support cross-domain databases.
- 🎯 Improve generalization to unseen schemas via meta-learning.

---

## 📃 License

This project is for academic and research purposes.  
Feel free to modify and extend it for your own experiments.
