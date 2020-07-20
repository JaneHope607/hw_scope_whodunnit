# Scope Homework: Who Dunnit

### Learning Objectives

- Understand function scope
- Know the difference in between the let and const keywords

## Brief

Using your knowledge about scope and variable declarations in JavaScript, look at the following code snippets and predict what the output or error will be and why. Copy the following episodes into a JavaScript file and add comments under each one detailing the reason for your predicted output.

### MVP

#### Episode 1

```js
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Library',
  weapon: 'Rope'
};

const declareMurderer = function() {
  return `The murderer is ${scenario.murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);
```

<!-- Outcome - The murderer is Miss Scarlet. -->
<!-- Reason: The declareMurderer function returns the string with the murderer value -->

#### Episode 2

```js
const murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```

<!-- Outcome: Error -->
<!-- Reason: There would be an error here are the murderer variable is trying to be reasssigned but it is a constant variable so this is not allowed -->


#### Episode 3

```js
let murderer = 'Professor Plum';

const declareMurderer = function() {
  let murderer = 'Mrs. Peacock';
  return `The murderer is ${murderer}.`;
}

const firstVerdict = declareMurderer();
console.log('First Verdict: ', firstVerdict);

const secondVerdict = `The murderer is ${murderer}.`;
console.log('Second Verdict: ', secondVerdict);
```

<!-- Outcome - 'First Verdict: Mrs. Peacock.' -->
<!-- Outcome - 'Second Verdict: Professor Plum.' -->
<!-- Reason - The first outcome is because the declareMurderer function is called which creates a new local variable
with 'Mrs. Peacock' assigned to it. The second is because it is calling the murderer vairable directly outside of the function.  -->


#### Episode 4

```js
let suspectOne = 'Miss Scarlet';
let suspectTwo = 'Professor Plum';
let suspectThree = 'Mrs. Peacock';

const declareAllSuspects = function() {
  let suspectThree = 'Colonel Mustard';
  return `The suspects are ${suspectOne}, ${suspectTwo}, ${suspectThree}.`;
}

const suspects = declareAllSuspects();
console.log(suspects);
console.log(`Suspect three is ${suspectThree}.`);
```

<!-- Outcome - 'Suspects are Miss Scarlet, Professor Plum, Colonel Mustard.'
'Suspect three is Mrs. Peacock' -->
<!-- Reason: Colonel Mustard has become suspect three for when declareAllSuspects has been called. However in the last console log, it returns the initial suspectThree variable (Mrs peacock )which has remained unchanged due to the reassignment of suspectThree variable only extending to the scope of the declareAllSuspects function -->


#### Episode 5

```js
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Kitchen',
  weapon: 'Candle Stick'
};

const changeWeapon = function(newWeapon) {
  scenario.weapon = newWeapon;
}

const declareWeapon = function() {
  return `The weapon is the ${scenario.weapon}.`;
}

changeWeapon('Revolver');
const verdict = declareWeapon();
console.log(verdict);
```

<!-- Outcome - The weapon is the revolver. -->
<!-- Reason - This is because changeWeapon is called with the argument revoler, giving the weapon key a new value of revolver. Then the declareWeapon function is called and stored within a constant varibale, then printed to the console.Objects can be mutated with a cont variable. -->


#### Episode 6

```js
let murderer = 'Colonel Mustard';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    murderer = 'Mrs. White';
  }

  plotTwist();
}

const declareMurderer = function () {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```

<!-- Outcome - The murderer is Mrs White. -->
<!-- Reason: changeMurderer is called which reassigns the value of the variable murderer first to Mr. Green. A second function is then called, plotTist, which reassigns the variable murderer to Mrs. White -->

#### Episode 7

```js
let murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    let murderer = 'Colonel Mustard';

    const unexpectedOutcome = function() {
      murderer = 'Miss Scarlet';
    }

    unexpectedOutcome();
  }

  plotTwist();
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
```

<!-- Outcome - The murderer is Mr Green -->
<!-- Reason: There would be an error here are the murderer variable is trying to be reasssigned but it is a constant variable so this is not allowed -->

#### Episode 8

```js
const scenario = {
  murderer: 'Mrs. Peacock',
  room: 'Conservatory',
  weapon: 'Lead Pipe'
};

const changeScenario = function() {
  scenario.murderer = 'Mrs. Peacock';
  scenario.room = 'Dining Room';

  const plotTwist = function(room) {
    if (scenario.room === room) {
      scenario.murderer = 'Colonel Mustard';
    }

    const unexpectedOutcome = function(murderer) {
      if (scenario.murderer === murderer) {
        scenario.weapon = 'Candle Stick';
      }
    }

    unexpectedOutcome('Colonel Mustard');
  }

  plotTwist('Dining Room');
}

const declareWeapon = function() {
  return `The weapon is ${scenario.weapon}.`
}

changeScenario();
const verdict = declareWeapon();
console.log(verdict);
```

<!-- Outcome - The weapon is Candle Stick. --> 
<!-- Reason: changeScenario is called which in turn changes the murderer to Mrs Peacock and the room to Dining Room. plotTwist equates to true so changes the murderer to Colonel Mustard. Then unexpectedOutcome equates to true and so the weapon is changed to Candle Stick. -->

#### Episode 9

```js
let murderer = 'Professor Plum';

if (murderer === 'Professor Plum') {
  let murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);
```

<!-- Outcome - The murderer is Professor Plum. -->
<!-- Reason - The if statement is reassinging the murderer variable to Mrs. Peacock, only when the condition is true and also 
only inside that block of code as it us declared using let. This doesn;t affect the intial value of the variable and so 
in the declareMurderer function, the initial variable value is -->


### Extensions

Make up your own episode!
