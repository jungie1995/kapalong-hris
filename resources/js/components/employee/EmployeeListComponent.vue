<template>
	<div>
		<div class="row page-titles">
			<div class="col-md-5 align-self-center">
				<h4 class="text-themecolor">List Of All Employees</h4>
			</div>
			<div class="col-md-7 align-self-center text-right">
				<div class="d-flex justify-content-end align-items-center">
					<ol class="breadcrumb">
						<li class="breadcrumb-item"><router-link :to="{ name: 'dashboard' }"><span class="hide-menu">Dashboard</span></router-link></li>
						<li class="breadcrumb-item active">List Of All Employees</li>
					</ol>
				</div>
			</div>
		</div>

		<div class="row">
			<div class="col-12">
				<div class="card">
					<div class="card-body">
						<div class="form-group pull-right col-md-4">
							<input v-model="search.query" v-on:keyup="searchEmployee" type="text" class="form-control" placeholder="Looking for someone? Use me!">
							<small class="text-info">Found {{search.total}} matche(s).</small>
						</div>
						<div class="table-responsive">
							<table class="table color-table primary-table fixed ">
								<col width="80px" />
								<col width="250px" />
								<col width="200px" />
								<col width="180px" />
								<col width="120px" />
								<col width="200px" />
								<thead style="text-align: center;">
									<tr>
										<th >ID No.</th>
										<th>Employee Name</th>
										<th>Office</th>
										<th>Status</th>
										<th>Date Enrolled</th>
										<th>Actions</th>
									</tr>
								</thead>
								<tbody style="text-align: center;">
									<tr v-for="item in EmployeeData.data">
										<td>{{item.bio_num}}</td>
										<td>{{item.lastname}} {{item.presuf}}, {{item.firstname}} {{item.middlename}}</td>
										<td>{{item.office_name}}</td>
										<td>{{item.appointment_name}}</td>
										<td>{{item.created_at | moment("MMM, DD, YYYY")}}</td>
										<td>
											<router-link :to="{name: 'viewemployee', params: {id: item.bio_num}}" class="btn btn-info btn-xs"><span class="fa fa-eye"></span>&nbspView</router-link>
											<!-- <router-link :to="{name: 'editemployee', params: {id: item.bio_num,bio_num: item.bio_num}}" class="btn btn-warning btn-xs"><span class="fa fa-edit"></span>&nbspEdit</router-link> -->
											<!-- <button class="btn btn-success btn-xs" @click="report(item.bio_num)">&nbspPrint PDS</button> -->
											<!-- <a class="btn btn-success btn-xs" :href="'/api/view-pds/'+item.bio_num" target="_blank">&nbspPrint PDS</a> -->
											<a class="btn btn-danger btn-xs" :href="'/delete-employee?bio_num='+item.bio_num"><span class="fa fa-trash"></span>&nbspDelete</a>
										</td>
									</tr>
								</tbody>
							</table>
							<pagination :data="EmployeeData" @pagination-change-page="employeeDataList" style="margin-top: 10px;" class="float-right"></pagination>

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
			search: {
				query:'',
				total:'0'
			},
			items: [
			{
				text: "Dashboard",
				href: "/dashboard"
			},
			{
				text: "Employee List",
				active: true
			}
			],
			
			EmployeeData: {},
		}
	},
	mounted() {
		this.employeeDataList();
	},
	methods: {
		employeeDataList(page = 1){
			var _this = this;
			axios.get('/api/employee-data-list?page='+page).then(function(response){
				_this.EmployeeData = response.data;
			});
		},
		report(bio_num){
			window.open(`${'http://localhost:8000/api/view-pds/'+bio_num}`, '_blank');
		},
		searchEmployee(page = 1){
			var _this = this;
			// console.log(_this.search);
			axios.post('/api/search-employee?page='+page,_this.search).then(function(response){
				_this.EmployeeData = response.data;
				_this.search.total = response.data['total'];
				// console.log(response.data['total']);
			});
		}
	}
}
</script>
<style>
table.fixed {table-layout:fixed;}/*Setting the table width is important!*/
table.fixed td {overflow:hidden;}/*Hide text outside the cell.*/
table.fixed td:nth-of-type(1) {width:100px;}/*Setting the width of column 1.*/
table.fixed td:nth-of-type(2) {width:200px;}/*Setting the width of column 1.*/
table.fixed td:nth-of-type(3) {width:100px;}/*Setting the width of column 1.*/
table.fixed td:nth-of-type(4) {width:100px;}/*Setting the width of column 1.*/
table.fixed td:nth-of-type(5) {width:100px;}/*Setting the width of column 1.*/
table.fixed td:nth-of-type(6) {width:100px;}/*Setting the width of column 1.*/
</style>
