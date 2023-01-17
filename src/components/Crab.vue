<script setup>
    import { ref, computed } from 'vue';
    const color = ref("#66FE87");

    const data = ref({
      name: 'Crab tank 1',
      state: 'working',
      params: [
        {
          name: 'Temperature',
          value: '+10',
          type: 'C',
          state: 'working',
          divisionSize: 5,
          start: -5
        },
        {
          name: 'Oxygen',
          value: '-77',
          type: 'mg/L',
          state: 'working',
          divisionSize: 5,
          start: 0
        }
      ]
    });

    /* Массивы для значений (нумерации) шкалы */
    let firstParamScale = [];
    let secondParamScale = [];

    /* Размер делений */
    const divisionSize = data.value["params"][0]["divisionSize"];

    /* Расчет шкалы */
    for (let index = 5; index >= 0; index--){
      firstParamScale[index]=data.value.params[0].start + index * divisionSize;
      secondParamScale[index]=data.value.params[1].start + index * divisionSize;
    }
    console.log(firstParamScale);
    console.log(secondParamScale);


    /* Цвета параметров в стандартном состоянии */
    const firstParamColor = ref("#48A7FF");
    const secondParamColor = ref("#B378FF");

    /* Изменение цвета состояния по первому параметру (левая шкала, нумерация шкалы и первое значение)*/
    function changeFirstState(){
      if (data.value["params"][0]["state"]!='working'){
        firstParamColor.value="#DB8181";
      }

      return firstParamColor.value;
    }

    /* Изменение цвета состояния по второму параметру (правая шкала, нумерация шкалы и второе значение) */
    function changeSecondState(){
      if(data.value["params"][1]["state"]!='working'){
        secondParamColor.value="#DB8181";
      }
      
      return secondParamColor.value;
    }


    /* Изменение цвета общего состояния (цвет рамки шкалы и краба) */
    function changeState(){
      console.log("kkk")
      if (data.value["params"][0]["state"]!='working' || data.value["params"][1]["state"]!='working'){
        color.value= "#DB8181";
      }  
      return color.value;
    }

    /*  */
    function firstParamValue (){
      console.log("dkk")
      let arr = (data.value["params"][0]["value"]).split("");
      let num = arr[1];
      // num = ...
      return num + "vh";
    } 

    function secondParamValue (){
      console.log("dkk")
      let arr = (data.value["params"][1]["value"]).split("");
      let num = arr[1];
      // num = ...
      return num + "vh";
    }
   
</script>

<template >
  <div class="w-[13vw] h-[17vh] opacity-40 bg-gradient-to-b p-[0.1vw] from-[#D6EBFF] to-[#272933] rounded-[0.6vw]">
    <div class="bg-[#3E404C] h-full rounded-[0.6vw] flex gap-[0.4vw]">
      
      <div :style="{'border-color':changeState()}" class="w-[3.33vw] h-[14.07vh] ml-[0.83vw] mt-[0.83vw]  border-2 border-solid rounded-lg relative">
        
        <div class="absolute left-[1.25vw] top-[1.1vh]">
          <!-- <img src="../assets/icons/crab.svg"/> -->
          <svg class="w-[0.625vw] h-[1.1vh]" viewBox="0 0 12 12" :fill="changeState()" xmlns="http://www.w3.org/2000/svg">
            <path d="M9.64912 6.62911C9.42992 7.17914 8.44355 7.56619 7.67634 8.13659C7.12833 8.54401 6.47074 8.66622 5.86793 8.50325C5.59393 8.44214 5.33816 8.31993 5.10069 8.13659C5.10069 8.13659 5.10067 8.13659 5.08241 8.11622C4.9728 8.03473 4.86324 7.9736 4.75364 7.89212C4.4431 7.68841 4.13258 7.52545 3.85858 7.34211C3.65764 7.21988 3.4749 7.07728 3.32877 6.93468C3.21917 6.83283 3.14613 6.73098 3.09133 6.60875C3.01827 6.44578 3 6.2828 3 6.1402C3 5.75315 3.20095 5.38647 3.65763 4.99942C4.5527 4.20495 5.17376 3.85864 6.37937 3.85864C7.20138 3.85864 7.74939 4.02161 8.29739 4.36792C8.55313 4.53089 8.80885 4.7346 9.10112 4.97906C9.28379 5.14203 9.4299 5.305 9.5395 5.46797C9.77697 5.87539 9.81353 6.24206 9.64912 6.62911Z" />
            <path d="M10.5342 2.32151C10.5898 2.15267 10.6641 1.8572 10.4786 1.49842C10.2189 1.01302 9.43969 0 8.45654 0C7.4734 0 6.75 0.400988 6.75 0.633139C6.75 0.86529 7.97428 0.56982 8.30818 0.865285C8.40093 0.949704 8.53078 1.09743 8.67918 1.30848C8.67918 1.30848 8.27104 1.64616 7.71454 1.70947C7.15805 1.77278 6.91693 1.7939 6.91693 2.06826C6.91693 2.34263 7.67752 2.46924 8.34532 2.23709C8.71632 2.11046 8.95747 1.96274 9.08732 1.87832C9.21717 2.06826 9.32843 2.23708 9.42118 2.36371C8.97598 2.74359 9.25423 3.67221 9.32843 3.90436C8.82758 3.75663 8.28963 4.26314 8.12268 4.43197C8.38238 4.60081 8.64206 4.81186 8.93886 5.06511C9.12436 5.23395 9.27274 5.40279 9.38404 5.57163C9.43969 5.50832 9.55103 5.42389 9.69943 5.27616C9.88493 5.10732 10.0148 4.87517 9.97768 4.64302C10.5713 4.22093 10.8309 3.86215 10.868 3.35564C10.9051 2.87024 10.7939 2.49035 10.5342 2.32151Z" />
            <path d="M4.20823 0.865285C4.5287 0.56982 5.625 0.86529 5.625 0.633139C5.625 0.400988 4.96726 0 4.07333 0C3.17941 0 2.47104 1.01302 2.23491 1.49842C2.06624 1.8361 2.13366 2.15267 2.18426 2.32151C1.96499 2.49035 1.84696 2.87024 1.88069 3.35564C1.91443 3.86215 2.16739 4.19982 2.69025 4.64302C2.65652 4.89628 2.77458 5.10732 2.94325 5.27616C3.07818 5.42389 3.17941 5.52942 3.23001 5.57163C3.33121 5.40279 3.46613 5.23395 3.63479 5.06511C3.88779 4.81186 4.1239 4.60081 4.3769 4.43197C4.24197 4.24203 3.73597 3.73552 3.28058 3.90436C3.34804 3.67221 3.60104 2.72249 3.19625 2.36371C3.28058 2.23708 3.38183 2.06826 3.49989 1.87832C3.61796 1.96274 3.82035 2.11046 4.17455 2.23709C4.78174 2.46924 5.47322 2.34263 5.47322 2.06826C5.47322 1.7939 5.25399 1.77278 4.74799 1.70947C4.242 1.64616 3.8709 1.30848 3.8709 1.30848C4.00584 1.11854 4.1239 0.949704 4.20823 0.865285Z" />
            <path d="M3.13962 6.45594C3.06114 6.28352 3.04152 6.11109 3.04152 5.96022L1.33454 5.57229C1.33454 5.57229 1.13838 5.55073 1.07952 5.78781C1.07952 5.78781 0.412385 5.93867 0.137705 7.01631C-0.136974 8.09394 0.0396821 8.24481 0.314362 8.09394C0.589041 7.94307 0.804803 7.53358 0.942143 7.31805C1.07948 7.10252 1.45228 6.47749 1.45228 6.47749C1.53076 6.52059 1.6092 6.54216 1.6092 6.54216L3.23772 6.82233C3.23772 6.82233 3.31614 6.84388 3.375 6.80078C3.2769 6.69302 3.17886 6.58526 3.13962 6.45594Z" />
            <path d="M3.95139 7.28687C3.44245 7.42981 2.38681 7.73613 2.38681 7.73613C2.38681 7.73613 2.14175 7.83822 2.17945 8.00158C2.17945 8.00158 1.84023 7.96075 1.87792 9.08388C1.91562 10.207 2.21716 10.4112 2.38681 10.2274C2.55646 10.0436 2.70725 9.28807 2.7638 9.04303C2.78265 8.9205 2.80156 8.71632 2.82041 8.55295L4.6865 7.9199C4.6865 7.9199 4.7996 7.91992 4.875 7.83823C4.55456 7.63403 4.23413 7.45023 3.95139 7.28687Z" />
            <path d="M6 8.5292C5.7126 8.46831 5.44431 8.34653 5.19523 8.16385C5.19523 8.16385 5.19521 8.16385 5.17605 8.14355C5.15689 8.16385 5.13779 8.18414 5.13779 8.18414L3.375 9.50353V9.52382C3.43248 9.7471 3.81572 11.2898 3.89237 11.5739C3.96901 11.8987 4.27555 12.3453 4.448 11.5739C4.62044 10.8229 4.4288 9.8486 4.40964 9.808C4.46712 9.74711 4.52467 9.6862 4.58216 9.64561C4.81208 9.52382 5.54015 8.91487 6 8.5292Z" />
            <path d="M11.8906 7.01505C11.6784 5.93835 11.1632 5.78763 11.1632 5.78763C11.1328 5.55075 10.9662 5.57229 10.9662 5.57229L9.64774 5.95988C9.64774 6.13215 9.61744 6.2829 9.57197 6.45517C9.52651 6.58437 9.46592 6.69204 9.375 6.79971C9.43562 6.84277 9.48103 6.82124 9.48103 6.82124L10.7389 6.54131C10.7389 6.54131 10.7843 6.51977 10.8601 6.4767C10.8601 6.4767 11.148 7.10119 11.2541 7.31652C11.3602 7.53186 11.5269 7.941 11.7391 8.09174C11.9815 8.24248 12.1028 8.11327 11.8906 7.01505Z" />
            <path d="M10.5705 8.00158C10.6082 7.83822 10.3632 7.73611 10.3632 7.73611C10.3632 7.73611 9.30756 7.42981 8.79861 7.28687C8.51587 7.47065 8.19544 7.634 7.875 7.83821C7.9504 7.91989 8.0635 7.9199 8.0635 7.9199L9.92959 8.55293C9.94844 8.71629 9.96735 8.9205 9.9862 9.04303C10.0427 9.28807 10.1935 10.0436 10.3632 10.2274C10.5328 10.4112 10.8532 10.207 10.8721 9.08388C10.9098 7.96075 10.5705 8.00158 10.5705 8.00158Z" />
            <path d="M7.61856 8.18393C7.61856 8.18393 7.59922 8.16375 7.57992 8.14355C7.57992 8.14355 7.57999 8.14355 7.56069 8.16374C7.30978 8.34547 7.03952 8.46663 6.75 8.52721C7.21323 8.91085 7.96595 9.49641 8.15896 9.65795C8.21686 9.69833 8.29414 9.75889 8.33275 9.81947C8.33275 9.85985 8.12039 10.8291 8.29411 11.5762C8.46782 12.3435 8.77662 11.8993 8.85383 11.5762C8.93103 11.2733 9.3171 9.75891 9.375 9.5368C9.375 9.51661 9.375 9.51659 9.375 9.51659L7.61856 8.18393Z"/>
          </svg>
        </div>

        <div class=" absolute left-[0.95vw] bottom-[0.39vh] ">
          <!-- <img :style="{'filter':changeFirstState()}" src="../assets/icons/thermo.svg"/> -->
          <svg class="w-[0.625vw] h-[10.2vh]" viewBox="0 0 14 112" :stroke="changeFirstState()" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M1 1H7"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M1 89H7"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M1 45H7"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M1 23H4H7"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M4.75 12L5.875 12L7 12"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M4.75 34L5.875 34L7 34"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M4.75 56L5.875 56L7 56"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M4.75 78L5.875 78L7 78"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M4.75 100L5.875 100L7 100"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M1 67H7"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M1 111H13"  stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 111L7 0.999999"  stroke-width="2" stroke-miterlimit="10"/>
          </svg>
          
        </div>

        <div class=" absolute right-[0.95vw] bottom-[0.39vh]">
          <!-- <img src="../assets/icons/thermo-right.svg"/> -->
          <svg width="0.625vw" height="10.2vh" viewBox="0 0 14 112" :stroke="changeSecondState()" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M7 1H13" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 89H13" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 45H13" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 23H10H13" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 12H8.125H9.25" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 34H8.125H9.25" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 56H8.125H9.25" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 78H8.125H9.25" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 100H8.125H9.25" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 67H13" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M1 111L13 111" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round"/>
            <path d="M7 111L7 0.999999" stroke-width="2" stroke-miterlimit="10"/>
          </svg>
        
        </div>

        <div :style="{'background-color':changeFirstState(), 'height':firstParamValue()}" class="w-[0.35vw] absolute left-[1.07vw] bottom-[1.11vh]"></div>
        <div :style="{'background-color':changeSecondState(), 'height':secondParamValue()}" class="w-[0.35vw] absolute right-[1.07vw] bottom-[1.11vh]"></div>
      
      <div class="absolute top-[2.05vh] left-[0.04vw] flex flex-col gap-[0.75vh]">
        <div :style="{'color':changeFirstState()}" v-for="item in firstParamScale" class="w-[0.78vw] h-[1.3vh] font-euclid text-[0.52vw] flex justify-end">{{item}}</div>
      </div>

      <div class="absolute top-[2.05vh] right-[0.04vw] flex flex-col gap-[0.75vh]">
        <div :style="{'color':changeSecondState()}" v-for="item in secondParamScale" class="w-[0.78vw] h-[1.3vh] font-euclid text-[0.52vw] flex justify-start text-[#009CF3]">{{item}}</div>   
      </div>

      </div>



    <div class="flex flex-col mt-[0.83vw]">

      <div class="w-[8.3vw] h-[2.9vh] bg-[#272933] rounded-tl-3xl rounded-bl-3xl rounded-tr-0 rounded-br-0 flex items-center">
        <div class="ml-[0.83vw] text-[#D6EBFF] font-medium text-[0.94vw] truncate font-euclid">{{ data["name"] }} </div>
      </div>

      <div class="flex flex-col mt-[2vh] ">
        <div class="flex flex-row gap-[0.4vw]">
          <div class="w-[4.01vw] ml-[0.3vw] text-[#D6EBFF] font-medium text-[0.625vw] font-euclid flex items-center justify-end"> <div class="truncate">{{data["params"][0]["name"]}}</div>:</div>
          <div :style="{'color':changeFirstState()}" class="w-[2.81vw] font-medium text-[0.83vw] font-euclid truncate flex items-center"> <div class="truncate mr-0.5">{{ data["params"][0]["value"] }}</div> {{data["params"][0]["type"]}} </div>
        </div>

        <div class="flex flex-row gap-[0.4vw] mt-[-0.3vh]"> 
          <div class=" w-[4.01vw] ml-[0.3vw] text-[#D6EBFF] font-medium text-[0.625vw] font-euclid overflow-hidden flex items-center justify-end"><div class="truncate">{{data["params"][1]["name"]}}</div>:</div>
          <div :style="{'color':changeSecondState()}" class="w-[3.5vw] font-medium text-[0.83vw] font-euclid truncate flex items-center"> <div class="truncate mr-0.5">{{ data["params"][1]["value"] }}</div> {{data["params"][1]["type"] }} </div>
        </div>
      </div>


      <div class="flex flex-row mt-[3.4vh] gap-[0.2vw] items-center">
        <img src="../assets/icons/vector.svg" class=" ml-[1.2vw]"/>
        <div class="w-[0.68vw] h-[0.93vh] text-[#33C300] font-medium text-[0.42vw] font-euclid text-center truncate overflow-hidden flex items-center">ON</div>
      </div>

    </div>


    </div>
  </div>
</template>

<style scoped>

</style>
