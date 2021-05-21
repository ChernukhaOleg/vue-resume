<template>
<div class="container column">
  <app-resume-creator @block="addblock"></app-resume-creator>
  <app-resume-list :addinfo="block"></app-resume-list>
  </div>
  <div class="container">
  <app-comment @loadComment="loadComment" :comments="comments" :isLoad="isLoad"></app-comment>
  <app-loader v-if="appLoad"></app-loader>
</div>
</template>

<script>
import AppResumeCreator from './components/AppResumeCreator'
import AppResumeList from './components/AppResumeList'
import AppComment from './components/AppComment'
import AppLoader from './components/AppLoader'

export default {
  name: 'App',
  data() {
    return {
      block: [],
      comments: [],
      appLoad:false,
      isLoad: false,
    }
  },
  methods: {
    addblock(val) {
      console.log(val);
      this.block.push(val)
    },
    async loadComment() {
       this.appLoad = true
      if (!this.isLoad) {
        setTimeout(async () => {
          let comment = await (
            await fetch("http://localhost:3000/comments")
          ).json();
          this.comments = comment.map((item) => {
            return { userName: item.userName, text: item.body };
          });
          console.log(this.comments);
          this.isLoad = true;
          this.appLoad = false
        }, 1500);
      } else {
        this.isLoad = false;
        this.appLoad = false
      }
    },
  },

  components: {
    AppResumeCreator,
    AppResumeList,
    AppComment,
    AppLoader
  }
}
</script>

<style>

</style>
