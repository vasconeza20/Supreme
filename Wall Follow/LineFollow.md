Angel Jimenez and James McCue: Line Follow Code

#include <kipr/botball.h>
//DECLARE VARIABLES
int l_motor = 0;
int r_motor = 3;
int f_sensor = 0;
int s_sensor = 5;
int pause = 700;
int highspeed = 90;
int midspeed = 55;
int lowspeed = 20;
int ftarget = 2400;
int starget = 100;
int servoport  = 0;
int servoposl = 100;
int servoposr = 1500;

int main()
{
   forward();
        
        
      while(analog(f_sensor) <= ftarget){
            if (analog(s_sensor) < starget){
                left();
                printf("going left");
            }
            if (analog(s_sensor) > starget){
                right();
                printf("going right");
            }
    }
    
    while(analog(f_sensor) >= ftarget){
    ao();
      wave();
    printf("waving");
    }
}

//FUNCTION DEFINITIONS//
void forward(){
    motor(l_motor,midspeed);
    motor(r_motor,midspeed);
    msleep(pause);
}
void left(){
    motor(l_motor,lowspeed);
    motor(r_motor,highspeed);
}
void right(){
    motor(l_motor,highspeed);
    motor(r_motor,lowspeed);
}
void wave (){
   enable_servo(servoport);
   set_servo_position(servoport, servoposl);
   set_servo_position(servoport, servoposr);
   disable_servo(servoport);
}
