### Open Street Map

https://github.com/msteiger/jxmapviewer2

``` groovy

    implementation 'org.jxmapviewer:jxmapviewer2:2.8'
    
```

This link shows how to create a simple application that displays a map.

https://github.com/msteiger/jxmapviewer2/blob/master/examples/src/sample1_basics/Sample1.java

This code allows you to make your map interactive. (
from https://github.com/msteiger/jxmapviewer2/blob/master/examples/src/sample3_interaction/Sample3.java)

``` java

        MouseInputListener mia = new PanMouseInputListener(mapViewer);
        mapViewer.addMouseListener(mia);
        mapViewer.addMouseMotionListener(mia);

        mapViewer.addMouseListener(new CenterMapListener(mapViewer));

        mapViewer.addMouseWheelListener(new ZoomMouseWheelListenerCursor(mapViewer));

        mapViewer.addKeyListener(new PanKeyListener(mapViewer));

```

## Drawing over the map

# Drawing Anchors (known as Waypoints)

``` java 

        WaypointPainter<Waypoint> waypointPainter = new WaypointPainter<Waypoint>();
        Set<Waypoint> waypoints = Set.of(
                new DefaultWaypoint(new GeoPosition(40.77228687788679, -73.9842939376831)),
                ...
        );
        waypointPainter.setWaypoints(waypoints);

```

# Drawing Routes

``` java

    RoutePainter routePainter = new RoutePainter(track);

```

Copy this file into your repository since it's only in their examples. You can edit this class to allow you to set
tracks.

https://github.com/msteiger/jxmapviewer2/blob/master/examples/src/sample2_waypoints/RoutePainter.java

# Using Multiple Painters

``` java 
        List<Painter<JXMapViewer>> painters = List.of(
            routePainter,
            waypointPainter
        );

        CompoundPainter<JXMapViewer> painter = new CompoundPainter<JXMapViewer>(painters);
        mapViewer.setOverlayPainter(painter);
```

# Clicking on the Map

``` java

    mapViewer.addMouseListener(new MouseAdapter() {
            @Override
            public void mouseClicked(MouseEvent e) {
                int x = e.getX();
                int y = e.getY();
                Point2D.Double point = new Point2D.Double(x, y);
                GeoPosition position = mapViewer.convertPointToGeoPosition(point);
            }
        });

```

## Automatic Zooming to Fit

``` java 

        mapViewer.zoomToBestFit(
                Set.of(from, startStation, endStation, to),
                1.0
        );

```

