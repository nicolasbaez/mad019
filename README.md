# mad019
basic casino loop

![mad019](https://github.com/nicolasbaez/mad019/blob/master/mad019.gif)

```processing
int cuadros=2;
float ancho;
float k=0;
int pasos=1024;
int periodo=0;
void setup() {
  size(512, 256);
  background(255);
  ancho=width/16;
  noStroke();
}
void luz(float xx, float yy, float k) {
  for (float i=xx; i<ancho+xx; i+=ancho/cuadros) {
    for (float j=yy; j<ancho+yy; j+=ancho/cuadros) {
      fill(random(map(sin(radians(map(k, 0, pasos, 0, 360))), -1, 1, 128, 255)), random(map(sin(radians(map(k, 0, pasos, 0, 360))), -1, 1, 255, 128)), random(map(cos(radians(map(k, 0, pasos, 0, 360))), -1, 1, 128, 255)));
      rect(i, j, ancho/cuadros, ancho/cuadros);
    }
  }
}
void draw() {
  fill(255, 255, 255, 16);
  rect(0, 0, width, height);
  luz(map(k, 0, pasos, 0, width-ancho), 0, k);
  luz(width-ancho, map(k, 0, pasos, 0, height-ancho), k);
  luz(map(k, 0, pasos, width-ancho, 0), height-ancho, k);
  luz(0, map(k, 0, pasos, height-ancho, 0), k);
  k+=ancho/cuadros;
  if (k>pasos) {
    k=0;
    periodo++;
  }
  if (periodo>=2&&periodo<=4) {
    saveFrame("gif/mad019-######.png");
  }
}
```
