<script setup>
  import { ref, computed } from 'vue';

  const data = ref({
    name: 'ГД1',
    state: 'warning',
    type: 'engine', // ['diesel-generator', 'boiler' ] (дизель-генератор, котел)
    frequency_value: 216,
    frequency_type: 'об/мин',
    params: [
      {
        name: 'Мгн. расход',
        value: '324444',
        type: 'кг/чxxxx',
      },
      {
        name: 'Мгн. расход',
        value: '324324',
        type: 'кг/ч',
      },
      {
        name: 'Мгн. расход',
        value: '324324',
        type: 'кг/ч',
      },
      {
        name: 'Мгн. расход',
        value: '324324',
        type: 'кг/ч',
      },
      {
        name: 'Мгн. расход',
        value: '324324',
        type: 'кг/ч',
      },
    ],
  });

  // Цвета параметров
  const states = ref({
    warning: '#FFCC81',
    error: '#DB8181',
    default: '#48A7FF',
    working: '#66FE87',
  });

  // Изменение цвета состояния по первому параметру (левая шкала, нумерация шкалы и первое значение)
  function changeStateColor(state) {
    if (states.value[state]) {
      // if not undefined
      return states.value[state];
    }
    return states.value.default;

    // if (data.value.type == 'engine' || data.value.type == 'diesel-generator') {
    //   if (data.value.frequency_value != 0) {
    //     if (data.value.state == 'warning') {
    //       stateColor.value = '#FFCC81';
    //     } else if (data.value.state == 'error') {
    //       stateColor.value = '#DB8181';
    //     }
    //   } else {
    //     stateColor.value = '#48A7FF';
    //   }
    // } else {
    //   if (data.value.state == 'warning') {
    //     stateColor.value = '#FFCC81';
    //   } else if (data.value.state == 'error') {
    //     stateColor.value = '#DB8181';
    //   }
    // }
    // return stateColor.value;
  }
</script>

<template>
  <div
    class="h-[17vh] w-[13vw] rounded-[0.6vw] bg-gradient-to-b from-[#D6EBFF] to-[#272933] p-[0.1vw] font-euclid">
    <div class="flex h-full rounded-[0.6vw] bg-[#3E404C]">
      <div class="flex flex-col">
        <div
          class="mt-[1.94vh] ml-[1.09vw] flex h-[2.037vh] w-[3.125vw] flex-row items-center gap-[0.42vw]">
          <div
            :style="{ color: changeStateColor() }"
            class="flex h-[2.037vh] w-[1.40625vw] items-center justify-end truncate text-[0.9375vw] text-[#66FE87]">
            {{ data.frequency_value }}
          </div>
          <div
            class="flex h-[2.037vh] w-[1.04vw] items-center overflow-y-hidden break-all text-[0.5208vw] leading-[0.75vh] text-[#D6EBFF]">
            {{ data.frequency_type }}
          </div>
        </div>
        <div class="relative mt-[1.9vh] ml-[0.9375vw]">
          <img class="h-[2.22vh] w-[2.708vw]" src="../assets/icons/agregat/engine.svg" />
          <img
            v-if="['error', 'warning'].includes(data.state)"
            class="absolute left-[0.57vw] top-[0.28vh]"
            src="../assets/icons/agregat/warning_sign.svg" />
        </div>
      </div>

      <div class="flex flex-col">
        <div
          class="rounded-tr-0 rounded-br-0 mt-[1.48vh] ml-[0.50vw] flex h-[2.9vh] w-[8.1vw] items-center rounded-tl-3xl rounded-bl-3xl bg-[#272933]">
          <div class="ml-[0.83vw] truncate font-euclid text-[0.94vw] font-medium text-[#D6EBFF]">
            {{ data.name }}
          </div>
        </div>

        <div class="ml-[0.47vw] mt-[1.46vh] flex flex-col">
          <div v-for="item in data.params" class="flex h-[1.4vh] flex-row gap-[0.52vw]">
            <div class="flex w-[3.96vw] items-center justify-end text-[0.625vw] text-[#D6EBFF]">
              <div class="overflow-hidden">{{ item.name }}</div>
              :
            </div>
            <div
              :style="{ color: changeStateColor() }"
              class="flex w-[2.86vw] items-center gap-[0.15vw] text-[0.73vw] text-[#66FE87]">
              <div class="overflow-hidden whitespace-nowrap">{{ item.value }}</div>
              <div class="w-[1.5vw] overflow-hidden whitespace-nowrap">
                {{ item.type }}
              </div>
            </div>
          </div>
        </div>

        <div class="mt-[1.2vh] ml-[6vw] flex flex-row items-center gap-[0.2vw]">
          <div
            class="flex h-[0.93vh] w-[0.68vw] items-center overflow-hidden truncate text-center font-euclid text-[0.42vw] font-medium text-[#35D1C8]">
            WB
          </div>
          <img src="../assets/icons/agregat/vector.svg" class="" />
          <div
            class="flex h-[0.93vh] w-[0.68vw] items-center overflow-hidden truncate text-center font-euclid text-[0.42vw] font-medium text-[#33C300]">
            ON
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
