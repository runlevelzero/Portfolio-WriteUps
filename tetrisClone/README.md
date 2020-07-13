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

It's coming along nicely, I will work on this and improve this project more soon. You can monitor its progress [here](https://git.rubenruiz.org/runlevelzero/tetris)
