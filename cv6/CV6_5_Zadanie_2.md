## Zadanie 2 (5b)

V tomto zadaní budete pracovať s aplikáciou v adresári `machine_learning` a datasetom: **Breast Cancer Wisconsin (Diagnostic)**

Dataset je dostupný aj online samostatne, alebo v knižnici scikit-learn: 
https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic
https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html

Dataset Breast Cancer Wisconsin (Diagnostic) obsahuje údaje získané z digitalizovaných obrazov tenkých ihlových aspirátov (FNA) hmoty prsníka, ktoré opisujú charakteristiky jadier buniek v nich. Zahŕňa 569 prípadov s 30 vlastnosťami, s cieľom na klasifikáciu benigných alebo maligných prípadov rakoviny prsníka na základe rôznych vlastností jadier buniek. Viac informácií nájdete na UCI Machine Learning Repository. [1]

### Úloha 1 (1b)

Pridajte do kódu ďalší model strojového učenia (ľubovoľný), a taktiež definujte parametre a ich hodnoty pre Grid Search.

**Uveďte aký ML model a hodnoty jeho parametrov ste použili:**

Za ďalší model strojového učenia som zvolil Random Forest, kde počiatočný seed som nastavil na hodnotu 42.

Parametre pre grid search:

- počet stromov v lese (n_estimators): [100, 200, 300]
    
- maximálna hĺbka stromu (max_depth): [None, 10] (None - stromy rastú, až do kým nie su listy čisté)
    
- minimálny počet vzoriek na rozdelenie uzla (min_samples_split): [2, 5]
    
- minimálny počet vzoriek v listovom uzle (min_samples_leaf): [1, 2]
    
- maximálny počet vlastností (max_features): ['sqrt', 'log2']


### Úloha 2 (2b)

Implementujte ďalšiu (ľubovoľnú) metriku pre evaluáciu modelov. Nezabudnite na to, aby sa implementovaná metrika ukladala do logov v súbore `model_accuracies.csv` a tiež ju pridajte do grafov (do grafov pre funkciu hustoty rozdelenia a tiež pre ňu vytvorte nový graf ktorý bude zobrazovať jej priebeh počas replikácií - tak ako pre presnosť (accuracy)).  

**Uveďte akú metriku ste doplnili:**

Ako ďalšiu metriku pre evaluáciu modelov som použil Precision.

Precision = TP / (TP + FP) (napr. koľko z predikovaných chorých, bolo skutočne chorých)

### Úloha 3 (1b)

Do implementácie pridajte ukladanie všetkých grafov, ktoré sa vytvárajú pri behu skriptu `main.py`` v adresári `machine_learning`.

### Úloha 4 (1b)

**V skripte `main.py`** nastavte počet replikácií na vyššie číslo (rozumne, podľa vlastného uváženia). Vykonajte beh aplikácie s Vašou implementáciou. Po skončení behu zanalyzujte vygenerované grafy a pár vetami popíšte ich interpretáciu. (Napr. v čom je ktorý ML model lepší, a pod.)

Confusion matrix:
    
- Logistická regresia má menej chýb (4.4 a 2.9) v porovnaní s Random Forest (5.4 a 6.07)

Accuracy per replication:

- Oba modely si vedú viac menej podobne (LR: 0.97, RF: 0.96)
- LR je o čosi stabilnejšia

Precision per replication:

- LR má vyššiu priemernú precíznosť (0.97) s menšími výkyvmi v porovnaní s RF (0.96)

Density precision: 

- LR dosahuje vyššiu precíznosť

Density accuracy:

- LR má väčšiu presnosť (sústredenú okolo 0.97)

Density ROC_AUC:

- LR má o niečo vyššie skóre ako RF

Density F1 score:

- LR má vyššie F1 skóre ako RF


#### LR je presnejšia a viac spoľahlivejšia v porovnaní s RF.


**Odovzdávanie riešenia:** Ako súčasť riešenia zahrňte okrem odpovedí na otázky aj skripty s Vašou implementáciou, vygenerované logy a grafy (všetko môžete dať na Github).

----

#### Referencie

[1] Street, W. N., Wolberg, W. H., & Mangasarian, O. L. (1993). Nuclear feature extraction for breast tumor diagnosis. Electronic Imaging, 1905, 861–870. https://doi.org/10.1117/12.148698
