# FWEagleLibrary
Eagle Library for FW boards and electronics

 ### ERC/DRC check
 - ERC check to done on Schimatic to check for errors.
 - DRC check is done by loading the DRC file(.dru extension), is done on the PCB board to check for airwires, overlaps, clearence etc. 

 ### Component and Naming
 - All the connectors should preferably have a same orientaion.
 - On the daughter board it should stay clear of high rise components like big capacitors.
 - The names and value for the connectors and components  are to be added to the silkscreen top by including tplace, tOrigin, TName, Tvalue layers during the cam process
 - All test points should be named.
 - The FFC cable orintation should be determined and the FFC connectors should be oriented correctly

### Track Width and Via.

- Track width for between components should be as per current requirements.

- The standard we follow is :
    - 24 mils for all signals and 24v and ground.
    - 16 mils to connect signals to the test points.
    - 100 mils for the H+ and H- ( which are extruder heater pins).
    - The 100 mils tracks should have 3 vias.

### Board Diamension 

- The daughter board diamensions should match that of the motherboard. For which use a .dxf file of the motherboard to get the diamension and position of the board.

- the diamension of the chassis board and the carrage board should be collected from the mechanical team.

- The position and diameter of the drill holes must be verified.


 ### Keep Orfans
 
 While making polygon/copper pour for any GND signal Keep orphan option must be enabled