``this``
========

----

Słowo kluczowe ``this``
======================

 - ``this`` odwołuje się do kontekstu (najbliższy obiekt)
 - kontekst może być zmieniony (``bind``, ``call``, ``apply``)
 - kontekst zależy od miejsca wywołania
 - zmienia się w strictmode - nie oznacza scope'a globalnego

----

this: miejsce wywołania
=======================

.. code-block:: javascript

  function logThis () { console.info(this); }

  function logThis2 () {
    'use strict';

    console.info(this);
  }

  var a = { logThis: logThis };
  var b = a.logThis;

  logThis();
  logThis2(); 
  a.logThis();
  b();
  logThis.call({});

----

this: najczęstsza wpadka
=========================

.. code-block:: javascript

  var a = {
    logThis: function () {
      console.info(this);

      setTimeout(function () { console.info(this); }, 0);

      return this;
    }
  };

  a.logThis();
