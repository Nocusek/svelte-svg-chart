<script>

    let graphWidth = 300;
    let graphHeight = 200;

    let xPointsCount = 10;
    // @ts-ignore
    let yPointsCount = 10;

    // @ts-ignore
    let points = [
        {
            x: 10,
            y: 10
        },
        {
            x: 50,
            y: 50,
        },
        {
            x: 80,
            y: 30
        }
    ]

    // @ts-ignore
    function formatPoints(points) {
        // @ts-ignore
        return points.map(point => `${point.x},${point.y}`).join(' ');
    }

</script>

<svg version="1.1"
     width={graphWidth} height={graphHeight}
     xmlns="http://www.w3.org/2000/svg">
     
     <g>
        <line x1="0" x2="0" y1="0" y2="200" stroke="orange" stroke-width="5"/>
        {#each Array(xPointsCount) as _, i}
            <circle cx="0" cy={i * 20} r="5" stroke="red" fill="red"/>
        {/each}
     </g>

     <g>
        <line x1="0" x2="300" y1="200" y2="200" stroke="orange" stroke-width="5"/>
        {#each Array(xPointsCount) as _, i}
            <circle cx="{i * 20}" cy="200" r="5" stroke="red" fill="red"/>
        {/each}
     </g>

     <g>
        <polyline 
        class="polyline"
        points={formatPoints(points)}/>
     </g> 

</svg>

<style>
.polyline {
    fill: none;
    stroke: blue;
    stroke-linejoin: round;
    stroke-linecap: round;

    &:hover {
        stroke-width: 5;
    }
}
</style>