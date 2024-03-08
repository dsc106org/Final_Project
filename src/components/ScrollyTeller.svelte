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
      <h1 class="title">Is Volcano Activity Increasing over the Years?</h1>
      <p class="para">
        Volcano eruptions, while volatile, aren't often occuring with high frenquency and such occurences are often balanced out by the ability of predicting when they'll occur along with <br>
        the positives that they can bring to nature. But with the world facing the increasing and new recording temperatures thanks to climate change, <br />
        it's been theorized by experts that this may influence increasing occurences in natural phenomenoms, including volcanic eruptions. Therefore it may be that we're expected to start seeing increasing <br />
        counts of volcanic eruptions with greater explositivity over the upcoming years. This could prove
        problematic as while <br />
        volcanos have many benefits, too many consecutive eruptions may endanger
        nearby civilizations <br />
        along with greatly reducing potential living space as our population continues
        to skyrocket. Along <br />
        with this, multiple volcano eruptions on a large scale could cause a cooling
        event which would further worsen the global temperature.
      </p>
      <p class="para">Let's put this theory to the test. To determine the activity extent of volcanos currently, <br>
        we've plotted multiple historically recorded volcano eruptions ranging from some pre 1800s and even <br>
        in the BC, all the way to the 2000s. Try exploring and hovering the US map first and compare the occurences <br>
        and intensitivity of eruptions between years. For an extra activity, try to find the eruptions <br>
        with the highest destructive rank. Then switch the US map and try exploring similar or different trends! </p>
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
  }

  .WriteUp {
    height: 80vh;
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
</style>
