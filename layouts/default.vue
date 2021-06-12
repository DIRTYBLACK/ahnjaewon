<template>
  <div>
    <nav class="breadcrumb">
      <ul>
        <li><nuxt-link to="/"><i class="fas fa-home"></i> 홈으로</nuxt-link></li>
        <li><nuxt-link to="/player"><i class="fas fa-file-signature"></i>&nbsp;선수단</nuxt-link></li>
        <li><nuxt-link to="/legends"><i class="fas fa-globe-americas"></i>&nbsp;레전드 선수들</nuxt-link></li>
      </ul>      
    </nav>
    <nuxt/>
    <footer class="footer">
      <div class="content has-text-centered">
        <i class="fas fa-copyright"></i> 2020-2021, 모든 저작권은 <strong>안재원의 맨유</strong>에 있습니다. 
      </div>
    </footer>
  </div>
</template>