# Nx-Monorepo [https://nx.dev/getting-started/tutorials/angular-monorepo-tutorial]
Build system, optimized for monorepos, with plugins for popular frameworks and tools and advanced CI capabilities including caching and distribution.

Monorepo is an architectural solution to this problem that is used by some of the largest tech companies in the world, such as Google and Facebook, as well as being used by some of the most popular open source libraries such as Babel, React Jest and countless more.

## What is a Monorepo?
A monorepo or a mono repository is a single repository that stores all of the code and assets for all of your projects, rather than each product or library being stored in its own source control. This allows you to develop, test and deploy all of your projects and their dependencies simultaneously with everything using the latest iteration of everything else.
For example, imagine that you're developing a product and you have built a small library with helpful functionality used by your product. Now you want to add a new feature to your product, which requires you to update your library. Using a monorepo you can make all the required changes at the same time and test the changes instantly, allowing you to catch potential bugs or issues early. When the modifications are complete, you can then release your product and your library simultaneously. This pattern of developing software is used by some of the largest tech companies in the world, such as Google and Facebook, although at their scale, it requires them to have developed some specialized
sets of tools to manage it all. But most open source projects would almost certainly never have to worry about that. And there is a selection of amazing free tools and libraries out there for helping to manage everything.

When working in a monorepo One of the great features is that you can import and use your own libraries just like you would any other NPM package.
