<template>
  <div class="about">
    <!-- <h1>This is an about page</h1> -->
    <div class="container">
      <div class="row">


        <div class="col-md-12">


          <ul class="nav nav-pills mb-3" id="pills-tab" role="tablist">


            <li class="nav-item" role="presentation">
              <!-- <button class="nav-link active" id="pills-home-tab" data-bs-toggle="pill" data-bs-target="#pills-home" type="button" role="tab" aria-controls="pills-home" aria-selected="true">Home</button> -->
              <button class="nav-link" :class="{'active': current_step == 1}" id="pills-home-tab" data-bs-toggle="pill" data-bs-target="#pills-home" type="button" role="tab" aria-controls="pills-home" aria-selected="true"
                @click.prevent="goToStep(1)">Home</button>
            </li>

            <li class="nav-item" role="presentation">
              <!-- <button class="nav-link" id="pills-profile-tab" data-bs-toggle="pill" data-bs-target="#pills-profile" type="button" role="tab" aria-controls="pills-profile" aria-selected="false">Profile</button> -->
              <button class="nav-link" :class="{'disabled': max_step < 2, 'active': current_step == 2}" id="pills-profile-tab" data-bs-toggle="pill" data-bs-target="#pills-profile" type="button" role="tab" aria-controls="pills-profile" aria-selected="false" @click.prevent="goToStep(2)">Profile</button>
            </li>

            <li class="nav-item" role="presentation">
              <!-- <button class="nav-link" id="pills-contact-tab" data-bs-toggle="pill" data-bs-target="#pills-contact" type="button" role="tab" aria-controls="pills-contact" aria-selected="false">Contact</button> -->
              <button class="nav-link" :class="{'disabled': max_step < 3, 'active': current_step == 3}" id="pills-contact-tab" data-bs-toggle="pill" data-bs-target="#pills-contact" type="button" role="tab" aria-controls="pills-contact" aria-selected="false" @click.prevent="goToStep(3)">Contact</button>
            </li>


          </ul>


          <div class="tab-content" id="pills-tabContent">

            <div class="tab-pane fade show active" id="pills-home" role="tabpanel" aria-labelledby="pills-home-tab"
             v-show="current_step == 1">
              Home page
            </div>

            <div class="tab-pane fade" id="pills-profile" role="tabpanel" aria-labelledby="pills-profile-tab"
             v-show="current_step == 2">
              Profile page
            </div>

            <div class="tab-pane fade" id="pills-contact" role="tabpanel" aria-labelledby="pills-contact-tab"
             v-show="current_step == 3">
              Contact page
            </div>

          </div>

          <button class="btn btn-primary" @click="advanceStep">
            <!-- <span v-if="max_step === 3">Submit</span> -->
            <span>Next</span>
          </button>


        </div>


      </div>
    </div>
  </div>
</template>

<script setup>

  import { ref } from '@vue/reactivity'

  let current_step = ref(1)
  let max_step = ref(1)



  let advanceStep = () => {
    current_step.value++

    if(max_step.value < current_step.value) {
      max_step.value = current_step.value
    }

  }

  let goToStep = (value) => {
    current_step.value = value
  }

</script>


<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
