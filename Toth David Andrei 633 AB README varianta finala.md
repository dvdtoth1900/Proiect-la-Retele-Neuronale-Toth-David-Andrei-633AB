Student	Toth David-Andrei
Grupa / Specializare	633AB / Informatică Industrială
Disciplina	Rețele Neuronale
Instituție	POLITEHNICA București – FIIR
Link Repository GitHub	https://github.com/dvdtoth1900/Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB
Acces Repository	Public
Stack Tehnologic	LabVIEW (Vision Development Module + Deep Learning Toolkit)
Domeniul Industrial	Automotive / Controlul Calității
Tip Rețea Neuronală	: Retea realizata in Lab View

Rezultate Cheie (Etapa 5 vs Etapa 6)

Metric,Țintă Minimă,Rezultat Etapa 5,Rezultat Etapa 6,Îmbunătățire,Status
Accuracy (Test Set),≥70%✓
F1-Score (Macro),≥0.65✓
Latență Inferență,<50 ms✓

2. Descrierea Nevoii și Soluția SIA
2.1 Nevoia Reală
În industria automotive, detectarea defectelor de suprafață (zgârieturi, lovituri) pe piesele metalice este critică. Inspecția manuală este obositoare și subiectivă. Acest proiect propune un sistem automatizat care utilizează viziune artificială și rețele neuronale pentru a clasifica piesele în timp real, eliminând eroarea umană și crescând viteza de producție.

2.3 Tabel: Nevoie → Soluție SIA

Nevoie reală concretă,Cum o rezolvă SIA-ul,Modul software,Metric măsurabil
Detecție zgârieturi metal,Clasificare imagini preprocesate,Neural Network ,Accuracy >70%
Filtrare particule (LabVIEW),
Alertare instantanee,State Machine cu ramură de Rebut,UI / Control Logic <50ms

3. Dataset și Contribuție Originală
3.1 Sursa și Caracteristicile Datelor
Origine date: Mixt (Dataset public pentru defecte metalice + Imagini capturate local cu camera web).

Total observații: 100 de imagini.

Contribuție originală: 44% (44 de imagini).

3.3 Preprocesare (Configurația LabVIEW)
Color Threshold: HSL (Luminance: 80 - 150).

Morfologie: Operator "Open" pentru eliminarea zgomotului.

Particle Filter: Minimum area: 60 pixeli.

4. Arhitectura SIA și State Machine
4.2 State Machine (Conform Diagramă Bloc)
Sistemul utilizează un flux logic circular implementat în LabVIEW:

Initializare: Pregătirea IMAQ Create.

Asteptare Comanda: Buclă de idle.

Selectare Date: Achiziția imaginii de la fișier/cameră.

Control: Ingerarea datelor în modelul optimized_model.h5.

Rebut / Piesa Buna: Clasificare binară.

Evidentiere Defecte: Desenarea cercurilor  rosii pe imaginea originală.

Oprire

5. Modelul RN – Antrenare și Optimizare
5.1 Arhitectura Rețelei (CNN)
Input: Grayscale.
Conv Layers: pentru verioficarea texturilor componentelor.
Dense Layers: 128 neuroni ReLU + Strat Output Softmax (2 clase).

5.3 Experimente de Optimizare

Exp#,Modificare,Accuracy,Observații
1,Baseline (Etapa 5),80%,Ratează defectele fine sub-iluminate.
2,Ajustare Threshold (80-150),85%,Elimină reflexiile parazite.
3,Filtru Particule (Min 60px),75%,Elimină alarmele false date de praf.
4,Fine-tuning Learning Rate,75%,Configurația Finală (Optimă).

6. Performanță Finală și Analiză Erori
6.1 Metrici pe Test Set
Accuracy: >70%

F1-Score: >0.65

Confusion Matrix: [n, m] n-piese ratate, m-piese verificate cu succes

6.3 Analiza Top Erori
Cauză: Contrast extrem de scăzut între zgârietură și reflexia metalică.

Implicație: Necesită iluminare controlată (dom optic) pentru a elimina umbrele.

8. Structura Repository-ului
proiect-rn-[nume-prenume]/
│
├── README.md                               # ← ACEST FIȘIER (Overview Final Proiect - Pe moodle la Evaluare Finala RN > Upload Livrabil 1 - Proiect RN (Aplicatie Sofware) - trebuie incarcat cu numele: NUME_Prenume_Grupa_README_Proiect_RN.md)
│
├── docs/
│   ├── etapa3_analiza_date.md              # Documentație Etapa 3
│   ├── etapa4_arhitectura_SIA.md           # Documentație Etapa 4
│   ├── etapa5_antrenare_model.md           # Documentație Etapa 5
│   ├── etapa6_optimizare_concluzii.md      # Documentație Etapa 6
│   │
│   ├── state_machine.png                   # Diagrama State Machine inițială
│   ├── confusion_matrix_optimized.png      # Confusion matrix model final
│   │
│   ├── screenshots/
│   │   ├── ui_demo.png                     # Screenshot UI schelet (Etapa 4)
│   │   ├── inference_real.png              # Inferență model antrenat (Etapa 5)
│   │   └── inference_optimized.png         # Inferență model optimizat (Etapa 6)
│   │
│   ├── demo/                               # Demonstrație funcțională end-to-end
│   │   └── demo_end_to_end.gif             # (sau .mp4 / secvență screenshots)
│   │
│   ├── results/                            # Vizualizări finale
│   │   ├── loss_curve.png                  # Grafic loss/val_loss (Etapa 5)
│   │   ├── metrics_evolution.png           # Evoluție metrici (Etapa 6)
│   │   └── learning_curves_final.png       # Curbe învățare finale
│   │
│   └── optimization/                       # Grafice comparative optimizare
│       ├── accuracy_comparison.png         # Comparație accuracy experimente
│       └── f1_comparison.png               # Comparație F1 experimente
│
├── data/
│   ├── README.md                           # Descriere detaliată dataset
│   ├── raw/                                # Date brute originale
│   ├── processed/                          # Date curățate și transformate
│   ├── generated/                          # Date originale (contribuția ≥40%)
│   ├── train/                              # Set antrenare (70%)
│   ├── validation/                         # Set validare (15%)
│   └── test/                               # Set testare (15%)
│
├── src/
│   ├── data_acquisition/                   # MODUL 1: Generare/Achiziție date
│   │   ├── README.md                       # Documentație modul
│   │
│   ├── preprocessing/                      # Preprocesare date (Etapa 3+)
│   │
│   ├── neural_network/                     # MODUL 2: Model RN
│   │   ├── README.md                       # Documentație arhitectură RN
│   │
│   └── app/                                
│       ├── README.md                       
│       └── "Proiect Rn Toth David-Andrei 633 AB-Detectarea defectiunilor pieselor auto.vi"                      
│
├── models/
│   ├── untrained_model.h5                  # Model schelet neantrenat (Etapa 4)
│   ├── trained_model.h5                    # Model antrenat baseline (Etapa 5)
│   ├── optimized_model.h5                  # Model FINAL optimizat (Etapa 6) ← FOLOSIT
│   
│
│
├── config/
│   └── optimized_config.yaml               # Configurație finală model (Etapa 6)
│
├── requirements.txt                        # Dependențe Python (actualizat la fiecare etapă)





10. Concluzii
Proiectul demonstrează că integrarea unei rețele neuronale într-un State Machine LabVIEW poate sa creasca acuratetea verificarii pieselor. Lecția principală a fost că preprocesarea datelor (filtrarea corectă a particulelor sub 60 pixeli) este la fel de importantă ca arhitectura rețelei neuronale pentru obținerea rezultatelor corespunzatoare.

Data și ora demonstrației: 09.02.2026, 20:15

Tag Git: v0.6-optimized-final