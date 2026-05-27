# 🏛️ Simulatore Investimento B&B — Via Boiardo, Roma

Simulatore single-file (React) per valutare l'acquisto del seminterrato di **Via Matteo Boiardo 12/B, Roma** come B&B / affitto.
Uso interno: Domenico × Luca.

## Come si usa
- Apri **`index.html`** col doppio click (o `open index.html`).
- Nessun build, nessun backend. Funziona offline **dopo il primo caricamento** (le librerie React/Recharts/Tailwind arrivano da CDN al primo load).
- I dati che inserisci si salvano automaticamente nel browser (localStorage). "Reset default" per azzerare.
- "Esporta PDF" usa la stampa del browser (Salva come PDF).

## Le 5 pagine
1. **Parametri** — prezzo, oneri, imposta di registro calcolata, mutuo (ammortamento francese), dati catastali.
2. **Scenari reddito** — fino a 4 scenari (B&B / affitto / misto), camere con ADR+occupazione, mix piattaforme.
3. **Costi & Tasse** — costi fissi annui, IMU calcolata, regime fiscale (cedolare 21/26%, IRPEF, forfettario).
4. **Dashboard** — KPI, cash flow cumulato, breakdown costi, confronto scenari, tabella riepilogo.
5. **Proiezioni 25 anni** — rivalutazione/inflazione, IRR, valore vs debito, what-if live.

## Formule chiave implementate
- **Rata mutuo**: ammortamento francese `M = P·[r(1+r)^n]/[(1+r)^n−1]`.
- **IMU**: `rendita × 1,05 × 160 × aliquota` (Roma seconda casa 10,6‰ → ~€1.931). Prima casa esente.
- **Imposta registro**: `rendita × 1,05 × 126 × 9%` (seconda casa) / `×115,5 × 2%` (prima casa), min €1.000.
- **Cedolare secca**: sui **ricavi LORDI** (21% o 26%), non sul profitto.
- **IRR**: bisezione su NPV con valore di uscita all'anno X (al netto ~3% costi di vendita).

## Caveat onesti
- I numeri dell'"esempio venditore" (costi operativi €27.348) **non quadrano** col dettaglio voce-per-voce: l'app calcola tutto trasparente, non forza quel totale.
- Coefficiente catastale seconda casa: usato **126** (prudenziale). Alcuni usano 120 → verifica col notaio.
- Forfettario: di norma **non applicabile** alle locazioni brevi — incluso solo con caveat.
- Tasso variabile: calcoli indicativi (il tasso cambia nel tempo).
- Seminterrato → voce manutenzione/umidità tenuta volutamente prudente.

Verifica sempre i numeri finali col commercialista prima di firmare.
