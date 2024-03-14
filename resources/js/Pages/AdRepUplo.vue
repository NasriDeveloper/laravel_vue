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

defineProps(["users"]);


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
                          <div class="box-inn-sp admin-form">
  <div class="inn-title">
    <h4>Student Details</h4>
    <p>Enter student details here</p>
    </div>
            <div class="tab-inn">
                 <form @submit.prevent="submitForm">
                    <div class="row">
                                <!-- Email -->
                              <div class="col-md-6 form-group">
                                 <label for="emailSelect">Select Email:</label>
                                <select v-model="formData.email" id="email" name="email" class="form-control" required>
                                <option v-for="user in users" :key="user.id">{{ user.email }}</option>
                                </select>
                               </div>


         

                                <div class="col-md-6 form-group">
                                    <label for="pdp">Upload PDF:</label>
                                    <input
                                        type="file"
                                        id="pdp"
                                        name="pdp"
                                        class="form-control-file"
                                        accept=".pdp"
                                        ref="pdp"
                                    />
                                </div>

                                <!-- Middle Name (if needed) -->

                                <div class="row">
                                    <div class="col-md-12">
                                        <button type="submit" class="btn btn-primary">Submit</button>
                                    </div>
                                </div>
                            </div>
                        </form>

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


<script>
export default {
    data() {
        return {
            formData: {
                email: '',
                pdp: null,
            },
        };
    },
    methods: {
        async submitForm() {
            try {
                let formData = new FormData();

                for (let key in this.formData) {
                    formData.append(key, this.formData[key]);
                }

                // Append the file data to FormData
                formData.append('pdp', this.$refs.pdp.files[0]);

                await this.$inertia.post(route('Reportform'), formData);

                // Redirect or show success message as needed
            } catch (error) {
                // Handle errors
                console.error(error);
            }
        },
    },
};
</script>