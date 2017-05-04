int pantalla=0;
int seleccion=0;
int turno=0;

PImage bg1;
PImage bg2;
PImage bg3;
PImage mon1;
PImage mon2;
PImage mon3;
PImage mon4;
PImage mon5;
PImage mon6;
int[] jugador1=new int[4];
int[] jugador2=new int[4];
int[] m1=new int[4];
int[] m2=new int[4];
int[] m3=new int[4];
int[] m4=new int[4];
int[] m5=new int[4];
int[] m6=new int[4];
void setup()
{


  m1[0]=3;
  m1[1]=3;
  m1[2]=15;
  m1[3]=1;

  m2[0]=3;
  m2[1]=3;
  m2[2]=15;
  m2[3]=2;

  m3[0]=3;
  m3[1]=4;
  m3[2]=15;
  m3[3]=1;

  m4[0]=4;
  m4[1]=3;
  m4[2]=15;
  m4[3]=2;

  m5[0]=3;
  m5[1]=2;
  m5[2]=15;
  m5[3]=1;

  m6[0]=3;
  m6[1]=2;
  m6[2]=15;
  m6[3]=2;

  size(600, 400); 
   
  bg1 = loadImage("P1.png");
  bg2 = loadImage("P2.png");
  bg3 = loadImage("P3.png");
  mon1 = loadImage("m1.png");
  mon2 = loadImage("m2.png");
  mon3 = loadImage("m3.png");
  mon4 = loadImage("m4.png");
  mon5 = loadImage("m5.png");
  mon6 = loadImage("m6.png");
  
}

void draw()
{
 
  
  

  switch (pantalla)
  {
  case 0:
   
    image(bg1,0,0);
    
    break;
  case 1:
    
    image(bg2,0,0);

    monster1();
    
    pushMatrix();
    translate(200, 0);
    monster2();
    popMatrix();

    pushMatrix();
    translate(400, 0);
    monster3();
    popMatrix();

    pushMatrix();
    translate(0, 200);
    monster4();
    popMatrix();

    pushMatrix();
    translate(200, 200);
    monster5();
    popMatrix();

    pushMatrix();
    translate(400, 200);
    monster6();
    popMatrix();
   
    break;
    
  case 2:
   
    image(bg3,0,0);
    textSize(24);
    text("J1 GLP1= A GLP2= S     J2 GLP1= L GLP2= K", 50, 370);
    
    pushMatrix();
    fill(255,0,0);
    rect(100,100,jugador1[2],30);
    popMatrix();
    
    pushMatrix();
    fill(255,0,0);
    rect(300,100,jugador2[2],30);
    popMatrix();
    
    pushMatrix();
    translate(100, 100);
    if (jugador1==m1)
    {
      monster1();
    } else if (jugador1==m2)
    {
      monster2();
    } else if (jugador1==m3)
    {
      monster3();
    } else if (jugador1==m4)
    {
      monster4();
    } else if (jugador1==m5)
    {
      monster5();
    } else if (jugador1==m6)
    {
      monster6();
    }
    popMatrix();

    pushMatrix();
    translate(400, 100);
    if (jugador2==m1)
    {
      monster1();
    } else if (jugador2==m2)
    {
      monster2();
    } else if (jugador2==m3)
    {
      monster3();
    } else if (jugador2==m4)
    {
      monster4();
    } else if (jugador2==m5)
    {
      monster5();
    } else if (jugador2==m6)
    {
      monster6();
    }
    popMatrix();


    if (jugador1[2]<=0)
    {
      fill(255);
      text("YOU WIN PRESS BAR", 220, 50);
    } else if (jugador2[2]<=0)
    {
      fill(255);
      text("YOU WIN PRESS BAR", 50, 50);
    }
  }
}

void  monster1()
{
image(mon1,0,0);  
}

void  monster2()
{
image(mon2,0,0);  
}

void  monster3()
{
image(mon3,0,0);  
}

void  monster4()
{
image(mon4,0,0);  
}

void  monster5()
{
image(mon5,0,0);  
}

void  monster6()
{
image(mon6,0,0);  
}

void keyPressed()
{
  if (keyCode==UP)
  {
    pantalla=1;
  }

  if (turno==0&&pantalla==2)
  {
    if (key=='a'||key=='A')
    {
      
      //GIFF
      jugador2[2]=jugador2[2]-(jugador1[0]-jugador2[3]);
      println(jugador2[2]);
      turno=1;
    }
    if (key=='s'||key=='S')
    {
      //image (golpe4,0,-150);
      jugador2[2]=jugador2[2]-(jugador1[1]-jugador2[3]);
      println(jugador2[2]);
      turno=1;
    }
  }
  if (turno==1&&pantalla==2)
  {
    if (key=='l'||key=='L')
    {
      //image (golpe1,0,-100);
      jugador1[2]=jugador1[2]-(jugador2[0]-jugador1[3]);
      println(jugador1[2]);
      turno=0;
    } 
    if (key=='k'||key=='K')
    {
      //image (golpe2,0,-100);
      jugador1[2]=jugador1[2]-(jugador2[1]-jugador1[3]);
      println(jugador2[2]);
      turno=0;
    }
  }

  if (jugador1[2]<=0||jugador2[2]<=0)
  {
    if (key==' ') {
      pantalla=0;
    }
  }
}

void mouseClicked()
{
  if (pantalla==1)
  {
    //Monster1
    if (mouseX>0&&mouseX<200&&mouseY>0&&mouseY<200)
    {
      if (seleccion==0)
      {
        jugador1=m1;
        seleccion=1;
        //println(jugador1);
        //println(seleccion);
      } else if (seleccion==1)
      {
        //P2
        jugador2=m1;
        //println(jugador2);
        pantalla=2;
      }
    }

    //Monster2
    if (mouseX>200&&mouseX<400&&mouseY>0&&mouseY<200)
    {
      if (seleccion==0)
      {
        jugador1=m2;
        seleccion=1;
        //println(jugador1);
      } else if (seleccion==1)
      {
        //P2
        jugador2=m2;
        //println(jugador2);
        pantalla=2;
      }
    }

    //Monster3
    if (mouseX>400&&mouseX<600&&mouseY>0&&mouseY<200)
    {
      if (seleccion==0)
      {
        jugador1=m3;
        seleccion=1;
        //println(jugador1);
        //println(seleccion);
      } else if (seleccion==1)
      {
        //P2
        jugador2=m3;
        //println(jugador2);
        pantalla=2;
      }
    }

    //Monster4
    if (mouseX>0&&mouseX<200&&mouseY>200&&mouseY<400)
    {
      if (seleccion==0)
      {
        jugador1=m4;
        seleccion=1;
      } else if (seleccion==1)
      {
        //P2
        jugador2=m4;
        pantalla=2;
      }
    }

    //Monster5
    if (mouseX>200&&mouseX<400&&mouseY>200&&mouseY<400)
    {
      if (seleccion==0)
      {
        jugador1=m5;
        seleccion=1;
      } else if (seleccion==1)
      {
        //P2
        jugador2=m5;
        pantalla=2;
      }
    }

    //Monster6
    if (mouseX>400&&mouseX<600&&mouseY>200&&mouseY<400)
    {
      if (seleccion==0)
      {
        jugador1=m6;
        seleccion=1;
      } else if (seleccion==1)
      {
        //P2
        jugador2=m6;
        pantalla=2;
      }
    }
  }
}
