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

46b.Done.



47a. The makeABid method includes the following two statements:
Bid abid = new Bid(bidder, value);
boolean successful = selectedLot.bidFor(bid);
The abid variable is only used here as a placeholder for the newly created 
Bid object before it is passed immediately to the lot’s bidFor method. 
Rewrite these statements to eliminate the bid variable by using an anonymous 
object as seen in the enterLot method.

47b.boolean successful = selectedLot.bidFor(new Bid(bidder, value));



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
    public void close()
    {
        for(Lot lot : listOfLots)
        {
            if(lot.getHighestBid() != null)//always check if null first before calling its methods.
            {
                long highestBid = lot.getHighestBid().getValue();
                String highestBidder = lot.getHighestBid().getBidder().getName();
                System.out.println(lot.getNumber() + ":" + lot.getDescription()+" was SOLD to: " + highestBidder + " for: "+ highestBid + "$");
            }else
            {
                System.out.println(lot.getNumber() + ":" + lot.getDescription() + " to be sold at a later auction.");
            }
        }
    }

49a. Add a getUnsold method to the Auction class with the following header:
 public ArrayList<Lot> getUnsold()
 This method should iterate over the lots field, storing unsold lots in a new 
ArrayList local variable. What you are looking for is Lot objects whose highestBid 
field is null. At the end of the method, return the list of unsold lots.

49b.
    public ArrayList getUnsold()
    {
        ArrayList<Lot> listOfUnsoldLots = new ArrayList<Lot>();
        for(Lot lot : listOfLots)
        {
            if(lot.getHighestBid() == null)
            {
                listOfUnsoldLots.add(lot);
            }
        }
        return listOfUnsoldLots;
    }

50a. Suppose that the Auction class includes a method that makes it possible to 
remove a lot from the auction. Assuming that the remaining lots do not have their 
lotNumber fields changed when a lot is removed, write down what you think the 
impact would be on the getLot method.

50b. The lots'indexes following after the removed lot in the arrayList would no
longer correspond to lotNumber filed. Example, if I remove lot 3 from a list of 5,
then the forth lot would have an index of 2(which is the index for 3), in the
array list while its lotNumber field would be 4(its no longer the fourth.)

51a. Rewrite getLot so that it does not rely on a lot with a particular number 
being stored at index (number1) in the collection. For instance, if lot number 2 
has been removed, then lot number 3 will have been moved from index 2 to index 1, 
and all higher lot numbers will also have been moved by one index position. You 
may assume that lots are always stored in increasing order according to their lot 
numbers.

51b.
    /**
     * Return the lot with the given number. Return null if a lot with this 
     * number does not exist.
     * @param lotNumber The number of the lot to return.
     * @return The lot with the given number, or null.
     */
    public Lot getLotV2(int lotNumber)
    {
        for(Lot lot : listOfLots)
        {
            if(lotNumber == lot.getNumber())
            {
                return lot;
            }
        }
        return null;
    }    

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
    /**
    * Remove the lot with the given lot number.
    * @param number The number of the lot to be removed.
    * @return The Lot with the given number, or null if
    * there is no such lot.
    */
    public Lot removeLot(int number)
    {
        Iterator<Lot> it = listOfLots.iterator();
        while(it.hasNext())
        {
            Lot lot = it.next();
            if(number == lot.getNumber())
            {
                it.remove();
                return lot;
            }
        }
        return null;
    }


53a. The ArrayList class is found in the java.util package. That package also 
includes a class called LinkedList. Find out what you can about the LinkedList 
class, and compare its methods with those of ArrayList. Which methods do they 
have in common, and which are different?

53b. They are both lists that can contain one Type of Object, however LinkedList
permits null elements to be within it. It can grow or shrink dynamically,
meaning we can call the remove method without the need of an Iterator. They both
have certain methods like .get(int index) .size(int index), .add(int index), 
.remove(int index). But Linkedlist has a few standout ones such as 
.addLast(Element element), .addFirst(Element element), set(int index, Element element),
removeFirst(), removeLast(), peek() & poll(). The set method is for replacing
an element at the given index. The peek method is for retrieving the head of the queue
without removing it, while the poll method, retrieves the head of the queue and removes it.



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

