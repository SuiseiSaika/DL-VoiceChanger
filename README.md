# DL-VoiceChanger #
## Introduction ##
我們的目標是將一個人的聲音轉換成另一個人的聲音，希望透過訓練出來的模型，在輸入來源音訊 S 後，可以輸出成目標音訊 T。
首先，我們會將很一段或多段.wav音訊檔透過 [WORLD Vocoder](https://github.com/JeremyCCHsu/Python-Wrapper-for-World-Vocoder) 擷取特徵後轉換成神經網路可以學習的資料型態 tensor，並且參考 [CycleGAN](https://junyanz.github.io/CycleGAN/) 這個對抗式生成模型架構做訓練，分別選擇 [U-Net](https://lmb.informatik.uni-freiburg.de/people/ronneber/u-net/) generator 和 Patched discriminator([CycleGAN VC2](http://www.kecl.ntt.co.jp/people/kaneko.takuhiro/projects/cyclegan-vc2/index.html)) 做為我們的生成器和鑑別器。

## Experiment ##
為了達成我們的目標，我們進行了多次實驗，以下是我們的實驗內容：
* __One-shot learning__ :
在這個實驗當中我們只在來源資料集T與目標資料集S當中選擇一筆資料作為訓練資料。
  * 初始設定 :
    * RMSprop as generator's optimizer, and SGD as discriminator's optimizer. Initial learning rate = 5e-5.
    * Losses :　Two-Step Adversarial Losses(MSE), Cycle-consistency loss(MAE), Identity-mapping loss(MAE).
  * The "G only" Phase :
    * 在這個階段，我們只訓練 Generator。
  * The "Loss change" Phase :
    * 這個階段中的 Two-Step Adversarial Losses 改使用 Binary cross entropy(BCE)。
  * 
    * 簡報製作
    * 資料蒐集
* __一般訓練__ :
在這個實驗當中我們使用來源資料集T與目標資料集S中的所有資料作為訓練資料。
  * 初始設定
    * RMSprop as generator's optimizer, and SGD as discriminator's optimizer. Initial learning rate = 5e-5.
    * Losses :　Two-Step Adversarial Losses(MSE), Cycle-consistency loss(MAE), Identity-mapping loss(MAE).
## Train Model
在這個實驗當中我們只在來源資料集T與目標資料集S當中選擇一筆資料作為訓練資料。
  * 初始設定 :
    * RMSprop as generator's optimizer, and SGD as discriminator's optimizer. Initial learning rate = 5e-5.
    * Losses :　Two-Step Adversarial Losses(BCE), Cycle-consistency loss(MSE), Identity-mapping loss(MSE).  

## Reference
*
*
*
*
*
*
## Authors
* National Chengchi University, NCCU
  * 資管四 105306088 陳昌碩
    * 建立模型
    * 實驗設計與進行
    * 資料蒐集
  * 資管四 105306002 林貞妮
    * 文獻探討與驗證
  * 廣告四 105405073 陳筑均
    * 報告
    * 資料蒐集
  * 資管一 108306036 羅永富
    * 簡報製作
    * 資料蒐集
