<script lang="ts">
    import type { StravaActivity } from '$lib/activities.js'
    import ChartContainer from '$lib/components/charts/chart-primitive.svelte'
    import * as Plot from "@observablehq/plot";
    export let activities: StravaActivity[];

    let chart: HTMLDivElement;

    $: if (activities && activities[0] && chart) {
        chart.innerHTML = '';
        chart?.append( // @ts-ignore
            Plot.rectY(
                activities, 
                Plot.binX(
                    {y: "count" },
                    {x: (d) => Math.sqrt(d.distance || NaN)}
                )
            ).plot({x: {label: "Distance", transform: (x) => `${(x*x) / 1000} km`},}
            )
        );
    }
</script>
  
<ChartContainer>
    <svelte:fragment slot="options">
    </svelte:fragment>
    <svelte:fragment slot="title">
        <h2>Rides by Frequency</h2>
    </svelte:fragment>
    <svelte:fragment slot="chart">
        <div bind:this={chart}>
        </div>
    </svelte:fragment>
</ChartContainer>