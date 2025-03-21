<script setup>

const stats = [
            { value: '1 000 км+', description: 'прокладено кабелю' },
            { value: '10 000 камер+', description: 'встановлено' },
            { value: '10 років+', description: 'роботи' },
            { value: '100 %', description: 'надійності' },
            { value: '4.9', description: 'рейтинг компанії Google' }
    ];

    const services = [
  { name: "Відеонагляд", to: "/", img_src: "/images/cctv.jpg", img_alt: "камера відеоспостереження" },
  { name: "Охорона сигналізація", to: "/", img_src: "/images/security-alarm.jpg", img_alt: "сигналізація" },
  { name: "Пожежна сигналізація", to: "/", img_src: "/images/fire-alarm.jpg", img_alt: "пожежна безпека" },
  { name: "Домофонія", to: "/", img_src: "/images/intercom.jpg", img_alt: "відеодомофон" },
  { name: "Контроль доступу", to: "/", img_src: "/images/control-access.jpg", img_alt: "система контролю доступу" },
  { name: "Автоматика воріт", to: "/", img_src: "/images/automatic-gates.jpg", img_alt: "автоматика відкатних та розпашних воріт" },
  { name: "Розумний будинок", to: "/", img_src: "/images/smart-home.jpg", img_alt: "система розумного будинку" },
  { name: "Мережеві рішення", to: "/", img_src: "/images/internet.jpg", img_alt: "інтернет рішення" },
  { name: "Електрика", to: "/", img_src: "/images/electric.jpg", img_alt: "прокладка електрики" },
  { name: "Шлагбауми", to: "/", img_src: "/images/barrier.jpg", img_alt: "встановлення шлагбаума" },
  { name: "Кліматичні системи", to: "/", img_src: "/images/conditioning.jpg", img_alt: "встановлення кондиціонеру" },
];

const steps = [
  {
    title: 'Консультація',
    description: '',
  }, {
    title: 'Проектування',
    description: '',
  }, {
    title: 'Підбір обладнання',
    description: ''
  },
  {
    title: 'Монтаж',
    description: ''
  }, {
    title: 'Навчання',
    description: ''
  }, {
    title: 'Підтримка',
    description: ''
  }
]

</script>


<template>
    <div>
        <UContainer>
            <div class="lg:flex gap-3 items-center justify-between">
                <div>
                    <h1 class="text-3xl font-medium">Повний цикл робіт із систем безпеки — від задуму до реалізації</h1>
                    <p class="text-lg text-primary-500 font-light">Потрібна порада щодо безпеки? Надішліть заявку та отримайте безкоштовну консультацію!</p>
                </div>
                <div class="text-center">   
                    <NuxtImg src="/sphere.gif" class="m-auto w-full" alt="красива сфера" />
                    <p class="text-gray-200">*тут має бути відео нашої роботи, але воно ще не готове</p>
                </div>
            </div>
        </UContainer>
    </div>

    <div class="my-20">
        <UContainer class="text-center">
            <UBadge variant="outline" size="lg">Про нас у цифрах</UBadge>
            <ul class="grid lg:grid-cols-5 grid-cols-1 gap-5 justify-between items-center mt-8">
                <li class="flex flex-col p-4 bg-gray-50 dark:bg-gray-800 rounded-lg" v-for="stat in stats"><h1 class="text-primary-500 text-xl lg:text-3xl font-medium">{{ stat.value }}</h1><p class="lg:text-lg">{{ stat.description }}</p></li>
            </ul>
        </UContainer>
    </div>

    <div class="my-20">
        <UContainer class="text-center">
            <UBadge variant="outline" size="lg">Наші послуги</UBadge>
            <ul class="mt-7 grid grid-cols-2 lg:grid-cols-4 gap-2">
                <li v-for="service in services" :key="service.to">
                            <NuxtLink :to="service.to" class="block group">
                              <div class="relative overflow-hidden rounded-lg shadow-md">
                                <NuxtImg :src="service.img_src" :alt="service.img_alt" class="w-full h-50 object-cover transition-transform duration-300 ease-in-out group-hover:scale-105"/>
                                <div class="absolute bottom-0 left-0 w-full bg-black/50 text-white p-3 flex items-center justify-between transition-all duration-300 ease-in-out group-hover:bg-black/80">
                                  <span class="text-sm font-semibold transition-colors group-hover:text-primary">{{ service.name }}</span>
                                  <UIcon name="material-symbols:arrow-forward" class="w-4 h-4 transition-transform group-hover:scale-110 group-hover:text-primary group-hover:rotate-45" />
                                </div>
                              </div>
                            </NuxtLink>
                </li>
            </ul>
        </UContainer>
    </div>

    <div class="my-20">
  <UContainer class="text-center">
    <UBadge variant="outline" size="lg">Як ми працюємо?</UBadge>
    <UStepper
      orientation="vertical"
      size="lg"
      ref="stepper"
      :items="steps"
      class="w-full flex flex-col max-w-4xl lg:flex-row mx-auto whitespace-nowrap"
    >
      <template #content="{ item }">
        <div class="flex items-center">
          <span class="text-lg font-medium">{{ item.title }}</span>
        </div>
      </template>
    </UStepper>
  </UContainer>
</div>

</template>