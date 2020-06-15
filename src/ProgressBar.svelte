{#if loading}
<div class="progress-line"></div>
{/if}
<script>
export let loading = false;
</script>

<style>
  .progress-line, .progress-line:before {
    height: 7px;
    width: 100%;
    margin: 0;
  }

  .progress-line {
    z-index: 100;
    display: -webkit-flex;
    display: flex;
    position: absolute;
    left: 0;
    right: 17px;
    top: 0;
    height: 7px;

  }

  .progress-line:before {
    background-color: #a02323;
    content: '';
    -webkit-animation: running-progress 2s cubic-bezier(0.4, 0, 0.2, 1) infinite;
    animation: running-progress 2s cubic-bezier(0.4, 0, 0.2, 1) infinite;
  }

  @-webkit-keyframes running-progress {
    0% {
      margin-left: 0px;
      margin-right: 100%;
    }
    50% {
      margin-left: 25%;
      margin-right: 0%;
    }
    100% {
      margin-left: 100%;
      margin-right: 0;
    }
  }

  @keyframes running-progress {
    0% {
      margin-left: 0px;
      margin-right: 100%;
    }
    50% {
      margin-left: 25%;
      margin-right: 0%;
    }
    100% {
      margin-left: 100%;
      margin-right: 0;
    }
  }


</style>
