<template>
    <div id="landslide-alert-layer" class="landslide-alert-layer">
        <l-layer-group :layer-type="alertLayerType" :name="alertLayerName" :visible="alertLayerVisible">
            <div v-for="landslideAlert in landslideAlerts">
                <landslide-alert-station-layer :specific-alert="landslideAlert"> </landslide-alert-station-layer>
            </div>
        </l-layer-group>
    </div>
</template>

<script>
    import LandslideAlert from "../../../store/models/alerts/landslide/landslideAlert";
    import LandslideAlertStationLayer from "./LandslideAlertStationLayer";
    import { LLayerGroup } from "vue2-leaflet"

    export default {
        name: "landslide-alert-layer",
        components:{ LLayerGroup,LandslideAlertStationLayer},
        data(){
            return {
                alertLayerName: 'general-layer-landslide-alert',
                alertLayerType: 'overlay',
                alertLayerVisible: true,
            }
        },
        computed: {
            landslideAlerts(){
                return LandslideAlert.all()
            }
        }
    }
</script>

<style scoped>

</style>