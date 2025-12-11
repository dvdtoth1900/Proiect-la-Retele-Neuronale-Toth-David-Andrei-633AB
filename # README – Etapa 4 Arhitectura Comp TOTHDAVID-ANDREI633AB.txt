# README – Etapa 4: Arhitectura Completă a Aplicației SIA bazată pe Rețele Neuronale

**Disciplina:** Rețele Neuronale  
**Instituție:** POLITEHNICA București – FIIR  
**Student:** Toth David-Andrei
**Link Repository GitHub**
**Data:** 4.12.2025  


### 1. Tabelul Nevoie Reală → Soluție SIA → Modul Software

| **Nevoie reală concretă**                         | **Cum o rezolvă SIA-ul vostru**                                  |---------------------------------------------------|---------------------------------                                
| -Identificarea defectiunilor pieselor auto        | -marcarea defectiunilor piesei in imaginea care a fost procesata                                                               
| -Asigurarea calitatii componentelor autoturismelor| -afisarea rezultatelor finale dupa procesarea imaginii (afisarea solutiilor in cazul in care apar erori)                                                                                                          
| -Siguranta participantilor la trafic              | -Cu ajutorul preciziei rezultatelor, SIA-ul dezvoltat poate asigura siguranta                                   |                                                 
|                                                   |                                                                 
|                                                   |                                                                 


| **Modul software responsabil** |
|--------------------------------
|-UI+RN detectarea defectelor și analiza soluțiilor
|-RN ofera rezultate precise care pot dezvolta industria auto
|-RN

### 2. Contribuția Voastră Originală la Setul de Date – MINIM 40% din Totalul Observațiilor Finale

| **Tip contribuție**                        | **Exemple concrete din inginerie**  | **Dovada minimă cerută** |
|---------------------                       |-------------------------------------|--------------------------|
| **Date generate prin simulare fizică**     |-imagini cu piese auto                -descrierea imaginilor
| **Date de testare și validare independente |-fotografii cu componentele care urmeaza sa fie procesate|-rezultate comparative cu modelul antrenat    

**Descriere detaliată:** Datele de intrare au fost obtinute de pe Google Chrome, acestea fiind poze cu piese auto. Se doreste procesarea a 200 de fotografii.

			Dupa alegerea datelor de intrare urmeaza scarnarea pieselor auto din poze pentru a identifica daca piesele sunt bune sau rebuturi.
			
			Ca data de iesire vom avea un image display care afiseaza defectele piesei cu buline rosii daca piesa are defecte si un boolean care este verde daca piesa este buna sau rosu daca piesa este defecta. 

			In concluzie, acest proiect se remarca prin setul numeos de date de intrare si prin identificarea defectiunilor.

			

**Locația codului:** LabVIEW/Verificarea_defectiunilor.vi
**Locația datelor:** In folderul ProiectRN in subfolderul data





### 3. Diagrama State Machine a Întregului Sistem 

APLICATIE OPRITA->START(PORNIREA APLICATIEI)->PRIMIREA DATELOR->PROCESAREA DATELOR->AFISAREA REZULTATELOR
									               ├─ [OK] →PIESA POATE TRECE MAI DEPARTE
									               └─ [DEFECT] → PIESA ESTE REBUT->NU TRECE MAI DEPARTE
->SALVAREA RESULTATELOR->OPRIREA APLICATIEI

### 4. Scheletul Complet al celor 3 Module Cerute la Curs (slide 7)



| **Modul** | **LabVIEW** | **Cerință minimă funcțională (la predare)** |
|-----------|----------------------------------|-------------|----------------------------------------------|
| **1. Data Logging / Acquisition** | `src/data_acquisition/` | LLB cu VI-uri de generare/achiziție | 
 Cod rulează fără erori și generează minimum 100 samples demonstrative. |
| **2. Neural Network Module** | `src/neural_network/model.py` sau folder dedicat | LLB cu VI-uri RN | required:** Model antrenat cu performanță bună (poate avea weights random/inițializați). |
| **3. Web Service / UI** | Streamlit, Gradio, FastAPI, Flask, Dash | WebVI sau Web Publishing Tool | required:** UI frumos, funcționalități avansate. |

#### Detalii per modul:

#### **Modul 1: Data Logging / Acquisition**

**Funcționalități obligatorii:**
- [x ] Cod rulează fără erori:LabVIEW
- [x ] Include minimum 40% date originale în dataset-ul final
- [x ] Documentație în cod: ce date generează, cu ce parametri

#### **Modul 2: Neural Network Module**

**Funcționalități obligatorii:**
- [ ] Arhitectură RN definită și compilată fără erori
- [ ] Model poate fi salvat și reîncărcat
- [ ] Include justificare pentru arhitectura aleasă (în docstring sau README)
- [ ] **NU trebuie antrenat** cu performanță bună (weights pot fi random)


#### **Modul 3: Web Service / UI**

**Funcționalități MINIME obligatorii:**
- [ ] Propunere Interfață ce primește input de la user (formular, file upload, sau API endpoint)
- [ ] Includeți un screenshot demonstrativ în `docs/screenshots/`




## Structura Repository-ului la Finalul Etapei 4 (OBLIGATORIE)

**Verificare consistență cu Etapa 3:**

```
proiect-rn-[nume-prenume]/
├── data/
│   ├── raw/
│   ├── processed/
│   ├── generated/  # Date originale
│   ├── train/
│   ├── validation/
│   └── test/
├── src/
│   ├── data_acquisition/
│   ├── preprocessing/  # Din Etapa 3
│   ├── neural_network/
│   └── app/  # UI schelet
├── docs/
│   ├── state_machine.*           #(state_machine.png sau state_machine.pptx sau state_machine.drawio)
│   └── [alte dovezi]
├── models/  # Untrained model
├── config/
├── README.md
├── README_Etapa3.md              # (deja existent)
├── README_Etapa4_Arhitectura_SIA.md              # ← acest fișier completat (în rădăcină)
└── requirements.txt  # Sau .lvproj
```


## Checklist Final – Bifați Totul Înainte de Predare

### Documentație și Structură
- [ ] Tabelul Nevoie → Soluție → Modul complet (minimum 2 rânduri cu exemple concrete completate in README_Etapa4_Arhitectura_SIA.md)
- [ ] Declarație contribuție 40% date originale completată în README_Etapa4_Arhitectura_SIA.md
- [ ] Cod generare/achiziție date funcțional și documentat
- [ ] Dovezi contribuție originală: grafice + log + statistici în `docs/`
- [ ] Diagrama State Machine creată și salvată în `docs/state_machine.*`
- [ ] Legendă State Machine scrisă în README_Etapa4_Arhitectura_SIA.md (minimum 1-2 paragrafe cu justificare)
- [ ] Repository structurat conform modelului de mai sus (verificat consistență cu Etapa 3)

### Modul 1: Data Logging / Acquisition
- [ ] Cod rulează fără erori (`python src/data_acquisition/...` sau echivalent LabVIEW)
- [ ] Produce minimum 40% date originale din dataset-ul final
- [ ] CSV generat în format compatibil cu preprocesarea din Etapa 3
- [ ] Documentație în `src/data_acquisition/README.md` cu:
  - [ ] Metodă de generare/achiziție explicată
  - [ ] Parametri folosiți (frecvență, durată, zgomot, etc.)
  - [ ] Justificare relevanță date pentru problema voastră
- [ ] Fișiere în `data/generated/` conform structurii

### Modul 2: Neural Network
- [ ] Arhitectură RN definită și documentată în cod (docstring detaliat) - versiunea inițială 
- [ ] README în `src/neural_network/` cu detalii arhitectură curentă

### Modul 3: Web Service / UI
- [ ] Propunere Interfață ce pornește fără erori (comanda de lansare testată)
- [ ] Screenshot demonstrativ în `docs/screenshots/ui_demo.png`
- [ ] README în `src/app/` cu instrucțiuni lansare (comenzi exacte)

---


**Tag obligatoriu:**  
`git tag -a v0.4-architecture -m "Etapa 4 - Skeleton complet SIA"`

