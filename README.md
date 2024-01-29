The Excel incident tracker is hosted here:
https://docs.google.com/spreadsheets/d/1x6ijusYs6zQkMYCrb0MQLAy0d0U4t3hO/edit?usp=sharing&ouid=114388627769657303489&rtpof=true&sd=true


In order to update the GeoJSON "features" objects for the map, you can do the following to create the objects for you:
1) select and copy all the data (Only the data) for columns (CODE,COLOR,LON,LAT).
2) paste into a text editor with regex search and replace functionality.
3) Use the following for the find: ^([^\t]+)\t([^\t]+)\t([^\t]+)\t([^\t]+)$
4) Use the following for the replace all (this is a multiline string):
{
   "type": "Feature", "geometry": { "type": "Point", "coordinates": [$3, $4] },
   "properties": { "color":"$2", "description": "$1" }
},
