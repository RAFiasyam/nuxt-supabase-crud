<script setup>
import { createClient } from '@supabase/supabase-js'
const supabase = createClient(
  'https://qhzindbhulgpuvgfglvo.supabase.co',
  'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InFoemluZGJodWxncHV2Z2ZnbHZvIiwicm9sZSI6ImFub24iLCJpYXQiOjE3Mzk3NzU0MjMsImV4cCI6MjA1NTM1MTQyM30.vz-gfjO7PKLRYe6Jm8vsl9_j2KME2av7T7DCeEsTXQE'
)
const instruments = ref([])

async function getInstruments() {
  const { data } = await supabase
    .from('instruments')
    .select()
  instruments.value = data
}

onMounted(() => {
  getInstruments()
})
</script>

<template>
  <div class="bg-blue-950 h-screen text-white">
    <ul>
      <li v-for="instrument in instruments" :key="instrument.id">{{ instrument.name }}</li>
    </ul>
  </div>
</template>