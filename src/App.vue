<script setup>
import { ref } from "vue";
import ResultState from "./components/ResultState.vue";

const isVisible = ref(false);
const activeRef = ref(null);
const rates = ref([1, 2, 3, 4, 5]);

</script>

<template>
  <main>
    <div v-show="!isVisible" class="card-container">
      <div class="content-container">
        <div class="star-icon">
          <img src="./assets/images/icon-star.svg" alt="" />
        </div>
        <div class="text">
          <h1>How did we do?</h1>
          <p>
            Please let us know how we did with your support request. All
            feedback is appreciated to help us improve our offering!
          </p>
        </div>

        <ul>
          <li
            v-for="rate in rates"
            :key="rate"
            @click="activeRef = rate"
            class="rating"
            :class="{ active: activeRef === rate }"
          >
            {{ rate }}
          </li>
        </ul>

        <button @click="isVisible = !isVisible" class="btn">Submit</button>
      </div>
    </div>
  </main>
  <div v-show="isVisible">
    <ResultState :activeRef="activeRef" />
  </div>
</template>

<style lang="scss" scoped>
@use "./main.scss" as *;
.card-container {
  display: flex;
  align-items: center;
  max-width: 26rem;
  background-image: linear-gradient(hsl(213, 19%, 18%), hsl(216, 12%, 11%));
  border-radius: 2rem;
  .content-container {
    margin: $baseMargin * 2;

    .star-icon {
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: $baseMargin * 2;
      background-color: hsl(213, 19%, 23%);
      width: 3rem;
      height: 3rem;
      border-radius: 50%;
    }
    .text h2 {
      font-size: 2rem;
      font-weight: 400;
    }
    .text p {
      color: $lightGray;
      margin-top: $baseMargin;
    }
    ul {
      margin-top: $baseMargin * 2;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-left: 0;

      .rating {
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: hsl(213, 19%, 23%);
        width: 3rem;
        height: 3rem;
        color: $lightGray;
        border-radius: 50%;
        cursor: pointer;
        &.active {
          background-color: $orange;
          color: white;
          &:hover {
            background-color: $orange;
          }
        }
        &:hover {
          background-color: $lightGray;
          color: white;
          transition: 0.4s;
        }
      }
    }
    .btn {
      margin-top: $baseMargin * 2;
      cursor: pointer;
      text-transform: uppercase;
      color: white;
      background-color: $orange;
      border: none;
      border-radius: 3rem;
      width: 100%;
      height: 2.5rem;
      letter-spacing: 2px;
      &:hover {
        background-color: white;
        color: $orange;
        transition: 0.5s;
      }
    }
  }
}
</style>
