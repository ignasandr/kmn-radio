<script>
  import logo from "./assets/logo.png"

  let audio;
  let paused = true;

  const togglePlay = () => {
    if (paused) {
      audio.play();
    }
    else {
      audio.pause();
    }
  }
</script>

<main>
  <div class="image-container">
    <img src={logo} alt="Kombinatas logo">
  </div>
  <div class="button-container">
    <div role = "button" tabIndex={0} id="button" class={paused ? "button" : "button pause"} on:click={togglePlay}>
        <audio
          bind:this={audio}
          bind:paused
          src={"https://radijas.kmn.lt/listen/kombinatas_radio/radio.mp3"}
        />
    </div>
    </div>
</main>

<style lang="scss">
.image-container {
  left: 0;
  bottom: 0;
  position: fixed;
  img {
    max-height: 70vh;
    max-width: 50vw;
  }
}

.button-container {
  position: fixed;
  left: 44vw;
  top: 44vh;
}

.button {
  box-sizing: border-box;
  height: 74px;
  
  border-color: transparent transparent transparent #f37021;
  transition: 100ms all ease;
  will-change: border-width;
  cursor: pointer;

  // play state
  border-style: solid;
  border-width: 37px 0 37px 60px;

  // paused state
  &.pause {
    border-style: double;
    border-width: 0px 0 0px 60px;
  }
}
</style>
