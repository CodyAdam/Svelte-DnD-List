<div class="card">
  <div class="textBox">
    <h3 class="title">Name {id}</h3>
    <h5 class="subtitle">id: card-{id}</h5>
  </div>

  <div class="actionBox">

    <ButtonCody on:click={() => dispatch("delete")} on:mouseover={() => isHovered = true} on:mouseleave={() => isHovered = false}>
      {#if isHovered}
        🥭
      {:else}
        -
      {/if}
    </ButtonCody>


  </div>
</div>

<script>
import ButtonCody from "./ButtonCody.svelte";

export let id;
let isHovered = false;

import {createEventDispatcher} from "svelte";

const dispatch = createEventDispatcher();


</script>


<style>
  .card {
    margin: 0 0 20px 0;
    padding: 20px;
    background-color: #393939;
    height: 80px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    min-width: 0;
    flex-flow:row nowrap;
    box-sizing: border-box;
    cursor: grab;
  }

  .textBox {
    min-width: 0;
    flex-shrink: 2;
  }

  .actionBox {
    min-width: 0;
    flex-shrink: 1;
  }


  .title {
    margin: 0;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
  }

  .subtitle {
    margin: 0;
    font-weight: normal;
    font-style: italic;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
  }

  .minus {
    margin: 20px;
    padding: 10px;
    border: none;
    border-radius: 4px;
    width: 50px;
    height: 50px;
    color: #e2dddd;
    font-size: large;
    transition: all 0.2s;
    cursor: pointer;
    outline: none;
    background-color: #2d2d2d;
  }
</style>
