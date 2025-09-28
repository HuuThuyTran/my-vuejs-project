<script setup>
import { reactive, ref, toRefs } from 'vue';

defineOptions({ name: 'AppBody' });
let body = "Body Component";

// Interpolation & Data (ref(), reactive())
let myFullName = ref("Trần Hữu Thủy")
let myAge = ref(22)
let myAddress = ref("Quảng Nam")
let myBirthday = ref("30/04/2003")
let myIsGender = ref(true)
let myHobbies = ref(["Ăn", "Ngủ", "Chơi game", "Xem phim", "Code", "Đá bóng"])

let girl = reactive({
  fullName: "Nguyễn Thị Thùy Dương",
  age: 22,
  address: "Quảng Nam",
  birthday: "15/08/2003",
  isGender: false
})

let hobbies = reactive(["Ăn", "Ngủ", "Chơi game", "Xem phim", "Du lịch"])

let cars = ref(["BMW", "Mercedes", "Audi", "Lexus"])

const { fullName, age, address, birthday, isGender } = toRefs(girl)

// Events: 25/09/2025 - học tiếp
const name = ref("")

const increaseAge = () => {
  age.value++
}

const greeting = (event) => {
  console.log(111, event);
}

function handleInput(e) {
  console.log("Input:", e.target.value)
}
function handleChange(e) {
  console.log("Change:", e.target.value)
}
function handleSubmit() {
  alert(`Form submitted với tên: ${name.value}`)
}

function mouseOver() {
  console.log("Chuột đang ở trong div")
}
function mouseOut() {
  console.log("Chuột đã rời khỏi div")
}

function onScroll(e) {
  console.log("Scroll Top:", e.target.scrollTop)
}

function warn(message, event) {
  // now we have access to the native event
  if (event) {
    event.preventDefault()
  }
  alert(message)
}

// v-model
const checked = ref(false)
const gender = ref("")
const selectedFood = ref("")


</script>

<template>
  <h1>{{ body }}</h1>
  <div>
    <h3>My Information:</h3>
    <p>Fullname: {{ myFullName }}</p>
    <p>Age: {{ myAge }}</p>
    <p>Address: {{ myAddress }}</p>
    <p>Birthday: {{ myBirthday }}</p>
    <p>Gender: {{ myIsGender ? 'Nam' : 'Nữ' }}</p>
    <p>Hobbies: {{ myHobbies.join(', ') }}</p>
  </div>
  <hr>
  <div>
    <h3>Girl's Information:</h3>
    <p>Fullname's girl: {{ girl.fullName }}</p>
    <p>Age: {{ girl.age }}</p>
    <p>Address: {{ girl.address }}</p>
    <p>Birthday: {{ girl.birthday }}</p>
    <p>Gender: {{ girl.isGender ? 'Nam' : 'Nữ' }}</p>
    <p>Hobbies: {{ hobbies.join(', ') }}</p>
  </div>
  <hr>
  <div>
    <p>Cars: {{ cars.join(" - ") }}</p>
  </div>
  <hr>
  <div>
    <h3>Keep reactive toRefs:</h3>
    <p>Fullname: {{ fullName }}</p>
    <p>Age: {{ age }}</p>
    <p>Address: {{ address }}</p>
    <p>Birthday: {{ birthday }}</p>
    <p>Gender: {{ isGender ? 'Nam' : 'Nữ' }}</p>
  </div>
  <hr>
  <div>
    <!-- Cú pháp chuẩn: @eventName="handler" -->
    <!-- Các event hay dùng: @click @input, @change, @submit.prevent @keydown, @keyup.enter @mouseover, @mouseout @scroll -->
    <h3>Events:</h3>
    <h4>+ Mouse Events:</h4>
    <p>@click: <button @click="increaseAge">Increase</button></p>
    <p>@click: <button @click="greeting('Greeting')">Greeting</button></p>

    <p>@input, @change, @submit.prevent</p>
    <form action="" @submit.prevent="handleSubmit">
      <input type="text" v-model="name" placeholder="Enter your name" @input="handleInput" @change="handleChange" />
      <button type="submit">Submit</button>
    </form>

    <div @mouseover="mouseOver" @mouseout="mouseOut">
      <b>Rê chuột vào/ra rồi nhấn</b>
    </div>

    <div @scroll="onScroll">
      <p v-for="n in 20" :key="n">Dòng số {{ n }}</p>
    </div>

    <div>
      <button @click="(event) => warn('Form cannot be submitted yet.', event)">
        Submit
      </button>
    </div>
  </div>
  <div>
    <!-- v-model -->
    <!-- Cách sử dụng: nằm trong thẻ input(text, checkbox, radio, select) -->
    <hr>
    <h3>V-MODEL</h3>
    <input type="text" v-model.lazy="name" placeholder="Enter your name" />
    <p>Tên của bạn là: {{ name }}</p>
    <hr>
    <input type="checkbox" v-model="checked" />
    <p>Trạng thái: {{ checked }}</p>
    <hr>
    <input type="radio" value="Nam" v-model="gender"> Nam
    <input type="radio" value="Nữ" v-model="gender"> Nữ
    <p>Gioi tinh: {{ gender }}</p>
    <hr>
    <select v-model="selectedFood">
      <option disabled value="">Chọn món ăn</option>
      <option value="Pizza">Pizza</option>
      <option value="Burger">Burger</option>
      <option value="Salad">Salad</option>
    </select>
    <p>Món ăn bạn chọn: {{ selectedFood }}</p>

  </div>
</template>
