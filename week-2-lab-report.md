# **Week 2 Lab Report**
***
## Part 1: ChatServer

**code for `ChatServer`**
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // array list to store strings
    String output = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return output;
        } 
        else {
            if (url.getPath().contains("/add-message")) {

                // split url before and after '&' sign into array
                // [s=Hello, user=jpolitz]
                String[] parameters = url.getQuery().split("&");

                // split key & value by '=' sign 
                // [s, Hello]
                String[] message1 =  parameters[0].split("=");

                // split key & value by '=' sign 
                // [user, jpolitz]
                String[] message2 =  parameters[1].split("=");

                // create temporary string to store values
                String temp = "";

                // store jpolitz in temp string
                if (message2[0].equals("user")) {
                temp += message2[1];
                }

                // store Hello in temp string
                if (message1[0].equals("s")) {
                    temp += ": " + message1[1];
                }

                // store temp string in output string, with new line
                output += temp + "\n";
                return output;
            }
            return "404 Not Found!";
        }
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
**Screenshot of `/add-message?s=Hello&user=jpolitz`**
[Screenshot] (https://drive.google.com/file/d/1aF8EjpzR-2N5ggnS2dGZ-YQQK7XRtSlJ/view?usp=sharing)

**Screenshot of `/add-message?s=How%20are%20you&user=yash`**
[Screenshot] (https://drive.google.com/file/d/1Qr9aGd4_EaMCVjUy-PJMHnUhvoK2P7Vt/view?usp=sharing)


