<template>
  <div class="app-textarea">
    <textarea
      ref="textarea"
      :value="text"
      class="app-textarea__text"
      placeholder="Insert a description for your voice transcription here..."
      @input="changeDescription($event.target.value)"
    />
  </div>
</template>
    <script>
    export default {
      name: "AppTextarea",
    
      props: {
        text: {
          type: String,
          required: true,
        }
      },

      emits: ['change-description'],

      mounted () {
          this.setHeight();
      },

      methods: {
         setHeight () {
          const textarea = this.$refs.textarea;
          textarea.style.height = textarea.scrollHeight + 'px';
        },

        changeDescription (description) {
          this.setHeight();
            this.$emit('change-description', description)
        }
    }
    };
    </script>
    <style lang="scss" scoped>

  .app-textarea__text { 
    border: none;
    width: 100%;
    resize: none;
    color: $slate-gray;
    font-size: $default-size;
    font-family: OpenSansRegular;
    overflow-x: hidden;
    overflow-y: auto;
    }
    </style>