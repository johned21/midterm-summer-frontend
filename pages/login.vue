<template>  
  <div class="bg" :style="{backgroundImage: `url(${image})`}">
    <NavBar/>

    <div class="container"><br>
      <div class="row">
          <div class="col-md-4 offset-4 mt-3">
              <h1 style="color: yellow;">Login Form</h1>
              <br>
              <div class="card">
                <b-card style="color:white;" header="Please fill up all the fields!">
                    <form action="#" @submit.prevent="onLogin">
                        <div class="form-group" style="color:white;">
                            <label for="email">Email</label>
                            <input style="background-color: #0008; color:white;" type="email" v-model="creds.email" id="email" class="form-control">
                        </div>

                        <div class="form-group" style="color:white;">
                            <label for="password">Password</label>
                            <input style="background-color: #0008; color:white;" type="password" v-model="creds.password" id="password" class="form-control">
                        </div>
<br>
                        <div class="form-group">
                            <button class="btn btn-success form-control">Login</button>
                        </div>

                    </form>
                </b-card>
              </div>
              
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import bg from "assets/bg2.jpg";

export default {
    data(){
        return{
            image: bg,
            creds:{

            }
        }
    },
    methods:{
        async onLogin(){
            try{
                await this.$auth.loginWith('local', {
                    data:this.creds
                }).then((res)=>{

                }).catch((res)=>{
                    alert('Invalid credentials')
                })
            }catch(e){
                return;
            }
        }
    }
}
</script>


<style scoped>
h1{
    text-align: center;
}
.bg{
    height: 49rem;
    background-size:  cover;
    background-repeat:  no-repeat;
    background-attachment: fixed;
}
.card{
    background-color: #0008;
}
</style>