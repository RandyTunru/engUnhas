<template>
    <div>
      <header class="bg-blue-200 flex flex-col">
        <div class="text-sm self-center flex w-full max-w-[80vw] justify-between items-start gap-5 mt-5 mb-4 max-md:max-w-full max-md:flex-wrap">
          <div class="items-start flex gap-4 self-start">
            <div class="text-blue text-justify font-medium self-stretch">
              Phone: +(62) 852-9999-9958
            </div>
            <div class="text-blue text-justify font-medium self-stretch">
              Email: teknik@unhas.ac.id
            </div>
          </div>
          <div class="self-end justify-between items-start flex max-w-full gap-5 max-md:justify-center">
            <a href="#" class="text-blue text-justify text-base font-medium self-stretch">
              SITE MAP
            </a>
            <a href="#" class="text-blue text-justify text-base font-medium self-stretch w-[123px]">
              QUICK ACCESS
            </a>
            <div class="justify-center items-start self-center flex gap-4 my-auto">
              <img loading="lazy" src="~/assets/images/id.png">
              <img loading="lazy" src="~/assets/images/uk.png">
            </div>
          </div>
        </div>
      </header>
      <div class="justify-left items-start bg-blue flex pl-[10vw]">
        <img loading="lazy" src="~/assets/images/logo.png" class="object-cover object-left w-[500px] max-w-full my-8"/>
      </div>
      <div class="justify-center items-center content-center flex-wrap bg-yellow flex flex-col">
        <nav class="self-center flex w-full max-w-[80vw] items-start justify-between gap-5 my-6 max-md:max-w-full max-md:flex-wrap max-md:justify-center">
          <div class="items-start self-stretch flex flex-col justify-between gap-1 relative inline-block dropdown-area" v-for ="nav in Navbar">
            <div v-if="nav.haveSubNav">
              <span class="items-start self-stretch flex justify-between gap-1">
                <a href="#" class="text-blue text-justify text-sm font-bold self-stretch">{{ nav.nama }}</a>
                <img loading="lazy" src="~/assets/images/dropdown.png" class="aspect-square object-cover object-center w-4 overflow-hidden self-center shrink-0 my-auto"/>
              </span>
              <div class="hidden absolute z-10 top-6 max-w-[25vw] dropdown-content">
                <div class="py-2 px-5 bg-yellow overflow-hidden whitespace-nowrap" v-for="subnav in filterSubnav(nav.id)"> {{ subnav.nama }}</div>
              </div>
            </div>
            <div v-else>
              <a href="#" class="text-blue text-justify text-sm font-bold self-stretch">{{ nav.nama }}</a>
            </div>
          </div>
        </nav>
      </div>
    </div>
</template>
          
<script>
    export default {
        name: 'Berita',
        props: {
            
        },

        mounted() {
            this.fetchNavbar()
            this.fetchSubnavbar()
        },

        methods: {
            fetchNavbar() {
                const res = fetch('http://localhost:8055/items/navbar')
                .then (res => res.json())
                .then (res => {
                    console.log(res.data)
                    return this.Navbar = res.data
                })
                .catch(err => {
                    console.log(err)
                })
            },

            fetchSubnavbar() {
                const res = fetch('http://localhost:8055/items/subnavbar')
                .then (res => res.json())
                .then (res => {
                    console.log(res.data)
                    return this.Subnavbar = res.data
                })
                .catch(err => {
                    console.log(err)
                })
            },

            filterSubnav(id){
              let filteredSubnav = this.Subnavbar.filter(subnav => subnav.navheader == id) 
              return filteredSubnav
            }
        },

        data() {
            return {
                Navbar: [],
                Subnavbar: []
            }
        }
    }
</script>