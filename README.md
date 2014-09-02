A javascript widget to display a calendar.

Define a variable called `semesterDates` as an array of one or more date specs.
Date specs may be given in any order in the array.

A date spec is an array with an even length of at least two elements.  The
first two elements of a date spec `ds` are

  ds[0] = date month, 1 <= ds[0] <= 12, jan = 1.
  ds[1] = day in month, 1 <= ds[1] <= last day in month ds[0].

The elements after the first two elements in a date spec are taken as a
sequence of (attribute name, attribute value) pairs for the date being
specified.  An attribute name is always a string; the attribute value's type
depends on the attribute being specified (or, if you prefer, has type Object).
Attribute pairs may appear in any order in a date spec.

Although a date spec may contain arbitrary attribute pairs, the two used by the
semester calendar are:

  ('color', [r, g, b]), where r, g, and b are numbers in [0..255]: the
  background color used when the date is drawn in the calendar.  If a date has
  no color attribute defined, the calandar's background color is used.

  ('test', b), where b is a boolean: there's a test on this date iff b is true.
  If a date has no test attribute defined, no test is assumed for the date.

For example (which should be pleasing to those ultra-anal about name-space
pollution):

  <script>
   var semesterDates = 
     (function() {

       var green    = [  0, 255,   0];
       var orange   = [255, 165,   0];
       var red      = [255,   0,   0];
       var yellow   = [255, 255,   0];
       var skyBlue  = [135, 206, 235];

       return [ [ 9,  2, 'color', green], 
		[10, 16, 'color', skyBlue], 
		[10, 21, 'color', yellow, 'test', true], 
		[11,  4, 'color', orange], 
		[11, 27, 'color', skyBlue], 
		[12, 11, 'color', red] ];
       })();
  </script>
