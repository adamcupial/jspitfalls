Miękkie typowanie
=================

----

Miękkie typowanie
==================

 - js jest ``miękko typowany``, będzie próbował dopasować typ automatycznie
 - posiada stałą ``NaN`` => wynik operacji niemożliwej na liczbach
 - polecenie ``switch`` jest twardo typowane
 - dwa typy operatorów: ``==`` i ``===``


----

Miękkie typowanie: casting
==========================

.. code-block:: javascript

  console.info(false == '0');
  console.info(null == undefined);
  console.info(" \t\r\n" == 0);
  console.info('' == 0);
  console.info(NaN != NaN);
  console.info(NaN !== NaN);
  console.info(!!{});
  console.info(!![]);

----

Miękkie typowanie: switch
=========================

.. code-block:: javascript
  
  function sw (x) {
    switch (x) {
      case '5':
        console.info('Five');
        break;
      default:
        console.info('Other');
    }
  }

  sw(5);
