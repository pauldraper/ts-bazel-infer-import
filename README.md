# TS Bazel Infer Import

## ts

```sh
yarn install
node_modules/.bin/tsc -p example
```

target/example/example.d.ts is

```ts
export declare const result: import("rxjs").Observable<number>;
```

## Bazel

```sh
bazel build example:ts
```

Output is

```
ERROR: /home/paul/dev/pauldraper/ts-bazel-infer-import/example/BUILD.bazel:3:1: Compiling TypeScript (devmode) //example:ts failed (Exit 1)
example/example.ts:1:20 - error TS2307: Cannot find module 'rxjs'.

1 import { of } from 'rxjs';
```
