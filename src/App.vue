<template>
  <div id="header" class="flex justify-center bg-white p-8">
    <h1 class="text-5xl">復興資傳</h1>
  </div>
  <div class="">
    <transition
      name="signIn"
      enter-from-class="opacity-0 -translate-x-[50px] "
      enter-active-class="transition duration-200 ease-in-out delay-[500ms]"
      enter-to-class="opacity-100 translate-x-0 "
      leave-from-class="opacity-100 translate-x-0"
      leave-active-class="transition duration-200 ease-in-out "
      leave-to-class="opacity-0 -translate-x-[50px] "
    >
      <div
        key="signinPage"
        v-show="OnInPage"
        class="flex w-full flex-col items-center space-y-4 bg-white"
      >
        <p class="text-3xl">登入</p>
        <form
          @submit.prevent="signin"
          class="flex flex-col items-center space-y-4"
        >
          <input
            type="text"
            placeholder="請輸入帳號"
            name="acc"
            v-model="acc"
            autocomplete="off"
            required
            class="w-[50vw] rounded-md border-[1px] border-gray-400 p-2"
          />
          <div class="relative">
            <input
              :type="cansee"
              placeholder="請輸入密碼"
              name="pass"
              v-model="pass"
              autocomplete="off"
              required
              class="w-[50vw] rounded-md border-[1px] border-gray-400 p-2"
            />
            <div @click="showpassword($event)" class="w-[20px]">
              <i
                class="fa-solid fa-eye absolute top-[14px] right-[8px] cursor-pointer text-gray-400 hover:text-gray-600"
              ></i>
            </div>
          </div>

          <button
            class="w-[50vw] rounded-md bg-gradient-to-b from-green-900 to-green-600 py-1 text-lg text-white"
          >
            登入
          </button>
        </form>
        <button
          @click="swToSignup"
          class="w-[50vw] rounded-md bg-gradient-to-b from-orange-600 to-orange-400 py-1 text-lg text-white"
        >
          申請註冊
        </button>
      </div>
    </transition>
    <transition
      name="signUp"
      enter-from-class="opacity-0 translate-x-[50px] "
      enter-active-class="transition duration-200 ease-in-out delay-[500ms]"
      enter-to-class="opacity-100 translate-x-0 "
      leave-from-class="opacity-100 "
      leave-active-class="transition duration-200 ease-in-out"
      leave-to-class="opacity-0 translate-x-[50px]"
    >
      <div
        key="signupPage"
        v-show="OnUpPage"
        class="flex w-full flex-col items-center space-y-4 bg-white"
      >
        <p class="text-3xl">註冊</p>
        <form class="flex flex-col space-y-4">
          <input
            type="text"
            placeholder="請輸入帳號"
            required
            class="w-[50vw] rounded-md border-[1px] border-gray-400 p-2"
          />
          <input
            type="password"
            placeholder="請輸入密碼"
            required
            class="w-[50vw] rounded-md border-[1px] border-gray-400 p-2"
          />
          <input
            type="password"
            placeholder="請重複輸入密碼"
            required
            class="w-[50vw] rounded-md border-[1px] border-gray-400 p-2"
          />
          <input
            type="text"
            placeholder="請輸入真實姓名"
            required
            class="w-[50vw] rounded-md border-[1px] border-gray-400 p-2"
          />
          <input
            type="email"
            placeholder="請輸入電子信箱"
            required
            class="w-[50vw] rounded-md border-[1px] border-gray-400 p-2"
          />
          <div class="h-1"></div>
          <button
            class="rounded-md bg-gradient-to-b from-orange-600 to-orange-400 py-1 text-lg text-white"
          >
            註冊
          </button>
        </form>
        <button
          @click="swToSignin"
          class="w-[50vw] rounded-md bg-gradient-to-b from-green-900 to-green-600 py-1 text-lg text-white"
        >
          回到登入
        </button>
      </div>
    </transition>
  </div>
  <div
    id="footer"
    class="flex justify-evenly bg-white p-10 text-lg text-gray-600"
  >
    <a href="#" target="_blank"><p>常見問題</p></a>
    <a href="#" target="_blank"><p>服務條款</p></a>
  </div>
</template>

<script>
import { ref } from "vue";
import "animate.css";
export default {
  setup() {
    const acc = ref("");
    const pass = ref("");
    const cansee = ref("password");
    const showpassword = function (event) {
      if (event.target.tagName == "path") {
        event.target.parentNode.classList.toggle("fa-eye");
        event.target.parentNode.classList.toggle("fa-eye-slash");
      }
      if (cansee.value == "password") {
        cansee.value = "text";
      } else {
        cansee.value = "password";
      }
      event.target.classList.toggle("fa-eye");
      event.target.classList.toggle("fa-eye-slash");
    };
    const signin = function () {
      alert("帳號:" + acc.value + "\n" + "密碼:" + pass.value);
      acc.value = "";
      pass.value = "";
    };
    const OnInPage = ref("y");
    const OnUpPage = ref("");
    const swToSignup = function () {
      OnInPage.value = "";
      OnUpPage.value = "y";
    };
    const swToSignin = function () {
      OnUpPage.value = "";
      OnInPage.value = "y";
    };
    return {
      acc,
      pass,
      cansee,
      showpassword,
      signin,
      OnInPage,
      OnUpPage,
      swToSignup,
      swToSignin,
    };
  },
};
</script>

<style></style>
