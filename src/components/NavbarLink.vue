<template>
    <a
     class="nav-link" 
     :class="activeClasses"
     :href="page.link.url" 
     :title="'This links goes to the ${page.link.text} page'" 
     
                   >{{page.link.text}} </a>
</template>
<script>
export default{
    props:['page','isActive'],
    computed:{
        activeClasses(){
            return{
                active:this.isActive,
                emphasize:this.isActive
                
            }
        }
    }

}
</script>
<style scoped>
.emphasize{
    text-decoration: underline !important
}
</style>