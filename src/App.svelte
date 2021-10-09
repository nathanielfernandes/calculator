<script>
  import Calculator from "./components/Calculator.svelte";
</script>

<main>
  <h1>this is a calculator</h1>
  <div class="calc">
    <Calculator />
  </div>
  <p>
    made with 4 braincells and svelte.<br />
    <a href="https://github.com/nathanielfernandes/calculator">source</a>
  </p>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  .calc {
    display: flex;
    width: 100%;
    justify-content: center;
    text-align: center;
  }

  h1 {
    color: #ff3e00;
    font-size: 4em;
    font-weight: 500;
    -webkit-user-select: none;
    -moz-user-select: none;
  }

  p {
    -webkit-user-select: none;
    -moz-user-select: none;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
