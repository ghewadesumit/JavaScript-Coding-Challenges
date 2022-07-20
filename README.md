# JavaScript-Coding-Challenges
JavaScript Coding Challenges


# Recursion Coding Questions

1. get all the names of the artists from the object into an array and finally return the array

```js

const artistsByGenre = {
  jazz: ["Miles Davis", "John Coltrane"],
  rock: {
      classic: ["Bob Seger", "The Eagles"],
      hair: ["Def Leppard", "Whitesnake", "Poison"],
      alt: {
          classic: ["Pearl Jam", "The Killers"],
          current: ["Joywave", "Sir Sly"]
      }
  },
  unclassified: {
      new: ["Caamp", "Neil Young"],
      classic: ["Seal", "Morcheeba", "Chris Stapleton"]
  }
}
```

Answer:

```js
const printArtist = (artistsObj,arr) => {
  if(artistsObj == null) return arr;
  for(let i in artistsObj){
    if(Array.isArray(artistsObj[i])){
       artistsObj[i].forEach((artist)=>{
         console.log(artist);
         arr.push(artist);
       });
    }else{
    // we do not return from here because it will break the loop so instead return the array after the loop
       printArtist(artistsObj[i],arr);
    }
  }
  return arr;
}


console.log('artists are', printArtist(artistsByGenre,[]));
```


2. Deep copy of an object
```js
Object.assign({}, obj);

// another way
JSON.parse(JSON.stringify(obj))
```
```js

function deepCopy(obj){
  if(typeof obj == 'object' || obj == null) return obj;
  
  let newObj = Array.isArray(obj) ? [] : {};
  
  for(let i in obj){
    let value = obj[i];
    newObj[i] = deepCopy(value);
    }
    
    return newObj;
  }
```

3. Create an object with a property 'marks' which cannot be set to a value less than 0

```js
const normalObj = {
  marks:0,

  set setMarks(value){
    if(value < 0) throw new Error('Cant set value of marks less than zero');
    this.marks = value;
  },
  get getMarks(){
    return this.marks;
  }
}


normalObj.setMarks = 10;
console.log(normalObj.getMarks);
```


4. Singleton Pattern

```js

const singleton = (function(){
  function ProcessManager(){
    this.numprocess = 0;
  }

  let processManagerInstance = null;

  function createProcessManager(){
    
      processManagerInstance = new ProcessManager();
      return processManagerInstance;
  }
    return {

      getProcessManager: ()=>{
        if(!processManagerInstance){
          processManagerInstance = createProcessManager();
        }
        return processManagerInstance;
      }

    }
})()


let instanceOne = singleton.getProcessManager();
let instanceTwo = singleton.getProcessManager();

console.log(instanceOne === instanceTwo);

```
