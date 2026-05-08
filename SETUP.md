# Development Setup Instructions

## Install uv (one-time)
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

## Setup for Each Package

Replace `01_numpy` with `02_pandas`, `03_matplotlib`, etc.

### 1. Create package structure
```bash
mkdir -p notebooks/01_numpy/src
cd notebooks/01_numpy
```

### 2. Initialize project
```bash
uv init
```

### 3. Add dependencies
```bash
# For numpy
uv add numpy jupyter ipykernel matplotlib

# For pandas
uv add pandas numpy jupyter ipykernel matplotlib

# For matplotlib
uv add matplotlib numpy jupyter ipykernel

# For scikit-learn
uv add scikit-learn numpy pandas matplotlib jupyter ipykernel

# For pytorch
uv add torch torchvision numpy matplotlib jupyter ipykernel
```

### 4. Start Jupyter
```bash
uv run jupyter notebook src/
```

### 5. Create notebook
- Create `src/basics.ipynb`
- Write code and test locally

### 6. Before committing
```bash
# Clear outputs
uv run jupyter nbconvert --clear-output --inplace src/*.ipynb

git add .
git commit -m "Add [package] basics"
git push
```

## .gitignore
Add to repo root:
```
*.ipynb_checkpoints/
.venv/
__pycache__/
*.pyc
```