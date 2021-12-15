# geocode
Experimenting with all-numeric geocodes to support the delivery of parcels and logistic units that do not have a conventional postal address.

A demo page is available at https://gs1.github.io/geocode/

Within a barcode, an all-numeric geocode can be encoded more efficiently than a code that requires symbol characters such as + or - or decimal point or alphabetic characters such as N, S, E, W.

Using 20 numeric digits it is possible to encode WGS84 latitude/longitude coordinates with a precision of around 1.1 centimetres.

That's because 0.0000001 degrees corresponds to approximately 1.1cm  on the surface of the Earth (2&pi; * 6371,000m / 1E7 / 360.

In this approach we use two 10 digit fields that are concatenated together to form a 20-digit numeric geocode string.  

The first ten digits represent latitude measured in decimal degrees northwards from the goegraphic south pole, then multiplied by 10 million and (if necessary) left-padded with '0' digits to reach a total of 10 digits.  This approach means that the value is always positive, ranging from 0 at the geographic south pole to 1800000000 at the geographic north pole.

The second ten digits represent longitude measured in decimal degrees east of the Greenwich meridian, then multiplied by 10 million.  Locations west of the Greenwich meridian (such as the Hallgrímskirkja in Reykjavik, Iceland) might be considered to have a negative longitude such as -21.926538572471713 but by adding 360°, this can be expressed as a positive longitude such as +338.0734614275.  It is this positive longitude value in decimal degrees that is then multiplied by 10 million and (if necessary) left-padded with '0' digits to reach a total of 10 digits.

The following diagrams provide some further explanation of this approach:

![Latitude and longitude](GeoCodeIntroPage.svg?raw=true "Latitude and longitude")

Flowchart for encoding latitude and longitude as a 20-digit geocode:

![Encoding flowchart](Flowchart1.svg?raw=true "Flowchart for encoding")

Flowchart for decoding a 20-digit geocode to latitude and longitude:

![Decoding flowchart](Flowchart2.svg?raw=true "Flowchart for decoding")

Summary of formulae:

![Formulae summary](Summary.svg?raw=true "Summary of formulae")

Worked Example 1:

![Worked example 1](WorkedExample1.svg?raw=true "Worked example 1")

Worked Example 2:

![Worked example 2](WorkedExample2.svg?raw=true "Worked example 2")







