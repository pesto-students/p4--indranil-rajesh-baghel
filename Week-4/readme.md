4.2:

Var Person = function(){};
Person.prototype.initialize=function(name,age){
    this.name = name;
    this.age = age;
}

var Teacher = function(){
    this.teach = function(subject){
        console.log(this.name + "is teaching" + subject);
    } 
}

Teacher.prototype = new Person();
var newteacher = new Teacher();


4.3:

const fibonacci = {
    [symbol.iterator](){
        let n1 = 0, n2 = 1, value;
        return{
            next(){
                [value, n1, n2] = [n1, n2, n1 + n2];
                return {value};
            }
        };
    }
};

