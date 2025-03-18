<script setup>

    const colorMode = useColorMode()

    const isDark = computed({
    get() {
        return colorMode.value === 'dark'
    },
    set() {
        colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
    }
    })

    const links = [
  { name: "Рішення", to: "/solutions" },
  { name: "Об'єкти", to: "/objects" },
  { name: "Компанія", to: "/company" },
  { name: "FAQ", to: "/faq" },
  { name: "Контакти", to: "/contacts" },
];

const brands_header = [
  { src: 'brands/ajax-logo.svg', to: '/' },
  { src: 'brands/dahua-logo.svg', to: '/' },
  { src: 'brands/hikvision-logo.svg', to: '/' },
  { src: 'brands/imou-logo.svg', to: '/' },
  { src: 'brands/mikrotik-logo.svg', to: '/' },
  { src: 'brands/zkteco-logo.svg', to: '/' },
  { src: 'brands/steelon-logo.svg', to: '/' },
  { src: 'brands/neolight-logo.svg', to: '/' },
  { src: 'brands/neoclima-logo.svg', to: '/' },
  { src: 'brands/ezviz-logo.svg', to: '/' },
  { src: 'brands/yli-logo.svg', to: '/' },
  { src: 'brands/tiras-logo.svg', to: '/' }
];
const services = [
      { name: "Відеонагляд", to: "/", img_src: "/images/cctv.jpg", img_alt: "камера відеоспостереження" },
      { name: "Охорона сигналізація", to: "/", img_src: "/images/security-alarm.jpg", img_alt: "сигналізація" },
      { name: "Пожежна сигналізація", to: "/", img_src: "/images/fire-alarm.jpg", img_alt: "пожежна безпека" },
      { name: "Домофонія", to: "/", img_src: "/images/intercom.jpg", img_alt: "відеодомофон" },
      { name: "Контроль доступу", to: "/", img_src: "/images/control-access.jpg", img_alt: "система контролю доступу" },
      { name: "Автоматика воріт", to: "/", img_src: "/images/automatic-gates.jpg", img_alt: "автоматика відкатних та розпашних воріт" },
      { name: "Розумний будинок", to: "/", img_src: "/images/smart-home.jpg", img_alt: "система розумного будинку" },
      { name: "Мережеві рішення", to: "/", img_src: "/images/internet.jpg", img_alt: "інтернет рішення" }
];

const other_services = [
      { name: "Електрика", to: "/" },
      { name: "Шлагбауми", to: "/" },
      { name: "Кліматичні системи", to: "/" }
];

const socials = [
      {icon: "skill-icons:instagram", to: "https://www.instagram.com/bezpeka.center/"},
      {icon: "logos:facebook", to: "https://www.facebook.com/bezpeka.center.nv"},
      {icon: "logos:youtube-icon", to: "https://www.youtube.com/@bezpeka.center"},
      {icon: "logos:tiktok-icon", to: "https://www.tiktok.com/"}
];

</script>

<template>
    <header class="border-b border-gray-100 p-4">
        <UContainer >
            <div class="flex items-center justify-between">
            
                <ULink to="/"><Logo class="text-black dark:text-white transition-colors hover:text-gray-500" /></ULink>    
                <UModal>
                    <UButton icon="heroicons:device-phone-mobile" size="lg">
                        Залишити заявку
                    </UButton>
                    <template #content>
                        
                    </template>
                </UModal>
                
                <ul class="flex gap-5 items-center">
                    <UPopover>
                        <UButton variant="outline" trailing-icon="heroicons:wrench-screwdriver">
                        Послуги
                        </UButton>
                        <template #content>
                            <div class="w-screen flex justify-between gap-12">
                               
                                <div class="flex flex-col justify-between py-3 gap-3">
                  <div class="header-brands">
                        <h1 class="text-2xl mb-4">Бренди</h1>
                        <ul class="grid grid-cols-3 gap-7 items-center">
                            <li v-for="brand_header in brands_header" :key="brand_header.to">
                              <NuxtLink :to="brand_header.to"><NuxtImg class="w-28 h-auto" :src="brand_header.src" /></NuxtLink>
                            </li>
                        </ul>
                  </div>
                  <div class="header-soc">
                        <h1 class="text-2xl mb-4">Ми в соціальних мережах</h1>
                        <ul class="flex items-center gap-5">
                              <li v-for="social in socials" :key="social.to"><a :href="social.to" target="_blank"><UIcon  :name="social.icon" class="w-8 h-8 transition-color hover:text-primary"/></a></li>
                        </ul>
                  </div>
                </div>  

                <div class="w-[75%]">
                        <ul class="grid grid-cols-4 gap-5">
                              <li v-for="service in services" :key="service.to">
                                    <NuxtLink :to="service.to" class="block group">
                                          <div class="relative overflow-hidden">
                  
                                                <NuxtImg :src="service.img_src" :alt="service.img_alt" class="w-full h-full object-cover transition-transform duration-300 ease-in-out group-hover:scale-105"/>
                                                
                                                <div class="absolute bottom-0 left-0 w-full bg-black/50 text-white p-3 flex items-center justify-between transition-all duration-300 ease-in-out group-hover:bg-black/80">
                                                      <span class="text-sm font-semibold transition-colors duration-300 group-hover:text-primary">{{ service.name }}</span>
                                                      <UIcon name="material-symbols:arrow-forward" class="w-5 h-5 transition-transform duration-300 group-hover:scale-110 group-hover:text-primary group-hover:rotate-45" />
                                                </div>
                                          </div>
                                    </NuxtLink>

                              </li>
                        </ul>
                        <div class="header-boxs_other flex mt-4 text-white items-center gap-20">
                                    <ul class="grid grid-cols-3 w-full gap-10">
                                          <li v-for="other_service in other_services" :key="other_service.to" >
                                                <NuxtLink :to="other_service.to" class="bg-black/50 text-white p-3 flex items-center justify-between group">
                                                  <span class="text-sm font-semibold transition-colors duration-300 group-hover:text-primary">{{ other_service.name }}</span>
                                                      <UIcon name="material-symbols:arrow-forward" class="w-5 h-5 transition-transform duration-300 group-hover:scale-110 group-hover:text-primary group-hover:rotate-45" />
                                                </NuxtLink>
                                          </li>
                                    </ul>
                        </div>
                  </div>

                            </div>
                        </template>
                    </UPopover>
                    <li v-for="link in links">
                        <NuxtLink :to="link.to" class="relative inline-block after:absolute after:bottom-0 after:left-0 after:w-0 after:h-[2px] after:bg-current after:transition-all after:duration-300 hover:after:w-full">
                            {{ link.name }}
                        </NuxtLink>
                    </li>
                </ul>

                <UButton
                :icon="isDark ? 'i-lucide-moon' : 'i-lucide-sun'"
                color="neutral"
                variant="ghost"
                @click="isDark = !isDark"
                />

            </div>
        </UContainer>
    </header>
</template>