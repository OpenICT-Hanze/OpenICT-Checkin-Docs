Bevindingen
========================

-----------
Bevinding 1:
-----------
- Probleem: (Vermoedelijk) Spamfilter van de Hanze filtert automatisch berichten van een onbekende bron uit, waardoor mails niet binnenkomen, zelfs niet in de ongewenste mail. 

- Oplossing/Kanttekening: Het versturen van mails naar een omgeving buiten Outlook om, zoals gmail is wel mogelijk. De huidige instellingen van de mailserver is de vinden in het .env bestandje in het project. Vermoedelijk moet er contact worden opgenomen met de Hanze over het whitelisten van onze applicatie, zodat er ook mailtjes verstuurd kunnen worden naar schoolmail adressen

-----------
Bevinding 2:
-----------
- Probleem: Er worden te veel API calls gemaakt op het docentendashboard, waardoor als jij de pagina laadt hij soms tot vaak een foutmelding geeft ‘Too many requests’. Dit is voornamelijk op de lokale omgeving.

- Oplossing: In de toekomst zou kunnen gekeken worden naar de structuur van API calls, zodat deze beperkt worden. Eventueel kan ook gekeken worden naar de api rate limitter / throttle.

-----------
Bevinding 3:
-----------
- Probleem: De applicatie is nog niet geheel responsive momenteel, als voorbeeld het docentendashboard wordt incorrect ingeladen op de mobiel waardoor het een onprofessionele look geeft.

- Oplossing: De formatting en css moet aangepast worden zodat dit op alle/meeste apparaten netjes en correct weergeven wordt.
