<script>
  import Product from "./Product.svelte";
  import Cart from "./Cart.svelte";

  let cartItems = [];

  const addToCart = (e) => (cartItems = [...cartItems, e.detail]);

  const removeFromCart = (e) => {
    cartItems = cartItems.filter((_, index) => index != e.detail);
  };
</script>

<main>
  <Product on:addtocart={addToCart} />
  {#if cartItems.length}
    <Cart {cartItems} on:removefromcart={removeFromCart} />
  {/if}
</main>
