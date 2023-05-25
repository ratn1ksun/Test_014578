<template>
  <div class="about">
    <PreviewItem
    :name = this.ShowData.name
    :second_name = this.ShowData.second_name
    :third_name = this.ShowData.third_name
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
    ShowData(){
    
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
        
    
    }
  }
}
</script>
