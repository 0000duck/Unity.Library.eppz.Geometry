# eppz.Geometry
> part of [**Unity.Library.eppz**](https://github.com/eppz/Unity.Library.eppz)

📐 2D geometry for Unity.

Polygon triangulation, Delunay triangulation, Voronoi, polygon offset, polygon outline, union of polygons, substraction of polygons. polygon clipping, polygon winding direction, polygon area, polygon centroid, centroid of multiple polygons, line intersection, point-line distance, segment intersection, polygon-point containment, and more.

The library is **being used in production**. However, it comes with the disclaimed liability and warranty of [MIT License](https://en.wikipedia.org/wiki/MIT_License)).

## [`Geometry.cs`](Geometry.cs)

The basic 2D geometry algorithm collection is implemented in this static base class.

* **Point**
	+ `bool ArePointsEqualWithAccuracy(Vector2 a, Vector2 b, float accuracy)`
		+ Determine if points are equal with a given accuracy.
	+ `bool ArePointsCCW(Vector2 a, Vector2 b, Vector2 c)`
		+ Determine winding direction of three points.		
* **Rect / Bounds**
	+ `bool IsRectContainsRectSizeWithAccuracy(Rect rect1, Rect rect2, float accuracy)`
		+ Determine if `rect2.size` fits into `rect1` (compare sizes only).
	+ `bool IsRectContainsRectWithAccuracy(Rect rect1, Rect rect2, float accuracy)`
		+ Determine if `rect2` is contained by `rect1` (even if permiters are touching) with a given accuracy.
* **Line**
	+ `Vector2 IntersectionPointOfLines(Vector2 segment1_a, Vector2 segment1_b, Vector2 segment2_a, Vector2 segment2_b)`
		+ Returns intersection point of two lines (defined by segment endpoints). Returns zero, when segments have common points, or when a segment point lies on other.
	+ `float PointDistanceFromLine(Vector2 point, Vector2 segment_a, Vector2 segment_b)`
		+ Determine point distance from line (defined by segment endpoints).
* **Segment**
	+ `bool PointIsLeftOfSegment(Vector2 point, Vector2 segment_a, Vector2 segment_b)`
		+ Determine if a given point lies on the left side of a segment (line beneath).
	+ `bool AreSegmentsEqualWithAccuracy(Vector2 segment1_a, Vector2 segment1_b, Vector2 segment2_a, Vector2 segment2_b, float accuracy)`
		+ Determine if segments (defined by endpoints) are equal with a given accuracy.
	+ `bool HaveSegmentsCommonPointsWithAccuracy(Vector2 segment1_a, Vector2 segment1_b, Vector2 segment2_a, Vector2 segment2_b, float accuracy)`
		+ Determine if segments (defined by endpoints) have common points with a given accuracy.
	+ `bool AreSegmentsIntersecting(Vector2 segment1_a, Vector2 segment1_b, Vector2 segment2_a, Vector2 segment2_b)`
		+ Determine if two segments defined by endpoints are intersecting (defined by points). True when the two segments are intersecting. Not true when endpoints are equal, nor when a point is contained by other segment. Credits to [Bryce Boe](https://github.com/bboe) (@bboe) for his writeup [Line Segment Intersection Algorithm](http://bryceboe.com/2006/10/23/line-segment-intersection-algorithm).
* **Polygon** (using `EPPZ.Geometry.Polygon`)
	+ `bool IsPolygonContainsPoint(Polygon polygon, Vector2 point)`
		+ Test if a polygon contains the given point (checks for sub-polygons recursive). Uses the same Bryce boe algorithm above, so considerations are the same. See [Point in polygon](https://en.wikipedia.org/wiki/Point_in_polygon#Ray_casting_algorithm) for more.
	+ `Vector2 CentroidOfPolygons(Polygon[] polygons, Polygon.WindingDirection windingDirection = Polygon.WindingDirection.Unknown)`
		+ Returns the compound centroid of multiple polygon using [Geometric decomposition](https://en.wikipedia.org/wiki/Centroid#By_geometric_decomposition).

## Modules

For clipping, offsetting, triangulating the library use these brilliant third party `C#` libraries below.

* [Clipper](https://github.com/eppz/Clipper)

	+ Polygon and line clipping and offsetting library (C++, C#, Delphi) by Angus Johnson. See standalone project repository [Clipper](https://github.com/eppz/Clipper) for details.

* [Triangle.NET](https://github.com/eppz/Triangle.NET)

	+ Triangle.NET generates 2D (constrained) Delaunay triangulations and high-quality meshes of point sets or planar straight line graphs. It is a C# port by Christian Woltering of Jonathan Shewchuk's Triangle software. See standalone project repository [Triangle.NET](https://github.com/eppz/Triangle.NET) for details.

## License

> Licensed under the [**MIT License**](https://en.wikipedia.org/wiki/MIT_License).