<template>
  <div class="home">
    <div class="l_body">
      <div class='container clearfix'>
        <div v-for="item in list" :key="item.Id" class='post-wrapper'>
            
              <article class="post ">
                <section class="meta">
                  <h2>
                    {{item.UserName}}
                  </h2>
                </section>
              </article>
            </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "home",
  components: {},
    data() {
        return {
            list: []
        }
    },
    created() {
        this.getData()
    },
    methods: {
        getData() {
            this.$api.get('User/Get', null, r => {
                this.list = r.body;
            })
        }
    },
    watch: {
        '$route'(to, from) {
            this.list=[]
            this.getData()
        }
    }
};
</script>