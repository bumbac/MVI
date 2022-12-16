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






Training from scratch, 5 epochs:

    INFO:root:Generator loss: 1.0044530600309372, Discriminator loss: 0.00038591690390603616
    INFO:root:Generator loss: 0.9820897907018662, Discriminator loss: 0.0005988561392541669
    INFO:root:Generator loss: 0.9860841780900955, Discriminator loss: 0.0006284933011556859
    INFO:root:Generator loss: 0.9680219531059265, Discriminator loss: 0.00022628391907346667
    INFO:root:Generator loss: 1.0031898647546769, Discriminator loss: 0.000825498571521166
Evaluation:

    pesq:  1.0641768157482148 csig:  1.4174080517807113 cbak:  1.3879450216314246 covl:  1.1703623086346744 ssnr:  -1.884990330774863 stoi:  0.3174120471978805

Training from scratch, 50 epochs:

    INFO:root:Generator loss: 0.9738902419805526, Discriminator loss: 0.0004084870933866114
    INFO:root:Generator loss: 0.9725780338048935, Discriminator loss: 0.0018327188306102471
    INFO:root:Generator loss: 0.9634257942438126, Discriminator loss: 0.0022692547257975094
    INFO:root:Generator loss: 1.005217006802559, Discriminator loss: 0.0013587505243776831
    INFO:root:Generator loss: 0.9515760540962219, Discriminator loss: 0.001605068576100166
    INFO:root:Generator loss: 0.9593596309423447, Discriminator loss: 0.000416731200311915
    INFO:root:Generator loss: 0.9414912819862366, Discriminator loss: 0.0004748937507429218
    INFO:root:Generator loss: 0.9729780316352844, Discriminator loss: 0.00030636623214377325
    INFO:root:Generator loss: 1.0468609809875489, Discriminator loss: 0.00048415454821224555
    INFO:root:Generator loss: 1.0191098541021346, Discriminator loss: 0.0001870904319730471
    INFO:root:Generator loss: 1.0200064212083817, Discriminator loss: 0.00029639989652423536
    INFO:root:Generator loss: 1.0671175956726073, Discriminator loss: 0.0001523649574664887
    INFO:root:Generator loss: 1.0065761804580688, Discriminator loss: 0.00010405286220702692
    INFO:root:Generator loss: 0.995909008383751, Discriminator loss: 0.008662087500124472
    INFO:root:Generator loss: 1.0159991353750228, Discriminator loss: 0.000182370871425519
    INFO:root:Generator loss: 1.0039551854133606, Discriminator loss: 0.00012664271698668018
    INFO:root:Generator loss: 1.0257580250501632, Discriminator loss: 0.00011018243333182909
    INFO:root:Generator loss: 1.068786734342575, Discriminator loss: 0.00014884724787407323
    INFO:root:Generator loss: 1.0456076204776763, Discriminator loss: 0.00015389831041829894
    INFO:root:Generator loss: 1.0347481161355971, Discriminator loss: 0.0001171350188087672
    INFO:root:Generator loss: 1.0478502482175827, Discriminator loss: 7.005644611126626e-05
    INFO:root:Generator loss: 1.0798900127410889, Discriminator loss: 0.0012122564669880375
    INFO:root:Generator loss: 1.041588193178177, Discriminator loss: 0.0036577262269929635
    INFO:root:Generator loss: 1.074593186378479, Discriminator loss: 0.0002621836891194107
    INFO:root:Generator loss: 1.0486982107162475, Discriminator loss: 6.42522727503092e-05
    INFO:root:Generator loss: 1.0700945883989335, Discriminator loss: 0.00033098831299867016
    INFO:root:Generator loss: 1.0645505845546723, Discriminator loss: 5.4103344064060364e-05
    INFO:root:Generator loss: 1.074211984872818, Discriminator loss: 0.00010944717705569928
    INFO:root:Generator loss: 1.072346466779709, Discriminator loss: 0.00018734835957729957
    INFO:root:Generator loss: 1.0560636162757873, Discriminator loss: 0.00010278059180564014
    INFO:root:Generator loss: 1.0399885863065719, Discriminator loss: 0.0001253332316991873
    INFO:root:Generator loss: 1.0597063571214675, Discriminator loss: 0.0001746055782859912
    INFO:root:Generator loss: 1.0671822249889373, Discriminator loss: 0.00010207884170085891
    INFO:root:Generator loss: 1.0756561845541, Discriminator loss: 0.00012279253478482134
    INFO:root:Generator loss: 1.0512960582971573, Discriminator loss: 0.00010804541416291613
    INFO:root:Generator loss: 1.0466693550348283, Discriminator loss: 0.0006358093021844979
    INFO:root:Generator loss: 1.0753205329179765, Discriminator loss: 0.005824737032526173
    INFO:root:Generator loss: 1.0676013618707656, Discriminator loss: 0.0008540094800991938
    INFO:root:Generator loss: 1.0410430133342743, Discriminator loss: 0.00013016909961152123
    INFO:root:Generator loss: 1.0918779402971268, Discriminator loss: 0.0001956570455149631
    INFO:root:Generator loss: 1.0473725110292436, Discriminator loss: 9.093053740798496e-05

Evaluation:

    pesq:  1.0587524145841598 csig:  1.0777227792749267 cbak:  1.418621684416482 covl:  1.0125614981105242 ssnr:  -1.4984374963315985 stoi:  0.1859480103555091

Training on pretrained model from authors:

tba
Evaluation:

tba

Pretrained model from authors:

Evaluation:

    pesq:  1.2303554445505143 csig:  1.412312253735375 cbak:  1.4103906610004537 covl:  1.3146698547489466 ssnr:  -2.0189492452763718 stoi:  0.2451594971056267


Fine-tuning on pretrained model from authors:

    
    INFO:root:Generator loss: 0.9803555607795715, Discriminator loss: 0.004497478474513627
    INFO:root:Generator loss: 0.9839551508426666, Discriminator loss: 0.0002254387409038827
    INFO:root:Generator loss: 1.0049857378005982, Discriminator loss: 0.00017971180259337415
    INFO:root:Generator loss: 0.9877994626760482, Discriminator loss: 0.0001390831252138014
    INFO:root:Generator loss: 0.9810490518808365, Discriminator loss: 0.0002643458637066942


Evaluation:

    
    pesq:  1.0351979941129685 csig:  1.152096069765623 cbak:  1.4057466341602713 covl:  1.054459746950025 ssnr:  -1.8605812995926392 stoi:  0.2338759234258574



**Current state:**
1. Successfully processed sample data with pretrained model for comparison.
2. Successfully preprocessed custom training and evaluation data.


**TODO:**
Compare results.
Create report.
