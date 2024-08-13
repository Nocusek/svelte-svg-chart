<script>

    let graphWidth = 300;
    let graphHeight = 200;

    let graphWidthPadding = 20;
    let graphHeightPadding = 20;

    let xPointsCount = 10;
    let yPointsCount = 10;

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

    /**
	 * @param {any[]} points
	 */
    function formatPoints(points) {
        return points.map(point => `${point.x},${point.y}`).join(' ');
    }

    let numbers = Array.from({ length: yPointsCount + 1 }, (_, i) => i).toReversed();

</script>

<svg version="1.1"
     width={graphWidth} height={graphHeight}
     xmlns="http://www.w3.org/2000/svg">
     
     <g>
        <line x1={graphWidthPadding} x2={graphWidthPadding} y1={-graphHeightPadding} y2={graphHeight} stroke="orange" stroke-width="5"/>
        {#each numbers as value, index}
            <circle cx={graphWidthPadding} cy={index * 20 - graphHeightPadding} r="5" stroke="red" fill="red"/>
            <text x={0} y={index * 20 - graphHeightPadding + 5} font-size="20">{value}</text>
        {/each}
     </g>

     <g>
        <line x1={graphWidthPadding} x2={graphWidth} y1={graphHeight - graphHeightPadding} y2={graphHeight - graphHeightPadding} stroke="orange" stroke-width="5"/>
        {#each Array(xPointsCount) as _, i}
            <circle cx="{i * 20 + graphWidthPadding}" cy={graphHeight - graphHeightPadding} r="5" stroke="red" fill="red"/>
            <text x={i * 20 + graphWidthPadding - 5} y={graphHeight} font-size="20">{i}</text>
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