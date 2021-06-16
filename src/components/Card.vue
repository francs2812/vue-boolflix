<template>
    <div>
        <section> 
            <div>
                <img id="image" :src="getImage(poster)" alt="">
            </div>

            <div id="dettagli" style="padding: 20px; " >
                <h1>Titolo : <span v-if="title > ''" > {{ title }}</span> <span v-else>  {{ name }} </span> </h1>
                <h1>Titolo originale : <span v-if="originalTitle > '' " >{{ originalTitle }}</span> <span v-else> {{ originalName }} </span> </h1>
                <h1>Lingua originale : <span v-if="originalLanguage == 'en'" ><img src="../assets/images/en.png" alt="bandiera en"></span> <span v-else><img src="../assets/images/it.png" alt="bandiera it"></span></h1>
                <h1>Voto : <span v-for="(star,index) in stars" :key="index" > <i style="color: red;" class="fas fa-star">  </i> </span> </h1>
                <h1 style="max-height: 100px; overflow: hidden;" >Overview : <span> {{ descrition }} </span></h1>
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
        "originalName": String,
        "name": String,
        "descrition": String,
    },
    data: function() {
    return {
            starVote :"",
        }
    },
    methods: {
        getImage: function(element) {
               let scr = "https://image.tmdb.org/t/p/w342/"+ element;
               //console.log(scr);
               console.log(this.title);
                return scr
            },
    },
    computed : {
        stars: function() {
            const voto = Math.floor(this.voteAverage);
            //console.log(voto);
            return voto
        },
    },

}
</script>

<style lang="scss" scoped>
    section {
        width: calc(100% / 5);
        height: 350px;
        margin : 20px;
        text-align: center;
        float: left;
        border: 1px solid white;
        color: red;
        position: relative;
        box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.5);

        h1 {
            padding: 2px;
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
    div>#image {
        position: absolute;
        z-index: 5;
        left: 0;
        top: 0;
    }
    section:hover  #image {
           opacity: 20%;
           z-index: 1
           img {
               opacity: 10%;
           }
        }

    #dettagli {
        position: absolute;
        z-index: 4;
        left: 0;
        top: 0;   
    }
    section:hover #dettagli {
        opacity: 100%;
        z-index: 5
    }

</style>>