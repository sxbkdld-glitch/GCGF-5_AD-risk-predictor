[README.md](https://github.com/user-attachments/files/29838031/README.md)
# GCGF-5 Streamlit Deployment

This package contains the Streamlit deployment files for **GCGF-5**, a compact version of the **Group-aware Clinical-Guided Fusion Network (GCGF)** for predicting MCI-to-AD progression within 36 months / 3 years.

## Package Contents

```text
app.py
adni_backbone_training_common.py
run_streamlit.bat
requirements.txt
environment.yml
.streamlit/config.toml
docs/ENVIRONMENT_SETUP.md
docs/MRI_PREPROCESSING.md
docs/CLINICAL_VARIABLES.md
```

## Required Model Weights

The trained model weights are not included in this minimal package.

Download `GCGF-5_checkpoints.zip` from the **Releases** page of this same GitHub repository:

```text
Releases -> Assets -> GCGF-5_checkpoints.zip
```

After downloading, extract it into the project root. After extraction, the directory should be:

```text
checkpoints/top5/top5_fold0/best_full_clinical_guided_densenet121.pt
checkpoints/top5/top5_fold1/best_full_clinical_guided_densenet121.pt
checkpoints/top5/top5_fold2/best_full_clinical_guided_densenet121.pt
checkpoints/top5/top5_fold3/best_full_clinical_guided_densenet121.pt
checkpoints/top5/top5_fold4/best_full_clinical_guided_densenet121.pt
```

## Required Input

1. A preprocessed T1 MRI NIfTI file:

```text
.nii or .nii.gz
```

Expected final shape:

```text
169 x 208 x 179
```

2. Five clinical variables:

```text
FAQ
APOE4
RAVLT_immediate
CDRSB
LDELTOTAL
```

## Environment Setup

See:

```text
docs/ENVIRONMENT_SETUP.md
```

## MRI Preprocessing

See:

```text
docs/MRI_PREPROCESSING.md
```

## Clinical Variable Scoring

See:

```text
docs/CLINICAL_VARIABLES.md
```

## Run the Project

After installing the environment and placing model weights, run:

```bash
python -m streamlit run app.py --server.port 8501
```

On Windows, you can also double-click:

```text
run_streamlit.bat
```

The `.bat` launcher first tries to use:

```text
.venv\Scripts\python.exe
```

If `.venv` is not found, it uses the system `python` command.

Open the app at:

```text
http://127.0.0.1:8501
```

## Disclaimer

This deployment is a research prototype and is not a certified medical device.
