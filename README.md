## Welcome to the Redux 4.0 Beta

Here are several guidelines to consider when testing:

First and foremeost, while we feel this version of Redux is fast approching stable, we must caution you about using this code in production.  At this time - should you chose to do so - it's with no guarentees from us for any given feature or function.

Second, unlike the current v3 of Redux, the plugin slug for v4 is not yet 'redux-framework'.  It is HIGHLY recommended you do not install this version into the current v3 folder.  The slug for this private build is 'redux-framework-4' and os what the plugin folder is titled.  When testing, please disable the v3 plugin.  Remember, the active plugin of Redux will supercede any embedded version.  You are also free to use embedding.

Third, as far as known issues go, there are potentially two we are aware of that will require my further investigating.  The first is a possible 'run in' with an embedded v3 when running v4 as a plugin.  The other is custom styling for the v4 option panl.  Some folks have restyled Redux to their own liking.  Because Redux v4 is now theme aware, current custom CSS may not render properly.  If that should happen, it is possible to turn off the 'theme aware' feature and return to the v3 styling which will not interfere with any custom styling.  To do this, all the followng argument to your global arguments array:

```php
'admin_theme => 'classic'
```

Fourth, for the time being, please report any issues here on this repo's issue tracker.  Please do not use the current redux-framework issue tracker for v3.  If filing as issue, please be aware the the usual instructions for sending reports.  Specifically, the support hash/URL and the specific steps and circumstances in which the issue occured.  Basically, we'll need instructions to guide us through what you did to recreate the issue.  If need be, we may ask you for a copy of your project in the event we're unable to recreate the issue on our own.

Fifth; Tranlations.  Due to the undertaking of rewriting the Redux core, more than a few translation strings were changed, removed, or added.  When Redux v4 goes 'gold' and is added to wp.org, we will be using their online translation services.  It will allow the community to add their own translations for the many languages out there.  Redux would then automatically download the one it needs on demand, versus packing them all in one project.  For now, a current .POT file is included in the ReduxCore/languages folder in the event you'd like to do some local translation.  If so, please feel free to submit them via pull request.  We will add them to wp.org when Redux v4 is released.  Eventually, lanuage submissions will be made here:  https://translate.wordpress.org/projects/wp-plugins/redux-framework (No need to do so right now, as any work done will apply to v3 and NOT v4).

Lastly, we are not accepting pull requests at this time.  The reason for this is because this code is extremely complicated, especially in terms of backward compatibility with v3.  Please propose changes via the issue tracker so they may be evaluated for backward compatibility.

If you would like to interact with us directly, you can join our Slack workspace at [http://slack.redux.io](http://slack.redux.io).  We have a channel dedicated for this beta.  Our handles are @Kev and @dovy.  Message us for access!

Please check back nightly for new code pushes.

## Changelog ##

See [Changelog.md](https://github.com/reduxframework/redux-framework-4/blob/master/CHANGELOG.md)

## Field Sanitizing ##

Field sanitizing allows one to pass an array of function names as an argument to a field in which the return value will be the sanitizing string.  This feature will only work with text based fields including text, textarea, and multi_text (ACE Editor and WP Editor not included).

One may use any existing function including PHP functions, WordPress functions and custom written functions.  The return value of any used function must be that of a string.  Any other return value will be disregarded.

Please view the [sample-config.php](https://github.com/reduxframework/redux-framework-4/blob/master/sample/sample-config.php) file for specific examples.

## Select2 AJAX Loading ##

The AJAX loading routines for the select2 fields have been fixed/finished.  See the 'capabilities' field in the demo panel for an example.  

For the interim, this feature will only work when used in conjunction with the `data` argument (that is, the one that fetches WordPress data).  

To set AJAX loading, add the `'ajax' => true` argument to your select field.  The `min_input_length` argument may also be added to specify how many characters should be typed before results are shown.  Default is `1`.

## Field/Section Disabling ##

This feature has been request quite a few times over the years.  Fields and sections can now be disabled by adding the `'disabled' => true` argument to either a section or a field.  The section or field will then appear 'greyed out' and not respond to input.  This comes in handy in the event one may want to offer teasers for premium versions of their products.

Since those with a little CSS know-how could easily reactive disabled fields with a little CSS, I took the added precaution of having Redux remove any `name` atttibutes on disabled fields/sections.  This way, even if a clever user reactivates the field, it will never save.

## Metabox Lite ##

A lite version of Metaboxes is available with Redux v4.  Please see the [sample-metabox-config.php](https://github.com/reduxframework/redux-framework-4/blob/master/sample/sample-metabox-config.php) in the `sample` folder for usage.

Metabox Lite supports the following fields only:  `text, textarea, checkbox, radio, color, media`.  Post Format and Page Template features are also not available.  These features plus support for all fields will be available in the Advanced Metaboxes portion of Redux Pro.

Due to the complex nature in which the Metaboxes feature integrates with Redux and existing option panels, it is important that a strict load order be maintained.  The metabox config must be loaded in your option config via a specific action hook, otherwise the metaboxes config will not load properly.  The see `BEGIN METABOX CONFIG` section of the [sample-config.php](https://github.com/kprovance/redux-dev/blob/master/sample/sample-config.php) file.

The current Metabox extension *is* supported and will override the lite version. 