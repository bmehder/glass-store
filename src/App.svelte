<script>
  import { cartItems } from "./cartItems";
  import Header from "./Header.svelte";
  import Product from "./Product.svelte";
  import Cart from "./Cart.svelte";
</script>

<Header>LOGO</Header>
<main>
  <Product />
  {#if $cartItems.length}
    <Cart />
  {/if}
</main>
