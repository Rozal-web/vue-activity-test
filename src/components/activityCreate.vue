<template>
  <div class="activityCreateForm">
    <a
      v-if="!isFormDisplayed"
      class="button is-primary is-block is-alt is-large"
      href="#"
      @click="toddleFormDisplay"
    >New Activity</a>

    <div v-if="isFormDisplayed" class="create-form">
      <h2>Create Activity</h2>
      <form>
        <div class="field">
          <label class="label">Title</label>
          <div class="control">
            <input
              v-model="newActivity.title"
              class="input"
              type="text"
              placeholder="Read a Book"
            >
          </div>
          <div class="field">
            <label class="label">Notes</label>
            <div class="control">
              <textarea v-model="newActivity.notes" class="textarea" placeholder="Textarea" />
            </div>
          </div>
          <div class="field">
            <label class="label">Notes</label>
            <div class="control">
              <select v-model="newActivity.category" class="select">
                <option disabled value="">Please Select</option>
                <option v-for="category in categories" 
                        :key="category.id">{{ category.text }}</option>
              </select>
            </div>
          </div>
        </div>
        <div class="field is-grouped">
          <div class="control">
            <button class="button is-link" :disabled="!isFormValid" @click="createActivity">
              Create Activity
            </button>
          </div>
        </div>
      </form>

      <div class="control">
        <button class="button is-text" @click="toddleFormDisplay">
          Cancel
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    props:{
        categories: {
            type: Object,
            required: true
        }
    },
    data(){
        return{
            isFormDisplayed: false,
            newActivity: {
        title: "",
        notes: "",
        category: ""
      },
        }
    },
    computed:{
        isFormValid () {
    return this.newActivity.title && this.newActivity.notes
  },
    },
    methods: {
        toddleFormDisplay() {
      this.isFormDisplayed = !this.isFormDisplayed;
    },
    createActivity() {
      console.log(this.newActivity);
    }
    }
}
</script>

<style lang="stylus" scoped>

</style>