<script>
  import { products } from "./data.js";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
</script>

<section>
  {#each products as product, i}
    <article>
      <figure>
        <span>{product.price} €</span>
        <img src={product.image} alt={product.title} />
      </figure>
      <div>
        <h4>{product.title}</h4>
        <button on:click={(e) => dispatch('addtocart', product)}>Add to Cart</button>
      </div>
    </article>
  {/each}
</section>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  section {
    display: flex;
    justify-content: space-evenly;
    max-width: 960px;
    margin: 40px auto;
    padding: 80px 40px;
    background: rgba(255, 255, 255, 0.05);
    box-shadow: 1px 1px 5px rgba(255, 255, 255, 0.5) inset,
      10px 10px 20px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(20px);
    text-shadow: 0 0 4px rgba(0, 0, 0, 0.5);
    color: white;
  }
  article {
    position: relative;
    /* background: white; */
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.24);
    backdrop-filter: blur(20px);
    border-radius: 20px;
  }
  figure {
    width: 220px;
    height: 220px;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
  }
  img {
    object-fit: cover;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
  }
  span {
    position: absolute;
    top: 2%;
    right: 4%;
    width: 60px;
    height: 50px;
    background: #228b22;
    color: white;
    text-align: center;
    line-height: 50px;
    font-weight: bold;
    border-radius: 2px;
    border-top-right-radius: 5px;
    border-bottom-left-radius: 25px;
    box-shadow: 1px 1px 5px rgba(255, 255, 255, 0.5) inset,
      10px 10px 20px rgba(0, 0, 0, 0.1);
  }
  div {
    padding: 20px;
    text-align: center;
  }
  h4 {
    font-size: 1.5em;
    line-height: 1.5em;
  }
  button {
    display: block;
    width: 100%;
    margin: 20px 0;
    padding: 15px 20px;
    background: #228b22;
    font-weight: bold;
    color: white;
    border: none;
    outline: none;
    box-shadow: 1px 1px 5px rgba(255, 255, 255, 0.5) inset,
      10px 10px 20px rgba(0, 0, 0, 0.1);
    border-radius: 5px;
    cursor: pointer;
  }
</style>
