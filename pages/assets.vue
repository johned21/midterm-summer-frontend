<template>
    <div class="body">
        <NavBar/>
        <EditFriendModal :asset="selectedAsset"/>
        <DeleteFriendModal :asset="selectedAsset" @onDeleted="getAll"/>
        <div class="container"><br>
            <a href="/dashboard" class="btn btn-secondary btn-sm"> Back to Dashboard</a><br><br>
            <h1 style="color: yellow;">
                My Friends
                <AssetEntryModal class="float-right" @onAdd="getAll"/>
            </h1>
            

            <table class="table table-boredered tabled-striped">
                <thead>
                    <tr class="bg-info text-white">
                        <th>Account ID</th>
                        <th>Account Server</th>
                        <th>In_Game_Name</th>
                        <th>Rank</th>
                        <th>&nbsp;</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="info" v-for="asset in assets" :key="asset.id">
                        <td>{{asset.ml_id}}</td>
                        <td>{{asset.ml_server}}</td>
                        <td>{{asset.in_game_name}}</td>
                        <td>{{asset.rank}}</td>
                        <td>
                            <b-button @click="onEdit(asset)" variant="info" size="sm">
                                Edit
                            </b-button>
                            <b-button @click="onDelete(asset)" variant="danger" size="sm">
                                Delete
                            </b-button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
   data(){
       return{
           assets:[],
           selectedAsset: {}
       }
   },
   methods:{
        async getAll(){
            await this.$axios.get('/api/assets')
            .then((res)=>{
                if(res.status==200) {
                    this.assets = res.data
                    console.log(this.assets)
                }
            })
        },
        onEdit(selectedAsset) {
            this.selectedAsset = selectedAsset;
            this.$bvModal.show('editFriendModal')
        },
        onDelete(selectedAsset) {
            this.selectedAsset = selectedAsset;
            this.$bvModal.show('deleteFriendModal')
        }
   },
   created(){
       this.getAll()
   }
}
</script>
<style scoped>
.body{
    height: 48rem;
    background-image: linear-gradient(300deg, rgb(0, 59, 80), rgb(0, 0, 0));
}
.info{
    color: white;
}
</style>