<template>
    <header class="whole-header-container max-width">
        <div class="header-container flex">
            <div class="logo">
                LOGO
            </div>
            <nav>
                <ul class="flex">
                    <li>Menu</li>
                    <li>Menu</li>
                    <li>Menu</li>
                    <li>Menu</li>
                </ul>
            </nav>
            <div class="user" @click="showMenu">
                <img src="https://images.generated.photos/ERWujtGdPrsx5TqtmelYDCs05-YcdEG6yYS08QsRUsw/rs:fit:512:512/wm:0.95:sowe:18:18:0.33/Z3M6Ly9nZW5lcmF0/ZWQtcGhvdG9zL3Yz/XzAwMjMwNDYuanBn.jpg" alt="">
            </div>
            <div class="menu absolute">
                <ul>
                    <li class="flex info">
                        <img src="../assets/icons/user.svg" alt="user-icon">
                        <div>
                            <span>My Profile</span>
                            <p>Change settings of your account</p>
                        </div>                    
                    </li>
                    <hr>
                    <li class="flex logout">
                        <img src="../assets/icons/logout.svg" alt="log-out">
                        <span>Logout</span>
                    </li>
                </ul>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name:'Header',
    methods:{
        showMenu(){
            let menu = document.querySelector('.menu')
            menu.classList.toggle('open')
        },
    }
}
</script>

<style scoped lang="scss">
    .whole-header-container{
        background:#1E1ADD;
        color:white;
        padding:.5rem 2rem;
        margin-top: 1rem;
        border-radius: .5rem;
        z-index: 30;

        .header-container{
            justify-content: space-between;
            .logo{
                flex:1;
                font-size: 1.5rem;
                font-weight: 600;
            }
            nav{
                flex:5;

                ul{
                    flex-direction: column;
                    li{
                        margin:0 1rem;
                        font-size: 1rem;
                        cursor:pointer;
                    }
                }

            }
            .to-dark-mode{
                input{
                    display:none;
                }
                .switcher{
                    background:white;
                    height:1.5rem; width:3rem;
                    border-radius: 200px;
                    cursor:pointer;

                    .ball{
                        background:rgb(199, 199, 199);
                        height:1.7rem; width:1.7rem;
                        border-radius: 200px;
                    }
                }
            }
            .user{
                cursor:pointer;
                img{
                    width:3.5rem;
                    border-radius: 200px;
                    border:2px solid white;
                }
            }
            .menu{
                color:black;
                background:white;
                right:2rem;
                top:4.5rem;
                box-shadow: 0 4px 10px rgba(0,0,0,.3);;
                z-index: 30;
                display:none;

                ul{
                    img{
                        width:2rem;
                    }
                    li{
                        padding:1rem .5rem;
                        font-weight: 600;
                        cursor:pointer;
                        transition:.4s all;
                    }
                    li:hover{
                        background:rgb(241, 241, 241)
                    }

                    .info{
                        align-items: flex-start;                
                        span{
                            color:#4A5568;
                        }
                        p{
                            color:#A0AEC0;
                            width:60%;
                            margin-top: .4rem;
                            font-weight: 500;
                        }
                    }
                    .logout{
                        span{
                            color:#E53E3E;
                        }
                    }
                }
                img{
                    margin-right: .5rem;
                }
            }
        }
    }

    @media(min-width: 1000px){
        .whole-header-container{
            .header-container{
                nav{
                    ul{
                        flex-direction: row;
                    }
                }
            }
        }
    }
</style>