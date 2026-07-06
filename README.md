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
