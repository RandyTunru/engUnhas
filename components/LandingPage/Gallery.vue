<template>
    <div>
    <div class="flex-col overflow-hidden relative flex bg-blue">
        <section class="my-12">
            <div class="flex relative items-center justify-center h-full w-full">
                <h1 class="py-2 px-5 bg-grey text-xl font-bold text-center text-blue">GALERI</h1>
            </div>
            <div class="flex flex-row gap-6 overflow-y-auto scrollbar-hide mt-6 px-4">
                <img loading="lazy" v-for="galeri in Gallery" :src="'http://localhost:8055/assets/' + galeri.gambar" class="max-w-[45vw] object-contain">
            </div>
        </section>
    </div>
    </div>
</template>

<script>
    export default {
        name: 'Berita',
        props: {
            
        },

        mounted() {
            this.fetchGallery()
        },

        methods: {
            fetchGallery() {
                const res = fetch('http://localhost:8055/items/galeri')
                .then (res => res.json())
                .then (res => {
                    console.log(res.data)
                    return this.Gallery = res.data
                })
                .catch(err => {
                    console.log(err)
                })
            },

        },

        data() {
            return {
                Gallery: [],
            }
        }
    }
</script>

<!-- http://localhost:8055/assets/6b93b9eb-faba-4c41-9ce2-973780e9619d?download=&access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImY1MGZlNGI1LTdmOTctNDk2Zi05YzY5LTQzMjg2NDQyMjA3MCIsInJvbGUiOiJkM2YyZTY2OS1lYjI4LTQ1NzItYmU4Zi1jMTVhNTJjODJjOGYiLCJhcHBfYWNjZXNzIjoxLCJhZG1pbl9hY2Nlc3MiOjEsImlhdCI6MTcwMjI5MDQ0MywiZXhwIjoxNzAyMjkxMzQzLCJpc3MiOiJkaXJlY3R1cyJ9.V6fBavkx-R0c-21RAc7DyUVEGGMSpP-U1fB0oW7n-OY -->