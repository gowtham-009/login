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
         <div class="w-100 bg-grey-lighten-4 rounded-t-xl pa-1 d-flex justify-center align-center" :style="{ height: boxex2Height + 'px' }" >
             <v-form class="w-100 d-flex justify-space-between flex-column  ga-2" :style="{ height: form + 'px' }">
              <div class="w-100 over-f" :style="{height:form1 +'px'}" >
                 <div class="w-100 b1 pa-1 rounded-xl bg-white" >
                  <div v-if="!pdfpanshow" class="w-100 d-flex ga-2 flex-column  b1" >
                             <p class="text-center">
                              Aadhaar Proof
                             </p>
                            <div class="w-100 pdf rounded-xl d-flex justify-center" style="border: 4px solid black;">
                              <v-btn class="bg-yellow">Auto File Show / File Uploaded</v-btn>
                            </div>
                            <p class="text-center">
                              Pan Proof
                             </p>
                            <div class="w-100 pdf rounded-xl d-flex justify-center " style="border: 4px solid black;">
                              <v-btn class="bg-yellow">Auto File Show / File Uploaded</v-btn>
                            </div>
                         </div>
                         <div v-if="pdfpanshow" class="w-100 d-flex ga-2  b1" >
                            <div class="w-100 pdf-m rounded-xl d-flex justify-center flex-column ga-2" >
                              <p class="text-center">
                              Aadhaar Proof
                             </p>
                              <adharpancheck
                            v-for="option in adharoption "
                            :key="option.value"
                            :name="'adhar-type'"
                            :label="option.label"
                            :value="option.value"
                            v-model="adhar"
                            class="pa-2"
                        />
                            </div>
                            <div class="w-100 pdf-m rounded-xl d-flex justify-center flex-column ga-2" >
                              <p class="text-center">
                              Pan Proof
                             </p>
                              <adharpancheck
                            v-for="option in panoption "
                            :key="option.value"
                            :name="'pan-type'"
                            :label="option.label"
                            :value="option.value"
                            v-model="pan"
                            class="pa-2"
                        />
                            </div>
                         </div>
                 </div>
                 <div class="w-100 b2 pa-3 d-flex flex-column justify-space-between rounded-xl bg-white pt-3">
                  <div class="w-100">
                        <v-text-field label="PAN Number" variant="solo-filled"></v-text-field>
                      </div>
                      <div class="w-100">
                        <v-text-field label="Name as per PAN Website" variant="solo-filled"></v-text-field>
                      </div>
                      <div class="w-100 date d-flex ga-2">
                        <input type="date" name="" id="" class="w-50 pa-1 rounded-lg"   style=" height: 60px;">
                        <v-text-field class="w-50 aad" label="Aadhaar Number (Least four Digit Number)" variant="solo-filled"></v-text-field>
                     </div>
                     <div class="w-100">
                        <v-text-field label="Father Name" variant="solo-filled"></v-text-field>
                      </div>
                      <div class="w-100">
                        <v-text-field label="Mother Name" variant="solo-filled"></v-text-field>
                      </div>
                      <div class="w-100">
                        <p>Gender*</p>
                        <CheckboxButton
                            v-for="option in genderoption "
                            :key="option.value"
                            :name="'gender-type'"
                            :label="option.label"
                            :value="option.value"
                            v-model="gender"
                            class="pa-2"
                        />
                      </div>
                      <div class="w-100">
                        <p>Marital Status*</p>
                        <CheckboxButton
                            v-for="option in maritaloption "
                            :key="option.value"
                            :name="'marital-type'"
                            :label="option.label"
                            :value="option.value"
                            v-model="marital"
                            class="pa-2"
                        />
                      </div>
                 </div>
              </div>
              <div class="w-100 pa-1  d-flex align-center justify-space-between">
                <v-btn  class="bg-black rounded-xl">Preview</v-btn>
                <v-btn  class="bg-indigo rounded-xl">Next</v-btn>
            </div>
             </v-form>
         </div>
      </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import CheckboxButton from '~/components/checkbutton.vue';
import adharpancheck from '~/components/adharpancheck.vue';
// height
const deviceHeight = ref(0);
const boxex1Height=ref(0)
const boxex2Height=ref(0)
const form=ref(0)
const form1=ref(0)
const forminput=ref(0)
const show = ref(false);
const ismobile=ref(false)
const pdfpanshow=ref(false)
const toggleShow = () => {
show.value = !show.value;
};
// Set the device height when the component is mounted
const updateDeviceDimensions = () => {
if(window.innerWidth > 800){
  deviceHeight.value = window.innerHeight;
  boxex1Height.value = Math.floor(deviceHeight.value * 0.12); 
  boxex2Height.value = Math.floor(deviceHeight.value * 0.88); 
  form.value = Math.floor(boxex2Height.value * 0.97); 
  form1.value = Math.floor(form.value * 0.93); 
  forminput.value = Math.floor(form.value * 0.90); 
  ismobile.value=false
  pdfpanshow.value=false
}
else{
  deviceHeight.value = window.innerHeight;
  boxex1Height.value = Math.floor(deviceHeight.value * 0.10); 
  boxex2Height.value = Math.floor(deviceHeight.value * 0.95);
  form.value = Math.floor(boxex2Height.value * 0.97); 
  form1.value = Math.floor(form.value * 0.93); 
  forminput.value = Math.floor(form.value * 0.90); 
  ismobile.value=true
  pdfpanshow.value=true
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

const genderoption = ref([
      { label: 'Male ', value: 'Male' },
      { label: 'Female', value: 'Female' },
      { label: 'Transgender', value: 'Transgender' },
     
    ]);
    const gender=ref('')

    const maritaloption = ref([
      { label: 'Single ', value: 'Single' },
      { label: 'Married', value: 'Married' },
    
     
    ]);
    const marital=ref('')

    const adharoption = ref([
      { label: 'Checked ', value: 'Checked' },
     
    
     
    ]);
    const adhar=ref('')

    const panoption = ref([
      { label: 'Checked ', value: 'Checked' },
     
    
     
    ]);
    const pan=ref('')
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
.pdf{
  height: 250px;
}
.over-f{
  display: flex;
  align-items: stretch; 
  gap: 5px;
  overflow: hidden;
}
.b1, .b2 {
flex-grow: 1; /* Makes them equally stretch */
display: flex; /* Optional, if you want content inside to be flexbox aligned */
justify-content: center;
align-items: center;
}
.pdf-m{
    height: 100px;

}

.over-f{
  overflow: hidden;
}
.date input{
  background-color: rgb(245, 244, 244);
  box-shadow: rgba(103, 103, 103, 0.2) 2px 8px 24px;
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
overflow-y: scroll;

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
.date{
  flex-wrap: wrap;
}
.date input{
  width: 100% !important;
  background-color: rgb(236, 236, 236);
}
.aad{
  margin-top: 2%;
}
}
</style>
