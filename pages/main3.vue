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
              <v-form class="w-100 d-flex justify-space-between flex-column"  :style="{ height: form + 'px' }" >
                  <div class="w-100 d-flex flex-column ga-2 overflow-f" >
                     <div class="w-100 d-flex justify-center check ga-2 pa-1">
                        <div class="w-100 pa-2">
                                <p class="text-h6 text-center"><span class="bg-grey-lighten-2">Qualification</span></p>
                                <v-row class="mt-1">
                                    <v-col
                                    v-for="option in qualificationoption"
                                    :key="option.value"
                                    cols="12" sm="6"
                                    >
                                    <CheckboxButton 
                                        :name="'qualification-type'"
                                        :label="option.label"
                                        :value="option.value"
                                        v-model="qualification"
                                        class=" w-100"
                                    />
                                    </v-col>
                                </v-row>
                            </div>
                            <div class="w-100 pa-2" >
                                <p class="text-h6 text-center"><span class="bg-grey-lighten-2">Occupation</span></p>
                                <v-row class="mt-1">
                                    <v-col
                                    v-for="option in occupationoption"
                                    :key="option.value"
                                    cols="12" sm="6"
                                    >
                                    <CheckboxButton 
                                        :name="'occupation-type'"
                                        :label="option.label"
                                        :value="option.value"
                                        v-model="occupation"
                                        class=" w-100"
                                    />
                                    </v-col>
                                </v-row>
                            </div>
                            <div class="w-100 pa-2" >
                                <h1 class="text-h6 text-center"><span class="bg-grey-lighten-2">Annual Income</span></h1>
                                <v-row class="mt-1">
                                    <v-col
                                    v-for="option in annualincomeoption"
                                    :key="option.value"
                                    cols="12" sm="6"
                                    >
                                    <CheckboxButton 
                                        :name="'annualincome-type'"
                                        :label="option.label"
                                        :value="option.value"
                                        v-model="annualincome"
                                        class=" w-100"
                                    />
                                    </v-col>
                                </v-row>
                            </div>
                            <div class="w-100" >
                                <h1 class="text-h6 text-center"><span class="bg-grey-lighten-2">Trading Experience</span></h1>
                                <v-row class="mt-1">
                                    <v-col
                                    v-for="option in tradingoption"
                                    :key="option.value"
                                    cols="12" sm="6"
                                    >
                                    <CheckboxButton 
                                        :name="'trading-type'"
                                        :label="option.label"
                                        :value="option.value"
                                        v-model="trading"
                                        class=" w-100"
                                    />
                                    </v-col>
                                </v-row>
                            </div>
                     </div>
                     <div class="w-100 pa-1 d-flex flex-column ga-2 pa-2" >
                        <div class="w-100 ysno d-flex justify-space-between" >
                            <div class="w-100 al d-flex justify-end align-center">
                                <p><span class="bg-grey-lighten-2">ARE YOU PEP / RELATED TO PEP</span> <span class="bg-grey-lighten-2">[PEP = POLITICALLY EXPOSED PERSON]</span></p>
                            </div>
                            <div class="w-100 d-flex ysnobtn justify-center" >
                                    <CheckboxButton 
                                     v-for="option in yesnooption"
                                    :key="option.value"
                                        :name="'yesno-type'"
                                        :label="option.label"
                                        :value="option.value"
                                        v-model="yesno"
                                        class=" pa-1 full"
                                    />
                                </div>
                            </div>

                            <div class="w-100 ysno d-flex justify-space-between pa-2" >
                            <div class="w-100 al d-flex justify-end align-center">
                                <p><span class="bg-grey-lighten-2">NATIONALITY</span></p>
                            </div>
                            <div class="w-100 d-flex ysnobtn justify-center" >
                                    <CheckboxButton 
                                     v-for="option in nationoption"
                                    :key="option.value"
                                        :name="'nation-type'"
                                        :label="option.label"
                                        :value="option.value"
                                        v-model="nation"
                                        class=" pa-1 full"
                                    />
                                </div>
                            </div>
      
                     </div>
                  </div>
                  <div class="w-100 pa-1 d-flex justify-space-between align-center" >
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
  // height
  const deviceHeight = ref(0);
  const boxex1Height=ref(0)
  const boxex2Height=ref(0)
  const form=ref(0)
  const form1=ref(0)
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
    form.value = Math.floor(boxex2Height.value * 0.97); 
    form1.value = Math.floor(form.value * 0.90); 
    ismobile.value=false
    
  }
  else{
    deviceHeight.value = window.innerHeight;
    boxex1Height.value = Math.floor(deviceHeight.value * 0.10); 
    boxex2Height.value = Math.floor(deviceHeight.value * 0.95);
    form.value = Math.floor(boxex2Height.value * 0.97); 
    form1.value = Math.floor(form.value * 0.90); 
    ismobile.value=true
  
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
  
  const qualificationoption = ref([
      { label: 'Graduate ', value: 'Graduate' },
      { label: 'Post Graduate', value: 'Post Graduate' },
      { label: 'Professional Degree', value: 'Professional Degree' },
      { label: 'Doctrate ', value: 'Doctrate' },
      { label: 'High School', value: 'High School' },
      { label: 'Under High School', value: 'Under High School' },
      { label: 'Illitrate', value: 'Illitrate' },

    ]);
    const qualification=ref('')

    const occupationoption = ref([
      { label: 'Private Sector ', value: 'Private Sector' },
      { label: 'Student', value: 'Student' },
      { label: 'Public Sector', value: 'Public Sector' },
      { label: 'House Wife ', value: 'House Wife' },
      { label: 'Business', value: 'Business' },
      { label: 'Retired', value: 'Retired' },
      { label: 'Professional', value: 'Professional' },
      { label: 'Forex Dealer', value: 'Forex Dealer' },
     { label: 'Agriculturalist', value: 'Agriculturalist' },

    ]);
    const occupation=ref('')

    const annualincomeoption = ref([
      { label: 'Upto 1 Lakh ', value: 'Upto 1 Lakh' },
      { label: '1 Lakh to 5 Lakhs', value: '1 Lakh to 5 Lakhs' },
      { label: '5 Lakhs to 10 Lakhs', value: '5 Lakhs to 10 Lakhs' },
      { label: '10 Lakhs to 25 Lakhs ', value: '10 Lakhs to 25 Lakhs' },
      { label: 'Above 25 Lakhs', value: 'Above 25 Lakhs' },
    ]);
    const annualincome=ref('')

    const tradingoption = ref([
      { label: 'New to Trading ', value: 'New to Trading' },
      { label: '1 to 2 Years', value: '1 to 2 Years' },
      { label: '2 to 5 Years', value: '2 to 5 Years' },
      { label: '5 to 10 Years ', value: '5 to 10 Years' },

    ]);
    const trading=ref('')
 
    const yesnooption = ref([
      { label: 'NO, I am Not ', value: 'NO, I am Not' },
      { label: 'YES, I am', value: 'YES, I am' },
      
    ]);
    const yesno=ref('')

    const nationoption = ref([
      { label: 'Indian ', value: 'Indian' },
      { label: 'Others', value: 'Others' },
      
    ]);
    const nation=ref('')
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
 
.overflow-f{
    overflow: hidden;

}
  @media(max-width:800px){
  .overflow-f{
    overflow-y: scroll;
  }
 
  .check{
    flex-wrap: wrap;
  }
  .ysno{
    flex-wrap: wrap;
  }
  .over-f{
    overflow-y: scroll;
  }
  .ysnobtn{
    justify-content: start !important;
  }
  .al{
    align-items: start !important;
    justify-content: start !important;
  }
  .full{
    display: flex !important;
    width: 100% !important;
  }
  }
  </style>
  