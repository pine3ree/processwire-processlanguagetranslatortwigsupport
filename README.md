### ProcessWire 

# Process Language Translator Twig Support

## Overview:

Extends Language Translator Modul.  
Changes view and adds twig support.  
If you don't use Twig (for example [TemplateTwigReplace](http://modules.processwire.com/modules/template-twig-replace)) 
as template engine, you can use this module equally.

Designed for use with ProcessWire 2.6
[http://processwire.com](http://processwire.com)

## Installation

1. Clone the module and place `ProcessLanguageTranslatorTwigSupport` in your site/modules/ directory. 

```
git clone https://github.com/justonestep/processwire-processlanguagetranslatortwigsupport.git your/path/site/modules/ProcessLanguageTranslatorTwigSupport
```

2. Login to ProcessWire admin and click Modules. 
3. Click "Check for new modules".
4. Click "install" next to the new `ProcessLanguageTranslatorTwigSupport` module. 
   If you do use Twig as template engine, you have to install the `TemplateTwigReplaceLanguageSupport` module as well.
5. That's all!

## Usage ProcessLanguageTranslatorTwigSupport

**admin/setup/languages**

In ProcessWire admin go to _admin/setup/languages_.  
Choose a language and click on the button _Translate File_.  
Now you see a dropdown list of all files you don't have translated for the choosen language yet.  

**Notice**: If you use twig as your template engine, you get your twig files listed!

Choose a file, click _Translate File_ and translate all phrases you want to.

Below that list is a language switcher, where you can easily switch your language.

![Setup Languages](https://github.com/justonestep/processwire-processlanguagetranslatortwigsupport/blob/master/screens/languages.png)

**admin/setup/language-translator**

In ProcessWire admin go to _admin/setup/language-translator_.  
On the top is a language switcher as well.  
All translated files for the choosen language are listed.  
You can edit the belonging phrases by clicking on the file.  
Furthermore you can add another file to translate by clicking the _Translate another File_ Button.

![Setup Language-Translator](https://github.com/justonestep/processwire-processlanguagetranslatortwigsupport/blob/master/screens/language-translator.png)

## Usage TemplateTwigReplaceLanguageSupport

To get your `.twig` files listed as well, you need to wrap the phrases like this:

```html
{{ __('text to translate', 'filepath/filename relative to site/templates/') }}
{{ __('another text to translate', 'home') }}
{{ __('one more text to translate', 'partials/header') }}
```

* first line - general usage
* second line - example for a text in _site/templates/home.twig_
* third line - example tor a text in _site/templates/partials/header.twig_

## Often used translations

You could wrap often used translations in a file called ``_strings.twig`` placed in ``site/templates``. Doing this you can copy this file between various ProcessWire installations und reuse it. Make sure to copy also the corresponding json file and import it.

Calling such a translation in another file is really easy, you don't have to provide a translation domain:

```html
{{ __('Save') }}
```

Now have a look at ``_strings.twig``, in this file you need to have the same entry (one per line) including a translation domain.

Example on how ``_strings.twig`` could look like:

```html
{# Intentionally commented out

{% set s = '_strings %}

{{ __('Save', s) }}
{{ __('Send', s) }}
{{ __('Email address', s) }}

#}
```

## Enable Language Translators for Editors

This module provides a permission called **language-edit** (you see this permission listed here: ``Admin > Access > Permissions``).

If a specific role should be able to use the Language Translator just go to ``Admin > Access > Roles``, edit the specific role and check **language-edit**.

The modules will display **only the site translation files**, the core files will be hidden.

If you need the interface to be translated go to module settings (Language Translator Twig Support) and activate the checkbox. **Be careful:** there was no way to use a normal hook before/after method, this hook replaces a core function. A pull request (enhance language translator module for text translation, avoid label text duplication) was sent, hopefully I can remove this soon. 

After activating the checkbox you can translate all the content using the Language Translator. You have to add a translation for ``site/modules/ProcessLanguageTranslatorTwigSupport/ProcessLanguageTranslatorTwigSupport.module``.

