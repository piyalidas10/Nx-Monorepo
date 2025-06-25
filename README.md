# Nx-Monorepo 
[Nx-Monorepo](https://nx.dev/getting-started/tutorials/angular-monorepo-tutorial)
Build system, optimized for monorepos, with plugins for popular frameworks and tools and advanced CI capabilities including caching and distribution.

> Monorepo is an architectural solution to this problem that is used by some of the largest tech companies in the world, such as Google and Facebook, as well as being used by some of the most popular open source libraries such as Babel, React Jest and countless more.

## What is a Monorepo?
A monorepo or a mono repository is a single repository that stores all of the code and assets for all of your projects, rather than each product or library being stored in its own source control. This allows you to develop, test and deploy all of your projects and their dependencies simultaneously with everything using the latest iteration of everything else.
For example, imagine that you're developing a product and you have built a small library with helpful functionality used by your product. Now you want to add a new feature to your product, which requires you to update your library. Using a monorepo you can make all the required changes at the same time and test the changes instantly, allowing you to catch potential bugs or issues early. When the modifications are complete, you can then release your product and your library simultaneously. This pattern of developing software is used by some of the largest tech companies in the world, such as Google and Facebook, although at their scale, it requires them to have developed some specialized
sets of tools to manage it all. But most open source projects would almost certainly never have to worry about that. And there is a selection of amazing free tools and libraries out there for helping to manage everything.

When working in a monorepo One of the great features is that you can import and use your own libraries just like you would any other NPM package.

## Advantages of Nx Monorepo
   ✔ Default Nx follows the single version policy meaning that all of the packages are just installed and referenced at the root level and then all of the other applications and libraries withing the workspace point to those references. For long run, it gives a lot of benifits because you never run into issues where you have two different libraies you want to share & reuse in one application but both of them use or require different angular versions.
  ✔ You don't necessarily need to go to full route. You can also have a setup where every appliction every library have their own package.json & node_modules. You would use something like npm, yarn, pnpm workspaces to actually make sure that the linking amoung those libraies happens such that you actually gets some benefits from a monorepo setup.
  ✔ Nx has a built-in caching system [Nx Cache](https://nx.dev/features/cache-task-results) that speeds up the execution time of many common tasks by reusing previous results and only building, testing, or linting code affected by recent changes. By default, Nx caches task results locally. If you are running a task that was previously executed, Nx restores the results of running that task from the cache instead of executing it again. However, as Nx states: The biggest benefit of caching comes from using remote caching in CI, where you can share the cache between different runs.
  ✔ 
  ✔ 

## Nx Monorepo Steup
```
~❯ npx create-nx-workspace@latest angular-monorepo --preset=angular-monorepo

NX   Let's create a new workspace [https://nx.dev/getting-started/intro]

✔ Application name · angular-monorepo
✔ Which bundler would you like to use? · esbuild
✔ Default stylesheet format · scss
✔ Do you want to enable Server-Side Rendering (SSR) and Static Site Generation (SSG/Prerendering)? · No
✔ Which unit test runner would you like to use? · jest
✔ Test runner to use for end to end (E2E) tests · playwright
✔ Which CI provider would you like to use? · github
```

![Setup 1](https://github.com/piyalidas10/Nx-Monorepo/blob/bbb3423ddbd1adaeae2ecddcf5a467805e734223/basic_examples/images/Nx_Monorepo_Setup_1.png)
![Setup 2](https://github.com/piyalidas10/Nx-Monorepo/blob/bbb3423ddbd1adaeae2ecddcf5a467805e734223/basic_examples/images/Nx_Monorepo_Setup_2.png)

## Nx Monorepo Folder Structure
```
└─ angular-monorepo
   ├─ .github
   │  ├─ workflows
   │  │  ├─ ci.yml
   ├─ .nx
   │  ├─ cache
   │  │  ├─ ci.yml
   │  │  ├─ cloud
   │  │  |  ├─ verify.lock
   │  │  |  ├─ 2506.22.2
   │  │  |  |  ├─ lib
   │  │  |  |  |  ├─ daemon
   │  │  |  |  |  |  ├─ process-run-end.js
   │  │  |  |  |  ├─ heartbeat
   │  │  |  |  |  |  ├─ heartbeat-process.js
   │  │  |  |  ├─ static
   │  │  |  |  |  ├─ login-end.html
   │  │  |  |  |  ├─ login-start.html
   │  │  |  |  ├─ index.js
   │  │  |  |  ├─ package.json
   │  ├─ workspace-data
   │  │  ├─ eslint-2654242865465226088.hash
   │  │  ├─ file-map.json
   │  │  ├─ lockfile.hash
   │  │  ├─ nx_files.nxt
   │  │  ├─ parsed-lock-file.json
   │  │  ├─ playwright-5186013267177752385.hash
   │  │  ├─ eslint-2654242865465226088.hash
   │  │  ├─ project-graph.json
   │  │  ├─ project-graph.lock
   │  │  ├─ source-maps.json
   ├─ apps
   │  ├─ angular-monorepo
   │  │  ├─ public
   │  │  │  ├─ favicon.ico
   │  │  ├─ src
   │  │  │  ├─ app
   │  │  │  │  ├─ app.scss
   │  │  │  │  ├─ app.html
   │  │  │  │  ├─ app.spec.ts
   │  │  │  │  ├─ app.ts
   │  │  │  │  ├─ app.config.ts
   │  │  │  │  ├─ app.routes.ts
   │  │  │  │  └─ nx-welcome.ts
   │  │  │  ├─ assets
   │  │  │  ├─ index.html
   │  │  │  ├─ main.ts
   │  │  │  ├─ styles.scss
   │  │  │  └─ test-setup.ts
   │  │  ├─ eslint.config.mjs
   │  │  ├─ jest.config.ts
   │  │  ├─ project.json
   │  │  ├─ tsconfig.app.json
   │  │  ├─ tsconfig.json
   │  │  └─ tsconfig.spec.json
   │  ├─ angular-monorepo-e2e
   │  │  ├─ src
   │  │  │  ├─example.spec.ts
   │  │  ├─ eslint.config.mjs
   │  │  ├─ playwright.config.ts
   │  │  ├─ project.json
   │  │  └─ tsconfig.json
   ├─ nx.json
   ├─ tsconfig.base.json
   ├─ node_modules
   ├─ .prettierrc
   ├─ eslint.config.mjs
   ├─ jest.config.ts
   ├─ jest.preset.js
   ├─ README.md
   ├─ package-lock.json
   └─ package.json
```
One way to structure an Nx monorepo is to place application projects in the apps folder and library projects in the libs folder. Applications are encouraged to be as light-weight as possible so that more code is pushed into libraries and can be reused in other projects. This folder structure is just a suggestion and can be modified to suit your organization's needs.
The nx.json file contains configuration settings for Nx itself and global default settings that individual projects inherit. 

## @nx/angular
[@nx/angular intro](https://nx.dev/technologies/angular/introduction)

## Migrating an Angular CLI project to Nx
[Nx migration from Angular Cli](https://nx.dev/technologies/angular/migration/angular)

