#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <conio.h>
#include <ctype.h>
#include <windows.h>
#include <stdlib.h>
#include <time.h>

//FUNCTIONS
void book();  
void petcal();
void deletee();
void list();

struct CustomerDetails   //STRUCTURE DECLARATION
{
	char ownername[20];
	char phonenumber[20];
	char dogname[20];
	char period[10];
	char arrivaldate[10];
	//char pickup[10];
	char breed[10];
	char size[10];
	char gender[10];
	char food[10];
	char shower[10];
	char special[10];
}c;

void book() //BOOKING FUNCTION
{
	FILE* f;
	char test;
	f = fopen("add.txt", "a+");

	if (f == 0)
	{
		f = fopen("add.txt", "w+");
		system("cls");
		printf("Please hold on....");
		printf("\nProcess completed press any key to continue");
		getchar();
	}

	while (1)
	{
		system("cls");
		printf("\n************************************");
		printf("\n-----------|BOOKING PAGE|------------");
		printf("\n************************************");
		printf("\nPlease enter the information below");
		printf("\n\nEnter owner's name : ");
		scanf("%s", c.ownername);
		fflush(stdin);
		printf("\nEnter your dog's name : ");
		scanf("%s", c.dogname);
		printf("\nEnter your phone number : ");
		scanf("%s", c.phonenumber);
		printf("\nEnter period(days) : ");
		scanf("%s", c.period);
		//printf("\nEnter pick-up time : ");
		//scanf("%s", &c.pickup);
		printf("\nEnter Arrival date(dd/mm/yyyy) : ");
		scanf("%s", &c.arrivaldate);
		printf("\nEnter your dog's breed : ");
		scanf("%s", &c.breed);
		printf("\nEnter your dog's size (small/medium/large) : ");
		scanf("%s", c.size);
		printf("\nEnter your dog's gender (male/female) : ");
		scanf("%s", c.gender);
		printf("\nDo you bring his/her food? enter (yes/no) : ");
		scanf("%s", c.food);
		printf("\nDo your dog need any special help ? Any allergy enter (yes/no) ? //if yes enter something : ");
		scanf("%s", c.special);

		fwrite(&c, sizeof(c), 1, f);
		fflush(stdin);
		printf("\n\nSuccessfully booked!!");
		//printf("\nDon't forget to pick-up your dog the same time as you arrive\n");
		printf("\nPress esc key to exit or any other key to add another dog : \n");
		test = getchar();
		system("pause");
		break;
		
	}
	fclose(f);
}

void deletee() //DELETING FUNCTION
{
	FILE* f, * t;
	int i = 1;
	char dogname[20];

	if ((t = fopen("temp.txt", "w")) == NULL)
		exit(0);
	if ((f = fopen("add.txt", "r")) == NULL)
		exit(0);

	system("cls");
	printf("\n************************************");
	printf("\n-----------|DELETING PAGE|-----------");
	printf("\n************************************");
	printf("\nPlease enter the answer below to delete");
	printf("\nEnter your dog's name : ");
	fflush(stdin);
	scanf("%s", dogname);

	while (fread(&c, sizeof(c), 1, f) == 1)
	{
		if (strcmp(c.dogname,dogname) == 0)
		{
			i = 0;
			continue;
		}
		else
			fwrite(&c, sizeof(c), 1, t);
	}

	if (i == 1)
	{
		printf("\n\nRecords is not found.\nPress enter to go back to the first page\n");
		system("pause");
		getchar();
		fclose(f);
		fclose(t);
		main();
	}
	fclose(f);
	fclose(t);
	remove("add.txt");
	rename("temp.txt", "add.txt");

	printf("\nSuccessfully removed!!!\n");
	printf("\n\nPress enter to go back to main menu\n");
	fclose(f);
	fclose(t);
	getchar();
	system("pause");
}

void list() //LISTING FUNCTION
{
	FILE* f;
	int i;

	if ((f = fopen("add.txt", "r")) == NULL)
		exit(0);

	system("cls");
	printf("\n**********************************************");
	printf("\n-------------------|NAME LIST|-------------------");
	printf("\n**********************************************\n");
	for (i = 0; i < 175; i++)
		printf("-");
	//PRINT OUT THE HEAD
	printf("\nOWNER NAME\t");
	printf("DOG'S NAME\t");
	printf("PHONENUMBER\t");
	printf("PERIOD\t");
	//printf("PICK-UP TIME\t");
	printf("ARRIVALDATE\t");
	printf("BREED\t");
	printf("\tSIZE\t");
	printf("GENDER\t");
	printf("FOOD(Y/N)\t");
	printf("SPECIAL NEED\t\n");

	for (i = 0; i < 175; i++)
		printf("-");
	while (fread(&c, sizeof(c), 1, f) == 1)
	{
		printf("\n%s \t\t%s \t\t%s \t%s \t%s \t%s \t%s \t%s \t%s \t%s", c.ownername, c.dogname, c.phonenumber, c.period, c.arrivaldate, c.breed, c.size, c.gender, c.food, c.special);
	}
	printf("\n");
	for (i = 0; i < 175; i++)
		printf("-");
	printf("\n\nPress enter to go back to main menu\n");
	fclose(f);
	getchar();
	system("pause");
}

void petcal() {
	float age, newage;
	
	system("cls");
	printf("\n*************************************");
	printf("\n-----------|Pet calculator|-----------");
	printf("\n*************************************");
	while (1) {
		printf("\n\nEnter a dog's age in human years : ");
		scanf("%f", &age);
		if (age <= 0) {
			printf("Age can't be less or equal to 0");
		}
		else if (age <= 2) {
			newage = age * 10.5;
			break;
		}
		else {
			newage = 21 + (age - 2) * 4;
			break;
		}
	}
	printf("\nThe dog's age in human's age is %5.1f years old ", newage);
	printf("\n\nPress enter to go back to main menu\n");
	getchar();
	system("pause");
}

int main() {     //MAIN FUNCTION	
	int i = 0;
	time_t t;
	time(&t);
	char choice;

	system("cls");   //FOR CLEARING SCREEN
	printf("\n\n\t\t\t\t*****************************************************************");
	printf("\n\t\t\t\tHello, Welcome to Jacky hotel!!!");
	printf("\n\t\t\t\tThis is a hotel for dogs where they can feel like home ^^");
	printf("\n\t\t\t\tThis is a program to book a room for your dog \n\t\t\t\tand a Pet Calculator to calculate your dog's age to human's age.");
	printf("\n\t\t\t\t*****************************************************************\n\n");
	printf("\n\t\t\t\tPress enter to continue ");
	getchar(); //TO PRESS ENTER
	
	while (1)      //INFINITE LOOP
	{
		system("cls");
		printf("\n");
		printf("----------------------------------|-MAIN MENU-|---------------------------------- \n");
		for (i = 0; i < 80; i++)
			printf("*");
		printf("\n\t\tCurrent date and time : %s", ctime(&t));
		for (i = 0; i < 80; i++)
			printf("*");
		printf("\n");
		printf("\t\t\t -Please enter your choice for menu-");
		printf("\n\n");
		printf("------------------------------------");
		printf("\nEnter 1 -> Book a room");
		printf("\n------------------------------------");
		printf("\nEnter 2 -> Pet Calculator");
		printf("\n------------------------------------");
		printf("\nEnter 3 -> Print All the name list");
		printf("\n------------------------------------");
		printf("\nEnter 4 -> Delete");
		printf("\n------------------------------------");
		printf("\nEnter 5 -> Exit");
		printf("\n------------------------------------");
		printf("\n\n");
		printf("\nEnter your answer : ");
		choice = getchar();
		choice = toupper(choice);
		switch (choice)  //SWITCH STATEMENT
		{
		case '1':
			book(); 
			break;
		case '2':
			petcal(); 
			break;
		case '3':
			list(); 
			break;
		case '4':
			deletee(); 
			break;
		case '5': //EXIT
			//system("cls");
			printf("\n\n -THANK YOU- \n\n");
			exit(0);
			break;
		default: //OUT OF 1-5
			//system("pause");
			printf("\nIncorrect Input");
			printf("\nPress enter to try again\n");
			getchar();
			system("pause");
			break;
		}
	}
	
}
