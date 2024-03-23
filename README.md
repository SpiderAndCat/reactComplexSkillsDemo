# reactComplexSkillsDemo
This repo showcases my understanding of more complex React skills through code snippet walkthroughs, and an interative web app demo. This demonstrates my understaning of the following topics:
- **Complex State** (nested JS objects and arrays),
- **Destructuring** (Arrays, Objects, and nested Arrays and Objects),
- **Controlled Components** (reflecting state across components),
- **Conditional Rendering** (utilizing the Terenary and AND operators)
- **Event Handling** (across components)

## Code Skill snippet overviews

### Destructuring
```js
// Animal data
const animals = {
  cat: {
    name: "cat",
    sound: "meow",
    feedingRequirements: {
      food: "fish",
      drink: "water",
    },
  },
  dog: { name: "dog", sound: "woof" },
// Toggle including this:
// hamster: { name: "hamster", sound: "squeak" },

};

function hearAnimal(animal) {
  return [
    animal.name,
    function () {
      console.log(animal.sound);
    },
  ];
}
export default animals;
export { hearAnimal };

```

```js
// App logic
import animals, { hearAnimal } from "./data";

//-------------- Destructuring Objects -----------------//

console.log("Animals: ", animals);
/*Prints:
Animals:  
  {cat: Object, dog: Object, hamster: Object}
  cat: 
    {name: 'cat', sound: 'meow', feedingRequirements: Object}
  dog: 
    {name: 'dog', sound: 'woof'}
  hamster: 
    {name: 'hamster', sound: 'squeak'}
*/

const {
  cat: {
    feedingRequirements: { food: catFood },
  },
  dog,
  hamster: {
    name: hamsterName,
    feedingRequirements: hamsterDiet = {
      food: "small veggies",
      drink: "water",
    },
  },
} = animals;
// this approach also overwrites the required `food` key to be a more communicative name, `catFood`
// and assigns a `hamsterDiet` to specify between the common `feedingRequirements` keys

console.log(
  "Cats eat ",
  catFood +
    " and can be friends with a " +
    dog.name +
    " but maybe not a " +
    hamsterName
);

/*Prints:
Cats eat  fish and can be friends with a dog but maybe not a hamster
*/

console.log("Hamster Diet: ", hamsterDiet);
// defaults to the given object when the source data does not have that key, such as in this case
/*Prints:
{food: 'small veggies', drink: 'water'}
*/


// This is useful when ingesting JSON API objects, treated as JS objects. This approach shows how I store only the values I am interested in: `cat > feedingRequirements > food`, and then the entire `dog` object. Similar use cases are used when only needing to access particular fields of JSON API inputs, and not worrying about excess metadata. 
```

### Complex State
```js
import React, { useState } from "react";

function App() {
// -------------------------- State ------------------------ //

  const [contact, setContact] = useState({
    fName: "",
    lName: "",
    email: ""
  });

// ---------------------- Event Handler -------------------- //

  function handleChange(event) {
    // Grabs the input field name (component identifier) and value (linked to a state) from the input field that triggered the event
    const { name, value } = event.target;

    // Utilizes the spread operator, to create a new object, merging the old data, and overwriting the field that is being edited and thereby triggered the event
    setContact(prevValue => {
      return {
        ...prevValue,
        [name]: value
      };
    });
  }

// ----------------------- Form Markup --------------------- //

  // The controlled components bind the state variables to the value displayed in the text field, in real time (between each character typed)
  return (
    <div className="container">
      <h1>
        Hello {contact.fName} {contact.lName}
      </h1>
      <p>{contact.email}</p>
      <form>
        <input
          onChange={handleChange}
          name="fName"
          value={contact.fName}
          placeholder="First Name"
        />
        <input
          onChange={handleChange}
          name="lName"
          value={contact.lName}
          placeholder="Last Name"
        />
        <input
          onChange={handleChange}
          name="email"
          value={contact.email}
          placeholder="Email"
        />
        <button>Submit</button>
      </form>
    </div>
  );
}

export default App;
```
### Conditional Rendering
See my ***dedicated repo*** & ***live web app*** demo which showcases this skill:
https://github.com/SpiderAndCat/reactBasicsDemo_conditionalRenderingAndUseState

### Controlled Components
```js
// the <input> "value" will be tied to a state, 'inputText'
const [inputText, setInputText] = useState("");
...
// The <input> field will only show the value of 'inputText'. The field will properly update to show the string being typed, thanks to the inclusion of "value={inputText} />"
<input onChange={handleChange} type="text" value={inputText} />
...

```
## See these skills put to the test!
 ***Access the live demo*** here: (WIP)


### Event Handling (across Components)
```js
//show code here
```
