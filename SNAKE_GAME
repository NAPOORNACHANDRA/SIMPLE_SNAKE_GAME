#include<iostream>
#include<windows.h>
#include<conio.h>
using namespace std;
bool gameover;
#define KEY_UP 72
#define KEY_DOWN 80
#define KEY_LEFT 75
#define KEY_RIGHT 77
    //defining all the global variables
    const int width=25; 
    const int height=25;
     int snake_x ,snake_y;
     int fruit_x, fruit_y;
     int tailx[100] , taily[100], tail_len, score, highest_score;
     enum direction{Stop=0,Left,Right,Up,Down};
     direction dir;

 //initializing the game 
 void setup(){
     gameover=false;
      snake_x = width / 2;
      snake_y = height / 2;
     fruit_x = rand() % width;
     fruit_y = rand() % height;
     dir=Stop;
     score=0;
     //setting all the paremters
 }
 //function for drawing table,snake,fruit,and projecting score.
void draw(){
   
    system("cls");
    
    if(fruit_x==0){
    fruit_x=fruit_x+1;
    }
    else if(fruit_y==0){
        fruit_y=fruit_y+1;
    }
    else if(fruit_x==width||fruit_x==width-1){
    fruit_x=fruit_x-2;
    }
    else if(fruit_y==height||fruit_y==height-1){
        fruit_y=fruit_y-2;
    }
   
    for(int i=0;i<width;i++){
        for(int j=0;j<height;j++){
            
            if(j==0||j==height-1||i==0||i==width-1){
                cout<<"*";
            }
    
             else if(j!=0&&i!=width-1&&j!=height-1&&i!=0){
                  if(i==snake_x&&j==snake_y){
                 cout<<"O";
                }
                
                else if (i==fruit_x&&j==fruit_y){
                    cout<<"F";
                }
                
                else
            {
                bool print = false;
                for (int k = 0; k <tail_len; k++)
                {
                    if (tailx[k] == i && taily[k] == j)
                    {
                        cout << "o";
                        print = true;
                    }
                }
                if (!print)
                    cout << " ";
            }
             }
             
            
            
            
        }
        cout<<endl;
    }
    cout << endl;
    cout << "Score:" << score << endl;
    cout<<  endl;
    cout<<  endl;
    cout<< "<------Highest Score :" <<highest_score<<" ------>";
    }
//updating the highest score
void Highest_score(){
     highest_score=100;
    if(score>=highest_score)
    highest_score=score;

}
void Input()
//taking the input from keyboard
{
    if (_kbhit())
    {
        switch(getch()) {
        case KEY_UP:
         dir=Up;//key up
            break;
        case KEY_DOWN:
        dir=Down;   // key down
            break;
        case KEY_LEFT:
        dir=Left;  // key left
            break;
        case KEY_RIGHT:
            dir=Right;  // key right
            break;
        case 'x':
            gameover = true;
            break;
        }
    }
}
void Logic()
{   //storing the positions of tail segments and mving it forward
    int past_x = tailx[0];
    int past_y = taily[0];
    
    tailx[0] = snake_x;
    taily[0] = snake_y;
    int ppast_x, ppast_y;
    for (int i = 1; i <tail_len; i++)
    {
        ppast_x = tailx[i];
        ppast_y = taily[i];
        tailx[i] = past_x;
        taily[i] = past_y;
        past_x = ppast_x;
        past_y= ppast_y;
    }
    switch (dir)
    {
    case Up:
        snake_x--;
        break;
    case Down:
        snake_x++;
        break;
    case Left:
        snake_y--;
        break;
    case Right:
        snake_y++;
        break;
    default:
        break;
    }
    //use this for tough level if it touches the wall then the game is over
    //if (x > width || x < 0 || y > height || y < 0)
    //  gameOver = true;
    if (snake_x >= width-1) snake_x = 1; else if (snake_x <= 0) snake_x = width - 2;
    if (snake_y >= height-1) snake_y = 1; else if (snake_y <= 0) snake_y = height - 2;
 
    for (int i = 0; i < tail_len; i++)
        if (tailx[i] == snake_x && taily[i] == snake_y)
            gameover = true;
 
    if (snake_x == fruit_x && snake_y == fruit_y)
    {
        score += 10;
        fruit_x = rand() % width;
        fruit_y = rand() % height;
        tail_len++;
    }
}
int main()
{
    setup();
    while (!gameover)
    {  
        draw();
        Input();
        Logic();
        Highest_score();

        Sleep(30); //sleep(10);
    }
    cout<<endl;
    cout<<endl;
    return 0;
}
