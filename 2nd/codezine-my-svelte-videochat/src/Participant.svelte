<script lang="ts">
  export let participant: { name: string; video: boolean };
</script>

<div class="participant">
  <span>{participant.name}</span>
  <img src="https://placekitten.com/320/240?image=1" alt="participant-1" />
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
