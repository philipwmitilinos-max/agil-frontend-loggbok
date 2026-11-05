# Individuell loggbok – Webbshopprojektet

> **Obs:** Loggboken är sammanställd utifrån det arbete som finns dokumenterat i mina samtal och uppgifter. Lägg till eller rätta datum om jag arbetade med något annat den dagen. Veckorna nedan är kalenderveckor och ska inte tolkas som officiella sprintnummer.

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

Jag testade hur kundvagnen hanterar produkter och lagersaldo samt hur frontend visar felmeddelanden när en beställning inte kan genomföras. Jag kontrollerade även att kundvagnens innehåll behålls om utcheckningen misslyckas.

Mot slutet av veckan började jag arbeta med Spring Cloud Gateway. Jag granskade `pom.xml`, lade till beroendet för Spring Cloud Gateway Server Web MVC och arbetade med konfigurationen i `application.properties`. Jag undersökte hur Gateway skulle fungera som en gemensam ingång till Auth Server, Product Service och Order Service. Jag arbetade även med portkonfigurationen, miljövariabler och routning till backend-tjänsterna.

**Problem och resultat**

När kunden försökte beställa fler produkter än vad som fanns i lager svarade Product Service med HTTP 400, medan Order Service skickade HTTP 500 till frontend. Jag förbättrade felhanteringen så att Order Service returnerar HTTP 409 Conflict med ett begripligt meddelande vid otillräckligt lager.

Jag testade sedan att varningen visas och att kundvagnen behålls när beställningen misslyckas. Tester bekräftade att hanteringen av slutsålda produkter och fel vid utcheckning fungerade som förväntat.

Arbetet med Gateway kom också vidare. Maven-kommandot `compile` slutfördes med `BUILD SUCCESS` och Gateway-applikationen startade lokalt utan fel. Grundkonfigurationen och routningen till backend-tjänsterna kom på plats, men alla routes till Product Service och Order Service var ännu inte fullständigt verifierade.

### Vecka 43 – 19–25 oktober 2026

**Vad jag arbetade med**

Jag arbetade vidare med autentisering genom Spring Cloud Gateway och frontendens återställning av inloggad användare. Veckans huvudsakliga uppgift var FE-36, som handlar om att användaren ska förbli inloggad även efter att sidan laddas om.

Jag började med att undersöka den befintliga autentiseringslösningen i React och TypeScript. Jag gick igenom `authService.ts`, `LoginPage`, `LoginForm`, `WelcomePage`, `App.tsx` och `ProtectedRoute.tsx` för att förstå hur inloggning, användarinformation och skyddade routes fungerade.

Jag städade och anpassade autentiseringsrelaterad kod i `authService.ts`, `apiClient.ts`, `ProtectedRoute.tsx`, `Header.tsx`, `LoginForm.tsx` och `AuthContext.tsx`. Jag kopplade `LoginForm` och `Header` till `AuthContext` och arbetade med `AuthProvider` för att hantera användarens autentiseringstillstånd globalt.

Jag anpassade frontend till autentisering med HttpOnly-cookie genom att använda `credentials: "include"` och hämta användarinformation från Gatewayns `/auth/me` i stället för att läsa en JWT från frontendens lagring.

Jag arbetade även med Gateway-konfigurationen och korrigerade frontendens Gateway-adress till `http://localhost:9003/gateway`. I den uppdaterade Product Backlog är FE-34, FE-35 och FE-36 markerade som klara.

**Problem och resultat**

Under arbetet undersökte jag hur användarens session skulle kunna återställas automatiskt när applikationen startar. Jag anpassade `AuthContext` så att den kontrollerar den befintliga sessionen och hämtar användarinformation från `/auth/me`.

Jag uppdaterade även `ProtectedRoute` så att skyddade sidor väntar medan sessionen kontrolleras. På så sätt undviks att användaren skickas till inloggningssidan innan kontrollen av den befintliga sessionen är färdig.

Jag verifierade att `GET /auth/me` returnerar användarens `subject`, `roles` och `expiresIn` när sessionen är giltig. Jag laddade om `/welcome` med F5 och kontrollerade att användaren fortfarande var inloggad och att välkomstmeddelandet och rollen `USER` visades.

Jag testade även utloggningen och kontrollerade att användaren navigeras till `/login`. När sessionen saknades returnerade `/auth/me` HTTP 401 Unauthorized, vilket var förväntat.

Ändringarna för FE-36 committades på branchen `feature/keep-login`, och funktionen fungerade vid testning.

Administratörsåtkomst fungerade ännu inte som avsett och behövde undersökas separat med gruppen. Jag identifierade även duplicerade routes i `App.tsx`, som skulle diskuteras med gruppen innan eventuella ändringar genomfördes.

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

### Vecka 45 – 2–8 november 2026

**Vad jag arbetade med**

Den här veckan fokuserade jag på att förbereda och genomföra gruppens presentation av webbshopprojektet.

Tisdagen den 3 november deltog jag i planeringen av presentationen tillsammans med gruppen. Vi gick igenom hur presentationen skulle delas upp mellan gruppmedlemmarna och planerade upplägget i Google Slides. Presentationen skulle vara totalt 20 minuter. Min del handlade om produktvisning, produktdetaljer och kundvagn.

Onsdagen den 4 november fortsatte jag med att förbereda min del av presentationen. Jag gick igenom slides och tog fram kodexempel från bland annat `productService.ts`, `ProductsPage.tsx` och `Cart.tsx` för att visa hur funktionerna är implementerade. Jag gick igenom hur produkterna hämtas från Product Service, hur lagerkontroller fungerar och hur kundvagnen hanterar antal, radpriser och totalsumma. Jag sammanställde även ett separat dokument med förklaringar och kodexempel som stöd inför presentationen.

**Resultat och presentation**

Torsdagen den 5 november genomförde gruppen presentationen av webbshopprojektet. Jag presenterade mina delar av frontendutvecklingen och visade hur de olika produkt- och kundvagnsfunktionerna fungerar.

Presentationens genomförande gick bra. Jag hade även förberett ett separat manus som stöd, men använde det inte under själva presentationen. Gruppens presentationsmaterial användes vid redovisningen.

---

## Samarbete och agilt arbetssätt

Vi arbetar i grupp med en återkommande rutin. På måndagar har vi sprintplanering där vår Scrum Master går igenom vad vi ska arbeta med och vem som ansvarar för vad. Under resten av veckan har vi ett möte om dagen för att stämma av arbetet och diskutera hur vi ligger till. På fredagar är det planerat att vi ska demonstrera arbetet för läraren.

Mitt eget arbete har framför allt varit inriktat på produktvisning, kundvagn och kopplingen mellan frontend och Order Service. Jag har delat upp utvecklingen i mindre steg och testat funktionerna efter hand. När problem har uppstått har jag undersökt orsaken och arbetat med att förbättra lösningen.

Jag har inte tillräckligt med dokumentation för att säkert ange vilka sprint reviews eller retrospektiv som genomförts. Därför har jag inte registrerat sådana aktiviteter som genomförda i denna loggbok.

---

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
- Använde en kontroll av produktens lagersaldo (`product.stock <= 0`) för att avgöra om produkten skulle markeras som slutsåld.
- Inaktiverade köpknappen för slutsålda produkter och ändrade knappens text till `Slutsåld`.
- Undersökte varför utcheckningen gav HTTP 500 när kunden försökte beställa fler varor än vad som fanns i lager.
- Gick igenom hur frontendens funktioner `addToCart()` och `increaseQuantity()` kontrollerar att kunden inte lägger till fler produkter än vad som finns i lager.
- Undersökte hur fel från Order Service hanterades i frontendens `handleCheckout()`.

**Problem och resultat**

- Identifierade att Product Service svarade med HTTP 400 när lagret inte räckte, men att Order Service skickade HTTP 500 till frontend.
- Ändrade produktvisningen så att slutsålda produkter fortfarande är synliga men inte längre kan läggas i kundvagnen via köpknappen.
- Befintliga kontroller i kundvagnen begränsade antalet produkter till tillgängligt lagersaldo.
- Identifierade att frontendens felhantering vid utcheckning behövde förbättras eftersom den visade ett generellt felmeddelande.
- Kom fram till att `orderService.ts` behövde hantera och vidarebefordra mer information om backendens fel så att användaren kunde få ett tydligare meddelande vid otillräckligt lagersaldo.

### Tisdag 13 oktober 2026

**Vad jag arbetade med**

- Förbättrade felhanteringen i frontend och Order Service.
- Ändrade `orderService.ts` så att frontend kan läsa och hantera felmeddelanden från backend.
- Ändrade `catch`-blocket i `handleCheckout()` så att felmeddelandet från backend visas för användaren.
- Skapade `GlobalExceptionHandler.java` i Order Service för att hantera fel som uppstår när Product Service rapporterar att lagersaldot inte räcker.
- Arbetade med att skilja på olika typer av fel så att otillräckligt lager inte längre behandlas som ett generellt serverfel.
- Implementerade hantering av HTTP 409 Conflict för situationer där en beställning inte kan genomföras på grund av otillräckligt lager.

**Problem och lösning**

- Tidigare visades ett generellt HTTP 500-fel när lagersaldot inte räckte.
- Problemet berodde på att felet från Product Service inte hanterades korrekt av Order Service.
- Skapade en global felhanterare som fångar upp felet och returnerar HTTP 409 Conflict med ett begripligt felmeddelande.
- Anpassade frontendens felhantering så att meddelandet från backend kan visas i stället för ett generellt felmeddelande.

**Resultat**

- Testade utcheckningen igen och kontrollerade att användaren får en tydlig varning när lagersaldot inte räcker.
- Kontrollerade att kundvagnens innehåll behålls om beställningen misslyckas.
- Felhanteringen blev tydligare och frontend kunde skilja på otillräckligt lager och andra typer av fel.
- Utcheckningen fick en bättre återkoppling till användaren när en beställning inte kunde genomföras.

### Onsdag 14 oktober 2026

**Vad jag arbetade med**

- Följde upp och testade funktionerna för slutsålda produkter och utcheckning.
- Kontrollerade att slutsålda produkter fortfarande visas, att köpknappen är inaktiverad och att kunden får en varning om lagersaldot inte räcker.
- Testade hur frontend hanterar felmeddelanden från Order Service när en beställning inte kan genomföras.
- Kontrollerade att Order Service returnerar HTTP 409 Conflict när Product Service rapporterar otillräckligt lager.
- Testade att kundvagnens innehåll behålls när utcheckningen misslyckas.
- Gick igenom att felmeddelandet visas tydligt för användaren i samband med utcheckningen.

**Resultat**

- Bekräftade att funktionerna fungerade vid testning och att kundvagnen behålls när beställningen misslyckas.
- Kontrollerade att slutsålda produkter inte kan läggas till i kundvagnen via köpknappen.
- Verifierade att användaren får ett begripligt felmeddelande när lagersaldot inte räcker.
- Felhanteringen mellan frontend och Order Service fungerade som avsett vid de tester som genomfördes.

### Torsdag 15 oktober 2026

**Vad jag arbetade med**

- Började arbeta med Spring Cloud Gateway som en gemensam ingång till webbshopens olika mikrotjänster.
- Gick igenom Gateway-projektets `pom.xml` och kontrollerade vilka beroenden som behövdes.
- Arbetade med konfigurationen i `application.properties`.
- Gick igenom huvudklassen `WebshopGatewayApplication.java` och hur Gateway-applikationen startas.
- Undersökte hur routes skulle konfigureras för att vidarebefordra anrop till Auth Service, Product Service och Order Service.
- Arbetade med portkonfigurationen och miljövariabler för tjänsternas adresser.

**Problem och resultat**

- Behövde sätta mig in i hur Spring Cloud Gateway fungerar och hur den kopplar samman mikrotjänsterna.
- Gick igenom projektets beroenden och konfiguration för att få Gateway att fungera.
- Kom vidare med grundstrukturen och routingen i Gateway-projektet.
- Projektet kompilerades utan fel och Maven visade `BUILD SUCCESS`.

### Fredag 16 oktober 2026

**Vad jag arbetade med**

- Började arbeta med Gateway-delen av webbshopprojektet.
- Granskade `pom.xml` och lade till beroendet för Spring Cloud Gateway Server Web MVC.
- Kontrollerade konfigurationen i `application.properties`, inklusive port 9003 och routning till Auth Server, Product Service och Order Service.
- Använde miljövariabler med lokala standardadresser för backend-tjänsterna.
- Arbetade med att förstå hur Gateway fungerar som en gemensam ingång till webbshopens olika mikrotjänster.
- Gick igenom hur inkommande HTTP-anrop ska matchas mot olika routes och vidarebefordras till rätt backend-tjänst.
- Undersökte hur Gateway-konfigurationen behöver samverka med tjänsternas olika adresser och portar.
- Kontrollerade huvudkonfigurationen och hur Gateway-applikationen startas lokalt.

**Problem och resultat**

- Körning av Maven-kommandot `compile` slutfördes med `BUILD SUCCESS`.
- Gateway-applikationen startade lokalt utan fel.
- Grundkonfigurationen för Gateway och routningen till backend-tjänsterna kom på plats.
- Vid den första kontrollen var routningen till respektive backend ännu inte verifierad genom separata anrop.
- Senare arbete med autentisering via Gateway verifierade delar av flödet, bland annat inloggning, session och utloggning.
- Alla routes till Product Service och Order Service är inte dokumenterade som fullständigt verifierade här.

### Måndag 19 oktober 2026

**Vad jag arbetade med**

- Gick igenom nya krav och uppdateringar i webbshopprojektet inför den kommande sprinten.
- Började sätta mig in i uppgiften FE-36, som handlar om att återställa användarens inloggning efter att sidan laddats om.
- Undersökte hur den befintliga autentiseringslösningen i React och TypeScript fungerade.
- Gick igenom hur frontend kommunicerar med Gateway och hur autentiseringen är kopplad till backend-tjänsterna.
- Diskuterade hur användarens inloggning skulle kunna behållas vid en sidomladdning.
- Gick igenom kopplingen mellan autentisering via cookies och Gateway.

**Resultat**

- Fick en tydligare förståelse för kraven i FE-36 och vad som behövde utvecklas.
- Identifierade vilka delar av frontendens autentiseringslösning som behövde undersökas närmare.
- Förberedde arbetet med att återställa användarens inloggning efter en sidomladdning.
- Arbetet med FE-36 blev utgångspunkten för det fortsatta arbetet under sprinten.

### Tisdag 20 oktober 2026

**Vad jag arbetade med**

- Fortsatte undersökningen av FE-36, som handlar om att återställa användarens inloggning efter att sidan laddats om.
- Gick igenom `authService.ts` för att förstå hur autentiseringsinformationen sparas och hämtas.
- Undersökte hur `access_token` och `loginResponse` sparas i `sessionStorage`.
- Gick igenom funktionerna `isAuthenticated()` och hur den kontrollerar om en användare har en sparad token.
- Granskade `LoginPage.tsx` och `LoginForm.tsx` för att förstå hur inloggningen genomförs.
- Undersökte `WelcomePage.tsx` och hur användarinformationen hämtas från den sparade inloggningsinformationen.
- Gick igenom `App.tsx` och hur applikationens routes och skyddade sidor är uppbyggda.

**Resultat**

- Fick en bättre förståelse för hur autentiseringen fungerar i frontend och hur inloggningsinformationen hanteras med `sessionStorage`.
- Identifierade hur användarens token kontrolleras när applikationen navigerar mellan olika sidor.
- Kartlade vilka komponenter och funktioner som berörs av FE-36.
- Undersökningen gav en bättre grund för det fortsatta arbetet med att återställa användarens inloggning efter en sidomladdning.

### Onsdag 21 oktober 2026

**Vad jag arbetade med**

- Fortsatte arbetet med FE-36, som handlar om att återställa användarens inloggning efter att sidan laddats om.
- Gick igenom `ProtectedRoute.tsx` och undersökte hur komponenten kontrollerar om användaren är inloggad.
- Granskade funktionerna `isAuthenticated()` och `hasRole()` för att förstå hur autentisering och behörigheter kontrolleras.
- Kontrollerade hur användare som inte är inloggade skickas vidare till `/login`.
- Fortsatte felsöka inloggningen via Spring Cloud Gateway.
- Undersökte varför POST-anropet till `http://localhost:9003/auth/login` returnerade HTTP 404.
- Granskade Gateway-konfigurationen och upptäckte att Auth-routen använde `Path=/gateway/auth/**` och `StripPrefix=1`.
- Jämförde frontendens API-adress med Gateway-routen för att hitta orsaken till att anropet inte fungerade.

**Problem och resultat**

- Fick en bättre förståelse för hur `ProtectedRoute.tsx` hanterar autentisering och användarbehörigheter.
- Identifierade att frontendens inloggningsanrop inte matchade Gateway-routen eftersom `/gateway` saknades i anropsadressen.
- Kom fram till att `VITE_API_GATEWAY_URL` behövde innehålla rätt basadress för Gateway.
- Problemet identifierades, men ändringen och det efterföljande testet genomfördes först senare.

### Torsdag 22 oktober 2026

**Vad jag arbetade med**

- Fortsatte arbetet med FE-36, som handlar om att återställa användarens inloggning efter att sidan laddats om.
- Korrigerade `VITE_API_GATEWAY_URL` till `http://localhost:9003/gateway` efter genomgång tillsammans med läraren.
- Uppdaterade `authService.ts` och lade till `credentials: "include"` i login-anropet för att cookies skulle skickas med förfrågningarna.
- Behöll den befintliga hanteringen av JWT-token och `loginResponse` i `sessionStorage`.
- Arbetade vidare med funktionerna för inloggning, utloggning och hantering av användarroller.
- Granskade och rättade ett syntaxfel i `pom.xml` där en dependency-tagg hade avslutats felaktigt.
- Fortsatte testa kommunikationen via Gateway och undersökte problem med routningen till `/gateway/orders`.

**Problem och resultat**

- Korrigerade Gateway-adressen så att frontend använder rätt basadress för API-anropen.
- Lade till `credentials: "include"` för att möjliggöra överföring av cookies vid inloggning.
- Rättade syntaxfelet i `pom.xml`, vilket gjorde att konflikterna i projektet försvann.
- Vid fortsatt testning returnerade Gateway HTTP 404 vid anrop till `/gateway/orders`, vilket behövde undersökas vidare.
- Kom vidare med autentiseringslösningen och arbetet med FE-36.

### Fredag 23 oktober 2026

**Vad jag arbetade med**

- Arbetade med FE-36, som i den uppdaterade Product Backlog är markerad som klar. Uppgiften handlar om att återställa användarens inloggning efter att sidan laddas om.
- Städade och anpassade frontendkod kopplad till autentisering i `authService.ts`, `apiClient.ts`, `ProtectedRoute.tsx`, `Header.tsx`, `LoginForm.tsx` och `AuthContext.tsx`.
- Anpassade frontend till autentisering med HttpOnly-cookie genom att använda `credentials: "include"`.
- Ändrade hanteringen av användarinformation så att frontend hämtar information från Gatewayns `/auth/me` i stället för att läsa en JWT från frontendens lagring.
- Arbetade med `AuthContext` och `AuthProvider` för att hantera användarens autentiseringstillstånd globalt i React.
- Committade ändringarna på branchen `feature/keep-login`.

**Problem och lösning**

- Säkerställde att `AuthContext` återställer användaren vid appstart genom att kontrollera den befintliga sessionen.
- Anpassade `ProtectedRoute` så att komponenten väntar medan sessionen kontrolleras innan användaren får tillgång till skyddade sidor.
- Uppdaterade inloggningsformuläret så att `AuthContext` får användarinformationen direkt efter en lyckad inloggning.
- Förbättrade utloggningen så att användaren tas bort från Reacts autentiseringstillstånd och navigeras vidare till `/login`.
- Använde Gatewayns `/auth/me` för att kontrollera om användarens session fortfarande är giltig.

**Resultat och testning**

- Testade att `GET /auth/me` returnerar användarens `subject`, `roles` och `expiresIn` när sessionen är giltig.
- Laddade om `/welcome` med F5 och verifierade att användaren fortfarande var inloggad och att välkomstmeddelandet och rollen `USER` visades efter omladdningen.
- Testade utloggning och kontrollerade att direkt navigering till `/products` efter utloggning skickar användaren till `/login`.
- Kontrollerade att anropet till `/auth/me` returnerade `401 Unauthorized` när användaren saknade en giltig session.
- FE-36 fungerade vid testning och kunde markeras som klar.
- Administratörsåtkomst fungerade ännu inte som avsett och behövde undersökas separat med gruppen.
- Dubbla routes i `App.tsx` identifierades och skulle diskuteras med gruppen innan några ändringar genomfördes.

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

### Tisdag 3 november 2026

**Vad jag arbetade med**

- Deltog i planeringen av gruppens presentation av webbshopprojektet.
- Gick igenom hur presentationen skulle delas upp mellan gruppmedlemmarna.
- Planerade min del av presentationen, som omfattade produkter, produktdetaljer och kundvagn.
- Arbetade med upplägget för presentationen i Google Slides.
- Diskuterade tidsfördelningen för presentationen, som skulle vara totalt 20 minuter.

**Resultat**

- Gruppen fick en tydligare struktur för presentationen.
- Ansvarsområdena för presentationen fördelades mellan gruppmedlemmarna.

### Onsdag 4 november 2026

**Vad jag arbetade med**

- Förberedde min del av gruppens presentation av webbshopprojektet.
- Gick igenom slides om produktvisning, produktdetaljer, lagersaldo och kundvagn.
- Granskade kodexempel från `productService.ts`, `ProductsPage.tsx` och `Cart.tsx`.
- Skapade ett separat dokument med förklaringar till min del av presentationen.
- Förberedde kodexempel som visar hur kundvagnen beräknar radpris och totalsumma med `map()` och `reduce()`.

**Resultat**

- Färdigställde mitt presentationsmaterial och mitt separata manus inför gruppens redovisning den 5 november.

### Torsdag 5 november 2026

**Vad jag arbetade med**

- Deltog i gruppens presentation av webbshopprojektet.
- Presenterande min del av frontendutvecklingen, som omfattade produktvisning, produktdetaljer, lagersaldo och kundvagn.
- Visade hur frontend hämtar produkter från Product Service och hur produkterna presenteras med React-komponenter.
- Gick igenom funktioner för produktsökning, kategorifiltrering, lagerkontroller och kundvagnens prisberäkningar.
- Förklarade hur kundvagnen hanterar produkter, antal och totalsumma samt hur innehållet sparas per användare i `sessionStorage`.

**Resultat**

- Gruppen genomförde presentationen av webbshopprojektet.
- Jag fick möjlighet att visa och redogöra för de delar av frontend som jag hade arbetat med.
- Presentationen gick bra.
