# style-guide-no-limit
A simple react style guide for the No Limit Software team

## Boolean Naming
Boolean variables/constants must start with **is** or **has**
Names must be short and affirmative(non-negative).

```javascript
//good
const isPaidFor = true;

//bad
const areBillsPaidFor = true;
```

## No Nested Terneries
Nested ternaries make code unreadable.
Prefer to use an if statement and extract the code in a separate function.

```javascript
//good
if(confirm) {
    <ConfirmationPopup />
} else {
    miniForm ? <MiniForm/> : <OtherForm/>
}

//bad
confirm ?
    <ConfirmationPopup />
    :
    miniForm ? <MiniForm/> : <OtherForm/>
```

## Commented code is used only for explanation.
Delete the code, do not comment out blocks of code. If we need it for some reason later on it is in the git history.

## Don't leave any console objects in production
Always delete `console.log` or similar code used for testing before merging

## Prefer if/return over if/else in functions
If your function only has two return possibilities, and one is conditional, then you do not need the `else { }` block around your non-conditional return. Make that return your default, and include an `if` condition before
```javascript
//good
function sayHello(name) {
  if(name.length > 10) {
     return "Wow ${name}, you have a very long name."
  } 
  return "Hello, ${name}!"
}

//bad
function sayHello(name) {
  if(name.length > 10) {
     return "Wow ${name}, you have a very long name."
  } else {
     return "Hello, ${name}!"
  }
}
```

## Prefer using constants over long prop values
Long prop values should be stored in a constant outside of the component.
```javascript
//good
const initialValues = {email: '', firstName: '', lastName: '', commentBox: ''}
<Formik initialValues={{...initialValues}}>

//bad
<Formik
  initialValues={{
    email: '',
    firstName: '',
    lastName: '',
    commentBox: '',
  }}
>
```

## Prefer if statements over && in functions 
If it is not a conditional statement don't treat it like one. Prefer if statement since we are not assigning values and it is clearer what is executed in the block.
```javascript
//good
if (hero){
    window.scroll({ top: hero.offsetTop, behavior: 'smooth' });
}

//bad
hero &&
    window.scroll({ top: hero.offsetTop, behavior: 'smooth' });
```

This is also okay:
```javascript
const name = hero && "Superman";
```

## Destrucutre objects where appropirate
If an object has multiple fields that you use in the same place than prefer to desctructure them instead of using dot notation to access an object's attributes.
```javascript
//good
const {linksFirstCol, linksSecondCol, linksThirdCol} = navItem;

linksFirstCol.map((link) => ())
linksSecondCol.map((link) => ())
linksThirdCol.map((link) => ())

// bad
navItem.linksFirstCol.map((link) => ())
navItem.linksSecondCol.map((link) => ())
navItem.linksThirdCol.map((link) => ())
```
