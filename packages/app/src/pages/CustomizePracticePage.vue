<template>
  <q-page class="mobile-container">
    <div class="column full-viewport-height q-pb-lg">
      <q-stepper
        transition-next="slide-left"
        flat
        v-model="step"
        ref="stepper"
        contracted
        color="primary"
        animated
      >
        <q-step
          title="Mode Picker"
          :name="1"
          :done="step > 1"
        >
          <mode-picker />
        </q-step>

        <q-step
          :name="2"
          title="Value Picker"
          caption="Optional"
          :done="step > 2"
        >
          <value-picker />
        </q-step>

        <q-step
          :name="3"
          title="Difficulty Picker"
        >
          <difficulty-picker />
        </q-step>

        <template v-slot:navigation>
          <q-stepper-navigation class="justify-center">
            <q-btn
              v-if="step < 3"
              class="full-width"
              rounded
              @click="$refs.stepper.next()"
              color="primary"
              label="Next"
            />
            <router-link
              v-else
              to="/"
            >
              <q-btn
                class="full-width"
                rounded
                color="primary"
                label="Done"
              />
            </router-link>
          </q-stepper-navigation>
        </template>
      </q-stepper>
    </div>
  </q-page>
</template>

<script>
import ModePicker from "../components/ModePicker.vue";
import ValuePicker from "../components/ValuePicker.vue";
import DifficultyPicker from "../components/DifficultyPicker.vue";

export default {
  data () {
    return {
      step: 1
    };
  },
  components: {
    ModePicker,
    ValuePicker,
    DifficultyPicker
  }
};
</script>

<style>
.mobile-container {
  width: 420px;
  max-height: 100%;
  display: flex;
  flex-direction: column;
}

@media (max-width: 599px) {
  .mobile-container {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
}
</style>