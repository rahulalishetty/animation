# Easing and Springing

### Simple easing, long form
```
   var dx = targetX – object.x,
       dy = targetY – object.y;
   vx = dx * easing;
   vy = dy * easing;
   object.x += vx;
   object.y += vy;
```

### Simple easing, abbreviated form
   
```
   vx = (targetX - object.x) * easing;
   vy = (targetY - object.y) * easing;
   object.x += vx;
   object.y += vy;
```

### Simple easing, short form

```
   object.x += (targetX - object.x) * easing;
   object.y += (targetY – object.y) * easing;
```

### Simple spring, long form

```
   var ax = (targetX - object.x) * spring,
       ay = (targetY - object.y) * spring;
   vx += ax;
   vy += ay;
   vx *= friction;
   vy *= friction;
   object.x += vx;
   object.y += vy;
```

### Simple spring, abbreviated form

```
   vx += (targetX - object.x) * spring;
   vy += (targetY - object.y) * spring;
   vx *= friction;
   vy *= friction;
   object.x += vx;
   object.y += vy;
```

### Simple spring, short form

```
   vx += (targetX - object.x) * spring;
   vy += (targetY - object.y) * spring;
   object.x += (vx *= friction);
   object.y += (vy *= friction);
```

### Offset spring

```
   var dx = object.x – fixedX,
       dy = object.y – fixedY,
       angle = Math.atan2(dy, dx),
       targetX = fixedX + Math.cos(angle) * springLength,
       targetY = fixedX + Math.sin(angle) * springLength;
   //spring to targetX, targetY as above
```