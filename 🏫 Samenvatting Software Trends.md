---
sticker: emoji//1f3eb
---
#🏫School #Software_Trends #GDPR #Reactive_Programming #WASM #Svelte
[[2024-01-08 Exam Software trends|Examen 08-01 15:00-17:00]]
# GDPR
## Wat?
- Wetgeving in Europa van 2018
- Burger beschermen tegen grote Tech bedrijven
- Persoonlijke data
	- Ethiek
	- politieke voorkeur
	- religie
	- genetische en biometrische data
	- gezondheid
	- Seksuele voorkeur
## Waar?
Niet Europese bedrijven die:
- Goederen/diensten leveren in EU
- Europese burgers volgen op Europese grondgebied

## Wanneer niet van toepassing.
- Bedrijf met <250 werknemers (minder strikt)
- Persoonlijk gebruik (bv lijst van je vrienden)

## Individuele rechten
Recht op:
- informatie
- vergeten te word
- correctie/rechtzetting
- verwijderen data
- verminderde verwerking
- portabiliteit
- protest
- weigering automated decision making

## GDPR vragen bij Software development
### 1. Heb ik de data echt nodig?
- Minder data -> veiliger
### 2. Encrypt alle persoonlijke data
- gevoelige data moet veilig zijn
- Breaches zijn onvermijdelijk
### 3. Gebruik HTTPS 🔐
- Contact forms bevatten vaak gevoelige data
- HTTPS encrypt automatisch met SSH
### 4. Consent moet open zijn
- Geen pre-ticked checkboxes
- Opt-in i.p.v. opt-out

![[Pasted image 20240101115830.png]]
### 5. Opt-in moet [granulair](https://www.encyclo.nl/begrip/granulair) zijn
- Opsplitsen in meer opties
- bv: Verschillende cookies als elk een aparte opt-in

![[Pasted image 20240101115802.png]]
### 6. Wees specifiek over 3rd Parties 
- Geef andere partijen aan die deze data zullen gebruiken

![[Pasted image 20240101120103.png]]
### 7. Terms & Conditions apart 📄| ✅

![[Pasted image 20240101120151.png]]

### 8. T&C moeten zichtbaar zijn📄

![[Pasted image 20240101120234.png]]

### 9. Gebruikers moeten consent kunnen intrekken
- Gebruik van unsubscribe
- Toe staan om te op-out'en later

### 10. Pas cookie beleid aan 🍪
- Cookies mogen enkel
	- Als het wettelijk verplicht is
		- Leeftijd voor gokwebsites
	- Legitiem belang heeft
		- Froude preventie
	- Noodzakelijke data is
		- Bankrekening van een leverancier
	- User consent heeft
### 11. Vermijd security vragen met persoonsinformatie
bv:
- Hoe noemt je eerste hond
- Wat was je eerste school
- Hoe noemt jouw moeder

### 12. Informeer over IP-logs
- Als ip's (bv login attempts) gelogd worden -> informeer gebruiker
 ![[Pasted image 20240101121748.png]]
<div style="page-break-after: always;"></div>

### 13. Verwijder persoonlijke data na de pay-gateway
- Voor e-commerce: data na 60 dagen verwijderen
- Geen data via pay-gateway bewaren

### 14. Users mogen business intelligence tracking weigeren

### 15. Verwijder ongevraagde tracking data 
- Users mogen niet zonder toestemming worden geanalyseerd (gebeurde pre GDPR vaak op ecommerce websites)
[DPR Checklist](https://learning.ap.be/pluginfile.php/2717830/mod_resource/content/1/checklist_gdpr%20%281%29.pdf)
---

# Reactive Programming
## Wat is het?
- Principe voor responsieve software systemen te bouwen

## Probleem met Async
- Tegenwoordig veel asynchroon (API calls, databases, file systems)
	- Moeilijk want:
		- Bevatten cancellation, retry, chained async calls etc.
		- Dit kan snel voor bugs zorgen
### Oplossing:
- Gebruik streams
	- dynamisch
	- kan continue nieuwe gegevens krijgen
	- zijn oneindig
		- bv coordinate krijgen door het bewegen van een muis
- Promises:
	- eerste oplossing voor call-back functions
	- nadelen:
		- Moeilijk combineren met andere async concepten
		- lost call-back hell niet volledig op (bv nesting door call na een andere call te doen)
		- geen retry of cancel mechanisme
		- geeft maar 1 waarde terug
- Observers
	- Registreren zich op een stream
	- Luisteren naar nieuwe gegevens
	- 

## Concepten

### Observable:
- Gegevensstroom over bepaalde tijdsperiode
- Kan oneindig lang luisteren of krijgt een levensduur
### Observer:
- Functie die opgeroepen wordt als er nieuwe data komt
- Ontvanger van gegevens van observable
### Subscription
- Eenzijdige verbinding tussen observer en observable
- Observables doen niets tot er een subscribe wordt opgeroepen
### Operatoren
- Functies om transformaties uit te voeren op een Observable
- Krachtige manier om streams te manipuleren, filteren of te combineren

## Cold VS Hot Observables
### Cold ❄️
- Wordt pas gestart bij een subscribe
- Unicast: Maar 1 listener
- eigen execution context
	- Elke subscribe is een eigen execution
	- bv: YouTube video kijken

### Hot 🔥
- Kan al bezig zijn bij subscribe
- Multicast: Meerdere listeners
- Gedeelde execution context
	- iedereen krijgt dezelfde data
	- bv: Twitch livestream bekijken

## Operators
<iframe width="110" height="200" src="https://www.myinstants.com/instant/sade-smooth-operator-71248/embed/" frameborder="0" scrolling="no"></iframe>
- Maken observables echt nuttig
- Twee verschillende soorten:
	- Creation Operators
	- Pipeable Operators

### Creation Operators 🛠️
Wat?
- Functie voor maken van nieuwe observables
Doel?
- Genereert observables op basis van verschillende bronnen
- bv uit arrays, timers, events, HTTP Requests
Voorbeelden:
- Of()
- From()
- Interval()
- Timer()
### Pipeable Operators ||
Wat?
- Functie voor transformeren en bewerken van observables
Doel?
- Manipuleren van gegevensstromen binnen een observable
Voorbeelden:
- Map()
- Filter()
- First()
Tip: Piping teken bij Linux

### Higher-order operators
Observables kunnen soms zelf een stream van observables geven.
Voorbeelden:
- ConcatAll()
- MergeAll()
## Marble Diagrams ‼️
Wat?
- Visuele representatie van operator's functionaliteit
Waarom?
- Operators zijn vaak tijd gerelateerd
- In woorden moeilijk te beschrijven hoe ze werken
https://rxmarbles.com/

### Operatoren moet je kunnen uitleggen aan de hand van de marble diagram

![[Pasted image 20240101142146.png]]![[Pasted image 20240101141648.png]]![[Pasted image 20240101141655.png]]![[Pasted image 20240101141700.png]]![[Pasted image 20240101141708.png]]![[Pasted image 20240101141712.png]]

--- 

# Web Assembly (WASM) <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1f/WebAssembly_Logo.svg/600px-WebAssembly_Logo.svg.png" style="height: 18px; ">
## Wat?
- Nieuw manier voor back-end code op web te implementeren
- Vroeger alleen JavaScript
- Compilatie target voor broncode
- Laat toe om code uit te voeren tegen (bijna) de snelheid van native code.
- geen nieuwe taal te leren
## Doel?
- Code kan snel op verschillende platformen uitgevoerd worden
- Low level assembly taal dat leesbaar is door mensen
- Secure:
	- wordt uitgevoerd in een sandbox omgeving
	- respecteert browser's veiligheidsnormen
- Moet samenwerken met andere web technologieën en backwards compatible zijn. 

## Waarom geen Java Virtual Machine?
WASM ...
- is sneller
- is dichter bij echte machine code
- heeft geen garbage collection
- kan met JS Communiceren
- loopt in sandbox waardoor meer secure

## Compiler vs Interpreter
- Vertaling nodig tussen programmacode en machinecode 
- Twee verschillende manieren 
	- Interpreter: code wordt lijn per lijn vertaald  
	- Compiler: code wordt op voorhand vertaald
### Interpreter
- Code wordt lijn per lijn geïnterpreteerd
- ideaal voor web development want
	- snel gestart
	- kan code direct uitvoeren zonder compilatie
	- interpreters zijn eenvoudig op te zetten (bv chrome dev tools)
- Inefficient bij code die herhaald word
	- code wordt opnieuw geïnterpreteerd bij elke loop
### Compiler
- Code wordt helemaal op voorhand vertaald
- Initieel trager dan interpreters
- loops zijn sneller (1x vertaald)
- Kan extra optimalisatie stap uitvoeren
	- Kent code volledig en kan wijzigingen doen voor efficiëntie
	- Interpreters niet want zijn anders te traag
## JIT Compiler
- Combineert Interpreter en Compiler
- Sneller opstarttijd en beter optimalisatie
### Warm/hot
- Oplossing voor loop probleem
	- Als stuk code meer dan 1 maal wordt uitgevoerd -> <span style="color:#fcba03;">Warm</span>
	- Als het nog vaker uitgevoerd -> <span style="color:#b80000">HOT</span>🔥
### Baseline compiler
- <span style="color:#fcba03;">Warme</span> code naar baseline compiler
- Compiled dit en slaagt deze op
- Zelfde code en variables?
	- gebruik opgeslagen code
- Runt parallel met Interpreter
### Optimization compiler
 - Voert optimalisaties uit
 - Te lang voor baseline compiler? -> optimization compiler
	 - betere uitvoersnelheid
 - Als code <span style="color:#b80000">HOT</span> word -> Optimization compiler
 - Maakt veronderstellingen van code
	 - Als code plots niet klopt door veronderstelling -> Trashing
	 - Optimalisatie laten vallen en op nieuw uitvoeren

### Performance
#### Non JIT:
![[Pasted image 20240101152035.png]]
#### Met JIT
![[Pasted image 20240101152050.png]]
Parse: lezen van source code 
Execute: Tijd code uitvoering
Garbage collection: Tijd om geheugen op te kuisen
Compile + optimise: Tijd voor baseline en optimizing compiler
Re-optimize: verloren tijd door verkeerde assumpties (trashing)
Stappen gebeuren door elkaar

## Assembly
- Low level programeer taal
- Direct vertaald naar machinecode
- Menselijk leesbaar
- Ander architectuur van processor -> Ander dialect
	- x86 processor anders dan ARM
## Intermediate Representation
- Taal tussen codeer taal en assembly taal
- Enkel compileren naar IR
	- Compiled voor jou naar juiste architectuur
- Geen nood om elke taal naar elke architectuur te vertalen
### WASM
- Tussen IR en architecturen.
- Machine taal voor conceptuele machine
- Is dus virtueel
- Dicht bij echte machine
- Geen rechtstreekse mapping
  
![[Pasted image 20240101153635.png]]
- Wasm files zijn binary files als WAT files
- Kunnen zelf geschreven worden
---
# Svelte <img src="https://uxwing.com/wp-content/themes/uxwing/download/brands-and-social-media/svelte-icon.png" style="height:25px"/>
## Wat?
- Open source frontend framework
- JS  en TS support
- Compiler based
- Zeer compact
## Virtual DOM
### DOM
- Html boomstructuur van je pagina
- JS heeft toegang tot DOM voor html dynamischer te maken
- Via DOM elementen toe voegen, oproepen, aan passen, verwijderen
- Aanpassingen aan dom zijn snel, maar pagina moet opnieuw renderen wat traag is
### Virtueel
- Lightweight replica van DOM in geheugen
- Bestaat uit objecten
- Virtuele DOM aanpassen past niet direct de echte DOM aan
- Gebruikt door Vue, React, Preact
- Alleen de aangepaste elementen worden geüpdatet
## Reconciliation Algorithm (React)
- Efficiëntste manier op een structuur aan te passen?
- 1000 elementen vergelijken zorgt voor miljard vergelijkingen
- Vergelijkt chronologisch, als een lijst aanpast moet hele lijst opnieuw gerenderd worden
## Svelte Compiler
- Geen virtuele DOM
- Geoptimaliseerde compiler
- Efficient DOM Manipulatie
- Code na compile is zeer compact
- Variabelen kunnen als Reactive gedeclareerd worden, alleen dan wordt UI geüpdatet
## Svelte Nadelen ➖
- Jong
- Kleine community
- Weinig packages
- Misbruikt code constructs van js
	- export voor properties
	- $: label voor computed values
- Eigen niet-standard language features
	- if en for loops syntax
	- eigen eventing system
- Is bijna een eigen taal
- Reactive waarden zijn soms moeilijk
- Moeilijk te refractoren
## Svelte Voordelen ➕
+ Minder lijnen code nodig dn react
- Build in async
- Eenvoudig voor beginners
## SvelteKit
- Full stack framework op Svelte
- Ingebouwde router
- Kan offline werken
- Preload pagina's
- Kan server-side rendering (SSR), client-side rendering en build-time prerendering.

---

# GraphQL
## Wat?
- Nieuwe API Standaard door Meta
- Opensource met Grote community
- Gebruikt declaratieve data fetching
	- Client beschrijft exact wat hij nodig heeft
- Server heeft één enkele endpoint en antwoord op queries
- Kan tcp, websockets etc gebruiken
- Kan door elke taal gebruikt worden
## Waarom?
- Meer mobiele applicaties
	- Minder processing power
	- slechter internet
	- Beter minder traffic genereren
- Client krijgt exact en alleen data die hij nodig heeft
- API moet snel evolueren en snel opeenvolgende producten itereren.

## Rest 
- Stateless server
- Gestructureerde toegang to data
- Niet flexible en efficiënt genoeg voor mobile
### Voordelen ➕
- Snel op te zetten
- Standaard http calls
### Nadelen ➖
- Geen relationele data
- Geen ordening of paginering
- Geen notificatie bij nieuwe data
- Als een endpoint niet genoeg data geeft moeten er meerdere calls uitgevoerd worden
	- Slecht bij lijsten
- Overfetching
	- Client krijgt meer data dan gewenst binnen
- Underfetching
	- Meerdere requests nodig voor data te krijgen

## GraphQL
- Gebruikt een type systeem om de mogelijkheden van de API te definiëren.
- Schema geldt als contract tussen client en server
- Frontend team en backend team kunnen volledig onafhankelijk van elkaar functioneren.
- Strongly typed:
	- Server bepaalt applicatie specifiek systeem
	- Op compile time checken of query geldig is
	- Server kan bepaalde garanties geven over de vorm en types van het antwoord
- Entiteiten die kunnen worden bevraagd
- Wordt bepaald wat allemaal kan worden afgehaald
- Subscriptions
	- Real-time connectie met de server
	- Bij een update wordt deze naar de client gestuurd
	- Is dus een stream
### Use case
- Server met een verbonden database
	- Gebruikt bij greenfield projecten
	- gebruikt webserver die GraphQL Implementeert
	- Server maakt db queries en maakt daarop een response
	- ![[Pasted image 20240102132435.png]]
- Als dunne laag waar legacy system(en) achter zit
- Aanpak met databases en legacy systemen
- Met bestaande systemen
	- Handig voor bestaande API's te kopellen
	- Unificeren van systemen en complexe logica te verbergen
	- Bronnen maken niet meer uit
	- ![[Pasted image 20240102132357.png]]
- Hybrid
	- Server met database, die ook andere api's oproept
	- ![[Pasted image 20240102132449.png]]

### Declaratieve data fetching
- Beschrijf de data requirements (bv in een query)
- Toon data in de UI

### Introspection
- De server weet wat het schema is, maar de client niet
- Schema opvragen a.d.h.v. een query
- Dynamisch een GraphQL  playground te genereren

---

# Smart Data
## IMEC
SWOT
- Strength
- Weaknesses
- Opportunities
- Threats
![[Pasted image 20240102133659.png]]

## Big Data
### 5 V's
- Volume
	- te groot voor een laptop
- Velocity
	- Continue aanvoer van data
- Variatie
- Verschillende bronnen in on-, semi- of gestructureerde database
- Veracity (waarachtigheid)
	- Data moet consistent zijn, kwaliteit wordt actief bewaakt
- Value
	- Data is nog geen informatie
### Beperkingen
- Data leeft in silo's -hard to find
- Geen standard tussen databases - Hard to understand
- Nieuwe vraag -> Nieuw maatwerk -Hard to combine
   -> Eerste vier V's leiden tot systeem met veel Big Data
## Fair Data
- Findable
- Accesible
- Interoperable
- Reusable
Fair data is technisch gezien klaar voor hergebruik
Data is waardeloos als het in foute context gebruikt wordt

### Van big naar fair
- F: Data moet makkelijk terug te vinden zijn
- A: Moet makkelijk toegankelijk zijn
- I: Data moet kunnen samenwerken met andere data
	- Syntax & metadata moeten dit garanderen
- R: Data moet herbuikbaar zijn

## Actief data kwaliteit bewaken
- Automatische controlle van data
- Manueel werk analyst onvoldoende.
- Systeem moet data automatisch kunnen begrijpen

## Smart Data
### Big naar smart in 5 stappen
- Betekenis toevoegen
	- 
- Context toevoegen
	- Truth bestaat niet echt
	- Behandel metadata als Data. Link naar bron, geef aan hoe bruikbaar data is
- data in graphs structureren
	- Geef netwerk-achtige structuur
	- Nieuwe data? Nieuwe edge
	- Linkable!!
- Agile methodology
	- Je kan niet alles op voorhand weten
	- Data lake over data warehouse want flexibeler
- Gebruik standaarden
	- Zeker met externe wereld wil communicate.
	- RDF, GraphQL

### Smart data platform
Moet optreden als data broker tussen bedrijven, overheden,...
### Smart and fair
liggen dicht bij elkaar
- Fair: Technische aspecten
- Smart: Gaat ook over andere aspecten zoals Trusted, contextual, relative
- Smart data is dus Fair data waar, doordat de data Fair is, een extra vorm van kwaliteitscontrole is kunnen gebeuren
- 
## Open data
Links van meneer werken niet eens, That's all folks
## Linked Data
### Wat is Web?
Combinatie van internet, documenten en links
### Probleem?
- Willen niet altijd documenten, willen antwoorden op vragen
- HTML file die gerenderd is lezen, en informatie in staat vinden
	- Moeilijk voor computers
	- Google maakte PageRank of the schatten of je antwoord er in staat
- Gestructureerde data wordt niet-gestructureerd getoond op webpagina's
- Willen een systeem waar we makkelijk informatie vinden
### Semantisch Web
- Goed voorbeeld is Wikipedia die in de buurt komt
- Is een web van gelinkte Data
- Huidige weg is web van gelinkte data
	- Bestaat al maar in veel verschillende formaten
	- Data is niet samenhangend

### Data op web
- Relationele DB's
- Files zoals XML, CSV, JSON
- API's
- Te veel formaten
- Niet van zelfsprekend om data samen te nemen 
### RDF
- Kan worden gesteriliseerd op verschillende manieren
	- RDF/XML
	- JSON
- Json-LD Is beter
### Json-LD
- Bevat naast data ook metadata
- LD = Linked Data
- Is machine-readable en discoverable
- Nodig om verbanden te laten zoeken uit verschillende bronnen door machines

### Verschillen RDF en Relationeel model
- Relationeel:
	- Tabelstructuur
	- Hebben eigenschappen
- RDF:
	- Alles heeft links met elkaar
	- Graph structuur
### Systeem verbeteren?
- Alles benoemen met URI (Unique Resource Identifier)
- i.p.v. ID's Gebruiken we URL
- Linked Data
### Basis principe Linked data
- URI's gebruiken als naam
- Op de IRL relevante data voorzien
- Link naar andere URI's voorzien
	- Maakt internet een web 🕸️

Opvragen kan via GraphQL, Neo4J etc

---

# Low Code & No Code
## Wat?
WYSIWYG: What you see is what you get
### No code 🚫
- Drag and Drop
- Geen toegang tot code
- Geen mogelijkheid tot uitbreiden

### Low code ↘️
- Idem als no code maar mogelijkheid tot eigen code toevoegen
- Meer technische kennis nodig

## AI 🐘➡🏠
- Genereerd nieuwe input gebaseerd op gekende input
- Meerdere diepe neurale netwerken
	- Generator: Maakt data
	- Discriminator: Evalueert data

### ChatGPT
- Is een LLM (Large Language Model)
- Getrained met
	- Supervised learning
	- Reinforcement Learning from Human Feedback
- Capabiliteit: Made waarin een model zijn objective functie kan verlagen
	- Kostfunctie -> doel van het model bv expressies zo laag mogelijk te maken
- Alignment: Objectieve functie consistent met intenties?
	- Typisch getrained op data v.h. internet. Kan problemen geven
- Kan feiten verzinnen
- Niet verifieerbaar
- Toxische output bv scheldwoorden, racisme etc

#### Transformer
- Een deep learning model dat textkst inneemt en via een convolutional neural network aan Natural Language Processing doet
- Generative Pre-trained Transformer is een specifieke transformer, getrained op data van Wikipedia
- Deze modellen kunnen teksten vertalen en het meest waarschijnlijke volgende woord in een zin voorspellen (masked language modeling).
	- Kan structuur van taal leren
- Probleem!
	- Kan correcte zinnen maken die inhoudelijk fout zijn
#### Gebruik van menselijk Feedback
- 3 stappen
	- Supervised fine-tuning op kleine dataset: SFT model
		- Lijst van props worden aan gebruikers gegeven, en geven hun verwachte output
		- Is menselijk dus traag en duur
		- Zeer kwalitatief resultaat
	- labellers stemmen op SFT Outputs: RW Reward Model
		- Laat labellers antwoorden rangschikken via reinforcement learning
			- Meest gelikte: meeste punten
			- Rangschikken is sneller dan zelf antwoorden
	- Verdere finetuning: PPO Proximal Policy Optimization
		- Direct updaten van de policy -> continue verbetering
		- Gebruikt antwoorden van SFT model en rewards van RW
![[Pasted image 20240102155454.png]]
#### Nadelen
- Reflecteert voorkeur van labellers
- Beginfase is ook gebaseerd op menselijke input
- Maakt GPT mogelijk Biased
- Geeft wenselijke antwoorden maar niet noodzakelijk juiste antwoorden
#### Voordelen
- Zal development landscape veranderen
- Specialisatie in een vak gaat verminderen
- Bied kansen om sneller bij te leren

---

# Quantum Computing
## Double slit experiment
Kans dat deeltje op een plaats uit komt is een symmetrisch golfpatroon
![[Pasted image 20240102160530.png]]
Als deeltes geobserveerd worden geeft dit niet dit patroon en heeft het deeltje 50% kans om boven of vanonder uit te komen.

## Superpositie
- Een quantum bits (qubit) is tegelijkertijd 0 en 1
- Door te meten staat de positie vast als ofwel 0 ofwel 1
- 0-qubit: |0>
- 1-qubit: |1>
- Superposities
	- |+>
		- (|0> + |1>) / sqrt(2)
	- |->
		- (|0> - |1>) / sqrt(2)
### Hadamard Gate (H-gate)
- Als een Hadamard gate toe gepast word op |0> wordt het
	- (|0> + |1>) / sqrt(2)
- Als dit op |1> gebeurd wordt het
	- (|0> - |1>) / sqrt(2)
- Dus 0 -> +
- 1 -> -
- Als je H-gate opnieuw toepast op |+> of |-> wordt het terug 0 of 1 respectievelijk
- Een meting vernietigd een super positie
	- Alleen meten nadat alle bewerkingen klaar zijn
## Entanglement
- Twee electrons die gekoppeld zijn aan elkaar
- Als de ene 0 is, is de andere 1
- Als de ene gemeten word, staat de andere ook vast
## Verschil tussen bits en Qubit
| Klasiek | Quantum |
| ---- | ---- |
| Transistoren op 0 en 1 te genereren in volt waardes | Electrons bevatten informatie zoals spin, geven een waarden tussen 0 en 1 |
| modernce CPU heeft veel transistoren | Eigenschappen van Quantumfysica kunne bits 0 en 1 tegelijkertijd zijn |
| computer is deterministisch | Kwantumcomputer(QC) Is niet deterministisch |
| computer met 3 bits kan 3 bits opslagen | een QC met 3 quibuts kan 2³ bits opslagen |
| Computers met n bits kan dus een getal van n bits onthouden | computer met n qubits kan 2^n opslagen. wat exponentieel groter wordt |
Qubits kunnen sneller werken doordat ze simultaan zijn

Werkt momenteel alleen onder lage temperaturen en is niet mobiel noch praktisch
Het vereist een gewone computer voor validatie 

## Quantum gates
- cx() : controlled not gate: de qubits worden 'verstrengeld' zodat hun waardes gekoppeld zijn.
	- Tweede qubit word omgedraaid als de eerste 1 is
	- Dit resulteert in een gelijke verdeling van de waardes <00> en <11>. Dit heet een Bell state, omdat er maximale verstrengeling is: de waarde van de ene bepaalt volledig de waarde van de andere.
- Boodschap versturen op afstand
	- X functie: Not gate: omkeren qubit
	- Z functie: Flip gate: 0 blijft 0, 1 wordt -1
- Superdense Computing
	- Een aantal klassieke bits aan informatie delen, door een kleiner aantal qubits door te sturen, op voorwaarde dat de partijen toegang hebben tot eerder verstrengelde qubits.
![[Pasted image 20240102164523.png]]

## Algoritmes
### Deutsch-Jozsa probleem
QC met volgende kenmerken:
	- Input is array van binaire waardes
	- Output is 0 of 1 voor elke bit
	- ofwel is de output alleen maar 0, of wel alleen maar 1, ofwel de helt 0 en de helft 1
- je krijgt een 5 bit input wat 32 combinaties heeft
- als je de combinaties deelt door de helft + 1 krijg je het gewenste resultaat want
	- Stel dat je de 50/50 combinatie krijgt -> als je 16 keer 0 toevallig kreeg, is de 17de sowieso 1
	- zo dien het 0 is => antwoord is 0
- Bij Quantum moet je maar 1 maal checken want superposities
### Grover's Algorithm
- Lijst met N elementen kan je doorzoeken met verschillende algoritmes.
- Max sqrt(N) stappen nodig.
- Stappen in het algoritme: 
	1. Qubits in superpositie met Hadamard gate 
	2. Implementeer een 'oracle functie' die de correcte staat weergeeft (wat je zoekt) 
	3. Maak een amplificatie circuit, die in essentie telkens de goede status 'vergroot' en alle andere verkleint. 
	4. Meet qubits. Door de amplitude is de meest gemeten qubit de gezochte waarde.

### Shor's Algorithm
- Dit algoritme vindt de priemfactoren van een getal
- Zoekt voor geheel getal een deler. Herhaaldelijk op alle stukjes toepassen levert dan een volledige ontbinding.
- zoekt via een discrete quantum Fourier transformatie naar alle mogelijke potentiële delers van een getal
- Voor échte delers, hetgeen we zoeken, gaat het signaal versterkt worden
- RSA werkt op grote priemgetallen
	- Vermenigvuldigen is snel en eenvoudig 
	- terug ontbinden is traag
		- Quantum kan dit wel erg snel
		- Onderzoek om dit op te lossen met quantumcryptografie

## Decoherence & Fault Tolerance
### Decoherence
- Coherence time : de tijd waarin een qubit in superpositie kan blijven (enkele milliseconden)
- beperkt de mogelijke duur om een berekening uit te voeren
- rond liggende deeltjes kunnen een qubit verstoren door bv botsingen
- Heeft stroom nodig zoals RAM

### Fault Tolerance
- Decoherence -> hindered grote berekeningen -> QC is bedoeld voor grote berekeningen
- In onderzoek naar fouttolerante algoritmes maken 

Wordt nog volledig ontwikkeld maar er bestaat al software en algoritmes voor. Mogelijks later toegang via API's

--- 

# Mojo
## wat?
- Systeem programmeertaal zoals RUST en C++
- Mogelijkheid om gebruiksgemak van python libraries te combineren met C (taal) performantie
- Voornamelijk voor AI

## Vergelijking python
- Gelijkaardige syntax
- Ambitie om superset te zijn van Python
	- Python code is compileerbaar naar Mojo
- Heeft 
	- Type checking
	- Memory safety
	- Compiled Language met Ahead of Time en JIT
		- Kleinere memory footprint
		- Snellere opstartminder stroomverbruik
- fn ipv Def
## Variabelen, functies en meer
- var: mutable (aanpasbaar later)
- let: immutable (kan niet aangepast worden)
- functies moeten argumenten met types hebben
- memory safety
	- Kan met pointers werken
	- Moet voldoen aan ownership rules (anders geen memory safety)
- borrowed: Argument word alleen geleden en niet aangepast (immutable)
	- Hierdoor geen koppie nodig -> betere performantie
	- Is eigenlijk by default
- inout: Data wordt wel in functie aangepast 
	- De gegeven parameter wordt als memory aangepast en is de originele waarden ook aangepast
- owned: Data wordt wel in functie aangepast als kopie
	- Originele waarden van de gegeven argument blijft hetzelfde
- Struct: OOP manier (object)

--- 

# Veel Success
Examen in lokaal **Via.01.30** op **Maandag 08.01 tussen 15:00 en 17:00 uur**
