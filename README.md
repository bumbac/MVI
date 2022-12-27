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

[GAN training](https://neptune.ai/blog/gan-failure-modes)



**Approach:**
1. Infer evaluation data with the available pretrained model
   a. Compute score (PESQ and STOI).
2. Fine-tune existing pretrained model using custom data with Spanish speakers.

      **a.** Infer evaluation data.

      **b.** Compute score.
3. Compare results.

### PESQ:




**Results:**

### Training from scratch
5 epochs:

    INFO:root:Generator loss: 1.0044530600309372, Discriminator loss: 0.00038591690390603616
    INFO:root:Generator loss: 0.9820897907018662, Discriminator loss: 0.0005988561392541669
    INFO:root:Generator loss: 0.9860841780900955, Discriminator loss: 0.0006284933011556859
    INFO:root:Generator loss: 0.9680219531059265, Discriminator loss: 0.00022628391907346667
    INFO:root:Generator loss: 1.0031898647546769, Discriminator loss: 0.000825498571521166
**Evaluation:**

    pesq:  1.0641768157482148 csig:  1.4174080517807113 cbak:  1.3879450216314246 covl:  1.1703623086346744 ssnr:  -1.884990330774863 stoi:  0.3174120471978805

50 epochs:

    ...
    INFO:root:Generator loss: 1.0753205329179765, Discriminator loss: 0.005824737032526173
    INFO:root:Generator loss: 1.0676013618707656, Discriminator loss: 0.0008540094800991938
    INFO:root:Generator loss: 1.0410430133342743, Discriminator loss: 0.00013016909961152123
    INFO:root:Generator loss: 1.0918779402971268, Discriminator loss: 0.0001956570455149631
    INFO:root:Generator loss: 1.0473725110292436, Discriminator loss: 9.093053740798496e-05

**Evaluation:**

    pesq:  1.0587524145841598 csig:  1.0777227792749267 cbak:  1.418621684416482 covl:  1.0125614981105242 ssnr:  -1.4984374963315985 stoi:  0.1859480103555091

50 epochs LR1e-8

    ...
    INFO:root:Epoch 31, Step 168, loss: 1.2215607166290283, disc_loss: 0.37016499042510986
    INFO:root:Epoch 31, Step 169, loss: 1.4389499425888062, disc_loss: 0.3658515512943268
    INFO:root:Epoch 31, Step 170, loss: 1.48197340965271, disc_loss: 0.6567169427871704
    INFO:root:Epoch 31, Step 171, loss: 0.6764488220214844, disc_loss: 0.3552115559577942
    INFO:root:Epoch 31, Step 172, loss: 1.4702340364456177, disc_loss: 0.6860331296920776

**Evaluation:**

    pesq:  1.1032311558723449 csig:  1.2620735504715674 cbak:  1.3549868431609529 covl:  1.172604710565108 ssnr:  -2.0698603452510556 stoi:  0.2548194037686168


### Pretrained model from authors:

**Evaluation:**

    pesq:  1.2303554445505143 csig:  1.412312253735375 cbak:  1.4103906610004537 covl:  1.3146698547489466 ssnr:  -2.0189492452763718 stoi:  0.2451594971056267


### Fine-tuning on pretrained model from authors:

5 epochs

    INFO:root:Generator loss: 0.9803555607795715, Discriminator loss: 0.004497478474513627
    INFO:root:Generator loss: 0.9839551508426666, Discriminator loss: 0.0002254387409038827
    INFO:root:Generator loss: 1.0049857378005982, Discriminator loss: 0.00017971180259337415
    INFO:root:Generator loss: 0.9877994626760482, Discriminator loss: 0.0001390831252138014
    INFO:root:Generator loss: 0.9810490518808365, Discriminator loss: 0.0002643458637066942

**Evaluation:**


    pesq:  1.0351979941129685 csig:  1.152096069765623 cbak:  1.4057466341602713 covl:  1.054459746950025 ssnr:  -1.8605812995926392 stoi:  0.2338759234258574

17 epochs LR1e-8

**Evaluation:**

    pesq:  1.2344390451908112 csig:  1.4126004655629687 cbak:  1.4128319739965893 covl:  1.3169226579917268 ssnr:  -2.0149663413693455 stoi:  0.24508382519855107
    

**Current state:**
1. Successfully processed sample data with pretrained model for comparison.
2. Successfully preprocessed custom training and evaluation data.


**TODO:**
Compare results.
Create report.
