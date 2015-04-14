This is a very simple python module/script to help find postal code, city, province, latitude/longitude matching the supplied postal code, city, province, or coordinate.

The geographical data is stored in a SQLite database file (44.5 MB).

For usage on running from the shell, type:
<pre>./geolocate --help<br>
Usage: geolocate [options]<br>
<br>
Look up geo. details about a postal code, city, province, or coordinate<br>
<br>
Options:<br>
--version   show program's version number and exit<br>
-h, --help  show this help message and exit<br>
-d FILE     the filename of the database containing geolocation data<br>
-p PC       the postal code string to locate (may be partial)<br>
-c CITY     the city name to search for<br>
-P PROV     the province name or code to search for<br>
-r LATLON   perform a reverse lookup based on supplied lat/lon<br>
-a DECPTS   lat/lon accuracy (precision) to match, default 2<br>
-x          output results as XML (can be piped into an XML file).<br>
<br>
If -a precision is greater than -r (lat/lon) precision, it will be set to the<br>
lesser of the lat/lon precisions. Currently only has infromation for Canadian<br>
postal codes.</pre>

To use it from your Python scripts, make sure it's in the PYTHONPATH and then use like this:
```

from geolocate import GeoLocation
gl = GeoLocation()
results = gl.locate_by_postal_code('L0M1P0')
results = gl.search_database(city='ottawa')
results = gl.locate_by_latlon(
'44.4500000000000028', '-80.2172000000000054')
```
<em>Note: I'm not sure what those question marks are doing in the code, something put there by Google Code, please don't include them in your Python code.</em>

The current database only has Canadian postal codes (765,344 of them).  I'm pretty sure there are currently over 800,000 postal codes, so this database is not completely up to date.

I plan on adding more Canadian postal codes as well as US zip codes and possibly post codes from the UK.