<script>

    let xPointsCount = 10;
    let yPointsCount = 10;

</script>

<svg version="1.1"
     width="300" height="200"
     xmlns="http://www.w3.org/2000/svg">

    <line x1="0" x2="0" y1="0" y2="200" stroke="orange" stroke-width="5"/>
    <line x1="0" x2="300" y1="200" y2="200" stroke="orange" stroke-width="5"/>


    {#each Array(xPointsCount) as _, i}
        <circle cx="0" cy={i * 20} r="5" stroke="red" fill="red"/>
    {/each}


</svg>

<style>

</style>