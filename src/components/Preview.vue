<template>
    <div class="main">     
        <div class="section">
            
            <div class="adult">
              <h2>Персональные данные</h2>
              {{ name }}, {{ age }} лет
            </div>

            <div class="child">
              <h2>Дети</h2>

              <div v-for="(index, key) in child" :key="key">
                
                  {{ index.data.child_name }}
                  {{ index.data.child_age }}
              
              </div>
  
            </div>
  
  
        </div>  
  
       
    </div>
  </template>
  
  <script>
  /* eslint-disable */
  export default {
    name: 'PreviewItem',
    props: {
            name:{
                type: String,
                default: "NULL"
            },
            second_name:{
                type: String,
                default: "NULL"
            },
            third_name:{
                type: String,
                default: "NULL"
            },
            age:{
                type: String,
                default: "NULL"
            },
           child:{
                type: Array,
                default: "NULL"
            },
        },
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
    .main{
        display: flex;
        justify-content: space-around;
  
        width: 100vw;
    }
    .section{
        margin: auto;
  
        min-width: 20rem;
        min-height: 30rem;
  
        width: auto;
        height: auto;
  
        background-color: rgba(137, 111, 207, 0.205);
  
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
    }
    .adult{
        width: 100%;
        height: 100%;
  
        display: flex;
        flex-direction: column;
  
        justify-content: space-between;
        /* background-color: #a33737; */
    }
  </style>
  