# Pile of Sticks
### @explicitHints true


## {Intro @showdialog}

Your code from the last activity is already in the workspace.

Let's add some code that allows the player to win or lose.


![Time is ticking](/static/skillmap/sparks/sparks2.gif "Let's add win & loss conditions." )




## {2. Play Your Game}


**Play the clicker game!**

Press the (A) button or **space bar** and watch the score go up!




~hint My game doesn't work ⚠️

---

If your code isn't working and you can't figure out why, click
<br/>"Replace my code"<br/>
to replace the blocks in your workspace with new starter code.

hint~





## {3. Win Some}

**Add a score event.**

- :id card: From the ``||info:Info||`` category, drag<br/>
``||info:on score [30]||``<br/>
into an **empty area** of the workspace.



#### ~ tutorialhint

```blocks
info.onScore(30, function () {})
```



## {4. Game Over}

**Win the game when the score reaches 30.**

- :circle: From the ``||game:Game||`` category, drag<br/>
``||game:game over <WIN>||``<br/>
into the **empty** <br/>
``||info(noclick):on score [30]||`` container.



#### ~ tutorialhint

```blocks
info.onScore(30, function () {
    game.gameOver(true)
})
```






## {5. Check Your Game!}


- :binoculars: Try your project in the game window.

Press the (A) button as quickly as possible and you should win the game when you score gets to 30.




## {6. Counting the Seconds}

Right now, the winning score will always be 30.  Let's change the final score to the amount of time it took to win the game, then celebrate the "lowest" score.

- :id card: From the ``||info:Info||`` category, drag<br/>
``||info:set score to [0]||``<br/>
into the **top of** the<br/>
``||info(noclick):on score [30]||`` container that's already in the workspace.

- :circle: From the ``||game:Game||`` category, drag<br/>
``||game:time since start (tenths)||``<br/>
to replace **0** inside the <br/>
``||info(noclick):set score to [0]||`` block.



#### ~ tutorialhint

```blocks
info.onScore(30, function () {
    //@highlight
    info.setScore(game.timeSinceStartSec())
    game.gameOver(true)
})
```




## {7. Lowest Wins}


- :circle: From the ``||game:Game||`` category, drag<br/>
``||game:use [high score] as best score||``<br/>
into the **top of** the<br/>
``||info(noclick):on score [30]||`` container that's already in the workspace.

- :mouse pointer: Click ``||game:high score||`` and choose
``||game: low score||`` from the dropdown menu.



#### ~ tutorialhint

```blocks
info.onScore(30, function () {
    //@highlight
    game.setGameOverScoringType(game.ScoringType.LowScore)
    info.setScore(game.timeSinceStartSec())
    game.gameOver(true)
})
```




## {8. Lose Some}


**Time for a challenge!** <br/>
❤️‍🔥 ❤️‍🔥 ❤️‍🔥

It's too easy to reach 30. Let's subtract a point every second to add a twist.


- :circle: From the ``||game:Game||`` category, drag<br/>
``||game: on game update every [500] ms||``<br/>
into **an empty area** of the workspace.

- :mouse pointer: Change **500** ms to **1000** ms (which is also 1 second.)



#### ~ tutorialhint

```blocks
game.onUpdateInterval(1000, function () { })
```


## {9. Lose Some}


- :id card: From the ``||info:Info||`` category, drag<br/>
``||info: change score by [1]||``<br/>
into **the empty**<br/>
``||game(noclick): on game update every [1000] ms||``<br/>
container already in the workspace.

- :mouse pointer: Change **1** to **-1** to remove a point.



#### ~ tutorialhint

```blocks
game.onUpdateInterval(1000, function () {
//@highlight
        info.changeScoreBy(-1)
})
```





## {10. Check Your Game!}


- :binoculars: Try your project in the game window.

Press the (A) button as quickly as possible and see if you can hit 30 points before too many points are taken away.





## {11. Enough is Enough}

Let's add a way to lose the game when points fall too far below zero.

🕰️ 🕰️ 🕰️

- :id card: From the ``||info:Info||`` category, drag<br/>
``||info:on score [30]||``<br/>
into an **empty area** of the workspace.

- :mouse pointer: Click inside the empty container and change **30** to **-5**.


#### ~ tutorialhint

```blocks
info.onScore(-5, function () { })
```




## {12. Enough is Enough}



- :circle: From the ``||game:Game||`` category, drag<br/>
``||game:game over <WIN>||``<br/>
into the **empty** <br/>
``||info(noclick):on score [-5]||`` container.

- :mouse pointer: Click **`<WIN`>** and change it to **`<LOSE`>**.



#### ~ tutorialhint

```blocks
info.onScore(-5, function () {
    //@highlight
    game.gameOver(false)
})
```






## {13. Check Your Game!}


- :binoculars: Take a look at the game window

Don't touch any buttons or keys...you should lose the game after five seconds.



## {14. Play again}


- :binoculars: Reset your game and play again!

Click the (A) button as fast as you can.  Is the game any harder to win?

💡 _Don't worry if your game is still too easy. In the next tutorial, we'll add more
levels, which will make the game much harder!_




## {9. Finale}

**👨🏽‍🚒 You're FIRE 👨🏽‍🚒**

What a great game you've got there!


~hint How do I share my game?💡

---

**Want to share your game?**

Click "Done" to get back out to the skillmap, then look in the lower-right corner for the share button.

![Share your card](/static/skillmap/sparks/share.gif )

hint~


When you're ready, click **Done** to return to the skillmap so you can
add levels to your game!


```blockconfig.global
info.onScore(30, function () {})
game.gameOver(true)
let kindling = sprites.create(img`.`, SpriteKind.Player)
kindling.setPosition(70, 80)
kindling.startEffect(effects.fire)

info.onScore(30, function () { })
```

```template

controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
        info.changeScoreBy(1)
        kindling.startEffect(effects.fire, 25)
})

let kindling: Sprite = null
scene.setBackgroundImage(sparks.background)
kindling = sprites.create(sparks.pile1, SpriteKind.Player)
kindling.setPosition(70, 80)
```

```ghost
info.onScore(30, function () {
    game.gameOver(true)
})

game.onUpdateInterval(1000, function () {
    if (inCutscene == false) {
        info.changeScoreBy(currentLevel * -1)
    }
})
```



```package
arcade-carnival=github:microsoft/arcade-carnival
arcade-storytelling=github:microsoft/arcade-storytelling
arcade-text=github:microsoft/arcade-text
sparks=github:kiki-lee/sparks#v0.0.5

```



```customts
namespace game {
    /**
     * This is a reporter block that returns
     * the number of seconds since the game started
     */
    //% block="time since start (tenths) "
    export function timeSinceStartSec(): number {
        return game.runtime()/100;
    }
}
```