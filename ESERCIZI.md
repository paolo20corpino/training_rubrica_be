# 1.	Implementare un metodo getListTelefonoByIdPersona che dato in input un idPersona restituisca una lista contenente i numeri di telefono della persona.

  - L'id della persona deve essere passato come **@PathVariable**

  **1.1	Se l'id persona non esiste restituire una lista vuota.**

# 2.	Implementare un metodo getPersoneByNumeroTelefono che dato in input un numero di telefono restituisca la lista delle persone al numero di telefono dato.

  **2.1	Per ogni persona deve essere mostrato nome, cognome, città indirizzo e e-mail (creare un oggetto [nome]RTO apposito)**

  **2.2	Il numero di telefono deve essere passato come @RequestParam**

  - **IMPORTANTE:** SOLO le classi Service e Repository possono lavorare con oggetti Entity quindi le informazioni associate alla 
    persona dovranno essere inserite in un oggetto custom (RTO) che passerà attraverso il Facade per poi essere restituito al controller
    Per convenzione quando costruiamo un nuovo oggetto da restituire il nome della classe avrà la struttura 
    [nomeClasse]RTO (RTO è acronimo di Return Type Object)

  **2.3	 Se il numero di telefono non esiste restituire una lista vuota.**

# 3.	Implementare un metodo getAllPersone che restituisca una lista contenente tutte le persone e per ciascuna persona tutte le informazioni e una lista con i suoi numeri di telefono.

# 4.	Implementare un metodo getPersonaById che dato in input un idPersona restituisca una oggetto contenente tutte le informazioni della persona e una lista con i suoi numeri di telefono.

  **4.1	 Se l'id persona non esiste restituire una lista vuota.**

# 5.	Implementare un metodo getPersoneByIds che data in input una lista di idPersona restituisca una lista delle persone corrispondenti.

  - Per ciascuna persona indicare Nome e Cognome e una lista con i suoi numeri di telefono.
  - Potrebbe esservi utile far restituire direttamente alla query l’oggetto RTO

# 6.	Implementare un metodo findPersoneByNomeAndCognome che prenda in input un oggetto contenente nome e cognome e che restituisca una lista delle persone trovate. Per ciascuna persona riportare tutte le informazioni e una lista con i suoi numeri di telefono.
  - **IMPORTANTE:** utilizzare l’annotation @RequestBody e di conseguenza utilizzare una POST

# 7.	Implementare un metodo POST savePersona che date in input tutte le informazioni relative alla persona ne effettui il salvataggio a DB.

  **7.1	Inserire la validazione dell’oggetto in input sfruttando l’annotation @Validate. Prevedere i controlli su: campi null, lunghezza dei campi, validazione CF tramite regex.**

# 8.	Implementare un metodo saveNumTelefonoPersona che dati in input una lista di numeri di telefono e l’id della Persona salvi a DB dell’associazione dei numeri di telefono della persona data.

# 9.	Implementare un metodo modificaPersona che date in input tutte le informazioni relative alla persona ne effettui il salvataggio a db.
  - Utilizzare l'annotation **@PutMapping**
  - **IMPORTANTE:** l’oggetto in input prevede tutte le informazioni associabili alla persona, ma saranno popolate solo le informazioni che sono state
  modificate, le altre saranno null; I campi non modificati devono restare inalterati.

  **9.1  Inserire la validazione dell’oggetto in input per i campi valorizzati. Sfruttare classe CheckErrors per effettuare i controlli.**

# 10.	Implementare un metodo modificaNumTelefonoPersona che dati in input l’id della persona e una lista di numeri di telefono elimini i numeri non più presenti in lista, aggiorni i numeri modificati e salvi i nuovi numeri aggiungi 
- Se il numero che si sta inserendo è già presente a DB salvarlo con l’id associato, se il numero di telefono cancellato è associato a più utenti rimuoverlo dall’associativa ma non rimuoverlo dalla tabella telefono.

# 11.	Implementare un metodo deleteNumTelefono che dato un numero di telefono in input lo rimuova dal DB.
  - Utilizzare l'annotation **@DeleteMapping**

# 12.	Implementare un metodo deletePersona che dato in input l’id della persona ne effettui la cancellazione a DB compresi i suoi numeri di telefono, se non condivisi con altre persone.

# 13.	Implementare un metodo modificaNumTelefonoPersonaMessaggi dati in input l’id della persona e una lista di numeri di telefono modifica dei numeri di telefono di un utente. 
- Se l’utente condivide dei numeri di telefono con altri utenti tali numeri non possono essere modificati.
- Modificare solo quelli associati all'utente e restituire una lista di messaggi per ogni numero non modificabile indicando il numero e a quali altri utenti è associato. In caso sia possibile modificare tutti i numeri restituire un messaggio di avvenuta modifica.
