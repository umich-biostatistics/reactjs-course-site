# reveal.js Presentation Site Example

This is an example repo for hosting both a private repo for your own version 
control, along with a public GitHub Pages site to provide to students. The site 
is rendered using Quarto via RStudio, and outputs a landing page with 
presentations using reveal.js

## Git Subtree

In order for this to work with 2 repos, publishing only the `site/` contents to 
the public gh-pages repo, you have to use `git subtree`. This is non-trivial, 
and requires a bit of additional learning and effort. An alternative is to 
simply not have a private repo, and push everything in a public repo, building 
your site out of the `site/` folder, or using `.gitignore` to only version 
control/push your `site/` directory.

### Steps

``` bash
quarto render
git commit -am 'your helpful commit message here'

# set the remote for your public GitHub Pages repo, giving it a remote name of
# 'public' in this example
git remote add public https://github.com/your-username/public-site-repo.git

# initial push to the public repo, where the prefix flag only publishes items in the site folder
git subtree push --prefix=site public main
```

> [!NOTE] 
> Make sure to update your public repo settings to enable GitHub Pages! 
> [Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

Then after any future updates:

``` bash
git commit -am 'your helpful commit message here'

# push to main, private repo
git push

# push to github pages repo using the 'public' remote's main branch
# -P is equivalent to --prefix= just easier to type
git subtree push -P site public main
```
