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

 ### How to generate BOM(Bill of Materials) from EagleCAD?

 1. To generate the `BOM` file make sure you are in EAGLE Schematic Editor.

    Go to `File`>>`Export`>>`BOM`
 ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/afbc7601-ac45-468a-8a3b-81065dccd258)


 2. This will open up new window which shows the BOM configurations.

    Check the `Values` and the `CSV` option.

    Uncheck `List attributes` and save the file in desired location by clicking `Save` option.

    ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/8656bcbb-9c33-4d53-924c-8b0e209be8bd)


 3. The saved file needs to be edited before uploading to Lion Circuits. Kindly import the saved csv file into any spreadsheet editor. In this example we are using      `Google Spreadsheets`.
 
    Go to `File` >> `Import`. In the newly opened window select upload and select the recently created `Bom.csv` file.

    ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/973c3aa7-b5b8-4d86-9325-cdca2d872fba)


 4. Now you can configure how to import file. You need to put in the correct separator which in our case is semicolon `' ; '` and click import data.

    ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/9b4c681b-bee9-4d85-8bcb-34fcf36c6753)

5. Now you need to adjust the file by changing column names, addition/deletion of columns so that it matches what is shown below. This is the configuration of JLCPCB manufacturing 

    ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/fb8d5258-2ecb-4ba1-b3f2-f782bc460cba)

   As per the above screenshot:
   - `Quantity` - Count of particular component required per PCB
   - `Designators` - This is the identifier for the component which will also be printed on the PCB
   - `Footprint` - It defines the footprint of the component as per the design
   - `Comment`- This column provides important details of the component like tolerance, wattage, maximum voltage and other information.
   - `LCSC Part #` - This is the reference part number which can be used to order the components online.
   - `Description` - Any special instructions like soldering profile
   - `Value` - Part value

Note: Leave the `LCSC Part #` blank when making the BOM. This is to be filled by referring the `JLCPCB website` when ordering for the boards.

6. Next, download the sheet in the format of `Comma Seperated Values (.csv)` into your system folder by heading to `File` >> `Download` >> `Comma Seperated Values (.csv)`. This is your final BOM file that is to be given for assembly of the board.

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/59214568-16fb-402b-a54b-edf29533feea)

### How to generate Pick and Place (Centroid) File from EagleCAD?

1. To generate the pick and place file make sure you are in EAGLE Board editor.

   Go to `File` >> `Export` >> `Mount SMD`

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/2f90ecf0-dfb6-455e-9311-a5714132a0da)

2. This will prompt twice to select location to generate pick and place files separately for top and bottom.

   The first prompt is for the top assembly file, save this as `top.csv`.

   The second prompt is for bottom assembly file, save this as `bottom.csv`

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/891e4a21-c7d7-4bbd-a681-a92fef1497aa)

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/8e49ccf7-31f0-4435-a287-8368b8124d39)

3. The file generated from EAGLE will not be in the format accepted by JLCPCB.

   Start with a `New Spreadsheet`, go to `File`>>`Import`. In the newly opened window select upload and select the generated pick and place file.

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/df7590df-02d0-42ea-a22e-8bf6ae85ff88)

4. Once it is imported you will notice that columns are not properly alligned.

   To fix this select data and then go to `Data`>>`Data Cleanup`>>`Trim whitespace`

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/b324d519-4c43-4e10-8277-98ec2318f979)

5. Next, select the first column, and then go to `Data`>> `Split text to columns`

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/2308430e-580c-4cff-8f02-3ccf3480e084)

   Then, an option pops up to select the `Seperator` type. The default will be selected as `Automatically`. This is to be changed.

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/31703d3d-770f-4269-a608-555cbe2aeea5)

   Change the `Seperator` to `Space`

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/f6ac407f-3680-4272-85a9-74aa2e547493)

6. Now the data is separated into columns and column headers need to be added.

   First column generated by Eagle is Designator column, next is Mid X, Mid Y , Layer and Rotation. Remaining cloumns can be deleted . The final file       required after all the changes should look like this.

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/dc9517fe-fb6b-459f-932e-77caf77501cb)

8. After completing the editing kindly export it from Google Spreadsheets.

   Go to `File`>>`Download`>> `Comma-separated values(.csv)`

   ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/693b1159-6edb-4816-8986-3a56348980b9)

9. Now open the downloaded in `Microsoft Excel`. It is a good practice to add units of the placement dimensions and values. In order to add units to all the values:
    - Select the cells where the units are to be added. Then right-click and select `Format cells`

      ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/b928152a-6ac0-4f91-83da-98af58e795ec)
      
    - Under `Number` tab, select `Custom` Category. In the `Type:` box, type in `#.##"mm"`. This saves the accurate values of upto 2 decimal points.
      Then click `OK`

      ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/dd69bb4e-e730-4a88-a260-b46ce4a6e6da)
      
    - Now the units are added to all the dimensional and positional values

      ![image](https://github.com/FracktalWorks/FWEagleLibrary/assets/80109965/2f4d1a8e-13f1-485a-a24e-975292f8e4d9)



    





