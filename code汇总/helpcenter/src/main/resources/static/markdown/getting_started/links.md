<h1 id="title1">Links</h1>

> **Summary:** When creating links, you can use standard HTML or Markdown formatting. However, you can also implement an automated approach to linking that makes linking much less error-prone (meaning less chances of broken links in your output) and requiring less effort.

<h2 id="title2">Create an external link</h2>

When linking to an external site, use Markdown formatting because it’s simplest:

```
[Google](http://google.com)
```

<h2 id="title3">Linking to internal pages</h2>

When linking to internal pages, you can manually link to the pages like this:

```
[Icons](mydoc_icons.html)
```

However, if you change the file name, you’ll have to update all of your links. It’s much easier to use Automated links, as described in the next section.

<h2 id="title4">Automated links</h2>

This method for automated links creates a master list of all links in a Markdown reference format based on entries in your sidebar table of contents.

With this Automated links method, make sure all your pages are referenced in a sidebar or topnav data file (inside _data > sidebars). If they’re not in a sidebar or top nav (such as links to headings on a page), list them in the `other.yml` file (which is in the _data/sidebars folder).

The *links.html* file (in _includes) will iterate through all your sidebars and create a list of reference-style markdown links based on the `url` properties in the sidebar items.

> **Note:** For the automated links method to work, each of your pages must have a `permalink`property in the frontmatter. The `permalink` property must match the file name. For example, if the file name is `somefile.html`, your permalink property would be `somefile.html`. See [Pages](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_pages.html) for more details.

To implement managed links:

1. In your *_config.yml* file, list each sidebar in the `sidebars` property — including the *other.yml* file too:

   ```
   sidebars:
   - home_sidebar
   - mydoc_sidebar
   - product1_sidebar
   - product2_sidebar
   - other
   ```

2. At the bottom of each topic where you plan to include links, include the *links.html* file:

   ```
   {% include links.html %}
   ```

3. To link to a topic, use reference-style Markdown links, with the referent using the file name (without the file extension). For example:

   ```
   See the [Icon][mydoc_icons] file.
   ```

   Here’s the result:

   See the [Icon](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_icons.html) file.

   If the link doesn’t render, check to make sure the page is correctly listed in the sidebar.

<h2 id="title5">Automated links to headings on pages</h2>

If you’re linking to the specific heading from another page, first give the heading an ID:

```
## Some heading {#someheading}
```

Then add a property into the *other.yml* file in your _data/sidebars folder:

```
    - title: Some link bookmark
      url: /mydoc_pages.html#someIdTag
```

And reference it like this:

```
This is [Some link][mydoc_pages.html#someIdTag].
```

**Result:**

This is [Some link](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_pages.html#someIdTag).

It’s a little strange having the `.html#` in a reference like this, but it works.