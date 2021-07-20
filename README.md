# c-program


#include<stdio.h>
#include<stdlib.h>
#include<stdbool.h>

int curr_student;

void print_header(){
	system ("cls");
	printf("\t\t\tStudent information center.\n");
}

struct student{
	char name [100];
	int roll;
	float marks[3];
}st[100];
	

void add_student(struct student *s){
	int i;
	float perc = 0;
	
	printf("Enter student name: ");
	scanf("%s",&s->name);
	printf("Enter student roll no.: ");
	scanf("%d",&s->roll);
	for(i=0;i<3;i++){
		printf("Enter %d marks of %s: ",i+1,s->name);
		scanf("%f",&s->marks[i]);
	}
	for(i=0;i<3;i++){
		perc += s->marks[i];
	}
	 perc = (perc/300)*100;
	 printf("Percentage of %s is: %.2f \n",s->name, perc);
		
	
	printf("\nStudent added successful...");
	printf("%d", s->roll);
	sleep(2);
}

void edit_student(){
	int roll,i,j;
	int foundIndex =0 ;
	bool found = false;
	printf("Enter student roll: ");
	scanf("%d",&roll);
	for(i=0;i<curr_student;i++){
		if(roll == st[i].roll){
			foundIndex = i;
			found = true;
			break;
		}
	}
	if(found){
		printf("student found\n");
		printf("Enter new name: ");
		scanf("%s",&st[foundIndex].name);
		for(j=0;j<3;j++){
			printf("Enter %d marks of %s: ",j+1,st[i].name);
			scanf("%f",&st[i].marks[j]);
		}
		printf("\nSucessfully changed");
	}else{
		printf("not found\n");
		printf("Please re enter\n");
		sleep(3);
		edit_student();
	
	}
}
void search_student(){
	int i,roll,j;
	float perc = 0;
	printf("Enter roll number: ");
	scanf("%d",&roll);
	for(i=0;i<curr_student;i++){
		if(roll == st[i].roll){
			printf("Name: %s\n",st[i].name);
			printf("Roll no. : %d\n",st[i].roll);
		
			for(j=0;j<3;j++){
				printf("Marks of %d is %.2f\n",j+1,st[i].marks[j]);	
			}
			for(j=0;j<3;j++){
				perc += st[i].marks[j];	
			}
			 perc = (perc/300)*100;
	 		printf("\nPercentage of %s is: %.2f \n",st[i].name,perc);
		}
	}
			
	
}
void all_student(){
	int i,j;
	
	printf("\t\t\tDisplaying student information...\n");
	for(i=0;i<curr_student;i++){
		float perc = 0;
		printf("\nStudent Name : %s\n",st[i].name);
		printf("Roll number: %d\n",st[i].roll);
		for(j=0;j<3;j++){
			printf("Marks  %d is: %f\n",j+1,st[i].marks[j]);
			perc += st[i].marks[j];
		}
		
		perc = (perc/300)*100;	
	 	printf("\nPercentage of %s is: %.2f \n",st[i].name, perc);
	 	
	}
		
}

int main(){
	int i;
	int choice;
		
	while(choice != 5){
	
		
		print_header();
		
		printf("\n 1- Add student");
		printf("\n 2- Edit student");
		printf("\n 3- Search student");
		printf("\n 4- Show all student");
		printf("\n 5- Quit");
		printf("\n Enter choice: ");
		scanf("%d",&choice);
		
		switch(choice){
			case 1:
				print_header();
				 add_student(&st[curr_student]);
				 curr_student++;
				 sleep(1);
				 break;
				 
				
			case 2:
				edit_student();
				sleep(2);
				break;
			
			case 3:
				search_student();
		
					char c;
				printf("\nEnte M for menu: ");
				scanf("%c");
				scanf("%c",&c);
				if(c == 'm'|| c == 'M'){
					break;
				}
// for testing 
//			case 9:
//				
//				for(i=0;i<curr_student;i++){
//					printf("%s\n", st[i].name);
//				}
//				sleep(3);
//				break;
			
			case 4: 
				all_student();
				char ch;
				printf("\nEnte M for menu: ");
				scanf("%c");
				scanf("%c",&ch);
				if(ch == 'm'|| ch == 'M'){
					break;
				}
			case 5:
				exit(3);
				break;
			
			
		}	
	
	}
}
