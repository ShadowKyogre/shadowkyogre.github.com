<!-- 
.. title: QTarot
.. slug: QTarot
.. date: 2014-07-17 21:58:59 UTC-07:00
.. tags: 
.. link: 
.. template: github-project.tmpl
.. author: ShadowKyogre
.. description: A simple tarot fortune teller
.. type: text
.. contributors: [('ShadowKyogre', '/about'),]
-->

QTarot is a simple fortune telling app for Linux systems primarily. It works on Windows too. I'm pretty sure it works on Macs. Currently only has the Rider-Waite deck and the Elder Futhark, but more can be added. You can also change the background image for the current reading.

# Todo

* Make a GUI editor for deck definitions
* Make a GUI editor for layouts
* Make only the basename for an image in a deck definition matter
* Actually fill out the Elder Futhark deck definition
* More deck themes :|.
* Streamline the GUI for making a new reading with another deck definition

# Dependencies

* Python 3
* PyQt
* lxml

# Install

Copy the files to /usr/share/qtarot if you plan to use the *.desktop file included. If not, feel free to leave it where you downloaded it or place it somewhere else.

# License

GPL

# Credits

Inspired by <http://www.zyqote.com/Linux/pub/tarot/> and <http://linux.softpedia.com/get/Education/Qtarot-18925.shtml>.
Default deck and table also are from here.

## Deck definitions
* Teaser deck definitions for the Rider-Waite deck are courtesy of [Biddy Tarot](http://www.biddytarot.com). Please check out her page by clicking her name.

## Layout sources

* <http://www.tryskelion.com/tryskelion/planetary.htm>
* <http://www.readtarot.com/spreads.html>
* <http://www.learntarot.com/yinyang.htm>

## Stuff I looked up while writing not related to layouts

* <http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-0.4.html>
* <http://stackoverflow.com/questions/7451183/how-to-create-image-file-from-qgraphicsscene-qgraphicsview>
* <http://www.qtcentre.org/wiki/index.php?title=QGraphicsView:_Smooth_Panning_and_Zooming#Zooming>
* <http://thesmithfam.org/blog/2007/02/03/qt-improving-qgraphicsview-performance/>
* <http://kunalmaemo.blogspot.com/2010/07/rotation-and-mirroring-qgraphicsitem-in.html>