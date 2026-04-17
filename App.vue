<template>
  <div id="app">
    <div class="ui inverted segment navbar">
      <div class="ui center aligned container">
        <div class="ui large secondary inverted pointing menu compact">
          <router-link to="/words" exact class="item">
            <i class="comment outline icon"></i> Words
          </router-link>
          <router-link to="/words/new" class="item">
            <i class="plus circle icon"></i> New
          </router-link>
          <router-link to="/test" class="item">
            <i class="graduation cap icon"></i> Test
          </router-link>
          <router-link to="/video" class="item">
            <i class="video icon"></i> Video
          </router-link>
          
        </div>
      </div>
    </div>

    <div class="ui text container">
      <flash-message class="myFlash"></flash-message>
      <div class="ui one column grid">
        <div class="column">
          <router-view />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app'
};
</script>

<style scoped>
#app > div.navbar {
  margin-bottom: 1.5em;
}
.myFlash {
  width: 250px;
  margin: 10px;
  position: absolute;
  top: 50px; /* Sửa top để đảm bảo hiển thị đúng */
  right: 10px;
  z-index: 1000; /* Đảm bảo thông báo không bị che */
}
input {
  width: 300px;
}
div.label {
  width: 120px;
}
div.input {
  margin-bottom: 10px;
}
button.ui.button {
  margin-top: 15px;
  display: block;
}
/* Tùy chỉnh thông báo flash */
.flash-message .success {
  background-color: #4caf50;
  color: white;
  border-radius: 4px;
  padding: 10px;
}
.flash-message .error {
  background-color: #f44336;
  color: white;
  border-radius: 4px;
  padding: 10px;
}

</style>