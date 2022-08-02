<template>
  <q-page class="q-ma-md">
    <span class="text-h3"> Forms </span>
    <q-separator spaced />

    <div class="row justify-center">
      <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-xs col-md-8 col-12 q-pt-xl"
      >
        <q-input
          filled
          v-model="userForm.email"
          label="Type Email"
          hint="email"
          type="email"
          no-error-icon
          lazy-rules
          :rules="[
            (val) => (val && val.length > 0) || 'This field is required',
            isValidEmail,
          ]"
        />

        <q-input
          filled
          type="password"
          v-model="userForm.password1"
          label="Password"
          lazy-rules
          no-error-icon
          :rules="[
            (val) => (val && val.length > 0) || 'This field is required',
          ]"
        />
        <q-input
          filled
          type="password"
          v-model="userForm.password2"
          label="Repet password"
          no-error-icon
          lazy-rules
          :rules="[
            (val) => (val && val.length > 0) || 'This field is required',
            isSamePassword,
          ]"
        />

        <q-checkbox
          v-model="userForm.conditions"
          label="I accept conditions"
          :style="
            userForm.errorInConditions && !userForm.conditions && 'color: red'
          "
        />

        <div class="row justify-end">
          <q-btn
            label="Reset"
            type="reset"
            color="primary"
            flat
            class="q-ml-sm"
          />
          <q-btn unelavated label="Submit" type="submit" color="primary" />
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from "vue";
import { useQuasar } from "quasar";

export default defineComponent({
  name: "Forms",

  setup() {
    const $q = useQuasar();

    const userForm = ref({
      email: "",
      password1: "",
      password2: "",
      conditions: false,
      errorInConditions: false,
    });

    return {
      userForm,
      onSubmit() {
        userForm.value.errorInConditions = false;
        if (!userForm.value.conditions) {
          userForm.value.errorInConditions = true;
          $q.notify({
            message: "You should accept conditions.",
            icon: "las la-exclamation-circle",
          });
          return;
        } else {
          // enviamos datos:
          console.log(userForm.value);
        }
      },
      onReset() {
        userForm.value = {
          email: "",
          password1: "",
          password2: "",
          conditions: false,
          errorInConditions: false,
        };
      },
      isValidEmail(val) {
        const emailPattern =
          /^(?=[a-zA-Z0-9@._%+-]{6,254}$)[a-zA-Z0-9._%+-]{1,64}@(?:[a-zA-Z0-9-]{1,63}\.){1,8}[a-zA-Z]{2,63}$/;
        return emailPattern.test(val) || "El correo no parece ser válido";
      },
      isSamePassword(val) {
        return val === userForm.value.password1 || "Password isn't equals.";
      },
    };
  },
});
</script>

<style></style>
