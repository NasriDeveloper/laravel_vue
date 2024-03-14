<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import AdNavHeader from "./AdNavHeader.vue";
import AdSidebar from "./AdSidebar.vue";
import { ref } from 'vue';
import { Head, Link, router } from '@inertiajs/vue3';
import ApplicationMark from '@/Components/ApplicationMark.vue';
import Banner from '@/Components/Banner.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';




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

defineProps(["userp"]);


const asset = (path) => `${import.meta.env.VITE_APP_BASE_URL}/${path}`;

const successMessage = ref('');


function deleteUser(id){
  router.delete('/userp/' + id)
  successMessage.value = 'User has been successfully deleted.';
}

function edit(id){
  router.get('/userp/'+id+'/edit')
}


function closeSuccessMessage() {
    successMessage.value = '';
}

</script>

<template>
    
<AppLayout title="Dash">




<body>
    <!--== MAIN CONTRAINER ==-->
 
 <AdNavHeader />
                                 


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
                    <h4 class="text-center">STUDENT DETAILS</h4>
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
                                     <th>Photo</th>
                                    <th>First Name</th>
                                    <th>Middle Name</th>
                                    <th>Parent First Name</th>
                                    <th>Parent Last Name</th>
                                    <th>Class</th>
                                    <th>Year of Entry</th>
                                    <th>Gender</th>
                                    <th>Date of Birth</th>
                                    <th>Nationality</th>
                                    <th>Place of Birth</th>
                               
                                    <th>Actions</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="user in userp" :key="user.id">
                                    <td>
                                        <span class="list-img"> <img :src="user.photo" alt="Photo" class="img-fluid"></span>
                                    </td>
                                    <td><b>{{ user.firstName }}</b></td>
                                    <td><b>{{ user.middleName }}</b></td>
                                    <td><b>{{ user.parentfirstName }}</b></td>
                                    <td><b>{{ user.parentlastName }}</b></td>
                                    <td><b>{{ user.class }}</b></td>
                                    <td><b>{{ user.yearOfEntry }}</b></td>
                                    <td><b>{{ user.gender }}</b></td>
                                    <td><b>{{ user.dob }}</b></td>
                                    <td><b>{{ user.nationality }}</b></td>
                                    <td><b>{{ user.placeOfBirth }}</b></td>
                                   
                                    <td>
                                        <a @click.prevent="edit(user.id)" class="btn btn-primary">Edit</a>
                                    </td>
                                    <td>
                                        <a @click.prevent="deleteUser(user.id)" class="btn btn-danger">Delete</a>
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


