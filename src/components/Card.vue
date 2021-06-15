<template>
<div onmouseover="bigImg" onmouseout="normalImg">
    <section > 
        <div style="padding: 20px;" v-if="false">
            <h1>Titolo : <span>{{ title }}</span></h1>
            <h1>Titolo originale : <span>{{ originalTitle }}</span> </h1>
            <h1>Lingua originale : <span v-if="originalLanguage == 'en'" ><img src="../assets/images/en.png" alt="bandiera en"></span> <span v-else><img src="../assets/images/it.png" alt="bandiera it"></span></h1>
            <h1>Voto : <span>{{ voteAverage }}</span> </h1>
        </div>

        <div v-else>
            <img  :src="getImage(poster)" alt="">
        </div>
    </section>
</div>
</template>

<script>
export default {
    name:"Card",
    props: {
        "title": String,
        "originalTitle":String,
        "originalLanguage":String,
        "voteAverage":String,
        "poster":String,

    },
    methods: {
        getImage: function(element) {
               let scr = "https://image.tmdb.org/t/p/w342/"+ element;
               //console.log(scr);
                return scr
            },
    },
    computed: {
        bigImg: function () {
        return false
        },
        normalImg: function () {
        return  true
            //this.displayPoster = true
        }
    },
    data: function() {
        return {
            displayPoster : false
        }
    }
}
</script>

<style lang="scss" scoped>
    section {
        width: calc(100% / 5);
        height: 300px;
        margin : 20px;
        //padding: 20px;
        text-align: center;
        float: left;
        color: rgba(255, 251, 0, 0.692);
        background-color: rgb(29, 35, 63);

        h1 {
            padding: 5px;
            font-size: 17px;
            span {
                color: white;
                img {
                    width: 45px;
                    height: 20px;
                }
            }
        }
    }
    div {
        width: 100%;
        height: 100%;
        img {
            width: 100%;
            height: 100%;

        }
    }

</style>>