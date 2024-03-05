<script>
    //globe section

    import * as d3 from 'd3';
    import { onMount } from 'svelte';
	import * as topojson from 'topojson-client';
	import { geoPath, geoAlbersUsa } from 'd3-geo';
	import { draw } from 'svelte/transition';
    import { geoOrthographic, geoGraticule10} from "d3-geo";
	import { json } from "d3-fetch";

    const projection_globe = geoOrthographic().scale(400);
    const graticule = geoGraticule10();
    const path_globe = geoPath(projection_globe)

    let outline = ({type: "Sphere"});
    let land, borders;

    export let volcanos;
    export let US_volcanos;

    json(
        "https://cdn.jsdelivr.net/npm/world-atlas@2/countries-50m.json"
        ).then((world) => {
	land = topojson.feature(world, world.objects.land);
	borders = topojson.mesh(world, world.objects.countries, (a, b) => a !== b)
    });


    const width = 1200;
	const height = 1000;

    function coord_proj_cx(d) {
                let coords = [  
                        { lat: d['latitude'], long: d['longitude'] },
                        ].map(p => projection_globe([p.long, p.lat]))
                //$: console.log(coords[0][0])
                return coords[0][0]
        }

    function coord_proj_cy(d) {
            let coords = [
		    { lat: d['latitude'], long: d['longitude'] },
	            ].map(p => projection_globe([p.long, p.lat]))
            //$: console.log(d['longitude'])
            //$: console.log(coords[0][1])

            return coords[0][1]
    }

    function color_checker(d) {
        if (d['country'] == "United States") {
            return "red";
        }
        if (d['location'] == "Africa-E") {
            return "orange";
        }
        if (d['country'] == "Cameroon") {
            return "yellow";
        }
        return "black";
    }

    //console.log(volcanos);
</script>
<div class="globe"> 

    <svg
                {width}
                {height}
                viewBox="-120 -250 {width} {height}"
                style:max-width="100%"
                style:height="auto"
                style:display="block"
                style:margin="auto"
                style:max-height="100%"
                >   

                <path d={path_globe(outline)} fill="#12dbff"/>
                <path d={path_globe(graticule)} stroke="black" fill="none"/>
                <path d={path_globe(land)} fill="green"/>
                <path d={path_globe(borders)} fill="none" stroke="black" />
                <path d={path_globe(outline)} fill="none" stroke="black" />

                {#each volcanos as d, i}
                        <circle
                            cx={coord_proj_cx(d)}
                            cy={coord_proj_cy(d)}
                            r=4
                            fill={color_checker(d)}
                        />
                {/each}
    </svg>
</div>