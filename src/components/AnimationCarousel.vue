<template>
    <div class="container">
      <div class="vertical-center container-btn" id="skip">
            <button class="btn" @click="togglePlayPause" :aria-label="isPlaying? 'pause' : 'play'">{{ isPlaying ? '⏸️' : '▶️' }}</button>
          </div>
        <div class="carousel-container" @click="togglePlayPause">
          
        <div class="carousel-image" v-for="(image, index) in images" 
            <--- use role if any --->
        :key="index" 
        :style="{ backgroundImage: `url(${image.src})` }" 
        :class="{ 'active': index === currentIndex }">
            <img :src="image.src" :alt="image.alt" />     
        </div>  
        </div>
    </div>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Non sodales neque sodales ut etiam sit. Facilisis magna etiam tempor orci eu lobortis elementum nibh tellus. Mauris sit amet massa vitae tortor condimentum lacinia quis. Sollicitudin tempor id eu nisl nunc mi ipsum faucibus vitae. Nunc vel risus commodo viverra maecenas accumsan. Vitae purus faucibus ornare suspendisse sed nisi lacus sed. Tempor commodo ullamcorper a lacus vestibulum sed. A arcu cursus vitae congue. Ultricies mi eget mauris pharetra et ultrices neque. Leo in vitae turpis massa. Dui ut ornare lectus sit amet. Proin nibh nisl condimentum id venenatis a. Dignissim enim sit amet venenatis urna cursus eget nunc scelerisque. Justo nec ultrices dui sapien eget mi proin. Purus faucibus ornare suspendisse sed nisi. Massa tempor nec feugiat nisl pretium fusce. Sodales ut etiam sit amet nisl purus. Netus et malesuada fames ac turpis egestas. Sed felis eget velit aliquet sagittis id consectetur.

Sit amet nulla facilisi morbi tempus iaculis. Ligula ullamcorper malesuada proin libero. Curabitur vitae nunc sed velit dignissim sodales ut eu. Vivamus at augue eget arcu dictum varius. Nulla porttitor massa id neque aliquam. Arcu cursus euismod quis viverra nibh cras pulvinar mattis. Felis donec et odio pellentesque diam volutpat commodo. Dolor purus non enim praesent elementum facilisis leo vel. Sed arcu non odio euismod. Enim ut sem viverra aliquet. Justo laoreet sit amet cursus sit amet dictum sit. Diam donec adipiscing tristique risus nec feugiat in. Eleifend donec pretium vulputate sapien. Sed viverra tellus in hac habitasse platea.

Ultrices mi tempus imperdiet nulla malesuada. Sed euismod nisi porta lorem mollis aliquam ut. Venenatis cras sed felis eget velit aliquet sagittis id. Lacus sed viverra tellus in hac habitasse platea dictumst vestibulum. Pulvinar neque laoreet suspendisse interdum. Gravida quis blandit turpis cursus in. Nec ultrices dui sapien eget mi proin. Ullamcorper velit sed ullamcorper morbi tincidunt ornare massa eget. Ultrices sagittis orci a scelerisque. Auctor augue mauris augue neque gravida in fermentum et. In ante metus dictum at tempor commodo ullamcorper. Sit amet purus gravida quis blandit. Venenatis lectus magna fringilla urna porttitor rhoncus dolor. Ultrices neque ornare aenean euismod. Turpis cursus in hac habitasse platea. Mauris ultrices eros in cursus turpis massa tincidunt dui ut. Justo eget magna fermentum iaculis. Morbi tincidunt augue interdum velit euismod. Nulla facilisi morbi tempus iaculis.

Tempus egestas sed sed risus pretium quam vulputate dignissim suspendisse. Tincidunt id aliquet risus feugiat in. Semper auctor neque vitae tempus quam. Ullamcorper sit amet risus nullam eget. Sodales neque sodales ut etiam sit amet nisl purus in. Pellentesque id nibh tortor id aliquet lectus proin nibh nisl. Donec ultrices tincidunt arcu non sodales neque sodales ut etiam. Varius morbi enim nunc faucibus a. At elementum eu facilisis sed odio morbi quis. Leo vel fringilla est ullamcorper eget nulla facilisi. Commodo quis imperdiet massa tincidunt nunc pulvinar.

Commodo nulla facilisi nullam vehicula ipsum a. Volutpat est velit egestas dui id ornare arcu odio ut. Nunc consequat interdum varius sit amet. Lobortis scelerisque fermentum dui faucibus in. Sed libero enim sed faucibus turpis in. Proin fermentum leo vel orci porta non pulvinar neque. Vitae tortor condimentum lacinia quis. Massa placerat duis ultricies lacus sed turpis tincidunt id aliquet. Suspendisse in est ante in nibh mauris cursus mattis molestie. Consectetur lorem donec massa sapien faucibus. Sed odio morbi quis commodo odio. Nunc sed augue lacus viverra. Sed enim ut sem viverra aliquet eget sit amet tellus.</p>

</template>
<script>
export default {
    data() {
        return {        
          images: [
        { src:  '/Image/image1.jpg', alt: 'Quaint & Healing beauty of Natue' },
        { src:  '/Image/image2.jpg', alt: 'Quaint & Healing beauty of Natue' },
        { src:  'Image/image3.jpg', alt: 'Quaint & Healing beauty of Natue' },
        { src:  'Image/image4.jpg', alt: 'Quaint & Healing beauty of Natue' },
        { src:  '/Image/image5.jpg', alt: 'Quaint & Healing beauty of Natue' }
        // Add more images as needed
      ],
      currentIndex: 0,
      isPlaying: true,
      intervalId: null,
        }
    },
    mounted() {
    this.startRotation();
    },
    methods: {
    startRotation() {
      this.intervalId = setInterval(() => {
        this.currentIndex = (this.currentIndex + 1) % this.images.length;
      }, 2000); // Rotate every 5 seconds
    },
    stopRotation() {
      clearInterval(this.intervalId);
    },
    togglePlayPause() {
      this.isPlaying = !this.isPlaying;
      if (this.isPlaying) {
        this.startRotation();
      } else {
        this.stopRotation();
      }
    },
    actionMethod() {
      console.log("Yea!! I'm in action.")
    }
 },
}
</script>
<style scoped>
img {
  height: 100%;
  width: 100%;
}
p {
  padding-top: 5px;
}
.carousel-container {
 position: relative;
 width: 100%;
 height: 400px;
 overflow: hidden;
}

.carousel-image {
 position: absolute;
 width: 100%;
 height: 100%;
 background-size: cover;
 background-position: center;
 opacity: 0;
 transition: opacity 1s;
 background-color: pink;
}
.carousel-image.active {
 opacity: 1;
}
.container { 
position: relative;
}
.vertical-center {
margin: 5px;    
position: absolute;     
top: -18px;
-ms-transform: translateY(-50%);
transform: translateY(-50%);
}
button {
border: none;
border-radius: px;
background-color: white;
}
/* Hidding button */
#skip button
{
position:absolute;
left:-10000px;    
top:auto;
width:1px;
height:1px;
overflow:hidden;
}
 /* Display button with hover and focus */
.container:hover #skip button,
#skip button:focus
{
position:static;
width:auto;
height:auto;
}
</style>
