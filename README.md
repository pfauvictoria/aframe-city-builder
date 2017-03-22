# aframe-city-builder
A-Frame project demonstrating touch controls for building a VR city scene.

## Demo
<strong><a href="https://kfarr.github.io/aframe-city-builder">If you have an HTC Vive or Oculus Rift with accompanying controllers, click here to try it out now!</a></strong>

## Screenshots
<img src="./assets/images/screenshots.gif" />
* https://raw.githubusercontent.com/kfarr/aframe-city-builder/master/assets/images/screenshot1.png
* https://raw.githubusercontent.com/kfarr/aframe-city-builder/master/assets/images/screenshot2.png
* https://raw.githubusercontent.com/kfarr/aframe-city-builder/master/assets/images/screenshot3.png
* https://raw.githubusercontent.com/kfarr/aframe-city-builder/master/assets/images/screenshot4.png

## Feature Highlights
- Place voxel objects in a fun virtual city of your creation
- Navigate available voxel objects with a scrolling menu interface in VR
- Place base plates for streets, grass, parks and residential lots that snap to a simple grid layout
- Save and load your city to/from JSON format
- Support for Oculus Touch and HTC Vive Controllers (VR headset and controllers required)
- Convenience utilities in /utils for creating new object JSON groups for aspiring city voxel artists

## Changelog
- See history of newly added features here https://github.com/kfarr/aframe-city-builder/blob/master/CHANGELOG.md

## How do I add new objects to City Builder?
City Builder is only as cool as the objects you can place! So let's add more! (Some day I'd love to have a sketchfab-like fancy cloud interface for uploading objects, an in-app voxel editor and more, but for now you'll have to do a bunch of manual work.)

### Step-By-Step Guide
(1) Make the object - I suggest using MagicaVoxel: https://ephtracy.github.io/

(2) Come up with a filename - Each object has unique filename according to this suggested naming convention: "creator_group_object". For example "kfarr_bases_valencia" or "mmmm_obj_candle".

(3) Export to OBJ and take preview image
For each object, there are multiple files using the same filename but with different extensions to represent their function in the application:
* .jpg - A preview image used to represent the object in a menu interface, stored here: /assets/preview/. Should be 1:1 aspect ratio, suggested 256 x 256 dimensions. (Required)
* .obj, .mtl, .png - Object file format used when placing into A-Frame scene, stored as three files per model here: /assets/obj/ (Required)
* .vox - The object's raw source file that can be edited again in the future, stored here: /assets/vox/ (Optional)

(4) Add to JSON File - To enable placement of the object within the City Builder app, the object needs to be included in a "creator_group" JSON file. Here's an example: /assets/mmmm_veh.json

To make it easier to add a large number of objects at once, there is a utility script to create a new "creator_group" JSON file here: /utils/json_builder.js

(5) Load JSON file from City Builder - You must add the newly created JSON "creator_group" file to the list of included model definitions upon load of City Builder app. Add your filename to this list:
https://github.com/kfarr/aframe-city-builder/blob/master/lib/builder-controls.js#L57

(5) Test it out! Take a screenshot while you're testing! Submit a pull request and include a note and your fancy screenshot!

## Need inspiration? What are some other objects to make?
* more cool vehicles
* flying things
* more "bases" like intersection, left turn, right turn, green park only, pedestrian and bike path only
* more advanced light poles, signals, signs
* people
* trains

## How can I contribute to City Builder?
Fork this repo, start making changes, and submit a pull request! Also feel free to file an issue or reach out directly kieran.farr@gmail.com with your idea and I can try to help make your idea work.

## Need inspiration? Here is a partial wishlist for City Builder features:
NOT IN THIS RELEASE
- load directly from voxel https://gist.github.com/JoshGalvin/398ad2339ad7ae93e72489684d599466 https://github.com/daishihmr/vox.js
- enable second controller
- new bases to fit scene (http://streetmix.net/kfarr/3/a-frame-city-builder-street-only)
- ability for select bar component to delay loading / init
- add promise to know when all objects are loaded (or fail)
- teleport https://chenzlabs.github.io/aframe-teleport-controls/sample/
- blender baking of AO texture and progressive application of AO textures after scene fully loaded
- support for google draco object compression
- scale large/small (and rotate?) with both grips being pressed (what would happen to undo?)
- add a small haptic feedback see: https://github.com/imgntn/jBow/blob/ab2d254f288c563f33e6ed745e41a72ee2b7f759/components/bow-and-arrow.js#L163
- create components from the useful a-frame stuff (menu switcher, save/load json, desktop dialog ui, message notification)
- placing a baseplate over another object should replace the baseplate, not place both on same location
  - use flushtodom to force update of position to DOM https://aframe.io/docs/0.4.0/components/debug.html#component-to-dom-serialization
- sound effects - commodore 64 style
- aframe city website - have a central registry of objects (json file is fine to start) that is not in index.html file ui inspiration - https://buffy.run/model/578e438962c6c80000ea4c5e -> this could be done without a server -> use a git based site builder service. register this as aframe.city
- try progressive enhancement to replace obj with baked ply after loading
- load new scenes without destroying original (load by appending) - does not handle collision case
- add support for google draco object compression
- add some clouds
- send a VR postcard to facebook / social media
- add sunlight day cycle as aframe component http://jeromeetienne.github.io/threex.daynight/examples/basic.html
- firebase or simple db storage for scenes in json or other format
- use a proper build process to combine and minify all the various libraries
- clear / delete (bulldozer?)
- adopt a palette or other creative user interface to choose categories of objects, it is tiresome to scroll past many objects
- integrate with http://streetmix.net/ to generate street blocks
- auth / storage service
- highlight currently overlapping grid location
- cars to follow prescribed course on roads
- user generated objects / global object store
- add aframe snowplay type support https://github.com/rondagdag/aframe-snow-play
- persistent multiuser world
- use geolocation api to with virtual citybuilder locations to create "mini second life"
- physics
- try isometric view on mobile / non-vr devices (examples https://github.com/aframevr/aframe/issues/84 and http://wafi.iit.cnr.it/webvis/lab/preview.php?gist_id=07b5887a1d57b40b6065)
- add non-flat lowpoly terrain like this example https://playcanvas.com/

## Credits
* most models made by Mike Judge, see more here: https://github.com/mikelovesrobots/mmmm
* table http://tf3dm.com/3d-model/table-65702.html
* tree and simple base plates created by kfarr using magicavoxel (https://ephtracy.github.io/)
* city builder text based on https://github.com/ngokevin/kframe/blob/master/components/text/examples/vaporwave/index.html
* vox/kfarr_veh_tram_avenio.vox inspired by https://sketchfab.com/models/7e3d9f90af9447dabcb813a4af43ae76

## License
* The A-Frame City Builder codebase is MIT License Copyright (c) 2017 Kieran Farr
* Most nice looking objects are made by Mike Judge from his <a href="https://github.com/mikelovesrobots/mmmm">"Mini Mike's Metro Minis" project</a> under the <a href="https://github.com/mikelovesrobots/mmmm/blob/master/LICENSE">Creative Commons License.</a>
