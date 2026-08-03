# Slutgranskning av Jobblys integritetspolicy

Granskad den 3 augusti 2026 mot app- och backendkod, deklarerad produktionskonfiguration, publika produktionsadresser samt aktuell officiell dokumentation från Apple och berörda leverantörer.

Detta är ett praktiskt dataskydds- och App Store-underlag, inte formell juridisk rådgivning.

## A. Publicerbar svensk integritetspolicy

### Status: policytext färdig, lansering fortfarande blockerad

En ren svensk målversion har nu skrivits i `integritetspolicy.html`, och användarvillkoren har synkroniserats. Texten får publiceras först när uppgifterna i avsnitt B har bekräftats och produktbristerna i avsnitt C har åtgärdats så att appen motsvarar policyn.

Den nu publicerade sidan på https://brickphone.github.io/jobbly-policies/integritetspolicy.html är tekniskt publik, stabil och mobilåtkomlig, och samma URL finns i appen. GitHub Pages visar dock den äldre versionen tills de lokala ändringarna har granskats, committats och pushats.

Bekräftade uppgifter som kan användas i nästa version är:

- Senast angivna policydatum: 28 juni 2026.
- Personuppgiftsansvarig enligt befintligt underlag: Mattis Huttenrauch, organisationsnummer 20030515-2811.
- Avsedd kontaktadress: support@jobbly.se. Adressen är ännu inte verifierad som fungerande.
- Tillämpad minimiålder för lansering: 18 år.
- Rekommenderad slutlig policy-URL: den befintliga GitHub Pages-adressen ovan. Ingen ändring av appens juridiska URL behövs.

Den nya HTML-texten har kontrollerats maskinellt och innehåller inga hakparenteser, ”Att fylla i”-instruktioner, alternativa åldrar eller interna granskningsanteckningar.

## B. Needs owner confirmation

1. Bekräfta fullständig juridisk postadress med korrekt gatunamn, gatunummer, postnummer och ort. Den ofullständiga uppgiften ”bjornkarrsgatan 12” får inte publiceras.
2. Skapa och funktionstesta support@jobbly.se för både inkommande och utgående e-post. DNS-kontrollen den 3 augusti 2026 visade ingen MX-post för jobbly.se.
3. Bekräfta att den nu tillämpade avtalsåldern 18 år ska behållas i release. Google Geminis gällande API-villkor kräver att API-klienter inte riktas till eller sannolikt används av personer under 18 år.
4. Bestäm om personnummer ska tas bort som generellt obligatoriskt profilfält, vilket rekommenderas, eller om nuvarande krav ska behållas med dokumenterad nödvändighet och rättsligt stöd enligt svensk rätt.
5. Låt svensk dataskyddsjurist fastställa rättslig grund för varje ändamål, särskilt AI-behandling, personnummer, platsdata, Superwalls händelsedata, säkerhetsloggar och utlämnande till arbetsgivare. Apples uttryckliga AI-tillstånd är ett separat plattformskrav och avgör inte GDPR-grunden.
6. Fastställ konkreta lagringstider eller tydliga raderingskriterier för aktivt konto och profil, raderat konto, CV, personliga brev, ansökningshistorik, arbetsgivarinkorg och användarsvar, automatiseringsposter, drift- och säkerhetsloggar, frågeskärmbilder, eventuella felsökningsartefakter, säkerhetsincidenter och lokala appdata.
7. Bekräfta databasbackupers och lagringsbackupers faktiska löptid, inklusive Supabase-plan och eventuell PITR, samt när kopior av ett raderat konto definitivt upphör att finnas.
8. Bekräfta om bokförings-, betalnings- eller skatteunderlag behandlas utanför repot, vilka uppgifter det gäller och tillämplig lagringstid.
9. Bekräfta Supabase-projektets valda region, abonnemangsplan, supportåtkomst, aktuella underbiträden, undertecknat eller accepterat personuppgiftsbiträdesavtal och faktisk radering efter Jobblys begäran.
10. Bekräfta den live-driftsatta Render-tjänstens region och miljövariabler, Workspace-plan, logglagring eller extern loggströmning, aktuella underbiträden och accepterat personuppgiftsbiträdesavtal. Repots manifest anger Frankfurt men ger inte åtkomst till Render-kontots liveinställningar.
11. Bekräfta att Gemini-projektet har aktiv fakturering och därför används som Paid Service, att Googles personuppgiftsbiträdesvillkor gäller, om Zero Data Retention har godkänts, samt vilket internationellt överföringsstöd som faktiskt åberopas. Direkt Gemini Developer API har ingen verifierad EU-datalokaliseringsgaranti i underlaget.
12. Bekräfta Resends live-nyckel, sändande domän, mottagningsdomän, sändningsregion, avtal, underbiträden och raderingsfunktioner. Bekräfta separat om Supabase Authentication använder Resend som anpassad SMTP; koden bevisar inte detta.
13. Bekräfta Superwall-kontots avtal, DPA, aktiva integrationer, händelseinställningar, underbiträden, användarradering och lagring. Repot visar SDK-användning men inte dashboardinställningarna.
14. Bekräfta de juridiska rollerna för Apple, Google, Arbetsförmedlingen JobTech och arbetsgivarnas rekryteringssystem med svensk jurist. De är inte automatiskt Jobblys personuppgiftsbiträden för all behandling.
15. Bekräfta om Apple-diagnostik används eller granskas i App Store Connect och att ingen fristående crashrapportering, reklamidentifierare, ATT-data eller annonseringsspårning har lagts till utanför det granskade repot.
16. Bekräfta slutlig policy-URL. Rekommendationen är att behålla https://brickphone.github.io/jobbly-policies/integritetspolicy.html.
17. Ange en publik Support URL med aktuella kontaktuppgifter och kontrollera App Store Connects nuvarande Support URL, integritetssvar och åldersklassificeringssvar.
18. Bekräfta vilket datum som ska anges som senaste uppdatering i den faktiskt publicerade slutversionen.

## C. Product changes required before publication

### Måste vara klart före App Store-inlämning

- Implementera ett separat, tydligt och bekräftande tillstånd innan den första överföringen av personuppgifter till Google Gemini. Skärmen ska namnge Google Gemini, beskriva syftet och sammanfatta de datakategorier som kan skickas. Fortsatt användning, registrering eller ett godkännande av allmänna villkor får inte ensamt räknas som AI-tillstånd.
- Lagra tillståndets version, mottagare, ändamål och tidsstämpel på serversidan. Backend ska avvisa AI-anrop om giltigt tillstånd saknas.
- Lägg till ”AI och datadelning” under Profil → Inställningar. Där ska användaren kunna återkalla tillståndet utan att radera kontot. Efter återkallelse ska nya Gemini-anrop stoppas, appen ska förklara vilka ansökningsfunktioner som slutar fungera och åtkomst till kontoradering och dataskyddsrättigheter ska finnas kvar.
- Om 18 år godkänns: lägg till ålderskontroll före konto- och AI-användning, hindra minderåriga från att fortsätta och synkronisera appflöde, användarvillkor och integritetspolicy. App Stores innehållsbaserade åldersklassificering ska besvaras separat och sanningsenligt.
- Ta bort personnummer, födelsedatum, kön, fullständig adress och andra uppgifter från den generella ”profil komplett”-spärren när de inte behövs för den specifika ansökan. Begär personnummer först när en identifierad ansökningsblankett faktiskt kräver det och visa varför. Om nuvarande obligatoriska modell behålls krävs i stället juridiskt godkänd motivering och korrekt policytext före lansering.
- Rätta kontoraderingen så att även användarens objekt i Supabase-bucketen `application-runs` tas bort: CV-kopior, personliga brev, frågeskärmbilder och eventuella felsökningsartefakter. Nuvarande endpoint tar bara bort objekt i `resumes` innan auth-användaren raderas.
- Inför schemalagda raderingsjobb för de lagringstider ägaren beslutar om. De ska omfatta ansökningspayload, historik, meddelanden och svar, dokumentkopior, automatiseringsdata, skärmbilder, felsökningsartefakter och relevanta loggar. Testa både normal radering, delvis leverantörsfel och backup-expiration.
- Säkerställ att en användares raderingsbegäran även skickas vidare till Resend, Superwall och andra biträden där ett separat API- eller supportärende krävs. Dokumentera vad som inte kan återkallas från en arbetsgivare efter att ansökan redan skickats.
- Skapa och testa en riktig supportbrevlåda. Publicera en supportsida med aktuell juridisk adress och fungerande kontaktuppgift. Lägg till Support/Kontakt under Profil → Inställningar, gör e-postlänken klickbar och fyll i samma fungerande Support URL i App Store Connect.
- Behåll den befintliga integritetspolicy-URL:en, testa den i release-bygget och fyll i exakt samma URL under App Privacy i App Store Connect. Sidan ska vara publik utan inloggning och mobilvänlig.
- Uppdatera App Store Connects integritetssvar efter den slutliga datakartan. De ska omfatta egna och inbyggda tredjeparts-SDK:ers behandling, bland annat kontaktuppgifter, exakt eller ungefärlig plats, användarinnehåll, identifierare, köp, produktinteraktion och diagnostik där det är tillämpligt.
- Ta bort eller begränsa `NSAllowsArbitraryLoads` om det inte finns ett dokumenterat releasebehov. Alla appens egna verifierade API-adresser använder HTTPS.

### Rättighets- och driftflöden

- Lägg till eller dokumentera ett operativt flöde för tillgång, rättelse, begränsning, dataportabilitet och invändning mot behandling som grundas på berättigat intresse. Ange svarskanal och ansvarig person.
- Håll kontoradering och återkallat AI-tillstånd som två separata åtgärder i både gränssnitt och backend.
- Verifiera om Resend skickar autentiseringsmejl via Supabase SMTP innan den funktionen beskrivs i policyn.
- Lås produktionsmiljön till Gemini och ta bort eller håll Qwen helt avstängt om leverantören inte ska användas. Browserbase/Stagehand och visionskärmbilder ska fortsatt vara avstängda om de inte genomgår en ny integritetsgranskning och ett nytt användartillstånd.
- Inför ett versionsstyrt register över policyn, AI-informationen, mottagare och konfiguration. En leverantörs-, payload- eller regionsändring ska utlösa ny granskning före release.

### Kräver svensk juridisk granskning

- Samtliga GDPR-grunder och lagringstider samt eventuella intresseavvägningar.
- Behandling av personnummer enligt 3 kap. 10 § dataskyddslagen och om behandlingen alls är klart motiverad.
- Om en konsekvensbedömning enligt artikel 35 GDPR behövs med hänsyn till ny teknik, omfattande profil- och rekryteringsdata, personnummer, automatisering och tredjeparts-AI.
- Ansvarsfördelningen mellan Jobbly, arbetsgivare, rekryterare, ATS-leverantörer, Apple, Google och JobTech.
- Internationella överföringar, leverantörsavtal, SCC, eventuellt Data Privacy Framework och kompletterande skyddsåtgärder.
- Formuleringen av rättigheter, invändning, AI-tillstånd och återkallelse samt samordningen med användarvillkoren.

## D. Processor/data map

| Mottagare | Uppgifter som tas emot | Ändamål | Roll | Region och internationell överföring | Lagring och radering | Verifieringskälla |
|---|---|---|---|---|---|---|
| Supabase | Auth-ID, e-post och auth-metadata; profilsammanfattning; full ansökningspayload med kontakt-, adress-, köns-, födelse-, medborgarskaps-, arbetstillstånds- och personnummeruppgifter; erfarenhet, utbildning och svar; CV och personliga brev; ansökningsstatus, fel, historik, kvoter; arbetsgivarmejl, inkorg och användarsvar | Autentisering, databas, privat dokumentlagring, ansökningshistorik, meddelanden och behörigheter | Personuppgiftsbiträde för Jobblys data enligt Supabase DPA, under förutsättning att avtalet gäller för kontot | Projektets valda region är inte verifierad. Supabase anger att data lagras och huvudsakligen behandlas i vald region, men behandling, support och underbiträden kan innebära åtkomst utanför EES; DPA innehåller SCC | Profil, ansökningar och meddelanden saknar tidsstyrd gallring i repot. Auth-radering kaskadraderar databasposter. `resumes`-objekt tas bort, men `application-runs`-objekt lämnas kvar. Databasbackup beror på plan och omfattar inte Storage-objekt | `backend/supabase/*.sql`, `backend/src/routes/account.ts:8`, `backend/src/services/applications/queue.ts:43`; [Supabase regions](https://supabase.com/docs/guides/platform/regions), [backups](https://supabase.com/docs/guides/platform/backups), [DPA](https://supabase.com/downloads/docs/Supabase%2BDPA%2B260601.pdf) |
| Render | API-anrop, kontots Supabase-ID, sökfilter och ibland koordinater; full ansökningspayload och dokument under bearbetning; apply-URL; status-, fel-, säkerhets- och driftmetadata | Backendhosting, jobbsökning, ansökningsautomatisering, e-postorkestrering och loggning | Personuppgiftsbiträde för kunddata; egen personuppgiftsansvarig för vissa konto- och användningsdata enligt Render DPA | Repots produktionsmanifest anger Frankfurt. Livekontots region är inte direkt verifierad. Render är en USA-baserad leverantör och DPA anger DPF eller SCC för relevanta överföringar | Applikationsdata ligger främst i Supabase. Render-loggarnas tid beror på Workspace-plan och eventuell extern loggströmning, vilka inte är verifierade | `render.yaml:1`, live `https://jobbly-backend-6yl1.onrender.com/health`; [Render regions](https://render.com/docs/regions), [logging](https://render.com/docs/logging), [DPA](https://render.com/dpa) |
| Google Gemini Developer API | Namn, kontakt- och adressuppgifter, kön, personnummer, födelsedatum, medborgarskap, arbetstillstånd, erfarenhet, utbildning, urvalssvar och användarens frågesvar; extraherad text ur personligt brev; ansökningssidas URL, rubriker, formulärfrågor, alternativ, fältinnehåll, sidans tillgänglighetsträd och åtgärdshistorik. Rå CV-fil skickas inte i den granskade agentvägen. Skärmbilder skickas inte med deklarerad produktionskonfiguration | Tolka ansökningsformulär, välja nästa åtgärd, föreslå eller utveckla svar och hjälpa till att fylla i ansökan | Google är biträde för prompts och svar endast när Paid Service och tillämplig DPA är verifierade. Konto- och användningsdata omfattas av andra Google-villkor. Nuvarande kontostatus är okänd och därför blockerande | Ingen EU-lagringsgaranti är verifierad för direkt Gemini Developer API. Googles villkor säger att paid prompts och svar tillfälligt kan lagras eller cachas i länder där Google eller dess ombud har anläggningar. Överföringsmekanism måste bekräftas i det gällande avtalet | Paid Service använder inte prompts eller svar för att förbättra Googles produkter, men begränsad säkerhetsloggning förekommer. Zero Data Retention kräver särskild kvalificering. Faktisk plan och ZDR-status är inte verifierade | `render.yaml:20`, `backend/src/services/applications/agent/llm.ts:20`, `backend/src/services/applications/agent/agent.ts:755`, `backend/src/services/applications/quizAnswerExpansion.ts:58`; [Gemini API terms](https://ai.google.dev/gemini-api/terms), [billing](https://ai.google.dev/gemini-api/docs/billing), [zero data retention](https://ai.google.dev/gemini-api/docs/zdr) |
| Resend | Sökandens namn, e-post och telefon; arbetsgivarens eller rekryterarens e-post; ämne och brödtext; CV och personliga brev; ansökningsspecifik svarsadress; inkommande arbetsgivarsvar; användarens svar från Jobbly; leverantörs-, leverans-, webhook- och meddelande-ID samt bilagemetadata | Skicka e-postansökningar och användarsvar, ta emot arbetsgivarsvar samt följa leverans | Personuppgiftsbiträde enligt Resend DPA, om kontots avtal är giltigt | Kontodata, loggar och API-poster lagras i USA oavsett sändningsregion. Resend anger EU–US DPF och SCC i DPA. Sändningsregion och livekonfiguration är inte verifierade | Resend anger normalt 30 dagars lagring av e-postdata. Jobblys normaliserade kopia i Supabase saknar egen tidsstyrd gallring. DPA anger radering av kunddata inom 90 dagar efter avslutat kundkonto, vilket inte är samma sak som en användares radering | `backend/src/services/applications/emailSubmission.ts`, `backend/src/services/inbox.ts`, `backend/src/routes/resendWebhook.ts`, `backend/src/routes/inbox.ts`; [Resend DPA](https://resend.com/legal/dpa), [regions](https://resend.com/docs/dashboard/domains/regions), [receiving](https://resend.com/docs/dashboard/receiving/introduction), [retention](https://resend.com/docs/dashboard/webhooks/how-to-store-webhooks-data) |
| Superwall | Supabase-användar-ID; auth-provider; abonnemangsnivå; StoreKit-prenumerationsstatus; enhets-, installation-, sessions-, paywall- och placementhändelser; parametrar som återstående dagskvot och kreditsaldo | Paywall, prenumerationsstatus, köp/återställning, analys, målgruppsregler och placeringar | Personuppgiftsbiträde enligt Superwall DPA för Jobblys data, om avtalet gäller; egen roll för vissa konto- och tjänstedata måste juridiskt bekräftas | Superwalls DPA listar flera USA-baserade behandlingar och globala Cloudflare-tjänster samt SCC för begränsade överföringar | Ingen per-användare-gallring är implementerad i appen. DPA beskriver lagring under avtalstiden och radering från live-system efter avslut och begäran, med reservation för backup. Dashboard- och kontoinställning är inte verifierad | `jobswipe/Services/SuperwallManager.swift:20` och placements i vyerna; [Superwall configuration](https://superwall.com/docs/ios/guides/configuring), [user properties](https://superwall.com/docs/ios/quickstart/setting-user-properties), [DPA](https://superwall.com/legal/dpa) |
| Apple, StoreKit och App Store | Apple-konto, betalningsuppgifter hos Apple, produkt- och transaktionsdata, prenumerationsstatus; vid Apple-inloggning token, eventuellt namn och e-post; plats till Apples systemtjänster när användaren tillåter det; eventuella Apple-diagnostikrapporter | Inloggning, köp, prenumeration, återställning, systemtjänster och App Store-distribution | Apple behandlar huvudsakligen data enligt egna villkor för dessa tjänster. Exakt ansvarsfördelning ska juridiskt bekräftas | Apples egna regioner och överföringsvillkor gäller; ingen mer specifik Jobbly-konfiguration är verifierad | Styrs dels av Apple. Jobbly lagrar inte kortuppgifter; appen och Superwall behandlar produkt-, transaktions- och abonnemangsstatus | `jobswipe/Services/SuperwallManager.swift:1`, Apple-inloggning i auth-koden; [StoreKit](https://developer.apple.com/storekit/), [Sign in with Apple](https://developer.apple.com/documentation/signinwithapple/authenticating-users-with-sign-in-with-apple) |
| Google-inloggning | OAuth-förfrågan, Google-kontoidentifierare, e-post och auth-token enligt valda scopes | Valfri inloggning via Supabase Authentication | Google behandlar data enligt egna villkor; exakt gemensamt eller självständigt ansvar ska juridiskt bekräftas. Supabase är Jobblys auth-biträde | Googles egna globala behandlings- och överföringsvillkor gäller; ingen separat Jobbly-region är verifierad | Googles lagring styrs av Google-kontot och avtalet. Jobblys auth-post ligger i Supabase tills kontoradering och eventuella backups löpt ut | auth-koden och Supabase OAuth; [Google OAuth authorization](https://developers.google.com/identity/authorization) |
| Arbetsgivare, rekryterare, deras webbplatser och ATS | De uppgifter och dokument som användaren skickar i ansökan, inklusive kontaktuppgifter, profil, personnummer när fältet fylls, svar, CV och personligt brev; tekniska ansökningsmetadata | Ta emot, bedöma och administrera jobbansökan | Normalt självständigt personuppgiftsansvariga efter mottagandet. Varje mottagares roll och information måste bedömas för den konkreta ansökan | Varierar per mottagare och kan innebära behandling utanför EES. Jobbly kan inte lämna en generell överföringsgaranti | Styrs av respektive arbetsgivares eller ATS-leverantörs information. Jobblys kontoradering återkallar inte redan skickade kopior; användaren måste kunna hänvisas till mottagaren | Backendens Playwright-ansökningsflöde och e-postflöde; den specifika platsannonsens mottagare och integritetstext |
| Arbetsförmedlingen JobTech JobSearch | Fritext, yrkes- och platsfilter, radie och ibland position när Jobblys kommunmappning inte kan ersätta koordinaterna | Söka och hämta offentliga platsannonser | Mottagare och tjänsteleverantör för egen API-drift; inget biträdesavtal är verifierat. Rollen ska bekräftas | Region, logglagring och eventuella överföringar är inte verifierade | Jobbly lagrar användarens valda sökfilter lokalt. JobTechs serverloggar styrs av Arbetsförmedlingen och är inte verifierade | `backend/src/services/jobtech.ts:3`, `jobswipe/Services/JobAPI.swift:75`; [JobSearch API](https://jobsearch.api.jobtechdev.se/), [JobSearch open data](https://data.jobtechdev.se/dataservice/jobsearch/) |
| GitHub Pages | IP-adress, webbläsar- och åtkomstmetadata när användaren öppnar den publika policysidan | Publik hosting av integritetspolicy och villkor | GitHub behandlar webbåtkomst enligt egna villkor; inget Jobbly-biträdesavtal är verifierat | GitHubs egna globala behandling och överföringsvillkor gäller | Styrs av GitHub för webbåtkomstloggar | `jobswipe/Resources/AppLegalLinks.swift:4`, publik URL och [GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement) |

### Leverantörer som inte ska stå som aktiva i policyn

- Qwen stöds av koden men både primär och fallback är deklarerade som Gemini i `render.yaml`. Ingen verifierad produktionsanvändning av Qwen har hittats.
- Browserbase används inte av den granskade Stagehand-implementationen. Stagehand är deklarerat avstängt och kör annars i lokal miljö med API:t avstängt.
- Visionskärmbilder till Gemini eller Qwen är deklarerade avstängda. Vanliga frågeskärmbilder skapas däremot lokalt i backend och lagras privat i Supabase när en användare måste svara på en ansökningsfråga.

## Verifierad datainsamling och tekniskt beteende

- Konto och auth: Supabase-ID, e-post, auth-provider, session och tokens. Sessionen ligger i iOS Keychain.
- Profil: namn, e-post, telefon, kön, full adress, personnummer, födelsedatum, medborgarskap, arbetstillstånd, erfarenheter, utbildning, önskade roller och orter, sökradie, erfarenhetsnivå och löneförväntan.
- Dokument: uppladdade och genererade CV samt personliga brev. Profil och dokument finns både lokalt och, vid synkronisering eller ansökan, i Supabase.
- Användning: swipe, spara, hoppa över, ansökningshistorik, status, felkoder, kompletteringsfrågor och svar.
- Meddelanden: arbetsgivares inkommande e-post, bilagemetadata och användarens svar från Jobblys inkorg.
- Köp: produkt, transaktion och abonnemangsstatus via StoreKit och Superwall; inga kortuppgifter i Jobbly-koden.
- Plats: valda orter, sökradie och vid platsbaserad sökning exakta koordinater. Koordinater sparas lokalt och skickas till Render; de kan nå JobTech enligt ovan.
- Drift: backend behandlar versions-, autentiserings-, status-, fel-, säkerhets- och leveransmetadata. Ingen fristående crash-SDK, reklam-SDK, IDFA- eller ATT-implementation hittades i repot.
- Automatisering: tillfälliga browserdata på arbetsgivarens ansökningssida. Felsökningsskärmbilder och HTML är deklarerade avstängda. En frågeskärmbild lagras däremot när användarens svar krävs; den raderas när frågan besvaras eller körningen avslutas, och kompletteringsläget löper ut efter 24 timmar.

## Säkerhet som kan beskrivas utan överdrift

En framtida policy kan sanningsenligt säga att Jobbly använder HTTPS för de verifierade tjänsteanropen, sparar appsessionen i iOS Keychain, använder privata Supabase-buckets för CV och ansökningsartefakter samt använder Row Level Security för de granskade användartabellerna. Policyn ska samtidigt säga att ingen teknisk lösning kan garantera absolut säkerhet.

Följande påståenden är inte tillräckligt verifierade och ska inte publiceras utan ytterligare bevis: att all data är krypterad i vila, att personnummer har särskild fältkryptering, att lokala dokument har explicit extra filskydd, att endast personal inom EU kan få åtkomst eller att Jobbly generellt ”säkerställer” alla internationella skyddsåtgärder.

## Apple-kontroll

- Guideline 1.5 kräver att appen och Support URL har ett enkelt, aktuellt sätt att kontakta utvecklaren. Det saknas i appinställningarna och Support URL är inte verifierad.
- Guideline 2.1 kräver en slutlig app med fungerande URL:er och utan platshållare. Den nuvarande policytexten uppfyller inte det kravet.
- Guideline 5.1.1 kräver en lättillgänglig policy som anger insamling, användning, tredje parter, lagring, radering och hur tillstånd återkallas. Den kräver också kontoradering i appen när konto kan skapas; Jobbly har ett sådant gränssnitt men raderingen är tekniskt ofullständig.
- Guideline 5.1.2 kräver tydlig information och uttryckligt tillstånd innan personuppgifter delas med tredjeparts-AI. Den nuvarande onboardingtexten är endast bunden till fortsatt registrering, namnger inte Gemini och har ingen återkallelse eller serverkontroll.
- App Store Connect kräver en Privacy Policy URL för iOS och korrekta integritetssvar även för inbyggda tredjeparts-SDK:er.
- Support URL måste leda till faktiska kontaktuppgifter och är ett separat obligatoriskt metadatafält.

Officiella källor: [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/), [Manage app privacy](https://developer.apple.com/help/app-store-connect/manage-app-information/manage-app-privacy/), [Platform version information](https://developer.apple.com/help/app-store-connect/reference/app-information/platform-version-information).

## E. Change summary

- Den befintliga texten bedömdes som blockerad i stället för att fyllas med antaganden.
- Alla faktiska datakategorier i app-, backend- och databasflödena kartlades, inklusive kön, exakt plats, personnummer, dokument, användarhistorik, meddelanden, Superwall-händelser, status/fel och tillfälliga ansökningsskärmbilder.
- Personnummerbeskrivningen konstaterades vara felaktig eftersom appen i dag kräver personnummer för att profilen ska anses komplett och för att skicka ansökan.
- Resendbeskrivningen utökades till det verkliga ansöknings- och inkorgsflödet. Användning för auth-mejl lämnades obekräftad.
- Gemini-payloaden preciserades. Rå CV-fil och skärmbilder är inte del av den deklarerade produktionsvägen, men full profil, formulärinnehåll, svar och extraherad brevtext kan skickas.
- Qwen och Browserbase uteslöts som aktiva mottagare. JobTech och GitHub Pages lades till eftersom faktisk data kan nå dem.
- Den nuvarande kontoraderingens lagringslucka identifierades och konkreta raderings- och gallringskrav lades till.
- Superwall beskrevs som SDK-baserad händelse- och prenumerationsbehandling, inte som cookies. Ingen reklamspårning eller IDFA-användning hittades i repot.
- Säkerhetstexten begränsades till verifierbara åtgärder och undviker absoluta garantier.
- Den befintliga juridiska URL:en behölls. Både integritetspolicyn och användarvillkoren har rensats och skrivits om lokalt; publicering ska ske först efter att appen och ägarbekräftelserna matchar texten.

## Underlag för juridisk granskning

Svensk dataskyddsjurist bör särskilt granska personnummer, rättslig grund för AI och mottagarutlämnanden, intresseavvägningar, lagringstider, konsekvensbedömning, internationella överföringar och ansvarsfördelning. IMY beskriver personnummer som extra skyddsvärda och anger att behandling utan samtycke bara får ske när den är klart motiverad av ändamålet, säker identifiering eller annat beaktansvärt skäl: [IMY om personnummer](https://www.imy.se/link/bdea7626cc4e462eb4afd088de8d9ff5.aspx).
