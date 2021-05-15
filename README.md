# JS Closures / Scoping exercises

1. What’s the result of executing this code and why.
  ```
  function test() {
     console.log(a);
     console.log(foo());
     
     var a = 1;
     function foo() {
        return 2;
     }
  }
  
  test();
  ```
_It returns "undefined" and then returns "2". console.log(a); returns "undefined" because a is defined after the console.log, console.log(foo()) returns 2 because 2 is available with closure._

2. What is result?
  ```
  var a = 1; 
  
  function someFunction(number) {
    function otherFunction(input) {
      return a;
    }
    
    a = 5;
    
    return otherFunction;
  }
  
  var firstResult = someFunction(9);
  var result = firstResult(2);
  ```
_This code returns 5 because the value of a is defined as 5 with closure._

3. What is the result of the following code? Explain your answer.
  ```
  var fullname = 'John Doe';
  var obj = {
     fullname: 'Colin Ihrig',
     prop: {
        fullname: 'Aurelio De Rosa',
        getFullname: function() {
           return this.fullname;
        }
     }
  };
  
  console.log(obj.prop.getFullname());

  var test = obj.prop.getFullname;
  
  console.log(test());
  ```
_On line 53 getFullname should be called with () because is a method. If getFullname() is defined the () on line 55 are not required._

4. What will you see in the console for the following example?
  ```
  var a = 1; 
  function b() { 
      a = 10; 
      return; 
      function a() {} 
  } 
  b(); 
  console.log(a);    
  ```
_This code displays 1 because the function b doesn't console.log anything, the function a declared in line 65 is only available inside function b. Therefore, the console.log in line 68 uses the variable a declared in line 61, which is "1"._