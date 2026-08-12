# namanjaswani27.github.io

Personal site and blog, served by GitHub Pages from the `main` branch at `/` (root).

## Layout

```
.
├── .nojekyll                       skip Jekyll; files are served exactly as committed
├── index.html                      landing page
├── 404.html
└── blog/
    ├── index.html                  post list
    └── attention-sinks/index.html  one post, one self-contained file
```

Each post is a single HTML file with its own CSS and JavaScript inline. No build step,
no dependencies to install, nothing to break at deploy time. KaTeX and the webfonts come
from CDNs with pinned versions and subresource integrity hashes.

## Adding a post

1. `mkdir blog/<slug>` and write `blog/<slug>/index.html`.
2. Add an entry to the list in `blog/index.html`.
3. Commit and push. Live within a minute or two.

## Local preview

Absolute paths like `/blog/` do not resolve over `file://`, so use a server:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploying

Remote:

```bash
git remote add origin git@github.com:namanjaswani27/namanjaswani27.github.io.git
```

Push to `main`. Pages is configured under Settings > Pages as
"Deploy from a branch", branch `main`, folder `/ (root)`.

## Keeping this separate from work accounts

Commit identity is set per repo rather than globally:

```bash
git config user.name  "Naman Jaswani"
git config user.email "personal@email.com"
git log -1 --format='%an %ae'      # verify before pushing
```

If your SSH agent holds a work key, GitHub will authenticate as that account. Pin the
right key with a host alias in `~/.ssh/config` and use it in the remote URL.
