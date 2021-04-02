<script>
  export let viewBox = '0 0 50 50'
  export let topping = 'ham'
</script>

<svg
  data-topping={topping}
  class="oderBox"
  data-orderBox
  {viewBox}
  width="50"
  height="50"
  fill="none"
  xmlns="http://www.w3.org/2000/svg">
  <rect width="50" height="50" fill="pink" />
  <rect x="100" width="50" height="50" fill="brown" />
  <rect x="200" width="50" height="50" fill="green" />
  <rect x="300" width="50" height="50" fill="plum" />
  <rect x="400" width="50" height="50" fill="skyblue" />
  <rect y="100" width="50" height="50" fill="blue" />
  <rect y="200" width="50" height="50" fill="teal" />
  <rect y="300" width="50" height="50" fill="red" />
  <rect y="400" width="50" height="50" fill="purple" />
</svg>

<style type="text/scss">
  .oderBox {
    width: 50px;
    height: 50px;
  }
</style>
