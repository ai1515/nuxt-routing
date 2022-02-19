<template>
  <section class="container">
    <div>
      <img src="~/assets/cat.jpg" />
      <!-- 受け取ったJSONを画面に表示 -->
      <!-- {{ users[0].id }}, {{ users[0].name }} -->

      <!-- 複数のユーザーデータの表示 -->
      <ul>
        <li v-for="user in users" :key="user.id">
          {{ user.id }},{{ user.name }},{{ user.company.name }}
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
const axios = require("axios");
let url = "https://jsonplaceholder.typicode.com/users";
export default {
  // asyncData：ページコンポーネントをローディング前に非同期処理を行えるようにするメソッド
  asyncData({ params, error }) {
    // axios.get(url)：APIからのデータ取得をリクエストしてレスポンスを受け取った段階でthenメソッドが呼ばれる
    // res:サーバーからのレスポンスデータが入っている、res.data：JSONオブジェクトが入っている。
    // このデータにusersという名前をつけて、表示させる
    return axios
      .get(url)
      .then((res) => {
        return { users: res.data };
      })
      .catch((e) => {
        // console.log(e.response.status);
        // エラーメッセージを表示させるメソッド、ステータスコードと表示するメッセージを指定
        // error({ users: e.response.status, message: e.message });
        error({ users: e.response.status, message: "Error!!!!!" });
      });
  },
};
</script>
