Changelog
=========

1.2.0 (unreleased)
------------------

- Moved away from extending ATLink. It was probably a bad idea from the beginning, plus
  some `changes`__ introduced on Plone 4.2 lead to issue when external video contents are show in
  portal tab and navigation
  [keul]

__ https://github.com/plone/Products.CMFPlone/commit/be6b828870387259a731bf13c45150258efc48cb

1.1.1 (2015-08-17)
------------------

- Handle possible HTTP ``Not Found`` error in thumbnail retrieve
  [cekk]


1.1.0 (2014-07-11)
------------------

- Fixed Python import for Plone 4.3 (close `#14`__) [bhenker]
- Named the schemaextender adapter, to be compatible with latests
  collective.flowplayer versions [keul]

  __ https://github.com/RedTurtle/redturtle.video/pull/14

- Fix permission to add portlet. Now who can manage portlets can create it [cekk]
- Added the uninstall profile (this close `#12`__) [keul]

  __ https://github.com/RedTurtle/redturtle.video/issues/12

- Added a Generic Setup import profile for migrate to wildcard.media
  (at the best of what we can do) [keul]

1.0.1 (2013-04-03)
------------------

- We don't need any new catalog index so we are not creating them.
  To don't break 3rd party packages we will *not* remove index when upgrading
  [keul]
- Added reindex for hasSplashScreenImage when retrieve thumb from external plugin
  [cekk]

1.0.0 (2012-10-01)
------------------

- Updated italian translation [keul]
- Added video path to portlet info dict [cekk]

0.8.1 (2012-09-21)
------------------

- added fix for thumb size. Now uses plone.app.imaging sizes [cekk]

0.8.0 (2012-09-04)
------------------

* add a body field to the video types [davismr]
* fixed missing Generic Setup dependency (close `#8`__) [davismr]
* adds events that call getThumb on the RemoteVideo adapter, and try to get a thumb image
  for the video [cekk, lucabel]
* fixed a GS circular dependency error [keul]
* video size in content was ignored when also present in video metadata (close `#6`__)
  [keul]

__ https://github.com/RedTurtle/redturtle.video/pull/8
__ https://github.com/RedTurtle/redturtle.video/issues/6

0.7.3 (2012-05-18)
------------------

* version 0.7.2 was a broken egg [keul]

0.7.2 (2012-05-17)
------------------

* removed (commented) code that reindex an index when it's created while installing
  the product. This can take a *very* long time on huge site [keul]
* added spanish translation [Manuel]
* fixed tests for Plone 4.2 compatibility [keul]
* fixed migration step that was not running the proper dependecy (see `#2`__) [keul]
* year field now limited to 4 chars [keul]
* from now include compiled .mo files in the egg [keul]
* fixed a bug when migrating from File to InternalVideo on Plone 4 (using plone.app.blob).
  ``IVideo`` now extends ``IFileContent`` [keul]

__ https://github.com/RedTurtle/redturtle.video/issues/2

0.7.1 (2012-01-02)
------------------

* blob file field have a different meta_type that make the migration walker fail.
  Now supported both ATFile and ATBlob [keul]
* the migrator view from File was not properly taking video metadata [keul]
* ``getEmbedCode`` and ``getPlayerCode`` methods can now be called from other views [keul]
* no more running ``plone.app.image`` generic profile setup when installing.
  This was giving some trouble when the products was already in use, because
  custom image size are removed [keul]
* related items in Plone 4 were doubled; fixed. to keep also Plone 3 compatibility,
  added dependency to `collective.relateditems`__ [keul]
* fixed a bug that break video if a user remove sizes information [keul]
* fixed bug in metadata extraction on Plone 3 if not blob support is present [keul]

__ http://plone.org/products/collective.relateditems/

0.7.0 (2011-09-28)
------------------

* added a ``@@flowplayer-video-migration`` for migrate base Plone Flowplayer enabled contents to RedTurtle
  Video contents [keul]
* updated documentation related to iOS devices [keul]

0.6.0 (2011-08-31)
------------------

* update imports to support latest zope.formlib release, which is
  pinned in 4.1 release [mamico]
* dependency on ``Products.CMFPlone`` instead of ``Plone``, for
  Plone 4.1 compatibility (see `documentation`__) [keul]
* fixed portlet target_url if the target is a folder (close `#10`__) [cekk]
* removed internal support for "Vimeo" and "Metacafe" services, moved away in proper external projects.
  This close ticket `#7`__ [keul]
* added two ZMI properties to controls default video size when creating new contents. Also the default
  size has been changed to 400x300 [keul]
* added some missing ``.copy()`` call when working with default AT schema (close `#9`__)  [keul]
* fixed some CSS z-index issues that create problems with Sunburst theme and other add-ons
  (close `#8`__) [nekorin]

__ http://plone.org/documentation/manual/upgrade-guide/version/upgrading-plone-4.0-to-4.1/updating-add-on-products-for-plone-4.1/changing-dependencies-from-plone-to-products.cmfplone
__ http://plone.org/products/redturtle.video/issues/10
__ http://plone.org/products/redturtle.video/issues/7
__ http://plone.org/products/redturtle.video/issues/9
__ http://plone.org/products/redturtle.video/issues/8

0.5.2 (2011-05-30)
------------------

* file field for RTInternalVideo content is defined
  as primary also with blobs, so can be used with FTP/WEB-DAV uploads
  [keul]
* RTInternalVideo now register himself for video content in the
  ``content_type_registry`` [keul]

0.5.1 (2011-05-19)
------------------

* restored "i18n" folder for translate the ``plone`` domain
  (translation with locales sometimes sucks) [keul]

0.5.0 (2011-05-12)
------------------

* fixed dependency for plone.app.imaging to version 1.0b9 or better [keul]
* removed support for video.google.com videos (close `#6`__) [keul]
* removed support for youtube video, moved to `collective.rtvideo.youtube`__
  this is part of ticket `#7`__ [keul]
* typo error bug fixed: Vimeo embed view was using YouTube template [keul]
* now also remote video use size fields for the view [keul]
* XHTML fix for Metacafe template [keul]
* Fixed a bug that break saving an internalvideo,
  when metadata can't be extracted [keul]
* when using splashscreen image, also display a "Play" icon on the image
  [nekorin]
* translations fixes [keul]

__ http://plone.org/products/redturtle.video/issues/6
__ http://pypi.python.org/pypi/collective.rtvideo.youtube
__ http://plone.org/products/redturtle.video/issues/7

0.4.0 (2011-04-14)
------------------

* add metacafe.com and video.google.com adapters [nan010]
* add some documentation how to write an adapter [nan010]
* video contents now implements the ``IImageContent`` interface [keul]
* now supported `plone.app.blob`__ [keul]
* added way (*/@@blob-video-migration* view) to migrate from ZODB to blob [keul]
* bug fixed: the title for internal video was not required [keul]
* shortened the embedding code, using the `External configuration file`__,
  this also fix problems when embedding in documents using TinyMCE [keul]
* the internal video size is now the uploaded video size (close `#1`__) [keul]
* simple video links to .flv URL were broken [keul]
* restored right position for a lot of viewlet manager
  (reverting some changes done in version 0.3.1) [keul]
* splashscreen image can be used (optionally) as real video splashscreen.
  Now `plone.app.imaging`__ is required (even without ``plone.app.blob``) [keul]
* added video size fields; video view and embed code now use it [keul]
* properly registering types in TinyMCE (this close `#5`__) [keul]
* external video now provides the ``IFlowPlayable`` interface only when linking
  simple .flv resources. This close `#2`__ [keul]
* portlet header is not required anymore [keul]

__ http://pypi.python.org/pypi/plone.app.blob
__ http://flowplayer.org/demos/installation/alternate/index.html#external_config
__ http://plone.org/products/redturtle.video/issues/1
__ http://pypi.python.org/pypi/plone.app.imaging
__ http://plone.org/products/redturtle.video/issues/5
__ http://plone.org/products/redturtle.video/issues/2

0.3.1 (2010-03-18)
------------------

* inserted embed string over the player [fdelia]

0.3.0 (2010-03-03)
------------------

* embedded code link to flowplayer [alert, fdelia, keul]
* added youtube.com and vimeo.com adapters [gborelli]
* getting video embed html code with adapter (and removed BeautifulSoup) [gborelli]
* added redturtle_video macros [gborelli]
* added some tests [gborelli]
* added locales rebuild script [gborelli]
* fixed package install [gborelli]

0.2.2 (2009-11-11)
------------------

* portlet does not return the getYear and getDuration method anymore [keul]
* moved hachoir import inside function from module level, due to stdout PDB error [keul]
* added a *very* ugly support for remote video to Youtube links [keul]
* removed validators for image field as it was not required but was not possible to ignore it [keul]

0.2.1beta (2009-10-19)
----------------------

* fixed bug using redturtle.video with latests collective.flowplayer versions (3.0+) [fdelia]
* tested with latest flowplayer release [fdelia]

0.2.0beta (2009-10-14)
----------------------

* added informations (duration and year) of the video, that will be displayed in the portlet
* fixed bug finders in using getFolderContents for ATTopic

0.1.0alpha (2009-09-28)
-----------------------

* initial release
