Inksze
======

----

Inksze: parseInt
================

.. code-block:: javascript

  console.info(parseInt('0800'));
  console.info(parseInt('0x800'));
  console.info(parseInt('0xFF'));
  console.info(parseInt(100000000000000000000000000, 10));

----

Inksze: globals
===============

.. code-block:: javascript

  for (i=0; i<10; i++) {
    // do no harm
  }

  console.info(window.i);

----

Inksze: for...in
================

.. code-block:: javascript

  var arr = ['a','b','c'], indexes = [];
  Array.prototype.each = function() {};
   
  for (var index in arr) {
      indexes.push(index);
  }
   
  console.info(indexes)
