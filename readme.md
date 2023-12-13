# @ghom/task

Modern task runner for Node.js (gulp like)

## Install

```bash
npm install @ghom/task
```

## Usage

You can use TypeScript just by renaming the file to `tasks.ts`.

```js
import "@ghom/task"
import "@ghom/task-esbuild" // optional module for esbuild

function build() {
  return esbuild({
    entryPoints: ["src/index.ts"],
    outfile: "dist/index.js",
    bundle: true,
    platform: "node",
    target: "node14",
  })
}

function clean() {
  return del("dist");
}

const cleanAndBuild = steps(clean, build)

export {
  cleanAndBuild as build,
  cleanAndBuild as default,
  clean
}
```

And then run the task:

```bash
task # for default task
task build
task clean
```