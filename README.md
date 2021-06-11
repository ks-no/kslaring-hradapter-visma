.h1 KS læring hr adapter mot Visma. 
Originalt utviklet av Narvik kommune.



Kort forklart for å få løsningen til å kjøre slik den er nå: 

.env.example må kopieres til .env og verdiene må fylles ut der. 

Database må opprettes, her kan refresh_development_database.sql-scriptet brukes som utgangspunkt for å få en blank database, det ligger SQL for oppretting av tabellene. 

Ved å kjøre byggescriptet, build.ps1, så lages det en zip-fil som inneholder alt som trengs for å få det opp å kjøre på en server. 
  

Prosjektet er kodet vha. VSCode, så det ligger klart konfigurasjon for å starte det derfra: 

- KslIntegrationWorker synkroniserer inn i databasen fra API-ene. 

- KslIntegrationServer starter serveren lokalt slik at det er mulig å teste det fra utviklermaskinen. 

- jasmine kjører testene til koden. 

nodejs (https://nodejs.org/en/) må installeres på maskinen det skal utvikles på - kjør build.ps1 for å få på plass alt. 
  

container.js konfigurerer og setter opp alle avhengighetene, så de fleste endringer gjøres her hvis det skal endres på hvilke klasser som brukes for innhenting av data fra API f.eks. 

EmployeeTaxonomy og Venue er ikke implementert.   

Vi bruker AD som grunnlag for e-postadresser, siden det ikke er alt som stemmer i HRM; hvis dette skal endres må det skrives om og bytte ActiveDirectoryService i container.js:61 med den nye klassen som innhenter e-postadresser. 
  

Siden det ble nevnt at dere ikke har Person- og Organisasjonseksport-modulen til Visma, så vil det være aktuelt å skrive nye klasser som erstatter de som blir satt opp på linje 82-84 i container.js; de må hente ut dataene og etterligne strukturen som er i XML-en. 

Testene bør være et greit utgangspunkt for å finne ut av hvordan det skal være. 
  
