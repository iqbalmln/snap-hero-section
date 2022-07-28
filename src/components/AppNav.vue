<script setup>
import { ref } from "vue";
// Feature
const isClicked = ref(true);
const featureActive = ref([
  {
    id: 0,
    img: "notepad",
    name: "Todo List",
  },
  {
    id: 1,
    img: "calendar",
    name: "Calendar",
  },
  {
    id: 2,
    img: "bell",
    name: "Reminders",
  },
  {
    id: 3,
    img: "search-alt-2",
    name: "Planning",
  },
]);

// Company
const isClickedCompany = ref(true);
const companyActive = ref([
  {
    id: 0,
    name: "History",
  },
  {
    id: 1,
    name: "Out Team",
  },
  {
    id: 2,
    name: "Blog",
  },
]);

const activeMenu = ref(false);
const featureActiveMobile = ref(false);
const companyActiveMobile = ref(false);
</script>

<template>
  <Transition>
    <div v-if="activeMenu" class="overlay" />
  </Transition>
  <header>
    <div class="navigasi">
      <img src="../assets/images/logo.svg" />
      <nav>
        <li class="features">
          <a href="" @click.prevent="isClicked = !isClicked">Features</a>
          <box-icon
            v-if="isClicked"
            name="chevron-down"
            color="gray"
            class="icon"
          />
          <box-icon v-else name="chevron-up" color="gray" class="icon" />
          <Transition>
            <div v-if="!isClicked" class="menu-features">
              <li v-for="feature in featureActive" :key="feature.id">
                <box-icon
                  :name="feature.img"
                  color="gray"
                  class="icon"
                  size="sm"
                />
                {{ feature.name }}
              </li>
            </div>
          </Transition>
        </li>
        <li class="company">
          <a href="" @click.prevent="isClickedCompany = !isClickedCompany"
            >Company</a
          >
          <box-icon
            v-if="isClickedCompany"
            name="chevron-down"
            color="gray"
            class="icon"
          />
          <box-icon v-else name="chevron-up" color="gray" class="icon" />
          <Transition>
            <div v-if="!isClickedCompany" class="menu-company">
              <li v-for="company in companyActive" :key="company.id">
                {{ company.name }}
              </li>
            </div>
          </Transition>
        </li>
        <li>
          <a href="">Careers</a>
        </li>
        <li>
          <a href="">About</a>
        </li>
      </nav>
    </div>
    <div class="nav-button">
      <button>Login</button>
      <button>Register</button>
    </div>
  </header>
  <div class="header-mobile">
    <div class="header-mobile-inner">
      <img src="../assets/images/logo.svg" />
      <div>
        <box-icon
          v-if="!activeMenu"
          @click="activeMenu = !activeMenu"
          name="menu"
          class="icon-menu"
        />
        <box-icon
          v-else
          @click="activeMenu = !activeMenu"
          name="x"
          class="icon-menu"
        />
      </div>
    </div>
    <div class="menu-item" :class="{ active: activeMenu }">
      <ul class="ul-menu">
        <li class="features-mobile">
          <a href="">Features</a>
          <box-icon
            @click="featureActiveMobile = !featureActiveMobile"
            name="chevron-down"
            color="gray"
          />
        </li>
        <li class="child-menu-feature" v-show="featureActiveMobile">
          <span style="display: block">Todo List</span>
          <span style="display: block">Calendar</span>
          <span style="display: block">Reminders</span>
          <span style="display: block">Planning</span>
        </li>
        <li class="company-mobile">
          <a href="">Company</a>
          <box-icon
            @click="companyActiveMobile = !companyActiveMobile"
            name="chevron-down"
            color="gray"
          />
        </li>
        <li class="child-menu-company" v-show="companyActiveMobile">
          <span style="display: block">Todo List</span>
          <span style="display: block">Calendar</span>
          <span style="display: block">Reminders</span>
          <span style="display: block">Planning</span>
        </li>
        <li><a href="">Careers</a></li>
        <li><a href="">About</a></li>
      </ul>
      <div class="nav-button">
        <button>Login</button>
        <button>Register</button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.25s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  background-color: #000;
  opacity: 50%;
  z-index: 97;
  width: 100%;
  height: 100vh;
}
header {
  @media (max-width: 768px) {
    display: none;
  }
  position: absolute;
  display: flex;
  width: 100%;
  justify-content: space-between;
  padding: 2rem;
  .navigasi {
    display: flex;
    align-items: center;
    gap: 5rem;

    nav {
      display: flex;
      align-items: center;
      gap: 2.5rem;
      li {
        list-style: none;
        display: flex;
        align-items: center;
        font-size: 14px;
        color: hsl(0, 0%, 41%);
        &.features {
          position: relative;
          .menu-features {
            position: absolute;
            top: 30px;
            left: -20px;
            width: 120px;
            padding: 12px;
            display: flex;
            flex-direction: column;
            border-radius: 8px;
            gap: 16px;
            box-shadow: 0px 0px 16px -4px rgba(74, 74, 74, 0.2);
            li {
              font-size: 12px;
              display: flex;
              gap: 10px;
              align-items: center;
            }
          }
        }
        &.company {
          position: relative;
          .menu-company {
            position: absolute;
            top: 30px;
            width: 100px;
            padding: 12px;
            display: flex;
            flex-direction: column;
            border-radius: 8px;
            gap: 16px;
            box-shadow: 0px 0px 16px -4px rgba(74, 74, 74, 0.2);
            li {
              font-size: 12px;
              display: flex;
              gap: 10px;
              align-items: center;
            }
          }
        }

        a {
          color: hsl(0, 0%, 41%);
          text-decoration: none;
          font-weight: 600;
          &:hover {
            color: black;
          }
        }
      }
    }
  }
  .nav-button {
    display: flex;
    gap: 3rem;
    button {
      font-family: "Epilogue", sans-serif;
      background: none;
      outline: none;
      border: none;
      color: hsl(0, 0%, 41%);
      cursor: pointer;
      transition: 0.3s ease;
      font-weight: 600;
      &:nth-child(2) {
        border: 2px solid hsl(0, 0%, 41%);
        border-radius: 6px;
        padding: 0.5rem 1rem;
        font-weight: 600;
        transition: 0.3s ease;
        &:hover {
          border: 2px solid #000;
          color: #000;
        }
      }
      &:hover {
        color: #000;
      }
    }
  }
}
.header-mobile {
  position: relative;
  @media (min-width: 800px) {
    display: none;
  }
  .header-mobile-inner {
    display: flex;
    justify-content: space-between;
    padding: 1rem;
    .icon-menu {
      position: absolute;
      top: 1rem;
      right: 1rem;
      z-index: 99;
    }
  }
  .menu-item {
    position: absolute;
    top: 0;
    right: -70%;
    background: #fff;
    width: 70%;
    height: 100vh;
    box-shadow: 0px 0px 16px -4px rgba(74, 74, 74, 0.2);
    z-index: 98;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    transition: 0.5s ease-in;
    .ul-menu {
      padding: 20% 1.5rem;
      display: flex;
      flex-direction: column;
      gap: 2rem;
      .child-menu-feature {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        color: hsl(0, 0%, 41%);
        padding-left: 1rem;
      }
      .child-menu-company {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        color: hsl(0, 0%, 41%);
        padding-left: 1rem;
      }
      .features-mobile {
        display: flex;
        align-items: center;
        gap: 4px;
      }
      .company-mobile {
        display: flex;
        align-items: center;
      }
      li {
        list-style: none;
        a {
          text-decoration: none;
          color: hsl(0, 0%, 41%);
          cursor: pointer;
        }
      }
    }
    .nav-button {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      padding: 1rem 1.5rem;
      button {
        font-family: "Epilogue", sans-serif;
        background: none;
        outline: none;
        border: none;
        color: hsl(0, 0%, 41%);
        cursor: pointer;
        transition: 0.3s ease;
        &:nth-child(2) {
          border: 1.5px solid hsl(0, 0%, 41%);
          border-radius: 12px;
          padding: 0.5rem 1rem;
          transition: 0.3s ease;
          &:hover {
            border: 1.5px solid #000;
            color: #000;
          }
        }
        &:hover {
          color: #000;
        }
      }
    }
  }
  .active {
    right: 0;
  }
}
</style>
