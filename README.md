# dev-npm-package-react-typescript-boilerplate

It is a boilerplate for starting developing react library to be published to npm.

It setups 
- minimum building environment (React and TypeScript)
- a demo page to be published as a GitHub Pages
- a GitHub Action to publish your library to npm
- several scripts to help developing

# How to use

## prepare local worktree

1. clone this repository
1. `git remote set-url origin [your-repository]`
1. edit package.json
		- "name" of the npm package you are going to publish
		- "author"
		- "repository"
 1. you can do `git add` and `git commit` as usual

## develop your library

1. rename or replace `src/ModuleFile.ts` with your library file(s)
1. edit `index.js` and `index.d.ts` as if your library files are all in `dist` folder.
1. you can do `git add` and `git commit` as usual


__NOTE: you must start a commit message by "perf:", "feat:" or "fix:" at least one of the commits so that the auto-publishing action can decide next version number.__
more detail; see a documentation of [semantic-release](https://github.com/semantic-release/semantic-release)

related scripts
```
# build sources in `src` into `dist` folder
yarn run build
```

## develop demo page

1. create your demo page in `demo/src/components/App.tsx`
1. you can `git add` and `git commit` as usual

If you don't want to publish source code of demo page, you can ignore `demo` folder by .gitignore.

related scripts
```
# build demo page into `demo/dist` folder
# it also copies `demo/dist` into `docs` for GitHub Pages
yarn run build:demo

# build library and start running local server to host demo page
yarn run dev
```


## get npm access token

1. if not yet, create npm user account via [npm](https://www.npmjs.com/)
1. create new token via `Settings -> Auth Tokens`
1. copy the token to clipboard

## setup remote repository

1. if not yet, create a git repository in [GitHub](https://github.com/)

### to publish to npm
1. go to `Settings -> Secrets`
1. create new Secret by
	- name: NPM_TOKEN
	- value: [your npm token]

to publish GitHub Pages
1. go to `Settings => Options -> GitHub Pages`
1. Select branch as you like  
__note: you cannot set this before pushing a file into this repository__
1. Select Folder `/docs`

## Release!

1. commit your updates  
__Again confirm at least one of your new commit message starts with "perf:", "feat:" or "fix:" otherwise no new version will be released__
1. just `git push` and the new version will be published to npm automatically by GitHub Actions