<script lang="ts">
  import Participant from "./Participant.svelte";

  let visible = true;
  let audio_enable = true;

  let participantNames = ["Member cat(2)", "Member cat(3)", "Member cat(4)"];

  let nextParticipant: string;
  setInterval(() => {
    nextParticipant = `Member cat(${participantNames.length + 2})`;
  }, 5 * 1000);
  const handleApprove = () => {
    // Svelte's reactivity is triggered by assignment.
    participantNames = [...participantNames, nextParticipant];
    nextParticipant = undefined;
  };
</script>

{#if nextParticipant}
  <div id="popup">
    Waiting "{nextParticipant}"
    <button on:click={handleApprove}>Approve</button>
  </div>
{/if}

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
  {#each participantNames as name, index}
    <Participant {name} catType={index} />
  {/each}
</div>

<div class="list-of-participants">
  <ul>
    <li>participant(1) (you)</li>
    {#each participantNames as name}
      <li>{name}</li>
    {/each}
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
