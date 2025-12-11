# 📘 README – Etapa 5: Configurarea și Antrenarea Modelului RN

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
6. **Salvare model antrenat** în `models/trained_model.h5` (Keras/TensorFlow) sau `.pt` (PyTorch) sau `.lvmodel` (LabVIEW)
7. **Integrare în UI din Etapa 4:**
   - UI trebuie să încarce modelul ANTRENAT (nu dummy)
   - Inferență REALĂ demonstrată
   - Screenshot în `docs/screenshots/inference_real.png`

#### Tabel Hiperparametri și Justificări (OBLIGATORIU - Nivel 1)

Completați tabelul cu hiperparametrii folosiți și **justificați fiecare alegere**:

| **Hiperparametru** | **Valoare Aleasă** | **Justificare** |
|--------------------|-------------------|-----------------|
| Learning rate | Ex: 0.001 | |
| Batch size | Ex: 200 |  |
| Number of epochs | Ex: 50 |  |
| Optimizer | David |  |
| Loss function |  |  |
| Activation functions |  |  |

**Justificare detaliată batch size (exemplu):**
```
Am ales batch_size=32 pentru că avem N=15,000 samples → 15,000/32 ≈ 469 iterații/epocă.
Aceasta oferă un echilibru între:
- Stabilitate gradient (batch prea mic → zgomot mare în gradient)
- Memorie GPU (batch prea mare → out of memory)
- Timp antrenare (batch 32 asigură convergență în ~50 epoci pentru problema noastră)
```




