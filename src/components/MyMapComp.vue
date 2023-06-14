<template>
<h2 class="heading">Welcome to my map</h2>
    <div id="map">
    </div>
</template>

<script>
import L from 'leaflet';
import vechicleCoordinates from '../data/vechicleCoordinates';
// import taxiIcon from '../assets/taxicab.png';
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
}
map.on('locationfound', onLocationFound);
function onLocationError(e) {
    alert(e.message);
}
map.on('locationerror', onLocationError);
 var taxiIcon = L.icon({
     iconUrl: 'https://i.postimg.cc/FRPsCtnR/ic-new-white-taxi.png',
     iconSize: [50,50]
 })
 for(const vechicleCoordinate of vechicleCoordinates)
 L.marker([vechicleCoordinate.latitude,vechicleCoordinate.longitude],{icon: taxiIcon}).addTo(map);
    }
}

</script>

<style scoped>
.heading {
    margin-top: 55px;
}
#map {
    width: 80vw;
    height: 85vh;
    justify-content: center;
    align-items: center;
    margin-left: 150px;
}
</style>
