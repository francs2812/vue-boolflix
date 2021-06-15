<template>
<div>
    <section > 
        <div>
            <img id="image" :src="getImage(poster)" alt="">
        </div>

        <div id="dettagli" style="padding: 20px; " >
            <h1>Titolo : <span>{{ title }}</span></h1>
            <h1>Titolo originale : <span>{{ originalTitle }}</span> </h1>
            <h1>Lingua originale : <span v-if="originalLanguage == 'en'" ><img src="../assets/images/en.png" alt="bandiera en"></span> <span v-else><img src="../assets/images/it.png" alt="bandiera it"></span></h1>
            <h1>Voto : <span v-for="(star,index) in stars" :key="index" > <i style="color: red;" class="fas fa-star">  </i> </span> </h1>
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
        "voteAverage":Number,
        "poster":String,

    },
    data: function() {
    return {
            starVote :""
        }
    },
    methods: {
        getImage: function(element) {
               let scr = "https://image.tmdb.org/t/p/w342/"+ element;
               //console.log(scr);
                return scr
            },
    },
    computed : {
        stars: function() {
            const voto = Math.floor(this.voteAverage);
            console.log(voto);
            return voto
        }
    },

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
        color: red;
        position: relative;

        h1 {
            padding: 5px;
            font-size: 17px;
            span {
                color: black;
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
    #image {
        position: absolute;
        z-index: 5;
        left: 0;
        top: 0;
    }
    #image:hover {
           opacity: 30%;
        }

    #dettagli {
        position: absolute;
        z-index: 2;
        left: 0;
        top: 0;
        

    }

</style>>