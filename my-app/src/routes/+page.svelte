<script>
    import pell from '$lib/pell';
    import { onMount } from 'svelte';
let editor
    onMount(() => {
        // Initialize pell on an HTMLElement
pell.init({
  // <HTMLElement>, required
  element: editor,

  // <Function>, required
  // Use the output html, triggered by element's `oninput` event
  onChange: html => console.log(html),

  // <string>, optional, default = 'div'
  // Instructs the editor which element to inject via the return key
  defaultParagraphSeparator: 'div',

  // <boolean>, optional, default = false
  // Outputs <span style="font-weight: bold;"></span> instead of <b></b>
  styleWithCSS: false,

  // <Array[string | Object]>, string if overwriting, object if customizing/creating
  // action.name<string> (only required if overwriting)
  // action.icon<string> (optional if overwriting, required if custom action)
  // action.title<string> (optional)
  // action.result<Function> (required)
  // Specify the actions you specifically want (in order)
  actions: [
    'bold',
    {
      name: 'custom',
      icon: 'C',
      title: 'Custom Action',
      result: () => console.log('Do something!')
    },
    'underline'
  ],

  // classes<Array[string]> (optional)
  // Choose your custom class names
  classes: {
    actionbar: 'pell-actionbar',
    button: 'pell-button',
    content: 'pell-content',
    selected: 'pell-button-selected'
  }
})
    });
</script>

<h1>Peel.js testing</h1>

<div bind:this={editor} id="some-id"></div>