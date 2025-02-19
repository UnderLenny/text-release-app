<template>
  <div id="app">
    <ReleaseForm />
  </div>
</template>

<script>
import ReleaseForm from './components/ReleaseForm.vue';

export default {
  components: {
    ReleaseForm
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');
body {
  background-image: url('https://cdn.dribbble.com/userupload/15218831/file/original-2f91edd80c3fd232d29e8697444deb8e.png?resize=1504x938');
  background-size: cover;
  background-color: #f7f7f7;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  min-height: 100vh;
  box-sizing: border-box;
}

#app {
  font-family: 'Montserrat', serif;
  display: flex;
  max-width: 100%;
  margin-top: 50px;
  padding: 30px;
  border-radius: 8px;
}
h2 {
  text-align: center;
  color: #F8F8FF;
  font-size: 28px;
  margin-bottom: 20px;
}

h3 {
  color: #F8F8FF;
  font-size: 20px;
  margin-top: 30px;
}

button {
  font-family: 'Montserrat', serif;
  font-weight: 600;
  background-color: #007bff;
  color: #F8F8FF;
  padding: 10px 15px;
  margin-bottom: 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3;
}

label {
  display: block;
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 8px;
  color: #F8F8FF;
}

input, select, textarea {
  font-family: 'Montserrat', serif;
  background-color: #355E3B;
  color: #F8F8FF;
  width: 100%;
  padding: 10px;
  margin: 10px 0 20px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  box-sizing: border-box;
  transition: border-color 0.3s ease;
}

input::placeholder {
  color: #adadb3;
  font-weight: 600;
}

select {
  padding-left: 40px;
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"><path fill="none" stroke="white" stroke-width="2" d="M5,6 L15,6 M5,10 L15,10 M5,14 L15,14"/></svg>');
  background-repeat: no-repeat;
  background-position: 10px center;
  background-size: 20px 20px;
}

select, input {
  margin-right: 8px;
}
</style>
