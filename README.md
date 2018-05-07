# vue--watch
vue的watch-监听自己的一点理解



                <div id="app">
                    <div>{{obj.name}}</div>
                    <div>{{obj.age}}</div>
                    <input type="text" v-model="oldname">
                    <input type="text" v-model="obj.name">
                </div>
                <input type="button" value="按钮" id="inbtn">
                   <script>
                       var inpt=document.getElementById("inbtn");
                        var vm=new Vue({
                            el:"#app",
                            data:{
                              obj:{
                                name:"xiaohua",
                                age:25
                              },
                              oldname:'小明'
                            },
                            watch:{
                                obj:{
                                    deep:true, //深度监听  (这里必须深度监听，不然就监听不到数据的变化)
                                    handler:function(newval,oldval){
                                        vm.obj.age=26;
                                    }
                                },
                                //键路径必须加上引号
                               'obj.name':function(val,oldval){
                                 console.log(val)
                               }
                            }
                        });
                       inpt.onclick=function(){
                           vm.obj.name="哈哈哈";
                       };
                      //主动调用$watch方法来进行数据监测
                       vm.$watch("oldname",function(newval,oldval){
                       console.log(newval)
                       })

                   </script>
