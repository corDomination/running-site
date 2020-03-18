<template>
  <div id="topbar">
      <p id="menutitle">
        The Runner's Page
      </p>
      <nav>
        <a class="active" href="#home">Home</a>
        <a target="_blank" href="https://gobearcats.com/sports/track-and-field/schedule/2019-20">Team Schedule</a>
        <a target="_blank" href="https://gobearcats.com/sports/track-and-field/archives">News</a>
        <a target="_blank"
          href="https://www.tfrrs.org/top_performances/OH_college_m_Cincinnati.html?list_hnd=2776&season_hnd=474">Mens
          Results</a>
        <a target="_blank"
          href="https://www.tfrrs.org/top_performances/OH_college_f_Cincinnati.html?list_hnd=2776&season_hnd=474">Womens
          Results</a>
      </nav>
    </div>
</template>

<script>
export default {
  name: 'topbar',
  props: ['header'],
}
</script>

<style scoped>
a {
    font-size: 30px;
    color: white;
    text-decoration: none;
    border-radius: 6px;
    border: 4px solid white;
    margin: 8px;
    padding: 2px;
  }
  a:hover {
    border-color: red;
  }

  nav {
    color: whitesmoke;
    text-align: center;
    font-size: 48px;
    background-color: black;
    width: 100%;
    border-top: 10px solid blue;
    border-bottom: 10px solid blue;
    padding-bottom: 20px;
  }
  p#menutitle {
    float: left;
    width: 100%;
    margin: 8px 0;
    border: none;
    font-size: 64px;
    text-align: center;
    color: white;
    background-color: black;
  }
</style>