<template>
<!-- <div class="agreement">
    <div class="text">
      <p>
        To keep your account safe, we need to verify your identiy. This is a
        legal requirement that helps us to keep your account secure
      </p>
      <p>
        We accept photos/scans of a driving license, passport, national ID card
        or residence permit issued in European Economic Are(EEA).
      </p>
      <p>Follow these tips to make sure your documents are accepted.</p>
    </div>
    <div class="flex align-baseline confirm">
      <a-checkbox
        v-model="agreementChecked"
        @change="onChange"
        class="mt-3"
      ></a-checkbox>
      <span class="fs-16 ml-2"
        >I have consent for the candidate to represent</span
      >
    </div>
  </div> -->
  <div class="text-center">
    <v-dialog v-model="dialogFlag" width="600">
      <v-card v-if="!showConfirmation">
        <v-card-title class="text-h5"> Review and publish </v-card-title>

        <v-card-text>
          Please check the information and details that you have provided. If
          you are not happy, please edit. If you are happy, please submit the
          form for approval by the MatrimonyAssist Team.
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn class="v-btn-cancel" rounded @click="cancel"> Cancel </v-btn>
          <v-btn class="v-btn-submit" rounded @click="save">Submit </v-btn>
        </v-card-actions>
      </v-card>
      <v-card class="message" v-if="showConfirmation">
        <div class="container-fluid mb-3 body-container">
          <div class="content-text">
            <img
            src="@/assets/icon/check-circle-success.svg"
            alt="icon"
            class=""
            />
            <h3 class="mt-3 font-weight-bolder congo-text">
              CONGRATULATIONS !
            </h3>
            <h4 class="mt-3 fw-700 text-black-50 header-text">
              Representative Form Submitted.
            </h4>

            <p class="mt-4">
              Thank you for submitting your profile details. It will be reviewed
              and approved by the MatrimonyAssist shortly. However, if there are
              any compliance issues, MatrimonyAssist shall contact you through
              notification and customer support/personal settings section.
            </p>

            <button @click="submit" class="btn btn-block ms-2 text-nowrap continue-button mb-4">
              Continue
            </button>
          </div>
        </div>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  components: {},
  props: ["dialog"],
  data() {
    return { showConfirmation: false };
  },
  computed: {
    dialogFlag: function () {
      return this.dialog;
    },
  },
  methods: {
    save() {
      this.$emit("submit", null);
      setTimeout(() => {
        this.showConfirmation = true;
      }, 1000);
    },
    submit() {
      this.$emit("continue", true);
    },
    cancel() {
      this.$emit("cancel", false);
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/styles/base/_variables.scss";
.message {
  display: flex;
  flex-direction: column;
  padding: 10px;
  justify-content: center;
  align-items: center;
  .content-text {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
  header {
    height: 100px;
    background-color: $bg-secondary;
    img {
      margin-top: 10px;
      height: 80px;
    }
  }
  h4 {
    font-family: $body-font;
  }
  h3 {
    color: #42bf28;
  }
  img {
    height: 80px;
    margin: 20px 0px 10px 0px;
  }
  button {
    border: 1px solid $color-primary;
    background-color: $color-primary;
    padding: 0px 20px;
    color: white;
  }
}
.header-text {
  font-family: $body-font;
  //font-size: 32px;
  @media (min-width: 768px) {
    //padding: 40px 0;
  }
}
.type-access {
  color: $color-primary;
  text-decoration: underline;
  font-weight: 700;
}
.continue-button {
  height: 36px;
  border-radius: 60px;
  &:hover {
    background-color: #fff;
    color: $color-primary;
  }
}
.congo-text {
  margin-bottom: 20px;
  @media (min-width: 768px) {
    //padding-bottom: 16px;
  }
}
.verify-text {
  @media (min-width: 768px) {
    padding-top: 12px;
  }
}

.header-container {
  flex-shrink: 0;
}
.body-container {
  flex-grow: 1;
  overflow: auto;
  min-height: 2em;
}
.footer-container {
  flex-shrink: 0;
}
.body-container::-webkit-scrollbar {
  display: none;
}

.v-btn-cancel {
  background-color: #fff !important;
  border: 1px solid $color-brand;
  color: $color-brand;

  &:hover {
    background-color: $color-brand !important;
    color: #fff;
  }
}

.v-btn-submit {
  background-color: $color-success !important;
  border: 1px solid $color-success;
  color: #fff;
  &:hover {
    background-color: #fff !important;
    color: $color-success;
  }
}
</style>

