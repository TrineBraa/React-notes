[[Component rendering and side effects]]

Conditional rendering:
	- du kan rendre komponenter under spesifikke kondisjoner.
	- Dette er gjerne det du kan bruke med en if statement, du kan få en komponent til å rendre enting dersom en verdi er sann, eller noe annet dersom verdien ikke er sann f.eks. 
	- du kan skrive det på forskjellige måter
		- en if statement
		- en inline med ? (Dersom sann) og : (ellers gjør dette)
		![[Pasted image 20241011103104.png]]

Conditionally rendering components
- Akkurat slik at du kan rendre mindre komponenter som et bilde dersom det er kondisjoner, kan du også gjøre det med større komponenter som foreldre komponenter. 
- Dette vil gi inntrykk av f.eks sider, men egentlig er det rendering av forskjellige komponenter
- Dersom du ikke liker inline kan du også sette det opp som en variabel og rendre variabelen istedet. 
![[Pasted image 20241011104146.png]]

Passing in Functions as props and determining state location
- I dette tilfellet har du Banner og House som du kan vise frem, koden er satt opp med en useState for å velge et hus, men du må på en måte sende dette til huslisten slik at applikasjonen kan vite at du har klikket på en husrad og dermed har valgt et hus. 
	- Dette gjør du ved å sende setSelectedhouse useStaten som et parameter til forelderen av hus, hus liste
eks: 
![[Pasted image 20241011104657.png]]
på denne måten setter du opp en funskjon som vil først sjekke om selectedHouse ar sann, at noe er satt i denne variabelen.
	-Dersom det er satt noe der, vil du sende det objektet inn som et hus.
	- Dersom den ikke er satt vil du rendre hus listen. 
	- du setter paranteser rundt funksjonene slik at applikasjonen vet samlet hva den skal gjøre. 
- Når du har gjort det på denne måten må du også ta imot denne prop i houseList som er forelder komponenten til hus.
		- Den vil ikke brukes i houseList i seg selv, men vi kan nå sende den videre til houseRow som dette:
		![[Pasted image 20241011105056.png]]
		Du kan nå ta imot den i houseRow, og du kan sette en onclick i houseRow og kalle funksjonen fra root app. På denne måten vil du kunne laste forskjellige komponenter. 
		![[Pasted image 20241011105429.png]]
![[Pasted image 20241011105610.png]]
- KUNN sett state i root komponenten som ikke passer noe annen plass! 
- deling av state på denne måten kan bli veldi komplisert, så bare del det mellom komponenter når det trengs. 
- Plasser State så langt ned ei hierarkiet som mulig for å unngå unødvendig komplikasjon av koden og tunge prosesser ved re-rendering.

Mounting and Unmounting
	Når en komponent vises i browseren er den mounted, statene og effektene kjører.
	Dersom komponenter senere fjernes fra browseren er de Unmounted.
			- Det som er viktig å huske med unmounting er at alle state av komponenter er ødelagt.
			- Dersom en bruker ønsker å komme tilbake til en tidligere 'side' av komponenter vil de startes opp igjen som om de ikke har vært kjørt tidligere. 

Function Wrappers and the CallbackHook
	Du kan sette en wrapper funksjon som kan ta imot et objekt og som gjør kallet til i dette tilfellet SelectedHouse.
			-Det vil gjøre at i dette tilfellet har app root fortsatt full kontroll av sin egen state. 
			- SetSelectedHouse vil nå være innkapslet i sin egen komponent. 
			![[Pasted image 20241011111703.png]]
		gjenskape funksjoner:
			- Funksjon objekter blir gjenskapt
			- nye referanser
			- vær obs på memoriserte komponenter!
			- eller om funksjonen er i en dependency array
			- pakk med useCallback om nødvendig
			- memoriserer den inneholdte funksjonen
			- kommer med overhead
				- bruk det kunn om det er nødvendig
			![[Pasted image 20241011112102.png]]
			virker likt som useMemo
			I dette tilfellet vil funksjonen kunn kalles når komponenten er mounted.
			 setState funksjoner trenger aldri å pakkes inn i callback fordi react will passe på at de ikke er laget på nytt ved hver re-render.

Delegating State to a Custom Hook
	Du kan legge hooks inn i egne dokumeter og sette opp en hooks folder i prosjektet ditt.
	På denne måten kan du flytte hooks og rydde opp i deler av koden din. 
	Hooks skal alltid ha 'use' prefixet i navnet deres
	hooks er funksjoner, men de returnerer ikke JSX men de kan bruke andre hooks. 
	I tilfellet med hus når vi drar useHouses inn i sitt eget dokument kan vi returnere arrayet av Houses
	Du kan sette return staten inn i en variabel

	Cutsom hooks:
		- funksjon
		- når en returnert state endres, vil komponenten som bruker den re-rendres
		- Separasjon av bekymmringer
		- gjenbruk
		- isolert state i hver bruker komponent. 

Adding additional state to a custom hook
	- Du kan legge til flere elementer i en custom hook.
		- Eks at lasting tar tid, det kan være mer bruker vennlig og vise brukeren at noe laster eller om det feilet i lastingen.
		- Du kan sette opp en loading som en state i en hook, på denne måten kan du sette den til å vise at siden laster eller om den feiler med en try catch metode. 
	![[Pasted image 20241011115904.png]]

Increasing the Reusability of a Custom hook 
	Du kan sette opp en egen hook for get requests, hvor props er en URL som gjør at hooken kan brukes av forskjellige get requester!
	![[Pasted image 20241011120307.png]]
	Da kan du dermed sette inn loading staten inn i denne generelle hooken og unngå at du må gjenta den koden biten. 
	Du må dermed også refaktroere koden hvor du først hadde satt opp API kallet. 
	![[Pasted image 20241011120512.png]]
	Denne refaktoreringen vil føre til en re-rendering loop som kan brytes ced å sette en useCallback funksjon i Gat Async funksjonen i useGetRequest hooken. og dette et dependency array knyttet til URL. Det må være der fordi det er en eksternal dependency. 
	Callback will gjøre at Get funksjonen ikke er laget på nytt ved re-renders, den endres kunn om URL endres. 


Conditional Rendering:
	- Alle JavaScript kondisjonerte statementer eller uttrykk kan ble brukt i JSX
	- if statementer
	- ? og :
	- &&
	- samt: tidlig retur fra en komponent
State sharing:
	- Bruk en prop
	- funksjon som en prop
	- fra en custom hook