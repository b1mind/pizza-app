<script>
  import { onMount } from 'svelte'
  import { gsap } from 'gsap'
  import { Draggable } from 'gsap/Draggable'

  gsap.registerPlugin(Draggable)

  console.dir(Draggable)

  let sizeButtons

  onMount(() => {
    Draggable.create(sizeButtons.children, {
      bounds: document.querySelector('[data-viewBox]'),
      onDragEnd: (e) => {
        console.log(e.target)
        console.log('drag end')
      },
    })
  })

  function resizePizza(e) {
    const size = e.target.dataset.size
    const resize = size / 10
    gsap.to('[data-pizza]', { duration: 1, scale: resize, transformOrigin: 'center' })
    console.log(sizeButtons.children)
  }
</script>

<svg data-viewBox fill="none" viewBox="0 0 360 640" xmlns="http://www.w3.org/2000/svg">
  <path fill="#C4C4C4" d="M0 0h360v60H0z" />
  <path fill="#C4C4C4" d="M0 455h360v185H0z" />

  <circle data-pizza cx="180" cy="251" r="75" fill="#C4C4C4" />

  <g class="sizes" bind:this={sizeButtons} on:click={resizePizza}>
    <circle data-size="12" cx="66" cy="552" r="30" />
    <circle data-size="15" cx="158.5" cy="551.5" r="40" />
    <circle data-size="20" cx="276" cy="547" r="50" />
  </g>

  <g class="size-text">
    <path
      fill="#000"
      d="M61.27 558h-1.09v-7.23l-2.18.8v-.98l3.1-1.16h.17V558zm8.77 0h-5.6v-.78l2.96-3.28c.44-.5.74-.9.9-1.2.17-.32.25-.64.25-.97 0-.45-.13-.81-.4-1.1a1.41 1.41 0 00-1.08-.43c-.54 0-.96.16-1.26.47-.3.3-.44.73-.44 1.27h-1.09c0-.78.26-1.42.76-1.9.5-.49 1.18-.73 2.03-.73.8 0 1.42.21 1.88.63.46.41.7.97.7 1.66 0 .84-.54 1.84-1.61 3l-2.29 2.48h4.29v.88zm1.4-6.13l-.61-.42c.36-.5.55-1.04.56-1.6V549h1.07v.76c0 .4-.1.78-.29 1.17-.19.39-.43.7-.73.94zm1.8 0l-.61-.42c.36-.5.55-1.04.56-1.6V549h1.07v.76c0 .4-.1.78-.3 1.17-.18.39-.42.7-.72.94z" />
    <path
      fill="#000"
      d="M153.27 556h-1.09v-7.23l-2.18.8v-.98l3.1-1.16h.17V556zm3.67-4.28l.44-4.25h4.37v1h-3.45l-.26 2.33c.42-.25.9-.37 1.43-.37.77 0 1.39.26 1.85.77a3 3 0 01.68 2.08c0 .88-.24 1.57-.71 2.08a2.6 2.6 0 01-1.99.76 2.7 2.7 0 01-1.84-.63 2.5 2.5 0 01-.82-1.73h1.03c.06.48.24.85.52 1.1.28.25.65.37 1.11.37.5 0 .9-.17 1.18-.51.3-.35.44-.82.44-1.43 0-.57-.16-1.02-.47-1.37-.3-.35-.72-.52-1.24-.52-.47 0-.84.1-1.11.31l-.29.24-.87-.23zm6.5-1.85l-.61-.42c.36-.5.55-1.04.56-1.6V547h1.07v.76c0 .4-.1.78-.29 1.17-.19.39-.43.7-.73.94zm1.8 0l-.61-.42c.36-.5.55-1.04.56-1.6V547h1.07v.76c0 .4-.1.78-.3 1.17-.18.39-.42.7-.72.94z" />
    <path
      fill="#000"
      d="M273.3 554h-5.6v-.78l2.96-3.28c.44-.5.74-.9.9-1.2.17-.32.26-.64.26-.97 0-.45-.14-.81-.4-1.1a1.41 1.41 0 00-1.09-.43c-.53 0-.95.16-1.26.47-.3.3-.44.73-.44 1.27h-1.08c0-.78.25-1.42.75-1.9.5-.49 1.19-.73 2.03-.73.8 0 1.42.21 1.88.63.47.41.7.97.7 1.66 0 .84-.54 1.84-1.6 3l-2.3 2.48h4.29v.88zm6.5-3.64c0 1.27-.22 2.21-.65 2.83-.44.62-1.11.93-2.04.93-.9 0-1.58-.3-2.02-.9-.44-.61-.66-1.51-.68-2.71v-1.45c0-1.25.22-2.18.65-2.8.44-.6 1.12-.9 2.04-.9.92 0 1.6.29 2.03.88.43.58.66 1.49.67 2.72v1.4zm-1.09-1.48c0-.92-.13-1.59-.38-2-.26-.43-.67-.64-1.23-.64-.55 0-.96.21-1.21.63a3.88 3.88 0 00-.4 1.93v1.73c0 .92.14 1.6.4 2.05.27.43.68.65 1.22.65.54 0 .94-.2 1.2-.62.25-.41.4-1.07.4-1.96v-1.77zm2.73-1l-.61-.43c.36-.5.55-1.04.56-1.6V545h1.07v.76c0 .4-.1.78-.29 1.17-.19.39-.43.7-.73.94zm1.8 0l-.61-.43c.36-.5.55-1.04.56-1.6V545h1.07v.76c0 .4-.1.78-.3 1.17-.18.39-.42.7-.72.94z" />
  </g>
</svg>

<style type="text/scss">
  svg {
    max-height: 100vh;
  }

  .sizes {
    fill: white;
    stroke: black;
    -webkit-tap-highlight-color: transparent;
    cursor: pointer;
  }

  [data-size] {
    &:active,
    &:hover {
      fill: red;
    }

    &:focus {
      fill: blue;
    }
  }
</style>
