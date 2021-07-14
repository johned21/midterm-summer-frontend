<template>
    <div>

        <b-modal id="deleteFriendModal" title="Delete Friend" ok-title="Delete" @ok="onDelete" ok-variant="danger">
            Are You Sure about deleting this friend?<br><br>
            <h2>{{asset.in_game_name}}</h2> 
            <h5>- {{asset.rank}}</h5>
        </b-modal>
    </div>
</template>

<script>
export default {
    props: {
        asset: {}
    },
    methods: {
        async onDelete(){
            this.$axios.delete('/api/assets/' + this.asset.id)
            .then((res)=>{
                if(res.status==202) {
                    alert('Friend is deleted successfully')
                    this.$emit('onDeleted')
                }
            })
        }
    }
}
</script>