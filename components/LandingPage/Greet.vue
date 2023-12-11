<template>
    <div>
    <div class="flex-col overflow-hidden relative flex min-h-[579px] px-16">
    <img loading="lazy" src="@/assets/images/bg-sambutan.png" class="absolute z-[-1] h-full w-full object-cover object-center inset-0" />    
        <section class="mt-9 max-md:max-w-full">
            <div class="gap-5 flex flex-col md:flex-row items-stretch">
                <div class="w-full md:w-[38%] mr-5 md:mr-0">
                    <img loading="lazy" src="http://localhost:8055/assets/7bc35b82-082b-4a46-b154-96e31e1dcc2c?&access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImY1MGZlNGI1LTdmOTctNDk2Zi05YzY5LTQzMjg2NDQyMjA3MCIsInJvbGUiOiJkM2YyZTY2OS1lYjI4LTQ1NzItYmU4Zi1jMTVhNTJjODJjOGYiLCJhcHBfYWNjZXNzIjoxLCJhZG1pbl9hY2Nlc3MiOjEsImlhdCI6MTcwMjI4OTMyMCwiZXhwIjoxNzAyMjkwMjIwLCJpc3MiOiJkaXJlY3R1cyJ9.lTliQP374kIyv2fAKv9gmweZqdxSubbDHzxEhd1LbXo" class="bottom-0">
                </div>
                <div class="w-full md:w-[62%]">
                    <div class="relative flex flex-col my-auto">
                        <div class="text-white text-justify text-xl font-semibold w-[787px] max-w-full">
                            {{ Greet[0]?.konten }}
                        </div>
                        <div class="w-[618px] max-w-full mt-10">
                            <div class="gap-5 flex max-md:flex-col max-md:items-stretch max-md:gap-0">
                                <div class="flex flex-col items-stretch w-[1%] max-md:w-full max-md:ml-0">
                                    <div class="bg-white flex w-2 h-28 flex-col mx-auto max-md:mt-3"></div>
                                </div>
                                <div class="flex flex-col items-stretch w-[99%] max-md:w-full max-md:ml-0">
                                    <div class="flex grow flex-col mt-1 max-md:max-w-full max-md:mt-4">
                                        <div class="text-white text-justify text-3xl font-bold leading-[121.88%] w-[768px] max-w-full">
                                            {{Greet[0]?.subjudul}}
                                        </div>
                                        <div class="text-white text-justify text-xl font-bold leading-[195%] mt-1 max-md:max-w-full">
                                            {{Greet[0]?.jabatan}}
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
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
            this.fetchGreet()
        },

        methods: {
            fetchGreet() {
                const res = fetch('http://localhost:8055/items/sambutan')
                .then (res => res.json())
                .then (res => {
                    console.log(res.data)
                    return this.Greet = res.data
                })
                .catch(err => {
                    console.log(err)
                })
            },

        },

        data() {
            return {
                Greet: [],
            }
        }
    }
</script>