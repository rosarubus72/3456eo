# Paper2Poster: Towards Multimodal Poster Automation from Scientific Papers

<p align="center">
  <a href="" target="_blank"><img src="https://img.shields.io/badge/arXiv-xxx-red"></a>
  <a href="https://paper2poster.github.io/" target="_blank"><img src="https://img.shields.io/badge/Project-Page-brightgreen"></a>
  <a href="https://huggingface.co/datasets/Paper2Poster/Paper2Poster" target="_blank"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Dataset-orange"></a>
</p>

We address **How to create a poster from a paper** and **How to evaluate poster.**

![PaperCoder Overview](./assets/overall.png)

## 🗺️ Outline

- [📚 Introduction](#-introduction)
- [🔧 Environment setup](#-environment-setup)
- [🕹️ Run PosterAgent](#-run-posteragent)
- [🔮 Evaluation](#-evaluation)
---

## 📚 Introduction

**Paper2Poster:** _A benchmark for paper to poster generation, paired with human generated poster, with a comprehensive evaluation suite_, including metrics like **Visual Quality**, **Textual Coherence**, **VLM-as-Judge** and **PaperQuiz**. Notably, PaperQuiz is a novel evaluation which assume _A Good poster should convey core paper content visually_.


![PaperCoder Overview](./assets/paperquiz.png)

**PosterAgent:** _A Top-down, visual-in-the-loop, efficient multi-agent pipeline_, which includes (a) Parser distills the paper into a structured asset library; the (b) Planner aligns text–visual pairs into a binary‐tree layout that preserves reading order and spatial balance; and the (c) Painter-Commentor loop refines each panel by executing rendering code and using VLM feedback to eliminate overflow and ensure alignment.

![PaperCoder Overview](./assets/posteragent.png)

---

## 🔧 Environment setup

Install pytorch according to your cuda version.

```bash
pip install -r requirements.txt
```

### OpenAI API key

Create a `.env` file in the project root and add your key:

```bash
OPENAI_API_KEY=<your_openai_api_key>
```

---

### Setup Datasets
To download Paper2Poster dataset:
```bash
python -m PosterAgent.create_dataset
```

## 🕹️ Run PosterAgent
To generate a poster using PosterAgent:
```bash
python -m PosterAgent.new_pipeline \
    --poster_path="Paper2Poster/${paper_name}/paper.pdf"
```

## 🔮 Evaluation
To evaluate a generated poster with **PaperQuiz**:
```bash
python -m Paper2Poster-eval.eval_poster_pipeline \
    --paper_name="${paper_name}" \
    --poster_method="${model_t}_${model_v}_generated_posters" \
    --metric=qa # PaperQuiz
```

To evaluate a generated poster with **VLM-as-Judge**:
```bash
python -m Paper2Poster-eval.eval_poster_pipeline \
    --paper_name="${paper_name}" \
    --poster_method="${model_t}_${model_v}_generated_posters" \
    --metric=judge # VLM-as-Judge
```

To evaluate a generated poster with other statistical metrics (such as visual similarity, PPL, etc):
```bash
python -m Paper2Poster-eval.eval_poster_pipeline \
    --paper_name="${paper_name}" \
    --poster_method="${model_t}_${model_v}_generated_posters" \
    --metric=stats # statistical measures
```

### 📦 Create your own Quiz
To create your own PaperQuiz:
```bash
python -m Paper2Poster-eval.create_paper_questions \
    --paper_folder="Paper2Poster/${paper_name}"
```

## 📖 Citation

Please kindly cite our paper if you find this project helpful.

```bibtex

```
