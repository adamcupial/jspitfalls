Dziedziczenie
=============

----

Dziedziczenie
=============

 - oparte na ``prototypach``, fundamentalnie innym modelu dziedziczenia niż klasyczne
 - w dziedziczeniu prototypowym dziedziczy się po ``instancjach`` (obiektach) nie po klasie
 - dwa obiekty mające ten sam prototyp mają referencję do TEGO SAMEGO OBIEKTU
 - ``class`` z ES6 używa tego samego mechanizmu (`syntactic sugar`)


----

Dziedziczenie - przykład
========================

.. code-block:: javascript

  var proto = {
    me: 'protoDefault',
    changeProto: function () { this.__proto__.me = 'protoChanged'; },
    changeMe: function () { this.me = 'MeChanged'; }
  };

  function A () { return this; }
  function B () { return this; }

  A.prototype = proto;
  B.prototype = proto;

  var a = new A();
  var b = new B();

  console.info('bez-zmian', a.me, b.me);
  b.changeMe();
  console.info('zmiana-instancji A', a.me, a.__proto__.me);
  console.info('zmiana-instancji B', b.me, b.__proto__.me);
  b.changeProto();
  console.info('zmiana-klasy A', a.me, a.__proto__.me);
  console.info('zmiana-klasy B', b.me, b.__proto__.me);
  delete b.me;
  console.info('po-usunięciu B', b.me, b.__proto__.me);
