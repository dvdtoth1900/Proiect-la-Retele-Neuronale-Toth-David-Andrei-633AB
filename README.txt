README – Etapa 3: Analiza și Pregătirea Setului de Date pentru Rețele Neuronale

**Disciplina:** Rețele Neuronale  
**Instituție:** POLITEHNICA București – FIIR  
**Student:** Toth David-Andrei 633 AB  

**Data:** 20.11.2025 

## Introducere

Acest document descrie activitățile realizate în **Etapa 3**, în care se analizează și se preprocesează setul de date necesar proiectului „Rețele Neuronale". Scopul etapei este pregătirea corectă a datelor pentru instruirea modelului RN, respectând bunele practici privind calitatea, consistența și reproductibilitatea datelor.

Petru a accesa repository-ul cu numele "Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB" accesati urmatorul link:

https://github.com/dvdtoth1900/Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB/tree/main

Mai jos sunt descrisi pasii care formeaza etapa 3 a proiectului.

##  1. Structura Repository-ului GitHub "Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB" (versiunea Etapei 3)

Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB
├── README.md
├── documente
│   └── Proiect la Retele Neuronale Toth David-Andrei 633AB.pptx          
├── data/
|   ├──intrare
|       └── Tipul_piesei
|       └── Tipul_echipamentului
|       └──Marca_masinii
|   ├──iesire
|       └──Rezultatul_final_pentru_piesa
|       └──Rezultatul_final_pentru_echipament
│   ├── raw/   
|	└── Tipul_piesei
|       └── Tipul_echipamentului
|       └──Marca_masinii          
│   ├── processed/  
|       └── Tipul_piesei
|       └── Tipul_echipamentului
|       └──Marca_masinii      
│   ├── train/
|       └── Tipul_piesei
|       └── Tipul_echipamentului
|       └──Marca_masinii            
│   ├── validation/ 
|       └── Tipul_piesei
|       └── Tipul_echipamentului
|       └──Marca_masinii       
│   └── test/ 
|       └── Tipul_piesei
|       └── Tipul_echipamentului
|       └──Marca_masinii             
├── src/
│   ├── preprocessing/     # funcții pentru preprocesare
│   ├── data_acquisition/  # generare / achiziție date (dacă există)
│   └── neural_network/    # implementarea RN (în etapa următoare)
├── config/                # fișiere de configurare
└── requirements.txt      

##  2. Descrierea Setului de Date

### 2.1 Sursa datelor

* **Origine:** LabView
* **Modul de achiziție:** ☐ Senzori reali / ✓ Simulare / ☐ Fișier extern / ☐ Generare programatică
* **Perioada / condițiile colectării:** Noiembrie 2025

### 2.2 Caracteristicile dataset-ului

* **Număr total de observații:
* **Număr de caracteristici (features):
* **Tipuri de date:** ☐ Numerice / ☐ Categoriale / ☐ Temporale / ☐ Imagini / ✓ Siruri de caractere
* **Format fișiere:** ☐ CSV / ✓ TXT / ☐ JSON / ☐ PNG / ☐ Altele: [...]

### 2.3 Descrierea fiecărei caracteristici

| **Caracteristică** | **Tip** | **Unitate** | **Descriere** | **Domeniu valori** |
|--------------------|---------|-------------|---------------|--------------------|

**Fișier recomandat:**  README.txt

##  3. Analiza Exploratorie a Datelor (EDA) – Sintetic

### 3.1 Statistici descriptive aplicate

* **Medie, mediană, deviație standard**
* **Min–max și quartile**
* **Distribuții pe caracteristici** (histograme)
* **Identificarea outlierilor** (IQR / percentile)

### 3.2 Analiza calității datelor

* **Detectarea valorilor lipsă** (% pe coloană)
* **Detectarea valorilor inconsistente sau eronate**
* **Identificarea caracteristicilor redundante sau puternic corelate**

### 3.3 Probleme identificate

* [exemplu] Feature X are 8% valori lipsă
* [exemplu] Distribuția feature Y este puternic neuniformă
* [exemplu] Variabilitate ridicată în clase (class imbalance)
