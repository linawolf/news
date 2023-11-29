.. include:: /Includes.rst.txt

.. _viewButton:

===========
View button
===========

It is possible to activate the :guilabel:`View` Button for news records.

This button is displayed on the top of the edit record page:

.. figure:: /Images/ManualScreenshots/ViewButton.png
   :class: with-shadow

   The :guilabel:`View` button

Add the following page TSconfig to your root page. It is recommended to use
a site package extension, see
:doc:`Official Tutorial: Site Package <t3sitepackage:Index>` for this purpose.

.. code-block:: typoscript
   :caption: EXT:my_sitepackage/Configuration/page.tsconfig

   TCEMAIN.preview {
      tx_news_domain_model_news {
         previewPageId = 123
         useDefaultLanguageRecord = 0
         fieldToParameterMap {
            uid = tx_news_pi1[news_preview]
         }
         additionalGetParameters {
            tx_news_pi1.controller = News
            tx_news_pi1.action = detail
         }
      }
   }

By using the given example, a link will be generated which leads to the
page with the id `123`.

If a news plugin is placed on this page, the news article will be shown.

.. hint::
   This TSconfig configuration can be used to display any record with with any
   kind of parameters. Read more about it in
   :ref:`TSconfig Reference: TCEMAIN.preview <t3tsconfig:pagetcemain-preview>`.

Preview hidden and other non-visible news records
=================================================

If you also want to preveiw hidden news records, use the setting 
:confval:`previewHiddenRecords` in your TypoScript setup configuration:

.. code-block:: typoscript
   :caption: EXT:my_sitepackage/Configuration/TypoScript/setup.typoscript

   plugin.tx_news.settings.previewHiddenRecords = 1

Use a single view plugin on a page that is secured from non-admin users, for example by
Using the page type :guilabel:`Backend User Section`. Or by making the page availible
to authorisized frontend users only.
