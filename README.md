# Drupal 8 site using bootstrap 3 sub theme
based on 
## Generic Drupal 8 Site

## Usage

This site was coded in a Windows 10 machine, using Docker for Desktop

The `docker-compose.yml` file was updated to avoid port clash with existing mysql & web server ports in machine.

The sub theme was set up using bootstrap version 3.4.1 as base, and using bootstrap sass as the subtheme, making use of a css processing task based on laravel-mix. The configuration is hosted on the root of the sub theme folder named `javi`. Again, this configuration also was updated to work on a Win10 machine.

Full Drupal site was set up at http://localhost:8181 (from updated `docker-compose.yml` file) but this should be overriden to original master version of the file to avoid issues.

## Process
Exercise was entirely applied to `javi` sub theme code, meaning that base theme and original template twig files were not touched.

The edited files on sub theme are:
```
themes\custom\javi\scss\_default-variables.scss
themes\custom\javi\scss\_overrides.scss
themes\custom\javi\templates\system\page-title.html.twig
themes\custom\javi\templates\node\node.html.twig
```

The CSS was processed/generated with `laravel-mix` task runner, and automatically placed in <pre>javi/css/style.css</pre>

CSS code was left in development mode (i.e. not minified/uglified).

In order to ensure changes to drupal content were propagated, The `Run Cron` and `Clear Cache` actions have to be performed after every template / module change.

Also, for the site to work correctly with the subtheme, is needed to have base Bootstrap theme to be first installed and set as default; then, the sub theme has to be installed and set as default, in order to avoid certain styling issue.

Then, for the sub theme to apply CSS/JS correctly, is required to have the `Aggregate CSS files` and `Aggregate Javascript files` checkboxes cleared.
