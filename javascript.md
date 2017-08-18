1. 获取字符串长度 str.length;  
2. 获取字符串的第一个字符 str[0];
3. var str = "Che"; str[0] = 'z'; console.log(str);//'Che' 值不改变
4. 
var family = ['cheche', 'yangyang'];  
var removeFromFamily = family.pop();  
console.log(removeFromFamily); // yangyang
family.push(removeFromFamily);
console.log(family); // ['cheche', 'yangyang']  
removeFromFamily = family.shift();
console.log(removeFromFamily); // 'cheche'  
family.unshift(removeFromFamily); 
console.log(family); // ['cheche', 'yangyang']  
5. 局部变量和全局变量
function myTest(){
    var str = 'cheche';
    console.log(str);
}
myTest(); // 'cheche'
console.log(str); // undefined

function anotherTest(){
    str = 'cheche';
    console.log(str);
}
anotherTest(); // 'cheche'
console.log(str); // 'cheche'
6. 同名的局部变量和全局变量同时存在时，局部变量优先于全局变量
var someVar = "cheche";
function myFun(){
    var someVar = 'yangyang';
    console.log(someVar);
}
myFun(); // 'yangyang'
7. 一个入栈出栈的小函数
function queue(arr, item){
    arr.push(item);
    return arr.shift();
}
