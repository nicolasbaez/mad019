# mad019
basic casino loop

![mad019](https://github.com/nicolasbaez/mad019/blob/master/mad019.gif)

```processing
int cuadros=1;
float ancho;
float k=0;
int pasos=2048;
int periodo=0;
int rr=0;
int gg=0;
int bb=0;
int vMin=2;
int dColor=64;
void setup() {
  size(512, 256);
  background(255);
  ancho=width/8;
  noStroke();
}
void luz(float xx, float yy, float k) {
  for (float i=xx; i<ancho+xx; i+=ancho/cuadros) {
    for (float j=yy; j<ancho+yy; j+=ancho/cuadros) {
      rect(i, j, ancho/cuadros, ancho/cuadros);
    }
  }
}
void draw() {
  fill(255, 255, 255, 64);
  rect(0, 0, width, height);
  rr+=random(-dColor, dColor);
  if (rr<0) {
    rr+=2*dColor;
  }
  if (rr>255) {
    rr-=2*dColor;
  }
  gg+=random(-dColor, dColor);
  if (gg<0) {
    gg+=2*dColor;
  }
  if (gg>255) {
    gg-=2*dColor;
  }
  bb+=random(-dColor, dColor);
  if (bb<0) {
    bb+=2*dColor;
  }
  if (bb>255) {
    bb-=2*dColor;
  }
  fill(rr, gg, bb);
  luz(map(k, 0, pasos, 0, width-ancho), 0, k);
  luz(width-ancho, map(k, 0, pasos, 0, height-ancho), k);
  luz(map(k, 0, pasos, width-ancho, 0), height-ancho, k);
  luz(0, map(k, 0, pasos, height-ancho, 0), k);
  if (k<=pasos/2) {
    k+=map(k, 0, pasos, vMin, ancho/cuadros);
  }
  if (k>pasos/2) {
    k+=map(k, 0, pasos, ancho/cuadros, vMin);
  }
  if (k>pasos) {
    k=0;
    periodo++;
  }
  if (periodo>=2&&periodo<4) {
    saveFrame("gif/mad019-######.png");
  }
}
```
