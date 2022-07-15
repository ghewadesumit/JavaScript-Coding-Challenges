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
