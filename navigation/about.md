---
layout: post
title: About Me
permalink: /about/
comments: true
---

## My Conversation Starters

Here are some places I have lived.



<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
        }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<!--
<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
   var living_in_the_world = [
  <img src="{{site.baseurl}}/images/India-flag-a4.jpg" alt="flag of India">
  <img src="{{site.baseurl}}/images/about/tamara_fam.jpg" alt="Image 3">
  <img src="{{site.baseurl}}/images/about/surf.jpg" alt="Image 4">
  <img src="{{site.baseurl}}/images/about/john_lora.jpg" alt="Image 5">
  <img src="{{site.baseurl}}/images/about/lora_fam.jpg" alt="Image 6">
    ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements
        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // concatenate the source and flag
        img.alt = location.flag + " Flag"; // add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script> -->



<div class="row">
  <img src="{{site.baseurl}}/images/India-flag-a4.jpg" style="height:100px; margin-right:50px;">
  <img src="{{site.baseurl}}/Flag-of-america.png" style="height:100px; margin-right:50px;">
  <img src="{{site.baseurl}}/images/Flag_of_California.svg.png" style="height:100px; margin-right:50px;">
  <img src="{{site.baseurl}}/images/download.jpeg" style="height:100px; margin-right:50px;">
</div>
India - Two years        Moved to America        I've lived in California for 12 years        One day I'll explore the Galaxy as an astronaut! -->



### Journey through Life

Here's a little bit about me!

- 🏫 Elementary School and Middle School in San Diego (CA)
- 🏫 High School in San Diego (CA), Del Norte High, Class of '29
- 🎓 My dream College is Cornell for Aerospace Engineering!
- 🧑‍🚀 When I grow up, I want to be an Astronaut!
- 💼 I want to work at NASA or ISRO or another space agency.
- 🎓 I want to hopefully go to space and make a discovery that changes lives!
- 💼 I have a little brother and a big sister

### Culture, Family, and Fun

Everything for me, as for many others, revolves around family and faith.

- I am proud to be an Indian American
- I have a big family and a lot of cousins!

<comment>
Gallery of Pics, scroll to the right for more ...
</comment>
<div class="image-gallery">
  <img src="{{site.baseurl}}/images/India-flag-a4.jpg" alt="flag of India">
  <img src="{{site.baseurl}}/images/alaska-trip (1).jpg" alt="Image 3">
  <img src="{{site.baseurl}}/images/cruise-pic (1).jpg" alt="Image 4">
  <img src="{{site.baseurl}}/images/deshatty-family-pic (1).jpg" alt="Image 5">
  <img src="{{site.baseurl}}/images/mariokart-universal-pic (1).jpg" alt="Image 6">
  <img src="{{site.baseurl}}/images/mom-sam-dad-alaska (1).jpg" alt="Image 7">
  <img src="{{site.baseurl}}/images/samaghna-alaska-pic (1).jpg" alt="Image 8">
  <img src="{{site.baseurl}}/images/sesame-street-pic (1).jpg" alt="Image 9">
</div>
