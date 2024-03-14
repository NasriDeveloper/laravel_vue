<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import ParNavHeader from "./ParNavHeader.vue";
import ParSidebar from "./ParSidebar.vue";
import { ref } from 'vue';
import { Head, Link, router } from '@inertiajs/vue3';
import ApplicationMark from '@/Components/ApplicationMark.vue';
import Banner from '@/Components/Banner.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';

defineProps(["repons"]);




const showingNavigationDropdown = ref(false);

const switchToTeam = (team) => {
    router.put(route('current-team.update'), {
        team_id: team.id,
    }, {
        preserveState: false,
    });
};

const logout = () => {
    router.post(route('logout'));
};

</script>

<template>
    
<AppLayout title="Dash">




<body>
    <!--== MAIN CONTRAINER ==-->
 
 <ParNavHeader />
                                 


    <!--== BODY CONTNAINER ==-->
    <div class="container-fluid sb2">
        <div class="row">
           
           <ParSidebar />
            <!--== BODY INNER CONTAINER ==-->
            <div class="sb2-2">
                <!--== breadcrumbs ==-->
                <div class="sb2-2-2">
                    <ul>
                        <li><a href="/repot"><i class="fa fa-home" aria-hidden="true"></i> Parent Dashboard</a>
                        </li>
                        <li class="active-bre"><a href="/repot"> Welcome </a>
                        </li>
                        <li class="page-back"><a href="/repot"><i class="fa fa-backward" aria-hidden="true"></i> Back</a>
                        </li>
                    </ul>
                </div>


                <div class="sb2-2-3">
                    <div class="row">
                        <div class="col-md-12">
                          <div class="box-inn-sp admin-form">
    <div class="inn-title">
         <h4>Student Details</h4>
         <p>Enter student details here</p>
    </div>
            <div class="tab-inn">
                <div class="table-responsive table-desi" style="overflow-y: auto;">
                   <div class="free-iframe">
                         <iframe v-for="repon in repons" :key="repon.id" :src="repon.pdp" alt="PDF" class="img-fluid" width="1000" height="1700"></iframe>
                   </div>
                 </div>
             </div>
           </div>

                        </div>
                    </div>
                </div>


         
            </div>

        </div>
    </div>

    <!--Import jQuery before materialize.js-->
  
   
</body>


</AppLayout>

</template>

<style>



.img-fluid {
 width: 1000;
 height: 1200;
}
</style>
