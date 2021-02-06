<template>
  <div>
    <textarea rows="1" class="form-control" name="text" v-model="text" required hidden></textarea>
    <div class="post-text my-3" v-if="!edit" v-html="text" @click="$emit('text-clicked')"></div>
    <iframe v-else :id="generatedId" class="postIframe" src="/editors/iframe_post.html" @load="loadText"></iframe>
  </div>
</template>

<script>
  export default {
    props: {
      iframeText: {
        type: String,
        default: ""
      },
      iframeEdit: {
        type: Boolean,
        default: false
      }
    },

    data() {
      return {
        text: this.iframeText,
        modified: false,
        edit: this.iframeEdit,
        generatedId: String,
      }
    },

    methods : {
      loadText: function () {
        document.querySelector('#' + this.generatedId).contentWindow.postMessage(this.text, '*');
      
      },

      textClicked: function () {
        this.edit = true
        document.querySelectorAll('.postIframe').forEach(iframe => {
          console.log(iframe);
        })
      },

      generateId: function () {
        this.generatedId = 'iframe' + Math.floor(Math.random() * 10000);
      },
    },

    mounted() {
      window.addEventListener('message', (e) => {
        if (typeof e.data === "string" && this.edit) {
          this.text = e.data;
          this.modified = true;
        }
      })
      this.generateId()
    }
  }
</script>
