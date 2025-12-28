<template>
  <div class="app-container  w-full min-h-screen  pb-5 lg:pt-3 px-5"
  :class="isDark ? 'bg-[#091540] text-white' : 'bg-[#d6e2f5ff] text-black'">
    <div class="flex flex-col w-full">
        <!-- Header -->
      <header class="header border rounded-[10px] bg-[#f7f7f8ff] my-3 mx-2">
        <div class="flex justify-between items-center  py-[10px]">
            <img src="./assets/images/logo.svg" alt="logo" class="pl-[9px]"/>
            <div @click="toggleTheme" class="w-10 h-10 border rounded-[15px] bg-[#c7c7c7ff] flex justify-center items-center mr-[1rem]">
              <img src="./assets/images/icon-moon.svg" alt="Dark mode" v-if="!isDark" class="py-1rem px-1rem " />
              <img src="./assets/images/icon-sun.svg" alt="Light mode" v-else class="py-1rem px-1rem" />
            </div>
        </div>
      </header>

      <!-- Main content area -->
      <main class="content w-full">
        <div class="flex flex-col justify-center items-center lg:flex-row justify-between px-4">
          <h1 class="text-[30px] font-bold">Extensions List</h1>

          <div class="btn-filter flex flex-row items-center gap-[1rem] mt-4 lg:gap-3 ">
            <button @click="setFilter('all')" :class="filter === 'all' ? 'bg-[#f25c54ff] text-white': 'bg-[#f7f7f8ff] text-black'" class=" text-[20px]  border rounded-[18px] px-4 py-1 transition">All</button>
            <button @click="setFilter('active')" :class="filter === 'active' ? 'bg-[#f25c54ff] text-white': 'bg-[#f7f7f8ff] text-black'" class=" text-[20px] border rounded-[18px] px-4 py-1 transition">Active</button>
            <button @click="setFilter('inactive')" :class="filter === 'inactive' ? 'bg-[#f25c54ff] text-white': 'bg-[#f7f7f8ff] text-black'" class=" text-[20px] border rounded-[18px] px-4 py-1 transition">Inactive</button>
          </div>
        </div>

        <div class="flex flex-col min-h-screen w-full px-4 lg:grid grid-cols-3 gap-3 ">
          <ExtensionCard
            v-for="ext in filteredExtensions"
            :key="ext.id"
            v-bind="ext"
            :isDark="isDark"
            @toggle="toggleExtension(ext.id)"
            @remove ="removeExtension(ext.id)"
          
          />
        </div>
      </main>
    </div>
    
  </div>
</template>

<script setup>
import ExtensionCard from './components/ExtensionCard.vue';
import { ref } from 'vue';
import { computed } from 'vue';

//Import logos

import DevLensLogo from './assets/images/logo-devlens.svg'
import StyleSpyLogo from './assets/images/logo-style-spy.svg'
import SpeedBoostLogo from './assets/images/logo-speed-boost.svg'
import JsonWizardLogo from './assets/images/logo-json-wizard.svg'
import TabMasterLogo from './assets/images/logo-tab-master-pro.svg'
import ViewportBuddyLogo from './assets/images/logo-viewport-buddy.svg'
import MarkupNotes from './assets/images/logo-markup-notes.svg'
import GridGuides from './assets/images/logo-grid-guides.svg'
import PalettePicker from './assets/images/logo-palette-picker.svg'
import LinkChecker from './assets/images/logo-link-checker.svg'
import DomSnapshot from './assets/images/logo-dom-snapshot.svg'
import ConsolePlus from './assets/images/logo-console-plus.svg'


const extensions = ref([
  {
    id: 1,
    name: 'DevLens',
    description: 'Quickly inspect page layouts and visualize element boundaries.',
    logo: DevLensLogo,
    enabled: true,
  },
  {
    id: 2,
    name: 'StyleSpy',
    description: 'Instantly analyze and copy CSS from any webpage element.',
    logo: StyleSpyLogo,
    enabled: false,
  },
  {
    id: 3,
    name: 'SpeedBoost',
    description: 'Optimizes browser resource usage to accelerate page loading.',
    logo: SpeedBoostLogo,
    enabled: true,
  },
  {
    id: 4,
    name : 'JSONWizard',
    description: "Formats, validate, and prettifies JSON responses in browser.",
    logo: JsonWizardLogo,
    enabled: true,
  },
  {
    id: 5,
    name : 'TabMater Pro',
    description:"Organizes browser tabs into groups and sessions.",
    logo: TabMasterLogo,
    enabled: true,
  },
  {
    id: 6,
    name : 'ViewportBuddy',
    description:"Simulates various screen resolutions directly with in the browser.",
    logo: ViewportBuddyLogo,
    enabled: true,
  },
  {
    id: 7,
    name : 'Markup Notes',
    description:"Enables annotation and notes directly onto webpages for collaborative debugging.",
    logo: MarkupNotes,
    enabled: false,
  },
  {
    id: 8,
    name : 'Grid Guides',
    description:"Overlay customizable grids and alignment guides on any webpage.",
    logo: GridGuides,
    enabled: false,
  },
  {
    id: 9,
    name : 'LinkChecker',
    description:"Scans and highlights broken links on any page.",
    logo: LinkChecker,
    enabled: true,
  },
  {
    id: 10,
    name : 'PalettePicker',
    description:"Instantly extracts color palattes from any webpage.",
    logo: PalettePicker,
    enabled: false,
  },
  {
    id:11,
    name : 'DOM Snapshot',
    description:"Capture and export DOM structures quickly.",
    logo: DomSnapshot,
    enabled: true,
  },
  {
    id: 12,
    name : 'ConsolePlus',
    description:"Enhanced developer console with advanced filtering and logging.",
    logo: ConsolePlus,
    enabled: false,
  },
])


function toggleExtension(id) {
  const ext = extensions.value.find(e => e.id === id)
  if (ext) {
    ext.enabled = !ext.enabled
  }
}


function removeExtension(id) {
  extensions.value = extensions.value.filter(ext => ext.id !== id)
}

function setFilter(value) {
  filter.value = value
}

const filter =ref('all')

const filteredExtensions =computed(() =>{
  if (filter.value === 'active') {
    return extensions.value.filter(ext => ext.enabled)
  }
  if (filter.value === 'inactive') {
    return extensions.value.filter(ext => !ext.enabled)
  }
  return extensions.value
})


const isDark = ref(false)

function toggleTheme() {
  isDark.value = !isDark.value
}

</script>

<style>

</style>
