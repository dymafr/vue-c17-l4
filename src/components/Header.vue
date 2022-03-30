<script setup lang="ts">
import type { Page } from '@/interfaces';
defineProps<{
  page: Page;
}>();
const emit = defineEmits<{
  (e: 'navigate', page: Page): void;
}>();
</script>


<template>
    <header class="px-20 d-flex flex-row align-items-center">
        <a href="#" class="d-flex flex-row align-items-center mr-20">
            <img src="../assets/logo.svg" />
            <span class="logo">Dyma</span>
        </a>
        <div class="d-flex flex-row align-items-center flex-fill actions-container">
            <ul class="d-flex flex-row flex-fill hide-xs flex-fill">
                <li class="mr-10">
                    <a
                        :class="{ active: page === 'Boutique' }"
                        @click="emit('navigate', 'Boutique')"
                    >Boutique</a>
                </li>
                <li>
                    <a
                        :class="{ active: page === 'Admin' }"
                        @click="emit('navigate', 'Admin')"
                    >Admin</a>
                </li>
            </ul>
            <ul class="d-flex flex-row hide-xs">
                <li class="mr-10">
                    <a href="#">Inscription</a>
                </li>
                <li>
                    <a href="#">Connexion</a>
                </li>
            </ul>
            <div class="menu-xs-container">
                <Calc :open="state.open" @close="state.open = false" :transparent="true" />
                <i @click="state.open = !state.open" class="fa-solid fa-bars show-xs"></i>
                <Transition>
                    <ul @click="state.open = false" v-if="state.open" class="menu card">
                        <li>
                            <a
                                :class="{ active: page === 'Boutique' }"
                                @click="emit('navigate', 'Boutique')"
                            >Boutique</a>
                        </li>
                        <li>
                            <a
                                :class="{ active: page === 'Admin' }"
                                @click="emit('navigate', 'Admin')"
                            >Admin</a>
                        </li>
                        <li>
                            <a href="#">Inscription</a>
                        </li>
                        <li>
                            <a href="#">Connexion</a>
                        </li>
                    </ul>
                </Transition>
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped>
header {
  background-color: var(--primary-1);
  a {
    color: var(--text-primary-color);
    img {
      width: 20px;
      margin-right: 5px;
    }
    .logo {
      font-weight: 700;
      font-size: 20px;
    }
  }
  a.active {
    text-decoration: underline;
  }
}
</style>
