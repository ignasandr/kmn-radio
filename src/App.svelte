<script>
import {onMount, onDestroy} from 'svelte'

  import logo_new from "./assets/logo_new.png"

  let audio;
  let paused = true;

  let timer = 0;

  let timeout = false;
  let notified = false;

  const interval = setInterval(() => timer += 1, 1000);
  $: if(paused && !notified && timer >= 5) 
    {
      timeout = true;
      notified = true;
    };

	onDestroy(() => {
		clearInterval(interval);
	});


  const togglePlay = () => {
    if (paused) {
      audio.play();
      timeout = false;
      notified = true;
    }
    else {
      audio.pause();
    }
  }

</script>

<main>
  <div class="button-container">
    <div role = "button" tabIndex={0} id="button" class="button"  on:click={togglePlay}>
      <img src={logo_new} alt="PLAY" class={paused ? "pause" : "play"}/>
        <audio
          bind:this={audio}
          bind:paused
          src={"https://radijas.kmn.lt/listen/sapfo_radijas/radio.mp3"}
        />
    </div>
    <div class={timeout ? "warning true" : "warning"} > ↑ Listen here ↑ </div>
</main>

<style lang="scss">

.button-container {
  position: absolute;
  left: 50%;
  top: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

.button {
    cursor: pointer;
  img {
    max-height: 30vh;
    transition: 300ms all ease;
    filter: gray; /* IE6-9 */
    -webkit-filter: grayscale(1); /* Google Chrome, Safari 6+ & Opera 15+ */
    filter: grayscale(1); /* Microsoft Edge and Firefox 35+ */

  // play state
    &.play {
      filter: none;
    }
  }
}

.warning {
  margin-top: 10px;
  color: #d94814;
  width: 100%;
  text-align: center;
  visibility: hidden;
  opacity: 0%;
  &.true {
    visibility: visible;
    opacity: 100%;
    margin-top: 20px;
  }
  transition: 600ms all ease;
} 


</style>
