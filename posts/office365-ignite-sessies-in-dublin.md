---
title: 'Office365 Ignite Sessies in Dublin'
date: '2011-02-21T19:07:52-04:00'
author: jasper@kraak.com
tags:
    - Cloud
---

Office365 Iginite Conference, 7 – 10 februari 20110, Dublin

In de afgelopen twee jaar heb ik ongeveer 25 keer de BPOS ééndagstraining voor Nederlands Microsoft Partners gegeven. Ik noemde BPOS wel Cloud 1.0, as is.

Vandaag ben ik in Dublin gearriveerd voor de Office365 Ignite Conference en zal ik de komende dagen verslag doen van wetenswaardigheden die ik hier te horen krijg.

Dag 1

De eerste demo’s; het lijkt in niets meer op BPOS voor zover het de verschillende webinterfaces betreft. Dat is even wennen maar het is wel een stuk beter zo.

Opmerkelijk is dat Office Pro Plus de naam gaat worden voor de subscription via Office365 en dat daarnaast de VLK versie gewoon Office 2010 blijft heten (met een jaartal dus). Deze Subscription versie gaat niet werken in Citrix/RDS omgeveingen. Maar weer wel in VDI-oplossingen. Dan is een voorwaarde wel dat gebruik gemaakt wordt van de Federation Gateway.

En dat is gelijk “the highlight of the day”; Federation Services 2.0 en de configuratie daarvan. Simpel! En daarna dus Single Sign On, naar alle Office365 producten, gewoon met de eigen AD Credentials. Zaken als password policies en synchronisatie zijn dan overbodig.

Dag 2

Een groot deel van de dag stond in het teken van Security en Compliance. Er heerst in de markt nog veel scepsis over het onderbrengen van (mail)data in een Microsoft Datacenter. “Veiligheid is een gevoel”.

Interessanter vond ik het deel over migratie en coexistence. Rich Coexistence betekent dat er on-premises 1 Exchange 2010 Server achterblijft, je kunt vanuit de Management Console de Online Mailboxen beheren, inclusief Transport Rules, Mailbox Policies en noem maar op.

Of de optie om de dagelijkse mailbox on-premises te houden maar de Archives Online onder te brengen.

Zo zijn er vele scenario’s denkbaar en zal er altijd wel eentje passend zijn voor een bepaalde klantsituatie.

Voor mensen met een BPOS en/of Exchange 2010 achtergrond is het allemaal goed te volgen hier, voor velen gaat het echter veel te snel en veel te veel info.

Dag 3

Vandaag heel veel “techniek” over Federated Identity en Federated Services. Hoe zet je nou “rich-coexistence” op. De voordelen van rich-coexistence zijn met name voor wat grotere organisaties zeer interessant
- feitelijk de complete feature set van Exchange 2010 SP1. Hetgeen met een cutover migratie (alles naar Exchange Online) niet het geval is.

Veel AD, Pwershell, Authenticatie en Certificates kwam in rap tempo voorbij. Dat werd allemaal nog meer toen Lync erbij betrokken werd; de echte Unified Communications scenario’s.

Lync2010 is Full-Blown beschikbaar als Online Service behalve dan PSTN-integratie, d.w.z. als afnemer moet je wel zelf een (aantal) telefoonlijnen hebben. Live Meeting komt te vervallen en is geintegreerd in Lync, ook wat betreft de Client.

Zoals gezegd, de hele configuratie is niet echt makkelijk maar binnen Nebula bijvoorbeeld is het wel makkelijk reproduceerbaar, alles kan immers met Powershell gescript worden en met Opalis geregiseerd.

Dag 4

Deze dag stond stond grotendeels in het teken van SharePoint. SharePoint krijgt een enorme boost ten opzichte van de aanbieding in BPOS waar het meer Windows SharePoint Services was.

Vrijwel de gehele feature set van wat er met SharePoint 2010 On-Premises mogelijk is, kan ook met SharePoint Online.

Goeie demo’s over Customization:

1\. Vanuit de webbrowser: themes, master pages, navigation, webpparts etc.

2\. Met SharePoint Designer: workflows (eerst in Visio!), StyleSheets, Simple Solutions

3\. Visual Studio 2010: voor het echte .NET programmeerwerk.

De laatste sessies gingen over de migratie van BPOS naar Office365. Daar zitten voor de klant wel een paar haken en ogen aan. Zo wordt Office 2003 niet ondersteund, de Office Communicator 2007 R2 en de Sign In tool moeten van clients verwijderd worden. De URLs voor OWA en Mobile Devices veranderen!

Voor SharePoint en Exchange krijgen klanten een aantal Pilot Accounts tot hun beschikking om te testen of alles naar behoren functioneert. Ze krijgen een voorstel voor een transitie-weekend maar kunnen dat uitstellen (niet naar voren schuiven).

De feitelijke transitie gebeurt verder in de Datacenters van Microsoft zonder onderbrekeing van Mailflow. SharePoint Sites zijn max. 48 uur “read-only”.

De grooteste winst voor BPOS klanten is te behalen door gebruik te gaan maken van SSO door middels van Identity Federation.
