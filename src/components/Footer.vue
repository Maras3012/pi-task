<template>
    <footer class="fixed bottom-0 left-0 w-full text-center bg-black text-white p-4">
        <div class="text-3xl md:text-2xl">
            <!-- <ul class="list-group">
                <li class="list-group-item text-base" v-show="date">{{ date }}</li>
                <li class="list-group-item text-base" v-show="time">{{ time }}</li>
            </ul> -->
            <i class="fa fa-laptop-code text-xl" /> By Maras
        </div> 
    </footer>
</template>

<script>
export default {
    name: 'Footer',
    // data: () => ({
    //       date: '',
    //       time: '',
    //     }),
    //     methods: {
    //       printDate: function () {
    //         return new Date().toLocaleDateString();
    //       },
    //       printTime: function () {
    //         return new Date().toLocaleTimeString();
    //       }
    //     },
    //     mounted: function () {
    //       this.date = this.printDate();
    //       this.time = this.printTime();
    //     },
}
</script>