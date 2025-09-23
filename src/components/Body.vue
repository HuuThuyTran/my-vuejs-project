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
</template>
