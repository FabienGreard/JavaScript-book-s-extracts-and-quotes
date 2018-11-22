The reason the preceding code works is that JavaScript engines move the declaration of foo to the beginning of the scope. They execute the code as if it looked like this:

function foo() {
    ...
}
foo();
var declarations are hoisted, too, but only the declarations, not assignments made with them. Therefore, using a var declaration and a function expression similarly to the previous example results in an error:

foo();  // TypeError: undefined is not a function
var foo = function () {
    ...
};
Only the variable declaration is hoisted. The engine executes the preceding code as:

var foo;
foo();  // TypeError: undefined is not a function
foo = function () {
    ...
};
