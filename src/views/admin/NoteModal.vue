<template>
  <div class="dialog-container">
    <v-dialog persistent v-model="dialogFlag" :width="500">
      <v-card>
        <div class="p-5">
          <v-form ref="form">
            <v-textarea
              outlined
              name="note"
              label="Note"
              v-model="note"
            ></v-textarea>
            <v-btn color="warning" class="mr-4" @click="cancel"> Cancel</v-btn>

            <v-btn color="primary" class="mr-4" @click="save"> Save</v-btn>
          </v-form>
        </div>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import ButtonComponent from "@/components/atom/ButtonComponent.vue";
export default {
  components: {
    ButtonComponent,
  },
  props: ["dialog"],
  data() {
    return { 
      note: null,
    };  
  },
  computed: {
    dialogFlag: function () {
      return this.dialog;
    },
  },
  methods: {
    save() {
      this.$emit("save", this.note);
    },
    cancel() {
      this.$emit("cancel", false);
    },
  },
};
</script>