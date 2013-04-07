---
title: Vagrant
isChild: true
---

## Vagrant

Corrent la vostre aplicaci� en diferents entorns en desenvolupament i producci� pot conduir a errors estranys que fan esclatar per amunt del vostre nivell. Tamb� �s dif�cil de mantenir entorns de desenvolupament diferents al dia amb la mateixa versi� per a totes les biblioteques que utilitzen quan es treballa amb un equip de desenvolupadors.

Si estas desenvolupant en Windows i la implementaci� es fa en Linux (o qualsevol altre sistema que no sigui Windows) o estan desenvolupant en un equip, ha de considerar l'�s d'una m�quina virtual. Aix� sona complicat, per� amb [Vagrant][vagrant] vost� pot configurar una m�quina virtual simple amb nom�s uns pocs passos. Aquesta caixa base es pot configurar manualment, o b� pot utilitzar programari com [Puppet][puppet] o [Chef][chef] que far� aquesta tasque per tu. La caixa base �s una gran manera d'assegurar-se que les caixes m�ltiples es configuren en forma id�ntica i elimina la necessitat per tu, la de �crear� les llistes d'ordres. Tamb� pot "destruir" la seva caixa base i tornar-la a crear amb molt pocs passos manuals, es f�cil crear un "fresc" de la instal�laci�.

Vagrant crea carpetes per compartir el vostre codi entre el vostre amfitri� i la vostra m�quina virtual, significa pot crear i editar els vostres arxius en la vostra m�quina amfitriona i llavors executar-los dins la vostra m�quina virtual.

[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
