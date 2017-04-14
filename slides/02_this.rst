this
====

`this` odwołuje się w JS do kontekstu, ale:
 - kontekst może być zmieniony (bind, call, apply)
 - kontekst zależy od miejsca osadzenia
 - zmienia się w strictmode

----

this c/d
========

.. code-block:: javascript

  function logThis () {
    console.log(this);
  }

  function logThis2 () {
    'use strict';

    console.log(this);
  }

  var a = {
    logThis: logThis
  };

  logThis(); // window
  logThis2(); // undefined
  a.logThis(); // a
