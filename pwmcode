# SIT210_Task7.3D_RPiPWM

import RPi.GPIO as GPIO
import time


GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)

GPIO_TRIGGER = 23
GPIO_ECHO = 22

GPIO.setup(25, GPIO.OUT)
GPIO.setup(GPIO_TRIGGER, GPIO.OUT)
GPIO.setup(GPIO_ECHO, GPIO.IN)

def distance():
    GPIO.output(GPIO_TRIGGER, True)
    time.sleep(0.00001)
    GPIO.output(GPIO_TRIGGER, False)
    start = time.time()
    stop = time.time()
    while GPIO.input(GPIO_ECHO) == 0:
          start = time.time()

    while GPIO.input(GPIO_ECHO) == 1:
          stop = time.time()

    measuredTime = stop - start
    distance = (measuredTime * 34000) / 2

    return distance
p = GPIO.PWM(25, 50)
p.start(0);

if __name__ == '__main__':
    try:
        while True:
              dist = distance()
              print ("Distance : {0:5.1f}cm".format(dist))
              if dist <= 10:
                 for dc in range(50, 101, 5):
                     p.ChangeDutyCycle(dc)
                     time. sleep(0.1)

              elif dist <= 30 and dist >= 10:
                  for dc in range(11, -1, -5):
                      p.ChangeDutyCycle(dc)
                      time. sleep(0.1)
              else:
                   for dc in range(0, -1, -5):
                       p.ChangeDutyCycle(dc)
                       time.sleep(0.1)
        except KeyboardInterrupt:
           print("Distance stopped")
           p.stop()
           GPIO.cleanup()
                       
    
