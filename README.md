# Casper Blue Theme

Casper is the default theme for [Ghost](http://github.com/tryghost/ghost/). I did not care for the Default Dark Grey Color scheme, so I changed the SCREEN.CSS and GLOBAL.CSS files to a Dark Blue Color scheme.


If you're just looking to download the latest release of Ghost with the default Casper Theme, head over to the [releases](https://github.com/TryGhost/Casper/releases) page.

&nbsp;

![screenshot-desktop](https://github.com/mcarter960/casperblue/blob/master/casperblue.jpg)

&nbsp;

# First time using a Ghost theme?

Ghost uses a simple templating language called [Handlebars](http://handlebarsjs.com/) for its themes.

This theme has lots of code comments to help explain what's going on just by reading the code. Once you feel comfortable with how everything works, we also have full [theme API documentation](https://ghost.org/docs/api/handlebars-themes/) which explains every possible Handlebars helper and template.

**The main files are:**

- `default.hbs` - The parent template file, which includes your global header/footer
- `index.hbs` - The main template to generate a list of posts, usually the home page
- `post.hbs` - The template used to render individual posts
- `page.hbs` - Used for individual pages
- `tag.hbs` - Used for tag archives, eg. "all posts tagged with `news`"
- `author.hbs` - Used for author archives, eg. "all posts written by Jamie"

One neat trick is that you can also create custom one-off templates by adding the slug of a page to a template file. For example:

- `page-about.hbs` - Custom template for an `/about/` page
- `tag-news.hbs` - Custom template for `/tag/news/` archive
- `author-ali.hbs` - Custom template for `/author/ali/` archive

## If you want SEARCH Feature You Need to Create an ACCOUNT: [SiteSearch360](https://www.sitesearch360.com/)

## ADDING or REMOVING SiteSearch360 - STEP #1

```
edit Line 17 in "index.hbs" just under class="site-description"

                <h2 class="site-description">{{@site.description}}</h2>
                {{!--START Site Search--}}
                <div>
                    <section role="search" data-ss360="true">
	                   <input type="search" id="searchBox">
                    </section>
                </div>
                {{!--END Site Search--}}
```

## ADDING or REMOVING SiteSearch360 - STEP #2  

```
// Change the URL in "default.hbs" in the "Site Search 360 script"

<!-- Start of Site Search 360 script (put right before the closing </body> tag) -->
<script type="text/javascript">
window.ss360Config = {
    style: {
        searchBox: {
            border: {
                color: "#FFFFFF",
                radius: "16px"
            },
            text: {
                color: "#FFFFFF",
                size: "16px"
            },
            background: {
                color: "#15202B"
            },
            padding: "10px",
            icon: {
                image: "magnifier",
                color: "#C2C2C2"
            }
        }
    },
    tracking: {
        providers: []
    },
    dataPoints: {
        exclude: [],
        single: []
    },
    siteId: "casperblue.devops10.com",  //CHANGE URL TO YOUR WEBSITE!!
    suggestions: {
        minChars: "4"
    },
    results: {
        num: "6",
        moreResultsPagingSize: "10",
        moreResultsButton: null
    },
    layout: {
        mobile: {
            type: "grid",
            showUrl: true,
            gridColsMd: 1
        },
        desktop: {
            type: "grid",
            showUrl: true,
            gridColsXl: 2,
            gridColsLg: 2
        },
        navigation: {
            position: "top"
        }
    },
    showErrors: false
};

var e=document.createElement("script");
e.type="module";
e.src="https://cdn.sitesearch360.com/sitesearch360-v12.mjs";
document.getElementsByTagName("body")[0].appendChild(e);

e=document.createElement("script");
e.type="text/javascript";
e.async=!0;
e.setAttribute("nomodule", "nomodule");
e.src="https://cdn.sitesearch360.com/sitesearch360-v12.min.js";
document.getElementsByTagName("body")[0].appendChild(e);
</script>
<!-- End of Site Search 360 script -->

```


# Development

Casper styles are compiled using Gulp/PostCSS to polyfill future CSS spec. 

You'll need [Node](https://nodejs.org/), [Yarn](https://yarnpkg.com/) and [Gulp](https://gulpjs.com) installed globally. 

INSTALL YARN

```bash
# install yarn
sudo curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt

sudo echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo

sudo apt update && sudo apt install yarn

yarn --version

sudo yarn set version berry
```

INSTALL GULP

```bash
# install gulp
sudo npm install gulp-cli -g

sudo npm install gulp -D

sudo npm install -g npm

```

After that, from the theme's root directory:

```bash
# run development server
yarn dev

```

Now you can edit `/assets/css/` files, which will be compiled to `/assets/built/` automatically.

The `zip` Gulp task packages the theme files into `dist/<theme-name>.zip`, which you can then upload to your site.

```bash
# create .zip file
yarn zip
```

# PostCSS Features Used

- Autoprefixer - Don't worry about writing browser prefixes of any kind, it's all done automatically with support for the latest 2 major versions of every browser.
- Variables - Simple pure CSS variables
- [Color Function](https://github.com/postcss/postcss-color-function)


# SVG Icons

Casper uses inline SVG icons, included via Handlebars partials. You can find all icons inside `/partials/icons`. To use an icon just include the name of the relevant file, eg. To include the SVG icon in `/partials/icons/rss.hbs` - use `{{> "icons/rss"}}`.

You can add your own SVG icons in the same manner.


# Copyright & License

Copyright (c) 2013-2020 Ghost Foundation - Released under the [MIT license](LICENSE).
