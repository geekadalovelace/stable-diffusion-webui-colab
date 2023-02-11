# Colab Installation
```shell
!pip install -q https://github.com/camenduru/stable-diffusion-webui-colab/releases/download/0.0.16/xformers-0.0.16+814314d.d20230118-cp38-cp38-linux_x86_64.whl
 
!pip install -q --pre triton
 
 
 
!git clone -b v1.6 https://github.com/camenduru/stable-diffusion-webui
 
!wget https://raw.githubusercontent.com/camenduru/stable-diffusion-webui-scripts/main/run_n_times.py -O /content/stable-diffusion-webui/scripts/run_n_times.py
 
!git clone -b v1.6 https://github.com/camenduru/deforum-for-automatic1111-webui /content/stable-diffusion-webui/extensions/deforum-for-automatic1111-webui
 
!git clone -b v1.6 https://github.com/camenduru/stable-diffusion-webui-images-browser /content/stable-diffusion-webui/extensions/stable-diffusion-webui-images-browser
 
!git clone -b v1.6 https://github.com/camenduru/stable-diffusion-webui-huggingface /content/stable-diffusion-webui/extensions/stable-diffusion-webui-huggingface
 
!git clone -b v1.6 https://github.com/camenduru/sd-civitai-browser /content/stable-diffusion-webui/extensions/sd-civitai-browser
 
!git clone -b v1.6 https://github.com/camenduru/sd-webui-additional-networks /content/stable-diffusion-webui/extensions/sd-webui-additional-networks
 
%cd /content/stable-diffusion-webui
 
 
 
!wget https://civitai.com/api/download/models/8958 -O /content/stable-diffusion-webui/models/Stable-diffusion/chilloutmix_mix.safetensors
 
!wget https://moritz.pm/files/ulzzang-6500.pt -O /content/stable-diffusion-webui/embeddings/ulzzang-6500.pt
 
!wget https://huggingface.co/stabilityai/sd-vae-ft-mse-original/resolve/main/vae-ft-mse-840000-ema-pruned.ckpt -O /content/stable-diffusion-webui/models/VAE/vae-ft-mse-840000-ema-pruned.ckpt
 
 
 
!sed -i -e '''/prepare_environment()/a\    os.system\(f\"""sed -i -e ''\"s/self.logvar\\[t\\]/self.logvar\\[t.item()\\]/g\"'' /content/stable-diffusion-webui/repositories/stable-diffusion-stability-ai/ldm/models/diffusion/ddpm.py""")''' /content/stable-diffusion-webui/launch.py
 
!sed -i -e '''/prepare_environment()/a\    os.system\(f\"""sed -i -e ''\"s/dict()))/dict())).cuda()/g\"'' /content/stable-diffusion-webui/repositories/stable-diffusion-stability-ai/ldm/util.py""")''' /content/stable-diffusion-webui/launch.py
 
!sed -i '$a fastapi==0.90.0' requirements_versions.txt
 
!python launch.py --share --xformers --enable-insecure-extension-access
```
