<template>
  <div>
    <div class="left-content">
      <DxTextArea :height="90" :max-length="maxLength" v-model:value="value" />
    </div>
    <div class="full-width-content">
      <DxTextArea
        :height="90"
        v-model:value="valueForEditableTextArea"
        :value-change-event="eventValue"
      />
      <DxTextArea
        :inputAttr="{
          wrap: 'off',
          rows: '1',
          style: 'white-space: nowrap;',
        }"
        :read-only="true"
        :value="valueText"
      />
    </div>
  </div>
</template>
<script>
import DxTextArea from "devextreme-vue/text-area";

import service from "./data.js";

export default {
  components: {
    DxTextArea,
  },
  data() {
    return {
      eventValue: service.valueChangeEvents[0].name,
      maxLength: null,
      value: service.getContent(),
      valueForEditableTextArea: service.getContent(),
    };
  },
  computed: {
    valueText() {
      let _text = "asdasdfkajhgflafkjghsdlghlsdgfh";
      for (let i = 0; i < 10; i++) {
        _text += _text;
      }
      return _text;
    },
  },
};
</script>
<style>
.full-width-content {
  width: 100%;
  margin-top: 30px;
}

.full-width-content > .dx-widget {
  margin-bottom: 20px;
}

.full-width-content .dx-field {
  max-width: 385px;
}
</style>
