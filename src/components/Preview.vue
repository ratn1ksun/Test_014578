<template>
    <div class="main">     
        <div class="section">
            
            <div class="adult">
              <h2>Персональные данные</h2>
              <span>{{ name }}, {{ age }} лет</span>
            </div>

            <div class="child">
              <h2>Дети</h2>

              <div v-for="(index, key) in child" :key="key">
                <div class="Child_preview">
                    
                    {{ index.data.child_name }}
                    {{ index.data.child_age }}

                </div>       
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
  
        width: auto;
        height: auto;
  
        display: flex;
        flex-direction: column;
        justify-content: space-between;
  
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
    .Child_preview{
        background-color: #9e9e9e73;
        border-radius: 5px;
        padding: 0.5rem;

        margin: 0.75rem;

        font-weight: bold;
        font-size: 24px;
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

        text-align: start;
    }
    .adult h2{
        font-weight: normal;
    }
    .adult span{
        font-weight: bold;
        font-size: 24px;
    } 
    .child h2{
        font-weight: normal;

        margin-top: 20%;

        text-align: start;
    }
  </style>
  
  //old
  <!-- props: {
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
}, -->