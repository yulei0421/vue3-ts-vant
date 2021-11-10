<template>
  <p>Welcome home!</p>
  <van-button type="primary">主要按钮</van-button>
  <van-cell title="选择单个日期" :value="date" @click="show = true" />
  <van-calendar v-model:show="show" @confirm="onConfirm" />
  <Slot>1111</Slot>
  <van-checkbox-group v-model="checked">
    <van-checkbox name="a">复选框 a</van-checkbox>
    <van-checkbox name="b">复选框 b</van-checkbox>
  </van-checkbox-group>
  <About :title="title" />
</template>

<script>
import { Button, Checkbox, CheckboxGroup } from "vant";
import { ref } from "vue";
import About from "./About.vue";
import Slot from "../components/Slot.vue";
export default {
  components: {
    About,
    Button,
    Slot,
    Checkbox,
    CheckboxGroup,
  },
  setup() {
    const date = ref("");
    const show = ref(false);
    const title = ref("请选择日期");
    const checked = ref(["a", "b"]);

    const formatDate = (date) => `${date.getMonth() + 1}/${date.getDate()}`;
    const onConfirm = (value) => {
      title.value = "你已选择日期";
      console.log(value, title, "value");

      show.value = false;
      date.value = formatDate(value);
    };

    return {
      date,
      show,
      onConfirm,
      title,
      checked,
    };
  },
};
</script>
<style>
    
</style>