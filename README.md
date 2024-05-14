# 台灣閩南語大型語言模型 Taiwanese Hokkien (Taigi) LLMs

[**中文**](./README_ZH.md) | [**台灣閩南語**](./README_HAN.md) | [**English**](./README.md) | 🤗 <a href="https://huggingface.co/collections/Bohanlu/taiwanese-hokkien-llm-6614ba7456e6789bc2f10ca0" target="_blank">Model Collection</a> | 📜 <a href="https://arxiv.org/abs/2403.12024" target="_blank">Paper</a>
<br>
<!-- <p align="center">
<img src="https://dummyimage.com/800x800/000/faf" width="100"> <br/>
</p> -->

<p align="center">
    <br>
        <img src="https://img.shields.io/badge/Code_License-MIT-blue"></a>
        <img src="https://img.shields.io/badge/Data%20License-CC%20By%20NC%204.0-red.svg"></a>
    <br/>
</p>

## Introduction

This project is based on Traditional Chinese LLaMA-2 models. We continued pre-training with 78MB of Taiwanese Hokkien monolingual corpora, which includes POJ, Hanlo, and Hanzi writing systems, to produce the Taiwanese Hokkien version LLaMA-2 base model, **Taigi-Llama-2**. We then trained a translation model based on **Taigi-Llama-2** using collected parallel datasets to obtain **Taigi-Llama-2-Translator**. Using this translator, we produced Taiwanese Hokkien Hanzi instruction fine-tuning datasets from the Mandarin Chinese version. Following this, we obtained **Taigi-Llama-2-Chat** by instruction fine-tuning on Taiwanese Hokkien Hanzi datasets.

## In Progress

- [ ] **Taigi-Llama-2-Chat 7B / 13B Model**: We are currently utilizing the Taigi-Llama-2-Translator to produce datasets for training the chat model. The model will be released in the near future.

## Prompt Template
### Taigi-Llama-2-Translator
```
[TRANS]\n{source_sentence}\n[/TRANS]\n[{target_language}]\n
```
- `source_sentence`: The sentence you want to translate.
- `target_language`: The target language you want to translate to. Use "ZH" for Mandarin Chinese, "EN" for English, "POJ" for Taiwanese Hokkien POJ, "HL" for Taiwanese Hokkien Hanlo, and "HAN" for Taiwanese Hokkien Hanzi.

## Download

| Name | Description | Type | Link |
| :--- | :---| :--- | :--- |
| Taigi-Llama-2-7B | Continued pre-training of a traditional Chinese Llama2 model using a Hokkien corpus. | 🦙 Base Model | [🤗 Bohanlu/Taigi-Llama-2-7B](https://huggingface.co/Bohanlu/Taigi-Llama-2-7B) |
| Taigi-Llama-2-13B | Continued pre-training of a traditional Chinese Llama2 model using a Hokkien corpus. | 🦙 Base Model | [🤗 Bohanlu/Taigi-Llama-2-13B](https://huggingface.co/Bohanlu/Taigi-Llama-2-13B) | 
| Taigi-Llama-2-Translator-7B | Fine-tuning Taigi-Llama-2 with parallel data in Taiwanese Hokkien, Mandarin Chinese, and English. | 🔁 Translation Model | [🤗 Bohanlu/Taigi-Llama-2-Translator-7B](https://huggingface.co/Bohanlu/Taigi-Llama-2-Translator-7B) |
| Taigi-Llama-2-Translator-13B | Fine-tuning Taigi-Llama-2 with parallel data in Taiwanese Hokkien, Mandarin Chinese, and English. | 🔁 Translation Model | [🤗 Bohanlu/Taigi-Llama-2-Translator-13B](https://huggingface.co/Bohanlu/Taigi-Llama-2-Translator-13B) |
| Taigi-Llama-2-Chat-7B | Fine-tuning Taigi-Llama-2 with Taiwanese Hokkien Hanzi instruction fine-tuning datasets. | 💬 Chat Model | [🔨 Coming Soon](#) |
| Taigi-Llama-2-Chat-13B | Fine-tuning Taigi-Llama-2 with Taiwanese Hokkien Hanzi instruction fine-tuning datasets. | 💬 Chat Model | [🔨 Coming Soon](#) |
| iCorpus-100 | A parallel dataset for evaluating the performance of Taiwanese Hokkien translation models. | 📃 Dataset | [🤗 Bohanlu/iCorpus-100](https://huggingface.co/datasets/Bohanlu/iCorpus-100) |


## Taigi-Llama-2-Translator Performance on iCorpus-100
Using greedy decoding with beam size set to 1 and repetition penalty to 1.1, the performance of Taigi-Llama-2-Translator on iCorpus-100 is as follows:

### Taigi-Llama-2-Translator-7B
<table>
  <tr>
    <th>Source Language</th>
    <th>Target Language</th>
    <th>BLEU</th>
    <th>chrF++</th>
    <th>GPT-4 Score</th>
    <th>GPT-4 Accuracy</th>
  </tr>
  <tr>
    <td rowspan="2">ZH</td>
    <td>HAN</td>
    <td>39.53</td>
    <td>39.72</td>
    <td>83.95</td>
    <td>81</td>
  </tr>
  <tr>
    <td>POJ</td>
    <td>1.13</td>
    <td>35.08</td>
    <td>67.70</td>
    <td>45</td>
  </tr>
  <tr>
    <td rowspan="2">EN</td>
    <td>HAN</td>
    <td>18.82</td>
    <td>23.13</td>
    <td>77.85</td>
    <td>70</td>
  </tr>
  <tr>
    <td>POJ</td>
    <td>0.35</td>
    <td>25.03</td>
    <td>50.25</td>
    <td>18</td>
  </tr>
  <tr>
    <td rowspan="3">HAN</td>
    <td>ZH</td>
    <td>53.99</td>
    <td>53.05</td>
    <td>85.55</td>
    <td>83</td>
  </tr>
  <tr>
    <td>EN</td>
    <td>22.72</td>
    <td>48.39</td>
    <td>74.60</td>
    <td>60</td>
  </tr>
  <tr>
    <td>POJ</td>
    <td>1.92</td>
    <td>46.52</td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td rowspan="3">POJ</td>
    <td>ZH</td>
    <td>47.08</td>
    <td>45.97</td>
    <td>65.65</td>
    <td>44</td>
  </tr>
  <tr>
    <td>EN</td>
    <td>14.35</td>
    <td>39.31</td>
    <td>49.95</td>
    <td>13</td>
  </tr>
  <tr>
    <td>HAN</td>
    <td>70.46</td>
    <td>70.18</td>
    <td>-</td>
    <td>-</td>
  </tr>
</table>



### Taigi-Llama-2-Translator-13B
<table>
  <tr>
    <th>Source Language</th>
    <th>Target Language</th>
    <th>BLEU</th>
    <th>chrF++</th>
    <th>GPT-4 Score</th>
    <th>GPT-4 Accuracy</th>
  </tr>
  <tr>
    <td rowspan="2">ZH</td>
    <td>HAN</td>
    <td>41.29</td>
    <td>41.15</td>
    <td>87.45</td>
    <td>89</td>
  </tr>
  <tr>
    <td>POJ</td>
    <td>0.93</td>
    <td>34.95</td>
    <td>70.35</td>
    <td>54</td>
  </tr>
  <tr>
    <td rowspan="2">EN</td>
    <td>HAN</td>
    <td>20.44</td>
    <td>24.66</td>
    <td>79.95</td>
    <td>70</td>
  </tr>
  <tr>
    <td>POJ</td>
    <td>0.43</td>
    <td>26.43</td>
    <td>58.60</td>
    <td>30</td>
  </tr>
  <tr>
    <td rowspan="3">HAN</td>
    <td>ZH</td>
    <td>53.50</td>
    <td>53.07</td>
    <td>88.40</td>
    <td>93</td>
  </tr>
  <tr>
    <td>EN</td>
    <td>26.81</td>
    <td>52.79</td>
    <td>80.10</td>
    <td>70</td>
  </tr>
  <tr>
    <td>POJ</td>
    <td>2.20</td>
    <td>49.15</td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr>
    <td rowspan="3">POJ</td>
    <td>ZH</td>
    <td>51.44</td>
    <td>49.87</td>
    <td>71.30</td>
    <td>47</td>
  </tr>
  <tr>
    <td>EN</td>
    <td>17.73</td>
    <td>44.03</td>
    <td>55.55</td>
    <td>27</td>
  </tr>
  <tr>
    <td>HAN</td>
    <td>73.33</td>
    <td>71.95</td>
    <td>-</td>
    <td>-</td>
  </tr>
</table>

## Citation
If you use the resources in this repository, please cite the following work:

```
@misc{lu2024enhancing,
      title={Enhancing Hokkien Dual Translation by Exploring and Standardizing of Four Writing Systems}, 
      author={Bo-Han Lu and Yi-Hsuan Lin and En-Shiun Annie Lee and Richard Tzong-Han Tsai},
      year={2024},
      eprint={2403.12024},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```
---