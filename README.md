CLONARE UN PROGETTO LARAVEL
1. composer i
2. cp .env.example .env
3. php artisan key:gen
4. php artisan migrate

COMPONENTI
= astrazione di un blocco di codice che possiamo riutilizzare più volte semplicemente richiamandolo
CODICE MODULARE -> possiamo fare la nostra modifica in un unico punto, e ci saranno conseguenze a cascata 

BUNDLING DEGLI ASSETS
bundle = insieme, fascicolo, raggruppare
assets = risorse, risorse di frontend (css, js, immagini ecc)
NODE.JS - npm, package manager (node package manager)
- importare i pacchetti esterni tramite npm 
1. npm i
2. npm i bootstrap (es. installazione del singolo pacchetto)
3. elenchi delle risorse di css e js in app.css e app.js
4. dire a vite di elaborare le risorse elencate al punto 3 (@vite(['resources/css/app.css', 'resources/js/app.js']))
5. attivare vite con npm run dev