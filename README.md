# Unreal-Engine-C-CheatSheet
A Basic cheat sheet for programming for the Unreal Engine 
The file is a C++ File for Visual Basics so you must have visual Basic in order to see both ".h" & ".cpp" files
Hope this helps you on your Unreal Development Journey..

Just in case you are to lazy to get visual studios for some reason then Ill will put the main_source.cpp file in the read me for quick reference.





#include<iostream>
#include<string>
#include"Object.h"
#include"Actor.h"
#include"Pawn.h"
using namespace std;



//Unreal Engine C++ Practice Cheat Sheet




/* Function Overload Partice
void Print(string str);
void Print(int i);
void Print(string str1, string str2);
void Print(int i, string str);*/

//REFFERENCE EX.
//void ChangeStr(const string & str);

//ENUMERATION PRACTICE
/*enum PlayerStatus
{
	PS_Crouched,
	PS_Standing,
	PS_Running,
	PS_Sprinting
};

enum MovementStatus
{
	MS_Crouched,
	MS_Running

};*/


//Varibles for switches enum type
/*enum PlayerStatus
{
	PS_Walking,
	PS_Jogging,
	PS_Running
};

const float RunSpeed = 800.f;
const float WalkSpeed = 350.f;
const float JogSpeed = 500.f;

void UpdateMovementSpeed(PlayerStatus P_Status, float& speed);


//Varible for switches integer type
void SwitchOnInt(int i);*/



//STRUCT NOTES AND PRACTICE
/*struct LocationVector
{
	float x;
	float y;
	float z;
};


struct Player
{
	int Level;
	float Damage;
	float Stamina;
	float Health;

	LocationVector Location = { 0.f, 0.f, 0.f };

		void TakeDamge(float dmg)
	{
		Health -= dmg;
	}
	int GetLevel()
	{
		if (Level > 10)
		{
			cout << "Level Greater than ten" << endl;
		}
		return Level;
	}


	void DisplayLocation()
	{
		cout << "Location x = " << Location.x << endl;
		cout << "Loaction y = " << Location.y << endl;
		cout << "Location z = " << Location.z << endl;
	}


};*/
//Struct example for pointer
/*struct Container
{

	string Name;
	int x;
	int y;
	int z;
	
};*/
//Constuctor Example Practice
/*class Dog
{


public:


	Dog();




	string Name;
	int Age;
	float Health;
	void bark()
	{
		cout << "Bark!" << endl;
	}
};*/

//Parent class
//Inheritance Example
/*class Animal
{
public:
	Animal();
	Animal(string name, int age, int num_limbs);

	string Name;
	int Age;
	int NumberOFLimbs;

	void Report();
};

//Child of Animal
class Dog : public Animal
{
public:
	Dog();
	Dog(string name, int age, int num_limbs);

	void Speak();
};

//Child of Dog & Animal
class Corgi : public Dog
{

};*/

//Class Creation Practice #2 while using different access varibles (private, public, pretected)
/*class Creature
{
public:

	
	Creature();


	//Creating functions for private varible in private access modifiers.
	//SETTING Function for the private varible Name
	void setName(string name);

	//GETTER Function  for the private name varible 
	string getName();

	//GETTER Function for private health varible
	float getHealth();

	//Function For Taking Damge
	void takeDamage(float damage);


private:

	string Name;
	float Health;
	

protected:

	int numberOfLimbs;


};

class Goblin : public Creature
{
public:
	int getNumberOfLimbs();
	Goblin();
};*/


//Pointer and memory allocation Practice
/*struct Character
{
	Character();
	//Defining function inside the struct 
	{
		Name = "James";
		Health = 100.f;
	}
	void PrintHealth();
	{
		cout << "Health is " << Health << endl;
	}
	string Name;
	float Health;
};*/

//Defining function outside the struct or fully qualifying the name of the function.
/*Character::Character()
{
	Name = "James";
	Health = 100.f;
}

void Character::PrintHealth()
{
	cout << "Health is " << Health << endl;
}*/








//Destructors Practice
/*class Character
{
public:

	Character();
	~Character();
	int* CharacterAge;
	float* CharacterHealth;
};

Character::Character()
{
	cout << "Charcter was created " << endl;

	//Dynamically Allocate MEM for a int and float and the HEAP
	CharacterAge = new int(1);
	CharacterHealth = new float(100.f);
}

Character::~Character()
{
	cout << "Player Died " << endl;
	
	//When Character is destroy the destructor also destroy it from the HEAP
	delete CharacterAge;
	delete CharacterHealth;
}*/


//Destructor Practice
/*class Item
{
public:
	Item()
	{
		cout << "An Irem has been created " << endl;
	}
	~Item()
	{
		cout << "An Item Has been Destroyed " << endl;

	}
};*/

//STATIC KEYWORD PRACTICE
/*class Critter
{
public:
	Critter()
	{
		cout << "Acritter was born " << endl;


		CritterCount++;
	}

	static void AnnounceCount()
	{
		cout << CritterCount << endl;
	}
	static int CritterCount;
};



int Critter::CritterCount = 0;*/



//VIRTUAL PARENT TO GRANDCHILD INHERITENCE PRACTICE
/*class Object
{
public:
	virtual void BeginPlay();




};

class Actor :public Object
{
public:
	virtual void BeginPlay() override;

};

class Pawn : public Actor
{
public:
	virtual void BeginPlay() override;

};



void Object::BeginPlay()
{
	cout << "Object BeginPlay()has been called " << endl;
}*/


//POLYMORPHISM PRACTICE INHERETENCE CHAIN
//Check other .h & .cpp files

void InheritenceFunction()
{
	Object* ptr_To_object = new Object;
	Actor* ptr_To_actor = new Actor;
	Pawn* ptr_To_pawn = new Pawn;



	Object* ObjectArray[] = { ptr_To_actor, ptr_To_object, ptr_To_pawn };

	for (int i = 0; i < 3; i++)
	{
		//ObjectArray[i]->BeginPlay();
		//working with temp varible
		Object* obj = ObjectArray[i];


		//this conversion takes pointers Dynamaics casting checks
		Actor* act = dynamic_cast<Actor*>(obj);

		if (act)
		{
			act->ActorFunction();
		}

		Pawn* pwn = dynamic_cast<Pawn*> (obj);
		if (pwn)
		{
			pwn->PawnFunction();
		}



		//this conversion takes pointers
		//STATIC CAST DOES NOT CHECK
		/*Actor* act = static_cast<Actor*>(obj);

		if (act)
		{
			act->ActorFunction();
		}

		Pawn* pwn = static_cast<Pawn*> (obj);
		if (pwn)
		{
			pwn->PawnFunction();
		}*/
	}







	delete ptr_To_pawn;
	delete ptr_To_actor;
	delete ptr_To_object;
}










int main()
{
	//Practice with FOR LOOPS
	/*for (int i = 0; i <= 5 ; i++)
	{
		for (int j = 0; j <= 10; j++)
		{
			for (int k = 0; k <= 15; k++)
			{
				cout << "i = " << i <<  " j = " << j << " k = " << k << endl;
			}
		}
	}
	cout << endl;

	//REFFERENCE EX.
	string myStr = "Druid";
	ChangeStr(myStr);
	cout << myStr << endl;*/


	//Function OverLoad Practice
	/*int myInt = 3;
	string myStr = "James";
	string meSecondStr = "Weed ";

	Print(myStr);
	Print(meSecondStr);
	Print(myInt);
	Print(myInt, myStr);
	Print(myStr, meSecondStr);*/


	//Practice With Strings
	/*string MyString;
	MyString = "MY dog's name is  ";
	string first = "Spot ";
	string last = " Jones ";
	MyString += (first + last);

	cout << MyString << endl;*/

	//AND (&&) & OR (||) Practice
	/*int  i = 1;
	int j = 2;
	int k = 3;*/

	//OR
	/*if (i <= k || i == j) 
	{
		cout << "this is OR" << endl;
	}*/

	//AND
	/*if ((i <= k && j == j) && (k >= i))
	{
		cout << "this is AND " << endl;
	}*/

	//ARRAY PRACTICE WITH FOR LOOPS
	/*int MyArray[5] = { 1,2,34,6,9 };
	for (int i = 0; i < 5; i++)
	{

		cout << "MyArray[ " << i << " ] = " << MyArray[i] << endl;
		
	}
	int MyIntArray[10];

	for (int i = 0; i < 10 ; i++)
	{
		MyIntArray[i] = i;


		Loop that initializes 40 bytes of memory in the array

		cout << MyIntArray[i] << endl;
	}
	Printing single element of array to screen
	cout << "the first element in My Int Array is : " << MyIntArray[0] << endl;

	cout << " The Fifth Element in MyIntArray is: " << MyIntArray[4] << endl;*/


	//ENUMERATION PRATICE
	/*PlayerStatus status;
	
	status = PlayerStatus::PS_Running;
	
	MovementStatus move;

	move = MovementStatus::MS_Running;

	if (status == PS_Running && move == MS_Running)
	{
		cout << " This Player is Crouching! " << endl;
	}*/



	//Using Switches with ENUMS
	/*float MovementSpeed;


	PlayerStatus status = PS_Running;

	UpdateMovementSpeed(status, MovementSpeed);

	cout << "Movement Speed = " << MovementSpeed << endl;*/


//Using Switches with INTEGERS
/*int integer = 99;

SwitchOnInt(integer);*/



//STRUCT NOTES AND PRACTICE	
/*Player p_1;
p_1.Level = 11;
p_1.Health = 100.f;
p_1.Stamina = 100.f;
p_1.Damage = 10.f;

cout << " p_1 Level = " << p_1.GetLevel() << endl;


p_1.TakeDamge(40.f);

cout << "p_1 take " << 40.f << " damage! " << endl;
cout << "p_1 health = " << p_1.Health << endl;


p_1.DisplayLocation();

Player p_2 = { 1, 50.f, 40.f, 5.f,{5.f, 5.f, 5.f} };

p_2.DisplayLocation();*/




//Simple POINTER PRACTICE
/*int a = 100;
int* aPtr;
aPtr = &a;
cout << *aPtr << endl;

int b = 50;
aPtr = &b;
cout << *aPtr << endl;*/









//POINTER PRACTICE WITH ARRAYS
/*int number[] = { 0,1,2,3,4,5,6,7,8,9,10 };
int* NumPtr = number;


cout << *NumPtr << endl;


NumPtr++;

cout << *NumPtr << endl;

NumPtr += 5;

cout << *NumPtr << endl;

Container container = {"Sam",5,6,7 };

Container* PtrToCount = &container;









//Dereferenced PtrToCount and used the dot operator to reference the name and other elements.
//Ugly Notation pointer
cout << (*PtrToCount).Name << endl;
cout << (*PtrToCount).x << endl;
cout << (*PtrToCount).y << endl;
cout << (*PtrToCount).z << endl;

//PrettyNotation pointer
cout << PtrToCount->Name << endl;
cout << PtrToCount->x << endl;
cout << PtrToCount->y << endl;
cout << PtrToCount->z << endl;*/


//Constructor Example Practice
/*Dog dog;


cout << dog.Name << endl;
cout << dog.Age << endl;
cout << dog.Health << endl;

dog.Name = "jow";
dog.Age = 10;
dog.Health = 10.f;

cout << dog.Name << endl;
cout << dog.Age << endl;
cout << dog.Health << endl;*/

//Calling Base Animal Constructor
/*Animal animal;

animal.Report();


//Calling Animal Constructor Overloads
Animal animal_2("Cheetah", 7, 5);

animal_2.Report();*/

//Calling child of parent class
/*Corgi corgi;
corgi.Speak();
corgi.Report();*/


//Accessing Private Varibles
//Changing and getting private function class
//Good practice to use getter and setters
/*Creature Igore;

//setting Igore class name to Igore in literal strings
Igore.setName("Igore");

//Print Name to screen
cout << "Name: " << Igore.getName() << endl;

//Print health to screen
cout << "Health: " << Igore.getName() << endl;

//Taking damage away from Igore then calling the remaining health
cout << "Igor will now take 35 damage " << endl;
Igore.takeDamage(35.0);
cout << endl << endl;

 //Calling child of creating Goblin with varible name Gobby
Goblin Gobby;


cout << Gobby.getName() << endl;

cout << Gobby.getNumberOfLimbs() << endl;*/

//LOOP for pointer character and memory allocation practice
	/*for (int i = 0; i < 10; i++)
	{

		//this character is stored in the HEAP so we are resposible for pulling it out of scope with the keyword DELETE.
		//Creating varible for single or multi sctruct objects then deleting them after they are created.
		Character* PtrToChar = new Character();

		cout << PtrToChar->Name << endl;

		PtrToChar->PrintHealth();

		delete PtrToChar;

	}*/
	//Remember how to call varibles in pointers
	/*cout << PtrToChar->Name << endl;

	cout << PtrToChar->Health << endl;*/



	//Destructor Function Practice
	/*Character* Char = new Character;
	delete Char;*/


//STATIC KEYWORD POINTER DECLARATION
/*Critter* crit = new Critter;
Critter::AnnounceCount;
delete crit;*/


//VIRTUAL INHERITENCE PRATCTICE CALLS
/*Object* obj = new Object;
obj->BeginPlay();


Actor* act = new Actor;
act->BeginPlay();


Pawn* paw = new Pawn;
paw->BeginPlay();


delete obj;
delete act;
delete paw;*/





//POLYMORPHOSIM POINTER TO OBJECT WIT OBJECT ARRAY
//guessing this is good for spawn items in game



InheritenceFunction();

	system("pause");
}

//Function Definitions!!!!!








//SWITCHES With ENUMS
/*void UpdateMovementSpeed(PlayerStatus P_Status, float& speed)
{
	switch (P_Status)
	{
	case PS_Running:
		speed = RunSpeed;
		break;

	case PS_Walking:
		speed = WalkSpeed;
		break;
	case PS_Jogging:
		speed = JogSpeed;
	}
}*/

//SWITCHES With INTERGERS
/*void SwitchOnInt(int i)
{
	switch (i)
	{
	case 0:
		cout << "your number was zero" << endl;
		break;
	case 1:
		cout << "your number was one" << endl;
		break;
	case 2:
		cout << " your number was two" << endl;
		break;
	default:
		cout << "Invalid number" << endl;
	}
}*/


//REFERENCE PRACTICE
/*void ChangeStr(const string & str)
{
	str += "!";
}*/


//Function OverLoad Practice
/*void Print(string Str)
{
	cout << Str << endl;
}

void Print(int i)
{
	cout << i << endl;
}

void Print(string str1, string str2)
{
	cout << "String1: " << str1 << "String 2: " << str2 << endl;
}




void Print(int i, string str)
{
	cout << "Integer Value: " << i << endl;
	cout << "String Value: " << str << endl;
}*/


//Constructor Example Practice
/*Dog::Dog()
{
		bark();

		Name = "Default Name";
		Age = 10;
		Health = 100.f;
}*/

//DEFAULT Animal constructor function
/*Animal::Animal()
{
	cout << "an Animal is born" << endl;

	Name = "DEFAULT";
	Age = 2;
	NumberOFLimbs = 4;
}
//Animal overload Constructor
/*Animal::Animal(string name, int age, int num_limbs)
{
	Name = name;
	Age = age;
	NumberOFLimbs = num_limbs;
}*/

//Animal Overload Constructor Using Parentheses Notation
/*Animal::Animal(string name, int age, int num_limbs) : Name(name), Age(age), NumberOFLimbs(num_limbs) 
{
	Report();
}

//Defined Report Function For the Animal class
void Animal::Report()
	{
	cout << endl;
		cout << "Name: " << Name << endl;
		cout << "Age: " << Age << endl;
		cout << "Number of Limbs: " << NumberOFLimbs << endl;
	}

Dog ::Dog()
{
	cout << "A dog is born" << endl;
}

//calling the dog constructor values in stead of the animal  overload class function
Dog::Dog(string name, int age, int num_limbs) : Animal(name, age, num_limbs)
{
}

void Dog::Speak()
{
	cout << "Roof! " << endl;
}*/

//Creature Function Definition 02!
/*Creature::Creature()
{

	Health = 100.f;
	cout << "A creature has been born" << endl;

	



}


//Creating Igor
void Creature::setName(string name)
{
	Name = name;
}


string Creature::getName()
{
	return Name;

}



float Creature::getHealth()
{
	return Health;
}




//Defining Damage... remeber damage was private not public!!!!!
void Creature::takeDamage(float damage)
{
	//Creating a proxy varible
	float Total;
	Total = Health - damage;

	if (Total <=0.f)
	{
		cout << getName() << " Has Died" << endl;
	}else
	
	{

		Health -= damage;
	}
	
	cout << "Remaining Health: " << Health << endl;
}

Goblin::Goblin()
{
	numberOfLimbs = 5;

	//Using public setName function to change the private name varible in the creature private class
	setName("Gobby");
}


//Changing number of limbs accessing a protected varible
int Goblin::getNumberOfLimbs()
{
	return numberOfLimbs;
}*/




//VIRTUAL KEYWORD OVERRIDE FUNCTION PRACTICE
/*void Actor::BeginPlay()
{
	cout << "A Play has been created." << endl;
	Object::BeginPlay();
}
void Pawn::BeginPlay()
{
	cout << "A Pawn has been created." << endl;
	Actor::BeginPlay();
}*/


//POLYMORPHISM PRATCICE INHERENTENCE CHAIN


//Check other .h & .cpp files

