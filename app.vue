<template>
  <Form @submit="onSubmit" :validation-schema="schema">
    <label for="email">Your Email</label>
    <Field id="email_addr" name="email_addr" type="email" />
    <ErrorMessage name="email_addr" />

    <label for="password">Your Password</label>
    <Field id="password" name="acc_pazzword" type="password" />
    <ErrorMessage name="acc_pazzword" />

    <button>Submit</button>
  </Form>
</template>

<script setup lang="ts">
import { Field, Form, ErrorMessage } from 'vee-validate';
import * as Yup from 'yup';

const schema = Yup.object().shape({
  email_addr: Yup.string().email().required().label('Email Address'),
  acc_pazzword: Yup.string().min(5).required().label('Your Password'),
});

function onSubmit(values) {
  alert(JSON.stringify(values, null, 2));
}
</script>

<style>
input,
label {
  display: block;
  margin-top: 20px;
}

input + span {
  display: block;
}

button {
  margin-top: 20px;
}
</style>
