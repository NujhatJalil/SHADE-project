# The S.H.A.D.E. Project - ADSC F25

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>

The Systematic Heat Analysis and Data Evaluation Project @ Texas A&M University.\
Predictive modeling for heat waves, analyzing time-series temperature data from Austin, TX (1999-2023).

Naming convention for all files is team name, a number (for ordering), and a short `-` delimited description, e.g. `ml-1.0-initial-data-exploration.ipynb` or `hybrid-1.0-heatmap-calendar.png`.

## Project Organization

```
├── Makefile
├── README.md          <- The top-level README for developers using this project.
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is team name, a number (for ordering),
│                         and a short `-` delimited description, e.g.
│                         `ml-1.0-initial-data-exploration`.
│
├── pyproject.toml     <- Project configuration file with package metadata
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.cfg          <- Configuration file for flake8
│
└── the_s.h.a.d.e._project___adsc_f25   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes the_s.h.a.d.e._project___adsc_f25 a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Scripts to download or generate data
    │
    ├── features.py             <- Code to create features for modeling
    │
    ├── modeling                
    │   ├── __init__.py 
    │   ├── predict.py          <- Code to run model inference with trained models          
    │   └── train.py            <- Code to train models
    │
    └── plots.py                <- Code to create visualizations
```

--------

