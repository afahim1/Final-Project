



public class SavingsAccount extends BankAccount {


	
	private double interestRate;
	
	
	String name;
	
public SavingsAccount(String name, double rate){

	super(name);
	
	if(rate > 0 && rate < 10)
	
		 interestRate = rate;
		 
	else interestRate = 1;
	
}
public double getRate(){

	return interestRate;
	
}
public String toString(){

	return ("Saving Account\n" + super.toString() + "/n" );
	
}
public void addInterest(){
	return;
}

}
// i do not know how to do this and i am like in last miniute.



public class CheckingAccount extends BankAccount {
	
	private int checkNumber;
	
	public CheckingAccount(String name, double rate){
	
		super(name);
		
		if (Check > 0)
		
			double checkNum;
			
		else 
		
			checkNum = 1000;
			
		
	}
	
	public int getcheckNum(){
	
		return Ckeck;
	}
	
	public String toString(){
	
		return String;
		
	}
	
	public void writeCheck(){
	
		return checkNum;
		
	}

}



// Abdul Majid Fahim

// 10614742

// PA13

// 
public class Bank {

	private BankAccount[] accounts;
	
	private int count;

	public Bank(int cap) {
	
		accounts = new BankAccount[cap];
		
		count = 0;
	}

	private int indexOf(BankAccount a) {
	
		for (int i = 0; i < count; i++) {
		
			if (accounts[i].equals(a))
			
				return i;
		}
		
		return -1;
	}

	public boolean contains(BankAccount a) {// show to dr.v
	
		if (indexOf(a) != -1)
		
			return true;
			
		else
			return false;
			
		// return indexOf(a) != -1;
	}

	public boolean add(BankAccount a) {
	
		if (contains(a))
		
			return false;

		if (full())
		
			doubleCapacity();

		accounts[count] = a;
		
		count++;
		
		return true;
	}

	public boolean remove(BankAccount a) {
	
		if (!contains(a))
		
			return false;
			
		int mama = indexOf(a);

		accounts[mama] = accounts[count - 1];
		
		accounts[count - 1] = null;
		
		count--;
		
		return true;
		

	}

	public int getCount() {
	
		return count;
		
	}

	public String toString() {
	
		StringBuilder sb = new StringBuilder();
		
		sb.append("Bank Accounts\n");
		
		for (BankAccount a : accounts)
		
			sb.append(a + "\n    **************    \n");
			
		return sb.toString();
	}

	public void sort() {
	
		for (int i = 0; i < count - 1; i++) {
		
			int I = i;
			
			for (int j = i + 1; j < count; j++)
			
				if (accounts[j].getAcctNum() < accounts[I].getAcctNum())
				
					I = j;

			BankAccount smallerAccount = accounts[I];
			
			accounts[I] = accounts[i];
			
			accounts[i] = smallerAccount;
		}

	}

	private void doubleCapacity() {
	
		BankAccount[] temp = accounts;
		
		accounts = new BankAccount[temp.length * 2];
		
		for (int i = 0; i < temp.length; i++)
		
			accounts[i] = temp[i];
	}

	private boolean full() {
	
		return count >= accounts.length;
	}
	public BankAccount find(int acct) { for (int i = 0; i < count; i++)
	
		if (accounts[i].getAcctNum() == acct) return accounts[i]; return null;
		}
		private int indexOf1(BankAccount a) { if (a == null) return -1;
		
		for (int i = 0; i < count; i++)
		
		if (accounts[i].equals(a)) return i; return -1;
		}
		
}




// Abdul Majid Fahim(Hamilton)
// 10614742
// PA12
// 6 hours
import java.util.Date;
import java.util.Random;

public class BankAccount {

	protected String name;
	protected double balance;
	protected int acctNum;
	protected Date date;
	protected static int accountsCreated;

	public BankAccount(String name) {
		this.name = name;
		this.balance = 0;
		this.acctNum = generateAcctNum();
		this.date = new Date();
		accountsCreated++;
	}
	
	public static int getAccountsCreated(){
		return accountsCreated;
	}

	public int getAcctNum() {
		return acctNum;
	}

	public boolean transfer(BankAccount b2, double amt) {
		if (this.balance < amt || amt < 0)
			return false;
		this.balance -= amt;
		b2.balance += amt;
		return true;
	}

	public double getBalance() {
		return balance;
	}

	public boolean deposit(double amt) {
		if (amt >= 0) {
			balance += amt;
			return true;
		}
		return false;

	}

	public boolean withdraw(double amt) {
		if (amt >= 0 && amt <= balance) {
			balance -= amt;
			return true;
		}
		return false;
	}

	public String toString() {
		return name + "[" + acctNum + "]\n" + date.toString() + "\n" + "$" + String.format("%,.2f", balance);
	}

	public boolean equals(BankAccount that) {
		if (this.acctNum == that.acctNum)
			return true;
		else
			return false;
	}

	protected int generateAcctNum() {
		Random r = new Random();
		String s = r.nextInt(9) + 1 + "";
		for (int i = 1; i <= 8; i++)
			s += r.nextInt(10);
		return Integer.parseInt(s);
	}

}





import java.util.Scanner;

public class BankTeller {

	// private static
public static void main (String [] args) {

	char command;
	
	Scanner input = new Scanner(System.in);
	
	printMenu();
	
    do {
    
    	System.out.println("\nPlease enter a command or type ?");
	
    	command = input.nextLine().toLowerCase().charAt(0);
    	
    	switch (command) {
	
    	case 'a':
	
    	int savingaccountOrCheckingaccount = -1;
	
    	while (savingaccountOrCheckingaccount < 1 || savingaccountOrCheckingaccount > 2){
	
    		System.out.println("Enter 1 for Savings Account or 2 for Checking Account: ");
		
    		savingaccountOrCheckingaccount = Integer.parseInt(input.nextLine());
    	
    	
    	
    	
    		System.out.println("Bank Teller Options");
    		String Options = input.nextLine();
    		System.out.println("-----------------------------------");
    		System.out.println("a: add an account to the bank");
    		String a = input.nextLine();
    		System.out.println("b: remove an account from the bank");
    		String b = input.nextLine();
    		System.out.println("c: display the accounts in the bank");
    		String c = input.nextLine();
    		System.out.println("d: count the accounts in the bank");
    		String d = input.nextLine();
    		System.out.println("e: sort the accounts in the bank");
    		String e = input.nextLine();
    		System.out.println("f: update an account in the bank");
    		String f = input.nextLine();
    		System.out.println("?: display the menu again");
    		String nocomprenda = input.nextLine();
    		System.out.println("q: quit this program");
    		String q = input.nextLine();
    		
    		Account a1;
    		if (savingaccountOrCheckingaccount == 1){
    			System.out.println("Enter account holder name: ");
    			int n = Integer.parseInt(input.nextLine());
    			n = new account();
    			
    		}
    		else {
    			System.out.println("Enter staring check number: " + 100);
    			int t = Integer.parseInt(input.nextLine());
    			case 'a' = account.add();
    			break;
    			if ((account.add(n)) System.out.println("\nAccount added successfuly\n");
    			else System.out.println("Account not added. No duplicates please. \n");
    			break;
    			case 'c': account.display();
    			System.out.println(account.toString());
    			break;
    			case 'd': account.getCount();
    			System.out.println("\nThere are" + account.getCount() + "accounts in the bank");
    			break;
    			case 'e' account.sort(Bank);
    			break; 
    			case 'f' account.update();
    			System.out.println("\n The Account is updated");
    			break;
    			case '?': account.printmenu();
    			return printmenu;
    			break;
    			case 'q': account.quit();
    			System.out.println("\nGOODBYE");
    		}
    	
    			
    			
    		
    	
    	
    }

	
}

	public static void printMenu() {
		System.out.print("\nBank Teller Options\n" + "-----------------------------------\n"
				+ "a: add an account to the bank\n" + "b: remove an account from the bank\n"
				+ "c: display the accounts in the bank\n" + "d: count the accounts in the bank\n"
				+ "e; sort the accounts in the bank\n" + "f: update an account in the bank"
				+ "?: display the menu again\n" + "q: quit this program\n\n");
	}
}



public class TestBankAccount {

	public static void main(String[] args) {
	
		BankAccount b = new BankAccount("t=yomamma");
		
		System.out.println(b.toString());
	}

}



