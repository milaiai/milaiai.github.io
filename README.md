# Requirement
- [Hugo](https://gohugo.io/)
- npm

```sh
npm install -g postcss-cli
npm install -g autoprefixer
```

- themei: https://themes.gohugo.io/blonde/
```sh
$ git submodule add https://github.com/opera7133/Blonde.git themes/Blonde
$ cd themes/Blonde
$ npm install
```
Update the theme 
```sh
$ git submodule update --remote --merge
```

# Usage
## Run

```sh
hugo server --renderToDisk
```
