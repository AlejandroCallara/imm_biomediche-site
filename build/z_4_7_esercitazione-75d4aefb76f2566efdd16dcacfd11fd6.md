# Esercitazione 4.7: Visualizzazione Ed Elaborazione di Segnali 1H-MRS

<!-- Origine: Esercitazione_2025_2026_8_CALLARA_SANTARELLI.docx -->

La cartella “Dati per MRS” contiene
- *File 1H_MRS_soleo_NL.mat*
- *File 1H_MRS_soleo_OB.mat*

In ciascun file sono memorizzati 18FID: i primi 2 sono stati acquisiti senza soppressione dell’acqua, mentre gli altri 16 sono stati acquisiti con la soppressione dell’acqua.
Ciascun segnale è stato acquisito con $\Delta f = 5000\text{Hz}/2048 \text{pts}$

## A.1 
Eseguire
- una correzione di fase di ordine 0 di tutti i FID memorizzati nei due file e mostrare i risultati ottenuti su uno spettro senza soppressione dell’acqua e uno con soppressione dell’acqua (es. 1 e 10). Mostrare parte reale e immaginaria dei FID e degli spettri prima e dopo la correzione di fase.
- TIP: Per correggere la fase occorre trovare quel valore di PHI_0 per cui
`real(FT_sig.*(cos(PHI_0)+1j*sin(PHI_0)))` sia massimo

## A.2 
Visualizzare
- La parte reale dello spettro mediando i 16 spettri corretti in fase con soppressione dell’acqua (`FID[2:]`) del file 1H_MRS soleo_NL, con l’asse delle ascisse sia in Hz che in ppm

**TIP:** per passare da Hz a ppm usare la seguente formula di conversione

```
conversione = 60.71
ppm_acqua = 4.8
fppm = -(fHz/conversione)+ppm_acqua
```

**TIP 2:** l’ascissa, nella presentazione in ppm, è in ordine decrescente (invertire l'asse x)

## A.3
Stimare, utilizzando il modello visto a lezione, i parametri sui dati sperimentali ottenuti dal FID mediato del punto precedente e corretto in fase (NB. Qui si tratta del FID mediato).

- Farlo sui dati contenuti nel file *1H_MRS_soleo_NL.mat*
- Farlo sui dati contenuti nel file *1H_MRS_soleo_OB.mat*

### SUGGERIMENTI PER LA STIMA DEI PARAMETRI

A seguire una descrizione del modello del FID secondo

$$
y_n
=
\sum_{k=1}^{K}
a_k e^{i\phi_k}
e^{-\left(d_k+i2\pi f_k\right)t_n}
+
e_n
$$

E la stima dei parametri $a_k$, $d_k$ e $f_k$. NB. $\phi_k=0$ (correzione di fase già effettuata)

# Fitting Models
Utilizzare il seguente codice

```
def model_fun_r(t, a1, d1, f1, a2, d2, f2):
return (a1 * np.exp(-d1 * t) * np.cos(2 * np.pi * f1 * t) +
a2 * np.exp(-d2 * t) * np.cos(2 * np.pi * f2 * t))

def model_fun_i(t, a1, d1, f1, a2, d2, f2):
return (a1 * np.exp(-d1 * t) * np.sin(2 * np.pi * f1 * t) +
a2 * np.exp(-d2 * t) * np.sin(2 * np.pi * f2 * t))

# Initial parameters and bounds
starting_vals = [1e6, 30, 408, 1e6, 30, 436]
lb = [0, 10, 400, 0, 10, 420]
ub = [1e8, 80, 415, 1e8, 80, 452]

# Curve fitting
coef_est_r_ob, _ = curve_fit(
model_fun_r, t, s1r,
p0=starting_vals, bounds=(lb, ub)
)

coef_est_i_ob, _ = curve_fit(
model_fun_i, t, s1i,
p0=starting_vals, bounds=(lb, ub)
)

# Generate fitted data using the optimized parameters
fit_fid_r = model_fun_r(t, *coef_est_r_ob) # Unpack coef_est_r
fit_fid_i = model_fun_i(t, *coef_est_i_ob) # Unpack coef_est_i
fit_fid = fit_fid_r + 1j * fit_fid_i

```
## A.4 

Mostrare i risultati del punto precedente mediante un grafico con sovrapposto lo spettro mediato (parte reale), ottenuto dai dati sperimentali, e lo spettro risultante dalla stima dei parametri.

SOLUZIONE

<img src="./images/z_4_6/z_4_6_img_01.png" alt="Esercitazione 4.6" style="width:100%;">

*Figura 1. FID (n=10).*

<img src="./images/z_4_6/z_4_6_img_02.png" alt="Esercitazione 4.6" style="width:100%;">

*Figura 2. No Correzione di fase, no soppressione acqua.*

<img src="./images/z_4_6/z_4_6_img_03.png" alt="Esercitazione 4.6" style="width:100%;">

*Figura 3. Correzione di fase, no soppressione acqua.*

<img src="./images/z_4_6/z_4_6_img_04.png" alt="Esercitazione 4.6" style="width:100%;">

*Figura 4. No correzione di fase, con soppressione acqua.*

<img src="./images/z_4_6/z_4_6_img_05.png" alt="Esercitazione 4.6" style="width:100%;">

*Figura 5. Correzione di fase, soppressione acqua.*

<img src="./images/z_4_6/z_4_6_img_06.png" alt="Esercitazione 4.6" style="width:100%;">

*Figura 6. Fitting soggetto sano.*

<img src="./images/z_4_6/z_4_6_img_07.png" alt="Esercitazione 4.6" style="width:100%;">

*Figura 7. Fitting paziente obeso.*

| Indice | Healthy (Real + Imag) | Obese (Real + Imag) |
|---:|---:|---:|
| 0 | $1.142\times10^{7} + j\,1.116\times10^{7}$ | $1.443\times10^{7} + j\,1.261\times10^{7}$ |
| 1 | $8.000\times10^{1} + j\,8.000\times10^{1}$ | $6.400\times10^{1} + j\,5.597\times10^{1}$ |
| 2 | $4.087\times10^{2} + j\,4.088\times10^{2}$ | $3.931\times10^{2} + j\,3.936\times10^{2}$ |
| 3 | $1.201\times10^{7} + j\,1.182\times10^{7}$ | $9.507\times10^{-7} + j\,2.521\times10^{-9}$ |
| 4 | $8.000\times10^{1} + j\,8.000\times10^{1}$ | $8.000\times10^{1} + j\,8.000\times10^{1}$ |
| 5 | $4.349\times10^{2} + j\,4.348\times10^{2}$ | $4.400\times10^{2} + j\,4.456\times10^{2}$ |