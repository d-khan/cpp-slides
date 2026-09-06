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
const showExplanation = ref(false)

function checkAnswer() {
  if (selected.value) {
    checked.value = true

    if (selected.value === props.correct) {
      showExplanation.value = true
    }
  }
}

function selectAnswer() {
  checked.value = false
  showExplanation.value = false
}

function closeExplanation() {
  showExplanation.value = false
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
          @change="selectAnswer"
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


    <!-- =====================================================
         EXPLANATION POPUP
         ===================================================== -->

    <div
      v-if="showExplanation"
      class="explanation-overlay"
      @click.self="closeExplanation"
    >
      <div class="explanation-popup">

        <div class="explanation-title">
          ✓ Correct
        </div>

        <div
          class="explanation-text"
          v-html="formattedExplanation"
        />

        <button
          class="close-explanation"
          @click="closeExplanation"
        >
          Close
        </button>

      </div>
    </div>

  </div>
</template>