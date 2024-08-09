<template>
  <div class="grid gap-4">
    <header class="flex items-start justify-between">
      <div class="grow">
        <p>Welcome back Wagto.</p>
        <h1>Dashboard</h1>
      </div>
      <div class="w-[120px] h-9 bg-neutral-200"></div>
    </header>
    <main class="grid gap-4">
      <Tabs default-value="account" class="w-full">
        <TabsList>
          <TabsTrigger
            v-for="(item, index) in list"
            :key="index"
            :value="item.title"
          >
            {{ item.title }}
          </TabsTrigger>
        </TabsList>
        <TabsContent
          id="account"
          class="w-full"
          v-for="(item, index) in list"
          :key="index"
          :value="item.title"
        >
          <ChartPie :options="chartOptions" />
        </TabsContent>
      </Tabs>
    </main>
    <footer>
      <div class="flex items-center gap-4">
        <div
          class="w-full h-[260px] bg-neutral-200"
          v-for="(item, index) in 3"
          :key="index"
        ></div>
      </div>
    </footer>
  </div>
</template>

<script setup>
const loading = ref(false);
let categories = ref({ today: [], week: [], month: [], year: [] });
let currentCategory = ref([
  "Jan",
  "Feb",
  "Mar",
  "Apr",
  "May",
  "Jun",
  "Jul",
  "Aug",
  "Sep",
  "Oct",
  "Nov",
  "Dec",
]);

const list = [
  { title: "Today", component: "<div>Today</div>" },
  { title: "Week", component: "<div>Week</div>" },
  { title: "Month", component: "<div>Month</div>" },
  { title: "Year", component: "<div>Year</div>" },
];

const options = computed(() => ({
  chart: {
    type: "line",
  },
  title: {
    text: "Monthly Average Temperature",
  },
  subtitle: {
    text: "Source",
  },
  xAxis: {
    categories: [
      "Jan",
      "Feb",
      "Mar",
      "Apr",
      "May",
      "Jun",
      "Jul",
      "Aug",
      "Sep",
      "Oct",
      "Nov",
      "Dec",
    ],
  },
  yAxis: {
    title: {
      text: "Temperature (°C)",
    },
  },
  plotOptions: {
    line: {
      dataLabels: {
        enabled: true,
      },
      enableMouseTracking: false,
    },
  },
  series: [
    {
      name: "Reggane",
      data: [
        16.0, 18.2, 23.1, 27.9, 32.2, 36.4, 39.8, 38.4, 35.5, 29.2, 22.0, 17.8,
      ],
    },
    {
      name: "Tallinn",
      data: [
        -2.9, -3.6, -0.6, 4.8, 10.2, 14.5, 17.6, 16.5, 12.0, 6.5, 2.0, -0.9,
      ],
    },
  ],
}));

const chartOptions = {
  title: {
    text: "ECharts örneği",
  },
  tooltip: {
    trigger: "item",
  },
  legend: {
    orient: "vertical",
    left: "left",
  },
  series: [
    {
      name: "ECharts örneği",
      type: "pie",
      radius: "50%",
      data: [
        { value: 1048, name: "Kategori A" },
        { value: 735, name: "Kategori B" },
        { value: 580, name: "Kategori C" },
        { value: 484, name: "Kategori D" },
        { value: 300, name: "Kategori E" },
      ],
      emphasis: {
        itemStyle: {
          shadowBlur: 10,
          shadowOffsetX: 0,
          shadowColor: "rgba(0, 0, 0, 0.5)",
        },
      },
    },
  ],
};
</script>
