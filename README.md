# draw-a-heart-using-python-turtle
This is a introduction of drawing a heart with Cubic Bézier curve using python turtle

# Draw a Heart Shape using Cubic Bezier Curve by Liu Yuxuan
import turtle

# Initialize the turtle screen
screen = turtle.Screen()
screen.setup(width=800, height=600)
screen.title("Heart Shape(using Cubic Bezier Curve)")
turtle.speed(0)  # Set the drawing speed to maximum

# Function to draw a control point and label
def draw_point(x, y, label):
    turtle.penup()
    turtle.goto(x, y)  # Position the label
    turtle.pendown()
    turtle.dot(8, "blue")  # Draw the control point
    turtle.write(label, align="center")

# Function to compute the Bezier point
def cubic_bezier(t, p0, p1, p2, p3):
    x = (1 - t)**3 * p0[0] + 3 * (1 - t)**2 * t * p1[0] + 3 * (1 - t) * t**2 * p2[0] + t**3 * p3[0]
    y = (1 - t)**3 * p0[1] + 3 * (1 - t)**2 * t * p1[1] + 3 * (1 - t) * t**2 * p2[1] + t**3 * p3[1]
    return x, y


# Define the control points
p0 = (0, 180)# This is the top point
p1 = (-250, 400)
p2 = (-350, 20)
p3 = (0, -180)#This is the bottom point
p4 = (250, 400)
p5 = (350, 20)

# Draw the control points 
turtle.pencolor("magenta")
draw_point(*p0, "P0")
draw_point(*p1, "P1")
draw_point(*p2, "P2")
draw_point(*p3, "P3")
draw_point(*p4, "P4")
draw_point(*p5, "P5")

# Draw the Bezier curve
turtle.penup()
for t in range(0, 101):
    t /= 100.0
    x, y = cubic_bezier(t, p0, p1, p2, p3)
    turtle.goto(x, y)
    turtle.pendown()

turtle.penup()
for t in range(0, 101):
    t /= 100.0
    x, y = cubic_bezier(t, p0, p4, p5, p3)
    turtle.goto(x, y)
    turtle.pendown()
