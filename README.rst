Fish Atlas Transformation
=========================

This codebase transforms one old-style static website into a Bootstrap-kicking
awesome-looking set of responsive pages.  We provide a server for live-theming
the files -- trying to rely on a script (eg Regex) to do the transform would
not only be `insane
<http://stackoverflow.com/questions/1732348/regex-match-open-tags-except-xhtml-self-contained-tags/`>_
but also really slow because a static site is usually full of inconsistencies,
just like this one is!

The code is provided in the public domain for those who might be interested in
doing the same thing -- transforming old, static webpages according to a set
of rules.  Keep in mind the code here is an example **only** and you'll need
to build rules that work for your own site.  The code provided is specifically
geared for the Fish Atlas pages and is hard-coding the transformations because
that's the only way it's possible.

Technology used
---------------

* Python
* Diazo theming engine (CSS to XSLT transforms)
* PasteScript
* Bower
* wget script (https://github.com/jcu-eresearch/static-plone-wget)

Setup
-----

.. code-block:: bash

   virtualenv . -p /usr/bin/python2.7
   source ./bin/activate
   pip install -r requirements.txt #installs python dependencies
   bower install #installs dependencies
   # Serve the local files, transformed
   ./bin/paster serve development.ini --reload

By doing the above, you can now view the transformed files live at
``http://localhost:8080``.

Try the site out, adjust the Diazo rules accordingly if your transformation is
lacking and when you're ready, wget the site back to static files::

   git clone https://github.com/jcu-eresearch/static-plone-wget.git
   ./static-plone-wget/wget_plone.sh http://localhost:8080/Index.htm

