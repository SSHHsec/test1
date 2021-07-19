<template>
  <div id="ImageDetection">
    <v-row>
      <canvas id="ImageDetection"></canvas>
    </v-row>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "ImageDetection",
  props: {
    getImaggaAuth: {
      type: Function,
      required: true,
    },
  },
  data: () => ({
    DetectionData: [], 
    }),
  created() {
    this.getImageDections();
  },
    methods: {
      async getImageDections() {
      await axios  
        .get(
          `https://api.imagga.com/v2/faces/detections?image_url=${this.$store.state.imageUrl}&language=ko`,
          this.getImaggaAuth()
        )
        .then((res) => {
          if (res.data.status.type === "success") {
           const imageDetections = res.data.result.faces.image_faces;
    
          }
             
        
    

    function draw() {
        var canvas = document.getElementById('canvas');
        if (canvas.getContext) {
            var ctx = canvas.getContext('2d');
            var lineCap = 'button';
            ctx.strokeRect(100, 100, 100, 100);
            ctx.strokeStyle = 'red';
            for (var i=0;i<lineCap.length;i++){
                ctx.lineWidth = 10;
                ctx.lineCap = lineCap[i];
                ctx.beginPath();
                ctx.rect(30,50,100,100);
            }
        }
    
            var ctx = document.getElementById('canvas').getContext('2d');
            ctx.font = '15px serif';
            ctx.fillText('Female', 10, 50);
            ctx.fillStyle = "black"
            ctx.textBaseline = 'hanging';
            ctx.strokeText('Female', 0, 70);    
    
    }
        }
</script>