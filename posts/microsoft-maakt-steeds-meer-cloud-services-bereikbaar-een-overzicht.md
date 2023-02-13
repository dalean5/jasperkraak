---
title: 'Microsoft maakt steeds meer Cloud Services bereikbaar, een overzicht.'
date: '2011-03-27T10:49:41-04:00'
author: jasper@kraak.com
tags:
    - Uncategorized
---

Al ruim 2 jaar staan veel artikelen in het teken van de Cloud. Maar als puntje bij paaltje komt dan blijken de aantallen organisaties die ook werkelijk gebruik maken van het Cloud concept nog niet overweldigend. Sommigen beweren dat een eigen Datacenter ook een Cloud is, een private Cloud.  
Cloud gaat niet (alleen) over een fysieke locatie van resources, belangrijker is de mate van elasticiteit en daarmee de mate van geautomatiseerd workloads kunnen laten starten en stoppen. Het grote voordeel daarvan is dat je in principe alleen kosten hebt als er workloads draaien; pay per use.

Daar kunnen we over het algemeen in onze eigen datacenters voorlopig nog niet aan tippen. Ook als de hardware stil staat kost het geld. Vaste kosten plus variabele kosten dus.

De Cloud portfolio van Microsoft omvat inmiddels een aantal producten die het ook voor IT afdeling die niet over state-of-the-art technische vaardigheden beschikt mogelijk maken om gebruik te maken van elastische Cloud workloads. Alleen variabele kosten voor de workloads die daadwerkelijk gebruikt worden.

**Business Productivity Online Suite**  
Een viertal Microsoft Services waarvoor per gebruiker per maand betaald wordt: Exchange, SharePoint, OCS en LiveMeeting (de services zijn ook afzonderlijk verkrijgbaar). BPOS bestaat inmiddels ruim 2 jaar en schoorvoetend raken organisaties aan het concept gewend. De mailbox in de Cloud, Office documenten in de Cloud, is dat wel te vertrouwen? Betaling per gebruiker.  
**Office 365**  
De groots aangekondigde opvolger van BPOS omvat de meest recente versies van de drie grote Collaboration Service van Microsoft: Exchange 2010, SharePoint 2010 en Lync 2010. Veel van wat BPOS nog niet te bieden had, zit wel in Office365: Single Identity, Rich Coexistence, Public IM en Presence en uitgebreidere beheer mogelijkheden. Beschikbaar medio(?) 2011. Betaling per gebruiker (meerdere opties beschikbaar).

**Windows Intune**  
Windows Intune (beschikbaar per 23 maart 2011) is de eerste voorbode van wat komen gaat: de System Center producten in de Cloud. Met Windows Intune worden Windows Clients beheerd voor wat betreft security, patching, software inventaris en policies. Beheer op afstand, ook als de Clients geen lid zijn van een domain, aanzienlijk eenvoudiger in gebruik dan de System Center producten (SCCM, SCOM). Betaling per client.

**Microsoft Dynamics CRM Online**  
Het klantenbeheer systeem online, overal vandaan benaderbaar met alle functionaliteiten die ook met het pakket in huis beschikbaar zijn. Betaling per gebruiker.

**Windows Azure**  
Het Azure platform gaat nog een stap verder waar het elasticiteit betreft: betaling per instance, opslag en bandbreedte. Voor veel IT organisaties gaat dit een stap te ver: die willen een Operating System waarop ze hun applicaties beheren, Azure zegt eerder: “OS? Who needs an OS!?” Het hele Azure concept werkt volgens het principe van Scale-Out, als er meer performance gevraagd wordt dan worden er niet meer resources aan de instances toegekend (scale-up) maar er worden meer instances aan het proces toegekend.

**AppFabric**: Het is voor .NET ontwikkelaars echt niet zo heel moeilijk om applicaties geschikt te maken om deze met AppFabric op Azure te laten draaien. De missende schakel ligt op het gebied van Infrastructuur kennis.  
**Compute**: omvat een drietal rollen plus bijbehorende storage, queus en connectivity.  
De *Web Role* is geschikt om .NET We applicaties op te laten draaien volgens IIS7 principes  
De *Worker Role* draait processen die o.a. vanuit de Web Role geinitialiseerd worden.  
De *VM Role* (beta) maakt het mogelijk om Virtuele Machines vanuit een eigen Hyper-V omgeving volgens het Scale-out principe naar Azure te porteren.

**Azure SQL**: Alle rollen van een SQL Server Instance in de Cloud.  
*SQL Azure Database* SQL Server zoals we die kennen, alleen als backend (database only) in te zetten.  
*SQL Azure Data Sync* Het bouwen van meerder instances van eenzelfde Database, bevindt zich nog in de CTP fase.  
*SQL Azure Reporting* Reporting Services voor het genereren van rapporten uit Databases in huis en/of online, bevindt zich nog in CTP fase.
