<script>

export let location;
export let count;

let mapId = "map-" + count;

    import { onMount } from 'svelte'
    import mapboxgl from "mapbox-gl";
    mapboxgl.accessToken = "pk.eyJ1Ijoib3dlbmdvdCIsImEiOiJjbDcyNzFwMGwwaG5lM29uOWI3dTVsM2ZqIn0.4xI9UmoEHiQHFJ8C9mEvNg"
    

    onMount(() => {
        const map = new mapboxgl.Map({
            container: mapId,
            style: "mapbox://styles/owengot/cj8sxsh1tcvh92rqnskcxfht3",
            center: [location.lng, location.lat],
            zoom: 12,
            attributionControl: false
            
        });     
    })
</script>


<main>
<div id="{mapId}"></div>
</main>

<style>
    main div {
        height: 200px;
        position: relative;
    }

</style>