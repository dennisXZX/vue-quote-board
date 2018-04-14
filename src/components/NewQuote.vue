<template>
    <div class="row">
        <!-- error messages -->
        <div v-if="errors.length" class="col-xs-12">
            <div>Please correct the following error(s):</div>
            <ul>
                <li v-for="error in errors">{{ error }}</li>
            </ul>
        </div>

        <!-- new quote form -->
        <form>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <label>Quote</label>
                <textarea class="form-control" rows="3" v-model="quote"></textarea>
            </div>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <button class="btn btn-primary" @click.prevent="createNew">Add Quote</button>
            </div>
        </form>
    </div>
</template>

<script>
  export default {
    data: function () {
      return {
        errors: [],
        quote: ''
      }
    },
    methods: {
      createNew() {
        // validate the form
        if (this.checkForm()) {
          this.$emit('quoteAdded', this.quote);
          this.quote = '';
        }
      },
      checkForm() {
        // clear up all the errors
        this.errors = [];

        if (!this.quote) {
          this.errors.push('Quote required');
        }

        return this.errors.length <= 0 ? true : false;
      }
    }
  };
</script>

<style scoped>

</style>