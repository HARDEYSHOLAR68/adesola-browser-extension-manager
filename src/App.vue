<template>
  <div class="app-container  w-full min-h-screen  bg-[#d6e2f5ff] pb-5">
    <div class="flex flex-col w-full">
        <!-- Header -->
      <header class="header border rounded-[10px] bg-[#f7f7f8ff] my-3 mx-2">
        <div class="flex justify-between items-center  py-[10px]">
            <img src="./assets/images/logo.svg" alt="logo" class="pl-[9px]"/>
            <div class="w-10 h-10 border rounded-[15px] bg-[#c7c7c7ff] flex justify-center items-center mr-[1rem]">
              <img src="./assets/images/icon-moon.svg" alt="toggle" class="py-1rem px-1rem " />
            </div>
        </div>
      </header>

      <!-- Main content area -->
      <main class="content w-full">
        <div class="flex flex-col justify-center items-center">
          <h1 class="text-[30px] font-bold">Extensions List</h1>

          <div class="btn-filter flex flex-row items-center gap-[1rem] mt-4 ">
            <button class="all text-[20px]  border rounded-[18px] px-4 py-1 bg-[#f7f7f8ff]">All</button>
            <button class="active text-[20px] border rounded-[18px] px-4 py-1 bg-[#f7f7f8ff]">Active</button>
            <button class="inactive text-[20px] border rounded-[18px] px-4 py-1 bg-[#f7f7f8ff]">Inactive</button>
          </div>
        </div>

        <div class="flex flex-col min-h-screen w-full px-4">
          <ExtensionCard
            name = "DevLens"
            description="Quickly inspect page layouts and visualize element boundaries."
            :logo="DevLensLogo"
            :isActive="true"
          />

          <ExtensionCard
            name = "StyleSpy"
            description="Instantly anaylyze and copy CSS from any webpage element."
            :logo="StyleSpyLogo"
            :enabled="false"
          />

          <ExtensionCard
            name = "SpeedBoost"
            description="Optimizes browser resource usage to accelerate page loading."
            :logo="SpeedBoostLogo"
            :enabled="true"
          />


          <ExtensionCard
            name = "JSONWizard"
            description="Formats, validate, and prettifies JSON responses in browser."
            :logo="JsonWizardLogo"
            :enabled="true"
          />


          <ExtensionCard
            name = "TabMater Pro"
            description="Organizes browser tabs into groups and sessions."
            :logo="TabMasterLogo"
            :enabled="true"
          />


          <ExtensionCard
            name = "ViewportBuddy"
            description="Simulates various screen resolutions directly with in the browser."
            :logo="ViewportBuddyLogo"
            :enabled="true"
          />


          <ExtensionCard
            name = "Markup Notes"
            description="Enables annotation and notes directly onto webpages for collaborative debugging."
            :logo="MarkupNotes"
            :enabled="false"
          />


          <ExtensionCard
            name = "Grid Guides"
            description="Overlay customizable grids and alignment guides on any webpage."
            :logo="GridGuides"
            :enabled="false"
          />


          <ExtensionCard
            name = "Palette Picker"
            description="Instantly extracts color palettes from any webpage."
            :logo="PalettePicker"
            :enabled="false"
          />


          <ExtensionCard
            name = "LinkChecker"
            description="Scans and highlights broken links on any page."
            :logo="LinkChecker"
            :enabled="false"
          />


          <ExtensionCard
            name = "DOM Snapshot"
            description="Capture and export DOM structures quickly."
            :logo="DomSnapshot"
            :enabled="false"
          />


          <ExtensionCard
            name = "ConsolePlus"
            description="Enhanced developer console with advanced filtering and logging."
            :logo="ConsolePlus"
            :enabled="false"
          />
        </div>
      </main>
    </div>
    
  </div>
</template>

<script setup>
import ExtensionCard from './components/ExtensionCard.vue';
import { ref } from 'vue';

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

const isActive = ref(false)

function removeItem() {
  console.log("Item removed");
}

</script>

<style>

</style>
