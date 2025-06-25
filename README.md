# Nx-Monorepo 
[Nx-Monorepo](https://nx.dev/getting-started/tutorials/angular-monorepo-tutorial)
Build system, optimized for monorepos, with plugins for popular frameworks and tools and advanced CI capabilities including caching and distribution.

> Monorepo is an architectural solution to this problem that is used by some of the largest tech companies in the world, such as Google and Facebook, as well as being used by some of the most popular open source libraries such as Babel, React Jest and countless more.

## What is a Monorepo?
A monorepo or a mono repository is a single repository that stores all of the code and assets for all of your projects, rather than each product or library being stored in its own source control. This allows you to develop, test and deploy all of your projects and their dependencies simultaneously with everything using the latest iteration of everything else.
A monorepo is a single repository that contains the source code for multiple projects. These projects can range from different types of applications to libraries, services, and more. By keeping all related code in one place, a monorepo provides easier code sharing and management.
For example, imagine that you're developing a product and you have built a small library with helpful functionality used by your product. Now you want to add a new feature to your product, which requires you to update your library. Using a monorepo you can make all the required changes at the same time and test the changes instantly, allowing you to catch potential bugs or issues early. When the modifications are complete, you can then release your product and your library simultaneously. This pattern of developing software is used by some of the largest tech companies in the world, such as Google and Facebook, although at their scale, it requires them to have developed some specialized sets of tools to manage it all. But most open source projects would almost certainly never have to worry about that. And there is a selection of amazing free tools and libraries out there for helping to manage everything.
![Monrepo](https://media.geeksforgeeks.org/wp-content/uploads/20240814182951/article.png)
In this example, the /web-app and /mobile-app directories represent different projects within the same monorepo. The /shared directory contains shared components and utilities that both apps can use. This setup allows you to update shared code in one place and ensure that all projects have access to the latest version.

### Tools for managing a Monorepo
Some of the most popular and Effective tools for managing a monorepo:

   -   Turborepo: Turborepo is a high-performance build system for JavaScript and TypeScript monorepos. It automatically determines the dependency graph and only rebuilds what’s necessary, making it ideal for large codebases.
   -   Lerna: It is one of the most well-known tools for managing JavaScript monorepos.It helps in managing multiple packages within a single repository, including versioning, dependency management, and publishing.
   -   Nx: It is a smart, extensible build framework that helps manage monorepos. Originally created for Angular projects, It has expanded to support many frameworks and languages.
   -   Bazel: It is used to support large codebases across multiple languages. Originally developed by Google, Bazel is known for its performance and ability to handle large, complex builds efficiently. It's language-agnostic, making it suitable for diverse technology stacks.

## Advantages of Nx Monorepo
   - Default Nx follows the single version policy meaning that all of the packages are just installed and referenced at the root level and then all of the other applications and libraries withing the workspace point to those references. For long run, it gives a lot of benifits because you never run into issues where you have two different libraies you want to share & reuse in one application but both of them use or require different angular versions.
  - You don't necessarily need to go to full route. You can also have a setup where every appliction every library have their own package.json & node_modules. You would use something like npm, yarn, pnpm workspaces to actually make sure that the linking amoung those libraies happens such that you actually gets some benefits from a monorepo setup.
  - Nx has a built-in caching system [Nx Cache](https://nx.dev/features/cache-task-results) that speeds up the execution time of many common tasks by reusing previous results and only building, testing, or linting code affected by recent changes. By default, Nx caches task results locally. If you are running a task that was previously executed, Nx restores the results of running that task from the cache instead of executing it again. However, as Nx states: The biggest benefit of caching comes from using remote caching in CI, where you can share the cache between different runs.
  -  
  -  

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

## Nx Cache for improving build times
Rebuilding and retesting the same code repeatedly is costly. Nx offers a sophisticated and battle-tested computation caching system that ensures code is never rebuilt twice. This:
   - drastically speeds up your task execution times while developing locally and even more in CI
   - saves you money on CI/CD costs by reducing the number of tasks that need to be executed

Nx restores both the terminal output and the files created from running the task (e.g., your build or dist directory).
[Use Remote Caching (Nx Replay)](https://nx.dev/ci/features/remote-cache)
[How Nx Cache works](https://nx.dev/concepts/how-caching-works)


