## Local Jekyll setup

This site uses Bundler with a repo-local install path so gems are installed into `vendor/bundle` rather than the system Ruby directories. That avoids permission errors with Homebrew Ruby.

For Ruby version management, this repo includes a `.ruby-version` file. Tools like `rbenv`, `asdf`, `mise`, and `chruby` can use that file to switch to the expected Ruby automatically when you enter the project directory.

Typical setup:

```sh
bundle install
bundle exec jekyll serve
```

If your current Ruby does not match `.ruby-version`, install that version with your preferred manager first.

## Project overview

This repository is a Jekyll static site. Source files are compiled into `_site/`, which is generated output and should not normally be edited directly.

The active site theme is the remote theme `ankitsultana/researcher`, configured in `_config.yml`. Local layouts and styles override parts of that theme where needed.

## Important directories

- `_config.yml`: site-wide metadata, navigation, plugins, collection definitions, and theme configuration. Changes here usually require restarting `bundle exec jekyll serve`.
- `_layouts/`: the main local HTML layout overrides. `default.html` is the root wrapper, `home.html` adds the hero section, `project.html` renders project metadata, and `page.html`/`post.html` are thin wrappers.
- `_journey/`: the main custom content collection. These files are rendered as standalone pages and currently drive the project/case-study content on the site.
- `_posts/`: dated blog posts.
- `index.md`, `about.md`, `journey.md`, `privacy.md`: top-level Markdown pages.
- `css/main.scss`: the main stylesheet entrypoint. It imports the theme styles and then applies local overrides.
- `assets/`: site images, fonts, web manifest files, and other static assets.
- `_site/`: generated build output. Treat as disposable.
- `vendor/bundle/`: local gem install path. Treat as environment output, not source.

## How the site is composed

Jekyll reads the front matter from each Markdown file, chooses the layout named in `layout:`, renders the Markdown to HTML, then wraps that content with the matching layout from `_layouts/`.

Typical flow:

- `index.md` uses `layout: home`, so it is rendered through `_layouts/home.html`, which itself uses `_layouts/default.html`.
- files in `_journey/` use `layout: project`, which adds the metadata panel from front matter fields like `status`, `repository`, `app_url`, `docs`, and `issues`.
- files in `_posts/` use the post layout and are published to dated permalink paths.

## Agent guidance

- Prefer editing source files only. Do not manually edit `_site/`.
- If a change affects site metadata, navigation, collections, or plugins, inspect `_config.yml` first.
- If a page looks visually wrong, inspect `_layouts/` and `css/main.scss` before assuming the remote theme is the problem.
- If a change touches a project page, check whether the content belongs in `_journey/` rather than a top-level page.
- If `_config.yml` changes, restart the Jekyll dev server before re-testing.
- Use `bundle exec jekyll build` as the main verification step for structural changes.

## Theme and legacy notes

The repository still contains some Minima-era files and dependencies, including the `minima` gem and some files in `_includes/` and `assets/` related to Minima social icons. The active rendering path is the `researcher` remote theme plus the local layouts in `_layouts/`.

Agents should treat those older Minima-related files as potentially legacy unless they are clearly referenced by the current layouts or config.

## Common change recipes

- Add or edit a project page: work in `_journey/`. Use `layout: project` and front matter fields such as `title`, `status`, `repository`, `app_url`, `docs`, and `issues` when needed.
- Change the homepage intro or welcome copy: edit `index.md`.
- Change the hero section on the homepage: inspect both `_layouts/home.html` and `css/main.scss`.
- Change navigation links or site-wide metadata: edit `_config.yml`, then restart `bundle exec jekyll serve`.
- Change the page wrapper, header, footer, or shared meta tags: edit `_layouts/default.html`.
- Change project metadata presentation: edit `_layouts/project.html` and, if styling is needed, `css/main.scss`.
- Add or edit a dated blog post: create or update a file in `_posts/` using the usual `YYYY-MM-DD-title.md` naming convention.
- Change site styling: start in `css/main.scss`. Treat the imported theme styles as upstream defaults and keep overrides local.
- Add images or fonts: place them in `assets/` and reference them with Jekyll/Liquid relative URL helpers where practical.
- Verify a structural or content change: run `bundle exec jekyll build`.

## Practical cautions

- `_config.yml` is not hot-reloaded by Jekyll; restart the dev server after changing it.
- `_site/` may look like the live site, but it is only generated output.
- `vendor/bundle/` may contain installed gems for more than one Ruby version over time; it is environment state, not source.
- The repo includes both the active remote theme path and some older Minima-related files. Check whether a file is actually referenced before editing it.

## Debugging visual issues

- Navigation links wrong or missing: check `_config.yml` first, then `_layouts/default.html`.
- Homepage banner, hero copy, or top-of-page layout looks wrong: check `_layouts/home.html`, `index.md`, and `css/main.scss`.
- A project page is missing metadata or links: check the page front matter in `_journey/` first, then `_layouts/project.html`.
- A page renders but has the wrong wrapper or structure: check the page's `layout:` front matter and the corresponding file in `_layouts/`.
- Styling changes are not visible: check `css/main.scss`, then confirm Jekyll rebuilt the site successfully.
- A config change seems to have no effect: restart `bundle exec jekyll serve`, because `_config.yml` is not hot-reloaded.
- A file appears correct in `_site/` but not in source: treat `_site/` as output and trace back to the Markdown, layout, or SCSS source file instead.