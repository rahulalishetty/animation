# Conservation of Momentum

### Conservation of Momentum, in Straight Mathematical Terms
             
```
             (m0 - m1) × v0 + 2 × m1 × v1
   v0Final = ----------------------------
                        m0 + m1


             (m1 - m0) × v1 + 2 × m0 × v0
   v1Final = ----------------------------
                        m0 + m1
```

### Conservation of Momentum in JavaScript, with a Shortcut
   
```
   var vxTotal = vx0 – vx1;
   vx0 = ((ball0.mass - ball1.mass) * vx0 + 2 * ball1.mass * vx1) /
         (ball0.mass + ball1.mass);
   vx1 = vxTotal + vx0;
```