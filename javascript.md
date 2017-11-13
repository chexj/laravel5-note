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
8. 如果switch语句中的case分支的break 语句漏掉了，后面的 case语句会一直执行直到遇到break。  
switch(val){
    case 1:
    case 2:
    case 3:
      answer = 'Low';
      break;
    case 4:
    case 5:
    case 6:
      answer = 'Mid';
      break;
    case 7:
    case 8:
    case 9:
      answer = 'High';
      break;
  }
9.  访问 JS 对象的属性 1.obj.prop 2.使用 obj['prop'] 3.使用变量访问 obj[val]
10. 更改 JS 对象的属性 obj.prop = 'a new val';
11. 增加 JS 对象的属性 obj.newProp = 'val';
12. 删除 JS 对象的属性 : delete obj.prop;
13. 检测一个 JS 对象是否存在 obj.hasOwnProperty('prop'); 存在返回 true; 否则返回 false;
14. JavaScript Object Notation --- JSON
15. Math.floor(Math.random() * (max - min +1)) + min  -- min 到 max 之间所有的整数，包括 min 和 max
