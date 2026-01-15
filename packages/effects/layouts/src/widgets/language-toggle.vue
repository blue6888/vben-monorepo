<script setup lang="ts">
import type { SupportedLanguagesType } from '@web/locales';

import { SUPPORT_LANGUAGES } from '@web/constants';
import { Languages } from '@web/icons';
import { loadLocaleMessages } from '@web/locales';
import { preferences, updatePreferences } from '@web/preferences';

import { VbenDropdownRadioMenu, VbenIconButton } from '@web-core/shadcn-ui';

defineOptions({
  name: 'LanguageToggle',
});

async function handleUpdate(value: string | undefined) {
  if (!value) return;
  const locale = value as SupportedLanguagesType;
  updatePreferences({
    app: {
      locale,
    },
  });
  await loadLocaleMessages(locale);
}
</script>

<template>
  <div>
    <VbenDropdownRadioMenu
      :menus="SUPPORT_LANGUAGES"
      :model-value="preferences.app.locale"
      @update:model-value="handleUpdate"
    >
      <VbenIconButton class="hover:animate-[shrink_0.3s_ease-in-out]">
        <Languages class="text-foreground size-4" />
      </VbenIconButton>
    </VbenDropdownRadioMenu>
  </div>
</template>
