<script lang="ts">
  export let name: string;
  export let catType: number;
  let video: boolean = true;
</script>

<div class="participant">
  <span on:click={() => (video = !video)}>{name}</span>

  {#if video}
    <img
      src="https://placekitten.com/320/240?image={catType + 2}"
      alt="participant-{catType + 2}"
    />
  {:else}
    <img
      src="https://via.placeholder.com/320x240/000000/FFFFFF/?text=Video%20OFF"
      alt="participant-{catType + 2}-video-off"
    />
  {/if}
</div>

<style>
  .participant {
    position: relative;
    width: 320px;
    height: 240px;
    border: 1px solid black;
    margin: 2px;
    background-color: black;
  }
  .participant span {
    background-color: black;
    color: white;
    padding: 0 0.5rem;
    position: absolute;
    top: 0;
  }
</style>
