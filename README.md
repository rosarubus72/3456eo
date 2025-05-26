# Paper2Poster

Official repository for **Paper2Poster**, a toolkit that automatically converts academic papers into concise, visually appealing posters and provides question–answer pairs for evaluation.

---

## Environment setup

Install pytorch according to your cuda version.

```bash
pip install -r requirements.txt
```

## OpenAI API key

Create a `.env` file in the project root and add your key:

```bash
OPENAI_API_KEY=<your_openai_api_key>
```

---

## Dataset generation
To download Paper2Poster dataset:
```bash
python -m PosterAgent.create_dataset
```

## Run PosterAgent
To generate a poster using PosterAgent:
```bash
python -m PosterAgent.new_pipeline \
    --poster_path="Paper2Poster/${paper_name}/paper.pdf"
```

## Run evaluation
To evaluate a generated poster with PaperQuiz:
```bash
python -m Paper2Poster-eval.eval_poster_pipeline \
    --paper_name="${paper_name}" \
    --poster_method="${model_t}_${model_v}_generated_posters" \
    --metric=qa # PaperQuiz
```

To evaluate a generated poster with VLM-as-Judge:
```bash
python -m Paper2Poster-eval.eval_poster_pipeline \
    --paper_name="${paper_name}" \
    --poster_method="${model_t}_${model_v}_generated_posters" \
    --metric=judge # VLM-as-Judge
```

To evaluate a generated poster with other statistical measures:
```bash
python -m Paper2Poster-eval.eval_poster_pipeline \
    --paper_name="${paper_name}" \
    --poster_method="${model_t}_${model_v}_generated_posters" \
    --metric=stats # statistical measures
```

## Create your own quiz
To create your own PaperQuiz:
```bash
python -m Paper2Poster-eval.create_paper_questions \
    --paper_folder="Paper2Poster/${paper_name}"
```
