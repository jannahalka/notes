# ITU BDS MLOPS'25 - Project
This project is a submission for MLOPS final project.
Authors: Jan Nahalka & Oliver Souc

## Project Organization
```
.
├── .github
│   └── workflows
│       └── test_action.yml
├── .gitignore
├── .dagger
│   ├── dagger.gen.go
│   ├── go.mod
│   ├── go.sum
│   ├── internal
│   └── main.go
├── LICENSE
├── Makefile
├── README.md
├── dagger.json
├── pyproject.toml
├── requirements.txt
├── data
│   ├── interim
│   │   └── make_dataset.py
│   ├── processed
│   └── raw
├── models
├── notebooks
│   └── main.ipynb
├── tests
│   ├── data
│   │   ├── training_data.csv
│   │   ├── X.csv
│   │   └── y.csv
│   └── test_training_data.py
└── itu_sdse_project
    ├── config.py
    ├── features.py
    ├── helpers.py
    └── modeling
        ├── predict.py
        ├── selection.py
        └── train.py
```
## Installation
> Make sure you have [Go](https://go.dev/doc/install), [Python](https://www.python.org/downloads/), and [dvc](https://doc.dvc.org/install) already installed on your machine.

To start out using the project, clone the repository and follow the these steps:
```bash
# 1. Create virtual environment
make create_environment

# 2. Activate virtual environment
workon itu-sdse-project

# 3. Install dependecies
make requirements

# 4. Pull raw data (Optional for dagger workflow)
dvc get https://github.com/Jeppe-T-K/itu-sdse-project-data \
raw_data.csv -o data/raw
```

## 📚 Documentation
In this project we split Jupyter notebook located in `notebooks/main.ipynb` into manageable, clean and easy to read code throughout the codebase.

First we tackled the data cleaning part of the notebook, where we placed data generation into `make_dataset.py` files inside the `data/` directory.

## Usage


## Project requirements checklist
- [x] Usage of Git
- [x] Usage of PRs
- [x] Decomposition of the notebook
- [x] Adherence to the MLOps project structure
- [x] Presence of tests
- [x] Management of data
- [x] Presence of a workflow that trains the model
- [x] Presence of a workflow that tests the model
- [x] Orchestration of dagger workflow through gh actions

## Todos - NOT PART OF README.md

### TODO: General logging for the project
Throughout the project we have tasks like training, cleaning data, selecting best performing model, etc. All of that should come with logging, which will enhance developer experience, while running and debugging various scripts.
### TODO: Test for the model inference
Right now the model inference is in the file `itu_sdse_project/modeling/selection` we will move this into a test suite, which will later be run in dagger function. The test will assert if the output of the model given test features matches set of test labels.
- Testing features are under `data/processed/X_test.csv`
- Testing labels are under `data/processed/y_test.csv`

### TODO: Fix the warning logs shown while training models
When running a train script for logistic regression model, the command line prints out warnings ranging from unfit parameter values to lack of configuration definition in mlflow. Check this for both models.

![[Pasted image 20251120233321.png]]

## Exam Notes
- We have not implemented deployment to the production since it was not required in the exam document.
