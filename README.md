# C Project defending mistakes

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <ctype.h> 
#include <string.h>

#define STR_SIZE 2000000 

int intAfterCheck(char *msg)
{
	char temp[STR_SIZE];
	int i, arith;
	bool flag;
	
	do
	{
		flag=1;
		
		printf("%s",msg);
		gets(temp);
		
		if(strlen(temp)==0)	
			flag=0;	
		
		else if((temp[0]=='+' || temp[0]=='-') && strlen(temp)==1)
			flag=0;
		
		else if(temp[0]!='+' && temp[0]!='-') 
		{
			for(i=0;i<strlen(temp); i++)
			{
				if(isdigit(temp[i])!=0) 
					flag = flag&1;
				else				
					flag = flag&0;
			}
		}

		
		else if((temp[0]=='+'&&temp[1]=='+')|| (temp[0]=='+'&&temp[1]=='-') || (temp[0]=='-'&&temp[1]=='+') || (temp[0]=='-'&&temp[1]=='-')) 
			flag = 0; 
		
		
		else if((temp[0]=='+'&&temp[1]!='+')|| (temp[0]=='+'&&temp[1]!='-')||(temp[0]=='-'&&temp[1]!='+') || (temp[0]=='-'&&temp[1]!='-')) 
		{	
			for(i=1;i<strlen(temp); i++)
			{
				if(isdigit(temp[i])!=0) 
					flag = flag&1;
				else					
					flag = flag&0;
			}
		}		
		
		if(flag==0) 
		{
			printf("\n\You didnt enter a number, Please try again !\n\n");
			system("pause");
			system("cls");
		}
	}while(flag==0);
	
	
	arith = atoi(temp);
					  	
	return arith;
}

float floatAfterCheck(char *msg)
{
	char temp[STR_SIZE];
	int i, count, flag=0;
	float arith;
	
	do
	{
		flag=1; 
		count=0;
		
		printf("%s",msg);
		gets(temp);
		
		if(strlen(temp)==0)
			flag=0;	
		else
		{
			
			for(i=0;i<strlen(temp)-1; i++)
				if(temp[i]=='.')
					count++;
			
			if (count>=2)
				flag=0; 
				
			if(temp[0] == '.' || temp[strlen(temp)-1] == '.')	
				flag=0;
			
			if((temp[0]=='+' || temp[0]=='-') && strlen(temp)==1)
				flag=0;
				
			if(temp[0]!='+' && temp[0]!='-')
			{
				
				if(count<=1)
				{
					for(i=0;i<strlen(temp); i++)
					{
						if(temp[i]=='.')
							continue;  
						else
						{
							if(isdigit(temp[i])!=0) 
								flag = flag*1;
							else					
								flag = flag*0;
						}
					}
				}	
			}
			
			
			if((temp[0]=='+'&&temp[1]=='+') || (temp[0]=='+'&&temp[1]=='-') || (temp[0]=='-'&&temp[1]=='+') || (temp[0]=='-'&&temp[1]=='-')) 
				flag = 0; 
			
			if((temp[0]=='+'&&temp[1]=='.') || (temp[0]=='-'&&temp[1]=='.')) 
				flag = 0; 
				
				
			if((temp[0]=='+'&&temp[1]!='+') || (temp[0]=='+'&&temp[1]!='-') || (temp[0]=='-'&&temp[1]!='+') || (temp[0]=='-'&&temp[1]!='-'))  
			{	
				for(i=1;i<strlen(temp); i++)
				{
					if(temp[i]=='.')
						continue;   
					else
					{
						if(isdigit(temp[i])!=0) 
							flag = flag*1;
						else				
							flag = flag*0;
					}
				}
			}
		}
		
		if(flag==0) 
		{
			printf("\n\n You didnt give a number! \a\n Please try again !\n\n");
			system("pause");
			system("cls");
		}
	}while(flag==0); 
	
	arith = atof(temp); 
					  
	return arith;
}

int main()
{
	system("chcp 1253");
	system("cls");
	int temp1;
	float temp2;
	
	temp1 = intAfterCheck("type and integer:");
	printf("the integer you typed is  %d.\n\n", temp1);
	
	temp2 = floatAfterCheck(" Give a number:");
	printf("The number you gave is %.2f.\n\n", temp2);
	
	system("pause");
	return 0;
}
		

