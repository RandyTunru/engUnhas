<template>
  <main class="justify-center items-center bg-blue flex flex-col px-[5vw] sm:px-[10vw]">
      <header class="justify-center items-center bg-grey self-center flex w-[197px] max-w-full flex-col mt-14 px-5 py-4">
        <h1 class="text-blue text-justify font-bold self-center">AGENDA</h1>
      </header>
      <div class="flex flex-col gap-[2vh] mt-12 w-[100%]">
        <section class="justify-center items-center self-center w-[100%]" v-for="agenda in Agenda">
          <div class="flex flex-row w-[100%] justify-between">
            <div class="flex flex-col items-stretch w-[25%] sm:w-[17%]">
              <div class="justify-center items-center self-stretch bg-amber-400 flex grow flex-col px-5 py-9 rounded-lg max-md:mt-4">
                <div class="text-2xl text-black text-right font-bold leading-[100%] self-center">{{agenda?.waktu[2]}}</div>
                <div class="justify-center items-center flex max-w-full flex-col mt-2 text-sm sm:text-xl">
                  <div class="text-black text-center font-medium leading-[133.33%] self-stretch">{{agenda?.waktu[1]}}</div>
                  <div class="text-black text-right text-base font-medium leading-[125%] self-center mt-2">{{agenda?.waktu[0]}}</div>
                </div>
              </div>
            </div>
            <div class="flex flex-col items-center justify-center w-[65%] sm:w-[80%]">
              <div class="justify-center items-start bg-amber-400 flex grow flex-col w-full mx-auto px-5 py-6 rounded-lg max-md:mt-4">
                <div class="text-black text-center text-base leading-[100%] justify-center items-center border border-[color:var(--black,#000)] w-[110px] max-w-full ml-1 px-4 py-2 rounded-3xl border-solid">{{agenda?.jenis}}</div>
                <h2 class="text-black text-xl font-bold leading-9 mt-5 sm:text-3xl max-md:max-w-full">{{agenda?.judul}}</h2>
                <p class="text-black text-base leading-4 ml-1 mt-6">{{agenda?.lokasi}}</p>
              </div>
            </div>
          </div>
        </section>
        <!-- <section class="justify-center items-center self-center w-[100%]">
          <div class="flex flex-row w-[100%] justify-between">
            <div class="flex flex-col items-stretch w-[25%] sm:w-[17%]">
              <div class="justify-center items-center self-stretch bg-amber-400 flex grow flex-col px-5 py-9 rounded-lg max-md:mt-4">
                <div class="text-2xl text-black text-right font-bold leading-[100%] self-center">23</div>
                <div class="justify-center items-center flex max-w-full flex-col mt-2 text-sm sm:text-xl">
                  <div class="text-black text-center font-medium leading-[133.33%] self-stretch">Oktober</div>
                  <div class="text-black text-right text-base font-medium leading-[125%] self-center mt-2">2023</div>
                </div>
              </div>
            </div>
            <div class="flex flex-col items-center justify-center w-[65%] sm:w-[80%]">
              <div class="justify-center items-start bg-amber-400 flex grow flex-col w-full mx-auto px-5 py-6 rounded-lg max-md:mt-4">
                <div class="text-black text-center text-base leading-[100%] justify-center items-center border border-[color:var(--black,#000)] w-[110px] max-w-full ml-1 px-4 py-2 rounded-3xl border-solid">Konferensi</div>
                <h2 class="text-black text-xl font-bold leading-9 mt-5 sm:text-3xl max-md:max-w-full">THE 2nd INTERNATIONAL CONFERENCE ON MARINE RESEARCH AND TECHNOLOGY</h2>
                <p class="text-black text-base leading-4 ml-1 mt-6">Labuan Bajo</p>
              </div>
            </div>
          </div>
        </section>
        <section class="justify-center items-center self-center w-[100%]">
          <div class="flex flex-row w-[100%] justify-between">
            <div class="flex flex-col items-stretch w-[25%] sm:w-[17%]">
              <div class="justify-center items-center self-stretch bg-amber-400 flex grow flex-col px-5 py-9 rounded-lg max-md:mt-4">
                <div class="text-2xl text-black text-right font-bold leading-[100%] self-center">23</div>
                <div class="justify-center items-center flex max-w-full flex-col mt-2 text-sm sm:text-xl">
                  <div class="text-black text-center font-medium leading-[133.33%] self-stretch">Oktober</div>
                  <div class="text-black text-right text-base font-medium leading-[125%] self-center mt-2">2023</div>
                </div>
              </div>
            </div>
            <div class="flex flex-col items-center justify-center w-[65%] sm:w-[80%]">
              <div class="justify-center items-start bg-amber-400 flex grow flex-col w-full mx-auto px-5 py-6 rounded-lg max-md:mt-4">
                <div class="text-black text-center text-base leading-[100%] justify-center items-center border border-[color:var(--black,#000)] w-[110px] max-w-full ml-1 px-4 py-2 rounded-3xl border-solid">Konferensi</div>
                <h2 class="text-black text-xl font-bold leading-9 mt-5 sm:text-3xl max-md:max-w-full">THE 2nd INTERNATIONAL CONFERENCE ON MARINE RESEARCH AND TECHNOLOGY</h2>
                <p class="text-black text-base leading-4 ml-1 mt-6">Labuan Bajo</p>
              </div>
            </div>
          </div>
        </section> -->
      </div>
      <div class="text-white text-right font-medium underline self-end mt-12 mb-20 max-md:max-w-full">
        <a href="#" class="text-white">Lihat agenda lainnya &gt;&gt;</a>
      </div>
    </main>
</template>

<script>
    export default {
        name: 'Berita',
        props: {
            
        },

        mounted() {
            this.fetchAgenda()
        },

        methods: {
            fetchAgenda() {
                const res = fetch('http://localhost:8055/items/agenda')
                .then (res => res.json())
                .then (res => {
                    console.log(res.data)
                    for (let i = 0; i < res.data.length; i++) {
                        res.data[i].waktu = res.data[i].waktu.split('-')
                        switch (res.data[i].waktu[1]) {
                            case '01':
                                res.data[i].waktu[1] = 'Januari'
                                break;
                            case '02':
                                res.data[i].waktu[1] = 'Februari'
                                break;
                            case '03':
                                res.data[i].waktu[1] = 'Maret'
                                break;
                            case '04':
                                res.data[i].waktu[1] = 'April'
                                break;
                            case '05':
                                res.data[i].waktu[1] = 'Mei'
                                break;
                            case '06':
                                res.data[i].waktu[1] = 'Juni'
                                break;
                            case '07':
                                res.data[i].waktu[1] = 'Juli'
                                break;
                            case '08':
                                res.data[i].waktu[1] = 'Agustus'
                                break;
                            case '09':
                                res.data[i].waktu[1] = 'September'
                                break;
                            case '10':
                                res.data[i].waktu[1] = 'Oktober'
                                break;
                            case '11':
                                res.data[i].waktu[1] = 'November'
                                break;
                            case '12':
                                res.data[i].waktu[1] = 'Desember'
                                break;
                            default:
                                break;
                        }
                    }
                    return this.Agenda = res.data
                })
                .catch(err => {
                    console.log(err)
                })
            },
        },

        data() {
            return {
                Agenda: []
            }
        }
    }
</script>