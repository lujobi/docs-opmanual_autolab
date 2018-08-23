# Future projects {#autocharging-future status=beta}

There are still multiple tasks which would improve the charging area by a lot. In the following, you find a list of those tasks with a small description.

## Improve the intersection navigation

For traversing through the maintenance area, intersection navigation is a crucial part. With the new Unicorn Intersection Node, the success rate was raised to over 90%. For a completely autonomous city, this is still way too low.

## Implement the battery capacity estimation

Currently, the time a Duckiebot drives through the city and stays inside a charger are hard coded variables. With a high enough charging time and a low enough driving time, it is ensured that a Duckiebot never reaches a battery level of 0%. The drawback is that the efficiency in terms of the ratio $\frac {driving time}{charging time}$ is very low. This can be improved by implementing the battery capacity estimation: with the new add-on board, one is able to measure the current going into the battery and therefore integrate it to obtain the battery level.

## Improve the vehicle detection

In order to keep distance to a Duckiebot in front, the vehicle avoidance node detects a circle grid pattern ($7 \times 3$) and adapts the velocity. However, the detection only runs at $2Hz$ and fails sometimes.

## Improve the TCP Communication Node

With the introduction of a charging station, communication between different Duckiebots outside of intersections became crucial. This is why we developed the TCP Communication Node: Every time a Duckiebot goes charging, it finds a free spot by asking a centralized server and reserves it. When the Duckiebot finishes charging, it releases that spot again.

This node was not tested enough and may have some bugs which need to be fixed. Also, if a Duckiebot is killed while charging (unplug the Raspberry pi without terminating ROS with CTRL+C), a charging spot is used by a Duckiebot phantom. This phantom can only be removed by connecting to the TCP server and manually adjusting the variable.