<template>
 <nav class="navbar navbar-expand-lg"
            :class="[`navbar`, `navbar-expand-lg`,`bg-${theme}`, theme === 'dark' ? 'navbar-dark' : 'navbar-light']"
>
             <div class="container-fluid">
                <a class="navbar-brand" href="#">My Vue</a>
            <ul class="nav navbar-nav me-auto mb-2 mb-lg-0">
                <li v-for="(page,index) in publishedPages" :key="index" class="nav-item">
                    <navbar-link
                        :page="page"
                        :isActive="activePage === index"
                        @click.prevent="navLinkClick(index)"
>
                    </navbar-link>
                </li>
                
            </ul>
            <form class="d-flex">
                <button class="btn btn-primary" @click.prevent="createTheme()">Toggle</button>
            </form>
        </div>
        </nav>
        
        `

</template>
<script>
import NavbarLink from './NavbarLink.vue';
export default{
    computed:{
        publishedPages(){
            return this.pages.filter(page=>page.published);
        }
        
    },
    components:{
       NavbarLink 
    },
    created(){
         this.getThemeSetting();

    },
     props:['pages','activePage','navLinkClick'],

       
        methods:{
            createTheme(){
                  let theme='light';
                  if(this.theme=='light'){
                    theme='dark';
                  }
                  this.theme=theme;
                  this.storeThemeSetting();
            },
            storeThemeSetting(){
                localStorage.setItem('theme',this.theme);
            },
            getThemeSetting(){
                let theme=localStorage.getItem('theme');
                if(theme){
                    this.theme=theme;
                }
            }
    },
    data(){
        return{
            theme:'light'
        }
    }
    
}

</script>