# svelte-typewriter

> A simple and reusable scramble effect

[DEMO](https://berkinakkaya.github.io/svelte-scramble)

## Installation

```bash
# yarn
yarn add -D svelte-scramble

# npm
npm i -D svelte-scramble
```

## Usage

You need to import the Svelte component, and wrap your elements with the `<Typewriter>` component

```svelte
<script>
	import Scramble from 'svelte-scramble';
</script>

<Scramble>
	<h1>THIS TEXT WILL BE SCRAMBLED</h1>
</Scramble>
```
