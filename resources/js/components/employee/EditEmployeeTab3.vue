<template>
  <div>
    <div class="row page-titles">
        <div class="col-md-5 align-self-center">
            <h4 class="text-themecolor">Edit Employee tab 3</h4>
        </div>
        <div class="col-md-7 align-self-center text-right">
            <div class="d-flex justify-content-end align-items-center">
                <ol class="breadcrumb">
                    <li class="breadcrumb-item"><router-link :to="{ name: 'dashboard' }"><span class="hide-menu">Dashboard</span></router-link></li>
                    <li class="breadcrumb-item"><router-link :to="{ name: 'employee' }"><span class="hide-menu">Eployees</span></router-link></li>
                    <li class="breadcrumb-item active">Edit Employee tab 3</li>
                </ol>
            </div>
        </div>
    </div> 

      <div class="row">
            <div class="col-lg-12">
                <div class="card">
                    <div class="card-header bg-primary">
                        <h4 class="m-b-0 text-white">Educational Background </h4>
                    </div>
                    <div class="card-body">

                            <!-- Educational Background -->
                            <div class="row">
                                <div class="col-lg-12">
                                    <div class="card">
                                        <div class="card-body">
                                            <div class="form-body">
                                                <div class="row">
                                                    <div class="card-title">
                                                        <h4 class="font-weight-bold">Elementary</h4>
                                                    </div>
                                                </div>
                                                <div class="row">
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Name of School (In Full)</label>
                                                        <input v-model="backgroundEducList.e_name" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Basic Education/Degree/Course (In Full)</label>
                                                        <h4>--</h4>
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(FROM)</label>
                                                        <input v-model="backgroundEducList.e_from" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(TO)</label>
                                                        <input v-model="backgroundEducList.e_to" type="text" class="form-control">
                                                    </div>
                                                </div>

                                                <div class="row">
                                                    <div class="card-title">
                                                        <h4 class="font-weight-bold">Secondary</h4>
                                                    </div>
                                                </div>
                                                <div class="row">
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Name of School (In Full)</label>
                                                        <input v-model="backgroundEducList.s_name" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Basic Education/Degree/Course (In Full)</label>
                                                        <h4>--</h4>
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(FROM)</label>
                                                        <input v-model="backgroundEducList.s_from" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(TO)</label>
                                                        <input v-model="backgroundEducList.s_to" type="text" class="form-control">
                                                    </div>
                                                </div>

                                                <div class="row">
                                                    <div class="card-title">
                                                        <h4 class="font-weight-bold">Vocation/Trade</h4>
                                                    </div>
                                                </div>
                                                <div class="row">
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Name of School (In Full)</label>
                                                        <input v-model="backgroundEducList.v_name" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Basic Education/Degree/Course (In Full)</label>
                                                        <input v-model="backgroundEducList.v_degree" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(FROM)</label>
                                                        <input v-model="backgroundEducList.v_from" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(TO)</label>
                                                        <input v-model="backgroundEducList.v_to" type="text" class="form-control">
                                                    </div>
                                                </div>

                                                <div class="row">
                                                    <div class="card-title">
                                                        <h4 class="font-weight-bold">College</h4>
                                                    </div>
                                                </div>
                                                <div class="row">
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Name of School (In Full)</label>
                                                        <input v-model="backgroundEducList.c_name" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Basic Education/Degree/Course (In Full)</label>
                                                        <input v-model="backgroundEducList.c_degree" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(FROM)</label>
                                                        <input v-model="backgroundEducList.c_from" type="text" class="form-control">
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(TO)</label>
                                                        <input v-model="backgroundEducList.c_to" type="text" class="form-control">
                                                    </div>
                                                </div>

                                                <div class="row">
                                                    <div class="card-title">
                                                        <h4 class="font-weight-bold">Graduate Studies</h4>
                                                    </div>
                                                </div>
                                                <div class="row">
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Name of School (In Full)</label>
                                                        <h4>--</h4>
                                                    </div>
                                                    <div class="form-group col-md-4">
                                                        <label class="control-label">Basic Education/Degree/Course (In Full)</label>
                                                        <h4>--</h4>
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(FROM)</label>
                                                        <h4>--</h4>
                                                    </div>
                                                    <div class="form-group col-md-2">
                                                        <label class="control-label">(TO)</label>
                                                        <h4>--</h4>
                                                    </div>
                                                </div>

                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- End Educational Background -->



                           <!--  <div class="form-body">
                                <div class="form-group row">
                                   <div class="form-group col-md-8">
                                        <label class="control-label">Fullname</label>
                                        <input type="text" class="form-control">
                                    </div>
                                    <div class="form-group col-md-4">
                                        <label class="control-label">birthday</label>
                                        <input  type="date" class="form-control">
                                    </div>
                                </div>
                            </div> -->
                            <div class="form-actions">
                                <div class="row">
                                    <div class="col-md-12">
                                        <div class="row">
                                            <div class="offset-sm-3 col-md-9">
                                                <button type="submit" class="btn btn-success" > <i class="fa fa-check"></i> Update</button>
                                                <button type="button" class="btn btn-inverse">
                                                    <router-link :to="{ name: 'editemployeetab2',  params: {id: 1} }"><i class="fa fa-times"></i> Cancel</router-link></button>
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
    data() {
        return{
          
            backgroundEducList:{},
        
        }
    },
    mounted() {
        this.getEducBackground();
    },
    methods: {
        getEducBackground(){
            var _this = this;
            var _id = this.$route.params.id;
            axios.get('/api/get-educ-background/'+ _id).then(function(response){
                _this.backgroundEducList = response.data[0];
                
            });
        },
    }
       
      
}
</script>

<style>
 
</style>