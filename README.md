# Thanks for viewing my Project ✨

![ a main page screenshot](./images/screen2.png)
<br />

## :star: Demonstration Video: ([https://katarzynadworak.github.io/modern-web-design/](https://katarzynadworak.github.io/JS-AdvancedCalculator/))
<br />
<br />

## Main goal of my work was to:
- provide **basic arithmetic operations**: implement fundamental operations such as addition, subtraction, multiplication, division, and exponentiation to ensure the calculator can handle a variety of basic mathematical tasks
- ensure **input validation and error handling**: validate user inputs to prevent incorrect calculations and handle errors gracefully, providing clear feedback to the user
- maintain a **history of operations**: store and display a history of all operations performed during the session, allowing users to review past calculations.
- create a **modular and extensible codebase**: design the calculator with a modular architecture, making it easy to extend with additional features and operations in the future.
<br />

## Solutions provided in the project
**1. Basic Arithmetic Operations**
The calculator provides basic arithmetic operations. The implementation of each operation is done through respective methods in the Calculator prototype.

    Calculator.prototype.add = function(num1, num2) {
      return num1 + num2; 
    }

    Calculator.prototype.sub = function(num1, num2) {
      return num1 - num2; 
    }

    Calculator.prototype.mul = function(num1, num2) {
      return num1 * num2; 
    }

    Calculator.prototype.div = function(num1, num2) {
      if (num2 === 0) {
          alert('Cannot divide by zero!');
          return null;
      }
      return num1 / num2; 
    }

    Calculator.prototype.pow = function(num1, num2) {
      return Math.pow(num1, num2);
    }
**2. Input Validation and Error Handling**
The calculator includes functions to check for NaN inputs and to provide user alerts when invalid data is entered.

    Calculator.prototype.checkIsNaN = function(num) {
        if(isNaN(num)) {
            alert('Invalid number entered!');
            return true;
        }
        return false;
    }
**3. History of Operations**
The calculator maintains a history of operations performed during the session and can display this history as a string.

    Calculator.prototype.getHistoryAsString = function() {
        return this.history.join('\n');
    }
    
    Calculator.prototype.transform = function(action, num1, num2) {
        if(this.checkIsNaN(num1) || this.checkIsNaN(num2)) {
            alert('Invalid data entered!');
            return;
        } else {
            const result = this[action](Number(num1), Number(num2));
            this.history.push(`${num1} ${action} ${num2} = ${result}`);
            return result;
        }
    }
**4. Modular and Extensible Codebase**
The codebase is designed with a modular approach, making it easy to extend with new operations or functionalities.

    const operations = {
        '+': calc.add,
        '-': calc.sub,
        '*': calc.mul,
        '/': calc.div,
        '^': calc.pow,
    };
    
    // Adding a new operation (example)
    Calculator.prototype.mod = function(num1, num2) {
        return num1 % num2;
    };
    
    operations['%'] = calc.mod;

**Example Usage**
The following example demonstrates how the calculator can be used interactively, prompting the user for operations and operands, and showing the history of calculations.

    const calc = new Calculator();
    let action, number1, number2;
    
    do {
        let promptContent = 'Choose an operation (+, -, *, /, ^) and confirm. \n';
        promptContent += 'Press Cancel to exit. \n';
        promptContent += 'History of operations: \n' + calc.getHistoryAsString();
    
        action = prompt(promptContent);
        if (calc.isCorrectAction(action)) {
            number1 = prompt('Enter number 1');
            number2 = prompt('Enter number 2');
    
            const result = calc.transform(action, number1, number2);
            if (result !== undefined) {
                alert(`Result: ${result}`);
            }
        }
    
    } while (calc.isCorrectAction(action));
<br />
<br />

## 🛠️ Languages and Tools used: 

<img align="left" alt="JavaScript" width="50px" src="https://raw.githubusercontent.com/github/explore/379d8d145b878a5b7a1c2a5b5800b1d82d5c8c8f/topics/javascript/javascript.png" />

<img align="left" alt="HTML5" width="50px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/html/html.png" />

<img align="left" alt="CSS3" width="50px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/css/css.png" />

<img align="left" alt="Git" width="50px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/git/git.png" />

<img align="left" alt="GitHub" width="50px" src="https://raw.githubusercontent.com/github/explore/78df643247d429f6cc873026c0622819ad797942/topics/github/github.png" />

<img align="left" alt="Terminal" width="50px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/terminal/terminal.png" />

<img align="left" alt="Visual Studio Code" width="50px" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/visual-studio-code/visual-studio-code.png" />

<br />
<br />
<br />
<br />

## :blue_heart:  You can find me on:
<br/>

[<img align="left" alt="Mateusz Sowa LinkedIn" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />](https://www.linkedin.com/in/katarzynadworakk/)

 
<br />

### Thanks
To Colorlib [colorlib.com](https://colorlib.com) for free templates.

# JavaScript: Podstawy

Twoim zadaniem będzie dopisanie do istniejącego kodu niezbędnych elementów, które pozwolą wykonywać obliczenia oraz przechowywać historię wykonanych operacji.

Nasz **kalkulator** powinien posiadać następujące opcje:

* dodawanie (+)
* odejmowanie (-)
* mnożenie (*)
* dzielenie (/)
* potęgowanie (^) – wykonaj to przy pomocy pętli, nie korzystaj z `Math.pow()`.

Gdy otworzysz plik `./js/app.js`, to zauważysz, że mamy tam już gotowy konstruktor o nazwie `Calculator`, który musimy uzupełnić odpowiednimi metodami.

Wzoruj się na metodzie `Calculator.prototype.add`, w której znajdziesz rozpiskę kolejnych kroków do wykonania.

We naszym pliku `app.js` wykorzystujemy również pętlę [do...while](https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Polecenia/do...while), która w swoim wnętrzu pobiera dane od użytkownika. Na ich podstawie wykonywane są dalsze czynności. 

To tam należy dopisać kilka instrukcji `if` oraz wywołać odpowiednie metody.
