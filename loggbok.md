# Individuell loggbok – Webbshopprojektet

> **Obs:** Loggboken är sammanställd utifrån det arbete som finns dokumenterat i mina samtal och uppgifter. Lägg till eller rätta datum om jag arbetade med något annat den dagen. Veckorna nedan är kalenderveckor och ska inte tolkas som officiella sprintnummer.

## Daglig loggbok

### Tisdag 22 september 2026

**Vad jag fick och arbetade med**

- Fick kursmaterial inför det fortsatta arbetet med webbshopprojektet.
- Fick en genomgång av React Router, inklusive routes, navigering och skyddade routes.
- Fick material om Sprint Review och hur sprintens resultat ska demonstreras.
- Gick igenom riktlinjerna för fredagens Sprint Review, inklusive tidsplan, live-demo och feedback.

**Resultat**

- Fick en bättre förståelse för hur React Router används för navigering och skyddade sidor.
- Fick information om hur gruppen ska förbereda och genomföra Sprint Reviews.

### Onsdag 23 september 2026

**Vad jag arbetade med**

- Började arbeta med webshopprojektet i grupp 1, där jag ansvarar för Product Service.
- Gick igenom hur frontend ska kommunicera med Product Service.
- Arbetade med säkerhetskonfigurationen i `SecurityConfig`.
- Började undersöka och konfigurera CORS för att tillåta kommunikation mellan backend och frontend.
- Gick igenom tillåtna frontendadresser, HTTP-metoder och headers.
- Diskuterade FE-11, som handlar om att skapa en separat produktsida och hämta produkter från Product Service genom `GET /products`.

**Problem och resultat**

- Upptäckte att den befintliga säkerhetskonfigurationen främst hanterade JWT och roller.
- Gick igenom hur CORS behöver konfigureras separat med `CorsConfigurationSource`.
- Fick en bättre förståelse för hur frontend och Product Service ska kunna kommunicera på ett säkert sätt.

### Torsdag 24 september 2026

**Vad jag arbetade med**

- Fortsatte arbetet med Product Service och dess säkerhetskonfiguration.
- Arbetade med FE-06, som handlade om att konfigurera CORS.
- Uppdaterade och kontrollerade `SecurityConfig`.
- Konfigurerade tillåtna frontendadresser för localhost på portarna 5173, 5174 och 5175.
- Gick igenom tillåtna HTTP-metoder och headers.
- Kontrollerade att CORS fungerar tillsammans med Spring Security och JWT-autentisering.
- Gick igenom befintlig funktionalitet i Product Service, bland annat `GET /products`.

**Problem och resultat**

- Kontrollerade att CORS-konfigurationen tillåter frontendens anrop till backend.
- Säkerställde att nödvändiga HTTP-metoder och headers tillåts.
- FE-06 för CORS markerades som färdig.
- Diskuterade nästa steg för integrationen mellan frontend och Product Service.

### Fredag 25 september 2026

**Vad jag arbetade med**

- Arbetade med frontendens koppling till Product Service.
- Gick igenom `productService.ts` och funktionen `getProducts()` för att hämta produkter från backend.
- Arbetade med API-adressen via `VITE_API_PRODUCT_SERVICE_URL`.
- Gick igenom hur JWT-token hämtas och skickas med i frontendens API-anrop genom `Authorization`-headern.
- Började bygga `ProductsPage.tsx` för att visa produkter i frontend.
- Arbetade med att koppla produktsidan till React Router via routen `/products`.

**Problem och resultat**

- Upptäckte att `getProducts()` behövde läsa JSON-svaret från backend och returnera produktinformationen.
- Lade grunden för frontendens integration med Product Service och för den kommande produktvisningen.

### Måndag 28 september 2026

**Vad jag arbetade med**

- Fortsatte med produktvisningen och frontendens hantering av resultat från Product Service.
- Arbetade med `ProductsPage.tsx`, `ProductCard.tsx` och `productService.ts` för att hantera hämtning och presentation av produkter.
- Gick igenom hur produkterna skulle visas i frontend och hur informationen från Product Service skulle presenteras.
- Arbetade med hur tomma produktlistor skulle hanteras när det inte finns några produkter att visa.
- Undersökte hur fel vid hämtning av produkter skulle hanteras och visas för användaren.

**Resultat**

- Kom vidare med produktvisningen och kopplingen mellan frontend och Product Service.
- Arbetet lade grunden för att kunna presentera produkter på ett tydligt sätt.
- Förbättrade hanteringen av tomma resultat och fel vid hämtning av produkter.

### Tisdag 29 september 2026

**Vad jag arbetade med**

- Började arbeta med kundvagnens grundläggande funktioner.
- Arbetade med `Cart` och kopplingen mellan produktsidan och kundvagnen.
- Arbetade med `ProductsPage` för att hantera kundvagnens innehåll med hjälp av React state.
- Kopplade ihop `ProductCard` med funktionen `addToCart()` så att produkter kunde läggas till från produktsidan.
- Arbetade med att visa och dölja kundvagnen.
- Började implementera hantering av produkter i kundvagnen, inklusive kontroll av produktens lagersaldo.
- Arbetade med hur kundvagnen skulle visa produkter och hantera ett tomt innehåll.

**Resultat**

- Lade grunden för att kunna lägga produkter i kundvagnen och visa kundvagnens innehåll.
- Skapade kopplingen mellan `ProductCard`, `ProductsPage` och `Cart`.
- Kundvagnen kunde visa produkter och hantera när den var tom.
- Påbörjade funktionaliteten för att hantera produkter och deras antal i kundvagnen.

### Onsdag 30 september 2026

**Vad jag arbetade med**

- Fortsatte utvecklingen av kundvagnen.
- Arbetade med antal produkter och beräkningar av radpris och totalsumma.
- Arbetade med hur kundvagnen skulle hantera flera exemplar av samma produkt utan att skapa separata rader för varje exemplar.
- Gick igenom beräkningen av radpriset genom att multiplicera produktens pris med antalet.
- Arbetade med beräkningen av kundvagnens totala pris genom att summera alla produkters radpriser.
- Fortsatte med funktionaliteten för att öka och minska antalet produkter i kundvagnen.

**Problem och resultat**

- Arbetade med att hantera flera exemplar av samma produkt och se till att antalet och priserna uppdaterades korrekt.
- Implementerade beräkningar för radpris och totalsumma baserat på produktens pris och antal.
- Säkerställde att samma produkt skulle samlas på en rad i kundvagnen och att antalet skulle uppdateras.
- Beräkningarna för priserna fanns på plats, men visningen av produktpris och radpris behövde fortfarande kompletteras.

### Torsdag 1 oktober 2026

**Vad jag arbetade med**

- Fortsatte att testa kundvagnens grundfunktioner.
- Arbetade med att öka och minska antal, ta bort produkter och visa eller dölja kundvagnen.
- Kontrollerade visningen av produktpriser, radpriser, totalsumma och tom kundvagn.
- Testade att flera exemplar av samma produkt visades på en gemensam rad i kundvagnen.
- Kontrollerade att antalet uppdaterades korrekt när jag använde knapparna för att öka och minska kvantiteten.
- Testade att produkten togs bort från kundvagnen när antalet minskades till noll.
- Kontrollerade att det inte gick att lägga till fler produkter än vad som fanns i lager.

**Resultat**

- Grundfunktionerna för kundvagnen och prisberäkningarna var klara och testade.
- Beräkningen av radpris och totalsumma fungerade korrekt.
- Kundvagnen hanterade både flera exemplar av samma produkt och borttagning av produkter.
- Testerna för FE-15 och FE-16 såg bra ut och funktionerna kunde markeras som klara.

### Tisdag 6 oktober 2026

**Vad jag arbetade med**

- Började arbeta med att spara kundvagnens innehåll i `sessionStorage`.
- Arbetade med `orderService.ts` och typen `CreateOrderRequest` inför kopplingen till Order Service.
- Arbetade med FE-21, som omfattade att bevara kundvagnens innehåll och skicka en beställning till Order Service.
- Gick igenom hur kundvagnens produkter skulle omvandlas till rätt format innan de skickades till backend.
- Arbetade med att skapa en funktion för att skicka beställningar med HTTP POST.
- Förberedde `handleCheckout()` i `ProductsPage` för att hantera beställningsflödet.
- Arbetade med hur kundvagnen skulle kontrolleras innan en beställning skickades och hur resultatet skulle hanteras.

**Resultat**

- Kom vidare med att bevara kundvagnens innehåll under sessionen och förbereda beställningsflödet.
- Skapade grunden för att skicka beställningar till Order Service genom `orderService.ts`.
- Anpassade beställningsinformationen till `CreateOrderRequest`, som innehåller produktens ID och antal.
- Förberedde hantering av lyckade beställningar och fel som kan uppstå vid beställning.

### Onsdag 7 oktober 2026

**Vad jag arbetade med**

- Fortsatte med utcheckningen och kopplingen mellan kundvagnen och Order Service.
- Arbetade med `handleCheckout()` i `ProductsPage.tsx`.
- Kopplade utcheckningsfunktionen till `Cart` genom `onCheckout`.
- Arbetade med vad som ska hända när en beställning lyckas eller misslyckas.
- Använde `orderService.ts` för att skicka beställningsinformationen till Order Service.
- Arbetade med att skicka produkt-ID och antal enligt strukturen i `CreateOrderRequest`.
- Gick igenom hur kundvagnens innehåll skulle hanteras efter att beställningen skickats.
- Arbetade med återkoppling till användaren så att resultatet av beställningen blir tydligt.

**Resultat**

- Frontend fick en tydligare funktion för att skicka beställningen till Order Service och hantera resultatet.
- `handleCheckout()` kopplades till kundvagnens utcheckningsfunktion genom `onCheckout`.
- Beställningsflödet fick en tydligare struktur för hantering av lyckade och misslyckade anrop.
- Arbetet med kopplingen mellan kundvagnen och Order Service gick vidare.

### Fredag 9 oktober 2026

**Vad jag arbetade med**

- Undersökte hur Order Service startas och är konfigurerad.
- Granskade tjänstens `Dockerfile` och försökte förstå hur tjänsten byggs och startas.
- Undersökte hur Order Services beroenden var konfigurerade, bland annat RabbitMQ.
- Gick igenom hur Order Service kommunicerar med RabbitMQ och vilken roll meddelandekön har i systemet.
- Försökte förstå hur konfigurationen av tjänstens olika beroenden påverkar uppstarten och beställningsflödet.
- Undersökte möjliga orsaker till problem som kunde påverka utcheckningen från frontend.

**Resultat**

- Fick en bättre bild av hur Order Service startas och hur dess Docker-konfiguration fungerar.
- Fick en bättre förståelse för RabbitMQ och hur det används tillsammans med Order Service.
- Identifierade vilka delar av tjänstens konfiguration och beroenden som behövde undersökas vidare vid problem med utcheckningen.

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

### Måndag 26 oktober 2026

**Vad jag arbetade med**

- Påbörjade arbetet med FE-43 under Sprint 7.
- Planerade att skapa README-filer för webshopprojektets olika repositories.
- Gick igenom vilken information som behövde dokumenteras för Auth Service, Product Service, Order Service, Gateway och Frontend.
- Planerade dokumentation av projektens ansvarsområden, tekniker, databaser, miljövariabler, portar och instruktioner för uppstart.

**Resultat**

- Lade grunden för dokumentationsarbetet för hela webshopprojektet.
- Identifierade vilken information som behövde finnas med i respektive README-fil.

### Tisdag 27 oktober 2026

**Vad jag arbetade med**

- Fortsatte arbetet med FE-36 för att återställa inloggad användare efter att sidan laddas om.
- Arbetade med autentiseringsflödet mellan frontend, Gateway och Auth Service.
- Undersökte hur `/auth/me` används för att kontrollera om användarens session fortfarande är giltig.
- Arbetade med `AuthProvider` och `ProtectedRoute` i frontend.
- Lade till `AuthProvider` i `main.tsx`.
- Arbetade med Gatewayens routning till Product Service och undersökte problem med produktanrop.

**Problem och lösning**

- Undersökte problem med att hämta produkter genom Gateway.
- Upptäckte att routningen använde `/api/products` i stället för `/products`.
- Korrigerade routningen och testade att produktlistan kunde hämtas.
- Undersökte även ett HTTP 405-fel vid POST-anrop mot `/gateway/products`.

**Resultat och testning**

- Testade administratörsinloggning, återställning av session efter F5, rollbaserad åtkomst och utloggning. Samtliga fyra tester fungerade.
- Verifierade att Gateway kunde hämta produkter från Product Service.
- Kom vidare med autentiseringsflödet och integrationen mellan frontend och backend.

### Onsdag 28 oktober 2026

**Vad jag arbetade med**

- Arbetade med dokumentationen för Auth Server och Product Service.
- Gick igenom projektens konfigurationer, beroenden och miljövariabler.
- Kontrollerade databasinställningarna för respektive tjänst.
- Undersökte hur SQL-initialiseringen fungerar i Product Service.
- Kontrollerade vilka filer och konfigurationsinställningar som behövde beskrivas i README-filerna.

**Resultat**

- Kom vidare med dokumentationen för Auth Server och Product Service.
- Fick en tydligare bild av hur respektive backendtjänst är konfigurerad och startas.

### Torsdag 29 oktober 2026

**Vad jag arbetade med**

- Arbetade vidare med FE-43 och dokumentationen för webshopprojektets backendtjänster.
- Färdigställde och sparade README-filerna för Auth Service, Product Service och Order Service.
- Gick igenom Gateway-projektets konfiguration och kontrollerade att Maven Wrapper-filerna `mvnw` och `mvnw.cmd` finns.
- Dokumenterade Gatewayens port, miljövariabler och cookie-inställningar.
- Påbörjade genomgången av `GatewayController` för att kontrollera vilka API-endpoints som skulle dokumenteras.

**Resultat**

- README-filerna för Auth Service, Product Service och Order Service blev färdiga och sparade.
- Kom vidare med dokumentationen för Gateway och dess konfiguration.

### Fredag 30 oktober 2026

**Vad jag arbetade med**

- Färdigställde arbetet med att spara kundvagnen separat för varje inloggad användare.
- Använde `sessionStorage` och användarens `subject` för att skilja kundvagnarna åt.
- Arbetade med återställning av kundvagnen efter siduppdatering och återinloggning.
- Testade kundvagnens funktionalitet med olika användare.
- Uppdaterade README-filerna för Frontend, Gateway och Order Service.
- Dokumenterade frontendens autentisering, kundvagn och beställningsflöde.
- Uppdaterade Gateway-dokumentationen med order-endpoints och kommunikation med Order Service.
- Kompletterade Order Service-dokumentationen med rollbaserad åtkomst och orderhantering.

**Problem och lösning**

- Tidigare kunde olika användare få tillgång till samma sparade kundvagn.
- Ändrade lagringen så att varje användare får en separat kundvagn baserad på sitt `subject`.

**Resultat och testning**

- Testade att kundvagnen återställs efter F5.
- Testade att olika användare har separata kundvagnar.
- Verifierade att kundvagnen återställs efter utloggning och återinloggning.
- Samtliga tester av kundvagnens nya funktionalitet fungerade.
- Uppdaterade och sparade README-filerna för Frontend, Gateway och Order Service.
- README-dokumentationen för samtliga sex delar av webshopprojektet är nu uppdaterad.

---

## Veckovisa sammanfattningar

### Vecka 39 – 21–27 september 2026

**Vad jag arbetade med**

Den här veckan påbörjade jag arbetet med webbshopprojektet tillsammans med min grupp. Jag fick ansvar för Product Service och började undersöka hur frontend och backend skulle kommunicera med varandra.

Jag fick även kursmaterial om React Router, navigering och skyddade routes samt hur vi skulle arbeta med Sprint Reviews och demonstrationer.

Jag arbetade med säkerhetskonfigurationen i Product Service och CORS (Cross-Origin Resource Sharing). Jag gick igenom hur frontendens olika localhost-adresser skulle tillåtas kommunicera med backend, vilka HTTP-metoder och headers som behövde tillåtas samt hur CORS fungerar tillsammans med Spring Security och JWT.

Jag påbörjade även arbetet med FE-11, som handlar om produktvisning i frontend. Jag arbetade med `productService.ts`, funktionen `getProducts()` och `ProductsPage.tsx` för att skapa kopplingen mellan frontend och Product Service. Jag gick även igenom hur API-anropet använder JWT-token för autentisering.

**Problem och resultat**

Under arbetet med CORS behövde jag förstå hur konfigurationen samverkar med Spring Security och JWT. Jag gick igenom och konfigurerade `CorsConfigurationSource` i `SecurityConfig` för att tillåta kommunikation från frontend. CORS-uppgiften FE-06 färdigställdes.

Jag började även bygga grunden för produktvisningen i frontend. Arbetet med `productService.ts` och `ProductsPage.tsx` lade grunden för att kunna hämta och visa produkter från Product Service.

Veckan gav mig en bättre förståelse för hur frontend, backend, CORS och JWT samverkar i webbshopprojektet.

### Vecka 40 – 28 september–4 oktober 2026

**Vad jag arbetade med**

Jag fortsatte med produktvisningen och utvecklade kundvagnens grundfunktioner. Jag arbetade med `ProductCard`, `ProductsPage` och `Cart`, inklusive kopplingen mellan produktsidan och kundvagnen.

Jag arbetade med funktioner för att lägga till produkter, öka och minska antal samt ta bort produkter från kundvagnen. Jag utvecklade även hanteringen av flera exemplar av samma produkt så att de kunde visas på en gemensam rad.

Jag arbetade med prisberäkningar där radpriset beräknas utifrån produktens pris och antal. Jag fortsatte även med beräkningen av kundvagnens totala summa. Utöver detta arbetade jag med visningen av kundvagnen, inklusive hantering av tom kundvagn.

**Problem och resultat**

Under utvecklingen behövde jag säkerställa att antalet produkter och prisberäkningarna uppdaterades korrekt när innehållet i kundvagnen ändrades. Jag arbetade även med att kontrollera produktens lagersaldo så att det inte gick att lägga till fler exemplar än vad som fanns tillgängligt.

Jag testade kundvagnens funktioner, bland annat att lägga till produkter, ändra antal, ta bort produkter och kontrollera prisberäkningarna.

Grundfunktionerna för kundvagnen blev klara och testades. Arbetet med FE-15 och FE-16 gick framåt och kundvagnen kunde hantera produkter, antal och totalsumma.

### Vecka 41 – 5–11 oktober 2026

**Vad jag arbetade med**

Jag arbetade med att spara kundvagnens innehåll i `sessionStorage` och utveckla utcheckningsflödet för att kunna skicka beställningar till Order Service.

Jag arbetade med `orderService.ts` och typen `CreateOrderRequest` för att förbereda och skicka beställningsinformationen från frontend till backend. Jag fortsatte även med `handleCheckout()` i `ProductsPage.tsx` och kopplingen mellan `ProductsPage` och `Cart` genom funktionen `onCheckout`.

En del av arbetet handlade om att hantera vad som skulle hända efter att en beställning skickats, både när beställningen lyckades och när ett fel uppstod. Jag undersökte även hur kundvagnens innehåll skulle hanteras efter en genomförd beställning.

Mot slutet av veckan undersökte jag Order Services uppstart och konfiguration. Jag granskade dess `Dockerfile` och försökte förstå hur tjänstens beroenden fungerade, framför allt RabbitMQ och dess roll i beställningsflödet.

**Problem och resultat**

Under arbetet behövde jag undersöka hur frontend skulle kommunicera med Order Service och hur beställningsinformationen skulle skickas i rätt format. Jag kom vidare med integrationen genom att skapa en tydligare struktur för utcheckningen och hanteringen av beställningsresultatet.

Jag undersökte även problem som kunde påverka beställningsflödet genom att granska Order Services konfiguration, Docker-uppstart och beroenden. Arbetet med RabbitMQ gav mig en bättre förståelse för hur tjänsterna kommunicerar med varandra och hur meddelandeköer används i systemet.

Arbetet med utcheckningen och integrationen mellan frontend och Order Service gick framåt, men det fanns fortfarande delar av beställningsflödet och tjänstens konfiguration som behövde undersökas vidare.

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

### Vecka 44 – 26 oktober–1 november 2026

**Vad jag arbetade med**

Den här veckan arbetade jag med flera delar av webshopprojektet. Jag började med FE-43 under Sprint 7, som handlar om att skapa och uppdatera README-dokumentation för projektets olika repositories.

Jag fortsatte även arbetet med autentiseringen mellan frontend, Gateway och Auth Server. Jag arbetade med återställning av inloggad användare efter siduppdatering, `AuthProvider` och `ProtectedRoute`. Jag testade även inloggning, utloggning, sessionsåterställning och rollbaserad åtkomst.

Jag arbetade vidare med Gateway och dess kommunikation med Product Service och Order Service. Jag undersökte och korrigerade problem med routningen till Product Service. Jag arbetade även med order-endpoints för att kunna skapa och hämta beställningar genom Gateway.

I Order Service arbetade jag med hämtning av beställningar baserat på användarens roll. Vanliga användare ska endast kunna se sina egna beställningar, medan administratörer ska kunna hämta samtliga beställningar.

I frontend fortsatte jag utvecklingen av kundvagnen. Jag förbättrade lagringen så att varje inloggad användare får en egen kundvagn med hjälp av `sessionStorage` och användarens `subject`.

Jag arbetade också med dokumentationen för samtliga sex delar av webshopprojektet: Auth Server, Product Service, Email Service, Gateway, Order Service och Frontend.

**Problem och resultat**

Under arbetet med Gateway upptäckte jag problem med routningen till Product Service. Jag korrigerade sökvägen och verifierade att produktlistan kunde hämtas genom Gateway.

Jag testade även orderhanteringen och kontrollerade att en vanlig användare endast får sina egna beställningar och att en administratör kan se samtliga beställningar.

Ett annat problem var att kundvagnen tidigare kunde delas mellan olika användare. Jag ändrade därför lagringen så att varje användare får en separat kundvagn. Jag testade att innehållet finns kvar efter F5, att olika användare inte delar kundvagn och att rätt kundvagn återställs efter utloggning och återinloggning.

Veckans dokumentationsarbete resulterade i att README-filerna för samtliga sex repositories uppdaterades och sparades. Dokumentationen beskriver respektive tjänsts ansvarsområde, tekniker, konfiguration och funktionalitet.

---

## Samarbete och agilt arbetssätt

Vi arbetar i grupp med en återkommande rutin. På måndagar har vi sprintplanering där vår Scrum Master går igenom vad vi ska arbeta med och vem som ansvarar för vad. Under resten av veckan har vi ett möte om dagen för att stämma av arbetet och diskutera hur vi ligger till. På fredagar är det planerat att vi ska demonstrera arbetet för läraren.

Mitt eget arbete har framför allt varit inriktat på produktvisning, kundvagn och kopplingen mellan frontend och Order Service. Jag har delat upp utvecklingen i mindre steg och testat funktionerna efter hand. När problem har uppstått har jag undersökt orsaken och arbetat med att förbättra lösningen.

Jag har inte tillräckligt med dokumentation för att säkert ange vilka sprint reviews eller retrospektiv som genomförts. Därför har jag inte registrerat sådana aktiviteter som genomförda i denna loggbok.
