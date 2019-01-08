import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.OutputStream;
import java.io.OutputStreamWriter;
import java.net.HttpURLConnection;
import java.net.MalformedURLException;
import java.net.URL;
import java.net.URLEncoder;
import java.util.ArrayList;

public class Task {

	private int id;
	private Account author;
	private double wage;
	private String estimatedTime;
	private ArrayList <String> skillsRequired;
	private String location;
	private String description;
	private TaskStatus status;
	
	//account author, string?
	Task(int id, Account author, double wage, String estimatedTime, String skillsRequired, String location, String description){
		
		this.id=id;
		this.author=author;
		this.wage=wage;
		this.estimatedTime=estimatedTime;
		this.skillsRequired.add(skillsRequired); ///GOTTA FIX THIS string to string list thing
		this.location=location;
		this.description=description;
		
	}
	
	//getters
	int getId(){
		return this.id;
	}
	Account getAuthour(){
		return this.author;
	}
	double getWage(){
		return this.wage;
	}
	String getEstimatedTime(){
		return this.estimatedTime;
	}
	ArrayList<String> getSkillsRequired(){
		return this.skillsRequired;
	}
	
	String getLocation(){
		return this.getLocation();
	}
	String getDescription(){
		return this.description;
	}
	TaskStatus getTaskStatus(){
		return this.status;
	}
	
	//setters
	
	void setWage(double wage){
		this.wage=wage;
	}
	void setEstimatedTime(String estimatedTime){
		this.estimatedTime=estimatedTime;
	}
	void setSkillsRequired(ArrayList<String> skillRequired){
		this.skillsRequired=skillRequired;
	}
	void setLocation(String location){
		this.location=location;
	}
	void setDescription(String desc){
		this.description=desc;
	}
	
	
	static void createTask(Task newTask){
		
		
		String newAuthor = newTask.getAuthour().getUsername();
		String newWage = Double.toString(newTask.getWage());
		String newEstimatedTime = newTask.getEstimatedTime();
		String newSkillsRequired = newTask.getSkillsRequired().toString();
		String newLocation = newTask.getLocation();
		String newDescription = newTask.getDescription();
		
		 
		URL URLcreateAccount;
		try {
			URLcreateAccount = new URL("http://104.196.62.218/CreateTask.php");
			HttpURLConnection httpUrlConnection = (HttpURLConnection) URLcreateAccount.openConnection();
			httpUrlConnection.setRequestMethod("POST");
			httpUrlConnection.setDoOutput(true);
			OutputStream outputStream = httpUrlConnection.getOutputStream();
			
			BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream, "UTF-8"));
			   String data_string = URLEncoder.encode("author", "UTF-8") + "=" + URLEncoder.encode(newAuthor, "UTF-8") + "&" +
			           URLEncoder.encode("pay", "UTF-8") + "=" + URLEncoder.encode(newWage, "UTF-8")+ "&" +
					   URLEncoder.encode("estimatedTime", "UTF-8") + "=" + URLEncoder.encode(newEstimatedTime, "UTF-8")+ "&" +
					   URLEncoder.encode("skillsRequired", "UTF-8") + "=" + URLEncoder.encode(newSkillsRequired, "UTF-8")+ "&" +
					   URLEncoder.encode("location", "UTF-8") + "=" + URLEncoder.encode(newLocation, "UTF-8")+ "&" +
					   URLEncoder.encode("description", "UTF-8") + "=" + URLEncoder.encode(newDescription, "UTF-8");

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
	}
	static String getTaskDetails(Task task){
		String newId = Integer.toString(task.getId());
		String JSON_STRING;
		String returnString="";
		try {
			   URL url = new URL("http://104.196.62.218/GetTaskDetails.php");
			   HttpURLConnection httpUrlConnection = (HttpURLConnection) url.openConnection();
			   httpUrlConnection.setRequestMethod("POST");
			   httpUrlConnection.setDoOutput(true);
			   OutputStream outputStream = httpUrlConnection.getOutputStream();
			   BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream, "UTF-8"));
			   String data_string = URLEncoder.encode("id", "UTF-8") + "=" + URLEncoder.encode(newId, "UTF-8");
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
		
		
	}

}
