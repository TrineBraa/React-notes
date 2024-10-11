[[React 18 Fundamentals]]
History
- 2011 Created by facebook
- 2012 Used on Instagram
- 2013 Open sourced
- 2014 Embraced by many large companies
- 2015 React Native Realesed (for creating apps and mobile apps)
- 2016 React 15 released (0.14 before)
- 2022 React 19 Released
- today Full-time dev staff Used by many in fortune 500


Hvorfor React
- Fleksibilitet
- Utvilker opplevelse
- Bedrifts innvestering
- Fellesskaps støtte
- prestasjon
- test mulighet. 

Fleksibilitet
- React er et bibliotek og ikke et framework.
- hva brukes React til
		- Web app
		- Statiske sider
		- Mobil
		- Desktop
		- Server-render
		- Virtural reality
	- React Renderers:
		- react-dom (rendrer komponenter til HTML)
		- react-native (rendrer komponenter til native-vennlig kode)
		- react-vr (rendrer koden inn i et Virtural Reality enviroment)
- Frameworks
		- Next.js
		- Remix
		- Gatsby

Utvilker opplevelse
- En minimal API innebygget, veldig lightweight som gjør at du skjeldent vil trekke å sjekke docs for det. 
	- React API
- Props (objekt variabel)
- JSX compiler til JS
	- JS (Trykk på </> for å vise koden) 
			- <h1 color="red">Heading</h1>
	- React.createElement (Denne kaller for å generere HTML)
	- React.createElement("h1",{color: "red"}, "heading here")
- CodeSandbox, du kan eksperimentere med React uten å måtte kjøre VS. 

Tradisjonell UI testing:
- Styr å sette opp
- krever en browser
- treigt
- skjøre integrasjons tester
- tar tid å skrive og oppdatere
React:
- Lite til ingen config kreves
- kjører in-memory via Node
- Raskt
- pålitelig, deterministisk enhets tester
- Skrives raskt, oppdateres lett


Du har mange test frameworks som du kan kjøre med react
- Mocha
- Jasmine
- Tape
- QUnit
- AVA
- Jest (den mest populære for tiden, laget av Facebook)


Tradeoffs I react

Framework vs Library
	Frameworks:
		- Angular 
		- Ember
	Library:
		- React

Fordeler med Frameworks:
	- klare muliheter
	- mindre decision fatigue
	- mindre setup overhead
	- mer cross-team konsistens
Fordel med Library:
	- Lett vektig
	- kan strøs inn i allerede eksisterende apper
	- du kan velge hva du trenger
	- lar deg velge best teknologi
	- populærer boilerplates eksisterer (Create React App gjør React til et valgfritt framework)

Andre React frameworks:
Mange av disse inkluderer Routing, HTTP, forms, testing, builds, mm.
- Next.js
- Vite
- Gatsby
- Remix
- RedwoodJS
- Hydrogen

javascriptstuff.com/react-starter-projects

![[Pasted image 20241009120236.png]]![[Pasted image 20241009120448.png]]
![[Pasted image 20241009120533.png]]![[Pasted image 20241009122926.png]]
Du kan bygge React på Funksjoner eller Class
Funksjon er mer vanlig nå. 

![[Pasted image 20241009123358.png]]![[Pasted image 20241009123651.png]]