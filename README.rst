##############
Growers Nation Dojo Theme
##############

Based on the Dojo Bootstrap project developed by thesociable: https://github.com/thesociable/dbootstrap

.. image:: https://raw.github.com/thesociable/dbootstrap/master/resource/preview.png

************
Get The Code
************

    $ git clone --recursive git://github.com/GrowersNation/dbootstrap.git

******************
Build Requirements
******************

To build the project locally you will need the following installed:

* `Python <http://www.python.org>`_ >= 2.6, <3
* `Nodejs <http://www.nodejs.org>`_ >= 10.5
* `Stylus <http://learnboost.github.io/stylus/>`_ >= 0.31
* `Java <http://www.java.com>`_ >= 7.0 (aka 1.7.0)

All other requirements are bundled as git submodules so make sure you have
initialised them (the default when using `--recursive` with `git clone`)

****
Demo
****

For a live preview of the theme using Dojo's Theme Tester, see
http://thesociable.github.com/dbootstrap/

To build the demo locally:

#. Navigate to your clone of the repo::

    $ cd /path/to/dbootstrap

#. Build it::

    $ python build.py demo

   .. note::

        If you like to see what is going on under the hood, run with a lower
        logging level::

             $ python build.py -v debug demo

#. Fire up a server::

    $ cd build/demo
    $ python -m SimpleHTTPServer 8000

#. Take a look::

    Point your browser at http://localhost:8000/

***********
Integration
***********

Want to use the theme in your own project? Here's a short guide to integrating
it successfully.

Standalone Package
==================

Useful if you just want a quick play of the theme with your project. For a
better solution see the integrated build below.

#. Navigate to your clone of the repo::

    $ cd /path/to/dbootstrap

#. Build just the theme::

    $ python build.py theme

   .. note::

        If you like to see what is going on under the hood, run with a lower
        logging level::

            $ python build.py -v debug theme

#. Copy (or link) the resulting package *dbootstrap/build/theme/dbootstrap*
   into the appropriate location in your project and ensure you notify Dojo
   about the location. One way to do this is through the Dojo config::

    'packages': [
        ...,
        {
            location: '/path/to/dbootstrap',
            name: 'dbootstrap'
        }
    ]

#. Add a require call for dbootstrap. You must require dbootstrap
   before any Dijit widgets are loaded for the icons to work correctly::

    require(['dbootstrap', ...], function(dbootstrap) {
        // Start application.
    });

#. Add *dbootstrap* as a css class to your <body> element::

    <body class='dbootstrap'>

#. View your project as normal.

Integrated Build
================

#. Copy or link the *dbootstrap/source/dbootstrap* folder into your project
   (typically so that it is a sibling to your Dojo and Dijit packages). You
   will also need to link the *xstyle* and *nib* packages if you don't already
   have them.

   .. note::

       Only tested with Dojo 1.8+

#. Add the following to your build profile.js to include dbootstrap as a
   package and separate build layer::

    packages: [
        ...
        'dbootstrap',
        'xstyle'
    ],

    layers: {
        ...
        'dbootstrap/main': {
            include: [
                'dbootstrap/main',
                'xstyle/load-css'
            ],
        }
    }

   .. note::

        If you have placed your dbootstrap package somewhere that isn't
        directly accessible as a child directory of your *basePath* then you
        must use the fuller package syntax in the packages list::

            {
                location: '/path/to/dbootstrap',
                name: 'dbootstrap'
            }

#. In your main application entry point (or index.html) require the dbootstrap
   package before any Dijit widgets are loaded::

    require(['dbootstrap', ...], function(dbootstrap) {
        // Start application.
    });

#. Add *dbootstrap* as a css class to your <body> element::

    <body class='dbootstrap'>

#. Add to your build process relevant calls to Stylus to compile the CSS files
   into one dbootstrap.css file::

    $ stylus --include path/to/dbootstrap/nib/lib \
             --include path/to/dbootstrap/theme/dbootstrap \
             path/to/dbootstrap/theme/dbootstrap/index.styl

    $ mv path/to/dbootstrap/theme/dbootstrap/index.css \
         path/to/dbootstrap/theme/dbootstrap/dbootstrap.css

   .. note::

        The CSS build must happen before the Dojo build is performed as the
        generated css file is required as part of the build. Therefore, the css
        file is built in the source tree to be copied to the build directory
        during the Dojo build step.

#. Build your project and view as normal.


***********
Bug tracker
***********

Found a bug? Report it at https://github.com/thesociable/dbootstrap/issues

*********************
Copyright and license
*********************

Copyright (c) 2012 Martin Pengelly-Phillips

Licensed under the Apache License, Version 2.0 (the "License"); you may not use
this work except in compliance with the License. You may obtain a copy of the
License in the LICENSE.txt file, or at:

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed
under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
CONDITIONS OF ANY KIND, either express or implied. See the License for the
specific language governing permissions and limitations under the License.

Font-Awesome
============

The icons are provided by the excellent Font-Awesome team at
http://fortawesome.github.com/Font-Awesome/

