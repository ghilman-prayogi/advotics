<template>
    <div class="column full-height" style="min-height: 100vh;" v-if="$q.screen.gt.xs">
        <div class="col">
            <q-card class="background-white" flat>
                <div class="row justify-center items-center q-mt-xl">
                    <div class="col-7">
                        <div class="text-title-login text-weight-bolder">
                            Welcome to My Terra
                        </div>
                        <div class="q-mt-xs text-subtitle-login">
                            Property Management
                        </div>
                        <img class="q-mt-md full-width" src="img/login-frame.svg" />
                    </div>
                </div>
            </q-card>
        </div>
        <div class="col-auto">
            <div class="text-footer-login text-center q-pa-md">
                © Copyright 2021 My Terra
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'BannerLogin',
  methods: {
    toKebijakanPrivasi () {
      window.open('https://daftarcpns.id/kebijakan-privasi', '_blank')
    },
    toKetentuanPengguna () {
      window.open('https://daftarcpns.id/ketentuan-penggunaan', '_blank')
    }
  }
}
</script>
