﻿<script setup>

import HomeCards from "@/components/HomeCards.vue";
import Hero from "@/components/Hero.vue";
import JobListings from "@/components/JobListings.vue";
</script>

<template>
  <Hero />
  <HomeCards />
  <JobListings :limit="3" :show-button="true"/>
</template>

<style scoped>

</style>
