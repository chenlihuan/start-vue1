初学vue的心得体会
1，es5与es6的语法区别
   变量，var let
   let / var
   let变量 const常量 标识符
   //监听按钮的点击
   var btns = document.getElementsByTagName("button");
   for(var i =0;i < btns.length;i++){
    (function(i){
      btns[i].onclick = function(){
       alert('' + i +'')
      }
    })(i)
   }
   
   let btns = document.getElementsByTagName("button");
   for(let i =0;i < btns.length;i++){   
      btns[i].onclick = function(){
       alert('' + i +'')
      }   
   }
   //es5中的var是没有块级作用域的,比如说(if/for)
   //es6中的let是有块级作用域的,比如说(if和for)  
   //es5之前因为if和for没有块级作用域的概念，所以在很多时候，我们都必须借助于function的作用域来解决应用外面变量的问题。
   //es6中，加入了let，let它是有if和for的块级作用域。
   //变量作用域:变量在什么范围内是可用.
   //没有块级作用域引起的问题：if的块级
   //没有块级作用域引起的问题：for的块级
   //为什么闭包可以解决问题：函数是一个作用域。  
    const btns = doc.getElementsByTagNam('button')
    for(let i = 0; i<btns.length;i++){
        btns[i].addEventListener('click',function(){
                alert('' + i +'')
        })
    }   
   块级作用域
   const的使用
        const关键字
        建议在ES6 中，优先使用const，只有需要改变某一个标识符的时候才使用let.
        const的注意 1
                const a = 20;
                a = 30;//错误：不可以修改。
               2
                const name;//错误:const修饰的标识符必须赋值。
            注意1：一旦给const修饰的标识符被赋值之后，不能修改
                2：在使用const定义标识符，必须进行赋值
                3：常量的含义是指向的对象不能修改，但是可以改变对象内部的属性。
                const obj ={
                  name:"why",
                  age:18,
                  height:1.88
                }
                console.log(obj)
      ES6的对象字面量的增强写法
      //const obj = new   Object()
         const obj ={}
      // 1.属性的增强写法
     const name ='ade'
     const age ='12'
     const height ='1.8'
     
     //es5的写法
     const obj ={
         name:name,
         age:age,
         height:height,
     }
     es6
     const obj ={
         name,
         age,
         height
     }
     //2 函数的增强写法
     es5 
     const obj = {
         run:function(){
         },
         test:function(){
         }
     }
     obj.run();
     es6
     const obj ={
      run(){
      
      },
      text(){
      
      }      
     }
     obj.run();                
    
    
    二：事件监听： v-on介绍
                  作用：绑定事件监听器
                  缩写：@
                  预期：Function| Inliine Statement | Object
                  参数: event
                  <template>
               <div id="app">
                     <!--<h2>{{counter}}</h2>-->
                     <!--语法糖-->
                     <!--<h2 v-bind:title=""></h2>
                     <h2 :title="">{{counter}}</h2>-->
                     <!--<button v-on:click="increment">+</button>
                     <button v-on:click="increment">-</button>-->
                     <!--<button @click="increment">+</button>
                     <button @click="decrement">-</button>-->
                     <!--1.事件调用的方法没有参数-->
                     <button @click="bt1na()">1</button> 
                     <button @click="bt12dd">2</button> 
                     <!--2.在事件定义时，写函数是省略了小括号，但是方法本身是需要一个参数的，				
                     这个时候，vue会默认将浏览器的event事件对象作为参数传入到方法-->
                     <butto  @click="btn2ddw">3</button> 
                     <!--3.方法定义时，我们需要enent对象，同时又需要其他参数-->
                     <!--在调用方法式，如何手动的获取到浏览器的event的对象：$event-->
                     <button @click="btn3ddw(abc,$event)">4</button> 
               </div>
               <!--1 v-on的修饰符-->
               <div id="app">		
                  <div @click="divclick">
                     aaaa
                     <!--.stop修饰符的使用 停止事件冒泡-->
                     <button @click.stop="btnclick">4</button>
                     <!--.prevent修饰符的使用阻止默认行为-->
                     <form action="baidu" @submit.prevent>
		    <!--.prevent修饰符的使用阻止默认行为-->
                        <input type="submit" name="" id="" value="提交"  @click.prevent="submintClick"/>
                     </form>
                  </div>
                  <!--.{keyCode | keyAlias}监听某个键盘的键帽的点击-->
                  <input type="text" @keyup.enter="keyup" />
                  <!--自定义组件-->
                  <!--<cpn @click.native = "cpnClick"></cpn>-->
                  <!--.once修饰，指触发回调一次-->
                  <input type="text" @click.once="keyup" />
               </div>
            </template>
            <script></script>
            <script>
               const  app = new Vue({
                   el:"#app",
                   data:{
                     counter:0,
                     abc:123
                   },
                   methods:{
            //		 	increment(){
            //		 		this.counter ++
            //		 	},
            //			decrement(){
            //		 		this.counter --
            //		 	}
                     btna(){
                        console.log(btna)
                     },
                     btnddw(event){
                        console.log('............',event)
                     },
                     btn3ddw(abc,event){
                        console.log('............',abc ,event)
                     },
                     submintClick(){
                        console.log(submintClick)
                     },
                     keyup(){

                     }
                   }

               })
               //如果函数需要产参数，但是没有传入，那么函数的形参为undinfind。	
            </script>      
            //备注
                  当通过methods中定义的方法，以供@click调用时，主要注意参数的问题
                     情况一:如果该方法不需要额外的参数，那么方法后的()可以不用添加。
                              但是注意:如果方法本身中有一个参数，那么会默认将原生事件even参数传递进去
                      情况二: 如果需要同时传入某个参数，同时需要event时，可以通过$event传入事件。
               
	          
      
