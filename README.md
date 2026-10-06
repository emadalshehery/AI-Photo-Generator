# AI Image Generation with Stable Diffusion

**Notebook:** `AI_ceate_photo.ipynb`

Text-to-image, image-to-image, and in-painting using Hugging Face `diffusers`.

## Sections

| Section | Pipeline | Model | Prompt / Input |
|---------|----------|-------|----------------|
| Text → Image | `DiffusionPipeline` | `CompVis/stable-diffusion-v1-4` | "Photo of a lion in a jungle" |
| Image → Image | `StableDiffusionImg2ImgPipeline` | `runwayml/stable-diffusion-v1-5` | `Hill and River.png` + "A realistic mountain landscape with a large castle." (`strength=1`) |
| In-painting | `StableDiffusionInpaintPipeline` | `runwayml/stable-diffusion-inpainting` | `cat_on_bench.jpg` + `cat_mask.jpg` ("A photo of an guy"); `desk.jpg` + `desk_mask.jpg` ("A photo of a book") |

## Requirements

- **GPU with CUDA** (models are moved with `.to("cuda")`, e.g. Google Colab GPU runtime)
- `pip install diffusers` (plus `torch`, `transformers`, `matplotlib`, `pillow`)
- Input images must be uploaded next to the notebook: `Hill and River.png`, `cat_on_bench.jpg`, `cat_mask.jpg`, `desk.jpg`, `desk_mask.jpg`

## Notes

- Images are resized to 512×512 for in-painting; the masks mark the area to be replaced.
- The in-painting model download printed a warning about a missing `safetensors` file for the VAE.
- The first code cell starts with a stray `z` before a comment (`z#a tool used...`) which will cause an error; delete it.
