<script setup lang="ts">
import {ref, computed} from 'vue'

const year = ref(null);
const month = ref(null);
const day = ref(null);


function calculateAge() {

  const birthDate = new Date(`${year.value}-${month.value}-${day.value}`)
  const today = new Date()
  let years = today.getFullYear() - birthDate.getFullYear()
  let months = today.getMonth() - birthDate.getMonth()
  let days = today.getDate() - birthDate.getDate()

  if (months < 0 || (months === 0 && days < 0)) {
    years--
    months += 12
  }
  if (days < 0) {
    const lastMonth = new Date(today.getFullYear(), today.getMonth() - 1, 0)
    days += lastMonth.getDate()
    months--
  }
  return { years, months, days }
}

const age = computed(() => calculateAge())


</script>

<template>
  <main class="bg-[#f0f0f0] w-full h-screen flex px-[20px]">
    <section
      class="px-[30px]  py-[40px] md:pl-[40px] md:pr-0 rounded-t-[30px] rounded-bl-[20px] rounded-br-[100px] md:rounded-br-[190px] flex w-full sm:w-[80%] max-w-[650px] flex-col m-auto bg-[#ffffff]"
    >
      <form action="" class="flex justify-between lg:justify-start mb-[50px] lg:mb-0">
        <div class="w-[80px] lg:w-[130px] lg:mr-5">
          <label class="text-[#716f6f] text-[10px]" for="">DAY</label>
          <input
            class="font-[inter] mt-1 font-semibold text-center rounded-[5px] text-[38px]  w-full border-[1px] border-[#dbdbdb]"
            type="number"
            v-model="day"
            placeholder="DD"
            id=""
          />
        </div>
        <div class="w-[80px] lg:w-[130px] lg:mr-5">
          <label class="text-[#716f6f] text-[10px]" for="">MONTH</label>
          <input
            class="font-[inter] mt-1 font-bold text-center rounded-[5px] text-[38px] w-full border-[1px] border-[#dbdbdb]"
            type="number"
            v-model="month"
            placeholder="MM"
            id=""
          />
        </div>
        <div class="w-[80px] lg:w-[130px]">
          <label class="text-[#716f6f] text-[10px]" for="">YEAR</label>
          <input
            class="font-[inter] mt-1 font-bold text-center rounded-[5px] text-[38px] w-full border-[1px] border-[#dbdbdb]"
            type="number"
            v-model="year"
            placeholder="YYYY"
            id=""
          />
        </div>
      </form>

      <div class="relative flex items-center w-full mt-[10px]">
        <div class="bg-[#dbdbdb] w-full md:w-[80%] h-[1px]"></div>
        <div
          class="left-[42.5%] absolute lg:static flex justify-center items-center w-[50px] h-[50px] md:w-[70px] md:h-[70px] rounded-[50%] bg-[#854dff]"
        >
          <svg
            class="w-[25px] md:w-[100%]"
            xmlns="http://www.w3.org/2000/svg"
            width="46"
            height="44"
            viewBox="0 0 46 44"
          >
            <g fill="none" stroke="#FFF" stroke-width="2">
              <path
                d="M1 22.019C8.333 21.686 23 25.616 23 44M23 44V0M45 22.019C37.667 21.686 23 25.616 23 44"
              />
            </g>
          </svg>
        </div>
      </div>

      <div class="mt-[50px] lg:mt-0 text-[50px] md:text-[80px] leading-[1.1]">
        <div>
          <span v-if="!age.years" class="text-[#854dff]">- -</span>
          <span v-else class="text-[#854dff]">{{age.years}}</span>
          <span>years</span>
        </div>
        <div>
          <span v-if="!age.months" class="text-[#854dff]">- -</span>
          <span v-else class="text-[#854dff]">{{age.months}}</span>
          <span>months</span>
        </div>
        <div>
          <span v-if="!age.days" class="text-[#854dff]">- -</span>
          <span v-else class="text-[#854dff]">{{ age.days }}</span>
          <span>days</span>
        </div>
      </div>
    </section>
  </main>
</template>

<style></style>
