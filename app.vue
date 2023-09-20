<template>
  <div class="h-full w-full">
    <NuxtPage />
  </div>
</template>

<style>
html,
body,
#__nuxt {
  height: 100%;
  background: #1E1E1E;
  font-family: '', sans-serif;
}

body {
  font-size: 1.1rem;
}
.header-text {
    font-size: 1.8rem;
    line-height: 1.1;
}

@media (min-width: 768px) {
  body {
    font-size: 1.35rem;
  }
  .header-text {
    font-size: 3rem;
    line-height: 1.1;
}


}
</style>
