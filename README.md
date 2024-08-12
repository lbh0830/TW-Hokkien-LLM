# 台灣閩南語大型語言模型 Taiwanese Hokkien (Taigi) LLMs

[**中文**](./README_ZH.md) | [**台灣閩南語**](./README_HAN.md) | [**English**](./README.md) | 🤗 <a href="https://huggingface.co/collections/Bohanlu/taiwanese-hokkien-llm-6614ba7456e6789bc2f10ca0" target="_blank">Model Collection</a> | 📜 <a href="https://arxiv.org/abs/2403.12024" target="_blank">Paper</a>

<p align="center">
<img src="./pics/logo.jpg" width="450">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Code_License-MIT-blue"></a>
  <img src="https://img.shields.io/badge/Data%20License-CC%20By%20NC%204.0-red.svg"></a>
</p>

## Introduction

This project is based on Traditional Chinese LLaMA-2 models. We continued pre-training with 78MB of Taiwanese Hokkien monolingual corpora, which includes POJ, Hanlo, and Hanzi writing systems, to produce the Taiwanese Hokkien version LLaMA-2 base model, **Taigi-Llama-2**. We then trained a translation model based on **Taigi-Llama-2** using collected parallel datasets to obtain **Taigi-Llama-2-Translator**. Using this translator, we produced Taiwanese Hokkien Hanzi instruction fine-tuning datasets from the Mandarin Chinese version. Following this, we obtained **Taigi-Llama-2-Chat** by instruction fine-tuning on Taiwanese Hokkien Hanzi datasets.

## Prompt Template
### Taigi-Llama-2-Translator
```
{BOS}[TRANS]\n{source_sentence}\n[/TRANS]\n[{target_language}]\n
```
- `source_sentence`: The sentence you want to translate.
- `target_language`: The target language you want to translate to. Use "ZH" for Mandarin Chinese, "EN" for English, "POJ" for Taiwanese Hokkien POJ, "HL" for Taiwanese Hokkien Hanlo, and "HAN" for Taiwanese Hokkien Hanzi.
- For examples on how to use the models, please refer to [generation_sample_code.ipynb](./Notebook/generation_sample_code.ipynb).

### Taigi-Llama-2-Chat
```
{BOS}[INST] {user} [/INST]
```
- `user`: The user message you want to chat with the model.
- For examples on how to use the models, please refer to [generation_sample_code.ipynb](./Notebook/generation_sample_code.ipynb).

## Download

| Name | Description | Type | Link |
| :--- | :---| :--- | :--- |
| Taigi-Llama-2-7B | Continued pre-training of a traditional Chinese Llama2 model using a Hokkien corpus. | 🦙 Base Model | [🤗 Bohanlu/Taigi-Llama-2-7B](https://huggingface.co/Bohanlu/Taigi-Llama-2-7B) |
| Taigi-Llama-2-13B | Continued pre-training of a traditional Chinese Llama2 model using a Hokkien corpus. | 🦙 Base Model | [🤗 Bohanlu/Taigi-Llama-2-13B](https://huggingface.co/Bohanlu/Taigi-Llama-2-13B) | 
| Taigi-Llama-2-Translator-7B | Fine-tuning Taigi-Llama-2 with parallel data in Taiwanese Hokkien, Mandarin Chinese, and English. | 🔁 Translation Model | [🤗 Bohanlu/Taigi-Llama-2-Translator-7B](https://huggingface.co/Bohanlu/Taigi-Llama-2-Translator-7B) |
| Taigi-Llama-2-Translator-13B | Fine-tuning Taigi-Llama-2 with parallel data in Taiwanese Hokkien, Mandarin Chinese, and English. | 🔁 Translation Model | [🤗 Bohanlu/Taigi-Llama-2-Translator-13B](https://huggingface.co/Bohanlu/Taigi-Llama-2-Translator-13B) |
| Taigi-Llama-2-Chat-7B | Fine-tuning Taigi-Llama-2 with Taiwanese Hokkien Hanzi instruction fine-tuning datasets. | 💬 Chat Model | [🤗 Bohanlu/Taigi-Llama-2-Chat-7B](https://huggingface.co/Bohanlu/Taigi-Llama-2-Chat-7B) |
| Taigi-Llama-2-Chat-13B | Fine-tuning Taigi-Llama-2 with Taiwanese Hokkien Hanzi instruction fine-tuning datasets. | 💬 Chat Model | [🤗 Bohanlu/Taigi-Llama-2-Chat-13B](https://huggingface.co/Bohanlu/Taigi-Llama-2-Chat-13B) |
| iCorpus-100 | A parallel dataset for evaluating the performance of Taiwanese Hokkien translation models. | 📃 Dataset | [🤗 Bohanlu/iCorpus-100](https://huggingface.co/datasets/Bohanlu/iCorpus-100) |
| TAIDE-14-tasks-Hokkien | The Taiwanese Hokkien Hanzi dataset includes prompts for 14 distinct tasks | 📃 Dataset | [🤗 Bohanlu/TAIDE-14-tasks-Hokkien](https://huggingface.co/datasets/Bohanlu/TAIDE-14-tasks-Hokkien) |


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

## Examples for Taigi-Llama-2-Chat on TAIDE-14-tasks-Hokkien

| Prompt  | Taigi-Llama-2-Chat-7B | Taigi-Llama-2-Chat-13B |
|------------|------------|------------|
| 請分析下面這段話內底的心情，作者咧講著天氣變遷予地球造成的影響，𪜶敢有煩惱、受氣、傷悲抑是樂天的心情？請你共我解說一下。<br>氣候變遷對地球的影響是袂當無看見的。逐年，咱看著極端氣候的事件佇咧增加，冰山溶去造成海水面升懸，無數的生物當咧面臨滅種的危機。雖罔狀況真嚴重，毋過咱猶是有機會來改變這一切。透過減少溫室氣體的排放、栽培樹仔佮保護生態系統，咱會使為著地球的後代做出奉獻。 | 佇這个段落內底，作者表達出對氣候變遷的擔憂佮關心。伊描寫了氣候變遷帶來的影響，親像極端氣候事件增加、冰川溶去致使海平面上升，閣有真濟物種面對滅絕的威脅。遮的描寫攏顯露出來作者對氣候變遷的掛慮佮不安。<br>毋過，作者嘛強調講咱猶是會當做一寡代誌來改變這寡情形。伊建議咱減少溫室氣體的排放、種樹仔佮保護生態系統，按呢會當對地球的後代做出貢獻。遮的建議顯露出作者向望佮樂觀的態度，相信人類若做伙拍拚，就會當克服氣候變遷帶來的挑戰。<br>總講一句，作者的心情主要是憂愁佮向望相參。伊煩惱氣候變遷對地球佮生物造成傷害，毋過仝款嘛認為人類有才調改變現況，而且閣愛積極採取行動。這款心情反映出作者對環境的關心佮責任心，嘛顯露出伊向望未來的世界會變甲較好的期待。  | 佇這段話內底，作者的心情是積極佮樂天的。伊表達了氣候變遷對地球的影響是真實的閣嚴重的，毋過仝時嘛強調講這馬猶有機會通改變這一切。作者呼籲人著採取行動，親像減少溫室氣體的排放、種樹仔佮保護生態系統，來保護地球佮地球頂面的生物。這款積極的態度佮樂天的精神，顯露出作者佇面對氣候變遷的時，雖然知影狀況嚴峻，猶是充滿希望佮信心。 |
| 請生出一段佮醫學健康相關的對話，內面有牽涉著組織的資訊。對話應該會牽連著組織的功能、相關病症佮治療的方法。<br>阿明共𪜶老母問講人的一个組織，伊想欲知影肝臟的功能、可能會拄著的病症佮醫治的方法。𪜶老母是一个醫生，所以伊對遮的智識真熟似。𪜶的對話按呢寫： | 阿明：阿母，我聽人講肝是人身體上重要的器官之一，毋過我對肝的了解並袂濟。你敢會當共我講肝的功用佮可能會拄著的病症佮治療的方法？<br><br>老母：當然，肝臟是咱人體中真重要的器官之一。伊主要的功能包括：<br><br>1. 解毒：肝臟會當分解佮消除身軀內面的毒素，親像藥物、酒精佮有毒的化學物等等。<br>2. 營養代謝：肝臟負責共食物中的養份分解佮吸收，閣來參與脂肪、蛋白質佮醣類的新陳代謝。<br>3. 貯血：肝臟會當貯佮調節血液中ê油脂，閣會當調節血糖濃度。<br>4. 免疫功能：肝臟有免疫細胞，會當對抗感染佮發炎。<br><br>啊若肝病，肝病會分做兩類：<br><br>1. 急性肝病：像急性肝炎、肝中毒等等，通常是因為病毒、細菌抑是藥仔引起--的。<br>2. 慢性肝病：像肝硬化、肝癌等等，通常是因為長期喝酒、慢性肝炎、脂肪肝等等因素造成的。<br><br>啊若肝病的治療方法，會使分做下列幾款：<br><br>1. 藥物治療：針對無仝款的肝病，會使用無仝款的藥物來治療。比論講，對肝炎會使用抗病毒的藥仔；對肝硬化會使用保肝劑；對肝癌會使用化學療法、放射線療法等等。<br>2. 手術治療：對一寡肝病，親像肝腫瘤、肝囊腫等等，會當透過手術來治療。<br>3. 介入性治療：對一寡肝病，親像肝動脈栓塞術、肝臟移植等等，會當透過介入性治療來改善病情。<br><br>阿明：多謝你的解說，按呢我對肝臟的功能佮肝病的治療方式已經有較清楚矣。<br><br>老母：你嘛愛注意維持身體健康，避免食酒、食薰等等的歹習慣，定期做身體檢查，提早發現問題來治療。 | 阿明：阿母，我聽人講肝臟真重要，會當共咱的身軀內底的新陳代謝佮解毒的功能做甲好勢好勢。是按怎咧？<br>阿母：無毋著，肝臟是人體上大的器官之一，伊的主要功能就是新陳代謝佮解毒。新陳代謝就是共食入去的營養素轉化做身體需要的能量，嘛共食入去的毒素佮有害物質分解。解毒就是共血液中的毒素佮有害物質過濾掉，予伊袂入去身軀內。<br>阿明：是講肝臟是按怎會生出病來？<br>阿母：肝臟的病症包括肝炎、肝硬化、肝癌等等。肝炎是講肝臟發炎，肝硬化是講肝臟纖維化，肝癌是講肝臟生腫瘤。遮的病症的病因各無仝款，親像病毒感染、酒精中毒、肝硬化、遺傳因素等等。<br>阿明：是按怎會當治療肝病？<br>阿母：肝病的治療方法因為病情無仝，像肝炎會使用抗病毒的藥仔，肝硬化會使用保肝的藥仔，肝癌會使用手術、放射線治療、化學治療抑是標靶治療。另外，保持健康的生活方式，親像均衡飲食、適當的運動、避免啉酒等等，嘛會當幫贊保護肝臟。<br>阿明：若肝臟出問題，有啥物症頭？<br>阿母：肝病的症頭因為病情無仝，像肝炎可能會有厭𤺪、無胃口、黃疸、茶色尿等等的症頭。肝硬化的時陣可能會有腹肚疼、腰子疼、疲勞、體重減輕等等。肝癌的症頭嘛是百百款，親像腹肚漲疼、黃疸、茶色尿、體重減輕等等。<br>阿母：所以，保護肝臟真要緊。除了保持健康的生活方式以外，定期做身體檢查嘛真重要。若出現任何佮肝臟相關的症頭，著愛即時去病院看。<br>阿明：多謝阿母，我今仔日學著真濟有關肝臟的智識。 |
| 根據下跤用戶對電動車的評論，分析內底的情緒成份，閣共評論者滿意的程度評分（一到十），十分代表誠滿意，一分代表誠不滿意。<br>我最近買一台電動車，我對伊的設計佮環保性真有好感。雖罔充電站無遐爾仔好揣，毋過伊的續行力夠額予我做工課用矣。有時陣會煩惱揣袂著充電站，總是講起來，我對我的電動車感覺誠滿意。 | 評論者對電動車的評價主要是正面的，對設計佮環保性攏表示出肯定。雖然佇充電站方面有小可仔掛慮，毋過整體來講猶是感覺滿意。根據情緒分析，這个評論者對電動車的滿意度應該會使評做七分（誠滿意）。  | 這个評論者對電動車的滿意度是七分，主要是對電動車的設計佮環保性感覺滿意，毋過對充電站的便利性有淡薄仔掛慮。  |
| 請將下面的中文句仔翻做英文：「頭家咧發想創新的生理型態的時陣，愛考慮著市場的需求、佮競爭者的實力、閣有創新的策略等等濟濟項的因端。」  | When the boss is thinking about a new business model, he or she needs to consider many factors, such as market demand, competitor strength, and innovation strategies.  | When the boss is brainstorming innovative business types, he needs to consider market demand, competitor strength, and innovative strategies, among many other factors.  |
| 將下面這段有關地動的英文，請翻譯做閩南語。<br>Earthquakes are the result of sudden release of energy in the Earth's crust, leading to seismic waves. The intensity and magnitude of an earthquake can vary greatly depending on factors such as the depth of the focus and the distance from the epicenter. Earthquakes can cause significant damage to buildings, infrastructure, and even lead to loss of life. It is essential for governments and communities to invest in earthquake-resistant infrastructure and educate the public on how to respond during an earthquake.  | 地動是地球殼層雄雄放出能量，造成地動波。地動的強弱佮規模會因為震央佇佗位、離震源遠近無仝來改變。地動會予建築物、基礎建設佮性命害了了。政府佮社區愛投資佇防震的基礎建設，閣教示民眾按怎佇地動來的時陣有反應。  | 地動是地球殼內能量雄雄放出所引起的，致使地動波。地動的強弱佮規模會因為像震央深度佮離震央遠近等等因素，產生足大的精差。地動會嚴重破壞建築物、基礎建設，甚至造成性命的損失。政府佮社區愛投資佇抗震的基礎設施，嘛愛教育民眾按怎因應地動。 |

## Citation
If you use the resources in this repository, please cite the following work:

```
@misc{lu2024enhancing,
      title={Enhancing Taiwanese Hokkien Dual Translation by Exploring and Standardizing of Four Writing Systems}, 
      author={Bo-Han Lu and Yi-Hsuan Lin and En-Shiun Annie Lee and Richard Tzong-Han Tsai},
      year={2024},
      eprint={2403.12024},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```
---