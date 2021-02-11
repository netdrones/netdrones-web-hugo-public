# SF Stroke Center Website

[![Netlify Status](https://api.netlify.com/api/v1/badges/f5d9e59b-cd9e-434a-9820-9a31e78432bd/deploy-status)](https://app.netlify.com/sites/sfstroke/deploys)

We are deployed on Netlify using Forester CMS for content with and use
Themefisher and the new Hugo module support that pulls from their repo. This
uses the basic template from [@richtong](https://github.com/richtong)

To snapshot those modules, you can use
[Hugo](https://gohugo.io/commands/hugo_mod_vendor/) to do this with a single
command which adds all the modules currently running and puts them into
[_vendor](_vendor);

```bash
hugo mod vendor
```

## Installation into netlify

The steps are:

1. Fork this repo into a the new organization
2. Run `make netlify` to make sure variables are set. This requires the @richtong
   fabulous [bin](https://github.com/richtong/bin)
   [lib](https://github.com/richtong/lib) helper repos

If you do not use these then run, this repo uses Git LFS so run:

```bash
brew install netlify-cli
# Normally for free accounts, you have a separate login per site
netlify login
# links this to netlify
netlify link
netlify env:set GIT_LFS_ENABLED true
``````

## Installation into netlify

The steps are:

1. Fork this repo into a the new organization
2. Run `make netlify` to make sure variables are set. This requires the @richtong
   fabulous [bin](https://github.com/richtong/bin)
   [lib](https://github.com/richtong/lib) helper repos

If you do not use these then run, this repo uses Git LFS so run:

```bash
brew install netlify-cli
# Normally for free accounts, you have a separate login per site
netlify login
# links this to netlify
netlify link
netlify env:set GIT_LFS_ENABLED true
``````

## How to use this template

There are two different layouts:

1. The first layout takes posts that are of type *featured* and puts them in
   the top as a set of images. The *category* is used as the subtitle and then
   the *title* is all you see. the content appears when you click.
   The *post* type goes in the traditional blog format below.
2. The second layout reformats this to the traditional blog format. You get
   text based on the [config.yaml](config.yaml) parameters so for instance the
   bio goes on the front as does the author. You need to edit the layout to
   change this.

If you want to change the layouts then:

1. Run `hugo mod vendor` to get the latest template files from the other themes
2. Browse into [_vendor](_vendor) and look for the layout, for instance to
   modify the main page layout, look in
   [_vendor/github.com/themefisher/parsa-hugo/layout](_vendor/github.com/themefisher/parsa-hugo/layout)
   and copy the appropriate layout into [layout](layout) and this should be
   used instead of the default in themese.

## Managing menu items

The v2 of this links to top level pages so [content/about.md](content/about.md)
is the about and in [config.yaml](config.yaml) sets this in the `menu` entries

The other one is the [content/contact.md](content/contact.md) which is that
page.

If you want other parent pages, just create them and then point to them in
config.yaml

## Managing blog entries

These appear in the top of the home page. So you can use this for various
features and product sections. Just change the entries in
[content/blog](content/blog) and you should be able to change the products and
features as needed.

## Updating to latest theme

The theme is pinned in [go.mod](go.mod) and this is set in
[config.yaml](config.yaml) in the module.imports.path location
to update the modules, run as [Hugo Modules](https://gohugo.io/hugo-modules/use-modules/)
explains:

```shell
hugo mod get -u ./...
hugo mod vendor
```

There are certain pages that are overridden by the theme, you will have to do a
manual merge to get these correct. So compare the files in [layouts](layouts)
with the theme files in (_vendor/github.com)(_vendor/github.com) and you can
pick up the changes.

The main ones are in:

- [layouts/index.html](layouts/index.html) where we delete
the world `Blog`

## Based on  Hugo Parsa Forestry Starter

[Hugo Parsa Theme developed by
Themefischer](https://github.com/themefisher/parsa-hugo) for Forestry CMS.

Import to Forestry in one single click!

[![Import to Forestry](https://assets.forestry.io/import-to-forestryK.svg)](https://app.forestry.io/quick-start?repo=forestryio/hugo-parsa-forestry&engine=hugo&version=0.74.3)

## Prerequisites

- Hugo > 0.62.2 (tested with 0.74.3)

## Content Management

This project has been pre-configured to work with
[Forestry](https://forestry.io), just import your repository ✨. \ Any changes
you make will be committed back to the repo, and deployed if you're using
Netlify.

## Customization

You can customize the theme through the [`config.toml`
file](https://github.com/forestryio/hugo-parsa-forestry/blob/master/config.toml).
Those values are accessible from within Forestry.

## Deployment and hosting with Netlify

Import your site in [Netlify](https://netlify.com)

1. Create a new site in Netlify and import your repository.
2. Set the build command to: `hugo --gc --minify`
3. Set the publish directory to: `public`
4. Set `HUGO_VERSION` to `0.74.3`

That's it, now your site gets deployed automatically on `git push` or when
saving documents from Forestry.

## Development

```bash
# clone your repository
# cd in the project directory
cd hugo-parsa-forestry

# Start local dev server
hugo server

## Adding Images

The images are currently kept in the Theme core repo.

The images here are actually imported from the theme. To override and add your
own images, you need to create a image directory and then it will replicate
what was in the theme image and put them there for you to edit.
```

For more information, see [official Hugo documentation](https://gohugo.io/getting-started/).
