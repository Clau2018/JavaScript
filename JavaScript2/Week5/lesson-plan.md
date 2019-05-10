# Lesson plan
```
> Focus on having lots of in class exercises.

> DONT teach everything, let the students investigate topics on their own aswell!

> Focus on how to read documentation, google answers and google errors!!

> Teach towards the students being able to solve the homework
```

Remember to add the code you wrote in the class to the relevant class branch's class work folder. If the branch has not been created just create and push it :) If you dont have access, write to one from the core team. You can see an example below!

To find examples of what teachers have taught before go to the class branches in the classwork folder, Fx [class 07](https://github.com/HackYourFuture-CPH/JavaScript/tree/class07/JavaScript1/Week1/classwork)

If you find anything that could be improved then please create a pull request! We welcome changes, so please get involved if you have any ideas!!!

---

- Array functions - only do with traditional function, no arrow keys yet!
  - Try write your own `forEach`, `map` and `filter` with the students. Shows very precisely how it works!
  - ForEach - Executes function forEach element, NO RETURN!
    - [Code inspiration](#foreach)
    - [Foreach homemade](#foreach-homemade)
    - [Exercises](#foreach-1)
  - Map - Changes the items in the array
    - [Code inspiration](#map)
    - [Foreach homemade](#map-homemade)
    - [Exercises](#map-1)
  - Filter - Changes the number of items in the array. Let the students investigate filter
    - [Code inspiration](#filter)
    - [Foreach homemade](#filter-homemade) - Get help from students to write this
    - [Exercises](#filter-1)
  - [Other example](#other-example)
- Arrow function
  - [Code inspiration](#arrow-function)
  - [Exercises](#arrow-functions)

<!---
- Code flow, using the [call stack](../../JavaScript1/Week3/readme.md#call-stack)
-->


[Listing project](#listing-project) - Uses arrow Functions, map, filter and forEach


## Code inspiration

### Mentors

```js
const mentors = [
    { "name": "Abed Sujan", "subjects": ['JS', 'HTML', 'CSS', 'NODEJS'], yearOfExperience: 4},
    { "name": "Ahmed Magdy", "subjects": ['JS', 'Database', 'CSS'], yearOfExperience: 1},
    { "name": "Alicia Gonzales", "subjects": ['DB', 'HTML', 'NODEJS'], yearOfExperience: 8},
    { "name": "allan Thraen", "subjects": ['REACT', 'HTML', 'CSS'], yearOfExperience: 3},
    { "name": "Anders Ravn", "subjects": ['JS', 'HTML', 'NODEJS'], yearOfExperience: 2},
    { "name": "Daniel Fernandes", "subjects": ['Database', 'HTML', 'CSS'], yearOfExperience: 9}
];

console.log(mentors);
```
### ForEach 

```js
mentors.forEach(function(mentor) {
    console.log(mentor);
    console.log(mentor.name);

    mentor.subjects.forEach(function(subject) {
        console.log(subject);
    });
});

```

### ForEach homemade

```js
function forEachHomemade(array, functionToExecute) {
    for (let i = 0; i < array.length; i++) {
        const currentItem = array[i];
        functionToExecute(currentItem, i);
    }
}

```

### Map

```js
// We are mapping/transforming the mentors array. Same size, different items.
const mentorNames = mentors.map(function(mentor) {
    return mentor.name;
});

const mentorNamesFormatted = mentors.map(function(mentor) {
    return 'Mentors name is: ' + mentor.name;
});

const mentorSummary = mentors.map(function(mentor) {
    return `Mentors name is: ${mentor.name}. He has ${mentor.yearsOfExperience} years of experience`;
});
```

### Map homemade

```js
function mapHomemade(array, functionToExecute) {
    const mappedArray = [];
    for (let i = 0; i < array.length; i++) {
        const currentItem = array[i];
        const newItem = functionToExecute(currentItem, i);
        // This is where the magic happens!!!
        mappedArray.push(newItem);
    }

    return mappedArray;
}
```


### Filter

```js
// We are mapping/transforming the mentors array. Same size, different items.
const experiencedMentors = mentors.filter(function(mentor) {
    if (mentor.yearsOfExperience > 7) {
        return true;
    } else {
        return false;
    }

    // can also be written as
    // reuturn mentor.yearsOfExperience > 7
    // Explain why!
});

// Get help from students to write this
const mentorsThatStartWithA = mentors.filter(function(mentor) {
    return mentor.name[0] == 'A'; // Missing Allan, why?? lowercase
});

```

### Filter homemade

```js
function FilterHomemade(array, functionToExecute) {
    const filteredArray = [];
    for (let i = 0; i < array.length; i++) {
        const currentItem = array[i];
        const shouldKeepItemInNewArray = functionToExecute(currentItem, i);
        // This is where the magic happens!!!
        if (shouldKeepItemInNewArray) {
            filteredArray.push(currentItem);
        }
    }

    return filteredArray;
}
```


### Arrow function

```js
function circleArea(radius) {
    return radius * 2 * Math.pi;
}

// Remove the function keyword add in arrow
const circleArea1 = (radius) => {
    return radius * 2 * Math.pi;
}

// If there is only one parameter, we can remove the paranthesis
const circleArea2 = radius => {
    return radius * 2 * Math.pi;
}

// If there is only one line in the function we can remove the curly braces and the return statement
// radius * 2 * Math.pi is AUTOMATICALLY being returned
const circleArea3 = radius => radius * 2 * Math.pi;

```


### Other example
```js
function filterMentorList(courseID) {
    const resultHtml = document.getElementById('result');

    let listHtml = '';
    listHtml += '<div> Fowad</div>';
    listHtml += '<div> Susane</div>';
    listHtml += '<div> Sara</div>';
    resultHtml.innerHTML = listHtml;
    
    console.log('courseID', courseID);
}

let modifiedMentors = mentors.map(function(mentor) {

    mentor.name = (mentor["name"].length >10)? "Mr "+ mentor.name: "Ms " + mentor.name;

    mentor.age = mentor["name"].length;
    // if(mentor["name"].length >10)
    // mentor.name = "Mr " + mentor.name;
    // else 
    // mentor.name = "Ms " + mentor.name;
    
    return mentor;

});

function filterMentorList(courseID) {
    const resultHtml = document.getElementById('result');
    let listHtml = '';

    let filteresListByCourseId = mentors.filter(function (mentor) {
        const sub = mentor.subject;
        return sub.indexOf(courseID) >= 0;
    });

    filteresListByCourseId.forEach(function (mentor) {
        listHtml += `<div>  ${mentor.name}  - ${mentor.age}  </div>`;
    });

    resultHtml.innerHTML = listHtml;
}



 function filterMentorListUsingFor(courseID){
    const resultHtml = document.getElementById('result');
    let listHtml = '';
    for(let i=0; i<mentors.length; i++){
    
        listHtml += `<div> ${mentors[i].name}</div>`;
    } 
    resultHtml.innerHTML = listHtml;
    console.log('courseID', courseID);
} 
```


## Exercises

Use this function to generate random listings

```js
/**
 * Get random integer between two numbers, found here: https://stackoverflow.com/a/7228322
 * @param {integer} min - The min number
 * @param {integer} max - The max number
 * @returns {Number} Random number between min and max
 */
function randomIntFromInterval(min, max) {
    return Math.floor(Math.random() * (max - min + 1) + min);
}


/**
 * Get an array with Rental objects with random color and speed
 * @param {integer} numberOfRentals - The number of Rentals 
 * @returns {array} Array containing the Rental objects
 */
function generateRentalListings(numberOfRentals) {
    const rentals = [];

    const rentalType = ['House', 'Apartment', 'Shed', 'Dorm', 'Farm'];
    const rentalFacilities = ['Parkering', 'Elevator', 'Altan', 'Have', 'Husdyr'];
    
    for (let i = 0; i < numberOfRentals; i++) {
        const rental = {};
        const randomTypeIndex = randomIntFromInterval(0, rentalType.length - 1);
        const numberOfFacilities = randomIntFromInterval(1, rentalFacilities.length - 1);
        const facilities = [];
        for(let i = 0; i < numberOfFacilities; i++) {
            const randomIndexFacilities = randomIntFromInterval(0, rentalFacilities.length - 1);
            const randomFacility = rentalFacilities[randomIndexFacilities];
            
            if (!(facilities.includes(randomFacility))) {
                facilities.push(randomFacility);
            }
        }

        rental.type = rentalType[randomTypeIndex];
        rental.facilities = facilities;
        rental.price = randomIntFromInterval(1, 10000);
        rental.hasGarden = Boolean(randomIntFromInterval(0, 1));
        rental.size = randomIntFromInterval(12, 1000);

        rentals.push(rental);
    }

    return rentals;
}

generateRentalListings(20);
```

### ForEach

- Create 37 listings and log out every listings size

### Map

- Create an array that contains all the listings prices. 

### Filter 

- Create an array of cheap listings. You define what cheap means. Each item in this array should be of type object
- Create an array of expensize listings prices. Each item in this array should be of type number
- Create an array of listings that have parking. Each item in this array should be of type object


### Arrow functions

Rewrite the code above (`forEach`, `map` and `filter`) to arrow functions.


### Listing project

