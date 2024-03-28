<template>
    <div>
        <LandingPageHeadNew/>
        <div v-html="Data[0]?.kontenNewVer" class="mx-[10vw] my-[3vh]" id="modular">
        </div>
        <LandingPageFooter/>
    </div>
</template>

<script scoped>
    export default {
        name: 'Berita',
        props: {
            
        },

        mounted() {
            this.fetchData()
        },

        methods: {
            fetchData() {
                const res = fetch('http://localhost:8055/items/' + this.$route.params.pathname)
                .then (res => res.json())
                .then (res => {
                    console.log(res.data)
                    return this.Data = res.data
                })
                .catch(err => {
                    console.log(err)
                })
            },

        },

        data() {
            return {
                Data: [],
            }
        }
    }
</script>

<style scoped>   
    :deep(h3)   { 
        font-size: 1.5rem;
        font-weight: 500;
        line-height: 1.2;
        letter-spacing: -.05em;
    }

    :deep(#modular ul)   { 
        list-style-type: disc;
        margin-left: 1.5rem;
    }

    :deep(ol)   { 
        list-style-type: decimal;
        margin-left: 1.5rem;
        color:rgb(54, 99, 247);
    }

    :deep(ol ul)   {
        color:black;
    }

    :deep(p a){
        color:rgb(54, 99, 247);
    }

    :deep(table) {
        border-collapse: collapse;
        border-spacing: 0;
        width: 100%;
        display: table;
        border-color: #000;
        border-width: 1px;
        padding: 1vh 1vw;
    }

    :deep(table tr) {
        border-bottom: 1px solid #000;
        display: table-row;
        vertical-align: inherit;
        border-color: inherit;
    }

    :deep(table td) {
        border-bottom: 1px solid #000;
        display: table-cell;
        vertical-align: inherit;
        border-color: inherit;
        padding: 1vh 1vw;
    }

    :deep(.img-sarana){
        display: flex;
        flex-direction: row;
    }
</style>

<style>

*{
  font-family: 'DM Sans';
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  font-family: 'DM Sans';
}
</style>