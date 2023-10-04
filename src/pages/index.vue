<script setup lang="ts">
const templates = [
  {
    name: 'Manual Enrollment',
    text: `I'm attaching to this email a Manual Enrolment form for you to provide me with the details (schedule and campus) of the subjects you want to enrol. 

Kindly, please fill it out and send it back by replying to this email. 

Once I receive the form I will gladly process your enrolment. 
`,
  },
  {
    name: 'TimeTable change',
    text: `I'm attaching to this email a Timetable change form for you to provide me with the details of the subjects you want to enrol and the subjects you want to withdraw. 

Kindly, please fill it out and send it back by replying to this email. 

Once I receive the form I will gladly process your enrolment. 
`,
  },
  {
    name: 'Subject withdrawal',
    text: `Regarding your email, I can certainly assist you with withdrawing your subject. For this, I will send you a form where you can provide me with the details of the subjects you want to withdraw. 

Kindly, please fill it out and send it back by replying to this email. Please make sure the form is signed. 

Once I receive the form I will gladly process your enrolment.`,
  },
  {
    name: 'Student ID card',
    text: `Regarding your email, we received your request for a student ID card. For this, we have two options: We can send you the ID card posted to your home address. However, if we send it there, the card won't grant you access to the campus. 

If you want a card that grants you access to campus, you will have to pick it up on campus. I can request it for you and once it is ready, you can go to pick it up. 

Knowing this, would you like me to send it to your home address with no campus access or would you want me to request it on campus for you to pick up with access to campus?`,
  },
]
const isCopied = ref(false)

function handleClick(source: any) {
  const { text, copy, copied, isSupported } = useClipboard({ source })
  copy(source)
  isCopied.value = true
}
/*
{
    'name': '',
    'text': ``
  }
  */
</script>

<template>
  <div class="mx-auto container">
    <div text-4xl>
      <div i-carbon-catalog-publish inline-block />
    </div>
    <h1 class="mb-8 text-2xl font-semibold">
      Templates
    </h1>
    <div v-if="isCopied" class="mx-auto mb-3 max-w-sm flex items-center justify-between border-1 border-emerald-400 rounded-lg bg-emerald-200 text-emerald-600/80 transition">
      <p />
      <p>Copied</p>
      <button class="bg-emerald-200 text-emerald-800 btn hover:bg-emerald-300" @click="() => isCopied = false">
        x
      </button>
    </div>

    <div class="grid grid-cols-3 mx-auto max-w-2xl gap-6">
      <div
        v-for="template in templates" :key="template.name"
        class="grid-col-1 grid gap-6 border-1 border-gray-200 rounded-xl px-6 py4"
      >
        <h3 class="row-span-2">
          {{ template.name }}
        </h3>
        <div class="grid grid-cols-3 gap-3">
          <button class="col-span-2 btn">
            read text
          </button>
          <button class="place btn-copy" @click="handleClick(template.text)">
            <div i-carbon-copy />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>
