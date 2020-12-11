# sveltejs

## Sveltejs is compailer and not a framework

### To create a svelte application
```svelte
npx degit sveltejs/template nameOfProject
```

sveltejs is mostly html, but with some differences.

### Styling svelte application
```svelte
Done between <style><style> tags
```
### Including JS in svelte
```svelte
<script>
  //JS code
</script>
```

### Using variables in svelte
```svelte
<script>
  let variableName="data";
</script>
<p>The data is, {variableName}</p>
```
### Importing new components into app.svelte
```svelte
<script>
  import Component from 'Component.svelte'
</script>
```

### Using html styles like bold, underline, etc.. inside JS code
```svelte
<script>
  let variable="some new <htmlTag>text</htmlTag>"
</script>
<p>{@html variable}</p>
```

### Adding functionality to a button
```svelte
<button on:click={clickHandlerFunction}>...</button>
```

#### alternate way:
```svelte
<script>
  $:variableName=action;
 </script>
 ```
 The $: can also be used in front of if blocks
 
 ### Arrays in svelte
 After performing operations on arrays, it must be reassigned to itself.
 
 #### Simpler way:
 To perform the above operation in more easy way, spread operator(...) is used.
 Ex:
 ```svelte
 <script>
   function addNumber() {
    numbers = [...numbers, numbers.length + 1];
  }
</script>
 ```

### Props in svelte
Props in svelte are defined using the 'export' keyword
```svelte
// Inside a component
<script>
  export answer;
</script>
```
This property (prop for short), is used inside another component which imports the component

```svelte
<ImportedComponent property=value/>
```
Default values can be provided to the svelte props which are used when no prop and value are given for that component when used in another component

```svelte
//Iniside ImportedComponent
<script>
  export let answer=<value>
</script>
```
The value can be a string or number or a boolean.

### Properties used in object
When n number of props are used inside an object, while calling, use that package name insted of assigning values to the props explicitly
Example:
```svelte
<script>
	import Info from './Info.svelte';

	const pkg = {
		name: 'svelte',
		version: 3,
		speed: 'blazing',
		website: 'https://svelte.dev'
	};
</script>

<Info {...pkg}/>
```

### Conditional statements
```svellte
{#if <condition>}
	statements
{:else}
	statements
{/if}
```

### Multiple conditions
```svelte
{#if <condition>}
	statements
{:else if <condition>}
	statements
{:else}
	statements
{/if}
```

### Looping in an array
```svelte
{#each <arrayName> as <singleItemName>}
	statement which operate on {<singleItemName.data>}
{/each}
```
Example:
```svelte
<script>
	let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];
</script>

<h1>The Famous Cats of YouTube</h1>

<ul>
	{#each cats as cat}
		<li><a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
			{cat.name}
		</a></li>
	{/each}
</ul>
```
#### Array with index
```svelte

<script>
	let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];
</script>

<h1>The Famous Cats of YouTube</h1>

<ul>
	{#each cats as cat, i}
		<li><a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
			{i+1}:{cat.name}
		</a></li>
	{/each}
</ul>

'i' stands for index of the array elements. Therefore, i+1 means the value 1 if array element has the index value of 0
``` 

### Asynchronous programming with sveltejs
First an async function is defined in b/w the script tags and using the await keyword, fetching and convertion are done
```svelte
<!--Outside the script tags, at the end of the file-->
{#await <variableThatReceivesTheReturnValueOfPromise>}
Code that will execute before displaying fetched data
{:then variableWhichStoresThePromise}
//code
{:catch error}
exception handling code
{/await}
