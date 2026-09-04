<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  question: String,
  options: Array,
  correct: String,
  explanation: String,
})

const selected = ref('')
const checked = ref(false)

function checkAnswer() {
  if (selected.value) {
    checked.value = true
  }
}

/* Convert `code` into <code>code</code> */
function formatCode(text) {
  if (!text)
    return ''

  return text.replace(
    /`([^`]+)`/g,
    '<code>$1</code>'
  )
}

/* Format question */
const formattedQuestion = computed(() => {
  return formatCode(props.question)
})

/* Format explanation */
const formattedExplanation = computed(() => {
  return formatCode(props.explanation)
})
</script>

<template>
  <div class="mt-(-4)">

    <!-- Question -->
    <div
      class="text-2xl mb-4"
      v-html="formattedQuestion"
    />

    <!-- Code or other question content -->
    <div
      v-if="$slots.default"
      class="mb-6"
    >
      <slot />
    </div>

    <!-- Answer choices -->
    <div class="space-y-1 text-xl">
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

          <span v-html="formatCode(option)" />

          <!-- Correct -->
          <span
            v-if="checked && selected === option && option === correct"
            class="text-green-400 font-bold ml-2"
          >
            ✓
          </span>

          <!-- Incorrect -->
          <span
            v-if="checked && selected === option && option !== correct"
            class="text-red-400 font-bold ml-2"
          >
            ✗
          </span>
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

    <!-- Explanation -->
    <div
      v-if="checked && selected === correct"
      class="mt-3 text-lg"
      v-html="formattedExplanation"
    />

  </div>
</template>