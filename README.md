<!-- AUTOMATION BADGES -->

[![CodeQL](https://github.com/webceyhan/vite-bmi-app/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/webceyhan/vite-bmi-app/actions/workflows/codeql-analysis.yml)
[![Build and Deploy](https://github.com/webceyhan/vite-bmi-app/actions/workflows/build-and-deploy.yml/badge.svg)](https://github.com/webceyhan/vite-bmi-app/actions/workflows/build-and-deploy.yml)

<!-- HEADER ///////////////////////////////////////////////////////////// -->

# Vite BMI/BMR Calculator Application

This is a simple BMI & BMR calculator application which asks you to fill in 
your gender, age, weight and height to calculate your BMI and BMR results accordingly.

The application is built with Vite + Vue 3 + Bootstrap.
There is no need for backend server as it only works in single-play mode against the computer.

[View Demo](https://ceyhan.io/vite-bmi-app/) |
[Report Issue](https://github.com/webceyhan/vite-bmi-app/issues) |
[Request Feature](https://github.com/webceyhan/vite-bmi-app/pulls) |
[@webceyhan](https://twitter.com/webceyhan)

<br>
<!-- REQUIREMENTS /////////////////////////////////////////////////////// -->

## Requirements

You need to install the [Node.js](https://nodejs.dev/) and `npm` package manager first.

> Recommended IDE:
> [VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)

<br>
<!-- INSTALLATION //////////////////////////////////////////////////////// -->

## Installation

1. Clone the repository.
    ```sh
    git clone https://github.com/webceyhan/vite-bmi-app.git
    ```
2. Get inside the cloned project folder.
    ```sh
    cd vite-bmi-app
    ```
3. Install NPM packages.
    ```sh
    npm install
    ```

<br>
<!-- USAGE /////////////////////////////////////////////////////////////// -->

## Usage

You can use following commands to do various task with the project.

```sh
npm run dev             # start development server
npm run build           # build for production
npm run preview         # preview built application
```

> Take a look at the other scripts in [`package.json`](./package.json)

<br>

<!-- DEVELOPMENT ///////////////////////////////////////////////////////// -->

## Development

Start the development server to watch changes while you code.

```sh
npm run dev
```

<br>
<!-- BUILDING //////////////////////////////////////////////////////////// -->

## Building

Build the application for production.

```sh
npm run build
```

You can also preview the application after building it.

```sh
npm run preview
```

<br>
<!-- DEPLOYMENT ////////////////////////////////////////////////////////// -->

## Deployment (GitHub Pages)

A GitHub Action will automatically deploy the project to GitHub Pages on every push.

The workflow will build the project using npm and output the result to the `dist` folder which will be then pushed to the `gh-pages` branch.

> See the details in [.github/workflows/build-and-deploy.yml](./.github/workflows/build-and-deploy.yml)

<br>
<!-- REFERENCES ////////////////////////////////////////////////////////// -->

## References

-   [Node.js](https://nodejs.dev/)
-   [Vite](https://vitejs.dev/)
-   [Vue.js](https://vuejs.org/)
-   [Bootstrap](https://getbootstrap.com)
-   [GitHub Actions](https://docs.github.com/en/actions)
    -   [GitHub Pages](https://pages.github.com/)
    -   [github-pages-deploy-action](https://github.com/JamesIves/)
