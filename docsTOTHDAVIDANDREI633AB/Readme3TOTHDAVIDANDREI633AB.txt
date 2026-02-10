📘 README – Etapa 3: Analiza și Pregătirea Setului de Date pentru Rețele Neuronale
Disciplina: Rețele Neuronale

Instituție: POLITEHNICA București – FIIR

Student:Toth David-Andrei 633 AB

Link repo: https://github.com/dvdtoth1900/Proiect-la-Retele-Neuronale-Toth-David-Andrei-633AB

Data: 09 Februarie 2026

Introducere
În cadrul Etapei 3, am realizat trecerea de la procesarea brută a imaginii la structurarea datelor necesare unei Rețele Neuronale. Activitatea s-a concentrat pe transformarea informației vizuale capturate în LabVIEW în trăsături numerice (features) exportate în format CSV, care vor servi drept input pentru antrenarea și testarea modelului de clasificare a defectelor.

1. Structura Repository-ului Github (versiunea Etapei 3)
defect-detection-sia/
├── README.md              # Documentația etapei 3
├── docs/
│   └── datasets/          # Diagrame de flux (LabVIEW Block Diagram)
├── data/
│   ├── raw/               # Imagini originale (.jpg/.png) preluate din camera/simulare
│   ├── processed/         # Imagini după Color Threshold și Morphology (binarizate)
│   ├── train/             # Subset de date pentru instruire 
│   ├── validation/        # Subset de date  pentru validare 
│   └── test/              # Subset de date  pentru testare finală 
├── src/
│   ├── preprocessing/     # VI-uri pentru Thresholding și Filtrare Morfologică
│   └── data_acquisition/  # VI-ul principal cu IMAQ Read File și Particle Analysis
└── config/                # Valorile optime de Min/Max (HSL) salvate ca constante
2. Descrierea Setului de Date
2.1 Sursa datelor
Origine: Imagini de înaltă rezoluție ale componentelor metalice (piese auto).

Modul de achiziție: ☐ Senzori reali / ☒ Fișier extern (Dataset simulat cu piese conforme și neconforme).

Condiții: Iluminare axială pentru evidențierea zgârieturilor prin reflexie.

2.2 Caracteristicile dataset-ului
Număr total de observații: 100 de imagini procesate.

Număr de caracteristici (features): 3 (Aria, Perimetrul, Intensitatea medie).

Tipuri de date: ☒ Imagini (Input) / ☒ Numerice (Output procesat).

Format fișiere: ☒ CSV (pentru RN) / ☒ PNG (pentru vizualizare).

2.3 Descrierea fiecărei caracteristici (Extrasă prin Particle Analysis)

Caracteristică,	Tip,		Unitate,		Descriere,Domeniu valori
Area,		numeric,		pixeli,		Suprafața totală a defectului detectat,0 – 5000
Perimeter,       	numeric,		pixeli,		Lungimea conturului defectului,0 – 1200
Luminance,	numeric,		0-255,		Intensitatea luminoasă medie a zonei,150 – 255

3. Analiza Exploratorie a Datelor (EDA)
3.1 Statistici descriptive aplicate
Medie/Mediană: Analiza ariei medii a defectelor pentru a stabili pragul de activare a alarmei.

Distribuția: Observarea histogramelor în LabVIEW pentru a separa "zgomotul" (pixeli izolați) de defectele reale.

3.2 Analiza calității datelor
Detectarea valorilor inconsistente: Identificarea reflexiilor de pe marginile piesei care generează arii mari, dar nu reprezintă defecte.

Probleme identificate: S-a observat un dezechilibru între piesele OK și cele Defecte în setul brut; s-a aplicat augmentarea datelor (rotații de imagini).

4. Preprocesarea Datelor (Implementată în LabVIEW)
4.1 Curățarea datelor (Nivel Imagine)
IMAQ Color Threshold: Filtrarea imaginii pentru a obține masca binară.

IMAQ Morphology: Aplicarea operației "Remove Small Objects" pentru eliminarea particulelor sub 10 pixeli.

4.2 Transformarea și Structurarea
Normalizare: Conversia coordonatelor pixelilor în valori relative față de centrul piesei.

Împărțire: Datele au fost împărțite în:

70% Train (70 intrări)

15% Validation (15 intrări)

15% Test (15 intrări)

4.3 Salvarea rezultatelor
Rezultatele numerice sunt stocate în data/processed/metrics.csv.

Imaginea cu overlay este salvată în data/processed/defect.jpg pentru validare umană.

5. Fișiere Generate în Această Etapă
 
"C:\Users\User\Desktop\aplicatiern\source\app\Proiect Rn Toth David-Andrei 633 AB-Detectarea defectiunilor pieselor auto.vi"

6. Stare Etapă (Completat)
[x] Structură repository configurată

[x] Dataset analizat (Identificat prag optim de Luminanță)

[x] Date preprocesate (Imagine -> Mască Binară -> Date Numerice)

[x] Seturi train/val/test 

[x] Documentație actualizată