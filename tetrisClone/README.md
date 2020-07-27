During this pandemic and throughout my extra free time this Summer, I have gotten into Tetris. I used to play Tetris a fair little bit a couple of years ago every now and again, but I never really did anything special with the pieces. I mainly just got good enough to beat my sister whenever we would play together. This time, however, I want to actually get better at battle Tetris (think Tetris 99 and other competitive multiplayer Tetris games). Learning building techniques for modern Tetris and how to guarantee victory everytime I play players around my skill level. My current game of choice is [Puyo Puyo Tetris](https://en.wikipedia.org/wiki/Puyo_Puyo_Tetris) on the Switch. I play this version because it was the only way to play single player and local multiplayer Tetris on the Switch at that time. Now that I spend more of my free time near my computer and less time near my Switch, I have been looking for a Tetris game on the desktop pc. There is, of course, many versions of Tetris available for the pc on all operating systems; probably the most popular among them being [Nullpomino](https://github.com/nullpomino/nullpomino) and [JStris](https://jstris.jezevec10.com/). While they are perfectly fine implementations of modern Tetris, Nullpomino's main MacOS binary requires legacy JDK's on Catalina and doesn't seem to have gamepad support in the swing version (if it does, that's nice, but I am still going to make this), and JStris seems to have the same problem. So I wanted to make a clean looking Tetris game that has gamepad support that can be ran on a pc relatively fast.

### How?

I am writing this game in pure JavaScript in an Electron App. While electron apps aren't known to be particularly efficient space wise and memory wise, I just wanted to experiment with this and canvases as I really don't have much experience with this. This is how the app looked at this time:

|![](https://raw.githubusercontent.com/runlevelzero/Portfolio-WriteUps/master/tetrisClone/tetrisElectron.png)|
|-|
|The initial state of the electron app with the canvas unpainted|

Once I got the canvas drawn, I started getting ready to draw the grid for the pieces. In case you don't know, standard Tetris boards are 10x20 block grids. Here it is in the program.

|![](https://raw.githubusercontent.com/runlevelzero/Portfolio-WriteUps/master/tetrisClone/tetrisWithGrid.png)|
|-|
|the math for this took longer than I am willing to admit, yes it's easy and my implementation will break at much lower resolutions, I'll try to fix that later|

Once I got the board drawn, I was able to move onto how to actually draw the pieces (known as tetriminos) on the board. I wrote a function designed to be called every time I want the frame to be updated here is a GIF of it drawing a square in every grid.

|![](https://raw.githubusercontent.com/runlevelzero/Portfolio-WriteUps/master/tetrisClone/UpdateFrameFunction.gif)|
|-|
|my draw function takes too long I think, I'll optimize it soon|

I spent a lot of time thinking how I could optimize the drawing method, but by only redrawing the affected blocks, I ended up with some ghosting for some odd reason. so for now, I'll stick to complete redraws. I have an idea for how I can do only sectional redraws, but that will happen later, first let's get a piece drawn, I started simply by creating another javascript object to store the information about the piece like its position. Starting simply with a 1x1 piece, I was able to get it drawn, lookee

|![]()|
|-|
|A single 'mino' as it were|

But a piece isn't any good if you can't move it, so I added a key press listener to the body of the app so that way, any time you push a button while the window is in focus, it will control the piece, this will need to be modified later to allow for menus and typing, and adjustment, but for now you can play this game with the WASD keypads, with a pseudo hard-drop feature when you press the up (W) key

now that that was sorted out, the next biggest thing to do for this game was... wait for it...

### Gravity!!!

One of the biggest ways that Tetris becomes overly addictive is its subtle but sometimes brutal difficulty curve, where you can go from leisurely play to too fast to handle. I spent some time researching how gravity works in Tetris games, and since most are designed to be ran at around 30 to 60 frames per second each, their gravities are always a multiple of 6 or 3. Since I am loading a fram every 10 milliseconds form 100 refreshes a second, the gravity for my game will have to be slightly different. The initial rate for my game will be one block every 100 frames, but could ramp up into multiple blocks in how ever many frames I decide based on two variables, the time it takes for a block to move, and how far the block moves.

Now that gravity exists in some form, I think its time to introduce more blocks into the mix. Looking into how modern Tetris pieces rotate is the next step on this journey

You can monitor its progress [here](https://git.rubenruiz.org/runlevelzero/tetris)

