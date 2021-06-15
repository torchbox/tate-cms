# [Tate Sprintnotes notepad](https://torchbox.github.io/tate-cms/)

The Tate CMS project’s sprint notes, administered as a [Jekyll](https://jekyllrb.com/) site hosted in [GitHub Pages](https://pages.github.com/).

## Site structure

- `_config.yml` is the Jekyll configuration.
- `index.md` is the contents of the site’s homepage.
- Files in `_posts/` are listed on the homepage from newest to oldest.
- Files in `images/` can be used as images in posts.

## Publishing notes

You can use the [editor on GitHub](https://github.com/torchbox/tate-cms/edit/gh-pages/index.md) to maintain and preview the content of the site in [Markdown](https://guides.github.com/features/mastering-markdown/) files.

When creating a new post,

- The post’s filename needs to start with a date in the YYYY-MM-DD format: https://github.com/torchbox/tate-cms/blob/main/_posts/2021-04-21-ep1-inception-and-discovery.md
- The post title should be wrapped in quotes, for example: `title: "This week’s sprint"`

The [live site](https://torchbox.github.io/tate-cms/) is automatically updated whenever making changes in GitHub.

### Adding images

1. In GitHub, upload the image file in the `images/` folder.
2. Reference the image with the correct path and file name from your post: `![Image alt text](/tate-cms/images/my-file-name.png)`.

Or with a link over the image:

```markdown
[![Image alt text](/tate-cms/images/my-file-name.png)](https://www.example.com/)
```
