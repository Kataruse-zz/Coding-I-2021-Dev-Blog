---
title: "Drone Progression Update 1"
Date: 2021-03-19
---

<h2><b>Introduction</b></h2>
So far this week of working on our drones has been really succesful. We are at a point where we can control the drone easily and create custom commands for the drone to preform and could most likely run the course.

![Image of Mover](/assets/MoverTool.png)

<h2><b>Process</b></h2>
*Monday
--*We spent the day making a copy of our frontend github tool.
*Tuesday
--*Finished up the "Mover" and the drone can take commands from it.
*Wednsday
--*Allowed the program to detect errors to run the input again and added a fast emergency command.
*Thursday
--*We tested the "Mover" program and learned how to use it, we also gathered some measurments.
*Friday
--*I spent the class hours working on this blog post.

<h2><b>Successes</b></h2>
Some of the things we added to our "Mover" include
*Displayed Title
*Command Inputs
*Custom Commands
*Error Detector

```javascript
utils.displayTitle();
  while (true) {
    let userCommand
    while (errormsg !== "error") {
      userCommand = await prompt.askForCommand();
      server.send(Buffer.from(userCommand.commandbox), "8889", "192.168.10.1");
      if (userCommand.commandbox == "exit") {
        process.exit();
      } else if (userCommand.commandbox == "e") {
        server.send(Buffer.from("emergency"), "8889", "192.168.10.1");
      } else if (userCommand.commandbox == "8") {
        server.send(Buffer.from("emergency"), "8889", "192.168.10.1");
      }

    }
```
![name]({{site.url}}/assets/[filename])

<h2><b>Failures</b></h2>
*Moving the drone with key controls
*Display Drone Battery in the program

<h2><b>What We Need To Add</b></h2>
We need to add more custom commands to make the course easier to run and we need to add the battery detection so we'll know our drones battery level.

<h2><b>Things We Need To Fix</b></h2>
we need to fix our display title to only display once and fix the error detector because it doesn't really work correctly. 