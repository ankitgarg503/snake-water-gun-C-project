# snake-water-gun-C-project
Snake Water Gun is one of the famous two-player game played by many people. A game in which the player randomly chooses any of the three forms i.e. snake, water, and gun .This C project is to build a game for a single player that plays with the computer.


// Complete Project Coding


	#include <stdio.h>
	#include <string.h>
	#include <time.h>
	#include<stdlib.h>
	#include <windows.h>
    #include <unistd.h>
	    
	#define COLOR_RESET  "\x1b[0m"
	#define COLOR_RED    "\x1b[31m"
	#define COLOR_GREEN  "\x1b[32m"
	#define COLOR_YELLOW "\033[31;44m"

	#define reset "\x1B[0m"
	#define bold "\x1B[1m"
void takeinput(char ch[50]);
struct user
{
    char fullname[50];
    char phone[50];
    char email[50];
    char password[50];
};
void login()
{
	char email1[50];
        char password3[50];
        struct user usr;
    //change colour of terminal
    FILE *fp;
    int opt,usrfound=0;
    struct user user;
    char password2[50];
    printf("\n\t\t\t\t------------------WELCOME-------------------");
    printf("\n\t\t\t\t             Please Choose Your Operation");
    printf("\n\t\t\t\t1.Signup");
    printf("\n\t\t\t\t2.Login");
    printf("\n\t\t\t\t3.Exit");
    printf("\n\nYour Choice\t");
    scanf("%d",&opt);
    fgetc(stdin);
    switch(opt)
    {
        case 1:
        // add function to clear screen
        printf("\n\t\tEnter your full name: ");
        takeinput(user.fullname);
        printf("\t\tEnter your phone number: ");
        takeinput(user.phone);
        printf("\t\tEnter your email: ");
        takeinput(user.email);
        printf("\t\tEnter your password: ");
        takeinput(user.password);
        printf("\t\tConfirm your password:");
        takeinput(password2);
        // check both the password are same or not
        if(!strcmp(user.password,password2))
        {
            fp=fopen("Users.dat","a+");
            fwrite(&user,sizeof(struct user),1,fp);
            if(fwrite!=0)
            printf("\n   User Sign Up successfull   ");
            else
            printf("\n\nSorry!!,Something went wrong: ");
            fclose(fp);
        }
        else
        {
            printf("\n\nPassword do not matched, Try again");
        }
         printf("\n ENTER ANY NUMBER TO GO TO MAIN MENU\n");
	    	getch();
	    	menu();
		    
        break;
        
        
        case 2:
       
        printf("\n\t\tEnter your email: ");
        takeinput(email1);
        printf("\t\tEnter your password: ");
        takeinput(password3);
        fp=fopen("Users.dat","r");
        while(fread(&usr,sizeof(struct user),1,fp))
        {
            if(!(strcmp(usr.email,email1)))
            {
                if(!(strcmp(usr.password,password3)))
                {
                   // system("clr");// to clear screen
                    printf("\n\t\t\t\t\t WELCOME %s",usr.fullname);
                    printf("\n\n\t\t|Full Name:\t%s",usr.fullname);
                    printf("\n\t\t|Email : \t%s",usr.email);
                    printf("\n\t\t|Contact no. : \t%s",usr.phone);
                }
                else
                printf("\n\n\t\tInvalid gmail or Password!!");
                
            }
            
                usrfound=1;
            
        }
        if(!usrfound)
        {
            printf("\n\n\t\tUser is not registered!!");
        }
        fclose(fp);
         printf("\n ENTER ANY NUMBER TO GO TO MAIN MENU\n");
	    	getch();
	    	menu();
		    
        break;
        case 3:
        printf("----------------END------------------------");
        exit(0);
        
        break;
        
    }
    
}

	void Exit()
		{
		  printf("\n You are Sucessfully Exit From the Game\n ");
		  exit(0);
		  //getch();
		}
	  void Result(int win,int drawn,int loose)
		{
			 if (win==2 && drawn ==1 && loose==2 || drawn==5 ||loose==win)
		    {
		        printf("THIS GAME IS DRAWN SO PLEASE TRY AGAIN  WIN=%d  LOOSE =%d  DRAW=%d",win,drawn,loose);
		    }
		    else if (win==3 || (win==2 && drawn==2) || (win==1 && drawn==4)|| (win==2 && drawn==3)||win==4||win==5)
		    {
		        printf("CONGRATULATION, YOU WON HIS GAME WITH TOTAL POINT %d ",win);
		    }
		    
		    
		    else
		    {
		        printf("OOPS, YOU LOOSE THIS GAME PLEASE TRY AGAIN\n");
		    }
		    printf("\n ENTER ANY NUMBER TO GO TO MAIN MENU\n");
	    	getch();
	    	menu();
		    
			
		}
				void Rules()
		{
			
			printf(COLOR_GREEN   "\t");
			//printf(COLOR_YELLOW   "\t");
			printf("\n\t\t\t--------------------------------------------------------------------\n");
			printf(COLOR_GREEN"\t\t\t|Snake Water Gun is one of the famous\t\t\t\t   | \n\t\t\t|two-player game played by many people.");
			printf("  A game in which the player|\n\t\t\t|randomly chooses any of the three forms i.e. snake, water, and gun| "); 
			printf("\n\t\t\t--------------------------------------------------------------------");
			printf("\n\t\t\t--------------------------------------------------------------------");
			printf("\n\t\t\t|This C project is to build a game for a\t\t\t   | \n\t\t\t|single player that plays with the computer\t\t\t   |" );
			printf("\n\t\t\t--------------------------------------------------------------------\n");
			printf(COLOR_RED   "\t");
			printf("\n\t\t\t**************\t*************\t*****************\t************\t**************");
			printf(COLOR_RESET "\t");
            printf("\n\n\t\t\t\tFollowing are the rules of the game:");
            printf(COLOR_GREEN   "\t");
            printf("\n\n\t\t\t\tSnake vs. Water: Snake drinks the water hence wins.");
            printf("\n\t\t\t\tWater vs. Gun: The gun will drown in water, hence a point for water");
            printf("\n\t\t\t\tGun vs. Snake: Gun will kill the snake and win.");
               printf(COLOR_RESET "\t");
           // fclose(fptr);
           // printf(COLOR_YELLOW   "\t");
	    	printf("\n ENTER ANY NUMBER TO GO TO MAIN MENU\n");
	    //	printf(COLOR_RESET "\t");
	    	getch();
	    	menu();

		}
	void Game()
	{
		 int i=0;
	    char name[100];
	    static int win=0;
	    static int drawn=0;
	    static int loose=0;
	    int n;
	    printf("\t\t\tSNAKE=0,WATER=1,GUN=2\n");
	
	    printf("\t\t\tENTER Your Name\n");
	    scanf("%s",&name);
	    while(i<5)
	    {   
		    srand(time(NULL));
		    int s = rand()%3;
		    printf("\t\t\t%s TURN\n", name);
		    scanf("%d", &n);
		    printf("\t\t\t%s:%d\n", name, n);
		    printf("\t\t\tPLAYER 2 TURN\n");
		    printf("\t\t\tCOMPUTER Choice:%d\n", s);
		    
		   if(n>2)
		    {
		    	printf("\n Invalid Choice!\n");
		    	continue;
			}
			else
		    if (n == s && s==0)
		    {
		    	printf("\t\t\t%s and Computer Enter Snake \n  ",name);
		    	printf(COLOR_RED   "\t");
		        printf("\t\t\tMATCH DRAWN & GET 0 POINT\n");
		        printf(COLOR_RESET "\t");
		        printf("\n\t\t\t************  ***************  **************\n\n");
		        drawn++;
		
		       
		    }
		    else
			 if (n == s && s==1)
		    {
		    	printf("\t\t\t%s and Computer Enter Water \n  ",name);
		    	printf(COLOR_RED   "\t");
		        printf("\t\t\tMATCH DRAWN & GET 0 POINT\n");
		        printf(COLOR_RESET "\t");
		        printf("\n\t\t\t************  ***************  **************\n\n");
		        drawn++;
		
		       
		    }
		     else
			 if (n == s && s==2)
		    {
		    	printf("\t\t\t%s and Computer Enter Gun \n  ",name);
		    	printf(COLOR_RED   "\t");
		        printf("\t\t\tMATCH DRAWN & GET 0 POINT\n");
				printf(COLOR_RESET "\t");		        
		        printf("\n\t\t\t************  ***************  **************\n\n");
		        drawn++;
		
		       
		    }
		    else if (n == 0 && s == 1 || n == 1 && s == 2 || n == 2 && s == 0 || n==0 && s==2 || n==1 && s==0  || n==2 && s==1)
		    {
		    	if(n==0 && s==1)
		    	{
		    	   printf("\t\t\t%s Enter Snake and Computer Enter Water\n",name);	
		    	   printf(COLOR_RED   "\t");
		           printf("\t\t\t%s WIN THE GAME AND GET 1 POINT\n", name );
				   printf(COLOR_RESET "\t");		           
		           printf("\n\t\t\t************  ***************  **************\n\n");
		           win++;
				}
				else
				if(n==0 && s==2)
		    	{
		    	   printf("\t\t\t%s Enter Snake and Computer Enter Gun\n",name);
				   printf(COLOR_RED   "\t");	
		           printf("\t\t\tComputer Win THE GAME AND GET 1 POINT\n" );
				   printf(COLOR_RESET "\t");		           
		           printf("\n\t\t\t************  ***************  **************\n\n");
		           loose++;
				}
				else
				if(n==1 && s==2)
		    	{
		    	   printf("\t\t\t%s Enter Water and Computer Enter Gun\n",name);
				   printf(COLOR_RED   "\t");	
		           printf("\t\t\t%s Win THE GAME AND GET 1 POINT\n",name);	
				   printf(COLOR_RESET "\t");	           
		           printf("\n\t\t\t************  ***************  **************\n\n");
		          // win++;
				}
				else
				if(n==1 && s==0)
		    	{
		    	   printf("\t\t\t%s Enter Water and Computer Enter Snake\n",name);	
		    	   printf(COLOR_RED   "\t");
		           printf("\t\t\tComputer Win THE GAME AND GET 1 POINT\n" );
				   printf(COLOR_RESET "\t");		           
		            printf("\n\t\t\t************  ***************  **************\n\n");
		            loose++;
				}
				else
				if(n==2 && s==0)
		    	{
		    	   printf("\t\t\t%s Enter Gun and Computer Enter Snake\n",name);
				   printf(COLOR_RED   "\t");	
		           printf("\t\t\t%s Win THE GAME AND GET 1 POINT\n",name);	
				   printf(COLOR_RESET "\t");	           
		           printf("\n\t\t\t************  ***************  **************\n\n");
		          // win++;
				}
				else
				if(n==2 && s==1)
		    	{
		    	   printf("\t\t\t%s Enter Gun and Computer Enter Water\n",name);	
		    	   printf(COLOR_RED   "\t");
		           printf("\t\t\tComputer Win THE GAME AND GET 1 POINT\n" );
				   printf(COLOR_RESET "\t");		           
		           printf("\n\t\t\t************  ***************  **************\n\n");
		           loose++;
				}
		    }
		  /*  else
		    {
		        printf("COMPUTER WIN THE GAME AND GET 1 point\n");
		        loose++;
		    }*/
		    i++;
	    }
	    printf("\n\n");
	    Result(win,drawn,loose);
	}
		void choice(char n)
	{
	
	  switch (n)
	  {
	
	  case '1':
	    login();
	    break;
	  case '2':
	    Game();
	    break;
	  case '3':
	    Rules();
	  case '4':
	     Exit();  
	  
	   
	   
	   
	    break;
	  default:
	  {
	    printf("ERROR INVALID KEY\n");
	
	    printf("Please enter correct choice\n");
	
	    sleep(1);
	    menu();
	  }
	  }
	}
		

void menu()
	{
	  system("cls");
	   // printf(COLOR_RED   "\t");
   
	  char n;
	  printf("\t\t\t\t--------------------------\n");
	  printf("%s\t\t\t|      %s  WELCOMES YOU    |\t\t\t\t%s\n", __DATE__,bold,__TIME__);
	  printf("\t\t\t\t---------------------------\n\n\n");
	printf(COLOR_RED   "\t");
	  printf("1.CREATE ACCOUNT/DASHBOARD   \n        2.START GAME   \n        3.RULES  \n        4.EXIT \n\n");
	   printf(COLOR_RESET "\t");
	
	  printf("%sEnter your choice ", bold);
	  scanf("%c", &n);
	  choice(n);
	}
int main()
{
	menu();
	login();
     
    
}
void takeinput(char ch[50])
{
    fgets(ch,50,stdin);
    ch[strlen(ch)-1]=0;// to store 0 in the last index of char array;
}
