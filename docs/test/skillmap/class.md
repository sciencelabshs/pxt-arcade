# Miss Kiki's Class
* name: Miss Kiki's Class
* description: Create a fast-paced maze game by programming a student to move through the crowded halls to collect assignments without being interrupted by a teacher trying to give them more work!
* infoUrl: skillmap/educator-info/class-map-info
* backgroundurl: /static/skillmap/backgrounds/class-comp.png
* bannerurl: /static/skillmap/class/class.gif
* primarycolor: #ff93c4
* secondarycolor: #fdf60c
* tertiarycolor: #161112
* strokecolor: #ffffff
* highlightcolor: #ffffff
* completednodecolor: #3b3738

## class
* name: Miss Kiki's Class
* layout: manual

### class1
* name: Trapped in the Halls
* type: tutorial
* description: Add a student to the halls of the school, then keep an eye on them as they move around!
* url: /skillmap/class/class1
* tags: easy, sprites, tiles
* imageUrl: /static/skillmap/class/class1.gif
* next: class2
* position: 1 -1

### class2
* name: All the Assignments
* type: tutorial
* description: Write the code to help the student collect assignments to win the game.
* url: /skillmap/class/class2
* tags: easy, tiles, events
* imageUrl: /static/skillmap/class/class2.gif
* next: class3
* position: 2 -1

### class3
* name: Avoid the Teacher!
* type: tutorial
* description: Add teachers to try to slow you down on your way out the door!
* url: /skillmap/class/class3
* tags: easy, enemies, overlap, lives
* imageUrl: /static/skillmap/class/class3.gif
* next: class-finish
* position: 3 0


### class-finish
* kind: completion
* type: certificate
* url: /static/skillmap/certificates/class-cert.pdf
* imageUrl: /static/skillmap/certificates/class-cert.png
* position: 4 0
* actions:
    * map: [Try Space Explorer](/skillmap/space)
    * editor: [Mod this project](/)
* rewards:
    * certificate: /static/skillmap/certificates/class-cert.pdf
    * completion-badge: /static/badges/class-rockstar.png

