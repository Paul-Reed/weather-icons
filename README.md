# DO NOT USE - SEE [WEATHER-ICONS-LITE](https://github.com/Paul-Reed/weather-icons-lite) WHICH IS MERGED INTO NODE-RED CORE

## 222 Weather Themed Icons and CSS

Weather Icons is the only icon font and CSS with 222 weather themed icons, ready to be dropped right into [Bootstrap](http://www.getbootstrap.com), or any project that needs high quality weather, maritime, and meteorological based icons!

Get started at [http://weathericons.io](http://weathericons.io)!

![Icon Preview](http://i.imgur.com/XmZW2q3.png)

## Basic Usage

The icons are displayed by using an `i` element and adding the base class `wi` and then the icon class you want, such as `day-sunny`. This then looks like `<i class="wi wi-day-sunny"></i>`.

To add a modifier, include the class you want after the icon name, which looks like `<i class="wi wi-day-sunny wi-flip-vertical"></i>`. You can flip, rotate, or add a fixed width. See it all at [http://weathericons.io](http://weathericons.io).

## API Usage

This set includes companion CSS files for popular weather service API. Presently there are mappings for Forecast.io, Open Weather Map, World Meteorological Organization, Weather Underground, and Yahoo. Check the [API List](https://erikflowers.github.io/weather-icons/api-list.html) to see the class names.

For darksky - use the mappings for forecast.io - they are compatible.

## Wind Usage

To display a wind indicator, you must use the base class `wi` and `wi-wind`, and then include the towards/from direction you want, like `from-293-deg`. This ends up looking like . You can use any degree from 0 to 359 in this manner. **Note:** A "from" class has the point of the arrow at the opposite end of the degree. For example, a "from 90 degrees" icon would point to the 270 degree mark, wheras a "towards 270 degrees" would point at the same 270 degree mark.

Included in the set as well are aliases to point to cardinal directions. They work the same as degrees, for example `<i class="wi wi-wind towards-sse"></i>` would be an arrow pointing to the South by Southeast (roughly 158 degrees). 

## Use in node-red dashboards

Create a new static directory within your `.node-red` directory from which you can serve the CSS and Font files, for example 'public'.  
Git clone this repo into your newly created static directory;

    cd && cd .node-red/public
    git clone https://github.com/Paul-Reed/weather-icons.git

Edit your node-red settings file, usually `nano /home/pi/.node-red/settings.js` as follows;

Firstly, edit httpStatic to read your static folder  
`httpStatic: '/home/pi/.node-red/public',`
and also if you havent already done so, httpAdminRoot must also be used to make the editor UI available at a path other than /. So for example if you changed the setting to `httpAdminRoot: '/admin',` then instead of your editor being accessed at the URL `192.168.168.13:1880/` you would use `192.168.168.13:1880/admin`

Then stop and restart node-red

An example of using the icons in a node-red ui 'template node', would be;

    <link rel="stylesheet" href="/weather-icons/mycss/weather-icons.min.css">
    <div style="display: flex;height: 100%;justify-content: center;align-items: center;">
    <i class="fa-4x wi wi-wu-{{msg.payload}}"></i>
    </div> 

The class shown will retreive the icon as called in the msg payload, display it at x4 size (fa-4x), and use the Wunderground.com icon mapping (wi-wu).

The `<div>` will centre the icon in the dashboard panel.

There is an [example node-red flow](/example/example.txt) to get you started, once you have completed the above.

## Add entries to app.cache

If you have password protected your dashboard by enabling `httpNodeAuth`, then unless the weather-icons css & font files are added to the node-red dashboard app.cache, you will get repeated requests to re-authorise, due to them being again requested from the server, instead of being cached by the browser.

To add the files to the dashboard app.cache;  
`nano /home/pi/.node-red/node_modules/node-red-dashboard/dist/dashboard.appcache`  
and add the following entries to the the file;  
```
../../../weather-icons/mycss/weather-icons.min.css
../../../weather-icons/myfonts/weathericons-regular-webfont.eot
../../../weather-icons/myfonts/weathericons-regular-webfont.svg
../../../weather-icons/myfonts/weathericons-regular-webfont.ttf
../../../weather-icons/myfonts/weathericons-regular-webfont.woff
../../../weather-icons/myfonts/weathericons-regular-webfont.woff2
```  
Save, and restart the node-red server to take effect.

**Please note** Updating or re-installing the dashboard node will wipe out these changes, and they will need to be re-applied.

## Contributing
If you feel so inclined to add icon ideas, icon art, or other fixes/changes to how the package works, feel free to help!

## Credit
The icon designs are originally by [Lukas Bischoff](http://www.twitter.com/artill). Icon art for v1.1 forward, HTML, Less, and CSS are by [me (Erik)](http://www.helloerik.com).
Node-red compatibility changes by Paul Reed.

## Licensing

* Weather Icons licensed under [SIL OFL 1.1](http://scripts.sil.org/OFL)
* Code licensed under [MIT License](http://opensource.org/licenses/mit-license.html)
* Documentation licensed under [CC BY 3.0](http://creativecommons.org/licenses/by/3.0)
