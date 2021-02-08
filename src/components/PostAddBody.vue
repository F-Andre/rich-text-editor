<template>
  <div>
    <rich-text-editor
      :iframe-edit="edit"
      v-on:text-clicked="onTextClicked($event)"
    ></rich-text-editor>
    <button @click.prevent="onEditOverButton">
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

  props: {
    edit: Boolean,
  },

  data() {
    return {
      buttonText: this.edit ? "Terminer l'édition" : "Reprendre l'édition",
    };
  },

  methods: {
    onTextClicked: function (event) {
      this.$children.forEach((child) => {
        if (child.id === event) {
          child.edit = true
          this.buttonText = "Terminer l'édition"
        } else {
          child.edit = false
          this.buttonText = "Reprendre l'édition"
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
