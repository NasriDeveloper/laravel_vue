<script setup>

import AppLayout from '@/Layouts/AppLayout.vue';
import {useForm} from '@inertiajs/vue3';
import {router} from '@inertiajs/vue3';
import AdNavHeader from "./AdNavHeader.vue";
import AdSidebar from "./AdSidebar.vue";
import { ref } from 'vue';


const success = ref(false);






const props = defineProps({
  user: Object,
})



// Declare a ref for form data
const formData = useForm({
            firstName:props.user.firstName,
            middleName:props.user.middleName, 
            lastName:props.user.lastName, 
            parentfirstName:props.user.parentfirstName, 
            parentlastName:props.user.parentlastName, 
            class:props.user.class, 
            yearOfEntry:props.user.yearOfEntry,
            gender:props.user.gender, 
            dob:props.user.dob, 
            nationality:props.user.nationality, 
            placeOfBirth:props.user.placeOfBirth, 
           
});

function submitForm(id){
   router.put('/userp/'+id,formData);
   success.value = true;
}

function closeSuccessMessage() {
  success.value = false;
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
                          <div class="box-inn-sp admin-form">
  <div class="inn-title">
    <h4>Student Details</h4>
    <p>Enter student details here</p>
  </div>
  <div v-if="success" class="alert alert-success mt-3">
    <span>User has been successfully edited. <button @click="closeSuccessMessage" class="close" aria-label="Close">&times;</button></span>
  </div>
  <div class="tab-inn">
    <form @submit.prevent="submitForm(user.id)">
      <div class="row">
        <!-- First Name -->
        <div class="col-md-6 form-group">
          <label for="firstName">First Name:</label>
          <input
            v-model="formData.firstName"
            type="text"
            id="firstName"
            name="firstName"
            class="form-control"
            required
          />
        </div>

        <!-- Middle Name -->
        <div class="col-md-6 form-group">
          <label for="middleName">Middle Name:</label>
          <input
            v-model="formData.middleName"
            type="text"
            id="middleName"
            name="middleName"
            class="form-control"
          />
        </div>

        <!-- Last Name -->
        <div class="col-md-6 form-group">
          <label for="lastName">Last Name:</label>
          <input
            v-model="formData.lastName"
            type="text"
            id="lastName"
            name="lastName"
            class="form-control"
            required
          />
        </div>

        <!-- Parent First Name -->
        <div class="col-md-6 form-group">
          <label for="parentfirstName">Parent First Name:</label>
          <input
            v-model="formData.parentfirstName"
            type="text"
            id="parentfirstName"
            name="parentfirstName"
            class="form-control"
            required
          />
        </div>

        <!-- Parent Last Name -->
        <div class="col-md-6 form-group">
          <label for="parentlastName">Parent Last Name:</label>
          <input
            v-model="formData.parentlastName"
            type="text"
            id="parentlastName"
            name="parentlastName"
            class="form-control"
            required
          />
        </div>

        <!-- Class -->
        <div class="col-md-6 form-group">
          <label for="class">Class:</label>
          <select v-model="formData.class" id="class" name="class" class="form-control" required>
            <option value="" disabled>Select Class</option>
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5</option>
            <option value="6">6</option>
            <option value="7">7</option>
            <!-- Add Bootstrap-compatible options as needed -->
          </select>
        </div>

        <!-- Year of Entry -->
        <div class="col-md-6 form-group">
          <label for="yearOfEntry">Year of Entry:</label>
          <select v-model="formData.yearOfEntry" id="yearOfEntry" name="yearOfEntry" class="form-control" required>
            <option value="" disabled>Select Year</option>
            <option value="2010">2010</option>
            <option value="2011">2011</option>
            <option value="2012">2012</option>
            <option value="2013">2013</option>
            <option value="2014">2014</option>
            <option value="2015">2015</option>
            <option value="2016">2016</option>
            <option value="2017">2017</option>
            <option value="2018">2018</option>
            <option value="2019">2019</option>
            <option value="2020">2020</option>
            <option value="2021">2021</option>
            <option value="2022">2022</option>
            <option value="2023">2023</option>
            <option value="2024">2024</option>
            <option value="2025">2025</option>
            <option value="2026">2026</option>
            <option value="2027">2027</option>
            <option value="2028">2028</option>
            <option value="2029">2029</option>
            <option value="2030">2030</option>
            <option value="2031">2031</option>
            <option value="2032">2032</option>
            <option value="2033">2033</option>
            <option value="2034">2034</option>
            <option value="2035">2035</option>
            <option value="2036">2036</option>
            <option value="2037">2037</option>
            <option value="2038">2038</option>
            <option value="2039">2039</option>
            <option value="2040">2040</option>
            <!-- Add Bootstrap-compatible options as needed -->
          </select>
        </div>

        <!-- Gender -->
        <div class="col-md-6 form-group">
          <label for="gender">Gender:</label>
          <select v-model="formData.gender" id="gender" name="gender" class="form-control" required>
            <option value="" disabled>Select Gender</option>
            <option value="boy">Boy</option>
            <option value="girl">Girl</option>
          </select>
        </div>

        <!-- Date of Birth -->
        <div class="col-md-6 form-group">
          <label for="dob">Date of Birth:</label>
          <input
            v-model="formData.dob"
            type="date"
            id="dob"
            name="dob"
            class="form-control"
            required
          />
        </div>

        <!-- Upload Photo -->
        <div class="col-md-6 form-group">
          <label for="photo">Upload Photo:</label>
          <input
            type="file"
            id="photo"
            name="photo"
            class="form-control-file"
            accept="image/*"
            ref="photo"
          />
        </div>

        <!-- Nationality -->
        <div class="col-md-6 form-group">
          <label for="nationality">Nationality:</label>
          <select v-model="formData.nationality" id="nationality" name="nationality" class="form-control" required>
            <option value="" disabled>Select Nationality</option>
            <option value="US">US</option>
          
            <!-- Add Bootstrap-compatible options as needed -->
          </select>
        </div>

        <!-- Place of Birth -->
        <div class="col-md-6 form-group">
          <label for="placeOfBirth">Place of Birth:</label>
          <input
            v-model="formData.placeOfBirth"
            type="text"
            id="placeOfBirth"
            name="placeOfBirth"
            class="form-control"
            required
          />
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

    <!--Import jQuery before materialize.js-->
  
   
</body>


</AppLayout>

</template>


