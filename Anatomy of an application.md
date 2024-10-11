[[The Power of React]]

En komponent

const Banner = () => <h1>This is a banner  /h1 (Har forlat denne åpen da jeg ikke ønsker en h1 her!)

Componenter og JSX
	- Componenter er JavaScript funksjoner som returnerer jsx
	- JSX ser ut som HTML men er ikke det
	- En alternativ måte å skrive JavaScript
	- JSX: JavaScript eXtension
	- Oversatt til JavaScript av et verktøy
			- Babel er ett slikt verktøy
				- Babel · https://babeljs.io

En annen komponent knyttet til banner komponenten over

const Greeting = () => (
<div>
<Banner/>
<h2 classname="highlight">Greetings!</h2>
</div>
);

Innebyggede komponenter:
	- Koresponderer til DOM elementer
	- forskjellige output mål bruker forskjellige innebyggede komponenter
	- de er camelCased
	- custom komponenter er PascalCased

Komponent typer:
- React team ambefaler funksjoner
- Ny fremtidig React funksjoner er kunn tilgjengelig i funksjoner
- funksjoner er mindre ordrike og lettere å håndtere.

Komposisjon:
![[Pasted image 20241009135559.png]]

Verktøy i React
- start punkt
- Transformerer JSX til JavaScript
- Prosess JavaScriptFiler
- Kjøre en dev server
- automatisk oppdaterer browser når kilde filer endres
- lage en produkt build

muligheter for verktøy
- Du kan gjøre det selv, men er mye arbeid
- bruke et klart utviklings miljø
	- Create React app (CRA)
	- Next.js
		- legger til funksjoner til start prosjektet
		- valgfri server side funksjoner
		-  React !== Next.js

Modules
- Ikke react spesific, de er JacaScript
- Export nøkkelordet gjør at andre moduller kan importere og ta denne modullen i bruk.
- Klasser, funksjoner eller onjekter, så lenge det kan holdes i en variabel. 
- Du kan eksportere flere ting, bare skill dem med komma. 
![[Pasted image 20241009143443.png]]

Export av en default ved å bruke nøkkelordet export default du trenger da ikke barte klammene i syntaxen og du kan kalle den hva du vil.

![[Pasted image 20241009143546.png]]

![[Pasted image 20241009143631.png]]

grunn til å bruke moduller
	- Kode struktur
	- gjennbruk
	- innkapsling
	- trengs til bunting (Bundling?)

ESLint
	- Oppdager problemer
	- Kode styling
	- typisk brukt
	- Next.js: Innebygget i React sine regler
- last ned ESLint plugin i VS code. 

