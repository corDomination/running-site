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
    color: black;
    text-decoration: none;
    border-radius: 20px;
    border: 4px solid var(--primary);
    margin: 8px;
    padding: 8px 30px;
    background-color: rgb(204,204,204);
  }
  a:hover {
    color: blue;
    border-color: blue;
    background-color: rgb(222,222,222);
  }

  nav {
    color: whitesmoke;
    text-align: center;
    font-size: 48px;
    background-color: white;
    width: 100%;
    border-bottom: 10px solid var(--primary);
    margin-bottom:10px;
    padding-bottom: 20px;
    padding-top:10px;
  }
  p#menutitle {
    width: 100%;
    margin: 0px 0;
    border: none;
    font-size: 48px;
    text-align: center;
    color: white;
    background-color: var(--primary);
  }
</style>