<template>
    <div class="table-container toDark">
        <div class="table toDark">
            <div class="headings">
                <div class="employee-heading">
                    Employee
                </div>
                <div class="last-login-heading">
                    Last login
                </div>
                <div class="department-heading">
                    Department
                </div>
                <div class="status-heading">
                    Status
                </div>
            </div>
                <div class="value-container" v-for="(user, index) in users" :key="index">
                    <hr class="separator">
                    <div class="value">
                        <div class="employee-value flex">
                            <!--I decided to use static imgs because the images that the API returns don't exist anymore.-->
                            <img src="../assets/icons/user.svg" alt="user-img">
                            <div class="info">
                                <h4>{{user.first_name}} {{user.last_name}}</h4>
                                <span>{{user.email}}</span>
                            </div>
                        </div>
                        <div class="lastLogin-value flex">
                            <h3 v-html="handleDate(user.sessions[0], user.sessions[1], user.sessions[2])"></h3>
                        </div>
                        <div class="department-value flex">
                            <h3>{{user.department}}</h3>
                        </div>
                        <div class="status-value flex" >
                            <h3 v-html="user.status === true ? 'Active' : 'Inactive'" 
                            :class="user.status === true ? 'active' : 'inactive'"></h3>
                            <img src="../assets/icons/arrow.svg" alt="">
                        </div>
                    </div>
                </div>            
        </div>
    </div>
</template>

<script>
export default {
    name:'Table',
    data(){
        return{
            users:[],
        }
    },
    methods:{
        handleDate(date1, date2, date3){
            let dates = [new Date(date1), new Date(date2), new Date(date3)]
            let maxDate = 0;
            
            for(let i = 0; i <= maxDate; i++){
                if(dates[i] > maxDate){
                    maxDate = dates[i]
                    return new Date(maxDate).toLocaleDateString(
                        'en-gb',
                        {
                            month: 'long',
                            year: 'numeric',
                            day: 'numeric',
                        }
                    );
                }
            }
        },
    },
    async mounted() {
        // Users
        const userResponse = await fetch('/api/users');
        const users = await userResponse.json();
        this.users = users.users.slice(5)

        console.log({users})
    },
}
</script>

<style scoped lang="scss">
.table-container{
    .table{
        border:1px solid #C2C9D1;
        border-radius: .6rem;
        width:100%;
        font-size:.7rem;

        .headings{
            display:grid;
            grid-template-columns:285px 191px 174px 174px;
            grid-template-rows: 1fr;
            font-size: 1rem;
            font-weight: 500;
            padding:1rem;
            opacity:.5
        }
        .value-container{
            .separator{
                border:1px solid #c2c9d160;
            }
            .value{
                padding:1rem ;
                display:grid;
                grid-template-columns:285px 191px 174px 174px;

                .employee-value{
                    img{
                        width:2rem;
                        margin-right: .3rem;
                    }
                    h4{
                        font-size: .8rem;
                        font-weight: 500;
                    }
                    span{
                        font-size: .7rem;
                        opacity: .5;
                    }
                }

                .lastLogin-value{
                    h3{
                        font-weight: 500;
                    }
                }

                .department-value{
                    h3{
                        font-weight: 500;
                    }
                }

                .status-value{
                    justify-content: space-between;
                    h3{
                        font-weight: 500;
                    }
                    img{
                        margin-right: 1.5rem;
                        cursor:pointer;
                    }
                }
            }
            .value:hover{
                background:rgb(243, 243, 243)
            }
        }
    }
}
</style>