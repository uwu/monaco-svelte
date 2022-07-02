# Monaco for Svelte

This is a component that wraps Microsoft's great Monaco editor for Svelte.

All props are reactive except for `otherCfg`, which is only assigned at first render.

The `value` prop is a store, not a simple value.
If it is writable, it will be written to on change.
If it is only readable, it will not be.

See below for fairly self explanatory usage. Should have TS defs if you have svelte ts setup.

You may use any theme from [*here*](https://github.com/brijeshb42/monaco-themes/tree/master/themes) by name.

```svelte
<script>
  // TODO: figure out if npm module exports can be svelte files?
  import Monaco from "monaco-svelte";
  import { writable } from "svelte/store";

  let value = writable(""); // Writable<string> | Readable<string>
</script>

<!-- value and lang are required, but not others -->
<Monaco
  {value}
  lang="javascript"
  theme="Monokai"
  readonly={false}
  height="30rem"
  width="20rem"
  otherCfg={{}}
/>
```
