---
name: Custom Template
---

# Custom Template

You can inject your custom head or footer content to Gogs without touching source code of main repository. This is useful if you want to add analytics code or include custom statis resources.

Read more about [inject custom head and footer](https://discuss.gogs.io/t/how-to-inject-custom-head-and-footer/943).

## Include Custom CSS File

Here is an example of how you can include a custom CSS file to your Gogs instance. Names and directory are just for demonstration, you can put anywhere as long as it can be accessed via network requests.

1. Create a file named `custom.css` under `public/css` directory.
2. Put some CSS rules into the file.
3. Edit file `custom/templates/inject/head.tmpl` and add a line `<link rel="stylesheet" href="/css/custom.css">`
4. Restart Gogs
5. More editing to the custom CSS file does not require restart Gogs