<template>
    <div class="bg" :style="{backgroundImage: `url(${image})`}">
        <NavBar/>
<br>
        <div class="container">
            <br>
            <h1 style="color: yellow;">My Account</h1>

            <a href="/assets" class="btn btn-success float-right" style="margin-top:-40px;">My Friends</a>
            <hr>


            <div class="row">
                <div class="col-md-3">
                    <img class="pp" src="img/avatar1.png" alt="">
                </div>
                <div class="col-md-6 info" style="color:white;"><br>
                    <h2><strong>{{$auth.user.in_game_name}}</strong></h2>
                    <h5>Acount ID: <strong>{{$auth.user.ml_id}}</strong> </h5>
                    <h5>Acount Server: <strong>({{$auth.user.ml_server}})</strong> </h5>
                    <h5>Gmail: <strong>{{$auth.user.email}}</strong> </h5>
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
            
        }
    },
}
</script>
<style scoped>
th{
    font-size: 18px;
}

.pp{
    height: 220px;
    width: 220px;
    margin-left: 12%;
    margin-right: 30%;
}
.row{
    margin-top: 2%;
    margin-left: 2%;
    height: 32rem;
    width: 70rem;

}
.bg{
    height: 48rem;
    background-size:  cover;
    background-repeat:  no-repeat;
    background-attachment: fixed;
}
.container{
    background-color: rgba(0, 0, 0, 0.904);
    height: 41rem;
}
.info{
    margin-top: 3%;
    margin-left: 3%;
}
h5{
    color: rgb(206, 205, 205);
}
</style>