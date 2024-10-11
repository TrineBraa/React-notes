[[Context and navigation]]

Controlled and uncontrolled components:
- form i JavaScript applikasjoner:
	- skrive kode som får referanse til input elementer
	- dra ut de eksisterende verdiene
	- poste til API
	- konvertere intern state til React state.
	- kontrollerte komponenter
![[Pasted image 20241011135843.png]]
Her vil ikke firstname endres ved input derfor legger vi til en onchange som gjør at firstname vil kunne endres når bruker skriver i input feltet

![[Pasted image 20241011135904.png]] 
e er det samme objektet som brukes i alle JavaScript event handlers.
objektet har et target property som er en referanse til DOM element objekt som førte til at eventet kjørte. 
fra det kan en verdi bli lest som inneholder en string some representerer inputet sitt innhold. 
dersom det er en checkbox eller radio bruker vi checked istedet for value. 

Forms
	Når inputet er brukt på et form, kan onSubmit event bli håndtert oh handleren får et event objekt om gjør at preventDefault, blir kalt. 
![[Pasted image 20241011143602.png]]
Dette er veldig standar i javaScrip funksjoner for å hindre at broweser gjør en default submit aksjon.
![[Pasted image 20241011143834.png]]
Det er veldig vanlig å gi hvert element sin egen onchange handler. 
Computed property name i JavaScript.
- e.target.name peker til navn atributten i input feltet. verdien av atributten må korespondere til propertien navn i state objektet.

![[Pasted image 20241011145741.png]]
![[Pasted image 20241011145819.png]]
Ukontrollerte komponenter:
	- Kontrollert er deffinitivt veien å gå
	- kontrollerte komponenter kan likevel ha veldig mye jobb involvert, du må skrive event handlers osv. 
	- når en konverterer eksisterende kodebase. 
	- quick and dirty løsning.
	- midlertidig løsning
![[Pasted image 20241011150420.png]]

Adding Form functionality:
	- Validation
	- Error messages
	- Handling form submission
	- State handling
	- External library
			- Formik (formik.org)

