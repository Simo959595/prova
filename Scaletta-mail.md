# COME INVIARE UNA MAIL CON LARAVEL
1. Creare una rotta di tipo get() con la funzione nel controller che ritorna una vista
    1.1 la vista dovrà contenere un form di contatto
2. Il form dovrà avere le seguenti caratteristiche:
    - action: dove andremo a inserire la rotta che farà scattare il form
    - method: il metodo della rotta (POST)
    - @csrf token: indispensabile per non avere errore 419 (page expired)
    - gestire i vari input e inserire l'attributo name per identificarli lato backend
    - button di type submit
3. Creare la rotta di tipo post in web.php
4. creare la funzione nel controller:
    - deve accettare un oggetto di classe Request
    - salvato nelle variabili i valori che l'utente inserisce nel form e che recuperiamo dalla request
        $mail = $request->input('email');
        oppure:
        $informazioni = $request->info;
5. Creare la nostra classe mail con il comando:
    php artisan make:mail NameMail
6. Gestire la classe della mail:
    6.1 nella funzione envelope() inserire l'oggetto della mail ed eventualmente il mittente
        public function envelope(): Envelope
        {
            return new Envelope(
                from: new Address('no-reply@hackademy159.com', 'Hackademy 159'),
                subject: 'Grazie per averci contattato',
            );
        }
    6.2 Nella funzione content() gestire il percorso del file blade
        view: 'mail.invio-mail',
    6.3 Nelle viste creare la cartella mail con il file blade e inserire un template HTML con il testo della mail
7. Ritorniamo nella funzione nel controller e inviamo la mail con il nostro oggetto di classe mail creato
    Mail::to($mail)->send(new ContactMail());
8. Registrarvi su MailTrap, copiare le credenziali in chiaro, inserirli nel file .env e inserire anche la riga:
    MAIL_ENCRIPTION=tls
9. Adesso possiamo provare a inviare la prima mail.

# COME INVIARE UNA MAIL DINAMICA CON LARAVEL
1. Nella classe della mail inserire gli attributi pubblici e gestire il metodo costruttore
2. nella funzione nel controller, quando inviamo la mail dobbiamo passare anche i parametri reali che sono quelli che l'utente ha inserito nel form e che noi abbiamo salvato nelle variabili
    Mail::to('admin@hackademy.com')->send(new AdminMail($name, $mail, $informazioni));
