Brief
=====

.. image:: https://img.shields.io/pypi/v/lazyxml.svg
   :target: https://pypi.python.org/pypi/lazyxml
   :alt: Latest Version
.. image:: https://img.shields.io/github/license/heronotears/lazyxml.svg
   :target: https://github.com/heronotears/lazyxml/blob/master/LICENSE
   :alt: License
.. image:: https://img.shields.io/pypi/dm/lazyxml.svg
   :target: https://pypi.python.org/pypi/lazyxml
   :alt: Downloads

简单的xml解析/生成库. 类似于simplejson的用法.


Installation
============

* Use `pip`

.. code-block:: bash

   $ pip install lazyxml

* Use `easy_install`

.. code-block:: bash

   $ easy_install lazyxml

* Use source. Download the project source and decompress, then do the following command.

.. code-block:: bash

   $ cd lazyxml
   $ python setup.py install


Examples
========

* xml转换成python对象

.. code-block:: python

   >>> import lazyxml
   >>> xml = '<demo><foo>foo</foo><bar>bar</bar></demo>'
   >>> lazyxml.loads(xml)
   {'bar': 'bar', 'foo': 'foo'}
   >>> lazyxml.loads(xml, strip_root=False)
   {'demo': {'bar': 'bar', 'foo': 'foo'}}
   >>> xml = '<demo><foo>foo</foo><bar>1</bar><bar>2</bar></demo>'
   >>> lazyxml.loads(xml)
   {'bar': ['1', '2'], 'foo': 'foo'}

* python对象转换成xml

.. code-block:: python

   >>> data = {'demo':{'bar': ['1', '2'], 'foo': '<foo>'}}
   >>> lazyxml.dumps(data)
   '<?xml version="1.0" encoding="utf-8"?><demo><foo><![CDATA[<foo>]]></foo><bar><![CDATA[1]]></bar><bar><![CDATA[2]]></bar></demo>'
   >>> lazyxml.dumps(data, cdata=False)
   '<?xml version="1.0" encoding="utf-8"?><demo><foo>&lt;foo&gt;</foo><bar>1</bar><bar>2</bar></demo>'
   >>> print lazyxml.dumps(data, indent=' ' * 4)
   <?xml version="1.0" encoding="utf-8"?>
   <demo>
       <foo><![CDATA[<foo>]]></foo>
       <bar><![CDATA[1]]></bar>
       <bar><![CDATA[2]]></bar>
   </demo>

* 详细用法参见 `demo <https://github.com/heronotears/lazyxml/tree/master/demo>`_


Documentation
=============

See `docs in pythonhosted <http://pythonhosted.org/lazyxml>`_ or `docs in readthedocs <http://lazyxml.readthedocs.org/en/latest/>`_



Changelog
=========

See `changelog <http://pythonhosted.org/lazyxml/changelog.html>`_
