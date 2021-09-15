<template>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field
      v-model="inputData.name"
      :rules="validRules.name"
      :counter="10"
      label="Name"
      required
    ></v-text-field>

    <v-text-field
      v-model="inputData.email"
      :rules="validRules.email"
      label="E-mail"
      required
    ></v-text-field>

    <v-select
      v-model="inputData.select"
      :rules="validRules.items"
      :items="items.select"
      label="Item"
      required
    ></v-select>

    <v-checkbox
      v-model="inputData.checkbox"
      :rules="validRules.checkbox"
      label="Do you agree?"
      required
    ></v-checkbox>

    <div class="d-flex flex-wrap">
      <v-btn
        :disabled="!valid"
        color="secondary"
        class="mx-1 my-1"
        width="calc(50% - 8px)"
        @click="validate"
      >
        キャンセル
      </v-btn>
      <v-btn
        :disabled="!valid"
        color="primary"
        class="mx-1 my-1"
        width="calc(50% - 8px)"
        @click="validate"
      >
        確認
      </v-btn>

    </div>
  </v-form>
</template>

<script>
  export default {
    data: () => ({
      valid: true,
      validRules: {
        name: [
          v => !!v || 'Name is required',
          v => (v && v.length <= 10) || 'Name must be less than 10 characters',
        ],
        email: [
          v => !!v || 'E-mail is required',
          v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
        ],
        items: [v => !!v || 'Item is required'],
        checkbox: [v => !!v || 'You must agree to continue!'],
      },
      inputData: {
        name: '',
        email: '',
        select: null,
        checkbox: false,
      },
      items: {
        select: [
          'Item 1',
          'Item 2',
          'Item 3',
          'Item 4',
        ],
      }
    }),

    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
  }
</script>