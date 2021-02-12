# svelte-typewriter

> A simple and reusable typewriter effect for your Svelte applications

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

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
