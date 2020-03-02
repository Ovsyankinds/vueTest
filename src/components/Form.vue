<template lang="pug">
  div
    h2 Форма с валидацией
    div.form
      .input-container
        input#questionary-name(type="text" name="name" placeholder="Ваше имя" v-model.trim="name" data-question="q")
      .input-container
        input#questionary-email(type="email" name="email" placeholder="Электронная почта" v-model.trim="email" data-question="q")
      .input-container
        input#questionary-phone(type="tel" name="phone" placeholder="89275555555" v-model.trim="phone" data-question="q")
      .submit
        input(type="button" value="Отправить" @click='sendQuestionary()' v-bind:class="{disabled: isDisabled}")
</template>

<script>
  export default {
    name: 'Form',
    data(){
      return{
        name: '',
        email: '',
        phone: '',
        isDisabled: true,
        cntInterval: 0,
      }
    },
    methods:{
      validName(name){
        if(name) return true
        return false
      },
      validEmail(email){
        var re = /.+@.+\..+/i
        return re.test(email)
      },
      validPhone(phone){
        let re = /^\+?[78][-\(]?\d{3}\)?-?\d{3}-?\d{2}-?\d{2}$/i
        return re.test(phone)
      },
      freezButton(){
        let interval = setInterval(()=>{
          this.cntInterval++
          if(this.cntInterval == 30){
            this.cntInterval = 0
            clearInterval(interval)
          }
        }, 1000)
      },
    },
    watch:{
      userName(){
        let inputName = document.getElementById("questionary-name")
        if(this.name && !this.validName(this.name)){
          inputName.classList.add("error")
        }else{
          inputName.classList.remove("error")
        }
      },
      email(){
        let inputEmail = document.getElementById("questionary-email")
        if(this.email && !this.validEmail(this.email)){
          inputEmail.classList.add("error")
        }else{
          inputEmail.classList.remove("error")
        }
      },
      phone(){
        let inputPhone = document.getElementById("questionary-phone")
        if(this.phone && !this.validPhone(this.phone)){
          inputPhone.classList.add("error")
        }else{
          inputPhone.classList.remove("error")
        }
      }
    }
  }
</script>

<style scoped lang="sass">
  .form
    .input-container
      margin: 10px 0 10px 0
      input
        width: 300px
        height: 40px
        outline: none
        border: none
        border-bottom: 1px solid #cfcfcf
        padding: 15px
        &:hover
          border-color: #a98953
        &::placeholder
          font-size: 14px
      .error
        border-bottom: 1px solid red
        color: red
    .submit
      input
        width: 220px
        background-color: transparent
        font-family: 'Nimbus Roman'
        font-weight: 400
        font-style: italic
        font-size: 20px
        color: #7a7a7a
        border-radius: 0
        border: 1px solid #cfcfcf
        text-transform: capitalize
        min-width: 220px
        padding: 16px
        cursor: pointer
        margin-top: 25px
        &.disabled
          pointer-events: none
        &:hover
          border-color: #a98953
          color: #a98953
</style>