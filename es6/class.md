### class类继承

- class声明类
- constructor定义构造函数初始化
- extends继承父类
- super调用父级构造器
- static定义静态方法和属性
- 父类方法可以重写



1. ```vue
   //介绍和初体验
   
   <script>
    // es5
     //手机
     function Phone(brand, price) {
       this.brand = brand;
       this.price = price;
     }
     
     //添加方法
     Phone.prototype.call = function(){
       console.log('我可以带电话')
     }
     
     //实例化对象
     let Huawei = new Phone('华为'，5999);
     Huawei.call()
     console.log(Huawei)
     </script>
     
     <script>
     //es6  class
     class Phone{
       //构造函数，名字不能变，这个函数会自动执行的(当 new Phone的时候就会执行)
       constructor(brand, price){
         this.brand = brand;
         this.price = price;
       }
       //方法必须使用该语法，不能使用es5的对象完整形式
       call(){
         console.log('我可以打电话')
       }
     }
     let onePlus = new Phone('1+',1999);
     console.log(onePlus)
   </script>
   ```

2. ```vue
   //class静态成员
   //es5
   <script>
   	function Phone(){
       
     }
     //往函数对象Phone上添加属性和方法
     Phone.name = '手机';
     Phone.change  = function(){
       console.log('我可以改变世界')
     }
     let nokia = new Phone();
     console.log(nokia.name) //undefind
     nokia.change() //nokia.change is not a function
     </script>
   	//所以说函数对象和实例对象是不通的（属性和方法是不能共享的）；
     //但是实例对象和构造函数的原型对象(prototype)是相通的
     <script>
     function Phone(){
       
     }
     //往函数对象Phone原型对象上添加属性和方法
     Phone.prototype.name = '手机';
     Phone.prototype.change  = function(){
       console.log('我可以改变世界')
     }
     let nokia = new Phone();
     console.log(nokia.name) //手机
     nokia.change() //我可以改变世界
   </script>
   ```

3. 