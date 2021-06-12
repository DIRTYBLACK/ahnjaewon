<template>
  <div>
    <section class="hero is-danger">
      <div class="hero-body">
        <p class="title">
          <i class="fas fa-futbol"></i> 선수단          
        </p>
        <p class="subtile">
          맨체스터 유나이티드의 선수단 목록입니다
        </p>
      </div>
    </section>
    <hr />
    <section class="columns">
      <div class="column">
        <table class="table is-striped is-hoverable is-fullwidth">
          <thead>
            <tr>
              <th>등번호</th>
              <th>선수명</th>
            </tr>
          </thead>
          <tbody>
            <template v-for="pos in tableplayerInfo.length">
              <tr :key="pos">
                <td>{{ pos }}</td>
                <td>{{ tableplayerInfo[pos - 1] }}</td>
              </tr>
            </template>
          </tbody>
        </table>
        <div class="content">
            <span class="tag is-danger">출처</span>
            <a href="https://www.manutd.com/ko/players-and-staff/first-team">맨체스터 유나이티드 공식 홈페이지</a>
          </div>
      </div>
    </section>
  </div>
</template>
<script>
import playerInfo from "~/static/playerInfo.json";
export default {
  data() {
    return {      
      tableplayerInfo: playerInfo.names
    };
  }
};
</script>