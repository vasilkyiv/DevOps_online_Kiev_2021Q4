
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 08 Python](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m8) 
===========================================================================

[TASK_8.1 Python intro](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m8/task8.1) 

> - 1 install & configure ***jupiterlab*** under windows 11 (64)

[Install Python and Jupyter Notebook in Windows 11. Using pip.](https://www.youtube.com/watch?v=1w-Bm4zpFgs)

# tuping  in CMD

***python --version***

***pip --version***

***pip install jupiterlab***

***python.exe -m pip install --upgrade pip***

***python3 -m pip install jupyterlab***

***python -m pip install jupyterlab***

***python -m pip install jupyter***

***python -m pip install jupyter notebook***

# to start ***jupyter notebook*** tuping ***jupyter notebook*** in CMD

***jupyter notebook***

*********************************************

[Lesson 1](https://www.youtube.com/watch?v=LFCq-mNF96c)

[Lesson 2](https://www.youtube.com/watch?v=P8XvMo_NNvo)

[Lesson 3](https://www.youtube.com/watch?v=GLaH7YYO-2I)

[Lesson 4](https://www.youtube.com/watch?v=sZ0EIwgLblY)

# solv_square_equation.py

    import math


    def validate_param():
        attepmts = 3
        while attepmts > 0:
            try:
                print(f'you have {attepmts} attepmts')
                a = int(input("Enter value for a: "))
                b = int(input("Enter value for b: "))
                c = int(input("Enter value for c: "))
            except ValueError:
                print("Value is not integer!")
                attepmts -= 1
                # validate_param(a, b, c)
                continue
            else:
                return a, b, c


    def discriminant(a, b, c):
        discr = b ** 2 - 4 * a * c
        return discr


    def roots(discr, a, b, c):
        if discr > 0:
            x1 = (-b + math.sqrt(discr)) / (2 * a)
            x2 = (-b - math.sqrt(discr)) / (2 * a)
            print("x1 = %.2f \nx2 = %.2f" % (x1, x2))
            return x1, x2
        elif discr == 0:
            x = -b / (2 * a)
            print("x = %.2f" % x)
            return x
        else:
            print("Equation no have roots")



    def solv_square(a, b, c) -> roots:
        discr = discriminant(a, b, c)
        root = roots(discr, a, b, c)
        print("Discriminant =", discr)
        return root

    def square_print(a, b, c, roots):
        print("a =", a)
        print("b =", b)
        print("c =", c)
        roots


    def main():
        print("Please enter values for equation:")
        valid_params = validate_param()
        a = valid_params[0]
        b = valid_params[1]
        c = valid_params[2]
        solv_square(a, b, c)
        square_print(a, b, c, roots)

        

    if __name__ == "__main__":
        main() 

# unit_test.py

    import unittest
    import solv_square_equation

    class MyTest(unittest.TestCase):
        def test_discriminant(self):
            self.assertEqual(solv_square_equation.discriminant(1,2,3), -8)

        def test_solv_square(self):
            self.assertEqual(solv_square_equation.solv_square(24,580,45), (-0.07783690692744945, -24.088829759739216))


        def test_roots(self):
            self.assertEqual(solv_square_equation.roots(332080, 24,580,45), (-0.07783690692744945, -24.088829759739216))


    if __name__ == '__main__':
        unittest.main()