<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import AdNavHeader from "./AdNavHeader.vue";
import AdSidebar from "./AdSidebar.vue";
import { ref } from 'vue';
import { router } from '@inertiajs/vue3';

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

defineProps(["upers"]);

const asset = (path) => `${import.meta.env.VITE_APP_BASE_URL}/${path}`;

// Ref for managing success message
const successMessage = ref('');

// Function to handle delete action
function deleteUsed(id) {
    router.delete('/upers/' + id);
    // Set the success message
    successMessage.value = 'User has been successfully deleted.';
}

function editUsed(id) {
    router.get('/upers/' + id + '/edit');
}

// Function to close the success message
function closeSuccessMessage() {
    successMessage.value = '';
}
</script>

<template>
<AppLayout title="Dash">
    <body>
        <!--== MAIN CONTAINER ==-->
        <AdNavHeader />
        <!--== BODY CONTAINER ==-->
        <div class="container-fluid sb2">
            <div class="row">
                <AdSidebar />
                <!--== BODY INNER CONTAINER ==-->
                <div class="sb2-2">
                    <!--== breadcrumbs ==-->
                    <div class="sb2-2-2">
                        <ul>
                            <li><a href="index-2.html"><i class="fa fa-home" aria-hidden="true"></i> Home</a></li>
                            <li class="active-bre"><a href="#"> Dashboard</a></li>
                            <li class="page-back"><a href="index-2.html"><i class="fa fa-backward" aria-hidden="true"></i> Back</a></li>
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
                                        <!-- Success Message -->
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
                                                        <th>User Name</th>
                                                        <th>Email</th>
                                                        <th>Action</th>
                                                        <th>Action</th>
                                                    </tr>
                                                </thead>
                                                <tbody>
                                                    <tr v-for="uper in upers" :key="uper.id">
                                                        <td>{{ uper.name }}</td>
                                                        <td>{{ uper.email }}</td>
                                                        <td>
                                                            <a @click.prevent="editUsed(uper.id)" class="btn btn-primary">Edit</a>
                                                        </td>
                                                        <td>
                                                            <!-- Show the delete confirmation modal on delete button click -->
                                                            <a @click.prevent="deleteUsed(uper.id)" class="btn btn-danger">Delete</a>
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
    </body>
</AppLayout>
</template>
