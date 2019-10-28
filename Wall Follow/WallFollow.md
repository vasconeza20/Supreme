Angel Jimenez and James McCue: Wall Fallow Code

#include <kipr/botball.h>
//DECLARE VARIABLES
int l_motor = 0;
int r_motor = 3;
int f_sensor = 0;
int r_sensor = 5;
int pause = 665;
int highspeed = 70;
int midspeed = 55;
int lowspeed = 40;
int ftarget = 2400;
int starget = 2900;

int main()
{
      while(analog(f_sensor) <= ftarget){
            if (analog(r_sensor) > starget){
                left();
            }
            if (analog(r_sensor) < starget){
                right();
            }
    }
    ao();
    forward();
    msleep(100);
    turn();
    ao();
   
     while(analog(f_sensor) <= ftarget){
            if (analog(r_sensor) > starget){
                left();
            }
            if (analog(r_sensor) < starget){
                right();
            }
            if (analog(f_sensor) > ftarget){
                ao();
            }
    }
      
}

//FUNCTION DEFINITIONS//
void forward(){
    motor(l_motor,lowspeed);
    motor(r_motor,lowspeed);
    msleep(pause);
}
void turn(){
    motor(l_motor,highspeed);
    motor(r_motor,-highspeed);
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

