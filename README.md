# tictactoe
game tictactoe  in c++ = by DILJEET KAKKAR
#include<iostream.h>
#include<conio.h>
#include<stdlib.h>
#include<string.h>
#include<stdio.h>
#include<dos.h>
 char a[3][3]; int filleda[9];  int i,j,m;
 int winstatus=0,drawstatus=0;
 int userpos,compos,user1pos,user2pos;
 int fillcounter=0;
 void singleuser();
 void twouser();
 void display();
 void check();
 void checktwouser();
 void details();
void main()
{      clrscr();
int mode;
 starting:
cout<<endl<<"                      WELCOME TO TIC TAC TOE" <<endl<<endl;
 cout<<" ENTER THE GAME MODE(1 or 2):             "<<endl;
cout<<"1. SINGLE USER "<<endl<<"2.TWO USERS"<<endl<<"3. EXIT"<<endl;

cin>>mode;
if(mode==1)
{
singleuser();
delay(4000);
}
else if(mode==2)
{
twouser();
delay(4000);
}
else if(mode==3)
{exit(0);
}
else
{ clrscr();
cout<<endl<<endl<<"WRONG OPTION SELECTED ENTER 1,2 OR 3 ONLY";
goto starting;
}
  details();
  getch();
}


void singleuser()
{          clrscr();
cout<<"                    WELCOME TO SINGLE USER TIC TAC TOE" ;
cout<<endl<<"<NOTE:EMPTY PLACES ARE REPRESENTED BY -9>"<<endl<<endl ;
 for(i=0;i<3;i++)
 { for( j=0;j<3;j++)
  { a[i][j]='*';
   cout<<"\t"<<a[i][j]<<"\t";
  }
  cout<<endl;
 }
cout<<endl<<"instructions : "<<endl<<"  USER REPRESENTS 0 "<<endl<<"  COMPUTER REPRESENTS 1" ;
cout<<endl<< "please entre one of the following positions  0 to 9  and the same position cant entetred again ,represented as:"<<endl<<endl;
int p=1;
 for( i=0;i<3;i++)
 { for( j=0;j<3;j++)
  { cout<<"\t"<<p<<"\t";
	    p++;
  }
  cout<<endl;
 }
 fflush(stdin);
while(winstatus!=1 || drawstatus!=1)
{  fflush(stdin);
 if(winstatus==1)
 break;

	if(fillcounter==9)
   { cout<<endl<<"ITS A DRAW................";
     drawstatus=1;  break;
   }
	 //input positions of user
   inputuser:
   cout<<endl<<"entre user position: ";cin>>userpos;
   for( m=0;m<=fillcounter;m++)
   if(userpos==filleda[m])
   {
    cout<<endl<<"user input position invalid input again " ;
     goto inputuser;
   }
   filleda[fillcounter]=userpos;
   fillcounter++;
   if( userpos>=1 && userpos<=3)
   a[0][userpos-1]=48;
   if( userpos>3&&userpos<=6)
   a[1][userpos-4]=48;
   if(userpos>6&& userpos<=9)
   a[2][userpos-7]=48;
   clrscr();
    cout<<endl<<"user position:";
    display();
    check();
     fflush(stdin);
 if(winstatus==1)
 break;

	// computer position input and assigning

   inputcomputer:
   srand(time(NULL));
   compos=rand()%9 ;
   for(int m=0;m<=fillcounter;m++)
   if(compos==filleda[m])
   { goto inputcomputer;
   }
   filleda[fillcounter]=compos;
   fillcounter++;
   if( compos>=1 && compos<=3)
   a[0][compos-1]=49;
   if( compos>3 && compos<=6)
   a[1][compos-4]=49;
   if(compos>6 && compos<=9)
   a[2][compos-7]=49;
    fflush(stdin);  clrscr();
    cout<<endl<<" computers position=";
    display();
   check();
 }
}

void twouser()
{          clrscr();    fflush(stdin);
cout<<"                    WELCOME TO TWO USER TIC TAC TOE" ;
cout<<endl<<"<NOTE:EMPTY PLACES ARE REPRESENTED BY -9>"<<endl<<endl ;
 for(i=0;i<3;i++)
 { for( j=0;j<3;j++)
  { a[i][j]=42;
   cout<<"\t"<<a[i][j]<<"\t";
  }
  cout<<endl;
 }
cout<<endl<<"instructions : "<<endl<<"  USER1 REPRESENTS 0 "<<endl<<"  USER2 REPRESENTS 1" ;
cout<<endl<< "please entre one of the following positions  0 to 9  and the same position cant entetred again ,represented as:"<<endl<<endl;
int p=1;
 for( i=0;i<3;i++)
 { for( j=0;j<3;j++)
  { cout<<"\t"<<p<<"\t";
	    p++;
  }
  cout<<endl;
 }
 fflush(stdin);
while(winstatus!=1 || drawstatus!=1)
{  fflush(stdin);
 if(winstatus==1)
 break;

	if(fillcounter==9)
   { cout<<endl<<"ITS A DRAW................";
     drawstatus=1;  break;
   }

	 //input positions of user1
   inputuser1:
   cout<<endl<<"entre user1 position: ";cin>>user1pos;
   for( m=0;m<=fillcounter;m++)
   if(user1pos==filleda[m])
   {
    cout<<endl<<"user1 input position invalid input again " ;
     goto inputuser1;
   }
   filleda[fillcounter]=user1pos;
   fillcounter++;
   if( user1pos>=1 && user1pos<=3)
   a[0][user1pos-1]=48;
   if( user1pos>3&&user1pos<=6)
   a[1][user1pos-4]=48;
   if(user1pos>6&& user1pos<=9)
   a[2][user1pos-7]=48;
   fflush(stdin);
   clrscr();
   cout<<endl<<"user1 position:"<<endl;
   display();
   checktwouser();

   fflush(stdin);
 if(winstatus==1)
 break;

	  // input user2 and assigning position
   inputuser2:
    cout<<endl<<"entre user2 position: ";cin>>user2pos;
   for(int m=0;m<=fillcounter;m++)
   if(user2pos==filleda[m])
   {
   cout<<endl<<" user2 pos invalid entre again";
   goto inputuser2;
   }
   filleda[fillcounter]=user2pos;
   fillcounter++;
   if( user2pos>=1 && user2pos<=3)
   a[0][user2pos-1]=49;
   if( user2pos>3 && user2pos<=6)
   a[1][user2pos-4]=49;
   if(user2pos>6 && user2pos<=9)
   a[2][user2pos-7]=49;
    fflush(stdin);
    clrscr();
    cout<<endl<<"user2 position"<<endl;
    display();
   checktwouser();
 }
}


void check()
{   fflush(stdin);
if( (a[0][0]==a[0][1]&& a[0][2]==a[0][1]&& a[0][0]==48) || (a[1][0]==a[1][1]&& a[1][2]==a[1][1]&& a[1][0]==48)  || (a[2][0]==a[2][1]&& a[2][2]==a[2][1]&& a[2][2]==48)  ||
    (a[0][0]==a[1][1]&& a[2][2]==a[1][1]&& a[0][0]==48) || ( a[0][2]==a[1][1]&& a[2][0]==a[1][1]&& a[1][1]==48) ||
    (a[0][0]==a[1][0]&& a[1][0]==a[2][0]&& a[0][0]==48) || (a[0][1]==a[1][1]&& a[1][1]==a[2][1]&& a[1][1]==48)  || (a[0][2]==a[1][2] && a[1][2]==a[2][2]&& a[2][2]==48)
  )
 {   clrscr(); winstatus=1;
 cout<<endl<<endl<<" USER WINS CONGRATULATIONS";    display();

 }
if( (a[0][0]==a[0][1]&& a[0][2]==a[0][1]&& a[0][0]==49) || (a[1][0]==a[1][1]&& a[1][2]==a[1][1]&& a[1][0]==49)  || (a[2][0]==a[2][1]&& a[2][2]==a[2][1]&& a[2][2]==49)  ||
    (a[0][0]==a[1][1]&& a[2][2]==a[1][1]&& a[0][0]==49) || ( a[0][2]==a[1][1]&& a[2][0]==a[1][1]&& a[1][1]==49) ||
    (a[0][0]==a[1][0]&& a[1][0]==a[2][0]&& a[0][0]==49) || (a[0][1]==a[1][1]&& a[1][1]==a[2][1]&& a[1][1]==49)  || (a[0][2]==a[1][2] && a[1][2]==a[2][2]&& a[2][2]==49)
  )
 { clrscr();    winstatus=1;
 display();
  cout<<endl<<endl<<" ooops   you lost the game"<<endl<<"       COMPUTER WINS";

  }
}

void checktwouser()
{   fflush(stdin);
if( (a[0][0]==a[0][1]&& a[0][2]==a[0][1]&& a[0][0]==48) || (a[1][0]==a[1][1]&& a[1][2]==a[1][1]&& a[1][0]==48)  || (a[2][0]==a[2][1]&& a[2][2]==a[2][1]&& a[2][2]==48)  ||
    (a[0][0]==a[1][1]&& a[2][2]==a[1][1]&& a[0][0]==48) || ( a[0][2]==a[1][1]&& a[2][0]==a[1][1]&& a[1][1]==48) ||
    (a[0][0]==a[1][0]&& a[1][0]==a[2][0]&& a[0][0]==48) || (a[0][1]==a[1][1]&& a[1][1]==a[2][1]&& a[1][1]==48)  || (a[0][2]==a[1][2] && a[1][2]==a[2][2]&& a[2][2]==48)
  )
 {   clrscr(); winstatus=1;
 cout<<endl<<endl<<" USER1 WINS CONGRATULATIONS";    display();

 }
if( (a[0][0]==a[0][1]&& a[0][2]==a[0][1]&& a[0][0]==49) || (a[1][0]==a[1][1]&& a[1][2]==a[1][1]&& a[1][0]==49)  || (a[2][0]==a[2][1]&& a[2][2]==a[2][1]&& a[2][2]==49)  ||
    (a[0][0]==a[1][1]&& a[2][2]==a[1][1]&& a[0][0]==49) || ( a[0][2]==a[1][1]&& a[2][0]==a[1][1]&& a[1][1]==49) ||
    (a[0][0]==a[1][0]&& a[1][0]==a[2][0]&& a[0][0]==49) || (a[0][1]==a[1][1]&& a[1][1]==a[2][1]&& a[1][1]==49)  || (a[0][2]==a[1][2] && a[1][2]==a[2][2]&& a[2][2]==49)
  )
 { clrscr();    winstatus=1;
 display();
 cout<<endl<<endl<<" ooops   user1 lost the game"<<endl<<"       user2 WINS";
  }


}

void display()
{   fflush(stdin);  cout<<endl;
 for(i=0;i<3;i++)
  { for( j=0;j<3;j++)
  {
   cout<<"\t"<<a[i][j]<<"\t";
  }
   cout<<endl;
  }
}
void details()
{clrscr();
cout<<"********************************************************************************";
cout<<endl<<endl<<endl<<endl<<endl<<"                          ";
cout<<"  THANKS FOR PLAYING  TIC TAC TOE ";
cout<<endl<<endl<<endl<<endl<<endl<<endl<<endl<<endl<<endl<<endl<<endl<<endl;
cout<<"                                     made by:-DILJEET KAKKAR";
cout<<endl<<"                             roll no:-1250393(btech/cse/2k12"<<"/393)";
cout<<endl<<"                             college:-SBSSTC"<<endl;
cout<<"****************************************************************************";
}

