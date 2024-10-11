[[Anatomy of an application]]
[[Styling Components]]


En prop kan være hva enn du kan putte inn i en variabel, som objekter, arrays eller funksjoner.
En komponent kan ta imot props ved at de settes inn i komponent funksjonen:
		- const Komponent = (Props) =>
	Streng regel: Props er read-only! husk på dette!
		- en komponent skal ALDRI kunne endre på props som er sendt in. 
Props:
	- Sender et argument til komponenter
	- bruker HTML lignende attributt syntax
	- Mottakende komponent har tilgang til props objekt
	- tillater for bedre gjenbruk av komponenter

Children props:
	- Du kan sende inn en children som prop, hvor komponenten mottar et barn av det du sender inn. 
	- Du kan eks sende inn en div som et barn.

Fragments and Mapping data to JSX:
	- Fragmenter brukes siden komponenter kunn kan ha èn forelder. 
			- <> </> Brukes for å legge rundt koden i en komponent for å tilsvare det.
		- på denne måten vil browseren rendre de barna du har i koden uten en foreldre node.
	- map er ikke spesifikt til React, men brukes ofte i react applikasjoner
		- Det er en JavaScript funksjon som kan brukes til Arrays
			- Den tar hvert element i et array og mapper det til noe annet
				- Dette lager et nytt array
![[Pasted image 20241010103538.png]]

![[Pasted image 20241010103631.png]]
Dette vil gi et tr element til alle husene i arrayet.


The Key prop:
	Et nøkkel prop er alltid trengt når arrays av react elementer er laget!
		- Nøkkelen gjør at react vet at elementer er rendret, og det gjør at den ikke trenger å rendre alt på nytt dersom du legger til noe nytt i arrayet.
	Velge en Key verdi:
		- Bruk ID elementet om det er tilgjengelig
		- ellers uansett hvilken kombinasjon av elementer som er unike
		- siste utvei: indexen gitt av map funksjonen.

Extracting components:
	bruke eksemplet over mes hus arrayet:
		Du kan ta hele tr elementet og sette det inn i en egen komponent hvor vi sender inn house som et prop.
		![[Pasted image 20241010104642.png]]
		Aldri bruk nøkkel propen utenfor konteksten av arrayet!
		Derfor har du fjernet key fra tr elementet i HouseRow. Du sender nøkkelen inn fra komponenten arrayet tilhører!
		![[Pasted image 20241010104742.png]]
	ved å dra ut liste elementene fra houseList inn i houserow har du skapt en klarere separasjon av elementer
I HouseRow nå må vi referere til house i alle kall, du kan dekonstruere props som du sender inn å korte ned på dette og dermed håndtere DRY
![[Pasted image 20241010105057.png]]
Du kan nå også velge å ta vekk House ordet, du tar imot de forskjellige verdiene fra house og trenger dermed ikke ordet house.
	- Dette gjør koden mer gjennbrukelig for vi sender kunn inn primitive og ikke et komplisert hus objekt. 
	- I dette tilfellet kan listen av props bli lang, og du kan derfor bruke en spread operator i JavaScript { ... h } hvor den vil dele opp verdier i objektet og sende de inn hver for seg
		- Vær forsiktig med dette, dersom vi legger til nye elementer som vi ikke trenger i listen vil fortsatt bli sendt over uten å bli brukt. Det vil kunne ha en negativ reaksjon på preformasjonen av applikasjonen.
	- Dersom radene av hus ikke brukes andre steder enn hus listen er det best og bruke den første metoden og sende inn hus objektet og heller liste det opp slik. 


Hooks:
	- Hooks er en funksjon
	- Starter alltid med ordet "use"
	- Hooks inkapsler kompleksiteten og vi kan bruke den uten å egentlig vite hva den gjør
	- Gir tilgang til react sine funksjoner inni komponent funksjoner.
	- du kan også lage dine egne hooks
	- dersom du vil bruke hooks må du også importere dem.

	Regler for hooks:
		- Du skal KUNN kalle hooks på top nivå 
				- De skal alltid bli kalt
					- Det er ikke lov å kalle dem betinget, pakke dem 
						inn i en if settning.
					-De kalles i den samme orden
		- du skal kunn kalle hooks i funskjons komponenter
				- noen kall utenfor en slik komponent vil gi error
			- det eneste unntaket fra dette er en selvlaget hook
				- De kan kalle til andre hooks om nødvendig.

State:
	Den mest brukte Hooken
		- State er data som er holdt internt av en komponent.
![[Pasted image 20241010110645.png]]
Dersom du legger til noe bakerst i flowen vil ikke rect vite at det er lagt til noe, den letteste måten og endre dette på er ved å bruke State.

House arrayet har blitt gitt et nytt navn houseArray
![[Pasted image 20241010110922.png]]
 - houses er her listen av objekter som allerede sitter i houseArray
 - setHouse prefixet er det som gjør det mulig å endre houses arrayet.
 - På denne måten er ikke arrayet direkte brult lengre, det er bare den initisielle verdien av state.
 - OBS: Kallet til UseState skal altid gjøres Først i en funksjon!

Setting State:
	Du kan ved å bruke setState endre på innholdet i basis arrayet du har satt opp.
		- Du kan gjøre dette ved å sette opp en knapp
		- Når knappen er trykket ønsker du å legge et hus til staten.
		- Dette gjør du ved å legge til en funksjon inni komponenten
			- const addHouse = () => {setHouses([... houses])};
				- setHouse ar funksjonen som tillater endring av arrayet
				- spread syntaxen drar ut alle elementene fra det eksisterende arrayet og putter dem inn i det nye vi lager.
				- Da kan du også legge till et nytt element, i dette tilfellet et nytt hus.
			- ikke endre på Houses, den er ment til å være read-only.
			- React vill kun endre UI om state er endret via Set funksjonen. 
		- Du vil legge en onClick på knappen vi laget hvor du kan sette inn addHouse funksjonen. 
	- Du kan bruke State hooken flere ganger i en komponent, du kan dermed gjøre endringer til flere arrayer i en komponent. som om du har en lsite med hus og ønsker en liste som teller hvor mange hus du har i arrayet. 
	![[Pasted image 20241010112807.png]]

State main takeways:
	- State er intern data som håndteres av komponenten
	- introduseres med state hook
	- parameter er start verdien
	- returnerer et array med den satte veriden og en funksjon til å endre denne veriden. (i Set funksjonen)
	- KUNN endre state ved å bruke set funksjonen.


Props and state interactions
	En prop verdi kan endres!
	hva som er en prop verdi for en funksjon er ofte en state for en annen.

