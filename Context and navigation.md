[[Conditional Rendering and Shared State]]

![[Pasted image 20241011131942.png]]

Declaring Context
	- I komponent som gir kontekt eller separate moduller:
			const context = React.createContext("Default value");
	- i komponent som skal gi kontekst:
			 <Context.Provider value ="some value">
			 Children
			 </context.Provider>
	- I barne komponenter:
			 const value = useContext(context);
	Når verdien av konteksten endrer seg, vil alle som bruker den kontekssten bli re-rendret. Dette gjelder alle barn som bruker den. 

Providing Context:
	Du kan sette opp en const som lager en kontekst  verdi og setter den når du starter applikasjonen, i dette tilfelle setter vi den som Home. 
	![[Pasted image 20241011133025.png]]
	![[Pasted image 20241011133120.png]]
	Den kan nå brukes til å gi verdien til barne komponentene. 
	Du vil ikke sette verdien som statisk når du kaller på den, det er bedre å sette den i en state hook slik at verdien kan endres. 
	![[Pasted image 20241011133252.png]]
	Du vil pakke denne funksjonen inn i en callback funksjon siden alle barne komponenter vil få tilgang til den. Dette for å unngå unødvendige re-renders 
	![[Pasted image 20241011133447.png]]
	![[Pasted image 20241011133545.png]]
	Dette sikrer at staten i seg selv tar seg av re-renders, det er derfor best å inkludere funksjonen navigate til staten.
	![[Pasted image 20241011133811.png]]
	Du vil på denne måten kunne sette opp en slik metode som vil reagere når nye verdier satt inn.

Consuming Context:
 - Nå i barne komponentene vil du kunne kalle på 
	 - useContext med kontekst objektet som et parameter. 
	 ![[Pasted image 20241011134317.png]]
	![[Pasted image 20241011134435.png]]
	Legge til Param som enda et parameter i callback funksjonen
	![[Pasted image 20241011134520.png]]

Navigation Libraries:
	- Hva om flere funksjoner er trengte:
			- Bygg det selv
			- Next.js router
			- React router
	- betraktelser:
		- ekstra bibliotek dependencies
		- Alt av det er basert på en global state

Where and When to use context:
	- Når den samme staten skal sendes til mange komponenter
	- Tenk på re-renders Manke komponenter vil re-rendre når noe endres. 
	- det gjør komponent gjenbruk vannskeligere
	- State gitt via kontekts er gjemte states