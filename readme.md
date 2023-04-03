# Start from Alpaca

Novices also want to join the bandwagon of building LLMs !

Start from Organizing and assembling the Existing repository, and then try to add something new !!


## Source

### CheckPoints：

- [LLaMA](https://huggingface.co/decapoda-research)：The original Weights

- [Alpaca-native](https://huggingface.co/chavinlo/alpaca-native)： Using the origin code from  Stanford-Alpaca without lora

- [tloen/alpaca-lora-7b](https://huggingface.co/tloen/alpaca-lora-7b): the original 7B Alpaca-LoRA checkpoint by tloen

- [chansung/alpaca-lora-13b](https://huggingface.co/chansung/alpaca-lora-13b): the 13B Alpaca-LoRA checkpoint by changsung with the same script to tune the original 7B model

- [chansung/alpaca-lora-30b](https://huggingface.co/chansung/alpaca-lora-30b): the 30B Alpaca-LoRA checkpoint by chansung with the same script to tune the original 7B model

- 中文LLaMA模型在原版的基础上扩充了中文词表，使用了中文纯文本数据进行二次预训练，具体见[训练细节](https://github.com/ymcui/Chinese-LLaMA-Alpaca#训练细节)一节。
  **注意：如希望体验类ChatGPT对话交互，请使用Alpaca模型，而不是LLaMA模型。**

  | 模型名称           | 类型     | 重构所需模型     | 大小[2] | LoRA下载地址                                                 | SHA256[3]          |
  | ------------------ | -------- | ---------------- | ------- | ------------------------------------------------------------ | ------------------ |
  | Chinese-LLaMA-7B   | 通用     | 原版LLaMA-7B[1]  | 770M    | [[百度网盘\]](https://pan.baidu.com/s/1oORTdpr2TvlkxjpyWtb5Sw?pwd=33hb) [[Google Drive\]](https://drive.google.com/file/d/1iQp9T-BHjBjIrFWXq_kIm_cyNmpvv5WN/view?usp=sharing) [[HuggingFace\]](https://huggingface.co/ziqingyang/chinese-llama-lora-7b) | 39b86b......fe0e60 |
  | Chinese-LLaMA-13B  | 通用     | 原版LLaMA-13B[1] | ⏳       | ⏳                                                            | ⏳                  |
  | Chinese-Alpaca-7B  | 指令精调 | 原版LLaMA-7B[1]  | 790M    | [[百度网盘\]](https://pan.baidu.com/s/1xV1UXjh1EPrPtXg6WyG7XQ?pwd=923e) [[Google Drive\]](https://drive.google.com/file/d/1JvFhBpekYiueWiUL3AF1TtaWDb3clY5D/view?usp=sharing) [[HuggingFace\]](https://huggingface.co/ziqingyang/chinese-alpaca-lora-7b) | 9bb5b6......ce2d87 |
  | Chinese-Alpaca-13B | 指令精调 | 原版LLaMA-13B[1] | ⏳       | ⏳                                                            | ⏳                  |
  
- Various adapter weights (download at own risk):
  
  - 7B:
    - https://huggingface.co/tloen/alpaca-lora-7b
    - https://huggingface.co/samwit/alpaca7B-lora
    - 🇧🇷 https://huggingface.co/22h/cabrita-lora-v0-1
    - 🇨🇳 https://huggingface.co/qychen/luotuo-lora-7b-0.1
    - 🇯🇵 https://huggingface.co/kunishou/Japanese-Alapaca-LoRA-7b-v0
    - 🇫🇷 https://huggingface.co/bofenghuang/vigogne-lora-7b
    - 🇹🇭 https://huggingface.co/Thaweewat/thai-buffala-lora-7b-v0-1
    - 🇩🇪 https://huggingface.co/thisserand/alpaca_lora_german
    - 🇮🇹 https://huggingface.co/teelinsan/camoscio-7b-llama
    - 🇷🇺 https://huggingface.co/IlyaGusev/llama_7b_ru_turbo_alpaca_lora
  - 13B:
    - https://huggingface.co/chansung/alpaca-lora-13b
    - https://huggingface.co/mattreid/alpaca-lora-13b
    - https://huggingface.co/samwit/alpaca13B-lora
    - 🇯🇵 https://huggingface.co/kunishou/Japanese-Alapaca-LoRA-13b-v0
    - 🇰🇷 https://huggingface.co/chansung/koalpaca-lora-13b
    - 🇨🇳 https://huggingface.co/facat/alpaca-lora-cn-13b
    - 🇪🇸 https://huggingface.co/plncmm/guanaco-lora-13b
  - 30B:
    - https://huggingface.co/baseten/alpaca-30b
    - https://huggingface.co/chansung/alpaca-lora-30b
    - 🇯🇵 https://huggingface.co/kunishou/Japanese-Alapaca-LoRA-30b-v0



### Building the model:

[Stanford_alpaca](https://github.com/tatsu-lab/stanford_alpaca)

【The :one:first popular player using the LLaMA】This is the repo for the Stanford Alpaca project, which aims to build and share an instruction-following LLaMA model. The repo contains:

- The [52K data](https://github.com/tatsu-lab/stanford_alpaca#data-release) used for fine-tuning the model.
- The code for [generating the data](https://github.com/tatsu-lab/stanford_alpaca#data-generation-process).
- The code for [fine-tuning the model](https://github.com/tatsu-lab/stanford_alpaca#fine-tuning).



[Alpaca-lora](https://github.com/tloen/alpaca-lora)

This repository contains code for reproducing the [Stanford Alpaca](https://github.com/tatsu-lab/stanford_alpaca) results using [low-rank adaptation (LoRA)](https://arxiv.org/pdf/2106.09685.pdf). We provide an Instruct model of similar quality to `text-davinci-003` that can run [on a Raspberry Pi](https://twitter.com/miolini/status/1634982361757790209) (for research), and the code is easily extended to the `13b`, `30b`, and `65b` models.

In addition to the training code, which runs within hours on a single RTX 4090, we publish a script for downloading and inference on the foundation model and LoRA, as well as the resulting [LoRA weights themselves](https://huggingface.co/tloen/alpaca-lora-7b/tree/main). To fine-tune cheaply and efficiently, we use Hugging Face's [PEFT](https://github.com/huggingface/peft) as well as Tim Dettmers' [bitsandbytes](https://github.com/TimDettmers/bitsandbytes).

Without hyperparameter tuning, the LoRA model produces outputs comparable to the Stanford Alpaca model. (Please see the outputs included below.) Further tuning might be able to achieve better performance



[BELLE: Be Everyone's Large Language model Engine](https://github.com/LianjiaTech/BELLE)

项目包含以下内容:

项目包含以下内容:

- ![Docs](https://camo.githubusercontent.com/891a55bda5f44b5da6bb2a00163b7155fac2bd60154f59accc244b6c31783316/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f254538254145254144254537254242253833254534254242254133254537254130253831747261696e2d626c7565)

  - 详见[BELLE/train](https://github.com/LianjiaTech/BELLE/tree/main/train)，尽可能简化的一个训练代码实现，支持finetune，lora，deepspeed

- ![Docs](https://camo.githubusercontent.com/411b860c93c9780ebbc8e876d0fea0f0fb9aeeb8e94c8bab8f850b28a2a3dab2/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f254536253935254230254536253844254145254535254243253830254536253934254245312e354d2d626c7565)

   

  ![Docs](https://camo.githubusercontent.com/8a9ab3975a7baa6652c8618f95ed2fec580b07ba80ac11db1973050d52be8cf8/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f25453625393525423025453625384425414525453525424325383025453625393425424531304d2d626c7565)

  - 详见[BELLE/1.5M](https://github.com/LianjiaTech/BELLE/tree/main/1.5M)，参考[Stanford Alpaca](https://github.com/tatsu-lab/stanford_alpaca) 生成的中文数据集[1M](https://huggingface.co/datasets/BelleGroup/train_1M_CN) + [0.5M](https://huggingface.co/datasets/BelleGroup/train_0.5M_CN)；
  - 持续开放的数据集，详见[BELLE/10M](https://github.com/LianjiaTech/BELLE/tree/main/10M)，目前开放了[0.25M数学指令数据集](https://huggingface.co/datasets/BelleGroup/school_math_0.25M)和[0.8M多轮任务对话数据集](https://huggingface.co/datasets/BelleGroup/multiturn_chat_0.8M)

- ![Docs](https://camo.githubusercontent.com/6baec3b647d7b89723332b80b62bef1e303ef430e41f75b0c977c72032288903/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f2545362541382541312545352539452538422d626c7565)

  - 基于BLOOMZ-7B1-mt优化后的模型：[BELLE-7B-0.2M](https://huggingface.co/BelleGroup/BELLE-7B-0.2M)，[BELLE-7B-0.6M](https://huggingface.co/BelleGroup/BELLE-7B-0.6M)，[BELLE-7B-1M](https://huggingface.co/BelleGroup/BELLE-7B-1M)，[BELLE-7B-2M](https://huggingface.co/BelleGroup/BELLE-7B-2M)
  - 基于[huggingface的LLaMA实例](https://huggingface.co/decapoda-research)实现[调优的模型](https://huggingface.co/BelleGroup)：[BELLE-LLAMA-13B-2M](https://huggingface.co/BelleGroup/BELLE-LLAMA-13B-2M)，[BELLE-LLAMA-7B-2M](https://huggingface.co/BelleGroup/BELLE-LLAMA-7B-2M)，[BELLE-LLAMA-7B-0.6M](https://huggingface.co/BelleGroup/BELLE-LLAMA-7B-0.6M)。请注意，本项目不能保证其是原版的LLaMA模型，也不能保证调优后的模型和LLaMA原版模型之间的关系。请参考[Meta LLaMA的License](https://github.com/facebookresearch/llama/blob/main/LICENSE)和[huggingface的LLaMA实例的License](https://huggingface.co/decapoda-research/llama-7b-hf/blob/main/LICENSE)，目前仅供学习交流。请严遵守LLaMA的使用限制。强烈建议大家基于训练脚本和开放数据调优模型。

- ![Docs](https://camo.githubusercontent.com/18346c77c508307e601aa65b46ad01f2435bb015b1291b6083feb313d678300f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f254536254138254131254535253945253842254539253837253846254535253843253936677074712d626c7565)

  - 详见[BELLE/gptq](https://github.com/LianjiaTech/BELLE/tree/main/gptq)，参考gptq的实现，对本项目中相关模型进行了量化



**[Chinese-LLaMA-Alpaca](https://github.com/ymcui/Chinese-LLaMA-Alpaca)**

本项目开源了**中文LLaMA模型和经过指令精调的Alpaca大模型**。这些模型**在原版LLaMA的基础上扩充了中文词表**并使用了中文数据进行二次预训练，进一步提升了中文基础语义理解能力。同时，在中文LLaMA的基础上，本项目使用了中文指令数据进行指令精调，显著提升了模型对指令的理解和执行能力。

**主要内容：**

🚀 开源了经过中文文本数据预训练的中文LLaMA大模型

🚀 开源了进一步经过指令精调的中文Alpaca大模型

🚀 快速地使用笔记本电脑（个人PC）本地部署和体验量化版大模型



**[llama.cpp](https://github.com/ggerganov/llama.cpp)**

Inference of [LLaMA](https://arxiv.org/abs/2302.13971) model in pure C/C++ :weary:

The main goal is to run the model using 4-bit quantization on a MacBook(also supports Windows)

- Plain C/C++ implementation without dependencies
- Apple silicon first-class citizen - optimized via ARM NEON and Accelerate framework
- AVX2 support for x86 architectures
- Mixed F16 / F32 precision
- 4-bit quantization support
- Runs on the CPU



###  Data && Deployment

**[AlpacaDataCleaned](https://github.com/gururise/AlpacaDataCleaned)**

This repository hosts a cleaned and curated version of a dataset used to train the Alpaca LLM (Large Language Model). The original dataset had several issues that are addressed in this cleaned version.



[Alpaca-LoRA-Serve](https://github.com/deep-diver/Alpaca-LoRA-Serve)

Alpaca-LoRA as a Chatbot Service

<img src="https://cdn.jsdelivr.net/gh/Darren-greenhand/Darren-greenhand-image@main/img/202304011729858.png" alt="img" style="zoom: 19%;" />



**[Alpaca.cpp](https://github.com/antimatter15/alpaca.cpp)**

Run a fast ChatGPT-like model locally on your device.

Based on the [Alpaca-lora](https://github.com/tloen/alpaca-lora) and the horiible [llama.cpp](https://github.com/ggerganov/llama.cpp) but  add a **chat interface**.





## 免责声明

本项目相关资源仅供学术研究之用，严禁用于商业用途。使用涉及第三方代码的部分时，请严格遵循相应的开源协议。模型生成的内容受模型计算、随机性和量化精度损失等因素影响，本项目无法对其准确性作出保证。对于模型输出的任何内容，本项目不承担任何法律责任，亦不对因使用相关资源和输出结果而可能产生的任何损失承担责任。

本项目由个人及协作者业余时间发起并维护，因此无法保证能及时回复解决相应问题。
