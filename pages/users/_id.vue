<template>
  <section class="container">
    <p>{{ message }}</p>
    <!-- URLパラメータとして渡された値を表示する書き方 -->
    <p>id:{{ this.$route.params.id }}</p>
    <router-link to="/price">Price page</router-link>
  </section>
</template>

<script>
export default {
  data: function () {
    return {
      message: "/users/_id.vueを表示中",
    };
  },
  //   URLパラメータが数字以外だとエラーにするバリデーションの書き方
  // .test→JavaScriptの正規表現チェック記述
  validate({ params }) {
    return /^\d;$/.test(params.id);
  },
};
</script>
