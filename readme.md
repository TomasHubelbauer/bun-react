# Bun React

The minimal way to use React in Bun.

- Install dependencies first with `bun install`.
- Run the app with `bun start` (has live reload)
- Find the app running at http://localhost:3000

The way this works:

- Use `esm.sh` to serve React and React DOM transpiled to ESM (with their deps)
- Use `Bun.Transpiler` to transpile TypeScript to JavaScript and serve the code

Note that we can't use Bun's built-in implicit React transpilation because while
it will transpile a module before it is executed, it doesn't give us a way to
get the module's transpiled text to serve, so we need to transpile explicitly.

Note that we can't serve React and ReactDOM from `node_modules` because they
only ship CJS and UMD versions, not an ESM version, hence the use of `esm.sh`,
otherwise they could be served as `static` on the `Bun.Serve` alongside `fetch`.
