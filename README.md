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
Compiling TypeScript (devmode) //example:ts failed (Exit 1)
example/example.ts:3:14 - error TS2742: The inferred type of 'result' cannot be named without a reference to '../external/npm/node_modules/rxjs'. This is likely not portable. A type annotation is necessary.

3 export const result = of(1);
```
