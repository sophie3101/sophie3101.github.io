# sophie3101.github.io

This repository is used to build a personal website using Jekyll

Jekyll Folder Structure Overview:

Jekyll recognizes specific folder and file names as part of its default structure: 
```
my-website/
├── _config.yml          # Site settings
├── _posts/              # Blog posts (Markdown files)
├── _layouts/            # Page templates (HTML with Liquid)
├── _includes/           # Reusable snippets
├── _data/               # YAML/JSON data files
├── _site/               # Compiled site (auto-generated)
├── assets/              # Images, CSS, JS
├── index.md             # Home page content
└── about.md             # Sample page
```

To preview the site locally with live reloading:

`bundle exec jekyll serve --livereload`