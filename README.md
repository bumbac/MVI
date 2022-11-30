# NI-MVI Semestra project 2022

**Goal:**
Compare the quality of audio recording of Spanish speakers enhanced by CMGAN model.
I will compare inferred data from :
    1. Model pretrained on english speakers as provided by authors of the CMGAN.
    2. Fine-tuned pretrained model with Spanish speakers.


**Model:**
CMGAN: Conformer-Based Metric-GAN for Monaural Speech Enhancement
Sherif Abdulatif, Ruizhe Cao, Bin Yang
- Paper: [ArXiv](https://arxiv.org/abs/2209.11112)
- Implementation: [GitHub](https://github.com/SherifAbdulatif/CMGAN)
- My testing environment: [Google Colab](https://colab.research.google.com/drive/1dh6u9pUiavzUvHp46ed1p0js6fviYjeP?usp=sharing)
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
Preprocessing notebook: GitLab


**Research:**
CMGAN is almost SoA. The successor SCP-CMGAN offers other metrics system which I did
not understand so I chose the closest solution with available pretrained model and public
dataset. [paperswithcode.com](https://paperswithcode.com/task/speech-enhancement)


**Approach:**
1. Infer evaluation data with the available pretrained model
   a. Compute score (PESQ and STOI).
2. Fine-tune existing pretrained model using custom data with Spanish speakers.

      **a.** Infer evaluation data.

      **b.** Compute score.
3. Compare results.


**Current state:**
1. Successfully processed sample data with pretrained model for comparison.
2. Successfully preprocessed custom training and evaluation data.


**TODO:**
Create and upload training script to CTU computation cluster VM.
Compare results.
Create report.
