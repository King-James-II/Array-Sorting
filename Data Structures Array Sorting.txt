/* This Program prints a 2D array with State and State Capital values and then uses a BubbleSort 
 * function to sort an array by State Capitals then Produces a quiz for the user where it asks for 
 * the capital of each state and at the end displays the number of correct answers and the 
 * percentage correct.*/
import java.util.Scanner;
public class BubbleSort {
	//Function to Sort the array by State Capital
	public void bubbleSort(String[][] array) {
		int p = array[1].length;
		//Nested for loop to allow traversal of each element for comparison and sorting.
		for (int i = 0; i < p-1; i++) {
			for (int j = 0; j < p-i-1; j++) {	
					if (array[1][j].compareTo(array[1][j+1])> 0) {
						String temp1 = array[0][j];
						String temp2 = array[1][j];
						array[0][j] = array[0][j+1];
						array[1][j] = array[1][j+1];
						array[0][j+1] = temp1;
						array[1][j+1] = temp2;
					}
			}
		}
	}
    public static void main (String [] args)
    {
    //Initializing variables and class object.
    BubbleSort bubble = new BubbleSort();
    String[][] statesAndCapitals = {
        {"Alabama", "Alaska", "Arizona", "Arkansas", "California", "Colorado", "Connecticut", 
        "Delaware", "Florida", "Georgia", "Hawaii", "Idaho", "Illinois", "Indiana", "Iowa", 
        "Kansas", "Kentucky", "Louisiana", "Maine", "Maryland", "Massachusetts", "Michigan", 
        "Minnesota", "Mississippi", "Missouri", "Montana", "Nebraska", "Nevada", "New Hampshire", 
        "New Jersey", "New Mexico", "New York", "North Carolina", "North Dakota", "Ohio", 
        "Oklahoma", "Oregon", "Pennsylvania", "Rhode Island", "South Carolina", "South Dakota", 
        "Tennessee", "Texas", "Utah", "Vermont", "Virginia", "Washington", "West Virginia", 
        "Wisconsin", "Wyoming"},
        {"Montgomery", "Juneau", "Phoenix", "Little Rock", "Sacramento", "Denver", "Hartford", 
        "Dover", "Tallahassee", "Atlanta", "Honolulu", "Boise", "Springfield", "Indianapolis", 
        "Des Moines", "Topeka", "Frankfort", "Baton Rouge", "Augusta", "Annapolis", "Boston", 
        "Lansing", "Saint Paul", "Jackson", "Jefferson City", "Helena", "Lincoln", "Carson City", 
        "Concord", "Trenton", "Santa Fe", "Albany", "Raleigh", "Bismarck", "Columbus", 
        "Oklahoma City", "Salem", "Harrisburg", "Providence", "Columbia", "Pierre", "Nashville", 
        "Austin", "Salt Lake City", "Montpelier", "Richmond", "Olympia", "Charleston", "Madison", 
        "Cheyenne"}
    };
    //Output Current array before sorting.
    System.out.println("Displaying States and Capitals Array:");
    printArray(statesAndCapitals);
    //Sort and display array sorted by state capital names.
    bubble.bubbleSort(statesAndCapitals);
    System.out.println("\n\nDisplaying Sorted States and Capitals Array:");
    printArray(statesAndCapitals);
    //Call the Quiz function and return number of correct answers to display to the user.
    int correct = capitalQuiz(statesAndCapitals);
    double percent = (correct/50.0)*100.0;
    System.out.println("\nTotal of correct answers: " + correct + " (" + (percent) + "%)");
    }
    // Method to print current contents of the 2D array passed into it. Added additional formatting
    // so that the array output is easily understandable.
    static void printArray (String array[][]) {
    for (int i = 0; i < array.length; i++) {
        for (int j = 0; j < array[i].length; j++) {
        	if (j == 0) {
        		if (i==0) {
        		System.out.println("{");
        		}
        		System.out.print("{");
        	}
        	if (j%6 ==0)
        	{
        		if (j!= 0) {
        			System.out.println();
        		}
        	}
        	if (j != 49) {
        		System.out.print(array[i][j] + ", ");
        	}
        	else {
        		System.out.print(array[i][j] + "");
        	}
        }
        if (i !=1) {
        	System.out.println("},\n");
        }
        else {
        	System.out.println("}");
        	System.out.print("}");
        }
    }
    }
    //Quiz method that prompts user to enter the state capital for each state in the sorted array.
    static int capitalQuiz (String array[][]) {
    	Scanner scan = new Scanner(System.in);
    	int ttlcorrect = 0;
    	//Prompt for user input and use toLowerCase to ensure that values are equal when correct.
    	for (int i=0; i < array[0].length; i++) {
    		System.out.println("\n\nWhat is the state capital of " + array[0][i] + "?");
    		String input = scan.nextLine().toLowerCase();
    		String capital = array[1][i].toLowerCase();
    		if (input.equals(capital)) {
    			ttlcorrect += 1;
    			System.out.println(input + " is correct. Current Score: " + ttlcorrect + "/50");
    		}
    		else {
    			System.out.println(input + " is incorrect. Current Score: " + ttlcorrect + "/50");
    		}
    	}
    	return ttlcorrect;
    }
}
