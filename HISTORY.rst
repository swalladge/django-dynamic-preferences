.. :changelog:

Changelog
=========

1.3 (03-07-2017)
*******************

This release fix a critical bug in 1.2 that can result in data loss.

Please upgrade to 1.3 as soon as possible and never use 1.2 in production. See `#81 <https://github.com/EliotBerriot/django-dynamic-preferences/pull/81>`_ for more details.

1.2 (06-07-2017)
*******************

.. warning::

    There is a critical bug in this that can result in dataloss. Please upgrade to 1.3 as
    soon as possible and never use 1.2 in production. See `#81 <https://github.com/EliotBerriot/django-dynamic-preferences/pull/81>`_ for more details.

- important performance improvements (less database and cache queries)
- A brand new `REST API <https://django-dynamic-preferences.readthedocs.io/en/latest/rest_api.html>`_ based on Django REST Framework, to interact with preferences (this is an optionnal, opt-in feature)
- A new `FilePreference <https://django-dynamic-preferences.readthedocs.io/en/latest/preference_types.html#dynamic_preferences.types.FilePreference>`_ [original work by @macolo]

1.1.1 (11-05-2017)
*******************

Bugfix release to restore disabled user preferences admin (#77).

1.1 (06-03-2017)
*****************

* Fixed #49 and #71 by passing full section objects in templates (and not just the section identifiers). This means it's easier to write template that use sections, for example if you want have i18n in your project and want to display the translated section's name. URL reversing for sections is also more reliable in templates. If you subclassed `PreferenceRegistry`  to implement your own preference class and use the built-in templates, you need to add a ``section_url_namespace`` attribute to your registry class to benefit from the new URL reversing.

[Major release] 1.0 (21-02-2017)
***********************************

Dynamic-preferences was release more than two years ago, and since then, more than 20 feature and bugfixe releases have been published.
But even after two years the project was still advertised as in Alpha-state on PyPi, and  the tags used for the releases, were implicitly saying that the project was not production-ready.

Today, we're changing that by releasing the first major version of dynamic-preferences, the ``1.0`` release. We will stick to semantic versioning and keep backward compatibility until the next major version.

Dynamic-preferences is already used in various production applications .The implemented features are stable, working, and address many of the uses cases the project was designed for:

- painless and efficient global configuration for your project
- painless and efficient per-user (or any other model) settings
- ease-of-use, both for end-user (via the admin interface) and developpers (settings are easy to create and to manage)
- more than decent performance, thanks to caching

By making a major release, we want to show that the project is trustworthy and, in the end, to attract new users and develop the community around it. Development will goes on as before, with an increased focus on stability and backward compatibility.

**Because of the major version switch, some dirt was removed from the code, and manual intervention is required for the upgrade. Please have a for the detailed instructions:** https://django-dynamic-preferences.readthedocs.io/en/latest/upgrade.html

Thanks to all the people who contributed over the years by reporting bugs, asking for new features, working on the documentation or on implementing solutions!

0.8.4 (10-01-2017)
******************

This version is an emergency release to restore backward compatibility that was broken in 0.8.3, as
described in issue #67. Please upgrade as soon as possible if you use 0.8.3.

Special thanks to [czlee](https://github.com/czlee) for reporting this!


0.8.3 (06-01-2017) (**DO NOT USE: BACKWARD INCOMPATIBLE**)
**********************************************************

**This release introduced by mistake a backward incompatible change (commit 723f2e).**
**Please upgrade to 0.8.4 or higher to restore backward compatibility with earlier versions**

This is a small bugfix release. Happy new year everyone!

* Now fetch model default value using the get_default method
* Fixed #50: now use real apps path for autodiscovering, should fix some strange error when using AppConfig and explicit AppConfig path in INSTALLED_APPS
* Fix #63: Added initial doc to explain how to bind preferences to arbitrary models (#65)
* Added test to ensure form submission works when no section filter is applied, see #53
* Example project now works with latest django versions
* Added missing max_length on example model
* Fixed a few typos in example project


0.8.2 (23-08-2016)
******************

* Added django 1.10 compatibility [ricard33]
* Fixed tests for django 1.7
* Fix issue #57: PreferenceManager.get() returns value [ricard33]
* Fixed missing coma in boolean serializer [czlee]
* Added some documentations and example [JetUni]

0.8.1 (25-02-2016)
******************

* Fixed still inconsistend preference order in form builder (#44) [czlee]

0.8 (23-02-2016)
****************

**Warning**: there is a backward incompatbile change in this release. To address #45 and #46, an
import statement was removed from __init__.py. Please refer to the documentation for upgrade instructions:
http://django-dynamic-preferences.readthedocs.org/en/stable/upgrade.html

0.7.2 (23-02-2016)
******************

* Fix #45: importerrror on pip install, and removed useless import
* Replaced built-in registries by persisting_theory, this will maintain a consistent order for preferences, see #44

0.7.1 (12-02-2016)
******************

* Removed useless sections and fixed typos/structure in documentation, fix #39
* Added setting to disable user preferences admin, see #33
* Added setting to disable preference caching, fix #7
* Added validation agains sections and preferences names, fix #28, it could raise backward incompatible behaviour, since invalid names will stop execution by default

0.7 (12-01-2016)
****************

* Added by_name and get_by_name methods on manager to retrieve preferences without using sections, fix #34
* Added float preference, fix #31 [philipbelesky]
* Made name, section read-only in django admin, fix #36 [what-digital]
* Fixed typos in documentation [philipbelesky]

0.6.6 (23-12-2015)
******************

* Fixed #23 (again bis repetita): Fixed second migration to create section and name columns with correct length

0.6.5 (23-12-2015)
******************

* Fixed #23 (again): Fixed initial migration to create section and name columns with correct length

0.6.4 (23-12-2015)
******************

* Fixed #23: Added migration for shorter names and sections

0.6.3 (09-12-2015)
******************

* Fixed #27: AttributeError: 'unicode' object has no attribute 'name' in preference `__repr__` [pomerama]

0.6.2 (24-11-2015)
******************

* Added support for django 1.9, [yurtaev]
* Better travic CI conf (which run tests against two version of Python and three versions of django up to 1.9), fix #22 [yurtaev]

0.6.1 (6-11-2015)
*****************

* Added decimal field and serializer

0.6 (24-10-2015)
****************

* Fixed #10 : added model choice preference
* Fixed #19 : Sections are now plain python objects, the string notation is now deprecated

0.5.4 (06-09-2015)
******************

* Merged PR #16 that fix a typo in the code

0.5.3 (24-08-2015)
******************

* Added switch for list_editable in admin and warning in documentation, fix #14
* Now use Textarea for LongStringPreference, fix #15

0.5.2 (22-07-2015)
******************

* Fixed models not loaded error

0.5.1 (17-07-2015)
******************

* Fixed pip install (#3), thanks @willseward
* It's now easier to override preference form field attributes on a preference (please refer to `Preferences attributes <http://django-dynamic-preferences.readthedocs.org/en/latest/quickstart.html#preferences-attributes>`_  for more information)
* Cleaner serializer api

0.5 (12-07-2015)
****************

This release may involves some specific upgrade steps, please refer to the ``Upgrade`` section of the documentation.

0.5 (12-07-2015)
****************

This release may involves some specific upgrade steps, please refer to the ``Upgrade`` section of the documentation.

* Migration to CharField for section and name fields. This fix MySQL compatibility issue #2
* Updated example project to the 0.4 API

0.4.2 (05-07-2015)
******************

* Minor changes to README / docs

0.4.1 (05-07-2015)
******************

* The cookiecutter part was not fully merged

0.4 (05-07-2015)
****************

* Implemented cache to avoid database queries when possible, which should result in huge performance improvements
* Whole API cleanup, we now use dict-like objects to get preferences values, which simplifies the code a lot (Thanks to Ryan Anguiano)
* Migrated the whole app to cookiecutter-djangopackage layout
* Docs update to reflect the new API

0.3.1 (10-06-2015)
******************

* Improved test setup
* More precise data in setup.py classifiers

0.2.4 (14-10-2014)
******************

* Added Python 3.4 compatibility

0.2.3 (22-08-2014)
******************

* Added LongStringPreference

0.2.2 (21-08-2014)
******************

* Removed view that added global and user preferences to context. They are now replaced by template context processors

0.2.1 (09-07-2014)
******************

* Switched from GPLv3 to BSD license
