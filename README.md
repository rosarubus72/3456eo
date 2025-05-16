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

```bash
python create_dataset.py
```

## Create QA for evaluation

```bash
python create_paper_questions.py --paper_folder=<path_to_paper_folder>
```

## Run PosterAgent

```bash
python new_pipeline.py --poster_path=<path_to_paper_pdf>
```

## Run evaluation

```bash
python eval_poster_pipeline.py --paper_name=<name_of_paper> --poster_method=<poster_method> --poster_image_name=poster.png --metric=qa
```