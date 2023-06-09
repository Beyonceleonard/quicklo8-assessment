<template>
<h2 class="heading">Welcome to my map</h2>
    <div id="map">
    </div>
</template>

<script>
import L from 'leaflet';
export default {
    mounted(){
        const map = L.map('map').fitWorld();

L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '© OpenStreetMap'
}).addTo(map);
map.locate({setView: true, maxZoom: 16});
function onLocationFound(e) {
    var radius = e.accuracy;

    L.marker(e.latlng).addTo(map)
        .bindPopup("You are within " + radius + " meters from this point").openPopup();

    L.circle(e.latlng, radius).addTo(map);
}

map.on('locationfound', onLocationFound);
function onLocationError(e) {
    alert(e.message);
}

map.on('locationerror', onLocationError);
    }
}

</script>

<style scoped>
.heading {
    margin-top: 55px;
}
#map {
    width: 100vw;
    height: 100vh;
}
</style>
