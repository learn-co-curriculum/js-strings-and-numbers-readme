# Modifying The DOM

You have now successfully grabbed elements from the DOM. Congrats! That's a big deal, and the first step to something great. The next step is a bit more fun. Let's _modify_ the DOM. Through DOM modification we will learn a bit about the difference between Strings and Numbers as well as learn some more on variables. Let's get started!

<iframe height='265' scrolling='no' title='OpwrqM' src='//codepen.io/joemburgess/embed/OpwrqM/?height=265&theme-id=0&default-tab=html,result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/joemburgess/pen/OpwrqM/'>OpwrqM</a> by Joe Burgess (<a href='http://codepen.io/joemburgess'>@joemburgess</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

Take a look at the code above. It's fairly short. We have a header, two "labels", and two pieces of data. One of them is a name: "Joe Burgess" and one is a height in inches "74". Let's start playing with this to see if we can modify the name and height.

**Note**: If you are having difficulty accessing the code pen displayed above, 
open a second browser tab and navigate to [the code pen](https://codepen.io/joemburgess/pen/OpwrqM) (https://codepen.io/joemburgess/pen/OpwrqM) before following along.

### Selecting Elements
Let's do a quick review of how to select elements on the screen. First, right click and choose inspect. Then select "Console". Finally, remember to change your console to the CodePen by selecting the drop down that says `top` and changing it to "CodePen Preview".

![Codepen](https://web-dev-readme-photos.s3.amazonaws.com/js/select-code-pen.gif)

OK, now click the element inspector icon (![icon](https://web-dev-readme-photos.s3.amazonaws.com/js/elementinspector-icon.png)) and select "Joe Burgess". How can we use Javascript to select it? The `id` looks pretty promising. This is an `id` so we need to begin our selector with the `#` character. Therefore, the command to select this element is `document.querySelector('#name')`. Write that into your console, press Enter and you should get the "Joe Burgess" element.

I'll leave the next one up to you. Go through the same process and then come out on the other end with the appropriate `document.querySelector()` command that retrieves the height.

Now let's write the JS code in the CodePen to save these selectors into a variable. Variables are just like they were in algebra class. They are simply names for any sort of data. You can re-set them to something else as much as you'd like. In this case, click the JS tab of the CodePen and then type:

```
var nameSelector = document.querySelector('#name')
```

Great! You just set the variables `nameSelector` to be `document.querySelector('#name')`. Now, whenever you are going to use `document.querySelector('#name')`, you can use `nameSelector` instead. Muuuuuch easier. Go ahead and make another variable called `heightSelector` for the selector for the height element.

### Changing Elements

We now have two variables: `nameSelector` and `heightSelector` that reference our name and height. All of this you've seen before. Unless you are named Joe Burgess and are 74 inches high, I doubt the information presented in the CodePen is correct. Let's make it right!

If you re-open your Console, change the dropdown to CodePen, type in `nameSelector` and press Enter you'll get the "Joe Burgess" element again. All selectors have an additional feature called `innerHTML`. Let's find out what our `nameSelector`'s `innerHTML` is by typing in the console `nameSelector.innerHTML`. You should immediately see just the name "Joe Burgess". To re-set this name we are going to think back to something we've done before. We can change the value assigned to the `nameSelector` variable the same way we originally set it: using the `=`. On the left of the equal sign will be the thing we are changing -- in this case, `nameSelector`. On the right is what we are changing it to. So `nameSelector.innerHTML = "Avi Flombaum"`. You'll notice the name changes. Congratulations.

![whats-my-name](https://web-dev-readme-photos.s3.amazonaws.com/js/whats-my-name.gif)

Finally, we can modify the height using our `heightSelector` variable. You probably guessed what we need to do here. In the console type: `heightSelector.innerHTML = "70"`. Thankfully height just changed. Go ahead and modify the items in the JS tab to be your actual name and height.

### Why The Quotes?

Those quotes around `Avi Flombaum` and `70` are really important. This means that those two phrases are a String. The term String comes from the fact that both are a string of characters. The quotes are important because without the quotes Javascript will think the words `Avi Flombaum` are some sort of Javascript command. There is not a Javascript command called `Avi Flombaum` so you'll get an error. Let's see what that error would be. Go ahead and open the console back up, switch to
the CodePen in the drop down and then type `nameSelector.innerHTML = Avi Flombaum`. You'll get an error that says `Uncaught SyntaxError: Unexpected identifier`. This is because Javascript couldn't find anything within itself called `Avi Flombaum`. We have to tell Javscript, that this is just some letters and to not really worry about it. That's why we go with `"Avi Flombaum"`. 

### Quotes and Numbers

Let's say you just put some shoes on with a 2-inch heel. You are now 2 inches taller! You can update the height directly by just doing this in the JS tab of the CodePen `heightSelector.innerHTML = "72"`. That will work if your previous height was 70 inches. What if your height was something else? If you wanted this to be _dynamic_ you could just say "increase the current height by two inches". In code this would look something like this:

```
heightSelector.innerHTML = heightSelector.innerHTML + 2
```

On the right of the `=` we grab the current value of the height (`heightSelector.innerHTML`) and then add `2` to it. If you write that code in the JS tab of the CodePen, you'll get `702`. Woah! That's not right. It just appended the `2` to the end of the `70`. That's because we did the `"` around our `70`. This makes our `70` a String. When you add something to a String, it just appends. This is useful for most strings. For example, if your name was just `"Joe"` and you wanted to add a
last name you could do `"Joe" + " Burgess"` and it would return `"Joe Burgess"`. In this case though, we need to tell Javascript to think of the `70` as a number. 

We need to have Javascript convert the string `"70"` into a number. The way to do that is simply to wrap your string value in a new thing called `parseInt()`. So if we want the number representation of the height, we just do `parseInt(heightSelector.innerHTML)`. To show you the difference, open up your console, select the CodePen from the drop down and then type `heightSelector.innerHTML`. You'll get `"70"`. Notice the quotes? That means this is a String. If we now type this: `parseInt(heightSelector.innerHTML)`, you'll still get `70`
but notice the lack of quotes. This means that it's a number.

So to finalize everything let's modify our addition line in the JS tab of the CodePen to be:

```
heightSelector.innerHTML = parseInt(heightSelector.innerHTML) + 2
```

Now that should work how you planned. Go ahead and play around with setting the initial height in the HTML tab to different values. You'll see it is now dynamic. No matter what you put in as the initial setting, we add 2 to it.

<p class='util--hide'>View <a href='https://learn.co/lessons/js-strings-and-numbers-readme'>Strings and Numbers</a> on Learn.co and start learning to code for free.</p>
