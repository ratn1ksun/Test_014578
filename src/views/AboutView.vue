<template>
  <div class="about">
    <PreviewItem
    :name = this.ShowData.name
    :age = this.ShowData.age
    :child = this.ShowData.child
    ></PreviewItem>
  </div>
</template>
<script>
import PreviewItem from '../components/Preview.vue';
export default {
  components: {
    PreviewItem
  },
  computed: {
    //в случае, если данных в localsotrage нет, подставляет шаблон 
    //чтобы не допустить возникновения ошибок. В протвином случае,
    //отобразит данные по ключу 'CustomerData', не предусматривает 
    //проверки на "пустоту строк" приходящих из localstorage
    ShowData(){
    
      if(localStorage.getItem('CustomerData') === null){

        const parent = {
          name: 'Тут будет Ваше имя',
          age: 'и количество',
          child: []
        }
        parent.child.push({
           data:{
             child_name: 'Имя Вашего ребенка',
             child_age: 'и его возраст'
           }
      })

        return parent  
   
      }else{
        
        return JSON.parse(localStorage.getItem('CustomerData'))

      }
    }
  }
}
</script>


//old
<!-- <template>
  <div class="about">
    <PreviewItem
    :name = this.ShowData.name
    :second_name = this.ShowData.second_name
    :third_name = this.ShowData.third_name
    :age = this.ShowData.age
    :child = this.ShowData.child
    ></PreviewItem>
  </div>
</template> -->

<!-- ShowData(){
    
  if(JSON.parse(localStorage.getItem('CustomerData'))){

    return JSON.parse(localStorage.getItem('CustomerData'))
  
  }else{
    const parent = {
    second_name: 'Ваша фамилия',
    name: 'Тут будет Ваше имя',
    third_name: 'И отчество',
    age: 'и количество',
    child: []
  }
  parent.child.push({

       data:{
         child_name: 'Имя Вашего ребенка',
         child_age: 'и его возраст'
       }
   
  })
    return parent
  }
    

} -->