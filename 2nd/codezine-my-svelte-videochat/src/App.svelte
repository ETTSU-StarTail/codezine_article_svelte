<script lang="ts">
  import Participant from "./Participant.svelte";

  let visible = true;
  let audio_enable = true;

  let participants = [
    { name: "Member cat(2)", video: true },
    { name: "Member cat(3)", video: true },
    { name: "Member cat(4)", video: true },
  ];
</script>

<div class="participants">
  <div class="participant p1">
    <span
      >participant cat(1) (you) {#if audio_enable}
        🔊
      {:else}
        🔇
      {/if}</span
    >
    {#if visible}
      <img src="https://placekitten.com/320/240?image=1" alt="participant-1" />
    {:else}
      <img
        src="https://via.placeholder.com/320x240/000000/FFFFFF/?text=Video%20OFF"
        alt="participant-1-video-off"
      />
    {/if}
  </div>
  {#each participants as participant, index}
    <Participant name={participant.name} catType={index} />
  {/each}
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
  <button on:click={() => (audio_enable = !audio_enable)}>Audio ON/OFF</button>
  <button on:click={() => (visible = !visible)}>Video ON/OFF</button>
  <button>Share screen</button>
</div>

<style>
  .participants {
    display: flex;
    flex-flow: row wrap;
  }
  .list-of-participants {
    clear: both;
  }
</style>
