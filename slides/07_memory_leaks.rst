Memory leaks
============

----

Memory leaks
============

  - powstają kiedy zalokowana pamięć nie może być automatycznie zwolniona przez ``garbage collector``
    czyli coś trzyma referencję do danego obiektu
  - detached DOM nodes
  - dangling references
  - circular references

----

Memory leaks: detached DOM nodes
================================

.. code-block:: html

  <div id="grow">Zapełnij pamięć</div>

.. code-block:: javascript

  var detachedNodes;

  function create() {
    var ul = document.createElement('ul');
    for (var i = 0; i < 10; i++) {
      var li = document.createElement('li');
      ul.appendChild(li);
    }
    detachedNodes = ul;
  }

  document.getElementById('grow').addEventListener('click', create);

----

Memory leaks: dangling references
=================================

.. code-block:: javascript

  var theThing = null;
  var replaceThing = function () {
    var originalThing = theThing;

    var unused = function () {
      if (originalThing) { console.info('hi'); }
    };

    theThing = {
      longStr: new Array(1000000).join('*'),
      someMethod: function () {
        console.log(someMessage);
      }
    };

  };
  setInterval(replaceThing, 1000);

----

Memory leaks: circular references
=================================

.. code-block:: javascript

  function addClickHandler(element) {
      element.click = function onClick(e) {
          alert("Clicked the " + element.nodeName)
      }
  }


