<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { useForm } from '@inertiajs/vue3';
import { router } from '@inertiajs/vue3';
import AdNavHeader from "./AdNavHeader.vue";
import AdSidebar from "./AdSidebar.vue";
import AdStyles from "./AdStyles.vue";
import { ref } from 'vue';

const success = ref(false);

const props = defineProps({
  uper: Object,
});

const formData = useForm({
  name: props.uper.name,
  email: props.uper.email,
});

function submitFormu(id) {
  router.put('/upers/' + id, formData);
  success.value = true;
}

function closeSuccessMessage() {
  success.value = false;
}
</script>

<template>
  <AppLayout title="Dash">
    <AdStyles />
    <body>
      <!--== MAIN CONTRAINER ==-->
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
                  <div class="box-inn-sp admin-form">
                    <div class="inn-title">
                      <h4>Student Details</h4>
                      <p>Enter student details here</p>
                    </div>
                    <div v-if="success" class="alert alert-success mt-3">
                      <span>User has been successfully edited. <button @click="closeSuccessMessage" class="close" aria-label="Close">&times;</button></span>
                    </div>
                    <div class="tab-inn">
                      <form @submit.prevent="submitFormu(uper.id)">
                        <div class="row">
                          <!-- First Name -->
                          <div class="col-md-6 form-group">
                            <label for="firstName">Name:</label>
                            <input
                              v-model="formData.name"
                              type="text"
                              id="name"
                              name="name"
                              class="form-control"
                              required
                            />
                          </div>
                          <!-- Middle Name -->
                          <div class="col-md-6 form-group">
                            <label for="email">Email:</label>
                            <input v-model="formData.email" type="text" id="email" name="email" class="form-control" required>
                          </div>
                        </div>
                        <div class="row">
                          <div class="col-md-12">
                            <button type="submit" class="btn btn-primary">Submit</button>
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
    </body>
  </AppLayout>
</template>
