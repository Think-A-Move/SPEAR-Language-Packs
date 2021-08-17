# SPEAR-Language-Packs-staging
Language Packs for SPEAR-ASR and SPEAR-WakeUp are general-purpose language models that can be used for transcriptions, dictations and conversational AI. 

If you need:
- to extend the existing language models
- other spoken languages such as Spanish
- domain specific language models such as for Medics
- limited vocabulary language models for Command and Control

contact us at info@think-a-move.com.

For each Language, we provide a data folder and a model folder separately. 

## Data Folder
Each data folder should have two sub folders named as `SPEAR-ASR` and `SPEAR-WakeUp`. The content of these subfolders will be used to initialize `SpearSdkApi`.
When using android API, you can put the data folder on any phone HDD and call the following codes to create `SpearSdkApi`, where `LM_Package` is the absolute path of the data folder.

```java
spearSdkApi = SpearSdkApi.getInstance();
spearSdkApi.initialize(getApplicationContext(), LM_Package);
```

## Model Folder
The model folder holds several fsts, some of which are used to define tasks for SPEAR-ASR, some of which are used to define tasks for SPEAR-WakeUp.

### SPEAR-ASR
When using android API, you can put the corresponding fst on any phone HDD and call the following codes to create `SpeechRecognizer`, where `example.fst` needs to be replaced with the absolute path of the fst.

```java
speechRecognizer = spearSdkApi.createSpeechRecognizer();
speechRecognizer.setFstGrammar("example.fst", true);
```

### SPEAR-WakeUp
When using android API, you can put the corresponding fst on any phone HDD and call the following codes to create `SpearWakeUp`, where `WAKEUP_FST` needs to be replaced with the absolute path of the fst.

```java
spearWakeUp = spearSdkApi.createSpearWakeUp();
spearWakeUp.initWithFst(WAKEUP_FST);
```

