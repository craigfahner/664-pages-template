# Python Project Showcase Template

This repository is a template for publishing a Python project as a website using **GitHub Pages**. The page you're reading right now is the site's home page — it's just the `README.md` file from the repo, turned into a web page.

Everything here is plain Markdown. GitHub pages renders markdown as HTML so it is viewable in the browser.

## Pages in This Site

This home page links to two other Markdown files in the repo. Click them to see linking in action:

- [About the Project](about.md) — an example page describing a project
- [How to Run It](how-to-run.md) — an example page with setup instructions

Each of those pages links back here and to each other. Open them on GitHub.com *and* on the published site — the same links work in both places.

## How It Works

- GitHub Pages runs a tool called Jekyll on your repo automatically every time you push. It converts each `.md` file into an `.html` page.
- **`README.md` is the home page.** If there's no `index.md` in the repo, GitHub Pages uses `README.md` as the landing page.
- **Linking between pages is just a normal Markdown link.** Write `[About the Project](about.md)` and GitHub Pages rewrites it to `about.html` when it builds the site. Because the link points to the `.md` file, it also works when browsing the repo on GitHub.com.
- **No front matter required.** You don't need the `---` block some Jekyll tutorials show at the top of each file. Each page's first `# Heading` is used as its title.
- **`_config.yml` controls site-wide settings.** In this repo it only sets the site title, description, and theme. Try changing the `theme:` line to another [supported theme](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll/) such as `jekyll-theme-cayman`.

## Publishing Your Site on GitHub.com

1. **Make your own copy.** Click **Use this template → Create a new repository** at the top of this repo on GitHub.com (or fork it). Give the repository a name; it will become part of your site's URL.
2. **Turn on GitHub Pages.** In your new repo, go to **Settings → Pages**. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose the `main` branch and the `/ (root)` folder, and click **Save**.
3. **Wait for the build.** Open the **Actions** tab to watch the "pages build and deployment" job. It usually takes a minute or two.
4. **Visit your site.** It will be at:

   ```
   https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
   ```

   The link also appears at the top of **Settings → Pages** once the site is live.
5. **Edit and push.** Any change pushed to `main`, including edits made directly on GitHub.com with the pencil icon, rebuilds the site automatically.

## Adding a New Page

1. Create a new file ending in `.md`, for example `gallery.md`.
2. Start it with a heading: `# Gallery`.
3. Link to it from this README: `[Gallery](gallery.md)`.
4. Commit and push. The new page appears on the site after the next build.

## Troubleshooting

- **404 on the site?** Make sure Pages is enabled (step 2 above) and the build in the **Actions** tab finished with a green check.
- **A link is broken?** Check the filename's spelling and capitalization. `About.md` and `about.md` are different files.
- **Changes aren't showing?** Wait for the build to finish, then hard-refresh your browser (Shift + Reload).
