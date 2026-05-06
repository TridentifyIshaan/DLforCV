# Install WSL2 & Latest TensorFlow for GPU

You have chosen the "Latest Tech" path! This is the professional standard for doing Deep Learning on Windows machines.

By doing this, we will be installing a native Ubuntu Linux environment on your computer. Your Windows GPU will automatically be passed through to this Linux environment. 

## ⚠️ User Review Required: Workflow Changes

Before we begin, you need to understand how your workflow will change:
1. **Linux Filesystem**: Right now, your project is on your Windows Desktop. If we run Linux code on Windows files, it will be very slow. We will need to copy your `DLforCV` folder into the Linux filesystem.
2. **VS Code WSL Mode**: You will no longer just open the folder in Windows. You will use the "WSL" extension in VS Code to open the folder *inside* the Linux environment.
3. **New Environment**: Your current Windows `.venv` will be abandoned. We will create a brand new Linux Python environment with the absolute newest TensorFlow.

## Proposed Changes

We will execute the following steps:

### 1. Install Ubuntu Distribution
The WSL2 core is already installed on your PC, but it has no Linux distribution.
- Run `wsl --install -d Ubuntu`
- **IMPORTANT:** This will likely open a new terminal window asking you to create a "UNIX username" and "password". You must complete this manually when the window pops up.

### 2. Move Project to Linux
- Copy `c:\Users\Ishaan Rastogi\Desktop\DLforCV` to the Ubuntu home directory (`~`).

### 3. Setup Python & TensorFlow (Linux Side)
- Install `python3-venv` and `python3-pip` in Ubuntu.
- Create a new virtual environment.
- Install the absolute newest `tensorflow[and-cuda]` package. This automatically pulls the newest NVIDIA CUDA libraries.

### 4. Connect VS Code
- Ensure you have the "WSL" extension installed in VS Code.
- Re-open your `DLforCV` folder using the WSL connection.
- Select the new Linux Python kernel for your Jupyter Notebook.

## Verification Plan

### Automated Tests
- Run `python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"` inside WSL to confirm the GPU is perfectly detected by the newest TensorFlow.

### Manual Verification
- You will run your `7.ipynb` notebook from the WSL connection and verify that training speeds are incredibly fast using the latest TF 2.16+ version.
