# 🌈 English to Latin Translator with T5

This repo creates an English to Latin translator model by finetuning a pretrained T5 model. This translator is then pushed to the huggingface hub, ready to be used by anyone interested. Pls see [the published model here](https://huggingface.co/MenaWANG/translator-en-la). 🥳 

## On the T5 Model 🤖

The T5 (Text-To-Text Transfer Transformer) model is a type of transformer-based neural network architecture developed by researchers at Google. It differs from previous transformer models like BERT or GPT in that it is designed to perform a wide range of NLP tasks using a unified text-to-text approach. In the T5 model, both inputs and outputs are represented as text strings, and the model is trained to convert one text string into another. This text-to-text framework allows T5 to excel at various tasks 😎 such as text classification, language translation,  summarization, and more, by framing each task as a text-to-text transformation.

## Github Codespaces 🌌

Fine-tuning the T5 model for the English to Latin translation task requires substantial computational resources. Therefore, I tried [Github Codespaces](https://docs.github.com/en/codespaces/overview) for the task. Github has offered GPU to some lucky *selected customers during a trial period* but unfortunately the only machine type I can choose at the moment is 2-core and 4-core (Why, my beloved Github, why??🥺). But here is [how to configure NVIDIA CUDA for codespaces](https://docs.github.com/en/codespaces/overview) for future. 🤞 

## Some lessons learned

This is the first time I tried to fine-tune a LLM. Below is some learning I wish I had known before I started

* The training of LLM takes a long time and creates large amount of files into your repo. So before kicking off the big run:
    * Add files that I don't want to be tracked to `.gitignore`
    * I will push the training code to the repo after initial testing and before the official run.
    * We may still encounter issues when pushing to git repo due to file size
        * use `git lfs`
        * or/and change git configuration to allow larger files ([discussions](https://stackoverflow.com/questions/2702731/git-fails-when-pushing-commit-to-github))
        * doulecheck remote URL with `git remote -v` if necessary
* Codespaces
    * env: My understanding is that by default we are operating in a virtual env, which could be a plus especially for collaboration.
    * autostop and idletime：My codespace stopped twice during the training, while my quota was far from the limit. While I believe training time shouldn't be considered as idle, but I increase the idletime anyway during the training [here](https://github.com/settings/codespaces).
    * speed: I used 4-core machine (fastest option available to me), and the speed is as fast as (if not slower than) running on my local. Much slower than running on google colab. For this repo that runs on github codespaces I revised the code to only run on 1/5 of the train data to shorten the training time.
    * git commit. I encountered some issue while doing git commit to this repo. This seems to be a rare event though, pls see [issue posted here for updates](https://github.com/orgs/community/discussions/114849).

## Useful links: 🔗

* Demo on huggingface: https://huggingface.co/docs/transformers/en/tasks/translation
* Dataset used for finetuning: https://huggingface.co/datasets/grosenthal/latin_english_parallel

Feel free to explore the repository, contribute improvements, or utilize the translator model for your NLP tasks. If you encounter any issues or have suggestions, don't hesitate to open an issue or pull request. Your feedback is greatly appreciated! 🥰