<template>
    <div>
        <div class="w-100" :style="{ height: deviceHeight + 'px' }">
           <div class="w-100 bg-indigo">
            <div v-if="!ismobile" class="w-100 d-flex" :style="{ height: boxex1Height + 'px' }">
                <div class="w-100 d-flex justify-start align-center logo"  >
                <p class="text-h5 text-white pl-1">Logo</p>
                </div>
                <div  class="w-100" >
                <p class="text-h5 text-white text-center">Welcome User</p>
                <div class="mt-1 d-flex justify-center justify-space-between ga-2">
                    <div class="b bg-white d-flex justify-center align-center rounded-circle"><span>1</span></div>
                    <div class="b bg-white d-flex justify-center align-center rounded-circle"><span>2</span></div>
                    <div class="b bg-white d-flex justify-center align-center rounded-circle"><span>3</span></div>
                    <div class="b bg-white d-flex justify-center align-center rounded-circle"><span>4</span></div>
                    <div class="b bg-white d-flex justify-center align-center rounded-circle"><span>5</span></div>
                    <div class="b bg-white d-flex justify-center align-center rounded-circle"><span>6</span></div>
                    <div class="b bg-white d-flex justify-center align-center rounded-circle"><span>7</span></div>
                    <div class="b bg-white d-flex justify-center align-center rounded-circle"><span>8</span></div>
                </div>
                </div>
                <div class="w-100 d-flex justify-end align-center pa-1" >
                <div class="c bg-white rounded-circle"></div>
                </div>
            </div>
            <!-- mobile -->
            <div v-if="ismobile" class="w-100"  >
                <v-card class="mx-auto w-100 bg-indigo">
                    <v-card-actions>
                    <v-btn color="text-white" text="Logo"></v-btn>
                    <v-spacer><p class="text-center">75%</p></v-spacer>
                    <v-btn :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'" @click="toggleShow"></v-btn>
                    
                    </v-card-actions>

                    <v-expand-transition>
                    <div v-show="show">
                      
                        <v-card-text>
                          <div class="w-100 d-flex justify-center ga-2">
                             <div class="level d-flex justify-center align-center rounded-circle"><span class="text-black">1</span></div>
                             <div class="level d-flex justify-center align-center rounded-circle"><span class="text-black">2</span></div>
                             <div class="level d-flex justify-center align-center rounded-circle"><span class="text-black">3</span></div>
                             <div class="level d-flex justify-center align-center rounded-circle"><span class="text-black">4</span></div>
                             <div class="level d-flex justify-center align-center rounded-circle"><span class="text-black">5</span></div>
                             <div class="level d-flex justify-center align-center rounded-circle"><span class="text-black">6</span></div>
                             <div class="level d-flex justify-center align-center rounded-circle"><span class="text-black">7</span></div>
                             <div class="level d-flex justify-center align-center rounded-circle"><span class="text-black">8</span></div>
                          </div>
                        </v-card-text>
                    </div>
                    </v-expand-transition>
                </v-card>
            </div>

           </div>
           <div class="w-100 rounded-t-xl pa-1 d-flex justify-center align-center" :style="{ height: boxex2Height + 'px' }" >
               <v-form class="w-100 d-flex justify-space-between flex-column  ga-2" :style="{ height: form + 'px' }" >
                  <div class="w-100 pa-1 over-f" :style="{ height: form1 + 'px' }" >
                       <div v-if="!log" class="w-100 b1 pa-2 d-flex justify-center align-center rounded-xl bg-grey-lighten-5" >

                       </div>
                       <div class="w-100 b2 pa-2 d-flex justify-center align-center flex-column rounded-xl bg-grey-lighten-5" >
                        <div class="w-75 wd mt-3">
                                <v-text-field label="Login" variant="solo-filled"></v-text-field>
                            </div>
                        <div class="w-75 wd mt-3">
                                <v-text-field label="Password" variant="solo-filled"></v-text-field>
                            </div>
                       </div>
                  </div>
                  <div class="w-100 pb-2 d-flex justify-space-between">
                    <v-btn size="large" class="bg-black rounded-xl">Preview</v-btn>
                    <v-btn size="large" class="bg-indigo rounded-xl">Next</v-btn>
                  </div>
               </v-form>
           </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

// height
const deviceHeight = ref(0);
const boxex1Height=ref(0)
const boxex2Height=ref(0)
const form=ref(0)
const form1=ref(0)
const forminput=ref(0)
const log=ref(false)
const show = ref(false);
const ismobile=ref(false)

const toggleShow = () => {
  show.value = !show.value;
};
// Set the device height when the component is mounted
const updateDeviceDimensions = () => {
 if(window.innerWidth > 800){
    deviceHeight.value = window.innerHeight;
    boxex1Height.value = Math.floor(deviceHeight.value * 0.12); 
    boxex2Height.value = Math.floor(deviceHeight.value * 0.88); 
    form.value = Math.floor(boxex2Height.value * 0.95); 
    form1.value = Math.floor(form.value * 0.90); 
    forminput.value = Math.floor(form.value * 0.90); 
    ismobile.value=false
    log.value=false
 }
 else{
    deviceHeight.value = window.innerHeight;
    boxex1Height.value = Math.floor(deviceHeight.value * 0.10); 
    boxex2Height.value = Math.floor(deviceHeight.value * 0.95);
    form.value = Math.floor(boxex2Height.value * 0.95); 
    ismobile.value=true
    log.value=true
 }
};

// Setup event listeners for device dimension changes
onMounted(() => {
  updateDeviceDimensions(); // Initial call to set dimensions on component mount
  window.addEventListener('resize', updateDeviceDimensions); // Listen for window resize events
});

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateDeviceDimensions); // Clean up: remove resize event listener
});
</script>

<style>
html, body {
    overflow-y: hidden;
   
}
.b {
  width: 30px;
  height: 30px;
}
.c {
  width: 60px;
  height: 60px;
  cursor: pointer; /* Ensures it's clear this is clickable */
}
.level{
    width: 40px;
    height: 40px;
    background-color: white;
}
.over-f{
    display: flex;
    align-items: stretch; 
    gap: 5px;

}
.b1, .b2 {
  flex-grow: 1; /* Makes them equally stretch */
  display: flex; /* Optional, if you want content inside to be flexbox aligned */
  justify-content: center;
  align-items: center;
}
.b2{
    flex-direction: column;
    justify-content: space-between;
}


.over-f{
    overflow: hidden;
}
@media(max-width:800px){
.wd{
  width: 100% !important;
}
.over-f{
  flex-wrap: wrap;
 gap: 5px;
  
}
.over-f{
  display: block;
  
  
}

  .b1, .b2 {
    width: 100%; 
    flex-grow: 0;
    height: auto; 
    margin-top: 2%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
