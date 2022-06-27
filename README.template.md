Frontend App README Template
=============================

<!--
This should act as a template README.md for a new frontend application.
Just remove the parts that are not relevant to your bundle and
replace placeholders like "{{Name}}" with your app name and so on.

List of placeholders:
- {{name}}: Name of the app in lowercase, like "formalize"
- {{Name}}: Name of the app in camel case, like "Formalize"
- {{NAME}}: Name of the app in uppercase, like "FORMALIZE"
- {{bundle-path}}: GitLab bundle repository path, like "formalize/dbp-relay-formalize-bundle"
- {{bundle-name}}: Name of the bundle for packagist, like "relay-formalize-bundle"
- {{app-path}}: GitLab repository path of the frontend application, like "formalize/formalize"
- {{app-description}}: A brief description of the app in 2-5 sentences
- {{list-of-activities}}: A list of activities in the app
- {{app-based-attributes}}: Add app based attributes to the table(name | type | [activity-name](link-to-activity))
-->

# {{Name}} Application

{{app-description}}

[GitLab Repository](https://gitlab.tugraz.at/dbp/{{app-path}}) |
[npmjs package](https://www.npmjs.com/package/@dbp-topics/{{name}}) |
[Unpkg CDN](https://unpkg.com/browse/@dbp-topics/{{name}}/) |
[{{Name}} Bundle](https://gitlab.tugraz.at/dbp/{{bundle-path}}) |
[Project documentation](https://dbp-demo.tugraz.at/site/software/{{name}}.html)

## Prerequisites

- You need the [API server](https://gitlab.tugraz.at/dbp/relay/dbp-relay-server-template) running
- You need the [{{bundle-name}}](https://gitlab.tugraz.at/dbp/{{bundle-path}}) 
- For more information please visit the [{{name}} project documentation](https://dbp-demo.tugraz.at/site/software/{{name}}.html)

## Local development

```bash
# get the source
git clone git@gitlab.tugraz.at:dbp/{{app-path}}.git
cd signature
git submodule update --init

# install dependencies
yarn install

# constantly build dist/bundle.js and run a local web-server on port 8001 
yarn run watch

# run tests
yarn test
```

Jump to <http://localhost:8001> and you should get a Single Sign On login page.

## Using this app as pre-built package

### Install app

If you want to install the DBP Signature App in a new folder `{{name}}-app` with a path prefix `/` you can call:

```bash
npx @digital-blueprint/cli install-app {{name}} {{name}}-app /
```

Afterwards you can point your Apache web-server to `{{name}}-app/public`.

Make sure you are allowing `.htaccess` files in your Apache configuration.

Also make sure to add all of your resources you are using (like your API and Keycloak servers) to the
`Content-Security-Policy` in your `{{name}}-app/public/.htaccess`, so the browser allows access to those sites.

You can also use this app directly from the [Unpkg CDN](https://unpkg.com/browse/@dbp-topics/{{name}}/)
for example like this: [dbp-{{name}}/index.html](https://gitlab.tugraz.at/dbp/{{app-path}}/-/tree/master/examples/dbp-{{name}}/index.html)

Note that you will need a Keycloak server along with a client id for the domain you are running this html on.

### Update app

If you want to update the dbp {{name}} App in the current folder you can call:

```bash
npx @digital-blueprint/cli update-app {{name}}
```

## Activities
This app has the following activities:
- {{list-of-activities}}

You can find the documentation of these activities in the [{{name}} activities documentation](https://gitlab.tugraz.at/dbp/{{app-path}}/-/tree/main/src).

## Adapt app

### Functionality
You can add multiple attributes to the `<dbp-{{name}}>` tag.

| attribute name | value | Link to description |
|----------------|-------| ------------|
| `provider-root` | Boolean | [appshell](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/app-shell#attributes) |
| `lang`         | String | [language-select](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/language-select#attributes) | 
| `entry-point-url` | String | [appshell](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/app-shell#attributes) |
| `keycloak-config` | Object | [appshell](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/app-shell#attributes) |
| `base-path` | String | [appshell](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/app-shell#attributes) |
| `src` | String | [appshell](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/app-shell#attributes) |
| `html-overrides` | String | [common](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/common#overriding-slots-in-nested-web-components) |
| `themes` | Array | [theme-switcher](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/theme-switcher#themes-attribute) |
| `darkModeThemeOverride` | String | [theme-switcher](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/theme-switcher#themes-attribute) |

{{app-based-attributes}}


#### Mandatory attributes

If you are not using the `provider-root` attribute to "terminate" all provider attributes
you need to manually add these attributes so that the topic will work properly:

```html
<dbp-{{name}}
    auth
    requested-login-status
    analytics-event
>
</dbp-{{name}}>
```


### Design
For frontend design customizations, such as logo, colors, font, favicon, and more, take a look at the [theming documentation](https://dbp-demo.tugraz.at/dev-guide/frontend/theming/).


## "dbp-{{name}}" Slots

These are common slots for the app-shell. You can find the documentation of these slot in the [app-shell documentation](https://gitlab.tugraz.at/dbp/web-components/toolkit/-/tree/master/packages/app-shell).
For the app specific slots take a look at the [{{name}} activities](https://gitlab.tugraz.at/dbp/{{app-path}}/-/tree/main/src).
