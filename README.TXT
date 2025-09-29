Project: auction
Authors: David J. Barnes and Michael Kölling

This project is part of the supplementary material for
chapter 4 of the book

   Objects First with Java - A Practical Introduction using BlueJ
   Seventh edition
   David J. Barnes and Michael Kölling

Purpose of project: To demonstrate collections of objects
How to start this project:
    + Create an Auction object.

    + Enter a few lots via its enterLot method. Only String
    descriptions of the lots are required.

    + Create one or more Person objects to represent bidders.

    + Show the lots and decide on one to bid for. Make a note
      of the lot number.

    + Enter a bid for the lot by calling the makeABid method on
      the Auction object. Pass the number of the lot, the Person
      who is bidding, and the amount of the bid.

Lab raport (part a = question, part b = answer)

46a. Create an auction with a few lots, persons, and bids. Then use 
the object inspector to investigate the object structure. Start with 
the auction object, and continue by inspecting any further object 
references you encounter in the objects’ fields.

46b.



47a. The makeABid method includes the following two statements:
Bid abid = new Bid(bidder, value);
boolean successful = selectedLot.bidFor(bid);
The abid variable is only used here as a placeholder for the newly created 
Bid object before it is passed immediately to the lot’s bidFor method. 
Rewrite these statements to eliminate the bid variable by using an anonymous 
object as seen in the enterLot method.

47b.



48a. Add a close method to the Auction class. This should iterate over the 
collection of lots and print out details of all the lots. Use a for-each loop. 
Any lot that has had at least one bid for it is considered to be sold, so what 
you are looking for is Lot objects whose highestBid field is not null. Use a 
local variable inside the loop to store the value returned from calls to the 
getHighestBid method, and then test that variable for the null value. For lots 
with a bidder, the details should include the name of the successful bidder and 
the value of the winning bid. For lots with no bidder, print a message that 
indicates this.

48b.



49a. Add a getUnsold method to the Auction class with the following header:
 public ArrayList<Lot> getUnsold()
 This method should iterate over the lots field, storing unsold lots in a new 
ArrayList local variable. What you are looking for is Lot objects whose highestBid 
field is null. At the end of the method, return the list of unsold lots.

49b.



50a. Suppose that the Auction class includes a method that makes it possible to 
remove a lot from the auction. Assuming that the remaining lots do not have their 
lotNumber fields changed when a lot is removed, write down what you think the 
impact would be on the getLot method.

50b.



51a. Rewrite getLot so that it does not rely on a lot with a particular number 
being stored at index (number1) in the collection. For instance, if lot number 2 
has been removed, then lot number 3 will have been moved from index 2 to index 1, 
and all higher lot numbers will also have been moved by one index position. You 
may assume that lots are always stored in increasing order according to their lot 
numbers.

51b.



52a. Add a removeLot method to the Auction class, having the following header:
 /**
 * Remove the lot with the given lot number.
 * @param number The number of the lot to be removed.
 * @return The Lot with the given number, or null if
 * there is no such lot.
 */
 public Lot removeLot(int number)
This method should not assume that a lot with a given number is stored at any 
particular location within the collection

52b.



53a. The ArrayList class is found in the java.util package. That package also 
includes a class called LinkedList. Find out what you can about the LinkedList 
class, and compare its methods with those of ArrayList. Which methods do they 
have in common, and which are different?

53b.



54a. Continue working with the club project from Exercise 4.40. Define a method 
in the Club class with the following description:
 /**
 * Determine the number of members who joined in the
 * given month.
 * @param month The month we are interested in.
 * @return The number of members who joined in that month.
 */
 public int joinedInMonth(int month)
If the month parameter is outside the valid range of 1 to 12, print an error 
message and return zero.

54b.



55a. Define a method in the Club class with the following description:
 /**
 * Remove from the club's collection all members who
 * joined in the given month, and return them stored
 * in a separate collection object.
 * @param month The month of the membership.
 * @param year The year of the membership.
 * @return The members who joined in the given month and year.
 */
 public ArrayList<Membership> purge(int month, int year)
If the month parameter is outside the valid range of 1 to 12, print an error 
message and return a collection object with no objects stored in it.
Note: The purge method is significantly harder to write than any of the others 
in this class.

55b.

