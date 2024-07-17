#include <iostream>
using namespace std;


//Tic Tac Toe structure
char space[3][3]={{'1','2','3'},{'4','5','6'},{'7','8','9'}};
int row,column;
char token= 'x';
//No of players
string p1=" ";
string p2=" ";
bool tie=false;

//Creating functions
void function_1()
{
    //Creating structure and adding elements
    cout<<"     |     |     \n";
    cout<<"  "<<space[0][0]<<"  |  "<<space[0][1]<<"  |  "<<space[0][2]<<" \n";
    cout<<"__ __|__ __|__ __\n";
    cout<<"     |     |     \n";
    cout<<"  "<<space[1][0]<<"  |  "<<space[1][1]<<"  |  "<<space[1][2]<<" \n";
    cout<<"__ __|__ __|__ __\n";
    cout<<"     |     |     \n";
    cout<<"  "<<space[2][0]<<"  |  "<<space[2][1]<<"  |  "<<space[2][2]<<" \n";
    cout<<"     |     |     \n";
}

void function_2()
{
    int digit;
    if(token=='x')
    {
        cout<<p1<<" enter digit : ";
        cin>>digit;
    }
    if(token=='0')
    {
        cout<<p2<<" enter digit : ";
        cin>>digit;
    }
    
    //assining digits
    if(digit==1)
    {
        row=0;column=0;
    }
    if(digit==2)
    {
        row=0;column=1;
    }
    if(digit==3)
    {
        row=0;column=2;
    }
    if(digit==4)
    {
        row=1;column=0;
    }
    if(digit==5)
    {
        row=1;column=1;
    }
    if(digit==6)
    {
        row=1;column=2;
    }
    if(digit==7)
    {
        row=2;column=0;
    }
    if(digit==8)
    {
        row=2;column=1;
    }
    if(digit==9)
    {
        row=2;column=2;
    }
    else if(digit<1 || digit>9)
    {
        cout<<"Invalid !!"<<endl;
    }
    
    //if condition
    if(token=='x' && space[row][column]!='x' && space[row][column]!='0')
    {
        space[row][column]='x';
        token='0';
    }
    else if(token=='0' && space[row][column]!='x' && space[row][column]!='0')
    {
        space[row][column]='0';
        token='x';
    }
    else
    {
        cout<<"There is no empty space!!"<<endl;
        function_2();
    }
    
    function_1();
}

bool function_3()
{
    //row win or column win
    for(int i=0;i<3;i++)
    {
        if(space[i][0]==space[i][1] && space[i][0]==space[i][1] //rows
                            ||
           space[0][i]==space[1][i] && space[0][i]==space[2][i] //columns 
           )
        return true;
    }
    
    //diagonal win
    if(space[0][0]==space[1][1] && space[1][1]==space[2][2] 
                    ||
       space[0][2]==space[1][1] && space[1][1]==space[2][0]    
       )
    return true; 
    
    //game is still going on
    for(int i=0;i<3;i++)
    {
        for( int j=0;j<3;j++)
        {
            if(space[i][j]!='x' && space[i][j]!='0')
            return false;
        }
    }
    tie=true;
    return false;
}

int main()
{
    cout<<"Enter the name of the first player : ";
    getline(cin,p1);
    cout<<"Enter the name of the second player : ";
    getline(cin,p2);
    cout<<p1<<" is player 1 so he/she will play first \n";
    cout<<p2<<" is player 2 so he/she will play second \n";
    
    while(!function_3())
    {
        function_1();
        function_2();
        function_3();
    }
    
    if(token=='x' && tie==false)
    {
        cout<<p2<<" Wins!!"<<endl;
    }
    else if(token=='0' && tie==false)
    {
        cout<<p1<<" Wins!!"<<endl;
    }
    else
    {
        cout<<"It's a draw!!";
    }
}
