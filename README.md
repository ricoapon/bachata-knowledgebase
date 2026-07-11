# Quartz v4

This is a fork of [Quartz](https://github.com/jackyzha0/quartz) with my own changes.

Current version: 4.5.2.

## How to update

To update this repository, execute the following steps:

1. Run `npx quartz update` to get the commits from the `v4` branch.
2. Resolve any conflicts if needed.
3. Push the changes.

## My changes

### Allow start parameter for YouTube embedding

I had to make code changes to get the `start=X` to work. 

See `quartz/plugins/transformers/ofm.ts` or commit `90bea3d650919ef61ba0007226c52b48c8bb1337`.

### Do not show number of items in folder

Showing the number of items in a folder can be disabled using `showFolderCount`. However, there was no way to actually pass this value, so I updated the default value to `false`.

See `quartz/components/pages/FolderContent.tsx` or commit `97e89c95054cc3165df0d23abe8cd8d069e1f658`.

### Fix backlinks to aliases

Quartz shows all the backlinks for each page. However, when linking to a page using its alias, it does not show a backlink. This has been fixed.

See `quartz/components/Backlinks.tsx` or commit `ac4abf49b7081b58d5c163343370bec88c6bc1b5`.

### Always use the same layout

I want my own layout, so I made the changes I needed to get my own layout.

See `quartz.layout.ts` and `quartz/styles/custom.scss` or commit `3ecea621f5c6fb761cf43a0c69e41e7226d7166b`

### Use custom workflow to deploy to GitHub Pages

The Quartz repository had many files in the `.github` directory, like issue templates and GitHub Actions. I don't need these, so I have deleted the `.github` directory.

My own repositories will always be published to GitHub Pages using GitHub Actions, so I have added a `.github/workflows/deploy-to-gh-pages.yaml` to support this.

See commit `86102740305a5848a505f068e71ae2d0fc426bc3`.

### Use this repository as upstream

Quartz handles upgrading the repository. However, it sets the original repository as upstream. I changed it to use this repository instead.

See `quartz/cli/handlers.js` or commit `68a4567ab7c29152bdb5e914a1b2097213e990ed`

## Forking

To use my own Quartz repository, execute the following steps:

1. Clone this repository using `git clone https://github.com/ricoapon/quartz.git`.
2. Rename the branch to `main` using `git branch main`.
3. Update `pageTitle`, `baseUrl` and `colors` in `quartz.config.ts`.
4. Remove all the `README.md` text until the `TODO` chapter below.
5. Fill in the repository name and the repository description.
6. Push changes using `git push origin main`.

# TODO: Your Repository Name

TODO: Your Repository Description

## Development

To run this project locally, run:

```
npx quartz build --serve
```

Open the page served on port 8080, not 3001.

Note that YouTube embedding will show an 153 error when running locally. It will work when deployed to GitHub Pages.

## Technical

It uses Quartz. The repository was initialized using [my own template](https://github.com/ricoapon/quartz) (specifically, v4).

To upgrade the repository, executing the following steps:

1. Run `npx quartz update`.
2. Resolve any conflicts if needed.
3. Push the changes.

# Markdown specifics

There are a few situations that need more details to work as expected. If some standard way of working needs to be used, place it here.

## YouTube links

Embedding a YouTube video is possible, but there are strict requirements. To ensure it works, always embed it as follows:

```
![YouTube Video](https://youtu.be/6OW1gkSE2d8?start=120)
```

The name ("YouTube Video") is irrelevant and won't be shown. This can be replaced with a descriptive name that is useful for myself. The `start=X` is optional and can be used to start a video at a specific timestamp. Make sure to use this exact URL, because a regex is used to determine YouTube video's. It will not work if the URL doesn't match the regex. To stay consistent, always use this format.


## Using index.md

When I have a page that contains many variants, I will use a directory name `X`, with files `index.md`, `X Variant 1.md`, etc. When linking to this main page, you want `[[X]]` to work. However, `[[X]]` only works if the exact filename is also `X.md`. Therefore, we need to add an alias to the `index.md` as follows:

```
---
title: X
aliases:
  - X
---
```

If this alias is forgotten, `[[X]]` will not work.
