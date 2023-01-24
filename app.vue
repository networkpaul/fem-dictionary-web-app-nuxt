<template>
  <header>
    <div class="container header">
      <div class="header-icon">
        <img src="@/assets/images/logo.svg" alt="" class="icon">
      </div>
      <div class="header-choices">
        <DropdownList />
        <ThemeToggle />
      </div>
    </div>
  </header>
  <main>
    <SearchInput />
  </main>
</template>

<script>

export default {
  name: 'App'
}
</script>
