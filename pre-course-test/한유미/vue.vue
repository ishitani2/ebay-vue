<template>
  <div>
    <!-- 문제 1 -->
    <!-- 아래 버튼을 클릭했을 때 브라우저 기본 경고창을 띄워보세요 -->
    <button v-on:click="alert">click me</button>

    <!-- 문제 2 -->
    <!-- 뷰 데이터 속성인 login 값에 따라 아래 태그가 표시되거나 미표시되게 해보세요.  -->
    <p v-if="login === true">user has been logged in</p>

    <!-- 문제 3 -->
    <!-- '<p>hello vue</p>' 를 기본 템플릿으로 갖는 로컬 컴포넌트를 한개 등록해보세요 -->

    <!-- 문제 4 -->
    <!-- 문제 3에서 등록한 컴포넌트에 아래의 num 데이터를 전달해보세요 -->

    <!-- 문제 5 -->
    <!-- 문제 3에서 등록한 컴포넌트에서 이벤트를 발생시켜 num 데이터의 값을 변경해보세요 -->
    <local-component :number="num" v-on:send-message="getChildEvent"/>

  </div>
</template>

<script>
  var localComponent = {
    props: ['number'],
    template: '<p v-on:click="sendMessage">hello vue!! The number is {{number}}</p>',
    methods: {
      sendMessage: function(){
        this.$emit('send-message')
      }
    }
  }

  export default {
    data() {
      return {
        login: false,
        num: 10,
      }
    },

    methods: {
      alert: () => {
        alert('alert message!!!');
      },
      getChildEvent: function(){
        this.num++;
      }
    },

    components: {
      'local-component': localComponent
    }
  }
</script>

<style>

</style>

