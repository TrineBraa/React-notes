[[Anatomy of an application]]

Vanlig CSS kan legges til komponenter, det er noen forskjellige metoder å gjøre dette på.
	I Next.js: (Det skal være en understrek her men Obsidian vil vist ikke det)app.js
	last en CSS fil i HTML root dokumentet
	Legg til en CSS fil på komponent level
	Bruk styling attributt på en komponent. 
Programmer:
	- Bootstrap
	- TailWind

	typisk plass å laste: index.html
	next.js er det ikke direkte tilgjengelig
			under pages lag en understrek document.js fil
			Branch: Styling

![[Pasted image 20241010093919.png]]typisk innhold inne i den filen. 

Leggetil CSS klasser til komponenter.

![[Pasted image 20241010094212.png]]
Det er delt inni 12 rader og i collums. på denne måten kan du bestemme hvor stor plass componenter skal ta. En foreldre div kan foreksempel ta en row, mens barne komponentene inni den kan ta opp så mange colonner som du ønsker opp til 12. 
OBS ikke overlapp komponentene dine!

eks:

![[Pasted image 20241010094438.png]]
![[Pasted image 20241010094504.png]]
På denne måten vil den første div'en ta 5 colonner av de 12 tilgjengelige

![[Pasted image 20241010094515.png]]
Mens den neste Div tar de gjenværende 7. Slik kan du plassere komponentene slik at du bygger siden slik du ønsker.

![[Pasted image 20241010094629.png]]
Dersom du vil ha litt plass før neste komponent kommer under kan du sette en Margin-Bottom med utvalgt avstand ønsket. 
eller mt - for Margin-Top

Css moduler og uttrykk

CSS moduler
- Importer CSS filer i en komponent
- CSS ar kunn tilgjengelig i komponenten
- Ikke et React trekk
- Kan hjelpe med organisasjon av klasser
- ungå scoping problemer
- bundles (samlet)
- klasse navn automatisk gitt nytt navn.

Banner.module.css kan settes opp som et eget dokument hvor du setter styling inni for å holde selve koden ryddigere, du vil da injekte det til koden på denne måten:
![[Pasted image 20241010095316.png]]
du kan også dekonstruere modul dokumentet ved å sette barteklammer å spesifisere hvilket element du ønsker å importere som dette:
	import {Logo} from "./banner.modules.css";
	Du vil da kunne kalle på den direkte og skrive {Logo} i koden din. 

Style attribute
	- Kan brukes med komponenter
	- tar et objekt som inneholder CSS
	- inline eller forholdts erklert objekt
	- Det er foretrukket å ikke bruke Style attributer
	- bruk heller CSS filer:
			- Separasjon
			- Prestasjon

![[Pasted image 20241010095704.png]]
Inline objekt, må bruke dobbel barteklammer for dette.

![[Pasted image 20241010095758.png]]
Du kan også lage et objekt med stylingen i komponenten og sette navnet på objektet i barteklammene bak style. Disse elementene vil ikke kunne brukes utenfor denne komponenten. 

