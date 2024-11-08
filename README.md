# Summary
This is the dataset proposed in our paper [**TIP-I2V: A Million-Scale Real Text and Image Prompt Dataset for Image-to-Video Generation**](https://arxiv.org/abs/2411.04709).

TIP-I2V is the first dataset comprising over 1.70 million unique user-provided text and image prompts. Besides the prompts, TIP-I2V also includes videos generated by five state-of-the-art image-to-video models (Pika, Stable Video Diffusion, Open-Sora, I2VGen-XL, and CogVideoX-5B). The TIP-I2V contributes to the development of better and safer image-to-video models.

![image](https://github.com/WangWenhao0716/TIP-I2V/blob/main/assets/teasor.png)
# Datapoint
![image](https://github.com/WangWenhao0716/TIP-I2V/blob/main/assets/datapoint.png)
# Statistics
![image](https://github.com/WangWenhao0716/TIP-I2V/blob/main/assets/stat.png)
# Download
For users in mainland China, try setting `export HF_ENDPOINT=https://hf-mirror.com` to successfully download the weights.
## Download the text and (compressed) image prompts with related information

```python
# Full (text and compressed image) prompts: ~13.4G
from datasets import load_dataset
ds = load_dataset("WenhaoWang/TIP-I2V", split='Full', streaming=True)

# Convert to Pandas format (it may be slow)
import pandas as pd
df = pd.DataFrame(ds)
```


```python
# 100k subset (text and compressed image) prompts: ~0.8G
from datasets import load_dataset
ds = load_dataset("WenhaoWang/TIP-I2V", split='Subset', streaming=True)

# Convert to Pandas format (it may be slow)
import pandas as pd
df = pd.DataFrame(ds)
```

```python
# 10k TIP-Eval (text and compressed image) prompts: ~0.08G
from datasets import load_dataset
ds = load_dataset("WenhaoWang/TIP-I2V", split='Eval', streaming=True)

# Convert to Pandas format (it may be slow)
import pandas as pd
df = pd.DataFrame(ds)
```

## Download the embeddings for text and image prompts

```python
# Embeddings for full text prompts (~21G) and image prompts (~3.5G)
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="Embedding/Full_Text_Embedding.parquet", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="Embedding/Full_Image_Embedding.parquet", repo_type="dataset")
```

```python
# Embeddings for 100k subset text prompts (~1.2G) and image prompts (~0.2G)
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="Embedding/Subset_Text_Embedding.parquet", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="Embedding/Subset_Image_Embedding.parquet", repo_type="dataset")
```

```python
# Embeddings for 10k TIP-Eval text prompts (~0.1G) and image prompts (~0.02G)
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="Embedding/Eval_Text_Embedding.parquet", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="Embedding/Eval_Image_Embedding.parquet", repo_type="dataset")
```

## Download uncompressed image prompts

```python
# Full uncompressed image prompts: ~1T
from huggingface_hub import hf_hub_download
for i in range(1,52):
    hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="image_prompt_tar/image_prompt_%d.tar"%i, repo_type="dataset")
```

```python
# 100k subset uncompressed image prompts: ~69.6G
from huggingface_hub import hf_hub_download
for i in range(1,3):
    hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="sub_image_prompt_tar/sub_image_prompt_%d.tar"%i, repo_type="dataset")
```

```python
# 10k TIP-Eval uncompressed image prompts: ~6.5G
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="eval_image_prompt_tar/eval_image_prompt.tar", repo_type="dataset")
```

## Download generated videos

```python
# Full videos generated by Pika: ~1T
from huggingface_hub import hf_hub_download
for i in range(1,52):
    hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="pika_videos_tar/pika_videos_%d.tar"%i, repo_type="dataset")
```

```python
# 100k subset videos generated by Pika (~57.6G), Stable Video Diffusion (~38.9G), Open-Sora (~47.2G), I2VGen-XL (~54.4G), and CogVideoX-5B (~36.7G)
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="subset_videos_tar/pika_videos_subset_1.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="subset_videos_tar/pika_videos_subset_2.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="subset_videos_tar/svd_videos_subset.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="subset_videos_tar/opensora_videos_subset.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="subset_videos_tar/i2vgenxl_videos_subset_1.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="subset_videos_tar/i2vgenxl_videos_subset_2.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="subset_videos_tar/cog_videos_subset.tar", repo_type="dataset")
```

```python
# 10k TIP-Eval videos generated by Pika (~5.8G), Stable Video Diffusion (~3.9G), Open-Sora (~4.7G), I2VGen-XL (~5.4G), and CogVideoX-5B (~3.6G)
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="eval_videos_tar/pika_videos_eval.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="eval_videos_tar/svd_videos_eval.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="eval_videos_tar/opensora_videos_eval.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="eval_videos_tar/i2vgenxl_videos_eval.tar", repo_type="dataset")
hf_hub_download(repo_id="WenhaoWang/TIP-I2V", filename="eval_videos_tar/cog_videos_eval.tar", repo_type="dataset")
```

# Comparison with VidProM and DiffusionDB
![image](https://github.com/WangWenhao0716/TIP-I2V/blob/main/assets/table.png)
![image](https://github.com/WangWenhao0716/TIP-I2V/blob/main/assets/comparison.png)

Click the [WizMap (TIP-I2V VS VidProM)](https://poloclub.github.io/wizmap/?dataURL=https%3A%2F%2Fhuggingface.co%2Fdatasets%2FWenhaoWang%2FPublic%2Fresolve%2Fmain%2Fdata_tip-i2v_vidprom.ndjson&gridURL=https%3A%2F%2Fhuggingface.co%2Fdatasets%2FWenhaoWang%2FPublic%2Fresolve%2Fmain%2Fgrid_tip-i2v_vidprom.json) and [WizMap (TIP-I2V VS DiffusionDB)](https://poloclub.github.io/wizmap/?dataURL=https%3A%2F%2Fhuggingface.co%2Fdatasets%2FWenhaoWang%2FPublic%2Fresolve%2Fmain%2Fdata_tip-i2v_diffusiondb.ndjson&gridURL=https%3A%2F%2Fhuggingface.co%2Fdatasets%2FWenhaoWang%2FPublic%2Fresolve%2Fmain%2Fgrid_tip-i2v_diffusiondb.json)
(wait for 5 seconds) for an interactive visualization of our 1.70 million prompts.

# Curators
TIP-I2V is created by [Wenhao Wang](https://wangwenhao0716.github.io/) and Professor [Yi Yang](https://scholar.google.com/citations?user=RMSuNFwAAAAJ&hl=zh-CN).

# License

The prompts and videos in our TIP-I2V are licensed under the [CC BY-NC 4.0 license](https://creativecommons.org/licenses/by-nc/4.0/deed.en). 


# Citation
```
@article{wang2024tipi2v,
  title={TIP-I2V: A Million-Scale Real Text and Image Prompt Dataset for Image-to-Video Generation},
  author={Wang, Wenhao and Yang, Yi},
  booktitle={arXiv preprint arXiv:2411.04709},
  year={2024}
}
```

# Contact

If you have any questions, feel free to contact Wenhao Wang (wangwenhao0716@gmail.com).
