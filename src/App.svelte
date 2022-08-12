<script>
  import logo from "./assets/logo.png"
  import logo_new from "./assets/logo_new.png"

  let audio;
  let paused = true;

  const togglePlay = () => {
    if (paused) {
      audio.play();
      paused = false;
    }
    else {
      audio.pause();
      paused = true;
    }
  }
</script>

<main>
  <!-- <div class="image-container">
    <img src={logo} alt="Kombinatas logo">
  </div> -->
  <div class="button-container">
    <div role = "button" tabIndex={0} id="button" class="button"  on:click={togglePlay}>
      <img src={logo_new} alt="PLAY" class={paused ? "pause" : "play"}/>
        <audio
          bind:this={audio}
          bind:paused
          src={"https://radijas.kmn.lt/listen/sapfo_radijas/radio.mp3"}
        />
    </div>
  </div>
</main>

<style lang="scss">
/* .image-container {
  left: 0;
  bottom: 0;
  position: fixed;
  img {
    max-height: 30vh;
    max-width: 50vw;
  }
} */

.button-container {
  /* position: fixed;
  left: 44vw;
  top: 44vh; */
  position: absolute;
  left: 50%;
  top: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

.button {
    cursor: pointer;
  // play state
  img {
    max-height: 30vh;
    transition: 300ms all ease;

/* Disable grayscale on hover */
    &.play {
      filter: none;
    }

    &.pause {
      filter: gray; /* IE6-9 */
      -webkit-filter: grayscale(1); /* Google Chrome, Safari 6+ & Opera 15+ */
      filter: grayscale(1); /* Microsoft Edge and Firefox 35+ */
    }
  &:hover {
    -webkit-filter: grayscale(0);
    filter: none;
  }
  }
}
</style>
