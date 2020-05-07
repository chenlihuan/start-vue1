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
                        
        
    JS中
