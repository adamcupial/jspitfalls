Scope
=====

----

Scope: intro
=============

  - scope jest ``funkcyjny`` a nie blokowy
  - zmienne zadeklarowane w funkcji są ``dostępne w całej funkcji``
  - funkcja ma dostęp do zmiennych ze scope'u w którym została zadeklarowana (*closure*)
  - wyjątek: ``let`` w ES6

----

Scope: function scope && variable hoisting
=========================================

.. code-block:: javascript

  for (var i=0; i < 10; i++) {
    // do no harm
  }

  console.info(i); 

.. code-block:: javascript

  function Hello () {
    console.info(a);
    var a = 0;
    console.info(a);
  }

  console.info(a);

----

Scope: closure
===============

.. code-block:: javascript

  (function () {
    var a = 'Hello World';

    (function () { console.info(a); }());
    setTimeout(function () { console.info(a); }, 0);
    setTimeout(function () { a = 'Bye World'; }, 0);
    setTimeout(function () { console.info(a); }, 1000);

    return a;

  }());

----

Scope: najczęstsza wpadka
=========================

.. code-block:: javascript

  for (var i = 0; i < 5; i++) {
    setTimeout(function () { console.info(i); }, 0);
  }

.. code-block:: javascript

  for (var i = 0; i < 5; i++) {
    setTimeout((
      function (j) { console.info(j); }
    ).bind(null, i), 0);
  }
