# Individuell loggbok – Webbshopprojektet

> **Obs:** Loggboken är sammanställd utifrån det arbete som finns dokumenterat i mina samtal och uppgifter. Lägg till eller rätta datum om jag arbetade med något annat den dagen. Veckorna nedan är kalenderveckor och ska inte tolkas som officiella sprintnummer.

## Daglig loggbok

### Fredag 25 september 2026

**Vad jag arbetade med**
- Arbetade med frontendens koppling till Product Service.
- Arbetade med `productService.ts`, funktionen `getProducts()` och `ProductsPage.tsx` för att hämta och visa produkter.

**Resultat**
- Lade grunden för att frontend skulle kunna hämta produkter från backend.

### Måndag 28 september 2026

**Vad jag arbetade med**
- Fortsatte med produktvisningen och frontendens hantering av resultat från Product Service.
- Arbetade med `ProductsPage.tsx`, `ProductCard.tsx` och `productService.ts`.
- Arbetade med hur tomma produktlistor och fel vid hämtning skulle visas.

**Resultat**
- Kom vidare med produktvisningen och hanteringen av tomma resultat och fel.

### Tisdag 29 september 2026

**Vad jag arbetade med**
- Började arbeta med kundvagnens grundläggande funktioner.
- Arbetade med `Cart` och kopplingen mellan produktsidan och kundvagnen.

**Resultat**
- Lade grunden för att kunna lägga produkter i kundvagnen och visa kundvagnens innehåll.

### Onsdag 30 september 2026

**Vad jag arbetade med**
- Fortsatte utvecklingen av kundvagnen.
- Arbetade med antal produkter och beräkningar av radpris och totalsumma.

**Problem och resultat**
- Arbetade med att hantera flera exemplar av samma produkt och se till att antalet och priserna uppdaterades korrekt.

### Torsdag 1 oktober 2026

**Vad jag arbetade med**
- Fortsatte att testa kundvagnens grundfunktioner.
- Arbetade med att öka och minska antal, ta bort produkter och visa eller dölja kundvagnen.
- Kontrollerade visningen av radpriser, totalsumma och tom kundvagn.

**Resultat**
- Grundfunktionerna för kundvagnen och prisberäkningarna var klara och testade.

### Tisdag 6 oktober 2026

**Vad jag arbetade med**
- Började arbeta med att spara kundvagnens innehåll i `sessionStorage`.
- Arbetade med `orderService.ts` och typen `CreateOrderRequest` inför kopplingen till Order Service.

**Resultat**
- Kom vidare med att bevara kundvagnens innehåll under sessionen och förbereda beställningsflödet.

### Onsdag 7 oktober 2026

**Vad jag arbetade med**
- Fortsatte med utcheckningen och kopplingen mellan kundvagnen och Order Service.
- Arbetade med `handleCheckout()` i `ProductsPage.tsx`.
- Kopplade utcheckningsfunktionen till `Cart` genom `onCheckout`.
- Arbetade med vad som ska hända när en beställning lyckas eller misslyckas.

**Resultat**
- Frontend fick en tydligare funktion för att skicka beställningen till Order Service och hantera resultatet.

### Fredag 9 oktober 2026

**Vad jag arbetade med**
- Undersökte hur Order Service startas och är konfigurerad.
- Granskade dess `Dockerfile` och försökte förstå hur tjänstens beroenden, bland annat RabbitMQ, var konfigurerade.

**Resultat**
- Fick en bättre bild av hur Order Service startas och vad som kunde behöva undersökas vid problem med utcheckningen.

### Måndag 12 oktober 2026

**Vad jag arbetade med**
- Arbetade vidare med lagersaldot och utcheckningen.
- Ändrade `ProductCard.tsx` så att produkter med lagersaldo noll fortfarande visas men markeras som slutsålda.
- Inaktiverade köpknappen för slutsålda produkter.
- Undersökte varför utcheckningen gav HTTP 500 när kunden försökte beställa fler varor än vad som fanns i lager.

**Problem och resultat**
- Identifierade att Product Service svarade med HTTP 400 när lagret inte räckte, men att Order Service skickade HTTP 500 till frontend.

### Tisdag 13 oktober 2026

**Vad jag arbetade med**
- Förbättrade felhanteringen i frontend och Order Service.
- Ändrade `orderService.ts` så att frontend kan läsa felmeddelanden från backend.
- Ändrade `catch`-blocket i `handleCheckout()` så att felmeddelandet visas för användaren.
- Skapade `GlobalExceptionHandler.java` i Order Service för att hantera felet när Product Service rapporterar otillräckligt lager.

**Problem och lösning**
- Tidigare visades ett generellt HTTP 500-fel när lagersaldot inte räckte.
- Felhanteraren kontrollerar svaret från Product Service och returnerar HTTP 409 Conflict med ett begripligt meddelande när felet gäller otillräckligt lager.

**Resultat**
- Testade utcheckningen igen och kontrollerade att användaren får en tydlig varning och att kundvagnen behålls om beställningen misslyckas.

### Onsdag 14 oktober 2026

**Vad jag arbetade med**
- Följde upp och testade funktionerna för slutsålda produkter och utcheckning.
- Kontrollerade att slutsålda produkter fortfarande visas, att köpknappen är inaktiverad och att kunden får en varning om lagersaldot inte räcker.

**Resultat**
- Bekräftade att funktionerna fungerade vid testning och att kundvagnen behålls när beställningen misslyckas.

### Fredag 16 oktober 2026

**Vad jag arbetade med**
- Började arbeta med Gateway-delen av webbshopprojektet.
- Granskade `pom.xml` och lade till beroendet för Spring Cloud Gateway Server Web MVC.
- Kontrollerade konfigurationen i `application.properties`, inklusive port 9003 och routning till Auth Server, Product Service och Order Service.
- Använde miljövariabler med lokala standardadresser för backend-tjänsterna.

**Problem och resultat**
- Körning av Maven-kommandot `compile` slutfördes med `BUILD SUCCESS`.
- Gateway-applikationen startade lokalt utan fel.
- Vid den första kontrollen var routningen till respektive backend ännu inte verifierad genom separata anrop. Senare arbete med autentisering via Gateway verifierade delar av flödet, bland annat inloggning, session och utloggning. Alla routes till Product Service och Order Service är inte dokumenterade som fullständigt verifierade här.


### Fredag 23 oktober 2026

**Vad jag arbetade med**
- Arbetade med FE-36, som i den uppdaterade Product Backlog är markerad som klar: återställning av inloggad användare efter att sidan laddas om.
- Städade frontendkod kopplad till autentisering i `authService.ts`, `apiClient.ts`, `ProtectedRoute.tsx`, `Header.tsx`, `LoginForm.tsx` och `AuthContext.tsx`.
- Anpassade frontend till autentisering med HttpOnly-cookie genom att använda `credentials: "include"` och hämta användarinformation från Gatewayns `/auth/me` i stället för att läsa en JWT från frontendens lagring.
- Committade ändringarna på branchen `feature/keep-login`.

**Problem och lösning**
- Säkerställde att `AuthContext` återställer användaren vid appstart och att `ProtectedRoute` väntar medan sessionen kontrolleras.
- Uppdaterade inloggningsformuläret så att `AuthContext` får användarinformationen direkt efter lyckad inloggning.
- Rensade utloggningen så att användaren tas bort från Reacts autentiseringstillstånd och navigeras till `/login`.

**Resultat och testning**
- Testade att `GET /auth/me` returnerar användarens `subject`, `roles` och `expiresIn` när sessionen är giltig.
- Laddade om `/welcome` med F5 och verifierade att välkomstmeddelandet och rollen `USER` visas även efter omladdning.
- Testade utloggning och att direkt navigering till `/products` efter utloggning skickar användaren till `/login`. Anropet till `/auth/me` svarade då `401 Unauthorized`, vilket var förväntat när sessionen saknas.
- Administratörsåtkomst fungerar ännu inte som avsett och ska undersökas separat med gruppen. Duplicerade routes i `App.tsx` identifierades och ska också tas upp med gruppen innan de ändras.


---

## Veckovisa sammanfattningar

### Vecka 39 – 21–27 september 2026

**Vad jag arbetade med**
Jag började arbeta med integrationen mellan frontend och Product Service. Jag arbetade med `productService.ts`, `getProducts()` och `ProductsPage.tsx`.

**Problem och resultat**
Jag arbetade med att få frontend att hämta och visa produkter från backend. Det lade grunden för produktvisningen i webbshoppen.

### Vecka 40 – 28 september–4 oktober 2026

**Vad jag arbetade med**
Jag fortsatte med produktvisningen och utvecklade kundvagnens grundfunktioner. Jag arbetade med `ProductCard`, `ProductsPage` och `Cart`, inklusive att lägga till produkter, ändra antal och beräkna radpriser och totalsumma.

**Problem och resultat**
Jag arbetade med att hålla antalet och prisberäkningarna korrekta när kundvagnen ändrades. Grundfunktionerna för kundvagnen blev klara och testades.

### Vecka 41 – 5–11 oktober 2026

**Vad jag arbetade med**
Jag arbetade med att spara kundvagnen i `sessionStorage` och skicka beställningar till Order Service. Jag arbetade med `orderService.ts`, `CreateOrderRequest`, `handleCheckout()` och kopplingen mellan `ProductsPage` och `Cart`. Jag undersökte även Order Services konfiguration och beroenden.

**Problem och resultat**
Jag kom vidare med integrationen mellan frontend och Order Service och undersökte problem i beställningsflödet.

### Vecka 42 – 12–18 oktober 2026

**Vad jag arbetade med**
Jag fokuserade på lagerhantering och felhantering vid utcheckning. Jag ändrade `ProductCard.tsx` så att slutsålda produkter visas men inte kan läggas i kundvagnen. Jag arbetade också med felhantering i `orderService.ts`, `handleCheckout()` och den nya `GlobalExceptionHandler.java` i Order Service.

**Problem och resultat**
När kunden försökte beställa fler produkter än vad som fanns i lager svarade Product Service med HTTP 400, medan Order Service skickade HTTP 500 till frontend. Jag förbättrade felhanteringen så att Order Service returnerar HTTP 409 Conflict med ett begripligt meddelande vid otillräckligt lager. Jag testade sedan att varningen visas och att kundvagnen behålls när beställningen misslyckas.


### Vecka 43 – 19–25 oktober 2026

**Vad jag arbetade med**
Jag arbetade vidare med autentisering genom Gateway och frontendens återställning av inloggad användare. Jag städade autentiseringsrelaterad kod, kopplade `LoginForm` och `Header` till `AuthContext` och kontrollerade att skyddade routes väntar tills sessionen har kontrollerats. I den uppdaterade Product Backlog är FE-34, FE-35 och FE-36 markerade som klara.

**Problem och resultat**
Jag verifierade att användaren stannar kvar på `/welcome` efter omladdning och att `/auth/me` returnerar användarinformation när sessionen är giltig. Efter utloggning skickas användaren till `/login`, och `/auth/me` svarar `401 Unauthorized` när sessionen saknas. Ändringarna för FE-36 är committade på `feature/keep-login`. Administratörsåtkomst och duplicerade routes i `App.tsx` återstår att diskutera och hantera separat.

---

## Samarbete och agilt arbetssätt

Vi arbetar i grupp med en återkommande rutin. På måndagar har vi sprintplanering där vår Scrum Master går igenom vad vi ska arbeta med och vem som ansvarar för vad. Under resten av veckan har vi ett möte om dagen för att stämma av arbetet och diskutera hur vi ligger till. På fredagar är det planerat att vi ska demonstrera arbetet för läraren.

Mitt eget arbete har framför allt varit inriktat på produktvisning, kundvagn och kopplingen mellan frontend och Order Service. Jag har delat upp utvecklingen i mindre steg och testat funktionerna efter hand. När problem har uppstått har jag undersökt orsaken och arbetat med att förbättra lösningen.

Jag har inte tillräckligt med dokumentation för att säkert ange vilka sprint reviews eller retrospektiv som genomförts. Därför har jag inte registrerat sådana aktiviteter som genomförda i denna loggbok.
