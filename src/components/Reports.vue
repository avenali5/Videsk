<template>
    <main class="whole-main-container ">
        <section class="main-container max-width">
            <div class="bread-crumbs">
                <p>Home / <span>Reports & Insights</span></p>
            </div>
            <section class="chart-and-information flex">
                <article class="chart-container shadow">
                    <h3>Why do you create a startup?</h3>
                    <span>Trends</span>
                    <Chart/>
                </article>
                <article class="employees-container">
                    <h3>Employees</h3>
                    <Table/>
                </article>
            </section>
        </section>
    </main>
</template>

<script>
import Chart from './Chart.vue'
import Table from './Table.vue'

export default {
    name:'Reports',
    data(){
        return{
        }
    },
    components:{
        Chart,
        Table
    },
    
}
</script>

<style scoped lang="scss">
    .whole-main-container{
        background:#F7FAFC;
        .main-container{
            padding:2rem;
            .bread-crumbs{
                font-size: 1.2rem;
                font-weight: 300;
                color:#718096;
                span{
                    font-weight: 500;
                    text-decoration: underline;
                    cursor:pointer;
                }
            }
            .chart-and-information{
                display:grid;
                grid-template-columns: 1fr;
                grid-template-rows: 1fr 1fr;

                .chart-container{
                    box-shadow: 0 3px 10px rgba(0,0,0,.3);
                    width:100%;
                    padding:1rem;
                    font-size: 1.2rem;
                    text-align: center;
                    background:white;
                    margin:1rem 0 2rem;
                    border-radius:.4rem;

                    h3{
                        font-weight: 500;
                        color:#4A5568;
                    }
                    span{
                        color:#A0AEC0;
                    }
                }
                .employees-container{
                    box-shadow: 0 3px 10px rgba(0,0,0,.3);
                    width:100%;
                    overflow-y: auto;
                    padding:1rem;
                    font-size: 1rem;
                    background:white;
                    border-radius:.4rem;

                    h3{
                        font-weight: 500;
                        color:#4A5568;
                        margin-bottom: 2rem;
                        font-size: 1.4rem;
                    }
                }
            }
        }
    }

    @media(min-width: 1100px){
        .whole-main-container{
            .main-container{
                padding:2rem 0;
                align-items: flex-start;

                 .bread-crumbs{
                    font-size: 1.2rem;
                    font-weight: 300;
                    color:#718096;
                    padding-left: 1rem;

                    span{
                        font-weight: 500;
                        text-decoration: underline;
                    }
                }
                .chart-and-information{
                    grid-template-columns: 30% 1fr;
                    grid-template-rows: 1fr;
                    width:100%;
                    margin-top: 2rem;
                    gap:2rem;

                    .chart-container{
                        flex:1;
                        margin:0;
                        text-align: left;
                        
                    }
                    .employees-container{
                        flex:2;
                        min-height: 33.3rem;
                    }
                }
            }
        }
    }
</style>