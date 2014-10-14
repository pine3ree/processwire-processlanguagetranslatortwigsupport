### ProcessWire 

# Process Language Translator Twig Support

## Overview:

Extends Language Translator Modul.  
Changes view and adds twig support.  
If you don't use Twig (for example [TemplateTwigReplace](http://modules.processwire.com/modules/template-twig-replace)) 
as template engine, you can use this module equally.

Designed for use with ProcessWire 2.5
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
