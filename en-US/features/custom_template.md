---
name: Custom template
---

# Customizing templates

## Override HTML templates

You can override HTML templates (including templates for emails) by creating a customized version under `custom/templates/` directory. Your version of HTML templates will survive code updates, but you may want to keep tabs on them in case functionality changes. Be careful when overriding HTML templates as you may break things in future releases.

An example is to customize the look and contents of the home page:

1. Copy the content of template file `templates/home.tmpl`.
2. Save edited file as `custom/templates/home.tmpl`.

:warning: Edits to the custom HTML templates **require restarting Gogs**.

:warning: Override for email templates is disabled when `[server] LOAD_ASSETS_FROM_DISK = true`

## Override static files

You can override static files (CSS, JavaScript, images, etc.) by creating a customized version under `custom/public/` directory. Your version of static files will survive code updates, but you may want to keep tabs on them in case functionality changes. Be careful when overriding static files as you may break things in future releases.

For example, you can override the site favicon by putting your version of favicon to `custom/public/img/favicon.png`.

:warning: Edits to the custom static files **DO NOT require restarting Gogs**.

## Inject content into existing templates

You can inject your custom head or footer content to Gogs without touching source code of main repository. This is useful if you want to add analytics code or include custom static resources.

[You can read more about injecting a custom head and footer here.](https://discuss.gogs.io/t/how-to-inject-custom-head-and-footer/943).

This approach is recommended whenever possible because it has the minimum impact on templates.

### Inject custom CSS file

Here is an example of how you can include a custom CSS file in your Gogs instance. Names and directories are just for demonstration, you can put it anywhere as long as it can be accessed via network requests.

1. Create a file named `custom.css` under `custom/public/css/` directory.
2. Put some CSS rules into the file.
3. Edit file `custom/templates/inject/head.tmpl` and add a line `<link rel="stylesheet" href="/css/custom.css">`
4. Restart Gogs.
5. Future edits to the custom CSS file **DO NOT require restarting Gogs**.
