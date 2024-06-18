# VTP LPD (12. grupa)
**Autori:**  
Haralds Upītis (hu21001),  
Paulis Kristofers Siks (ps21049)

## Izvēlētā tēma, tās saistība ar valodu tehnoloģijām (0-2 punkti)
### Izvēlētā tēma:
**Loģikas "kļūdu" noteikšana​**

### Saistība ar valodu tehnoloģijām
Izvēlētā tēma ir fundamentāli saistīta ar valodu tehnoloģijām un valodniecību, jo ievade ir jebkāds cilvēkam lasāms teksts angļu valodā, un mērķis ir klasificēt teikumā esošo loģisko kļūdu.

## Īss pārskats par jomā paveikto, jaunākie sasniegumi (0-2 punkti)
### Aktuālie dokumenti:
https://arxiv.org/pdf/2202.13758 <-- Dokuments, kuru izmantojām par pamatu mūsu risinājumam.  
https://arxiv.org/pdf/2301.11879  
https://arxiv.org/pdf/2405.02318  

Visos dokumentos izmantojot zero-shot klasifikatorus, bez fine-tuning, rezultāti modeļiem ir ~≤30%, ar fine-tuning ~≤70%.
Izmantojot few-shot klasifikatorus, ar fine-tuning rezultāti ir daudz labāki, pat ~≥90%.

## Prototips: demonstrācija, novērtēšana, datu un koda pieejamība (0-4 punkti)
### Process
Kopā izmantojām 13 loģisko kļūdu marķējumus (labels), kuri apskatāmi 'Data/mappings.json' failā:
```json
{
    "ad hominem": "[MSK1] is claiming [MSK2]. [MSK1] is a moron. Therefore, [MSK2] is not true.",
    "ad populum": "A lot of people believe [MSK1]. Therefore, [MSK1] must be true.",
    "appeal to emotion": "[MSK1] is made without evidence. In place of evidence, emotion is used to convince the interlocutor that [MSK1] is true.",
    "circular reasoning": "[MSK1] is true because of [MSK2]. [MSK2] is true because of [MSK1].",
    "equivocation": "[MSK1] is used to mean [MSK2] in the premise. [MSK1] is used to mean [MSK3] in the conclusion.",
    "fallacy of credibility": "[MSK1] claims that [MSK2]. [MSK1] are experts in the field concerning [MSK2]. Therefore, [MSK2] should be believed.",
    "fallacy of extension": "[MSK1] makes claim [MSK2]. [MSK3] restates [MSK2] (in a distorted way). [MSK3] attacks the distorted version of [MSK2]. Therefore, [MSK2] is false.",
    "fallacy of logic": "If [MSK1] is true, then [MSK2] is true. [MSK2] is true. Therefore, [MSK1] is true.",
    "fallacy of relevance": "It is claimed that [MSK1] implies [MSK2], whereas [MSK1] is unrelated to [MSK2].",
    "false causality": "[MSK1] occurred, then [MSK2] occurred. Therefore, [MSK1] caused [MSK2].",
    "false dilemma": "Either [MSK1] or [MSK2] is true.",
    "faulty generalization": "[MSK1] has attribute [MSK2]. [MSK1] is a subset of [MSK3]. Therefore, all [MSK3] has attribute [MSK2].",
    "intentional": "[MSK1] knows [MSK2] is incorrect. [MSK1] still claim that [MSK2] is correct using an incorrect argument."
  }
```
Izmantotie ievades dati tika ņemti no [saite uz izmantoto datu kopu](https://github.com/tmakesense/logical-fallacy/blob/main/dataset-fixed/edu_all_fixed.csv). Tie ir pamatdokumenta dati, kuri ir pārveidoti un uzlaboti, labojot dažus oriģināldatu [(saite uz oriģināldatiem)](https://github.com/causalNLP/logical-fallacy/blob/main/data/edu_all.csv) defektus [(apraksts par labojumiem)](https://www.logical-fallacy.com/articles/dataset-review/).
### Izmantotās datu kopas piemērs
```csv
updated_label,original_url,old_label,source_article,explanations,rationale
faulty generalization,https://quizizz.com/admin/quiz/5f948dcbedafcd001e0c5506/logical-fallacies,hasty generalization,"""Annie must like Starbucks because all white girls like Starbucks.""",,
...
...
```
Tad ievades datu kopā `updated_label` kolonā esošās loģiskās kļūdas tiek aizstātas ar attiecīgo mapping.
### Mapped datu kopas piemērs
```
updated_label,original_url,old_label,source_article,explanations,rationale
"[MSK1] has attribute [MSK2]. [MSK1] is a subset of [MSK3]. Therefore, all [MSK3] has attribute [MSK2].","https://quizizz.com/admin/quiz/5f948dcbedafcd001e0c5506/logical-fallacies","hasty generalization","""Annie must like Starbucks because all white girls like Starbucks.""","",""
...
...
```
Tālāk visi kolonā `source_article` esošie teikumi tika aizmaskēti pēc zemāk redzāmās diagrammas principa.

### Mūsu rezultāti
...

## Prezentācija un atbildes uz jautājumiem (0-2 punkti)
### Links uz prezentāciju:
...
