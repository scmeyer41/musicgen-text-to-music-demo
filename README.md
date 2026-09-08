# MusicGen Text-to-Music Demo

An exploration of Meta's pretrained MusicGen models for text-conditioned music generation, audio continuation, and melody-conditioned generation. The project uses Python, PyTorch, and the AudioCraft library in Google Colab.

> This was a collaborative academic project for DS 677: Deep Learning at the New Jersey Institute of Technology. The team consisted of me, Michel Fosa, and Mallika Kasi. I proposed MusicGen as the project topic and contributed to the research, technical analysis, documentation, and presentation. My teammates led more of the hands-on demo execution and testing.

## Important distinction

Our team did **not** develop or train MusicGen. MusicGen was developed by Meta AI, and this repository demonstrates how its released pretrained models can be applied. Portions of the notebook follow patterns from Meta's public AudioCraft examples; links to the original project and paper are provided below.

## Demonstrated generation modes

| Mode | Input | Purpose |
|---|---|---|
| Text-conditioned | A written description | Generate music matching a requested genre, mood, or instrumentation |
| Audio continuation | A short waveform | Extend an existing rhythm or melody |
| Melody-conditioned | Text plus a melody | Preserve melodic structure while changing musical style |

The experiments used `facebook/musicgen-small` and `facebook/musicgen-melody`. Parameters such as duration, sampling, and `top_k` were configured to explore the model's output.

## Architecture explored

MusicGen combines three central ideas:

1. **EnCodec audio tokens** convert waveforms into compact discrete representations.
2. **An autoregressive Transformer** predicts sequences of audio tokens.
3. **Conditioning mechanisms** guide generation using text, melody, or both.

This design lets MusicGen model audio using sequence-learning methods while avoiding direct autoregressive prediction of raw waveform samples.

## Repository structure

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── NOTICE.md
└── notebooks/
    └── musicgen_demo.ipynb
```

## Run in Google Colab

MusicGen is computationally demanding. A CUDA-enabled Colab runtime is strongly recommended.

1. Open `notebooks/musicgen_demo.ipynb` in Google Colab.
2. Select **Runtime > Change runtime type > GPU**.
3. Run the installation cell.
4. Run the model-loading and generation cells in order.
5. For the file-based examples, upload an audio clip you have permission to use and update the filename if necessary.

The pretrained model weights are downloaded when the notebook runs. The download can be several gigabytes, and generation time depends on the selected model, clip duration, and available GPU.

## Results and limitations

The demonstration produced examples that followed broad prompt characteristics and retained recognizable melodic guidance. These observations were qualitative; the project did not perform a formal benchmark, human-listening study, model training, or fine-tuning. Outputs may vary because generation uses sampling.

This project should therefore be understood as an applied demonstration and architectural study—not evidence that the team created a new generative model.

## Responsible use

- Use only melody inputs and recordings you have permission to process.
- Do not present generated audio as the work of a real artist.
- Review the terms and model-card guidance associated with MusicGen and AudioCraft before commercial use.
- Consider licensing, attribution, and potential training-data concerns when using generative-audio systems.

## References and attribution

- [MusicGen research paper](https://arxiv.org/abs/2306.05284)
- [Meta AudioCraft repository](https://github.com/facebookresearch/audiocraft)
- [MusicGen documentation](https://github.com/facebookresearch/audiocraft/blob/main/docs/MUSICGEN.md)
- [MusicGen model collection on Hugging Face](https://huggingface.co/facebook/musicgen-small)

MusicGen and AudioCraft are the work of their respective authors and maintainers. This repository is an independent academic demonstration and is not affiliated with or endorsed by Meta.
