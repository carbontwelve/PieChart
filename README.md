PieChart
========

A reasonably efficient* class for drawing pie charts with ImageMagick or GD in PHP. Intended as a
learning exercise for using the NetBeans IDE and the Xdebug profiler and debugger. The code is
available under the [GNU GPL v3.0](http://www.gnu.org/licenses/gpl-3.0.html), so feel free to use it
with attribution. I recommend using the Imagick version, `PieChartImagick` over the GD version,
 `PieChartGD`.

### Demonstration ###
Below is the code required to generate a pie chart and echo it to the client's browser. The example
uses the method `outputPNG()` to tell the browser to render the image. Alternatively, the function
`forceDownloadPNG()` can be used to instruct the browser to bring up the save dialog.

### Documentation ###
[View the documentation](http://samchristy.github.com/PieChart/documentation/index.html)
(generated with [ApiGen](http://apigen.org/)).

#### Installation ####
[Use Composer](https://packagist.org/packages/samchristy/piechart)!

#### Example Usage ####
````php
<?php
require 'vendor/autoload.php';  // Composer's autoloader.
use SamChristy\PieChart\PieChartGD;

$chart = new PieChartGD(600, 375);

$chart->setTitle('Browser Usage Statistics (January - April)');
// Method chaining coming soon!
$chart->addSlice('Google Chrome',   27, '#4A7EBB');
$chart->addSlice('Mozilla Firefox', 23, '#DA8137');
$chart->addSlice('Apple Safari',    11, '#9BBB59');
$chart->addSlice('Opera',            3, '#BE4B48');
$chart->addSlice('Other',            5, '#7D60A0');

$chart->draw();
$chart->outputPNG();
````
#### Output ####
![Pie Chart](src/SamChristy/PieChart/example/example.png)

*This example took 150ms to execute on my laptop (i3-350M @ 2.27 GHz).

#### Transparency ####
Basic transparency support has been added and can be set on initiation of the `PieChartGD` class
by setting the last attribute to `true` like so:

````php
<?php
require 'vendor/autoload.php';  // Composer's autoloader.
use SamChristy\PieChart\PieChartGD;

$chart = new PieChartGD(600, 375, 'Browser Usage Statistics (January - April)', 0x222222, 0x092c5c, true);
$chart->addSlice('Google Chrome',   27, '#4A7EBB');
$chart->addSlice('Mozilla Firefox', 23, '#DA8137');
$chart->addSlice('Apple Safari',    11, '#9BBB59');
$chart->addSlice('Opera',            3, '#BE4B48');
$chart->addSlice('Other',            5, '#7D60A0');

$chart->draw();
$chart->outputPNG();

````

© Sam Christy 2013
