<template>

    <q-layout view="lHh Lpr lFf">

        <q-header elevated>

            <q-toolbar>

                <q-btn flat dense round icon="menu" aria-label="Menu"
                       @click="leftDrawerOpen = !leftDrawerOpen"/>

            </q-toolbar>
            <div class="q-px-lg q-pt-xl q-mb-md">
                <div class="text-h3">Todo</div>
                <div class="text-subtitle">{{todayDays }}</div>
            </div>

            <q-img alt="Header logo" src="~assets/header.jpg" class="header-image absolute-top"/>

        </q-header>

        <q-drawer v-model="leftDrawerOpen" show-if-above :width="250" :breakpoint="600">

            <q-img class="absolute-top" src="~assets/header.jpg" style="height: 185px">
                <div class="absolute-bottom bg-transparent">
                    <q-avatar size="56px" class="q-mb-sm">
                        <img src="https://lh3.googleusercontent.com/ogw/ADGmqu_qxYQ-g3nRymKRM3GE6tA5iuQ7rbjfT89V-8Xi=s32-c-mo">
                    </q-avatar>
                    <div class="text-weight-bold">Nurbek Makhmudov</div>
                    <div>@NurbekMakhmudov</div>
                </div>
            </q-img>


            <q-scroll-area style="height: calc(100% - 185px); margin-top: 185px; border-right: 1px solid #ddd">
                <q-list padding>
                    <q-item exact to="/" clickable v-ripple>

                        <q-item-section avatar>
                            <q-icon name="list"/>
                        </q-item-section>

                        <q-item-section>
                            Todo
                        </q-item-section>

                    </q-item>

                    <q-item exact to="/help" clickable v-ripple>

                        <q-item-section avatar>
                            <q-icon name="help"/>
                        </q-item-section>

                        <q-item-section>
                            Help
                        </q-item-section>

                    </q-item>


                </q-list>
            </q-scroll-area>


        </q-drawer>


        <q-page-container>



            <router-view/>
        </q-page-container>
    </q-layout>
</template>

<script>
    import {date} from 'quasar'
    import EssentialLink from 'components/EssentialLink.vue'

    const linksData = [
        {
            title: 'Docs',
            caption: 'quasar.dev',
            icon: 'school',
            link: 'https://quasar.dev'
        },
        {
            title: 'Github',
            caption: 'github.com/quasarframework',
            icon: 'code',
            link: 'https://github.com/quasarframework'
        },
        {
            title: 'Discord Chat Channel',
            caption: 'chat.quasar.dev',
            icon: 'chat',
            link: 'https://chat.quasar.dev'
        },
        {
            title: 'Forum',
            caption: 'forum.quasar.dev',
            icon: 'record_voice_over',
            link: 'https://forum.quasar.dev'
        },
        {
            title: 'Twitter',
            caption: '@quasarframework',
            icon: 'rss_feed',
            link: 'https://twitter.quasar.dev'
        },
        {
            title: 'Facebook',
            caption: '@QuasarFramework',
            icon: 'public',
            link: 'https://facebook.quasar.dev'
        },
        {
            title: 'Quasar Awesome',
            caption: 'Community Quasar projects',
            icon: 'favorite',
            link: 'https://awesome.quasar.dev'
        }
    ];

    export default {
        name: 'MainLayout',
        components: {EssentialLink},
        data() {
            return {
                leftDrawerOpen: false,
                essentialLinks: linksData
            }
        },
        computed: {
            todayDays() {
                let timeStamp = Date.now()
                return date.formatDate(timeStamp, 'dddd D MMMM')
            }
        }
    }
</script>


<style lang="scss">
    .header-image {
        height: 100%;
        z-index: -1;
        opacity: 0.2;
        filter: grayscale(100%);
    }

</style>