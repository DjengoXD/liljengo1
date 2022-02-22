<template>

  <div>
      
    <h1>product</h1>

    <div class="container">
        <div class="row">
            <div class="col-md-4" v-for="produk in products" :key="produk.id">
                <div class="card">
                    <div class="card-header">
                        <img :src="produk.foto" alt="">
                    </div>
                    <div class="card-body">
                        <h4>{{produk.nama}}</h4>
                        <h4>{{produk.harga}}</h4>
                        <a :href="produk.link_eksternal" class="btn btn-danger btn-block" >whatsapp</a>
                    </div>
                </div>
            </div>
        </div>
    </div>

    
  </div>
  
</template>

<script>
export default {
    data() {
        return {
            products: ''
        }
    },
    mounted() {
        this.getProduk()
    },

    methods: {
        async getProduk() {
            let {data, error} = await this.$supabase
                .from('tb_produk')
                .select()
                .limit(3)
                .order('id', { ascending: false })
            
            if(data) this.products = data
            if(error) console.log(error)
        }
    }
}
</script>


<style lang="scss" scoped>

</style>