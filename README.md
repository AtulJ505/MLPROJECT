# Student Performance Regression Project

A Python project exploring a machine-learning workflow from tabular data ingestion through preprocessing, regression-model comparison, saved artifacts, and a Flask prediction interface.

## Project structure

- `notebook/`: dataset and exploratory notebooks.
- `src/components/data_ingestion.py`: CSV ingestion and reproducible train/test split.
- `src/components/data_transformation.py`: preprocessing for numeric and categorical features.
- `src/components/model_trainer.py`: regression-model comparison and artifact persistence.
- `src/pipeline/predict_pipeline.py`: preprocessing and prediction using saved artifacts.
- `application.py`: Flask routes for the input form and predictions.

## Local setup

```bash
git clone https://github.com/AtulJ505/MLPROJECT.git
cd MLPROJECT
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Use `.venv\Scripts\activate` on Windows. Run commands from the repository root. The dataset is expected at `notebook/data/stud.csv`.

## Train and run

```bash
python -m src.components.data_ingestion
python application.py
```

Training evaluates multiple model families and hyperparameters, so it can take time. The web application listens on port 8000 and expects the trained `artifacts/model.pkl` and `artifacts/preprocessor.pkl` files. Open `http://127.0.0.1:8000/predictdata` for the form.

The prediction interface accepts reading and writing scores alongside the dataset's categorical features. Refer to the notebook for the target variable, feature definitions, preprocessing choices, and dataset provenance.

## Reproducibility and limitations

Dependencies are currently unpinned. Record your Python and package versions when reporting a result, and retain the preprocessing artifact with the model that was trained against it. Only load pickle artifacts from trusted sources.

The current trainer compares models using the test split; a stronger evaluation would choose the model using training/validation data and reserve a final hold-out set for reporting. No accuracy claim or production deployment is implied by this repository. This educational dataset includes demographic attributes; the project is not a validated system for making decisions about students.

## Contributing

Include reproduction steps and dependency versions for bugs. Changes to training should document the split, preprocessing, metrics, and whether a result was actually reproduced. Do not include private student records.
