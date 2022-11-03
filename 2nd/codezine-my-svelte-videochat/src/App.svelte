<script lang="ts">
  let visible = true;
</script>

<div class="participants">
  <div class="participant p1">
    <span>participant cat(1) (you)</span>
    {#if visible}
      <img src="https://placekitten.com/320/240?image=1" alt="participant-1" />
    {:else}
      <img
        src="https://via.placeholder.com/320x240/000000/FFFFFF/?text=Video%20OFF"
        alt="participant-1-video-off"
      />
    {/if}
  </div>
  <div class="participant">
    <span>participant cat(2)</span>
    <img src="https://placekitten.com/320/240?image=2" alt="participant-2" />
  </div>
  <div class="participant">
    <span>participant cat(3)</span>
    <img src="https://placekitten.com/320/240?image=3" alt="participant-3" />
  </div>
  <div class="participant">
    <span>participant cat(4)</span>
    <img src="https://placekitten.com/320/240?image=4" alt="participant-4" />
  </div>
</div>

<div class="list-of-participants">
  <ul>
    <li>participant(1) (you)</li>
    <li>participant(2)</li>
    <li>participant(3)</li>
    <li>participant(4)</li>
  </ul>
</div>

<div class="control">
  <button>Leave</button>
  <button>Audio ON/OFF</button>
  <button on:click={() => (visible = !visible)}>Video ON/OFF</button>
  <button>Share screen</button>
</div>

<style>
  .participants {
    display: flex;
    flex-flow: row wrap;
  }
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
  .list-of-participants {
    clear: both;
  }
</style>
