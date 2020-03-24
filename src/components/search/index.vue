<template lang="pug">
  .wrap-search
    input(type="text" placeholder="Поиск по системе")
    .logo
      img(src="./assets/icon.svg")
      .info
        span.name Alexander C.
        span.role Администратор

</template>

<script>
	export default{
		name: 'search',
		data(){
			return{
			}
		}
	}
</script>

<style soped>
  .wrap-search{
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin: 25px 0 25px 0;
  }
  .wrap-search input {
    width: 450px;
    height: 35px;
  }
  .wrap-search input::placeholder {
    padding-left: 25px;
  }
  .info{
    display: grid;
    grid-template-columns: 100px;
    grid-template-rows: 25px 25px;
    margin: 8px 0 0 10px;
  }
  .logo{
    display: flex;
    justify-content: flex-end;
  }
  .logo img{
    width: 50px;
    height: 50px;
  }
  .logo .name{
    width: 100px;
    margin: 0;
    text-align: center;
  }
  .logo .role{
    width: 100px;
    margin: 0;
    text-align: center;
  }
</style>