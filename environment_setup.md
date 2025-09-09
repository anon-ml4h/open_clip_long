
## Step 1: Create a Virtual Environment
```
conda create --name train_clip python=3.9
conda activate train_clip
```

## Step 2: Install torch 
Make sure to search for correct cuda ver.
```
pip3 install torch torchvision --index-url https://download.pytorch.org/whl/cu122
```

## Step 3: Clone Open CLIP repo and install
```
git clone https://github.com/mlfoundations/open_clip.git

# Enter the project root directory
cd open_clip

# Install training dependcies 
pip install -r requirements-training.txt

# Install wandb
pip install wandb

```

## Step 4: Setup HF and Weights & Biases
```
huggingface-cli login
wandb login
```


## Step 5: Update job submission script

### 0. Switch to branch `bmc-512-long`

We will use `scripts/submit_job.py` to submit the training job.

### 1. Replace the default environment initialization with your environment name:
```
source "$HOME/miniconda3/etc/profile.d/conda.sh"
conda activate {CONDA_ENV}
```

### 2. Update the `LOG_PATH` variable to the directory where you want checkpoint to be saved:
```
LOG_PATH = "/path/to/logs"
```


## Step 6: Submit job
Once the script is configured, submit your job from inside the scripts/ directory:
```
conda activate train_clip
python submit_job.py
```



