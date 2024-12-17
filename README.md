# u03-quiz-app-copy


Using splice to clear the highestScores array does work, but there are a few considerations to improve clarity and ensure proper behavior.

Why splice works
The line:

javascript
Copy code
highestScores.splice(0, highestScores.length);
Removes all elements from the highestScores array.
Since splice modifies the array in place, any other part of your code that references highestScores will see it emptied.
Is splice necessary here?
If your intention is to completely reset the highestScores array, a simpler and cleaner alternative is:

javascript
Copy code
highestScores.length = 0;
This clears the array without creating a new reference.
It's shorter and arguably easier to understand.
Local Storage and Array References
localStorage.removeItem("highestScores"); clears the data stored in localStorage, but you still need to reset the in-memory highestScores array. That’s why you’re using splice.

Full Summary
Your use of splice is correct and works.
Improvement: Replace splice with highestScores.length = 0; for clarity.
Here’s the improved snippet:

javascript
Copy code
clearBtn.addEventListener("click", () => {
  localStorage.removeItem("highestScores");
  highestScores.length = 0; // Clear the array
  highestResultsList.innerHTML = "";
  clearBtn.style.display = "none";
  const finalScore = document.getElementById("finalScore");
  finalScore.style.display = "none";
  highestResultsList.style.display = "none";
});
