<script setup>
import { ref, watch } from 'vue'
import { useRoute } from 'vue-router'

const openBurgerMenu = ref(false)
const route = useRoute()

// Закриваємо UDrawer при зміні маршруту
watch(() => route.path, () => {
  openBurgerMenu.value = false
})

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
    <header class="border-b border-gray-100 py-4">
        <UContainer>
            <div class="flex items-center justify-between gap-2">
            
                <ULink to="/"><Logo class="text-black dark:text-white transition-colors hover:text-gray-500" /></ULink>    
                <UModal title="Безкоштовна консультація">
                    <UButton icon="heroicons:device-phone-mobile" label="Залишити заявку" size="lg" class="hidden lg:flex items-align gap-2" />
                    <template #body>
                      <div class="m-auto">
                              <UForm class="flex flex-col gap-2">
                                <UFormField label="Ім'я" required>
                                  <UInput placeholder="Ваше ім'я" class="w-full" />
                                </UFormField>
                                <UFormField label="Телефон" required>
                                  <UInput placeholder="+380 (XX) XXX XX XX" class="w-full" />
                                </UFormField>
                                <UFormField label="Послуга" required>
                                  <USelectMenu :options="services" placeholder="Оберіть" class="w-full" />
                                </UFormField>
                                <UFormField label="Опис">
                                  <UTextarea placeholder="Ваше питання" class="w-full" />
                                </UFormField>
                                <UButton block color="primary" size="md" class="mt-3">Відправити</UButton>
                              </UForm>
                            </div>      
                    </template>
                </UModal>
                
                <ul class="hidden lg:flex gap-5 items-center">
                  <UPopover :popper="{ placement: 'bottom-start', strategy: 'fixed' }">
                    <UButton variant="outline" trailing-icon="heroicons:wrench-screwdriver">
                      Послуги
                    </UButton>
  
                <template #content>
                  <div class="w-screen max-w-full bg-white/10 dark:bg-gray-500/50 backdrop-blur-md rounded-lg p-5">
                    <div class="flex flex-wrap gap-12 justify-center">

                      <div class="w-full md:w-3/4">
                        <ul class="grid grid-cols-2 md:grid-cols-4 gap-4">
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

          
                      <div class="header-boxs_other flex mt-5 text-white items-center gap-4">
                        <ul class="grid grid-cols-2 md:grid-cols-3 w-full gap-4">
                          <li v-for="other_service in other_services" :key="other_service.to">
                            <NuxtLink :to="other_service.to" class="group bg-black/50 text-white p-3 flex items-center justify-between rounded-lg transition-all hover:bg-black/80">
                              <span class="text-sm font-semibold transition-colors group-hover:text-primary">{{ other_service.name }}</span>
                              <UIcon name="material-symbols:arrow-forward" class="w-4 h-4 transition-transform group-hover:scale-110 group-hover:text-primary group-hover:rotate-45" />
                            </NuxtLink>
                          </li>
                        </ul>
                      </div>
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
                class="hidden lg:block"
                />
                
                <UDrawer direction="right" v-model:open="openBurgerMenu">
                  <UButton color="neutral" variant="ghost" size="xl" icon="i-lucide-menu" class="lg:hidden" />

                  <template #content>
                    <div class="w-96 h-full flex flex-col gap-5 justify-between p-4 overflow-y-auto">
                      
                      <ul>
                        <li class="py-2">
                            <UCollapsible class="flex flex-col w-full gap-2">
                                <UButton
                                size="3xl"
                                label="Послуги"
                                variant="ghost"
                                trailing-icon="i-lucide-chevron-down"
                                class="group text-3xl font-normal text-muted gap-1 items-center"
                                :ui="{
                                  trailingIcon: 'group-data-[state=open]:rotate-180 transition-transform duration-200'
                                }"
                                />

                                <template #content class="w-full">
                                  <ul class="text-2xl w-full">
                                      <li v-for="service in services" class="py-1"><NuxtLink to="service.to">{{ service.name }}</NuxtLink></li>
                                  </ul>
                                </template>
                            </UCollapsible>
                        </li>
                        
                        <li v-for="link in links" class="text-3xl flex flex-col w-full py-2">
                          <ULink :to="link.to">{{ link.name }}</ULink>
                        </li>
                      </ul>


                    <div class="mt-auto flex flex-col gap-4">  
                      <ul class="flex items-center gap-6">
                        <li v-for="social in socials"><a :href="social.to" target="_blank"><UIcon  :name="social.icon" class="w-8 h-8 transition-color hover:text-primary"/></a></li>
                      </ul>
                      
                      <div class="flex justify-between">
                        <UModal title="Безкоштовна консультація">
                          <UButton icon="heroicons:device-phone-mobile" size="xl">
                            Залишити заявку
                          </UButton>
                          <template #body>
                            <div class="m-auto">
                              <UForm class="flex flex-col gap-2">
                                <UFormField label="Ім'я" required>
                                  <UInput placeholder="Ваше ім'я" class="w-full" />
                                </UFormField>
                                <UFormField label="Телефон" required>
                                  <UInput placeholder="+380 (XX) XXX XX XX" class="w-full" />
                                </UFormField>
                                <UFormField label="Послуга" required>
                                  <USelectMenu :options="services" placeholder="Оберіть" class="w-full" />
                                </UFormField>
                                <UFormField label="Опис">
                                  <UTextarea placeholder="Ваше питання" class="w-full" />
                                </UFormField>
                                <UButton block color="primary" size="md" class="mt-3">Відправити</UButton>
                              </UForm>
                            </div>
                          </template>
                        </UModal>
                        <UButton
                                :icon="isDark ? 'i-lucide-moon' : 'i-lucide-sun'"
                                color="neutral"
                                variant="ghost"
                                @click="isDark = !isDark"
                                size="xl"
                        />
                      </div>
                    </div>
                    </div>
                  </template>
                </UDrawer>


            </div>
        </UContainer>
    </header>
</template>

<style>

.text-muted {
 color: oklch(0.55 0.05 257.42 / 1);
}


</style>