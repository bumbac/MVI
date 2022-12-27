# NI-MVI Semestra project 2022

**Goal:**
Compare the quality of audio recording of Spanish speakers enhanced by CMGAN model.
I will compare inferred data from :

    1. Model pretrained on english speakers as provided by authors of the CMGAN.
    2. Fine-tuned pretrained model with Spanish speakers.
    3. Model trained from scratch using custom data.


**Model:**

CMGAN: Conformer-Based Metric-GAN for Monaural Speech Enhancement
Sherif Abdulatif, Ruizhe Cao, Bin Yang

- Paper: [ArXiv](https://arxiv.org/abs/2209.11112)
- Implementation: [GitHub](https://github.com/SherifAbdulatif/CMGAN)
- My training and testing environment: [Google Colab](https://colab.research.google.com/drive/17Ereity6brAaT6wktlQelUwZcTqrGMpb?usp=sharing)
- Custom training script: [GitLab](https://gitlab.fit.cvut.cz/sutymate/mvi-sp/-/blob/master/src/finetrain.py)
- Framework: [PyTorch](https://github.com/SherifAbdulatif/CMGAN/blob/main/src/requirements.txt)


**Data:**
Spanish speaking audio recording in high quality (podcast quality).
Data downloaded from YouTube.
Both sexes - male and female.
After preprocessing 50 minutes of data.
Train:evaluation ratio is 40:10.
Preprocessing consists in:
- Tokenization: split data to short audio files, 3-8 seconds long.
- Downsampling: recommended procedure in paper, 16kHz and 16 bits per sample.
- Adding noise using the [DEMAND dataset](https://zenodo.org/record/1227121) as recommended in the paper.
List of data sources is in the `sources.txt` file.
The preprocessed data are available on my university [Google Drive](https://drive.google.com/drive/folders/169XabHIrAIN7jDUYQXusL27IDqc71rJx?usp=share_link), link in sources.txt.


**Research:**
CMGAN is almost SoA. The successor SCP-CMGAN offers other metrics system which I did
not understand so I chose the closest solution with available pretrained model and public
dataset. [paperswithcode.com](https://paperswithcode.com/task/speech-enhancement)

[GAN training](https://neptune.ai/blog/gan-failure-modes)



**Approach:**

1. Preprocess custom data.
2. Train model from scratch using custom data.
3. Fine-tune existing pretrained model using custom data.
4. Evaluate models with PESQ and STOI metrics:
    5. Scratch.
    6. Fine-tuned.
    7. Pre-trained.

3. Compare results.
4. Prepare [samples](https://drive.google.com/drive/folders/1FXIaY9Mi-1CrgUJFrcU7idJe7hoT3eEF?usp=share_link):
    5. Clean audio.
    6. Noisy audio.
    7. Enhanced with different models.

[Final Report](https://gitlab.fit.cvut.cz/sutymate/mvi-sp/-/blob/master/report.pdf)
