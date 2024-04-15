import math

def add_vectors(vec1, vec2):
    return [x + y for x, y in zip(vec1, vec2)]

def subtract_vectors(vec1, vec2):
    return [x - y for x, y in zip(vec1, vec2)]

def scalar_multiply(vector, scalar):
    return [x * scalar for x in vector]

def dot_product(vec1, vec2):
    return sum(x * y for x, y in zip(vec1, vec2))

def cross_product(vec1, vec2):
    if len(vec1) != 3 or len(vec2) != 3:
        raise ValueError("Cross product is defined only for 3-dimensional vectors")
    return [
        vec1[1] * vec2[2] - vec1[2] * vec2[1],
        vec1[2] * vec2[0] - vec1[0] * vec2[2],
        vec1[0] * vec2[1] - vec1[1] * vec2[0]
    ]

def multiply_by_constant(vector, constant):
    return [x * constant for x in vector]

def divide_by_constant(vector, constant):
    return [x / constant for x in vector]


from vector_operations import *

vector1 = [1, 2, 3]
vector2 = [4, 5, 6]

print("Addition:", add_vectors(vector1, vector2))
print("Subtraction:", subtract_vectors(vector1, vector2))
print("Scalar multiplication:", scalar_multiply(vector1, 2))
print("Dot product:", dot_product(vector1, vector2))
print("Cross product:", cross_product(vector1, vector2))
print("Multiplication by constant:", multiply_by_constant(vector1, 3))
print("Division by constant:", divide_by_constant(vector2, 2))
