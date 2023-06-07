<template>
  <div id="app">
    <nav>
      <router-link to="/">Форма</router-link> |
      <router-link to="/about">Превью</router-link>
    </nav>
    <span @click="zadacha = !zadacha" style="margin-top: 2rem; cursor: pointer;  font-family: monospace;   font-size: 15px;">
          ⓘ Задача
            <p style="padding: 0rem 5rem" v-show="zadacha">
             <b>Разработайте веб приложение с помощью фреймворка VueJS,</b>
<br>
              где пользователь может заполнить информацию о себе и своих детях.

              Должны быть поля ввода ФИО и возраста пользователя.
<br>
              Ниже должна вводится информация о детях. Изначально пользователь видит только кнопку "+",
<br>
              при нажатии на нее появляется блок в котором можно ввести информацию о ребенке:
<br>
              Имя и возраст. Таким образом пользователь может добавить вплоть до 5 детей.
<br>
              Когда пользователь добавил 5 детей — кнопка "+" исчезает и больше недоступна.
<br>
              Так же напротив каждого ребенка есть кнопка "удалить" , при нажатии на которую соответствующая запись удаляется.
<br>
             <b>Реализовать функционал нужно без серверной части. При нажатии на кнопку "Сохранить" введенные данные должны отображаться на странице "Превью".</b>
<br>
              Есть вторая страница, на которой отображаются введенные данные, без возможности редактировать.
            </p>
        </span>
    <router-view/>
  </div>
</template>
<style>
body, html{
  margin: 0;
  padding: 0;


}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  width: 100vw;
  height: 100vh;

  min-width: 355px;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: purple;
}
h3{
  font-family: monospace;
}
</style>
<script>
export default {
  name: 'AppItem',
  data() {
    return {
      zadacha: false
    }
  }
}
</script>