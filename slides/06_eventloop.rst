Współbieżność i event loop
==========================

----

Współbieżność i event loop
==========================

 - ten mechanizm jest odpowiedzialny za `nieblokującą` architekturę JS
 - wszystkie wydarzenia asynchroniczne są dodawane do kolejki eventowej (timery, eventy, ajax)
 - kolejka eventowa jest procesowana ``tylko w przypadku pustego stosu``
 - każda funkcja z kolejki eventowej jest ``procesowana w pełni`` zanim następna zostanie podjęta
 - web worker, cors iframe mają własny stos i kolejkę

----

Współbieżność i event loop - obraz
==================================

.. image:: ../__assets/js_runtime.png

----

Współbieżność i event loop - przykład
=====================================

.. code-block:: javascript

  (function () {
    var now = performance.now();

    for (var i=0; i < 5; i++) {
      setTimeout(function () {
        console.info(performance.now() - now, i);
      }, i * 1000);
    }
  }());

----

Współbieżność i event loop - przykład
=====================================

.. code-block:: javascript

  (function () {
    var now = performance.now();

    setTimeout(function () {
      console.info('FIRST', performance.now() - now);
    }, 0);

    console.info('SECOND', performance.now() - now);

    while (performance.now() - now < 5000) {
      // do no harm
    }

  }());

----

Współbieżność i event loop - przykład
=====================================

.. code-block:: javascript

  (function () {
    var now = performance.now();
    var printDiff = function (time) {
      console.info(time, performance.now() - now);
    };

    setTimeout(printDiff.bind(this, 1000), 1000);
    setTimeout(printDiff.bind(this, 2000), 2000);
    setTimeout(function () {
      while ((performance.now() - now) < 5000) {
        // do no harm
      }
      printDiff(3000);
    }, 3000);
    setTimeout(printDiff.bind(this, 4000), 4000);

  }());
