# sveltejs

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
