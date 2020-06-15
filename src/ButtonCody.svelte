<button on:click={() => dispatch('click')} on:mouseover={() => dispatch("mouseover")} on:mouseleave={() => dispatch("mouseleave")} disabled={loading}>
    {#if loading}

      <svg class="button-loading" style="width:24px;height:24px" viewBox="0 0 24 24">
        <path fill="currentColor" d="M12,4V2A10,10 0 0,0 2,12H4A8,8 0 0,1 12,4Z"/>
      </svg>

    {:else}
      <slot></slot>
    {/if}
</button>

<script>
export let loading = false;

import {createEventDispatcher} from "svelte";
const dispatch = createEventDispatcher();
</script>

<style>
  @keyframes loading {
    0% {
      transform: rotate(0);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  button {
    position: relative;
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
    background-color: #393939;

  }

  .button-loading {
    animation: loading 1s infinite 0s linear;
  }

  button:hover {
    background-color: #487988;
  }
  button:disabled {
    background-color: #7b7b7b;
    cursor: auto;
  }
</style>
