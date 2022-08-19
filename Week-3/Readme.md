-------------------------- 1 -----------------------------------

Memoization or memoisation is an optimization technique used primarily to speed up computer program by storing the result of expensive function. Call & returing the cached result when the same output occurs again.

function memoize(fn){
    const cache = new Map();
    return function (...args){
        const key = args.tostring();
        if(cache.has(key)){
            return cache.get(key);
        }
        cache.set(key, fn(..args));
        return cache.get(key);
    };
}

----------------------------------- 2 ----------------------------

Bind:
    The bind() method creates a new function that , when called has its this keyword set to the provided value with a given sequence of arguments.
    syntax: function.bind(thisArg[,arg1[arg2[....]]])

    function sum(a,b){
        return this.a + this.b;
    }

    console.log(sum());   //!Nan Because a,b are not globally present, we get undefined + undefined = NaN

If we use bind():
   const sumb = sum.bind({a:10, b:20});     //! 30

If we create another variable that using same sum function  
   const sumc = sum.bind({a:20, b:20});    //! 30 Because of .bind(). It binds the permanantely.


call:
    The call() method calls a functyion with a given this value & arguments provideed individaully.
    syntax: function.call(thisArg, arg1, arg2...)

    function greet() {
        var reply = [
            this.animal,
            'typically sleeps b/w;,
            this.sleepDuration
        ].join(' ');
        console.log(reply);
    }

    var obj = {animal: 'cats', sleepDuration: '12 & 16 hours'};
    greet.call(obj);       //! cats typically sleeps b/w 12 & 16 hours   

    If we create another object
    var obj2 = {animal: 'dog', sleepDuration: '2 to 5 hours'}
    greet.call(obj2);     //! dog typically sleeps b/w 2 & 5 hours  
                          //! unlike .bind() that binds permanantely, according pass object we can get the output.


apply:
    apply() accepts a single array of argument.
    console.log(Math.max(20,10,3,7))    //! 20

    var number=[25,6,2,3,7]
    console.log(Math.max(numbers));    //! NaN because Math.max only accept positional argument.

    var number=[25,6,2,3,7]
    var max = console.log(Math.max.apply(null, numbers);  //! this = null
    console.log(max);        //! 7


*******
    The fundamental difference is that call() accept an argument list, while apply() accepts a single array of arguments.
    with call, know the argument at compile time. with apply, we defer that decision at run time.


-------------------------------------------- 3 ---------------------------

functioncreateIncrement() {
    let count=0;
    functionincrement() {
        count++;
        }
    let message=`Count is${count}`;
    function log() {
        console.log(message);
        }
    return[increment,log];
    }
const[increment,log] =createIncrement();
increment();                            //! 1
increment();                            //! 2
increment();                            //! 3  
log();                                  //! count is 0

createIncrement() function called, count=0, declared increment.Then we created the meesage string. The message string created only once now. This string nothing to do with count variable. log() log the message.

increment(), count is increment to 3 but not the message. 


-------------------------------------------- 4 ----------------------------------
function createStack() {
  return {                       //! const item =[] 
    items: [],
    push(item) {
      this.items.push(item);
    },
    pop() {
      return this.items.pop();
    }
  };
}
const stack = createStack();
stack.push(10);
stack.push(5);
stack.pop(); // => 5
stack.items; // => [10]
stack.items = [10, 100, 1000]; // Encapsulation broken!

function createStack() {
  // Write your code here...
}
const stack = createStack();
stack.push(10);
stack.push(5);
stack.pop(); // => 5
stack.items; // => undefined

function createStack() {
  const items = [];
  return {
    push(item) {
      items.push(item);
    },
    pop() {
      return items.pop();
    }
  };
}

We can move the item to a creatsStack() scope. item we moved to createStack() scope from this outside of createStack() scope, there is no way to access or modify items array. Now items is private variable.
