<template>
  <div class="card w70">
    <div v-if="!addinfo.length">
      <h3>Добавьте первый блок, чтобы увидеть результат</h3>
    </div>
    <div v-else>
      <component 
      v-for="type in addinfo" :key="type"
      :info="type.text"
      :is="'resume-'+type.title"
      v-bind="type"
      ></component>
      
    </div>
  </div>
</template>

<script>
import ResumeTitle from './structure/ResumeTitle'
import ResumeSubtitle from './structure/ResumeSubtitle'
import ResumeText from './structure/ResumeText'
import ResumeAvatar from './structure/ResumeAvatar'

export default {
  props: ['addinfo'],

  
  components: {
      ResumeTitle,
      ResumeSubtitle,
      ResumeText,
      ResumeAvatar
  }
}
</script>