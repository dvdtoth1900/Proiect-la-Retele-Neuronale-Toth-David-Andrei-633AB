# 📘 README – Etapa 3: Analiza și Pregătirea Setului de Date pentru Rețele Neuronale

**Disciplina:** Rețele Neuronale  
**Instituție:** POLITEHNICA București – FIIR  
**Student:** Toth David-Andrei 
**Data:** 27.11.2025  

---

## Introducere

Acest document descrie activitățile realizate în **Etapa 3**, în care se analizează și se preprocesează setul de date necesar proiectului „Rețele Neuronale". Scopul etapei este pregătirea corectă a datelor pentru instruirea modelului RN, respectând bunele practici privind calitatea, consistența și reproductibilitatea datelor.

---

##  1. Structura Repository-ului Github (versiunea Etapei 3)

```
project-detectie-defecte-auto/
├── README.md
├── docs/
│ └── datasets/
│ └── descriere_dataset.md # documentația dataset-ului
├── data/
│ ├── raw/
│ │ ├── images/
│ │ │ ├── OK/ # imagini cu piese conforme
│ │ │ └── DEFECT/ # imagini cu piese defecte
│ │ └── metadata_raw.csv # date brute asociate imaginilor
│ ├── processed/
│ │ └── metadata_processed.csv # date preprocesate
│ ├── train/
│ │ ├── images/
│ │ │ ├── OK/
│ │ │ └── DEFECT/
│ │ └── labels_train.csv
│ ├── validation/
│ │ └── labels_validation.csv
│ └── test/
│ └── labels_test.csv
├── src/
│ ├── preprocessing/
│ │ ├── clean_data.py # eliminare erori, valori lipsă
│ │ ├── normalize_data.py # normalizare date
│ │ └── split_dataset.py # împărțire train/val/test
│ ├── data_acquisition/
│ │ └── capture_images.py # achiziție imagini (simulat / cameră)
│ └── neural_network/
│ ├── model.py # arhitectura RN
│ └── train_model.py # antrenarea modelului
├── labview/
│ ├── Main.vi # aplicația principală LabVIEW
│ ├── CheckDefect.vi # subVI analiză defect
│ └── VisionConfig.vi # configurare cameră
├── config/
│ └── preprocessing_config.yaml # parametri preprocesare
└── requirements.txt
```

---

##  2. Descrierea Setului de Date

2.1 Sursa datelor

Origine: Set de date pentru inspecția vizuală a pieselor auto

Modul de achiziție: Imagini capturate de cameră industrială + date generate sintetic

Perioada colectării: Martie 2025 – Aprilie 2025

Condiții experimentale: Iluminare controlată, fundal uniform, distanță fixă față de piesă

2.2 Caracteristicile dataset-ului

Număr total observații: 1000

Număr caracteristici: 5 + eticheta clasei

Tipuri de date: Imagini + date numerice și categoriale

Format fișiere: PNG (imagini) + CSV (metadata)

### 2.3 Descrierea fiecărei caracteristici

Caracteristică	|Tip	    |Unitate	|Descriere	                             |  Domeniu valori
--------------------------------------------------------------------------------------------------------------------------------------
fisura_mm	|numeric	    |mm	              |Lungimea fisurii detectate	                | 0 – 10
rugina_pct	|numeric	    |%	              |Procent de rugină pe suprafață             | 0 – 100
textura	              |categorial   |  -	              |Tipul suprafeței piesei	                |neteda / aspra
iluminare	              |categorial   |  -	              |Condiții de iluminare	                |buna / slaba
clasa	              |categorial   |  -	              |Eticheta piesei	                              |OK / DEFECT

**Fișier recomandat:**  `data/README.md`

---

##  3. Analiza Exploratorie a Datelor (EDA) – Sintetic

### 3.1 Statistici descriptive aplicate

Analiza statistică a inclus:

Media și deviația standard pentru variabilele numerice

Valorile minime și maxime

Histograme pentru distribuția caracteristicilor

Boxplot-uri pentru detectarea valorilor extreme

Exemple rezultate:

media fisurilor pentru piesele OK: 0.4 mm

media fisurilor pentru piesele DEFECT: 3.8 mm

### 3.2 Analiza calității datelor

Procent valori lipsă:

fisura_mm: 1.2%

rugina_pct: 0.5%

Nu au fost identificate date invalide

Corelație ridicată între fisura_mm și clasa piesei

### 3.3 Probleme identificate

Dezechilibru de clasă (70% OK, 30% DEFECT)

Distribuție neuniformă a valorilor de iluminare

Puține valori lipsă pentru unele instanțe

---

##  4. Preprocesarea Datelor

### 4.1 Curățarea datelor

Eliminare duplicate

Imputare valori lipsă:

fisura_mm : mediană

rugina_pct : medie

Eliminare outlieri folosind metoda IQR
### 4.2 Transformarea caracteristicilor

Normalizare Min-Max pentru variabile numerice

One-Hot Encoding pentru variabile categoriale

Pregătire pentru introducere în rețea neuronală

### 4.3 Structurarea seturilor de date

Împărțire realizată astfel:

70% train

15% validation

15% test

Stratificare aplicată pentru menținerea proporției claselor
**Principii respectate:**
* Stratificare pentru clasificare
* Fără scurgere de informație (data leakage)
* Statistici calculate DOAR pe train și aplicate pe celelalte seturi

### 4.4 Salvarea rezultatelor preprocesării

Fisiere preprocesate: data/processed/metadata_processed.csv

Seturi separate în folderele dedicate

Parametri salvați în config/preprocessing_config.yaml

---

##  5. Fișiere Generate în Această Etapă

data/raw/ – date brute

data/processed/ – date curățate și transformate

data/train/ – set antrenare

data/validation/ – set validare

data/test/ – set testare

Scripturi în src/preprocessing/

Documentație în docs/datasets/descriere_dataset.md

---

##  6. Stare Etapă (de completat de student)

- [ ] Structură repository configurată
- [ ] Dataset analizat (EDA realizată)
- [ ] Date preprocesate
- [ ] Seturi train/val/test generate
- [ ] Documentație actualizată în README + `data/README.md`

---
