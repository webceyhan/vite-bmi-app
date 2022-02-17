<script setup>

import { computed, ref } from 'vue';

const form = ref({
  gender: 'male',
  age: 15,
  height: 150,
  weight: 50,
});

const bmiMap = {
  underweight: { label: 'Underweight', color: 'info' },
  normal: { label: 'Normal', color: 'success' },
  overweight: { label: 'Overweight', color: 'warning' },
  obesity: { label: 'Obesity', color: 'danger' },
}

const bmi = computed(() => {
  const { weight, height, age } = form.value;
  const value = ((weight / height / height) * 10000).toFixed(2);

  if (age >= 20) { // adults
    if (value < 18.5) return { ...bmiMap.underweight, value };
    if (value < 25) return { ...bmiMap.normal, value };
    if (value < 30) return { ...bmiMap.overweight, value };
    return { ...bmiMap.obesity, value };
  } else { // kids
    if (value < 20.7) return { ...bmiMap.underweight, value };
    if (value < 34) return { ...bmiMap.normal, value };
    if (value < 39.8) return { ...bmiMap.overweight, value };
    return { ...bmiMap.obesity, value };
  }
});

const bmr = computed(() => {
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
    <h1 class="display-5">BMI/BMR Calculator</h1>

    <div class="card bg-light shadow mb-4">
      <div class="card-body p-4">
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
              pattern="[0-9]*"
              min="15"
              max="85"
              v-model.number="form.age"
              required
            />
          </div>

          <div class="col-12 col-md-6 mb-3">
            <label for="height" class="form-label">Height:</label>
            <div class="input-group">
              <input
                type="number"
                name="height"
                class="form-control form-control-lg"
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

    <div class="card bg-dark text-light shadow">
      <div class="card-body p-4">
        <h4 class="card-title">Your results</h4>

        <hr />

        <dl class="row mb-2">
          <dt class="col-12 col-md">Body Mass Index (BMI):</dt>
          <dd class="col-12 col-md">
            <span :class="`text-${bmi.color}`">{{ bmi.value }}</span>
          </dd>
        </dl>

        <div class="progress mb-4" style="height: 1.5rem;">
          <div
            :class="`progress-bar bg-${bmi.color}`"
            :style="{ width: `${bmi.value}%` }"
          >{{ bmi.label }}</div>
        </div>

        <dl class="row mb-2">
          <dt class="col-12 col-md">The Basal Metabolic Rate (BMR):</dt>
          <dd class="col-12 col-md">
            <span :class="`text-${bmi.color}`">{{ bmr }}</span> kcal / day
          </dd>
        </dl>
      </div>
    </div>
  </div>
</template>