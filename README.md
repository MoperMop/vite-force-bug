# Vite Bug With `--force`

## Steps to Reproduce

1. Download repo and run `pnpm i` and `pnpm run build`.
2. Navigate to `playground/force-bug` and run `pnpm run dev`.
  - This will run `vite` without any options.
  - `server.force` should be `undefined`.
  - `optimizeDeps.force` should be `false`.
3. Run `pnpm run dev1`.
  - This will run `vite --force`.
  - `server.force` should be `true`, _this is the bug_.
  - `optimizeDeps.force` should be `true`.
4. Run `pnpm run dev2`.
  - This will run `vite -c force.config.ts`, which configures
    `optimizeDeps.force` to `true`.
  - `server.force` should be `undefined`.
  - `optimizeDeps.force` should be `true`.
