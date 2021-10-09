<script>
  import Button from "./Button.svelte";
  import Display from "./Display.svelte";

  let buttons = [
    { label: "AC", position: "ac", value: "reset" },
    { label: "⌫", position: "del", value: "delete" },
    { label: "%", position: "precent", value: "%" },
    { label: "÷", position: "divide", value: "/" },
    { label: "x", position: "x", value: "*" },
    { label: "-", position: "minus", value: "-" },
    { label: "+", position: "plus", value: "+" },
    { label: ".", position: "dot", value: "." },
    { label: "=", position: "equal", value: "=" },
  ];

  let base_nums = [7, 8, 9, 4, 5, 6, 1, 2, 3, 0];
  buttons = buttons.concat(
    base_nums.map((e) => {
      return {
        label: e,
        position: `n${e}`,
        value: e,
      };
    })
  );

  let past_expression = "";
  let expression = "";
  function click(event) {
    const { value } = event.detail;
    if (expression.includes("Error") || expression.includes("Infinity")) {
      expression = past_expression;
    }
    switch (value) {
      case "reset":
        expression = "";
        past_expression = "";
        break;
      case "delete":
        expression = expression.slice(0, -1);
        break;
      case "=":
        if (past_expression !== expression) {
          past_expression = new String(expression);
          if (expression === "9+10") {
            expression = "21";
            past_expression = "you stupid";
            break;
          }
          try {
            let result = new String(eval(expression));
            expression = result != "undefined" ? result : "Error";
          } catch (e) {
            expression = "Error";
          }

          if (expression.valueOf() === "69") {
            past_expression = "nice";
          }
        }
        break;
      default:
        if (expression.length <= 25) {
          expression += new String(value);
        }
    }
  }
</script>

<div class="eve">
  <div class="calcu">
    <Display top={past_expression} main={expression} />
    {#each buttons as { label, value, position }}
      <Button {label} {position} {value} on:click={click} />
    {/each}
  </div>
</div>

<style>
  .calcu {
    display: grid;
    grid-template-columns: repeat(4, 7rem);
    grid-template-rows: repeat(7, 6rem);
    grid-template-areas:
      "screen screen  screen screen"
      "screen screen  screen screen"
      "ac     precent divide del"
      "n7     n8      n9     x"
      "n4     n5      n6     minus"
      "n1     n2      n3     plus"
      "dot    n0      equal  equal";
    justify-content: center;
  }

  .eve {
    box-shadow: 0px 0px 10px 1px rgba(0, 0, 0, 0.375);
    border-radius: 20px;
    overflow: hidden;
  }
</style>
