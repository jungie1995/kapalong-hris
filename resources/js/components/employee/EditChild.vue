<template>
  <div>
    <div class="row page-titles">
        <div class="col-md-5 align-self-center">
            <h4 class="text-themecolor">Edit Child</h4>
        </div>
        <div class="col-md-7 align-self-center text-right">
            <div class="d-flex justify-content-end align-items-center">
                <ol class="breadcrumb">
                    <li class="breadcrumb-item"><router-link :to="{ name: 'dashboard' }"><span class="hide-menu">Dashboard</span></router-link></li>
                    <li class="breadcrumb-item"><router-link :to="{ name: 'employee' }"><span class="hide-menu">Eployees</span></router-link></li>
                    <li class="breadcrumb-item active">Edit Child</li>
                </ol>
            </div>
        </div>
    </div>

    <div class="row">
            <div class="col-lg-12">
                <div class="card">
                    <div class="card-header bg-primary">
                        <h4 class="m-b-0 text-white">Child Number </h4>
                    </div>
                    <div class="card-body">
                            <div class="form-body">
                                <div class="form-group row">
                                   <div class="form-group col-md-8">
                                        <label class="control-label">Fullname</label>
                                        <input v-model="childData.fullname"type="text" class="form-control">
                                    </div>
                                    <div class="form-group col-md-4">
                                        <label class="control-label">birthday</label>
                                        <input v-model="childData.child_birthday" type="date" class="form-control">
                                    </div>
                                </div>
                            </div>
                            <div class="form-actions">
                                <div class="row">
                                    <div class="col-md-12">
                                        <div class="row">
                                            <div class="offset-sm-3 col-md-9">
                                                <button type="submit" class="btn btn-success"  v-on:click="updateChild()"> <i class="fa fa-check"></i> Update</button>
                                                <button type="button" class="btn btn-inverse">
                                                    <router-link :to="{ name: 'editemployeetab2',  params: {id: childData.child_id} }"><i class="fa fa-times"></i> Cancel</router-link></button>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                    </div>
                </div>
            </div>
    </div>


  </div>
</template>

<script>
export default {
     data(){
        return {
            data: {},
            childData:{
                fullname:'',
                child_birthday:''
            },
        }
    },
    mounted(){
        this.getChild();
    },
    methods: {
        
       getChild(){
            var _this = this;
            var _id = this.$route.params.id;
            axios.get('/api/get-child/'+ _id).then(function(response){
                _this.childData = response.data[0];
                console.log(_this.childData);
            });
        },
        updateChild(){
            var _this = this;
            var _id = this.$route.params.id;

                console.log(_this.childData);
             axios.put('/api/update-child',_this.childData).then(function (response) {
                 if (response.data.ChildData.status=="Success") {
                    Vue.swal(
                        response.data.ChildData.header,
                        response.data.ChildData.name,
                        'success',
                    ).then(function(isConfirm) {
                       _this.$router.push('/edit-employee-tab2/'+_this.childData.child_id)
                    });
                }else if(response.data.ChildData.status=="Error"){
                    Vue.swal({
                    title: response.data.ChildData.header,
                    type: 'error'
                    });
                }else{
                    Vue.swal(
                        'Something went wrong!',
                        response,
                        'error'
                        )   
                }
            })
        },
    }
}
</script>

<style>

</style>