---
name: Custom Template
---

# Customizing Templates

There are two types of template customizations you can utilize:
1. Template replacement
    * The core template is superseded by the custom template and thus the original will not execute.
    * Future template changes must be manually integrated into your custom override templates. 
2. Code injection
    * This keeps the original template, but simply injects additional code.
    * Future template changes are automatically integrated when you upgrade to newer releases.  
 

## Replace With a Custom Template
You can replace/override core templates by creating a custom version.  Your replacement templates will survive code updates, but you may want to keep tabs on them in case functionality changes. Be careful when replacing core templates as you may break things in future releases.

A great example is to customize the look and contents of the home page.

1. Copy the existing template  `/templates/home.tmpl` 
2. Save edited file as `custom/templates/home.tmpl` 

Edits to the custom template file(s) do not require restart Gogs

Other templates can also be replaced by saving the customized template in the same relative location as the original, but under the `custom/templates` directory.  Create subdirectories as needed in the `custom/templates` directory to match the corresponding template file you wish to override.  

To create a custom replacement 404 template, you would save it as `custom/templates/status/404.tmpl`


## Inject Code Into Existing Template
You can inject your custom head or footer content to Gogs without touching source code of main repository. This is useful if you want to add analytics code or include custom static resources.

[You can read more about injecting a custom head and footer here.](https://discuss.gogs.io/t/how-to-inject-custom-head-and-footer/943).

## Include Custom CSS File

Here is an example of how you can include a custom CSS file in your Gogs instance. Names and directories are just for demonstration, you can put it anywhere as long as it can be accessed via network requests.

1. Create a file named `custom.css` under `public/css` directory.
2. Put some CSS rules into the file.
3. Edit file `custom/templates/inject/head.tmpl` and add a line `<link rel="stylesheet" href="/css/custom.css">`
4. Restart Gogs
5. Further changes to the custom CSS file do not require restarting Gogs.
