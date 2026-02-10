

📘 README – Etapa 4: Arhitectura Completă a Aplicației SIA bazată pe Rețele Neuronale
Disciplina: Rețele Neuronale

Instituție: POLITEHNICA București – FIIR

Student: Toth David-Andrei 633 AB

Repository:https://github.com/dvdtoth1900/Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB

Data: 09 Februarie 2026

1. Tabel Nevoie Reală → Soluție SIA → Modul Software

Nevoie reală concretă,						Cum o rezolvă SIA-ul vostru,						Modul software responsabil
Detectarea automată a zgârieturilor pe componente metalice lucioase,	Segmentare HSL + Clasificare binară (OK/Defect) în < 500ms,		Modul 1 (Acquisition) + Modul 2 (RN)
Trasabilitatea defectelor în linia de producție,				Salvare automată a coordonatelor și a imaginii procesate cu overlay roșu,	Modul 1 (Logging) + Modul 3 (UI)
Monitorizarea ratei de rebut la distanță,				Transmiterea statusului piesei către un dashboard web centralizat,		Modul 3 (Web Service)

2. Contribuția Originală la Setul de Date
Total observații finale: 100 de imagini/mostre

Observații originale: 44 (44%)

Tipul contribuției: [x] Date achiziționate cu senzori proprii (Cameră/Dataset real adnotat)

[x] Etichetare/adnotare manuală

[ ] Date generate prin simulare fizică

Descriere detaliată: Contribuția originală constă în realizarea unui setup de achiziție vizuală utilizând piese metalice reale. Am colectat 50 de imagini cu piese conforme și 22 de imagini cu piese prezentând defecte induse controlat (zgârieturi de diverse adâncimi).

Fiecare imagine a fost etichetată manual prin definirea regiunii de interes (ROI) și extragerea metricilor de Arie și Luminanță folosind tool-ul de Particle Analysis din LabVIEW. Aceste date au fost salvate într-un fișier CSV original care servește drept bază pentru instruirea ulterioară a modelului, asigurând o variabilitate mai mare decât dataset-urile publice generice (care nu includ texturi metalice specifice).

Locația codului: "C:\Users\User\Desktop\aplicatiern\Proiect Rn Toth David-Andrei 633 AB-Detectarea defectiunilor pieselor auto.vi"
"C:\Users\User\Desktop\aplicatiern\Readme4.txt"

Locația datelor: "C:\Users\User\Desktop\aplicatiern\data"

3. Diagrama State Machine a Întregului Sistem
Justificarea State Machine-ului ales:

Stările principale sunt:

ON: Punctul de pornire al sistemului.

Initializare: Configurarea parametrilor inițiali și pregătirea hardware-ului/software-ului.

Asteptarea urmatoarei comenzi: Starea de veghe în care sistemul stă activ până primește un semnal de execuție.

Primirea datelor de intrare: Capturarea sau citirea imaginilor/datelor brute (de exemplu, de la cameră sau fișier).

Selectarea datelor care vor fi procesate: Filtrarea și pregătirea subsetului de date relevant pentru analiză.

Control: Etapa centrală de procesare și analiză (unde intervine Rețeaua Neuronală pentru decizie).

Din starea de Control, fluxul se ramifică în funcție de rezultat:

Ramura REBUT: 7. Rebut: Identificarea piesei ca fiind neconformă. 8. Evidentierea defectelor: Marcarea vizuală a zonelor cu probleme pe piesă.

Ramura PIESA BUNA: 7. Piesa auto buna: Validarea conformității piesei.

După oricare dintre cele două ramuri, sistemul revine la:

Asteptarea urmatoarei comenzi: Reîntoarcerea în starea de veghe.

De aici, există două opțiuni finale:

Continuarea procesului de verificare: Reluarea ciclului pentru o nouă piesă.

Oprire: Închiderea programului și finalizarea execuției.

4. Scheletul Complet al Modulelor

Modul,  								Statut funcțional
1. Data Logging,							FUNCȚIONAL
2. Neural Network,							DEFINIT: Arhitectură LabView
3. Web Service / UI,						FUNCȚIONAL: Interfață cu indicator string și afișare imagine procesată.

