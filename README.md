# hello-world






import turtle

import random


turtle.setup(500, 500)

turtle.bgcolor("gray")

turtle.title("贪吃蛇")

turtle.tracer(False)



square_size = 20

start_length = 3

delay = 100


snake = []
for i in range(start_length):
    turtle.goto(i * square_size, 0)
    snake_segment = turtle.Turtle("square")
    snake_segment.color("white")
    snake_segment.penup()
    snake.append(snake_segment)


food = turtle.Turtle("circle")
food.color("red")
food.penup()
food.goto(random.randint(-12, 12) * square_size, random.randint(-12, 12) * square_size)


def move():
    global food
    head = snake[0].clone()
    head.color("green")
    head.forward(square_size)

    if head.distance(food) < square_size:
        food.goto(random.randint(-12, 12) * square_size, random.randint(-12, 12) * square_size)
        snake.append(food.clone())

    for i in range(len(snake) - 1, 0, -1):
        snake[i].goto(snake[i - 1].xcor(), snake[i - 1].ycor())

    snake[0].setheading(head.towards(snake[1]))
    snake[0] = head

    if head.xcor() < -12 * square_size or head.xcor() > 12 * square_size or head.ycor() < -12 * square_size or head.ycor() > 12 * square_size:
        turtle.bye()

    for i in range(1, len(snake)):
        if head.distance(snake[i]) < square_size:
            turtle.bye()

    turtle.ontimer(move, delay)


move()
turtle.done()
