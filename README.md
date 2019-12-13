# Tailwind CSS with Rails 6 and Webpacker 

> This README is above all a cheatsheet made for me and by me. It may not suit your needs.

## [Installation](https://tailwindcss.com/docs/installation)

- Create a new Rails 6 project (optional):
```bash
rails new tailwindcss-app
```

- Inside, install Tailwind CSS framework:
```bash
yarn add tailwindcss
```

- In `app/javascript/`, create a `stylesheets/` directory and inside it, a `application.scss` file. In `application.scss`:

```scss
@import "~tailwindcss/base";
@import "~tailwindcss/components";
@import "~tailwindcss/utilities";
```

- In `app/javascript/packs/application.js`, import the scss file:

```js
import '../stylesheets/application.scss';
```

- In `app/views/layouts/application.html.erb`, replace "stylesheet_link_tag" by "stylesheet_pack_tag":

```erb
  <%= stylesheet_pack_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>
```

- In `config/webpacker.yml`, set default value of `extract_css:` key to `true`:

```yml
# Extract and emit a css file
  extract_css : true
```

- In `postcss.config.js`'s plugins array, require Tailwind CSS:

```js
module.exports = {
  plugins: [
    require('tailwindcss'),
    require('postcss-import'),
    require('postcss-flexbugs-fixes'),
    require('postcss-preset-env')({
      autoprefixer: {
        flexbox: 'no-2009'
      },
      stage: 3
    }),
  ]
};
```

- Run `rails server` and `bin/webpack-dev-server` commands in two different terminal windows.

## [Configuration](https://tailwindcss.com/docs/configuration/#creating-your-configuration-file)

- To generate a complete configuration file based Tailwind's default configuration, run:

```bash
# remove --full for a minimal config file only
npx tailwind init --full
```

And you are done! You may have to rerun `rails server` and/or `bin/webpack-dev-server` sometimes. 
