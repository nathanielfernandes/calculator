<script>
  export let top;
  export let main;

  $: size = (main.length > 10 ? main.length - 10 : 0) * 1.25;
</script>

<div class="screen">
  <div class="top">ㅤ{top.replaceAll("*", "x").replaceAll("/", "÷")}</div>
  <div style="font-size: {40 - size}px" class="main">
    {main.replaceAll("*", "x").replaceAll("/", "÷")}
  </div>
</div>

<style>
  .screen {
    padding-top: 1.5rem;
    background-color: rgb(250, 250, 250);
    grid-area: screen;
    text-align: right;
  }

  .top {
    /* padding: 1rem 3rem; */
    margin: 1.5rem 1rem;

    font-size: 1.2rem;
    color: rgb(105, 105, 105);
    font-weight: 800;
  }

  .main {
    /* height: 100%; */
    align-items: center;
    margin: 1.5rem 1rem;
    padding: 0;
    color: rgb(47, 47, 47);
    /* font-size: 2rem; */
    font-weight: 800;
  }
</style>
