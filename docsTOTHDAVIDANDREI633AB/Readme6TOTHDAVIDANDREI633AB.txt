📘 README – Etapa 6: Analiza Performanței, Optimizarea și Concluzii Finale
Disciplina: Rețele Neuronale

Instituție: POLITEHNICA București – FIIR

Student:Toth David-Andrei 633 AB

Link Repository GitHub:https://github.com/dvdtoth1900/Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB

Data predării: 09 Februarie 2026

1. Tabel Experimente de Optimizare

Exp#,					Modificare față de Baseline (Etapa 5),			Accuracy,		F1-score,		Timp antrenare,		Observații
Exp 1,					Configurația din Etapa 5 	,			0.70,		0.70,		10 min,			Referință
Exp 2,					LR 0.005 → 0.001 ,				0.80,		0.79,		12 min,			Convergență lină
Exp 3,					Augmentări HSL (Luminanță ±15%),			0.95,		0.93,		20 min,			BEST

Justificare alegere configurație finală: Am ales Exp 4 ca model final. Creșterea performanței se datorează augmentării robuste a datelor (simularea variațiilor de iluminare industrială). 
Aceasta a permis rețelei să ignore micile variații de reflexie ale metalului și să se concentreze pe trăsăturile geometrice ale zgârieturii.

2. Actualizarea Aplicației Software în Etapa 6

Componenta,			Stare Etapa 5,			Modificare Etapa 6,				Justificare
Model,				trained_model.lvmodel,		optimized_model.lvmodel,			+7% Acuratețe
Alert Threshold,			0.5 (Standard),			0.35,					Minimizare False Negatives (siguranță)
Stare Nouă 			N/A,CALIBRATE_LIGHT,		Verifică dacă lumina e optimă înainte de captură


3. Analiza Detaliată a Performanței
3.1 Interpretare Confusion Matrix:
Clasa cu cea mai bună performanță: Piesă Conformă (Normal). Modelul recunoaște suprafețele curate datorită texturii uniforme.

 Zgârieturile foarte fine nu produc o schimbare de luminanță suficientă pentru a fi distinse de granulația naturală a metalului.

3.2 Analiza a 5 Exemple Greșite (Rezumat)
Index #45: Defect clasificat ca OK. Cauză: Reflexie puternică ce a "șters" vizual zgârietura.

Index #88: OK clasificat ca Defect. Cauză: Scama de praf interpretată ca particulă de defect. Soluție: Filtru de curățare aer comprimat în stadiul de preprocesare.

4. Concluzii Finale și Lecții Învățate
4.1 Evaluarea Performanței Finale
Sistemul a atins o acuratețe de peste 70%, depășind obiectivul. Integrarea cu State Machine-ul LabVIEW asigură un timp de răspuns de 50ms.

4.2 Limitări Identificate
Senzitivitate la praf: Impuritățile pe piesă pot genera alarme false.

Geometrie: Funcționează optim doar pe suprafețe plane; pe suprafețe curbe, distorsiunile optice scad performanța.

4.3 Lecții Învățate
Datele bat Modelul: Augmentarea inteligentă a luminanței a adus un beneficiu mai mare decât adăugarea de straturi neurale complexe.

Contextul contează: Într-o fabrică, un "False Negative" este mult mai costisitor decât un "False Positive". 

Preprocessing-ul este cheia: 80% din succesul proiectului a depins de calitatea segmentării HSL din Etapa 3.

5. Plan Post-Feedback (Examen)
În urma feedback-ului, voi:

Îmbunătăți starea CALIBRATE_LIGHT pentru a auto-regla timpul de expunere al camerei.

Actualiza README-urile anterioare pentru a asigura o coerență totală a documentației.

Tag final: git tag -a v1.0-final-exam -m "Versiune finală pentru examen" Commit final: Etapa 6 completă 