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
