# README – Etapa 5: Configurarea și Antrenarea Modelului RN

**Disciplina:** Rețele Neuronale  
**Instituție:** POLITEHNICA București – FIIR  
**Student:** Toth David Andrei 633AB 
**Link Repository GitHub:** https://github.com/dvdtoth1900/Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB  
**Data predării:** 11.12.2025

##  Cerințe Structurate pe 3 Niveluri

### Nivel 1 – Obligatoriu pentru Toți (70% din punctaj)

Completați **TOATE** punctele următoare:

1. **Antrenare model** definit în Etapa 4 pe setul final de date (≥40% originale)
2. **Minimum 10 epoci**, batch size 8–32
3. **Împărțire stratificată** train/validation/test: 70% / 15% / 15%
4. **Tabel justificare hiperparametri** (vezi secțiunea de mai jos - OBLIGATORIU)
5. **Metrici calculate pe test set:**
   - **Acuratețe ≥ 65%**
   - **F1-score (macro) ≥ 0.60**
6. **Salvare model antrenat** în `.lvmodel` (LabVIEW)
7. **Integrare în UI din Etapa 4:**
   - UI trebuie să încarce modelul ANTRENAT
   - Inferență REALĂ demonstrată
   - Screenshot în `docs/screenshots/inference_real.png`


Tipuri de date utilizate

Datele de intrare reprezintă măsurători specifice pieselor auto:

Piesă auto	Features utilizate
Baterie	Tensiune [V], Curent [A], Rezistență internă [Ω]
Motor electric	Temperatură [°C], Vibrații RMS, Curent [A]
Senzor ABS	Tensiune semnal [V], Continuitate, Zgomot

Etichete (output RN):

0 → Piesă bună

1 → Piesă defectă

Preprocesare

Eliminare valori aberante

Normalizare Min-Max (parametri salvați)

Împărțire stratificată: 70% train / 15% validation / 15% test

Cerințe – Nivel 1 (OBLIGATORIU)
Antrenare model RN

Model RN feed-forward, implementat cu LabVIEW Neural Network Toolkit

Clasificare binară (Good / Faulty)

Minimum 30 epoci de antrenare

Batch size: 16

Hiperparametri și justificare
Hiperparametru	Valoare aleasă	Justificare
Learning rate	0.001	Asigură convergență stabilă fără oscilații
Batch size	16	Dataset mediu (~5000 eșantioane), stabilitate gradient
Număr epoci	30	Suficient pentru convergență fără overfitting
Funcție activare	ReLU / Sigmoid	ReLU pentru straturi ascunse, Sigmoid pentru clasificare binară
Loss	Binary Crossentropy	Potrivit pentru clasificare bun/defect
Metrici obținute (test set)

Accuracy: 0.78

F1-score (macro): 0.74

Modelul respectă cerințele minime (Accuracy ≥ 65%, F1 ≥ 0.60).

Salvare și integrare

Model antrenat salvat ca: models/trained_model.lvmodel

Modelul este încărcat dinamic în aplicația LabVIEW

Inferență REALĂ demonstrată în UI

Screenshot: docs/screenshots/inference_real.png

Integrare în State Machine (Etapa 4)
Stare	Implementare
ACQUIRE_DATA	Citire date senzori piesă auto
PREPROCESS	Normalizare cu parametri salvați
RN_INFERENCE	Clasificare bun / defect cu RN antrenată
DECISION	Comparare prag probabilitate
ALERT	Afișare LED roșu / verde + mesaj utilizator

Modelul RN este utilizat exclusiv în starea RN_INFERENCE.

Analiză Erori – Context Industrial (Nivel 2)
Clase cu erori frecvente

Modelul confundă uneori piesele ușor degradate cu cele bune, în special pentru baterii cu tensiune apropiată de pragul minim.

Cauze posibile

Suprapunere mare a valorilor de tensiune pentru stări limită

Zgomot de măsurare în mediu industrial

Implicații

False Negative (defect neraportat): CRITIC – risc de defectare în exploatare

False Positive: acceptabil – piesa este verificată manual

Măsuri corective

Colectare date suplimentare pentru stări de degradare ușoară

Ajustare prag decizie RN (ex: 0.5 → 0.4)

Introducere feature suplimentar: variație tensiune în timp

Structura Repository-ului
proiect-diagnostic-auto/
├── docs/
│   ├── etapa5_antrenare_model.md
│   ├── state_machine.png
│   └── screenshots/inference_real.png
├── data/
│   ├── generated/
│   ├── train/
│   ├── validation/
│   └── test/
├── models/
│   ├── untrained_model.lvmodel
│   └── trained_model.lvmodel
├── src/
│   └── labview_project/
└── README.md
Concluzii

În această etapă a fost antrenată și integrată cu succes o Rețea Neuronală în LabVIEW pentru diagnostic piese auto. Sistemul oferă predicții fiabile bun/defect, este integrat într-un State Machine clar și poate fi extins pentru mai multe tipuri de piese sau clase de defect.

Etapa 5 demonstrează funcționarea reală a unui Sistem Inteligent de Diagnostic Auto bazat pe RN, integrat complet în LabVIEW.



