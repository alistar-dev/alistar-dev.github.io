Mail SPF record
Om correct mails te kunnen versturen vanuit de natchcloud omgeving met uw domein als afzender (bvb @natcheurope.com) is een DNS aanpassing nodig van het SPF record (of creatie ervan).

 

Hoe SPF record instellen?
Voeg deze include toe aan uw SPF record om instellingen over te nemen die door Natch worden beheerd. Zo hoeft u niets aan te passen als onze IP nummers wijzigen.

include:spf.natchcloud.com

 

Extra info
Een tool om het SPF record te controleren, met voorbeeld van gebruik voor natcheurope.com

https://mxtoolbox.com/SuperTool.aspx?action=spf%3anatcheurope.com&run=toolpage

Meer informatie over SPF: https://postmarkapp.com/guides/spf



Oude methode
Indien deze method gebruikt wordt, mag onderstaande data in uw SPF record vervangen worden door nieuwe methode.

Het IP nummer of IP range van natchcloud wordt rechtstreeks opnemen in uw SPF record. Bij wijziging van onze cloud omgegeving (bvb nieuwe smtp server) moet uw SPF record aangepast worden.

Indien deze oude entries in uw SPF record staan, moeten ze vervangen worden door de include.

ip4:178.208.41.192/26

ip4:178.208.41.202

a:smtp.natchcloud.com

 
