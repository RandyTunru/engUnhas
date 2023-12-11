<template>
    <div>
    <div class="flex-col overflow-hidden relative flex bg-blue2">
        <section class="mx-16 mt-9">
            <div class="flex flex-col gap-2 relative items-center justify-center h-full w-full">
                <h1 class="text-blue text-xl font-bold text-center">   
                    TEKNIK INFO
                </h1>
                <h1 class="py-2 px-5 bg-grey text-xl font-bold text-center text-blue">
                    BERITA DAN ARTIKEL
                </h1>
            </div>
            <div class="grid grid-cols-2 gap-6 mt-6">
                <div class="flex justify-center items-center" v-for="berita in Berita">
                    <div class="flex flex-col items-stretch w-full">
                    <img loading="lazy" src="@/assets/images/berita-1.png" class="aspect-[1.7] object-fit-cover object-center max-w-[580] overflow-hidden max-w-full" />
                    <h3 class="text-black text-justify text-l font-bold py-4">
                        <a href="#">{{ berita?.judul }}Filler</a>
                    </h3>
                    <p class="line-clamp-2 text-justify text-black">
                        {{ berita?.konten }}
                    </p>
                    </div>
                </div>
            </div>
            <div class="flex justify-end inset-y-0 text-blue underline mt-4 mb-9 text-right">
                <a href="#">Lihat berita lainnya >></a>
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
            this.fetchBerita()
        },

        methods: {
            fetchBerita() {
                const res = fetch('http://localhost:8055/items/berita')
                .then (res => res.json())
                .then (res => {
                    console.log(res.data)
                    return this.Berita = res.data
                })
                .catch(err => {
                    console.log(err)
                })
            },
        },

        data() {
            return {
                Berita: []
            }
        }
    }
</script>

