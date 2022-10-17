<template>
  <div class="h-full w-full relative bg-blue-50">
    <div
      class="p-4 h-24 w-4/5 mx-auto bg-white rounded-xl shadow-md flex items-center space-x-4 absolute left-1/2 -translate-x-1/2 top-24"
    >
      <div class="flex-shrink-0">
        <img class="h-12 w-12" src="../assets/bill.svg" alt="ChitChat Logo" />
      </div>
      <div>
        <div class="text-xl font-medium text-black">Silly Bill</div>
        <p class="text-gray-500">Enter the secret key to unlock</p>
      </div>
    </div>
    <div
      class="w-4/5 absolute left-1/2 -translate-x-1/2 top-1/2 -translate-y-1/2 flex flex-col mb-4"
    >
      <input
        type="password"
        v-model="key"
        placeholder="请输入密钥"
        class="input input-bordered input-info w-full input-md max-w-xs"
      />
      <button class="btn btn-info mt-4" @click="unlock">解锁</button>
    </div>
    <div class="toast" v-if="showToast">
      <div class="alert alert-info">
        <div>
          <span>密码不正确，请重新输入</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watchEffect } from "vue";
import secretkey from "../../SecretKey.json";

const key = ref<string>("");
const showToast = ref<boolean>(false);

const unlock = () => {
  if (key.value !== secretkey.key) {
    showToast.value = true;
    setTimeout(() => {
      showToast.value = false;
    }, 2000);
  }else{
  }
};
</script>
