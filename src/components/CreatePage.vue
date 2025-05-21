<template>
    <form action="" class="container mb-3">
        <div class="row">
            <div class="col-md-8">
                <div class="mb-3">
                    <label for="" class="form-label">
                        PageTitle
                    </label>
                    <input type="text" class="form-control" v-model="pageTitle" />
                </div>
                <div class="mb-3">
                    <label for="" class="form-label">
                        Content
                    </label>
                    <textarea type="text" rows="5" class="form-control" v-model="content"></textarea>
            </div>
             <button class="btn btn-primary" @click.prevent="submitForm" :disabled="isFormInvalid">
                    Create Page
                    </button>
            </div>
            <div class="col">
                <div class="mb-3">
                    <label for="" class="form-label">
                        Link Text
                    </label>
                    <input type="text" class="form-control" v-model="linkText">
                </div>
                <div class="mb-3">
                    <label for="" class="form-label">
                        Link URL
                    </label>
                    <input type="text" class="form-control" v-model="linkUrl">
                </div>
                <div class="row mb-3">
                <div class="form-check">
                    <input type="checkbox" class="form-check-input" v-model="published">
                    <label class="form-check-label" for="gridCheck1">Published</label>
                    </div>
                    </div>
             
               
            </div>
            
        </div>
    </form>
</template>
<script>
export default{
    computed:{
        isFormInvalid(){
            return !this.pageTitle || !this.content || !this.linkText || !this.linkUrl;
        }
    },
    props:['pageCreated'],
    data(){
        return{
            pageTitle:'',
            content:'',
            linkText:'',
            linkUrl:'',
            published:true
           
          
        }
    },
    methods:{
        submitForm(){
            if(!this.pageTitle|| !this.content|| !this.linkText || !this.linkUrl){
                alert('Please fill all fields');
                return;
            }
            this.$emit('page-created',{
                 pageTitle: this.pageTitle,
                content:this.content,
                link:{
                    text:this.linkText,
                    url:this.linkUrl

                },
                published:this.published
            })
        
            this.pageTitle='';
            this.content='';
            this.linkText='';
            this.linkUrl='';
            this.published=true;
        }
       
    },
    watch:{
        pageTitle(newTitle,oldTitle){
            if(this.linkText==oldTitle){
                this.linkText=newTitle;
            }
        }
    }
}
</script>