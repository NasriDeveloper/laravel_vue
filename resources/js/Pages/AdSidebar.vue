<script setup>
import Link from "./Link.vue";

const sidebarLinks = [
  { name: 'Dashboard', href: '/dashboard',  current: true },
  { name: 'All Users Registered', href: '/dash',  current: true },
  { name: 'Student Registration', href: '/reg', current: true },
  { name: 'Parent Registration', href: '/nasr', current: true },
  { name: 'Teacher Registration', href: '/teacher', current: true },
  { name: 'View Students', href: '/nas', current: true },
  { name: 'View Parents', href: '/viewp', current: true },
  { name: 'Report Upload1,2', href: '/reportT1', current: true },
  { name: 'Report Upload3,4,7', href: '/reportT', current: true },
  { name: 'Report Upload5,6', href: '/reportT5', current: true },
  { name: 'Report standard1', href: '/reportvT1', current: true },
  { name: 'Report standard2', href: '/reportvT2', current: true },
  { name: 'Report standard3', href: '/reportvT3', current: true },
  { name: 'Report standard4', href: '/reportvT4', current: true },
  { name: 'Report standard5', href: '/reportvT5', current: true },
  { name: 'Report standard6', href: '/reportvT6', current: true },
  { name: 'Report standard7', href: '/reportvT7', current: true },
  { name: 'Report Upload', href: '/uplo', current: true },
];
</script>



<template>
    <div class="sb2-1">
      <!--== USER INFO ==-->
      <div class="sb2-12">
        <ul>
          <li><img src="homes/img/logo/logo.png" alt=""></li>
          <li>
            <h5> GRACE SCHOOLS <span> kigamboni </span></h5>
          </li>
          <li></li>
        </ul>
      </div>
      <!--== LEFT MENU ==-->
      <div class="sb2-13">
        <ul class="collapsible" data-collapsible="accordion">
          
         <li><Link preserve-scroll v-for="link in sidebarLinks" :key="link.name" :href="link.href" :name="link.name" :component="link.name"></Link></li> 
        </ul>
      </div>
    </div>
  </template>
  