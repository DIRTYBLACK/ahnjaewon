<template>
   <div>
      <section class="hero is-danger">
         <div class="hero-body">
            <p class="title"><i class="fas fa-futbol"></i>맨유의 레전드 선수들</p>
            <p class="subtile">
               맨체스터 유나이트를 빛낸 역대 최고의 선수들 입니다.
            </p>
         </div>
      </section>
      <hr />
      <section class="columns"></section>
      <div class="column">
         <table class="table">
            <thead>
               <th>번호</th>
               <th>이름</th>
               <th>포지션</th>
            </thead>
            <tbody>
               <template v-for="pos in tablelegendsKeys.length">
                  <tr :key="pos">
                     <td>{{ pos }}</td>
                     <td>{{ tablelegendsKeys[pos - 1] }}</td>
                     <td>
                        <span
                           class="tag is-black"
                           v-if="
                              ((ar = tablelegends[tablelegendsKeys[pos - 1]]),
                              ar.length == 0)
                           "
                           >없음</span
                        >
                        <span v-else
                           ><template v-for="subbreed in ar"
                              ><span class="tag is-success" :key="subbreed">{{
                                 subbreed
                              }}</span
                              >&nbsp;</template
                           >
                        </span>
                     </td>
                  </tr>
               </template>
            </tbody>
         </table>
         <div class="content">
            <p class="tag is-danger">출처</p>
            <a href="https://www.manutd.com/ko/players-and-staff/legends">맨체스터 유나이티드 공식 홈페이지</a><br />
            <a
               class="button is-primary is-small"
               href="https://raw.githubusercontent.com/DIRTYBLACK/ahnjaewon/master/static/legendInfo.json"
               >all list</a
            >
         </div>
      </div>
      <div class="column"></div>
   </div>
</template>
<script>
   import axios from 'axios';
   export default {
      async asyncData() {
         const legends = await axios.get('https://raw.githubusercontent.com/DIRTYBLACK/ahnjaewon/master/static/legendInfo.json');
         //alert(Object.keys(legends));
         return {
            tablelegends: legends.data.message,
            tablelegendsKeys: Object.keys(legends.data.message),
         };
      },
   };
</script>