# Constructing Laser Cut Millifluidics

## Page under construction

## Protocol

### Control Layer (1/4" acrylic)

Cut outlines first

* Hairline outline
* 3 copies

Keep full stock in place + outline on computer

* Acts as a frame for the device
* Remove board from stock with tweezers

Add adhesive

Put adhesive covered outline back in place on stock

On the computer

* Align control vector cuts (ports) to the outlines
* Delete outlines
* Print (3 copies for 1/4")

Keep board in place

Rastering control channel

* Undo deletion of outline, delete previous vector cuts
* Align raster outline to old outline + delete outline
* Load control channel 2 in advanced settings
* 1200 dpi
* 1 copy => print

Remove board + stock from laser cutter

&#x20;

### Flow Layer (1/8" acrylic)

Cut adhesive sheet

* Copy/paste in design with scooped out region around bridge
* Cut adhesive out first
* This way we don't have to move the acrylic stock later to put adhesive on the laser cutter
* Check adhesive stickiness
*
  * Remove corner from adhesive
  * One side will stay attached to adhesive, one will remove cleanly
* Put adhesive sheet on laser cutter, with side that easily removes down
* Focus to adhesive
* Vector cut Full speed + 80 - 90% power

Cutting acrylic

* Delete scoops, we just want the outlines
* Print vector cut for outline
* Refocus laser cutter to 1/8th inch + cut

Plasma clean acrylic

Put adhesive on

Rastering acrylic

* Place device back in stock on laser cutter
* Copy/paste raster of flow route
* Remove outline
* Raster cut
* While rastering, start tapping control board

&#x20;

### Assembly

Tap control board

* 2 turns one way, little turn the other way
* Use a countersink to remove burrs around the holes
*
  * A couple of turns
  * Both sides of board
  * Allows silicone to sit flush + barbs to insert easily
* Blow out small bits of acrylic from threading using air before plasma treating

Remove backing from all acrylic (helps with alignment later)

&#x20;

Silicone

* Sam from Densmore lab bought a big roll
* Some in drawer under cutting station
* Cut larger size than device
* Peal one side of silicone
* Plasma treat 30 seconds

Apply silicone to control board

* Align and press onto control board
* Take off plastic from other side of silicone
* Wrap in paper towel
* Put between aluminum plates in vice
* Turn tight + one small more turn
* Wait 10 minutes

Punch holes in silicone

* Use biopsy punch (green on shelf above 3D printers) to make holes silicone for flow
* Don't need to do the control
* Put pressure and turn

Clean silicone + adhere to flow layer

* Use piece of packing tape to remove dust
* Plasma clean silicone 30 seconds
* Align flow and control
*
  * Take special care to align the valves
  * Easier to align flow layer on top
* Clamp full device in paper towel for 10 minutes
*
  * Avoid over tightening - this can overstretch the silicone layer

Put loctite on barbs + screw in to board

* Barbs are in Dan's drawer



Subprotocols

### Warnings

Don't run ethanol through acrylic!!! Will eat away at it

Instead use bleach and then water

### &#x20;

### Design

Eagle

* Using Eagle to drag and drop elements + make layers
* Problem with Eagle
*
  * Only outputs dxf
  * We then have to trace as a png in illustrator
  * This creates a double line
  * Less accurate + goes over each area twice

Zach defines width of the pumps, but doesn't worry about depth

&#x20;

Width of channel / valves

* Too small = hard to align + valves will no longer stay closed
* Larger is more robust

&#x20;

Barb spacing

* Want enough space between each barb for tool
* Far enough from the edge
*
  * Prevent leaking from the port

&#x20;

### Laser Cutter

Different colors of line produce different depth / intensity of cut

* Use black for everything

Make all lines hairline outline

* Otherwise it won't cut!

Open up a new page

* Paste whatever you're cutting into this
* This will be the correct size of bed

#### Printing

USB Bullshit

* Open up printers / devices
* Have to reconnect USB multiple times for it to be recognized

&#x20;

1. Open up print
2. Select correct printer you figured out
3. Load the correct settings
4. Set the correct copy number
5.
   1. For millifluidics this is 2 for vector cutting (we have the double line problem)
   2. 1 for raster probably
6. Press print

#### On the Laser Cutter

Make sure it's on / connected

Focus first using metal thing attached to laser

Run the job with lid open to double check it's doing what you hope

Run the job

&#x20;

### Plasma Cleaning

Plasma treat surfaces (except adhesive)

* Take off one side of acrylic backing
* Vacuum knob arrow left
* Metal valve tight, then quarter turn loose
* Pump on + power on to remove air 1 minute
* Then switch on upper right knob to high
*
  * Acrylic = 1 minute treatment
  * Silicone = 30 seconds treatment
* Turn off pump and power
* Slowly open black knob and let vacuum fill

&#x20;

### Adhesive

Adhesive is in a box above 3D printers

Cut adhesive to larger size than acrylic

* Remove adhesive backing and place face up on surface
* Remove acrylic from plasma cleaner and firmly press clean side onto adhesive
* Squeegee the bubbles out as much as you can (and away from where the channels will be)
* Cut excess adhesive off with razor blade
