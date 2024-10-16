# USABLE
Repository to track news and resources from the USABLE initiative; learn more at https://usable.tools

## Editing content
Content contained in the `content` directory as markdown files. Each file should have a `.md` extension. With [Hugo](https://gohugo.io/) installed, you can add content through the command line: `hugo new content/[SECTION]/[FILENAME].md`.

**Paths** will be constructed using the section's directory within `content` and the name given to the markdown file. So a markdown file in `content/events/my-awesome-event.md` will have this URL `https://usable.tools/events/my-awesome-event`, so he last fragment of the path will match the filename but without the `.md` extension.

**Drafts** are set to true by default. If content doesn't appear after adding the markdown file inside the `content` directory, check to make sure that draft is set to false with `draft: false`.

**Blog** content is published within the `content/blog` directory. There is an example unpublished blog content at `content/blog/blog-example.md`.

**Events** are published within the `content/events` directory.
Note: the `eventdate` font matter field should be filled in so the sort on the events page will display most recent events on top. There is an unpublished example event content `content/events/event-example.md`.

**Personas** are published within the `content/personas` directory. There is an example unpublished personal content `content/personas/persona-example.md`.

**Pages** can be published within the top level of the `content` directory. For example the about page `https://usable.tools/about` is published at `content/about.md`.

**Images and Files**
To add an image to content, first place it in the `static/images` directory. Hugo will copy any files in `static` to the published site. For example an image path would be `images/[FILENAME].png`.

To add a PDF to content, place it in the `static/pdfs` directory. For example a path to a PDF should be `pdfs/[FILENAME].pdf`.

Anything added to the `static` directory will be available to the published site.

## Publishing content / Deploying changes

This website uses Git workflows. This means that, any time a file changes within the website, GitHub will automatically launch an instance of [Hugo](https://gohugo.io) to build the website. Hugo turns all of the files in this repository into a static website. This website is then hosted on [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages).

If you have the appropriate permissions in the repository and would like to check the status of the Git workflows, just go to the 'Actions' tab in the upper left corner of your GitHub menu. For more information on GitHub Actions, check out [GitHub's documentation](https://docs.github.com/en/actions/about-github-actions/understanding-github-actions) on the topic.

It's also possible to test out the website locally; particularly useful if you want to try out new things without uploading the changing to your repository or syncing them to GitHub Pages. In order to do so, [install Hugo](https://gohugo.io/getting-started/quick-start/) on your machine, open the folder with the repository in it. Within that folder:

* To build the static files run `hugo`.
* To preview the website locally run `hugo server`.


## Styles and stylesheets

This website uses [SASS](https://sass-lang.com/guide/) to manage its stylesheets. In order to modify the styling of the site, just update `assets/scss/style.scss`. Afterwards, you will need to run the `sass` command in order to turn the .scss files into the css files which the site's styles are based on. **Do note:** we currently do not have a GitHub workflow that uses `sass` to build the css files when the site is being built via GitHub Pages. This means that, whenever we change the scss files, we will run `sass` locally on our machines in order to compile them into css files, then commit those new files to the webpage's repository.

This webpage uses the [Bootstrap](https://getbootstrap.com/) library (version 4).

To compile the css, first install SASS by [following those directions](https://sass-lang.com/install/). Once this is installed, open the folder containing the webpage in your terminal and run `sass assets/scss/style.scss static/css/style.css --no-source-map` (we pass the `no-source-map` parameter when getting the site ready for production, since the source map is just used for debugging).

At time of writing, we used SASS version 1.79.4 compiled with dart2js 3.5.3 (you can check which version you use by running `sass --version`).


## Updating Home Page
**Home page carousel** content is published within the `content/front_carousel` directory. The full text of this content is displayed on the front page. HTML can be included in these, such as the orange USABLE text within the the h2 tag with: `<span class="orange">USABLE</span>`.

The `link_path` field is required for the slide to be displayed. If the value for this is empty than the entire slide will not be visible on the front page.

The `link_text` field is optional. If not defined, it defaults to "Read more."

The `weight` property controls the order of front page items.

If you would like to unpublish any front carousel content, the draft property can be set to false with `draft: false`.

This content type doesn't require the `title` value. If `title` is defined in `front_carousel` content, it will not be visible anywhere.

**Intro** on front page can be edited in `data/intro.json`. It has a title and description.

**Personas** block on front page can be edited in `data/personas.json`.

## Configuration

**Configuration** is stored in `config.toml`. This file contains various Hugo settings as well as site wide values such as the name of the site. The contact information, social media links, twitter card data and OG data are also defined in this file.

**Main menu:** Menu items can be added in the configuration file `config.toml`.

**baseURL**
The base baseURL in `config.toml` will need to be changed to `baseURL = "http://usable.tools/"` before switching to this domain. The trailing `/` is required for the site to render correctly.