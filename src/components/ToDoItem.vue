<template>
  <div>
    <div v-if="!isEditing">
      <span>{{ todo.name }}</span>
      <button
        type="button"
        class="btn"
        ref="editButton"
        @click="toggleToItemEditForm"
      >
        Edit
        <span class="visually-hidden">Edit this item</span>
      </button>
      <button type="button" @click="deleteItem">Delete</button>
    </div>

    <div v-else>
      <input
        ref="labelInput"
        v-model="editedName"
        type="text"
        autocomplete="off"
      />
      <button @click="saveEdit">Save</button>
      <button @click="cancelEdit">Cancel</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: Object,
  },
  data() {
    return {
      isEditing: this.todo.isEditing,
      editedName: this.todo.name,
    };
  },
  methods: {
    toggleToItemEditForm() {
      this.isEditing = true;
      this.$nextTick(() => {
        // Focus on input field when edit form is shown
        this.$refs.labelInput.focus();
      });
    },
    saveEdit() {
      this.$emit('item-edited', this.editedName);
      this.isEditing = false;
      this.$nextTick(() => {
        // Focus back on the edit button
        this.$refs.editButton.focus();
      });
    },
    cancelEdit() {
      this.isEditing = false;
      this.$nextTick(() => {
        // Focus back on the edit button when cancelling edit
        this.$refs.editButton.focus();
      });
    },
    deleteItem() {
      this.$emit('item-deleted', this.todo.id);
    },
  },
};
</script>

<style scoped>
/* You can add scoped styles for this component */
</style>
