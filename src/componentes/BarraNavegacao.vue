<template>
    <nav class="navbar navbar-expand navbar-light bg-light">
  <div class="container-fluid">
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
            <RouterLink class="nav-link" to="/">Primeira Geração</RouterLink>
        </li>
        <li class="nav-item">
            <RouterLink class="nav-link" to="/geracao2">Segunda Geração</RouterLink>
        </li>
        <li class="nav-item dropdown">
            <RouterLink class="nav-link" to="/geracao3">Terceira Geração</RouterLink>
        </li>
      </ul>

    </div>
  </div>
</nav>
</template>