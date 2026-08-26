---
layout: post
title: About
permalink: /about/
comments: true
---

## As a conversation Starter

Hi! My name is Barbara. Here are some places I have lived.

<comment>
Flags are made using Wikipedia images
</comment>

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

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
    {"flag": "0/01/Flag_of_California.svg", "greeting": "Hey", "description": "California - most of the 17 years of my life"},
    {"flag": "f/fa/Flag_of_the_People%27s_Republic_of_China.svg", "greeting": "Nǐ hǎo", "description": "China - a couple months when I was a baby"}
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
</script>

### Here's some basic information about me

- I am Chinese-American
- Born in Santa Barbara and lived for the first couple years of my life. Then, I moved to San Diego and have lived here since.
- Some of my hobbies include drawing, editing photos and videos, taking photos, and listening to music.
- my favorite food are mochi donuts!
- I like using kaomojis/emoticons. these things --> ( ˶ˆᗜˆ˵ )

### Interests - more specific stuff

- I like to listen to j-pop and vocaloid. My main <a href="https://youtube.com/playlist?list=PLrSSNb7pD0xFcy_ttT4B4tn8Ag-iBJ9qS&si=Eis16K00riS9n2al">playlist</a> consists of over 600 songs, but I mainly just like to listen to the most recent songs because I tend to get tired of songs easily and I'm too lazy to create a new playlist.
- The main fandoms I'm in are Alien Stage, Chiikawa, and Project Sekai. The gallery includes pictures of the stuff I'm interested in, artwork I've made, and me :3

<comment>
Gallery of Pics, scroll to the right for more ...
</comment>
<div class="image-gallery">
  <img src="https://imgs.search.brave.com/MlEi9ic9bu3rkctC5TBStqgY1mCvjzTBqsi4SfSVjwg/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9tLm1l/ZGlhLWFtYXpvbi5j/b20vaW1hZ2VzL00v/TVY1Qk5qVTJOV0Zs/WVdVdE5tVmlZaTAw/WldWbUxUazBaR1l0/TUdObU1EUXdZbVF6/TkRRelhrRXlYa0Zx/Y0djQC5qcGc" alt="Image 1">
  <img src="https://imgs.search.brave.com/d-zcBiPx56BDf1a8in7__v98yDAmuX7SH6s-XWgmlMM/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9pMC53/cC5jb20vemFsb3Jh/c2luZ2Fwb3JlYmxv/Zy53cGNvbXN0YWdp/bmcuY29tL3dwLWNv/bnRlbnQvdXBsb2Fk/cy8yMDI1LzA2L0No/aWlrYXdhLndlYnA_/cmVzaXplPTcyMCw2/Nzgmc3NsPTE" alt="Image 2">
  <img src="https://static.wikia.nocookie.net/projectsekai/images/b/bf/Main-image.jpg/revision/latest?cb=20201011130100" alt="Image 3">
  <img src="https://imgs.search.brave.com/y-Cr5XIiFaFEy-C2kxMuNE4sTO3ax4bq9MWrmT8eSDU/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9jZG4u/c3ByaW5rbGViYWtl/cy5jb20vbWVkaWEv/MjAyMi8wNi9Nb2No/aS1kb3VnaG51dHMt/MTEtMS5qcGc" alt="Image 4">
  <img src="https://cdn.mos.cms.futurecdn.net/8ToUvuPXxcD5ANh3D9Sr8L-1200-80.jpg" alt="Image 5">
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSZR9RoZV2VE3evUC3mhncGM9aNTzfSko6T27Vwfx7I7jEShMOeYyOf_YU&s=10" alt="Image 6">
  <img src="{{site.baseurl}}/images/PEE2 (1) (1).png" alt="Image 7">
  <img src="{{site.baseurl}}/images/fin2 (2).jpg" alt="Image 8">
  <img src="{{site.baseurl}}/images/about/trent_family.png" alt="Image 9">
  <img src="{{site.baseurl}}/images/about/claire.jpg" alt="Image 10">
  <img src="{{site.baseurl}}/images/about/grandkids.jpg" alt="Image 11">
  <img src="{{site.baseurl}}/images/f4576b792b248812ca370099de18d401-Photoroom.png" alt="Image 12">
</div>
