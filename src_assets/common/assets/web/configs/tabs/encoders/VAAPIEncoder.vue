<script setup>
import { ref } from 'vue'
import Checkbox from "../../../Checkbox.vue";
import CodecSupportPanel from "./CodecSupportPanel.vue";

const props = defineProps([
  'platform',
  'config',
])

const config = ref(props.config)
</script>

<template>
  <div id="vaapi-encoder" class="config-page">
    <section class="settings-section settings-section-compact">
      <div class="settings-section-header">
        <div class="section-kicker">Linux GPU Encoding</div>
        <h3 class="settings-section-title">VA-API behavior</h3>
        <p class="settings-section-copy">Tune Polaris's VA-API path for AMD and Intel GPUs: rate-control mode, driver features, and strict bitrate compliance.</p>
      </div>

      <CodecSupportPanel :config="config" />

      <Checkbox class="mb-3"
                id="vaapi_strict_rc_buffer"
                locale-prefix="config"
                v-model="config.vaapi_strict_rc_buffer"
                default="false"
      ></Checkbox>

      <div class="settings-subtle-surface mb-3">
        <div class="eyebrow-label mb-2">{{ $t('config.vaapi_rc_group') }}</div>
        <div class="mb-0">
          <label for="vaapi_rc_mode" class="block text-sm font-medium text-storm mb-1">{{ $t('config.vaapi_rc_mode') }}</label>
          <select id="vaapi_rc_mode" class="settings-input" v-model="config.vaapi_rc_mode">
            <option value="0">{{ $t('config.vaapi_rc_auto') }}</option>
            <option value="1">{{ $t('config.vaapi_rc_cqp') }}</option>
            <option value="2">{{ $t('config.vaapi_rc_cbr') }}</option>
            <option value="3">{{ $t('config.vaapi_rc_vbr') }}</option>
            <option value="4">{{ $t('config.vaapi_rc_icq') }}</option>
            <option value="5">{{ $t('config.vaapi_rc_qvbr') }}</option>
            <option value="6">{{ $t('config.vaapi_rc_avbr') }}</option>
          </select>
          <div class="text-sm text-storm mt-1">{{ $t('config.vaapi_rc_mode_desc') }}</div>
        </div>
      </div>

      <div class="settings-subtle-surface">
        <div class="eyebrow-label mb-2">{{ $t('config.vaapi_driver_features_group') }}</div>
        <Checkbox class="mb-3"
                  id="vaapi_low_power"
                  locale-prefix="config"
                  v-model="config.vaapi_low_power"
                  default="false"
        ></Checkbox>

        <Checkbox class="mb-0"
                  id="vaapi_blbrc"
                  locale-prefix="config"
                  v-model="config.vaapi_blbrc"
                  default="false"
        ></Checkbox>
      </div>
    </section>
  </div>
</template>

<style scoped>

</style>
