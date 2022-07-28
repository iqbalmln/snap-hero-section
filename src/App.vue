<script setup lang="ts">
import AppNav from "./components/AppNav.vue";
</script>

<template>
  <div class="container">
    <AppNav class="nav" />
    <main>
      <div class="main-col left">
        <div class="main-caption">
          <h1>Make remote work</h1>
          <p>
            Get your team in sync, no matter your location. Streamline
            processes, create team rituals, and watch productivity soar.
          </p>
          <button>Learn more</button>
          <div class="client">
            <div class="client-image">
              <img src="@/assets/images/client-databiz.svg" />
            </div>
            <div class="client-image">
              <img src="@/assets/images/client-audiophile.svg" />
            </div>
            <div class="client-image">
              <img src="@/assets/images/client-meet.svg" />
            </div>
            <div class="client-image">
              <img src="@/assets/images/client-maker.svg" />
            </div>
          </div>
        </div>
      </div>
      <div class="main-col right">
        <img src="./assets/images/image-hero-desktop.png" />
      </div>
      <div class="main-col right-mobile">
        <img src="./assets/images/image-hero-mobile.png" />
      </div>
    </main>
  </div>
</template>

<style lang="scss">
@import "./assets/sass/main.scss";
.container {
  position: relative;
  overflow: hidden;
  main {
    @media (min-width: 800px) {
      padding: 0 120px;
      flex-direction: row;
    }
    height: 100vh;
    width: 100%;
    flex-direction: column-reverse;
    display: flex;
    justify-content: space-around;
    align-items: center;
    .main-col {
      height: 70vh;
      &.left {
        flex-basis: 40%;
        display: flex;
        align-items: flex-end;
        @media (max-width: 768px) {
          padding: 1rem;
        }
        .main-caption {
          display: flex;
          flex-direction: column;
          justify-content: flex-end;
          gap: 2rem;
          @media (max-width: 768px) {
            align-items: center;
          }
          align-items: flex-start;
          h1 {
            @media (max-width: 768px) {
              text-align: center;
              font-size: 32px;
            }
            font-size: 72px;
          }
          p {
            @media (max-width: 768px) {
              text-align: center;
            }
            color: #000;
            opacity: 50%;
          }
          button {
            background: #000;
            color: #fff;
            padding: 0.75rem 1.5rem;
            outline: none;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            border: 2px solid #000;
            cursor: pointer;
            font-family: "Epilogue", sans-serif;
            transition: 0.25s ease;
            &:hover {
              background: none;
              color: #000;
              border: 2px solid #000;
            }
          }
          .client {
            @media (max-width: 768px) {
              margin-top: 0;
              img {
                width: 4rem;
              }
            }
            margin-top: 5rem;
            display: flex;
            width: 100%;
            gap: 1rem;
            justify-content: space-between;
          }
        }
      }
      &.right {
        @media (max-width: 768px) {
          display: none;
        }
        flex-basis: 50%;
        display: flex;
        justify-content: flex-end;
        height: 70vh;
        img {
          height: 100%;
        }
      }
      &.right-mobile {
        @media (min-width: 800px) {
          display: none;
        }
        margin-top: 10%;
        img {
          width: 100%;
        }
      }
    }
  }
}
</style>
