<script>
  import Scroller from "@sveltejs/svelte-scroller";
  import App from "../components/App.svelte";

  let count, index, offset, progress;
</script>

<Scroller
  top={0.0}
  bottom={1}
  threshold={0.5}
  bind:count
  bind:index
  bind:offset
  bind:progress
>
  <!-- <div class="background" slot="background">

  </div> -->

  <div class="foreground" slot="foreground">
    <section class="WriteUp">
      <h1 class="title">Are Volcanoes Becoming Deadlier?</h1>
      <h2> A visualization by David Lycke, Dhilan Sunanda Bong, and Joshua Huang</h2>
      <div class='pad'></div>
      <p class="para">
        Volcano eruptions, while volatile, don't happen often and we are also able to predict when they'll occur. <br> 
        However, with the world facing record high temperatures because of climate change, <br>
        experts theorized that this warming may lead to increasing frequency of some natural phenomenoms, <br>
        including volcanic eruptions. 
      </p>
      <p class='para'>
        As such, we could expect to see increasing counts of volcanic eruptions with greater explositivity over the upcoming years. <br> 
        This could prove problematic as consecutive eruptions will whittle down our livable space, all the while our population continues to skyrocket. <br> 
        Along with that, multiple volcano eruptions on a large scale could lead to a cooling event which could destroy ecosystems.
      </p>
      <p class="para">Let's put this theory to the test. To determine the activity extent of volcanos currently, <br>
        we've plotted multiple historically recorded volcano eruptions ranging from all the way in the BC period to the near present. <br> 
        Try exploring and hovering the US map first and compare the occurences and intensity of eruptions between years. <br>
        For an extra activity, try to find the eruptions with the highest destructive rank. Then, switch to the global map and try exploring similar or different trends! </p>
        
    </section>
    <section class="Graph">
      US Volcano records over the past 200+ years. Choose one or multiple
      filters and explore! Switch to the world map for even further exploration:
  
      <App />
    </section>
    <section class="WriteUp">This is the third section.</section>
  </div>
</Scroller>

<style>
  .Graph {
    height: 130vh;
    background-color: lightblue; /* 20% opaque */
    /* color: white; */
    outline: black;
    text-align: center;
    max-width: 5000px; /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
    width: 100%;
    margin-right: auto;
    margin-left: auto;
    margin-top: 0px;
  }

  .WriteUp {
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.2); /* 20% opaque */
    /* color: white; */
    outline: black;
    text-align: center;
    max-width: 5000px; /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
  }

  .title {
    padding: 1em;
  }

  .para {
    padding: 1em
  }

  h2 {
    text-align:center;
    font-size: 18px;
    color:gray;
    margin: 2px;
  }
  .pad {
    margin:15vh;
  }
</style>
