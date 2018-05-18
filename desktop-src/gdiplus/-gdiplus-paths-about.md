---
Description: 'Paths are formed by combining lines, rectangles, and simple curves. Recall from the Overview of Vector Graphics that the following basic building blocks have proven to be the most useful for drawing pictures.'
ms.assetid: '88fea2ec-7b53-44bb-841d-486c5c879c68'
title: Paths
---

# Paths

Paths are formed by combining lines, rectangles, and simple curves. Recall from the [Overview of Vector Graphics](-gdiplus-overview-of-vector-graphics-about.md) that the following basic building blocks have proven to be the most useful for drawing pictures.

-   Lines
-   Rectangles
-   Ellipses
-   Arcs
-   Polygons
-   Cardinal splines
-   Bézier splines

In Windows GDI+, the [**GraphicsPath**](-gdiplus-class-graphicspath-class.md) object allows you to collect a sequence of these building blocks into a single unit. The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the [**Graphics::DrawPath**](-gdiplus-class-graphics-drawpath-pen-path-.md) method of the [**Graphics**](-gdiplus-class-graphics-class.md) class. The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.

![illustration of a path that combines a line, an arc, a bezier spline, and a cardinal spline](images/aboutgdip02-art14.png)

The [**GraphicsPath**](-gdiplus-class-graphicspath-class.md) class provides the following methods for creating a sequence of items to be drawn: [AddLine](-gdiplus-class-graphicspath-addline-methods.md), [AddRectangle](-gdiplus-class-graphicspath-addrectangle-methods.md), [AddEllipse](-gdiplus-class-graphicspath-addellipse-methods.md), [AddArc](-gdiplus-class-graphicspath-addarc-methods.md), [AddPolygon](-gdiplus-class-graphicspath-addpolygon-methods.md), [AddCurve](-gdiplus-class-graphicspath-addcurve-methods.md) (for cardinal splines), and [AddBezier](-gdiplus-class-graphicspath-addbezier-methods.md). Each of these methods is overloaded; that is, each method comes in several variations with different parameter lists. For example, one variation of the AddLine method receives four integers, and another variation of the AddLine method receives two [**Point**](-gdiplus-class-point-class.md) objects.

The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: [AddLines](-gdiplus-class-graphicspath-addlines-methods.md), [AddRectangles](-gdiplus-class-graphicspath-addrectangles-methods.md), and [AddBeziers](-gdiplus-class-graphicspath-addbeziers-methods.md). Also, the [AddCurve](-gdiplus-class-graphicspath-addcurve-methods.md) method has a companion method, [AddClosedCurve](-gdiplus-class-graphicspath-addclosedcurve-methods.md), that adds a closed curve to the path.

To draw a path, you need a [**Graphics**](-gdiplus-class-graphics-class.md) object, a [**Pen**](-gdiplus-class-pen-class.md) object, and a [**GraphicsPath**](-gdiplus-class-graphicspath-class.md) object. The **Graphics** object provides the [**Graphics::DrawPath**](-gdiplus-class-graphics-drawpath-pen-path-.md) method, and the **Pen** object stores attributes of the path, such as line width and color. The **GraphicsPath** object stores the sequence of lines, rectangles, and curves that make up the path. The addresses of the **Pen** object and the **GraphicsPath** object are passed as arguments to the **Graphics::DrawPath** method. The following example draws a path that consists of a line, an ellipse, and a Bézier spline.


```
myGraphicsPath.AddLine(0, 0, 30, 20);
myGraphicsPath.AddEllipse(20, 20, 20, 40);
myGraphicsPath.AddBezier(30, 60, 70, 60, 50, 30, 100, 10);
myGraphics.DrawPath(&amp;myPen, &amp;myGraphicsPath);
```



The following illustration shows the path.

![illustration of a path made up of a line, an ellipse, and a bezier spline](images/aboutgdip02-art15.png)

In addition to adding lines, rectangles, and curves to a path, you can add paths to a path. This allows you to combine existing paths to form large, complex paths. The following code adds **graphicsPath1** and **graphicsPath2** to **myGraphicsPath**. The second parameter of the [**GraphicsPath::AddPath**](-gdiplus-class-graphicspath-addpath-addingpath-connect-.md) method specifies whether the added path is connected to the existing path.


```
myGraphicsPath.AddPath(&amp;graphicsPath1, FALSE);
myGraphicsPath.AddPath(&amp;graphicsPath2, TRUE);
```



There are two other items you can add to a path: strings and pies. A pie is a portion of the interior of an ellipse. The following example creates a path from an arc, a cardinal spline, a string, and a pie.


```
myGraphicsPath.AddArc(0, 0, 30, 20, -90, 180);
myGraphicsPath.AddCurve(myPointArray, 3);
myGraphicsPath.AddString(L"a string in a path", 18, &amp;myFontFamily, 
   0, 24, myPointF, &amp;myStringFormat);
myGraphicsPath.AddPie(230, 10, 40, 40, 40, 110);
myGraphics.DrawPath(&amp;myPen, &amp;myGraphicsPath);
```



The following illustration shows the path. Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.

![illustration of a path made up of disconnected lines: an arc, a cardinal spline, a string, and a pie](images/aboutgdip02-art16.png)

 

 


