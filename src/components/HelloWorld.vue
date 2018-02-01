<template>
  <div class="hello">
    {{msg}}
    <div id="jsmind_container"></div>
  </div>
</template>


<script type="text/javascript">
  import Vue from 'vue'
  import jsDrag from '../../static/js/jsmind.draggable'
  import jsMind from '../../static/js/jsmind'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      mind:{
          "meta":{
            "name":"demo",
            "author":"hizzgdev@163.com",
            "version":"0.2",
          },
          "format":"node_array",
          "data":[
            {"id":"root", "isroot":true, "topic":"jsMind"},

            {"id":"sub1", "parentid":"root", "topic":"sub1", "background-color":"#ff5082"},
            {"id":"sub11", "parentid":"sub1", "topic":"sub11"},
            {"id":"sub12", "parentid":"sub1", "topic":"sub12"},
            {"id":"sub13", "parentid":"sub1", "topic":"sub13"},

            {"id":"sub2", "parentid":"root", "topic":"sub2"},
            {"id":"sub21", "parentid":"sub2", "topic":"sub21"},
            {"id":"sub22", "parentid":"sub2", "topic":"sub22","foreground-color":"#ff3b1b"},

            {"id":"sub3", "parentid":"root", "topic":"sub3"},
          ]
      },
      options : {
        container:'jsmind_container',
        theme:'orange',
        editable:true
      },

    }
  },
  methods: {
    load_jsmind : function (){

    var jm = jsMind.show(this.options,this.mind);

      jm.add_node("sub2","sub23", "new node", {"background-color":"red"});
      jm.set_node_color('sub21', 'green', '#ccc');

  }

  },
  components:{
    jsMind
  },
  mounted() {

    Vue.nextTick(() => {
      // var jm = new jsMind(this.options);
      // jm.show(this.mind);
      this.load_jsmind();

    });

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #jsmind_container{
    width:100%;
    height:800px;
    border:solid 1px #ccc;
    /*background:#f4f4f4;*/
    background:#f4f4f4;
  }
</style>
