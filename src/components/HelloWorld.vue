<script setup>
    import { ref } from 'vue';
    const color = ref("");
    const componentState = ref("error"); // working, error, warning
    function changeState(){
      console.log("kkk")
      if (componentState=='working'){
      color= "#66FE87";
    } else 
    if (componentState=="warning"){
      color= "#FFCC81";
    } else
    if (componentState=="error"){
      color="#DB8181";
    }
    console.log(color)
    return (color.style);
  }
    // if working ..
</script>

<template >
  <div class="w-[13vw] h-[17vh] opacity-40 bg-gradient-to-b p-[0.1vw] from-[#D6EBFF] to-[#272933] rounded-[0.6vw]">
    <div class="bg-[#3E404C] h-full rounded-[0.6vw] flex gap-[0.4vw]">
      
      <div :style="{'border-color':changeState()}" class="w-[3.33vw] h-[14.07vh] ml-[0.83vw] mt-[0.83vw]  border-2 border-solid rounded-lg relative">
        
        <div class="absolute left-[1.3vw] top-[1.1vh]">
          <img src="../assets/icons/crab.svg"/>
        </div>

        <div class=" absolute left-[0.85vw] top-[2.7vh]">
          <img src="../assets/icons/thermo.svg"/>
        </div>

        <div class=" absolute right-[0.85vw] top-[2.7vh]">
          <img src="../assets/icons/thermo-right.svg"/>
        </div>

        <div class="w-[0.4vw] h-[5.9vh] bg-[#009CF3] absolute left-[1.01vw] top-[7.2vh]"></div>
        <div class="w-[0.4vw] h-[3vh] bg-[#B378FF] absolute right-[1.01vw] top-[10.1vh]"></div>
      
      <div class="absolute top-[2.05vh] left-[0.04vw] flex flex-col gap-[0.8vh]">
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-end text-[#009CF3]">20</div>
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-end text-[#009CF3]">20</div>
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-end text-[#009CF3]">20</div>
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-end text-[#009CF3]">20</div>
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-end text-[#009CF3]">20</div>      
      </div>

      <div class="absolute top-[2.05vh] right-[0.04vw] flex flex-col gap-[0.8vh]">
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-start text-[#009CF3]">20</div>
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-start text-[#009CF3]">20</div>
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-start text-[#009CF3]">20</div>
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-start text-[#009CF3]">20</div>
        <div class="w-[0.78vw] h-[1.3vh] font-euclid text-[10px] flex justify-start text-[#009CF3]">20</div>      
      </div>

      </div>



    <div class="flex flex-col mt-[0.83vw]">

      <div class="w-[8.3vw] h-[2.9vh] bg-[#272933] rounded-tl-3xl rounded-bl-3xl rounded-tr-0 rounded-br-0 flex items-center">
        <div class="ml-[0.83vw] text-[#D6EBFF] font-medium text-lg truncate overflow-hidden font-euclid">Crab tank 1 </div>
      </div>

      <div class="flex flex-col mt-[2vh] ">
        <div class="flex flex-row gap-[0.4vw]">
          <div class="w-[4.01vw] ml-[0.3vw] text-[#D6EBFF] font-medium text-xs text-right font-euclid truncate overflow-hidden  flex items-center justify-end"> Temperature:</div>
          <div class="text-[#48A7FF] font-medium text-base font-euclid truncate overflow-hidden flex items-center">+8 C</div>
        </div>

        <div class="flex flex-row gap-[0.4vw] mt-[-0.3vh]"> 
          <div class=" w-[4.01vw] ml-[0.3vw] text-[#D6EBFF] font-medium text-xs font-euclid truncate overflow-hidden flex items-center justify-end">Oxygen:</div>
          <div class=" text-[#B378FF] font-medium text-base font-euclid truncate overflow-hidden flex items-center">7 mg/L</div>
        </div>
      </div>


      <div class="flex flex-row mt-[3.7vh] gap-[0.2vw] items-center">
        <img src="../assets/icons/vector.svg" class=" ml-[1.2vw]"/>
        <div class="w-[13px] h-[10px] text-[#33C300] font-medium text-[8px] font-euclid text-center truncate overflow-hidden flex items-center">ON</div>
      </div>

    </div>


    </div>
  </div>
</template>

<style scoped>

</style>
