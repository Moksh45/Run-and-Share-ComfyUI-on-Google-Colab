# Run and Share ComfyUI on Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Moksh45/Run-and-Share-ComfyUI-on-Google-Colab/blob/main/run-and-share-comfyui-on-google-colab.ipynb)

A simple and efficient way to run **ComfyUI** on Google Colab with public URL sharing via **Pinggy**. This notebook allows you to use ComfyUI's powerful node-based interface for Stable Diffusion and other AI models directly in your browser, without any local installation.

## 📋 Overview

[ComfyUI](https://github.com/comfyanonymous/ComfyUI) is a powerful and modular stable diffusion GUI with a graph/nodes interface. This repository provides a Google Colab notebook that:

- ✅ Sets up ComfyUI in a Google Colab environment
- ✅ Installs all necessary dependencies automatically
- ✅ Creates a public URL using Pinggy for easy sharing and access
- ✅ Supports GPU acceleration for faster image generation
- ✅ Requires no local installation or setup

## 🎯 Features

- **Zero Installation**: Run ComfyUI directly in your browser without any local setup
- **GPU Acceleration**: Leverage Google Colab's free GPU resources for faster inference
- **Public Access**: Share your ComfyUI instance with others via a public URL
- **Easy Setup**: Just click and run - all dependencies are installed automatically
- **Free to Use**: Utilize Google Colab's free tier for experimentation

## 📝 Prerequisites

- A Google account to access Google Colab
- Basic understanding of how to use Jupyter notebooks
- Familiarity with ComfyUI (optional, but helpful)

## 🚀 Quick Start

1. **Click the "Open in Colab" badge** at the top of this README
2. **Enable GPU acceleration**:
   - Go to `Runtime` → `Change runtime type`
   - Select `GPU` (T4 recommended) as the hardware accelerator
   - Click `Save`
3. **Run all cells** in order by clicking `Runtime` → `Run all`
4. **Wait for setup** to complete (usually 2-5 minutes)
5. **Access ComfyUI** using the Pinggy URL provided in the output

## 📖 Step-by-Step Guide

### Cell 1: Install System Packages
```bash
!apt-get update
!apt-get install -y wget aria2 libgl1-mesa-glx
```
Installs necessary system packages including `wget`, `aria2` (for faster downloads), and OpenGL libraries.

### Cell 2: Clone ComfyUI Repository
```bash
!git clone https://github.com/comfyanonymous/ComfyUI.git
```
Downloads the official ComfyUI repository from GitHub.

### Cell 3: Install Python Dependencies
```bash
%cd ComfyUI
!pip install -r requirements.txt
```
Navigates to the ComfyUI directory and installs all required Python packages.

### Cell 4: Install Pinggy
```bash
!pip install pinggy
```
Installs Pinggy, a tool for creating secure tunnels to expose local servers to the internet.

### Cell 5: Create Public Tunnel
```python
import pinggy
tunnel1 = pinggy.start_tunnel(forwardto="localhost:8188")
print(f"Tunnel1 started - URLs: {tunnel1.urls}")
```
Creates a public URL that forwards to your local ComfyUI instance running on port 8188.

### Cell 6: Run ComfyUI
```bash
!python main.py --listen 0.0.0.0
```
Starts the ComfyUI server, accessible via the Pinggy URL.

## 🔗 Accessing ComfyUI

After running all cells:

1. Look for the output from Cell 5 showing the Pinggy URLs (e.g., `http://xxxxx.a.free.pinggy.link`)
2. Click on the HTTPS URL (recommended for security)
3. ComfyUI interface will load in your browser
4. Start creating AI-generated images using the node-based workflow!

## ⚠️ Important Notes

- **Runtime Limits**: Google Colab free tier has usage limits. Sessions may disconnect after ~12 hours or if idle too long.
- **GPU Availability**: Free GPU resources are limited. If GPU is unavailable, try again later or use Colab Pro.
- **Pinggy URLs**: The public URLs are temporary and will change each time you run the notebook.
- **Data Persistence**: Files generated during the session will be lost when the runtime disconnects. Download important outputs.
- **Models**: ComfyUI uses default models. To use custom models, you'll need to upload them to the Colab environment (can be time-consuming).

## 💡 Tips and Tricks

- **Keep the browser tab open** to prevent the session from timing out
- **Download your generated images** regularly as they won't persist after the session ends
- **Use shorter workflows** initially to test if everything is working correctly
- **Monitor your GPU usage** in Colab to ensure you're not hitting limits
- **Bookmark the Pinggy URL** during your session for easy access

## 🙏 Credits

- **ComfyUI**: [comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI)
- **Pinggy**: [pinggy.io](https://pinggy.io/)
- **Google Colab**: [colab.research.google.com](https://colab.research.google.com/)
