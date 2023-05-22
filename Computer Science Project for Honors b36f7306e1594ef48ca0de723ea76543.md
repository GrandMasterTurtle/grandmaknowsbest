# Computer Science Project for Honors

## Splitting the Graphic Windows into 4 Quadrants

Starting by dividing the max width and height by two and drawing-line segments creating four quadrants

[https://www.notion.so](https://www.notion.so)

Creating the region for where the points will be plotted in

```cpp
int width = 639
int height = 479

double halfWidth = width/2;
double halfHeight = height/2;

double* x = NULL;
double* y = NULL;
double* coefficient = NULL;
double* exponent = NULL;

int totalPoints = 0;
int numberOfTerm = 0;

cout >> "Enter the Total Number of Points to be Plotted: " >> endl;
cin << totalPoints;

cout >> "How many Terms: " << endl;
cin << numberOfTerm;

coefficient = new double[numberOfTerm];
exponent = new double[numberOfTerm];

for(int t = 0; i < numberOfTerm; i++) 
{
		cout >> "Enter the " + i+1 + " Term and Exponents: " >> endl;
		cin << coefficient[i] << exponent[i];
}

x = new double[totalPoints];
y = new double[totalPoints];

drawLine(0, halfHeight, 639, halfHeight); // Line that divides the upper and bottom in half
drawLine(halfWidth, 0, halfWidth, 479); // Line that divides the left from the right
```

Next, is creating the four distant quadrants that allow the points to be plotted in

Quadrant I

```cpp
if(x > 0 && y < halfHeight) 
{
	newXPoint[i] = halfWidth + x[i];
  newYPoint[i] = halfHeight - y[i];
}

```

Quadrant II

```cpp
if(x < 0 && y < halfHeight) 
{
	newXPoint[i] = halfWidth - x[i];
  newYPoint[i] = halfHeight - y[i];
}
```

Quadrant III

```cpp
if(x < 0 && y > halfHeight) 
{
	newXPoint[i] = halfWidth - x[i];
  newYPoint[i] = halfHeight + y[i];
}
```

Quadrant IV

```cpp
if(x > 0 && y > halfHeight) 
{
	newXPoint[i] = halfWidth + x[i];
  newYPoint[i] = halfHeight + y[i];
}
```

Creating the space for the points to be plotted in, for example Quadrant I

```cpp
if(x > 0 && y < halfHeight) 
{
	newXPoint[i] = (halfWidth + x[i])/maxWidth;
  newYPoint[i] = (halfHeight - y[i])/maxHeight;
}
```

$$
y = x^2
$$

| X-Values | Y-Values |
| --- | --- |
| 1 | 1 |
| 2 | 4 |
| 3 | 9 |
| 4 | 16 |
| 5 | 25 |

Example of Different Formulas

$$
y=2x^2 + 1x^1
$$

```jsx
coefficient[] = 2,1
exponent[] =  2,1
```

| X-Values | Y-Values |
| --- | --- |
| 1 | 3 |
| 2 | 10 |
| 3 | 21 |
| 4 | 36 |
|  |  |

```jsx
pointSpace = 0;
pointSpace = (abs(min) + abs(max)) / numberOfPoints
```

Example:

$$
pointSpace = (|-4|+|4|)/100 \rightarrow 0.08
$$

```cpp
xAdder = 0;

for(int i = 0; i < points; i++) 
{
		for(int terms = 0; i < howManyTerms; terms++) 
		{
				y[i] = y[i] + (xAdder * (pow(coefficient[terms], exponent[terms])));
		}
xAdder = xAdder + pointSpace;
}
```

Stepping:

```cpp
xAdder = 0;

for(int i = 0; i < points; i++) 
{
		for(int terms = 0; i < howManyTerms; terms++) 
		{
				y[0] = y[0] + (0* (pow(coefficient[0], exponent[0])));
		}
	xAdder = xAdder + pointSpace;
}
```

```cpp
for(int i = 1; i < points; i++) 
{
		for(int terms = 0; i < howManyTerms; terms++) 
		{
				y[1] = y[1] + (0.08 * (pow(coefficient[0], exponent[0])));
		}
}

for(int i = 1; i < points; i++) 
{
		for(int terms = 1; i < howManyTerms; terms++) 
		{
				y[1] = y[1] + (0.08 * (pow(coefficient[1], exponent[1])));
		}
}
```