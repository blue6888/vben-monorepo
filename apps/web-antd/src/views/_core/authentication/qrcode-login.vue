<script lang="ts" setup>
import { AuthenticationQrCodeLogin } from '@web/common-ui';
import { LOGIN_PATH } from '@web/constants';

defineOptions({ name: 'QrCodeLogin' });
</script>

<template>
  <AuthenticationQrCodeLogin :login-path="LOGIN_PATH" />
</template>
