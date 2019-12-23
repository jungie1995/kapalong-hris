<template>
  <div>
    <div class="row page-titles">
        <div class="col-md-5 align-self-center">
            <h4 class="text-themecolor">Edit Employee tab 2</h4>
        </div>
        <div class="col-md-7 align-self-center text-right">
            <div class="d-flex justify-content-end align-items-center">
                <ol class="breadcrumb">
                    <li class="breadcrumb-item"><router-link :to="{ name: 'dashboard' }"><span class="hide-menu">Dashboard</span></router-link></li>
                    <li class="breadcrumb-item"><router-link :to="{ name: 'employee' }"><span class="hide-menu">Eployees</span></router-link></li>
                    <li class="breadcrumb-item active">Edit Employee tab 2</li>
                </ol>
            </div>
        </div>
    </div>


      <!-- Start Page Content -->
        <!-- ============================================================== -->
        <div class="row">
            <div class="col-12">
                <div class="card">
                    <div class="card-body">
                    <h4>Spouse Information</h4>
                    <hr>
                    <div class="row">
                        <div class="form-group col-md-4">
                            <label class="control-label">Firstname</label>
                            <input v-model="data.spfirstname" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-3">
                            <label class="control-label">Middlename</label>
                            <input v-model="data.spmiddlename" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-4">
                            <label class="control-label">Lastname</label>
                            <input v-model="data.spsurname" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-1">
                            <label class="control-label">Sufix</label>
                            <input v-model="data.spsuf" type="text" class="form-control">
                        </div>
                         <div class="form-group col-md-4">
                            <label class="control-label">Occupation</label>
                            <input v-model="data.spoccupation" type="text" class="form-control">
                        </div>
                         <div class="form-group col-md-4">
                            <label class="control-label">Employer/Business Name</label>
                            <input v-model="data.spemployer" type="text" class="form-control">
                        </div>
                         <div class="form-group col-md-4">
                            <label class="control-label">Telephone No.</label>
                            <input v-model="data.sptelephone" type="text" class="form-control">
                        </div>
                         <div class="form-group col-md-12">
                            <label class="control-label">Business Address</label>
                            <input v-model="data.spbadd" type="text" class="form-control">
                        </div>
                    </div>
                        <h4>Father's Information</h4>
                        <hr>
                    <div class="row">
                        <div class="form-group col-md-3">
                            <label class="control-label">Firstname</label>
                            <input v-model="data.ffirstname" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-3">
                            <label class="control-label">Middlename</label>
                            <input v-model="data.fmiddlename" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-4">
                            <label class="control-label">Lastname</label>
                            <input v-model="data.fsurname" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-2">
                            <label class="control-label">Sufix</label>
                            <input v-model="data.fsuf" type="text" class="form-control">
                        </div>
                    </div>
                        <h4>Mother's Information</h4>
                        <hr>
                    <div class="row">
                        <div class="form-group col-md-3">
                            <label class="control-label">Firstname</label>
                            <input v-model="data.mfirstname" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-3">
                            <label class="control-label">Middlename</label>
                            <input v-model="data.mmiddlename" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-3">
                            <label class="control-label">Lastname</label>
                            <input v-model="data.msurname" type="text" class="form-control">
                        </div>
                        <div class="form-group col-md-3">
                            <label class="control-label">Maiden Name</label>
                            <input v-model="data.mmaiden" type="text" class="form-control">
                        </div>
                    </div>

                    <br>
                    <h4>Children's Information</h4>
                       

                        <div class="row" v-for="item in childrenList">
                            <div class="form-group col-md-8">
                                <label class="control-label">Fullname</label>
                                <input v-model="item.fullname" type="text" class="form-control" readonly>
                            </div>
                            <div class="form-group col-md-3">
                                <label class="control-label">Birthday</label>
                                <input v-model="item.child_birthday" type="text" class="form-control" readonly>
                            </div>
                            <div class="form-group col-md-1">
                                <router-link style="margin-top: 30px;" :to="{name: 'editchild',  params: {id: item.id,bio_num: item.family_id }}" class="btn btn-danger" ><i class="fa fa-edit"></i> Edit</router-link>
                            </div>
                        </div>
                    <hr>
                        <div class="pull-right">
                          <b-button variant="default"><router-link :to="{name: 'viewemployee', params: {id: this.$route.params.id}}">Cancel</router-link></b-button>  
                        <b-button variant="danger" v-on:click="updateData()">Update</b-button>
                        </div>

                    </div>
                </div>
            </div>
        </div>
        <!-- ============================================================== -->
        <!-- End PAge Content -->




  </div>
</template>

<script>
export default {
    data(){
        return {
            data: {},
            childrenList:{},
        }
    },
    mounted(){
        this.getFamilyBackground();
        this.getChildren();
    },
    methods: {
        getFamilyBackground(){
            var _this = this;
            var _id = this.$route.params.id
            axios.get('/api/get-family-background/' + _id).then(function(response){
                _this.data = response.data[0];
                });
        },
       getChildren(){
            var _this = this;
            var _id = this.$route.params.id;
            axios.get('/api/get-children-list/'+ _id).then(function(response){
                _this.childrenList = response.data;
                console.log(_this.childrenList);
            });
        },
        updateData(){
            var _this = this;
            var _id = this.$route.params.id
            console.log(_this.data);
            axios.put('/api/update-family-data',_this.data).then(function (response) {
                 if (response.data.FamilyData.status=="Success") {
                    Vue.swal(
                        response.data.FamilyData.header,
                        response.data.FamilyData.name,
                        'success',
                    ).then(function(isConfirm) {
                       _this.$router.push('/view-employee/'+_id)
                    });
                }else if(response.data.FamilyData.status=="Error"){
                    Vue.swal({
                        title: response.data.FamilyData.header,
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