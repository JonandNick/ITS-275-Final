
import java.util.Scanner; //create scanner
import java.util.*;
public class GymMembers { 


Member members[]; //calling from Member abstract class
{
this.members = members; //this statement to refer to current object 
}
public GymMembers() {//create GymMembers constructor that contains the information of all members in an array
super(); // super keyword used to invoke the parent class constructor
Member chris = new Member();
chris.name = "Chris Smith"; //create constants for each category
chris.membernumber = 1;
chris.age = 20;
chris.weight= 185;
chris.height = 71;
chris.membership = true;
chris.level = "BluePro";
chris.bench = 385;
chris.squat = 405;
chris.deadlift = 465;
chris.date = new Date(); //date object for today's date

Member ben = new Member(); //insert new user Ben into the system
ben.name = "Ben Sharp";
ben.membernumber = 2;
ben.age = 34;
ben.weight= 228;
ben.height = 73;
ben.membership = true;
ben.level = "Blue";
ben.bench = 255;
ben.squat = 325;
ben.deadlift = 405;
ben.date = new Date(); 

Member alex = new Member(); //insert Alex info into the database
alex.name = "Alex Gardner";
alex.membernumber = 3;
alex.age = 18;
alex.weight= -1;
alex.height = -1;
alex.membership = true;
alex.level = "Trial";
alex.bench = -1;
alex.squat = -1;
alex.deadlift = -1;
alex.date = new Date();

members= new Member[] {ben, chris, alex}; }

public void BMIconvert() { //void statement that gets ovderridden

Scanner in = new Scanner(System.in);

String BMI = "y";
BMI = in.next();

System.out.println(BMI);

int yourBMI;
while(!BMI.equals("n")) {
System.out.println("Do you want to check your BMI? (y/n):"); 
if (BMI.toLowerCase() == "n") {//converts strng to lowercase defined by "n".
break;
}
while (!in.hasNextInt()) {
in.next();

}

yourBMI = in.nextInt(); //BMI information is calculated and placed into one of the four categories

System.out.println("Your BMI is" + yourBMI);
if(yourBMI < 18.5) { //conditional operation used to set BMI to determine body type
System.out.println("Underweight");
}   else if (yourBMI < 25) {
System.out.println("Normal");
}   else if (yourBMI < 30) {
System.out.println("Overweight");
} else {
System.out.println("obese");
}

System.out.println("Check another BMI? (y/n): "); //loop if you want to keep checking someone elses BMI
BMI = in.next();
}
}

public Member userSearch(String name) { //method overloading using the members method but in different paramaters

Member result = null;
// Search through the array of all members
for (int i = 0;i < members.length; i++) {
if (members[i]== null) {
break;
}
if(members[i].name.equals(name)) {
result = members[i];
break;
}
}

return result;
}

public double getbmi(String name){ //recursion used to continuously get BMI when specific username is selected
Member m = null;
m=userSearch(name);
if (m == null) {
return -1;
}
return m.getbmi(); //return statement for continuation
}
}






import java.util.Scanner; //import scanner

public class Main { //main class
public static void main(String[] args) {
Scanner input = new Scanner(System.in);

String first = "nick"; //admin access to database so no one unauthorized can see the members personal information
String last = "venito";

Scanner in = new Scanner(System.in);
boolean validInput = false; //boolean used if item is false
String search =" search";
while (!validInput) { //if input is valid then proceed with username and password for access to database
System.out.print("Enter username:");
String username = in.next();
System.out.print("Enter password:");
String pass = in.next();

// Check if user-name and password match or not.
if (username.equals(first) && pass.equals(last))
{
System.out.printf("Welcome to the Gym database!   %n   Type search or bmi: ");
validInput=true;

}

else { //if input is invalid then access is denied
System.out.println("Access Denied");
{
	 try { //try and catch statement for a random password 
	      int[] myMemberPassword = {0};
	      System.out.println(myMemberPassword);
	    } catch (Exception e) { //exception used
	      System.out.println("Something went wrong."); //catch statement that inputs something went wrong because it is the incorrect password
	    } finally {
	        System.out.println("Enter username: ");
	    }
}

}
}
if (!validInput) {
System.exit(0);

}
GymMembers g = new GymMembers(); //call from GymMembers class  for variable g
g.userSearch("Chris Smith");
String inputtext = " ";
while(!inputtext.equals("quit")) {

inputtext=in.nextLine();
switch (inputtext) { //switch statement used for username and password
case "search":
System.out.println("Type in known username ");
inputtext = in.nextLine();
Member m = g.userSearch(inputtext);
if (m == null) {
System.out.println("User not found try again"); //user not found statement if wrong username entered
}
else {
m.printinfo();
}
System.out.println();
break;

case "bmi":
System.out.println("Enter a Username");
inputtext=in.nextLine();

double bmi = g.getbmi(inputtext);
if (bmi < 0){
System.out.println("Not valid bmi");    
}
else{
System.out.println("The Entered Members Bmi is: " + bmi); //calculates BMI from methods used in other class
System.out.println();
break;

}
}



}
}
}



import java.util.*; //import java. util

public class Member { //member class that features the members information that will be called for other class 
public String name = "no name"; //contains all the information needed for the information of our members 
public int membernumber = 0 ;
public int age = 0;
public double height = 0;
public double weight = 0;
public boolean membership = false; //boolean for true or false
public String level = "undefined";
public int squat = 0;
public int bench = 0;
public int deadlift = 0;
public Date date = new Date();
public void printinfo(){ //create a method is not going to take any value or return any and access the properties of this class
System.out.println("Member Name "+ name);
System.out.println("Member Number "+ membernumber);
System.out.println("Member Age: "+ age);
System.out.println("Has MemberShip? "+ membership);
System.out.println("height: " + height);
System.out.println("weight: " + weight);
System.out.println("Bench Max: " + bench);
System.out.println("Squat Max: " + squat);
System.out.println("Deadlift Max: " + deadlift);
System.out.println("Member information accurate as of: "+ date);
System.out.println();
System.out.println("Level? "+ level);
System.out.println();

}
public double getbmi() { //double method used for all calculations
double bmi=0;

final double KILOGRAMS_PER_POUNDS = 0.45359237; //insert formulas for calculations

final double METERS_PER_INCH = 0.0254;

double weightInKilograms = weight * KILOGRAMS_PER_POUNDS;

double heightINmeters = height * METERS_PER_INCH;

bmi = weightInKilograms/ (heightINmeters * heightINmeters);

return bmi; //return statement
}
