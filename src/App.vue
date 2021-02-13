<template>
  <div class="container">
    <form @submit.prevent="submitHandler" class="card">
      <h1>Анкета на Vue разработчика!</h1>
      
  <!-- <div class="form-control" :class="{invalid: error}">
          <label :for="id">Как тебя зовут?</label>
          <input
              placeholder="введите имя"
              v-model.trim="name"
              type="text"
              id="name"
          >
          <small v-if="error" >{{ error }}</small> -->

          <!-- <input
          type="text"
          id="name"
          placeholder="Введи имя"
          ref="nameInput"> -->
      <!-- </div> -->

      <app-input
        placeholder="Введи имя"
        :error="errors.name"
        label="Как тебя зовут"
        v-model="name"
      ></app-input>
      <div class="form-control">
        <label for="age">Выбери возраст</label>
        <input
        type="number"
        id="age"
        v-model.number="age"
        max="70">
      </div>

      <div class="form-control">
        <label for="city">Твой город</label>
        <select id="city" v-model="city">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="nsk">Новосибирск</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Готов к переезду в Токио?</span>
        <div class="checkbox">
          <label><input v-model="relocate" type="radio" value="yes" name="trip"/> Да</label>
        </div>

        <div class="checkbox">
          <label><input type="radio" value="no" v-model="relocate" name="trip"/> Нет</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Что знаешь во Vue?</span>
        <div class="checkbox">
          <label><input v-model="skills" name="skills" value="vuex" type="checkbox"/> Vuex</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="cli" /> Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" value="router" name="skills" /> Vue Router</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Правила нашей компании</span>
        <div class="checkbox">
          <label><input v-model="agree" type="checkbox"/> С правилами согласен</label>
        </div>
      </div>

      <button type="submit" class="btn primary">Отправить</button>
    </form>
  </div>
</template>

<script>
  import AppInput from './AppInput'
  export default {
    data(){
      return {
        name: '',
        age: 23,
        city: 'spb',
        relocate: null,
        skills: [],
        agree: false,
        errors: {
          name: null
        }
      }
    },
    components:{
      AppInput
    },
    methods:{
      formIsValid(){
        let isValid = true
        if(this.name.length === 0){
          this.errors.name = "Имя не может быть пустым"
          isValid = false
        } else {
          this.errors.name = null
        }
        return isValid
      },
      submitHandler(event){
        //event.preventDefault()
        if(this.formIsValid()){
          console.group()
          console.log('Name', this.name)
          console.log('Age', this.age)
          console.log('City', this.city)
          console.log('To Tokyo', this.relocate)
          console.log('Skills', this.skills)
          console.log('Agree', this.agree)
          // console.log('Name Ref', this.$refs.nameInput.value)
        }
        
        console.groupEnd()

      }
    }
}
</script>

<style >
  .form-control small {
    color: #e53935;
  }
  .form-control.invalid input {
    border-color: #e53935;
  }
</style>
