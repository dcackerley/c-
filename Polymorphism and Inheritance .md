Ch. 11 default constructor, what's a copy constructor 

string s; (default constructor)
string v(s); (copy constructor)
string v(“mike”); (convert constructor)
-CCClass(int a);
-string(char *) //String class can convert from c-strings
--Can use string s = “hello”; //with assignment operator

string(const string s) for best practice, reference so it can't be modified
only declare functions as const that don't change anything

Operator overloading

Think about whether class contains other objects, composition controls life cycle of other objects
Overriding vs overloading: overloading name of function stays same, arguments have different types/#
overriding name, data types, arguments are the same.  Overriden = works on base class and inherited class.  

Aggregation: Object of one class owns an object of another class (has a)
Composition: Type of aggregation, enclosing object controls lifetime of objects of enclosed class (same as owner, destroyed using owner's destructor)
Class Student{
private:
	StudentInfo personalData;
};
To aggregate, put member initialization list in constructor (enclosing class pass argu to enclosed)
owner_class(parameters) : owned_object(parameters)

When we create inheritance... private/protected/public.  Derived class inherits from base class.  
Class Person
private name
public getNames
Base class if derived from nothing.  
Class student : public person (student is derived from person) 
protected means anything public becomes protected (all public information becomes hidden from those outside of inheritance scheme) (derived, base can use protected)
If protected in class definition, student can access name
class Base{};
class Derived : public Base{}; //Derived 'is-a' base (base access, if in function list member access)
(Use pointers to objects instead of objects for parameter lists/arguments)
class Child : public/protected/private Parent{}; (base class access)

parent constructor → child constructor 
child destructor → parent destructor

Overriding: Function in derived class with same name & parameters as base class function
-Derived class objects will use overriden.  Access parent with scope resolution operator.

Seek moves, tell tells you where it is
g is for reading, p is for writing(?)

Chapter 12: Understand how c-string is terminated, REVIEW STRING CLASS AND METHODS, such as append, insert, remove.  How do we test c-strings?  Use character testing.  strcmp(s1,s2) (loops until null.)  Can't just do s1 == s2, can do *s1 == *s2.  
Character array is the same thing as a c-string
Comparing two strings vs comparing two character arrays.  
Null will be on the test.
Strlength, strcat, strcpy, strcmp (be very familiar with what's in the slides)
#include <cstring>
-Cstring terminated by NULL (\0, int 0, const NULL)
--Cstring is pointer to char (“Hi there!”, char *p, char str[20])
---String literal: Null-terminated char array (const pointer to char)
strlen(char *str) //returns # char in string, not including null, NOT size of array
strcat(char *dest, char *source) //adds second string to end of first string (no bound check)
strcpy(char *dest, char *source) //copy string from source address to destination address
int strcmp(char *str1, char*str2) //compare relative alphabetic order. <0 str1 precedes, >0 str2 precedes, 0 if equal.  End when encounter null or c-strings differ.
-Comparisons case sensitive, cannot use relational operators

#include <sstream> to convert between numbers and strings
to_string() number to string
stoi() string to int, stol() string to long, stof() string to float, stod() string to double
int stoi(const string& str, size_t* pos=0, int base = 10)

string class lets you find parts, modify it, inserting, replacing, swapping, 
#include <string>
default constructor string(), copy constructor string(string&), convert constructor string(char *)
-data(), c_str() returns c-string equivalent of string object
--str = “nice one!”;
--strcat(“ayyyy”, str.data());
-str.append(string s) appends s to end of str 
-str.insert(int pos, string s) insert s at position pos in str 
--str.insert(8, “NOT”)














Chapter 13: string class which iostream inherits from, fstream.  Look at picture of stream class inheritance.  They all inherit from <ios>.  Know what ios::binary,in,out,app mean.  Ios::good, eof(), feof(), fail() error state flags (eofbit, failbit, badbit) (not on test?) FAILING, FILE MODES
clear function resets everything to good (review more eof, good)
peek, get, put: all character operations.  C++ assumes file consists of characters.  
-File naming conventions
-Using fstream, ofstream, ifstream
-File modes: ios::binary, ios::in, ios::out, ios::app
--ios::app create file/append to end of existing file
--ios::ate go to end of existing file, write anywhere
--ios::binary read/write in binary mode
--ios::in open for input, open fails if file not found
--ios::out open for output, starts with empty file
-Failing: fail(), eof()
-Peek, get, put
-Binary files – structures, random access, seekg, seekp
ifstream/istream/istringstream (read), ofstream (write), fstream (either)
File open modes: ios::in, ios::out
fstream filename;
filename.open(“tap.dat”, ios::in | ios::out); OR fstream filename(“tap.dat”, ios::in); (constructor opens)

Ifstream/Ofstream do not need to specify a file open mode

Error state bits: 
ios::eofbit (set when end of file detected) eof() TRUE
ios::failbit (set when operation failed) fail() TRUE
ios::hardfail(set when irrecoverable error occurs) fail() TRUE
ios::badbit (set when invalid operation occurs) bad() TRUE
ios::goodbit(no other bits set) good() TRUE
clear() clear all flags, or clear specific flag
File handle set to true if operation succeeds.  If(!inFile) fails then set to false

Open file, close file, stream object.  If not for ios::binary file would be opened as character.  

getline(source, dest, stopChar)
-Source: stream being read from
-dest: string to hold text from source
-stopChar: terminator char (default \n)

get() read single character from input stream, return character, does not skip whitespace
get(char &ch) puts character into ch
ifstream infile; char ch;
infile.open(“myfile”);
infile.get(ch);

peek() read single character from input stream, do not remove character from input stream, don't skip white space
ch = infile.peek();

put() outputs a char into file, int code of char is passed to put
ofstream outfile;
outfile.open(“tap.dat”);
outfile.put('G');

seekg(offset, place)
-offset: # bytes from place, long
-place: offset calculation.  Ios::beg (beginning of file), ios::end (end of file), ios::cur (current)
infile.seekg(0L, ios::beg);
infile.clear(); to get rid of eof() bits and errors

Files open as text by default (numeric values are strings of ascii characters)
ios::binary to open member function 
infile.open(“tap.dat”,ios::binary); (binary uses special read/write member functions)
read(char *buffer, int numberBytes)
write(char *buffer, int numberBytes)
Buffer: array of bytes to transfer between memory and file (cast to char *)
reinterpret_cast<char *>
ofstream outfile(“myfile”,ios::binary);
double d[2] = {12.3, 34.5}
outfile.write(reinterpret_cast<char *>(d), sizeof(d))

Structures written to file must not have pointers, string objects (use char arrays)
Random access files
Sequential access: Start at beginning of file, go through it in order to end (reach 100th after 99 entries)
Random access: Access data in any order (reach 100th directly)
-seekg(offset, place) (use with input)
-seekp(offset, place) (use with output)
offset: long int, # bytes to move
place: start point for move, ios::beg, ios::cur, ios::end
inData.seekg(0L,ios::beg);
inData.seekp(-10L,ios::cur);
tellg() return current byte position in input file as long
tellp() return current byte position in output file as long
long whereAmI;
whereAmI = inFile.tellg();

simultaneous input/output:
fstream gradeList(“tap.dat”,ios::in|ios::out);

~~~~sstream stuff~~~~


Chapter 15
Virtual function: Has virtual keyword.  
Pure virtual has keyword 0, signifies it as abstract.  Normally done on base class.  
Note HOW to signify pure virtual function.
How do you make polymorphism work?  
Need to put it on base method
Static vs dynamic (early vs late): Virtual gives you dynamic.  
When is static decided?  When does C++ do static binding?  
Binding functions to the class.  Using base pointer without virtual keyword = static.  Static determined at compile time.  

Static done before program runs, dynamic done during runtime
Dyanmic binding enabled polymorphism using virtual keyword

static vs dynamic, what binding means

To be abstract, one pure virtual function
To be a pure virtual function, assign body = 0
To make virtual use virtual keyword

Base vs derived, virtual functions, abstract base classes and pure virtual functions, composition vs inheritance, static vs dynamic binding

Base class pointer can point to derived class objects Animal *pA = new Cat;
Base class pointer can point to derived class pointer WITH CAST
cat *pC
pC = static_cast<Cat *>(pA);
To access derived class members, type cast base class pointer to derived class with static_cast
If functions overridden, compiler determines function version by pointer type rather than object type

Polymorphic code behaves differently depending on object type, achieved using virtual keyword
class Animal{
public:
	virtual void id();
}
class Cat{
public:
	virtual void id();
}
class Dog{
public:
	virtual void id();
}
Function binding: Determining which function to use for particular function call.
-Static binding: Choose function in class of base class pointer, regardless of pointer (COMPILE TIME)
-Dynamic binding: Choose most specific version of function VIRTUAL (EXECUTION TIME)

OVERRIDE keyword at end of function prototype to indicate overriding functions
FINAL keyword to ensure no other classes will override function

Abstract class: Contains no objects that are not members of derived classes
-eg animal is an abstract class, because there's no “animal” animal
--abstract class has at least one abstract member function in C++


Pure virtual functions
Declare member function to be abstract function by making it virtual, replacing body with = 0;
class Animal{
public:
	virtual void id()=0;
};
Pure virtual/abstract functions cannot be instantiated.  Only inherited from.
To instantiate, must override all pure virtual functions with concrete member functions.

Inheritance: is-a
