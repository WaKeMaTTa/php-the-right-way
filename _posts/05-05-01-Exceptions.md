---
title: Excepcions
isChild: true
---

## Excepcions

Les **Excepcions** s�n un aspecte normal dels llenguatges de programaci� m�s populars, per� sovint s�n pasades per alt pels programadores de PHP. Altres llenguatges com Ruby utilitzen les **Excepcions** en gran quantitat, tant que cada vagada que succeeix un error com una petici� HTTP que ha fallat o una l�nia de consulta a una base de dades que no funciona, o potser hi havia una imatge que no existeix, Ruby (o qualsavol gama en ejecuci�) llan�a una excepci� a la pantalla deixant a coneix-re que hi va haver-hi un error.

PHP es poc exigent en aquestes instancies. Per exemple, una trucada a la funci� `file_get_contents()` usualment sol retornar un `FALSE` i una advert�ncia. Molts de les estructures base (frameworks) m�s antigues de PHP com CodeIgniter simplement retorna un valor `FALSE`, i registren un missatge en els seus registres i potser el permetin utilitzar un m�tode com `$this->upload->get_error()` per veure que funciona malament. El problema amb aquests es que un mateix te que anar a buscar el error i assegurar-se en la documentaci� de quin dels m�todes per verificar errors a de utilitzar, en comptes de fer que el error sigui m�s obi.

Un altre problema com� es quan les classes automaticament llancen un error a la pantalla i paren el flux del programa. Quan aix� passa el desenvolupador no te la oportunitat de manejar el error din�micamenet. En aquesta instancia es tenene que utilitzar les excepcions per que el desenvolupador estigui conscient de que hi ha un error i pot escollir com manejar la situaci�. Per exemple: correu electr�nic

{% highlight php %}
<?php
$correuElectronic = new Fuel\Email;
$correuElectronic->subject('El Meu Assumpte');
$correuElectronic->body('Como estas?');
$correuElectronic->to('persona@exemple.com', 'Algun persona');

try
{
    $correuElectronic->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // Hi va haver un error en la validaci�
}
catch(Fuel\Email\SendingFailedException $e)
{
    // El gestor no va poder enviar el correu
}
{% endhighlight %}

### Excepcions de la SPL

Les excepcions, per defecte, no tenen cap significat i el m�tode m�s com� de asign�rselos �s en donar-los un nom:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

Aix� li permet afegir m�ltiples blocs `catch` i manejar diferents excepcions de diferent manera. Aix� pot conduir a la creaci� d'una gran quantitat d'excepcions particulars nom�s a la seva aplicaci�, moltes de les quals poguessin eliminar en usar les excepcions que proveeix la [extensi� de la SPL][splext].

Si, per exemple, utilitza el m�tode m�gic `__call()` i aquest sol�licita un m�tode inv�lid, llavors en comptes de llan�ar una excepci� est�ndard de significat dubt�s o crear una excepci� particular, nom�s caldr� fer aix�:

{% highlight php %}
<?php
throw new BadFunctionCallException;
{% endhighlight %}


* [Llegir sobre les Excepcions][exceptions]
* [Llegir sobre les Excepcions de la SPL][splexe]
* [Com niar excepcions en PHP][nesting-exceptions-in-php]
* [Les millors pr�ctiques per a les excepcions en PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/es/language.exceptions.php
[splexe]: http://php.net/manual/es/spl.exceptions.php
[splext]: /#biblioteca_est�ndar_de_php
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
