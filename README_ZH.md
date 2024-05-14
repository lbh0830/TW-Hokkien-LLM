# 台灣閩南語大型語言模型 Taiwanese Hokkien (Taigi) LLMs

[**中文**](./README_ZH.md) | [**Hokkien Han**](./README_HAN.md) | [**English**](./README.md) | 🤗 <a href="https://huggingface.co/collections/Bohanlu/taiwanese-hokkien-llm-6614ba7456e6789bc2f10ca0" target="_blank">Model Collection</a> | 📜 <a href="https://arxiv.org/abs/2403.12024" target="_blank">Paper</a>
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

## 介紹

這個專案是基於繁體中文的 LLaMA-2 模型開發。我們使用 78MB 的台灣閩南語單語語料，包括白話字（POJ）、漢羅（Hanlo）和漢字書寫系統，進行繼續預訓練，產生台灣閩南語版本的 LLaMA-2 語言模型，**Taigi-Llama-2**。接著，我們基於 **Taigi-Llama-2** 訓練了一個台語對中英文以及台語不同文字系統間的翻譯模型，使用收集的平行資料集得到 **Taigi-Llama-2-Translator**。最後，使用這個翻譯器，我們可以從中文版本的指令精調資料集生成相對應的台灣閩南語漢字版本，我們通過在台灣閩南語漢字資料集上進行指令精調，獲得了 **Taigi-Llama-2-Chat**。

## 進行中

- [ ] **Taigi-Llama-2-Chat 7B / 13B Model**: 我們目前正在利用 Taigi-Llama-2-Translator 生成數據集，以訓練對話模型。該模型將在不久的將來發布。

## 提示模板
### Taigi-Llama-2-Translator
```
[TRANS]\n{source_sentence}\n[/TRANS]\n[{target_language}]\n
```
- `source_sentence`: 希望翻譯的句子。
- `target_language`: 希望翻譯成的目標語言。使用 "ZH" 表示繁體中文，"EN" 表示英文，"POJ" 表示台灣閩南語白話字，"HL" 表示台灣閩南語漢羅，"HAN" 表示台灣閩南語漢字。

## 模型下載

| 名稱 | 描述 | 類型 | 連結 |
| :--- | :---| :--- | :--- |
| Taigi-Llama-2-7B | 使用台灣閩南語語料對繁體中文 Llama2 模型繼續預訓練。 | Base Model | [🤗 Bohanlu/Taigi-Llama-2-7B](https://huggingface.co/Bohanlu/Taigi-Llama-2-7B) |
| Taigi-Llama-2-13B | 使用台灣閩南語語料對繁體中文 Llama2 模型繼續預訓練。 | Base Model | [🤗 Bohanlu/Taigi-Llama-2-13B](https://huggingface.co/Bohanlu/Taigi-Llama-2-13B) | 
| Taigi-Llama-2-Translator-7B | 使用台灣閩南語、中文和英文的平行數據對 Taigi-Llama-2 進行微調。 | Translation Model | [🤗 Bohanlu/Taigi-Llama-2-Translator-7B](https://huggingface.co/Bohanlu/Taigi-Llama-2-Translator-7B) |
| Taigi-Llama-2-Translator-13B | 使用台灣閩南語、中文和英文的平行數據對 Taigi-Llama-2 進行微調 | Translation Model | [🤗 Bohanlu/Taigi-Llama-2-Translator-13B](https://huggingface.co/Bohanlu/Taigi-Llama-2-Translator-13B) |
| Taigi-Llama-2-Chat-7B | 利用台灣閩南語漢字指令精調資料集對 Taigi-Llama-2 進行精調。 | Chat Model | [🔨 Coming Soon](#) |
| Taigi-Llama-2-Chat-13B | 利用台灣閩南語漢字指令精調資料集對 Taigi-Llama-2 進行精調。 | Chat Model | [🔨 Coming Soon](#) |
| iCorpus-100 | 用於評估台灣閩南語翻譯模型性能的平行數據集。 | Dataset | [🤗 Bohanlu/iCorpus-100](https://huggingface.co/Bohanlu/iCorpus-100) |


## Taigi-Llama-2-Translator 在 iCorpus-100 上的翻譯表現
使用貪婪解碼，將波束大小設置為 1，重複懲罰設置為 1.1，Taigi-Llama-2-Translator 在 iCorpus-100 上的表現如下：

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

## 引用
如果您使用了這個存儲庫中的資源，請引用以下文獻：

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