# Installation Guide
## Overview
There are already several [guides](https://tailwindcss.com/docs/installation#integration-guides) on the tailwindcss webpage including **next.js, Vue 3, Laravel, Nuxt.js, React App** and **Gatsby**. 
So I decided to make an installation guide for Tailwindcss with Angular and PostCSS. As well as we use these technologies in our project. This guide is based on the [Angular 10 with Tailwind CSS](https://notiz.dev/blog/angular-10-with-tailwindcss#setup) manual.

## Angular with Tailwindcss and PostCSS
### Requirements
You should already have installed the following before starting the setup:

 - Angular with Node.js ( [installation guide](https://angular.io/guide/setup-local) )

### Setup
1. Create an Angular project and open the CLI

2. Start by adding dependencies for Tailwind, Postcss and ngx-build-plus for angular :
`npm i -D tailwindcss autoprefixer postcss postcss-import postcss-loader`
3. Create manually a **webpack.config.js** in your root folder to configure Postcss with Tailwind.
4. In the webpack.config.js put the following code :

    `module.exports = {
    module: {
    rules: [
    {
	test: /\.css$/,
	loader: 'postcss-loader',
	options: {
	postcssOptions: {
	ident: 'postcss',
	syntax: 'postcss',
	plugins: [
	require('postcss-import'),
	require('tailwindcss'),
	require('autoprefixer'),
	],
}, }, }, ], }, };`

6. Open the **angular.json** file in your root folder (it already exists) to apply the extra webpack config to generate Tailwind styles during `ng build`, `ng serve` and `ng test`.


![angular.json](https://raw.githubusercontent.com/eicul04/tailwindcss/main/angular-json.png)

> Image source: https://notiz.dev/blog/angular-10-with-tailwindcss#setup

7. Create the Tailwind configuration file :

   ` npx tailwindcss init`
  
   => this should put a file called tailwind.config.js to the root folder.
8. To include Tailwind to the CSS stylesheets, open the styles.css in the src folder and paste the following code in there :
 ` @import "tailwindcss/base";`
 `@import "tailwindcss/components";`
 `@import "tailwindcss/utilities";`



Now you can start using the Tailwind utility classes - Have fun! 🎉

