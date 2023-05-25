<template>   
      <div class="section">
          
          <div class="adult">
              <h2>Персональные данные</h2>
                <div style="width: 100%; display: flex; flex-direction: column;">
                  <input type="input" v-model.trim="parent.name" placeholder="Имя"/>
                  <input type="input" v-model.trim="parent.age" placeholder="Возраст"/>
                </div>
            </div>
          
          <div class="child-header">
            <h2>Дети</h2>

            <transition>
                  
                  <div v-if="is_adding_available">
                    
                    <input class="addChild-btn btn" @click="Another_child()" type="button" value="✚    Добавить ребенка">
  
                  </div>

            </transition>

          </div>

          <div v-if="IsChildExist" class="child">
              

                <div style="margin: 0.25rem;"  v-for="(index, key) in parent.child" :key="key">
 
                <div class="added-child">
               
                    <input type="input" v-model="index.data.child_name" placeholder="Имя ребенка"/>
                    <input type="input" v-model="index.data.child_age" placeholder="Возраст"/>
                    <div  style="cursor: pointer; margin: auto;" @click="parent.child.splice(key, 1)">  
                      <svg xmlns="http://www.w3.org/2000/svg" height="30" viewBox="0 -960 960 960" width="30"><path d="M261-120q-24.75 0-42.375-17.625T201-180v-570h-41v-60h188v-30h264v30h188v60h-41v570q0 24-18 42t-42 18H261Zm438-630H261v570h438v-570ZM367-266h60v-399h-60v399Zm166 0h60v-399h-60v399ZM261-750v570-570Z"/></svg>
                    </div>

                </div>
              
              </div>

          </div>

          <input class="savedata-btn btn" style="padding: 0.75rem;" @click="SaveData()" type="button" value="Сохранить данные">

          <span @click="zametka = !zametka" style="margin-top: 2rem;  font-family: monospace;   font-size: 15px;">
            ⓘ Заметка на полях
              <p v-show="zametka">
                Отдельно позволю себе заметить, что форма не обременена никаким типом валидации т.к. в задании не указана политика, согласно которой необходимо 
                обработать данные. А пытаясь ответить на вопросы политики заместо неё, велик шанс допустить логическую ошибку, к примеру: <br> <b>Может ли быть взрослый без ребенка вовсе? 
                </b><br>
                Ответ на него зависит от бизнес-процессов, сведений о которых, я увы не имею( 
              </p>
          </span>
      </div>  

     

</template>

<script>
/* eslint-disable */
export default {
  name: 'FormItem',
  data() {
    return {
      parent: {
        name: 'Имя',
        age: '20',
        child: []
      },
      //флаги
      IsChildExist: false, //регулирует отображение блока детей
      // далее флаг не влияющий на основные механики приложения
      zametka: false
    }
  },
    computed: {
      is_adding_available(){
        
        return this.parent.child.length >= 5 ? false : true;
      
      },
    },
    methods: {
      Another_child(){
        
        this.IsChildExist = true
        this.parent.count ++

        this.parent.child.push({
           
            data:{
              child_name: '',
              child_age: ''
            }
        
        })

      },
      SaveData(){
        localStorage.setItem('CustomerData', JSON.stringify(this.parent))
      }

  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .main{
      display: flex;
      justify-content: space-around;

      width: 80vw;
      margin: auto;
  }
  .section{
      margin: auto;

      overflow: hidden;

      width: 55%;
      height: auto;

      /* background-color: rgba(137, 111, 207, 0.205); */

      display: flex;
      flex-direction: column;
      justify-content: space-evenly;

      padding: 0.75rem;
  }
  .section h3{
      margin: 0.35rem;

      font-size: 14px;
  }
  .child{
      width: 100%;
      height: 100%;

      display: block;

      flex-direction: column;

      justify-content: center;

      /* background-color: #468f3d; */
  }
  .child div > input[type=input]{
    text-align: center;
    width: 100%;
    text-align: center;
    padding: 0.75rem 0;

    border: 1.8px solid;
    border-radius: 2px;

    margin-left: 5px;
  }
  .child-header {
    display: flex;
    justify-content: space-between;;
  } 
  .child-header h2{
    text-align: start;
  }
  .child-header div{
    margin: auto 0;
  }
  .added-child{
    width: 100%;
    display: flex;
    justify-content: center;
  } 
  .added-child svg{
    padding: 0;
    margin: auto;
  }
  .added-child svg:hover{
    fill: red;
  }
  .adult{
      width: 100%;
      height: 100%;

      display: flex;
      flex-direction: column;

      justify-content: space-between;
      /* background-color: #a33737; */
  }
  .adult h2{
    text-align: start;
  }
  .adult input[type=input]{
    text-align: center;

    padding: 0.75rem 0;
    margin: 0.35rem 0;

    width: 100%;
  }
  .addChild-btn{
    transition: all 0.2s linear;


    padding: 0.75rem 1.7rem;

    font-weight: bolder;

    border-radius: 6px;
    color: #01a7fd;
    border: 2px solid #01a7fd;
    background-color: #fff;
  }
  .savedata-btn{
    transition: all 0.2s linear;

    margin-top: 2rem;

    font-weight: bold;

    border-radius: 6px;
    color: #01a7fd;
    border: 2px solid #01a7fd;
    background-color: #fff;
  }
  .btn{
    cursor: pointer;
  }
  .btn:hover{
    transition: all 0.2s linear;
    background-color: #01a7fd;
    color: #fff;
    border: 2px solid #fff;
  }
  #app > div > span:hover{
    color: purple;
    cursor: pointer;

    padding: 0.05rem;
    margin: 0.25rem;

    outline: 2px solid purple;
  }
  @media (max-width: 567px){
    .child-header{
      flex-direction: column;
    }
  }
</style>

//old
<!-- <div class="adult">
  <h2>Персональные данные</h2>
    <div style="width: 100%; display: flex; flex-direction: column;">
      <input type="input" v-model.trim="parent.second_name" placeholder="Фамилия"/>
      <input type="input" v-model.trim="parent.name" placeholder="Имя"/>
      <input type="input" v-model.trim="parent.third_name" placeholder="Отчество"/>
      <input type="input" v-model.trim="parent.age" placeholder="Возраст"/>
    </div>
</div> -->
<!-- data() {
  return {
    parent: {
      second_name: 'Фамилия',
      name: 'Имя',
      third_name: 'Отчество',
      age: '20',
      child: []
    },
    //флаги
    IsChildExist: false, //регулирует отображение блока детей
    // далее флаг не влияющий на основные механики приложения
    zametka: false
  }
}, -->