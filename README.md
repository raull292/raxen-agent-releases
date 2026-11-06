# Raxen Market Agent – versiuni publicate

Acest repository conține **doar** fișierele publicate ale aplicației Windows *Raxen Market Agent*
(agentul care citește prețurile pieței B-Zone și le trimite pe [market.raxen.ro](https://market.raxen.ro)).
Nu conține cod sursă.

## Instalare

1. Deschide pagina **[Releases](../../releases/latest)** și descarcă `RaxenMarketAgent-Setup-<versiune>.exe`.
2. Rulează instalatorul. Dacă Windows SmartScreen afișează „Windows a protejat PC-ul”, apasă
   „Mai multe informații” → „Rulează oricum” (instalatorul nu este încă semnat cu certificat de cod).
3. Instalarea se face per utilizator, fără drepturi de administrator, peste versiunea existentă;
   setările, baza de date locală și contul rămân.

Varianta portabilă (`RaxenMarketAgent-Portable-<versiune>.zip`) rulează din orice folder, fără instalare,
dar nu se actualizează singură.

## Actualizări automate

Începând cu versiunea 0.4.4, agentul instalat verifică singur acest repository
(`releases/latest/download/manifest.json`), anunță versiunea nouă și o instalează cu un click,
cu repornire automată. Fiecare release conține:

| Fișier | Rol |
|---|---|
| `RaxenMarketAgent-Setup-<versiune>.exe` | instalatorul Windows (Inno Setup, per utilizator) |
| `RaxenMarketAgent-Portable-<versiune>.zip` | varianta portabilă |
| `manifest.json` | manifestul de actualizare, semnat Ed25519 cu cheia Raxen (verificată de agent înainte de orice instalare) |
| `SHA256SUMS.txt` | amprentele SHA-256 ale fișierelor |
| `RELEASE-NOTES.md` | notele versiunii |

Agentul refuză orice manifest nesemnat, semnat cu altă cheie, mai vechi decât versiunea instalată
sau care indică o descărcare de pe alt domeniu, și verifică SHA-256 al instalatorului înainte de a-l porni.
