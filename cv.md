# Pavel Lushko

### Contacts
  * Email: paulworkweb@gmail.com
  * Phone: +375 33 3128092
  * GitHub: https://github.com/paulwebdeveloper

### Summary
  I have math abilities. I like to solve various logical tasks. My goal is to become a professional in the field of front-end development. I want to get more experience in creating web sites and web applications.

### Skills
  * HTML5
  * CSS3
  * JavaScript
  * jQuery
  * Git
  * BEM

#### Tools
  * SublimeText
  * Photoshop
  * Figma

### Code examples
  Task solution example on codewars: 
  [Evaluate mathematical expression](https://www.codewars.com/kata/52a78825cdfc2cfc87000005)
  ```javascript
  const calc = expr => {
    let countBrackets = 0;

    expr = removeSpaces(expr);
    expr = replaceTwoMinus(expr);
    countBrackets = countRoundBrackets(countBrackets,expr);
  
    while (countBrackets--) {
      expr = parenthesesAll(expr);
    }
  
    expr = computeExpression(expr);

    return Number(expr);
  };

  const removeSpaces = str => str.split('').filter(e => e != ' ').join('');


  const countRoundBrackets = (count,expr) => {
    for (let i = 0; i < expr.length; i++) if (expr[i] == '(') count++;
    return count;
  };


  const replaceTwoMinus = expr => expr.split('')
    .map((item, i, arr) => item === '+' && arr[i+1] === '-' ? '' : item)
    .map((item, i, arr) => item === '-' && arr[i+1] === '-' ? '+' : item)
    .map((item, i, arr) => item === '-' && arr[i-1] === '+' ? '' : item)
    .map((item, i, arr) => item === '+' && (arr[i-1] === '/' || arr[i-1] === '*') ? '' : item)
    .join('');


  const computeExpression = str => {
    let newStr = '';
    let substr = '';
    let arrSign = [];
    let j = 0;
  
    str = replaceTwoMinus(str);
  
    for (let i = 0; i < str.length; i++) {
      if ((str[i] =='+' || str[i] =='-') && str[i-1] != '*' && str[i-1] != '/'){
        arrSign[j] = str[i];
        str = str.replace(str[i],' ');
        j++;
      }
    }
  
    do {
      for (let i = 0; i < str.length; i++) {
        if (str[i] != ' ') substr += str[i];
        else break;
      }

      str = str.replace((substr + ' '),'');
      substr = calcSubStr(substr);
    
      newStr += substr;
      substr = '';
      newStr = calculateExprSubStr(newStr);
    
      if (arrSign.length > 0) newStr += arrSign.shift();  
    } while(j--);

    return newStr;
  };


  const calcSubStr = substr => {
    let countSign = 0;
  
    for (let i = 0; i < substr.length; i++) {
      if (/^[\+\-\*\/]/.test(substr[i])) countSign++;
      if (/^[\+\-\*\/]/.test(substr[i]) && substr[i+1] == '-') countSign--;
    }

    while (countSign--) {
      substr = calculateExprSubStr(substr);
    }
  
    return substr;
  };

  const calculateExprSubStr = exprsubstr => {
    let a = '', b = '', sign;
    let p  = 0

    if (exprsubstr[0] == '-') a += '-';
    for (let i = 0; i < exprsubstr.length; i++) {
      if (/^[0-9\.]/.test(exprsubstr[i]) && !sign) a += exprsubstr[i];
      if (/^[\+\-\*\/]/.test(exprsubstr[i]) && i && !sign) sign = exprsubstr[i];
     
      if (sign && exprsubstr[i+1] == '-' && !b) b += '-';
      if (/^[0-9\.]/.test(exprsubstr[i]) && sign) b += exprsubstr[i];
     
      p = i + 1;
      if (sign && /^[\*\/]/.test(exprsubstr[i+1])) break;
     }

    let value = calculate(a ,sign, b);
    let res = exprsubstr.slice(0, p);
    exprsubstr = exprsubstr.replace(res, value);

    return exprsubstr;  
  };


  const parenthesesAll = str => {
    let count = 0;
  
    for (let i = 0; i < str.length; i++) {
      if (str[i] == '(') count++;
      if (str[i] == ')') {
        str = parentheses(count,str);
        break;
      }
    }
  
    return str;
  };

  const parentheses = (count, str) => {
    let substr = '';
    let p = 0;

    for (let i = 0; i < str.length; i++) {
      if (str[i] == '(') count--;
      if (!count && str[i] != '(' && str[i] != ')')  substr += str[i];
      if (!count && str[i] == ')') {
        p = i + 1;
        break;
      }
    }

    let value = computeExpression(substr);
    let res = str.slice((p - substr.length - 2), p);
    str = str.replace(res, value);
  
    return str;
  };


  const calculate = (a,sign,b) => {
    switch (sign) {
      case '+': return Number(a) + Number(b);
      case '-': return Number(a) - Number(b);
      case '*': return Number(a) * Number(b);
      case '/': return Number(a) / Number(b);
      default: return Number(a);
    }
  };
  ```
### Experience
  Examples of my works:
  * [GitHub](https://github.com/PaulWebDeveloper?tab=repositories)
  * [Codewars](https://www.codewars.com/users/StudentTraveler)

### Education
  Belarusian National Technical University, Manager-economist, 2015

  ESL, English course, 2018

### English
  Pre-intermediate

