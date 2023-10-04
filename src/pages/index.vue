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
  <div>
    <div text-4xl>
      <div i-carbon-campsite inline-block />
    </div>
    <p>
      <a rel="noreferrer" href="https://github.com/antfu/vitesse" target="_blank">
        Templates
      </a>
    </p>
    <div v-if="isCopied">
      Copied
    </div>

    <div class="grid grid-cols-4 mx-auto max-w-lg">
      <div v-for="template in templates" :key="template.name" class="grid-col-1 grid auto-rows-max grid-flow-row gap-1 p-2">
        <h3 class="row-span-2">
          {{ template.name }}
        </h3>
        <button class="place btn" @click="handleClick(template.text)">
          copy
        </button>
      </div>
    </div>
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>
