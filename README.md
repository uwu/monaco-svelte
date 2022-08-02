# Monaco for Svelte

This is a component that wraps Microsoft's great Monaco editor for Svelte.

All props are reactive.

The `value` prop is a store, not a simple value.
If it is writable, it will be written to on change.
If it is only readable, it will not be.

See below for fairly self explanatory usage. Should have TS defs if you have svelte ts setup.

You may use any theme from [*here*](https://github.com/brijeshb42/monaco-themes/tree/master/themes) by name.

You can use monaco from an npm package by passing to `noCDN`.
This will only do anything on the first render of any `<Monaco>`,
and will apply to all later uses of the component.

If you do not do this, monaco will just be loaded from jsDelivr.

```svelte
<script>
  import Monaco from "monaco-svelte";
  import * as monaco from "monaco-editor"
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
  noCDN={monaco}
/>

<pre><code>{$value}</code></pre>
```
