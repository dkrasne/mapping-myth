# Acquiring, adding, and selecting data

## Learning Objectives
In this tutorial, you will learn how to:
- Locate and download geographical data (geodata) appropriate for mapping the ancient Mediterranean.
- Add a custom basemap to your map.
- Add shapefiles and other types of geodata to your map as layers.
- Select and display only a subset of data in a layer.

## Tutorial
Since there is rarely any reason to replicate what someone else has already done well, one of the first steps to take when working with spatial data is to locate already-available data. A lot of high quality geodata has already been created specifically by and for scholars working with the ancient Mediterranean. However, it's not all in the same place.

Three sites to become familiar with are: [Pleiades](https://pleiades.stoa.org/), the [Ancient World Mapping Center (AWMC)](https://awmc.unc.edu/), and the [Digital Atlas of the Roman Empire (DARE)](https://imperium.ahlfeldt.se/).

If you ever need to search for other available geodata, you can search for the name of the location you're interested in plus one of the words "shapefile" or "geodata".

### Starting a new project

*N.B. The QGIS documentation includes [a comprehensive overview of the menus and ribbons](https://docs.qgis.org/latest/en/docs/user_manual/introduction/qgis_gui.html), including useful keyboard shortcuts for some of the most regularly-used commands.*

1. Open a new project in QGIS (![New Project icon](images/qgis_icons/mActionFileNew.png) or Project menu > New).

1. Save the project (Project menu > ![Save As icon](images/qgis_icons/mActionFileSaveAs.png) Save As...) with a name like `tutorial1.qgz`. While you can save the project anywhere you like on your computer, you'll want to be a bit choosier when it comes to your geodata files later on (more on this [below](#saving)). For now, I'd recommend creating a folder somewhere for all your GIS stuff, and creating another inside that for your tutorial projects.

### Adding a basemap

We want a background for our map so that we can see where our geographical features are located. (One doesn't always need a basemap, but usually it's helpful.) For the ancient Mediterranean, the two options are a basemap produced by [the Consortium of Ancient World Mappers (CAWM)](https://cawm.lib.uiowa.edu/index.html), which tries to accurately reconstruct the ancient coastline, and [a basemap produced by DARE](https://ancientworldonline.blogspot.com/2014/04/digital-atlas-of-roman-empire.html), which includes labels with many ancient Roman names. We will use the CAWM map.

1. There are two main methods for adding this and most other freely-available basemaps, but not all basemaps can be added by each method. Since the CAWM basemap can be added by *both* methods, I'm providing both options here so that you have the basic instructions for other basemaps that you may want to use.

    * **Option 1: Using WMTS**
    1. Click ![Data Source Manager icon](images/qgis_icons/mActionDataSourceManager.png) or under the 'Layer' menu, click on 'Data Source Manager'.
    1. Choose 'WMS/WMTS' in the lefthand menu, and click on 'New' to add a new layer.
    1. In the 'Name' field, write "CAWM basemap" (or anything else you might want to call it).
    1. In the URL field, put: https://cawm.lib.uiowa.edu/wmts
    1. Click 'OK'.
    1. Now click the 'Connect' button underneath the name of the new map.
    1. It should automatically switch to the 'Tilesets' tab, but if not, choose 'Tilesets' at the top of the window.
    1. Select the only layer listed (some maps will have multiple layers), and click 'Add' at the bottom of the window. The basemap will be added to your empty project.

    * **Option 2: Using XYZ**
    1. Click ![Data Source Manager icon](https://docs.qgis.org/latest/en/_images/mActionDataSourceManager.png) or under the 'Layer' menu, click on 'Data Source Manager'.
    1. Choose 'XYZ' in the lefthand menu, and click on 'New' to add a new layer.
    1. In the 'Name' field, write "CAWM basemap" (or anything else you might want to call it).
    1. In the URL field, put: http://cawm.lib.uiowa.edu/tiles/{z}/{x}/{y}.png (Note that you can tell if a basemap requires XYZ because it will have that `{z}/{x}/{y}` in the URL!)
    1. Untick 'Max. Zoom Level' (this isn't required, but it will help to keep the map from disappearing when you zoom way in; some XYZ services will tell you their minimum and maximum zoom levels, and you can fill those in).
    1. Click 'OK'.
    1. Click 'Add' at the bottom of the window. The basemap will be added to your empty project:

        <figure>

        ![loaded basemap](images/tutorial_1/add_basemap.png)
        
        <figcaption><b>The newly-loaded basemap.</b>
        </figcaption>
        </figure>

    Once you have gone through either process once, the connection is stored in QGIS; for future maps, you can simply double click on the layer in the Browser panel to add it.

1. **Save your project!** (![Save icon](images/qgis_icons/mActionFileSave.png) or Project menu > Save). Saving frequently is very important, as QGIS can sometimes crash. You don't want to lose lots of hard work!

1. Zoom into the area around Greece and the Mediterranean (you can double-click with the hand icon, or select the zoom magnifying class and single-click).


### Downloading and adding data

Pleiades is a good source for specific ancient world point locations; the AWMC is a good source for things like bodies of water or political regions that are best represented as lines or polygons. We will be adding data from both sources in this tutorial.

#### AWMC

1. From [the AWMC GIS Data page](https://awmc.unc.edu/gis-data/), click on 'AWMC Geodata Github Repository'. (You can also [go there directly](https://github.com/AWMC/geodata), but it's good to know how to find it.)

    If you think you'll want to use a lot of files from the repository, you can download the entire thing from the main page by clicking on the green 'Code' button and then selecting 'Download ZIP'. However, we'll only be working with a few files, which we will download individually.

1. Go to the 'Physical Data' folder.

1. We will be downloading **inland water**, so go to the 'inland_water' folder.

    There are two different versions of this file: a shapefile (in .zip format) and a GeoJSON file. We'll download both of them.

1. Click on the `inland-water-OSM.geojson` file. It should show you a map, although larger files will not do so.

1. Click on the download icon (![download icon](images/other_icons/download_20px.svg)) at the top of the page.

    <span id="saving">Depending on your browser and your setup, you may be prompted to save the file, or it may automatically save somewhere on your computer (e.g., a Downloads folder).</span> However, we don't want the file just anywhere: file locations are important, as is not needlessly replicating data all over your computer.
    
    The specific directory names and locations that I provide in the following instructions are not themselves required: what's important is to have your files in a tidy and logical structure that enables you to know their original sources and locate them easily on your computer.

1. Inside the GIS folder you created earlier on your computer, create another folder called **AWMC Data** (or another similar name). Save the file here, or move it here if it was automatically saved somewhere else.

1. Follow the same process with the other file (which will not show you a map when you click on it).

1. On your computer, open the .zip file to see its contents. It contains **multiple** files. A so-called "shapefile" is actually multiple files, and they need to stay together. (You don't need to extract the contents; QGIS can automatically read it.)

1. In your QGIS project, go to Layer menu > Add Layer > ![Add Vector Layer icon](images/qgis_icons/mActionAddOgrLayer.png) Add Vector Layer...

1. Make sure that 'File' is selected under Source Type and that 'Automatic' is selected in the drop-down Encoding menu.

1. Click the button with three dots at the far right of the Vector Dataset(s) field.

1. In the file selection window, navigate to the **AWMC Data** folder you created earlier. Select the geojson file and click Open (or double-click it).

1. Leave all the choices under Options as their default settings, and click Add. The data will be added to your map.

1. Follow the same process to add the shapefile .zip file to your map. (There won't be any options listed, this time.)

1. Close the Data Source Manager by clicking Close.

    <figure>

    ![inland water added to map](images/tutorial_1/add_open_water.png)

    <figcaption>
    <b>Inland water added.</b>
    </figcaption>
    </figure>

1. If the Layers panel is not open in QGIS, go to View menu > Panels and tick the 'Layers Panel' box.

    The two inland water layers should be listed above the basemap in your Layers panel; if not, drag them above the basemap in the Layers panel. (If you're having trouble dragging, you can also right-click the layer and choose 'Move to Top'.)

1. In the Layers panel, untick the box for the top layer. Notice that the layer beneath it, which is now revealed, appears to be identical except for the color &ndash; QGIS assigns colors randomly when it imports most vector files. (You'll learn how to change the colors in a future tutorial.)

    There are minor differences between these two files (primarily the number of significant digits included in some attributes), but to all extents and purposes, these two files are the same.

    Since GeoJSON is the more modern and flexible format, that's the one we'll use.

1. Delete the shapefile (it's the one with .shp at the end of its name in the Layers panel): select that layer in the Layers panel and click ![Remove Layer icon](images/qgis_icons/mActionRemoveLayer.png) at the top of the Layers panel (you can also right-click the layer to open the context menu, and choose Remove Layer).

1. On the AWMC GitHub page, go back to the main directory and download 'Physical Shapefiles Apr 2024.zip' following the same process as before.

1. Add the file to your map following the earlier instructions. Notice that this time QGIS prompts you to select which layers you want &ndash; this file contains *multiple* shapefiles. Select **only** the two river layers: one is called `river polygons/rivers_polygons_final` and the other is called `rivers/awmc-osm-rivers`.

    <figure>

    ![Rivers added to map](images/tutorial_1/add_rivers.png)

    <figcaption>
    <b>River lines and polygons added.</b>
    </figcaption>
    </figure>


#### Pleiades

For Pleiades, there are two methods for acquiring data: one is useful if you only want a few locations, and the other is useful if you want a lot of locations. We'll try both.

1. Go to the main Pleiades website at https://pleiades.stoa.org/.

    ##### <u>Individual sites</u>

1. First we want to find information for Delphi, the oracular center of the Greek world. Type 'Delphi' into the search box and scroll down to the result that says "Delphi = 540726". Click on the hyperlinked number.

    The number is this location's **Pleiades ID number (PID)**, which serves as a unique identifier for that particular place, allowing us to disambiguate ancient Greek Delphi from, say, modern-day [Delphi, Indiana](https://en.wikipedia.org/wiki/Delphi,_Indiana).

1. Click on the URL in the address bar and, at the end of the address, after the number, add `/json`. Hit return.

    <figure>

    ![Delphi GeoJSON representation](images/tutorial_1/delphi_json.png)

    <figcaption>
    <b>Delphi GeoJSON representation.</b>
    </figcaption>
    </figure>


    The data that you are now looking at is the GeoJSON representation of the point marking the Temple of Apollo at Delphi, which was marked as a blue and red crosshairs on the previous page. 

1. In the **GIS** folder on your computer, create a new **Pleiades Data** folder, and inside that folder create another **Individual sites** folder. (Again, you can use different names if you prefer.) Save the Delphi JSON file to this folder as 'delphi_540726.json'.

1. Add the Delphi file to your map following the same process as before. There should now be a round dot just north of the Greek Peloponnese:

    <figure>

    ![Delphi point added to map](images/tutorial_1/add_delphi.png)

    <figcaption>
    <b>Delphi point added.</b>
    </figcaption>
    </figure>

    ##### <u>Full dataset</u>

1. From any Pleiades page (the main site or the Delphi page), click on 'Downloads' in the top menu bar. Scroll down to "Pleiades Data for GIS and General Use (CSV)" and click on it.

1. Read this page up through the 'Files' section.

1. Download 'pleiades_gis_data.zip' anywhere you like.

1. Make a new **GIS data** folder inside your **Pleiades Data** folder.

1. Inside the .zip file you downloaded is a 'data' folder, and inside that is a 'gis' folder. Transfer/unzip the contents of that inner 'gis' folder into your new **Pleiades data > GIS data** folder.

1. Follow the instructions under 'Quick Start' on the '*Pleiades* Data for GIS' page to add the points to your map. (When it says to load `places.csv` as delimited text, it means to choose ![delimited text icon](images/qgis_icons/mActionAddDelimitedTextLayer.png) 'Add Delimited Text Layer' under the QGIS Layer menu, or to select Delimited Text in the Data Source Manager.)

    You should now have a map full of points!

    <figure>

    ![Pleiades points added to map](images/tutorial_1/add_pleiades.png)

    <figcaption>
    <b>Pleiades data added.</b>
    </figcaption>
    </figure>

    ##### <u>Exploring the data</u>

1. Delete the individual Delphi point layer from your map; that point is contained within this larger dataset.

1. Make sure the 'places' layer is selected, then click on ![Open Attribute Table icon](images/qgis_icons/mActionOpenTable.png), or go to Layer menu > Open Attribute Table, or right-click on the 'places' layer in your layers panel and select 'Open Attribute Table'.

    <figure>

    ![Pleiades places attribute table](images/tutorial_1/pleiades_places_attribute_table.png)

    <figcaption>
    <b>Pleiades places attribute table.</b>
    </figcaption>
    </figure>

    Each of the rows contains information about one point in the dataset; each column in the row contains a piece of information about that point, such as a description of the site, its name, its latitude or longitude, or its Pleiades ID (PID) value.

1. Close the attribute table.

### Joining Data

You may have noticed that the Pleiades GIS Data page talks about using joins to attach other files and get more information about the points. As discussed above, each Pleiades place has a unique numerical ID, its PID. Each of the files in the GIS data package contains additional information about many of the points, referenced by that PID. We therefore can use that value to connect the files to each other and thereby enrich our points with additional information.

- add Pleiades data; join with name data and place type data CSVs; filter to show just religious(?) spots (temple, sanctuary, shrine, tomb(?), __); add labels of Latin(?) names
