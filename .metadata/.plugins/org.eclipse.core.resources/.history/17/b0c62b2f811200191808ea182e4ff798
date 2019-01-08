import java.io.*;
import java.net.MalformedURLException;
import java.net.*;
import java.util.*;

import org.json.*;

//import org.json.JSONParser;
public class Account {

	private int id;
	private String username; //email?
	private String firstName;
	private String lastName;
	private String password;
	private int age;
	
	private Bio bio;
	private Review reviews;
	
	//Constructor
	Account(String userName, String firstName, String lastName, String password, int age){
		this.username=userName;
		this.firstName=firstName;
		this.lastName=lastName;
		this.password=password;
		this.age=age;
		
	}
	//Getters
	int getId(){
		return this.id;
	}
	String getUsername(){
		return this.username;
	}
	String getLastName(){
		return this.lastName;
	}
	String getFirstName(){
		return this.firstName;
	}
	String getPassword(){
		return this.password;
	}
	int getAge(){
		return this.age;
	}
	Bio getBio(){
		return this.bio;
	}
	
	//Setters
	
	void setId(int id){
		this.id=id;
	}
	void setUsername(String username){
		this.username=username;
	}
	void setLastName(String lastName){
		this.lastName=lastName;
	}
	void setFirstName(String firstName){
		this.firstName=firstName;
	}
	void setPassword(String password){
		this.password=password;
	}
	void setAge(int age){
		this.age=age;
	}
	void setBio(Bio bio){
		this.bio=bio;
	}
	
	
	static void createAccount(Account newAccount){
		
		String newUsername =newAccount.getUsername(); 
		String newFirstName =newAccount.getFirstName();
		String newLastName=newAccount.getLastName();
		String newPassword=newAccount.getPassword();
		String newAge=Integer.toString(newAccount.getId());//change to int later
		
		 
		URL URLcreateAccount;
		try {
			URLcreateAccount = new URL("http://104.196.62.218/CreateAccount.php");
			HttpURLConnection httpUrlConnection = (HttpURLConnection) URLcreateAccount.openConnection();
			httpUrlConnection.setRequestMethod("POST");
			httpUrlConnection.setDoOutput(true);
			OutputStream outputStream = httpUrlConnection.getOutputStream();
			
			BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream, "UTF-8"));
			   String data_string = URLEncoder.encode("username", "UTF-8") + "=" + URLEncoder.encode(newUsername, "UTF-8") + "&" +
			           URLEncoder.encode("firstName", "UTF-8") + "=" + URLEncoder.encode(newFirstName, "UTF-8")+ "&" +
					   URLEncoder.encode("lastName", "UTF-8") + "=" + URLEncoder.encode(newLastName, "UTF-8")+ "&" +
					   URLEncoder.encode("password", "UTF-8") + "=" + URLEncoder.encode(newPassword, "UTF-8")+ "&" +
					   URLEncoder.encode("age", "UTF-8") + "=" + URLEncoder.encode(newAge, "UTF-8");

			   bufferedWriter.write(data_string);
			   bufferedWriter.flush();
			   bufferedWriter.close();
			   outputStream.close();
			 //Getting data
			   InputStream inputStream = httpUrlConnection.getInputStream();
			  
			   inputStream.close();
			   httpUrlConnection.disconnect();
			  

		} catch (MalformedURLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		//return newAge;
		
		 
		 

}
	static void updateAccount(){
		
	}
	
	static String getAccount(String userName){
		
		String JSON_STRING;
		String returnString="";
		try {
			   URL url = new URL("http://104.196.62.218/GetAccount.php");
			   HttpURLConnection httpUrlConnection = (HttpURLConnection) url.openConnection();
			   httpUrlConnection.setRequestMethod("POST");
			   httpUrlConnection.setDoOutput(true);
			   OutputStream outputStream = httpUrlConnection.getOutputStream();
			   BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream, "UTF-8"));
			   String data_string = URLEncoder.encode("username", "UTF-8") + "=" + URLEncoder.encode(userName, "UTF-8");
			   bufferedWriter.flush();
			   bufferedWriter.close();

			   //Getting data
			   InputStream inputStream = httpUrlConnection.getInputStream();
			   BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(inputStream, "iso-8859-1"));
			   StringBuilder stringBuilder = new StringBuilder();

			   while ((JSON_STRING = bufferedReader.readLine()) != null) {

			       stringBuilder.append(JSON_STRING + "\n");
			   }

			   bufferedReader.close();
			   inputStream.close();
			   httpUrlConnection.disconnect();
			   returnString=stringBuilder.toString().trim();
			

			}
		
		 catch (MalformedURLException e) {
			   e.printStackTrace();
			} catch (IOException e) {
			   e.printStackTrace();
			}
		 return returnString;

	}
public static void main(String[] args) {
	Account tester = new Account("charr", "akram","hannoufa", "adwa", 7);
				
		createAccount(tester);
		System.out.println(getAccount("charr"));;
		//System.out.println(JSONText);
	}
}