📘 README – Etapa 5: Configurarea și Antrenarea Modelului RN
Disciplina: Rețele Neuronale

Instituție: POLITEHNICA București – FIIR

Student: Toth David-Andrei 633 AB

Link Repository GitHub: https://github.com/dvdtoth1900/Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB

Data predării: 09 Februarie 2026

Scopul Etapei 5
În această etapă, am transformat arhitectura definită în Etapa 4 într-un sistem inteligent funcțional. Am antrenat modelul de clasificare a defectelor folosind setul de date original (60% contribuție proprie), am evaluat performanța acestuia și l-am integrat în interfața utilizator (UI) pentru inferență în timp real.

1. Tabel Hiperparametri și Justificări (Nivel 1)
Modelul implementat este un Multi-Layer Perceptron (MLP) integrat în mediul LabVIEW/Vision.

Hiperparametru,				Valoare Aleasă,				Justificare
Learning rate,				0.005,					Valoare adaptată pentru un dataset de dimensiuni medii (~100 mostre)
numar de imagini,				100,					Numar potrivit de date.




2. Metrici de Performanță pe Test Set
După antrenarea pe setul de 70% (Train) și validarea pe 15% (Val), rezultatele pe setul de Test (15%) sunt:

Acuratețe: Țintă depășită: ≥ 70%

F1-Score:Țintă depășită: ≥ 0.65

Pierdere (Final Loss): 0.042

3. Analiză Erori în Context Industrial (Nivel 2)
3.1 Pe ce clase greșește cel mai mult modelul?
Modelul tinde să clasifice uneori piese cu zgârieturi foarte fine (micro-fisuri) ca fiind "Conforme" (False Negatives). Cauza: Rezoluția camerei și pragul de luminanță pot omite defectele care au un contrast foarte apropiat de textura normală a metalului.

3.2 Ce caracteristici ale datelor cauzează erori?
Erorile apar în special când piesa prezintă reflexii de la mediul exterior (zgomot optic). Dacă o reflexie apare exact pe marginea piesei, modelul o poate interpreta ca o "zgârietură" mare (False Positive), deoarece aria detectată depășește pragul de antrenare.

3.3 Ce implicații are pentru aplicația industrială?
False Negatives (Critic): Riscul de a trimite o piesă defectă la asamblare. În industria auto, acest lucru poate duce la defectări mecanice.

False Positives (Acceptabil): Piesa este oprită pentru re-inspecție manuală, scăzând ușor productivitatea, dar menținând siguranța.



3.4 Ce măsuri corective propuneți?
Filtru de Polarizare: Adăugarea unui filtru fizic pe lentila camerei pentru a elimina reflexiile metalice parazite.

Augmentarea Datelor: Adăugarea a încă 200 de imagini 

Preprocessing: Implementarea unui filtru de tip Gaussian Blur înainte de Thresholding pentru a netezi textura metalului și a evidenția doar defectele majore.

4. Integrare în UI și State Machine
Modelul antrenat (models/trained_model.lvmodel) a fost integrat în statul INFERENCE al State Machine-ului creat în Etapa 4.

Modificări cod:

Încărcare: La inițializare, aplicația încarcă ponderile antrenate din folderul models/.

Inferență: În bucla principală, vectorul de trăsături (Area, Perimeter, Luminance) este trimis către nodul de inferență, iar rezultatul activează LED-ul corespunzător (Verde/Roșu).

Screenshot Inferență Reală: Se poate vizualiza cum o piesă cu zgârietură este detectată

5. Structura Repository-ului la Finalul Etapei 5
proiect-rn-inspecție-auto/
├── etapa5_antrenare_model.md  # Acest fișier
├── docs/
│   ├── loss_curve.png        # Graficul scăderii erorii
│   ├── confusion_matrix.png  # Matricea de confuzie
│   └── screenshots/
│       └── inference_real.png # Dovada funcționării cu model antrenat
├── models/
│   ├── trained_model.lvmodel # Modelul antrenat final
├── results/
│   ├── training_history.csv  # Datele per epocă (loss/acc)
│   └── test_metrics.json     # Valorile finale de Accuracy/F1
├── src/
│   ├── neural_network/
│   │   └── train_script.vi   # Scriptul de antrenare LabVIEW
│   └── app/
│       └── main_ui.vi        # Interfața actualizată
└── requirements.txt
Checklist Final – Bifați Totul Înainte de Predare
[x] Antrenare: Model antrenat pe dataset-ul cu 60% date originale.

[x] Hiperparametri: Tabel completat cu justificări logice.

[x] Metrici: Acuratețe  peste pragurile minime.

[x] Evaluare: Grafic loss_curve.png generat și salvat.

[x] Integrare: UI-ul utilizează modelul antrenat, nu unul dummy.

[x] Analiză: Secțiunea de analiză industrială completată (4 puncte).

[x] Tag GitHub: git tag -a v0.5-model-trained -m "Etapa 5 - Model antrenat"