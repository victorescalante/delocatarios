<template>
  <div>
    <Cover :title=business.name :cover_image=business.cover.url></Cover>
    <el-row class="body-business">
      <el-col :md="16">

        <el-card class="box-card">
          <h1 class="title">{{ business.name }}</h1>
          <el-divider></el-divider>
          <h4>Descripción</h4>
          <br>
          <p v-html="business.description"></p>
          <el-divider></el-divider>
          <h4>Categorías</h4>
          <el-row class="business-categories">
            <el-button type="primary" v-for="category in business.categories">{{ category.name}}</el-button>
          </el-row>
        </el-card>

        <el-card>
          <div slot="header" class="clearfix">
            <span>Galería</span>
          </div>
          <div>
            <el-carousel indicator-position="outside" height="500px" :autoplay=false>
              <el-carousel-item v-for="item in business.images" :key="item.id">
                <div class="item-image" :style=getImage(item.url)></div>
              </el-carousel-item>
            </el-carousel>
          </div>
        </el-card>

      </el-col>
      <el-col :md="8">

        <el-card class="box-card">
          <h4>Información de contacto</h4>
          <div class="business-info">
            <p v-if="business.phone"><i class="el-icon-phone"></i> {{ business.phone }}</p>
            <p v-if="business.address"><i class="el-icon-add-location"></i> {{ business.address }}</p>
            <p v-if="business.email"><i class="el-icon-user"></i> {{ business.email }}</p>
          </div>
        </el-card>

        <el-card class="box-card">
          <h4>Horario</h4>
        </el-card>

        <el-card class="box-card">
          <h4>Localización</h4>
        </el-card>

      </el-col>
    </el-row>
  </div>
</template>

<script>
  import Cover from "../../components/general/Cover";


  export default {
    layout: 'general',
    components: {
      'Cover': Cover
    },
    data(){
      return {
        url: process.env.backend,
        business: {},
        error: null
      }
    },
    methods: {
      getImage(url_image){
        let url = process.env.backend + url_image;
        return "background-image: url("+url+")";
      }
    },
    async fetch () {
      try {
        this.business = await this.$strapi.findOne('businesses', this.$route.params.id);
        console.log(this.business);
      } catch (error) {
        this.error = error
      }
    }
  }
</script>

<style lang="scss">
  .body-business{
    background-color: #f9f9f9;
    min-height: 70vh;
    .el-col{
      padding: 15px;
    }
    .el-card{
      margin-top: 15px;
    }
    .title{
      max-width: 50%;
      color: #ba25e3;
    }
    .business-categories{
      padding: 25px 0;
    }
    .business-info{
      p{
        padding: 10px 0;
      }
    }
    h4{
      color: dodgerblue;
    }
    .item-image{
      width: 100%;
      height: 100%;
      background-position: center;
      background-size: auto;
    }
  }
</style>
