---
title: Formatter
description: Learn about the Formatter tool that allows you to find and fix mistakes in the code style.
last_updated: Feb 14, 2021
template: concept-topic-template
originalLink: https://documentation.spryker.com/v6/docs/formatter
originalArticleId: 776ba318-4023-458b-b79f-c0a769d20c4e
redirect_from:
  - /v6/docs/formatter
  - /v6/docs/en/formatter
---

*Formatter* allows you to find and fix code style mistakes and keep the code more readable.

To format files, [Prettier](https://prettier.io/) is used.

## Installation
For details on how to install Formatter for your project, see [Formatter integration guide](/docs/scos/dev/migration-and-integration/202009.0/development-tools/formatter-integration-guide.html).

## Using formatter

To execute the formatter, do the following:

1. Install the Node modules:
```bash
npm ci
```
2. Execute the formatter in:
* validation mode:
```bash
npm run formatter
```
* fix mode
```bash
npm run formatter:fix
```
## File types

The default file types for formatting are:

*     *.scss
*     *.css
*     *.less
*     *.js
*     *.ts
*     *.json
*     *.html

To change the list of file extensions, adjust `/frontend/settings.js`:

```
formatter: [
    `**/*.(scss|css|less|js|ts|json|html)`,
],
```

{% info_block infoBox %}

Twig is **not validated** by Prettier. The existing [twig plugin](https://github.com/trivago/prettier-plugin-twig-melody) can't work with widgets and attributes.

{% endinfo_block %}
## Formatter config

The config for Prettier resides in the[ @spryker/frontend-config.prettier](https://www.npmjs.com/package/@spryker/frontend-config.prettier) module.

To redefine the path for the config file, adjust `/frontend/libs/formatter.js`  and use other [options](https://prettier.io/docs/en/options.html) for Prettier:

```
const configPath = 'node_modules/@spryker/frontend-config.prettier/.prettierrc.json';
```
The Prettier formatter uses the ignore file `/.prettierignore` that includes directories and files where the formatter shouldn’t be executed.

## CI checks and pre-commit hook

The Formatter is integrated into:
* Pre-commit hooks.
The function that executes formatter before the commit resides in `/.githook`

```
- GitHook\Command\FileCommand\PreCommit\FrontendFormatterCommand
```
* Travis.
Command to run the formatter is integrated into `.travis.yml`

```
- node ./frontend/libs/formatter
```

{% info_block warningBox "Important" %}

If you commit without the pre-commit hooks, you should run the formatter manually to avoid issues with Travis.

{% endinfo_block %}

{% info_block infoBox %}

Pre-commit hooks weren’t integrated into [B2B](https://github.com/spryker-shop/b2b-demo-shop) and [B2C](https://github.com/spryker-shop/b2c-demo-shop) demo shops, only in the [Shop Suite](https://github.com/spryker-shop/suite).

{% endinfo_block %}


