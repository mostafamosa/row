<template>
  <div class="api-docs__item">
    <div class="api-docs__left">
      <h2 id="section-authentication" class="api-docs__heading-2">
        {{ $t('apiDocs.authent') }}
      </h2>
      <i18n path="apiDocsAuth.description" tag="p" class="api-docs__content">
        <template #settingsLink>
          <a @click.prevent="$refs.settingsModal.show('tokens')">{{
            $t('apiDocsAuth.settingsLink')
          }}</a>
        </template>
      </i18n>
    </div>
    <div class="api-docs__right">
      <APIDocsExample
        :value="value"
        :url="$config.PUBLIC_BACKEND_URL"
        :include-user-fields-checkbox="false"
        type=""
        @input="$emit('input', $event)"
      ></APIDocsExample>
    </div>
    <SettingsModal ref="settingsModal"></SettingsModal>
  </div>
</template>

<script>
import SettingsModal from '@baserow/modules/core/components/settings/SettingsModal'
import APIDocsExample from '@baserow/modules/database/components/docs/APIDocsExample'

export default {
  name: 'APIDocsAuth',
  components: {
    SettingsModal,
    APIDocsExample,
  },
  props: {
    value: {
      type: Object,
      required: true,
    },
  },
}
</script>
