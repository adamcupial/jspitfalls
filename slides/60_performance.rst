Performance
===========

----

Performance: for
================

.. code-block:: javascript

  var arr = [1, 2, 3, 4];

  for (var i = 0; i < arr.length; i++) {
    // do no harm
  }

vs

.. code-block:: javascript

  var arr = [1, 2, 3, 4];

  for (var i = 0, l = arr.length; i < l; i++) {
    // do no harm
  }

----

Performance: arrays
===================

.. code-block:: javascript

  var a = [1, 2, 3, 4];

vs

.. code-block:: javascript

  var a = [];
  for (var i = 1; i <= 4; i++) {
    a.push(i);
  }

vs

.. code-block:: javascript

  var a = new Array(4);
  for (var i = 1; i <= 4; i++) {
    a.push(i);
  }

----

Performance: arrays
===================

.. code-block:: javascript

  var a = [1, 2, 3, 4];

vs

.. code-block:: javascript

  var a = [1, 2, null, 4];

----

Performance: classes
====================

.. code-block:: javascript

  function Point(x, y) {
    this.x = x;
    this.y = y;
  }

  var p1 = new Point(11, 22);
  var p2 = new Point(33, 44);

vs

.. code-block:: javascript

  function Point() {}

  var p1 = new Point();
  p1.x = 11;
  p1.y = 22;

  var p2 = new Point();
  p2.x = 33;
  p2.y = 44;

----

Performance: inksze
===================

 - integery zajmują mniej pamięci niż double
 - globalne zmienne nie podlegają Garbage Collection ...
 - używaj closure TYLKO gdy jest wymagane
 - nie używaj with oraz eval, nigdy
 - switch jest wydajniejsze niż wielokrotne if ... else if
 - try ... catch jest niemożliwe do optymalizacji
 - pamiętaj że typy proste są kopiowane, obiekty są przekazywane przez referencję
 - zawsze odpinaj event handlery których nie potrzebujesz
