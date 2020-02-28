#include <FEHLCD.h>
#include <FEHUtility.h>
#include <FEHServo.h>
#include <FEHMotor.h>

FEHServo hand(FEHServo::Servo0);
FEHMotor arm(FEHMotor::Motor2, 5.0);


void starting_position();

void arm_horizontal();

int main(void)
{
    hand.SetMin(500);
    hand.SetMax(2314);

    float x,y, i=0;

    LCD.Clear(FEHLCD::Black);
    LCD.SetFontColor(FEHLCD::White);

    while(true)
    {
        if (i<1)
        {
            LCD.WriteLine("REady & Waiting...");
            i += 2;
        }

        if (LCD.Touch(&x, &y))
        {
            LCD.Clear();
            LCD.WriteLine("Beginning Warmup...");

            Sleep(1.0);

            starting_position();

            Sleep(2.0);

            hand.SetDegree(0);

            Sleep(2.0);

            arm_horizontal();

            Sleep(100);

            LCD.WriteLine("Finished with Warmup");
        }
    }

    return 0;
}

void starting_position()
{
    float start_time;

    hand.SetDegree(112);

    Sleep(500);

    start_time=TimeNow();

    while (TimeNow()-start_time<2.0)
    {
        arm.SetPercent(100);
    }

    arm.Stop();

    LCD.WriteLine("Ready to Go!!!!");

}

void arm_horizontal()
{
    float start_time;

    hand.SetDegree(40);

    start_time=TimeNow();

    while(TimeNow()-start_time < 1.75)
    {
        arm.SetPercent(-100);
    }

    arm.Stop();

    LCD.WriteLine("Arm is Horizontal");
}
