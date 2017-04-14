Scope
=====

Scope w JS jest funkcyjny a nie blokowy!

.. code-block:: javascript

  for (var i=0; i < 10; i++) {
    // ...
  }
  console.log(i); // zwraca 10

.. code-block:: javascript

  function Hello () {
    console.log(a); // undefined
    var a = 0;
    console.log(a); // 0
  }

  console.log(a); // undefined lub ReferenceError
