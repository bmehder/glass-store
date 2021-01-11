<script>
  import { cartItems } from "./cartItems";
  import Product from "./Product.svelte";
  import Cart from "./Cart.svelte";
</script>

<main>
  <Product />
  {#if $cartItems.length}
    <Cart />
  {/if}
</main>
