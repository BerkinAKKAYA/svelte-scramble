<script>
	import { onMount } from 'svelte';

	const INTERVAL = 30;
	const SCRAMBLE_COUNT = 100;

	let node;
	let elements = [];

	function RandomString (word, foundIndexes) {
		const arrayOfLetters = [...Array(word.length).keys()];

		return arrayOfLetters.map(i => {
			const found = (foundIndexes.includes(i) || word[i] == " ");
			const letter = String.fromCharCode(65 + Math.round(Math.random() * 50));
			return found ? word[i] : letter;
		}).join("")
	}
	
	function GetElements (parentElement) {
		const hasSingleTextNode = el => el.childNodes.length === 1 && el.childNodes[0].nodeType === 3;
		const treeWalker = document.createTreeWalker(parentElement, NodeFilter.SHOW_ELEMENT);
		let currentNode = treeWalker.nextNode();

		while (currentNode) {
			const text = currentNode.textContent.split('');
			hasSingleTextNode(currentNode) && elements.push({ currentNode, text });
			currentNode = treeWalker.nextNode();
		}

		if (hasSingleTextNode(node)) {
			const text = node.textContent.split('');
			node.textContent = '';
			const childNode = document.createElement('p');
			node.appendChild(childNode);
			elements.push({ currentNode: childNode, text });
		}
	}

	function Scramble() {
		GetElements(node);

		const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));

		elements.forEach(async element => {
			const { currentNode, text } = element;
			const foundIndexes = [];
			let i = 0;

			do {
				currentNode.textContent = RandomString(currentNode.textContent, foundIndexes);

				for (let i=0; i<text.length; i++) {
					const current = currentNode.textContent;
					if (!foundIndexes.includes(i) && text[i] === current[i]) {
						foundIndexes.push(i);
					}
				}

				i += 1;
				await sleep(INTERVAL);
			} while (currentNode.textContent != text.join("") && i < SCRAMBLE_COUNT)

			currentNode.textContent = text.join("");
		})
	}

	onMount(Scramble)
</script>

<div bind:this={node}>
	<slot />
</div>
