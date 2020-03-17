<template>
  <div id="topbar">
      <p id="menutitle">
        <img src="smol_cpaw.jpeg" alt="cpaw" width="32" height="46">
        {{ header }}
        <img src="smol_cpaw.jpeg" alt="cpaw" width="32" height="46">
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