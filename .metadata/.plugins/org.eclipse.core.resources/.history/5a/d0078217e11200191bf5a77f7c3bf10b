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

public class Review {

	private int id;
	private Account subject;
	private Account author;
	private String message;
	private int rating;
	
	Review(int id, Account subject, Account author, String message, int rating){
		this.id=id;
		this.subject=subject;
		this.author=author;
		this.message=message;
		this.rating=rating;
		
	}
	
	Review(int rating){
		this.rating=rating;
	}
	
	//Getters
	int getId(){
		return this.id;
	}
	Account getSubject(){
		return this.subject;
	}
	Account getAuthor(){
		return this.author;
	}
	String getMessage(){
		return this.message;
	}
	int getRating(){
		return this.rating;
	}
	
	//Setters
	void setMessage(String message){
		this.message=message;
	}
	void setRating(int rating){
		this.rating=rating;
	}
	
	static void createReview(Review review){
		String newSubject =review.getSubject().getUsername(); 
		String newAuthor = review.getAuthor().getUsername();
		String newMessage = review.getMessage();
		String newRating = Integer.toString(review.getRating());
		 
		URL URLcreateAccount;
		try {
			URLcreateAccount = new URL("http://104.196.62.218/CreateReview.php");
			HttpURLConnection httpUrlConnection = (HttpURLConnection) URLcreateAccount.openConnection();
			httpUrlConnection.setRequestMethod("POST");
			httpUrlConnection.setDoOutput(true);
			OutputStream outputStream = httpUrlConnection.getOutputStream();
			
			BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream, "UTF-8"));
			   String data_string = URLEncoder.encode("subject", "UTF-8") + "=" + URLEncoder.encode(newSubject, "UTF-8") + "&" +
			           URLEncoder.encode("author", "UTF-8") + "=" + URLEncoder.encode(newAuthor, "UTF-8")+ "&" +
					   URLEncoder.encode("message", "UTF-8") + "=" + URLEncoder.encode(newMessage, "UTF-8")+ "&" +
					   URLEncoder.encode("rating", "UTF-8") + "=" + URLEncoder.encode(newRating, "UTF-8");

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
	static String getReview(Review review){
		String newSubject = review.getSubject().getUsername();
		String JSON_STRING;
		String returnString="";
		try {
			   URL url = new URL("http://104.196.62.218/GetReview.php");
			   HttpURLConnection httpUrlConnection = (HttpURLConnection) url.openConnection();
			   httpUrlConnection.setRequestMethod("POST");
			   httpUrlConnection.setDoOutput(true);
			   OutputStream outputStream = httpUrlConnection.getOutputStream();
			   BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream, "UTF-8"));
			   String data_string = URLEncoder.encode("suject", "UTF-8") + "=" + URLEncoder.encode(newSubject, "UTF-8");
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
