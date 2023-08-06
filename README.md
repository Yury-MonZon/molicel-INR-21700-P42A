# This is a very simple voltage to capacity(percent) function for Molicel INR-21700-P42A with 20A discharge current

```
#include <stdio.h>
#include <math.h>

int get_capacity(float voltage)
{
    float result = 0.0;
    if (voltage >= 3.78) result = 100;
    else if (voltage <= 3.0) result = 26.75*voltage - 69.55;
    else result = 218.9973 - 218.1101*voltage + 49.31891*voltage*voltage;
               
    return (int)result;
}


int main()
{
    
    float x;
    
    int y;
    
    for (int v = 4200; v >= 2600; v -= 10)
    {
        x = (float)v/1000;
        y = get_capacity(x);
        printf("%f = %d%%\n", x, y);
    }
    return 0;
}

```

Output:
```
4.200000 = 100%
4.100000 = 100%
4.000000 = 100%
3.900000 = 100%
3.800000 = 100%
3.700000 = 87%
3.600000 = 72%
3.500000 = 59%
3.400000 = 47%
3.300000 = 36%
3.200000 = 26%
3.100000 = 16%
3.000000 = 10%
2.900000 = 8%
2.800000 = 5%
2.700000 = 2%
2.600000 = 0%
```
