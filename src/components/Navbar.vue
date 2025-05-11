<template>
 <nav class="navbar navbar-expand-lg"
            :class="[`navbar`, `navbar-expand-lg`,`bg-${theme}`, theme === 'dark' ? 'navbar-dark' : 'navbar-light']"
>
             <div class="container-fluid">
                <a class="navbar-brand" href="#">My Vue</a>
            <ul class="nav navbar-nav me-auto mb-2 mb-lg-0">
                <li v-for="(page,index) in pages" :key="index" class="nav-item">
                    <a class="nav-link" :href="page.link.url" :title="'This links goes to the ${page.link.text} page'" @click.prevent="navLinkClick(index)"
                   >{{page.link.text}}</a></li>
                
            </ul>
            <form class="d-flex">
                <button class="btn btn-primary" @click.prevent="createTheme()">Toogle Button</button>
            </form>
        </div>
        </nav>
        
        `

</template>
<script>
export default{
     props:['pages','activePage','navLinkClick'],
       
        methods:{
            createTheme(){
                  let theme='light';
                  if(this.theme=='light'){
                    theme='dark';
                  }
                  this.theme=theme;
            }
    },
    data(){
        return{
            theme:'light'
        }
    }
    
}

</script>