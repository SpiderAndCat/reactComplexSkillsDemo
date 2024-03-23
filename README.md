# reactComplexSkillsDemo
This repo showcases my understanding of more complex React skills through code snippet walkthroughs, about the following topics:
- **Complex State** (nested JS objects and arrays),
- **Destructuring** (Arrays, Objects, and nested Arrays and Objects),
- **Controlled Components** (reflecting state across components),
- **Event Handling** (across components)

## Code Skill snippet overviews

### Destructuring
```js
// Animal data
const animals = {
  cat: {
    name: "Jimmy",
    sound: "meow",
    feedingRequirements: {
      food: "fish",
      drink: "water",
    },
  },
  dog: { name: "Arfy", sound: "woof" },
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

//--------------(1) Destructuring Objects-----------------//

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
//--------------(2) Functional Objects-----------------//


### Complex State
```js
//show code here
```

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
