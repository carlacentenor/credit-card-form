

## Funciones Statements y Globales

```javascript
function activeButton() {
    $buttonNext.attr('disabled', false);
  }
``` 
 
  ```javascript
function desactiveButton() {  
     $buttonNext.attr('disabled', true);
  } 
```

```javascript
function lengthCard(input) {
    if (input.trim().length === 16) {
      return input;
    }
  }
```

```javascript
function onlyNumbers(input) {
    var regex = /^[0-9]+$/;
    if (regex.test(input)) {
      return input;
    }
  }
```

```javascript
function isValidCreditCard(numberCard) {
    var creditCardNumber = onlyNumbers(lengthCard(numberCard));
    if (creditCardNumber !== undefined) {
      var arr = [];
      var sumTotal = 0;
      for (var index = creditCardNumber.length - 1; index >= 0; index--) {
        arr.push(creditCardNumber[index]);
      }
      for (var index = 1; index < arr.length; index = index + 2) {
        arr[index] = arr[index] * 2;
        if (arr[index] >= 10) {
          arr[index] = arr[index] - 9;
        }    
      }
     
      for (var index = 0; index < arr.length; index++) {
        sumTotal = sumTotal + parseInt(arr[index]);
      }
     
      if (sumTotal % 10 === 0) {
        console.log('Es una tarjeta valida');
        activeButton();
      } else {
        console.log('No es un numero valido');
        desactiveButton();
      }
    } else {
      console.log('Verifique el numero de su tarjeta'); 
      desactiveButton();  
    }
  }
```
## Función Anónima

```javascript
$inputCard.on('input', function() {
    isValidCreditCard($(this).val().trim());
  });
```

```javascript
$(document).ready(function() {

}
```

## Función Callback

```javascript
var creditCardNumber = onlyNumbers(lengthCard(numberCard));
```

## Funciones de stack execution
En la función `isValidCreditCard` existen estas funciones que forman parte de la pila de Ejecución.

1.-  `onlyNumbers()`

2.-  `lengthCard()` 

## Funciones que forman parte de la cola de Eventos (event queue)

La función `isValidCreditCard` forma parte de la cola de ejecución durante el evento `input`.

```javascript
$inputCard.on('input', function() {
    isValidCreditCard($(this).val().trim());
  });
```

