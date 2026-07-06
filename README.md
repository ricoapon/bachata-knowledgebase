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
