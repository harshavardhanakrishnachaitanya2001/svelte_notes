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
 
 
