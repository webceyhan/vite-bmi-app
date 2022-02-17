<script setup>

import { computed, ref } from 'vue';

const form = ref({
  gender: 'male',
  age: 0,
  weight: 0,
  height: 0,
});

const calories = computed(() => {
  // get input values
  const { age, weight, height, gender } = form.value;

  // calculate calories based on the gender
  return (gender === 'male')
    ? (655.09 + 9.56 * weight + 1.84 * height - 4.67 * age).toFixed(2)
    : (66.47 + 13.75 * weight + 5 * height - 6.75 * age).toFixed(2);
});

</script>

<template>
  <div class="container p-lg-5">
    <h1 class="display-5">BMI Calculator</h1>

    <div class="card bg-light mb-4 mx-auto">
      <div class="card-body">
        <form class="row">
          <div class="col-12 col-md-6 mb-3">
            <label for="gender" class="form-label">Gender:</label>
            <select name="gender" class="form-select form-select-lg" v-model="form.gender">
              <option value="female">Female</option>
              <option value="male">Male</option>
            </select>
          </div>

          <div class="col-12 col-md-6 mb-3">
            <label for="age" class="form-label">Age:</label>

            <input
              type="number"
              name="age"
              class="form-control form-control-lg"
              inputmode="numeric"
              pattern="[0-9]*"
              min="0"
              v-model.number="form.age"
            />
          </div>

          <div class="col-12 col-md-6 mb-3">
            <label for="height" class="form-label">Height:</label>
            <div class="input-group">
              <input
                type="number"
                name="height"
                class="form-control form-control-lg"
                inputmode="numeric"
                pattern="[0-9]*"
                min="0"
                v-model.number="form.height"
              />
              <span class="input-group-text">cm</span>
            </div>
          </div>

          <div class="col-12 col-md-6 mb-3">
            <label for="weight" class="form-label">Weight:</label>
            <div class="input-group">
              <input
                type="number"
                class="form-control form-control-lg"
                name="weight"
                inputmode="numeric"
                pattern="[0-9]*"
                min="0"
                v-model.number="form.weight"
              />
              <span class="input-group-text">kg</span>
            </div>
          </div>
        </form>
      </div>
    </div>

    <div>
      <h6>The Basal Metabolic Rate (BMR):</h6>
      <input class="form-control form-control-lg" readonly v-model="calories" />
    </div>
  </div>
</template>