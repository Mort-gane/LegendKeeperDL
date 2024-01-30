# LegendKeeperDL
Just a tool do dl your uploaded LK pictures

1. Install Node.js with npm on your computer
2. Download the tool
3. Install the packages needed with npm install
4. Run the tool with npm run dev (never tested to build it, thx bit i'm lazy)
5. Go to http://localhost:5173/
6. Open a second tab with your legend keeper project
7. Open the inspector on your legend keeper project and track down your requests in your logs - you are searching for the urls of the tiles that legend keeper charge to render the map
8. Track down and copy the url of the southernmost eastermost tile of your map
9. For me it look like that : https://tiles.legendkeeper.com/processed/clfmd6ib00022a6en4yzpzuy/tiles/6/63/29.png
10. Copy that url and click on CHARGE TILES, it can take a bit of time to download every tile (max 10 sec)
11. You should see your map, its a preview so you cant really do anything with it yet, but mind you its just to allow you to know if you messed up somewhere
12. If the full map is to your liking, and you didnt mess up along the way, click on MAKE IT A CANVA, it'll again take a bit of time
13. Now a pop will tell you when its ready, close it
14. You just have to right click on the picture and save it. TADA ! (if you are a barbarian like me the picture is 200mo of size and you'll have to WAIT A BIT AGAIN)
