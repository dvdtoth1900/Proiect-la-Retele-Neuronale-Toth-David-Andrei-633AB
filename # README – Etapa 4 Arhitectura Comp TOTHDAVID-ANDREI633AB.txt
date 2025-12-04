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



### 3. Diagrama State Machine a Întregului Sistem (OBLIGATORIE)

APLICATIE OPRITA->START(PORNIREA APLICATIEI)->PRIMIREA DATELOR->PROCESAREA DATELOR->AFISAREA REZULTATELOR
									               ├─ [OK] →PIESA POATE TRECE MAI DEPARTE
									               └─ [DEFECT] → PIESA ESTE REBUT->NU TRECE MAI DEPARTE
->SALVAREA RESULTATELOR->OPRIREA APLICATIEI

