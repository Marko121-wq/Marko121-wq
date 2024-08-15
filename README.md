- 👋 Hi, I’m @Marko121-wq
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Marko121-wq/Marko121-wq is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
// ==UserScript==
// @name         EncryptMyData
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Content Pythonista
// @author       Inger
// @match        *://*/*
// @icon         https://www.drupal.org/files/issues/2020-02-26/favicon-v5.png
// @grant        none
// @run-at       document-end
// ==/UserScript==



(function() {
    'use strict';
// Define the text and value variables here
const text1 = "4.991,87";
const value1 = "80,937.14";
const text2 = "text2";
const value2 = "value2";
const text3 = "text3";
const value3 = "value3";
const text4 = "text4";
const value4 = "value4";
const text5 = "text5";
const value5 = "value5";

// function to replace text
function replaceText(target) {
  // Find all text nodes in the target element
  const walker = document.createTreeWalker(target, NodeFilter.SHOW_TEXT, null, false);
  let node;

  while (node = walker.nextNode()) {
    // Check if the text node contains the search value
    if (node.textContent.match(text1)) {
      // Replace the search value with the replace value
      const newText = node.textContent.replace(new RegExp(text1, 'g'), value1);
      node.textContent = newText;
    }
    if (node.textContent.match(text2)) {
      // Replace the search value with the replace value
      const newText = node.textContent.replace(new RegExp(text2, 'g'), value2);
      node.textContent = newText;
    }
    if (node.textContent.match(text3)) {
      // Replace the search value with the replace value
      const newText = node.textContent.replace(new RegExp(text3, 'g'), value3);
      node.textContent = newText;
    }
    if (node.textContent.match(text4)) {
      // Replace the search value with the replace value
      const newText = node.textContent.replace(new RegExp(text4, 'g'), value4);
      node.textContent = newText;
    }
    if (node.textContent.match(text5)) {
      // Replace the search value with the replace value
      const newText = node.textContent.replace(new RegExp(text5, 'g'), value5);
      node.textContent = newText;
    }
  }
}

// function to run after page is fully rendered
function onPageLoad() {
  // Replace all occurrences of the texts with the corresponding values in the body
  replaceText(document.body);

  // Set up a mutation observer to detect changes in the DOM
  const observer = new MutationObserver(function(mutationsList) {
    for (let mutation of mutationsList) {
      if (mutation.type === 'childList') {
        // Replace all occurrences of the texts with the corresponding values in the new content
        replaceText(mutation.target);
      }
    }
  });

  // Start observing the DOM for changes
  observer.observe(document.body, { childList: true, subtree: true });
}

// function to restart the JavaScript code
function restartCode() {
  // Remove event listener to prevent multiple restarts
  document.removeEventListener("click", restartCode);

  // Call the onPageLoad function again
  onPageLoad();

  // Add event listener to detect click and restart the code
  document.addEventListener("click", restartCode);
}

// Add event listener to detect click and restart the code
document.addEventListener("click", restartCode);

// Call the onPageLoad function when the page is fully loaded
window.addEventListener("load", onPageLoad);

})();
