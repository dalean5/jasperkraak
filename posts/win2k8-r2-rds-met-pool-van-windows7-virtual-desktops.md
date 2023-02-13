---
title: 'Win2k8 R2 RDS met Pool van Windows7 Virtual Desktops'
date: '2009-09-22T10:57:50-04:00'
author: jasper@kraak.com
tags:
    - 'Win2k8 R2'
---

<div class="bvMsg" id="msgcns!3FD1C7C6EA1A2!166"><div>Built it, been there, done that, got the T-Shirt! (niet helemaal, ik heb een polo van Windows7)</div><div> </div><div>Twee adders onder het gras waarvan je niet zomaar 1,2,3 weet hoet dat nou moet/zit. Gelukkig staat er een goeie deployment guide hier:</div><div> </div><div><http://technet.microsoft.com/en-us/library/dd883265(WS.10).aspx></div><div> </div><div>maar daar zit wel een behoorlijke FOUT in. Het maken van de Snapshot van de VMs moet (natuurlijk) pas NA de regedit en wmic commando’s! Anders doet de boel het maar één keer, dan ben je heel blij en dan opeens niet meer 🙁 </div><div> </div><div>Voor het overige: very smooth!</div></div>
