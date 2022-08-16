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
