

## Setup
```
pip install robotpy
pip install robotpy-commands-v2

```
https://robotpy.readthedocs.io/en/stable/install/rev.html#install-rev

## Unit Tests in this project

There are several kinds of unit tests that are used in this project. The tests are there
to make sure that the code does and continues to do what we expect it to do.

### Unit Tests for the Arm Subsystem

The first kind of unit test is a test for the arm subsystem. The arm subsystem is a class
that is used to control the arm of the robot. The arm has a motor that is used to move the
arm up and down. The arm also has a sensor that is used to measure the angle of the
arm.

We are going to test a few things about the arm subsystem. First we are going to test the
```set_angle``` method. This method is used to set the angle of the arm. To do this 
we will need to mock out the motor for the arm, and make sure that when we ask to set 
the angle that the motor gets the information. We won't 
be able to test to make sure it gets the right information, but we will make 
sure that the motor activates its ```setReference``` method.

We will also test the ```get_angle``` method. This method is used to get the angle of the
arm. To do this we will need to mock out the sensor for the arm, and make sure that when
we ask the motor for the value of the encoder it gives a particular value. Then we will be
able to check that our ```get_angle``` method returns the correct value.

All of this is made easier by creating a **fixture** at the top of the test that 
mocks out the arm subsystem. This fixture is used by the test to get the arm subsystem
that is being tested. 

#### Test Operator Control

The first test that we will write is a test for the operator control method. This method
is used to control the robot during the operator control period. The operator control
period is the period of the match where the driver controls the robot.

This test checks to see if a joystick input causes a corresponding
motor output. Obviously this is a silly example, but you can build
upon it to make much more comprehensive (and stateful) tests.

Keep in mind that when you set a value, the robot code does not
see the value immediately, but only when teleopPeriodic is called,
which is typically every 20ms.

What happens in this test is that we simulate a motor that is intended
to be a drive motor. Then we simulate the joystick. We set the joystck to 
different values and then we check to see if the motor is set to the
appropriate value.

#### Test Autonomous

This test is one that comes with the robotpy project. It is a test that
is used to test the autonomous mode of the robot. 

#### Test Disabled

This test is one that comes with the robotpy project. It is a test that
is used to test the disabled mode of the robot.

#### Test Practice

This test is one that comes with the robotpy project. It is a test that
is used to test the practice mode of the robot.

#### Test Unit Conversion

In the ```arm_test.py``` file there is a test for the unit conversion test. This 
is to test a helper method in the arm subsystem that converts from degrees to
encoder ticks. This test is a simple test that makes sure that the conversion
is correct.

### Make the tests run

```python
python robot.py test
```


## Make pretty
Use this to run the black auto-formatter.
```commandline
black .
```