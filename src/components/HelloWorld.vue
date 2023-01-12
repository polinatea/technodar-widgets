<script setup>
    import { ref } from 'vue';
    const componentState = ref(""); // working, error, warning
    // if working ..
</script>

<template >
  <div class="w-[13vw] h-[17vh] opacity-40 bg-gradient-to-b p-[0.1vw] from-[#D6EBFF] to-[#272933] rounded-[0.6vw]">
    <div class="bg-[#3E404C] h-full rounded-[0.6vw] relative">

      <div class="w-[3.3vw] h-[14vh] border-2 border-[#66FE87] border-solid rounded-lg absolute left-[6.5%] top-[8.7%]">
        
        <div class="absolute left-[40.62%] right-[40.62%] top-[7.89%] bottom-[84.21%]">
          <img src="../assets/icons/crab.svg"/>
        </div>

        <div class="w-[0.6vw] h-[10vh] absolute left-[29.69%] right-[51.56%] top-[19.74%] bottom-[7.89%]">
          <img src="../assets/icons/thermo.svg"/>
        </div>

        <div class="w-[0.6vw] h-[10vh] absolute left-[51.56%] right-[29.69%] top-[19.74%] bottom-[7.89%]">
          <img src="../assets/icons/thermo-right.svg"/>
        </div>

        <div class="w-[0.4vw] h-[5.9vh] bg-[#009CF3] absolute left-[32.81%] right-[54.69%] top-[51.32%] bottom-[7.89%]"></div>
        <div class="w-[0.4vw] h-[3.1vh] bg-[#B378FF] absolute left-[54.69%] right-[32.81%] top-[72.37%] bottom-[7.89%]"></div>
      </div>

      <div class="w-[8.2vw] h-[2.9vh] bg-[#272933] rounded-tl-3xl rounded-bl-3xl rounded-tr-0 rounded-br-0 absolute left-[35.96%] right-[0%] top-[8.7%] bottom-[73.91%]">
        <p class=" text-[#D6EBFF] font-medium text-xs truncate overflow-hidden absolute left-[10.06%] right-[28.93%] top-[15.62%] bottom-[15.63%] flex items-center font-euclid">Crab tank 1 </p>
      </div>

      <p class="w-[77px] h-[10px] text-[#D6EBFF] font-medium text-[9px] text-right font-euclid truncate overflow-hidden absolute left-[36.99%] right-[31.71%] top-[40.22%] bottom-[54.35%] flex items-center "> Temperature:</p>

      <p class="w-[34px] h-[13px] text-[#48A7FF] font-medium text-xs font-euclid truncate overflow-hidden absolute left-[71.54%] right-[14.63%] top-[38.59%] bottom-[54.35%] flex items-center">+8 C</p>
    
      <p class="w-[48px] h-[14px] text-[#D6EBFF] font-medium text-[9px] text-right font-euclid truncate overflow-hidden absolute left-[48.78%] right-[31.71%] top-[51.09%] bottom-[41.3%] flex items-center">Oxygen:</p>
   
      <p class="w-[54px] h-[15px] text-[#B378FF] font-medium text-xs font-euclid truncate overflow-hidden absolute left-[71.54%] right-[6.5%] top-[50.54%] bottom-[42.39%] flex items-center">7 mg/L</p>
   
      <div class="w-[46px] h-[13px] absolute left-[34.96%] right-[46.34%] top-[80.24%] bottom-[8.7%] ">
        <img src="../assets/icons/vector.svg" class="absolute left-[54.35%] right-[46.65%] top-0 bottom-0"/>
        <p class="w-[13px] h-[10px] text-[#33C300] font-medium text-[8px] font-euclid text-center truncate overflow-hidden absolute left-[63.04%] right-[8.7%] top-[15.38%] bottom-[7.69%] flex items-center">ON</p>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
