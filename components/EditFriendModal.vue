<template>
    <div>

        <b-modal id="editFriendModal" title="Friend Entry" ok-title="Save" @ok="onSubmit">
            <form action="#">

                <b-form-group
                    label="Account ID"
                    label-for="ml_id">
                    
                    <b-form-input id="ml_id" v-model="asset.ml_id" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="Account Server"
                    label-for="ml_server">
                    
                    <b-form-input id="ml_server" v-model="asset.ml_server" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="In Game Name"
                    label-for="in_game_name">
                    
                    <b-form-input id="in_game_name" v-model="asset.in_game_name" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="Rank"
                    label-for="rank">
                    
                    <b-form-select v-model="asset.rank" :options="ranks"></b-form-select>
                    
                </b-form-group>

            </form>
        </b-modal>
    </div>
</template>

<script>
export default {
    props: {
        asset: {}
    },
    data(){
        return{
            asset:{},
            ranks:[
                {value: 'Warrior I', text: 'Warrior I'},
                {value: 'Warrior II', text: 'Warrior II'},
                {value: 'Warrior III', text: 'Warrior III'},

                {value: 'Elite I', text: 'Elite I'},
                {value: 'Elite II', text: 'Elite II'},
                {value: 'Elite III', text: 'Elite III'},

                {value: 'Master I', text: 'Master I'},
                {value: 'Master II', text: 'Master II'},
                {value: 'Master III', text: 'Master III'},
                {value: 'Master IV', text: 'Master IV'},

                {value: 'GrandMaster I', text: 'GrandMaster I'},
                {value: 'GrandMaster II', text: 'GrandMaster II'},
                {value: 'GrandMaster III', text: 'GrandMaster III'},
                {value: 'GrandMaster IV', text: 'GrandMaster IV'},
                {value: 'GrandMaster V', text: 'GrandMaster V'},

                {value: 'Epic I', text: 'Epic I'},
                {value: 'Epic II', text: 'Epic II'},
                {value: 'Epic III', text: 'Epic III'},
                {value: 'Epic IV', text: 'Epic IV'},
                {value: 'Epic V', text: 'Epic V'},

                {value: 'Legend I', text: 'Legend I'},
                {value: 'Legend II', text: 'Legend II'},
                {value: 'Legend III', text: 'Legend III'},
                {value: 'Legend IV', text: 'Legend IV'},
                {value: 'Legend V', text: 'Legend V'},

                {value: 'Mythic I', text: 'Mythic I'},
                {value: 'Mythic II', text: 'Mythic II'},
                {value: 'Mythic III', text: 'Mythic III'},
                {value: 'Mythic IV', text: 'Mythic IV'},
                {value: 'Mythic V', text: 'Mythic V'},

                {value: 'Mythic Glory', text: 'Mythic Glory'}

            ]
        }
    },
    methods: {
        async onSubmit(){
            this.$axios.put('/api/assets/' + this.asset.id, this.asset)
            .then((res)=>{
                if(res.status==202) {
                    alert('Update Succesful!!')
                }
            })
            .catch((err)=>{
                alert(err.message)
            })
        }
    }
}
</script>