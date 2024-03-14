<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import AdNavHeade from "./AdNavHeade.vue";
import AdSidebar from "./AdSidebar.vue";
import { ref } from 'vue';
import { Head, Link, router } from '@inertiajs/vue3';
import ApplicationMark from '@/Components/ApplicationMark.vue';
import Banner from '@/Components/Banner.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';


const successMessage = ref('');

const deleteUse = (id) => {
  router.delete('/uters/' + id);
  successMessage.value = 'User has been successfully deleted.';
};

const editUse = (id) => {
  router.get('/uters/' + id + '/edit');
};



const props = defineProps({
    uters: Array
})



function closeSuccessMessage() {
    successMessage.value = '';
}

</script>

<template>
    
<AppLayout title="Dash">




<body>
    <!--== MAIN CONTRAINER ==-->
 
 <AdNavHeade />
                                 


    <!--== BODY CONTNAINER ==-->
    <div class="container-fluid sb2">
        <div class="row">
           
           <AdSidebar />
            <!--== BODY INNER CONTAINER ==-->
            <div class="sb2-2">
                <!--== breadcrumbs ==-->
                <div class="sb2-2-2">
                    <ul>
                        <li><a href="index-2.html"><i class="fa fa-home" aria-hidden="true"></i> Home</a>
                        </li>
                        <li class="active-bre"><a href="#"> Dashboard</a>
                        </li>
                        <li class="page-back"><a href="index-2.html"><i class="fa fa-backward" aria-hidden="true"></i> Back</a>
                        </li>
                    </ul>
                </div>
                <!--== DASHBOARD INFO ==-->
              

                <!--== User Details ==-->
                <div class="sb2-2-3">
    <div class="row">
        <div class="col-md-12">
            <div class="box-inn-sp">
                <div class="inn-title">
                    <h4>Student Details</h4>
                    <p>All about students like name, student id, phone, email, country, city, and more</p>
                </div>
                <div class="tab-inn">
                    
                                    <div v-if="successMessage" class="alert alert-danger mt-3">
                                            {{ successMessage }}
                                            <button @click="closeSuccessMessage" class="close" aria-label="Close">
                                                <span aria-hidden="true">&times;</span>
                                            </button>
                                        </div>
    <div class="table-responsive table-desi" style="overflow-x: auto;">
        <table class="table table-hover">
            <thead>
                <tr>
                    <th>Father Photo</th>
                    <th>Father Name</th>
                    <th>Father First Name</th>
                    <th>Class</th>
                    <th>Email</th>
                    <th>Father Address</th>
                    <th>Father Phone</th>
                    <th>Father Occupation</th>
                    <th>Father Education</th>
                    <th>Father NID</th>
                    <th>Father Religion</th>
                    <th>Actions</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="uter in uters" :key="uter.id">
                    <td>
                        <span class="list-img"><img :src="uter.fatherPhoto"></span>
                    </td>
                    <td><b>{{ uter.fatherName }}</b></td>
                    <td><b>{{ uter.fatherFname }}</b></td>
                    <td><b>{{ uter.Class }}</b></td>
                    <td><b>{{ uter.email }}</b></td>
                    <td><b>{{ uter.fatherAddress }}</b></td>
                    <td><b>{{ uter.fatherPhone }}</b></td>
                    <td><b>{{ uter.fatherOccupation }}</b></td>
                    <td><b>{{ uter.fatherEducation }}</b></td>
                    <td><b>{{ uter.fatherNID }}</b></td>
                    <td><b>{{ uter.fatherReligion }}</b></td>
                   
                    <td>
                        <button @click.prevent="editUse(uter.id)" class="btn btn-primary">Edit</button>
                    </td>
                    <td>
                        <button @click.prevent="deleteUse(uter.id)" class="btn btn-danger">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</div>

<div class="tab-inn">
    <div class="table-responsive table-desi" style="overflow-x: auto;">
        <table class="table table-hover">
            <thead>
                <tr>
                    <th>Mother Photo</th>
                    <th>Mother Name</th>
                    <th>Mother First Name</th>
                    <th>Mother Address</th>
                    <th>Mother Phone</th>
                    <th>Mother Occupation</th>
                    <th>Mother Education</th>
                    <th>Mother NID</th>
                    <th>Mother Religion</th>
                    <th>Actions</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="uter in uters" :key="uter.id ">
                    <td>
                        <span class="list-img"><img :src="uter.motherPhoto" alt="Mother Photo" class="img-fluid"></span> 
                    </td>
                    <td><b>{{ uter.MotherName }}</b></td>
                    <td><b>{{ uter.motherCname }}</b></td>
                    <td><b>{{ uter.motherAddress }}</b></td>
                    <td><b>{{ uter.motherPhone }}</b></td>
                    <td><b>{{ uter.motherOccupation }}</b></td>
                    <td><b>{{ uter.motherEducation }}</b></td>
                    <td><b>{{ uter.motherNID }}</b></td>
                    <td><b>{{ uter.motherReligion }}</b></td>

                    <td>
                        <button @click.prevent="editUse(uter.id)" class="btn btn-primary">Edit</button>
                    </td>
                    <td>
                        <button @click.prevent="deleteUse(uter.id)" class="btn btn-danger">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
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

