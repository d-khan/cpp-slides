<script setup>
import { ref } from 'vue'

const props = defineProps({
  question: String,
  options: Array,
  correct: String,
  explanation: String,
})

const selected = ref('')
const checked = ref(false)

function checkAnswer() {
  if (selected.value)
    checked.value = true
}
</script>

<template>
  <div class="mt-8">

    <!-- Question -->
    <div class="text-2xl mb-4">
      {{ question }}
    </div>

    <!-- Code or other question content -->
    <div
      v-if="$slots.default"
      class="mb-6"
    >
      <slot />
    </div>

    <!-- Answer choices -->
    <div class="space-y-4 text-xl">
      <label
        v-for="(option, index) in options"
        :key="option"
        class="flex items-center gap-3 cursor-pointer"
      >
        <input
          v-model="selected"
          type="radio"
          :value="option"
          @change="checked = false"
        >

        <span>
          {{ String.fromCharCode(65 + index) }})
          <code>{{ option }}</code>
        </span>
      </label>
    </div>

    <!-- Check Answer -->
    <button
      class="mt-6 px-6 py-2 rounded-lg bg-blue-600 text-white"
      @click="checkAnswer"
    >
      Check Answer
    </button>

    <!-- Feedback -->
    <div
      v-if="checked"
      class="mt-5 text-xl"
    >
      <div
        v-if="selected === correct"
        class="text-green-400 font-bold"
      >
        ✓ Correct!
      </div>

      <div
        v-else
        class="text-red-400 font-bold"
      >
        ✗ Incorrect. Try again.
      </div>

      <div
        v-if="selected === correct"
        class="mt-3 text-lg"
      >
        {{ explanation }}
      </div>
    </div>

  </div>
</template>