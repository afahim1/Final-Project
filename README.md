
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


