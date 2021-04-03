<script>
  export let topping = 'ham'
  export let width = '100%'
  let useTopping = `./assets/toppings.svg#${topping}`
</script>

<svg
  fill="none"
  viewBox="0 0 50 50"
  xmlns="http://www.w3.org/2000/svg"
  {width}
  data-topping={topping}>
  <use href={useTopping} />
</svg>
