[[Hooks, Props and State]]

Rendering er ikke det samme som å oppdatere browseren
Oppdatering av browseren er gjort av react via rekonsiliasjon
	Dersom en komponent har en state som endrer seg vill react rendre den komponenten på nytt.
		en ny rendering betyr at komponentens funksjon er gjørt på nytt
	Viktig å huske:
		- Når state av en komponent endres rendres den komponenten på nytt!
		- Det betyr ikke at hele komponenten rendres på nytt, react bruker rekonsilasjon til å se hvilke endringer som er gjort og rendrer kunn endringene som er gjort. !
		![[Pasted image 20241010130323.png]]
		![[Pasted image 20241010131903.png]]
	State change og  Rendering på nytt:
		- overlappende effekt
		- fører ikke til dårligere preformasjon i en bra designet applikasjon
		- husk at rekonsiliasjon i React Kunn laster nye endringer i UI
		- Noe å alltid ha i tankene når en designer en applikasjon.

Pure functions and side effects:
	en pure function er en funksjon som alltid sender tilbake det samme resultatet.
			- lett å teste
			- forutsigbar
			- pålitelig
			- kan buffres
			- funksjon komponenter må være pure functions!
				- Det betyr at gitt de samme prop verdiene og den samme state skal funksjonen alltid returnere den samme JSX.

	du kan bruke Memo til å huske tidlgere prop verdier, på denne måten kan du hindre at alt rendres på nytt. Så når du legger til noe nytt vil memo huske de verdiene du hadde fra før og legge til dem. 
	Dette brukes ved å pakke komponenten med react.memo
		When to use React.memo
			- om det er raskere enn react sin rendering syklus
			- du kan måle om det er raskere
			- det er kun raskere om det er en Pure functional component
			- Rendres ofte
			- beholder de samme prop verdiene
			- JSX ikke er trivial
		https://reactjs.org/docs/react-api.html#reactmemo
				- utdatert
			- https://react.dev/reference/react/memo


Side effects and the effect hook
	uforusette operasjoner i komponenter burde bli satt til side. 
	Rene funksjoner kan høres veldig rett frem ut men i praksis må vi gjøre ting i komponenter som ikke altid er like praktisk og stødig
	disse operasjonene kalles (Side) effects eller bare effect.
		- Dersom vi trekker informasjon utenfra react vil være en effekt.
	- Effekt eksempler:
		- API interkasjoner
		- Browser API (Dokumenter, window)
		- Bruk av Timeing functions (setTimeout)
	Effekt hook:
		- useEffect(()=> {Gjennomfør effekten})
		- Tar en funksjon som et parameter.
			- den vil kjøres automatisk når react er ferdig med rene funksjoner og browser er oppdatert
		- du kan f.eks hente data fra en API med denne.
		![[Pasted image 20241011094626.png]]
		Dette er et kall til en API ved å bruke en useEffect. du setter en async funksjon inni useEffecten og kan på den måten sette await på API kallet, og få responsen via JSON som settes i const houses. før du så endrer arrayet med setHouses. 
	

Effect and Re-Rendering
	OBS vær forsiktig med bruk av useEffect siden den vil kjøre en re-render det kan føre til en uendelig loop dette kan løses med å sette opp et 'dependency array'
	![[Pasted image 20241011095139.png]]
	![[Pasted image 20241011095224.png]]
	Du kan håndtere det ved å bruke et dependency array slik at useEffekt kunn kjører dersom endringer er gjort. 
	Dersom du bare ønsker at effekten skal gjøre engang når den først rendres, kan du sende inn et tomt array istedet.
	Dersom du trenger flere useEffekts, ikke prøv å sett dem inn i en, du kan ha flere så sett heller opp flere useEffects. Husk på det at du ønsker hver komponentt til å kunn gjøre en ting!
	Du kan også returnere en funksjon i en useEffect, 

The memo Hook
	- memorize values in components!
	- Dersom du har en kalkulasjon som du trenger i din applikasjon kan du bruke en memo hook til å huske verdien slik at ikke oppdateres ved hver re-render.
	- eks:
	![[Pasted image 20241011100011.png]]
	Den første funksjonen () etter memo er den sok gjennomfører kalkulasjonen, og når du sender med houses som et dependency vil denne kun oppdateres ved første render og ved endringer. 
		- Så når ingenting endres vil memo returnere den tiligere verdien ved en rerender. 
		- igjen du burde måle om dette er raskere før du putter det inn!

The Ref Hook:
	Persists values that survive re-renders without causing a re-render
	- veldig likt State, men endring av Ref verdi endrer ikke en re-render.
	- Du kan sette opp en ref verdi av f.eks hvor mange ganger en re-render har skjedd, uten å trigge en ny re-render. 
