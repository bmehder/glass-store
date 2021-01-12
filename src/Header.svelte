<header>
  <h1>
    <slot />
  </h1>
</header>

<style>
  header {
    padding: 5px;
    background: rgba(255, 255, 255, 0.05);
    box-shadow: 1px 0px 5px rgba(255, 255, 255, 0.5) inset,
      10px 10px 20px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(20px);
    text-shadow: 0 0 4px rgba(0, 0, 0, 0.5);
    color: white;
    text-align: center;
  }
</style>
