---
title: "What is Frontend Development?"
date: 3-2-2021
---
<h2><b>Intro</b></h2>
Frontend development is making an interactive piece of media that is created 
with codeing languges like HTML, CSS and Javascript. The reason why I think its
called "Frontend" development is because your working with the raw code the "front"
of the piece of media/data your creating.
<br/>
<h2><b>Refelction on Learning</b></h2>
An example of something that we've been working on that is Frontend development is our
<a href="https://011-Frontend-Development-Pinboard-Kataruse.dbcs.repl.co"><b>Pinboard project</b></a>.In this project we were tasked with making a pinboard 
and then making it our own with adding features and a different title to separate it from our peers 
pinboards. This entire project was Frontend development since we were working directly with the code 
using CSS, HTML and Javascript to create our board. I think the main things I learn thought this project is the
different javascript commands and what they do since a lot of my additions like comments and links mostly involed Javascript and
a little HTML. I wish I messed around more with the CSS since I am not a sure with the commands and stuff you can do to style
your code but overall I'am happy with my Pinboard. Some of the things I wish I could of added was the option to search for
multiple tags and to fix how the links appear on the post cards.
<br/>
<h2><b>Screenshots & Code snippets</b></h2>
![Creating a Post](https://i.ibb.co/cD45vSz/Newpost.png)
```HTML
  <label for="imgSrc">Image source</label>
          <input
            type="text"
            id="imgsrc"
            name="source"
            class="newCardInput"
            placeholder="Paste your image url here"
          />
          <label for="desc">Description</label>
          <input
            type="text"
            id="desc"
            name="text"
            class="newCardInput"
            placeholder="Enter a short description of your post"
            />
          <label for="tags">Tags</label>
          <input
            type="text"
            id="tags"
            name="tags"
            class="newCardInput"
            placeholder="Separate tags with a semicolon ( ; )"
          />
          <label for="link">Link</label>
          <input
             type="text"
             id="link"
             name="link"
             class="newLink"
             placeholder="Add a Link"
            />
```
<br/>
![Link Hiding](https://i.ibb.co/nCyV28R/Cards.png)
```Javascript
    var link = document.createElement("a")
    link.className = "link";
    if (data[i].link == "") {
      link.innerText = ""
    } else {
      link.innerText = "Link"
    }
    link.setAttribute('href',data[i].link);
    card.appendChild(link)
```
<br/>
<h2><b>Conclusion</b></h2>
Overall what I've learned about Frontend Development is that it invloes a lot of trial and error
with figuring out exactly what you need to acomplish a goal, i've also learned that when trying to
figure out whats wrong with a specific problem sometimes coming back to it later is better as you
might figure out the exact type of code you need for it to work properly later with a more clear head.
Moving forward I want to learn more about Javascript but mostly focus on HTML and CSS as I didn't do much
with those to languages as I did with Javascript.
