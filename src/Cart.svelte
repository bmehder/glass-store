<script>
  import { fly } from "svelte/transition";
  import { flip } from "svelte/animate";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  const i11n = new Intl.NumberFormat("nl-NL");

  export let cartItems = [];
  let subtotal = 0;
  let total;

  const removeFromCart = (i) => {
    cartItems = cartItems.filter((_, index) => index != i);
    dispatch("removefromcart", i);
  };

  $: {
    subtotal = 0;
    cartItems.forEach((item) => (subtotal += item.price));
    cartItems.length > 1 ? (total = subtotal * 0.9) : (total = subtotal);
    total;
  }
</script>

<section transition:fly={{ x: 400 }}>
  <article>
    {#each cartItems as item, i (item.title + i)}
      <p animate:flip>
        <span>{item.title}</span>
        <span>{item.price} €</span>
        <button on:click={(e) => removeFromCart(i)}>X</button>
      </p>
    {/each}
  </article>
  <div>
    Total:
    {i11n.format(total.toFixed(2))}
    €<br />
    {#if cartItems.length > 1}
      <small><em>(10% Quantity Discount Applied)</em></small>
    {/if}
  </div>
  <button class="submit">Checkout</button>
</section>

<style>
  section {
    position: fixed;
    width: 280px;
    top: 1%;
    right: 1%;
    padding: 2em 1em;
    background: rgba(255, 255, 255, 0.05);
    box-shadow: 1px 1px 5px rgba(255, 255, 255, 0.5) inset,
      10px 10px 20px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(20px);
    text-shadow: 0 0 4px rgba(0, 0, 0, 0.5);
    color: white;
    overflow-y: scroll;
  }
  article {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 80%;
    max-width: 400px;
    margin: auto;
    border-bottom: 1px solid #eee;
  }
  p {
    display: grid;
    grid-template-columns: 8fr 4fr 2fr;
    grid-gap: 0.5em;
    align-items: center;
    font-weight: bold;
  }
  p button {
    background: none;
    border: none;
    outline: none;
    margin: 0;
    color: #228b22;
    font-weight: bold;
    font-size: 1.25em;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    cursor: pointer;
  }
  div {
    margin-top: 2em;
    font-weight: bold;
    text-align: center;
    line-height: 1.5em;
  }
  .submit {
    display: block;
    width: 80%;
    margin: 20px auto;
    padding: 20px;
    background: #228b22;
    color: white;
    font-weight: bold;
    border: none;
    outline: none;
    transition: all 300ms;
    border-radius: 10px;
    box-shadow: 1px 1px 5px rgba(255, 255, 255, 0.5) inset,
      10px 10px 20px rgba(0, 0, 0, 0.1);
    cursor: pointer;
  }
</style>
