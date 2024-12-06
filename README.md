# reveal.js Presentation Site Example

This is an example repo for hosting both a private repo for your own version
control, along with a public GitHub Pages site to provide to students. The
site is rendered using Quarto via RStudio, and outputs a landing page with
presentations using reveal.js

## Git Subtree

In order for this to work with 2 repos, publishing only the `site/` contents
to the public gh-pages repo, you have to use git submodules. This is non-trivial,
and requires a bit of additional learning and effort. The alternative is to simply
not have a private repo, and whate everything in a public repo, building your 
site out of the `site/` folder.

### Steps

```bash
quarto render
git commit -am 'your commit to private repo'
git subtree split --prefix=site -b gh-pages
git remote add public https://github.com/your-username/public-site-repo.git
git push public gh-pages:main
```

Then after any future updates:

```bash
git commit -am 'your commit to private repo'
git push origin main
git subtree push --prefix=site public main
```