<template>
  <div id="post-body">
    <rich-text-editor
      :iframe-edit="true"
      v-on:text-clicked="onTextClicked($event)"
    ></rich-text-editor>
    <button class="btn btn-success" @click.prevent="onEditOverButton">
      {{ buttonText }}
    </button>
  </div>
</template>

<script>
import RichTextEditor from "../components/RichTextEditor";

export default {
  components: {
    RichTextEditor,
  },

  data() {
    return {
      buttonText: "Terminer l'édition",
    };
  },

  methods: {
    onTextClicked: function (event) {
      this.$children.forEach((child) => {
        if (child.id === event) {
          child.edit = true;
        } else {
          child.edit = false;
        }
      });
    },

    onEditOverButton: function () {
      this.$children.forEach((child) => {
        if (child.edit === false) {
          child.edit = true;
          this.buttonText = "Terminer l'édition";
        } else {
          child.edit = false;
          this.buttonText = "Reprendre l'édition";
        }
      });
    },
  },
};
</script>
