<template>
  <div>
    <div class="flex flex-wrap mt-4 gap-4">
      <div
        class="card max-h-[420px] p-4 bg-white rounded-xl shadow-lg text-gray-600 mb-2 w-full lg:w-1/3 overflow-auto"
      >
        <div class="flex justify-between items-center mb-4">
          <h1 class="text-lg">Details</h1>
        </div>
        <div
          v-for="(value, key) in details"
          :key="key"
          class="flex justify-start gap-12 text-sm py-[6px] border-b-[1px]"
        >
          <p class="capitalize w-24">{{ key.replace("_", " ") }}</p>
          <p class="font-bold">{{ value }}</p>
        </div>
      </div>
      <div
        class="card p-4 bg-white rounded-xl shadow-lg text-gray-600 mb-2 w-full lg:w-auto max-h-[420px] lg:grow overflow-auto"
      >
        <div class="flex justify-between items-center mb-4">
          <h1 class="text-lg">Last Location</h1>
          <p class="text-[12px] underline">See more</p>
        </div>
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d14125.620960757906!2d106.82544110611863!3d-6.538317562071019!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e69c1f16d898121%3A0x3e38ea30691d94a8!2sSAMSAT%20Cibinong%20Bogor!5e0!3m2!1sid!2sid!4v1738730425290!5m2!1sid!2sid"
          height="450"
          style="border: 0"
          allowfullscreen=""
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          class="rounded-lg"
        ></iframe>
      </div>
    </div>
    <div class="flex flex-wrap mt-2 gap-4">
      <div
        class="card max-h-[420px] p-4 bg-white rounded-xl shadow-lg text-gray-600 mb-2 w-full lg:w-1/3 overflow-auto"
      >
        <div class="flex justify-between items-center mb-4">
          <h1 class="text-lg">Driver Behavior</h1>
          <p class="text-[12px] underline">See more</p>
        </div>
        <h2 class="text-[18px] mb-2">{{ behavior.trip }} Trips</h2>
        <div class="flex gap-6 mb-4">
          <h2 class="mb-2 text-4xl font-bold">
            {{ ((behavior.trip / 30) * 100).toFixed(1) }} %
          </h2>
          <div class="text-center">
            <div
              class="badge badge-outline font-bold"
              :class="{
                'badge-error': lastMonth > behavior.trip,
                'badge-success': lastMonth <= behavior.trip,
              }"
            >
              {{
                (((lastMonth - behavior.trip) / lastMonth) * 100 * -1).toFixed()
              }}
              %
            </div>
            <p>vs last month</p>
          </div>
        </div>
        <div>
          <progress
            class="progress progress-success w-full h-6"
            :value="((behavior.trip / 30) * 100).toFixed(1)"
            max="100"
          ></progress>
        </div>
        <div class="flex flex-wrap gap-3 justify-start">
          <div
            v-for="(value, key) in behavior.data"
            :key="key"
            class="w-[45%] flex items-center gap-2"
          >
            <div
              class="w-8 h-8 flex items-center justify-center rounded-md bg-gray-200"
            >
              <span class="font-bold">{{ value }}</span>
            </div>
            <p class="capitalize">{{ key.replace("_", " ") }}</p>
          </div>
        </div>
      </div>
      <div
        class="card p-4 bg-white rounded-xl shadow-lg text-gray-600 mb-2 w-full lg:w-auto max-h-[420px] lg:grow overflow-auto"
      >
        <div class="flex justify-between items-center mb-4">
          <h1 class="text-lg">Driver Activity Timeline</h1>
        </div>
        <div v-for="(item, index) in timeline" :key="index">
          <div class="flex items-top justify-between">
            <div class="flex items-start gap-2">
              <div class="mt-[2px] flex flex-col items-center">
                <Icon
                  name="fa6-solid:circle"
                  :class="{
                    'text-yellow-400': item.status == 1,
                    'text-purple-400': item.status == 2,
                    'text-red-400': item.status == 3,
                  }"
                />
                <div class="min-h-8 border-s-2 mt-2"></div>
              </div>
              <div>
                <h2>{{ item.title }}</h2>
                <p class="py-2">{{ item.desc }}</p>
              </div>
            </div>

            <div>
              {{ dayjs(item.date).fromNow() }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
  
<script setup lang="ts">
import { useDayjs } from "#dayjs";

const dayjs = useDayjs();

const details = {
  name: "Asep Gunawan",
  phone: "0813833610802",
  email: "asep@gmail.com",
  fleet_group: "Balaraja",
  employment: "Part-Time",
  vehicle: "B-1234-VCE",
  status: "Moving",
};

const timeline = [
  {
    status: 3,
    title: "12 Invoices have been paid",
    date: "2025-02-05 12:08:04",
    desc: "Invoices have been paid to the company",
  },
  {
    status: 2,
    title: "Meeting with john",
    date: "2025-02-05 10:08:04",
    desc: "Project meeting with jhon @10.15",
  },
  {
    status: 1,
    title: "Create a new react project for client",
    date: "2025-02-01 19:08:04",
    desc: "5 team member in a project",
  },
  {
    status: 1,
    title: "Create a new golang project for client",
    date: "2025-01-31 19:08:04",
    desc: "5 team member in a project",
  },
];

const lastMonth = 35;
const behavior = {
  trip: 28,
  data: {
    overspeed: 24,
    harsh_acc: 50,
    harsh_blake: 12,
    harsh_cornering: 38,
    overstay: 12,
    geofencne_out: 18,
  },
};
</script>
  