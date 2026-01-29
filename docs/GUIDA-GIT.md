# Guida Git per agriSuite360

## Setup completato

- **Repository GitHub**: https://github.com/FPI78/agriSuite360
- **Stack**: Python (framework da decidere)
- **IDE**: Visual Studio Code con estensioni raccomandate
- **Terminale VS Code**: usare **PowerShell** (non cmd)

### Configurazione iniziale fatta

- Repository Git locale inizializzato
- File di configurazione: `.gitignore`, `.editorconfig`, `.vscode/settings.json`, `.vscode/extensions.json`
- Remote collegato a GitHub
- Autenticazione GitHub tramite `gh auth login`

---

## Comandi Git essenziali

### Aggiornare il codice (fallo SEMPRE prima di iniziare a lavorare)

```bash
git pull
```

### Vedere lo stato del progetto

```bash
git status
```

Mostra quali file sono stati modificati, aggiunti o cancellati.

### Salvare le modifiche (commit)

```bash
git add nome-file.py          # aggiunge un file specifico
git add .                      # aggiunge TUTTI i file modificati
git commit -m "Descrizione di cosa hai fatto"
```

### Inviare le modifiche su GitHub

```bash
git push
```

### Scaricare le modifiche del tuo amico

```bash
git pull
```

---

## Workflow quotidiano

Ogni volta che lavori al progetto, segui questo ordine:

```
1. git pull                              # scarica le ultime modifiche
2. ... lavora ai tuoi file ...
3. git add .                             # prepara i file modificati
4. git commit -m "Cosa ho fatto"         # salva le modifiche in locale
5. git push                              # invia su GitHub
```

---

## Lavorare con i branch (feature branch)

I branch servono per lavorare su una funzionalità senza toccare il codice principale.

### Creare un nuovo branch

```bash
git checkout -b feature/nome-funzionalita
```

### Lavorare e committare sul branch

```bash
git add .
git commit -m "Descrizione"
```

### Pushare il branch su GitHub

```bash
git push -u origin feature/nome-funzionalita
```

(la prima volta serve `-u origin nome-branch`, dopo basta `git push`)

### Tornare sul branch principale

```bash
git checkout main
```

### Dopo che la Pull Request è stata approvata e mergiata su GitHub

```bash
git checkout main
git pull
git branch -d feature/nome-funzionalita    # cancella il branch locale
```

---

## Pull Request (PR)

Le Pull Request servono per far revisionare il codice prima di unirlo al branch principale.

1. Pusha il tuo branch su GitHub
2. Vai su https://github.com/FPI78/agriSuite360
3. Clicca "Compare & pull request" (appare in automatico)
4. Scrivi titolo e descrizione
5. L'altro revisiona, commenta, approva
6. Clicca "Merge pull request"

---

## Risolvere i conflitti

Succede quando tu e il tuo amico modificate lo stesso file nelle stesse righe.

1. Fai `git pull`
2. Git ti segnalerà i conflitti
3. Apri il file in VS Code: vedrai qualcosa tipo:

```
<<<<<<< HEAD
il tuo codice
=======
il codice del tuo amico
>>>>>>> origin/main
```

4. Scegli quale versione tenere (o combinale), cancella i marcatori `<<<`, `===`, `>>>`
5. Salva, poi:

```bash
git add .
git commit -m "Risolto conflitto su nome-file"
git push
```

---

## Regole per lavorare in due

1. **Sempre `git pull` prima di iniziare** a lavorare
2. **Commit piccoli e frequenti** con messaggi chiari
3. **Dividetevi le aree**: se uno lavora sul backend, l'altro sul frontend (meno conflitti)
4. **Usate i branch** per funzionalità nuove
5. **Non pushare mai codice rotto** sul branch `main`
6. **Usate Live Share** (estensione VS Code) per lavorare insieme sullo stesso file in tempo reale

---

## Comandi utili extra

| Comando | Cosa fa |
|---|---|
| `git log --oneline` | Cronologia dei commit in formato compatto |
| `git diff` | Mostra le modifiche non ancora committate |
| `git stash` | Mette da parte le modifiche temporaneamente |
| `git stash pop` | Riprende le modifiche messe da parte |
| `git branch` | Lista dei branch locali |
| `git branch -a` | Lista di tutti i branch (anche remoti) |

---

## Aggiungere un collaboratore al repo

1. Vai su https://github.com/FPI78/agriSuite360/settings/access
2. Clicca "Add people"
3. Cerca il tuo amico per username o email GitHub
4. Lui accetta l'invito e clona:

```bash
git clone https://github.com/FPI78/agriSuite360.git
cd agriSuite360
```

VS Code gli suggerirà automaticamente le estensioni raccomandate.
